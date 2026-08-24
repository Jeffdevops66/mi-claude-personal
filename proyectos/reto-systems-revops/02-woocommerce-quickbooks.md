# 🛒 2. WooCommerce + QuickBooks Online de Sensi Home (criterios 3 y 4 de la evaluación)

> **Objetivo:** Que para el 16 de septiembre Jeffrey sea el dueño total de la tienda online (WooCommerce en mysensihome.com) y del sistema de contabilidad (QuickBooks Online): que pueda manejar productos, precios y órdenes sin ayuda de Miguel, que entienda y documente cómo se conecta la tienda con inFlow, y que QuickBooks funcione con reportes automáticos que Miguel ya aprobó y una división clara de trabajo con el bookkeeper. Jeffrey NO tiene que ser contador ni programador: su trabajo es administrar los sistemas, cuidar las conexiones y sacar los reportes.

---

## 🔍 Auditoría inicial — verifica esto ANTES de empezar

No asumas que algo está hecho. Verifícalo con tus propios ojos y marca la casilla.

- [ ] **¿Ya puedo entrar como administrador a la tienda (WordPress/WooCommerce)?**
  - 👀 Cómo verificarlo: Abre https://mysensihome.com/wp-admin en el navegador e intenta entrar con tu email de trabajo. Si no tienes usuario o te da error, anota 'FALTA ACCESO' — lo pedirás en el handover con Miguel.
- [ ] **¿Ya puedo entrar a QuickBooks Online?**
  - 👀 Cómo verificarlo: Abre https://qbo.intuit.com e intenta entrar con jeffrey@mysensihome.com. Si no tienes invitación, anota 'FALTA ACCESO'. Ojo: pide rol de 'Administrador de la empresa' (Company admin), no solo 'ver reportes'.
- [ ] **¿Existe HOY una conexión activa entre WooCommerce e inFlow? ¿Con qué herramienta?**
  - 👀 Cómo verificarlo: Entra a inFlow (web) > icono de engranaje > Integrations y mira si aparece WooCommerce conectado. Si no aparece, revisa en Zapier si hay zaps con 'WooCommerce' en el nombre. Si tampoco, pregúntale a Miguel: '¿Cómo pasan hoy las órdenes de la tienda a inFlow: automático o a mano?'
- [ ] **¿Sé quién es el bookkeeper, su contacto y qué días trabaja?**
  - 👀 Cómo verificarlo: Busca en tu email la palabra 'bookkeeper' o 'QuickBooks'. Si no encuentras nada, agrégalo como pregunta obligatoria del handover: nombre, email, días/horas que trabaja, y qué hace exactamente cada mes.
- [ ] **¿Existe documentación previa de la tienda o de QuickBooks?**
  - 👀 Cómo verificarlo: Busca en Google Drive / OneDrive / el repo de GitHub las palabras: 'WooCommerce', 'tienda', 'QuickBooks', 'QBO', 'bookkeeper'. Anota qué existe (aunque sea viejo) para no documentar desde cero.
- [ ] **¿Miguel ya revisa algún reporte de QuickBooks cada mes? ¿Cuál?**
  - 👀 Cómo verificarlo: Pregunta directa a Miguel (puede ser por mensaje): '¿Qué números de QuickBooks miras hoy cada mes y quién te los manda?'. La respuesta define qué reportes vas a automatizar.
- [ ] **¿La tienda WordPress tiene copias de seguridad (backups)?**
  - 👀 Cómo verificarlo: Cuando tengas acceso a wp-admin: menú Plugins > busca palabras como 'backup', 'UpdraftPlus', 'Jetpack'. Si no hay nada, pregunta a Miguel si el hosting hace backups. Esto es CRÍTICO antes de tocar cualquier cosa de la tienda.

---

## ✅ Tareas semana a semana

