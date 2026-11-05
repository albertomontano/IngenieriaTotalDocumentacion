# Logs crudos — Auditoría Manual Java/Algoritmos (2026-06-19)

> Salida verbatim de los 7 agentes auditores que recorrieron el manual en paralelo.
> Síntesis y plan de acción en [`../2026-06-19_Auditoria-Manual-Java-Algoritmos.md`](../2026-06-19_Auditoria-Manual-Java-Algoritmos.md).
> Cada agente recibió la misma rúbrica adversarial (test de la isla desierta P3 + estándar de densidad §3 + verificación de hechos P4) sobre un rango de líneas distinto.

---

## logs#1 — Preliminar + Java §0.0–0.5 (líneas 51–1188) · agente a3cf9253119a3113b

Veredicto: isla desierta **PARCIAL→Sí** · **8.5/10**

Hallazgos clave:
- 🟡 PRELIMINAR usa términos no definidos (Big-O, HashMap, ventana, log n) ante principiante absoluto → añadir nota "es vistazo de motivación, todo se enseña desde cero".
- 🟠 §0.0.2 primer código `Perro` ejecutable antes de explicar nombre de archivo (§0.2.1) → añadir `// archivo: Perro.java`.
- 🟠 §0.2.4 (y §0.2.7 Ej.3/6, §0.4.9 Ej.2, §0.5.9 Ej.6): la "salida" mezcla la entrada del usuario (eco del terminal) con lo que imprime el programa → distinguir visualmente lo tecleado. Afecta 5 ejemplos con Scanner.
- 🟠 §0.2.4 bug `nextInt()`+`nextLine()` mencionado pero no demostrado con su síntoma.
- 🔴 §0.4.7 bitwise: `>>` presentado como "÷2" (incorrecto para negativos: `-3>>1=-2`) y **falta `>>>`** (uso canónico `mid=(lo+hi)>>>1` anti-overflow). **La corrección más importante del tramo.**
- 🟠 §0.3.2 aritmética `byte`/`short` se promueve a `int` (`byte c=a+b;` no compila) — no advertido.
- 🟡 §0.4.2 y §0.4.4 sin bloque "// Salida:" unificado (inconsistencia de formato).
- 🟡 §0.5.8 falta `labeled break/continue` para bucles anidados.
- 🟡 §0.5.1 falta error `=` vs `==`.
- 🟡 huecos: división por cero (int→excepción, double→Infinity/NaN); precisión de `double` (`0.1+0.2≠0.3`, BigDecimal); `\'` y `\r` en escapes.
- ✅ Verificados correctos: historia de Java, JVM/JRE/JDK/GC (sección sobresaliente), overflow int (-2147483648), caché de Integer (true/false/true), `5/2=2`/`5.0/2=2.5`/`(char)('A'+1)=B`, todos los bucles y FizzBuzz, suma 1..100=5050.

---

## logs#2 — Java §0.6–0.10 (líneas 1189–2240) · agente a021df1d579f258ff

Veredicto: isla desierta **PARCIAL** · **6.5/10**

