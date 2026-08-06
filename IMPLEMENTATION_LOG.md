# Implementation Log — trait-evolution-sim

Dev log of **what already shipped** (past tense). **Append** new dated sections at the bottom. Do not use this file for roadmap, “what’s next,” or backlog — that lives only in **`FUTURE_FEATURES.md`**.

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

This establishes the project's vision, scope, three locked traits, and collaboration workflow before any code was written in `index.html`.

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

---

## 2026 — Design artifact nomenclature standardized (0.4.1+)

**Applies from here forward.**

- Design docs / implementation guides in `design-docs/` now use version codename prefix matching the shipped `N.x.y-codename` scheme (e.g. `0.4.1-observability-metrics-design.html`).
- Previous design docs renamed in-repo for consistency:
  - `0.1.0-foundation-design.html`
  - `0.2.0-run-history-design.html`
  - `0.3.0-observability-design.html`
- New rule documented in `AGENTS.md` (Versioning Ritual) and `FUTURE_FEATURES.md` (Version scheme).
- Canonical artifact is the versioned `.html` in `design-docs/`. Markdown drafts from `/design` may be kept as `.md` alongside when useful.
- All future `/design` outputs and manual design docs must follow this nomenclature.

This change was prepared together with the 0.4.1 observability metrics design and will ship in the same PR as the implementation changes.

## 2026 — `0.7.0-run-compare` Implemented

**Version / Phase:** `0.7.0-run-compare` · Phase 0 · Survive

**Pull Request**: (to be opened by human)

**Archive:** `archive/index-0.7.0-run-compare.html`

**Status**: Implementation complete. PR description prepared. Human will review/test further and decide on 0.8.0/0.9.0 before closing Phase 0.

**What was implemented** (changes applied iteratively with AI assistance, final state committed by human; this PR bundles 0.5.0-phase-rail + 0.6.0-run-setup + 0.7.0-run-compare):

- 0.5.0-phase-rail: Thematic arc UI label in sim (updated to v0.7.0-run-compare as part of this PR).
- 0.6.0-run-setup: Initial agent count slider, presets (Lenient / Balanced / Punishing), simplified controls + Advanced collapse, currentPreset tracking.
- 0.7.0-run-compare:
  - Full-run trends: trend arrays reset on `startNewRun()`, `MAX_TREND_SAMPLES=4000`, sampling conditioned on `!currentRunEnded`, x-scaling across full run duration.
  - Richer history cards: two-row compact cards with left color bar (by preset), ended badges, duration/initial pop on top, alive/end + avgs with readable labels on bottom.
  - Agent IDs: `nextAgentId`, `this.id` on Agent, shown in inspector.
  - Pin agent: "Pin to trends" button in inspector header (static, reliable). Creates separate "Pinned Agent Trends" section below main charts with dedicated Hunger + Food canvases.
  - Pinned box status: ID + `(alive)` / `(dead)` (color-coded) shown live in the pinned trends box header.
  - Remove/unpin: "Remove" button in pinned box header fully resets pinned state + graphs. Pin/unpin always clears pinned trend data.
  - Search by ID: input + Pin button in Trends tab; `searchAndPinAgent()` locates and pins.
  - History tab overview: added "Session Overview" stats (runs, avg dur, extinction rate, avg longest, avg peak pop, best).
- Cleanup per user feedback: removed top "Pinned:" status line near search input; removed bottom pin button from inside inspector content (kept only the reliable header button); pinned graphs are distinctly separate section.
- Tab switching robustness: forced re-renders on tab switch to prevent charts "stopping".

All changes respect single-file `index.html`, AGENTS.md rules, and radical simplicity.

**Documentation updates** (this PR):
- Archived previous state.
- Updated `VERSION`, `README.md`, `IMPLEMENTATION_LOG.md`, `FUTURE_FEATURES.md`.
- 0.7.0 marked shipped; roadmap updated.

**Testing notes**:
- Long runs show full history from beginning.
- Pin from inspector or search works; graphs appear below with status.
- Unpin resets cleanly.
- History cards readable and informative.
- Trends update after tab switches and speed changes.
- User will do further testing post-PR.

This completes the core 0.7.0 scope. Further Phase 0 work (0.8.0/0.9.0) TBD after testing.

---

## 2026-07-23 — Collaboration process resteer (Track A / Track B)

**Version / Phase:** process change (docs) · Phase 0 · Survive still active  
**Sim code:** not required by this entry alone (layout work may ship under separate 0.8.x entries)

### Why

