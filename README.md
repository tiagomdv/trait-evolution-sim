# trait-evolution-sim

A **spatial agent-based evolutionary simulation** that starts as a survival sandbox and grows into an observable micro-economy.

**North star:** Watch what helps agents survive become what helps them thrive as the world gets richer — hunger first, then behavioral differences, then generations, then economic interaction.

**Right now:** Phase 1 · Differ **live** as `1.0.0-differ`. Survive is a **finished game** next to it — two different HTML files (see below).

This project is also a deliberate learning vehicle for:
- Understanding emergent evolutionary dynamics in simple (then richer) economic systems
- Practicing structured project management while collaborating with AI coding agents
- Building good habits around incremental development and GitHub workflows

---

## Thematic arc

| Phase | Name | Focus |
|-------|------|-------|
| **0** | **Survive** | Hunger, food, death, Lab, params desk — **closed** |
| **1** | **Differ** | Behavioral traits; agents become heterogeneous ← **now (live)** |
| **2** | **Evolve** | In-run reproduction, inheritance, generations |
| **3** | **Economy** | Trade, storage, production, labor, … (one PR each) |

### Phase finish index

Each closed phase leaves a **frozen copy of the sim** next to `index.html`. Live lab stays `index.html`. Do not keep editing finish files.

| Phase | Status | Finish build | What “done” meant |
|-------|--------|--------------|-------------------|
| **0 · Survive** | **Closed** 2026-08-13 | **[`phase-0-survive-finished.html`](phase-0-survive-finished.html)** (`0.9.6-params`) | Hunger, Seek/Random, Special, Lab, export, island + Seek/Agent desk. Uniform agents. |
| **1 · Differ** | **Open** (`1.0.0-differ`) | — | Differ… modal, per-agent traits, apply on Reset. Trends/history/Lab later. |
| **2 · Evolve** | Later | — | In-run kids, inheritance, mutation. |
| **3 · Economy** | Later | — | Trade first, then storage / production / labor. |

When a phase closes, add a row snapshot here + `archive/index-<version>.html` + flip the canvas path. Don’t bump major `VERSION` until that phase’s first ship (`1.x`, `2.x`, …).

Active ideas: `FUTURE_FEATURES.md`. Ship history: `IMPLEMENTATION_LOG.md`.

---

## Two ways to play (do not mix them up)

You download / open **one file at a time**. They do not share state.

| | **Current Differ** (in development) | **Finished Survive** (closed game) |
|--|-------------------------------------|-------------------------------------|
| **Open this** | [`index.html`](index.html) | [`phase-0-survive-finished.html`](phase-0-survive-finished.html) |
| **Version** | `1.0.0-differ` (see `VERSION`) | Frozen `0.9.6-params` |
| **What it is** | Live World. Agents **differ at spawn**. | The Survive product, frozen 2026-08-13. Uniform crowd. |
| **You do** | **Crowd…** → Groups or Roster (or Import `phase-1-differ-presets/`) → **Reset**. Watch leftover colors. | Seek vs Random, L/B/P island, Special…, Lab batches, Trends, History, Parameters… |
| **Applies when** | Crowd edits apply on **Reset**. Food spawn is live weather. | Sliders / masters / presets as in Survive Help. |
| **Frozen / off** | Lab, Special, Trends, History (Survive leftovers, not Differ-aware). | Nothing — this file is the full Survive game. |
| **Do not** | Expect Lab or Special here. Don’t edit the Survive finish file. | Treat it as the live Differ lab. Don’t keep adding features to it. |

`index.html` is the only moving entrypoint. `phase-0-survive-finished.html` is a snapshot — same idea as `archive/index-0.9.6-params.html`, but named as the **playable Survive game**.

Need both? Keep the folder together. Opening only `index.html` is Differ; opening only the finish file is Survive. There is no in-app link between them (a lone download of `index.html` would 404).

---

## Current version

**`VERSION` file** is the single source of truth. Update it on every release PR, and update the live-release line below at the same time.

> **Live release:** `1.0.0-differ` · Phase 1 · Differ (first `1.x`)

**1.0.0-differ** — World **Differ…** modal (Groups + Roster). Default 30/30 Control vs Strain. Hunt / hunger / efficiency / speed per body; apply on Reset. Thin rail (no Policy, masters, L/B/P). Fair-eat. Inspector shows traits. Trends / History / Lab unchanged.

**0.9.6-params** — Survive close. Policy + island L/B/P + Parameters…. Catch = bag +1. Frozen as `phase-0-survive-finished.html`.

**0.9.5-lab** — **World | Lab** mode switch; Lab headless batches (1–5 crowd setups, Parameters, progress, result cards, Export/Copy last batch). Default Lab ladder: Wander × Lenient / Balanced / Punishing. Shared difficulty packs tuned for an **alive-first** ladder under Wander (short Max-time for pop ranking; All-dead + 600s safety for wipe stories). No special in Lab. Design: `design-docs/0.9.5-lab-design.html`.

