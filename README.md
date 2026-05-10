# 🎨 tokidev-skills

Skills de Cowork / Claude Code para el contenido de **@tokidev.ai** — carruseles de Instagram, infografías para LinkedIn, diseño web y más.

## Skills disponibles

| Skill | Descripción |
|---|---|
| [`carousel-tokidev`](./carousel-tokidev/) | Genera carruseles de Instagram 1080×1350px listos para exportar como PNG |
| [`infografia-tokidev`](./infografia-tokidev/) | Genera infografías para LinkedIn 1080×1440px listos para exportar como PNG |
| [`linkedin-dev-auditor`](./linkedin-dev-auditor/) | Audita perfiles de LinkedIn para developers — 10 aspectos, puntaje y recomendaciones concretas |
| [`tokidev-design-system`](./tokidev-design-system/) | Aplica el estilo visual de Tokidev (dark navy, gradientes cálidos, glassmorphism) en cualquier proyecto web |

---

## ¿Qué es un skill?

Un skill es un conjunto de instrucciones que le enseña a Claude cómo generar un tipo de contenido específico. Incluye el sistema de diseño, la plantilla HTML, las reglas de layout y los componentes — así Claude sabe exactamente cómo crear cada pieza sin que tengas que explicarle nada.

## Instalación

### Opción A — Claude Code CLI

```bash
npx skills add tokidev-ai/tokidev-skills
```

### Opción B — Manual (Cowork / Claude Desktop)

1. Cloná o descargá este repo
2. Copiá la carpeta del skill que querés (ej. `carousel-tokidev/`) a tu carpeta de skills de Claude:
   - **Windows:** `%APPDATA%\Claude\skills\`
   - **Mac:** `~/Library/Application Support/Claude/skills/`
3. Reiniciá Claude Desktop o Cowork

---

## Uso

### Carrusel de Instagram

Una vez instalado, simplemente describile a Claude lo que querés:

```
Hacé un carrusel de 8 slides sobre los mejores frameworks de JavaScript
```

```
Nuevo carrusel sobre cómo usar la API de Claude
```

```
Carrusel de 10 slides sobre productividad para developers
```

Claude va a leer el skill automáticamente y generar el HTML listo para abrir en el navegador y exportar como PNG.

### Infografía para LinkedIn

```
Hacé una infografía sobre cómo funcionan los tokens en los LLMs
```

```
Nueva infografía sobre los mejores modelos de IA en 2025
```

```
Infografía sobre cómo optimizar prompts para GPT y Claude
```

Claude genera el HTML listo para abrir en el navegador y exportar como PNG en formato retrato LinkedIn (1080×1440px).

### Diseño web estilo Tokidev

```
Aplicá el estilo tokidev a mi landing page
```

```
Refactorizá este componente para que use tokidev design system en Tailwind
```

Claude aplica automáticamente los tokens, gradientes y patrones visuales del sistema de diseño Tokidev.

---

## Contribuir

¿Querés agregar un skill nuevo? Abrí un PR con la carpeta del skill siguiendo la estructura de `carousel-tokidev/` como referencia.

---

Made with ❤️ by [@tokidev.ai](https://instagram.com/tokidev.ai)
