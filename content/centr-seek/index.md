---
title: "CEnTR*SEEK: Making Engagement Visible"
description: "Identify, classify, and surface community-engaged research from unstructured institutional text, without relying on self-reporting."
layout: "seek"
type: "seek"

blocks:
  - block: "hero"
  - block: "context"
  - block: "seek-pipeline"
  - block: "seek-transparency"
  - block: "seek-outputs"
#  - block: "seek-field"
  - block: "cta"

# ─────────────────────────────────────────
# HERO
# ─────────────────────────────────────────
hero_section_class: "seek-hero"
hero_botanical: "assets/fern.png"
hero_botanical_alt: "Botanical illustration of a fern with exposed root system"
hero_quote: "Finding what's already there, without asking anyone to report it."
hero_quote_class: ""

hero_eyebrow: "The CEnTR* System"
hero_title: "CEnTR*SEEK"
hero_lead_1: "Community-engaged research is happening across your institution right now. Most of it is invisible, distributed across websites, reports, course descriptions, and publications that were never designed with discoverability in mind."
hero_lead_2: "CEnTR*SEEK reads that text and finds the engagement. No self-reporting. No siloed databases. No additional burden on faculty, staff, or partners."

hero_strip:
  - name: "Sources"
    label: "Collect Institutional Text"
    icon: "/assets/icons/pile.png"
    icon_class: "seek-icon--ingest"
    anchor: "pipeline"
  - name: "Signals"
    label: "Detect Engagement"
    icon: "/assets/icons/lantern.png"
    icon_class: "seek-icon--analyze"
    anchor: "pipeline"
  - name: "Patterns"
    label: "Classify & Structure"
    icon: "/assets/icons/patterns.png"
    icon_class: "seek-icon--pattern"
    anchor: "pipeline"
  - name: "Understanding"
    label: "Structured Outputs"
    icon: "/assets/icons/report.png"
    icon_class: "seek-icon--surface"
    anchor: "outputs"

# ─────────────────────────────────────────
# CONTEXT
# ─────────────────────────────────────────
context_section_class: "seek-context"
context_stripe_class: "seek-stripe"
context_callout_class: "seek-callout"

context_eyebrow: "The Problem"
context_title: "You can't coordinate what you can't see."
context_sidebar_1: "Community engagement offices, centers for public service, and evaluation teams face the same problem: the engaged work happening across their institution is nearly impossible to see in full."
context_sidebar_2: "Faculty and staff may be conducting meaningful community partnerships without those efforts appearing in any central record. Strategic coordination — connecting academic resources to community-identified needs — depends on knowing where engagement is already occurring, and where the gaps are."
context_callout: "CEnTR*SEEK doesn't ask people to report their work. It finds the work in text that already exists."
context_body_1: "Traditional approaches rely on self-reporting, keyword searches, or manual review, all of which systematically miss work that doesn't describe itself in the expected terms. Engaged scholarship often uses different language than traditional research, and the communities it serves rarely appear in the databases institutions use to measure impact."
context_body_2: "CEnTR*SEEK transforms dispersed institutional text into structured representations of engagement, giving institutions a comprehensive, accurate picture of their community-engaged landscape without creating new administrative burden."

# ─────────────────────────────────────────
# PIPELINE
# ─────────────────────────────────────────
pipeline_eyebrow: "How It Works"
pipeline_title: "From sources to understanding, a modular pipeline for institutional text."
pipeline_sidebar_1: "CEnTR*SEEK is designed as a modular, extensible system capable of operating at institutional scale. Its components can be independently updated or replaced, allowing it to evolve as needs change."
pipeline_sidebar_2: "The pipeline can begin with a corpus of documents or a root URL, from which it recursively crawls and extracts relevant content while filtering out non-substantive material."

