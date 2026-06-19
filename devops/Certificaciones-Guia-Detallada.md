# Guía Detallada de Certificaciones

> Companion del documento maestro *Ruta Maestra · DevOps · Cloud · SRE · DevSecOps*.
> Explica qué es cada certificación, qué aprendes, cómo es el examen y dónde encaja.
> **Última actualización:** 2026-06-14 · Datos vigentes verificados a esta fecha.

---

## Cómo leer esta guía

Una certificación es un examen que, al aprobarlo, te da una credencial oficial que dice "esta persona domina X". Sirve para tres cosas: **(1)** te da una meta concreta que ordena tu estudio, **(2)** es una señal en tu CV que los reclutadores filtran, y **(3)** el proceso de prepararla te obliga a cubrir temas que solo no verías.

**Advertencia honesta:** una certificación **no** sustituye saber hacer el trabajo. El mercado en 2026 premia a quien construye, rompe y arregla sistemas, no a quien colecciona insignias. Por eso en nuestro plan las certificaciones van *después* o *junto* a la práctica real, nunca en lugar de ella. Y nunca se usan *exam dumps* (bancos de respuestas robadas): te hacen "pasar" sin aprender, que es justo lo contrario de lo que buscas.

Los costos son aproximados en USD y varían por región e impuestos.

---

## 1. AZ-900 — Microsoft Azure Fundamentals

**Qué es:** la certificación de **entrada** al mundo Azure. Nivel: fundamentos (la más básica). No requiere experiencia previa.

**Qué aprendes:**
- **Conceptos de nube** que aplican a *cualquier* proveedor: qué es la nube, modelos (IaaS/PaaS/SaaS), nube pública/privada/híbrida, el modelo de responsabilidad compartida (qué asegura el proveedor vs. qué aseguras tú).
- **Servicios core de Azure:** cómputo (máquinas virtuales, contenedores), almacenamiento, redes, bases de datos — a nivel de "qué es y para qué sirve cada uno", sin configurarlos a fondo.
- **Seguridad, identidad y gobernanza:** cómo Azure controla accesos, protege recursos y aplica políticas.
- **Precios y soporte:** cómo se cobra, cómo estimar costos, qué garantiza un SLA (acuerdo de nivel de servicio).

**Formato del examen:** ~40–60 preguntas (opción múltiple, arrastrar y soltar, casos); se aprueba con **700 de 1000**. Mayormente teórico/conceptual — no tienes que operar Azure en vivo.

**Costo y vigencia:** ~$99 USD. La credencial de fundamentos no caduca.

**Dónde encaja en el plan:** **Fase 2.** Es el "sprint de motivación" que mencionamos: te da una victoria temprana y tu primera línea de certificación en el CV.

**¿Vale la pena?** Sí, como hito motivacional y por su buen costo-beneficio. Pero ten claro qué es: valida *vocabulario y conceptos*, no que sepas administrar nada. Es el escalón, no la meta.

---

## 2. AZ-104 — Microsoft Azure Administrator Associate

**Qué es:** el salto serio. Nivel: **asociado** (intermedio). Aquí ya no es vocabulario: certifica que sabes **operar Azure en el día a día**, como lo haría un administrador de infraestructura real. Es una de las certificaciones de Azure más respetadas y pedidas.

**Qué aprendes (sus 5 dominios):**
1. **Identidades y gobernanza (15–25%):** gestionar usuarios y grupos en Microsoft Entra (antes Azure AD), control de acceso basado en roles (RBAC = decidir quién puede hacer qué), suscripciones, grupos de recursos, políticas, etiquetas y control de costos. *Por qué importa: el acceso mal configurado es una de las mayores causas de brechas de seguridad en la nube.*
2. **Almacenamiento (15–20%):** crear y asegurar cuentas de almacenamiento, manejar archivos, blobs y permisos de acceso.
3. **Cómputo (20–25%):** desplegar y administrar máquinas virtuales, contenedores y apps; escalarlos según la carga.
4. **Redes virtuales (20–25%):** diseñar cómo se comunican los recursos de forma segura — redes virtuales, subredes, balanceadores de carga, DNS, conexiones. *Por qué importa: la mayoría de las caídas e incidentes de seguridad nacen de un mal diseño de red.*
5. **Monitoreo y respaldo (10–15%):** vigilar la salud de los recursos y poder recuperarlos ante un fallo.

**Formato del examen:** 40–60 preguntas, 100 minutos, **basado en escenarios** (te plantean un problema real y tienes que razonar la solución, no solo recordar definiciones). Se aprueba con **700 de 1000**. Necesitas experiencia real con el portal de Azure, la línea de comandos (CLI) y PowerShell — quien solo lee documentación sin tocar Azure, reprueba.

**Costo y vigencia:** ~$165 USD. Válida **1 año**, con renovación gratuita en línea.

**Dónde encaja en el plan:** **futuro**, después de la Fase 2 y de tener experiencia práctica con nube e IaC. No es para ya; es el objetivo natural si tu carrera apunta fuerte a Azure.

**¿Vale la pena?** Sí, si quieres trabajar con Azure profesionalmente. A diferencia del AZ-900, esta sí le dice a un empleador "puede operar mi infraestructura". Es notablemente más difícil porque prueba ejecución, no teoría.

---

## 3. HashiCorp Terraform Associate (004) — Infraestructura como Código

