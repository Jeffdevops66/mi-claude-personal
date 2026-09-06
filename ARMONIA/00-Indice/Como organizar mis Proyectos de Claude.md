---
tags: [meta, claude]
---

# 🗂️ Cómo organizar mis Proyectos de Claude (para no mezclar contextos)

## Paso 0 — Arreglar el repo primero ✅ HECHO (2026-09-06)
El vault ARMONIA vivía en la rama `claude/obsidian-google-chrome-sync-oqjuaj`, no en `main`.
Ya está resuelto: ARMONIA completo (45 archivos) está en `main` (commit `a0a8c9a`), sin tocar los agentes del reto Tektone.
En GitHub Desktop, cuando abras el repo, asegúrate de estar parado en la rama **main**.

## Las 5 bóvedas en Claude.ai (Proyectos) — ⏳ pendiente, lo haces tú

Esto SÍ lo tienes que hacer tú a mano, porque requiere tu clic de "Autorizar" con tu cuenta — nadie más lo puede hacer por ti.

### Paso 1 — Crear los 5 proyectos
Ve a [claude.ai](https://claude.ai) → **Proyectos** (menú izquierdo) → **Crear proyecto**. Repite 5 veces con estos nombres:

1. ☯️ ARM — Armonía
2. 💪 TAI — Hábitos
3. 🏠 HAM — Sensi / Trabajo
4. 🎭 ZEN — Keni
5. 👔 CEO — Zamrud

### Paso 2 — Pegar las instrucciones de cada uno
Entra a cada proyecto → ⚙️ (configurar proyecto) → **Instrucciones personalizadas** → pega el texto correspondiente:

**☯️ ARM**
> Este proyecto es ARM: la vista general de mi proyecto de vida. Aquí reviso el balance entre mis 4 áreas (TAI, HAM, ZEN, CEO) y tomo decisiones grandes. Si te pregunto algo muy específico de una sola área, dime que lo lleve a su proyecto correspondiente. Respóndeme en español, simple como si tuviera 10 años, con emojis, y dame siempre el paso exacto a seguir.

**💪 TAI**
> Este proyecto es TAI: mis hábitos (inglés, italiano, ruso, chino, ejercicio, meditación, journaling), de lunes a viernes. No hables de Sensi, Zamrud ni de Keni aquí. Respóndeme en español, simple, con emojis, y dame el paso exacto.

**🏠 HAM**
> Este proyecto es HAM: Sensi Home (mi único ingreso), HubSpot, Zapier, WooCommerce, catálogo, y cualquier ingreso extra. No mezcles con Zamrud (CEO) ni con mis hobbies (ZEN). Respóndeme en español, simple, con emojis, y dame el paso exacto.

**🎭 ZEN**
> Este proyecto es ZEN: Keni, mi lado artista (música, edición de fotos/video, cámaras) y deportista extremo (buceo, paracaidismo, kart) y viajes. No mezcles con trabajo (HAM) ni con Zamrud (CEO). Respóndeme en español, simple, con emojis, y dame el paso exacto.

**👔 CEO**
> Este proyecto es CEO: Zamrud — cash, legal, contenido (shorts, faceless), línea de ropa, marketing con IA. No mezcles con Sensi (HAM) ni con hobbies (ZEN). Respóndeme en español, simple, con emojis, y dame el paso exacto.

### Paso 3 — Conectar cada proyecto a GitHub (para que lea el vault actualizado)
Dentro de cada proyecto → **Agregar contenido** → **GitHub** → autoriza tu cuenta `Jeffdevops66` (solo la primera vez) → elige el repo **mi-claude-personal** → confirma.

Repite esto en los 5 proyectos, eligiendo siempre el mismo repo (ya tiene ARMONIA adentro, en `main`).

### Cómo usarlo día a día (activación)
- Cada vez que quieras hablar de un tema, abre el Proyecto correcto (no un chat normal) — así Claude ya sabe el contexto y no mezcla nada.
- Si actualizas una nota en Obsidian y la subes a GitHub (commit + push desde GitHub Desktop), el proyecto conectado la ve automáticamente la próxima vez que le preguntes — no hay que resubir nada a mano.
- Si abres un chat normal (fuera de Proyectos), Claude no sabe nada de esto — usa siempre el Proyecto correspondiente.

## Claude Code (en el PC)
- `ARMONIA/` (Documents\GitHub\mi-claude-personal) = vault de vida
- `mi-claude-personal\mi-claude-personal` = repo técnico del reto Tektone (temporal, hasta 16-sep-2026)
- Se mantienen separados por ahora; se revisa fusión después del reto.

## Regla de oro
Antes de escribir: ¿esto es ARM, TAI, HAM, ZEN o CEO? → abrir ESE proyecto/carpeta.

⬅️ Volver a [[ARM]]
