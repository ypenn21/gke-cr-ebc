# gke-cr-ebc — Project Instructions

## Project Overview

this is a webpage show casing the oogle Cloud Executive Briefing Center (EBC)

## Key References

- [README.md](README.md) — Project overview, tech stack
- [docs/BACKLOG.md](docs/BACKLOG.md) — Feature backlog with priorities, status, dependencies, and feedback (owned by PM)
- [docs/PROGRESS.md](docs/PROGRESS.md) — Session-by-session development log (update every session)
- [docs/RELEASENOTES.md](docs/RELEASENOTES.md) — Version history (Keep a Changelog format, owned by PM)
- [docs/PIPELINE.md](docs/PIPELINE.md) — MermaidJS agent workflow diagram
- [docs/specs/](docs/specs/) — Product requirement specs (one per feature, owned by PM)
- [docs/specs/TEMPLATE.md](docs/specs/TEMPLATE.md) — Spec template for PM

## Product Owner / CEO

- **Name:** yanni peng
- **Role:** Product Owner (PO) and CEO — the human in the loop
- **GitHub:** ypenn21
- **Email:** yannipeng21@gmail.com
- **Git config:** Always use `git -c user.name="yanni peng" -c user.email="yannipeng21@gmail.com"` for commits so authorship is consistent in history.

## Version Control

- **Commit frequently** — after each meaningful change (new feature, bug fix, refactor, config change). Small, focused commits over large monolithic ones.
- **Write verbose commit messages** — first line is a concise summary (imperative mood, under 72 chars), followed by a blank line and a detailed body explaining *what* changed and *why*. Include context that won't be obvious from the diff.
- **Never commit secrets** — `.gitignore` protects `*-sa-key.json` and `.env`. Verify with `git status` before committing.
- **Review before pushing** — use `git diff --staged` to review staged changes before committing.
- **Keep `main` stable** — use feature branches for non-trivial work, merge back to `main` when ready.
- **Tag milestones** — use annotated git tags for significant releases or milestones.

## Progress Journaling

- **Always update docs/PROGRESS.md** at the end of every session with:
  - Date and session number
  - What was accomplished (with specifics — files changed, features added, bugs fixed)
  - Key decisions made and rationale
  - Next steps / open items
- Commit the docs/PROGRESS.md update as part of the session's final commit

## Team Workflow

This project uses a multi-agent team structure.

### Feedback → Backlog → Execution Pipeline

**This is the mandatory workflow for all user feedback and requests:**

1. **PO (yanni peng)** provides feedback, feature requests, or bug reports to the **PM**
2. **PM** translates PO feedback into a product spec in `docs/specs/F-NNNN-slug.md` with detailed requirements and acceptance criteria
3. **PM** creates/updates work items in docs/BACKLOG.md with priority, scope, and dependencies
4. **PM** assigns work to **SWE-1**
5. **SWE-1** implements on a feature branch, following the existing codebase conventions
6. **SWE-1** hands off completed work to **SWE-Test** for verification
7. **SWE-1** updates docs/BACKLOG.md marking items as completed, tested, and verified
8. **PM** updates docs/PROGRESS.md and docs/RELEASENOTES.md
9. **PM** reports back to the **PO** with a summary of completed work
10. **Tag the release** with `git tag -a vX.Y.Z` after PO approval and push tags

**Every piece of feedback goes through this pipeline — no skipping steps.**

**Always use the pipeline for all bug fixes and new features — never ask the PO for confirmation on whether to use the pipeline. Just do it.**

### Agent-Only Execution Rule (Non-Negotiable)

**All project work must be performed by a designated Agent role.** No work is done directly — it is always delegated to the appropriate agent (PM, SWE-1, SWE-Test). If a task requires a role or specialization that does not exist in the current team roster, **stop and check with the PO (yanni peng)** before proceeding. The PO will decide whether to create a new agent role or reassign the work.

### Interactive Agent Teams via Tmux (Non-Negotiable)

