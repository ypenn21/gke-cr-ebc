# F-0001: EBC Slide Deck Single-Page Application

**Type:** Feature
**Priority:** P0 (critical)
**Status:** Approved
**Requested by:** PO yanni peng
**Date:** 2026-05-27

## Problem

The project has no presentation layer. An executive-quality slide deck SPA is needed to showcase the GKE/Cloud Run LAMP modernization journey at an EBC (Executive Briefing Center) briefing. Without this, the team has no deliverable to present to C-suite and decision-maker audiences.

## Requirements

1. **Single-file delivery:** Produce one `index.html` file in the project root with all CSS and JavaScript embedded inline. No external build tools or bundlers. Google Fonts may be loaded via CDN `<link>` tag.

2. **Google Cloud branding:** Use the official Google Cloud palette throughout:
   - Primary blue: `#4285F4`
   - Accent red: `#EA4335`
   - Accent yellow: `#FBBC05`
   - Accent green: `#34A853`

3. **Full-screen slide layout:** One slide fills the viewport at a time. No scrolling within slides — all content must be visible at once on a standard 16:9 projector/display.

4. **Navigation:**
   - On-screen left (`◀`) and right (`▶`) arrow buttons visible at all times
   - Keyboard left/right arrow keys must also navigate slides
   - Navigation wraps or stops gracefully at first/last slide

5. **Slide progress indicator:** Display current slide position at all times (e.g., "3 / 5" counter or 5 progress dots). Must update correctly on every navigation event.

6. **Exactly 5 slides** in this order, with the following content drawn from `EBC-AGENDA.md`:

   **Slide 1 — Welcome & Introductions**
   - Speaker: EBC Host / Account Executive
   - Content: Session goals (strategic working session, not a sales pitch); round-table introductions prompt; tone-setting from the agenda's Welcome section

   **Slide 2 — Your Business: Listening Session**
   - Speaker: Account Executive + Customer Engineer
   - Content: Discovery-first framing; LAMP friction pain points (scaling, release cycles, cost, developer talent); success framing question ("What does success look like in 12–18 months?"); key framing quote from agenda

   **Slide 3 — The Modernization Imperative: GKE & Cloud Run as the Answer**
   - Speaker: Customer Engineer / Technical Specialist
   - Content: Three structural LAMP problems (cost inefficiency, fragility at scale, operational drag); GKE vs Cloud Run comparison table reproduced verbatim from the agenda; Cloud Run and GKE summary paragraphs; executive takeaway callout

   **Slide 4 — Google Cloud's Application Modernization Vision**
   - Speaker: Industry Solutions Consultant
   - Content: Google's philosophy (meet you where you are); the three destinations (managed containers, serverless, CI/CD); Google's own infrastructure story (Gmail/Search/YouTube on Kubernetes); executive takeaway callout

   **Slide 5 — The Migration Journey: From LAMP to Cloud-Native**
   - Speaker: Customer Engineer
   - Content: All four migration phases presented visually as distinct cards or steps:
     - Phase 1 — Assess: Know What You Have
     - Phase 2 — Plan: Design for the Future (storage, sessions, database pillars)
     - Phase 3 — Deploy: Zero-Downtime Migration (Strangler Fig pattern; DMS; Cloud Build)
     - Phase 4 — Optimize: Day-Two Value (CDN, autoscaling, observability)
   - Executive takeaway callout

7. **Per-slide structure:** Every slide must display:
   - Slide title (large, prominent)
   - Speaker role badge (styled label, e.g., "Customer Engineer")
   - Slide body content (bullets, tables, callouts as appropriate)

8. **Executive-quality design:** Clean, minimal, and impactful. Suitable for C-suite audiences and projector display. Generous whitespace, legible font sizes (body text ≥ 16px), strong heading hierarchy.

9. **Smooth CSS transition:** Slides transition with a CSS animation (fade, slide, or equivalent) when navigating. No jarring jumps.

## Acceptance Criteria

- [ ] `index.html` opens in a modern browser with no console errors
- [ ] All 5 slides render with correct, complete content sourced from `EBC-AGENDA.md`
- [ ] Left/right on-screen arrow buttons navigate to previous/next slide
- [ ] Keyboard left/right arrow keys navigate to previous/next slide
- [ ] Slide progress indicator (counter or dots) updates correctly on every navigation
- [ ] GKE vs Cloud Run comparison table is visible and legible on Slide 3
- [ ] All 4 migration phases (Assess, Plan, Deploy, Optimize) are visually distinct on Slide 5
- [ ] Google Cloud brand colors (`#4285F4`, `#EA4335`, `#FBBC05`, `#34A853`) are used throughout
- [ ] Speaker role badge is visible on every slide
- [ ] CSS transition animation plays between slides
- [ ] No external build tools required — file opens by double-clicking in a browser

## Out of Scope

- Backend, server, or API of any kind
- Database or authentication
- Mobile responsiveness (desktop/projector display only)
- Slides beyond the 5 defined above (sessions 6–12 from the agenda are excluded from this deliverable)
- Slide editing or presenter mode controls

## Dependencies

- `EBC-AGENDA.md` (project root) — source of all slide content; must exist and be accurate before implementation begins

## Open Questions

- None — requirements are fully defined and approved by PO.