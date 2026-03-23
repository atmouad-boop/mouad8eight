# CLAUDE.md — Mouad8eight DJ Portfolio

This file is the source of truth for Claude when working on this project.
Read this before touching any file.

---

## Project Overview

A professional DJ portfolio website for **Mouad8eight**.
Built with **Astro + Tailwind CSS**, deployed on **Netlify** (static, zero server maintenance).
Contact/booking form handled by **Formspree** (no backend needed).
YouTube embeds for sets (no self-hosted audio/video).

---

## Stack

| Layer       | Technology              |
|-------------|-------------------------|
| Framework   | Astro                   |
| Styling     | Tailwind CSS            |
| Forms       | Formspree               |
| Video       | YouTube embed (iframe)  |
| Deployment  | Netlify                 |
| DNS/CDN     | Cloudflare              |

---

## Brand Identity

- **Name:** Mouad8eight
- **Display name:** MOUAD8EIGHT
- **Background:** #0a0a0a (near black)
- **Primary text:** #ffffff
- **Accent:** #e63030 (deep red) — can be revisited
- **Heading font:** Bebas Neue (bold, impactful)
- **Body font:** DM Sans (clean, modern)
- **Logo concept:** MOUAD wordmark + oversized 8 styled as ∞

---

## Site Structure

```
/ (Home)
  ├── #hero        — Full viewport, name, tagline, CTAs
  ├── #sets        — YouTube embed grid
  ├── #about       — Bio + genre tags
  ├── #gigs        — Upcoming events list
  ├── #gallery     — Photo grid
  ├── #booking     — Formspree contact form
  └── #footer      — Socials, email, copyright
```

Single page app — all sections on one scrollable page.

---

## Data Files (friend edits these to update content)

| File                  | Purpose                        |
|-----------------------|--------------------------------|
| src/data/sets.js      | YouTube set embeds             |
| src/data/gigs.js      | Upcoming gigs list             |
| src/data/gallery.js   | Gallery image paths            |
| src/data/bio.js       | About text + genre tags        |

**These are the ONLY files the DJ needs to touch to update content.**
Keep them simple: plain arrays of objects, well commented.

---

## Components

| Component              | Description                        |
|------------------------|------------------------------------|
| Navbar.astro           | Fixed top nav, smooth scroll links |
| Hero.astro             | Full viewport hero section         |
| SetCard.astro          | Single YouTube embed card          |
| SetsGrid.astro         | Grid of SetCards                   |
| About.astro            | Bio section                        |
| GigItem.astro          | Single gig row                     |
| GigsList.astro         | Upcoming gigs section              |
| GalleryGrid.astro      | Photo masonry/grid                 |
| BookingForm.astro      | Formspree form                     |
| Footer.astro           | Footer with socials                |

---

## Conventions

- All components in `src/components/`
- One layout: `src/layouts/BaseLayout.astro` (head, fonts, global styles)
- Tailwind for all styling — no custom CSS unless absolutely necessary
- Use CSS variables for brand colors (defined in BaseLayout)
- Mobile first — always
- No inline styles
- Images go in `public/images/` — use descriptive filenames (gig-2024-madrid.jpg)

---

## Formspree Setup

- Create account at formspree.io
- Create a new form → copy the endpoint
- Paste endpoint into `src/components/BookingForm.astro`
- Fields: name, email, event_type, date, location, budget, message

---

## Deployment

1. Push to GitHub
2. Connect repo to Netlify
3. Build command: `astro build`
4. Publish directory: `dist/`
5. Point domain via Cloudflare DNS

---

## What NOT to do

- Do not add a backend or database — this is intentionally static
- Do not self-host video or audio — always embed from YouTube
- Do not add a CMS — the data files ARE the CMS for now
- Do not use React or Next.js — Astro is the right tool here
- Do not over-engineer — this is a portfolio, keep it simple and shippable
