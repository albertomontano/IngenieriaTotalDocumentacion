# Biblia de Entrevistas · QA Automation · SDET · 2026

> **Fuente de la verdad** para que Alberto vuelva al mercado y consiga un empleo como SDET / QA Automation en menos de 4 meses.
> Documento vivo: se regenera al cierre de cada avance significativo, igual que la Ruta Maestra de DevOps.

| | |
|---|---|
| **Dueño** | Alberto |
| **Mentor / asesor** | Claude |
| **Versión** | 1.1 |
| **Fecha de creación** | 2026-06-19 |
| **Última actualización** | 2026-06-19 |
| **Ventana objetivo** | 16 semanas · 2026-06-22 → 2026-10-11 |
| **Estado general** | Arranque — Semana 0 (montaje) |

---

## Documentos relacionados (esta biblia es el maestro; la profundidad vive en companions)

Este documento es un **track de carrera**: el mapa que orquesta tu preparación. La profundidad de cada tema vive en sus companions, para no duplicar y mantener una sola fuente de verdad:

| Tema | Companion (profundidad) | Estado |
|---|---|---|
| **Algoritmos y estructuras** (Apéndice A) | [`programacion/Manual-Java-Algoritmos-y-Estructuras.md`](programacion/Manual-Java-Algoritmos-y-Estructuras.md) — *Volumen I-A* | ✅ En uso |
| **CI/CD, Docker, nube** (§3.5–3.6) | [`devops/Ruta-Maestra-DevOps.md`](devops/Ruta-Maestra-DevOps.md) + [`devops/Manual_AZ-900.md`](devops/Manual_AZ-900.md) | ✅ En uso |
| **Playwright** (Apéndice B) | `qa/Companion-Playwright.md` | 🟡 Blueprint — se llena en Bloque A–B |
| **API testing** (§3.4) | `qa/Companion-API-Testing.md` | 🟡 Blueprint — se llena en Bloque A–B |
| **IA en testing** (Apéndice C) | `qa/Companion-IA-en-Testing.md` | 🟡 Blueprint — se llena en Bloque C |
| **Framework de automatización** (Apéndice D) | `qa/Companion-Framework-Automatizacion.md` | 🟡 Blueprint — se llena en Bloque B |

Mapa completo del repositorio: [`INDICE-MAESTRO.md`](INDICE-MAESTRO.md).

---

## Antes de empezar — honestidad sobre lo que esto es y lo que no

Esto no es un amuleto. Ningún documento, por bueno que sea, garantiza que apruebes una entrevista — y quien te prometa lo contrario te está mintiendo o te quiere vender un curso. Lo que sí hace este documento: te da un mapa **basado en cómo es el mercado y las entrevistas hoy** (investigado con fuentes de 2026, no con lo que funcionaba hace tres años), un plan de entrenamiento con fechas reales, y profundidad de verdad en lo que más te ha costado (algoritmos). El resto lo pones tú: las horas, la práctica deliberada, y las repeticiones.

Dos verdades incómodas que conviene aceptar desde hoy:

1. **El número de temas que "viste" no importa. Importa lo que puedes hacer sin guía y explicar con tus palabras bajo presión.** Aprobar es demostrar criterio en vivo, no recitar definiciones. Todo el plan está diseñado alrededor de eso.
2. **El mercado de QA cambió.** No es que "ya no haya vacantes": es que cambiaron de nombre, de stack y de filtro. Lo que casi desapareció es el QA puramente manual y el "automatizador de Selenium y nada más". Lo que creció es el **SDET** — el que programa, diseña frameworks, integra en CI/CD y ahora orquesta IA. Tú ya tienes la mitad del camino andado (Java, Selenium, API, algo de CI/CD). Esto es reactivación y actualización, no empezar de cero.

Una suposición que estoy haciendo y que necesito que confirmes: armé el plan asumiendo una intensidad de **~15–20 horas semanales** (es un plan de "supervivencia", no de hobby). Si puedes más, aceleramos; si puedes menos, recortamos el alcance sin romper la columna vertebral. Dime tu número real y recalibro las fechas. Todo lo demás del documento se sostiene igual.

---

## Cómo usar este documento

1. **Las Partes I, II y III son la investigación**: el estado del mercado, cómo son las entrevistas hoy, y qué herramientas/skills piden — todo con fuentes. Léelas una vez completas para entender *el terreno*. Luego se vuelven referencia.
2. **La Parte IV es el plan**: 16 semanas con fechas, temas, laboratorios e hitos. Es lo que ejecutas día a día.
3. **Los Apéndices son la profundidad**: el playbook de algoritmos (tu punto débil), el plan exprés de Playwright, las skills prácticas de IA en testing, el marco para responder preguntas de comportamiento, y la estrategia de CV y aplicaciones (incluyendo el ángulo nearshore, que para ti vale oro).
4. **El Tracker de competencias** se marca `[x]` solo cuando lo dominas de verdad. Es tu termómetro honesto.
5. **Vive y se actualiza** bajo el mismo *Way of Work* de tus otros documentos: al cerrar cada bloque, regenero el documento al día y tú reemplazas la versión en *Files*.

### Way of Work (igual que en DevOps)

- **Sesiones guiadas por tu salida real.** Tú resuelves, compartes tu código / tu intento / tu resultado, y diagnosticamos sobre lo real. Nada de volcados gigantes de teoría.
- **Práctica > consumo.** Un problema resuelto por ti vale más que diez videos vistos.
- **La IA es copiloto, no muleta.** Vas a *usar* IA en testing (es lo que pide el mercado) y a *practicar sin ella* lo que te van a evaluar a mano (algoritmos). Saber cuándo es cuál es parte de la habilidad.
- **Definición de "dominado":** lo haces sin ayuda y lo explicas. No cuando "lo entendiste viéndolo".

---

# PARTE I — Estado del mercado para QA Automation / SDET en 2026

> Objetivo de esta parte: que entiendas el terreno antes de pelear. Dónde está la demanda, qué se está muriendo, qué está creciendo, y dónde encajas tú.

## 1.1 La foto grande

El rol de QA se partió en dos y la brecha se ensanchó:

- **El QA manual puro** y el **automatizador mono-herramienta** perdieron terreno. Las empresas ya no contratan gente solo para ejecutar casos a mano o para mantener una suite de Selenium sin tocar nada más.
- **El SDET** (Software Development Engineer in Test) es el rol que crece más rápido dentro del universo de automatización de pruebas. Es un perfil **híbrido developer-tester**: programa, construye frameworks, contribuye al pipeline de CI/CD, y cada vez más, supervisa y orquesta herramientas de IA. Según el reporte de empleos de automatización de TestDino (marzo 2026, con datos de Indeed, LinkedIn y ZipRecruiter), el título "SDET" es el que más rápido crece entre todos los títulos de automatización, y citando la encuesta salarial de Lorien 2025 (UK), el sector de IA, Machine Learning y Automatización creció ~50% desde 2024, con los SDET entre los roles de mayor crecimiento dentro de él.

