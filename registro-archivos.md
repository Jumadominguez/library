# Registro de Archivos y Dependencias

Este documento registra las descripciones de cada archivo en el proyecto, incluyendo su propósito, ubicación y relaciones/dependencias con otros archivos. Manténlo actualizado para facilitar la navegación y modificaciones.

## Tabla de Archivos

| Archivo | Ubicación | Descripción | Dependencias | Última Modificación |
|---------|-----------|-------------|--------------|---------------------|
| instrucciones-globales.md | docs/ | Define reglas globales para desarrollo con Vibe Coding. | glosario.md, sandbox.md | [Fecha] |
| instrucciones-inicio.md | docs/ | Guía paso a paso para iniciar proyectos. | cuestionario-inicial.md, puertos.md | [Fecha] |
| sandbox.md | docs/ | Explica el uso del entorno Sandbox. | instrucciones-globales.md | [Fecha] |
| glosario.md | docs/ | Definiciones de términos clave. | Ninguna | [Fecha] |
| cuestionario-inicial.md | docs/ | Cuestionario para recopilar info inicial. | instrucciones-inicio.md | [Fecha] |
| puertos.md | docs/ | Registro de puertos asignados. | instrucciones-globales.md | [Fecha] |
| guia-uso.md | docs/ | Guía para usar los documentos. | Todos los .md | [Fecha] |
| github-instrucciones.md | docs/ | Instrucciones para Git y GitHub. | instrucciones-globales.md | [Fecha] |
| proceso-creativo.md | docs/ | Describe el proceso visual y creativo de desarrollo. | sandbox.md, instrucciones-globales.md | [Fecha] |
| registro-archivos.md | docs/ | Registro de archivos y dependencias. | Todos los archivos del proyecto | [Fecha] |

## Instrucciones de Uso

- **Actualización**: Agrega una fila por cada nuevo archivo creado. Incluye descripción breve, dependencias (archivos que usa o que lo usan) y fecha.
- **Dependencias**: Lista archivos relacionados, e.g., "Depende de utils.py para funciones auxiliares".
- **Búsqueda**: Usa esta tabla para identificar archivos rápidamente antes de modificaciones.
- **Mantenimiento**: Actualiza al crear, modificar o eliminar archivos. Registra en commits como `[DOC-XXX] Actualizar registro-archivos.md`.

Este registro asegura una estructura modular y clara, facilitando el trabajo con la IA.
