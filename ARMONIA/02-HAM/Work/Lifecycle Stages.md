---
tags: [ham, work, hubspot]
rama: HAM
estado: activo
cssclasses:
  - ham
---

# 🎯 Lifecycle Stages — HubSpot Sensi

Resumen sacado directo del portal de HubSpot (Sensi Home, ID 9338219) el 2026-09-08. Es una etiqueta de qué tan avanzada está una Company — desde "recién la conocemos" hasta "ya es cliente fiel". Cada Company tiene UNA sola etiqueta puesta en un momento dado.

## Las 11 etapas que existen hoy (con cuántas Companies hay en cada una)

| Etapa | Companies (2026-09-08) | ¿Quién la mueve? |
|---|---:|---|
| Subscriber | 1 | Manual |
| Lead | 2,240 | Manual / marketing |
| Marketing Qualified Lead | 8 | Manual |
| Sales Qualified Lead | 1 | Manual |
| Opportunity | 28 | Manual |
| **Customer** ✅ | 1,623 | 🤖 Automático |
| **Evangelist** 🏆 | 146 | 🤖 Automático |
| Other | 1 | Manual |
| Retired / Non-operational | 12 | Manual |
| Currently uninterested | 57 | Manual |
| Unresponsive | 28 | Manual |

Las primeras 8 (Subscriber → Other) vienen de fábrica con HubSpot. Las últimas 3 (Retired / Non-operational, Currently uninterested, Unresponsive) las agregamos nosotros — sirven para marcar Companies muertas o que no responden, pero hoy nadie las mueve sola, se ponen a mano.

## ⚠️ Corrección importante (2026-09-23): SÍ hay robots de Subscriber → Opportunity
Se creía que Lead/MQL/SQL eran 100% manuales (así se documentó el 8-sep). Revisando los workflows completos en HubSpot el 23-sep-2026, aparecieron 3 workflows más que sí las mueven solas. Quedan **6 workflows** en total:

**1. "Company nueva - Lifecycle stage inicial (Lead)"** — ID 1884238447
- Se activa cuando se crea una Company
- Condición: su Lifecycle Stage está vacío (`unknown`)
- Acción: la pone en **Lead** automáticamente. Toda company nueva entra como Lead sola.

**2. "Company avanza a MQL (respondió email)"** — ID 1881839702
- Se activa cuando un Contacto de esa Company: **contesta una llamada** (Call Outcome = Connected) **O responde un correo de ventas** (la propiedad "Recent sales email replied date" pasa a tener valor)
- Condición: la Company hoy está en **Lead**
- Acción: sube la Company a **Marketing Qualified Lead**

**3. "Company avanza a SQL (actividad registrada)"** — ID 1881976730
- Se activa cuando se **agenda una reunión** (meeting booked) con un Contacto de esa Company
- Condición: la Company hoy está en **Lead o MQL**
- Acción: sube la Company a **Sales Qualified Lead**

**4. "Company avanza a Customer (Deal SO)"** — ID 1880061235 — el motor de subida
- Se activa cuando un Deal llega a la etapa **SO** (venta cerrada)
- Siempre pone la Company en **Customer**
- Luego mira su historial de compras con las propiedades `Fecha Inicio Periodo`, `Compras-Periodo-Actual`, `Compras-Periodo-Anterior`:
  - 🆕 Primera compra → arranca el contador en 1
  - 🔁 Compra dentro del mismo periodo (60 días) → suma 1 al contador, y si junta suficientes compras en ese periodo, sube a **Evangelist**
  - ⏳ Ya pasó el periodo (nuevo ciclo) → guarda el contador viejo y reinicia en 1

**5. "Sincronizar Lifecycle Empresa a Contactos"** — ID 1876577614
- La Company es la fuente de la verdad. Cuando cambia su etiqueta, este workflow copia esa misma etiqueta a todos los Contactos asociados a esa Company.

**6. "Company baja de Evangelist a Customer (60 dias sin comprar)"** — ID 1880803939 — armado el 2026-09-08
- Si una Company es Evangelist y pasan 60 días sin comprar de nuevo (sin que se actualice `Fecha Inicio Periodo`), la baja sola de vuelta a **Customer**.
- Probado con una Company de prueba antes de activarlo; no afecta retroactivamente a Companies que ya cumplieran la condición el día que se prendió.

## Resumen: toda la cadena Lead → Evangelist está automatizada
| Etapa | ¿Automática? | Qué la dispara |
|---|---|---|
| Lead | ✅ Sí | Company creada sin lifecycle stage |
| MQL | ✅ Sí | Contacto contesta llamada o responde email de ventas |
| SQL | ✅ Sí | Se agenda una reunión con un contacto |
| Opportunity | ❓ No encontrado | No apareció workflow — revisar si existe o si pasa a mano |
| Customer | ✅ Sí | Deal llega a etapa SO |
| Evangelist | ✅ Sí | 2ª+ compra dentro del mismo periodo de 60 días |

Otros 2 workflows relacionados que existen pero no mueven la etapa en sí:
- **"Remove Marketing Contact of MQL SQL after 4 months (120 days)"** — limpia el estado de "Marketing Contact" en Contactos, no toca el lifecycle stage de la Company.
- **"Lead entra como Non-Marketing Contact"** (ID 1884237478) — control de contactos de marketing, no de lifecycle.

## Qué significa esto para el audit C4 (39 filas ambiguas)
Ya no es cierto que "no hay ningún criterio automatizado" — si una Company aparece con Expected Value ambiguo (lead/MQL/SQL), ahora se puede acercar la respuesta revisando: ¿tiene alguna llamada Connected o email de ventas respondido? (→MQL) ¿tiene una reunión agendada? (→SQL) ¿ninguna de las dos? (→Lead). Esto no reemplaza el criterio de Jeffrey pero da una pista objetiva por Company.

## Pendiente / a revisar
- Confirmar si existe un workflow para **Opportunity** (no apareció en la revisión del 23-sep) — o si esa etapa es intencionalmente manual.
- El umbral exacto de compras para "Cumple Evangelist" no se pudo confirmar por un bloqueo raro de la interfaz de HubSpot al abrir esa condición — revisar directo en el workflow 1880061235 (rama "Mismo periodo" → Branch 8) si se necesita el número exacto.

⬅️ Volver a [[HubSpot]]
