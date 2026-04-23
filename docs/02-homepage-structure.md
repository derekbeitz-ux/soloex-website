# 02 · Homepage Structure

The homepage carries most of Soloex's conversion weight. This document breaks it down section by section — what's there, why it's there, and what content fills it.

The homepage has 13 sections, top to bottom.

---

## Section 1 · Hero

**Purpose:** First impression. Headline that names the pain, subhead that names the solution, CTAs that capture the click.

**Contents:**
- **Headline (Newsreader, large):** *"Your CRM isn't working. We'll fix it."* (working copy — may refine at build)
- **Subheadline (Inter, smaller):** *"Salesforce and HubSpot consulting without the agency overhead. Five years in. 100+ projects delivered. Women-owned."*
- **Primary CTA button:** `Fix my CRM →` — filled, dark blue (`#0C5494`), links to Calendly
- **Secondary CTA button:** `See our work` — outlined, scrolls to logo carousel (Section 4)

**Visual:**
- White background with subtle grid-line texture (40×40px SVG pattern, ~10% opacity navy)
- Generous whitespace above and below content
- Hero copy left-aligned, max-width ~540px
- No hero image required (text + stats do the lifting)

---

## Section 2 · Stats Strip

**Purpose:** Instant credibility above the fold. Specific numbers the visitor can verify.

**Contents:**
| 100+ | 5 | WBENC | Summit-trained |
|---|---|---|---|
| projects completed | certifications *(Salesforce + HubSpot)* | certified, women-owned | former Salesforce Summit Partner consultant |

**Visual:**
- Four columns, evenly spaced
- Large number or key word in Newsreader, weight 500
- Small descriptor below in Inter, muted text color
- Full-width section with light separator above and below

---

## Section 3 · Upwork Proof Bar

**Purpose:** Third-party verified social proof. One of Soloex's strongest assets.

**Contents:**
> ★ **5.0** on Upwork · **100%** Job Success · **Top Rated Plus** *(top 3% globally)*
>
> [*→ Read reviews on Upwork*]

**Visual:**
- Compact horizontal bar, centered
- Small gold/amber star icons for the rating
- Link arrow on the right goes to Upwork profile
- Do NOT copy Upwork's branded badge graphics — recreate the information in Soloex's design system

---

## Section 4 · Client Logo Carousel

**Purpose:** Social proof at scale. Familiar logos = legitimacy.

**Contents:**
- 10–15 client logos (gathered pre-launch — see checklist)
- Scrolls right-to-left in a continuous loop
- Logos displayed in grayscale by default
- Hover highlights a logo to its full color
- Short label above: *"Trusted by leading teams"* (or similar)

**Visual:**
- Full-width scroll with logos evenly spaced
- Logos masked to consistent height (~28px)
- Smooth infinite animation (CSS or lightweight JS)
- Inspired by getambassador.com

**Technical note:** The carousel should have two copies of the logo list in the scroll container for seamless looping.

---

## Section 5 · The Problem

**Purpose:** Agitate the pain. Make the visitor nod and say, "That's me."

**Contents:**
Three cards addressing the three CRM pain states that map to Soloex's three services:

| Card 1 · Inherited Mess | Card 2 · Outgrown System | Card 3 · Tech Stack Exhaustion |
|---|---|---|
| Someone before you built it wrong, customized it to death, or abandoned it mid-project. | What worked for 20 people is breaking at 150. Reports are slow. Data is stale. Teams are working around the system. | Too many tools. Too many workflows. Nothing is integrated the way it should be. Your team is drowning in tabs. |

**Visual:**
- Three equal cards, clean borders, light background
- Each card has an optional small icon at top (TBD — simple line icon in medium blue)
- Headline in Newsreader, body in Inter
- Cards lead the eye naturally into Section 6 (Services) — each problem maps to a service

---

## Section 6 · Services (Implement · Migrate · Optimize)

**Purpose:** The solution to the problem just named.

**Contents:**
Three service cards, each with:

### Implement
*Start fresh. Build right.*
Full Salesforce or HubSpot implementation from the ground up — scoped, architected, delivered. No abandoned half-builds. No "we'll figure it out in production."
`→ Learn more`

### Migrate
*Out of the old. Into what works.*
Platform switches, data migrations, consolidation. Salesforce ↔ HubSpot, or from Zoho, Marketo, Eloqua, or other systems. Zero data loss. Minimal downtime.
`→ Learn more`

### Optimize
*Fix what's broken. Keep what works.*
CRM audits, workflow cleanup, reports and dashboards, admin support, and ongoing optimization. Make the system you already have do what it was supposed to do.
`→ Learn more`

**Visual:**
- Three cards, equal width, clean layout
- Each card links to the Services page (anchor to that section)
- Headlines in Newsreader, body in Inter
- Primary brand color accents

---

## Section 7 · Platforms & Expertise

**Purpose:** Technical specificity — decision-makers filter vendors by tech stack compatibility.

**Contents:**

### Salesforce
Sales Cloud · Service Cloud · Marketing Cloud Growth · Marketing Cloud Account Engagement · Financial Services Cloud · Health Cloud · Automotive Cloud *(beta partner)*

### HubSpot
Sales Hub · Marketing Hub · Content Hub · Service Hub

### Migrations from
Zoho · Marketo · Eloqua · NetSuite · Pipedrive · and others

### Integrations & tools
Zapier · Make.com · Clay · Conga · Customer.io · RingCentral · QuickBooks · ZoomInfo · Apollo · Gong · and others

