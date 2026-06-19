# Fase 0 — Fundamentos · Guía Maestra

> Documento único de la Fase 0. Contiene el material completo de cada semana a densidad de libro de texto: conceptos con su porqué, ejemplos resueltos con la salida esperada, laboratorios paso a paso, errores comunes, retos y autoevaluación.
> Léelo con el droplet abierto al lado y ejecuta cada cosa. No memorices: entiende la analogía y practica.
> **Última actualización:** 2026-06-14 · **Estado:** Fase 0 COMPLETA — las 6 semanas de contenido y el proyecto integrador.

## Índice de la Fase 0
1. **Semana 1** — La shell y el sistema de archivos ✅
2. **Semana 2** — Usuarios, permisos y procesos ✅
3. **Semana 3** — Paquetes, servicios y logs ✅
4. **Semana 4** — SSH y acceso seguro ✅
5. **Semana 5** — Redes fundamentales ✅
6. **Semana 6** — Bash scripting y Git ✅
7. **Semanas 7–8** — Proyecto integrador ✅

Convención: lo que escribes va `así`. Un marcador `<algo>` significa "reemplaza por tu valor real" (sin los signos `<>`). Una línea que empieza con `$` o `#` en los ejemplos es el prompt; lo que sigue es el comando, y debajo viene su salida.

---
---

# Semana 1 — La shell y el sistema de archivos

## 0. Mapa de la semana

Al terminar vas a poder sentarte frente a *cualquier* servidor Linux y moverte por él como por tu casa: saber dónde estás, qué hay, cómo llegar a otro lado, y cómo ver, crear, copiar, mover y borrar cosas sin miedo. Es la habilidad más básica y, a la vez, la que más vas a usar el resto de tu vida en infraestructura. Todo lo demás —servicios, redes, contenedores— se opera desde esta misma terminal.

## 1. Qué es realmente la shell

Tu servidor tiene un **kernel**: el núcleo del sistema operativo, el programa que habla directo con el hardware (CPU, memoria, disco, red). Tú nunca le hablas al kernel directamente; sería como dar órdenes moviendo neuronas a mano. Necesitas un intermediario que traduzca tus intenciones en llamadas al kernel.

Ese intermediario es la **shell**: un programa cuyo único trabajo es mostrarte un *prompt*, esperar a que escribas una línea, interpretarla, pedirle al kernel que ejecute lo que corresponda, y mostrarte el resultado. Luego repite. A ese ciclo se le llama **REPL** (Read–Eval–Print Loop): leer, evaluar, imprimir, repetir. La shell más común en Linux se llama **Bash**, y es lo que te recibe en tu droplet.

**¿Por qué texto y no clics?** Por tres razones que agradecerás mil veces:
- **Automatización.** Una línea de texto se guarda en un archivo y se repite mil veces sin error. Un clic no. Toda la disciplina de DevOps nace de aquí.
- **Velocidad y precisión.** Con los comandos dominados vas más rápido que con el ratón, y el resultado es exacto.
- **Acceso remoto.** Tus servidores no tienen monitor. La terminal viaja por la red (SSH) sin problema; un escritorio gráfico, mucho peor.

**El prompt, descifrado.** Cuando ves:
```
root@lab-aprendizaje:~#
```
- `root` — el usuario con el que trabajas.
- `@lab-aprendizaje` — el nombre de la máquina (hostname).
- `:~` — la carpeta donde estás. El `~` significa "mi carpeta personal".
- `#` — el símbolo final. `#` indica que eres **root** (superusuario); `$` indica un usuario normal. Es una alarma visual de cuánto poder tienes: el `#` dice "cuidado, puedes romper cosas".

## 2. Anatomía de un comando

Cuando escribes una línea y presionas Enter, la shell la parte por espacios y la interpreta así:
```
comando   -opciones   argumentos
```
- El **comando** es el programa a ejecutar (`ls`, `cp`, `cat`...).
- Las **opciones** (*flags*) modifican su comportamiento. Cortas con `-` (ej. `-l`), largas con `--` (ej. `--all`).
- Los **argumentos** son los datos sobre los que actúa (un archivo, una carpeta).

Leído en voz alta, `ls -l /var/log` es: "ejecuta `ls`, en modo `-l` (formato largo con detalles), sobre la carpeta `/var/log`". Las opciones cortas se combinan: `ls -lah` = `ls -l -a -h`.

Dos detalles que importan desde hoy:

*Linux distingue mayúsculas.* `ls` ≠ `LS`; `Notas.txt` ≠ `notas.txt`.

*El código de salida.* Cada comando deja un número invisible al terminar: `0` = éxito, cualquier otro = error. Se consulta con `echo $?`. Es el cimiento sobre el que después los scripts deciden ("si lo anterior falló, haz esto"). Pruébalo:
```
$ ls /carpeta-que-no-existe
ls: cannot access '/carpeta-que-no-existe': No such file or directory
$ echo $?
2
```
El `2` confirma que `ls` falló.

## 3. El sistema de archivos de Linux

En Windows hay varias "unidades" (`C:`, `D:`). En Linux **no existe eso**: hay un único árbol, y todo cuelga de un solo punto de partida, la **raíz** `/`. Imagínalo como un árbol genealógico boca abajo: el ancestro de todos es `/`, y de ahí se ramifica todo. Hasta un disco extra aparece como una carpeta *dentro* del árbol (a eso se le llama "montar").

Ramas que pisarás seguido:

| Carpeta | Qué vive ahí |
|---|---|
| `/` | La raíz. El origen de todo. |
| `/home` | Carpetas personales de usuarios (`/home/alberto`). |
| `/root` | Carpeta personal de root (no vive en `/home`). |
| `/etc` | **Configuraciones** del sistema y servicios, en texto. Tu "panel de control". |
| `/var` | Datos que **cambian**: logs, sitios web, colas. |
| `/var/log` | Los **registros**. Cuando algo falla, aquí buscas. |
| `/tmp` | Archivos **temporales**; se borran al reiniciar. |
| `/usr` | Programas y librerías (`/usr/bin` tiene muchos comandos). |
| `/bin`, `/sbin` | Comandos esenciales del sistema. |

**"Casi todo es un archivo".** Uno de los principios más profundos de Linux. No solo tus documentos: la configuración de un servicio es un archivo de texto en `/etc`, los logs son archivos en `/var/log`, e incluso muchos dispositivos del hardware se representan como archivos en `/dev`. ¿Por qué importa? Porque **las mismas herramientas para leer y manipular archivos** (`cat`, `less`, `grep`, los editores) te sirven para casi todo el sistema. Aprendes a manejar archivos una vez, y con eso manejas el 90% de Linux.

## 4. Rutas: cómo se nombra cualquier punto del árbol

Una **ruta (path)** es la dirección de un archivo o carpeta. Dos formas:

**Ruta absoluta.** Empieza en `/` y describe el camino completo: `/home/alberto/proyectos/web/index.html`. Como una dirección postal completa: funciona estés donde estés.

**Ruta relativa.** Parte de donde estás ahora. Si ya estás en `/home/alberto`, basta `proyectos/web/index.html`. Como decir "el segundo cuarto a la derecha": depende de tu posición.

**Atajos** que usarás todo el tiempo:
- `~` → tu carpeta personal. `~/proyectos` = `/home/alberto/proyectos`.
- `.` → la carpeta actual.
- `..` → la carpeta de arriba. `cd ..` sube un nivel; `../..` sube dos.
- `-` (solo con `cd`) → la carpeta donde estabas antes (como "atrás").

Estando en `/home/alberto/proyectos`: `cd ..` → `/home/alberto`; `cd ../..` → `/home`; `cd ~` → `/home/alberto` desde donde sea.

## 5. Navegar: moverte y mirar

**`pwd`** — *print working directory*: "¿en qué carpeta estoy?".
```
$ pwd
/home/alberto
```

**`ls`** — *list*: qué hay en una carpeta. Sus opciones clave:
- `ls -l` → formato largo (permisos, dueño, tamaño, fecha).
- `ls -a` → incluye ocultos (los que empiezan con `.`).
- `ls -h` → tamaños humanos (KB, MB).
- Combinadas: `ls -lah`.

```
$ ls -lah
total 28K
drwxr-xr-x 4 alberto alberto 4.0K jun 14 10:12 .
drwxr-xr-x 3 root    root    4.0K jun 14 09:50 ..
-rw-r--r-- 1 alberto alberto  220 jun 14 09:50 .bashrc
drwxr-xr-x 2 alberto alberto 4.0K jun 14 10:12 proyectos
-rw-r--r-- 1 alberto alberto  1.2K jun 14 10:10 notas.txt
```
La línea de `notas.txt`: `-rw-r--r--` es tipo y permisos (el primer carácter `-` = archivo normal, `d` = carpeta — fíjate que `proyectos` empieza con `d`); luego dueño y grupo (`alberto alberto`), tamaño (`1.2K`), fecha y nombre. Los permisos los desmenuzas a fondo en la Semana 2.

**`cd`** — *change directory*: te mueve.
```
cd /var/log     # absoluta
cd proyectos    # relativa
cd ..           # subir
cd ~            # a casa
cd -            # a donde estaba antes
```

Extra útil: **`tree`** dibuja el árbol (instala con `sudo apt install tree`):
```
$ tree ~/proyectos
/home/alberto/proyectos
└── web
    ├── index.html
    └── estilos.css
```

## 6. Ver el contenido de archivos

**`cat`** — vuelca todo de golpe (archivos cortos).
```
$ cat /etc/os-release
PRETTY_NAME="Ubuntu 24.04 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
```

**`less`** — archivos largos, página por página. Dentro: flechas/espacio para avanzar, `/palabra` para buscar, `q` para salir.

**`head`** / **`tail`** — primeras / últimas líneas. Cruciales con logs (lo reciente está al final).
```
head -n 10 notas.txt
tail -n 20 /var/log/syslog
```

**`tail -f`** — modo "seguir": muestra las líneas nuevas en tiempo real. Con esto vigilas un servicio en vivo (Semana 3). Sales con `Ctrl+C`.
```
tail -f /var/log/nginx/access.log
```

## 7. Crear, copiar, mover y borrar

**`touch`** — crea un archivo vacío: `touch nota.txt`.

**`mkdir`** — crea carpetas; `-p` crea toda la ruta anidada:
```
mkdir -p proyecto/src/componentes
```
Recordatorio: `mkdir` crea **carpetas**, `touch` crea **archivos**. Confundirlos es un tropiezo clásico.

**`cp`** — copia (el original se queda):
```
cp nota.txt copia.txt          # archivo
cp -r carpeta/ respaldo/       # carpeta entera (-r recursivo)
cp -i nota.txt copia.txt       # -i pregunta antes de sobrescribir
```

**`mv`** — mueve **o renombra** (en Linux es la misma operación):
```
mv nota.txt documentos/        # mover
mv viejo.txt nuevo.txt         # renombrar
```

**`rm`** — borra. **La advertencia más importante de la semana:**

> En Linux **no hay papelera**. Lo que borras con `rm` desaparece para siempre, sin confirmación.

