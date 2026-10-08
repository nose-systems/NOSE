# Guía de contribución

## Flujo de trabajo
1. Crea una rama desde `develop`.
2. Haz tus cambios con commits pequeños.
3. Abre un Pull Request hacia `develop` usando la plantilla.
4. Necesitas mínimo 1 aprobación de Dictadores.
5. Se integra con **squash merge** y la rama se borra automáticamente.

`main` y `develop` están protegidas: no se hace commit directo.

## Convención de ramas
| Prefijo | Uso | Ejemplo |
| --- | --- | --- |
| `feature/<squad>-<descripcion>` | Nueva funcionalidad | `feature/cerebritos-post-decisions` |
| `fix/<descripcion>` | Corrección de bugs | `fix/veto-limite-tres` |
| `docs/<descripcion>` | Documentación | `docs/adr-plataforma` |

Squads: `dictadores`, `cerebritos`, `pixelados`.

## Conventional Commits
Formato: `tipo: descripción corta en minúscula`

| Prefijo | Cuándo |
| --- | --- |
| `feat` | Nueva funcionalidad |
| `fix` | Corrección de un bug |
| `docs` | Solo documentación |
| `refactor` | Cambio interno sin alterar comportamiento |
| `test` | Agregar o corregir tests |
| `chore` | Tareas de mantenimiento, configuración |

Ejemplos: `feat: agregar endpoint POST /decisions`, `docs: redactar ADR de identidad`.
