# Handover & Architectural Guide for AI Coding Agents

> **Project:** House of Recovery Landing Page
> **Target Audience:** Future AI coding agents tasked with implementing the Next.js 15 React application.
> **Objective:** Transition the static prototype (`House of Recovery.html`) into a production-ready, high-performance Next.js 15 site.

---

## 1. Executive Summary & Brand Positioning

House of Recovery is a clinical, results-driven wellness sanctuary in Worksop, UK. It is **not** a generic high-street spa. The design language, copy, and tone must be editorial, disciplined, and slightly austere (reminiscent of a high-end Japanese ryokan combined with a sports science clinic).

### Voice & Copy Rules
*   **Tone**: Short, declarative, authoritative. Short fragments are acceptable.
*   **Allowed Terms**: *discipline, protocol, reset, resilience, supramaximal, vascular, lymphatic, customised, prescribed, restorative, recover, vitality.*
*   **Prohibited Terms**: *pamper, treat yourself, me-time, indulge, beauty break, glow-up, self-care Sunday, oasis, sanctuary-of-bliss.*
*   **Spelling**: Always use **British English** (e.g., *programme, customised, optimisation, centre, colour, favourite*).
*   **Testimonial Annotations**: All sample testimonials must be preceded by the HTML comment: `<!-- SAMPLE COPY — replace before launch -->`.

---

## 2. Design System & Styling (Tailwind Configuration)

You must port the styling system directly from `House of Recovery.html` into the Next.js Tailwind configuration (`tailwind.config.ts`).

### 2.1 Core Palette Tokens
Define these exact brand hex values in the Tailwind config theme:

```typescript
const colors = {
  cream:       '#F3F2ED', // Primary light surface, main page background
  'cream-dark': '#E5E2D9', // Secondary light surface, alternating sections
  taupe:       '#9d948b', // Brand-signature warm grey, mid accent
  'taupe-light':'#CFC5BB', // Light accents on dark surfaces, soft dividers
  'taupe-dark': '#7d756e', // Body text on light surfaces, low-contrast borders
  'earth-dark': '#3E3832', // Primary dark surface, deep section background
  charcoal:    '#2C2C2C', // Headline text, deepest neutral
  ice:         '#A8B8BE', // Accent - cold/plunge moments only (never brand/nav)
  ember:       '#B8916A', // Accent - infrared/sauna moments only (never brand/nav)
}
```

### 2.2 Typography
*   **Headlines & Display**: Google Font **`Playfair Display`** (weights: 400, 500, 600, italic).
*   **UI & Body**: Google Font **`Lato`** (weights: 300 for body, 400 for UI defaults, 700 for small caps / CTAs).
*   **Scale Specification**:
    *   `h1`: 56px (mobile) / 96px (desktop), Playfair, line-height `0.95`, italic on accent words.
    *   `h2`: 36px (mobile) / 56px (desktop), Playfair, line-height `1.05`.
    *   `h3`: 24px (mobile) / 32px (desktop), Playfair.
    *   `body`: 16px (mobile) / 17px (desktop), Lato 300, line-height `1.7`.
    *   `eyebrow / UI caps`: 10px (mobile) / 11px (desktop), Lato 700, tracking `0.25em`, uppercase.

### 2.3 Animations & Keyframes
Port the following custom keyframe animations into `tailwind.config.ts`:
*   `fade-in-up`: Opacity 0 & translate-y (24px) to opacity 1 & translate-y (0).
*   `fade-in`: Opacity 0 to opacity 1.
*   `pulse-slow`: Subtle opacity pulsation (used for background blobs).

---

## 3. Image Assets & Media Rules

All raster imagery must be generated via Imagen-3 (or successor) using the style spine below. Drop generated images in `public/images/`.

### 3.1 Style Spine (Include in all prompt runs)
> *"Soft, naturally-lit editorial photograph. Warm, restrained palette — cream, taupe, deep brown, charcoal. Matte finish, slight grain. Architectural and clinical, not pampering. No emojis, no text overlays, no flowers, no candles, no pebbles, no lotus shapes, no overt 'spa' imagery, no fluorescent lighting, no oversaturated colours, no AI-glossy skin. British minimalism crossed with Japanese ryokan."*

