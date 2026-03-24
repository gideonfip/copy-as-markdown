# AGENTS.md - Debug Mode

This file provides debugging-specific guidance for this repository.

## Debug Mode
- Enable in [`vitest.config.ts`](vitest.config.ts) by setting `DEBUG_MODE: true`
- Use `debugLog()` from [`src/utils/debug.ts`](src/utils/debug.ts) for logging
- Debug logging is compile-time controlled - disabled builds have no debug overhead
- When enabled, logs appear in browser extension console (Extension Host)

## Console Output Locations
- Extension popup: Browser popup console
- Settings page: Settings page console  
- Content script: Page console (Inspect Element)
- Background: Background script console (Extensions > Service Workers)

## Common Issues
- Import failures silent: Check browser polyfill is being used correctly
- Tests fail: Ensure test files are co-located with source, not in __tests__/
- Watch mode: Use `npm run test:watch` during development
