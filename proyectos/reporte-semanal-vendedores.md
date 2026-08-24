# 📊 Proyecto: Reporte Semanal de Vendedores (para pegar en otro chat con Sonnet)

> **Cómo usarlo (3 pasos):**
> 1. Abre un chat nuevo con Claude (Sonnet) que tenga tu **conector de HubSpot** activo.
> 2. Copia TODO lo que está dentro del recuadro grande de abajo (desde `Eres un analista...` hasta el final).
> 3. Pégalo y envía. Cada **viernes** repites el paso 2-3 y te entrega el reporte de esa semana. ✅

---

## ⬇️ COPIA DESDE AQUÍ ⬇️

Eres un analista de ventas experto. Tu trabajo es armar el **Reporte Semanal de Vendedores** de mi empresa usando el **conector de HubSpot** (todos los datos salen de HubSpot). El reporte debe ser **claro, visual y útil** — NADA de gráficas confusas. Habla en español, sencillo.

Mi usuario de GitHub es Jeffdevops66 y trabajo con inFlow sincronizado a HubSpot: las **ventas (SO = Sales Orders)** y las **cotizaciones (SQ = Sales Quotes)** ya viven en HubSpot como *deals*.

### 🎯 QUÉ DEBE MOSTRAR EL REPORTE (por cada vendedor)
1. 💰 **Ventas (SO)** de la semana: cuántas y por cuánto dinero (monto total).
2. 📝 **Cotizaciones (SQ)** de la semana: cuántas y por cuánto dinero.
3. 📞 **Llamadas** hechas.
4. 🤝 **Visitas** (reuniones).
5. ✉️ **Correos** enviados.
6. 🏆 Un **ranking** del que más vendió al que menos.

### 🗓️ RANGO DE FECHAS
- La "semana" = de **lunes 00:00** a **viernes 23:59** de la **semana actual** (calcúlala tú a partir de la fecha de hoy).
- Al inicio del reporte escribe claramente: "Semana del [lunes] al [viernes]".

### 🔎 PASO 1 — INVESTIGA PRIMERO (no adivines nombres)
Antes de calcular, descubre en MI HubSpot:
- La **lista de vendedores** (owners activos del equipo de ventas).
- Los **pipelines y etapas** de deals: identifica cuál etapa representa una **venta cerrada/ganada (SO)** y cómo se distinguen las **cotizaciones (SQ)** (puede ser otro pipeline, otra etapa, u otra propiedad). Si hay un pipeline llamado "Sales Order/Ventas" y otro "Quote/Cotización", úsalos.
- Los objetos de actividad: **calls (llamadas)**, **meetings (reuniones/visitas)** y **emails (correos)**.
Si algo no queda claro, dime qué encontraste y qué supuesto tomaste, luego continúa (no te detengas).

### 🧮 PASO 2 — CALCULA (agrupa TODO por vendedor / hubspot_owner_id)
- **Ventas (SO)**: deals con etapa = cerrada-ganada cuya fecha de cierre (`closedate`) cae dentro de la semana. Cuenta cuántos y suma el `amount`.
- **Cotizaciones (SQ)**: deals/cotizaciones creados dentro de la semana. Cuenta cuántas y suma el `amount`.
- **Llamadas**: objetos "call" con fecha (`hs_timestamp`) dentro de la semana.
- **Visitas**: objetos "meeting" con fecha dentro de la semana.
- **Correos**: objetos "email" enviados con fecha dentro de la semana.
- Si un vendedor no tuvo actividad en algo, pon **0** (no lo omitas).
- Calcula también los **totales del equipo**.

### 🖼️ PASO 3 — ENTRÉGAME 2 COSAS

**(A) Un resumen corto en el chat** (máximo 3 líneas, nada más), así:
- 🏆 [nombre] fue el top con $[monto] en ventas.
- 💰 Equipo: $[monto] en [N] ventas (SO), $[monto] en [N] cotizaciones (SQ).
- ⚠️ 1 alerta o recomendación, solo si hay algo importante que decir (si no hay nada raro, omite esta línea).

