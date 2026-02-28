# ⏱ PrezTimingTool

**Plan and fine-tune your presentation slide timing with an intuitive visual timeline.**

A free, open-source, single-file web tool that helps presenters allocate and adjust time across slides. No installation, no accounts, no tracking — just open and go.

🔗 **[Use it now → sylvainservicenow.github.io/preztimingtool](https://sylvainservicenow.github.io/preztimingtool)**

## ✨ Features

- **Visual timeline** — Horizontal slide blocks sized proportionally to duration
- **Sections** — Group slides into sections with independent timing control; split and merge sections visually
- **Drag dividers** — Redistribute time between adjacent slides by dragging
- **Drag to reorder** — Rearrange slides on the timeline
- **15-second precision** — All durations snap to 15-second increments
- **PDF import** — Import a PDF of your presentation with real slide thumbnail previews
- **PPTX import** — Import PowerPoint files to extract slide count, titles, and sections
- **Multiple variants** — Clone timing plans to compare different pacing strategies (e.g. 15-min vs 30-min)
- **Variant diff highlighting** — Visual indicators show where variants differ
- **Undo/Redo** — Up to 20 levels of undo, global across all actions
- **Save/Load** — Native Chrome file save dialog, or standard download in other browsers
- **Export timing sheet** — Generate a text file with cumulative timestamps per slide
- **Up to 50 slides** per variant, desktop optimized

## 🚀 Quick Start

### Use online (recommended)
Visit **[sylvainservicenow.github.io/preztimingtool](https://sylvainservicenow.github.io/preztimingtool)**

### Run locally
1. Download `index.html`
2. Open it in Chrome
3. That's it — no server, no build step

## 📂 Import Options

| Format | What it imports | Thumbnails? |
|--------|----------------|-------------|
| **PDF** | Slide count + visual previews | ✅ Real slide images |
| **PPTX** | Slide count + titles + sections | ❌ No thumbnails |
| **JSON** | Full saved plan with all settings | N/A |

> 💡 **Tip**: Export your PowerPoint as PDF first for the best experience — you get both visual thumbnails AND can manually add sections.

## 🛠 Technical Details

- **Single HTML file** — No build step, no bundler, no framework
- **Vanilla JavaScript** — No React, no Vue, no jQuery
- **CDN dependencies**: Google Fonts, JSZip (PPTX parsing), PDF.js (thumbnail rendering)
- **File System Access API** — Native Chrome file save/open with download fallback
- Works offline after first load

## 📋 Documentation

See [DOCS.md](DOCS.md) for full architecture, data model, design decisions, and re-prompting guide.

## 🤝 Contributing

Contributions are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines. Please keep the single-file architecture.

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

Built with ❤️ for the presentation community. If this tool helps you nail your timing, give it a ⭐!
