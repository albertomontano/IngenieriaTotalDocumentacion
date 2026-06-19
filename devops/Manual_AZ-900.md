# 📘 MANUAL INTENSIVO DE CERTIFICACIÓN
# AZ-900: Microsoft Azure Fundamentals
### Guía completa de estudio — de principiante absoluto a aprobar con puntaje máximo

---

> **Versión del temario:** Habilidades medidas oficiales (*Skills Measured*) vigentes al **14 de enero de 2026**.
> **Rutas de Microsoft Learn:** verificadas y actualizadas (última revisión de Microsoft: marzo 2026).
> **Idioma del examen:** disponible en español. · **Nivel del manual:** desde cero absoluto hasta dominio experto.
>
> **Propósito de este documento:** ser un manual **autosuficiente y de consulta permanente**. Si lo estudias completo, resuelves su práctica y haces los laboratorios enlazados de Microsoft Learn, tienes todo lo necesario para aprobar la AZ-900 — apuntando al puntaje máximo, no apenas al mínimo.

---

## Cómo está organizado este manual

Este manual se divide en seis partes. Puedes leerlo en orden (recomendado para principiantes) o saltar a la parte que necesites (útil como referencia para quien ya tiene experiencia).

| Parte | Contenido | Para quién |
|---|---|---|
| **I. Fundamentos y método** | Qué es el examen, cómo se estructura, cómo estudiar y el mapa completo de Microsoft Learn. | Todos. |
| **II. Conocimiento base** | Capítulo 0: fundamentos de TI explicados desde cero. | Principiantes absolutos. |
| **III. Los tres dominios** | El corazón del manual: todo el temario explicado en profundidad, con ejemplos y mapeo a Microsoft Learn. | Todos. |
| **IV. Refuerzo y memorización** | Pares confundibles, mnemotecnias, hojas de referencia rápida y glosario maestro. | Repaso final. |
| **V. Práctica y examen** | Banco de preguntas, simulacros y estrategia del día del examen. | Antes de agendar. |
| **VI. Apéndices** | Metodología reproducible para crear este tipo de manual en futuras certificaciones, y registro de elaboración. | Para replicar el manual con AZ-104 u otras. |

### Convenciones visuales que verás a lo largo del manual

- 📚 **Caja "Dónde estudiarlo en Microsoft Learn":** te dice el módulo y unidad exactos para reforzar ese tema con el contenido oficial gratuito (con laboratorios).
- 🎓 **Objetivos oficiales:** al abrir cada dominio, la lista literal de objetivos de aprendizaje de Microsoft.
- 🔑 **Clave de examen:** el dato exacto que más se pregunta.
- ⚠️ **Trampa común:** confusiones que el examen explota a propósito.
- 🏠 **Analogía:** una comparación cotidiana para fijar el concepto.
- 💡 **En la práctica:** cómo se ve esto en el mundo real.
- 🧪 **Escenarios resueltos:** al final de cada dominio, casos razonados paso a paso.
- 📝 **Preguntas de práctica:** banco por dominio en la Parte V.

---

## Índice general

