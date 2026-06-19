# Ruta Maestra · DevOps · Cloud · SRE · DevSecOps

> **Fuente de la verdad** del camino de aprendizaje de Alberto, de fundamentos a experto.
> Documento vivo: se actualiza en cada sesión de avance.

| | |
|---|---|
| **Dueño** | Alberto |
| **Mentor / asesor** | Claude |
| **Versión** | 2.1 |
| **Última actualización** | 2026-06-14 |
| **Estado general** | En marcha — Fase 0 |

---

## Estado actual (de un vistazo)

- **Fase activa:** Fase 0 — Fundamentos
- **Bloque activo:** Semana 1 — Orientación en Linux
- **Siguiente acción concreta:** Crear el droplet de laboratorio en DigitalOcean (`lab-aprendizaje`, Ubuntu 24.04 LTS, tamaño más barato) y conectarse vía consola.
- **Tiempo semanal comprometido:** 5–8 horas.

> Esta sección siempre refleja "¿dónde estoy parado hoy y qué sigue?". Es lo primero que ambos consultamos.

---

## Cómo usar este documento

1. **Big picture con sustancia.** Aquí está el *qué*, el *por qué*, una definición entendible de cada concepto, el plan semana por semana y dónde estudiarlo. No es un tutorial profundo de cada tema (eso se ve en las sesiones), pero sí una guía que se sostiene sola.
2. **Es la brújula compartida.** El mentor lo usa para dar seguimiento; Alberto lo usa para no perder la imagen general.
3. **Vive y se actualiza** según el proceso definido en *Way of Work*.
4. **El orden importa.** Las fases se construyen una sobre otra. No saltarse fundamentos: es la causa #1 por la que la gente se estanca para siempre.

### Guías detalladas (companions)

Este maestro es el *mapa*. La *profundidad* —cada concepto explicado para principiante, con ejemplos resueltos, laboratorios paso a paso y autoevaluaciones— vive en guías detalladas independientes, una por fase, más una de certificaciones:

| Guía | Estado |
|---|---|
| **Fase 0 — Fundamentos · Guía Maestra** | ✅ Completa (6 semanas + integrador) |
| **Guía Detallada de Certificaciones** | ✅ Completa |
| Fase 1 a Fase 5 · Guías detalladas | Se construyen al llegar a cada fase |

---

## Way of Work — cómo trabajamos

Esta sección define las reglas del juego entre Alberto y el mentor. Es vinculante para ambos.

### Lineamientos

1. **Fundamentos primero.** Linux, redes e identidad/permisos resuelven el 80% de los problemas reales de producción. No se avanza de fase con huecos en la anterior.
2. **Agnóstico al proveedor en el núcleo.** Las habilidades que importan transfieren entre DO, Azure, AWS y GCP. Eso se aprende primero; lo específico de cada nube, después.
3. **Aprender haciendo.** Cada concepto se aplica en un laboratorio práctico la misma semana. Nada de teoría que se queda en el cuaderno.
4. **Laboratorio ≠ producción.** Jamás se practica en servidores de clientes o proyectos reales en vivo. El aprendizaje sucio se hace en servidores desechables.
5. **La mentalidad QA es superpoder.** DevOps es la filosofía de testing aplicada a la entrega y la infraestructura. Se explota ese ángulo en cada fase.

### Ciclo de cada sesión

1. El mentor explica el siguiente paso o concepto (en porciones digeribles, no volcados gigantes).
2. Alberto ejecuta y **comparte la salida real** de su terminal o entorno.
3. Se diagnostica sobre lo real y se itera hasta que funciona y se entiende.
4. Se marca el avance y se define el siguiente paso.

### Mantenimiento de este documento (proceso de actualización)

- Este documento es la **fuente única de la verdad**. Vive en la sección *Files* del proyecto.
- **No se actualiza solo.** Al cierre de cada avance significativo, el mentor **regenera el documento completo** con las secciones *Estado actual*, *Tracker de competencias* y *Bitácora* al día, y sube la versión de número incrementado en el *Changelog*.
- Alberto **reemplaza la versión anterior** en *Files* por la nueva. Así nunca hay dos verdades.
- Cualquiera de los dos puede proponer cambios estructurales (agregar secciones, reordenar fases, ajustar alcance); se reflejan en una nueva versión.

### Definición de "dominado"

