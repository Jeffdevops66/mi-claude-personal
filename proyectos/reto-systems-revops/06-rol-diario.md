# 👁️ 6. El ROL de todos los días — Ojo de CEO, automatizar, auditar y documentar

> **De dónde sale esto:** recomendaciones directas de Miguel (7-jul-2026) sobre cómo ejercer el rol de Systems & RevOps Lead. No es parte del reto de 1 hora — es tu TRABAJO diario. Pero alimenta directamente los criterios 1, 2, 3 y 10 de la evaluación del 16-sep.

---

## 🎯 Los 4 mandatos de Miguel (tu brújula)

1. **👁️ Ojo de CEO:** estar SIEMPRE buscando lo que se sale del patrón. Cazar el error antes de que explote. Un número raro, un pedido atorado, un precio en $0, un deal duplicado — tú lo ves primero.
2. **🤖 Tu función es AUTOMATIZAR y AUDITAR:** si algo se hace a mano y se repite, es candidato a automatizarse. Y todo lo automatizado se audita — nunca confíes ciegamente en un robot que tú mismo armaste.
3. **📝 DOCUMENTAR todo proceso** que vayas automatizando o realizando. Sin excepción. (Esto ES el criterio 10 de tu evaluación.)
4. **🛒 WooCommerce es tu tienda:** precios correctos, productos bien posicionados, experiencia de la página cada vez mejor, y el catálogo en tu cabeza. La revisas TODOS los días.

---

## 🗓️ Tu mapa de tiempo (las 2 capas)

| Capa | Cuánto | Cuándo | Comando |
|------|--------|--------|---------|
| 🏆 **El RETO** (construir hacia el 16-sep) | 1 hora | L-S | `/sesion-diaria` |
| 👁️ **El ROL** (operar el negocio con ojo de CEO) | 30 min | L-V | `/ronda-diaria` |
| 🔄 Auditoría cruzada semanal | 45 min | **Miércoles** (reemplaza la ronda de ese día) | `/auditoria-cruzada` |
| 🧨 Auditoría cruzada PROFUNDA | 1-2 h | **Primer lunes de cada mes** | `/auditoria-cruzada profunda` |
| 📨 Update semanal a Miguel | 15 min | Viernes | `/update-semanal` |

> ⚠️ **Modo actual (hasta el Lun 13-jul):** todavía no tienes acceso admin a WooCommerce (handover con Miguel el lunes 13). Hasta entonces, la ronda usa la **tienda pública** (mysensihome.com) + inFlow + HubSpot + Zapier, que sí controlas. La primera auditoría cruzada completa es el **Mié 15-jul**.

---

## 👁️ LA RONDA DIARIA (30 min, L-V) — comando: `/ronda-diaria`

Tres bloques fijos. El comando te guía por ellos cada día:

### Bloque 1 — Caza de anomalías (10-12 min) 🕵️
Recorres tus sistemas buscando lo que se sale del patrón:

| Sistema | Qué mirar | Anomalías típicas |
|---------|-----------|-------------------|
| **inFlow** (fuente de verdad) | Órdenes de las últimas 24h | Orden atorada sin avanzar, cantidad rara (999, 0), precio en $0, cliente duplicado, orden sin factura |
| **HubSpot** | Deals nuevos de ayer | Deal duplicado (mismo nombre + monto), deal sin contacto/empresa, monto que no cuadra con la orden, etapa incorrecta |
| **Zapier** | Historial de los 2 zaps (371387390 / 371387408) | Errores en las últimas 24h, tareas frenadas, task usage subiendo raro |
| **Tienda** (pública por ahora) | Portada + 1 categoría | Precio en $0 o raro, producto agotado en portada, imagen rota, página que no carga |
| **Bandeja** | Emails de clientes/equipo | Alguien reportando un error de pedido, pago o página |

**Regla del ojo de CEO:** si algo te hace decir "qué raro…" → SE ANOTA en [log-anomalias.md](../rol/log-anomalias.md), aunque resulte ser nada. El patrón de rarezas repetidas es donde viven los errores grandes.

