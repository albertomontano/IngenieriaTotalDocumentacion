# 🛠️ Tracker de implementación — Auditoría Manual Java/Algoritmos (2026-06-19)

> Estado de las correcciones derivadas de [`2026-06-19_Auditoria-Manual-Java-Algoritmos.md`](2026-06-19_Auditoria-Manual-Java-Algoritmos.md).
> Leyenda: ✅ hecho · 🔄 en curso · ⬜ pendiente (backlog).

## Fase 1 — Errores factuales y código roto (🔴/🟠 hechos)

| ID | Ubicación | Corrección | Estado |
|---|---|---|---|
| C1 | §0.4.7 | `>>` matiz negativos + añadir `>>>` | ⬜ |
| C2 | §0.8.1 | orden visibilidad protected/default | ⬜ |
| C3 | §0.10.4 | reescribir frase de `finalize()` | ⬜ |
| C4 | §0.11.4 / §0.11.8 | HashMap: orden no garantizado | ⬜ |
| C5 | Patrón 2 / 2.J | celda "negativos" reescrita | ⬜ |
| C6 | Patrón 10 | `fusionar` copia defensiva + tocantes | ⬜ |
| C7 | Patrón 13 | `formasEscalera` caso base | ⬜ |
| C8 | Ordenamientos 🅐🅑 | implementar `mezclar` y `particionar` | ⬜ |
| C9 | Patrón 7 | densidad: traza, bugs, complejidad, órdenes DFS | ⬜ |
| I1 | §1-B.1 | `String` interno = `byte[]` (Java 9+) | ⬜ |
| I2 | §1.7/§1.4 | `Arrays.sort(int[])` peor O(n²) | ⬜ |
| I3 | §5.7 | HashMap peor caso O(log n)/O(n) | ⬜ |
| I4 | §2.5/§10.1 | lista enlazada al final O(n) | ⬜ |
| I5 | §3.3/§4.3 | `poll()/pop()` NPE → usar Integer | ⬜ |
| I6 | Patrón 3 | `sumaMaxK` guarda k>length | ⬜ |
| I7 | Patrón 11 | salida heap no determinista | ⬜ |
| I8 | Patrón 12 | "suman K" con `put(0,1)` + código | ⬜ |
| I9 | Patrón 1 | supuesto op/s coherente | ⬜ |

## Fase 2 — Auto-suficiencia SDET (🟠 densidad)

| ID | Ubicación | Mejora | Estado |
|---|---|---|---|
| D1 | §4.3 | completar 3Sum (saltar duplicados) | ⬜ |
| D2 | §4.3 | completar Course Schedule | ⬜ |
| D3 | §4.3 | completar Permutaciones | ⬜ |
| D4 | §4.3 | completar Combination Sum | ⬜ |
| D5 | §4.3 | completar K más frecuentes + Min-Stack | ⬜ |
| D6 | Patrón 4 | código binaria en rotado | ⬜ |
| D7 | Patrón 5 | memoización in-situ (fib) | ⬜ |
| D8 | Patrón 9 | traza completa pila monótona | ⬜ |
| D9 | Patrón 13 | tabla dp completa minMonedas + centinela | ⬜ |

## Fase 3 — Profundidad de experto (backlog rastreado)

| ID | Ubicación | Mejora | Estado |
|---|---|---|---|
| E1 | §0.6.6 | traza visual de referencias | ⬜ |
| E2 | §0.8.2 | composición vs herencia | ⬜ |
| E3 | §0.8.3 | reglas de override válido | ⬜ |
| E4 | §0.9.2 | conflicto del diamante (default methods) | ⬜ |
| E5 | §0.10.4 | try-with-resources múltiple + suprimidas | ⬜ |
| E6 | §0.10.7 | encadenamiento de causas | ⬜ |
| E7 | §0.10.4 | trampa `return` en `finally` | ⬜ |
| E8 | §0.12.6 | PECS nombrado + por qué no `add` | ⬜ |
| E9 | §0.13.4 | copia defensiva en inmutabilidad | ⬜ |
| E10 | §0.13.3 | contrato completo de `equals` | ⬜ |
| E11 | §0.15 | Optional | ⬜ |
| E12 | §0.15 | Collectors (groupingBy, joining, toMap) | ⬜ |
| E13 | §0.15 | laziness demostrada + stream se consume una vez | ⬜ |
| E14 | §6.5 | AVL/rotaciones + invariantes | ⬜ |
| E15 | §7.5 | heapify O(n) + traza arreglo interno | ⬜ |
| E16 | §2.6 | doubly linked list enseñada | ⬜ |
| E17 | §6.8 | borrado en BST (sucesor inorden) | ⬜ |
| E18 | Ordenamientos | counting sort + matiz "barrera O(n log n)" | ⬜ |
| E19 | Algoritmos grafos | Bellman-Ford enseñado | ⬜ |
| E20 | Algoritmos grafos | Floyd-Warshall enseñado | ⬜ |
| E21 | Algoritmos grafos | Kruskal enseñado (reusa Union-Find) | ⬜ |
| E22 | Algoritmos grafos | topological sort por DFS | ⬜ |

## Pulido (🟡 — por tandas)

| ID | Ubicación | Mejora | Estado |
|---|---|---|---|
| P-a | §0.2.4 y 4 ejemplos | distinguir entrada de usuario vs salida | ⬜ |
| P-b | §0.3.2 | byte/short promueve a int; 0.1+0.2≠0.3 / BigDecimal | ⬜ |
| P-c | §0.4.1 | división por cero int vs double | ⬜ |
| P-d | §0.5.8 | labeled break/continue | ⬜ |
| P-e | §0.2.3 | escapes `\'` y `\r` | ⬜ |
| P-f | §1.3/§1.6 | log base 2; Θ/Ω; espacio de recursión | ⬜ |
| P-g | varios | overflow de `a-b` como comparador | ⬜ |
| P-h | Parte 5 | cheat sheet: prefix sum + pila monótona | ⬜ |
| P-i | §1.4 | O(n!) con su tratamiento | ⬜ backlog |
| P-j | §0.15.3 | @FunctionalInterface, BinaryOperator | ⬜ backlog |

## Pendiente de decisión de Alberto / segundo pase

- ⬜ **Ejecutar todos los snippets en un JDK 17+ real** (la auditoría verificó por análisis experto + trazas, no por compilación en máquina).
- ⬜ Huecos de experto opcionales: KMP/Rabin-Karp, radix sort, Fenwick/segment tree, B-tree/skip list/bloom filter/LRU, ventana mínima (Map de conteos), borrado en Trie, DFS iterativo en grafos, mediana con dos heaps. *Decidir si entran (camino A) o se alinea la promesa al alcance SDET (camino B).*
