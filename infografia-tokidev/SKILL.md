---
name: infografia-tokidev
description: "Crear infografías de LinkedIn para @tokidev.ai en HTML con canvas fijo (1080×1440px), exportación PNG. Usar cuando el usuario pida infografía, infographic LinkedIn, imagen informativa, visual educativo, o cualquier variante. Incluye todo el sistema de diseño — colores, tipografía, secciones, componentes y export listo. NO necesita explicar colores ni estructura, ya está todo aquí."
---

# Skill: Infografía LinkedIn @tokidev.ai

Genera infografías de LinkedIn en formato HTML listo para abrir en el navegador y exportar como PNG de 1080×1440px. Usa el sistema de diseño y los componentes documentados aquí. Guarda el resultado como `[tema]-linkedin.html` en la carpeta del proyecto.

---

## Flujo de trabajo

1. **Preguntar** el tema y las secciones que quiere mostrar (si no están especificadas)
2. **Planificar** las secciones: máximo 4–5 secciones numeradas + header
3. **Generar** el HTML usando los componentes y CSS del sistema de diseño
4. **Guardar** como `[tema]-linkedin.html` en `C:\Users\Usuario\OneDrive\Documentos\Claude\Projects\Contenido\`
5. **Compartir** el link al archivo

---

## Datos fijos — NUNCA cambiar

| Variable | Valor |
|---|---|
| Handle | `tokidev.ai` |
| Canvas | `1080 × 1440 px` |
| Formato export | PNG via dom-to-image |
| Idioma | Español rioplatense (voseo) |
| Font | `'Segoe UI', system-ui, -apple-system, sans-serif` |

---

## Paleta de colores

| Nombre | Hex | Uso |
|---|---|---|
| Dark Purple | `#131139` | Fondo header, cards, filas |
| Deep Dark | `#0e0c2c` | Fondo secciones alt |
| Body BG | `#0a0820` | Fondo canvas |
| Cool Orange | `#FA743F` | Acento principal, highlights |
| Good Purple | `#A406E9` | Acento secundario, gradientes |
| Aero Pink | `#DA2984` | Tags, notas, énfasis |
| Cool Red | `#F53955` | Alertas, datos negativos |
| Amber | `#f59e0b` | Tercer acento (ladrones, warnings) |

### Gradientes de marca
```css
/* Acento principal */
background: linear-gradient(135deg, #FA743F, #A406E9);

/* Divider decorativo */
background: linear-gradient(90deg, rgba(250,116,63,0.4), rgba(164,6,233,0.4), transparent);

/* Glow header derecho */
background: radial-gradient(circle, rgba(164,6,233,0.25) 0%, transparent 65%);

/* Glow header izquierdo */
background: radial-gradient(circle, rgba(250,116,63,0.18) 0%, transparent 65%);
```

---

## Estructura HTML base

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>[Tema] — tokidev.ai</title>
<style>
/* PEGAR CSS COMPLETO AQUÍ */
</style>
</head>
<body>

<div id="infographic">

  <!-- HEADER -->
  <div class="hdr">
    <div class="hdr-glow"></div>
    <div class="hdr-glow-b"></div>
    <div class="hdr-top">
      <div class="eyebrow">[Categoría] · [Subtítulo]</div>
      <div class="brand">
        <div class="brand-dot"></div>
        <div class="brand-name">tokidev.ai</div>
      </div>
    </div>
    <div class="hdr-title">
      [Título principal]<br>de <span class="hi">[palabra clave]</span>
    </div>
    <div class="hdr-pills">
      <div class="pill">Tag 1</div>
      <div class="pill">Tag 2</div>
      <div class="pill">Tag 3</div>
    </div>
  </div>

  <div class="divline"></div>

  <!-- SECCIÓN 01 -->
  <div class="sec">
    <div class="sec-hdr">
      <div class="badge">01</div>
      <div class="sec-title">Título de sección</div>
    </div>
    <!-- Contenido con componentes -->
  </div>

  <div class="divline"></div>

  <!-- SECCIÓN 02 -->
  <div class="sec alt">
    <!-- ... -->
  </div>

  <!-- ... más secciones ... -->

</div><!-- / #infographic -->

<button id="ebtn" onclick="exportPNG()">⬇ Exportar PNG — 1080 × 1440 px</button>

