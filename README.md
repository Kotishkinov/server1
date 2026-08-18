# Acilav — SEO Agency Website

Static website (HTML export from Webflow). No build step and no dependencies —
the files are served exactly as they are.

## Structure

| Path | Purpose |
| --- | --- |
| `index.html` | Home page |
| `insights/*.html` | 10 blog / insight articles |
| `template-pages/*.html` | Changelog, license, style guide |
| `404.html`, `401.html` | Error and password-protected pages |

## Local preview

Internal links are extensionless (`/insights/seo-trends-that-matter`), so the
preview server must resolve `/foo` to `foo.html` — the same way GitHub Pages,
Netlify and Vercel do.

```bash
python -m http.server 8000
```

Note: Python's built-in server does **not** do extensionless resolution, so
article links will 404 locally even though they work once deployed.

## Deployment

Deploy the repository root as-is.

- **GitHub Pages** — Settings → Pages → deploy from `main` / root.
- **Netlify / Vercel** — no build command, publish directory `.`

`.nojekyll` is required so GitHub Pages serves the files verbatim instead of
processing them with Jekyll.

## Assets

CSS, JavaScript, fonts and images are loaded from Webflow's CDN
(`cdn.prod.website-files.com`). The site therefore requires an internet
connection and stays dependent on that CDN remaining available.

## Environment variables

None. This is a fully static site with no backend and no API keys.
