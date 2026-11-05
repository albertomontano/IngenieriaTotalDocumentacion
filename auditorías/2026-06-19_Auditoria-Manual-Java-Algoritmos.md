# 🔍 AUDITORÍA EXHAUSTIVA — Manual Java/Algoritmos y Estructuras (Vol. I-A)

> **Documento auditado:** `programacion/Manual-Java-Algoritmos-y-Estructuras.md` (7 884 líneas).
> **Tipo:** auditoría adversarial total contra el **test de la isla desierta** (P3) y el **estándar de densidad** (§3 de CLAUDE.md).
> **Pregunta que responde:** *si imprimo SOLO este manual y me voy semanas al bosque sin internet, ¿me convierte —a mí o a cualquier persona que sepa leer, escribir y matemáticas básicas— en experto de nivel mundial en Java y algoritmos?*
> **Fecha:** 2026-06-19 · **Datos verificados a esta fecha.**
> **Método:** 7 agentes auditores en paralelo, uno por tramo, cada uno con la misma rúbrica adversarial; verificación de hechos por conocimiento experto del lenguaje y **trazas comprobadas a mano**. Logs crudos en [`logs/2026-06-19_logs-auditores.md`](logs/2026-06-19_logs-auditores.md).
> **Estado:** Completo · alimenta el tracker de implementación en [`2026-06-19_Tracker-implementacion.md`](2026-06-19_Tracker-implementacion.md).

---

## 1. Veredicto en una frase

El manual es **excelente** —muy por encima de la mayoría de libros comerciales— y **pasa el test de la isla desierta para su objetivo declarado (entrevista SDET / mid-level)**, pero **NO alcanza, tal cual está hoy, la promesa literal de "experto mundial solo con esto"**: lo impiden **un puñado de errores factuales reales** (que el lector memorizaría mal), **dos algoritmos que no son implementables** con lo escrito (merge sort y quicksort), y **huecos temáticos de profundidad** que un experto debe dominar y aquí solo se nombran.

**Puntaje global ponderado: 7.6 / 10.** Corregidos los errores factuales y los dos huecos de auto-suficiencia, sube a ~8.7; cerrados los huecos de experto, a ≥9.5.

---

## 2. Puntajes por tramo

| Tramo | Secciones | Isla desierta | Puntaje | Auditor |
|---|---|---|---|---|
| 1 | Preliminar + Java §0.0–0.5 (qué es Java, JVM/GC, 1er programa, tipos, operadores, control) | Parcial→Sí | **8.5** | logs#1 |
| 2 | Java §0.6–0.10 (métodos, POO, 4 pilares, interfaces, excepciones) | Parcial | **6.5** | logs#2 |
| 3 | Java §0.11–0.15 (colecciones, genéricos, esenciales, frameworks, lambdas/streams) | Parcial | **6.5** | logs#3 |
| 4 | Big-O + Estructuras de datos (Partes 1–2) | Parcial | **7.5** | logs#4 |
| 5 | Patrones 1–7 | Parcial | **8.0** | logs#5 |
| 6 | Patrones 8–13 + algoritmos con nombre | Parcial (→No en 2 puntos) | **7.0** | logs#6 |
| 7 | Banco de preguntas + referencia + apéndice | Sí (parcial-alto) | **8.5** | logs#7 |

**Lo más fuerte:** las analogías con números, el desglose palabra-por-palabra, las trazas verificadas (Two Sum, dos punteros, ventana `"abcabcbb"`, binaria, factorial, fib, subconjuntos, permutaciones, Kadane=6, monedas=3, robber=12, temperaturas=`[1,1,4,2,1,1,0,0]` — **todas correctas**), el banco de preguntas y la honestidad del apéndice. **El manual NO depende de internet para aprender:** la Parte 6 (enlaces) está correctamente marcada como complemento prescindible.

---

## 3. Hallazgos CRÍTICOS (🔴) — errores que rompen la promesa

