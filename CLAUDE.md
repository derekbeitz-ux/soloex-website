# CLAUDE.md

Operating guide for AI coding assistants working in this repository. Read this end to end before editing code. The deep brand context lives in `/docs`; this file is the working rulebook.

---

## 1. Project overview

Soloex.io is a Salesforce and HubSpot consultancy for companies in CRM distress. Co-founders: Derek Beitz (technical lead) and Kristin Beitz (operations). Women-owned, WBENC certified. Mechanicsburg, PA.

This repository is the marketing website. Seven pages: Home, Services, About, Process, Contact, Privacy, Terms. It is a public conversion surface; every change is reader-facing.

For the full brand brief, see `docs/01-creative-brief.md`. For homepage section structure, `docs/02-homepage-structure.md`. For the copy bank (reusable content, founder story, testimonials), `docs/03-copy-and-content-bank.md`. **Treat the docs directory as the source of truth for content.** When you change copy in a page, update the matching section in `/docs`.

---

## 2. Stack

| Component | Choice |
|---|---|
| Framework | Astro 5 (static) |
| Styling | Tailwind v4 via `@tailwindcss/vite` + design tokens in `src/styles/global.css` |
| Fonts | Newsreader Variable (serif headlines) + Inter Variable (sans body), via `@fontsource-variable` |
| Images | Astro `<Image>` and `<Picture>` from `astro:assets`. Source files in `src/assets/` so they flow through the optimizer. Never reference images from `public/` unless you explicitly want no optimization. |
| Forms | Web3Forms (access key in `src/pages/contact.astro`) |
| Analytics | Cloudflare Web Analytics (cookieless), beacon snippet staged in `src/layouts/Layout.astro` |
| Hosting | Cloudflare Pages, auto-deploy from `main` |
| Sitemap | `@astrojs/sitemap` generates at build time |

Local commands: `npm run dev` (4321), `npm run build`, `npm run preview`.

---

## 3. File organization

```
src/
  assets/        # Images that should be optimized by Astro (JPG, PNG)
  components/    # Reusable .astro components: Logo, Nav, Footer
  layouts/
    Layout.astro # Base layout: head, meta, Nav, Footer, skip-link
  pages/         # One .astro file per route
  styles/
    global.css   # Design tokens + base styles (colors, type, components)
public/          # Static files served as-is (favicon, og-default.svg, robots.txt)
docs/            # Brand + content source of truth (creative brief, copy bank)
```

Every page uses `<Layout>`. Every page has exactly one `<h1>`. Section padding and container widths come from `global.css` (`.container`, `.container-narrow`, `.container-wide`, `.section-hero`, `.section-compact`, `.section-tight`, `.section-tinted`, `.section-dark`).

---

## 4. Voice and copy rules

Sage / Guide archetype. Bold but calm. Wisdom, not hype. See `docs/01-creative-brief.md` §2 for the full voice spec.

### Rules

- **"We" throughout.** Soloex is a company, not a freelancer.
- **No hedging.** Never "we think," "we try," "we hope."
- **No hype.** Never "crush," "unlock," "game-changing," "revolutionary."
- **No sales-y urgency.** Never "limited time," "don't miss out."
- **No ALL CAPS.** Never, anywhere.
- **Exclamation points** are not default punctuation. Use sparingly (the CTA `Fix my CRM →` does not need one).
- **Use regular hyphens (-), never em dashes (—). Em dashes read as AI-generated.**
- **Never claim Soloex is Summit-tier.** We are a certified Salesforce Partner, and Derek trained at a Summit Partner. OK: "former consultant at a Summit-tier Salesforce Partner," "trained inside a Summit-tier agency before going independent," "Summit-trained." Not OK: "Summit-tier consultancy," "Summit-tier work," "Summit-tier expertise."
- **Never "5 years of experience."** Lead with "100+ projects" instead. OK: "nearly 5 years in the CRM ecosystem."
- **Scripture, doctrine, and faith-based sales framing are off-limits everywhere.** The About page may reference the founders' personal backstory (they met on a college missions trip in Africa) as the one exception. See `docs/01-creative-brief.md` §1.2 for the full policy.

