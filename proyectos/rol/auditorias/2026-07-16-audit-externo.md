# 🔄 Reporte de Auditoría inFlow ↔ HubSpot — 16-jul-2026

> Fuente: `audit16.7.csv` (2,886 filas) — auditoría externa recibida hoy, no generada por nuestra rutina interna.
> Regla sagrada: inFlow es la fuente de verdad. Todo "Fix Action" de este archivo ya viene calculado (Current Value → Expected Value).

---

## ✅ Cambios en vivo ya aplicados (16-jul, Prioridad 1 segura)

Jeffrey aprobó aplicar SOLO la Prioridad 1 segura (no zona roja, no duplicados). Resultado final:

| Regla | Alcance | Confirmados | Fallidos | Nota |
|---|---|---|---|---|
| D2 | 1 monto de deal | ✅ 1/1 | 0 | SQ-014592 → $819.94 |
| D6 | 1 dueño de deal | ✅ 1/1 | 0 | SQ-014948 → Lina Aristizabal |
| C2 | 57 dueños de empresa | ✅ 54/57 | 3 | 3 fallaron por 404 "Resource not found" (IDs del audit ya no existen en HubSpot — probable empresa eliminada/fusionada) |
| K4 | 3 dueños de contacto | ✅ 2/3 | 1 | 1 quedó AMBIGUO — "Iris Mendonca" no existe en HubSpot, ni asociada a la empresa esperada. No se escribió nada |
| C7 | 3 empresas "faltantes" | 0/3 (no aplicaba) | — | **Falso positivo**: las 3 ya existían, solo que inFlow tiene doble espacio en el nombre y no hizo match exacto |

**Total: 58 de 61 correcciones de dueño/monto aplicadas y verificadas en vivo** (cada una confirmada con una lectura aparte después de escribir, no solo por el "SUCCESS" de la herramienta). Los 3 pendientes (3 empresas 404 + 1 contacto ambiguo) quedan anotados abajo con lo que falta para cerrarlos.

**Companies fallidas (404, ID del audit no existe en HubSpot):**
- Quick Books (id auditado 53291454480)
- Coballes LLC (id auditado 53517510260)
- LGM Remodeling (id auditado 54002343471)
→ Siguiente paso: buscarlas por nombre en HubSpot para encontrar su ID real y reintentar, o confirmar que ya no existen.

**Contacto ambiguo:**
- "Iris Mendonca" (esperado en empresa Rizziolli Kitchen, Corp.) — no existe ningún contacto con ese nombre en HubSpot, y esa empresa no tiene ningún contacto asociado. El único apellido parecido ("Josy Rizziolli Mendonca") es otra persona en otra empresa. No se tocó nada.

**Anomalías nuevas encontradas durante la ejecución** (detalle completo en [log-anomalias.md](../log-anomalias.md)):
1. Falso positivo C7 (doble espacio en nombres de inFlow)
2. Cambio de dealname SQ→SO durante la ejecución (comportamiento normal, sin impacto)
3. Escrituras de HubSpot vía Zapier no confiables en lote — patrón documentado, mitigado con verificación obligatoria
4. 9 de las 43 empresas del lote del agente en segundo plano resolvieron a un ID de HubSpot distinto al auditado (mismo nombre) — patrón compatible con fusiones de registros
5. 2 contactos (Paola Hernandez, Miguel Benedetty) corregidos en dueño, pero su empresa asociada real no coincide con la que decía el audit — vale la pena revisar a mano
6. **Susto del mismo día:** una re-verificación en vivo pareció mostrar que 7 de las 9 empresas del punto 4 habían "perdido" el dueño correcto horas después de aplicado — se pausó todo y se investigó con `guardian-sync`. Diagnóstico (16-jul, vía historial oficial `propertiesWithHistory`, sin escribir nada): **fue una falsa alarma de lectura**, no una reversión real. Las 6 empresas revisadas a fondo mantienen el dueño correcto como último evento en su historial oficial. El bug de fiabilidad ya documentado en el punto 3 (escrituras) **también aplica a lecturas** (`get_company_by_id`/`query_crm_data`) — de ahora en adelante, cualquier verificación de dueño debe hacerse con GET directo + `propertiesWithHistory`, no con esas herramientas. Detalle completo en el log de anomalías.

---

## 📊 Resumen ejecutivo

| Métrica | Valor |
|---|---|
| Total de hallazgos | **2,886** |
| 🔴 CRITICAL | 269 (9.3%) |
| 🟡 WARNING | 1,753 (60.7%) |
| 🔵 INFO (nota, no bloquea) | 864 (29.9%) |
| Deals con al menos 1 hallazgo | 1,226 (72 con algo CRITICAL) |
| Companies con al menos 1 hallazgo | 635 (76 con algo CRITICAL) |
| Contacts con al menos 1 hallazgo | 246 (107 con algo CRITICAL) |

