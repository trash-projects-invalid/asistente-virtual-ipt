# Requisitos funcionales

Los requisitos funcionales describen las funciones que el sistema debe realizar. Se obtienen a partir de las historias de usuario identificadas.

> **Diferencia importante**
>
> - **Historia de usuario:** expresa la necesidad desde el punto de vista del usuario.
> - **Requisito funcional:** expresa lo que el sistema debe hacer para satisfacer esa necesidad.

## Listado de requisitos funcionales

| ID | Requisito funcional |
| --- | --- |
| RF01 | El sistema debe permitir consultar los requisitos, costos y plazos de los trámites del catálogo TUPA. |
| RF02 | El sistema debe permitir guiar al administrado paso a paso en el inicio de un trámite, solicitando los datos y documentos necesarios. |
| RF03 | El sistema debe permitir consultar el estado de un expediente a partir de su número y los datos del administrado. |
| RF04 | El sistema debe permitir atender al administrado por múltiples canales (WhatsApp, web y SMS) manteniendo el mismo flujo conversacional. |
| RF05 | El sistema debe permitir transcribir mensajes de voz a texto para alimentar el mismo flujo de clasificación y respuesta. |
| RF06 | El sistema debe permitir clasificar la intención del mensaje (información, iniciar trámite, consultar estado u otro) y enrutar al componente correspondiente. |
| RF07 | El sistema debe permitir extraer entidades del mensaje (trámite, área, número de expediente, datos de contacto). |
| RF08 | El sistema debe permitir generar respuestas sustentadas en el corpus normativo oficial (TUPA, directivas, TUO de la Ley 27444) e incluir la cita del documento. |
| RF09 | El sistema debe permitir derivar al gestor de área, con un borrador ya redactado, cuando la confianza de la respuesta automática sea insuficiente. |
| RF10 | El sistema debe permitir al gestor de área aprobar, rechazar o editar las respuestas derivadas antes de enviarlas al administrado. |
| RF11 | El sistema debe permitir al gestor de área actualizar el catálogo de trámites (requisitos, costos, plazos y base legal) de su área. |
| RF12 | El sistema debe permitir registrar y consultar los expedientes generados a través del flujo guiado en el sistema de gestión documentaria. |
| RF13 | El sistema debe permitir notificar al administrado, por el canal de origen, los cambios de estado de su expediente. |
| RF14 | El sistema debe permitir almacenar la trazabilidad de cada respuesta (versión del documento citado, nivel de confianza y aprobador, si hubo derivación). |
| RF15 | El sistema debe permitir consultar indicadores de demanda, trámites más consultados, plazos vencidos y motivos de derivación para la autoridad o administrador. |

## Relación entre historias de usuario y requisitos funcionales

| Historia de usuario | Requisitos funcionales relacionados |
| --- | --- |
| HU01 Consultar requisitos, costos y plazos | RF01, RF08 |
| HU02 Orientación guiada para iniciar un trámite | RF02, RF12 |
| HU03 Consultar estado del expediente | RF03, RF13 |
| HU04 Atención por WhatsApp con voz y texto | RF04, RF05 |
| HU05 Respuesta con cita del documento | RF08, RF14 |
| HU06 Derivación a gestor humano | RF09, RF10 |
| HU07 Bandeja de casos derivados | RF09, RF10 |
| HU08 Actualización del catálogo de trámites | RF11 |
| HU09 Validación de borradores de respuesta | RF10, RF14 |
| HU10 Indicadores de demanda | RF15 |
| HU11 Visualización de plazos vencidos | RF15 |
| HU12 Indicadores de satisfacción y mejora | RF14, RF15 |