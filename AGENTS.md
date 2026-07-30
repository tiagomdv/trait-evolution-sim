# AGENTS.md — trait-evolution-sim

**Repository**: https://github.com/tiagomdv/trait-evolution-sim

**Your Role**: Coding collaborator. The human (tiagomdv) is Project Manager and final decider on mechanics/tuning.

**Read this whole file** at the start of any session that implements, versions, or opens a PR for the sim.

---

## Process resteer (2026-07-23) — READ FIRST

The old flow (full design doc → section-by-section human paste into `index.html` → AI never touches the sim) was too slow for layout work. **New default:**

| Track | What | Who implements | Design doc? | Gate |
|-------|------|----------------|-------------|------|
| **A — Layout / chrome / presentation** | CSS, DOM structure, panels, docks, tabs, labels, spacing, visual hierarchy, non-behavioral UI | **AI may edit `index.html` directly** | Optional bullets/sketch only; skip full design-docs unless human asks | Human opens in browser; short smoke test; keep or restore archive |
| **B — Mechanics / sensibility** | Parameters, functions, algorithms, hunger/food/movement rules, run lifecycle, anything that changes sim *behavior* | **Human leads** (AI may propose patches; human applies/tunes or explicitly asks AI to apply under supervision) | Short design when behavior is ambiguous; `/design` for non-trivial mechanics | Human runs the sim and judges feel + metrics |

**Match process cost to risk.** Layout is reversible if snapshots exist. Mechanics are not.

**Still true:**

- Live app remains a **single** runnable `index.html` (do not rename the live entrypoint; version lives in `VERSION` + archive filenames + UI label).
- **One feature at a time** per session / PR when possible.
- **Never push** unless the human explicitly asks you to push.
- Prefer **human commits** unless the human says otherwise for that session.
- Respect phase scope (Phase 0 · Survive until the human moves on).

---

## Handoff for the next PR (checklist)

Use this when shipping the next version (e.g. layout 0.8.x work currently local).

### Before coding

1. Read `VERSION`, live `index.html` version label, and `archive/MANIFEST.md`.
2. Classify the work as **Track A** (layout) or **Track B** (mechanics). Do not mix tracks in one PR without human approval.
3. If live `index.html` is ahead of the latest archive snapshot for the *previous* good state, **archive first** (see Versioning).

### While coding (Track A — default for layout)

1. Edit `index.html` in place.
2. Bump `VERSION` and the in-sim version/phase label together.
3. Snapshot **meaningful** steps only (not every CSS tweak):
   - Before a risky rewrite
   - When a codename/version feels “done enough”
   - Before switching tracks or opening a PR
4. Do **not** silently change mechanics while doing layout.

### Smoke test (layout PRs) — human or AI-guided

- Start a new run; pause / resume; change speed
- Open Trends and History tabs; charts still draw after tab switch
- Inspector: select agent, pin/unpin if present, search-by-ID if present
- Resize window; nothing critical overflows or vanishes
- Confirm UI version string matches `VERSION`

### Before opening the PR

1. `archive/index-<previous-or-current-version>.html` exists for the pre-PR baseline if this PR changes the sim
2. `VERSION` matches in-sim label
3. `archive/MANIFEST.md` has a row for any new archive file
4. README live-release line updated if this ships a new version
5. Short `IMPLEMENTATION_LOG.md` section at the bottom (add, don’t replace)
6. `FUTURE_FEATURES.md` — **remove** shipped/dismissed items; **append** only still-open ideas (see Log philosophy)
7. **No** requirement for a full design-docs package on Track A unless the human wanted one

### PR description template

```markdown
## Track
A (layout) | B (mechanics) | mixed (human approved)

## Summary
- What changed in plain language
- Version: `x.y.z-codename` (from VERSION)

## Process
- [ ] Snapshot/archive step done for baseline
- [ ] VERSION + in-sim label + MANIFEST (+ README if needed) updated
- [ ] Smoke test passed (layout) / sim feel checked (mechanics)
- [ ] Human reviewed and requested this PR after verification

## Notes
- AI applied layout directly / human applied mechanics / other: …
- Known follow-ups (optional)
```

**Standing PR Directive (updated):** Every PR must state that the human **requested the PR after verification**, and how the code was applied (**AI Track A**, **human Track B**, or **paired**). Simulation/code PRs must note that the human (or paired session) **tested in the browser**. Process integrity = human ownership of *shipping*, not necessarily hand-typing every line of CSS.

---

## File Discipline (Non-Negotiable)

- **Do not create new files** unless the human has explicitly approved them for the current work, or they fall under approved exceptions.
- Keep the sim as a **single** `index.html` for as long as possible. No new `.js` / `.css` / `.json` splits without explicit approval.
- **Approved exceptions:**
  - `VERSION` — one-line live release label
  - `archive/index-<version>.html` — frozen sim snapshots (**never edit in place**)
  - `archive/docs/*` — safety copies before large doc restructuring
  - `archive/MANIFEST.md` — archive index only
  - `design-docs/` — design artifacts when the human wants them (not mandatory for Track A)
- Keep `index.html` readable; put long rationale in docs (`README.md`, `IMPLEMENTATION_LOG.md`, `FUTURE_FEATURES.md`, `AGENTS.md`).

### Naming

- **Live entrypoint stays `index.html`.** Do not rename it to carry the version.
- Version identity: `VERSION` file + UI label + `archive/index-<version>-<codename>.html`.

---

## Versioning Ritual (lightweight + milestone)

**Scheme:** `N.x.y-codename` where **major N = phase number** (`0.x` = Phase 0 · Survive, …).

