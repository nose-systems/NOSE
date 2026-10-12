# NOSE — Registro de decisiones de arquitectura (ADR)

Este documento reúne las nueve decisiones de arquitectura acordadas por el equipo de NOSE. Cada registro presenta el contexto, la decisión tomada, las alternativas consideradas, la justificación y las consecuencias.

## Índice

1. [ADR-001 — Plataforma cliente](#adr-001--plataforma-cliente)
2. [ADR-002 — Backend con Node.js y NestJS](#adr-002--backend-con-nodejs-y-nestjs)
3. [ADR-003 — PostgreSQL como base de datos principal](#adr-003--postgresql-como-base-de-datos-principal)
4. [ADR-004 — TypeScript para el desarrollo](#adr-004--typescript-para-el-desarrollo)
5. [ADR-005 — Identidad mediante proveedor externo](#adr-005--identidad-mediante-proveedor-externo)
6. [ADR-006 — Monorepo con límites estrictos](#adr-006--monorepo-con-límites-estrictos)
7. [ADR-007 — Estrategia de pruebas](#adr-007--estrategia-de-pruebas)
8. [ADR-008 — Entorno local con Docker Compose](#adr-008--entorno-local-con-docker-compose)
9. [ADR-009 — Gestión del catálogo](#adr-009--gestión-del-catálogo)

---

## ADR-001 — Plataforma cliente

**Estado:** Aceptado por el equipo.

### Contexto

NOSE necesita una experiencia principal móvil y un punto de entrada desde computadores para que las personas conozcan el producto y accedan a su descarga.

### Decisión

Desarrollar una aplicación móvil y una landing page web desde la que se pueda acceder a la información de NOSE y a los enlaces de descarga.

### Alternativas consideradas

- Aplicación web adaptable como producto principal.
- Aplicación móvil sin landing page.
- Aplicación móvil acompañada de una landing page.

### Justificación

La opción acordada prioriza la experiencia móvil y ofrece un punto de entrada para quienes descubran el producto desde un navegador de escritorio.

### Consecuencias y asuntos pendientes

Se deberán definir las plataformas móviles objetivo, el proceso de publicación y los enlaces de descarga. La landing page no se considera una versión completa de la aplicación.

---

## ADR-002 — Backend con Node.js y NestJS

**Estado:** Aceptado por el equipo.

### Contexto

NOSE necesita una API que gestione la lógica del producto y conecte la aplicación con la persistencia y otros servicios.

### Decisión

Utilizar Node.js con NestJS para implementar el backend.

### Alternativas consideradas

- Node.js con Express.
- Node.js con Fastify.
- Backend gestionado o BaaS.

### Justificación

NestJS ofrece una estructura modular y convenciones para organizar las responsabilidades del backend, lo que puede facilitar su mantenimiento y evolución.

### Consecuencias

El equipo deberá seguir las convenciones de NestJS, definir módulos y responsabilidades claras, y mantener las dependencias y la configuración del servidor.

---

## ADR-003 — PostgreSQL como base de datos principal

**Estado:** Aceptado por el equipo.

### Contexto

NOSE necesita persistir información relacionada con perfiles, preferencias, catálogo, recomendaciones, feedback y progreso.

### Decisión

Utilizar PostgreSQL como base de datos principal.

### Alternativas consideradas

- MongoDB.
- Una base de datos gestionada por un proveedor.

### Justificación

PostgreSQL permite modelar relaciones entre entidades, aplicar restricciones de integridad y realizar consultas transaccionales sobre los datos del producto.

### Consecuencias

El equipo deberá definir el modelo relacional, administrar las migraciones y establecer estrategias de respaldo, configuración y acceso a la base de datos.

---

## ADR-004 — TypeScript para el desarrollo

**Estado:** Aceptado por el equipo.

### Contexto

NOSE necesita mantener una base de código comprensible y reducir errores derivados de inconsistencias en los tipos de datos.

### Decisión

Utilizar TypeScript en las partes del sistema que lo soporten, conforme al stack acordado.

### Alternativas consideradas

- JavaScript con validación en tiempo de ejecución.
- TypeScript con generación de tipos a partir de contratos OpenAPI.

### Justificación

TypeScript aporta comprobación estática de tipos y permite establecer convenciones comunes de desarrollo.

### Consecuencias

Se deberán configurar las herramientas de compilación y comprobación de tipos. La validación de los datos recibidos en tiempo de ejecución seguirá siendo necesaria, ya que TypeScript por sí solo no valida entradas externas.

---

## ADR-005 — Identidad mediante proveedor externo

**Estado:** Aceptado por el equipo.

### Contexto

NOSE necesita asociar el perfil del usuario con sus preferencias y progreso, procurando evitar una gestión innecesaria de credenciales propias.

### Decisión

Utilizar un proveedor de identidad externo para la autenticación. El proveedor concreto y los métodos admitidos deberán especificarse en la configuración del proyecto.

### Alternativas consideradas

- Perfil anónimo por navegador.
- Cuenta con correo y contraseña gestionada por NOSE.
- No mantener un perfil persistente.

### Justificación

Delegar la autenticación puede reducir la responsabilidad de gestionar directamente contraseñas y facilitar el acceso a la cuenta.

### Consecuencias y asuntos pendientes

Será necesario integrar y configurar el proveedor, gestionar errores y vincular de forma segura la identidad autenticada con el perfil de NOSE. También deberán definirse la privacidad, los permisos y el comportamiento si el proveedor no está disponible.

---

## ADR-006 — Monorepo con límites estrictos

**Estado:** Aceptado por el equipo.

### Contexto

NOSE contiene componentes con responsabilidades distintas que deben evolucionar de forma coordinada sin mezclar sus responsabilidades.

### Decisión

Mantener el código del proyecto en un monorepo y establecer límites claros entre aplicaciones, módulos y responsabilidades.

### Alternativas consideradas

- Monorepo sin límites explícitos.
- Repositorios separados para cada componente.

### Justificación

Un único repositorio facilita revisar cambios coordinados, mientras que los límites explícitos ayudan a mantener la separación entre componentes.

### Consecuencias

El equipo deberá definir la estructura de carpetas, las reglas de dependencias, los comandos, los procesos de integración continua (CI) y las responsabilidades de cada componente. La existencia de carpetas por sí sola no garantiza esos límites.

---

## ADR-007 — Estrategia de pruebas

**Estado:** Aceptado por el equipo.

### Contexto

NOSE necesita comprobar su comportamiento y proteger las funcionalidades críticas a medida que evoluciona.

### Decisión

Priorizar las pruebas según el riesgo funcional y complementar las pruebas automatizadas con pruebas manuales exploratorias.

### Alternativas consideradas

- Utilizar la pirámide de pruebas como estrategia principal.
- Dar prioridad a pruebas de contratos de API, integración y extremo a extremo (E2E).
- Realizar pruebas manuales sin una estrategia automatizada basada en riesgos.

### Justificación

La priorización por riesgos centra la cobertura en comportamientos cuyo fallo tendría mayor impacto, mientras que la exploración manual ayuda a detectar problemas de usabilidad y escenarios inesperados.

### Consecuencias

Se deberán identificar y revisar los riesgos, documentar escenarios críticos y definir qué pruebas se automatizan. Las pruebas manuales complementan, pero no sustituyen, las pruebas automatizadas repetibles.

### Áreas críticas iniciales

- Puntuación y selección de recomendaciones.
- Respuesta alternativa cuando no hay coincidencias (fallback).
- Aceptar o vetar una recomendación.
- Persistencia de preferencias y progreso.
- Manejo de errores de la API.

---

## ADR-008 — Entorno local con Docker Compose

**Estado:** Aceptado por el equipo.

### Contexto

Los integrantes necesitan un entorno de desarrollo reproducible y una forma consistente de ejecutar los servicios que requiere NOSE.

### Decisión

Utilizar Docker Compose para definir y ejecutar los servicios locales necesarios para el desarrollo.

### Alternativas consideradas

- Instalar todos los servicios directamente en cada máquina.
- Ejecutar la aplicación localmente y algunos servicios en contenedores.
- Usar un entorno remoto de desarrollo.

### Justificación

Docker Compose permite describir los servicios y su configuración en archivos versionados, reduciendo las diferencias entre entornos de desarrollo.

### Consecuencias y asuntos pendientes

Se deberá mantener el archivo de Compose, documentar las variables de entorno y los puertos, definir la persistencia de datos y evitar guardar secretos en el repositorio. Las versiones concretas de Node.js y PostgreSQL deben alinearse con la configuración que acuerde el equipo.

---

## ADR-009 — Gestión del catálogo

**Estado:** Aceptado por el equipo.

### Contexto

NOSE necesita un catálogo inicial de opciones de comida para que el motor de recomendación consulte datos controlados. El alcance acordado no incluye un panel administrativo para gestionar ese catálogo.

### Decisión

Mantener el catálogo en un archivo versionado y validado en el repositorio, y cargar sus datos en la base de datos mediante un proceso de seed.

### Alternativas consideradas

- Mantener el catálogo únicamente en la base de datos mediante seeds.
- Consultar directamente un archivo versionado durante la ejecución.
- Administrar los cambios mediante scripts sin un archivo fuente versionado.

### Justificación

El archivo facilita revisar y versionar cambios en el contenido, mientras que la base de datos permite que la aplicación consulte el catálogo junto con el resto de los datos.

### Consecuencias y asuntos pendientes

Se deberá definir el formato del archivo, validar sus datos y mantener el proceso de seed reproducible e idempotente para evitar duplicados o modificaciones accidentales. También habrá que establecer cómo se aplican las actualizaciones y cómo se manejan los registros retirados del catálogo.