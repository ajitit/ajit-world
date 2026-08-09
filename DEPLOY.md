# Deploying the Executive Website

The site is a single dependency-free `index.html` — no build step, no framework, no external fonts or scripts. It works on any static host.

## Option 1 — GitHub Pages (free, recommended)
```bash
# from a new empty repo (e.g. ajitit/ajitit.github.io)
git init && git add index.html && git commit -m "Executive site"
git branch -M main
git remote add origin https://github.com/ajitit/ajitit.github.io.git
git push -u origin main
# → live at https://ajitit.github.io within a minute
```

## Option 2 — Netlify / Vercel / Cloudflare Pages
Drag-and-drop the `website/` folder onto https://app.netlify.com/drop — done.
(Vercel: `npx vercel` in this folder. Cloudflare: Pages → Upload assets.)

## Option 3 — Custom domain
Buy e.g. `ajitkumar.tech`, point it at the host above, then update the
`og:url` meta tag in `index.html` to the real domain.

## Before going live — 3 edits to consider
1. Replace `https://ajitkumar.example.com/` in the `og:url` meta tag with your real URL.
2. Add a professional headshot if desired (hero section currently has none by design).
3. Fill the two `[METRIC NEEDED]` / `[INFORMATION REQUIRED]` markers when you have the numbers — they are honest placeholders, not errors.

## Notes
- Light & dark theme follow the visitor's OS preference automatically.
- Fully responsive to 375px; keyboard-accessible (native `<details>` expanders, visible focus states); reduced-motion respected.
- SEO: title/description/OG tags + JSON-LD `Person` schema are already in the file.
