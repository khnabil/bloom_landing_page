# 🌸 Bloom Wellness — Landing Website

The official marketing website for **Bloom Wellness**, a women's health & PCOS
assistant app. This site introduces the product, showcases its features, and
guides visitors toward downloading the app.

Built with **htmx** + **Tailwind CSS** — a lightweight, server-friendly stack
that keeps every page fast, consistent, and easy to maintain.

---

## ✨ Pages

| Page | Path | Purpose |
|------|------|---------|
| Landing | [`index.html`](index.html) | Hero, "How it works", feature bento grid, testimonial, download CTA |
| Features | [`features.html`](features.html) | Every Bloom capability: cycle tracking, mood logging, AI plans, AI therapist, community, resources |
| Mood Tracking | [`mood-tracking.html`](mood-tracking.html) | How check-ins work, an interactive mood demo, and insight previews |
| Therapy | [`therapy.html`](therapy.html) | The 24/7 CBT-based AI therapist, a sample conversation, and guided approaches |
| Resources | [`resources.html`](resources.html) | Filterable library of meditations, sleep stories, breathing exercises, and articles |

All pages share the same header (with the **Bloom logo**), footer, color
palette, and typography via htmx-loaded partials.

---

## 🎨 Design System — "Organic Minimalism"

The site follows the same design language as the Bloom app, adapted for the web:

- **Palette:** Soft lavender `#655974` (primary), muted sage `#4a654f`
  (secondary), warm cream `#f4faff` (background), deep slate `#0e1d25` (text).
- **Dark mode:** A built-in toggle (sun/moon icon in the navbar) switches the
  whole site to a deep-slate dark palette. The choice is saved to
  `localStorage` and follows the system preference by default. All colors are
  defined as CSS custom properties in `assets/bloom.css`, so every page adapts
  automatically — no per-element `dark:` classes needed.
- **Typography:** Noto Serif for headlines, Plus Jakarta Sans for body and
  labels — a "high-low" contrast pairing that feels warm yet evidence-based.
- **Shapes:** Extreme roundedness — pill buttons, 32px+ card radii, and organic
  "blob" shapes that break the rigidity of the grid.
- **Depth:** Glassmorphism panels (20px backdrop blur) and soft "ambient glow"
  shadows instead of heavy drop shadows.
- **Motion:** Gentle floating and pulsing animations for decorative elements.

The palette is defined once in [`partials/head.html`](partials/head.html)
(Tailwind config) and [`assets/bloom.css`](assets/bloom.css) (custom styles),
so every page stays perfectly in sync.

---

## 🧩 How it's built

- **htmx** — the header and footer are shared partials
  ([`partials/header.html`](partials/header.html),
  [`partials/footer.html`](partials/footer.html)) loaded with
  `hx-get` + `hx-trigger="load"`. Update one file, and every page updates.
- **Static `<head>`** — the `<head>` (fonts, Tailwind config, `bloom.css`,
  htmx) is written **directly into every page**, not loaded via htmx. Loading
  it dynamically would break styling: a `<head>` nested inside `<head>` is
  dropped by the HTML parser, and `<script>` tags inserted via `innerHTML`
  never execute (so the Tailwind CDN would never run). [`partials/head.html`](partials/head.html)
  is kept as the canonical template — copy it into any new page.
- **Tailwind CSS** (CDN) — utility-first styling with a custom theme that maps
  directly to the Bloom design tokens.
- **Material Symbols** — the icon set used across the app and the site.
- **Vanilla JS** — small progressive enhancements (mobile menu, mood demo,
  resource filter) that work without any build step.

```
bloom landingp/
├── index.html              # Landing page
├── features.html           # Features overview
├── mood-tracking.html      # Mood tracking page
├── therapy.html            # Therapy & support page
├── resources.html          # Resources & library page
├── partials/
│   ├── head.html           # Canonical <head> template (copy into pages)
│   ├── header.html         # Shared header with Bloom logo (htmx-loaded)
│   └── footer.html         # Shared footer (htmx-loaded)
└── assets/
    ├── bloom.css           # Shared custom styles (blobs, glass, glows)
    ├── bloom_logo.png      # Bloom logo
    └── hero.png            # Hero background image
```

---

## 🚀 Run locally

No build step, no dependencies to install — just serve the folder:

```bash
# Python
python3 -m http.server 8000

# or Node
npx serve .
```

Then open <http://localhost:8000>.

> **Note:** the header/footer are loaded via htmx, so open the site through a
> local server (not `file://`) for the partials to load.

---

## 🔗 Related

- **Bloom app** — the Flutter + FastAPI application this site markets
  (`Cross_platform_android_app/dart/bloom`).
- **UI design** — the original landing page design
  (`bloom_landingpage_uidesign/`).

---

© 2024 Bloom Wellness. Your digital sanctuary for growth.