# Alcance del MVP: NOSE Qué Comer

<!-- markdownlint-disable MD013 -->

> Fuentes: Informe NOSE_HS (secciones 7, 11, 12, 13 y 14) y Plan de sprints Fase 1 (hojas Backlog, GitHub y Hallazgos).
> Issue: #5 · Ticket del plan: 0.4 · Responsable: Dictadores

## 1. Objetivo del MVP

Demostrar que una persona puede entrar con una indecisión sobre qué comer, recibir una decisión útil en pocos segundos y volver a delegar otra.
El flujo central es: **necesidad → contexto mínimo → una opción principal → aceptar/vetar → feedback**.

**Relación con el roadmap del informe (sección 13):**

| Fase del informe | Qué cubre en este plan |
| --- | --- |
| 0 · Fundaciones | Sprint 0 |
| 1 · MVP | Sprints 1 a 3 (este documento) |
| 1.5 · Validación con usuarios reales | Fuera de los 4 sprints. Se planifica cuando el MVP esté demostrable |
| 2 en adelante | Diferido (ver sección 4) |

## 2. Actores

| Actor | Rol en el MVP |
| --- | --- |
| Usuario final | Expresa su necesidad, recibe una recomendación, acepta o veta, acumula XP y racha |
| Administrador / equipo | Mantiene el catálogo inicial (vía seed) y consulta métricas |
| Sistema (motor de decisión) | Puntúa candidatos, explica la elección y aplica el fallback |

## 3. Procesos incluidos

| # | Proceso | Tickets |
| --- | --- | --- |
| P1 | Entrada de necesidad (texto libre + accesos rápidos) | 0.14, 1.7 |
| P2 | Contexto mínimo (presupuesto, tiempo, ubicación, compañía; solo si aporta valor) | 1.7 |
| P3 | Una recomendación principal con explicación breve | 1.4, 1.5, 2.5 |
| P4 | Aceptar / Vetar (máx. 3 vetos, con motivo) | 2.1, 2.2, 2.5 |
| P5 | XP y racha | 2.2, 2.3, 3.4 |
| P6 | Analítica (eventos y métricas, incl. Time to Value) | 2.4, 3.3 |
| P7 | Preferencias persistentes y aprendizaje v0 | 1.3, 3.1, 3.2 |

## 4. Clasificación de historias de usuario

**Estados:**

- **Incluida:** se construye en la Fase 1 (Sprints 0 a 3).
- **Diferida:** está en el roadmap, pero en una fase posterior.
- **Fuera del MVP:** no se construye en la Fase 1 y no tiene fase asignada.

| US | Nombre | Épica | Prioridad | Estado | Sprint / motivo | Tickets |
| --- | --- | --- | --- | --- | --- | --- |
| US-01 | Inicio rápido | E1 | Crítica | Incluida | Sprint 1 | 0.14, 1.7 |
| US-02 | Lenguaje natural | E1 | Alta | Incluida | Sprint 1. Captura de texto libre; la intención se interpreta por reglas/palabras clave | 1.7, 1.5 |
| US-03 | Contexto mínimo | E1 | Crítica | Incluida | Sprint 1 | 1.7 |
| US-04 | Qué Comer | E2 | Crítica | Incluida | Sprint 1 | 1.2, 1.4, 1.5 |
| US-05 | Recomendación principal | E2 | Crítica | Incluida | Sprint 1 (API), Sprint 2 (UI) | 1.4, 2.5 |
| US-06 | Aceptar | E2 | Crítica | Incluida | Sprint 2. La aceptación se registra; no hay acción externa posterior | 2.2, 2.5 |
| US-07 | Vetar | E2 / E3 | Crítica | Incluida | Sprint 2 | 2.1, 2.5 |
| US-08 | Aprendizaje | E2 / E3 | Alta | Incluida | Sprint 3 | 3.2 |
| US-09 | Preferencias | E2 / E3 | Alta | Incluida | Sprint 1 (básico), Sprint 3 (editable) | 1.3, 3.1 |
| US-10 | Explicación | E2 / E3 | Alta | Incluida | Sprint 1 (motor), Sprint 2 (UI) | 1.5, 2.5 |
| US-11 | Time to Value | E3 | Alta | Incluida | Sprint 2 (eventos), Sprint 3 (métrica) | 2.4, 3.3 |
| US-12 | DICE | E4 | Media | Diferida ⚠️ | Fase 2+. Solo microcopy si sobra tiempo | F.1 |
| US-13 | XP y racha | E4 | Media | Incluida | Sprint 2 (API), Sprint 3 (UI) | 2.2, 2.3, 3.4 |
| US-14 | Botón del Caos | E4 | Media | Diferida | Fase 3 (Social). Requiere más de un módulo | F.2 |
| US-15 | Parejas y grupos | E4 | Media | Diferida | Fase 3 (Social) | F.3 |
| US-16 | Base de candidatos | E5 | Alta | Incluida | Sprint 1, solo por seed. Sin interfaz de administración | 1.2 |
| US-17 | Fallback | E5 | Alta | Incluida | Sprint 1 (motor), Sprint 3 (QA) | 1.5, 3.6 |
| US-18 | Analítica | E5 | Crítica | Incluida | Sprint 2 y Sprint 3 | 2.4, 3.3 |
| US-19 | Privacidad | E5 | Crítica | Incluida | Sprint 3 (consentimiento), apoyado en Sprint 1 | 1.3, 3.1 |
| US-20 | Módulos extensibles | E5 | Alta | Incluida como arquitectura | Solo como principio de diseño (motor genérico). No se implementa ningún otro módulo | 0.12, 1.5, 2.7 |
| US-21 | Qué Ver | E6 | Futura | Diferida | Fase 2 (Frecuencia) | F.4 |
| US-22 | A Dónde Ir | E6 | Futura | Diferida | Fase posterior a la 2 (el roadmap no fija fase exacta) | F.4 |
| US-23 | Estudio | E6 | Futura | Diferida | Fase 2 (Frecuencia) | F.4 |
| US-24 | Acción externa | E6 | Futura | Diferida | Fase 4 (Transacción). Requiere integraciones | F.5 |

