# ⏱ PrezTimingTool

**Plan and fine-tune your presentation slide timing with an intuitive visual timeline.**

A free, open-source, single-file web tool that helps presenters allocate and adjust time across slides. No installation, no accounts, no tracking — just open and go.

🔗 **[Use it now → sylvainservicenow.github.io/preztimingtool](https://sylvainservicenow.github.io/preztimingtool)**

## ✨ Features

- **Visual timeline** — Horizontal slide blocks sized proportionally to duration (CSS Grid)
- **Sections** — Group slides into sections with independent timing control; split, merge, drag-reorder
- **PDF import** — Slide thumbnails + titles extracted from text content
- **PPTX import** — Slide titles + sections (hidden slides auto-detected and skipped)
- **PDF + PPTX combo** — Import both for thumbnails from PDF + sections/titles from PPTX
- **Lock slides/sections** — 🔒 Lock durations so they don't change when adjusting others
- **Slide hover preview** — Large thumbnail popup when hovering slides with images
- **Multiple variants** — Clone timing plans to compare pacing (e.g. 15-min vs 30-min)
- **Drag dividers** — Redistribute time between adjacent slides
- **15-second precision** — All durations snap to 15s increments, 15s minimum
- **Summary popup** — Copy-to-clipboard timing breakdown with sections
- **Undo/Redo** — 20 levels, global across all actions
- **Save/Load** — Native Chrome file dialog, .json format
- **Desktop optimized** — Designed for wide screens

## 🚀 Quick Start

### Use online (recommended)
Visit **[sylvainservicenow.github.io/preztimingtool](https://sylvainservicenow.github.io/preztimingtool)**

### Run locally
1. Download `index.html`
2. Open it in Chrome
3. That's it — no server, no build step

## 📂 Import Options

| Format | What it imports | Thumbnails? | Sections? |
|--------|----------------|-------------|----------|
| **PDF** | Slide count + titles + previews | ✅ Real images | ❌ |
| **PPTX** | Slide count + titles + sections | ❌ | ✅ Auto-imported |
| **PDF + PPTX** | Best of both | ✅ From PDF | ✅ From PPTX |
| **JSON** | Full saved plan | N/A | N/A |

> 💡 Hidden slides in PPTX are automatically detected and skipped to match PDF export.

## 🛠 Technical Details

- **Single HTML file** — No build step, no bundler, no framework
- **Vanilla JavaScript** — No React, no Vue, no jQuery
- **CDN dependencies**: Google Fonts, JSZip (PPTX parsing), PDF.js (thumbnail rendering)
- **CSS Grid timeline** — Slides and sections share grid columns for pixel-perfect alignment
- **File System Access API** — Native Chrome file save with download fallback

## 📋 Documentation

See [DOCS.md](DOCS.md) for full architecture, data model, design decisions, and re-prompting guide.
See [CHANGELOG.md](CHANGELOG.md) for version history.

## 🤝 Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md). Please keep the single-file architecture.

## 📄 License

MIT License — see [LICENSE](LICENSE).

---
© 2026 [Sylvain Hauser](https://www.linkedin.com/in/sylvainhauser/) — Built with ❤️ for the presentation community
