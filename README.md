# Quedamos — landing

Página de `quedamos.com.mx`. Es un solo HTML estático: no hay que compilar nada.

| Ruta | Qué es |
|---|---|
| `quedamos-landing/` | El sitio (`index.html`, `assets/`, `.nojekyll`). Es lo único que se publica. |
| `.github/workflows/publicar.yml` | En cada push a `main` que toque `quedamos-landing/`, copia la carpeta a la raíz de la rama `gh-pages`. |

## Publicar

Primera vez:

1. `git push -u origin main gh-pages` (las dos ramas en un solo push).
2. En GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, rama
   `gh-pages`, carpeta `/ (root)`.
3. Queda en `https://cgardan1.github.io/9.1-quedamos-landing/`.

Después: editar `quedamos-landing/`, hacer commit y `git push`. El workflow actualiza `gh-pages`
solo; también se puede correr a mano desde **Actions → Publicar landing → Run workflow**.

Ver en local: `python3 -m http.server -d quedamos-landing 8000` y abrir `http://localhost:8000`.

## Dominio propio (`quedamos.com.mx`)

1. Crear `quedamos-landing/CNAME` con una sola línea: `quedamos.com.mx`. Desde ese momento la
   dirección de `github.io` redirige al dominio, así que conviene hacerlo junto con el paso 2.
2. En el DNS del dominio (GoDaddy):
   - Registros `A` de `@` a `185.199.108.153`, `185.199.109.153`, `185.199.110.153` y
     `185.199.111.153`.
   - Registro `CNAME` de `www` a `cgardan1.github.io`.
3. En **Settings → Pages**, escribir el dominio y activar **Enforce HTTPS** cuando aparezca.

La imagen para compartir (`og:image`) y `og:url` ya apuntan a `https://quedamos.com.mx/`; hasta que
el dominio funcione, las vistas previas en redes no mostrarán imagen.
