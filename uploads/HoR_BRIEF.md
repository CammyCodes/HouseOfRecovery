# House of Recovery — Design & Build Brief

> **Audience for this document:** a design/engineering agent producing the new House of Recovery landing page.
> **Status of source-of-truth values (prices, copy, address, hours, palette tokens, stack):** locked. Do not paraphrase, round, or substitute.

---

## 1. TL;DR

House of Recovery is a small, clinical, results-driven wellness sanctuary in Worksop, UK. It offers four recovery & skin-health disciplines: Body Ballancer™ lymphatic compression, Dermalogica skin treatments, Contrast & Infrared Therapy (ice plunge + infrared sauna), and the Tesla HIFEM Pelvic Floor Chair.

Build a **single, sleek, modern landing page** that reads like a confident clinical sanctuary — not a generic high-street spa. Tone is editorial, disciplined, slightly austere. The page must surface every service and every price clearly, with smooth motion on both desktop and mobile, and route bookings out to the external SumUp link.

Stack is Next.js 15 (App Router) + React 19 + Tailwind + `motion` + GSAP/ScrollTrigger + Lenis. Output is a deployable repo, pushed to GitHub.

---

## 2. Project context

- **Deliverable:** one scrollable landing page (`app/page.tsx`) plus the supporting layout, config, and assets needed to deploy to Vercel or any Next.js host.
- **Repo target:** new Next.js 15 project, intended to be pushed directly to GitHub. Do **not** continue the existing `/new` Vite project — that was an exploratory React playground and is being retired.
- **The four `Concept*.tsx` files in `/new/components/`** were exploratory variants (Editorial Wellness, Spatial Action, Liquid Architecture, Immersive Sensory). They are **not templates to copy**; treat them only as evidence of the brand voice.
- **Booking is external.** All booking CTAs link out to SumUp (URL in §12). No in-page booking form, no calendar embed.
- **No CMS.** All content lives in TypeScript modules (e.g. `lib/services.ts`).

---

## 3. Brand & positioning

### Who walks through the door
- High performers and athletes needing measurable physiological recovery.
- Postpartum mothers and adults addressing pelvic floor weakness or incontinence.
- Skin-health seekers who want clinical, prescribed treatment rather than a "facial that smells nice."
- Anyone seeking deliberate, structured recovery — not a pamper day.

### The wedge
House of Recovery is *not a spa*. The site must read as clinical, technical, and quietly luxurious — closer to a high-end physiotherapy clinic crossed with a Japanese ryokan than to a hotel spa.

### Voice rules
- **Use:** discipline, protocol, reset, resilience, supramaximal, vascular, lymphatic, customised, prescribed, restorative, recover, vitality.
- **Avoid:** pamper, treat yourself, me-time, indulge, beauty break, glow-up, self-care Sunday, oasis, sanctuary-of-bliss.
- **Spelling:** British English throughout (programme, customised, optimisation, centre, colour, favourite).
- **Sentence shape:** short, declarative, occasionally fragmentary. Authority without bombast.

### Canonical taglines (use verbatim or as inspiration)
- *"Restoring Vitality."* — hero headline candidate
- *"Skincare is health. Recovery is discipline."* — philosophy block
- *"We build resilience. You build life."* — secondary editorial line
- *"Restoration · Resilience · Results"* — kicker/eyebrow line

---

## 4. Visual identity

### Core palette — locked

| Token | Hex | Intended use |
|---|---|---|
| `cream` | `#F3F2ED` | Primary light surface, page background |
| `cream-dark` | `#E5E2D9` | Secondary light surface, alternating sections |
| `taupe` | `#9d948b` | Brand-signature warm grey, mid accent |
| `taupe-light` | `#CFC5BB` | Light accents on dark surfaces, soft dividers |
| `taupe-dark` | `#7d756e` | Body text on light, low-contrast borders |
| `earth-dark` | `#3E3832` | Primary dark surface, deep section background |
| `charcoal` | `#2C2C2C` | Headline text, deepest neutral |

