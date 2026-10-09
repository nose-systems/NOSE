# Guía de contribución

Gracias por contribuir a NOSE. Esta guía describe cómo preparar el entorno de trabajo, organizar los cambios y proponerlos para revisión.

## Tabla de contenido

- [Antes de empezar](#antes-de-empezar)
- [Estrategia y nomenclatura de ramas](#estrategia-y-nomenclatura-de-ramas)
- [Flujo de trabajo](#flujo-de-trabajo)
- [Mensajes de commit](#mensajes-de-commit)
- [Pull Requests](#pull-requests)
- [Revisión e integración](#revisión-e-integración)
- [Contratos compartidos](#contratos-compartidos)

## Antes de empezar

Lee el [README](README.md) y, cuando el cambio lo requiera, consulta la arquitectura y los contratos de API del proyecto. Antes de comenzar, identifica el issue o la tarea relacionada para mantener el alcance del cambio claro.

Si aún no tienes una copia local del repositorio:

```bash
git clone https://github.com/nose-systems/NOSE.git
cd NOSE
```

## Estrategia y nomenclatura de ramas

Las ramas de trabajo se crean desde `develop` y se integran a `develop` mediante Pull Request. `main` y `develop` están protegidas: no hagas commits directamente en ellas.

| Prefijo | Uso | Ejemplo |
| --- | --- | --- |
| `feature/<squad>-<descripcion>` | Nueva funcionalidad | `feature/cerebritos-post-decisions` |
| `fix/<descripcion>` | Corrección de un error | `fix/veto-limite-tres` |
| `docs/<descripcion>` | Cambio de documentación | `docs/adr-plataforma` |

Los squads de NOSE son `dictadores`, `cerebritos` y `pixelados`. Usa minúsculas y separa las palabras con guiones; procura que la descripción sea breve y clara.

## Flujo de trabajo

Actualiza `develop` y crea una rama para tu cambio:

```bash
git switch develop
git pull --ff-only origin develop
git switch -c feature/cerebritos-post-decisions
```

Sustituye el nombre de ejemplo por el que corresponda, según la convención de ramas. Implementa el cambio en commits pequeños y coherentes. Al terminar, publica la rama:

```bash
git push -u origin feature/cerebritos-post-decisions
```

Para las siguientes actualizaciones de esa misma rama, basta con `git push`.

## Mensajes de commit

NOSE utiliza una versión sencilla de Conventional Commits:

| Prefijo | Cuándo usarlo |
| --- | --- |
| `feat` | Nueva funcionalidad |
| `fix` | Corrección de un error |
| `docs` | Cambios únicamente de documentación |
| `refactor` | Cambio interno que no altera el comportamiento |
| `test` | Agregar o corregir pruebas |
| `chore` | Mantenimiento, configuración o dependencias |

Formato: `tipo: descripción breve en minúscula`.

```text
feat: agregar endpoint POST /decisions
fix: limitar los intentos de veto
docs: documentar la arquitectura de identidad
```

Cada commit debe representar un cambio coherente. Evita mensajes genéricos como `update`, `arreglo` o `wip`, y no incluyas secretos, tokens, credenciales ni archivos `.env`.

## Pull Requests

Todo cambio destinado a `develop` debe proponerse mediante un Pull Request. Abre el PR en GitHub usando la [plantilla de Pull Request](.github/PULL_REQUEST_TEMPLATE.md) y confirma que incluya:

- Una descripción de qué cambia y por qué.
- El issue relacionado, si existe.
- Cómo se probó o validó el cambio.
- Evidencia visual cuando el cambio afecte la interfaz.
- La documentación actualizada cuando corresponda.

Mantén el PR enfocado en una tarea y comprueba que la rama y los commits sigan las convenciones de esta guía.

## Revisión e integración

- `main` y `develop` no aceptan commits directos.
- Los Pull Requests hacia `develop` requieren al menos una aprobación de una persona del squad `dictadores`, que revisa los cambios por defecto según la configuración del repositorio.
- Atiende los comentarios de revisión y actualiza la misma rama del PR.
- Los cambios se integran mediante **squash merge**.
- Después de la integración, la rama de trabajo se elimina automáticamente.

## Contratos compartidos

Si el cambio afecta endpoints, DTO, estructuras de datos, estados, enums o interfaces compartidas entre backend y frontend, comunícalo en el issue o PR antes de implementarlo y coordínalo con los squads involucrados. Actualiza también el contrato de API en `docs/api/openapi.yaml` cuando corresponda.
