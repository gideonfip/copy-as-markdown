# Copy as Markdown

Copy any web page to your clipboard as Markdown to give your LLMs full context. Forked from Obsidian Web Clipper extension.

## Features

- **One-click copy**: Press a keyboard shortcut to copy the current page as Markdown
- **LLM-ready output**: Formatted content perfect for pasting into ChatGPT, Claude, Gemini, or any LLM
- **Smart extraction**: Uses Defuddle for intelligent content extraction
- **Preserves formatting**: Maintains headings, lists, code blocks, and more

## Installation

### From Source (Developer Mode)

1. Build the extension:
   ```
   npm run build:chrome
   ```
2. Open your browser and navigate to `chrome://extensions`
3. Enable **Developer mode**
4. Click **Load unpacked** and select the `dist` directory
5. The extension will remain installed even after closing your browser - just reload after making changes

### Firefox

1. Build the extension:
   ```
   npm run build:firefox
   ```
2. Open Firefox and navigate to `about:debugging#/runtime/this-firefox`
3. Click **Load Temporary Add-on**
4. Navigate to the `dist_firefox` directory and select the `manifest.json` file

## Keyboard Shortcuts

- **Mac**: Command+Shift+X - Copy page to clipboard
- **Windows/Linux**: Ctrl+Shift+X - Copy page to clipboard

## Usage

1. Navigate to any webpage
2. Press the keyboard shortcut (or click the extension icon)
3. The page content is copied to your clipboard as Markdown
4. Paste directly into your LLM chat

## Building

```
npm run build        # Build all browser targets
npm run build:chrome # Build Chrome/Brave/Edge
npm run build:firefox # Build Firefox
npm run build:safari # Build Safari
```

### Development Mode

To avoid rebuilding after every code change:

```
npm run dev
```

Then load the `dist` directory. The extension will auto-reload when you make changes.

### Packing the Extension (Permanent Installation)

To make the extension permanent without publishing to the Chrome Web Store:

1. Build the extension: `npm run build:chrome`
2. Open brave://extensions/ (or chrome://extensions/)
3. Enable **Developer mode**
4. Click **Pack extension** (not "Pack loader")
5. In the dialog:
   - Extension root directory: Select the `dist` folder
   - Private key file: Leave empty (it will generate one)
6. Click **Pack Extension**
7. Two files will be created in your project root:
   - `dist.crx` - The packed extension file
   - `dist.pem` - Your private key (keep this safe!)

To install the packed extension, drag the `dist.crx` file into brave://extensions/.

The .crx file can be shared and installed on any Chrome/Brave/Edge browser.

## Third-party libraries

- [webextension-polyfill](https://github.com/mozilla/webextension-polyfill) for browser compatibility
- [defuddle](https://github.com/kepano/defuddle) for content extraction and Markdown conversion
- [dayjs](https://github.com/iamkun/dayjs) for date parsing and formatting
- [lz-string](https://github.com/pieroxy/lz-string) to compress templates to reduce storage space