These map directly to the existing Tailwind config — see [index.html:11–25](new/index.html) for the original definitions. Reuse these token names exactly in `tailwind.config.ts`.

### Permitted accent colours (sparingly)
You may introduce **up to two** muted accent colours to differentiate the cold and hot states in the Contrast & Infrared section. Suggested:

- `ice` — a desaturated glacial blue around `#A8B8BE` (cold/plunge moments only).
- `ember` — a warm dusty amber around `#B8916A` (infrared/sauna moments only).

Rules: never as primary brand colours, never on CTAs, never in nav, never tinting the logo. They are scene colours, not brand colours.

### Typography
- **Display / headlines:** Playfair Display — weights 400, 500, 600; italic permitted for emphasis.
- **UI / body:** Lato — weights 300 (body), 400 (UI default), 700 (small caps and CTAs).
- Load both via `next/font/google` with `display: 'swap'` and only the weights listed.
- **Type scale (mobile / desktop, suggested):**
  - H1: 56 / 96 px, Playfair, line-height 0.95
  - H2: 36 / 56 px, Playfair, line-height 1.05
  - H3: 24 / 32 px, Playfair
  - Body: 16 / 17 px, Lato 300, line-height 1.7
  - Eyebrow / UI caps: 10 / 11 px, Lato 700, tracking 0.25em, uppercase

### Logo
All variants are at [new/assets/logo/](new/assets/logo). Copy the directory into the new repo at `public/logo/`. Lockups available: **full** (mark + wordmark), **icon** (mark only), **text** (wordmark only). Colourways: `base`, `black`, `color1`, `customcolor`.

Usage rules:
- Default top-left navigation: black wordmark on cream (`black/full/black_logo_transparent_background.png`).
- Over dark hero or dark sections: white wordmark (`black/full/white_logo_transparent_background.png`).
- Sticky / scrolled nav on light background: black wordmark, full lockup.
- Favicon: `black/icon/black_icon_transparent_background.png` (export to `favicon.ico` + `icon.png`).

---

## 5. Services & pricing — LOCKED CANONICAL DATA

> Prices, durations, and service names are not to be re-worded, rounded, abbreviated, or "tidied." Surface them exactly as below. Currency symbol is £ (pound sterling).

### 5.1 Body Ballancer™ — Compression Lymphatic Drainage

**One-line summary:** Rhythmic compression therapy that mimics manual lymphatic drainage to reduce fluid retention, puffiness, and the appearance of cellulite. Also excellent post-exercise for flushing lactic acid.

**The mechanism:** A computer-controlled suit inflates and deflates air chambers in a rhythmic wave, pushing waste fluid toward the lymph nodes for expulsion.

**Who it's for:** Bloating, "heavy legs", post-training recovery, lymphatic congestion, smoothing the appearance of cellulite.

| Session | Duration | Price |
|---|---|---|
| Body Ballancer Full Body | 45 min | **£50.00** |
| Body Ballancer Course of 5 (Full Body) | 5 × 45 min | **£200.00** *(saves £50 vs single)* |
| Body Ballancer Lower Body | 45 min | **£30.00** |
| Body Ballancer Upper Body | 45 min | **£30.00** |

---

### 5.2 Dermalogica Skin Health

**One-line summary:** Clinical, prescribed facials using professional-grade Dermalogica products and Face Mapping® diagnosis. Founded on the belief that skincare is health, not luxury.

**The mechanism:** Face Mapping® diagnosis followed by a customised protocol addressing congestion, dehydration, or premature ageing. Therapists also prescribe a home-care regimen.

**Who it's for:** Anyone seeking clinical, structural skin transformation rather than a relaxation-led facial.

| Session | Duration | Price |
|---|---|---|
| Dermalogica ProSkin 30 Facial | 45 min | **£35.00** |
| Dermalogica ProSkin 60 Facial | 1 h 10 min | **£60.00** |
| Dèsse Pro LED Face Mask (add-on) | 10 min | **£5.00** *(add-on to any facial or Body Ballancer)* |

---

### 5.3 Contrast & Infrared Therapy

