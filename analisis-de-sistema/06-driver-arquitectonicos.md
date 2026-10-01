# Drivers arquitectónicos

Los drivers arquitectónicos son los requisitos, atributos de calidad y restricciones que influyen significativamente en las decisiones de arquitectura del sistema.

## Listado de drivers arquitectónicos

| ID | Driver arquitectónico | Origen | ¿Por qué influye en la arquitectura? |
| --- | --- | --- | --- |
| DA01 | Toda respuesta sobre requisitos, costos o plazos debe sustentarse en el documento normativo vigente. | AC01 – Exactitud | Obliga a separar el componente generador del recuperador documental y a registrar la cita y la versión del documento en cada respuesta. |
| DA02 | Las consultas de estado de expedientes deben resolverse con datos reales del sistema documentario, no con texto generado. | AC01 – Exactitud / RF03 | Obliga a enrutar la consulta directamente al Servicio de trámites, evitando el paso por el modelo generativo para evitar alucinaciones sobre casos concretos. |
| DA03 | El gateway de canales debe responder en menos de 200 ms y absorber picos de concurrencia. | AC02 – Disponibilidad / AC03 – Rendimiento | Obliga a un gateway sin estado, a un bus de eventos que desacople la ingesta de la inferencia y a workers que escalen de forma independiente. |
| DA04 | El sistema debe seguir aceptando mensajes aunque el proveedor de modelos o el sistema documentario estén degradados. | AC02 – Disponibilidad / AC10 – Resiliencia | Obliga a un diseño con degradación controlada: respuestas básicas del catálogo, derivación al gestor humano y caché de estados. |
| DA05 | El sistema debe proteger los datos personales conforme a la Ley 29733. | AC05 – Privacidad / RC03 | Obliga a enmascarar DNI y datos de contacto antes de enviarlos al proveedor externo, a registrar consentimiento y a definir retención de conversaciones. |
| DA06 | El sistema debe integrarse con el sistema de gestión documentario mediante una capa anticorrupción. | RC04 – Integración con sistema documentario | Obliga a aislar el modelo interno de los expedientes del esquema del proveedor para evitar acoplamiento y facilitar cambios. |
| DA07 | El catálogo de trámites (TUPA) debe poder actualizarse sin desplegar código. | AC07 – Mantenibilidad del conocimiento / RC06 | Obliga a separar el corpus normativo del código, con versionado y alertas de vigencia, y a reindexar automáticamente al actualizarse. |
| DA08 | Cada respuesta debe quedar trazada (versión del documento, confianza, gestor aprobador). | AC06 – Trazabilidad | Obliga a persistir un registro de auditoría por cada respuesta automática y por cada derivación aprobada. |
| DA09 | El sistema debe atender al administrado por WhatsApp, web y SMS con el mismo flujo conversacional. | RC01 – Canales digitales / RF04 | Obliga a un gateway único que abstraiga los canales y a que la lógica de negocio no dependa de un canal específico. |
| DA10 | La aplicación web ciudadana debe ser accesible y, cuando aplique, ofrecer quechua. | AC08 – Accesibilidad e inclusión / RC09 | Obliga a criterios WCAG, lenguaje claro y opción multilingüe desde el inicio del diseño de la interfaz. |