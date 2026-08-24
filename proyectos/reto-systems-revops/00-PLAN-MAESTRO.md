# 🏆 PLAN MAESTRO — Reto Systems & RevOps Lead

> **Meta:** Pasar la evaluación del **16 de septiembre de 2026** cumpliendo los 10 criterios del contrato → tu tarifa sube de **$2,000 a $2,500/mes**.
>
> **Hoy es 6 de julio de 2026. Tienes 72 días. Con 1 hora al día, alcanza.**

---

## 🧭 Cómo funciona este plan (léelo una vez y ya)

1. **Cada día de lunes a sábado trabajas 1 hora** en lo que dice el cronograma de abajo. Nada más.
2. **Las reuniones (Miguel, Alejandro, Paola, bookkeeper, broker, MSPs) son BLOQUES ESPECIALES** — van aparte de tu hora diaria.
3. **Cada viernes envías el UPDATE SEMANAL a Miguel** (plantilla en el archivo 05). Sin excepción. Son 15 min extra.
4. **Cada área tiene su propio archivo** con el detalle completo: auditoría inicial, pasos, recursos, riesgos y plantillas.
5. **Marcas tu avance en [TRACKER.md](TRACKER.md)** — checkbox por semana. Si una semana se cae, el sábado siguiente se recupera lo crítico primero.
6. **Regla de oro: nunca asumas que algo está hecho.** La semana 1 es una auditoría total precisamente por eso.
7. **Desde el 7-jul hay una segunda capa: el ROL diario** (recomendaciones directas de Miguel): 30 min L-V de ronda con ojo de CEO (`/ronda-diaria`), auditoría cruzada Woo↔HubSpot↔inFlow los miércoles (`/auditoria-cruzada`) y barrido profundo el primer lunes del mes. Detalle completo en [06-rol-diario.md](06-rol-diario.md).

---

## 🎯 Los 10 criterios de la evaluación (y dónde se trabaja cada uno)

Esto es lo que Miguel va a revisar el 16-sep. Cada criterio tiene su archivo con el plan completo:

| # | Criterio (lo que dice el contrato) | Archivo del plan | Estado hoy |
|---|-----------------------------------|------------------|------------|
| 1 | Dominio total de **inFlow (Sensi Home)** — documentado, sin depender de Miguel | [01-hubspot-inflow.md](01-hubspot-inflow.md) | 🟡 Lo usas, falta documentar |
| 2 | Dominio total de **HubSpot** — pipeline, integraciones, handoff de Lina funcionando | [01-hubspot-inflow.md](01-hubspot-inflow.md) | 🟢 Sync UUID v2 vivo desde 4-jul; falta documentar |
| 3 | Dominio total de **WooCommerce** — catálogo, órdenes, sync con inFlow | [02-woocommerce-quickbooks.md](02-woocommerce-quickbooks.md) | 🔴 Falta handover de Miguel |
| 4 | Dominio total de **QuickBooks Online** — coordinación con el bookkeeper andando | [02-woocommerce-quickbooks.md](02-woocommerce-quickbooks.md) | 🔴 Falta handover de Miguel |
| 5 | **Sistemas Tektone iniciados** — production scheduling y órdenes operando | [04-tektone.md](04-tektone.md) | 🔴 Desde cero, con Alejandro |
| 6 | **Workflows de back-office de Karine** construidos y corriendo | [04-tektone.md](04-tektone.md) | 🔴 Por construir |
| 7 | **1Password desplegado** en todo el equipo (11 personas) | [03-it-seguridad.md](03-it-seguridad.md) | 🔴 Por desplegar |
| 8 | **MSP contratado** e infraestructura IT operando | [03-it-seguridad.md](03-it-seguridad.md) | 🔴 ⚠️ VENCIDO desde 1-jul |
| 9 | **Seguro cibernético activo** | [03-it-seguridad.md](03-it-seguridad.md) | 🔴 ⚠️ VENCIDO desde 1-jul |
| 10 | **Todos los procesos documentados** — cero workflows sin documentar | [05-documentacion-evaluacion.md](05-documentacion-evaluacion.md) | 🔴 Índice P-01 a P-18 por crear |