**One-line summary:** A visceral reset through deliberate temperature exposure. Infrared sauna detoxifies from the inside; the ice plunge triggers vasoconstriction and a metabolic dopamine spike.

**The mechanism:** Infrared panels heat tissue directly at 45–65 °C, penetrating deeper than conventional saunas. The ice plunge (≈3–10 °C) triggers intense vasoconstriction and a sympathetic-nervous-system response.

**Who it's for:** Athletes seeking recovery; high-performers wanting a mental-resilience protocol; anyone needing a deep detox or dopamine reset.

| Session | Duration | Price |
|---|---|---|
| Ice Plunge | 10 min | **£5.00** |
| Infrared Sauna — 1 Person | 30 min | **£15.00** |
| Infrared Sauna — 2 Persons | 30 min | **£25.00** |

---

### 5.4 Tesla Pelvic Floor Chair (HIFEM)

**One-line summary:** Non-invasive electromagnetic stimulation that delivers approximately 11,000 supramaximal pelvic-floor contractions per session, fully clothed.

**The mechanism:** High-Intensity Focused Electromagnetic (HIFEM) energy stimulates thousands of supramaximal contractions in a single session — equivalent to about 11,000 Kegels — forcing rapid muscular adaptation.

**Who it's for:** Postpartum recovery, stress and urge incontinence (men and women), pelvic-floor weakness, core stability, sexual-health support.

| Session | Duration | Price |
|---|---|---|
| Tesla Pelvic Floor Chair | 45 min | **£70.00** |
| Tesla Pelvic Floor Chair Course of 4 | 4 × 30 min | **£250.00** *(saves £30 vs four singles)* |

---

## 6. Information architecture

The page is a single, vertical scroll experience. Sections appear in this order:

### Section 1 — Hero (required)
- Full-viewport. Background image OR a subtle ambient video (≤6 s loop, ≤1 MB, muted, `playsinline`).
- Eyebrow: `RESTORATION · RESILIENCE · RESULTS`
- Headline: *Restoring Vitality* (Playfair, italic on "Vitality")
- Sub: one sentence naming the four pillars by name.
- Primary CTA: **Book a Session** (links to SumUp).
- Secondary CTA: **Explore the Disciplines** (anchors to §3).

### Section 2 — Philosophy (required)
- Editorial block, single column, ~720 px max width on desktop.
- Lead with the *"Skincare is health. Recovery is discipline."* line.
- Two short paragraphs articulating the clinical-not-pampering wedge.
- Background: dark surface (`earth-dark`) with cream text, or a strong cream block with an adjacent atmospheric image.

### Section 3 — The Four Disciplines (required, this is the hero of the content)
- Each of the four services is its own visually distinct sub-section.
- All variations, durations, and prices from §5 must be visible without click-through. **No "view more" hiding the price list.** A modal or expanding panel for *additional* detail is fine, but the price table must be on the page.
- Each service should feel like a different room, not a different card in the same grid. Possible directions:
  - Body Ballancer — soft, rhythmic, flow-based.
  - Dermalogica — clinical, white-light, precise.
  - Contrast & Infrared — split-screen hot/cold, where the `ice` and `ember` accent colours appear.
  - Tesla Chair — electric, geometric, precise.
- Each ends with the SumUp **Book** CTA scoped to that discipline (the link is the same URL — no per-service deep links exist).

### Section 4 — Testimonials / social proof (required)
- 3 to 5 short testimonials, ~30–60 words each.
- **Agent may write plausible sample copy** for now. Mark every sample testimonial with an HTML comment immediately above it: `<!-- SAMPLE COPY — replace before launch -->`.
- Treatments mentioned in samples must come from §5 (no fictional services).
- Optional but encouraged: small monogram-style author avatars (Gemini-generated, see §9).

### Section 5 — Visit & Contact (required)
Real data, locked:

