# Sathyan-B924.github.io

The landing page for **Laboratory Calculators**, published at
<https://sathyan-b924.github.io/>.

This repository holds the homepage **only**. Each calculator keeps its own repository and its own
GitHub Pages site; nothing here duplicates their source.

| Calculator | Repository | Live site |
| --- | --- | --- |
| Pipette Split | [`pipette-split-calculator`](https://github.com/Sathyan-B924/pipette-split-calculator) | <https://sathyan-b924.github.io/pipette-split-calculator/> |
| Molarity | [`molarity-calculator`](https://github.com/Sathyan-B924/molarity-calculator) | <https://sathyan-b924.github.io/molarity-calculator/> |
| Nanoparticle | [`nanoparticle-calculator`](https://github.com/Sathyan-B924/nanoparticle-calculator) | <https://sathyan-b924.github.io/nanoparticle-calculator/> |

## Design notes

- One self-contained `index.html`: markup, CSS, and card icons (inline SVG) in a single file.
  No framework, no build step, no fonts or scripts from other servers, no tracking.
- Light and dark themes follow the operating system via `prefers-color-scheme`.
- Mobile-first single column; three columns from `46rem` upward. Whole cards are tap targets.
- Each card is tinted with its calculator's own accent colour — teal, blue, amber — so the
  homepage and the app you land on look related.

## ⚠ Why there is no service worker here

**This site must never register a service worker, and must never serve a web app manifest scoped
to `/`.**

This is a GitHub *user* site, so it is published at the origin root. A service worker registered
from `/` would take `/pipette-split-calculator/`, `/molarity-calculator/` and
`/nanoparticle-calculator/` into its scope, where it could shadow each calculator's own service
worker and serve this landing page in place of theirs. The calculators are offline-first PWAs and
that would break them.

The homepage is a plain static document by design. Keep it that way.

## Adding another calculator

1. Publish the calculator from its own repository with GitHub Pages.
2. Copy one `<li>` block in `index.html`, point the `href` at the new site, and change the heading,
   description, and inline icon.
3. Add an accent class next to `.pipette` / `.molarity` / `.nanoparticle`, defining `--accent`
   and `--wash`.
4. Add a row to the table above.
