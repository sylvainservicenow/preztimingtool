# CHANGELOG

## 2026-03-01 — v2.0
- **PDF+PPTX combo import** — When importing PDF, optionally also import PPTX to get sections and titles combined with PDF thumbnails. Validates matching slide counts.
- **Loading indicator** — Spinner overlay with status message during file imports (PDF rendering, PPTX parsing)
- **Lock slides** — Lock individual slide durations so they don't change when adjusting other slides. 🔒 icon shown on locked slides.
- **Lock sections** — Lock entire sections (locks all slides within). Locked sections are skipped during time cascade.
- **Drag-reorder sections** — Drag and drop section blocks to reorder them. All slides within the section move together.
- **Lock-aware redistribution** — setDur, setSectionDuration, and divider drag all skip locked slides/sections

## 2026-03-01 — v1.6
- **PDF title extraction** — PDF import now extracts slide titles from text content (first text line per page) in addition to thumbnails
- **Sections on all variants** — Section bar now visible on inactive variants too (dimmed, non-interactive). Only active variant allows editing

## 2026-03-01 — v1.5
- **Summary popup** — "Summary" button replaces "Export". Shows timing breakdown in a modal with copy-to-clipboard
- **CSS Grid timeline** — Slides and sections share a CSS Grid for pixel-perfect alignment
- **Minimum 15s slides** — Enforced in slider, manual input, divider drag, and section redistribution
- **LinkedIn footer** — © 2026 Sylvain Hauser with LinkedIn icon link
- **Toolbar labels** — All buttons have text: Undo, Redo, Save, Duration, Slide, Summary, Clone, Hide

## 2026-02-28 — v1.0
- Initial release
- Visual horizontal timeline with proportional slide blocks
- Drag dividers, sections, variants, undo/redo
- PDF import (thumbnails), PPTX import (titles + sections)
- Native Chrome file save, Summary popup
- 4-action homepage: New Plan, Import PDF, Import PPTX, Load Plan
