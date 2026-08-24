# 💎 PROYECTO: Landing Page — Club Zamrud Colombia

> **Autor del diseño:** Claude Fable 5 (sesión del 10-jul-2026)
> **Ejecutor:** Claude Sonnet (otra sesión) — este documento es tu misión completa.
> **Dueño:** Jeffrey (Jeffdevops66)
> **Estado:** ✅ Listo para ejecutar

---

## 📌 PROMPT PARA JEFFREY (copiar y pegar en la nueva sesión)

```
Lee el archivo C:/Users/Lenovo/mi-claude-personal/mi-claude-personal/proyectos/landing-club-zamrud.md
y ejecútalo paso a paso. No cambies el diseño ni el código: síguelo exacto.
Al final dame el checklist de verificación completado y los pasos para publicar.
```

> ⚠️ Ojo: hay dos carpetas `mi-claude-personal` anidadas. Todo este proyecto
> vive en la **interna** (la que ya tiene la carpeta `proyectos/`).

---

## 1. 🎯 LA MISIÓN (qué vas a construir)

Una **landing page de UNA sola página, en UN solo archivo `index.html`**, full animada, para el **Club Zamrud Colombia** — un club privado de música. El objetivo de la página es que el visitante **se una al club**: deja sus datos y recibe la **EVA 1.0** (la evaluación de ingreso).

**Reglas de oro para ti, Sonnet:**

1. ❌ **NO** uses frameworks (nada de React, Vue, Tailwind, build tools). Es HTML + CSS + JS vanilla + GSAP por CDN.
2. ❌ **NO** rediseñes ni "mejores" el diseño. El código de la sección 7 es la fuente de verdad — cópialo **EXACTO**.
3. ✅ Tu trabajo es: crear el archivo, verificarlo con el checklist de la sección 8, y explicarle a Jeffrey (en español simple, con emojis, con pasos exactos) cómo probarlo, personalizarlo y publicarlo.
4. ✅ Si encuentras un error real al probar (algo roto en consola, algo que no se ve), arréglalo con el cambio MÍNIMO posible y repórtalo.
5. ✅ Responde siempre a Jeffrey como si tuviera 10 años: simple, claro, directo.

---

## 2. 🧠 CONTEXTO DEL NEGOCIO

- **Club Zamrud Colombia** = club privado alrededor de un proyecto musical. "Zamrud" significa **esmeralda** 💎 (por eso la identidad visual es verde esmeralda — encaja perfecto con Colombia, tierra de esmeraldas).
- **EVA 1.0** = la evaluación de ingreso al club. No mide conocimiento, mide **corazón**. Evalúa exactamente 2 dimensiones:
  1. **INTERÉS REAL** — ¿de verdad te mueve esta música?
  2. **IDENTIFICACIÓN CON EL PROYECTO MUSICAL** — ¿sientes el proyecto como tuyo?
- **Ángulo de marketing:** exclusividad. *"Aquí no entra cualquiera. Entra quien lo siente."* La EVA no es una barrera aburrida: es lo que hace valioso ser miembro.

**Decisiones ya tomadas por Jeffrey (NO re-preguntar):**

| Decisión | Respuesta |
|---|---|
| Objetivo / CTA principal | **Unirse al Club Zamrud** (la EVA 1.0 es parte del proceso de entrada) |
| Copy (textos) | Creados por Fable en este documento (Jeffrey los puede editar después) |
| Estilo visual | **Oscuro + esmeralda neón** (con acentos dorados) |
| Tecnología | **1 solo archivo HTML** con GSAP por CDN |

---

## 3. 🎨 IDENTIDAD VISUAL (sistema de diseño)

### Paleta de colores

| Variable CSS | Hex | Uso |
|---|---|---|
| `--bg` | `#060807` | Fondo principal (negro profundo con tinte verde) |
| `--bg-2` | `#0b100e` | Fondo de tarjetas y franjas |
| `--bg-3` | `#101713` | Fondo de tarjetas (gradiente) |
| `--esmeralda` | `#12e68c` | Color estrella: títulos acento, botones, brillos |
| `--esmeralda-osc` | `#0a8a55` | Esmeralda oscura (gradientes) |
| `--dorado` | `#e8c15a` | Acento secundario de lujo |
| `--blanco` | `#f2f7f4` | Texto principal |
| `--gris` | `#95a39b` | Texto secundario |
| `--borde` | `rgba(18,230,140,.14)` | Bordes sutiles esmeralda |

### Tipografías (Google Fonts)

- **Syne** (600/700/800) → títulos, números, logo. Moderna, musical, con carácter.
- **Inter** (400/500/600/700) → cuerpo de texto, botones, formulario.

### Sensación general

Club nocturno premium: negro profundo, brillos esmeralda que "respiran", partículas flotando como polvo de esmeralda, barras de ecualizador vivas, dorado solo como toque de lujo. Mucho espacio negativo. Nada recargado.

---

## 4. 🗺️ ESTRUCTURA DE LA PÁGINA (de arriba a abajo)

1. **Preloader** — pantalla negra con "ZAMRUD", contador 0→100% y barra esmeralda; sube como telón.
2. **Nav fijo** — logo + enlaces (El Club / EVA 1.0 / Beneficios / botón Únete). En móvil: menú hamburguesa a pantalla completa.
3. **Hero** — título gigante "CLUB ZAMRUD" letra por letra, partículas en canvas, orbes de luz, 2 botones CTA, ecualizador animado abajo.
4. **Marquee** — cinta infinita: MÚSICA EN VIVO ✦ COMUNIDAD REAL ✦ ESMERALDA ✦ …
5. **El Club** — qué es + 3 pilares en tarjetas con efecto tilt 3D.
6. **EVA 1.0** — la joya de la página: 2 anillos de progreso animados (Interés Real / Identificación) + línea de tiempo de 3 pasos que se dibuja al hacer scroll.
7. **Beneficios** — 6 tarjetas con reveal escalonado.
8. **Stats** — franja de 4 contadores animados.
9. **Testimonios** — 3 tarjetas (⚠️ son EJEMPLOS, Jeffrey debe reemplazarlos por reales).
10. **Únete (formulario)** — nombre, email, ciudad, motivo → al enviar abre WhatsApp con el mensaje listo + animación de éxito.
11. **Footer** — redes, logo, año automático.

---

## 5. 🎬 ESPECIFICACIÓN DE ANIMACIONES (la biblia — máximo detalle)

Motor: **GSAP 3.12.5 + ScrollTrigger** (CDN jsdelivr). Todo respeta `prefers-reduced-motion`: si el usuario pide menos movimiento, se muestran los estados finales sin animar (las partículas y el ecualizador, que son puramente decorativos, se omiten). Si GSAP o ScrollTrigger no cargan (sin internet / CDN bloqueado), la página se ve completa y funcional con todo en su estado final — contadores con su número, anillos llenos, línea de pasos dibujada. Cero pantallas en blanco.

| # | Elemento | Animación | Trigger | Duración / Ease |
|---|---|---|---|---|
| A1 | Preloader contador | Número 0%→100% + barra `scaleX` 0→1 | Al cargar | 1.8s `power2.inOut` |
| A2 | Preloader salida | Panel sube `yPercent:-100` (telón) | Tras contador | 0.8s `power4.inOut` |
| A3 | Título hero | Letra por letra sube desde `translateY(110%)` con máscara `overflow:hidden` | 0.55s antes de que termine el telón | 1s, stagger 0.045, `power4.out` |
| A4 | Eyebrow, subtítulo, CTAs, scroll-hint | Fade + subida `y:30→0` escalonados | Después de las letras (solape -0.5s) | 0.8s, stagger 0.12, `power3.out` |
| A5 | Partículas hero | Canvas 2D: hasta 100 puntos esmeralda subiendo lento con parpadeo senoidal | Siempre (pausa si la pestaña está oculta) | rAF continuo |
| A6 | Ecualizador hero | 36 barras CSS `height` 8%→95%, cada una con duración/delay aleatorio | Siempre | 0.7–1.6s alternante |
| A7 | Orbes de luz | Parallax al scroll: orbe 1 baja 140px, orbe 2 sube 120px | Scroll del hero | `scrub:true` |
| A8 | Marquee | Cinta infinita CSS `translateX 0→-100%` (2 grupos idénticos = loop perfecto) | Siempre | 30s lineal |
| A9 | Reveals genéricos `[data-reveal]` | Fade + subida `y:44→0`, con `data-delay` para escalonar tarjetas | `top 86%` del viewport, una vez | 0.9s `power3.out` |
| A10 | Tarjetas `.tilt` | Rotación 3D siguiendo el mouse (máx ±8°, perspectiva 800px), vuelve suave al salir | mousemove (solo desktop) | 0.4s / 0.6s |
| A11 | Botones `.magnetic` | Efecto imán: siguen el cursor ×0.3, regresan con rebote elástico | mousemove (solo desktop) | `elastic.out(1,.4)` |
| A12 | Anillos EVA | `stroke-dashoffset` de circunferencia completa (339.3) → 0 + número central 0→100% | `top 85%`, una vez | 1.6s `power2.inOut` |
| A13 | Línea de pasos | `scaleY 0→1` desde arriba, dibujándose con el scroll | scrub 0.6 entre `top 75%` y `bottom 55%` | Ligada al scroll |
| A14 | Contadores stats | `innerText` 0→meta con redondeo, prefijo/sufijo por data-attributes | `top 88%`, una vez | 1.8s `power2.out` |
| A15 | Cursor custom | Aro esmeralda que sigue el mouse con `quickTo` (lerp), crece sobre enlaces/tarjetas | Solo `pointer:fine` | 0.35s `power3` |
| A16 | Éxito del formulario | Aparece con `scale .96→1` + fade + rebote | Al enviar | 0.6s `back.out(1.6)` |
| A17 | Nav | Gana fondo blur + borde al pasar 40px de scroll | scroll | transición CSS 0.3s |
| A18 | Menú móvil | Panel baja a pantalla completa `translateY(-102%)→0` | Clic hamburguesa | 0.55s cubic-bezier(.77,0,.18,1) |