Traducción para ti: las vacantes que "no ves" probablemente están publicadas como *SDET*, *Quality Engineer*, *Test Automation Engineer*, *Software Engineer in Test* o *QA Automation Engineer* — no como "QA" a secas. Parte de tu problema de "ya no hay vacantes" puede ser de **vocabulario de búsqueda**.

## 1.2 La demanda existe, pero pide un perfil específico

Lo que el mercado pide hoy, según múltiples fuentes de 2026 (TestDino, Refonte Learning, marutitech, QualityAssuranceJobs):

- **Programación de verdad, no scripting de juguete.** Un lenguaje dominado (Java, Python, JavaScript/TypeScript o C#), conceptos de POO sólidos, y capacidad de leer/contribuir código de producción. Esto es no-negociable para SDET.
- **Automatización moderna**: frameworks de UI (Playwright en ascenso, Selenium aún masivo), API testing, y diseño de frameworks (no solo "escribir tests", sino *arquitecturarlos*).
- **CI/CD**: integrar pruebas en pipelines (GitHub Actions, Jenkins, GitLab CI). La cobertura de pruebas automatizadas supera el 74% en pipelines modernos de CI/CD según datos de industria citados por marutitech — el testing ya no es una fase, está embebido en todo el ciclo.
- **Nube y contenedores**: nociones de Docker, y cada vez más de algún proveedor cloud. Aquí tu ruta de DevOps/AZ-900 es una ventaja directa y diferenciadora.
- **Fluidez con IA**: integrar IA en el flujo de testing (generación de casos, triage de defectos, análisis de cobertura, self-healing). La demanda de "fluidez en IA" en vacantes de EE. UU. se multiplicó casi por siete en dos años (McKinsey Global Institute, citado por Artech, junio 2026) — más rápido que cualquier otra habilidad. El World Quality Report 2025 (citado por TestDino) encontró que el 58% de las empresas está capacitando a sus equipos de QA en IA.

## 1.3 Dinero (referencias, no promesas)

Los rangos varían brutalmente por país, empresa y seniority. Como referencia de 2026:

- **SDET en EE. UU.**: la mediana subió de ~$90,000 (2023) a un rango de ~$96,500–$145,800 (2026) según fuente y definición del título (TestDino). En empresas top, senior/staff SDET puede pasar de $200,000 en compensación total (QualityAssuranceJobs).
- **Premium por multi-herramienta**: quien domina **Selenium *y* Playwright** (o Playwright y Cypress) gana 15–25% más que un especialista de una sola herramienta (TestDino). Este dato es directamente accionable para tu plan.
- **El salto que paga**: la diferencia entre "sé Playwright" y "construyo con agentes de Playwright / IA" se está volviendo el nuevo diferencial salarial (ScrollTest, 2026).

## 1.4 Tu mercado real: nearshore / remoto desde México

Esto es lo más importante de toda la Parte I para tu caso, y casi nadie te lo va a decir tan directo: **tu mercado natural no es solo Chihuahua, es EE. UU. contratando talento mexicano en remoto (nearshore).** Y está en auge.

- México es uno de los destinos top de nearshoring de software, con 700,000+ desarrolladores y un mercado de servicios de TI que alcanzó ~$21.28 mil millones en 2026, proyectado a ~$37.28 mil millones para 2030 (BEON.tech, N-iX, 2026).
- **Las agencias de staffing nearshore reclutan QA/SDET explícitamente.** BEON.tech, Near, Revelo y Remotely listan QA/SDET entre sus roles activos, contratan en LATAM incluyendo México, pagan en **contratos en USD**, y venden a sus clientes la **alineación de zona horaria** (México = Centro/Montaña de EE. UU.) como ventaja principal.
- **Rangos nearshore**: un ingeniero senior nearshore en LATAM ronda los $55,000–$95,000 USD/año según país y especialización (Revelo, 2026); las tarifas reales que pagan las empresas de EE. UU. suelen correr 1.5–2x el promedio local por la fluidez en inglés y la experiencia en proyectos internacionales.

**Implicación para tu estrategia de aplicación** (detalle en el Apéndice E): no apliques solo a bolsas locales. Regístrate en las plataformas nearshore, ten un CV en inglés impecable orientado a palabras clave, y prepárate para entrevistar en inglés. El **inglés técnico fluido** puede valer literalmente el doble de sueldo en tu caso. Si tu inglés conversacional está oxidado, eso entra al plan como ítem de práctica, no como adorno.

---

# PARTE II — Cómo son las entrevistas hoy (2026)

> Objetivo: que no te sorprenda nada. Aquí está el embudo completo, etapa por etapa, qué evalúan y con qué fuente lo sé.

## 2.1 El cambio de fondo: de "trivia de herramientas" a "criterio"

La señal más fuerte de 2026 (Artech, junio 2026): los hiring managers **dejaron de premiar la trivia de herramientas**. Ya no gana el que recita la diferencia entre `findElement` y `findElements`. Gana el que demuestra que **piensa estructuradamente, comunica riesgo y conecta decisiones de calidad con impacto de negocio** — incluso en entornos que no construyó. Esto cambia *cómo* preparas, no solo *qué* preparas.

## 2.2 El embudo típico, etapa por etapa

No todas las empresas usan todas las etapas, pero este es el menú completo del que se sirven en 2026:

**Etapa 0 — El filtro antes del humano (CV + ATS).**
La mayoría de los equipos de contratación empresarial ya usan **screening asistido por IA**: herramientas que transcriben, puntúan y rankean candidatos antes de que un reclutador humano lea nada (Deloitte 2025 Talent Acquisition Technology Trends, citado por Artech). El WEF (Future of Jobs 2025, citado por Artech) reporta que el 63% de los empleadores ve la brecha de habilidades como su principal barrera — buscan **combinaciones precisas de skills**, no "experiencia general en QA". *Tu CV tiene que sobrevivir al algoritmo antes que al humano.* (Cómo, en el Apéndice E.)

**Etapa 1 — Recruiter screen (20–30 min).**
Conversación no técnica o semi-técnica: tu historia, por qué buscas, expectativas de sueldo, disponibilidad, nivel de inglés. Filtran fit básico y comunicación. No la subestimes: aquí mueren muchas candidaturas por respuestas vagas sobre sueldo o por inglés titubeante.

**Etapa 2 — Online Assessment / coding screen (60–90 min).**
Aquí es donde **tu punto débil (algoritmos) pega más fuerte**, y donde la realidad **depende del tipo de empresa**:

- **Empresas tipo FAANG / big-tech / startups bien fondeadas** (Amazon SDET, Tesla, etc.): assessment con **1–2 problemas estilo LeetCode (nivel Medium típico)**, con énfasis en eficiencia y casos borde, frecuentemente + una sección de **fundamentos de CS** tipo opción múltiple (propiedades ACID, indexación en BD, algoritmos de reemplazo de página, stack TCP/IP básico). Esto está documentado en experiencias reales de Amazon SDET-1 (LeetCode Discuss, 2026) y confirmado en foros como Blind.
- **Empresas de producto medianas, consultoras y la mayoría de roles nearshore**: coding **práctico** orientado a testing — invertir un string sin built-ins, contar frecuencia de caracteres con un `Map`, segundo mayor de un arreglo sin ordenar, eliminar duplicados, substring más largo sin repetir — más que rompecabezas de algoritmos competitivos (Artech FAQ; recopilaciones de coding para SDET). El propio Artech lo resume: la mayoría de entrevistas SDET esperan **código limpio y legible de automatización**, no resolución de puzzles competitivos.

**Conclusión operativa:** tienes que preparar *ambos niveles*, pero con pesos distintos. La base de patrones de algoritmos (Apéndice A) te cubre el 80% de los OA prácticos casi gratis, y te da la plataforma para escalar a los Medium de big-tech si decides apuntarle a esas empresas. No necesitas volverte un competidor de Codeforces; necesitas reconocer patrones y escribir código correcto y claro bajo tiempo.

**Etapa 3 — Entrevista técnica de automatización (45–60 min).**
La más predecible y la más preparable. Combina varias de estas:

- **"Explícame tu framework de automatización"** — el prompt más común de nivel mid-senior, y el más arruinado. No necesitas haber construido uno desde cero; necesitas **contar con claridad** cómo funciona uno: stack (lenguaje + runner + librerías), patrón de diseño (Page Object Model, arquitectura por capas, separación de datos de prueba), integración con CI/CD, reporting (Allure, Extent), y **qué parte fue tuya**. Máximo cuatro minutos, como conversación, no como guion (Artech). Marco completo en el Apéndice D.
- **Coding en vivo de automatización**: escribir un test, manejar una respuesta de API, parsear datos, esperar un elemento correctamente (waits), encontrar un localizador robusto.
- **Preguntas de fundamentos**: tipos de waits, jerarquía de localizadores, POO aplicada a tests, diferencia entre `==` y `.equals()` en Java, `HashMap` vs `TreeMap`, etc.

**Etapa 4 — Preguntas basadas en escenarios (lo nuevo y lo decisivo).**
Lo que los entrevistadores *realmente* preguntan en 2026 (Artech, citas textuales parafraseadas):

- *"Tu suite de automatización está frenando los releases. ¿Qué haces?"*
- *"Te entregan una app legada, sin documentación. ¿Por dónde empiezas?"*
- *"Un bug de producción explota a las 2 AM. Camíname por tu respuesta."*

No son preguntas trampa. Evalúan **pensamiento estructurado, conciencia de riesgo y conexión con impacto de negocio**. La estructura que funciona (Artech): **(1) Clarifica** — una o dos preguntas antes de lanzarte. **(2) Enmarca el riesgo** — ¿qué se rompe si esto sale mal? **(3) Esboza tus pasos** — prácticos y secuenciales, no exhaustivos. **(4) Conecta con impacto** — velocidad, calidad, confianza del equipo, cadencia de release. Respuestas de libro de texto pierden ofertas; pensamiento estructurado que suena a experiencia real las gana.

**Etapa 5 — IA en testing (cada vez más frecuente).**
No basta con saber que existen las herramientas de IA: tienes que demostrar que las **usas con criterio** — generación de casos de prueba, triage de defectos, análisis de huecos de cobertura — y que sabes dónde *no* confiar en ellas (Artech; Deloitte 2025: 45% de los líderes tech de EE. UU. dicen que las skills de GenAI son su necesidad más urgente). Detalle práctico en el Apéndice C.

**Etapa 6 — Diseño de sistemas de prueba / "test design" (mid-senior+).**
"Diseña la estrategia de prueba para [X]" (p. ej. un carrito de compras, una API de pagos). Evalúan cobertura, priorización por riesgo, pirámide de pruebas, datos de prueba, y trade-offs. No es system design de SWE puro, es **cómo asegurarías calidad** a escala.

**Etapa 7 — Comportamiento / fit (siempre).**
STAR (Situación, Tarea, Acción, Resultado). Conflictos, fallas, decisiones difíciles, trabajo en equipo. En roles nearshore/remotos, pesan **comunicación, autonomía y proactividad** porque trabajarás distribuido.

## 2.3 Qué evalúan en el fondo (el meta-mapa)

Si destilas todo lo anterior, te evalúan cuatro cosas:

1. **¿Sabes programar?** (coding limpio, POO, estructuras de datos básicas)
2. **¿Sabes automatizar bien?** (frameworks, waits, localizadores, API, CI/CD, diseño)
3. **¿Piensas como ingeniero de calidad?** (riesgo, cobertura, escenarios, impacto)
4. **¿Se puede trabajar contigo en remoto?** (comunicación, inglés, autonomía)

Todo el plan de la Parte IV está construido para llenar estas cuatro casillas, en ese orden de esfuerzo según tus huecos declarados.

---

# PARTE III — El stack y los hard skills que piden en 2026

> Objetivo: que sepas exactamente qué herramientas tocar, cuánto y por qué — con datos de adopción reales, no opiniones.

## 3.1 Lenguaje de programación: elige tu base, no la abandones

Tu base es **Java** (Selenium + TestNG). No la tires; es masiva en el mercado enterprise y nearshore. Pero el mundo moderno de Playwright vive cómodo en **TypeScript/JavaScript**. Recomendación:

- **Mantén Java sólido** como tu lenguaje principal de entrevista (es donde tienes fondo y donde hay más vacantes enterprise).
- **Suma TypeScript** a nivel funcional para Playwright (la sintaxis de Playwright es casi idéntica entre lenguajes, así que el costo es bajo).
- Python es comodín útil si te lo piden, pero no lo persigas si tu tiempo es escaso.

Para entrevistas de coding, **resuelve los algoritmos en el lenguaje que más domines** (Java para ti). No te compliques aprendiendo sintaxis nueva bajo presión.

## 3.2 Automatización de UI: Playwright vs Selenium — los números

Esto es lo que viste de reojo ("ya piden más Playwright"), ahora con datos:

| | Selenium | Playwright |
|---|---|---|
| **Antigüedad** | Desde 2004, estándar por ~2 décadas | Desde 2020 (Microsoft, ex-equipo de Puppeteer) |
| **Adopción (encuestas recientes 2026)** | ~22% | ~45.1% entre profesionales de QA |
| **Crecimiento** | Cuota erosionándose (de ~40% a ~22% en algunas regiones) | +235% interanual; ~78,600 estrellas en GitHub |
| **npm semanal** | — | Pico ~13.5M a mediados de 2026, superando a Cypress |
| **Arquitectura** | WebDriver + HTTP (request-response) | WebSocket persistente / CDP (más directo y rápido) |
| **Setup** | Drivers separados (ChromeDriver, GeckoDriver) | Trae los navegadores; un comando |
| **Waits** | Manuales / explícitos | Auto-waiting inteligente |
| **Paralelismo** | Selenium Grid (más complejo) | Nativo |
| **API testing** | No nativo | Nativo |
| **Dónde domina** | Enterprise/legado, suites grandes ya invertidas, navegadores viejos, equipos Ruby/PHP | Startups, product companies, proyectos nuevos, cloud-native |

Fuentes: getpanto, BrowserStack, Medium/bluudit, Belitsoft, nareshit (todos 2026).

**El veredicto del mercado es unánime y matizado: Selenium no está muerto** (300M+ ejecuciones diarias, 31,854+ organizaciones), pero **Playwright es a donde va el momentum**, sobre todo en producto. Y el dato que te importa por dinero: **dominar ambos paga 15–25% más.** Por eso tu plan es: **refrescar Selenium (ya lo tienes) + aprender Playwright bien (lo nuevo) = perfil multi-herramienta premium.**

## 3.3 IA en testing: el diferenciador de 2026 (y lo que de verdad significa)

Esto es lo que te preocupaba ("piden mucho de IA y cómo integrarla"). Desglosado en lo que es real y útil hoy, no humo:

**a) Generación de tests con IA.** Modelos que generan tests desde specs, PRDs o grabaciones. Las suites generadas con IA requieren ~60–80% menos PRs de mantenimiento que las escritas a mano (BuildBetter, 2026) — pero "solo son tan buenas como los flujos que eliges probar".

