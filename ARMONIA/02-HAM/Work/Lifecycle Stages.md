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

## Los 3 workflows que mueven Customer ↔ Evangelist solos

**1. "Company avanza a Customer (Deal SO)"** — ID 1880061235 — el motor de subida
- Se activa cuando un Deal llega a la etapa **SO** (venta cerrada)
- Siempre pone la Company en **Customer**
- Luego mira su historial de compras con las propiedades `Fecha Inicio Periodo`, `Compras-Periodo-Actual`, `Compras-Periodo-Anterior`:
  - 🆕 Primera compra → arranca el contador en 1
  - 🔁 Compra dentro del mismo periodo (60 días) → suma 1 al contador, y si junta suficientes compras en ese periodo, sube a **Evangelist**
  - ⏳ Ya pasó el periodo (nuevo ciclo) → guarda el contador viejo y reinicia en 1

**2. "Sincronizar Lifecycle Empresa a Contactos"** — ID 1876577614
- La Company es la fuente de la verdad. Cuando cambia su etiqueta, este workflow copia esa misma etiqueta a todos los Contactos asociados a esa Company.

**3. "Company baja de Evangelist a Customer (60 dias sin comprar)"** — ID 1880803939 — armado el 2026-09-08
- Si una Company es Evangelist y pasan 60 días sin comprar de nuevo (sin que se actualice `Fecha Inicio Periodo`), la baja sola de vuelta a **Customer**.
- Probado con una Company de prueba antes de activarlo; no afecta retroactivamente a Companies que ya cumplieran la condición el día que se prendió.

## Nota importante
Las etapas de arriba de Customer (Subscriber → Opportunity) hoy **no tienen ningún robot** que las mueva — eso pasa a mano o por otras herramientas (marketing, ventas). Solo el tramo **Customer ↔ Evangelist** está 100% automatizado.

## Pendiente / a revisar
- ¿Vale la pena automatizar también Lead → Customer o algún otro tramo?
- El umbral exacto de compras para "Cumple Evangelist" no se pudo confirmar por un bloqueo raro de la interfaz de HubSpot al abrir esa condición — revisar directo en el workflow 1880061235 (rama "Mismo periodo" → Branch 8) si se necesita el número exacto.

⬅️ Volver a [[HubSpot]]