After several releases, **manually implementing every feature** (full design doc → section-by-section paste into `index.html` → AI never touches the sim) became too time-consuming relative to the risk of the change. Layout and chrome work especially did not need that level of ceremony.

### What changed

Collaboration split into two tracks (documented in `AGENTS.md` and summarized in `README.md`):

| Track | Scope | Who implements | Gate |
|-------|--------|----------------|------|
| **A — Layout / presentation** | CSS, DOM, panels, docks, tabs, labels, visual hierarchy; no behavior change | AI may edit `index.html` directly | Browser smoke test; keep or restore archive |
| **B — Mechanics / sensibility** | Parameters, functions, algorithms, hunger/food/movement, run lifecycle, anything that changes sim behavior | Human leads; AI proposes or applies only with explicit supervision | Human judges sim feel + metrics |

**Still required:** single-file live `index.html`, versioned `archive/index-<version>.html` snapshots on meaningful steps and before PRs, human owns verification and “open the PR / push” decisions.

**Relaxed for Track A:** mandatory full design-docs and hand-typing every layout change. Design artifacts remain optional when the human wants them (especially Track B / non-trivial mechanics).

### Files updated for this resteer

- `AGENTS.md` — process resteer, Track A/B, lightweight versioning, next-PR checklist + PR template, updated Standing PR Directive, anti-patterns, new-chat paste blurb
- `README.md` — Development approach rewritten to match (why the change + two tracks)
- `IMPLEMENTATION_LOG.md` — this section

### Intent

Match process cost to risk: layout stays reversible via archives; **sensitive** changes (parameters, mechanics, algorithms) stay under human hands or close supervision.
---

## 2026-07-23 — `0.8.4-tight-layout` (Track A layout dashboard arc)

**Version / Phase:** `0.8.4-tight-layout` · Phase 0 · Survive  
**Track:** **A — Layout / presentation** (no hunger/food/movement algorithm changes)  
**Pull Request:** (to open after human verification)

### Arc included in this ship

| Step | Version | What |
|------|---------|------|
| Layout shell | `0.8.0-layout-dashboard` | Tall Command: header + left/center/right, Arctic Ice tokens, no tabs |
| Metrics + dock | `0.8.1-metrics-dock` | KPI live metrics; inspector dock in left column (not over canvas) |
| History table | `0.8.2-history-table` | Table D+: `# Pre Dur End Hung Food`; best top-right only; End=0 red; preset font colors; pin-by-ID in dock |
| Layout experiments | `0.8.3-layout-flex` | Intermediate flex/hide attempts (archived) |
| Tight A | `0.8.4-tight-layout` | `260 / 1fr / 260`; Hide on column heads; edge restore tabs; flush canvas; `resizeSimCanvas` when columns hide/show |

### Supporting fixes (still Track A)

- UI redraw gated on `uiFrame` (not `tick % N`) so 5×/10× charts keep updating after speed changes.
- Trend charts sized to column width (`sizeTrendCanvas`).
- Hide right/left uses `display: none` + 2-column grid so panels do not overlap the canvas.

### Archives

- `archive/index-0.8.0-layout-dashboard.html` … `archive/index-0.8.4-tight-layout.html` (intermediate freezes + live snapshot)
- `archive/MANIFEST.md` rows updated

### Docs

- Process resteer already in `AGENTS.md` / README Development approach / this log (2026-07-23 process section)
- `FUTURE_FEATURES.md` — 0.8.x marked shipped; deferred slide drawers noted there

### Explicitly not in this PR (Track B / later)

- Forage / seek-food movement
- Traits / greed analysis
- Animated slide drawers (registered in FUTURE_FEATURES only)

### How code was applied

AI Track A direct edits to `index.html` under human direction and iterative browser testing; human is Project Manager and owns verification + shipping.

---

## 2026-07-30 — Docs resteer: FUTURE_FEATURES backlog hygiene

**Version / Phase:** docs process · Phase 0 · Survive (`0.8.4-tight-layout` still live)  
**Track:** A (documentation / process only — no sim code)

### Why

`FUTURE_FEATURES.md` had become a **second history log**: every shipped idea stayed with “Completed in PR #…” markers, plus long superseded phase narratives. That cluttered the file and made “what’s next?” hard to see. History already lives in `IMPLEMENTATION_LOG.md`, archives, git, and VERSION.

### Before → after

| | **Before** | **After** |
|--|------------|-----------|
| **FUTURE_FEATURES.md** | Living historical record; mark done, never delete | **Active backlog only**; remove when shipped or dismissed |
| **IMPLEMENTATION_LOG.md** | Append-only ship log | Unchanged role — **sole museum** of shipped work + process notes |
| **Safety freeze** | — | `archive/docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md` (full pre-hygiene text) |

