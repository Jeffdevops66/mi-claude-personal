# 🔄 1. HubSpot + inFlow Sensi Home (criterios 1 y 2 de la evaluación)

> **Objetivo:** Que para el 16 de septiembre Jeffrey sea el dueño total de HubSpot (pipeline, integraciones, handoff Lina→Bautista) y de inFlow Sensi Home (inventario, cotizaciones, órdenes), sin depender de Miguel para nada. VENTAJA ENORME: la parte más difícil YA ESTÁ HECHA — el sync inFlow↔HubSpot con arquitectura UUID v2 está vivo en producción desde el 4 de julio, y la auto-asociación de contactos a deals desde el 5 de julio. Este plan es para: (1) vigilar que siga funcionando, (2) documentarlo como si otro fuera a heredarlo, y (3) dominar las partes de inFlow y HubSpot que todavía no tocas a diario.

---

## 🔍 Auditoría inicial — verifica esto ANTES de empezar

No asumas que algo está hecho. Verifícalo con tus propios ojos y marca la casilla.

- [ ] **¿Los 2 zaps nuevos del sync siguen encendidos (ON)?**
  - 👀 Cómo verificarlo: Entra a https://zapier.com/app/zaps y busca los zaps 371387390 y 371387408. Los dos deben decir ON (interruptor morado). Los zaps viejos del sync deben seguir OFF.
- [ ] **¿Los 2 workflows de auto-asociación siguen encendidos?**
  - 👀 Cómo verificarlo: En HubSpot > Automatizaciones > Workflows, busca los workflows 1847002123 y 1845886875. Ambos deben decir ON. Revisa la pestaña de historial: no debe haber errores rojos en los últimos 7 días.
- [ ] **¿Hay deals duplicados nuevos desde el 4 de julio?**
  - 👀 Cómo verificarlo: En HubSpot, filtra deals creados después del 4-jul y ordena por nombre. Si ves dos deals con el mismo nombre y monto, anota el `inflow_order_uuid` de ambos: si es el mismo UUID, el sync falló y hay que investigar el historial del zap ese día.
- [ ] **¿Puedo entrar a inFlow Sensi Home con mi propio usuario admin?**
  - 👀 Cómo verificarlo: Abre https://app.inflowinventory.com e inicia sesión. Ve a Settings > Team: tu usuario debe tener rol de administrador. Si entras con la cuenta de Miguel, anota 'FALTA USUARIO PROPIO' — pídelo en el handover.
- [ ] **¿Sé cuántos productos, órdenes abiertas y cotizaciones activas hay HOY en inFlow Sensi?**
  - 👀 Cómo verificarlo: En inFlow: Products (número total), Sales Orders con estado abierto, y Quotes activas. Anota los 3 números — es tu foto de partida y te sirve para notar cosas raras después.
- [ ] **¿El pipeline de HubSpot tiene etapas claras y sé qué significa cada una?**
  - 👀 Cómo verificarlo: En HubSpot > Settings > Objects > Deals > Pipelines. Anota las etapas en orden. Si hay alguna que no sabes explicar en una frase, apúntala como duda para Miguel o Lina.
- [ ] **¿El handoff Lina→Bautista está definido en algún lado (workflow, regla o costumbre)?**
  - 👀 Cómo verificarlo: Pregunta directa a Lina: '¿Cómo le pasas hoy un lead a Bautista? ¿Hay algo automático en HubSpot o lo haces a mano?'. Busca también en Workflows de HubSpot palabras como 'Lina', 'Bautista', 'handoff', 'asignación'.
- [ ] **¿Tengo acceso a las cuentas de Zapier y sé cuánto task usage llevamos del plan?**
  - 👀 Cómo verificarlo: En https://zapier.com > foto de perfil > Settings > Billing & usage. Anota el % de tareas usadas del mes. Si va arriba del 80%, avísale a Miguel antes de que el sync se pause solo.

---

## ✅ Tareas semana a semana

### 📌 Semana 1: Auditoría del sync y foto de partida

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Haz los 8 checks de la auditoría inicial, uno por uno, y anota VERDE/AMARILLO/ROJO.
2. Crea el documento 'estado-hubspot-inflow.md' con el semáforo y los 3 números de inFlow (productos, órdenes, cotizaciones).
3. Anota las dudas del pipeline y del handoff para preguntarlas en la reunión con Miguel de esta semana.

📦 **Entregable:** Documento 'estado-hubspot-inflow.md' con semáforo de 8 checks y lista de dudas.

