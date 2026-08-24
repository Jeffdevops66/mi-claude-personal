# 🚀 GUÍA DE INICIO — Cómo empezar el reto (sin saber nada de código)

> **Para quién es esto:** para ti, o para CUALQUIER persona que agarre este proyecto sin saber programar.
> **Qué necesitas saber:** abrir programas y escribir mensajes. Nada más. 😊

---

## 🎯 ¿De qué se trata todo esto? (en 4 frases)

1. El **16 de septiembre de 2026**, Miguel (el CEO) te va a evaluar con una lista de **10 puntos**.
2. Si pasas, tu pago sube de **$2,000 a $2,500 al mes**. 💰
3. Este proyecto es tu **mapa**: te dice qué hacer cada día, 1 hora al día, durante 11 semanas.
4. Claude es tu **copiloto**: tú escribes un comando, y él te dice exactamente qué toca hoy y te acompaña a hacerlo.

**La regla de oro:** 🥇 *Nunca digas que algo está "hecho" sin una prueba (una captura de pantalla, un documento, un contrato). Si no hay prueba, no está hecho.*

---

## 🧰 Parte 1 — Tus herramientas (qué es cada cosa)

Piensa en esto como tu mochila de la escuela. Llevas 3 cosas:

| Herramienta | ¿Qué es? | ¿Para qué la usas? |
|---|---|---|
| **Claude Code** 🤖 | La app donde escribes mensajes a Claude (esta misma) | Aquí vive tu copiloto. Aquí escribes los comandos. |
| **GitHub Desktop** 📦 | Una app que guarda copias de seguridad de tus archivos en internet | Para que NUNCA pierdas tu trabajo, ni aunque se dañe la computadora. |
| **La carpeta del proyecto** 📂 | `C:\Users\Lenovo\mi-claude-personal\mi-claude-personal\proyectos\reto-systems-revops` | Aquí están todos los planes, el checklist y tus evidencias. |

### 📂 ¿Qué hay dentro de la carpeta del proyecto?

| Archivo | ¿Qué es? (en simple) |
|---|---|
| `00-PLAN-MAESTRO.md` | 🗺️ El mapa completo: el calendario de las 11 semanas, día por día. |
| `01-hubspot-inflow.md` | Plan para el sistema de ventas (HubSpot) y el inventario (inFlow). |
| `02-woocommerce-quickbooks.md` | Plan para la tienda online y la contabilidad. |
| `03-it-seguridad.md` | Plan de seguridad: contraseñas, antivirus de empresa (MSP) y seguro. ⚠️ Lo más urgente. |
| `04-tektone.md` | Plan para montar los sistemas de la otra empresa (Tektone). |
| `05-documentacion-evaluacion.md` | Plan para escribir los 18 manuales (SOPs) y preparar la evaluación. |
| `TRACKER.md` | ✅ Tu checklist. Cada día marcas lo que SÍ hiciste. Es tu boleta de calificaciones. |
| `GUIA-DE-INICIO.md` | 📖 Este archivo que estás leyendo. |

💡 **Truco:** puedes abrir cualquiera de estos archivos con doble clic (se abren como texto). Pero casi nunca necesitas hacerlo — Claude los lee por ti con los comandos.

---

## ⌨️ Parte 2 — Tus 6 comandos mágicos (apréndete solo estos)

Un "comando" es un mensaje que empieza con `/`. Lo escribes en Claude Code y aprietas Enter. Ya. Eso es todo el "código" que necesitas saber. 😄