### 📌 Semana 1: Auditoría de accesos: ¿qué tengo y qué me falta?

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Abre un documento nuevo llamado 'estado-woo-qbo.md' (en tu repo o Drive).
2. Haz los 7 checks de la auditoría inicial, uno por uno.
3. Para cada check escribe: VERDE (lo tengo), AMARILLO (a medias), ROJO (no lo tengo).
4. Al final escribe la lista exacta de cosas que le vas a pedir a Miguel.

📦 **Entregable:** Documento 'estado-woo-qbo.md' con semáforo de los 7 checks y lista de pedidos para Miguel.

### 📌 Semana 1: Pedir la reunión de handover a Miguel (con agenda incluida)

⏱️ **Tiempo estimado:** 30 min

**Pasos:**
1. Copia la plantilla 'Agenda de handover con Miguel' (está abajo en plantillas).
2. Pega tu lista de faltantes de la auditoría en la sección de accesos.
3. Envíasela a Miguel por email o WhatsApp proponiendo 2 fechas concretas de la semana del 13-19 de julio.
4. Ponla en el calendario apenas confirme.

📦 **Entregable:** Reunión de handover agendada en calendario con agenda enviada.

### 📌 Semana 2: Reunión de handover con Miguel (WooCommerce + QuickBooks)

⏱️ **Tiempo estimado:** Reunión 60-90 min con Miguel (bloque especial, no cuenta como tu hora de estudio)

**Pasos:**
1. Sigue la agenda punto por punto (plantilla abajo).
2. Objetivo #1: salir de la reunión CON los accesos creados (que Miguel los cree ahí mismo, no 'después').
3. En WordPress: pide usuario propio con rol 'Administrador' (no compartir el de Miguel).
4. En QuickBooks: pide que te invite como 'Administrador de la empresa' desde Configuración > Administrar usuarios.
5. Pregunta y ANOTA: ¿cómo se conecta la tienda con inFlow?, ¿quién toca la tienda hoy?, ¿quién es el bookkeeper y qué hace?, ¿qué reportes mira Miguel?
6. Toma notas y guárdalas en 'notas-handover-woo-qbo.md'.

📦 **Entregable:** Accesos admin a WordPress y QuickBooks funcionando + notas de la reunión guardadas.

### 📌 Semana 2: Guardar accesos en 1Password y probar login en frío

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Guarda las credenciales de WordPress y QuickBooks en tu bóveda de 1Password de Sensi Home.
2. Activa la verificación en dos pasos (MFA) en ambas cuentas si no la tienen.
3. Cierra sesión en todo y vuelve a entrar desde cero a wp-admin y a qbo.intuit.com para confirmar que funcionan.
4. Actualiza tu 'estado-woo-qbo.md': pon en VERDE lo que ya conseguiste.

📦 **Entregable:** Credenciales en 1Password con MFA activo y login verificado en ambos sistemas.

### 📌 Semana 3: Tour de WordPress/WooCommerce SIN tocar nada

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Entra a wp-admin y recorre el menú de izquierda: Productos, Pedidos (Orders), Plugins, Ajustes de WooCommerce.
2. En Plugins: haz una captura de pantalla de la lista completa de plugins activos.
3. Identifica cuál plugin (o conexión) habla con inFlow — anótalo aunque no lo entiendas todavía.
4. Regla de oro esta semana: SOLO MIRAR. No actives, desactives ni actualices nada.
5. Escribe un mini-mapa: 'dónde están los productos, dónde las órdenes, dónde los precios'.

📦 **Entregable:** Captura de plugins activos + mini-mapa del admin en tus notas.

### 📌 Semana 3: Ver los videos oficiales de WooCommerce 101

⏱️ **Tiempo estimado:** 1-2 sesiones de 1h

**Pasos:**
1. Abre https://woocommerce.com/document/woocommerce-101-video-series/
2. Mira los videos de: agregar productos, gestionar pedidos, y ajustes generales (puedes saltarte los de pagos/envíos por ahora).
3. Mientras miras, ten abierta tu tienda real en otra pestaña y ubica cada cosa que muestran.
4. Anota 3 dudas que te queden para preguntar o investigar después.

📦 **Entregable:** Videos clave vistos + lista de 3 dudas anotadas.

