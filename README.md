# Sailor — meetsailor.com

Marketing homepage for Sailor. Static site, no build step, served by GitHub Pages.

## Layout

| Path | What it is |
| --- | --- |
| `index.html` | The homepage ("Your iMessage, organized."). Written for the `dc` runtime — `x-dc` markup plus a `<script>` state class at the bottom. |
| `support.js` | The `dc` runtime. Compiles the markup and renders it with React. |
| `MessageThread.dc.html` | The animated iMessage thread component used in the hero. |
| `vendor/` | React 18.3.1 + ReactDOM UMD builds, vendored so the page makes no third-party script requests. |
| `sailor-mark.png` | Logo mark; also the favicon and OG image. |
| `src/` | Earlier builds kept for reference — the v1 design (`sailor-v1-standalone.html` is fully self-contained and opens straight from disk). |

## Local preview

```
python3 -m http.server 8000
```

Then open http://localhost:8000 — open it over HTTP, not `file://`, since the runtime fetches `MessageThread.dc.html`.

## Editing

Edit `index.html` directly; there is nothing to compile. The `window.__resources` map in `<head>` points the runtime at `vendor/` instead of unpkg — leave it in place unless you intend to reintroduce the CDN dependency.

## Deploy

Pushing to `main` publishes. GitHub Pages serves from the repo root; `CNAME` holds the custom domain and `.nojekyll` stops Jekyll from touching the files.