Estos son falsedades que el lector tomaría como verdad, o código que no se puede ejecutar/implementar. **Prioridad máxima.**

| # | Ubicación | Problema | Corrección |
|---|---|---|---|
| C1 | §0.4.7 Bitwise | `>>` presentado como "dividir entre 2" (falso para negativos: `-3>>1 = -2`, no `-1`) **y falta `>>>`** (el operador estrella de entrevistas: `mid=(lo+hi)>>>1`). | Corregir la equivalencia (÷2 redondeando a −∞) y añadir fila `>>>` con su uso anti-overflow. |
| C2 | §0.8.1 Encapsulación | Orden de visibilidad **invertido**: dice `protected` es *menos* abierto que *default*. Es al revés: `protected` = paquete **+** subclases ⊋ default. | Corregir el orden y aclarar que `protected` añade subclases (incluso de otro paquete). |
| C3 | §0.10.4 Excepciones | "try-with-resources **reemplaza** al obsoleto `finalize()`" — conceptualmente falso (cierre determinista ≠ ciclo de vida del GC). | Reescribir: son mecanismos distintos; `finalize` quedó deprecated y no sirve para liberar recursos. |
| C4 | §0.11.4 y §0.11.8 Ej.1 | Salidas de `HashMap` presentadas como **orden determinista** (`{a=3, b=1, c=1}`), contradiciendo lo que el propio manual enseña (HashMap no garantiza orden). El lector correrá el código y verá otro orden. | Marcar "orden no garantizado" o usar `LinkedHashMap`/`TreeMap` si se quiere salida fija. |
| C5 | Patrón 2, tabla 2.J "Negativos" | Celda de caso borde con anotación **rota y contradictoria** ("-1+… no; -3+…") que sugiere que la pareja correcta falla. | Reescribir limpia: resultado `[1,2]`, justificación `-1 + 2 = 1`. |
| C6 | Patrón 10, `fusionar` | **Bug de aliasing:** `res.add(cur)` guarda la referencia al arreglo de entrada y luego lo muta → efecto colateral sobre el input. | `res.add(new int[]{cur[0], cur[1]})` + advertir el caso de intervalos que se tocan (`[1,3],[3,5]`). |
| C7 | Patrón 13, `formasEscalera` | Caso base inconsistente: `formas(0)` devuelve 0 (debería ser 1) y `return n` mezcla convenciones; 13.J exige definir los casos base y aquí no se define `formas(0)`. | Unificar a convención Fibonacci limpia (`dp[0]=1, dp[1]=1`) o documentar dominio n≥1, mostrando `formas(0)=1`. |
| **C8** | Ordenamientos 🅐 y 🅑 | **`mezclar()` y `particionar()` NO existen** — están como comentario. Merge sort y quicksort **no son implementables** con lo dado: falta justo la parte difícil. **El hueco más grave del manual.** | Escribir el cuerpo completo de `mezclar` (arreglo auxiliar + 2 punteros + remanentes) y `particionar` (Lomuto) con su traza. |
| C9 | Patrón 7 (árboles) | Rompe el estándar de densidad: sin traza paso a paso, sin bugs clásicos, sin complejidad derivada, sin los 3 órdenes DFS. Es referencia, no lección → no se puede "pasar de leer a resolver" solo con esto. | Subir al estándar: traza de `porNiveles`, bug del `cola.size()`, complejidad O(n)/O(ancho), caja de pre/in/post-orden. |

---

## 4. Hallazgos IMPORTANTES (🟠) — errores y huecos que sí pesan