### Bloque 2 — Estudio del catálogo (10 min) 📚
- Catálogo: **50-150 productos** → estudias **3 al día**, por categoría (una categoría completa antes de pasar a la otra).
- Ritmo: ~15 por semana → catálogo completo en **7-8 semanas** (listo antes de la evaluación ✅).
- Por cada producto llenas una fila en [catalogo-estudio.md](../rol/catalogo-estudio.md): nombre, SKU, categoría, precio en inFlow, precio en la tienda, ¿coinciden?, posición (dónde aparece), calidad de foto/descripción (1-5), y tu nota de mejora.
- **Desde hoy puedes empezar:** el precio público de la tienda y el precio en inFlow los ves sin necesitar wp-admin.

### Bloque 3 — Experiencia de la página (8-10 min) 🎨
Cada día miras UNA parte de la tienda con ojos de CLIENTE (rotación fija):

| Día | Qué revisas | Preguntas guía |
|-----|-------------|----------------|
| Lun | Portada (home) | ¿Se entiende qué vendemos en 5 segundos? ¿Lo destacado es lo que más conviene vender? |
| Mar | Una categoría | ¿El orden de los productos tiene lógica? ¿Los mejores están arriba? |
| Mié | *(hoy toca auditoría cruzada — no hay bloque 3)* | |
| Jue | Ficha de un producto | ¿La foto vende? ¿La descripción responde las dudas? ¿El precio está visible y correcto? |
| Vie | Carrito y checkout | ¿Cuántos clics hasta pagar? ¿Algo confunde o estorba? *(sin completar compras reales)* |

- Cada hallazgo → una línea en el log de anomalías (si es error) o en el [backlog de mejoras](../rol/backlog-automatizaciones.md) (si es idea).
- 1 vez por semana (viernes) el comando te pide revisar la tienda **desde el teléfono** 📱 — la mitad de los clientes compran así.

---

## 🔄 AUDITORÍA CRUZADA Woo ↔ HubSpot ↔ inFlow — comando: `/auditoria-cruzada`

**La regla sagrada: inFlow es la FUENTE DE VERDAD.** Si un precio o stock difiere entre sistemas, el correcto es el de inFlow (y si inFlow está mal, se corrige inFlow PRIMERO y luego se propaga).

### Semanal (Miércoles, 45 min)
1. **Precios (muestra):** 10 productos al azar de la categoría de la semana → precio inFlow vs precio tienda. ¿Coinciden al centavo?
2. **Stock (muestra):** los mismos 10 → stock inFlow vs disponibilidad en la tienda.
3. **Órdenes (últimos 7 días):** cada pedido de la tienda existe en inFlow → y su deal existe en HubSpot con `inflow_order_uuid`. Los 3 números deben cuadrar.
4. **Huérfanos:** ¿deals en HubSpot sin orden en inFlow? ¿órdenes en inFlow sin deal? (los duplicados eran EL problema histórico — ojo aquí).
5. **Reporte:** se guarda en `proyectos/rol/auditorias/YYYY-MM-DD-semanal.md` con tabla de discrepancias, gravedad (🔴 cliente lo ve / 🟡 interno / 🟢 cosmético) y acción con responsable.
6. El resultado alimenta el update del viernes a Miguel.

### Profunda (primer lunes del mes, 1-2h)
1. **Barrido TOTAL de precios y stock:** exportar la lista completa de productos de inFlow (CSV) y de WooCommerce (CSV) → Claude compara los dos archivos completos y te da TODAS las diferencias (precio, stock, SKUs que están en uno y no en el otro).
2. **Órdenes del mes completo:** conteo tienda vs inFlow vs deals HubSpot — los 3 totales cuadrados.
3. **Posiciones y categorías:** ¿cada producto está en su categoría correcta? ¿los destacados siguen siendo los correctos?
4. **Salud de la página:** velocidad (PageSpeed Insights), links rotos, imágenes faltantes.
5. **Reporte mensual** → mini-resumen para Miguel (3 líneas + tabla).