Un tema se marca como dominado en el *Tracker* solo cuando Alberto puede **hacerlo sin guía y explicarlo con sus palabras** — no cuando "lo vio en un video".

---

## North Star — ¿a dónde vamos?

Convertir a Alberto en un **profesional de infraestructura realmente competente**, capaz de:

- Administrar y operar infraestructura en producción sin depender de terceros ni de la IA para lo esencial.
- Diseñar, automatizar, monitorear y asegurar sistemas en cualquier contexto.
- Calificar para roles de **DevOps Engineer, SRE, Cloud / Infrastructure Engineer o Platform Engineer** en el mercado, incluyendo entrevistas técnicas.
- Apalancar su perfil de QA/SDET como diferenciador, no como punto de partida desde cero.

**Definición de "experto" para este camino:** no es saber más herramientas que nadie. Es entender los *fundamentos* tan bien que cualquier herramienta nueva sea solo sintaxis encima de conceptos ya dominados.

---

## Principios guía

1. **Fundamentos sobre herramientas.** Las herramientas cambian; los fundamentos no. Este es el consenso de la industria para 2026.
2. **Construir, romper, arreglar.** La confianza real viene de operar sistemas, no de coleccionar certificados.
3. **Aprendizaje estructurado y constante** le gana al esfuerzo aleatorio. Progreso lento pero sostenido.
4. **La IA es un copiloto, no una muleta.** El objetivo es entender lo suficiente para mandar tú, no para que la IA decida por ti.

---

## Contexto: el laboratorio y la portabilidad del conocimiento

El aprendizaje se ancla en práctica real. Hoy, los proyectos disponibles sirven de banco de pruebas:

| Proyecto | Qué es | Uso como laboratorio |
|---|---|---|
| **Calibeb** | Sistema tipo ERP | CI/CD, despliegues, observabilidad de una app de negocio. |
| **Grupo Estibarrel** | Web + tienda en línea + Odoo Community autoalojado | Administración de servidores, contenedores, redes, backups, seguridad. |
| **Servidor de laboratorio** | Droplet desechable en DigitalOcean | Práctica destructiva de Linux y servidores sin riesgo. |

> **Importante — no ser determinista con los proyectos.** Calibeb y Estibarrel son proyectos **temporales**. Son un *medio*, no el *fin*. El objetivo es **conocimiento portable**: todo lo aprendido debe poder aplicarse igual a proyectos propios, de clientes futuros, o a un empleo. Cuando un proyecto actual no aplique para un tema, el laboratorio desechable o un proyecto propio de práctica cumplen la misma función. La habilidad viaja contigo; los proyectos van y vienen.

---

## Estrategia de nube

| Plataforma | Rol | Por qué |
|---|---|---|
| **DigitalOcean** | Profundidad y práctica real | Ya en uso, barata, menos abstraída → enseña fundamentos sin capas mágicas de por medio. |
| **Azure** | Amplitud y señal de mercado | Certificación AZ-900 como hito + red de apoyo (amigos que lo manejan) + consola clara. Se introduce en Fase 2. |

**Regla:** el cert de Azure es para *señal/amplitud*; DO es para *profundidad/práctica*. No se migran los proyectos a Azure "para aprender Azure" — sería una distracción cara. Los fundamentos aprendidos aplican a AWS y GCP por igual.

---

# El roadmap — las 6 fases

> Cada fase: objetivo · por qué importa · conceptos clave con definición · plan semana por semana · laboratorio · hito de dominio · recursos · duración. Tiempos calculados a 5–8 h/semana desde nivel principiante.

---

## Fase 0 — Fundamentos

**Objetivo:** dominar la línea de comandos de Linux, las redes básicas y el scripting. Poder levantar y operar un servidor con confianza.

**Por qué importa:** es el cimiento de absolutamente todo. Quien se salta esto memoriza recetas sin entender, y vive pegado a Stack Overflow. Dominarlo es lo que te separa del montón.

### Conceptos clave (qué es cada cosa)

