# Handoff: Página de producto galca.app

## Resumen
Landing estática de Galca para el dominio raíz **galca.app**. Presenta el producto (captura de reportes de campo, revisión y análisis), sus módulos, cómo funciona sin señal y el contacto. Botón principal "Acceder" → https://tm2.galca.app/.

## Sobre los archivos
`sitio/index.html` NO es solo referencia: es HTML/CSS/JS plano, sin build ni librerías, y **se puede publicar tal cual**. El repo actual (cesangal15/RASEC) se sirve por GitHub Pages en tm2.galca.app; la landing va en un repo/carpeta aparte servido en la raíz galca.app.

Fidelidad: **alta** (colores, tipografía, textos y animaciones finales). Datos: ninguno real.

## Cómo implementarlo con Claude Code (pasos)
1. Crear repo `galca-web` (o carpeta `web/` en RASEC) y copiar `sitio/*` a la raíz.
2. Añadir `CNAME` con `galca.app`; activar GitHub Pages (rama main, raíz).
3. En Cloudflare DNS: apuntar `galca.app` (A/ALIAS) a GitHub Pages y CNAME `www` → `<usuario>.github.io`. Mantener `tm2` y `api` como están.
4. Exportar la animación del tablero a `tablero.mp4` (≤ 5 MB, H.264, 1280×800, sin audio) y dejarla junto a index.html. Sin el archivo, el cuadro muestra un aviso discreto (ya manejado en JS).
5. Reemplazar `contacto@galca.app` por el correo definitivo.
6. Opcional: descargar Red Hat Display (700/800) y Public Sans (400–700) a `fonts/` y sustituir el <link> de Google Fonts por @font-face, para que la página no dependa de red externa. Ajustar la CSP si se añade una (font-src 'self').
7. Opcional: `robots.txt`, `sitemap.xml`, Open Graph (og:image 1200×630 con el logotipo blanco sobre #0b1f3a).

Prompt sugerido para Claude Code:
> Publica la landing de `design_handoff_galca_web/sitio/` como sitio estático en la raíz de galca.app vía GitHub Pages (repo nuevo galca-web con CNAME). No cambies el diseño ni los textos. Añade robots.txt, meta Open Graph y sirve las fuentes en local con @font-face. Verifica que el botón "Acceder" apunta a https://tm2.galca.app/ y que la página carga sin errores de consola en móvil y escritorio.

## Estructura de la página
1. **Hero** (fondo #0b1f3a): nav (logotipo blanco, enlaces, botón "Acceder · TM2"), eyebrow "Captura · Revisión · Análisis", H1 "Del reporte en campo al dato que decide.", párrafo, botones "Acceder" (blanco) y "Cómo funciona en campo" (contorno). Fondo: red abstracta SVG interactiva con el mouse (nodos se acercan al cursor, opacidad .3 → .5).
2. **Franja TM2** (blanco): "En uso en la obra TM2" · tm2.galca.app.
3. **Qué resuelve** (#que): H2 + 3 celdas numeradas 01–03.
4. **Módulos** (#modulos): H2; **diagrama de flujo** SVG (viewBox 890×380) sobre fondo espacial (degradado #0a0f2e→#160b3a→#2a0b3d, nebulosas violeta/magenta/azul, 260 puntos con filamentos, núcleos con halo pulsante). Nodos: CAMPO (Capataz, Chequeadora, Operador · QR, Asistencia) → GALCA (Captura, Revisión) → SALIDAS (Excel maestro, Tablero, Reporte del día, Nómina). Hover/tap: resalta conexiones, atenúa el resto (.12/.3), acelera los puntos que viajan (3.2 s → 1.4 s) y muestra la nota debajo. Bloque destacado "Tablero de producción" (azul) con video + 3 indicadores; 6 tarjetas de una línea.
5. **En campo** (#campo, blanco): H2 + 4 pasos numerados.
6. **Contacto** (#contacto): H2, correo, caja azul "Ya soy usuario" con "Acceder".
7. **Footer**: logotipo azul, © 2026 Galca · galca.app.

## Tokens
- Azul marca #0b1f3a · texto #1c2230 · secundario #3c4858 · eyebrow #4d5c70 · texto sobre azul #c9d4e3 / #9fb3cc · fondo #f3f6f8 · bordes #d5dae0 · azul hover #1d4d8a.
- Diagrama: entradas #8fb4ff, salidas #ff8fb0, núcleo #fff; espacio #070b18; filamentos #8a7dff / #c96bd9 / #ff7fa0; halos #ffc46b→#ff5c8a.
- Tipografía: Red Hat Display 700/800 (títulos), Public Sans 400–700 (texto). H1 clamp(38px,6vw,76px); H2 clamp(26px,3.2vw,40px); cuerpo 15–16 px.
- Botones: 48 px alto, sin radio; nav 44 px. Sin sombras salvo drop-shadow luminoso en nodos del diagrama.
- Espaciado: padding lateral clamp(20px,5vw,72px); secciones clamp(56px,8vw,104px).
- Animación: @keyframes pulso (4 s), animateMotion en enlaces; respeta prefers-reduced-motion.

## Responsive
Todo con grid auto-fit (minmax 260–300 px) y clamp(); sin breakpoints. Verificado 360–1600 px.

## Archivos
- sitio/index.html · sitio/favicon-32.png · sitio/icon-180.png · sitio/LEEME.md
- marca/ — SVG y PNG de identidad (símbolo, logotipos, iconos PWA, manifest-ejemplo).
- Fuente de diseño en este proyecto: Galca Web A.dc.html; animación del tablero: media/Tablero Video.dc.html (+ tablero-video.jsx).