Hallazgos clave:
- 🔴 §0.8.1 tabla de modificadores: orden "de más a menos abierto: public→protected→default→private" **INVERTIDO**. `protected` (paquete + subclases) es MÁS abierto que default (solo paquete).
- 🟠 §0.8.1 fila `protected` imprecisa: acceso desde subclase en otro paquete está restringido (solo vía referencias del propio tipo).
- 🔴 §0.10.4 "try-with-resources reemplaza al obsoleto `finalize()`" — falso: cierre determinista ≠ ciclo de vida del GC. Además `finalize` aparece sin haberse explicado.
- 🟠 §0.10.4 falta: try-with-resources **múltiple** (cierre en orden inverso) y **excepciones suprimidas** (`getSuppressed()`).
- 🟠 §0.10.4 `finally`: falta la trampa de `return`/`throw` dentro de `finally` (anula el del try).
- 🟠 §0.10.7/8 falta **encadenamiento de causas** (`new X("...", e)`, `getCause()`, "Caused by:").
- 🟠 §0.8.2 falta **composición vs herencia**.
- 🟠 §0.8.3 polimorfismo: falta estático vs dinámico, upcast/downcast, `instanceof`, `ClassCastException` (que se cita luego sin mostrar).
- 🟠 §0.8.3 tabla override: reglas reales faltantes (retorno covariante, acceso no se reduce, no override de private/static/final, excepciones checked no se amplían).
- 🟠 §0.9.2.1 faltan métodos `private` de interfaz (Java 9+) y **conflicto del diamante** (`Interfaz.super.metodo()`).
- 🟠 §0.6.6 falta traza visual de referencias (modificar vs reasignar) — el punto más resbaladizo, sin el diagrama que el resto sí tiene.
- 🟠 §0.7.3-4 nunca se explican los valores por defecto de campos (0/false/null) vs locales (obligatorio inicializar); el ejemplo `Coche` imprime `velocidad=0` sin explicar por qué.
- 🟡 §0.8.4 Abstracción: único pilar sin programa completo con salida (rompe la promesa de línea 1619).
- 🟡 §0.6 falta caja de "errores comunes" (missing return, non-static from static context).
- 🟡 §0.6.7 varargs: faltan reglas (debe ir último; solo uno por método).
- 🟡 §0.10.5 diagrama: "checked" parece una clase; checked = Exception − RuntimeException.
- 🟡 §0.10.12 Ej.1 usa Scanner con close() manual (antipatrón que el propio cap. desaconseja).
- 🟡 huecos: `record` (16+), `sealed` (17+), clases anónimas/internas.
- ✅ Verificados: toString `velocidad=0`, área triángulo 6.0, `retirar(150)`→`Faltan $50.0`.

---

## logs#3 — Java §0.11–0.15 (líneas 2241–3028) · agente a83f39220f1774deb

Veredicto: isla desierta **PARCIAL** · **6.5/10**

Hallazgos clave:
- 🔴 §0.11.4 salida de `entrySet()` de HashMap presentada como orden fijo (`manzanas=60`/`peras=30`) → HashMap no garantiza orden; contradice §0.11.1/6.
- 🔴 §0.11.8 Ej.1 `{a=3, b=1, c=1}` mismo problema (orden de HashMap no garantizado).
- 🟠 §0.12.6 wildcards: falta nombrar **PECS** y mostrar por qué `add` no compila sobre `? extends`.
- 🟠 §0.12.7 type erasure: `instanceof List<?>` y `instanceof List` SÍ valen (matiz); falta choque de firmas por erasure.
- 🟠 §0.13.3 contrato de `equals` incompleto (faltan 5 propiedades + simetría/herencia, `instanceof` vs `getClass`).
- 🟠 §0.13.4 inmutabilidad: falta **copia defensiva** (final ≠ inmutable para objetos mutables).
- 🟠 §0.13.5 Comparator: doble `sort` consecutivo confunde sobre qué salida produce cada línea.
- 🟠 §0.15 falta **Optional** (retorno de reduce/findFirst/max/min); falta `IntStream`/`mapToInt().sum()`.
- 🟠 §0.15 falta **Collectors** (groupingBy, joining, toMap, counting, partitioningBy).
- 🟠 §0.15 *laziness* afirmada pero no demostrada (falta peek/traza).
- 🟠 §0.15 faltan parallel streams, "stream se consume una vez" (IllegalStateException), no-interferencia.
- 🟡 §0.11.1 "List → ordenada" ambiguo (orden de inserción ≠ ordenada numéricamente).
- 🟡 §0.11 trampa `List.remove(int)` vs `remove(Object)`.
- 🟡 §0.11.6 recomienda ArrayDeque sin ningún ejemplo de código.
- 🟡 overflow de `(a,b)->a-b` como comparador (§0.13.5/§0.15).
- 🟡 §0.13.6 import comodín `*` sin nota de buenas prácticas.
- 🟡 §0.14.3 `assertEquals` usa `Objects.equals` (null-safe), no literalmente `.equals()`.
- 🟡 §0.15.3 falta `BinaryOperator` (usado en reduce), `@FunctionalInterface`.
- ✅ Verificados: ConcurrentModificationException + Iterator.remove() bien tratados; type erasure básico; enum Marte 259.7; streams ej.1 (2) y ej.2 ([KIWI,MANZANA,PERA,UVA]) correctos.

