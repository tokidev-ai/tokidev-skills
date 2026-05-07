# 🔍 linkedin-dev-auditor

Skill para auditar perfiles de LinkedIn orientados a **desarrolladores de software** — analiza 10 aspectos clave y entrega recomendaciones concretas con ejemplos adaptados a tu stack real.

## ¿Qué hace?

Le enseña a Claude a revisar un perfil de LinkedIn como lo haría un experto en personal branding tech:

- Accede al perfil vía navegador (Claude in Chrome) o te pide las secciones por chat
- Evalúa 10 aspectos con estado ✅ / ⚠️ / ❌
- Da ejemplos de mejora personalizados a tu stack y nivel (junior / senior)
- Cierra con las 3 acciones de mayor impacto ordenadas por prioridad

---

## Requisitos

- **Claude Desktop / Cowork** con el skill instalado
- **Claude in Chrome** (extensión) instalada en Chrome o Edge — para que Claude pueda acceder al perfil automáticamente
  - Si no tenés la extensión, Claude te pedirá las secciones por chat

---

## Instalación

Seguí las instrucciones del [README principal](../README.md).

Una vez instalado, el nombre del skill es `linkedin-dev-auditor`.

---

## Cómo usarlo

### Con Claude in Chrome (recomendado)

Asegurate de tener la extensión instalada, luego escribile a Claude:

```
Audita mi perfil de LinkedIn como developer
```

```
Revisa mi LinkedIn y decime qué mejorar
```

```
Analiza mi perfil de LinkedIn, soy dev fullstack
```

Claude va a:
1. Pedirte el link de tu perfil
2. Enviarte una notificación en la extensión para conectar el navegador (si no está conectado)
3. Abrir tu perfil, hacer scroll y escanearlo completo
4. Entregarte el reporte con puntaje y recomendaciones

### Sin navegador (solo chat)

Si no tenés Claude in Chrome, Claude te va a pedir que pegues tus secciones manualmente y hace el análisis igual.

---

## Los 10 aspectos que analiza

| # | Aspecto | Por qué importa |
|---|---------|-----------------|
| 1 | 📸 Foto de perfil | Sin foto = 14x menos visitas de recruiters |
| 2 | 🖼️ Banner / Portada | Primera impresión visual de tu marca |
| 3 | 📝 Titular (Headline) | Bien hecho = 5x más mensajes, +40% vistas |
| 4 | 💬 About | Historia + stack + logros + CTA |
| 5 | 💼 Experiencia | Impacto cuantificado vs solo tareas |
| 6 | ⭐ Featured | Portafolio, GitHub, proyectos visibles |
| 7 | 🛠️ Skills | Relevantes, ordenadas, con endorsements |
| 8 | 🏅 Certificaciones | AWS, GCP, Meta, Google, etc. |
| 9 | 🔗 URL personalizada | linkedin.com/in/tunombre vs /in/abc-123456 |
| 10 | 📢 Actividad | Publicar = señal de expertise para recruiters |

---

## ¿No usás Claude? Prompt standalone

Si usás ChatGPT, Gemini, Mistral u otro modelo, podés usar el prompt que está al final del `SKILL.md` — copialo y pegalo directamente en cualquier IA con tu información de LinkedIn.

---

## Estructura de archivos

```
linkedin-dev-auditor/
├── SKILL.md     # Instrucciones completas para Claude + prompt standalone
└── README.md    # Este archivo
```

---

Made with ❤️ by [@tokidev.ai](https://instagram.com/tokidev.ai)
