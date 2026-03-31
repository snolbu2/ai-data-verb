# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the App

Open `index.html` directly in a browser — no build step, no server, no dependencies.

## Architecture

The entire application is a single self-contained file (`index.html`) with inline CSS and JavaScript. There is no build system, package manager, or external dependencies.

**Data:** A hardcoded `QUOTES` array (24 items) at the top of the `<script>` block. Each quote has `id`, `text`, `author`, `role`, `cat`, and `color`.

**State:** Three module-level variables drive the UI:
- `likes` — object keyed by quote id tracking liked status
- `currentFilter` — active category string (`"all"`, `"wisdom"`, etc.)
- `currentSearch` — current search string

**Rendering:** Two main render functions called together after any state change:
- `renderFeatured()` — updates the large featured quote section
- `renderGrid()` — re-renders all quote cards based on `getFiltered()`

**`getFiltered()`** — returns the subset of `QUOTES` matching both `currentFilter` and `currentSearch` (searches `text` and `author` fields, case-insensitive).

**Categories:** `all`, `wisdom`, `courage`, `success`, `life`, `love`, `change`

**UI feedback:** A toast notification system (`showToast()`) handles copy-to-clipboard confirmation.
