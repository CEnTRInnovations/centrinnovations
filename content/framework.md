---
title: "The Framework"
description: "A layered model for understanding community-engaged research."
layout: "framework"
type: "framework"

blocks:
  - block: "hero"
  - block: "framework-intro"
  - block: "framework-layers"
  - block: "framework-relations"

# ─────────────────────────────────────────
# HERO
# ─────────────────────────────────────────
hero_section_class: "framework-hero"
hero_botanical: "assets/framework.png"
hero_botanical_alt: "Botanical illustration of an oak tree with visible root system"

hero_eyebrow: "The Framework"
hero_title: "Community-engaged scholarship has <em>depth</em>."
hero_lead_1: "Understanding it requires looking beneath the surface through history, culture, systems, and the structures through which it becomes visible. This framework provides that view."

hero_strip:
  - name: "Stratigraphy"
    label: "History · Deep Structures"
    icon: "/assets/framework/stratigraphy.png"
    icon_class: "fstrip-strat"
    anchor: "stratigraphy"
  - name: "Topography"
    label: "Culture · Meaning"
    icon: "/assets/framework/topography.png"
    icon_class: "fstrip-topo"
    anchor: "topography"
  - name: "Infrastructure"
    label: "Systems · Practices"
    icon: "/assets/framework/infrastructure.png"
    icon_class: "fstrip-infra"
    anchor: "infrastructure"
  - name: "Architecture"
    label: "Measures · Representations"
    icon: "/assets/framework/architecture.png"
    icon_class: "fstrip-arch"
    anchor: "architecture"

# ─────────────────────────────────────────
# INTRO
# ─────────────────────────────────────────
intro_eyebrow: "How to read this framework"
intro_title: "Four layers of analysis, read together."
intro_body:
  - "Community-engaged research cannot be fully understood from the surface. Like a landscape that reveals its history only when you read the layers beneath it, CEnR has depth that conventional evaluation rarely reaches."
  - "This framework borrows the language of geology and landscape to provide a structured way of seeing that depth, not as metaphor alone, but as analytical scaffolding. Each layer asks different questions, surfaces different evidence, and demands different kinds of attention."
  - "Read together, the four layers give institutions, researchers, and community partners a full-spectrum view: where the work comes from, what it means to the people it involves, how it moves through systems, and how it becomes legible to the wider world."

intro_diagram_labels:
  - name: "Architecture"
    sub: "Measures · Representations"
    class: "diagram-label diagram-label-arch"
  - name: "Infrastructure"
    sub: "Systems · Practices"
    class: "diagram-label diagram-label-infra"
  - name: "Topography"
    sub: "Culture · Meaning"
    class: "diagram-label diagram-label-topo"
  - name: "Stratigraphy"
    sub: "History · Deep Structures"
    class: "diagram-label diagram-label-strat"

intro_diagram_note: "A conceptual cross-section of community-engaged research"

