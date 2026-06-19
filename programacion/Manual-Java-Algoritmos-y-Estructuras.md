# 📗 MANUAL INTENSIVO SDET — ALGORITMOS Y ESTRUCTURAS DE DATOS
## De no entender nada a resolver y explicar en entrevista
### Volumen I-A · El manual de la isla desierta

---

> **Promesa de este documento.** Si lo único que tuvieras para estudiar algoritmos fuera este archivo impreso, sería suficiente. No asume que sabes Big-O (de hecho asume que nunca lo entendiste). No menciona conceptos: los **enseña**, despacio, con números concretos, varias analogías por idea, código que puedes correr, trazas paso a paso de qué pasa en memoria, encuadre de entrevista, y un banco grande de preguntas con respuestas resueltas al final.
>
> **Cómo leerlo.** Despacio y con las manos. Escribe el código, córrelo, cámbiale números, rómpelo. Un algoritmo no se entiende leyéndolo: se entiende **trazándolo a mano** una vez. Hay cajas "✍️ Traza a mano" justo para eso.
>
> **Idioma:** Java para el código (tu base). Los conceptos son idénticos en cualquier lenguaje.
>
> **Dónde encaja este documento.** Es el **companion de profundidad** del *track de carrera* `Guía-Estudio-Entrevistas-SDET-2026.md` (raíz del repo): su **Apéndice A — Playbook de Algoritmos** es el mapa de los ~15 patrones; este manual es donde cada patrón se *enseña* a fondo. Si vienes del playbook buscando profundidad, llegaste al lugar correcto. Ver también el [Índice Maestro](../INDICE-MAESTRO.md).

---

## Índice

**PRELIMINAR — Mentalidad de entrevista y mapa de aprendizaje**
- M.1 Por qué los algoritmos deciden tu entrevista · M.2 El ritual de 7 pasos · M.3 Cómo hablar mientras resuelves · M.4 Mapa de dependencias de aprendizaje

**CAPÍTULO 0 — JAVA DESDE CERO** *(la base de todo; empieza aquí si nunca has programado)*
- 0.0 ¿Qué es Java? · 0.1 La plataforma: JVM, JDK, JRE y bytecode · 0.2 Tu primer programa (compilar y ejecutar) · 0.3 Variables y tipos de datos
- 0.4 Operadores · 0.5 Estructuras de control (condicionales y bucles) · 0.6 Métodos
- 0.7 POO: clases y objetos · 0.8 Los 4 pilares de la POO (encapsulación, herencia, polimorfismo, abstracción) · 0.9 Interfaces y clases abstractas
- 0.10 Excepciones (manejo de errores) · 0.11 Colecciones (List, Set, Map) · 0.12 Genéricos · 0.13 Esenciales (static, enums, equals/hashCode…) · 0.14 Java aplicado a frameworks de prueba (SDET) · 0.15 Lambdas y Streams

**PARTE 1 — BIG-O DESDE CERO ABSOLUTO** *(el corazón del razonamiento de eficiencia)*
- 1.1 El problema que Big-O resuelve · 1.2 No contamos segundos: contamos pasos · 1.3 La tabla que lo cambia todo · 1.4 Las siete complejidades una por una · 1.5 Las tres reglas para calcular Big-O · 1.6 Complejidad de espacio · 1.7 Leer la Big-O de un código · 1.8 Preguntas de Big-O resueltas

**PARTE 2 — ESTRUCTURAS DE DATOS A FONDO** *(cada una desde cero: declarar, usar, internals, práctica)*
- 1. Arreglos · 1-B. Strings · 2. Listas enlazadas · 3. Pilas · 4. Colas · 5. Tablas hash *(clave)* · 6. Árboles · 7. Heaps · 8. Grafos · 9. Tries · 10. Tabla comparativa y guía de elección

**PARTE 3 — LOS PATRONES Y ALGORITMOS** *(cómo reconocer y CONSTRUIR cada algoritmo)*
- 3.0 Framework universal · Patrones 1–13: Hashing · Dos punteros · Ventana deslizante · Búsqueda binaria · Recursión · Backtracking · Árboles (DFS/BFS) · Grafos · Pila monótona · Intervalos · Top-K (heap) · Prefix sum · Programación dinámica
- 🔢 Algoritmos clásicos con nombre (ordenamientos: merge sort, quicksort y comparativa)
- 🕸️ Algoritmos de grafos con nombre (Dijkstra, orden topológico, Union-Find y referencia de otros)

**PARTE 4 — BANCO DE PREGUNTAS (estilo tutor)**
- 4.1 Fundamentos y Big-O · 4.2 Estructuras de datos (conceptuales) · 4.3 Problemas de código por patrón (~33 resueltos) · 4.4 Preguntas verbales / de comunicación

**PARTE 5 — HOJAS DE REFERENCIA RÁPIDA**

**PARTE 6 — RECURSOS DE REFERENCIA POR TEMA** *(links curados; útiles cuando tengas internet)*

**APÉNDICE — Cómo se construyó este manual** *(guía para futuros agentes y editores: filosofía, marco pedagógico, estilo, método iterativo, pipeline técnico y playbook reutilizable para manuales de otros temas)*

---
---

# PRELIMINAR — MENTALIDAD DE ENTREVISTA Y MAPA DE APRENDIZAJE

## M.1 Por qué los algoritmos deciden tu entrevista

En tus palabras: el 80% de tus entrevistas técnicas tuvieron ejercicios de algoritmos y es lo que más te ha costado. No es casualidad ni mala suerte. Las empresas usan algoritmos como filtro por una razón concreta: **un problema de algoritmos revela en 30 minutos si sabes descomponer un problema, elegir la herramienta correcta, escribir código correcto y razonar sobre su eficiencia** — justo lo que hace un buen ingeniero. No les importa si memorizaste la solución; les importa **ver cómo piensas**.

La buena noticia, y quiero que la creas porque cambia todo: **no necesitas ser un genio ni resolver 500 problemas.** La gente que "es buena en algoritmos" no improvisa: **reconoce un patrón** que ya practicó y aplica una plantilla. Hay alrededor de 15 patrones. Cuando los dominas, la mayoría de los problemas dejan de ser página en blanco y se vuelven "ah, esto es ventana deslizante". Este manual te lleva ahí.

## M.2 El ritual de 7 pasos para cualquier problema

Memoriza esto. No es decoración: es exactamente lo que harás en la entrevista, en voz alta, y es lo que te va a salvar cuando te bloquees.

1. **Reformula el problema con tus palabras.** "Entonces, me das un arreglo de números y quiero encontrar dos que sumen un objetivo, ¿correcto?". Esto confirma que entendiste y te da segundos para pensar.
2. **Pregunta supuestos en voz alta.** ¿La entrada puede estar vacía? ¿Puede haber números repetidos? ¿Negativos? ¿Ya viene ordenada? ¿Qué devuelvo si no hay solución? — *Solo este paso ya te distingue: demuestra mentalidad de calidad, que es tu súper-poder de QA.*
3. **Plantea la fuerza bruta primero, y di su Big-O.** Siempre existe una solución obvia (aunque sea lenta). Nunca te quedes callado: "lo más directo es comparar todos los pares, eso es O(n²)…". Tener *algo* es infinitamente mejor que tener nada.
4. **Busca el cuello de botella y optimiza.** "Ese segundo bucle es el problema. ¿Puedo recordar lo que ya vi con un Map y evitarlo?". Aquí entran los patrones.
5. **Codifica limpio, narrando.** Habla mientras escribes. El entrevistador evalúa tu razonamiento tanto como tu código.
6. **Prueba con casos borde.** Vacío, un solo elemento, duplicados, el valor máximo, negativos. Encontrar tus propios bugs impresiona.
7. **Da la complejidad final** de tiempo **y** espacio.

> 🔑 **Clave de entrevista:** un candidato que hace fuerza bruta → identifica el cuello de botella → propone la optimización → maneja casos borde, **gana aunque no termine de compilar el código**. Uno que se lanza a teclear en silencio y se traba, **pierde aunque casi lo logre**. La entrevista de algoritmos es un examen de *pensamiento verbalizado*, no de mecanografía.

## M.3 Cómo hablar mientras resuelves

Frases que debes tener listas (te dan tiempo y te hacen ver senior):
- "Déjame aclarar un par de supuestos antes de empezar…"
- "La solución ingenua sería… y su costo es O(…). Veamos si podemos mejorar."
- "El cuello de botella es este bucle anidado. Si uso un HashMap puedo cambiar tiempo por espacio…"
- "Voy a trazar un ejemplo pequeño para validar mi lógica: con la entrada [2,7,11,15]…"
- "Casos borde que debo manejar: arreglo vacío, un elemento, duplicados…"

El silencio es tu enemigo. Pensar en voz alta es la habilidad que más sube tu calificación.

---
---

## M.4 Mapa de dependencias de aprendizaje (LÉELO ANTES DE EMPEZAR)

> Esta es una de las cosas que más confunde a quien estudia algoritmos por su cuenta: **intentar aprender grafos antes de entender pilas y colas, o intentar backtracking sin dominar recursión.** Es como querer correr antes de gatear. Aquí está el orden correcto. Cada tema lista de qué **depende** (qué debes dominar *antes*). No te saltes la cadena.

🏠 **Analogía:** aprender algoritmos es como construir una casa. No puedes poner el techo (grafos, DP) antes que los cimientos (Big-O, arreglos) y las paredes (recursión, pilas). Si algo "no te entra", casi siempre es porque te saltaste un ladrillo de abajo. Cuando te atores, **baja un nivel** en esta escalera.

**La escalera de dependencias (de abajo hacia arriba):**

```
NIVEL 5  ┌─ Programación dinámica ──── depende de: recursión + arreglos
         │  Backtracking ───────────── depende de: recursión + pilas (call stack)
         │  Grafos (BFS/DFS) ────────── depende de: colas + pilas + recursión + hash sets
NIVEL 4  ├─ Árboles (DFS/BFS) ───────── depende de: recursión + colas + pilas
         │  Heaps / Top-K ───────────── depende de: árboles + arreglos
NIVEL 3  ├─ Recursión ───────────────── depende de: funciones + la pila de llamadas
         │  Pilas y Colas ───────────── depende de: arreglos o listas enlazadas
         │  Ventana deslizante ──────── depende de: dos punteros + hash sets
         │  Búsqueda binaria ────────── depende de: arreglos ordenados + Big-O (log n)
NIVEL 2  ├─ Hashing (Map/Set) ───────── depende de: arreglos + la idea de O(1)
         │  Dos punteros ────────────── depende de: arreglos + bucles
NIVEL 1  ├─ Arreglos y strings ──────── depende de: variables, bucles, índices
         │  Big-O ───────────────────── depende de: bucles (saber contar pasos)
NIVEL 0  └─ Fundamentos: variables, tipos, bucles, condicionales, funciones
```

**Cómo usar este mapa:**
1. **Estudia de abajo hacia arriba.** Asegúrate de dominar cada nivel antes de subir.
2. **Cuando te atores en un tema, mira de qué depende y regresa a reforzar eso.** El 90% de los bloqueos en grafos son en realidad debilidad en pilas/colas/recursión.
3. **Las "Dependencias de aprendizaje"** aparecen al inicio de cada patrón en la Parte 3, para que sepas exactamente qué repasar si algo no cuaja.

> 🔑 **Clave mental:** un algoritmo "difícil" casi nunca es difícil por sí mismo — es difícil porque se apoya en 3 o 4 ideas más simples que no terminaste de dominar. Aísla esas ideas, domínalas por separado, y el algoritmo "difícil" se vuelve obvio.

---
# CAPÍTULO 0 — JAVA DESDE CERO (la base de todo el manual)

> 🔗 **Dependencias de aprendizaje:** **ninguna.** Este es el verdadero punto de partida (el "Nivel 0" del mapa de aprendizaje). Si nunca has programado, **empieza aquí**. Todo lo demás del manual (Big-O, estructuras, algoritmos) usa el código que aprenderás en este capítulo.
>
> 📌 **Cómo está organizado:** del concepto más básico (¿qué es Java? ¿cómo corre un programa?) a la Programación Orientada a Objetos completa, con la misma profundidad que el resto del manual: analogías 🏠, claves 🔑, trampas ⚠️, ejemplos que puedes correr, y cómo cada cosa **se aplica a frameworks de prueba (SDET)**. Numeración anidada (0.0, 0.1, 0.2.1…) para que ubiques cualquier subtema.
>
> 🧪 **Nota SDET/QA:** Java es la base de los frameworks de automatización más usados (Selenium, Playwright para Java, RestAssured, JUnit, TestNG). Dominar Java no es "extra" para un SDET: **es el idioma en el que escribirás tus pruebas**.

---

## 0.0 ¿Qué es Java? (y por qué es la base de tu carrera)

**Java** es un **lenguaje de programación**: un idioma con reglas estrictas que usas para darle instrucciones a una computadora. Fue creado por James Gosling en Sun Microsystems (hoy de Oracle) y publicado en **1995**. Décadas después sigue siendo uno de los lenguajes más usados del planeta — en banca, sistemas empresariales, Android, *big data* y, lo que más te interesa, **automatización de pruebas**.

🏠 **Analogía:** un lenguaje de programación es una receta de cocina **extremadamente** estricta. La computadora es un cocinero obediente y literal: hace **exactamente** lo que dice la receta, sin interpretar ni adivinar. Si olvidas un punto y coma, la receta entera no corre. Java es una receta especialmente ordenada y exigente — esa rigidez molesta al inicio, pero es justo lo que lo hace confiable para sistemas enormes donde un error cuesta millones.

### 0.0.1 ¿Por qué Java es "compilado e interpretado" a la vez?

La mayoría de los lenguajes son **o** compilados (se traducen una vez a código de máquina, como C) **o** interpretados (se traducen línea por línea al correr, como Python clásico). Java es un **híbrido**, y entender esto te explica casi todo lo demás:

1. **Se compila** una vez con `javac` a un formato intermedio llamado **bytecode** (no a código de máquina de tu procesador).
2. Ese bytecode lo **ejecuta** (interpreta y optimiza) la **JVM** en cualquier sistema.

🔑 Ese diseño es la razón del lema **"write once, run anywhere"** ("escríbelo una vez, córrelo donde sea"): el mismo bytecode corre en Windows, Mac y Linux sin reescribirlo. Lo verás a fondo en §0.1.

### 0.0.2 Los rasgos de Java, con código que lo demuestra

No memorices la lista: **velos funcionando**.

**Rasgo 1 — Orientado a objetos.** Java organiza todo en **objetos** (cosas con datos y comportamientos). No hay código "suelto"; todo vive dentro de clases. Un programa completo que lo muestra:
```java
public class Perro {
    String nombre;                              // dato (estado)
    void ladrar() {                             // comportamiento
        System.out.println(nombre + " dice: ¡Guau!");
    }
    public static void main(String[] args) {
        Perro p = new Perro();                  // creamos un objeto
        p.nombre = "Firulais";
        p.ladrar();
    }
}
// Salida:
// Firulais dice: ¡Guau!
```
Lo verás a fondo en §0.7–§0.9. Por ahora, fíjate: los datos (`nombre`) y la acción (`ladrar`) viven **juntos** en el objeto.

**Rasgo 2 — Fuertemente y estáticamente tipado.** Cada variable tiene un **tipo** fijo, declarado, y el **compilador** revisa los tipos **antes** de ejecutar. Esto atrapa errores tempranísimo:
```java
public class Tipos {
    public static void main(String[] args) {
        int edad = 30;
        edad = "treinta";   // ❌ ERROR DE COMPILACIÓN: no compila siquiera
    }
}
// El compilador (javac) dice:
// error: incompatible types: String cannot be converted to int
```
🔑 **Por qué esto es bueno:** en un lenguaje no tipado, ese error explotaría **en producción** frente al usuario. En Java explota en tu pantalla, al compilar, cuando es barato arreglarlo. La rigidez es una **red de seguridad**.

**Rasgo 3 — Portable (gracias al bytecode).** El mismo archivo `.class` compilado corre en cualquier sistema con una JVM. No recompilas para cada sistema operativo. (§0.1.)

**Rasgo 4 — Gestión automática de memoria (garbage collector).** En C/C++ tú reservas y **liberas** memoria a mano; si olvidas liberar, hay *fugas*; si liberas dos veces, hay *crashes*. Java trae un **recolector de basura** que libera automáticamente la memoria de los objetos que ya nadie usa. Menos errores, menos control fino. (Lo explico a fondo en §0.1.6 — fue uno de los huecos del manual y aquí queda cubierto.)

**Rasgo 5 — Robusto y seguro.** Sin punteros crudos (no puedes corromper memoria arbitraria como en C), con verificación de bytecode antes de ejecutar, y manejo de errores estructurado mediante **excepciones** (§0.10).

**Rasgo 6 — Multihilo.** Soporta ejecutar varias tareas en paralelo (hilos) de forma nativa. (Tema avanzado; no lo necesitas para entrevistas de algoritmos, pero conviene saber que existe.)

### 0.0.3 ¿Dónde se usa Java? (y por qué te conviene)

- **Sistemas empresariales y banca** — backends grandes con Spring/Jakarta EE. Estabilidad y mantenibilidad.
- **Android** — históricamente el lenguaje principal de apps Android (hoy compartido con Kotlin, que corre en la misma JVM).
- **Big data** — Hadoop, Kafka, Spark están escritos en Java/JVM.
- **Automatización de pruebas (lo tuyo) 🧪** — Selenium WebDriver, RestAssured, JUnit, TestNG, Appium. La mayoría de las vacantes de SDET piden Java porque el ecosistema de automatización vive ahí.

### 0.0.4 Versiones de Java (sale en entrevistas)

Java evoluciona en versiones. Las **LTS** (*Long-Term Support*, soporte largo) son las que las empresas usan: **Java 8** (introdujo lambdas y streams, aún muy común), **Java 11**, **Java 17** y **Java 21**. 🔑 Si te preguntan "¿qué versión usas?", menciona una LTS reciente (17 o 21) y que conoces las novedades clave de Java 8 (lambdas/streams). Para aprender, cualquier JDK 17+ te sirve.

### 0.0.5 Ejercicios resueltos

**Ejercicio 1.** Explica en una frase de entrevista qué es Java.
> *Solución:* "Java es un lenguaje orientado a objetos, fuerte y estáticamente tipado, y portable: compila a bytecode que ejecuta la JVM en cualquier sistema, con gestión automática de memoria."

**Ejercicio 2.** ¿Por qué se dice que Java es "compilado e interpretado"?
> *Solución:* Se **compila** una vez a bytecode con `javac`, y ese bytecode lo **ejecuta** (interpreta y optimiza con JIT) la JVM en cada sistema. Híbrido de ambos mundos.

**Ejercicio 3.** Escribe un programa completo que imprima tu nombre tres veces, y da su salida.
> *Solución:*
> ```java
> public class Nombre {
>     public static void main(String[] args) {
>         for (int i = 0; i < 3; i++) System.out.println("Alberto");
>     }
> }
> // Salida:
> // Alberto
> // Alberto
> // Alberto
> ```

**Ejercicio 4.** ¿Qué ventaja práctica tiene que Java sea estáticamente tipado, frente a un lenguaje que no lo es?
> *Solución:* Atrapa errores de tipo en **compilación** (antes de ejecutar), no en producción frente al usuario; es una red de seguridad que abarata corregir bugs.

**Ejercicio 5.** Menciona dos lugares donde se usa Java y por qué te conviene como SDET.
> *Solución:* Backends empresariales/banca y automatización de pruebas (Selenium/RestAssured/JUnit). Te conviene porque la mayoría de vacantes SDET piden Java por su ecosistema de automatización.

**Ejercicio 6.** ¿Qué es una versión LTS y por qué importa?
> *Solución:* *Long-Term Support*: versiones con soporte prolongado (8, 11, 17, 21) que las empresas adoptan por estabilidad. Importa porque es lo que usarás en el trabajo y lo que conviene mencionar en entrevista.

---

## 0.1 La plataforma Java: JVM, JDK, JRE, bytecode y el recolector de basura

Esta es la pregunta de entrevista #1 sobre fundamentos de Java, y casi nadie la explica completa. Vamos a fondo, despacio.

### 0.1.1 El viaje del código: de lo que escribes a lo que se ejecuta

```
   Tu código          Compilador        Formato intermedio        Ejecución
  (Hola.java)  ──────►  (javac)  ──────►   (Hola.class)    ──────►  (JVM)
  texto que          revisa tipos       "bytecode": ni texto      lo carga,
  tú escribes        y traduce          ni código máquina;        verifica,
                                         intermedio y universal    interpreta y
                                                                    optimiza (JIT)
```
1. Escribes en un archivo **`.java`** (texto legible para ti).
2. **`javac`** lo **compila**: revisa la sintaxis y los tipos, y si todo está bien produce un **`.class`** con **bytecode**.
3. La **JVM** toma ese bytecode y lo ejecuta en tu máquina.

### 0.1.2 ¿Qué es el bytecode, en concreto?

🔧 El **bytecode** es un conjunto de instrucciones de bajo nivel para una "máquina imaginaria" (la JVM), no para un procesador real. Es **intermedio**: más cercano a la máquina que tu código, pero independiente del procesador. Por eso es portable: cualquier JVM sabe leerlo.

Puedes **verlo** con la herramienta `javap` (viene en el JDK). Para el "Hola mundo", `javap -c Hola` muestra algo como:
```
public static void main(java.lang.String[]);
  Code:
     0: getstatic     #7   // System.out
     3: ldc           #13  // String "¡Hola, mundo!"
     5: invokevirtual #15  // println
     8: return
```
No necesitas leer bytecode a mano nunca, pero **saber que existe y qué es** te distingue en una entrevista.

🏠 **Analogía:** escribes un libro y quieres publicarlo en 50 países con idiomas distintos. En vez de traducirlo 50 veces, lo traduces a **un idioma universal** (el bytecode); cada país tiene una máquina lectora (la JVM) que lo "lee en voz alta" en su idioma local. Escribes una vez, se lee en todos lados.

### 0.1.3 JVM, JRE y JDK (las muñecas rusas)

Tres cosas que se contienen una a otra:

- **JVM (Java Virtual Machine):** el **motor** que ejecuta el bytecode. Hay una JVM distinta para cada sistema operativo, pero **todas ejecutan el mismo bytecode** — esa es la magia de la portabilidad.
- **JRE (Java Runtime Environment):** la JVM **+** las librerías estándar (`java.util`, `java.lang`, etc.). Es lo mínimo para **ejecutar** programas Java.
- **JDK (Java Development Kit):** el JRE **+** las herramientas de **desarrollo**: el compilador `javac`, el depurador, `javap`, etc. Para **escribir** Java necesitas el **JDK**.

```
┌──────────────────── JDK (DESARROLLAR) ─────────────────────┐
│  javac · javap · jdb (compilador y herramientas)            │
│  ┌──────────────── JRE (EJECUTAR) ──────────────────────┐   │
│  │  librerías estándar (java.util, java.lang, ...)      │   │
│  │   ┌──────────── JVM (el motor) ───────────┐          │   │
│  │   │  carga, verifica, interpreta, optimiza │          │   │
│  │   └───────────────────────────────────────┘          │   │
│  └──────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────┘
```
> 🔑 **Regla:** desarrollas → necesitas **JDK**. Solo ejecutas → basta el **JRE**. La **JVM** es el motor dentro de ambos.

### 0.1.4 Cómo ejecuta la JVM (por dentro): carga, verificación, JIT

Cuando corres `java Hola`, la JVM hace más de lo que parece:
1. **Class Loader (cargador de clases):** localiza y carga el `.class` en memoria.
2. **Bytecode Verifier (verificador):** revisa que el bytecode sea seguro y válido (que no haga trampas peligrosas). Parte de la "robustez" de Java.
3. **Ejecución:** la JVM **interpreta** el bytecode instrucción por instrucción. Pero hay un truco de rendimiento clave:
4. **JIT (Just-In-Time Compiler):** la JVM detecta el código que se ejecuta **muchas veces** (los "puntos calientes", de ahí el nombre **HotSpot** de la JVM de Oracle) y lo **compila a código de máquina nativo** en caliente, para que corra tan rápido como C en esos tramos. 🔑 Por eso Java, aunque "interpretado", es **muy** rápido en la práctica: lo caliente se vuelve nativo.

### 0.1.5 La memoria de la JVM: Heap y Stack (debes saber esto)

🔧 La JVM divide la memoria en zonas. Las dos que **siempre** caen en entrevistas:

- **Stack (pila):** guarda las **variables locales** y los **marcos de llamada** de los métodos (cada llamada a un método crea un "marco"). Es rápida y se limpia sola cuando el método retorna. Aquí viven los **primitivos locales** y las **referencias** (las flechas).
- **Heap (montón):** guarda **todos los objetos** creados con `new`. Es la zona grande y compartida. Aquí es donde trabaja el **garbage collector**.

```java
public class Memoria {
    public static void main(String[] args) {
        int x = 5;                    // 'x' (primitivo) vive en el STACK
        Perro p = new Perro();        // la referencia 'p' en el STACK;
                                      // el OBJETO Perro vive en el HEAP
    }
}
```
```
   STACK (por método)            HEAP (objetos)
   ┌───────────────┐             ┌────────────────┐
   │ x = 5         │             │  objeto Perro  │
   │ p ───────────────────────►  │  nombre=null   │
   └───────────────┘             └────────────────┘
```
🔑 Esto explica cosas que ya viste: por qué `int b = a` copia el valor (primitivo en stack) pero `Perro b = a` hace que ambos apunten al **mismo objeto del heap** (copian la flecha, no el objeto). También explica el `StackOverflowError` (la pila se llena con demasiadas llamadas recursivas) y el `OutOfMemoryError` (el heap se llena de objetos).

### 0.1.6 EL RECOLECTOR DE BASURA (GARBAGE COLLECTOR) — a fondo

Este fue un hueco del manual; aquí queda cubierto con la profundidad que merece, porque **es pregunta de entrevista clásica**.

**El problema que resuelve.** Cada objeto que creas con `new` ocupa espacio en el **heap**. Si nadie liberara esa memoria, el heap se llenaría y el programa moriría (`OutOfMemoryError`). En C/C++ **tú** liberas a mano (`free`/`delete`), y equivocarte causa los dos peores bugs: **fugas de memoria** (olvidas liberar) y **errores de doble liberación / punteros colgantes** (liberas algo que aún se usa). Java **elimina** esa clase entera de bugs.

**Qué es.** El **garbage collector (GC)** es un proceso de la JVM que corre **automáticamente** en segundo plano, encuentra los objetos que **ya nadie puede usar** y libera su memoria. Tú nunca liberas memoria a mano en Java.

🏠 **Analogía:** un servicio de limpieza en un hotel que, sin que se lo pidas, detecta las habitaciones que ya nadie ocupa (a las que ya nadie tiene llave) y las desocupa para nuevos huéspedes. Tú solo te preocupas por hospedarte; el hotel recupera el espacio.

**¿Cómo decide qué es basura? — Alcanzabilidad (reachability).** 🔧 El GC parte de unas raíces llamadas **GC Roots** (variables locales activas en el stack, variables estáticas, etc.) y sigue todas las referencias. Un objeto al que **se puede llegar** siguiendo flechas desde una raíz está **vivo**. Un objeto al que **ya no se puede llegar** desde ninguna raíz es **basura**: nadie lo puede usar, así que se recolecta.
```java
public class Basura {
    public static void main(String[] args) {
        String s = new String("hola");   // objeto A, alcanzable por 's'
        s = new String("mundo");          // 's' ahora apunta a B;
                                          // el objeto A ("hola") quedó SIN referencias
                                          // -> es basura, el GC lo recolectará
        System.out.println(s);            // mundo
    }
}
// Salida:
// mundo
// (en algún momento, el GC liberará el objeto "hola" sin que tú hagas nada)
```

**Generaciones (cómo trabaja de forma eficiente).** 🔧 La mayoría de los objetos mueren jóvenes (se usan un instante y se desechan). El GC aprovecha esto dividiendo el heap en **generaciones**:
- **Young Generation (joven):** donde nacen los objetos. Se limpia muy seguido y rápido (un **Minor GC**). La mayoría de la basura muere aquí.
- **Old Generation (vieja/tenured):** los objetos que **sobreviven** varias limpiezas se "promueven" aquí. Se limpia con menos frecuencia (un **Major GC** o **Full GC**, más costoso).

🔑 **"Stop-the-world":** durante ciertas fases de recolección, la JVM **pausa** brevemente tu programa para limpiar con seguridad. Los GC modernos (G1, ZGC, Shenandoah) minimizan esas pausas, y por eso existen distintos recolectores para distintas necesidades.

**Lo que NO controlas (y cae en entrevistas):**
- **No decides cuándo corre** el GC; lo decide la JVM. `System.gc()` es solo una **sugerencia** que la JVM puede ignorar — **no lo uses** para "forzar" limpieza.
- **Aún puedes tener fugas de memoria en Java.** El GC libera lo **inalcanzable**, pero si **sigues teniendo referencias** a objetos que ya no necesitas (p. ej. una `List` estática donde metes cosas y nunca las quitas), esos objetos **siguen alcanzables** → el GC no los toca → la memoria crece. La fuga clásica de Java es "referencias olvidadas".
- **`finalize()` está obsoleto** (deprecated); no lo uses para liberar recursos. Para cerrar archivos/conexiones se usa **try-with-resources** (§0.10).

🧪 **Nota SDET:** en suites de automatización largas, las fugas por "referencias olvidadas" (caches que crecen, *listeners* no removidos, drivers no cerrados) provocan que la ejecución se ponga lenta o reviente con `OutOfMemoryError`. Entender el GC te ayuda a diagnosticar por qué tu suite consume cada vez más memoria.

### 0.1.7 "Write once, run anywhere" — la idea completa

Juntando todo: compilas **una vez** a bytecode portable; cada sistema tiene su propia JVM (con su propio GC y su JIT adaptados a ese sistema) que ejecuta ese mismo bytecode. Por eso el `.class` que compilas en tu Windows corre igual en el Linux del servidor sin recompilar. La JVM es la capa que "absorbe" las diferencias entre sistemas.

### 0.1.8 Ejercicios resueltos

**Ejercicio 1.** Diferencia entre JDK, JRE y JVM, y cuál necesitas para programar.
> *Solución:* La **JVM** ejecuta el bytecode (el motor). El **JRE** = JVM + librerías, sirve para **ejecutar**. El **JDK** = JRE + herramientas (`javac`), sirve para **desarrollar**. Para programar necesitas el **JDK**.

**Ejercicio 2.** ¿Qué hace `javac` y qué hace `java`?
> *Solución:* `javac Archivo.java` **compila** a bytecode (`Archivo.class`). `java Archivo` **ejecuta** ese bytecode en la JVM.

**Ejercicio 3.** ¿En qué zona de memoria vive cada cosa?
> ```java
> int x = 10;
> int[] arr = new int[3];
> ```
> *Solución:* `x` (primitivo local) y la **referencia** `arr` viven en el **stack**; el **objeto arreglo** (`new int[3]`) vive en el **heap**.

**Ejercicio 4.** ¿Qué es el garbage collector y cómo decide qué liberar?
> *Solución:* Un proceso automático de la JVM que libera la memoria de objetos **inalcanzables**. Decide por **alcanzabilidad**: si no se puede llegar a un objeto siguiendo referencias desde las *GC Roots*, es basura y se recolecta.

**Ejercicio 5.** Verdadero o falso: en Java no puede haber fugas de memoria. Justifica.
> *Solución:* **Falso.** El GC libera lo inalcanzable, pero si conservas **referencias olvidadas** a objetos que ya no usas (p. ej. en una colección estática que nunca limpias), siguen siendo alcanzables y el GC no los libera → la memoria crece.

**Ejercicio 6.** ¿Por qué Java, siendo "interpretado", puede ser tan rápido como un lenguaje compilado?
> *Solución:* Por el **JIT (Just-In-Time)**: la JVM detecta el código que más se ejecuta y lo compila a **código de máquina nativo** en caliente, así que los tramos críticos corren a velocidad nativa.

**Ejercicio 7.** ¿Qué error indica que se llenó el heap y cuál que se llenó el stack?
> *Solución:* Heap lleno → `OutOfMemoryError`. Stack lleno (p. ej. recursión infinita) → `StackOverflowError`.

**Ejercicio 8.** Tu compañero llama a `System.gc()` para "asegurarse" de que se libere memoria. ¿Qué le dices?
> *Solución:* Que `System.gc()` es solo una **sugerencia** que la JVM puede ignorar; no garantiza nada y no debe usarse para controlar la memoria. Si hay un problema de memoria, casi siempre es una **referencia olvidada** que hay que eliminar.

---
## 0.2 Tu primer programa: estructura, compilar y ejecutar

### 0.2.1 El "Hola, mundo", palabra por palabra

Todo programa Java vive **dentro de una clase**. El más simple posible:
```java
public class Hola {
    public static void main(String[] args) {
        System.out.println("¡Hola, mundo!");
    }
}
// Salida:
// ¡Hola, mundo!
```
Desglose de **cada palabra** (no memorices: entiende):
- **`public`** — modificador de acceso: "visible desde cualquier lado". La JVM necesita poder llamar a esta clase/método desde afuera.
- **`class Hola`** — declara una **clase** llamada `Hola`. En Java **todo el código vive dentro de una clase**. ⚠️ El archivo **debe** llamarse igual que la clase pública: `Hola.java`.
- **`static`** — el método pertenece a la **clase**, no a un objeto; puede ejecutarse **sin crear un objeto** primero (§0.7).
- **`void`** — el método **no devuelve** ningún valor.
- **`main`** — el nombre exacto que la JVM busca como **punto de entrada**: al ejecutar el programa, corre este método primero.
- **`String[] args`** — un **arreglo de Strings** con los argumentos de la línea de comandos (casi nunca lo usarás al principio).
- **`System.out.println(...)`** — imprime texto y salta de línea. `System.out` es la salida estándar (la consola); `println` = "print line".
- **`;`** — **toda instrucción termina en punto y coma.**
- **`{ }`** — delimitan **bloques** (el cuerpo de la clase, el del método). Cada `{` que abres lo cierras con `}`.

🔑 La línea `public static void main(String[] args)` la escribirás tantas veces que se volverá automática, pero ahora sabes **qué significa cada parte**.

### 0.2.2 Compilar y ejecutar (el ciclo de trabajo)

```bash
javac Hola.java      # COMPILA -> genera Hola.class (el bytecode)
java Hola            # EJECUTA -> corre la clase (sin la extensión .class)
# Salida: ¡Hola, mundo!
```
✍️ **Paso a paso:** `javac Hola.java` revisa tu código y, si no hay errores, crea `Hola.class`. Luego `java Hola` arranca la JVM, que busca el `main` de la clase `Hola` y lo ejecuta. *(Desde Java 11 puedes correr `java Hola.java` directo, sin compilar aparte — cómodo para practicar.)*

> 🔑 Este ciclo **escribir → `javac` → `java` → ver salida** es tu laboratorio. Repetirlo decenas de veces es lo que convierte la teoría en dominio.

### 0.2.3 Imprimir: `println`, `print` y `printf`

```java
public class Imprimir {
    public static void main(String[] args) {
        System.out.println("Línea 1");   // imprime y SALTA de línea
        System.out.print("Sin salto. "); // imprime SIN saltar
        System.out.print("Misma línea.\n"); // \n = salto manual
        System.out.printf("Hola %s, tienes %d años.%n", "Ana", 30); // con formato
    }
}
// Salida:
// Línea 1
// Sin salto. Misma línea.
// Hola Ana, tienes 30 años.
```
🔧 **Secuencias de escape** (caracteres especiales dentro de un texto): `\n` salto de línea, `\t` tabulación, `\"` comilla doble literal, `\\` barra invertida. En `printf`, `%s` inserta un String, `%d` un entero, `%f` un decimal, `%n` un salto de línea portable.

### 0.2.4 Leer datos del usuario (programas interactivos) con `Scanner`

Para practicar de verdad necesitas programas que reciban datos. Se usa la clase `Scanner`:
```java
import java.util.Scanner;   // traemos Scanner (import: §0.13)

public class Saludo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);   // lee del teclado
        System.out.print("¿Cómo te llamas? ");
        String nombre = sc.nextLine();          // lee una línea de texto
        System.out.print("¿Cuántos años tienes? ");
        int edad = sc.nextInt();                // lee un entero
        System.out.println("Hola " + nombre + ", el próximo año tendrás " + (edad + 1));
        sc.close();
    }
}
// Si el usuario escribe "Alberto" y luego 34:
// Salida:
// ¿Cómo te llamas? Alberto
// ¿Cuántos años tienes? 34
// Hola Alberto, el próximo año tendrás 35
```
🔑 Métodos de `Scanner`: `nextLine()` (una línea de texto), `nextInt()` (entero), `nextDouble()` (decimal), `next()` (una palabra). ⚠️ Mezclar `nextInt()` con `nextLine()` causa un bug famoso (el `nextInt` deja un salto de línea pendiente); por ahora, usa uno u otro de forma consistente.

### 0.2.5 Comentarios (notas para humanos, ignoradas por el compilador)

```java
// Comentario de una línea
/* Comentario
   de varias líneas */
/** Javadoc: documenta clases y métodos (se puede generar documentación de aquí) */
```
Sirven para explicar el **porqué** de algo. No afectan la ejecución.

### 0.2.6 Cómo leer un error del compilador (clave para desatorarte solo)

Cuando `javac` falla, **lee el mensaje**: trae el **archivo**, la **línea**, y **qué** está mal. Ejemplo:
```java
public class Error1 {
    public static void main(String[] args) {
        System.out.println("hola")   // falta el ;
    }
}
```
```
Error1.java:3: error: ';' expected
        System.out.println("hola")
                                  ^
1 error
```
🔑 **Cómo descifrarlo:** `Error1.java:3` = archivo y **línea 3**; `';' expected` = **qué** falta; la **flecha `^`** señala **dónde**. Errores comunes que reconocerás rápido: `';' expected` (falta punto y coma), `cannot find symbol` (nombre mal escrito o variable no declarada), `incompatible types` (asignaste un tipo donde va otro), `class X is public, should be declared in a file named X.java` (el archivo no se llama como la clase).

### 0.2.7 Ejercicios resueltos

**Ejercicio 1.** Escribe un programa que imprima tu nombre y tu profesión en **dos líneas**, con una sola instrucción `println` por línea.
> ```java
> public class YoSoy {
>     public static void main(String[] args) {
>         System.out.println("Alberto");
>         System.out.println("SDET");
>     }
> }
> // Salida:
> // Alberto
> // SDET
> ```

**Ejercicio 2.** Usa `printf` para imprimir: `Producto: Café | Precio: $45.50`.
> ```java
> System.out.printf("Producto: %s | Precio: $%.2f%n", "Café", 45.5);
> // Salida: Producto: Café | Precio: $45.50
> ```
> (`%.2f` muestra el decimal con 2 cifras.)

**Ejercicio 3.** Programa que pida al usuario dos números enteros y muestre su suma.
> ```java
> import java.util.Scanner;
> public class Suma {
>     public static void main(String[] args) {
>         Scanner sc = new Scanner(System.in);
>         System.out.print("Primer número: ");
>         int a = sc.nextInt();
>         System.out.print("Segundo número: ");
>         int b = sc.nextInt();
>         System.out.println("Suma: " + (a + b));
>         sc.close();
>     }
> }
> // Con 7 y 5 -> Suma: 12
> ```

**Ejercicio 4.** Este código no compila. ¿Por qué y cómo lo arreglas?
> ```java
> public class Mal {
>     public static void main(String[] args) {
>         System.out.println(mensaje);
>     }
> }
> ```
> *Solución:* `cannot find symbol`: `mensaje` no está declarado. Arreglo: `String mensaje = "hola"; System.out.println(mensaje);`

**Ejercicio 5.** ¿Por qué el archivo de `public class Reporte` debe llamarse `Reporte.java`?
> *Solución:* Regla de Java: el archivo debe tener el mismo nombre que la clase **pública** que contiene; si no, error de compilación.

**Ejercicio 6.** Programa que pida el nombre y salude usando `\t` para tabular la salida.
> ```java
> import java.util.Scanner;
> public class Tab {
>     public static void main(String[] args) {
>         Scanner sc = new Scanner(System.in);
>         System.out.print("Nombre: ");
>         String n = sc.nextLine();
>         System.out.println("Hola:\t" + n);   // \t inserta una tabulación
>         sc.close();
>     }
> }
> // Con "Ana" -> Hola:    Ana
> ```

---

## 0.3 Variables y tipos de datos

### 0.3.1 Qué es una variable y cómo se declara

Una **variable** es un espacio con **nombre** para guardar un valor. En Java, al declararla declaras también su **tipo** (qué clase de dato guardará). Sintaxis: **`tipo nombre = valor;`**.
```java
public class Variables {
    public static void main(String[] args) {
        int edad = 30;           // entero
        String nombre = "Ana";   // texto
        double precio = 19.99;   // decimal
        boolean activo = true;   // verdadero/falso
        System.out.println(nombre + " tiene " + edad + " años, activo: " + activo);
    }
}
// Salida:
// Ana tiene 30 años, activo: true
```
Puedes declarar sin asignar y asignar después: `int x; x = 5;`. 🏠 **Analogía:** una variable es una **caja etiquetada**: la etiqueta es el nombre (`edad`), el tipo dice qué cabe (solo enteros), y dentro va el valor (30).

### 0.3.2 Los 8 tipos PRIMITIVOS, a detalle

Los **primitivos** guardan el valor **directamente** y son los ladrillos básicos. Java tiene exactamente 8:

| Tipo | Guarda | Tamaño | Rango / nota | Ejemplo |
|---|---|---|---|---|
| `byte` | entero | 8 bits | −128 a 127 | `byte b = 100;` |
| `short` | entero | 16 bits | −32 768 a 32 767 | `short s = 1000;` |
| `int` | entero | 32 bits | ≈ ±2.1 mil millones | `int i = 42;` |
| `long` | entero grande | 64 bits | enorme; sufijo `L` | `long x = 9000000000L;` |
| `float` | decimal | 32 bits | menos preciso; sufijo `f` | `float f = 3.14f;` |
| `double` | decimal | 64 bits | el **default** para decimales | `double d = 3.14;` |
| `char` | un carácter | 16 bits | comillas **simples** | `char c = 'A';` |
| `boolean` | lógico | — | solo `true`/`false` | `boolean ok = true;` |

🔑 Los que más usarás: **`int`**, **`double`**, **`boolean`**, **`char`**. Nota: `char` usa comillas **simples** (`'A'`), `String` (que **no** es primitivo) usa comillas **dobles** (`"texto"`).

**El desbordamiento (overflow) — programa que lo demuestra:** un `int` tiene un máximo; si lo rebasas, "da la vuelta" al mínimo:
```java
public class Overflow {
    public static void main(String[] args) {
        int max = Integer.MAX_VALUE;        // 2147483647
        System.out.println(max);
        System.out.println(max + 1);        // ¡da la vuelta al negativo!
    }
}
// Salida:
// 2147483647
// -2147483648
```
🔑 Por eso, para contar cosas muy grandes (o sumar muchos enteros), a veces necesitas `long`. En algoritmos, este detalle evita bugs sutiles.

### 0.3.3 Los tipos de REFERENCIA y el modelo de memoria

Todo lo que **no** es primitivo es de **referencia**: `String`, arreglos y cualquier objeto. 🔧 La diferencia clave (conecta con §0.1.5): un primitivo guarda **el valor** (en el stack si es local); una referencia guarda **una flecha** que apunta al objeto, que vive en el **heap**.
```java
public class Referencias {
    public static void main(String[] args) {
        int a = 5;
        int b = a;          // COPIA el valor: b es otro 5 independiente
        b = 99;
        System.out.println(a + " " + b);   // 5 99  (a NO cambió)

        int[] x = {1, 2, 3};
        int[] y = x;        // COPIA la flecha: x e y apuntan al MISMO arreglo
        y[0] = 99;
        System.out.println(x[0] + " " + y[0]);   // 99 99  (¡x SÍ cambió!)
    }
}
// Salida:
// 5 99
// 99 99
```
🏠 **Analogía:** un primitivo es el número de tu casa escrito en un papel (copiarlo te da otro papel igual). Una referencia es la **dirección** de una casa: copiarla te da otra nota con la **misma** dirección — ambas apuntan a la misma casa. Por eso modificar por `y` también se ve por `x`.

⚠️ Consecuencia que ya conoces: comparar objetos con `==` compara **direcciones** (¿la misma casa?), no contenido. Por eso los Strings se comparan con `.equals()` (§0.4.3, cap. 1-B).

### 0.3.4 Valores por defecto e inicialización obligatoria de locales

- **Atributos** (variables de instancia) sin asignar toman un **default**: números → `0`, `boolean` → `false`, `char` → `'\u0000'`, referencias → `null`.
- ⚠️ **Variables locales** (dentro de un método) **NO** tienen default: usarlas sin asignar es **error de compilación**.
```java
public class Locales {
    public static void main(String[] args) {
        int x;
        System.out.println(x);   // ❌ error: variable x might not have been initialized
    }
}
```

### 0.3.5 Constantes con `final`

Si un valor no debe cambiar, márcalo `final` (por convención, en MAYÚSCULAS):
```java
final double PI = 3.14159;
// PI = 3.0;   // ❌ error: cannot assign a value to final variable PI
```

### 0.3.6 Inferencia de tipo con `var` (Java 10+)

Java puede **deducir** el tipo por el valor: `var edad = 30;` es un `int`; `var nombre = "Ana";` es un `String`. Útil para acortar, pero sé explícito cuando ayude a la claridad. ⚠️ `var` solo funciona con variables locales **inicializadas** (Java debe poder deducir el tipo).

### 0.3.7 Conversión de tipos (casting), con programas

**Ampliar (widening) — automático:** un tipo pequeño cabe en uno grande sin esfuerzo.
```java
int x = 5;
double d = x;            // 5 -> 5.0 automático
System.out.println(d);   // 5.0
```
**Reducir (narrowing) — manual y con riesgo:** de grande a chico hay que forzarlo, y se puede **perder información**.
```java
double precio = 9.99;
int entero = (int) precio;       // forzado: TRUNCA el decimal (no redondea)
System.out.println(entero);      // 9
```
🔑 El casting de `double` a `int` **trunca** (corta el decimal), no redondea. Para redondear usa `Math.round(...)`.

### 0.3.8 Autoboxing y la trampa del caché de Integer

Cada primitivo tiene su versión **objeto** (*wrapper*): `int↔Integer`, `double↔Double`, `char↔Character`, `boolean↔Boolean`. Java convierte entre ambos automáticamente (**autoboxing** / **unboxing**). Importa porque las **colecciones** solo guardan objetos: `List<Integer>`, no `List<int>` (§0.11–0.12).
```java
Integer a = 5;     // autoboxing: int 5 -> Integer
int b = a;         // unboxing: Integer -> int
```
⚠️ **Trampa de entrevista — `==` con `Integer`:** comparar dos `Integer` con `==` compara **referencias**, no valores, y por una optimización (la JVM cachea los Integer de −128 a 127) "funciona" para valores pequeños y **falla** para grandes:
```java
public class CacheInteger {
    public static void main(String[] args) {
        Integer a = 100, b = 100;
        System.out.println(a == b);        // true  (cacheados, misma referencia)
        Integer c = 1000, d = 1000;
        System.out.println(c == d);        // false (fuera de caché, distintas referencias)
        System.out.println(c.equals(d));   // true  (equals compara VALOR -> correcto)
    }
}
// Salida:
// true
// false
// true
```
🔑 **Lección:** con objetos (incluido `Integer`), compara con **`.equals()`**, no con `==`.

### 0.3.9 Promoción de tipos en expresiones

⚠️ En operaciones, Java "promueve" al tipo más grande involucrado — y la **división entera** sorprende:
```java
System.out.println(5 / 2);        // 2    (int / int = int, trunca)
System.out.println(5.0 / 2);      // 2.5  (un double involucrado -> double)
System.out.println('A' + 1);      // 66   ('A' se promueve a int: 65 + 1)
System.out.println((char)('A' + 1)); // B  (de vuelta a char)
```

### 0.3.10 Ejercicios resueltos

**Ejercicio 1.** Declara una constante para el número de días de la semana y úsala.
> ```java
> final int DIAS_SEMANA = 7;
> System.out.println("Hay " + DIAS_SEMANA + " días.");
> ```

**Ejercicio 2.** ¿Qué imprime y por qué?
> ```java
> int a = 10, b = 3;
> System.out.println(a / b);
> System.out.println((double) a / b);
> ```
> *Solución:* `3` (división entera: 10/3 trunca a 3) y `3.3333...` (al convertir `a` a double, la división es decimal).

**Ejercicio 3.** Programa que demuestre que copiar un arreglo con `=` NO crea una copia independiente.
> ```java
> int[] x = {1, 2, 3};
> int[] y = x;          // misma flecha
> y[0] = 99;
> System.out.println(x[0]);   // 99  -> demuestra que comparten el mismo objeto
> ```

**Ejercicio 4.** ¿Por qué `Integer a = 1000, b = 1000; a == b;` da `false` pero `a.equals(b)` da `true`?
> *Solución:* `==` compara referencias y 1000 está fuera del caché de Integer (−128..127), así que son objetos distintos. `.equals()` compara el **valor**, que sí es igual.

**Ejercicio 5.** Convierte `double nota = 8.7` a `int` y explica el resultado.
> ```java
> double nota = 8.7;
> int n = (int) nota;   // 8  (TRUNCA, no redondea)
> ```
> Para redondear: `int n = (int) Math.round(nota);` daría 9.

**Ejercicio 6.** Predice la salida:
> ```java
> int max = Integer.MAX_VALUE;
> System.out.println(max + 1);
> ```
> *Solución:* `-2147483648`. Es **overflow**: rebasar el máximo de un `int` da la vuelta al mínimo. Para evitarlo, usa `long`.

**Ejercicio 7.** ¿Qué tipo conviene para guardar la población mundial (≈ 8 000 000 000) y por qué?
> *Solución:* `long`, porque ese número rebasa el máximo de `int` (≈ 2.1 mil millones) y causaría overflow.

---
## 0.4 Operadores

Los **operadores** son símbolos que combinan o transforman valores. Son las herramientas con las que manipulas datos.

### 0.4.1 Aritméticos

| Operador | Hace | `a=7, b=2` |
|---|---|---|
| `+` | suma | `9` |
| `-` | resta | `5` |
| `*` | multiplica | `14` |
| `/` | divide | `3` ⚠️ |
| `%` | módulo (residuo) | `1` |

```java
public class Aritmetica {
    public static void main(String[] args) {
        int a = 7, b = 2;
        System.out.println(a + b);   // 9
        System.out.println(a / b);   // 3   <- división ENTERA, trunca
        System.out.println(a % b);   // 1   <- residuo
        System.out.println(7.0 / 2); // 3.5 <- con un double, da decimal
    }
}
// Salida:
// 9
// 3
// 1
// 3.5
```
⚠️ **La trampa clave — división entera:** `int / int` da `int` y **trunca** el decimal. Para decimales, al menos un operando debe ser `double` (`7.0 / 2`).

🔑 **El módulo `%` es oro en algoritmos:**
- `n % 2 == 0` → ¿es par?
- `n % 10` → el último dígito de `n`.
- `i % tam` → "dar la vuelta" en un arreglo circular.
- Lo usaste en FizzBuzz (`i % 15 == 0`).

### 0.4.2 Asignación (y atajos compuestos)

`=` **asigna** (≠ `==`, que compara). Atajos:
```java
public class Asignacion {
    public static void main(String[] args) {
        int x = 10;
        x += 5;  System.out.println(x);  // 15  (x = x + 5)
        x -= 3;  System.out.println(x);  // 12
        x *= 2;  System.out.println(x);  // 24
        x /= 4;  System.out.println(x);  // 6
        x %= 4;  System.out.println(x);  // 2
    }
}
```

### 0.4.3 Comparación (relacionales) — dan `true`/`false`

| Operador | Significa |
|---|---|
| `==` | ¿iguales? |
| `!=` | ¿distintos? |
| `<` `>` | menor / mayor |
| `<=` `>=` | menor-o-igual / mayor-o-igual |

⚠️ **Recordatorio crítico:** `==` con **objetos** (como `String`, `Integer`) compara **referencias**, no contenido (lo viste en §0.3.8). Para contenido usa `.equals()`. `==` solo es seguro con **primitivos**.

### 0.4.4 Lógicos y la evaluación en corto-circuito

| Operador | Significa | Verdadero cuando… |
|---|---|---|
| `&&` | Y (AND) | **ambas** condiciones verdaderas |
| `\|\|` | O (OR) | **al menos una** verdadera |
| `!` | NO (NOT) | invierte el valor |

```java
public class Logicos {
    public static void main(String[] args) {
        int edad = 25;
        System.out.println(edad >= 18 && edad <= 65);  // true (cumple ambas)
        System.out.println(edad < 13 || edad > 60);    // false (ninguna)
        System.out.println(!(edad == 25));             // false (invierte true)
    }
}
```
🔧 **Corto-circuito (importantísimo):** en `A && B`, si `A` es falso, Java **no evalúa B** (ya sabe el resultado). En `A || B`, si `A` es verdadero, no evalúa B. Esto se usa para **protegerte de errores**:
```java
String texto = null;
// Si 'texto' es null, la 1ª parte es falsa y NUNCA se evalúa texto.length() -> no revienta:
if (texto != null && texto.length() > 0) {
    System.out.println("tiene contenido");
}
System.out.println("No reventó");
// Salida:
// No reventó
```
🔑 El **orden importa**: pon primero la condición que protege (`texto != null`).

### 0.4.5 Incremento y decremento (pre vs post)

`++` suma 1, `--` resta 1. La diferencia pre/post solo se nota cuando usas el valor **en la misma línea**:
```java
public class IncrDecr {
    public static void main(String[] args) {
        int b = 5;
        int x = b++;   // POST: usa b (5), LUEGO incrementa -> x=5, b=6
        System.out.println(x + " " + b);   // 5 6

        int c = 5;
        int y = ++c;   // PRE: incrementa primero, LUEGO usa -> y=6, c=6
        System.out.println(y + " " + c);   // 6 6
    }
}
// Salida:
// 5 6
// 6 6
```
🔑 En un `for` (`i++` o `++i`) dan lo mismo, porque no usas el valor en esa línea.

### 0.4.6 El operador ternario (un `if` express)

`condición ? valorSiVerdadero : valorSiFalso`:
```java
int edad = 20;
String tipo = (edad >= 18) ? "adulto" : "menor";
System.out.println(tipo);   // adulto

int a = 7, b = 3;
int mayor = (a > b) ? a : b;   // mayor = 7
```

### 0.4.7 Operadores a nivel de bits (bitwise) — para entrevistas

🔧 Operan sobre los **bits** de los enteros. No los usarás a diario, pero aparecen en problemas de entrevista y trucos de optimización:

| Operador | Nombre | Idea |
|---|---|---|
| `&` | AND bit a bit | 1 solo si ambos bits son 1 |
| `\|` | OR bit a bit | 1 si algún bit es 1 |
| `^` | XOR | 1 si los bits **difieren** |
| `~` | NOT | invierte todos los bits |
| `<<` | desplazar a la izquierda | `x << 1` = multiplicar por 2 |
| `>>` | desplazar a la derecha | `x >> 1` = dividir entre 2 |

🔑 **El truco del XOR** (pregunta clásica): `a ^ a == 0` y `a ^ 0 == a`. Por eso, si en un arreglo todos los números están **dos veces menos uno**, hacer XOR de todos deja **el único que aparece una vez** (los pares se cancelan):
```java
public class XOR {
    public static void main(String[] args) {
        int[] nums = {4, 1, 2, 1, 2};   // todos repetidos menos el 4
        int resultado = 0;
        for (int n : nums) resultado ^= n;   // XOR acumulado
        System.out.println(resultado);        // 4
    }
}
// Salida:
// 4
```
🔑 También: `x << 1` duplica (`5 << 1` = 10) y `x >> 1` divide entre 2 (`20 >> 1` = 10) — útil en heaps (índices de hijos) y optimizaciones.

### 0.4.8 Precedencia (quién va primero)

De mayor a menor prioridad (resumen práctico): `()` → `! ++ --` → `* / %` → `+ -` → `< > <= >=` → `== !=` → `&&` → `||` → `= += ...`. ⚠️ Ante la duda, **usa paréntesis**: `(a && b) || c` es más claro y evita errores.

### 0.4.9 Ejercicios resueltos

**Ejercicio 1.** ¿Cuánto da `17 / 5` y `17 % 5`?
> *Solución:* `17 / 5` = 3 (entera, trunca). `17 % 5` = 2 (residuo).

**Ejercicio 2.** Programa que diga si un número leído es par o impar usando el ternario.
> ```java
> import java.util.Scanner;
> public class ParImpar {
>     public static void main(String[] args) {
>         Scanner sc = new Scanner(System.in);
>         int n = sc.nextInt();
>         System.out.println((n % 2 == 0) ? "par" : "impar");
>         sc.close();
>     }
> }
> // Con 8 -> par ; con 7 -> impar
> ```

**Ejercicio 3.** Explica por qué `if (lista != null && !lista.isEmpty())` es seguro.
> *Solución:* Corto-circuito: si `lista != null` es falso, `&&` no evalúa la segunda parte, así que nunca llama a `.isEmpty()` sobre null.

**Ejercicio 4.** ¿Qué vale `x` y `y`?
> ```java
> int a = 5; int x = a++; int y = ++a;
> ```
> *Solución:* `x = 5` (post: usa 5, luego a=6), `y = 7` (pre: a pasa a 7 y se usa). Al final `a = 7`.

**Ejercicio 5.** Usa XOR para encontrar el número que no se repite en `{7, 3, 5, 3, 7}`.
> ```java
> int r = 0;
> for (int n : new int[]{7,3,5,3,7}) r ^= n;
> System.out.println(r);   // 5
> ```
> *Solución:* Los pares (7^7, 3^3) se cancelan a 0; queda el 5.

**Ejercicio 6.** Obtén el último dígito de un número `n` y la decena completa sin él.
> *Solución:* último dígito = `n % 10`; quitar el último dígito = `n / 10`. Para `n = 273`: `273 % 10` = 3, `273 / 10` = 27.

**Ejercicio 7.** ¿Qué hace `x << 1` y `x >> 1` con `x = 6`?
> *Solución:* `6 << 1` = 12 (duplica), `6 >> 1` = 3 (mitad). Desplazar bits equivale a multiplicar/dividir por 2.

---

## 0.5 Estructuras de control (condicionales y bucles)

Por defecto el código corre **de arriba abajo, una línea tras otra**. Las estructuras de control cambian eso: permiten **decidir** (condicionales) y **repetir** (bucles). 🔑 **Los bucles son el corazón de Big-O:** contar cuántas veces se repite un bucle *es* calcular la complejidad (Parte 1).

### 0.5.1 Condicionales: `if` / `else if` / `else`

```java
public class Notas {
    public static void main(String[] args) {
        int nota = 75;
        if (nota >= 90)      System.out.println("Excelente");
        else if (nota >= 60) System.out.println("Aprobado");  // solo si la anterior fue falsa
        else                 System.out.println("Reprobado");
    }
}
// Salida:
// Aprobado
```
🔑 **El orden importa:** Java entra en el **primer** `if` verdadero e ignora el resto. Por eso el caso más restrictivo va primero (lo viste en FizzBuzz). ⚠️ Sin llaves, el `if` solo controla la **siguiente** línea; usa `{ }` siempre para evitar bugs.

### 0.5.2 `switch` (elegir entre valores fijos)

Cuando comparas una variable contra **varios valores concretos**:
```java
public class DiaSemana {
    public static void main(String[] args) {
        int dia = 3;
        switch (dia) {
            case 1: System.out.println("Lunes"); break;     // ⚠️ break clave
            case 2: System.out.println("Martes"); break;
            case 3: System.out.println("Miércoles"); break;
            default: System.out.println("Otro");
        }
    }
}
// Salida:
// Miércoles
```
⚠️ **Trampa famosa (fall-through):** sin `break`, la ejecución "cae" al siguiente caso y lo ejecuta también. 🔧 **Java moderno (14+)** ofrece el `switch` con flecha, que no necesita `break` y puede devolver valor:
```java
String nombre = switch (dia) {
    case 1 -> "Lunes";
    case 2 -> "Martes";
    case 3 -> "Miércoles";
    default -> "Otro";
};   // nombre = "Miércoles"
```

### 0.5.3 Bucle `for` (cuando controlas cuántas veces)

Tres partes: **inicio**; **condición**; **paso**.
```java
public class ForDemo {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {     // i=0; mientras i<5; +1 cada vuelta
            System.out.print(i + " ");
        }
    }
}
// Salida:
// 0 1 2 3 4
```
✍️ **Traza:** i=0 (imprime 0) → i=1 → i=2 → i=3 → i=4 (imprime 4) → i=5 (5<5 falso, sale). **5 vueltas.** 🔑 *Ese "5 veces" sobre un límite `n` es un O(n).*

### 0.5.4 Bucle `while` (mientras se cumpla algo)

```java
public class WhileDemo {
    public static void main(String[] args) {
        int n = 16;
        while (n > 1) {        // repite mientras n > 1
            n = n / 2;
            System.out.print(n + " ");
        }
    }
}
// Salida:
// 8 4 2 1
```
🔑 *Dividir entre 2 cada vuelta → ~log₂(n) repeticiones → es la forma de un **O(log n)*** (búsqueda binaria). ⚠️ Si la condición nunca se vuelve falsa, tienes un **bucle infinito**: asegúrate de que algo avance hacia la salida.

### 0.5.5 Bucle `do-while` (ejecuta al menos una vez)

Revisa la condición **al final**, así corre mínimo una vez:
```java
public class DoWhile {
    public static void main(String[] args) {
        int x = 10;
        do {
            System.out.println("corre una vez, x=" + x);
            x++;
        } while (x < 5);   // 10<5 es falso, pero ya corrió una vez
    }
}
// Salida:
// corre una vez, x=10
```

### 0.5.6 Bucle `for-each` (recorrer colecciones/arreglos)

```java
public class ForEach {
    public static void main(String[] args) {
        int[] nums = {10, 20, 30};
        for (int valor : nums) System.out.print(valor + " ");
    }
}
// Salida:
// 10 20 30
```
🔑 Más limpio y seguro (no te equivocas de índice), pero **no te da el índice** ni permite modificar el arreglo en su lugar; para eso usa el `for` clásico.

### 0.5.7 `break` y `continue`

- **`break`** sale del bucle por completo. **`continue`** salta a la siguiente vuelta.
```java
public class BreakContinue {
    public static void main(String[] args) {
        for (int i = 0; i < 10; i++) {
            if (i == 7) break;          // al llegar a 7, sale del bucle
            if (i % 2 == 0) continue;   // si es par, salta esta vuelta
            System.out.print(i + " ");
        }
    }
}
// Salida:
// 1 3 5
```

### 0.5.8 Bucles anidados → el origen del O(n²)

Un bucle dentro de otro recorre **combinaciones**:
```java
public class Anidados {
    public static void main(String[] args) {
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= 3; j++) {
                System.out.print(i + "," + j + "  ");
            }
            System.out.println();
        }
    }
}
// Salida:
// 1,1  1,2  1,3
// 2,1  2,2  2,3
// 3,1  3,2  3,3
```
🔑 *Las repeticiones se **multiplican**: 3×3 = 9. Dos bucles anidados sobre `n` → n×n = **O(n²)**.* Esta es la conexión que más usarás al analizar algoritmos.

### 0.5.9 Ejercicios resueltos

**Ejercicio 1.** Imprime los números del 1 al 10 con un `for`.
> ```java
> for (int i = 1; i <= 10; i++) System.out.print(i + " ");
> // 1 2 3 4 5 6 7 8 9 10
> ```

**Ejercicio 2.** Suma los números del 1 al 100 e imprime el total.
> ```java
> int suma = 0;
> for (int i = 1; i <= 100; i++) suma += i;
> System.out.println(suma);   // 5050
> ```

**Ejercicio 3.** Programa FizzBuzz del 1 al 15 (múltiplos de 3 → Fizz, de 5 → Buzz, de ambos → FizzBuzz).
> ```java
> for (int i = 1; i <= 15; i++) {
>     if (i % 15 == 0) System.out.println("FizzBuzz");
>     else if (i % 3 == 0) System.out.println("Fizz");
>     else if (i % 5 == 0) System.out.println("Buzz");
>     else System.out.println(i);
> }
> // 1,2,Fizz,4,Buzz,Fizz,7,8,Fizz,Buzz,11,Fizz,13,14,FizzBuzz
> ```
> 🔑 El `% 15` va primero, o los múltiplos de 15 nunca dirían "FizzBuzz".

**Ejercicio 4.** Cuenta cuántas veces se ejecuta el cuerpo y di su Big-O:
> ```java
> for (int i = 0; i < n; i++)
>     for (int j = 0; j < n; j++)
>         System.out.println(i + "," + j);
> ```
> *Solución:* n×n = n² veces → **O(n²)**.

**Ejercicio 5.** Imprime la tabla de multiplicar del 5 (del 1 al 10) con un `while`.
> ```java
> int i = 1;
> while (i <= 10) { System.out.println("5 x " + i + " = " + (5 * i)); i++; }
> ```

**Ejercicio 6.** Programa que lea números hasta que el usuario escriba 0, y al final muestre la suma.
> ```java
> import java.util.Scanner;
> public class SumaHastaCero {
>     public static void main(String[] args) {
>         Scanner sc = new Scanner(System.in);
>         int suma = 0, n;
>         do { n = sc.nextInt(); suma += n; } while (n != 0);  // do-while: lee al menos uno
>         System.out.println("Suma: " + suma);
>         sc.close();
>     }
> }
> // Con 3, 4, 5, 0 -> Suma: 12
> ```

**Ejercicio 7.** Imprime solo los números impares del 1 al 20 usando `continue`.
> ```java
> for (int i = 1; i <= 20; i++) { if (i % 2 == 0) continue; System.out.print(i + " "); }
> // 1 3 5 7 9 11 13 15 17 19
> ```

---
## 0.6 Métodos (funciones)

Un **método** es un bloque de código con **nombre** que hace una tarea y puedes **reutilizar** llamándolo. Evita repetir código y parte el programa en piezas manejables.

🏠 **Analogía:** un método es como una licuadora. Le metes ingredientes (parámetros), hace su trabajo dentro (no necesitas saber cómo) y te entrega un resultado (el valor de retorno). La usas mil veces sin reconstruirla.

### 0.6.1 Anatomía de un método

```java
public class Calculadora {
    // modificador | static | retorno | nombre | (parámetros)
    public static int sumar(int a, int b) {
        int resultado = a + b;
        return resultado;          // devuelve un valor y termina el método
    }
    public static void main(String[] args) {
        int total = sumar(3, 4);
        System.out.println(total);  // 7
    }
}
// Salida:
// 7
```
- **`public`** — quién puede llamarlo (§0.8).
- **`static`** — pertenece a la clase, se llama sin crear objeto (por ahora, los de utilidad son `static`).
- **`int`** — el **tipo que devuelve**. Si no devuelve nada → **`void`**.
- **`sumar`** — el nombre (por convención empieza en minúscula).
- **`(int a, int b)`** — los **parámetros** (datos que recibe, cada uno con su tipo).
- **`return`** — devuelve el valor (su tipo debe coincidir con el declarado) y **corta** el método ahí.

### 0.6.2 `void`, parámetros vs argumentos

Un método `void` solo "hace", no devuelve:
```java
public class Saludos {
    public static void saludar(String nombre) {   // 'nombre' = PARÁMETRO
        System.out.println("Hola, " + nombre);
    }
    public static void main(String[] args) {
        saludar("Ana");      // "Ana" = ARGUMENTO
        saludar("Beto");
    }
}
// Salida:
// Hola, Ana
// Hola, Beto
```
🔑 **Parámetro** = la variable en la definición. **Argumento** = el valor real que pasas al llamar. Se asignan en orden.

`return` también sirve para **salir temprano**:
```java
public static String clasificar(int n) {
    if (n < 0) return "negativo";   // sale aquí mismo si es negativo
    if (n == 0) return "cero";
    return "positivo";
}
```

### 0.6.3 Sobrecarga (overloading): mismo nombre, distintos parámetros

```java
public class Overload {
    static int sumar(int a, int b) { return a + b; }
    static double sumar(double a, double b) { return a + b; }   // distinto TIPO
    static int sumar(int a, int b, int c) { return a + b + c; } // distinto NÚMERO

    public static void main(String[] args) {
        System.out.println(sumar(2, 3));        // 5    (primera)
        System.out.println(sumar(2.5, 1.5));    // 4.0  (segunda)
        System.out.println(sumar(1, 2, 3));     // 6    (tercera)
    }
}
// Salida:
// 5
// 4.0
// 6
```
🔑 Java elige la versión según los argumentos. ⚠️ No basta cambiar solo el **tipo de retorno**; deben diferir los **parámetros**.

### 0.6.4 Ámbito (scope) de variables

Una variable declarada **dentro** de un método (o bloque `{}`) solo existe ahí:
```java
public static void ejemplo() {
    int x = 5;            // x vive solo en ejemplo()
    if (x > 0) {
        int y = 10;       // y vive solo dentro de este if
    }
    // aquí 'y' YA NO existe -> usarla sería error de compilación
}
```

### 0.6.5 Paso por valor (primitivos): el método recibe una COPIA

```java
public class PorValor {
    static void intentarCambiar(int n) { n = 999; }   // cambia la copia local
    public static void main(String[] args) {
        int a = 5;
        intentarCambiar(a);
        System.out.println(a);   // 5  (NO cambió: se pasó una copia)
    }
}
// Salida:
// 5
```
🔑 **Java siempre pasa por valor.** Para un primitivo, el método recibe una copia, así que no puede alterar tu variable.

### 0.6.6 El matiz con objetos (la COPIA es de la referencia)

⚠️ Cuando pasas un objeto/arreglo, se copia la **referencia** (la flecha). El método no puede hacer que tu variable apunte a otro objeto, pero **sí puede modificar el objeto al que apunta**:
```java
public class PorValorObjetos {
    static void modificar(int[] arr) { arr[0] = 999; }   // modifica el MISMO arreglo
    static void reasignar(int[] arr) { arr = new int[]{-1}; }  // reasigna SOLO la copia local
    public static void main(String[] args) {
        int[] x = {1, 2, 3};
        modificar(x);
        System.out.println(x[0]);   // 999  (SÍ cambió: misma referencia)
        reasignar(x);
        System.out.println(x[0]);   // 999  (reasignar NO afectó la x de afuera)
    }
}
// Salida:
// 999
// 999
```
🔑 Resumen: puedes **modificar** el objeto compartido, pero no **reapuntar** la variable del que llama.

### 0.6.7 Métodos con argumentos variables (varargs)

Permite recibir **cualquier cantidad** de argumentos con `...`:
```java
public class Varargs {
    static int sumarTodos(int... nums) {     // nums se comporta como un arreglo
        int total = 0;
        for (int n : nums) total += n;
        return total;
    }
    public static void main(String[] args) {
        System.out.println(sumarTodos(1, 2, 3));        // 6
        System.out.println(sumarTodos(10, 20, 30, 40)); // 100
    }
}
// Salida:
// 6
// 100
```

### 0.6.8 Recursión: un método que se llama a sí mismo (puente al Patrón 5)

Un método **recursivo** se llama a sí mismo sobre una versión más pequeña del problema, hasta un **caso base** que lo detiene:
```java
public class Factorial {
    static int factorial(int n) {
        if (n <= 1) return 1;            // CASO BASE: detiene la recursión
        return n * factorial(n - 1);     // CASO RECURSIVO: se acerca al base
    }
    public static void main(String[] args) {
        System.out.println(factorial(4));   // 24
    }
}
// Salida:
// 24
```
✍️ **Traza** de `factorial(4)`: `4*factorial(3)` → `3*factorial(2)` → `2*factorial(1)` → `1` (base). Se "desenrolla": 2*1=2, 3*2=6, 4*6=**24**. ⚠️ Sin caso base (o uno inalcanzable) → `StackOverflowError` (la pila de llamadas se llena, §0.1.5). Lo profundizas en el Patrón 5.

### 0.6.9 Por qué importan para SDET

🧪 Toda suite de automatización se organiza en métodos: un método por **caso de prueba** (`testLoginValido()`), métodos **auxiliares** reutilizables (`iniciarSesion(usuario, clave)`, `esperarElemento(...)`). El **Page Object Model** agrupa métodos que representan acciones de una página. Dominar métodos es dominar la estructura de tu framework.

### 0.6.10 Ejercicios resueltos

**Ejercicio 1.** Método que reciba dos enteros y devuelva el mayor.
> ```java
> static int mayor(int a, int b) { return (a > b) ? a : b; }
> ```

**Ejercicio 2.** Método `void` que imprima una línea de `n` asteriscos.
> ```java
> static void linea(int n) {
>     for (int i = 0; i < n; i++) System.out.print("*");
>     System.out.println();
> }
> // linea(4) -> ****
> ```

**Ejercicio 3.** Sobrecarga: un método `area` para un cuadrado (un lado) y para un rectángulo (dos lados).
> ```java
> static int area(int lado) { return lado * lado; }
> static int area(int base, int altura) { return base * altura; }
> ```

**Ejercicio 4.** ¿Imprime qué? Explica.
> ```java
> static void cambia(int x) { x = x * 2; }
> public static void main(String[] a) {
>     int n = 10; cambia(n); System.out.println(n);
> }
> ```
> *Solución:* `10`. Paso por valor: `cambia` recibe una copia; la `n` original no cambia.

**Ejercicio 5.** Método recursivo que sume los números del 1 al n.
> ```java
> static int suma(int n) {
>     if (n == 0) return 0;        // caso base
>     return n + suma(n - 1);      // caso recursivo
> }
> // suma(5) -> 15
> ```

**Ejercicio 6.** Método con varargs que devuelva el máximo de cualquier cantidad de enteros.
> ```java
> static int maximo(int... nums) {
>     int m = nums[0];
>     for (int n : nums) if (n > m) m = n;
>     return m;
> }
> // maximo(3, 9, 2, 7) -> 9
> ```

**Ejercicio 7.** Método recursivo que cuente cuántos dígitos tiene un número positivo.
> ```java
> static int digitos(int n) {
>     if (n < 10) return 1;            // base: un solo dígito
>     return 1 + digitos(n / 10);      // quita un dígito y suma 1
> }
> // digitos(2025) -> 4
> ```

---

## 0.7 Programación Orientada a Objetos (POO): clases y objetos

Llegamos al concepto central de Java. Lo anterior (variables, métodos) eran las piezas; la POO es **cómo se organizan en unidades con sentido**.

### 0.7.1 Qué es la POO y por qué existe

La **POO** organiza el código modelando **"cosas" como objetos**, donde cada objeto agrupa sus **datos** (qué es) y sus **comportamientos** (qué hace). En vez de variables y funciones sueltas, las juntas.

🏠 **Analogía:** sin POO tendrías "color de coche", "velocidad", y funciones "acelerar", "frenar" flotando sueltas. Con POO creas un objeto **Coche** que **tiene** color y velocidad y **sabe** acelerar y frenar. Todo lo del coche, junto y coherente.

### 0.7.2 Clase vs objeto (la distinción que SIEMPRE preguntan)

- Una **clase** es el **plano/molde**: define qué datos y métodos tendrán los objetos. No es una cosa concreta.
- Un **objeto** es una **instancia** concreta creada con `new`: una cosa real con valores propios.

```
   CLASE (plano)              OBJETOS (instancias)
   ┌──────────┐               ┌──────────┐  ┌──────────┐
   │  Coche   │   ──new──►    │ miHonda  │  │ elToyota │
   │ color    │               │ rojo     │  │ azul     │
   │ acelerar │               │ 0 km/h   │  │ 80 km/h  │
   └──────────┘               └──────────┘  └──────────┘
```
🏠 La clase `Coche` es el **plano arquitectónico**; cada coche construido con él (tu Honda rojo, el Toyota azul) es un **objeto**. Un plano, muchas casas.

### 0.7.3 Definir una clase (atributos)

Los **atributos** (campos) son las variables que describen al objeto — su **estado**:
```java
public class Coche {
    String color;       // atributos = estado del objeto
    int velocidad;
}
```

### 0.7.4 Crear objetos: `new`, constructor, `this`, y constructores múltiples

`new` crea el objeto; el **constructor** (método especial con el **nombre de la clase y sin tipo de retorno**) lo inicializa:
```java
public class Coche {
    String color;
    int velocidad;

    Coche(String color) {          // CONSTRUCTOR
        this.color = color;        // 'this' = este objeto; distingue atributo de parámetro
        this.velocidad = 0;        // todo coche nace detenido
    }
    Coche() {                      // CONSTRUCTOR sobrecargado (sin argumentos)
        this("blanco");            // llama al otro constructor con un color por defecto
    }

    public static void main(String[] args) {
        Coche miHonda = new Coche("rojo");   // usa el primer constructor
        Coche generico = new Coche();         // usa el segundo -> color "blanco"
        System.out.println(miHonda.color);    // rojo
        System.out.println(generico.color);   // blanco
    }
}
// Salida:
// rojo
// blanco
```
🔑 **`this`** = el objeto actual; **constructores múltiples** (sobrecarga) dan distintas formas de crear el objeto; **`this("...")`** llama a otro constructor de la misma clase. 🔧 Si no escribes **ningún** constructor, Java da uno vacío por defecto; al escribir uno propio, ese por defecto desaparece.

### 0.7.5 Métodos de instancia (comportamiento que usa el estado)

```java
public class Coche {
    String color;
    int velocidad;
    Coche(String color) { this.color = color; this.velocidad = 0; }

    void acelerar(int cuanto) { this.velocidad += cuanto; }   // modifica ESTE objeto
    void frenar() { this.velocidad = 0; }

    public static void main(String[] args) {
        Coche c = new Coche("azul");
        c.acelerar(50);
        c.acelerar(30);
        System.out.println(c.velocidad);   // 80
        c.frenar();
        System.out.println(c.velocidad);   // 0
    }
}
// Salida:
// 80
// 0
```
🔑 Cada objeto tiene **su propio** estado: acelerar `c` no afecta a otro coche.

### 0.7.6 El método `toString()` (cómo se "imprime" un objeto)

Por defecto, imprimir un objeto muestra algo ilegible (`Coche@1b6d3586`). Sobrescribe `toString()` para una salida útil:
```java
public class Coche {
    String color; int velocidad;
    Coche(String color) { this.color = color; }

    @Override
    public String toString() {
        return "Coche{color=" + color + ", velocidad=" + velocidad + "}";
    }
    public static void main(String[] args) {
        Coche c = new Coche("rojo");
        System.out.println(c);   // Java llama a toString() automáticamente
    }
}
// Salida:
// Coche{color=rojo, velocidad=0}
```

### 0.7.7 `static` vs de instancia (con programa)

Un miembro **`static`** pertenece a **la clase entera** (uno solo, compartido); uno **de instancia** existe **por objeto**:
```java
public class Contador {
    static int totalCreados = 0;     // compartido por TODOS
    int id;                          // propio de cada objeto
    Contador() { totalCreados++; this.id = totalCreados; }

    public static void main(String[] args) {
        Contador a = new Contador();
        Contador b = new Contador();
        Contador c = new Contador();
        System.out.println(a.id + " " + b.id + " " + c.id);   // 1 2 3
        System.out.println(Contador.totalCreados);            // 3 (por la CLASE)
    }
}
// Salida:
// 1 2 3
// 3
```
🏠 "Número de ruedas = 4" sería `static` (igual para todos). "Velocidad actual" es de instancia (cada coche la suya). Por eso `main` es `static`: corre sin que exista ningún objeto.

### 0.7.8 Por qué importa para SDET

🧪 El **Page Object Model** es POO pura: una **clase por página** (`LoginPage`, `HomePage`), cuyos **atributos** son los elementos de la página y cuyos **métodos** son las acciones (`iniciarSesion(...)`). Tus pruebas crean objetos de esas clases y llaman sus métodos. Sin clases y objetos, no entiendes tu propio framework.

### 0.7.9 Ejercicios resueltos

**Ejercicio 1.** Crea una clase `Persona` con `nombre` y `edad`, un constructor, y un método que se presente.
> ```java
> public class Persona {
>     String nombre; int edad;
>     Persona(String nombre, int edad) { this.nombre = nombre; this.edad = edad; }
>     void presentarse() { System.out.println("Soy " + nombre + ", " + edad + " años"); }
>     public static void main(String[] a) {
>         new Persona("Ana", 30).presentarse();   // Soy Ana, 30 años
>     }
> }
> ```

**Ejercicio 2.** Diferencia entre clase y objeto, en una frase.
> *Solución:* La clase es el plano que define datos y métodos; el objeto es una instancia concreta creada con `new`, con valores propios.

**Ejercicio 3.** Crea una clase `CuentaBancaria` con `saldo`, y métodos `depositar` y `retirar` (sin permitir saldo negativo).
> ```java
> public class CuentaBancaria {
>     double saldo;
>     void depositar(double m) { if (m > 0) saldo += m; }
>     void retirar(double m) { if (m > 0 && m <= saldo) saldo -= m; }
>     public static void main(String[] a) {
>         CuentaBancaria c = new CuentaBancaria();
>         c.depositar(100); c.retirar(30);
>         System.out.println(c.saldo);   // 70.0
>     }
> }
> ```

**Ejercicio 4.** ¿Qué imprime y por qué?
> ```java
> Contador a = new Contador(); Contador b = new Contador();
> System.out.println(Contador.totalCreados);
> ```
> *Solución:* `2`. `totalCreados` es `static` (compartido por la clase) y aumenta en cada constructor; se crearon 2 objetos.

**Ejercicio 5.** Agrega un `toString()` a `Persona` que devuelva `"Persona{nombre=..., edad=...}"`.
> ```java
> @Override
> public String toString() { return "Persona{nombre=" + nombre + ", edad=" + edad + "}"; }
> ```

**Ejercicio 6.** Crea una clase `Rectangulo` con `ancho` y `alto`, y un método `area()` que devuelva el área. Crea dos objetos distintos y muestra sus áreas.
> ```java
> public class Rectangulo {
>     int ancho, alto;
>     Rectangulo(int ancho, int alto) { this.ancho = ancho; this.alto = alto; }
>     int area() { return ancho * alto; }
>     public static void main(String[] a) {
>         System.out.println(new Rectangulo(3, 4).area());   // 12
>         System.out.println(new Rectangulo(5, 2).area());   // 10
>     }
> }
> ```

---
## 0.8 Los 4 pilares de la POO

**La** pregunta de POO en entrevistas. Cuatro principios: **encapsulación, herencia, polimorfismo y abstracción**. Cada uno con programa completo y su salida.

### 0.8.1 Pilar 1 — Encapsulación (proteger y controlar los datos)

**Encapsulación** = esconder los datos internos y exponerlos solo de forma **controlada**: atributos **`private`** + métodos públicos **getter** (leer) y **setter** (escribir con validación).

🏠 **Analogía:** un cajero automático. No metes la mano a la bóveda (datos protegidos); interactúas por una ranura controlada (los métodos) que valida tu PIN antes de dejarte tocar el dinero.

```java
public class CuentaBancaria {
    private double saldo;                 // PRIVADO: nadie lo toca directo

    public double getSaldo() { return saldo; }          // getter: leer controlado

    public void depositar(double monto) {               // setter con validación
        if (monto > 0) saldo += monto;
    }
    public boolean retirar(double monto) {
        if (monto > 0 && monto <= saldo) { saldo -= monto; return true; }
        return false;                                   // protege la regla "no sobregiro"
    }
    public static void main(String[] args) {
        CuentaBancaria c = new CuentaBancaria();
        c.depositar(100);
        c.retirar(30);
        System.out.println(c.getSaldo());   // 70.0
        c.retirar(999);                      // rechazado (no hay fondos)
        System.out.println(c.getSaldo());   // 70.0  (intacto)
        // c.saldo = -5000;  // ❌ no compila: saldo es private
    }
}
// Salida:
// 70.0
// 70.0
```

🔧 **Modificadores de acceso** (quién ve cada cosa), de más a menos abierto:

| Modificador | Visible desde |
|---|---|
| `public` | cualquier lugar |
| `protected` | misma clase + subclases + mismo paquete |
| *(nada / default)* | solo el mismo paquete |
| `private` | solo dentro de la misma clase |

🔑 **Por qué importa:** si `saldo` fuera `public`, cualquiera haría `cuenta.saldo = -9999` y rompería las reglas del negocio. Encapsular **garantiza que los datos solo cambien de formas válidas**. Es la base del código robusto.

### 0.8.2 Pilar 2 — Herencia (reutilizar y especializar)

**Herencia** = una clase **hija** hereda atributos y métodos de una clase **padre** (con `extends`) y puede añadir o cambiar cosas. Evita duplicar lo común. Relación "**es un/una**".

```java
class Animal {
    String nombre;
    Animal(String nombre) { this.nombre = nombre; }
    void comer() { System.out.println(nombre + " está comiendo"); }
    void dormir() { System.out.println(nombre + " duerme"); }
}

class Perro extends Animal {              // Perro HEREDA de Animal
    Perro(String nombre) { super(nombre); }   // super(...) llama al constructor del padre
    void ladrar() { System.out.println(nombre + " dice ¡Guau!"); }  // usa 'nombre' heredado
}

public class DemoHerencia {
    public static void main(String[] args) {
        Perro p = new Perro("Firulais");
        p.comer();    // heredado de Animal -> Firulais está comiendo
        p.dormir();   // heredado          -> Firulais duerme
        p.ladrar();   // propio de Perro   -> Firulais dice ¡Guau!
    }
}
// Salida:
// Firulais está comiendo
// Firulais duerme
// Firulais dice ¡Guau!
```
🔧 **`super`** se refiere al **padre**: `super(...)` llama a su **constructor** (debe ir en la primera línea del constructor hijo); `super.metodo()` llama a su **versión** de un método. 🔑 En Java una clase **solo hereda de UNA** (herencia simple); para combinar capacidades se usan interfaces (§0.9).

### 0.8.3 Pilar 3 — Polimorfismo (mismo mensaje, distinto comportamiento)

**Polimorfismo** ("muchas formas") = el **mismo** método se comporta **distinto según el objeto real** que lo ejecuta. Se logra con **override (sobrescritura)**: una subclase **redefine** un método del padre.

🏠 **Analogía:** das la orden "haz tu sonido" a varios animales. El perro ladra, el gato maúlla. **Una orden, muchas respuestas.**

```java
class Animal {
    void hacerSonido() { System.out.println("(sonido genérico)"); }
}
class Perro extends Animal {
    @Override void hacerSonido() { System.out.println("¡Guau!"); }
}
class Gato extends Animal {
    @Override void hacerSonido() { System.out.println("¡Miau!"); }
}
class Vaca extends Animal {
    @Override void hacerSonido() { System.out.println("¡Muu!"); }
}

public class DemoPolimorfismo {
    public static void main(String[] args) {
        Animal[] zoo = { new Perro(), new Gato(), new Vaca() };  // todos son Animal
        for (Animal a : zoo) a.hacerSonido();   // cada uno responde a SU manera
    }
}
// Salida:
// ¡Guau!
// ¡Miau!
// ¡Muu!
```
🔑 **El poder:** tratas objetos distintos **de forma uniforme** (todos `Animal`) y cada uno responde a su modo. El código es **extensible**: agregar `Caballo` no obliga a tocar el bucle. 🔧 Java elige la versión del **objeto real** en tiempo de ejecución (*dynamic dispatch*), no la del tipo de la variable.

⚠️ **Override vs Overload** (no confundir):

| | **Override (sobrescritura)** | **Overload (sobrecarga)** |
|---|---|---|
| Qué es | redefinir un método del padre | mismo nombre, distintos parámetros |
| Dónde | en una **subclase** | en la **misma** clase |
| Firma | **igual** que la del padre | **distinta** (parámetros) |
| Relación | polimorfismo | conveniencia de nombres |

La anotación **`@Override`** marca que sobrescribes (y el compilador te avisa si te equivocas en la firma — atrapa bugs).

### 0.8.4 Pilar 4 — Abstracción (mostrar lo esencial, ocultar lo complejo)

**Abstracción** = exponer **qué** hace algo, ocultando **cómo** lo hace. Trabajas con un concepto simple sin cargar los detalles internos.

🏠 **Analogía:** manejas con volante y pedales (interfaz simple) sin saber de combustión interna (complejidad oculta). Sabes *qué* hace el pedal, no necesitas el *cómo*.

En Java la abstracción se logra con **clases abstractas** e **interfaces** (§0.9): defines **qué** métodos existen sin decir cómo, y cada implementación los resuelve a su modo.

🔧 **Encapsulación vs abstracción** (se confunden): la **encapsulación** esconde los **datos** (el saldo `private`); la **abstracción** esconde la **complejidad de la implementación** (el "cómo"). Una protege el estado; la otra simplifica el uso.

### 0.8.5 Por qué importan para SDET

🧪 Tu framework **es** POO en acción: **herencia** (una `BaseTest` con setup común que tus pruebas heredan); **encapsulación** (localizadores `private` en un Page Object); **polimorfismo** (manejar navegadores distintos con la misma interfaz `WebDriver`); **abstracción** (`WebDriver` te da `click()` sin que sepas cómo lo hace Chrome vs Firefox).

### 0.8.6 Ejercicios resueltos

**Ejercicio 1.** Nombra los 4 pilares en una frase cada uno.
> *Solución:* Encapsulación (proteger datos con `private` + getters/setters), herencia (reutilizar de una superclase con `extends`), polimorfismo (un método se comporta distinto según el objeto), abstracción (mostrar qué, ocultar cómo).

**Ejercicio 2.** Crea una clase `Termostato` que encapsule `temperatura` (privada), con un setter que solo acepte valores entre 15 y 30.
> ```java
> public class Termostato {
>     private int temperatura = 20;
>     public int getTemperatura() { return temperatura; }
>     public void setTemperatura(int t) { if (t >= 15 && t <= 30) temperatura = t; }
> }
> ```

**Ejercicio 3.** Crea `Vehiculo` con `arrancar()`, y `Moto`/`Auto` que hereden y agreguen su propio método.
> ```java
> class Vehiculo { void arrancar() { System.out.println("Arranca"); } }
> class Moto extends Vehiculo { void caballito() { System.out.println("¡Caballito!"); } }
> class Auto extends Vehiculo { void abrirCajuela() { System.out.println("Cajuela abierta"); } }
> ```

**Ejercicio 4.** Diferencia entre override y overload.
> *Solución:* Override: una subclase redefine un método del padre (misma firma) → polimorfismo. Overload: mismo nombre, distintos parámetros, en la misma clase.

**Ejercicio 5.** Crea una clase `Figura` con `dibujar()`, y `Circulo`/`Cuadrado` que la sobrescriban; recórrelas en un arreglo de `Figura`.
> ```java
> class Figura { void dibujar() { System.out.println("figura"); } }
> class Circulo extends Figura { @Override void dibujar() { System.out.println("○"); } }
> class Cuadrado extends Figura { @Override void dibujar() { System.out.println("□"); } }
> // for (Figura f : new Figura[]{new Circulo(), new Cuadrado()}) f.dibujar();  -> ○  □
> ```

**Ejercicio 6.** ¿Encapsulación vs abstracción?
> *Solución:* Encapsulación esconde los **datos** (el estado, con `private`); abstracción esconde la **complejidad de la implementación** (el cómo, con interfaces/clases abstractas).

---

## 0.9 Interfaces y clases abstractas

Ambas implementan la **abstracción**: definir **qué** debe hacerse sin decir **cómo**. Son la columna vertebral de los frameworks (incluido el tuyo de pruebas). Esta sección va extendida porque el tema es central y sutil.

### 0.9.1 El problema que resuelven

Imagina que tu código debe trabajar con muchos tipos que comparten un comportamiento — distintos métodos de pago, distintos navegadores, distintas figuras — pero **cada uno lo hace distinto**. Quieres escribir código que los use **a todos por igual**, sin atarte a uno concreto. Eso es lo que dan las interfaces y las clases abstractas: un **tipo común** que esconde las diferencias.

### 0.9.2 Interfaz (un contrato puro)

Una **interfaz** es un **contrato**: una lista de métodos que una clase **se compromete a implementar**. Se declara con `interface`; las clases la adoptan con **`implements`** y **deben** implementar sus métodos.

🏠 **Analogía:** "ser conducible" es un contrato. Cualquier vehículo que lo firme **debe** tener `arrancar()`, `acelerar()`, `frenar()` — pero cada uno los implementa a su manera. La interfaz dice *qué*, no *cómo*.

```java
interface Figura {
    double area();        // método abstracto (sin cuerpo): es el contrato
    double perimetro();
}

class Circulo implements Figura {
    double radio;
    Circulo(double radio) { this.radio = radio; }
    @Override public double area() { return Math.PI * radio * radio; }
    @Override public double perimetro() { return 2 * Math.PI * radio; }
}
class Rectangulo implements Figura {
    double ancho, alto;
    Rectangulo(double ancho, double alto) { this.ancho = ancho; this.alto = alto; }
    @Override public double area() { return ancho * alto; }
    @Override public double perimetro() { return 2 * (ancho + alto); }
}

public class DemoInterfaz {
    public static void main(String[] args) {
        Figura[] figuras = { new Circulo(2), new Rectangulo(3, 4) };
        for (Figura f : figuras)                      // las tratamos a TODAS como Figura
            System.out.printf("área=%.2f%n", f.area());
    }
}
// Salida:
// área=12.57
// área=12.00
```
🔑 **Una clase puede implementar VARIAS interfaces** (`class X implements A, B, C`), a diferencia de la herencia (una sola clase padre). Por eso las interfaces son la forma flexible de **componer capacidades**. Relación "**es capaz de / se comporta como**".

**0.9.2.1 — Qué puede tener una interfaz (más allá del contrato):**
- **Métodos abstractos:** la regla; sin cuerpo, los implementa quien firma.
- **Constantes:** los campos son `public static final` automáticamente.
- **Métodos `default` (Java 8+):** métodos **con** cuerpo que las clases heredan sin obligación de reescribir — sirven para añadir funciones a una interfaz sin romper las clases que ya la implementan:
```java
interface Saludable {
    void comer();
    default void rutina() {            // método con implementación por defecto
        System.out.println("Hago ejercicio");
        comer();
    }
}
class Persona implements Saludable {
    @Override public void comer() { System.out.println("Como verduras"); }
}
// new Persona().rutina();  ->  Hago ejercicio / Como verduras
```
- **Métodos `static`:** utilidades asociadas a la interfaz (`Comparator.naturalOrder()`).

### 0.9.3 Clase abstracta (plantilla parcial con estado)

Una **clase abstracta** está a medio terminar: puede tener **atributos con estado**, **métodos ya implementados** (comunes) y **métodos abstractos** (sin cuerpo, que las hijas deben completar). Se marca con **`abstract`** y **no se puede instanciar** (`new` directo prohibido).

```java
abstract class Empleado {
    protected String nombre;                       // estado COMPARTIDO
    Empleado(String nombre) { this.nombre = nombre; }   // constructor (sí los tiene)

    void registrarEntrada() {                      // método YA implementado (común a todos)
        System.out.println(nombre + " marcó entrada");
    }
    abstract double calcularSalario();             // ABSTRACTO: cada tipo lo define distinto
}

class EmpleadoPorHora extends Empleado {
    double horas, tarifa;
    EmpleadoPorHora(String n, double horas, double tarifa) { super(n); this.horas = horas; this.tarifa = tarifa; }
    @Override double calcularSalario() { return horas * tarifa; }
}
class EmpleadoAsalariado extends Empleado {
    double salarioMensual;
    EmpleadoAsalariado(String n, double s) { super(n); this.salarioMensual = s; }
    @Override double calcularSalario() { return salarioMensual; }
}

public class DemoAbstracta {
    public static void main(String[] args) {
        // Empleado e = new Empleado("X");  // ❌ no compila: es abstracta
        Empleado a = new EmpleadoPorHora("Ana", 160, 50);
        Empleado b = new EmpleadoAsalariado("Beto", 12000);
        a.registrarEntrada();                       // método común heredado
        System.out.println(a.nombre + ": " + a.calcularSalario());   // Ana: 8000.0
        System.out.println(b.nombre + ": " + b.calcularSalario());   // Beto: 12000.0
    }
}
// Salida:
// Ana marcó entrada
// Ana: 8000.0
// Beto: 12000.0
```
🔑 Una clase abstracta **da código y estado comunes** a una familia de clases, **obligando** a las hijas a completar las partes que varían (`calcularSalario`).

### 0.9.4 Interfaz vs clase abstracta (la tabla que debes saber)

| | **Interfaz** | **Clase abstracta** |
|---|---|---|
| Se adopta con | `implements` | `extends` |
| ¿Cuántas por clase? | **varias** | **una sola** |
| Estado (atributos) | solo constantes | **sí**, atributos normales |
| Constructor | no | **sí** |
| Métodos con código | `default`/`static` (Java 8+) | sí, libremente |
| Relación | "es capaz de" (capacidad) | "es un/una" (jerarquía/familia) |
| Úsala cuando | clases **no relacionadas** comparten una **capacidad** | familia de clases con **código y estado comunes** |

🔑 **Regla práctica:** ¿clases dispares que solo comparten un *comportamiento*? → **interfaz**. ¿Una *familia* con código y estado comunes? → **clase abstracta**. Muchas veces se **combinan**.

### 0.9.5 Combinarlas (lo normal en código real)

Una clase puede **extender una** clase abstracta **e implementar varias** interfaces a la vez:
```java
abstract class Animal { abstract void comer(); }
interface Nadador { void nadar(); }
interface Volador { void volar(); }

class Pato extends Animal implements Nadador, Volador {   // una clase + dos capacidades
    @Override void comer() { System.out.println("come semillas"); }
    @Override public void nadar() { System.out.println("nada"); }
    @Override public void volar() { System.out.println("vuela"); }
}
```
🔑 Así modelas: "un Pato **es un** Animal (jerarquía) y además **es capaz de** nadar y volar (capacidades)".

### 0.9.6 Por qué importan para SDET (ejemplo que verás a diario)

🧪 **`WebDriver` de Selenium es una INTERFAZ.** `WebDriver driver = new ChromeDriver();` usa el contrato `WebDriver` (que define `get()`, `findElement()`, `click()`…) implementado por `ChromeDriver`. Cambiar a Firefox es solo `new FirefoxDriver()`: el resto de tu código **no cambia**, porque programas **contra la interfaz, no contra la implementación**. Y una **`BasePage` abstracta** con métodos comunes (esperar, hacer clic) de la que **heredan** todos tus Page Objects es el caso de libro de clase abstracta. Polimorfismo + abstracción + interfaces, trabajando juntos en la primera línea de casi toda prueba.

### 0.9.7 Ejercicios resueltos

**Ejercicio 1.** Define una interfaz `Reproducible` con `reproducir()` y `pausar()`, e impleméntala en `Cancion`.
> ```java
> interface Reproducible { void reproducir(); void pausar(); }
> class Cancion implements Reproducible {
>     @Override public void reproducir() { System.out.println("▶ sonando"); }
>     @Override public void pausar() { System.out.println("⏸ en pausa"); }
> }
> ```

**Ejercicio 2.** ¿Por qué no se puede hacer `new` de una clase abstracta?
> *Solución:* Porque está incompleta (puede tener métodos abstractos sin cuerpo); solo se instancian sus subclases concretas que los implementan.

**Ejercicio 3.** Crea una clase abstracta `FiguraGeometrica` con un método abstracto `area()` y un método concreto `describir()`; impleméntala en `Triangulo`.
> ```java
> abstract class FiguraGeometrica {
>     abstract double area();
>     void describir() { System.out.println("Área = " + area()); }
> }
> class Triangulo extends FiguraGeometrica {
>     double base, altura;
>     Triangulo(double b, double h) { base = b; altura = h; }
>     @Override double area() { return base * altura / 2; }
> }
> // new Triangulo(4, 3).describir();  ->  Área = 6.0
> ```

**Ejercicio 4.** ¿Cuántas interfaces puede implementar una clase y de cuántas clases puede heredar?
> *Solución:* Varias interfaces; una sola clase (herencia simple).

**Ejercicio 5.** Interfaz o clase abstracta para: (a) clases no relacionadas que pueden "imprimirse"; (b) una familia de cuentas bancarias con saldo y código común.
> *Solución:* (a) interfaz (capacidad compartida entre clases dispares); (b) clase abstracta (familia con estado/código común).

**Ejercicio 6.** Crea una interfaz con un método `default`, e impleméntala en una clase que NO sobrescriba ese método; demuestra que se hereda.
> ```java
> interface Notificador {
>     void enviar(String msg);
>     default void enviarUrgente(String msg) { enviar("URGENTE: " + msg); }  // default
> }
> class Correo implements Notificador {
>     @Override public void enviar(String msg) { System.out.println("Email: " + msg); }
> }
> // new Correo().enviarUrgente("caída");  ->  Email: URGENTE: caída
> ```

**Ejercicio 7.** Modela: un `Smartphone` que **es un** `Dispositivo` (clase abstracta) y además **es capaz de** `Llamar` y `Conectar` (interfaces).
> ```java
> abstract class Dispositivo { abstract void encender(); }
> interface Llamar { void llamar(String n); }
> interface Conectar { void wifi(); }
> class Smartphone extends Dispositivo implements Llamar, Conectar {
>     @Override void encender() { System.out.println("encendido"); }
>     @Override public void llamar(String n) { System.out.println("llamando a " + n); }
>     @Override public void wifi() { System.out.println("conectado"); }
> }
> ```

---
## 0.10 Excepciones (manejo de errores)

Un programa real choca con problemas en ejecución: un dato inválido, una división entre cero, un elemento que no existe, una red caída. Las **excepciones** son el mecanismo de Java para **manejar esos errores con control**, en vez de que el programa muera de golpe.

### 0.10.1 El problema: qué pasa SIN manejo de errores

```java
public class SinManejo {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3};
        System.out.println(arr[5]);          // índice inválido
        System.out.println("Esta línea NO se ejecuta");
    }
}
// Salida (el programa MUERE):
// Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException:
//         Index 5 out of bounds for length 3
//         at SinManejo.main(SinManejo.java:4)
```
🔑 Sin manejo, una excepción **detiene** el programa y muestra un **stack trace**. 🧪 Ese stack trace que ves cuando una prueba falla **es** una excepción no atrapada; leerlo (el **tipo** de error y la **línea**) es media depuración.

### 0.10.2 Qué es una excepción y cómo se PROPAGA

🔧 Una **excepción** es un **objeto** que Java "lanza" (**throw**) cuando algo sale mal. Ese objeto **sube por la pila de llamadas** (§0.1.5) buscando quién lo atrape; si nadie lo hace, llega hasta `main` y el programa termina. Un programa que muestra la propagación:
```java
public class Propagacion {
    static void nivel3() { int x = 10 / 0; }     // aquí NACE la excepción
    static void nivel2() { nivel3(); }           // no la atrapa: la deja subir
    static void nivel1() { nivel2(); }           // tampoco
    public static void main(String[] args) {
        try {
            nivel1();
        } catch (ArithmeticException e) {        // se atrapa hasta acá arriba
            System.out.println("Atrapada en main: " + e.getMessage());
        }
    }
}
// Salida:
// Atrapada en main: / by zero
```
🔑 La excepción "burbujea" desde donde ocurre (`nivel3`) hacia arriba hasta el primer `catch` que la maneje. Por eso el *stack trace* muestra **toda la cadena** de llamadas.

### 0.10.3 `try` / `catch` y atrapar varios tipos

Envuelves el código riesgoso en `try`; si lanza, salta al `catch` que coincida:
```java
public class TryCatch {
    public static void main(String[] args) {
        try {
            int[] datos = {10, 20};
            System.out.println(datos[5]);    // lanza ArrayIndexOutOfBounds
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Índice fuera de rango");
        } catch (Exception e) {              // catch general (va AL FINAL)
            System.out.println("Otro error: " + e.getMessage());
        }
        System.out.println("El programa CONTINÚA");   // no murió
    }
}
// Salida:
// Índice fuera de rango
// El programa CONTINÚA
```
🔑 Con **varios `catch`**, van del **más específico al más general** (si pones `Exception` primero, atrapa todo y los demás quedan inalcanzables → error de compilación). El objeto `e` trae info: `e.getMessage()` (descripción), `e.printStackTrace()` (dónde ocurrió), `e.getClass()` (el tipo).

**Multi-catch (un solo bloque para varios tipos), con `|`:**
```java
try { /* ... */ }
catch (NumberFormatException | NullPointerException e) {   // dos tipos, mismo manejo
    System.out.println("Dato inválido o nulo");
}
```

### 0.10.4 `finally` y try-with-resources

**`finally`** corre **siempre** —haya o no excepción, e incluso si hay un `return`—. Ideal para **liberar recursos**:
```java
public class Finally {
    static String prueba() {
        try {
            return "desde try";
        } finally {
            System.out.println("finally SIEMPRE corre (incluso con return)");
        }
    }
    public static void main(String[] args) {
        System.out.println(prueba());
    }
}
// Salida:
// finally SIEMPRE corre (incluso con return)
// desde try
```
🔧 **try-with-resources (la forma moderna de limpiar):** si un recurso implementa `AutoCloseable` (archivos, conexiones, `Scanner`), declararlo en el `try(...)` hace que Java lo **cierre solo** al terminar, sin `finally` manual:
```java
try (Scanner sc = new Scanner(System.in)) {
    int n = sc.nextInt();
    // ... usar sc ...
}   // Java llama sc.close() automáticamente, pase lo que pase
```
🔑 Esto reemplaza al obsoleto `finalize()` para liberar recursos.

### 0.10.5 La jerarquía de excepciones (con diagrama)

🔧 Todo desciende de **`Throwable`**, que se ramifica:
```
Throwable
├── Error                         → fallos graves de la JVM; NO los manejas tú
│     OutOfMemoryError, StackOverflowError
└── Exception                     → problemas que tu programa SÍ puede manejar
      ├── (checked)               → el compilador OBLIGA a manejarlas
      │     IOException, SQLException, FileNotFoundException
      └── RuntimeException        → (unchecked) NO obligadas
            NullPointerException, ArrayIndexOutOfBoundsException,
            ArithmeticException, NumberFormatException, ClassCastException
```

### 0.10.6 Checked vs unchecked (pregunta de entrevista clásica)

- **Checked (verificadas):** el **compilador obliga** a manejarlas (con `try/catch`) o a declararlas (con `throws`). Representan problemas **externos previsibles**: archivo no encontrado, fallo de red/BD. Ej.: `IOException`.
- **Unchecked (RuntimeException):** el compilador **no** obliga. Suelen ser **bugs de programación** que deberías **prevenir**, no atrapar a ciegas: `NullPointerException`, `ArrayIndexOutOfBoundsException`, `ArithmeticException`.

🔑 Distinción mental: **checked** = "algo del mundo exterior puede fallar, anticípalo"; **unchecked** = "tu código tiene un error de lógica, arréglalo".

### 0.10.7 `throw` y `throws`

- **`throw`** — **lanza** una excepción tú mismo cuando detectas algo inválido:
```java
static void retirar(double saldo, double monto) {
    if (monto > saldo) throw new IllegalArgumentException("Fondos insuficientes");
    // ...
}
```
- **`throws`** — en la **firma** declara que un método **puede** lanzar cierta excepción (obligatorio para checked), pasando la responsabilidad a quien llame:
```java
static void leer(String ruta) throws IOException { /* ... */ }
```
⚠️ **No confundir:** `throw` (verbo, lanza **una**) vs `throws` (declara que un método **puede** lanzar). Una letra, conceptos distintos.

### 0.10.8 Crear tus propias excepciones

Extiende `RuntimeException` (unchecked) o `Exception` (checked) para errores específicos de tu dominio:
```java
class SaldoInsuficienteException extends RuntimeException {
    SaldoInsuficienteException(String msg) { super(msg); }
}

public class Cuenta {
    private double saldo = 100;
    void retirar(double monto) {
        if (monto > saldo) throw new SaldoInsuficienteException("Faltan $" + (monto - saldo));
        saldo -= monto;
    }
    public static void main(String[] args) {
        try {
            new Cuenta().retirar(150);
        } catch (SaldoInsuficienteException e) {
            System.out.println("Rechazado: " + e.getMessage());
        }
    }
}
// Salida:
// Rechazado: Faltan $50.0
```
🔑 Las excepciones propias hacen el código **legible** (`catch (SaldoInsuficienteException e)` dice exactamente qué pasó) y permiten manejar cada caso distinto.

### 0.10.9 Buenas prácticas

- **No te "comas" las excepciones:** un `catch` vacío (`catch (Exception e) {}`) oculta el error y crea bugs fantasma. Al menos regístralo.
- **Sé específico:** atrapa el tipo concreto, no `Exception` genérico, salvo que de verdad quieras todos.
- **Limpia recursos** con try-with-resources o `finally`.
- **No uses excepciones para flujo normal** (son para lo *excepcional*, no para reemplazar un `if`).

### 0.10.10 Catálogo de excepciones que verás siempre

| Excepción | La causa típica |
|---|---|
| `NullPointerException` | usar un método/campo de algo que es `null` |
| `ArrayIndexOutOfBoundsException` | índice fuera de `0..length-1` |
| `ArithmeticException` | división entera entre cero |
| `NumberFormatException` | `Integer.parseInt("abc")` (texto no numérico) |
| `ClassCastException` | castear a un tipo incompatible |
| `IllegalArgumentException` | pasar un argumento inválido a un método |
| `ConcurrentModificationException` | modificar una colección mientras la recorres |

### 0.10.11 Por qué importan para SDET

🧪 La automatización vive de excepciones: `NoSuchElementException` (no se halló un elemento), `TimeoutException` (un *wait* expiró), `StaleElementReferenceException` (el elemento cambió en el DOM). Un buen SDET las atrapa con sentido: **toma un screenshot en el `catch`**, registra evidencia, reintenta, y **cierra el navegador en el `finally`/try-with-resources**. Y las **aserciones** (`assertEquals`) lanzan `AssertionError` al fallar: por eso aparece ese tipo en los reportes.

### 0.10.12 Ejercicios resueltos

**Ejercicio 1.** Programa que pida un número y maneje el caso de que el usuario escriba texto no numérico.
> ```java
> import java.util.Scanner;
> public class LeerSeguro {
>     public static void main(String[] args) {
>         Scanner sc = new Scanner(System.in);
>         try {
>             int n = Integer.parseInt(sc.nextLine());
>             System.out.println("El doble es " + (n * 2));
>         } catch (NumberFormatException e) {
>             System.out.println("Eso no es un número");
>         }
>         sc.close();
>     }
> }
> // Con "abc" -> Eso no es un número
> ```

**Ejercicio 2.** ¿Qué imprime y en qué orden?
> ```java
> try { System.out.println("A"); throw new RuntimeException(); }
> catch (Exception e) { System.out.println("B"); }
> finally { System.out.println("C"); }
> ```
> *Solución:* `A`, `B`, `C`. Se ejecuta el try hasta el throw (A), salta al catch (B), y finally siempre corre (C).

**Ejercicio 3.** Diferencia entre `throw` y `throws`.
> *Solución:* `throw` lanza una excepción concreta en ese punto; `throws` declara en la firma que el método puede lanzar cierta excepción.

**Ejercicio 4.** Crea una excepción propia `EdadInvalidaException` y lánzala si una edad es negativa.
> ```java
> class EdadInvalidaException extends RuntimeException {
>     EdadInvalidaException(String m) { super(m); }
> }
> static void setEdad(int e) {
>     if (e < 0) throw new EdadInvalidaException("Edad negativa: " + e);
> }
> ```

**Ejercicio 5.** ¿Checked o unchecked es `NullPointerException`? ¿Qué implica?
> *Solución:* Unchecked (RuntimeException): el compilador no obliga a atraparla; suele ser un bug que se previene verificando nulos, no atrapándolo a ciegas.

**Ejercicio 6.** Reescribe este `finally` manual usando try-with-resources.
> ```java
> // Antes:
> Scanner sc = new Scanner(System.in);
> try { /* usar sc */ } finally { sc.close(); }
> // Después:
> try (Scanner sc = new Scanner(System.in)) { /* usar sc */ }  // se cierra solo
> ```

**Ejercicio 7.** ¿Por qué un `catch (Exception e) {}` vacío es peligroso?
> *Solución:* "Se come" el error sin registrarlo ni manejarlo; el programa sigue como si nada y los bugs se vuelven invisibles e imposibles de diagnosticar.

---

## 0.11 Colecciones (List, Set, Map): el puente a las estructuras de datos

Java trae el **Collections Framework**: clases listas para usar que implementan las estructuras de la Parte 2. Aquí ves **la sintaxis de Java** para manejarlas; los *internals* y cuándo elegir cada una están a fondo en los capítulos 1–9.

### 0.11.1 El mapa del framework

🔧 Casi todo cuelga de dos grandes interfaces, **`Collection`** y **`Map`**:
```
Collection (un grupo de elementos)
├── List  → ordenada, permite duplicados, acceso por índice  → ArrayList, LinkedList
├── Set   → SIN duplicados, sin orden garantizado            → HashSet, TreeSet
└── Queue → colas (FIFO)                                      → LinkedList, ArrayDeque
Map (pares clave→valor, claves únicas)                        → HashMap, TreeMap
```
🔑 Programas contra la **interfaz** y eliges la **implementación**: `List<String> x = new ArrayList<>();` (así puedes cambiar la implementación sin tocar el resto, §0.9).

### 0.11.2 `List` / `ArrayList` (secuencia ordenada que crece)

```java
import java.util.*;
public class DemoList {
    public static void main(String[] args) {
        List<String> tareas = new ArrayList<>();
        tareas.add("comprar");          // agrega al final -> [comprar]
        tareas.add("cocinar");          // -> [comprar, cocinar]
        tareas.add("limpiar");          // -> [comprar, cocinar, limpiar]

        System.out.println(tareas.get(1));        // cocinar  (acceso por índice)
        tareas.set(1, "lavar");                   // reemplaza -> [comprar, lavar, limpiar]
        tareas.remove("limpiar");                 // borra por valor -> [comprar, lavar]
        System.out.println(tareas.size());        // 2
        System.out.println(tareas.contains("comprar"));  // true
        System.out.println(tareas.indexOf("lavar"));     // 1
        for (String t : tareas) System.out.print(t + " ");  // comprar lavar
    }
}
// Salida:
// cocinar
// 2
// true
// 1
// comprar lavar
```

### 0.11.3 `Set` / `HashSet` (sin duplicados)

```java
import java.util.*;
public class DemoSet {
    public static void main(String[] args) {
        Set<Integer> ids = new HashSet<>();
        ids.add(1); ids.add(2); ids.add(2); ids.add(3);   // el segundo 2 se ignora
        System.out.println(ids.size());        // 3
        System.out.println(ids.contains(2));   // true
        boolean nuevo = ids.add(1);            // ya existía
        System.out.println(nuevo);             // false  (add devuelve false si ya estaba)
    }
}
// Salida:
// 3
// true
// false
```
🔑 Truco: `add()` devuelve `false` si el elemento ya estaba → detectar duplicados en una línea.

### 0.11.4 `Map` / `HashMap` (clave → valor)

```java
import java.util.*;
public class DemoMap {
    public static void main(String[] args) {
        Map<String, Integer> stock = new HashMap<>();
        stock.put("manzanas", 50);
        stock.put("peras", 30);
        stock.put("manzanas", 60);            // misma clave -> sobrescribe (60)

        System.out.println(stock.get("manzanas"));            // 60
        System.out.println(stock.get("uvas"));                // null (no existe)
        System.out.println(stock.getOrDefault("uvas", 0));    // 0 (evita null)
        System.out.println(stock.containsKey("peras"));       // true

        for (Map.Entry<String,Integer> e : stock.entrySet())  // recorrer pares
            System.out.println(e.getKey() + " = " + e.getValue());
    }
}
// Salida:
// 60
// null
// 0
// true
// manzanas = 60
// peras = 30
```
🔑 **`getOrDefault`** es tu mejor amigo para contar frecuencias: `mapa.put(k, mapa.getOrDefault(k, 0) + 1)`.

### 0.11.5 Recorrer colecciones (las formas)

```java
for (String t : lista) { ... }                       // List/Set: for-each
for (String clave : mapa.keySet()) { ... }           // Map: solo claves
for (int v : mapa.values()) { ... }                  // Map: solo valores
for (Map.Entry<String,Integer> e : mapa.entrySet()) {// Map: pares (lo más usado)
    e.getKey(); e.getValue();
}
```
⚠️ **No modifiques** una colección (add/remove) mientras la recorres con for-each → `ConcurrentModificationException`. Para borrar mientras recorres, usa un `Iterator` y su `it.remove()`.

### 0.11.6 Elegir la colección correcta

| Necesitas | Usa | Por qué |
|---|---|---|
| Secuencia ordenada, acceso por índice | `ArrayList` | índice O(1) |
| Evitar duplicados | `HashSet` | pertenencia O(1) |
| Asociar clave→valor | `HashMap` | búsqueda O(1) |
| Claves/elementos **ordenados** | `TreeMap`/`TreeSet` | mantienen orden (O(log n)) |
| Pila o cola | `ArrayDeque` | extremos O(1) |

### 0.11.7 Por qué importan (y nota SDET)

🔑 Estas colecciones son el **80% de lo que usarás** resolviendo algoritmos en Java: `HashMap` para frecuencias/búsquedas O(1), `HashSet` para duplicados, `ArrayList` para resultados, `ArrayDeque` para pila/cola. Dominar su sintaxis aquí hace que la Parte 3 (patrones) fluya. 🧪 En pruebas: una `List<WebElement>` de resultados, un `Map` de datos de prueba, un `Set` para verificar que no haya filas duplicadas en una tabla.

### 0.11.8 Ejercicios resueltos

**Ejercicio 1.** Cuenta cuántas veces aparece cada palabra en un arreglo de Strings.
> ```java
> String[] palabras = {"a", "b", "a", "c", "a"};
> Map<String,Integer> conteo = new HashMap<>();
> for (String p : palabras) conteo.put(p, conteo.getOrDefault(p, 0) + 1);
> System.out.println(conteo);   // {a=3, b=1, c=1}
> ```

**Ejercicio 2.** Dada una lista con repetidos, obtén los elementos únicos.
> ```java
> List<Integer> nums = Arrays.asList(1, 2, 2, 3, 3, 3);
> Set<Integer> unicos = new HashSet<>(nums);
> System.out.println(unicos);   // [1, 2, 3]
> ```

**Ejercicio 3.** Guarda nombres con su teléfono y consulta uno; maneja el caso de no existir.
> ```java
> Map<String,String> tel = new HashMap<>();
> tel.put("Ana", "555-1234");
> System.out.println(tel.getOrDefault("Luis", "sin registro"));   // sin registro
> ```

**Ejercicio 4.** ¿Por qué `List<String> x = new ArrayList<>();` en vez de `ArrayList<String> x`?
> *Solución:* Programar contra la interfaz: permite cambiar la implementación (p. ej. a `LinkedList`) sin tocar el resto del código.

**Ejercicio 5.** Recorre un `Map<String,Integer>` e imprime solo las claves cuyo valor sea mayor a 10.
> ```java
> for (Map.Entry<String,Integer> e : mapa.entrySet())
>     if (e.getValue() > 10) System.out.println(e.getKey());
> ```

**Ejercicio 6.** ¿Qué pasa si haces `lista.remove(x)` dentro de un for-each sobre esa lista, y cómo se evita?
> *Solución:* Lanza `ConcurrentModificationException`. Se evita usando un `Iterator` y su `it.remove()`, o recolectando lo que vas a borrar y borrándolo después del recorrido.

---
## 0.12 Genéricos

Ya los has usado (los `<...>` de `List<String>`). Aquí entiendes **qué son, por qué existen y cómo crear los tuyos**.

### 0.12.1 Qué son y qué problema resuelven

Los **genéricos** permiten escribir clases y métodos que funcionan con **cualquier tipo**, especificándolo entre `<>` al usarlos, con **seguridad de tipos**: el compilador garantiza que solo metas el tipo correcto.

🏠 **Analogía:** una caja **etiquetada**. `List<String>` es "una caja **solo para Strings**". Si intentas meter un número, el compilador lo rechaza **antes** de ejecutar — atrapas el error temprano, no en producción.

```java
import java.util.*;
public class SeguridadTipos {
    public static void main(String[] args) {
        List<String> nombres = new ArrayList<>();
        nombres.add("Ana");
        // nombres.add(42);            // ❌ no compila: 42 no es String
        String n = nombres.get(0);     // sin convertir: Java SABE que es String
        System.out.println(n.toUpperCase());   // ANA
    }
}
// Salida:
// ANA
```
🔧 Sin genéricos (estilo viejo), una colección guardaba `Object` y tenías que convertir a mano, con riesgo de `ClassCastException` **en ejecución**. Los genéricos mueven ese error a **compilación**, mucho más seguro.

### 0.12.2 Por qué `List<Integer>` y no `List<int>`

⚠️ Los genéricos **solo aceptan tipos de referencia (objetos)**, no primitivos. Por eso usas las versiones objeto: `Integer`, `Double`, `Character`, `Boolean`. El **autoboxing** (§0.3.8) convierte solo, así que escribes `lista.add(5)` y Java lo empaqueta a `Integer`.

### 0.12.3 Crear una clase genérica propia

Parametrizas la clase con un tipo `T` (convención: `T` tipo, `E` elemento, `K`/`V` clave/valor):
```java
public class Caja<T> {            // T = "tipo a decidir al usar"
    private T contenido;
    public void guardar(T x) { this.contenido = x; }
    public T obtener() { return contenido; }

    public static void main(String[] args) {
        Caja<String> cs = new Caja<>();
        cs.guardar("hola");
        System.out.println(cs.obtener().toUpperCase());   // HOLA

        Caja<Integer> ci = new Caja<>();
        ci.guardar(42);
        System.out.println(ci.obtener() + 1);             // 43
    }
}
// Salida:
// HOLA
// 43
```
Una clase con **dos** parámetros (clave-valor):
```java
class Par<K, V> {
    K clave; V valor;
    Par(K clave, V valor) { this.clave = clave; this.valor = valor; }
    public String toString() { return clave + "=" + valor; }
}
// new Par<String,Integer>("edad", 30)  ->  edad=30
```

### 0.12.4 Métodos genéricos

Un método puede ser genérico aunque su clase no lo sea; el `<T>` va antes del tipo de retorno:
```java
public class Utiles {
    static <T> T primero(List<T> lista) {   // funciona con cualquier tipo de lista
        return lista.get(0);
    }
    public static void main(String[] args) {
        System.out.println(primero(Arrays.asList("a", "b", "c")));   // a
        System.out.println(primero(Arrays.asList(10, 20, 30)));      // 10
    }
}
// Salida:
// a
// 10
```

### 0.12.5 Límites de tipo (bounded types)

A veces necesitas que `T` tenga ciertas capacidades. `<T extends Comparable<T>>` exige que `T` sea comparable, para poder usar `compareTo`:
```java
static <T extends Comparable<T>> T maximo(List<T> lista) {
    T mejor = lista.get(0);
    for (T x : lista) if (x.compareTo(mejor) > 0) mejor = x;
    return mejor;
}
// maximo(Arrays.asList(3, 9, 2))  ->  9   ;   maximo(Arrays.asList("a","z","m"))  ->  z
```
🔑 `extends` aquí significa "que sea (o implemente) Comparable", así el compilador permite llamar `compareTo`.

### 0.12.6 Comodines (wildcards) — nivel intermedio

`?` significa "algún tipo desconocido". Útil para métodos que **leen** de colecciones de tipo flexible:
- `List<?>` — lista de algo (no sabes de qué).
- `List<? extends Number>` — lista de Number o subtipos (Integer, Double…); ideal para **leer**.
- `List<? super Integer>` — lista de Integer o supertipos; ideal para **escribir** Integers.
```java
static double sumar(List<? extends Number> nums) {   // acepta List<Integer>, List<Double>...
    double total = 0;
    for (Number n : nums) total += n.doubleValue();
    return total;
}
```

### 0.12.7 Type erasure (dato de entrevista)

🔧 Los genéricos existen en **tiempo de compilación**; al compilar, la información de tipo se "borra" (*type erasure*) y el bytecode trabaja con `Object` más casts automáticos. Consecuencia práctica: no puedes hacer `new T[]` ni `if (x instanceof List<String>)`. No lo necesitas a diario, pero saberlo distingue.

### 0.12.8 Ejercicios resueltos

**Ejercicio 1.** ¿Qué ventaja dan los genéricos?
> *Solución:* Seguridad de tipos: el compilador impide meter el tipo equivocado y evita conversiones manuales, moviendo errores de ejecución a compilación.

**Ejercicio 2.** ¿Por qué `List<int>` no compila?
> *Solución:* Los genéricos solo aceptan tipos de referencia; hay que usar `Integer`.

**Ejercicio 3.** Crea una clase genérica `Pila<T>` con `push`, `pop` y `estaVacia`, usando una `List<T>` por dentro.
> ```java
> class Pila<T> {
>     private List<T> datos = new ArrayList<>();
>     void push(T x) { datos.add(x); }
>     T pop() { return datos.remove(datos.size() - 1); }
>     boolean estaVacia() { return datos.isEmpty(); }
> }
> // Pila<String> p = new Pila<>(); p.push("a"); p.pop();  ->  "a"
> ```

**Ejercicio 4.** Método genérico que reciba dos valores de cualquier tipo y devuelva si son iguales.
> ```java
> static <T> boolean iguales(T a, T b) { return a.equals(b); }
> // iguales("x", "x") -> true ; iguales(5, 6) -> false
> ```

**Ejercicio 5.** Método genérico con límite que devuelva el mínimo de una lista.
> ```java
> static <T extends Comparable<T>> T minimo(List<T> l) {
>     T m = l.get(0);
>     for (T x : l) if (x.compareTo(m) < 0) m = x;
>     return m;
> }
> // minimo(Arrays.asList(4, 1, 7)) -> 1
> ```

**Ejercicio 6.** ¿Qué es type erasure?
> *Solución:* Que la información de tipo genérico se elimina al compilar; el bytecode usa `Object` + casts. Por eso no puedes crear `new T[]` ni comprobar `instanceof List<String>`.

---

## 0.13 Esenciales: static, enums, equals/hashCode, inmutabilidad, Comparable, paquetes

Conceptos que aparecen seguido en código real y en entrevistas, ahora con la base de POO ya puesta.

### 0.13.1 `static` a fondo

Un miembro **`static`** existe **una vez para toda la clase**, compartido; uno de instancia, **uno por objeto**.
```java
public class Banco {
    static double tasaInteres = 0.05;     // compartida por TODAS las cuentas
    static int cuentasAbiertas = 0;       // contador global
    int numero;                           // propio de cada cuenta

    Banco() { cuentasAbiertas++; numero = cuentasAbiertas; }

    static double interesDe(double saldo) {   // método static: no usa estado de instancia
        return saldo * tasaInteres;
    }
    public static void main(String[] args) {
        new Banco(); new Banco();
        System.out.println(Banco.cuentasAbiertas);   // 2  (por la CLASE)
        System.out.println(Banco.interesDe(1000));   // 50.0
    }
}
// Salida:
// 2
// 50.0
```
🔑 Usa `static` para **constantes** (`static final`), **utilidades** que no dependen de un objeto (`Math.max`) y **contadores/estado compartido**. ⚠️ Un método `static` **no** puede usar `this` ni atributos de instancia (no hay objeto).

### 0.13.2 Enums (conjunto fijo de valores, con superpoderes)

Un **enum** define un tipo con un conjunto **cerrado** de valores con nombre. Más seguro que números o strings sueltos, y puede tener **atributos y métodos**:
```java
enum Planeta {
    TIERRA(9.81), MARTE(3.71), JUPITER(24.79);   // cada valor con su gravedad

    private final double gravedad;
    Planeta(double g) { this.gravedad = g; }      // constructor del enum
    double peso(double masa) { return masa * gravedad; }
}
public class DemoEnum {
    public static void main(String[] args) {
        Planeta p = Planeta.MARTE;
        System.out.println(p);                     // MARTE
        System.out.printf("Pesas %.1f N en Marte%n", p.peso(70));   // 259.7 N
        for (Planeta x : Planeta.values())         // recorrer todos los valores
            System.out.println(x + " g=" + x.gravedad);
    }
}
// Salida:
// MARTE
// Pesas 259.7 N en Marte
// TIERRA g=9.81
// MARTE g=3.71
// JUPITER g=24.79
```
🔑 Ventaja: el compilador **solo permite** los valores definidos. Se usan genial en `switch`. 🧪 En pruebas: `enum Ambiente { DEV, QA, PROD }`, `enum Navegador { CHROME, FIREFOX }`.

### 0.13.3 `equals()` y `hashCode()` (la pareja inseparable), con demostración

🔧 Por defecto `equals()` compara **referencias** (como `==`). Para que dos objetos **distintos con el mismo contenido** sean "iguales", sobrescribes `equals()` — y **siempre junto a `hashCode()`**.
```java
import java.util.*;
public class Persona {
    String nombre; int id;
    Persona(String nombre, int id) { this.nombre = nombre; this.id = id; }

    @Override public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Persona)) return false;
        return id == ((Persona) o).id;           // iguales si mismo id
    }
    @Override public int hashCode() { return Integer.hashCode(id); }  // consistente con equals

    public static void main(String[] args) {
        Persona a = new Persona("Ana", 1);
        Persona b = new Persona("Ana B.", 1);    // distinto nombre, MISMO id
        System.out.println(a.equals(b));         // true (mismo id)

        Set<Persona> set = new HashSet<>();
        set.add(a); set.add(b);                  // b se considera duplicado de a
        System.out.println(set.size());          // 1
    }
}
// Salida:
// true
// 1
```
🔑 **La regla de oro:** si `a.equals(b)`, entonces `a.hashCode() == b.hashCode()`. **Por qué:** `HashSet`/`HashMap` usan `hashCode` para la cubeta y `equals` para confirmar (cap. 5). Inconsistentes → "pierden" objetos o crean duplicados lógicos. Los IDE autogeneran ambos; `String` e `Integer` ya los traen bien (por eso son claves perfectas).

### 0.13.4 Inmutabilidad y `final`

Un objeto **inmutable** no cambia tras crearse (como `String`). Se logra con atributos `private final` y **sin setters**:
```java
public final class Punto {        // final en la CLASE: nadie puede heredar
    private final int x, y;        // final en los ATRIBUTOS: no cambian
    public Punto(int x, int y) { this.x = x; this.y = y; }
    public int getX() { return x; }
    public int getY() { return y; }
    // sin setters: una vez creado, es inmutable
}
```
🔑 **`final`** según dónde: en **variable** → no reasignable; en **método** → no sobrescribible; en **clase** → no heredable. Ventajas de la inmutabilidad: segura de compartir (nadie la altera por sorpresa), segura entre hilos, y confiable como clave de `Map`.

### 0.13.5 `Comparable` y `Comparator` (ordenar tus objetos)

Para ordenar objetos propios necesitas decir **cómo** se comparan:
- **`Comparable`** — el objeto define su orden **natural** con `compareTo` (devuelve negativo/cero/positivo):
```java
class Producto implements Comparable<Producto> {
    String nombre; double precio;
    Producto(String n, double p) { nombre = n; precio = p; }
    @Override public int compareTo(Producto o) { return Double.compare(this.precio, o.precio); }
    public String toString() { return nombre + "($" + precio + ")"; }
}
// List<Producto> l = ...; Collections.sort(l);   // ordena por precio (orden natural)
```
- **`Comparator`** — un orden **externo y alternativo**, útil para ordenar de varias formas:
```java
List<Producto> l = new ArrayList<>(List.of(
    new Producto("Café", 45), new Producto("Té", 30), new Producto("Agua", 15)));
l.sort(Comparator.comparing(p -> p.nombre));            // por nombre
l.sort(Comparator.comparingDouble((Producto p) -> p.precio).reversed());  // por precio desc
System.out.println(l);   // [Café($45.0), Té($30.0), Agua($15.0)]
```
🔑 `compareTo`/`compare` devuelven: **negativo** si "este" va antes, **0** si igual, **positivo** si va después. Es la base de cómo se ordenan colecciones de objetos.

### 0.13.6 Paquetes e imports

Un **paquete** agrupa clases relacionadas y evita choques de nombres. **`import`** trae una clase de otro paquete:
```java
package com.miempresa.pruebas;     // 1ª línea: a qué paquete pertenece
import java.util.ArrayList;        // traer una clase
import java.util.*;                // traer todo un paquete (comodín)
```
🧪 En tu framework: `import org.openqa.selenium.WebDriver;`, `import org.junit.jupiter.api.Test;`.

### 0.13.7 Ejercicios resueltos

**Ejercicio 1.** ¿Cuándo conviene `static`?
> *Solución:* Cuando algo no depende del estado de un objeto: utilidades, constantes, contadores/estado compartido. Se accede por la clase.

**Ejercicio 2.** Crea un enum `Talla { CH, M, G }` con un atributo `letra` y un método que lo devuelva.
> ```java
> enum Talla {
>     CH("S"), M("M"), G("L");
>     private final String letra;
>     Talla(String l) { letra = l; }
>     String getLetra() { return letra; }
> }
> // Talla.CH.getLetra()  ->  S
> ```

**Ejercicio 3.** ¿Por qué hay que sobrescribir `equals` y `hashCode` juntos?
> *Solución:* Las colecciones hash usan `hashCode` para la cubeta y `equals` para confirmar; inconsistentes, "pierden" objetos o crean duplicados lógicos.

**Ejercicio 4.** Haz que dos `Persona` con el mismo `id` se consideren iguales y no se dupliquen en un `HashSet`.
> *Solución:* Sobrescribir `equals` (comparando `id`) y `hashCode` (`Integer.hashCode(id)`), como en §0.13.3 → el `HashSet` tendrá tamaño 1.

**Ejercicio 5.** Ordena una lista de `Producto` por precio ascendente y luego por nombre.
> ```java
> lista.sort(Comparator.comparingDouble((Producto p) -> p.precio));   // por precio
> lista.sort(Comparator.comparing(p -> p.nombre));                    // por nombre
> ```

**Ejercicio 6.** ¿Qué hace `final` en una variable, un método y una clase?
> *Solución:* Variable → no se reasigna; método → no se sobrescribe; clase → no se hereda de ella.

**Ejercicio 7.** ¿Qué devuelve `compareTo` y qué significa cada caso?
> *Solución:* Un entero: negativo (este va antes), 0 (iguales), positivo (este va después). Define el orden al ordenar.

---
## 0.14 Java aplicado a frameworks de prueba (cierre SDET)

Aquí se junta **todo** lo del Capítulo 0 en lo que harás como SDET: escribir pruebas automatizadas. Cada concepto de Java tiene su lugar.

### 0.14.1 JUnit / TestNG: los frameworks de prueba

Una **prueba automatizada** es un **método** (§0.6) que ejecuta una acción y **verifica** un resultado esperado. Los frameworks **JUnit** y **TestNG** dan la estructura para escribir y correr esas pruebas. Una clase de prueba es una clase normal cuyos métodos están marcados con anotaciones.

### 0.14.2 Anotaciones (`@`): metadatos que guían al framework

Una **anotación** es una etiqueta que empieza con `@` y le dice al framework cómo tratar un método o clase. Las que usarás a diario:
```java
import org.junit.jupiter.api.*;

class LoginTest {
    @BeforeEach                       // corre ANTES de cada prueba (preparar)
    void setup() { /* abrir navegador */ }

    @Test                             // marca este método como una PRUEBA
    void loginConCredencialesValidas() {
        // 1. acción   2. verificación (aserción)
    }

    @AfterEach                        // corre DESPUÉS de cada prueba (limpiar)
    void teardown() { /* cerrar navegador */ }
}
```
🔑 `@Test` es la esencial; `@BeforeEach`/`@AfterEach` (en TestNG: `@BeforeMethod`/`@AfterMethod`) manejan preparación y limpieza — justo donde usas el `finally`-style de liberar recursos.

### 0.14.3 Aserciones: el corazón de una prueba

Una **aserción** verifica que la realidad coincide con lo esperado; si no, **falla la prueba** (lanza `AssertionError`, §0.10).
```java
import static org.junit.jupiter.api.Assertions.*;

assertEquals("Bienvenido", titulo);     // ¿son iguales? (usa .equals internamente)
assertTrue(boton.isEnabled());          // ¿es verdadero?
assertNotNull(usuario);                 // ¿no es null?
```
⚠️ Aquí paga entender `==` vs `.equals()` (§0.4.3): `assertEquals` compara **contenido** con `.equals()`. Por eso comparar Strings mal escrito da falsos resultados.

### 0.14.4 Page Object Model (POM): POO aplicada a pruebas

El **POM** es el patrón estándar: una **clase por página** (§0.7) que **encapsula** (§0.8) los elementos y acciones de esa página. Las pruebas usan esos métodos, sin conocer los detalles internos (abstracción):
```java
public class LoginPage {
    private WebDriver driver;                          // encapsulado (private)
    private By campoUsuario = By.id("user");           // localizadores privados
    private By campoClave = By.id("pass");

    public LoginPage(WebDriver driver) { this.driver = driver; }   // constructor

    public HomePage iniciarSesion(String u, String c) {            // acción de alto nivel
        driver.findElement(campoUsuario).sendKeys(u);
        driver.findElement(campoClave).sendKeys(c);
        driver.findElement(By.id("login")).click();
        return new HomePage(driver);                                // devuelve la siguiente página
    }
}
```
🔑 Mira cuántos pilares aparecen: **clase/objeto**, **constructor**, **this**, **encapsulación** (private), **métodos** que devuelven objetos. El POM **es** el Capítulo 0 en acción.

### 0.14.5 WebDriver y RestAssured (interfaces y herencia en vivo)

🧪 **`WebDriver`** es una **interfaz** (§0.9): `WebDriver driver = new ChromeDriver();` programa contra el contrato, no contra Chrome. Una **`BaseTest`** con el setup común que tus clases de prueba **heredan** (§0.8) evita repetir código. Para **APIs**, **RestAssured** usa Java para enviar peticiones HTTP y verificar respuestas (`given().when().get("/users").then().statusCode(200)`). Todo es Java: objetos, métodos, excepciones, colecciones (una `List<WebElement>` de resultados).

### 0.14.6 El mapa completo: cada concepto de Java → su uso en pruebas

| Concepto de Java | Dónde lo usas como SDET |
|---|---|
| Clases y objetos (§0.7) | Cada Page Object, cada clase de prueba |
| Encapsulación (§0.8) | Localizadores `private` en los Page Objects |
| Herencia (§0.8) | `BaseTest` con setup común |
| Polimorfismo + interfaces (§0.8–0.9) | `WebDriver` para distintos navegadores |
| Métodos (§0.6) | Cada caso de prueba y cada helper |
| Excepciones (§0.10) | Manejar `NoSuchElement`/`Timeout`, evidencias |
| Colecciones (§0.11) | Listas de elementos, datos de prueba |
| Estructuras de control (§0.5) | Recorrer resultados, validar condiciones |

### 0.14.7 Práctica, con respuestas

**P1.** ¿Qué hace la anotación `@Test`?
> Marca un método como una prueba que el framework (JUnit/TestNG) debe ejecutar.
**P2.** ¿Qué es una aserción y qué pasa si falla?
> Verifica que el resultado real coincide con el esperado; si no, falla la prueba lanzando un AssertionError.
**P3.** ¿Qué pilares de la POO usa un Page Object?
> Clases/objetos, encapsulación (localizadores private), y se apoya en polimorfismo/abstracción vía WebDriver; con herencia en una BaseTest.
**P4.** ¿Por qué `WebDriver driver = new ChromeDriver();` es buen diseño?
> Programa contra la interfaz WebDriver; cambiar de navegador no rompe el resto del código.
**P5.** ¿Dónde usarías `@BeforeEach` y `@AfterEach`?
> Preparar antes de cada prueba (abrir navegador) y limpiar después (cerrarlo).

---

## 0.15 Lambdas y Streams (Java moderno)

Introducidas en **Java 8**, las lambdas y los streams cambiaron cómo se escribe Java. Son **muy** preguntadas en entrevistas de Java moderno y aparecen en frameworks de prueba. Eran un hueco del manual; aquí van a fondo.

### 0.15.1 El problema: pasar "comportamiento", no solo datos

Hasta ahora pasabas **datos** a los métodos (un `int`, un `String`). ¿Y si quisieras pasar **una acción** — "qué hacer con cada elemento"? Antes había que crear una clase entera o una clase anónima, verboso. Las **lambdas** permiten pasar una **función** de forma corta.

### 0.15.2 Qué es una lambda

Una **lambda** es una **función anónima** (sin nombre) que escribes en línea. Sintaxis: `(parámetros) -> { cuerpo }`.
```java
import java.util.*;
public class DemoLambda {
    public static void main(String[] args) {
        List<String> nombres = new ArrayList<>(List.of("Carlos", "Ana", "Beto"));

        // Antes de Java 8 (clase anónima, verboso):
        nombres.sort(new Comparator<String>() {
            @Override public int compare(String a, String b) { return a.length() - b.length(); }
        });

        // Con lambda (lo mismo, breve):
        nombres.sort((a, b) -> a.length() - b.length());   // ordena por longitud
        System.out.println(nombres);   // [Ana, Beto, Carlos]

        // for-each con lambda:
        nombres.forEach(n -> System.out.println("Hola " + n));
    }
}
// Salida:
// [Ana, Beto, Carlos]
// Hola Ana
// Hola Beto
// Hola Carlos
```
🔑 La lambda `(a, b) -> a.length() - b.length()` **es** la implementación del método `compare` de `Comparator`, escrita en una línea. Variantes de sintaxis: sin parámetros `() -> ...`; un parámetro `x -> ...` (paréntesis opcionales); cuerpo con varias líneas `(x) -> { ...; return y; }`.

### 0.15.3 Interfaces funcionales (lo que hace posible la lambda)

🔧 Una lambda solo funciona donde se espera una **interfaz funcional**: una interfaz con **un solo método abstracto**. La lambda **es** la implementación de ese método. Las más usadas (paquete `java.util.function`):

| Interfaz | Método | Recibe → devuelve | Ejemplo de lambda |
|---|---|---|---|
| `Predicate<T>` | `test` | T → boolean | `x -> x > 0` |
| `Function<T,R>` | `apply` | T → R | `s -> s.length()` |
| `Consumer<T>` | `accept` | T → (nada) | `x -> System.out.println(x)` |
| `Supplier<T>` | `get` | (nada) → T | `() -> new Random().nextInt()` |
| `Comparator<T>` | `compare` | (T,T) → int | `(a,b) -> a - b` |

```java
import java.util.function.*;
public class Funcionales {
    public static void main(String[] args) {
        Predicate<Integer> esPar = n -> n % 2 == 0;
        Function<String, Integer> largo = s -> s.length();
        Consumer<String> imprime = s -> System.out.println("-> " + s);

        System.out.println(esPar.test(4));     // true
        System.out.println(largo.apply("hola"));// 4
        imprime.accept("dato");                 // -> dato
    }
}
// Salida:
// true
// 4
// -> dato
```

### 0.15.4 Referencias a métodos (`::`)

Cuando una lambda solo **llama a un método existente**, puedes acortarla con `::`:
```java
List<String> l = List.of("b", "a", "c");
l.forEach(System.out::println);          // equivale a  x -> System.out.println(x)
l.stream().map(String::toUpperCase);     // equivale a  s -> s.toUpperCase()
```
🔑 `Clase::metodo` o `objeto::metodo` es azúcar sintáctica para una lambda que solo redirige a ese método.

### 0.15.5 Streams: procesar colecciones como una tubería

Un **Stream** es una **secuencia de elementos** sobre la que aplicas operaciones en **cadena** (estilo tubería), de forma declarativa: dices **qué** quieres, no **cómo** recorrer. Un stream tiene tres partes:
1. **Fuente:** de dónde salen los datos (`lista.stream()`).
2. **Operaciones intermedias:** transforman y devuelven otro stream (`filter`, `map`, `sorted`, `distinct`, `limit`). Son **perezosas** (no hacen nada hasta el final).
3. **Operación terminal:** produce el resultado y dispara todo (`collect`, `forEach`, `count`, `reduce`, `sum`).

```java
import java.util.*;
import java.util.stream.*;
public class DemoStream {
    public static void main(String[] args) {
        List<Integer> nums = List.of(1, 2, 3, 4, 5, 6);

        List<Integer> resultado = nums.stream()        // 1. fuente
            .filter(n -> n % 2 == 0)                   // 2. quédate los pares -> 2,4,6
            .map(n -> n * n)                           // 2. eleva al cuadrado -> 4,16,36
            .collect(Collectors.toList());             // 3. terminal: recoge en lista

        System.out.println(resultado);   // [4, 16, 36]
    }
}
// Salida:
// [4, 16, 36]
```
🏠 **Analogía:** una **línea de producción**. Los datos entran por un extremo (fuente), pasan por estaciones que filtran y transforman (operaciones intermedias) y salen como producto terminado (operación terminal).

### 0.15.6 Las operaciones de stream más usadas

| Operación | Tipo | Hace |
|---|---|---|
| `filter(pred)` | intermedia | conserva los que cumplen la condición |
| `map(fn)` | intermedia | transforma cada elemento |
| `sorted()` | intermedia | ordena |
| `distinct()` | intermedia | quita duplicados |
| `limit(n)` | intermedia | toma los primeros n |
| `collect(...)` | terminal | recoge en lista/set/map |
| `forEach(acc)` | terminal | hace algo con cada uno |
| `count()` | terminal | cuántos hay |
| `reduce(...)` | terminal | combina todo en un valor |
| `anyMatch/allMatch` | terminal | ¿alguno/todos cumplen? |

Más ejemplos con su salida:
```java
import java.util.*;
import java.util.stream.*;
public class StreamEjemplos {
    public static void main(String[] args) {
        List<String> palabras = List.of("manzana", "pera", "kiwi", "manzana", "uva");

        // 1) Contar cuántas tienen más de 4 letras:
        long largas = palabras.stream().filter(p -> p.length() > 4).count();
        System.out.println(largas);   // 2  (manzana, manzana)

        // 2) Únicas, en mayúsculas, ordenadas:
        List<String> r = palabras.stream()
            .distinct().map(String::toUpperCase).sorted()
            .collect(Collectors.toList());
        System.out.println(r);   // [KIWI, MANZANA, PERA, UVA]

        // 3) Suma de una lista de números con reduce:
        int suma = Stream.of(1, 2, 3, 4).reduce(0, (a, b) -> a + b);
        System.out.println(suma);   // 10

        // 4) ¿Alguna empieza con 'k'?
        System.out.println(palabras.stream().anyMatch(p -> p.startsWith("k")));   // true
    }
}
// Salida:
// 2
// [KIWI, MANZANA, PERA, UVA]
// 10
// true
```

### 0.15.7 Streams vs bucles (cuándo cada uno)

🔑 Los streams brillan para **transformar/filtrar/agregar** colecciones de forma legible y declarativa. Un **bucle** sigue siendo mejor cuando necesitas índices, modificar en su lugar, o lógica con muchos pasos y efectos secundarios. ⚠️ No abuses: un stream con 6 operaciones encadenadas puede ser **menos** legible que un `for` claro. Usa el que comunique mejor la intención.

### 0.15.8 Por qué importan para SDET

🧪 En automatización las verás seguido: las **esperas explícitas** de Selenium usan lambdas (`wait.until(d -> d.findElement(...).isDisplayed())`); y procesar una `List<WebElement>` con streams es natural — por ejemplo, extraer los textos de todas las filas de una tabla:
```java
List<String> textos = filas.stream()
    .map(WebElement::getText)
    .filter(t -> !t.isEmpty())
    .collect(Collectors.toList());
```

### 0.15.9 Ejercicios resueltos

**Ejercicio 1.** Con una lambda, ordena una lista de Strings por longitud.
> ```java
> lista.sort((a, b) -> a.length() - b.length());
> ```

**Ejercicio 2.** Usando streams, obtén la lista de los cuadrados de los números impares de `[1..6]`.
> ```java
> List<Integer> r = Stream.of(1,2,3,4,5,6)
>     .filter(n -> n % 2 != 0).map(n -> n * n).collect(Collectors.toList());
> // [1, 9, 25]
> ```

**Ejercicio 3.** Cuenta cuántas palabras de una lista tienen más de 3 letras (con stream).
> ```java
> long c = palabras.stream().filter(p -> p.length() > 3).count();
> ```

**Ejercicio 4.** Suma todos los elementos de `List<Integer> nums` usando `reduce`.
> ```java
> int suma = nums.stream().reduce(0, Integer::sum);
> ```

**Ejercicio 5.** Convierte una lista de nombres a MAYÚSCULAS, sin duplicados y ordenada.
> ```java
> List<String> r = nombres.stream().map(String::toUpperCase).distinct().sorted()
>     .collect(Collectors.toList());
> ```

**Ejercicio 6.** Define un `Predicate<Integer>` que diga si un número es positivo y úsalo.
> ```java
> Predicate<Integer> esPositivo = n -> n > 0;
> System.out.println(esPositivo.test(-3));   // false
> ```

**Ejercicio 7.** ¿Qué es una interfaz funcional y qué relación tiene con las lambdas?
> *Solución:* Una interfaz con **un solo método abstracto**; una lambda **es** la implementación de ese único método, escrita en línea.

---
> ✅ **Fin del Capítulo 0 — Java desde cero.** Con esto tienes la base completa: desde qué es Java y la JVM, pasando por variables, control, métodos y los 4 pilares de la POO, hasta excepciones, colecciones, genéricos, lambdas/streams y cómo todo se aplica a tu trabajo de automatización. **Ahora sí puedes entrar a la Parte 1 (Big-O) y al resto del manual leyendo el código sin perderte.**

---
# PARTE 1 — BIG-O DESDE CERO ABSOLUTO

> Esta es la parte que pediste que nadie te ha explicado bien. Vamos a construirla ladrillo por ladrillo, con números reales. Al final vas a *sentir* lo que significa cada complejidad, no solo recitarla. No te saltes nada de aquí.

## 1.1 El problema que Big-O resuelve

Imagina dos programadores. Los dos escriben un programa que busca un nombre en una lista de clientes. Con una lista de 10 clientes, ambos programas responden al instante; parecen iguales de buenos. Pero la empresa crece a **50 millones de clientes**. El programa de uno sigue respondiendo en una fracción de segundo. El del otro **tarda 8 horas** y tira el servidor.

¿Cómo pudimos saber esto **sin esperar a tener 50 millones de clientes**? Ahí entra Big-O. **Big-O es una forma de predecir cómo se comportará un algoritmo cuando los datos crezcan**, mirando solo su estructura, sin necesidad de correrlo con datos gigantes.

🏠 **Analogía:** es como evaluar dos rutas para ir al trabajo. Hoy, sin tráfico, las dos tardan 20 minutos. Pero una ruta tiene 8 semáforos y la otra es una autopista directa. No necesitas un día de tráfico pesado para saber **cuál se va a colapsar en hora pico**: lo deduces de su *estructura*. Big-O mira la estructura del algoritmo y te dice cuál se colapsa cuando llega el "tráfico" (datos grandes).

## 1.2 No contamos segundos: contamos pasos

Aquí está la idea que destraba todo, y casi nadie la dice con claridad:

**Big-O NO mide tiempo en segundos.** ¿Por qué no? Porque los segundos dependen de la máquina: tu laptop vieja vs. un servidor nuevo darían números distintos para el *mismo* algoritmo. Eso no sirve para comparar algoritmos de forma objetiva.

En lugar de segundos, **contamos cuántos "pasos" (operaciones) ejecuta el algoritmo, y cómo ese número crece según el tamaño de la entrada.** Al tamaño de la entrada lo llamamos **`n`**.

Veámoslo con código concreto. Aquí buscamos un número en un arreglo, uno por uno:

```java
public static boolean contiene(int[] arr, int objetivo) {
    for (int i = 0; i < arr.length; i++) {   // se repite n veces
        if (arr[i] == objetivo) {            // 1 comparación por vuelta
            return true;
        }
    }
    return false;
}
```

¿Cuántos "pasos" hace? Depende del tamaño del arreglo. Contemos la operación importante (la comparación `arr[i] == objetivo`):
- Si el arreglo tiene **10** elementos → en el peor caso, **10** comparaciones.
- Si tiene **1,000** → **1,000** comparaciones.
- Si tiene **`n`** → **`n`** comparaciones.

El número de pasos **crece en proporción directa a `n`**. Eso es lo que escribimos como **O(n)** y leemos "orden de n" o "lineal".

> 💡 **El "peor caso".** Big-O normalmente describe el **peor caso**, porque es la garantía que nos importa: "pase lo que pase, no será peor que esto". En el ejemplo, el peor caso es que el número esté al final (o no esté), forzando recorrer todo.

✍️ **Traza a mano.** Toma `arr = [4, 8, 15, 16, 23]` y `objetivo = 23`. Cuenta: comparas con 4 (no), 8 (no), 15 (no), 16 (no), 23 (¡sí!). Fueron **5** comparaciones para `n = 5`. Si el objetivo fuera 42 (no está), también 5. Eso es O(n): pasos ≈ n.

## 1.3 La tabla que lo cambia todo

Aquí es donde Big-O deja de ser abstracto. Esta tabla muestra **cuántos pasos** hace cada complejidad para distintos tamaños de entrada. Léela despacio; es lo más importante de toda la Parte 1.

Supón que cada paso tarda 1 microsegundo (0.000001 s). Veamos cuánto tarda cada complejidad:

| n (tamaño) | O(1) | O(log n) | O(n) | O(n log n) | O(n²) | O(2ⁿ) |
|---|---|---|---|---|---|---|
| **10** | 1 paso | ~3 | 10 | ~33 | 100 | 1,024 |
| **100** | 1 paso | ~7 | 100 | ~664 | 10,000 | un número de 30 dígitos |
| **1,000** | 1 paso | ~10 | 1,000 | ~9,966 | 1,000,000 | imposible |
| **1,000,000** | 1 paso | ~20 | 1 millón | ~20 millones | **1 billón** (10¹²) | imposible |

Traducido a tiempo real para n = 1,000,000:
- **O(1):** 1 microsegundo. Instantáneo.
- **O(log n):** ~20 microsegundos. Instantáneo.
- **O(n):** ~1 segundo. Bien.
- **O(n log n):** ~20 segundos. Aceptable.
- **O(n²):** ~**11.5 días**. Tu programa "se colgó".
- **O(2ⁿ):** más que la edad del universo. Literalmente nunca termina.

> 🔑 **Lo que debes sentir al ver esto:** la diferencia entre O(n) y O(n²) **no es "el doble de lento"**. Para datos grandes es la diferencia entre **1 segundo y 11 días**. Por eso en una entrevista, cuando logras bajar una solución de O(n²) a O(n), el entrevistador sonríe: acabas de convertir un programa inservible en uno excelente. **Ese es, literalmente, el juego de la mayoría de los problemas de entrevista.**

🏠 **Analogía de los logaritmos (para que O(log n) no te asuste).** "Log" suena a matemáticas feas, pero la idea es simple: **¿cuántas veces puedo partir n a la mitad hasta llegar a 1?**. Parte 1000 → 500 → 250 → 125 → 62 → 31 → 15 → 7 → 3 → 1. Fueron ~10 pasos. Para un millón, ~20 pasos. **Cada vez que un algoritmo "descarta la mitad" en cada paso, es O(log n)**, y es asombrosamente rápido: duplicar los datos solo añade *un* paso. Por eso buscar en un directorio telefónico ordenado abriendo por la mitad es tan veloz.

## 1.4 Las siete complejidades, una por una

Ahora cada clase con su definición, analogía, código y cómo reconocerla.

### O(1) — Constante: "el costo no cambia"

El algoritmo hace **el mismo número de pasos sin importar cuán grande sea la entrada**.

```java
int primero = arr[0];          // acceder a una posición: 1 paso, siempre
boolean vacio = lista.isEmpty();
int valor = mapa.get("clave"); // un HashMap busca en O(1)
```

🏠 **Analogía:** abrir tu casa con la llave correcta. No importa si tu calle tiene 5 casas o 5,000; meter *tu* llave en *tu* cerradura toma lo mismo.

**Cómo reconocerlo:** acceso directo por índice o por clave, operaciones aritméticas simples, sin bucles que dependan de `n`.

### O(log n) — Logarítmica: "descarta la mitad"

Cada paso **elimina la mitad** de los datos restantes. Brutalmente eficiente.

```java
// Búsqueda binaria (lo veremos a fondo en la Parte 3)
while (izq <= der) {
    int medio = (izq + der) / 2;
    if (arr[medio] == objetivo) return medio;
    else if (arr[medio] < objetivo) izq = medio + 1;  // descarta mitad izquierda
    else der = medio - 1;                              // descarta mitad derecha
}
```

🏠 **Analogía:** adivinar un número del 1 al 100. Si preguntas "¿es mayor que 50?" y partes el rango cada vez, llegas en ~7 intentos, no 100.

**Cómo reconocerlo:** "ordenado" + búsqueda, o cualquier cosa donde en cada paso **partes el problema a la mitad**.

### O(n) — Lineal: "recorre una vez"

Los pasos crecen en proporción directa a `n`. Un solo bucle sobre la entrada.

```java
int suma = 0;
for (int x : arr) {   // n vueltas
    suma += x;
}
```

🏠 **Analogía:** leer un libro página por página. 200 páginas = el doble de trabajo que 100.

**Cómo reconocerlo:** un bucle que recorre la entrada una vez.

### O(n log n) — "lo mejor para ordenar"

Un bucle lineal que en cada vuelta hace algo logarítmico, o los algoritmos de ordenamiento eficientes.

```java
Arrays.sort(arr);   // los métodos de ordenamiento de Java son O(n log n)
```

🔑 **Clave de entrevista:** **no se puede ordenar comparando elementos más rápido que O(n log n)**. Si tu solución empieza por `sort(...)`, su piso de complejidad es O(n log n). A veces vale la pena (ordenar simplifica el problema); a veces el entrevistador quiere que evites ordenar para llegar a O(n).

### O(n²) — Cuadrática: "todos contra todos"

Un bucle **dentro** de otro, ambos sobre `n`. El número de pasos es n × n.

```java
for (int i = 0; i < n; i++)        // n veces
    for (int j = 0; j < n; j++)    // n veces cada una -> n*n
        System.out.println(arr[i] + arr[j]);
```

🏠 **Analogía:** en una fiesta de `n` personas, que **cada quien salude a cada quien**. Con 10 personas son ~100 saludos; con 100, ~10,000. Crece feo.

**Cómo reconocerlo:** bucles anidados sobre la misma entrada; "comparar todos los pares". ⚠️ **Esta es la complejidad que más vas a querer eliminar.** Cuando la veas, pregúntate: *¿puedo cambiar el bucle interno por un HashMap (→ O(n)) o por dos punteros sobre datos ordenados (→ O(n log n))?*

### O(2ⁿ) — Exponencial: "explota"

Los pasos se **duplican** cada vez que `n` crece en 1. Casi siempre señal de recursión que recalcula lo mismo.

```java
// Fibonacci recursivo ingenuo: recalcula los mismos valores millones de veces
public static int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);   // dos llamadas por nivel -> explosión
}
```

🏠 **Analogía:** un rumor donde cada persona se lo cuenta a 2, que se lo cuentan a 2… El total se dispara. `fib(50)` ingenuo hace ~mil millones de llamadas. **Casi siempre se puede arreglar** (con memoización → O(n), lo verás en DP).

### O(n!) — Factorial: "todas las ordenaciones"

El peor de todos. Aparece al generar **todas las permutaciones**. n=10 ya da 3.6 millones; n=15 da un billón. Solo viable para entradas diminutas.

## 1.5 Las tres reglas para calcular Big-O

Con estas tres reglas calculas la Big-O de casi cualquier código. Cada una con su porqué y ejemplos.

### Regla 1 — Cuenta los bucles según su anidamiento

- Sin bucles (o bucles de tamaño fijo) → **O(1)**.
- Un bucle sobre `n` → **O(n)**.
- Dos bucles anidados sobre `n` → **O(n²)**. Tres → **O(n³)**.
- Un bucle que parte el rango a la mitad → **O(log n)**.

```java
// Ejemplo A
for (int i = 0; i < n; i++) { ... }          // O(n)

// Ejemplo B
for (int i = 0; i < n; i++)
    for (int j = 0; j < n; j++) { ... }       // O(n²)

// Ejemplo C — ¡cuidado! bucles SEPARADOS, no anidados
for (int i = 0; i < n; i++) { ... }          // O(n)
for (int j = 0; j < n; j++) { ... }          // O(n)
// Total: O(n) + O(n) = O(2n) = O(n)  (ver Regla 2)
```

⚠️ **Trampa común:** ver dos bucles y decir "O(n²)" automáticamente. Solo es O(n²) si están **anidados** (uno dentro del otro). Dos bucles **separados** son O(n) + O(n) = O(n).

### Regla 2 — Ignora las constantes

O(2n) se escribe **O(n)**. O(n/2) también es **O(n)**. O(500) es **O(1)**.

**¿Por qué?** Porque Big-O describe la **forma del crecimiento**, no el número exacto. Una recta con pendiente 2 y una con pendiente 1 son ambas *rectas*: crecen linealmente. Para datos grandes, el "2" es irrelevante comparado con el efecto de `n`.

```java
for (int i = 0; i < n; i++) {
    System.out.println(arr[i]);   // paso 1
    System.out.println(arr[i]);   // paso 2
}
// Son 2n impresiones, pero la Big-O es O(n), no O(2n).
```

### Regla 3 — Quédate solo con el término dominante

O(n² + n) se escribe **O(n²)**. O(n + log n) es **O(n)**.

**¿Por qué?** Porque para `n` grande, el término más grande **aplasta** a los demás. Mira los números: con n = 1,000, el `n²` vale 1,000,000 y el `n` vale 1,000. El `n` es **ruido** al lado del `n²`. Nos quedamos con el que manda.

```java
for (int i = 0; i < n; i++)
    for (int j = 0; j < n; j++) { ... }   // O(n²)  <- domina
for (int k = 0; k < n; k++) { ... }       // O(n)   <- despreciable al lado
// Total: O(n² + n) = O(n²)
```

🧪 **Ejercicio resuelto — calcula la Big-O de esto:**
```java
public static void misterio(int[] arr) {
    int n = arr.length;
    System.out.println(arr[0]);                 // (a) O(1)
    for (int i = 0; i < n; i++) {               // (b) bucle O(n)
        System.out.println(arr[i]);
    }
    for (int i = 0; i < n; i++)                 // (c) bucle anidado O(n²)
        for (int j = 0; j < n; j++)
            System.out.println(arr[i] + arr[j]);
}
```
Razonamiento: (a) es O(1), (b) es O(n), (c) es O(n²). Total = O(1 + n + n²). Por la Regla 3, domina el n². **Respuesta: O(n²).**

## 1.6 Complejidad de espacio (la mitad olvidada)

Big-O también mide **memoria extra** que usa el algoritmo, no solo tiempo. Se calcula igual: ¿cuánta memoria adicional crece con `n`?

```java
// O(1) de espacio: solo unas pocas variables, no importa el tamaño de arr
int suma = 0;
for (int x : arr) suma += x;

// O(n) de espacio: creamos una estructura que crece con la entrada
Set<Integer> visto = new HashSet<>();
for (int x : arr) visto.add(x);   // el Set puede llegar a tener n elementos
```

🔑 **Clave de entrevista — el trade-off tiempo/espacio:** muchísimas optimizaciones **cambian espacio por tiempo**. En Two Sum, pasamos de O(n²) tiempo / O(1) espacio (fuerza bruta) a O(n) tiempo / O(n) espacio (con HashMap). Gastamos memoria para ganar velocidad. El entrevistador a veces pregunta explícitamente: "¿y si no pudieras usar memoria extra?". Saber nombrar el trade-off te hace ver sólido.

## 1.7 Cómo "leer" la Big-O de un código en 30 segundos

Una checklist mental para la entrevista:
1. ¿Hay bucles? ¿Anidados (multiplica) o separados (suma)?
2. ¿Algún bucle parte el rango a la mitad? → factor `log n`.
3. ¿Hay recursión? ¿Cuántas llamadas se ramifican por nivel? (2 ramas → sospecha exponencial sin memoización.)
4. ¿Creo estructuras que crecen con `n`? → eso es tu espacio.
5. Aplica Reglas 2 y 3: tira constantes, quédate con el término dominante.

## 1.8 Preguntas de Big-O de entrevista, resueltas

**P1. ¿Cuál es la complejidad de buscar en un HashMap? ¿Y en un arreglo sin ordenar?**
R: HashMap → **O(1)** promedio (acceso directo por clave). Arreglo sin ordenar → **O(n)** (hay que revisar elemento por elemento). *Esta diferencia es la base del patrón de hashing.*

**P2. Tengo un bucle que va `for (i = 1; i < n; i *= 2)`. ¿Qué complejidad es?**
R: **O(log n)**. La `i` se **duplica** cada vuelta (1, 2, 4, 8, 16…), así que llega a `n` en ~log₂(n) pasos. La señal de O(log n) es multiplicar/dividir el índice, no sumarle 1.

**P3. ¿Es O(n²) siempre peor que O(n)?**
R: Para `n` grande, sí. Pero para `n` **pequeño**, un O(n²) con constantes chicas puede ganarle a un O(n) con mucho overhead. Big-O describe el comportamiento *asintótico* (cuando n crece). En entrevista, asume n grande salvo que digan lo contrario.

**P4. Dos bucles separados, cada uno sobre n. ¿O(n) u O(n²)?**
R: **O(n)**. Separados se suman (n + n = 2n = O(n)). Solo anidados se multiplican.

**P5. ¿Cuál es la complejidad de `Arrays.sort()` y por qué importa?**
R: **O(n log n)**. Importa porque si tu solución arranca ordenando, ya no puedes bajar de O(n log n); si necesitas O(n), tienes que resolver **sin ordenar** (típicamente con un HashMap).

✅ **Autoevaluación de la Parte 1** (sin mirar):
1. ¿Por qué Big-O cuenta pasos y no segundos?
2. Sin ver la tabla, ordena de más rápido a más lento: O(n²), O(1), O(n log n), O(log n), O(n).
3. Explica con la analogía de partir a la mitad por qué O(log n) es tan rápido.
4. ¿Cuándo dos bucles dan O(n) y cuándo O(n²)?
5. Simplifica: O(3n² + 10n + 50). (Respuesta: O(n²).)
6. ¿Qué trade-off haces al usar un HashMap para acelerar una búsqueda?

---
---

# PARTE 2 — ESTRUCTURAS DE DATOS A FONDO

> Una estructura de datos es una forma de organizar información en memoria para hacer ciertas operaciones rápido. Elegir la estructura correcta es la mitad de resolver un problema. Cada estructura va como un capítulo de libro: qué es desde cero, **cómo funciona por dentro**, cada operación con su Big-O y *por qué*, **ventajas y desventajas**, cuándo usarla y cuándo no, variantes, trampas y encuadre de entrevista.

---

## 1. ARREGLOS (ARRAYS) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** variables y tipos (`int`, `char`, `String`...) · bucles (`for`, `while`) · la idea de "índice/posición". Es el **primer** tema concreto del manual y la base de casi todo lo demás (hashing, dos punteros, pilas, heaps se construyen sobre arreglos). Lo enseñamos desde **cero absoluto**: declarar, inicializar, usar, y recién después los internals.
>
> 📌 **Cómo está organizado este capítulo:** (1) qué es y para qué sirve → (2) **cómo declararlo e inicializarlo** (sintaxis) → (3) acceder y modificar → (4) recorrerlo → (5) arreglos 2D → (6) operaciones paso a paso → (7) métodos útiles de la librería → (8) cómo funciona por dentro → (9) **ArrayList (el arreglo que crece), como tema aparte** → (10) ventajas, cuándo usarlo, bugs y práctica. Al final, **Strings** como sección independiente.

### 1.1 Qué es un arreglo y qué problema resuelve

Sin arreglos, para guardar 30 calificaciones necesitarías 30 variables (`nota1`, `nota2`, …). Absurdo. Un **arreglo** te deja guardar **muchos valores del mismo tipo** en una sola variable, accesibles por un número de **posición (índice)**.

```
índice:  0    1    2    3    4
valor:  85   90   78   92   88
```

🏠 **Analogía:** una hilera de buzones numerados desde el **0**, todos del mismo tamaño y pegados. Si te digo "buzón 3", vas directo a él.

🔑 **Dos reglas que nunca cambian en Java:**
- Los índices **empiezan en 0**. El primer elemento es `arr[0]`.
- Un arreglo de tamaño `n` tiene índices válidos de `0` a `n-1`. El último es `arr[n-1]`.
- El **tamaño es fijo** una vez creado (para uno que crece, ver §1.9, ArrayList).

### 1.2 Cómo DECLARAR e INICIALIZAR un arreglo (la sintaxis, paso a paso)

**Declarar** = decir "voy a tener un arreglo de cierto tipo". **Inicializar** = crearlo de verdad en memoria con un tamaño o con valores.

**Forma 1 — Declarar y crear con un tamaño (se llena con valores por defecto):**
```java
int[] notas = new int[5];   // arreglo de 5 enteros, TODOS inician en 0
```
🔧 Los valores por defecto en Java al usar `new tipo[n]`: `int/long` → **0**, `double` → **0.0**, `boolean` → **false**, `char` → `'\u0000'`, y tipos objeto (`String`, etc.) → **null**.
```java
System.out.println(notas[0]);   // Salida: 0   (aún no asignamos nada)
```

**Forma 2 — Declarar e inicializar con valores literales (de un golpe):**
```java
int[] notas = {85, 90, 78, 92, 88};   // crea el arreglo Y lo llena. Tamaño = 5 (automático)
```
⚠️ Esta forma literal **solo funciona en la misma línea de la declaración**. Si declaras primero y asignas después, necesitas `new int[]{...}`:
```java
int[] notas;
notas = new int[]{85, 90, 78};   // correcto
// notas = {85, 90, 78};         // ERROR de compilación
```

**Forma 3 — Crear vacío y llenar elemento por elemento:**
```java
String[] dias = new String[3];   // [null, null, null]
dias[0] = "lunes";
dias[1] = "martes";
dias[2] = "miércoles";
```

**Sintaxis de los corchetes:** en Java, `int[] arr` es el estilo recomendado (los corchetes junto al tipo). También se permite `int arr[]` (estilo C), pero se prefiere el primero.

### 1.3 Acceder y modificar elementos

```java
int[] arr = {10, 20, 30, 40};

int x = arr[2];     // LEER la posición 2 -> x vale 30
arr[2] = 99;        // ESCRIBIR en la posición 2 -> el arreglo ahora es {10, 20, 99, 40}

int tam = arr.length;   // LONGITUD del arreglo -> 4   (¡sin paréntesis! es un atributo)
int ultimo = arr[arr.length - 1];   // el ÚLTIMO elemento -> 40
```
⚠️ **El error #1 del mundo (ArrayIndexOutOfBoundsException):** acceder a un índice fuera de `0 .. length-1`. Con `arr` de tamaño 4, `arr[4]` **revienta** (el último válido es `arr[3]`). Recuerda: *tamaño 4 → índices 0,1,2,3*.

### 1.4 Recorrer un arreglo (las 3 formas)

**Forma A — `for` clásico (cuando necesitas el índice):**
```java
for (int i = 0; i < arr.length; i++) {
    System.out.println("posición " + i + ": " + arr[i]);
}
```
🔑 La condición es `i < arr.length` (estricto), porque el último índice válido es `length - 1`. Usar `i <= arr.length` es un bug clásico (se sale por 1).

**Forma B — `for-each` (cuando solo necesitas los valores, no el índice):**
```java
for (int valor : arr) {
    System.out.println(valor);
}
```
Más limpio y seguro (no puedes equivocarte de índice), pero **no te da el índice** ni te deja modificar el arreglo en su lugar.

**Forma C — `while` (control manual):**
```java
int i = 0;
while (i < arr.length) { System.out.println(arr[i]); i++; }
```

### 1.5 Arreglos de dos dimensiones (matrices)

Un arreglo 2D es "un arreglo de arreglos" — una tabla con filas y columnas. Es la base de problemas de cuadrículas (tableros, imágenes, "número de islas").
```java
int[][] matriz = new int[2][3];      // 2 filas, 3 columnas, todo en 0
int[][] m = { {1, 2, 3},             // o con literales:
              {4, 5, 6} };

int v = m[1][2];     // fila 1, columna 2 -> 6
m[0][0] = 99;        // modifica la esquina superior izquierda

System.out.println(m.length);     // número de FILAS -> 2
System.out.println(m[0].length);  // número de COLUMNAS de la fila 0 -> 3
```
**Recorrer una matriz** = dos bucles anidados (uno por dimensión):
```java
for (int i = 0; i < m.length; i++) {        // recorre filas
    for (int j = 0; j < m[i].length; j++) { // recorre columnas de esa fila
        System.out.print(m[i][j] + " ");
    }
    System.out.println();
}
```

### 1.6 Operaciones fundamentales, paso a paso

**a) Recorrer / sumar (O(n)):**
```java
int suma = 0;
for (int x : arr) suma += x;   // visita cada elemento una vez
```

**b) Buscar un valor — búsqueda lineal (O(n)):**
```java
public static int indiceDe(int[] arr, int objetivo) {
    for (int i = 0; i < arr.length; i++)
        if (arr[i] == objetivo) return i;   // lo encontré, devuelvo su posición
    return -1;                              // recorrí todo y no estaba
}
```
*Paso a paso:* compara `arr[0]` con el objetivo, luego `arr[1]`, … hasta encontrarlo (devuelve el índice) o agotar el arreglo (devuelve -1). Peor caso: n comparaciones → O(n).

**c) Insertar un valor en la posición `p` (O(n)):** como el tamaño es fijo y no puede haber huecos, hay que **empujar a la derecha** todo lo que está desde `p`.
```java
// (asumiendo que hay espacio: 'n' es cuántos elementos reales hay, < arr.length)
for (int i = n; i > p; i--) arr[i] = arr[i - 1];  // corre todos un lugar a la derecha
arr[p] = nuevo;                                   // coloca el nuevo en el hueco
n++;
```
✍️ Insertar 99 en la posición 1 de `{10,20,30,_}` (n=3): se mueve 30→pos3, 20→pos2, queda `{10,_,20,30}`, y se pone 99 → `{10,99,20,30}`. Hasta n movimientos → O(n).

**d) Borrar en la posición `p` (O(n)):** lo inverso, **empujar a la izquierda** para cerrar el hueco.
```java
for (int i = p; i < n - 1; i++) arr[i] = arr[i + 1];
n--;
```

**e) Invertir un arreglo in-place (dos punteros, O(n)):**
```java
int izq = 0, der = arr.length - 1;
while (izq < der) {
    int tmp = arr[izq]; arr[izq] = arr[der]; arr[der] = tmp;  // intercambia extremos
    izq++; der--;
}
```

**f) Copiar un arreglo:** ⚠️ `int[] b = a;` **NO copia** — hace que `b` apunte al **mismo** arreglo (cambiar `b` cambia `a`). Para una copia real:
```java
int[] b = Arrays.copyOf(a, a.length);   // copia independiente
int[] c = a.clone();                    // también copia
```

### 1.7 Métodos útiles de la librería (`java.util.Arrays`)

No reinventes; para arreglos, Java trae utilidades (recuerda `import java.util.Arrays;`):
```java
Arrays.sort(arr);                 // ordena ascendente (in place) — O(n log n)
Arrays.fill(arr, 7);              // pone 7 en todas las posiciones
int[] copia = Arrays.copyOf(arr, arr.length);       // copia
int[] trozo = Arrays.copyOfRange(arr, 1, 4);        // sub-arreglo de índices 1,2,3
System.out.println(Arrays.toString(arr));           // imprime "[10, 20, 30]" (para depurar)
boolean iguales = Arrays.equals(a, b);              // compara CONTENIDO (no usar == con arreglos)
int pos = Arrays.binarySearch(arr, 30);             // búsqueda binaria (requiere arreglo ordenado)
```
⚠️ **`a == b` con arreglos compara referencias** (si son el mismo objeto), **no el contenido**. Para comparar contenido usa `Arrays.equals(a, b)`.

### 1.8 Cómo funciona por dentro (por qué el acceso es O(1))

🔧 Como todos los elementos son del mismo tipo, **ocupan el mismo número de bytes** y están en memoria **contigua** (pegados). Si el arreglo empieza en la dirección `D` y cada elemento ocupa `T` bytes, la posición del índice `i` se calcula **directo**:
```
dirección(i) = D + (i × T)
```
La computadora **no recorre nada**: hace una multiplicación y una suma → **O(1)**, sin importar el tamaño. A esto se le llama **acceso aleatorio**. La otra cara: como todo debe estar contiguo y sin huecos, **insertar/borrar en medio es O(n)** (hay que mover los demás). Esa es la esencia del arreglo: acceso instantáneo, pero rígido para insertar.

### 1.9 El arreglo que CRECE: `ArrayList` (tema aparte)

> Hasta aquí, todo era sobre el **arreglo estático** (`int[]`), de **tamaño fijo**. Pero muchas veces no sabes cuántos elementos tendrás. Para eso existe `ArrayList`: un arreglo que **crece solo**. Es una estructura distinta (de la librería `java.util`), aunque por dentro use un arreglo.

**Declararlo y usarlo:**
```java
import java.util.ArrayList;
import java.util.List;

List<Integer> lista = new ArrayList<>();   // arreglo dinámico de enteros, vacío
lista.add(10);                 // agrega al final -> [10]
lista.add(20);                 // -> [10, 20]
lista.add(30);                 // -> [10, 20, 30]

int x = lista.get(1);          // LEER la posición 1 -> 20   (¡con get(), no con []!)
lista.set(1, 99);              // ESCRIBIR la posición 1 -> [10, 99, 30]
lista.remove(0);               // borrar la posición 0 -> [99, 30]
int tam = lista.size();        // TAMAÑO -> 2   (¡size(), no .length!)
boolean tiene = lista.contains(99);   // ¿está el 99? -> true
```
🔑 **Diferencias de sintaxis clave** (causa de muchos errores al empezar):

| | Arreglo `int[]` | `ArrayList` |
|---|---|---|
| Crear | `new int[5]` | `new ArrayList<>()` |
| Leer | `arr[i]` | `lista.get(i)` |
| Escribir | `arr[i] = x` | `lista.set(i, x)` |
| Tamaño | `arr.length` (atributo) | `lista.size()` (método) |
| Agregar al final | (no crece) | `lista.add(x)` |
| Tipo de elemento | cualquier tipo | solo **objetos** (`Integer`, no `int`) |

🔧 **Cómo crece por dentro (y qué es "O(1) amortizado"):** un `ArrayList` es un arreglo estático con un truco: cuando se **llena**, crea uno nuevo del **doble** de tamaño y copia todo (O(n)). Pero como eso ocurre **rara vez** (tras duplicar hay espacio para muchas inserciones baratas), el costo **promedio** de `add` al final es **O(1) amortizado**. Agregar/quitar al final es O(1) amortizado; en medio, O(n) (mueve elementos, como el arreglo).

**¿Cuándo cada uno?** Usa `int[]` cuando sabes el tamaño y quieres máxima eficiencia/memoria; usa `ArrayList` cuando el tamaño cambia o no lo sabes de antemano. En entrevistas, `ArrayList` suele ser más cómodo salvo que pidan algo específico.

### 1.10 Ventajas, desventajas y cuándo usar arreglos

➕ **Ventajas:** acceso por índice **O(1)** (lo más rápido); muy eficiente en memoria (solo los datos); **localidad de caché** excelente (contiguos → el procesador los lee en bloque, rapidísimo en la práctica).
➖ **Desventajas:** **tamaño fijo** (el estático); insertar/borrar en medio **O(n)**; buscar es **O(n)** si no está ordenado.
✅ **Úsalo cuando:** accedes por índice, recorres en secuencia, conoces (aprox.) el tamaño, o te importa la memoria/caché.
❌ **Evítalo cuando:** insertas/borras mucho en medio (→ lista enlazada) o buscas por valor constantemente (→ HashMap/HashSet).

### 1.11 Bugs clásicos (y por qué)

**Bug 1 — Índice fuera de rango.** `arr[arr.length]` revienta; el último válido es `arr.length - 1`. *Por qué:* confundir *cantidad* con *última posición* (off-by-one).
**Bug 2 — `i <= arr.length` en el bucle.** Toca un índice de más. Debe ser `i < arr.length`.
**Bug 3 — `int[] b = a;` creyendo que copia.** Solo copia la **referencia**: ambos apuntan al mismo arreglo. Usa `Arrays.copyOf` o `clone()`.
**Bug 4 — Comparar con `==`.** Compara referencias, no contenido; usa `Arrays.equals`.
**Bug 5 — Mezclar sintaxis de arreglo y ArrayList.** `lista.length` o `arr.size()` no compilan. Arreglo: `.length` + `[]`. ArrayList: `.size()` + `.get()/.set()`.

### 1.12 Práctica, con respuestas

**P1.** ¿Cuáles son los índices válidos de un arreglo de tamaño 6?
> Del 0 al 5 (`length - 1`).

**P2.** ¿Qué imprime `int[] a = new int[3]; System.out.println(a[0]);`?
> 0 (valor por defecto de un `int` sin asignar).

**P3.** Declara e inicializa en una línea un arreglo con los números 4, 8, 15.
> `int[] arr = {4, 8, 15};`

**P4.** ¿Por qué `int[] b = a;` no crea una copia, y cómo sí la creas?
> Porque copia la referencia (ambos apuntan al mismo arreglo). Para copiar: `int[] b = Arrays.copyOf(a, a.length);` o `a.clone()`.

**P5.** ¿Por qué insertar al inicio de un arreglo es O(n)?
> Hay que empujar todos los elementos una posición a la derecha para abrir hueco.

**P6.** Diferencia de sintaxis: ¿cómo obtienes el tamaño de un `int[]` vs un `ArrayList`?
> Arreglo: `arr.length` (atributo, sin paréntesis). ArrayList: `lista.size()` (método).

**P7.** ¿Cuándo usarías `ArrayList` en vez de `int[]`?
> Cuando no sabes el tamaño de antemano o este cambia mucho (el ArrayList crece solo).

📚 **Recursos:** VisuAlgo — Array (visualgo.net) · Baeldung — "Arrays in Java" y "Java ArrayList" · documentación oficial `java.util.Arrays`.

---

## 1-B. STRINGS (texto) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** arreglos (un String es, en esencia, un arreglo de caracteres) · variables y bucles. Lo tratamos **aparte** de los arreglos porque, aunque se parecen, los Strings tienen dos rasgos propios (inmutabilidad y comparación) que SIEMPRE caen en entrevistas.

### 1-B.1 Qué es un String y cómo se declara

Un **String** es una secuencia de caracteres (texto). Conceptualmente es **un arreglo de `char`** (`"hola"` ≈ `['h','o','l','a']`), pero es su propia clase con métodos útiles.
```java
String saludo = "hola";                 // forma normal (literal)
String vacio = "";                      // string vacío (longitud 0)
char[] letras = {'h','o','l','a'};
String desdeArreglo = new String(letras);   // "hola" a partir de un char[]
```

### 1-B.2 Operaciones básicas con Strings (con ejemplos)

```java
String s = "Programa";

int n = s.length();              // LONGITUD -> 8   (¡con paréntesis! es método)
char c = s.charAt(0);            // carácter en la posición 0 -> 'P'
String sub = s.substring(0, 4);  // subcadena de índices 0..3 -> "Prog"  (fin exclusivo)
int pos = s.indexOf("gr");       // posición de "gr" -> 3   (-1 si no está)
boolean emp = s.startsWith("Pro"); // ¿empieza con? -> true
String may = s.toUpperCase();    // "PROGRAMA"
String min = s.toLowerCase();    // "programa"
char[] arr = s.toCharArray();    // convierte a arreglo de char (para recorrer/modificar)
String[] partes = "a,b,c".split(","); // divide -> ["a","b","c"]
String unido = "x" + 5 + true;   // concatenar con + -> "x5true"
```
**Recorrer un String** (carácter por carácter):
```java
for (int i = 0; i < s.length(); i++) System.out.println(s.charAt(i));
// o:  for (char ch : s.toCharArray()) System.out.println(ch);
```
⚠️ Nota: `length` en arreglos es **atributo** (`arr.length`), pero en String es **método** (`s.length()`). Esta inconsistencia de Java confunde mucho al inicio.

### 1-B.3 Rasgo 1: Inmutabilidad (lo más importante)

Un String, una vez creado, **NO cambia**. Cada "modificación" crea un objeto **nuevo**.
```java
String s = "hola";
s.toUpperCase();              // crea "HOLA" pero NO modifica s
System.out.println(s);        // Salida: hola   (¡sigue igual!)
s = s.toUpperCase();          // ahora SÍ: capturamos el nuevo en s
System.out.println(s);        // Salida: HOLA
```
⚠️ **Trampa:** creer que `s.toUpperCase()` cambia `s`. No: devuelve uno nuevo que **debes capturar**.

🔧 **Consecuencia de rendimiento — usa `StringBuilder` para construir:** concatenar en un bucle con `+=` crea un objeto nuevo en **cada** vuelta → O(n²) y mucha basura. La solución es `StringBuilder` (mutable):
```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) sb.append("x");   // O(n) total, no O(n²)
String resultado = sb.toString();                // conviertes a String al final
```

### 1-B.4 Rasgo 2: `==` vs `.equals()` (pregunta MUY frecuente)

- `==` compara **referencias** (¿son el mismo objeto en memoria?).
- `.equals()` compara **contenido** (¿dicen lo mismo?).
```java
String a = new String("hola");
String b = new String("hola");
System.out.println(a == b);        // false  (objetos distintos en memoria)
System.out.println(a.equals(b));   // true   (mismo contenido)
```
⚠️ **Trampa peligrosa:** `==` con strings "funciona" a veces (por una optimización llamada *string pool*) y falla otras → bug **intermitente**, de los peores. **Para comparar strings, usa SIEMPRE `.equals()`.** En aserciones de testing, equivocarse aquí da falsos positivos/negativos.

### 1-B.5 El truco `c - 'a'` (mini-hash de letras)

Restar `'a'` a una letra la convierte en un índice 0–25 (`'a'`→0, `'b'`→1, …, `'z'`→25). Sirve para contar letras con un arreglo de 26 (un "hash" manual perfecto cuando el universo es las 26 letras). Lo verás en anagramas y conteos:
```java
int[] conteo = new int[26];
for (char ch : "banana".toCharArray()) conteo[ch - 'a']++;   // cuenta cada letra
// conteo['a'-'a'] = conteo[0] = 3 (tres 'a')
```

### 1-B.6 Bugs clásicos de Strings

**Bug 1 — Esperar que un método mute el String.** `s.replace(...)`, `s.trim()`, etc. devuelven uno **nuevo**; hay que capturarlo.
**Bug 2 — Comparar con `==`.** Da resultados inconsistentes; usa `.equals()` (o `.equalsIgnoreCase()` si ignoras mayúsculas).
**Bug 3 — Concatenar con `+` en bucles grandes.** O(n²); usa `StringBuilder`.
**Bug 4 — `substring(a, b)` creyendo que `b` es inclusivo.** El fin es **exclusivo**: `"hola".substring(0,2)` es `"ho"`, no `"hol"`.

### 1-B.7 Práctica, con respuestas

**P1.** ¿Qué imprime? `String s="ab"; s.concat("c"); System.out.println(s);`
> "ab". `concat` devuelve uno nuevo que no se capturó; `s` no cambia (inmutabilidad).

**P2.** ¿Por qué nunca comparar strings con `==`?
> `==` compara referencias (mismo objeto), no contenido; "funciona" a veces por el string pool y falla otras. Usa `.equals()`.

**P3.** Construyes un texto de 100.000 caracteres en un bucle. ¿`+=` o `StringBuilder`? ¿Por qué?
> `StringBuilder`: `+=` crea un objeto nuevo cada vuelta (O(n²)); `StringBuilder` es mutable (O(n)).

**P4.** ¿Qué devuelve `"programa".substring(0, 4)`?
> "prog" (índices 0,1,2,3; el fin 4 es exclusivo).

**P5.** ¿Cómo cuentas cuántas veces aparece cada letra de una palabra usando un arreglo de 26?
> Recorres la palabra y haces `conteo[ch - 'a']++` por cada carácter.

📚 **Recursos:** Baeldung — "Java String" y "String vs StringBuilder" · VisuAlgo (para visualizar operaciones sobre secuencias) · documentación oficial de `String`.

---
## 2. LISTAS ENLAZADAS (LINKED LISTS) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** la idea de **referencia/objeto** (una variable que "apunta" a algo) · clases básicas · arreglos (cap. 1, para contrastar). Enseñado **desde cero**: primero qué es y cómo se define y se crea en código, luego operaciones y problemas.
>
> 📌 **Orden del capítulo:** (1) qué es → (2) **cómo se define un nodo** → (3) **cómo se crea una lista en código, nodo por nodo** → (4) **cómo se recorre, paso a paso** → (5) operaciones (insertar/buscar/borrar) → (6) variantes → (7) internals → (8) ventajas/cuándo → (9) problemas de entrevista → (10) bugs y práctica.

### 2.1 Qué es y qué problema resuelve

El arreglo es genial para acceso por índice, pero tiene **tamaño fijo** e insertar al inicio o en medio cuesta O(n) (mover todo). La **lista enlazada** resuelve eso: crece sin límite e insertar/borrar es barato — a cambio de perder el acceso por índice.

Una lista enlazada es una **cadena de nodos**. Cada **nodo** guarda dos cosas: un **valor** y una **referencia (flecha) al siguiente nodo**. Los nodos **no** están pegados en memoria (como el arreglo): están dispersos, unidos solo por esas flechas.

```
[1| ●]──▶[2| ●]──▶[3| /]
 dato sig                  (el último apunta a null = "/", fin de la lista)
```
🏠 **Analogía:** una búsqueda del tesoro. Cada pista (nodo) tiene un premio (valor) y la ubicación de la **siguiente** pista. Para llegar a la pista 5, **debes** seguir la cadena desde la primera; no puedes saltar directo.

### 2.2 Cómo se DEFINE un nodo (la pieza básica)

Antes de tener una lista, necesitas definir de qué está hecha: el nodo. En Java es una clase pequeña:
```java
class Nodo {
    int valor;        // el dato que guarda este nodo
    Nodo siguiente;   // una REFERENCIA al siguiente nodo (o null si es el último)

    Nodo(int valor) { // constructor: crea un nodo con un valor y sin "siguiente" aún
        this.valor = valor;
        this.siguiente = null;
    }
}
```
🔑 Lo nuevo aquí: el campo `siguiente` es **del mismo tipo `Nodo`**. Un nodo apunta a otro nodo — por eso se llama "enlazada". `null` significa "no hay siguiente" (fin de la cadena).

### 2.3 Cómo se CREA una lista en código, nodo por nodo

Vamos a construir la lista `1 -> 2 -> 3` desde cero, paso a paso, para que veas cómo se enlazan:
```java
Nodo a = new Nodo(1);    // creo el nodo con valor 1       [1| /]
Nodo b = new Nodo(2);    // creo el nodo con valor 2       [2| /]
Nodo c = new Nodo(3);    // creo el nodo con valor 3       [3| /]

a.siguiente = b;         // enlazo: el 1 apunta al 2       [1|●]──▶[2| /]
b.siguiente = c;         // enlazo: el 2 apunta al 3       [1|●]──▶[2|●]──▶[3| /]
// c.siguiente queda en null (es el último)

Nodo cabeza = a;         // guardo una referencia al PRIMER nodo. La "cabeza" (head)
```
🔑 **La "cabeza" (head)** es la referencia al **primer** nodo. **Es lo único que necesitas guardar:** desde la cabeza puedes llegar a todos los demás siguiendo las flechas. Si pierdes la cabeza, pierdes la lista entera.

### 2.4 Cómo se RECORRE una lista, paso a paso

Recorrer = visitar cada nodo de principio a fin. Como no hay índices, usas un puntero que **salta de nodo en nodo** siguiendo las flechas:
```java
Nodo actual = cabeza;            // empiezo en el primer nodo
while (actual != null) {         // mientras no me haya pasado del final...
    System.out.println(actual.valor);  // hago algo con el nodo actual
    actual = actual.siguiente;   // SALTO al siguiente nodo
}
```
✍️ **Traza** sobre `1 -> 2 -> 3`:
```
actual = nodo(1) -> imprime 1 -> actual = nodo(1).siguiente = nodo(2)
actual = nodo(2) -> imprime 2 -> actual = nodo(2).siguiente = nodo(3)
actual = nodo(3) -> imprime 3 -> actual = nodo(3).siguiente = null
actual == null -> se acaba el while
```
🔑 La línea clave es `actual = actual.siguiente;` — es el "saltar al siguiente". Y la condición `actual != null` es la que detecta el final. *Por qué es O(n):* no hay atajo; para llegar al nodo i, das i saltos.

### 2.5 Operaciones, paso a paso

**a) Insertar al INICIO (O(1)) — la operación estrella de las listas:**
```java
Nodo nuevo = new Nodo(0);     // 1) creo el nodo nuevo
nuevo.siguiente = cabeza;     // 2) el nuevo apunta a la antigua cabeza
cabeza = nuevo;               // 3) la cabeza ahora es el nuevo
```
✍️ Insertar 0 en `1 -> 2`: `nuevo(0).siguiente = nodo(1)` → `0 -> 1 -> 2`, y `cabeza = nodo(0)`. **Solo 3 asignaciones, sin mover nada → O(1).** (En un arreglo, insertar al inicio es O(n) porque hay que empujar todo.)

**b) Buscar un valor (O(n)):** recorres comparando.
```java
public static boolean contiene(Nodo cabeza, int objetivo) {
    Nodo actual = cabeza;
    while (actual != null) {
        if (actual.valor == objetivo) return true;
        actual = actual.siguiente;
    }
    return false;
}
```

**c) Insertar al FINAL (O(n)):** hay que recorrer hasta el último (el que tiene `siguiente == null`) y engancharle el nuevo.
```java
Nodo nuevo = new Nodo(9);
if (cabeza == null) { cabeza = nuevo; }      // lista vacía: el nuevo es la cabeza
else {
    Nodo actual = cabeza;
    while (actual.siguiente != null) actual = actual.siguiente;  // llega al último
    actual.siguiente = nuevo;                // engancha
}
```

**d) Borrar un nodo (O(1) si tienes el anterior):** el nodo anterior "salta por encima" del que se borra.
```java
anterior.siguiente = aBorrar.siguiente;   // el anterior ahora apunta al siguiente del borrado
```
✍️ Para borrar el 2 de `1 -> 2 -> 3`: `nodo(1).siguiente = nodo(3)` → `1 -> 3`. El nodo 2 queda sin referencias y Java lo recolecta. Solo reconectas un puntero → O(1).

### 2.6 Variantes

- **Simplemente enlazada:** cada nodo apunta solo al siguiente (lo que vimos). Una dirección.
- **Doblemente enlazada:** cada nodo apunta al siguiente **y al anterior** (`anterior` además de `siguiente`). Permite recorrer en ambos sentidos y borrar en O(1) si ya tienes el nodo. Cuesta un puntero extra. (`LinkedList` de Java es doble.)
- **Circular:** el último apunta de vuelta al primero, formando un anillo (turnos round-robin, buffers).

### 2.7 Cómo funciona por dentro

🔧 La diferencia esencial con el arreglo: **no hay fórmula de dirección**. Para llegar al nodo `i`, partes de la cabeza y das `i` saltos → acceso por posición **O(n)**, no O(1). A cambio, **insertar/borrar no mueve nada**: solo reconecta punteros. Por eso la lista gana en inserción/borrado y pierde en acceso.

### 2.8 Ventajas, desventajas y cuándo usarla

➕ **Ventajas:** inserción/borrado en extremos **O(1)** (sin mover otros); **tamaño dinámico** natural (crece/encoge sin redimensionar); no reserva memoria de más.
➖ **Desventajas:** **acceso por índice O(n)** (sin acceso aleatorio); **memoria extra** por nodo (los punteros); **mala localidad de caché** (nodos dispersos → más lenta en la práctica que un arreglo, aunque ambos sean O(n)).
✅ **Úsala cuando:** insertas/borras mucho en extremos y no necesitas índices. Es la base de pilas y colas.
❌ **Evítala cuando:** necesitas acceso por índice frecuente (→ arreglo).

### 2.9 Problemas de entrevista que DEBES dominar

**🔑 Invertir una lista** (reconectar punteros con `prev`, `actual`, `siguiente`):
```java
public static Nodo invertir(Nodo cabeza) {
    Nodo prev = null, actual = cabeza;
    while (actual != null) {
        Nodo siguiente = actual.siguiente;  // 1) GUARDA el siguiente (clave: no perder la cola)
        actual.siguiente = prev;            // 2) invierte el puntero
        prev = actual;                      // 3) avanza prev
        actual = siguiente;                 // 4) avanza actual
    }
    return prev;   // nueva cabeza
}
// 1->2->3  =>  3->2->1   |  O(n) tiempo, O(1) espacio
```
**🔑 Detectar un ciclo (liebre y tortuga):** dos punteros, lento (+1) y rápido (+2); si se encuentran, hay ciclo. O(1) espacio.
**🔑 Encontrar el nodo medio:** misma técnica; cuando el rápido llega al final, el lento está en el medio.

### 2.10 Bugs clásicos (y por qué)

**Bug 1 — Perder el resto de la lista.** Si reasignas `actual.siguiente` **antes** de guardar el siguiente, pierdes toda la cola. *Solución:* guarda `siguiente` primero (clave al invertir).
**Bug 2 — `NullPointerException` al recorrer.** La parada es `while (actual != null)`. Acceder a `actual.siguiente.siguiente` sin verificar nulos revienta al final.
**Bug 3 — Olvidar actualizar la cabeza.** Al insertar/borrar el primer nodo, hay que mover `cabeza`, o trabajas con una lista "vieja".

### 2.11 Práctica, con respuestas

**P1.** ¿Qué guarda un nodo de lista enlazada?
> Un valor (el dato) y una referencia al siguiente nodo (o null si es el último).

**P2.** ¿Qué es la "cabeza" y por qué es importante?
> La referencia al primer nodo; desde ella se llega a toda la lista. Si la pierdes, pierdes la lista.

**P3.** ¿Por qué insertar al inicio es O(1) en lista pero O(n) en arreglo?
> En la lista solo reconectas 3 punteros; en el arreglo hay que empujar todos los elementos para abrir hueco.

**P4.** Al invertir, ¿por qué se guarda `siguiente` antes de reasignar `actual.siguiente`?
> Porque al hacer `actual.siguiente = prev` perderías acceso al resto; guardarlo primero lo conserva.

**P5.** ¿Por qué un arreglo suele recorrerse más rápido que una lista, aun siendo ambos O(n)?
> Localidad de caché: el arreglo es contiguo y se carga en bloque; los nodos de la lista están dispersos.

📚 **Recursos:** VisuAlgo — Linked List (visualgo.net) · William Fiset (YouTube) — "Linked Lists" · NeetCode — "Linked List".

---

## 3. PILAS (STACK) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** arreglos o listas (caps. 1 y 2, porque una pila se construye sobre ellos). Es **prerrequisito** de recursión, DFS y backtracking. Enseñado **desde cero**: qué es, cómo se crea y se usa en código, y luego los usos.
>
> 📌 **Orden:** (1) qué es → (2) **cómo se declara y crea** → (3) **los métodos uno por uno** → (4) ejemplo de uso con traza → (5) internals → (6) la conexión con recursión → (7) un problema resuelto → (8) bugs y práctica.

### 3.1 Qué es y qué problema resuelve

Una **pila** sirve cuando quieres recuperar **lo último que metiste, primero** (deshacer/Ctrl-Z, el botón "atrás", verificar paréntesis anidados). Su regla es **LIFO — Last In, First Out**. Solo puedes tocar el elemento **de arriba** (el *tope*).

```
        ┌───┐
 tope → │ 3 │  ← lo último que entró, lo primero que sale
        │ 2 │
        │ 1 │  ← lo primero que entró, lo último que sale
        └───┘
```
🏠 **Analogía:** una pila de platos. Pones platos encima y, para tomar uno, agarras **el de arriba**.

### 3.2 Cómo se DECLARA y se CREA en Java

La forma recomendada hoy es usar `Deque` con `ArrayDeque` (más rápida que la vieja clase `Stack`). Recuerda los imports:
```java
import java.util.ArrayDeque;
import java.util.Deque;

Deque<Integer> pila = new ArrayDeque<>();   // una pila de enteros, vacía
```
*(También existe la clase `Stack<Integer> pila = new Stack<>();`, más antigua; funciona, pero se prefiere `ArrayDeque`.)*

### 3.3 Los métodos, uno por uno

| Método | Qué hace | Ejemplo |
|---|---|---|
| `push(x)` | Pone `x` en el tope | `pila.push(5);` |
| `pop()` | Quita y **devuelve** el tope | `int x = pila.pop();` |
| `peek()` | **Mira** el tope sin quitarlo | `int t = pila.peek();` |
| `isEmpty()` | ¿Está vacía? | `if (pila.isEmpty()) ...` |
| `size()` | Cuántos elementos hay | `int n = pila.size();` |

Todas son **O(1)** (solo tocan el tope).

### 3.4 Ejemplo de uso, paso a paso

```java
Deque<Integer> pila = new ArrayDeque<>();
pila.push(1);                 // pila: [1]            (1 es el tope)
pila.push(2);                 // pila: [1, 2]         (2 es el tope)
pila.push(3);                 // pila: [1, 2, 3]      (3 es el tope)

System.out.println(pila.peek());    // 3   (mira el tope, NO lo saca)
System.out.println(pila.pop());     // 3   (saca el tope) -> pila: [1, 2]
System.out.println(pila.pop());     // 2   -> pila: [1]
System.out.println(pila.isEmpty()); // false  (queda el 1)
```
✍️ **Traza:** tras los 3 `push`, el tope es 3. `peek()` devuelve 3 sin cambiar la pila. El primer `pop()` saca 3, el segundo saca 2 — **en orden inverso al que entraron** (eso es LIFO).

### 3.5 Cómo funciona por dentro

🔧 La pila no es una estructura física nueva: es un **comportamiento** (LIFO) impuesto sobre un arreglo o lista, **restringiendo el acceso a un solo extremo** (el tope). Como solo tocas el tope, nunca hay que recorrer ni mover → **todas las operaciones son O(1)**. Esa restricción no es un defecto: *es el punto* — garantiza el orden LIFO.

### 3.6 La conexión que DEBES saber: recursión = pila

🔑 **Toda recursión usa una pila por dentro — la "pila de llamadas" (call stack).** Cada llamada se **apila**; al retornar, se **desapila**. Por eso una recursión muy profunda da `StackOverflowError`: **se llenó la pila de llamadas**. Y por eso toda recursión se puede reescribir de forma iterativa con una **pila explícita**. (El *stack trace* que ves cuando un test falla **es** el estado de esta pila.)

### 3.7 Problema resuelto: paréntesis balanceados

```java
public static boolean balanceado(String s) {
    Deque<Character> pila = new ArrayDeque<>();
    Map<Character,Character> pares = Map.of(')','(', ']','[', '}','{');
    for (char c : s.toCharArray()) {
        if (c=='('||c=='['||c=='{') pila.push(c);                      // apertura: apila
        else if (pila.isEmpty() || pila.pop()!=pares.get(c)) return false; // cierre: debe casar
    }
    return pila.isEmpty();   // si sobran aperturas, no estaba balanceado
}
// "({[]})" -> true ; "([)]" -> false
```
✍️ Con `"([])"`: push `(`, push `[`, llega `]` → saca `[` (casa), llega `)` → saca `(` (casa), pila vacía → true.

### 3.8 Bugs, cuándo usarla, y práctica

⚠️ **Bug típico — `pop()`/`peek()` sobre pila vacía** lanza excepción. Verifica `isEmpty()` antes.
✅ **Úsala cuando:** "lo último primero" — deshacer, paréntesis, historial "atrás", **DFS**, "siguiente mayor".

**P1.** ¿Por qué todas las operaciones de una pila son O(1)?
> Porque solo se toca el tope; nunca se recorre ni se mueven elementos.
**P2.** ¿Qué relación hay entre recursión y pila?
> La recursión usa la pila de llamadas: cada llamada se apila y se desapila al retornar.
**P3.** Metes 1, 2, 3 y haces dos `pop()`. ¿Qué sale?
> 3 y luego 2 (LIFO). Queda el 1.
**P4.** ¿Pila o cola para el botón "atrás" del navegador? ¿Por qué?
> Pila (LIFO): "atrás" recupera la última página visitada primero.

📚 **Recursos:** VisuAlgo — Stack · NeetCode — "Stack" · Baeldung — "Java ArrayDeque".

---

## 4. COLAS (QUEUE) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** listas o arreglos (caps. 1 y 2). Es **prerrequisito** de BFS (recorrido por niveles en árboles y grafos). Enseñado **desde cero**.
>
> 📌 **Orden:** (1) qué es → (2) **cómo se declara y crea** → (3) **los métodos uno por uno** → (4) ejemplo con traza → (5) internals → (6) la conexión con BFS → (7) Deque y pila-vs-cola → (8) bugs y práctica.

### 4.1 Qué es y qué problema resuelve

Una **cola** sirve cuando quieres atender las cosas **en el orden en que llegaron** (la fila del banco, tareas de impresión, mensajes). Su regla es **FIFO — First In, First Out**: entras por el **final** y sales por el **frente**. Es lo **opuesto** a la pila.

```
  sale ←  [ 1 ] [ 2 ] [ 3 ]  ← entra
  (frente)                 (final)
```
🏠 **Analogía:** la fila de la tortillería. El primero que llega es el primero que se atiende; los nuevos se forman al final.

### 4.2 Cómo se DECLARA y se CREA en Java

```java
import java.util.LinkedList;
import java.util.Queue;

Queue<Integer> cola = new LinkedList<>();   // una cola de enteros, vacía
```
*(También `Queue<Integer> cola = new ArrayDeque<>();` — `ArrayDeque` es más rápida y es la opción moderna preferida.)*
⚠️ **No uses un `ArrayList` como cola:** sacar del frente con `lista.remove(0)` es **O(n)** (empuja todos los elementos). `LinkedList`/`ArrayDeque` lo hacen en O(1).

### 4.3 Los métodos, uno por uno

| Método | Qué hace | Ejemplo |
|---|---|---|
| `add(x)` / `offer(x)` | Encola al **final** | `cola.add(5);` |
| `poll()` | Saca y **devuelve** el **frente** (null si vacía) | `int x = cola.poll();` |
| `peek()` | **Mira** el frente sin sacarlo | `int f = cola.peek();` |
| `isEmpty()` | ¿Está vacía? | `if (cola.isEmpty()) ...` |
| `size()` | Cuántos hay | `int n = cola.size();` |

Todas O(1).

### 4.4 Ejemplo de uso, paso a paso

```java
Queue<Integer> cola = new LinkedList<>();
cola.add(1);                  // cola: [1]        (frente y final = 1)
cola.add(2);                  // cola: [1, 2]
cola.add(3);                  // cola: [1, 2, 3]  (1 al frente, 3 al final)

System.out.println(cola.poll());  // 1   (sale el PRIMERO que entró) -> [2, 3]
System.out.println(cola.peek());  // 2   (el nuevo frente, sin sacar)
System.out.println(cola.poll());  // 2   -> [3]
```
✍️ **Traza:** los elementos salen **en el mismo orden que entraron** (1, luego 2…). *Compara con la pila: ahí salía el 3 primero; aquí sale el 1.* Esa es la diferencia FIFO vs LIFO.

### 4.5 Cómo funciona por dentro

🔧 Se implementa con referencias a **ambos extremos** (frente y final), así encolar (al final) y desencolar (del frente) son **O(1)**. Si solo guardaras el frente, encolar al final costaría O(n). Por eso una cola bien hecha mantiene los dos extremos.

### 4.6 La conexión que DEBES saber: cola = BFS

🔑 **La cola es el motor del BFS** (Breadth-First Search). Cuando un problema diga "**nivel por nivel**", "el **camino más corto** sin pesos", o "expandir desde un punto **hacia afuera en ondas**", piensa cola: metes el inicio y, mientras la cola no esté vacía, sacas uno y **metes a sus vecinos** al final. El orden FIFO garantiza visitar todo lo de distancia 1 antes que lo de distancia 2 → camino más corto. Lo verás en árboles (cap. 6) y grafos (cap. 8).

### 4.7 Deque y la comparación Pila vs Cola

🔧 Un **Deque** (double-ended queue, `ArrayDeque`) permite meter/sacar por **ambos** extremos; puede actuar como **pila o cola** y es más rápido que `Stack`/`LinkedList`. Es la opción moderna para ambas.

| | **Pila** | **Cola** |
|---|---|---|
| Regla | LIFO (último entra, primero sale) | FIFO (primero entra, primero sale) |
| Analogía | Pila de platos | Fila de la tortillería |
| Sale primero | El más **reciente** | El más **antiguo** |
| Recorrido asociado | **DFS** | **BFS** |

### 4.8 Bugs, cuándo usarla y práctica

⚠️ **Bug:** usar `ArrayList.remove(0)` como cola (O(n)). Usa `LinkedList`/`ArrayDeque`.
✅ **Úsala cuando:** procesas en orden de llegada (tareas, mensajes) o haces **BFS**.

**P1.** Diferencia FIFO vs LIFO con un ejemplo cotidiano.
> FIFO (cola): fila del banco, el primero llega/se atiende primero. LIFO (pila): pila de platos, tomas el último que pusiste.
**P2.** Encolas 5, 3, 9 y haces dos `poll()`. ¿Qué sale?
> 5 y luego 3 (FIFO). Queda el 9.
**P3.** ¿Qué estructura es el motor del BFS y por qué?
> La cola: su orden FIFO garantiza visitar por niveles (distancia 1 antes que 2) → camino más corto sin pesos.
**P4.** ¿Por qué no usar `ArrayList.remove(0)` para una cola?
> Es O(n): borrar el primer elemento empuja todos los demás. Usa `LinkedList`/`ArrayDeque` (O(1)).

📚 **Recursos:** VisuAlgo — Queue · NeetCode — "Queue" · Baeldung — "ArrayDeque in Java".

---
## 5. TABLAS HASH (HASHMAP / HASHSET) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** arreglos (cap. 1, porque por dentro una tabla hash *es* un arreglo de cubetas) · la idea de O(1) vs O(n) (Parte 1). **Si dominas una sola estructura para entrevistas, que sea esta:** convierte O(n²) en O(n) una y otra vez. Enseñado **desde cero**: primero qué es y cómo se usa, luego los internals.
>
> 📌 **Orden:** (1) qué es → (2) **cómo se declara y crea** (HashMap y HashSet) → (3) **los métodos uno por uno con ejemplos** → (4) **cómo se recorre** → (5) cómo funciona por dentro (cubetas, colisiones, rehashing) → (6) hashCode/equals → (7) variantes → (8) cuándo usarla, bugs → (9) en la entrevista y práctica.

### 5.1 Qué es y qué problema resuelve

Imagina una agenda con un millón de contactos y quieres el teléfono de "Juan" **al instante**. Con un arreglo, revisarías uno por uno (O(n)). **El problema:** ¿cómo guardo pares (clave → valor) y recupero el valor por su clave casi instantáneamente? La respuesta es la tabla hash: **O(1) promedio**.

- **HashMap:** guarda pares **clave → valor** (ej. `"Juan" → "555-1234"`). Recuperas el valor dando la clave.
- **HashSet:** guarda solo **claves** (sin valor). Sirve para responder *"¿este elemento ya existe?"* en O(1).

🏠 **Analogía:** un guardarropa con fichas numeradas. Das la ficha (la clave) y el encargado va **directo** a tu gancho (el valor), sin revisar los otros 500.

### 5.2 Cómo se DECLARA y se CREA en Java

```java
import java.util.HashMap;
import java.util.HashSet;
import java.util.Map;
import java.util.Set;

Map<String, Integer> edades = new HashMap<>();   // clave String -> valor Integer
Set<String> nombres = new HashSet<>();           // conjunto de Strings (solo claves)
```
🔑 Entre `<>` van los **tipos**: `<String, Integer>` = "claves String, valores Integer". El Set lleva un solo tipo. Los tipos deben ser **objetos** (`Integer`, `String`...), no primitivos (`int`).

### 5.3 Los métodos del HashMap, uno por uno (con ejemplos)

```java
Map<String, Integer> stock = new HashMap<>();

stock.put("manzanas", 50);        // GUARDAR un par (clave -> valor)
stock.put("peras", 30);
stock.put("manzanas", 60);        // misma clave -> SOBREESCRIBE (ahora manzanas=60)

int m = stock.get("manzanas");    // LEER por clave -> 60
Integer x = stock.get("uvas");    // clave que NO existe -> devuelve null  (¡cuidado!)
int u = stock.getOrDefault("uvas", 0);  // si no existe, usa 0 en vez de null -> 0

boolean hay = stock.containsKey("peras");  // ¿existe la clave? -> true
stock.remove("peras");            // BORRAR por clave
int cuantos = stock.size();       // cuántos pares hay
```
🔑 **`getOrDefault(clave, valorPorDefecto)`** es tu mejor amigo para contar: te da el valor actual o un default si la clave es nueva, evitando `null`.

### 5.4 Los métodos del HashSet, uno por uno

```java
Set<Integer> visto = new HashSet<>();

visto.add(7);                     // AGREGAR un elemento
boolean tiene = visto.contains(7);// ¿existe? -> true
boolean nuevo = visto.add(7);     // add() devuelve FALSE si ya existía -> false
visto.remove(7);                  // BORRAR
int n = visto.size();
```
🔑 Truco útil: `add()` devuelve `false` si el elemento ya estaba — un "pregunta y guarda" en una sola línea (perfecto para detectar duplicados).

### 5.5 Cómo se RECORRE

**Un HashMap** (recorres sus pares clave-valor):
```java
for (Map.Entry<String,Integer> e : stock.entrySet()) {
    System.out.println(e.getKey() + " -> " + e.getValue());
}
// o solo las claves:  for (String k : stock.keySet()) ...
// o solo los valores: for (int v : stock.values()) ...
```
**Un HashSet:**
```java
for (int x : visto) System.out.println(x);
```
⚠️ El orden del recorrido **no está garantizado** en un HashMap/HashSet (ver §5.7 variantes si necesitas orden).

### 5.6 Ejemplo completo: contar frecuencias (el uso más común)

```java
Map<Character, Integer> conteo = new HashMap<>();
for (char c : "banana".toCharArray())
    conteo.put(c, conteo.getOrDefault(c, 0) + 1);   // suma 1, o empieza en 0
// conteo = {b=1, a=3, n=2}
```
✍️ **Paso a paso** con "banana": 'b'→ no estaba, 0+1=1. 'a'→0+1=1. 'n'→0+1=1. 'a'→1+1=2. 'n'→1+1=2. 'a'→2+1=3. Resultado `{b=1, a=3, n=2}`.

### 5.7 Cómo funciona por dentro (por qué es O(1))

🔧 Por dentro es **un arreglo de "cubetas" (buckets)**. Para guardar un par: una **función hash** convierte la clave en un número, que se reduce al **índice de una cubeta** (con módulo); ahí se guarda. Para buscar, se repite el cálculo y se va **directo** a esa cubeta → **O(1)**, sin recorrer.

🔧 **Colisiones:** dos claves distintas pueden caer en la misma cubeta (hay infinitas claves y finitas cubetas). Java lo resuelve con **encadenamiento**: la cubeta guarda una **lista** de los pares que cayeron ahí, y al buscar la recorre comparando con `equals`. Con pocas colisiones, esas listas son diminutas y sigue siendo ~O(1).

🔧 **Factor de carga y rehashing:** si se llena demasiado (en Java, factor de carga > **0.75**), crea un arreglo de cubetas **más grande** (el doble) y **redistribuye** todo — operación O(n) **ocasional** (por eso "O(1) **amortizado**").

🔧 **Peor caso:** si **todas** las claves colisionan en una cubeta (hash pésimo), esa cubeta es una lista de n y buscar es **O(n)**. Java 8+ lo mitiga: si una cubeta acumula muchas colisiones, convierte la lista en un **árbol** (O(log n)). Por eso se dice "**O(1) promedio, O(n) peor caso**".

### 5.8 La regla de oro: hashCode + equals

⚠️ Si usas un **objeto propio** como clave, **DEBES sobrescribir `hashCode()` y `equals()`** de forma consistente: si dos objetos son iguales según `equals()`, **deben** tener el mismo `hashCode()`. 🔧 **Por qué:** guardar usa `hashCode()` para elegir la cubeta, y recuperar usa `hashCode()` (misma cubeta) + `equals()` (clave exacta). Si son inconsistentes, guardas con un objeto y lo buscas en **otra cubeta** → el mapa "pierde" tus datos. `String` e `Integer` ya los implementan bien (por eso funcionan perfecto como claves).

### 5.9 Variantes (cuál usar)

| Variante | Orden | Costo | Cuándo |
|---|---|---|---|
| **HashMap** | Ninguno garantizado | O(1) | El default. Solo importa acceso rápido. |
| **LinkedHashMap** | Orden de **inserción** | O(1) | Cuando necesitas recordar en qué orden insertaste. |
| **TreeMap** | Claves **ordenadas** | O(log n) | Cuando necesitas recorrer en orden o buscar rangos. |

🔧 `TreeMap` no usa hashing: por dentro es un **árbol rojo-negro** (cap. 6), por eso mantiene orden y es O(log n).

### 5.10 Cuándo usarla, bugs, y en la entrevista

✅ **Úsala cuando:** búsquedas rápidas por clave, contar frecuencias, detectar duplicados, agrupar, memorizar. **Es tu arma #1 contra O(n²).**
❌ **Evítala cuando:** necesitas orden (→ TreeMap/LinkedHashMap) o índice posicional (→ arreglo).

⚠️ **Bugs clásicos:** (1) clave personalizada sin `hashCode`/`equals` (no la encuentras); (2) asumir orden en un HashMap; (3) usar `get` de una clave inexistente y olvidar que devuelve `null` (usa `getOrDefault`).

🔑 **El patrón que más rinde:** "estaba comparando todos contra todos (O(n²)); en su lugar **guardo lo que ya vi en un HashMap** y consulto en O(1) → O(n)". Two Sum, duplicados, anagramas, frecuencias: todos son esto.

### 5.11 Práctica, con respuestas

**P1.** ¿Cómo declaras un mapa de nombre (String) a edad (int)?
> `Map<String, Integer> edades = new HashMap<>();`

**P2.** ¿Qué devuelve `get` de una clave que no existe, y cómo lo evitas?
> Devuelve `null`. Lo evitas con `getOrDefault(clave, valorPorDefecto)`.

**P3.** Explica con tus palabras por qué un HashMap encuentra un valor en O(1).
> Hashea la clave para obtener un número, lo reduce al índice de una cubeta y va directo a ella, sin recorrer el resto.

**P4.** ¿Qué es una colisión y cómo la resuelve Java?
> Dos claves distintas en la misma cubeta. Java usa encadenamiento: guarda una lista en la cubeta y la recorre con `equals`.

**P5.** Cuenta la frecuencia de cada palabra de una lista. ¿Qué estructura y método?
> Un `HashMap<String,Integer>` con `getOrDefault(palabra, 0) + 1`.

**P6.** ¿Por qué hay que sobrescribir `hashCode` y `equals` juntos en una clave propia?
> Porque guardar usa hashCode (cubeta) y recuperar usa hashCode + equals; si son inconsistentes, el mapa busca en la cubeta equivocada y pierde los datos.

📚 **Recursos:** VisuAlgo — Hash Table (visualgo.net/en/hashtable) · Baeldung — "How HashMap Works in Java" · NeetCode — "Arrays & Hashing".

---
## 6. ÁRBOLES (TREES) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** **recursión** (Patrón 5 — los árboles se recorren recursivamente; dependencia #1) · **colas** (cap. 4, para BFS) · **referencias** (como en listas, cap. 2). Enseñado **desde cero**: primero qué es, cómo se define el nodo y cómo se construye un árbol en código; luego recorridos y problemas.
>
> 📌 **Orden:** (1) qué es y vocabulario → (2) **cómo se define un nodo de árbol** → (3) **cómo se construye un árbol pequeño en código** → (4) BST → (5) desbalance → (6) recorridos (DFS/BFS) paso a paso → (7) la plantilla "pide a los hijos" → (8) operaciones y costos → (9) cuándo, bugs, práctica.

### 6.1 Qué es y vocabulario

Los arreglos y listas son **lineales** (una cosa tras otra). Pero mucha información es **jerárquica**: un organigrama, un sistema de archivos, el **HTML de una página** (un elemento contiene otros). El **árbol** modela ese "contiene a / es hijo de".

```
            8          ← RAÍZ (el de arriba, sin padre)
          /   \
         3     10      ← hijos de 8
        / \      \
       1   6      14   ← 1, 6 y 14 son HOJAS (sin hijos)
```
**Vocabulario** (cae en entrevistas): **raíz** = nodo superior; **hijo/padre** = relación directa; **hoja** = nodo sin hijos; **profundidad** de un nodo = su distancia a la raíz; **altura** del árbol = la profundidad máxima; **subárbol** = un nodo con todos sus descendientes.

🏠 **Analogía:** un árbol genealógico al revés (la raíz arriba). Cada persona (nodo) tiene descendientes (hijos).

### 6.2 Cómo se DEFINE un nodo de árbol

Como la lista enlazada, pero ahora cada nodo apunta a **dos** hijos (árbol binario = máximo 2 hijos):
```java
class Nodo {
    int valor;
    Nodo izq;     // referencia al hijo IZQUIERDO (o null si no tiene)
    Nodo der;     // referencia al hijo DERECHO  (o null si no tiene)

    Nodo(int valor) {
        this.valor = valor;
        this.izq = null;
        this.der = null;
    }
}
```
🔑 Igual que en listas, los hijos son del tipo `Nodo`, y `null` significa "no hay hijo ahí".

### 6.3 Cómo se CONSTRUYE un árbol pequeño en código

Vamos a construir este árbol, paso a paso:
```
     8
    / \
   3   10
```
```java
Nodo raiz = new Nodo(8);     // creo la raíz                 (8)
raiz.izq = new Nodo(3);      // le cuelgo un hijo izquierdo  8.izq = (3)
raiz.der = new Nodo(10);     // le cuelgo un hijo derecho    8.der = (10)
// raiz.izq.izq, raiz.izq.der, etc. quedan en null (3 y 10 son hojas por ahora)
```
Para agregar más niveles, sigues colgando: `raiz.izq.izq = new Nodo(1);` pondría un 1 como hijo izquierdo del 3. **Guardas solo la `raiz`**: desde ella llegas a todo el árbol siguiendo `izq`/`der`.

### 6.4 Árbol binario y BST (árbol binario de búsqueda)

- **Árbol binario:** cada nodo tiene **a lo más 2 hijos**.
- **BST (Binary Search Tree):** un árbol binario con una **regla de orden**: para **cada** nodo, todo lo de su subárbol **izquierdo es menor** y todo lo del **derecho es mayor**. (El árbol del §6.1 es un BST.)

🔧 **Por qué el BST da O(log n):** por la regla de orden, en cada nodo puedes **descartar la mitad del árbol**. ¿Buscas algo menor que el nodo? Te vas a la izquierda e **ignoras todo el subárbol derecho**. Es la misma idea de la **búsqueda binaria** (Patrón 4), sobre una estructura enlazada → O(log n) si está balanceado.

### 6.5 El problema del desbalance

⚠️ Un BST **se degrada** si insertas datos ya ordenados. Inserta 1,2,3,4,5: cada uno es mayor que el anterior, así que **todos van a la derecha** y el árbol se vuelve una **lista inclinada**:
```
1
 \
  2
   \
    3   ← sin mitades que descartar: buscar es O(n), no O(log n)
```
🔧 **Solución — árboles autobalanceados** (AVL, rojo-negro): se reordenan solos al insertar/borrar para mantener la altura ~log n. Por eso `TreeMap`/`TreeSet` de Java garantizan O(log n) **siempre**. No necesitas implementarlo, **pero debes saber que existe y por qué**.

### 6.6 Los recorridos (recorrer = visitar todos los nodos)

**DFS (en profundidad)** — baja hasta el fondo de una rama antes de retroceder. Se hace con **recursión**. El caso base es `nodo == null`. Tres variantes según **cuándo** visitas la raíz respecto a los hijos:

| Recorrido | Orden | Para qué sirve |
|---|---|---|
| **Inorden** | izq → **RAÍZ** → der | En un BST, da los valores **ORDENADOS** |
| **Preorden** | **RAÍZ** → izq → der | Copiar/serializar el árbol |
| **Postorden** | izq → der → **RAÍZ** | Borrar el árbol (hijos antes que el padre) |

```java
public static void inorden(Nodo n) {
    if (n == null) return;            // CASO BASE: no hay nodo, no hago nada
    inorden(n.izq);                   // 1) recorro todo lo de la izquierda
    System.out.print(n.valor + " ");  // 2) visito la raíz (en medio = "in")
    inorden(n.der);                   // 3) recorro todo lo de la derecha
}
```
✍️ **Traza del inorden** sobre el BST 8/3/10/1/6/14: imprime 1 → 3 → 6 → 8 → 10 → 14. **Sale ordenado**, justo por la regla del BST.
🔑 Truco para recordar: "**pre/in/post**" = cuándo visitas la raíz (antes/en medio/después de los hijos).

**BFS (por niveles)** — visita nivel por nivel, con una **cola** (aquí paga esa dependencia):
```java
public static void porNiveles(Nodo raiz) {
    if (raiz == null) return;
    Queue<Nodo> cola = new LinkedList<>();
    cola.add(raiz);
    while (!cola.isEmpty()) {
        Nodo n = cola.poll();                 // saca el del frente
        System.out.print(n.valor + " ");
        if (n.izq != null) cola.add(n.izq);   // mete los hijos al final
        if (n.der != null) cola.add(n.der);
    }
}
// imprime 8 -> 3 -> 10 -> 1 -> 6 -> 14 (un nivel completo antes de bajar)
```

### 6.7 La plantilla "pide a los hijos y combina" (resuelve la mayoría de problemas)

🗝️ Muchísimos problemas de árbol se resuelven así: *"para resolver el nodo actual, pido la respuesta de mis hijos (confiando en la recursión) y la combino"*. Ejemplo, la **altura**:
```java
public static int altura(Nodo n) {
    if (n == null) return 0;                              // caso base
    return 1 + Math.max(altura(n.izq), altura(n.der));    // 1 + la rama más alta
}
```
Con la misma forma resuelves: ¿balanceado?, suma de nodos, ¿iguales dos árboles?, diámetro. **Aprende la plantilla, no cada problema.**

### 6.8 Operaciones del BST y su costo

| Operación | Big-O (balanceado) | Degenerado |
|---|---|---|
| Buscar / Insertar / Borrar | **O(log n)** | O(n) |
| Recorrer (cualquiera) | **O(n)** | O(n) |

### 6.9 Ventajas, cuándo usarlo, bugs y práctica

➕ Un BST balanceado da búsqueda/inserción/borrado **O(log n)** **y mantiene el orden** (a diferencia del HashMap): puedes pedir "el menor", recorrer ordenado, buscar rangos.
➖ Se degrada a O(n) sin balanceo; más lento que un HashMap para búsqueda pura; más memoria por nodo (dos punteros).
✅ **Úsalo cuando:** necesitas datos **ordenados con búsqueda eficiente** o modelar jerarquías.
❌ **Evítalo cuando:** solo búsqueda por clave sin orden (→ HashMap).

⚠️ **Bugs:** olvidar el caso base `if (n==null) return` (NullPointerException en las hojas); asumir que un árbol binario cualquiera es un BST.

💡 **Tu ventaja QA:** el **DOM** de una página web **es un árbol**; un XPath como `//div/span` **navega ese árbol**. Entender árboles te hace mejor automatizador.

**P1.** ¿Qué recorrido de un BST da los valores ordenados y por qué?
> Inorden (izq → raíz → der): por la regla del BST, a la izquierda están los menores, luego el nodo, luego los mayores.
**P2.** ¿Cómo defines un nodo de árbol binario en código?
> Una clase con un valor y dos referencias `izq` y `der` (de tipo Nodo, null si no hay hijo).
**P3.** ¿Por qué un BST se degrada a O(n) y cómo se evita?
> Insertando datos ordenados, todo cae de un lado (lista inclinada). Se evita con árboles autobalanceados (AVL, rojo-negro).
**P4.** ¿Qué estructura usa DFS y cuál BFS?
> DFS usa recursión (pila); BFS usa una cola.
**P5.** Escribe el caso base y la combinación para "sumar todos los valores de un árbol".
> Base: si el nodo es null, devuelve 0. Combinación: `n.valor + suma(n.izq) + suma(n.der)`.

📚 **Recursos:** VisuAlgo — Binary Search Tree · William Fiset (YouTube) — "Tree algorithms" · NeetCode — "Trees".

---
## 7. HEAPS / COLAS DE PRIORIDAD · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** **árboles binarios** (cap. 6 — un heap *es* un árbol binario especial) · **arreglos** (cap. 1 — se guarda en un arreglo) · O(log n). Habilita el patrón **Top-K**. Enseñado **desde cero**: primero cómo se usa, luego los internals.
>
> 📌 **Orden:** (1) qué es → (2) **cómo se declara y crea** (min y max) → (3) **los métodos uno por uno** → (4) ejemplo con traza → (5) internals → (6) el truco Top-K → (7) cuándo, bugs, práctica.

### 7.1 Qué es y qué problema resuelve

Imagina una sala de urgencias: siempre quieres atender **al más grave primero**, sin importar cuándo llegó. **El problema:** acceder siempre al **mínimo (o máximo)** rapidísimo, mientras sigues metiendo y sacando. Un **heap** (en Java, `PriorityQueue`) te da eso: el mín/máx en **O(1) para mirar**, **O(log n) para sacar/insertar**.

🏠 **Analogía:** la sala de urgencias — no atiende por orden de llegada (eso es una cola FIFO), sino por **gravedad**. El heap siempre tiene "al más grave" listo en la cima.

> 🔑 Un heap **NO** mantiene todo ordenado: solo garantiza **quién está en la cima** (el mínimo o el máximo). Por eso es más barato que una lista totalmente ordenada.

### 7.2 Cómo se DECLARA y se CREA (min-heap y max-heap)

```java
import java.util.PriorityQueue;
import java.util.Collections;

PriorityQueue<Integer> minHeap = new PriorityQueue<>();   // por defecto: MÍNIMO en la cima
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder()); // MÁXIMO en la cima
```
🔑 Por defecto, `PriorityQueue` es un **min-heap** (sale primero el menor). Para un **max-heap**, le pasas `Collections.reverseOrder()`.

### 7.3 Los métodos, uno por uno

| Método | Qué hace | Big-O |
|---|---|---|
| `add(x)` / `offer(x)` | Inserta `x` | **O(log n)** |
| `poll()` | Saca y **devuelve** la cima (mín o máx) | **O(log n)** |
| `peek()` | **Mira** la cima sin sacarla | **O(1)** |
| `size()` / `isEmpty()` | Cuántos hay / ¿vacío? | O(1) |

### 7.4 Ejemplo de uso, paso a paso

```java
PriorityQueue<Integer> h = new PriorityQueue<>();   // min-heap
h.add(5);                  // h tiene {5}
h.add(1);                  // {1, 5}      (el 1 sube a la cima)
h.add(3);                  // {1, 3, 5}   (1 sigue en la cima)

System.out.println(h.peek());  // 1   (mira el mínimo, NO lo saca)
System.out.println(h.poll());  // 1   (saca el mínimo) -> queda {3, 5}
System.out.println(h.poll());  // 3   -> queda {5}
```
✍️ **Traza:** sin importar el orden en que metiste (5,1,3), el heap siempre te entrega **el menor primero** (1, luego 3, luego 5). Eso es lo que lo hace útil.

### 7.5 Cómo funciona por dentro

🔧 Un heap es un **árbol binario completo** (niveles llenos salvo quizá el último) con la **propiedad de heap**: cada padre es ≤ sus hijos (en min-heap), así el mínimo está **siempre en la raíz**. Lo asombroso: se guarda en **un arreglo**, sin punteros, con aritmética de índices — para el nodo en el índice `i`: hijo izquierdo `2i+1`, hijo derecho `2i+2`, padre `(i-1)/2`.
- **Insertar (bubble up):** pones el nuevo al final y lo **subes** mientras sea menor que su padre → O(log n).
- **Sacar el mínimo (bubble down):** quitas la raíz, subes el último a la cima y lo **hundes** mientras viole la propiedad → O(log n).

### 7.6 El truco contraintuitivo de Top-K

🔑 Para los K elementos **más GRANDES**, usa un **MIN-heap de tamaño K**: agregas elementos y, si el heap pasa de K, **sacas el mínimo** (`poll`). Así conservas los K mayores, y la raíz es el **K-ésimo mayor**. 🔧 ¿Por qué min-heap para "los mayores"? Porque quieres **descartar fácil al más pequeño** de tus candidatos, y el min-heap te lo da en la cima. Costo **O(n log k)**.
```java
public static int kMayor(int[] nums, int k) {
    PriorityQueue<Integer> h = new PriorityQueue<>();
    for (int n : nums) { h.add(n); if (h.size() > k) h.poll(); }
    return h.peek();   // el k-ésimo mayor
}
// [3,2,1,5,6,4], k=2 -> 5
```

### 7.7 Cuándo, bugs y práctica

✅ **Úsalo cuando:** necesitas repetidamente el mín/máx, **Top-K**, la **mediana de un flujo** (dos heaps), o **Dijkstra**.
❌ **Evítalo cuando:** buscar elementos arbitrarios (es O(n)) o recorrer todo en orden (→ TreeMap).
⚠️ **Bugs:** (1) creer que recorrerlo da orden (solo la raíz está garantizada; para orden, haz `poll` repetido); (2) usar max-heap para "los K mayores" (es min-heap); (3) `poll()` sobre heap vacío devuelve null.

**P1.** ¿Cómo declaras un max-heap en Java?
> `new PriorityQueue<>(Collections.reverseOrder());`
**P2.** ¿Por qué `peek()` es O(1) y `poll()` O(log n)?
> `peek` lee la raíz; `poll` la quita y reordena el heap (bubble down) recorriendo la altura.
**P3.** Para "los 3 más grandes", ¿min o max-heap de tamaño 3? ¿Por qué?
> Min-heap: para descartar fácil al más pequeño de los candidatos.
**P4.** ¿Un heap mantiene todos sus elementos ordenados?
> No; solo garantiza el mín/máx en la raíz.

📚 **Recursos:** VisuAlgo — Binary Heap · NeetCode — "Heap / Priority Queue" · William Fiset (YouTube) — "Priority Queue".

---

## 8. GRAFOS (GRAPHS) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje (las más altas):** **colas** (cap. 4, BFS) · **pilas/recursión** (DFS) · **hash sets** (cap. 5, visitados) · **árboles** (cap. 6, un grafo es "un árbol con ciclos"). Enseñado **desde cero**: primero qué es y **cómo se construye en código**, luego recorridos.
>
> 📌 **Orden:** (1) qué es y tipos → (2) **cómo se construye el grafo en código** (lista de adyacencia paso a paso) → (3) representaciones y trade-offs → (4) BFS/DFS con visitados, paso a paso → (5) costos → (6) problemas clásicos → (7) cuándo, bugs, práctica.

### 8.1 Qué es y tipos

El árbol modela jerarquías (un padre, sin ciclos). El **grafo** modela relaciones **libres**: una red social, un mapa de carreteras (con rutas que forman círculos), dependencias entre tareas, el internet. Es un conjunto de **nodos (vértices)** unidos por **aristas (edges)**.

🏠 **Analogía:** ciudades (nodos) unidas por carreteras (aristas).

**Tipos:** **no dirigido** (la arista va en ambos sentidos: si A es amigo de B, B es amigo de A) · **dirigido** (un solo sentido: "A sigue a B") · **ponderado** (las aristas tienen peso/costo: distancia, tiempo) · **no ponderado** (solo importa si hay conexión).

### 8.2 Cómo se CONSTRUYE un grafo en código (lista de adyacencia, paso a paso)

La forma más común de guardar un grafo: cada nodo guarda **una lista de sus vecinos**, en un `Map`. Construyamos este grafo:
```
1 → 2, 3
2 → 4
3 → 4
```
```java
import java.util.*;

Map<Integer, List<Integer>> grafo = new HashMap<>();
grafo.put(1, new ArrayList<>(Arrays.asList(2, 3)));  // el nodo 1 conecta con 2 y 3
grafo.put(2, new ArrayList<>(Arrays.asList(4)));     // el 2 conecta con 4
grafo.put(3, new ArrayList<>(Arrays.asList(4)));
grafo.put(4, new ArrayList<>());                      // el 4 no apunta a nadie
```
Para **agregar una arista** A→B sobre la marcha:
```java
grafo.putIfAbsent(A, new ArrayList<>());   // crea la lista de A si no existe
grafo.get(A).add(B);                        // añade B como vecino de A
```
⚠️ En un grafo **no dirigido**, agregas la arista en **ambos** sentidos (`A→B` y `B→A`). En uno **dirigido**, solo en uno.

### 8.3 Las dos representaciones (trade-off)

| | Lista de adyacencia | Matriz de adyacencia |
|---|---|---|
| Qué es | cada nodo guarda sus vecinos | matriz V×V, `m[i][j]=1` si hay arista |
| Espacio | **O(V+E)** (ideal para grafos dispersos) | O(V²) (caro) |
| ¿Existe arista A→B? | O(grado de A) | **O(1)** (acceso directo) |
| Cuándo | **el default** (la mayoría de grafos reales) | grafos densos o muchas consultas de arista |

### 8.4 Los recorridos, con la regla CRÍTICA: marcar visitados

⚠️ Como un grafo puede tener **ciclos**, debes **marcar los nodos visitados** (con un `HashSet`) o recorrerías en círculo **para siempre**. Esta es la diferencia clave con recorrer un árbol.

**BFS (por niveles, con COLA)** — da el camino más corto en número de aristas (sin pesos):
```java
public static void bfs(Map<Integer,List<Integer>> g, int inicio) {
    Queue<Integer> cola = new LinkedList<>();
    Set<Integer> visitado = new HashSet<>();
    cola.add(inicio); visitado.add(inicio);          // marca al meter
    while (!cola.isEmpty()) {
        int nodo = cola.poll();
        System.out.print(nodo + " ");
        for (int vecino : g.getOrDefault(nodo, List.of())) {
            if (!visitado.contains(vecino)) {        // solo los NO visitados
                visitado.add(vecino);
                cola.add(vecino);
            }
        }
    }
}
```
✍️ Desde 1: saca 1 (mete 2,3), saca 2 (mete 4), saca 3 (4 ya visitado, no lo mete), saca 4 → imprime `1 2 3 4`. El `visitado` evitó meter el 4 dos veces.

**DFS (en profundidad, con RECURSIÓN):**
```java
public static void dfs(Map<Integer,List<Integer>> g, int nodo, Set<Integer> visitado) {
    if (visitado.contains(nodo)) return;             // ya estuve aquí: corta el ciclo
    visitado.add(nodo);
    System.out.print(nodo + " ");
    for (int vecino : g.getOrDefault(nodo, List.of()))
        dfs(g, vecino, visitado);
}
```

### 8.5 Costos

Recorrer (BFS/DFS) = **O(V + E)** (visitas cada vértice y arista una vez). Camino más corto sin pesos = BFS, O(V+E). Con pesos = Dijkstra, O((V+E) log V).

### 8.6 Problemas clásicos (y ver el "grafo oculto")

Muchos problemas son grafos sin decirlo: una **cuadrícula** (islas: cada celda es nodo, vecinos las celdas adyacentes), **dependencias** (orden de tareas → grafo dirigido), **estados** (transformar paso a paso). Clásicos: **número de islas** (DFS/BFS marcando), **¿se puede llegar de A a B?**, **orden topológico** (tareas con prerrequisitos), **camino más corto** (BFS/Dijkstra).

### 8.7 Cuándo, bugs y práctica

✅ **Úsalo cuando:** el problema habla de **conexiones, redes, rutas, dependencias, islas, "¿llegar de A a B?", "amigos de amigos"**.
⚠️ **Bugs:** (1) **olvidar marcar visitados** → bucle infinito (el error #1); (2) en BFS, marcar al sacar en vez de al meter (un nodo entra varias veces); (3) en grafos dirigidos, construir la arista en ambos sentidos.

**P1.** ¿Cómo construyes una lista de adyacencia para "1 conecta con 2 y 3"?
> `grafo.put(1, new ArrayList<>(Arrays.asList(2,3)));`
**P2.** ¿Por qué hay que marcar visitados en un grafo y no necesariamente en un árbol?
> Porque un grafo puede tener ciclos; sin marcar, recorrerías en círculo infinitamente. Un árbol no tiene ciclos.
**P3.** ¿Lista o matriz de adyacencia, y cuándo cada una?
> Lista: O(V+E), para grafos dispersos (el default). Matriz: O(V²) pero O(1) para consultar una arista; para grafos densos.
**P4.** ¿Por qué BFS da el camino más corto sin pesos?
> Explora por niveles (FIFO): visita lo de distancia 1 antes que lo de 2, así el primer arribo es por el camino más corto en aristas.

📚 **Recursos:** William Fiset (YouTube) — "Graph Theory" (la mejor serie gratis) · NeetCode — "Graphs" · VisuAlgo — Graph Traversal.

---

## 9. TRIES (ÁRBOL DE PREFIJOS) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** **árboles** (cap. 6, un trie es un árbol especializado) · **hash maps** (cap. 5, cada nodo usa un map de hijos) · strings. Estructura de nicho pero elegante (autocompletado, correctores). Enseñado **desde cero**.
>
> 📌 **Orden:** (1) qué es → (2) **cómo se define el nodo** → (3) **cómo se inserta una palabra paso a paso** → (4) buscar palabra y prefijo → (5) por qué O(L) → (6) trie vs HashSet, práctica.

### 9.1 Qué es y qué problema resuelve

Tienes un diccionario de 100.000 palabras y un **autocompletado**: el usuario escribe "pro" y quieres todas las palabras que **empiezan con "pro"** al instante. **El problema:** buscar por **prefijo** ultrarrápido. La respuesta es el **trie** ("árbol de prefijos"): un árbol donde **cada arista es un carácter** y cada camino raíz→abajo deletrea un prefijo. Las palabras que comparten prefijo **comparten el mismo camino inicial**.

```
        (raíz)
        /    \
       c      s
       |      |
       a      o
      / \     |
     s   r    l    → "casa", "caro", "sol"
    (✓) (✓)  (✓)   ← marca de "aquí termina una palabra"
```
🏠 **Analogía:** un índice de diccionario llevado al extremo, letra por letra.

### 9.2 Cómo se DEFINE el nodo de un trie

Cada nodo tiene: (1) un **mapa de hijos** (una entrada por cada siguiente letra posible) y (2) un booleano **`esFinDePalabra`** que marca si el camino hasta aquí forma una palabra completa (no solo un prefijo).
```java
class NodoTrie {
    Map<Character, NodoTrie> hijos = new HashMap<>();
    boolean esFinDePalabra = false;
}
```

### 9.3 Cómo se INSERTA una palabra, paso a paso

Insertar = recorrer letra por letra, creando el camino si falta, y marcar el final:
```java
NodoTrie raiz = new NodoTrie();

void insertar(String palabra) {
    NodoTrie nodo = raiz;
    for (char c : palabra.toCharArray()) {
        nodo.hijos.putIfAbsent(c, new NodoTrie());  // si no existe el hijo 'c', créalo
        nodo = nodo.hijos.get(c);                   // baja a ese hijo
    }
    nodo.esFinDePalabra = true;                     // aquí termina una palabra
}
```
✍️ Insertar "sol": desde la raíz, ¿existe hijo 's'? si no, créalo y baja; ¿existe 'o'? créalo y baja; ¿existe 'l'? créalo y baja; marca `esFinDePalabra=true`. Si luego insertas "sola", reutiliza el camino "sol" y solo añade la 'a'.

### 9.4 Buscar palabra y buscar prefijo

```java
boolean buscar(String palabra) {        // ¿existe la palabra EXACTA?
    NodoTrie n = recorrer(palabra);
    return n != null && n.esFinDePalabra; // el camino existe Y termina palabra aquí
}
boolean empiezaCon(String prefijo) {    // ¿alguna palabra empieza con este prefijo?
    return recorrer(prefijo) != null;    // basta con que el camino exista
}
private NodoTrie recorrer(String s) {
    NodoTrie nodo = raiz;
    for (char c : s.toCharArray()) {
        if (!nodo.hijos.containsKey(c)) return null;  // se cortó el camino: no está
        nodo = nodo.hijos.get(c);
    }
    return nodo;
}
```
🔑 Diferencia clave: `buscar` exige `esFinDePalabra=true` al final; `empiezaCon` solo exige que el camino exista.

### 9.5 Por qué O(L)

🔧 Insertar o buscar cuesta **O(L)**, donde L es la **longitud de la palabra**, **independiente de cuántas palabras haya almacenadas**. Tengas 10 o 10 millones, buscar "programa" cuesta lo mismo: 8 pasos. Eso es lo que ninguna lista ni HashSet de palabras completas logra para búsqueda **por prefijo**.

### 9.6 Trie vs HashSet, y práctica

✅ **Úsalo cuando:** autocompletado, corrector, "todas las palabras con prefijo X", búsqueda de palabras en una matriz.
❌ **Evítalo cuando:** solo necesitas "¿existe esta palabra exacta?" sin prefijos → un **HashSet es más simple** y suficiente (también O(L)). El trie gana **cuando importan los prefijos**.

**P1.** ¿Qué guarda cada nodo de un trie?
> Un mapa de hijos (siguiente letra → nodo) y un booleano `esFinDePalabra`.
**P2.** ¿Por qué buscar es O(L) y no depende del número de palabras?
> Sigues el camino letra por letra de la palabra buscada (L pasos); cuántas otras palabras existan no afecta.
**P3.** ¿Diferencia entre `buscar` (exacta) y `empiezaCon` (prefijo)?
> Ambas recorren las letras; `buscar` además exige `esFinDePalabra=true`; `empiezaCon` solo que el camino exista.
**P4.** ¿Cuándo es mejor un HashSet que un trie?
> Cuando solo compruebas existencia exacta, sin consultas por prefijo.

📚 **Recursos:** VisuAlgo — Trie · NeetCode — "Tries" (Implement Trie, Word Search II).

---
## 10. TABLA COMPARATIVA MAESTRA Y GUÍA DE ELECCIÓN

### 10.1 Costos de todas las operaciones (referencia rápida)

| Estructura | Acceso | Buscar | Insertar | Borrar | Orden | Memoria |
|---|---|---|---|---|---|---|
| Arreglo | **O(1)** | O(n) | O(n) | O(n) | Si lo ordenas | Baja |
| Lista enlazada | O(n) | O(n) | **O(1)**† | **O(1)**† | No | Media |
| Pila / Cola | — | — | **O(1)** | **O(1)** | LIFO / FIFO | Baja |
| HashMap / HashSet | — | **O(1)*** | **O(1)*** | **O(1)*** | No | Media-alta |
| TreeMap / TreeSet (BST balanceado) | O(log n) | **O(log n)** | O(log n) | O(log n) | **Sí** | Media |
| Heap | O(1) (solo mín/máx) | O(n) | O(log n) | O(log n) | Solo la cima | Media |
| Grafo (lista adyacencia) | — | O(V+E) recorrido | O(1) arista | O(grado) | — | O(V+E) |
| Trie | — | O(L) | O(L) | O(L) | Por prefijo | Alta |

(*promedio · †en extremo/posición conocida)

### 10.2 Cómo elegir la estructura (árbol de decisión)

- ¿Necesito **acceso por índice/posición**? → **Arreglo**.
- ¿Necesito **búsqueda por clave ultrarrápida sin orden**? → **HashMap/HashSet**.
- ¿Necesito **búsqueda rápida Y orden** (recorrer ordenado, rangos, "el siguiente mayor")? → **TreeMap/TreeSet**.
- ¿Necesito siempre **el mín/máx / Top-K**? → **Heap**.
- ¿Comportamiento **LIFO** (anidamiento, deshacer, DFS)? → **Pila**.
- ¿Comportamiento **FIFO** (orden de llegada, BFS)? → **Cola**.
- ¿**Inserción/borrado constante en extremos** sin acceso por índice? → **Lista enlazada**.
- ¿**Relaciones/conexiones/redes/dependencias**? → **Grafo**.
- ¿**Búsqueda por prefijo / autocompletado**? → **Trie**.

### 10.3 Las tres frases que te hacen ver senior en entrevista

1. *"Cambiaría este O(n²) por O(n) usando un HashMap para recordar lo que ya vi en O(1)."*
2. *"Un BST me da O(log n) **y** orden, pero se degrada a O(n) si no está balanceado; por eso los TreeMap de Java usan árboles rojo-negro autobalanceados."*
3. *"Para grafos uso lista de adyacencia por defecto porque son dispersos; recorro con BFS si busco el camino más corto sin pesos, marcando visitados para no ciclar."*

# PARTE 3 — LOS PATRONES: CÓMO RECONOCER Y CONSTRUIR CADA ALGORITMO

> Esta es la parte más importante para tu entrevista. Aquí no solo te muestro la solución ya hecha (eso es inútil para aprender): te enseño **cómo se construye desde cero**, qué debes saber **antes** (dependencias), una explicación tan simple que un niño la entendería, las **claves para armar** el algoritmo tú mismo, varios ejemplos con traza, y links para profundizar.
>
> **Cómo está estructurado cada patrón:**
> - 🔗 **Dependencias de aprendizaje:** qué dominar antes (si no cuaja, repasa esto).
> - 👶 **Explicación simple:** la idea central, sin tecnicismos.
> - 🎯 **La señal:** cómo reconocer que el problema pide este patrón.
> - 🗝️ **Claves para construir el algoritmo:** la receta paso a paso para armarlo tú.
> - 🧪 **Ejemplos resueltos con traza.**
> - 🔁 **Variantes y follow-ups** de entrevista.
> - 📚 **Recursos** para profundizar.

---

## 3.0 El framework universal: cómo atacar CUALQUIER algoritmo

Antes de los patrones, interioriza este framework. Sirve para todo problema, lo hayas visto o no. Cuando te quedes en blanco en una entrevista, **vuelve aquí**.

**Paso 1 — Entiende (no asumas).** Reformula el problema con tus palabras. Dibuja un ejemplo pequeño a mano. Pregunta: ¿entrada vacía? ¿duplicados? ¿negativos? ¿ordenado? ¿qué devuelvo si no hay respuesta?

**Paso 2 — Ejemplifica a mano.** Toma una entrada chica (3–5 elementos) y resuélvela **a mano en papel**, observando *qué pasos das tú*. La intuición de cómo lo resuelves manualmente **es** el algoritmo; solo falta traducirla a código.

**Paso 3 — Fuerza bruta primero.** Escribe la solución obvia aunque sea lenta, y di su Big-O. *Tener algo siempre le gana a tener nada.* Muchas veces la fuerza bruta ya pasa, y siempre te da un punto de partida para optimizar.

**Paso 4 — Identifica el cuello de botella.** ¿Dónde está el trabajo repetido? El bucle anidado (O(n²)) casi siempre es el culpable. Pregúntate: *"¿estoy recalculando algo que ya sabía? ¿estoy comparando todo contra todo?"*

**Paso 5 — Reconoce el patrón.** Mira la tabla "señal → patrón" (Parte 5). La señal del problema te dice qué herramienta saca: "¿pares/duplicados?" → hashing; "¿ventana contigua?" → ventana deslizante; "¿ordenado y buscar?" → búsqueda binaria.

**Paso 6 — Construye con la receta del patrón.** Cada patrón de abajo tiene sus "claves para construir". Síguelas.

**Paso 7 — Traza, prueba bordes, da complejidad.** Recorre tu código a mano con un ejemplo. Prueba: vacío, 1 elemento, duplicados, máximo. Da tiempo y espacio.

> 🔑 **La clave que nadie te dice:** **el algoritmo está en cómo lo resuelves a mano.** Si puedes hacerlo en papel con números pequeños, puedes codificarlo — solo tienes que observarte y traducir tus pasos a instrucciones. Por eso el Paso 2 es mágico.

---

## 🧠 Patrón 1 — Hashing (Map / Set) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** arreglos (Parte 2 · Arreglos) · tablas hash y *por qué* son O(1) (Parte 2 · Tablas hash) · Big-O, especialmente la diferencia entre O(n²) y O(n) (Parte 1). Si algo aquí no cuaja, casi siempre es porque "cómo funciona un HashMap por dentro" no quedó firme — regresa a ese capítulo.

### 1.A El problema, antes de cualquier solución

Olvida los "algoritmos" un momento. El problema humano es este: tienes una lista de números y quieres responder *"¿hay dos de estos números que, sumados, den exactamente 9?"* y, si los hay, *"¿en qué posiciones están?"*.

```
posición:  0   1   2   3
valor:     2   7  11  15
```

A simple vista lo resuelves: 2 + 7 = 9, posiciones 0 y 1. Fácil con 4 números. Pero con **un millón** de números, la *forma* de buscar esos dos decide si tu programa responde al instante o se cuelga. El problema real no es "sumar dos números", es **encontrar la pareja sin revisar todas las combinaciones posibles**.

### 1.B La solución obvia (y por qué no basta)

Lo natural: **toma cada número y compáralo con todos los demás** a ver si alguna pareja suma 9.

```java
for (int i = 0; i < nums.length; i++) {            // cada número...
    for (int j = i + 1; j < nums.length; j++) {    // ...contra cada otro número
        if (nums[i] + nums[j] == 9) return new int[]{i, j};
    }
}
```

Funciona. Pero cuenta el trabajo: para cada uno de los `n` números, lo comparas con ~`n` números más. Eso es `n × n` = **O(n²)**. Con un millón de números, son ~un billón (10¹²) de comparaciones → tu programa tarda **días** (revisa la tabla de Big-O en la Parte 1: O(n²) con n=1.000.000 ≈ 11.5 días). Inservible.

**La pregunta que abre la puerta:** ¿podemos evitar el segundo bucle? ¿Podemos saber si "el número que me falta" ya apareció, **sin recorrer toda la lista otra vez**?

### 1.C La idea central, construida desde cero

🏠 **Analogía: emparejar calcetines.** Tienes una canasta de calcetines revueltos y quieres encontrar pares del mismo color. La forma tonta: tomar un calcetín y compararlo con TODOS los demás de la canasta, uno por uno (eso es el O(n²) de arriba). La forma lista: vas sacando calcetines uno por uno y los dejas extendidos sobre una **mesa, ordenados por color**. Cuando sacas un calcetín nuevo, **miras la mesa de un vistazo**: ¿ya hay uno de ese color? Si sí, ¡par encontrado! Si no, lo dejas en la mesa y sigues.

Esa "mesa donde miras de un vistazo, sin recorrer" es el **HashMap**. Su súper-poder, explicado en la Parte 2, es que responde *"¿tengo esto?"* en **O(1)** — tiempo constante, sin importar cuántas cosas haya en la mesa. (Por dentro usa una función hash que va directo a la "cubeta" correcta; si no recuerdas por qué eso es O(1), vuelve a Parte 2 · Tablas hash.)

Ahora traslada la analogía al problema: para cada número `x`, lo que necesito para sumar 9 es su **complemento**, `9 - x`. Entonces, mientras recorro la lista, por cada número me pregunto: *"¿el complemento que me falta ya está en mi mesa (mi HashMap)?"*. Si sí → encontré la pareja. Si no → dejo el número actual en la mesa para los que vengan.

> 🔑 **EL INSIGHT CENTRAL:** la fuerza bruta busca la pareja *mirando hacia adelante* (comparo con todos los que faltan). El hashing busca la pareja *mirando hacia atrás* (¿ya vi al complemento?), y ese "¿ya lo vi?" es O(1) gracias al HashMap. Cambiamos un bucle (O(n)) por una consulta (O(1)). Resultado: O(n²) → **O(n)**. Este cambio de mentalidad —de "comparar contra todos" a "recordar lo visto y preguntar"— es el patrón más rentable de todas las entrevistas.

### 1.D El algoritmo en español, sin código todavía

Para encontrar dos números en `nums` que sumen `objetivo`:

1. Prepara una "mesa" vacía: un HashMap que guardará, de cada número que ya vi, **su valor → su posición**.
2. Recorre la lista de izquierda a derecha, un número a la vez. Para el número actual `x` en la posición `i`:
   a. Calcula el complemento que me falta: `falta = objetivo - x`.
   b. **Pregunta a la mesa:** ¿ya tengo `falta` guardado? 
      - Si **sí** → la pareja es la posición guardada de `falta` y la posición actual `i`. Devuélvelas. Terminaste.
      - Si **no** → guarda el número actual en la mesa (`x → i`) para que esté disponible para los siguientes, y sigue.
3. Si terminas la lista sin encontrar pareja, no existe. Devuelve "no hay".

> ⚠️ **El orden importa muchísimo:** *primero preguntas, luego guardas*. Si guardaras antes de preguntar, podrías emparejar un número **consigo mismo** (ej. con objetivo 6 y un único 3, te diría que 3+3 usando la misma posición). Preguntar antes de guardar lo impide de forma natural.

### 1.E El código, y cada línea bajo el microscopio

```java
public static int[] twoSum(int[] nums, int objetivo) {
    Map<Integer, Integer> visto = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int falta = objetivo - nums[i];
        if (visto.containsKey(falta)) {
            return new int[]{ visto.get(falta), i };
        }
        visto.put(nums[i], i);
    }
    return new int[]{};
}
```

- **`Map<Integer, Integer> visto = new HashMap<>();`** — crea la "mesa". La clave es el **valor** de un número que ya vi; el valor asociado es **su posición**. La guardamos así (valor→posición) porque lo que voy a *preguntar* es por un valor (el complemento), y lo que necesito *recuperar* es su posición.
- **`for (int i = 0; i < nums.length; i++)`** — recorremos una sola vez, de principio a fin. Una sola pasada es lo que hace este algoritmo O(n).
- **`int falta = objetivo - nums[i];`** — el complemento. Si `nums[i]` es 7 y el objetivo 9, `falta` es 2: "necesito haber visto un 2".
- **`if (visto.containsKey(falta))`** — la consulta O(1) a la mesa: *¿ya vi el complemento?* Esta línea es la que reemplaza el segundo bucle de la fuerza bruta.
- **`return new int[]{ visto.get(falta), i };`** — si lo vi, devuelvo **la posición donde guardé el complemento** (`visto.get(falta)`) y **la posición actual** (`i`). El orden las pone de menor a mayor índice porque el complemento se vio antes.
- **`visto.put(nums[i], i);`** — solo se llega aquí si NO encontramos pareja para el actual; entonces lo dejamos en la mesa para los futuros. Guardamos `valor → posición`.
- **`return new int[]{};`** — recorrimos todo sin pareja: devolvemos vacío (convención para "no hay solución").

### 1.F La ejecución completa, paso a paso, con TODAS las variables

`nums = [2, 7, 11, 15]`, `objetivo = 9`. Estado de `visto` y decisiones en cada vuelta:

**Iteración i=0:** `nums[0]=2`. `falta = 9 - 2 = 7`. ¿`visto` tiene 7? `visto` está vacío → **no**. Guardamos: `visto = {2→0}`.

**Iteración i=1:** `nums[1]=7`. `falta = 9 - 7 = 2`. ¿`visto` tiene 2? `visto = {2→0}` → **¡sí!**, en la posición 0. Devolvemos `{0, 1}`. **Fin.**

Resultado: posiciones **[0, 1]**, en **2 pasos**, una sola pasada. La fuerza bruta habría hecho hasta 6 comparaciones aquí, y con un millón de números la diferencia es abismal.

### 1.G Un segundo recorrido: cuando NO hay solución

`nums = [1, 4, 6]`, `objetivo = 20`:
- i=0: `nums[0]=1`, `falta=19`. ¿visto tiene 19? No. `visto = {1→0}`.
- i=1: `nums[1]=4`, `falta=16`. ¿16? No. `visto = {1→0, 4→1}`.
- i=2: `nums[2]=6`, `falta=14`. ¿14? No. `visto = {1→0, 4→1, 6→2}`.
- Se acabó la lista → `return {}` (vacío). Correcto: no hay pareja que sume 20.

### 1.H Bugs clásicos (y POR QUÉ ocurren)

**Bug 1 — Guardar antes de preguntar.** Si pones `visto.put(...)` *antes* del `if`, con `nums=[3]` y `objetivo=6`, guardarías `{3→0}`, luego preguntarías "¿hay un 3?" y dirías "sí, en 0", emparejando el 3 **consigo mismo**. *Por qué pasa:* el complemento de 3 es 3, y al guardar primero, el número se "encuentra a sí mismo". *Solución:* siempre preguntar y solo después guardar.

**Bug 2 — Usar la estructura equivocada.** Si necesitas las **posiciones**, debes usar un `Map` (valor→posición). Si usaras un `Set` (que solo guarda valores), sabrías *que existe* la pareja pero no *dónde*. *Por qué pasa:* confundir "¿existe?" (Set) con "¿dónde está?" (Map). Elige la estructura según lo que el problema pide devolver.

**Bug 3 — Olvidar el caso "no hay solución".** Si no devuelves algo al final (vacío o −1), el código no compila o devuelve basura. Siempre maneja el "no encontrado".

### 1.I La complejidad, derivada

- **Tiempo: O(n).** Una sola pasada por los `n` elementos. Dentro de cada vuelta, las operaciones del HashMap (`containsKey`, `get`, `put`) son **O(1) promedio** (ver Parte 2 · Tablas hash para el "promedio" y su peor caso). `n × O(1) = O(n)`.
- **Espacio: O(n).** En el peor caso (sin pareja hasta el final) la "mesa" llega a tener los `n` elementos guardados.
- **El trade-off explícito:** pasamos de la fuerza bruta O(n²) tiempo / O(1) espacio, a O(n) tiempo / O(n) espacio. **Gastamos memoria para ganar velocidad.** Nombrar este trade-off en voz alta es exactamente lo que un entrevistador senior quiere oír.

### 1.J Todos los casos borde

| Caso | Entrada | Resultado esperado | Por qué importa |
|---|---|---|---|
| Lista vacía | `[]`, obj 5 | `[]` | El for no entra; debe no romper. |
| Un elemento | `[5]`, obj 5 | `[]` | No hay *dos* números; el complemento (0) nunca se vio. |
| Sin solución | `[1,2,3]`, obj 100 | `[]` | Recorre todo y devuelve vacío. |
| Pareja al final | `[3,1,4,2]`, obj 6 | `[2,3]` (4+2) | Verifica que sigue hasta el final. |
| Negativos | `[-1,-2,5]`, obj 3 | `[1,2]` (-2+5) | El método funciona igual con negativos. |
| Duplicados | `[3,3]`, obj 6 | `[0,1]` | El primer 3 se guarda; el segundo encuentra su complemento. |

### 1.K Las variantes que SÍ caen en entrevistas

**Variante 1 — Contar frecuencias (Map como contador).** El uso más común del hashing: contar cuántas veces aparece cada cosa.
```java
Map<Character, Integer> conteo = new HashMap<>();
for (char c : texto.toCharArray())
    conteo.put(c, conteo.getOrDefault(c, 0) + 1);  // suma 1, o empieza en 0
// "banana" -> {a=3, b=1, n=2}
```
🗝️ **Clave:** `getOrDefault(c, 0)` te da el conteo actual o 0 la primera vez. Este patrón resuelve: ¿primer carácter único?, ¿elemento mayoritario?, ¿anagramas?, ¿K más frecuentes?

**Variante 2 — Detectar duplicados con un Set.** Si solo te importa "¿existe?", un Set basta:
```java
Set<Integer> visto = new HashSet<>();
for (int n : nums) if (!visto.add(n)) return true;  // add() devuelve false si ya existía
return false;
```
🗝️ **Clave:** `add()` en un Set devuelve `false` si el elemento ya estaba — un dos-en-uno (pregunta y guarda a la vez).

**Variante 3 — Agrupar (Map de clave→lista).** "Agrupa los anagramas": la clave es la palabra ordenada, el valor es la lista de palabras que comparten esa firma.

**Follow-up de la propia Two Sum:** *"¿y sin memoria extra?"* → si el arreglo viene **ordenado**, usa **dos punteros** (Patrón 2): O(n) tiempo, O(1) espacio, sin HashMap. Saber cuándo cada técnica es la respuesta de un senior.

### 1.L Cómo reconocer que un problema pide hashing

Señales, de más a menos obvias:
1. **Explícitas:** "encuentra un par/duplicado/anagrama", "cuenta cuántas veces", "¿existe un elemento tal que...?".
2. **Por la complejidad:** si la fuerza bruta es O(n²) por "comparar todos contra todos" y te piden mejorarla → casi siempre un HashMap la baja a O(n).
3. **Mentalidad:** cada vez que pienses *"tendría que recordar lo que ya vi"* o *"necesito buscar algo rápido por su valor"* → HashMap/HashSet.

### 1.M Receta para construirlo tú mismo

1. ¿Qué necesito "recordar" de lo ya visto, y qué necesito "preguntar"? Eso define la clave del Map.
2. ¿Necesito devolver posición/valor (→ `Map`) o solo saber si existe (→ `Set`)?
3. Recorre una vez. Por cada elemento: **primero pregunta** (¿está lo que busco?), **luego guarda** el actual.
4. Maneja el "no encontrado" al final.
5. Complejidad: casi siempre O(n) tiempo, O(n) espacio.

### 1.N Práctica, con respuestas

**P1.** En `[3, 2, 4]`, objetivo 6, traza Two Sum. ¿Resultado?
> i=0: x=3, falta=3, no visto, guarda {3→0}. i=1: x=2, falta=4, no, guarda {3→0,2→1}. i=2: x=4, falta=2, ¡sí en pos 1! → [1, 2].

**P2.** ¿Por qué Two Sum con HashMap es O(n) y no O(n²)?
> Porque el segundo bucle de "comparar con todos" se reemplaza por una consulta O(1) al HashMap ("¿ya vi el complemento?"). Una sola pasada × O(1) = O(n).

**P3.** ¿Cuándo preferirías dos punteros sobre el HashMap para Two Sum?
> Cuando el arreglo ya está **ordenado**: dos punteros logran O(n) tiempo con O(1) espacio (sin gastar memoria en el Map).

**P4.** Cuenta la frecuencia de cada carácter en "test". ¿Qué Map resulta?
> {t=2, e=1, s=1}.

**P5.** ¿Qué bug hay si haces `visto.put` antes del `if containsKey` en Two Sum?
> Bug 1: un número puede emparejarse consigo mismo (ej. [3], obj 6 → diría [0,0]). Siempre preguntar antes de guardar.

📚 **Recursos:** NeetCode — "Arrays & Hashing" (neetcode.io) · VisuAlgo — Hash Table (visualgo.net/en/hashtable) · LeetCode Explore: "Hash Table".

---

## 🧠 Patrón 2 — Dos punteros · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** arreglos e índices (Parte 2 · Arreglos) · bucles `while` · Big-O O(n) vs O(n²). Para la variante "lento/rápido" en listas, también listas enlazadas (Parte 2).

### 2.A El problema, antes de cualquier solución

Tienes un arreglo **ordenado** y quieres saber si hay dos números que sumen un objetivo:
```
posición:  0   1   2   3   4
valor:     1   3   4   7   9
```
¿Hay dos que sumen 11? Sí: 4 + 7. El problema, como en hashing, no es "sumar", es **hallar la pareja eficientemente** — pero aquí hay un dato extra que cambia todo: **el arreglo está ordenado**. Ese dato es la llave de una técnica más eficiente en memoria que el HashMap.

### 2.B La solución obvia (y por qué no basta)

Fuerza bruta: comparar todos los pares. O(n²). Lo mismo que en hashing. Y el HashMap lo baja a O(n) tiempo… pero a costa de O(n) espacio (la "mesa"). **La pregunta nueva:** ya que el arreglo está **ordenado**, ¿podemos lograr O(n) tiempo **sin gastar memoria extra**?

### 2.C La idea central, construida desde cero

🏠 **Analogía: dos dedos que se acercan.** Pon el dedo izquierdo en el primer número y el derecho en el último. Suma lo que ambos señalan:
- Si la suma es **igual** al objetivo → encontraste la pareja.
- Si la suma es **muy pequeña** → necesitas más. Como el arreglo está ordenado, mover el **dedo izquierdo a la derecha** apunta a un número **mayor**, que sube la suma. Lo mueves.
- Si la suma es **muy grande** → necesitas menos. Mover el **dedo derecho a la izquierda** apunta a un número **menor**, que baja la suma. Lo mueves.

Repites hasta que los dedos se toquen. Como cada dedo solo avanza en una dirección y nunca retrocede, **entre los dos recorren el arreglo una sola vez** → O(n). Y no usas estructura extra → **O(1) de espacio**.

> 🔑 **EL INSIGHT CENTRAL:** el orden del arreglo te da una **brújula**. La suma de los extremos te dice, sin ambigüedad, hacia dónde moverte: muy chica → sube el izquierdo; muy grande → baja el derecho. Sin orden, esta brújula no existe (no sabrías qué dedo mover), y por eso dos punteros "de extremos" exige datos ordenados. Esa brújula es lo que te ahorra la memoria del HashMap.

### 2.D El algoritmo en español, sin código todavía

Para hallar dos números en un arreglo **ordenado** `arr` que sumen `objetivo`:
1. Pon un puntero `izq` en el inicio (posición 0) y un puntero `der` al final (posición n−1).
2. **Mientras `izq` esté antes de `der`** (no se hayan cruzado):
   a. Calcula `suma = arr[izq] + arr[der]`.
   b. Si `suma == objetivo` → devuelve las posiciones `izq` y `der`. Fin.
   c. Si `suma < objetivo` → necesito más → avanza `izq` un paso a la derecha.
   d. Si `suma > objetivo` → necesito menos → retrocede `der` un paso a la izquierda.
3. Si los punteros se cruzan sin encontrar nada, no hay pareja.

### 2.E El código, y cada línea bajo el microscopio

```java
public static int[] dosSumaOrdenado(int[] arr, int objetivo) {
    int izq = 0;
    int der = arr.length - 1;
    while (izq < der) {
        int suma = arr[izq] + arr[der];
        if (suma == objetivo) {
            return new int[]{izq, der};
        } else if (suma < objetivo) {
            izq++;
        } else {
            der--;
        }
    }
    return new int[]{};
}
```

- **`int izq = 0;` / `int der = arr.length - 1;`** — los dos "dedos", en los extremos. Recuerda `length - 1` para la última posición (igual que en búsqueda binaria; olvidarlo revienta con índice fuera de rango).
- **`while (izq < der)`** — seguimos mientras los dedos **no se hayan tocado ni cruzado**. Aquí es `<` (estricto, sin igual), a diferencia de la búsqueda binaria: si `izq == der`, ambos dedos apuntan al **mismo** número, y "sumar un número consigo mismo usando la misma posición" no es una pareja válida. Por eso no incluimos el caso igual.
- **`int suma = arr[izq] + arr[der];`** — la suma de lo que señalan ambos dedos.
- **`if (suma == objetivo) return ...;`** — pareja encontrada, devuelve las dos posiciones.
- **`else if (suma < objetivo) izq++;`** — la suma se quedó corta. Subimos el dedo izquierdo a un valor mayor (gracias al orden) para **aumentar** la suma.
- **`else der--;`** — la suma se pasó. Bajamos el dedo derecho a un valor menor para **reducir** la suma.
- **`return new int[]{};`** — los dedos se cruzaron sin éxito: no hay pareja.

### 2.F La ejecución completa, paso a paso, con TODAS las variables

`arr = [1, 3, 4, 7, 9]`, `objetivo = 11`:

**Iteración 1:** `izq=0, der=4`. `suma = arr[0]+arr[4] = 1+9 = 10`. ¿10 == 11? No. ¿10 < 11? Sí → `izq++` → `izq=1`.
**Iteración 2:** `izq=1, der=4`. `suma = 3+9 = 12`. ¿12 == 11? No. ¿12 < 11? No → `der--` → `der=3`.
**Iteración 3:** `izq=1, der=3`. `suma = 3+7 = 10`. ¿10 == 11? No. ¿10 < 11? Sí → `izq++` → `izq=2`.
**Iteración 4:** `izq=2, der=3`. `suma = 4+7 = 11`. ¿11 == 11? **¡Sí!** → devuelve `[2, 3]`. **Fin.**

Resultado **[2, 3]** en 4 pasos, recorriendo el arreglo una sola vez, **sin memoria extra**.

### 2.G Un segundo recorrido: cuando NO hay solución

`arr = [1, 2, 3]`, `objetivo = 100`:
- izq=0, der=2: suma=1+3=4 <100 → izq=1.
- izq=1, der=2: suma=2+3=5 <100 → izq=2.
- ¿`izq(2) < der(2)`? No, son iguales → sale el while. `return {}`. Correcto: ningún par suma 100.

### 2.H Bugs clásicos (y POR QUÉ ocurren)

**Bug 1 — Usar `<=` en vez de `<` en el while.** Con `<=`, cuando `izq == der` sumarías `arr[izq] + arr[der]` = el mismo número dos veces, devolviendo una "pareja" falsa que es el mismo elemento. *Por qué pasa:* copiar mecánicamente la plantilla de búsqueda binaria (que sí usa `<=`). Aquí, como necesitamos **dos** elementos distintos, es `<`.

**Bug 2 — Mover el puntero equivocado.** Si cuando `suma < objetivo` mueves `der--` en vez de `izq++`, la suma **baja** cuando querías subirla, y nunca convergerás. *Por qué pasa:* no razonar la "brújula". Recuerda: suma chica → sube izq (a mayores); suma grande → baja der (a menores).

**Bug 3 — Aplicarlo a un arreglo desordenado.** Si el arreglo no está ordenado, la brújula miente y el resultado es incorrecto. *Por qué pasa:* olvidar la precondición. Pregunta siempre "¿está ordenado?".

### 2.I La complejidad, derivada

- **Tiempo: O(n).** En cada iteración, `izq` sube o `der` baja: la distancia entre ellos se reduce en 1 cada vez. Empieza en `n−1` y llega a 0, así que hay a lo más `n−1` iteraciones. Lineal.
- **Espacio: O(1).** Solo tres variables (`izq`, `der`, `suma`), sin importar el tamaño. **Esta es la ventaja sobre el HashMap**, que usa O(n).
- **Comparación directa con hashing:** mismo tiempo O(n), pero dos punteros usa O(1) espacio *si el arreglo ya viene ordenado*. Si NO está ordenado, ordenarlo cuesta O(n log n), y entonces el HashMap (O(n) sin ordenar) suele ganar. El contexto decide.

### 2.J Todos los casos borde

| Caso | Entrada | Resultado | Por qué importa |
|---|---|---|---|
| Vacío | `[]`, obj 5 | `[]` | `der=-1`, el while no entra. |
| Un elemento | `[5]`, obj 5 | `[]` | `izq=der=0`, el while (`<`) no entra: no hay dos elementos. |
| Pareja en extremos | `[2,3,4,8]`, obj 10 | `[0,3]` (2+8) | Se resuelve en la 1ª iteración. |
| Sin solución | `[1,2,3]`, obj 100 | `[]` | Los punteros se cruzan. |
| Negativos (ordenados) | `[-3,-1,2,5]`, obj 1 | `[1,2]` (-1+... no; -3+... ) | Funciona si el orden se respeta. |

### 2.K Las variantes que SÍ caen en entrevistas

**Variante 1 — Palíndromo (extremos que se acercan comparando).**
```java
int izq = 0, der = s.length() - 1;
while (izq < der) {
    if (s.charAt(izq) != s.charAt(der)) return false;
    izq++; der--;
}
return true;   // "reconocer" -> true
```
Mismo esqueleto: dos dedos a los extremos, pero ahora **comparan** en vez de sumar.

**Variante 2 — Puntero lento/rápido (no de extremos).** Ambos empiezan a la izquierda; uno avanza más que el otro. Se usa para:
- **Mover ceros al final / compactar in-place:** el lento marca dónde colocar el próximo elemento válido, el rápido explora.
```java
int lento = 0;
for (int rapido = 0; rapido < arr.length; rapido++)
    if (arr[rapido] != 0) { int t=arr[lento]; arr[lento]=arr[rapido]; arr[rapido]=t; lento++; }
// [0,1,0,3,12] -> [1,3,12,0,0]
```
- **Detectar ciclo en lista enlazada (liebre y tortuga):** el lento avanza 1, el rápido 2; si se encuentran, hay ciclo. O(1) espacio.
- **Encontrar el elemento medio de una lista:** cuando el rápido llega al final, el lento está en el medio.

**Variante 3 — Three Sum (la evolución natural).** Tres números que sumen 0: **ordenas**, fijas un número con un bucle, y para el resto aplicas **dos punteros**. Combina ordenar + dos punteros, O(n²). Clásico absoluto de entrevistas.

### 2.L Cómo reconocer que un problema pide dos punteros

1. **Arreglo/string ORDENADO** + "par/objetivo/encuentra" → dos punteros de extremos.
2. "Palíndromo", "invertir in-place", "comparar desde los extremos" → extremos que se acercan.
3. "Mover/compactar/eliminar in-place sin memoria extra", "ciclo en lista", "elemento medio" → lento/rápido.
4. Pista de optimización: si lograste O(n) con un HashMap pero te piden **O(1) espacio** y los datos están (o puedes dejarlos) ordenados → dos punteros.

### 2.M Receta para construirlo tú mismo

1. Decide el tipo: **extremos que se acercan** (`izq=0`, `der=n-1`) o **lento/rápido** (ambos a la izquierda).
2. Para extremos: `while (izq < der)`; calcula la cantidad de interés (suma/comparación); decide qué puntero mover según la "brújula".
3. Para lento/rápido: el rápido explora en el `for`; el lento avanza solo cuando se cumple una condición.
4. Verifica la precondición (¿necesita orden? entonces confirma que está ordenado).
5. Complejidad: O(n) tiempo, O(1) espacio.

### 2.N Práctica, con respuestas

**P1.** En `[2,4,6,8,10]`, objetivo 14, traza dos punteros.
> izq=0(2),der=4(10): 12<14→izq=1. izq=1(4),der=4(10):14==14 → [1,4].

**P2.** ¿Por qué el while usa `<` y no `<=`?
> Porque necesitamos **dos elementos distintos**; con `<=`, en `izq==der` sumaríamos el mismo número consigo mismo.

**P3.** Dos punteros para Two Sum exige una precondición. ¿Cuál y por qué?
> El arreglo debe estar **ordenado**, porque la decisión de qué puntero mover depende de que mover izq dé valores mayores y der menores.

**P4.** ¿Cuándo prefieres dos punteros sobre HashMap, y cuándo al revés?
> Dos punteros si ya está ordenado (O(1) espacio). HashMap si está desordenado y no quieres pagar O(n log n) por ordenar.

**P5.** ¿Qué técnica de dos punteros detecta un ciclo en una lista enlazada?
> Lento/rápido (liebre y tortuga): lento avanza 1, rápido 2; si se encuentran, hay ciclo; O(1) espacio.

📚 **Recursos:** NeetCode — "Two Pointers" · LeetCode Explore: "Two Pointer Technique" · VisuAlgo para visualizar.

---
## 🧠 Patrón 3 — Ventana deslizante (sliding window) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** **dos punteros** (Patrón 2, porque la ventana se mueve con dos índices) · **hash sets/maps** (cap. 5, que suelen ser el "contenido" de la ventana) · arreglos y strings (cap. 1). Si la ventana no te cuaja, casi siempre es porque dos punteros aún no está firme — repásalo.

### 3.A El problema que resuelve

Tienes una secuencia (un arreglo o un string) y buscas el **mejor tramo CONTIGUO** que cumpla una condición: el subarreglo de suma máxima de tamaño k, el substring más largo sin letras repetidas, la ventana más corta que contiene ciertos caracteres. **El problema es: examinar todos los tramos contiguos posibles sin que el costo explote.**

### 3.B La solución obvia (y por qué no basta)

Lo natural: probar **todos** los tramos posibles. Para cada inicio `i`, recorrer cada fin `j ≥ i` y evaluar el tramo `[i, j]`. Eso son dos bucles anidados → **O(n²)** (o peor, O(n³) si reevalúas el tramo entero cada vez). Para secuencias grandes, inservible.

**La pregunta que abre la puerta:** cuando muevo el tramo una posición a la derecha, **casi todo el tramo es el mismo de antes**. ¿Por qué recalcularlo entero? ¿Puedo aprovechar lo que ya sabía y solo ajustar lo que cambió?

### 3.C La idea central, construida desde cero

🏠 **Analogía: la ventanilla de un tren.** Imagina una ventanilla rectangular por la que solo ves unos cuantos asientos a la vez. La ventanilla se desliza por el vagón:
- A veces la **estiras** para ver más asientos (mueves el borde **derecho**).
- A veces la **encoges** porque ya no cabe lo que buscas (mueves el borde **izquierdo**).
- Vas anotando la "mejor vista" que lograste.

Lo clave: cuando la ventana avanza, **no vuelves a contar todos los asientos** — solo sumas el que **entra** por la derecha y restas el que **sale** por la izquierda. Como cada asiento entra y sale de la ventana **a lo más una vez**, recorres todo el vagón en **O(n)**, no O(n²).

> 🔑 **EL INSIGHT CENTRAL:** la fuerza bruta recalcula cada tramo desde cero (trabajo repetido). La ventana deslizante **reutiliza** el tramo anterior: ajusta solo los extremos (uno entra, uno sale). Ese "reutilizar en vez de recalcular" es lo que convierte O(n²) en O(n). Es el mismo espíritu que el hashing (no repetir trabajo), aplicado a tramos contiguos.

### 3.D Los dos tipos de ventana (debes distinguirlos)

1. **Ventana de tamaño FIJO (k):** el tramo siempre mide k. Avanzas: entra uno por la derecha, sale uno por la izquierda. Ej. "suma máxima de k elementos contiguos".
2. **Ventana de tamaño VARIABLE:** la ventana crece y se encoge según una condición. Ej. "substring más largo sin repetir" (crece mientras sea válido, se encoge cuando deja de serlo).

### 3.E El algoritmo en español (ventana variable), sin código

Para el substring más largo sin caracteres repetidos:
1. Pon dos punteros: `izq = 0` y `der`, que recorre la secuencia.
2. Lleva un Set con los caracteres que están **dentro** de la ventana actual.
3. Por cada posición de `der`:
   a. **Si** el carácter en `der` ya está en la ventana (rompería la regla "sin repetidos"), **encoge** por la izquierda: saca `s[izq]` del Set y avanza `izq`, hasta que el repetido salga.
   b. **Expande:** agrega `s[der]` al Set.
   c. **Registra:** actualiza el máximo con el tamaño actual de la ventana, que es `der - izq + 1`.
4. Al final, el máximo es la respuesta.

> 🔑 **El esqueleto mental universal de la ventana variable** (memorízalo):
> ```
> izq = 0
> para der de 0 a n-1:
>     mete s[der] a la ventana
>     mientras (la ventana es INVÁLIDA):
>         saca s[izq]; izq++
>     registra el resultado con la ventana actual (der - izq + 1)
> ```

### 3.F El código, y cada línea bajo el microscopio

```java
public static int sinRepetir(String s) {
    Set<Character> ventana = new HashSet<>();
    int izq = 0;
    int max = 0;
    for (int der = 0; der < s.length(); der++) {
        while (ventana.contains(s.charAt(der))) {
            ventana.remove(s.charAt(izq));
            izq++;
        }
        ventana.add(s.charAt(der));
        max = Math.max(max, der - izq + 1);
    }
    return max;
}
```

- **`Set<Character> ventana = new HashSet<>();`** — el "contenido" de la ventana: los caracteres que están dentro ahora mismo. Usamos un Set porque la pregunta es "¿ya está este carácter?" (membresía O(1)).
- **`int izq = 0;`** — el borde izquierdo de la ventana.
- **`int max = 0;`** — la mejor longitud encontrada hasta ahora.
- **`for (int der = 0; ...)`** — `der` es el borde derecho; avanza una posición por vuelta. Cada carácter entra por aquí.
- **`while (ventana.contains(s.charAt(der)))`** — *antes* de meter el nuevo carácter, si ya está dentro, la ventana sería inválida (tendría un repetido). Mientras eso pase, **encogemos por la izquierda**.
- **`ventana.remove(s.charAt(izq)); izq++;`** — saca el carácter del borde izquierdo y avanza `izq`. Esto repite hasta que el carácter repetido salga de la ventana.
- **`ventana.add(s.charAt(der));`** — ahora sí, la ventana es válida; metemos el carácter nuevo.
- **`max = Math.max(max, der - izq + 1);`** — el tamaño de la ventana actual es `der - izq + 1` (cuenta inclusiva de ambos extremos). Actualizamos el máximo.

### 3.G La ejecución completa, paso a paso, con TODAS las variables

`s = "abcabcbb"`:

| der | s[der] | ¿está en ventana? | encoge (izq) | ventana tras ajustar | tamaño (der-izq+1) | max |
|---|---|---|---|---|---|---|
| 0 | a | no | — | {a} | 1 | 1 |
| 1 | b | no | — | {a,b} | 2 | 2 |
| 2 | c | no | — | {a,b,c} | 3 | 3 |
| 3 | a | **sí** | saca a → izq=1 | {b,c,a} | 3 | 3 |
| 4 | b | **sí** | saca b → izq=2 | {c,a,b} | 3 | 3 |
| 5 | c | **sí** | saca c → izq=3 | {a,b,c} | 3 | 3 |
| 6 | b | **sí** | saca a,b → izq=5 | {c,b} | 2 | 3 |
| 7 | b | **sí** | saca c,b → izq=7 | {b} | 1 | 3 |

**Resultado: 3** (el "abc"). Cada carácter entró y salió de la ventana **a lo más una vez** → O(n).

### 3.H Ejemplo de ventana FIJA (la otra mitad del patrón)

"Suma máxima de k elementos contiguos":
```java
public static int sumaMaxK(int[] arr, int k) {
    int suma = 0;
    for (int i = 0; i < k; i++) suma += arr[i];   // 1) suma de la PRIMERA ventana
    int max = suma;
    for (int der = k; der < arr.length; der++) {
        suma += arr[der] - arr[der - k];          // entra arr[der], SALE arr[der-k]
        max = Math.max(max, suma);
    }
    return max;
}
// [2,1,5,1,3,2], k=3 -> 9   (5+1+3)
```
🗝️ **Clave de la ventana FIJA:** no recalcules la suma entera en cada paso (eso sería O(n·k)). **Suma el que entra y resta el que sale** → cada paso es O(1) → total O(n). Esta línea `suma += arr[der] - arr[der-k]` *es* la esencia del patrón.

### 3.I Bugs clásicos (y por qué)

**Bug 1 — Recalcular la ventana entera en cada paso.** Anula la ventaja: vuelves a O(n·k) u O(n²). *Por qué pasa:* no aprovechar que solo cambian los extremos. *Solución:* suma el que entra, resta el que sale.
**Bug 2 — Calcular mal el tamaño de la ventana.** Es `der - izq + 1` (inclusivo en ambos extremos), no `der - izq`. *Por qué:* olvidar que ambos índices cuentan. Verifícalo con una ventana de 1 elemento (der=izq → tamaño 1).
**Bug 3 — Encoger después de registrar (en ventana variable).** Si registras el máximo *antes* de arreglar una ventana inválida, cuentas una ventana que no cumple. *Solución:* primero asegura validez (el `while`), luego registra.
**Bug 4 — Olvidar el caso de string/arreglo vacío.** El `for` no entra y se devuelve `max=0`, que suele ser correcto, pero verifícalo según el problema.

### 3.J La complejidad, derivada

- **Tiempo: O(n).** Aunque hay un `while` dentro del `for`, **`izq` solo avanza, nunca retrocede**, y en total se mueve a lo más `n` veces en toda la ejecución. Así que `der` hace n pasos y `izq` hace ≤ n pasos: O(n) total, no O(n²). (Este razonamiento —"cada elemento entra y sale una vez"— es el que debes verbalizar en la entrevista.)
- **Espacio:** O(tamaño de la ventana) — en el peor caso O(n) si la ventana llega a abarcar todo (con el Set); O(1) en la versión de suma fija (solo variables).

### 3.K Todos los casos borde

| Caso | Entrada | Resultado | Por qué importa |
|---|---|---|---|
| Vacío | `""` | 0 | El for no entra. |
| Un carácter | `"a"` | 1 | Ventana de tamaño 1. |
| Todos iguales | `"aaaa"` | 1 | La ventana se encoge constantemente a 1. |
| Todos distintos | `"abcd"` | 4 | La ventana nunca encoge: crece a n. |
| k mayor que el arreglo (fija) | `[1,2]`, k=5 | manejar aparte | Validar que k ≤ longitud. |

### 3.L Variantes y follow-ups de entrevista

- **Ventana variable con condición numérica:** "subarreglo más corto cuya suma ≥ X" (crece hasta cumplir, encoge para minimizar).
- **Ventana con un Map en vez de Set:** "substring más largo con a lo más K caracteres distintos" (el Map cuenta cuántos de cada uno).
- **Ventana mínima que cubre un patrón:** "menor substring que contiene todas las letras de T" (clásico difícil: ventana + Map de conteos).
- **Anagramas en un string:** ventana fija del tamaño del patrón + comparación de conteos.

### 3.M Cómo reconocer que un problema pide ventana deslizante

1. La palabra clave **"contiguo"** (subarreglo/substring **pegado**, no salteado).
2. "El más **largo/corto** que cumpla X", "la suma/máximo de **k** seguidos".
3. Si tu solución de fuerza bruta tiene dos bucles anidados sobre tramos contiguos (O(n²)) → casi seguro una ventana lo baja a O(n).

### 3.N Receta para construirlo tú mismo

1. ¿Ventana **fija** (k dado) o **variable** (según condición)? Eso decide la plantilla.
2. Decide qué llevas "dentro" de la ventana: una suma, un Set, un Map de conteos.
3. Expande con `der` (mete el que entra). Para fija, además resta el que sale (`arr[der-k]`).
4. Para variable: tras expandir, **encoge con `izq` mientras la ventana sea inválida**.
5. Registra el resultado con el tamaño/valor actual (`der - izq + 1`).
6. Complejidad: O(n) tiempo (cada elemento entra y sale una vez).

### 3.O Práctica, con respuestas

**P1.** En `[1,3,2,6,2,1]`, k=3, ¿cuál es la suma máxima de 3 contiguos? Traza.
> ventana inicial 1+3+2=6. der=3: +6-1=11. der=4: +2-3=10. der=5: +1-2=9. Máx=11 (3+2+6).

**P2.** ¿Por qué la ventana deslizante es O(n) y no O(n²), aun con un while dentro del for?
> Porque `izq` solo avanza (nunca retrocede) y se mueve a lo más n veces en total; cada elemento entra y sale de la ventana una sola vez.

**P3.** ¿Cuál es el tamaño de una ventana entre los índices izq=2 y der=5?
> 5 - 2 + 1 = 4.

**P4.** En la ventana fija, ¿qué hace la línea `suma += arr[der] - arr[der-k]`?
> Actualiza la suma en O(1): agrega el elemento que entra (`arr[der]`) y quita el que sale (`arr[der-k]`), sin recalcular todo.

**P5.** ¿Qué señal en un enunciado te dice "esto es ventana deslizante"?
> "Subarreglo/substring **contiguo** más largo/corto que cumple X" o "suma/máximo de k elementos seguidos".

📚 **Recursos:** NeetCode — "Sliding Window" · "Grokking the Coding Interview" (patrón de ventana) · VisuAlgo para visualizar el avance de los punteros.

---
## 🧠 Patrón 4 — Búsqueda binaria · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** arreglos con acceso por índice O(1) (Parte 2 · Arreglos) · datos **ORDENADOS** · Big-O O(log n) y la idea de "partir a la mitad" (Parte 1 · §1.4). Si la binaria no te entra, casi siempre es el manejo de **límites de índices** lo que falta — repásalo aquí.

### 4.1 El problema, antes de cualquier solución

Olvida la "búsqueda binaria" por un momento. Empecemos por el problema humano.

Tienes una lista de números y quieres responder una pregunta simple: **"¿está el número 73 en esta lista? Y si está, ¿en qué posición?"**

```
posición:  0    1    2    3    4    5    6    7    8
valor:     3    9   15   22   31   48   59   73   88
```

Parece trivial. Lo es… cuando la lista tiene 9 números. Pero imagina que la lista tiene **mil millones** de números (los usuarios de una base de datos, los registros de un banco). Ahora la forma de resolverlo **decide si tu programa responde en un parpadeo o tarda horas**. Ese es el verdadero problema: no "encontrar el número", sino **encontrarlo de forma que escale**.

### 4.2 La solución obvia (y por qué no basta)

La forma natural, la que haría cualquiera: **empezar por el principio y revisar uno por uno** hasta encontrarlo.

```
¿Es 3 el 73? No. Siguiente.
¿Es 9 el 73? No. Siguiente.
¿Es 15 el 73? No. Siguiente.
... (sigues) ...
¿Es 73 el 73? ¡Sí! Está en la posición 7.
```

Esto se llama **búsqueda lineal**. Funciona. Pero cuenta los pasos: en el peor caso (el número está al final, o no está), revisas **los `n` elementos**. Para mil millones de elementos, son mil millones de comparaciones. Eso es **O(n)** (si no entiendes esta notación, está explicada a fondo en la Parte 1 del manual; aquí solo necesitas saber que "O(n)" significa "el trabajo crece igual que el tamaño de la lista").

**La pregunta clave que abre la puerta a la búsqueda binaria:** ¿podemos hacerlo sin revisar uno por uno? ¿Podemos **descartar muchos de golpe**?

### 4.3 La idea central, construida desde cero

Aquí viene la magia, y la voy a construir despacio porque es el corazón de todo.

🏠 **Analogía: el juego de adivinar el número.** Pienso un número del 1 al 100. Tú tienes que adivinarlo, y yo solo te digo "más alto" o "más bajo". ¿Cuál es tu mejor primera jugada?

Si dices "¿1?", desperdicias la pregunta: si te digo "más alto", solo descartaste UN número (quedan 99). Mal.

La jugada óptima es decir **50** (la mitad). ¿Por qué? Porque sin importar mi respuesta, **descartas la mitad del rango de un solo golpe**:
- Si digo "más alto" → el número está entre 51 y 100. Acabas de eliminar los números del 1 al 50. **50 descartados con una sola pregunta.**
- Si digo "más bajo" → está entre 1 y 49. Igual de bueno.

Y repites: preguntas la mitad del rango que queda, descartas la mitad otra vez. 100 → 50 → 25 → 12 → 6 → 3 → 1. **En ~7 preguntas atrapas cualquier número del 1 al 100.** Compáralo con preguntar 1, 2, 3, 4… que podría tomar 100 preguntas.

**Eso es la búsqueda binaria.** "Binaria" porque en cada paso partes el problema en **dos** y tiras una mitad.

⚠️ **Pero hay una condición sin la cual nada de esto funciona, y es crítica:** el juego solo funciona porque los números tienen un **orden**. Cuando te digo "más alto", tú sabes hacia qué lado ir *porque están ordenados del 1 al 100*. Si los números estuvieran revueltos, "más alto" no te diría hacia qué lado buscar.

> 🔑 **LA PRECONDICIÓN ABSOLUTA:** la búsqueda binaria **solo funciona sobre datos ORDENADOS.** Si no están ordenados, no puedes decidir "ir a la izquierda o a la derecha", y todo el método se cae. Esta es la primera pregunta que debes hacerte (y verbalizar en una entrevista): *"¿están ordenados los datos?"*. Si no lo están, o los ordenas primero (con un costo, ver §10) o usas otra técnica.

### 4.4 El algoritmo en español, sin código todavía

Antes de una sola línea de código, vamos a escribir el algoritmo en palabras. Si entiendes esto, el código es solo traducción.

Para buscar un `objetivo` en un arreglo `arr` ordenado:

1. Mantén dos marcadores que delimitan **la zona donde el objetivo todavía podría estar**. Al inicio, esa zona es todo el arreglo: un marcador `izquierda` al principio (posición 0) y un marcador `derecha` al final (posición n−1).
2. **Mientras la zona no esté vacía** (es decir, mientras `izquierda` no haya pasado a `derecha`):
   a. Mira el elemento **del medio** de la zona actual.
   b. **Si el del medio ES el objetivo** → ¡lo encontraste! Devuelve su posición. Terminaste.
   c. **Si el del medio es MENOR que el objetivo** → el objetivo, si existe, está en la **mitad derecha** (porque todo a la izquierda del medio es aún menor). Así que mueve `izquierda` a justo **después** del medio. Acabas de descartar la mitad izquierda completa.
   d. **Si el del medio es MAYOR que el objetivo** → el objetivo está en la **mitad izquierda**. Mueve `derecha` a justo **antes** del medio. Descartaste la mitad derecha.
3. Si la zona se vació sin encontrarlo, **el objetivo no está**. Devuelve "no encontrado" (por convención, −1).

Léelo dos veces. **Todo el código de la siguiente sección es solo esto, traducido a Java.**

### 4.5 El código, y cada línea bajo el microscopio

```java
public static int busquedaBinaria(int[] arr, int objetivo) {
    int izquierda = 0;
    int derecha = arr.length - 1;

    while (izquierda <= derecha) {
        int medio = izquierda + (derecha - izquierda) / 2;

        if (arr[medio] == objetivo) {
            return medio;
        } else if (arr[medio] < objetivo) {
            izquierda = medio + 1;
        } else {
            derecha = medio - 1;
        }
    }
    return -1;
}
```

Ahora, **cada línea, palabra por palabra**:

- **`int izquierda = 0;`** — el marcador izquierdo arranca en la primera posición del arreglo (los índices empiezan en 0). Es el inicio de "la zona donde el objetivo podría estar".

- **`int derecha = arr.length - 1;`** — el marcador derecho arranca en la **última** posición. Ojo: `arr.length` es la *cantidad* de elementos (ej. 9), pero la última *posición* es `length - 1` (ej. 8), porque contamos desde 0. Si pusieras `arr.length` aquí, accederías a una posición que no existe y reventarías con `ArrayIndexOutOfBoundsException`. Este `-1` es de los detalles más fáciles de olvidar.

- **`while (izquierda <= derecha)`** — el bucle sigue **mientras la zona sea válida**. La zona es válida si el marcador izquierdo no ha rebasado al derecho. El `<=` (menor *o igual*) es crucial y lo analizamos a fondo en §7: con `<=`, cuando `izquierda == derecha` la zona tiene **exactamente un elemento** que todavía hay que revisar. Si pusieras solo `<`, te saltarías revisar ese último elemento y fallarías en casos donde el objetivo es justo ese.

- **`int medio = izquierda + (derecha - izquierda) / 2;`** — calcula la posición central de la zona actual. Dos cosas finísimas aquí:
  1. **Por qué no `(izquierda + derecha) / 2`:** matemáticamente da lo mismo, PERO si `izquierda` y `derecha` son números enormes, su suma puede **desbordar** el límite de un `int` (volverse negativa por overflow) y romper todo. La fórmula `izquierda + (derecha - izquierda) / 2` nunca suma los dos grandes, así que no desborda. Es el modo "correcto" y el que esperan ver en una entrevista seria.
  2. **La división entera descarta el decimal:** si la zona tiene un número par de elementos, `medio` cae en el de la izquierda de los dos centrales. No importa para la correctitud; solo debes saberlo.

- **`if (arr[medio] == objetivo) return medio;`** — caso feliz: el del medio ES el objetivo. Devolvemos su posición y salimos. Fin.

- **`else if (arr[medio] < objetivo) izquierda = medio + 1;`** — el del medio es **menor**. Como el arreglo está ordenado, **todo lo que está a la izquierda del medio es todavía más pequeño**, así que es imposible que el objetivo esté ahí. Descartamos toda esa mitad moviendo `izquierda` a `medio + 1` (el `+1` es clave: ya revisamos `medio`, no hay que volver a incluirlo, o entrarías en bucle infinito — ver §7).

- **`else derecha = medio - 1;`** — el del medio es **mayor**. Todo a la derecha es aún más grande, imposible que esté el objetivo. Movemos `derecha` a `medio - 1`.

- **`return -1;`** — si salimos del `while` (la zona se vació) sin haber devuelto, el objetivo no estaba. Por convención universal se devuelve −1 ("no encontrado").

### 4.6 La ejecución completa, paso a paso, con TODAS las variables

Las tablas resumen están bien, pero aquí lo hacemos exhaustivo: **cada iteración, mostrando el estado completo**, para que veas la máquina por dentro. Usamos:

```
posición:  0    1    2    3    4    5    6    7    8
valor:     3    9   15   22   31   48   59   73   88
```

### Caso A: buscar el 73 (que SÍ está)

**Estado inicial:** `izquierda = 0`, `derecha = 8`. Zona = todo.

**Iteración 1:**
- ¿`izquierda(0) <= derecha(8)`? Sí → entramos al bucle.
- `medio = 0 + (8 - 0)/2 = 0 + 4 = 4`.
- `arr[4]` = 31.
- ¿31 == 73? No.
- ¿31 < 73? Sí → el objetivo está a la derecha → `izquierda = medio + 1 = 5`.
- **Acabamos de descartar las posiciones 0,1,2,3,4 de un solo golpe.** Zona ahora: posiciones 5 a 8.

**Iteración 2:**
- ¿`izquierda(5) <= derecha(8)`? Sí.
- `medio = 5 + (8 - 5)/2 = 5 + 1 = 6`.
- `arr[6]` = 59.
- ¿59 == 73? No.
- ¿59 < 73? Sí → `izquierda = 6 + 1 = 7`.
- Zona ahora: posiciones 7 a 8.

**Iteración 3:**
- ¿`izquierda(7) <= derecha(8)`? Sí.
- `medio = 7 + (8 - 7)/2 = 7 + 0 = 7`.
- `arr[7]` = 73.
- ¿73 == 73? **¡Sí!** → `return 7`.

**Resultado: posición 7.** Lo encontramos en **3 comparaciones**, no 8. Con 9 elementos la diferencia es pequeña; con mil millones, serían ~30 comparaciones en vez de mil millones.

### Caso B: buscar el 50 (que NO está) — para ver cómo TERMINA

Esto es vital: hay que ver que el bucle **termina** y no se cuelga cuando el objetivo no existe.

**Estado inicial:** `izquierda = 0`, `derecha = 8`.

**Iteración 1:** `medio = 4`, `arr[4] = 31`. 31 < 50 → `izquierda = 5`. Zona: 5–8.
**Iteración 2:** `medio = 6`, `arr[6] = 59`. 59 > 50 → `derecha = 5`. Zona: 5–5.
**Iteración 3:** `medio = 5`, `arr[5] = 48`. 48 < 50 → `izquierda = 6`. Zona: 6–5.
**Comprobación del while:** ¿`izquierda(6) <= derecha(5)`? **NO** (6 no es ≤ 5). El bucle termina.
**`return -1`.** Correcto: el 50 no está.

🔑 Fíjate cómo la zona se hizo **inválida** (`izquierda` rebasó a `derecha`): esa es la señal de "ya no queda dónde buscar", y es lo que garantiza que el algoritmo siempre termina.

### 4.7 Los tres bugs clásicos (y POR QUÉ ocurren)

Estos tres errores son los que hacen fallar a la gente en entrevistas en vivo. No basta con "evitarlos": hay que entender por qué pasan.

**Bug 1 — Usar `<` en vez de `<=` en el while.**
Si escribes `while (izquierda < derecha)`, dejas de revisar el caso en que la zona tiene **un solo elemento** (`izquierda == derecha`). 
- *Cómo se manifiesta:* el algoritmo falla **solo a veces** — específicamente cuando el objetivo está en una posición que queda como zona de tamaño 1. Es un bug intermitente, los peores.
- *Ejemplo concreto:* busca el 88 (última posición) en nuestro arreglo. Con `<` llegarías a `izquierda = derecha = 8` y el while saldría sin revisar la posición 8, devolviendo −1 incorrectamente.

**Bug 2 — Mover los marcadores a `medio` en vez de `medio ± 1`.**
Si escribes `izquierda = medio` (sin el `+1`):
- *Cómo se manifiesta:* **bucle infinito**, el programa se cuelga. 
- *Por qué:* imagina `izquierda = 0, derecha = 1`. `medio = 0`. Si `arr[0] < objetivo` y haces `izquierda = medio = 0`, ¡no cambió nada! `izquierda` sigue en 0, vuelves a calcular el mismo `medio = 0`, eternamente. El `+1` garantiza que la zona **siempre se encoge**, lo que garantiza terminación.

**Bug 3 — `(izquierda + derecha) / 2` y el overflow.**
- *Cómo se manifiesta:* funciona en todas tus pruebas con arreglos chicos y **explota en producción** con arreglos enormes. 
- *Por qué:* si `izquierda` y `derecha` son cercanos al máximo de un `int` (~2.100 millones), su suma se pasa del límite y se vuelve un número **negativo** (overflow). Entonces `medio` es negativo → `arr[medio]` revienta. La fórmula `izquierda + (derecha - izquierda)/2` evita sumar los dos grandes. *Este es el detalle que separa una respuesta "correcta" de una "correcta y robusta" en una entrevista de empresa seria.*

### 4.8 La complejidad, derivada de verdad (no solo "es O(log n)")

¿Por qué exactamente O(log n)? Derivémoslo.

En cada iteración, la zona de búsqueda se reduce **a la mitad**. Si empiezas con `n` elementos, las zonas van siendo:

```
n  →  n/2  →  n/4  →  n/8  →  ...  →  1
```

La pregunta es: **¿cuántas veces puedo dividir `n` entre 2 hasta llegar a 1?** Llamemos a ese número de veces `k`. Entonces:

```
n / 2^k = 1
n = 2^k
```

Despejando `k`, eso es exactamente la definición de logaritmo base 2: `k = log₂(n)`.

- Para `n = 8`: log₂(8) = 3 (porque 2³ = 8). Máximo 3 pasos. ✓ (lo viste en el Caso A)
- Para `n = 1.000`: ~10 pasos.
- Para `n = 1.000.000`: ~20 pasos.
- Para `n = 1.000.000.000`: ~30 pasos.

**Por eso la búsqueda binaria es O(log n).** Y por eso es casi mágica: **multiplicar el tamaño por mil solo añade ~10 pasos.** Duplicar los datos añade **un** paso. Compáralo con O(n), donde duplicar los datos duplica el trabajo.

**Complejidad de espacio:** O(1). No creamos estructuras nuevas; solo usamos tres variables (`izquierda`, `derecha`, `medio`) sin importar el tamaño del arreglo. (La versión recursiva sería O(log n) de espacio por la pila de llamadas — ver §11.)

### 4.9 Todos los casos borde (la prueba de que tu código es correcto)

Un buen ingeniero prueba su algoritmo contra los bordes. Aquí están todos, con el resultado esperado:

| Caso borde | Entrada | Resultado esperado | ¿Por qué importa? |
|---|---|---|---|
| Arreglo vacío | `[]`, buscar 5 | −1 | `derecha = -1`, el while ni entra. Debe no romper. |
| Un solo elemento, está | `[5]`, buscar 5 | 0 | `izquierda=derecha=0`, lo revisa (gracias al `<=`). |
| Un solo elemento, no está | `[5]`, buscar 9 | −1 | Lo revisa, no casa, zona se invalida. |
| Objetivo es el primero | `[1,2,3]`, buscar 1 | 0 | El algoritmo baja `derecha` hasta aislarlo. |
| Objetivo es el último | `[1,2,3]`, buscar 3 | 2 | El algoritmo sube `izquierda` hasta aislarlo. |
| Objetivo menor que todos | `[10,20]`, buscar 5 | −1 | `derecha` baja hasta −1; termina. |
| Objetivo mayor que todos | `[10,20]`, buscar 99 | −1 | `izquierda` sube hasta length; termina. |

> 💡 **En la entrevista:** enumerar estos casos en voz alta —*antes* de que el entrevistador te los pida— es señal de mentalidad de calidad. Para ti, con fondo de QA, esto es una **ventaja natural**: piensas en bordes mejor que un dev promedio. Explótalo.

### 4.10 "¿Y si no está ordenado?" — el trade-off completo

La búsqueda binaria exige orden. ¿Qué haces si te dan datos desordenados?

- **Opción A — ordenar primero, luego binaria.** Ordenar cuesta O(n log n); la binaria, O(log n). Total: O(n log n). 
  - **¿Vale la pena?** Solo si vas a hacer **muchas** búsquedas sobre los mismos datos. Ordenas una vez (caro) y luego cada búsqueda es baratísima (log n). Si haces miles de búsquedas, ganas muchísimo.
  - **¿Cuándo NO vale?** Si solo vas a buscar **una vez**, ordenar (O(n log n)) es más caro que una sola búsqueda lineal (O(n)). En ese caso, búsqueda lineal gana.
- **Opción B — usar un HashSet.** Si solo te importa "¿existe?" y no la posición, mete todo en un HashSet: construirlo es O(n), y cada búsqueda es O(1). A menudo gana a la binaria si no necesitas el orden para otra cosa.

🔑 **Esta discusión de trade-offs es justo lo que un entrevistador senior quiere oír.** No hay una respuesta "correcta" única; hay una respuesta correcta **según el contexto**, y demostrar que piensas en ese contexto es lo que te separa.

### 4.11 Variantes que SÍ caen en entrevistas

La búsqueda binaria "buscar un valor" es solo la versión básica. Estas variantes son las que de verdad preguntan:

**Variante 1 — Primera o última aparición de un valor repetido.**
Si el arreglo tiene duplicados (`[1,2,2,2,3]`) y te piden la **primera** posición del 2, no basta con encontrar *un* 2: al encontrarlo, **no paras**; sigues buscando hacia la izquierda (`derecha = medio - 1`) guardando el candidato, para ver si hay otro 2 antes. Para la **última**, buscas hacia la derecha.
```java
// Primera aparición de 'objetivo'
int resultado = -1;
while (izquierda <= derecha) {
    int medio = izquierda + (derecha - izquierda) / 2;
    if (arr[medio] == objetivo) { resultado = medio; derecha = medio - 1; } // sigue a la izq
    else if (arr[medio] < objetivo) izquierda = medio + 1;
    else derecha = medio - 1;
}
return resultado;
```

**Variante 2 — Buscar en un arreglo ordenado pero ROTADO.**
`[4,5,6,7,0,1,2]` está ordenado pero "rotado". Sigue siendo binaria, pero en cada paso identificas **qué mitad está ordenada** (comparando `arr[izquierda]` con `arr[medio]`) y decides hacia dónde ir según si el objetivo cae en esa mitad ordenada. Es la binaria "con un giro" y es un clásico de FAANG.

**Variante 3 — "Búsqueda binaria sobre la respuesta".**
La más avanzada y la que más impresiona. A veces no buscas en un arreglo, sino en un **rango de respuestas posibles**. Ejemplo: "¿cuál es la menor capacidad de un barco para enviar todos los paquetes en D días?". La capacidad posible va de un mínimo a un máximo; haces **búsqueda binaria sobre ese rango de capacidades**, y para cada capacidad candidata verificas (con una función auxiliar) si es factible. La señal: "minimiza/maximiza un valor tal que se cumpla una condición monótona".

### 4.12 Cómo reconocer que un problema pide búsqueda binaria

Las señales, ordenadas por qué tan obvias son:
1. **Explícita:** "el arreglo está ordenado" + "busca/encuentra". Casi grita búsqueda binaria.
2. **Por la complejidad pedida:** si el problema dice "hazlo en O(log n)" sobre datos ordenados, es binaria (es de las pocas cosas O(log n) que existen).
3. **Oculta (la avanzada):** "encuentra el mínimo/máximo valor que cumple X", donde "cumplir X" es **monótono** (si un valor cumple, todos los mayores también, o viceversa). Eso es búsqueda binaria sobre la respuesta.

### 4.13 Receta para construirla tú mismo (chuleta mental)

Cuando la necesites y no recuerdes el código, reconstrúyela con esto:
1. ¿Están **ordenados** los datos? Si no, la binaria no aplica directo.
2. `izquierda = 0`, `derecha = n - 1`.
3. `while (izquierda <= derecha)` — recuerda el `<=`.
4. `medio = izquierda + (derecha - izquierda) / 2` — recuerda la forma anti-overflow.
5. Tres casos: igual → devuelve; menor → `izquierda = medio + 1`; mayor → `derecha = medio - 1`.
6. Fuera del bucle → `return -1`.
7. **Mentalmente, traza con [1,3,5] buscando 5 y buscando 4** para verificar que no tienes bug de límites.

### 4.14 Práctica, con respuestas

**P1.** En `[2, 5, 8, 12, 16, 23, 38]`, traza la búsqueda del 23. ¿Cuántas comparaciones?
> `medio=3 (12)`, 12<23 → izq=4. `medio=5 (23)` → encontrado en 2 comparaciones, posición 5.

**P2.** ¿Por qué la búsqueda binaria no sirve sobre una lista enlazada, aunque esté ordenada?
> Porque una lista enlazada **no tiene acceso por índice O(1)**: llegar al elemento "del medio" cuesta O(n) (hay que recorrer nodo por nodo). Sin acceso O(1) al medio, se pierde toda la ventaja. La binaria necesita acceso aleatorio, propio de los arreglos.

**P3.** Tienes un arreglo ordenado de 1.000.000 de elementos. En el peor caso, ¿cuántas comparaciones hace la búsqueda binaria?
> ~20 (log₂ de 1.000.000 ≈ 20).

**P4.** ¿Qué bug tiene este código? `while (izquierda < derecha)` con todo lo demás correcto.
> Bug 1 (§7): el `<` en vez de `<=` deja sin revisar la zona de tamaño 1. Falla cuando el objetivo está en esa última posición aislada.

**P5.** Te dan un arreglo desordenado y debes hacer UNA sola búsqueda. ¿Conviene ordenar + binaria, o búsqueda lineal? Justifica.
> Búsqueda lineal (O(n)). Ordenar cuesta O(n log n), más caro que una sola búsqueda lineal. Ordenar solo conviene si harás muchas búsquedas.

---

## 🧠 Patrón 5 — Recursión · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** funciones y parámetros (cómo se llama una función y cómo devuelve un valor) · **pilas** (cap. 3, porque la recursión usa la "pila de llamadas" por dentro — sin esto, no entenderás *cómo* funciona). La recursión es **prerrequisito** de árboles, grafos, backtracking y DP. Es el salto conceptual más importante del manual: tómate tu tiempo aquí.

### 5.A El problema que la recursión resuelve

Algunos problemas son, por naturaleza, **versiones más pequeñas de sí mismos**. Piensa en un sistema de carpetas: una carpeta contiene archivos y... otras carpetas, que a su vez contienen archivos y carpetas. Para contar todos los archivos, "abre cada subcarpeta y haz lo mismo". O piensa en el factorial: 4! = 4 × 3!, y 3! = 3 × 2!... cada paso es el mismo problema, más pequeño. **El problema es: ¿cómo resuelvo algo que se define en términos de sí mismo?** La respuesta es la recursión: una función que **se llama a sí misma** sobre una versión más pequeña del problema.

### 5.B Qué es, exactamente

**Recursión** es cuando una función **se llama a sí misma** para resolver un problema, delegando una **versión más pequeña** del mismo problema, hasta llegar a un caso tan simple que la respuesta es obvia.

Toda función recursiva tiene **dos partes obligatorias**:
1. **Caso base:** la condición en la que el problema es tan pequeño que respondes directo, **sin volver a llamarte**. Es el freno que detiene la recursión.
2. **Caso recursivo:** te llamas a ti mismo con una entrada más pequeña, acercándote al caso base, y combinas ese resultado con el trabajo del paso actual.

🏠 **Analogía: las muñecas rusas (matrioskas).** Abres una muñeca y dentro hay otra más pequeña; la abres y dentro hay otra... hasta la más chiquita que **ya no se abre** (el caso base). El proceso de "abrir la siguiente" es el caso recursivo; la muñeca sólida que no abre es lo que detiene todo.

🏠 **Segunda analogía (para el caso recursivo): la fila.** Estás en una fila larga y quieres saber tu posición. Le preguntas al de adelante: "¿en qué número vas?". Él le pregunta al de adelante, y así hasta el primero, que responde "voy en la 1" (caso base). Esa respuesta viaja hacia atrás, cada quien suma 1, hasta llegar a ti. **Tú no necesitas ver toda la fila: confías en que el de adelante te dará su número correcto y le sumas 1.**

### 5.C El "salto de fe recursivo" (la clave mental que destraba todo)

Esto es lo que más cuesta y lo que, una vez que lo captas, lo cambia todo:

> 🔑 **NO intentes seguir todas las llamadas en tu cabeza** — te marearás y te bloquearás. En lugar de eso, **confía** en que la llamada recursiva devuelve la respuesta correcta para el problema más pequeño, y solo decide **qué haces tú con esa respuesta**. A esto se le llama el *salto de fe recursivo*.
>
> Ejemplo: al escribir `factorial(n)`, NO trates de imaginar `factorial(4)` desenrollando `factorial(3)`, `factorial(2)`... Solo asume: *"factorial(n-1) ya me da el factorial de n-1, correcto. Entonces yo solo lo multiplico por n."* Eso es todo. La recursión se vuelve fácil cuando dejas de perseguir las llamadas y confías en ellas.

### 5.D Cómo funciona por dentro: la pila de llamadas

🔧 Aquí es donde la dependencia de **pilas** (cap. 3) paga. Cada vez que una función se llama (a sí misma o a otra), la computadora **apila** un "marco" (frame) con sus variables y dónde debe regresar. Cuando la función termina, su marco se **desapila** y el control vuelve a quien la llamó. La recursión, entonces, es literalmente **apilar llamadas hasta el caso base, y luego desapilar resolviéndolas en orden inverso**.

🔧 Por eso una recursión **sin caso base** (o que nunca lo alcanza) llena la pila hasta reventar → **`StackOverflowError`**. Es, literalmente, "la pila de llamadas se desbordó".

### 5.E Ejemplo 1: factorial, con traza completa de la pila

```java
public static int factorial(int n) {
    if (n <= 1) return 1;             // CASO BASE: detiene la recursión
    return n * factorial(n - 1);     // CASO RECURSIVO: problema más pequeño
}
```

✍️ **Traza de `factorial(4)`, mostrando la pila crecer y desapilar:**

**Fase de IDA (se apila, "bajando" hacia el caso base):**
```
llamo factorial(4) → necesita 4 * factorial(3), se pausa y apila          [pila: f(4)]
  llamo factorial(3) → necesita 3 * factorial(2), se pausa y apila        [pila: f(4), f(3)]
    llamo factorial(2) → necesita 2 * factorial(1), se pausa y apila      [pila: f(4), f(3), f(2)]
      llamo factorial(1) → n<=1, CASO BASE, devuelve 1                    [pila: f(4), f(3), f(2), f(1)]
```
**Fase de VUELTA (se desapila, "subiendo" resolviendo):**
```
      factorial(1) devolvió 1, se desapila
    factorial(2) = 2 * 1 = 2, devuelve 2, se desapila
  factorial(3) = 3 * 2 = 6, devuelve 6, se desapila
factorial(4) = 4 * 6 = 24, devuelve 24, se desapila
```
**Resultado: 24.** Observa el patrón: **primero se apilan todas las llamadas hasta el caso base, luego se resuelven de adentro hacia afuera.**

### 5.F Ejemplo 2: suma de un arreglo (recursión sobre una colección)

```java
public static int suma(int[] arr, int i) {
    if (i == arr.length) return 0;            // CASO BASE: ya no hay elementos
    return arr[i] + suma(arr, i + 1);         // este + la suma del resto
}
// suma([1,2,3], 0): 1 + (2 + (3 + 0)) = 6
```
🗝️ **Clave:** "este elemento + la suma de los que faltan". Confías en que `suma(arr, i+1)` ya suma el resto (salto de fe).

### 5.G Ejemplo 3: invertir un string (recursión sobre texto)

```java
public static String invertir(String s) {
    if (s.length() <= 1) return s;                    // CASO BASE
    return invertir(s.substring(1)) + s.charAt(0);    // invierte el resto, + el primero al final
}
// invertir("abc") = invertir("bc") + 'a' = (invertir("c")+'b') + 'a' = ("c"+'b')+'a' = "cba"
```

### 5.H Ejemplo 4: Fibonacci, y POR QUÉ la recursión ingenua es lenta

```java
public static int fib(int n) {
    if (n <= 1) return n;                  // casos base: fib(0)=0, fib(1)=1
    return fib(n - 1) + fib(n - 2);        // DOS llamadas por nivel
}
```
🔧 **El problema:** dos llamadas recursivas por nivel hacen que el "árbol de llamadas" se **duplique** en cada nivel. Y peor: **recalcula los mismos valores muchas veces.** Mira el árbol de `fib(5)`:
```
                    fib(5)
              /                \
          fib(4)              fib(3)
         /      \            /      \
     fib(3)    fib(2)    fib(2)    fib(1)
     /   \      /  \      /  \
  fib(2) fib(1) ...      ...        ← fib(2) se calcula 3 veces, fib(3) dos veces...
```
`fib(3)` se calcula 2 veces, `fib(2)` 3 veces, y empeora con n. Esto es **O(2ⁿ)** — exponencial, inservible para n grande (fib(50) haría ~mil millones de llamadas).
🗝️ **La cura es la memoización** → guardar cada resultado la primera vez para no recalcularlo. Eso convierte O(2ⁿ) en **O(n)**, y es justo el tema del Patrón 13 (Programación Dinámica). *La recursión es la puerta a la DP.*

### 5.I Recursión vs. iteración

Todo lo que haces con recursión, puedes hacerlo con un bucle (iteración) y una **pila explícita** — porque la recursión *es* una pila por dentro. ¿Cuándo cada una?
- **Recursión:** más natural y legible para problemas **auto-similares** (árboles, grafos, "divide y vencerás", backtracking). El precio: usa **O(profundidad)** de espacio en la pila de llamadas, y puede dar `StackOverflowError` si es muy profunda.
- **Iteración:** más eficiente en memoria (sin pila de llamadas), pero a veces menos legible. Para recorridos lineales simples, casi siempre mejor.

🔑 **En la entrevista:** saber que "toda recursión se puede convertir en iteración con una pila explícita" y *por qué* (la recursión usa la call stack) es una respuesta que impresiona.

### 5.J Las claves para CONSTRUIR una solución recursiva (la receta)

Cuando enfrentes un problema recursivo, sigue esto en orden:
1. **Define el caso base PRIMERO.** Pregúntate: *¿cuál es la versión más pequeña del problema, tan simple que la respuesta es obvia y NO necesito recursión?* (lista vacía → 0; n≤1 → 1; nodo null → nada). Sin caso base → recursión infinita → crash.
2. **Define el caso recursivo con el salto de fe.** Asume que la llamada recursiva sobre el problema más pequeño **ya funciona**, y pregúntate: *¿cómo combino ese resultado con el trabajo de este paso?*
3. **Asegura el progreso.** Cada llamada debe acercarse al caso base (n-1, mitad, el siguiente índice/nodo). Si no, nunca paras.
4. **Confía y prueba.** Traza un caso pequeño a mano (como en §5.E) para validar.

### 5.K Bugs clásicos (y por qué)

**Bug 1 — Sin caso base (o nunca se alcanza).** `StackOverflowError`. *Por qué:* la pila de llamadas crece sin fin. *Solución:* escribe el caso base **primero** y verifica que el caso recursivo siempre se acerque a él.
**Bug 2 — El caso recursivo no reduce el problema.** Ej. `factorial(n)` que llama `factorial(n)` en vez de `factorial(n-1)` → bucle infinito. *Solución:* confirma que el argumento "encoge" en cada llamada.
**Bug 3 — Recursión exponencial sin memoización** (como fib ingenuo) → lentísimo. *Solución:* si ves que recalculas subproblemas, memoiza (DP).
**Bug 4 — Recursión demasiado profunda en datos grandes** → StackOverflow aunque la lógica sea correcta. *Solución:* convertir a iterativo si la profundidad puede ser enorme.

### 5.L Complejidad de la recursión

- **Tiempo:** (número de llamadas) × (trabajo por llamada). Una recursión lineal (1 llamada por nivel, n niveles) es O(n). Una con 2 llamadas por nivel sin memoizar es O(2ⁿ).
- **Espacio:** O(profundidad máxima de la recursión), por la pila de llamadas. Una recursión lineal de profundidad n usa O(n) de pila aunque no cree estructuras.

### 5.M Cómo reconocer que un problema pide recursión

1. El problema se **define en términos de sí mismo** (factorial, Fibonacci).
2. La estructura de datos es **auto-similar/jerárquica**: árboles, grafos, carpetas anidadas.
3. "Genera **todas** las combinaciones/permutaciones/caminos" → recursión + backtracking (Patrón 6).
4. "Divide y vencerás": parte el problema en mitades, resuelve cada una recursivamente y combina (merge sort, búsqueda binaria).

### 5.N Práctica, con respuestas

**P1.** ¿Cuáles son las dos partes obligatorias de toda función recursiva?
> Caso base (detiene) y caso recursivo (se llama con una entrada más pequeña, acercándose al caso base).

**P2.** Traza `factorial(3)`. ¿Cuántas llamadas y cuál es el resultado?
> f(3)=3*f(2)=3*(2*f(1))=3*(2*1)=6. Tres llamadas recursivas (f(3), f(2), f(1)). Resultado 6.

**P3.** ¿Por qué `fib` recursivo ingenuo es O(2ⁿ) y cómo se arregla?
> Porque hace 2 llamadas por nivel y recalcula los mismos subproblemas muchas veces. Se arregla con memoización (guardar cada resultado), bajándolo a O(n).

**P4.** ¿Qué causa un `StackOverflowError` en recursión?
> No tener caso base, o que el caso recursivo nunca lo alcance: la pila de llamadas crece hasta desbordarse.

**P5.** Escribe el caso base y el recursivo para "contar los elementos de una lista enlazada".
> Base: si el nodo es null, devuelve 0. Recursivo: `1 + contar(nodo.siguiente)`.

**P6.** ¿Por qué la recursión usa memoria aunque no cree estructuras?
> Por la pila de llamadas: cada llamada pendiente ocupa un marco; la profundidad determina el espacio O(profundidad).

📚 **Recursos:** "Grokking Algorithms" — cap. de recursión (el más amigable que existe) · VisuAlgo — Recursion · Abdul Bari (YouTube) — "Recursion".

---
## 🧠 Patrón 6 — Backtracking · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** **recursión sólida** (Patrón 5 — el backtracking *es* recursión que explora opciones; sin recursión firme, no hay backtracking) · la **pila de llamadas** (cap. 3) · listas/arreglos para llevar el estado parcial. Es la base de muchos problemas "genera todas las...".

### 6.A El problema que el backtracking resuelve

A veces no quieres *una* respuesta, sino **TODAS** las posibilidades: todos los subconjuntos de un conjunto, todas las formas de ordenar unas letras (permutaciones), todas las combinaciones que suman a un número, todas las formas de colocar 8 reinas en un tablero sin que se ataquen, todas las palabras que se pueden formar en un Boggle. **El problema es: ¿cómo exploro sistemáticamente *todas* las combinaciones posibles, sin olvidar ninguna y sin repetir?** La respuesta es el backtracking.

### 6.B La solución obvia (y por qué no basta)

Para "todas las parejas" bastan dos bucles anidados. Para "todos los tríos", tres bucles. ¿Y para "todos los subconjuntos de tamaño variable"? No puedes escribir un número fijo de bucles anidados cuando la **profundidad depende de la entrada**. **La pregunta:** ¿cómo genero "bucles anidados de profundidad variable"? La recursión lo hace: cada nivel de recursión es "un bucle más".

### 6.C La idea central, construida desde cero

🏠 **Analogía: explorar un laberinto con un hilo.** Avanzas por un pasillo. En cada cruce, eliges un camino y lo marcas con tu hilo. Si llegas a un muro (callejón sin salida), **regresas** (back-track) recogiendo el hilo hasta el último cruce, y pruebas **otro** camino. Repitiendo esto, exploras **todos** los caminos posibles sin perderte ni repetir. Las tres acciones son: **elegir** un camino, **explorar** a fondo, y si no sirve, **deshacer** (recoger el hilo) y probar el siguiente.

> 🔑 **EL INSIGHT CENTRAL — "elige · explora · deshaz":** el backtracking construye soluciones **paso a paso**. En cada paso: (1) **elige** una opción y añádela a la solución parcial; (2) **explora** recursivamente con esa elección hecha; (3) cuando esa rama se agota, **deshaz** la elección (quítala) para dejar el estado limpio y poder probar la siguiente opción. Ese "deshacer" es lo que da el nombre *backtracking* y es **el paso que la gente olvida**.

### 6.D El esqueleto mental universal (memorízalo)

```
backtrack(solucionParcial, opcionesDisponibles):
    si (solucionParcial está completa):
        guardar una copia de solucionParcial
        return
    para cada opción en opcionesDisponibles:
        elegir opción        → añadir a solucionParcial
        backtrack(...)        → explorar con la elección hecha
        deshacer opción       → quitar de solucionParcial  (¡el paso clave!)
```
Casi todos los problemas de backtracking son **este esqueleto** con pequeñas variaciones en "qué es una solución completa" y "cuáles son las opciones".

### 6.E El algoritmo en español (subconjuntos), sin código

Para generar **todos los subconjuntos** de `[1,2,3]`:
1. Lleva una lista `actual` (el subconjunto que vas construyendo) y un índice `inicio` (desde dónde puedes elegir, para no repetir).
2. **Cada estado parcial ya es un subconjunto válido** → guárdalo apenas entras.
3. Para cada elemento desde `inicio` hasta el final:
   a. **Elige:** agrégalo a `actual`.
   b. **Explora:** llama recursivamente avanzando el índice (para que cada elemento se considere una sola vez).
   c. **Deshaz:** quítalo de `actual`, para probar el siguiente elemento desde un estado limpio.

### 6.F El código, y cada línea bajo el microscopio

```java
public static List<List<Integer>> subconjuntos(int[] nums) {
    List<List<Integer>> res = new ArrayList<>();
    backtrack(nums, 0, new ArrayList<>(), res);
    return res;
}
private static void backtrack(int[] nums, int inicio,
                              List<Integer> actual, List<List<Integer>> res) {
    res.add(new ArrayList<>(actual));            // (A) guarda una COPIA del estado actual
    for (int i = inicio; i < nums.length; i++) {
        actual.add(nums[i]);                     // (B) ELIGE
        backtrack(nums, i + 1, actual, res);     // (C) EXPLORA (i+1: no repetir)
        actual.remove(actual.size() - 1);        // (D) DESHAZ
    }
}
```

- **(A) `res.add(new ArrayList<>(actual));`** — guarda el subconjunto actual. ⚠️ Hay que guardar una **copia** (`new ArrayList<>(actual)`), no `actual` directo: `actual` se sigue modificando después, y si guardaras la referencia, todos los resultados acabarían apuntando a la misma lista (vacía al final). *Bug clásico.*
- **`for (int i = inicio; ...)`** — recorre las opciones disponibles desde `inicio`. Empezar en `inicio` (y no en 0) evita generar el mismo subconjunto en distinto orden (`[1,2]` y `[2,1]`).
- **(B) `actual.add(nums[i]);`** — **elige** el elemento `i`.
- **(C) `backtrack(nums, i + 1, actual, res);`** — **explora** con esa elección. El `i + 1` asegura que cada elemento se use una sola vez por rama.
- **(D) `actual.remove(actual.size() - 1);`** — **deshaz**: quita el último elegido para que la siguiente vuelta del `for` parta de un estado limpio. *Sin esta línea, los elementos se acumularían y el resultado sería incorrecto.*

### 6.G La ejecución completa, paso a paso (árbol de decisiones)

`nums = [1, 2, 3]`. El backtracking construye este árbol (cada nodo guarda el estado `actual` al entrar):
```
[]                                  ← guarda []
├─ elige 1 → [1]                    ← guarda [1]
│   ├─ elige 2 → [1,2]              ← guarda [1,2]
│   │   └─ elige 3 → [1,2,3]        ← guarda [1,2,3]; deshaz 3
│   │   (deshaz 2)
│   └─ elige 3 → [1,3]              ← guarda [1,3]; deshaz 3
│   (deshaz 1)
├─ elige 2 → [2]                    ← guarda [2]
│   └─ elige 3 → [2,3]              ← guarda [2,3]; deshaz 3
│   (deshaz 2)
└─ elige 3 → [3]                    ← guarda [3]; deshaz 3
```
**Resultado (8 subconjuntos):** `[], [1], [1,2], [1,2,3], [1,3], [2], [2,3], [3]`. Observa cómo el "deshaz" permite que, tras explorar la rama del 1, el árbol vuelva a `[]` para explorar la del 2.

### 6.H Segundo ejemplo: permutaciones (misma receta, opciones distintas)

Para **todas las ordenaciones** de `[1,2,3]`: aquí una solución está completa cuando usa **todos** los elementos, y las opciones son "los elementos aún no usados".
```java
public static List<List<Integer>> permutaciones(int[] nums) {
    List<List<Integer>> res = new ArrayList<>();
    backtrack(nums, new boolean[nums.length], new ArrayList<>(), res);
    return res;
}
private static void backtrack(int[] nums, boolean[] usado,
                              List<Integer> actual, List<List<Integer>> res) {
    if (actual.size() == nums.length) {           // solución completa: usó todos
        res.add(new ArrayList<>(actual)); return;
    }
    for (int i = 0; i < nums.length; i++) {
        if (usado[i]) continue;                   // salta los ya usados
        usado[i] = true; actual.add(nums[i]);     // ELIGE
        backtrack(nums, usado, actual, res);      // EXPLORA
        usado[i] = false; actual.remove(actual.size()-1);  // DESHAZ (ambas cosas)
    }
}
// [1,2,3] -> [1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]
```
🗝️ **Clave:** misma plantilla "elige · explora · deshaz". Lo único que cambia entre problemas de backtracking es **qué es "completa"** y **cuáles son las opciones**.

### 6.I Bugs clásicos (y por qué)

**Bug 1 — Olvidar el "deshaz".** El estado parcial se contamina entre ramas y el resultado es basura. *Por qué:* sin limpiar la elección, la siguiente opción del `for` parte de un estado sucio. *Es EL bug del backtracking.*
**Bug 2 — Guardar la referencia en vez de una copia.** `res.add(actual)` en lugar de `res.add(new ArrayList<>(actual))`: como `actual` se sigue mutando, todos los resultados terminan iguales (vacíos). *Solución:* siempre copia al guardar.
**Bug 3 — No avanzar el índice / no marcar usados.** Genera duplicados o permutaciones donde no debía. *Solución:* `i+1` para combinaciones; arreglo `usado` para permutaciones.

### 6.J La complejidad (y por qué suele ser exponencial)

El backtracking explora **todas** las posibilidades, así que su costo refleja **cuántas hay**:
- **Subconjuntos:** 2ⁿ (cada elemento entra o no) → **O(2ⁿ)**.
- **Permutaciones:** n! (todas las ordenaciones) → **O(n!)**.
Es **inevitablemente exponencial** porque la *salida misma* es exponencial. ⚠️ Por eso el backtracking solo es viable para **n pequeño**. Si te piden "todas las combinaciones" con n grande, probablemente el problema real pide otra cosa (a menudo **DP**, que cuenta sin enumerar).

🔧 **Optimización — "poda" (pruning):** si puedes detectar temprano que una rama **nunca** llevará a una solución válida, la cortas sin explorarla (ej. en N-reinas, si dos reinas ya se atacan, no sigas). La poda no cambia el peor caso teórico, pero acelera muchísimo en la práctica.

### 6.K Cómo reconocer que un problema pide backtracking

1. La palabra **"todas/todos"**: "**todas** las combinaciones/permutaciones/subconjuntos/caminos/formas".
2. "Genera/enumera/lista" + algo combinatorio.
3. Construyes una solución por **decisiones secuenciales** y cada decisión abre nuevas opciones.
4. Clásicos: subconjuntos, permutaciones, combinaciones que suman X, generar paréntesis válidos, N-reinas, sudoku, partición de palabras.

### 6.L Receta para construirlo tú mismo

1. **¿Qué es una "solución completa"?** (un subconjunto cualquiera; una permutación de longitud n; un tablero lleno). Eso define el caso base/guardado.
2. **¿Cuáles son las opciones** en cada paso? (los elementos desde `inicio`; los no usados; las casillas válidas).
3. Aplica **elige · explora · deshaz** en el `for`.
4. **Guarda una COPIA** cuando llegues a una solución.
5. Añade **poda** si puedes descartar ramas inválidas temprano.

### 6.M Práctica, con respuestas

**P1.** ¿Cuáles son los tres pasos del esqueleto de backtracking?
> Elegir una opción, explorar recursivamente, y deshacer la elección (backtrack).

**P2.** ¿Por qué hay que guardar `new ArrayList<>(actual)` y no `actual`?
> Porque `actual` se sigue modificando; guardar la referencia haría que todos los resultados apunten a la misma lista (vacía al final). Hay que copiar.

**P3.** ¿Qué pasa si olvidas la línea "deshaz"?
> El estado parcial se contamina entre ramas: los elementos se acumulan y el resultado es incorrecto.

**P4.** ¿Cuántos subconjuntos tiene un conjunto de n elementos y por qué?
> 2ⁿ, porque cada elemento puede estar o no estar (2 opciones × n elementos).

**P5.** ¿Cuál es la complejidad de generar todas las permutaciones de n elementos?
> O(n!), porque hay n! ordenaciones posibles.

**P6.** Te piden "todas las combinaciones de monedas que suman 11". ¿Patrón? ¿Y si te pidieran solo "el número mínimo de monedas"?
> "Todas" → backtracking. "Mínimo número" → programación dinámica (cuenta el óptimo sin enumerar todo).

📚 **Recursos:** NeetCode — "Backtracking" (subsets, permutations, combination sum, N-queens) · "Grokking the Coding Interview" — patrón de subconjuntos · VisuAlgo — Recursion (para ver el árbol de decisiones).

---
## 🧠 Patrón 7 — Recorrido de árboles (DFS y BFS) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** la estructura **árbol** (cap. 6 — ahí están los internals; aquí nos enfocamos en *resolver problemas*) · **recursión** (Patrón 5, para DFS) · **colas** (cap. 4, para BFS).
>
> 📎 Los internals de los recorridos (los tres DFS, BFS, la plantilla "pide a los hijos y combina") están desarrollados a fondo en el **capítulo 6 — Árboles**. Aquí va el ángulo de **entrevista**: cómo reconocer qué recorrido usar y resolver los problemas típicos.

### 7.A La decisión clave: ¿DFS o BFS?

Ante un problema de árbol, lo primero es elegir el recorrido, y la regla es simple:
- **¿La respuesta depende de la PROFUNDIDAD o de explorar ramas completas?** (altura, ¿es balanceado?, suma de caminos raíz-hoja, validar BST) → **DFS** (recursión).
- **¿La respuesta depende de los NIVELES o de la cercanía a la raíz?** ("recorrido por niveles", "vista lateral derecha", "nodo más cercano que cumple X", "anchura máxima") → **BFS** (cola).

🗝️ **Pista textual:** si el enunciado dice "nivel", "por niveles", "más cercano", piensa BFS. Si dice "camino", "profundidad", "subárbol", piensa DFS.

### 7.B Cómo construir la solución (las dos plantillas)

**Plantilla DFS — "pide a los hijos y combina":** resuelve el nodo actual asumiendo (salto de fe recursivo) que los hijos ya están resueltos.
```java
public static int altura(Nodo n) {
    if (n == null) return 0;                              // caso base
    return 1 + Math.max(altura(n.izq), altura(n.der));    // combina resultados de los hijos
}
```
Con esta forma resuelves altura, ¿balanceado?, suma total, diámetro, "¿son iguales dos árboles?", validar BST, etc. **Memoriza la forma, no cada problema.**

**Plantilla BFS — niveles con cola, procesando por tandas:**
```java
public static List<List<Integer>> porNiveles(Nodo raiz) {
    List<List<Integer>> res = new ArrayList<>();
    if (raiz == null) return res;
    Queue<Nodo> cola = new LinkedList<>();
    cola.add(raiz);
    while (!cola.isEmpty()) {
        int tam = cola.size();                  // CUÁNTOS hay en este nivel (la clave)
        List<Integer> nivel = new ArrayList<>();
        for (int i = 0; i < tam; i++) {         // procesa exactamente ese nivel
            Nodo n = cola.poll();
            nivel.add(n.valor);
            if (n.izq != null) cola.add(n.izq);
            if (n.der != null) cola.add(n.der);
        }
        res.add(nivel);
    }
    return res;
}
```
🗝️ **El truco del BFS por niveles:** capturar `cola.size()` **al inicio de cada vuelta** te dice cuántos nodos hay en el nivel actual, para procesarlos en tanda y separar niveles. Esto resuelve "vista lateral derecha" (el último de cada nivel), "nivel de suma máxima", "promedio por nivel", etc.

### 7.C Problemas típicos y qué plantilla usar

| Problema | Recorrido | Idea |
|---|---|---|
| Altura / profundidad máxima | DFS | 1 + max(hijos) |
| ¿Está balanceado? | DFS | comparar alturas de hijos |
| Validar BST | DFS (inorden) | inorden debe salir ordenado |
| Suma de caminos raíz→hoja | DFS | acumular al bajar |
| Recorrido por niveles | BFS | tandas por `cola.size()` |
| Vista lateral derecha | BFS | el último de cada nivel |
| Nodo más cercano con valor X | BFS | el primero que aparece |

### 7.D Práctica, con respuestas

**P1.** "Devuelve los valores nivel por nivel". ¿DFS o BFS y por qué?
> BFS: la respuesta se organiza por niveles, justo lo que da la cola procesando por tandas.

**P2.** ¿Cómo validas que un árbol es un BST con DFS?
> Recorrido inorden: debe producir valores estrictamente crecientes (o lleva límites min/max en la recursión).

**P3.** ¿Para qué sirve capturar `cola.size()` al inicio de cada vuelta del BFS?
> Para saber cuántos nodos hay en el nivel actual y procesarlos en una sola tanda, separando niveles.

📚 **Recursos:** NeetCode — "Trees" · VisuAlgo — Tree Traversal · (internals en el cap. 6 de este manual).

---

## 🧠 Patrón 8 — Recorrido de grafos (BFS / DFS con visitados) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** la estructura **grafo** (cap. 8 — internals, representaciones, por qué marcar visitados) · **colas** (BFS) · **recursión/pilas** (DFS) · **hash sets** (visitados).
>
> 📎 Los internals (lista vs matriz de adyacencia, la regla de visitados, traza de BFS/DFS) están en el **capítulo 8 — Grafos**. Aquí, el ángulo de entrevista: reconocer el grafo "escondido" y elegir el recorrido.

### 8.A Lo más difícil de los grafos en entrevista: ver el grafo oculto

Muchos problemas **no dicen** "grafo", pero lo son. Aprende a verlos:
- Una **matriz/cuadrícula** ("islas", "regiones", "flood fill"): cada celda es un nodo; sus vecinos son las celdas adyacentes (4 u 8).
- **Dependencias** ("orden de cursos/tareas", "¿se puede terminar?"): nodos = tareas, aristas = "requiere".
- **Estados y transiciones** ("transformar una palabra letra a letra", "menos pasos para..."): nodos = estados, aristas = movimientos válidos.
- **Relaciones** ("amigos de amigos", "¿conectados?"): obvio grafo.

🗝️ **Señal:** si puedes plantear "cosas + cómo se conectan + ¿llegar/contar/camino?", es un grafo aunque no lo nombre.

### 8.B Cómo construir la solución (los tres pasos universales)

1. **Representa** el grafo (lista de adyacencia por defecto; si es una cuadrícula, la matriz misma lo es).
2. **Elige el recorrido:**
   - **BFS** (cola) → "camino **más corto** en nº de pasos", "nivel/distancia mínima".
   - **DFS** (recursión) → "explorar/contar componentes", "¿existe un camino?", "marcar todo lo conectado".
3. **Marca visitados** (un `Set`, o modifica la propia cuadrícula) → sin esto, **bucle infinito**.

### 8.C Ejemplo: número de islas (DFS sobre cuadrícula)
```java
public static int contarIslas(char[][] grid) {
    int islas = 0;
    for (int i = 0; i < grid.length; i++)
        for (int j = 0; j < grid[0].length; j++)
            if (grid[i][j] == '1') { islas++; hundir(grid, i, j); }
    return islas;
}
private static void hundir(char[][] g, int i, int j) {
    if (i<0 || j<0 || i>=g.length || j>=g[0].length || g[i][j]=='0') return;
    g[i][j] = '0';                                            // marca visitado
    hundir(g,i+1,j); hundir(g,i-1,j); hundir(g,i,j+1); hundir(g,i,j-1);
}
```
🗝️ Cada vez que encuentras un '1' nuevo, es una isla nueva; el DFS "hunde" toda esa isla (la marca) para no contarla otra vez.

### 8.D Problemas típicos y qué usar

| Problema | Recorrido | Idea |
|---|---|---|
| Número de islas / regiones | DFS o BFS | contar grupos conectados, marcando |
| Camino más corto sin pesos | BFS | el primer arribo es el más corto |
| Camino más corto con pesos | Dijkstra | BFS + heap |
| Orden de tareas con dependencias | Topológico (DFS o Kahn/cola) | ordenar respetando "requiere" |
| ¿Se puede llegar de A a B? | DFS/BFS | ¿se visita B desde A? |
| Detectar ciclo | DFS | volver a un nodo "en proceso" |

### 8.E Práctica, con respuestas

**P1.** "Mínimo número de pasos para llegar de A a B en una cuadrícula". ¿Recorrido?
> BFS: en grafos sin pesos da el camino más corto en número de pasos.

**P2.** "¿En qué orden debo tomar cursos con prerrequisitos?". ¿Qué técnica?
> Orden topológico (DFS o algoritmo de Kahn con cola), porque hay dependencias dirigidas.

**P3.** ¿Por qué "número de islas" es un problema de grafos?
> Cada celda '1' es un nodo y sus vecinos adyacentes son aristas; contar islas es contar componentes conectados.

📚 **Recursos:** William Fiset (YouTube) — "Graph Theory" · NeetCode — "Graphs" · (internals en el cap. 8).

---

## 🧠 Patrón 9 — Pila monótona / "siguiente mayor" · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** **pilas** (cap. 3, LIFO) · arreglos. Es un uso "avanzado" de la pila que cae en entrevistas de producto y FAANG.

### 9.A El problema que resuelve

Para cada elemento de un arreglo, quieres saber algo sobre **el siguiente (o anterior) elemento que es mayor (o menor)**: "para cada día, ¿cuántos días faltan hasta uno más caluroso?", "el siguiente número mayor a la derecha", "el rectángulo más grande en un histograma". **El problema:** la fuerza bruta compara cada elemento con todos los de su derecha → O(n²). ¿Se puede en O(n)?

### 9.B La idea central

🏠 **Analogía:** imagina personas de distintas estaturas en fila, y para cada una buscas "la siguiente persona más alta hacia la derecha". Si vas guardando en una **pila** solo a las personas que **aún no han encontrado** a alguien más alto, cuando llega una nueva más alta, ella es la respuesta para **todas** las de la pila más bajas que ella (las vas sacando y resolviendo). Cada persona entra y sale de la pila una vez → **O(n)**.

> 🔑 **INSIGHT:** una **pila monótona** mantiene sus elementos en orden (creciente o decreciente). Cuando llega un elemento que "rompe" ese orden, **desapilas** resolviendo a los que quedaron "atrapados". Así, en una sola pasada, resuelves "el siguiente mayor/menor" para todos.

### 9.C Cómo construir el algoritmo (receta)

1. Recorre el arreglo. Usa una pila que guarda **índices** (no valores, para poder calcular distancias).
2. Mientras la pila no esté vacía y el elemento actual **rompa la monotonía** (ej. es mayor que el del tope), **desapila** y resuelve ese elemento (su "siguiente mayor" es el actual).
3. Apila el índice actual.

### 9.D Ejemplo: temperaturas (días hasta uno más caluroso)
```java
public static int[] diasMasCaluroso(int[] t) {
    int[] res = new int[t.length];
    Deque<Integer> pila = new ArrayDeque<>();        // guarda ÍNDICES
    for (int i = 0; i < t.length; i++) {
        while (!pila.isEmpty() && t[i] > t[pila.peek()]) {
            int prev = pila.pop();                   // este día encontró uno más caluroso
            res[prev] = i - prev;                    // distancia en días
        }
        pila.push(i);
    }
    return res;   // los que quedan en la pila tienen 0 (no hay día más caluroso después)
}
// [73,74,75,71,69,72,76,73] -> [1,1,4,2,1,1,0,0]
```
✍️ **Traza parcial:** con `i=1` (74 > 73 del tope) → resuelve el día 0: `res[0]=1-0=1`. Cada índice entra y sale una vez → O(n).

### 9.E Cómo reconocerlo y práctica

🗝️ **Señal:** "siguiente/anterior elemento **mayor/menor**", "para cada elemento, ¿cuándo aparece uno más grande?", histogramas, "span" de precios de acciones.

**P1.** ¿Por qué la pila guarda índices y no valores?
> Para poder calcular distancias/posiciones (ej. cuántos días de diferencia), no solo el valor.

**P2.** ¿Por qué es O(n) si hay un while dentro del for?
> Cada índice se apila y desapila a lo más una vez en total; el trabajo total es lineal.

**P3.** ¿Qué señal en un enunciado grita "pila monótona"?
> "El siguiente (o anterior) elemento mayor/menor" para cada posición.

📚 **Recursos:** NeetCode — "Stack" (Daily Temperatures, Next Greater Element, Largest Rectangle in Histogram).

---

## 🧠 Patrón 10 — Intervalos · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** **ordenamiento** (`Arrays.sort` con comparador) · arreglos. Aparece muchísimo en problemas de calendarios/reservas, muy relevantes para software de negocio.

### 10.A El problema que resuelve

Tienes rangos con inicio y fin —reuniones, reservas, tareas— y quieres: fusionarlos si se solapan, contar cuántos chocan, encontrar huecos, o cuántas salas necesitas. **El problema:** las relaciones entre intervalos son confusas hasta que los pones en orden.

### 10.B La idea central (casi siempre el mismo primer paso)

🏠 **Analogía: barras en una línea de tiempo.** Si las dibujas y las **ordenas de izquierda a derecha por su hora de inicio**, las relaciones se vuelven obvias: solo tienes que comparar cada barra con la "actual" que llevas, viendo si empieza antes de que la actual termine (se solapan) o después (separadas).

> 🔑 **INSIGHT:** **ordenar por inicio** es el 80% de la solución en problemas de intervalos. Una vez ordenados, un solo recorrido lineal resuelve casi todo.

### 10.C Cómo construir el algoritmo (receta)

1. **Ordena los intervalos por su inicio.**
2. Recorre manteniendo el "intervalo actual" (al principio, el primero).
3. Por cada siguiente intervalo:
   - Si **empieza antes o cuando termina** el actual → **se solapan**: extiende el fin del actual al máximo de ambos.
   - Si **empieza después** → no solapan: guarda el actual y el siguiente pasa a ser el nuevo "actual".

### 10.D Ejemplo: fusionar intervalos
```java
public static int[][] fusionar(int[][] iv) {
    Arrays.sort(iv, (a, b) -> a[0] - b[0]);             // 1) ordena por inicio
    List<int[]> res = new ArrayList<>();
    for (int[] cur : iv) {
        if (res.isEmpty() || res.get(res.size()-1)[1] < cur[0])
            res.add(cur);                               // no solapa: nuevo
        else
            res.get(res.size()-1)[1] =
                Math.max(res.get(res.size()-1)[1], cur[1]);  // solapa: extiende el fin
    }
    return res.toArray(new int[0][]);
}
// [[1,3],[2,6],[8,10],[15,18]] -> [[1,6],[8,10],[15,18]]
```
✍️ **Traza:** ordenado ya. [1,3] entra. [2,6]: 2 ≤ 3 → solapa → actual pasa a [1,6]. [8,10]: 8 > 6 → nuevo. [15,18]: nuevo.

### 10.E Variantes, reconocimiento y práctica

**Variantes:** insertar un intervalo en una lista ordenada; **salas de reuniones mínimas** (cuántos intervalos se solapan a la vez — se resuelve con un heap de fines, conectando con el Patrón 11); intersección de dos listas de intervalos.

🗝️ **Señal:** el problema da rangos `[inicio, fin]` y pide fusionar, contar solapes, huecos, o recursos simultáneos.

**P1.** ¿Cuál es casi siempre el primer paso con intervalos y por qué?
> Ordenar por inicio: vuelve obvias las relaciones de solape y permite resolver en un solo recorrido.

**P2.** ¿Cuándo se solapan dos intervalos `[a,b]` y `[c,d]` (ya ordenados por inicio)?
> Cuando `c <= b` (el segundo empieza antes o cuando termina el primero).

**P3.** "¿Cuántas salas de reunión mínimas necesito?" — idea general.
> Ordenar y usar un min-heap de horas de fin: si la siguiente reunión empieza después del fin más temprano, reutilizas sala; si no, abres una nueva. El tamaño máximo del heap es la respuesta.

📚 **Recursos:** NeetCode — "Intervals" (Merge Intervals, Insert Interval, Meeting Rooms).

---

## 🧠 Patrón 11 — Top-K con heap · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** la estructura **heap / PriorityQueue** (cap. 7 — internals y el truco contraintuitivo) · hashing (para Top-K por frecuencia).
>
> 📎 Los internals del heap y el porqué del "min-heap para los K mayores" están a fondo en el **capítulo 7 — Heaps**. Aquí, el ángulo de entrevista.

### 11.A La señal y la idea

🗝️ **Señal inconfundible:** la letra **"K"** + "más grandes / más pequeños / más frecuentes", o "el **K-ésimo** mayor/menor", o "la **mediana** de un flujo". En cuanto leas "K mayores/frecuentes", piensa heap.

🔑 **La idea (recordatorio del cap. 7):** mantén un heap de **tamaño K**. Para los K **mayores**, usa un **min-heap** (para descartar fácil al más pequeño); para los K **menores**, un **max-heap**. Costo **O(n log k)**, mejor que ordenar todo (O(n log n)) cuando k es pequeño.

### 11.B Cómo construir la solución (receta)

1. Elige el tipo de heap (min para "mayores", max para "menores").
2. Recorre los elementos; agrégalos al heap.
3. Si el heap supera tamaño K, saca la raíz (`poll`).
4. Al final, el heap tiene los K buscados; su raíz es el "K-ésimo".

### 11.C Ejemplo: K elementos más frecuentes (heap + hashing)
```java
public static List<Integer> kMasFrecuentes(int[] nums, int k) {
    Map<Integer,Integer> freq = new HashMap<>();
    for (int n : nums) freq.put(n, freq.getOrDefault(n, 0) + 1);   // 1) contar (hashing)
    // 2) min-heap por frecuencia, de tamaño k
    PriorityQueue<Integer> heap = new PriorityQueue<>((a, b) -> freq.get(a) - freq.get(b));
    for (int n : freq.keySet()) {
        heap.add(n);
        if (heap.size() > k) heap.poll();          // descarta el menos frecuente
    }
    return new ArrayList<>(heap);                  // los k más frecuentes
}
// [1,1,1,2,2,3], k=2 -> [2,1]
```
🗝️ **Clave:** este problema **combina dos patrones** — hashing (contar frecuencias) + heap (quedarte con los K mayores por frecuencia). Reconocer combinaciones es señal de madurez.

### 11.D Variantes y práctica

**Variantes:** K-ésimo mayor (un solo número); mezclar K listas ordenadas (heap de cabezas); mediana de un flujo (dos heaps, uno min y uno max, balanceados).

**P1.** Para "los 3 números más frecuentes", ¿qué dos estructuras combinas?
> Un HashMap para contar frecuencias y un min-heap de tamaño 3 por frecuencia.

**P2.** ¿Por qué min-heap para los K mayores?
> Para descartar en la cima al más pequeño de los candidatos, conservando los K mayores; costo O(n log k).

**P3.** ¿Cuándo es mejor el heap que ordenar todo el arreglo?
> Cuando k es pequeño frente a n: O(n log k) < O(n log n).

📚 **Recursos:** NeetCode — "Heap / Priority Queue" (Kth Largest, Top K Frequent, Find Median from Data Stream) · (internals en el cap. 7).

---

## 🧠 Patrón 12 — Prefix sum (sumas acumuladas) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje:** arreglos · aritmética básica · (para una variante potente) hashing.

### 12.A El problema que resuelve

Te hacen **muchas** preguntas del tipo "¿cuánto suman los elementos entre las posiciones i y j?" sobre el mismo arreglo. Calcular cada suma recorriendo el rango es O(n) por consulta → O(n·consultas), lento si hay muchas. **El problema:** ¿puedo responder cada consulta de rango en O(1)?

### 12.B La idea central

🏠 **Analogía: el cuentakilómetros.** Un odómetro anota cuánto llevas recorrido **en total** en cada punto del viaje. Para saber la distancia entre el km 30 y el km 70, no vuelves a manejar: restas `70 - 30 = 40`. Igual con sumas: si precalculas el **acumulado hasta cada posición**, cualquier suma de rango es una **resta** de dos acumulados → O(1).

> 🔑 **INSIGHT:** inviertes un trabajo O(n) **una sola vez** (construir los acumulados) para que **cada** consulta posterior sea O(1). Es "precalcular para amortizar".

### 12.C Cómo construir el algoritmo (receta)

1. Crea `prefix[]` de tamaño n+1, con `prefix[0] = 0`.
2. Llénalo en una pasada: `prefix[i+1] = prefix[i] + arr[i]` (acumulado hasta i inclusive).
3. La suma del rango `[i, j]` (inclusive) = `prefix[j+1] - prefix[i]`.

### 12.D Ejemplo
```java
int[] arr = {2, 4, 6, 8};
int[] prefix = new int[arr.length + 1];
for (int i = 0; i < arr.length; i++)
    prefix[i+1] = prefix[i] + arr[i];
// prefix = [0, 2, 6, 12, 20]
// suma de arr[1..2] (el 4 y el 6) = prefix[3] - prefix[1] = 12 - 2 = 10
```
✍️ **Por qué funciona:** `prefix[3]` es 2+4+6 y `prefix[1]` es 2; al restar, el "2" inicial se cancela y queda 4+6.

### 12.E La variante potente: prefix sum + hashing

🔑 "**¿Cuántos subarreglos suman exactamente K?**" se resuelve combinando prefix sum con un **HashMap** que cuenta cuántas veces ha aparecido cada suma acumulada. Si en la posición actual la suma acumulada es `S`, y ya viste la suma acumulada `S - K` antes, entonces existe un subarreglo que suma K. Es O(n) y un clásico difícil que mezcla dos patrones.

### 12.F Reconocimiento y práctica

🗝️ **Señal:** "**suma de un rango/subarreglo**", "muchas consultas de suma", "subarreglo que suma K", "promedio de un segmento".

**P1.** Con `prefix = [0,2,6,12,20]`, ¿cuánto suma el rango de índices [0..3]?
> `prefix[4] - prefix[0] = 20 - 0 = 20`.

**P2.** ¿Por qué prefix sum hace cada consulta de rango O(1)?
> Porque precalculas los acumulados una vez; cualquier suma de rango es la resta de dos de ellos.

**P3.** ¿Qué dos patrones combinas para "cuántos subarreglos suman K"?
> Prefix sum + un HashMap de frecuencias de sumas acumuladas.

📚 **Recursos:** NeetCode / LeetCode tag "Prefix Sum" (Range Sum Query, Subarray Sum Equals K).

---
## 🧠 Patrón 13 — Programación dinámica (DP) · VERSIÓN SUPREMA

> 🔗 **Dependencias de aprendizaje (las más altas del manual):** **recursión sólida** (Patrón 5 — la DP *nace* de la recursión; si no la dominas, NO empieces aquí) · **arreglos** (cap. 1, para la tabla) · haber visto **por qué Fibonacci recursivo es O(2ⁿ)** (Patrón 5 §5.H — ese es el problema exacto que la DP resuelve). Es la cima de la escalera. Ve despacio.

### 13.A El problema que la DP resuelve

Recuerda Fibonacci recursivo (§5.H): era O(2ⁿ) porque **recalculaba los mismos subproblemas una y otra vez** (fib(3) se computaba varias veces). Ese desperdicio aparece en muchísimos problemas de optimización ("el camino de costo mínimo", "el máximo de...", "¿de cuántas formas...?"). **El problema es: ¿cómo evito recalcular subproblemas que ya resolví?** La respuesta —simple pero poderosa— es la programación dinámica: **resuelve cada subproblema UNA vez y guarda su resultado** para reutilizarlo.

> 🔑 **Definición honesta:** "programación dinámica" es un nombre intimidante para una idea sencilla: **recursión + memoria.** No te dejes asustar por el término.

### 13.B Los dos ingredientes que un problema necesita para ser DP

No todo problema es DP. Necesita **dos** propiedades (saber detectarlas es media batalla):
1. **Subproblemas superpuestos (overlapping subproblems):** el problema se resuelve resolviendo versiones más pequeñas, y **esas versiones se repiten** (como fib(3) calculándose varias veces). *Si no se repiten, es "divide y vencerás" normal, no DP.*
2. **Subestructura óptima (optimal substructure):** la solución óptima del problema se **construye a partir** de las soluciones óptimas de sus subproblemas. (El camino más corto a la meta se arma con el camino más corto al penúltimo paso.)

### 13.C La idea central, construida desde cero

🏠 **Analogía: subir una escalera contando formas.** Quieres saber de cuántas formas puedes subir una escalera de n escalones, dando pasos de 1 o 2 escalones. Para llegar al escalón 10, pudiste venir del 9 (un paso) o del 8 (dos pasos). Así que *formas(10) = formas(9) + formas(8)*. Si calculas esto recursivamente sin memoria, recalcularás *formas(8)* miles de veces. La DP dice: **anota en un papelito cada formas(i) la primera vez que lo calcules, y la próxima vez solo léelo.** Recalcular se vuelve consultar: de O(2ⁿ) a O(n).

> 🔑 **EL INSIGHT CENTRAL:** la DP convierte un **árbol** de llamadas recursivas que se ramifica y repite (exponencial) en una **tabla** que se llena una sola vez (lineal o polinomial). Cambias **tiempo por memoria**: gastas una tabla para no repetir trabajo.

### 13.D La pieza más importante: la relación de recurrencia

🗝️ **Todo problema de DP gira en torno a UNA fórmula: la relación de recurrencia**, que dice cómo la respuesta de un estado se arma a partir de estados más pequeños. Encontrarla **es** resolver el problema; lo demás (memoizar o tabular) es mecánico.

- Escaleras: `formas(i) = formas(i-1) + formas(i-2)`.
- Fibonacci: `fib(i) = fib(i-1) + fib(i-2)`.
- Mínimo de monedas para `c`: `min(c) = 1 + min(c - moneda)` para la mejor moneda.

**Cómo encontrarla:** pregúntate *"para resolver el estado actual, ¿de qué decisiones/estados anteriores depende?"*. Esa dependencia, escrita como fórmula, es la recurrencia.

### 13.E Las dos formas de hacer DP

**Forma 1 — Top-down (memoización): recursión + un "papelito".** Es la más intuitiva: escribes la recursión normal y le añades memoria.
```java
public static int fib(int n, Map<Integer,Integer> memo) {
    if (n <= 1) return n;                       // casos base
    if (memo.containsKey(n)) return memo.get(n); // ¿ya lo calculé? léelo (clave de la DP)
    int resultado = fib(n-1, memo) + fib(n-2, memo);
    memo.put(n, resultado);                      // guárdalo antes de retornar
    return resultado;
}
```
🔧 La línea `if (memo.containsKey(n)) return memo.get(n);` es **toda** la magia: la primera vez calcula y guarda; las siguientes, lee en O(1). Eso poda el árbol exponencial: cada fib(i) se calcula **una sola vez** → O(n).

**Forma 2 — Bottom-up (tabulación): llena una tabla con bucles, sin recursión.**
```java
public static int formasEscalera(int n) {
    if (n <= 2) return n;
    int[] dp = new int[n + 1];
    dp[1] = 1; dp[2] = 2;                      // casos base
    for (int i = 3; i <= n; i++)
        dp[i] = dp[i-1] + dp[i-2];            // la recurrencia, aplicada en orden
    return dp[n];
}
```
✍️ **Traza de `formasEscalera(5)`** llenando la tabla:
```
dp[1]=1, dp[2]=2
dp[3] = dp[2]+dp[1] = 2+1 = 3
dp[4] = dp[3]+dp[2] = 3+2 = 5
dp[5] = dp[4]+dp[3] = 5+3 = 8
return 8
```
De O(2ⁿ) recursivo a **O(n)** con un simple bucle. Y el espacio puede bajar a O(1) si solo guardas los dos últimos valores.

🗝️ **¿Cuál usar?** Top-down (memoización) es más fácil de derivar desde la recursión natural y solo calcula los estados que necesitas. Bottom-up evita la pila de llamadas (sin riesgo de StackOverflow) y suele ser un pelín más rápido. Para empezar, **memoización** es más intuitiva.

### 13.F Segundo ejemplo completo: cambio de monedas (mínimo)

"¿Cuál es el **mínimo** número de monedas para formar la cantidad `c`, con denominaciones dadas?"
- **Recurrencia:** `min(c) = 1 + el menor de min(c - moneda)` para cada moneda que quepa.
```java
public static int minMonedas(int[] monedas, int c) {
    int[] dp = new int[c + 1];
    Arrays.fill(dp, c + 1);                 // "infinito" (imposible)
    dp[0] = 0;                              // 0 monedas para formar 0
    for (int cant = 1; cant <= c; cant++)
        for (int m : monedas)
            if (m <= cant)
                dp[cant] = Math.min(dp[cant], 1 + dp[cant - m]);   // la recurrencia
    return dp[c] > c ? -1 : dp[c];          // si quedó "infinito", es imposible
}
// monedas {1,2,5}, c=11 -> 3   (5+5+1)
```
✍️ **Idea de la traza:** `dp[11] = 1 + min(dp[10], dp[9], dp[6])` (quitando una moneda de 1, 2 o 5). Cada `dp[cant]` se calcula una vez reusando los anteriores → O(c × número de monedas).

### 13.G Bugs clásicos (y por qué)

**Bug 1 — Casos base mal puestos.** En DP, los casos base son las primeras celdas de la tabla; si están mal, todo lo construido encima está mal. *Solución:* identifica con cuidado dp[0], dp[1].
**Bug 2 — Recurrencia incorrecta.** Si la fórmula que relaciona el estado con los anteriores está mal, el resultado es incorrecto aunque el código "corra". *Solución:* deriva y verifica la recurrencia con un ejemplo chico a mano antes de codificar.
**Bug 3 — Orden de llenado equivocado (bottom-up).** Debes llenar las celdas en un orden tal que, al calcular `dp[i]`, las que necesita (`dp[i-1]`, etc.) **ya estén calculadas**. *Solución:* respeta las dependencias de la recurrencia.
**Bug 4 — Memoizar con una clave incompleta.** Si el estado depende de dos variables, la clave del memo debe incluir **ambas**, o mezclarás subproblemas distintos.

### 13.H La complejidad

- **Tiempo:** (número de estados/subproblemas) × (trabajo por estado). Escaleras: n estados × O(1) = **O(n)**. Monedas: (c estados) × (nº de monedas) = O(c·monedas).
- **Espacio:** O(número de estados) por la tabla (a veces reducible a O(1) si solo dependes de los últimos pocos).
- **El gran salto:** convierte exponencial (O(2ⁿ), O(n!)) en polinomial (O(n), O(n²)). Ese es el superpoder de la DP.

### 13.I Cómo reconocer que un problema pide DP

1. Palabras de **optimización**: "mínimo/máximo número de...", "el costo más bajo", "la longitud máxima de...".
2. Palabras de **conteo**: "¿de **cuántas** formas...?".
3. Decisiones **secuenciales** donde cada una afecta a las siguientes.
4. La pista interna: escribes la versión recursiva y ves que **recalcula los mismos subproblemas**.
5. ⚠️ **Contraste con backtracking:** "dame **todas** las combinaciones" → backtracking (enumera). "Dame el **mínimo/máximo/cuántas**" → DP (optimiza/cuenta **sin** enumerar todo).

### 13.J Receta para construirlo tú mismo

1. **¿Es DP?** Busca subproblemas superpuestos + subestructura óptima (o "optimiza/cuenta" + recursión que repite).
2. **Define el estado:** ¿qué representa `dp[i]`? (ej. "formas de llegar al escalón i", "mín. monedas para la cantidad i").
3. **Encuentra la recurrencia:** ¿cómo se arma `dp[i]` a partir de estados menores?
4. **Define los casos base** (las primeras celdas).
5. **Elige forma:** memoización (recursión + memo) o tabulación (bucle que llena la tabla en orden).
6. **Lee la respuesta** de la celda final.

### 13.K Realismo honesto (importante para tu objetivo)

⚠️ La DP es lo más difícil del manual y **rara vez** aparece en entrevistas SDET/QA fuera de las FAANG. Domina la versión "tipo Fibonacci/escaleras" (1-D, la más común) y entiende la idea de memoización. Pero si tu tiempo es limitado para volver al mercado pronto, **invierte primero** en hashing, dos punteros, ventana deslizante, árboles y grafos — rinden muchísimo más para roles SDET típicos y nearshore. La DP es un "extra de lujo", no la base.

### 13.L Práctica, con respuestas

**P1.** ¿Qué es la DP en una frase?
> Recursión con memoria: resolver cada subproblema una vez y guardar el resultado para no recalcularlo.

**P2.** ¿Qué dos propiedades necesita un problema para ser DP?
> Subproblemas superpuestos (se repiten) y subestructura óptima (el óptimo se arma con óptimos de subproblemas).

**P3.** ¿Qué línea convierte la recursión de Fibonacci en DP top-down, y por qué basta?
> `if (memo.containsKey(n)) return memo.get(n);`. Hace que cada fib(i) se calcule una sola vez (las demás se leen), podando el árbol exponencial a O(n).

**P4.** Escribe la recurrencia para "subir una escalera con pasos de 1 o 2".
> `formas(i) = formas(i-1) + formas(i-2)`, con formas(1)=1, formas(2)=2.

**P5.** "Todas las combinaciones de monedas que suman 11" vs "el mínimo de monedas que suman 11": ¿qué técnica cada una?
> "Todas" → backtracking (enumera). "Mínimo" → DP (optimiza sin enumerar).

**P6.** ¿Por qué la DP convierte O(2ⁿ) en O(n) en Fibonacci?
> Porque elimina el recálculo: hay solo n subproblemas distintos (fib(0)..fib(n)); con memoria, cada uno se calcula una vez.

📚 **Recursos:** "Grokking Dynamic Programming" (el concepto, muy didáctico) · **NeetCode — "1-D Dynamic Programming"** (empieza por aquí antes de DP en 2-D) · Abdul Bari (YouTube) para la intuición.

---
## 🔢 Algoritmos clásicos con nombre — Ordenamientos

> 🔗 **Dependencias de aprendizaje:** **recursión** (Patrón 5, para merge sort y quicksort) · **arreglos** (cap. 1) · **Big-O** (Parte 1, para entender por qué O(n log n) vence a O(n²)). Ordenar es una de las operaciones más fundamentales en computación; entender *cómo* lo hacen estos algoritmos es pregunta frecuente, aunque en el día a día uses `Arrays.sort`.

### Por qué importan (aunque ya exista `Arrays.sort`)

En la práctica **nunca** implementarás un ordenamiento desde cero: usas `Arrays.sort()` o `Collections.sort()`. Pero en una entrevista te pueden pedir **explicar cómo funciona uno** (clásico de fundamentos de CS), y entender la idea de "divide y vencerás" detrás de merge sort y quicksort te ayuda con muchos otros problemas. Dato útil: `Arrays.sort` de Java usa **Dual-Pivot QuickSort** para primitivos y **TimSort** (una mezcla de merge sort e insertion sort) para objetos.

### La gran división: O(n²) vs O(n log n)

Hay ordenamientos "lentos" O(n²) (burbuja, selección, inserción) y "rápidos" O(n log n) (merge, quick, heap). La diferencia es enorme: para n = 1.000.000, O(n²) hace ~10¹² operaciones (días) y O(n log n) ~2×10⁷ (instantáneo). **Los O(n log n) lo logran con "divide y vencerás":** parten el problema a la mitad repetidamente (de ahí el `log n`) y hacen trabajo lineal en cada nivel.

---

### 🅐 Merge Sort (ordenamiento por mezcla) — el confiable O(n log n)

> 🔗 Depende de **recursión** y de saber **mezclar dos listas ordenadas** (que es dos punteros, Patrón 2).

🏠 **La idea (divide y vencerás):** ¿cómo ordenas una baraja grande? **Divídela** en dos mitades, pide a dos amigos que ordenen cada mitad (ellos hacen lo mismo recursivamente), y cuando te devuelvan dos mitades ordenadas, **mézclalas** en una sola baraja ordenada. La magia está en que **mezclar dos mitades YA ordenadas es fácil y lineal**: comparas las cartas de arriba de cada montón y tomas la menor.

**Los dos pasos:**
1. **Dividir (divide):** parte el arreglo por la mitad, recursivamente, hasta que cada trozo tenga 1 elemento (un arreglo de 1 elemento ya está "ordenado" — ese es el caso base).
2. **Mezclar (conquer):** combina pares de trozos ordenados en trozos más grandes ordenados, subiendo hasta reconstruir todo.

✍️ **Traza de la idea** con `[5, 2, 8, 1]`:
```
DIVIDIR:  [5,2,8,1] → [5,2] y [8,1] → [5][2] y [8][1]
MEZCLAR:  [5]+[2]=[2,5];  [8]+[1]=[1,8];  [2,5]+[1,8]=[1,2,5,8]
```
La mezcla `[2,5]+[1,8]`: comparo 2 vs 1 → tomo 1; 2 vs 8 → tomo 2; 5 vs 8 → tomo 5; queda 8. Resultado `[1,2,5,8]`.

```java
public static void mergeSort(int[] arr, int izq, int der) {
    if (izq >= der) return;                        // CASO BASE: 0 o 1 elemento
    int medio = izq + (der - izq) / 2;
    mergeSort(arr, izq, medio);                    // ordena mitad izquierda
    mergeSort(arr, medio + 1, der);                // ordena mitad derecha
    mezclar(arr, izq, medio, der);                 // combina las dos mitades ordenadas
}
// mezclar() recorre ambas mitades con dos punteros, tomando siempre el menor.
```

**Complejidad:** **O(n log n) SIEMPRE** (mejor, peor y caso promedio — muy predecible). Espacio **O(n)** (necesita un arreglo auxiliar para mezclar).

➕ **Ventajas:** O(n log n) garantizado (sin "peor caso" malo); es **estable** (mantiene el orden relativo de elementos iguales — importante al ordenar por varias claves); ideal para datos enormes o externos (en disco).
➖ **Desventajas:** usa **O(n) de memoria extra** (no ordena "in place").

---

### 🅑 Quick Sort (ordenamiento rápido) — el veloz en la práctica

> 🔗 Depende de **recursión** y de la idea de **particionar** alrededor de un pivote (dos punteros).

🏠 **La idea (divide y vencerás, pero al revés que merge):** elige un elemento como **pivote**. **Particiona** el arreglo de modo que todo lo **menor** que el pivote quede a su izquierda y todo lo **mayor** a su derecha (el pivote queda en su posición final correcta). Luego aplica lo mismo, recursivamente, a la parte izquierda y a la derecha. A diferencia de merge sort, **el trabajo difícil (particionar) ocurre ANTES de las llamadas recursivas, no después** — por eso no necesita un paso de mezcla.

**Los pasos:**
1. **Elige un pivote** (un elemento del arreglo).
2. **Particiona:** reordena para que menores ← pivote → mayores. El pivote queda fijo en su lugar definitivo.
3. **Recursión** sobre la sub-parte izquierda y la derecha.

✍️ **Traza de la idea** con `[5,2,8,1,9,3]`, pivote = 5:
```
particiona → menores de 5 a la izq, mayores a la der:  [2,1,3] 5 [8,9]
                                                         ↑ pivote en su lugar final
recursión en [2,1,3] y en [8,9] → ... → [1,2,3,5,8,9]
```

```java
public static void quickSort(int[] arr, int izq, int der) {
    if (izq >= der) return;                       // CASO BASE
    int p = particionar(arr, izq, der);           // coloca el pivote en su lugar final
    quickSort(arr, izq, p - 1);                   // ordena los menores
    quickSort(arr, p + 1, der);                   // ordena los mayores
}
```

**Complejidad:** **O(n log n) en promedio** (muy rápido en la práctica, con buena localidad de caché). ⚠️ **Peor caso O(n²)** si el pivote elegido es siempre el peor (ej. el menor o mayor de cada parte, que ocurre con datos ya ordenados y pivote fijo). Se mitiga eligiendo el pivote **al azar** o por "mediana de tres". Espacio **O(log n)** (solo la pila de recursión — ordena **in place**).

➕ **Ventajas:** suele ser el **más rápido en la práctica**; ordena **in place** (O(log n) de memoria, mucho menos que merge sort).
➖ **Desventajas:** peor caso O(n²) (mitigable); **no es estable**; su rendimiento depende de elegir bien el pivote.

---

### 🅒 Los O(n²) (debes reconocerlos, rara vez usarlos)

- **Burbuja (bubble sort):** compara pares adyacentes y los intercambia si están desordenados, repetidamente. Los mayores "burbujean" al final. Solo didáctico.
- **Selección (selection sort):** busca el mínimo y lo pone al frente; repite con el resto. Pocos intercambios, pero siempre O(n²) comparaciones.
- **Inserción (insertion sort):** toma cada elemento y lo "inserta" en su lugar entre los ya ordenados (como ordenar cartas en la mano). **Es O(n²) en general, pero O(n) si el arreglo ya está casi ordenado** — por eso se usa dentro de TimSort para tramos pequeños.

### 🅓 Tabla comparativa maestra de ordenamientos

| Algoritmo | Mejor | Promedio | Peor | Espacio | ¿Estable? | Cuándo |
|---|---|---|---|---|---|---|
| Burbuja | O(n) | O(n²) | O(n²) | O(1) | Sí | Solo enseñanza |
| Selección | O(n²) | O(n²) | O(n²) | O(1) | No | Pocos swaps; casi nunca |
| Inserción | O(n) | O(n²) | O(n²) | O(1) | Sí | Datos casi ordenados o pequeños |
| **Merge** | O(n log n) | O(n log n) | **O(n log n)** | O(n) | **Sí** | Garantía O(n log n), estabilidad, datos enormes |
| **Quick** | O(n log n) | O(n log n) | O(n²) | O(log n) | No | El más rápido en práctica, in place |
| **Heap** | O(n log n) | O(n log n) | O(n log n) | O(1) | No | O(n log n) garantizado e in place |

🔑 **Las respuestas que importan en entrevista:**
- *¿Cuál es el más rápido en la práctica?* → Quicksort (promedio O(n log n), in place, buena caché).
- *¿Cuál garantiza O(n log n) sin peor caso malo?* → Merge sort y heap sort.
- *¿Qué significa "estable" y cuál lo es?* → Mantiene el orden relativo de elementos con clave igual; merge e inserción son estables, quick y heap no. Importa al ordenar por múltiples criterios.
- *¿Cuál usa Java?* → Dual-Pivot Quicksort (primitivos) y TimSort (objetos).

### Práctica, con respuestas

**P1.** Explica merge sort en una frase.
> Divide el arreglo a la mitad recursivamente hasta trozos de 1, luego mezcla pares de mitades ordenadas en O(n) por nivel → O(n log n).

**P2.** ¿Por qué quicksort puede ser O(n²) y cómo se evita?
> Si el pivote es siempre el peor (p. ej. con datos ya ordenados y pivote fijo), las particiones quedan desbalanceadas. Se evita eligiendo el pivote al azar o por mediana de tres.

**P3.** ¿Cuándo prefieres merge sort sobre quicksort?
> Cuando necesitas O(n log n) **garantizado**, estabilidad, o estás ordenando datos enormes/externos. Quicksort gana cuando quieres velocidad in place y la memoria importa.

**P4.** ¿Qué quiere decir que un ordenamiento es "estable" y por qué importa?
> Que dos elementos con la misma clave conservan su orden original relativo. Importa al ordenar por varias claves en cascada (p. ej. por apellido y luego por nombre).

**P5.** ¿Por qué los O(n log n) vencen tanto a los O(n²)?
> Porque parten el problema a la mitad (log n niveles) y hacen trabajo lineal por nivel; para n grande, n·log n es muchísimo menor que n².

📚 **Recursos:** VisuAlgo — Sorting (anima los 6 ordenamientos lado a lado) · Abdul Bari (YouTube) — Sorting algorithms · "Grokking Algorithms" — quicksort y merge sort.

---
## 🕸️ Algoritmos de grafos con nombre

> 🔗 **Dependencias de aprendizaje:** la estructura **grafo** (cap. 8: representaciones, BFS/DFS, visitados) · **heaps/PriorityQueue** (cap. 7, para Dijkstra) · **colas** (cap. 4, para orden topológico) · **recursión**. Estos son los algoritmos "con nombre" que extienden los recorridos básicos. Los tres primeros (Dijkstra, topológico, Union-Find) son los que de verdad caen en entrevistas; el resto va como referencia para que la biblia los tenga todos.

---

### 🅐 Dijkstra — camino más corto con pesos

> 🔗 Depende de **grafos ponderados** (cap. 8) y **min-heap** (cap. 7). Es "BFS para grafos con pesos".

🅐.1 **El problema:** BFS encuentra el camino más corto contando **aristas** (todas valen 1). Pero ¿y si las aristas tienen **pesos** distintos (distancia entre ciudades, tiempo, costo)? El camino con menos aristas puede no ser el más barato. **El problema es: el camino de menor COSTO TOTAL entre dos nodos en un grafo con pesos.** Es lo que hace tu GPS.

🅐.2 **La idea:** 🏠 imagina que el costo es "tiempo de viaje" y quieres llegar lo antes posible. Dijkstra es **goloso (greedy)**: siempre expande **el nodo no visitado al que se llega con el MENOR costo acumulado hasta ahora**. Como siempre procesa primero lo más barato, la primera vez que "fija" un nodo, ya tiene su costo mínimo definitivo. Es BFS, pero en lugar de una cola FIFO usa una **cola de prioridad (min-heap)** que entrega siempre el siguiente nodo más barato.

> 🔑 **INSIGHT:** Dijkstra = BFS + min-heap. La cola normal de BFS daba "el más cercano en aristas"; el min-heap da "el más cercano en **costo**". Ese cambio de estructura es todo.

🅐.3 **Cómo se construye (receta):**
1. `dist[]`: el costo mínimo conocido a cada nodo, inicializado a ∞ salvo el origen (0).
2. Un **min-heap** de `(costo, nodo)`, empezando con `(0, origen)`.
3. Saca del heap el nodo de menor costo. Para cada vecino, si llegar a él **por este nodo** mejora su `dist`, actualízalo y mételo al heap.
4. Repite hasta vaciar el heap. `dist[]` queda con los costos mínimos.

```java
public static int[] dijkstra(Map<Integer,List<int[]>> g, int origen, int n) {
    int[] dist = new int[n];
    Arrays.fill(dist, Integer.MAX_VALUE);
    dist[origen] = 0;
    // min-heap por costo acumulado: {costo, nodo}
    PriorityQueue<int[]> heap = new PriorityQueue<>((a, b) -> a[0] - b[0]);
    heap.add(new int[]{0, origen});
    while (!heap.isEmpty()) {
        int[] actual = heap.poll();
        int costo = actual[0], nodo = actual[1];
        if (costo > dist[nodo]) continue;                  // entrada obsoleta, ignórala
        for (int[] arista : g.getOrDefault(nodo, List.of())) {
            int vecino = arista[0], peso = arista[1];
            if (dist[nodo] + peso < dist[vecino]) {        // ¿mejora el camino al vecino?
                dist[vecino] = dist[nodo] + peso;          // "relajación" de la arista
                heap.add(new int[]{dist[vecino], vecino});
            }
        }
    }
    return dist;
}
```
✍️ **Traza (idea):** desde el origen con `dist=0`, sacas el más barato, "relajas" sus vecinos (mejoras sus distancias), los metes al heap; el heap siempre te devuelve el siguiente nodo de menor costo total. La operación clave `dist[nodo] + peso < dist[vecino]` se llama **relajación**.

🅐.4 **Complejidad:** **O((V + E) log V)** con min-heap (cada arista puede provocar una inserción en el heap, y cada operación del heap es log V).

⚠️ **Limitación crítica (pregunta de entrevista):** Dijkstra **NO funciona con pesos NEGATIVOS.** Su lógica golosa asume que una vez fijado el costo mínimo de un nodo, no puede mejorar — pero un peso negativo podría abrir un atajo posterior, rompiendo esa suposición. Para pesos negativos → **Bellman-Ford** (abajo).

🅐.5 **Cuándo usarlo:** "camino más corto/barato con pesos positivos" (GPS, redes, costos). **Señal:** "distancias", "costos", "tiempo mínimo" + grafo con números en las aristas.

---

### 🅑 Orden topológico (topological sort) — ordenar con dependencias

> 🔗 Depende de **grafos dirigidos** (cap. 8) y **colas** (cap. 4) o recursión/DFS.

🅑.1 **El problema:** tienes tareas con **dependencias** ("para hacer A primero necesitas B y C") y quieres un orden válido para ejecutarlas todas. Ejemplos: orden de cursos con prerrequisitos, orden de compilación de módulos, resolución de dependencias de paquetes (npm, Maven). **El problema es: linealizar un grafo dirigido respetando todas las flechas "antes que".**

🅑.2 **Requisito:** solo existe orden topológico si el grafo es un **DAG** (grafo dirigido **acíclico**). Si hay un ciclo (A necesita B y B necesita A), **no hay orden posible** — y detectar esa imposibilidad es parte del problema.

🅑.3 **La idea (algoritmo de Kahn, con cola y grados de entrada):**
🏠 Empieza por las tareas que **no dependen de nada** (grado de entrada 0): esas pueden ir primero. Al "completar" una tarea, reduces el contador de dependencias de las que dependían de ella; cuando alguna llega a 0, ya está lista para entrar.
```java
public static List<Integer> ordenTopologico(int n, int[][] aristas) {
    List<List<Integer>> g = new ArrayList<>();
    int[] gradoEntrada = new int[n];
    for (int i = 0; i < n; i++) g.add(new ArrayList<>());
    for (int[] a : aristas) { g.get(a[0]).add(a[1]); gradoEntrada[a[1]]++; }  // a[0] -> a[1]
    Queue<Integer> cola = new LinkedList<>();
    for (int i = 0; i < n; i++) if (gradoEntrada[i] == 0) cola.add(i);  // sin dependencias
    List<Integer> orden = new ArrayList<>();
    while (!cola.isEmpty()) {
        int nodo = cola.poll();
        orden.add(nodo);
        for (int vecino : g.get(nodo))
            if (--gradoEntrada[vecino] == 0) cola.add(vecino);  // ya no tiene pendientes
    }
    return orden.size() == n ? orden : new ArrayList<>();  // si no entraron todos → había ciclo
}
```
🗝️ **Clave doble:** (1) procesar por grado de entrada 0 da un orden válido; (2) si al final **no salieron todos los nodos**, es porque había un **ciclo** (esos nodos nunca llegaron a grado 0). Así, el mismo algoritmo **ordena Y detecta ciclos**.

🅑.4 **Complejidad:** **O(V + E)**. **Señal:** "orden de tareas/cursos/compilación con prerrequisitos", "¿se pueden terminar todos los cursos?".

---

### 🅒 Union-Find (Disjoint Set Union, DSU) — conjuntos y conectividad

> 🔗 Depende de **arreglos** (cap. 1) y la idea de "representante de un grupo". No necesita BFS/DFS; es una estructura aparte muy elegante.

🅒.1 **El problema:** quieres responder rapidísimo *"¿estos dos elementos están en el mismo grupo/conectados?"* y *"une estos dos grupos"*, con muchas consultas. Ejemplos: ¿están dos personas en la misma red de amigos?, detectar si agregar una arista crea un ciclo, contar componentes conectados, redes. **El problema: gestionar grupos que se van fusionando, con consultas de pertenencia ultrarrápidas.**

🅒.2 **La idea:** 🏠 cada grupo es como un árbol donde todos apuntan (directa o indirectamente) a un mismo **"líder" (representante/raíz)**. Dos elementos están en el mismo grupo **si tienen el mismo líder**. Dos operaciones:
- **`find(x)`:** sube de padre en padre hasta el líder del grupo de x.
- **`union(a, b)`:** encuentra los líderes de a y b y hace que uno apunte al otro (fusiona los dos grupos).

```java
class UnionFind {
    int[] padre, rango;
    UnionFind(int n) {
        padre = new int[n]; rango = new int[n];
        for (int i = 0; i < n; i++) padre[i] = i;   // cada quien es su propio líder al inicio
    }
    int find(int x) {
        if (padre[x] != x) padre[x] = find(padre[x]);  // COMPRESIÓN DE CAMINO: apunta directo a la raíz
        return padre[x];
    }
    boolean union(int a, int b) {
        int ra = find(a), rb = find(b);
        if (ra == rb) return false;                 // ya estaban juntos (¡detecta ciclo!)
        if (rango[ra] < rango[rb]) { int t = ra; ra = rb; rb = t; }  // UNIÓN POR RANGO
        padre[rb] = ra;
        if (rango[ra] == rango[rb]) rango[ra]++;
        return true;
    }
}
```
🔧 **Las dos optimizaciones que lo hacen casi O(1):**
- **Compresión de caminos (path compression):** en cada `find`, haz que los nodos apunten **directamente** a la raíz, aplanando el árbol para futuras consultas.
- **Unión por rango (union by rank):** al fusionar, cuelga el árbol más bajo del más alto, para que no crezca de más.
Con ambas, `find` y `union` son **O(α(n))** — α es la función inversa de Ackermann, que para cualquier n imaginable es **≤ 4**. En la práctica, **O(1) amortizado**.

🅒.3 **Usos clave:** contar componentes conectados, **detectar ciclo en grafo no dirigido** (si `union` devuelve false, los dos ya estaban conectados → la arista cierra un ciclo), y el algoritmo de **Kruskal** para árbol de expansión mínima. **Señal:** "grupos", "¿conectados?", "componentes", "redes que se fusionan".

---

### 🅓 Los demás (referencia para tenerlos todos)

| Algoritmo | Para qué | Complejidad | Nota clave |
|---|---|---|---|
| **Bellman-Ford** | Camino más corto **con pesos negativos** | O(V·E) | Más lento que Dijkstra, pero soporta negativos y **detecta ciclos negativos** |
| **Floyd-Warshall** | Camino más corto entre **TODOS los pares** | O(V³) | DP sobre grafos; sirve para grafos pequeños y densos |
| **Kruskal (MST)** | Árbol de expansión **mínima** (conectar todo al menor costo) | O(E log E) | Ordena aristas + **Union-Find** para evitar ciclos |
| **Prim (MST)** | Árbol de expansión mínima | O(E log V) | Como Dijkstra pero con min-heap de aristas; crece desde un nodo |
| **A*** | Camino más corto **con heurística** (videojuegos, mapas) | depende | Dijkstra + una estimación que guía hacia la meta (más rápido) |
| **Tarjan / Kosaraju** | Componentes fuertemente conexos | O(V+E) | Para grafos dirigidos: grupos donde todos se alcanzan mutuamente |

🔑 **Cómo elegir el de camino más corto (mapa mental de entrevista):**
- Sin pesos → **BFS**.
- Pesos positivos → **Dijkstra**.
- Pesos negativos → **Bellman-Ford**.
- Todos los pares → **Floyd-Warshall**.
- Con heurística (a una meta concreta) → **A***.

### Práctica, con respuestas

**P1.** ¿Por qué Dijkstra usa un min-heap en vez de la cola del BFS?
> Porque con pesos hay que expandir siempre el nodo de **menor costo acumulado**, no el de menos aristas; el min-heap entrega ese mínimo eficientemente.

**P2.** ¿Por qué Dijkstra falla con pesos negativos?
> Su estrategia golosa asume que el costo mínimo de un nodo, una vez fijado, no mejora; un peso negativo podría crear un atajo posterior, rompiendo esa suposición. Se usa Bellman-Ford.

**P3.** En orden topológico, ¿cómo sabes que el grafo tenía un ciclo?
> Si al terminar no salieron los V nodos (algunos nunca llegaron a grado de entrada 0), hay un ciclo y no existe orden válido.

**P4.** ¿Qué dos optimizaciones hacen a Union-Find casi O(1)?
> Compresión de caminos (aplana el árbol en cada find) y unión por rango (cuelga el árbol bajo del alto).

**P5.** ¿Cómo detecta Union-Find un ciclo en un grafo no dirigido?
> Si al unir los extremos de una arista resulta que ya tenían el mismo líder (union devuelve false), esa arista cierra un ciclo.

**P6.** Quieres conectar N ciudades con cable al **menor costo total**. ¿Qué algoritmo?
> Un árbol de expansión mínima: Kruskal (ordenar aristas + Union-Find) o Prim (min-heap).

📚 **Recursos:** **William Fiset (YouTube) — "Graph Theory"** (Dijkstra, topológico, Union-Find, MST, todo) · NeetCode — "Advanced Graphs" · VisuAlgo — Single-Source Shortest Paths y Union-Find.

---
# PARTE 4 — BANCO DE PREGUNTAS (estilo "tutor privado")

> Este banco está pensado para que estudies **bien**, no solo para autoevaluarte. **Cada pregunta trae cinco cosas**, como si un tutor se sentara contigo:
> - **🎯 Qué evalúan:** el *porqué* de la pregunta — qué quiere ver realmente el entrevistador.
> - **🧠 Qué necesitas saber:** los conceptos previos para responderla (con referencia a la sección del manual donde estudiarlos).
> - **🗝️ Cómo pensarla:** el método/la lógica para llegar a la respuesta, paso a paso.
> - **✅ La respuesta:** la solución, explicada a fondo.
> - **⚠️ Trampas y follow-up:** errores comunes y la pregunta que probablemente venga después.
>
> **Cómo usarlo:** lee la pregunta, **tápate todo lo demás** e intenta responder en voz alta (como en la entrevista real). Luego compara. Si fallas en el "qué necesitas saber", ese es justo el tema que debes repasar.
>
> **Cobertura:** el banco cubre la gran mayoría de lo que se pregunta en entrevistas SDET / Software Developer (de screen telefónico a panel técnico). Está organizado por categorías:
> - **4.1 Fundamentos y Big-O** · **4.2 Estructuras de datos (conceptuales)** — *abajo, a nivel tutor.*
> - **4.3 Problemas de código por patrón** · **4.4 Preguntas verbales / de comunicación** — *continúan después.*

---

## 4.1 Fundamentos y Big-O

> Son las preguntas más comunes en un screen inicial. Casi siempre las hacen para ver si **razonas** sobre eficiencia, no si memorizaste tablas.

### A1. "Explícame Big-O como si yo no supiera programar."

**🎯 Qué evalúan:** si entiendes Big-O de verdad (no solo la fórmula) y si sabes **comunicar** algo técnico de forma simple — habilidad clave en un equipo.
**🧠 Qué necesitas saber:** la idea de "escalar" y la diferencia entre medir *tiempo real* y *número de operaciones en función del tamaño* (§1.1–1.3).
**🗝️ Cómo pensarla:** no definas, **ejemplifica con la vida real**. Usa una analogía de "buscar un nombre en una agenda" y enfócate en *qué pasa cuando los datos crecen*.
**✅ Respuesta:** "Big-O es una forma de predecir cómo se vuelve más lento un programa cuando le das más datos, **sin tener que ejecutarlo**. En vez de medir segundos (que dependen de la computadora), contamos cuántos pasos hace en función del tamaño de la entrada. Si al duplicar los datos el trabajo se duplica, es **lineal** O(n); si se cuadruplica, es **cuadrático** O(n²); si casi no cambia, es **logarítmico** O(log n). Es como comparar dos rutas no por cuántos minutos tardas hoy, sino por cuánto empeoran con el tráfico."
**⚠️ Trampas / follow-up:** no te enredes en matemáticas. *Follow-up probable:* "¿y por qué ignoramos las constantes?" → porque a gran escala el término que domina decide todo (A2).

### A2. "Simplifica O(4n² + 2n + 7). ¿Por qué se puede?"

**🎯 Qué evalúan:** si dominas las reglas de simplificación y entiendes *por qué* existen (no solo aplicarlas).
**🧠 Qué necesitas saber:** las tres reglas — tirar constantes multiplicativas, tirar términos menores, quedarte con el dominante (§1.5).
**🗝️ Cómo pensarla:** pregúntate *"cuando n es enorme, ¿qué término manda?"*.
**✅ Respuesta:** "**O(n²)**. Cuando n crece, el término n² aplasta a los demás: con n=1.000, n² es 1.000.000 mientras que 2n es 2.000 y el 7 es insignificante. Las constantes (el 4) tampoco importan porque Big-O describe la *forma* del crecimiento, no el valor exacto: 4n² y n² se cuadruplican igual al doblar n."
**⚠️ Trampas:** no dejar el "4" ni el "+2n". *Follow-up:* "¿O(n + m)?" → si n y m son entradas independientes, **no** se simplifica a O(n); se quedan ambas.

### A3. "Diferencia entre O(log n), O(n), O(n log n) y O(n²). Da un ejemplo de cada una."

**🎯 Qué evalúan:** que reconozcas las clases más comunes y las asocies a algoritmos reales.
**🧠 Qué necesitas saber:** qué operación produce cada clase (§1.3, §1.8).
**🗝️ Cómo pensarla:** ancla cada clase a "qué le pasa al trabajo cuando doblas los datos".
**✅ Respuesta:**
- **O(log n):** al doblar los datos, **un** paso más. Ej.: **búsqueda binaria** (parte a la mitad).
- **O(n):** al doblar los datos, **doble** trabajo. Ej.: recorrer un arreglo una vez.
- **O(n log n):** un poco más que lineal. Ej.: los **buenos ordenamientos** (merge sort, quicksort).
- **O(n²):** al doblar los datos, **cuádruple** trabajo. Ej.: **dos bucles anidados** (comparar todos contra todos).
**⚠️ Trampas:** confundir O(n log n) con O(n²). *Follow-up:* "¿cuál es el límite teórico para ordenar comparando?" → O(n log n).

### A4. "¿Qué complejidad tiene `for (int i = 1; i <= n; i *= 2)` y por qué?"

**🎯 Qué evalúan:** si sabes detectar logaritmos (la gente suele decir O(n) por reflejo).
**🧠 Qué necesitas saber:** que multiplicar/dividir el índice → logarítmico; sumar/restar → lineal (§1.8).
**🗝️ Cómo pensarla:** cuenta cuántas veces se duplica i hasta pasar n: 1, 2, 4, 8… son potencias de 2.
**✅ Respuesta:** "**O(log n)**. Como `i` se **duplica** cada vuelta (no aumenta de 1 en 1), llega a n en aproximadamente log₂(n) pasos. Con n=1.000.000, son ~20 vueltas, no un millón."
**⚠️ Trampas:** decir O(n) por ver un solo `for`. La clave no es cuántos bucles hay, sino **cómo avanza** el índice.

### A5. "Dos bucles **separados** sobre n vs dos bucles **anidados**: ¿se suman o se multiplican?"

**🎯 Qué evalúan:** la diferencia entre secuencia (suma) y anidamiento (producto) — fuente de errores muy común.
**🧠 Qué necesitas saber:** Reglas 1 y de productos de Big-O (§1.5).
**🗝️ Cómo pensarla:** "uno después de otro" = sumar; "uno dentro de otro" = multiplicar.
**✅ Respuesta:** "**Separados se suman:** n + n = 2n = **O(n)**. **Anidados se multiplican:** por cada vuelta del externo, el interno corre n veces → n × n = **O(n²)**. La diferencia entre escribir un bucle *después* o *dentro* de otro cambia por completo la complejidad."
**⚠️ Trampas:** ver dos bucles y decir O(n²) sin fijarse si están anidados o no.

### A6. "¿Qué es la complejidad de **espacio** y cómo la mides? ¿Cuenta la recursión?"

**🎯 Qué evalúan:** que no te olvides de la memoria (mucha gente solo piensa en tiempo) y que conozcas el costo oculto de la recursión.
**🧠 Qué necesitas saber:** que el espacio mide memoria extra en función de n, y que **la pila de llamadas cuenta** (§1.6, Patrón 5).
**🗝️ Cómo pensarla:** pregúntate *"¿cuánta memoria NUEVA creo según el tamaño de entrada?"*, incluyendo estructuras auxiliares y la profundidad de la recursión.
**✅ Respuesta:** "Es cuánta **memoria adicional** usa el algoritmo en función de n. Un bucle con un par de variables es O(1); crear un HashMap con n elementos es O(n). Y sí: **la recursión cuenta**, porque cada llamada pendiente ocupa un marco en la pila de llamadas. Una recursión de profundidad n usa O(n) de espacio aunque no cree ninguna estructura."
**⚠️ Trampas:** olvidar la pila de recursión. *Follow-up:* "¿cómo bajarías el espacio?" → a menudo, convertir recursión en iteración o reutilizar el arreglo (in-place).

### A7. "¿Qué son mejor, peor y caso promedio? Dame un ejemplo."

**🎯 Qué evalúan:** que entiendas que un algoritmo no tiene "una" complejidad, sino un rango según la entrada.
**🧠 Qué necesitas saber:** la distinción y por qué solemos reportar el **peor caso** (§1.7).
**🗝️ Cómo pensarla:** imagina la entrada más afortunada y la más desafortunada.
**✅ Respuesta:** "Son la complejidad según qué tan favorable sea la entrada. En **búsqueda lineal**: mejor caso O(1) (el elemento está primero), peor caso O(n) (está al final o no está), promedio O(n). Solemos reportar el **peor caso** porque da una **garantía**: 'nunca será peor que esto'. **Quicksort** es el ejemplo clásico de que importan: promedio O(n log n), pero peor caso O(n²) si el pivote se elige mal."
**⚠️ Trampas:** dar solo el caso promedio. Menciona que se reporta el peor por garantía.

### A8. "¿Qué significa **O(1) amortizado**? Da un ejemplo."

**🎯 Qué evalúan:** un concepto de nivel medio que distingue a quien entiende las estructuras por dentro.
**🧠 Qué necesitas saber:** el crecimiento del ArrayList (duplicar y copiar) y el rehashing del HashMap (cap. 1 y 5).
**🗝️ Cómo pensarla:** "no cada operación, sino el **promedio** a largo plazo".
**✅ Respuesta:** "Significa que el costo **promedio** por operación es O(1), aunque alguna operación ocasional sea cara. El ejemplo es agregar al final de un **ArrayList**: casi siempre es O(1), pero cuando se llena, crea un arreglo del doble y copia todo (O(n)). Como esa copia cara ocurre **rara vez** (tras duplicar, hay espacio para muchas inserciones baratas), repartido entre todas las operaciones el promedio es O(1). Lo mismo pasa con el rehashing de un HashMap."
**⚠️ Trampas:** confundir "amortizado" (promedio garantizado a largo plazo) con "promedio" (sobre entradas aleatorias). Son parecidos pero no idénticos.

### A9. "¿Qué es más importante optimizar, tiempo o espacio?"

**🎯 Qué evalúan:** madurez de ingeniería — que no des una respuesta absoluta y que pienses en **trade-offs** y contexto.
**🧠 Qué necesitas saber:** el concepto de trade-off tiempo/espacio (§1.6) y ejemplos (hashing gasta espacio para ganar tiempo).
**🗝️ Cómo pensarla:** la respuesta correcta empieza con **"depende"** y pregunta por las restricciones.
**✅ Respuesta:** "Depende del contexto, y lo más importante es **nombrar el trade-off** explícitamente. En un dispositivo con memoria muy limitada (embebido, móvil), el espacio manda. En la mayoría de los servicios, se busca el mejor **tiempo** aceptando un espacio razonable — por eso usamos tanto los HashMaps, que gastan O(n) de memoria para lograr búsquedas O(1). Antes de optimizar, yo preguntaría: ¿cuál es el cuello de botella real y qué recurso es escaso aquí?"
**⚠️ Trampas:** dar una respuesta absoluta ("siempre el tiempo"). Lo que evalúan es que pienses en el contexto.

---

## 4.2 Estructuras de datos (conceptuales)

> Las preguntas "explícame cómo funciona X" son pan de cada día en SDET. No basta con definir: hay que explicar el **porqué** y el **cuándo usarla**.

### B1. "¿Cómo funciona un HashMap por dentro y por qué es O(1)?"

**🎯 Qué evalúan:** comprensión real de la estructura más usada; separa a quien memoriza de quien entiende.
**🧠 Qué necesitas saber:** función hash → cubeta, colisiones, encadenamiento, factor de carga, peor caso (cap. 5).
**🗝️ Cómo pensarla:** explica el camino completo de "guardar" y "buscar", y no escondas el peor caso.
**✅ Respuesta:** "Por dentro es un **arreglo de cubetas**. Para guardar un par clave-valor, una **función hash** convierte la clave en un número, que se reduce al índice de una cubeta; ahí se guarda. Para buscar, se repite el cálculo y se va **directo** a esa cubeta — sin recorrer el resto, por eso es **O(1) promedio**. Cuando dos claves caen en la misma cubeta (una **colisión**), se guardan en una lista dentro de esa cubeta (**encadenamiento**) y se recorre comparando con `equals`. Si hay demasiadas colisiones, degrada a **O(n)** en el peor caso; Java 8+ lo mitiga convirtiendo la lista en un árbol (O(log n)). Y cuando se llena (factor de carga > 0.75), hace **rehashing**: duplica las cubetas y redistribuye."
**⚠️ Trampas:** decir solo "es O(1)" sin explicar colisiones ni el peor caso. *Follow-up casi seguro:* "¿y `hashCode`/`equals`?" → B11.

### B2. "¿Diferencia entre Array (ArrayList) y LinkedList? ¿Cuándo cada uno?"

**🎯 Qué evalúan:** que entiendas el trade-off acceso vs inserción, base de muchas decisiones de diseño.
**🧠 Qué necesitas saber:** memoria contigua vs nodos enlazados, y los Big-O de cada operación (caps. 1 y 2).
**🗝️ Cómo pensarla:** contrasta sus dos operaciones clave: acceso por índice y inserción/borrado.
**✅ Respuesta:** "El **ArrayList** guarda elementos en memoria **contigua**, así que el **acceso por índice es O(1)** (calcula la dirección directo), pero **insertar/borrar en medio es O(n)** porque hay que mover los demás. La **LinkedList** son nodos dispersos unidos por punteros: **insertar/borrar en los extremos es O(1)** (solo reconectas punteros), pero **acceder por índice es O(n)** porque hay que recorrer desde el inicio. Regla práctica: **ArrayList por defecto** (el acceso rápido y la buena localidad de caché ganan casi siempre); LinkedList solo si insertas/borras mucho en extremos y no necesitas índices."
**⚠️ Trampas:** decir que LinkedList "siempre es más rápida para insertar" — solo lo es si ya tienes la referencia a la posición.

### B3. "¿Stack vs Queue? ¿Para qué sirve cada una?"

**🎯 Qué evalúan:** que asocies la regla de acceso (LIFO/FIFO) con casos de uso reales y con DFS/BFS.
**🧠 Qué necesitas saber:** LIFO vs FIFO y sus conexiones (caps. 3 y 4).
**🗝️ Cómo pensarla:** "¿qué quiero sacar primero, lo último o lo primero que metí?".
**✅ Respuesta:** "La **pila (Stack)** es **LIFO** — el último en entrar sale primero, como una pila de platos. Sirve para deshacer (Ctrl-Z), balanceo de paréntesis, el botón 'atrás', y **DFS**. La **cola (Queue)** es **FIFO** — el primero en entrar sale primero, como la fila del banco. Sirve para procesar tareas en orden de llegada, mensajes, y **BFS**. Una conexión clave: DFS usa pila, BFS usa cola."
**⚠️ Trampas:** confundir cuál es cuál. Ancla con las analogías (platos = pila; fila = cola).

### B4. "¿Por qué los Strings son inmutables en Java y qué implica eso?"

**🎯 Qué evalúan:** un detalle de Java que afecta rendimiento y corrección, muy preguntado en SDET por su relación con aserciones.
**🧠 Qué necesitas saber:** inmutabilidad, `StringBuilder`, y `==` vs `.equals()` (cap. 1, sección Strings).
**🗝️ Cómo pensarla:** "si no cambia, cada 'modificación' crea uno nuevo — ¿qué consecuencias tiene?".
**✅ Respuesta:** "Un String, una vez creado, **no cambia**: métodos como `toUpperCase()` devuelven un objeto **nuevo**. Implicaciones: (1) concatenar en un bucle con `+=` crea un objeto nuevo cada vuelta → O(n²) y basura; por eso se usa **`StringBuilder`** (mutable) para construir. (2) Para comparar strings hay que usar **`.equals()`** (compara contenido), nunca `==` (compara si son el mismo objeto), porque `==` 'funciona' a veces por el *string pool* y falla otras → bugs intermitentes. En testing, equivocarse aquí da aserciones con falsos resultados."
**⚠️ Trampas:** decir que `toUpperCase()` modifica el string. *Follow-up:* "¿`==` vs `.equals()`?" — tenlo listo.

### B5. "¿Qué es un BST y por qué da O(log n)? ¿Cuándo se degrada?"

**🎯 Qué evalúan:** comprensión de árboles de búsqueda y conciencia del problema del desbalance.
**🧠 Qué necesitas saber:** la regla de orden del BST, la idea de descartar mitades, y el desbalance (cap. 6).
**🗝️ Cómo pensarla:** relaciónalo con la búsqueda binaria: en cada nodo descartas medio árbol.
**✅ Respuesta:** "Un **BST** es un árbol binario donde, para cada nodo, todo lo de su izquierda es **menor** y todo lo de su derecha es **mayor**. Por esa regla, al buscar puedes **descartar la mitad del árbol en cada paso** (si buscas algo menor, ignoras todo el subárbol derecho), igual que la búsqueda binaria → **O(log n)** si está balanceado. **Se degrada a O(n)** si insertas datos ya ordenados: todos caen de un lado y el árbol se vuelve una lista inclinada, sin mitades que descartar. Se evita con árboles **autobalanceados** (AVL, rojo-negro), que es lo que usa `TreeMap`."
**⚠️ Trampas:** olvidar mencionar el desbalance (es justo lo que quieren ver que sabes).

### B6. "¿Qué es un heap y cuándo lo usarías?"

**🎯 Qué evalúan:** que reconozcas la estructura para problemas de prioridad/Top-K.
**🧠 Qué necesitas saber:** min/max-heap, acceso O(1) al extremo, y la señal "K" (cap. 7).
**🗝️ Cómo pensarla:** "¿necesito siempre el mínimo o el máximo, repetidamente?".
**✅ Respuesta:** "Un **heap** (PriorityQueue) te da acceso **instantáneo al mínimo o al máximo** (O(1) para mirar, O(log n) para sacar/insertar), sin mantener todo ordenado. Lo usas cuando necesitas repetidamente el elemento más prioritario: problemas **Top-K** ('los K más grandes/frecuentes'), la **mediana de un flujo**, o algoritmos como **Dijkstra**. Truco clave: para los K **mayores** se usa un **min-heap** de tamaño K, para poder descartar fácil al más pequeño."
**⚠️ Trampas:** creer que un heap mantiene todo ordenado (solo garantiza la raíz).

### B7. "¿Cómo recorres un árbol? ¿DFS o BFS?"

**🎯 Qué evalúan:** que conozcas los recorridos y sepas cuándo cada uno.
**🧠 Qué necesitas saber:** DFS (inorden/preorden/postorden, recursión) y BFS (por niveles, cola) (cap. 6).
**🗝️ Cómo pensarla:** "¿la respuesta depende de profundidad/ramas o de niveles/cercanía?".
**✅ Respuesta:** "Dos familias. **DFS** baja por una rama hasta el fondo antes de retroceder; se hace con **recursión** y tiene tres órdenes: inorden (izq-raíz-der, que en un BST da los valores **ordenados**), preorden y postorden. **BFS** visita **nivel por nivel** con una **cola**. Uso DFS para altura, validar BST o caminos raíz-hoja; BFS para 'recorrido por niveles', el nodo más cercano, o el camino más corto en aristas."
**⚠️ Trampas:** no saber que inorden de un BST sale ordenado (pregunta muy típica).

### B8. "¿Cómo representas y recorres un grafo? ¿Por qué hay que marcar visitados?"

**🎯 Qué evalúan:** comprensión de grafos y el detalle crítico de los ciclos.
**🧠 Qué necesitas saber:** lista vs matriz de adyacencia, BFS/DFS, y por qué los visitados (cap. 8).
**🗝️ Cómo pensarla:** "¿cómo guardo las conexiones y cómo evito dar vueltas en círculo?".
**✅ Respuesta:** "Se representa casi siempre con una **lista de adyacencia** (cada nodo guarda sus vecinos), eficiente para grafos dispersos (O(V+E) espacio); la matriz de adyacencia (O(V²)) sirve para grafos densos o consultas de arista en O(1). Se recorre con **BFS** (cola, da el camino más corto sin pesos) o **DFS** (recursión, para explorar/contar componentes). Y hay que **marcar los visitados** (un HashSet) porque, a diferencia de un árbol, un grafo puede tener **ciclos**: sin marcar, recorrerías el ciclo **infinitamente**."
**⚠️ Trampas:** olvidar mencionar los visitados — es el error #1 en grafos.

### B9. "¿HashMap vs TreeMap? ¿Cuándo cada uno?"

**🎯 Qué evalúan:** que sepas el trade-off velocidad vs orden.
**🧠 Qué necesitas saber:** HashMap (O(1), sin orden) vs TreeMap (O(log n), ordenado, árbol rojo-negro) (cap. 5).
**🗝️ Cómo pensarla:** "¿necesito orden, o solo búsqueda rápida?".
**✅ Respuesta:** "**HashMap** da acceso **O(1) promedio** pero **no garantiza ningún orden**. **TreeMap** mantiene las claves **ordenadas** y permite consultas de rango ('el menor mayor que X'), pero a cambio sus operaciones son **O(log n)** (por dentro es un árbol rojo-negro autobalanceado, no usa hashing). Uso HashMap por defecto (más rápido); TreeMap cuando necesito recorrer en orden o hacer consultas de rango. Si solo necesito recordar el **orden de inserción**, uso LinkedHashMap."
**⚠️ Trampas:** asumir que HashMap mantiene orden (no lo hace).

### B10. "¿Qué es la recursión y la pila de llamadas? ¿Qué causa un StackOverflowError?"

**🎯 Qué evalúan:** comprensión profunda de recursión y de su costo en memoria.
**🧠 Qué necesitas saber:** caso base/recursivo y la call stack (Patrón 5, cap. 3).
**🗝️ Cómo pensarla:** "una función que se llama a sí misma, y cada llamada se apila".
**✅ Respuesta:** "Recursión es cuando una función **se llama a sí misma** sobre una versión más pequeña del problema, hasta un **caso base** que detiene todo. Por dentro usa la **pila de llamadas**: cada llamada pendiente se apila con sus variables, y se desapila al retornar. Un **`StackOverflowError`** ocurre cuando esa pila se llena: típicamente por **falta de caso base** (o uno que nunca se alcanza), de modo que la recursión nunca para y sigue apilando. Por eso toda recursión necesita: un caso base, y que cada llamada se acerque a él."
**⚠️ Trampas:** no relacionar recursión con la pila (es justo la conexión que evalúan).

### B11. "¿Por qué hay que sobrescribir `hashCode` y `equals` juntos?"

**🎯 Qué evalúan:** un detalle de Java que delata si entiendes cómo funcionan los HashMap por dentro.
**🧠 Qué necesitas saber:** cómo el HashMap usa hashCode para la cubeta y equals para la clave exacta (cap. 5).
**🗝️ Cómo pensarla:** "¿cómo encuentra el mapa mi objeto al guardarlo y al buscarlo?".
**✅ Respuesta:** "Porque el HashMap usa **`hashCode()`** para decidir en qué **cubeta** va la clave, y **`equals()`** para encontrar la clave exacta **dentro** de esa cubeta. Si dos objetos que son 'iguales' según `equals()` tienen **distinto** `hashCode()`, el mapa los manda a **cubetas diferentes**: guardas con uno y, al buscar con otro idéntico, mira la cubeta equivocada y 'pierde' tus datos. La regla: si `a.equals(b)`, entonces `a.hashCode() == b.hashCode()`. Por eso `String` e `Integer` funcionan perfecto como claves (ya los implementan bien) y, con clases propias, debes sobrescribir **ambos** de forma consistente."
**⚠️ Trampas:** sobrescribir solo uno. *Follow-up:* "¿qué pasa si dos objetos distintos tienen el mismo hashCode?" → es una colisión, es válido; `equals` los distingue dentro de la cubeta.

---
## 4.3 Problemas de código por patrón

> Cada problema en formato tutor: **🎯 qué evalúan · 🧠 qué necesitas saber · 🗝️ cómo pensarla (de la fuerza bruta a la solución) · ✅ código explicado con traza y Big-O · ⚠️ trampas y variantes.** Resuélvelos tapando la solución; si te atoras en "qué necesitas saber", repasa esa sección. *(Esta es la tanda 1: arreglos/strings, hashing, dos punteros, ventana, búsqueda binaria. La tanda 2 cubre listas, pilas, árboles, grafos, heaps, backtracking y DP.)*

### — Arreglos y Strings —

#### 🔹 Invertir un string (sin `reverse()`)

**🎯 Qué evalúan:** manejo básico de índices/strings y si conoces el truco de dos punteros in-place; es un "calentamiento" típico de assessment.
**🧠 Qué necesitas saber:** que un String es inmutable (por eso trabajas sobre `char[]` o `StringBuilder`), y dos punteros de extremos (cap. 1, Patrón 2).
**🗝️ Cómo pensarla:** la fuerza bruta es recorrer de atrás hacia adelante construyendo otro string (O(n) espacio). La versión elegante: dos punteros en los extremos que **intercambian y se acercan** → O(1) espacio extra.
**✅ Solución (dos punteros, in-place sobre char[]):**
```java
public static String invertir(String s) {
    char[] c = s.toCharArray();
    int izq = 0, der = c.length - 1;
    while (izq < der) {
        char tmp = c[izq]; c[izq] = c[der]; c[der] = tmp;  // intercambia extremos
        izq++; der--;                                       // acércalos
    }
    return new String(c);
}
// "abc" -> "cba"   |  O(n) tiempo, O(1) espacio extra
```
**⚠️ Trampas / variante:** intentar reasignar caracteres de un String directo (no se puede, es inmutable). *Variante simple:* `new StringBuilder(s).reverse().toString()` — válida si no te prohíben librerías.

#### 🔹 FizzBuzz

**🎯 Qué evalúan:** que puedas traducir reglas a código sin errores y que ordenes bien las condiciones; filtra a quien no programa.
**🧠 Qué necesitas saber:** el operador módulo `%` y el **orden** de los `if`.
**🗝️ Cómo pensarla:** la trampa está en el orden: el caso más específico (divisible por 3 **y** 5) va **primero**.
**✅ Solución:**
```java
for (int i = 1; i <= n; i++) {
    if (i % 15 == 0) System.out.println("FizzBuzz");       // 3 Y 5 -> primero
    else if (i % 3 == 0) System.out.println("Fizz");
    else if (i % 5 == 0) System.out.println("Buzz");
    else System.out.println(i);
}
```
**⚠️ Trampa clásica:** revisar `% 3` antes que `% 15`: entonces los múltiplos de 15 imprimen "Fizz" y nunca "FizzBuzz". Revisa siempre del caso más restrictivo al más general.

#### 🔹 ¿Es un palíndromo?

**🎯 Qué evalúan:** dos punteros y manejo de bordes (mayúsculas, espacios) si lo piden.
**🧠 Qué necesitas saber:** dos punteros de extremos (Patrón 2).
**🗝️ Cómo pensarla:** compara el primero con el último, avanza hacia el centro; si en algún punto difieren, no es palíndromo.
**✅ Solución:**
```java
public static boolean esPalindromo(String s) {
    int izq = 0, der = s.length() - 1;
    while (izq < der) {
        if (s.charAt(izq) != s.charAt(der)) return false;
        izq++; der--;
    }
    return true;
}
// "reconocer" -> true ; "hola" -> false   |  O(n) tiempo, O(1) espacio
```
**⚠️ Variante frecuente:** "ignorando mayúsculas y no-alfanuméricos" (ej. "A man, a plan, a canal: Panama") → salta caracteres no alfanuméricos con `Character.isLetterOrDigit` y compara en minúsculas.

#### 🔹 Máximo subarreglo contiguo (algoritmo de Kadane) ⭐ MUY frecuente

**🎯 Qué evalúan:** si puedes pasar de la fuerza bruta O(n²) a una solución O(n) elegante; es un clásico que separa niveles.
**🧠 Qué necesitas saber:** la idea de "arrastrar el mejor resultado hasta aquí" (una mini-DP de una variable).
**🗝️ Cómo pensarla:** fuerza bruta = probar todos los subarreglos (O(n²)). El insight de Kadane: recorriendo una vez, en cada posición decides *"¿me conviene extender la suma que traía, o empezar de nuevo desde aquí?"*. Si lo que traías es negativo, te lastra: empieza de nuevo.
**✅ Solución:**
```java
public static int maxSubarreglo(int[] arr) {
    int mejorAqui = arr[0];   // mejor suma que TERMINA en la posición actual
    int mejorGlobal = arr[0]; // mejor suma vista en todo el recorrido
    for (int i = 1; i < arr.length; i++) {
        mejorAqui = Math.max(arr[i], mejorAqui + arr[i]);   // ¿empiezo aquí o extiendo?
        mejorGlobal = Math.max(mejorGlobal, mejorAqui);
    }
    return mejorGlobal;
}
// [-2,1,-3,4,-1,2,1,-5,4] -> 6  (el subarreglo [4,-1,2,1])  |  O(n), O(1)
```
✍️ **Traza (clave):** en `i=3` (valor 4), `mejorAqui` traía algo negativo, así que `max(4, neg+4)=4` → reinicia en 4. Luego va sumando -1, 2, 1 → llega a 6.
**⚠️ Trampas:** inicializar en 0 (falla si todos son negativos; inicializa con `arr[0]`). *Follow-up:* "¿y devolver los índices del subarreglo?" → guarda dónde reiniciaste.

### — Hashing —

#### 🔹 Two Sum ⭐ el problema-arquetipo

**🎯 Qué evalúan:** el reflejo de cambiar O(n²) por O(n) con un HashMap — la habilidad #1 que buscan.
**🧠 Qué necesitas saber:** HashMap y la idea "recuerda lo visto y pregunta por el complemento" (Patrón 1).
**🗝️ Cómo pensarla:** fuerza bruta = comparar cada par (O(n²)). Optimización: por cada número, lo que me falta es `objetivo - actual`; si ya vi ese complemento (consulta O(1) al Map), encontré la pareja. Recorro una vez.
**✅ Solución:**
```java
public static int[] twoSum(int[] nums, int objetivo) {
    Map<Integer,Integer> visto = new HashMap<>();   // valor -> índice
    for (int i = 0; i < nums.length; i++) {
        int falta = objetivo - nums[i];
        if (visto.containsKey(falta)) return new int[]{visto.get(falta), i}; // pregunta
        visto.put(nums[i], i);                                               // luego guarda
    }
    return new int[]{};
}
// [2,7,11,15], 9 -> [0,1]   |  O(n) tiempo, O(n) espacio
```
**⚠️ Trampa:** guardar antes de preguntar (te emparejas contigo mismo). *Variante:* si el arreglo está **ordenado**, dos punteros lo hace en O(1) espacio.

#### 🔹 ¿Contiene duplicados?

**🎯 Qué evalúan:** elegir la estructura correcta (Set) para "¿ya existe?".
**🧠 Qué necesitas saber:** HashSet y que `add` devuelve false si ya existía (cap. 5).
**🗝️ Cómo pensarla:** recorre metiendo en un Set; si alguno ya estaba, hay duplicado.
**✅ Solución:**
```java
public static boolean hayDuplicados(int[] nums) {
    Set<Integer> visto = new HashSet<>();
    for (int n : nums) if (!visto.add(n)) return true;  // add() falso = ya existía
    return false;
}
// [1,2,3,1] -> true   |  O(n) tiempo, O(n) espacio
```
**⚠️ Trade-off:** O(n) espacio. Alternativa O(1) espacio pero O(n log n) tiempo: ordenar y buscar vecinos iguales. **Nombrar el trade-off es lo que evalúan.**

#### 🔹 ¿Son anagramas?

**🎯 Qué evalúan:** conteo de frecuencias (el segundo uso más común del hashing).
**🧠 Qué necesitas saber:** Map como contador, o el truco del arreglo de 26 (`c - 'a'`) (Patrón 1).
**🗝️ Cómo pensarla:** dos palabras son anagramas si tienen **las mismas letras con las mismas frecuencias**. Cuenta las de una sumando y las de la otra restando; si todo queda en 0, son anagramas.
**✅ Solución:**
```java
public static boolean anagramas(String a, String b) {
    if (a.length() != b.length()) return false;
    int[] c = new int[26];
    for (int i = 0; i < a.length(); i++) { c[a.charAt(i)-'a']++; c[b.charAt(i)-'a']--; }
    for (int x : c) if (x != 0) return false;
    return true;
}
// "listen","silent" -> true   |  O(n) tiempo, O(1) espacio (26 fijo)
```
**⚠️ Variante:** "agrupa los anagramas de una lista" → usa un Map cuya clave sea la palabra **ordenada** (firma común) y el valor la lista de palabras con esa firma.

### — Dos punteros —

#### 🔹 Mover ceros al final (in-place)

**🎯 Qué evalúan:** la técnica lento/rápido para compactar sin memoria extra.
**🧠 Qué necesitas saber:** dos punteros lento/rápido (Patrón 2).
**🗝️ Cómo pensarla:** un puntero "lento" marca dónde va el próximo no-cero; el "rápido" explora. Cada vez que el rápido halla un no-cero, lo coloca en la posición del lento y avanza el lento. Los ceros quedan empujados al final.
**✅ Solución:**
```java
public static void moverCeros(int[] arr) {
    int lento = 0;
    for (int rapido = 0; rapido < arr.length; rapido++)
        if (arr[rapido] != 0) {
            int t = arr[lento]; arr[lento] = arr[rapido]; arr[rapido] = t;
            lento++;
        }
}
// [0,1,0,3,12] -> [1,3,12,0,0]   |  O(n) tiempo, O(1) espacio
```
**⚠️ Trampa:** querer "borrar y reinsertar" ceros (O(n²)). El patrón lento/rápido lo hace en una pasada.

#### 🔹 3Sum (tríos que suman 0)

**🎯 Qué evalúan:** combinar **ordenar + dos punteros** y manejar duplicados; es un clásico de nivel medio.
**🧠 Qué necesitas saber:** ordenar y dos punteros de extremos (Patrón 2).
**🗝️ Cómo pensarla:** fuerza bruta = tres bucles (O(n³)). Mejor: **ordena**; fija un número con un bucle, y para el resto usa dos punteros (como Two Sum ordenado) buscando `-fijo`. O(n²).
**✅ Solución (idea):**
```java
Arrays.sort(nums);
for (int i = 0; i < nums.length - 2; i++) {
    if (i > 0 && nums[i] == nums[i-1]) continue;          // evita tríos repetidos
    int izq = i + 1, der = nums.length - 1, objetivo = -nums[i];
    while (izq < der) {
        int suma = nums[izq] + nums[der];
        if (suma == objetivo) { /* guarda el trío; avanza ambos saltando duplicados */ izq++; der--; }
        else if (suma < objetivo) izq++;
        else der--;
    }
}
// O(n²) tiempo, O(1) espacio extra (sin contar el orden)
```
**⚠️ Trampas:** olvidar saltar duplicados (genera tríos repetidos). El ordenamiento previo es lo que habilita los dos punteros.

### — Ventana deslizante —

#### 🔹 Substring más largo sin caracteres repetidos ⭐

**🎯 Qué evalúan:** dominio de la ventana variable (expandir/contraer) — pregunta muy frecuente.
**🧠 Qué necesitas saber:** ventana deslizante variable + un Set (Patrón 3).
**🗝️ Cómo pensarla:** fuerza bruta = probar todos los substrings (O(n²)+). Con ventana: expande el borde derecho metiendo caracteres a un Set; si aparece un repetido, **contrae** por la izquierda hasta que salga; registra el máximo tamaño. Cada carácter entra y sale una vez → O(n).
**✅ Solución:**
```java
public static int sinRepetir(String s) {
    Set<Character> ventana = new HashSet<>();
    int izq = 0, max = 0;
    for (int der = 0; der < s.length(); der++) {
        while (ventana.contains(s.charAt(der))) { ventana.remove(s.charAt(izq)); izq++; }
        ventana.add(s.charAt(der));
        max = Math.max(max, der - izq + 1);
    }
    return max;
}
// "abcabcbb" -> 3   |  O(n) tiempo, O(min(n, alfabeto)) espacio
```
**⚠️ Trampa:** calcular mal el tamaño (`der - izq + 1`, inclusivo). *Ver traza completa en §3-Patrón 3.*

#### 🔹 Mejor momento para comprar y vender una acción ⭐

**🎯 Qué evalúan:** reconocer que un problema "de bolsa" es en realidad "mín visto + mejor ganancia" en una pasada.
**🧠 Qué necesitas saber:** llevar un mínimo corriente (variante de ventana/recorrido único).
**🗝️ Cómo pensarla:** fuerza bruta = probar cada par compra/venta (O(n²)). Insight: recorre una vez llevando el **precio mínimo visto hasta ahora**; en cada día, la mejor ganancia posible es `precio_hoy - mínimo_visto`. Guarda la mayor.
**✅ Solución:**
```java
public static int maxGanancia(int[] precios) {
    int minVisto = Integer.MAX_VALUE, mejor = 0;
    for (int p : precios) {
        minVisto = Math.min(minVisto, p);        // el mejor día para haber comprado
        mejor = Math.max(mejor, p - minVisto);   // ganancia si vendo hoy
    }
    return mejor;
}
// [7,1,5,3,6,4] -> 5  (compra en 1, vende en 6)   |  O(n), O(1)
```
**⚠️ Trampa:** permitir vender antes de comprar. Como solo restas contra el mínimo **anterior**, eso queda excluido naturalmente.

### — Búsqueda binaria —

#### 🔹 Búsqueda binaria clásica

**🎯 Qué evalúan:** implementarla **sin bugs de límites** (lo que más falla en vivo).
**🧠 Qué necesitas saber:** datos ordenados, `izq<=der`, medio anti-overflow (Patrón 4).
**🗝️ Cómo pensarla:** compara con el medio; si es menor, ve a la derecha; si mayor, a la izquierda; descarta media lista cada vez.
**✅ Solución:**
```java
public static int buscar(int[] arr, int objetivo) {
    int izq = 0, der = arr.length - 1;
    while (izq <= der) {
        int medio = izq + (der - izq) / 2;
        if (arr[medio] == objetivo) return medio;
        else if (arr[medio] < objetivo) izq = medio + 1;
        else der = medio - 1;
    }
    return -1;
}
// O(log n)
```
**⚠️ Trampas:** `<` en vez de `<=` (deja sin revisar 1 elemento); `izq=medio` sin +1 (bucle infinito); `(izq+der)/2` (overflow). *Ver la muestra suprema completa en §3-Patrón 4.*

#### 🔹 Buscar el mínimo en un arreglo ordenado y ROTADO

**🎯 Qué evalúan:** adaptar la búsqueda binaria cuando el arreglo no está perfectamente ordenado (nivel medio/FAANG).
**🧠 Qué necesitas saber:** búsqueda binaria + razonar qué mitad está ordenada (Patrón 4).
**🗝️ Cómo pensarla:** un arreglo rotado tiene un "punto de quiebre" que es el mínimo. Compara el medio con el extremo derecho: si `arr[medio] > arr[der]`, el quiebre está a la derecha; si no, está en el medio o a la izquierda.
**✅ Solución:**
```java
public static int minRotado(int[] arr) {
    int izq = 0, der = arr.length - 1;
    while (izq < der) {
        int medio = izq + (der - izq) / 2;
        if (arr[medio] > arr[der]) izq = medio + 1;  // el mínimo está a la derecha
        else der = medio;                            // está aquí o a la izquierda
    }
    return arr[izq];
}
// [4,5,6,7,0,1,2] -> 0   |  O(log n)
```
**⚠️ Trampa:** comparar con el extremo **izquierdo** en vez del derecho complica los casos; comparar con `arr[der]` es el método limpio.

---
### — Listas enlazadas —

#### 🔹 Invertir una lista enlazada ⭐

**🎯 Qué evalúan:** manejo fino de punteros sin perder nodos — el problema de listas más preguntado.
**🧠 Qué necesitas saber:** nodos y referencias; la técnica de tres punteros `prev/actual/siguiente` (cap. 2).
**🗝️ Cómo pensarla:** recorres la lista invirtiendo cada puntero para que apunte al **anterior**. La clave: **guarda el siguiente ANTES** de reasignar, o perderías el resto de la lista.
**✅ Solución:**
```java
public static Nodo invertir(Nodo cabeza) {
    Nodo prev = null, actual = cabeza;
    while (actual != null) {
        Nodo siguiente = actual.siguiente;  // 1) GUARDA el siguiente (imprescindible)
        actual.siguiente = prev;            // 2) invierte el puntero
        prev = actual;                      // 3) avanza prev
        actual = siguiente;                 // 4) avanza actual
    }
    return prev;  // nueva cabeza
}
// 1->2->3  =>  3->2->1   |  O(n) tiempo, O(1) espacio
```
**⚠️ Trampa:** reasignar `actual.siguiente = prev` antes de guardar `siguiente` → pierdes todo lo que venía después.

#### 🔹 Detectar un ciclo (liebre y tortuga)

**🎯 Qué evalúan:** que conozcas la técnica lento/rápido y logres O(1) espacio.
**🧠 Qué necesitas saber:** dos punteros a distinta velocidad (Patrón 2, cap. 2).
**🗝️ Cómo pensarla:** la solución obvia usa un Set de nodos visitados (O(n) espacio). La elegante: un puntero **lento** avanza 1 y uno **rápido** avanza 2; si hay ciclo, el rápido "alcanza" al lento (como dos corredores en una pista circular); si no, el rápido llega a `null`.
**✅ Solución:**
```java
public static boolean tieneCiclo(Nodo cabeza) {
    Nodo lento = cabeza, rapido = cabeza;
    while (rapido != null && rapido.siguiente != null) {
        lento = lento.siguiente;            // +1
        rapido = rapido.siguiente.siguiente;// +2
        if (lento == rapido) return true;   // se encontraron -> hay ciclo
    }
    return false;
}
// O(n) tiempo, O(1) espacio
```
**⚠️ Trampa:** no verificar `rapido != null && rapido.siguiente != null` → NullPointerException al final.

#### 🔹 Fusionar dos listas ordenadas

**🎯 Qué evalúan:** la operación de "mezcla" (la misma de merge sort) sobre listas.
**🧠 Qué necesitas saber:** recorrer dos listas con dos punteros, comparando cabezas; el truco del **nodo centinela (dummy)** para simplificar.
**🗝️ Cómo pensarla:** como unir dos filas ordenadas: compara las cabezas, engancha la menor, avanza esa lista; repite. Un nodo "dummy" inicial evita casos especiales para la cabeza.
**✅ Solución:**
```java
public static Nodo fusionar(Nodo a, Nodo b) {
    Nodo dummy = new Nodo(0), cola = dummy;     // centinela para simplificar
    while (a != null && b != null) {
        if (a.valor <= b.valor) { cola.siguiente = a; a = a.siguiente; }
        else                    { cola.siguiente = b; b = b.siguiente; }
        cola = cola.siguiente;
    }
    cola.siguiente = (a != null) ? a : b;       // engancha lo que sobre (ya ordenado)
    return dummy.siguiente;
}
// 1->3->5 , 2->4 => 1->2->3->4->5   |  O(n+m), O(1)
```
**⚠️ Truco clave:** el **dummy** evita escribir lógica especial para el primer nodo. Recuérdalo: aparece en muchísimos problemas de listas.

#### 🔹 Encontrar el nodo medio

**🎯 Qué evalúan:** otra aplicación de lento/rápido.
**🧠 Qué necesitas saber:** dos punteros a distinta velocidad.
**🗝️ Cómo pensarla:** cuando el rápido (avanza 2) llega al final, el lento (avanza 1) está justo a la mitad.
**✅ Solución:**
```java
public static Nodo medio(Nodo cabeza) {
    Nodo lento = cabeza, rapido = cabeza;
    while (rapido != null && rapido.siguiente != null) {
        lento = lento.siguiente; rapido = rapido.siguiente.siguiente;
    }
    return lento;   // el medio (en lista par, el segundo de los dos centrales)
}
// O(n), O(1)  (una sola pasada, sin contar primero la longitud)
```
**⚠️ Variante:** combina con "invertir la segunda mitad" para verificar si una lista es palíndromo en O(1) espacio.

### — Pilas y Colas —

#### 🔹 Paréntesis válidos ⭐

**🎯 Qué evalúan:** reconocer que el anidamiento "se abre y se cierra" pide una pila (LIFO).
**🧠 Qué necesitas saber:** pila y el mapeo cierre→apertura (cap. 3, Patrón 9).
**🗝️ Cómo pensarla:** cada apertura se apila; cada cierre debe casar con el tope (la última apertura sin cerrar). Al final, pila vacía = balanceado.
**✅ Solución:**
```java
public static boolean valido(String s) {
    Deque<Character> pila = new ArrayDeque<>();
    Map<Character,Character> pares = Map.of(')','(', ']','[', '}','{');
    for (char c : s.toCharArray()) {
        if (c=='('||c=='['||c=='{') pila.push(c);                 // apertura
        else if (pila.isEmpty() || pila.pop()!=pares.get(c)) return false; // cierre debe casar
    }
    return pila.isEmpty();
}
// "({[]})" -> true ; "([)]" -> false   |  O(n)
```
**⚠️ Trampa:** olvidar verificar `pila.isEmpty()` antes del `pop` (un cierre sin apertura previa).

#### 🔹 Min-Stack (pila con mínimo en O(1))

**🎯 Qué evalúan:** diseño de estructura — cómo obtener el mínimo en O(1) sin recorrer.
**🧠 Qué necesitas saber:** que puedes llevar una **segunda pila** con los mínimos.
**🗝️ Cómo pensarla:** mantén una pila auxiliar que en cada nivel guarda el mínimo **hasta ese punto**; al hacer push, apilas `min(nuevo, minActual)`; al pop, sacas de ambas. Así `getMin()` es solo mirar el tope de la auxiliar.
**✅ Solución (idea):**
```java
Deque<Integer> pila = new ArrayDeque<>(), mins = new ArrayDeque<>();
void push(int x){ pila.push(x); mins.push(mins.isEmpty()? x : Math.min(x, mins.peek())); }
void pop(){ pila.pop(); mins.pop(); }
int getMin(){ return mins.peek(); }   // O(1)
```
**⚠️ Trampa:** intentar calcular el mínimo recorriendo (O(n)). El truco es **precalcular** el mínimo por nivel.

#### 🔹 Temperaturas diarias (pila monótona)

**🎯 Qué evalúan:** el patrón "siguiente elemento mayor" en O(n).
**🧠 Qué necesitas saber:** pila monótona de índices (Patrón 9).
**🗝️ Cómo pensarla:** fuerza bruta = para cada día mirar todos los siguientes (O(n²)). Con una pila que guarda **índices** de días aún sin resolver: cuando llega un día más caluroso, resuelve a todos los de la pila más fríos que él.
**✅ Solución:**
```java
public static int[] diasMasCaluroso(int[] t) {
    int[] res = new int[t.length];
    Deque<Integer> pila = new ArrayDeque<>();
    for (int i = 0; i < t.length; i++) {
        while (!pila.isEmpty() && t[i] > t[pila.peek()]) { int p = pila.pop(); res[p] = i - p; }
        pila.push(i);
    }
    return res;
}
// [73,74,75,71,69,72,76,73] -> [1,1,4,2,1,1,0,0]   |  O(n)
```
**⚠️ Clave:** la pila guarda **índices** (no temperaturas) para poder calcular la distancia en días.

### — Árboles —

#### 🔹 Profundidad máxima de un árbol binario

**🎯 Qué evalúan:** la plantilla recursiva "pide a los hijos y combina".
**🧠 Qué necesitas saber:** DFS recursivo (cap. 6, Patrón 7).
**🗝️ Cómo pensarla:** la profundidad de un nodo es 1 + la mayor de las profundidades de sus hijos. Caso base: árbol vacío = 0.
**✅ Solución:**
```java
public static int profundidad(Nodo n) {
    if (n == null) return 0;
    return 1 + Math.max(profundidad(n.izq), profundidad(n.der));
}
// O(n) tiempo, O(altura) espacio (pila de recursión)
```
**⚠️ Trampa:** olvidar el caso base null. *Misma plantilla resuelve:* ¿balanceado?, diámetro, suma de nodos.

#### 🔹 Invertir un árbol binario (espejo)

**🎯 Qué evalúan:** recursión sobre árboles (famoso por una anécdota de entrevista).
**🧠 Qué necesitas saber:** DFS recursivo.
**🗝️ Cómo pensarla:** intercambia los hijos de cada nodo, recursivamente.
**✅ Solución:**
```java
public static Nodo invertir(Nodo n) {
    if (n == null) return null;
    Nodo t = n.izq; n.izq = n.der; n.der = t;  // intercambia hijos
    invertir(n.izq); invertir(n.der);          // baja en ambos
    return n;
}
// O(n), O(altura)
```
**⚠️ Nota:** se puede hacer también con BFS (cola) intercambiando hijos al sacar cada nodo.

#### 🔹 Recorrido por niveles (level order) ⭐

**🎯 Qué evalúan:** BFS con cola y el truco de procesar por tandas.
**🧠 Qué necesitas saber:** BFS con cola y capturar `cola.size()` por nivel (cap. 6, Patrón 7).
**🗝️ Cómo pensarla:** mete la raíz; en cada vuelta procesa **exactamente** los nodos del nivel actual (su cantidad es `cola.size()` al inicio) y encola sus hijos.
**✅ Solución:**
```java
public static List<List<Integer>> niveles(Nodo raiz) {
    List<List<Integer>> res = new ArrayList<>();
    if (raiz == null) return res;
    Queue<Nodo> cola = new LinkedList<>(); cola.add(raiz);
    while (!cola.isEmpty()) {
        int tam = cola.size();                       // nodos de ESTE nivel
        List<Integer> nivel = new ArrayList<>();
        for (int i = 0; i < tam; i++) {
            Nodo n = cola.poll(); nivel.add(n.valor);
            if (n.izq != null) cola.add(n.izq);
            if (n.der != null) cola.add(n.der);
        }
        res.add(nivel);
    }
    return res;
}
// O(n), O(n)
```
**⚠️ Clave:** capturar `tam = cola.size()` **antes** del for interno. Resuelve también "vista lateral derecha" (el último de cada nivel).

#### 🔹 Validar un BST

**🎯 Qué evalúan:** entender la **regla global** del BST (no basta comparar padre-hijo).
**🧠 Qué necesitas saber:** la propiedad del BST y que cada nodo tiene un rango válido (cap. 6).
**🗝️ Cómo pensarla:** ⚠️ el error típico es solo comparar cada nodo con sus hijos directos — insuficiente. La forma correcta: pasa hacia abajo un **rango (min, max)** permitido; cada nodo debe caer dentro, y estrecha el rango para sus hijos. (Alternativa: el **inorden** debe salir estrictamente creciente.)
**✅ Solución (con rango):**
```java
public static boolean esBST(Nodo n, long min, long max) {
    if (n == null) return true;
    if (n.valor <= min || n.valor >= max) return false;       // fuera de rango
    return esBST(n.izq, min, n.valor) && esBST(n.der, n.valor, max);
}
// llamada inicial: esBST(raiz, Long.MIN_VALUE, Long.MAX_VALUE)   |  O(n)
```
**⚠️ Trampa principal:** validar solo `izq < nodo < der` localmente; un nieto puede violar la regla aunque los padres directos no.

#### 🔹 ¿Son iguales dos árboles?

**🎯 Qué evalúan:** recursión que avanza en dos árboles a la vez.
**🧠 Qué necesitas saber:** DFS paralelo.
**🗝️ Cómo pensarla:** son iguales si las raíces coinciden y, recursivamente, sus izquierdos y derechos también.
**✅ Solución:**
```java
public static boolean iguales(Nodo a, Nodo b) {
    if (a == null && b == null) return true;
    if (a == null || b == null || a.valor != b.valor) return false;
    return iguales(a.izq, b.izq) && iguales(a.der, b.der);
}
// O(n)
```
**⚠️ Trampa:** olvidar el caso "uno null y el otro no" (estructuras distintas).

### — Grafos —

#### 🔹 Número de islas ⭐

**🎯 Qué evalúan:** ver la cuadrícula como grafo y recorrer marcando.
**🧠 Qué necesitas saber:** DFS/BFS sobre matriz + marcar visitados (cap. 8, Patrón 8).
**🗝️ Cómo pensarla:** recorre la matriz; cada vez que halles un '1' no visitado, es una **isla nueva** → cuéntala y "hunde" toda su tierra conectada (DFS a los 4 vecinos) para no recontarla.
**✅ Solución:**
```java
public static int contarIslas(char[][] g) {
    int islas = 0;
    for (int i=0;i<g.length;i++) for (int j=0;j<g[0].length;j++)
        if (g[i][j]=='1') { islas++; hundir(g,i,j); }
    return islas;
}
private static void hundir(char[][] g,int i,int j){
    if (i<0||j<0||i>=g.length||j>=g[0].length||g[i][j]=='0') return;
    g[i][j]='0';
    hundir(g,i+1,j); hundir(g,i-1,j); hundir(g,i,j+1); hundir(g,i,j-1);
}
// O(filas × columnas)
```
**⚠️ Trampa:** olvidar marcar (hundir) → cuentas la misma isla muchas veces o entras en bucle.

#### 🔹 Course Schedule (¿se pueden tomar todos los cursos?)

**🎯 Qué evalúan:** reconocer dependencias como grafo dirigido y detectar ciclos (orden topológico).
**🧠 Qué necesitas saber:** grafo dirigido, grados de entrada, algoritmo de Kahn (sección "Algoritmos de grafos con nombre").
**🗝️ Cómo pensarla:** los cursos son nodos; "B requiere A" es una arista A→B. Se pueden tomar todos **si y solo si NO hay ciclo**. Aplica orden topológico (Kahn): si logras ordenar los `n` cursos, sí; si quedan cursos atrapados (ciclo), no.
**✅ Solución (idea):** construye `gradoEntrada[]`, mete a una cola los de grado 0, ve "completando" y reduciendo grados; cuenta cuántos completaste. Si `completados == n` → true; si no, hay ciclo → false. **O(V+E).**
**⚠️ Clave:** este problema **es** detección de ciclo en un grafo dirigido disfrazada.

### — Heaps —

#### 🔹 K-ésimo elemento más grande

**🎯 Qué evalúan:** el patrón Top-K con heap y el truco del min-heap.
**🧠 Qué necesitas saber:** PriorityQueue de tamaño K (cap. 7, Patrón 11).
**🗝️ Cómo pensarla:** mantén un **min-heap de tamaño K**; al exceder K, saca el mínimo. Al final, la raíz es el K-ésimo mayor. O(n log k), mejor que ordenar todo si k es chico.
**✅ Solución:**
```java
public static int kMayor(int[] nums, int k) {
    PriorityQueue<Integer> h = new PriorityQueue<>();
    for (int n : nums) { h.add(n); if (h.size() > k) h.poll(); }
    return h.peek();
}
// [3,2,1,5,6,4], k=2 -> 5   |  O(n log k)
```
**⚠️ Trampa:** usar max-heap (tendrías que sacar k-1 elementos). El min-heap de tamaño k es lo limpio.

#### 🔹 K elementos más frecuentes

**🎯 Qué evalúan:** combinar dos patrones (hashing + heap).
**🧠 Qué necesitas saber:** Map de frecuencias + min-heap por frecuencia.
**🗝️ Cómo pensarla:** (1) cuenta frecuencias con un Map; (2) mantén un min-heap de tamaño k **ordenado por frecuencia**, descartando el menos frecuente.
**✅ Solución (idea):**
```java
Map<Integer,Integer> f = new HashMap<>();
for (int n: nums) f.put(n, f.getOrDefault(n,0)+1);
PriorityQueue<Integer> h = new PriorityQueue<>((a,b)->f.get(a)-f.get(b));
for (int n: f.keySet()){ h.add(n); if (h.size()>k) h.poll(); }
// los k más frecuentes quedan en h   |  O(n log k)
```
**⚠️ Nota:** reconocer que es **hashing + heap** combinados es señal de madurez.

### — Recursión y Backtracking —

#### 🔹 Todos los subconjuntos ⭐

**🎯 Qué evalúan:** el esqueleto "elige · explora · deshaz".
**🧠 Qué necesitas saber:** backtracking (Patrón 6).
**🗝️ Cómo pensarla:** cada estado parcial ya es un subconjunto válido; para cada elemento desde un índice, elígelo, explora más adelante, y deshaz para probar sin él.
**✅ Solución:**
```java
void backtrack(int[] nums, int inicio, List<Integer> actual, List<List<Integer>> res){
    res.add(new ArrayList<>(actual));                // copia del estado
    for (int i=inicio;i<nums.length;i++){
        actual.add(nums[i]);                         // ELIGE
        backtrack(nums,i+1,actual,res);              // EXPLORA
        actual.remove(actual.size()-1);              // DESHAZ
    }
}
// [1,2,3] -> 8 subconjuntos   |  O(2ⁿ)
```
**⚠️ Trampa:** guardar `actual` (referencia) en vez de **una copia**, y olvidar el "deshaz".

#### 🔹 Permutaciones

**🎯 Qué evalúan:** backtracking con elementos "usados".
**🧠 Qué necesitas saber:** la misma plantilla, con un arreglo `usado`.
**🗝️ Cómo pensarla:** una permutación está completa cuando usa todos; en cada paso prueba cada elemento aún no usado.
**✅ Solución (idea):** lleva `boolean[] usado`; si `actual.size()==n` guarda; si no, por cada `i` no usado: marca, agrega, recurre, desmarca y quita. **O(n!).**
**⚠️ Clave:** mismo esqueleto que subconjuntos; solo cambian "¿qué es completa?" y "¿qué opciones hay?".

#### 🔹 Combination Sum (combinaciones que suman un objetivo)

**🎯 Qué evalúan:** backtracking con poda (cuando te pasas del objetivo, corta).
**🧠 Qué necesitas saber:** backtracking + poda.
**🗝️ Cómo pensarla:** en cada paso, si la suma parcial **excede** el objetivo, abandona esa rama (poda); si lo iguala, guarda. Para permitir repetir un número, recurres con el **mismo** índice.
**✅ Idea de poda:** `if (suma > objetivo) return;` y `if (suma == objetivo) { guarda; return; }` antes del bucle de opciones.
**⚠️ Trampa:** no podar → explora ramas inútiles y se dispara el costo.

### — Programación dinámica —

#### 🔹 Subir escaleras (cuántas formas) ⭐

**🎯 Qué evalúan:** detectar la recurrencia y convertir recursión exponencial en O(n).
**🧠 Qué necesitas saber:** la relación `dp[i]=dp[i-1]+dp[i-2]` (Patrón 13).
**🗝️ Cómo pensarla:** a cada escalón llegas desde el anterior (paso de 1) o desde el de dos atrás (paso de 2), así que las formas se suman — es Fibonacci disfrazado.
**✅ Solución:**
```java
public static int formas(int n){
    if (n<=2) return n;
    int a=1,b=2;
    for (int i=3;i<=n;i++){ int c=a+b; a=b; b=c; }   // dp[i]=dp[i-1]+dp[i-2], O(1) espacio
    return b;
}
// n=5 -> 8   |  O(n) tiempo, O(1) espacio
```
**⚠️ Trampa:** resolverlo recursivo sin memoria → O(2ⁿ). La recurrencia + tabla lo baja a O(n).

#### 🔹 Cambio de monedas (mínimo número)

**🎯 Qué evalúan:** DP de optimización con una recurrencia menos obvia.
**🧠 Qué necesitas saber:** `dp[c] = 1 + min(dp[c - moneda])` (Patrón 13).
**🗝️ Cómo pensarla:** la mínima cantidad para `c` es 1 (la moneda que uso ahora) más la mínima para `c - esa_moneda`, probando cada moneda. Llena de menor a mayor cantidad.
**✅ Solución:**
```java
public static int minMonedas(int[] monedas, int c){
    int[] dp = new int[c+1]; Arrays.fill(dp, c+1); dp[0]=0;
    for (int cant=1; cant<=c; cant++)
        for (int m: monedas) if (m<=cant) dp[cant]=Math.min(dp[cant], 1+dp[cant-m]);
    return dp[c] > c ? -1 : dp[c];
}
// {1,2,5}, 11 -> 3   |  O(c × nº monedas)
```
**⚠️ Trampa:** confundirlo con "todas las combinaciones" (eso sería backtracking). Aquí piden el **mínimo** → DP.

#### 🔹 House Robber (máximo sin robar casas adyacentes)

**🎯 Qué evalúan:** una recurrencia con una decisión binaria por paso.
**🧠 Qué necesitas saber:** `dp[i] = max(dp[i-1], dp[i-2] + casa[i])`.
**🗝️ Cómo pensarla:** en cada casa decides: **no robarla** (te quedas con lo mejor hasta la anterior) o **robarla** (lo mejor hasta dos atrás + esta casa, porque no puedes la adyacente). Toma el máximo.
**✅ Solución:**
```java
public static int robar(int[] casas){
    int dos=0, uno=0;               // mejor hasta i-2 y hasta i-1
    for (int x: casas){ int cur=Math.max(uno, dos+x); dos=uno; uno=cur; }
    return uno;
}
// [2,7,9,3,1] -> 12 (2+9+1)   |  O(n), O(1)
```
**⚠️ Trampa:** creer que siempre conviene robar una de cada dos; la DP elige óptimamente según los valores.

---
## 4.4 Preguntas verbales / de comunicación

> En una entrevista de código, **cómo piensas en voz alta** pesa tanto como la solución. Aquí, cada pregunta con **🎯 qué evalúan · 🗝️ cómo responder (la estructura) · ✅ respuesta modelo · ⚠️ qué NO hacer.** Practícalas en voz alta: la fluidez se entrena.

### V1. "¿Cómo abordarías un problema de algoritmos que nunca has visto?"

**🎯 Qué evalúan:** que tengas un **método** y no te paralices ante lo desconocido — más valioso que saberte un problema concreto.
**🗝️ Cómo responder:** describe un proceso ordenado (el framework universal del §3.0).
**✅ Respuesta modelo:** "Sigo un proceso de pasos. Primero **reformulo** el problema con mis palabras y hago **preguntas aclaratorias** (¿entrada vacía?, ¿duplicados?, ¿ordenado?, ¿qué devuelvo si no hay respuesta?). Luego resuelvo **un ejemplo pequeño a mano** para entender la mecánica. Planteo la **fuerza bruta** con su Big-O —tener algo le gana a tener nada— e identifico el **cuello de botella** (normalmente un bucle anidado). Ahí busco el **patrón** que lo optimiza (hash, dos punteros, ventana...). Codifico **narrando** lo que hago, y al final **pruebo casos borde** y doy la complejidad."
**⚠️ Qué NO hacer:** lanzarte a codificar sin aclarar ni planear. El silencio y el código a ciegas es la peor señal.

### V2. "Tu solución es O(n²). ¿Cómo la mejorarías?"

**🎯 Qué evalúan:** si sabes localizar el cuello de botella y conoces las herramientas de optimización.
**🗝️ Cómo responder:** identifica el bucle anidado y propón el cambio concreto.
**✅ Respuesta modelo:** "El O(n²) casi siempre viene de un bucle anidado que compara todos contra todos. Mi primera pregunta es: ¿puedo reemplazar el bucle interno por una **consulta O(1) a un HashMap** de lo que ya vi? Eso suele bajarlo a O(n). Si los datos están (o puedo dejarlos) **ordenados**, quizá **dos punteros** o **búsqueda binaria** lo resuelvan en O(n) u O(n log n) sin memoria extra. Y si recalculo subproblemas, **memoización**."
**⚠️ Qué NO hacer:** decir "lo optimizaría" sin nombrar **cómo**. Sé concreto: qué estructura, qué patrón, a qué complejidad bajas.

### V3. "¿Qué es más importante, optimizar tiempo o espacio?"

**🎯 Qué evalúan:** madurez para razonar trade-offs en vez de dar absolutos.
**🗝️ Cómo responder:** empieza con "depende", pregunta restricciones, da un ejemplo.
**✅ Respuesta modelo:** "Depende del contexto y lo importante es **nombrar el trade-off**. En memoria limitada (embebidos, móvil), el espacio manda. En la mayoría de servicios se prioriza el **tiempo** aceptando un espacio razonable —por eso usamos HashMaps, que gastan O(n) de memoria para lograr O(1)—. Antes de decidir, preguntaría cuál es el recurso escaso y el cuello de botella real."
**⚠️ Qué NO hacer:** responder con un absoluto ("siempre el tiempo"). Lo que buscan es contexto.

### V4. "¿Qué haces cuando te atoras y no se te ocurre la solución?"

**🎯 Qué evalúan:** cómo manejas la presión y si tienes estrategias de desbloqueo (muy importante: todos se atoran).
**🗝️ Cómo responder:** muestra técnicas concretas, no pánico.
**✅ Respuesta modelo:** "No me quedo callado. Primero **vuelvo al ejemplo a mano** y observo qué pasos doy yo manualmente —ahí suele estar el algoritmo—. Si sigo atorado, **escribo la fuerza bruta** aunque sea lenta, para tener algo y partir de ahí. Pienso en voz alta qué **patrón** podría aplicar y por qué. Y no dudo en **decir mi razonamiento al entrevistador**: muchas veces una pista pequeña me destraba, y mostrar cómo pienso es justo lo que evalúan."
**⚠️ Qué NO hacer:** congelarte en silencio o rendirte. El proceso visible vale más que la respuesta perfecta.

### V5. "¿Cómo decides qué estructura de datos usar?"

**🎯 Qué evalúan:** que conectes las operaciones que el problema necesita con la estructura que las hace baratas.
**🗝️ Cómo responder:** parte de "¿qué operación domina?".
**✅ Respuesta modelo:** "Me pregunto **qué operación voy a hacer más** y la elijo por ahí. ¿Búsqueda rápida por clave o '¿ya vi esto?' → **HashMap/HashSet** (O(1)). ¿Acceso por índice y recorrido → **arreglo**. ¿Insertar/borrar mucho en extremos → **lista enlazada**. ¿Siempre el mínimo/máximo → **heap**. ¿Datos ordenados con búsqueda → **árbol/TreeMap**. ¿Último primero (anidamiento) → **pila**; ¿primero primero (orden de llegada) → **cola**. La estructura correcta a menudo *es* la solución."
**⚠️ Qué NO hacer:** elegir por costumbre sin justificar. Conecta operación → estructura.

### V6. "¿Qué preguntas harías antes de empezar a programar?"

**🎯 Qué evalúan:** que no asumas; aclarar requisitos es una señal de seniority (y muy de QA).
**🗝️ Cómo responder:** enumera categorías de preguntas.
**✅ Respuesta modelo:** "Aclararía: el **rango y tipo de la entrada** (¿puede venir vacía?, ¿negativos?, ¿duplicados?, ¿ya ordenada?), qué hacer en **casos sin respuesta** (¿devuelvo -1, null, excepción?), el **tamaño esperado** (¿miles o millones? eso decide si O(n²) es aceptable), y si hay **restricciones** de memoria o de no usar ciertas librerías. Confirmaría también con un ejemplo que entendí bien la salida esperada."
**⚠️ Qué NO hacer:** asumir en silencio. Las suposiciones no dichas son la causa #1 de soluciones equivocadas.

### V7. "Háblame mientras resuelves" / pensar en voz alta

**🎯 Qué evalúan:** comunicación bajo presión y colaboración — cómo serías de trabajar contigo.
**🗝️ Cómo responder:** narra **intención antes que sintaxis**.
**✅ Respuesta modelo:** "Voy narrando el **porqué**, no leyendo el código: 'voy a usar un HashMap para recordar lo que ya vi y así evitar el bucle anidado'. Anuncio mi plan antes de escribirlo, marco mis supuestos, y si cambio de idea lo digo. Trato al entrevistador como un colega con quien razono el problema."
**⚠️ Qué NO hacer:** programar en silencio, o narrar la sintaxis ('pongo un for, abro llave') en vez de la **intención**.

### V8. "Acabas de escribir esta función. ¿Cómo la probarías?" (puente con tu perfil QA ⭐)

**🎯 Qué evalúan:** mentalidad de calidad — y aquí tu fondo de **SDET es una ventaja directa** sobre un dev promedio.
**🗝️ Cómo responder:** enumera categorías de casos de prueba de forma sistemática.
**✅ Respuesta modelo:** "Probaría por categorías: el **caso normal** (entrada típica), los **casos borde** (entrada vacía, un solo elemento, el máximo tamaño esperado), **valores especiales** (negativos, ceros, duplicados, ya ordenado o en orden inverso), y los **casos sin solución** (que devuelva el valor correcto, no una excepción). Como vengo de QA, pienso en romper mi propio código: ¿qué entrada inesperada lo haría fallar? Mencionar esto demuestra mentalidad de testing."
**⚠️ Qué NO hacer:** decir "probaría con un par de ejemplos". Sé sistemático: normal, bordes, especiales, sin-solución.

### V9. "¿Cómo determinas la complejidad de tu propia solución?"

**🎯 Qué evalúan:** que sepas **analizar** lo que escribiste, no solo escribirlo.
**🗝️ Cómo responder:** cuenta bucles y costos de operaciones.
**✅ Respuesta modelo:** "Miro la estructura: bucles **separados se suman**, **anidados se multiplican**. Reviso el costo de cada operación interna (un `get` de HashMap es O(1), un `contains` de lista es O(n)). Para el **espacio**, cuento la memoria extra que creo, **incluyendo la pila de recursión**. Luego simplifico: tiro constantes y términos menores, me quedo con el dominante. Y reporto el **peor caso** como garantía."
**⚠️ Qué NO hacer:** decir un Big-O 'a ojo' sin justificarlo. Explica de dónde sale.

### V10. "Cuéntame de una vez que optimizaste algo / un reto técnico." (conductual técnica)

**🎯 Qué evalúan:** que sepas comunicar impacto y razonamiento, no solo código.
**🗝️ Cómo responder:** usa la estructura **situación → problema → qué hiciste → resultado**.
**✅ Respuesta modelo:** ancla en algo real tuyo (p. ej. una suite de pruebas lenta, una consulta costosa, un proceso O(n²) en datos crecientes), explica el cuello de botella que identificaste, la estructura/algoritmo con que lo resolviste, y el resultado medible ("de X a Y", "de minutos a segundos"). Conecta con conceptos de este manual cuando aplique.
**⚠️ Qué NO hacer:** divagar sin estructura ni resultado. Sé concreto y mide el impacto.

> 📌 **Nota de alcance:** las preguntas puramente de **teoría de QA/testing** (pirámide de pruebas, manual vs automatización, qué automatizar, tests flaky, estrategias de cobertura) son muy relevantes para tu rol, pero pertenecen a un **manual de testing/QA aparte**, no a este de algoritmos y estructuras. Si quieres, puedo construir ese manual de preparación de entrevistas SDET (testing + automatización + Playwright/Selenium) con este mismo nivel de detalle, como documento hermano.
---
---

# PARTE 5 — HOJAS DE REFERENCIA RÁPIDA

**Costos de operaciones por estructura:**

| Estructura | Acceso | Buscar | Insertar | Borrar |
|---|---|---|---|---|
| Arreglo | O(1) | O(n) | O(n) | O(n) |
| HashMap/HashSet | — | O(1)* | O(1)* | O(1)* |
| Pila / Cola | — | — | O(1) | O(1) |
| Lista enlazada | O(n) | O(n) | O(1)† | O(1)† |
| BST balanceado | O(log n) | O(log n) | O(log n) | O(log n) |
| Heap | — | — | O(log n) | O(log n) |

(*promedio · †en extremo conocido)

**Señales → patrón:**

| Si el problema dice… | Piensa en… |
|---|---|
| "par / duplicado / complemento / contar" | Hashing (Map/Set) |
| "ordenado" + "par/objetivo", "palíndromo", "invertir" | Dos punteros |
| "subarreglo/substring contiguo más largo/corto" | Ventana deslizante |
| "ordenado" + "buscar", "minimiza valor factible" | Búsqueda binaria |
| "todas las combinaciones/permutaciones/caminos" | Backtracking |
| "árbol", "profundidad", "camino" | DFS (recursión) |
| "nivel por nivel", "más corto sin pesos" | BFS (cola) |
| "islas", "conexiones", "dependencias" | Grafos (BFS/DFS + visitados) |
| "balanceado", "siguiente mayor" | Pila |
| "rangos", "reuniones", "fusionar" | Intervalos (ordenar por inicio) |
| "K más grandes/frecuentes" | Heap (Top-K) |
| "óptimo secuencial", "¿de cuántas formas?" | DP (memoización) |

**Recursión — checklist:** ¿caso base definido? ¿el caso recursivo se acerca al base? ¿qué devuelve cada nivel?

**Big-O — calcular en 30 s:** bucles anidados multiplican, separados suman · partir a la mitad = log n · tira constantes · quédate con el término dominante.

---


# PARTE 6 — RECURSOS DE REFERENCIA POR TEMA

> Materiales gratuitos y reputados para profundizar cada tema de este manual. Prioriza **visualizar** (VisuAlgo) y **practicar por patrón** (NeetCode) — es lo que más acelera el aprendizaje de algoritmos.

## Plataformas para practicar (las que de verdad importan)

- **NeetCode** — `neetcode.io`. La lista **NeetCode 150** organiza los problemas **por patrón**, justo como este manual. Cada problema tiene video-explicación. **Tu recurso #1 de práctica.**
- **LeetCode** — `leetcode.com`. El banco de problemas estándar de la industria. Filtra por *tag* (Two Pointers, Sliding Window…) y por empresa. Usa "LeetCode Explore" para rutas guiadas.
- **HackerRank** — `hackerrank.com`. Más enfocado a ejercicios prácticos y assessments tipo empresa.

## Visualizadores (para *ver* cómo funcionan)

- **VisuAlgo** — `visualgo.net`. Anima estructuras y algoritmos paso a paso (arreglos, hash, árboles, heaps, grafos, ordenamientos, búsqueda binaria). **Insuperable para "entender por dentro".**
- **Big-O Cheat Sheet** — `bigocheatsheet.com`. Tabla visual de complejidades de todas las estructuras y ordenamientos.

## Big-O y fundamentos

- **Big-O Cheat Sheet** (arriba).
- **MIT OpenCourseWare 6.006 — Introduction to Algorithms** — `ocw.mit.edu`. Universitario serio; gratis.
- **"Grokking Algorithms"** (Aditya Bhargava) — el libro más amigable y visual para principiantes. Si un solo libro, este.

## Estructuras de datos

- **VisuAlgo** (arriba) — sección por estructura.
- **William Fiset (YouTube)** — serie "Data Structures" — explicaciones excelentes de listas, pilas, colas, heaps, hash, árboles balanceados.
- **GeeksforGeeks** — `geeksforgeeks.org`. Referencia enciclopédica por estructura (úsalo para consultar, no como curso lineal).
- **Baeldung** — `baeldung.com` — para detalles específicos de Java (Collections, HashMap interno, etc.).

## Algoritmos y patrones

- **NeetCode** (arriba) — por patrón.
- **"Grokking the Coding Interview: Patterns for Coding Questions"** — el material que popularizó el enfoque por patrones (dos punteros, ventana deslizante, etc.).
- **Abdul Bari (YouTube)** — algoritmos clásicos con intuición visual (recursión, DP, grafos).

## Grafos (que requieren más apoyo)

- **William Fiset (YouTube) — "Graph Theory"** — la mejor serie gratuita de grafos (BFS, DFS, Dijkstra, topológico).

## Recursión y DP (lo más difícil)

- **"Grokking Algorithms"** — capítulos de recursión y DP, los más digeribles.
- **NeetCode — "1-D Dynamic Programming"** — empieza por aquí antes de DP en 2-D.

## Java para entrevistas

- **Baeldung** y la **documentación oficial de Java** (`docs.oracle.com`) para Collections, Streams y detalles de `HashMap`/`equals`/`hashCode`.

> 🔑 **Cómo usar estos recursos sin perder el tiempo:** este manual es tu **columna vertebral** (qué estudiar y en qué orden). Usa VisuAlgo cuando algo "no lo veas" mentalmente, NeetCode para **practicar el patrón** que acabas de leer aquí, y los libros/videos solo para reforzar un tema específico que se resista. No saltes de recurso en recurso: manual → visualiza → practica 3–5 problemas del patrón → siguiente.

---
# Registro de elaboración

| Versión | Fecha | Cambios |
|---|---|---|
| 7.6 | 2026-06-19 | **Apéndice metodológico.** Añadida la sección final **APÉNDICE — Cómo se construyó este manual**: filosofía (isla desierta, honestidad sobre inflación, profundidad no negociable, lo básico primero), marco pedagógico (plantilla suprema por tema, plantilla tutor del banco, sistema de marcadores, interrelación), voz/estilo, arquitectura, método iterativo (calibrar muestra, entregas, auditorías estrictas, bucle con el dueño, registro), pipeline técnico (splice, no romper referencias), checklist de calidad para seguir editando, y un **playbook de 11 pasos + anti-patrones** para que futuros agentes construyan manuales así sobre otros temas. Añadido al índice. |
| 7.5 | 2026-06-19 | **Capítulo 0 Java COMPLETO a profundidad máxima.** Añadida **0.15 Lambdas y Streams** (hueco detectado): el problema de pasar comportamiento, lambdas y su sintaxis, interfaces funcionales (Predicate/Function/Consumer/Supplier/Comparator) con programa, referencias a métodos (::), streams como tubería (fuente→intermedias→terminal), filter/map/reduce/collect/sorted/distinct con ejemplos y salida, streams vs bucles, uso en SDET (esperas, procesar WebElements), 7 ejercicios. Índice y nota de cierre actualizados. **Con esto las 16 secciones del Capítulo 0 (0.0-0.15) están a profundidad máxima, con programas completos y 4-7 ejercicios resueltos cada una.** |
| 7.4 | 2026-06-19 | **Profundización cap. 0: 0.12 y 0.13.** **0.12 Genéricos** a fondo: seguridad de tipos con programa, por qué Integer no int, **clase genérica propia Caja<T> y Par<K,V>**, métodos genéricos, **límites <T extends Comparable<T>>**, comodines (? extends/super), type erasure, 6 ejercicios. **0.13 Esenciales** a fondo: static (con programa, qué puede y no un método static), **enums con atributos/métodos/constructor (Planeta)**, **equals/hashCode con demostración en HashSet**, inmutabilidad y final (los 3 usos), **Comparable y Comparator para ordenar objetos propios**, paquetes/imports, 7 ejercicios. Pendiente: 0.15 lambdas/streams (nuevo) + actualizar índice. |
| 7.3 | 2026-06-19 | **Profundización cap. 0: 0.10 y 0.11.** **0.10 Excepciones** a fondo (era "unos cuantos renglones"): qué pasa sin manejo, **propagación por la pila con programa**, try/catch, múltiples catch, multi-catch, finally (corre con return) y **try-with-resources**, jerarquía Throwable con diagrama, checked vs unchecked, throw vs throws, **excepciones propias**, buenas prácticas, **catálogo de excepciones comunes**, nota SDET (screenshots/cierre), 7 ejercicios. **0.11 Colecciones** a fondo: mapa del framework, List/Set/Map cada uno con programa completo y salida, formas de recorrer, ConcurrentModificationException, tabla de elección, 6 ejercicios. Pendiente: 0.12 genéricos, 0.13 esenciales, 0.15 lambdas/streams. |
| 7.2 | 2026-06-19 | **Profundización cap. 0: 0.8 y 0.9 (las marcadas como flojas).** **0.8 Los 4 pilares** a fondo, cada pilar con programa completo y salida: encapsulación (CuentaBancaria con private/getters/setters/validación, tabla de modificadores), herencia (Animal->Perro con super), polimorfismo (arreglo de Animal, dynamic dispatch, tabla override vs overload), abstracción, encapsulación vs abstracción, 6 ejercicios. **0.9 Interfaces y clases abstractas** muy extendida: el problema que resuelven; interfaz como contrato con programa (Figura/Circulo/Rectangulo), métodos abstractos/constantes/default (Java 8)/static; clase abstracta con estado/constructor/métodos abstractos y concretos (Empleado->PorHora/Asalariado); tabla comparativa completa; combinarlas (extends + implements); WebDriver/BasePage como ejemplo SDET; 7 ejercicios de codificar. Pendiente: 0.10 excepciones a fondo, 0.11-0.13, lambdas/streams. |
| 7.1 | 2026-06-19 | **Profundización cap. 0: 0.6 y 0.7.** **0.6 Métodos** a fondo: anatomía, void, parámetros vs argumentos, return temprano, sobrecarga con programa, scope, **paso por valor (primitivos) y el matiz con objetos/arreglos** ambos con programa, **varargs**, **recursión con factorial y traza** (puente al Patrón 5), nota SDET, 7 ejercicios. **0.7 Clases y objetos** a fondo: POO, clase vs objeto con diagrama, atributos, **new/constructor/this/constructores múltiples**, métodos de instancia, **toString()**, **static vs instancia con programa (contador)**, POM, 6 ejercicios de codificar (crea una clase…) resueltos. Pendiente: 0.8-0.14 + lambdas/streams. |
| 7.0 | 2026-06-19 | **Profundización cap. 0: 0.4 y 0.5.** **0.4 Operadores** a fondo: aritméticos con programa y trampa de división entera, usos del módulo, asignación compuesta, comparación, lógicos con **corto-circuito demostrado**, incremento/decremento pre vs post con programa, ternario, **operadores a nivel de bits (con el truco del XOR para el número único y los desplazamientos)**, tabla de precedencia, 7 ejercicios. **0.5 Control de flujo** a fondo: if/else, switch clásico y **switch con flecha (Java 14+)**, for/while/do-while/for-each cada uno con programa y salida, break/continue, **bucles anidados → O(n²)**, conexión explícita con Big-O (bucle=O(n), /2=O(log n)), 7 ejercicios de codificar resueltos. Pendiente: 0.6-0.14 + lambdas/streams. |
| 6.9 | 2026-06-19 | **Profundización cap. 0: 0.2 y 0.3.** **0.2 Tu primer programa** a fondo: Hola mundo palabra por palabra, ciclo compilar/ejecutar, println/print/printf y secuencias de escape, **lectura de entrada con Scanner** (programas interactivos), comentarios, **cómo leer errores del compilador** (para desatorarse offline), 6 ejercicios resueltos. **0.3 Variables y tipos** a fondo: declaración, los 8 primitivos con tamaños/rangos y **overflow** demostrado, tipos de referencia con el modelo de memoria stack/heap y programa que muestra copia de valor vs de referencia, defaults e inicialización obligatoria de locales, final, var, casting widening/narrowing con truncamiento, **autoboxing y la trampa del caché de Integer (==)**, promoción de tipos, 7 ejercicios resueltos. Pendiente: 0.4-0.14 + lambdas/streams. |
| 6.8 | 2026-06-19 | **Reescritura profunda del cap. 0 (inicio) — máxima profundidad.** Tras auditoría estricta del usuario, se profundiza TODO el Capítulo 0 sección por sección, con varios programas completos + su salida y 4-6 ejercicios resueltos cada una. Esta entrega: **0.0 ¿Qué es Java?** (compilado+interpretado, los 6 rasgos cada uno con programa, dónde se usa, versiones LTS, ejercicios) y **0.1 La plataforma** ampliada a fondo: viaje del código, bytecode con javap, JVM/JRE/JDK, **cómo ejecuta la JVM (class loader, verifier, interpreter, JIT/HotSpot)**, **memoria JVM (heap vs stack, qué vive dónde)** y **EL GARBAGE COLLECTOR a fondo** (alcanzabilidad/GC roots, generaciones young/old, minor/major GC, stop-the-world, System.gc() es sugerencia, fugas por referencias olvidadas, finalize obsoleto), con ejercicios. Pendiente: profundizar 0.2-0.14 + añadir lambdas/streams. |
| 6.7 | 2026-06-19 | **Capítulo 0 Java COMPLETO.** Añadidas las dos últimas secciones a nivel supremo: **0.13 Esenciales** (static a fondo, enums, equals/hashCode y la regla de oro, inmutabilidad y final, paquetes/imports) y **0.14 Java aplicado a frameworks de prueba** (JUnit/TestNG, anotaciones /, aserciones, Page Object Model como POO en acción, WebDriver como interfaz, RestAssured, y una tabla que mapea CADA concepto de Java a su uso en automatización SDET). Con esto el Capítulo 0 (0.0 a 0.14) queda terminado: el manual ya enseña Java desde cero antes de Big-O. Índice actualizado. |
| 6.6 | 2026-06-19 | **Capítulo 0 Java, entrega 4.** A nivel supremo: **0.10 Excepciones** (qué son, try/catch/finally, jerarquía Throwable, checked vs unchecked, throw vs throws, excepciones propias, y excepciones típicas de Selenium/aserciones), **0.11 Colecciones** (mapa del framework List/Set/Map/Queue, sintaxis de ArrayList/HashSet/HashMap, recorridos, puente explícito a la Parte 2) y **0.12 Genéricos** (qué son, seguridad de tipos, por qué List<Integer> y no List<int>, genéricos propios con T). Pendiente: 0.13 esenciales (static, enums, equals/hashCode, inmutabilidad), 0.14 Java aplicado a frameworks de prueba SDET. |
| 6.5 | 2026-06-19 | **Capítulo 0 Java, entrega 3 (POO).** A nivel supremo: **0.7 Clases y objetos** (qué es la POO, clase vs objeto con analogía del plano, definir clase/atributos, crear con new, constructor, this, métodos de instancia, static vs instancia, POM como POO), **0.8 Los 4 pilares** (encapsulación con private/getters/setters y modificadores de acceso; herencia con extends/super; polimorfismo con override y  vs overload; abstracción; cómo cada pilar aparece en un framework de pruebas) y **0.9 Interfaces y clases abstractas** (interfaz como contrato/implements, clase abstracta/abstract, tabla de diferencias, cuándo cada una, y WebDriver como ejemplo real de interfaz). Pendiente: 0.10 excepciones, 0.11 colecciones, 0.12 genéricos, 0.13 esenciales, 0.14 Java para SDET. |
| 6.4 | 2026-06-19 | **Capítulo 0 Java, entrega 2.** Añadidas a nivel supremo: **0.4 Operadores** (aritméticos con la trampa de la división entera, módulo, asignación, comparación, lógicos con corto-circuito, ++/--, ternario, práctica), **0.5 Estructuras de control** (if/else if/else, switch con fall-through, bucles for/while/do-while/for-each, break/continue, bucles anidados, conectando explícitamente con Big-O: bucle=O(n), dividir entre 2=O(log n), anidados=O(n²)) y **0.6 Métodos** (anatomía, parámetros vs argumentos, sobrecarga, scope, paso por valor y el matiz con objetos, y por qué importan para frameworks de prueba/POM). Pendiente: 0.7-0.9 POO y pilares, 0.10 excepciones, 0.11 colecciones, 0.12 genéricos, 0.13 esenciales, 0.14 Java para SDET. |
| 6.3 | 2026-06-19 | **Coherencia + inicio del Capítulo 0 de Java.** (1) **Índice reescrito** fiel a la estructura real (Capítulo 0 Java, split Arreglos/Strings, secciones nuevas de algoritmos con nombre, banco 4.1-4.4). (2) Parte de mentalidad renumerada a M.1-M.4 para liberar la numeración 0.x. (3) Nuevo **CAPÍTULO 0 — JAVA DESDE CERO** (la base, antes de Big-O), primera entrega a nivel supremo con numeración anidada: 0.0 ¿Qué es Java? · 0.1 La plataforma (JVM/JDK/JRE/bytecode, con diagramas) · 0.2 Tu primer programa (Hola mundo palabra por palabra, compilar/ejecutar, comentarios) · 0.3 Variables y tipos (primitivos, referencia, final, var, casting, autoboxing). Cada sección con analogías, trampas, nota SDET y práctica. Pendiente (próximas entregas): 0.4 operadores, 0.5 control, 0.6 métodos, 0.7-0.9 POO y pilares, 0.10 excepciones, 0.11 colecciones, 0.12 genéricos, 0.13 esenciales, 0.14 Java para frameworks de prueba. |
| 6.2 | 2026-06-19 | **Corrección (caps. 7-9) — auditoría COMPLETA.** Heaps (cómo se declara min/max-heap, métodos uno a uno con traza, luego internals y Top-K), Grafos (cómo se construye la lista de adyacencia en código paso a paso, agregar aristas, antes de BFS/DFS) y Tries (definir el nodo, insertar palabra paso a paso, buscar/prefijo) reescritos desde cero. Con esto los 11 capítulos de estructuras enseñan "lo básico desde cero antes de los internals". Auditoría y corrección de todo el bloque de estructuras TERMINADA. |
| 6.1 | 2026-06-19 | **Corrección (cap. 6).** Árboles reescrito desde cero: vocabulario, **cómo se define el nodo** (valor + izq/der), **cómo se construye un árbol pequeño en código** paso a paso, luego BST y por qué O(log n), desbalance, recorridos DFS/BFS con código y traza, plantilla "pide a los hijos", costos, DOM=árbol, bugs y práctica. Pendientes: caps. 7 (heaps), 8 (grafos), 9 (tries). |
| 6.0 | 2026-06-19 | **Corrección (cap. 5).** Tablas hash reescrito desde cero: cómo se declara HashMap/HashSet, los métodos uno por uno (put/get/getOrDefault/containsKey/remove; add/contains), cómo recorrer, ejemplo de conteo de frecuencias con traza, y RECIÉN después los internals (cubetas, colisiones, rehashing, peor caso), hashCode/equals, variantes, bugs y práctica. Pendientes: caps. 6 (árboles), 7 (heaps), 8 (grafos), 9 (tries). |
| 5.9 | 2026-06-19 | **Auditoría + corrección (caps. 2-4).** Auditados los 11 capítulos: el gap común era arrancar en internals/problemas saltándose "lo básico desde cero". Corregidos: **Listas enlazadas** (definir el nodo, crear la lista nodo por nodo, recorrerla paso a paso, antes de operaciones y problemas), **Pilas** (cómo se declara/crea, métodos uno por uno con ejemplo y traza, antes de los usos) y **Colas** (igual: declaración, métodos, traza FIFO). Pendientes de la misma corrección: caps. 5 (hash), 6 (árboles), 7 (heaps), 8 (grafos), 9 (tries). |
| 5.8 | 2026-06-19 | **Corrección mayor (Arreglos).** Reescrito el cap. 1 desde cero: faltaba lo básico (declaración, inicialización, operaciones paso a paso). Ahora cubre en orden: qué es, **declarar e inicializar** (3 formas, valores por defecto), acceder/modificar, recorrer (3 formas), arreglos 2D, operaciones paso a paso (buscar/insertar/borrar/invertir/copiar con código y traza), métodos de java.util.Arrays, internals O(1), **ArrayList como tema aparte** (sintaxis get/set/size/add, tabla de diferencias, O(1) amortizado), ventajas/cuándo/bugs/práctica. Y **Strings separado** (cap. 1-B): declaración, operaciones, inmutabilidad, StringBuilder, ==/equals, c-a, bugs, práctica. Inicia auditoría de "lo básico primero" en todos los capítulos. |
| 5.7 | 2026-06-19 | **Entrega 18.** Sección 4.4 (preguntas verbales/comunicación) ampliada a formato tutor (qué evalúan · cómo responder · respuesta modelo · qué NO hacer): abordar un problema nuevo, optimizar O(n²), tiempo vs espacio, qué hacer al atorarse, elegir estructura de datos, preguntas aclaratorias antes de codificar, pensar en voz alta, cómo probar tu propio código (puente con QA), analizar tu propia complejidad, y conductual técnica. Nota de alcance: la teoría de QA/testing iría en un manual hermano. **Con esto el banco de preguntas (Parte 4) queda completo: conceptuales + ~33 problemas de código + verbales, todo en formato tutor.** |
| 5.6 | 2026-06-19 | **Entrega 17.** Sección 4.3 ampliada con la tanda 2 de problemas de código en formato tutor: listas enlazadas (invertir, ciclo liebre/tortuga, fusionar ordenadas con centinela, nodo medio), pilas/colas (paréntesis válidos, min-stack, temperaturas/pila monótona), árboles (profundidad, invertir, niveles, validar BST con rango, árboles iguales), grafos (número de islas, course schedule/topológico), heaps (k-ésimo mayor, top-K frecuentes), backtracking (subconjuntos, permutaciones, combination sum con poda) y DP (escaleras, cambio de monedas, house robber). Cada uno con qué evalúan, qué necesitas saber, cómo pensarla, código y trampas. Banco de código completo (~33 problemas) cubriendo el grueso de entrevistas SDET/dev. |
| 5.5 | 2026-06-19 | **Entrega 16.** Sección 4.3 (Problemas de código por patrón) reconstruida en formato tutor — tanda 1: arreglos/strings (invertir, FizzBuzz, palíndromo, Kadane/máximo subarreglo), hashing (Two Sum, duplicados, anagramas), dos punteros (mover ceros, 3Sum), ventana deslizante (substring sin repetir, comprar/vender acción) y búsqueda binaria (clásica, mínimo en rotado). Cada uno con qué evalúan, qué necesitas saber, cómo pensarla (fuerza bruta→óptimo), código con traza y Big-O, y trampas/variantes. Pendiente tanda 2: listas, pilas, árboles, grafos, heaps, backtracking, DP. |
| 5.4 | 2026-06-19 | **Entrega 15.** Banco de preguntas reconstruido en formato "tutor privado" (cada pregunta con: qué evalúan · qué necesitas saber · cómo pensarla · respuesta detallada · trampas/follow-up). Completas a ese nivel: **4.1 Fundamentos y Big-O** (9 preguntas: explicar Big-O, simplificar, clases de complejidad, logaritmos, suma vs producto, espacio y recursión, casos mejor/peor/promedio, amortizado, tiempo vs espacio) y **4.2 Estructuras de datos conceptuales** (11 preguntas: HashMap interno, Array vs LinkedList, Stack vs Queue, inmutabilidad de String, BST, heap, recorridos de árbol, grafos/visitados, HashMap vs TreeMap, recursión/StackOverflow, hashCode/equals). Código y verbales renumerados a 4.3/4.4, pendientes de elevar a tutor. |
| 5.3 | 2026-06-19 | **Entrega 14.** Nueva sección a nivel supremo: **Algoritmos de grafos con nombre** (final de la Parte 3): **Dijkstra** (camino más corto con pesos = BFS + min-heap, relajación, código y traza, por qué falla con negativos), **orden topológico** (Kahn con grados de entrada y cola, ordena Y detecta ciclos), **Union-Find/DSU** (find/union con compresión de caminos y unión por rango, casi O(1), detección de ciclos y MST), más tabla de referencia de Bellman-Ford, Floyd-Warshall, Kruskal, Prim, A*, Tarjan, el mapa mental para elegir camino más corto, y práctica. Con esto la biblia cubre TODOS los algoritmos clásicos. |
| 5.2 | 2026-06-19 | **Entrega 13.** Elevado a nivel supremo: **Tries** (cap. 9: el problema del autocompletado, internals con mapa de hijos y esFinDePalabra, insertar/buscar/prefijo en O(L) independiente del nº de palabras, cuándo trie vs HashSet, práctica). Y nueva sección **Algoritmos clásicos con nombre — Ordenamientos** al final de la Parte 3: por qué importan, O(n²) vs O(n log n), **Merge Sort** (divide y vencerás, traza, estable, garantizado) y **Quick Sort** (particionar, traza, in place, peor caso y mitigación) con código, los O(n²) (burbuja/selección/inserción), tabla comparativa maestra (mejor/promedio/peor/espacio/estabilidad), las respuestas de entrevista y práctica. Con esto, TODAS las estructuras y los ordenamientos clásicos quedan a nivel supremo. |
| 5.1 | 2026-06-19 | **Entrega 12.** Elevados a nivel supremo los **patrones 7-12**: Recorrido de árboles (DFS/BFS, la decisión y las dos plantillas, BFS por niveles con cola.size()), Recorrido de grafos (ver el grafo oculto, los 3 pasos universales, islas), Pila monótona/siguiente mayor (la analogía de la fila, temperaturas con traza), Intervalos (ordenar por inicio, fusionar con traza, salas de reuniones), Top-K con heap (la señal K, K más frecuentes combinando hashing+heap), Prefix sum (el cuentakilómetros, consultas O(1), la variante prefix+hash para subarreglos que suman K). Cada uno con dependencias, idea, receta, ejemplo, reconocimiento y práctica. **Con esto los 13 patrones Y las 9 estructuras están a nivel supremo.** |
| 5.0 | 2026-06-19 | **Entrega 11.** Elevada a nivel supremo: **Programación dinámica** (Patrón 13, el tema más difícil): el problema (no recalcular subproblemas), los dos ingredientes (subproblemas superpuestos + subestructura óptima), la idea con la analogía de la escalera, la relación de recurrencia como pieza central, las dos formas (memoización top-down y tabulación bottom-up) con código y traza de llenado de tabla, cambio de monedas, bugs, complejidad (de exponencial a polinomial), cómo reconocerla vs backtracking, receta, una nota honesta de prioridad para SDET, y práctica con respuestas. **Con esto, los 13 patrones quedan a nivel supremo.** |
| 4.9 | 2026-06-19 | **Entrega 10.** Elevado a nivel supremo: **Backtracking** (Patrón 6): el problema (generar TODAS las posibilidades), por qué no bastan bucles anidados fijos, la analogía del laberinto con hilo, el insight "elige·explora·deshaz", el esqueleto mental universal, subconjuntos con cada línea bajo el microscopio y árbol de decisiones, permutaciones, bugs (olvidar deshaz, guardar referencia en vez de copia), complejidad exponencial (2ⁿ/n!) y poda, receta y práctica con respuestas. |
| 4.8 | 2026-06-19 | **Entrega 9.** Elevado a nivel supremo: **Grafos** (cap. 8, culminación de las estructuras): el problema (redes, dependencias), tipos (dirigido/no dirigido/ponderado), las dos representaciones (lista vs matriz de adyacencia) con trade-offs, BFS (cola) y DFS (recursión) con la regla crítica de marcar visitados y traza, por qué sin visitados hay bucle infinito, operaciones y costos O(V+E), problemas clásicos (islas, ciclo, orden topológico, camino más corto/Dijkstra), el patrón mental universal de grafos, bugs y práctica con respuestas. Con esto quedan completas TODAS las estructuras de datos a nivel supremo. |
| 4.7 | 2026-06-19 | **Entrega 8.** Elevado a nivel supremo: **Heaps / colas de prioridad** (cap. 7): el problema (sala de urgencias), min/max-heap, internals completos (árbol binario completo guardado en arreglo con aritmética de índices 2i+1/2i+2/(i-1)/2, propiedad de heap, bubble up/down con traza), cada operación con su Big-O, heapify O(n), el truco contraintuitivo de Top-K (min-heap para los K mayores y por qué), ventajas/desventajas, bugs y práctica con respuestas. |
| 4.6 | 2026-06-19 | **Entrega 7.** Elevada a nivel supremo: **Árboles** (cap. 6): el problema que resuelven (datos jerárquicos: DOM, archivos), todo el vocabulario (raíz, hoja, profundidad, altura, subárbol), BST y por qué da O(log n), el problema del desbalance y los árboles autobalanceados (AVL/rojo-negro), los tres recorridos DFS (inorden/preorden/postorden) y BFS con código y traza, el patrón "pide a los hijos y combina" (altura), operaciones y costos, ventajas/desventajas, la conexión DOM=árbol para QA, bugs y práctica con respuestas. |
| 4.5 | 2026-06-19 | **Entrega 6.** Elevada a nivel supremo: **Ventana deslizante** (Patrón 3): el problema, por qué la fuerza bruta O(n²) recalcula de más, la idea con la analogía de la ventanilla del tren, los dos tipos (fija y variable), el esqueleto mental universal, cada línea bajo el microscopio, traza completa con todas las variables, ejemplo de ventana fija con suma deslizante O(1), por qué es O(n) aunque tenga un while interno, bugs, casos borde, variantes, receta y práctica con respuestas. |
| 4.4 | 2026-06-19 | **Entrega 5.** Elevado a nivel supremo: **Recursión** (Patrón 5): el problema que resuelve (auto-similitud), caso base y recursivo, el "salto de fe recursivo", cómo funciona por dentro vía la pila de llamadas, 4 ejemplos con traza completa de la pila (factorial, suma, invertir string, Fibonacci con árbol de llamadas y por qué O(2ⁿ)), recursión vs iteración, la receta para construir soluciones recursivas, bugs y por qué, complejidad, y práctica con respuestas. Con esto queda completa toda la base lineal de estructuras + recursión. |
| 4.3 | 2026-06-19 | **Entrega 4.** Elevada a nivel supremo: **Tablas Hash** (cap. 5, la estructura clave): el problema que resuelve, internals completos (función hash → cubeta, colisiones y encadenamiento, factor de carga 0.75 y rehashing, peor caso O(n) y la mitigación con árboles de Java 8+), la regla hashCode/equals y su porqué, cada operación con traza, variantes HashMap/LinkedHashMap/TreeMap, bugs, preguntas de internals de entrevista y práctica con respuestas. |
| 4.2 | 2026-06-19 | **Entrega 3.** Elevados a nivel supremo (en orden de aprendizaje): **Pilas** (cap. 3: problema que resuelve, internals de la restricción al tope, operaciones con traza, la conexión pila=recursión/call stack, balanceo de paréntesis con traza, bugs, práctica) y **Colas** (cap. 4: FIFO, internals de los dos extremos, por qué no usar ArrayList.remove(0), Deque/ArrayDeque, la conexión cola=BFS, tabla pila vs cola, práctica). |
| 4.1 | 2026-06-19 | **Entrega 2 (orden de aprendizaje).** A petición, el trabajo ahora avanza en el orden en que aprende un estudiante (escalera de dependencias §0.4), de lo fundamental a lo complejo. Elevados a nivel supremo: **Arreglos y Strings** (cap. 1: el problema que resuelven, internals del acceso O(1), O(1) amortizado del ArrayList con traza, inmutabilidad de String, ==/equals, StringBuilder, bugs y por qué, práctica con respuestas) y **Listas enlazadas** (cap. 2: internals de punteros, operaciones con traza, invertir/ciclo/medio, bugs, práctica). |
| 4.0 | 2026-06-19 | **Inicio de la versión SUPREMA (entrega 1/N).** Tras confirmar el nivel de profundidad con la muestra de búsqueda binaria, se reescriben los patrones al máximo detalle (problema desde cero · solución obvia y por qué no basta · idea construida con analogía · algoritmo en español antes del código · cada línea bajo el microscopio · traza completa con todas las variables · segundo recorrido sin solución · bugs clásicos y por qué ocurren · complejidad derivada · todos los casos borde · variantes de entrevista · receta para construirlo · práctica con respuestas). **Listos a nivel supremo: Patrón 1 (Hashing), Patrón 2 (Dos punteros), Patrón 4 (Búsqueda binaria).** Pendientes a este nivel: patrones 3, 5–13, estructuras, Big-O y algoritmos con nombre. |
| 3.0 | 2026-06-19 | **Auditoría y profundización.** (1) Nuevo **mapa de dependencias de aprendizaje** (§0.4): la escalera de prerrequisitos de todo el manual. (2) **Parte 3 (patrones) reescrita a fondo**: framework universal "cómo atacar cualquier algoritmo" + cada uno de los 13 patrones ahora con *dependencias de aprendizaje*, *explicación simple (nivel principiante)*, *señal*, *claves para construir el algoritmo* (recetas paso a paso), *más ejemplos con traza*, *follow-ups* y *recursos/links*. (3) Nueva **Parte 6 — Recursos de referencia por tema** con links curados (NeetCode, VisuAlgo, William Fiset, Grokking, MIT OCW, Baeldung). |
| 2.0 | 2026-06-19 | Consolidación en un solo archivo: Algoritmos + Estructuras de Datos a fondo (9 estructuras con internals, operaciones, ventajas/desventajas). |
| 1.0 | 2026-06-19 | Manual inicial: Big-O desde cero, estructuras, patrones, banco de preguntas, hojas de referencia. |


---
---

# APÉNDICE — Cómo se construyó este manual (guía para futuros agentes y editores)

> **Para quién es este apéndice.** Para tres lectores: (1) un **agente de IA** o un **humano** que vaya a *seguir editando y mejorando* este manual; (2) cualquier agente que quiera **replicar este enfoque** para construir un manual igual de profundo **sobre otro tema** (otro lenguaje, otra certificación, otra disciplina); y (3) el **autor/dueño** del documento, para que el criterio con que se construyó quede explícito y no se diluya con el tiempo.
>
> No es relleno: es el **modelo de pensamiento** detrás de cada página. Si lo sigues, producirás material del mismo nivel. Si lo ignoras, el documento se degradará hacia lo genérico.

---

## A.1 La filosofía (el "porqué" antes del "cómo")

Cuatro principios gobiernan **todo**. Si en algún momento una decisión de edición los contradice, la decisión está mal.

1. **El principio de la isla desierta (autosuficiencia).** El manual se escribe como si fuera **lo único** que el estudiante tendrá para aprender el tema —impreso, sin internet, durante semanas—. Consecuencias prácticas: no se "menciona" un concepto suponiendo que el lector lo buscará después; **se enseña aquí, completo**. Los enlaces externos son un complemento "para cuando haya internet", nunca un sustituto del contenido.

2. **Honestidad sobre inflación.** No se mide la calidad por número de páginas. No se prometen garantías falsas ("con esto dominarás 100%"): el dominio real de habilidades como programar o resolver algoritmos exige **práctica con retroalimentación** (escribir y correr código), no solo leer. El manual lleva al **entendimiento sólido**; el dominio fluido requiere además practicar. Decirlo con franqueza es parte del trabajo, aunque el lector pida certeza absoluta.

3. **Profundidad no negociable: entender > memorizar.** Cada tema explica *por qué* las cosas son como son (por qué un HashMap es O(1), por qué un BST se degrada, por qué `==` falla con objetos). Las tablas de una línea, los "overviews" superficiales y los volcados de teoría sin ejemplos están **prohibidos**.

4. **Lo básico primero, desde cero absoluto.** Antes de los *internals* y los casos avanzados, se enseña lo elemental: cómo se **declara**, se **crea** y se **usa** algo, paso a paso. El error más común (y que aquí se auditó y corrigió varias veces) es arrancar en lo avanzado saltándose el escalón de abajo.

---

## A.2 El marco pedagógico (cómo se enseña cada tema)

Esto es lo replicable. Cada unidad de contenido sigue plantillas fijas.

### A.2.1 La plantilla "suprema" para enseñar un concepto técnico

El orden con que se presenta cualquier tema (estructura, patrón, concepto de Java):
1. **El problema antes de la solución** — ¿qué dolor resuelve esto? El lector debe *sentir* la necesidad antes de ver la herramienta.
2. **La solución obvia y por qué no basta** — la fuerza bruta primero, con su costo, para motivar la optimización.
3. **La idea central con una analogía cotidiana** (🏠) — anclar lo abstracto a algo del mundo real (una fila, una pila de platos, un cajero, un plano y su casa).
4. **Lo elemental: declarar → crear → usar, paso a paso** — antes de cualquier *internal*.
5. **El algoritmo/idea en español, antes del código** — la lógica primero; el código después es solo la traducción.
6. **Código completo y ejecutable, con su salida** (`// Salida:`) — nada de fragmentos sueltos cuando se puede dar un programa que corre.
7. **Traza a mano** (✍️) — recorrer un ejemplo pequeño mostrando cómo cambian las variables. Un algoritmo se entiende trazándolo una vez.
8. **Cómo funciona por dentro** (🔧) — los *internals*, ya con la base puesta.
9. **Bugs clásicos y por qué ocurren** (⚠️) — no solo "cuidado con X", sino la causa.
10. **Complejidad derivada**, no afirmada — explicar de dónde sale el Big-O.
11. **Cuándo usarlo / cuándo no**, ventajas y desventajas.
12. **Práctica con respuestas** y, para temas de programación, **ejercicios de codificar resueltos** (4–7 por sección).

### A.2.2 La plantilla "tutor" para bancos de preguntas

Cada pregunta del banco no da solo la respuesta; da el razonamiento, como un tutor al lado:
- **🎯 Qué evalúan** — el *porqué* de la pregunta; qué busca ver el entrevistador.
- **🧠 Qué necesitas saber** — los prerrequisitos, con referencia a dónde estudiarlos.
- **🗝️ Cómo pensarla** — el método para llegar a la respuesta (de la fuerza bruta a lo óptimo).
- **✅ La respuesta/solución** — a fondo, con código y traza si aplica.
- **⚠️ Trampas y follow-up** — errores comunes y la pregunta que probablemente venga después.

### A.2.3 El sistema de marcadores (notación visual consistente)

Se usan los mismos íconos en todo el documento, con significado fijo. Mantenerlos es lo que hace que se sienta **un solo autor**:

| Marcador | Significado |
|---|---|
| 🔗 | Dependencias de aprendizaje (qué dominar antes) |
| 🏠 | Analogía cotidiana |
| 🔑 | Idea clave / lo que hay que recordar |
| ⚠️ | Trampa / error común |
| ✍️ | Traza paso a paso |
| 🔧 | Cómo funciona por dentro (internals) |
| 🧪 | Nota de aplicación a SDET/pruebas |
| ✅ | Autoevaluación / cierre |

### A.2.4 La interrelación (que no se sienta como temas sueltos)

- Un **mapa de dependencias de aprendizaje** (la "escalera") al inicio ordena todo de lo fundamental a lo complejo, y cada tema declara de qué depende.
- Los temas se **cruzan explícitamente**: los bucles se conectan con Big-O; las colecciones apuntan a los capítulos de estructuras; la POO desemboca en el Page Object Model; `==` vs `.equals()` se reusa en las aserciones. El lector debe sentir que todo es **un tejido**, no una lista de artículos independientes.

---

## A.3 La voz y el estilo (cómo debe "sonar")

Para que cualquier sección nueva encaje sin parecer de otro autor:
- **Idioma:** español, cálido, directo, en segunda persona ("tú").
- **Cada término se define la primera vez** que aparece, con palabras simples.
- **Analogías de la vida diaria** para cada idea abstracta.
- **Profundidad = más conceptos, ejemplos y matices**, nunca repetición ni paja.
- **Sin condescendencia y sin humo:** se trata al lector como inteligente pero principiante; no se exagera lo que el material logra.
- **Honestidad en primera persona** cuando algo no se puede garantizar.

---

## A.4 La arquitectura del documento

- **Un solo archivo vivo** en Markdown (no fragmentos dispersos). El dueño lo reemplaza tras cada entrega y corre su propio pipeline a PDF.
- **Orden de lectura = orden de aprendizaje (de abajo hacia arriba):** Orientación/mentalidad → **Java desde cero (la base)** → Big-O → Estructuras → Patrones → Banco de preguntas → Hojas de referencia → Recursos → Registro → este Apéndice.
- **Numeración anidada** (0.0, 0.1, 0.2.1…) para ubicar cualquier subtema.
- **Una sección "viva" por fase**, más que muchos archivos fragmentados.

---

## A.5 El método de construcción iterativo (cómo se trabajó de verdad)

Esto es clave para futuros agentes: **no se construyó de un solo golpe**, y hacerlo de golpe habría producido material superficial.

1. **Calibrar el nivel con una muestra.** Antes de producir en masa, se escribió **una** muestra (la búsqueda binaria) y se validó con el dueño que ese era el nivel deseado. Recién entonces se replicó.
2. **Avanzar por entregas, una fase a la vez, profundidad sobre velocidad.** Cada entrega cubre pocas secciones, pero completas. Intentar "todo de una" reproduce justo la superficialidad que se rechaza.
3. **Construir de abajo hacia arriba** siguiendo la escalera de dependencias.
4. **Auditar de forma estricta.** Periódicamente se hizo una revisión "como pedagogo mundial" con tres preguntas: ¿se entiende leyéndolo en orden?, ¿las explicaciones son simples?, ¿el estilo es consistente (un solo autor)? Las auditorías detectaron errores reales (arrancar en *internals*, secciones demasiado breves, huecos como el garbage collector o lambdas/streams) que se corrigieron.
5. **El bucle de retroalimentación con el dueño es parte del método.** Cuando el dueño señaló que algo era superficial, no se defendió: se reescribió a fondo. La exigencia del lector es una señal, no un obstáculo.
6. **El "Registro de elaboración"** (changelog al final) documenta cada versión y qué cambió: es la memoria del proyecto y permite a cualquiera reconstruir la historia.

---

## A.6 El pipeline técnico (cómo se edita el archivo sin romperlo)

Para un agente con herramientas de archivos:
- **Localizar antes de editar:** usar `grep -n` para encontrar los límites exactos de una sección por su encabezado.
- **Integrar por *splice*:** reconstruir el archivo como `cabeza + contenido_nuevo + cola` (con `sed -n` por rangos), reemplazando solo el rango de la sección. Escribir el contenido nuevo en un archivo temporal y ensamblarlo.
- **Actualizar el Registro** en cada entrega (insertando una fila de versión nueva).
- **Verificar** con `grep` que la estructura quedó bien, y **presentar** el archivo al dueño.
- **No renumerar anclas referenciadas** sin revisar primero las referencias cruzadas (`grep` de "§X.Y", "Parte N", "cap. N"). Mover numeración sin verificar rompe enlaces internos. (Ejemplo real: la parte de mentalidad se renumeró a M.x **solo** tras confirmar que ninguna sección la referenciaba por número.)
- **El PDF** lo genera el dueño con su propio pipeline (Markdown → preprocesado en Python → `wkhtmltopdf`); el agente entrega el Markdown como fuente de verdad.

---

## A.7 Cómo seguir editándolo y mejorándolo (checklist de calidad)

Antes de dar por buena **cualquier** sección nueva o corregida, verifica:

- [ ] ¿Enseña **lo básico primero** (declarar/crear/usar paso a paso) antes de los *internals*?
- [ ] ¿Tiene **al menos un programa completo y ejecutable con su salida** (no solo fragmentos)?
- [ ] ¿Incluye **una analogía**, las **trampas con su porqué**, y la **complejidad derivada** (si aplica)?
- [ ] ¿Trae **práctica y ejercicios de codificar resueltos** (4–7)?
- [ ] ¿Usa los **marcadores** correctos y la **misma voz** que el resto?
- [ ] ¿Se **cruza** con otros temas (dependencias, referencias) en vez de quedar aislada?
- [ ] ¿Se **actualizaron el índice y el Registro**?
- [ ] ¿Se **respetaron las referencias cruzadas** (no se rompió numeración)?

**Trabajo pendiente conocido (roadmap):** aplicar a **Big-O y a las estructuras (Parte 2)** el mismo nivel de *ejercicios de codificar resueltos* que ya tiene el Capítulo 0; mantener todo verificado contra fuentes al día cuando haya internet.

---

## A.8 Playbook reutilizable: construir un manual así sobre OTRO tema

Si eres un agente que va a crear un manual de **otro** tema (p. ej. Python, SQL, redes, una certificación cloud, ciberseguridad) con esta misma calidad, sigue estos pasos. El **proceso** es independiente del tema.

**Paso 1 — Fija el principio rector.** Declara la "promesa de la isla desierta": el manual debe bastarse a sí mismo. Esto te obliga a *enseñar*, no a *mencionar*.

**Paso 2 — Dibuja la escalera de dependencias del dominio.** ¿Qué es el "Nivel 0" (los fundamentos sin los cuales nada se entiende)? ¿Qué se apoya en qué? Ordena todo el temario de abajo hacia arriba. Esto evita el error de enseñar lo avanzado antes de los cimientos.

**Paso 3 — Define la plantilla por tema y el sistema de marcadores** (puedes reusar los de A.2). Que sean **fijos** para todo el documento.

**Paso 4 — Calibra una muestra con el dueño.** Escribe **una** sección al nivel que crees correcto y valídala antes de producir en masa. Ahorra rehacer todo.

**Paso 5 — Construye de abajo hacia arriba, por entregas, profundidad primero.** Pocas secciones por entrega, pero completas. Nunca todo de golpe.

**Paso 6 — Enseña lo básico primero** en cada tema: cómo se declara/crea/usa, paso a paso, antes de los *internals*.

**Paso 7 — Incluye ejemplos completos ejecutables + su salida + trazas a mano.** El entendimiento viene de ver algo correr y de trazarlo, no de leer teoría.

**Paso 8 — Añade un banco de preguntas en formato tutor** (qué evalúan · qué saber · cómo pensarla · solución · trampas) y **ejercicios prácticos resueltos**. La práctica con solución es lo que acerca al dominio cuando no hay internet.

**Paso 9 — Mantén un solo archivo vivo, un índice fiel y un Registro de cambios.** Edita por *splice*, verifica, no rompas referencias.

**Paso 10 — Audita estrictamente** con las tres preguntas (¿se entiende en orden?, ¿es simple?, ¿un solo autor?) más el checklist de A.7. Corrige sin defenderte.

**Paso 11 — Sé honesto sobre los límites.** Ningún documento garantiza el dominio de cualquiera por sí solo; recomienda explícitamente el ciclo de práctica con retroalimentación (correr código, hacer ejercicios reales).

### A.8.1 Anti-patrones (lo que NO debes hacer)

- ❌ Medir la calidad por **número de páginas**.
- ❌ Empezar por los *internals* o lo avanzado, **saltándote lo básico**.
- ❌ Tablas de una línea, "overviews" superficiales, teoría sin ejemplos ejecutables.
- ❌ Querer entregarlo **todo de una vez** (produce superficialidad).
- ❌ Prometer **garantías de dominio** ("con esto pasas seguro").
- ❌ **Referencias hacia adelante** (usar un concepto antes de explicarlo) o depender de **enlaces externos** para lo esencial en un documento pensado para usarse sin internet.
- ❌ Romper la **numeración referenciada** sin revisar las referencias cruzadas.
- ❌ Volverte **inconsistente** en voz o marcadores (rompe la sensación de un solo autor).

> 🔑 **La idea en una frase, para que la lleves a cualquier tema:** *enseña desde cero el porqué de cada cosa, con analogías, ejemplos que corren y trazas; construye de abajo hacia arriba en un solo documento vivo; practica con solución; audita sin piedad; y sé honesto sobre lo que un manual puede y no puede lograr.* Eso es lo que hace a este manual lo que es, y es transferible a cualquier disciplina.

---
