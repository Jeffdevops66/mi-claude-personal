# 🔐 3. IT y ciberseguridad (criterios 7, 8 y 9) + Microsoft 365

> **Objetivo:** Que el 16 de septiembre puedas demostrar tres cosas con evidencia: (1) 1Password funcionando en los 11 empleados con bóvedas por empresa y cero contraseñas compartidas, (2) un MSP (empresa que hace de departamento de IT por una cuota mensual) contratado y trabajando, con MFA y Backblaze activos en todo, y (3) el seguro cibernético (un seguro que paga los daños si te hackean) activo. Además, que manejes Microsoft 365 como admin básico: usuarios, buzones compartidos y permisos. Todo documentado en tu repo para el criterio 10.

---

## 🔍 Auditoría inicial — verifica esto ANTES de empezar

No asumas que algo está hecho. Verifícalo con tus propios ojos y marca la casilla.

- [ ] **¿Existe ya una cuenta de 1Password Teams pagada?**
  - 👀 Cómo verificarlo: Pregunta a Miguel: '¿Compramos 1Password en mayo?'. Intenta entrar en https://start.1password.com con tu correo de trabajo. Si nadie sabe, revisa los estados de cuenta de la tarjeta de la empresa buscando '1Password' o 'AgileBits'.
- [ ] **¿Cuántos de los 11 empleados usan 1Password hoy?**
  - 👀 Cómo verificarlo: Si hay cuenta: entra como admin a la consola de 1Password → menú 'People' (Personas). Cuenta cuántos aparecen como 'Active'. Anota el número exacto: X de 11.
- [ ] **¿MFA activo en Microsoft 365 para todos?**
  - 👀 Cómo verificarlo: MFA = un segundo candado además de la contraseña (un código en tu teléfono). Entra a https://admin.microsoft.com → Usuarios → Usuarios activos → botón 'Autenticación multifactor' (arriba). Verás la lista: 'Deshabilitado', 'Habilitado' o 'Aplicado'. Anota quién NO tiene.
- [ ] **¿MFA activo en HubSpot?**
  - 👀 Cómo verificarlo: En HubSpot: engranaje (Configuración) → Valores predeterminados de la cuenta → pestaña 'Seguridad'. Busca la opción 'Exigir autenticación de dos factores'. Si está apagada, anótalo. También revisa tu propio perfil → Seguridad para ver si TÚ la tienes.
- [ ] **¿MFA activo en QuickBooks Online?**
  - 👀 Cómo verificarlo: Cada usuario entra a https://accounts.intuit.com/app/account-manager/security → sección 'Verificación en dos pasos' (2-step verification). Pídele al bookkeeper y a Miguel una captura de esa pantalla. Anota quién la tiene ON.
- [ ] **¿MFA en WooCommerce (WordPress)?**
  - 👀 Cómo verificarlo: Entra a mysensihome.com/wp-admin → menú Plugins. Busca si hay un plugin de dos factores activo (se llaman 'Two-Factor', 'Wordfence' o 'Jetpack'). Si no hay ninguno, anótalo: falta instalar.
- [ ] **¿MFA en inFlow?**
  - 👀 Cómo verificarlo: En inFlow Cloud (web) → tu avatar/cuenta → configuración de cuenta → busca 'two-factor' o 'security'. Si la opción no existe en inFlow, anótalo como excepción (lo mitigamos con contraseñas únicas fuertes en 1Password).
- [ ] **¿Backblaze está instalado en alguna computadora?**
  - 👀 Cómo verificarlo: Backblaze = copia automática de los archivos en la nube por si la compu muere o la roban. Mira junto al reloj de cada PC si está el ícono de la llama roja de Backblaze. Pregunta a Miguel si se compró la cuenta en junio. Revisa estados de cuenta buscando 'Backblaze'.
- [ ] **¿Hay MSP contratado o en conversaciones?**
  - 👀 Cómo verificarlo: MSP = empresa que es tu departamento de IT por una cuota mensual. Pregunta directo a Miguel: '¿Hablamos con algún proveedor de IT? ¿Hay alguien que dé soporte hoy cuando algo se rompe?'. Si la respuesta es 'nadie', el criterio 8 está en cero.
- [ ] **¿Hay seguro cibernético o cotización en curso?**
  - 👀 Cómo verificarlo: Pregunta a Miguel: '¿Quién es nuestro broker de seguros y ya le pedimos el cyber?'. Pide el nombre y correo del broker y una copia de la póliza actual de Sensi Home (la necesitarás para pedir el add-on).
- [ ] **¿Cuántas computadoras hay y de quién son?**
  - 👀 Cómo verificarlo: Haz la lista física: recorre la oficina (y pregunta por remotos). Por cada equipo anota: dueño, laptop o desktop, Windows o Mac, empresa (Sensi/Tektone). Esta lista manda para Backblaze y para el MSP.
- [ ] **¿Tienes acceso de administrador a Microsoft 365 y existe un admin de respaldo?**
  - 👀 Cómo verificarlo: Entra a https://admin.microsoft.com. Si entras, ve a Usuarios → Usuarios activos → tu usuario → verifica que dice 'Administrador global'. Pregunta: ¿alguien más es admin? Si eres el único, hay que crear una cuenta de emergencia (tarea de Semana 7).

---

## ✅ Tareas semana a semana

### 📌 Semana 1: Auditoría IT completa: llenar el inventario

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Abre la plantilla 'Inventario IT' (abajo) y créala como archivo: proyectos/it/inventario-it.md en tu repo.
2. Recorre los 12 checks de la auditoría inicial uno por uno y anota la respuesta real de cada uno.
3. Para los que dependen de otras personas (Miguel, bookkeeper, broker), envía HOY los mensajes de pregunta — no esperes la respuesta para seguir.
4. Marca cada fila con un semáforo: VERDE (listo), AMARILLO (a medias), ROJO (no existe).
5. Guarda el archivo y haz commit en GitHub Desktop con el mensaje 'Auditoría IT inicial'.

📦 **Entregable:** proyectos/it/inventario-it.md con las 12 respuestas y semáforo. Esta es tu foto de partida.

### 📌 Semana 1: Reunión con Miguel: luz verde de presupuesto IT

⏱️ **Tiempo estimado:** Reunión 30min con Miguel + 20min de preparación

