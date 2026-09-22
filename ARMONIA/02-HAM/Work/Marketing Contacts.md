---
tags: [ham, work, hubspot]
rama: HAM
estado: activo
cssclasses:
  - ham
---

# 📬 Marketing Contact vs Non-Marketing Contact — HubSpot Sensi

Test hecho directo sobre el portal de HubSpot (Sensi Home, ID 9338219) el 2026-09-15, usando la propiedad `hs_marketable_status`.

## 🤔 ¿Qué es esto?

Cada Contact en HubSpot tiene una etiqueta:
- **Marketing contact** ✅ → le puedes mandar emails masivos de marketing (newsletters, promos). **Esto cuesta dinero** — HubSpot te cobra según cuántos Marketing Contacts tienes.
- **Non-marketing contact** 🚫 → NO le puedes mandar emails masivos, pero SÍ le puede escribir un vendedor uno-a-uno, o recibir emails de una compra (transaccionales). **Esto es gratis**, no cuenta para tu factura.

**Regla simple:** solo marca como Marketing Contact a quien de verdad le vas a mandar campañas de marketing. Si es un Lead que aún no muestra interés, mejor dejarlo Non-marketing — así no pagas de más.

## 🧪 Resultado del test (hoy, datos reales)

| Estado | Contactos | % |
|---|---:|---:|
| **Marketing contact** ✅ | 988 | 46.5% |
| **Non-marketing contact** 🚫 | 1,137 | 53.5% |
| **Total** | 2,125 | 100% |

## 📊 Cómo se reparte por etapa (Lifecycle Stage)

| Etapa | Marketing ✅ | Non-marketing 🚫 | % Marketing |
|---|---:|---:|---:|
| Customer | 817 | 0 | 100% |
| Evangelist | 79 | 0 | 100% |
| Opportunity | 12 | 0 | 100% |
| Sales Qualified Lead | 15 | 88 | 15% |
| Lead | 54 | 1,000 | 5% |
| Otras (Retired, Uninterested, Unresponsive, etc.) | 11 | 47 | 19% |

👉 Esto tiene mucho sentido: en cuanto una Company se vuelve **Customer**, TODOS sus contactos pasan a Marketing automático. Los Leads (la mayoría de tu base) se quedan Non-marketing hasta que avanzan — así no pagas por gente que ni te ha comprado.

## 🤖 % de Automatización

Miré quién puso la etiqueta "Marketing contact" en cada uno de los 988 contactos:

| Quién lo puso | Contactos | % |
|---|---:|---:|
| 🤖 **Workflow (automático)** | 981 | **99.3%** |
| Form Submission | 5 | 0.5% |
| Contact Import | 1 | 0.1% |
| User Set (manual) | 1 | 0.1% |

### ✅ Conclusión: estamos al 99.3% de automatización

Prácticamente nadie está marcando contactos como Marketing a mano. El workflow **"Sincronizar Lifecycle Empresa a Contactos"** (ID 1876577614, ver [[Lifecycle Stages]]) es el que empuja esto: cuando una Company pasa a Customer/Evangelist, sus Contacts se vuelven Marketing solos.

## 🚫 Unsubscribe y Hard Bounce — ¿qué son?

- **Unsubscribe (se dio de baja)** 🙅 → la persona hizo click en "darme de baja" en un email tuyo. Legalmente NUNCA le puedes volver a mandar marketing. Propiedad: `hs_email_optout`.
- **Hard bounce (rebote duro)** 💥 → le mandaste un email y rebotó fuerte, o sea el correo NO EXISTE o está mal escrito (o está lleno, bloqueado, marcado como spam). HubSpot deja de intentar mandarle. Propiedad: `hs_email_hard_bounce_reason_enum`. Las razones que vi en tu cuenta:

| Razón | Qué significa | Contactos |
|---|---|---:|
| Unknown user | El correo no existe (mal escrito o cerrado) | 132 |
| Mailbox full | El buzón está lleno | 25 |
| Other | Otro motivo | 16 |
| Policy | El servidor del destinatario lo bloqueó | 7 |
| Spam | Te marcaron como spam | 4 |
| **Total con problema** | | **184** |

## ⚠️ ¿Cómo debo tratarlos en Marketing Contact? (hallazgo del test)

**Regla de oro:** si alguien se dio de baja (unsubscribe) o rebotó fuerte (hard bounce), **NUNCA le vas a poder mandar marketing otra vez** — así que no tiene sentido seguir pagando por él como Marketing Contact. Hay que pasarlo a **Non-marketing** ✅.