**Visual:**
- Grid of pill-shaped tags, grouped by category header
- Subtle styling — this is information-dense, so let whitespace do the work
- Small "Salesforce Partner" badge and "Automotive Cloud Beta" callout if available

---

## Section 8 · Proof / Project Highlights

**Purpose:** Concrete, numbered outcomes. Prove the "100+ projects" claim with specifics.

**Contents:**
Three short project highlights — single sentence each — describing real work Soloex has done. To be drafted together with Derek using actual client projects (see `04-pre-launch-checklist.md`).

Example format (placeholder):

> **Healthcare migration, Australia.** *Migrated a women's health company from Salesforce to HubSpot in 6 weeks, preserving all historical patient interaction data.*
>
> **University CRM rebuild, UK.** *Rebuilt a fragmented student lifecycle CRM into a unified Sales Cloud and Marketing Cloud Account Engagement instance, reducing admissions response time by 40%.*
>
> **Tech startup stack consolidation, Washington.** *Consolidated 6 disconnected tools into a single HubSpot instance with Zapier-driven integrations. Eliminated 4 recurring software costs.*

**Visual:**
- Stacked or three-column card layout
- No logos here (they're in Section 4)
- Small project tag at top (e.g., "Migration" / "Implementation" / "Optimization")
- Crisp numeric outcome where possible

---

## Section 9 · Testimonials

**Purpose:** Voice of the client. Credibility in their words.

**Contents:**
Three 5-star Upwork testimonials. Full quotes and shortened versions are in `03-copy-and-content-bank.md`.

**Featured testimonial (largest):**
> *"His knowledge of the Salesforce Platform outperformed that of a hired agency recommended by Salesforce. If you need an innovator to get the most out of the Salesforce environment, Derek is my first choice."*
>
> ★★★★★ · Upwork

**Two supporting testimonials below or beside it** — see copy bank for full text.

**Visual:**
- Featured testimonial larger/centered
- Two supporting testimonials in a row below
- Each shows: quote, stars, "Upwork" source, any trait pills (Solution Oriented, Clear Communicator, etc.)
- Serif for pull-quote feel (Newsreader)
- Reviewer names added pre-launch if permission granted

---

## Section 10 · Meet the Team

**Purpose:** Humanize the brand. Decision-makers buy people.

**Contents:**
- **Derek Beitz** — headshot, short bio, LinkedIn icon
- **Kristin Beitz** — headshot, short bio, (LinkedIn if she has one)
- Caption framing: *"Husband-and-wife team. Women-owned. Built on trust."*
- Link to About page for full story

**Visual:**
- Two photos side by side, equal weight
- Photos should be similar in style (natural light, outdoor or clean background)
- Small LinkedIn icon under each if applicable
- Brief role description: *Founder & Technical Lead* / *Co-founder & Operations*

---

## Section 11 · Process Preview

**Purpose:** Reassure that engagement is structured and predictable.

**Contents:**
Condensed 6-step flow with numbers and titles only (body text lives on the Process page):

1. **Kickoff call** — free, 30 min, no pressure
2. **Discovery call** — focused working session
3. **Scope & plan** — technical document with pricing
4. **Build** — milestone or retainer model
5. **Go live** — your team, trained and in control
6. **Ongoing support** — available when you need us

`→ See the full process`

**Visual:**
- Horizontal timeline on desktop, vertical stack on mobile
- Numbered steps with short titles
- Link to full Process page at the bottom

---

## Section 12 · Final CTA Block

**Purpose:** Last chance to convert before the footer. Full-width, high-contrast, one clear action.

**Contents:**
- **Headline:** *"Ready to fix your CRM? Let's talk."*
- **Subheadline:** *"Free 30-minute call. No pitch. Just your CRM, our questions, and a clear next step."*
- **CTA button:** `Fix my CRM →` — large, prominent
- Optional supporting text: *"Mechanicsburg, PA · Working with clients across North America and internationally."*

**Visual:**
- Full-width section, possibly with a dark navy background (`#051A2B`) and light text for visual contrast against the white sections above
- OR stay light with a strong border/frame — TBD at build time
- Centered content
- Large, bold CTA button

---

## Section 13 · Footer

**Purpose:** Navigation, contact, legal, trust signals.

**Contents:** See full spec in `01-creative-brief.md` Section 11.

Four columns:
1. Soloex (logo, tagline, 1-line description)
2. Services (Implement, Migrate, Optimize)
3. Company (About, Process, Contact)
4. Get in Touch (email, phone, location, social icons)

Bottom bar:
- Copyright
- Privacy Policy · Terms of Service
- WBENC badge · Salesforce Partner badge
- (HubSpot badge and AppExchange link when available)

---

## Visual rhythm across sections

To keep the page from feeling monotonous, alternate visual density:

| Section | Visual density |
|---|---|
| 1 Hero | Light, airy — hero breathes |
| 2 Stats strip | Dense numbers |
| 3 Upwork bar | Compact, minimal |
| 4 Logo carousel | Motion + variety |
| 5 Problem | Three-card visual grid |
| 6 Services | Three-card visual grid |
| 7 Platforms | Dense tag grid |
| 8 Proof | Text-focused |
| 9 Testimonials | Pull-quote editorial feel |
| 10 Team | Image-forward |
| 11 Process | Timeline structure |
| 12 Final CTA | Full-width break |
| 13 Footer | Utilitarian |

The pattern alternates: light → dense → compact → motion → cards → cards → dense → text → editorial → image → structure → break → footer. This keeps the scroll feeling varied without being chaotic.
