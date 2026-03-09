# Contributing to PrezTimingTool

Thanks for your interest! Here's how to get started.

## Architecture

**Single-file application.** Everything lives in `index.html`. This is intentional — no build step, instant download-and-run. **Please maintain this.**

See [DOCS.md](DOCS.md) for data model, design decisions, and technical details.

## How to Contribute

1. **Fork** the repository
2. **Clone** your fork locally
3. **Open** `index.html` in Chrome to test
4. **Make changes** directly to `index.html`
5. **Test** thoroughly:
   - Timeline: drag dividers, reorder slides, add/remove slides
   - Sections: split, merge, drag-reorder, adjust duration, verify grid alignment
   - Locking: lock slides, lock sections, verify redistribution skips locked items
   - Import: PDF (thumbnails + titles), PPTX (titles + sections + hidden slides), combo
   - Undo/redo across all operations
   - Save/load .json files
   - Variants: clone, diff highlighting, hide/show, sections visible on all
   - Hover preview: verify popup shows on slides with thumbnails
6. **Commit** with clear messages
7. **Push** and open a **Pull Request**

## Guidelines

- Keep all code in `index.html`
- CDN dependencies only: JSZip, PDF.js, Google Fonts
- Test in Chrome (primary target)
- Add `data-tip` tooltips to all interactive elements
- All buttons must have text labels
- Maintain undo/redo for state-changing operations
- Minimum slide duration: 15 seconds (`STEP`)
- Sections must always cover all slides, no gaps
- Locked items must never have their duration changed by redistribution

## Reporting Issues

Open an issue with: expected behavior, actual behavior, browser version, steps to reproduce.

## Feature Requests

Open an issue tagged "enhancement" with: problem, proposed solution, alternatives considered.
