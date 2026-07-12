# CEnTRInnovations

The organizational website for **CEnTRInnovations, LLC**: tools and frameworks for community-engaged scholarship.

**Site:** [centrinnovations.com](https://centrinnovations.com)

---

## About CEnTRInnovations

CEnTRInnovations develops tools and approaches that support community-engaged scholarship. Our work centers on bridging institutional research with community partnership, impact measurement, and open-source collaboration.

This repository contains the source code for our organizational website, built with Hugo as a static site.

---

## Project Structure

```
/
├── content/                 # Page content and front matter
├── layouts/                 # Hugo templates
│   ├── baseof.html          # Single base template (all HTML/head/body tags)
│   ├── index.html           # Homepage template
│   ├── _default/            # Shared and default layouts
│   └── partials/            # Reusable template components
├── static/                  # Static assets (images, icons, illustrations)
├── css/                     # Stylesheets
├── config/                  # Hugo configuration
└── public/                  # Generated site (build output)
```

### Key Files

- **`layouts/baseof.html`** — Single base template; all other layouts extend it via Hugo blocks
- **`layouts/index.html`** — Homepage: orchestrates partials in sequence
- **`layouts/_default/single.html`** — Shared layout for all tool pages (SEEK, MAP, IMPACT)
- **`config/_default/hugo.toml`** — Hugo configuration, taxonomies
- **`config/_default/params.toml`** — Sitewide parameters

---

## Content Pages

- **Homepage** (`/`) — Long-scroll page with multiple sections
- **System Overview** (`/system`) — Overview of the CEnTR system
- **Framework** (`/framework`) — The four-layer framework
- **CEnTR SEEK** (`/centr-seek`) — Community engagement and knowledge integration tool
- **CEnTR MAP** (`/centr-map`) — Measurement and alignment planning tool
- **CEnTR IMPACT** (`/centr-impact`) — Impact-centered outcomes tool
- **Knowledge Graph** (`/terms`) — Interactive visualization of topics and audiences

---

## Architecture

### Templates

All templates extend `baseof.html` via Hugo blocks:

- `{{ block "main" . }}` — Required; every layout must define this
- `{{ block "scripts" . }}` — Optional; page-specific JS at end of body

### Stylesheets

Each page declares its stylesheet via front matter:

```yaml
---
css: "seek"
---
```

`baseof.html` loads it conditionally without hardcoded if-chains.

### Partials

Reusable components live in `layouts/partials/`. Partials with no per-page variation use `partialCached`.

### Reveal Animation

The IntersectionObserver script is defined once in `layouts/partials/reveal.html` and included in the `scripts` block via `baseof.html`.

---

## Front Matter Convention

All page parameters use nested YAML objects, passed directly to partials:

```yaml
---
title: "Page Title"
css: "seek"
topics: ["institutional-alignment", "community-representation"]
audiences: ["institutions", "researchers", "community-partners"]
hero:
  title: "CEnTR*SEEK"
  lead: "Long description..."
  eyebrow: "The CEnTR* System"
---
```

Partials receive these as: `{{ partial "hero.html" .Params.hero }}`

### Taxonomies

- **Audiences:** `institutions`, `researchers`, `community-partners`
- **Topics:** `institutional-alignment`, `community-representation`, `impact-measurement`, `open-source`, `partnership-development`

---

## Style & Identity

- **Colors:** Parchment background, gold accents
- **Body Font:** Alegreya (serif)
- **UI Font:** Alegreya Sans, Alegreya Sans SC (sans-serif)
- **Motif:** Network-inspired botanical illustrations
- **Assets:** Located in `static/assets/`; always provide meaningful alt text

---

## Contact

For questions about this site or CEnTRInnovations, visit [centrinnovations.com](https://centrinnovations.com) or contact centrinnovations@gmail.com.
