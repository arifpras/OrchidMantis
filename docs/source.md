# Source & extraction methodology

**Source document:** `20210629_Rapim_Strategi_Komunikasi_dan_Kehumasan_DJPPR_v2.pdf` — "Strategi Komunikasi DJPPR Semester II", dated 29 Juni 2021. 29 slides. Internal Rapim (leadership meeting) deck for DJPPR's communications team.

**Extracted:** 17 September 2026.

## What was extracted and how

1. **Colors** — key slides were rendered to 200dpi PNGs (`pdftoppm`), then sampled with two methods: (a) median-color sampling at specific coordinates for flat/solid fills, and (b) dominant-color clustering over small bounding boxes for gradients and busier regions. Colors that appeared consistently across multiple independent slides/samples are marked `"confidence": "high"` in `tokens/colors.json`; colors sampled once, or from areas with photo bleed-through, are marked `"medium"` or `"low"`.

2. **Typography** — font family names were read directly from the PDF's embedded font table via `pdffonts`. This is exact: the deck embeds subsetted Gotham Narrow (multiple weights), Arial, Calibri, Wingdings (icon glyphs), and Courier New (rare). Type *sizes* were not embedded as reusable metadata in a form this extraction captured, so the scale in `tokens/typography.json` is a visual estimate against a normalized slide canvas, not a measurement.

3. **Logos** — cropped directly from the rendered title-slide PNG. These are raster crops at limited resolution, sufficient for a quick reference/mockup but **not** suitable for production use. Replace with official vector assets before using this system for anything client-facing or printed.

4. **Layout components** — identified by eye across all 29 slides and described qualitatively in `docs/design-system.md` §4. No automated layout/geometry extraction was performed (no XML/shape-level access to the original .pptx — only the flattened PDF was available).

## Known limitations

- This extraction did **not** have access to the original `.pptx` file, only a flattened PDF export. Anything that only exists in editable PowerPoint metadata (exact hex values from the theme palette, exact point sizes, exact spacing/margins, shape effects) is approximated from pixels, not read from source.
- A handful of program-specific slides (InFest Inkubasi financial-educator sub-brand, mentor badge grids) use colors outside the core palette; these are flagged as low-confidence in the tokens and are optional to carry forward.
- If a future version of this repo gets access to the source `.pptx`, re-extracting the theme's exact color palette and master-slide layouts from the XML would meaningfully increase confidence across the board — worth doing if pixel-perfect fidelity matters.
