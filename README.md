# Web de Va De Dades!

Concurs Valencià d'Estadística per a la Ciència de Dades. Esta es la web del concurso hecha con [Quarto](https://quarto.org) y pensada para publicarse gratis en GitHub Pages.

## Estructura

```
WEBGITHUB/
├── _quarto.yml          ← configuración general (casi nunca hay que tocarla)
├── index.qmd            ← PORTADA en castellano
├── bases.qmd  ayudas.qmd  premios.qmd  blog.qmd  acerca-de.qmd
├── ca/                  ← las mismas páginas en valenciano
│   ├── index.qmd        ← PORTADA en valenciano
│   └── bases.qmd  ajudes.qmd  premis.qmd  blog.qmd  acerca-de.qmd
├── _partials/
│   ├── cabecera.html    ← menú superior (los dos idiomas)
│   └── pie.html         ← pie de página (logos y correo)
├── estilos/
│   ├── vadedades.scss   ← colores, tipografías y diseño
│   ├── fuentes.css      ← tipografía Plus Jakarta Sans
│   └── fuentes/
├── img/                 ← imágenes (en formato .webp, ligero)
│   └── iconos/          ← iconos de las tarjetas (bases, inscripción, ayudas, premios)
├── _site/               ← web ya generada (no se edita a mano; se regenera sola)
└── .github/workflows/publicar.yml  ← publicación automática en GitHub Pages
```

## Editar el contenido

Cada página es un archivo `.qmd`: texto en Markdown con bloques de color.

- **Franjas de color**: cada bloque `:::: {.seccion .naranja}` … `::::` es una franja a todo el ancho.
  Colores: `crema`, `naranja`, `morado`, `amarillo`, `blanco`. Extras: `.ola` (onda arriba) y `.pico` (pico abajo).
- **Botón**: `[Texto del botón](enlace){.boton}`
- **Imagen**: `![](img/archivo.webp){fig-alt="Descripción para lectores de pantalla"}`
- **Correo**: `[vadedades@umh.es](mailto:vadedades@umh.es)`

Si cambias algo en castellano, **cámbialo también en la versión en valenciano** (carpeta `ca/`).

### Cambios habituales cada curso

| Qué | Dónde |
|---|---|
| Calendario | Sustituir `img/calendario-es.webp` y `img/calendario-ca.webp` (mismo nombre) y actualizar el texto `fig-alt` con las fechas |
| Enlace al formulario de inscripción | `index.qmd`, `ca/index.qmd` y `_partials/cabecera.html` |
| Bases (PDF en Drive) | Tarjeta "bases" en `index.qmd` y `ca/index.qmd` |
| Folleto | Imagen `img/folleto-es.webp` / `folleto-ca.webp` y el enlace "Descarga el folleto" |

Para convertir una imagen PNG o JPG a WebP: <https://squoosh.app> (gratuito y en el navegador).

## Ver la web en tu ordenador

1. Instala Quarto: <https://quarto.org/docs/get-started/>
2. Abre un Terminal en la carpeta `WEBGITHUB` y escribe:

   ```
   quarto preview
   ```

   Se abre la web en el navegador y se actualiza sola cada vez que guardas un archivo.

**Con RStudio**: *File → New Project → Existing Directory* → elegir `WEBGITHUB`.
Después, en la pestaña **Build**, pulsa *Render Website* (toda la web) o abre un `.qmd` y pulsa *Render* (solo esa página).

## Publicar en GitHub Pages (una sola vez)

1. Crea un repositorio **público** en GitHub, por ejemplo `vadedades`.
2. Sube el contenido de esta carpeta con **GitHub Desktop**:
   *File → Add local repository* → elegir `WEBGITHUB` → (si lo pide, *create a repository*) → *Commit to main* → *Publish repository*
   (desmarca *Keep this code private*).
3. En GitHub, dentro del repositorio: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. Ve a la pestaña **Actions**: verás "Publicar web". Si no se ha lanzado sola, entra y pulsa *Run workflow*.
   Tarda uno o dos minutos; cuando aparezca el círculo verde, la web está en
   `https://TU-USUARIO.github.io/vadedades/`.

A partir de ahí, **cada vez que subas cambios (Commit + Push en GitHub Desktop), la web se actualiza sola.**
No hace falta subir la carpeta `_site/`: GitHub genera la web por su cuenta.

### Mantener la dirección vadedades.umh.es (opcional)

Hay que pedir al Servicio de Informática de la UMH que cree un registro DNS `CNAME`
de `vadedades.umh.es` hacia `TU-USUARIO.github.io`. Después:
crea en esta carpeta un archivo llamado `CNAME` (sin extensión) con una sola línea: `vadedades.umh.es`,
súbelo, y en *Settings → Pages* escribe `vadedades.umh.es` en *Custom domain* y marca *Enforce HTTPS*.

## Pendiente

- [x] Portada (castellano y valenciano)
- [x] Bases
- [ ] Ayudas / Ajudes
- [x] Premios / Premis (ediciones 2023 a 2026)
- [ ] Noticias / Notícies (17 entradas del blog, con galerías y vídeos)
- [ ] Quiénes somos / Qui som
