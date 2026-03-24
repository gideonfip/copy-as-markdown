# AGENTS.md - Architect Mode

This file provides architectural guidance for this repository.

## Architecture Overview
This is a browser extension (Chrome/Firefox/Safari) that clips web content to Obsidian notes. It uses a template system with filters similar to Liquid.

## Key Architectural Decisions

### Browser-Specific Code
The `browser-detection.ts` module is critical - all three browser builds share code but have subtle differences in APIs and behavior.

### Template System
- Templates use a custom filter system (not LiquidJS)
- Filters are in `src/utils/filters/` with validator functions
- Each filter must be registered in `src/utils/filters.ts`

### Entry Points
- `popup.ts` - Main clipping UI (runs in extension popup)
- `settings.ts` - Settings page (runs in extension options page)
- `content.ts` - Injected into web pages
- `background.ts` - Service worker (browser-specific)

### Build Output
- Three separate output directories for cross-browser compatibility
- Webpack bundles all TypeScript into JS for each entry point

### Storage
- Uses browser.storage for settings
- Templates stored as compressed JSON (lz-string)

### Testing Strategy
- Unit tests co-located with source (Vitest)
- Integration tests with fixture HTML files in `src/utils/fixtures/`