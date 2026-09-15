# galca.app · landing estática

Página de producto de Galca para la raíz del dominio **galca.app**. HTML, CSS y JS
planos en un solo archivo, sin build ni librerías. Origen: handoff
`Identidad_visual_Galca.zip` (design_handoff_galca_web/sitio), sin cambios de
diseño ni de textos.

## Archivos

| Archivo | Uso |
|---|---|
| `index.html` | Página completa. |
| `fonts/*.woff2` | Red Hat Display y Public Sans (variables, latin + latin-ext), servidas en local con `@font-face`. No depende de Google Fonts. |
| `favicon-32.png`, `icon-180.png` | Favicon y icono iOS (mismos PNG que `../icons/`). |
| `og-image.png` | Imagen Open Graph 1200×630 (logotipo blanco sobre #0b1f3a). |
| `robots.txt`, `sitemap.xml` | SEO básico. |
| `CNAME` | `galca.app`, para cuando esta carpeta se sirva como sitio propio. |

## Cómo publicar

Este repo se sirve por GitHub Pages en **tm2.galca.app**, por lo que esta carpeta
solo queda accesible como `tm2.galca.app/web/`. Para publicarla en la raíz de
galca.app hay que servirla como sitio aparte:

1. Crear el repo `galca-web` y copiar el contenido de esta carpeta a su raíz
   (incluido `CNAME`).
2. Activar GitHub Pages (rama `main`, carpeta raíz).
3. En Cloudflare DNS: `galca.app` (A/ALIAS) a GitHub Pages y `www` como CNAME a
   `<usuario>.github.io`. Mantener `tm2` y `api` como están.

## Pendientes

- `tablero.mp4`: exportar la animación del tablero (≤ 5 MB, H.264, 1280×800, sin
  audio) y dejarla junto a `index.html`. Sin el archivo, el cuadro muestra un
  aviso discreto (ya manejado en JS) y la consola registra un 404, esperado.
- `contacto@galca.app` es provisional. Buscar y reemplazar en `index.html`.

## Verificado

Con Chromium headless a 360 px y 1440 px: sin errores de consola (salvo el 404
del video), sin scroll horizontal, fuentes locales cargadas y los tres botones
«Acceder» apuntando a https://tm2.galca.app/.