### 📌 Semana 2: Documentar P-01 — Sync inFlow↔HubSpot (tu proceso estrella)

⏱️ **Tiempo estimado:** 1 sesión de 1h (sábado 18-jul según cronograma)

**Pasos:**
1. Usa la plantilla de SOP (está en el archivo 05-documentacion-evaluacion.md).
2. Explica el flujo con un diagrama simple: inFlow (orden) → Zapier (zap 371387390 / 371387408) → HubSpot (deal con inflow_order_uuid).
3. Documenta la historia: por qué había duplicados (la llave sales_order_id cambiaba cuando una cotización se volvía orden) y cómo lo resolviste (llave UUID que nunca cambia + backfill al 100%).
4. Incluye la sección '¿Qué hago si falla?': dónde mirar (historial del zap), qué revisar (task usage, credenciales), y a quién avisar.
5. Toma capturas de los 2 zaps ON y de un deal con su inflow_order_uuid lleno.

📦 **Entregable:** SOP P-01 completo con diagrama, capturas y plan de emergencia — primera fila VERDE del índice maestro.

### 📌 Semana 3 (y todas las siguientes): Rutina de monitoreo semanal del sync — 10 minutos cada viernes

⏱️ **Tiempo estimado:** 10 min cada viernes (dentro de la sesión del update semanal)

**Pasos:**
1. Zapier: los 2 zaps siguen ON y sin errores en el historial de los últimos 7 días.
2. HubSpot: los 2 workflows siguen ON y sin errores.
3. HubSpot: buscar deals duplicados creados en la semana (mismo nombre + mismo monto).
4. Elegir 1 orden creada en inFlow esta semana y verificar que su deal existe en HubSpot con el UUID correcto.
5. Anotar el resultado en una línea del update semanal: 'Sync: ✅ sin errores' o 'Sync: ⚠️ + qué pasó'.

📦 **Entregable:** Línea de estado del sync en cada update semanal a Miguel (evidencia acumulada para el criterio 2).

### 📌 Semana 4: Documentar P-02 (Handoff Lina→Bautista) y P-03 (Auto-asociación contactos→deals)

⏱️ **Tiempo estimado:** 1 sesión de 1h (sábado 1-ago según cronograma)

**Pasos:**
1. P-02: describe paso a paso cómo un lead pasa de Lina a Bautista (quién hace qué, en qué momento, qué campos se llenan). Si hoy es manual, documenta el proceso manual TAL CUAL es y anota 'oportunidad de automatizar' — documentar lo real vale más que inventar lo ideal.
2. P-03: documenta los workflows 1847002123 y 1845886875 — qué hacen (asocian el contacto al deal usando id_empresa_principal), cuándo corren, y captura del historial sin errores.
3. Agrega a ambos la sección '¿Qué hago si falla?'.

📦 **Entregable:** SOPs P-02 y P-03 completos con capturas — el criterio 2 ya tiene sus 3 procesos clave retratados.

### 📌 Semana 5: Dominar inFlow Sensi de punta a punta — ciclo de venta

⏱️ **Tiempo estimado:** 2 sesiones de 1h

**Pasos:**
1. Sesión A: recorre el ciclo completo con una orden de PRUEBA (márcala claramente como TEST): crear cotización → convertirla en orden de venta → marcar como cumplida (fulfilled) → ver cómo baja el inventario. Bórrala o cancélala al final.
2. Verifica que tu orden TEST llegó a HubSpot por el sync (y bórrala también allá) — así confirmas el flujo completo con tus propias manos.
3. Sesión B: recorre los reportes de inFlow (Reports): identifica los 3 que más le sirven a Miguel (ventas por mes, inventario valorizado, órdenes pendientes) y aprende a sacarlos en menos de 2 minutos cada uno.

📦 **Entregable:** Nota 'ciclo-venta-inflow.md' con el paso a paso del ciclo y los 3 reportes clave con capturas.

### 📌 Semana 6: Dashboard #1 para Miguel en HubSpot

⏱️ **Tiempo estimado:** 1 sesión de 1h (sábado 15-ago según cronograma)

**Pasos:**
1. En HubSpot > Reports > Dashboards, crea 'Dashboard Semanal — Miguel' con 4 reportes: deals nuevos por semana, deals por etapa del pipeline, monto total en pipeline, y deals ganados del mes.
2. Configura el envío automático por email cada lunes a las 8am (botón 'Email this dashboard' > recurrente).
3. Mándale a Miguel un mensaje: 'Te va a llegar esto cada lunes — dime si le cambio algo'.

