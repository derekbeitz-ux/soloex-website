# Soloex.io - TODO

Launched 2026-04-23. Live at https://soloex.io.

This file tracks what shipped at launch and what's queued for after. The post-launch list is prioritized: week-one items flagged `[week 1]` unblock revenue or credibility; everything else is "when you have time."

---

## Done at launch (v1.0)

### Build
- [x] Astro 5 scaffold with Tailwind v4, variable fonts (Newsreader + Inter), `@astrojs/sitemap`, design tokens in `src/styles/global.css`
- [x] Seven pages: Home (13-section structure minus the deferred logo carousel), Services, About, Process, Contact, Privacy, Terms
- [x] BaseLayout with shared Nav + Footer (LinkedIn, Upwork, AppExchange social icons)
- [x] Grid SVG background at 8% navy opacity across every page
- [x] All copy pulled from `docs/03-copy-and-content-bank.md` (source of truth lives in `/docs`)
- [x] Astro `<Image>` for headshots (WebP, 1x/2x densities, 112px circles, matched treatment)
- [x] Astro `<Picture>` for family photo (AVIF + WebP + JPG fallback, 4-width srcset, 720px contained frame)
- [x] Four real project highlights in 2x2 desktop grid on homepage
- [x] Three Upwork 5-star reviews rendered as initials + role (no fake company names)

### SEO + accessibility
- [x] Unique title + meta description per page, OG tags, canonical URLs
- [x] `sitemap-index.xml` auto-generated, linked from `robots.txt`
- [x] Semantic HTML, one `<h1>` per page, keyboard focus rings, AA-contrast text, alt text on every image, skip-link

### Forms + delivery
- [x] Web3Forms contact form with live access key, honeypot on, dynamic subject line per submitter, inline thank-you panel, error fallback
- [x] Contact form tested end to end - delivery confirmed to `derek.beitz@soloex.io`

### Infra
- [x] Git repo at `github.com/derekbeitz-ux/soloex-website`, main-branch auto-deploy
- [x] Cloudflare Pages connected to the repo, build command `npm run build`, output `dist/`
- [x] Namecheap nameservers switched to Cloudflare; zone active
- [x] Both `soloex.io` (apex) and `www.soloex.io` configured as Pages custom domains
- [x] SSL issued and active (Google Trust Services via Cloudflare)
- [x] Email records (MX, SPF, DKIM, DMARC) survived the nameserver switch - derek.beitz@ and operations@ confirmed working post-switch

### Brand / voice
- [x] Em dashes banned site-wide (`docs/01-creative-brief.md` §2.3 codifies the rule)
- [x] A1 "no public faith references" rule retired in favor of a narrower rule that permits the About page backstory (§1.2)

---

## Post-launch follow-ups

### This week - flagged `[week 1]`

These unblock either revenue, credibility, or basic ops hygiene. Worth knocking out in the first seven days.

- [ ] **`[week 1]` Wire Cloudflare Web Analytics.** The beacon snippet is already staged in `src/layouts/Layout.astro` (commented out). In Cloudflare dashboard -> Analytics & Logs -> Web Analytics -> Add a site -> enter `soloex.io` -> copy the beacon token -> uncomment the script tag in Layout.astro and paste the token where it says `REPLACE_ME`. Commit and push. Without this you're flying blind on traffic.
- [ ] **`[week 1]` Submit sitemap to Google Search Console.** Verify ownership at https://search.google.com/search-console (the fastest method is a DNS TXT record, which you can add directly in the Cloudflare DNS tab since the zone is now there). Once verified, submit `https://soloex.io/sitemap-index.xml`. Indexing starts within 48 hours.
- [ ] **`[week 1]` Request testimonial permissions.** Three reviewers on the homepage render as `J.M.`, `S.R.`, `K.T.` - pull their real names from your Upwork contract history and send each the template in `docs/03-copy-and-content-bank.md` §7.4. Once you have written permission, add `name` and `company` fields to the `testimonials` array in `src/pages/index.astro` and update the render template. Full-name testimonials convert significantly better than initials.
- [ ] **`[week 1]` Announce the launch on LinkedIn.** Post from both the Soloex company page and your personal profile. Include the soloex.io URL. You're losing reach for every day this sits.
- [ ] **`[week 1]` Add `soloex.io` to your email signature** and update the Upwork profile's portfolio link.