**Linux**
- **Sistema de archivos:** Linux organiza todo en una sola jerarquía que empieza en la raíz `/`. Principio mental: "en Linux, casi todo es un archivo".
- **Permisos:** cada archivo tiene un dueño, un grupo y permisos de lectura/escritura/ejecución (`rwx`) que controlan quién puede hacer qué.
- **Procesos:** cada programa en ejecución es un proceso con un identificador (PID). Aprendes a verlos, inspeccionarlos y terminarlos.
- **Usuarios y grupos:** el sistema sabe quién eres. `root` es el superusuario todopoderoso; `sudo` te da permisos elevados puntuales y auditables.
- **Paquetes:** software que instalas y actualizas con un gestor (en Ubuntu, `apt`), en vez de bajar instaladores sueltos.
- **systemd:** el sistema que arranca y supervisa los servicios (procesos de fondo, como un servidor web). Se controla con `systemctl`; los logs se leen con `journalctl`.
- **SSH:** protocolo para conectarte de forma cifrada y segura a un servidor remoto desde tu terminal.

**Redes**
- **IP / CIDR:** la dirección numérica de una máquina en la red. CIDR es la notación (ej. `10.0.0.0/24`) para definir rangos y subredes.
- **DNS:** el "directorio telefónico" de internet; traduce nombres (`grupoestibarrel.com`) a direcciones IP.
- **Puertos:** números que identifican un servicio dentro de una máquina (80 = HTTP, 443 = HTTPS, 22 = SSH).
- **Firewall:** filtro que decide qué tráfico entra y sale del servidor. En Ubuntu se administra fácil con `ufw`.
- **HTTP/HTTPS:** el protocolo de la web. HTTPS es la versión cifrada, con certificado (el candado del navegador).

**Automatización y versiones**
- **Bash scripting:** escribir secuencias de comandos en un archivo para automatizar tareas repetitivas (respaldos, despliegues), usando variables, condicionales y bucles.
- **Git:** control de versiones para registrar el historial del código, trabajar en ramas y colaborar sin pisarse.

### Plan semana por semana

- **Semana 1 — Orientación en Linux:** qué es Linux y la shell; navegar el sistema de archivos (`pwd`, `ls`, `cd`); rutas absolutas vs relativas; ver y manipular archivos y carpetas (`cat`, `less`, `touch`, `mkdir`, `cp`, `mv`, `rm`). *Lab: explorar a fondo el droplet.*
- **Semana 2 — Usuarios, permisos y procesos:** usuarios y grupos; `sudo`; permisos `rwx` con `chmod`/`chown`; procesos con `ps`, `top`, `kill`. *Lab: crear un usuario no-root y gestionar permisos de archivos.*
- **Semana 3 — Paquetes y servicios:** gestor `apt` (instalar, actualizar, eliminar); `systemd` y `systemctl`; leer logs con `journalctl`. *Lab: instalar y administrar Nginx como servicio.*
- **Semana 4 — SSH y acceso seguro:** cómo funciona SSH; llaves pública/privada vs contraseña; configurar acceso por llave; *hardening* básico (deshabilitar login de root por contraseña). *Lab: conectarte por llave SSH desde Git Bash.*
- **Semana 5 — Redes fundamentales:** modelo de capas simplificado; IP, CIDR y subredes; DNS; puertos; TCP/UDP; HTTP/HTTPS; firewall con `ufw`. Herramientas: `ping`, `curl`, `dig`, `ss`. *Lab: configurar el firewall e inspeccionar conexiones abiertas.*
- **Semana 6 — Bash + Git:** variables, condicionales, bucles y argumentos en Bash; refuerzo de Git (ramas, *merge*, conflictos, `.gitignore`). *Lab: escribir un script de respaldo y versionarlo en Git.*
- **Semanas 7–8 (buffer + proyecto integrador):** repaso de huecos y el hito.

### Hito de dominio
Levantar un servidor desde cero: crear un usuario seguro, configurar firewall y SSH por llave, instalar un servidor web y servir un sitio simple — **explicando cada paso con tus palabras**.

### Recursos recomendados
- **The Linux Command Line** (William Shotts) — libro gratuito, la referencia clásica: `linuxcommand.org/tlcl.php`
- **Linux Journey** — curso interactivo, ideal para aprender haciendo: `linuxjourney.com`
- **OverTheWire: Bandit** — juego para practicar CLI + SSH resolviendo retos: `overthewire.org/wargames/bandit`
- **MIT — The Missing Semester** — CLI, scripting y Git al estilo universitario serio: `missing.csail.mit.edu`
- **DigitalOcean Community Tutorials** — guías prácticas de servidores y redes: `digitalocean.com/community/tutorials`
- **Practical Networking** (YouTube) — para construir intuición de redes.