### 📌 Semana 3: Mapear el flujo WooCommerce ↔ inFlow (versión 1)

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Copia la plantilla 'Mapa del flujo Woo↔inFlow' (abajo).
2. Responde con lo que sabes hasta ahora: ¿dónde se crean los productos primero?, ¿quién manda en el stock?, ¿qué pasa paso a paso cuando un cliente compra?
3. Lee la página oficial de la integración: https://www.inflowinventory.com/integrations/woocommerce para entender qué DEBERÍA sincronizarse.
4. Marca con '???' todo lo que no sepas — esas son tus preguntas para Miguel o para probar.

📦 **Entregable:** Documento 'mapa-flujo-woo-inflow.md' versión 1 (con huecos marcados).

### 📌 Semana 4: Practicar catálogo en modo seguro (producto de prueba)

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Confirma primero que existe backup de la tienda (check de la auditoría). Si no hay, pídelo antes de seguir.
2. En wp-admin > Productos > Añadir nuevo: crea un producto llamado 'PRUEBA JEFFREY - NO COMPRAR' y déjalo en estado 'Borrador' (draft), nunca publicado.
3. Practica: cambiar precio, cambiar foto, cambiar stock, cambiar descripción.
4. Revisa en inFlow si ese producto de prueba apareció o no — eso te dice cómo funciona la sync en la dirección Woo→inFlow.
5. Borra el producto de prueba al terminar (o déjalo en borrador documentado).
6. Escribe la mini-guía 'cómo editar un producto' con capturas.

📦 **Entregable:** Mini-guía 'como-editar-producto-woo.md' + aprendizaje real de qué sincroniza y qué no.

### 📌 Semana 4: Seguir una orden real de punta a punta ('la vida de una orden')

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Elige una orden reciente en WooCommerce > Pedidos.
2. Síguela por cada sistema: ¿apareció en inFlow?, ¿se creó factura?, ¿llegó algo a HubSpot o QuickBooks?
3. Anota CADA paso en orden: quién lo hace (persona o robot), en qué sistema, y cuánto tarda.
4. Actualiza tu 'mapa-flujo-woo-inflow.md' con lo que descubriste — borra los '???' que ya resolviste.

📦 **Entregable:** Documento 'vida-de-una-orden.md' + mapa de flujo versión 2 (mucho más completo).

### 📌 Semana 5: Tour de QuickBooks Online SIN tocar asientos contables

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Entra a qbo.intuit.com y recorre: Panel (Dashboard), Ventas > Facturas, Gastos, Informes (Reports).
2. Mira 10-15 min de tutoriales oficiales en https://quickbooks.intuit.com/tutorials/ (los de 'getting around' y 'reports').
3. Regla de oro: NO edites transacciones, NO borres nada, NO toques el plan de cuentas. Eso es territorio del bookkeeper.
4. Anota: ¿qué facturas entran solas (de la tienda o inFlow) y cuáles se meten a mano?

📦 **Entregable:** Notas del tour de QBO + lista de qué entra automático vs. manual.

### 📌 Semana 5: Reunión con el bookkeeper: ¿quién hace qué?

⏱️ **Tiempo estimado:** Reunión 30 min + 30 min para pasar en limpio

**Pasos:**
1. Agenda 30 min con el bookkeeper (contacto que te dio Miguel en el handover).
2. Copia la plantilla 'Matriz quién-hace-qué' (abajo) y llénala CON él/ella en la llamada.
3. Preguntas clave: ¿qué haces tú cada mes y qué días?, ¿qué necesitas de mí?, ¿qué se atora hoy?, ¿cómo te aviso de cosas nuevas?
4. Acuerden un check-in fijo (ej. 15 min cada 2 semanas) y ponlo en el calendario.

📦 **Entregable:** Matriz quién-hace-qué v1 llena + check-in recurrente agendado.