**b) Self-healing (auto-reparación).** Cuando un localizador se rompe (por un rediseño de UI), la IA detecta el cambio y sugiere/aplica un reemplazo. Reduce drásticamente el mantenimiento, el dolor histórico #1 de la automatización.

**c) Playwright MCP (Model Context Protocol).** Lo más importante que aprender aquí. MCP le da a la IA acceso a una **vista semántica estructurada** de tu app (el árbol de accesibilidad: roles, labels, estados) más acciones estructuradas (click, type, navigate). Así la IA **maneja el navegador de verdad** en lugar de adivinar con selectores frágiles o pixeles. Microsoft envió los **Playwright Test Agents** en la versión 1.56.0, y el ecosistema explotó desde entonces (ScrollTest, TestDino, Autify, 2026). Herramientas del ecosistema: ZeroStep, Bug0, Octomind, Autify Aximo, Auto Playwright.

**d) IA asistiendo tu flujo diario.** GitHub Copilot / Claude para escribir y depurar tests, generar datos de prueba, triage de defectos, análisis de huecos de cobertura.

**El matiz que te hace ver senior en una entrevista:** la IA **no es hands-off**. Sigue necesitando supervisión humana por tres razones que debes poder nombrar: **explosión de tests** (genera de más), **aserciones alucinadas** (afirma cosas falsas), y **huecos de lógica de negocio** (no entiende el *por qué*). El que dice "la IA lo hace todo" suena junior. El que dice "la IA acelera la autoría y el mantenimiento, pero yo valido aserciones, priorizo por riesgo y vigilo flakiness con visibilidad de CI" suena a quien quieren contratar.