<script src="https://cdnjs.cloudflare.com/ajax/libs/dom-to-image/2.6.0/dom-to-image.min.js"></script>
<script>
function exportPNG() {
  var btn = document.getElementById('ebtn');
  btn.textContent = '⏳ Generando PNG...';
  btn.disabled = true;
  var el = document.getElementById('infographic');
  window.scrollTo(0, 0);
  setTimeout(function() {
    domtoimage.toPng(el, {
      bgcolor: '#0a0820',
      width: 1080,
      height: 1440,
      style: { 'overflow': 'hidden' },
      filter: function(node) {
        if (node.classList) {
          if (node.classList.contains('hdr-glow')) return false;
          if (node.classList.contains('hdr-glow-b')) return false;
        }
        return true;
      }
    })
    .then(function(dataUrl) {
      var a = document.createElement('a');
      a.download = '[tema]-linkedin-tokidev.png';
      a.href = dataUrl;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      btn.textContent = '✅ ¡PNG descargado!';
      setTimeout(function() {
        btn.textContent = '⬇ Exportar PNG — 1080 × 1440 px';
        btn.disabled = false;
      }, 2500);
    })
    .catch(function(err) {
      btn.textContent = '❌ ' + (err && err.message ? err.message.slice(0,60) : String(err).slice(0,60));
      btn.disabled = false;
    });
  }, 300);
}
</script>
</body>
</html>
```

---

## CSS completo del sistema de diseño

```css
* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  background: #0a0820;
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  display: flex; flex-direction: column;
  align-items: center; padding: 40px 20px 60px;
}

#infographic {
  width: 1080px; height: 1440px;
  min-height: 1440px; max-height: 1440px;
  background: #0a0820; overflow: hidden;
  display: flex; flex-direction: column;
  position: relative; isolation: isolate;
}

