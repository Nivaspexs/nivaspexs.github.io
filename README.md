# nivaspexs.github.io — Portada y portafolio

Sitio personal de Nico. Está hecho con **HTML y CSS**, sin JavaScript, sin frameworks y sin proceso de build.

La estética toma como referencia la app **n** de Jorge Drexler, en concreto **n2**: papel crema, tipografía serif y pocos elementos. No usa recursos de la app; solo su idea visual.

---

## Estructura

```text
.
├── index.html               ← portada pública
├── portafolio.html          ← portafolio completo, noindex
├── static/
│   ├── css/site.css         ← estilos compartidos y variables de diseño
│   └── favicon.svg
├── quiz2.html               ← quiz antiguo, conservado como archivo
├── Assets/                  ← CSS y JS del quiz antiguo
└── README.md
```

No hay dependencias locales ni `package.json`. La tipografía **Newsreader** se carga desde Google Fonts; si no carga, el sitio usa Georgia o una serif del sistema.

---

## Personalización

### 1. Portada

`index.html` contiene el texto exacto de la portada y una ilustración SVG inline. Para cambiar el mensaje, edita el `<h1 class="cover-title">`; conserva la frase completa si quieres mantener el sentido actual.

La Lycoris usa blanco y rojo solo dentro del SVG:

- `#B23A2F` — rojo de los pétalos y filamentos;
- `#8F241D` — rojo oscuro del centro y del tallo;
- `#FFFDF4` — blanco de bordes, venas y anteras.

El resto de la página usa únicamente la paleta del sitio. No uses el rojo como color de enlaces, botones o acentos generales.

### 2. Metadatos e identidad

En el `<head>` de `index.html`, revisa:

- `<title>`, `description` y `author`;
- la URL de `rel="canonical"` y `og:url`;
- el wordmark `nivaspexs` de la cabecera.

En `portafolio.html`, cambia `[Tu Nombre]`, el correo, GitHub y LinkedIn cuando el portafolio deje de ser una versión de trabajo. Mientras tanto, la página lleva:

```html
<meta name="robots" content="noindex, nofollow">
```


### 3. Proyectos

Cada proyecto es un `<li class="project">` dentro de `.project-list`. Para añadir uno, duplica un bloque y cambia:

- el número (`project-num`);
- la categoría (`project-cat--software`, `project-cat--electronica` o `project-cat--iot`);
- el año;
- el título, la descripción y las tecnologías.

Las tres categorías comparten el mismo color de texto legible; el punto que las precede usa un tono distinto de la paleta. Cuando tengas los enlaces, cambia:

```html
<p class="project-links"><span class="pending">[repo]</span><span class="pending">[demo]</span></p>
```

por:

```html
<p class="project-links"><a href="https://github.com/...">repo ↗</a><a href="https://...">demo ↗</a></p>
```

### 4. Notas

Cada nota es un `<details>` nativo: se abre sin JavaScript. Reemplaza la fecha, el título y el contenido. Si no quieres una sección de notas, elimina el bloque completo `<section class="section" id="notas">` y su enlace en la navegación.

### 5. Diseño

Casi todo el lenguaje visual está en las variables al inicio de `static/css/site.css`:

```css
:root {
  --paper: #f4efda;        /* fondo crema */
  --ink: #2f4858;          /* texto principal */
  --ink-soft: #486971;     /* texto secundario y enlaces */
  --muted: #486971;        /* metadatos legibles */
  --line: #c3ceb9;         /* líneas suaves */
  --line-strong: #94ac9f;  /* líneas y separadores */
  --accent: #486971;       /* enlaces y detalles */
  --accent-deep: #2f4858;  /* hover y énfasis */
  --sage: #6a8b87;         /* decoración */
  --serif: "Newsreader", Georgia, serif;
  --max: 52rem;            /* ancho del portafolio */
}
```

La portada usa las mismas variables y añade los estilos `.cover-*` al final de `site.css`. La ilustración no usa imágenes externas: está dibujada con `<path>`, `<use>` y un `<title>` accesible.

El semicírculo del portafolio sigue siendo el `<svg class="hero-mark">` de `portafolio.html`. Puedes borrarlo o cambiar su tamaño en `.hero-mark`.

### 6. Imágenes (opcional)

El diseño no usa fotos. Si quieres añadir una al portafolio, crea `static/img/` y coloca la imagen donde corresponda:

```html
<img src="static/img/perfil.jpg" alt="Retrato de Nico">
```

Añade una regla sencilla en `site.css` para que no desborde:

```css
img {
  display: block;
  max-width: 100%;
  height: auto;
}
```

---


## Checklist

- [ ] Portafolio: nombre, correo, GitHub y LinkedIn.
- [ ] Los seis proyectos: título, descripción, año, tecnologías y enlaces.
- [ ] Biografía y datos de formación.
- [ ] Tres notas (o eliminar la sección).
- [ ] Fecha de «última edición» en el pie.
- [ ] URL canónica y Open Graph.
- [ ] Revisar en 1440, 390 y 320 px.
- [ ] Confirmar que no hay scroll horizontal.
- [ ] Revisar la impresión de la portada.

---

## Accesibilidad y detalles

- Navegación y notas funcionan sin JavaScript.
- Las notas usan `<details>`/`<summary>` nativos.
- Animaciones desactivadas con `prefers-reduced-motion`.
- Estilos de impresión incluidos.
- Sin cookies, analítica ni peticiones externas salvo la tipografía.

---

## Créditos

- Tipografía: [Newsreader](https://fonts.google.com/specimen/Newsreader), servida por Google Fonts.
- Inspiración visual: la app **n** de Jorge Drexler, especialmente **n2** («Madera de deriva»). El sitio no reutiliza assets de la app.
- Lycoris radiata: ilustración SVG original hecha para este repositorio.