## 3.4 API testing

Sigue siendo core y muy preguntado. Stack a dominar:
- **Postman** (+ Newman para correrlo en CI) — el universal.
- **REST Assured** (Java) — el estándar para API testing en ecosistemas Java; encaja con tu base.
- **Playwright API testing** — nativo, útil para combinar UI + API en un solo framework.
- Conceptos: métodos HTTP, códigos de estado, headers, autenticación (Bearer/OAuth), validación de esquema JSON, contract testing (noción de Pact), y el porqué de probar la capa de API (más rápida y estable que la UI — base de la pirámide de pruebas).

## 3.5 CI/CD para QA

> **Profundidad en tu ruta DevOps.** Lo que sabes de CI/CD, Docker y nube se desarrolla a fondo en [`devops/Ruta-Maestra-DevOps.md`](devops/Ruta-Maestra-DevOps.md) (Fases 1–2) y [`devops/Manual_AZ-900.md`](devops/Manual_AZ-900.md). Aquí solo está lo que la **entrevista de SDET** te va a preguntar; no repitas el material — apóyate en esos documentos y, en la entrevista, vende ese cruce como diferenciador.

- **GitHub Actions** (prioritario — ya lo estás tocando en tu ruta DevOps), **Jenkins** (muy presente en enterprise), **GitLab CI**.
- Qué debes poder hacer y explicar: disparar la suite en cada push/PR, correr en paralelo, condicionar el deploy a pruebas verdes, publicar reportes, manejar secretos. Tu ruta de DevOps te da ventaja real aquí — explótala en la entrevista.

## 3.6 Lo transversal

- **Git** (lo estás reforzando ya): ramas, merge, conflictos, PRs.
- **Docker** (nociones): correr la app y los tests en contenedores, entornos reproducibles.
- **SQL**: consultas para validar datos en BD (joins, agregaciones, subconsultas). Muy preguntado.
- **Fundamentos de CS** para los OA de big-tech: BD (ACID, índices), SO (procesos, memoria), redes (TCP/IP, HTTP). 
- **Inglés técnico**: para nearshore, es multiplicador de sueldo, no opcional.

---

# PARTE IV — Plan de entrenamiento intensivo (16 semanas)

> 2026-06-22 → 2026-10-11. Calculado a ~15–20 h/semana (ajustable). No esperas 16 semanas para aplicar: **empiezas a aplicar en la Semana 5** porque las entrevistas mismas son práctica y tardan semanas en cuajar.

## Estructura macro

| Bloque | Semanas | Fechas | Foco |
|---|---|---|---|
| **A — Reactivación** | 1–4 | 22 jun – 19 jul | Programación + base de algoritmos + Playwright básico + CV listo |
| **B — Núcleo** | 5–9 | 20 jul – 23 ago | Algoritmos por patrones (intensivo) + Playwright avanzado + API + framework. **Empiezas a aplicar.** |
| **C — Especialización** | 10–13 | 24 ago – 20 sep | IA en testing + CI/CD + diseño de pruebas + mocks. Aplicas y entrevistas en serio. |
| **D — Pico** | 14–16 | 21 sep – 11 oct | Loops completos de mock, parchar debilidades, negociar ofertas. |

### Ritmo semanal sugerido (plantilla de cualquier semana)

