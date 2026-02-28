# ⏱ PrezTimingTool

**Plan and fine-tune your presentation slide timing with an intuitive visual timeline.**

A free, open-source, single-file web tool that helps presenters allocate and adjust time across slides. No installation, no accounts, no tracking — just open and go.

🔗 **[Use it now → sylvainservicenow.github.io/preztimingtool](https://sylvainservicenow.github.io/preztimingtool)**

## ✨ Features

- **Visual timeline** — Horizontal slide blocks sized proportionally to duration
- **Drag dividers** — Redistribute time between adjacent slides by dragging
- **Drag to reorder** — Rearrange slides on the timeline
- **15-second precision** — All durations snap to 15-second increments
- **Multiple variants** — Clone timing plans to compare different pacing strategies
- **Variant diff highlighting** — Visual indicators show where variants differ
- **Undo/Redo** — Up to 20 levels of undo, global across all actions
- **Save to file** — Native "Save As" dialog (Chrome) to store `.json` files locally
- **Import plans** — Load previously saved `.json` plans
- **Export timing sheet** — Generate a text file with cumulative timestamps per slide
- **Adjust total duration** — Change presentation length and redistribute equally or to last slide
- **Zero-duration slides** — Simulate hidden slides (greyed out on timeline)
- **Slide labels** — Optional 15-character labels for quick identification
- **Add/remove slides** — Insert anywhere, remove with time redistribution to adjacent slide
- **Up to 50 slides** supported
- **Desktop optimized** — Designed for wide screens

## 🚀 Quick Start

### Use online (recommended)
Visit **[sylvainservicenow.github.io/preztimingtool](https://sylvainservicenow.github.io/preztimingtool)**

### Run locally
1. Download `index.html`
2. Open it in Chrome
3. That's it — no server, no build step, no dependencies

## 💾 How Save Works

- Click the save button (💾) to save your plan as a `.json` file
- **First save**: Opens Chrome's native "Save As" dialog — pick your folder and filename
- **Subsequent saves**: Silently overwrites the same file (no dialog)
- **Import**: Load any saved `.json` file back into the tool

> Note: The native file save requires Chrome. In other browsers, it falls back to a standard download.

## 🛠 Technical Details

- **Single HTML file** — No build step, no bundler, no framework
- **Zero dependencies** — Only Google Fonts (Plus Jakarta Sans, JetBrains Mono)
- **Vanilla JavaScript** — No React, no Vue, no jQuery
- **File System Access API** — Native Chrome file save/open
- Works offline after first load (fonts cached by browser)

## 📋 Roadmap

- [ ] PowerPoint (.pptx) import with slide thumbnails
- [ ] Keyboard shortcuts
- [ ] Dark mode
- [ ] Presenter countdown mode
- [ ] Mobile/tablet support

## 🤝 Contributing

Contributions are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

Built with ❤️ for the presentation community. If this tool helps you nail your timing, give it a ⭐!
