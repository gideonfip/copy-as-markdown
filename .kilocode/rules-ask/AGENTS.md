# AGENTS.md - Ask Mode

This file provides contextual information for understanding this repository.

## Project Overview
This is the **Obsidian Web Clipper** - an official browser extension for clipping web pages to Obsidian.

## Key Components
- `src/core/popup.ts` - Main popup UI (clipping interface)
- `src/core/settings.ts` - Settings page
- `src/content.ts` - Content script (injected into pages)
- `src/background.ts` - Background service worker
- `src/utils/filters/` - Template filters (like Liquid filters)
- `src/utils/interpreter.ts` - AI/LLM integration for prompt processing

## Browser Builds
Three separate builds: Chrome (`dist/`), Firefox (`dist_firefox/`), Safari (`dist_safari/`)

## Documentation
- `docs/` folder contains user documentation
- `docs/Filters.md` - Template filter reference
- `docs/Templates.md` - Template system documentation
- `docs/Variables.md` - Variable system documentation