**Duración estimada:** 5–8 semanas · **Cert opcional:** Linux Foundation LFCA (más adelante).

---

## Fase 1 — Contenedores y CI/CD

**Objetivo:** empaquetar aplicaciones en contenedores y automatizar su prueba y entrega.

**Por qué importa:** es el corazón del DevOps moderno y donde tu fondo de QA brilla — pruebas automatizadas dentro del pipeline.

### Conceptos clave
- **Contenedor:** forma de empaquetar una app con todo lo que necesita (código, librerías, configuración) en una unidad aislada y portable. Más ligero que una máquina virtual porque comparte el kernel del host.
- **Imagen:** la "plantilla" inmutable a partir de la cual se crean los contenedores.
- **Dockerfile:** la receta que describe, paso a paso, cómo construir una imagen.
- **Volúmenes:** mecanismo para que los datos sobrevivan aunque el contenedor se destruya (persistencia).
- **Docker Compose:** herramienta para definir y levantar varios contenedores juntos (ej. app + base de datos) con un solo archivo.
- **CI/CD:** Integración Continua = cada cambio se prueba automáticamente al integrarse; Entrega/Despliegue Continuo = ese cambio se publica solo si pasa las pruebas.
- **GitHub Actions:** sistema de automatización de GitHub; defines *workflows* que corren al hacer push (pruebas, builds, despliegues).
- **Registry:** repositorio donde se guardan y distribuyen las imágenes (Docker Hub, GHCR).

### Plan semana por semana
- **Semana 1 — Docker básico:** contenedor vs VM; `docker run`, `ps`, `exec`, `logs`; ciclo de vida de un contenedor. *Lab: correr y manipular contenedores existentes.*
- **Semana 2 — Construir imágenes:** Dockerfile; capas y caché; buenas prácticas; volúmenes y redes de Docker. *Lab: contenerizar una app sencilla propia.*
- **Semana 3 — Docker Compose:** definir stacks multi-contenedor; variables de entorno. *Lab: levantar app + base de datos con un solo `compose up`.*
- **Semana 4 — CI con GitHub Actions:** workflows, jobs, steps; correr pruebas automáticas en cada push. *Lab: pipeline que ejecute la suite de pruebas.*
- **Semana 5 — CD completo:** build → test → deploy; despliegue condicionado a pruebas verdes; publicar imágenes a un registry. *Lab: despliegue automático de un componente de Calibeb.*
- **Semana 6 — Buffer + hito.**

### Hito de dominio
Un push a `main` que dispare pruebas automáticas y despliegue **solo si pasan**.

### Recursos recomendados
- **TechWorld with Nana** (YouTube) — Docker y DevOps explicados de forma excelente para principiantes.
- **Docker — Get Started** (docs oficiales): `docs.docker.com/get-started`
- **Docker Deep Dive** (Nigel Poulton) — libro de referencia.
- **GitHub Actions docs**: `docs.github.com/actions`
- **freeCodeCamp** — cursos gratuitos de Docker y CI/CD (YouTube).

**Duración estimada:** 4–6 semanas.

---

## Fase 2 — IaC y nube

**Objetivo:** definir infraestructura como código y entender la nube a nivel conceptual. Aprobar el AZ-900.

**Por qué importa:** infraestructura reproducible, versionada y sin "clics manuales" que nadie recuerda ni puede repetir.

### Conceptos clave
- **IaC (Infraestructura como Código):** definir servidores, redes y servicios en archivos de texto versionados, en lugar de crearlos a mano por la consola.
- **Terraform:** la herramienta de IaC más usada; describes el estado deseado y ella crea, modifica o destruye la infraestructura real para que coincida. Es agnóstica de proveedor.
- **Estado (state):** el archivo donde Terraform recuerda qué creó, para saber qué cambiar la próxima vez.
- **Módulos:** bloques reutilizables de Terraform para no repetir configuración (DRY).
- **IaaS / PaaS / SaaS:** modelos de nube — Infraestructura (rentas servidores), Plataforma (rentas un entorno gestionado), Software (rentas la app lista).
- **Regiones / zonas:** ubicaciones físicas de los centros de datos de la nube.
- **IAM (Identity and Access Management):** el sistema que define quién (usuarios, servicios) puede hacer qué sobre qué recursos.

