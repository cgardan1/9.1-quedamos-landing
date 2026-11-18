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

Si en la página aparece este README en lugar de la landing, Pages está publicando desde `main`:
cámbialo a `gh-pages`.

## Dominio propio (`quedamos.com.mx`)

- El dominio vive en `quedamos-landing/CNAME`, para que el workflow lo copie a `gh-pages`. No va en la
  raíz de `main`: si GitHub crea ahí un `CNAME` al editar el dominio en Settings, hay que moverlo a
  `quedamos-landing/`.
- DNS en GoDaddy: registros `A` de `@` a `185.199.108.153`, `185.199.109.153`, `185.199.110.153` y
  `185.199.111.153`; `www` como `CNAME` (recomendado: a `cgardan1.github.io`).
- En **Settings → Pages**, activar **Enforce HTTPS**.