### Approved alternatives to em dashes

| Instead of | Use |
|---|---|
| "the actual work — business analysis, …" | "the actual work - business analysis, …" (regular hyphen with spaces) |
| "the actual work — business analysis, …" | "the actual work: business analysis, …" (colon) |
| "the actual work — business analysis, …" | "the actual work. Business analysis, …" (sentence break) |

Prefer the sentence break when it reads natural. Use the spaced hyphen when you need the dash rhythm.

---

## 5. Design system

Colors and fonts are CSS custom properties in `src/styles/global.css`. Change one line, change the whole site.

### Palette

| Token | Hex | Use |
|---|---|---|
| `--color-ink-900` | `#051A2B` | Darkest navy. Body text, dark-section backgrounds. |
| `--color-ink-700` | `#0C5494` | Primary CTA fill, links, emphasis. |
| `--color-ink-500` | `#479DE7` | Accents, secondary callouts, logo flow lines. |
| `--color-ink-300` | `#A8D4FA` | Soft accents on dark backgrounds. |
| `--color-text-secondary` | `#4A5A6B` | Muted body text, descriptions. |
| `--color-bg-tinted` | `#F7FAFD` | Alternating section tint. |

### Type

- Headlines: `var(--font-serif)` = Newsreader Variable, weight 500, letter-spacing -0.015em.
- Body: `var(--font-sans)` = Inter Variable, weight 400 for prose, 500 for buttons and labels.
- Numeric displays: Inter (not the serif).
- Never use Tailwind font utilities when a variable exists; reach for the token.

### Background texture

`html` has an inline SVG grid at 40×40px, 0.5px navy stroke, 8% opacity. This is the signature visual anchor. Don't remove it.

### Buttons

`.btn` base, with `.btn-primary` (filled ink-700), `.btn-secondary` (outline), `.btn-light` (for dark sections). Sizes: `.btn-nav`, `.btn-large`.

### Cards and pills

`.card` for white content cards with hairline border. `.pill-dark` for the platform tags on the dark Platforms section. `.tag` for neutral pills.

### Breakpoints

Two primary breakpoints: 900px (tablet to mobile, grid collapses) and 640px (small mobile, type resizes). See the media queries at the bottom of each page's scoped style block.

---

## 6. Deployment

The site auto-deploys to Cloudflare Pages on push to `main`. Build command: `npm run build`. Output: `dist/`.

Every commit to main triggers a fresh build in ~60-90 seconds. The Cloudflare Pages project UI at dash.cloudflare.com shows build logs. If a build fails, check the log - it's almost always a missing asset or a typo in frontmatter.

Domain: `soloex.io` via Namecheap, pointed at Cloudflare nameservers. `www.soloex.io` redirects to apex.

Never commit directly from Claude to production without a clear "ship it" from Derek. Never push to main with an unconfirmed change to copy, pricing, or legal pages.

---

## 7. When you edit something

1. **Content change** (copy edit, section addition): update the matching section in `/docs` too, in the same commit. The docs are the source of truth; the page is the render of it.
2. **Design token change**: edit `src/styles/global.css` and verify every page still reads correctly. A palette or type shift affects all 7 pages.
3. **New page**: `src/pages/<name>.astro`, wrap in `<Layout title="..." description="..." active="...">`, give it a single `<h1>`, use `container-narrow` for text-heavy pages and `container` for card grids.
4. **New asset**: put optimized-eligible images in `src/assets/`, reference them with `<Image>` or `<Picture>` from `astro:assets`. Public-folder images skip the optimizer and should be a last resort.
5. **Build before you push**: run `npm run build` locally. The sitemap regenerates, Astro catches broken imports and missing images, and the optimizer reports file sizes so you can tell if a new photo is carrying too much weight.

---

## 8. Known pending items

Tracked in `TODO.md` at the project root. Keep that file current when you finish an item or add a new one.
