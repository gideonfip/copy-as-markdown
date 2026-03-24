# Copy as Markdown

Copy any web page to your clipboard as Markdown to give your LLMs full context. Forked from Obsidian Web Clipper extension.

## Features

- **One-click copy**: Press a keyboard shortcut (`Command+Shift+X` or `Ctrl+Shift+X`) to copy the current page as Markdown
- **LLM-ready output**: Formatted content that can be pasted directly into ChatGPT, Claude, Gemini, or any LLM
- **Smart extraction**: Uses Defuddle for intelligent content extraction
- **Preserves formatting**: Maintains headings, lists, code blocks, and more

## Installation

### Prerequisites

You'll need [Node.js](https://nodejs.org/) installed (v18 or later recommended). You can verify by running `node -v` in your terminal.

### Step 1 — Download the source code

1. Go to this repository on GitHub
2. Click the green **Code** button → **Download ZIP**
3. Unzip the downloaded file somewhere on your computer (e.g. your Desktop or Documents folder)

### Step 2 — Open a terminal in the project folder

**VS Code (recommended):**
1. Open VS Code
2. Go to **File → Open Folder** and select the unzipped folder
3. Open the integrated terminal: **Terminal → New Terminal** (or `` Ctrl+` `` / `` Cmd+` ``)

**Mac:**
Right-click the unzipped folder in Finder → **New Terminal at Folder**

**Windows:**
Open the unzipped folder in File Explorer, then click the address bar, type `cmd`, and press Enter

### Step 3 — Install dependencies

In the terminal, run:

```
npm install
```

This downloads all required packages into a `node_modules` folder. It only needs to be done once.

### Step 4 — Build the extension

```
npm run build:chrome
```

This creates a `dist/` folder with the built extension files.

### Step 5 — Load the extension in Chrome / Brave / Edge

1. Open your browser and navigate to `chrome://extensions` (or `brave://extensions`)
2. Enable **Developer mode** (toggle in the top-right corner)
3. Click **Load unpacked**
4. Select the `dist` folder inside the project folder
5. The extension icon will appear in your toolbar

The extension stays installed even after closing your browser. After making code changes, rebuild with `npm run build:chrome` and click the refresh icon on the extension card.

### Firefox

```
npm run build:firefox
```

1. Open Firefox and navigate to `about:debugging#/runtime/this-firefox`
2. Click **Load Temporary Add-on**
3. Open the `dist_firefox` folder and select `manifest.json`

> Note: Firefox requires reloading the temporary add-on each time you restart the browser.

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

## Forked from

This project is a fork of [Obsidian Web Clipper](https://github.com/obsidianmd/obsidian-clipper)