```
rm nota.txt          # un archivo
rm -r carpeta/       # carpeta y todo su contenido
rm -i nota.txt       # pregunta antes (red de seguridad)
```
`rm -rf` borra recursivo y sin preguntar. **Jamás** `rm -rf /`: borraría el sistema. Con `rm -r`, lee la ruta dos veces antes de Enter. Buen hábito: usa `rm -i` hasta que el cuidado sea automático.

## 8. Comodines (globbing)

La shell entiende símbolos que significan "cualquier cosa", para operar sobre muchos archivos a la vez:
- `*` → cualquier secuencia. `*.txt` = todo lo que termina en `.txt`.
- `?` → un solo carácter. `nota?.txt` = `nota1.txt`, no `nota10.txt`.
- `[ ]` → un carácter de un conjunto. `nota[12].txt` = `nota1.txt` o `nota2.txt`.

```
ls *.log
rm temp_*
cp *.conf respaldo/
```
La shell *expande* el comodín **antes** de ejecutar: si hay `a.log` y `b.log`, `ls *.log` se vuelve `ls a.log b.log`.

## 9. Pedir ayuda dentro de la terminal

No memorices todo; aprende a consultar (habilidad de experto):
- **`man <comando>`** — el manual completo (navega como `less`, sal con `q`). Ej. `man ls`.
- **`<comando> --help`** — ayuda rápida. Ej. `ls --help`.
- **`apropos <tema>`** — busca comandos por tema cuando no recuerdas el nombre.

Hábito de oro: cuando no sepas qué hace una opción, **no adivines** — consúltala.

## 10. Productividad: autocompletado e historial

- **Tab** — escribe parte de un comando o ruta y presiona `Tab`: la shell lo completa. Doble `Tab` muestra todas las opciones. Además de comodidad, **evita errores de tipeo** y confirma que la ruta existe.
- **Historial** — `↑`/`↓` recorre comandos previos; `history` los lista; **`Ctrl+R`** busca hacia atrás (empieza a teclear y aparece el comando viejo). Esto ahorra horas.

## 11. Laboratorio guiado

1. `pwd` y `ls -lah` — ubícate y observa los ocultos.
2. `cat /etc/os-release` — confirma Ubuntu 24.04.
3. Estructura de un jalón: `mkdir -p ~/practica/semana1/{datos,respaldo}` y `cd ~/practica/semana1`. Verifica con `tree .`.
4. Archivos: `touch a.txt b.txt notas.md servidor.log`.
5. Comodines: `ls *.txt`, luego `ls *.log`.
6. Llena y lee de tres formas:
   ```
   echo "primera linea" > notas.md
   echo "segunda linea" >> notas.md
   cat notas.md
   head -n 1 notas.md
   tail -n 1 notas.md
   ```
   (`>` escribe, `>>` añade — adelanto de redirección.)
7. Organiza: `cp a.txt datos/` y `mv b.txt datos/`. Verifica con `ls datos`.
8. Renombra: `mv notas.md notas-semana1.md`.
9. Log real: `tail -n 15 /var/log/syslog`.
10. Navegación: desde `~/practica/semana1`, prueba `cd datos`, `cd ..`, `cd -`.
11. Limpia con cuidado: `rm servidor.log`; al final `cd ~` y `rm -r ~/practica` (lee la ruta dos veces).

**Qué esperar:** los comandos que tocan archivos no imprimen nada si todo va bien (Linux es silencioso en el éxito). Si ves "No such file or directory" o "Permission denied", **léelo**: te dice qué pasó.

## 12. Errores comunes
- **"No such file or directory":** ruta inexistente o mal escrita. Usa `Tab`.
- **Borraste de más con `rm`:** no hay deshacer. De ahí `rm -i` y leer la ruta.
- **`mkdir` cuando querías `touch`** (o al revés).
- **Mayúsculas:** `cd Documentos` ≠ `documentos`.
- **Espacios:** `cd "mi carpeta"` o evita espacios con `mi-carpeta`.

## 13. Reto opcional
Juega **OverTheWire: Bandit** (`overthewire.org/wargames/bandit`) desde el nivel 0: retos reales de CLI y SSH que refuerzan justo lo de esta semana.

## 14. Autoevaluación (sin consultar la guía)
- [ ] Decir en qué carpeta estás y listar su contenido con ocultos.
- [ ] Navegar por ruta absoluta y volver por relativa.
- [ ] Explicar `.`, `..`, `~` y `-`.
- [ ] Crear estructura anidada con un solo comando.
- [ ] Crear, copiar, renombrar y mover archivos.
- [ ] Ver primeras/últimas líneas y seguir un log en vivo.
- [ ] Usar `*` sobre varios archivos.
- [ ] Borrar entendiendo el riesgo, y consultar `man`/`--help`.

---
---

# Semana 2 — Usuarios, permisos y procesos

## 0. Mapa de la semana

Linux fue diseñado desde su origen para que **muchas personas y servicios compartan una misma máquina sin pisarse ni espiarse**. Esta semana entiendes ese modelo: quién es quién (usuarios y grupos), quién puede hacer qué sobre cada archivo (permisos), y cómo ver y controlar lo que se está ejecutando (procesos). Es la base de toda la seguridad de un servidor: cuando en la Semana 4 endurezcas el acceso, o en la Fase 5 apliques "mínimo privilegio", todo descansa sobre lo de aquí.

## 1. El modelo multiusuario

En un servidor no solo hay personas: hay también **usuarios de sistema** que existen para correr servicios (por ejemplo, Nginx corre bajo un usuario llamado `www-data`). Separar usuarios sirve para dos cosas: **orden** (cada quien con sus archivos) y **seguridad** (si un servicio es comprometido, el atacante solo tiene los permisos de *ese* usuario, no de todo el sistema).

Cada usuario tiene un número único llamado **UID** (User ID), y pertenece a uno o varios **grupos**, cada uno con su **GID** (Group ID). El sistema, por dentro, razona con esos números; los nombres son para nosotros.

Toda la lista de usuarios vive en un archivo de texto: `/etc/passwd` (no guarda contraseñas pese al nombre; esas están cifradas en `/etc/shadow`). Cada línea es un usuario:
```
$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
alberto:x:1000:1000:Alberto:/home/alberto:/bin/bash
```
Leyendo la línea de `alberto`, separada por `:` —
- `alberto` — nombre de usuario.
- `x` — la contraseña va cifrada en otro archivo (`/etc/shadow`).
- `1000` — su **UID**. Dato clave: los humanos suelen empezar en 1000; los usuarios de sistema tienen UIDs bajos.
- `1000` — su **GID** principal.
- `Alberto` — comentario (nombre real).
- `/home/alberto` — su carpeta personal.
- `/bin/bash` — la shell que se le asigna al entrar. Fíjate que `www-data` tiene `/usr/sbin/nologin`: ese usuario existe para correr el servicio, **pero no puede iniciar sesión** — una medida de seguridad.

`root` siempre tiene **UID 0**. Ese número, no el nombre, es lo que el sistema reconoce como "el todopoderoso".

## 2. root y el principio de menor privilegio

**root** es el superusuario: UID 0, puede hacer absolutamente todo, incluido destruir el sistema sin preguntar. Es la llave maestra del edificio.

Por eso la regla de oro: **no trabajes como root a diario.** Operas con tu usuario normal y, cuando necesitas un permiso elevado puntual, antepones **`sudo`** al comando:
```
sudo apt install nginx
```
`sudo` hace tres cosas buenas: te presta el poder de root **solo para ese comando**, te pide *tu* contraseña (no la de root), y **deja registro** de quién usó el privilegio y para qué (auditable en los logs). Esto se llama **principio de menor privilegio**: cada quien con el mínimo poder necesario, y solo cuando lo necesita. Es uno de los pilares de la seguridad que verás en la Fase 5.

Para que un usuario pueda usar `sudo`, debe pertenecer al grupo `sudo`. Lo agregas con `usermod` (lo verás en el lab).

## 3. Anatomía de los permisos

Aquí está el corazón de la semana. Cada archivo y carpeta tiene permisos que deciden **quién puede hacer qué**. Cuando haces `ls -l`, la primera columna te lo dice todo:
```
-rwxr-x--- 1 alberto devs 2048 jun 14 10:00 script.sh
```
Esa cadena `-rwxr-x---` tiene **10 caracteres** que se leen en cuatro partes:

```
 -      rwx      r-x      ---
tipo   dueño    grupo    otros
```

- **Carácter 1 — tipo:** `-` archivo normal, `d` carpeta, `l` enlace.
- **Caracteres 2-4 — dueño:** qué puede hacer el dueño del archivo.
- **Caracteres 5-7 — grupo:** qué pueden hacer los miembros del grupo del archivo.
- **Caracteres 8-10 — otros:** qué puede hacer todo el resto del mundo.

Y dentro de cada bloque de tres, las letras significan:
- **r** (read) — leer.
- **w** (write) — modificar o borrar.
- **x** (execute) — ejecutar.
- Un `-` en lugar de la letra significa "ese permiso no está".

Así, `-rwxr-x---` se lee: "es un archivo; el dueño puede leer, escribir y ejecutar; el grupo puede leer y ejecutar; los demás no pueden nada".

**El matiz que casi todos pasan por alto: r/w/x significan algo distinto en una CARPETA.**
- **r en una carpeta** → puedes *listar* los nombres de lo que hay dentro (`ls`).
- **w en una carpeta** → puedes *crear, borrar o renombrar* archivos dentro de ella (¡aunque no seas dueño de esos archivos!).
- **x en una carpeta** → puedes *entrar* en ella (`cd`) y acceder a sus archivos.

Esto explica situaciones raras que de otro modo te volverían loco: puedes tener `r` sin `x` en una carpeta (ves los nombres pero no puedes entrar), o `x` sin `r` (puedes entrar y abrir un archivo *si sabes su nombre exacto*, pero no puedes listar). Entender esto te ahorra horas de "¿por qué no me deja?".

## 4. Cambiar permisos: `chmod`

`chmod` (*change mode*) modifica los permisos. Tiene dos formas; aprende las dos porque te las encontrarás ambas.

**Forma simbólica** (legible, ideal para cambios puntuales). Se compone de: a quién (`u`=dueño, `g`=grupo, `o`=otros, `a`=todos), una operación (`+` añadir, `-` quitar, `=` fijar exacto), y el permiso (`r`, `w`, `x`):
```
chmod u+x script.sh      # añade ejecución al dueño
chmod g-w archivo.txt    # quita escritura al grupo
chmod o= archivo.txt     # deja a "otros" sin ningún permiso
chmod a+r archivo.txt    # da lectura a todos
chmod u=rwx,g=rx,o= app  # fija todo de una vez
```

**Forma octal** (numérica, compacta, la verás en tutoriales y scripts). Cada permiso vale un número: **r=4, w=2, x=1**. Sumas dentro de cada bloque:
- `rwx` = 4+2+1 = **7**
- `r-x` = 4+0+1 = **5**
- `rw-` = 4+2+0 = **6**
- `r--` = 4+0+0 = **4**
- `---` = 0