| Comando | ¿Cuándo lo usas? | ¿Qué hace? |
|---|---|---|
| `/sesion-diaria` | 🌅 **Todos los días** (lunes a sábado), al empezar tu hora | Te dice qué toca HOY, con los pasos exactos, y al final marca tu avance en el checklist. |
| `/update-semanal` | 📨 **Todos los viernes**, al final de tu hora | Revisa que el sync no esté roto y te arma el mensaje semanal para Miguel, listo para copiar y pegar. |
| `/documentador-sop` | 📝 Cuando toque escribir un manual de un proceso | Te hace 5 preguntas y convierte tus respuestas en un manual profesional. |
| `/preparador-evaluacion` | 🎯 Una vez al mes, y mucho en septiembre | Te dice cómo vas (🟢🟡🔴), arma la carpeta de evidencias y juega a ser Miguel para practicar. |
| `/ronda-diaria` | 👁️ **Todos los días laborales** (lun-vie, 30 min) — es tu TRABAJO, aparte del reto | La ronda del ojo de CEO: caza anomalías en inFlow/HubSpot/Zapier/tienda, estudia 3 productos del catálogo y revisa la experiencia de la web. |
| `/auditoria-cruzada` | 🔄 Los **miércoles** (en lugar de la ronda) y el **primer lunes del mes** (profunda) | Cruza WooCommerce ↔ HubSpot ↔ inFlow (inFlow manda) y entrega el reporte de diferencias con qué corregir. |

Y tienes un **guardián** 🔎 llamado `verificador-calidad`. No es un comando — es un ayudante al que llamas escribiendo esto en Claude Code:

```
Usa el agente verificador-calidad para revisar este documento antes de enviarlo
```

Úsalo SIEMPRE antes de mandarle algo importante a Miguel, al broker de seguros o al MSP. Él caza errores de fechas, números y datos inventados.

---

## 📋 Parte 3 — LA CHULETA: qué escribir cada día (copia y pega, sin buscar nada)

Esta tabla es TODO tu día. No necesitas abrir ningún archivo del proyecto:

| Día | 👁️ ROL (30-45 min, mañana) | 🏆 RETO (1 hora) | 📨 Extra |
|---|---|---|---|
| **Lunes** | `/ronda-diaria` | `/sesion-diaria` | 1er lunes del mes: `/auditoria-cruzada profunda` (2h) |
| **Martes** | `/ronda-diaria` | `/sesion-diaria` | — |
| **Miércoles** | `/auditoria-cruzada` (45 min — hoy NO hay ronda) | `/sesion-diaria` | — |
| **Jueves** | `/ronda-diaria` | `/sesion-diaria` | — |
| **Viernes** | `/ronda-diaria` | `/sesion-diaria` | `/update-semanal` (15 min) + guardar en GitHub Desktop 📦 |
| **Sábado** | 😌 sin ronda | `/sesion-diaria` (SOPs cuando toque) | — |
| **Domingo** | 😴 libre | 😴 libre | — |

### ✂️ Frases listas para copiar (para cualquier momento)

| Cuando... | Copia y pega esto en Claude |
|---|---|
| Terminaste una tarea del reto | `Listo, terminé. Mi evidencia es: [tu prueba]` |
| Vas a enviar algo a Miguel/broker/MSP | `Usa el agente verificador-calidad para revisar esto antes de enviarlo` |
| Viste algo raro FUERA de tu ronda | `Anota esta anomalía en el log: vi [qué] en [sistema]` |
| Hiciste algo a mano por 3ª vez | `Agrega al backlog de automatizaciones: [la tarea repetida]` |
| Te trabaste en un paso | `Me trabé en el paso [N], me sale esto: [lo que ves]` |
| Crees que rompiste el sync | `Creo que rompí el sync, esto fue lo que hice: [pasos]` (y NO toques nada más) |
| Quieres saber cómo vas con los 10 criterios | `/preparador-evaluacion` y pide el semáforo |

### 🗂️ Cómo organizar tus sesiones de Claude (tu sistema de control)

Los comandos están instalados en TU computadora, así que funcionan en **cualquier chat nuevo**. Organízate así:

| Sesión | ¿Para qué sirve? |
|---|---|
| 📌 **Sesión "copy-paste"** (una fija) | Solo para venir a copiar comandos y frases. Aquí NO se trabaja. |
| 🌅 **Sesión "daily"** (una nueva cada día) | Cada mañana abres un chat nuevo y ahí corres `/ronda-diaria` y `/sesion-diaria`. |
| 🔧 **Sesión por tarea grande** (una por tema) | Una sesión aparte para cada cosa grande: "Inventario IT", "Llamadas MSP", "Auditoría profunda". |

