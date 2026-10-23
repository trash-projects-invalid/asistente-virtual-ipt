# Documentación del sistema

Este directorio reúne la documentación del asistente virtual para trámites e información administrativa. El proyecto se organiza siguiendo el enfoque del repositorio de referencia: la documentación vive en `docs/`, junto con sus fuentes y recursos visuales.

## Contenido

### Contexto y propuesta

- [Propuesta del asistente virtual](propuesta.md): contexto, actores, contenedores, flujo de respuesta, atributos de calidad, riesgos y fases.
- [Caso de arquitectura](caso-arquitectura.pdf): material de referencia del caso de estudio.

### Análisis del sistema

- [Actores](analisis-de-sistema/01-actores.md)
- [Historias de usuario](analisis-de-sistema/02-historias-del-usuario.md)
- [Requisitos funcionales](analisis-de-sistema/03-requisitos-funcionales.md)
- [Atributos de calidad](analisis-de-sistema/04-atributos-de-calidad.md)
- [Restricciones](analisis-de-sistema/05-restricciones.md)
- [Drivers arquitectónicos](analisis-de-sistema/06-driver-arquitectonicos.md)

### Arquitectura

- [Arquitectura inicial](arquitectura/arquitectura-inicial.md): capas, contenedores y diagrama del sistema.
- [Estilo arquitectónico](arquitectura/estilo-arquitectonico.md): workers desacoplados sobre bus de eventos.
- [Enfoque arquitectónico](arquitectura/enfoque-arquitectonico.md): Clean Architecture aplicado al Servicio de trámites.

### Diseño y diagramas

- [Diseño del sistema y diagramas](diseno/README.md): previsualizaciones y fuentes editables en Mermaid y PlantUML.

## Orden recomendado de lectura

1. [Propuesta](propuesta.md)
2. [Análisis del sistema](analisis-de-sistema/01-actores.md)
3. [Arquitectura inicial](arquitectura/arquitectura-inicial.md)
4. [Estilo arquitectónico](arquitectura/estilo-arquitectonico.md)
5. [Enfoque arquitectónico](arquitectura/enfoque-arquitectonico.md)
6. [Diseño y diagramas](diseno/README.md)