Entonces das tres dígitos: dueño, grupo, otros.
```
chmod 755 app     # rwxr-xr-x  (típico de programas)
chmod 644 doc.txt # rw-r--r--  (típico de archivos normales)
chmod 700 secreto # rwx------  (solo el dueño, nada para nadie más)
chmod 750 script  # rwxr-x---  (dueño todo, grupo lee/ejecuta, otros nada)
```
Comprobación mental: `750` → 7=rwx (dueño), 5=r-x (grupo), 0=--- (otros). Es exactamente la cadena que vimos al inicio.

## 5. Dueño y grupo: `chown` y `chgrp`

Los permisos dependen de quién es el dueño y el grupo del archivo. Para cambiarlos:
```
sudo chown alberto archivo          # cambia el dueño
sudo chown alberto:devs archivo     # cambia dueño y grupo a la vez
sudo chgrp devs archivo             # cambia solo el grupo
sudo chown -R alberto:devs carpeta/ # -R aplica a todo lo de dentro (recursivo)
```
Necesitas `sudo` porque cambiar la propiedad de un archivo es una operación privilegiada (si no, cualquiera "regalaría" archivos para evadir permisos).

## 6. Procesos: lo que se está ejecutando

Distingue dos cosas que es fácil confundir:
- Un **programa** es un archivo en disco (la receta).
- Un **proceso** es ese programa **corriendo ahora mismo** en memoria (el platillo cocinándose). Puedes tener el mismo programa corriendo en varios procesos a la vez.

Cada proceso tiene un **PID** (Process ID), un número único como un ticket de turno, y un **PPID** (el PID del proceso "padre" que lo lanzó). Así se forma un árbol de procesos: todo desciende del primer proceso que arranca el sistema.

**Ver procesos con `ps aux`:**
```
$ ps aux | head -n 3
USER  PID %CPU %MEM    VSZ   RSS TTY STAT START TIME COMMAND
root    1  0.0  0.4 168100 11200 ?   Ss   09:50 0:01 /sbin/init
www-d 812  0.0  0.6  72000 16400 ?   S    09:52 0:00 nginx: worker process
```
Las columnas que más importan:
- **USER** — bajo qué usuario corre (clave para seguridad: nota que Nginx corre como `www-data`, no como root).
- **PID** — su identificador.
- **%CPU / %MEM** — cuánto procesador y memoria consume.
- **STAT** — su estado (`S` durmiendo a la espera, `R` ejecutándose, `Z` zombi).
- **COMMAND** — qué es.

El `| grep` (que verás más a fondo después) filtra la salida. Para buscar un proceso por nombre:
```
ps aux | grep nginx
```

**Ver procesos en vivo con `top` o `htop`.** Son monitores interactivos que se actualizan solos, ordenados por consumo. `htop` es más bonito y usable (instálalo con `sudo apt install htop`). Sales con `q`.

## 7. Señales: cómo se detiene un proceso

No "cierras" un proceso: le mandas una **señal**, un mensaje que le pide o le ordena hacer algo. Las dos que importan ahora:
- **SIGTERM (15)** — "por favor, termina ordenadamente": le da al proceso la oportunidad de guardar y cerrar bien. Es la señal por defecto.
- **SIGKILL (9)** — "muere ya, sin discutir": lo mata de inmediato, sin oportunidad de limpiar. Último recurso, porque puede dejar cosas a medias.

```
kill <PID>       # manda SIGTERM (lo educado): intenta esto primero
kill -9 <PID>    # manda SIGKILL (lo brusco): solo si lo anterior no funcionó
```
También útiles: `pkill nombre` (mata por nombre en vez de PID) y `Ctrl+C` (que es enviar SIGINT al proceso de primer plano: "interrúmpete").

## 8. Control de trabajos (foreground / background)

Cuando lanzas un comando, normalmente ocupa tu terminal hasta que termina (primer plano). A veces quieres dejarlo corriendo y seguir trabajando:
- `comando &` → lánzalo directo en **segundo plano**.
- `Ctrl+Z` → **pausa** el proceso de primer plano y te devuelve la terminal.
- `jobs` → lista los trabajos en segundo plano de esta sesión.
- `fg %1` → trae el trabajo 1 de vuelta al **primer plano**.
- `bg %1` → reanuda en **segundo plano** un trabajo pausado.

## 9. Laboratorio guiado

1. **Quién eres:** `whoami` y `id` (mira tu UID y tus grupos).
2. **Crea tu usuario no-root:** `sudo adduser practica` (pon una contraseña simple, es de lab).
3. **Dale sudo:** `sudo usermod -aG sudo practica`. Verifica: `id practica` (debe aparecer el grupo `sudo`).
4. **Cámbiate a él:** `su - practica`, confirma con `whoami`, y vuelve con `exit`.
5. **Lee la línea del nuevo usuario** en el sistema: `grep practica /etc/passwd`.
6. **Experimenta con permisos:**
   ```
   touch demo.sh
   ls -l demo.sh          # observa los permisos por defecto
   chmod 700 demo.sh
   ls -l demo.sh          # ahora debe decir -rwx------
   chmod u=rwx,go=r demo.sh
   ls -l demo.sh          # y ahora -rwxr--r--
   ```
   Lee cada cambio en voz alta antes de mirar el resultado, y comprueba si acertaste.
7. **Provoca un "permission denied":** `sudo touch /root/secreto`; intenta leerlo sin privilegios: `cat /root/secreto`. Observa el mensaje. Ahora con permiso: `sudo cat /root/secreto`.
8. **Procesos:** abre `htop` (instálalo si hace falta), obsérvalo, sal con `q`. Luego `ps aux | grep ssh` para ver el proceso de SSH.
9. **Señales (con cuidado):** lanza un proceso de prueba en segundo plano `sleep 300 &`, lístalo con `jobs` y `ps aux | grep sleep`, y termínalo educadamente: `kill <PID>`.

## 10. Errores comunes
- **`chmod 777`** da permiso total a todo el mundo: casi nunca es correcto y es una bandera roja de inseguridad. Si crees necesitarlo, casi siempre la respuesta correcta es ajustar el *dueño* con `chown`.
- **Olvidar que `x` en carpetas es "entrar":** un "permission denied" al hacer `cd` suele ser falta de `x`, no de `r`.
- **`kill -9` de entrada:** intenta primero `kill` normal; el `-9` no deja al proceso cerrar bien.
- **Editar `/etc/passwd` a mano:** usa `adduser`/`usermod`. Un error ahí puede dejar el sistema inconsistente.
- **No usar `sudo`** al cambiar dueño o permisos de archivos que no son tuyos → "Operation not permitted".

## 11. Reto opcional
Crea dos usuarios y un grupo común (`sudo groupadd equipo`, `sudo usermod -aG equipo usuario1`, etc.), crea una carpeta compartida y, jugando con `chown`, `chgrp` y `chmod`, logra que **ambos usuarios puedan escribir en ella pero nadie más pueda ni entrar**. Esto te obliga a aplicar de verdad el modelo dueño/grupo/otros.

## 12. Autoevaluación (sin consultar la guía)
- [ ] Explicar qué es un UID y por qué root es especial (UID 0).
- [ ] Leer una cadena como `rwxr-x---` e identificar qué puede hacer cada quién.
- [ ] Explicar qué significan r, w y x cuando se aplican a una **carpeta**.
- [ ] Cambiar permisos en forma simbólica y en octal, y predecir el resultado antes de verlo.
- [ ] Crear un usuario, darle sudo y entender qué hace `sudo` por dentro.
- [ ] Encontrar un proceso por nombre, ver su consumo y terminarlo con la señal correcta.
- [ ] Explicar la diferencia entre SIGTERM y SIGKILL.

---
---

# Semana 3 — Paquetes, servicios y logs

## 0. Mapa de la semana

Hasta ahora navegaste y manipulaste lo que *ya estaba* en el servidor. Esta semana aprendes a **instalar software nuevo**, a **administrar los servicios** que ese software pone a correr de fondo, y —lo más importante para tu vida real como operador— a **leer los logs** para entender qué está pasando cuando algo falla. Al final vas a instalar un servidor web de verdad, servir una página, romperlo a propósito, diagnosticar el porqué leyendo sus registros, y arreglarlo. Ese ciclo (instalar → operar → diagnosticar) es, literalmente, el día a día de un administrador de infraestructura.

## 1. Cómo se instala software en Linux

En Windows bajas un `.exe` de una página web y le das doble clic. En Linux eso es la excepción, no la regla, y por buenas razones: bajar instaladores sueltos de internet es lento, desordenado y riesgoso (¿quién te garantiza que ese `.exe` es seguro?).

En su lugar, Linux usa un **gestor de paquetes**: un sistema central que instala, actualiza y elimina software desde **repositorios** confiables. Un **repositorio** es como una tienda de apps oficial para tu servidor: un servidor curado donde viven miles de programas verificados. Un **paquete** es un programa empaquetado y listo para instalar (en Ubuntu, un archivo `.deb`).

La gran ventaja: el gestor resuelve las **dependencias** por ti. Casi todo programa necesita de otros para funcionar (librerías compartidas). Si instalas Nginx y Nginx necesita la librería X, el gestor trae también la X automáticamente. En Windows tú sufres eso ("falta tal DLL"); en Linux el gestor lo hace solo.

En Ubuntu, el gestor de alto nivel se llama **apt**. (Por debajo hay una herramienta de más bajo nivel, `dpkg`, que maneja los `.deb` uno por uno; tú casi siempre usarás `apt`, que es más inteligente.)

La lista de repositorios de los que tu servidor baja software vive en `/etc/apt/sources.list` y en la carpeta `/etc/apt/sources.list.d/`.

## 2. apt en profundidad

**La distinción que más confunde a los principiantes: `update` vs `upgrade`.**
- **`sudo apt update`** — *no instala nada*. Solo va a los repositorios y **refresca la lista** de qué software hay y en qué versión. Es como actualizar el catálogo de la tienda.
- **`sudo apt upgrade`** — **instala** las versiones nuevas de lo que ya tienes, según esa lista. Es como ir y comprar las actualizaciones.

Por eso el patrón correcto casi siempre es: primero `update` (refresca el catálogo), luego `install` o `upgrade` (actúa).

Los comandos que vas a usar:
```
sudo apt update              # refresca el catálogo (hazlo antes de instalar)
sudo apt upgrade             # actualiza todo lo instalado
sudo apt install nginx       # instala un paquete
sudo apt remove nginx        # lo desinstala PERO deja sus archivos de configuración
sudo apt purge nginx         # lo desinstala Y borra su configuración
sudo apt autoremove          # elimina dependencias huérfanas que ya nadie usa
apt search <palabra>         # busca paquetes por nombre/descripción
apt show nginx               # muestra detalles de un paquete
```
El matiz `remove` vs `purge` importa: si desinstalas con `remove` y reinstalas, te encuentras tu configuración vieja intacta (a veces útil, a veces fuente de confusión). `purge` deja todo limpio.

## 3. Servicios y demonios