¿Por qué separar sesiones? 3 razones simples:
1. 🧠 Claude no se confunde mezclando temas distintos.
2. ⛽ Las sesiones cortas gastan menos límite del plan Pro.
3. 🔍 Si quieres revisar qué pasó con una tarea, sabes exactamente en qué sesión está.

💡 **Tranquilo:** Claude tiene memoria entre sesiones. Aunque abras un chat nuevo, ya sabe quién eres, tu proyecto y tus reglas. No tienes que explicarle nada de nuevo.

---

## 📅 Parte 4 — Tu rutina diaria (la de todos los días)

Esto es lo que haces de lunes a sábado. Tarda 1 hora. Síguelo como una receta:

### Paso 1 — Abre Claude Code 🤖
- Busca "Claude" en el menú de inicio de Windows y ábrelo.
- Asegúrate de estar en el proyecto **mi-claude-personal** (aparece el nombre de la carpeta en la app).

### Paso 2 — Escribe el comando del día
```
/sesion-diaria
```
Aprieta Enter.

### Paso 3 — Lee lo que Claude te dice
Claude va a mirar el calendario y el checklist, y te va a decir:
- 📌 Qué tarea toca HOY
- 🪜 Los pasos exactos (con clics: "abre tal página > menú tal > botón tal")
- 🎁 Qué "entregable" debes tener al final (la prueba de que lo hiciste)

### Paso 4 — Haz la tarea (con Claude al lado)
- Sigue los pasos uno por uno.
- Si te trabas, escríbele a Claude: *"me trabé en el paso 3, me sale esto: [lo que ves]"*. Él te ayuda.
- Si algo te da miedo tocar (por ejemplo, algo del sync de ventas), pregunta ANTES de hacer clic.

### Paso 5 — Guarda tu prueba 📸
- Toma la captura de pantalla, guarda el documento, o anota el dato que pediste.
- Las capturas van en la carpeta del proyecto (Claude te dice dónde exactamente).

### Paso 6 — Cierra el día ✅
Dile a Claude:
```
Listo, terminé. Mi evidencia es: [qué prueba tienes]
```
Claude marca la casilla en el `TRACKER.md`. **Solo se marca con prueba.** Si no terminaste, dilo tal cual — no pasa nada, mañana se recupera.

🕐 **Total: 1 hora.** Si un día no puedes, no te estreses: al día siguiente `/sesion-diaria` detecta lo que quedó pendiente y lo rescata primero.

### 👁️ Y además del reto: tu media hora del ROL (lun-vie)
Tu trabajo diario tiene su propio comando. Escribe:
```
/ronda-diaria
```
Son 30 minutos con 3 bloques: cazar anomalías (lo que se sale del patrón), estudiar 3 productos del catálogo y revisar una parte de la tienda con ojos de cliente. **Los miércoles cambia:** en vez de la ronda escribes `/auditoria-cruzada` (45 min) para cruzar los 3 sistemas. Todo el detalle está en [06-rol-diario.md](06-rol-diario.md).

---

## 📨 Parte 5 — La rutina del viernes (la más importante de la semana)

Los viernes haces tu hora normal Y ADEMÁS esto (15 minutos):

1. Escribe en Claude Code:
   ```
   /update-semanal
   ```
2. Claude te guía por un chequeo de 10 minutos del sync de ventas (para asegurarse de que nada se rompió esta semana).
3. Claude te arma el **mensaje para Miguel** con formato fijo: qué hiciste, qué viene, qué necesitas de él.
4. **Copia el mensaje y envíaselo a Miguel HOY MISMO** (WhatsApp o email). No lo dejes para el lunes. 📬
5. Claude guarda una copia como evidencia (te servirá en septiembre).

¿Por qué es tan importante? Porque cuando llegue la evaluación, Miguel habrá recibido **10 updates tuyos** mostrando avance constante. Eso ya te tiene medio examen ganado. 😎

