# Atributos de calidad

Los atributos de calidad describen **cómo** debe comportarse el sistema, más allá de las funcionalidades que ofrece.

## Escenario

La entidad atiende a miles de administrados a través de canales digitales. El asistente recibe consultas sobre requisitos, costos y plazos, solicitudes para iniciar trámites y preguntas sobre el estado de expedientes, a veces con voz y texto. Si la información que entrega es incorrecta o el sistema se cae en horas pico, el administrado pierde tiempo y la entidad pierde confianza. ¿Qué atributos de calidad resultan importantes?

## Atributos de calidad identificados

| ID | Atributo de calidad | Escenario de calidad |
| --- | --- | --- |
| AC01 | Exactitud | Toda respuesta sobre requisitos, costos o plazos debe estar sustentada en el documento normativo vigente. Cuando no se alcanza un nivel mínimo de confianza, el sistema debe derivar el caso a un gestor humano. |
| AC02 | Disponibilidad | El canal de atención debe seguir recibiendo mensajes aun cuando los servicios de inferencia estén degradados. Si el proveedor de modelos no responde, el sistema debe entregar respuestas básicas del catálogo y derivar el resto. |
| AC03 | Rendimiento | El gateway de canales debe devolver un código de seguimiento al administrado en menos de 200 ms, incluso bajo alta concurrencia. |
| AC04 | Escalabilidad | El gateway, el bus de eventos y los workers deben escalar de forma independiente según la carga de cada etapa (tráfico de canales, transcripción, clasificación, generación). |
| AC05 | Privacidad y protección de datos | El sistema debe cumplir con la Ley 29733: enmascarar DNI y datos de contacto antes de enviarlos al proveedor externo, solicitar consentimiento y definir la retención de conversaciones. |
| AC06 | Trazabilidad | Cada respuesta debe quedar registrada con la versión del documento citado, el nivel de confianza y, si hubo derivación, el gestor que aprobó la respuesta. |
| AC07 | Mantenibilidad del conocimiento | Cuando cambia el TUPA o un documento normativo, el gestor de área debe poder actualizar el catálogo y reindexar el corpus sin desplegar código. |
| AC08 | Accesibilidad e inclusión | El sistema debe ofrecer voz y texto, lenguaje claro y la opción de quechua si el público de la entidad lo necesita, además de cumplir con criterios de accesibilidad web (WCAG) en la aplicación ciudadana. |
| AC09 | Interoperabilidad | El sistema debe integrarse con el sistema de gestión documentaria, los canales de atención (WhatsApp, web, SMS), el proveedor de modelos y, opcionalmente, con RENIEC y la pasarela de pagos, mediante capas anticorrupción. |
| AC10 | Resiliencia | La caída del proveedor de modelos o del sistema documentario no debe impedir la atención: debe haber degradación controlada y caché de estados para consultas ya resueltas. |