📦 **Entregable:** Dashboard vivo + email automático de lunes activo + OK de Miguel.

### 📌 Semana 8: Documentar P-07 — Pipeline de HubSpot (etapas y reglas)

⏱️ **Tiempo estimado:** 1 sesión de 1h (viernes 28-ago según cronograma)

**Pasos:**
1. Documenta cada etapa del pipeline: nombre, qué significa, quién mueve el deal a esa etapa y cuándo.
2. Documenta las reglas: campos obligatorios por etapa, workflows que se disparan, y qué pasa cuando un deal se gana o se pierde.
3. Incluye captura del pipeline y del historial de un deal real de ejemplo (tapa datos sensibles del cliente).

📦 **Entregable:** SOP P-07 completo — con esto el criterio 2 queda documentado al 100%.

### 📌 Semana 9: Documentar P-10 — Compras y órdenes de compra en inFlow Sensi

⏱️ **Tiempo estimado:** media sesión (martes 1-sep, compartida con P-12 según cronograma)

**Pasos:**
1. Documenta cómo se crea una orden de compra (PO) a un proveedor, cómo se recibe la mercancía y cómo sube el inventario.
2. Anota quién aprueba compras y desde qué monto (pregúntale a Miguel si no está claro).
3. Incluye capturas del flujo con una PO real o de prueba.

📦 **Entregable:** SOP P-10 completo — el criterio 1 queda con documentación completa.

### 📌 Semana 10: Evidencia final y simulacro de los criterios 1 y 2

⏱️ **Tiempo estimado:** dentro del dossier y simulacro de la semana 10 (ver archivo 05)

**Pasos:**
1. Para el criterio 1 (inFlow Sensi): junta en el dossier los SOPs P-01 y P-10, las capturas del ciclo de venta, y los 3 reportes clave.
2. Para el criterio 2 (HubSpot): junta los SOPs P-02, P-03 y P-07, la captura del dashboard de Miguel, y las 8+ semanas de líneas 'Sync: ✅' de tus updates.
3. Simulacro: pídele a alguien (o hazlo solo en voz alta) que te pregunte '¿cómo funciona el sync?' y '¿qué haces si aparece un duplicado?' — debes responder sin mirar notas en menos de 2 minutos.

📦 **Entregable:** Secciones de criterios 1 y 2 del dossier completas y respuesta fluida en el simulacro.

---

## 📚 Recursos de aprendizaje

