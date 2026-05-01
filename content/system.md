---
title: "The CEnTR* System"
description: "An integrated overview of CEnTR*SEEK, CEnTR*MAP, and CEnTR*IMPACT."
layout: "system"
type: "system"
url: "/system/"

# ─────────────────────────────────────────
# HERO
# ─────────────────────────────────────────
hero_eyebrow: "The CEnTR* System"
hero_title: "Three connected tools.<br>One coherent infrastructure for community-engaged scholarship."
hero_body: "The CEnTR* System helps institutions discover engagement, represent it with integrity, and demonstrate its value in ways communities and institutions can trust. Each tool can stand alone. Together, they form a full workflow for making engagement visible, actionable, and sustainable."

# ─────────────────────────────────────────
# CONNECTOR — intro to the three tools
# ─────────────────────────────────────────
connector_eyebrow: "How the System Works"
connector_title: "The sequence is practical. The relationship is iterative."
connector_body_1: "SEEK surfaces engagement that is already happening but not yet visible. MAP documents what communities are contributing to that engagement — centering assets, not deficits. IMPACT demonstrates the value of what the work produces in terms that travel across institutional contexts."
connector_body_2: "The tools are designed to feed each other. SEEK's structured outputs become the starting point for MAP's asset documentation. MAP's representations of partnership quality inform what IMPACT is asked to measure. And IMPACT's evidence — of what works, where, and why — strengthens the case for the engagement that SEEK is still finding."

# ─────────────────────────────────────────
# SEEK SECTION
# ─────────────────────────────────────────
seek_eyebrow: "Tool One"
seek_title: "CEnTR*SEEK"
seek_lead: "Make engagement visible."
seek_status: "In Development"
seek_status_class: "badge-dev"

seek_sidebar_1: "Community-engaged work is happening across your institution right now. Most of it is invisible — distributed across websites, reports, course descriptions, and publications that were never designed with discoverability in mind."
seek_sidebar_2: "CEnTR*SEEK reads that text and finds the engagement — without requiring faculty or staff to self-report, and without relying on keyword searches that miss work that doesn't describe itself in the expected terms."

seek_body: "SEEK is the system's entry point. It ingests institutional text from multiple sources and processes it through a modular pipeline: preprocessing and named entity recognition, transformer-based embedding, and multi-dimensional classification across five dimensions — Partnership and Power, Community Voice, Process and Methods, Outcomes and Impacts, and Sustainability."
seek_body_2: "Every output includes not just a classification and confidence score but highlighted excerpts and plain-language rationales. The system is designed as an analytical partner that invites human review — not an opaque judge that produces verdicts."

seek_outputs_label: "What SEEK produces"
seek_outputs:
  - "Structured engagement records with classification labels and confidence scores"
  - "Named entities — faculty, partners, neighborhoods, organizations — anchored to the text"
  - "Supporting excerpts that explain how each determination was made"
  - "A dataset ready for import into CEnTR*MAP and CEnTR*IMPACT"

seek_link: "centr-seek"
seek_link_text: "Explore CEnTR*SEEK →"

seek_into_map: "SEEK's structured outputs — engagement records tagged by dimension, partner, and location — become the raw material that MAP organizes into an asset-based picture of what communities are contributing."

# ─────────────────────────────────────────
# MAP SECTION
# ─────────────────────────────────────────
map_eyebrow: "Tool Two"
map_title: "CEnTR*MAP"
map_lead: "Understand and represent engagement with integrity."
map_status: "In Development"
map_status_class: "badge-dev"

map_sidebar_1: "Conventional documentation asks what communities lack. CEnTR*MAP asks what they have. Grounded in Asset-Based Community Development, Community Cultural Wealth, and ecological systems thinking, it transforms what gets documented, how it is organized, and what insights become possible."
map_sidebar_2: "MAP can work from existing textual artifacts — interview transcripts, project reports, research memos — or from SEEK's structured outputs. Narrative is not merely an interface feature. It is a foundational data source that can be revisited, reinterpreted, and built upon over time."

