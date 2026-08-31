<div align="center">

# Erick Gutiérrez

### Full Stack Developer (HealthTech) · QA Analyst en Sistemas de Pago Bancario

React · NestJS · Node · PostgreSQL — Postilion · ISO 8583 · BRE-B — Desarrollo asistido por agentes

Colombia 🇨🇴 · 100% remoto

<sub>Full stack developer in health tech with 2+ years of QA in banking payment systems. Available for remote roles.</sub>

[![Portfolio](https://img.shields.io/badge/erickgutierrez.dev-0E2742?style=flat-square&logo=vercel&logoColor=white)](https://erickgutierrez.dev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0E7C82?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/erick-guti%C3%A9rrez-8b4289248)
[![Email](https://img.shields.io/badge/Email-8A93A0?style=flat-square&logo=gmail&logoColor=white)](mailto:erickgutierrez085@gmail.com)

</div>

---

## Sobre mí

Desarrollador **Full Stack en GoEcosystem Digital Health**, donde trabajo sobre un ecosistema clínico multi-tenant: React 19 + NestJS para producto nuevo, PHP/CodeIgniter 3 sobre PostgreSQL para los módulos heredados.

Antes, más de **2 años como QA Analyst en el sector financiero** certificando proyectos de alta criticidad para las 5 entidades del Grupo Aval: **BRE-B/SPI** y **PSE Avanza**, sobre Postilion, ISO 8583 y Base24.

Esa combinación es lo que define cómo trabajo: escribo producto con el criterio de alguien acostumbrado a romperlo antes de que llegue a producción.

Estudiante de Ingeniería de Sistemas en UNISANGIL · Tecnólogo ADSO (SENA) · T.P. COPNIA 154145-0770760.

---

## Cómo trabajo

**Desarrollo asistido por agentes.** Claude Code como vehículo principal de desarrollo, no como autocompletado. El principio es simple: *la IA programa, yo desarrollo* — la velocidad la pone el modelo, el criterio y la responsabilidad del código que entra a producción son míos.

Lo concreto y verificable en mis repos:

- **`CLAUDE.md` por repositorio bajo 200 líneas** como contrato con el agente: comandos, decisiones de arquitectura y gotchas. Un archivo más largo consume contexto y degrada la adherencia a instrucciones.
- **Reglas duras versionadas en `.claude/rules/`** (tenant-scoping, migraciones, nomenclatura). Las invariantes que el agente no puede violar viven en git, no en la memoria de una conversación.
- **Dos subagentes propios:** `business-logic-validator` (ciclo obligatorio *analizar → preguntar → proponer*, para que el agente nunca asuma reglas de negocio) y `ui-ux-designer`.
- **Integración de servidores MCP** (PostgreSQL/Supabase, Playwright, Obsidian, Azure DevOps) y estudio de su superficie de ataque: las salidas de una herramienta son datos no confiables.
- **`evals/` vs `tests/`:** lo determinista se testea; el comportamiento de un agente ante cambios de prompt o modelo se evalúa. No son lo mismo.

**Prácticas de ingeniería:** SQL parametrizado sin ORM · migraciones expand-contract e idempotentes · aislamiento por tenant tomado del token, nunca del cliente · Conventional Commits + PR con checklist · ADRs para lo que alguien va a cuestionar en seis meses.

---

## Stack

**Desarrollo**
TypeScript · JavaScript (ESM/CJS) · PHP · Python · Java
React 19 · Next.js (App Router) · Vite · Tailwind v4 · MUI · TanStack Query · Zustand · Zod
NestJS 11 · Express 5 · Node ≥20 · CodeIgniter 3 · FastAPI
PostgreSQL (Supabase y self-hosted) · Oracle/SQL · `pg` directo sin ORM · Knex (migraciones) · RLS

**QA & Testing**
Postilion Realtime/Office · ISO 8583 · Base24 · Octane · Jira · Confluence
Postman · SoapUI · Oracle/SQL · Playwright · Vitest · Jest · `node --test`

**Automatización** *(formación interna SQA + proyecto propio)*
Java 17 · Serenity BDD · Cucumber/Gherkin · patrón Screenplay · JMeter · Azure DevOps CI/CD

**Infra**
Docker · GitHub Actions · Vercel · Render · nginx · GHCR · Infisical

---

## Proyectos

| Proyecto | Qué resuelve | Stack | Estado |
|---|---|---|---|
| 🏥 **ChatBot Enfermería** | Reservas de laboratorios en UNISANGIL. 41 laboratorios, 3 roles, asistente guiado y calendario en tiempo real | React 19 · Express 5 · PostgreSQL · Supabase Realtime | 🟢 En producción |
| 📦 **Inventario Ok-producciones** | Almacén de una productora: imprimir la orden es lo que descuenta stock | Express 5 · PostgreSQL · sin framework en front | 🔄 Activo |
| 🛵 **MotoRed** | SaaS multi-tenant de domicilios (proyecto en equipo) | Next.js 14 · Supabase · Mapbox | 🔴 NO-GO tras auditoría propia |
| 🧪 **FlowCheck** | Testing E2E generado por IA: prompt → plan estructurado → ejecución Playwright con reporte en vivo | Next.js · Gemini · worker Express · Playwright | ⏸️ Funcional, pausado |
| 🌐 **Portafolio** | erickgutierrez.dev — bilingüe, con SSG e i18n propios | React 19 · Vite | 🟢 Desplegado |
| ✅ **Avanza** | Productividad personal: tareas, hábitos con rachas, XP | Next.js · Supabase · Zod | 🔄 En desarrollo |
| 💳 **Account X** | Framework de automatización de pruebas de API con Screenplay | Java 17 · Serenity BDD · Cucumber | ✅ Entregado |

---

## Tres decisiones que vale la pena contar

**Reservas sin condiciones de carrera** — *ChatBot Enfermería*
`SELECT ... FOR UPDATE` + constraint de no-solape por laboratorio. Dos docentes pidiendo la misma franja no pueden ganar los dos. El asistente conversacional, además, **no usa LLM**: es un patrón *state-dictionary* extensible, porque una máquina de estados era la herramienta correcta.

**Auditoría end-to-end con veredicto NO-GO** — *MotoRed*
Antes del paso a producción con clientes de pago encontré tres launch-blockers demostrables en vivo. El principal: la política RLS `perfiles_actualizar_propio` no tenía `WITH CHECK`, así que cualquier usuario autenticado podía hacerse `superadmin` desde el navegador con la anon key y acceder a los datos de todas las empresas. QA de seguridad aplicado a código propio, con evidencia reproducible.

**Guard anti-SSRF donde el usuario controla el destino** — *FlowCheck*
El producto recibe una URL arbitraria del usuario y la visita con un navegador real: eso es superficie de ataque directa, no un detalle. `safe-url.ts` existe por eso.

---

## Actualmente

- 🏥 Desarrollando sobre el ecosistema clínico de GoEcosystem (React 19 · NestJS 11 · CodeIgniter 3)
- 🤖 Profundizando en arquitectura de contexto y evaluación de agentes
- 📘 Preparando **ISTQB Foundation Level**
- 🇬🇧 Inglés B1 → B2

<div align="center">

![Estadísticas de eri323](https://github-readme-stats.vercel.app/api?username=eri323&show_icons=true&theme=github_dark&hide_border=true&bg_color=0D1117&title_color=0E7C82&icon_color=0E7C82&text_color=C9D1D9&rank_icon=github&locale=es)

</div>