**Pasos:**
1. Pide a Miguel 30 minutos esta semana: 'Necesito aprobar el presupuesto de IT pendiente de mayo/junio para llegar a septiembre'.
2. Llévale UNA hoja con 3 números: 1Password Teams ~$4-5/usuario/mes (~$55/mes por 11), Backblaze ~$9/equipo/mes (~$90-100/mes si son ~10 equipos), MSP $300-600/mes, seguro ciber $500-1,500/año.
3. Pídele 3 cosas concretas: (1) OK al gasto, (2) el contacto del broker de seguros, (3) que anuncie al equipo que 1Password será obligatorio.
4. Anota los acuerdos en proyectos/it/inventario-it.md al final, con fecha.

📦 **Entregable:** Presupuesto aprobado por escrito (aunque sea un mensaje de WhatsApp/email de Miguel diciendo OK) + contacto del broker.

### 📌 Semana 1: Tabla de MFA: verificar las 5 plataformas

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Crea proyectos/it/tabla-mfa.md con una tabla: plataforma × usuario, y estado ON/OFF.
2. Microsoft 365: admin.microsoft.com → Usuarios → Usuarios activos → botón 'Autenticación multifactor'. Copia el estado de cada usuario.
3. HubSpot: engranaje → Valores predeterminados de la cuenta → Seguridad → mira si 'Exigir 2FA' está activo.
4. QuickBooks: pide capturas de accounts.intuit.com/app/account-manager/security a cada usuario de QBO.
5. WooCommerce: wp-admin → Plugins → anota si existe plugin de 2FA. inFlow: revisa configuración de cuenta y anota si la opción existe.
6. Toma captura de pantalla de cada revisión y guárdalas en proyectos/it/evidencias/ (las usarás el 16-sep).

📦 **Entregable:** tabla-mfa.md completa: sabes exactamente a quién le falta MFA y dónde.

### 📌 Semana 2: Enviar email al broker pidiendo el seguro cibernético

⏱️ **Tiempo estimado:** 30 min

**Pasos:**
1. Seguro cibernético = un seguro que paga los daños si te hackean (roban datos, secuestran archivos, o el negocio se detiene).
2. Copia la plantilla 'Email al broker de seguros' (abajo), ponle los datos reales y envíala al broker que te dio Miguel, con Miguel en CC.
3. OJO: las aseguradoras suelen preguntar '¿tienen MFA y backups?' en su cuestionario. Por eso este email va YA (semana 2) pero el cuestionario lo llenaremos cuando MFA y Backblaze estén ON (semanas 4-5).
4. Agenda en tu calendario un recordatorio semanal: 'seguimiento broker' cada lunes hasta que llegue la cotización.

📦 **Entregable:** Email enviado con copia a Miguel + recordatorio semanal creado.

### 📌 Semana 2: 1Password Teams: cuenta lista y bóvedas creadas

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Bóveda = carpeta de contraseñas que se comparte solo con ciertas personas.
2. Si NO hay cuenta: crea una en https://1password.com/business (elige Business/Teams) con el correo it@ o tu correo de trabajo. Guarda tu Secret Key impresa y en un lugar seguro.
3. Si SÍ hay cuenta: pide que te hagan admin y entra a la consola.
4. Crea 4 bóvedas: 'Sensi Home', 'Tektone', 'IT-Admin' (solo tú y Miguel) y deja la 'Shared' por defecto para cosas de todos.
5. Regla de oro que documentarás: cada persona tiene su bóveda Privada + acceso SOLO a la bóveda de su empresa. Nadie se pasa contraseñas por WhatsApp o Excel nunca más.
6. Lee la guía oficial (recurso 5) mientras lo haces.

📦 **Entregable:** Cuenta 1Password Teams operativa con 4 bóvedas y tú como admin.

### 📌 Semana 2: Buscar y contactar 5-8 MSPs en Miami

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Busca en Google Maps: 'managed IT services Miami' y 'IT support small business Miami'. Abre los 10 primeros con reseñas de 4.5+ estrellas.
2. Busca también en https://www.cloudtango.net/msp/us/FL/miami (directorio de MSPs) y pide 1-2 recomendaciones al broker de seguros y al contador — ellos siempre conocen MSPs.
3. Filtra a 5-8 candidatos que atiendan empresas de 10-20 empleados (descarta los que solo hablan de clientes enormes).
4. Envíales este mensaje por su formulario o email: 'Somos dos empresas hermanas en Miami, ~11 empleados en total, Microsoft 365, buscamos soporte IT gestionado por $300-600/mes. ¿Podemos agendar una llamada de 30 min esta o la próxima semana?'
5. Anota los 5-8 nombres, teléfono y fecha de contacto en proyectos/it/msp-busqueda.md.

📦 **Entregable:** 5-8 MSPs contactados con llamadas por agendar.

### 📌 Semana 3: Invitar a los 11 empleados a 1Password

⏱️ **Tiempo estimado:** 1 sesión de 1h (+ mini-sesiones de 15min en la semana)

**Pasos:**
1. Pide a Miguel que envíe primero su anuncio (1 línea: 'Desde hoy usamos 1Password, es obligatorio, Jeffrey coordina').
2. En la consola de 1Password → People → Invite, invita a los 11 con su correo de trabajo.
3. Envía a cada uno el mensaje de la plantilla 'Bienvenida 1Password' (abajo): cómo aceptar la invitación, instalar la app y la extensión del navegador.
4. Asigna cada persona a la bóveda de su empresa (Sensi o Tektone). Karine va en Sensi/Tektone según defina Miguel.
5. Agenda mini-sesiones de 15 min con quien se atore (máximo 2-3 personas por día durante la semana).

📦 **Entregable:** 11 invitaciones enviadas + mensaje guía entregado + sesiones de ayuda agendadas.

### 📌 Semana 3: Llamadas con MSP #1 y #2

⏱️ **Tiempo estimado:** 2 bloques de 45min (agéndalos, no cuentan como tu hora de estudio)

**Pasos:**
1. Imprime o abre la plantilla 'Preguntas para llamadas con MSP' (abajo).
2. Haz las 2 primeras llamadas de 30-45 min. Haz TODAS las preguntas y anota las respuestas ahí mismo.
3. Al final de cada llamada pide: 'Envíenme propuesta por escrito con precio para 11 usuarios'.
4. Guarda las notas en proyectos/it/msp-busqueda.md, una sección por candidato.

📦 **Entregable:** 2 llamadas hechas con notas completas y propuestas solicitadas.