# ─────────────────────────────────────────
# LAYERS
# ─────────────────────────────────────────
framework_layers:

  - id: "stratigraphy"
    num: "01"
    title: "Stratigraphy"
    subtitle: "History · Deep Structures"
    section_class: "layer-section section-strat strat"
    description: "The sediment beneath everything. What has been deposited, compacted, and preserved over time."
    color_var: "var(--strat-mid)"
    icon: "/assets/framework/stratigraphy.png"
    icon_class: "fstrip-strat"
    asks_title: "What this layer asks"
    asks_body: "Stratigraphy is the reading of layers, the interpretation of what has been deposited over time and what those deposits reveal about past conditions. In community-engaged research, it asks: <em>What histories made this work possible, necessary, or contested?</em> What was here before the partnership? What has been promised, broken, or built?"
    quote: "The ground on which community-engaged research stands is never neutral. It was shaped by decisions made long before this partnership began."
    reveals_title: "What it reveals"
    reveals_body:
      - "This layer surfaces the deep structures that shape engagement: the histories of institutions in specific communities, the legacies of extractive or exploitative research, the long-term commitments that have built trust, and the structural conditions — economic, political, demographic — that define what is possible in a given place."
      - "Stratigraphy also recovers what has been buried: the community knowledge systems, the prior relationships, the informal networks that predate the formal partnership and often outlast it."
    concepts:
      - "Institutional history"
      - "Community memory"
      - "Prior relationships"
      - "Power histories"
      - "Structural conditions"
      - "Indigenous knowledge systems"
      - "Legacies of harm"
      - "Long-term trust"
    practice_title: "Questions for practice"
    practice_body: "What is the history of this institution's presence in this community? What prior research has been conducted here, and with what effects? What community-held knowledge predates and informs this work? What structural conditions — historical displacement, disinvestment, exclusion — shape what this partnership can and cannot do?"

  - id: "topography"
    num: "02"
    title: "Topography"
    subtitle: "Culture · Meaning"
    section_class: "layer-section section-topo topo"
    description: "The visible surface of the terrain. What rises and falls, where the paths form, how people move through the landscape."
    color_var: "var(--topo-mid)"
    marker_color: "var(--topo-mid)"
    icon: "/assets/framework/topography.png"
    icon_class: "fstrip-topo"
    asks_title: "What this layer asks"
    asks_body: "Topography maps the surface, the features that shape how people move, gather, and orient themselves. In community-engaged research, the topographic layer asks: <em>What does this work mean to the people involved?</em> How is it understood, valued, and narrated by different stakeholders? Where are the high points of shared purpose, and where are the valleys of disconnect?"
    quote: "Culture is not background. It is the terrain itself, the surface that engagement must traverse, not ignore."
    reveals_title: "What it reveals"
    reveals_body:
      - "This layer surfaces the cultural logics and meaning-making frameworks that partners bring to the work: how community members understand research, how faculty understand community, how institutions narrate their own mission, and where those narratives align or conflict."
      - "Topography reveals the contours of shared language, and the gaps where terms like \"partnership,\" \"impact,\" or \"community\" mean different things to different people. It maps the values, commitments, and expectations that shape what the work becomes."
    concepts:
      - "Shared values"
      - "Cultural assets"
      - "Narrative frames"
      - "Community priorities"
      - "Meaning-making"
      - "Relational norms"
      - "Definitions of benefit"
      - "Conceptual translation"
    practice_title: "Questions for practice"
    practice_body: "How do community partners define \"benefit,\" \"success,\" or \"knowledge\"? What cultural practices and assets does this community bring to the work? Where does the institution's narrative of engagement align with — or diverge from — how communities experience it? What shared language has emerged from the partnership itself?"

  - id: "infrastructure"
    num: "03"
    title: "Infrastructure"
    subtitle: "Systems · Practices"
    section_class: "layer-section section-infra infra"
    description: "The built systems beneath the surface. What carries the work from intention to practice."
    color_var: "var(--infra-mid)"
    marker_color: "var(--infra-mid)"
    icon: "/assets/framework/infrastructure.png"
    icon_class: "fstrip-infra"
    asks_title: "What this layer asks"
    asks_body: "Infrastructure is what makes a landscape traversable: the roads, transit lines, utilities, and communications networks that enable movement and exchange. In community-engaged research, the infrastructure layer asks: <em>What systems, structures, and practices carry this work?</em> How does it move through institutions and communities? Where does it flow freely, and where does it stall?"
    quote: "Good intentions without infrastructure are destinations without roads. The question is not whether you want to get there, but whether the systems exist to carry you."
    reveals_title: "What it reveals"
    reveals_body:
      - "This layer surfaces the operational reality of community-engaged research: the administrative structures, funding mechanisms, data systems, coordination practices, and relational protocols that either enable or impede engaged work. It makes visible the bottlenecks, redundancies, and gaps that practitioners experience daily but that rarely appear in strategic plans."
      - "Infrastructure analysis also reveals where community partners have built their own systems — asset maps, communication networks, knowledge-sharing practices — that the institution has not yet learned to recognize or work with."
    concepts:
      - "Administrative structures"
      - "Funding mechanisms"
      - "Coordination practices"
      - "Data systems"
      - "Community networks"
      - "Governance protocols"
      - "Communication systems"
      - "Capacity building"
    practice_title: "Questions for practice"
    practice_body: "What administrative structures support — or obstruct — community-engaged research? How does funding flow, and where does it slow or stop? What coordination mechanisms exist between researchers and community partners? What community-built systems and networks could the institution learn from or partner with?"

  - id: "architecture"
    num: "04"
    title: "Architecture"
    subtitle: "Measures · Representations"
    section_class: "layer-section section-arch arch"
    description: "The visible built environment. How the work is shaped, framed, and made legible to those who must see it."
    color_var: "var(--arch-mid)"
    marker_color: "var(--arch-mid)"
    icon: "/assets/framework/architecture.png"
    icon_class: "fstrip-arch"
    asks_title: "What this layer asks"
    asks_body: "Architecture is the built form through which human activity becomes organized and legible, the structures that both enable function and communicate meaning. In community-engaged research, the architecture layer asks: <em>How is this work measured, represented, and recognized?</em> What counts as evidence? Who decides? And whose contributions are made visible?"
    quote: "What gets measured gets managed, and what doesn't get measured often doesn't get counted, credited, or sustained."
    reveals_title: "What it reveals"
    reveals_body:
      - "This layer surfaces the evaluation systems, reporting frameworks, promotion and tenure criteria, funder metrics, and public narratives through which community-engaged research becomes — or fails to become — legible. It reveals which forms of knowledge are credentialed, which contributions are attributed, and which outcomes are counted."
      - "Architecture analysis makes visible the gap between what engagement produces and what institutional systems can recognize: the community capacity built, the relationships sustained, the knowledge co-created in forms that don't map onto traditional output categories. It also surfaces opportunities, for new metrics, new representations, and new languages of value."
    concepts:
      - "Evaluation frameworks"
      - "Impact metrics"
      - "P&T criteria"
      - "Attribution systems"
      - "Funder reporting"
      - "Community recognition"
      - "Output categories"
      - "Knowledge representation"
    practice_title: "Questions for practice"
    practice_body: "What gets counted in your institution's evaluation of community-engaged research? Whose contributions are attributed, and how? What forms of evidence do funders, accreditors, and administrators recognize, and what falls outside their view? How might new frameworks of representation make the full value of this work visible?"

