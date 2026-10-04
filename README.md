# Southington Community Site — Build Notes (frontend-dev)

Build output for the 7-page IA in `design/sitemap.md`, using the palette, type
scale, grid and asset register in `design/palette.md` / `design/assets.md` and
the six templates in `design/wireframes.md`. Vanilla HTML + CSS, no framework,
no build step.

## Files written

| Path | Template | Notes |
|---|---|---|
| `site/index.html` | A — Home | Hero, intro, 4-up stat strip, "A Town With Roots", 5 feature cards, CTA band |
| `site/about.html` | B — Standard | History prose, Key Facts (table + `<600px` definition list), governance, Learn More |
| `site/things-to-do.html` | C — List | 4 jump pills, parks cards, alternating feature rows, 2 event cards, closing CTA |
| `site/businesses.html` | D — Directory | Disclaimer callout, 3 category pills, 3×3 listing cards, closing CTA |
| `site/services.html` | C (Services variant) | 5 jump pills, Town Hall contact card, Departments, Utilities, Transit, Library |
| `site/news.html` | E — Stream | 3 headline rows with source chips, 3 event cards with season badges, sticky rail |
| `site/contact.html` | F — Contact | 3 equal-height contact cards with bottom-aligned action rows, Other Departments, note band |
| `site/styles.css` | — | All tokens from `palette.md` §4/§5.2 pasted as-is; grid, components, print stylesheet |
| `site/assets/img/favicon.svg` | LG-04 | Our own apple mark (orchard green + cider red). **Not** the municipal seal |
| `site/assets/img/README.txt` | — | Documents every pending image placeholder |
| `site/assets/fonts/README.txt` | FT-01/FT-02 | Documents the two SIL OFL fonts to drop in |
| `site/robots.txt` | — | Allow all + sitemap declaration |
| `site/sitemap.xml` | — | The 7 page URLs |

## Design decisions applied

- **Palette:** every colour is the token from `palette.md` §4 — no hex retyped
  by hand. Interactive blue text uses `--color-primary-700` or darker; the
  seal-sampled 500-level colours appear only as borders, icon fills and tints.
  Cider red appears only as the event-card left border and season badges.
- **Type scale:** all nine `clamp()` steps implemented; measure capped at 70ch;
  body copy is 17px and never smaller.
- **Grid:** 12-col intent realised as 1200px max width, 24px gutter, 24/40px
  page padding; header collapses at 900px; breakpoints sm<600 / md 600–899 /
  lg 900–1279 / xl≥1280.
- **Hero scrim** is the CSS token, applied over every hero placeholder — no
  text sits on an unscrimmed image.
- **No JS required to read any page.** The mobile drawer and its focus trap are
  the only script; without JS the drawer stays closed and every page is
  reachable through the footer's Explore column.

## Custom properties wiring (per design tokens)

Dark/light inversions (`hero`, `cta`, `footer`) set an accessible focus ring in
`--color-sand`; everything else uses `--color-focus`. `prefers-reduced-motion`
disables the card lift and smooth scrolling. `@media print` hides chrome and
prints the facts table and contact cards legibly with a `print-header` strip
(GR-09) carrying "Verify at southingtonct.gov".

## Link verification

Checked by hand against the built files. **All internal links and anchors
resolve** — the three broken `(#)` anchors from the copy deck are wired:

| Anchor in copy deck | Wired to | Present as |
|---|---|---|
| `[Businesses](#)` (things-to-do) | `businesses.html` | file exists |
| `[Services](#)` (businesses) | `services.html` | file exists |
| `[Contact](#)` (services) | `contact.html` | file exists |

Nav (6 items) → files: About/Things to Do/Businesses/Services/News/Contact. The
active page carries `aria-current="page"`. Every page's Explore footer column
links the same 6 pages plus Home.

Anchors, each verified to exist as an element `id`:

- `things-to-do.html` → `#parks-green`, `#trails`, `#winter`, `#events`
- `businesses.html` → `#restaurants`, `#retail`, `#services`
- `services.html` → `#town-hall`, `#departments`, `#utilities`,
  `#getting-around`, `#library`
- `news.html` → `#events`
- Every page → `#main` (skip link)

Cross-links resolved: home → about, things-to-do (4 anchors), businesses
(`#restaurants`), services, news (`#events`), contact; things-to-do → news
(`#events`) and businesses; news → things-to-do (`#events`, `#parks-green`,
`#winter`); about → home.

## Image / asset placeholders (documented)

All photography is **pending licence**. Per `assets.md` the build uses the GR-06
graded-tint block with the relevant Lucide icon at 20% opacity and a visible
"photo pending" caption — never a broken image, never unlicensed stock. Blocks
are present for: PH-01, PH-02, PH-03, PH-04, PH-05, PH-06, PH-08. See
`assets/img/README.txt` for the full list including `og-image.png` (LG-06) and
`apple-touch-icon.png` (LG-05), both referenced by the meta tags.

Fonts FT-01/FT-02 are declared with `font-display: swap` and preloaded; until
the `.woff2` files are dropped in, the stacks fall back to Georgia (headings)
and the system sans (body). See `assets/fonts/README.txt`.

## Open items handed to content (not changed by the build)

- **Bertucci's** is grouped under **Retail** in the deck though the name is a
  restaurant. The deck's grouping is preserved; flagged to content.
- No `Event` JSON-LD is emitted because the copy gives no festival dates.
- `southington.example` is a placeholder origin in canonical/OG/sitemap URLs —
  replace with the live domain at deploy.
