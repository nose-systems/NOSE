<!-- markdownlint-disable MD033 MD041 -->

<div align="center">

<h1>NOSE — No busques. NOSE.</h1>

<p><strong>La app que decide por ti cuando tú no sabes qué hacer.</strong></p>

<p>Motor de decisiones cotidianas · Marketplace contextual · Gamificación</p>

<p>
  <a href="ARCHITECTURE.md">Arquitectura</a> ·
  <a href="Propuesta.pdf">Propuesta NOSE</a> ·
  <a href="CONTRIBUTING.md">Contribuir</a>
</p>

</div>

<!-- markdownlint-enable MD033 MD041 -->

## ¿Qué es NOSE?

## Genesis del Proyecto

## Problema que resuelve

## Propuesta de valor

## Arquitectura resumida

## Stack tecnológico

| Área            | Herramienta                                   |
| --------------- | --------------------------------------------- |
| Lenguaje        | TypeScript (backend y frontend)               |
| Backend         | Node.js + Express                             |
| Base de datos   | PostgreSQL + Prisma (migraciones y seed)      |
| Frontend        | React + Vite                                  |
| Contrato de API | OpenAPI + Swagger UI                          |
| Entorno         | Docker + Docker Compose                       |
| Calidad         | ESLint, Prettier, Husky, lint-staged          |
| Pruebas         | Vitest (unitarias), Supertest (integración), Playwright (E2E) |
| CI              | GitHub Actions (lint + typecheck + tests + build en cada PR) |
| Dependencias    | Dependabot                                    |
| Diseño          | Figma                                         |

## Estructura del repositorio

> Estructura prevista. Los detalles finales quedan registrados en el ADR de estructura del repositorio.

```text
NOSE/
├── .github/
│   ├── ISSUE_TEMPLATE/          # plantilla de historia/ticket
│   ├── workflows/               # CI de Pull Requests
│   ├── CODEOWNERS
│   ├── dependabot.yml
│   └── pull_request_template.md
│
├── backend/
│   ├── prisma/                  # schema.prisma, migraciones y seed
│   ├── src/
│   │   ├── config/              # variables de entorno
│   │   ├── core/                # middlewares, errores, utilidades
│   │   ├── engine/              # motor de decisión (scoring, contexto, fallback)
│   │   └── modules/
│   │       ├── decisions/       # POST /decisions, /veto, /accept
│   │       ├── catalog/         # candidatos (Qué Comer)
│   │       ├── users/           # usuario mínimo, /stats
│   │       ├── preferences/     # preferencias y consentimiento
│   │       ├── analytics/       # eventos y métricas
│   │       └── partners/        # STRETCH (Sprint 3)
│   └── tests/
│
├── frontend/
│   └── src/
│       ├── components/
│       ├── features/            # input, resultado, preferencias, XP/racha
│       ├── hooks/
│       ├── pages/
│       ├── services/            # cliente HTTP (mock ↔ API real)
│       └── types/
│
├── docs/
│   ├── adr/                     # decisiones técnicas
│   ├── api/
│   │   └── openapi.yaml         # contrato único Backend ↔ Frontend
│   ├── ARCHITECTURE.md
│   ├── DATA_MODEL.md            # modelo ER y diccionario de datos
│   ├── MVP_SCOPE.md             # alcance, DoD y trazabilidad US → sprint
│   └── SCORING.md               # diseño del motor y casos de ejemplo
│
├── tests/
│   └── e2e/                     # Playwright
│
├── docker-compose.yml           # Postgres + backend + frontend
├── .env.example
├── CONTRIBUTING.md
└── README.md
```
