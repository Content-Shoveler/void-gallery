# Void Gallery

Rowan Findlay's 3D portfolio — live at **https://rowanfindlay.com**.

A PlayCanvas self-host export of the `Void` scene (PlayCanvas project "Void Gallery", scene 1096854), served as a plain static site. No build step.

## Run locally

The engine loads its files over HTTP, so opening `index.html` from disk won't work:

```sh
python3 -m http.server 8787
# → http://127.0.0.1:8787
```

## Layout

| Path | What |
|---|---|
| `index.html` | Entry page |
| `__game-scripts.js` | All game scripts, concatenated: first-person movement, UI (Vue 2), station/lost triggers |
| `1096854.json` | The scene |
| `config.json` | Asset manifest |
| `files/assets/` | Textures, fonts, skybox, Ammo physics, UI HTML/CSS |
| `vendor/` | Pinned jQuery 3.5.1 + Vue 2.7.16 (were CDN-loaded) |

Project content (titles, links, contact details) lives in the `loadUI` script inside `__game-scripts.js`.

## Deploy

Render static site `void-gallery` (Content-Shoveler workspace), auto-deploys on push to `main`, publish path `.`.
DNS: `rowanfindlay.com` + `www` CNAME → `void-gallery-f6vt.onrender.com` in Cloudflare, DNS-only. Mail (Google MX/TXT) untouched.

## Re-exporting from PlayCanvas

Editor → Publish / Download → Download .zip, scene `Void`. Unzip over the repo root, then re-apply `index.html` (vendor scripts, title) and the project URL fixes in `__game-scripts.js` — check `git diff`.
