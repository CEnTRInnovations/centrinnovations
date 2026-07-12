# Homepage & System Page Tools Reorganization — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Reorganize the homepage's "Our Tools" section and rebuild the CEnTR* System page so both stop presenting SEEK → MAP → IMPACT as a strict linear pipeline and instead present the growing six-tool set (SEEK, MAP, CANON, FLOW, FRAME, IMPACT) grouped by which Framework layer (Stratigraphy, Topography, Infrastructure, Architecture) each tool serves — while keeping the homepage itself free of Framework jargon.

**Architecture:** Homepage keeps its existing long-scroll partial-orchestration pattern (`layouts/index.html`) — only the `system` section's data shape and partial markup change, plus a third card is added to the existing Commons (`open_tools`) section. The System page (`layouts/system/single.html` + `content/system.md`) is substantially rewritten: the old alternating SEEK/MAP/IMPACT sections and flow-diagram are replaced with a single "MAP spans every layer" card and a vertical stack of six layer-grouped tool rows. `content/system.md` front matter is migrated from flat `key_value` pairs to nested YAML objects per this project's documented convention.

**Tech Stack:** Hugo static site, no JS framework, no build step beyond `hugo build`. Source content lives in `design_handoff_tools_reorganization/` (gitignored, not committed) — copy from it, never reference it from templates.

## Global Constraints

- Source of truth for copy/layout/IA: `design_handoff_tools_reorganization/README.md`, `Homepage.dc.html`, `System Page.dc.html`. These are **references only** — never link to or copy their raw HTML/CSS wholesale.
- **Design system decision (confirmed with user):** re-skin, don't port verbatim. Keep the handoff's information architecture, copy, and component structure, but implement with the site's existing Alegreya / Alegreya Sans / Alegreya Sans SC fonts and existing CSS custom properties (`--bg-main`, `--text`, `--secondary`, `--seek-mid`, `--strat-mid`, etc.) and existing component classes (`.tool-card`, `.status-badge`, `.badge-dev`, `.badge-active`, `.eyebrow`, `.button`). Do **not** add Source Serif 4 / Work Sans / IBM Plex Mono or the handoff's hex palette.
- Content front matter: nested YAML objects only, per `CLAUDE.md` (`hero: { title: ... }`, not `hero_title: ...`). `content/system.md` currently violates this — this reorg fixes it since the whole file is being rewritten anyway.
- No new Hugo partials named after the handoff files. Reuse/extend the two existing partials in play: `layouts/partials/system.html` (homepage "Our Tools" section) and `layouts/system/single.html` (the System page template).
- No `{{ if eq .Layout "x" }}` additions to `baseof.html` — not needed; `styles.css` already loads unconditionally (homepage) and `system.css` already loads via the existing `eq .Layout "system"` conditional (system page already has `layout: "system"` in its front matter).
- No test framework exists in this repo. Verification for every task is: `hugo build 2>&1 | grep -iE "error|warn"` must produce no output, plus a manual check of the rendered page with `hugo server -D`.
- Content notes baked into the design (carry these into front matter exactly):
  - SEEK, FRAME, IMPACT are all Architecture-layer tools (Architecture has 3 rows, others have 1).
  - MAP is cross-layer — its own section above the layer list, not one of the six rows.
  - Understory is an Open Tool: appears in the System page's layer list (Stratigraphy row, dashed styling, "open tool" badge) but is **excluded** from the homepage's "Our Tools" row; it stays in the homepage Commons section.
  - Status badges: SEEK, MAP, CANON = "in development"; FLOW, FRAME = "concept"; IMPACT = "actively used"; Understory = "open tool"; Apiary Hive = "almost complete."
  - Homepage copy never uses the words "Framework," "Stratigraphy," "Topography," "Infrastructure," or "Architecture" — that vocabulary is reserved for the System page and the Framework page.
  - Apiary Hive's GitHub repo has not been confirmed public — leave its link field blank with a content-author note rather than guessing a URL.

---

## File Structure

| File | Change |
|---|---|
| `static/assets/cedar.png` | Create — copied from handoff `assets/cedar.png` (CANON icon) |
| `static/assets/pussy-willow.png` | Create — copied from handoff `assets/pussy-willow.png` (FLOW icon) |
| `static/assets/birch.png` | Create — copied from handoff `assets/birch.png` (FRAME icon) |
| `static/assets/apiary-hive-logo.png` | Create — copied from handoff `assets/apiary_hive-logo.png` (Apiary Hive icon) |
| `static/css/styles.css` | Modify — add tool-card status badge variants, new tool icon-tint tokens, fix `.tools-cards` grid for 3 cards |
| `layouts/partials/system.html` | Modify — replace the SEEK→MAP→IMPACT flow markup with the 6-card "Our Tools" grid |
| `content/_index.md` | Modify — rewrite `system:` front matter to a `tools:` array; add third Commons card (Apiary Hive) to `open_tools.tools` |
| `content/system.md` | Modify — full front-matter rewrite: flat keys → nested objects, new copy/structure |
| `layouts/system/single.html` | Modify — replace per-tool alternating sections + flow diagram with MAP card + layer-row list |
| `static/css/system.css` | Modify — remove obsolete flow-diagram/tool-mascot/tool-section rules, add layer tokens + row/card styles |

---

### Task 1: Copy new tool icon assets

**Files:**
- Create: `static/assets/cedar.png`
- Create: `static/assets/pussy-willow.png`
- Create: `static/assets/birch.png`
- Create: `static/assets/apiary-hive-logo.png`

**Interfaces:**
- Produces: four image files referenced by `src="/assets/<name>.png"` in Tasks 3 and 7.

- [ ] **Step 1: Copy the four PNGs from the gitignored handoff folder into `static/assets/`**

```bash
cp "design_handoff_tools_reorganization/assets/cedar.png" static/assets/cedar.png
cp "design_handoff_tools_reorganization/assets/pussy-willow.png" static/assets/pussy-willow.png
cp "design_handoff_tools_reorganization/assets/birch.png" static/assets/birch.png
cp "design_handoff_tools_reorganization/assets/apiary_hive-logo.png" static/assets/apiary-hive-logo.png
```

