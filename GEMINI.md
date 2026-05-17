# Obsidian Extract URL - Development Guide

This project is an Obsidian plugin that transforms URLs into markdown content. It leverages Rust compiled to WebAssembly (WASM) for robust web scraping and content extraction.

## 🏗️ Architecture

- **Frontend (JavaScript):** `index.js` acts as the entry point. It loads the compiled WASM binary and initializes the plugin within Obsidian.
- **Core Logic (Rust):** The majority of the plugin's logic is written in Rust (`src/`). It handles:
    - **Obsidian Integration:** Managed via `wasm-bindgen` in `src/obsidian.rs`.
    - **URL Extraction:** Located in `src/extract.rs`.
    - **Content Transformation:** Found in `src/transform/`, including special handlers for GitHub and oEmbed.
    - **Readability:** Uses a custom implementation to extract the main content from HTML.

## 🚀 Building and Running

The project uses `wasm-pack` and `esbuild`.

- **Development Build:**
  ```bash
  yarn dev
  ```
  Compiles Rust with debug flags and bundles the JavaScript for quick iteration.

- **Release Build:**
  ```bash
  yarn build
  ```
  Optimizes the WASM binary and minifies the JavaScript for distribution.

- **Installation:**
  After building, the plugin files (`main.js`, `manifest.json`, and the bundled WASM) should be placed in your Obsidian vault's `.obsidian/plugins/obsidian-extract-url/` directory.

## 🛠️ Development Conventions

- **Rust/WASM Bridge:** Most Obsidian API calls are wrapped in `src/obsidian.rs`. When adding new interactions with Obsidian, update this file with the necessary `wasm-bindgen` externs.
- **Error Handling:** The project uses `thiserror` for descriptive Rust errors. Ensure new logic provides meaningful error variants.
- **Debugging:** `web_sys::console::log` can be used for logging from Rust to the Obsidian developer console (accessible via `Ctrl+Shift+I` in Obsidian).

## 📂 Key Files

- `index.js`: JavaScript entry point; initializes WASM.
- `manifest.json`: Obsidian plugin metadata.
- `src/lib.rs`: Rust entry point; registers commands and settings tabs.
- `src/extract.rs`: Core URL-to-markdown extraction logic.
- `src/transform/`: Directory for URL-specific content formatters.
- `src/obsidian.rs`: Bindings to the Obsidian JavaScript API.
- `src/request.rs`: Logic for fetching external URL content.