Un **servicio** —también llamado **demonio** (*daemon*)— es un programa que corre **de fondo**, sin ventana, esperando para hacer su trabajo: un servidor web esperando visitas, una base de datos esperando consultas, el propio SSH esperando conexiones.

A estos programas no los abres y cierras a mano cada vez. Quieres que:
- arranquen **solos** cuando el servidor enciende,
- se mantengan corriendo,
- se **reinicien** si se caen,
- y puedas prenderlos, apagarlos y revisarlos con un comando estándar.

De gestionar todo eso se encarga el **sistema de init** del servidor, que en Ubuntu (y casi todo Linux moderno) es **systemd**.

## 4. systemd y systemctl

**systemd** es el primer proceso que arranca al encender el servidor (tiene el PID 1) y el director de orquesta de todos los servicios. A cada servicio lo describe una **unit** (unidad): un archivo `.service` que dice cómo arrancar ese programa, bajo qué usuario, qué hacer si falla, etc. Esos archivos viven en `/lib/systemd/system/` (los que trae el sistema) y `/etc/systemd/system/` (los tuyos o modificados).

Lo controlas todo con **`systemctl`**:
```
sudo systemctl start nginx      # arrancar ahora
sudo systemctl stop nginx       # detener ahora
sudo systemctl restart nginx    # reiniciar (parar y volver a arrancar)
sudo systemctl reload nginx     # recargar la config SIN cortar el servicio
sudo systemctl enable nginx     # que arranque solo al encender el servidor
sudo systemctl disable nginx    # que NO arranque solo
systemctl status nginx          # ¿está vivo y sano?
systemctl is-active nginx       # responde solo "active" o "inactive"
systemctl is-enabled nginx      # ¿arranca al boot? "enabled"/"disabled"
```

Distinción clave: **`restart` vs `reload`.** `restart` apaga y vuelve a prender (hay un instante en que el servicio no responde). `reload` le dice al servicio "vuelve a leer tu configuración" sin cortarlo — ideal en producción cuando no quieres ni un segundo de caída. No todos los servicios soportan `reload`, pero Nginx sí.

Otra distinción que confunde: **`start` vs `enable` son cosas distintas.** `start` lo prende *ahora* (pero si reinicias el servidor, no vuelve solo). `enable` hace que arranque *en cada boot* (pero no lo prende ahora mismo). Para producción casi siempre quieres **ambos**: `enable --now` hace las dos de un jalón.

> Nota: si editas a mano un archivo `.service`, debes correr `sudo systemctl daemon-reload` para que systemd relea los cambios.

## 5. Leer la salida de `systemctl status`

Este es uno de los comandos que más vas a teclear en tu vida. Aprende a leerlo:
```
$ systemctl status nginx
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; preset: enabled)
     Active: active (running) since Sun 2026-06-14 10:05:12 UTC; 3min ago
   Main PID: 1234 (nginx)
      Tasks: 2 (limit: 1131)
     Memory: 4.0M
     CGroup: /system.slice/nginx.service
             ├─1234 nginx: master process /usr/sbin/nginx
             └─1235 nginx: worker process
```
- **El punto `●`** cambia de color según el estado: verde = corriendo, rojo = falló. Es lo primero que miras.
- **Loaded:** dónde está su archivo de unidad y si está `enabled` (arranca al boot).
- **Active:** el estado real. `active (running)` es lo que quieres ver. Si dice `failed` o `inactive (dead)`, hay problema.
- **Main PID:** el proceso principal del servicio.
- Y abajo, las **últimas líneas de su log**: cuando algo falla, aquí aparece la primera pista, sin tener que ir a otro lado.

## 6. Logs: dónde el servidor te cuenta qué pasa

Cuando algo falla, **la respuesta casi siempre está en los logs**. Saber leerlos es, sin exagerar, la habilidad de diagnóstico número uno. En Ubuntu hay dos mundos de logs que conviven:

**a) El journal de systemd, con `journalctl`.** systemd captura la salida de todos los servicios en un registro central. Lo consultas así:
```
journalctl -u nginx                      # solo los logs del servicio nginx
journalctl -u nginx -f                    # seguirlos en vivo (sal con Ctrl+C)
journalctl -u nginx --since "10 min ago"  # acotar por tiempo
journalctl -u nginx -e                     # saltar directo al final (lo más reciente)
journalctl -b                              # todo desde el último arranque (boot)
journalctl -p err                          # solo mensajes de prioridad error o peor
```
La opción `-u` (unit) es la que más usarás: filtra el ruido y te deja solo lo de *ese* servicio.

**b) Archivos de texto en `/var/log`.** Muchos programas escriben además sus propios archivos:
- `/var/log/syslog` — el log general del sistema.
- `/var/log/auth.log` — autenticación: quién inició sesión, quién usó `sudo`. (Útil para seguridad.)
- `/var/log/nginx/access.log` y `/var/log/nginx/error.log` — accesos y errores de Nginx.

Los lees con las herramientas de la Semana 1:
```
sudo tail -f /var/log/nginx/access.log      # ver visitas en vivo
sudo grep "error" /var/log/nginx/error.log  # buscar errores
```

## 7. El ciclo de diagnóstico (lo más importante de la semana)

Cuando un servicio "no funciona", **no adivines**. Sigue este orden, siempre:
1. **`systemctl status <servicio>`** — ¿está corriendo? Si falló, las últimas líneas del log ya te dan la pista.
2. **`journalctl -u <servicio> -e`** — si necesitas más detalle, lee el log completo del servicio.
3. **Corrige** lo que el log indique (un error de configuración, un puerto ocupado, un permiso).
4. **`systemctl restart <servicio>`** y vuelve al paso 1 para confirmar.

Internalizar este bucle te convierte en alguien que *resuelve* en vez de alguien que reza. Es exactamente la diferencia que dijiste querer.

## 8. Laboratorio guiado

1. **Refresca e instala:** `sudo apt update` y luego `sudo apt install nginx`.
2. **Verifica el servicio:** `systemctl status nginx`. Lee el punto verde, el `active (running)` y el `Loaded ... enabled`.
3. **Velo en el navegador:** averigua la IP del droplet (`ip a` o el panel de DigitalOcean) y ábrela. Debe aparecer la página de bienvenida de Nginx. **Serviste tu primer sitio.**
4. **Personaliza la página:** edita el archivo que sirve Nginx —`sudo nano /var/www/html/index.nginx-debian.html`— cambia el texto, guarda y recarga el navegador. Verás tu cambio.
5. **Practica el control del servicio:** `sudo systemctl stop nginx` (recarga el navegador: no carga) y `sudo systemctl start nginx` (vuelve). Luego `sudo systemctl enable nginx` para que arranque al boot.
6. **Rómpelo a propósito y diagnostica** (el ejercicio clave):
   - Mete un error en la configuración: `sudo nano /etc/nginx/sites-enabled/default` y borra un `;` o una `}` para dejarla inválida.
   - **Prueba la config antes de aplicarla:** `sudo nginx -t`. Verás que reporta el error y la línea exacta. (Hábito de oro: *siempre* `nginx -t` antes de reiniciar.)
   - Intenta reiniciar: `sudo systemctl restart nginx`. Falla.
   - Diagnostica como en producción: `systemctl status nginx` y `journalctl -u nginx -e`. Lee el mensaje.
   - Arregla el `;`/`}`, vuelve a `sudo nginx -t` (ahora dice `syntax is ok`) y `sudo systemctl restart nginx`. Confirma con `status`.
7. **Lee logs reales:** `sudo tail -f /var/log/nginx/access.log` y recarga el navegador para ver las peticiones entrar (sal con `Ctrl+C`).
8. **Mira quién usó sudo:** `sudo tail -n 20 /var/log/auth.log` y reconoce tus propios comandos con `sudo`.

## 9. Errores comunes
- **Confundir `apt update` con `apt upgrade`.** El primero refresca el catálogo; el segundo instala. Si "no encuentra" un paquete recién publicado, casi siempre te faltó `apt update`.
- **Olvidar `sudo`** al instalar o gestionar servicios → "permission denied" / "are you root?".
- **Editar la config y no recargar.** Los cambios no aplican hasta que hagas `reload` o `restart`. Tocar el archivo no basta.
- **Reiniciar sin probar la config.** Con Nginx, *siempre* `nginx -t` antes de `restart`: evita tumbar el sitio con un error de sintaxis.
- **`remove` cuando querías `purge`** (o viceversa): recuerda que `remove` deja la configuración vieja.
- **Editar un `.service` y no correr `daemon-reload`:** systemd seguirá usando la versión vieja.

## 10. Reto opcional
Haz que Nginx sirva en un **puerto distinto** (por ejemplo el 8080 en vez del 80): edita su configuración, prueba con `sudo nginx -t`, recarga, y verifica de dos formas — con `curl http://localhost:8080` y viendo el puerto abierto con `sudo ss -tulpn | grep 8080`. Esto te conecta con la Semana 5 (redes y puertos).

## 11. Autoevaluación (sin consultar la guía)
- [ ] Explicar qué es un repositorio y por qué Linux instala así en vez de con `.exe`.
- [ ] Decir la diferencia exacta entre `apt update` y `apt upgrade`.
- [ ] Instalar un servicio, verificar que corre y servir una página accesible desde el navegador.
- [ ] Explicar la diferencia entre `start`/`enable` y entre `restart`/`reload`.
- [ ] Leer una salida de `systemctl status` e identificar si el servicio está sano.
- [ ] Diagnosticar por qué un servicio falló usando `status` y `journalctl`, y arreglarlo.
- [ ] Seguir en vivo el log de accesos de un servicio.

---
---

# Semana 4 — SSH y acceso seguro

## 0. Mapa de la semana

Tu servidor vive en un centro de datos a kilómetros de ti, conectado a internet, donde a cada minuto hay bots intentando entrar a máquinas ajenas. Esta semana aprendes lo más importante de la administración remota: **cómo conectarte a tu servidor de forma segura (SSH), cómo hacerlo con llaves criptográficas en vez de contraseñas, y cómo endurecer el acceso** para que esos bots no tengan ninguna oportunidad. Lo que veas aquí es la primera línea de defensa real de cualquier servidor que pongas en producción, y la base de la mentalidad de seguridad que profundizarás en la Fase 5.

## 1. Qué es SSH

**SSH** (Secure Shell) resuelve un problema concreto: necesitas darle órdenes a una máquina que no tienes enfrente, a través de una red (internet) en la que cualquiera podría estar escuchando. SSH abre entre tu computadora y el servidor un canal **cifrado**: te entrega su terminal como si la tuvieras enfrente, pero todo lo que viaja —tus comandos, tus contraseñas, los resultados— va encriptado, ilegible para cualquiera en medio.

Funciona en modelo **cliente-servidor**: en tu máquina corre el *cliente* SSH (el comando `ssh`); en el servidor corre el *servidor* SSH (un servicio llamado `sshd`, que de hecho ya administraste en la Semana 3 con systemd). El cliente inicia la conexión; el servidor la acepta si te autenticas correctamente.

Anatomía del comando:
```
ssh <usuario>@<dirección>
```
Por ejemplo `ssh alberto@164.92.85.20` significa "conéctame como el usuario `alberto` a la máquina en esa IP". La primera vez te preguntará si confías en el servidor (te muestra su huella digital); respondes `yes` y queda registrado para futuras conexiones.

