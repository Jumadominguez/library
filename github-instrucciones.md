# Instrucciones para Uso Correcto y Eficiente de GitHub

Este documento proporciona guías detalladas para utilizar Git y GitHub de manera eficiente en proyectos con Vibe Coding. Enfocado en un sistema robusto de commits y branches para facilitar reversiones, tracking y colaboración.

## Introducción a Git y GitHub

Git es un sistema de control de versiones que permite rastrear cambios en el código. GitHub es la plataforma para alojar repositorios, colaborar y gestionar proyectos. En Vibe Coding, usamos Git como checkpoints para preservar avances funcionales y revertir fallos sin perder trabajo.

- **Repositorio**: Espacio donde se almacena el código y su historial.
- **Commit**: Instantánea de cambios, usado como checkpoint.
- **Branch**: Rama independiente para desarrollar features sin afectar el código principal.
- **Merge/Pull Request**: Integrar cambios de una branch a otra, con revisión.

## Sistema de Commits

Los commits son checkpoints críticos. Cada commit debe representar un avance funcional o una corrección, permitiendo reversiones precisas.

### Convenciones de Mensajes de Commit
Usa mensajes descriptivos y estandarizados para identificar fácilmente el proceso. Incluye nomenclatura numérica para versionado y fácil referencia.

- **Formato**: `[Tipo][Número] Descripción breve (máx. 50 chars)`
  - Ejemplos:
    - `[FEAT-001] Agregar autenticación de usuario`
    - `[FIX-002] Corregir error en login`
    - `[REFACTOR-003] Optimizar código de API`
    - `[DOC-004] Actualizar documentación de puertos`
    - `[TEST-005] Agregar tests para nueva feature`
    - `[CHECKPOINT-006] Guardar progreso en Experiments`

- **Nomenclatura Numérica**:
  - **[Número]**: Contador incremental por tipo o feature (e.g., FEAT-001, FEAT-002 para features consecutivas).
  - Para branches específicas: Usa prefijo de branch (e.g., en `feature/auth`, commits como [AUTH-001], [AUTH-002]).
  - Global: Mantén un contador en un archivo como `docs/commit-counter.txt` y actualízalo con cada commit.
  - Facilita referencias: "Revierte a [FEAT-005]" en lugar de hashes largos.

- **Tipos Comunes**:
  - `[FEAT]`: Nueva funcionalidad.
  - `[FIX]`: Corrección de bugs.
  - `[REFACTOR]`: Mejora de código sin cambiar funcionalidad.
  - `[DOC]`: Cambios en documentación.
  - `[TEST]`: Agregar o modificar tests.
  - `[CHECKPOINT]`: Guardar estado en Experiments/Prototypes.
  - `[MERGE]`: Integración de branches.

- **Frecuencia**: Commit después de completar una tarea pequeña o al final de una sesión. Evita commits grandes; divide en lógicos.
- **Uso como Checkpoints**: Antes de experimentar, commit con `[CHECKPOINT-XXX] Inicio de experimento X`. Si falla, revierte con `git reset --hard <commit-hash>` o `git revert`.

### Comandos Básicos para Commits
- `git add .` o `git add <archivo>`: Agregar cambios al staging.
- `git commit -m "[TIPO] Mensaje"` : Crear commit.
- `git log --oneline`: Ver historial de commits.
- `git reset --soft <commit>`: Deshacer commit pero mantener cambios.
- `git reset --hard <commit>`: Deshacer commit y cambios (usar con cuidado).

## Sistema de Branches

Branches permiten desarrollar en paralelo sin afectar el código principal. Usa una estrategia clara para identificar procesos fácilmente.

### Estrategia Recomendada
- **main**: Código de producción estable. Solo merges probados.
- **develop**: Rama de desarrollo, integra features completadas.
- **feature/[nombre]**: Para nuevas features (e.g., `feature/auth-user`).
- **experiment/[nombre]**: Para pruebas en `Sandbox/Experiments` (e.g., `experiment/new-api`).
- **prototype/[nombre]**: Para validaciones en `Sandbox/Prototypes` (e.g., `prototype/user-dashboard`).
- **hotfix/[issue]**: Para correcciones urgentes (e.g., `hotfix/login-bug`).

### Flujo de Trabajo
1. Desde `develop`, crea una branch para la tarea: `git checkout -b feature/nueva-feature`.
2. Desarrolla y commit con frecuencia.
3. Al completar, merge a `develop` via Pull Request (PR) en GitHub.
4. Para Experiments/Prototypes: Crea branches específicas y commit checkpoints.
5. Revisa y aprueba PRs antes de merge a `main`.

### Comandos para Branches
- `git branch`: Listar branches.
- `git checkout <branch>` o `git switch <branch>`: Cambiar branch.
- `git checkout -b <nueva-branch>`: Crear y cambiar.
- `git merge <branch>`: Integrar branch (desde la actual).
- `git branch -d <branch>`: Eliminar branch local.
- `git push origin <branch>`: Subir branch a GitHub.

## Integración con Sandbox

- **Incluir en Git**: `Sandbox/Experiments/` y `Sandbox/Prototypes/` se commitean para rastrear experimentos y prototipos. Útil para compartir avances o revertir.
- **Ignorar**: `Sandbox/Debug/` y `Sandbox/Temps/` quedan en `.gitignore` para evitar ruido (archivos temporales de debugging).
- **Actualización de .gitignore**:
  ```
  Sandbox/Debug/
  Sandbox/Temps/
  venv/
  node_modules/
  __pycache__/
  *.log
  .env
  ```

- **Flujo en Sandbox**:
  - Desarrolla en `Experiments/`, commit con `[CHECKPOINT]`.
  - Al validar, mueve a `Prototypes/` y commit en branch `prototype/`.
  - Integra a `develop` solo lo aprobado.

## Flujo Completo con Vibe Coding

1. **Setup Inicial**: Crea repo en GitHub, clona, configura `.gitignore` (ver arriba).
2. **Desarrollo**: Crea branch `feature/`, desarrolla en `Sandbox/Experiments/`, commit checkpoints.
3. **Validación**: Mueve a `Sandbox/Prototypes/`, crea branch `prototype/`, commit.
4. **Integración**: PR a `develop`, luego a `main` si es producción.
5. **Reversión**: Si falla, usa `git reset` o `git revert` a un checkpoint.
6. **Colaboración**: Usa Issues y PRs en GitHub para tracking.

## Comandos Útiles y Mejores Prácticas

- **Ver Cambios**: `git status`, `git diff`.
- **Resolver Conflictos**: Edita archivos, `git add`, `git commit`.
- **Push/Pull**: `git push origin <branch>`, `git pull origin <branch>`.
- **Mejores Prácticas**:
  - Commit temprano y menudo.
  - Usa branches para aislamiento.
  - Revisa PRs para calidad.
  - Documenta en commits el proceso (e.g., referencia a `proceso.md`).
  - Evita force push en branches compartidas.

## Referencias

- Consulta `instrucciones-globales.md` para reglas generales.
- Integra con `sandbox.md` para flujo de experimentación.
- Actualiza `proceso.md` con fases de desarrollo.

Siguiendo estas instrucciones, GitHub se convierte en una herramienta poderosa para versionado y checkpoints en Vibe Coding.
