# AGENTS.md

This file provides guidance to agents when working with code in this repository.

## Build/Test Commands
- `npm test` - Run all tests
- `vitest run src/path/to/file.test.ts` - Run single test file (vitest accepts full paths)
- `npm run build` - Build all browser targets
- `npm run build:chrome` - Build Chrome extension (outputs to `dist/`)
- `npm run build:firefox` - Build Firefox extension (outputs to `dist_firefox/`)
- `npm run build:safari` - Build Safari extension (outputs to `dist_safari/`)
- `npm run dev` - Dev mode (defaults to Chrome)

## Non-Obvious Patterns

### Custom Browser Polyfill
Always import browser from [`src/utils/browser-polyfill.ts`](src/utils/browser-polyfill.ts), NOT directly from `webextension-polyfill`. This is a project-specific wrapper.

### Tests Are Co-located
Test files (`.test.ts`) must be in the same directory as the source file, not in a separate `__tests__` folder. This is configured in [`vitest.config.ts`](vitest.config.ts).

### Import Aliases
Use tsconfig path aliases instead of relative paths when possible:
- `managers/*` → `src/managers/*`
- `utils/*` → `src/utils/*`
- `icons` → `src/icons`

### DEBUG_MODE
Debug logging is compiled-in based on [`vitest.config.ts`](vitest.config.ts). Set `DEBUG_MODE: true` in config to enable, then use [`src/utils/debug.ts`](src/utils/debug.ts) for logging.

### Browser-Specific Code
The codebase branches heavily on browser type (Chrome/Firefox/Safari). Use [`src/utils/browser-detection.ts`](src/utils/browser-detection.ts) to detect browser and adjust behavior accordingly.

### Filters Organization
Template filters are in [`src/utils/filters/`](src/utils/filters/). Each filter has a validator function that must be exported and registered in [`src/utils/filters.ts`](src/utils/filters.ts).
