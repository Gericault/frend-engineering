# Frend Engineering

The site at **frend.pro** — a two-person practice page that doubles as a CV
for Amy Michel (environmental engineering) and Cale Frend (information systems).

Plain static HTML and CSS. No build step, no framework, no external requests.
What is in this repository is what gets served.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole site — one page, four sections |
| `styles.css` | All styling, including dark mode and print |
| `404.html` | Served by Azure Static Web Apps for unknown paths |
| `staticwebapp.config.json` | 404 handling, security headers, caching |
| `robots.txt`, `sitemap.xml` | Crawler hints |

## Editing

Everything is in `index.html`. The two profile blocks are marked with
`<article class="profile">`; experience items follow the pattern:

```html
<li>
  <span class="when">2025 — present</span>
  <strong>Role title</strong>, Employer
  <span class="where">Location · note</span>
</li>
```

Colours and type live in the `:root` block at the top of `styles.css`.
There is a `prefers-color-scheme: dark` block immediately below it — edit both
if you change the palette.

## Local preview

```bash
python3 -m http.server 8081 --bind 127.0.0.1
# then open http://127.0.0.1:8081
```

## Deploying

Azure Static Web Apps builds nothing — the repository *is* the artifact, so the
workflow points `app_location` at `/` and skips the build entirely. Azure
generates the workflow and deployment token when the repo is connected in the
portal.
