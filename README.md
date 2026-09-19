# Cartero

Una web minimalista con estética de carta manuscrita. Quien visita el enlace rellena un formulario (nombre, email, carta libre, redes opcionales) y la "carta" llega directamente a tu Gmail. El `Reply-To` se pone al email del visitante, así puedes contestar desde tu Gmail con un click en "Responder".

**Bilingüe**: detecta el idioma del navegador y permite cambiar entre Español e Inglés con un toggle arriba a la derecha.

Diseñada para poner el enlace en la descripción de apps de ligue (Tinder, Bumble, Hinge, Badoo…) y que el primer contacto sea algo más pausado que un "hola".

## URL pública

Tras desplegar: **`https://romentoss.github.io/Cartero/`**

---

## Despliegue (solo una vez)

El repo ya existe y los archivos del proyecto están subidos. Solo falta activar GitHub Pages:

1. Ve a **`https://github.com/romentoss/Cartero/settings/pages`**.
2. En **Source**, elige **`Deploy from a branch`**.
3. En **Branch**, selecciona **`main`** y **`/ (root)`** → pulsa **Save**.
4. Espera 1–2 minutos. GitHub te mostrará arriba un banner verde con la URL publicada: `https://romentoss.github.io/Cartero/`.

### Activar FormSubmit (una sola vez)

FormSubmit es el servicio gratuito que envía los emails del formulario a tu Gmail. La primera vez que alguien (tú mismo) rellene el formulario, FormSubmit te enviará un email a `romenpadpol@gmail.com` pidiéndote que confirmes el enlace. **Confírmalo desde ese email**. A partir de ahí, cada carta llega como un email normal a tu bandeja.

---

## Cómo pegar el enlace en las apps de ligue

Copia `https://romentoss.github.io/Cartero/` y pégalo en el campo de "bio" / "sobre mí" / "descripción" de cada app. En algunas apps (Hinge, Bumble) sale como link clickable directamente.

---

## Cómo cambiar el email de destino

Si algún día quieres que las cartas lleguen a otro Gmail, edita **una sola línea** del `index.html`:

```html
<form ... action="https://formsubmit.co/TU_NUEVO_EMAIL@gmail.com" ...>
<form ... action="https://formsubmit.co/TU_NUEVO_EMAIL@gmail.com" ...>
```

Y en la URL de retorno:

```html
... value="https://romentoss.github.io/Cartero/?enviado=1" ...
```

Si cambias el email, **vuelve a confirmar FormSubmit** abriendo la web y enviando una carta de prueba.

---

## Cómo cambiar el aspecto / texto

Edita `index.html` directamente desde GitHub (botón ✏️ en la vista del archivo). Todo está en un solo archivo:

- **Colores**: cambia `#f5efe0` (fondo), `#3a2e1f` (tinta), `#8b2c1f` (lacre) en el bloque `<style>`.
- **Textos en español**: el titular "Escríbeme una carta" y la carta de confirmación están en el `<body>`. Búscalos con Ctrl+F.
- **Textos en inglés**: están en el objeto `TEXTOS.en` dentro del `<script>` al final del archivo.
- **Idiomas**: la web detecta automáticamente el idioma del navegador. Si quieres forzar uno u otro, cambia `var IDIOMA_POR_DEFECTO = 'es';` en el script.
- **Fuentes**: se cargan de Google Fonts (`Caveat` manuscrita + `Playfair Display` serif). Si quieres cambiarlas, edita el `<link>` en el `<head>` y las referencias en el CSS.

Tras cualquier cambio, GitHub Pages se actualiza solo en ~30 segundos.

---

## Protecciones anti-abuso incluidas

- **Captcha de FormSubmit** (servicio externo, integrado).
- **Doble honeypot** invisible para descartar bots.
- **Trampa de tiempo**: si el formulario se envía en menos de 5 s desde cargar, se bloquea.
- **Rate-limit local** (60 s entre envíos desde el mismo navegador).
- **Cabecera anti-iframe** (`frame-ancestors 'none'`): nadie puede embeber tu web para capturar cartas ajenas.
- **Validación de email** y longitudes mínimas para evitar mensajes vacíos.
- **Disabling de doble submit** del botón.

> ⚠️ Nota: las protecciones son razonables para un uso personal, pero no son infalibles. Si notas abuso, crea un **filtro en Gmail** para la palabra `Nueva carta de` y mueve esos emails a la papelera automáticamente.

---

## Privacidad

- No hay base de datos: los datos se envían directamente desde el navegador del visitante a FormSubmit y de ahí a tu Gmail. Nada se queda en un servidor intermedio.
- Si alguien te pide borrar su carta, bórrala manualmente de tu Gmail.

---

## Stack técnico

| Capa | Tecnología |
|---|---|
| Frontend | HTML + CSS + JS vanilla en un solo archivo |
| Email | [FormSubmit.co](https://formsubmit.co) (gratis) |
| Hosting | GitHub Pages (gratis) |
| Fuentes | Google Fonts |

Sin backend, sin build step, sin dependencias. Puedes editar todo desde la web de GitHub si no quieres tocar git en local.

---

## Estructura

```
Cartero/
├── index.html    ← la web entera
├── README.md     ← este archivo
└── .nojekyll     ← archivo vacío que evita Jekyll en GitHub Pages
```
