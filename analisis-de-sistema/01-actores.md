# Actores del sistema

Este documento identifica los actores (personas, organizaciones o sistemas externos) que interactúan con el asistente virtual de trámites e información administrativa.

## Actores

| Actor | Descripción | ¿Qué necesita realizar? |
| --- | --- | --- |
| Administrado | Persona (ciudadano o empresa) que realiza trámites y consulta información ante la entidad. | Consultar requisitos, costos y plazos de los trámites del TUPA, consultar el estado de su expediente e iniciar un trámite con ayuda guiada, por texto o voz. |
| Gestor de área | Servidor público asignado a un área de la entidad que mantiene actualizado el catálogo de trámites y resuelve los casos derivados por el asistente. | Atender casos derivados, validar y aprobar borradores de respuesta, actualizar requisitos y documentos normativos de su área y supervisar la calidad de las respuestas automáticas. |
| Autoridad o administrador | Funcionario con visión institucional que monitorea la demanda y el desempeño del servicio. | Consultar indicadores de demanda, trámites más consultados, cuellos de botella, plazos vencidos y nivel de satisfacción del administrado. |
| Sistema de gestión documentaria | Sistema externo (mesa de partes virtual o trámite documentario) donde se registran los expedientes y se consulta su estado. | Registrar expedientes y sus documentos asociados, así como exponer el estado y la trazabilidad de cada expediente. |
| Canales de atención | Sistemas externos que reciben y entregan mensajes al administrado. Incluyen WhatsApp, aplicación web y SMS. | Transportar los mensajes entre el administrado y su backend, entregando confirmaciones y respuestas. |
| Proveedor de modelos de lenguaje y voz | Servicio gestionado externo que provee capacidades de transcripción de voz y generación de texto. | Recibir texto o audio y devolver resultados estructurados (intención, entidades, respuesta redactada), cumpliendo los acuerdos de confidencialidad. |
| RENIEC / PIDE (opcional) | Servicio externo de validación de identidad del administrado, cuando la entidad lo requiere. | Validar la identidad del administrado cuando un trámite lo exige. |
| Pasarela de pagos (opcional) | Servicio externo para el cobro de tasas administrativas cuando el trámite lo requiere. | Procesar pagos de tasas y devolver el comprobante al sistema. |