---

## 6. 📋 PASOS EXACTOS DE EJECUCIÓN (para Sonnet)

1. **Crear la carpeta** `C:/Users/Lenovo/mi-claude-personal/mi-claude-personal/proyectos/landing-club-zamrud/` (fíjate: es la carpeta `mi-claude-personal` **interna**, la que ya tiene `proyectos/`).
2. **Crear el archivo** `index.html` dentro de esa carpeta, copiando **EXACTO** el código de la sección 7 (todo el bloque, desde `<!DOCTYPE html>` hasta `</html>`).
3. **Verificar** con el checklist de la sección 8 (abre el archivo en el navegador o usa herramientas de preview si las tienes).
4. **Entregar a Jeffrey:** confirmación + checklist completado + tabla de personalización (sección 9) + pasos de publicación (sección 10).

---

## 7. 💻 CÓDIGO COMPLETO — `index.html`

⚠️ Copiar TODO el bloque siguiente, sin cambios, a `proyectos/landing-club-zamrud/index.html`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Club Zamrud Colombia 💎 Donde la música se vive de verdad</title>
  <meta name="description" content="Club Zamrud Colombia: la comunidad privada donde la música no se escucha, se vive. Presenta la EVA 1.0 y gana tu lugar.">
  <meta name="theme-color" content="#060807">
  <meta property="og:title" content="Club Zamrud Colombia 💎">
  <meta property="og:description" content="La comunidad donde la música no se escucha — se vive. ¿Pasarías la EVA 1.0?">
  <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>💎</text></svg>">
  <script>document.documentElement.classList.add('js');</script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Syne:wght@600;700;800&display=swap" rel="stylesheet">
  <style>
    /* ============ BASE ============ */
    :root{
      --bg:#060807;
      --bg-2:#0b100e;
      --bg-3:#101713;
      --esmeralda:#12e68c;
      --esmeralda-osc:#0a8a55;
      --dorado:#e8c15a;
      --blanco:#f2f7f4;
      --gris:#95a39b;
      --borde:rgba(18,230,140,.14);
      --font-display:'Syne',system-ui,sans-serif;
      --font-body:'Inter',system-ui,sans-serif;
    }
    *,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
    html{scroll-behavior:smooth;scroll-padding-top:92px}
    body{
      background:var(--bg);
      color:var(--blanco);
      font-family:var(--font-body);
      line-height:1.6;
      overflow-x:hidden;
      -webkit-font-smoothing:antialiased;
    }
    ::selection{background:var(--esmeralda);color:#04120b}
    ::-webkit-scrollbar{width:10px}
    ::-webkit-scrollbar-track{background:var(--bg)}
    ::-webkit-scrollbar-thumb{background:#1d2a24;border-radius:6px}
    ::-webkit-scrollbar-thumb:hover{background:var(--esmeralda-osc)}
    img,svg,canvas{display:block;max-width:100%}
    a{color:inherit}

    /* ============ CURSOR CUSTOM ============ */
    .cursor{
      position:fixed;top:0;left:0;width:22px;height:22px;
      border:1.5px solid var(--esmeralda);border-radius:50%;
      pointer-events:none;z-index:9999;opacity:0;
      box-shadow:0 0 16px rgba(18,230,140,.35);
      transition:opacity .3s,width .25s,height .25s,background .25s;
    }
    body.cursor-on .cursor{opacity:.9}
    .cursor.is-hover{width:46px;height:46px;background:rgba(18,230,140,.08)}
    @media(pointer:coarse){.cursor{display:none}}

    /* ============ PRELOADER ============ */
    .preloader{
      position:fixed;inset:0;background:var(--bg);z-index:1000;
      display:none;flex-direction:column;align-items:center;justify-content:center;gap:1.6rem;
    }
    html.js .preloader{display:flex}
    .preloader__logo{
      font-family:var(--font-display);font-weight:800;
      font-size:clamp(2rem,6vw,3.4rem);
      letter-spacing:.35em;text-indent:.35em;
    }
    .preloader__logo b{color:var(--esmeralda);font-weight:800}
    .preloader__bar{
      width:min(320px,70vw);height:2px;border-radius:2px;overflow:hidden;
      background:rgba(255,255,255,.1);
    }
    .preloader__bar i{
      display:block;height:100%;width:100%;
      background:linear-gradient(90deg,var(--esmeralda),var(--dorado));
      transform:scaleX(0);transform-origin:left;
    }
    .preloader__count{
      font-family:var(--font-display);color:var(--esmeralda);
      font-size:.95rem;letter-spacing:.25em;
    }

    /* ============ NAV ============ */
    .nav{
      position:fixed;top:0;left:0;right:0;z-index:100;
      display:flex;justify-content:space-between;align-items:center;
      padding:1.1rem clamp(1.2rem,4vw,3rem);
      transition:border-color .3s;
      border-bottom:1px solid transparent;
    }
    /* El fondo con blur va en un ::before y NO en .nav: un backdrop-filter
       directo en .nav convertiría la barra en "ancla" del menú móvil fijo
       y el panel oculto se saldría a la vista al hacer scroll */
    .nav::before{
      content:'';position:absolute;inset:0;z-index:-1;
      background:rgba(6,8,7,.82);
      backdrop-filter:blur(14px);
      -webkit-backdrop-filter:blur(14px);
      opacity:0;transition:opacity .3s;
    }
    .nav--scrolled::before{opacity:1}
    .nav--scrolled{border-bottom-color:var(--borde)}
    .nav__logo{
      font-family:var(--font-display);font-weight:800;font-size:1.15rem;
      letter-spacing:.12em;text-decoration:none;z-index:120;position:relative;
    }
    .nav__logo span{color:var(--esmeralda)}
    .nav__links{display:flex;align-items:center;gap:2.2rem}
    .nav__links a{
      color:var(--blanco);text-decoration:none;font-size:.95rem;font-weight:500;
      transition:color .25s;
    }
    .nav__links a:hover{color:var(--esmeralda)}
    .nav__links .btn--small{
      background:var(--esmeralda);color:#04120b;border-radius:999px;
      padding:.6rem 1.4rem;font-size:.9rem;font-weight:600;
    }
    .nav__links .btn--small:hover{color:#04120b;box-shadow:0 0 24px rgba(18,230,140,.5)}
    .nav__burger{display:none}
    @media(max-width:820px){
      .nav__burger{
        display:flex;flex-direction:column;gap:6px;background:none;border:0;
        cursor:pointer;z-index:120;padding:8px;position:relative;
      }
      .nav__burger span{
        width:26px;height:2px;background:var(--blanco);
        transition:transform .3s,opacity .3s;border-radius:2px;
      }
      body.menu-open .nav__burger span:first-child{transform:translateY(4px) rotate(45deg)}
      body.menu-open .nav__burger span:last-child{transform:translateY(-4px) rotate(-45deg)}
      .nav__links{
        position:fixed;inset:0;z-index:110;
        background:rgba(6,8,7,.97);
        backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);
        flex-direction:column;justify-content:center;gap:2.4rem;
        transform:translateY(-102%);
        transition:transform .55s cubic-bezier(.77,0,.18,1);
      }
      .nav__links a{font-size:1.5rem;font-family:var(--font-display);font-weight:700}
      body.menu-open .nav__links{transform:translateY(0)}
      body.menu-open{overflow:hidden}
    }

    /* ============ BOTONES ============ */
    .btn{
      display:inline-flex;align-items:center;justify-content:center;gap:.5rem;
      padding:1rem 2.1rem;border-radius:999px;
      font-family:var(--font-body);font-weight:600;font-size:1rem;
      text-decoration:none;cursor:pointer;border:0;
      transition:box-shadow .3s,background .3s,border-color .3s,color .3s;
      will-change:transform;
    }
    .btn--primary{
      background:var(--esmeralda);color:#04120b;
      box-shadow:0 0 24px rgba(18,230,140,.35);
      animation:pulseGlow 2.6s ease-in-out infinite;
    }
    .btn--primary:hover{box-shadow:0 0 48px rgba(18,230,140,.65)}
    .btn--ghost{
      border:1px solid rgba(18,230,140,.35);color:var(--blanco);
      background:rgba(18,230,140,.05);
    }
    .btn--ghost:hover{border-color:var(--esmeralda);background:rgba(18,230,140,.12)}
    @keyframes pulseGlow{
      0%,100%{box-shadow:0 0 24px rgba(18,230,140,.35)}
      50%{box-shadow:0 0 40px rgba(18,230,140,.55)}
    }

    /* ============ HERO ============ */
    .hero{
      position:relative;min-height:100svh;
      display:flex;align-items:center;justify-content:center;
      text-align:center;overflow:hidden;
      padding:7.5rem 1.5rem 5rem;
    }
    #particles{position:absolute;inset:0;width:100%;height:100%;pointer-events:none}
    .orb{position:absolute;border-radius:50%;filter:blur(90px);opacity:.55;pointer-events:none}
    .orb--1{width:480px;height:480px;top:-12%;left:-10%;
      background:radial-gradient(circle,rgba(18,230,140,.5),transparent 70%)}
    .orb--2{width:420px;height:420px;bottom:-14%;right:-8%;
      background:radial-gradient(circle,rgba(232,193,90,.28),transparent 70%)}
    .orb--3{width:300px;height:300px;top:30%;right:18%;opacity:.35;
      background:radial-gradient(circle,rgba(18,230,140,.4),transparent 70%)}
    .hero__inner{position:relative;z-index:2;max-width:900px}
    .hero__eyebrow{
      color:var(--esmeralda);letter-spacing:.35em;font-size:.8rem;
      font-weight:600;text-transform:uppercase;margin-bottom:1.6rem;
    }
    .hero__title{
      font-family:var(--font-display);font-weight:800;
      /* máx 7.2rem: "ZAMRUD" en Syne 800 mide 7.64em de ancho y debe caber
         en el contenedor de 900px sin partirse ni desbordar */
      font-size:clamp(2.6rem,10vw,7.2rem);
      line-height:.95;letter-spacing:-.02em;text-transform:uppercase;
      margin-bottom:1.8rem;
    }
    /* nowrap: cada letra es un span independiente y sin esto el navegador
       puede partir la palabra entre letras (ej. "ZAMRU / D") */
    .hero__title .line{display:block;white-space:nowrap}
    .char-wrap{display:inline-block;overflow:hidden;vertical-align:top}
    html.js .char{display:inline-block;transform:translateY(110%)}
    .line--accent .char,.line--accent{
      background:linear-gradient(180deg,var(--esmeralda) 30%,var(--esmeralda-osc));
      -webkit-background-clip:text;background-clip:text;color:transparent;
    }
    .line--accent{filter:drop-shadow(0 0 28px rgba(18,230,140,.35))}
    .hero__sub{
      color:var(--gris);font-size:clamp(1.05rem,2.2vw,1.25rem);
      max-width:560px;margin:0 auto 2.6rem;line-height:1.7;
    }
    .hero__sub strong{color:var(--blanco)}
    .hero__cta{display:flex;gap:1rem;justify-content:center;flex-wrap:wrap}
    .hero__scroll{
      position:absolute;bottom:5.2rem;left:50%;transform:translateX(-50%);
      color:var(--gris);font-size:.78rem;letter-spacing:.25em;text-transform:uppercase;
      display:flex;flex-direction:column;align-items:center;gap:.6rem;z-index:2;
    }
    .hero__scroll span{
      width:1px;height:36px;
      background:linear-gradient(to bottom,var(--esmeralda),transparent);
      animation:scrollHint 1.8s ease-in-out infinite;
    }
    @keyframes scrollHint{
      0%{transform:scaleY(0);transform-origin:top}
      55%{transform:scaleY(1);transform-origin:top}
      56%{transform-origin:bottom}
      100%{transform:scaleY(0);transform-origin:bottom}
    }
    /* en pantallas bajas el hint se encimaría con los botones CTA */
    @media(max-width:820px){.hero__scroll{display:none}}
    .hero__eq{
      position:absolute;bottom:0;left:0;right:0;height:64px;
      display:flex;align-items:flex-end;justify-content:center;gap:6px;
      opacity:.45;z-index:1;pointer-events:none;
    }
    .hero__eq span{
      width:4px;border-radius:2px;height:20%;
      background:linear-gradient(to top,var(--esmeralda),transparent);
      animation:eq 1.1s ease-in-out infinite alternate;
    }
    @keyframes eq{from{height:8%}to{height:95%}}

    /* ============ MARQUEE ============ */
    .marquee{
      overflow:hidden;background:var(--bg-2);
      border-top:1px solid var(--borde);border-bottom:1px solid var(--borde);
      padding:1.1rem 0;display:flex;
    }
    .marquee__group{
      display:flex;flex-shrink:0;align-items:center;
      animation:marquee 30s linear infinite;
      font-family:var(--font-display);font-weight:700;font-size:1rem;
      letter-spacing:.18em;text-transform:uppercase;color:var(--gris);
      white-space:nowrap;
    }
    .marquee__group span{padding:0 1.6rem}
    .marquee__group .hl{color:var(--esmeralda)}
    @keyframes marquee{to{transform:translateX(-100%)}}

    /* ============ SECCIONES ============ */
    .section{padding:clamp(5rem,10vw,8.5rem) 1.5rem;position:relative}
    .container{max-width:1150px;margin:0 auto}
    .section__eyebrow{
      color:var(--esmeralda);letter-spacing:.35em;font-size:.78rem;
      font-weight:600;text-transform:uppercase;margin-bottom:1.2rem;
    }
    .section__title{
      font-family:var(--font-display);font-weight:700;
      font-size:clamp(2.1rem,5.4vw,3.9rem);line-height:1.06;margin-bottom:1.4rem;
    }
    .accent{
      background:linear-gradient(92deg,var(--esmeralda) 20%,var(--dorado));
      -webkit-background-clip:text;background-clip:text;color:transparent;
    }
    .section__lead{
      color:var(--gris);max-width:640px;font-size:1.08rem;
      line-height:1.75;margin-bottom:3.2rem;
    }
    .section__lead strong{color:var(--blanco)}

    /* ============ GRID + CARDS ============ */
    .grid{display:grid;gap:1.4rem}
    .grid--3{grid-template-columns:repeat(3,1fr)}
    @media(max-width:900px){.grid--3{grid-template-columns:1fr}}
    .card{
      background:linear-gradient(160deg,var(--bg-2),var(--bg-3));
      border:1px solid var(--borde);border-radius:20px;padding:2.2rem;
      transition:border-color .3s,box-shadow .3s;will-change:transform;
    }
    .card:hover{
      border-color:rgba(18,230,140,.4);
      box-shadow:0 20px 60px -20px rgba(18,230,140,.25);
    }
    .card__icon{
      font-size:2rem;margin-bottom:1.2rem;display:inline-block;
      filter:drop-shadow(0 0 12px rgba(18,230,140,.5));
    }
    .card h3{font-family:var(--font-display);font-size:1.3rem;margin-bottom:.7rem}
    .card p{color:var(--gris);line-height:1.7;font-size:.98rem}

    /* ============ EVA 1.0 ============ */
    .section--eva{
      background:
        radial-gradient(1100px 560px at 82% 8%,rgba(18,230,140,.07),transparent 60%),
        var(--bg);
    }
    .eva__rings{
      display:grid;grid-template-columns:repeat(2,minmax(0,1fr));
      gap:1.4rem;margin-bottom:4.5rem;
    }
    /* minmax(0,1fr) y min-width:0: sin esto la tarjeta no puede encoger
       menos que su contenido mínimo y desborda en celulares de 360-390px */
    @media(max-width:820px){.eva__rings{grid-template-columns:minmax(0,1fr)}}
    .ring-card{
      display:flex;align-items:center;gap:1.8rem;
      background:linear-gradient(160deg,var(--bg-2),var(--bg-3));
      border:1px solid var(--borde);border-radius:20px;padding:2rem;
    }
    .ring-card>div:last-child{min-width:0}
    .ring-card h3{overflow-wrap:break-word}
    /* en pantallas muy angostas la tarjeta se apila: anillo arriba, texto abajo */
    @media(max-width:480px){.ring-card{flex-direction:column;align-items:flex-start}}
    .ring{position:relative;width:130px;height:130px;flex-shrink:0}
    .ring svg{width:100%;height:100%;transform:rotate(-90deg);overflow:visible}
    .ring circle{fill:none;stroke-width:8;stroke-linecap:round}
    .ring circle.track{stroke:rgba(255,255,255,.07)}
    .ring circle.bar{
      stroke:var(--esmeralda);
      filter:drop-shadow(0 0 6px rgba(18,230,140,.6));
    }
    .ring--gold circle.bar{
      stroke:var(--dorado);
      filter:drop-shadow(0 0 6px rgba(232,193,90,.6));
    }
    .ring__num{
      position:absolute;inset:0;display:grid;place-items:center;
      font-family:var(--font-display);font-weight:700;
      font-size:1.5rem;color:var(--esmeralda);
    }
    .ring--gold .ring__num{color:var(--dorado)}
    .ring-card h3{font-family:var(--font-display);font-size:1.25rem;margin-bottom:.5rem}
    .ring-card p{color:var(--gris);font-size:.95rem;line-height:1.65}

    .steps{position:relative;max-width:700px}
    .steps__line{
      position:absolute;left:11px;top:8px;bottom:8px;width:2px;
      background:rgba(255,255,255,.08);
    }
    .steps__line i{
      position:absolute;inset:0;display:block;
      background:linear-gradient(to bottom,var(--esmeralda),var(--dorado));
      transform:scaleY(0);transform-origin:top;
    }
    .step{display:flex;gap:1.5rem;padding-bottom:2.6rem;position:relative}
    .step:last-child{padding-bottom:0}
    .step__dot{
      width:24px;height:24px;border-radius:50%;flex-shrink:0;margin-top:2px;
      border:2px solid var(--esmeralda);background:var(--bg);
      box-shadow:0 0 12px rgba(18,230,140,.45);position:relative;z-index:1;
    }
    .step__num{
      font-family:var(--font-display);color:var(--esmeralda);
      font-size:.8rem;letter-spacing:.25em;margin-bottom:.3rem;
    }
    .step h3{font-family:var(--font-display);font-size:1.25rem;margin-bottom:.4rem}
    .step p{color:var(--gris);font-size:.98rem;line-height:1.65}

    /* ============ STATS ============ */
    .stats{
      background:var(--bg-2);
      border-top:1px solid var(--borde);border-bottom:1px solid var(--borde);
    }
    .stats__grid{
      display:grid;grid-template-columns:repeat(4,1fr);gap:2rem;
      max-width:1150px;margin:0 auto;padding:3.6rem 1.5rem;text-align:center;
    }
    @media(max-width:700px){.stats__grid{grid-template-columns:repeat(2,1fr)}}
    .stat__num{
      font-family:var(--font-display);font-weight:800;
      font-size:clamp(2.2rem,4.5vw,3.4rem);color:var(--esmeralda);
      text-shadow:0 0 24px rgba(18,230,140,.35);line-height:1.1;
    }
    .stat__label{color:var(--gris);margin-top:.5rem;font-size:.92rem}

    /* ============ TESTIMONIOS ============ */
    .quote{position:relative}
    .quote::before{
      content:'“';position:absolute;top:1rem;right:1.6rem;
      font-family:var(--font-display);font-size:4rem;line-height:1;
      color:rgba(18,230,140,.18);
    }
    .quote p{margin-bottom:1.4rem;font-style:italic;color:var(--blanco)}
    .quote footer{font-size:.9rem}
    .quote footer b{color:var(--esmeralda);font-style:normal}
    .quote footer span{color:var(--gris);display:block;margin-top:.15rem}

    /* ============ ÚNETE (FORM) ============ */
    .section--join{
      background:
        radial-gradient(900px 500px at 18% 90%,rgba(232,193,90,.06),transparent 60%),
        radial-gradient(900px 500px at 85% 10%,rgba(18,230,140,.07),transparent 60%),
        var(--bg);
      text-align:center;
    }
    .section--join .section__lead{margin-left:auto;margin-right:auto}
    .join__box{
      max-width:620px;margin:0 auto;text-align:left;
      background:linear-gradient(160deg,var(--bg-2),var(--bg-3));
      border:1px solid var(--borde);border-radius:24px;
      padding:clamp(1.8rem,4vw,3rem);position:relative;
    }
    .field{margin-bottom:1.3rem}
    .field label{
      display:block;font-size:.9rem;font-weight:500;
      color:var(--blanco);margin-bottom:.45rem;
    }
    .field input,.field textarea{
      width:100%;background:rgba(255,255,255,.04);
      border:1px solid rgba(255,255,255,.1);border-radius:12px;
      padding:.9rem 1rem;color:var(--blanco);
      font-family:var(--font-body);font-size:1rem;
      transition:border-color .25s,box-shadow .25s;
    }
    .field textarea{resize:vertical;min-height:110px}
    .field input:focus,.field textarea:focus{
      outline:none;border-color:var(--esmeralda);
      box-shadow:0 0 0 3px rgba(18,230,140,.15);
    }
    .field input::placeholder,.field textarea::placeholder{color:#5c6a63}
    .join__box .btn{width:100%;margin-top:.4rem}
    .form__note{
      color:var(--gris);font-size:.82rem;text-align:center;margin-top:1rem;
    }
    .form__success{
      text-align:center;padding:2.5rem 1rem;
    }
    .form__success .big{font-size:3rem;margin-bottom:1rem;display:block}
    .form__success h3{
      font-family:var(--font-display);font-size:1.5rem;
      color:var(--esmeralda);margin-bottom:.6rem;
    }
    .form__success p{color:var(--gris)}

    /* ============ FOOTER ============ */
    .footer{
      border-top:1px solid var(--borde);
      padding:3.2rem 1.5rem 2.4rem;text-align:center;color:var(--gris);
    }
    .footer__logo{
      font-family:var(--font-display);font-weight:800;font-size:1.3rem;
      color:var(--blanco);letter-spacing:.12em;margin-bottom:1.4rem;display:block;
    }
    .footer__logo span{color:var(--esmeralda)}
    .footer__social{display:flex;justify-content:center;gap:1.8rem;margin-bottom:1.6rem}
    .footer__social a{
      color:var(--blanco);text-decoration:none;font-size:.95rem;
      transition:color .25s;
    }
    .footer__social a:hover{color:var(--esmeralda)}
    .footer small{font-size:.85rem}

    /* ============ REDUCED MOTION ============ */
    @media (prefers-reduced-motion:reduce){
      *,*::before,*::after{
        animation-duration:.01ms!important;
        animation-iteration-count:1!important;
        transition-duration:.01ms!important;
      }
      html{scroll-behavior:auto}
      html.js .char{transform:none}
    }
  </style>
</head>
<body>

  <!-- Cursor custom (solo desktop) -->
  <div class="cursor" aria-hidden="true"></div>

  <!-- Preloader -->
  <div class="preloader" aria-hidden="true">
    <div class="preloader__logo">ZAM<b>RUD</b></div>
    <div class="preloader__bar"><i></i></div>
    <div class="preloader__count">0%</div>
  </div>

  <!-- Nav -->
  <header class="nav" id="nav">
    <a class="nav__logo" href="#inicio">💎 CLUB <span>ZAMRUD</span></a>
    <nav class="nav__links" id="navLinks">
      <a href="#club">El Club</a>
      <a href="#eva">EVA 1.0</a>
      <a href="#beneficios">Beneficios</a>
      <a href="#unete" class="btn--small">Únete</a>
    </nav>
    <button class="nav__burger" id="burger" aria-label="Abrir menú" aria-expanded="false" aria-controls="navLinks">
      <span></span><span></span>
    </button>
  </header>

  <!-- ============ HERO ============ -->
  <section class="hero" id="inicio">
    <canvas id="particles" aria-hidden="true"></canvas>
    <div class="orb orb--1" aria-hidden="true"></div>
    <div class="orb orb--2" aria-hidden="true"></div>
    <div class="orb orb--3" aria-hidden="true"></div>

    <div class="hero__inner">
      <p class="hero__eyebrow" data-hero>◆ Club privado de música · Colombia</p>
      <h1 class="hero__title">
        <span class="line">CLUB</span>
        <span class="line line--accent">ZAMRUD</span>
      </h1>
      <p class="hero__sub" data-hero>
        La comunidad donde la música no se escucha — <strong>se vive</strong>.
        Un club privado para quienes sienten el proyecto musical como propio.
      </p>
      <div class="hero__cta" data-hero>
        <a href="#unete" class="btn btn--primary magnetic">Quiero ser parte 💎</a>
        <a href="#eva" class="btn btn--ghost magnetic">Conoce la EVA 1.0</a>
      </div>
    </div>

    <div class="hero__scroll" data-hero><span></span>Desliza</div>
    <div class="hero__eq" aria-hidden="true"></div>
  </section>

  <!-- ============ MARQUEE ============ -->
  <div class="marquee" aria-hidden="true">
    <div class="marquee__group">
      <!-- Las 6 frases van DOS veces por grupo: así cada grupo mide ~3576px
           y el loop cubre hasta monitores ultra-anchos sin dejar huecos -->
      <span>Música en vivo</span><span class="hl">✦</span>
      <span>Comunidad real</span><span class="hl">✦</span>
      <span>Esmeralda</span><span class="hl">✦</span>
      <span>Colombia</span><span class="hl">✦</span>
      <span>EVA 1.0</span><span class="hl">✦</span>
      <span>Experiencias exclusivas</span><span class="hl">✦</span>
      <span>Música en vivo</span><span class="hl">✦</span>
      <span>Comunidad real</span><span class="hl">✦</span>
      <span>Esmeralda</span><span class="hl">✦</span>
      <span>Colombia</span><span class="hl">✦</span>
      <span>EVA 1.0</span><span class="hl">✦</span>
      <span>Experiencias exclusivas</span><span class="hl">✦</span>
    </div>
    <div class="marquee__group">
      <!-- Las 6 frases van DOS veces por grupo: así cada grupo mide ~3576px
           y el loop cubre hasta monitores ultra-anchos sin dejar huecos -->
      <span>Música en vivo</span><span class="hl">✦</span>
      <span>Comunidad real</span><span class="hl">✦</span>
      <span>Esmeralda</span><span class="hl">✦</span>
      <span>Colombia</span><span class="hl">✦</span>
      <span>EVA 1.0</span><span class="hl">✦</span>
      <span>Experiencias exclusivas</span><span class="hl">✦</span>
      <span>Música en vivo</span><span class="hl">✦</span>
      <span>Comunidad real</span><span class="hl">✦</span>
      <span>Esmeralda</span><span class="hl">✦</span>
      <span>Colombia</span><span class="hl">✦</span>
      <span>EVA 1.0</span><span class="hl">✦</span>
      <span>Experiencias exclusivas</span><span class="hl">✦</span>
    </div>
  </div>

  <!-- ============ EL CLUB ============ -->
  <section class="section" id="club">
    <div class="container">
      <p class="section__eyebrow" data-reveal>El Club</p>
      <h2 class="section__title" data-reveal>
        No es un club de fans.<br><span class="accent">Es una familia musical.</span>
      </h2>
      <p class="section__lead" data-reveal>
        El <strong>Club Zamrud Colombia</strong> reúne a las personas que viven el
        proyecto musical de verdad. Como la esmeralda que nos da el nombre:
        pocos, auténticos y valiosos.
      </p>
      <div class="grid grid--3">
        <div class="card tilt" data-reveal>
          <span class="card__icon">🎤</span>
          <h3>Música en vivo</h3>
          <p>Conciertos íntimos, ensayos abiertos y noches que solo existen para los miembros del club.</p>
        </div>
        <div class="card tilt" data-reveal data-delay="0.12">
          <span class="card__icon">🤝</span>
          <h3>Comunidad verificada</h3>
          <p>Todos los que están adentro pasaron la EVA 1.0. Aquí nadie está por moda: están por amor a la música.</p>
        </div>
        <div class="card tilt" data-reveal data-delay="0.24">
          <span class="card__icon">💎</span>
          <h3>Experiencias esmeralda</h3>
          <p>Momentos únicos alrededor del proyecto musical que no se compran con dinero: se ganan con corazón.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ============ EVA 1.0 ============ -->
  <section class="section section--eva" id="eva">
    <div class="container">
      <p class="section__eyebrow" data-reveal>La entrada · EVA 1.0</p>
      <h2 class="section__title" data-reveal>
        Aquí no entra cualquiera.<br><span class="accent">Entra quien lo siente.</span>
      </h2>
      <p class="section__lead" data-reveal>
        La <strong>EVA 1.0</strong> es nuestra evaluación de ingreso. No mide
        conocimiento ni contactos: mide <strong>corazón</strong>. Solo dos cosas
        importan para ser Zamrud:
      </p>

      <div class="eva__rings">
        <div class="ring-card" data-reveal>
          <div class="ring" data-pct="100">
            <svg viewBox="0 0 120 120" aria-hidden="true">
              <circle class="track" cx="60" cy="60" r="54"></circle>
              <circle class="bar" cx="60" cy="60" r="54"></circle>
            </svg>
            <span class="ring__num">0%</span>
          </div>
          <div>
            <h3>Interés real</h3>
            <p>¿De verdad te mueve esta música? No buscamos seguidores de paso: buscamos personas a las que el proyecto les late en el pecho.</p>
          </div>
        </div>
        <div class="ring-card" data-reveal data-delay="0.15">
          <div class="ring ring--gold" data-pct="100">
            <svg viewBox="0 0 120 120" aria-hidden="true">
              <circle class="track" cx="60" cy="60" r="54"></circle>
              <circle class="bar" cx="60" cy="60" r="54"></circle>
            </svg>
            <span class="ring__num">0%</span>
          </div>
          <div>
            <h3>Identificación con el proyecto musical</h3>
            <p>¿Sientes el proyecto como tuyo? Los Zamrud no ven el proyecto desde afuera: lo cargan, lo defienden y lo hacen crecer.</p>
          </div>
        </div>
      </div>

      <div class="steps">
        <div class="steps__line" aria-hidden="true"><i></i></div>
        <div class="step" data-reveal>
          <div class="step__dot" aria-hidden="true"></div>
          <div>
            <p class="step__num">PASO 01</p>
            <h3>Regístrate</h3>
            <p>Deja tus datos en el formulario de abajo. Toma menos de un minuto.</p>
          </div>
        </div>
        <div class="step" data-reveal data-delay="0.1">
          <div class="step__dot" aria-hidden="true"></div>
          <div>
            <p class="step__num">PASO 02</p>
            <h3>Presenta la EVA 1.0</h3>
            <p>Te la enviamos directo. No hay respuestas correctas: responde con el corazón.</p>
          </div>
        </div>
        <div class="step" data-reveal data-delay="0.2">
          <div class="step__dot" aria-hidden="true"></div>
          <div>
            <p class="step__num">PASO 03</p>
            <h3>Bienvenido al Club</h3>
            <p>Si vibras con nosotros, eres Zamrud. Acceso a la comunidad, los eventos y todo lo demás.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ============ BENEFICIOS ============ -->
  <section class="section" id="beneficios">
    <div class="container">
      <p class="section__eyebrow" data-reveal>Beneficios</p>
      <h2 class="section__title" data-reveal>
        Lo que ganas al ser<br><span class="accent">miembro Zamrud</span>
      </h2>
      <div class="grid grid--3" style="margin-top:2.5rem">
        <div class="card tilt" data-reveal>
          <span class="card__icon">🎟️</span>
          <h3>Eventos exclusivos</h3>
          <p>Conciertos íntimos y noches privadas solo para miembros.</p>
        </div>
        <div class="card tilt" data-reveal data-delay="0.1">
          <span class="card__icon">🚀</span>
          <h3>Acceso anticipado</h3>
          <p>Escucha los lanzamientos antes que el resto del mundo.</p>
        </div>
        <div class="card tilt" data-reveal data-delay="0.2">
          <span class="card__icon">🎤</span>
          <h3>Cerca de los artistas</h3>
          <p>Encuentros, saludos y momentos que no se pueden comprar.</p>
        </div>
        <div class="card tilt" data-reveal>
          <span class="card__icon">🎬</span>
          <h3>Detrás de cámaras</h3>
          <p>El proceso creativo del proyecto, contado solo para el Club.</p>
        </div>
        <div class="card tilt" data-reveal data-delay="0.1">
          <span class="card__icon">🗳️</span>
          <h3>Voz y voto</h3>
          <p>Opina y decide en momentos clave del proyecto musical.</p>
        </div>
        <div class="card tilt" data-reveal data-delay="0.2">
          <span class="card__icon">💎</span>
          <h3>Estatus Zamrud</h3>
          <p>Tu insignia de miembro verificado por la EVA 1.0.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ============ STATS ============ -->
  <!-- ⚠️ EDITAR: Jeffrey, cambia estos números por los reales de tu club -->
  <div class="stats">
    <div class="stats__grid">
      <div class="stat" data-reveal>
        <div class="stat__num" data-count="2">0</div>
        <div class="stat__label">Dimensiones que mide la EVA 1.0</div>
      </div>
      <div class="stat" data-reveal data-delay="0.1">
        <div class="stat__num" data-count="3">0</div>
        <div class="stat__label">Pasos para entrar al Club</div>
      </div>
      <div class="stat" data-reveal data-delay="0.2">
        <div class="stat__num" data-count="1">0</div>
        <div class="stat__label">Comunidad esmeralda</div>
      </div>
      <div class="stat" data-reveal data-delay="0.3">
        <div class="stat__num" data-count="100" data-suffix="%">0</div>
        <div class="stat__label">Pasión por la música</div>
      </div>
    </div>
  </div>

  <!-- ============ TESTIMONIOS ============ -->
  <!-- ⚠️ EDITAR: estos testimonios son EJEMPLOS. Jeffrey debe reemplazarlos por reales antes de publicar -->
  <section class="section" id="testimonios">
    <div class="container">
      <p class="section__eyebrow" data-reveal>La familia habla</p>
      <h2 class="section__title" data-reveal>
        Ellos ya son <span class="accent">Zamrud</span>
      </h2>
      <div class="grid grid--3" style="margin-top:2.5rem">
        <div class="card quote" data-reveal>
          <p>Pensé que era un club más. La EVA me hizo entender que esto es en serio: aquí todos amamos el proyecto de verdad.</p>
          <footer><b>Nombre Ejemplo</b><span>Bogotá</span></footer>
        </div>
        <div class="card quote" data-reveal data-delay="0.12">
          <p>Estar cerca del proceso creativo y de los artistas no tiene precio. Es otra manera de vivir la música.</p>
          <footer><b>Nombre Ejemplo</b><span>Medellín</span></footer>
        </div>
        <div class="card quote" data-reveal data-delay="0.24">
          <p>Lo mejor no son los eventos: es la gente. Todos pasamos la EVA y eso se nota en cada encuentro.</p>
          <footer><b>Nombre Ejemplo</b><span>Cali</span></footer>
        </div>
      </div>
    </div>
  </section>

  <!-- ============ ÚNETE ============ -->
  <section class="section section--join" id="unete">
    <div class="container">
      <p class="section__eyebrow" data-reveal>Únete</p>
      <h2 class="section__title" data-reveal>
        Tu lugar en el Club<br><span class="accent">te está esperando</span>
      </h2>
      <p class="section__lead" data-reveal>
        Déjanos tus datos, recibe la <strong>EVA 1.0</strong> y da el primer paso
        para ser parte de la familia Zamrud.
      </p>

      <div class="join__box" data-reveal>
        <form id="joinForm">
          <div class="field">
            <label for="fNombre">Tu nombre *</label>
            <input id="fNombre" name="nombre" type="text" required placeholder="¿Cómo te llamas?" autocomplete="name">
          </div>
          <div class="field">
            <label for="fEmail">Tu correo *</label>
            <input id="fEmail" name="email" type="email" required placeholder="tucorreo@ejemplo.com" autocomplete="email">
          </div>
          <div class="field">
            <label for="fCiudad">Tu ciudad</label>
            <input id="fCiudad" name="ciudad" type="text" placeholder="Bogotá, Medellín, Cali…">
          </div>
          <div class="field">
            <label for="fMotivo">¿Por qué quieres ser parte del Club Zamrud?</label>
            <textarea id="fMotivo" name="motivo" placeholder="Cuéntanos con el corazón…"></textarea>
          </div>
          <button type="submit" class="btn btn--primary magnetic">Enviar y recibir mi EVA 1.0 💎</button>
          <p class="form__note">Al enviar se abre WhatsApp con tu mensaje listo. Sin spam, sin letra pequeña.</p>
        </form>
        <div class="form__success" hidden>
          <span class="big">💎</span>
          <h3>¡Listo! Primer paso dado.</h3>
          <p>Termina de enviar el mensaje en WhatsApp y pronto recibirás tu EVA 1.0.<br>Bienvenido al camino Zamrud.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ============ FOOTER ============ -->
  <footer class="footer">
    <span class="footer__logo">💎 CLUB <span>ZAMRUD</span></span>
    <div class="footer__social">
      <!-- ⚠️ EDITAR: los enlaces reales se ponen en CONFIG, al inicio del
           bloque de JavaScript al final de este archivo (Ctrl+F: CONFIG) -->
      <a id="linkInstagram" target="_blank" rel="noopener">Instagram</a>
      <a id="linkTiktok" target="_blank" rel="noopener">TikTok</a>
      <a id="linkYoutube" target="_blank" rel="noopener">YouTube</a>
    </div>
    <small>© <span id="year"></span> Club Zamrud Colombia · Hecho con 💎 y música</small>
  </footer>

  <!-- GSAP por CDN -->
  <script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/gsap.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/ScrollTrigger.min.js"></script>
  <script>
  // ==================================================
  // ⚙️ CONFIGURACIÓN — ⚠️ EDITAR AQUÍ (la parte MÁS importante;
  // también hay marcas ⚠️ EDITAR en las secciones STATS y TESTIMONIOS del HTML)
  // ==================================================
  const CONFIG = {
    // Número de WhatsApp del club: código de país + número, SIN el signo +
    // Ejemplo Colombia: '573001234567'
    whatsapp: '573001234567',                    // ⚠️ EDITAR
    instagram: 'https://instagram.com/',          // ⚠️ EDITAR
    tiktok: 'https://tiktok.com/',                // ⚠️ EDITAR
    youtube: 'https://youtube.com/',              // ⚠️ EDITAR
  };

  // ==================================================
  // Utilidades
  // ==================================================
  const $  = (s, c = document) => c.querySelector(s);
  const $$ = (s, c = document) => Array.from(c.querySelectorAll(s));
  const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  const isTouch = window.matchMedia('(pointer: coarse)').matches;

  // ==================================================
  // Básicos: funcionan SIEMPRE, con o sin GSAP
  // ==================================================
  function setSocialLinks(){
    $('#linkInstagram').href = CONFIG.instagram;
    $('#linkTiktok').href    = CONFIG.tiktok;
    $('#linkYoutube').href   = CONFIG.youtube;
  }

  function setYear(){
    $('#year').textContent = new Date().getFullYear();
  }

  function initNav(){
    const nav = $('#nav');
    window.addEventListener('scroll', () => {
      nav.classList.toggle('nav--scrolled', window.scrollY > 40);
    }, { passive: true });

    const burger = $('#burger');
    burger.addEventListener('click', () => {
      const open = document.body.classList.toggle('menu-open');
      burger.setAttribute('aria-expanded', String(open));
    });
    $$('.nav__links a').forEach(a => a.addEventListener('click', () => {
      document.body.classList.remove('menu-open');
      burger.setAttribute('aria-expanded', 'false');
    }));
  }

  function initForm(){
    const form = $('#joinForm');
    form.addEventListener('submit', (e) => {
      e.preventDefault();
      const data = new FormData(form);
      const msg = [
        'Hola 👋 Quiero unirme al Club Zamrud Colombia 💎',
        '',
        'Nombre: ' + data.get('nombre'),
        'Correo: ' + data.get('email'),
        'Ciudad: ' + (data.get('ciudad') || '-'),
        'Por qué quiero entrar: ' + (data.get('motivo') || '-'),
      ].join('\n');
      window.open('https://wa.me/' + CONFIG.whatsapp + '?text=' + encodeURIComponent(msg), '_blank');
      form.hidden = true;
      const ok = $('.form__success');
      ok.hidden = false;
      if (window.gsap) {
        gsap.fromTo(ok,
          { opacity: 0, y: 20, scale: .96 },
          { opacity: 1, y: 0, scale: 1, duration: .6, ease: 'back.out(1.6)' }
        );
      }
    });
  }

  setSocialLinks();
  setYear();
  initNav();
  initForm();
  buildEqualizer(); // el ecualizador es animación CSS pura: funciona con o sin GSAP

  // ==================================================
  // Animaciones (solo si GSAP *y* ScrollTrigger cargaron)
  // Ojo: se validan LOS DOS. Si solo falla ScrollTrigger, llamar a
  // gsap.registerPlugin(ScrollTrigger) lanzaría un error que dejaría
  // el preloader tapando la pantalla para siempre.
  // ==================================================
  if (!window.gsap || !window.ScrollTrigger) {
    // Sin internet / CDN bloqueado: quitamos el preloader y dejamos
    // todo en su estado final — página 100% visible y usable
    mostrarEstadoFinalSinGSAP();
  } else {
    gsap.registerPlugin(window.ScrollTrigger);
    splitHeroTitle();
    initPreloader();
    initCursor();
    initParticles();
    initMagnetic();
    initTilt();
    initReveals();
    initCounters();
    initRings();
    initStepsLine();
    initParallaxOrbs();
    if (document.fonts && document.fonts.ready) {
      document.fonts.ready.then(() => ScrollTrigger.refresh());
    }
  }

  // ---- Fallback sin GSAP: deja toda la página en su estado final ----
  function mostrarEstadoFinalSinGSAP(){
    const pre = $('.preloader');
    if (pre) pre.remove();
    // Contadores de stats con su valor final (el HTML trae "0" de inicio)
    $$('[data-count]').forEach(el => {
      el.textContent = (el.dataset.prefix || '') + el.dataset.count + (el.dataset.suffix || '');
    });
    // Anillos EVA llenos y con su porcentaje correcto
    $$('.ring').forEach(ring => {
      const bar = ring.querySelector('.bar');
      const pct = parseFloat(ring.dataset.pct || 100);
      const C = 2 * Math.PI * 54;
      bar.style.strokeDasharray = C;
      bar.style.strokeDashoffset = C * (1 - pct / 100);
      ring.querySelector('.ring__num').textContent = pct + '%';
    });
    // Línea de pasos completa
    const linea = $('.steps__line i');
    if (linea) linea.style.transform = 'scaleY(1)';
  }

  // ---- Ecualizador del hero (36 barras con ritmo aleatorio) ----
  function buildEqualizer(){
    const eq = $('.hero__eq');
    if (!eq || reduceMotion) return;
    for (let i = 0; i < 36; i++) {
      const bar = document.createElement('span');
      bar.style.animationDuration = (0.7 + Math.random() * 0.9).toFixed(2) + 's';
      bar.style.animationDelay = (Math.random() * -1.5).toFixed(2) + 's';
      eq.appendChild(bar);
    }
  }

  // ---- Divide el título del hero en letras (para animarlas una a una) ----
  function splitHeroTitle(){
    $$('.hero__title .line').forEach(line => {
      const text = line.textContent;
      line.textContent = '';
      [...text].forEach(ch => {
        const wrap = document.createElement('span');
        wrap.className = 'char-wrap';
        const inner = document.createElement('span');
        inner.className = 'char';
        inner.textContent = ch === ' ' ? ' ' : ch;
        wrap.appendChild(inner);
        line.appendChild(wrap);
      });
    });
  }

  // ---- Preloader: contador + telón + entrada del hero ----
  function initPreloader(){
    const pre = $('.preloader');
    const num = $('.preloader__count');
    const bar = $('.preloader__bar i');
    if (reduceMotion) {
      pre.remove();
      heroIntro(true);
      return;
    }
    const state = { v: 0 };
    const tl = gsap.timeline();
    tl.to(state, {
      v: 100, duration: 1.8, ease: 'power2.inOut',
      onUpdate: () => {
        num.textContent = Math.round(state.v) + '%';
        gsap.set(bar, { scaleX: state.v / 100 });
      }
    })
    .to(pre, {
      yPercent: -100, duration: .8, ease: 'power4.inOut',
      onComplete: () => { pre.remove(); ScrollTrigger.refresh(); }
    }, '+=0.15')
    .add(() => heroIntro(false), '-=0.55');
  }

  // ---- Entrada del hero: letras + elementos ----
  function heroIntro(instant){
    const chars = $$('.hero__title .char');
    const items = $$('[data-hero]');
    if (instant) {
      gsap.set(chars, { y: 0 });
      gsap.set(items, { opacity: 1, y: 0 });
      return;
    }
    gsap.set(items, { opacity: 0, y: 30 });
    gsap.timeline()
      .to(chars, { y: 0, duration: 1, ease: 'power4.out', stagger: 0.045 })
      .to(items, { opacity: 1, y: 0, duration: .8, ease: 'power3.out', stagger: 0.12 }, '-=0.5');
  }

  // ---- Cursor custom con lerp ----
  function initCursor(){
    if (isTouch || reduceMotion) return;
    const c = $('.cursor');
    gsap.set(c, { xPercent: -50, yPercent: -50 });
    const qx = gsap.quickTo(c, 'x', { duration: .35, ease: 'power3' });
    const qy = gsap.quickTo(c, 'y', { duration: .35, ease: 'power3' });
    window.addEventListener('mousemove', (e) => {
      document.body.classList.add('cursor-on');
      qx(e.clientX);
      qy(e.clientY);
    });
    $$('a, button, .card').forEach(el => {
      el.addEventListener('mouseenter', () => c.classList.add('is-hover'));
      el.addEventListener('mouseleave', () => c.classList.remove('is-hover'));
    });
  }

  // ---- Partículas esmeralda (canvas del hero) ----
  function initParticles(){
    const canvas = $('#particles');
    if (!canvas || reduceMotion) return;
    const ctx = canvas.getContext('2d');
    let w, h, parts = [];

    function resize(){
      w = canvas.width = canvas.offsetWidth;
      h = canvas.height = canvas.offsetHeight;
      const n = Math.min(100, Math.floor(w / 14));
      parts = Array.from({ length: n }, () => ({
        x: Math.random() * w,
        y: Math.random() * h,
        r: Math.random() * 1.8 + .4,
        vy: -(Math.random() * .35 + .08),
        vx: (Math.random() - .5) * .15,
        a: Math.random() * .5 + .15,
        tw: Math.random() * Math.PI * 2,
      }));
    }
    resize();
    window.addEventListener('resize', resize);

    (function draw(){
      if (!document.hidden) {
        ctx.clearRect(0, 0, w, h);
        for (const p of parts) {
          p.x += p.vx;
          p.y += p.vy;
          p.tw += .02;
          if (p.y < -10) { p.y = h + 10; p.x = Math.random() * w; }
          if (p.x < -10) p.x = w + 10;
          else if (p.x > w + 10) p.x = -10;
          const alpha = p.a * (0.6 + 0.4 * Math.sin(p.tw));
          ctx.beginPath();
          ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
          ctx.fillStyle = 'rgba(18,230,140,' + alpha.toFixed(3) + ')';
          ctx.fill();
        }
      }
      requestAnimationFrame(draw);
    })();
  }

  // ---- Botones magnéticos ----
  function initMagnetic(){
    if (isTouch || reduceMotion) return;
    $$('.magnetic').forEach(btn => {
      btn.addEventListener('mousemove', (e) => {
        const r = btn.getBoundingClientRect();
        gsap.to(btn, {
          x: (e.clientX - r.left - r.width / 2) * .3,
          y: (e.clientY - r.top - r.height / 2) * .3,
          duration: .4, ease: 'power3.out',
        });
      });
      btn.addEventListener('mouseleave', () => {
        gsap.to(btn, { x: 0, y: 0, duration: .7, ease: 'elastic.out(1,.4)' });
      });
    });
  }

  // ---- Tilt 3D en tarjetas ----
  function initTilt(){
    if (isTouch || reduceMotion) return;
    $$('.tilt').forEach(card => {
      card.addEventListener('mousemove', (e) => {
        const r = card.getBoundingClientRect();
        const rx = ((e.clientY - r.top) / r.height - .5) * -8;
        const ry = ((e.clientX - r.left) / r.width - .5) * 8;
        gsap.to(card, {
          rotateX: rx, rotateY: ry, transformPerspective: 800,
          duration: .4, ease: 'power2.out',
        });
      });
      card.addEventListener('mouseleave', () => {
        gsap.to(card, { rotateX: 0, rotateY: 0, duration: .6, ease: 'power3.out' });
      });
    });
  }

  // ---- Reveals al hacer scroll ----
  function initReveals(){
    if (reduceMotion) return;
    $$('[data-reveal]').forEach(el => {
      const delay = parseFloat(el.dataset.delay || 0);
      gsap.fromTo(el,
        { opacity: 0, y: 44 },
        {
          opacity: 1, y: 0, duration: .9, delay, ease: 'power3.out',
          scrollTrigger: { trigger: el, start: 'top 86%', once: true },
        }
      );
    });
  }

  // ---- Contadores animados ----
  function initCounters(){
    $$('[data-count]').forEach(el => {
      const target = parseFloat(el.dataset.count);
      const prefix = el.dataset.prefix || '';
      const suffix = el.dataset.suffix || '';
      if (reduceMotion) {
        el.textContent = prefix + target + suffix;
        return;
      }
      const state = { v: 0 };
      ScrollTrigger.create({
        trigger: el, start: 'top 88%', once: true,
        onEnter: () => gsap.to(state, {
          v: target, duration: 1.8, ease: 'power2.out',
          onUpdate: () => { el.textContent = prefix + Math.round(state.v) + suffix; },
        }),
      });
    });
  }

  // ---- Anillos de la EVA 1.0 ----
  function initRings(){
    $$('.ring').forEach(ring => {
      const bar = ring.querySelector('.bar');
      const num = ring.querySelector('.ring__num');
      const pct = parseFloat(ring.dataset.pct || 100);
      const C = 2 * Math.PI * 54; // circunferencia (r=54) ≈ 339.29
      bar.style.strokeDasharray = C;
      bar.style.strokeDashoffset = C;
      if (reduceMotion) {
        bar.style.strokeDashoffset = C * (1 - pct / 100);
        num.textContent = pct + '%';
        return;
      }
      const state = { v: 0 };
      ScrollTrigger.create({
        trigger: ring, start: 'top 85%', once: true,
        onEnter: () => gsap.to(state, {
          v: pct, duration: 1.6, ease: 'power2.inOut',
          onUpdate: () => {
            bar.style.strokeDashoffset = C * (1 - state.v / 100);
            num.textContent = Math.round(state.v) + '%';
          },
        }),
      });
    });
  }

  // ---- Línea de pasos que se dibuja con el scroll ----
  function initStepsLine(){
    const line = $('.steps__line i');
    if (!line) return;
    if (reduceMotion) {
      line.style.transform = 'scaleY(1)';
      return;
    }
    gsap.fromTo(line, { scaleY: 0 }, {
      scaleY: 1, ease: 'none',
      scrollTrigger: {
        trigger: '.steps', start: 'top 75%', end: 'bottom 55%', scrub: .6,
      },
    });
  }

  // ---- Parallax de orbes en el hero ----
  function initParallaxOrbs(){
    if (reduceMotion) return;
    gsap.to('.orb--1', {
      y: 140,
      scrollTrigger: { trigger: '.hero', start: 'top top', end: 'bottom top', scrub: true },
    });
    gsap.to('.orb--2', {
      y: -120,
      scrollTrigger: { trigger: '.hero', start: 'top top', end: 'bottom top', scrub: true },
    });
  }
  </script>
</body>
</html>
```

---

## 8. ✅ CHECKLIST DE VERIFICACIÓN (Sonnet debe completarlo)

Abrir `index.html` en el navegador y verificar:

### Carga y hero
- [ ] Preloader: aparece "ZAMRUD", cuenta 0→100% y sube como telón.
- [ ] El título "CLUB ZAMRUD" entra letra por letra (ZAMRUD en gradiente esmeralda).
- [ ] Se ven partículas esmeralda flotando hacia arriba en el hero.
- [ ] El ecualizador (barras verdes) baila en la base del hero.
- [ ] Los 2 botones del hero tienen efecto imán con el mouse y el primario "respira" con brillo.

### Scroll
- [ ] La cinta marquee corre infinita sin saltos.
- [ ] Cada sección aparece con fade + subida al hacer scroll (una sola vez).
- [ ] Las tarjetas tienen efecto tilt 3D al pasar el mouse.
- [ ] Los 2 anillos de la EVA se llenan hasta 100% con su número contando.
- [ ] La línea vertical de los 3 pasos se dibuja al hacer scroll (esmeralda→dorado).
- [ ] Los 4 contadores de stats cuentan desde 0.
- [ ] El nav gana fondo con blur al bajar.

### Funcional
- [ ] Los enlaces del nav llevan suave a cada sección.
- [ ] El formulario NO deja enviar sin nombre/email.
- [ ] Al enviar el formulario se abre la URL de `wa.me` con el mensaje armado y aparece la tarjeta de éxito 💎. ⚠️ **NO enviar el mensaje de WhatsApp durante la prueba**: el número aún es de ejemplo (falso) — solo verificar que la URL y el texto son correctos y cerrar la pestaña.
- [ ] El año del footer es el actual (automático).
- [ ] Sin errores en la consola del navegador (F12 → Console).
- [ ] En desktop: un aro esmeralda sigue el mouse y crece sobre enlaces y tarjetas.
- [ ] Los orbes de luz del hero se mueven levemente al hacer scroll (parallax).

### Resistencia (las promesas del documento)
- [ ] Modo sin internet: con DevTools → Network → Offline (o bloqueando `cdn.jsdelivr.net`), recargar — la página se ve completa, sin pantalla negra: contadores con su número final, anillos llenos al 100%, línea de pasos dibujada.
- [ ] Con `prefers-reduced-motion` emulado (DevTools → Rendering), el contenido se ve completo en su estado final, sin animaciones.

### Responsive (F12 → modo móvil, ej. iPhone 390px)
- [ ] El menú hamburguesa abre/cierra el panel a pantalla completa.
- [ ] El título del hero no se corta ni desborda.
- [ ] Tarjetas en 1 columna, stats en 2 columnas.
- [ ] No hay scroll horizontal.

---

## 9. 🔧 PERSONALIZACIÓN RÁPIDA (tabla para Jeffrey)

Todo lo editable está marcado con `⚠️ EDITAR` dentro del código. Buscar con `Ctrl+F`:

| Qué cambiar | Dónde (buscar en el código) | Nota |
|---|---|---|
| 📱 Número de WhatsApp | `whatsapp: '573001234567'` | Código de país + número, sin `+`. **ES LO MÁS IMPORTANTE** — hasta que lo cambies, el formulario apunta a un número de ejemplo (falso). No publicar sin cambiarlo |
| 📸 Redes sociales | `instagram:`, `tiktok:`, `youtube:` en `CONFIG` | Pegar las URLs reales |
| 🔢 Números de stats | `data-count="2"` etc. en la sección STATS | Cambiar número y etiqueta |
| 💬 Testimonios | Sección `TESTIMONIOS` | **Reemplazar los ejemplos por testimonios reales antes de publicar** |
| 🎨 Colores | Variables en `:root` al inicio del CSS | Ej. cambiar `--esmeralda` cambia toda la página |
| ✍️ Cualquier texto | Directo en el HTML | Los textos son de Fable; se pueden ajustar libremente |

---

## 10. 🚀 PUBLICAR GRATIS (pasos exactos para Jeffrey)

**Opción A — Netlify Drop (la más fácil, 2 minutos):**
1. Entra a https://app.netlify.com/drop
2. Arrastra la **carpeta** `landing-club-zamrud` (la que contiene `index.html`) a la página.
3. Netlify te da una URL tipo `https://algo-random.netlify.app` → ¡ya está en línea! 🎉
4. (Opcional) Crea cuenta gratis para cambiar el nombre de la URL o conectar dominio propio.

**Opción B — GitHub Pages (usando el repo que ya tienes):**
1. Sube la carpeta al repo `mi-claude-personal` con GitHub Desktop (commit + push).
2. En GitHub: repo → Settings → Pages → Source: `main` → carpeta raíz → Save.
3. La página queda en `https://jeffdevops66.github.io/mi-claude-personal/proyectos/landing-club-zamrud/`

---

## 📎 NOTAS FINALES DE FABLE

- El PDF original (`EVA 1.0.md`) venía bloqueado por una herramienta de pago — solo se rescataron los conceptos: **EVA 1.0, interés real, identificación con el proyecto musical, Club Zamrud Colombia**. Todo el copy fue creado desde esos conceptos. Si Jeffrey consigue el pitch completo, los textos se actualizan fácil (sección 9).
- La página funciona **offline** (sin GSAP se ve completa, solo sin animaciones) y respeta `prefers-reduced-motion` (accesibilidad).
- El formulario **no tiene backend**: usa WhatsApp como canal (perfecto para un club en Colombia). Si algún día Jeffrey quiere guardar los registros en una hoja de cálculo, se puede conectar con Formspree o un zap de Zapier — pero eso es un proyecto aparte.
