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

**Pull Request**: [#8 - feat: v0.1 Foundation Polish - Live hunger & consumption parameter controls](https://github.com/tiagomdv/trait-evolution-sim/pull/8)

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

**Pull Request**: [#10 - feat: Run History + Basic Stats (Minimal v1) — in-memory run tracking and sidebar UI](https://github.com/tiagomdv/trait-evolution-sim/pull/10)

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

**Pull Request**: [New PR from this branch - direct fixes to historical references]

**Note**: The PR numbers in the two sections above were corrected in-place in this commit (v0.1 Polish section now correctly points to merged PR #8; Run History section now correctly points to merged PR #10). This was done as an explicit exception to the project's normal "add, don't replace" rule for historical logs, per direct human request.

The previous incorrect references have been updated directly for long-term accuracy of the project record. The `design-docs/` folder and its two detailed step-by-step guides were created during PR #10 alongside the Run History feature.