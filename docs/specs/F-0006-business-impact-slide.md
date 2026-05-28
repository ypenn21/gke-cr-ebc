# F-0006: Business Impact Slide (Slide 8)

**Type:** Feature
**Priority:** P0 (critical)
**Status:** In Progress
**Requested by:** PO (yanni peng)
**Date:** 2026-05-28

## Problem

The deck currently ends at slide 7 (The Migration Journey) with no closing slide that synthesises the business case for executives. An EBC audience needs a landing slide that converts all the technical proof points — especially the full lifecycle metrics from slide 6 — into concrete business outcomes. Without this, the deck ends on a "how" note rather than a "why it matters" note, weakening the call to action.

## Requirements

1. The system must add a new `slide-8.html` fragment file inside `slides/` that renders a slide titled **"Business Impact"**.
2. The slide must contain **Section 1 — Hero Metric Row**: four stat callout cards displayed horizontally with a large bold number and a short descriptor:
   - **95%** faster deployment vs legacy platforms
   - **15–50%** cheaper than provisioned cloud infrastructure
   - **75%** cheaper than on-premises environments
   - **98%** fewer service interruptions
3. The slide must contain **Section 2 — Business Dimension Cards**: four cards arranged in a 2×2 grid or 4-column row, each with a title, color accent, and "From → To" transformation narrative:
   - **Speed to Market** (blue accent): From monthly release cycles and deployment Fridays → to multiple deploys per day, lead time measured in hours, rapid feedback loops that catch issues before customers do
   - **Cost Optimization** (green accent): From always-on VMs paying for peak 24/7 → to pay-per-use pricing, scale-to-zero during off-hours, Spot nodes for batch, Cost Allocation per team
   - **Operational Excellence** (yellow accent): From manual patching, toil-heavy ops, human error in deployments → to automated upgrades, auto-repair, Binary Authorization gates, MTTR in seconds not hours
   - **Platform Scalability** (red accent): From fixed VM estate that breaks under flash traffic → to instant scale-out handling Black Friday spikes, limited blast radius via canary deploys, global CDN edge caching
4. The slide must contain **Section 3 — Executive Takeaway**: a green `.takeaway` box (same CSS class used in slides 3 and 7) with:
   - Label: "The Bottom Line"
   - Text: "Migrating from LAMP on GCE to GKE or Cloud Run is not an infrastructure project — it's a business transformation. Your team ships faster, your platform costs less, your operations run themselves, and your customers experience fewer outages. The question is not whether to move — it's how to sequence it."
5. The slide must use the same `.slide`, `.slide-header`, `.slide-body`, `.section-title`, and speaker-badge markup conventions used by all other slide fragment files.
6. The four hero metric cards must visually emphasise the number (large, bold, primary colour) with the descriptor below in smaller supporting text.
7. The four business dimension cards must each include a "From" block and a "To" block with a visual arrow or separator between them, clearly distinguishing the legacy state from the target state.
8. The slide must be fully responsive and visually consistent with the existing design system (Google sans fonts, Google Blue primary, existing card/chip CSS patterns).
9. `index.html` must be updated to load `slides/slide-8.html` as the eighth slide fragment, maintaining the existing dynamic fragment-loading mechanism.
10. `slides/slide-1.html` must reflect "Business Impact" as agenda item 8 in the `agenda-list` (this is handled separately by the PM; SWE-1 must verify the agenda item is present before marking done).

## Acceptance Criteria

- [ ] `slides/slide-8.html` exists and is well-formed HTML.
- [ ] The slide renders slide number 8 with the section title "Business Impact" and the correct speaker-badge text.
- [ ] Section 1 displays all four hero metric cards with the exact values: 95%, 15–50%, 75%, 98% and their descriptors.
- [ ] Section 2 displays all four business dimension cards (Speed to Market, Cost Optimization, Operational Excellence, Platform Scalability), each with correct colour accent, From state, and To state.
- [ ] Each business dimension card clearly differentiates the "From" legacy state from the "To" target state (e.g. via arrow, divider, or label).
- [ ] Section 3 displays a `.takeaway` box with label "The Bottom Line" and the exact prescribed takeaway text.
- [ ] The slide is visually consistent with the existing design system — no new fonts, colours outside the palette, or layout patterns inconsistent with other slides.
- [ ] `index.html` loads `slides/slide-8.html` as the eighth fragment without breaking existing slide navigation.
- [ ] Navigating to slide 8 in the browser shows the Business Impact slide with all three sections fully rendered.
- [ ] All existing slides (1–7) continue to render correctly after the change — no regressions.

## Out of Scope

- Changes to slide content on slides 1–7 beyond the agenda list update on slide 1.
- Adding new CSS variables or design tokens not already present in the project.
- Any back-end or data-layer changes.
- Animations or transitions beyond what the existing design system already provides.

## Dependencies

- F-0004 (slide extraction refactor — establishes the fragment-loading pattern that slide 8 must follow)
- F-0005 (slide 6 CI/CD lifecycle metrics — the business outcomes in the hero row are derived from these proof points)

## Open Questions

- None — all content and layout requirements are fully specified by the PO.