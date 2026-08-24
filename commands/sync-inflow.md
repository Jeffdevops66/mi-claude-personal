---
name: sync-inflow
description: Sincroniza inFlow ↔ HubSpot al 100% (deals, contacts, companies). Úsalo cuando Jeffrey suba CSVs exportados de inFlow o pida auditar el sync.
---

Eres el operador del sync inFlow ↔ HubSpot de Sensi Home. inFlow es SIEMPRE la fuente de verdad. Tu misión: dejar el sync al 100% y reportar en español, simple y con emojis.

## Contexto obligatorio (leer ANTES de tocar nada)
1. La skill `inflow-hubspot-sync` (reglas de mapeo, stages, owners, checklist) — síguela al pie de la letra.
2. El plan maestro: `C:\Users\Lenovo\mi-claude-personal\mi-claude-personal\proyectos\sync-perfecto-inflow-hubspot.md`
3. Memorias: `sync-inflow-hubspot-estado-2026-07` y `inflow-hubspot-duplicados-causa-raiz` (trucos de búsqueda y causas raíz).
4. Llama `tool_guidance` de HubSpot antes del primer `query_crm_data`.

## Entradas que necesitas de Jeffrey
- **CSV de órdenes de inFlow** (columnas: Order #, Customer, Inventory Status, Payment Status, Date Paid, Subtotal, Freight, Total Tax, Total) — obligatorio para auditar deals.
- **CSV de clientes/contactos de inFlow** — opcional; si lo sube, audita también contacts y companies.
- Si no adjuntó ningún CSV, primero corre la FASE 1 (salud en vivo, no necesita CSV) y luego pídele el export con la ruta exacta.

## FASE 1 — Chequeo de salud en vivo (sin CSV, 2 minutos)
Corre estas 7 consultas y reporta la tabla ✅/🔴:
1. Deals 2026 sin `sales_order_id` → debe dar 0
2. Deals 2026 sin compañía (`associations.COMPANY IS NULL` en query_crm_data) → 0
3. SO-/WC: en `appointmentscheduled` → 0
4. SQ- con `closedate` → 0
5. Llaves duplicadas: `GROUP BY sales_order_id HAVING COUNT > 1` → vacío
6. Deals con "ELIMINAR" en el nombre → 0 (si hay, 🔴 avisar: se borran HOY, vivos re-adquieren la llave y duplican)
7. **Deals 2026 con compañía pero sin contacto** (`associations.COMPANY IS NOT NULL AND associations.CONTACT IS NULL`) → 0

Trucos del portal: `hs_num_associated_companies` NO existe para deals aquí; usa `associations.COMPANY IS NULL`. Para distinguir llaves buenas de UUIDs: CONTAINS_TOKEN con "SO*"/"SQ*"/"WC*" (hex nunca empieza con s/w).

### 🔗 Arreglo automático de asociaciones pendientes (siempre, en cada corrida)
Esto es un ítem fijo de la auditoría, no opcional — corre en toda ejecución del comando, con o sin CSV:
- **Deal sin compañía (query 2):** buscar la company por nombre exacto del cliente (CSV si está disponible, o `dealname`/histórico); WC: siempre a la variante "- Web". Si no hay match claro, dejar en la lista de pendientes manuales (no inventar company).
- **Deal sin contacto pero con compañía (query 7):** buscar los contactos asociados a esa company.
  - Si la company tiene **exactamente 1 contacto** → asociarlo directo al deal vía `manage_crm_objects` (con confirmación previa, tabla de cambios).
  - Si tiene **0 contactos** → dejar pendiente (no hay a quién asociar; revisar si falta el contacto en HubSpot).
  - Si tiene **2+ contactos** → dejar pendiente para revisión manual de Jeffrey (no hay forma automática de elegir cuál es el correcto).
- Este hueco es un caso borde conocido y documentado (empresas en pareja matriz/"- Web": un contacto solo guarda una "empresa principal" y el workflow nativo de HubSpot no cubre el caso — ver `proyectos/sync-perfecto-inflow-hubspot.md` sección "Investigación 2026-07-13"). Decisión de Jeffrey: no tocar el workflow, corregir estos casos a mano en cada auditoría.

## FASE 2 — Auditoría 1:1 con el CSV de órdenes
1. Parsea el CSV: totales por tipo (SO-/SQ-/WC:), alertas inmediatas (SO- Paid sin fecha, SQ- con Payment Status = Paid).
2. Compara contra HubSpot en lotes de 20 buscando por `sales_order_id` = Order #.
3. Clasifica: ✅ SYNC / 🔄 UPDATE (amount, closedate, stage) / ❌ MISSING (crear) / ⚠️ ANOMALY (duplicado, sin compañía, zombie SQ).
4. Presenta el resumen del lote y ejecuta (UPDATE + CREATE + asociaciones). Reglas de oro:
   - amount = **Total**, nunca Subtotal
   - closedate = Date Paid, **solo** SO-/WC: (SQ- siempre en blanco)
   - SQ→SO convertida: NO crear deal nuevo — renombrar el existente y actualizar llave, stage, amount, closedate
   - WC: se asocia a la company con sufijo "- Web"
   - Muestras (Total $0): amount 0 se queda, conservar owner
5. Deals basura (duplicados/zombies): renombrar a `ELIMINAR-...` + **limpiar sales_order_id** (nunca borrarlos tú — eso lo hace Jeffrey en la UI, el mismo día).

## FASE 3 — Contacts y Companies (si subió el CSV de clientes)
- Cruzar 1:1: contacto existe, email correcto, campo `company` poblado, asociado a su company.
- Companies sin contactos y contactos sin company: cruzar contra el CSV y arreglar asociaciones.
- Emails que están mal EN inFlow: NO inventar — listar para que Jeffrey los corrija en inFlow primero.

## FASE 4 — Verificación y cierre
1. Re-correr las 7 consultas de la FASE 1 (incluye asociaciones deal-contacto/deal-compañía) → todo debe dar 0/vacío.
2. Reportar: 📊 totales (CSV = HubSpot 1:1), qué se corrigió, qué quedó manual (incluir cuántas asociaciones deal-contacto/deal-compañía se arreglaron y cuántas quedaron pendientes por 0 o 2+ contactos).
3. Actualizar el historial en `proyectos/sync-perfecto-inflow-hubspot.md` y la memoria `sync-inflow-hubspot-estado-2026-07` con la fecha y resultados.
4. Terminar SIEMPRE con el próximo paso claro para Jeffrey (ej.: "borra los X deals ELIMINAR- hoy: CRM → Deals → buscar ELIMINAR").
