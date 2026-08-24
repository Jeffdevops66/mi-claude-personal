# 🔄 Auditoría cruzada HubSpot ↔ inFlow — 2026-07-07

**Alcance:** CSV del audit_engine (`Audit Sensi.csv`, generado 7-jul 11:45am, 467 hallazgos, inFlow = fuente de verdad) + verificación EN VIVO en HubSpot vía MCP (muestras de cada regla).

> Nota: la corrida anterior del mismo día tenía 1,090 hallazgos; esta tiene 467 y ya no trae reglas C (empresas) ni C4 (lifecycle) — o se corrigieron o el script corrió con otro alcance. Confirmar con Jeffrey qué versión del script generó este archivo.

## Cuadratura de órdenes
| Chequeo | Resultado |
|---------|-----------|
| Órdenes inFlow sin deal (D9) | **0 reales** — los 3 del CSV son falsos positivos (deals existen, creados en 2025: SO-008175, SO-009178, SO-009183) |
| Deals duplicados por uuid | 0 (verificado en los 2 sospechosos D8) |
| Flujo del sync 6–7 jul | ✅ vivo — 50 deals nuevos con `inflow_order_uuid`, todos 1:1 |
| Deals web nuevos con 2ª empresa | ✅ 0 — la fuga del D10 **ya no está activa** (verificado WC:17539 y WC:17546: 1 empresa cada uno) |

**¿Cuadran?** ✅ Órdenes 1:1. Lo que hay es backlog de datos, no órdenes perdidas.

## Discrepancias
| # | Regla | Qué | Cuántos | Gravedad | Acción | Responsable |
|---|-------|-----|---------|----------|--------|-------------|
| 1 | D10 | Deal con 2 empresas asociadas (backfill del 5-jul: 78 patrón "madre + -Web", 128 con empresa ajena del contacto) | 206 | 🟡 | ✅ EJECUTADO — 204/206 corregidos (prueba de 1 + 4 lotes de 51 vía Zapier). 2 excluidos: SQ-013439 (empresas duplicadas, ver #7) y WC:17130 (3 empresas asociadas, no 2 — necesita decisión) | Claude (auto) — hecho |
| 2 | K3 | Campo `company` del contacto ≠ empresa primaria | 99 | 🟡 | (a) copiar nombre de la primaria al campo — auto; (b) los que tienen primaria absurda (ej. "HubSpot, Inc.") → corregir la ASOCIACIÓN con el dato de inFlow | Claude (auto) |
| 3 | K3 | Contacto sin empresa primaria (backlog conocido del 3-jul; incluye contactos "12001", "14851" con nombre numérico = posible basura) | 65 | 🟡 | Cruzar con clientes inFlow y asociar; los no-inFlow → lista para decisión | Claude (semi-auto) + Jeffrey decide restos |
| 4 | K2 | Contacto sin email (el dato NO existe en ningún sistema) | 76 | 🟡 | Capturar el email en inFlow PRIMERO y de ahí propagar. No automatizable | Jeffrey / equipo ventas |
| 5 | K7b | Posibles contactos duplicados (Armando Martinez ×2, Duviel/Odil Rodriguez, Joel Fernandez/Hernandez, Rodney/Rokney Graveran ×2) | 5 | 🟡 | Confirmar si son la misma persona y hacer merge en HubSpot UI | Jeffrey (Claude entrega pares con links) |
| 6 | D8 | SQ fantasma: SQ-014853 ($0) y SQ-014856 ($174.73), creados 6-jul, no están en inFlow. Sin gemelo SO, sin rename — el zap SO no los tocó | 2 | 🟡 | Confirmar en inFlow: ¿se convirtieron a SO o se borraron? Si convertidos → Claude renombra por uuid; si borrados → Jeffrey borra los deals | Jeffrey confirma → Claude/Jeffrey ejecuta |
| 7 | D4/D5 | Nombres de empresa casi iguales: "The Carpentry  Team" (doble espacio EN inFlow), "Shaddai Carpentry" vs "Shadai Carpenter", y 2 empresas HubSpot con el mismo nombre "Junior wood working LLC" (SQ-013439) | 4 | 🟡 | Doble espacio → corregir en inFlow primero. Shaddai/Shadai → Jeffrey decide la grafía buena. Junior wood working → merge de empresas duplicadas | Jeffrey decide → Claude propaga |
| 8 | D6 | SQ-014592 con dueña Lina, esperado Miguel | 1 | 🟢 | Cambiar owner del deal | Claude (auto) |
| 9 | K4 | Dueño del contacto ≠ dueño de su empresa (Iris Mendonca → Lina; contacto "Lina Aristizabal" → Miguel) | 2 | 🟢 | Igualar owner del contacto al de la empresa | Claude (auto) |
| 10 | K5 | Teléfonos mal formateados: 2 reformateables (17865476425, (239) 418 – 0011) + 1 incompleto (786-374-354, 9 dígitos) | 3 | 🟢 | 2 auto; el incompleto → buscar el número real en inFlow | Claude (2) + Jeffrey (1) |
| 11 | K1 | "Luis Rafael Rafael" — apellido parece nombre | 1 | 🟢 | Confirmar con inFlow y corregir | Claude (auto) |
| 12 | D9 | 3 falsos positivos (filtro de fecha del script deja fuera deals viejos de órdenes nuevas — lección ya documentada el 3-jul) | 3 | 🟢 | Corregir audit_engine.py: buscar por sales_order_id SIN filtro de fecha | Jeffrey (dueño del script) |

## Veredicto
⚠️ **467 hallazgos, pero el sync está SANO**: 0 órdenes perdidas, 0 duplicados, flujo vivo, fuga D10 apagada. Es limpieza de backlog: **~375 casos automatizables por Claude (~80%)**, ~90 requieren decisión o dato humano.

## Correcciones hechas hoy / agendadas
- Hoy: D10 EJECUTADO — 204 de 206 deals corregidos (dejaron 1 sola empresa asociada, según regla WC→Web / SO→matriz). 2 casos quedaron pendientes de decisión de Jeffrey (ver fila #1 y #7).
- Agendado: resto del backlog (K3, K2, K7b, D8, D6, K4, K1, K5, fix del script D9) — pendiente que Jeffrey diga si seguimos con eso.
- Recordatorio: este reporte alimenta el update del viernes a Miguel; con 2 semanas rodando, el proceso se documenta como SOP P-19.
