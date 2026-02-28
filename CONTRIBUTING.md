# Contributing to PrezTimingTool

Thanks for your interest in contributing! Here's how to get started.

## Architecture

This is a **single-file application**. The entire tool lives in `index.html` — HTML, CSS, and JavaScript all in one file. This is intentional:

- No build step needed
- Anyone can download and run it instantly
- Easy to understand the full codebase
- Simple deployment (just serve the file)

**Please maintain this architecture** in your contributions.

## How to Contribute

1. **Fork** the repository
2. **Clone** your fork locally
3. **Open** `index.html` in Chrome to test
4. **Make changes** directly to `index.html`
5. **Test** thoroughly (timeline drag, undo/redo, save/load, variants)
6. **Commit** with clear messages
7. **Push** and open a **Pull Request**

## Guidelines

- Keep all code in `index.html`
- No external JS dependencies (Google Fonts for CSS is the only external resource)
- Test in Chrome (primary target browser)
- Maintain the existing code style
- Add tooltips (`data-tip`) to all interactive elements
- Maintain undo/redo support for all state-changing operations

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
