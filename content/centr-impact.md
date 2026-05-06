---
title: "CEnTR*IMPACT: Making Value Legible"
description: "Profile community impact across alignment, dynamics, and cascade effects. Translate engaged outputs into comparable scholarly credit."
layout: "impact"
type: "impact"
mathjax: true

blocks:
  - block: "hero"
  - block: "context"
  - block: "impact-cip"
  - block: "impact-sce"
  - block: "impact-cet"
  - block: "impact-integration"
  - block: "cta"

# ─────────────────────────────────────────
# HERO
# ─────────────────────────────────────────
hero_section_class: "impact-hero"
hero_botanical: "assets/milkweed.png"
hero_botanical_alt: "Botanical illustration of common milkweed"
hero_quote: "Like milkweed spreading silk-tufted seeds on the wind, intentional metrics help gather community members together and facilitate the distribution of information and power."
hero_quote_class: ""

hero_eyebrow: "The CEnTR* System"
hero_title: "CEnTR*IMPACT"
hero_lead_1: "Community-engaged research produces real value: for communities, for institutions, for the public good. But existing evaluation systems were never designed to see it. Impact goes uncounted, contributions go uncredited, and the most important work remains invisible."
hero_lead_2: "CEnTR*IMPACT changes that. Three integrated components profile community impact, translate engaged outputs into scholarly credit, and track how an institution's engagement deepens over time."

hero_strip:
  - name: "CIP"
    label: "Community Impact Profile"
    icon: "/assets/icons/community.png"
    icon_class: "impact-icon--cip"
    anchor: "cip"
  - name: "SCE"
    label: "Scholarly Credit Equivalent"
    icon: "/assets/icons/pile.png"
    icon_class: "impact-icon--sce"
    anchor: "sce"
  - name: "CET"
    label: "Community Engagement Trajectory"
    icon: "/assets/icons/seedling.png"
    icon_class: "impact-icon--cet"
    anchor: "cet"

# ─────────────────────────────────────────
# CONTEXT
# ─────────────────────────────────────────
context_section_class: "context-section"
context_stripe_class: "context-stripe"
context_callout_class: "context-callout"

context_eyebrow: "Why This Matters"
context_title: "Measurement shapes what gets valued. And what gets valued shapes what gets done."
context_sidebar_1: "Current evaluation systems were designed for traditional scholarship. When applied to community-engaged research, they systematically undercount contributions, misrepresent impact, and make invisible the most important things that happen."
context_sidebar_2: "CEnTR*IMPACT was built from the ground up to measure what matters in engaged scholarship, and to produce evidence that can travel across institutional contexts, support promotion and tenure decisions, and demonstrate public value in the language funders and accreditors understand."
context_callout: "The question isn't whether community-engaged research has value. The question is whether our measurement systems can see it."
context_body_1: "CEnTR*IMPACT addresses this through three integrated components, each answering a different question about the nature and significance of engaged scholarship. Together they form a complete picture, from the impact of a single project to the trajectory of an institution's engagement over time."
context_body_2: "The system is grounded in a validated framework developed through collaborative consensus-building with faculty, community partners, and institutional stakeholders at Indiana University Indianapolis, and piloted across real community-engaged projects."
context_report_text: "Read the foundational CUMU Collaboratory Fellowship Report →"
context_report_url: "https://cumuonline.org/wp-content/uploads/2024-CUMU-Collaboratory-Fellowship-Report.pdf"

# ─────────────────────────────────────────
# CIP — Community Impact Profile
# ─────────────────────────────────────────
cip_eyebrow: "Component One"
cip_title: "Community Impact Profile"
cip_status: "Actively Used"
cip_status_class: "badge-active"

cip_sidebar_1: "The CIP generates a multidimensional profile of a specific community-engaged project or partnership, capturing what it produced, how it was conducted, and how far its effects reached."
cip_sidebar_2: "It is the working heart of CEnTR*IMPACT: a tool researchers can use today to document and communicate the full value of their engaged scholarship."
cip_quote: "Previously hidden work becomes visible. Community impact becomes legible."