- **[inFlow Support / Academy](https://www.inflowinventory.com/support)** — videos y artículos, 5-15 min cada uno
  - ¿Por qué?: Es la fuente oficial: busca 'sales order workflow', 'purchase orders' y 'reports' para las semanas 5 y 9.
- **[HubSpot Academy — Reports & Dashboards](https://academy.hubspot.com)** — lección puntual, ~45 min
  - ¿Por qué?: Solo la lección de dashboards para la semana 6. NO hagas el curso completo antes del 16-sep — es para después.
- **[Zapier — historial y solución de errores](https://help.zapier.com/hc/en-us/articles/8496037690637)** — artículo, 10 min
  - ¿Por qué?: Para leer el historial de un zap y entender un error sin pánico — es tu herramienta de la rutina de los viernes.
- **[HubSpot — Workflows: historial de inscripciones](https://knowledge.hubspot.com/workflows/view-workflow-enrollment-history)** — artículo, 10 min
  - ¿Por qué?: Para revisar si los workflows 1847002123 y 1845886875 corrieron bien cada semana.
- **Tu propia memoria del proyecto: [sync-perfecto-inflow-hubspot.md](../sync-perfecto-inflow-hubspot.md)** — documento interno
  - ¿Por qué?: Ahí está la historia completa de la causa raíz de los duplicados y la solución UUID v2 — es la base del SOP P-01.

---

## ⚠️ Riesgos y cómo evitarlos

| Riesgo | Cómo evitarlo |
|--------|---------------|
| Alguien apaga o edita un zap sin avisar y vuelven los duplicados | Rutina de los viernes (10 min) + regla del equipo: nadie toca los zaps del sync sin avisarte. Dilo en la reunión con Miguel de la semana 1. |
| Zapier se queda sin tareas del plan a mitad de mes y el sync se pausa en silencio | Revisar task usage cada viernes en la rutina; si pasa del 80%, avisar a Miguel ESA semana para subir el plan. |
| Confiar en que 'ya funciona' y no documentar — el 16-sep el criterio pide DOCUMENTADO, no solo funcionando | Las fechas de P-01, P-02, P-03, P-07 y P-10 están clavadas en el cronograma. Si una se cae, se recupera el sábado siguiente ANTES que cualquier otra cosa. |
| Hacer pruebas en inFlow y olvidar borrar la orden TEST — ensucia inventario y reportes | Toda orden de prueba lleva 'TEST' en el nombre y se cancela/borra el mismo día. Verifica también que el deal de prueba se borró en HubSpot. |
| El handoff Lina→Bautista vive solo en la cabeza de Lina | Documentarlo en la semana 4 tal cual es hoy (aunque sea manual). Si Lina sale de vacaciones, el SOP P-02 es el respaldo. |
| Cambiar el pipeline o un workflow sin probar y romper el sync | Regla de oro: cambios en HubSpot/Zapier primero en un deal de prueba, nunca directo sobre datos reales. Documentar cada cambio con fecha en el SOP. |

---

## 🎯 Lo que te evalúan el 16-sep en esta área

- [ ] **Criterio 1:** Dominio total de inFlow (Sensi Home) — documentado, sin dependencia de Miguel
- [ ] **Criterio 2:** Dominio total de HubSpot — pipeline, integraciones y workflow de handoff de Lina funcionando

---

## 📄 Plantillas listas para copiar y usar

### 📋 Checklist de la rutina de los viernes (10 min)

````
## Rutina sync inFlow↔HubSpot — Viernes [FECHA]

- [ ] Zap 371387390: ON, sin errores últimos 7 días
- [ ] Zap 371387408: ON, sin errores últimos 7 días
- [ ] Workflow 1847002123: ON, sin errores
- [ ] Workflow 1845886875: ON, sin errores
- [ ] Duplicados nuevos esta semana: NO / SÍ (cuáles: ______)
- [ ] Orden de muestra verificada: inFlow #______ → deal en HubSpot ✅
- [ ] Task usage Zapier: ____% (avisar a Miguel si >80%)

Resultado para el update semanal: Sync ✅ / ⚠️ ______
````

### 📋 Mensaje a Lina para levantar el handoff (semana 1)

````
Hola Lina 👋 Estoy documentando los procesos de HubSpot.
¿Me ayudas con 3 preguntas rápidas sobre cómo le pasas leads a Bautista?

1. ¿En qué momento decides pasarle un lead? (¿qué señal esperas?)
2. ¿Cómo se lo pasas hoy? (¿le cambias el dueño en HubSpot, le escribes, otra cosa?)
3. ¿Qué información le dejas anotada en el deal para que él siga sin preguntarte?

Con eso armo el proceso escrito para que nada se pierda cuando estés de vacaciones 🙌
````

### 📋 Esqueleto del SOP P-01 (Sync inFlow↔HubSpot)

````
# P-01 — Sync inFlow ↔ HubSpot (UUID v2)

**Dueño:** Jeffrey | **Última actualización:** [FECHA] | **Estado:** En producción desde 4-jul-2026

## ¿Qué hace?
Cada orden de venta de inFlow crea/actualiza automáticamente un deal en HubSpot,
usando la llave `inflow_order_uuid` (nunca cambia, por eso no hay duplicados).

## Diagrama
inFlow (orden) → Zapier zap 371387390 / 371387408 → HubSpot (deal + inflow_order_uuid)
HubSpot workflows 1847002123 + 1845886875 → asocian contacto al deal (vía id_empresa_principal)

## Historia (por qué es así)
- Antes: la llave era sales_order_id, que CAMBIABA cuando una cotización (SQ) se volvía orden (SO) → duplicados.
- Ahora: llave UUID fija + backfill 100% de órdenes 2026 (completado 4-jul-2026).

## ¿Qué hago si falla?
1. Zapier > Zap history: buscar el error del día.
2. Revisar task usage (Settings > Billing) — si está al 100%, el sync está pausado por límite.
3. Revisar credenciales de inFlow/HubSpot en el zap (a veces expiran).
4. Si hay duplicado: comparar inflow_order_uuid de ambos deals antes de borrar nada.
5. Avisar a Miguel si afecta datos de clientes.

## Capturas
[zaps ON] [deal con UUID] [workflow history sin errores]
````
