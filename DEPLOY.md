# Deploying www.ajit.world

The site is a single dependency-free `index.html` — no build step, no framework, no external fonts or scripts. It works on any static host. This repo is already wired for Netlify.

**Important:** the apex `ajit.world` is a separate, existing deployment (a homelab/AgentOS platform) already routed via Cloudflare DNS — it is *not* this site and must not be touched. This site lives at **`www.ajit.world`** only.

## Current setup — Netlify (git-connected)
1. Repo: https://github.com/ajitit/ajit-world (this repo)
2. Netlify: **Add new site → Import an existing project → Deploy with GitHub** → select `ajit-world`
   - Build command: *(blank)*
   - Publish directory: `.`
   - (`netlify.toml` in this repo pins these automatically, plus security headers)
3. Netlify: **Site configuration → Domain management → Add a domain** → `www.ajit.world` (not the apex) → follow Netlify's verification steps
4. DNS is managed in **Cloudflare** (registrar is GoDaddy, but nameservers point to Cloudflare — check GoDaddy's nameserver settings if unsure). In Cloudflare → DNS → Records:
   - Edit the existing `www.ajit.world` `CNAME` record: change its content from `ajit.world` to `<your-site>.netlify.app`
   - Set its **Proxy status to "DNS only"** (grey cloud) so Netlify can issue and manage its own TLS certificate for `www.ajit.world` directly
   - **Do not touch** the two `A` records on the bare `ajit.world` apex — those serve the homelab platform
5. Netlify auto-provisions free HTTPS (Let's Encrypt) once DNS resolves. Pushes to `main` auto-deploy.

## Alternative hosts (if ever migrating off Netlify)
- **GitHub Pages**: add a `CNAME` file containing `www.ajit.world`, enable Pages on this repo, point the Cloudflare `CNAME` for `www` at `<user>.github.io`.
- **Cloudflare Pages**: `Workers & Pages → Create → Pages → Connect to Git` → same repo, publish dir `.`.
- **Vercel**: `npx vercel` from this folder, or import the repo at vercel.com.

## Before going live — checklist
1. ✅ `og:url` meta tag set to `https://www.ajit.world/`.
2. Add a professional headshot if desired (hero section currently has none by design).
3. Fill the two `[METRIC NEEDED]` / `[INFORMATION REQUIRED]` markers in `index.html` when you have the numbers — they are honest placeholders, not errors.

## Notes
- Deep Space dark theme is permanent (brand system), not OS-preference-dependent.
- Fully responsive to 375px; keyboard-accessible (native `<details>` expanders, visible focus states); reduced-motion respected.
- SEO: title/description/OG tags + JSON-LD `Person` schema are already in the file.