### Lightweight (Track A iteration)

1. If the current good state is not archived yet:  
   `cp index.html archive/index-<VERSION>.html` (use the version *being left behind*)
2. Implement; bump `VERSION` + in-sim label
3. Smoke test
4. Optional: commit when the human is happy

Do **not** spam archives every ten lines of CSS. Snapshot on meaningful steps and before PRs.

### Milestone / PR that ships a version

1. Ensure archive snapshot(s) for previous live version exist
2. `VERSION` + in-sim version/phase display
3. README live-release line
4. `archive/MANIFEST.md` row(s)
5. `IMPLEMENTATION_LOG.md` dated section
6. After merge (human): git tag `v<version>` when they care

**Docs-only PRs:** bump `VERSION` if release identity changes; copy docs to `archive/docs/` before large restructuring.

**Never edit files inside `archive/`** (only add new snapshots + update `MANIFEST.md`).

### Design artifacts (optional, not the default gate)

When the human asks for design docs or `/design` (especially Track B):

- `design-docs/<version>-<codename>-design.html`
- or `…-implementation-guide.html` for step-by-step guides

Track A does **not** require these by default.

---

## Core Rules (summary)

1. **One feature at a time** (don’t bundle unrelated mechanics + layout without approval).
2. **Track A:** AI may write `index.html`. **Track B:** human leads; AI assists.
3. **Human owns ship:** verification + “open the PR” decision; no surprise pushes.
4. **Phase scope** always.
5. **Add, don’t replace** history in `IMPLEMENTATION_LOG.md`. `FUTURE_FEATURES.md` is a **backlog** (remove done items — see Log philosophy).

---

## Capturing Deferred Ideas

Out of scope *for now* but still wanted → append to `FUTURE_FEATURES.md` under Deferred / the right phase.  
Dismissed forever (or for a long time) → one line in `IMPLEMENTATION_LOG.md` (why not); **do not** leave in FUTURE_FEATURES.

---

## Project Focus

**Thematic arc:** Survive → Differ → Evolve → Economy

| Phase | Name | Focus |
|-------|------|-------|
| 0 | Survive | Hunger, observability, run comparison, layout/usability ← **now** |
| 1 | Differ | Behavioral traits (no genetics) |
| 2 | Evolve | In-run reproduction, inheritance, generations |
| 3 | Economy | Trade → storage → production → labor → … |

Prefer one mechanic per PR. Stay observable. Trait set finalized when Phase 1 begins.

---

## Documentation Responsibilities

After the human approves a shipped change:

- `VERSION` + README live-release line (if version ships)
- `IMPLEMENTATION_LOG.md` — new dated section at the bottom (**append only**)
- `FUTURE_FEATURES.md` — **delete** matching open items that shipped; leave only still-open work; append new ideas if any
- `archive/MANIFEST.md` — when a new snapshot is added
- Full design-docs only if used for that feature

### Log philosophy (docs resteer 2026-07-30 — backlog hygiene)

| File | Role | Edit rule |
|------|------|-----------|
| **`IMPLEMENTATION_LOG.md`** | History of what shipped / process changes / dismissals | **Append only.** Never delete past sections. |
| **`FUTURE_FEATURES.md`** | **Active backlog** — next work + deferred-but-still-wanted | **Remove** items when shipped or dismissed. **Append** new open ideas. Do **not** keep “Completed in PR #N” clutter. |
| **`archive/docs/*`** | Safety freezes before large doc rewrites | Add-only snapshots |

**Before this resteer (mark-done / never-delete FUTURE_FEATURES):** the file mixed shipped history with open ideas and became hard to scan. Full pre-hygiene copy: `archive/docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md`.  

**After:** FUTURE_FEATURES = forward only; IMPLEMENTATION_LOG = museum. Optional one-line “Last shipped” pointer at top of FUTURE_FEATURES is fine.

**Lifecycle:** capture idea → FUTURE_FEATURES → ship or dismiss → IMPLEMENTATION_LOG entry → remove from FUTURE_FEATURES.

---

## Session discipline

- Prefer one clear goal per session (e.g. “metrics dock layout” or “hunger rate tuning”).
- Track A: implement → smoke → version/archive as needed → PR when human is ready.
- Track B: short design if needed → human (or supervised) apply → sim feel → docs → PR.
- Do not over-document minor layout tweaks; batch docs at milestone PR time if iterating fast.

---

## Anti-Patterns

- Changing hunger/food/movement/algorithms “while doing layout” without labeling Track B and human buy-in.
- Skipping archive before a large rewrite of `index.html`.
- Creating new source files / splitting the single-file sim without approval.
- Full design-doc + section paste ritual for pure CSS/layout (obsolete default).
- Pushing or opening PRs without human request.
- Editing anything under `archive/` except adding new snapshots + MANIFEST rows.
- Overwriting or deleting history in **`IMPLEMENTATION_LOG.md`**.
- Leaving **shipped or dismissed** items in **`FUTURE_FEATURES.md`** with completion markers (use the log, then delete from the backlog).

---

## Quick copy-paste for a new chat

```
Read AGENTS.md fully (process resteer 2026-07-23 + backlog hygiene 2026-07-30).
This session is Track A (layout) / Track B (mechanics): <pick one>.
Goal: <one sentence>.
Live VERSION is the source of truth; archive before risky edits; single index.html.
FUTURE_FEATURES is active backlog only — remove items when shipped; history goes in IMPLEMENTATION_LOG.
Do not push unless I ask. Open a PR only after I verify and request it.
```

---

This file is the single source of truth for how any AI should behave in this repository.
```