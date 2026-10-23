# Restricciones

Las restricciones son condiciones, reglas o limitaciones que deben respetarse durante el desarrollo del sistema. Pueden ser tecnológicas, organizacionales, legales o del proyecto.

## Listado de restricciones

| ID | Restricción | Descripción |
| --- | --- | --- |
| RC01 | Canales digitales | El sistema debe atender al administrado a través de canales digitales: WhatsApp, aplicación web y, opcionalmente, SMS para zonas con poca conectividad. |
| RC02 | Marco normativo peruano | El sistema debe alinearse con el TUPA de la entidad, el TUO de la Ley 27444 (Ley del Procedimiento Administrativo General) y demás normas vigentes aplicables. |
| RC03 | Protección de datos personales | El sistema debe cumplir con la Ley 29733 y su reglamento, incluyendo consentimiento, enmascarado, cifrado, retención de conversaciones y cláusulas de confidencialidad con el proveedor externo. |
| RC04 | Integración con sistema documentario | El sistema debe integrarse con el sistema de gestión documentaria o mesa de partes virtual de la entidad para registrar expedientes y consultar su estado, mediante una capa anticorrupción. |
| RC05 | Proveedor gestionado de modelos | El sistema debe apoyarse en un proveedor externo de modelos de lenguaje y voz, gestionado mediante contrato y con acuerdos de tratamiento de datos. |
| RC06 | Catálogo TUPA versionado | El catálogo de trámites debe estar versionado y ser actualizable por el gestor de área, sin necesidad de desplegar código. |
| RC07 | Control de versiones | El código fuente y los archivos de documentación deben gestionarse con Git en un repositorio compartido. |
| RC08 | Documentación como código | La documentación del sistema (diagramas, propuesta, análisis) debe versionarse junto con el código fuente. |
| RC09 | Accesibilidad | La aplicación web ciudadana debe cumplir con criterios de accesibilidad WCAG y, cuando el público lo requiera, ofrecer soporte de quechua. |
| RC10 | Idioma | La interfaz y las respuestas deben estar disponibles en español por defecto, con la opción de incluir quechua si la entidad lo define. |