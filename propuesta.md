# Propuesta: asistente virtual para trámites e información administrativa

Se tomó la estructura de WILLAKUY (contexto, contenedores, componentes del worker) y se adaptó de un canal de consultas y reclamos a un asistente que orienta, guía y da seguimiento a trámites. Se asume una entidad pública peruana con TUPA y mesa de partes. Si es otra institución, solo cambia el catálogo de trámites.

## 1. Contexto

El asistente es el punto único de orientación para trámites e información de la entidad. Lo usan tres actores:

- **Administrado (usuario):** consulta requisitos, costos, plazos y estado de su expediente. También recibe ayuda guiada para iniciar un trámite, por texto o voz.
- **Gestor de área:** atiende los casos que el asistente no puede resolver con certeza, valida borradores de respuesta y mantiene actualizado el catálogo de trámites de su área.
- **Autoridad o administrador:** consulta métricas de demanda, trámites más consultados, cuellos de botella y plazos vencidos.

**Sistemas externos:**

- WhatsApp y web como canales principales, más SMS para zonas con poca conectividad.
- Sistema de gestión documentaria o mesa de partes virtual, donde se registra el expediente y se consulta su estado.
- Proveedor gestionado de modelos de lenguaje y voz.
- Opcionales según la entidad: validación de identidad (RENIEC/PIDE) y pasarela de pagos.

**Cambio principal respecto a WILLAKUY:** el asistente no solo responde, también consulta el estado real del expediente y guía el llenado de requisitos. Eso introduce integración con sistemas internos y datos personales.

## 2. Contenedores

| Contenedor | Responsabilidad |
| --- | --- |
| Gateway de canales | API sin estado. Recibe de todos los canales, valida, encola el mensaje y devuelve un código de seguimiento en menos de 200 ms. Es lo único en la ruta crítica del usuario. |
| Bus de eventos | Colas por etapa: transcripción, clasificación, respuesta, notificación. Desacopla la ingesta de la inferencia. |
| Workers de procesamiento | Transcripción de voz, clasificación y enrutamiento, y generación de respuesta con recuperación documental. Escalan por separado. |
| Servicio de trámites (nuevo) | Expone el catálogo TUPA estructurado (requisitos, costos, plazos, base legal, área responsable). Consulta el estado de expedientes en el sistema documentario mediante una capa anticorrupción. |
| Gestor de diálogo guiado (nuevo) | Máquina de estados para flujos como "quiero iniciar el trámite X": pide datos, verifica requisitos, adjunta documentos y entrega el expediente prellenado. |
| Aplicación web ciudadana | Interfaz accesible (WCAG) con el mismo flujo que el canal conversacional. |
| Backoffice institucional | Bandeja de casos derivados, aprobación de respuestas, edición del catálogo, tablero de demanda y plazos. |
| Servicio de notificaciones | Responde por el canal de origen y avisa cambios de estado del expediente. |
| Almacenamiento | Base relacional con extensión vectorial (casos y corpus normativo), caché en memoria (sesión y respuestas frecuentes) y repositorio de documentos oficiales. |

## 3. Componentes del worker de respuesta

El flujo es el mismo de WILLAKUY, con dos agregados señalados:

- **Normalizador de texto:** limpia y unifica la entrada.
- **Clasificador de intención:** distingue entre información (requisitos, costos, horarios), iniciar trámite, consultar estado y otro. Esta distinción es nueva y define qué camino sigue la consulta.
- **Extractor de entidades:** trámite, área, número de expediente, datos de contacto.
- **Verificador de caché semántica:** evita llamadas costosas si una consulta equivalente ya fue resuelta. No se aplica a consultas de estado, porque dependen del expediente de cada persona.
- **Enrutador por intención (nuevo):**
  - **Información:** sigue al recuperador.
  - **Estado:** consulta el Servicio de trámites, sin pasar por el modelo generativo.
  - **Iniciar trámite:** pasa al Gestor de diálogo guiado.
- **Recuperador:** consulta el corpus oficial (TUPA, directivas, TUO de la Ley 27444).
- **Generador:** redacta la respuesta con su cita normativa.
- **Evaluador de confianza:** emite automáticamente si el sustento documental es suficiente. Si no, deriva al gestor con un borrador ya redactado.

Que el estado del expediente se resuelva con datos reales y no con texto generado evita que el asistente invente información sobre casos concretos, que es el error más costoso en este dominio.

## 4. Atributos de calidad y decisiones clave

- **Exactitud sobre fluidez:** toda respuesta sobre requisitos o costos debe citar el documento fuente. Sin sustento, deriva a un humano.
- **Disponibilidad:** la ingesta responde aunque la inferencia esté caída, porque el bus absorbe la carga. Si el proveedor de modelos falla, el sistema responde con información del catálogo y deriva el resto.
- **Privacidad:** cumplimiento de la Ley 29733 (protección de datos personales). Se solicita consentimiento, se enmascaran DNI y datos de contacto antes de enviarlos al proveedor externo, y se define retención de conversaciones.
- **Trazabilidad:** cada respuesta guarda versión del documento citado, nivel de confianza y quién aprobó, si hubo derivación.
- **Actualización del conocimiento:** cuando cambia el TUPA, el gestor actualiza el catálogo y se reindexa el corpus sin tocar código.
- **Accesibilidad e inclusión:** voz y texto, lenguaje claro, y opción de quechua si el público lo requiere.

## 5. Riesgos principales

| Riesgo | Mitigación |
| --- | --- |
| Respuesta incorrecta sobre requisitos o costos | Cita obligatoria, umbral de confianza, revisión humana en casos dudosos |
| Información desactualizada | Versionado del catálogo y alertas de vigencia |
| Filtración de datos personales | Enmascarado, cifrado, acuerdos con el proveedor |
| Integración frágil con el sistema documentario | Capa anticorrupción, caché de estados y degradación controlada |
| Baja adopción | Canal WhatsApp, flujos cortos, indicadores de satisfacción |

## 6. Implementación por fases

- **Fase 1, información:** consultas sobre trámites frecuentes con cita normativa.
- **Fase 2, estado:** consulta de expedientes e integración con el sistema documentario.
- **Fase 3, trámite guiado:** prellenado de requisitos y envío a mesa de partes.
- **Fase 4, analítica:** tablero para autoridades y mejora continua del catálogo.