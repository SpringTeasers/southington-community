ASSET PLACEHOLDERS — Southington Community Site
================================================
Build step: frontend-dev. Status: P0 assets NOT yet sourced.

This folder holds image assets. The build ships with PLACEHOLDERS so no page
is ever broken; every placeholder is the GR-06 "graded tint block" component
(design/assets.md §5 GR-06) rendered in CSS, not a file.

MISSING (must be licensed and recorded in design/assets.md §7 before launch):

  PH-01  Town Green in festival season   → Home hero, News hero
  PH-02  Town Green, quiet weekday       → About hero, Home "Roots" section
  PH-03  Apple orchard rows              → Businesses hero
  PH-04  Farmington Canal Heritage Trail → Things to Do hero + Trails feature
  PH-05  Mount Southington (winter)      → Things to Do Winter row, News
  PH-06  Panthorn Park                   → Things to Do Parks card
  PH-08  Town Hall, 75 Main St           → Services hero, Contact hero
  PH-09  Southington Public Library      → Contact card (optional, P2)

  LG-06  og-image.png (1200x630)         → referenced by every page's
                                           og:image meta tag
  LG-05  apple-touch-icon.png (180x180)  → referenced by every page

PRESENT:

  favicon.svg  LG-04 — our own stylised apple mark in orchard green /
                 cider red. Deliberately NOT the municipal seal.

TO SOURCE: open license (Unsplash / Pexels / Wikimedia Commons / Visit CT with
terms checked), downloaded and served locally — never hotlinked. Deliver WebP
with JPEG fallback at 1600/1200/800/480 px; hero fetchpriority="high", all
others loading="lazy".

Do NOT use the Town of Southington municipal seal or the official logo file.