### 3.2 Visual Asset List
*   **Hero (`public/images/hero.jpg`)**: Wide-angle interior of a minimalist recovery sanctuary at dawn. Concrete floor, warm linen treatment chair, single light shaft, 16:9 ratio.
*   **Body Ballancer (`public/images/discipline-ballancer.jpg`)**: Champagne-coloured compression suit folded on linen bench. Afternoon light, 4:5 ratio.
*   **Dermalogica (`public/images/discipline-dermalogica.jpg`)**: Overhead flat-lay of unbranded amber glass dropper, ceramic bowl with clear gel, white linen cloth, 1:1 ratio.
*   **Contrast & Sauna (`public/images/discipline-contrast.jpg`)**: Split composition: left half cold plunge with glacial-blue mist (`#A8B8BE`); right half warm infrared sauna with amber light (`#B8916A`). 16:9 ratio.
*   **Tesla Chair (`public/images/discipline-tesla.jpg`)**: Matte-charcoal HIFEM medical chair in clean light-grey room, three-quarter view, 4:5 ratio.
*   **Ambient Textures (`public/images/texture-1.jpg`, `texture-2.jpg`, `texture-3.jpg`)**: Trowel-marked off-white stucco (1), warm cream linen weave (2), warm travertine marble with veins (3). 1:1 ratio.
*   **Testimonials (`public/images/testimonial-1.jpg` to `-5.jpg`)**: Editorial portraits of varied demographic clients, head-and-shoulders, soft cream background, natural light, 1:1 ratio.

---

## 4. Brand Logos & Usage Guidelines

Logos are located under `public/logo/` (port directory structure from `assets/logo`).

*   **Default Sticky Header (Light Background)**: Black wordmark (`black/full/black_logo_transparent_background.png`).
*   **Dark Sections / Over Dark Hero**: White wordmark (`black/full/white_logo_transparent_background.png`).
*   **Favicon**: Icon-only mark (`black/icon/black_icon_transparent_background.png`).

---

## 5. Canonical Services & Pricing Data (Locked)

Do not paraphrase, round, or alter the price table variables or descriptions below.

### 5.1 Body Ballancer™ (Compression Lymphatic Drainage)
*   **Description**: Rhythmic compression therapy mimicking manual lymphatic drainage to reduce fluid retention, puffiness, cellulite, and flush lactic acid.
*   **Mechanism**: A computer-controlled suit inflates/deflates air chambers to push waste fluid to lymph nodes.
*   **Who it's for**: Bloating, heavy legs, post-training recovery, lymphatic congestion, smoothing cellulite.
*   **Pricing**:
    *   `Body Ballancer Full Body` | 45 min | **£50.00**
    *   `Body Ballancer Course of 5 (Full Body)` | 5 × 45 min | **£200.00** *(saves £50 vs single)*
    *   `Body Ballancer Lower Body` | 45 min | **£30.00**
    *   `Body Ballancer Upper Body` | 45 min | **£30.00**

### 5.2 Dermalogica Skin Health
*   **Description**: Clinical, prescribed facials using professional-grade Dermalogica products and Face Mapping® diagnosis. Skincare is health, not luxury.
*   **Mechanism**: Face Mapping® diagnosis followed by customised protocols for congestion, dehydration, or ageing.
*   **Who it's for**: Clinical, structural skin transformation.
*   **Pricing**:
    *   `Dermalogica ProSkin 30 Facial` | 45 min | **£35.00**
    *   `Dermalogica ProSkin 60 Facial` | 1 h 10 min | **£60.00**
    *   `Dèsse Pro LED Face Mask (add-on)` | 10 min | **£5.00** *(add-on to any facial or Body Ballancer)*

### 5.3 Contrast & Infrared Therapy
*   **Description**: Visceral temperature exposure. Infrared saunas detoxify; ice plunges trigger vasoconstriction and dopamine.
*   **Mechanism**: Infrared heat at 45–60 °C; Ice plunge at ≈3–10 °C for sympathetic response.
*   **Who it's for**: Athletes, high-performers, dopamine reset.
*   **Pricing**:
    *   `Ice Plunge` | 10 min | **£5.00**
    *   `Infrared Sauna — 1 Person` | 30 min | **£15.00**
    *   `Infrared Sauna — 2 Persons` | 30 min | **£25.00**