- **~40% Algoritmos / coding** (tu cuello de botella — recibe la mayor parte hasta el Bloque C).
- **~35% Automatización** (Playwright, API, framework).
- **~15% Proyecto/portafolio + CV/aplicaciones** (desde Bloque B).
- **~10% Comportamiento + inglés + repaso de fundamentos.**

Un día de descanso real a la semana. La constancia gana, no los maratones de fin de semana que te queman.

---

## BLOQUE A — Reactivación (Semanas 1–4)

### Semana 1 · 22–28 jun — Diagnóstico y reactivación de programación
- **Algoritmos:** Big-O (tiempo y espacio) explicado de verdad; arreglos y strings; complejidad de operaciones comunes. Resolver 8–10 problemas *Easy* en Java (LeetCode/NeetCode) para sacudir el óxido. *Diagnóstico honesto: anota cuáles te cuestan.*
- **Automatización:** instalar Node + Playwright; primer test (`npx playwright codegen`); correr en headed/headless. Confirmar que Java + Selenium aún corren en tu máquina.
- **Portafolio:** crear repo público `sdet-prep-2026` en tu GitHub (`github.com/albertomontano`) — será tu vitrina. Primer commit.
- **CV/inglés:** auditar tu CV actual contra palabras clave de 3 vacantes reales de SDET. *Lab integrador:* un test de Playwright que abra un sitio y valide un título, versionado en el repo.

### Semana 2 · 29 jun–5 jul — Estructuras de datos esenciales + Playwright I
- **Algoritmos:** Hash maps/sets (el patrón que resuelve más problemas de entrevista), listas, pilas y colas. 8–10 problemas Easy/Medium centrados en hashing y conteo.
- **Automatización:** localizadores de Playwright (role-based, `getByText`, `getByTestId`), auto-waiting, aserciones (`expect`). Por qué los localizadores robustos importan.
- **Portafolio:** 3–4 tests de un flujo real (login/búsqueda) en el repo.
- **Comportamiento:** redactar 2 historias STAR de tu experiencia pasada.

### Semana 3 · 6–12 jul — Two pointers / sliding window + Playwright II
- **Algoritmos:** patrones **dos punteros** y **ventana deslizante** (cubren una franja enorme de problemas de strings/arreglos). 8–10 problemas. *Aquí empiezas a sentir que reconoces patrones, no que improvisas.*
- **Automatización:** Page Object Model en Playwright; estructura de proyecto; fixtures; datos de prueba separados.
- **Portafolio:** refactorizar tus tests a POM.
- **Inglés:** grabarte explicando tu framework en inglés (4 min). Sí, incómodo; sí, necesario.

### Semana 4 · 13–19 jul — Recursión + API testing + cierre de CV
- **Algoritmos:** recursión y backtracking (nivel introductorio), árboles binarios (traversal). 8–10 problemas.
- **Automatización:** API testing — Postman + Newman; primeras pruebas de API en Playwright; validar status, headers, body, esquema.
- **CV:** versión final optimizada para ATS (Apéndice E), en español **y** inglés. 
- **Hito del Bloque A:** repo con ~10 tests (UI + API) en POM, CV listo, y ~35 problemas de algoritmos resueltos con tus patrones documentados. *Empiezas a perfilar dónde aplicarás.*

---

## BLOQUE B — Núcleo (Semanas 5–9)

> A partir de aquí **aplicas en paralelo**. Meta: 5–10 aplicaciones de calidad por semana (no spam), priorizando plataformas nearshore.

### Semana 5 · 20–26 jul — Patrones intermedios + Playwright avanzado + ARRANCAS A APLICAR
- **Algoritmos:** búsqueda binaria; ordenamientos (entender, no memorizar); patrón de intervalos. 10 problemas Medium.
- **Automatización:** Playwright avanzado — manejo de múltiples pestañas, iframes, descargas, intercepción de red (mocking de API), screenshots/trace para debugging.
- **Aplicaciones:** registrarte en plataformas nearshore (Apéndice E); 5 aplicaciones esta semana.
- **Comportamiento:** 2 historias STAR más.

### Semana 6 · 27 jul–2 ago — Árboles y grafos (intro) + diseño de framework
- **Algoritmos:** árboles (BFS/DFS), introducción a grafos. Estos aparecen en big-tech; nivel sólido pero sin obsesión. 10 problemas.
- **Automatización:** arquitectura de framework de cero — capas, configuración por entorno, reporting (Allure), retries, paralelismo.
- **Aplicaciones:** 5–8; empieza a registrar respuestas y primeras llamadas de recruiter.

### Semana 7 · 3–9 ago — Refuerzo Java para SDET + CI/CD
- **Algoritmos:** las preguntas Java-SDET clásicas (invertir string sin built-ins, frecuencia con Map, segundo mayor sin ordenar, dedup, `HashMap` vs `TreeMap`, `==` vs `.equals()`). Estas caen literalmente en OA prácticos.
- **Automatización:** integrar tu suite en **GitHub Actions** — correr en cada push, en paralelo, publicar reporte. (Tu ventaja DevOps.)
- **Aplicaciones:** 5–8. Primeras entrevistas reales = práctica real.

### Semana 8 · 10–16 ago — Programación dinámica (intro) + SQL
- **Algoritmos:** DP introductoria (los patrones base: memoización, problemas tipo Fibonacci/escaleras/subsecuencias). No te claves; nivel reconocer-y-resolver lo común.
- **Automatización:** SQL para QA — joins, agregaciones, subconsultas; validar datos de BD desde un test.
- **Aplicaciones + mocks:** primer mock de coding cronometrado (contigo mismo o con la IA como entrevistador).

### Semana 9 · 17–23 ago — Consolidación + primer loop de mock completo
- **Algoritmos:** repasar los patrones débiles (revisa tu bitácora de "cuáles me cuestan"). Resolver 5 Medium mezclados sin saber el patrón de antemano (así es la entrevista real).
- **Automatización:** cerrar el framework como pieza de portafolio presentable.
- **Hito del Bloque B:** framework completo en el repo (UI + API + CI/CD), ~80 problemas de algoritmos acumulados, CV aplicado en 8+ lugares, al menos 1 proceso de entrevista activo. **Mock completo:** recruiter screen + coding + técnica de automatización.

---

## BLOQUE C — Especialización (Semanas 10–13)

### Semana 10 · 24–30 ago — IA en testing (práctico)
- **IA:** montar **Playwright MCP** y los Test Agents; generar un test con IA y *corregirlo a mano* (para ver dónde alucina); self-healing en acción. Documentar en el repo. (Apéndice C.)
- **Algoritmos:** mantener el filo — 5 Medium/semana de aquí al final.
- **Aplicaciones:** ritmo sostenido; preparar respuestas de "¿cómo usas IA en testing?".

