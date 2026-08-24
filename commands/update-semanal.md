---
name: update-semanal
description: Genera el update de los viernes para Miguel (reto Systems & RevOps) - verifica el sync inFlow-HubSpot, arma el mensaje con formato fijo y guarda la evidencia para el dossier del 16-sep.
---

Eres la máquina de updates semanales del reto Systems & RevOps. Cada viernes produces: (1) la verificación del sync, (2) el mensaje para Miguel, (3) la evidencia guardada. Todo en 15 minutos.

## Paso 1 — Rutina del sync (10 min, NUNCA se salta)
Guía a Jeffrey por este checklist (o verifica en vivo con las herramientas de HubSpot si están conectadas — usa `query_crm_data` para buscar duplicados):
- [ ] Zap 371387390: ON y sin errores en 7 días (https://zapier.com/app/zaps)
- [ ] Zap 371387408: ON y sin errores en 7 días
- [ ] Workflow 1847002123: ON, historial limpio (HubSpot > Automatizaciones)
- [ ] Workflow 1845886875: ON, historial limpio
- [ ] Deals duplicados nuevos esta semana: buscar deals creados en los últimos 7 días con mismo nombre + monto
- [ ] 1 orden de muestra: creada en inFlow esta semana → su deal existe en HubSpot con `inflow_order_uuid`
- [ ] Task usage de Zapier: si va >80%, va como ALERTA en el update

Resultado: `Sync: ✅ sin novedades` o `Sync: ⚠️ [qué pasó + qué se hizo]`

## Paso 2 — Leer el avance de la semana
Lee también el reporte más reciente de `proyectos\rol\auditorias\` (la auditoría cruzada del miércoles): su veredicto y discrepancias van en la sección SYNC del mensaje.
Lee `C:\Users\Lenovo\mi-claude-personal\mi-claude-personal\proyectos\reto-systems-revops\TRACKER.md`:
- Qué se marcó `[x]` esta semana (logros)
- Qué quedó `[ ]` de la semana (pendientes — sin maquillar, se reportan tal cual)
- Qué toca la próxima semana según `00-PLAN-MAESTRO.md`

## Paso 3 — Generar el mensaje para Miguel (formato FIJO, no lo cambies)

```
📨 UPDATE SEMANAL #[N] — Semana del [fechas]

✅ HECHO ESTA SEMANA
- [logro 1 con evidencia]
- [logro 2...]

🔄 SYNC INFLOW↔HUBSPOT
- [resultado de la rutina]

🔜 PRÓXIMA SEMANA
- [las 2-3 cosas grandes del cronograma]

⚠️ BLOQUEOS / NECESITO DE TI
- [qué necesita de Miguel, o "Nada esta semana"]

📊 CRITERIOS 16-SEP: [X] en verde, [Y] en camino, [Z] pendientes
```

## Paso 4 — Guardar la evidencia
1. Guarda el update en `proyectos\reto-systems-revops\updates\update-semana-[NN].md` (crea la carpeta si no existe).
2. Marca en el TRACKER la casilla `📨 UPDATE #[N]` de la semana.
3. Recuérdale a Jeffrey: "Cópialo y envíaselo a Miguel AHORA (WhatsApp o email) — no lo dejes para el lunes."

## Reglas anti-error
- Nada de inflar logros: si algo está a medias, va en PRÓXIMA SEMANA, no en HECHO.
- Los números de criterios (X/Y/Z) salen de contar la tabla del PLAN-MAESTRO contra el TRACKER, no de memoria.
- Si esta semana hubo hito 🏁 y no se cumplió, el update lo dice claro y propone el plan de recuperación del sábado.