**PARTE I — FUNDAMENTOS Y MÉTODO DE ESTUDIO**
1. [Qué es la AZ-900 y por qué vale la pena](#1-qué-es-la-az-900-y-por-qué-vale-la-pena)
2. [Anatomía del examen: formato, tipos de pregunta y puntaje](#2-anatomía-del-examen)
3. [Método de estudio intensivo (cómo usar este manual)](#3-método-de-estudio-intensivo)
4. [Mapa completo de Microsoft Learn: las 3 rutas y sus 12 módulos](#4-mapa-completo-de-microsoft-learn)
5. [Plan de estudio con calendario](#5-plan-de-estudio-con-calendario)

**PARTE II — CONOCIMIENTO BASE**
6. [Capítulo 0: Fundamentos de TI desde cero](#6-capítulo-0-fundamentos-de-ti-desde-cero)

**PARTE III — LOS TRES DOMINIOS EN PROFUNDIDAD**
7. [Dominio 1 — Conceptos de la nube (25–30%)](#7-dominio-1--conceptos-de-la-nube-2530)
8. [Dominio 2 — Arquitectura y servicios de Azure (35–40%)](#8-dominio-2--arquitectura-y-servicios-de-azure-3540)
9. [Dominio 3 — Administración y gobernanza de Azure (30–35%)](#9-dominio-3--administración-y-gobernanza-de-azure-3035)
   *(cada dominio incluye objetivos oficiales de Microsoft Learn, explicación a fondo, escenarios resueltos y banco de preguntas)*

**PARTE IV — REFUERZO Y MEMORIZACIÓN**
10. [Pares de conceptos que más se confunden](#10-pares-de-conceptos-que-más-se-confunden)
11. [Mnemotecnias y trucos de memoria](#11-mnemotecnias-y-trucos-de-memoria)
12. [Hojas de referencia rápida (cheat sheets)](#12-hojas-de-referencia-rápida)
13. [Glosario maestro](#13-glosario-maestro)

**PARTE V — PRÁCTICA Y EXAMEN**
14. [Banco de preguntas por dominio](#14-banco-de-preguntas-por-dominio)
15. [Simulacro de examen integrador](#15-simulacro-de-examen-integrador)
16. [Estrategia para el día del examen](#16-estrategia-para-el-día-del-examen)
17. [Recursos y siguientes pasos](#17-recursos-y-siguientes-pasos)
18. [Checklist final antes de agendar](#18-checklist-final-antes-de-agendar)

**PARTE VI — APÉNDICES**
- [Apéndice A — Metodología de creación de este manual (playbook reproducible)](#apéndice-a--metodología-de-creación-de-este-manual-playbook-reproducible)
- [Apéndice B — Registro de elaboración de este manual (AZ-900)](#apéndice-b--registro-de-elaboración-de-este-manual-az-900)

---
---

# PARTE I — FUNDAMENTOS Y MÉTODO DE ESTUDIO

## 1. Qué es la AZ-900 y por qué vale la pena

La **AZ-900 (Microsoft Azure Fundamentals)** es la certificación de entrada al ecosistema de Microsoft Azure, la plataforma de nube de Microsoft. Es la credencial de nube más tomada del mundo y el punto de partida natural para cualquier carrera en la nube.

**Qué demuestra:** que comprendes los conceptos fundamentales de la computación en la nube en general y de Azure en particular — qué es la nube, cuáles son los servicios principales de Azure, y cómo se administra, gobierna y paga la plataforma.

**Qué NO es:** no es una certificación técnica de implementación. No mide si puedes configurar una red compleja o programar; mide si puedes **describir y entender** los conceptos y servicios. El verbo que domina todo el temario oficial es "*describir*".

### ¿Por qué vale la pena?

- **Es la puerta de entrada.** Da credibilidad, abre entrevistas y establece la mentalidad base para certificaciones de rol posteriores (AZ-104 Administrador, AZ-204 Desarrollador, AZ-305 Arquitecto, AZ-400 DevOps, AZ-500 Seguridad).
- **No tiene prerrequisitos.** Puedes presentarla en tu primer día en la nube.
- **No caduca nunca.** Las certificaciones *Fundamentals* de Microsoft son credenciales de por vida; no hay que renovarlas.
- **Sirve a perfiles técnicos y no técnicos por igual.** Desde un vendedor o gerente de proyecto que necesita hablar el idioma de la nube, hasta un administrador de sistemas que migra de la TI tradicional.

### ¿Para quién es este manual?

| Perfil | Cómo usarlo |
|---|---|
| **Principiante absoluto** (cero conocimiento de TI) | Empieza por la Parte II (Capítulo 0). No te saltes nada. |
| **Persona con algo de base** (usa computadoras, entiende lo básico) | Hojea el Capítulo 0 y concéntrate en la Parte III. |
| **Profesional de TI tradicional** | Usa la Parte III como mapeo de tus conocimientos a Azure; enfócate en lo específico de la nube. |
| **Experto que solo quiere certificarse** | Usa las Partes IV y V (referencia rápida y práctica) para validar y pulir. |

> 💡 **Idea central que debes interiorizar desde ya:** el examen mide comprensión conceptual, no memorización mecánica. Para cada servicio, la pregunta clave que debes poder responder es **"¿qué problema resuelve y cuándo lo usaría?"**. Si entiendes eso, respondes correctamente incluso preguntas que nunca habías visto.

---

## 2. Anatomía del examen

Conocer el examen *antes* de estudiar te da una ventaja enorme: sabes hacia dónde apuntar.

### Datos oficiales

| Aspecto | Detalle |
|---|---|
| **Código** | AZ-900 |
| **Nombre completo** | Microsoft Azure Fundamentals |
| **Costo** | ~99 USD (varía por país; en México se ajusta a la región) |
| **Duración** | ~45 minutos de examen (el tiempo total de asiento, con instrucciones, es algo mayor) |
| **N.º de preguntas** | Aproximadamente 40–60 (varía según la versión que te toque) |
| **Puntaje para aprobar** | **700 sobre 1000** |
| **Modalidad** | En línea con supervisión remota (desde casa) o en centro físico Pearson VUE |
| **Idiomas** | Inglés, **español**, japonés, chino, coreano, alemán, francés, italiano, portugués, ruso, árabe, indonesio |
| **Reintentos** | Si repruebas, puedes repetir 24 h después del primer intento (los siguientes reintentos tienen esperas mayores) |
| **Vigencia** | No caduca |

### Entendiendo el puntaje 700/1000 (esto confunde a muchos)

El puntaje **no es un porcentaje directo de respuestas correctas**. Es una **escala ponderada** de 1 a 1000, donde 700 es el mínimo para aprobar. Como las preguntas tienen distinto peso, **700 no equivale exactamente a "70% de respuestas correctas"**. En la práctica, apuntar a responder bien el ~80% o más te da un margen cómodo.

🔑 **Clave:** no necesitas el examen perfecto. Puedes fallar varias preguntas y aprobar. Esto debe **quitarte presión**, no dártela: si una pregunta te bloquea, márcala y sigue.

### Los tipos de preguntas que enfrentarás

El examen NO es solo opción múltiple simple. Familiarízate con estos formatos (puedes practicar la interfaz real en el *exam sandbox* — sección 17):

| Tipo | Cómo funciona | Estrategia |
|---|---|---|
| **Opción múltiple** | Eliges 1 respuesta correcta entre 4 opciones. | El formato más común. Descarta las claramente falsas primero. |
| **Selección múltiple** | "Selecciona TODAS las que apliquen" (2 o más correctas). | **No hay puntos parciales**: debes acertar todas. Evalúa cada opción como verdadero/falso independiente. |
| **Verdadero/Falso por afirmación** | Te dan un enunciado base y 3 afirmaciones; marcas Sí/No en cada una. | Lee cada afirmación de forma aislada; no dejes que una influya en otra. |
| **Arrastrar y soltar** (*drag and drop*) | Emparejas conceptos con sus definiciones o los ordenas. | Aquí se gana fácil si dominas el glosario. Empieza por los que tengas 100% seguros. |
| **Lista desplegable** (*dropdown*) | Completas una frase eligiendo la palabra correcta de un menú. | La terminología exacta importa muchísimo aquí. |
| **Áreas activas / Hot area** | Marcas zonas correctas en una imagen o tabla. | Lee bien qué te piden marcar. |

### Las tres áreas de habilidades (dominios) y su peso oficial

| # | Dominio | Peso | N.º aprox. de preguntas | Prioridad |
|---|---|---|---|---|
| 1 | Describir conceptos de la nube | **25–30%** | ~10–17 | Media |
| 2 | Describir arquitectura y servicios de Azure | **35–40%** | ~14–24 | **Máxima (el más grande)** |
| 3 | Describir administración y gobernanza de Azure | **30–35%** | ~12–21 | **Alta (el más subestimado)** |

⚠️ **Trampa de planeación:** la mayoría de candidatos sobre-estudian el Dominio 1 (es el más intuitivo) y descuidan el Dominio 3 (cubre herramientas exclusivas de Azure sin equivalente en TI tradicional). **Dale al Dominio 3 tanto tiempo como al Dominio 2.** Juntos, los dominios 2 y 3 son ~65–75% del examen.

---

## 3. Método de estudio intensivo

No basta con leer. Para apuntar al puntaje máximo, sigue este método probado de aprendizaje activo.

### El ciclo de 5 pasos por cada tema

1. **Lee el concepto en este manual.** Entiende el "qué" y el "para qué" con las analogías.
2. **Refuérzalo en Microsoft Learn** (usa la caja 📚 de cada sección). El contenido oficial añade matices y, sobre todo, **laboratorios prácticos gratuitos**.
3. **Haz el laboratorio.** Ver el servicio en la consola real de Azure fija el conocimiento como ningún texto puede.
4. **Resuelve las preguntas de práctica** del manual (Parte V). Si fallas una, vuelve al concepto.
5. **Explícalo en voz alta** como si se lo enseñaras a alguien. Si puedes explicarlo simple, lo dominas (técnica Feynman).

### Principios de estudio que multiplican resultados

- **Recuperación activa:** no releas pasivamente. Tápate la respuesta e intenta recordarla. El esfuerzo de recordar es lo que graba la memoria.
- **Repetición espaciada:** repasa los pares confundibles (sección 10) y el glosario (sección 13) varias veces a lo largo de los días, no todo de golpe.
- **Enfócate en distinciones, no en hechos sueltos:** el examen vive de contrastes (confiabilidad vs. predictibilidad, VPN vs. ExpressRoute). Estudia los conceptos *en pares*, comparándolos.
- **Práctica hasta el 80%+:** no agendes el examen hasta sacar consistentemente más del 80% en la evaluación de práctica oficial.

### Qué cubre este manual y qué no (expectativas honestas)

**Sí cubre:** el 100% de los temas del temario oficial, explicados desde cero, con ejemplos, mapeo exacto a Microsoft Learn, banco de preguntas y simulacros.

**Complementos que recomiendo encarecidamente (gratuitos):**
- **Los laboratorios prácticos de Microsoft Learn** — la experiencia en la consola real es insustituible.
- **La evaluación de práctica oficial** — es el termómetro más fiel de tu preparación.

> 🎯 **En una frase:** este manual + los laboratorios de las 3 rutas de Microsoft Learn + la evaluación de práctica oficial = una preparación de nivel mundial para presentarte con confianza. El resultado dependerá de cómo lo estudies, pero tendrás todo lo necesario a tu alcance.

---

## 4. Mapa completo de Microsoft Learn

Esta es la respuesta directa a "no sé por dónde empezar en Microsoft Learn". El problema es que el catálogo tiene cientos de módulos sueltos. **La solución:** existe **una ruta oficial diseñada exactamente para la AZ-900**, una serie de 4 partes llamada **"Introduction to Cloud Infrastructure"** (anteriormente "Microsoft Azure Fundamentals"). Son **12 módulos** repartidos en 3 rutas principales (+ una cuarta de proyectos).

> 📌 **Truco de idioma:** las URLs apuntan a la versión en inglés (`/en-us/`). Para verlas en español, cambia `en-us` por `es-es` en la barra de direcciones. La mayoría del contenido está traducido.

### Paso 0 — Preparación (antes de empezar cualquier ruta)

- **Crea tu cuenta gratuita de Microsoft Learn** y conéctala a tu perfil → guarda tu progreso y tus logros.
- **Crea tu cuenta gratuita de Azure** → https://azure.microsoft.com/es-es/free/ (incluye crédito inicial y servicios gratuitos; necesaria para los laboratorios).
- **Ten a la mano la guía de estudio oficial** → https://aka.ms/AZ900-StudyGuide

### 🛤️ RUTA 1 — Describir conceptos de la nube (Dominio 1)
**3 módulos.** 🔗 https://learn.microsoft.com/es-es/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/

| # | Módulo | URL |
|---|---|---|
| 1.1 | Describir la informática en la nube | https://learn.microsoft.com/es-es/training/modules/describe-cloud-compute/ |
| 1.2 | Describir las ventajas de usar servicios en la nube | https://learn.microsoft.com/es-es/training/modules/describe-benefits-use-cloud-services/ |
| 1.3 | Describir los tipos de servicios en la nube | https://learn.microsoft.com/es-es/training/modules/describe-cloud-service-types/ |

### 🛤️ RUTA 2 — Describir la arquitectura y los servicios de Azure (Dominio 2)
**5 módulos. El bloque más grande, con laboratorios prácticos.** 🔗 https://learn.microsoft.com/es-es/training/paths/azure-fundamentals-describe-azure-architecture-services/

| # | Módulo | URL |
|---|---|---|
| 2.1 | Describir los componentes arquitectónicos principales de Azure | https://learn.microsoft.com/es-es/training/modules/describe-core-architectural-components-of-azure/ |
| 2.2 | Describir los servicios de proceso (cómputo) de Azure | https://learn.microsoft.com/es-es/training/modules/describe-azure-compute-networking-services/ |
| 2.3 | Describir los servicios de red de Azure | https://learn.microsoft.com/es-es/training/modules/describe-azure-networking-services/ |
| 2.4 | Describir los servicios de almacenamiento de Azure | https://learn.microsoft.com/es-es/training/modules/describe-azure-storage-services/ |
| 2.5 | Describir la identidad, el acceso y la seguridad de Azure | https://learn.microsoft.com/es-es/training/modules/describe-azure-identity-access-security/ |

### 🛤️ RUTA 3 — Describir la administración y la gobernanza de Azure (Dominio 3)
**4 módulos.** 🔗 https://learn.microsoft.com/es-es/training/paths/describe-azure-management-governance/

| # | Módulo | URL |
|---|---|---|
| 3.1 | Describir la administración de costos en Azure | https://learn.microsoft.com/es-es/training/modules/describe-cost-management-azure/ |
| 3.2 | Describir características y herramientas de Azure para la gobernanza y el cumplimiento | https://learn.microsoft.com/es-es/training/modules/describe-features-tools-azure-for-governance-compliance/ |
| 3.3 | Describir características y herramientas para administrar e implementar recursos de Azure | https://learn.microsoft.com/es-es/training/modules/describe-features-tools-manage-deploy-azure-resources/ |
| 3.4 | Describir las herramientas de supervisión de Azure | https://learn.microsoft.com/es-es/training/modules/describe-monitoring-tools-azure/ |

### 🛤️ RUTA 4 (opcional pero muy recomendada) — Aplicar habilidades de Azure en proyectos guiados
Proyectos prácticos que consolidan todo lo aprendido. No es obligatoria para aprobar, pero afianza enormemente.
🔗 https://learn.microsoft.com/es-es/training/paths/introduction-cloud-infrastructure-apply-azure-skills-guided-projects/

### Resumen visual del mapa

```
SERIE "Introduction to Cloud Infrastructure" (preparación oficial AZ-900)
│
├── RUTA 1: Conceptos de la nube ........... 3 módulos → Dominio 1 (25–30%)
├── RUTA 2: Arquitectura y servicios ....... 5 módulos → Dominio 2 (35–40%)
├── RUTA 3: Administración y gobernanza .... 4 módulos → Dominio 3 (30–35%)
└── RUTA 4: Proyectos guiados (práctica) ... opcional
                                            ─────────
                                            12 módulos núcleo
```

---

## 5. Plan de estudio con calendario

Plan realista para un principiante dedicando **5–8 horas por semana**. Cada semana combina lectura del manual + módulo de Microsoft Learn + laboratorios + preguntas.

| Semana | Foco | Manual | Microsoft Learn | Práctica |
|---|---|---|---|---|
| **0** | Base de TI | Capítulo 0 | — | — |
| **1** | Conceptos de la nube | Dominio 1 | Ruta 1 (módulos 1.1–1.3) | Preguntas Dominio 1 |
| **2** | Arquitectura + cómputo | Dominio 2 (8.1–8.2) | Ruta 2 (módulos 2.1–2.2) + labs | — |
| **3** | Redes + almacenamiento + identidad | Dominio 2 (8.3–8.5) | Ruta 2 (módulos 2.3–2.5) + labs | Preguntas Dominio 2 |
| **4** | Administración y gobernanza | Dominio 3 | Ruta 3 (módulos 3.1–3.4) + labs | Preguntas Dominio 3 |
| **5** | Repaso + simulacros | Partes IV y V | Ruta 4 (opcional) | Simulacro + evaluación oficial |

**Ritmos alternativos:**
- **Intensivo (1–2 semanas):** para quien ya tiene base de TI o puede dedicar tiempo completo. Comprime una semana en 2–3 días.
- **Relajado (6–8 semanas):** un módulo cada pocos días. Ideal si estudias en ratos libres.

> ✅ **Regla de oro para agendar:** no fijes fecha de examen hasta sacar **>80% de forma consistente** en la evaluación de práctica oficial. Cuando eso pase, agenda pronto — no dejes enfriar el conocimiento.

---
---
# PARTE II — CONOCIMIENTO BASE

## 6. Capítulo 0: Fundamentos de TI desde cero

> 🟢 **¿Para quién es este capítulo?** Para quien viene de **cero absoluto** y quiere que el resto del manual se entienda sin tropiezos. Si ya trabajas en TI, hojéalo rápido y salta al Dominio 1. Aquí no hay nada que el examen pregunte directamente, pero sí el vocabulario que todo lo demás da por sabido.

### 6.1 ¿Qué es la computación, en el fondo?

Toda la tecnología que vamos a estudiar se reduce a tres cosas que una computadora hace: **procesar** (calcular cosas), **almacenar** (guardar datos) y **comunicar** (mover datos por una red). Azure es, en esencia, un proveedor que te renta esas tres capacidades a escala gigantesca. Cuando entiendas que casi todo servicio de Azure cae en "procesar", "almacenar" o "conectar", el panorama se ordena solo.

### 6.2 ¿Qué es un servidor?

Un **servidor** es una computadora —normalmente potente y siempre encendida— cuyo trabajo es *dar un servicio* a otras computadoras a través de una red. Cuando abres una página web, un servidor en algún lugar te la está "sirviendo". Los servidores no suelen tener pantalla ni teclado; viven apilados en estanterías dentro de centros de datos.

🏢 **Analogía:** un servidor es como el cocinero de un restaurante. Tú (el cliente) pides algo desde tu mesa (tu navegador o app), y el cocinero prepara y entrega el platillo (la página, el archivo, el dato). Hay muchos comensales (usuarios) y el cocinero atiende a todos.

### 6.3 ¿Qué es un centro de datos (*datacenter*)?

Un **edificio lleno de servidores**, con suministro eléctrico redundante, refrigeración industrial y conexiones de internet de alta velocidad, funcionando 24/7. Microsoft tiene cientos de centros de datos repartidos por el mundo. Cuando usas la nube, tus datos y tus programas viven físicamente en uno (o varios) de esos edificios.

### 6.4 ¿Qué es "on-premises" (o "local")?

"**On-premises**" (a veces escrito "on-prem" o traducido como "local") significa que una empresa tiene **sus propios servidores en su propio edificio**, y ella misma los compra, instala, mantiene, repara y reemplaza. Es el modelo tradicional, anterior a la nube.

🏠 **Analogía:** on-premises es ser **dueño de un coche** — lo compras, pagas seguro, lo reparas, lo guardas en tu cochera. La **nube** es usar un servicio de transporte por viaje — pagas solo cuando lo usas y nunca te preocupas por el mantenimiento. Ninguno es "mejor" siempre; dependen de tus necesidades.

### 6.5 Virtualización y máquinas virtuales (VM)

La **virtualización** es la tecnología que permite dividir un servidor físico potente en **varias computadoras independientes hechas de software**. Cada una de esas computadoras simuladas es una **máquina virtual (VM)**, y se comporta como una computadora completa: tiene su propio sistema operativo, su memoria, su disco… aunque todas comparten el mismo hardware físico por debajo.

🍰 **Analogía:** un servidor físico es un pastel grande. La virtualización lo corta en rebanadas. Cada rebanada (VM) parece un pastelito completo e independiente. Así, un solo servidor físico puede alojar 10 VMs de 10 clientes distintos sin que se estorben ni se vean entre sí.

💡 **Por qué importa para la nube:** la virtualización es la magia que hace posible la nube pública. Microsoft compra servidores físicos enormes y, mediante virtualización, te renta "rebanadas" (VMs) del tamaño que necesites, por el tiempo que las necesites.

### 6.6 Sistema operativo (SO)

El **software base** que hace funcionar una computadora y sobre el cual corren todos los demás programas. Gestiona la memoria, el procesador, los archivos. Los más comunes en servidores son **Windows Server** y **Linux** (en sus muchas variantes). Toda máquina virtual necesita un SO instalado.

### 6.7 Redes y direcciones IP

Una **red** es el conjunto de conexiones (cables, fibra óptica, señales) que permite que las computadoras se comuniquen entre sí. **Internet** es, simplemente, la red de redes a escala mundial.

Una **dirección IP** (Internet Protocol) es como el "número telefónico" o la "dirección postal" única de cada dispositivo en una red. Permite que los datos sepan a dónde ir y de dónde vienen. Ejemplo: `192.168.1.10`. Hay direcciones **públicas** (visibles desde internet, como la dirección de tu casa) y **privadas** (solo válidas dentro de una red interna, como el número de oficina dentro de un edificio).

📡 **Conceptos de red que verás:**
- **DNS (Domain Name System):** la "agenda de contactos" de internet. Traduce nombres fáciles de recordar (`www.ejemplo.com`) a las direcciones IP numéricas que las máquinas usan.
- **Firewall:** un "portero" que filtra qué tráfico de red puede entrar o salir, según reglas de seguridad.
- **Latencia:** el retardo en que un dato viaja de un punto a otro. Menos latencia = más rápido.

### 6.8 Bases de datos

Un programa especializado en **guardar, organizar y consultar información** de forma eficiente y confiable. Cuando una aplicación recuerda tu usuario, tus pedidos, tus mensajes o tu saldo, esos datos viven en una base de datos.

- **Bases de datos relacionales (SQL):** organizan los datos en **tablas** con filas y columnas, como una hoja de cálculo gigante y muy ordenada, con relaciones entre tablas. Ideales para datos estructurados (ej. clientes, facturas). Ejemplo en Azure: **Azure SQL Database**.
- **Bases de datos no relacionales (NoSQL):** más flexibles; guardan datos que no encajan bien en tablas rígidas (documentos, pares clave-valor, gráficos). Ideales para datos variados o a gran escala. Ejemplo en Azure: **Azure Cosmos DB**.

### 6.9 El concepto de "escalar"

**Escalar** significa ajustar la cantidad de recursos (potencia de cálculo, número de máquinas, almacenamiento) que tiene tu sistema según cuánta demanda recibe. Si tu tienda online recibe 10 visitas al día, necesitas pocos recursos; durante una gran oferta con 100.000 visitas simultáneas, necesitas muchísimos más. Escalar es subir o bajar esa capacidad — y una de las grandes ventajas de la nube es que puede hacerlo **automáticamente y al instante**.

### 6.10 Los actores: cliente y proveedor de nube

- **Proveedor de nube:** la empresa dueña de los centros de datos que renta capacidad de cómputo. En este manual: **Microsoft (Azure)**. Sus competidores principales son Amazon (AWS) y Google (Google Cloud).
- **Cliente / inquilino (*tenant*):** tú o tu organización, que renta y usa esos servicios. En Azure, tu "espacio" aislado dentro de la plataforma se llama *tenant* (inquilino).

### 6.11 Mini-glosario express de este capítulo

| Palabra | En una línea |
|---|---|
| **Hardware** | Las partes físicas que puedes tocar (la máquina, los cables). |
| **Software** | Los programas e instrucciones (lo que no puedes tocar). |
| **Middleware** | Software "intermedio" que conecta el sistema operativo con las aplicaciones (ej. el motor que ejecuta una app web). |
| **Aplicación / app** | Un programa que hace una tarea para el usuario (una web, un sistema de facturación). |
| **Parche** (*patch*) | Una actualización que corrige errores o cierra fallos de seguridad. |
| **Telemetría** | Datos que un sistema reporta sobre sí mismo (uso de CPU, errores, tiempos de respuesta). |
| **Cifrado** (*encryption*) | Convertir datos en código ilegible para protegerlos de quien no debe verlos. |
| **Egress / Ingress** | Salida de datos / entrada de datos. (En Azure, la **salida** suele costar dinero; la entrada normalmente es gratis.) |
| **Implementar / desplegar** (*deploy*) | Poner en funcionamiento un recurso o aplicación. |
| **Instancia** | Una copia individual en ejecución de un recurso (ej. "tres instancias de una VM" = tres VMs iguales corriendo). |
| **Carga de trabajo** (*workload*) | El conjunto de tareas o aplicaciones que se ejecutan (ej. "la carga de trabajo de facturación"). |
| **Redundancia** | Tener copias o componentes de respaldo para que, si uno falla, otro siga. |
| **Tolerancia a fallos** | La capacidad de un sistema de seguir funcionando aunque algo falle. |

> ✅ **Con esto ya tienes el vocabulario base.** A partir de aquí, todo el manual se entenderá con naturalidad. Avancemos al corazón del temario.

---
---

# PARTE III — LOS TRES DOMINIOS EN PROFUNDIDAD

> **Cómo leer esta parte.** Cada dominio abre con una caja que reproduce los **objetivos de aprendizaje oficiales** de los módulos de Microsoft Learn correspondientes y la lista de **unidades** que los componen — así sabes exactamente qué evalúa Microsoft y puedes cotejar tu avance unidad por unidad. Luego cada concepto se explica en profundidad: qué es, cómo funciona, cuándo usarlo (y cuándo no), un ejemplo concreto, la clave de examen y la trampa habitual. Al final de cada dominio hay **escenarios resueltos** (razonados paso a paso) y un enlace al banco de preguntas.

---

## 7. Dominio 1 — Conceptos de la nube (25–30%)

> <span class="badge b-learn">MS LEARN</span> **RUTA 1 completa** — *"Introduction to Cloud Infrastructure: Describe cloud concepts"* (3 módulos, 8+9+9 unidades).
> 🔗 https://learn.microsoft.com/es-es/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/

> **🎓 Objetivos de aprendizaje oficiales de este dominio** (traducidos de Microsoft Learn):
> - Definir la computación en la nube.
> - Describir el modelo de responsabilidad compartida.
> - Definir los modelos de nube: pública, privada e híbrida.
> - Identificar los casos de uso apropiados para cada modelo de nube.
> - Describir el modelo basado en consumo.
> - Comparar los modelos de precios de la nube.
> - Describir las ventajas de la alta disponibilidad y la escalabilidad.
> - Describir los beneficios de la confiabilidad y la predictibilidad.
> - Describir los beneficios de la seguridad y la gobernanza.
> - Describir la capacidad de administración en la nube.
> - Describir IaaS, PaaS y SaaS, y los casos de uso de cada uno.

Este dominio establece el **vocabulario y los marcos mentales** sobre los que se construye todo lo demás. Es el más intuitivo, pero Microsoft usa su terminología con **precisión quirúrgica**: muchas preguntas-trampa explotan diferencias sutiles entre términos parecidos. No basta con "entender la idea": hay que conocer la **definición exacta** de cada término y saber **distinguirlo de su vecino**.

---

### 7.1 ¿Qué es la computación en la nube?

> <span class="badge b-learn">MS LEARN</span> **Módulo 1.1 — *Describir la informática en la nube*** (8 unidades: introducción · qué es la nube · responsabilidad compartida · modelos de nube · modelo basado en consumo · evaluación · resumen).
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-cloud-compute/

La **computación en la nube** (*cloud computing*) es la entrega de servicios de cómputo —servidores, almacenamiento, bases de datos, redes, software, análisis e inteligencia— **a través de internet** ("la nube"), con un modelo de **pago por uso**. En lugar de comprar y mantener tu propia infraestructura física, "alquilas" exactamente lo que necesitas del proveedor, cuando lo necesitas, y lo liberas cuando terminas.

**Desglosemos la definición, porque cada parte importa:**
- *"Servicios de cómputo"* → no es solo "servidores"; incluye capacidad de procesamiento, almacenamiento, redes, bases de datos, IA y más.
- *"A través de internet"* → accedes a ellos de forma remota, sin tenerlos físicamente.
- *"Pago por uso"* → no compras el equipo; pagas por el consumo, como un servicio público.

🏠 **Analogía (interiorízala, vuelve mucho):** la nube es como la **electricidad** de tu casa. No construyes tu propia planta eléctrica, ni almacenas energía, ni contratas técnicos para mantenerla: simplemente enchufas tus aparatos y pagas por los kilovatios que consumes. Si un mes usas más, pagas más; si te vas de viaje, pagas casi nada. La nube hace exactamente eso, pero con **poder de cómputo**: te "enchufas" y pagas por lo que usas.

💡 **Por qué fue una revolución (contexto que ayuda a razonar las preguntas):** antes de la nube, lanzar una aplicación implicaba *comprar* servidores físicos (decenas de miles de dólares), *esperar* semanas a que llegaran, *instalarlos*, *mantenerlos* y, si crecías, *volver a comprar*. Si sobreestimabas la demanda, desperdiciabas dinero en equipo ocioso; si la subestimabas, tu servicio se caía. La nube elimina ese dilema: creas recursos en **minutos**, pagas solo por lo que usas, y escalas hacia arriba o hacia abajo al instante. Toda la lógica del examen —beneficios, modelos de precios, escalabilidad— se entiende mejor cuando recuerdas el problema que la nube vino a resolver.

#### 7.1.1 El modelo de responsabilidad compartida (a fondo)

Es uno de los conceptos **más preguntados de todo el examen**, así que vamos despacio y completo.

**El principio:** cuando usas la nube, la responsabilidad de mantener y asegurar el sistema completo **se reparte entre tú (cliente) y Microsoft (proveedor)**. La frontera exacta de "quién hace qué" **se mueve según el tipo de servicio** (IaaS, PaaS o SaaS). La regla general: **cuanto más administrado es el servicio, más responsabilidad asume Microsoft y menos tú.**

**Por qué existe este modelo:** en la TI tradicional (on-premises), tú eras responsable de *absolutamente todo*: desde el edificio y la electricidad hasta el último parche de software. En la nube, Microsoft se hace cargo de las capas físicas (que tú ya no controlas porque están en *sus* centros de datos), y tú conservas la responsabilidad de lo que sí controlas (tus datos, quién accede, cómo configuras).

**Reparto detallado de responsabilidades:**

| Capa | ¿Quién es responsable? | Por qué |
|---|---|---|
| **Información y datos** | **Siempre el cliente** | Son *tus* datos; solo tú decides su valor y quién los ve. |
| **Dispositivos** (móviles, PCs) | **Siempre el cliente** | Los equipos desde los que accedes son tuyos. |
| **Cuentas e identidades** | **Siempre el cliente** | Tú gestionas quién tiene credenciales y qué tan seguras son. |
| **Identidad e infraestructura de directorio** | **Compartida** | Depende del modelo de servicio. |
| **Aplicaciones** | **Compartida** | En IaaS las gestionas tú; en SaaS, Microsoft. |
| **Controles de red** | **Compartida** | Según el modelo. |
| **Sistema operativo** | **Compartida** | Tú en IaaS; Microsoft en PaaS/SaaS. |
| **Hosts físicos** (servidores) | **Siempre Microsoft** | Están en sus centros de datos. |
| **Red física** | **Siempre Microsoft** | Infraestructura del proveedor. |
| **Centro de datos físico** | **Siempre Microsoft** | El edificio y su seguridad son de Microsoft. |

🔑 **Clave de examen (memorízala literalmente):** *el cliente SIEMPRE es responsable de sus **datos**, sus **dispositivos** y sus **identidades/cuentas**, sin importar el modelo.* *Microsoft SIEMPRE es responsable de lo **físico** (hosts, red física, centros de datos).* Lo intermedio (SO, red, aplicaciones) **se reparte** según IaaS/PaaS/SaaS.

⚠️ **Trampa común #1:** "¿Quién es responsable de proteger los **datos** de los clientes / la confidencialidad de la información?" → **Siempre el cliente**, aunque uses SaaS. Microsoft protege la infraestructura, pero la responsabilidad de *tus datos y de quién accede a ellos* nunca se transfiere.

⚠️ **Trampa común #2:** "En un modelo **SaaS**, ¿de quién es la responsabilidad del **sistema operativo**?" → De **Microsoft** (en SaaS, Microsoft gestiona prácticamente todo salvo tus datos e identidades).

#### 7.1.2 Modelos de implementación (*deployment models*) — explicados a fondo

Definen **dónde** vive y **quién posee** la infraestructura. Son tres, y el examen pregunta cuál encaja en un escenario dado.

**1) Nube pública**
- **Qué es:** infraestructura propiedad de Microsoft, operada por Microsoft, **compartida** entre muchos clientes ("multi-inquilino"), accesible por internet.
- **Cómo funciona:** tú no posees ningún hardware; rentas capacidad lógica sobre la infraestructura compartida de Microsoft.
- **Ventajas:** sin inversión inicial en hardware; escalabilidad casi ilimitada; sin mantenimiento de equipo; pagas solo por uso.
- **Desventajas:** menos control sobre la infraestructura; recursos físicos compartidos (aunque lógicamente aislados).
- **Cuándo usarla:** la mayoría de cargas modernas; startups; cualquiera que quiera agilidad y costo variable.
- 💡 **Ejemplo:** una startup lanza su app sin comprar un solo servidor, usando VMs y bases de datos de Azure.

**2) Nube privada**
- **Qué es:** infraestructura de nube usada **exclusivamente por una sola organización**. Puede estar en el centro de datos propio de la empresa o alojada por un tercero, pero **dedicada** solo a ella.
- **Cómo funciona:** se construye la tecnología de nube (autoservicio, virtualización, escalado) sobre hardware de uso exclusivo.
- **Ventajas:** máximo control y personalización; cumple requisitos regulatorios estrictos sobre dónde y cómo viven los datos.
- **Desventajas:** costosa (tú asumes el hardware y su mantenimiento); menos elástica que la pública.
- **Cuándo usarla:** banca, salud, gobierno, o cualquier sector con normativas que exigen aislamiento total.
- 💡 **Ejemplo:** un banco mantiene los datos de clientes en su propia nube privada por exigencia regulatoria.

**3) Nube híbrida**
- **Qué es:** **combina** nube pública y privada (o nube y on-premises), permitiendo que datos y aplicaciones se muevan entre ambas.
- **Cómo funciona:** se conectan ambos entornos para que operen de forma coordinada.
- **Ventajas:** flexibilidad máxima; mantienes lo sensible en privado y aprovechas la escala/economía de lo público; permite migrar gradualmente.
- **Desventajas:** más compleja de diseñar y gestionar.
- **Cuándo usarla:** empresas en transición a la nube; cargas con partes sensibles y partes que necesitan escalar.
- 💡 **Ejemplo:** un hospital guarda historiales médicos en su nube privada (por ley), pero usa la nube pública para su portal de citas, que tiene picos de tráfico.

🔑 **Clave:** *pública = compartida del proveedor; privada = exclusiva de una organización; híbrida = combinación de ambas.* Si el escenario menciona "requisito regulatorio de datos en infraestructura dedicada" → privada o híbrida. Si menciona "mover cargas entre su centro de datos y Azure" → híbrida.

#### 7.1.3 El modelo basado en consumo, CapEx vs. OpEx y modelos de precios

La economía de la nube descansa en el **modelo basado en consumo**: **pagas solo por los recursos que usas, sin pago inicial ni compromiso de compra**. Esto cambia la naturaleza del gasto tecnológico.

**Los dos modelos de gasto (term clave del examen):**

| | **CapEx** (Gasto de Capital) | **OpEx** (Gasto Operativo) |
|---|---|---|
| **Qué es** | Gran inversión inicial en activos físicos que durarán años. | Gasto recurrente por usar un servicio, sin poseer el activo. |
| **Cuándo se paga** | Por adelantado, una sola vez (luego se deprecia). | De forma continua, según el uso. |
| **Ejemplo** | Comprar 10 servidores y un edificio. | Pagar la factura mensual de Azure por lo consumido. |
| **Modelo** | TI tradicional / on-premises. | La nube. |
| **Riesgo** | Si sobreestimas, desperdicias; si subestimas, te quedas corto. | El costo sigue al uso real; sin desembolso inicial. |

🔑 **Clave de examen:** *moverse a la nube = pasar de CapEx a OpEx.* Ventajas del modelo de consumo: (1) sin inversión inicial; (2) sin pagar por capacidad ociosa; (3) pagas más solo cuando necesitas más; (4) puedes dejar de pagar liberando recursos.

💡 **Ejemplo numérico para fijarlo:** montar un servidor on-premises podría costar $5.000 de golpe (CapEx) y servir aunque esté al 10% de uso. En la nube, esa misma carga podría costar $80/mes (OpEx) y, si la apagas de noche y fines de semana, aún menos. Pagas por uso real, no por capacidad instalada.

#### 7.1.4 Serverless (sin servidor)

**Serverless** es un modelo donde el proveedor administra **completamente** la infraestructura subyacente: tú solo aportas tu código o lógica, y pagas exclusivamente por la **ejecución real** (p. ej., por cada invocación).

⚠️ **Trampa de nombre:** "sin servidor" **no significa que no existan servidores**. Existen — pero tú no los ves, ni los aprovisionas, ni los parchas, ni los escalas. El proveedor hace todo eso de forma invisible y automática. Ejemplo en Azure: **Azure Functions**.

🏠 **Analogía:** serverless es como un **taxi**. No eres dueño del auto, no lo mantienes, no lo estacionas, no contratas al chofer; solo pides el viaje y pagas el trayecto. El auto (servidor) existe, pero su gestión nunca es tu problema.

---

### 7.2 Beneficios de usar servicios en la nube

> <span class="badge b-learn">MS LEARN</span> **Módulo 1.2 — *Describir las ventajas de usar servicios en la nube***.
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-benefits-use-cloud-services/

Microsoft define cada beneficio con **precisión**, y el examen los confunde a propósito. Estudia **qué significa cada uno** y, sobre todo, **en qué se diferencia del que se le parece**.

#### 7.2.1 Alta disponibilidad y escalabilidad

**Alta disponibilidad (*high availability*)**
- **Definición:** capacidad de mantener el servicio funcionando con **mínimo tiempo de inactividad**, incluso si fallan componentes individuales.
- **Cómo la logra la nube:** infraestructura redundante (varias copias del recurso); si una falla, otra toma el relevo automáticamente. En Azure se refuerza con zonas de disponibilidad.
- **Indicador:** se suele expresar como un **SLA** (acuerdo de nivel de servicio), p. ej. "99,9% de disponibilidad".
- 💡 **Ejemplo:** tu sitio web sigue en línea aunque un servidor concreto se caiga, porque hay otros sirviendo en paralelo.

**Escalabilidad (*scalability*)**
- **Definición:** capacidad de **agregar o quitar recursos** para ajustarse a la demanda.
- **Dos formas (muy preguntadas):**
  - **Vertical (*scale up/down*):** añadir potencia a un recurso existente (más CPU/RAM a la misma VM). Analogía: cambiar tu auto por uno de motor más potente.
  - **Horizontal (*scale out/in*):** añadir más instancias en paralelo (más VMs iguales). Analogía: sumar más autos a la flota.
- **Elasticidad (matiz):** cuando ese ajuste ocurre **automáticamente** según la demanda, se habla de elasticidad.
- 💡 **Ejemplo:** durante una promoción tu tienda escala *horizontalmente* (más instancias) y al terminar las libera, pagando solo por el pico mientras duró.

🔑 **Clave:** alta disponibilidad = *seguir funcionando ante fallos*; escalabilidad = *ajustar recursos a la demanda*. Vertical = máquina más grande; horizontal = más máquinas.

#### 7.2.2 Confiabilidad y predictibilidad (el par-trampa estrella)

**Confiabilidad (*reliability*)**
- **Definición:** capacidad del sistema de **recuperarse de fallas** y seguir operando. Incluye la **recuperación ante desastres**.
- **Cómo la logra la nube:** diseño distribuido y descentralizado; si una región entera falla, otra continúa el servicio.
- 💡 **Ejemplo:** un desastre deja fuera de servicio una región completa, y tu aplicación se restaura desde la región emparejada.

**Predictibilidad (*predictability*)**
- **Definición:** resultados **consistentes y anticipables**. Tiene dos caras:
  - **Predictibilidad del rendimiento:** tu app responde de forma consistente (autoescalado, balanceo de carga lo garantizan).
  - **Predictibilidad del costo:** puedes prever y controlar lo que gastarás (con herramientas de costos, que verás en el Dominio 3).
- 💡 **Ejemplo:** sabes que tu app mantendrá tiempos de respuesta estables bajo carga, y que tu factura rondará un monto previsible.

⚠️ **Trampa clásica (aparece casi siempre):** te dan un escenario y ambas palabras como opciones.
- Si la frase habla de **"recuperarse de una falla / seguir operando tras un problema"** → **confiabilidad**.
- Si habla de **"resultados/costos consistentes y anticipables"** → **predictibilidad**.

#### 7.2.3 Seguridad, gobernanza y manejabilidad

**Seguridad (*security*)**
- **Definición:** conjunto de herramientas y controles para **proteger** tus recursos.
- **Ventaja de la nube:** puedes elegir cuánto delegar — en SaaS, gran parte de la seguridad la asume el proveedor; en IaaS, tienes más control (y más responsabilidad). Microsoft aplica parches, cifrado, protección física, etc.
- 💡 **Ejemplo:** tus datos viajan y se almacenan cifrados; el acceso se controla con identidades y reglas.

**Gobernanza (*governance*)**
- **Definición:** capacidad de **aplicar políticas y estándares** para cumplir normativas y mantener orden y consistencia.
- 💡 **Ejemplo:** forzar por política que todos los recursos lleven una etiqueta de "departamento" o que solo se creen en ciertas regiones (lo verás con Azure Policy en el Dominio 3).

**Manejabilidad (*manageability*)** — tiene dos vertientes que conviene distinguir:
- **Administración *de* la nube:** gestionar tus recursos (escalar, supervisar, configurar alertas, desplegar con plantillas).
- **Administración *en* la nube:** **cómo** interactúas (portal web, CLI, PowerShell, APIs).
- 💡 **Ejemplo:** desplegar 100 servidores idénticos con una sola plantilla, o recibir una alerta automática si un recurso se sobrecarga.

🔑 **Clave:** seguridad = *proteger*; gobernanza = *aplicar reglas/cumplir normas*; manejabilidad = *facilidad de gestionar y de interactuar*.

---

### 7.3 Tipos de servicios en la nube: IaaS, PaaS y SaaS

> <span class="badge b-learn">MS LEARN</span> **Módulo 1.3 — *Describir los tipos de servicios en la nube***.
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-cloud-service-types/

**El concepto más importante del Dominio 1** y uno de los más preguntados del examen. Define **cuánto gestiona el proveedor y cuánto gestionas tú**. La clave es dominar la **división de responsabilidades** en cada nivel y reconocer **casos de uso**.

🍕 **La analogía de la pizza "as a service"** (la mejor para fijarlo). Según cuánto trabajo haces tú para comer pizza:

| Forma de comer pizza | Modelo | Lo que aportas tú | Lo que te dan hecho |
|---|---|---|---|
| Hacerla **desde cero** (cultivas el trigo, amasas, horneas) | **On-premises** | Todo | Nada |
| Comprar **kit + masa** y hornear en casa | **IaaS** | Horno, cocción, mesa, bebida | Ingredientes base |
| Pedirla **a domicilio** | **PaaS** | Mesa, bebida | Pizza lista y cocida |
| Ir al **restaurante** | **SaaS** | Solo tu apetito | Todo: mesa, servicio, pizza |

**Desglose técnico (lo que el examen evalúa):**

**IaaS — Infraestructura como Servicio**
- **Microsoft gestiona:** centros de datos, hardware físico, red física, capa de virtualización.
- **Tú gestionas:** sistema operativo (y sus parches), middleware, tiempo de ejecución, aplicaciones, datos, y buena parte de la configuración de red.
- **Control:** máximo. **Responsabilidad/trabajo:** máximo.
- **Cuándo:** necesitas control total del entorno; vas a migrar servidores existentes tal cual ("lift and shift"); requieres un SO o software muy específico.
- **Ejemplo en Azure:** **Azure Virtual Machines**, redes virtuales.

**PaaS — Plataforma como Servicio**
- **Microsoft gestiona:** todo lo de IaaS **+ el sistema operativo + middleware + entorno de ejecución**.
- **Tú gestionas:** solo **tus aplicaciones y tus datos**.
- **Control:** intermedio. **Responsabilidad/trabajo:** reducido.
- **Cuándo:** quieres **desarrollar y publicar aplicaciones** sin ocuparte de servidores, SO ni parches.
- **Ejemplo en Azure:** **Azure App Service**, **Azure SQL Database**, Azure Functions.

**SaaS — Software como Servicio**
- **Microsoft gestiona:** **prácticamente todo** — infraestructura, SO y la propia aplicación.
- **Tú gestionas:** solo **tus datos y la configuración de tus usuarios/cuentas**.
- **Control:** mínimo. **Responsabilidad/trabajo:** mínimo.
- **Cuándo:** solo quieres **usar un software ya hecho**, sin instalar ni mantener nada.
- **Ejemplo en Azure/Microsoft:** **Microsoft 365** (Outlook, Word/Excel en línea), **Dynamics 365**.

🔑 **Clave mental — la escalera de control vs. comodidad:**
```
IaaS  ───────────►  PaaS  ───────────►  SaaS
◄ más control               menos control ►
◄ más trabajo tuyo          menos trabajo tuyo ►
◄ tú gestionas el SO        Microsoft gestiona el SO ►
```

⚠️ **Trampa frecuente:** te describen quién administra qué y preguntan **el modelo**. La pista decisiva es **el sistema operativo**: si *tú* lo gestionas → **IaaS**; si lo gestiona Microsoft y tú solo tu app → **PaaS**; si solo aportas datos de usuario → **SaaS**.

#### 7.3.1 Casos de uso (las preguntas son de escenario)
- **IaaS** → "Necesito control total del SO para instalar software heredado muy específico" / "voy a mover mis servidores actuales sin rediseñarlos". → **Máquinas virtuales.**
- **PaaS** → "Mi equipo quiere publicar una app web y centrarse en el código, sin administrar servidores ni parchar el SO". → **App Service.**
- **SaaS** → "Solo quiero que mi empresa tenga correo, ofimática y CRM sin montar ni mantener nada". → **Microsoft 365 / Dynamics 365.**

---

### 🧪 Escenarios resueltos — Dominio 1

**Escenario 1.** *Una empresa quiere lanzar una nueva aplicación sin gastar capital en servidores y poder aumentar o reducir la capacidad según la demanda estacional. ¿Qué características de la nube satisfacen estas necesidades?*
**Razonamiento:** "sin gastar capital" → modelo basado en consumo (**OpEx** en vez de CapEx). "Aumentar o reducir según la demanda" → **escalabilidad** (elasticidad). **Respuesta:** modelo de consumo + escalabilidad.

**Escenario 2.** *Tras un incendio que inutiliza un centro de datos completo, el servicio debe restaurarse desde otra ubicación. ¿Qué beneficio de la nube se está aprovechando?*
**Razonamiento:** "restaurarse tras una falla grave" = recuperarse de un desastre → **confiabilidad** (no predictibilidad, que es consistencia). **Respuesta:** confiabilidad.

**Escenario 3.** *Una empresa de desarrollo quiere publicar una API sin administrar el sistema operativo ni aplicar parches, pero conservando el control de su código. ¿Qué modelo de servicio es el más adecuado?*
**Razonamiento:** no quieren gestionar el SO (descarta IaaS) pero sí controlar su aplicación (descarta SaaS) → **PaaS**. **Respuesta:** PaaS (p. ej., Azure App Service).

**Escenario 4.** *En un entorno SaaS, ocurre una filtración porque un empleado usó una contraseña débil y sin MFA. ¿De quién era la responsabilidad de proteger esa identidad?*
**Razonamiento:** las **identidades/cuentas** son responsabilidad del cliente **en todos los modelos**, incluido SaaS. **Respuesta:** del cliente.

### ✅ Resumen del Dominio 1
- **Nube** = cómputo por internet con pago por consumo (OpEx, no CapEx).
- **Responsabilidad compartida:** datos, dispositivos e identidades **siempre del cliente**; lo físico **siempre de Microsoft**; lo intermedio según el modelo.
- **Modelos de implementación:** pública (compartida), privada (exclusiva), híbrida (combinación).
- **Beneficios:** domina las definiciones exactas, sobre todo **confiabilidad** (recuperarse) vs. **predictibilidad** (consistencia); alta disponibilidad vs. escalabilidad; vertical vs. horizontal.
- **IaaS / PaaS / SaaS:** la división de responsabilidades, con el **SO** como pista clave.

*(Banco de preguntas del Dominio 1: sección 14.1.)*

---
---
## 8. Dominio 2 — Arquitectura y servicios de Azure (35–40%)

> <span class="badge b-learn">MS LEARN</span> **RUTA 2 completa** — *"Describe Azure architecture and services"* (5 módulos, con **laboratorios prácticos**).
> 🔗 https://learn.microsoft.com/es-es/training/paths/azure-fundamentals-describe-azure-architecture-services/

> **🎓 Objetivos de aprendizaje oficiales de este dominio:**
> - Describir los componentes principales de la arquitectura física y de administración de Azure (regiones, zonas de disponibilidad, pares de regiones, recursos, grupos de recursos, suscripciones, grupos de administración).
> - Comparar los servicios de cómputo (VMs, contenedores, funciones) y describir opciones de VM (escalado, conjuntos de disponibilidad), recursos de VM y opciones de hospedaje de aplicaciones.
> - Describir las categorías de servicios de IA, machine learning e IoT/Edge.
> - Describir las redes virtuales, VPN Gateway, ExpressRoute y Azure DNS.
> - Comparar los servicios de almacenamiento, niveles, redundancia, y opciones de movimiento/migración de datos.
> - Describir identidad y directorios (Entra ID, Domain Services), métodos de autenticación (SSO, MFA, passwordless), identidades externas, acceso condicional, RBAC, Zero Trust, defensa en profundidad y Defender for Cloud.

**El dominio más grande del examen.** Aquí pasamos de conceptos generales a la **estructura concreta de Azure** y sus servicios. La mayoría de preguntas son **de escenario**: te describen una necesidad y preguntan *"¿qué servicio usarías?"*. La meta no es memorizar nombres sueltos, sino **entender qué problema resuelve cada servicio y cuándo aplica**.

---

### 8.1 Componentes arquitectónicos principales

> <span class="badge b-learn">MS LEARN</span> **Módulo 2.1 — *Describir los componentes arquitectónicos principales de Azure***.
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-core-architectural-components-of-azure/

Azure se organiza en dos capas: una **física** (dónde viven realmente los servidores) y una **lógica/de administración** (cómo organizas y gobiernas tus recursos). Domina ambas.

#### 8.1.1 Estructura física

🏗️ **Analogía maestra:** piensa en Azure como un **país organizado jerárquicamente**: regiones (ciudades), dentro de ellas zonas (barrios con servicios propios), y dentro de cada zona, centros de datos (edificios).

**Centro de datos (*datacenter*)**
- La unidad física más pequeña: una instalación con miles de servidores, energía y refrigeración. No interactúas con él directamente.

**Región (*region*)**
- Un conjunto de centros de datos en un área geográfica, conectados por una red de baja latencia. **Eliges la región** donde creas tus recursos.
- **Por qué importa elegir bien la región:** (1) **cercanía a tus usuarios** (menos latencia); (2) **residencia de datos** (cumplir leyes que exigen que los datos permanezcan en un país); (3) **precio** (varía entre regiones); (4) **disponibilidad de servicios** (no todos los servicios existen en todas las regiones).
- 💡 **Ejemplo:** "Centro de México", "Este de EE. UU.", "Oeste de Europa".

**Zona de disponibilidad (*availability zone*)**
- Una o más instalaciones con **energía, refrigeración y red INDEPENDIENTES**, físicamente separadas, **dentro de una misma región**. Están conectadas por redes rápidas.
- **Para qué sirve:** lograr **alta disponibilidad**. Si distribuyes tu aplicación en varias zonas y una falla (corte eléctrico, incendio), las otras siguen funcionando.
- 🏠 **Analogía:** tres edificios separados en la misma ciudad, cada uno con su propia planta eléctrica y su propia entrada de internet.
- 💡 **Ejemplo:** despliegas tu app en las zonas 1, 2 y 3 de una región; aunque la zona 2 caiga, el servicio continúa.

**Pares de regiones (*region pairs*)**
- Cada región está emparejada con **otra región de la misma geografía**, normalmente a **300+ km** de distancia.
- **Para qué sirve:** **recuperación ante desastres**. Si una región **entera** falla (un desastre natural a gran escala), la región par respalda. Además, las actualizaciones planificadas de Azure se aplican a **una región del par a la vez**, nunca a ambas simultáneamente, reduciendo riesgo.
- 🏠 **Analogía:** dos ciudades hermanadas que se respaldan mutuamente ante una catástrofe.

**Regiones soberanas (*sovereign regions*)**
- Instancias de Azure **físicamente aisladas** del Azure global, para requisitos legales o gubernamentales especiales.
- 💡 **Ejemplos:** **Azure Government** (EE. UU.) y **Azure China** (operado por un socio local, 21Vianet).

🔑 **Clave de examen (distinción que SIEMPRE cae):**
- **Zonas de disponibilidad** → protegen contra fallos **dentro** de una región → **ALTA DISPONIBILIDAD**.
- **Pares de regiones** → protegen contra el fallo de una región **entera** → **RECUPERACIÓN ANTE DESASTRES**.

#### 8.1.2 Estructura lógica: jerarquía de administración

Organiza **tus recursos** y permite aplicar permisos, políticas y facturación de forma ordenada. De mayor a menor alcance:

```
GRUPOS DE ADMINISTRACIÓN  (agrupan suscripciones; políticas/permisos centralizados)
   └── SUSCRIPCIONES        (unidad de facturación y de límites/cuotas)
        └── GRUPOS DE RECURSOS  (contenedores lógicos de recursos relacionados)
             └── RECURSOS          (VMs, bases de datos, redes... lo que usas)
```

**Recurso (*resource*)**
- Cualquier servicio individual que creas (una VM, una base de datos, una red virtual, una cuenta de almacenamiento). Es la pieza concreta.
- **Regla:** cada recurso vive en **un solo** grupo de recursos (aunque puede moverse a otro).

**Grupo de recursos (*resource group*)**
- Contenedor **lógico** que agrupa recursos relacionados (típicamente, los de un mismo proyecto o ciclo de vida).
- **Para qué sirve:** gestionarlos **en bloque** — crearlos, eliminarlos o asignar permisos juntos.
- **Reglas clave:** si eliminas el grupo, **se eliminan TODOS los recursos dentro**; un recurso pertenece a un único grupo; los recursos de un grupo pueden estar en distintas regiones.
- 💡 **Ejemplo:** un grupo "CampañaVerano" con la web, su base de datos y su almacenamiento; al terminar la campaña, borras el grupo y se va todo junto.

**Suscripción (*subscription*)**
- Unidad de **facturación** y de **límites de acceso/cuotas**. Agrupa grupos de recursos.
- **Para qué sirve:** separar costos y accesos por departamento, proyecto o entorno; cada suscripción genera su **propia factura**. Las organizaciones pueden tener varias.
- 💡 **Ejemplo:** una suscripción "Producción" y otra "Pruebas", para que el gasto y los permisos no se mezclen.

**Grupo de administración (*management group*)**
- Contenedor **por encima** de las suscripciones; agrupa varias de ellas (y puede anidarse).
- **Para qué sirve:** aplicar **políticas y permisos (RBAC) a muchas suscripciones a la vez**, de forma centralizada. Esencial en organizaciones grandes.
- 💡 **Ejemplo:** un grupo de administración "Empresa" aplica una política de seguridad que heredan automáticamente todas las suscripciones de la organización.

🔑 **Clave:** memoriza el orden **Grupo de administración → Suscripción → Grupo de recursos → Recurso**. La **suscripción** es la **facturación**; el **grupo de recursos** es el contenedor lógico de recursos relacionados.

---

### 8.2 Servicios de cómputo

> <span class="badge b-learn">MS LEARN</span> **Módulo 2.2 — *Describir los servicios de proceso de Azure*** (incluye VMs, Virtual Desktop, contenedores, funciones, **IA/ML/IoT-Edge** y opciones de hospedaje).
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-azure-compute-networking-services/

Los servicios de **cómputo** **ejecutan** tus aplicaciones. Van de "más control y trabajo" a "menos control y trabajo".

#### 8.2.1 Máquinas virtuales (VMs) y sus recursos asociados

**Qué son:** servidores virtuales completos (IaaS) donde controlas el SO y todo lo instalado. Te dan máxima flexibilidad.
**Cuándo usarlas:** control total del entorno; migrar servidores existentes ("lift and shift"); software que exige un SO concreto; cargas de larga duración.

**Recursos que una VM necesita** (tema que el examen toca y que conviene conocer):
- **Tamaño** (SKU): combinación de CPU y memoria (RAM) según la carga.
- **Disco** (almacenamiento): el disco del SO y discos de datos adicionales.
- **Red virtual (VNet) y tarjeta de red (NIC):** para conectarse.
- **Dirección IP** (pública y/o privada) según deba ser accesible desde internet o solo internamente.
- 💡 **Combinaciones útiles:** una **VM** + disco + red conforman un servidor; varias VMs detrás de un balanceador de carga reparten el tráfico.

**Escalado de VMs:**
- **Conjuntos de escalado de VMs (*Virtual Machine Scale Sets*):** grupo de VMs **idénticas** que aumenta o reduce su número **automáticamente** según la demanda (escalado horizontal automatizado).
- **Conjuntos de disponibilidad (*availability sets*):** distribuyen las VMs en distinto hardware mediante **dominios de error** (hardware/energía separados) y **dominios de actualización** (mantenimientos escalonados), para que no fallen ni se reinicien todas a la vez. Dan **alta disponibilidad dentro de un centro de datos**.

🔑 **Clave:** *Scale Sets* = escalar el **número** de VMs automáticamente; *availability sets* = **alta disponibilidad** repartiendo VMs en hardware distinto.

#### 8.2.2 Azure Virtual Desktop
- **Qué es:** virtualización de **escritorios y aplicaciones de Windows** en la nube, accesibles desde cualquier dispositivo.
- **Cuándo:** trabajo remoto seguro; dar a empleados un escritorio corporativo centralizado; habilitar BYOD ("trae tu propio dispositivo") sin exponer datos.
- 💡 **Ejemplo:** una consultora da a sus auditores un escritorio Windows seguro al que entran desde su laptop personal, sin que los datos salgan de Azure.

#### 8.2.3 Contenedores (Azure Container Instances y AKS)
- **Qué son:** empaquetan una aplicación con todo lo que necesita para ejecutarse, pero **comparten el sistema operativo del host** → mucho más **ligeros** que las VMs.
- **Se ejecutan/orquestan con:** **Azure Container Instances (ACI)** para contenedores sueltos y rápidos; **Azure Kubernetes Service (AKS)** para orquestar muchos contenedores a escala.
- **Cuándo:** apps portátiles; microservicios; despliegues rápidos y densos; consistencia entre entornos ("funciona igual en mi máquina y en producción").
- 🍱 **VM vs. Contenedor:** una VM lleva un **SO completo** (pesada, arranca en minutos, totalmente aislada — *mudarte con toda la casa*). Un contenedor **comparte el SO** del host y solo empaqueta la app (ligero, arranca en segundos, caben muchos — *mudarte con una maleta*).

#### 8.2.4 Azure Functions (serverless)
- **Qué es:** cómputo **serverless** que ejecuta **fragmentos de código en respuesta a eventos**; pagas solo por ejecución.
- **Cuándo:** tareas cortas disparadas por eventos (procesar una imagen al subirse, reaccionar a un mensaje en cola, responder a una solicitud web puntual); cargas intermitentes donde no quieres pagar por servidores ociosos.
- 💡 **Ejemplo:** cada vez que un cliente sube una foto, una Function la redimensiona automáticamente; si nadie sube fotos, no pagas nada.

#### 8.2.5 Opciones de hospedaje de aplicaciones
- **Azure App Service** (PaaS): hospeda apps web, APIs y back-ends móviles **sin gestionar servidor ni SO**. La vía más cómoda para publicar una web.
- **Contenedores** (ACI/AKS): apps portátiles y microservicios.
- **Máquinas virtuales** (IaaS): control total del entorno.

🔑 **Clave — elige el cómputo según la pista del escenario:** *control total del SO / migrar servidor* → **VMs**; *portátil, ligero, microservicios* → **contenedores**; *código por eventos, sin gestionar nada* → **Functions**; *publicar una web rápido sin servidor* → **App Service**.

#### 8.2.6 Categorías de IA, machine learning e IoT/Edge (tema del temario)
Azure ofrece servicios en categorías que el examen menciona a nivel **conceptual** (no necesitas dominarlos, solo reconocer para qué sirven):
- **Inteligencia artificial / Machine Learning:** servicios para crear soluciones inteligentes — visión, lenguaje, predicción. Ejemplos de categoría: **Azure AI services** (modelos listos para visión, voz, lenguaje) y **Azure Machine Learning** (plataforma para crear y entrenar tus propios modelos). 💡 *Caso:* analizar el sentimiento de los comentarios de clientes, o detectar objetos en imágenes.
- **IoT (Internet de las cosas):** conectar y gestionar **dispositivos físicos** que envían datos (sensores, máquinas). Ejemplos de categoría: **Azure IoT Hub** (comunicación bidireccional con millones de dispositivos) e **IoT Central** (solución administrada). 💡 *Caso:* sensores de temperatura en una fábrica reportando en tiempo real.
- **Edge computing:** procesar datos **cerca de donde se generan** (en el propio dispositivo o cerca), en vez de enviar todo a la nube — reduce latencia y uso de red. 💡 *Caso:* una cámara que detecta defectos en una línea de producción al instante, sin esperar a la nube.

🔑 **Clave:** para el examen basta **reconocer la categoría** por el escenario: *"crear un modelo predictivo / analizar imágenes o texto"* → IA/ML; *"conectar y gestionar sensores/dispositivos"* → IoT; *"procesar datos en el dispositivo, cerca del origen, con baja latencia"* → Edge.

---

### 8.3 Servicios de red

> <span class="badge b-learn">MS LEARN</span> **Módulo 2.3 — *Describir los servicios de red de Azure*** (redes virtuales y subredes, VPN, ExpressRoute, DNS).
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-azure-networking-services/

Las redes **conectan** tus recursos entre sí, con tu red local y con internet, de forma segura.

**Red virtual (*Azure Virtual Network / VNet*)**
- Tu **red privada** dentro de Azure: el bloque fundamental que aísla y conecta tus recursos. Tus VMs viven dentro de una VNet.
- **Capacidades:** comunicación entre recursos de Azure, con internet y con tu red local; filtrado y enrutamiento del tráfico.

**Subred (*subnet*)**
- Subdivisión de una VNet para **segmentar y organizar** los recursos (ej. una subred para servidores web, otra para bases de datos), aplicando reglas distintas a cada una.

**Puntos de conexión (*endpoints*)**
- **Público:** dirección accesible **desde internet** (para exponer un servicio al mundo).
- **Privado:** dirección accesible **solo desde tu red privada (VNet)**, sin exposición a internet — más seguro para servicios internos como una base de datos.

**Conexiones híbridas (oficina ↔ Azure):**

| Opción | Qué es | Cuándo usarla |
|---|---|---|
| **VPN Gateway** | Túnel **cifrado** entre tu red local y tu VNet **a través de internet público**. | La mayoría de casos; económico; conexión segura sobre internet. |
| **ExpressRoute** | Conexión **privada y dedicada** que **NO pasa por internet** (va por la red del proveedor). | Máxima velocidad, baja latencia constante y seguridad superior; grandes volúmenes; datos muy sensibles. Más caro. |

**Azure DNS**
- Servicio de **resolución de nombres**: traduce nombres de dominio (`miweb.com`) a direcciones IP. Permite alojar y gestionar tus dominios en Azure con alta disponibilidad.

🔑 **Clave — VPN Gateway vs. ExpressRoute (par muy preguntado):** VPN = cifrada **por internet** (barata, suficiente para la mayoría); ExpressRoute = línea **privada dedicada, fuera de internet** (rápida, segura, cara). Mnemotecnia: **"Express = exprés y privado."**
⚠️ **Trampa:** si el escenario dice *"sin pasar por internet público"* o *"latencia baja y predecible garantizada"* → **ExpressRoute**, no VPN.

---

### 8.4 Servicios de almacenamiento

> <span class="badge b-learn">MS LEARN</span> **Módulo 2.4 — *Describir los servicios de almacenamiento de Azure*** (cuentas, redundancia, tipos, niveles, migración y movimiento de archivos).
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-azure-storage-services/

#### 8.4.1 Cuenta de almacenamiento y tipos
Todo el almacenamiento de objetos vive en una **cuenta de almacenamiento** (*storage account*), que define un espacio de nombres único y la configuración (redundancia, nivel). Dentro de ella, los **tipos**:

| Tipo | Qué guarda | Ejemplo de uso |
|---|---|---|
| **Blob Storage** | Objetos **no estructurados**: imágenes, videos, documentos, copias de seguridad, datos masivos. ("Blob" = *Binary Large Object*.) | Las fotos que suben los usuarios de una app. |
| **Azure Files** | **Recursos compartidos de archivos** accesibles por red (como una carpeta compartida), montables desde la nube o local. | Una carpeta compartida corporativa accesible desde cualquier lugar. |
| **Queue Storage** | **Colas de mensajes** para comunicar componentes de forma asíncrona. | Una app deja "tareas pendientes" y otro componente las procesa cuando puede. |
| **Table Storage** | Datos **NoSQL** simples (clave-valor), sin esquema rígido. | Datos estructurados ligeros de gran volumen, sin base de datos relacional. |
| **Disk Storage** | **Discos duros virtuales** conectados a las VMs. | El "disco C:" de una máquina virtual. |

🔑 **Clave:** *imágenes/videos/backups/no estructurado* → **Blob**; *carpeta compartida en red* → **Files**.

#### 8.4.2 Niveles de acceso (*access tiers*) — para Blob
Optimizan el costo según la frecuencia de acceso:

| Nivel | Costo de almacenar | Costo/velocidad de acceso | Para qué datos |
|---|---|---|---|
| **Hot** | Más caro | Barato y rápido | Acceso frecuente (uso diario). |
| **Cool** | Más barato | Más caro | Acceso poco frecuente (mín. ~30 días). |
| **Cold** | Aún más barato | Aún más caro | Acceso raro (mín. ~90 días). |
| **Archive** | El más barato | El más caro y **lento** (recuperación tarda horas) | Datos casi nunca accedidos (respaldos legales de años). |

🏠 **Mnemotecnia de temperatura:** Hot = caliente (a la mano, caro de guardar) … Archive = congelado (barato de guardar, "descongelar" cuesta y tarda). Más frío = más barato almacenar, más caro/lento recuperar.

#### 8.4.3 Redundancia (cuántas copias y dónde)
Azure siempre guarda **múltiples copias** para proteger tus datos:

| Opción | Qué hace | Protege contra |
|---|---|---|
| **LRS** (Local) | 3 copias en **un solo** centro de datos. | Fallos de hardware en ese centro. (La más barata.) |
| **ZRS** (Zonas) | Copias entre **varias zonas de disponibilidad** de la región. | El fallo de un centro de datos / zona completa. |
| **GRS** (Geo) | Copias en la región principal **+ otra región** (la par). | El desastre de una región entera. |
| **GZRS** (Geo + Zonas) | Combina ZRS + GRS. | Lo máximo: fallos de zona **y** desastre regional. |

🔑 **Mnemotecnia por inicial:** **L**RS=**L**ocal · **Z**RS=**Z**onas · **G**RS=**G**eografía · **GZRS**=todo. Más dispersión = más protección y más costo.

#### 8.4.4 Mover y migrar datos

| Herramienta | Qué hace | Cuándo |
|---|---|---|
| **AzCopy** | Línea de comandos para copiar datos hacia/desde Blob. | Transferencias automatizables. |
| **Azure Storage Explorer** | App de escritorio con interfaz gráfica. | Gestionar archivos cómodamente con clics. |
| **Azure File Sync** | **Sincroniza** archivos entre servidores locales y Azure Files. | Centralizar archivos en la nube con copias locales rápidas. |
| **Azure Migrate** | Servicio **central** para evaluar y **migrar** servidores, BD, apps y datos a Azure. | Planear/ejecutar una migración completa. |
| **Azure Data Box** | **Dispositivo físico** que Microsoft envía por paquetería para mover **volúmenes enormes** (TB/PB). | Cuando subir por internet tardaría semanas/meses. |

💡 **Data Box explicado:** ¿500 TB que mover? Por internet tardaría meses. Microsoft te envía un dispositivo robusto, lo llenas localmente (rápido) y lo devuelves; ellos cargan los datos directamente. Es "el camión de mudanzas" de los datos.

🔑 **Clave — no confundas:** *mover archivos* (AzCopy, Storage Explorer, File Sync) vs. *migrar a Azure* (Azure Migrate para servidores/apps; Data Box para volúmenes enormes por transporte físico).

---

### 8.5 Identidad, acceso y seguridad

> <span class="badge b-learn">MS LEARN</span> **Módulo 2.5 — *Describir la identidad, el acceso y la seguridad de Azure*** (11 unidades: directorios, autenticación, identidades externas, acceso condicional, RBAC, Zero Trust, defensa en profundidad, Defender for Cloud).
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-azure-identity-access-security/

#### 8.5.1 Autenticación vs. autorización (base de todo)

| Concepto | Qué responde | Ejemplo |
|---|---|---|
| **Autenticación** (*AuthN*) | **¿Quién eres?** Demostrar identidad. | Iniciar sesión con contraseña, o con huella. |
| **Autorización** (*AuthZ*) | **¿Qué puedes hacer?** Permisos una vez identificado. | Un usuario puede leer documentos pero no borrarlos. |

🔑 **Clave:** primero te **autenticas** (quién eres), luego te **autorizan** (qué puedes hacer). La *huella/contraseña* es autenticación; los *permisos* son autorización.

#### 8.5.2 Servicios de directorio e identidad
- **Microsoft Entra ID** (antes Azure Active Directory): el servicio de **identidad y directorio** en la nube de Microsoft. Gestiona usuarios, grupos y controla el acceso a apps y recursos. Es el corazón de la identidad en Azure.
- **Microsoft Entra Domain Services:** ofrece servicios de **dominio administrados** (unión a dominio, directivas de grupo, autenticación tipo Windows) **sin** que tú despliegues ni mantengas controladores de dominio.

#### 8.5.3 Métodos de autenticación
- **Inicio de sesión único (SSO):** un **solo** inicio de sesión da acceso a múltiples apps. Menos contraseñas, menos riesgo, mejor experiencia.
- **Autenticación multifactor (MFA):** exige **dos o más pruebas** de categorías distintas — algo que **sabes** (contraseña), algo que **tienes** (tu celular/un código), algo que **eres** (huella, rostro). Aunque roben tu contraseña, sin el segundo factor no entran.
- **Sin contraseña (*passwordless*):** acceder **sin contraseña**, con huella, rostro o una llave de seguridad física. Más seguro y cómodo que las contraseñas.

#### 8.5.4 Identidades externas y acceso condicional
- **Identidades externas:** permiten que personas **ajenas a tu organización** accedan a recursos: **B2B** (colaboración con socios/proveedores que usan **sus propias** identidades) y **B2C** (clientes que se registran en tu aplicación de cara al consumidor).
- **Acceso condicional (*Conditional Access*):** aplica reglas de acceso **según el contexto** (ubicación, dispositivo, nivel de riesgo). 💡 *Ejemplo:* "si alguien inicia sesión desde un país inusual o un dispositivo desconocido, exígele MFA o bloquéalo."

#### 8.5.5 Control de acceso y modelos de seguridad
- **RBAC (Control de acceso basado en roles):** asigna permisos según el **rol** de cada persona, con el **principio de mínimo privilegio** (cada quien solo lo que necesita). 💡 *Ejemplo:* el rol "Lector" puede ver recursos pero no modificarlos; "Colaborador" puede gestionarlos pero no dar permisos a otros.
- **Confianza cero (*Zero Trust*):** modelo cuyo lema es **"nunca confíes, siempre verifica"**. No se asume que algo es seguro por estar "dentro" de la red: **cada** solicitud se verifica explícitamente (identidad, dispositivo, contexto), sin importar su origen.
- **Defensa en profundidad (*defense in depth*):** **múltiples capas** de seguridad, de modo que si una falla, las otras protegen. Capas típicas: física → identidad y acceso → perímetro → red → cómputo → aplicación → datos. 🧅 *Analogía:* un castillo con foso, murallas, puertas y guardias; superar una capa no basta.
- **Microsoft Defender for Cloud:** herramienta que **monitorea continuamente** la seguridad de tus recursos (en Azure, on-premises y otras nubes), evalúa tu postura, detecta amenazas y da **recomendaciones** para mejorar.

🔑 **Clave — RBAC vs. Policy (no los confundas; Policy se ve en el Dominio 3):** **RBAC = permisos de personas** (quién puede hacer qué); **Azure Policy = reglas sobre recursos** (qué está permitido crear/configurar). *"Roles a las personas, Policy a los recursos."*

---

### 🧪 Escenarios resueltos — Dominio 2

**Escenario 2A.** *Una app debe seguir disponible si un centro de datos falla, pero los datos deben permanecer dentro de la misma región por normativa. ¿Qué usas?*
**Razonamiento:** seguir disponible ante fallo de un centro de datos **dentro** de la región → **zonas de disponibilidad** (no pares de regiones, que sacarían los datos a otra región). **Respuesta:** zonas de disponibilidad.

**Escenario 2B.** *Necesitas conectar tu centro de datos local con Azure para una carga crítica que exige latencia baja y constante, sin exponer el tráfico a internet. ¿Qué eliges?*
**Razonamiento:** "sin internet" + "latencia baja constante" → **ExpressRoute** (línea privada dedicada). **Respuesta:** ExpressRoute.

**Escenario 2C.** *Tu empresa guardará 1 PB de grabaciones históricas que casi nunca se consultarán, y necesita el menor costo de almacenamiento posible. ¿Qué nivel de Blob usas, y cómo subes el petabyte?*
**Razonamiento:** "casi nunca se consultan" + "menor costo de almacenamiento" → nivel **Archive**. Subir 1 PB por internet es inviable → **Azure Data Box**. **Respuesta:** nivel Archive + Azure Data Box.

**Escenario 2D.** *Quieres permitir que empleados de una empresa asociada accedan a un recurso compartido usando sus propias cuentas corporativas, sin crearles usuarios internos. ¿Qué función lo permite?*
**Razonamiento:** colaboración con otra organización usando sus identidades → **identidades externas B2B**. **Respuesta:** identidades externas (B2B).

### ✅ Resumen del Dominio 2
- **Físico:** Centro de datos → Zona de disponibilidad → Región → Pares de regiones. Zonas = alta disponibilidad; pares = recuperación ante desastres.
- **Lógico:** Grupo de administración → Suscripción (facturación) → Grupo de recursos (contenedor lógico) → Recurso.
- **Cómputo:** VMs (control total) · Scale Sets (escalado auto) · availability sets (alta disponibilidad) · contenedores (ligeros) · Functions (serverless) · App Service (web sin servidor) · categorías IA/ML, IoT, Edge.
- **Redes:** VNet/subredes; endpoints público/privado; VPN Gateway (por internet) vs. ExpressRoute (privada dedicada); Azure DNS.
- **Almacenamiento:** tipos (Blob/Files/Queue/Table/Disk); niveles (Hot/Cool/Cold/Archive); redundancia (LRS/ZRS/GRS/GZRS); mover (AzCopy/Explorer/File Sync) y migrar (Migrate/Data Box).
- **Identidad:** AuthN vs. AuthZ; Entra ID y Domain Services; SSO/MFA/passwordless; identidades externas; acceso condicional; RBAC; Zero Trust; defensa en profundidad; Defender for Cloud.

*(Banco de preguntas del Dominio 2: sección 14.2.)*

---
---
## 9. Dominio 3 — Administración y gobernanza de Azure (30–35%)

> <span class="badge b-learn">MS LEARN</span> **RUTA 3 completa** — *"Describe Azure management and governance"* (4 módulos).
> 🔗 https://learn.microsoft.com/es-es/training/paths/describe-azure-management-governance/

> **🎓 Objetivos de aprendizaje oficiales de este dominio:**
> - Describir los factores de costo y las herramientas para administrarlo (calculadora de precios, calculadora de TCO, Microsoft Cost Management, etiquetas).
> - Describir el propósito de Microsoft Purview, Azure Policy, los bloqueos de recursos y el **Service Trust Portal**.
> - Describir Azure Portal, Azure Cloud Shell (CLI y PowerShell), Azure Arc, y Azure Resource Manager con plantillas ARM.
> - Describir Azure Advisor, Azure Service Health y Azure Monitor (con Log Analytics, alertas y Application Insights).

**El dominio más subestimado.** Cubre las herramientas con las que **controlas costos, aplicas reglas, despliegas y supervisas**. Muchas **no tienen equivalente en la TI tradicional**, por lo que resultan menos intuitivas y ahí se pierden puntos. **Dale tanta dedicación como al Dominio 2.**

---

### 9.1 Administración de costos

> <span class="badge b-learn">MS LEARN</span> **Módulo 3.1 — *Describir la administración de costos en Azure***.
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-cost-management-azure/

#### 9.1.1 Factores que afectan el costo

| Factor | Cómo influye |
|---|---|
| **Tipo de recurso** | Un recurso más potente (VM grande) cuesta más que uno pequeño. |
| **Consumo** | Horas de uso, datos procesados/almacenados. Apagar lo ocioso ahorra. |
| **Mantenimiento** | Recursos encendidos pero sin usar **siguen costando**. |
| **Ubicación geográfica** | Los precios **varían entre regiones**. |
| **Tráfico de red** | La **salida de datos** (egress) suele costar; la **entrada** (ingress) normalmente es gratis. |
| **Tipo de suscripción** | Gratuita, pago por uso, Enterprise… con precios/descuentos distintos. |

#### 9.1.2 Herramientas de costos

| Herramienta | Qué hace | ¿Antes o después de gastar? |
|---|---|---|
| **Calculadora de precios** (*Pricing Calculator*) | **Estima** el costo de recursos **antes** de crearlos, combinando servicios. | **ANTES** (planeación). |
| **Calculadora de TCO** (*Total Cost of Ownership*) | **Compara** el costo de operar **on-premises** vs. en **Azure**. | **ANTES** (decisión de migrar). |
| **Microsoft Cost Management** | **Supervisa, analiza y controla** el gasto **real**; crea **presupuestos**, informes y **alertas**. | **DESPUÉS** (operación). |
| **Etiquetas** (*tags*) | Pares **clave-valor** (`Departamento: Ventas`) para organizar recursos y **agrupar/filtrar costos**. | Transversal. |

🔑 **Clave — Pricing Calculator vs. Cost Management:** *calculadora = estima ANTES* (planeación); *Cost Management = controla el gasto REAL DESPUÉS* (operación). Mnemotecnia: **"Calculas antes, Controlas después."**
💡 **Etiquetas:** etiqueta todo recurso de un proyecto con `Proyecto: Alpha` y luego filtra en Cost Management para saber **exactamente** cuánto cuesta ese proyecto. También sirven para aplicar políticas y organizar.

---

### 9.2 Gobernanza y cumplimiento

> <span class="badge b-learn">MS LEARN</span> **Módulo 3.2 — *Características y herramientas para la gobernanza y el cumplimiento*** (Purview, Azure Policy, bloqueos, **Service Trust Portal**).
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-features-tools-azure-for-governance-compliance/

**Gobernanza** = mantener orden, aplicar reglas y cumplir normativas conforme creces.

**Microsoft Purview**
- Solución de **gobierno de datos**: descubre, clasifica, cataloga y protege datos en toda la organización (Azure, on-premises, otras nubes, SaaS), apoyando el cumplimiento.
- 💡 *Ejemplo:* identificar automáticamente dónde hay datos personales sensibles y clasificarlos para protegerlos.

**Azure Policy**
- Aplica **reglas y estándares automáticos** a los recursos. Evalúa el cumplimiento, marca lo "no conforme" y puede **impedir** acciones que violen las reglas.
- 💡 *Ejemplos:* "prohibir crear recursos fuera de la región permitida"; "exigir que todo recurso tenga etiqueta de departamento"; "permitir solo ciertos tamaños de VM".

**Bloqueos de recursos (*resource locks*)**
- **Impiden la eliminación o modificación accidental** de recursos críticos. Dos tipos:
  - **CanNotDelete:** se puede **leer y modificar**, pero **NO eliminar**.
  - **ReadOnly:** **solo lectura** — ni modificar ni eliminar (más restrictivo).
- Se aplican incluso por encima de los permisos RBAC: aunque tengas permiso para borrar, el bloqueo lo impide hasta que se quite.
- 💡 *Ejemplo:* bloqueo CanNotDelete sobre la base de datos de producción para que nadie la borre por error.

**Service Trust Portal** *(tema que conviene reconocer)*
- Portal público de Microsoft que publica **informes de auditoría, certificaciones de cumplimiento y documentación de seguridad** (ISO, SOC, etc.). Sirve para **demostrar y revisar el cumplimiento** normativo de los servicios de Microsoft.
- 💡 *Ejemplo:* tu equipo legal descarga del Service Trust Portal el informe de cumplimiento ISO 27001 de Azure para una auditoría.

🔑 **Clave — Azure Policy vs. RBAC:** **RBAC = QUIÉN puede hacer algo** (personas); **Azure Policy = QUÉ se puede hacer con los recursos** (reglas). Son complementarios. *"Policy a los recursos, Roles a las personas."*
🔑 **Clave — bloqueos:** *CanNotDelete* = no borrar (sí editar); *ReadOnly* = ni editar ni borrar.

---

### 9.3 Herramientas para administrar y desplegar recursos

> <span class="badge b-learn">MS LEARN</span> **Módulo 3.3 — *Herramientas para administrar e implementar recursos*** (Portal, Cloud Shell, Arc, ARM/plantillas).
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-features-tools-manage-deploy-azure-resources/

| Herramienta | Qué es | Cuándo usarla |
|---|---|---|
| **Azure Portal** | **Interfaz web gráfica** (apuntar y hacer clic) para gestionar todo Azure. | Aprender, explorar, tareas puntuales. Ideal para principiantes. |
| **Azure Cloud Shell** | **Terminal en el navegador**, ya autenticada, sin instalar nada. Ofrece dos lenguajes ↓ | Comandos rápidos desde cualquier navegador. |
| → **Azure CLI** | Línea de comandos `az ...` (multiplataforma). | Automatizar/scriptear; estilo Linux. |
| → **Azure PowerShell** | Línea de comandos con cmdlets `Verb-AzNoun`. | Automatizar; estilo Windows. |
| **Azure Arc** | **Extiende la gestión de Azure a recursos FUERA de Azure** (on-premises, otras nubes, Kubernetes). | Gobernar un entorno híbrido/multinube desde un solo panel. |
| **Azure Resource Manager (ARM)** | El **motor** de despliegue subyacente: toda petición (portal, CLI…) pasa por ARM. | Es la capa que orquesta todo por debajo. |
| **Plantillas ARM / Bicep** | Archivos (**JSON**, o Bicep más legible) que **describen** la infraestructura y la despliegan de forma **repetible y automática**. Esto **es IaC**. | Desplegar entornos completos idénticos sin errores manuales. |

**Infraestructura como Código (IaC):** definir la infraestructura mediante **archivos** en lugar de clics. Ventajas: **repetible** (mismo archivo → mismo entorno), **versionable** (historial de cambios) y **automatizable** (sin errores humanos).

🔑 **Clave:** *Portal* = visual/aprender; *CLI/PowerShell* = automatizar tareas; *plantillas ARM/IaC* = desplegar entornos completos repetibles; *Azure Arc* = gestionar lo que está **fuera** de Azure.
⚠️ **Trampa:** "gestionar servidores **fuera** de Azure desde Azure" → **Azure Arc** (no Migrate, que es para *mover* a Azure).

---

### 9.4 Herramientas de supervisión (monitoreo)

> <span class="badge b-learn">MS LEARN</span> **Módulo 3.4 — *Describir las herramientas de supervisión de Azure*** (Advisor, Service Health, Azure Monitor).
> 🔗 https://learn.microsoft.com/es-es/training/modules/describe-monitoring-tools-azure/

| Herramienta | Qué hace | Pregunta que responde |
|---|---|---|
| **Azure Advisor** | **Recomendaciones personalizadas** en 5 categorías: confiabilidad, seguridad, excelencia operativa, rendimiento y costo. | "¿Qué debería mejorar en mis recursos?" |
| **Azure Service Health** | Estado de los **servicios de Azure mismo**: incidencias, interrupciones, mantenimientos planificados y avisos que te afectan. | "¿Hay un problema del lado de Azure que me afecta?" |
| **Azure Monitor** | **Plataforma central** que recopila y analiza **telemetría** de **tus** recursos y apps. | "¿Cómo se comportan mis recursos ahora mismo?" |

**Componentes de Azure Monitor:**
- **Log Analytics:** consultar y analizar los **registros (logs)** recopilados.
- **Azure Monitor Alerts:** **notifican** cuando se cumple una condición (CPU > 90%, sitio caído).
- **Application Insights:** **rendimiento de aplicaciones** (tiempos de respuesta, errores, uso, cuellos de botella).

🔑 **Clave — distingue las tres (van juntas como trampa):** **Advisor** te *aconseja a TI*; **Service Health** te *avisa del estado de AZURE*; **Azure Monitor** *mide TUS recursos*. Mnemotecnia: **"Advisor aconseja · Service Health = estado de Azure · Monitor mide lo tuyo."**
⚠️ **Trampa:** "¿qué usas para saber si **Azure** tiene una interrupción que te afecta?" → **Service Health** (no Monitor, que es para *tus* recursos; no Advisor, que recomienda).

---

### 🧪 Escenarios resueltos — Dominio 3

**Escenario 3A.** *Antes de migrar, la dirección quiere comparar cuánto cuesta mantener sus servidores actuales frente a operarlos en Azure. ¿Qué herramienta usas?*
**Razonamiento:** comparar **on-premises vs. Azure** → **Calculadora de TCO** (no la de precios, que solo estima recursos de Azure). **Respuesta:** TCO Calculator.

**Escenario 3B.** *Necesitas garantizar que ningún equipo cree recursos fuera de la región de México y que todo recurso lleve etiqueta de centro de costos. ¿Qué usas?*
**Razonamiento:** imponer **reglas sobre los recursos** → **Azure Policy** (RBAC controlaría quién, no impone estas reglas). **Respuesta:** Azure Policy.

**Escenario 3C.** *Un auditor externo pide los certificados de cumplimiento ISO y SOC de Azure. ¿Dónde los obtienes?*
**Razonamiento:** informes de auditoría y certificaciones de cumplimiento de Microsoft → **Service Trust Portal**. **Respuesta:** Service Trust Portal.

**Escenario 3D.** *Quieres que te avisen automáticamente cuando una VM supere el 85% de CPU, y revisar después los registros para investigar. ¿Qué usas?*
**Razonamiento:** telemetría de *tus* recursos, alertas y logs → **Azure Monitor** (alertas + Log Analytics). **Respuesta:** Azure Monitor.

### ✅ Resumen del Dominio 3
- **Costos:** Pricing Calculator y TCO **estiman antes**; Cost Management **controla el gasto real después**; **etiquetas** organizan/agrupan costos.
- **Gobernanza:** **Azure Policy** (reglas sobre recursos), **bloqueos** (CanNotDelete/ReadOnly), **Purview** (gobierno de datos), **Service Trust Portal** (cumplimiento/auditorías). *Policy = recursos, RBAC = personas.*
- **Administrar/desplegar:** **Portal** (visual), **CLI/PowerShell** (automatizar), **plantillas ARM/IaC** (despliegue repetible), **Azure Arc** (fuera de Azure), **ARM** (motor).
- **Supervisión:** **Advisor** (recomienda), **Service Health** (estado de Azure), **Azure Monitor** (telemetría: Log Analytics, alertas, Application Insights).

*(Banco de preguntas del Dominio 3: sección 14.3.)*

---
---
# PARTE IV — REFUERZO Y MEMORIZACIÓN

## 10. Pares de conceptos que más se confunden

Esta es una de las secciones **más rentables** del manual. La gran mayoría de las preguntas-trampa del examen consisten en ofrecerte dos conceptos parecidos y ver si distingues cuál aplica. Repasa esta tabla varias veces, especialmente el día antes del examen. Estúdiala tapando una columna e intentando recordar la diferencia.

| Concepto A | Concepto B | La diferencia en una frase |
|---|---|---|
| **CapEx** | **OpEx** | Inversión inicial grande (comprar) **vs.** gasto recurrente por uso (alquilar). |
| **Confiabilidad** | **Predictibilidad** | Recuperarse de fallas **vs.** consistencia de rendimiento/costo. |
| **Alta disponibilidad** | **Recuperación ante desastres** | Mínima inactividad ante fallos pequeños **vs.** restaurar tras la caída de una región entera. |
| **Zonas de disponibilidad** | **Pares de regiones** | Alta disponibilidad **dentro** de una región **vs.** respaldo **entre** regiones. |
| **Escalado vertical** | **Escalado horizontal** | Una máquina más potente (up/down) **vs.** más máquinas en paralelo (out/in). |
| **Escalabilidad** | **Elasticidad** | Capacidad de crecer/reducir **vs.** que ese ajuste ocurra **automáticamente** según la demanda. |
| **IaaS** | **PaaS** | Tú gestionas el sistema operativo **vs.** Microsoft gestiona el SO (tú solo tu app). |
| **PaaS** | **SaaS** | Tú gestionas tu aplicación **vs.** solo usas un software ya hecho. |
| **VM** | **Contenedor** | Incluye SO completo (pesado, lento de arrancar) **vs.** comparte el SO del host (ligero, arranca en segundos). |
| **Contenedor** | **Azure Functions** | App portátil que corre continuamente **vs.** código que se ejecuta por eventos (serverless). |
| **Autenticación** | **Autorización** | Demostrar **quién eres** (login) **vs.** qué **tienes permitido** hacer (permisos). |
| **VPN Gateway** | **ExpressRoute** | Túnel cifrado **por internet** **vs.** línea privada dedicada **fuera** de internet. |
| **Punto de conexión público** | **Punto de conexión privado** | Accesible desde internet **vs.** accesible solo desde tu red interna. |
| **VNet** | **Subred** | La red privada completa **vs.** una subdivisión dentro de ella. |
| **Blob** | **Files** | Objetos no estructurados (imágenes, videos, backups) **vs.** carpeta compartida en red. |
| **Hot** | **Archive** | Datos de acceso frecuente (caro guardar, barato/rápido acceder) **vs.** datos casi nunca usados (barato guardar, caro/lento recuperar). |
| **LRS** | **GRS** | Copias en un solo centro de datos **vs.** copias también en otra región (geo). |
| **RBAC** | **Azure Policy** | Permisos de **personas** (quién) **vs.** reglas sobre **recursos** (qué). |
| **Calculadora de precios** | **Cost Management** | Estima costos **antes** de crear **vs.** controla el gasto **real después**. |
| **TCO Calculator** | **Pricing Calculator** | Compara on-premises **vs.** Azure **vs.** estima el costo de recursos de Azure. |
| **Bloqueo CanNotDelete** | **Bloqueo ReadOnly** | No se puede borrar (pero sí editar) **vs.** ni editar ni borrar (solo lectura). |
| **Azure Advisor** | **Azure Service Health** | Recomendaciones para mejorar tus recursos **vs.** estado/caídas de los servicios de Azure. |
| **Azure Monitor** | **Azure Service Health** | Telemetría de **tus** recursos **vs.** salud de los **servicios de Azure** mismos. |
| **Microsoft Entra ID** | **Microsoft Defender for Cloud** | Identidad y gestión de accesos **vs.** monitoreo y recomendaciones de seguridad. |
| **Azure Policy** | **Microsoft Purview** | Reglas/estándares sobre recursos **vs.** gobierno y clasificación de datos. |
| **Grupo de recursos** | **Grupo de administración** | Contenedor de recursos relacionados **vs.** contenedor de varias suscripciones. |
| **Suscripción** | **Grupo de recursos** | Unidad de facturación y acceso **vs.** contenedor lógico de recursos. |
| **Azure CLI** | **Azure PowerShell** | Línea de comandos `az ...` (estilo Linux) **vs.** cmdlets `Verb-AzNoun` (estilo Windows). Ambas hacen lo mismo. |
| **Azure Arc** | **Azure Migrate** | Gestionar recursos que **siguen** fuera de Azure **vs.** mover recursos **hacia** Azure. |

---

## 11. Mnemotecnias y trucos de memoria

Reglas cortas para fijar lo que más se olvida:

- **Responsabilidad compartida → "Tus 3 cosas":** **D**atos, **D**ispositivos e **I**dentidades son **siempre tuyas**. Lo **físico** siempre de Microsoft.
- **IaaS → PaaS → SaaS → escalera de esfuerzo:** *I* = "**I** do more" (yo hago más); *S* = "**S**omebody else does it" (otro lo hace). Mientras más a la derecha, menos trabajo tuyo.
- **Niveles de almacenamiento = temperatura = frecuencia de uso:** **Hot** (caliente, lo usas seguido) → **Cool** → **Cold** → **Archive** (congelado, casi nunca). Más frío = más barato guardar, más caro/lento recuperar.
- **Redundancia por su inicial:** **L**RS = **L**ocal · **Z**RS = **Z**onas · **G**RS = **G**eografía (otra región) · **GZRS** = todo junto. Más letras/dispersión = más protección = más costo.
- **VPN vs. ExpressRoute → "Express es exprés y privado":** la vía rápida que evita el tráfico de internet.
- **Policy vs. RBAC → "Policy a los recursos, Roles a las personas."**
- **Las tres de monitoreo → "Advisor Aconseja · service Health = estado de azure · Monitor Mide lo tuyo."**
- **Pricing Calculator vs. Cost Management → "Calculas antes, Controlas después."**
- **Zonas vs. Pares → "Zonas = mismo barrio (alta disponibilidad); Pares = otra ciudad (desastre)."**
- **Autenticación vs. Autorización → "autenticación = identidad (¿quién?); autorización = permiso (¿qué puede?)."**
- **Jerarquía (de grande a chico) → "Mamá Sube Recados Rápido":** **M**anagement group → **S**ubscription → **R**esource group → **R**esource.

---

## 12. Hojas de referencia rápida

Tablas condensadas para el repaso final. Imprímelas y tenlas a la vista los últimos días.

### 12.1 Cheat sheet — Servicios de cómputo

| Necesidad | Servicio |
|---|---|
| Control total del SO / migrar servidor | **Máquinas virtuales** |
| Escalar VMs automáticamente | **VM Scale Sets** |
| App web sin gestionar servidor | **Azure App Service** |
| App portátil, microservicios, ligera | **Contenedores (ACI / AKS)** |
| Ejecutar código por eventos, serverless | **Azure Functions** |
| Escritorios Windows en la nube | **Azure Virtual Desktop** |

### 12.2 Cheat sheet — Redes

| Necesidad | Servicio |
|---|---|
| Red privada base en Azure | **Virtual Network (VNet)** |
| Conectar oficina a Azure por internet (cifrado) | **VPN Gateway** |
| Conexión privada dedicada, sin internet | **ExpressRoute** |
| Conectar dos VNets | **Peering** |
| Resolver nombres de dominio | **Azure DNS** |
| Acceso solo desde red interna | **Punto de conexión privado** |

### 12.3 Cheat sheet — Almacenamiento

| Necesidad | Respuesta |
|---|---|
| Imágenes, videos, backups (no estructurado) | **Blob Storage** |
| Carpeta compartida en red | **Azure Files** |
| Datos casi nunca usados, lo más barato de guardar | Nivel **Archive** |
| Datos de uso diario | Nivel **Hot** |
| Copias solo en un centro de datos | **LRS** |
| Copias en otra región (desastre regional) | **GRS** |
| Mover terabytes sin saturar internet | **Azure Data Box** |
| Migrar servidores/apps a Azure | **Azure Migrate** |

### 12.4 Cheat sheet — Identidad y seguridad

| Necesidad | Respuesta |
|---|---|
| Servicio de identidad/directorio en la nube | **Microsoft Entra ID** |
| Exigir un segundo factor al iniciar sesión | **MFA** |
| Un login para muchas apps | **SSO** |
| Permisos según el rol de cada persona | **RBAC** |
| Regla "verificar siempre, no confiar por defecto" | **Zero Trust** |
| Múltiples capas de protección | **Defensa en profundidad** |
| Recomendaciones y monitoreo de seguridad | **Defender for Cloud** |
| Reglas de acceso según contexto (ubicación, riesgo) | **Acceso condicional** |

### 12.5 Cheat sheet — Administración y gobernanza

| Necesidad | Respuesta |
|---|---|
| Estimar costos antes de crear | **Pricing Calculator** |
| Comparar on-premises vs. Azure | **TCO Calculator** |
| Controlar/analizar gasto real, poner presupuestos | **Cost Management** |
| Agrupar costos por proyecto/equipo | **Etiquetas (tags)** |
| Imponer reglas sobre los recursos | **Azure Policy** |
| Evitar borrado accidental (sí editar) | Bloqueo **CanNotDelete** |
| Solo lectura (ni editar ni borrar) | Bloqueo **ReadOnly** |
| Gobierno y clasificación de datos | **Microsoft Purview** |
| Gestionar recursos fuera de Azure | **Azure Arc** |
| Desplegar entornos repetibles (IaC) | **Plantillas ARM / Bicep** |
| Interfaz gráfica para gestionar Azure | **Azure Portal** |
| Recomendaciones de mejora | **Azure Advisor** |
| Saber si Azure tiene una caída | **Azure Service Health** |
| Monitorear telemetría de tus recursos | **Azure Monitor** |

---

## 13. Glosario maestro

| Término | Definición |
|---|---|
| **Alta disponibilidad** | Mínimo tiempo de inactividad ante fallos. |
| **Application Insights** | Componente de Azure Monitor para supervisar el rendimiento de aplicaciones. |
| **ARM (Azure Resource Manager)** | Motor de despliegue y gestión de recursos de Azure. |
| **Azure Advisor** | Da recomendaciones personalizadas (confiabilidad, seguridad, costo, rendimiento, operación). |
| **Azure Arc** | Extiende la gestión de Azure a recursos fuera de Azure. |
| **Azure Functions** | Cómputo serverless basado en eventos. |
| **Azure Monitor** | Plataforma central de supervisión y telemetría de tus recursos. |
| **Azure Policy** | Aplica reglas y estándares a los recursos; evalúa cumplimiento. |
| **Azure Portal** | Interfaz web gráfica para gestionar Azure. |
| **Bicep** | Lenguaje de IaC más legible que JSON, para desplegar recursos. |
| **Blob Storage** | Almacenamiento de objetos no estructurados (imágenes, videos, backups). |
| **Bloqueo de recursos** | Protección contra eliminación/modificación accidental (CanNotDelete / ReadOnly). |
| **CapEx** | Gasto de capital: inversión inicial grande (modelo on-premises). |
| **Cloud Shell** | Terminal en el navegador, lista para usar (CLI o PowerShell). |
| **Confianza cero (Zero Trust)** | "Nunca confíes, siempre verifica". |
| **Confiabilidad** | Capacidad de recuperarse de fallas. |
| **Contenedor** | Empaqueta una app compartiendo el SO del host; ligero y portátil. |
| **Cost Management** | Supervisa y controla el gasto real; presupuestos y alertas. |
| **Defender for Cloud** | Monitoreo y recomendaciones de seguridad. |
| **Defensa en profundidad** | Múltiples capas de seguridad. |
| **Egress / Ingress** | Salida / entrada de datos (la salida suele costar). |
| **Elasticidad** | Ajuste automático de recursos según la demanda. |
| **ExpressRoute** | Conexión privada dedicada a Azure, sin pasar por internet. |
| **Grupo de administración** | Contenedor de varias suscripciones. |
| **Grupo de recursos** | Contenedor lógico de recursos relacionados. |
| **IaaS** | Infraestructura como servicio (tú gestionas el SO). |
| **IaC (Infraestructura como Código)** | Definir infraestructura mediante archivos (plantillas ARM/Bicep). |
| **LRS / ZRS / GRS / GZRS** | Redundancia: local / zonas / geográfica / zonas+geo. |
| **Log Analytics** | Componente de Azure Monitor para consultar registros. |
| **Manejabilidad** | Facilidad de gestionar recursos (de y en la nube). |
| **MFA** | Autenticación multifactor (dos o más pruebas de identidad). |
| **Microsoft Entra ID** | Servicio de identidad y directorio en la nube (antes Azure AD). |
| **Microsoft Purview** | Gobierno, clasificación y protección de datos. |
| **Nube híbrida / pública / privada** | Combinación / compartida por el proveedor / exclusiva de una organización. |
| **OpEx** | Gasto operativo: pago recurrente por uso (modelo de la nube). |
| **Par de regiones** | Dos regiones emparejadas para recuperación ante desastres. |
| **PaaS** | Plataforma como servicio (Microsoft gestiona el SO; tú tu app). |
| **Predictibilidad** | Consistencia de rendimiento y costo. |
| **Punto de conexión público/privado** | Accesible desde internet / solo desde la red interna. |
| **RBAC** | Control de acceso basado en roles (permisos de personas). |
| **Recuperación ante desastres** | Restaurar el servicio tras una falla grave (ej. región caída). |
| **Región** | Conjunto de centros de datos en un área geográfica. |
| **SaaS** | Software como servicio (solo usas la app; gestionas tus datos). |
| **Serverless** | Modelo sin gestión de servidores; pago por ejecución. |
| **Service Health** | Informa del estado/caídas de los servicios de Azure. |
| **SSO** | Inicio de sesión único. |
| **Suscripción** | Unidad de facturación y acceso. |
| **Tags (etiquetas)** | Pares clave-valor para organizar recursos y agrupar costos. |
| **TCO Calculator** | Compara costos de on-premises vs. Azure. |
| **VM (máquina virtual)** | Servidor virtual con SO completo (IaaS). |
| **VNet / Subred** | Red privada en Azure / su subdivisión. |
| **VPN Gateway** | Túnel cifrado a Azure a través de internet. |
| **Zona de disponibilidad** | Centros de datos aislados dentro de una región (alta disponibilidad). |
| **Availability set (conjunto de disponibilidad)** | Reparte VMs en hardware distinto (dominios de error/actualización) para alta disponibilidad. |
| **VM Scale Set (conjunto de escalado)** | Grupo de VMs idénticas que escala su número automáticamente. |
| **Azure Virtual Desktop** | Escritorios y apps de Windows virtualizados en la nube. |
| **ACI / AKS** | Azure Container Instances (contenedores sueltos) / Azure Kubernetes Service (orquestación a escala). |
| **IA / Machine Learning** | Categoría de servicios para soluciones inteligentes (visión, lenguaje, predicción); ej. Azure AI services, Azure Machine Learning. |
| **IoT** | Internet de las cosas: conectar y gestionar dispositivos/sensores; ej. Azure IoT Hub. |
| **Edge computing** | Procesar datos cerca de su origen (en el dispositivo) para baja latencia. |
| **Service Trust Portal** | Portal con informes de auditoría y certificaciones de cumplimiento de Microsoft. |
| **Storage account (cuenta de almacenamiento)** | Contenedor de nivel superior para los datos de Azure Storage. |
| **SLA (Acuerdo de Nivel de Servicio)** | Compromiso del proveedor sobre disponibilidad/rendimiento (ej. 99,9%). |

---
---
# PARTE V — PRÁCTICA Y EXAMEN

## 14. Banco de preguntas por dominio

Preguntas originales en el estilo del examen, con respuestas explicadas. **Resuelve cada una antes de mirar la solución.** Si fallas, vuelve a la sección correspondiente del manual. Meta: >80% en cada dominio.

### 14.1 Preguntas — Dominio 1 (Conceptos de la nube)

**P1.** Una empresa deja de comprar servidores y pasa a pagar mensualmente solo por lo que usa. ¿Qué cambio de modelo de gasto representa?
- A) De OpEx a CapEx · B) De CapEx a OpEx · C) Ambos suben · D) Ninguno cambia

<details><summary>Respuesta</summary>**B.** Pasar de comprar hardware por adelantado (CapEx) a pagar por consumo (OpEx) es la esencia de la nube.</details>

**P2.** En el modelo de responsabilidad compartida, ¿qué es responsabilidad del cliente **sin importar** el modelo de servicio?
- A) Red física · B) Hosts físicos · C) Datos e identidades · D) Centro de datos

<details><summary>Respuesta</summary>**C.** Datos, dispositivos e identidades son **siempre** del cliente. Lo físico (A, B, D) es siempre de Microsoft.</details>

**P3.** Una tienda online debe absorber un pico de visitantes durante una oferta, agregando capacidad automáticamente. ¿Qué beneficio describe esto?
- A) Confiabilidad · B) Predictibilidad · C) Escalabilidad · D) Gobernanza

<details><summary>Respuesta</summary>**C. Escalabilidad** = agregar/quitar recursos según la demanda.</details>

**P4.** ¿Qué modelo de servicio da **mayor control** sobre el sistema operativo?
- A) SaaS · B) PaaS · C) IaaS · D) Serverless

<details><summary>Respuesta</summary>**C. IaaS.** Tú administras el SO completo.</details>

**P5.** (Selecciona todas) ¿Cuáles son modelos de **implementación** de la nube?
- A) Pública · B) Híbrida · C) Privada · D) Serverless