- **Address:** 86 High Hoe Rd, Worksop, S80 2DS, United Kingdom
- **Opening hours:**

  | Day | Hours |
  |---|---|
  | Monday | Closed |
  | Tuesday | 11:00 – 19:00 |
  | Wednesday | 12:00 – 19:00 |
  | Thursday | 10:00 – 16:00 |
  | Friday | 10:00 – 15:00 |
  | Saturday | 09:00 – 13:00 |
  | Sunday | Closed |

- **Map:** embed a static styled map image (warm/muted palette to match brand — not the default Google Maps colours). If using `next/image`, store at `public/map/worksop.png`. No live Google embed unless the host has a Maps API key configured.
- **Socials:** placeholder `[INSTAGRAM URL]` and `[FACEBOOK URL]` tokens — leave as visible TODOs; do not invent handles.
- **Phone / email:** placeholder `[PHONE]` and `[EMAIL]` tokens. Same TODO treatment.

### Section 6 — Footer (required)
- Logo (icon lockup).
- Compact repeat of address + hours.
- SumUp **Book a Session** CTA.
- Social icons (Lucide `Instagram`, `Facebook` line icons — `aria-label`s required).
- Year (`new Date().getFullYear()`) + "House of Recovery. All rights reserved."
- Small print row: placeholder links for Privacy, Terms, Accessibility (each anchored to `#` for now, with a visible `TODO` annotation in source).

### Optional content the agent may incorporate but is NOT required
- **Wellness Concierge AI** (Gemini-powered service recommender) — full prompt/spec exists at [new/services/geminiService.ts](new/services/geminiService.ts) and a working component at [new/components/ConciergeAI.tsx](new/components/ConciergeAI.tsx). Include only if it adds to the experience; if so, it sits between §3 and §4.
- **Weekly schedule grid** — example data at [new/components/Schedule.tsx](new/components/Schedule.tsx). Skip unless you can present it without making the page feel cluttered. The SumUp link is the canonical booking surface.

---

## 7. Motion & interaction principles

### Library responsibilities
- **`motion`** (Framer Motion v11+) — almost everything: component reveals, hover states, layout animations, modal transitions. Default choice.
- **`gsap` + `ScrollTrigger` + `@gsap/react`** — reserved for *pinned scrollytelling* moments only (e.g. a pinned hero that morphs through the four disciplines, or a horizontal-scroll pricing reveal). Do not reach for GSAP when `motion` will do the job.
- **`lenis`** — site-wide smooth scroll. Initialise in the root layout. Respect `prefers-reduced-motion` by disabling smooth scroll for users who request it.

### Motion rules
- **Reveals are scroll-driven, not auto-looping.** Use `whileInView` (motion) or ScrollTrigger.
- **Animate only `transform` and `opacity`.** No animating `width`, `height`, `top`, `left`, `box-shadow`, or `filter`-on-large-areas. Use `will-change` only on actively animating elements and remove it after.
- **Reduced motion is a first-class path.** Wrap motion configs in a `useReducedMotion()` check. With reduced motion: kill parallax, kill marquees, disable Lenis smooth scroll, shorten transitions to ≤120 ms, keep state changes but not the trip.
- **Touch parity.** Every effect that depends on `:hover` must have a tap-friendly equivalent. The price tables and CTAs must be reachable without ever needing to hover.
- **Loading states.** No layout-shifting skeletons; reserve space with aspect-ratio boxes for every image.
- **Easing default:** `cubic-bezier(0.22, 1, 0.36, 1)` (out-expo flavour). Durations: micro 120 ms, standard 280 ms, expressive 600 ms, pinned moments 800–1200 ms.

### Mobile-first specifics
- Hero headline must not exceed 2 lines on a 375 px viewport. Confirm with the longest tagline option.
- No horizontal-scroll-only patterns on mobile — pair with a vertical fallback or pagination.
- Tap targets ≥ 44×44 px.
- All scroll-pinned sections (if used) must be tested under iOS Safari's address-bar resize.

### Performance budget
- Hero LCP < 2.5 s on a mid-range Android (Moto G-class) on 4G.
- Total JS shipped to the homepage (gzipped) < 250 KB before code-splitting kicks in beyond the fold.
- Use `next/image` for every raster image with sensible `sizes`. Hero image priority `true`; everything below the fold lazy.
- Preload only the hero image and the two display font weights actually used above the fold.

