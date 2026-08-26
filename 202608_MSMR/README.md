# MSMR 2026 --- Computo (10 min + 3 min questions)

Quarto/Beamer version of the Computo talk, 16:9.

## Build

```sh
quarto render Computo.qmd     # -> Computo.pdf (XeLaTeX)
```

## Files

- `Computo.qmd` --- the deck (draft content, see `abstract.md`)
- `beamerthemecomputo.sty` --- Computo beamer theme, transposed from the
  reveal.js stylesheet `computo.scss` used by the HTML decks (colors, Oswald
  headings / Open Sans body, title & section slides, footline)
- `preamble.tex` --- Quarto-side tweaks (code blocks, callout colors, lists)
- `fonts/` --- Oswald static instances (OFL), used by the theme
- `figures/` --- hand-written TikZ figures (papers-per-year bar chart)
- `img/` --- bitmaps and logos; logos are vector (`.pdf`, converted from `design/*.svg`)

XeLaTeX is required (fontspec). `Open Sans` must be installed system-wide;
Oswald ships with the deck. Both fonts degrade gracefully if absent.

Note: do **not** load `enumitem` --- it silently removes beamer's item markers.