## 2. Contraseña vs llave: por qué la llave gana

Hay dos formas de probarle al servidor que eres tú:

**Por contraseña.** Funciona, pero es débil. Una contraseña se puede adivinar, robar, o atacar por **fuerza bruta**: los bots prueban millones de combinaciones por hora contra servidores expuestos. Si tu contraseña es débil o se filtra, entran.

**Por llave SSH.** Mucho más segura, y de hecho más cómoda (no tecleas contraseña cada vez). Se basa en **criptografía asimétrica**, que vale la pena entender con una analogía:

Imagina un **candado abierto** del que solo tú tienes la llave física. Repartes copias del candado a quien quieras (eso es tu **llave pública**): cualquiera puede cerrar algo con tu candado, pero **solo tú**, con tu llave física (tu **llave privada**), puedes abrirlo. La llave pública y la privada son un *par* matemáticamente ligado: lo que una "cierra", solo la otra "abre".

Aplicado a SSH: pones tu **llave pública** (el candado) en el servidor. Tu **llave privada** (la llave física) nunca sale de tu computadora — es tu secreto absoluto. Al conectarte, el servidor te plantea un reto que solo alguien con la llave privada correcta puede resolver, y tú lo resuelves **sin enviar nunca la llave privada por la red**. Así demuestras tu identidad sin exponer tu secreto. Por eso es tan robusto: aunque alguien espíe toda la conexión, nunca ve nada con lo que pueda suplantarte.

## 3. Generar tu par de llaves

Esto se hace **en tu máquina** (tu Windows con Git Bash), no en el servidor:
```
$ ssh-keygen -t ed25519
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/alberto/.ssh/id_ed25519):
Enter passphrase (empty for no passphrase):
```
- `-t ed25519` elige un tipo de llave moderno y seguro (mejor que el viejo RSA). Acepta la ruta por defecto presionando Enter.
- La **passphrase** es una contraseña *opcional* que cifra tu llave privada en disco: si alguien te roba el archivo, sin la passphrase no le sirve. Recomendado ponerla.

Esto crea **dos archivos** en tu carpeta `~/.ssh`:
- **`id_ed25519`** → tu **llave privada**. Tu secreto. *Nunca* la compartas, la subas a Git, ni la copies a ningún lado.
- **`id_ed25519.pub`** → tu **llave pública**. Esta sí la repartes; es el "candado".

## 4. Instalar tu llave en el servidor

Necesitas poner tu llave **pública** en el servidor, en un archivo llamado `~/.ssh/authorized_keys` del usuario con el que entrarás. La forma fácil:
```
ssh-copy-id alberto@<ip>
```
Te pedirá la contraseña *esta última vez*, y copiará tu llave pública al lugar correcto. A partir de ahí:
```
ssh alberto@<ip>
```
…ya **no** te pide contraseña (o te pide la *passphrase* de tu llave, que es distinto: esa la valida tu máquina localmente, no viaja).

Si `ssh-copy-id` no está disponible, el método manual es: copiar el contenido de tu `id_ed25519.pub` y pegarlo como una línea nueva en `~/.ssh/authorized_keys` del servidor.

**Permisos, un detalle que rompe a muchos:** SSH es estricto con los permisos por seguridad. En el servidor, la carpeta `~/.ssh` debe ser `700` y el archivo `authorized_keys` debe ser `600`. Si están más abiertos, SSH **ignora** la llave y vuelve a pedirte contraseña, sin decirte claramente por qué. (Aquí aplicas directo lo que aprendiste en la Semana 2.)

## 5. El archivo `~/.ssh/config`: calidad de vida

Teclear `ssh alberto@164.92.85.20 -p 22 -i ~/.ssh/id_ed25519` cada vez es tedioso. Puedes definir **alias** en un archivo `~/.ssh/config` (en tu máquina):
```
Host lab
    HostName 164.92.85.20
    User alberto
    Port 22
    IdentityFile ~/.ssh/id_ed25519
```
Ahora te conectas con solo:
```
ssh lab
```
Puedes tener tantos bloques `Host` como servidores administres. Esto se vuelve indispensable cuando manejas varias máquinas (Calibeb, Estibarrel, labs).

## 6. Copiar archivos por SSH: `scp`

El mismo canal seguro sirve para mover archivos, con **`scp`** (secure copy):
```
scp archivo.txt alberto@<ip>:~/          # subir un archivo al servidor
scp alberto@<ip>:~/registro.log .         # bajar un archivo del servidor (al "." = aquí)
scp -r carpeta/ alberto@<ip>:~/           # subir una carpeta entera (-r)
```
Con el alias del `config` es aún más corto: `scp archivo.txt lab:~/`. (Para sincronizaciones grandes existe `rsync`, más eficiente; lo verás cuando haga falta.)

## 7. Endurecer el servidor (hardening)

"Endurecer" = reducir las formas en que alguien podría entrar. La configuración del servidor SSH vive en **`/etc/ssh/sshd_config`**. Las tres medidas básicas:
1. **Prohibir el login directo de root:** `PermitRootLogin no`. Así, aunque adivinen la contraseña de root, no pueden entrar como root directo; deben pasar por un usuario normal y luego `sudo` (más difícil y auditable).
2. **Deshabilitar el acceso por contraseña:** `PasswordAuthentication no`. Si solo se permite el acceso por llave, los ataques de fuerza bruta por contraseña se vuelven inútiles.
3. (Opcional) **Cambiar el puerto** de SSH del 22 a otro, o limitar quién puede entrar con `AllowUsers alberto`.

Tras editar el archivo, aplicas los cambios reiniciando el servicio:
```
sudo systemctl restart ssh
```

> **La regla de seguridad más importante de la semana — no te encierres afuera.** Antes de aplicar `PasswordAuthentication no`, confirma en **otra terminal, sin cerrar la actual**, que ya entras por llave. Si te equivocas y desactivas el único método con el que podías entrar, te quedas fuera de tu propio servidor. En tu droplet de laboratorio no es grave (siempre puedes usar la consola web de DigitalOcean para recuperarlo), pero forma desde ya el hábito correcto que te salvará en producción.

## 8. Buenas prácticas de llaves
- **La llave privada nunca sale de tu máquina.** Ni a Git, ni a un chat, ni a otro servidor. Si se filtra, quien la tenga es "tú".
- **Usa passphrase** en la llave privada, y el **agente SSH** (`ssh-agent`) para no teclearla a cada rato dentro de una sesión.
- **Una llave por persona/dispositivo**, no compartidas entre personas. Así, si una se compromete, la revocas (borras del `authorized_keys`) sin afectar a los demás.
- **`.gitignore` la carpeta `.ssh`** y cualquier llave en tus proyectos. (Enlaza con la Semana 6.)

## 9. Laboratorio guiado

1. **Genera tu par de llaves** en Git Bash: `ssh-keygen -t ed25519` (acepta la ruta, pon passphrase). Confirma que existen: `ls ~/.ssh` (verás `id_ed25519` y `id_ed25519.pub`).
2. **Mira tu llave pública** (la que sí puedes compartir): `cat ~/.ssh/id_ed25519.pub`.
3. **Instálala en el droplet:** `ssh-copy-id alberto@<ip>` (te pide la contraseña esta última vez).
4. **Conéctate sin contraseña:** `ssh alberto@<ip>`. Debe entrar directo (o pedir solo tu passphrase local).
5. **Crea el alias** `~/.ssh/config` con el bloque `Host lab` de arriba y conéctate con `ssh lab`.
6. **Prueba `scp`:** crea un archivo local `echo "hola" > prueba.txt` y súbelo: `scp prueba.txt lab:~/`. Verifica en el servidor con `ls`.
7. **Verifica permisos** en el servidor: `ls -ld ~/.ssh` (debe ser `700`) y `ls -l ~/.ssh/authorized_keys` (debe ser `600`). Ajusta con `chmod` si no.
8. **Endurece con red de seguridad:** abre una **segunda** terminal y conéctate por llave (déjala abierta). En la primera, edita `sudo nano /etc/ssh/sshd_config`, pon `PermitRootLogin no` y `PasswordAuthentication no`, guarda, y `sudo systemctl restart ssh`. Comprueba en la segunda terminal (o una tercera conexión nueva) que sigues entrando por llave. Solo entonces cierra.

## 10. Errores comunes
- **Compartir o subir la llave privada.** El error más grave. Nunca, bajo ninguna circunstancia.
- **Permisos mal en `~/.ssh`:** si la llave "no funciona" y vuelve a pedir contraseña, revisa que `.ssh` sea `700` y las llaves/`authorized_keys` `600`.
- **Encerrarte afuera** al desactivar el acceso por contraseña sin haber probado la llave en otra sesión. Siempre deja una conexión abierta como red.
- **Confundir passphrase con contraseña del servidor:** la passphrase desbloquea tu llave *localmente*; no viaja ni es la del usuario remoto.
- **Copiar la llave privada al servidor** pensando que es la pública. Solo la `.pub` va al servidor.

## 11. Reto opcional
Configura el **agente SSH** para no teclear tu passphrase en cada conexión dentro de una sesión: investiga `ssh-agent` y `ssh-add`, añádele tu llave y comprueba que puedes conectarte varias veces seguidas sin re-teclear la passphrase. Es el flujo cómodo y seguro que usan los profesionales a diario.

## 12. Autoevaluación (sin consultar la guía)
- [ ] Explicar qué problema resuelve SSH y por qué la conexión va cifrada.
- [ ] Explicar, con la analogía del candado, qué son la llave pública y la privada y por qué la privada nunca se comparte.
- [ ] Generar un par de llaves e instalar la pública en un servidor.
- [ ] Conectarte sin contraseña usando un alias de `~/.ssh/config`.
- [ ] Copiar un archivo a y desde el servidor con `scp`.
- [ ] Endurecer el SSH (sin root directo, sin contraseña) **sin** encerrarte afuera.
- [ ] Explicar por qué los permisos de `~/.ssh` importan.

---
---

# Semana 5 — Redes fundamentales

## 0. Mapa de la semana

Tus servidores no viven solos: hablan entre ellos, con bases de datos, con internet y con tus clientes. Cuando algo "no conecta", "da timeout" o "no carga", el problema casi siempre está en la red. Esta semana entiendes cómo viajan los datos —direcciones IP, subredes, DNS, puertos— y cómo proteger tu servidor con un firewall. La meta no es que memorices teoría, sino que, ante un "no carga", sepas **diagnosticar en orden** dónde está la falla en vez de adivinar. Esa es exactamente la diferencia entre un operador novato y uno competente.

## 1. Cómo viaja un dato: cliente y servidor

Casi toda la red funciona en modelo **cliente-servidor**. El **cliente** (tu navegador, el comando `ssh`, una app) hace una **petición**; el **servidor** (la máquina que aloja el sitio, la base de datos, etc.) la **responde**. Cuando abres `grupoestibarrel.com`, tu navegador es el cliente que pide la página, y el servidor de Estibarrel responde con ella.

