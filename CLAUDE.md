# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Marketing website for **Andover AI Automation** — an AI automation agency in Andover, Hampshire, UK. Single-page static site targeting local small businesses for AI voice agents, chatbots, and workflow automation services.

**Live site:** https://aiautomationandover.co.uk

## Tech Stack

Single `index.html` with all CSS and JS inline. No build step, no frameworks, no dependencies.

- HTML5, vanilla JavaScript (ES5 compatible), CSS3 with custom properties
- Google Fonts: **Sora** (display) and **DM Sans** (body)
- No package.json, no npm — open `index.html` directly in a browser to develop

### Development

```bash
open index.html          # open in default browser
# or use any local server:
python3 -m http.server 8000
```

### Deployment

No build step. Deploy the root directory to any static host (GitHub Pages, Netlify, Vercel as "Other" framework, or any web server). Required files: `index.html`, `robots.txt`, `sitemap.xml`, `images/` folder.

## Architecture

Everything lives in `index.html` (~2150 lines):
- **Lines 1–143:** HTML head with meta tags, OG tags, JSON-LD schemas, Google Fonts import
- **Lines 144–1985:** Single `<style>` block (all CSS including responsive breakpoints and animations)
- **Lines 1986–2152:** HTML body with all sections, then two `<script>` blocks (IntersectionObserver animations, FAQ accordion, contact form handler, mobile menu, counter animations)

### Page Sections (anchor-linked navigation)
Hero → Pain Points → Services (bento grid) → Demo (live chatbot + AI voice agent phone numbers) → How It Works (3-step timeline) → Industries → FAQ (accordion) → Contact & Booking → Footer

### Key Integrations

- **Contact form** → POST to n8n webhook (`https://antekauto.app.n8n.cloud/webhook/29e3a09b-5b23-489b-a800-a07262afb4cb`). Includes honeypot "website" field for spam detection. Fields: name, email, phone, business, message, plus hidden source/page_url.
- **Cal.com embed** → iframe calendar booking widget (`antek-automation/30min`), monthly view on desktop, slots view on mobile
- **Demo section** → links to https://boltelectrical.uk/ (chatbot demo) and live AI voice agent phone numbers

## Design System

### Colour palette (CSS custom properties defined at `:root`)
- Backgrounds: `#0a0f1c` / `#111827` / `#1a1f2e` (cards)
- Text: `#f1f5f9` / `#94a3b8` / `#64748b`
- Accents: `#3b82f6` (electric blue), `#06b6d4` (cyan), `#10b981` (emerald green — CTAs only)
- **No warm tones** — zero orange, amber, gold, coral, salmon, or yellow anywhere

### Animation constraints
- Staggered fade-up on scroll (IntersectionObserver, ~100ms delays)
- Animated gradient orb in hero (CSS keyframes only)
- Card hover: `translateY(-4px)` with box-shadow transition
- Number counter animation for stats
- **No** particle effects, floating bubbles, or matrix rain

### Layout rules
- Full-width sections, 80–120px vertical padding
- Mobile-first responsive (breakpoints: 320px, 768px, 1440px)
- No stock photos — CSS gradients, SVG patterns, and icons only
- Dark theme throughout — no white sections

## Content & Copy Rules

- **UK English** spelling throughout (optimise, specialise, colour)
- Conversational but professional tone — target audience is local tradespeople and business owners, not developers
- Benefit-led copy — lead with what the customer gets

## SEO Requirements

- Single H1 (hero headline only), H2 per section, H3 for sub-items
- Semantic HTML5 (`<header>`, `<main>`, `<section>`, `<footer>`, `<nav>`)
- `lang="en-GB"` on `<html>`
- JSON-LD schemas embedded: LocalBusiness (geo: 51.2115, -1.4914), Organization, FAQPage
- Open Graph + Twitter Card meta tags
- Canonical URL, robots meta `index, follow`

## Quality Targets

- Lighthouse: 90+ on Performance, SEO, Accessibility, Best Practices
- No console errors
- JSON-LD validates at schema.org validator
- Dark theme consistent throughout — no white sections
