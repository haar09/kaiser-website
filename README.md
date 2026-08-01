# Team 6989 — Kaiser Robotics

The team website: a static HTML/CSS/JS site with no build step.

Live at <https://team6989.com>.

## Local preview

Any static file server works. From the repository root:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Use a server rather than opening
`index.html` directly — some asset paths are root-relative (`/src/...`)
and won't resolve over `file://`.

## Deployment

Deployed to GitHub Pages by `.github/workflows/deploy.yml` on every push to
`main` (or manually via the Actions tab → "Deploy to GitHub Pages" → "Run
workflow"). The repository root is published as-is.

One-time setup in the repository settings:

1. **Settings → Pages → Build and deployment → Source**: select
   **GitHub Actions**.
2. **Settings → Pages → Custom domain**: `team6989.com`, and tick
   **Enforce HTTPS** once the certificate has been issued.
3. At the DNS provider for `team6989.com`, point the apex record at GitHub
   Pages:

   | Type | Name | Value |
   | ---- | ---- | ----- |
   | A | `@` | `185.199.108.153` |
   | A | `@` | `185.199.109.153` |
   | A | `@` | `185.199.110.153` |
   | A | `@` | `185.199.111.153` |
   | CNAME | `www` | `haar09.github.io` |

The `CNAME` file in the repository root keeps the custom domain configured
across deployments; the empty `.nojekyll` file tells Pages to serve the
files verbatim instead of running them through Jekyll.