✅ **Auditoría de cobertura:** los 10 criterios tienen plan, semana asignada y entregable con evidencia. Los criterios 8 y 9 están VENCIDOS desde el 1-jul — por eso las semanas 1-3 los atacan primero.

---

## 📂 Archivos de este proyecto

| Archivo | Qué contiene |
|---------|--------------|
| **00-PLAN-MAESTRO.md** (este) | Visión general + cronograma de 11 semanas + hitos + reglas |
| [01-hubspot-inflow.md](01-hubspot-inflow.md) | HubSpot + inFlow Sensi: monitoreo del sync, documentación, dominio |
| [02-woocommerce-quickbooks.md](02-woocommerce-quickbooks.md) | Tienda online + contabilidad: handover, catálogo, bookkeeper, reportes |
| [03-it-seguridad.md](03-it-seguridad.md) | 1Password, MFA, MSP, seguro cyber, backups, auditoría de accesos |
| [04-tektone.md](04-tektone.md) | inFlow Tektone desde cero + workflows de Karine, con Alejandro y Paola |
| [05-documentacion-evaluacion.md](05-documentacion-evaluacion.md) | Los 18 SOPs (P-01 a P-18), dossier de evidencias y simulacro |
| [06-rol-diario.md](06-rol-diario.md) | El ROL de todos los días: ojo de CEO, ronda diaria, catálogo, experiencia web y auditoría cruzada (inFlow = fuente de verdad) |
| [semaforo-criterios.md](semaforo-criterios.md) | Semáforo vivo de los 10 criterios (se actualiza cada viernes) |
| [TRACKER.md](TRACKER.md) | Tu checklist semanal — aquí marcas el avance |

---

## 📅 Cronograma semana a semana (1 hora al día)

### 🗓️ Semana 1 (6-12 jul 2026) — Auditoría total: foto de partida

🎯 **Objetivo de la semana:** Saber el estado REAL de todo (nada de suponer): accesos, IT, Tektone y los 10 criterios. Salir de la semana con semáforos llenos, presupuesto IT aprobado y las reuniones clave agendadas.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 6 | Documentación | Armar la tabla semáforo v1 de los 10 criterios (verde/amarillo/rojo con responsable de cada rojo) y pedirle a Miguel UNA sola reunión esta semana con agenda de 3 puntos: confirmar criterios, aprobar presupuesto IT, y agendar el handover de WooCommerce+QuickBooks. |
| Mar 7 | IT y ciberseguridad | Llenar proyectos/it/inventario-it.md con las 12 respuestas y semáforo: ¿existe 1Password?, ¿hay MFA?, ¿hay backup?, ¿hay MSP?, ¿hay seguro?, ¿cuántas computadoras hay y de quién? |
| Mié 8 | WooCommerce + QBO | Auditoría de accesos: llenar estado-woo-qbo.md con el semáforo de los 7 checks (¿tengo login de WordPress?, ¿de QBO?, ¿quién es el bookkeeper?, etc.) y la lista exacta de pedidos para Miguel. |
| Mié 8 (BLOQUE ESPECIAL) | Reunión con Miguel | Reunión de 30-45 min: Miguel confirma los 10 criterios, aprueba el presupuesto IT POR ESCRITO (un email o WhatsApp con 'OK' basta), te da el contacto del broker de seguros, y queda agendado el handover Woo/QBO para el lunes 13. |
| Jue 9 | Tektone | Auditoría 'Tektone — Estado Real': responder los 8 checks (¿qué usan hoy para órdenes?, ¿cuántos productos?, ¿qué hace Karine?) y agendar la reunión con Alejandro (semana 2) y el check-in con Paola (semana 4), con agenda enviada. |
| Vie 10 | IT y ciberseguridad | Completar tabla-mfa.md de las 5 plataformas (quién tiene MFA y a quién le falta) + enviar el UPDATE SEMANAL #1 a Miguel (15 min extra; esto se repite TODOS los viernes hasta el 16-sep). |
| Sáb 11 | Documentación | Crear la 'casa' de la documentación en SharePoint: estructura de carpetas + índice maestro con los 18 procesos (P-01 a P-18) + compartirla con Miguel. |

