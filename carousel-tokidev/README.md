# 🪨 carousel-tokidev

Skill para generar carruseles de Instagram de **@tokidev.ia** — formato 1080×1350px, exportación PNG, sistema de diseño completo incluido.

## ¿Qué hace?

Le enseña a Claude a generar carruseles HTML listos para:
- Abrir en el navegador
- Navegar con flechas o teclado
- Exportar cada slide como PNG con un botón

No necesitás explicarle colores, tipografía ni estructura — todo está en el skill.

---

## Instalación

Seguí las instrucciones del [README principal](../README.md).

---

## Cómo usarlo

Una vez instalado el skill, escribile a Claude en Cowork o Claude Code:

```
Hacé un carrusel sobre [TEMA]
```

```
Nuevo carrusel de 8 slides sobre las mejores herramientas de IA para developers
```

```
Carrusel de 10 slides sobre cómo optimizar tokens en Claude y GPT
```

Claude va a:
1. Preguntarte cuántos slides querés (si no lo especificaste)
2. Leer la plantilla base (`assets/carousel-template.html`)
3. Generar el HTML completo con el contenido
4. Guardarlo en tu carpeta y darte el link para abrirlo

---

## Exportar los PNG

Una vez abierto el HTML en el navegador:

1. Hacé clic en el botón **"⬇ Exportar N slides PNG"** (arriba al centro)
2. Se van a descargar todos los slides como archivos PNG individuales
3. Listos para subir a Instagram

> Los PNG se exportan en resolución exacta **1080×1350px** — sin necesidad de edición.

---

## Sistema de diseño

| Elemento | Valor |
|---|---|
| Formato | 1080 × 1350 px |
| Fondo | `#131139` |
| Acento | Degradado naranja→morado `#FA743F → #A406E9` |
| Tipografía | Segoe UI / system-ui |
| Handle | `@tokidev.ia` |
| Idioma | Español rioplatense |

### Componentes incluidos
- Cards de 2 y 3 columnas
- Pills / tags de colores
- Números grandes (estadísticas)
- Iconos con colores (azul, naranja, verde, morado, teal, rosa)
- Slide de portada con imagen opcional a la derecha con degradado
- Slide CTA final fijo

---

## Estructura de archivos

```
carousel-tokidev/
├── SKILL.md                    # Instrucciones para Claude
├── README.md                   # Este archivo
└── assets/
    └── carousel-template.html  # Plantilla base con estilos y JS
```

---

## Ejemplo de output

Un carrusel sobre "Optimización de tokens en IA" generado con este skill:

- **Slide 01:** Portada con pregunta gancho + imagen lateral con degradado
- **Slides 02–09:** Contenido con cards, stats, before/after, herramientas
- **Slide 10:** CTA final con íconos GUARDA / COMPARTE / COMENTA

---

Made with ❤️ by [@tokidev.ia](https://instagram.com/tokidev.ia)
