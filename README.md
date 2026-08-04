# kitab — a config-driven book template

Publish a book as a static site by **editing config, never touching plumbing**.
kitab is the reader architecture extracted from `zistgah/tabdili`, generalised:
presentation, content, and data are decoupled, and a new book is a set of config
and content files.

## Make it your book

Edit only these:

- `config/book.config.json` — title, author, licence, DOI, chapter manifest, theme tokens
- `config/readers.config.json` — which reader formats are enabled + the default
- `config/features.config.json` — toggles: share, ratings, seeding/BYOK, talking artifacts, learning links, litigation hook
- `content/*.json` — one file per chapter (Lorem Ipsum templates are provided)
- `assets/figures/*` — your figures (placeholders provided)

No code changes are needed to add a book — only config and content.

## Readers (same content, selectable format)

- **paginated** — page by page
- **scroll** — one continuous column
- **liquid** — reflowable; reader adjusts width and font size

Format is a config choice (`readers.config.json`), not a fork. Add `?reader=scroll`
to the URL to open a specific one.

## Talking artifacts

Every figure declares itself in its content JSON: a pop-out **explanation**, **read
aloud** (browser TTS), and optional **Ask AI** (BYOK — the visitor supplies their own
key, stored only in their browser; no server). 3D and hyperdimensional figures declare
`kind`, `used_in`, and a `renderer_hook` so a live renderer can be attached later.

## Learning ↔ doing

Select any passage: linked courses appear if configured, otherwise a course request
is raised as a GitHub issue on the configured learning repo (`features.config.json →
learning.repo`, default `zistgah/varzish`). Readers can also comment or flag concerns
on any passage via pre-filled issues.

## Visitor participation (pure GitHub Pages, no server)

Share buttons, a fork-your-own-copy button, GitHub-star + a lightweight client-side
star rating, and issue-based comment/flag — all client-side or pre-filled links.

## Litigation-simulation hook

Per the estate contract, a litigation-simulation entry is present in every reader's
chrome (`features.config.json → litigation_sim`, default a stub pointing at
`zistgah/vakil`).

## Deploy

`index.html` is at the repo root and surfaces at `zistgah.org/kitab` (or your Pages
URL). Everything is static; no build step.

---

© 1900–2000 Auctor Nomen. All rights reserved. Content licence per `book.config.json`.
Template plumbing GPL-3.0-or-later. · model: Claude Opus 4.8