### Content + credibility (next 30 days)

- [ ] **Rebuild the client logo carousel.** Removed at launch since real logos needed written permission. When 8-10 clients have granted use of their logos, create `src/components/LogoCarousel.astro` that takes an array of `{ src, alt }`, drop the logo files into `public/logos/`, and slot the section back into `src/pages/index.astro` between Section 3 (Upwork bar) and Section 5 (Problem). Re-point the hero's `See our work` button from `#work` to the carousel anchor if you want it to jump there instead.
- [ ] **Project case studies.** The homepage has four one-sentence project highlights. Each could become a proper case study: situation, what you did, outcome, quote. If two of the four clients are willing, a `/work` page with two case studies would meaningfully upgrade the credibility story.
- [ ] **Paired founder photoshoot.** Derek's headshot is outdoor, Kristin's is studio. They read as a pair because we applied identical treatment (same circle, same ring, same crop framing) - but if you get one shoot together in similar lighting, it'll read sharper. Once the files are ready, drop them into `src/assets/` with the same filenames and the site picks them up automatically.
- [ ] **HubSpot Partner badge** in the footer once your HubSpot partner status is live. Currently only WBENC and Salesforce Partner pills show.
- [ ] **Real WBENC and Salesforce Partner badge SVGs** (footer currently uses text pills). Download from each partner portal, save to `public/badges/`, swap into `src/components/Footer.astro`.
- [ ] **AppExchange badge graphic** once the listing moves out of `pending`. URL is already wired - just swap the footer icon for the real AppExchange badge when available.

### SEO + growth (ongoing)

- [ ] Add `soloex.io` to Bing Webmaster Tools.
- [ ] Consider a `/resources` page once you have a lead magnet (CRM audit template, migration readiness checklist, or similar).
- [ ] Contact-page FAQ accordion for common qualifying questions ("fixed bid vs retainer?", "do you work internationally?", "do you take on full implementations or only migrations?").

### Brand polish (when the mood strikes)

- [ ] Replace the text wordmark in `src/components/Logo.astro` with the actual Soloex wordmark SVG if/when one is designed.
- [ ] WBENC footer badge -> link to Soloex's public WBENC profile page on `wbenc.org` once that URL is live.
- [ ] `<link rel="preload">` for the hero fonts if Core Web Vitals show LCP pressure in Cloudflare Analytics.
- [ ] Canonical `www` -> apex redirect via Cloudflare Page Rule. Currently both `soloex.io` and `www.soloex.io` serve the site directly. Not broken, just not canonical.

### Monitoring + maintenance (set and forget)

- [ ] Bump Astro and dependencies monthly (`npm update`, commit the lockfile, push). Cloudflare builds will fail loudly if anything breaks.
- [ ] Check Cloudflare Web Analytics monthly for traffic shape; use it to sharpen copy and CTAs on pages that are underperforming.
- [ ] Review testimonials and project highlights annually for continued accuracy (clients change roles, companies merge, metrics go stale).
- [ ] If a newsletter gets added later, use a reputable tool that handles unsubscribes automatically (Buttondown, Mailchimp, ConvertKit). Do not move contact-form submitters to a bulk list without a separate opt-in.
- [ ] Check Core Web Vitals every quarter in PageSpeed Insights. Current build is lean but images are the biggest payload - watch as case studies get added.

---

## Not doing (deliberate no at launch)

Listed here so future-Derek (or future-Claude) doesn't treat them as oversights:

- **Dark mode.** Brand is light-theme by design (creative brief §3.1).
- **Cookie banner.** Cloudflare Web Analytics is cookieless; no other trackers. Not legally required.
- **Blog / CMS.** Astro can gain a content collection later if blogging becomes strategic. Not at launch.
- **Newsletter signup in footer.** Deferred per creative brief §11.2 until there's actually a newsletter to sign up for.
- **Instagram, Twitter/X, YouTube icons.** No active accounts yet. Add when there's a reason to.