<details><summary>Respuesta</summary>**A, B y C.** *Serverless* es un modelo de ejecución/precios, no de implementación. Trampa típica.</details>

**P6.** Un sistema debe **recuperarse y seguir operando** aunque falle una región completa. ¿Qué beneficio describe esto?
- A) Escalabilidad · B) Confiabilidad · C) Predictibilidad · D) Elasticidad

<details><summary>Respuesta</summary>**B. Confiabilidad** = capacidad de recuperarse de fallas (incluye recuperación ante desastres).</details>

**P7.** Microsoft 365 (Outlook, Word en línea) es un ejemplo de:
- A) IaaS · B) PaaS · C) SaaS · D) On-premises

<details><summary>Respuesta</summary>**C. SaaS.** Software listo para usar; solo gestionas tus datos y usuarios.</details>

**P8.** Necesitas más potencia (CPU/RAM) en una sola máquina. ¿Qué tipo de escalado es?
- A) Horizontal (scale out) · B) Vertical (scale up) · C) Geográfico · D) Elástico

<details><summary>Respuesta</summary>**B. Vertical (scale up).** Más potencia a un recurso existente. (Horizontal sería *más* máquinas.)</details>

**P9.** "Sin servidor" (serverless) significa que:
- A) No existen servidores · B) Tú gestionas los servidores · C) El proveedor gestiona los servidores por ti · D) No se puede ejecutar código

