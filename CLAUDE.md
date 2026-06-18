# CloseFlow AI — Project Context

## What This Is
A single-page marketing website for **CloseFlow AI**, an AI automation agency. The site is a static HTML file deployed to GitHub Pages.

- **Live URL**: https://ryanjramirez23-commits.github.io/close-flow/
- **Repo**: ryanjramirez23-commits/close-flow
- **Dev branch**: `claude/close-flow-ai-website-qv9pbc`
- **Deploy**: GitHub Actions auto-deploys on push to that branch (`.github/workflows/deploy.yml`)

---

## The Business

**CloseFlow AI** builds custom AI automation systems for business owners who want to scale. The systems run marketing, lead generation, content, and operations — and improve automatically over time.

### Founder Background
- 2 years door-to-door sales (hundreds of thousands in sales, recruited large teams)
- Currently runs a life insurance agency doing ~$150k/month
- Has hands-on knowledge of what scaling actually requires

### Target Market
ANY business owner who wants to scale — NOT just D2D. Industries:
- Home Services
- Life Insurance
- Sales Teams
- E-Commerce
- Agencies
- Any Business

### Core Value Props
1. Everything costing time and money → automated
2. The system gets better every week on its own (self-improving)
3. Built by operators who've actually run businesses, not just tech people
4. Security is a top priority — enterprise-grade, built from the ground up
5. Team of developers (not a one-man shop — present as a full operation)

### Services
- Meta ads / lead generation — builds and runs campaigns that learn what converts
- Content creation — scans viral content in the client's space, produces and distributes on-brand content automatically
- Recruiting ads — finds candidates, AI screens and books interviews
- CRM / calendar automation — instant follow-up (under 60 seconds), auto-booking
- AI receptionist — answers calls, qualifies leads, books appointments
- Websites and landing pages
- Analytics, optimization, reporting — real-time dashboards, auto-shifts budget

---

## Critical Brand Rules

**NEVER mention specific AI tool names** — no Claude, OpenAI, ChatGPT, Anthropic, etc. The reason: it could push prospects to DIY or do nothing, which means they do nothing effective. Just say "AI systems," "our systems," "the system."

**Present as a full team** — "our development team," "our engineers," "our team reviews every system." Never imply one person.

**Tone**: Direct, confident, operator-to-operator. Not techie. Not sales-y hype. Speaks to someone who runs a real business.

---

## Design System

### Colors (CSS variables)
```
--gold:     #F0B429   (primary accent)
--gold-2:   #E8A010
--gold-dim: rgba(240,180,41,0.09)
--gold-glow: rgba(240,180,41,0.22)
--bg:       #080808   (background)
--s1:       #0E0E0E
--s2:       #141414
--s3:       #1C1C1C
--b1:       #222222   (borders)
--b2:       #2E2E2E
--t1:       #F9F9F9   (primary text)
--t2:       #A0A0A0
--t3:       #686868
--t4:       #444444
```

### Fonts
- **Display/headings**: Plus Jakarta Sans (700, 800, 900) — loaded from Google Fonts
- **Body**: Inter (400, 500, 600, 700) — loaded from Google Fonts
- Tailwind CSS via CDN

### 3D Scene (Three.js)
WebGL canvas fixed behind all content. Key elements:
- Central octahedron hub (gold, emissive, pulsing)
- 6 orbiting box-shaped workflow nodes: Ads, Content, Leads, Recruit, CRM, Reports
- 55 outer cube data nodes floating in space
- Connection lines: hub → nodes, nodes → outer, outer → outer
- 90 data packet particles flowing along paths
- Background grid dots (data-matrix aesthetic)
- Floating horizontal bars (code-line aesthetic)
- UnrealBloomPass (strength 1.2, radius 0.6, threshold 0.8)
- OrbitControls with auto-rotate, damping

---

## Page Sections (in order)

1. **Nav** — Fixed, frosted glass, scrolled state adds shadow
2. **Hero** — Full viewport, "Everything Costing You Time and Money. Automated." + industry list
3. **Stats** — 10×, 24/7, ↑ (gets better every week)
4. **What We Automate** — 6 cards: Lead Gen/Meta Ads, Content, Recruiting, CRM/Follow-up, AI Receptionist, Analytics
5. **How It Works** — 4-step flow: Discovery → Custom Build → Launch & Monitor → Learns & Improves
6. **Packages** — 3 tiers (see below)
7. **Why CloseFlow** — Operator-built, Full team, Gets better over time + Security block
8. **Founding Offer** — "2 founding spots remaining" urgency section
9. **Final CTA / Book a Call** — Contact card with email, phone, booking link
10. **Footer**

### Packages
| Tier | Name | Badge |
|------|------|-------|
| Starter | Growth Engine | std (gray) |
| Most Popular (featured) | Full Automation OS | pop (gold) |
| Enterprise | Business OS | std (gray) |

Most popular card has gold border and background tint, is the recommended CTA.

---

## Placeholders That Still Need Real Values

These are marked with `<!-- REPLACE -->` comments in the HTML:

1. **Email** (line ~509): Currently `contact@closeflow.ai` — confirm or replace
2. **Phone** (line ~515): Currently `+1 (000) 000-0000` — needs real number
3. **Booking link** (lines ~521, ~528): Currently `#` and `calendly.com/closeflow` — needs real Calendly or cal.com URL
4. **"2 founding spots remaining"** — update this number as spots fill

---

## Tech Stack
- Static HTML (single file: `index.html`)
- Tailwind CSS via CDN
- Three.js `0.160.0` via unpkg ESM import
- Three.js addons: OrbitControls, EffectComposer, RenderPass, UnrealBloomPass
- Google Fonts (Plus Jakarta Sans + Inter)
- IntersectionObserver for scroll-triggered `.fu` (fade-up) animations
- No build step, no framework, no dependencies to install

---

## Deployment
- GitHub Actions workflow at `.github/workflows/deploy.yml`
- Triggers on push to `claude/close-flow-ai-website-qv9pbc` or `main`
- Uploads entire repo root as GitHub Pages artifact
- Takes ~1-2 minutes after push; hard-refresh browser to see changes

---

## What NOT to Do
- Don't name specific AI tools (Claude, OpenAI, GPT, etc.) anywhere in the website copy
- Don't make it sound like a one-person operation
- Don't change the black/gold color scheme — user specifically rejected blue as "too generic"
- Don't add a build system or framework unless the user asks — keep it simple static HTML
- Don't push to `main` directly — always use the dev branch above
