---
name: nextjs-landing-page-builder
description: Build a conversion-focused SaaS landing page + waitlist in Next.js (App Router, TypeScript strict, Tailwind). Use when the user asks for a landing page, launch page, waitlist, or marketing site in Next.js/React.
---
# Next.js Landing Page Builder

## Goal
Ship a production-ready landing page with a working waitlist in one pass: builds clean, passes lint, is accessible, and is rebrandable from ONE config file.

## Workflow
1. **Brief (ask once, then assume):** product name, one-line value prop, audience, 3–6 features, pricing tiers (or "none"), primary CTA, brand color. If missing, pick sensible defaults and list them at the end.
2. **Scaffold:** `npx create-next-app@latest --ts --tailwind --app --eslint --src-dir`. Never add a UI kit unless asked.
3. **Single source of truth:** create `src/config/site.ts` exporting a typed `siteConfig` (name, tagline, nav, hero, features, steps, testimonials, pricing, faq, footer, links). Every component reads from it; no hard-coded copy in JSX.
4. **Sections (in order):** Navbar (sticky, mobile menu with focus trap) → Hero (H1 ≤ 10 words, sub ≤ 25 words, waitlist form) → Logo cloud → Feature grid → How it works (3 steps) → Product mockup (CSS only, no stock images) → Testimonials (clearly labeled placeholders) → Pricing (monthly/yearly toggle, highlight one plan) → FAQ (native `<details>` or ARIA accordion) → Final CTA → Footer.
5. **Waitlist API:** `src/app/api/waitlist/route.ts` with zod-style validation, honeypot field, in-memory rate limit (per IP, 5/min), and provider switch via `WAITLIST_PROVIDER=console|webhook|resend`. Return JSON `{ok, message}`; never leak provider errors to the client.
6. **SEO:** Metadata API (title template, description, OG/Twitter), `opengraph-image.tsx` generated with `ImageResponse`, `sitemap.ts`, `robots.ts`, JSON-LD `SoftwareApplication`.
7. **Theme:** dark mode via `class` strategy with an inline no-flash script; respect `prefers-reduced-motion`.
8. **Quality gate (must run):** `npm run lint && npm run build`. Fix every error before reporting.

## Rules
- Mobile-first; test 390px and 1440px widths.
- Contrast ≥ 4.5:1; every input has a label; visible focus rings.
- No fake social proof: placeholders say "Your customer quote here".
- Keep client components minimal (`"use client"` only for toggles/forms).

## Deliverable checklist (report back)
- [ ] Files created and what each does
- [ ] Env vars (`WAITLIST_PROVIDER`, `WAITLIST_WEBHOOK_URL`, `RESEND_API_KEY`, `RESEND_AUDIENCE_ID`)
- [ ] Assumptions made from the brief
- [ ] Lint + build output summary
- [ ] One-line deploy instruction (Vercel)
