# Greater — product page

Public landing page and download host for **Greater**, the Windows disk usage
analyzer.

- Live page: <https://aimesavoir.github.io/Greater-Site/>
- Arabic: <https://aimesavoir.github.io/Greater-Site/?lang=ar>
- Installer: [latest release](https://github.com/aimesavoir/Greater-Site/releases/latest)

The application source lives in a separate private repository. This repository
only holds the static page (`index.html`, `styles.css`, `main.js`, `img/`) and
the published installer as a release asset.

## Structure

| Path | Purpose |
|---|---|
| `index.html` | Page markup. English is inline; elements carry `data-t="key"` attributes. |
| `styles.css` | Styles. Palette mirrors the app theme (`--bg: #0b0d10`, `--accent: #4f8cff`). Includes RTL rules. |
| `main.js` | Arabic dictionary, language toggle, `?lang=` parameter, `localStorage` persistence. |
| `img/` | Real screenshots of the running app (1800 px JPEG) and the app icon. |
| `.nojekyll` | Serve files as-is, no Jekyll processing. |

## Editing

Text changes go in `index.html` (English) **and** in the `AR` dictionary in
`main.js` (Arabic). Keys must match on both sides; `main.js` snapshots the
English markup at load so switching back is lossless.

Serve locally with any static server, for example:

```powershell
npx serve .    # or: python -m http.server
```

No build step, no dependencies, no external requests.

## Publishing

Push to `main`. GitHub Pages serves the repository root; a release tagged
`v1.0.0` carries `Greater_1.0.0_x64-setup.exe`, which the download buttons link
to through `releases/latest/download/`.