Para que esa petición llegue a la máquina correcta y al servicio correcto, intervienen cuatro piezas que veremos una por una: la **dirección IP** (a qué máquina), el **DNS** (que traduce el nombre a esa IP), el **puerto** (a qué servicio dentro de la máquina) y el **protocolo** (en qué idioma se hablan).

## 2. Dirección IP: la dirección postal de cada máquina

Imagina internet como una ciudad gigantesca llena de casas. Para que el cartero entregue una carta, cada casa necesita una **dirección única**. En las redes, esa dirección es la **IP**: un número que identifica de forma única a cada dispositivo conectado — tu laptop, el servidor, tu celular.

Una IP (de las clásicas, versión 4) son cuatro números de 0 a 255 separados por puntos:
```
164.92.85.20
```
Cuando tu navegador entra a un sitio, en el fondo manda los datos a una IP así; el nombre es solo para humanos.

**Un detalle que importa mucho: IPs públicas vs privadas.** Algunos rangos de IP están reservados para redes *internas* (tu casa, una red privada en la nube) y **no son visibles desde internet**:
- `10.0.0.0` – `10.255.255.255`
- `172.16.0.0` – `172.31.255.255`
- `192.168.0.0` – `192.168.255.255`

Por eso tu router de casa le da a tu laptop algo como `192.168.1.50`: una dirección *privada*, válida solo dentro de tu hogar. Tu droplet, en cambio, tiene una IP **pública** (visible desde todo internet) para que la gente pueda llegar a tu sitio. Y hay una IP especial, `127.0.0.1` (llamada **localhost**), que siempre significa "esta misma máquina": útil para probar un servicio desde el propio servidor.

## 3. Subredes y CIDR: las colonias y su tamaño

Una ciudad no es una lista plana de un millón de casas; está dividida en **colonias**. Una **subred** es exactamente eso: una "colonia" dentro de la red — un grupo de IPs que pertenecen juntas y pueden hablar entre sí directamente.

¿Para qué dividir en colonias? Por **orden** y por **seguridad**. Por ejemplo, puedes poner tus servidores de base de datos en una colonia privada (a la que internet no llega) y tu servidor web en otra colonia que sí da a la calle. Así, aunque alguien ataque la parte pública, la base de datos está aislada en otra colonia.

Ahora la pregunta clave: ¿cómo defines dónde empieza y termina una colonia, y cuántas casas le caben? Para eso existe la **notación CIDR**, que es simplemente una forma corta de escribirlo. Se ve así:
```
10.0.0.0/24
```
El número después de la diagonal (el `/24`) es la llave de todo. Te dice **qué parte de la dirección identifica a la colonia (fija) y qué parte queda libre para las casas individuales**.

Piénsalo así: una dirección IP tiene dos partes pegadas:
- La **parte de la colonia** (qué red es) — fija para todos los de la misma colonia.
- La **parte de la casa** (qué dispositivo es) — cambia con cada dispositivo.

El número CIDR dice cuánto de la dirección se "congela" para la colonia:
- En **`/24`**, se congelan los primeros tres números (`10.0.0`). Esa es la colonia. El último número queda libre para las casas: de `10.0.0.1` a `10.0.0.254`, o sea **~254 dispositivos**.
- En **`/16`**, se congelan solo los primeros dos números (`10.0`). La colonia es mucho más grande: **~65,000 dispositivos**.
- En **`/8`**, solo se congela el primer número (`10`). Colonia enorme: **millones**.

La regla para recordarlo: **mientras más chico el número después de la diagonal, más grande la colonia.** Un `/24` es una cuadra; un `/8` es media ciudad.

**Por qué te importa como DevOps:** cuando crees una red privada en la nube —una *VPC* en DigitalOcean o una *VNet* en Azure (Fase 2)— vas a tener que elegir un rango CIDR. Si eliges mal, dos redes pueden chocar (dos colonias con el mismo nombre = caos para el cartero) o se te pueden acabar las direcciones. Saber leer un `/24` te da control real sobre cómo se comunican —y cómo se aíslan— tus servidores.

## 4. DNS: el directorio que traduce nombres a números

Nadie memoriza `164.92.85.20`. Memorizamos `grupoestibarrel.com`. El **DNS** (Domain Name System) es el **directorio telefónico de internet**: traduce el nombre legible a la IP numérica.

Analogía: marcas "Mamá" en tu celular; el teléfono busca en sus contactos el número real y llama. El DNS hace eso a escala mundial: tu navegador pregunta "¿cuál es la IP de grupoestibarrel.com?", un servidor DNS responde, y la conexión ocurre. La regla que asocia un nombre con una IP se llama **registro A** (hay otros tipos, pero el A es el básico: nombre → IPv4).

*Por qué importa:* una enorme cantidad de "el sitio no carga" son en realidad problemas de DNS — un registro mal puesto, un dominio que apunta a la IP equivocada, o un cambio que aún no se ha *propagado* (el DNS se guarda en caché por el mundo y los cambios tardan en llegar a todos). Saber consultarlo con `dig` te deja diagnosticar en segundos si el problema es el nombre o la máquina.

## 5. Puertos: las ventanillas numeradas de cada máquina

Una sola máquina puede ofrecer varios servicios a la vez: una página web, un acceso SSH, una base de datos. ¿Cómo sabe a cuál diriges tu petición? Por el **puerto**: un número (de 0 a 65535) que identifica un servicio específico *dentro* de la máquina.

Analogía: si la IP es la dirección del edificio, el puerto es el número de departamento o la ventanilla. Llegas al edificio (IP) y tocas en la ventanilla correcta (puerto). Algunos puertos son convenciones universales que memorizarás:
- **22** — SSH (acceso remoto).
- **80** — HTTP (web sin cifrar).
- **443** — HTTPS (web cifrada).
- **53** — DNS. **3306** — MySQL. **5432** — PostgreSQL.

Cuando escribes una URL sin puerto, el navegador asume el estándar (80 para http, 443 para https). Puedes forzar otro con `:puerto`, como `localhost:8080`.

## 6. TCP y UDP: las dos formas de enviar datos

Cuando dos máquinas se hablan, usan reglas de transporte. Las dos principales:
- **TCP** — confiable y ordenado. Establece una conexión, confirma que cada pedazo llegó y en el orden correcto, y reenvía lo que se perdió. Como una llamada telefónica donde confirmas "¿me escuchaste? sí". Lo usa la web, el correo, SSH — casi todo lo que no puede perder datos.
- **UDP** — rápido pero sin confirmar. Dispara los datos y sigue, sin garantizar que lleguen ni en qué orden. Como gritar avisos por un altavoz: veloz, pero si alguien no oyó, ni modo. Se usa en video en vivo, llamadas o juegos, donde la velocidad importa más que la perfección.

## 7. HTTP y HTTPS: el idioma de la web

**HTTP** es el protocolo con el que tu navegador y un servidor web conversan: "dame esta página", "aquí está". El problema es que en HTTP esa conversación viaja **en texto plano**: cualquiera en medio podría leerla (contraseñas, datos de tarjeta).

**HTTPS** es lo mismo pero **cifrado**, usando un **certificado** que además prueba que el sitio es quien dice ser (no un impostor). Es el candado que ves en el navegador. Hoy es obligatorio: sin HTTPS, los navegadores marcan tu sitio como "no seguro", y eso es pérdida directa de confianza y de ventas — crítico para la tienda en línea de Estibarrel.

## 8. Firewall: el guardia en la puerta

Un **firewall** es un filtro que decide **qué tráfico puede entrar y salir** de tu servidor. Tú defines las reglas: "deja entrar al 443 (web), deja entrar al 22 (SSH), y bloquea todo lo demás".

Analogía: es el guardia en la entrada del edificio con una lista. Lo que está en la lista pasa; lo demás rebota. Reduce drásticamente tu **superficie de ataque**: si un puerto está cerrado, nadie puede ni intentar atacar el servicio detrás de él. Es una de las medidas de seguridad de mayor impacto y menor esfuerzo.

En Ubuntu se administra fácil con **ufw** (Uncomplicated Firewall):
```
sudo ufw allow 22            # permitir SSH
sudo ufw allow 80/tcp        # permitir web
sudo ufw allow 443/tcp       # permitir web cifrada
sudo ufw enable              # activar el firewall
sudo ufw status              # ver las reglas
sudo ufw allow from <ip> to any port 22   # SSH solo desde tu IP (más estricto)
```

> **El error clásico que te deja afuera:** si activas `ufw enable` **sin** haber permitido antes el puerto 22, cierras tu propia conexión SSH y te quedas fuera. **Permite el 22 ANTES de activar el firewall.** (Misma lógica de "no te encierres" de la Semana 4.)

## 9. Herramientas de diagnóstico

Cada una responde una pregunta distinta. Apréndelas como tu botiquín:

| Comando | Pregunta que responde | Ejemplo |
|---|---|---|
| `ip a` | ¿Cuál es mi IP? | `ip a` |
| `ping` | ¿Alcanzo esa máquina? ¿Está viva? | `ping -c 4 8.8.8.8` |
| `dig` | ¿A qué IP resuelve este nombre? | `dig grupoestibarrel.com +short` |
| `curl` | ¿Qué responde este servicio web? | `curl -I http://localhost` |
| `ss -tulpn` | ¿Qué puertos tengo abiertos y quién los usa? | `sudo ss -tulpn` |
| `traceroute` | ¿Por dónde viaja mi tráfico hasta el destino? | `traceroute google.com` |

Ejemplo de `curl -I` (solo los encabezados de la respuesta):
```
$ curl -I http://localhost
HTTP/1.1 200 OK
Server: nginx/1.24.0
Content-Type: text/html
```
Ese `200 OK` significa "el servicio respondió bien". Otros códigos te orientan: `404` (no encontrado), `403` (prohibido), `500` (error del servidor), o si no responde nada, el servicio podría estar caído o bloqueado por el firewall.

## 10. El árbol de diagnóstico (lo más valioso de la semana)

Cuando tu sitio "no carga", recórrelo **en este orden** y aíslas la falla rápido:
1. **¿Resuelve el DNS?** `dig <dominio> +short`. Si no devuelve la IP correcta, el problema es DNS (el nombre), no el servidor.
2. **¿Llega la red?** `ping <ip>`. Si no responde, puede ser conectividad o que la máquina esté apagada.
3. **¿Está abierto el puerto?** `sudo ss -tulpn` (en el servidor) y `sudo ufw status`. Si el servicio escucha pero el firewall lo bloquea, ahí está.
4. **¿Corre el servicio?** `systemctl status nginx` (lo de la Semana 3). Si está `failed`, el problema es el servicio, no la red.

Recorrer estos cuatro pasos convierte un "no sé por qué no funciona" en "el problema está en el paso 3". Eso es diagnosticar.

## 11. Laboratorio guiado

