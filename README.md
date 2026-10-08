# Portafolio de David Galindo

Versión estática lista para publicar en GitHub Pages.

> **Estructura actual (v3, editorial):** el sitio principal es `index.html`, un
> solo archivo con su CSS y JS. Usa las fuentes de `fonts/` (Instrument Serif,
> Inter e IBM Plex Mono), las capturas de `projects/`, los mockups de servicios
> de `mockups/` (WebP con transparencia, 01–09), los retratos en blanco y negro
> de `retratos/` y el patrón damasco de `texturas/`. Paleta: claros, negro
> `#121110`, rojo `#8e1f1a` y verde inglés `#14392d`.
>
> El sitio anterior (bilingüe ES/EN) quedó archivado en `version-anterior/`
> y sigue online en `…/portafolio-david-galindo/version-anterior/`. Las
> secciones de este README sobre idiomas y `DICT` se refieren a esa versión.

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub.
2. Sube **todo el contenido de esta carpeta**, no la carpeta completa como un único archivo.
3. En el repositorio abre **Settings → Pages**.
4. En **Build and deployment**, selecciona **Deploy from a branch**.
5. Elige la rama **main**, la carpeta **/(root)** y guarda.
6. GitHub mostrará el enlace público cuando termine la publicación.

El archivo de entrada es `index.html`. Las capturas están dentro de `projects/`.

## Idiomas (español / inglés)

El sitio es bilingüe en **un solo enlace**. No hay `/en/` ni archivos duplicados:
el mismo `index.html` contiene los dos idiomas y el selector `ES / EN` del header
los intercambia al instante.

Qué idioma ve cada visitante:

1. Si la URL trae `?lang=es` o `?lang=en`, manda ese parámetro.
2. Si no, se usa el idioma que el visitante eligió antes (guardado en el navegador).
3. Si es su primera visita, se detecta el idioma del navegador: español para
   quienes lo tienen configurado, inglés para todos los demás.

Al pulsar el selector la URL pasa a `?lang=…`, así que se puede compartir el
portafolio forzando un idioma:

- Español: `…/portafolio-david-galindo/?lang=es`
- Inglés: `…/portafolio-david-galindo/?lang=en`

### Editar o agregar textos

Los textos viven en el objeto `DICT` del `<script>` al final de `index.html`,
con una entrada por idioma (`es` y `en`). En el HTML cada texto traducible lleva
un atributo que apunta a su clave:

| Atributo | Qué traduce |
| --- | --- |
| `data-i18n` | El texto del elemento |
| `data-i18n-html` | Texto con etiquetas dentro (por ejemplo un `<br>`) |
| `data-i18n-aria` | El `aria-label` |
| `data-i18n-alt` | El `alt` de una imagen |

En las tarjetas de proyecto, `{name}` dentro de un texto se reemplaza por el
valor de `data-project` del `<article>`, para no repetir el nombre 14 veces.

Al agregar una clave hay que añadirla en **ambos** idiomas. Si falta en inglés,
el sitio muestra el texto en español en lugar de dejar el hueco vacío.

El HTML se sirve en español, de modo que si el visitante tiene JavaScript
desactivado igual ve el portafolio completo.

### WhatsApp

Los enlaces con el atributo `data-wa` abren WhatsApp con un mensaje ya escrito
en el idioma activo. El texto está en la clave `wa.text` del `DICT`.

## Vista previa al compartir

`og-image.jpg` (1200×630) es la imagen que muestran WhatsApp, LinkedIn, X, etc.
al pegar el enlace. Los textos de esa vista previa están en las etiquetas
`og:*` del `<head>` de `index.html`.

## Capturas de proyectos

Las capturas en `projects/` deben ser de ~1333×926 px **sin la barra de scroll
del navegador**. Al reemplazar una, conviene mantener esa proporción y
actualizar los atributos `width` y `height` de su `<img>`.

## Servicios

La sección `#servicios` es un catálogo de 8 servicios planteados desde el
problema del cliente (“¿Tu sitio web genera ventas?”), no como lista de tareas.

- **01 Diseño web** es el servicio principal: bloque oscuro destacado y botón
  “Revisemos tu sitio”.
- **02–08** muestran su pieza de `services/` (1000×1000 px, JPG) y alternan
  el lado de la imagen.

Cada servicio (`id="servicio-0N"`) tiene sus textos en las claves `sN.*` del
`DICT`: `cat` (nombre), `need` (la frase del cliente), `title`, `lead`,
`i1…iN` (lo que incluye), `note`, `wa` (mensaje de WhatsApp). “Se combina con”
enlaza a los servicios relacionados para armar el recorrido
problema → servicio → servicios complementarios → conversación.

## Casa Peña (`casa-pena/`)

Sitio de reservas del departamento Casa Peña, publicado en
`…/portafolio-david-galindo/casa-pena/`.

- **`index.html`**: la página, con galería, comodidades, ubicación, calendario y formulario.
- **Configurar el contacto**: al inicio del `<script>`, en `CONFIG`, completa
  `whatsapp` (código de país sin `+`, ej. `5491112345678`) y/o `email`. El
  formulario abre WhatsApp (o el correo) con la solicitud ya escrita.
- **`reservas.json`**: las fechas ocupadas. Cada reserva bloquea desde `entrada`
  hasta el día anterior a `salida`, y el día de salida queda libre para otro
  ingreso. Las reservas que vienen ahora son de ejemplo. Para bloquear fechas,
  edita este archivo en GitHub y el calendario se actualiza solo.
- **Flyers**: `flyer-feed-1080x1350.jpg` (post de Instagram/Facebook),
  `flyer-historia-1080x1920.jpg` (historias/WhatsApp) y `og-casa-pena.jpg`
  (vista previa al compartir el link). Se generan desde `flyer.html`
  (`?solo=feed|story|og`).
- **`fotos/`**: las fotos optimizadas (máx. 1600 px).
