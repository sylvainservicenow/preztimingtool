# CHANGELOG

## 2026-03-01 — v1.6
- **PDF title extraction** — PDF import now extracts slide titles from text content (first text line per page) in addition to thumbnails
- **Sections on all variants** — Section bar now visible on inactive variants too (dimmed, non-interactive). Only active variant allows editing
- **Sections visible everywhere** — No more disappearing sections when switching between variants

## 2026-03-01 — v1.5
- **Summary popup** — "Summary" button replaces "Export". Shows timing breakdown in a modal with copy-to-clipboard instead of downloading a text file
- **CSS Grid timeline** — Slides and sections now share a CSS Grid, guaranteeing pixel-perfect alignment
- **Minimum 15s slides** — Slides cannot go below 15 seconds; enforced in slider, manual input, divider drag, and section duration redistribution
- **LinkedIn footer** — Homepage shows © 2026 Sylvain Hauser with LinkedIn icon link
- **Section duration editing** — Text input now properly editable (stopPropagation prevents parent re-render)
- **Section export** — Summary includes section cumulative end times when multiple sections exist
- **Toolbar labels** — All buttons have text: Undo, Redo, Save, Duration, Slide, Summary, Clone, Hide

## 2026-02-28 — v1.0
- Initial release
- Visual horizontal timeline with proportional slide blocks
- Drag dividers to redistribute time between slides
- Sections with split/merge and duration controls
- PDF import with real slide thumbnails (via PDF.js)
- PPTX import with titles and sections (via JSZip)
- Multiple timing variants with diff highlighting
- Undo/redo (20 levels)
- Native Chrome file save (File System Access API)
- 4-action homepage: New Plan, Import PDF, Import PPTX, Load Plan
