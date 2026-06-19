# 🏗️ Companion · Diseño de un Framework de Automatización
## De "escribir tests" a *arquitecturarlos* — y explicarlo en ≤4 minutos

> **Promesa de este documento.** Al terminar tendrás un framework propio presentable en el portafolio (UI + API +
> CI/CD) y, sobre todo, sabrás **explicarlo** con la plantilla que gana ofertas: stack → patrón de diseño →
> integración CI/CD → reporting → tu rol con un número.
>
> **Cómo leerlo.** Construyendo: este companion es el que convierte tus tests sueltos en una pieza de ingeniería.
>
> **Dominio:** qa · **Maestro / track:** [`../Guía-Estudio-Entrevistas-SDET-2026.md`](../Guía-Estudio-Entrevistas-SDET-2026.md) → Apéndice D + Etapa 3
> **Idioma del código:** TypeScript (Playwright) y/o Java (Selenium/TestNG)
> **Versión:** 0.1 · **Última actualización:** 2026-06-19 · **Estado:** `Borrador (blueprint)` — se llena en el Bloque B.

---

## 0. BLUEPRINT (spec del documento — definir antes de escribir; no se publica al lector)

- **Objetivos de aprendizaje** — al terminar, el lector podrá: 1) diseñar un framework por capas con Page Object
  Model, configuración por entorno y datos de prueba separados; 2) añadir reporting (Allure/Extent), retries y
  paralelismo; 3) integrarlo en CI/CD; 4) explicar el framework en ≤4 min, en español e inglés, con un resultado
  cuantificado.
- **Prerrequisitos** — `Companion-Playwright.md` y `Companion-API-Testing.md` a nivel funcional; el repo con tests.
- **Alcance** — arquitectura, patrones de diseño aplicados a tests, reporting, reliability (retries/paralelismo),
  el "elevator pitch" del framework para entrevista.
- **Fuera de scope** — Fundamentos de cada herramienta (→ sus companions); pipelines a fondo (→ ruta DevOps).
- **Esquema de secciones** — (1) Por qué un framework, no scripts sueltos · (2) Page Object Model y capas ·
  (3) Configuración multi-entorno y datos · (4) Reporting · (5) Reliability: retries, paralelismo, flakiness ·
  (6) Integración CI/CD · (7) Plantilla de explicación en ≤4 min (ES + EN).
- **Datos a verificar** — versiones de Allure/Extent y su integración vigente con el runner elegido.

<!-- Borrar/colapsar la sección 0 cuando el contenido esté escrito. Estándar de densidad: CLAUDE.md §3. -->

---

## Índice

*(se construye al desarrollar el contenido)*

---

## Changelog

| Versión | Fecha | Cambios |
|---|---|---|
| 0.1 | 2026-06-19 | Blueprint creado durante la integración del track SDET al framework. |