### 📌 Semana 3: Migrar contraseñas compartidas a las bóvedas

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Haz la lista de TODAS las contraseñas que hoy viven en Excel, notas, WhatsApp o en la cabeza de alguien (HubSpot, inFlow, Woo, QBO, M365, banco NO — el banco solo Miguel, redes sociales, hosting, Zapier, etc.).
2. Crea cada una como item en la bóveda correcta: las de Sensi en 'Sensi Home', las de Tektone en 'Tektone', las de admin puro (hosting, registrador de dominio, Zapier) en 'IT-Admin'.
3. Donde la contraseña sea débil o repetida, cámbiala usando el generador de 1Password ahí mismo.
4. Borra los archivos/notas viejas donde estaban (¡después de verificar que funcionan desde 1Password!).
5. Escribe la política en proyectos/it/politica-contrasenas.md: 'Cero contraseñas fuera de 1Password. Cero contraseñas compartidas por chat. Toda cuenta nueva nace en 1Password.'

📦 **Entregable:** Contraseñas de la empresa viviendo SOLO en 1Password + política escrita de 1 página.

### 📌 Semana 4: Encender MFA donde falte (las 5 plataformas)

⏱️ **Tiempo estimado:** 1 sesión de 1h (+ seguimiento a rezagados en la semana)

**Pasos:**
1. Abre tu tabla-mfa.md de la semana 1 y ve fila por fila en ROJO.
2. Microsoft 365: la vía simple es activar 'valores predeterminados de seguridad': entra.microsoft.com → Identidad → Información general → Propiedades → 'Administrar valores predeterminados de seguridad' → Habilitar. Esto obliga a todos a registrar la app Microsoft Authenticator. Avisa al equipo UN DÍA ANTES.
3. HubSpot: engranaje → Valores predeterminados de la cuenta → Seguridad → activa 'Exigir autenticación de dos factores'. Cada usuario la configura al entrar.
4. QuickBooks: envía a cada usuario el link accounts.intuit.com/app/account-manager/security con instrucción: 'activa 2-step verification y mándame captura'.
5. WooCommerce: wp-admin → Plugins → Añadir nuevo → busca 'Two-Factor' (el plugin oficial gratuito) → Instalar → Activar. Luego cada usuario: Usuarios → Perfil → sección Two-Factor → activa 'Authenticator app' escaneando el QR con su teléfono.
6. inFlow: si no hay opción de MFA, aplica la mitigación: contraseña única de 20+ caracteres generada por 1Password para cada usuario, y anota la excepción en tabla-mfa.md.
7. Los códigos MFA se pueden guardar en 1Password (campo 'contraseña de un solo uso') — así nadie se bloquea.

📦 **Entregable:** tabla-mfa.md toda en VERDE (o con excepción de inFlow documentada) + capturas en evidencias/.

### 📌 Semana 4: Llamada MSP #3 y cierre de propuestas

⏱️ **Tiempo estimado:** 1 bloque de 45min + 2 llamadas cortas

**Pasos:**
1. Haz la tercera llamada con la misma lista de preguntas.
2. Persigue las propuestas escritas de los 3: 'Necesito su propuesta este viernes para decidir este mes'.
3. Pide a cada finalista 2 referencias de clientes actuales y llama o escribe a al menos una por MSP: '¿Responden rápido? ¿Recomendarías?'.

📦 **Entregable:** 3 propuestas escritas en mano + al menos 2 referencias verificadas.

### 📌 Semana 4: Estudio: Microsoft 365 admin básico (Microsoft Learn)

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Abre el path gratuito 'Conceptos básicos de Microsoft 365' en Microsoft Learn (recurso 1).
2. Haz SOLO los módulos de administración y seguridad (no necesitas todo el path): unos 60-90 min.
3. Mientras estudias, ten abierto admin.microsoft.com de tu empresa y ubica cada cosa en tu pantalla real.
4. Anota en proyectos/it/notas-m365.md las 5 cosas que harás distinto (ej. cómo dar de baja un usuario sin perder su correo).

📦 **Entregable:** Notas propias de M365 admin + soltura moviéndote por el centro de administración.

### 📌 Semana 5: Backblaze: crear grupo y piloto en tu computadora

⏱️ **Tiempo estimado:** 1 sesión de 1h (el backup corre solo después)

**Pasos:**
1. Crea la cuenta en https://www.backblaze.com/cloud-backup/business → 'Backblaze Computer Backup' con Groups (grupos = panel central para ver los backups de todas las compus).
2. En el panel: Groups → crea el grupo 'Sensi-Tektone Oficina' con facturación centralizada (~$9/equipo/mes, confirma el precio actual al contratar).
3. Instala el cliente en TU computadora primero (piloto): acepta la invitación del grupo, instala, y deja que haga el primer backup completo (puede tardar horas/días, corre solo en segundo plano).
4. Verifica al día siguiente en el panel de Groups que tu equipo aparece con fecha de último backup.

📦 **Entregable:** Cuenta Backblaze Business con grupo creado y tu compu respaldándose.

### 📌 Semana 5: Backblaze: enrolar el resto de las computadoras

⏱️ **Tiempo estimado:** 1 sesión de 1h repartida en la semana (10 min por equipo)

**Pasos:**
1. Desde el panel de Groups → Invite, envía la invitación por email al dueño de cada computadora de tu inventario.
2. Pasa 10 min con cada persona (o guíala por mensaje): aceptar invitación → descargar → instalar → listo. No hay que configurar nada más: Backblaze respalda todo por defecto.
3. Marca en inventario-it.md cada equipo enrolado con la fecha.
4. Los primeros backups completos tardan días — está bien, lo verificaremos en semana 7.

📦 **Entregable:** Todas las computadoras del inventario con Backblaze instalado.

### 📌 Semana 5: Matriz comparativa de los 3 MSPs

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Copia la plantilla 'Comparativa MSP + recomendación' (abajo) a proyectos/it/msp-comparativa.md.
2. Llena la tabla con las 3 propuestas: precio, qué incluye, SLA (SLA = promesa por escrito de qué tan rápido responden), experiencia con M365, referencias.
3. Elige tu ganador y escribe 3 razones simples de por qué.
4. Si el broker ya respondió con la cotización del seguro, revisa también el cuestionario que pide la aseguradora — ya puedes contestar 'sí' a MFA y backups.

📦 **Entregable:** msp-comparativa.md lista para presentar a Miguel.

### 📌 Semana 6: Presentar recomendación de MSP a Miguel y decidir

⏱️ **Tiempo estimado:** Reunión 30min con Miguel + 30min de preparación