---

## logs#4 — Big-O + Estructuras de datos (líneas 3029–4660) · agente a309f265af7d4b6c8

Veredicto: isla desierta **PARCIAL** · **7.5/10**

Hallazgos clave:
- ✅ (falso positivo registrado por honestidad) Las 24 celdas de la tabla §1.3 de tiempos Big-O son **correctas** tras recálculo.
- 🟠 §1.4 falta dar a O(n!) el mismo tratamiento (analogía + código) que las otras seis; inconsistencia "siete complejidades".
- 🟡 §1.3 nunca dice explícitamente "logaritmo base 2" ni que la base es irrelevante en Big-O.
- 🟡 §1.6 no cuenta el espacio de la **pila de recursión** O(profundidad).
- 🟡 §1.2/1.8 no distingue Big-O (cota superior) de Θ/Ω.
- 🟠 §1.7/§1.4 `Arrays.sort(int[])` = Dual-Pivot Quicksort → **peor O(n²)**; solo objetos (TimSort) garantizan O(n log n) estable.
- 🟠 §1-B.1 `String` interno desde Java 9 = `byte[]` + coder, no `char[]`.
- 🟡 §1-B.3 `+=` en bucle O(n²): aclarar que aplica a concatenación iterativa, no a `a+b+c` en una expresión.
- 🟡 §1-B.5 truco `c-'a'` asume minúsculas a-z (AIOOBE con mayúsculas/acentos).
- 🟠 §2.5.d + tabla §10.1: lista enlazada simple insertar/borrar **al final es O(n)**, no O(1); contradice §2.5.c.
- 🟠 §2.6 doubly/circular linked list mencionadas pero no enseñadas (nodo prev/next, inserción/borrado, traza).
- 🟡 §2.9 detección de ciclo (Floyd) y nodo medio sin código ni traza.
- 🟡 §3.2 `ArrayDeque` no admite null (NPE).
- 🟠 §4.3 `int x = cola.poll();` → NPE por autounboxing vs "null si vacía".
- 🟠 §5.7 contradicción HashMap: tras treeificar, peor caso O(log n) (si claves Comparable), no O(n) liso.
- 🟡 §5.7 falta traza de cubetas/colisiones con números.
- 🟠 §6.5 AVL/Red-Black solo nombrados (falta rotación, invariantes, por qué O(log n)).
- 🟡 §6.8 falta espacio de recorridos (DFS O(h), BFS O(n)) e inserción/borrado en BST (sucesor inorden, 3 casos).
- 🟠 §7.5 falta **heapify O(n)** (`new PriorityQueue<>(coleccion)`); traza del arreglo interno del heap (la notación `{1,3,5}` engaña, el heap no está ordenado).
- 🟡 §8.4 DFS recursivo puede dar StackOverflow; falta versión iterativa.
- 🟡 §9.5 falta espacio del trie; borrado en trie no enseñado.
- 🟠 tabla §10.1: corregir lista enlazada, HashMap peor caso, aclarar que fila Grafo es lista de adyacencia, falta columna de espacio y fila árbol degenerado.
- 🟡 huecos: counting/radix sort, Union-Find/Fenwick/segment tree/B-tree/skip list/bloom/LRU (algunos en Parte 3).
- ✅ Verificados: acceso O(1) por fórmula; defaults de arreglos; inorden BST (1 3 6 8 10 14); BFS niveles (8 3 10 1 6 14); paréntesis balanceados; kMayor=5; índices de heap 2i+1/2i+2/(i-1)/2; Dijkstra O((V+E)log V); BFS grafo (1 2 3 4); trie. Todo Java 9+ (Map.of/List.of) — declarar versión mínima una vez.

