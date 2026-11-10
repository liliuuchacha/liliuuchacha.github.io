# Sitio de Lía Bianchi

Un portfolio simple para GitHub Pages: las series de obras en un menú
lateral, las fotos en mosaico y a pantalla completa al hacer clic. GitHub lo publica
gratis y no hace falta instalar nada.

## Qué archivo cambia qué

| Archivo | Qué controla |
|---------|--------------|
| `_config.yml` | Nombre, subtítulo, texto de inicio, links del menú, dirección del sitio |
| `sobre-mi.md` | La página "sobre mí": bio y muestras |
| `_albums/*.md` | Un archivo por serie de obras (ej. Pinturas): nombre, orden, carpeta, ficha de cada obra |
| `photos/<serie>/` | Las fotos de cada serie |
| `assets/css/style.css` | Colores, cantidad de columnas, tamaño y espacio de las fotos (arriba de todo) |

Todo lo que está pensado para cambiar está marcado con `CAMBIAR`. La carpeta
`_layouts/` tiene las plantillas; no hace falta tocarla.

## Publicarlo (la primera vez)

1. Entrá a github.com con tu cuenta (si no tenés, creá una; es gratis).
2. Creá un repositorio nuevo (`+` > **New repository**):
   - El nombre tiene que ser exactamente `TU-USUARIO.github.io`, con tu
     usuario de GitHub en minúsculas. Así el sitio queda en
     `https://TU-USUARIO.github.io`.
   - Elegí **Public** (con cuenta gratis, Pages solo funciona en repos públicos).
   - No marques "Add a README". Hacé clic en **Create repository**.
3. En la página del repo vacío, hacé clic en **uploading an existing file**.
   Arrastrá *todo lo que hay adentro* de esta carpeta (no la carpeta en sí) y
   hacé clic en **Commit changes**.
   - Fijate que `_config.yml` quede en el primer nivel del repo, no adentro de
     otra carpeta.
4. Andá a **Settings** > **Pages**. En "Build and deployment" elegí
   **Deploy from a branch**, rama **main**, carpeta **/ (root)**. Guardá.
5. Esperá uno o dos minutos y abrí `https://TU-USUARIO.github.io`. En la
   pestaña **Actions** se ve si se está publicando o si hubo algún error.

## Personalizarlo

Todo se puede editar desde github.com: abrís el archivo, tocás el lápiz,
cambiás y hacés **Commit changes**. El sitio se actualiza en un minuto.

1. **`_config.yml`**: poné tu usuario en `url`, tu Instagram y tu email en
   `links`. Si querés, cambiá `tagline` e `intro`.
2. **`sobre-mi.md`**: escribí tu bio y tus muestras. Hay un ejemplo para
   reemplazar.
3. **Subir pinturas**: las fotos que vienen son de relleno
   (`placeholder-01.jpg`, etc.). Borralas y subí las tuyas a
   `photos/pinturas/` (**Add file** > **Upload files**).
   - Se ordenan por nombre de archivo. Numeralas (`01-retrato.jpg`,
     `02-paisaje.jpg`) para elegir el orden.
   - La ficha de cada obra va en `captions` dentro de
     `_albums/pinturas.md`, con el nombre exacto del archivo:
     ```yaml
     captions:
       01-retrato.jpg: "Retrato. Óleo sobre tela, 50 × 70 cm, 2025."
     ```
4. **Nueva serie de obras** (dibujos, grabados, cerámica, lo que sea):
   1. Creá una carpeta, por ejemplo `photos/acuarelas/`, y subí las
      fotos. Usá minúsculas y guiones, sin espacios ni tildes.
   2. Creá `_albums/acuarelas.md` (**Add file** > **Create new file**):
      ```yaml
      ---
      title: Acuarelas
      order: 3
      folder: /photos/acuarelas
      ---
      Un texto corto sobre la serie (opcional).
      ```
      `order` es la posición en el menú (1 = arriba de todo).
      `folder` tiene que coincidir exacto con la carpeta.
5. **Sacar una serie**: borrá su archivo en `_albums/` y su carpeta en `photos/`.
6. **Colores y grilla**: arriba de `assets/css/style.css` están los colores,
   `--photo-columns` (columnas en pantalla grande), `--photo-width` y
   `--photo-gap`. Para un sitio oscuro: `--background: #000000;` y
   `--text: #ffffff;`.

## Fotos livianas

La grilla muestra las fotos tal cual, así que las originales de cámara hacen
que el sitio cargue lento. Antes de subirlas, achicalas a unos 2000 píxeles
del lado más largo, calidad JPG 80 (más o menos 300 a 600 KB cada una). En
Mac, sobre copias de las fotos:

```bash
sips -Z 2000 -s formatOptions 80 *.jpg
```

El sitio entero tiene que pesar menos de 1 GB, y cada archivo menos de 100 MB.

## Verlo en tu compu antes de publicar (opcional)

Necesita Ruby 3 o más nuevo. Desde esta carpeta:

```bash
bundle install
bundle exec jekyll serve
```

Y abrí http://localhost:4000.