### Plan semana por semana
- **Semana 1 — Conceptos de nube:** IaaS/PaaS/SaaS; regiones y zonas; cómputo, almacenamiento, redes, IAM; modelo de costos. *Lab: recorrer la consola de Azure.*
- **Semana 2 — AZ-900 (parte 1):** conceptos de nube y arquitectura/servicios core de Azure (Microsoft Learn). *Lab: módulos interactivos con quizzes.*
- **Semana 3 — AZ-900 (parte 2):** gestión, gobernanza, seguridad, identidad, precios y SLA; exámenes de práctica oficiales. *Lab: practice assessment de Microsoft.*
- **Semana 4 — Presentar AZ-900 + arrancar Terraform:** qué es IaC; instalación; *providers*; primer recurso. *Lab: crear tu primer recurso con Terraform.*
- **Semana 5 — Terraform a fondo:** variables, *outputs*, el *state* y por qué importa. *Lab: parametrizar una infra.*
- **Semana 6 — Módulos y entornos:** reutilización; separar dev/prod. *Lab: levantar y destruir un entorno completo.*
- **Semana 7 — Buffer + hito.**

### Hito de dominio
Levantar **y destruir** un entorno completo con un solo comando de Terraform. **+ AZ-900 aprobado** (se aprueba con 700/1000).

### Recursos recomendados
- **Microsoft Learn — ruta AZ-900** — oficial, gratuita, con quizzes: `learn.microsoft.com` (ruta "Azure Fundamentals").
- **John Savill — AZ-900 Study Cram** (YouTube) — repaso integral antes del examen.
- **Microsoft — Practice Assessment AZ-900** — examen de práctica oficial y gratuito.
- **HashiCorp — Terraform Tutorials** — oficiales: `developer.hashicorp.com/terraform/tutorials`
- **Terraform: Up & Running** (Yevgeniy Brikman) — libro de referencia.

**Duración estimada:** 5–7 semanas · **Certs:** **AZ-900** + (opcional) HashiCorp Terraform Associate.

---

## Fase 3 — Orquestación

**Objetivo:** correr aplicaciones en contenedores a escala con Kubernetes.

**Por qué importa:** es el estándar de la industria para operar sistemas distribuidos y uno de los mayores imanes de ofertas laborales.

### Conceptos clave
- **Kubernetes (K8s):** orquestador que automatiza el despliegue, escalado y operación de apps en contenedores a través de muchos servidores.
- **Pod:** la unidad mínima desplegable; envuelve uno o más contenedores.
- **Deployment:** define cuántas réplicas de tu app quieres y mantiene ese estado (recrea pods caídos).
- **Service:** da una dirección estable para acceder a un conjunto de pods que van y vienen.
- **Ingress:** gestiona el acceso externo (HTTP/HTTPS) hacia los servicios, con reglas de enrutamiento.
- **ConfigMap / Secret:** formas de inyectar configuración y datos sensibles a los pods.
- **Helm:** el "gestor de paquetes" de Kubernetes; empaqueta aplicaciones completas en *charts* reutilizables.
- **DOKS:** Kubernetes administrado por DigitalOcean — no mantienes tú el *control plane*.

### Plan semana por semana
- **Semana 1 — Por qué K8s + arquitectura:** *control plane* vs *nodes*; `kubectl`. *Lab: levantar un clúster local o pequeño y conectarte.*
- **Semana 2 — Pods y Deployments:** crear, inspeccionar, escalar. *Lab: desplegar tu primera app.*
- **Semana 3 — Services e Ingress:** exponer apps dentro y fuera del clúster. *Lab: publicar una app por HTTP.*
- **Semana 4 — Configuración y datos:** ConfigMaps, Secrets, volúmenes persistentes. *Lab: app con configuración y estado.*
- **Semana 5 — Clúster administrado (DOKS):** desplegar una app real de Calibeb/Estibarrel. *Lab: despliegue en DOKS.*
- **Semana 6 — Helm:** *charts*, *releases*, plantillas. *Lab: empaquetar tu app en un chart.*
- **Semana 7 — Operación:** escalado, *rolling updates*, *health checks*. *Lab: actualizar sin downtime.*
- **Semana 8 — Buffer + hito.**

### Hito de dominio
Desplegar, escalar y actualizar una app en Kubernetes **sin downtime**.