<details><summary>Respuesta</summary>**C.** Los servidores existen, pero el proveedor los gestiona de forma invisible. Tú solo aportas el código.</details>

**P10.** Un hospital debe mantener datos sensibles en infraestructura exclusiva por normativa, pero usa la nube pública para su web. ¿Qué modelo de implementación es?
- A) Pública · B) Privada · C) Híbrida · D) Comunitaria

<details><summary>Respuesta</summary>**C. Híbrida.** Combina privada (datos sensibles) y pública (web).</details>

---

### 14.2 Preguntas — Dominio 2 (Arquitectura y servicios)

**P1.** Tu aplicación debe seguir disponible aunque falle un centro de datos completo **dentro de la misma región**. ¿Qué usas?
- A) Pares de regiones · B) Zonas de disponibilidad · C) Grupos de recursos · D) Etiquetas

<details><summary>Respuesta</summary>**B. Zonas de disponibilidad** → alta disponibilidad dentro de una región.</details>

**P2.** ¿Cuál es el contenedor lógico que agrupa recursos relacionados para gestionarlos juntos?
- A) Suscripción · B) Grupo de administración · C) Grupo de recursos · D) Región

<details><summary>Respuesta</summary>**C. Grupo de recursos.**</details>

**P3.** ¿Cuál es la **unidad de facturación** en la jerarquía de Azure?
- A) Grupo de recursos · B) Suscripción · C) Recurso · D) Región