Also documented in `AGENTS.md` (Log philosophy + anti-patterns + PR checklist). Related earlier freezes: vision resteer `archive/docs/FUTURE_FEATURES-pre-resteer-2026-07-02.md` (2026-07-02).

### Audit of prior FUTURE_FEATURES open / mixed points

Every bullet from the pre-hygiene file was classified. Shipped items are **removed** from the backlog (already covered by log / PRs / archives). Open or deferred-wanted items remain in the new FUTURE_FEATURES. Dismissals recorded here so they are not re-added lightly.

#### Shipped (removed from FUTURE_FEATURES — history already in log / PRs)

| Item | Where it landed |
|------|-----------------|
| Hunger sliders / foundation polish | `0.1.0-foundation` · PR #7 |
| Run history minimal v1 | `0.2.0-run-history` · PR #8 |
| Observability suite (metrics, inspector, speed, trends, starvation counter, food respawn while alive) | `0.3.0-observability` · PR #13 |
| Archive infra + vision resteer docs | `0.4.0-docs-resteer` |
| Phase rail + version badge in UI | bundled in `0.7.0-run-compare` · PR #15 (0.5.0-phase-rail) |
| Presets, initial agent count, simplified controls | bundled in PR #15 (0.6.0-run-setup) |
| Full-run trends, richer history cards, agent IDs, pin + search by ID | `0.7.0-run-compare` · PR #15 |
| Layout dashboard arc (Tall Command, metrics dock, history table, column hide, canvas resize) | `0.8.0`–`0.8.4-tight-layout` · PR #17 |
| Old phase naming “Phase 1 = Trade” etc. | Superseded by Survive → Differ → Evolve → Economy (2026-07-02); not re-listed as open |

#### Still open / deferred-wanted (kept in FUTURE_FEATURES)

| Item | Status in new backlog |
|------|------------------------|
| `0.9.0-forage` (seek food / env-aware movement) | Phase 0 next · Track B |
| Slide left/right column drawers | Deferred UI · Track A later |
| Phase 1 traits + candidates (incl. hunger modulation once traits exist) | Phase 1 sketch |
| Phase 2 reproduction / inheritance / generational charts | Phase 2 sketch |
| Survivor Seed Lab Mode | Deferred after core Evolve |
| Trait-distribution live viz | Deferred with Evolve |
| Phase 3 economy sub-milestones (trade → …) | Phase 3 sketch |
| Multi-run overlay trend graphs | Observability open (lower priority) |
| Exportable / persistent run archives | Observability open |
| Light in-file code organization (comments/sections only) | Open, low priority |

#### Dismissed / out of scope for now (not in FUTURE_FEATURES backlog)

| Item | Why |
|------|-----|
| Government, policy layers | Explicitly deprioritized; not on path for Phase 0–2 |
| Multiple goods all at once | Breaks radical simplicity and observability-first path |
| Complex production chains without incremental observability | Same |
| Heavy financial systems early | Same — revisit only if Economy sub-milestones earn them later |

If any dismissed item is reconsidered, re-add it to FUTURE_FEATURES as a **new** open bullet with a short “why now,” and note the change in a new log section.

### Files touched this resteer

- `FUTURE_FEATURES.md` — rewritten lean backlog  
- `AGENTS.md` — Log philosophy, checklist, anti-patterns, new-chat blurb  
- `archive/docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md` — freeze  
- `archive/MANIFEST.md` — docs snapshot row  
- `IMPLEMENTATION_LOG.md` — this section  

### How applied

Docs-only Track A under human direction; no `index.html` / VERSION change required for this process resteer.

---

## 2026-07-30 — Design artifact: `0.9.0-forage`

**Version / Phase:** design only · Phase 0 · Survive (live sim still `0.8.4-tight-layout`)  
**Track:** B (mechanics design) — **not implemented**

### What

Added canonical design doc:

- `design-docs/0.9.0-forage-design.html`

Captures session brainstorm (2026-07-15 movement + always-seek + greed/analysis + presets roadmap), grounds it in current `Agent` random walk + eat rules, and specifies MVP algorithm, parameters, non-goals, Track B gates, acceptance criteria, and open human decisions (greed A/B/C, etc.).

### Docs cross-links

- `FUTURE_FEATURES.md` — open `0.9.0-forage` row points at the design file  
- Implementation still requires human request + browser feel tuning (Track B)

### Not in this step

- No `index.html` / VERSION / archive behavior change

---

## 2026-07-30 — `0.9.0-seek` (I1 Track B — forage arc)

