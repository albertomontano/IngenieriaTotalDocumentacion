# 🤖 Companion · IA en Testing (el diferenciador 2026)
## Usar la IA con criterio — y saber dónde NO confiar en ella

> **Promesa de este documento.** Al terminar podrás montar Playwright MCP + Test Agents, generar un test con IA y
> corregirlo a mano, y —lo decisivo en entrevista— **narrar los límites de la IA** (explosión de tests, aserciones
> alucinadas, huecos de lógica de negocio) como quien la usa de verdad, no como quien la idolatra.
>
> **Cómo leerlo.** Es el más práctico-experimental: cada sección termina en un experimento documentado en tu repo.
>
> **Dominio:** qa · **Maestro / track:** [`../Guía-Estudio-Entrevistas-SDET-2026.md`](../Guía-Estudio-Entrevistas-SDET-2026.md) → Apéndice C
> **Idioma del código:** TypeScript (Playwright) + el agente (Claude/Copilot)
> **Versión:** 0.1 · **Última actualización:** 2026-06-19 · **Estado:** `Borrador (blueprint)` — se llena en el Bloque C.

---

## 0. BLUEPRINT (spec del documento — definir antes de escribir; no se publica al lector)

- **Objetivos de aprendizaje** — al terminar, el lector podrá: 1) montar y usar Playwright MCP + Test Agents para
  que un agente explore la app por el árbol de accesibilidad y genere/depure tests; 2) generar un test con IA y
  validarlo a mano, identificando dónde alucina; 3) explicar self-healing y su trade-off; 4) articular "el discurso
  senior" sobre los límites de la IA y la supervisión humana.
- **Prerrequisitos** — Playwright a nivel del `Companion-Playwright.md`; un repo con tests reales que mejorar.
- **Alcance** — Playwright MCP/Test Agents, generación asistida, self-healing, IA en el flujo diario; criterio de
  supervisión.
- **Fuera de scope** — Fundamentos de Playwright (→ su companion); construir agentes/LLM apps desde cero.
- **Esquema de secciones** — (1) Qué es MCP y por qué importa · (2) Montar MCP + Test Agents · (3) Generar y
  corregir a mano · (4) Self-healing y su trade-off · (5) IA en el flujo diario · (6) El discurso senior para
  entrevista (límites + supervisión).
- **Datos a verificar** — versión de Playwright que envió los Test Agents (el maestro cita v1.56.0 — revalidar
  fecha y número); estado del ecosistema de herramientas (ZeroStep, Octomind, etc.) a la fecha de redacción.

<!-- Borrar/colapsar la sección 0 cuando el contenido esté escrito. Estándar de densidad: CLAUDE.md §3. Regla P4: nada de cifras sin verificar. -->

---

## Índice

*(se construye al desarrollar el contenido)*

---

## Changelog

| Versión | Fecha | Cambios |
|---|---|---|
| 0.1 | 2026-06-19 | Blueprint creado durante la integración del track SDET al framework. |