🏁 **Hito de la semana:** LISTO: semáforos de las 4 áreas llenos, presupuesto IT aprobado por escrito, contacto del broker en mano, handover Woo/QBO y reunión con Alejandro agendados, casa de documentación creada.

### 🗓️ Semana 2 (13-19 jul 2026) — Destrabar lo vencido + handovers

🎯 **Objetivo de la semana:** Atacar lo que ya venció el 1-jul (seguro cyber y MSP) y recibir los dos handovers grandes: WooCommerce+QBO de Miguel y los requisitos de Tektone de Alejandro.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 13 | IT y ciberseguridad | Enviar el email al broker pidiendo cotización del seguro cibernético (con copia a Miguel) + crear recordatorio de seguimiento semanal. Con los 30 min restantes: preparar notas para la reunión con Alejandro viendo 2-3 videos de inFlow (inFlow Academy/soporte: https://www.inflowinventory.com/support — videos de 5-10 min c/u, gratis). |
| Lun 13 (BLOQUE ESPECIAL) | Reunión con Miguel | Handover de WooCommerce + QuickBooks (60-90 min): salir con accesos admin FUNCIONANDO en ambos sistemas + notas de la reunión guardadas. |
| Mar 14 | IT y ciberseguridad | Crear la cuenta de 1Password Teams con las 4 bóvedas (Sensi, Tektone, IT, Compartida) y tú como administrador. |
| Mar 14 (BLOQUE ESPECIAL) | Reunión con Alejandro | Levantamiento de requisitos Tektone (60 min): cómo fluyen las órdenes hoy, lista de productos comprometida, y próxima cita agendada. |
| Mié 15 | Tektone | Pasar la reunión a limpio: diagrama del flujo de órdenes + definir por escrito el MÍNIMO OPERATIVO + confirmar el plan de inFlow Tektone (o enviar la solicitud de aprobación a Paola con el costo claro). |
| Jue 16 | IT y ciberseguridad | Buscar y contactar 5-8 MSPs en Miami (proveedores de IT gestionado, $300-600/mes) y dejar llamadas agendadas para la semana 3. |
| Vie 17 | WooCommerce + QBO | Guardar los accesos de WordPress y QuickBooks en 1Password con MFA activo y probar login en frío en ambos + UPDATE SEMANAL #2. |
| Sáb 18 | Documentación | Documentar P-01: Sync inFlow↔HubSpot (tu proceso estrella, ya está en producción desde el 4-jul: UUID v2, zaps y workflows). Primera fila VERDE del índice. |

🏁 **Hito de la semana:** LISTO: accesos Woo/QBO en tu poder y en 1Password, cuenta 1Password Teams viva, broker contactado con recordatorio activo, 5-8 MSPs contactados, mínimo operativo de Tektone definido, P-01 documentado.

### 🗓️ Semana 3 (20-26 jul 2026) — 1Password al equipo + inFlow Tektone nace

🎯 **Objetivo de la semana:** Desplegar 1Password a los 11 empleados, hacer las primeras llamadas con MSPs, montar la base de inFlow Tektone y empezar a conocer WooCommerce sin romper nada.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 20 | IT y ciberseguridad | Invitar a los 11 empleados a 1Password + enviar el mensaje guía de 'cómo entrar en 3 pasos' + agendar mini-sesiones de ayuda de 15 min en la semana para los que se traben. |
| Mar 21 | Tektone | Configuración base de inFlow Tektone: datos de la empresa, impuestos y ubicación. Apóyate en las guías gratuitas de inFlow (https://www.inflowinventory.com/support, artículos de setup de 10-15 min). |
| Mar y Jue (BLOQUES ESPECIALES) | Llamadas MSP | Llamadas con MSP #1 y MSP #2 (45 min cada una): tomar notas completas y pedir propuesta por escrito a cada uno. |
| Mié 22 | WooCommerce + QBO | Tour de WordPress/WooCommerce SIN tocar nada: captura de los plugins activos + mini-mapa del admin en tus notas (dónde vive el catálogo, las órdenes y la config del sync). |
| Jue 23 | Tektone | Cargar los productos top 20 en inFlow Tektone por importación CSV y verificar que quedaron bien (nombres, precios, unidades). |
| Vie 24 | Tektone | Crear los 3-4 usuarios de inFlow Tektone con permisos correctos (nadie con más poder del que necesita) y guardar credenciales en la bóveda Tektone de 1Password + UPDATE SEMANAL #3. |
| Sáb 25 | WooCommerce + QBO | Ver los videos oficiales de WooCommerce 101 (documentación y videos gratis: https://woocommerce.com/documentation/ — 60-90 min en total) y anotar tus 3 dudas principales. |

🏁 **Hito de la semana:** LISTO: 11 invitaciones de 1Password enviadas, 2 llamadas MSP hechas con propuestas pedidas, inFlow Tektone configurado con 20 productos y usuarios, y ya conoces el mapa de WooCommerce.

### 🗓️ Semana 4 (27 jul - 2 ago 2026) — MFA en verde + propuestas MSP cerradas

🎯 **Objetivo de la semana:** Cerrar la seguridad básica (MFA + contraseñas migradas), tener las 3 propuestas de MSP en mano, probar la primera orden completa en Tektone y decidir cómo será el calendario de producción.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 27 | IT y ciberseguridad | Encender MFA donde falte en las 5 plataformas hasta que tabla-mfa.md quede toda en VERDE (o con la excepción de inFlow documentada) + guardar capturas en evidencias/. |
| Mar 28 | IT y ciberseguridad | Migrar las contraseñas compartidas de la empresa a las bóvedas de 1Password (que NO vivan en Excel ni en chats) + escribir la política de contraseñas de 1 página. |
| Mar 28 (BLOQUE ESPECIAL) | Llamadas MSP | Llamada con MSP #3 (45 min) + 2 llamadas cortas de cierre: conseguir las 3 propuestas escritas y verificar al menos 2 referencias. |
| Mié 29 | Tektone | Probar el flujo completo de una orden en inFlow Tektone de punta a punta (cotización → orden → factura) + primer borrador de la guía con capturas. |
| Mié 29 (BLOQUE ESPECIAL) | Reunión con Paola | Check-in de 20-30 min con Paola: informarla del avance de Tektone, acordar el formato de reporte y confirmar prioridades. |
| Jue 30 | WooCommerce + QBO | Practicar el catálogo en modo seguro (crear/editar un producto de PRUEBA) para aprender qué sincroniza con inFlow y qué no + mini-guía 'como-editar-producto-woo.md' + mapa de flujo Woo↔inFlow versión 1. |
| Vie 31 | Tektone | Decidir el método del calendario de producción (plan A: dentro de inFlow / plan B: hoja compartida alimentada por inFlow) + primera prueba del método elegido + UPDATE SEMANAL #4. |
| Sáb 1 | Documentación | Documentar P-02 (Handoff Lina→Bautista) y P-03 (Auto-asociación contactos→deals) en una sola sesión: los dos son de HubSpot y ya funcionan, solo hay que retratarlos con capturas. |

🏁 **Hito de la semana:** LISTO: MFA completo con evidencia, contraseñas viviendo solo en 1Password, 3 propuestas MSP en mano, orden de prueba Tektone funcionando, Paola alineada, criterio 2 casi todo documentado.

### 🗓️ Semana 5 (3-9 ago 2026) — Backblaze + comparativa MSP + entrar a QBO

🎯 **Objetivo de la semana:** Encender los respaldos en todas las computadoras, dejar la comparativa de MSPs lista para Miguel, entregarle el calendario de producción a Alejandro y entender QuickBooks con el bookkeeper.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 3 | IT y ciberseguridad | Backblaze Business: crear la cuenta con grupo y hacer el piloto en TU computadora (el backup corre solo después). |
| Mar 4 | Tektone | Construir la versión 1 del calendario de producción con las órdenes REALES de la semana cargadas. |
| Mié 5 | IT y ciberseguridad | Armar msp-comparativa.md: matriz de los 3 MSPs (precio, qué incluye, referencias, tiempo de respuesta) con tu recomendación, lista para presentar a Miguel. |
| Mié 5 (BLOQUE ESPECIAL) | Reunión con Alejandro | Sesión de 30-45 min: validar el calendario de producción y ENTREGÁRSELO (que él lo use solo) + grabar un video Loom de referencia de 5 min. |
| Jue 6 | WooCommerce + QBO | Tour de QuickBooks Online SIN tocar asientos contables + lista de qué entra automático vs. manual. Apóyate en los tutoriales gratis de QuickBooks (https://quickbooks.intuit.com/tutorials/ — videos de 3-8 min). |
| Jue 6 (BLOQUE ESPECIAL) | Reunión con bookkeeper | Reunión de 30 min con el bookkeeper: llenar la matriz quién-hace-qué v1 + dejar agendado un check-in recurrente (30 min después para pasar todo en limpio). |
| Vie 7 | WooCommerce + QBO | Seguir una orden real de punta a punta ('la vida de una orden': Woo → inFlow → QBO) y escribir vida-de-una-orden.md + mapa de flujo versión 2 + UPDATE SEMANAL #5. |
| Sáb 8 | IT y ciberseguridad | Backblaze: enrolar el resto de las computadoras del inventario (10 min por equipo, repartido; hoy cierras las que falten). |

🏁 **Hito de la semana:** LISTO: todas las computadoras respaldándose en Backblaze, comparativa MSP lista para decidir, calendario de producción en manos de Alejandro, y entiendes cómo fluye el dinero en QBO.

### 🗓️ Semana 6 (10-16 ago 2026) — MSP elegido + reportes QBO + Karine

🎯 **Objetivo de la semana:** Que Miguel elija el MSP, revisar la cotización del seguro, dejar los 3 reportes mensuales de QBO programados y mejorar los workflows de Karine con su feedback real.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 10 | IT y ciberseguridad | Revisar la cotización del seguro cibernético contra las 3 coberturas mínimas + enviar recomendación a Miguel + preparar la presentación corta de la recomendación de MSP. |
| Lun 10 (BLOQUE ESPECIAL) | Reunión con Miguel | Reunión de 30 min: presentar la comparativa, ELEGIR el MSP con su OK y solicitar el contrato. |
| Mar 11 | WooCommerce + QBO | Configurar los 3 reportes de QBO que Miguel revisará cada mes y programarlos para que le lleguen SOLOS por email + pedirle su OK por email (async, sin reunión). |
| Mié 12 (BLOQUE ESPECIAL) | Reunión con Karine | Sesión de feedback de 45 min con Karine: verla trabajar de verdad y salir con la lista de fricciones y mejoras pedidas, con prioridad. |
| Mié 12 | Tektone | Mejorar los workflows de Karine con su feedback — parte 1 (atacar las 2 fricciones más grandes). |
| Jue 13 | Tektone | Mejorar los workflows de Karine — parte 2 + documentar los 3 workflows con capturas. |
| Vie 14 | Documentación | Documentar P-04: Entrada de órdenes de Karine (aprovechando que lo tienes fresco de esta semana) + UPDATE SEMANAL #6. |
| Sáb 15 | Documentación | Crear el Dashboard #1 para Miguel en HubSpot (que le llegue cada lunes solo): la semilla de la visión nov-2026. Guía gratis: HubSpot Academy, curso de reportes (https://academy.hubspot.com — lección de ~45 min). |

🏁 **Hito de la semana:** LISTO: MSP elegido con OK de Miguel y contrato pedido, seguro con recomendación enviada, 3 reportes QBO llegando solos, workflows de Karine mejorados y documentados, Dashboard #1 vivo.

### 🗓️ Semana 7 (17-23 ago 2026) — Contrato MSP firmado + intercompany

🎯 **Objetivo de la semana:** Firmar el MSP, verificar que los respaldos funcionan de verdad (con prueba de restauración), y construir + probar el flujo intercompany Sensi↔Tektone.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 17 | IT y ciberseguridad | Firmar el contrato con el MSP + agendar el kickoff para la semana 8 + seguimiento firme al broker: ¿cuándo queda ACTIVO el seguro? |
| Mar 18 | Tektone | Diseñar el flujo intercompany Sensi↔Tektone (cuando Sensi le compra a Tektone: quién crea qué orden y dónde) + crear el proveedor/cliente en ambos inFlow. |
| Mié 19 | Tektone | Probar el flujo intercompany con UNA orden completa registrada en ambos sistemas con referencia cruzada + documentar el proceso paso a paso. |
| Jue 20 | IT y ciberseguridad | Verificar el primer backup completo en Backblaze + hacer una prueba de restauración de un archivo + crear la cuenta admin de emergencia en Microsoft 365 (guía gratis: Microsoft Learn, https://learn.microsoft.com/training/ — módulo de admin básico de M365, ~40 min). |
| Vie 21 | WooCommerce + QBO | Documentar P-11: proceso de catálogo y precios en WooCommerce (usando tu mini-guía y lo aprendido con el producto de prueba) + UPDATE SEMANAL #7. |
| Sáb 22 | Documentación | Documentar P-05 (Cotizaciones en inFlow) y P-06 (Procesamiento de facturas) en una sola sesión: son procesos que ya dominas, solo falta escribirlos. Criterio 6 completa sus 3 procesos base. |

🏁 **Hito de la semana:** LISTO: MSP contratado con kickoff agendado, backups verificados con restauración probada, flujo intercompany funcionando y documentado, 9 procesos documentados.

### 🗓️ Semana 8 (24-30 ago 2026) — Kickoff MSP + seguro ACTIVO + operación real

🎯 **Objetivo de la semana:** Poner al MSP a operar, confirmar el seguro cibernético ACTIVO (criterio 9 cerrado), correr una semana de órdenes reales por inFlow Tektone y avanzar fuerte en documentación.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 24 | IT y ciberseguridad | Preparar el onboarding del MSP (entregarles el inventario-it.md como mapa) + presionar al broker hasta confirmar el seguro cibernético ACTIVO con documento guardado + escribir el plan de incidente de media página. |
| Lun 24 (BLOQUE ESPECIAL) | Reunión kickoff MSP | Kickoff de 1h con el MSP: entregar accesos, anunciar el canal de soporte al equipo y dejar agendado el check-in mensual. |
| Mar 25 | WooCommerce + QBO | Documentar P-13 (flujo mensual con el bookkeeper — 20 min de llamada corta con él para validar) y P-14 (reportes de QBO para Miguel) en una sesión. Criterio 4 documentado. |
| Mié 26 | Tektone | Semana de operación real: monitorear las órdenes corriendo por inFlow Tektone (15 min diarios toda la semana) + esta sesión de 1h para corregir lo que se trabe + contador de adopción. |
| Jue 27 | Documentación | Documentar P-15 (Production scheduling Tektone) y P-16 (Order management Tektone) con lo que YA construiste: evidencia honesta del estado. Criterio 5 con respaldo escrito. |
| Vie 28 | Documentación | Documentar P-07: Pipeline de HubSpot (etapas y reglas) — con esto el criterio 2 queda documentado al 100% + UPDATE SEMANAL #8. |
| Sáb 29 | IT y ciberseguridad | M365: configurar el buzón compartido sales@ con permisos bien puestos, probado por el equipo y con permisos documentados. |

🏁 **Hito de la semana:** LISTO: MSP operando (criterio 8 ✔), seguro cibernético ACTIVO (criterio 9 ✔), una semana de órdenes reales por inFlow Tektone, 14 de 18 procesos documentados.

### 🗓️ Semana 9 (31 ago - 6 sep 2026) — Semana autónoma + barrido de documentación

🎯 **Objetivo de la semana:** Operar Woo/QBO SIN preguntarle nada a Miguel (evidencia de ownership), cerrar los 18 procesos documentados (criterio 10 ✔) y hacer la primera auditoría trimestral de accesos.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 31 | Documentación | Documentar P-08 (Onboarding de usuario nuevo) y P-09 (Offboarding) en una sesión: son gemelos, uno es el espejo del otro. OJO: toda la semana corre la 'semana autónoma' de Woo/QBO — cero preguntas a Miguel + 15 min diarios de registro en semana-autonoma.md (durante el trabajo normal, no cuenta como tu hora). |
| Mar 1 | Documentación | Documentar P-10 (Compras y órdenes de compra en inFlow Sensi) y P-12 (Órdenes WooCommerce y sync con inFlow, con diagrama y plan de emergencia) en una sesión. Criterios 1 y 3 con documentación completa. |
| Mié 2 | IT y ciberseguridad | Ejecutar y firmar la PRIMERA auditoría trimestral de accesos: quién tiene acceso a qué, quién sobra, quién falta. La rutina continua queda en marcha. |
| Jue 3 | Documentación | Documentar P-17 (Verificación mensual de Backblaze) y P-18 (Rutinas IT: check-in MSP + auditoría de accesos) aprovechando la auditoría fresca de ayer. Los 18 procesos: COMPLETOS. |
| Jue 3 (BLOQUE ESPECIAL) | Reunión Paola + Alejandro | Check-in de 30 min: mostrar avance de Tektone, conseguir su validación + email de confirmación + enviar el primer Reporte #2 a Paola. |
| Vie 4 | Documentación | Prueba de fuego: Karine ejecuta un proceso usando SOLO el documento (sin tu ayuda); corregir lo que la confundió + UPDATE SEMANAL #9. |
| Sáb 5 | WooCommerce + QBO | Cerrar los huecos que encontró la semana autónoma: actualizar los documentos de proceso a versión final + verificar que el índice maestro quede SIN huecos (criterio 10 ✔). |

🏁 **Hito de la semana:** LISTO: 18/18 procesos documentados y uno validado por otra persona, semana autónoma completada con registro, auditoría trimestral firmada, Paola y Alejandro validaron Tektone por escrito.

### 🗓️ Semana 10 (7-13 sep 2026) — Dossier + simulacro de evaluación

🎯 **Objetivo de la semana:** Armar el dossier de evidencia de los 10 criterios, hacer el simulacro como si fueras Miguel, corregir huecos y entregarle el dossier a Miguel UNA SEMANA ANTES. Cero sorpresas el 16-sep.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 7 | Documentación | Armar el dossier de evidencia: esqueleto + llenar los criterios 1, 2, 7, 8 y 9 (capturas de inFlow/HubSpot, 1Password desplegado, contrato MSP, póliza del seguro). |
| Mar 8 | Documentación | Llenar el dossier: criterios 3, 4, 5, 6 y 10 (carpetas de evidencia de Woo/QBO, Tektone operando, workflows de Karine, índice de 18 procesos). |
| Mié 9 (BLOQUE ESPECIAL) | Simulacro | Simulacro de evaluación (1h): recorrer los 10 criterios como si fueras Miguel preguntando '¿demuéstramelo?' — salir con lista de huecos y fecha de corrección para cada uno. |
| Mié 9 (BLOQUE ESPECIAL) | Reunión MSP | Primer check-in mensual con el MSP (30 min) + revisión mensual de Backblaze (15 min): primera minuta guardada, rutina en marcha. |
| Jue 10 | Documentación | Corregir TODOS los huecos que encontró el simulacro y exportar el dossier final en PDF. |
| Vie 11 (BLOQUE ESPECIAL) | Reunión con Miguel | Pre-revisión de 30 min con Miguel: '¿qué falta para el OK?' + enviarle la invitación del 16-sep con el dossier PDF adjunto + UPDATE SEMANAL #10. |
| Sáb 12 | Tektone | Ensayar la demo de 10 minutos con datos reales, cronometrada: una orden Tektone en vivo + una orden Woo→inFlow→QBO en vivo. Grabarte y verte. |

🏁 **Hito de la semana:** LISTO: dossier final en PDF en manos de Miguel el viernes 11 (5 días antes), simulacro hecho, huecos corregidos, demo ensayada y cronometrada.

### 🗓️ Semana 11 (14-16 sep 2026) — Repaso final y evaluación

🎯 **Objetivo de la semana:** NADA NUEVO. Solo verificar, ensayar y presentar. Llegas al 16-sep con evidencia, no con promesas.

| Día | Área | Qué hacer |
|-----|------|-----------|
| Lun 14 | Documentación | Repaso final del dossier al 100% + refrescar evidencia de los criterios 5 y 6 (capturas de órdenes Tektone de ESTA semana) + verificar que todos los links y accesos de la demo funcionan. |
| Mar 15 | Documentación | Ensayo general de la presentación: demo de 10 min fluida + preparar respuestas a las 3 preguntas más difíciles que Miguel podría hacer + preparar el cierre (mencionar la visión nov-2026: dashboards en vivo y automatización). |
| Mié 16 (BLOQUE ESPECIAL) | LA EVALUACIÓN | La reunión de evaluación (45 min): recorrer los 10 criterios con el dossier, demo en vivo, y cerrar con el plan de nov-2026. Evidencia, no promesas. |

🏁 **Hito de la semana:** LISTO: evaluación aprobada con los 10 criterios demostrados. Pago sube a $2,500/mes.

---

## 🚩 Hitos clave del reto

- Vie 10-jul (fin Semana 1): auditoría completa de las 4 áreas + presupuesto IT aprobado por Miguel por escrito.
- Vie 17-jul (fin Semana 2): accesos Woo/QBO en tu poder, broker de seguro contactado, 5-8 MSPs contactados — lo vencido del 1-jul ya está en movimiento.
- Sáb 1-ago (fin Semana 4): MFA en verde en las 5 plataformas, 3 propuestas de MSP en mano, primera orden de prueba completa en inFlow Tektone.
- Lun 10-ago (Semana 6): Miguel elige el MSP — la decisión más atrasada del plan queda tomada.
- Vie 28-ago (fin Semana 8): MSP operando (criterio 8 ✔) y seguro cibernético ACTIVO (criterio 9 ✔) — los dos criterios con fecha vencida quedan cerrados.
- Sáb 5-sep (fin Semana 9): 18/18 procesos documentados (criterio 10 ✔) + semana autónoma de Woo/QBO completada (evidencia de ownership).
- Vie 11-sep (Semana 10): dossier final en PDF entregado a Miguel 5 días antes — cero sorpresas.
- Mié 16-sep: LA EVALUACIÓN — los 10 criterios demostrados con evidencia.

## 📏 Reglas del plan

- Si pierdes un día entre semana, el sábado es tu comodín: recuperas ESA sesión, no intentes recuperar dos. Si pierdes dos días, cae primero la tarea de documentación (se puede juntar con la del sábado siguiente); las reuniones y lo de IT vencido NUNCA se caen.
- Las reuniones (bloques especiales) NO cuentan como tu hora diaria de estudio: son parte de tu trabajo operativo. Propónlas siempre lunes o martes para que, si se mueven, quepan en la misma semana.
- El update de los viernes a Miguel es sagrado: 15 minutos, mismo formato (hecho / en curso / bloqueado / próximo). Si un viernes no hay avance, se envía igual — la constancia ES la evidencia.
- Si alguien externo te frena (broker sin respuesta, MSP lento, bookkeeper ocupado): NO esperes. Envía recordatorio, cópiale a Miguel a la segunda semana sin respuesta, y usa la sesión en la siguiente tarea de la lista.
- Regla de las dos documentaciones: documenta cada proceso la misma semana en que lo construyes o lo tocas (está fresco = 1 hora; frío = 2 horas). Los procesos que ya dominas se documentan de a dos por sesión.
- Después del lunes 7-sep NO se empieza NADA nuevo: solo dossier, correcciones y ensayo. Un criterio al 90% bien contado vale más que dos cosas nuevas a medias.
- Se pospone para DESPUÉS del 16-sep (no afecta los 10 criterios): estudio profundo de Microsoft 365 admin en Microsoft Learn, dashboards en vivo avanzados para Miguel y Paola (visión nov-2026), automatizaciones extra de Zapier, y cursos completos de HubSpot Academy — ahora solo lecciones puntuales.
- Si el estado real de la Semana 1 revela sorpresas (ej. ya existe un MSP, o WooCommerce ni está montado), ajusta el plan ESA misma semana: los criterios mandan, el cronograma sirve a los criterios y no al revés.