**Version / Phase:** `0.9.0-seek` · Phase 0 · Survive  
**Track:** **B — Mechanics** (movement only; hunger rates / eat relief unchanged)  
**Versioning:** option **B** — each 0.9 slice gets its own codename + archive.

### What shipped

- **Default policy `seek`:** nearest food within `senseRadius`, blend = `clamp((hunger/100) * seekStrength)`, accel toward target + residual `wanderAmp` noise; speed capped at `maxSpeed`.
- **Policy `random`:** same wander-only path as pre-0.9 (A/B baseline).
- **Controls (basic):** Seek | Random buttons; sense radius; seek strength.
- **Inspector:** policy, seek blend, dist → food.
- Constants `seekAccel` / `wanderAmp` / `maxSpeed` exist for later Advanced UI (I3).

### Not in this slice

- Special agent, memory, density gradient, greed, Advanced popup.

### Archives / docs

- `archive/index-0.9.0-seek.html` + MANIFEST row  
- `VERSION` + UI badge `v0.9.0-seek`  
- README live line; FUTURE_FEATURES updated  
- Design still: `design-docs/0.9.0-forage-design.html`

### How applied

AI Track B implementation under human-directed I1 plan; human owns browser feel / keep-or-tweak.

### Human feel-test (2026-07-30) — freeze confirmed

- Tuned **max hunger rate** + **min food spawn** + sense/seek until ~½ agents survived long runs under **Seek**.  
- Toggled **Random** → population died quickly — strong A/B proof that seek works and is fun.  
- **Decision:** freeze this build as the official `0.9.0-seek` snapshot (re-copy live → `archive/index-0.9.0-seek.html`).

### Folded into the same freeze (other session feel-tunes)

Session `019fb43e-793a-7df0-9242-2a9b355e5ab3` (Track B feel-tests, then versioned here):

| Change | Detail |
|--------|--------|
| Food spawn interval slider | 1–50 (was 2–30); preset values still 5 / 8 / 12 |
| Spawn batch | 3 pellets per interval fire |
| Ground food ceiling | `NUM_FOOD * 10` (~700) |
| Agent draw fatness | `3 + sqrt(food) * 0.5` (consistent on main/outline paths) |
| KPI labels | Avg hunger; Min/Max **carried food** (not hunger min/max) |

---

## 2026-07-30 — Design artifact: `0.9.1-ui-chrome`

**Version / Phase:** design only · live sim remains `0.9.0-seek`  
**Track:** A (layout / presentation)

### What

- Added / revised `design-docs/0.9.1-ui-chrome-design.html` — viewport lock, header/badge/speed spacing, Seek/Random placement, basic sliders in wireframe, Advanced modal, Help/glossary modal, preset highlight + **retune for Seek-default**, acceptance, locked decisions.
- Cross-link / checklist updates in `FUTURE_FEATURES.md`.

### Not implemented

- No live CSS/DOM changes in this step.

## 2026-07-30 — `0.9.1-ui-chrome` (Track A freeze)

**Version / Phase:** `0.9.1-ui-chrome` · Phase 0 · Survive  
**Track:** A (layout / presentation + light preset retune + Help copy)

### What shipped

- Viewport lock: no page scroll; panels scroll internally.
- Header: title / phase / quiet mono version; Speed label outside tray + breathing room; Pause / Reset.
- Left rail: Run size → Environment → Movement (full-width Seek|Random + sense/seek) → Presets (`.on`) → Advanced… | Help → KPIs + inspector.
- Advanced modal (self-consume + ground eat knobs, live sliders).
- Help modal: plain-language lab guide (modes, controls, seek strength as hunger-driven pull, presets, metrics, history).
- Preset highlight + custom clear; Seek-default retune (Lenient / Balanced / Punishing numbers).
- Seek pathing / eat rules: unchanged from `0.9.0-seek` freeze.

### Process

- `VERSION` + badge → `0.9.1-ui-chrome`
- `archive/index-0.9.1-ui-chrome.html` + MANIFEST row
- Removed open 0.9.1 checklist from `FUTURE_FEATURES.md`
- README live-release line updated
- Human: “freeze it” after enjoying Seek feel

## 2026-08-02 — `0.9.2-special` (Track B + chrome freeze)

**Version / Phase:** `0.9.2-special` · Phase 0 · Survive  
**Track:** B (special param profile) + A (chrome around it)

### What shipped