### Semana 11 · 31 ago–6 sep — Diseño de estrategia de pruebas
- **Diseño:** practicar "diseña la prueba para [carrito / API de pagos / login]": pirámide de pruebas, priorización por riesgo, cobertura, datos, trade-offs. (Etapa 6.)
- **Automatización:** visual regression (concepto + una herramienta), pruebas de accesibilidad básicas.
- **Mocks:** un mock de escenarios (Etapa 4) con la estructura Clarifica→Riesgo→Pasos→Impacto.

### Semana 12 · 7–13 sep — Escenarios + comportamiento a punto
- **Escenarios:** ensayar en voz alta los tres clásicos (suite lenta, app legada sin docs, bug a las 2 AM) hasta que fluyan como conversación.
- **Comportamiento:** banco de 6–8 historias STAR pulidas, en inglés y español.
- **Mocks:** loop técnico completo. Ajustar según feedback de entrevistas reales que ya estés teniendo.

### Semana 13 · 14–20 sep — Repaso integral + parchado de debilidades
- Diagnóstico honesto: ¿dónde fallaste en entrevistas reales o mocks? Atacar *eso* específicamente.
- **Hito del Bloque C:** puedes (1) generar y validar tests con IA explicando sus límites, (2) diseñar una estrategia de prueba de viva voz, (3) responder escenarios con estructura, (4) tener 2+ procesos activos.

---

## BLOQUE D — Pico (Semanas 14–16)

### Semana 14 · 21–27 sep — Loops completos de mock
- Simular el día completo de entrevista (coding + automatización + escenarios + diseño + comportamiento) 1–2 veces.
- Seguir aplicando y entrevistando. Refinar con cada rechazo (pide feedback siempre).

### Semana 15 · 28 sep–4 oct — Afinado fino y negociación
- Pulir puntos débiles residuales.
- Preparar **negociación de oferta**: rangos (Parte I), cómo hablar de sueldo en USD para nearshore, evaluar ofertas.

### Semana 16 · 5–11 oct — Cierre
- Mantener entrevistas activas; no bajar el ritmo de aplicaciones hasta tener oferta firmada.
- Si ya hay oferta: evaluar contra tus criterios. Si no: el motor está caliente, sigues hasta cerrar — el plan no "termina", la búsqueda continúa con la maquinaria ya montada.

> **Realismo:** 16 semanas es para *estar listo y tener procesos activos*, no necesariamente para tener la firma el día 11 de octubre. Conseguir empleo depende de variables fuera de tu control (timing, número de vacantes, suerte). Lo que *sí* controlas — estar genuinamente preparado y aplicar con volumen y calidad — es exactamente lo que este plan maximiza.

---

# APÉNDICE A — Playbook de Algoritmos (tu prioridad #1)

> **Este apéndice es el mapa; la profundidad vive en el companion.** Cada patrón de aquí se *enseña* a fondo —con analogías, código corrible, trazas a mano y banco de problemas resueltos— en [`programacion/Manual-Java-Algoritmos-y-Estructuras.md`](programacion/Manual-Java-Algoritmos-y-Estructuras.md) (*Volumen I-A*). Usa este apéndice para saber **qué patrón y en qué orden**; usa el manual para **aprenderlo**. No dupliques notas entre ambos: el manual es la fuente de verdad de algoritmos.

> Esto es lo que más te ha costado y donde más rinde el esfuerzo. La clave no es "resolver 500 problemas". Es **dominar ~15 patrones** y aprender a **reconocer cuál aplica**. La mayoría de los problemas de entrevista son variaciones de estos patrones.

## A.1 Mentalidad correcta

El error clásico (y probablemente el tuyo en el pasado): tratar cada problema como nuevo y entrar en pánico. La verdad: el 80% de los problemas de entrevista caen en un puñado de patrones. Tu trabajo es **reconocer el patrón en los primeros 60 segundos** y aplicar la plantilla. Eso solo se logra con repetición deliberada: resolver, *identificar el patrón*, y anotar la señal que lo delató.

**Método por problema (no negociable):**
1. Lee y **reformula** el problema con tus palabras.
2. Pregunta/aclara supuestos (en entrevista, en voz alta: tamaño de entrada, duplicados, vacío, negativos).
3. **Fuerza bruta primero**, di su Big-O. Siempre. Nunca te quedes en blanco.
4. Optimiza: ¿qué patrón reduce la complejidad?
5. Codifica limpio, **narrando tu razonamiento** (en entrevista esto vale tanto como el código).
6. Prueba con casos borde (vacío, uno, duplicados, máximo).
7. Da la complejidad final de tiempo y espacio.

## A.2 Los patrones que cubren la mayoría de las entrevistas

1. **Hashing (Map/Set)** — conteo de frecuencias, detectar duplicados, "¿existe el complemento?". *Señal:* "encuentra pares/duplicados/anagramas", "cuenta...". Ej. canónico: Two Sum.
2. **Dos punteros** — arreglos/strings ordenados, pares desde extremos. *Señal:* "ordenado", "par que sume X", "palíndromo", "invertir".
3. **Ventana deslizante** — subarreglo/substring contiguo óptimo. *Señal:* "substring/subarreglo más largo/más corto que cumpla...". Ej. canónico: substring más largo sin repetir.
4. **Búsqueda binaria** — espacio de búsqueda ordenado o monótono. *Señal:* "ordenado" + "encuentra", o "minimiza/maximiza un valor factible".
5. **Recursión + Backtracking** — generar combinaciones/permutaciones/subconjuntos. *Señal:* "todas las combinaciones/caminos posibles".
6. **Árboles (DFS/BFS)** — recorridos, profundidad, caminos. *Señal:* estructura jerárquica, "nodo/hijo/raíz".
7. **Grafos (BFS/DFS)** — conectividad, caminos más cortos sin peso, componentes. *Señal:* "red", "conexiones", "islas", "dependencias".
8. **Pilas** — emparejar/anidar, "el más reciente". *Señal:* paréntesis balanceados, "siguiente mayor elemento".
9. **Colas / BFS** — nivel por nivel, más corto. 
10. **Intervalos** — solapamientos, fusiones. *Señal:* "reuniones", "rangos", "fusiona intervalos".
11. **Ordenamiento como herramienta** — a veces ordenar primero simplifica todo.
12. **Prefix sum / acumulados** — sumas de rangos repetidas.
13. **Programación dinámica** — subproblemas que se repiten, "de cuántas formas / mínimo costo". *Señal:* "óptimo" + decisiones secuenciales. Empieza por memoización.
14. **Heaps / colas de prioridad** — "top K", "mediana en streaming".
15. **Manipulación de strings** — parsing, conteo, transformaciones (muy común en SDET práctico).

## A.3 Lista curada Java-SDET (las que caen en OA prácticos)

