# Roadmap: Obsidian Extract URL Improvements

This document outlines the planned improvements for the Obsidian Extract URL plugin to enhance performance, reliability, and code quality.

## ✅ Phase 1: Performance Optimization
- [ ] **Parallel Archiving:** Implement concurrent URL processing in `Archive` mode using `futures::future::join_all`.
- [ ] **Streamlined UI Notifications:** Replace per-URL notices with a consolidated progress indicator or a single completion message.
- [ ] **Minimize JS/Rust Bridge Overhead:** Optimize data structures passed between the WASM and JavaScript layers.

## 🛠️ Phase 2: Reliability & UX
- [ ] **Robust Link Extraction:** Improve link detection regex/logic to handle complex URLs and edge cases in markdown.
- [ ] **Comprehensive Error Handling:** Ensure all network and transformation errors are reported clearly to the user with actionable feedback.
- [ ] **Reliable Fallbacks:** Improve the transformation pipeline to guarantee a fallback to basic readability if specialized transformers (oEmbed, GitHub) fail.

## 🧹 Phase 3: Refactoring & Maintenance
- [ ] **DRY Transformation Logic:** Consolidate `readable_content` and `readable_title` to share the same extraction base.
- [ ] **Type Safety:** Replace `inline_js` blocks with standard `js-sys` or `web-sys` bindings.
- [ ] **Test Expansion:** Add unit tests for complex HTML structures and edge-case URLs.

## 🚀 Phase 4: Enhanced Features
- [ ] **Retry Mechanism:** Add automatic retries for transient network failures.
- [ ] **Local Caching:** Cache transformation results to avoid redundant network requests for recently processed URLs.