📅 **Primera semanal completa:** Mié 15-jul (tras el handover). **Primera profunda:** Lun 3-ago.

---

## 🤖 DOCTRINA: Automatizar → Auditar → Documentar

Este es el ciclo de tu rol. Todo lo que tocas pasa por él:

1. **Detecta** (en la ronda): algo manual que se repite. **Regla del 3:** si lo hiciste a mano 3 veces, va al [backlog de automatizaciones](../rol/backlog-automatizaciones.md).
2. **Automatiza:** con la herramienta más simple que funcione (workflow de HubSpot > zap de Zapier > otra cosa). SIEMPRE probado con un dato de PRUEBA antes de tocar datos reales.
3. **Audita:** toda automatización nueva entra a la rutina de vigilancia (la ronda diaria la primera semana, luego la auditoría semanal).
4. **Documenta:** SOP el mismo sábado con `/documentador-sop`. Sin SOP, la automatización "no existe" para el criterio 10.
5. Antes de que algo importante salga al mundo → agente `verificador-calidad`.

> 📌 Dos procesos nuevos entran al índice maestro de documentación: **P-19 Auditoría cruzada Woo↔HubSpot↔inFlow** y **P-20 Ronda diaria (ojo de CEO)**. Se documentan cuando lleven 2 semanas rodando (Sáb 25-jul aprox.).

---

## 📅 Qué agregar a tu calendario (Outlook/Google) — HOY

Crea estos eventos repetitivos (copia los nombres tal cual):

| Evento | Repetición | Duración | Sugerencia de hora |
|--------|------------|----------|--------------------|
| 👁️ Ronda diaria (ojo de CEO) | Lun a Vie | 30 min | 8:30 am (antes del ruido del día) |
| 🔄 Auditoría cruzada semanal | Miércoles | 45 min | en el mismo bloque de la ronda |
| 🧨 Auditoría profunda mensual | Primer lunes del mes | 2 h | primera: **Lun 3-ago** |
| 🏆 Hora del reto | Lun a Sáb | 1 h | la que ya tengas |
| 📨 Update semanal a Miguel | Viernes | 15 min | al final del día |

---

## 📂 Archivos del rol (viven en `proyectos/rol/`)

| Archivo | Qué es |
|---------|--------|
| [log-anomalias.md](../rol/log-anomalias.md) | El diario del ojo de CEO: toda rareza detectada, con fecha y desenlace |
| [catalogo-estudio.md](../rol/catalogo-estudio.md) | Tu estudio del catálogo, producto por producto |
| [backlog-automatizaciones.md](../rol/backlog-automatizaciones.md) | Ideas de automatización y mejoras de la página, priorizadas |
| `auditorias/` | Los reportes de cada auditoría cruzada (semanal y mensual) |

---

## 🏆 Cómo esto alimenta tu evaluación del 16-sep

| Mandato de Miguel | Criterio que fortalece | Evidencia que genera |
|-------------------|------------------------|----------------------|
| Ojo de CEO + ronda diaria | 1 (inFlow) y 2 (HubSpot) | log-anomalias.md con semanas de vigilancia real |
| Catálogo + experiencia web | 3 (WooCommerce) | catalogo-estudio.md completo + mejoras implementadas |
| Auditoría cruzada | 1, 2, 3 | reportes semanales/mensuales con inFlow como fuente de verdad |
| Automatizar-auditar-documentar | 10 (todo documentado) | backlog → automatizaciones → SOPs P-19, P-20 y los que nazcan |

El día de la evaluación, cuando Miguel pregunte "¿cómo sabes que tus sistemas están bien?", tu respuesta es esta carpeta: *"Los vigilo todos los días, los audito cada miércoles a fondo cada mes, y aquí está el registro."* 🎤⬇️
