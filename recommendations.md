Right now the main pressure points are:

* very large front matter content blobs in content/_index.md, content/centr-impact.md, content/centr-map.md, content/centr-seek.md, content/system.md
* very large page-specific templates in layouts/impact/single.html, layouts/map/single.html, layouts/seek/single.html, layouts/system/single.html
* almost no use of data/, so content + presentation are tightly coupled
* generated output (public/, resources/_gen/) creating huge git churn

3 viable structure options
1) Section/page-bundle structure (lowest risk)
Move each page into a folder bundle so content is better grouped:

* content/system/index.md
* content/centr-seek/index.md
* content/centr-map/index.md
* content/centr-impact/index.md
* content/framework/index.md

Keep existing layouts mostly as-is.  
Good if you want cleaner organization without big template rewrites.
2) Block-based “page builder” structure (best fit here)
Define pages as ordered blocks in front matter/data, and render via shared block partials:

* layouts/partials/blocks/hero.html
* layouts/partials/blocks/context.html
* layouts/partials/blocks/feature-list.html
* layouts/_default/single.html loops over blocks

This removes duplication across impact/map/seek/system templates and makes new pages easier.  
Best if you expect to keep adding similarly structured pages.

3) Data-first content model (best for non-dev editing)
Keep templates thin and move most structured content to data/:

* data/pages/home.yaml
* data/pages/system.yaml
* data/pages/centr-seek.yaml, etc.

Templates consume site.Data.  
Great for long-form structured content, but a bit more abstraction.
What I’d recommend for this site
Use Option 2 (block-based), plus one hygiene changes:

split config into config/_default/ as it grows (menus, params, environments)
