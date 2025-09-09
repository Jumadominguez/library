# Instrucciones Globales para Desarrollo con Vibe Coding

Estas instrucciones globales rigen el proceso de desarrollo en cualquier proyecto utilizando el enfoque de Vibe Coding. El objetivo es mantener un entorno ordenado, eficiente y reproducible.

## Registro de Archivos Incorporados

Cada archivo incorporado al proyecto después de ser aprobado en `prototypes` debe tener un documento Markdown individual en la carpeta `docs/archivos/`. Este documento debe incluir:

- **Nombre del Archivo**: Ruta completa y nombre.
- **Propósito**: Descripción detallada de qué hace el archivo y su rol en la feature.
- **Relaciones con Otros Archivos**: Lista de archivos con los que interactúa, dependencias y cómo se conecta.
- **Instrucciones de Recreación**: Pasos detallados para recrear el archivo exactamente igual, incluyendo código clave, configuraciones y contexto.
- **Fecha de Incorporación**: Fecha en que fue aprobado y movido.
- **Feature Asociada**: Referencia a la feature que implementa.

Ejemplo de estructura para un archivo `docs/archivos/backend_api.py.md`:

```
# Desglose de Archivo: backend_api.py

## Propósito
Este archivo maneja las rutas de la API para el backend, conectando con la base de datos y procesando solicitudes.

## Relaciones
- Depende de `models/user.py` para la estructura de usuario.
- Llama a `utils/auth.py` para autenticación.
- Integrado en `app.py` como blueprint.

## Recreación
1. Crear archivo en `src/backend/api.py`.
2. Importar dependencias: `from flask import Blueprint, request`.
3. Definir rutas: `@api.route('/users', methods=['GET'])`.
4. Implementar lógica de autenticación y respuesta JSON.
```

Estos documentos deben mantenerse actualizados y permitir que una nueva sesión de IA recree el desarrollo leyendo solo estos archivos.

## Estructura de Carpetas para Tests y Archivos Temporales

- **Tests**: Ubicados en `tests/` en la raíz del proyecto. Subcarpetas por módulo, e.g., `tests/backend/`, `tests/frontend/`.
- **Archivos Temporales**: Usar `Sandbox/temps/` para cualquier archivo no esencial. Limpiar periódicamente.

No incorporar archivos de test o temporales en la estructura principal del proyecto.

## Registro de Puertos

Mantener un registro actualizado de puertos en `puertos.md` para evitar interferencias. Asignar puertos según rangos definidos:

- Frontend producción: X000
- Backend producción: Y000
- Prototypes frontend: X100
- Experiments: Rango X800-X899
- Debugging: Rango Z000-Z200

Antes de iniciar cualquier servidor, verificar que el puerto esté libre y actualizar la tabla en `puertos.md`. Para debugging temporal, usar puertos en Z000-Z200 y liberar después.

## Documentación del Proceso

Después de aprobar una nueva feature en `prototypes`, documentar el proceso completo en `proceso.md`. Este archivo debe incluir:

1. **Fase de Experimentación**: Pasos en `Sandbox/Experiments/`.
2. **Fase de Debugging**: Uso de `Sandbox/Debug/`.
3. **Fase de Prototipado**: Pruebas en `Sandbox/prototypes/`.
4. **Integración Final**: Movimiento a la estructura principal y ajustes.
5. **Testing**: Ejecución de tests y validación.
6. **Documentación**: Actualización de `docs/archivos/` y este `proceso.md`.

Mantener `proceso.md` actualizado con cada nueva feature para un registro cronológico. Consulta `proceso-creativo.md` para el enfoque visual en desarrollo.

## Interacción con la IA

- La IA debe seguir las instrucciones directamente sin explicaciones paso a paso sobre el proceso de desarrollo. Generar código, modificaciones o acciones de inmediato para optimizar el uso de créditos.
- Solo responder con texto cuando se le haga una pregunta explícita. De lo contrario, proceder con la tarea asignada silenciosamente.

## Buenas Prácticas Generales

- Siempre iniciar desarrollo en `Sandbox`.
- Mantener una estructura modular del proyecto: archivos más chicos y fácilmente identificables, en lugar de pocos archivos extensos. Esto facilita el procesamiento por parte de la IA y reduce errores en modificaciones.
- Usar control de versiones con Git, ignorando `Sandbox/Debug/`, `Sandbox/Temps/`, entornos virtuales y `tests/` si no es necesario. Incluir `Sandbox/Experiments/` y `Sandbox/Prototypes/` para rastrear avances.
- Documentar cambios en commits descriptivos.
- Revisar y limpiar `Sandbox/Temps/` semanalmente.
- Registrar descripciones y dependencias de archivos en `registro-archivos.md`.
- Gestionar bases de datos según `base-datos.md` para conexiones seguras y arquitectura evolutiva.