- [ ] **Step 2: Verify the files exist and are non-empty**

```bash
ls -la static/assets/cedar.png static/assets/pussy-willow.png static/assets/birch.png static/assets/apiary-hive-logo.png
```

Expected: all four listed with non-zero size.

- [ ] **Step 3: Commit**

```bash
git add static/assets/cedar.png static/assets/pussy-willow.png static/assets/birch.png static/assets/apiary-hive-logo.png
git commit -m "assets: add icons for CANON, FLOW, FRAME, and Apiary Hive"
```

---

### Task 2: Add new CSS tokens and status-badge variants to `styles.css`

**Files:**
- Modify: `static/css/styles.css:8-27` (the `:root` block) and `static/css/styles.css:568-641` (`.tools-cards` / `.tool-card` / `.tool-tags` region)

**Interfaces:**
- Consumes: existing `--bg-main`, `--text`, `--text-muted`, `--secondary` tokens (already in `:root`, `styles.css:8-27`).
- Produces: `--seek-tint`, `--map-tint`, `--impact-tint`, `--canon-tint`, `--flow-tint`, `--frame-tint` (icon-circle background tints for the homepage tool grid); `.badge-concept`, `.badge-open`, `.badge-almost` classes (new status-badge variants, siblings of the existing `.badge-active`/`.badge-dev` defined in `static/css/system.css:236-256` — these new variants live in `styles.css` because the homepage doesn't load `system.css`); `.our-tools-grid`, `.our-tool-card`, `.our-tool-icon`, `.our-tool-status` classes for the new 6-card grid.

- [ ] **Step 1: Add icon-tint tokens to `:root` in `styles.css`**

Open `static/css/styles.css`, find the `:root` block (lines 8-27), and add after the existing `--tools-color: #5A7A46;` line:

```css
  /* Tool icon tints — homepage "Our Tools" grid */
  --seek-tint:   #DCE4D6; /* matches existing .tool-mascot--seek */
  --map-tint:    #EADFD3; /* matches existing .tool-mascot--map */
  --impact-tint: #E7DADF; /* matches existing .tool-mascot--impact */
  --canon-tint:  #E4EDDB; /* Topography layer tint */
  --flow-tint:   #D8E4EE; /* Infrastructure layer tint */
  --frame-tint:  #EEDAD7; /* Architecture layer tint */
```

- [ ] **Step 2: Add status badge variants**

Find `.tools-cards` (around line 568) in `static/css/styles.css` and add this block immediately before it:

```css
/* ── OUR TOOLS (homepage grid) — status badges ── */
.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  font-family: "Alegreya Sans SC", "Alegreya Sans", sans-serif;
  font-size: 0.65rem;
  letter-spacing: 0.1em;
  padding: 0.3rem 0.75rem;
  border-radius: 20px;
}

.status-badge::before {
  content: "";
  display: inline-block;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  flex-shrink: 0;
}

.badge-active {
  background: rgba(74,107,66,0.1);
  color: #2C3A2A;
  border: 1px solid rgba(74,107,66,0.2);
}
.badge-active::before { background: #4A6B42; box-shadow: 0 0 0 2px rgba(74,107,66,0.15); }

.badge-dev {
  background: rgba(140,110,69,0.1);
  color: #4A3A1A;
  border: 1px solid rgba(140,110,69,0.2);
}
.badge-dev::before { background: #8C6E45; box-shadow: 0 0 0 2px rgba(140,110,69,0.15); }

.badge-concept {
  background: rgba(107,103,96,0.08);
  color: var(--text-muted);
  border: 1px solid rgba(107,103,96,0.18);
}
.badge-concept::before { background: var(--text-light); box-shadow: 0 0 0 2px rgba(107,103,96,0.12); }

.badge-open {
  background: rgba(107,103,96,0.08);
  color: var(--text-muted);
  border: 1px dashed rgba(107,103,96,0.3);
}
.badge-open::before { background: var(--text-light); box-shadow: 0 0 0 2px rgba(107,103,96,0.12); }

.badge-almost {
  background: rgba(107,103,96,0.08);
  color: var(--text-muted);
  border: 1px solid rgba(107,103,96,0.18);
}
.badge-almost::before { background: var(--text-light); box-shadow: 0 0 0 2px rgba(107,103,96,0.12); }
```

Note: `.status-badge`/`.badge-active`/`.badge-dev` are duplicated here (they already exist in `system.css:215-256`) because the homepage loads only `styles.css`, never `system.css`. This is an accepted duplication, not a DRY violation — the two stylesheets never load on the same page.

- [ ] **Step 3: Add the "Our Tools" grid layout classes**

Immediately after the status-badge block from Step 2, still before `.tools-cards`, add:

```css
/* ── OUR TOOLS (homepage grid) — layout ── */
.our-tools-grid {
  display: flex;
  gap: 1.1rem;
  flex-wrap: wrap;
  justify-content: center;
}

.our-tool-card {
  background: rgba(255,253,248,0.7);
  border: 1px solid rgba(0,0,0,0.08);
  border-radius: 8px;
  padding: 1.35rem;
  width: 190px;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.our-tool-icon {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.our-tool-icon img {
  width: 30px;
  height: 30px;
  object-fit: contain;
}

.our-tool-card h3 {
  font-family: "Alegreya", serif;
  font-weight: 500;
  font-size: 1rem;
  margin: 0;
  max-width: none;
}

.our-tool-desc {
  font-size: 0.8rem;
  line-height: 1.5;
  color: var(--text-muted);
  margin: 0;
  max-width: none;
}

.our-tools-more {
  text-align: center;
  margin-top: 1.75rem;
}

@media (max-width: 640px) {
  .our-tool-card { width: 100%; max-width: 260px; }
}
```

- [ ] **Step 4: Fix `.tools-cards` to reflow cleanly with 3 cards**

Find the existing rule (currently `static/css/styles.css:568-572`):

```css
.tools-cards {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.1rem;
}
```

Replace with:

```css
.tools-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1.1rem;
}
```

Leave the existing `@media (max-width: 768px) { .tools-cards { grid-template-columns: 1fr; } }` rule (around line 751) as-is — `auto-fit` with a 260px minimum already collapses to one column on narrow viewports, so the override is now redundant but harmless. Do not delete it; it's out of scope for this task.

- [ ] **Step 5: Verify the build is clean**

```bash
hugo build 2>&1 | grep -iE "error|warn"
```

Expected: no output (CSS changes alone can't break a Hugo build, but confirm nothing else broke).

- [ ] **Step 6: Commit**

```bash
git add static/css/styles.css
git commit -m "style: add homepage tool-grid classes, status badge variants, fix tools-cards reflow"
```

---

### Task 3: Rewrite the homepage "Our Tools" section

**Files:**
- Modify: `layouts/partials/system.html` (entire file — currently the SEEK→MAP→IMPACT flow partial)
- Modify: `content/_index.md:73-109` (the `system:` front-matter block)

**Interfaces:**
- Consumes: `.our-tools-grid`, `.our-tool-card`, `.our-tool-icon`, `.our-tool-desc`, `.status-badge`, `.badge-*` classes from Task 2.
- Produces: renders at `#system` anchor on the homepage, called from `layouts/index.html:11` as `{{ partial "system.html" .Params.system }}` — that call site does not change.

- [ ] **Step 1: Replace `content/_index.md`'s `system:` block**

Open `content/_index.md`. Find the `system:` block (starts at line 73, `system:\n  eyebrow: "Our System"\n...` through the end of the `steps:` array, ending right before `outcomes:`). Replace the entire block with:

```yaml
system:
  eyebrow: "Our Tools"
  title: "One system, a growing set of tools."
  body: "Each tool solves a different part of the same problem — from surfacing engagement, to representing the assets behind it, to making its value legible."
  link_text: "See how it all fits together →"
  link: "system"

  tools:
    - name: "CEnTR*SEEK"
      image: "/assets/fern.png"
      icon_tint: "var(--seek-tint)"
      description: "Classifies institutional text as community-engaged scholarship."
      status_text: "in development"
      status_class: "badge-dev"

    - name: "CEnTR*MAP"
      image: "/assets/goldenrod.png"
      icon_tint: "var(--map-tint)"
      description: "Identifies and relates the community assets a partnership draws on."
      status_text: "in development"
      status_class: "badge-dev"

    - name: "CEnTR*CANON"
      image: "/assets/cedar.png"
      icon_tint: "var(--canon-tint)"
      description: "Turns scattered term maps into a shared definition of the work."
      status_text: "in development"
      status_class: "badge-dev"

    - name: "CEnTR*FLOW"
      image: "/assets/pussy-willow.png"
      icon_tint: "var(--flow-tint)"
      description: "Analyzes the systems, dependencies, and leverage points that carry the work."
      status_text: "concept"
      status_class: "badge-concept"

    - name: "CEnTR*FRAME"
      image: "/assets/birch.png"
      icon_tint: "var(--frame-tint)"
      description: "Shapes how the work is represented, measured, and made visible."
      status_text: "concept"
      status_class: "badge-concept"

    - name: "CEnTR*IMPACT"
      image: "/assets/milkweed.png"
      icon_tint: "var(--impact-tint)"
      description: "Makes community-engaged value legible to funders, P&T committees, and institutions."
      status_text: "actively used"
      status_class: "badge-active"
```

- [ ] **Step 2: Rewrite `layouts/partials/system.html`**

Replace the entire file with:

```go
<section id="system" class="section-bg-main">
  <div class="section-inner">

    <div class="section-sidebar reveal" style="text-align:center;max-width:720px;margin:0 auto 2.5rem;">
      <span class="eyebrow">{{ .eyebrow }}</span>
      <h2>{{ .title }}</h2>
      <p class="sidebar-body">{{ .body }}</p>
    </div>

    <div class="our-tools-grid reveal">
      {{ range .tools }}
      <div class="our-tool-card">
        <div class="our-tool-icon" style="background:{{ .icon_tint }};">
          <img src="{{ .image }}" alt="" />
        </div>
        <h3>{{ .name }}</h3>
        <p class="our-tool-desc">{{ .description | safeHTML }}</p>
        <span class="status-badge {{ .status_class }}">{{ .status_text }}</span>
      </div>
      {{ end }}
    </div>

    {{ if .link }}
    <div class="our-tools-more">
      <a href='{{ .link | relURL }}' class="learn-link">{{ .link_text }}</a>
    </div>
    {{ end }}

  </div>
</section>
```

Note: this drops the old `.section-inner--reverse` / `.section-sidebar` two-column layout in favor of a centered intro + full-width card grid, matching the handoff's "Our Tools" section shape. `.section-inner` and `.section-bg-main` are existing sitewide classes (used by other sections already) — no new CSS needed for them.

- [ ] **Step 3: Build and visually verify**

```bash
hugo build 2>&1 | grep -iE "error|warn"
```

Expected: no output.

```bash
hugo server -D
```

Open `http://localhost:1313/` in a browser, scroll to the "Our Tools" section (`#system`). Confirm: 6 uniform cards (SEEK, MAP, CANON, FLOW, FRAME, IMPACT) in a wrapping row, each with a tinted icon circle, name, one-line description, and status badge; no tool is visually privileged; no Framework-layer language appears anywhere in this section.

- [ ] **Step 4: Commit**

```bash
git add layouts/partials/system.html content/_index.md
git commit -m "feat: replace homepage pipeline section with 6-tool grid"
```

---

### Task 4: Add Apiary Hive to the homepage Commons section

**Files:**
- Modify: `content/_index.md:131-149` (the `open_tools.tools` array)

**Interfaces:**
- Consumes: the existing `layouts/partials/open-tools.html` partial (unmodified — its `{{ range .tools }}` loop and `{{ if .primary_link }}` / `{{ if .secondary_link }}` conditionals already support a variable number of cards and optional links).
- Produces: a third Commons card.

- [ ] **Step 1: Append the Apiary Hive entry**

Open `content/_index.md`, find the `open_tools.tools` array (ends after the `secondary_text: "View on GitHub →"` line for Understory, around line 149, right before `bridge:`). Add a third entry:

```yaml
    - name: "Apiary Hive"
      image: "/assets/apiary-hive-logo.png"
      description: "Gathers Apiary term maps from multiple contributor groups and consolidates them into one canonical vocabulary — the shared input CEnTR*CANON and CEnTR*FLOW both build on."

      tags:
        - "Vocabulary consolidation"
        - "Multi-group aggregation"

      # NOTE: GitHub repo not yet confirmed public as of this reorg — fill in
      # primary_link once available. Do not guess the URL.
      primary_link: ""
      primary_text: "Almost complete →"
```

- [ ] **Step 2: Build and visually verify**

```bash
hugo build 2>&1 | grep -iE "error|warn"
```

Expected: no output.

Run `hugo server -D`, open the homepage, scroll to "The Commons" section. Confirm three cards (Apiary, Understory, Apiary Hive) reflow cleanly at desktop and mobile widths (this is what the `.tools-cards` grid fix from Task 2 Step 4 enables). Confirm the Apiary Hive card shows no broken/dead link — since `primary_link` is empty, the `{{ if .primary_link }}` guard in `open-tools.html` means no link renders at all; the card will show tags but no CTA text. Flag this to the site owner as a follow-up once the repo URL is confirmed.

- [ ] **Step 3: Commit**

```bash
git add content/_index.md
git commit -m "content: add Apiary Hive as third Commons card"
```

---

### Task 5: Rewrite `content/system.md` front matter

**Files:**
- Modify: `content/system.md` (entire front matter — full rewrite, flat keys → nested objects)

**Interfaces:**
- Produces: `.Params.hero`, `.Params.map_spotlight`, `.Params.toolkit`, `.Params.cta` — the exact param names Task 7's template consumes.

- [ ] **Step 1: Replace the entire front matter block**

Open `content/system.md`. Replace everything between the opening `---` and closing `---` with:

```yaml
---
title: "The CEnTR* System"
description: "How CEnTR*SEEK, CEnTR*MAP, CEnTR*CANON, CEnTR*FLOW, CEnTR*FRAME, and CEnTR*IMPACT map onto the Framework's four layers."
layout: "system"
type: "system"
url: "/system/"

hero:
  eyebrow: "The CEnTR* System"
  title: "One system, a growing set of tools."
  body: "The CEnTR* System helps institutions discover engagement, represent community assets with integrity, and understand how that work moves through the deeper layers <a href=\"/framework/\">the Framework</a> describes: culture, systems, and the structures that make it legible. It's one ecosystem, made of tools built for different jobs."

map_spotlight:
  eyebrow: "Spans Every Layer"
  title: "CEnTR*MAP doesn't sit in one layer — it draws on all four."
  body: "Community assets show up everywhere: in the histories a place carries, the culture partners bring, the systems that document contributions, and the representations institutions recognize. MAP traces assets across all of it."
  status_text: "In development"
  status_class: "badge-dev"
  tagline: "Understand and represent engagement with integrity."
  image: "/assets/goldenrod.png"
  description: "Conventional documentation asks what communities lack. MAP asks what they have. Grounded in Asset-Based Community Development, Community Cultural Wealth, and ecological systems thinking, it identifies references to community contributions and maps them to a capital taxonomy — without replacing human interpretation."
  outputs_label: "What MAP produces"
  outputs:
    - "Asset-tagged project records organized by capital type and ecological system level"
    - "Deficit-language flags — where documentation frames communities by need rather than strength"
    - "Asset-centered narrative summaries for funders, accreditors, and leadership"
  link: "centr-map"
  link_text: "Explore CEnTR*MAP →"

toolkit:
  eyebrow: "Framework-Aligned Toolkit"
  title: "Organized by the layer of the work each tool serves."
  body: "Each tool below is built for a layer <a href=\"/framework/\">the Framework</a> describes: how community-engaged work is understood, carried, and made legible."

  rows:
    - layer_name: "Stratigraphy"
      layer_subtitle: "History · Deep Structures"
      layer_class: "strat"
      tool_name: "Understory"
      image: "/assets/log-color.png"
      status_text: "open tool"
      status_class: "badge-open"
      dashed: true
      description: "A multi-layer temporal canvas for mapping how policy, community, and institutional histories have unfolded and intersected — free and open, in <a href=\"/open-tools/\">The Commons</a>."
      link: "https://github.com/CEnTRInnovations/complexity_timeline"
      link_text: "View on GitHub ↗"
      external: true

    - layer_name: "Topography"
      layer_subtitle: "Culture · Meaning"
      layer_class: "topo"
      tool_name: "CEnTR*CANON"
      image: "/assets/cedar.png"
      status_text: "in development"
      status_class: "badge-dev"
      dashed: false
      description: "Turns each contributor group's own term map into shared, canonical vocabulary — then a working definition of community-engaged research the group can stand behind, sourced and reasoned."
      link: ""
      link_text: "Coming soon"
      external: false

    - layer_name: "Infrastructure"
      layer_subtitle: "Systems · Practices"
      layer_class: "infra"
      tool_name: "CEnTR*FLOW"
      image: "/assets/pussy-willow.png"
      status_text: "concept"
      status_class: "badge-concept"
      dashed: false
      description: "Analyzes the systems, practices, dependencies, and leverage points that carry community-engaged work — what moves it, what blocks it, what influences what."
      link: ""
      link_text: "Coming soon"
      external: false

    - layer_name: "Architecture"
      layer_subtitle: "Measures · Representations"
      layer_class: "arch"
      tool_name: "CEnTR*SEEK"
      image: "/assets/fern.png"
      status_text: "in development"
      status_class: "badge-dev"
      dashed: false
      description: "Classifies institutional text as community-engaged scholarship — the first step in making the work visible and legible to institutional systems."
      link: "centr-seek"
      link_text: "Explore →"
      external: false

    - layer_name: "Architecture"
      layer_subtitle: "Measures · Representations"
      layer_class: "arch"
      tool_name: "CEnTR*FRAME"
      image: "/assets/birch.png"
      status_text: "concept"
      status_class: "badge-concept"
      dashed: false
      description: "Shapes how community-engaged work is represented, measured, recognized, and made visible to the systems that decide advancement and funding."
      link: ""
      link_text: "Coming soon"
      external: false

    - layer_name: "Architecture"
      layer_subtitle: "Measures · Representations"
      layer_class: "arch"
      tool_name: "CEnTR*IMPACT"
      image: "/assets/milkweed.png"
      status_text: "actively used"
      status_class: "badge-active"
      dashed: false
      description: "An ensemble of four complementary score types that make community-engaged value legible to promotion & tenure committees, funders, and accreditors — a fuller story than any single metric."
      link: "centr-impact"
      link_text: "Explore →"
      external: false

cta:
  title: "Ready to apply the system in your context?"
  body: "If your institution is ready to move from fragmented documentation to coherent infrastructure for community-engaged scholarship, we'd be glad to talk."
  button_link: "https://calendly.com/centrinnovations/45min"
  button_text: "Book Time with Jeremy"
  secondary_link: "framework"
  secondary_text: "View the Framework"
---
```

This is the full replacement for the file's front matter; the file has no body content below the front matter, so nothing else in `content/system.md` changes.

- [ ] **Step 2: Verify the YAML parses**

```bash
hugo build 2>&1 | grep -iE "error|warn"
```

Expected: at this point in the plan, the build will show errors/missing-output on `/system/`, because `layouts/system/single.html` (Task 7) still references the old flat params (`.Params.hero_eyebrow`, `.Params.seek_body`, etc.) which no longer exist. That's expected — this task only lands the content; Task 7 lands the template that consumes it. Confirm specifically that the error is about missing/nil params on the system page, not a YAML syntax error (a YAML syntax error would show as a front-matter parse failure naming `content/system.md` directly).

- [ ] **Step 3: Commit**

```bash
git add content/system.md
git commit -m "content: rewrite system.md front matter to nested schema, layer-grouped toolkit"
```

---

### Task 6: Rewrite `static/css/system.css` for the new layout

**Files:**
- Modify: `static/css/system.css` — remove `static/css/system.css:1-11` (old `--seek-mid`/`--map-mid`/`--impact-mid` root block, will be replaced with a richer one), remove the "SHARED TOOL SECTION LAYOUT" through "BOTANICAL FLOW DIAGRAM" / "TOOL MASCOTS" regions (`static/css/system.css:83` through the `.tool-mascot img` rule, roughly lines 83-410 depending on exact old content — the sidebar/content/outputs/transition/flow-diagram/mascot rules), keep the hero, connector-intro-adjacent structural rules, status badges, and responsive block (updating selectors as needed).

**Interfaces:**
- Consumes: nothing new — self-contained CSS file.
- Produces: `.map-spotlight-card`, `.map-spotlight-icon`, `.strata-icon` (SVG wrapper), `.toolkit-row`, `.toolkit-row--dashed`, `.toolkit-layer-block`, `.toolkit-tool-icon`, `.toolkit-tool-body` — classes Task 7's template will use. Layer color tokens: `--strat-mid`, `--strat-bg`, `--topo-mid`, `--topo-bg`, `--infra-mid`, `--infra-bg`, `--arch-mid`, `--arch-bg` (values copied from `static/css/framework.css:6-25`, duplicated here because `system.css` and `framework.css` never load on the same page).

- [ ] **Step 1: Replace the file's `:root` block and remove obsolete sections**

Open `static/css/system.css`. Replace the top `:root` block (currently lines 1-11):

```css
/* Tool accent colors — drawn from individual tool palettes */
:root {
  --seek-mid:    #2E6E78;
  --map-mid:     #7A5C1E;
  --impact-mid:  #3F5E78;
}
```

with:

```css
/* Tool accent colors — drawn from individual tool palettes */
:root {
  --seek-mid:    #2E6E78;
  --map-mid:     #7A5C1E;
  --impact-mid:  #3F5E78;

  /* Framework layer colors — copied from framework.css; duplicated because
     system.css and framework.css never load on the same page. */
  --strat-deep:  #2C2417;
  --strat-mid:   #5C4A2A;
  --strat-bg:    #EDE0CC;

  --topo-deep:   #3A4D2A;
  --topo-mid:    #5A7A46;
  --topo-bg:     #E4EDDB;

  --infra-deep:  #2A3D52;
  --infra-mid:   #3F5E78;
  --infra-bg:    #D8E4EE;

  --arch-deep:   #4A2A3A;
  --arch-mid:    #7A4A62;
  --arch-bg:     #EEDAD7;
}
```

Now delete these now-obsolete regions entirely (search for the comment headers and delete from that header through the rule just before the next surviving header):
- `/* ── SHARED TOOL SECTION LAYOUT ── */` through `/* ── SECTION BACKGROUNDS ── */` (inclusive of `.system-tool-section`, `.system-section-inner`, `.system-section-inner--reverse`, `.tool-num`, `.tool-lead`, `.tool-stripe` + color variants, `.sidebar-body`, `.system-tool-content`, `.tool-body`, `.tool-outputs`, `.outputs-label`, `.outputs-list`, `.tool-page-link` + color variants, `.system-seek`, `.system-map`, `.system-impact`)
- `/* ── TRANSITION STRIPS ── */` through the end of `.transition-body`
- `/* ── IMPACT COLLAGE ── */` through the end of `.impact-score-card p`, `.viz-note` (this page no longer has an inline IMPACT section — the IMPACT row lives in `centr-impact.md`'s own page, unaffected by this reorg)
- `/* ── LIGHTBOX ── */` through `.viz-lightbox-close:hover`
- `/* ── BOTANICAL FLOW DIAGRAM ── */` through `/* ── TOOL MASCOTS ── */` and `.tool-mascot img`

Keep: the `/* ── HERO ── */` block, `/* ── CONNECTOR INTRO ── */` block (will be repurposed for the "Spans Every Layer" intro in Step 2), the `/* ── STATUS BADGES ── */` block, and the `/* ── RESPONSIVE ── */` block (will be trimmed in Step 3).

- [ ] **Step 2: Add badge variants and the MAP spotlight card styles**

After the existing `/* ── STATUS BADGES ── */` block (`.status-badge`, `.status-badge::before`, `.badge-active`, `.badge-dev`), add the missing variants and the new component styles:

```css
.badge-concept {
  background: rgba(107,103,96,0.08);
  color: #6b6760;
  border: 1px solid rgba(107,103,96,0.18);
}
.badge-concept::before { background: #8A867E; box-shadow: 0 0 0 2px rgba(107,103,96,0.12); }

.badge-open {
  background: rgba(107,103,96,0.08);
  color: #6b6760;
  border: 1px dashed rgba(107,103,96,0.3);
}
.badge-open::before { background: #8A867E; box-shadow: 0 0 0 2px rgba(107,103,96,0.12); }

.badge-almost {
  background: rgba(107,103,96,0.08);
  color: #6b6760;
  border: 1px solid rgba(107,103,96,0.18);
}
.badge-almost::before { background: #8A867E; box-shadow: 0 0 0 2px rgba(107,103,96,0.12); }

/* ── MAP SPOTLIGHT (spans every layer) ── */
.map-spotlight {
  background: var(--bg-main, #F6F2E7);
}

.map-spotlight .system-page-inner {
  padding-top: 1.5rem;
  padding-bottom: 4.5rem;
}

.map-spotlight h2 {
  max-width: 640px;
  font-size: 1.5rem;
  margin-bottom: 0.6rem;
}

.map-spotlight-intro {
  font-size: 0.92rem;
  color: var(--text-muted, #6b6760);
  max-width: 680px;
  margin-bottom: 2rem;
  line-height: 1.65;
}

.map-spotlight-card {
  background: white;
  border: 1px solid rgba(0,0,0,0.08);
  border-radius: 8px;
  padding: 2rem;
  display: flex;
  gap: 1.5rem;
  max-width: 1180px;
  margin: 0 auto;
}

.map-spotlight-icon-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.65rem;
  flex-shrink: 0;
}

.map-spotlight-icon {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: var(--map-tint, #EADFD3);
  display: flex;
  align-items: center;
  justify-content: center;
}

.map-spotlight-icon img {
  width: 40px;
  height: 40px;
  object-fit: contain;
}

.map-spotlight-body { flex: 1; }

.map-spotlight-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 0.4rem;
}

.map-spotlight-header h3 {
  font-family: "Alegreya", serif;
  font-size: 1.35rem;
  font-weight: 500;
  margin: 0;
  max-width: none;
}

.map-spotlight-tagline {
  font-family: "Alegreya", serif;
  font-style: italic;
  font-size: 0.9rem;
  color: var(--text-muted, #6b6760);
  margin-bottom: 0.9rem;
}

.map-spotlight-desc {
  font-size: 0.92rem;
  line-height: 1.65;
  color: var(--text, #3E3B35);
  max-width: none;
  margin-bottom: 1rem;
}

/* ── STRATA ICON (used by map-spotlight and each toolkit row) ── */
.strata-icon rect { transition: none; }

/* ── FRAMEWORK-ALIGNED TOOLKIT ── */
.toolkit-section {
  background: var(--bg-light, #F4EFE2);
}

.toolkit-section h2 {
  max-width: 700px;
  font-size: 1.6rem;
  margin-bottom: 0.6rem;
}

.toolkit-intro {
  font-size: 0.92rem;
  color: var(--text-muted, #6b6760);
  max-width: 700px;
  margin-bottom: 2.5rem;
  line-height: 1.65;
}

.toolkit-rows {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 1180px;
  margin: 0 auto;
}

.toolkit-row {
  background: white;
  border: 1px solid rgba(0,0,0,0.08);
  border-radius: 8px;
  padding: 1.4rem 1.6rem;
  display: flex;
  align-items: center;
  gap: 1.75rem;
}

.toolkit-row--dashed {
  border-style: dashed;
  background: rgba(255,255,255,0.5);
}

.toolkit-layer-block {
  width: 150px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.toolkit-layer-label {
  font-family: "Alegreya Sans SC", "Alegreya Sans", sans-serif;
  font-size: 0.62rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.toolkit-layer-name {
  font-family: "Alegreya", serif;
  font-size: 1.05rem;
  font-weight: 500;
}

.toolkit-layer-subtitle {
  font-size: 0.72rem;
  color: var(--text-muted, #6b6760);
}

.toolkit-row.strat .toolkit-layer-label,
.toolkit-row.strat .toolkit-layer-name { color: var(--strat-mid); }
.toolkit-row.topo .toolkit-layer-label,
.toolkit-row.topo .toolkit-layer-name { color: var(--topo-mid); }
.toolkit-row.infra .toolkit-layer-label,
.toolkit-row.infra .toolkit-layer-name { color: var(--infra-mid); }
.toolkit-row.arch .toolkit-layer-label,
.toolkit-row.arch .toolkit-layer-name { color: var(--arch-mid); }

.toolkit-divider {
  width: 1px;
  align-self: stretch;
  background: rgba(0,0,0,0.08);
  flex-shrink: 0;
}

.toolkit-tool-icon {
  width: 52px;
  height: 52px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.toolkit-tool-icon img {
  width: 36px;
  height: 36px;
  object-fit: contain;
}

.toolkit-tool-body {
  flex: 1;
  min-width: 0;
}

.toolkit-tool-header {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  margin-bottom: 0.3rem;
}

.toolkit-tool-header strong {
  font-family: "Alegreya", serif;
  font-size: 1.02rem;
  font-weight: 500;
}

.toolkit-tool-desc {
  font-size: 0.84rem;
  line-height: 1.55;
  color: var(--text-muted, #6b6760);
  max-width: none;
  margin: 0;
}

.toolkit-link {
  font-size: 0.82rem;
  font-weight: 500;
  white-space: nowrap;
  flex-shrink: 0;
}

.toolkit-link--muted {
  color: var(--text-light, #8A867E);
}
```

- [ ] **Step 3: Update the responsive block**

Find `/* ── RESPONSIVE ── */` at the bottom of the file. Replace its contents (which currently reference deleted classes like `.system-section-inner`, `.flow-connector`, `.tool-mascot`) with:

```css
@media (max-width: 960px) {
  .system-page-inner {
    padding: 3.5rem 1.25rem;
  }

  .system-page-hero-inner {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .system-page-hero h1 {
    font-size: 2.2rem;
  }

  .map-spotlight-card {
    flex-direction: column;
  }

  .map-spotlight-icon-col {
    flex-direction: row;
  }

  .toolkit-row {
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
  }

  .toolkit-layer-block {
    width: auto;
  }

  .toolkit-divider {
    display: none;
  }

  .toolkit-link {
    align-self: flex-start;
  }
}
```

- [ ] **Step 4: Verify no leftover references to deleted classes**

```bash
grep -n "system-tool-section\|system-section-inner\|tool-mascot\|flow-circle\|flow-node\|flow-connector\|impact-score-card\|viz-lightbox" static/css/system.css
```

Expected: no output (confirms the deleted regions from Step 1 are fully gone and don't leave dangling partial rules).

- [ ] **Step 5: Commit**

```bash
git add static/css/system.css
git commit -m "style: rebuild system.css for MAP spotlight + layer-grouped toolkit rows"
```

---

### Task 7: Rewrite `layouts/system/single.html`

**Files:**
- Modify: `layouts/system/single.html` (entire file)

**Interfaces:**
- Consumes: `.Params.hero`, `.Params.map_spotlight`, `.Params.toolkit`, `.Params.cta` from `content/system.md` (Task 5). Consumes `.map-spotlight-*`, `.toolkit-*`, `.status-badge`/`.badge-*` classes from `system.css` (Task 6).
- Produces: the full rendered `/system/` page.

- [ ] **Step 1: Replace the entire file**

```go
{{ define "main" }}

<!-- Hero -->
<section class="system-page-hero">
  <div class="system-page-inner">
    <span class="eyebrow">{{ .Params.hero.eyebrow }}</span>
    <h1>{{ .Params.hero.title }}</h1>
    <p class="system-page-lead">{{ .Params.hero.body | safeHTML }}</p>
  </div>
</section>

<!-- MAP: spans every layer -->
<section class="map-spotlight">
  <div class="system-page-inner">
    <span class="eyebrow">{{ .Params.map_spotlight.eyebrow }}</span>
    <h2>{{ .Params.map_spotlight.title }}</h2>
    <p class="map-spotlight-intro">{{ .Params.map_spotlight.body }}</p>

    <div class="map-spotlight-card reveal">
      <div class="map-spotlight-icon-col">
        <div class="map-spotlight-icon">
          <img src="{{ .Params.map_spotlight.image }}" alt="">
        </div>
        <svg class="strata-icon" width="22" height="40" viewBox="0 0 22 40">
          <rect x="0" y="0"  width="22" height="8" rx="1.5" fill="var(--arch-mid)"/>
          <rect x="0" y="10" width="22" height="8" rx="1.5" fill="var(--infra-mid)"/>
          <rect x="0" y="20" width="22" height="8" rx="1.5" fill="var(--topo-mid)"/>
          <rect x="0" y="30" width="22" height="8" rx="1.5" fill="var(--strat-mid)"/>
        </svg>
      </div>
      <div class="map-spotlight-body">
        <div class="map-spotlight-header">
          <h3>CEnTR*MAP</h3>
          <span class="status-badge {{ .Params.map_spotlight.status_class }}">{{ .Params.map_spotlight.status_text }}</span>
        </div>
        <p class="map-spotlight-tagline">{{ .Params.map_spotlight.tagline }}</p>
        <p class="map-spotlight-desc">{{ .Params.map_spotlight.description }}</p>
        <span class="eyebrow">{{ .Params.map_spotlight.outputs_label }}</span>
        <ul class="outputs-list">
          {{ range .Params.map_spotlight.outputs }}
          <li>{{ . }}</li>
          {{ end }}
        </ul>
        <a class="tool-page-link" href="{{ .Params.map_spotlight.link | relURL }}">{{ .Params.map_spotlight.link_text }}</a>
      </div>
    </div>
  </div>
</section>

<!-- Framework-aligned toolkit -->
<section class="toolkit-section">
  <div class="system-page-inner">
    <span class="eyebrow">{{ .Params.toolkit.eyebrow }}</span>
    <h2>{{ .Params.toolkit.title }}</h2>
    <p class="toolkit-intro">{{ .Params.toolkit.body | safeHTML }}</p>

    <div class="toolkit-rows">
      {{ range .Params.toolkit.rows }}
      <div class="toolkit-row {{ .layer_class }}{{ if .dashed }} toolkit-row--dashed{{ end }} reveal">
        <div class="toolkit-layer-block">
          <svg width="22" height="40" viewBox="0 0 22 40">
            <rect x="0" y="0"  width="22" height="8" rx="1.5" fill="{{ if eq .layer_class "arch"  }}var(--arch-mid){{ else }}#e5ded0{{ end }}"/>
            <rect x="0" y="10" width="22" height="8" rx="1.5" fill="{{ if eq .layer_class "infra" }}var(--infra-mid){{ else }}#e5ded0{{ end }}"/>
            <rect x="0" y="20" width="22" height="8" rx="1.5" fill="{{ if eq .layer_class "topo"  }}var(--topo-mid){{ else }}#e5ded0{{ end }}"/>
            <rect x="0" y="30" width="22" height="8" rx="1.5" fill="{{ if eq .layer_class "strat" }}var(--strat-mid){{ else }}#e5ded0{{ end }}"/>
          </svg>
          <div>
            <div class="toolkit-layer-label">Layer</div>
            <div class="toolkit-layer-name">{{ .layer_name }}</div>
            <div class="toolkit-layer-subtitle">{{ .layer_subtitle }}</div>
          </div>
        </div>

        <div class="toolkit-divider"></div>

        <div class="toolkit-tool-icon" style="background:var(--{{ .layer_class }}-bg);">
          <img src="{{ .image }}" alt="">
        </div>

        <div class="toolkit-tool-body">
          <div class="toolkit-tool-header">
            <strong>{{ .tool_name }}</strong>
            <span class="status-badge {{ .status_class }}">{{ .status_text }}</span>
          </div>
          <p class="toolkit-tool-desc">{{ .description | safeHTML }}</p>
        </div>

        {{ if .link }}
          <a class="toolkit-link" href="{{ if .external }}{{ .link }}{{ else }}{{ .link | relURL }}{{ end }}"{{ if .external }} target="_blank" rel="noopener"{{ end }}>{{ .link_text }}</a>
        {{ else }}
          <span class="toolkit-link toolkit-link--muted">{{ .link_text }}</span>
        {{ end }}
      </div>
      {{ end }}
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta">
  <div class="cta-inner">
    <h2>{{ .Params.cta.title }}</h2>
    <p>{{ .Params.cta.body }}</p>
    <a href="{{ .Params.cta.button_link }}" class="button primary" target="_blank" rel="noopener">{{ .Params.cta.button_text }}</a>
    <div style="margin-top:1.25rem;">
      <a href="{{ .Params.cta.secondary_link | relURL }}" class="button secondary">{{ .Params.cta.secondary_text }}</a>
    </div>
  </div>
</section>

{{ end }}
```

Note on `var(--{{ .layer_class }}-bg)`: Hugo string interpolation inside an inline `style` attribute produces literal CSS text like `background:var(--strat-bg);` — this works because `--strat-bg`, `--topo-bg`, `--infra-bg`, `--arch-bg` are real custom properties defined in `system.css` (Task 6, Step 1) and `.layer_class` values (`strat`/`topo`/`infra`/`arch`) match those suffixes exactly by construction in Task 5's front matter.

- [ ] **Step 2: Build and check for template errors**

```bash
hugo build 2>&1 | grep -iE "error|warn"
```

Expected: no output. If you see a nil-pointer error mentioning `.Params.hero.eyebrow` or similar, confirm Task 5 was committed and `content/system.md` has the nested `hero:` block, not the old flat `hero_eyebrow:` key.

- [ ] **Step 3: Visually verify in the browser**

```bash
hugo server -D
```

Open `http://localhost:1313/system/`. Confirm, top to bottom:
1. Hero renders left-aligned with eyebrow, title, body.
2. "Spans Every Layer" section shows one card for CEnTR*MAP with a 4-band strata icon (all 4 bands colored) and an "In development" badge.
3. "Framework-Aligned Toolkit" section shows 6 rows in this order: Understory (Stratigraphy, dashed border, "open tool" badge) → CEnTR*CANON (Topography) → CEnTR*FLOW (Infrastructure) → CEnTR*SEEK (Architecture) → CEnTR*FRAME (Architecture) → CEnTR*IMPACT (Architecture). Each row's strata icon highlights only that row's layer band in that layer's accent color.
4. CTA renders with both buttons working (Calendly link opens in new tab, Framework link is internal).
5. Resize the browser to ~600px wide: toolkit rows stack vertically without overlapping text; the MAP spotlight card stacks its icon column above the body.

- [ ] **Step 4: Commit**

```bash
git add layouts/system/single.html
git commit -m "feat: rebuild system page with MAP spotlight and layer-grouped toolkit"
```

---

### Task 8: Full-site verification pass

**Files:** none (verification only)

**Interfaces:** none

- [ ] **Step 1: Full clean build**

```bash
hugo build 2>&1 | grep -iE "error|warn"
```

Expected: no output.

- [ ] **Step 2: Confirm no other page references the removed pipeline sections**

```bash
grep -rln "system-tool-section\|flow-circle\|tool-mascot\|system-flow" layouts/ content/
```

Expected: no output (nothing outside the files already changed in Tasks 6-7 referenced these classes).

- [ ] **Step 3: Browser walkthrough of both changed pages plus one unrelated page**

Run `hugo server -D` and check:
- `/` — hero through footer, focusing on "Our Tools" (6 cards) and "The Commons" (3 cards); confirm no Framework-layer vocabulary appears anywhere on the page.
- `/system/` — full page per Task 7 Step 3's checklist.
- `/framework/` — spot-check that this page (untouched by this plan) still renders correctly, since Task 6 duplicated its color tokens into `system.css` rather than modifying `framework.css`.

- [ ] **Step 4: Confirm internal links resolve**

```bash
hugo build 2>&1 | grep -i "REF_NOT_FOUND\|404"
```

Expected: no output. (Hugo doesn't hard-fail on broken relURL targets by default, so this catches anything `hugo build`'s own error/warn stream would otherwise miss.)

- [ ] **Step 5: Final commit if any cleanup was needed**

If Steps 1-4 required fixes, commit them individually with descriptive messages as usual. If everything passed clean, no commit needed for this task.

---

## Self-Review Notes

- **Spec coverage:** Homepage nav (unchanged, already matches), hero/challenge/outcomes/bridge/cta (unchanged, already matched the handoff), Our Tools grid (Task 3), Commons third card (Task 4), System page hero/MAP-spotlight/toolkit-rows/CTA (Tasks 5, 7), status badge vocabulary for all 5 states (Tasks 2, 6), strata SVG icons (Task 7), layer accent colors (Task 6), asset sourcing (Task 1), flat→nested front-matter migration (Task 5) all have tasks. Mobile/responsive reflow — no breakpoints were specified in the original handoff for the new sections; Tasks 2, 6, and 7 add minimal reflow rules (flex-wrap / stacking) consistent with the rest of the site's existing responsive patterns, since the handoff explicitly flagged responsive layout as out of scope for that round.
- **Open item, not resolved by this plan:** Apiary Hive's GitHub link (Task 4) is intentionally left blank per the handoff's own caveat that the repo's public status wasn't confirmed. Surface this to the user as a follow-up once they've verified the URL.