**Qué es:** la certificación de IaC más popular del mercado y, por mucho, la de mejor relación costo-beneficio. Es **agnóstica de proveedor**, así que complementa cualquier certificación de nube (Azure, AWS o GCP).

> Nota de versión: la versión vigente es la **004** (la 003 se retiró el 7–8 de enero de 2026). La 004 se alinea con Terraform 1.12.

**Qué aprendes:**
- **Concepto de IaC** y por qué Terraform en vez de hacer las cosas a mano o con otras herramientas.
- **El flujo de trabajo core:** `init` (preparar), `plan` (previsualizar cambios), `apply` (crear/modificar), `destroy` (eliminar). Este ciclo es el pan de cada día.
- **HCL**, el lenguaje de configuración de Terraform (cómo escribir la definición de tu infraestructura).
- **Manejo del estado (state):** el archivo donde Terraform recuerda qué creó; estado local vs. remoto, y por qué el estado es tan delicado.
- **Módulos:** empaquetar configuración reutilizable.
- **HCP Terraform** (la plataforma en la nube de HashiCorp) y el ecosistema (providers, registry).

**Formato del examen:** ~57 preguntas (verdadero/falso, selección única y múltiple), 60 minutos, en línea con supervisor remoto (vía Certiverse). Resultado pass/fail inmediato.

**Costo y vigencia:** **~$70.50 USD** — la certificación seria más barata del mercado. Válida **2 años**.

**Dónde encaja en el plan:** **Fase 2 (opcional)**, justo cuando aprendes Terraform. Es un excelente segundo cert: barato, de alto valor y refuerza lo que ya estarás practicando.

**¿Vale la pena?** Casi siempre sí. Por su precio y por ser vendor-neutral, es de las credenciales de mayor retorno en todo IT. Con práctica real, 4–6 semanas de preparación bastan.

---

## 4. CKA — Certified Kubernetes Administrator

**Qué es:** el estándar de oro para demostrar que sabes **administrar clústeres de Kubernetes**. La emite la CNCF (la fundación que gobierna Kubernetes) junto con la Linux Foundation. Es vendor-neutral y muy reconocida; los puestos de SRE, Platform y DevOps senior suelen pedirla o valorarla mucho.

**Qué la hace distinta:** **no es de opción múltiple.** Es 100% práctica: te sientan frente a una terminal con clústeres reales y tienes que resolver tareas de verdad. No puedes adivinar; o sabes hacerlo, o no.

**Qué aprendes (sus dominios, 2026):**
- **Arquitectura, instalación y configuración del clúster (25%):** montar y mantener un clúster, actualizarlo, manejar permisos (RBAC), respaldar y restaurar `etcd` (la base de datos del clúster).
- **Servicios y redes (20%):** cómo se comunican los componentes y cómo se expone una app al exterior; políticas de red.
- **Cargas de trabajo y planificación (15%):** desplegar y programar aplicaciones.
- **Almacenamiento (10%):** volúmenes persistentes para datos que deben sobrevivir.
- **Diagnóstico y resolución de problemas (30%):** el dominio más pesado. Diagnosticar y arreglar clústeres rotos. *Tip de los que la pasan: dedica ~40% de tu estudio a romper y arreglar cosas a propósito.*

**Formato del examen:** práctico, supervisado en línea, ~15–20 tareas en 2 horas. Se aprueba con **66%**. Puedes consultar la documentación oficial (`kubernetes.io/docs`) durante el examen — saber buscar rápido ahí es parte de la habilidad.

**Costo y vigencia:** **$445 USD**, incluye un reintento gratis y 2 intentos en el simulador Killer.sh. Válida ~2 años.

**Dónde encaja en el plan:** **futuro**, después de la Fase 3. Es una certificación intermedia-avanzada: necesitas dominar Linux, YAML y contenedores *antes* de intentarla. No es un punto de partida.

**¿Vale la pena?** Si quieres especializarte en infraestructura cloud-native, es de las que más mueven la aguja salarial. Pero exige práctica real intensa (6–10 semanas); no se pasa leyendo.

---

## Otras certificaciones relevantes (para tu radar, no para ya)

- **LFCA / LFCS (Linux Foundation):** validan administración de Linux. Buen complemento a la Fase 0 si quieres una credencial de fundamentos de sistemas.
- **SC-900 (Microsoft Security Fundamentals):** primo del AZ-900 pero enfocado en seguridad/identidad. Útil de cara a la Fase 5 (DevSecOps).
- **CKAD / CKS (CNCF):** hermanas de la CKA. CKAD se enfoca en *desarrollar* apps para Kubernetes; CKS en *seguridad* de Kubernetes (requiere tener la CKA primero).
- **Equivalentes en AWS** (Cloud Practitioner, Solutions Architect): si algún día tu mercado pide AWS en vez de Azure, el camino es análogo. Los fundamentos que aprenderás transfieren.

---

## Orden recomendado para Alberto

1. **AZ-900** (Fase 2) — victoria temprana, conceptos de nube.
2. **Terraform Associate** (Fase 2, opcional) — barato, alto valor, refuerza IaC.
3. **CKA** (post Fase 3) — el salto de peso, cuando ya domines Kubernetes con las manos.
4. **AZ-104** (futuro) — si tu carrera se inclina fuerte hacia Azure y administración de nube.

> Regla de oro: ninguna se intenta sin haber hecho primero la práctica de su fase. La credencial confirma una habilidad que ya tienes; no la reemplaza.