<details><summary>Respuesta</summary>**B. Suscripción.**</details>

**P4.** Necesitas una conexión a Azure que **no pase por internet público**, con baja latencia constante. ¿Qué eliges?
- A) VPN Gateway · B) ExpressRoute · C) Azure DNS · D) Peering

<details><summary>Respuesta</summary>**B. ExpressRoute** = línea privada dedicada. (La VPN viaja cifrada *por* internet.)</details>

**P5.** Tienes 200 TB de datos históricos y tu internet tardaría meses en subirlos. ¿Qué usas?
- A) AzCopy · B) Azure File Sync · C) Azure Data Box · D) Storage Explorer

<details><summary>Respuesta</summary>**C. Azure Data Box.** Dispositivo físico para mover volúmenes enormes.</details>

**P6.** Quieres exigir un código del celular además de la contraseña al iniciar sesión. ¿Qué función?
- A) SSO · B) RBAC · C) MFA · D) Zero Trust

<details><summary>Respuesta</summary>**C. MFA (autenticación multifactor).**</details>

**P7.** ¿Qué tipo de almacenamiento usarías para guardar videos e imágenes (no estructurados)?
- A) Table · B) Queue · C) Blob · D) Files

<details><summary>Respuesta</summary>**C. Blob.**</details>

**P8.** Quieres ejecutar pequeños fragmentos de código en respuesta a eventos, pagando solo por ejecución, sin gestionar servidores. ¿Qué usas?
- A) Máquinas virtuales · B) Azure Functions · C) App Service · D) AKS