**Errores factuales / código:**
- **§1-B.1** `String` interno desde Java 9 es `byte[]` + coder (Compact Strings), **no** `char[]`. Mantener la analogía conceptual pero corregir el hecho.
- **§1.7 / Parte 2** `Arrays.sort(int[])` usa Dual-Pivot Quicksort → **peor caso O(n²)**; solo `Arrays.sort(Object[])`/`Collections.sort` (TimSort) es O(n log n) garantizado y estable. El manual lo afirma sin matiz.
- **§5.7 + tabla §10.1** Contradicción: tras explicar la treeificación (cubeta → O(log n)) concluye "peor caso O(n)". Precisar: O(log n) si las claves son `Comparable`, O(n) si no.
- **§2.5 + tabla §10.1** Lista enlazada simple: insertar/borrar **al final es O(n)**, no O(1). La tabla insinúa O(1) en "extremos" y contradice §2.5.c.
- **§3.3/§4.3** `int x = cola.poll();` / `pila.pop();` → **NPE por autounboxing** si está vacía, incompatible con el comentario "null si vacía". Usar `Integer`.
- **Patrón 3** `sumaMaxK` **revienta con `k > arr.length`** (AIOOBE) pese a que la tabla 3.K dice manejar ese caso. Añadir guarda.
- **Patrón 11** Salida `[2,1]` de `kMasFrecuentes` presentada como determinista; el orden interno del heap no está garantizado. Mostrar como conjunto o aclarar.
- **Patrón 12** "Subarreglos que suman K" se enseña sin código y **sin el caso base crítico `map.put(0,1)`** → off-by-one garantizado.
- **Patrón 1** "O(n²), n=10⁶ ≈ 11.5 días" inconsistente con el supuesto de op/s del resto del manual (con 10⁹ op/s son ~minutos). Unificar supuesto.
- **§7 (banco)** 6 problemas marcados "(idea)" sin código completo: **3Sum, Course Schedule, Permutaciones, Combination Sum, K más frecuentes, Min-Stack** — el §4.3 promete "código con traza y Big-O" para cada uno.

**Huecos de profundidad (experto):**
- **§0.6–0.10:** composición vs herencia; reglas reales de un *override* válido (covarianza, acceso, excepciones); conflicto del diamante en *default methods* (`A.super.m()`); try-with-resources **múltiple + excepciones suprimidas**; **encadenamiento de causas** (`new X("...", e)` / "Caused by:"); trampa del `return`/`throw` en `finally`; traza visual de referencias en §0.6.6.
- **§0.12–0.15:** **PECS** nombrado + por qué `add` no compila sobre `? extends`; **`Optional`** (retorno de reduce/findFirst/max/min); **Collectors** (groupingBy, joining, toMap); **parallel streams**; demostración real de *laziness*; "stream se consume una vez"; **copia defensiva** en inmutabilidad (final ≠ inmutable); **contrato completo de `equals`** (5 propiedades + simetría/herencia).
- **Parte 2:** **AVL/Red-Black** (qué es una rotación, invariantes) solo nombrados; **heapify O(n)** ausente; **borrado en BST** (sucesor inorden) y **en Trie** sin algoritmo; **doubly/circular linked list** mencionadas, no enseñadas; columna de **espacio** en recorridos de árbol; traza del **arreglo interno del heap** y de las **cubetas del hash**.
- **Patrones:** Three Sum con **manejo de duplicados**; búsqueda binaria en **rotado** (código); **ventana mínima** (Map de conteos); **memoización in-situ** en recursión; **duplicados en backtracking**; traza numérica de **Dijkstra**; **topological sort por DFS** (prometido, no entregado).
- **Algoritmos con nombre:** **Bellman-Ford, Floyd-Warshall, Kruskal** solo como fila de tabla (Floyd son 4 líneas de DP justo tras la Parte DP); **heap sort** en la tabla pero no enseñado; **counting/radix sort** (rompen la "barrera O(n log n)" que se menciona sin matizar que es solo para ordenamientos por comparación).

---

## 5. Hallazgos MENORES (🟡) — pulido (muestra representativa)

