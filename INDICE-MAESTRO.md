# 🗺️ Índice Maestro · Ingeniería Total · Documentación

> Mapa único de toda la base de conocimiento de Alberto. Punto de entrada: desde aquí se llega a cualquier
> documento y se ve su estado. Cómo se trabaja este repo: [`CLAUDE.md`](CLAUDE.md). Plantilla de doc nuevo:
> [`_framework/PLANTILLA-Documento.md`](_framework/PLANTILLA-Documento.md).
>
> **Última actualización:** 2026-06-19

---

## Cómo está organizado

El repo tiene **dos ejes** que se cruzan:

- **Tracks de carrera** (raíz) — documentos *maestros* que orquestan tu preparación hacia un objetivo de empleo.
  Son el mapa: dicen *qué estudiar, en qué orden y por qué*. Apuntan a los dominios para la profundidad.
- **Dominios de conocimiento** (carpetas) — el material profundo a densidad de libro de texto (manuales, guías,
  companions). Es el terreno: *enseñan* cada tema.

Un track puede apoyarse en varios dominios, y un dominio puede servir a varios tracks (p. ej. los algoritmos
sirven tanto al track SDET como a cualquier entrevista técnica). Para evitar duplicar: **cada tema tiene un solo
documento de profundidad** (fuente única de verdad) y los demás lo enlazan.

---

## Tracks de carrera (raíz)

| Track | Documento maestro | Objetivo | Estado |
|---|---|---|---|
| **SDET / QA Automation** | [`Guía-Estudio-Entrevistas-SDET-2026.md`](Guía-Estudio-Entrevistas-SDET-2026.md) | Empleo SDET/QA (nearshore) en ~16 semanas | 🟢 Activo — Semana 0 |
| **DevOps · Cloud · SRE · DevSecOps** | [`devops/Ruta-Maestra-DevOps.md`](devops/Ruta-Maestra-DevOps.md) | De fundamentos a experto en infraestructura | 🟢 Activo — Fase 0 |

> Nota: la ruta DevOps vive dentro de su dominio (`devops/`) por razones históricas; funciona a la vez como
> maestro de track y de dominio. Los tracks nuevos viven en la raíz.

---

## Dominios de conocimiento

### `programacion/` — Programación (base: Java)
| Documento | Qué es | Sirve a | Estado |
|---|---|---|---|
| [`Manual-Java-Algoritmos-y-Estructuras.md`](programacion/Manual-Java-Algoritmos-y-Estructuras.md) | *Vol. I-A* · algoritmos y estructuras desde cero, con encuadre de entrevista | Track SDET (Apéndice A) | 🟢 En uso |

### `devops/` — DevOps · Cloud · SRE · DevSecOps
| Documento | Qué es | Estado |
|---|---|---|
| [`Ruta-Maestra-DevOps.md`](devops/Ruta-Maestra-DevOps.md) | Maestro: mapa de 6 fases (fuente de verdad) | 🟢 Activo — Fase 0 |
| [`Fase-0-Guia-Detallada.md`](devops/Fase-0-Guia-Detallada.md) | Companion: fundamentos (6 semanas + integrador) | ✅ Completa |
| [`Certificaciones-Guia-Detallada.md`](devops/Certificaciones-Guia-Detallada.md) | Companion: guía de certificaciones | 🟢 En uso |
| [`Manual_AZ-900.md`](devops/Manual_AZ-900.md) | Companion: manual de certificación Azure AZ-900 | 🟢 En uso |

### `qa/` — Quality Engineering / SDET (companions de profundidad)
| Documento | Qué es | Estado |
|---|---|---|
| [`Companion-Playwright.md`](qa/Companion-Playwright.md) | Playwright de cero a portafolio | 🟡 Blueprint |
| [`Companion-API-Testing.md`](qa/Companion-API-Testing.md) | API testing (Postman/Newman, REST Assured, Playwright API) | 🟡 Blueprint |
| [`Companion-IA-en-Testing.md`](qa/Companion-IA-en-Testing.md) | IA en testing (Playwright MCP, self-healing, criterio) | 🟡 Blueprint |
| [`Companion-Framework-Automatizacion.md`](qa/Companion-Framework-Automatizacion.md) | Diseño y explicación de un framework de automatización | 🟡 Blueprint |

### Dominios reservados (aún sin contenido)
`db/` (bases de datos · SQL) · `ia/` (inteligencia artificial) · `redes/` (redes).
Cuando se abra uno, sigue el patrón maestro + companions descrito en [`CLAUDE.md`](CLAUDE.md) §5.

---

## Leyenda de estado

✅ Completo · 🟢 En uso / activo · 🟡 Blueprint (spec definida, contenido pendiente) · ⚪ Reservado (vacío)

---

> Mantenimiento: al crear, completar o mover un documento, **actualiza esta tabla en la misma sesión** (P8 del
> framework). Este índice es 🔴 nivel rojo — cambios de fondo requieren autorización de Alberto.