Practica estas hasta poder escribirlas sin pensar (son las que más aparecen en assessments prácticos de SDET):
- Invertir un string **sin** `StringBuilder.reverse()`.
- Frecuencia de caracteres con `HashMap`.
- Segundo número mayor de un arreglo **sin ordenar**.
- Eliminar duplicados de una lista/arreglo.
- Substring más largo sin caracteres repetidos.
- Verificar anagramas / palíndromos.
- `HashMap` vs `TreeMap`: cuándo cada uno y por qué.
- `==` vs `.equals()` en Java (y por qué importa en aserciones).
- FizzBuzz y variantes (sí, todavía cae).
- Contar palabras / ocurrencias en un texto.

## A.4 Plan de práctica (cómo, no solo qué)

- **Volumen objetivo realista:** ~120–150 problemas en las 16 semanas, no 500. Calidad sobre cantidad.
- **Distribución:** ~60% Easy/Medium prácticos (cubren la mayoría de roles SDET/nearshore), ~30% Medium de patrones (para big-tech), ~10% repaso de los que fallaste.
- **Recurso ancla:** **NeetCode 150** (organizado por patrón — ideal para tu forma de aprender) y **LeetCode** (filtrar por patrón y por empresa).
- **Regla de oro:** si no lo sacas en ~25–30 min, mira la solución, **entiende el patrón**, ciérrala, y **vuelve a resolverlo a los 2–3 días desde cero**. La segunda vez es la que aprende.
- **Lleva una bitácora** de "problema → patrón → señal que lo delató → mi error". Esa bitácora es tu mapa de debilidades.

---

# APÉNDICE B — Plan exprés de Playwright

> Asumiendo tu base de Selenium, Playwright se aprende rápido. Meta: de cero a portafolio presentable en ~4 semanas distribuidas en el plan.

**Nivel 1 — Fundamentos:** instalación, `codegen`, estructura de test, localizadores role-based (`getByRole`, `getByText`, `getByLabel`, `getByTestId`), auto-waiting (la gran diferencia vs Selenium: no más `Thread.sleep`), aserciones web-first (`expect(locator).toBeVisible()`).

**Nivel 2 — Real:** Page Object Model, fixtures, configuración multi-entorno, datos de prueba, manejo de pestañas/iframes/descargas.

**Nivel 3 — Avanzado:** intercepción y mocking de red, API testing nativo, trace viewer y debugging, screenshots/video, retries, paralelismo, reporting.

**Nivel 4 — CI/CD:** correr en GitHub Actions, en paralelo, en contenedores Docker, publicar reportes.

**Para la entrevista, debes poder explicar (no solo hacer):** por qué el auto-waiting reduce flakiness, por qué los localizadores role-based son más robustos que XPath frágil, cómo Playwright difiere arquitectónicamente de Selenium (WebSocket/CDP vs WebDriver/HTTP), y cuándo *seguirías* eligiendo Selenium (legado, navegadores viejos, equipos Ruby/PHP, suites enormes ya invertidas).

**Recursos:** documentación oficial de Playwright (excelente), canal de Playwright en YouTube, y construir **tu propio** proyecto sobre un sitio real (tu vitrina pesa más que cualquier certificado).

---

# APÉNDICE C — IA en testing, en la práctica

> Lo que de verdad debes *poder hacer y comentar*, no solo nombrar.

**Montar y usar Playwright MCP + Test Agents** (v1.56.0+): conectar un agente (Claude/Copilot) vía MCP para que explore tu app por el árbol de accesibilidad y genere/depure tests. *Documenta el experimento en tu repo* — eso es oro en entrevista.

**Generar un test con IA y corregirlo a mano:** el ejercicio más formativo. Verás dónde la IA alucina aserciones o cubre el flujo equivocado. Poder narrar esto te separa del montón.

**Self-healing:** entender el concepto (la IA repara localizadores rotos) y poder discutir su trade-off (menos mantenimiento vs. riesgo de "reparar" hacia algo incorrecto).

**IA en tu flujo diario:** Copilot/Claude para autoría y debugging, generación de datos de prueba, triage de defectos, análisis de huecos de cobertura.

**El discurso senior (memorízalo en tu propio lenguaje):** "La IA acelera autoría y mantenimiento — 60–80% menos PRs de mantenimiento en suites generadas — pero no es hands-off. Yo superviso por explosión de tests, aserciones alucinadas y huecos de lógica de negocio, y mido confiabilidad con visibilidad de CI. La IA escribe; yo decido qué vale la pena probar y valido que las aserciones sean correctas."

Herramientas que conviene poder nombrar: ZeroStep, Bug0, Octomind, Autify Aximo, Auto Playwright, Testim, Mabl, Applitools.

---

# APÉNDICE D — Cómo explicar tu framework (sin divagar)

> El prompt mid-senior más común y más arruinado. Plantilla de Artech, en ≤4 minutos, como conversación:

1. **Stack:** lenguaje + runner + librerías. *Ej.:* "Java + Selenium + TestNG" o "TypeScript + Playwright".
2. **Patrón de diseño:** Page Object Model, arquitectura por capas, separación de datos de prueba.
3. **Integración CI/CD:** Jenkins/GitHub Actions, cómo se disparan los tests, en paralelo.
4. **Reporting:** Allure/Extent; quién ve los resultados y cuándo.
5. **Tu rol:** qué te tocó a ti, qué mejoraste (con un número si puedes: "reduje el tiempo de la suite 40%", "subí cobertura a X%").

Practícalo **en voz alta** hasta que fluya. Y ten una versión en **inglés**.

---

# APÉNDICE E — CV, ATS y estrategia de aplicaciones (especialmente nearshore)

## E.1 Sobrevivir al filtro de IA (ATS)

- **Usa el lenguaje exacto de las vacantes**: SDET, QA Automation Engineer, Quality Engineer, Test Automation Engineer — el ATS empareja palabras clave antes de que un humano lea.
- **Nombra las herramientas explícitamente**: Java, Playwright, Selenium, TestNG, REST Assured, Postman, GitHub Actions, Docker, SQL, y tu experiencia con IA (Copilot, Playwright MCP, generación de tests). *No entierres la experiencia con IA — nómbrala.*
- **Mínimo un resultado cuantificado**: reducción de tiempo de suite, % de cobertura, impacto en cadencia de release. Un número vale más que diez adjetivos.
- **Adapta cada aplicación** como si fuera a un algoritmo de matching — porque probablemente lo es.

## E.2 Dónde aplicar (tu mapa nearshore)

No te limites a bolsas locales. Regístrate en plataformas nearshore que reclutan QA/SDET en México con contratos en USD: **BEON.tech, Revelo, Near, Remotely, Turing, Mismo**, entre otras. Suma LinkedIn (con búsquedas por "SDET remote LATAM / nearshore") y bolsas remotas (Jobicy, We Work Remotely). 