<details><summary>Respuesta</summary>**B. Azure Functions** (cómputo serverless por eventos).</details>

**P9.** ¿Qué le da **alta disponibilidad** a un grupo de VMs distribuyéndolas en distinto hardware dentro de un centro de datos?
- A) VM Scale Sets · B) Conjuntos de disponibilidad · C) Pares de regiones · D) Peering

<details><summary>Respuesta</summary>**B. Conjuntos de disponibilidad** (*availability sets*). (Los *Scale Sets* son para escalar el número de VMs automáticamente.)</details>

**P10.** Un usuario demuestra **quién es** con su huella digital. ¿Eso es autenticación o autorización?

<details><summary>Respuesta</summary>**Autenticación** (demostrar identidad). La autorización sería decidir qué puede hacer después.</details>

**P11.** Quieres que una base de datos sea accesible **solo desde tu red privada**, sin exposición a internet. ¿Qué usas?
- A) Punto de conexión público · B) Punto de conexión privado · C) VPN Gateway · D) Azure DNS

<details><summary>Respuesta</summary>**B. Punto de conexión privado.**</details>

**P12.** Necesitas máxima portabilidad y arranque en segundos para una arquitectura de microservicios. ¿Qué tecnología de cómputo encaja mejor?
- A) Máquinas virtuales · B) Contenedores · C) Azure Virtual Desktop · D) Availability sets

<details><summary>Respuesta</summary>**B. Contenedores.** Ligeros, portátiles, arrancan en segundos.</details>

**P13.** ¿Qué redundancia replica tus datos en **otra región** para protegerte de un desastre regional?
- A) LRS · B) ZRS · C) GRS · D) Ninguna

<details><summary>Respuesta</summary>**C. GRS** (Geo-Redundant Storage).</details>

**P14.** ¿Qué servicio es la **red privada base** dentro de la cual viven tus recursos en Azure?
- A) Azure DNS · B) Virtual Network (VNet) · C) ExpressRoute · D) Subred

<details><summary>Respuesta</summary>**B. Virtual Network (VNet).** (La subred es una *subdivisión* de la VNet.)</details>

---

### 14.3 Preguntas — Dominio 3 (Administración y gobernanza)

**P1.** Quieres **estimar el costo** de unos recursos **antes** de crearlos. ¿Qué herramienta?
- A) Cost Management · B) Pricing Calculator · C) Azure Advisor · D) Azure Policy

<details><summary>Respuesta</summary>**B. Pricing Calculator** (estima antes; planeación).</details>

**P2.** Tu organización quiere **impedir** que se creen recursos fuera de la región permitida. ¿Qué usas?
- A) RBAC · B) Bloqueos · C) Azure Policy · D) Etiquetas

<details><summary>Respuesta</summary>**C. Azure Policy** (reglas sobre los recursos).</details>

**P3.** Quieres evitar que un recurso crítico se **borre por accidente**, pero permitir editarlo. ¿Qué aplicas?
- A) Bloqueo ReadOnly · B) Bloqueo CanNotDelete · C) Azure Policy · D) MFA

<details><summary>Respuesta</summary>**B. Bloqueo CanNotDelete.** (ReadOnly impediría también editar.)</details>

**P4.** Necesitas administrar, desde Azure, servidores que están en tu centro de datos local y en otra nube. ¿Qué servicio?
- A) Azure Arc · B) Azure Monitor · C) ExpressRoute · D) Azure Migrate