# ─────────────────────────────────────────
# RELATIONS
# ─────────────────────────────────────────
relations_eyebrow: "Reading the Layers Together"
relations_title: "No layer stands alone."
relations_lead: "The power of this framework comes from reading the layers in relationship. Each layer shapes the others, and the most important insights emerge at their intersections."

relation_cards:
  - title: "History shapes meaning"
    body: "The cultural significance of community-engaged research in a given place cannot be understood without the historical record beneath it. Trust — or its absence — is always earned over time."
    layers: ["rl-strat", "rl-topo"]
  - title: "Culture shapes systems"
    body: "The infrastructure of engagement reflects cultural priorities. What gets resourced, coordinated, and systematized reveals what the institution actually values, not just what it says it values."
    layers: ["rl-topo", "rl-infra"]
  - title: "Systems shape recognition"
    body: "What can be measured is determined by what has been built to measure it. Evaluation frameworks that ignore community-built infrastructure will always undercount what engagement produces."
    layers: ["rl-infra", "rl-arch"]
  - title: "Recognition shapes history"
    body: "What gets documented, credited, and preserved becomes the record. Measurement choices made today determine what future partners will inherit, or have to recover."
    layers: ["rl-arch", "rl-strat"]
  - title: "Deep structures shape systems"
    body: "Administrative structures for engagement are rarely built from scratch. They emerge from — and often reproduce — the institutional histories and power relations embedded in stratigraphy."
    layers: ["rl-strat", "rl-infra"]
  - title: "Meaning shapes measure"
    body: "What we decide is worth counting reflects what we believe is worth valuing. Evaluation systems that ignore cultural meaning produce data that is precise but not true."
    layers: ["rl-topo", "rl-arch"]
---