### % completado: **0%**
Es una auditoría nueva, recién recibida — nada de esto se ha corregido todavía. Este reporte es la línea base de hoy.

### % sync (salud del sync ahora mismo): **90.7%**
Fórmula: `(2,886 − 269 CRITICAL) / 2,886 = 90.7%`
Lectura: 9 de cada 10 hallazgos son limpieza normal (fechas, formato, etiquetas). El otro **9.3% son rupturas reales** — dinero mal puesto, dueño equivocado, empresa/contacto/deal fantasma o mal asociado.

> ⚠️ Nota honesta: no pude sacar en vivo el total real de deals/companies/contacts en HubSpot (el endpoint de conteo no está disponible desde aquí), así que no tengo un "% de cobertura total" preciso. La última cifra que tengo en memoria es 1,575 companies (15-jun-2026) — puede haber cambiado. Si quieres el número exacto hoy, lo puedo pedir por otra vía.

---

## 🔍 Desglose por categoría y regla

### Deals (1,895 hallazgos)
| Regla | Qué revisa | Cantidad | Gravedad |
|---|---|---|---|
| D3 | Fecha de creación no coincide con inFlow | 940 | 🟡 |
| D3 (informativo) | Fecha de cierre distinta a la fecha de orden inFlow | 863 | 🔵 |
| D10 | Deal asociado a 2 empresas (debe ser solo 1, la de inFlow) | 71 | 🔴 |
| D8 | Deal "fantasma": SQ convertido a SO en inFlow pero no se borró en HubSpot | 10 | 🟡 |
| D4 | Texto del campo empresa del deal no coincide | 3 | 🟡 |
| D9 | Orden de inFlow SIN deal en HubSpot — posible falla del Zap | 3 | 🔴 |
| D5 | Empresa asociada casi-coincide (posible error de tipeo) | 2 | 🟡 |
| D2 | Monto del deal no coincide con inFlow | 1 | 🔴 |
| D6 | Dueño del deal no coincide con el rep de inFlow | 1 | 🔴 |

### Companies (731 hallazgos)
| Regla | Qué revisa | Cantidad | Gravedad |
|---|---|---|---|
| C4 | Lifecycle stage inválido o vacío | 576 | 🟡 |
| C2 | Dueño de la empresa no coincide con inFlow | 57 | 🔴 |
| C6b | Posible empresa duplicada (nombre parecido) | 44 (21🔴+23🟡) | 🔴/🟡 |
| C3 | Contacto asociado con nombre igual pero email distinto | 41 | 🟡 |
| C5 | Estado/región no coincide | 7 | 🟡 |
| C7 | Cliente de inFlow SIN empresa en HubSpot | 3 | 🔴 |
| C1 | Nombre con mayúsculas/espacios distintos a inFlow | 2 | 🟡 |
| C6 | Empresa duplicada EXACTA (mismo nombre, 2 registros) | 1 | 🔴 |

### Contacts (260 hallazgos)
| Regla | Qué revisa | Cantidad | Gravedad |
|---|---|---|---|
| K2 | Email faltante o mal formado | 74 | 🟡 |
| K3 | Contacto sin empresa principal asociada | 68 | 🔴 |
| K1 | Nombre mal formado (coma pegada, "Apellido,Nombre") | 67 | 🟡 |
| K7b | Posible contacto duplicado | 45 (41🔴+4🟡) | 🔴/🟡 |
| K5 | Teléfono mal formado | 3 | 🟡 |
| K4 | Dueño del contacto no coincide con dueño de su empresa | 3 (2🔴+1🟡) | 🔴 |

---

## 🔴 Prioridad 1 — Esta semana (rompe dinero, sync o reportes)

