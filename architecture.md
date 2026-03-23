# Architecture Decisions

## ADR-001 — Astro over Next.js
**Date:** 2026-03-23
**Decision:** Use Astro instead of Next.js
**Reason:** This is a static portfolio. No server-side logic needed. Astro ships zero JS by default, loads faster, and is simpler to maintain. Next.js would be overkill.

## ADR-002 — No CMS
**Date:** 2026-03-23
**Decision:** Use plain JS data files instead of Strapi or any headless CMS
**Reason:** Content updates are infrequent (new set every few weeks). A CMS adds infrastructure, maintenance, and cost. Data files edited directly are sufficient for this scale.

## ADR-003 — Formspree over custom backend
**Date:** 2026-03-23
**Decision:** Use Formspree for the booking form
**Reason:** No backend needed. Formspree handles email delivery, spam filtering, and notifications for free under 50 submissions/month — more than enough for a DJ booking form.

## ADR-004 — YouTube embeds over self-hosted video
**Date:** 2026-03-23
**Decision:** Embed sets from YouTube, not self-hosted
**Reason:** Self-hosting video requires storage infrastructure, CDN, and streaming configuration. YouTube handles all of this for free and provides better playback performance globally.

## ADR-005 — Netlify over Hetzner VPS
**Date:** 2026-03-23
**Decision:** Deploy on Netlify instead of a VPS
**Reason:** Static site needs no server. Netlify gives free hosting, automatic deploys from Git, HTTPS, and CDN with zero configuration. Hetzner VPS would require maintenance for no benefit here.
