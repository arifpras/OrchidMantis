# DJPPR Design System

Colors, typography, and layout-component reference extracted from the DJPPR internal deck **"Strategi Komunikasi DJPPR Semester II"** (29 Juni 2021), so it can be reused as a style reference for new decks, docs, or Claude-built artifacts.

```
djppr-design-system/
├── README.md                       ← you are here
├── tokens/
│   ├── colors.json                 ← structured color tokens, with confidence + usage notes
│   ├── colors.css                  ← same colors as CSS custom properties
│   └── typography.json             ← font families (exact, read from the PDF) + estimated type scale
├── docs/
│   ├── design-system.md            ← full style guide: color, type, logo usage, layout components
│   └── source.md                   ← extraction methodology, provenance, known limitations
└── assets/
    └── logos/
        ├── kemenkeu-logo-reference.png   ← low-res reference crop, NOT production-ready
        └── djppr-logo-reference.png      ← low-res reference crop, NOT production-ready
```

Start with **`docs/design-system.md`** — it's the human-readable guide. The `tokens/` files are the machine-readable version of the same information.

## Pushing this to GitHub

From inside this folder:

```bash
git init
git add .
git commit -m "Add DJPPR design system extracted from Strategi Komunikasi deck"
git branch -M main
git remote add origin <your-repo-url>
git push -u origin main
```

Replace `<your-repo-url>` with your repo's URL (e.g. `git@github.com:yourname/djppr-design-system.git` or the HTTPS equivalent). If the repo doesn't exist yet, create an empty one first (no README/license, to avoid a merge conflict with this commit) via `gh repo create djppr-design-system --private --source=. --remote=origin` (if you have the GitHub CLI installed and authenticated), or through github.com.

## Using it with Claude / Claude Design

- Point Claude at `tokens/colors.json`, `tokens/colors.css`, and `tokens/typography.json` (or paste their contents into the chat) when asking it to build something "in the DJPPR style" — a Design artifact, a slide deck, a doc, or a web page.
- Reference the named components in `docs/design-system.md` §4 (section divider, program card, numbered circle + pill badge, etc.) directly in your prompt — e.g. *"lay this out using the program-card pattern from the DJPPR design system"* — rather than re-describing the look each time.
- If you have Claude's Design System artifact type available, you can also hand it this repo's `docs/design-system.md` plus the token files as the seed content when creating one, so the palette and type choices are pre-loaded into an editable, shareable design system artifact rather than living only as files.

## Caveats before production use

- Colors were extracted by pixel-sampling rendered slides, not read from the original PowerPoint theme — the "high confidence" tokens are solid, but verify anything pixel-critical against the source `.pptx` or an official Kemenkeu/DJPPR brand guideline.
- The logo files here are low-resolution crops for reference only. Swap in official vector logo assets before using this in anything client-facing or printed.
- See `docs/source.md` for the full extraction methodology and limitations.
