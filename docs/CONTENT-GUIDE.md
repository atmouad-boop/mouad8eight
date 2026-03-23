# Mouad8eight — Content Update Guide

Everything you need to update the site is in two places:
- **`src/data/`** — text content, links, and media references
- **`public/images/`** — photo files

After any change, run `git add . && git commit -m "your message" && git push`
and Netlify rebuilds the site automatically in ~30 seconds.

---

## Table of Contents

1. [Add or change photos](#1-add-or-change-photos)
2. [Add or change the logo](#2-add-or-change-the-logo)
3. [Add or change YouTube sets](#3-add-or-change-youtube-sets)
4. [Add or change gigs](#4-add-or-change-gigs)
5. [Update the bio and genre tags](#5-update-the-bio-and-genre-tags)
6. [Update social links and email](#6-update-social-links-and-email)
7. [Change any text on the site](#7-change-any-text-on-the-site)
8. [Change brand colors or fonts](#8-change-brand-colors-or-fonts)
9. [Update the booking form email](#9-update-the-booking-form-email)
10. [Change the site title or SEO description](#10-change-the-site-title-or-seo-description)

---

## 1. Add or change photos

### Hero background (full-screen image behind the name)

**File:** `src/components/Hero.astro`

Find this line:
```html
<img
  src="https://images.unsplash.com/..."
```

Replace the `src` value with either:
- A local file: drop the photo in `public/images/` and use `src="/images/your-photo.jpg"`
- A direct image URL from any host

Recommended size: at least **1920×1080px**, compressed under 500KB.

---

### About portrait (the tall portrait next to the bio)

**File:** `src/components/About.astro`

Find this line:
```html
<img
  src="https://images.unsplash.com/..."
```

Replace the `src` value the same way as the hero.
Recommended size: **800×1067px** (3:4 ratio), compressed under 300KB.

---

### Gallery photos

**File:** `src/data/gallery.js`

Each object in the array is one photo in the grid:

```js
{
  id: 1,                          // unique number — increment for each new photo
  src: "/images/your-photo.jpg",  // local path OR a full URL
  alt: "Brief description",       // shown to screen readers and if image fails to load
},
```

**To add a photo:**
1. Drop the file into `public/images/`
2. Add a new object to the array in `src/data/gallery.js`

**To remove a photo:** delete its object from the array.

**To reorder photos:** change the order of the objects in the array.
Photos are distributed across 4 columns automatically — no manual layout needed.

Recommended size: **800px wide**, compressed under 300KB each.

---

## 2. Add or change the logo

The site currently uses a text wordmark ("MOUAD8EIGHT") instead of an image logo.
There are two places it appears:

| Location | File |
|---|---|
| Navigation bar | `src/components/Navbar.astro` — line with `MOUAD8EIGHT` inside the `<a>` tag |
| Footer | `src/components/Footer.astro` — line with `MOUAD8EIGHT` inside the `<div>` tag |

### To replace with an image logo:

1. Drop your logo file (SVG recommended) into `public/images/logo.svg`
2. In `Navbar.astro`, replace:
```html
<a href="#home" class="text-2xl font-black tracking-tighter text-white sonic-monolith">
  MOUAD8EIGHT
</a>
```
With:
```html
<a href="#home">
  <img src="/images/logo.svg" alt="MOUAD8EIGHT" class="h-8" />
</a>
```
3. Do the same in `Footer.astro`

### Favicon (browser tab icon)

Replace the files at:
- `public/favicon.svg` — SVG version
- `public/favicon.ico` — ICO version (fallback)

Keep the same filenames.

---

## 3. Add or change YouTube sets

**File:** `src/data/sets.js`

Each object is one set card on the site:

```js
{
  id: 1,                          // unique number
  title: "Club Session Vol. 1",   // shown as the card title
  venue: "Example Club",          // shown in the subtitle
  city: "Málaga",                 // shown in the subtitle
  date: "2025-12-01",             // format: YYYY-MM-DD
  genre: "Techno",                // shown in the subtitle
  videoId: "dQw4w9WgXcQ",        // the part after "watch?v=" in the YouTube URL
},
```

**How to find the videoId:**
Open the YouTube video. The URL looks like:
`https://www.youtube.com/watch?v=dQw4w9WgXcQ`
The videoId is everything after `watch?v=` — in this case `dQw4w9WgXcQ`.

**Grid layout:**
- The **first** set in the array is always displayed as the large featured card
- Sets 2 and 3 appear as smaller side cards
- Any sets beyond 3 are counted in the "View All on YouTube" link but not shown individually — add them to YouTube and they'll be accessible via that link

---

## 4. Add or change gigs

**File:** `src/data/gigs.js`

Each object is one row in the Gigs section:

```js
{
  id: 1,                                        // unique number
  date: "2026-04-12",                           // format: YYYY-MM-DD
  venue: "Club Name",                           // shown as the main title
  city: "Málaga",                               // shown in the subtitle
  country: "Spain",                             // shown in the subtitle
  ticketUrl: "https://example.com/tickets",    // link for the Tickets button
  // ticketUrl: null,                           // use null if there's no ticket link yet
},
```

**Tips:**
- Keep the list in **chronological order** (nearest date first)
- **Remove past gigs** to keep the list clean — just delete their object
- When `ticketUrl` is `null`, the row shows "TBA" instead of a Tickets button

---

## 5. Update the bio and genre tags

**File:** `src/data/bio.js`

```js
export const bio = {
  tagline: "Techno. House. No limits.",   // shown as the eyebrow text in the Hero section
  text: `...`,                            // the paragraph in the About section
  genres: ["Techno", "House", ...],       // the tag badges in the About section — add or remove as needed
  socials: { ... },                       // see section 6 below
};
```

- Edit `tagline` to change the short line that appears under the name in the hero
- Edit `text` to change the bio paragraph in the About section
- Edit `genres` to add, remove, or rename the genre tag badges

---

## 6. Update social links and email

**File:** `src/data/bio.js` — the `socials` object:

```js
socials: {
  instagram: "https://instagram.com/mouad8eight",
  soundcloud: "https://soundcloud.com/mouad8eight",
  youtube:    "https://youtube.com/@mouad8eight",
  email:      "booking@mouad8eight.com",
},
```

These values are used automatically across the site:
- `email` appears in the Booking section and is used for the mailto link
- `soundcloud` appears in the Booking section
- `youtube` is the destination of the "View All on YouTube" link in the Sets section
- `instagram`, `soundcloud`, `youtube` appear as links in the Footer

---

## 7. Change any text on the site

| Text | File | What to look for |
|---|---|---|
| Hero tagline ("Techno. House. No limits.") | `src/data/bio.js` | `tagline:` |
| Hero subheading ("Sculpting sonic landscapes...") | `src/components/Hero.astro` | The `<p>` below the `<h1>` |
| About section heading ("The Architect") | `src/components/About.astro` | The `<h2>` tag |
| About bio paragraph | `src/data/bio.js` | `text:` |
| Sets section description | `src/components/SetsGrid.astro` | The `<p>` in the section header |
| Gigs section heading ("Global Circuit") | `src/components/GigsList.astro` | The `<h2>` tag |
| Gallery section heading ("In the Dark") | `src/components/GalleryGrid.astro` | The `<h2>` tag |
| Booking section heading ("Secure Date") | `src/components/BookingForm.astro` | The `<h2>` tag |
| Booking description paragraph | `src/components/BookingForm.astro` | The `<p>` below the `<h2>` |
| Footer copyright name | `src/components/Footer.astro` | The `MOUAD8EIGHT` text and the copyright line |

---

## 8. Change brand colors or fonts

**File:** `src/styles/global.css` — the `@theme { }` block at the top.

### Key colors

```css
--color-background:  #0a0a0a;  /* main page background */
--color-secondary:   #3b82f6;  /* accent color — buttons, links, highlights */
--color-on-surface:  #e5e2e1;  /* main text color */
--color-on-surface-variant: #c2c6d6;  /* secondary/muted text */
```

Change `--color-secondary` to change the accent color site-wide (currently blue).

### Fonts

```css
--font-headline: "Space Grotesk", sans-serif;  /* headings, buttons, labels */
--font-body:     "Inter", sans-serif;           /* body text */
```

If you change fonts, also update the Google Fonts `<link>` in `src/layouts/BaseLayout.astro`
to load the new font family.

---

## 9. Update the booking form email

The form submissions go to whoever owns the Formspree account.
To change the notification email:
1. Log in at **formspree.io**
2. Open the form named "Mouad8eight Booking"
3. Go to **Settings** and update the notification email there

No code change needed.

---

## 10. Change the site title or SEO description

**File:** `src/layouts/BaseLayout.astro`

```astro
const {
  title = "MOUAD8EIGHT | Official Artist Portfolio",
  description = "Precision Techno Artist. Sculpting sonic landscapes...",
} = Astro.props;
```

Edit the default values for `title` and `description`.
These appear in the browser tab and in Google search results.

---

## Quick deploy reminder

After making any change:

```bash
git add .
git commit -m "describe what you changed"
git push
```

Netlify picks it up automatically. The live site updates in about 30 seconds.
