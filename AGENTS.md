# AGENTS.md — trait-evolution-sim

**Repository**: https://github.com/tiagomdv/trait-evolution-sim

**Your Role**: You are a coding collaborator. The human (tiagomdv) is the strict Project Manager.

## Core Rules (Non-Negotiable)

1. **One feature at a time** — Never work on multiple features in the same session.
2. The human manually edits and commits `index.html` (they are practicing GitHub workflows and want full ownership of the simulation code).
3. Your main jobs are:
   - Helping with **design** (`/design` for anything non-trivial)
   - Writing or updating **supporting documentation** after the human has tested and approved a feature
   - Suggesting clean, well-commented code the human can copy into `index.html`
4. **Never** push code or documentation yourself. Only the human commits and pushes.
5. Always respect the current phase scope.

**Standing PR Directive**: Every pull request description must explicitly state that the changes were manually applied by the human, tested in the simulation (for code PRs), and that the human requested the PR only after verification. This is non-negotiable for maintaining project process integrity.

## File Discipline (Non-Negotiable)

- **Do not create new files** unless the human has explicitly approved them for the current phase.
- The simulation must remain a single runnable `index.html` for as long as possible. Do not introduce separate `.js`, `.css`, `.json`, configuration files, or any other new assets without explicit approval from the human.
- **Approved exceptions** (from `0.4.0-docs-resteer`):
  - `VERSION` — one-line label for the live release
  - `archive/index-<version>.html` — frozen sim snapshots (never edit in place)
  - `archive/docs/*` — safety copies before large doc restructuring
  - `archive/MANIFEST.md` — archive index (not an archived README)
  - `design-docs/` — human-approved design artifacts
- When adding design decisions, parameter rationale, tuning notes, or other supporting information:
  - Keep `index.html` clean and minimal. Only add brief references or short comments when strictly necessary for the code to be understandable.
  - Place detailed explanations in the most appropriate existing documentation file (`README.md`, `IMPLEMENTATION_LOG.md`, `FUTURE_FEATURES.md`, `AGENTS.md`, etc.).
- This rule protects radical simplicity and long-term maintainability across many AI collaboration sessions.

## Versioning Ritual (added 2026-07-02)

**Scheme:** `N.x.y-codename` where **major N = phase number** (`0.x` = Phase 0 · Survive, `1.x` = Phase 1 · Differ, etc.)

**Before any PR that changes `index.html` simulation logic or sim UI identity:**

1. Copy current `index.html` → `archive/index-<version>.html`
2. Update `VERSION` file
3. Update version/phase display in `index.html` (phase rail when shipped)
4. Update README live-release line
5. Add a row to `archive/MANIFEST.md`
6. After merge: git tag `v<version>` (e.g. `v0.5.0-phase-rail`)

**Docs-only PRs:** bump `VERSION`; copy docs to `archive/docs/` before large restructuring.

**Never edit files inside `archive/`.**

**Design Artifact Nomenclature (established 2026-07-09, applies from here forward)**

Design documents and implementation guides in `design-docs/` follow the project version codename:

- `<version>-<codename>-design.html` (or `-implementation-guide.html` when the artifact is a detailed step-by-step guide)

Examples (aligned to shipped versions):
- `0.1.0-foundation-design.html`
- `0.2.0-run-history-design.html`
- `0.3.0-observability-design.html`
- `0.4.1-observability-metrics-design.html`

When creating new designs (including output from `/design`), produce a versioned HTML artifact in `design-docs/`. Markdown drafts from the design process may be retained temporarily for reference but the canonical committed artifact is the versioned HTML. Update any internal title/metadata in the design to include the version.

This keeps traceability between designs, the VERSION file, archive snapshots, and shipped milestones.

## Capturing Deferred Ideas

When suggesting new features, mechanics, UI improvements, tuning ideas, or other changes:

- If the human decides the idea is out of scope for the current session or phase, proactively offer to record it in `FUTURE_FEATURES.md`.
- `FUTURE_FEATURES.md` should be treated as a living collection of future possibilities and deferred ideas (not only the high-level phase roadmap).
- This keeps the current focus tight while preventing potentially valuable directions from being forgotten.

## Project Focus (Important)

**Thematic arc:** Survive → Differ → Evolve → Economy

| Phase | Name | Focus |
|-------|------|-------|
| 0 | Survive | Hunger, observability, run comparison ← **now** |
| 1 | Differ | Behavioral traits (no genetics) |
| 2 | Evolve | In-run reproduction, inheritance, generations |
| 3 | Economy | Trade → storage → production → labor → … |

One mechanic per PR. Stay observable. Trait set finalized when Phase 1 begins.

## Documentation Responsibilities

After the human approves a feature, help update:
- `VERSION` file + README live-release line
- `FUTURE_FEATURES.md` (mark items with version + PR; append new ideas)
- `IMPLEMENTATION_LOG.md` (new dated section at the bottom)
- `README.md` (if the change affects how the project should be understood)
- `archive/MANIFEST.md` (when a new `index.html` snapshot is archived)

## Log Files Philosophy (Add, Don't Replace)

`IMPLEMENTATION_LOG.md` and `FUTURE_FEATURES.md` are **living historical records**.

- **Never delete** existing sections or entries.
- When a feature ships, **add** completion notes with version + PR (e.g. `0.3.0-observability` · PR #13).
- New ideas → **append** new bullets or dated sections.
- When version/phase names change, **update references inline** — keep the original narrative.
- `IMPLEMENTATION_LOG.md`: new work = new dated section at the bottom.
- Before large doc restructuring, copy current files to `archive/docs/` first (`0.4.0-docs-resteer` did this).

## Session & Process Discipline

- Prefer **one fresh session per feature**.
- Use `/design` for any feature that introduces new mechanics or changes how traits evolve.
- Follow the standard flow: scoping → design (when needed) → human implements → human tests → documentation updates.

## Anti-Patterns

- Do not write code directly into `index.html` expecting it to be committed.
- Do not push for scope creep without strong justification tied to observability or the active phase.
- Do not over-document minor tweaks.

---

This file is the single source of truth for how any AI should behave while working on this repository.