### Accessibility checklist
- Colour contrast: every text/background pair meets WCAG AA. Body text on cream (`#F3F2ED`) must use `charcoal` or `earth-dark`, not `taupe`.
- All interactive elements have visible focus rings (use `taupe` outline at 2 px offset).
- Skip-link at top, hidden until focused.
- Section headings form a valid hierarchy (single `h1` in hero; `h2` per section).
- Booking CTA has descriptive accessible name (`Book a session at House of Recovery (opens external booking site)`).

---

## 8. Tech stack — use exactly this

- **Framework:** Next.js 15 (App Router) + React 19 + TypeScript (strict).
- **Styling:** Tailwind CSS. Reuse the existing colour tokens by name (see §4). Ship `tailwind.config.ts` mirroring the original [index.html:11–25](new/index.html) Tailwind config, ported faithfully (including the existing keyframes: `fade-in-up`, `fade-in`, `pulse-slow`).
- **Animation:**
  - `motion` (Framer Motion v11+)
  - `gsap`, `@gsap/react`, GSAP `ScrollTrigger`
  - `lenis`
- **Icons:** `lucide-react` (line icons only, weight 1.5px, size 18–24 px in UI).
- **Type loading:** `next/font/google` for Playfair Display + Lato. Self-host via Next's font pipeline; don't link Google Fonts CDN at runtime.
- **Class composition:** `clsx` + `tailwind-merge` (wrap as a `cn(...)` helper in `lib/utils.ts`).
- **No additional UI libraries.** No shadcn, no Radix unless strictly needed for a single primitive (e.g. a dialog) — if so, isolate it.
- **No state library.** React `useState`/`useReducer` is sufficient for this page.

Project structure suggestion (not prescriptive beyond `app/page.tsx`):

```
app/
  layout.tsx
  page.tsx
  globals.css
components/
  hero.tsx
  philosophy.tsx
  disciplines/
    body-ballancer.tsx
    dermalogica.tsx
    contrast.tsx
    tesla-chair.tsx
  testimonials.tsx
  visit.tsx
  footer.tsx
  ui/
    cta-button.tsx
    section-eyebrow.tsx
lib/
  services.ts        // canonical data port of /new/data/services.ts
  utils.ts           // cn() helper
  smooth-scroll.tsx  // Lenis provider
public/
  logo/              // copied from /new/assets/logo
  images/            // Gemini-generated outputs
tailwind.config.ts
```

---

## 9. Imagery — Gemini prompt library

All hero and ambient imagery is generated via Gemini (Imagen-3 or successor). Drop the outputs into `public/images/` with the suggested filenames.

> **Common style spine for every prompt** (prepend or include): *"Soft, naturally-lit editorial photograph. Warm, restrained palette — cream, taupe, deep brown, charcoal. Matte finish, slight grain. Architectural and clinical, not pampering. No emojis, no text overlays, no flowers, no candles, no pebbles, no lotus shapes, no overt 'spa' imagery, no fluorescent lighting, no oversaturated colours, no AI-glossy skin. British minimalism crossed with Japanese ryokan."*

### 9.1 Hero — `public/images/hero.jpg`
> A wide-angle interior of a calm, minimalist recovery sanctuary at dawn. Polished concrete floor, warm linen drape across a treatment chair, a single shaft of soft window light falling across a marble plinth. Earthy palette — cream walls, taupe drapery, deep brown wood. Camera at eye level, 35 mm lens, shallow depth of field. No people. 16:9 ratio. Editorial, quiet, expensive.

### 9.2 Body Ballancer — `public/images/discipline-ballancer.jpg`
> Close-up detail of a champagne-coloured compression therapy suit folded neatly on a linen-covered bench in a softly lit treatment room. Visible texture of the technical fabric, subtle quilted air chambers. Warm afternoon light from a high window. Taupe and cream tones. No people, no faces. 4:5 portrait ratio. Clinical but inviting.