<details><summary>Respuesta</summary>**A. Azure Arc** (gestiona recursos fuera de Azure).</details>

**P5.** ¿Qué herramienta da **recomendaciones** para mejorar seguridad, costo y rendimiento de tus recursos?
- A) Service Health · B) Azure Advisor · C) Log Analytics · D) Azure Policy

<details><summary>Respuesta</summary>**B. Azure Advisor.**</details>

**P6.** Quieres desplegar el **mismo entorno completo** de forma repetible con un archivo, sin clics manuales. ¿Qué enfoque?
- A) Azure Portal · B) Plantillas ARM (IaC) · C) Storage Explorer · D) Azure Advisor

<details><summary>Respuesta</summary>**B. Plantillas ARM / Infraestructura como código.**</details>

**P7.** ¿Qué herramienta te avisa si hay una **caída del lado de Azure** que afecta tus servicios?
- A) Azure Monitor · B) Azure Advisor · C) Azure Service Health · D) Cost Management

<details><summary>Respuesta</summary>**C. Azure Service Health.** (Monitor es para *tus* recursos; Advisor da recomendaciones.)</details>

**P8.** Quieres **agrupar y filtrar costos** por proyecto y departamento. ¿Qué usas?
- A) Etiquetas (tags) · B) Bloqueos · C) RBAC · D) Azure Policy

<details><summary>Respuesta</summary>**A. Etiquetas (tags).**</details>

**P9.** Diferencia clave: RBAC controla ____ y Azure Policy controla ____.
- A) recursos / personas · B) personas / recursos · C) costos / seguridad · D) redes / identidades

<details><summary>Respuesta</summary>**B. personas / recursos.** "Roles a las personas, Policy a los recursos."</details>

**P10.** ¿Qué componente de Azure Monitor supervisa el **rendimiento de aplicaciones** (tiempos de respuesta, errores)?
- A) Log Analytics · B) Application Insights · C) Service Health · D) Advisor

<details><summary>Respuesta</summary>**B. Application Insights.**</details>

**P11.** Quieres **controlar y analizar el gasto real** ya en curso y poner alertas de presupuesto. ¿Qué herramienta?
- A) Pricing Calculator · B) TCO Calculator · C) Microsoft Cost Management · D) Azure Advisor

<details><summary>Respuesta</summary>**C. Microsoft Cost Management** (controla el gasto real; operación).</details>

**P12.** ¿Qué herramienta usarías para **comparar** el costo de operar on-premises vs. en Azure?
- A) Pricing Calculator · B) TCO Calculator · C) Cost Management · D) Azure Policy

<details><summary>Respuesta</summary>**B. TCO Calculator** (Total Cost of Ownership: on-premises vs. Azure).</details>

---

### 14.4 Preguntas — Temas avanzados y transversales

Preguntas sobre los temas de mayor matiz (categorías de servicios, gobernanza, arquitectura).

**P1.** Una fábrica quiere conectar miles de sensores que envían lecturas de temperatura en tiempo real a Azure. ¿Qué categoría de servicio aplica?
- A) IA/Machine Learning · B) IoT · C) Serverless · D) Contenedores

<details><summary>Respuesta</summary>**B. IoT** (Internet de las cosas): conectar y gestionar dispositivos/sensores. (Ej.: Azure IoT Hub.)</details>

**P2.** Necesitas analizar automáticamente el sentimiento (positivo/negativo) de miles de reseñas de clientes. ¿Qué categoría usas?
- A) IoT · B) Edge · C) IA / Machine Learning · D) Almacenamiento

<details><summary>Respuesta</summary>**C. IA / Machine Learning** (servicios de lenguaje/análisis, p. ej. Azure AI services).</details>

**P3.** Quieres procesar datos de una cámara industrial **en el propio dispositivo**, con mínima latencia, sin enviar todo a la nube. ¿Qué enfoque es?
- A) Edge computing · B) ExpressRoute · C) Blob Storage · D) Region pairs

<details><summary>Respuesta</summary>**A. Edge computing**: procesar cerca del origen de los datos para reducir latencia y uso de red.</details>

**P4.** Un auditor pide los informes de cumplimiento ISO 27001 y SOC 2 de Azure. ¿Dónde se obtienen?
- A) Azure Advisor · B) Service Trust Portal · C) Azure Monitor · D) Microsoft Purview

<details><summary>Respuesta</summary>**B. Service Trust Portal**: publica auditorías y certificaciones de cumplimiento de Microsoft.</details>

**P5.** Quieres asegurar que un grupo de máquinas virtuales no se reinicien todas a la vez durante un mantenimiento ni fallen juntas por un problema de hardware. ¿Qué usas?
- A) VM Scale Sets · B) Conjuntos de disponibilidad (availability sets) · C) Azure Arc · D) Peering

<details><summary>Respuesta</summary>**B. Conjuntos de disponibilidad**: usan dominios de error y de actualización para repartir las VMs en hardware distinto.</details>

**P6.** Tu aplicación tiene una demanda muy variable y quieres que el número de VMs idénticas aumente y disminuya **automáticamente**. ¿Qué usas?
- A) Availability sets · B) VM Scale Sets · C) Azure Virtual Desktop · D) Azure Functions

<details><summary>Respuesta</summary>**B. VM Scale Sets**: escalan automáticamente el número de instancias según la demanda.</details>

**P7.** ¿Qué herramienta de gobierno de datos descubre y clasifica información sensible en toda la organización?
- A) Azure Policy · B) Microsoft Purview · C) Defender for Cloud · D) Service Health

<details><summary>Respuesta</summary>**B. Microsoft Purview** (gobierno y clasificación de datos). (Azure Policy aplica reglas a recursos; Defender for Cloud es seguridad.)</details>

**P8.** Empleados de una empresa asociada deben acceder a un proyecto compartido usando sus propias cuentas corporativas. ¿Qué función lo permite?
- A) SSO · B) Identidades externas (B2B) · C) RBAC · D) Passwordless

<details><summary>Respuesta</summary>**B. Identidades externas (B2B)**: colaboración con otras organizaciones usando sus identidades.</details>

---

## 15. Simulacro de examen integrador

20 preguntas mezcladas de los tres dominios, en el estilo del examen. Resuélvelas **de corrido** (ponte ~20 min) y luego revisa. **Meta para agendar: 16/20 o más.**

1. Pagar solo por lo que consumes, sin inversión inicial: ¿qué tipo de gasto es?
2. ¿IaaS, PaaS o SaaS te da más control sobre el sistema operativo?
3. ¿Qué da alta disponibilidad **dentro** de una región?
4. ¿Cuál es la unidad de **facturación** en la jerarquía de Azure?
5. Conexión privada dedicada que **no** pasa por internet: ¿cuál?
6. ¿Qué tipo de almacenamiento usarías para videos e imágenes?
7. Nivel de almacenamiento más barato para datos casi nunca accedidos: ¿cuál?
8. Demostrar **quién eres** al iniciar sesión: ¿autenticación o autorización?
9. Herramienta para **estimar costos antes** de crear recursos: ¿cuál?
10. Reglas que impiden crear recursos fuera de una región permitida: ¿qué servicio?
11. Permisos según el rol de cada persona: ¿qué mecanismo?
12. Recomendaciones para mejorar seguridad/costo/rendimiento: ¿qué herramienta?
13. ¿Qué te avisa si hay una **caída del lado de Azure**?
14. Gestionar servidores que están **fuera** de Azure desde el portal de Azure: ¿qué servicio?
15. Desplegar un entorno completo de forma repetible con un archivo: ¿qué enfoque?
16. ¿Qué beneficio es "recuperarse de fallas"? (confiabilidad o predictibilidad)
17. Cómputo ligero y portátil para microservicios: ¿VMs o contenedores?
18. ¿Qué redundancia protege contra el desastre de una región **entera**?
19. Bloqueo que impide borrar pero permite editar: ¿cuál?
20. Servicio de identidad y directorio en la nube de Microsoft: ¿cuál?

<details><summary>Ver todas las respuestas</summary>

1. OpEx (modelo basado en consumo) · 2. **IaaS** · 3. **Zonas de disponibilidad** · 4. **Suscripción** · 5. **ExpressRoute** · 6. **Azure Blob** · 7. **Archive** · 8. **Autenticación** · 9. **Pricing Calculator** · 10. **Azure Policy** · 11. **RBAC** · 12. **Azure Advisor** · 13. **Azure Service Health** · 14. **Azure Arc** · 15. **Plantillas ARM (IaC)** · 16. **Confiabilidad** · 17. **Contenedores** · 18. **GRS (geo-redundancia)** · 19. **CanNotDelete** · 20. **Microsoft Entra ID**

**Tu puntaje:**
- **18–20:** Excelente — listo para agendar.
- **15–17:** Bien — repasa los pares confundibles (sección 10) y vuelve a intentar.
- **<15:** Identifica los dominios donde fallaste y reestúdialos antes de seguir.
</details>

---

## 16. Estrategia para el día del examen

### Antes del examen
- **Descansa bien la noche anterior.** Un cerebro descansado rinde más que uno que estudió hasta tarde.
- **Repasa solo la sección 10 (pares confundibles) y las cheat sheets (sección 12)** la mañana del examen. No intentes aprender cosas nuevas ese día.
- **Si es en línea:** prepara tu espacio (habitación privada, escritorio despejado, buena conexión, webcam). Llega 15–30 min antes para el registro.

### Durante el examen
1. **Recuerda: 700/1000, ponderado.** Puedes fallar varias y aprobar. **No te bloquees** en una pregunta difícil.
2. **Lee cada pregunta completa y con cuidado.** La terminología exacta importa: una sola palabra ("antes/después", "privado/público") puede cambiar la respuesta.
3. **En preguntas de escenario,** pregúntate: *"¿qué servicio resuelve **exactamente** esta necesidad concreta?"*. Suele haber dos opciones plausibles; elige la que encaja mejor con el detalle del caso.
4. **Descarta primero las opciones claramente falsas.** Reduces a dos y decides entre ellas.
5. **Marca y avanza.** Si dudas, marca la pregunta, responde tu mejor opción y sigue. Vuelve al final con tiempo y mente fresca.
6. **En "selecciona todas las que apliquen":** evalúa cada opción como verdadero/falso independiente. No hay puntos parciales.
7. **No sobreanalices.** En nivel *Fundamentals*, la respuesta directa suele ser la correcta. No inventes trampas que no existen.
8. **No dejes preguntas en blanco.** No hay penalización por error: si no sabes, razona y elige la más probable.

### Mentalidad
La AZ-900 está **diseñada para ser aprobable**. Si estudiaste este manual, hiciste los laboratorios y practicaste hasta el 80%+, **vas preparado**. Entra con calma y confianza.

---

## 17. Recursos y siguientes pasos

### Recursos oficiales gratuitos (prioritarios)
- **Guía de estudio oficial AZ-900:** https://aka.ms/AZ900-StudyGuide
- **Página oficial de la certificación (agendar examen):** https://learn.microsoft.com/es-es/credentials/certifications/azure-fundamentals/
- **Evaluación de práctica oficial gratuita:** en la página de la certificación, sección "Práctica para el examen".
- **Espacio aislado del examen (*exam sandbox*)** — practica la interfaz y los tipos de pregunta reales: https://aka.ms/examdemo
- **Documentación de Azure:** https://learn.microsoft.com/es-es/azure/
- **Microsoft Virtual Training Days (AZ-900):** jornadas gratuitas en línea de Microsoft que a veces incluyen un **cupón de examen gratuito o con descuento**. Búscalas en el sitio de eventos de Microsoft.

### Las 4 rutas de Microsoft Learn (acceso rápido)
1. Conceptos de la nube → https://learn.microsoft.com/es-es/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/
2. Arquitectura y servicios → https://learn.microsoft.com/es-es/training/paths/azure-fundamentals-describe-azure-architecture-services/
3. Administración y gobernanza → https://learn.microsoft.com/es-es/training/paths/describe-azure-management-governance/
4. Proyectos guiados → https://learn.microsoft.com/es-es/training/paths/introduction-cloud-infrastructure-apply-azure-skills-guided-projects/

### Complementos opcionales
- Cursos en español en Udemy/Coursera/DataCamp (verifica fecha 2025/2026).
- Libro: *Exam Ref AZ-900 Microsoft Azure Fundamentals* (última edición disponible).
- Canales de YouTube de repaso AZ-900 (refuerzo visual).

> ⚠️ **Sobre simuladores externos:** úsalos para practicar el **formato**, no para memorizar respuestas (muchos tienen errores). La evaluación de práctica **oficial** es la referencia más fiel.

### Después de aprobar: ¿qué sigue?
La AZ-900 es la base. Desde aquí, según tu objetivo profesional:
- **Administración de infraestructura** → **AZ-104** (Azure Administrator).
- **Desarrollo de aplicaciones** → **AZ-204** (Azure Developer).
- **Arquitectura de soluciones** → **AZ-305** (Solutions Architect).
- **Automatización y CI/CD** → **AZ-400** (DevOps Engineer).
- **Seguridad** → **AZ-500** (Security Engineer).
- **Otras fundamentales** → **AI-900** (IA), **DP-900** (datos), **SC-900** (seguridad/identidad).

---

## 18. Checklist final antes de agendar

Marca cada punto. Cuando todos estén ✅, estás listo para agendar con confianza:

- [ ] Leí el Capítulo 0 y entiendo el vocabulario base (servidor, VM, red, base de datos, etc.).
- [ ] Completé las 4 rutas de Microsoft Learn, **incluyendo los laboratorios prácticos**.
- [ ] Entiendo IaaS vs. PaaS vs. SaaS y quién administra qué en cada uno.
- [ ] Domino el modelo de responsabilidad compartida (mis 3 cosas: datos, dispositivos, identidades).
- [ ] Distingo confiabilidad de predictibilidad, y autenticación de autorización.
- [ ] Sé la jerarquía: Grupos de administración → Suscripciones → Grupos de recursos → Recursos.
- [ ] Diferencio zonas de disponibilidad (alta disponibilidad) de pares de regiones (recuperación ante desastres).
- [ ] Sé cuándo usar VPN Gateway vs. ExpressRoute, y punto público vs. privado.
- [ ] Conozco los tipos (Blob/Files...), niveles (Hot/Cool/Archive) y redundancia (LRS/ZRS/GRS) de almacenamiento.
- [ ] Entiendo Entra ID, MFA, SSO, RBAC, Zero Trust y defensa en profundidad.
- [ ] Diferencio Pricing Calculator (estima antes) de Cost Management (controla después).
- [ ] Sé qué hace Azure Policy (recursos) vs. RBAC (personas), y los tipos de bloqueo.
- [ ] Distingo Azure Advisor, Service Health y Azure Monitor.
- [ ] Comprendo IaC, plantillas ARM y Azure Arc.
- [ ] Resolví el banco de preguntas de cada dominio con >80%.
- [ ] Resolví el simulacro integrador con 16/20 o más.
- [ ] Hice la **evaluación de práctica oficial** y saco >80% de forma consistente.

---

### 🎯 Palabras finales

Si estudiaste este manual de principio a fin, hiciste los laboratorios de Microsoft Learn y practicaste hasta superar el 80% de forma consistente, tienes una preparación de **nivel mundial** para la AZ-900 — apuntando no apenas a aprobar, sino a **dominar** el material.

Recuerda la idea que recorre todo el manual: **no se trata de memorizar, sino de entender qué problema resuelve cada servicio y cuándo usarlo.** Con esa comprensión, respondes correctamente incluso preguntas que nunca habías visto.

Entra al examen con calma y confianza. **Lo tienes.** 🚀

---
---

# PARTE VI — APÉNDICES

## Apéndice A — Metodología de creación de este manual (playbook reproducible)

> **Para qué sirve este apéndice.** Documenta, paso a paso, **cómo se construyó este manual**, de modo que el mismo proceso pueda **replicarse íntegro** para las siguientes certificaciones (AZ-104 Azure Administrator, AZ-204, AZ-305, AZ-400, AZ-500, AI-900, DP-900, SC-900, o incluso certificaciones de otros proveedores). Si entregas este apéndice como instrucción —junto con el nombre de la nueva certificación— se obtiene un manual con el mismo estilo, rigor, estructura y nivel de calidad. Está escrito como una receta: síguela en orden.

---

### A.0 Resumen ejecutivo del método (la receta en una página)

1. **Investiga y verifica** el temario oficial y la ruta de aprendizaje oficial del proveedor; extrae los **objetivos de aprendizaje y las unidades de cada módulo** (este paso es el que evita huecos).
2. **Verifica los datos logísticos** del examen (costo, duración, n.º de preguntas, puntaje de aprobación, formatos de pregunta, idiomas, vigencia).
3. **Construye el documento** siguiendo la arquitectura fija de partes (Fundamentos y método → Conocimiento base → Dominios en profundidad → Refuerzo → Práctica → Apéndices).
4. **Redacta cada concepto** con la plantilla de profundidad: *qué es / cómo funciona / cuándo usarlo (y cuándo no) / ejemplo / clave de examen / trampa común*.
5. **Aplica las convenciones visuales** (cajas de Microsoft Learn, claves, trampas, analogías, notas, escenarios resueltos).
6. **Crea la práctica** (banco de preguntas por dominio, escenarios resueltos, simulacro integrador), siempre con preguntas **originales**.
7. **Produce el PDF imprimible** con el pipeline técnico (Markdown → HTML → PDF), garantizando que las respuestas sean visibles en papel.
8. **Audita en iteraciones**: revisa contra el temario oficial, busca huecos, mejora, regenera. Repite hasta que el checklist de completitud esté 100% marcado.

---

### A.1 Filosofía y principios rectores (no negociables)

Estos principios definen la identidad del manual. Si alguno se rompe, el documento deja de ser "de nivel mundial".

1. **Información 100% verificada.** Todo dato del examen y todo enlace a la ruta oficial se obtiene y se comprueba en la fuente del proveedor (no de memoria, no de blogs). Si un dato no se puede verificar, no se incluye o se marca como aproximado.
2. **Honestidad sin garantías falsas.** Nunca se promete que "con solo leer esto apruebas". Se explica con franqueza que la preparación completa es *manual + laboratorios oficiales + evaluación de práctica oficial*, y que aprobar depende del estudio del lector.
3. **Profundidad real, no relleno.** El valor está en explicar bien cada concepto, no en inflar páginas. Se prefiere una explicación clara y un buen ejemplo a tres párrafos vacíos. El número de páginas nunca es un objetivo en sí mismo.
4. **Autosuficiencia.** El manual debe poder estudiarse por sí solo: desde cero (con el Capítulo 0) hasta el dominio del temario, sin depender de otras fuentes para *entender* (aunque sí se recomienden los laboratorios para *practicar*).
5. **Doble audiencia.** Sirve al principiante absoluto (que necesita el Capítulo 0 y las analogías) y al experto (que usa las hojas de referencia y la práctica). Las analogías cotidianas y las "claves de examen" cubren ambos extremos.
6. **Mapeo explícito a la fuente oficial.** Cada bloque de contenido indica **dónde estudiarlo en la ruta oficial** (módulo y unidad exactos), para que el lector pueda profundizar y hacer los laboratorios.
7. **Orientación al examen.** Todo se explica con la pregunta rectora: *"¿qué problema resuelve y cuándo se usa?"* — porque así se responden incluso preguntas no vistas. Se destacan las distinciones que el examen explota (pares confundibles).
8. **Imprimible y de consulta.** El resultado final debe poder imprimirse y estudiarse en papel cómodamente, y servir como obra de referencia permanente.

---

### A.2 Fase 1 — Investigación y verificación de fuentes

Esta fase es la que más distingue un manual riguroso de un resumen genérico. **No se redacta nada hasta completarla.**