### Recursos recomendados
- **KodeKloud** (Mumshad Mannambeth) — laboratorios interactivos de Kubernetes, los más populares para CKA.
- **Kubernetes — Tutorials** (docs oficiales): `kubernetes.io/docs/tutorials`
- **TechWorld with Nana** (YouTube) — Kubernetes crash course.
- **Kubernetes the Hard Way** (Kelsey Hightower, GitHub) — para entender el motor por dentro (avanzado, opcional).
- **DigitalOcean Kubernetes (DOKS) docs** — para el clúster administrado.

**Duración estimada:** 6–8 semanas · **Cert opcional (futuro):** CKA — Certified Kubernetes Administrator.

---

## Fase 4 — Observabilidad y SRE

**Objetivo:** ver, medir y garantizar la confiabilidad de los sistemas.

**Por qué importa:** "si no lo mides, no lo controlas". Es lo que separa operar de adivinar, y el núcleo del rol SRE.

### Conceptos clave
- **Observabilidad:** la capacidad de entender qué pasa dentro de un sistema desde afuera, a partir de sus señales.
- **Métricas:** números medidos en el tiempo (CPU, latencia, peticiones por segundo).
- **Logs:** registros de eventos que el sistema va escribiendo.
- **Trazas:** el recorrido de una petición a través de los distintos servicios.
- **Prometheus:** sistema que recolecta, almacena y consulta métricas (lenguaje PromQL).
- **Grafana:** herramienta de dashboards para visualizar métricas y logs.
- **Loki:** sistema de agregación de logs, de los creadores de Grafana.
- **SLI / SLO:** Indicador de Nivel de Servicio (lo que mides, ej. % de éxito) y Objetivo (la meta, ej. 99.9%).
- **Error budget:** el margen de fallo que tu SLO permite; cuánto puedes "gastar" en caídas antes de frenar cambios y enfocarte en estabilidad.
- **Postmortem:** análisis *sin culpas* de un incidente para aprender y prevenir su repetición.

### Plan semana por semana
- **Semana 1 — Pilares de observabilidad:** métricas, logs, trazas y por qué importan. *Lab: identificar qué medir en una app real.*
- **Semana 2 — Prometheus:** modelo de datos, *scraping*, PromQL básico. *Lab: recolectar métricas de un servicio.*
- **Semana 3 — Grafana:** dashboards, paneles, fuentes de datos. *Lab: dashboard de salud de Calibeb/Estibarrel.*
- **Semana 4 — Alertas + logs:** reglas de alerta; logs centralizados con Loki. *Lab: alerta que dispare ante una falla.*
- **Semana 5 — Conceptos SRE:** SLI, SLO, error budgets, postmortems, *toil*. *Lab: definir un SLO para una app real.*
- **Semana 6 — Buffer + hito.**

### Hito de dominio
Un dashboard que muestre la salud de un sistema real **+ una alerta funcional** que avise antes de que el cliente note el problema.

### Recursos recomendados
- **Google SRE Book** — la biblia del SRE, gratis en línea: `sre.google/books`
- **Prometheus — docs oficiales**: `prometheus.io/docs`
- **Grafana — Tutorials**: `grafana.com/tutorials`
- **Prometheus: Up & Running** (Brian Brazil) — libro de referencia.

**Duración estimada:** 4–6 semanas.

---

## Fase 5 — DevSecOps

**Objetivo:** integrar la seguridad en todo el ciclo de vida, no como un paso final.

**Por qué importa:** cierra el círculo del experto y es donde tu mentalidad QA se vuelve oro — compuertas de seguridad automatizadas en el pipeline.

### Conceptos clave
- **DevSecOps / shift-left:** mover la seguridad hacia el inicio del ciclo, integrándola en cada etapa en vez de revisarla al final.
- **Gestión de secretos:** manejar contraseñas, llaves y tokens de forma segura, **nunca en el código** (Vault, *secret managers* de la nube).
- **SAST / DAST:** análisis estático (revisa el código sin ejecutarlo) y dinámico (prueba la app corriendo) en busca de vulnerabilidades.
- **Escaneo de imágenes:** revisar las imágenes de contenedor en busca de vulnerabilidades conocidas antes de desplegarlas.
- **Mínimo privilegio:** dar a cada usuario y servicio solo los permisos estrictamente necesarios.
- **Cadena de suministro (supply chain):** asegurar todo lo que entra a tu software (dependencias, imágenes base). Un **SBOM** es el inventario de esos componentes.

