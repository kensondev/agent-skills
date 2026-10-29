# Example run
**User:** "Make me a landing page for 'Tidy', an AI inbox cleaner for freelancers. Two plans, $0 and $9/mo. Brand color teal."

**Agent (using this skill) output summary:**
- Scaffolded Next.js 16 App Router project, `src/config/site.ts` with Tidy copy (hero: "Inbox zero, on autopilot").
- 11 sections built from config; pricing toggle shows $9/mo or $90/yr.
- `/api/waitlist` with honeypot + 5 req/min rate limit; `WAITLIST_PROVIDER=console` by default.
- OG image, sitemap, robots, JSON-LD added.
- `npm run lint` ✔ 0 problems · `npm run build` ✔ compiled, 6 static routes.
- Assumptions: testimonials are placeholders; logo cloud uses neutral wordmarks.
- Deploy: `vercel --prod`.

A complete reference build of this skill's output (the LaunchKit template) is shown in the preview images.