**Tu ventaja competitiva nearshore:** zona horaria (Chihuahua = Centro/Montaña de EE. UU., solape total con la jornada gringa), y — si lo trabajas — inglés. Véndelos explícitamente.

## E.3 Volumen y disciplina

- 5–10 aplicaciones **de calidad** por semana desde la Semana 5 (no spam).
- Lleva un tracker (hoja de cálculo): empresa, rol, fecha, etapa, feedback.
- **Pide feedback en cada rechazo.** Es inteligencia gratis para parchar debilidades.
- Cada entrevista, aunque no la consigas, es práctica que mejora la siguiente. Trata las primeras como ensayos.

---

# Tracker de competencias

> `[x]` solo cuando lo haces sin guía y lo explicas con tus palabras.

**Programación y algoritmos**
- [ ] Big-O (tiempo y espacio) con soltura
- [ ] Hashing (Map/Set)
- [ ] Dos punteros y ventana deslizante
- [ ] Búsqueda binaria
- [ ] Recursión y backtracking (intro)
- [ ] Árboles (DFS/BFS)
- [ ] Grafos (intro)
- [ ] Pilas / colas / intervalos
- [ ] Programación dinámica (intro)
- [ ] Las 10 preguntas Java-SDET clásicas sin pensar
- [ ] Reconocer el patrón de un problema nuevo en <60 s

**Automatización**
- [ ] Playwright: localizadores, auto-waiting, aserciones
- [ ] Page Object Model
- [ ] API testing (Postman/Newman, REST Assured, Playwright API)
- [ ] Mocking/intercepción de red
- [ ] Framework propio en el repo
- [ ] Selenium refrescado (multi-herramienta = premium)
- [ ] SQL para validación de datos

**CI/CD y nube**
- [ ] Suite en GitHub Actions (paralela, con reporte)
- [ ] Tests en Docker
- [ ] Conectar con tu base de DevOps/AZ-900 en la entrevista

**IA en testing**
- [ ] Playwright MCP + Test Agents montados
- [ ] Generar un test con IA y validarlo a mano
- [ ] Discurso sobre límites de la IA (explosión, alucinación, lógica de negocio)

**Entrevista (meta-skills)**
- [ ] Explicar mi framework en ≤4 min (español e inglés)
- [ ] Responder escenarios con estructura Clarifica→Riesgo→Pasos→Impacto
- [ ] Banco de 6–8 historias STAR
- [ ] Inglés técnico fluido para entrevista
- [ ] CV optimizado para ATS (ES + EN)

---

# Recursos verificados

**Algoritmos**
- **NeetCode 150** — problemas organizados por patrón (`neetcode.io`).
- **LeetCode** — filtrar por patrón y por empresa (`leetcode.com`).
- **Grokking the Coding Interview** — el enfoque por patrones (concepto, no necesariamente el curso de pago).

**Playwright**
- **Documentación oficial** — `playwright.dev` (de las mejores docs que existen).
- **Canal oficial de Playwright en YouTube**.

**IA en testing**
- **Playwright MCP / Test Agents** — docs oficiales de Playwright (sección AI/Agents).
- Blogs técnicos 2026: TestDino, Autify, ScrollTest (referencia, con criterio).

**Mercado y entrevistas (las fuentes de este documento)**
- Artech — *QA Automation Interviews: What to Expect in 2026*.
- TestDino — *Test Automation Jobs Report 2026* y *Playwright AI Ecosystem 2026*.
- Refonte Learning, marutitech, QualityAssuranceJobs — tendencias y salarios SDET 2026.
- getpanto, BrowserStack, Belitsoft — Playwright vs Selenium 2026.
- Revelo, BEON.tech, N-iX, Remotely — mercado nearshore LATAM/México 2026.

**Comunidades**
- Ministry of Testing, r/QualityAssurance, LinkedIn (grupos de SDET/automation), Test Automation University (cursos gratuitos de calidad).

---

# Bitácora de progreso

> Lo más reciente arriba. Qué se cubrió, qué hiciste tú, laboratorios.

### 2026-06-19 — Integración al framework de documentación (v1.1)
- **Cubierto:** se enganchó la Biblia a la arquitectura del repo (ITD-SDD Framework). Enlaces a companions de profundidad sin duplicar contenido: Apéndice A ↔ manual de Java (*Volumen I-A*); §3.5–3.6 ↔ ruta DevOps + AZ-900. Se perfilaron como blueprint los companions de QA (Playwright, API testing, IA en testing, Framework) en `qa/`. Se creó el `INDICE-MAESTRO.md` de la raíz. Se añadió la tabla *Documentos relacionados* y el campo *Última actualización*.
- **Hecho por Alberto:** decidió que la Biblia vive en la raíz como track de carrera transversal y autorizó la integración completa.
- **Laboratorios:** —
- **Siguiente:** sin cambios respecto a v1.0 — confirmar horas semanales y arrancar Semana 1.

### 2026-06-19 — Creación de la Biblia (v1.0)
- **Cubierto:** investigación del mercado QA/SDET 2026 con fuentes verificadas (Parte I), anatomía de las entrevistas actuales etapa por etapa (Parte II), el stack y hard skills con datos de adopción reales — Playwright vs Selenium, IA en testing, API, CI/CD (Parte III), plan intensivo de 16 semanas con fechas (Parte IV), y apéndices de profundidad: playbook de algoritmos, plan exprés de Playwright, IA práctica, explicación de framework, y estrategia de CV/aplicaciones nearshore.
- **Hecho por Alberto:** solicitó la investigación de mercado + formato de entrevistas + plan, con el estándar de profundidad de sus documentos previos (Ruta DevOps, Fase 0, Manual AZ-900). Declaró su debilidad principal: algoritmos (~80% de sus entrevistas técnicas).
- **Laboratorios:** —
- **Siguiente:** confirmar horas semanales reales para calibrar fechas; arrancar Semana 1 (diagnóstico de programación + primer test de Playwright + crear repo `sdet-prep-2026`).

---

# Changelog del documento

| Versión | Fecha | Cambios |
|---|---|---|
| 1.1 | 2026-06-19 | Integración al ITD-SDD Framework: tabla *Documentos relacionados*, campo *Última actualización*, cross-links a companions (manual de Java algoritmos, ruta DevOps, AZ-900) en Apéndice A y §3.5, registro en `INDICE-MAESTRO.md` y blueprints de companions QA en `qa/`. Sin cambios al contenido de investigación. |
| 1.0 | 2026-06-19 | Creación: estado del mercado QA/SDET 2026, anatomía de entrevistas, stack y hard skills (Playwright/Selenium, IA, API, CI/CD), plan intensivo de 16 semanas con fechas, apéndices (algoritmos, Playwright, IA, framework, CV/nearshore), tracker, recursos y bitácora. Todo con fuentes verificadas de 2026. |
