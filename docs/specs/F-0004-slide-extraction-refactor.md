# F-0004: Slide Extraction Refactor

**Type:** Refactor
**Priority:** P1 (important)
**Status:** In Progress
**Requested by:** PO
**Date:** 2026-05-27

## Problem

`index.html` has grown bloated with all 7 slides defined inline. Each slide is a large HTML block, making the file difficult to read, navigate, and maintain. Extracting slides into separate files improves maintainability and keeps `index.html` focused on layout, navigation, and behavior.

## Requirements

1. Create a `slides/` directory at the repo root.
2. Extract each of the 7 slides into individual HTML fragment files: `slides/slide-1.html` through `slides/slide-7.html`. Each file contains only the `<div class="slide" id="slide-N">...</div>` element — no `<html>`, `<head>`, or `<body>` wrappers.
3. `index.html` retains all CSS, the empty `<div id="stage"></div>`, nav buttons, and all JS. No structural or visual changes to the page.
4. The `#dots` div in `index.html` is emptied of static markup — dots are generated dynamically by JS after slides load.
5. JS is updated to:
   a. Fetch slides sequentially (`slides/slide-1.html` through `slides/slide-7.html`).
   b. Inject each fetched HTML fragment into `#stage`.
   c. Generate one `.dot` div per slide and append to `#dots`.
   d. Mark the first slide and first dot as active.
   e. Run the existing navigation logic (arrow keys, button clicks, dot clicks, transitions) unchanged.
6. Slide count strategy: SWE-1 picks the simpler of (a) a hardcoded `const SLIDE_COUNT = 7` constant, or (b) auto-discovery by fetching in a loop and stopping on a non-ok (404) response.
7. All existing navigation behavior (arrow keys, prev/next buttons, dot indicators, slide transitions) must work identically after the refactor.
8. Zero content changes — slides are extracted verbatim from `index.html` with no edits to copy or markup.
9. Work is committed directly to `master` — no feature branch.

## Acceptance Criteria

- [ ] `slides/` directory exists with exactly 7 `.html` fragment files (`slide-1.html` through `slide-7.html`).
- [ ] Each fragment file contains only the `<div class="slide" id="slide-N">` element; no `<html>`, `<head>`, or `<body>` tags.
- [ ] `index.html` has no inline slide `<div class="slide">` markup remaining — `#stage` is empty on initial load.
- [ ] `#dots` in `index.html` has no static dot markup — dots are injected by JS.
- [ ] On page load, all 7 slides load and render correctly in the browser.
- [ ] Dot indicators (one per slide) appear and reflect the active slide.
- [ ] Arrow-key navigation, prev/next button navigation, and dot-click navigation all work as before.
- [ ] Slide transition animations are visually identical to pre-refactor behavior.
- [ ] Slide content is byte-for-byte identical to the extracted source (no copy changes).
- [ ] All changes committed directly to `master` with no feature branch.

## Out of Scope

- Any content edits, copy changes, or visual design changes to slides.
- Adding new slides or removing existing slides.
- CSS or animation changes.
- Test automation (no SWE-Test step for this refactor).
- Feature branching — commits go directly to `master`.

## Dependencies

- F-0001, F-0002, F-0003 (all done — slide content is stable)

## Open Questions

- None. SWE-1 decides between `const SLIDE_COUNT = 7` and auto-discovery based on simplicity.