### 📌 Semana 6: Configurar los 3 reportes que Miguel revisará cada mes

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. En QBO ve a Informes (Reports) y abre: 1) Pérdidas y Ganancias (Profit and Loss) mensual, 2) Ventas por producto/servicio, 3) Cuentas por cobrar vencidas (A/R Aging).
2. Personaliza cada uno (rango: mes anterior) y usa 'Guardar personalización' (Save customization).
3. Programa el envío automático: en el reporte guardado, opción de email programado (Set email schedule), destinatario Miguel + tú, día 3 de cada mes.
4. Envíate una prueba a ti mismo para verificar que llega y se lee bien.

📦 **Entregable:** 3 reportes guardados y programados para llegar solos por email cada mes.

### 📌 Semana 6: Revisar los reportes con Miguel y conseguir su OK

⏱️ **Tiempo estimado:** Reunión 30 min con Miguel (o async por email)

**Pasos:**
1. Muéstrale a Miguel los 3 reportes (puede ser en 20-30 min o por email con capturas).
2. Pregunta exacta: '¿Esto es lo que quieres ver cada mes? ¿Qué le falta o le sobra?'
3. Ajusta lo que pida y reprograma el envío.
4. Guarda su respuesta de aprobación (email o mensaje) — es EVIDENCIA para el 16-sep.

📦 **Entregable:** Reportes aprobados por Miguel, con su OK guardado por escrito.

### 📌 Semana 7: Documentar proceso: catálogo y precios en WooCommerce

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Copia la plantilla 'Documento de proceso' (abajo).
2. Escribe el proceso completo: cómo crear un producto, cambiar precio, cambiar stock, y qué pasa con inFlow en cada caso.
3. Incluye capturas de pantalla de cada paso (tecla Windows + Shift + S para recortar).
4. Súbelo a tu repo/Drive en la carpeta de procesos y ponle versión y fecha.

📦 **Entregable:** Documento 'proceso-catalogo-precios-woo.md' terminado y publicado.

### 📌 Semana 7: Documentar proceso: órdenes y sincronización Woo↔inFlow

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Con la misma plantilla, documenta: qué pasa cuando entra una orden, qué revisar cada día, qué hacer si la sync falla (a quién avisar, qué pantalla mirar).
2. Incluye tu diagrama final del flujo Woo↔inFlow (versión 2 del mapa).
3. Agrega una sección 'Si algo sale mal' con los 3 problemas más probables y su solución.
4. Publícalo junto al anterior.

📦 **Entregable:** Documento 'proceso-ordenes-sync-woo-inflow.md' con diagrama y plan de emergencia.

### 📌 Semana 8: Documentar proceso: QuickBooks y cierre mensual con el bookkeeper

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Documenta: qué hace Jeffrey en QBO (usuarios, reportes, conexiones), qué hace el bookkeeper (transacciones, conciliación, impuestos), y el calendario del mes.
2. Pega la matriz quién-hace-qué final dentro del documento.
3. Manda el borrador al bookkeeper para que confirme que está bien ('¿esto refleja la realidad?').
4. Publícalo con los otros procesos.

📦 **Entregable:** Documento 'proceso-qbo-cierre-mensual.md' validado por el bookkeeper.

### 📌 Semana 8: Simulacro: 3 tareas al azar sin ayuda

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Sin mirar tus notas primero, haz estas 3 cosas midiendo el tiempo: 1) cambia el precio de un producto de prueba en Woo, 2) encuentra una orden específica y di en qué estado está en inFlow, 3) saca el reporte de ventas del mes pasado en QBO.
2. Si te trabaste en algo, anótalo: ese es un hueco en tu conocimiento o en tu documentación.
3. Corrige el documento correspondiente para que la próxima vez sea obvio.

📦 **Entregable:** Simulacro completado + documentos corregidos donde hubo dudas.

### 📌 Semana 9: Semana de operación autónoma: cero preguntas a Miguel

⏱️ **Tiempo estimado:** Durante el trabajo normal + 15 min diarios de registro

