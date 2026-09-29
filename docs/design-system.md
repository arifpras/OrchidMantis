# DJPPR Communication Deck — Design System

Extracted from **"Strategi Komunikasi DJPPR Semester II"** (29 Juni 2021), a 29-slide internal Rapim presentation from Direktorat Jenderal Pengelolaan Pembiayaan dan Risiko (DJPPR), Kementerian Keuangan RI.

This document describes the recurring visual language of that deck — colors, typography, logo usage, and the layout components that repeat across slides — so it can be reused as a reference when producing new decks, docs, or artifacts in the same style.

> **Provenance note:** colors were extracted programmatically (pixel-sampling the rendered slides), and font families were read directly from the PDF's embedded font table — that part is exact. Everything else (exact spacing, precise type sizes, gradient angles) is a visual approximation. Treat this as a strong starting point, not a certified brand manual — cross-check against the source `.pptx` or an official Kemenkeu/DJPPR brand guideline before any pixel-critical or print use.

---

## 1. Color

### 1.1 Core palette

| Token | Hex | Swatch | Usage |
|---|---|---|---|
| `core.purple` | `#6C007D` | deep purple | Primary brand color — section headings, small square bullet icons, badge pills, accent text |
| `core.gold` | `#FFC000` | bright gold/amber | Primary accent — full-bleed section backgrounds, header icon squares, divider side-bars, stat highlights |
| `core.magentaPink` | `#D0208A` | magenta-pink | Underline rules beneath headlines; gradient end-stop |
| `core.navy` | `#002060` | navy | Icon fills on the circular roadmap/outline diagram |
| `core.lightBlue` | `#B4C7E7` | pale blue | Thin connector arcs on the agenda/outline slide |
| `core.neutralGray` | `#ABAAAA` | gray | Secondary connector arcs, muted dividers |
| `core.plum` | `#7C3F84` | muted plum | Solid banner blocks on title/closing slides |
| `core.pageBackground` | `#F5F6F8` | off-white | Default slide background |
| `core.textOnDark` | `#FFFFFF` | white | Text set on purple/magenta/gold fills |

Full machine-readable version: [`tokens/colors.json`](../tokens/colors.json) and [`tokens/colors.css`](../tokens/colors.css).

### 1.2 Signature gradient

The deck's most recognizable visual is a **diagonal purple-to-magenta gradient**: `#6B1F6B → #8B5890 → #C0208A`. It appears in two places:

- **Section-divider slides** — a translucent gradient panel layered over a dimmed architecture/building photograph, with a solid gold bar on the panel's right edge and a gold vertical bar on the far left of the slide.
- **Program call-out cards** — solid panels (InFest, Talkshow dan Podcast, Aktivasi Media Sosial, etc.) using the same gradient as a flat card background, with white text and gold-outlined pill sub-labels.

### 1.3 Decorative corner motif

Title and closing slides carry a small cluster of folded triangles in the bottom-right corner — gold `#FFC000`, orange `#F06020`, amber `#D87020`, magenta `#A03090` — echoing the fold in the djppr wordmark logo. Treat this as an optional flourish, not a required element.

### 1.4 Program-specific accents (secondary)

Some named sub-programs carry their own accent within the deck rather than the core palette — e.g. InFest Inkubasi's "Financial Educator" key visual uses a teal (~`#2FA888`) paired with black. These are lower-confidence, single-sample extractions and are only relevant if you're replicating that specific program's collateral rather than the general DJPPR system.

---

## 2. Typography

Read directly from the PDF's embedded fonts (exact, not estimated):

| Role | Family | Weights present | Notes |
|---|---|---|---|
| Display / headings | **Gotham Narrow** | Black, Bold, Medium, Book, Light, Book Italic | The deck's signature condensed geometric sans. Used for every slide title, card label, and stat number. If unlicensed for a web build, a reasonable fallback is a condensed geometric sans such as Oswald, Barlow Condensed, or Bebas Neue. |
| Body (primary) | **Arial** | Regular, Bold, Italic | Bullet copy and table content on several slides. |
| Body (secondary) | **Calibri** | Regular, Italic | Bullet copy / table content on a subset of slides — likely inherited from source content pasted from other documents rather than an intentional second typeface. |

**Practical rule:** headlines, section titles, card titles, and any big stat number → Gotham Narrow Bold/Black. Everything else (paragraphs, bullet lists, table cells) → Arial.

Full detail incl. estimated type scale: [`tokens/typography.json`](../tokens/typography.json).

---

## 3. Logo usage

Two logos appear on every content slide, always in the same top corners:

- **Kementerian Keuangan (Kemenkeu) logo** — top-left. Crest icon + two-line wordmark ("KEMENTERIAN KEUANGAN / REPUBLIK INDONESIA").
- **djppr wordmark** — top-right. Lowercase "djppr" in `core.purple`, with a small folded-triangle mark (gold-to-orange gradient) as the accent above the second "p".

Low-resolution reference crops (extracted from the deck, **not production-quality vector files**) are included at `assets/logos/kemenkeu-logo-reference.png` and `assets/logos/djppr-logo-reference.png`. **Replace these with the official vector logo files** from Kemenkeu/DJPPR's brand guidelines before using this system for anything beyond a quick internal mockup — extracted PDF-render crops are not appropriate for real production use.

---

## 4. Layout components

The deck is built from a small set of repeating slide patterns:

### 4.1 Section divider
Full-bleed dimmed photo (architecture/office interior) + the signature gradient panel (§1.2) with a bold white section title, gold accent bars flanking the panel. Used to break the deck into its three acts: *Current Progress*, *Evaluasi dan Target*, *Rencana Kegiatan*.

### 4.2 Standard content header
Small gold or purple square (8-10px) + bold slide title, with a thin magenta-to-plum gradient underline rule directly beneath. An optional lighter-weight subtitle/italic strapline sits below the rule.

### 4.3 Program card
Rounded-corner panel filled with the signature gradient (§1.2), a gold-outlined pill containing the sub-label, bold white card title, and 2-4 bullet points in white/light text. Cards are arranged in a 2x2 or 1+2 grid depending on content volume.

### 4.4 Full-bleed stat/gallery block
Alternating full-bleed gold and purple background blocks used to showcase social-media screenshots or program photo grids, each image captioned in a small white label chip.

### 4.5 Numbered circle + pill badge
A filled circle (white number on purple, or purple number on white) paired with a gold-outlined rounded-rectangle label — used for step-by-step process flows ("Develop → Building → Engage → Amplification") and workflow diagrams.

### 4.6 Circular roadmap / agenda diagram
A ring (light-blue outer arc, gray inner arc) around a white center circle holding the deck's title, with spokes leading to navy hexagonal icons and their labels — used once, on the agenda/outline slide.

### 4.7 Data table
Purple-to-plum gradient header row with white bold centered column headers, pale-gold (`#FFE9A8`-ish tint) body rows, black body text, left-aligned content columns.

---

## 5. Using this system in Claude

- **Design tokens** (`tokens/colors.json`, `tokens/colors.css`, `tokens/typography.json`) are the portable, structured source of truth — point Claude at these files (or paste their contents) when asking it to build a Design, Slides, or Docs artifact "in the DJPPR style."
- When asking Claude to build something from this system, reference the component names in §4 directly (e.g. "use the program-card pattern from the DJPPR design system for these four bullet points") — that's more reliable than describing the look from scratch each time.
- Because `core.gold` on `core.pageBackground` and white-on-`core.gold` both sit near typical WCAG AA thresholds, double-check contrast before using gold as a body-text background in an accessible deliverable — the source deck relies on large, bold type to compensate, which won't be there in every use case.
