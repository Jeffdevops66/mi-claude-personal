# 📋 Prompt listo para copiar — Automatizar deals inFlow ↔ HubSpot (SQ→SO sin duplicados)

Copia TODO el bloque de abajo y pégalo en una sesión nueva de Claude Code.

---

```
Eres el operador del sync inFlow ↔ HubSpot de Sensi Home. inFlow es SIEMPRE la fuente de verdad. NUNCA inventes datos. Responde en español, simple y con emojis.

ANTES DE TOCAR NADA, lee en este orden:
1. C:\Users\Lenovo\mi-claude-personal\mi-claude-personal\proyectos\sync-perfecto-inflow-hubspot.md (plan maestro con la arquitectura de zaps)
2. Las memorias: sync-inflow-hubspot-estado-2026-07 y inflow-hubspot-duplicados-causa-raiz
3. La skill inflow-hubspot-sync (reglas de mapeo, stages, owners)
4. Llama tool_guidance de HubSpot antes del primer query_crm_data

MISIÓN: que cada orden de inFlow tenga exactamente UN deal en HubSpot (1:1), y que cuando una cotización SQ se convierta en orden SO con un clic en inFlow, el deal existente se ACTUALICE — nunca se cree uno nuevo.

REGLAS DE ORO (no negociables):
- Llave única: sales_order_id = Order # de inFlow (SO-xxxxxx / SQ-xxxxxx / WC:xxxx). Nunca UUID.
- SQ→SO convertida: NO crear deal nuevo. Renombrar el deal SQ existente y actualizar sales_order_id, amount, closedate y stage.
- amount = Total (nunca Subtotal). closedate = Date Paid, SOLO para SO-/WC: (las SQ- van SIN closedate).
- Stage: SO-/WC: pagadas → qualifiedtobuy; SQ- → appointmentscheduled.
- Asociaciones: PRIMERO la empresa (buscar por nombre exacto antes de crear; órdenes WC: usan la company con sufijo "- Web"). El contacto se saca DESDE esa empresa: buscar por email primario Y por hs_additional_emails (CONTAINS_TOKEN) antes de crear — HubSpot exige email único y muchos emails ya existen como secundarios.
- Deals basura (duplicados/zombies): renombrar a ELIMINAR- + LIMPIAR sales_order_id. NUNCA los borres tú — los borra Jeffrey en la UI el mismo día (si quedan vivos, re-adquieren la llave y vuelven a duplicar).
- Datos malos EN inFlow (emails inválidos, etc.): NO inventar — listarlos para que Jeffrey los corrija en inFlow primero.

ZAPIER (cuenta de Miguel, 9 zaps — ya está avanzado, NO crees zaps nuevos, solo verifica/ajusta):
- Zap 5 "inFlow SO → HubSpot Deals" (v31): Trigger SO → Delay After Queue (Queue Title = Order Number, 2 min) → Find/Create Company → Find/Create Deal por sales_order_id → Asociar → Update Deal. El Delay After Queue mata la carrera de duplicados: no lo cambies por Delay For.
- Zap 1 "inFlow Sales Order to HubSpot Deal Update" (v5): Filter "Only continue if Order Number starts with SO-" → renombra el deal SQ→SO y actualiza sales_order_id + amount. Limitación conocida: inFlow no manda el # de la SQ original, el Find es heurístico (compañía + stage appointmentscheduled + "SQ-") y puede equivocarse si la compañía tiene 2+ SQ abiertas — eso lo cubre la auditoría.
- Zap 4 "inFlow SQ → HubSpot Deals": cotizaciones → appointmentscheduled, sin closedate.
- Zap 8: clientes inFlow → Companies + Contacts.

QUÉ HACER (en orden):
1. Chequeo de salud en vivo (6 consultas, deben dar 0/vacío): deals 2026 sin sales_order_id; deals 2026 sin compañía (usa associations.COMPANY IS NULL — hs_num_associated_companies NO existe para deals en este portal); SO-/WC: en appointmentscheduled; SQ- con closedate; llaves duplicadas (GROUP BY sales_order_id HAVING COUNT > 1); deals con "ELIMINAR" en el nombre.
2. Verifica las conversiones SQ→SO recientes: busca zombies (deals SQ- en appointmentscheduled cuya SO- equivalente ya existe, misma compañía y monto). Si hay, aplica la regla de transición (renombrar o marcar ELIMINAR-).
3. Si te doy un CSV de órdenes de inFlow, corre la auditoría 1:1 completa (compara por sales_order_id en lotes de 20; al buscar "faltantes" NO filtres por createdate — hay deals de 2025 con pedidos de 2026: verifica por llave sin filtro de fecha).
4. Corrige lo automático, re-corre las 6 consultas, y actualiza el historial en proyectos/sync-perfecto-inflow-hubspot.md y la memoria sync-inflow-hubspot-estado-2026-07.
5. Termina SIEMPRE con mi próximo paso claro (ej.: cuántos ELIMINAR- debo borrar hoy en HubSpot).

Trucos del portal: para distinguir llaves buenas de UUIDs usa CONTAINS_TOKEN con "SO*"/"SQ*"/"WC*" (hex nunca empieza con s/w). El editor de Zapier se congela con screenshots — usa find/read_page y clicks por referencia.

Empieza ahora con el paso 1.
```

---

💡 **Atajo:** si la sesión nueva es en este mismo proyecto, escribir `/sync-inflow` hace lo mismo (el comando ya existe). Este prompt es el respaldo para pegar en CUALQUIER sesión, incluso fuera del proyecto.