**Pasos:**
1. Pide 30 min a Miguel. Llévale la página de recomendación (parte 2 de la plantilla): ganador, precio, 3 razones, y qué pasa si no contratamos (sin soporte, criterio 8 en rojo, aseguradora puede pedir requisitos).
2. Pídele la decisión EN la reunión o máximo en 48h: 'La evaluación es el 16-sep y el onboarding toma semanas'.
3. Con el OK, responde al MSP ganador el mismo día: 'Adelante, envíen contrato'.
4. Avisa con cortesía a los 2 no elegidos (te los quedas de plan B).

📦 **Entregable:** MSP elegido con OK de Miguel y contrato solicitado.

### 📌 Semana 6: Revisar la cotización del seguro: verificar las 3 coberturas

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Cuando llegue la cotización, verifica que incluya mínimo: (1) respuesta a robo de datos ('data breach response': avisar a afectados, expertos forenses), (2) ransomware/extorsión ('cyber extortion': cuando secuestran tus archivos y piden rescate), (3) interrupción del negocio ('business interruption': te pagan lo que dejas de vender mientras estás caído).
2. Bonus si trae 'funds transfer fraud' (te engañan para transferir dinero) — con Zapier y facturas volando, vale la pena preguntarlo.
3. Verifica el límite: para este tamaño de empresa, $250,000 a $1,000,000 de cobertura es lo normal en el rango de $500-1,500/año.
4. Si el broker no ha respondido: llámalo (no email) y dile que necesitas la cotización esta semana. Lee el recurso 11 (guía de la FTC, 15 min) para hablar con seguridad.
5. Reenvía la cotización a Miguel con tu recomendación en 3 líneas.

📦 **Entregable:** Cotización revisada contra las 3 coberturas mínimas + recomendación enviada a Miguel.

### 📌 Semana 7: Firmar contrato MSP y agendar kickoff

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Lee el contrato del MSP buscando 3 cosas: plazo mínimo, qué pasa si cancelamos, y que el precio y el SLA prometidos estén POR ESCRITO.
2. Pasa el contrato a Miguel para firma (él firma, tú coordinas).
3. Agenda la reunión de kickoff (arranque) con el MSP para la semana 8.
4. Si algo se atora aquí, escala a Miguel de inmediato — cada semana perdida come el margen antes del 16-sep.

📦 **Entregable:** Contrato firmado + kickoff agendado.

### 📌 Semana 7: Verificar primer backup completo en Backblaze + cuenta admin de emergencia M365

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Entra al panel de Backblaze Groups y revisa cada computadora: la fecha de 'último backup' debe ser de los últimos 3 días. Persigue a los rezagados (suele ser una compu apagada o sin wifi).
2. Haz una prueba de restauración: desde el panel, restaura UN archivo cualquiera de tu propia compu. Un backup que nunca probaste restaurar no cuenta.
3. En M365: crea la cuenta admin de emergencia ('break glass' = por si un día pierdes acceso a la tuya): admin.microsoft.com → Usuarios → Agregar usuario → 'admin-emergencia@mysensihome.com' → rol Administrador global → contraseña de 30 caracteres generada por 1Password → guárdala en la bóveda IT-Admin compartida con Miguel.
4. Toma capturas del panel de Backblaze en verde para evidencias/.

📦 **Entregable:** Todos los backups en verde + prueba de restauración hecha + admin de emergencia creado.

### 📌 Semana 8: Onboarding del MSP: entregarles el mapa

⏱️ **Tiempo estimado:** Reunión kickoff 1h con el MSP + 30min de preparación

**Pasos:**
1. En el kickoff, entrégales: tu inventario-it.md (equipos y personas), la lista de plataformas (M365, HubSpot, inFlow, Woo, QBO, Backblaze, 1Password), y quién es quién.
2. Dales el acceso que pidan vía 1Password (crea items en una bóveda 'MSP' compartida) — nunca por email.
3. Acuerda 3 cosas por escrito: (1) cómo se pide soporte (email/portal/teléfono), (2) día fijo del check-in mensual de 30 min, (3) qué monitorean ellos (antivirus = guardia que vigila la computadora, parches = actualizaciones de seguridad).
4. Comunica al equipo: 'Desde hoy, si algo se rompe en tu compu, escribe a [soporte del MSP], con copia a mí'.

📦 **Entregable:** MSP operando con accesos, canal de soporte anunciado al equipo y check-in mensual agendado.

### 📌 Semana 8: M365: buzón compartido sales@ con permisos bien puestos

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Buzón compartido = un correo (sales@) que varias personas leen y responden sin tener contraseña propia; es gratis, no gasta licencia.
2. Crear: admin.microsoft.com → Equipos y grupos → Buzones compartidos → 'Agregar buzón compartido' → nombre 'Ventas', correo sales@mysensihome.com.
3. Dar permisos: clic en el buzón → 'Leer y administrar' (eso es Full Access = permiso para abrir y leer el buzón) → agrega a Lina, Bautista y Karine. Luego 'Enviar como' (Send As = permiso para mandar correos que salen como sales@) → agrega a los mismos.
4. Prueba: pide a Karine que en Outlook web haga clic en su avatar → 'Abrir otro buzón' → sales@. Y que envíe un correo de prueba eligiendo 'De: sales@'.
5. Documenta quién tiene qué permiso en proyectos/it/procesos/m365-buzones.md usando la plantilla de proceso (abajo).
6. Guías oficiales cortas: recursos 2 y 3 (15 min cada una).

📦 **Entregable:** sales@ funcionando, probado por el equipo, con permisos documentados.

### 📌 Semana 8: Confirmar el seguro cibernético ACTIVO

⏱️ **Tiempo estimado:** 30 min + seguimiento al broker

**Pasos:**
1. Con la cotización aprobada por Miguel, coordina la firma/pago con el broker (Miguel paga, tú persigues).
2. Pide al broker el documento de confirmación (póliza o 'binder' = confirmación provisional de que ya estás cubierto mientras emiten la póliza).
3. Guarda el PDF en proyectos/it/evidencias/ y anota en el inventario: fecha de inicio, coberturas, límite y a quién llamar si pasa algo (el número de reclamos 24/7).
4. Escribe el mini-proceso 'qué hacer si nos hackean' (media página): 1. desconectar el equipo, 2. llamar al MSP, 3. llamar al número de la aseguradora, 4. avisar a Miguel. Pégalo en proyectos/it/procesos/incidente-ciber.md.

