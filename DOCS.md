# PrezTimingTool — Project Documentation

## Overview
PrezTimingTool is a browser-based presentation slide timing planner. It helps presenters allocate and adjust time across slides using a visual horizontal timeline. It's a single HTML file with zero server dependencies.

**Live**: https://sylvainservicenow.github.io/preztimingtool
**Author**: © 2026 Sylvain Hauser — https://www.linkedin.com/in/sylvainhauser/

## Architecture
- **Single file**: Everything lives in `index.html` — HTML, CSS, JavaScript
- **Zero backend**: Runs entirely client-side in the browser
- **External dependencies** (loaded from CDN):
  - Google Fonts (Plus Jakarta Sans, JetBrains Mono)
  - JSZip 3.10.1 — for PPTX file parsing
  - PDF.js 3.11.174 — for PDF slide thumbnail rendering and text extraction
- **File System Access API** — Chrome's native save/open dialogs (with download fallback)
- **CSS Grid timeline** — Slides and sections share a single CSS Grid (`2N-1` columns), guaranteeing pixel-perfect alignment

## Data Model

### Plan
```json
{
  "id": "string",
  "name": "string",
  "createdAt": "timestamp",
  "variants": [Variant]
}
```

### Variant
```json
{
  "id": "string",
  "name": "string",
  "totalDuration": "seconds (integer)",
  "hidden": "boolean",
  "slides": [Slide],
  "sections": [Section]
}
```

### Slide
```json
{
  "id": "string",
  "duration": "seconds (integer, multiples of 15, minimum 15)",
  "label": "string (max 15 chars)",
  "thumb": "base64 data URL or null"
}
```

### Section
```json
{
  "id": "string",
  "name": "string (max 20 chars)",
  "startIdx": "integer (0-based slide index)",
  "endIdx": "integer (0-based slide index, inclusive)"
}
```

## Key Design Decisions

### Time Precision
- All durations snap to 15-second increments (`STEP=15`)
- Minimum slide duration is 15 seconds — to remove a slide, delete it
- Enforced in: slider, manual input, divider drag, section redistribution

### CSS Grid Timeline
- Grid has `2N-1` columns for N slides: `[slide1] [divider] [slide2] [divider] ... [slideN]`
- Slide columns: `minmax(60px, Xfr)` where X = slide duration
- Divider columns: fixed `18px`
- Row 1: time markers (span all columns)
- Row 2: slide cards and dividers
- Row 3: section blocks using `grid-column: startCol / endCol+1` to span exactly their slides
- This guarantees sections align perfectly with slides — they share the same column grid

### Section Model
- Every variant always has at least 1 section (the "Full Presentation" default)
- Sections are split via "Split after" buttons in the detail panel
- Sections are merged via ⇔ button between section blocks
- Each variant owns its own sections (independent across variants)
- Sections are visible on ALL variants (dimmed on inactive, interactive on active)
- Sections are contiguous and cover all slides — no gaps, no overlaps
- Adjusting a section's total time redistributes equally across its slides
- Time cascade: takes from next section first, or previous if last section

### Import Strategy
- **PDF import**: Uses PDF.js to render thumbnails AND extract titles via `getTextContent()`. Best option for visual previews.
- **PPTX import**: Uses JSZip to extract titles from slide XML and sections from `ppt/presentation.xml`. No thumbnails.
- Both accessible directly from homepage — goes to Create screen with data pre-filled.

### Save/Load
- First save: Chrome's native "Save As" dialog via File System Access API
- Subsequent saves: Silent overwrite of the same file handle
- Fallback: Standard browser download for non-Chrome browsers
- File format: JSON with the full plan structure
- No localStorage — user owns their files

### UI Principles
- Warm, colorful palette — cream (#faf5ef), indigo accent (#7c5cf5)
- Tooltips on every interactive element
- All buttons have text labels (Undo, Redo, Save, Duration, Slide, Summary, Clone, Hide)
- Desktop-optimized for wide screens (ultrawide 3440×1440 support)
- 4 action cards on homepage: New Plan, Import PDF, Import PPTX, Load Plan
- Summary popup with copy-to-clipboard (replaces file export)

## Feature List

### Core
- Visual horizontal timeline (CSS Grid, proportional columns)
- Drag dividers between slides to redistribute time
- Drag slides to reorder
- Add/remove slides (time redistributes to adjacent)
- Slide labels (15 char max)
- Manual duration input (mm:ss) or slider
- Minimum 15-second slide duration
- Up to 50 slides per variant

### Sections
- Always-visible section bar below timeline, pixel-perfect aligned via shared CSS Grid
- Default: 1 section spanning all slides ("Full Presentation")
- Visible on all variants (dimmed on inactive, interactive on active)
- Click section → detail panel with name, duration slider/input, split options
- Split via numbered buttons in detail panel
- Merge via ⇔ button between section blocks
- Duration adjustment redistributes equally, cascades to adjacent section
- 8 rotating color palettes
- Auto-imported from PPTX sections

### Variants
- Clone to compare pacing strategies
- Diff highlighting (green = longer, red = shorter vs first variant)
- Hide/show variants
- Independent sections per variant

### File Operations
- Import PDF (thumbnails + titles)
- Import PPTX (titles + sections)
- Import saved .json plans
- Save to file (native Chrome dialog)
- Summary popup with copy-to-clipboard (includes sections + slides)

### UX
- Undo/redo (20 levels, global)
- Adjust total duration (distribute equally or add to last)
- Tooltips everywhere
- Labeled toolbar buttons

## Roadmap
- [ ] Keyboard shortcuts
- [ ] Dark mode
- [ ] Presenter countdown mode
- [ ] Mobile/tablet support

## Re-prompting Guide
If the project needs to be rebuilt from scratch, use this prompt:

> Build a single-file HTML presentation timing tool called "PrezTimingTool" by Sylvain Hauser. Warm cream (#faf5ef) / indigo (#7c5cf5) color scheme, Plus Jakarta Sans + JetBrains Mono fonts. CSS Grid timeline with 2N-1 columns (slide columns as minmax(60px, Xfr), divider columns as 18px). Row 1: time markers. Row 2: slide cards with thumbnails, labels, durations. Row 3: section blocks using grid-column spans for pixel-perfect alignment. Features: 15-second precision, 15s minimum duration, max 50 slides, drag dividers, sections (split/merge, duration controls, visible on all variants), multiple variants with diff highlighting, undo/redo (20 levels), PPTX import (titles + sections via JSZip), PDF import (thumbnails + titles via PDF.js 3.11.174 getTextContent), native Chrome file save via File System Access API, Summary popup with copy-to-clipboard. No frameworks — vanilla JS with inline CSS. Desktop optimized. All buttons have text labels. Homepage: 4 action cards (New Plan, Import PDF, Import PPTX, Load Plan). Footer: © 2026 Sylvain Hauser with LinkedIn SVG icon.
