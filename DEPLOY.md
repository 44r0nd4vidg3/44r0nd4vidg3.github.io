# Deployment Guide — aarondavidge.com

Production-ready static site. No build step required at deploy time (CSS is pre-compiled).

## Files to deploy (upload all of these)

**Pages**
- `index.html` — home
- `contact.html` — contact + A4RON.AI comms panel
- `security.html` — responsible disclosure policy
- `blog.html`, `store.html`, `signin.html`, `assistant.html` — "coming soon" placeholders
- `404.html` — themed not-found page

**Assets**
- `tailwind.css` — compiled, minified styles (all pages depend on this)
- `hero.webp` + `hero.jpg` — hero background (WebP with JPEG fallback)
- `card_image.jpg` — social share card (og:image / twitter:image)
- `aaron_resume.pdf` — served by the Download CV button

**Config / SEO / security**
- `_headers` — security headers + CSP (Netlify / Cloudflare Pages format)
- `robots.txt`
- `sitemap.xml`
- `.well-known/security.txt` — RFC 9116 (hidden folder — make sure it uploads)

> `hero.png` and `card_image.png` are original source images and are **not referenced** — omit them.

## Host-specific notes

- **Netlify / Cloudflare Pages:** `_headers` is picked up automatically. Set the 404
  by ensuring `404.html` is at the site root (both hosts use it by default).
- **Vercel:** translate `_headers` into `vercel.json` (`headers` array). 404 is automatic.
- **Apache:** convert `_headers` to `.htaccess` `Header set` directives; add
  `ErrorDocument 404 /404.html`.
- **Nginx:** move `_headers` values into `add_header` directives; `error_page 404 /404.html;`.

## Before you go live

1. Point `aarondavidge.com` DNS at the host; enable HTTPS (the HSTS header assumes TLS).
2. Create the `bugs@aarondavidge.com` mailbox (referenced by the security policy).
3. Optional: create `aaron@aarondavidge.com` for the contact links.
4. Verify the CSP doesn't block anything in your browser's console on first load.

## SEO & social (done)

- Home page ranks for "Aaron Davidge": real name in `<title>`, meta description,
  H-level body copy, PROFILE.DAT, and a JSON-LD `Person` schema (name, alternateName,
  jobTitle, sameAs links to GitHub/LinkedIn/X/Instagram, degree, knowsAbout).
- Open Graph + Twitter `summary_large_image` cards on index/contact/security, sharing
  `card_image.jpg` (1600×1127) with alt text — link previews render with the site screenshot card.
- `robots.txt` + `sitemap.xml` expose the 3 real pages; placeholders are `noindex`.
- **After deploy:** submit the site to Google Search Console and request indexing of `/`
  to speed up ranking for your name. Verify cards at the Facebook Sharing Debugger and
  the X Card Validator (they cache — re-scrape after any change).

## Content still to personalize

- Project tech-stack chips on the home page are best guesses — adjust to taste.

## When subdomains launch

The BLOG / STORE / assistant links currently point to local `*.html` placeholders.
When the real subdomains go live, swap:
- `blog.html`   → `https://blog.aarondavidge.com`
- `store.html`  → `https://store.aarondavidge.com`
- `assistant.html` → `https://assistant.aarondavidge.com`
(and delete the matching placeholder page + its `robots.txt` Disallow line).

## Security posture (MVP)

- 100% static — no server code, no database, no user input persisted. Minimal attack surface.
- CSP locks scripts/styles to self + inline (needed for the inline `<script>`/`<style>`);
  images to self + `data:`; fonts to Google Fonts only; `frame-ancestors 'none'` blocks clickjacking.
- All external links use `rel="noopener"`. No `eval`, no `document.write`; the one dynamic
  DOM write uses `textContent` (no HTML injection path).
- HSTS with `preload` — only submit to the preload list once you're confident in permanent HTTPS.
