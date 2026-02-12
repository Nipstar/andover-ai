# Claude Code Prompt: Andover AI Automation Website Build

## Project Overview

Build a single-page marketing website for **Andover AI Automation** (andoveraiautoamation.com) — an AI automation agency based in Andover, Hampshire, UK. The site's primary goal is generating local leads for AI voice agents, chatbots, and workflow automation services targeting small businesses in Andover and Hampshire.

The site should be a **Next.js static site** (or single HTML file if simpler to deploy) that is SEO-optimised, fast-loading, and designed to convert visitors into booked discovery calls.

---

## Design Direction & Aesthetic

### Tone: Dark, premium tech — not generic AI slop

Take heavy inspiration from these three reference sites (study their layout patterns, not copy them):

- **agento-ai.com** — Clean single-page flow, cal.com embed at bottom, solutions split into voice agents & chatbots, simple FAQ accordion
- **6omb.ai** — Dark theme with subtle video backgrounds, animated marquee text, bento grid cards, bold typography, smooth scroll reveals
- **aitoflo.com** — Audio demo players, demo call CTA, use-case cards split into inbound/outbound/products, scrolling testimonial carousel

### Design Rules

1. **Dark theme** — Deep navy/charcoal base (#0a0f1c or similar), with electric blue (#3b82f6) or cyan (#06b6d4) as primary accent. Secondary accent: warm amber/gold (#f59e0b) for CTAs only
2. **Typography** — Use a bold display font like "Cabinet Grotesk", "Clash Display", "Satoshi", or "General Sans" (from Google Fonts or CDN). Body text in a clean sans like "Plus Jakarta Sans" or "DM Sans". NO Inter, Roboto, Arial
3. **Animations** — Subtle and purposeful:
   - Staggered fade-up on scroll for sections (IntersectionObserver, ~100ms delays between elements)
   - Gentle parallax on hero background (CSS or minimal JS)
   - Smooth hover lifts on cards (transform: translateY(-4px) with box-shadow transition)
   - A single animated gradient orb or mesh in the hero (CSS only, subtle pulse/drift)
   - Number counter animation for stats section
   - NO excessive particle effects, no floating bubbles, no matrix rain
4. **Layout** — Full-width sections, generous padding (80-120px vertical). Bento-style grid for features/services. Asymmetric hero layout with text left, visual element right
5. **Mobile-first** — Fully responsive. Hamburger nav on mobile. All sections stack cleanly
6. **NO stock photos** — Use CSS gradients, geometric SVG patterns, abstract shapes, icon-based illustrations. Use Lucide icons or Heroicons (outline style)

---

## Site Structure (Single Page, Anchored Sections)

### Navigation (Fixed/Sticky)
- Logo: "Andover AI" or "Andover AI Automation" text logo with a subtle circuit/waveform icon
- Nav links: Services | How It Works | Why Us | FAQ | Contact
- CTA button: "Book a Free Discovery Call" → scrolls to booking section

### Section 1: Hero
- **Headline**: "AI Voice Agents & Automation for Hampshire Businesses"
- **Subheadline**: "Stop missing calls. Stop losing leads. We build AI-powered voice agents, chatbots, and workflow automation that work 24/7 — so you don't have to."
- **Primary CTA**: "Book Your Free Discovery Call" → scroll to cal.com section
- **Secondary CTA**: "See How It Works" → scroll to How It Works
- **Visual**: Animated gradient mesh/orb on the right side, or a minimal waveform animation suggesting voice AI
- **Trust bar below hero**: "Serving businesses across Andover, Hampshire & the South of England" with subtle location pin icon

### Section 2: Problem / Pain Points (3 cards)
- "Missed calls costing you customers?"
- "Drowning in admin and repetitive tasks?"
- "Can't afford 24/7 reception staff?"
- Brief 1-2 sentence descriptions for each
- Use icons (phone-missed, clipboard-list, clock)

### Section 3: Services (Bento Grid)
Three main service cards in a bento/asymmetric grid:

**AI Voice Agents** (largest card)
- Handle inbound & outbound calls automatically
- 24/7 appointment booking & lead qualification
- Natural-sounding conversations that represent your brand
- Icon: Phone + waveform

**AI Chatbots**
- Website, WhatsApp & social media chatbots
- Instant customer support & FAQ handling
- Lead capture and qualification on autopilot
- Icon: Message bubbles

**Workflow Automation**
- Automate repetitive business processes
- CRM updates, email sequences, invoicing
- Connect all your business tools seamlessly
- Icon: Workflow/nodes diagram

### Section 4: How It Works (3-Step Process)
Horizontal timeline on desktop, vertical on mobile:
1. **Discovery Call** — "We learn about your business, pain points, and goals. 30 minutes, no obligation."
2. **Custom Build** — "We design and build your AI solution, tailored to your specific workflows and brand voice."
3. **Launch & Optimise** — "Go live with full support. We monitor, tweak, and optimise for peak performance."

### Section 5: Who We Help (Industry Cards)
Scrollable horizontal cards or grid:
- Plumbers & Heating Engineers
- Electricians
- HVAC Companies
- Estate Agents
- Dental & Medical Practices
- Trades & Field Service Businesses
- Professional Services
- Any small business that takes phone calls

Each card has an icon and 1-line description of the AI use case.

### Section 6: Why Choose Us / Stats
Bento grid with:
- "Based in Andover, Hampshire" — We're local. We understand local business.
- "30+ Years in Business Technology" — Not just AI hype. Real-world experience.
- "Certified Retell AI Partner" — Official partner badge/mention
- "24/7 AI That Never Calls in Sick" — Your AI works weekends, bank holidays, and 3am
- Animated counter stats: "500+ Calls Handled" | "24/7 Availability" | "< 1 Second Response Time" | "30+ Years Experience"

### Section 7: FAQ Accordion
Style: Clean dark cards, smooth expand/collapse animation, plus/minus toggle icon.

**Questions to include:**
- What is an AI voice agent?
- How much does it cost?
- How long does it take to set up?
- Will it sound robotic?
- Can it book appointments in my calendar?
- Do I need technical knowledge?
- What happens if the AI can't handle a call?
- Do you work with businesses outside Andover?

Write helpful, benefit-focused answers. Keep them conversational, not corporate. 2-3 sentences each.

### Section 8: Contact & Booking (Two-Column Layout)

**Left Column: Contact Form**
Fields:
- Name (required)
- Email (required)
- Phone (optional)
- Business Name (optional)
- Message / "Tell us about your business" (textarea, optional)
- Submit button: "Send Message"

**Form submission**: POST to webhook URL `https://antekauto.app.n8n.cloud/webhook-test/29e3a09b-5b23-489b-a800-a07262afb4cb`
- Add a hidden field for the page URL/source
- Show a success toast/message on submission
- Basic client-side validation
- Honeypot spam field (hidden)

**Right Column: Cal.com Embed**
Use this exact embed code:
```html
<div style="width:100%;height:100%;overflow:scroll" id="my-cal-inline-30min"></div>
<script type="text/javascript">
  (function (C, A, L) { let p = function (a, ar) { a.q.push(ar); }; let d = C.document; C.Cal = C.Cal || function () { let cal = C.Cal; let ar = arguments; if (!cal.loaded) { cal.ns = {}; cal.q = cal.q || []; d.head.appendChild(d.createElement("script")).src = A; cal.loaded = true; } if (ar[0] === L) { const api = function () { p(api, arguments); }; const namespace = ar[1]; api.q = api.q || []; if(typeof namespace === "string"){cal.ns[namespace] = cal.ns[namespace] || api;p(cal.ns[namespace], ar);p(cal, ["initNamespace", namespace]);} else p(cal, ar); return;} p(cal, ar); }; })(window, "https://app.cal.com/embed/embed.js", "init");
Cal("init", "30min", {origin:"https://app.cal.com"});
  Cal.ns["30min"]("inline", {
    elementOrSelector:"#my-cal-inline-30min",
    config: {"layout":"month_view","useSlotsViewOnSmallScreen":"true"},
    calLink: "antek-automation/30min",
  });
  Cal.ns["30min"]("ui", {"hideEventTypeDetails":false,"layout":"month_view"});
</script>
```

### Section 9: Footer
- Business name: Andover AI Automation
- Address line: "Based in Andover, Hampshire, UK"
- Email: contact@andoveraiautoamation.com (or placeholder)
- Links: Privacy Policy | Terms of Service
- Copyright: © 2025 Andover AI Automation. All rights reserved.
- Small tagline: "AI Automation Agency serving Andover, Hampshire & the South of England"

---

## SEO Requirements (CRITICAL)

### On-Page SEO

**Title tag**: "AI Voice Agents & Automation for Businesses in Andover, Hampshire | Andover AI Automation"

**Meta description**: "AI voice agents, chatbots and workflow automation for small businesses in Andover and Hampshire. 24/7 call handling, lead capture and appointment booking. Book a free discovery call today."

**H1**: Only one H1 — the hero headline
**H2s**: Each major section heading
**H3s**: Sub-items within sections (service cards, FAQ questions, etc.)

### Target Keywords to Weave Into Copy Naturally
These are derived from actual Google Search Console impression data. Work these into headings, body copy, alt text, and schema where natural:

**Primary (highest impression volume):**
- ai services hampshire (379 impressions)
- ai agency hampshire (308 impressions)
- ai automation company andover (92 impressions)
- ai automation for small business andover (80 impressions)
- automation solutions for small business andover (76 impressions)
- best ai automation company in andover (75 impressions)

**Secondary:**
- ai voice agents andover (39 impressions)
- automated phone answering andover (38 impressions)
- ai call handling solutions hampshire (35 impressions)
- who installs ai voice agents for businesses in andover (41 impressions)
- who provides ai voice assistants for businesses in andover (40 impressions)
- voice bot services for small business andover (8 impressions)
- ai customer service agents andover (6 impressions)

**Long-tail / Question-based (use in FAQ or body copy):**
- who can automate my business processes in andover?
- how do i automate my office in andover?
- can ai handle customer calls for my shop in andover?
- how can i automate my business calls in andover?
- who offers ai automation services near the chantry centre?

### AI/LLM Search Optimisation (GEO - Generative Engine Optimisation)
- Include **structured, factual statements** that LLMs can extract: "Andover AI Automation is an AI automation agency based in Andover, Hampshire, UK, specialising in AI voice agents, chatbots, and workflow automation for small businesses."
- Use **entity-rich copy**: mention "Andover", "Hampshire", "South of England", "UK" naturally throughout
- Include a **"About" micro-section** near the footer with a dense, factual paragraph about the business (who, what, where, for whom) — this is what AI search engines will cite
- Add **FAQ schema** (JSON-LD) so questions appear in AI-generated answers
- Add **LocalBusiness schema** (JSON-LD) with:
  - name: "Andover AI Automation"
  - address: Andover, Hampshire, UK
  - geo coordinates for Andover: 51.2115, -1.4914
  - areaServed: ["Andover", "Hampshire", "South of England", "United Kingdom"]
  - services offered
  - URL, telephone (placeholder)
- Add **Organization schema** with sameAs links (placeholder social URLs)
- Use `<article>` and semantic HTML throughout
- Natural internal anchor links between sections

### Technical SEO
- Semantic HTML5 (`<header>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<nav>`)
- Proper heading hierarchy (H1 → H2 → H3, no skipping)
- Alt text on all images/SVGs (descriptive, keyword-aware)
- Canonical URL tag
- Open Graph meta tags (title, description, image, URL, type)
- Twitter Card meta tags
- Robots meta: index, follow
- Sitemap.xml (basic)
- Fast loading: inline critical CSS, defer non-critical JS, no heavy frameworks unless needed
- Minified output
- `lang="en-GB"` on html tag
- Favicon (generate a simple one with SVG)

---

## Technical Stack Preference

**Option A (Preferred — if deploying on Vercel/Netlify):**
- Next.js 14+ with App Router, static export
- Tailwind CSS
- Framer Motion for animations
- TypeScript

**Option B (Simpler — single file deployment):**
- Single `index.html` file with inline CSS and JS
- Vanilla JS for interactions (IntersectionObserver for scroll animations, accordion toggles)
- CSS custom properties for theming
- No build step needed

**Choose Option B if the goal is a quick, deployable single file. Choose Option A for a more maintainable codebase.**

---

## Colour Palette (CSS Variables)

```css
:root {
  --bg-primary: #0a0f1c;
  --bg-secondary: #111827;
  --bg-card: #1a1f2e;
  --bg-card-hover: #232938;
  --text-primary: #f1f5f9;
  --text-secondary: #94a3b8;
  --text-muted: #64748b;
  --accent-primary: #3b82f6;
  --accent-secondary: #06b6d4;
  --accent-cta: #f59e0b;
  --accent-cta-hover: #d97706;
  --border: #1e293b;
  --gradient-start: #3b82f6;
  --gradient-end: #06b6d4;
}
```

---

## Copy Tone & Voice

- **Conversational but professional** — like talking to a knowledgeable local business owner, not a Silicon Valley startup bro
- **UK English spelling** throughout (optimise, specialise, colour, etc.)
- **Benefit-led** — always lead with what the customer gets, not what you do
- **Local pride** — mention Andover and Hampshire naturally, not forced
- **No jargon** — explain things simply. Target audience is a plumber or estate agent, not a developer
- **Confident but not arrogant** — "We build..." not "We're the world's leading..."

---

## Files to Generate

1. All source code files (components, pages, styles)
2. `robots.txt`
3. `sitemap.xml`
4. JSON-LD schema (embedded in head or as script tags)
5. `README.md` with setup/deploy instructions

---

## Final Checklist Before Delivering

- [ ] All sections render correctly on mobile (320px), tablet (768px), desktop (1440px)
- [ ] Contact form POSTs to webhook with all fields as JSON
- [ ] Cal.com embed loads and is interactive
- [ ] All scroll animations trigger correctly
- [ ] FAQ accordion works (only one open at a time)
- [ ] Lighthouse score: aim for 90+ on Performance, SEO, Accessibility, Best Practices
- [ ] All JSON-LD schema validates (test at schema.org validator)
- [ ] No console errors
- [ ] UK English spelling throughout
- [ ] All target keywords appear naturally in copy
- [ ] Dark theme is consistent throughout — no jarring white sections
- [ ] CTA buttons are visible and high-contrast (amber/gold on dark)
- [ ] Smooth scroll behaviour on anchor links
- [ ] Page loads fast — no unnecessary external dependencies
