---
tags: [indice, arm, herramientas, diseno]
fecha: 2026-09-25
---

# 🧰 Herramientas ARM

Tres herramientas en el celular que comparten el mismo diseño, los mismos colores y la misma barra de arriba (**ARM · Timebox · Cash · Brain**). Vuelve a [[ARM]].

## 📲 Mi ARM: un solo link
**https://claude.ai/artifact/DvAouD9ThdRsQFiaSFBdAP** (privado, solo para mí)

Las tres herramientas viven en una sola página con pestañas abajo. Todo se guarda en la nube, así que se ve igual en cualquier dispositivo.

| Pestaña | Para qué | Dónde se guarda |
|---|---|---|
| ⏱️ **Timebox** | Día (libreta), Semana, Mes (hábitos) y Año (pagos y proyectos) | colección `timebox` |
| 💵 **Cash** | Ingresos y egresos por cuenta de área, metas, por cobrar y por pagar | colecciones `transactions`, `proyectos`, `cx` |
| 🧠 **Brain** | Solo captura: guardar la idea y verla en la Bandeja | colección `ideas` |

Los artefactos sueltos anteriores (Timebox ARM, Cash Flow Jeff, Brain Dump) ya no se usan: lo que se marque ahí no pasa a Mi ARM.

## Un solo universo: las 4 áreas
Mismo color y misma sigla en las tres herramientas.

| Área | Color | Tema |
|---|---|---|
| [[TAI - Indice\|TAI]] | azul | Hábitos, idiomas, ejercicio |
| [[ZEN - Indice\|ZEN]] | verde | Keni: arte, deportes, música |
| [[HAM - Indice\|HAM]] | naranja | Sensi Home |
| [[CEO - Indice\|CEO]] | amarillo | Zamrud |

Morado = ARM. Turquesa = ingreso o hecho. Rojo = egreso o vencido.

## Reglas de diseño
- **Letra:** una sola, Inter, en todo. Modo oscuro morado-negro pensado para el celular.
- **Celular primero:** botones de 44 px, modo claro y oscuro, hoja que sube desde abajo para agregar algo.
- **Sin emojis** dentro de las herramientas: iconos de línea generales y cada área con su punto de color.
- El CSS compartido está en `99-Herramientas/arm-sistema-visual.css`, para que una cuarta herramienta nazca con el mismo diseño.

## Cómo alimentan a Obsidian
- **Brain →** botón *Copiar todo para Obsidian (.md)*, luego pegar en [[Diario - Indice|Diario]] o en la nota del área. Claude también puede leer las ideas de la nube y pasarlas a esta bóveda.
- **Timebox → Mes** sirve para la revisión semanal del domingo (ver [[ARM]]).
- **Cash →** el resumen del mes va a [[Seguimiento]] en HAM (o `Cash` en CEO).

## Cambios del 2026-09-25
- Diseño unificado en las tres, con la barra ARM para saltar entre ellas.
- Cash Flow: las ventanitas de "+ Meta", "+ Nueva" y "Abono" ahora son hojas dentro de la página; borrar tiene *Deshacer*.
- Brain Dump: una lista a la vez en el celular y las ideas vencidas se marcan en rojo.
- Timebox: pestañas fijas, texto oscuro sobre los colores de área, columna del día fija en Mes.

## 🔗 Cómo se conectan las tres (desde 2026-09-26)
**Brain → Semana → Día:** al programar una idea en Brain (fecha + una hora libre de 1 h) aparece como tarea en la Semana y, cuando llega el día, en el Día. No pisa hábitos ni otras tareas.
- Marcar las casillas de la tarea en el Día → la idea pasa a **Ejecutada**.
- **Ejecutar** en Brain → la tarea queda marcada en el Día.
- Borrar la tarea en Semana o Día → la idea vuelve a **Bandeja** (hay *Deshacer*).

**Brain → Cash (ideas de pago):** un título que empieza con `cash` es un pago.
- `cash 55 mil`, `cash 55k`, `cash 55.000`, `cash 1,5 millones` → monto. `cash +200 mil` → ingreso.
- El área elegida arriba (TAI, ZEN, HAM, CEO) es la **cuenta**; la descripción es la del movimiento.
- Al **ejecutar** la idea se crea el movimiento en Cash con la **fecha programada**.
- Si la idea se reabre o se desmarca, el movimiento se borra. Si se borra la idea ya ejecutada, el movimiento se queda.

**Cash:** el resumen de meses quedó al fondo; arriba van Balance, Ingresos, Egresos y Por cuenta.

## Cambios del 2026-09-26
- Las tres herramientas se unieron en **Mi ARM**, con pestañas abajo (Timebox, Cash, Brain).
- Datos migrados a la nube: hábitos de Timebox hasta el 25-sep, 30 movimientos y 3 cuentas por cobrar/pagar de Cash.
- Brain Dump: las ideas viejas estaban solo en el celular. Para pasarlas: en el Brain Dump viejo tocar *Copiar respaldo (JSON)*, y en Mi ARM > Brain > *Traer ideas del Brain Dump anterior* pegar e Importar.
- Al usar base de datos, Mi ARM no se puede compartir con "cualquiera con el link".
- Brain → Semana → Día sincronizados (arreglado un fallo que impedía guardar la tarea).
- Ideas `cash ...` que registran el pago en Cash al ejecutarse.
- Cash: meses al fondo.

## Cambios del 2026-09-26 (tarde)
- **Tipografía e iconos:** todo en Inter, modo oscuro más profundo, textos de mínimo 10 px, iconos de línea.
- **Timebox → Año (nuevo):** vista de 3 meses (cada mes una fila de días 1–31, como el cuaderno) o de todo el año con el botón *3 meses / Año*.
  - Arriba, el botón *Agregar pago o proyecto*; abajo, los **pendientes de todo el año** agrupados por mes, con la suma de pagos pendientes.
  - Al agregar se elige área, fecha y una hora libre o *Sin hora*. Con hora, aparece también en Semana y Día. Sin hora, solo en Año.
  - También se puede elegir una idea de la Bandeja ("De tu Bandeja").
  - *Listo* marca la idea como hecha (si es `cash`, crea el movimiento en Cash). La ✕ la devuelve a la Bandeja.
- **Timebox → Mes (acostado):** arriba el gráfico del % de hábitos cumplidos por día; abajo cada hábito es una fila y los días 1–31 van en columnas, con ✓/✗ y cuántos días va bien o mal.
- **Brain simplificado:** ya no tiene Programada ni Ejecutada (eso vive en los calendarios). Solo guardar la idea y la Bandeja; se programa desde Año. Se quitaron *Copiar para Obsidian* e *Importar del Brain anterior* (no funcionaban).
- Flujo: **idea en Brain → se programa en Año → se replica en Semana y Día → Listo = queda hecha.**

## Cambios del 2026-09-26 (noche)
- **Timebox → Mes**, de arriba abajo:
  1. Gráfico de puntos grande: % de hábitos cumplidos cada día (0 a 100%).
  2. **Cumplimiento del mes**: porcentaje sobre los días que ya pasaron (los que faltan no lo bajan).
  3. Tracker de hábitos (✓/✗ pequeños, fila OK delgada). Gráfico y tracker se deslizan juntos.
- **Timebox → Año:** cada día muestra su inicial (L M X J V S D); los domingos (descanso) salen apagados.