**Pasos:**
1. Esta semana, todo lo que surja de la tienda o de QuickBooks lo resuelves tú (con tus docs), sin preguntarle a Miguel.
2. Lleva un registro simple: fecha, qué pasó, cómo lo resolviste, cuánto tardaste.
3. Si algo de verdad te supera, anótalo como 'incidencia' — pero intenta resolverlo primero con la documentación oficial y tus notas.

📦 **Entregable:** Registro 'semana-autonoma.md' con todo lo que manejaste solo (evidencia de ownership).

### 📌 Semana 9: Cerrar los huecos que encontró la semana autónoma

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Revisa tu registro: ¿qué te costó trabajo o no supiste hacer?
2. Para cada hueco: busca la respuesta en la documentación oficial (WooCommerce/QBO/inFlow) o pregúntale a soporte de la herramienta.
3. Actualiza tus 3 documentos de proceso con lo aprendido.

📦 **Entregable:** Documentos de proceso actualizados a versión final.

### 📌 Semana 10: Armar la carpeta de evidencia de los criterios 3 y 4

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Crea una carpeta 'evidencia-evaluacion' con una página índice.
2. Criterio 3 (WooCommerce): enlaza tus 2 documentos de proceso, el mapa de flujo, capturas de órdenes que manejaste, y el registro de la semana autónoma.
3. Criterio 4 (QBO): enlaza el documento de proceso, la matriz con el bookkeeper, capturas de los reportes automáticos y el OK de Miguel.
4. Usa la plantilla 'Checklist de evidencia 16-sep' (abajo) para no dejar nada fuera.

📦 **Entregable:** Carpeta de evidencia completa con checklist marcado.

### 📌 Semana 10: Pre-revisión con Miguel: '¿qué falta para el OK?'

⏱️ **Tiempo estimado:** Reunión 30 min con Miguel

**Pasos:**
1. Agenda 30 min con Miguel ANTES de la evaluación real.
2. Muéstrale la carpeta de evidencia de los criterios 3 y 4.
3. Pregunta exacta: 'Si la evaluación fuera hoy, ¿marcarías estos dos criterios como cumplidos? ¿Qué falta?'
4. Anota lo que pida y agéndalo para la semana 10-11.

📦 **Entregable:** Lista corta de ajustes finales pedidos por Miguel (o su OK adelantado).

### 📌 Semana 11: Repaso final y ensayo de demo en vivo

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Relee tus 3 documentos de proceso y el mapa de flujo.
2. Ensaya una demo de 10 minutos: 1) editar un producto en Woo, 2) mostrar una orden viajando a inFlow, 3) abrir los reportes automáticos de QBO y explicar qué mira Miguel.
3. Cronométrate: si puedes hacerla fluida y sin mirar notas, estás listo.
4. Deja la carpeta de evidencia abierta y a la mano para el 16-sep.

📦 **Entregable:** Demo de 10 min ensayada y evidencia lista para la evaluación.

---

## 📚 Recursos de aprendizaje