1. **Tu IP:** `ip a` — identifica la interfaz pública del droplet y su IP.
2. **Conectividad a internet:** `ping -c 4 8.8.8.8` (el DNS público de Google). Observa los tiempos de respuesta.
3. **Prueba tu Nginx local:** `curl -I http://localhost`. Confirma el `200 OK`.
4. **Resuelve un dominio:** `dig openai.com +short` — verás una o más IPs.
5. **Puertos abiertos:** `sudo ss -tulpn`. Identifica el 22 (ssh) y el 80 (nginx).
6. **Configura el firewall en el orden correcto:**
   - Primero SSH para no cerrarte: `sudo ufw allow 22`.
   - Web: `sudo ufw allow 80/tcp` y `sudo ufw allow 443/tcp`.
   - Activa: `sudo ufw enable` (confirma con `y`). Verifica: `sudo ufw status`.
7. **Comprueba el aislamiento:** desde tu navegador, tu sitio (puerto 80) sigue cargando; pero si tuvieras otro servicio en un puerto no permitido, quedaría bloqueado.
8. **Practica el árbol de diagnóstico:** detén Nginx (`sudo systemctl stop nginx`), intenta `curl -I http://localhost` (fallará), y recorre mentalmente los cuatro pasos hasta concluir "el servicio está caído". Reinícialo.

## 12. Errores comunes
- **Activar `ufw` sin permitir el 22 primero** → te cierra el SSH. Permite SSH *antes* de `enable`.
- **Confundir "cerrado" con "filtrado":** un puerto puede estar bloqueado por el firewall aunque el servicio sí corra. Por eso revisas ambos (`ss` y `ufw status`).
- **Caché de DNS:** un cambio de DNS puede tardar en propagarse. No siempre está "mal"; a veces solo aún no llega.
- **Olvidar el puerto en la URL** cuando un servicio no usa el estándar (ej. `localhost:8080`).
- **Asumir que "no carga" = servidor caído.** Muchas veces es DNS o firewall. De ahí el árbol de diagnóstico.

## 13. Reto opcional
Restringe el acceso SSH para que **solo tu IP** pueda conectarse al puerto 22 (`sudo ufw allow from <tu-ip> to any port 22` y elimina la regla general del 22). Comprueba que sigues entrando. Es una de las medidas que más reducen los intentos de intrusión en un servidor real.

## 14. Autoevaluación (sin consultar la guía)
- [ ] Explicar la diferencia entre una IP pública y una privada, y qué es `localhost`.
- [ ] Leer un CIDR `/24` y decir cuántas direcciones cubre y cuál es la parte fija.
- [ ] Explicar qué hace el DNS y por qué un fallo de DNS provoca "no carga".
- [ ] Decir qué puerto usan SSH, HTTP y HTTPS, y qué es un puerto.
- [ ] Diferenciar TCP de UDP y HTTP de HTTPS.
- [ ] Configurar el firewall permitiendo solo lo necesario, sin cerrarte el SSH.
- [ ] Recorrer el árbol de diagnóstico (DNS → red → puerto → servicio) ante un "no carga".

---
---

# Semana 6 — Bash scripting y Git

## 0. Mapa de la semana

Esta semana cierra los fundamentos con las dos habilidades que transforman todo lo anterior en algo *profesional*: **automatizar** (Bash) y **versionar** (Git). Hasta ahora le diste comandos a la shell uno por uno; con scripts, le enseñas secuencias que se ejecutan solas, sin errores, las veces que quieras — el corazón mismo de DevOps. Y con Git registras cada cambio de tu trabajo, trabajas en paralelo sin romper lo estable, y guardas la configuración de tu infraestructura como código. Tu fondo de QA/SDET te da ventaja aquí: la mentalidad de "automatiza lo repetitivo" ya la traes; solo cambias el lenguaje.

---

## PARTE A — Bash scripting

## 1. Qué es un script y el shebang

Un **script** es un archivo de texto con una secuencia de comandos que la shell ejecuta de corrido. Es pasar de tocar notas sueltas en un piano a escribir una partitura que se toca sola. ¿Para qué? Para automatizar lo repetitivo: un respaldo diario, un despliegue, una limpieza. Lo que hoy haces a mano en 20 pasos, un script lo hace en uno y sin equivocarse.

Todo script de Bash empieza con una línea especial, el **shebang**:
```bash
#!/bin/bash
```
Le dice al sistema "ejecuta este archivo con Bash". Luego, para poder correrlo, lo haces **ejecutable** (recuerda los permisos de la Semana 2) y lo invocas:
```
chmod +x miscript.sh
./miscript.sh
```
El `./` significa "el script que está aquí, en esta carpeta".

## 2. Variables

Una **variable** guarda un valor para reutilizarlo. Se asigna **sin espacios** alrededor del `=` (un error clásico), y se lee anteponiendo `$`:
```bash
nombre="Alberto"
echo "Hola, $nombre"        # imprime: Hola, Alberto
```
Usa **comillas dobles** al leer variables (`"$nombre"`): si el valor tiene espacios y no las pones, el script se rompe. Esta es la fuente número uno de bugs en Bash de principiante.

## 3. Sustitución de comandos

Puedes guardar la *salida* de un comando dentro de una variable con `$(...)`:
```bash
fecha=$(date +%F)           # fecha = la fecha de hoy, ej. 2026-06-14
echo "Hoy es $fecha"
```
Esto es lo que te deja construir nombres dinámicos (como `respaldo-2026-06-14.tar.gz`).

## 4. Argumentos

Un script puede recibir datos cuando lo ejecutas. Dentro del script, se leen como:
- `$1`, `$2`, … → el primer, segundo, … argumento.
- `$@` → todos los argumentos.
- `$#` → cuántos argumentos recibió.
- `$0` → el nombre del propio script.

```bash
#!/bin/bash
echo "Saludando a $1"       # si corres ./saluda.sh Ana  →  Saludando a Ana
```

## 5. Condicionales

Permiten que el script **decida**:
```bash
if [ "$1" = "hola" ]; then
    echo "Hola tú también"
elif [ -z "$1" ]; then
    echo "No me dijiste nada"
else
    echo "No entendí"
fi
```
Detalles que importan:
- Los **espacios dentro de los corchetes** `[ ... ]` son obligatorios: `[ "$a" = "$b" ]`, no `["$a"="$b"]`.
- Comparaciones **numéricas**: `-eq` (igual), `-ne` (distinto), `-lt` (menor), `-gt` (mayor).
- Comparaciones de **texto**: `=`, `!=`, `-z` (está vacío), `-n` (no está vacío).
- Pruebas de **archivos**: `-f ruta` (existe y es archivo), `-d ruta` (existe y es carpeta), `-e ruta` (existe).

## 6. Bucles

Repiten una acción:
```bash
# Para cada archivo .log de la carpeta, comprimirlo:
for archivo in *.log; do
    gzip "$archivo"
    echo "Comprimido: $archivo"
done
```
```bash
# Mientras se cumpla una condición:
contador=1
while [ $contador -le 3 ]; do
    echo "Intento $contador"
    contador=$((contador + 1))
done
```

## 7. Códigos de salida y encadenamiento

Recuerda de la Semana 1: cada comando deja un código de salida (`0` = éxito). En scripts lo usas para encadenar lógica:
```bash
mkdir -p ~/respaldos && echo "carpeta lista"     # el 2º corre solo si el 1º tuvo éxito
comando_riesgoso || echo "algo falló"            # el 2º corre solo si el 1º falló
```
Y puedes terminar tu script con un código propio: `exit 0` (todo bien) o `exit 1` (hubo un error), útil para que *otro* script o un pipeline sepa cómo te fue.

## 8. Un script real, comentado

Este es el script de respaldo que construirás en el laboratorio. Léelo línea por línea:
```bash
#!/bin/bash
# Respalda una carpeta en un .tar.gz con la fecha en el nombre.
set -e   # si cualquier comando falla, detén el script de inmediato

fecha=$(date +%F)
origen="$HOME/practica"
destino_dir="$HOME/respaldos"
destino="$destino_dir/practica-$fecha.tar.gz"

mkdir -p "$destino_dir"

if [ ! -d "$origen" ]; then
    echo "Error: la carpeta $origen no existe."
    exit 1
fi

tar -czf "$destino" "$origen"
echo "Respaldo creado: $destino"
```
Cada parte aplica algo de las semanas previas: variables, sustitución de comandos, un condicional con prueba de carpeta, manejo de error con `exit 1`, y `tar` para comprimir.

## 9. Programar tareas con cron

Un script de respaldo sirve más si corre **solo**, todos los días. Para eso existe **cron**, el programador de tareas de Linux. Editas tu tabla con `crontab -e` y agregas una línea con el formato `minuto hora día mes día-semana comando`:
```
0 2 * * * /home/alberto/respaldo.sh
```
Eso ejecuta tu respaldo todos los días a las 2:00 AM. (Los `*` significan "cualquier valor".) Aquí se cierra el círculo de la automatización: el script lo escribes una vez, y cron lo ejecuta para siempre.

---

## PARTE B — Git

## 10. El modelo mental de Git

**Git** es un sistema de **control de versiones**: registra cada cambio en tus archivos, quién lo hizo y cuándo, y te deja volver a cualquier punto anterior. Ya lo vienes usando; aquí afianzamos el modelo.

Git tiene tres "zonas" por las que pasan tus cambios:
1. **Directorio de trabajo** — tus archivos, donde editas.
2. **Área de preparación (staging)** — lo que marcas para el próximo guardado (`git add`).
3. **Repositorio** — la historia de guardados confirmados (`git commit`).

Y luego está el **remoto** (GitHub), una copia en la nube a la que subes (`push`) y de la que bajas (`pull`).

Analogía: editar es escribir un borrador; `git add` es seleccionar qué páginas quieres archivar; `git commit` es archivarlas con una nota de qué cambiaste; `git push` es mandar una copia a la caja fuerte en la nube.

## 11. El flujo de trabajo básico

```bash
git init                      # crear un repo nuevo en esta carpeta
git status                    # ¿qué cambió? ¿qué está preparado?
git add archivo.sh            # preparar un archivo (o "git add ." para todos)
git commit -m "Mensaje claro" # guardar un punto en la historia
git log --oneline             # ver el historial de commits, compacto
git diff                      # ver exactamente qué cambió respecto al último commit
```
Un buen mensaje de commit describe *qué* y *por qué*, no "cambios" a secas. Tu yo del futuro te lo agradecerá.

## 12. Ramas y merge

Una **rama (branch)** es una línea de trabajo paralela: te deja experimentar sin tocar la versión estable (`main`). Cuando tu cambio está listo, lo **unes (merge)** de vuelta.
```bash
git switch -c nueva-funcion   # crear y cambiarse a una rama nueva
# ... editas y haces commits aquí, sin afectar main ...
git switch main               # volver a la rama principal
git merge nueva-funcion       # traer los cambios de la rama a main
```
A veces, si dos ramas tocaron la misma línea, Git no sabe cuál ganar y marca un **conflicto**: en el archivo aparecen marcadores `<<<<<<<`, `=======`, `>>>>>>>`. Resolverlo es editar el archivo dejando la versión correcta, borrar los marcadores, y luego `git add` + `git commit`. No es magia: es elegir a mano qué versión queda.

## 13. `.gitignore`: lo que Git NO debe ver

