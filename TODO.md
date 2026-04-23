# Soloex.io — Launch TODO

Track every placeholder that needs a real value, and every post-launch task that can't ship on day one.

---

## Before site handles real traffic

### Cloudflare Web Analytics (cookieless)
- [ ] In Cloudflare → Analytics & Logs → Web Analytics → Add a site → enter `soloex.io`.
- [ ] Copy the beacon token Cloudflare shows.
- [ ] Open `src/layouts/Layout.astro`. Find the commented-out `<script defer src="https://static.cloudflareinsights.com/beacon.min.js" ...>` line and uncomment it. Paste the token where it says `TOKEN`.
- [ ] Commit and push.

---

## This week — shipping now without them

These are shipping to production without the final piece in place. Swap them in as soon as the missing piece lands.

### Testimonial attributions (homepage Section 9)
- File: `src/pages/index.astro`, `testimonials` array.
- Current state: initials + role only (`— J.M., VP of Operations`, etc.). Quotes are real Upwork 5-star reviews. No fake company names on the page.
- Missing piece: explicit permission from each of the three reviewers to use their full names + company names publicly.
- Action: send the request template in `docs/03-copy-and-content-bank.md` §7.4 to each reviewer. Once permission comes back, add `name` and `company` fields to the testimonial objects and update the template to render `— First L., Role, Company`.

---

## Placeholders to replace

### Footer badges
- File: `src/components/Footer.astro`.
- Current: text pills `WBENC certified` and `Salesforce Partner`.
- Action: download badge SVGs from WBENC and the Salesforce Partner Community, save to `public/badges/wbenc.svg` and `public/badges/salesforce.svg`, swap the text pills for `<img>` tags.

---

## Deferred — add post-launch

### Client logo carousel (originally homepage Section 4)
- The carousel section was removed from the homepage entirely at launch — no placeholder tiles, no stub section.
- When real logos are ready, rebuild it as a `<LogoCarousel>` component at `src/components/LogoCarousel.astro` that takes an array of image paths + alt text, and drop the files into `public/logos/`.
- Slot it back into `src/pages/index.astro` between Section 3 (Upwork proof bar) and Section 5 (The Problem), and re-point the hero's "See our work" secondary CTA from `#work` to the carousel's anchor if desired.
- **Get written permission from each client before their logo goes live.**

---

## Post-launch follow-ups

### Domain and DNS
- [ ] Confirm Cloudflare nameservers are active for `soloex.io` (check in Namecheap → Domain List).
- [ ] Add `www.soloex.io` as a custom domain in Cloudflare Pages (Cloudflare handles the redirect).
- [ ] Verify HTTPS works on both `https://soloex.io` and `https://www.soloex.io`.

### Email deliverability
- [ ] Confirm SPF, DKIM, and DMARC records are set for `soloex.io` in Cloudflare DNS (these should exist already since email is working — just verify Cloudflare imported them).

### SEO
- [ ] Submit `https://soloex.io/sitemap-index.xml` to Google Search Console.
- [ ] Add `soloex.io` to Bing Webmaster Tools.
- [ ] Double-check meta descriptions are unique per page (they are at launch — keep it that way as pages are added).

### AppExchange listing
- Current AppExchange URL is wired into the footer. Once the listing moves out of "pending" status, verify the URL still works and update the footer badge with the real AppExchange badge image.

### Automotive Cloud beta
- Surfaced as a pill on the homepage Platforms section. If the status changes (beta ends, named participant), update the copy in `src/pages/index.astro` and `src/pages/services.astro`.

### WBENC public profile link
- Consider linking the WBENC footer badge to Soloex's public profile page on `wbenc.org` once it's live.

### Newsletter (not at launch)
- If a newsletter is added later, use a reputable tool that handles unsubscribes automatically (Buttondown, Mailchimp, ConvertKit). Do not add contact-form submitters to a bulk list without a clearer, separate opt-in.

---

## Iteration candidates (optional polish)

- [ ] Real client case-study page once 3+ projects have written permission.
- [ ] Resources / lead-magnet section (audit template, CRM readiness checklist).
- [ ] Add HubSpot Partner badge to footer once status is live.
- [ ] Replace the text wordmark in `Logo.astro` with the actual Soloex wordmark file if/when provided.
- [ ] Consider adding a FAQ accordion to the Contact page for common questions ("do you take fixed bids?", "do you work on retainer?", etc.).
- [ ] Add `<link rel="preload">` for hero fonts if Core Web Vitals show LCP pressure.

---

## Routine maintenance

- Bump Astro and dependencies monthly (`npm update`).
- Check Cloudflare Web Analytics quarterly for traffic shape; adjust copy and CTAs accordingly.
- Review every testimonial / project highlight annually for continued accuracy.