map_body: "MAP organizes its capital taxonomy within a nested ecological systems model — situating assets from the deeply personal to the broadly historical. Familial and linguistic capital. Resistance capital and historical heritage. The full range of what Yosso's Community Cultural Wealth framework makes legible, structured so that what gets documented reflects the depth and diversity of community strength."
map_body_2: "AI-assisted processing identifies references to community contributions across texts and maps them to the capital taxonomy — but never replaces human interpretation. The system surfaces connections and gaps while users maintain control over how their work and their partners are represented."

map_outputs_label: "What MAP produces"
map_outputs:
  - "Asset-tagged project records organized by capital type and ecological system level"
  - "Structured datasets supporting flexible querying and visualization over time"
  - "Deficit language flags — identifying where existing documentation frames communities in terms of need rather than strength"
  - "Asset-centered narrative summaries for funders, accreditors, and leadership"

map_link: "centr-map"
map_link_text: "Explore CEnTR*MAP →"

map_into_impact: "MAP's asset-tagged records and partnership quality data give IMPACT the context it needs to measure not just what a project produced, but how equitably it was pursued and how deeply community priorities shaped the work."

# ─────────────────────────────────────────
# IMPACT SECTION
# ─────────────────────────────────────────
impact_eyebrow: "Tool Three"
impact_title: "CEnTR*IMPACT"
impact_lead: "Make value legible."
impact_status: "Actively Used"
impact_status_class: "badge-active"

impact_sidebar_1: "The evaluative systems used by promotion and tenure committees, funders, and accreditors were not designed with community-engaged work in mind. They render invisible the relational, process-oriented, and community-transformative dimensions that give this work its meaning."
impact_sidebar_2: "CEnTR*IMPACT is not a single metric but an intentionally constructed ensemble: four complementary score types that together provide a composite, holistic view of a community-engaged project. Each illuminates a distinct dimension. Together they tell a fuller story than any single number."

impact_body: "The ensemble was developed through a rigorous participatory process with community-engaged scholars who identified the most salient dimensions of their work — giving CEnTR*IMPACT both face validity and expert validity. The metrics reflect what community-engaged scholars themselves say matters most."
impact_body_2: "The accompanying R package toolkit reads survey exports from Google Forms or Qualtrics, performs all calculations, and generates publication-quality visualizations and narrative-ready reports — making rigorous analysis accessible to any scholar regardless of statistical background. Visualizations draw on techniques pioneered by Florence Nightingale and W.E.B. DuBois."

impact_scores_label: "The four score types"
impact_scores:
  - sym: "S<sub>I</sub>"
    name: "Direct Indicators"
    desc: "Counts of quantifiable activities and outputs — engagement hours, individuals served, students involved — that provide essential contextual background."
  - sym: "S<sub>A</sub>"
    name: "Alignment Score"
    desc: "Captures how much researchers and community partners agree on how the project is being carried out across eight factors, from Goals and Purposes to Community Empowerment."
  - sym: "S<sub>D</sub>"
    name: "Project Dynamics"
    desc: "Organized around the CBPR framework across five domains, it reveals how evenly distributed effort and cooperation are spread across the full arc of the project."
  - sym: "S<sub>C</sub>"
    name: "Cascade Effects"
    desc: "Draws on social network analysis to map and measure the potential for information and impact to spread — illuminating clear pathways and bottlenecks."

impact_link: "centr-impact"
impact_link_text: "Explore CEnTR*IMPACT →"

# ─────────────────────────────────────────
# CTA
# ─────────────────────────────────────────
cta_title: "Ready to apply the system in your context?"
cta_body: "If your institution is ready to move from fragmented documentation to coherent infrastructure for community-engaged scholarship, we'd be glad to talk."
cta_primary_text: "Book Time with Jeremy"
cta_primary_url: "https://outlook.office.com/bookwithme/user/93badc8cbff54115aab9a542fbea0fdf@iu.edu?anonymous&ismsaljsauthenabled&ep=pcard"
cta_secondary_text: "View the Framework"
cta_secondary_url: "framework"
---