Un archivo `.gitignore` lista lo que Git debe **ignorar** por completo. Aquí va lo que **nunca** debe entrar al historial:
```
*.log
.env
secretos/
respaldos/
id_ed25519
```
Esto es **seguridad crítica**: contraseñas, llaves (¡como tu llave privada SSH de la Semana 4!), tokens y archivos `.env` jamás deben subirse a Git. Una vez que un secreto entra al historial, queda ahí aunque lo borres después. La regla de oro de la Fase 5 empieza aquí: *los secretos nunca van en el código*.

## 14. Trabajar con el remoto y deshacer

```bash
git remote add origin <url>   # conectar tu repo local a uno en GitHub
git push -u origin main       # subir tu rama main al remoto
git pull                      # bajar los cambios del remoto
git restore archivo.sh        # descartar cambios no guardados de un archivo
```
(El `git pull --allow-unrelated-histories` que ya te topaste sirve justo cuando el remoto y el local empezaron por separado — exactamente tu caso al inicializar el repo de Estibarrel con un README ya creado.)

## 15. Laboratorio guiado

1. **Escribe el script de respaldo:** `nano respaldo.sh` y pega el script comentado de la sección 8.
2. **Hazlo ejecutable y córrelo:** `chmod +x respaldo.sh` y `./respaldo.sh`. Verifica con `ls ~/respaldos`.
3. **Rómpelo a propósito:** renombra temporalmente la carpeta `practica` y vuelve a correr el script: debe imprimir tu mensaje de error y salir con `exit 1`. Restáuralo.
4. **Versiónalo en Git:** en la carpeta del script, `git init`, `git add respaldo.sh`, `git commit -m "Script de respaldo con manejo de errores"`.
5. **Crea un `.gitignore`** que ignore los respaldos y cualquier secreto:
   ```
   echo -e "respaldos/\n*.log\n.env" > .gitignore
   git add .gitignore && git commit -m "Ignorar respaldos y secretos"
   ```
6. **Practica ramas:** `git switch -c mejora`, edita el script (agrega un `echo` con la hora además de la fecha), `git commit -am "Añadir hora al mensaje"`, vuelve con `git switch main` y une con `git merge mejora`.
7. **Revisa la historia:** `git log --oneline` para ver tus commits.
8. **(Opcional) Programa el respaldo:** `crontab -e` y agrega una línea para que corra diario.

## 16. Errores comunes
- **Espacios en la asignación de variables:** `nombre = "Ana"` falla; debe ser `nombre="Ana"`.
- **Variables sin comillas:** `rm $archivo` se rompe si el valor tiene espacios; usa `rm "$archivo"`.
- **Espacios faltantes en `[ ]`:** `[ "$a" = "$b" ]`, con espacios por dentro.
- **Olvidar `chmod +x`** → "permission denied" al ejecutar el script.
- **Commitear secretos:** el error más peligroso. Configura `.gitignore` *antes* de tu primer commit.
- **Mensajes de commit vacíos o inútiles** ("cambios", "fix"): describe qué y por qué.

## 17. Reto opcional
Mejora tu script de respaldo para que **reciba la carpeta a respaldar como argumento** (`./respaldo.sh /ruta/a/respaldar`) en vez de tenerla fija, valide que el argumento existe, y borre automáticamente los respaldos de más de 7 días (investiga `find ... -mtime +7 -delete`). Esto te obliga a combinar argumentos, condicionales y `find` en un script útil de verdad.

## 18. Autoevaluación (sin consultar la guía)
- [ ] Escribir un script con shebang, una variable, una sustitución de comando y un mensaje de salida, y ejecutarlo.
- [ ] Usar un condicional que verifique si una carpeta existe.
- [ ] Escribir un bucle `for` que recorra varios archivos.
- [ ] Explicar las tres zonas de Git (trabajo, staging, repositorio) y el remoto.
- [ ] Hacer el ciclo add → commit → push.
- [ ] Crear una rama, hacer un cambio y unirla a `main` (resolviendo un conflicto si aparece).
- [ ] Explicar por qué los secretos van en `.gitignore` y nunca en el historial.

---
---

# Semanas 7–8 — Proyecto integrador (el hito de la Fase 0)

## 0. Qué es esto y por qué importa

Las seis semanas anteriores fueron piezas sueltas: navegar, permisos, servicios, SSH, redes, scripting. El integrador es donde **las juntas todas** para montar, desde un servidor vacío, un sitio web seguro y operable — como lo harías en un trabajo real. No aprendes nada nuevo aquí; *demuestras* que dominas lo anterior haciéndolo sin guía, end-to-end. Esto es exactamente lo que en *Way of Work* llamamos el "hito de dominio": no es "vi los videos", es "lo hice solo y sé explicar cada decisión".

Y tiene un valor extra concreto: este proyecto terminado es algo que **cuentas en una entrevista**. "Monté y aseguré un servidor web desde cero" con detalles reales pesa mil veces más que recitar definiciones.

## 1. El objetivo

Partiendo de un droplet recién creado y vacío, debes terminar con: un servidor donde ya **no** se entra como root ni por contraseña, protegido por firewall, sirviendo un sitio web propio, con un script de respaldo versionado en Git, y **documentado** paso a paso con tus palabras.

## 2. Preparación

Crea un **droplet nuevo** (no reutilices el de práctica, para empezar de cero como en un caso real): Ubuntu 24.04 LTS, el tamaño más barato, nómbralo `proyecto-fase0`. Conéctate inicialmente por la consola web de DigitalOcean o como root por SSH.

## 3. El proyecto, etapa por etapa

Cada etapa indica de qué semana proviene, para que veas cómo todo se integra.

**Etapa 1 — Punto de partida (Semana 1).**
Conéctate, ubícate (`pwd`, `ls -lah`), confirma el sistema (`cat /etc/os-release`) y actualiza el catálogo de paquetes (`sudo apt update`).

**Etapa 2 — Usuario seguro (Semana 2).**
Crea un usuario no-root y dale sudo:
```
sudo adduser alberto
sudo usermod -aG sudo alberto
```
Verifica con `id alberto`. A partir de aquí, deja de operar como root: trabaja como `alberto` y eleva con `sudo` cuando haga falta (principio de menor privilegio).

**Etapa 3 — Acceso por llave y hardening (Semana 4).**
Desde tu máquina (Git Bash), si no tienes llave, genérala (`ssh-keygen -t ed25519`). Instálala en el servidor para el usuario `alberto`:
```
ssh-copy-id alberto@<ip>
```
Conéctate por llave (`ssh alberto@<ip>`), crea un alias en `~/.ssh/config`, y **con una segunda terminal abierta como red de seguridad**, endurece `/etc/ssh/sshd_config` (`PermitRootLogin no`, `PasswordAuthentication no`) y `sudo systemctl restart ssh`. Confirma que sigues entrando por llave antes de cerrar.

**Etapa 4 — Firewall (Semana 5).**
Protege el servidor permitiendo solo lo necesario, **en el orden correcto** (SSH primero para no encerrarte):
```
sudo ufw allow 22
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status
```

**Etapa 5 — Servidor web (Semana 3).**
Instala y habilita Nginx:
```
sudo apt install nginx
sudo systemctl enable --now nginx
systemctl status nginx
```
Confirma en el navegador que la IP pública muestra la página de Nginx.

**Etapa 6 — Tu sitio propio.**
Reemplaza la página por defecto por una tuya. Crea un `index.html` simple en `/var/www/html/` (con tu nombre, un título, lo que quieras), ajusta permisos/propiedad si hace falta (Semana 2), y recarga el navegador para verlo. Si tienes un dominio, este es el momento de apuntar su registro A a la IP (Semana 5) y, más adelante, agregar HTTPS.

**Etapa 7 — Respaldo versionado (Semana 6).**
Escribe un script que respalde tu sitio y la configuración de Nginx en un `.tar.gz` con la fecha. Hazlo ejecutable, pruébalo, e inicialízalo en Git con un `.gitignore` que excluya los respaldos y cualquier secreto. Opcionalmente, prográmalo con cron. Súbelo a un repo en GitHub.

**Etapa 8 — Documentación.**
Redacta un documento corto (en Markdown, versionado junto al script) que explique **qué hiciste y por qué** en cada etapa. Este documento es la mitad del valor del proyecto: demuestra que entiendes, no solo que copiaste comandos.

## 4. Checklist de entrega
- [ ] Droplet nuevo creado desde cero.
- [ ] Usuario no-root con sudo; root ya no se usa a diario.
- [ ] Acceso por llave SSH funcionando, con alias en `~/.ssh/config`.
- [ ] Login por contraseña y de root deshabilitados, sin haberte encerrado.
- [ ] Firewall activo permitiendo solo 22, 80 y 443.
- [ ] Nginx instalado, habilitado al boot y sirviendo.
- [ ] Sitio propio publicado y visible desde el navegador.
- [ ] Script de respaldo funcional, con manejo de error.
- [ ] Todo versionado en Git, con `.gitignore` para secretos, subido a GitHub.
- [ ] Documento que explica cada paso con tus palabras.

## 5. Criterio de "dominado"

Marcas la Fase 0 como dominada cuando puedes **repetir todo este proceso en un droplet nuevo, sin guía, y explicar cada decisión** — por qué un usuario no-root, por qué llave en vez de contraseña, por qué ese orden en el firewall, qué hace cada línea del script. Si puedes hacerlo y explicarlo, los cimientos están puestos.

## 6. Cómo se cuenta esto en una entrevista

Practica narrarlo en 60 segundos, conectándolo con tu perfil de QA/SDET: *"Monté un servidor Linux de producción desde cero — usuario con privilegios mínimos, acceso solo por llave SSH, firewall restrictivo, Nginx sirviendo un sitio, respaldos automatizados con un script versionado en Git. Apliqué la misma mentalidad de QA que uso para automatizar pruebas: reducir el error humano automatizando, y validar cada paso."* Eso es señal de competencia real, no de certificados.

## 7. Autoevaluación final de la Fase 0

Repasa el *Tracker de competencias* del documento maestro. Deberías poder marcar, sin guía:
- [ ] Navegar el sistema de archivos de Linux con soltura.
- [ ] Permisos, usuarios y procesos.
- [ ] Instalar y administrar paquetes y servicios (systemd).
- [ ] SSH y acceso seguro a servidores.
- [ ] Redes básicas: IP/CIDR, DNS, puertos, firewall.
- [ ] Scripting básico en Bash.
- [ ] Levantar un servidor desde cero y servir un sitio.

## 8. Qué sigue

Con la Fase 0 dominada, tienes el cimiento que el resto del camino da por hecho. Sigue la **Fase 1 — Contenedores y CI/CD**, donde tu mentalidad de QA empieza a brillar: empaquetar aplicaciones en Docker y automatizar sus pruebas y despliegue. Pero nada de eso se entiende sin lo que acabas de construir aquí.

---
---

> **Fase 0 COMPLETA.** Este documento cubre las 6 semanas de contenido y el proyecto integrador a densidad de libro de texto. El documento maestro se actualiza a la versión 2.1 reflejando este cierre.
