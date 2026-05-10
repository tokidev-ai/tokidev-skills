# Tokidev Design System — Complete Reference

Extracted from [tokidev-landing.vercel.app](https://tokidev-landing.vercel.app)  
Stack: Astro v6 + Tailwind CSS v4 + Inter (Google Fonts)

---

## Color Tokens

| Token | Hex | Usage |
|-------|-----|-------|
| `--color-brand-bg` | `#0a111a` | Page background — deep navy |
| `--color-brand-text` | `#f0eef2` | Primary text — warm off-white |
| `--color-brand-orange` | `#ef6c4a` | Primary accent — coral orange |
| `--color-brand-yellow` | `#f5a623` | Secondary accent — golden yellow |
| `--color-brand-purple` | `#7b5ea7` | Tertiary accent — muted purple |
| `--color-brand-border` | `#7b5ea726` | Purple 15% opacity — borders |
| `--color-brand-glass` | `#1a102999` | Dark purple 60% opacity — glass surfaces |

### Color Opacity Variants (used in Tailwind)

```
brand-text/95   → rgba(240,238,242,0.95)   headings
brand-text/70   → rgba(240,238,242,0.70)   secondary body
brand-text/60   → rgba(240,238,242,0.60)   muted text
brand-text/50   → rgba(240,238,242,0.50)   placeholder text
brand-text/40   → rgba(240,238,242,0.40)   subtle text
brand-text/35   → rgba(240,238,242,0.35)   very subtle
brand-text/30   → rgba(240,238,242,0.30)   almost invisible

brand-orange/80 → rgba(239,108,74,0.80)    badge text
brand-orange/30 → rgba(239,108,74,0.30)    selection highlight
brand-orange/20 → rgba(239,108,74,0.20)    glow base
brand-orange/15 → rgba(239,108,74,0.15)    badge border
brand-orange/8  → rgba(239,108,74,0.08)    badge background

brand-purple/30 → rgba(123,94,167,0.30)    large glow
brand-purple/20 → rgba(123,94,167,0.20)    card border
brand-purple/15 → rgba(123,94,167,0.15)    ambient glow
brand-purple/10 → rgba(123,94,167,0.10)    faint glow

brand-yellow/20 → rgba(245,166,35,0.20)    glow base
brand-yellow/15 → rgba(245,166,35,0.15)    ambient glow
```

### Supplementary Colors (from Tailwind defaults used on site)

```
zinc-200 → oklch(92% .004 286.32)   very light gray
zinc-400 → oklch(70.5% .015 286.067) medium gray
white    → #ffffff
black    → #000000
```

---

## Typography

### Font Family

```
Primary: "Inter", sans-serif
Monospace: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace
```

**Google Fonts import:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap" rel="stylesheet">
```

### Type Scale

| Element | Size (desktop) | Size (mobile) | Weight | Letter Spacing | Line Height |
|---------|---------------|---------------|--------|----------------|-------------|
| H1 | 60px | 34px | 500 | -1.8px (lg) / -1.2px | 1.07 |
| H2 | 38px | 32px | 700 | -0.76px | 1.5 |
| H3 | 32px | 32px | 700 | -0.64px | 1.2 |
| Body | 16px | 16px | 400 | normal | 1.5 |
| Small | 14px | 14px | 400 | normal | 1.25 |
| XS / Badge | 12px | 12px | 600–700 | 0.05em (wider) | — |
| Nav Links | 14px | 14px | 500 | normal | — |
| CTA Button | 13px | 13px | 600 | normal | — |

### Font Weight Reference

```
400 → normal (body)
500 → medium (h1, nav links)
600 → semibold (buttons, badges)
700 → bold (h2, h3)
```

### Text Gradient Patterns

**H1 — top-to-bottom, white fading to orange:**
```css
background: linear-gradient(to bottom, #ffffff 0%, #ffffff 50%, #ef6c4a 100%);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
```

**H2 — left-to-right, text fading to yellow:**
```css
background: linear-gradient(to right, #f0eef2 0%, #f0eef2 55%, #f5a623 100%);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
```

**CTA / Decoration — diagonal orange to yellow:**
```css
background: linear-gradient(to bottom right, #ef6c4a, #f5a623);
```

---

## Component Patterns

### Navigation Bar

```
Position: fixed, top: 1.25rem (desktop: 2rem)
Width: 92% of viewport, max-width: 1120px
Height: 3.5rem (desktop: 4rem)
Background: rgba(26, 16, 41, 0.65) — brand-glass at 65%
Blur: backdrop-filter: blur(24px)
Border: 1px solid rgba(123, 94, 167, 0.15)
Border radius: 1rem (16px)
Padding: 0 1.5rem
```

Nav link active state: `bg-brand-orange` dot indicator below link

### Buttons

**Primary (CTA):**
```
Background: linear-gradient(to right, #ef6c4a, #f5a623)
Border radius: 9999px (pill)
Padding: 0.625rem 1.25rem
Font size: 13px, weight: 600
Color: white
Hover: opacity 0.9
```

**Secondary (Outline):**
```
Border: 1px solid rgba(240, 238, 242, 0.2)
Border radius: 9999px (pill)
Padding: 0.625rem 1.25rem
Font size: 14px, weight: 500
Color: brand-text
Hover: border-color opacity increases to 0.4
```

### Glassmorphic Card

```
Background: rgba(26, 16, 41, 0.60)
Blur: backdrop-filter: blur(10–15px)
Border: 1px solid rgba(123, 94, 167, 0.15–0.20)
Border radius: 1rem–1.5rem (16px–24px)
```

### Tech / Tag Badges

```
Background: rgba(239, 108, 74, 0.08)
Border: 1px solid rgba(239, 108, 74, 0.15)
Color: rgba(239, 108, 74, 0.80)
Border radius: 9999px
Padding: 0.25rem 0.75rem
Font size: 11–12px, weight: 700
Letter spacing: 0.05em (wider)
Text transform: uppercase
```

### Ambient Background Glows

Place absolutely inside `position: relative; overflow: hidden` containers:

```
Orange glow:  400px circle, blur 130px, brand-orange/20, top-left area
Purple glow:  350px circle, blur 120px, brand-purple/15, right side
Yellow glow:  300px circle, blur 140px, brand-yellow/15, bottom
Large purple: 500px circle, blur 150px, brand-purple/10, center-right
```

### Section Layout

```
Max content width: 1120px, centered
Horizontal padding: 1.25rem (mobile) → 1.5rem (desktop)
Section vertical padding: py-12 md:py-20 (48px → 80px)
Hero vertical padding: pt-24 pb-12 lg:pt-32 lg:pb-20
```

### Footer

```
Border top: 1px solid rgba(123, 94, 167, 0.10) — very faint purple
Padding: py-12 md:py-16 (48px → 64px)
```

---

## Spacing Scale (Tailwind base)

```
1 unit = 0.25rem = 4px
Common values used:
  px-5  = 1.25rem = 20px
  px-6  = 1.5rem  = 24px
  py-2.5 = 0.625rem = 10px
  gap-2  = 0.5rem  = 8px
  rounded-2xl = border-radius: 1rem
  rounded-3xl = border-radius: 1.5rem
  rounded-full = border-radius: 9999px
```

---

## Blur / Filter Values

```
blur-[60px]   → card details, small glow
blur-[80px]   → medium glow (md breakpoint)
blur-[120px]  → large ambient glow
blur-[130px]  → orange hero glow
blur-[140px]  → yellow ambient glow
blur-[150px]  → very large purple glow
blur-2xl      → Tailwind preset (40px)
blur-3xl      → Tailwind preset (64px)
backdrop-blur-md    → 12px (card blur)
backdrop-blur-xl    → 24px (nav blur)
backdrop-blur-2xl   → 40px (heavy glass)
backdrop-blur-[10px]
backdrop-blur-[15px]
```

---

## Border Radius Scale

```
rounded-full → pills, dots, avatar
rounded-2xl  → nav, cards (16px)
rounded-3xl  → larger cards (24px)
```

---

## Transition Defaults

```
transition-opacity: opacity 0.15s ease
transition-colors:  color, background-color, border-color 0.15s ease
default easing: cubic-bezier(0.4, 0, 0.2, 1)
```

---

## Responsive Breakpoints (Tailwind defaults)

```
sm:  640px+
md:  768px+
lg:  1024px+
xl:  1280px+
```
