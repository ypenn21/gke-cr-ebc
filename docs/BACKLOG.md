# Project Backlog — gke-cr-ebc

**Maintained by:** TPM
**Last updated:** 2026-05-28 (F-0006 opened)

---

## How to Read This Backlog

- **ID:** Unique feature identifier (`F-0001`, `F-0002`, etc.) — sequential across all milestones, never reused
- **Priority:** P0 (critical path), P1 (important), P2 (nice to have)
- **Status:** `backlog` | `in-progress` | `in-review` | `done` | `blocked`
- **Owner:** Assigned team member
- **Branch:** Git feature branch
- **Dependencies:** Other feature IDs that must complete first
- **Feedback:** Review notes, blockers, decisions — updated as work progresses

---

## Current Milestone

| ID | Feature | Spec | Priority | Status | Owner | Branch | Dependencies | Feedback |
|----|---------|------|----------|--------|-------|--------|--------------|----------|
| F-0001 | EBC Slide Deck SPA | [docs/specs/F-0001-ebc-slide-deck-spa.md](specs/F-0001-ebc-slide-deck-spa.md) | P0 | done | SWE-1 | feature/ebc-slide-deck | — | All 9 acceptance criteria passed. Slide 4 title defect patched before merge. Merged to master as v0.1.0. |
| F-0002 | GKE Enables Slide | [docs/specs/F-0002-gke-enables-slide.md](specs/F-0002-gke-enables-slide.md) | P0 | done | SWE-1 | feature/gke-enables-slide | F-0001 | All 12 acceptance criteria passed on first review. Merged to master as v0.2.0. |
| F-0003 | Cloud Run Enables Slide | [docs/specs/F-0003-cloud-run-enables-slide.md](specs/F-0003-cloud-run-enables-slide.md) | P0 | done | SWE-1 | master | F-0001, F-0002 | All acceptance criteria passed. Merged directly to master as v0.3.0. |
| F-0004 | Slide Extraction Refactor | [docs/specs/F-0004-slide-extraction-refactor.md](specs/F-0004-slide-extraction-refactor.md) | P1 | done | SWE-1 | master | F-0001, F-0002, F-0003 | Completed. index.html reduced from ~1,200 to 658 lines. 7 fragment files created in slides/. Committed to master as v0.4.0. |
| F-0005 | Slide 6 — Full CI/CD Lifecycle Expansion | [docs/specs/F-0005-slide6-cicd-lifecycle.md](specs/F-0005-slide6-cicd-lifecycle.md) | P0 | done | SWE-1 | master | F-0004 | CI/CD pillar bullets replaced with shift-left/env-parity framing. Full Lifecycle Outcomes strip added (5 cards). Committed to master as v0.5.0. |
| F-0006 | Slide 8 — Business Impact (Closing Slide) | [docs/specs/F-0006-business-impact-slide.md](specs/F-0006-business-impact-slide.md) | P0 | in-progress | SWE-1 | master | F-0004, F-0005 | New closing slide with hero metric row (4 stat cards), business dimension cards (4×From→To), and executive takeaway box. Assigned to SWE-1. |

---

## Future Items

| ID | Feature | Spec | Priority | Status | Owner | Branch | Dependencies | Feedback |
|----|---------|------|----------|--------|-------|--------|--------------|----------|
| | | | | | | | | |

---

## Team Roster

| Role | Agent | Specialty |
|------|-------|-----------|
| PM | PM | Product requirements & PO communication |
| TPM | TPM | Backlog, coordination & progress tracking |
| SWE-1 | SWE-1 | Full Stack Engineer |
| SWE-Test | SWE-Test | Automated testing & coverage |
