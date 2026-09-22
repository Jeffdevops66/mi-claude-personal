# 🔄 Reporte de Auditoría HubSpot — 21/22-sep-2026

> Fuente: `Sensi_HubSpot_Audit_2026-09-21(All Findings).csv` — generado por `audit_engine.py`, procesado con `/procesar-audit-hubspot`.
> Regla sagrada: inFlow es la fuente de verdad. El "Expected Value" del CSV ya viene calculado desde inFlow.

---

## 📊 Resumen ejecutivo

| Métrica | Valor |
|---|---|
| Total de filas | **1,893** |
| 🔵 INFO (no cuenta para el %) | 1,143 (60.4%) |
| 🟡 WARNING | 643 (34.0%) |
| 🔴 CRITICAL | 107 (5.6%) |
| **Accionables (WARNING+CRITICAL)** | **750** |

### % de completado: **332 / 750 = 44.3%** (parcial, sigue en curso — actualizado tras verificar zona roja)

---

## 🪣 Los 3 baldes

### ✅ SAFE — 304 filas mecánicas de 1 solo campo (ejecutado por `guardian-sync`)
| Regla | Qué es | Total | Aplicadas ✅ | Pendientes ⏳ |
|---|---|---:|---:|---:|
| C2 | Owner de company | 21 | 18 | 3 |
| C4 | Lifecycle stage | 108 | 69 | 39 |
| C5 | Estado/región | 6 | 6 | 0 |
| K4 | Owner de contact alineado a su company | 4 | 4 | 0 |
| D2 | Amount de deal | 2 | 2 | 0 |
| D3 | Createdate de deal | 155 | 136 | 19 |
| D4 | Texto `deal_company` | 2 | 2 | 0 |
| D6 | Owner de deal | 4 | 4 | 0 |
| D10 | Quitar asociación de company duplicada en deal | 2 | 0 | 2 |
| **Total SAFE** | | **304** | **241** | **63** |

**Por qué quedaron pendientes las 63:**
1. **C2 (3):** IDs auditados devuelven 404 en HubSpot — Miami Kitchen and Bath Remodeling (58455852169), Corner Stone Kitchen Bath & Floor (58465354353), "test" (58483242131). Mismo patrón de IDs desactualizados tras un merge ya documentado el 16-jul-2026.
2. **C4 (39):** el "Expected Value" del CSV trae 3 opciones ("lead / marketingqualifiedlead / salesqualifiedlead") en vez de 1 sola — `audit_engine.py` no decide cuál. **Hallazgo importante:** no existe ningún workflow de HubSpot que decida esto solo — ver [[Lifecycle Stages]]. Las etapas Subscriber→Opportunity (incluye Lead/MQL/SQL) son **100% manuales**; solo el tramo Customer↔Evangelist está automatizado. Necesita criterio de Jeffrey/ventas, no un dato que se pueda leer de un workflow.
3. **D3 (19):** saltos de fecha de 2 a 38 días (el patrón normal es +1 día), casi todas agrupadas en órdenes SO-0100xx recientes. `verificador-calidad` recomendó confirmarlas contra inFlow antes de aplicar — no se aplicaron a ciegas.
4. **D10 (2):** deal SO-010013 (quitar "Amazing Kitchen LLC") y SQ-015962 (quitar "Reguera Corporation") — **no existe ninguna herramienta en este MCP que permita remover una asociación ya existente** (`manage_crm_objects` solo agrega asociaciones, nunca quita). Requiere hacerlo a mano en HubSpot o vía navegador.

**Verificación:** las 165 filas de Deals (D2/D3/D4/D6/D10) pasaron primero por `verificador-calidad` antes de escribirse — veredicto **LISTO PARCIAL**: aprobó 146 (136 D3 limpias + D2 + D4 + D6 + D10), dejó fuera las 19 D3 sospechosas. Las 139 de Companies/Contacts (C2/C4/C5/K4) no necesitan ese paso. Cada escritura se verificó con una lectura aparte después de aplicar (regla del 16-jul: nunca confiar solo en "SUCCESS").

### 🔴 RED_ZONE — 134 filas, verificado en vivo — **91/134 resueltas**
| Regla | Filas | Resueltas | Cómo |
|---|---:|---:|---|
| C6+C6b | 48 | 40 | 1 duplicado real → `ELIMINAR-` (ONE HOME DESIGN, mismo teléfono y dominio); 37 falso positivo; 2 obsoletas (ya no existen) |
| K7b | 52 | 48 | 7 duplicados reales → `ELIMINAR-` (email/teléfono/dominio exacto); 40 falso positivo; 1 obsoleta |
| D9 | 2 | 2 | Falso positivo confirmado (4ª vez este mismo bug del script) — los 2 deals SÍ existen |
| D5 | 1 | 1 | Ya estaba bien asociado — "Shadai Carpenter" ni siquiera existe como company |
| D8 | 31 | 0 | Sin acceso a inFlow en esa sesión — las 31 quedaron pendientes, no se asumió nada |

Quedan **12 pendientes** (8 companies + 4 contacts, datos insuficientes para confirmar) + **31 D8** (necesitan buscarse en inFlow). 8 companies/contacts quedaron marcadas `ELIMINAR-` — Jeffrey debe fusionarlas por la UI de HubSpot (nunca por API) y borrar después el registro `ELIMINAR-`.

Con la muestra más grande medida hasta hoy (audit del 20-ago-2026), K7b y C6b habían dado ~97% falso positivo — hoy bajó porque esta corrida sí traía email para cruzar, no solo teléfono.

### ✋ MANUAL — 312 filas, requieren decisión humana (sin tocar)
| Regla | Qué es | Filas |
|---|---|---:|
| C3 | Contacto de inFlow no asociado a la company en HubSpot | 145 |
| K3 | Contacto sin company primaria asociada | 83 |
| K2 | Email de contacto faltante/inválido | 75 |
| K1 | Nombre con formato raro | 9 |

---

## 🪜 Próximos pasos

1. **D10 (2 filas):** Jeffrey resuelve a mano en HubSpot, o se intenta vía navegador (Chrome) ya que la API no tiene esa herramienta.
2. **C4 (39 filas):** Jeffrey decide el criterio para Lead/MQL/SQL (no hay automatización que lo resuelva sola).
3. **D3 (19 filas):** confirmar fechas contra inFlow antes de aplicar.
4. **C2 (3 filas):** confirmar si esas companies se fusionaron o se borraron.
5. **Zona roja (134):** verificación en vivo en curso.
6. **Manual (312):** agenda para revisión con Jeffrey/ventas.

Ver anomalías nuevas de esta corrida en [log-anomalias.md](../log-anomalias.md).