📦 **Entregable:** Seguro activo con documento guardado + plan de incidente de media página.

### 📌 Semana 9: Primera auditoría trimestral de accesos

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Auditoría de accesos = revisar quién puede entrar a qué, y quitar lo que sobra.
2. Copia la plantilla 'Checklist de auditoría trimestral' (abajo) a proyectos/it/auditorias/2026-Q3.md.
3. Recorre plataforma por plataforma (M365, HubSpot, inFlow, Woo, QBO, 1Password, Backblaze, Zapier) respondiendo: ¿todos los usuarios siguen en la empresa? ¿alguien tiene más permisos de los que necesita? ¿hay cuentas genéricas sin dueño?
4. Quita/reduce lo que encuentres en el momento y anótalo en el checklist.
5. Fírmalo con fecha y agenda la próxima: primera semana de diciembre 2026.

📦 **Entregable:** Primera auditoría trimestral ejecutada y firmada — rutina continua ya en marcha.

### 📌 Semana 9: Documentar procesos IT — parte 1 (1Password, MFA, Backblaze)

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Usa la 'Plantilla de documento de proceso' (abajo) para crear 3 archivos en proyectos/it/procesos/: 1password.md, mfa.md, backblaze.md.
2. En cada uno responde las 5 preguntas de la plantilla en lenguaje simple: qué es, quién lo usa, cómo se hace lo cotidiano (alta/baja de empleado, restaurar archivo), qué hacer si falla, dónde están las evidencias.
3. Regla del criterio 10: alguien que no seas tú debería poder seguir el documento sin llamarte.
4. Commit en GitHub Desktop: 'Docs IT parte 1'.

📦 **Entregable:** 3 procesos documentados que cualquiera puede seguir.

### 📌 Semana 9: Documentar procesos IT — parte 2 (MSP, seguro, M365)

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Crea otros 3 archivos en proyectos/it/procesos/: msp.md (cómo pedir soporte, SLA, check-in mensual), seguro-ciber.md (qué cubre, número de reclamos, renovación anual), m365-usuarios.md (alta de usuario, baja de usuario sin perder correo, reset de contraseña).
2. Para la baja de usuario en M365 documenta los 4 pasos: bloquear inicio de sesión → convertir su buzón en compartido → quitar licencia → quitar de 1Password y demás plataformas (esto conecta con tu checklist de auditoría).
3. Commit: 'Docs IT parte 2 — área IT 100% documentada'.

📦 **Entregable:** 6 procesos IT documentados en total. Criterio 10 cubierto para esta área.

### 📌 Semana 10: Primer check-in mensual con MSP + revisión mensual Backblaze

⏱️ **Tiempo estimado:** Reunión 30min con MSP + 15min de revisión

**Pasos:**
1. Haz la reunión mensual de 30 min con el MSP usando la agenda de la plantilla 'Rutina mensual' (abajo): tickets del mes, algo pendiente, algo por venir.
2. Haz la revisión Backblaze de 10 min: panel de Groups → todas las compus con backup < 3 días → persigue rojos.
3. Guarda la minuta del check-in en proyectos/it/msp-checkins/2026-09.md (3 líneas bastan).
4. Ya tienes la rutina continua girando: esto es exactamente lo que la guía de rol pide 'para siempre'.

📦 **Entregable:** Primera minuta de check-in MSP + revisión Backblaze del mes hecha.

### 📌 Semana 10: Armar la carpeta de evidencias para el 16-sep

⏱️ **Tiempo estimado:** 1 sesión de 1h

**Pasos:**
1. Revisa proyectos/it/evidencias/ y completa lo que falte: captura de 1Password People (11/11 activos), tabla MFA en verde con capturas, panel Backblaze en verde, contrato MSP, póliza/binder del seguro, captura de sales@ con permisos.
2. Crea proyectos/it/resumen-evaluacion-it.md: una página con los criterios 7, 8, 9 (+ M365 y docs) y al lado de cada uno: LISTO + dónde está la prueba.
3. Marca en rojo cualquier hueco que quede y su plan de cierre para la semana 11.

📦 **Entregable:** Carpeta de evidencias completa + resumen de 1 página listo para mostrar.

### 📌 Semana 11: Repaso final: ensayo de la evaluación

⏱️ **Tiempo estimado:** 1 sesión de 1h (lun 14 o mar 15 sep)

**Pasos:**
1. Relee tu resumen-evaluacion-it.md y ensaya en voz alta la respuesta de 1 minuto por criterio: '1Password: 11 de 11, cero contraseñas compartidas, aquí está la consola'.
2. Verifica EN VIVO (no de memoria) los 3 paneles: 1Password People, Backblaze Groups, tabla MFA — que estén verdes ese mismo día.
3. Cierra cualquier rojo pendiente o prepara la frase honesta: 'esto está al 90%, se cierra el [fecha] porque [razón]'.
4. Envía el resumen a Miguel un día antes de la evaluación — que no haya sorpresas el 16.

📦 **Entregable:** Área IT lista para defenderse sola el 16 de septiembre.

---

## 📚 Recursos de aprendizaje