- **[WooCommerce 101 Video Series (oficial)](https://woocommerce.com/document/woocommerce-101-video-series/)** — video, ~2h en total (videos cortos de 3-10 min)
  - ¿Por qué?: Es el curso oficial y gratuito de WooCommerce. Videos cortos que enseñan productos, pedidos y ajustes — perfecto para no-programadores y para ver junto a tu tienda real.
- **[Documentación oficial de WooCommerce (gestión de productos y pedidos)](https://woocommerce.com/documentation/woocommerce/)** — documentación, Consulta puntual; ~3h si lees las secciones de productos y pedidos
  - ¿Por qué?: Es la fuente de la verdad cuando tengas una duda concreta ('¿cómo cambio el stock?'). Gratis y siempre actualizada.
- **[Learn WordPress (cursos gratuitos de WordPress.org)](https://learn.wordpress.org/)** — curso, 2-3h (solo los módulos de fundamentos del panel de administración)
  - ¿Por qué?: WooCommerce vive dentro de WordPress. Estos cursos gratis te enseñan lo básico del panel (usuarios, plugins, páginas) sin necesidad de programar.
- **[Tutoriales oficiales de QuickBooks Online](https://quickbooks.intuit.com/tutorials/)** — video, 2-3h (videos de 2-5 min por tema)
  - ¿Por qué?: Videos oficiales y gratuitos de Intuit. Enfócate en los de 'getting around' (moverse por QBO), reportes y usuarios — que es tu rol, no la contabilidad profunda.
- **[inFlow: integración con WooCommerce (oficial)](https://www.inflowinventory.com/integrations/woocommerce)** — documentación, 30-45 min
  - ¿Por qué?: Explica qué sincroniza inFlow con WooCommerce oficialmente (productos, stock, órdenes). Te sirve para comparar 'lo que debería pasar' con 'lo que pasa hoy' en tu tienda.
- **[Centro de soporte de inFlow](https://www.inflowinventory.com/support)** — documentación, Consulta puntual
  - ¿Por qué?: Ya dominas inFlow por el proyecto de HubSpot; aquí resuelves dudas específicas de la sync con la tienda sin depender de Miguel.
- **[Certificación QuickBooks ProAdvisor (opcional, gratuita)](https://quickbooks.intuit.com/accountants/training-certification/)** — curso, ~8-10h (hazla DESPUÉS del 16-sep o solo si te sobra tiempo)
  - ¿Por qué?: Certificación oficial y gratis de Intuit. No es necesaria para pasar la evaluación, pero es un extra que impresiona a Miguel y te da credencial formal en QBO. Opcional.

---

## ⚠️ Riesgos y cómo evitarlos

| Riesgo | Cómo evitarlo |
|--------|---------------|
| Miguel no entrega los accesos a tiempo (el handover se atrasa y todo el plan se corre). | Pedir la reunión por escrito en la semana 1 con dos fechas concretas, y en la reunión conseguir que los usuarios se creen AHÍ MISMO, no 'después'. Si a la semana 3 no hay acceso, decirle a Miguel claro: 'sin esto no puedo cumplir los criterios 3 y 4 el 16-sep'. |
| Romper la tienda en producción (es la tienda real con clientes reales). | Regla de oro: primero solo mirar (semana 3), luego practicar solo con productos en 'Borrador' (semana 4). Verificar que existe backup ANTES de tocar nada. Nunca actualizar/desactivar plugins sin preguntar primero qué hacen. |
| La sincronización Woo↔inFlow es frágil o nadie sabe bien cómo funciona, y un cambio la rompe. | Mapear el flujo completo ANTES de tocar nada (tareas de semanas 3-4). Documentar quién es la 'fuente de la verdad' de cada dato (¿el stock manda inFlow o Woo?). Probar siempre con un producto de prueba, nunca con productos reales. |
| Meterse en terreno de contador y dañar los libros de QuickBooks. | Jeffrey administra el SISTEMA (usuarios, reportes, conexiones); el bookkeeper maneja la CONTABILIDAD (transacciones, conciliación). Esta división queda por escrito en la matriz quién-hace-qué y validada por el bookkeeper. Regla: en QBO no se borra ni edita ninguna transacción. |
| El bookkeeper part-time no responde o no colabora. | Agendar el check-in recurrente desde la primera llamada (semana 5) y acordar el canal (email/WhatsApp). Si no responde en 2 intentos, avisar a Miguel — coordinar al bookkeeper es parte del criterio 4, así que el bloqueo debe quedar visible. |
| La hora diaria de estudio se reparte entre varias áreas y esta se queda corta. | Lo urgente aquí es lo que depende de OTROS: handover con Miguel (semana 2) y llamada con bookkeeper (semana 5). Esas dos cosas no se mueven; el estudio de videos sí puede flexibilizarse una semana si hace falta. |
| Datos duplicados o descuadrados entre WooCommerce, inFlow y QuickBooks (ya pasó con inFlow-HubSpot). | Aplicar la lección aprendida del proyecto UUID: definir en el mapa de flujo una sola 'fuente de la verdad' por dato (productos, stock, órdenes, facturas) y verificar con una orden real de punta a punta antes de confiar en la sync. |

---

## 🎯 Lo que te evalúan el 16-sep en esta área

- [ ] Demo en vivo de WooCommerce: Jeffrey entra como admin y muestra sin ayuda cómo crear/editar un producto, cambiar un precio y revisar una orden — Miguel puede pedirle cualquier tarea al azar y la hace.
- [ ] Documento del flujo WooCommerce↔inFlow publicado (con diagrama), que explica qué se sincroniza, en qué dirección y qué hacer si falla — aprobado por Miguel.
- [ ] Registro de al menos 2-4 semanas operando la tienda de forma autónoma: órdenes revisadas y problemas resueltos SIN escalar a Miguel (el archivo 'semana-autonoma.md' es la prueba).
- [ ] Acceso admin a QuickBooks Online activo, guardado en 1Password con MFA, y demo en vivo de cómo sacar cualquier reporte que Miguel pida.
- [ ] Los 3 reportes mensuales (Pérdidas y Ganancias, Ventas, Cuentas por cobrar) llegan solos por email a Miguel cada mes, con su aprobación del formato guardada por escrito.
- [ ] Matriz 'quién hace qué' con el bookkeeper firmada/confirmada por ambos, y al menos 2 check-ins realizados con él/ella antes del 16-sep.
- [ ] Tres documentos de proceso publicados y actualizados: catálogo/precios en Woo, órdenes/sync Woo↔inFlow, y QBO/cierre mensual — esto además suma directo al criterio 10 (cero workflows sin documentar).

---

## 📄 Plantillas listas para copiar y usar

### 📋 Agenda de handover con Miguel (WooCommerce + QuickBooks, 60-90 min)

````
# Handover WooCommerce + QuickBooks — Jeffrey y Miguel

**Fecha:** ___ | **Duración:** 60-90 min | **Meta:** salir con accesos creados y funcionando

## 1. Accesos (20 min) — se crean EN la reunión
- [ ] WordPress: crear usuario admin para jeffrey@mysensihome.com (Usuarios > Añadir nuevo > rol Administrador)
- [ ] QuickBooks: invitar a Jeffrey como Administrador de la empresa (Configuración > Administrar usuarios)
- [ ] Verificar que Jeffrey puede entrar a ambos AHORA, antes de seguir

## 2. WooCommerce (20 min)
- ¿Quién toca la tienda hoy (productos, precios, órdenes)?
- ¿Cómo se conecta con inFlow? ¿Plugin, Zapier, a mano?
- ¿Quién manda en el stock: inFlow o la tienda?
- ¿Hay backups? ¿Quién es el proveedor de hosting?
- ¿Hay algo que NUNCA deba tocar?

## 3. QuickBooks (20 min)
- ¿Quién es el bookkeeper? Nombre, contacto, días que trabaja
- ¿Qué hace el bookkeeper y qué esperas que haga yo?
- ¿Qué números miras cada mes y quién te los manda hoy?
- ¿Hay conexiones activas (banco, inFlow, tienda) con QBO?

## 4. Acuerdos y siguientes pasos (10 min)
- [ ] Fecha de mi primera llamada con el bookkeeper: ___
- [ ] Confirmación: a partir de hoy la tienda y QBO son responsabilidad de Jeffrey
- [ ] Próximo check-in: ___
````

### 📋 Documento de proceso (formato estándar)

````
# Proceso: [nombre del proceso]

**Dueño:** Jeffrey | **Versión:** 1.0 | **Última actualización:** [fecha]
**Sistemas que toca:** [WooCommerce / inFlow / QuickBooks / etc.]

## ¿Para qué sirve este proceso?
[1-2 frases simples: qué logra y cuándo se usa]

## ¿Quién hace qué?
| Paso | Quién | Sistema |
|------|-------|---------|
| 1. ... | Jeffrey / robot / bookkeeper | ... |

## Pasos exactos (con capturas)
1. Entrar a [URL] con [usuario]
2. Ir a [menú > submenú]
3. [acción exacta]
4. Verificar que [resultado esperado]

## Si algo sale mal
| Problema | Qué hacer | A quién avisar |
|----------|-----------|----------------|
| ... | ... | ... |

## Historial de cambios
- [fecha] v1.0 — creado por Jeffrey
````

### 📋 Matriz quién-hace-qué con el bookkeeper (QuickBooks)

````
# QuickBooks Online — ¿Quién hace qué?

**Acordado entre:** Jeffrey y [nombre bookkeeper] | **Fecha:** ___

| Tarea | Jeffrey | Bookkeeper | ¿Cuándo? |
|-------|:-------:|:----------:|----------|
| Administrar usuarios y accesos de QBO | ✅ | | Cuando haga falta |
| Conexiones de QBO con otras apps (banco, inFlow, tienda) | ✅ | | Cuando haga falta |
| Reportes automáticos para Miguel | ✅ | | Día 3 de cada mes |
| Registrar y clasificar transacciones | | ✅ | Semanal |
| Conciliación bancaria | | ✅ | Mensual |
| Cierre de mes | | ✅ | Antes del día ___ |
| Impuestos | | ✅ | Según calendario |
| Avisar de facturas raras o duplicadas | ✅ | ✅ | Al detectarlas |

**Check-in recurrente:** cada ___ semanas, ___ min, por [canal]
**Regla de oro:** Jeffrey NO edita ni borra transacciones; el bookkeeper NO cambia usuarios ni conexiones sin avisar.
````

### 📋 Mapa del flujo WooCommerce ↔ inFlow (para llenar)

````
# Mapa de flujo: WooCommerce ↔ inFlow ↔ QuickBooks

**Versión:** ___ | **Fecha:** ___

## Fuente de la verdad (¿quién manda en cada dato?)
| Dato | Manda... | Se copia a... | ¿Cómo? (plugin/Zapier/a mano) |
|------|----------|---------------|-------------------------------|
| Catálogo de productos | ??? | ??? | ??? |
| Precios al cliente | ??? | ??? | ??? |
| Stock / inventario | ??? | ??? | ??? |
| Órdenes de venta | ??? | ??? | ??? |
| Facturas | ??? | ??? | ??? |

## La vida de una orden (paso a paso)
1. Cliente compra en mysensihome.com → se crea orden en WooCommerce
2. ??? (¿pasa sola a inFlow? ¿alguien la copia?)
3. ??? (¿se descuenta stock? ¿dónde?)
4. ??? (¿se factura en QBO? ¿quién?)
5. ??? (¿llega algo a HubSpot?)

## Preguntas abiertas (los '???' pendientes)
- [ ] ...

**Regla:** no tocar ninguna conexión hasta que este mapa esté completo y sin '???'.
````

### 📋 Checklist de evidencia 16-sep (criterios 3 y 4)

````
# Evidencia para la evaluación — Criterios 3 y 4

## Criterio 3: Ownership de WooCommerce
- [ ] Acceso admin propio funcionando (captura de wp-admin con mi usuario)
- [ ] Documento: proceso de catálogo y precios (link)
- [ ] Documento: proceso de órdenes y sync con inFlow, con diagrama (link)
- [ ] Registro de semana(s) autónoma(s): órdenes manejadas sin ayuda (link)
- [ ] Demo de 10 min ensayada (producto + orden + sync)

## Criterio 4: Ownership de QuickBooks Online
- [ ] Acceso admin funcionando, en 1Password con MFA (captura)
- [ ] Matriz quién-hace-qué confirmada por el bookkeeper (link)
- [ ] Al menos 2 check-ins hechos con el bookkeeper (fechas: ___, ___)
- [ ] 3 reportes automáticos llegando a Miguel cada mes (captura del email)
- [ ] OK de Miguel al formato de reportes, por escrito (link/captura)
- [ ] Documento: proceso QBO y cierre mensual (link)

## Extra que suma al criterio 10 (documentación total)
- [ ] Los 3 documentos de proceso están en la carpeta oficial, con versión y fecha
````

