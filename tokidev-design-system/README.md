# 🎨 tokidev-design-system

Skill para aplicar el estilo visual de Tokidev en cualquier proyecto web: fondo dark navy, acentos naranja/amarillo, tipografía Inter y componentes con glassmorphism.

## ¿En qué consiste?

Esta skill encapsula el sistema de diseño de Tokidev (basado en `tokidev-landing.vercel.app`) para que no tengas que definir colores, tipografías ni patrones visuales cada vez.

Incluye:
- Tokens de color listos para usar
- Reglas tipográficas (H1/H2 con gradientes, jerarquía de textos)
- Patrones de UI (navbar glass, CTA principal, cards, badges, glows)
- Recetas tanto para **CSS vanilla** como para **Tailwind**

---

## ¿Qué hace cuando la usás?

Cuando activás esta skill, el agente:
1. Reconoce que querés estilo Tokidev
2. Aplica los tokens y componentes correctos
3. Genera/edita HTML y CSS (o Tailwind) respetando la estética
4. Mantiene consistencia visual sin sobrecargar el diseño

---

## Instalación

Seguí las instrucciones del [README principal](../README.md).

Una vez instalada, el nombre de la skill es `tokidev-design-system`.

---

## Cómo usar la skill

Podés invocarla con prompts como:

```text
Aplicá el estilo tokidev a mi landing page
```

```text
Creá un hero dark con gradiente blanco→naranja y CTA naranja→amarillo
```

```text
Refactorizá este componente para que use tokidev design system en Tailwind
```

```text
Hacé una navbar glassmorphism estilo tokidev con fondo blur y borde púrpura suave
```

---

## Cuándo conviene usarla

Usala cuando quieras:
- Una landing premium en modo oscuro
- Consistencia visual entre secciones/componentes
- Replicar la estética Tokidev en un proyecto existente
- Evitar decisiones de diseño manuales en cada pantalla

---

## Tokens base (resumen rápido)

- Fondo principal: `#0a111a`
- Texto principal: `#f0eef2`
- Acento naranja: `#ef6c4a`
- Acento amarillo: `#f5a623`
- Acento púrpura: `#7b5ea7`

> Referencia completa de tokens, escalas y patrones en `references/DESIGN.md`.

---

## Estructura de archivos

```text
tokidev-design-system/
├── SKILL.md
├── README.md
└── references/
    └── DESIGN.md
```

---

Made with ❤️ by [@tokidev.ai](https://instagram.com/tokidev.ai)