- **[Microsoft Learn — Conceptos básicos de Microsoft 365 (path gratuito)](https://learn.microsoft.com/es-es/training/paths/m365-fundamentals/)** — curso, haz solo los módulos de admin/seguridad: ~1.5h (el path completo ~6h)
  - ¿Por qué?: Es EL curso oficial gratuito para entender qué administra un admin de M365; te da vocabulario para hablar con el MSP sin sentirte perdido.
- **[Microsoft Learn — Crear un buzón compartido](https://learn.microsoft.com/es-es/microsoft-365/admin/email/create-a-shared-mailbox)** — documentación, 15 min
  - ¿Por qué?: Guía oficial paso a paso para crear sales@ — es exactamente la tarea de la semana 8.
- **[Microsoft Learn — Dar permisos de buzón (Full Access y Send As)](https://learn.microsoft.com/es-es/microsoft-365/admin/add-users/give-mailbox-permissions-to-another-user)** — documentación, 15 min
  - ¿Por qué?: Explica los dos permisos que necesitas dominar para el criterio de M365: leer el buzón de otro y enviar como otro.
- **[Microsoft Learn — Valores predeterminados de seguridad (MFA fácil)](https://learn.microsoft.com/es-es/entra/fundamentals/security-defaults)** — documentación, 20 min
  - ¿Por qué?: Es la forma más simple (un interruptor) de obligar MFA a toda la empresa en Microsoft 365 sin pagar licencias extra.
- **[1Password — Guía para empresas (Get started with 1Password Business)](https://support.1password.com/explore/business/)** — documentación, 45 min
  - ¿Por qué?: La guía oficial de despliegue: crear cuenta, invitar gente, bóvedas y permisos — cubre las semanas 2 y 3 completas.
- **[1Password — Crear y compartir bóvedas](https://support.1password.com/create-share-vaults-teams/)** — documentación, 15 min
  - ¿Por qué?: El paso exacto para las bóvedas Sensi/Tektone/IT-Admin, que es el corazón de la política de cero contraseñas compartidas.
- **[Backblaze — Centro de ayuda (Computer Backup y Groups)](https://help.backblaze.com)** — documentación, 30 min (busca 'Groups getting started')
  - ¿Por qué?: Documentación oficial de cómo crear el grupo, invitar computadoras y leer el panel de monitoreo mensual.
- **[HubSpot Knowledge Base — autenticación de dos factores](https://knowledge.hubspot.com/account-security/set-up-two-factor-authentication)** — documentación, 10 min (si el link cambia, busca 'two-factor' en knowledge.hubspot.com)
  - ¿Por qué?: Te dice dónde exigir 2FA a todo el equipo de HubSpot — tarea de la semana 4.
- **[Intuit — página de seguridad de tu cuenta (2-step verification)](https://accounts.intuit.com/app/account-manager/security)** — herramienta, 10 min por usuario
  - ¿Por qué?: Es la pantalla exacta donde cada usuario de QuickBooks activa su MFA — mándasela por link a Miguel y al bookkeeper.
- **[Plugin oficial 'Two-Factor' para WordPress](https://wordpress.org/plugins/two-factor/)** — herramienta, 20 min instalar y probar
  - ¿Por qué?: Plugin gratuito y mantenido por el equipo de WordPress para poner MFA a WooCommerce sin pagar nada.
- **[FTC — Cyber Insurance (guía para pequeños negocios)](https://www.ftc.gov/business-guidance/small-businesses/cybersecurity/cyber-insurance)** — documentación, 15 min
  - ¿Por qué?: Guía del gobierno de EE.UU., en lenguaje simple, sobre qué debe cubrir un seguro cibernético — te prepara para hablar con el broker sin que te vendan de más.
- **[CISA — Turn On MFA (por qué el MFA importa)](https://www.cisa.gov/secure-our-world/turn-mfa)** — documentación, 10 min
  - ¿Por qué?: Material oficial y simple para explicarle al equipo POR QUÉ les estás pidiendo el segundo candado — te ayuda con la adopción.
- **[inFlow — Centro de soporte](https://www.inflowinventory.com/support)** — documentación, 15 min (busca 'security' o 'two-factor')
  - ¿Por qué?: Para confirmar oficialmente si inFlow ofrece MFA y, si no, tener el respaldo por escrito de tu mitigación.

---

## ⚠️ Riesgos y cómo evitarlos

| Riesgo | Cómo evitarlo |
|--------|---------------|
| Los empleados no adoptan 1Password (lo instalan y no lo usan, o ni lo instalan). | Que el anuncio salga de Miguel, no de ti (semana 3). Mini-sesiones de 15 min persona por persona. Fecha límite clara. Y el truco que más funciona: migra TÚ sus contraseñas de trabajo a la bóveda — cuando la contraseña ya solo vive ahí, no les queda de otra. |
| El MSP se atrasa: la meta original era 1-jul y ya venció; buscar + decidir + firmar + onboarding puede comerse 6 semanas. | Por eso el contacto arranca en semana 2 (no en agosto). Regla de escalado: si en la semana 7 no hay contrato firmado, reunión de emergencia con Miguel presentando los 2 finalistas y pidiendo decisión en 24h. |
| El broker del seguro tarda semanas en cotizar y el criterio 9 llega en rojo al 16-sep. | Email en semana 2 con Miguel en CC + recordatorio cada lunes + llamada telefónica en semana 6 si no hay respuesta. Si el broker no reacciona en semana 7, pide a Miguel autorización para cotizar directo con un segundo broker. |
| La aseguradora exige requisitos (MFA activo, backups, contraseñas gestionadas) antes de emitir la póliza. | El orden del plan ya lo resuelve: MFA (sem. 4) y Backblaze (sem. 5) quedan listos ANTES de llenar el cuestionario de la aseguradora (sem. 5-6). Si preguntan algo que aún no tienes, responde con fecha de implementación, no con 'no'. |
| Miguel no aprueba el presupuesto completo (~$450-750/mes nuevos entre Backblaze y MSP + seguro anual). | Presentarlo en semana 1 como UNA hoja con costos exactos y recordarle que 1Password, MFA y Backblaze eran metas de mayo/junio de la propia guía de rol. Si recorta, prioriza en este orden: MFA (gratis) → 1Password → Backblaze → MSP → seguro, y deja el recorte por escrito. |
| inFlow no tiene opción de MFA nativa y te queda un hueco de seguridad en el sistema más crítico de Sensi. | Mitigación documentada: contraseña única de 20+ caracteres por usuario generada en 1Password, nunca compartida por chat, y confirmación por escrito del soporte de inFlow sobre sus opciones. La excepción documentada en tabla-mfa.md cuenta como manejo profesional del riesgo, no como falla. |
| Eres el único administrador global de Microsoft 365: si pierdes tu cuenta o tu teléfono (donde vive el MFA), nadie entra. | Cuenta 'admin de emergencia' creada en semana 7, con contraseña de 30 caracteres en la bóveda IT-Admin compartida con Miguel. Es la práctica estándar que cualquier MSP te va a aplaudir. |
| Computadoras fuera del inventario (laptops personales, gente remota) se quedan sin Backblaze ni control. | El inventario de la semana 1 pregunta explícitamente por remotos. Decide CON Miguel la regla: equipo que toca datos de la empresa → entra a Backblaze y al MSP; equipo personal → no toca datos de la empresa. Déjalo escrito en la política. |

---

## 🎯 Lo que te evalúan el 16-sep en esta área

- [ ] Criterio 7 (1Password): abres la consola en vivo y se ve People = 11/11 activos, 4 bóvedas (Sensi, Tektone, IT-Admin, MSP) y puedes decir 'cero contraseñas viven fuera de 1Password' — con la política escrita en proyectos/it/politica-contrasenas.md.
- [ ] Criterio 8 (MSP e infraestructura): contrato firmado guardado en evidencias/, canal de soporte anunciado al equipo, y la minuta del PRIMER check-in mensual (semana 10) — no solo 'contratado' sino 'ya operando'.
- [ ] Criterio 8 (infraestructura, parte 2): tabla-mfa.md toda en verde con capturas por plataforma, y el panel de Backblaze Groups mostrando todas las computadoras con backup de menos de 3 días + una restauración de prueba hecha.
- [ ] Criterio 9 (seguro ciber): PDF de la póliza o binder en evidencias/ con las 3 coberturas mínimas (robo de datos, ransomware, interrupción de negocio), más el plan de incidente de media página.
- [ ] Microsoft 365: sales@ funcionando en vivo (abres el buzón compartido delante de Miguel), permisos Full Access/Send As documentados, cuenta admin de emergencia creada.
- [ ] Criterio 10 (para esta área): 6 documentos de proceso en proyectos/it/procesos/ que cualquier persona puede seguir sin llamarte, más la primera auditoría trimestral de accesos firmada (2026-Q3).
- [ ] La frase que resume el área ante Miguel: 'Cualquier empleado nuevo entra a todos los sistemas en 1 hora siguiendo mis documentos, y si mañana me atropella un bus, nada de IT se cae'.
- [ ] Prueba de rutina continua: en el calendario se ven agendados el check-in mensual del MSP, la revisión mensual de Backblaze y la auditoría de accesos de diciembre — el sistema sigue solo.

---

## 📄 Plantillas listas para copiar y usar

### 📋 Inventario IT (proyectos/it/inventario-it.md)

````
# Inventario IT — Sensi Home + Tektone\nActualizado: [fecha] | Dueño: Jeffrey\n\n## Personas y accesos\n| # | Nombre | Empresa | 1Password | MFA M365 | MFA HubSpot | MFA QBO | MFA Woo | inFlow |\n|---|--------|---------|-----------|----------|-------------|---------|---------|--------|\n| 1 | Miguel | Sensi | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ |\n| 2 | Karine | Sensi | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ |\n| ... hasta 11 | | | | | | | | |\n\nLeyenda: ✅ activo · ❌ falta · ➖ no usa esa plataforma\n\n## Computadoras\n| Equipo | Dueño | Tipo | Empresa | Backblaze | Fecha enrolado |\n|--------|-------|------|---------|-----------|----------------|\n| PC-01 | | Laptop Win | Sensi | ⬜ | |\n\n## Estado general (semáforo)\n| Ítem | Estado | Nota |\n|------|--------|------|\n| 1Password Teams | 🔴/🟡/🟢 | |\n| MFA (5 plataformas) | 🔴/🟡/🟢 | |\n| Backblaze | 🔴/🟡/🟢 | |\n| MSP | 🔴/🟡/🟢 | |\n| Seguro ciber | 🔴/🟡/🟢 | |\n\n## Acuerdos con Miguel\n- [fecha]: [acuerdo]
````

### 📋 Preguntas exactas para llamadas con MSP

````
# Llamada con MSP: [nombre] — [fecha]\nContexto que TÚ das primero (30 seg): \"Somos dos empresas hermanas en Miami, ~11 empleados, Microsoft 365, HubSpot, inventario en inFlow, tienda WooCommerce y QuickBooks. Buscamos soporte gestionado por $300-600/mes.\"\n\n## Las 12 preguntas (haz todas)\n1. ¿Cuántos clientes de nuestro tamaño (10-20 empleados) atienden hoy?\n2. ¿Qué incluye EXACTAMENTE la tarifa mensual? (soporte, monitoreo, antivirus, parches/actualizaciones)\n3. ¿Cuál es su tiempo de respuesta garantizado (SLA) para un problema normal? ¿Y para una emergencia?\n4. ¿Soporte remoto y en sitio en Miami? ¿La visita en sitio cuesta extra?\n5. ¿Administran Microsoft 365? ¿Pueden gestionar nuestro tenant (la cuenta grande de Microsoft de la empresa)?\n6. ¿Incluyen antivirus/EDR gestionado en cada computadora? ¿Cuál usan?\n7. ¿Cómo manejan altas y bajas de empleados? ¿Cuánto tardan?\n8. ¿Nos ayudan a cumplir los requisitos del seguro cibernético?\n9. ¿Contrato mínimo? ¿Penalidad por cancelar?\n10. ¿Cobran por usuario o por equipo? → Pedir cotización para 11 usuarios.\n11. ¿Me dan 2 referencias de clientes actuales?\n12. ¿Qué NO está incluido? (proyectos especiales, hardware, cableado)\n\n## Mis notas\n- Precio dicho: $___/mes por ___\n- Me gustó: \n- Me preocupó: \n- Siguiente paso: propuesta escrita para el [fecha]
````

### 📋 Email al broker de seguros (enviar en inglés, Miguel en CC)

````
**Asunto:** Cyber insurance add-on for Sensi Home LLC — quote request\n\nHi [nombre del broker],\n\nI'm Jeffrey, Systems & RevOps Lead at Sensi Home LLC (Miguel is CC'd). We'd like to add **cyber insurance** to our current policy.\n\nAbout us: ~11 employees across Sensi Home and our sister company Tektone, Miami. We run Microsoft 365, a CRM (HubSpot), inventory software (inFlow), an online store (WooCommerce) and QuickBooks Online.\n\nWe're looking for coverage in the **$500–$1,500/year** range including, at minimum:\n1. **Data breach response** (customer notification, forensics)\n2. **Ransomware / cyber extortion**\n3. **Business interruption**\n4. If available at this tier: **funds transfer fraud / social engineering**\n\nSecurity measures in place or being completed this month: company-wide password manager (1Password), multi-factor authentication on all platforms, and automatic cloud backups (Backblaze) on all computers.\n\nCould you send us a quote or the carrier's application form? We'd like to have this active before mid-September.\n\nThanks!\nJeffrey — jeffrey@mysensihome.com\n\n---\n*Nota para ti: si el broker pide llenar un cuestionario de seguridad, llénalo DESPUÉS de las semanas 4-5 para poder responder 'sí' a MFA y backups.*
````

### 📋 Comparativa MSP + recomendación para Miguel (proyectos/it/msp-comparativa.md)

````
# Comparativa MSP — [fecha]\n\n## Parte 1: tabla comparativa\n| Criterio | MSP A: ___ | MSP B: ___ | MSP C: ___ |\n|----------|-----------|-----------|------------|\n| Precio/mes (11 usuarios) | $ | $ | $ |\n| Incluye antivirus/EDR | ⬜ | ⬜ | ⬜ |\n| Incluye parches/monitoreo | ⬜ | ⬜ | ⬜ |\n| SLA emergencia | __h | __h | __h |\n| Maneja Microsoft 365 | ⬜ | ⬜ | ⬜ |\n| Soporte en sitio Miami | ⬜ | ⬜ | ⬜ |\n| Contrato mínimo | __ meses | | |\n| Referencias verificadas | ⬜ | ⬜ | ⬜ |\n| Mi impresión (1-10) | | | |\n\n## Parte 2: recomendación (esta página se la presentas a Miguel)\n**Recomiendo: [MSP ganador] — $___/mes**\n\nPor qué (3 razones):\n1. \n2. \n3. \n\nQué pasa si NO contratamos: sin soporte cuando algo se rompa, criterio 8 de mi evaluación en rojo, y la aseguradora puede poner condiciones más duras.\n\n**Decisión que necesito de ti:** OK para pedir contrato esta semana. La evaluación es el 16-sep y el arranque toma 2-3 semanas.\n\nFirma/OK de Miguel: ________ Fecha: ________
````

### 📋 Checklist de auditoría trimestral de accesos (proyectos/it/auditorias/AAAA-Qx.md)

````
# Auditoría trimestral de accesos — [2026-Q3]\nHecha por: Jeffrey | Fecha: ______ | Próxima: [1ª semana de diciembre]\n\nPor CADA plataforma responde las 4 preguntas:\n(A) ¿Todos los usuarios siguen trabajando aquí? (B) ¿Alguien tiene más permisos de los que su trabajo necesita? (C) ¿Hay cuentas genéricas sin dueño claro? (D) ¿MFA sigue activo para todos?\n\n| Plataforma | A | B | C | D | Acción tomada |\n|------------|---|---|---|---|---------------|\n| Microsoft 365 (admin.microsoft.com → Usuarios activos) | ⬜ | ⬜ | ⬜ | ⬜ | |\n| HubSpot (Configuración → Usuarios y equipos) | ⬜ | ⬜ | ⬜ | ⬜ | |\n| inFlow (configuración → miembros del equipo) | ⬜ | ⬜ | ⬜ | ⬜ | |\n| WooCommerce (wp-admin → Usuarios) | ⬜ | ⬜ | ⬜ | ⬜ | |\n| QuickBooks (Configuración → Administrar usuarios) | ⬜ | ⬜ | ⬜ | ⬜ | |\n| 1Password (consola → People y Vaults) | ⬜ | ⬜ | ⬜ | ⬜ | |\n| Backblaze (Groups → miembros) | ⬜ | ⬜ | ⬜ | ⬜ | |\n| Zapier (miembros y conexiones) | ⬜ | ⬜ | ⬜ | ⬜ | |\n\n## Hallazgos y acciones\n1. \n2. \n\nFirmado: Jeffrey — [fecha]
````

### 📋 Rutina mensual: Backblaze + check-in MSP

````
# Rutina mensual IT (primer lunes de cada mes, ~45 min total)\n\n## 1. Revisión Backblaze (10 min)\n- [ ] Entrar al panel de Groups\n- [ ] Toda computadora con 'último backup' < 3 días → 🟢\n- [ ] Si alguna está en rojo: ¿compu apagada? ¿desinstalado? → resolver con el dueño esta semana\n- [ ] Anotar resultado en 1 línea en proyectos/it/inventario-it.md\n\n## 2. Check-in con MSP (30 min — agenda fija mensual)\n**Agenda de la llamada:**\n1. Tickets del mes: ¿cuántos, cuáles se repiten? (5 min)\n2. ¿Algo pendiente de su lado o del nuestro? (10 min)\n3. ¿Alertas de seguridad o parches importantes? (5 min)\n4. Próximo mes: cambios de personal, equipos nuevos, proyectos (10 min)\n\n**Minuta** (3 líneas en proyectos/it/msp-checkins/AAAA-MM.md):\n- Lo importante del mes:\n- Acordamos:\n- Pendiente para el próximo:
````

### 📋 Plantilla de documento de proceso (formato estándar — criterio 10)

````
# Proceso: [nombre, ej. 'Alta de empleado nuevo en IT']\nDueño: Jeffrey | Última actualización: [fecha] | Sistema: [1Password / M365 / etc.]\n\n## 1. ¿Qué es esto y para qué sirve? (2 frases simples)\n\n## 2. ¿Quién lo usa y cuándo?\n\n## 3. Pasos exactos (que alguien que no soy yo pueda seguir)\n1. Entrar a [URL exacta]\n2. Clic en [botón exacto]\n3. ...\n\n## 4. ¿Qué hacer si falla?\n- Si pasa [X] → hacer [Y]\n- Si no se resuelve → contactar a [MSP / soporte de la plataforma] en [canal]\n\n## 5. Evidencias y accesos\n- Capturas en: proyectos/it/evidencias/\n- Credenciales en: 1Password → bóveda [nombre]\n\n> Prueba del algodón: pídele a Karine que siga los pasos sin ayudarte. Si se atora, el documento aún no está terminado.
````

### 📋 Mensaje de bienvenida a 1Password (para enviar a cada empleado)

````
Hola [nombre] 👋\n\nDesde esta semana usamos **1Password** para todas las contraseñas de trabajo (lo pidió Miguel, yo te ayudo con todo).\n\n**Qué tienes que hacer hoy (10 minutos):**\n1. Busca en tu correo la invitación de 1Password y haz clic en **Join**\n2. Crea tu contraseña maestra: una frase larga que puedas recordar (ej. 4 palabras al azar). Es LA ÚNICA que memorizarás de ahora en adelante\n3. **Guarda el Emergency Kit** (PDF que te da 1Password) en un lugar seguro — imprímelo si puedes\n4. Instala la app en tu compu y la **extensión del navegador** (el mismo sitio te lleva)\n5. Instala la app en tu teléfono\n\n**Las 3 reglas nuevas:**\n- 🔒 Ninguna contraseña de trabajo fuera de 1Password\n- 🚫 Nunca más contraseñas por WhatsApp, email o Excel\n- ✨ Cuenta nueva = contraseña generada por 1Password\n\n¿Te atoras en algo? Escríbeme y en 15 minutos lo resolvemos juntos.\n— Jeffrey
````