**(B) El correo en HTML** listo para enviar, usando EXACTAMENTE esta plantilla (rellena los valores reales, repite las filas `<tr>` por cada vendedor, ordena de mayor a menor venta, y en las barras usa `width` proporcional a las ventas del vendedor respecto al que más vendió):

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Reporte Semanal de Vendedores</title>
</head>
<body style="margin:0; padding:0; background-color:#f4f6f9; font-family:Arial, Helvetica, sans-serif; color:#1f2937;">
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0" style="background-color:#f4f6f9; padding:24px 0;">
    <tr>
      <td align="center">
        <table role="presentation" width="640" cellpadding="0" cellspacing="0" style="width:640px; max-width:100%; background-color:#ffffff; border-radius:12px; overflow:hidden; box-shadow:0 2px 8px rgba(0,0,0,0.06);">

          <!-- ENCABEZADO -->
          <tr>
            <td style="background-color:#1d4ed8; padding:28px 32px;">
              <div style="font-size:22px; font-weight:bold; color:#ffffff;">📊 Reporte Semanal de Vendedores</div>
              <div style="font-size:14px; color:#c7d2fe; margin-top:6px;">Semana del {{FECHA_LUNES}} al {{FECHA_VIERNES}}</div>
            </td>
          </tr>

          <!-- RESUMEN DEL EQUIPO (2 cajas) -->
          <tr>
            <td style="padding:24px 32px 8px 32px;">
              <table role="presentation" width="100%" cellpadding="0" cellspacing="0">
                <tr>
                  <td width="50%" style="padding:6px;">
                    <div style="background-color:#eff6ff; border-radius:10px; padding:14px; text-align:center;">
                      <div style="font-size:20px; font-weight:bold; color:#1d4ed8;">${{VENTAS_TOTAL}}</div>
                      <div style="font-size:12px; color:#6b7280;">💰 Ventas (SO) esta semana</div>
                    </div>
                  </td>
                  <td width="50%" style="padding:6px;">
                    <div style="background-color:#faf5ff; border-radius:10px; padding:14px; text-align:center;">
                      <div style="font-size:20px; font-weight:bold; color:#9333ea;">🏆 {{TOP_VENDEDOR}}</div>
                      <div style="font-size:12px; color:#6b7280;">Vendedor de la semana</div>
                    </div>
                  </td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- TABLA DETALLE (incluye ranking implícito: ya va ordenada mayor a menor) -->
          <tr>
            <td style="padding:16px 32px 24px 32px;">
              <div style="font-size:16px; font-weight:bold; margin-bottom:12px;">📋 Detalle por vendedor</div>
              <table role="presentation" width="100%" cellpadding="0" cellspacing="0" style="border-collapse:collapse; font-size:13px;">
                <thead>
                  <tr style="background-color:#f3f4f6;">
                    <th align="left"   style="padding:10px 8px; border-bottom:2px solid #e5e7eb;">Vendedor</th>
                    <th align="center" style="padding:10px 8px; border-bottom:2px solid #e5e7eb;">💰 SO</th>
                    <th align="right"  style="padding:10px 8px; border-bottom:2px solid #e5e7eb;">$ Ventas</th>
                    <th align="center" style="padding:10px 8px; border-bottom:2px solid #e5e7eb;">📝 SQ</th>
                    <th align="right"  style="padding:10px 8px; border-bottom:2px solid #e5e7eb;">$ Cotiz.</th>
                    <th align="center" style="padding:10px 8px; border-bottom:2px solid #e5e7eb;">📞</th>
                    <th align="center" style="padding:10px 8px; border-bottom:2px solid #e5e7eb;">🤝</th>
                    <th align="center" style="padding:10px 8px; border-bottom:2px solid #e5e7eb;">✉️</th>
                  </tr>
                </thead>
                <tbody>
                  <!-- Repite este <tr> por cada vendedor (ordenados por ventas, mayor a menor) -->
                  <tr>
                    <td style="padding:10px 8px; border-bottom:1px solid #f0f0f0;"><strong>{{VENDEDOR_NOMBRE}}</strong></td>
                    <td align="center" style="padding:10px 8px; border-bottom:1px solid #f0f0f0;">{{SO_CANT}}</td>
                    <td align="right"  style="padding:10px 8px; border-bottom:1px solid #f0f0f0;">${{SO_MONTO}}</td>
                    <td align="center" style="padding:10px 8px; border-bottom:1px solid #f0f0f0;">{{SQ_CANT}}</td>
                    <td align="right"  style="padding:10px 8px; border-bottom:1px solid #f0f0f0;">${{SQ_MONTO}}</td>
                    <td align="center" style="padding:10px 8px; border-bottom:1px solid #f0f0f0;">{{LLAMADAS}}</td>
                    <td align="center" style="padding:10px 8px; border-bottom:1px solid #f0f0f0;">{{VISITAS}}</td>
                    <td align="center" style="padding:10px 8px; border-bottom:1px solid #f0f0f0;">{{CORREOS}}</td>
                  </tr>
                  <!-- fin fila vendedor -->
                </tbody>
                <tfoot>
                  <tr style="background-color:#f9fafb; font-weight:bold;">
                    <td style="padding:10px 8px; border-top:2px solid #e5e7eb;">TOTAL EQUIPO</td>
                    <td align="center" style="padding:10px 8px; border-top:2px solid #e5e7eb;">{{SO_CANT_TOTAL}}</td>
                    <td align="right"  style="padding:10px 8px; border-top:2px solid #e5e7eb;">${{VENTAS_TOTAL}}</td>
                    <td align="center" style="padding:10px 8px; border-top:2px solid #e5e7eb;">{{SQ_CANT_TOTAL}}</td>
                    <td align="right"  style="padding:10px 8px; border-top:2px solid #e5e7eb;">${{COTIZACIONES_TOTAL}}</td>
                    <td align="center" style="padding:10px 8px; border-top:2px solid #e5e7eb;">{{LLAMADAS_TOTAL}}</td>
                    <td align="center" style="padding:10px 8px; border-top:2px solid #e5e7eb;">{{VISITAS_TOTAL}}</td>
                    <td align="center" style="padding:10px 8px; border-top:2px solid #e5e7eb;">{{CORREOS_TOTAL}}</td>
                  </tr>
                </tfoot>
              </table>
            </td>
          </tr>

          <!-- INSIGHT: solo si hay algo relevante, si no, quita este bloque completo -->
          <tr>
            <td style="padding:0 32px 28px 32px;">
              <div style="background-color:#eff6ff; border-left:4px solid #1d4ed8; border-radius:6px; padding:14px 16px;">
                <div style="font-size:13px; color:#374151; line-height:1.5;">💡 {{INSIGHT_Y_RECOMENDACION}}</div>
              </div>
            </td>
          </tr>

          <!-- PIE -->
          <tr>
            <td style="background-color:#f3f4f6; padding:16px 32px; text-align:center; font-size:11px; color:#9ca3af;">
              Reporte generado automáticamente · Datos de HubSpot · {{FECHA_VIERNES}}
            </td>
          </tr>

        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