pipeline_steps:
  - title: "Sources"
    body: "Accepts file-based inputs — PDFs, CSVs, structured text — or a root URL from which the system crawls institutional domains, extracting content with metadata while respecting rate limits and robots.txt. Transformer-based embeddings capture meaning beyond keyword matching, recognizing engagement even when it does not use expected vocabulary."
    icon: "/assets/icons/pile.png"
    class: "step-sources"
  - title: "Signals"
    body: "The system reads extracted text for indicators of community engagement: language of partnership, reciprocity, community voice, and shared purpose. Because engaged scholarship often describes itself in terms that differ from traditional research, signal detection operates on meaning rather than keywords alone."
    icon: "/assets/icons/lantern.png"
    class: "step-signals"
  - title: "Patterns"
    body: "A combination of machine learning models and rule-based logic assesses engagement across five dimensions: Partnership and Power, Community Voice, Process and Methods, Outcomes and Impacts, and Sustainability. Every classification includes highlighted excerpts and plain-language rationales that explain how the determination was made."
    icon: "/assets/icons/patterns.png"
    class: "step-patterns"
  - title: "Understanding"
    body: "Structured JSON objects include classification labels, confidence scores, and supporting excerpts, designed for interoperability with CEnTR*MAP and CEnTR*IMPACT, and for translation into human-readable summaries for researchers, administrators, and community partners."
    icon: "/assets/icons/report.png"
    class: "step-understand"

# ─────────────────────────────────────────
# TRANSPARENCY
# ─────────────────────────────────────────
transparency_eyebrow: "A Design Commitment"
transparency_title: "Transparency over opacity. Partnership over prescription."
transparency_sidebar_1: "A defining feature of CEnTR*SEEK is its commitment to interpretability. In community-engaged contexts, trust and accountability are foundational, an opaque system that produces classifications without explanation is incompatible with those values."
transparency_sidebar_2: "Every output includes not only a classification and confidence score but highlighted excerpts and plain-language rationales that explain how the determination was made. The system is designed as an analytical partner that invites human review."
transparency_quote: "CEnTR*SEEK is not an opaque judge. It is an analytical partner, one that shows its work and invites the humans closest to the community to interpret what it finds."

# ─────────────────────────────────────────
# OUTPUTS
# ─────────────────────────────────────────
outputs_eyebrow: "What Becomes Possible"
outputs_title: "From invisible to legible, at institutional scale."

outputs_cards:
  - title: "Surface Hidden Work"
    body: "Identify faculty and staff doing community-engaged work who are not yet connected to institutional collaborative structures, including work that falls outside traditional scholarly channels."
    class: "card-ingest"
  - title: "Reveal Patterns"
    body: "Surface engagement patterns across departments, neighborhoods, or partner types to inform strategic coordination and resource allocation, without waiting for annual surveys."
    class: "card-analyze"
  - title: "Support Documentation"
    body: "Generate structured data from existing institutional text that supports evaluation, accreditation, and reporting, reducing the documentation burden on researchers and partners."
    class: "card-surface"
  - title: "Demonstrate Scope"
    body: "Make the full landscape of institutional engagement legible to funders, accreditors, and leadership, in terms that reflect what the work actually is, not just what gets formally reported."
    class: "card-ingest"

# ─────────────────────────────────────────
# FIELD INFRASTRUCTURE (currently disabled in blocks)
# ─────────────────────────────────────────
field_eyebrow: "Beyond the Institution"
field_title: "Infrastructure for a field, not just a campus."
field_sidebar_1: "Across higher education, community-engaged work is documented in heterogeneous formats across disconnected systems, making it difficult to aggregate, compare, or learn from at scale."
field_sidebar_2: "CEnTR*SEEK creates the conditions for interoperability: a common pipeline for identifying and structuring engagement data that can work across institutional contexts, tracing the evolution of engagement practices and supporting coordinated learning while preserving local context and community voice."
field_quote: "When institutions can see their own engagement clearly, the field can begin to see itself."

# ─────────────────────────────────────────
# CTA
# ─────────────────────────────────────────
cta_title: "Ready to see what's already there?"
cta_body: "CEnTR*SEEK is in active development. If your institution is interested in piloting the system or contributing to its design, we'd like to talk."
cta_primary_text: "Book Time with Jeremy"
cta_primary_url: "https://outlook.office.com/bookwithme/user/93badc8cbff54115aab9a542fbea0fdf@iu.edu?anonymous&ismsaljsauthenabled&ep=pcard"
cta_secondary_text: "Learn About CEnTR*IMPACT"
cta_secondary_url: "/centr-impact/"
---