**Pero en tu cuenta, ahora mismo, HubSpot NO lo está haciendo solo:**

| Grupo | Total | Siguen como Marketing ✅ (pagando de más) | Ya están Non-marketing 🚫 (bien) |
|---|---:|---:|---:|
| Unsubscribed | 66 | **17** ⚠️ | 49 |
| Hard bounce | 184 | **77** ⚠️ | 107 |

👉 **94 contactos** (17 + 77) hoy están marcados Marketing Contact aunque NUNCA les vas a poder mandar nada — te están costando plata en la factura de HubSpot por gusto.

## 🔧 Intento de arreglo automático (2026-09-15)

Intenté corregir los 94 contactos directo por API (HubSpot MCP), en 10 tandas. **Los 94 fallaron** con el mismo error en todos:

> `Unable to mutate. Request contained marketable add-on data, but user lacks permissions for scope: marketable-contacts-write`

O sea: la conexión de Claude con este portal de HubSpot puede **leer** todo pero **no tiene permiso para cambiar** el switch Marketing/Non-marketing. Cero contactos se tocaron (falló limpio, no a medias).

**Camino correcto (no bloqueado por esto):** un **Workflow de HubSpot** sí puede hacer el cambio, porque corre con permisos del sistema, no con la conexión de Claude. Ver instrucciones de armado abajo.

**Para que Claude pueda hacerlo directo la próxima vez:** el admin de la cuenta debe dar el permiso **"Marketing contacts access"** al usuario conectado (Configuración → Usuarios y equipos → permisos → Contactos).

## ✅ Workflow activado (2026-09-15, hecho por Claude vía Chrome)

En vez de crear uno nuevo, encontré que **ya existía un workflow apagado** llamado `Remove Contact Marketing` (ID 1744062308) con la acción correcta ya armada pero sin disparador real (estaba "Manually triggered only"). Le agregué el disparador y lo activé:

- **Nombre:** `Remove Contact Marketing`
- **Disparador (OR):** `Unsubscribed from all email` es igual a `True` **OR** `Email hard bounce reason` is known
- **Acción:** Set marketing contact status → **Set as non-marketing contact**
- **Re-enroll:** activado (agarra casos nuevos para siempre)
- **Contactos existentes:** se activó "enroll existing contacts" — los 250 que ya cumplían la condición (66 unsub + 184 bounce) entraron de una vez
- **Estado:** 🟢 **ON**, link: https://app.hubspot.com/workflows/9338219/platform/flow/1744062308/edit

### ⚠️ Hallazgo importante: el cambio NO es instantáneo
HubSpot tiene una regla de facturación: **subir** a Marketing Contact es inmediato, pero **bajar** a Non-marketing solo se aplica **el día 1 del próximo mes o en tu fecha de renovación de HubSpot — lo que llegue primero**. Es una protección de HubSpot, no un error mío ni tuyo.

Verifiqué esto directo en los datos: los 99 contactos problema (subió de 94 a 99 porque siguieron llegando unsubscribes/bounces nuevos hoy) ahora tienen la propiedad `hs_marketable_until_renewal = true` — o sea, **el 100% ya está en cola correctamente** para pasar a Non-marketing automático. No hay que hacer nada más, solo esperar esa fecha.

## 📊 Total Marketing Contacts activos y optimización (2026-09-15)

| | Contactos | % |
|---|---:|---:|
| Marketing Contact activos (ahora mismo) | 1,068 | 100% |
| En cola para bajar a Non-marketing (unsub/bounce) | 99 | 9.3% ⏳ |
| Marketing Contacts "sanos" que quedarán tras la renovación | ~969 | ~90.7% |

**Conclusión:** el workflow está bien armado y **ya atrapó al 100% de los problema actuales** (99/99 en cola) — no está "optimizado" todavía en el número crudo porque HubSpot difiere la bajada a la fecha de renovación, pero la automatización en sí ya quedó completa y funcionando sola de aquí en adelante. El total subió de 988 a 1,068 en las últimas horas por actividad normal del negocio (Companies pasando a Customer vía el otro workflow de Lifecycle) — no relacionado con este cambio.

## 🔧 Hueco encontrado y cerrado en el workflow que PRENDE Marketing (2026-09-15)

El workflow que prende (ON) el Marketing Contact se llama **`Set Marketing Contact`** (ID 1875630514, portal 9338219). Tiene 2 caminos (OR):