cip_f1_title: "Multi-dimensional impact scoring"
cip_f1_body: "Combines alignment with community priorities, project dynamics, and cascade effects into a single comparable profile, without collapsing the complexity that makes the work meaningful."
cip_f2_title: "Values-aligned measurement"
cip_f2_body: "Intent matters as much as output. The CIP model weights genuine alignment with community priorities above raw activity, reflecting what practitioners know to be true about what makes engagement meaningful."
cip_f3_title: "Publication-ready outputs"
cip_f3_body: "Generates visualizations and narrative summaries suitable for P&T portfolios, grant reports, accreditation documentation, and institutional strategic planning."
cip_f4_title: "Transparent rationale"
cip_f4_body: "Every score comes with plain-language explanation, not a black box. Researchers and institutions can see exactly what the model is measuring and why."

cip_scores_label: "The four score types"
cip_scores_note: "Sample outputs from Rising Waters, Resilient Communities. Click any card to enlarge."
cip_scores:
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
    desc: "Draws on social network analysis to map and measure the potential for information and impact to spread, illuminating clear pathways and bottlenecks."

cip_primary_text: "Try CEnTR*IMPACT →"
cip_primary_url: "https://connect.posit.iu.edu/centrimpact/"
cip_secondary_text: "Read the Report"
cip_secondary_url: "https://cumuonline.org/wp-content/uploads/2024-CUMU-Collaboratory-Fellowship-Report.pdf"

# ─────────────────────────────────────────
# SCE — Scholarly Credit Equivalent
# ─────────────────────────────────────────
sce_eyebrow: "Component Two"
sce_title: "Scholarly Credit Equivalent"
sce_status: "In Development"
sce_status_class: "badge-dev"

sce_sidebar_1: "The SCE translates diverse scholarly contributions — articles, toolkits, community partnerships, policy documents, relational labor — into a common unit of scholarly credit."
sce_sidebar_2: "It doesn't ask whether a community partnership is equivalent to a journal article. It asks what the partnership is worth, expressed in terms that can travel across institutional contexts without subordinating community-engaged work to traditional academic categories."
sce_quote: "Not every contribution looks like a journal article. That's never been the problem. The problem is we've been using journal articles as the only unit of measure."

sce_formula_label: "The SCE Formula"
sce_formula_display: "$$SCE_i = W_o \\cdot V_i \\cdot R_i \\cdot Q_i$$"
sce_formula_vars:
  - sym: "$SCE_i$"
    desc: "Scholarly Credit Equivalent for contribution i"
  - sym: "$W_o$"
    desc: "Weight assigned to the output type, where institutional values are encoded"
  - sym: "$V_i$"
    desc: "Visibility: who can see and verify this contribution"
  - sym: "$R_i$"
    desc: "Reach: the breadth and reciprocity of impact"
  - sym: "$Q_i$"
    desc: "Quality: assessed in terms appropriate to the contribution type"

sce_f1_title: "A common currency, not a conversion"
sce_f1_body: "The SCE expresses contributions in a shared unit without forcing them into categories they don't fit. Community partnerships and journal articles can sit alongside each other, not ranked against each other."
sce_f2_title: "Locally calibrated weights"
sce_f2_body: "The W<sub>output</sub> term is where institutional values are encoded. Institutions can set weights that reflect their own priorities, and consulting with us helps make those choices explicit and defensible."
sce_f3_title: "Relational labor recognized"
sce_f3_body: "The sustained work of building and maintaining community partnerships — historically invisible in evaluation systems — becomes countable, comparable, and creditable."

# sce_primary_url and sce_secondary_url intentionally omitted — buttons hidden until ready
# sce_primary_text: "Calculate SCE"
# sce_primary_url: "#"
# sce_secondary_text: "Learn the Method"
# sce_secondary_url: "#"