**Resumen:** 17 incluidas · 7 diferidas · 0 fuera del MVP.

> Nota: en el informe, las épicas E2 y E3 comparten las US-07 a US-10. Aquí se marcan con ambas.

### Condicionado (stretch)

| Elemento | Estado | Motivo |
| --- | --- | --- |
| 3.5 Módulo de partners (CRUD) | Stretch, solo si sobra tiempo | La validación inicial no depende de acuerdos comerciales |
| 2.8 Plan de staging | Prioridad baja | No bloquea el MVP local |

## 5. Pantalla principal: qué entra y qué no

El informe (sección 4) describe una pantalla con más elementos de los que cubre el MVP:

| Elemento del informe | Estado en el MVP |
| --- | --- |
| Pregunta central «¿Qué necesitas decidir?» y entrada libre | Incluido |
| Acceso rápido **Comer** | Incluido |
| Accesos rápidos Ver, Salir/Hacer, Estudiar ⚠️ | Solo visuales o no mostrados; sin lógica (módulos diferidos) |
| Botón CAOS | Fuera de la pantalla del MVP (se identifica como futuro en los wireframes 0.14) |
| Aceptar / Vetar, explicación, indicador de patrocinio | Incluido |
| «+10 XP» y racha tras decidir | Incluido |

## 6. Métricas del informe (sección 14)

| Métrica | Estado | Ticket |
| --- | --- | --- |
| Activation Rate | Incluida | 3.3 |
| Decision Completion Rate | Incluida | 3.3 |
| Veto Rate | Incluida | 3.3 |
| Time to Value | Incluida | 2.4, 3.3 |
| Time to Decision ⚠️ | Diferida a la Fase 1.5 | Los eventos de 2.4 permiten calcularla después |
| Decisiones por usuario ⚠️ | Diferida a la Fase 1.5 | Los eventos de 2.4 permiten calcularla después |
| Retención D1 / D7 / D30 | Diferida a la Fase 1.5 | Requiere usuarios reales durante varios días |
| Share Rate | Diferida | No hay función de compartir en el MVP |

## 7. Supuestos y exclusiones

### Supuestos

1. La plataforma es web (React + Vite), según el ADR de 0.5.
2. El motor es por reglas, no IA compleja (informe, sección 7).
3. El catálogo inicial tiene 15-20 ítems reales cargados por seed.
4. La identidad de usuario es mínima, según el ADR de 0.5.
5. Se acepta un máximo aproximado de 2-3 interacciones hasta una recomendación (objetivo a validar con usuarios).
6. El flag `is_sponsored` y el tope de `sponsorship_weight` existen en el motor, pero no hay partners reales.

### Exclusiones

- Sin acuerdos comerciales ni monetización.
- Sin acciones externas (reservar, pedir, pagar, reproducir).
- Sin otros módulos aparte de comida (Qué Ver, A Dónde Ir, Estudio).
- Sin Botón del Caos ni modo parejas/grupos.
- Sin DICE como personaje (solo microcopy opcional).
- Sin panel de administración de catálogo.
- Sin integraciones externas (mapas, clima, streaming).

## 8. Cómo saber si un ticket está fuera de alcance

Un ticket nuevo está **fuera de alcance** si responde "sí" a cualquiera de estas preguntas:

1. ¿Depende de un acuerdo comercial o de una integración externa?
2. ¿Trata de un módulo distinto de Qué Comer?
3. ¿Corresponde a una US marcada como Diferida?
4. ¿No aparece en ningún proceso P1-P7 ni en el plan de sprints?
Si es así, no se construye; se registra como propuesta para una fase posterior.

## 9. Definition of Done común

Un ticket está terminado cuando:

- [ ] Cumple todos sus criterios de aceptación.
- [ ] Está en el alcance de este documento (la US figura como Incluida).
- [ ] El PR usa la plantilla y referencia el issue.
- [ ] La CI está en verde (lint, typecheck, tests y build).
- [ ] Tiene al menos 1 aprobación de Dictadores.
- [ ] Incluye tests cuando hay lógica (unitarios, integración o E2E según el ADR de pruebas).
- [ ] La documentación afectada está actualizada (README, OpenAPI, `docs/`).
- [ ] No incluye secretos ni credenciales.
- [ ] Se integra por squash merge y la rama se elimina.

> La Definition of Done técnica detallada se define en el ticket 0.18 y no debe contradecir esta lista.

## 10. Aprobación

El alcance requiere aprobación del squads definido.

| Squad | Integrantes | Aprobó | Fecha |
| --- | --- | --- | --- |
| Dictadores | Patrick, Estefani | | |
