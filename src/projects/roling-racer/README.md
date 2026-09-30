# Roling Racer

Bilingual (Persian/English) marketing website for the ROLING RACER racing-fuel brand — hero, brand statement, product index, engineering, about, closing statement, and contact footer, one page per locale.

- **Role:** Frontend Developer
- **Period:** 2026-09-25 – 2026-09-30
- **Relationship:** client work

## Overview

Roling Racer is a racing-fuel and engine-fluids brand (seven products: racing fuels, a fuel base, engine fluids) selling through contact-driven channels — phone, email, and Instagram. The website is a single-page presentation per locale: a full first-load splash intro over a masked video, a hero with an animated square marker sweeping glyph-by-glyph across the headline, scroll-reveal sections presenting the brand statement, the product index with a live preview pane, engineering discipline, and brand background, closing with a contact footer. The Persian version is the primary locale with a fully RTL-correct layout.

## Responsibilities & Contributions

- Developed the entire website as a Next.js App Router static export, end to end, delivered spec-first through my agentic development workflow.
- Built the first-load splash intro: a canvas pixel-rain simulation over a masked video, a brand-lockup tile animation, and a choreographed exit, with dedicated fallbacks for video error and ended events.
- Implemented the hero square-sweep animation, measuring each visible glyph of the headline and moving the marker glyph-to-glyph with a Web Animations API loop that pauses off-screen and resumes on re-entry.
- Built the shared scroll-reveal system (heading lines, copy, list items) used across all sections.
- Implemented the interactive product index with a desktop preview pane that swaps per hover/focus and an inline mobile presentation.
- Set up the per-locale routing (static export with client language detection at the root, extensionless `/fa` and `/en` URLs), RTL-correct Persian layout, per-locale SEO metadata with hreflang alternates, Organization JSON-LD, sitemap.xml, and robots.txt.
- Prepared and documented deployment to Apache shared hosting via cPanel, including extensionless URL rewriting, canonicalization, caching headers, and required file-permission fixing after upload.

## Notable Implementation Details

- Static export (`output: 'export'`, unoptimized images) — plain HTML/CSS/JS deployed to Apache shared hosting, with an `.htaccess` owning extensionless locale URLs, 301 canonicalization, and cache headers.
- Splash intro runs as a canvas-based pixel simulation with fixed pacing constants, capped in-flight elements, and layered reduced-motion behavior: the site-wide CSS motion floor, static equivalents for the sweep/reveal systems, and a rain-only skip in the splash.
- Hero sweep uses the Web Animations API with per-glyph keyframes, cap-height measurement with trailing letter-spacing correction, `resize`/font-loading re-measurement, and an IntersectionObserver pause/resume.
- The Reveal system is a reusable set of Motion primitives (heading lines, copy, list items) with a `once: true` viewport trigger and a `<noscript>` fallback keeping content visible without JavaScript.
- The product index is a static list mapped to per-product images, driven entirely by per-locale dictionaries; phones and contact data are hardcoded in the page component.

## Tech Stack

- Next.js
- React.js
- TypeScript
- Tailwind CSS
- Motion
- Agentic AI Development
- Agentic Workflows

## Public URL

- https://rolingracer.ir/en

## Related Experience

- [Senior Full-Stack Engineer (Agentic Development) @ Self-Employed / Freelance](../../experiences/senior-full-stack-engineer-agentic-development-self-employed/README.md)