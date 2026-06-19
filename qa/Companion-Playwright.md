# 🎭 Companion · Playwright de cero a portafolio (SDET)
## La herramienta de UI que el mercado 2026 está premiando

> **Promesa de este documento.** Si vienes de Selenium, al terminar este companion tendrás Playwright a nivel
> portafolio presentable y sabrás *explicarlo* en entrevista: por qué reduce flakiness, por qué sus localizadores
> son más robustos, y en qué se diferencia arquitectónicamente de Selenium.
>
> **Cómo leerlo.** Con el editor abierto: instala, corre, rompe, arregla. Cada laboratorio termina en un commit
> de tu repo `sdet-prep-2026`.
>
> **Dominio:** qa · **Maestro / track:** [`../Guía-Estudio-Entrevistas-SDET-2026.md`](../Guía-Estudio-Entrevistas-SDET-2026.md) → Apéndice B
> **Idioma del código:** TypeScript (Playwright) · base previa: Java/Selenium
> **Versión:** 0.1 · **Última actualización:** 2026-06-19 · **Estado:** `Borrador (blueprint)` — se llena en el Bloque A–B del plan.

---

## 0. BLUEPRINT (spec del documento — definir antes de escribir; no se publica al lector)

- **Objetivos de aprendizaje** — al terminar, el lector podrá: 1) montar Playwright y escribir tests con
  localizadores role-based y auto-waiting; 2) estructurar un proyecto con Page Object Model, fixtures y datos de
  prueba; 3) usar intercepción/mocking de red, trace viewer y reporting; 4) correr la suite en GitHub Actions; 5)
  explicar en entrevista las diferencias arquitectónicas con Selenium y cuándo elegir cada uno.
- **Prerrequisitos** — Node instalado; base de Selenium/Java; Git y el repo `sdet-prep-2026` creado (Semana 1).
- **Alcance** — Playwright para web (UI + API nativo), POM, CI/CD con GitHub Actions, debugging con trace.
- **Fuera de scope** — Algoritmos (→ manual de Java); CI/CD a fondo (→ ruta DevOps); IA en testing y Playwright
  MCP (→ `Companion-IA-en-Testing.md`); diseño de framework genérico (→ `Companion-Framework-Automatizacion.md`).
- **Esquema de secciones** — espejo de los 4 niveles del Apéndice B: (1) Fundamentos · (2) Real (POM/fixtures) ·
  (3) Avanzado (mocking/trace/paralelismo) · (4) CI/CD. Cierra con "Cómo explicarlo en entrevista".
- **Datos a verificar** — versión actual de Playwright y comandos de instalación; cifras de adopción vs Selenium
  (la tabla de §3.2 del maestro, revalidando fecha); API de localizadores vigente. Verificar contra `playwright.dev`.

<!-- Borrar la sección 0 o colapsarla cuando el contenido esté escrito. Seguir el estándar de densidad de CLAUDE.md §3. -->

---

## Índice

*(se construye al desarrollar el contenido)*

---

## Changelog

| Versión | Fecha | Cambios |
|---|---|---|
| 0.1 | 2026-06-19 | Blueprint creado durante la integración del track SDET al framework. |