---

## 📦 Parte 6 — Guardar todo en internet (GitHub Desktop)

Esto es tu copia de seguridad. Hazlo **cada viernes** después del update (2 minutos). Sin escribir código:

1. Abre la app **GitHub Desktop** 🖥️
2. Arriba a la izquierda debe decir **"mi-claude-personal"** (si no, haz clic ahí y selecciónalo).
3. A la izquierda verás la lista de archivos que cambiaron esta semana. Es normal que sean varios.
4. Abajo a la izquierda hay una cajita de texto que dice **"Summary"**. Escribe algo corto, por ejemplo:
   ```
   Avance semana 1
   ```
5. Haz clic en el botón azul **"Commit to main"** ✅
6. Arriba, haz clic en **"Push origin"** ⬆️

¡Listo! Tu trabajo ya está guardado en internet. Si tu computadora explota 💥, no pierdes nada.

---

## 🎯 Parte 7 — El calendario grande (para que sepas a dónde vas)

| Fecha | 🏁 Hito (meta grande) |
|---|---|
| **Semanas 1-3 (jul)** | ⚠️ LO URGENTE: el MSP (soporte de IT) y el seguro cibernético están VENCIDOS desde el 1 de julio. Se atacan primero. |
| **Vie 28-ago** | MSP contratado y seguro cibernético activo. ✅ |
| **Vie 11-sep** | Le entregas a Miguel el "dossier": el PDF con las pruebas de los 10 puntos. |
| **Lun 14 y Mar 15-sep** | Simulacros: Claude juega a ser Miguel y te hace el examen de práctica. |
| **Mié 16-sep** | 🏆 LA EVALUACIÓN. Si pasas: $2,500/mes. |

Una vez al mes (y cada semana en septiembre), escribe `/preparador-evaluacion` y pide el **semáforo** para ver cómo vas: 🟢 hecho con prueba, 🟡 en camino, 🔴 sin arrancar.

---

## 🆘 Parte 8 — ¿Qué hago si...?

| Problema | Solución |
|---|---|
| 😰 "No sé qué toca hoy" | Mira la chuleta (Parte 3) o escribe `/sesion-diaria`. Siempre. Es tu botón de inicio. |
| 📅 "Me perdí uno o varios días" | Escribe `/sesion-diaria` — detecta lo pendiente y rescata primero lo crítico. Los sábados sirven para recuperar. |
| 🤔 "No sé si algo ya estaba hecho de antes" | NUNCA lo supongas. Dile a Claude: "verifica si X está hecho" y busquen la prueba juntos. |
| ⛔ "Claude dice que llegué al límite de uso" | Es normal en el plan Pro. Espera a que se reinicie (te dice la hora) y mientras tanto haz la parte manual de la tarea (tomar capturas, enviar un email, leer un plan). |
| 💌 "Voy a enviar algo importante a Miguel/broker/MSP" | ANTES de enviar: "Usa el agente verificador-calidad para revisar esto". |
| 🔥 "Toqué algo y creo que rompí el sync de ventas" | No toques nada más. Dile a Claude: "creo que rompí el sync, esto fue lo que hice: [pasos]". El plan `01-hubspot-inflow.md` tiene la guía de rescate. |
| 🙋 "Otra persona va a seguir este proyecto" | Que lea ESTE archivo de arriba a abajo. Todo lo que necesita está aquí. |

---

## 🏁 Parte 9 — Tu PRIMER paso (hazlo ahora mismo)

Ya está todo montado. Solo falta que arranques:

1. ✍️ Escribe en Claude Code:
   ```
   /sesion-diaria
   ```
2. Haz tu primera hora siguiendo lo que te diga.
3. Al final, guarda la evidencia y cierra el día.

Eso es TODO. Un comando al día. El sistema hace el resto. 💪

> 🐢 **Recuerda:** esto no se gana en un día. Se gana con 1 hora al día, 6 días a la semana, durante 11 semanas. Como entrenar para una carrera: lo que cuenta es no faltar al entrenamiento.
