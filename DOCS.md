# PrezTimingTool — Project Documentation

## Overview
PrezTimingTool is a browser-based presentation slide timing planner. Single HTML file, zero server dependencies.

**Live**: https://sylvainservicenow.github.io/preztimingtool
**Author**: © 2026 Sylvain Hauser — https://www.linkedin.com/in/sylvainhauser/

## Architecture
- **Single file**: `index.html` — HTML, CSS, JavaScript
- **CDN dependencies**: Google Fonts, JSZip 3.10.1, PDF.js 3.11.174
- **File System Access API** — Chrome native save/open with download fallback
- **CSS Grid timeline** — `2N-1` columns shared by slides and sections

## Data Model

### Plan
```json
{"id": "string", "name": "string", "createdAt": "timestamp", "variants": [Variant]}
```

### Variant
```json
{"id": "string", "name": "string", "totalDuration": "seconds", "hidden": "boolean", "slides": [Slide], "sections": [Section]}
```

### Slide
```json
{"id": "string", "duration": "seconds (multiples of 15, min 15)", "label": "string (max 15)", "thumb": "base64 or null", "locked": "boolean"}
```

### Section
```json
{"id": "string", "name": "string (max 20)", "startIdx": "int", "endIdx": "int (inclusive)", "locked": "boolean"}
```

## Key Design Decisions

### Time: 15s precision, 15s minimum. Delete slide to remove it.

### CSS Grid Timeline
- `2N-1` columns: `[slide] [18px divider] [slide] ...`
- Slide columns: `minmax(60px, Xfr)` where X = duration
- Row 1: time markers. Row 2: slides + dividers. Row 3: section blocks via `grid-column` spans

### Sections
- Always ≥1 section ("Full Presentation" default)
- Split via detail panel numbered buttons, merge via ⇔ between blocks
- Drag-reorder sections (moves slides with them)
- Visible on all variants (dimmed on inactive)
- Duration cascade: takes from next unlocked section, or previous if last

### Locking
- Lock individual slides or entire sections
- Locked = completely frozen during redistribution
- Visual: 🔒 icon on cards, clear message in detail panel
- Duration changes skip locked items, cascade to unlocked

### Import
- **PDF**: thumbnails via canvas render + titles via `getTextContent()`
- **PPTX**: titles from XML + sections from `p14:section` + hidden slide detection (`show="0"`)
- **Combo**: dedicated screen, validates matching slide counts
- Loading spinner during all imports

### Homepage: 5 action cards on single row — New Plan, Import PDF, Import PPTX, PDF+PPTX, Load Plan

### Save: Chrome File System Access API → silent overwrite. Fallback: download.

### Slide Hover Preview: 360px popup with full thumbnail + title + duration when thumbnails exist.

## Re-prompting Guide

> Build a single-file HTML presentation timing tool called "PrezTimingTool" by Sylvain Hauser. Warm cream (#faf5ef) / indigo (#7c5cf5), Plus Jakarta Sans + JetBrains Mono. CSS Grid timeline (2N-1 columns: minmax(60px,Xfr) slides + 18px dividers). Row 1: markers. Row 2: slide cards with thumbnails, labels, lock icons, drag-reorder. Row 3: section blocks via grid-column spans. Features: 15s precision/minimum, max 50 slides, drag dividers, sections (split/merge/drag-reorder/lock), variants with diff highlighting, undo/redo (20), PPTX import (titles + sections + hidden slide detection via JSZip), PDF import (thumbnails + titles via PDF.js 3.11.174 getTextContent), combo PDF+PPTX import screen, lock slides/sections (🔒, skip during redistribution), slide hover preview popup (360px), Summary popup with copy-to-clipboard, native Chrome file save. Vanilla JS, inline CSS. Desktop optimized. 5 homepage cards: New Plan, Import PDF, Import PPTX, PDF+PPTX, Load Plan. Footer: © 2026 Sylvain Hauser with LinkedIn SVG.