### 5.4 Tesla Pelvic Floor Chair (HIFEM)
*   **Description**: Fully clothed electromagnetic stimulation delivering ~11,000 supramaximal contractions.
*   **Mechanism**: High-Intensity Focused Electromagnetic (HIFEM) energy induces rapid muscular adaptation (equivalent to 11,000 Kegels).
*   **Who it's for**: Postpartum recovery, stress/urge incontinence, core stability, pelvic-floor weakness.
*   **Pricing**:
    *   `Tesla Pelvic Floor Chair` | 45 min | **£70.00**
    *   `Tesla Pelvic Floor Chair Course of 4` | 4 × 30 min | **£250.00** *(saves £30 vs four singles)*

---

## 6. Information Architecture & Page Flow

All elements reside on a single vertical scroll page (`app/page.tsx`).

1.  **Section 1: Hero**
    *   Full-viewport, ambient video (`<=1MB`, muted, loop, `playsinline`) or image.
    *   Eyebrow: `RESTORATION · RESILIENCE · RESULTS`
    *   H1: *Restoring Vitality*
    *   CTAs: **Book a Session** (SumUp URL) & **Explore the Disciplines** (anchor link to Section 3).
2.  **Section 2: Philosophy**
    *   Dark background (`earth-dark`) with cream text.
    *   Headline: *Skincare is health. Recovery is discipline.*
    *   Two paragraphs on the clinical-not-spa approach.
3.  **Section 3: The Four Disciplines**
    *   Four sub-sections matching Section 5.
    *   All options and prices must be fully visible. **No "Read More" overlays hiding pricing.**
    *   SumUp Book CTA under each discipline section.
4.  **Section 4: Testimonials / Monograms**
    *   3–5 testimonials (use sample templates from `House of Recovery.html` or Section 12.6 of the brief).
    *   Monogram avatars (e.g., "A", "J", "S").
5.  **Section 5: Visit & Contact (Verbatim Details)**
    *   Address: `86 High Hoe Rd, Worksop, S80 2DS, United Kingdom`
    *   Opening hours:
        *   Mon: Closed
        *   Tue: 11:00 – 19:00
        *   Wed: 12:00 – 19:00
        *   Thu: 10:00 – 16:00
        *   Fri: 10:00 – 15:00
        *   Sat: 09:00 – 13:00
        *   Sun: Closed
    *   Contact Info: Placeholders `[PHONE]`, `[EMAIL]`, `[INSTAGRAM URL]`, `[FACEBOOK URL]` must be kept visibly in source/page if not supplied yet.
6.  **Section 6: Footer**
    *   Icon logo, address, hours, booking CTA, social links (Instagram/Facebook using Lucide icon weights of `1.5px`), and dynamic year copyright. Small-print links (Privacy, Terms, Accessibility) using `#` anchors.

---

## 7. Motion & Interaction Specifications

Ensure your motion patterns match these guidelines:

### 7.1 Framework Boundaries
*   **Framer Motion (`motion`)**: Default for reveals, component entries, hover/active states, and UI transitions.
*   **GSAP / ScrollTrigger**: Reserved **only** for pinned scrollytelling timelines (e.g., vertical pinning of structural cards on scroll). Do not use if Framer Motion can handle the animation.
*   **Lenis**: Setup a global layout smooth-scroll provider.

### 7.2 Accessibility & Mobile Rules
*   **`prefers-reduced-motion` Support**:
    ```typescript
    import { useReducedMotion } from 'framer-motion';
    const shouldReduceMotion = useReducedMotion();
    // If true: disable parallax/marquees, set transition duration to <=120ms, bypass Lenis.
    ```
*   **Touch Devices**: Ensure price lists and booking buttons do not require hover states to be interactive or visible. All buttons must have tap targets of at least `44x44` px.
*   **Performance**: Hero LCP must be `<2.5s` on 4G. Lazy load images below the fold.

---

## 8. Development Steps for the Next Agent

When executing the build:
1.  **Run bootstrap script**: `npx -y create-next-app@latest ./ --typescript --tailwind --app --src-dir --import-alias "@/*" --eslint`
2.  **Configure Tailwind**: Map the color hex values and font weights. Set up standard keyframes.
3.  **Setup Lenis Scroll Provider**: Create a client component `components/lenis-provider.tsx` to wrap the app root layout.
4.  **Componentize sections**: Split the page into structured files (`components/hero.tsx`, `components/philosophy.tsx`, etc.).
5.  **Inject data module**: Create `lib/services.ts` containing the service schemas. Do not write local variables inside components.
6.  **Verify WCAG Contrast**: Run tests ensuring dark neutral text on light surfaces matches contrast AA constraints.