`\'` y `\r` faltan en escapes (§0.2.3) · división por cero int vs double `Infinity`/`NaN` (§0.4.1) · `0.1+0.2 != 0.3` y `BigDecimal` (§0.3.2) · aritmética `byte`/`short` promueve a `int` (§0.3.2) · `labeled break` (§0.5.8) · `=` vs `==` en `if` (§0.5.1) · `List.remove(int)` vs `remove(Object)` (§0.11) · `ArrayDeque` no admite `null` (§3.2) · overflow de `a-b` como comparador (varios) · `Θ`/`Ω` y espacio de recursión (§1.6) · `record`/`sealed`/clases anónimas (nota) · `@FunctionalInterface`, `BinaryOperator` (§0.15) · ejemplo `ArrayDeque` en §0.11 · encoding de consola para `○`/`□` (§0.8.6) · stack trace en una sola línea (§0.10.1) · cheat sheet "Señales→patrón" sin prefix sum / pila monótona (Parte 5) · cifra "~33 resueltos" inflada (6 son "idea"). *(Lista completa en los logs.)*

---

## 6. ¿Pasa el test de la isla desierta?

- **Para el objetivo declarado del manual (resolver y explicar en entrevista SDET):** **SÍ**, casi al 100 %. Es autosuficiente, no depende de internet, y la densidad cumple el estándar del framework en la mayoría de secciones.
- **Para la promesa literal "experto mundial solo con esto":** **TODAVÍA NO.** Dos secciones fallan la auto-suficiencia (merge/quick sort no implementables; Patrón 7 sin densidad), hay ~9 errores factuales que un experto no debe arrastrar, y faltan temas canónicos (balanceo de árboles, heapify, Bellman-Ford/Floyd/Kruskal, counting sort, Optional/Collectors, doubly linked).

**Decisión de fondo para Alberto (P12 — honestidad radical):** hay una tensión real entre la promesa de la cabecera ("experto mundial") y el alcance realista declarado en §13.K ("objetivo SDET"). Hay dos caminos legítimos:
- **(A) Subir el contenido a la promesa:** añadir todo lo de experto (camino de la Fase 3 del tracker). Más trabajo, cumple la cabecera.
- **(B) Alinear la promesa al alcance:** mantener foco SDET y matizar la cabecera. Menos trabajo, honesto.

La implementación de esta auditoría toma el camino **(A) en lo crítico/importante** y deja el resto de experto como backlog rastreado, **sin tocar la promesa** salvo que Alberto decida (B).

---

## 7. Plan de acción priorizado

1. **Fase 1 — Correcciones (🔴+🟠 de hechos/código).** Quirúrgicas, alto impacto, cero riesgo de romper lo existente. Incluye C1–C9 y los errores importantes. → *bloquea declarar el manual "correcto".*
2. **Fase 2 — Auto-suficiencia SDET (🟠 densidad).** Completar los 6 "(idea)", trazas faltantes (Patrón 7, Dijkstra, pila monótona, memo DP), Three Sum con duplicados, binaria rotado, ventana mínima.
3. **Fase 3 — Profundidad de experto.** Optional/Collectors/streams, copia defensiva, AVL/rotaciones, heapify, doubly/circular linked, Bellman-Ford/Floyd/Kruskal, counting/radix, borrados BST/Trie, Θ/Ω. *(Backlog rastreado; se implementa por tandas.)*
4. **Pulido (🟡)** en paralelo a las fases.

El avance se registra en [`2026-06-19_Tracker-implementacion.md`](2026-06-19_Tracker-implementacion.md) y, al cerrar tandas, en el changelog del propio manual (P8).

---

## 8. Lo que esta auditoría NO verificó (P12)

- **No se ejecutó el código en una JVM real** (no hay JDK confirmado en el entorno): la verificación de compilación/salida es por análisis experto del lenguaje y trazas a mano, no por compilación en máquina. Recomendado, como segundo pase, correr todos los snippets en un JDK 17+.
- Los números del *constant pool* de `javap` (§0.1.2) y la salida exacta de `javap` no se contrastaron contra una versión concreta del JDK (están etiquetados como aproximados en el texto, lo cual es correcto).
- Los órdenes de iteración de `HashMap` afirmados podrían coincidir o no con una corrida concreta — precisamente por eso son un hallazgo (C4).
