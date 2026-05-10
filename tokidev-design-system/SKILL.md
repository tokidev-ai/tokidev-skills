---
name: tokidev-design-system
description: Apply the Tokidev design system (dark navy, coral orange, golden yellow, glassmorphism) to any web project. Use this skill whenever the user wants to: build a website with the Tokidev style, apply the tokidev colors or typography to a page, create a dark themed landing page with gradient headings and glassmorphic nav, replicate the tokidev.ia look in HTML/CSS/Tailwind, or use tokidev colors in any web component. Triggers for "tokidev style", "tokidev design", "use tokidev colors", "landing page like tokidev", "glassmorphism nav", or "dark portfolio design".
---

# Tokidev Design System

A premium dark-themed design system extracted from [tokidev-landing.vercel.app](https://tokidev-landing.vercel.app). Use it to apply a consistent, polished look across any web project.

Read `references/DESIGN.md` for the full token reference (colors, typography, component patterns). This SKILL.md contains the implementation recipes.

---

## Core Philosophy

The Tokidev aesthetic is built on three pillars:
1. **Deep dark base** — near-black navy (`#0a111a`) that feels premium, not harsh
2. **Warm gradient accents** — coral orange + golden yellow gradients used sparingly on headings and CTAs
3. **Glassmorphism depth** — frosted glass cards and navbars with subtle purple-tinted borders

Restraint is key: most content is `#f0eef2` on `#0a111a`. The orange/yellow gradients only appear on the most important headings and the primary CTA — never everywhere.

---

## Quick Setup

### CSS Custom Properties (Vanilla CSS / any framework)

```css
:root {
  /* Brand Colors */
  --brand-bg:      #0a111a;   /* Main background — deep navy */
  --brand-text:    #f0eef2;   /* Primary text — warm off-white */
  --brand-orange:  #ef6c4a;   /* Primary accent — coral orange */
  --brand-yellow:  #f5a623;   /* Secondary accent — golden yellow */
  --brand-purple:  #7b5ea7;   /* Tertiary accent — soft purple */
  --brand-border:  #7b5ea726; /* Purple at ~15% opacity — subtle borders */
  --brand-glass:   #1a102999; /* Dark glass at ~60% opacity — nav/cards */

  /* Typography */
  --font-primary: 'Inter', sans-serif;
}

body {
  background-color: var(--brand-bg);
  color: var(--brand-text);
  font-family: var(--font-primary);
  font-size: 16px;
  line-height: 1.5;
}
```

### Tailwind CSS Config Extension

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        'brand-bg':     '#0a111a',
        'brand-text':   '#f0eef2',
        'brand-orange': '#ef6c4a',
        'brand-yellow': '#f5a623',
        'brand-purple': '#7b5ea7',
        'brand-border': '#7b5ea726',
        'brand-glass':  '#1a102999',
      },
      fontFamily: {
        inter: ['Inter', 'sans-serif'],
      },
    },
  },
}
```

---

## Typography System

### H1 — Hero Heading (Gradient: white → orange, top to bottom)

```css
/* Vanilla CSS */
h1 {
  font-family: var(--font-primary);
  font-size: clamp(34px, 5vw, 60px);
  font-weight: 500;
  line-height: 1.07;
  letter-spacing: -1.8px;
  background: linear-gradient(to bottom, #ffffff 0%, #ffffff 50%, #ef6c4a 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
```

```html
<!-- Tailwind -->
<h1 class="text-[34px] sm:text-[48px] lg:text-[60px] font-medium leading-[1.07] tracking-[-1.8px] bg-linear-to-b from-white via-white via-50% to-brand-orange bg-clip-text text-transparent">
  Your heading here
</h1>
```

### H2 — Section Heading (Gradient: text → yellow, left to right)

```css
h2 {
  font-size: clamp(32px, 4vw, 38px);
  font-weight: 700;
  letter-spacing: -0.76px;
  background: linear-gradient(to right, #f0eef2 0%, #f0eef2 55%, #f5a623 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
```

```html
<!-- Tailwind -->
<h2 class="text-[32px] md:text-[38px] font-bold tracking-[-0.76px] bg-linear-to-r from-brand-text via-brand-text via-55% to-brand-yellow bg-clip-text text-transparent">
  Section title
</h2>
```

### H3 — Card / Subsection Heading

```css
h3 {
  font-size: 32px;
  font-weight: 700;
  letter-spacing: -0.64px;
  color: rgba(240, 238, 242, 0.95);
}
```

### Body / Supporting Text

```css
/* Primary body */   color: #f0eef2;       /* --brand-text */
/* Muted (60%) */    color: rgba(240, 238, 242, 0.6);
/* Subtle (40%) */   color: rgba(240, 238, 242, 0.4);
/* Accent text */    color: #ef6c4a;       /* --brand-orange */
```

---

## Component Recipes

### Glassmorphic Navigation Bar

```html
<nav class="fixed top-5 left-1/2 -translate-x-1/2 w-[92%] max-w-[1120px] h-16
            bg-[#1a102999]/65 backdrop-blur-xl border border-[#7b5ea726]
            rounded-2xl px-6 flex items-center justify-between">
  <!-- logo + links + CTA -->
</nav>
```

```css
/* Vanilla CSS */
nav {
  position: fixed;
  top: 1.25rem;
  left: 50%;
  transform: translateX(-50%);
  width: 92%;
  max-width: 1120px;
  height: 4rem;
  background: rgba(26, 16, 41, 0.6);
  backdrop-filter: blur(24px);
  border: 1px solid rgba(123, 94, 167, 0.15);
  border-radius: 1rem;
}
```

### Primary CTA Button (Orange → Yellow gradient)

```html
<!-- Tailwind -->
<a href="#contact" class="px-5 py-2.5 bg-linear-to-r from-brand-orange to-brand-yellow
                           rounded-full text-[13px] font-semibold text-white
                           hover:opacity-90 transition-opacity">
  Let's talk
</a>
```

```css
/* Vanilla CSS */
.btn-primary {
  padding: 0.625rem 1.25rem;
  background: linear-gradient(to right, #ef6c4a, #f5a623);
  border-radius: 9999px;
  font-size: 13px;
  font-weight: 600;
  color: white;
  transition: opacity 0.2s;
}
.btn-primary:hover { opacity: 0.9; }
```

### Outline / Secondary Button

```html
<a href="#projects" class="px-5 py-2.5 border border-[rgba(240,238,242,0.2)]
                            rounded-full text-[13px] font-medium text-brand-text
                            hover:border-brand-text/40 transition-colors">
  View Portfolio
</a>
```

### Glassmorphic Card

```html
<div class="bg-[#1a102999]/60 backdrop-blur-md border border-[#7b5ea726]
            rounded-2xl p-6">
  <!-- card content -->
</div>
```

### Tech / Tag Badge

```html
<span class="px-3 py-1 text-xs font-semibold rounded-full
             bg-[rgba(239,108,74,0.08)] border border-[rgba(239,108,74,0.15)]
             text-[rgba(239,108,74,0.8)] uppercase tracking-wider">
  RUST
</span>
```

### Background Ambient Glows

These colored blur circles give the page depth. Place them absolutely inside a `relative overflow-hidden` section:

```html
<!-- Orange glow (top-left hero area) -->
<div class="absolute top-0 left-1/4 w-[400px] h-[400px] rounded-full
            bg-brand-orange/20 blur-[130px] pointer-events-none"></div>

<!-- Purple glow (right side) -->
<div class="absolute top-1/4 right-0 w-[350px] h-[350px] rounded-full
            bg-brand-purple/15 blur-[120px] pointer-events-none"></div>

<!-- Yellow glow (bottom) -->
<div class="absolute bottom-0 left-1/2 w-[300px] h-[300px] rounded-full
            bg-brand-yellow/15 blur-[140px] pointer-events-none"></div>
```

---

## Full Starter Template

When the user asks for a complete page or component, use this base:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --brand-bg:      #0a111a;
      --brand-text:    #f0eef2;
      --brand-orange:  #ef6c4a;
      --brand-yellow:  #f5a623;
      --brand-purple:  #7b5ea7;
      --brand-border:  rgba(123, 94, 167, 0.15);
      --brand-glass:   rgba(26, 16, 41, 0.6);
    }
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      background: var(--brand-bg);
      color: var(--brand-text);
      font-family: 'Inter', sans-serif;
      font-size: 16px;
      line-height: 1.5;
    }
  </style>
</head>
<body>
  <!-- Your content here -->
</body>
</html>
```

---

## Implementation Notes

- **Always import Inter** from Google Fonts — it's the only typeface in this system.
- **Gradient text** requires `-webkit-background-clip: text` + `-webkit-text-fill-color: transparent` for broad browser support.
- **Glassmorphism** depends on `backdrop-filter: blur()` — check browser support if needed (it's well-supported as of 2024+).
- **Glow blurs** use very large `blur()` values (60px–150px) and low opacity (10–30%). Don't reduce the blur radius — it kills the effect.
- **Color opacity variants**: Use CSS `rgba()` or Tailwind's `/opacity` syntax (e.g., `bg-brand-orange/20`) throughout.
- For `references/DESIGN.md`, read it when you need the complete token list or want to verify specific values.
