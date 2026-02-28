# Contributing to PrezTimingTool

Thanks for your interest in contributing! Here's how to get started.

## Architecture

This is a **single-file application**. The entire tool lives in `index.html` — HTML, CSS, and JavaScript all in one file. This is intentional:

- No build step needed
- Anyone can download and run it instantly
- Easy to understand the full codebase
- Simple deployment (just serve the file)

**Please maintain this architecture** in your contributions.

See [DOCS.md](DOCS.md) for the full data model, design decisions, and technical details.

## How to Contribute

1. **Fork** the repository
2. **Clone** your fork locally
3. **Open** `index.html` in Chrome to test
4. **Make changes** directly to `index.html`
5. **Test** thoroughly:
   - Timeline: drag dividers, reorder slides, add/remove slides
   - Sections: split, merge, adjust duration, verify alignment with slides
   - Undo/redo across all operations
   - Save/load .json files
   - Import PDF and PPTX
   - Variants: clone, diff highlighting, hide/show
6. **Commit** with clear messages
7. **Push** and open a **Pull Request**

## Guidelines

- Keep all code in `index.html`
- CDN dependencies only: JSZip, PDF.js, Google Fonts — no npm, no bundler
- Test in Chrome (primary target browser)
- Maintain the existing code style (compact, minimal whitespace)
- Add `data-tip` tooltips to all interactive elements
- All buttons must have text labels (no icon-only buttons)
- Maintain undo/redo support for all state-changing operations
- Minimum slide duration is 15 seconds (STEP constant)
- Sections must always cover all slides with no gaps

## Reporting Issues

Open an issue with:
- What you expected to happen
- What actually happened
- Browser version
- Steps to reproduce

## Feature Requests

Open an issue tagged with "enhancement" and describe:
- The problem you're trying to solve
- Your proposed solution
- Any alternatives you've considered