### Plan semana por semana
- **Semana 1 — Mentalidad de seguridad:** *shift-left*; superficie de ataque; mínimo privilegio. *Lab: auditar permisos de un servidor real.*
- **Semana 2 — Gestión de secretos:** sacar secretos del repo; introducir un *secret manager*. *Lab: migrar credenciales a un gestor.*
- **Semana 3 — Escaneo de vulnerabilidades:** SAST, DAST, escaneo de imágenes y dependencias. *Lab: escanear una imagen propia.*
- **Semana 4 — Seguridad en CI/CD:** compuertas que bloquean despliegues inseguros. *Lab: pipeline que falla ante vulnerabilidad crítica.*
- **Semana 5 — IAM y cadena de suministro:** mínimo privilegio avanzado; SBOM y firmas. *Lab: endurecer accesos del proyecto.*
- **Semana 6 — Buffer + hito.**

### Hito de dominio
Un pipeline que **bloquee un despliegue** si detecta una vulnerabilidad crítica o un secreto expuesto.

### Recursos recomendados
- **OWASP** — Top 10 y guías de seguridad de referencia: `owasp.org`
- **HashiCorp — Vault Tutorials**: `developer.hashicorp.com/vault`
- **Trivy** — escáner de vulnerabilidades de imágenes y dependencias: `trivy.dev`
- **OWASP DevSecOps Guideline** — buenas prácticas de seguridad en el pipeline.

**Duración estimada:** 4–6 semanas.

---

## Más allá de la Fase 5 — especialización (futuro)

Una vez sólidas las 6 fases, caminos de profundización según hacia dónde apunte la carrera:

- **Platform Engineering** — construir plataformas internas de *developer experience*.
- **Kubernetes avanzado** — operadores, *service mesh*, multi-clúster, GitOps (ArgoCD).
- **Seguridad cloud-native** — *policy as code*, *runtime security*.
- **Multi-nube y FinOps** — optimización de costos y portabilidad.

---

## Ruta de certificaciones (señales de mercado)

| Cert | Cuándo | Rol |
|---|---|---|
| **AZ-900** (Azure Fundamentals) | Fase 2 | Hito motivacional + primera línea en el CV. Se aprueba con 700/1000. |
| Terraform Associate (**004**) | Fase 2 (opcional) | Valida IaC. La versión 003 se retiró en enero 2026. |
| CKA (Kubernetes Admin) | Post Fase 3 (opcional) | Cert con alto peso en el mercado. Practicar en `killer.sh`. |
| AZ-104 / equivalentes | Futuro | Profundidad de nube según objetivo laboral. |

> Las certificaciones son *señal y motivación*, no el objetivo. La habilidad real se construye operando sistemas. Nunca usar *exam dumps*: aprender los conceptos de verdad. **Detalle completo de cada cert** (qué es, qué aprendes, formato, costo) en la *Guía Detallada de Certificaciones*.

---

## Posicionamiento en el mercado (entrevistas)

- **Perfil diferenciador:** "QA/SDET que automatiza toda la cadena de entrega" — escaso y bien pagado.
- DevOps y SRE valoran la mentalidad de testing: pipelines, confiabilidad, automatización de calidad. Alberto ya piensa así.
- En entrevistas, conectar cada tema técnico con experiencia real (laboratorios o proyectos) pesa más que repetir definiciones.

---

## Recursos transversales (para todo el camino)

- **roadmap.sh/devops** — el mapa visual de referencia del rol DevOps.
- **milanm/DevOps-Roadmap** (GitHub) — roadmap 2026 con recursos por tema.
- **The DevOps Handbook** y **The Phoenix Project** (Gene Kim y col.) — la cultura y filosofía detrás de DevOps.
- **Comunidades:** r/devops, r/kubernetes (Reddit), CNCF Slack.

---

## Tracker de competencias

> Se marca `[x]` solo cuando se demuestra dominio real: hacerlo sin guía y explicarlo.

**Fase 0 — Fundamentos**
- [ ] Navegar el sistema de archivos de Linux con soltura
- [ ] Permisos, usuarios y procesos
- [ ] Instalar y administrar paquetes y servicios (systemd)
- [ ] SSH y acceso seguro a servidores
- [ ] Redes básicas: IP/CIDR, DNS, puertos, firewall
- [ ] Scripting básico en Bash
- [ ] Levantar un servidor desde cero y servir un sitio