# ─────────────────────────────────────────
# CET — Community Engagement Trajectory
# ─────────────────────────────────────────
cet_eyebrow: "Component Three"
cet_title: "Community Engagement Trajectory"
cet_status: "In Development"
cet_status_class: "badge-dev"

cet_sidebar_1: "The CET measures how an institution's community engagement evolves over time, tracking snapshots across multiple periods to reveal whether engagement is deepening, broadening, or stalling."
cet_sidebar_2: "Where the CIP asks what did this project produce? the CET asks what kind of institution are we becoming? That's the question trust-building requires."
cet_quote: "A single project tells you what happened. A trajectory tells you who this institution is becoming."

cet_formula_label: "The CET Formula"
cet_formula_display: "$$I_t = ℵ_t · f(a_t, d_t, c_t)$$"
cet_formula_vars:
  - sym: "$I_t$"
    desc: "Engagement snapshot at time t"
  - sym: "$ℵ_t$"
    desc: "Intent factor, scales the entire snapshot; genuine purpose conditions all else"
  - sym: "$a_t$"
    desc: "Alignment score: how well the work aligns with community priorities (weight: 0.6)"
  - sym: "$d_t$"
    desc: "Dynamics score: engagement hours, infrastructure, and outputs (weight: 0.3)"
  - sym: "$c_t$"
    desc: "Cascade score: partners, people served, and students involved (weight: 0.1)"

cet_f1_title: "Intent as the condition of possibility"
cet_f1_body: "ℵ, the Intentionality Factor, scales the entire engagement snapshot. A project with high activity but low intentionality scores accordingly. Genuine purpose is not just one variable among equals."
cet_f2_title: "Longitudinal, not just snapshots"
cet_f2_body: "The CET tracks how an institution's engagement changes over time. revealing patterns, growth, and gaps that single-project evaluations cannot show."
cet_f3_title: "Strategic planning support"
cet_f3_body: "For administrators making the case for community engagement — to legislators, accreditors, and funders — the CET provides longitudinal evidence of institutional commitment, not just activity counts."

cet_primary_text: "Map Trajectory"
cet_primary_url: "#"
cet_secondary_text: "Explore Examples"
cet_secondary_url: "#"

# ─────────────────────────────────────────
# INTEGRATION
# ─────────────────────────────────────────
integration_eyebrow: "The Complete Picture"
integration_title: "Three components. One coherent story of engaged scholarship."
integration_sidebar_1: "CIP, SCE, and CET are designed to work together, each answering a different question, all contributing to the same goal: making community-engaged scholarship visible, creditable, and legible to the audiences that need to see it."
integration_sidebar_2: "The tools make the evidence. The consulting helps you use it."

integration_cards:
  - title: "For Researchers"
    body: "Document the full value of your community-engaged work, including the parts that don't fit a traditional CV. Generate evidence for P&T portfolios, grant reports, and public audiences that reflects what your work actually is."
    bar: "bar-cip"
  - title: "For Institutions"
    body: "Understand the landscape of engagement across your campus, calibrate evaluation systems to your institutional values, and produce the longitudinal evidence that demonstrates genuine commitment to community, not just compliance."
    bar: "bar-sce"
  - title: "For Community Partners"
    body: "Ensure that your contributions — your knowledge, relationships, and labor — are represented accurately and credited appropriately. The framework is built to center community assets, not institutional outputs."
    bar: "bar-cet"

# ─────────────────────────────────────────
# CTA
# ─────────────────────────────────────────
cta_title: "Let's make the work visible, and the trust possible."
cta_body: "CEnTR*IMPACT works best when it's applied to your specific context. Let's talk about how the system can support your researchers, your institution, and your community partners."
cta_primary_text: "Book Time with Jeremy"
cta_primary_url: "https://outlook.office.com/bookwithme/user/93badc8cbff54115aab9a542fbea0fdf@iu.edu?anonymous&ismsaljsauthenabled&ep=pcard"
cta_secondary_text: "Try the Tool"
cta_secondary_url: "https://connect.posit.iu.edu/centrimpact/"
---