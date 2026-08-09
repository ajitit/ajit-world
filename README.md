# ajit.world

Executive personal site — a single dependency-free `index.html`. No build step, no framework, no external fonts or scripts.

## Local preview
Just open `index.html` in a browser. No server needed.

## Deploy
See [DEPLOY.md](DEPLOY.md). Live via Netlify, connected to this repo — pushes to `main` auto-deploy.

## Structure
- `index.html` — the entire site (markup, CSS, JS inline)
- `netlify.toml` — Netlify build/publish config, security headers, `www` → apex redirect
- `DEPLOY.md` — deployment notes and pre-launch checklist