#### A.2.1 Obtener el temario oficial ("Skills Measured") y su fecha de vigencia
- Localiza la **guía de estudio oficial** de la certificación (para las de Microsoft suele estar en `https://aka.ms/[CÓDIGO]-StudyGuide`, p. ej. `aka.ms/AZ900-StudyGuide`).
- Anota la **fecha de vigencia del temario** ("Skills measured as of [fecha]"). Los temarios se actualizan; el manual debe declarar a qué versión corresponde.
- Extrae los **dominios** (áreas de habilidades) y su **peso porcentual**. Estos definen las secciones de la Parte III y cómo se reparte el esfuerzo.

#### A.2.2 Identificar la ruta de aprendizaje oficial y sus módulos
- Para certificaciones de Microsoft, existe una **ruta/serie oficial en Microsoft Learn** diseñada para esa certificación. Identifícala (para AZ-900 es la serie *"Introduction to Cloud Infrastructure"*).
- Lista todas las **rutas (learning paths)** que la componen y, dentro de cada una, todos los **módulos**, con sus **URLs reales**.
- **Truco de idioma:** las URLs suelen estar en inglés (`/en-us/`); cambiando a `/es-es/` se obtiene la versión en español.

#### A.2.3 Extraer objetivos de aprendizaje y unidades de CADA módulo (paso crítico)
> **Este es el paso que reveló los huecos en las primeras versiones de este manual.** No te saltes ninguno.
- Abre (fetch) la página de **cada módulo** y extrae: (a) sus **objetivos de aprendizaje** oficiales y (b) la lista de **unidades** que lo componen.
- Usa esa lista como **checklist de completitud**: cada objetivo y cada unidad debe quedar cubierto en el manual. Si un tema aparece en un módulo y no en tu borrador, es un hueco que hay que llenar.
- Ejemplo real de esta guía: al hacer esto se detectó que faltaban **IA/ML, IoT/Edge** (módulo de cómputo), el **Service Trust Portal** (módulo de gobernanza) y los **recursos de una VM / conjuntos de disponibilidad**. Se añadieron en la auditoría.

#### A.2.4 Verificar los datos logísticos del examen
Comprueba y registra: **costo**, **duración**, **número aproximado de preguntas**, **puntaje de aprobación** (y si es escala ponderada, explícalo), **formatos de pregunta**, **idiomas disponibles**, **política de reintentos** y **vigencia/caducidad** de la credencial. Incluye los **recursos oficiales** (sandbox del examen, evaluación de práctica, cuenta gratuita).

#### A.2.5 Fuentes canónicas (orden de prioridad)
1. Guía de estudio oficial del examen (temario "Skills Measured").
2. Páginas de la ruta y de los módulos oficiales de aprendizaje (objetivos + unidades).
3. Página oficial de la certificación (datos logísticos, agendar).
4. Documentación oficial del producto (para matices técnicos).
> ⚠️ **Regla:** no se usan blogs, foros ni "dumps" de preguntas como fuente. Las preguntas de práctica del manual son **siempre originales**, creadas en el estilo del examen.

---

### A.3 Fase 2 — Arquitectura del documento (estructura fija)

Todo manual de esta colección sigue **la misma estructura de seis partes**. Esto garantiza consistencia entre certificaciones.

| Parte | Contenido | Notas de adaptación |
|---|---|---|
| **Portada** | Título, código, subtítulo, caja con versión del temario/idioma/nivel, fecha. | Cambia el código y el nombre de la certificación. |
| **Cómo está organizado + Índice** | Tabla de las partes y para quién es cada una; índice navegable. | Igual para todas. |
| **I. Fundamentos y método** | (1) Qué es la certificación y por qué vale la pena · (2) Anatomía del examen (formato, tipos de pregunta, puntaje) · (3) Método de estudio · (4) **Mapa completo de la ruta oficial** (todos los módulos con URLs) · (5) Plan de estudio con calendario. | El mapa y el plan se reconstruyen con los módulos reales de la nueva certificación. |
| **II. Conocimiento base** | (6) Capítulo 0: fundamentos que el temario da por sabidos, explicados desde cero. | **Se adapta al nivel**: en certificaciones de rol (AZ-104+) el Capítulo 0 asume más base y cubre prerrequisitos más avanzados. |
| **III. Los dominios en profundidad** | Una sección por **dominio oficial**. Cada una abre con los **objetivos de aprendizaje oficiales** y las **unidades** del/los módulo(s) correspondientes, explica cada concepto a fondo, incluye cajas "dónde estudiarlo", **escenarios resueltos** y remite al banco de preguntas. | El corazón del manual. El número de secciones = número de dominios del temario. |
| **IV. Refuerzo y memorización** | Pares de conceptos confundibles · mnemotecnias · hojas de referencia rápida (cheat sheets) · glosario maestro. | Se reconstruye con los términos de la nueva certificación. |
| **V. Práctica y examen** | Banco de preguntas por dominio · simulacro integrador · estrategia del día del examen · recursos y siguientes certificaciones · checklist final antes de agendar. | Preguntas originales nuevas. |
| **VI. Apéndices** | Este playbook metodológico + cualquier material extra (p. ej. flashcards). | Se conserva y se actualiza. |

---
### A.4 Fase 3 — Reglas de redacción y profundidad por concepto

**La plantilla de profundidad (aplícala a CADA concepto/servicio importante):**
1. **Qué es** — definición precisa, con la terminología oficial exacta.
2. **Cómo funciona** — el mecanismo, en lenguaje claro.
3. **Cuándo usarlo (y cuándo no)** — casos de uso y límites; el examen pregunta esto.
4. **Ejemplo concreto** — un caso del mundo real que lo aterrice.
5. **Clave de examen** — el dato exacto que más se pregunta.
6. **Trampa común** — la confusión que el examen explota.

**Reglas de estilo:**
- **Idioma:** español claro, cálido y directo; se conserva la terminología técnica oficial (a menudo en inglés) con su traducción la primera vez.
- **Tono:** de mentor que explica con paciencia, sin condescendencia; honesto sobre dificultades y expectativas.
- **Analogías cotidianas** para todo concepto abstracto (electricidad = nube; pizza = IaaS/PaaS/SaaS; taxi = serverless; maleta vs. casa = contenedor vs. VM; cebolla/castillo = defensa en profundidad; temperatura = niveles de almacenamiento). Una buena analogía por concepto difícil.
- **Distinciones en pares:** siempre que dos conceptos se confundan, explícalos juntos y contrástalos explícitamente (y añádelos a la sección de "pares confundibles").
- **Tablas** para comparar opciones (servicios, niveles, modelos). Son más claras que el texto corrido y se memorizan mejor.
- **Negritas** para los términos clave que deben quedar grabados; sin abusar.
- **Brevedad con sustancia:** frases cortas; cero relleno; cada oración aporta.

---

### A.5 Fase 4 — Convenciones visuales y de formato

Estos elementos dan identidad y facilitan el estudio. Úsalos de forma consistente:

| Elemento | Marca | Uso |
|---|---|---|
| **Caja "dónde estudiarlo"** | <span class="badge b-learn">MS LEARN</span> | Al inicio de cada tema: módulo y unidad exactos de la ruta oficial + URL. |
| **Objetivos oficiales** | <span class="badge b-goal">OBJETIVOS</span> | Al abrir cada dominio: lista literal de objetivos de aprendizaje del proveedor. |
| **Clave de examen** | <span class="badge b-key">CLAVE</span> | El dato exacto más preguntado. |
| **Trampa común** | <span class="badge b-warn">ATENCIÓN</span> | La confusión que el examen explota. |
| **Nota práctica** | <span class="badge b-note">NOTA</span> | "En la práctica…", ejemplos del mundo real, por qué importa. |
| **Escenarios resueltos** | <span class="badge b-prac">ESCENARIOS</span> | Al final de cada dominio: 3+ casos razonados paso a paso (enunciado → razonamiento → respuesta). |
| **Analogías** | (texto "Analogía:") | Comparaciones cotidianas; en el PDF el emoji decorativo se elimina y queda la palabra "Analogía". |

> **Nota técnica sobre emojis:** en el documento Markdown se usan emojis para lectura en pantalla, pero el conversor a PDF los transforma: los **estructurales** (📚🔑⚠️💡📝🎯🎓🧪) se convierten en *badges* de texto con color (MS LEARN, CLAVE, ATENCIÓN, etc.) y los **decorativos** (🏠🍕🧅…) se eliminan, dejando el texto en negrita que los acompaña. Así el PDF imprime limpio en cualquier impresora.

---

### A.6 Fase 5 — Reglas para la práctica

- **Banco de preguntas por dominio:** 10–15 preguntas por dominio, en los formatos reales del examen (opción múltiple, selección múltiple, verdadero/falso, escenario). Cada una con **respuesta explicada** (no solo la letra: el *porqué*).
- **Preguntas originales siempre.** Se crean en el estilo del examen; **nunca** se copian preguntas reales ni de "dumps". Se indica explícitamente en el pie del documento.
- **Respuestas visibles en papel:** en el Markdown pueden ir en bloques desplegables `<details>`, pero el conversor a PDF las expande a cajas visibles para poder estudiar impreso.
- **Escenarios resueltos:** además de las preguntas, 3+ casos por dominio razonados paso a paso, que enseñan el *método de razonamiento* ("pista del enunciado → descarte → respuesta").
- **Simulacro integrador:** ~20 preguntas mezcladas de todos los dominios, con umbral de aprobación sugerido y guía de interpretación del puntaje.
- **Calibración:** se recomienda no agendar el examen hasta superar consistentemente el ~80% en la evaluación de práctica **oficial**.

---

### A.7 Fase 6 — Producción técnica (pipeline Markdown → PDF imprimible)

El manual se redacta en **Markdown** (editable, versionable) y se convierte a **PDF imprimible**. El pipeline:

1. **Fuente:** un único archivo `.md` con todo el contenido.
2. **Preprocesado** (script en Python): (a) expandir los bloques de respuesta `<details>` a cajas visibles; (b) convertir emojis estructurales en *badges* de texto y eliminar los decorativos; (c) anteponer una **portada** elegante.
3. **Conversión Markdown → HTML** con extensiones de tablas y HTML embebido.
4. **CSS de impresión:** tamaño A4, tipografía legible (cuerpo ~12.5 px), tablas con encabezado en color y filas alternadas, saltos de página por sección, cajas de color para citas/objetivos/respuestas.
5. **HTML → PDF** con `wkhtmltopdf` (márgenes A4).
6. **Verificación visual:** se renderizan páginas de muestra (portada, tablas, banco de preguntas) y se comprueba la **integridad** (bloques de respuesta balanceados, enlaces correctos, ninguna sección cortada).

**Herramientas del entorno:** `pandoc`, `wkhtmltopdf`, `python-markdown`, `pdftoppm`/`pdfinfo` (para inspección), `pypdf`. *(El motor `weasyprint` no está disponible; `wkhtmltopdf` con su Qt no soporta numeración de página por pie, así que la navegación se hace por el índice con anclas.)*

> **Regla de entrega:** se entregan **dos formatos** — el `.md` (editable, para futuras actualizaciones) y el `.pdf` (imprimible, para estudiar). El PDF se presenta primero.

---

### A.8 Fase 7 — Auditoría iterativa (el ciclo de mejora)

El manual **no se da por terminado en la primera versión**. Se mejora en iteraciones, cada una con un foco:

1. **Iteración 1 — Base:** cubrir todo el temario con estructura completa.
2. **Iteración 2 — Verificación de fuentes:** fetch de la ruta oficial; ajustar mapeo y datos.
3. **Iteración 3 — Profundidad:** expandir cada concepto con la plantilla de profundidad; añadir analogías, claves y trampas.
4. **Iteración 4 — Auditoría contra unidades:** fetch de **cada módulo**; cotejar unidad por unidad; **llenar huecos** detectados; añadir escenarios resueltos y más preguntas.
5. **Iteración N — Pulido:** legibilidad, consistencia de términos, índice, formato de impresión.

**Cómo auditar (qué buscar en cada revisión):**
- ¿Cada objetivo de aprendizaje oficial está cubierto? ¿Cada unidad de cada módulo?
- ¿Hay datos sin verificar o potencialmente desactualizados?
- ¿Los pares confundibles están todos contrastados explícitamente?
- ¿Cada dominio tiene escenarios resueltos y preguntas suficientes?
- ¿La numeración de secciones y el índice están sincronizados?
- ¿El PDF se ve correcto (tablas, respuestas visibles, sin cortes feos)?
- ¿El tono es honesto (sin garantías falsas) y la profundidad es real (sin relleno)?

---

### A.9 Checklist maestro de completitud (antes de entregar)

- [ ] Temario oficial localizado, con su **fecha de vigencia** anotada en la portada.
- [ ] **Dominios y pesos** oficiales reflejados en la estructura y el plan de estudio.
- [ ] **Ruta oficial completa** mapeada: todas las rutas y módulos con URLs reales (y truco de idioma).
- [ ] **Objetivos de aprendizaje y unidades de cada módulo** extraídos y cubiertos (sin huecos).
- [ ] **Datos del examen** verificados (costo, duración, n.º preguntas, puntaje, formatos, idiomas, reintentos, vigencia).
- [ ] Las **seis partes** presentes y completas (incluido el Capítulo 0 adaptado al nivel).
- [ ] Cada concepto importante sigue la **plantilla de profundidad** (qué/cómo/cuándo/ejemplo/clave/trampa).
- [ ] **Analogías**, **claves de examen** y **trampas** repartidas por todo el contenido.
- [ ] **Pares confundibles**, **mnemotecnias**, **cheat sheets** y **glosario** completos.
- [ ] **Banco de preguntas** (10–15 por dominio) + **escenarios resueltos** (3+ por dominio) + **simulacro** (~20), todo **original** y con respuestas explicadas.
- [ ] **Estrategia del día del examen**, **recursos oficiales** y **checklist final** incluidos.
- [ ] Este **apéndice metodológico** presente y actualizado.
- [ ] **PDF imprimible** generado, verificado visualmente y con respuestas visibles.
- [ ] Pie con **nota de fuentes** y aclaración de que las preguntas son originales.
- [ ] Tono **honesto** (sin garantía falsa de aprobar); profundidad **real** (sin relleno).

---

### A.10 Adaptaciones según el tipo de certificación

La metodología es la misma, pero el énfasis cambia según el nivel de la certificación:

| Tipo | Ejemplos | Naturaleza del examen | Cómo se adapta el manual |
|---|---|---|---|
| **Fundamentals** | AZ-900, AI-900, DP-900, SC-900 | Conceptual ("describir"); opción múltiple; sin laboratorios en el examen. | Como este manual. Capítulo 0 extenso desde cero; foco en conceptos, definiciones y casos de uso. |
| **Associate / Rol** | **AZ-104** (Administrator), AZ-204 (Developer), AZ-500 (Security) | Técnico ("configurar/implementar/administrar"); escenarios complejos; **puede incluir laboratorios prácticos en vivo** y *case studies*. | Más **procedimientos paso a paso**, **comandos** (Azure CLI/PowerShell), flujos de configuración en el portal, y **laboratorios guiados**. El Capítulo 0 asume base (no parte de cero absoluto). Más escenarios de resolución de problemas. |
| **Expert** | AZ-305 (Solutions Architect), AZ-400 (DevOps) | Diseño y arquitectura; escenarios largos; decisiones de compromiso (trade-offs). | Énfasis en **criterios de diseño**, comparación de alternativas y **árboles de decisión**. Menos "qué es", más "cuál elegir y por qué". |
| **Especialidad / otros proveedores** | Terraform Associate, CKA (Kubernetes) | Varía; algunas son **prácticas en terminal** (CKA) con tiempo límite. | Para exámenes prácticos: **mucho laboratorio**, comandos memorizables, atajos, gestión del tiempo. La fuente oficial cambia de proveedor (ajustar A.2). |

> **Regla de oro al cambiar de certificación:** repite la **Fase 1 (investigación)** completa para la nueva certificación. Nunca asumas que el temario, los módulos o los datos del examen son iguales: cámbialos por los reales y vuelve a extraer objetivos y unidades módulo por módulo.

---

### A.11 Prompt reutilizable para la siguiente certificación

Copia y adapta este encargo en una nueva conversación para replicar el manual:

> *"Quiero que crees un manual de estudio para la certificación **[CÓDIGO y NOMBRE, p. ej. AZ-104: Microsoft Azure Administrator]**, siguiendo exactamente la metodología del **Apéndice A** del manual AZ-900 que ya elaboramos (te lo adjunto / está en el proyecto). Requisitos: (1) primero investiga y verifica el temario oficial vigente y su fecha, los dominios y sus pesos, y la ruta de aprendizaje oficial con todos sus módulos; (2) haz fetch de cada módulo para extraer objetivos de aprendizaje y unidades, y úsalos como checklist de completitud; (3) verifica los datos del examen; (4) construye el documento con las seis partes y todas las convenciones (cajas MS LEARN, claves, trampas, analogías, escenarios resueltos, banco de preguntas original, simulacro, cheat sheets, glosario, checklist); (5) adapta la profundidad al nivel de la certificación según A.10 (incluye procedimientos y comandos si es de rol); (6) genera el PDF imprimible con respuestas visibles; (7) audita en iteraciones contra el temario y llena huecos; (8) sé honesto: no garantices aprobar, integra labs + práctica oficial, y prioriza profundidad real sobre número de páginas. Entrégame el .md y el .pdf."*

> **Sugerencia de continuidad:** conserva todos los manuales en un mismo proyecto/carpeta. Así cada nuevo manual puede referenciar el estilo de los anteriores y mantener la colección coherente. Mantén también una pequeña **bitácora de versiones** (qué se añadió/corrigió en cada iteración).

---

### Apéndice B — Registro de elaboración de este manual (AZ-900)

A modo de ejemplo concreto del método, así evolucionó **este** manual:

| Iteración | Foco | Resultado |
|---|---|---|
| 1 | Base estructural | Guía inicial cubriendo el temario. |
| 2 | Verificación de fuentes + honestidad | Se añadió el Capítulo 0, práctica y simulacro; se ajustaron datos del examen. |
| 3 | Profundidad "nivel mundial" | Se verificaron las 3 rutas y los 12 módulos oficiales; se expandió cada concepto; se generó el PDF imprimible. |
| 4 | Auditoría contra unidades de cada módulo | Fetch de los 12 módulos; **se detectaron y llenaron huecos** (IA/ML, IoT/Edge, Service Trust Portal, recursos de VM, conjuntos de disponibilidad); se añadieron escenarios resueltos, más preguntas y objetivos oficiales por dominio. |
| 5 | Apéndice metodológico + auditoría integral | Se documentó este playbook reproducible y se revisó todo el documento integrado. |

> **Datos de referencia capturados** (verificar siempre por si cambian): examen ~99 USD; ~45 min; ~40–60 preguntas; aprobar **700/1000** (escala ponderada); disponible en español; no caduca; reintento a 24 h. Temario vigente al **14 de enero de 2026**. Ruta oficial: serie *"Introduction to Cloud Infrastructure"* (revisión de Microsoft de marzo de 2026), 12 módulos en 3 rutas + 1 ruta de proyectos.

---

*Manual elaborado con base en el temario oficial de habilidades medidas vigente al 14 de enero de 2026 y en las rutas oficiales de Microsoft Learn (serie "Introduction to Cloud Infrastructure", revisión de Microsoft de marzo de 2026). Todos los enlaces a Microsoft Learn son oficiales. Las preguntas de práctica son originales, creadas en el estilo del examen para fines de estudio (no son preguntas reales del examen). El Apéndice A documenta la metodología completa para replicar este manual en futuras certificaciones. Verifica siempre la guía de estudio oficial en aka.ms/AZ900-StudyGuide por si hubiera actualizaciones posteriores.*
