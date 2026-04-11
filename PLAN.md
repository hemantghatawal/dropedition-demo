# Shopify Landing Page — Build Plan

## Overview
Building a scalable, theme-configurable Shopify landing page using OS 2.0 standards.
Font: Inter | Animations: GSAP (CDN) | Approach: Section by section, one at a time.

---

## Section Roadmap

| # | Section File | Description | Status |
|---|---|---|---|
| 1 | `sections/header.liquid` | Logo (text), nav links, icons | 🔄 Built — awaiting animation |
| 2 | `sections/hero-banner.liquid` | Full-width bg image, text reveal, CTA | ⬜ Not started |
| 3 | `sections/featured-collection.liquid` | "Bestseller" — 3 static product cards | ⬜ Not started |
| 4 | `sections/living-room.liquid` | Asymmetric image grid + Shop Now arrow | ⬜ Not started |
| 5 | `sections/craftsmanship.liquid` | Dark section, large heading, two-col text | ⬜ Not started |
| 6 | `sections/sort-by-type.liquid` | Horizontal scrollable category row | ⬜ Not started |
| 7 | `sections/journals.liquid` | Large image left + smaller images right | ⬜ Not started |
| 8 | `sections/newsletter.liquid` | Dark bg, email subscribe form (visual) | ⬜ Not started |
| 9 | `sections/footer.liquid` | Video bg + glass card + Drop Edition style | ⬜ Not started |

---

## Global Architecture

### Design Tokens (set once, used everywhere)
- **File:** `config/settings_schema.json` + `snippets/css-variables.liquid`
- Colors: `--color-primary`, `--color-secondary`, `--color-bg`, `--color-text`, `--color-accent`
- Typography: `--font-heading`, `--font-body`, font size scale
- Spacing: `--space-xs` → `--space-xl`

### Font
- **Inter** — loaded via Shopify font system

### GSAP
- Loaded via CDN in `layout/theme.liquid`
- Plugins: ScrollTrigger (scroll animations), gsap core
- CDN: `https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js`
- ScrollTrigger: `https://cdn.jsdelivr.net/npm/gsap@3/dist/ScrollTrigger.min.js`

---

## Section-by-Section Animation Plan

| # | Section | GSAP Animation |
|---|---|---|
| 1 | Header | Fade-in from top on page load |
| 2 | Hero Banner | Background image fade-in + heading/CTA text reveal (stagger) |
| 3 | Featured Collection | Cards stagger fade-up on scroll |
| 4 | Living Room | Images fade-in with slight scale on scroll |
| 5 | Craftsmanship | Heading letter/word reveal + text fade-in on scroll |
| 6 | Sort By Type | Horizontal items stagger fade-in on scroll |
| 7 | Journals | Images parallax subtle shift on scroll |
| 8 | Newsletter | Section fade-up + input/button reveal on scroll |
| 9 | Footer | Video autoplay bg, glass card fade-in on scroll |

---

## Workflow Rules
- ✅ One section at a time
- ✅ No next section without explicit user permission
- ✅ After each section is built, user provides animation instructions
- ✅ Animations are added to that section before moving on
- ✅ All text uses `{{ 'key' | t }}` with keys in `locales/en.default.json`
- ✅ No hardcoded colors, fonts, or spacing — all via CSS variables
- ✅ Static image/text via schema settings (no live collection data yet)

---

## Key Files

| File | Purpose |
|---|---|
| `config/settings_schema.json` | Global design tokens |
| `snippets/css-variables.liquid` | Maps settings → CSS custom properties |
| `layout/theme.liquid` | GSAP CDN scripts loaded here |
| `locales/en.default.json` | All translation strings |
| `templates/index.json` | Wires all sections to the homepage |
| `assets/hero-banner.png` | Hero background image (uploaded) |
| Footer video | `https://dropedition.com/videos/footer-video.mp4` |

---

## Notes
- Footer video is external URL (Drop Edition CDN) — no need to upload
- "LOGO" renders as `shop.name` text — no image logo
- All links use `#` as placeholder until real URLs are provided
- Newsletter form is visual only (no Shopify form tag yet)
