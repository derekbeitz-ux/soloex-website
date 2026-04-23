# Soloex.io Website

Production codebase for [soloex.io](https://soloex.io) — a Salesforce and HubSpot consultancy for companies in CRM distress.

Built with Astro + Tailwind. Deployed on Cloudflare Pages.

---

## Stack

| Component | Choice |
|---|---|
| Framework | Astro 5 |
| Styling | Tailwind CSS v4 (via `@tailwindcss/vite`) + design tokens in `src/styles/global.css` |
| Fonts | Newsreader Variable (headlines) + Inter Variable (body), via `@fontsource-variable` |
| Hosting | Cloudflare Pages (free tier) |
| Domain | soloex.io (via Namecheap, pointed at Cloudflare) |
| Form handling | [Web3Forms](https://web3forms.com) (free, 250 submissions/month) |
| Analytics | Cloudflare Web Analytics (cookieless) |
| Booking | Calendly |
| Version control | Git + GitHub |

---

## Project structure

```
soloex-website/
├── astro.config.mjs          # Astro + sitemap + Tailwind
├── package.json              # Dependencies and scripts
├── tsconfig.json             # TypeScript config
├── TODO.md                   # Launch + post-launch punch list
├── public/
│   ├── favicon.svg           # Soloex diamond favicon
│   ├── og-default.svg        # Open Graph share image
│   └── robots.txt            # Allow-all + sitemap
└── src/
    ├── styles/
    │   └── global.css        # Design tokens, base styles, components
    ├── layouts/
    │   └── Layout.astro      # Base layout: head, meta/SEO, Nav, Footer
    ├── components/
    │   ├── Logo.astro        # SVG logo + wordmark
    │   ├── Nav.astro         # Sticky top nav + mobile drawer
    │   └── Footer.astro      # 4-column footer + bottom bar
    └── pages/
        ├── index.astro       # Homepage (13 sections)
        ├── services.astro    # Implement · Migrate · Optimize
        ├── about.astro       # Founder story + team
        ├── process.astro     # 6-step engagement walkthrough
        ├── contact.astro     # Calendly + Web3Forms contact form
        ├── privacy.astro     # Privacy policy (PA governing law)
        └── terms.astro       # Terms of service (PA governing law)
```

---

## Running locally

```bash
npm install
npm run dev
```

Open http://localhost:4321. Auto-reloads on save.

Other scripts:

```bash
npm run build      # Static build to dist/
npm run preview    # Serve the built site locally
```

---

## Deploying

The site auto-deploys to Cloudflare Pages on every push to `main`.

1. Push to GitHub (`git push`).
2. Cloudflare Pages picks up the change, runs `npm run build`, and publishes `dist/` in ~60 seconds.
3. Verify at https://soloex.io.

Cloudflare Pages settings:
- **Framework preset:** Astro
- **Build command:** `npm run build`
- **Build output directory:** `dist`
- **Node version:** 20 (or whichever Cloudflare auto-detects)

---

## Design tokens

All colors and fonts live in `src/styles/global.css` as CSS custom properties. Change one line, change the whole site.

```css
--color-ink-900: #051A2B;   /* Darkest navy — headlines, dark sections */
--color-ink-700: #0C5494;   /* Primary CTA, links, body emphasis */
--color-ink-500: #479DE7;   /* Accents, secondary highlights */
--color-ink-300: #A8D4FA;   /* Soft accents on dark */

--font-serif: 'Newsreader Variable', Georgia, serif;
--font-sans:  'Inter Variable', system-ui, -apple-system, sans-serif;
```

The subtle white/navy grid background sits on `html` as an inline SVG at 8% opacity — open `global.css` and adjust the `html { background-image: ... }` rule to tweak.

---

## Placeholders to replace before launch

See `TODO.md` for the full list. Short version:

1. **Web3Forms access key** in `src/pages/contact.astro`
2. **Cloudflare Web Analytics token** in `src/layouts/Layout.astro`
3. **10 client logos** in `src/pages/index.astro` (`clientLogos` array)
4. **3 project highlights** in `src/pages/index.astro` (`projects` array)
5. **Testimonial attributions** in `src/pages/index.astro` (`testimonials` array)
6. **Kristin's headshot** (currently a gray circle; swap in `src/pages/index.astro` + `src/pages/about.astro`)
7. **Footer badges** (currently text pills; swap for SVG files in `src/components/Footer.astro`)

---

## Brand voice (short version)

- Sage / Guide archetype. Bold but calm. No hype, no hedging.
- "We" throughout — Soloex is a company, not a freelancer.
- Never write: *Summit-tier consultancy · 5 years of experience · crush · unlock · revolutionary*
- OK to write: *Summit-trained · former consultant at a Summit-tier Salesforce Partner · certified Salesforce Partner · 100+ projects*

The full brand brief lives in `../Soloex.io Website Build/01-creative-brief.md`. Read it before writing new copy.

---

## Common edits

### Change the homepage headline
`src/pages/index.astro` — first `<h1>` in the hero section.

### Update nav links
`src/components/Nav.astro` — edit `navItems` array near the top.

### Add a new page
Create `src/pages/foo.astro`:

```astro
---
import Layout from '../layouts/Layout.astro';
---

<Layout title="Foo — Soloex.io" description="Plain description for search + social.">
  <section class="section-hero">
    <div class="container-narrow">
      <h1>Foo</h1>
    </div>
  </section>
</Layout>
```

Astro auto-creates the `/foo` route. The sitemap regenerates on build.

---

## License

Code in this repository is the property of Soloex.io. Content, branding, and copy are not licensed for external use. Third-party fonts (Newsreader, Inter) are used under the Open Font License.
