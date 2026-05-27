# F-0002: GKE Enables Slide

**Type:** Feature
**Priority:** P0 (critical)
**Status:** In Progress
**Requested by:** PO (yanni peng)
**Date:** 2026-05-27

---

## Problem

The current slide deck transitions directly from "The Modernization Imperative" (slide 3, which
establishes *why* to move) to "Google Cloud's Application Modernization Vision" (slide 4, which
covers the platform at large). There is no slide that dives into the specific technical capabilities
GKE unlocks for the customer — autoscaling, FinOps, GitOps, and Day 2 operational simplicity —
nor one that explains the tangible business value of migrating to GKE (flexibility, complex workload
support, custom developer platforms). This gap weakens the narrative between the business case and
the vision layer.

---

## Requirements

### Placement

1. The new slide MUST be inserted as the new **slide 4**, between the current slide 3
   ("The Modernization Imperative") and the current slide 4 ("Google Cloud's Application
   Modernization Vision").
2. After insertion the total slide count is 6. The former slide 4 ("Google Cloud Vision") becomes
   slide 5; the former slide 5 ("Migration Journey") becomes slide 6.
3. The HTML `id` of the new slide MUST be `slide-4`. The existing slides that shift must be
   renumbered in their `id` attributes (`slide-5` and `slide-6`).
4. The JavaScript navigation, progress dots `<div id="dots">`, and `aria-label` references
   MUST be updated to reflect 6 total slides.

### Header

5. The slide MUST include the standard `.slide-header` with the Google Cloud wordmark SVG
   (identical markup to existing slides) and a `.speaker-badge` reading
   **"Customer Engineer / Technical Specialist"**.

### Top Section — 4 GKE Capability Tiles

6. Below the section heading, the slide MUST render 4 capability tiles in a **2×2 grid** (two
   columns, two rows) or a **4-column single row** — whichever fits the viewport without
   scrolling. Use the existing CSS variable `--card`, `--border`, `--blue`, etc.
7. Each tile MUST have:
   - A distinct accent colour icon or symbol area (use `--blue`, `--green`, `--yellow`,
     `--red` in rotation across the 4 tiles).
   - A bold tile title.
   - 2–4 concise bullet points explaining the capability.
8. The 4 tiles and their content are:

   **Tile 1 — 4-Way Autoscaling** (accent: `--blue`)
   - Horizontal Pod Autoscaler (HPA): scales pods on CPU, memory, or custom metrics
   - Vertical Pod Autoscaler (VPA): right-sizes pod resource requests automatically
   - Cluster Autoscaler: adds/removes nodes based on pending pod demand
   - Multidimensional Pod Autoscaler (MPA): combines HPA + VPA for complex workloads

   **Tile 2 — FinOps** (accent: `--green`)
   - Resource quotas and LimitRanges prevent runaway spend per namespace
   - Committed use discounts and Spot node pools reduce steady-state costs
   - Cost Attribution via GKE cost allocation — per-namespace, per-label chargeback
   - Workload right-sizing recommendations from GKE's built-in Autopilot intelligence

   **Tile 3 — GitOps** (accent: `--yellow`)
   - Config Sync and Fleet Management keep cluster state in sync with Git
   - Declarative manifests in source control — every change is auditable and reversible
   - Automated rollouts via Cloud Deploy with progressive delivery (canary, blue/green)
   - Policy enforcement via Policy Controller (OPA Gatekeeper) applied at admission time

   **Tile 4 — Streamlined Day 2 Ops** (accent: `--red`)
   - Automatic control-plane upgrades, node auto-repair, and security patching
   - Binary Authorization ensures only signed, approved images run in production
   - Cloud Monitoring + Managed Prometheus for out-of-the-box observability
   - GKE Gateway API for advanced traffic management without custom ingress controllers

### Middle Section — Autopilot vs Standard & Autopilot Node Pools

9. Below the 4 capability tiles, the slide MUST include a concise sub-section (one compact block
   or small comparison row) that covers:
   - **GKE Autopilot**: Google manages nodes, scaling, and security; customers pay per pod
     resource (not per node); ideal for most workloads.
   - **GKE Standard**: Customer manages node pools and cluster topology; full flexibility for
     custom networking, GPU/TPU workloads, or specialised hardware.
   - **Autopilot Node Pools on Standard**: Standard clusters can now include Autopilot-style
     node pools, giving customers a hybrid approach — managed efficiency for general workloads
     plus manually configured pools for specialist needs.
10. This sub-section MUST be visually distinguishable from the tiles above (e.g., a compact
    horizontal strip, a small table, or a styled row using existing `--card` / `--border`
    styles).

### Bottom Section — "What Migrating to GKE Enables"

11. The slide MUST include a bottom section with the heading
    **"What Migrating to GKE Enables"** rendered in a styled label or sub-heading
    (using `.col-title` or equivalent small-caps label style).
12. The section MUST contain exactly **3 value-statement cards** displayed horizontally
    (one row of 3) using the existing `.card` or `.accent-card` pattern with left-border
    accent colours.
13. The 3 value statements and their content are (use exact wording for card titles
    and body text):

    **Card 1 — Ultimate Flexibility and Control** (left-border accent: `--blue`)
    Body: "As the most automated and secure Kubernetes offering, GKE provides full control
    and fine-grained customization over networking, storage, and policies."

    **Card 2 — Support for Complex Workloads** (left-border accent: `--green`)
    Body: "Enables customers to run workloads that require fast disk storage, long-lived
    instances, or stateful configurations that are not a fit for Cloud Run."

    **Card 3 — Custom Developer Platforms** (left-border accent: `--yellow`)
    Body: "Provides foundational infrastructure for customers to build their own internal
    developer platforms and standardize on industry-standard Kubernetes tooling."

### Visual Design Constraints

14. The slide MUST NOT introduce any new CSS class names or CSS variables beyond those
    already defined in `index.html`. Reuse `.card`, `.card-title`, `.card-body`,
    `.accent-card`, `.label-chip`, `.col-title`, `.section-title`, `.section-subtitle`,
    `.pillar-card`, `.pillar-icon`, `.pillar-bullets`, or any other existing class as needed.
15. Inline `style=""` attributes are permitted for one-off adjustments (colour overrides,
    gap tweaks, padding) consistent with the coding pattern already in use across slides 2–5.
16. The slide MUST NOT overflow the viewport vertically. All content must be visible without
    scrolling at a standard 1920×1080 viewport. Use `font-size`, `padding`, and `gap`
    reductions (via inline styles) if needed to fit — consistent with how slides 3 and 4
    currently handle dense content.
17. Background colour for the slide body MUST remain `var(--bg)` (`#0D1B2A`). No new
    background colours.

### Navigation & Dots

18. The `<div id="dots">` MUST contain **6** `.dot` child `<div>`s (was 5).
19. The JavaScript `total` is derived dynamically from `document.querySelectorAll('.slide')`,
    so no JS logic change is required — just ensure the new slide `<div class="slide">` is
    present in the DOM. SWE-1 MUST verify this by inspection.
20. `btn-prev` and `btn-next` behaviour is unchanged; the existing JS handles any count.

### Agenda Update (Slide 1)

21. The agenda list on slide 1 currently reads:
    - Welcome & Introductions
    - Discovery Session
    - Modernization Imperative & GKE / Cloud Run
    - Google Cloud Vision
    - Migration Journey — 4 Phases

    It MUST be updated to include the new agenda item at position 4:
    - Welcome & Introductions
    - Discovery Session
    - Modernization Imperative & GKE / Cloud Run
    - **GKE Enables**
    - Google Cloud Vision
    - Migration Journey — 4 Phases

---

## Acceptance Criteria

- [ ] A new `<div class="slide" id="slide-4">` exists in the DOM between slide 3 and what was
      previously slide 4 (now `slide-5`).
- [ ] Slide IDs are sequential: `slide-1` through `slide-6`. No gaps or duplicates.
- [ ] The slide header shows "Customer Engineer / Technical Specialist" in the speaker badge.
- [ ] The top section renders 4 capability tiles: 4-Way Autoscaling, FinOps, GitOps,
      Streamlined Day 2 Ops — each with the correct accent colour and bullet content.
- [ ] Each tile contains the exact bullet points specified in Requirements 8.
- [ ] The Autopilot vs Standard sub-section is present and describes all three modes:
      Autopilot, Standard, and Autopilot Node Pools on Standard.
- [ ] The bottom section heading "What Migrating to GKE Enables" is visible.
- [ ] Three value-statement cards are rendered side-by-side with left-border accent colours
      (blue, green, yellow) and the exact body copy from Requirements 13.
- [ ] No new CSS classes or CSS variables were introduced. Only existing design tokens used.
- [ ] The slide does not overflow at 1920×1080. All content is visible without scrolling.
- [ ] The `<div id="dots">` contains exactly 6 `.dot` child divs.
- [ ] The agenda list on slide 1 includes "GKE Enables" as the 4th item (between
      "Modernization Imperative" and "Google Cloud Vision").
- [ ] Keyboard navigation (← →) and click navigation move through all 6 slides correctly.
- [ ] Visual design is consistent with the existing slide aesthetic (dark background,
      Google brand colours, Google Sans font).

---

## Out of Scope

- Changes to slide content on slides 2, 3, 5 (new), or 6 (new) other than the agenda update
  on slide 1 and the renumbering of `id` attributes.
- Adding animations or transitions beyond the existing slide transition system.
- Any backend, build tooling, or test-runner changes — this is a single-file SPA.
- Mobile/responsive breakpoints — the deck targets desktop/presentation displays only.

---

## Dependencies

- F-0001 (done) — EBC Slide Deck SPA must be merged to master before this branch is cut.

---

## Open Questions

- None — all content and wording provided by PO verbatim.