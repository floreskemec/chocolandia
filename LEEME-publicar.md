# Cómo publicar Chocolandia (gratis, web + celular)

Esta carpeta ya es el sitio completo. Pesa ~170 KB y no necesita servidor ni base de datos.

```
index.html              el juego (página completa, con PWA activada)
manifest.webmanifest    hace que se pueda instalar como app en el celular
sw.js                   service worker: guarda el juego para jugar sin internet
icons/                  íconos de la app (192, 512, maskable, apple-touch)
404.html  .nojekyll      detalles para GitHub Pages
```

## Opción A — GitHub Pages (recomendada, link para siempre)

1. Entrá a github.com → **New repository** → nombre `chocolandia` → **Public** → Create.
2. En el repo vacío: **uploading an existing file** → arrastrá **todo el contenido de esta carpeta**
   (index.html, manifest.webmanifest, sw.js, la carpeta icons, 404.html). → Commit.
   - El archivo `.nojekyll` no se ve en el Finder: activá "mostrar archivos ocultos"
     (Cmd + Shift + punto) antes de arrastrar, o creálo desde GitHub con **Add file → Create new file**
     poniendo `.nojekyll` como nombre y dejándolo vacío.
3. **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main` / `(root)` → Save.
4. En un minuto queda en `https://TUUSUARIO.github.io/chocolandia/`.

Desde la terminal del Mac, si preferís:

```bash
cd ~/Chocolandia/web        # carpeta con estos archivos
git init && git add -A && git commit -m "Chocolandia web"
git branch -M main
git remote add origin https://github.com/TUUSUARIO/chocolandia.git
git push -u origin main
```

## Opción B — Netlify Drop (sin cuenta de GitHub, 30 segundos)

Entrá a `app.netlify.com/drop` y arrastrá la carpeta entera. Te da un link al toque.
Creando una cuenta gratis el link queda permanente y podés renombrarlo
(ej. `chocolandia.netlify.app`). Cloudflare Pages funciona igual de bien.

## En el celular (sin App Store ni Play Store)

Abrí el link y:

- **Android/Chrome**: aparece "Instalar app" o menú ⋮ → *Agregar a pantalla principal*.
- **iPhone/Safari**: botón Compartir → *Agregar a inicio*.

Queda con ícono propio, abre a pantalla completa (sin barra del navegador) y funciona
sin internet después de la primera vez.

## Al publicar una versión nueva del juego

1. Reemplazá `index.html` por el nuevo.
2. Subí el número de caché en `sw.js`: `const CACHE = 'chocolandia-v2';`
   (si no lo hacés, los que ya lo instalaron siguen viendo la versión vieja).
3. Volvé a subir los archivos.
