# Portafolio de David Galindo

Versión estática lista para publicar en GitHub Pages.

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