### 9.3 Dermalogica — `public/images/discipline-dermalogica.jpg`
> Overhead flat-lay of professional-grade skincare on a cream marble surface: an unbranded amber glass dropper bottle, a single ceramic bowl with a clear gel, a folded white linen cloth, a brushed-steel facial implement. Soft directional light from upper left. No labels, no logos. 1:1 square. Editorial product still life.

### 9.4 Contrast & Infrared — `public/images/discipline-contrast.jpg`
> Split composition: left half a still ice-cold plunge pool with mist drifting across a glacial-blue surface (use desaturated `#A8B8BE`-style blue); right half the warm interior of an infrared sauna lit by amber wood panels (use warm `#B8916A`-style amber). The two halves meet on a vertical seam at centre. No people. 16:9. Cinematic, almost-symmetrical.

### 9.5 Tesla Chair — `public/images/discipline-tesla.jpg`
> A modern matte-charcoal medical-grade chair in a clean, light-grey treatment room, photographed three-quarters from the front. Subtle ambient lighting, soft shadows, no clutter, no people. The chair feels engineered, not clinical-cold. 4:5 portrait. Editorial industrial-design feel.

### 9.6 Ambient textures (for section dividers) — `public/images/texture-{1,2,3}.jpg`
> 1) Macro of off-white stucco wall with raking light, showing trowel marks. Cream/taupe only.
> 2) Macro of natural linen weave, slightly creased, warm cream.
> 3) Macro of warm-brown travertine marble with subtle veining. Earth-dark tones.

All 1:1 ratio, 1600 px square minimum.

### 9.7 Testimonial portraits — `public/images/testimonial-{1..5}.jpg`
> Editorial portrait of a [varied demographic — vary age, gender, ethnicity across the set] adult, photographed against a soft cream backdrop with warm natural window light. Subject wears neutral linen or knitwear. Calm, candid expression, not smiling overtly at camera. 1:1 square crop, head and shoulders. No props. Soft film grain.

When generating the set, vary subjects deliberately so the testimonial wall reflects a real Worksop clientele (postpartum mothers, men in their 40s, athletes, professional women).

---

## 10. Constraints & non-goals

- **Do not mimic Drop Wellness.** The downloaded site at [drop_wellness/drop_wellness.html](drop_wellness/drop_wellness.html) is a *separate, sibling-local brand* (a Worksop pilates/yoga studio). Different colour territory, different motion language, no risk of brand collision. If anything, lean *away* from its choices.
- **No emoji icons.** Lucide line icons only. No emoji in markup, comments, or copy.
- **No spa stock-photo tropes.** No pebbles, lotus flowers, candles, cucumber slices, white robes on a chaise lounge, hands cupping water, or close-ups of orchids.
- **No carousel-only mobile UX.** Horizontal scroll is permitted only as a complement to a vertical layout, never as the only path to content.
- **No autoplaying audio. Ever.**
- **No fake urgency or fake scarcity.** No "only 2 spots left" badges, no countdown timers, no "trending" tags on pricing.
- **No third-party chat widgets, no popups, no exit-intent modals, no email-capture overlays.**
- **No "as featured in" press logos** unless real assets are supplied later.
- **Do not paraphrase prices, durations, or service names.** Even small drift (`£50` → `£49`, `Pro 30` → `30-min Pro`) is a regression.
- **Do not invent contact details.** Phone, email, social handles stay as bracketed TODOs until the client supplies them.

---

## 11. Acceptance checklist

The page is done when **all** of the following are true:

- [ ] Renders cleanly on iOS Safari (latest), Android Chrome, desktop Chrome, Firefox, Safari.
- [ ] Hero LCP < 2.5 s on a throttled "Slow 4G" Lighthouse run.
- [ ] All four services appear on the page with every variation, duration, and price from §5 — visible without clicking into a modal.
- [ ] Address and opening hours match §6 §5 verbatim.
- [ ] SumUp booking link in §12 is used for every Book CTA, opens in a new tab with `rel="noopener noreferrer"`.
- [ ] `prefers-reduced-motion: reduce` disables parallax, marquees, Lenis smooth scroll, and shortens transitions to ≤120 ms.
- [ ] No `:hover`-only interactions are required to reach content on touch devices.
- [ ] Colour contrast for body text on every background pair passes WCAG AA.
- [ ] All Lucide icons render with `aria-label` or visually-hidden text.
- [ ] No console warnings or errors on first load.
- [ ] No instances of disallowed words from §3 ("pamper", "indulge", "me-time", etc.).
- [ ] No emoji in source, markup, or output imagery.
- [ ] Every sample testimonial is annotated `<!-- SAMPLE COPY — replace before launch -->`.
- [ ] `[PHONE]`, `[EMAIL]`, `[INSTAGRAM URL]`, `[FACEBOOK URL]` tokens are visibly present where contact info should go — none invented.
- [ ] Logo assets are copied to `public/logo/` and referenced by the lockups specified in §4.
- [ ] `tailwind.config.ts` defines all seven core tokens by their original names.
- [ ] `README.md` in the new repo documents how to run locally, where to drop new images, and how to swap in real testimonials.

---

## 12. Appendix

### 12.1 Canonical booking URL
```
https://sumupbookings.com/house-of-recovery
```
Use this clean URL on every CTA. The version in [new/components/Services.tsx:82](new/components/Services.tsx) is an Instagram redirect wrapper — do not propagate that wrapped form.

### 12.2 Hex swatches (copy-paste)
```
cream        #F3F2ED
cream-dark   #E5E2D9
taupe        #9d948b
taupe-light  #CFC5BB
taupe-dark   #7d756e
earth-dark   #3E3832
charcoal     #2C2C2C
ice (accent) #A8B8BE
ember(accent)#B8916A
```

### 12.3 Address & hours (copy-paste)
```
House of Recovery
86 High Hoe Rd
Worksop, S80 2DS
United Kingdom

Monday      Closed
Tuesday     11:00 – 19:00
Wednesday   12:00 – 19:00
Thursday    10:00 – 16:00
Friday      10:00 – 15:00
Saturday    09:00 – 13:00
Sunday      Closed
```

### 12.4 Logo asset paths (relative to `public/logo/` once copied)
```
black/full/black_logo_transparent_background.png
black/full/white_logo_transparent_background.png
black/icon/black_icon_transparent_background.png
black/icon/white_icon_transparent_background.png
black/text/...
base/full/base_logo_transparent_background.png
color1/full/color1_logo_transparent_background.png
color1/full/white_logo_color1_background.png
```
(Full tree mirrors the existing structure at [new/assets/logo/](new/assets/logo).)

### 12.5 Source-of-truth files in the existing repo
- Pricing data: [new/data/services.ts](new/data/services.ts)
- Existing Tailwind config & keyframes: [new/index.html](new/index.html)
- Hero copy reference: [new/components/Hero.tsx](new/components/Hero.tsx)
- Existing AI concierge spec (optional, see §6): [new/services/geminiService.ts](new/services/geminiService.ts)
- Schedule grid reference data (optional, see §6): [new/components/Schedule.tsx](new/components/Schedule.tsx)

### 12.6 Sample testimonial seeds (the agent may rewrite — mark all as sample copy)
- *"After my second postpartum, the Tesla chair was the only thing that gave me my core back. I cried in the car park after my fourth session — happy crying."*
- *"I've trained for two ultras on the back of weekly Body Ballancer sessions. Recovery time on tired legs has halved. Worth every penny."*
- *"My skin was a mess of stress breakouts. Three ProSkin 60s in and people are asking what I'm doing. I'm doing this."*
- *"The ice plunge ruined every other 'cold shower' habit I'd ever built. Once you've done a proper plunge, the bathroom doesn't cut it."*
- *"They don't do the soft-music-and-cucumber-water thing here. It's clinical and it works. Exactly what I needed."*

(All sample. Replace before launch.)

---

*End of brief.*