**Fase 1 — Contenedores y CI/CD**
- [ ] Docker: imágenes, contenedores, volúmenes
- [ ] Docker Compose
- [ ] Pipeline CI/CD con pruebas automatizadas
- [ ] Despliegue automático condicionado a pruebas

**Fase 2 — IaC y nube**
- [ ] Conceptos de nube (cómputo, storage, redes, IAM)
- [ ] AZ-900 aprobado
- [ ] Terraform: recursos, estado, módulos
- [ ] Entorno completo levantado/destruido con un comando

**Fase 3 — Orquestación**
- [ ] Conceptos core de Kubernetes
- [ ] Despliegue en clúster administrado (DOKS)
- [ ] Helm
- [ ] Escalado y actualización sin downtime

**Fase 4 — Observabilidad y SRE**
- [ ] Métricas con Prometheus
- [ ] Dashboards con Grafana
- [ ] Alertas funcionales
- [ ] Conceptos SRE (SLI/SLO/error budgets)

**Fase 5 — DevSecOps**
- [ ] Gestión de secretos
- [ ] Escaneo de vulnerabilidades en CI/CD
- [ ] IAM y mínimo privilegio
- [ ] Pipeline que bloquea despliegues inseguros

---

## Bitácora de progreso

> Registro cronológico: qué se cubrió, qué hizo Alberto, laboratorios. Lo más reciente arriba.

### 2026-06-14 — Guías detalladas (v2.1)
- **Cubierto:** se definió la arquitectura de documentos (maestro = mapa; guías detalladas = profundidad, una por fase). Se completó la **Guía Detallada de Certificaciones** (AZ-900, AZ-104, Terraform Associate 004, CKA, y otras del radar) con datos vigentes verificados. Se completó la **Fase 0 · Guía Maestra**: las 6 semanas de contenido a densidad de libro de texto (shell y archivos; usuarios/permisos/procesos; paquetes/servicios/logs; SSH y hardening; redes/CIDR/firewall; Bash y Git) más el proyecto integrador con checklist y criterio de dominio.
- **Hecho por Alberto:** exigió mayor profundidad iterativamente (ejemplo clave: redefinir CIDR para principiante); pidió un solo documento por fase. Confirmó arranque por fundamentos con 5–8 h/semana.
- **Laboratorios:** —
- **Siguiente:** crear el droplet `lab-aprendizaje`, conectarse y arrancar la Semana 1 de la Fase 0.

### 2026-06-14 — Revisión del plan (v2.0)
- **Cubierto:** se enriqueció el documento maestro tras retroalimentación de Alberto. Se agregó la sección *Way of Work* (lineamientos, ciclo de sesión, proceso de actualización del documento, definición de "dominado"). Se generalizó el rol de los proyectos (temporales; el conocimiento es portable). Se añadieron definiciones de cada concepto, planes semana por semana y recursos verificados por fase.
- **Hecho por Alberto:** revisó la v1.0 y pidió mayor especificidad y profundidad.
- **Laboratorios:** —
- **Siguiente:** crear el droplet `lab-aprendizaje` y conectarse por consola para iniciar la Semana 1.

### 2026-06-14 — Sesión de arranque
- **Cubierto:** definición de objetivos y North Star. Mapeo del roadmap (6 fases). Estrategia de nube (DO para práctica, Azure para cert). Decisión de iniciar por Fase 0. Aclaración de por qué el laboratorio va en DO y no en Azure.
- **Hecho por Alberto:** definió disponibilidad (5–8 h/semana) y nivel actual (fundamentos casi desde cero). Solicitó este documento maestro.
- **Laboratorios:** —

---

## Changelog del documento

| Versión | Fecha | Cambios |
|---|---|---|
| 2.1 | 2026-06-14 | Arquitectura de guías detalladas (companions). Guía de Certificaciones y Guía Maestra de la Fase 0 completas. Terraform Associate sincronizado a la versión 004. |
| 2.0 | 2026-06-14 | Sección *Way of Work*. Proyectos generalizados como laboratorio temporal y portable. Definiciones de conceptos, planes semana por semana, hitos y recursos verificados por fase. Recursos transversales. |
| 1.0 | 2026-06-14 | Creación: North Star, principios, estrategia de nube, roadmap de 6 fases, certificaciones, tracker y bitácora. |