---

## logs#5 — Patrones 1–7 (líneas 4661–5921) · agente a44b47e90045a07e2

Veredicto: isla desierta **PARCIAL** · **8.0/10** (Patrón 7 aislado ~7; cuerpo 1–6 calidad de libro)

Hallazgos clave:
- 🔴 Patrón 2, tabla 2.J "Negativos" (`[-3,-1,2,5]` obj 1): anotación rota/engañosa "-1+… no; -3+…"; el resultado `[1,2]` es correcto (`-1+2=1`) pero el texto sugiere que falla. Reescribir limpia.
- 🟠 Patrón 3 `sumaMaxK` revienta con `k>arr.length` (AIOOBE) pese a que 3.K dice manejarlo → añadir guarda.
- 🔴 Patrón 7 (árboles): sin traza paso a paso, sin bugs, sin complejidad derivada, sin casos borde, sin los 3 órdenes DFS → es referencia, no lección.
- 🟠 Patrón 7 inconsistencia "validar BST = inorden ordenado" (estricto en P2, "ordenado" en 7.C) + bug `prev=Integer.MIN_VALUE`.
- 🟠 Patrón 7 plantilla DFS sin mostrar pre/in/post-orden; clase `Nodo` usada sin definir aquí.
- 🟠 Patrón 2 Three Sum sin código ni el detalle de **saltar duplicados**.
- 🟠 Patrón 4 variantes "rotado" y "binaria sobre la respuesta" sin código.
- 🟠 Patrón 3 falta ventana variable con **Map de conteos** (Minimum Window Substring).
- 🟠 Patrón 5 falta mostrar el código de **memoización** in-situ (se promete y se difiere a Patrón 13).
- 🟠 Patrón 6 faltan duplicados en backtracking y ejemplo concreto de poda.
- 🟡 Patrón 1 "O(n²) n=10⁶ ≈ 11.5 días" inconsistente con supuesto de op/s.
- 🟡 Patrón 1 variante "agrupar anagramas" sin código.
- 🟡 Patrón 5 `invertir` con substring(1) es O(n²) no advertido; factorial desborda int en 13!.
- 🟡 casos borde desaparecen en Patrones 5/6/7; densidad decae.
- ✅ **Trazas verificadas a mano todas correctas:** Two Sum [2,3]; mover ceros [1,3,12,0,0]; ventana "abcabcbb" celda por celda; binaria casos A(73) y B(50); factorial(4); suma; invertir; fib(5) árbol; subconjuntos (8 resultados exactos); permutaciones (orden exacto del comentario). Patrón 4 (binaria) es **ejemplar** (overflow, `<=` vs `<`, ±1).

---

## logs#6 — Patrones 8–13 + algoritmos con nombre (líneas 5922–6647) · agente a30698dd5074da275

Veredicto: isla desierta **PARCIAL (→No en 2 puntos)** · **7.0/10**