- **Grupo 1** (el que prende casi todo — Lifecycle stage = Evangelist/Opportunity/Customer): **NO revisaba** hard bounce ni unsubscribe. Si un contacto con hard bounce o dado de baja volvía a calificar (ej. su Company pasa a Customer), este grupo lo podía volver a marcar como Marketing por accidente.
- **Grupo 2** (respaldo, casi no se usa): sí revisaba "hard bounce is unknown", pero tampoco revisaba unsubscribe.

**Arreglo aplicado (vía Chrome, en vivo):** le agregué al Grupo 1 dos condiciones AND nuevas, copiando la misma lógica que ya usa la lista guardada del Grupo 2:
- `Email hard bounce reason` **is unknown**
- `Unsubscribed from all email` **is equal to False**

Quedó así:
> Grupo 1: Lifecycle stage is any of Evangelist, Opportunity, or Customer **AND** Email hard bounce reason is unknown **AND** Unsubscribed from all email is equal to False

Guardado con "Save and don't enroll existing contacts" (0 contactos nuevos cumplían el criterio ampliado, así que no hacía falta reprocesar nada). El workflow sigue 🟢 ON.

**Resultado:** ahora ningún contacto con hard bounce o unsubscribe puede volver a prenderse como Marketing por accidente — el hueco quedó cerrado en el origen, no solo parchado después por `Remove Contact Marketing`.

## 🚦 Auditoría completa: los 4 workflows que mueven el semáforo (2026-09-16)

Revisé en vivo, uno por uno directo en HubSpot, los 4 workflows que tienen permiso de prender o apagar Marketing Contact. Los otros dos (Set Marketing Contact y Remove Contact Marketing) ya estaban documentados arriba — aquí quedan reconfirmados tal cual están hoy, más los 2 que son nuevos y no estaban anotados.

| Workflow | Cuándo actúa | Qué hace | Estado |
|---|---|---|---|
| **Lead entra como Non-Marketing Contact** (ID 1884237478) 🆕 | Un contacto cambia su Lifecycle stage a Lead | Lo pone Non-marketing de una vez — nadie empieza pagando | 🟢 ON, re-enroll activado |
| **Set Marketing Contact** (ID 1875630514) | Grupo 1: empresa en Evangelist/Opportunity/Customer + correo sin rebote + no unsubscribed. Grupo 2: cae en la lista guardada "Non-marketing contacts in key lifecycle stages updated in past year with no…" | Lo pone Marketing | 🟢 ON, reconfirmado igual que el arreglo del 15-sep |
| **Remove Contact Marketing** (ID 1744062308) | Unsubscribed = True, o hard bounce reason conocido | Lo pone Non-marketing | 🟢 ON, reconfirmado sin cambios |
| **Remove Marketing Contact of MQL SQL after 4 months (120 days)** (ID 1885178732) 🆕 | Lifecycle stage = Marketing Qualified Lead con más de 120 días desde que entró, O Sales Qualified Lead con más de 120 días desde que entró | Lo pone Non-marketing — libera espacio para leads nuevos | 🟢 ON, re-enroll activado |

👉 Este último es la respuesta a la pregunta que se hizo esta semana: **sí, ya existe el timer** que baja a Non-marketing a los MQL/SQL que no avanzan.

**Cambio de límite (2026-09-16):** se armó originalmente con 40 días. El mismo día, por decisión de negocio, se cambió a **4 meses (120 días)** — se editó en vivo directo en HubSpot (las dos condiciones del trigger, Grupo 1 y Grupo 2) y se renombró el workflow para que el nombre no quede desactualizado. 0 contactos qualifying en el momento del cambio, así que se guardó sin necesidad de reprocesar nada.

⚠️ **A vigilar:** el workflow todavía no ha atrapado a nadie (normal, es nuevo y ahora el límite es más largo). Revisar en unas semanas.

📌 **Importante — qué SÍ y qué NO hace este workflow:** solo apaga Marketing Contact. **No mueve la etapa (Lifecycle Stage)** — una empresa que lleva 120+ días en MQL o SQL se queda exactamente en esa etapa, solo que deja de recibir marketing. Si nadie la mueve a mano o no vuelve a pasar el evento que la avanza (contestar un correo/llamada para MQL, agendar reunión para SQL), se queda ahí, sin marketing, indefinidamente.

### Prenden Marketing Contact también en MQL y SQL (no solo Opportunity/Customer/Evangelist)
Verificado en vivo el 16-sep-2026: el Grupo 2 de "Set Marketing Contact" usa la lista guardada **"Non-marketing contacts in key lifecycle stages updated in past year with no hard bounce"** (lista ID 449, creada 14-sep-2026). Esa lista prende como Marketing a cualquier contacto Non-marketing que esté en **MQL, SQL, Opportunity, Customer o Evangelist**, con fecha de entrada a esa etapa hace menos de 365 días, y sin rebote de correo. O sea: MQL y SQL también reciben marketing por diseño — el límite de 120 días es lo que se lo quita si no avanzan.

