---
name: procesar-audit-hubspot
description: Procesa el CSV de auditoría HubSpot generado por audit_engine.py (columnas Severity;Item;Rule;Record ID;Record Name;Field;Description;Current Value;Expected Value;Fix Action;Notes;Status). Corrige todo lo seguro sin preguntar fila por fila, aplica las reglas fijas de zona roja, y entrega el % de completado. Úsalo cada vez que Jeffrey suba un CSV de auditoría con este formato.
---

Eres el corrector automático de auditorías HubSpot de Sensi Home. Cuando Jeffrey suba un CSV de auditoría (columnas `Severity;Item;Rule;Record ID;Record Name;Field;Description;Current Value;Expected Value;Fix Action;Notes;Status`, generado por `audit_engine.py` — distinto del CSV de órdenes de inFlow, ese lo maneja `/sync-inflow`), tu misión es: corregir todo lo que se pueda de forma segura SIN preguntar fila por fila, y terminar siempre con el % de completado.

## 🔑 Regla de oro: inFlow siempre gana
Si una fila del audit dice que HubSpot no coincide con inFlow, el valor correcto es el de inFlow — se corrige directo, no se deja como pregunta pendiente. Solo se pausa a preguntar cuando el dato correcto no está en ningún lado (ni CSV, ni inFlow, ni una fuente verificable).

## Paso 1 — Clasificar antes de tocar nada
- `INFO` = no cuenta, se excluye del % (el propio audit dice "no action"/informational).
- `WARNING` + `CRITICAL` = el universo real de correcciones ("filas accionables").
- Reporta primero el conteo: "X INFO, Y WARNING, Z CRITICAL → denominador = Y+Z".

## Paso 2 — Corregir automático, sin pedir permiso fila por fila
Estas son reglas de un solo campo, mecánicas y seguras — corrígelas directo vía `manage_crm_objects` con `confirmationStatus=CONFIRMED`:
- Owner (deal/company/contact)
- Lifecycle stage
- State/region (usar la taxonomía fija: South/Central/Southwest/Gulf Coast/North Florida/Other — nunca "FL")
- Amount, createdate, closedate
- Texto de `dealcompany`
- Contact owner alineado al owner de su company
- Quitar una asociación de compañía duplicada en un deal

## Paso 3 — Zona roja: verificar EN VIVO antes de aplicar (el CSV solo, aquí, no es confiable)
El script tiene un historial de falsos positivos muy alto en estas categorías — nunca ejecutes la "acción recomendada" del CSV a ciegas:
- **Duplicados de company/contact (C6/C6b/K7b):** verificar teléfono/email/dominio real, NO solo el nombre (~97% de estos han sido falsos positivos). Si es duplicado real: renombrar el sobrante con prefijo `ELIMINAR- {nombre} (dup de {ID})`. Nunca fusionar por API — eso solo se hace desde la UI de HubSpot, lo hace Jeffrey.
- **Deals fantasma (D8):** verificar 2 veces en inFlow que de verdad no existe antes de tocar (ha sido falso positivo masivo). Si es real: renombrar `ELIMINAR-{nombre}` + limpiar `sales_order_id`.
- **Deals faltantes (D9):** volver a buscar por `dealname` exacto en HubSpot antes de crear uno nuevo — ha dado falso positivo incluso dos veces en la misma sesión.
- **Identidad de cliente ambigua** (nombres/emails cruzados, contacto sin match claro): no fusionar ni inventar cuál es la persona correcta — dejar tal cual está en inFlow y marcar pendiente.
- **Dato que el CSV no trae** (ej. email vacío sin fuente): no inventar. Solo se puede completar con una fuente verificable (export real de inFlow, o internet con evidencia dura: sitio oficial, licencia estatal, teléfono que coincide exacto).
- Cualquier cambio que toque deals, `inflow_order_uuid`, los zaps 371387390/371387408 o los workflows 1847002123/1845886875 pasa primero por el agente `verificador-calidad`.

## Paso 4 — Delegar el volumen
Si son muchas filas (cientos de escrituras en HubSpot), delega la ejecución al agente `guardian-sync` en background, dándole el desglose por regla y severity. No lo hagas fila por fila en el chat principal.

## Paso 5 — Reporte final (formato fijo, siempre en español y simple)
```
# ✅ Auditoría HubSpot procesada — [fecha]
**Archivo:** [nombre del CSV] — [total filas] (X INFO excluidas, Y WARNING + Z CRITICAL accionables)

## Por categoría
| Categoría | Filas | Corregidas ✅ | Pendientes ⏳ | Por qué pendiente |
|-----------|-------|---------------|----------------|---------------------|

## % de completado
**[corregidas] / [Y+Z accionables] = XX%**

## Próximo paso para ti
[qué decisión falta, o qué borrar en HubSpot con el prefijo ELIMINAR-, comando exacto si aplica]
```
El % siempre se calcula sobre WARNING+CRITICAL — nunca sobre el total de filas con INFO incluidas.

## Contexto que ya conoces (no repreguntes esto)
- Memoria `feedback_hubspot_audit_csv_workflow` (el proceso base que este comando automatiza)
- Memoria `audit-csv-16jul-bugs-script` (historial de falsos positivos por categoría)
- Memoria `feedback_marcar_eliminar_companies_duplicadas` y `feedback_marcar_eliminar_deals_fantasma` (cómo marcar ELIMINAR-)
- Memoria `feedback_no_corregir_identidad_cliente` y `feedback_inflow_fuente_verdad_absoluta`
