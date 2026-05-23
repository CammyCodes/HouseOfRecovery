# House of Recovery Landing Page

This repository contains the assets, design specifications, and a fully functional static HTML prototype for the new single-page landing page of **House of Recovery**, a clinical, results-driven wellness sanctuary in Worksop, UK.

## Project Structure

```text
├── assets/
│   └── logo/             # Brand logos (white, black, icons, and wordmarks)
├── uploads/
│   ├── HoR_BRIEF.md      # Canonical Design & Build Brief (locked content & specs)
│   └── [images]          # Source logo and icon design variations
├── House of Recovery.html # Static HTML prototype containing code & visual layout
├── agent.md              # Detailed handover guide for AI coding agents
└── readme.md             # Developer documentation (this file)
```

## Current State

The repository contains:
1.  **`House of Recovery.html`**: A fully realized static prototype built with HTML, Vanilla CSS, and custom JavaScript animations. It contains all marketing copy, service rates, opening hours, layout blocks, and interactive animation setups.
2.  **`assets/logo/`**: Pre-cropped, production-ready brand logo assets.
3.  **`uploads/HoR_BRIEF.md`**: The source of truth for the project content, specifications, and Gemini imagery generation prompts.

## Future Target Architecture

The static prototype is designed to be migrated into a modern, production-ready Next.js application with the following stack:

*   **Framework**: Next.js 15 (App Router) + React 19 + TypeScript (strict mode).
*   **Styling**: Tailwind CSS, utilizing the brand-specific HSL/HEX color tokens.
*   **Fonts**: `Playfair Display` (for headlines) and `Lato` (for UI and body text) loaded via `next/font/google`.
*   **Animations**:
    *   `motion` (Framer Motion v11+) for transitions, reveal animations, and hover states.
    *   `gsap` + `ScrollTrigger` + `@gsap/react` for scroll-pinned scrollytelling moments.
    *   `lenis` for site-wide smooth scrolling (disabled when `prefers-reduced-motion` is active).
*   **Icons**: `lucide-react` (line icons, weight 1.5px).

## Getting Started

To begin building the Next.js application inside this workspace, please follow the detailed guidelines and specifications outlined in the [agent.md](file:///y:/Github/HoR/House%20of%20Recovery/agent.md) file. 

### Bootstrapping the Next.js App
1.  Verify the environment is clean.
2.  Initialize the project:
    ```bash
    npx -y create-next-app@latest ./ --typescript --tailwind --app --src-dir --import-alias "@/*" --eslint
    ```
3.  Install core dependencies:
    ```bash
    npm install framer-motion gsap @gsap/react lenis lucide-react clsx tailwind-merge
    ```
4.  Port the Tailwind configuration from `House of Recovery.html` tokens.
5.  Port components and pages as described in `agent.md`.

## Content & Assets Management

*   **Imagery**: Do not use generic spa stock photos (no pebbles, lotus flowers, or candles). Refer to `uploads/HoR_BRIEF.md` or `agent.md` Section 3 for the Gemini Imagen prompts used to generate the clinical, high-end editorial visuals. Save all outputs in `/public/images/`.
*   **Logos**: Move `assets/logo/` into the `/public/logo/` folder of the new Next.js project.
*   **Verbatim Data**: Prices, schedules, and clinic contact placeholders must be kept exactly as specified.