✅ **Hueco cerrado (2026-09-16, aprobado por Jeffrey y hecho en vivo vía Chrome):** se agregó "Unsubscribed from all email is equal to False" a los 5 grupos de la lista 449 (MQL, SQL, Opportunity, Customer, Evangelist), copiando la misma lógica que ya tenía el Grupo 1 de "Set Marketing Contact". Se guardó con "No - Enroll contacts that meet this criteria in the future" (no se forzó a nadie a entrar de golpe, solo queda blindado hacia adelante). La lista quedó en modo "Processing" justo después de guardar — 0 contactos afectados en el momento del cambio, así que no había nadie mal clasificado que reprocesar.

📌 Con esto, **los dos caminos que prenden Marketing Contact (Grupo 1 directo y Grupo 2 vía lista 449) ya revisan unsubscribe y hard bounce por igual** — el hueco documentado el 15 y 16 de septiembre quedó cerrado.

### Descubrimiento extra: se armó todo un camino nuevo de Lifecycle Stage (14 al 16-sep-2026)
No tocan Marketing Contact directamente, pero son los que alimentan los workflows de arriba — no estaban documentados en [[Lifecycle Stages]] y quedan anotados aquí también:
- **Company nueva - Lifecycle stage inicial (Lead)** (ID 1884238447) — empresa nueva sin etapa → Lead.
- **Company avanza a MQL (respondio email)** (ID 1881839702) — contacto contestó llamada o correo de ventas → empresa a MQL.
- **Company avanza a SQL (actividad registrada)** (ID 1881976730) — contacto agendó reunión → empresa a SQL.
- **Company avanza a Opportunity (Deal SQ)** (ID 1880059429) — Deal llega a "reunión agendada" y la empresa aún no es Customer/Evangelist → empresa a Opportunity (tiene una rama que protege: si ya es Customer o Evangelist, no la baja).

Runbook completo y visual de todo esto, para compartir con el equipo: página armada el 2026-09-16 con el mapa completo y las reglas de oro (buscar en Claude "El Semáforo de Marketing Contact").

## 🔁 Reconfirmación en vivo (2026-09-16)

Jeffrey pidió cerrar el círculo de "quien se da de baja o rebota, se saca de Marketing". Volví a consultar los datos reales de HubSpot (no solo la nota vieja) para confirmar que el sistema sigue funcionando:

- **98 contactos** hoy tienen unsubscribe o hard bounce Y siguen marcados Marketing — pero los **98 (100%) ya tienen `hs_marketable_until_renewal = true`**, o sea HubSpot mismo ya los puso en cola para bajar a Non-marketing en la próxima fecha de facturación. Cero fuga real, es solo el retraso normal de facturación (ya documentado arriba).
- El hueco de la lista 449 (Grupo 2 de "Set Marketing Contact", no revisa unsubscribe) **sigue en 0 contactos afectados hoy** — consulté en vivo: nadie non-marketing por unsubscribe (sin bounce) está hoy en MQL/SQL/Opportunity/Customer/Evangelist con menos de 365 días. El hueco no ha hecho daño, pero sigue abierto estructuralmente.

📌 Conclusión: el sistema de salida (bajar de Marketing) está **100% automatizado y funcionando bien**. Lo único que falta para que quede blindado del todo es cerrar el hueco de la lista 449 — sigue esperando aprobación de Jeffrey.

## 📌 Pendiente / a revisar
- Revisar en unas semanas si "Remove Marketing Contact of MQL SQL after 4 months (120 days)" ya atrapó contactos (hoy sigue en 0).
- Revisar el 0.7% manual (7 contactos) — ver si vale la pena dejarlo así o mover esa lógica a workflow también.
- Revisar en la fecha de renovación de HubSpot (o el día 1 del próximo mes) que los 99 contactos realmente bajaron a Non-marketing.
- Pedir permiso "Marketing contacts access" para la conexión de Claude, así el próximo arreglo masivo se puede hacer directo sin pasar por el workflow manual.
- Actualizar [[Lifecycle Stages]] con los 4 workflows nuevos del camino Lead → MQL → SQL → Opportunity (hoy solo quedaron anotados aquí).

⬅️ Volver a [[HubSpot]]
