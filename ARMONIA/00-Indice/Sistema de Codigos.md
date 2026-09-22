---
tags: [meta, claude]
---

# 🚦 Sistema de Códigos (Portero ARM)

Todo en Obsidian es **ARM**. Estos códigos le dicen a Claude Code **de cuál rama** es la sesión, y él ya carga el contexto solo. Creado 2026-09-20.

## Los códigos
| Código | Rama | Se carga |
|---|---|---|
| `HAM:` 🏠 | Sensi Home (trabajo) | Índice HAM + lista de notas + reto Sensi (TRACKER/PLAN) + subagentes + zona roja |
| `CEO:` 👔 | Zamrud | Índice CEO + lista de notas + CLAUDE.md de `zamrud-landing` |
| `ZEN:` 🎭 | Keni | Índice ZEN + lista de notas |
| `TAI:` 💪 | Hábitos | Índice TAI + lista de notas |
| `ARM:` ☯️ | Balance de vida | ARM + los 4 índices |

Siempre se carga también `ARM.md` (vista general).

## Cómo escribirlo (primer mensaje de la sesión)
- `HAM: revisa el sync de hoy`
- `CEO - contrato de la marca`
- `[ZEN] plan de buceo`
- Solo `HAM` (por ejemplo, para responder a la pregunta de Claude)

> Mayúsculas o minúsculas da igual. El guion necesita espacio después (así `tai-chi` no cuenta como TAI).

## Reglas automáticas
1. **Con código** → carga el contexto del área (una sola vez por sesión).
2. **Mismo código otra vez** → solo un recordatorio corto (no repite todo, cuida tu plan Pro).
3. **Otro código en la misma sesión** → cambia de área y carga la nueva.
4. **Sin código en el primer mensaje** → Claude pregunta en 1 línea: ¿HAM, CEO, ZEN, TAI o ARM?
5. **Sesión reanudada o compactada** → recarga sola el área que tenía.
6. **Comandos `/ham` `/ceo` `/zen` `/tai` `/arm`** → siguen funcionando igual (respaldo manual).

## Dónde vive (no está en el vault)
- `C:\Users\Lenovo\.claude\arm-router\areas.json` → **aquí cambias qué se carga** por área
- `C:\Users\Lenovo\.claude\arm-router\router.js` → el portero (no hace falta tocarlo)
- `C:\Users\Lenovo\.claude\settings.json` → hooks `UserPromptSubmit` y `SessionStart` (respaldo: `settings.json.bak-2026-09-20`)

## Probarlo sin gastar nada
```
node C:\Users\Lenovo\.claude\arm-router\router.js test "HAM: hola"
```

## Para apagarlo
Borra el bloque `"hooks"` de `settings.json` (o restaura el `.bak-2026-09-20`).

## 🗂️ Sesiones en el sidebar (desde 2026-09-20)
- **Título:** `CÓDIGO - tema` (ej. `HAM - Auditoría HubSpot`, `CEO - SEO zamrudcol.co`).
- **Grupos del sidebar:** ☯️ ARM · 🏠 HAM · 👔 CEO · 🎭 ZEN · 💪 TAI.
- **Carpeta recomendada al abrir la sesión:** HAM → repo Sensi (`C:\Users\Lenovo\mi-claude-personal\mi-claude-personal`) · CEO → `C:\Users\Lenovo\zamrud-landing` · ZEN / TAI / ARM → el vault (`Documents\GitHub\mi-claude-personal`).
- **Evita "Sin carpeta":** esas sesiones trabajan en una carpeta temporal y sus archivos se borran al eliminar la sesión.
- **Foto del 2026-09-20:** 46 sesiones activas = 32 HAM, 8 CEO, 3 ZEN, 3 ARM, 0 TAI. Solo 18 de 46 estaban en la carpeta correcta; 24 en carpeta temporal; 4 CEO estaban en el repo equivocado (Sensi o vault).

## Pendientes
- Esto funciona en **Claude Code**. Los Proyectos de claude.ai siguen con sus propias instrucciones (ver [[Como organizar mis Proyectos de Claude]]).
- El reto Sensi tenía fecha final 16-sep-2026: cuando lo cierres, quita ese puntero de `HAM` en `areas.json`.

⬅️ Volver a [[ARM]]