- **Special agent:** one per run; amber ring; `p(agent, key)` resolver for overrides.
- **Special… popup:** per-knob custom vs world (policy, sense, seek strength, accel, wander, max speed, hunger, eat knobs); Match all → world; Focus/pin + Reroll body.
- **Not just pin:** pin = watch; special = different rules.
- **History:** dock shows latest **3** runs; **All history…** full session popup; history panel compact so **trends** get height.
- **Chrome:** Special + Help in header; Movement block at top of left rail; Initial agents under Environment; title **Trait Evolution Sim**; phase tagline *Agent evolution lab · Phase 0 Survive — hunger, food, who lasts* (`PHASE_TAGLINES` for later phases).
- Designs: `design-docs/0.9.2-special-design.html`, `design-docs/0.9.2-brand-header-design.html` (header options A–D; recommend B later).

### Process

- `VERSION` + badge → `0.9.2-special`
- `archive/index-0.9.2-special.html` + MANIFEST
- FUTURE_FEATURES updated for special shipped
- Human: freeze + push after feel OK

## 2026-08-02 — `0.9.3-vision` (product framing + brand path)

**Version / Phase:** `0.9.3-vision` · Phase 0 · Survive  
**Track:** A (presentation / vision)

### What shipped

- Header **N4:** `Project name: trait-evolution-sim` + subtitle **Agent evolution lab** + quiet version.
- **Vision…** modal: what this is, Survive now, Differ/Evolve/Economy later, dream of tuning best survivors (honest not built).
- Phase **P3** path as top chrome of **canvas-module** (connected to world, not agent field); no “You are here” / lab text on path; ~82% toward Differ.

### Process

- VERSION + archive `index-0.9.3-vision.html` + MANIFEST + README + FUTURE + LOG
- Builds on uncommitted post-0.9.2 path work after PR merge of special

---

## 2026-08-03 — Docs accuracy fix (README + FUTURE_FEATURES + log dates)

**Version / Phase:** docs only · Phase 0 · Survive (`0.9.3-vision` still live)  
**Track:** A (documentation)

### What changed

- **README.md**: Replaced outdated “Passive agents…” description with accurate current state (seek, special, vision shipped).
- **FUTURE_FEATURES.md**: Removed stale “default mechanic queue still `0.9.2-special`” sentence; backlog pointer corrected.
- **IMPLEMENTATION_LOG.md**: Corrected section dates for `0.9.2-special` and `0.9.3-vision` from 2026-07-30 → **2026-08-02** (actual commit dates). Appended this entry.

### Why

Review of project docs against live code and Git history found these three factual inaccuracies. No sim behaviour or VERSION change.

### How applied

AI Track A under human request to open the PR after the review.

---

## 2026-08-06 — Backlog: park last-food memory (skip as next)

**Version / Phase:** docs only · Phase 0 · Survive (`0.9.3-vision` still live)  
**Track:** docs / product priority

### Decision

Human does **not** want last-food memory (`0.9.4-memory`) as the next milestone. Keep the idea in `FUTURE_FEATURES.md` as **maybe later** only (revisit if play feel or Phase 1 traits earn it). Forage treated as playable with Seek + special alone.

### Docs updated

- `FUTURE_FEATURES.md` — strategy order, next table, deferred-mechanics section for memory  
- `README.md` — backlog pointer no longer leads with memory  
- This log entry  

No `VERSION` / `index.html` change.

---

## 2026-08-06 — `0.9.4-run-logs`

**Version / Phase:** `0.9.4-run-logs` · Phase 0 · Survive  
**Track:** A (modal / chrome / export) + light data plumbing (no agent behavior change)  
**Pull Request:** [#23](https://github.com/tiagomdv/trait-evolution-sim/pull/23)

### What shipped

- **Run logs…** modal (evolved All history): Option A table + click row → detail (outcomes, world knobs, special overrides).
- On `recordCurrentRun`: snapshot `knobs` + `special` (+ `movementPolicy`, `runInitialAgents`); dead special **`lifeSec`** via `specialLifeTicksAtDeath`.
- **Export last / all** + **Copy last / all** — pretty JSON envelope `{ version, exportedAt, runs }`.
- World Movement rail: **seek accel**, **wander amp**, **max speed** (parity with Special).
- Expanded Help glossary (movement knobs, run logs, metrics).
- Multi-run export → analysis loop documented in README; experiment findings recorded in **`FUTURE_FEATURES.md` Lab notes** (no Playbook file this version).
- Design: `design-docs/0.9.4-export-run-logs-design.html`.
- Archive: `archive/index-0.9.4-run-logs.html` + MANIFEST; `VERSION` + badge.

### Notes (as shipped)

- Knobs snapshot is end-of-run values; Export last is newest run (not necessarily selected row); Clear history does not reset run numbers.