1. **D9 (3 deals):** órdenes de inFlow que NO tienen deal en HubSpot — posible falla del Zap. Revisar el historial de Zapier para esas fechas antes de crear el deal a mano, para no duplicar si el Zap solo se atrasó.
2. **D2 (1 deal):** SQ-014592 tiene el monto mal — corrección directa: fijar a $819.94.
3. **Dueños mal asignados (D6 + C2 + K4 = 61 registros):** esto afecta comisiones y a quién le llega la notificación. El CSV ya trae el dueño correcto calculado — es aplicar el valor, no investigar.
4. **D10 (71 deals, 2 empresas asociadas):** ⚠️ **Esto es el MISMO problema que ya viste el 7-jul** (los 206 deals del backfill, [[inflow-hubspot-sync-estado]]) — incluye los 2 casos que quedaron pendientes entonces (SQ-013439 y WC:17130). Que siga apareciendo (71 nuevos) confirma que **la causa raíz sigue viva**: el workflow de auto-asociación (1847002123 / 1845886875) le pega la empresa base Y la empresa "- Web" al mismo deal en las órdenes de la tienda. **Antes de limpiar los 71, hay que arreglar el workflow** — si no, se vuelve a llenar.
5. **C7 (3 companies):** clientes reales de inFlow sin ficha de empresa en HubSpot — crearlas.

## 🟡 Prioridad 2 — Este mes (duplicados, necesitan ojo humano)

- **K7b + C6b (89 posibles duplicados):** 62 son de alta confianza (safe de fusionar con una revisión rápida de 10 segundos c/u), 27 son de confianza media (leer con más cuidado antes de fusionar — riesgo de perder contactos/deals si te equivocas, como pasó con Amauta Kitchen en la ronda del 7-jul).
- **K3 (68 contactos sin empresa):** parte tiene coincidencia sugerida por inFlow (ej. Johnny Zabala → johnny's woodwork corp) y se puede asociar directo; el resto necesita revisar si el contacto sigue vigente.

## 🟢 Prioridad 3 — Limpieza en bloque (alto volumen, bajo riesgo)

D3 (fechas, 940), C4 (lifecycle stage, 576), K1 (formato nombre, 67), K2 (email, 74), K5 (teléfono, 3), C1 (2), C3 (41), C5 (7), D4 (3), D5 (2), D8 (10 deals fantasma — confirmar y borrar).

---

## 🪜 Paso a paso sugerido

1. **Hoy/mañana:** resolver a mano los 4 registros de mayor impacto — los 3 D9 + el 1 D2. Son pocos pero son plata/sync real.
2. **Esta semana:** aplicar el batch de dueños (C2 + D6 + K4 = 61) — el CSV ya trae el valor correcto, es copiar y pegar o correr un script.
3. **Antes de tocar los 71 D10:** arreglar el workflow de auto-asociación. Esto es **zona roja** (toca deals + los workflows 1847002123/1845886875) → pasa por el agente `guardian-sync` para diagnosticar y `verificador-calidad` antes de aplicar.
4. **Después de arreglar el workflow:** limpiar los 71 D10 con el mismo método que ya funcionó el 7-jul (remove_associations en lotes de ~50 vía Zapier).
5. **Duplicados:** agenda 20-30 min/día, empezando por los 62 de alta confianza (K7b/C6b).
6. **Limpieza masiva (Prioridad 3):** correr un script que lea el CSV y aplique los valores ya calculados vía la API de HubSpot en lote.
7. **C7 (3):** crear las 3 empresas faltantes a mano — son pocas.
8. **D8 (10 deals fantasma):** confirmar uno por uno que sí son conversión SQ→SO y borrar en HubSpot — son pocos, no vale la pena automatizar.

---

## 🤖 Qué se puede automatizar

- **Script "aplica el Fix Action del CSV"** para las reglas de valor 1-a-1 ya calculado (D3, C1, C4, C5, D4, K1, K2 formato, K5 formato): ~1,770 de las 2,886 filas no necesitan criterio humano, solo aplicar `Expected Value` vía la API de batch-update de HubSpot. Esto es la mayor ganancia de tiempo de todo el reporte.
- **remove_associations en lote** para D10 — ya hay precedente que funcionó (7-jul, 204/206 corregidos). Reusar el mismo patrón.
- **Detección de duplicados** ya está resuelta (el audit la generó) — lo que falta automatizar es solo el paso de fusión de los de "alta confianza" (100% similitud, incluso mismo nombre exacto) — el resto debe quedar manual por riesgo de perder datos.
- **Recomendación:** que la ejecución de estos batches la corra `guardian-sync` en una sesión dedicada (no cabe en los 30 min de la ronda diaria), con `verificador-calidad` revisando la muestra antes de aplicar cualquier cambio masivo a HubSpot.

---

## 📌 Para el backlog de automatizaciones

Candidato a entrar en [backlog-automatizaciones.md](../backlog-automatizaciones.md): *"Script de aplicación batch de correcciones de auditoría (Fix Action → HubSpot API)"* — dolor: aplicar 1,770+ correcciones a mano es imposible; ya se repitió el patrón (7-jul con 206 deals, hoy con 71+576+etc.); herramienta probable: código + HubSpot batch API vía Zapier.
