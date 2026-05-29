# Implementation Log — trait-evolution-sim

## 2026 — Repository Created + Initial Documentation

**Repository**: https://github.com/tiagomdv/trait-evolution-sim

**Pull Request**: [#1 - docs: Add foundational documentation](https://github.com/tiagomdv/trait-evolution-sim/pull/1)

**Status**: Documentation PR opened for review.

**Files included in this PR**:
- `README.md`
- `AGENTS.md`
- `FUTURE_FEATURES.md`
- `IMPLEMENTATION_LOG.md`
- `.gitignore`

This establishes the project's vision, scope, three locked traits, and collaboration workflow before any code is written in `index.html`.

Next steps will focus on developing the simulation in subsequent PRs after this documentation foundation was reviewed and merged.

## 2026 — v0.1 Foundation Design Approved (Simple Approach)

**Design Artifact**: `trait-evolution-sim-design.html` (reviewed and tested by the human)

**Approach Chosen**: Simple version (plain `let` variables + a small number of hardcoded sliders in the sidebar). Rejected the heavier `CONFIG` + schema-driven panel for the initial foundation to keep things radically simple.

**Core Scope for v0.1 Implementation**:
- Add a few tunable parameters for hunger and consumption.
- Basic live sidebar controls for those parameters.
- Tune defaults to make starvation more punishing while remaining playable.
- Keep all changes inside the single existing `index.html`.

This design is now the reference for the first code changes to `index.html`. Implementation will follow small, focused PRs as per the updated AGENTS.md File Discipline rules.

Additional ideas from the design (starvation deaths counter, presets, future trait modulation of hunger, long-term code organization inside the single file) were moved to FUTURE_FEATURES.md under "Future Polish Ideas".

## 2026 — v0.1 Foundation Polish Implemented (Live Hunger Sliders)

**Pull Request**: [#7 - feat: v0.1 Foundation Polish - Live hunger & consumption parameter controls](https://github.com/tiagomdv/trait-evolution-sim/pull/7)

**Status**: PR opened.

**What was implemented** (all changes manually applied and tested by the human before requesting the PR):
- Added 5 plain top-level `let` variables for hunger parameters (`hungerRate`, `selfConsumeRelief`, `groundEatRelief`, `selfConsumeThreshold`, `selfConsumeAmount`) with explanatory comments.
- Implemented a minimal right sidebar using Tailwind with 5 hardcoded range sliders.
- All slider values directly mutate the `let` variables and take effect on the next frame (fully live).
- Layout change: wrapped the simulation in a flex container so the sidebar sits to the right of the canvas.
- Added `initHungerSliders()` wiring function.
- Through live experimentation (especially with high `groundEatRelief`), interesting "lucky survivor" dynamics were observed.

**Documentation updates**:
- `FUTURE_FEATURES.md` was significantly expanded with new sections:
  - Run History, Metrics & Observability (including run comparison and click-to-inspect individual agents)
  - Trait Exploration & Alternative Ideas
- These ideas emerged organically from actually using the tuned simulation rather than from upfront design.

This marks the completion of the approved v0.1 simple approach. The project now has live, tunable hunger mechanics while remaining radically simple.

## 2026 — Run History + Basic Stats (Minimal v1) Implemented

**Pull Request**: [#8 - feat: Run History + Basic Stats (Minimal v1) — in-memory run tracking and sidebar UI](https://github.com/tiagomdv/trait-evolution-sim/pull/8)

**Status**: PR opened.

**What was implemented** (all changes manually applied and tested by the human before requesting the PR):
- Added 6 top-level tracking variables (`runNumber`, `runStartTick`, `runHistory`, `currentRunMaxSurvivalTicks`, `currentRunEnded`, `bestLongestSec`).
- Added `birthTick` field to the `Agent` class.
- Implemented `recordCurrentRun()` — single function responsible for ending and saving a run.
- Recording triggers on both manual Reset and natural population == 0.
- Added `renderRunHistory()` and `clearRuns()` functions.
- Extended the existing right sidebar with "Best longest survival" callout + run list + Clear button.
- All changes follow the radically simple pattern established in v0.1 (plain `let`s + hardcoded Tailwind).

**Documentation updates**:
- Created `design-docs/` folder and moved design documents into it:
  - `design-docs/run-history-v1-design.html`
  - `design-docs/v0.1-simple-hunger-design-step-by-step.html`
- Updated `README.md` Project Structure.
- Marked Run History as completed in `FUTURE_FEATURES.md`.
- This entry in `IMPLEMENTATION_LOG.md`.

This delivers the first post-v0.1 observability feature that emerged from actual usage of the simulation.

## 2026 — PR Reference Corrections + Design Docs Clarification

**Pull Request**: [#XX - docs: Correct PR numbers in FUTURE_FEATURES.md and IMPLEMENTATION_LOG.md + document design docs creation](https://github.com/tiagomdv/trait-evolution-sim/pull/XX)

**Status**: Documentation-only correction PR.

**Corrections recorded** (additive only — all prior historical text preserved per Log Files Philosophy):

- **v0.1 Foundation Polish** (the 5 hunger `let` variables, live Tailwind sliders in the right sidebar, flex layout change, and `initHungerSliders()` wiring) was delivered in **merged PR #8** (not #7). PR #7 was an earlier duplicate attempt that was closed without merge (labeled "invalid").

- **Run History + Basic Stats (Minimal v1)** (the 6 tracking variables, `birthTick` on Agent, `recordCurrentRun()`, automatic recording on both manual Reset and natural population extinction, `renderRunHistory()` + `clearRuns()`, sidebar UI section with "Best longest survival this session" callout + list + Clear button, and all supporting logic) was delivered in **merged PR #10** (not #8). PR #9 was a noisy superseded attempt that was explicitly closed in favor of the clean PR #10.

- The `design-docs/` folder and its two detailed implementation guides were created in PR #10 as part of the Run History work:
  - `design-docs/run-history-v1-design.html` (11 micro-steps, exact scope table, key decisions, PR plan)
  - `design-docs/v0.1-simple-hunger-design-step-by-step.html`

These design docs are high-quality, self-contained step-by-step guides that were used during the actual human-led implementation sessions. They provide significantly more implementation detail than the summary entries in this log.

These corrections were identified via full review of the documentation against the actual merged PR diffs, changed files, commit history, and the current state of `index.html`. No existing historical text was modified — only this new section was appended.