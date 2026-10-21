# Zacapa Floral — Sitio Web Oficial

**"No decoramos espacios; transformamos emociones en recuerdos."**

Sitio web one-page de Zacapa Floral: alta floristería y diseño floral para eventos,
desde Nahuizalco, Sonsonate, El Salvador. El objetivo del sitio es convertir visitas en
cotizaciones por **WhatsApp Business (+503 6292 2118)**.

Contacto: zacapafloral@gmail.com · TikTok/Facebook/Instagram: @zacapafloral

## Características

- 100% estático (HTML + CSS + JS en un solo `index.html`) — sin build, sin dependencias
- Optimizado para celular, tablet y computadora (mobile-first, breakpoints 768px/1100px)
- Imágenes WebP con respaldo JPG (`<picture>`) — 43% más livianas
- Slider interactivo "Antes / Después"
- Galería doble (arreglos florales / espacios transformados) con lightbox
- Configurador "Diseña tu evento" que genera el mensaje de cotización para WhatsApp
- Sección de videos del proceso (placeholders listos para reemplazar)
- SEO local (meta tags, Open Graph, LocalBusiness JSON-LD) y `vercel.json` con caché de imágenes

## Estructura

```
zacapa-floral-web/
├── index.html      → todo el sitio (estilos y scripts incrustados)
├── sitemap.xml     → mapa del sitio para Google Search Console (1 URL + fotos de la galería)
├── robots.txt      → permite el rastreo e indica dónde está el sitemap
├── vercel.json     → caché de imágenes y URLs limpias
└── img/            → logos, fotos de trabajos, salón antes/después, favicons
```

## 🔎 Google Search Console (sitemap)

- **Dominio oficial:** `https://www.zacapafloral.com` (sin `www` redirige al `www`).
  El `sitemap.xml`, el `robots.txt`, el `<link rel="canonical">` y el `og:url`/`og:image`
  de `index.html` usan todos exactamente ese dominio.
- **Enviar el sitemap (una sola vez):** primero publica el sitio (merge a `main` →
  Vercel despliega), comprueba en el navegador que abre
  `https://www.zacapafloral.com/sitemap.xml`, y luego en
  [Google Search Console](https://search.google.com/search-console) ve a
  **Indexación → Sitemaps**, escribe solo `sitemap.xml` y pulsa **Enviar**.
  El estado debe quedar en **Correcto**. No hay que reenviarlo en cada cambio:
  Google lo revisa solo periódicamente (también está anunciado en `robots.txt`).
- **Es un sitio de una sola página**, por eso el sitemap lleva **una única URL**
  (`https://www.zacapafloral.com/`). No agregues las secciones con `#`
  (`/#galeria`, `/#paquetes`…): Google las ignora porque no son páginas separadas.
  Si algún día creas páginas nuevas, agrega cada una como un `<url>` más.
- **Fotos:** dentro de esa URL van listadas las fotos de la galería con la
  extensión de imágenes (`<image:image>`), para ayudar a que aparezcan en
  Google Imágenes (la galería se carga con JavaScript y así Google las descubre
  todas, no solo la primera categoría). Al agregar una foto nueva al arreglo
  `FOTOS` de `index.html`, agrega también su bloque `<image:image>` en
  `sitemap.xml` (copia uno y cambia el nombre del archivo) y actualiza la
  fecha `<lastmod>` a la del día del cambio. No marques fechas futuras ni
  cambies la fecha si el contenido no cambió.

---

## 🚀 Publicar en GitHub + Vercel (sin usar la terminal)

### Paso 1 — Subir a GitHub (desde el navegador)

1. Entra a [github.com](https://github.com) e inicia sesión (o crea tu cuenta gratis).
2. Arriba a la derecha, botón **+** → **New repository**.
3. Nombre: `zacapa-floral-web` · que sea **Public** (o Private, Vercel también lo acepta).
   **No** marques "Add a README" (este proyecto ya trae uno).
4. Clic en **Create repository**.
5. En la página que aparece, clic en el enlace **"uploading an existing file"**.
6. Arrastra TODOS los archivos y la carpeta `img` de este proyecto a esa página
   (o usa "choose your files"). Verifica que entren: `index.html`, `vercel.json`,
   `.gitignore`, `README.md` y la carpeta `img/` con todas las imágenes.
7. Abajo, clic en **Commit changes**. ✅ Tu sitio ya está en GitHub.

### Paso 2 — Publicar con Vercel (2 minutos)

1. Entra a [vercel.com](https://vercel.com) → **Sign Up** → elige **"Continue with GitHub"**.
2. Autoriza el acceso a tu GitHub.
3. En el panel de Vercel: **Add New… → Project**.
4. Aparecerá tu repo `zacapa-floral-web` → clic en **Import**.
5. **No cambies nada** (es un sitio estático, Vercel lo detecta solo) → clic en **Deploy**.
6. En ~30 segundos tendrás tu sitio en línea con una URL tipo:
   `https://zacapa-floral-web.vercel.app` 🎉

### Después del despliegue

- **Actualizar contenido:** edita `index.html` en GitHub (lápiz ✏️ → Commit) y Vercel
  republica automáticamente en segundos. Fotos nuevas: súbelas a `img/` y
  actualiza las etiquetas `<picture>`.
- **Dominio propio** (ej. `www.zacapafloral.com`): cómpralo y en Vercel ve a
  Project → Settings → Domains para conectarlo (gratis el SSL). Luego actualiza
  el `og:image` en `index.html` con la URL real.
- **Redes sociales:** reemplaza los `href="#"` de TikTok, Facebook e Instagram
  (busca el comentario `Reemplazar href="#"` en `index.html`).
- **Videos:** reemplaza las tarjetas "Próximamente" de la sección `#videos` por
  los embeds de TikTok cuando tengas el material.

---

Desarrollado con 💛 para Zacapa Floral · Nahuizalco, Sonsonate, El Salvador · 2026