/* ── HEADER ── */
.hdr { background: #131139; padding: 36px 60px 30px; flex-shrink: 0; position: relative; overflow: hidden; }
.hdr-glow { position: absolute; top: -60px; right: -60px; width: 320px; height: 320px; background: radial-gradient(circle, rgba(164,6,233,0.25) 0%, transparent 65%); pointer-events: none; }
.hdr-glow-b { position: absolute; bottom: -80px; left: 60px; width: 280px; height: 280px; background: radial-gradient(circle, rgba(250,116,63,0.18) 0%, transparent 65%); pointer-events: none; }
.hdr-top { display: flex; align-items: center; justify-content: space-between; margin-bottom: 16px; position: relative; }
.eyebrow { font-size: 13px; font-weight: 700; letter-spacing: 0.14em; text-transform: uppercase; color: #FA743F; white-space: nowrap; }
.brand { display: flex; align-items: center; gap: 9px; }
.brand-dot { width: 11px; height: 11px; border-radius: 50%; background: linear-gradient(135deg, #FA743F, #A406E9); flex-shrink: 0; align-self: center; }
.brand-name { font-size: 22px; font-weight: 800; color: #fff; letter-spacing: -0.01em; line-height: 1; }
.hdr-title { font-size: 60px; font-weight: 900; color: #fff; letter-spacing: -0.03em; line-height: 1.04; position: relative; margin-bottom: 16px; }
.hdr-title .hi { color: #FA743F; }
.hdr-pills { display: flex; gap: 8px; flex-wrap: nowrap; position: relative; }
.pill { padding: 8px 20px; border-radius: 30px; font-size: 15px; font-weight: 600; white-space: nowrap; border: 1px solid rgba(255,255,255,0.14); color: rgba(255,255,255,0.5); }

/* ── DIVIDER ── */
.divline { height: 1px; flex-shrink: 0; background: linear-gradient(90deg, rgba(250,116,63,0.4), rgba(164,6,233,0.4), transparent); }

/* ── SECCIÓN BASE ── */
.sec { padding: 16px 60px; flex-shrink: 0; }
.sec.alt { background: #0e0c2c; }
.sec-hdr { display: flex; align-items: center; gap: 10px; margin-bottom: 12px; }
.badge { width: 38px; height: 38px; border-radius: 10px; background: linear-gradient(135deg, #FA743F, #A406E9); display: flex; align-items: center; justify-content: center; font-size: 15px; font-weight: 800; color: #fff; flex-shrink: 0; }
.sec-title { font-size: 16px; font-weight: 800; color: #fff; letter-spacing: 0.08em; text-transform: uppercase; white-space: nowrap; }
.sec-aside { margin-left: auto; font-size: 15px; color: rgba(255,255,255,0.5); white-space: nowrap; font-weight: 600; }

/* ── COMPONENTE: CHIPS DE TOKEN ── */
.token-row { display: flex; align-items: center; gap: 10px; margin-bottom: 12px; }
.chip { padding: 11px 24px; border-radius: 9px; font-size: 20px; font-weight: 700; color: #fff; white-space: nowrap; }
.chip-o { background: rgba(250,116,63,0.2);  border: 1.5px solid rgba(250,116,63,0.45); }
.chip-g { background: rgba(16,185,129,0.16); border: 1.5px solid rgba(16,185,129,0.35); }
.chip-p { background: rgba(164,6,233,0.2);   border: 1.5px solid rgba(164,6,233,0.4); }
.chip-info { font-size: 16px; color: rgba(255,255,255,0.45); background: rgba(255,255,255,0.05); padding: 10px 18px; border-radius: 8px; border: 1px solid rgba(255,255,255,0.08); margin-left: 4px; white-space: nowrap; }
.formula { background: rgba(255,255,255,0.04); border: 1px solid rgba(255,255,255,0.07); border-radius: 9px; padding: 14px 18px; font-size: 16px; color: rgba(255,255,255,0.5); text-align: center; }
.formula b { color: #fff; }

/* ── COMPONENTE: LISTA DE FILAS CON BARRA COLOR ── */
.ladr-list { display: flex; flex-direction: column; gap: 8px; }
.lrow { background: #131139; border-radius: 10px; padding: 14px 20px; border: 1px solid rgba(255,255,255,0.06); display: flex; align-items: center; gap: 14px; overflow: hidden; }
.lbar { width: 4px; border-radius: 4px; align-self: stretch; flex-shrink: 0; min-height: 30px; }
.lbar.or { background: #FA743F; }
.lbar.re { background: #F53955; }
.lbar.am { background: #f59e0b; }
.lbar.pu { background: #A406E9; }
.lbar.pk { background: #DA2984; }
.lrow-main { flex: 1; }
.lrow-name { font-size: 19px; font-weight: 700; color: #fff; white-space: nowrap; }
.lrow-tag { flex-shrink: 0; padding: 7px 18px; border-radius: 20px; font-size: 15px; font-weight: 700; white-space: nowrap; background: rgba(218,41,132,0.15); color: #DA2984; border: 1px solid rgba(218,41,132,0.25); }

/* ── COMPONENTE: GRID DE CARDS 3 COLUMNAS ── */
.tec-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; }
.tcard { background: #131139; border-radius: 11px; padding: 12px 12px; border: 1px solid rgba(255,255,255,0.06); display: flex; gap: 10px; align-items: flex-start; overflow: hidden; }
.tcard-ico { width: 42px; height: 42px; border-radius: 10px; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
.tcard-ico svg { width: 20px; height: 20px; }
.ic-bl { background: rgba(59,130,246,0.18); }
.ic-te { background: rgba(20,184,166,0.18); }
.ic-gn { background: rgba(16,185,129,0.18); }
.ic-or { background: rgba(250,116,63,0.18); }
.ic-pu { background: rgba(164,6,233,0.18); }
.ic-pk { background: rgba(218,41,132,0.18); }
.tcard h4 { font-size: 17px; font-weight: 700; color: #fff; margin-bottom: 6px; }
.tcard p { font-size: 15px; color: rgba(255,255,255,0.4); line-height: 1.45; }

/* ── COMPONENTE: COMPARACIÓN 2 COLUMNAS ── */
.iov-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
.iov-card { border-radius: 12px; padding: 14px 20px; display: flex; flex-direction: column; gap: 6px; overflow: hidden; }
.iov-card.inp-card { background: rgba(59,130,246,0.1); border: 1px solid rgba(59,130,246,0.25); }
.iov-card.out-card { background: rgba(245,57,85,0.1); border: 1px solid rgba(245,57,85,0.25); }
.iov-card-lbl { font-size: 14px; font-weight: 600; color: rgba(255,255,255,0.5); text-transform: uppercase; letter-spacing: 0.08em; }
.iov-card-price { font-size: 22px; font-weight: 900; white-space: nowrap; line-height: 1; }
.iov-card.inp-card .iov-card-price { color: #60a5fa; }
.iov-card.out-card .iov-card-price { color: #f87171; }
.iov-card-sub { font-size: 14px; font-weight: 500; color: rgba(255,255,255,0.35); white-space: nowrap; }

/* ── EXPORT BTN ── */
#ebtn { margin-top: 28px; padding: 15px 52px; background: linear-gradient(90deg, #FA743F, #A406E9); color: #fff; border: none; border-radius: 12px; font-size: 16px; font-weight: 700; cursor: pointer; font-family: 'Segoe UI', system-ui; transition: opacity 0.2s; }
#ebtn:hover { opacity: 0.85; }
#ebtn:disabled { opacity: 0.5; cursor: wait; }
```

---

## Componentes disponibles

### Header
Siempre al tope. Fondo `#131139`, título grande en blanco con `.hi` (naranja) en la palabra clave. Glow decorativo derecha (púrpura) e izquierda (naranja) — se filtran en export automáticamente.

### Sección numerada
```html
<div class="sec">  <!-- o "sec alt" para fondo #0e0c2c -->
  <div class="sec-hdr">
    <div class="badge">01</div>
    <div class="sec-title">Nombre de sección</div>
    <div class="sec-aside">nota opcional</div>  <!-- opcional -->
  </div>
  <!-- contenido -->
</div>
<div class="divline"></div>
```

### Lista con barra de color (ladrones / pros / contras)
```html
<div class="ladr-list">
  <div class="lrow">
    <div class="lbar or"></div>  <!-- or | re | am | pu | pk -->
    <div class="lrow-main">
      <div class="lrow-name">Nombre del ítem</div>
    </div>
    <div class="lrow-tag" style="background:rgba(250,116,63,0.12);color:#FA743F;border-color:rgba(250,116,63,0.25);">etiqueta</div>
  </div>
</div>
```
Colores de lbar: `or` (naranja) · `re` (rojo) · `am` (ámbar) · `pu` (púrpura) · `pk` (rosa)

### Grid 3 columnas con ícono
```html
<div class="tec-grid">
  <div class="tcard">
    <div class="tcard-ico ic-bl">
      <svg viewBox="0 0 24 24" fill="none" stroke="#3b82f6" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
        <!-- SVG path -->
      </svg>
    </div>
    <div>
      <h4>Título</h4>
      <p>Descripción corta.</p>
    </div>
  </div>
</div>
```
Colores de ícono: `ic-bl` (azul) · `ic-te` (teal) · `ic-gn` (verde) · `ic-or` (naranja) · `ic-pu` (púrpura) · `ic-pk` (rosa)

### Comparación 2 columnas (precios / métricas)
```html
<div class="iov-grid">
  <div class="iov-card inp-card">
    <div class="iov-card-lbl">Opción A</div>
    <div class="iov-card-price">$0.003</div>
    <div class="iov-card-sub">descripción corta</div>
  </div>
  <div class="iov-card out-card">
    <div class="iov-card-lbl">Opción B</div>
    <div class="iov-card-price">$0.015</div>
    <div class="iov-card-sub">descripción · <b style="color:#f87171;">5× más caro</b></div>
  </div>
</div>
```

### Chips de ejemplo de código/tokens
```html
<div class="token-row">
  <div class="chip chip-o">Hola</div>
  <div class="chip chip-g">, mundo</div>
  <div class="chip chip-p">!</div>
  <div class="chip-info">≈ 3 tokens · 1 token ≈ ¾ palabra</div>
</div>
<div class="formula">
  <b>Input + Output = costo total</b> · descripción adicional
</div>
```

---

## Reglas de layout

- **Canvas fijo:** 1080×1440px, `overflow: hidden`. Todo el contenido DEBE entrar sin scroll.
- **Padding lateral:** siempre `60px` en secciones. No variar.
- **Secciones alternadas:** `.sec` (fondo transparente) y `.sec.alt` (fondo `#0e0c2c`) para generar contraste visual.
- **Máximo 4–5 secciones** numeradas para que el contenido respire.
- **`white-space: nowrap`** en todos los nombres de ítems, tags, eyebrow y sec-title para evitar wrapping en export.
- **`overflow: hidden`** en `.lrow` y `.tcard` para contener el contenido.
- Los glows decorativos (`.hdr-glow`, `.hdr-glow-b`) se filtran en el export via dom-to-image — no afectan al PNG.

---

## Reglas de contenido

- Titulares: **directos, sin rodeos** — dato fuerte o pregunta que genere curiosidad
- Español rioplatense: "usás", "hacés", "optimizá"
- **Sin emojis** decorativos en el canvas
- **Sin gradiente en texto** (`background-clip: text`) — no renderiza en dom-to-image
- La palabra clave del título va con `.hi` (color `#FA743F`)
- Tags de `.lrow-tag`: cada fila con su color de marca (naranja, rojo, ámbar, púrpura, rosa)

---

## Exportación

- Librería: `dom-to-image` 2.6.0 desde Cloudflare CDN
- Resolución: 1080×1440px PNG
- Los glow divs se filtran vía `filter` function (no `data-html2canvas-ignore`)
- **No usar** `html2canvas` — falla con `radial-gradient` en elementos internos
- Nombre de archivo: `[tema]-linkedin-tokidev.png`