**0.9.4-run-logs** — **Run logs…** modal + export/copy JSON; seek accel / wander / max speed on world rail.  
**0.9.3-vision** — header N4; Vision…; phase path on canvas-module.  
**0.9.2-special** — parameterized special agent.  
**0.9.1-ui-chrome** — viewport lock, Advanced + Help, preset retune.  
**0.9.0-seek** — hunger-weighted seek.

See `FUTURE_FEATURES.md` for Playbook, optional graphs/history polish, memory (parked), and Phase 1.

---

## Run logs → analysis loop

**Live Differ (`index.html`):** World canvas + Differ… + Reset. Trends / History / Lab are frozen. Use the inspector and leftover colors.

**Finished Survive (`phase-0-survive-finished.html`):** World: tune live, Special…, **Run logs…** → Export/Copy. Lab: **Parameters…** → Start batch → Export / Copy all. Default Lab: three Random setups on L/B/P. Prefer **short Max-time (75–90s)** when ranking remnant size; **All dead** (600s safety) for collapse. Long-run `avgFood` is tycoon-biased.

Paste Lab or World JSON into an assistant for analysis. Recipe write-ups belong in a future **`PLAYBOOK.md`**.

### Differ Lab screen (2026-08-13)

Human used **in-app Lab** (not a side script). Assistant read the JSON exports. Same island every card: Seek · Balanced · 90s · 30 seeds · one knob per variant. Control remnant held at **~4.2–4.7** alive / 60.

That is a **uniform-crowd** ranking (everyone shares the card’s knobs). It answers “does this knob move remnant?” It does **not** answer “does a quiet trait help in a mixed crowd?” — that needs mixed spawn later.

| Knob | Remnant shape (Balanced) | Differ lean |
|------|--------------------------|-------------|
| Hunger rate | Cliff then slope (0.049–0.084) | **1:1 trait** |
| Efficiency | 0.80 wipes; slope 1.2–2.4 | **1:1 trait** |
| Sight / pull / push | Off at floor; high end flat | One **hunt lock**, not three sliders |
| Max speed | Inverted U: 0.5 wipe · 1.2 tax · **1.6–3 flat** · 4 hurts | Freeze 2.0, or optional “slow” flavor |
| Gluttony · Eat threshold | Alive flat; bags/hunger shift | Not remnant traits |
| Drift (Seek) | ±0.8 | Optional / retest on Random |

Dose sketches (mean alive @ 90s):

- Hunger: `0.034→48` · `0.049→6.6` · `0.062→4.4` · `0.074→2.5` · `0.084→1.5`
- Efficiency: `0.80→0` · `1.20→1.9` · `1.60→4.2` · `2.00→6.6` · `2.40→8.2`
- Eat T: `5…28` all **~4.3–4.7**
- Speed: `1.2→3.1` · `1.6–3.0→4.2…4.8`

Full write-up: `IMPLEMENTATION_LOG.md` (2026-08-13 Differ Lab screen). Curves, other islands, mixed-edge: `FUTURE_FEATURES.md`.

---

## Philosophy

- **Observability first** — every feature must make it easier to see *why* populations change.
- **Radical simplicity on the core path** — complexity earns its place with clear signal.
- **Ambitious vision, disciplined execution** — we ship one focused PR at a time.

---

## Tech stack

- Single-file `index.html` (for now)
- Tailwind CSS (via CDN)
- Vanilla JavaScript + HTML Canvas
- No build tools

---

## Project structure

```
trait-evolution-sim/
├── VERSION
├── index.html
├── README.md
├── AGENTS.md
├── FUTURE_FEATURES.md
├── IMPLEMENTATION_LOG.md
├── archive/
│   ├── MANIFEST.md
│   ├── index-<version>.html
│   └── docs/
└── design-docs/
```

---

## Development approach

**Human as Project Manager** remains: one focused goal per session when possible, reviewable changes, and the human decides when to ship.

Early on, every feature was **manually implemented** in `index.html` (design → section paste → AI never touched the sim). That was great for learning GitHub workflows and owning the first survival mechanics. After several releases it became **too slow for low-risk work** (layout, chrome, presentation).

**Process resteer (2026-07-23):** match process cost to risk.

| Track | What | Who implements |
|-------|------|----------------|
| **A — Layout / presentation** | Structure, CSS, panels, docks, tabs, labels — no behavior change | AI may edit `index.html` directly; human smoke-tests in the browser |
| **B — Mechanics / sensibility** | Parameters, functions, algorithms, hunger/food/movement, run rules | Human leads (or closely supervises); AI proposes patches |

**Always:** live app is a single `index.html`; freeze good states as `archive/index-<version>.html`; human verifies and requests PRs/pushes. Version label lives in `VERSION` + the UI, not in the live filename.

Full rules, next-PR checklist, and PR template: **`AGENTS.md`**. History of this change: **`IMPLEMENTATION_LOG.md`** (2026-07-23). Optional design docs still live in `design-docs/` (`<version>-<codename>-design.html`) when useful — not required for pure layout work.

---

Built as a hands-on experiment in agent-based modeling and AI-assisted software development.
