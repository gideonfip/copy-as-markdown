# AGENTS.md - Code Mode

This file provides coding-specific guidance for this repository.

## Required Import Patterns

### Browser Polyfill
Always use: `import browser from './utils/browser-polyfill'`  
Do NOT use: `import browser from 'webextension-polyfill'`

### Template Filters
Each filter in `src/utils/filters/` must export both:
- The filter function
- A validator function (`validate*Params`)
- Register in `src/utils/filters.ts` for it to be available in templates

## TypeScript
- Strict mode is enabled in tsconfig.json
- Path aliases available: `managers/*`, `utils/*`, `icons`

## Browser Detection
Use `detectBrowser()` from `src/utils/browser-detection.ts` for any browser-specific behavior. The codebase has conditional logic for Chrome, Firefox, and Safari.