**All agent work MUST use interactive Agent Teams (TeamCreate), NOT subprocess agents.**

Agents must be spawned as interactive teammates in separate tmux panes so the PO can observe and interact with each agent in real time. The correct workflow is:

1. **Create a team** with `TeamCreate` (e.g., `team_name: "feature-xyz"`)
2. **Create tasks** with `TaskCreate` — one per work item, with clear descriptions
3. **Spawn teammates** using the `Agent` tool with `team_name` parameter — this launches each agent in its own tmux pane
4. **Assign tasks** via `TaskUpdate` with `owner` set to the agent name
5. **Coordinate** via `SendMessage` — agents report progress and results back to the team lead
6. **Shutdown gracefully** — send `shutdown_request` to each agent when work is complete
7. **Clean up** with `TeamDelete` after all agents have shut down

**Never use background subprocess agents (Agent tool without `team_name`).** The PO must always be able to see agent activity in tmux panes. Parallel work should be visible, not hidden.

**All agents MUST use the Sonnet 4.6 model (`claude-sonnet-4-6`).** When spawning teammates with the `Agent` tool, always set `model: "claude-sonnet-4-6"` unless the PO explicitly specifies a different model. No agent should default to a lesser model.


### Mandatory Development Pipeline (Non-Negotiable)

**All PO feedback and feature requests MUST follow this pipeline — no shortcuts, no exceptions:**

1. **PO → PM**: PO provides feedback, feature requests, or bug reports to the PM Agent
2. **PM → Spec**: PM creates a product spec in `docs/specs/F-NNNN-slug.md` (copy from `docs/specs/TEMPLATE.md`) with detailed requirements and acceptance criteria
3. **PM → Backlog**: PM creates/updates work items in docs/BACKLOG.md with priority, scope, and dependencies (linking to the spec)
4. **PM → SWE-1**: PM assigns the work item to SWE-1. SWE-1 implements on a feature branch
5. **SWE-1 → Testing**: After implementation, SWE-1 hands off to SWE-Test (runs all automated tests — existing tests must pass, new tests added for new functionality)
6. **SWE-1 → Backlog Update**: Once coding, functionality, and testing are complete, SWE-1 updates docs/BACKLOG.md marking items as completed, tested, and verified
7. **SWE-1 → PM**: SWE-1 informs PM that the work item is done
8. **PM → Progress + Release Notes**: PM updates docs/PROGRESS.md with session details and docs/RELEASENOTES.md with the new version entry
9. **PM → PO**: PM creates a summary of all completed work and reports back to the PO
10. **Tag**: After PO approval, tag the release with `git tag -a vX.Y.Z -m "description"` and push tags
11. **Mandatory updates**: docs/BACKLOG.md, docs/PROGRESS.md, and docs/RELEASENOTES.md MUST be updated every milestone. Git tags MUST be created for every release
12. **No direct code changes**: The orchestrator (main Claude context) MUST NEVER write or edit application code directly. Only SWE agents write code. Only PM agents update backlog/progress/release docs

**Violating this pipeline is a process failure.** If time pressure tempts a shortcut, stop and confirm with the PO first.

### Roles
- **PO / CEO** (yanni peng) — Product Owner, the human in the loop. Provides feedback, feature requests, and bug reports. Approves direction, tests the app
- **PM** — Receives PO feedback. Translates to specs. Manages backlog, progress log, and release notes. Coordinates with SWE-1 and SWE-Test
- **SWE-1** — Full Stack Engineer
- **SWE-Test** — Test coverage and quality assurance. Runs all automated tests after SWE implementation. Ensures existing tests pass and new tests are added for new functionality

### Backlog Tracking (Non-Negotiable)

**Every piece of work gets a backlog entry in `docs/BACKLOG.md` — no exceptions.**
Regardless of team size, all features, bug fixes, and enhancements must be tracked
in the backlog before implementation begins and updated when completed.

### Other Conventions
- **Branching:** Feature branches (`feature/<name>`) off `main`
- **Co-Author:** All commits include `Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>`
