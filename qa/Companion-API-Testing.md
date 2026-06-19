# 🔌 Companion · API Testing para SDET
## La capa más rápida y estable de la pirámide de pruebas

> **Promesa de este documento.** Al terminar sabrás diseñar y automatizar pruebas de API con las tres vías que
> pide el mercado (Postman/Newman, REST Assured en Java, Playwright API), y explicar *por qué* la capa de API es
> la base de la pirámide de pruebas.
>
> **Cómo leerlo.** Con una API real (o mock) abierta: manda peticiones, valida respuestas, automatiza, mete en CI.
>
> **Dominio:** qa · **Maestro / track:** [`../Guía-Estudio-Entrevistas-SDET-2026.md`](../Guía-Estudio-Entrevistas-SDET-2026.md) → §3.4
> **Idioma del código:** Java (REST Assured) + TypeScript (Playwright API)
> **Versión:** 0.1 · **Última actualización:** 2026-06-19 · **Estado:** `Borrador (blueprint)` — se llena en el Bloque A–B.

---

## 0. BLUEPRINT (spec del documento — definir antes de escribir; no se publica al lector)

- **Objetivos de aprendizaje** — al terminar, el lector podrá: 1) explicar métodos HTTP, códigos de estado,
  headers y autenticación (Bearer/OAuth); 2) automatizar pruebas con Postman + Newman, REST Assured y Playwright
  API; 3) validar esquema JSON y entender contract testing (noción de Pact); 4) argumentar el lugar de la API en
  la pirámide de pruebas.
- **Prerrequisitos** — base de Java; nociones de HTTP; el repo `sdet-prep-2026`.
- **Alcance** — REST sobre HTTP, validación de status/headers/body/esquema, auth, integración en CI.
- **Fuera de scope** — UI (→ `Companion-Playwright.md`); diseño de framework (→ `Companion-Framework-Automatizacion.md`);
  SQL para validación de datos (queda en el maestro §3.6 / posible companion futuro de BD).
- **Esquema de secciones** — (1) Fundamentos HTTP · (2) Postman + Newman · (3) REST Assured (Java) ·
  (4) Playwright API · (5) Validación de esquema y contract testing · (6) Cómo se pregunta en entrevista.
- **Datos a verificar** — versiones y comandos de Newman/REST Assured; sintaxis vigente de Playwright API request.

<!-- Borrar/colapsar la sección 0 cuando el contenido esté escrito. Estándar de densidad: CLAUDE.md §3. -->

---

## Índice

*(se construye al desarrollar el contenido)*

---

## Changelog

| Versión | Fecha | Cambios |
|---|---|---|
| 0.1 | 2026-06-19 | Blueprint creado durante la integración del track SDET al framework. |