### ✅ REGLAS IMPORTANTES
- Reemplaza TODOS los `{{...}}` con valores reales. No dejes ninguno sin llenar.
- El bloque "💡 Conclusión" solo va si hay algo realmente relevante que decir en 1 frase corta. Si no hay nada importante, borra ese bloque `<tr>` completo del correo.
- Formatea el dinero con separador de miles (ej: `$12,450`).
- Si no hay ventas de un vendedor, la barra va en `width="0%"` y el monto en `$0`.
- Ordena vendedores de **mayor a menor venta** en la tabla y en el ranking.
- Al final, dime en una línea el rango de fechas exacto que usaste, para que yo confirme.

## ⬆️ COPIA HASTA AQUÍ ⬆️

---

## 🛠️ Notas para Jeffdevops66 (no copiar al otro chat)
- El otro chat **debe tener el conector de HubSpot activo** (el mismo que usas aquí). Si no, Sonnet no podrá leer los datos.
- "Visita" = objeto **meeting/reunión** en HubSpot. Si tú registras las visitas de otra forma (ej. una propiedad o tipo de tarea especial), dímelo y ajustamos la definición.
- Si algún viernes quieres que además lo **envíe solo por correo**, se puede automatizar después con Zapier. Este proyecto por ahora te lo **arma en el chat** para que tú lo revises y envíes. 👍
