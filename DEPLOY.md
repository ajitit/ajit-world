# Deploying ajit.world

The site is a single dependency-free `index.html` — no build step, no framework, no external fonts or scripts. It works on any static host. This repo is already wired for Netlify.

## Current setup — Netlify (git-connected)
1. Repo: https://github.com/ajitit/ajit-world (this repo)
2. Netlify: **Add new site → Import an existing project → Deploy with GitHub** → select `ajit-world`
   - Build command: *(blank)*
   - Publish directory: `.`
   - (`netlify.toml` in this repo pins these automatically, plus security headers and a `www` → apex redirect)
3. Domain: **Site configuration → Domain management → Add a domain** → `ajit.world` → follow Netlify's DNS instructions
4. At the registrar (GoDaddy), set the DNS records Netlify gives you:
   - `A` record `@` → Netlify's load-balancer IP (Netlify's UI shows the current value)
   - `CNAME` record `www` → `<your-site>.netlify.app`
5. Netlify auto-provisions free HTTPS (Let's Encrypt) once DNS resolves. Pushes to `main` auto-deploy.

## Alternative hosts (if ever migrating off Netlify)
- **GitHub Pages**: add a `CNAME` file containing `ajit.world`, enable Pages on this repo, point GoDaddy `A`/`CNAME` records at GitHub.
- **Cloudflare Pages**: `Workers & Pages → Create → Pages → Connect to Git` → same repo, publish dir `.`.
- **Vercel**: `npx vercel` from this folder, or import the repo at vercel.com.

## Before going live — checklist
1. ✅ `og:url` meta tag set to `https://ajit.world/`.
2. Add a professional headshot if desired (hero section currently has none by design).
3. Fill the two `[METRIC NEEDED]` / `[INFORMATION REQUIRED]` markers in `index.html` when you have the numbers — they are honest placeholders, not errors.

## Notes
- Deep Space dark theme is permanent (brand system), not OS-preference-dependent.
- Fully responsive to 375px; keyboard-accessible (native `<details>` expanders, visible focus states); reduced-motion respected.
- SEO: title/description/OG tags + JSON-LD `Person` schema are already in the file.
