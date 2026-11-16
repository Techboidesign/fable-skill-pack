---
name: frontend-ship-check
description: "Pre-deploy checklist for a website - build, links, responsive, accessibility, performance, SEO/meta, forms, hosting config. Use for /ship-check, 'ready to deploy?', before going live."
---

# Front-end ship check

Run the checks; don't assume. Report PASS/FAIL per line with evidence.

## 1. Build
- Clean install + production build succeeds, zero errors. Note warnings.
- No `console.log`, TODO, lorem ipsum, localhost URLs, test keys: grep for them.
- Secrets not in the repo or the client bundle.

## 2. Pages & links
- Every route loads (200). Custom 404 exists.
- No broken internal links or images (crawl the built output).
- External links: `rel="noopener"` when `target="_blank"`.

## 3. Responsive
- 360, 768, 1280, 1920 wide: no horizontal scroll, no clipped text, tap targets >= 44px.
- Long words/names, empty states.

## 4. Accessibility (WCAG 2.2 AA basics)
- One `h1`, heading order without skips; landmarks (`header/nav/main/footer`).
- Every image: meaningful `alt` or `alt=""` if decorative.
- Contrast 4.5:1 text, 3:1 large text and UI.
- Full keyboard path; visible `:focus-visible`; skip link.
- Form inputs labelled; errors announced in text.
- `lang` on `<html>`; `prefers-reduced-motion` respected.

## 5. Performance
- Images: modern format (AVIF/WebP), sized to display, `width`/`height` set, `loading="lazy"` below the fold, hero image prioritised.
- Fonts: woff2, subset, `font-display: swap`, preload the one above-the-fold face.
- No unused heavy JS; CSS/JS minified.
- Run Lighthouse if available. Targets (Google's Core Web Vitals "good"): LCP <= 2.5s, INP <= 200ms, CLS <= 0.1.

## 6. SEO & sharing
- Unique `<title>` and meta description per page.
- Canonical URL; `robots.txt`; `sitemap.xml`.
- Open Graph + Twitter card tags; OG image 1200x630, absolute URL.
- Favicon set + `apple-touch-icon`; `theme-color`.
- Structured data where it fits (Person, Organization, LocalBusiness).

## 7. Forms & third parties
- Submit a real test; success and error states; spam protection.
- Analytics/cookies: consent where the law requires (EU: yes for non-essential cookies).
- Privacy/legal pages linked if data is collected.

## 8. Hosting
- HTTPS forced; www/non-www redirect to one; trailing-slash consistent.
- Redirects from old URLs (301) if replacing a site.
- Cache headers: long for hashed assets, short for HTML.
- Security headers where the host supports them (HSTS, X-Content-Type-Options, Referrer-Policy, a CSP if feasible).
- Env vars set in the host, not committed.

## Output
```
VERDICT: SHIP | FIX FIRST
| Area | Check | Result | Evidence | Fix |
Blockers: ...
Not checked: ...
```
Blockers = broken build/route, a11y failure on a primary flow, leaked secret, broken form. Everything else can follow the launch.
