# F-0005: Slide 6 — Full CI/CD Lifecycle Expansion

**Type:** Enhancement
**Priority:** P0 (critical)
**Status:** In Progress
**Requested by:** PO
**Date:** 2026-05-28

## Problem

`slides/slide-6.html` covers three pillars (Managed Containers, Serverless, CI/CD Automation) but the CI/CD pillar is thin and omits key lifecycle outcomes that EBC audiences expect to hear: shift-left reliability, automated testing, environment parity, patch automation, MTTR, lead time for changes, blast radius control, and rapid feedback loops. Without these, the slide undersells Google Cloud's full DevOps story.

## Requirements

1. **Preserve the 3 existing pillar cards** — Managed Containers, Serverless, and CI/CD Automation — with no changes to the first two pillar cards' content or markup.

2. **Expand the CI/CD Automation pillar bullets** — replace or augment the existing 4 content bullets (keep the `best-for` line) to include the following themes, each as a concise `<li>` entry:
   - Shift-left reliability: automated unit, integration, and smoke tests gate every build in Cloud Build before any artifact is promoted
   - Automated testing: Cloud Build steps run test suites; failing tests block promotion to Artifact Registry
   - Environment parity: identical container images are promoted through dev → staging → production via Cloud Deploy, eliminating "works on my machine" defects
   - Patch automation: Artifact Registry + GKE release channels surface and apply OS/runtime patches automatically, removing manual CVE triage cycles

3. **Add a "Full Lifecycle Outcomes" section** between the closing `</div>` of the pillars row and the opening `<div class="ecosystem-row">`:
   - Section heading: a `<div>` styled like `section-subtitle` or plain inline style — text "Full Lifecycle Outcomes", font-weight 600, color `#5f6368`, font-size 12px, margin-bottom 8px
   - A 5-column flex row (no new CSS class — use `style="display:flex; gap:10px; margin-bottom:12px;"`) containing 5 compact `.card` tiles
   - Each tile uses the existing `.card` class with `style="padding:8px 10px; flex:1; min-width:0;"` — no new classes
   - Tile content: a `<strong>` title line followed by a `<p style="margin:4px 0 0; font-size:11px; line-height:1.4; color:#5f6368;">` body sentence (no additional markup)

4. **Five tile definitions** (title / body):

   | Tile | Title | Body |
   |------|-------|------|
   | 1 | Rapid Feedback Loops | Cloud Build triggers on every commit; developers see pass/fail results in under 5 minutes, catching defects before they compound. |
   | 2 | Frequent Releases & Lead Time | Cloud Deploy pipelines advance approved images through environments automatically, compressing lead time from days to minutes. |
   | 3 | MTTR & Recovery | Cloud Run and GKE support instant rollbacks to the last known-good revision, minimizing mean time to recovery when a bad deploy ships. |
   | 4 | Minimized Human Error | Binary Authorization and Cloud Deploy approval gates enforce policy automatically — no ad-hoc SSH or manual kubectl apply in production. |
   | 5 | Limited Blast Radius | Canary and blue/green traffic splits in Cloud Deploy route a small percentage of traffic to new versions, containing the impact of any regression. |

5. **Viewport constraint** — the fully expanded slide must not overflow a 1920×1080 viewport. Achieve this by keeping all padding tight: pillar cards at `padding:16px 18px`, outcome tiles at `padding:8px 10px`, section heading margin ≤ 8px bottom, outcome row gap ≤ 10px.

6. **No new CSS classes or custom properties** — all layout and spacing is done via inline `style` attributes reusing existing classes (`.card`, `.pillar-card`, `.pillar-bullets`, etc.).

7. **Delivery directly to `master`** — no feature branch, no SWE-Test step.

## Acceptance Criteria

- [ ] `slides/slide-6.html` retains all 3 pillar cards with no changes to Managed Containers or Serverless content.
- [ ] CI/CD Automation pillar bullets include entries covering: shift-left reliability, automated testing, environment parity, and patch automation. The `best-for` line is preserved.
- [ ] A "Full Lifecycle Outcomes" heading appears between the pillars row and the ecosystem row.
- [ ] Exactly 5 `.card` tiles appear in a single flex row below the heading, each with a bold title and a short body sentence.
- [ ] Tile topics covered: Rapid Feedback Loops, Frequent Releases & Lead Time, MTTR & Recovery, Minimized Human Error, Limited Blast Radius.
- [ ] Each body sentence references at least one specific Google Cloud product (Cloud Build, Cloud Deploy, Cloud Run, GKE, Binary Authorization, Artifact Registry).
- [ ] No new CSS classes or CSS custom properties introduced — all styling via inline `style` attributes.
- [ ] Slide renders without vertical scrollbar at 1920×1080 in Chrome.
- [ ] The `ecosystem-row` and `highlight-box` remain intact below the new section.
- [ ] Changes committed directly to `master` with no feature branch.

## Out of Scope

- Changes to slides 1–5 or slide 7.
- Adding new slides.
- Changes to `index.html`, shared CSS, or navigation JS.
- SWE-Test automated test step (direct-to-master, no test gate).
- Feature branching.

## Dependencies

- F-0004 (done — slide-6.html exists as a standalone fragment in `slides/`)

## Open Questions

- None. SWE-1 has full latitude on exact bullet wording as long as the 4 themes and 5 tiles are present and the viewport constraint is met.