Hallazgos clave:
- 🔴 **C8** Ordenamientos: `mezclar()` (merge) y `particionar()` (quick) **NO existen** (solo comentario) → merge sort y quicksort no implementables. El hueco más grave.
- 🔴 Patrón 10 `fusionar`: bug de **aliasing** (`res.add(cur)` muta el input) → copiar el arreglo; advertir intervalos que se tocan.
- 🔴 Patrón 13 `formasEscalera`: caso base `formas(0)` inconsistente (devuelve 0, debe ser 1); `return n` mezcla convenciones.
- 🟠 Patrón 8 islas: sin traza, sin guarda `grid.length==0`, sin derivar O(m·n), sin advertir StackOverflow del DFS.
- 🟠 Patrón 9 pila monótona: traza solo muestra i=1 (falta el paso instructivo i=6 donde se vacía la pila). Resultado `[1,1,4,2,1,1,0,0]` verificado correcto.
- 🟠 Patrón 11 `kMasFrecuentes`: salida `[2,1]` presentada como determinista (orden interno del heap no garantizado); falta extracción y complejidad O(n+m log k).
- 🟠 Patrón 12 "subarreglos suman K" sin código y **sin `map.put(0,1)`** (off-by-one).
- 🟠 Patrón 13 top-down sin traza de memo; usa problemas distintos (fib vs escalera).
- 🟠 Patrón 13 `minMonedas` sin tabla dp[0..11] llena, sin explicar centinela `c+1`, sin unbounded vs 0/1. (Código correcto, dp[11]=3.)
- 🟠 Dijkstra sin traza numérica con grafo concreto.
- 🟠 Topological sort: solo Kahn; la variante DFS se promete varias veces y no se entrega.
- 🟠 Bellman-Ford/Floyd-Warshall/Kruskal solo como fila de tabla (Floyd = 4 líneas de DP).
- 🟡 Patrón 9 caso valores iguales (`>` estricto) no explicado.
- 🟡 comparador `a[0]-b[0]` overflow.
- 🟡 Patrón 11 mediana de flujo (dos heaps) solo mencionada.
- 🟡 Patrón 13 O(n!) impreciso (DP bitmask es O(2ⁿ·n), no polinomial).
- 🟡 heap sort en tabla pero no enseñado; burbuja O(n) solo con bandera; quicksort espacio O(n) peor caso.
- 🟡 Union-Find rank ≠ altura exacta tras compresión.
- 🟡 KMP/Rabin-Karp, counting/radix sort ausentes; matizar que "barrera O(n log n)" es solo para ordenamientos por comparación.
- ✅ Verificados correctos: prefix sum ([0,2,6,12,20], rangos 10 y 20); fusionar (resultado correcto pese al aliasing); formasEscalera(5)=8; minMonedas=3; temperaturas=[1,1,4,2,1,1,0,0]; Dijkstra (lazy deletion, relajación, por qué no negativos); Kahn (detección de ciclo); Union-Find (compresión + unión por rango); tabla de shortest-path y de ordenamientos factualmente correctas.

---

## logs#7 — Banco + referencia + apéndice (líneas 6648–7884) · agente a5c75d8f69cc51f84

Veredicto: isla desierta **SÍ (parcial-alto)** · **8.5/10**

Hallazgos clave:
- 🔴 (evaluación, no defecto) Parte 6 (recursos externos): correctamente marcada como complemento prescindible → **el manual NO depende de internet para aprender**. No hay violación de la promesa.
- 🟠 §4.3 6 problemas "(idea)" sin código completo: **3Sum** (falta saltar duplicados), **Course Schedule**, **Permutaciones**, **Combination Sum**, **K más frecuentes** (sin extracción), **Min-Stack** (parcial). El §4.3 promete "código con traza y Big-O" para cada uno.
- 🟠 "Buscar mínimo en rotado": correcto sin duplicados; falla/degrada a O(n) con duplicados (LeetCode 154) — no advertido.
- 🟠 B5 BST: no aclara duplicados; el validador (§4.3) asume claves únicas (usa `<`/`>` estrictos).
- 🟡 "Mover ceros": swap funciona, comentario menor.
- 🟡 "K más frecuentes": completar extracción + `Integer.compare`.
- 🟡 "Nodo medio": para palíndromo conviene el primer central (`rapido=cabeza.siguiente`).
- 🟡 cifra "~33 resueltos" inflada (6 son idea).
- 🟡 cheat sheet "Señales→patrón" sin prefix sum ni pila monótona.
- ✅ **Verificados correctos (~27 problemas):** invertir string, FizzBuzz, palíndromo, Kadane=6, Two Sum, duplicados, anagramas, substring sin repetir, comprar/vender=5, binaria, invertir lista, ciclo Floyd, fusionar listas, paréntesis, min-stack, temperaturas=[1,1,4,2,1,1,0,0], profundidad, invertir árbol, level-order, validar BST (con long anti-overflow), árboles iguales, islas, k-ésimo=5, subconjuntos, climbing stairs=8, coin change=3, house robber=12. Tabla de costos de Parte 5 correcta. Registro y apéndice coherentes con el contenido.
