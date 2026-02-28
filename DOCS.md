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
  - PDF.js 3.11.174 — for PDF slide thumbnail rendering
- **File System Access API** — Chrome's native save/open dialogs (with download fallback)
- **Unified scroll container** — Timeline slides and section bar share one horizontal scroll, ensuring perfect alignment

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
- Minimum slide duration is 15 seconds — to remove a slide, delete it instead
- This prevents micro-adjustments that aren't useful for presentation timing

### Section Model
- Every variant always has at least 1 section (the "Full Presentation" default)
- Sections are split/merged via the detail panel or merge buttons between section blocks
- Each variant owns its own sections (independent across variants)
- Sections are contiguous and cover all slides — no gaps, no overlaps
- Adjusting a section's total time redistributes equally across its slides
- Time cascade: takes from next section first, or previous section if it's the last one
- Section bar renders one cell per slide, colored by section — this guarantees pixel-perfect alignment with slides above

### Import Strategy
- **PDF import**: Uses PDF.js to render each page as a canvas → JPEG thumbnail. Provides real visual slide previews on the timeline. No titles extracted.
- **PPTX import**: Uses JSZip to parse the XML inside the .pptx archive. Extracts slide titles from title placeholders and sections from `ppt/presentation.xml` (`p14:section` elements). No thumbnails (PowerPoint doesn't store per-slide screenshots).
- Both can be used directly from the homepage — goes to Create screen with data pre-filled.

### Save/Load
- First save: Chrome's native "Save As" dialog via File System Access API
- Subsequent saves: Silent overwrite of the same file handle
- Fallback: Standard browser download for non-Chrome browsers
- File format: JSON with the full plan structure
- No localStorage — user owns their files

### UI Principles
- Warm, colorful palette — cream background (#faf5ef), indigo accent (#7c5cf5)
- Tooltips on every interactive element
- All buttons have text labels (not icon-only)
- Desktop-optimized, designed for wide screens (ultrawide 3440×1440 support)
- Generous vertical spacing — elements breathe
- 4 action cards on homepage: New Plan, Import PDF, Import PPTX, Load Plan

## Feature List

### Core
- Visual horizontal timeline with proportionally-sized slide blocks (flex-grow based)
- Drag dividers between slides to redistribute time
- Drag slides to reorder
- Add/remove slides (time redistributes to adjacent slide)
- Slide labels (15 char max)
- Manual duration input (mm:ss format) or slider
- Minimum 15-second slide duration
- Up to 50 slides per variant

### Sections
- Always-visible section bar below timeline, perfectly aligned with slides
- Default: 1 section spanning all slides ("Full Presentation")
- Click a section to select → shows detail panel with name, duration slider/input, split options
- Split a section by clicking slide number buttons in the detail panel
- Merge sections via ⇔ button between section blocks
- Adjust section total time → redistributes equally within section, cascades to adjacent
- Section colors rotate through 8 distinct palettes
- Sections imported from PPTX automatically

### Variants
- Clone variants to compare different pacing strategies
- Variant diff highlighting (green = longer, red = shorter vs first variant)
- Hide/show variants
- Each variant has independent sections

### File Operations
- Import PDF (with slide thumbnails)
- Import PPTX (with titles and sections)
- Import saved .json plans
- Save to file (native Chrome dialog)
- Export timing sheet as .txt

### UX
- Undo/redo (20 levels, global)
- Adjust total duration (distribute equally or add to last slide)
- Tooltips everywhere
- Labeled toolbar buttons (Undo, Redo, Save, Duration, Slide, Export, Clone, Hide)

## Roadmap
- [ ] Keyboard shortcuts
- [ ] Dark mode
- [ ] Presenter countdown mode
- [ ] Mobile/tablet support
- [ ] Speaker notes per slide

## Re-prompting Guide
If the project needs to be rebuilt from scratch, use the following prompt:

> Build a single-file HTML presentation timing tool called "PrezTimingTool" by Sylvain Hauser. Warm cream (#faf5ef) / indigo (#7c5cf5) color scheme, Plus Jakarta Sans + JetBrains Mono fonts. Features: visual horizontal timeline with flex-grow proportional slide blocks (15-second precision, 15s minimum, max 50 slides), drag dividers to redistribute time, sections below timeline in a unified scroll container (one colored cell per slide for pixel-perfect alignment), sections split/merge with duration controls, multiple timing variants with diff highlighting, undo/redo (20 levels), PPTX import (titles + sections via JSZip), PDF import (thumbnails via PDF.js 3.11.174), native Chrome file save via File System Access API, export timing sheet as text. No frameworks — vanilla JS with inline CSS. Desktop optimized. All buttons have text labels. Homepage has 4 action cards: New Plan, Import PDF, Import PPTX, Load Plan. Footer: © 2026 Sylvain Hauser with LinkedIn link.
