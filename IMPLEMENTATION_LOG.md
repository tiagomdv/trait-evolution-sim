# Implementation Log — trait-evolution-sim

Dev log. **Append** new dated sections at the bottom. When version/phase names change, add notes to existing entries — do not delete history.

> Safety snapshot before 2026-07-02 resteer: `archive/docs/IMPLEMENTATION_LOG-pre-resteer-2026-07-02.md`

---

## 2026 — Repository Created + Initial Documentation

**Version / Phase:** pre-versioning (docs foundation)

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

Next steps will focus on developing the simulation in subsequent PRs after this documentation foundation is reviewed and merged.

## 2026 — v0.1 Foundation Design Approved (Simple Approach)

**Version / Phase:** design target `0.1.0-foundation` · Phase 0 · Survive

**Design Artifact**: `trait-evolution-sim-design.html` (reviewed and tested by the human)

**Approach Chosen**: Simple version (plain `let` variables + a small number of hardcoded sliders in the sidebar). Rejected the heavier `CONFIG` + schema-driven panel for the initial foundation to keep things radically simple.

**Core Scope for v0.1 Implementation**:
- Add a few tunable parameters for hunger and consumption.
- Basic live sidebar controls for those parameters.
- Tune defaults to make starvation more punishing while remaining playable.
- Keep all changes inside the single existing `index.html`.

This design is now the reference for the first code changes to `index.html`. Implementation will follow small, focused PRs as per the updated AGENTS.md File Discipline rules.

Additional ideas from the design (starvation deaths counter, presets, future trait modulation of hunger, long-term code organization inside the single file) were moved to FUTURE_FEATURES.md under "Future Polish Ideas".

## 2026 — `0.1.0-foundation` Implemented (Live Hunger Sliders)

**Version / Phase:** `0.1.0-foundation` · Phase 0 · Survive

**Pull Request**: [#7 - feat: v0.1 Foundation Polish - Live hunger & consumption parameter controls](https://github.com/tiagomdv/trait-evolution-sim/pull/7)

**Archive:** `archive/index-0.1.0-foundation.html`

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

## 2026 — `0.2.0-run-history` Implemented

**Version / Phase:** `0.2.0-run-history` · Phase 0 · Survive

**Pull Request**: [#8 - feat: Run History + Basic Stats (Minimal v1) — in-memory run tracking and sidebar UI](https://github.com/tiagomdv/trait-evolution-sim/pull/8)

**Archive:** `archive/index-0.2.0-run-history.html`

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

## 2026 — `0.3.0-observability` Implemented

**Version / Phase:** `0.3.0-observability` · Phase 0 · Survive  
*(PR and `index.html` still said "UI/UX Polish v1" at ship time)*

**Pull Request**: [#13 - feat: UI/UX Polish v1 — tabs, metrics, trends, speed controls, floating inspector, deaths in run history](https://github.com/tiagomdv/trait-evolution-sim/pull/13)

**Archive:** `archive/index-0.3.0-observability.html`

**Status**: PR opened.

**What was implemented** (all changes manually applied and tested by the human before requesting the PR):
- Sidebar refactored into lightweight tabs (Controls | Metrics | Trends | History) to prevent clutter.
- Live aggregated metrics computation (`computeMetrics()`) and display in Metrics tab (alive, deaths, totalFood, avgHunger, minHunger, maxHunger, avgFood).
- Current-run time-series sampling + simple trend graphs (population, food, average hunger) in Trends tab.
- Speed control buttons (1x / 2x / 5x / 10x) with active styling in Controls tab.
- Floating bottom-right inspector card for selected agents (hunger, food, age) + pulsing pink outline on canvas.
- Starvation deaths now captured per run in `recordCurrentRun()`, stored in runHistory, and displayed in the history list.
- Food spawn interval exposed as live slider in Controls; respawn logic improved to keep food appearing while agents are alive.
- Full live update wiring (in gameLoop, tab switches, resets, etc.).

All changes maintain radical simplicity and single-file constraints.

**Documentation updates**:
- Added this entry to `IMPLEMENTATION_LOG.md`.
- Marked the UI/UX Polish section as completed in `FUTURE_FEATURES.md`.
- Updated phase labels in `index.html`.

This completes the UI/UX Polish + Advanced Observability section and creates the technical foundation for future observability (generational graphs etc.).

## 2026-07-02 — `0.4.0-docs-resteer` (Vision resteer + archive infrastructure)

**Version / Phase:** `0.4.0-docs-resteer` · Phase 0 · Survive  
**Type:** Documentation + archive. `index.html` simulation logic unchanged.

### What changed

- `archive/` with versioned `index.html` snapshots (`0.1.0`, `0.2.0`, `0.3.0`)
- `archive/docs/` safety copies of pre-resteer docs
- `archive/MANIFEST.md` index + `VERSION` file
- `archive/docs/README-pre-resteer-2026-07-02.md` (untouched GitHub copy)
- Merged docs: thematic arc, version references, preserved historical sections in `FUTURE_FEATURES.md` and `IMPLEMENTATION_LOG.md`
- `AGENTS.md`: versioning ritual + archive exceptions

### Vision decisions

- **Thematic arc:** Survive → Differ → Evolve → Economy
- **Version scheme:** `N.x` where major N = phase (`0.x` in Phase 0)
- Trade → Phase 3 · Economy (3.1), not standalone phase
- Phase 2 core: in-run reproduction; Survivor Seed Lab Mode deferred
- Traits not listed in README until Phase 1 scoping

### Next (Phase 0 code PRs)

1. `0.5.0-phase-rail` — thematic arc + version/phase in sim UI
2. `0.6.0-run-setup` — initial agents, presets, simplified controls
3. `0.7.0-run-compare` — full-run trends, richer history, agent pin

---
