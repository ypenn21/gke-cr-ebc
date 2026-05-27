# F-0003: Cloud Run Enables Slide

**Type:** Feature
**Priority:** P0 (critical)
**Status:** In Progress
**Requested by:** PO (yanni peng)
**Date:** 2026-05-27

---

## Problem

After the "GKE Enables" slide (slide 4) the deck jumps directly to "Google Cloud's Application
Modernization Vision" with no parallel treatment of Cloud Run. Customers evaluating Cloud Run vs
GKE see GKE's capabilities articulated in detail but get nothing equivalent for Cloud Run. This
gap weakens the narrative for Cloud Run-centric modernization journeys and leaves the "Why Cloud
Run?" question unanswered before the vision slide. A dedicated "Cloud Run Enables" slide — placed
symmetrically after GKE Enables — closes this gap by presenting Cloud Run's eight core
capabilities and the three headline business outcomes customers unlock by migrating to it.

---

## Requirements

### Placement

1. The new slide MUST be inserted as the new **slide 5**, immediately after the current slide 4
   ("GKE Enables") and before the current slide 5 ("Google Cloud's Application Modernization
   Vision").
2. After insertion the total slide count becomes **7**. The former slide 5 ("Google Cloud Vision")
   becomes slide 6; the former slide 6 ("Migration Journey") becomes slide 7.
3. The HTML `id` of the new slide MUST be `slide-5`. The existing slides that shift must be
   renumbered in their `id` attributes (`slide-6` and `slide-7`).
4. The JavaScript navigation, progress dots `<div id="dots">`, and any `aria-label` references
   MUST be updated to reflect 7 total slides.

### Header

5. The slide MUST include the standard `.slide-header` with the Google Cloud wordmark SVG
   (identical markup to all existing slides) and a `.speaker-badge` reading
   **"Customer Engineer / Technical Specialist"**.

### Section Heading

6. Below the slide header the slide MUST render a section heading:
   - Primary heading: **"Cloud Run Enables"** (use `.section-title` or equivalent).
   - Optional sub-label badge using `.label-chip` or similar, e.g. **"Fully Managed Serverless
     Container Platform"**, consistent with how other slides use subtitle chips.

### Top Section — 8 Capability Tiles

7. The slide MUST render exactly **8 capability tiles** arranged in a **2-row × 4-column grid**
   (or equivalent compact layout that fits without scrolling at 1920×1080).
8. Tile styling MUST reuse existing CSS classes and design tokens. Use `.card`, `.card-title`,
   `.accent-card`, `.pillar-card`, or inline `style=""` overrides — no new CSS classes.
9. Each tile MUST display a bold tile title. Short descriptive sub-text or an icon accent is
   optional but MUST use only existing design tokens (colours: `--blue`, `--green`, `--yellow`,
   `--red`, or `--text-dim`).
10. Accent colours MUST cycle across the 8 tiles using the four brand colours in order
    (`--blue`, `--green`, `--yellow`, `--red`, then repeat) so that no two adjacent tiles in the
    same column share the same accent.
11. The 8 tiles and their titles are (in row-major order, left-to-right, top-to-bottom):

    **Row 1**
    - Tile 1: **FinOps** (accent: `--blue`)
    - Tile 2: **Managed Service** (accent: `--green`)
    - Tile 3: **Auto Scaling** (accent: `--yellow`)
    - Tile 4: **Dev UX** (accent: `--red`)

    **Row 2**
    - Tile 5: **Easy Deploy** (accent: `--blue`)
    - Tile 6: **Scale to Zero** (accent: `--green`)
    - Tile 7: **Source to Image CI** (accent: `--yellow`)
    - Tile 8: **Low Ops** (accent: `--red`)

### Bottom Section — "What Migrating to Cloud Run Enables"

12. Below the capability tiles the slide MUST include a bottom section with the heading
    **"What Migrating to Cloud Run Enables"** rendered using `.col-title` or an equivalent
    small-caps / label style.
13. The section MUST contain exactly **3 value-statement cards** displayed side-by-side in one
    horizontal row using the existing `.card` or `.accent-card` pattern with a left-border
    accent colour.
14. The 3 value statements are (use exact wording for card titles and body text):

    **Card 1 — Accelerated Velocity and Productivity** (left-border accent: `--blue`)
    Body: "Cloud Run facilitates the fastest time to market by allowing developers to focus
    entirely on business logic while outsourcing operations to Google. It enables 95% faster
    deployment compared to legacy platforms."

    **Card 2 — Cost Efficiency** (left-border accent: `--green`)
    Body: "It is 15% to 50% cheaper than provisioned cloud platforms and up to 75% cheaper than
    on-premises environments. Customers only pay for the resources they need because the platform
    features fast scaling, no pre-provisioning, and the ability to scale to zero."

    **Card 3 — Higher Reliability and Built-in Security** (left-border accent: `--yellow`)
    Body: "Customers experience 98% fewer interruptions to service because Cloud Run is redundant
    by default, effectively making Google your Site Reliability Engineer (SRE). It also includes
    built-in sandboxing, ensuring each container instance runs in an isolated environment."

### Visual Design Constraints

15. The slide MUST NOT introduce any new CSS class names or CSS variables beyond those already
    defined in `index.html`. Reuse `.card`, `.card-title`, `.card-body`, `.accent-card`,
    `.label-chip`, `.col-title`, `.section-title`, `.section-subtitle`, `.pillar-card`,
    `.pillar-icon`, `.pillar-bullets`, or any other existing class as needed.
16. Inline `style=""` attributes are permitted for one-off adjustments (colour overrides, gap
    tweaks, padding, font-size reductions) consistent with the coding pattern already in use
    across slides 2–5.
17. The slide MUST NOT overflow the viewport vertically. All content must be visible without
    scrolling at a standard 1920×1080 viewport. Use `font-size`, `padding`, and `gap` reductions
    (via inline styles) if needed — consistent with how slides 3 and 4 currently handle dense
    content.
18. Background colour for the slide body MUST remain `var(--bg)` (`#0D1B2A`). No new background
    colours are permitted.

### Navigation & Dots

19. The `<div id="dots">` MUST contain **7** `.dot` child `<div>`s (was 6 after F-0002; now 7).
20. The JavaScript `total` is derived dynamically from `document.querySelectorAll('.slide')`,
    so no JS logic change is required — just ensure the new `<div class="slide">` is present in
    the DOM. SWE-1 MUST verify this by inspection.
21. `btn-prev` and `btn-next` behaviour is unchanged; the existing JS handles any count.

### Agenda Update (Slide 1)

22. The agenda list on slide 1 currently reads (after F-0002):
    - Welcome & Introductions
    - Discovery Session
    - Modernization Imperative & GKE / Cloud Run
    - GKE Enables
    - Google Cloud Vision
    - Migration Journey — 4 Phases

    It MUST be updated to include the new agenda item at position 5:
    - Welcome & Introductions
    - Discovery Session
    - Modernization Imperative & GKE / Cloud Run
    - GKE Enables
    - **Cloud Run Enables**
    - Google Cloud Vision
    - Migration Journey — 4 Phases

### Slide ID Renumbering

23. The existing slide previously identified as `slide-5` ("Google Cloud Vision") MUST be
    updated to `id="slide-6"`.
24. The existing slide previously identified as `slide-6` ("Migration Journey") MUST be
    updated to `id="slide-7"`.
25. Any `aria-label`, `data-*`, or JS references that hardcode slide-5 or slide-6 MUST be
    updated to slide-6 and slide-7 respectively.

---

## Acceptance Criteria

- [ ] A new `<div class="slide" id="slide-5">` exists in the DOM between the GKE Enables slide
      (`slide-4`) and what was previously slide 5 (now `slide-6`, Google Cloud Vision).
- [ ] Slide IDs are sequential: `slide-1` through `slide-7`. No gaps or duplicates.
- [ ] The slide header shows "Customer Engineer / Technical Specialist" in the speaker badge.
- [ ] A section heading "Cloud Run Enables" is visible on the slide.
- [ ] The top section renders exactly 8 capability tiles in a 2-row × 4-column (or equivalent)
      grid: FinOps, Managed Service, Auto Scaling, Dev UX (row 1) and Easy Deploy, Scale to
      Zero, Source to Image CI, Low Ops (row 2).
- [ ] Each tile displays its bold title and an accent colour matching Requirement 10 (blue, green,
      yellow, red repeating).
- [ ] No new CSS classes or CSS variables were introduced. Only existing design tokens used.
- [ ] The bottom section heading "What Migrating to Cloud Run Enables" is visible.
- [ ] Three value-statement cards are rendered side-by-side with left-border accent colours
      (blue, green, yellow) and the exact body copy specified in Requirement 14.
- [ ] The slide does not overflow at 1920×1080. All content is visible without scrolling.
- [ ] The `<div id="dots">` contains exactly 7 `.dot` child divs.
- [ ] The agenda list on slide 1 includes "Cloud Run Enables" as the 5th item (between "GKE
      Enables" and "Google Cloud Vision").
- [ ] Former `slide-5` is now `slide-6` (Google Cloud Vision); former `slide-6` is now `slide-7`
      (Migration Journey). No stale IDs remain.
- [ ] Keyboard navigation (← →) and click navigation move through all 7 slides correctly.
- [ ] Visual design is consistent with the existing slide aesthetic (dark background, Google
      brand colours, Google Sans font).

---

## Out of Scope

- Changes to slide content on slides 2, 3, or 4 other than the agenda update on slide 1 and
  the renumbering of `id` attributes on slides 5–6 (now 6–7).
- Adding animations or transitions beyond the existing slide transition system.
- Any backend, build tooling, or test-runner changes — this is a single-file SPA.
- Mobile/responsive breakpoints — the deck targets desktop/presentation displays only.
- Adding descriptive bullet points inside each of the 8 capability tiles (titles only are
  sufficient; sub-text is optional and at SWE-1's discretion within the no-overflow constraint).

---

## Dependencies

- F-0001 (done) — EBC Slide Deck SPA merged to master as v0.1.0.
- F-0002 (done) — GKE Enables Slide merged to master as v0.2.0. Slide numbering and dots
  updated to 6 slides; this spec extends that to 7.

---

## Open Questions

- None — all tile titles, card wording, and placement provided by PO verbatim.