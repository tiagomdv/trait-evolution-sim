# trait-evolution-sim

A **spatial agent-based evolutionary simulation** that starts as a survival sandbox and grows into an observable micro-economy.

**North star:** Watch what helps agents survive become what helps them thrive as the world gets richer — hunger first, then behavioral differences, then generations, then economic interaction.

**Right now:** Phase 0 · Survive. Hunger, food, Seek/Random, Lab, export. Parameters live in a modal (Seek / Agent / island). Catch banks 1 food (no ground fill). Traits still uniform.

This project is also a deliberate learning vehicle for:
- Understanding emergent evolutionary dynamics in simple (then richer) economic systems
- Practicing structured project management while collaborating with AI coding agents
- Building good habits around incremental development and GitHub workflows

---

## Thematic arc

| Phase | Name | Focus |
|-------|------|-------|
| **0** | **Survive** | Hunger, food, death, run setup & comparison ← **now** |
| **1** | **Differ** | Behavioral traits; agents become heterogeneous |
| **2** | **Evolve** | In-run reproduction, inheritance, generations |
| **3** | **Economy** | Trade, storage, production, labor, … (one PR each) |

Active ideas backlog (open only): `FUTURE_FEATURES.md`. Ship history: `IMPLEMENTATION_LOG.md`.

---

## Current version

**`VERSION` file** is the single source of truth. Update it on every release PR, and update the live-release line below at the same time.

> **Live release:** `0.9.6-params` · Phase 0 · Survive

**0.9.6-params** — World rail: Policy + island presets + Parameters…. Presets = **Food spawn + Initial agents** (higher N = harder: L 35 / B 60 / P 80). Seek + Agent masters in the modal. Catch = bag +1, no ground fill. Pocket: hunger −= Gluttony × Efficiency.

**0.9.5-lab** — **World | Lab** mode switch; Lab headless batches (1–5 crowd setups, Parameters, progress, result cards, Export/Copy last batch). Default Lab ladder: Wander × Lenient / Balanced / Punishing. Shared difficulty packs tuned for an **alive-first** ladder under Wander (short Max-time for pop ranking; All-dead + 600s safety for wipe stories). No special in Lab. Design: `design-docs/0.9.5-lab-design.html`.

**0.9.4-run-logs** — **Run logs…** modal + export/copy JSON; seek accel / wander / max speed on world rail.  
**0.9.3-vision** — header N4; Vision…; phase path on canvas-module.  
**0.9.2-special** — parameterized special agent.  
**0.9.1-ui-chrome** — viewport lock, Advanced + Help, preset retune.  
**0.9.0-seek** — hunger-weighted seek.

See `FUTURE_FEATURES.md` for Playbook, optional graphs/history polish, memory (parked), and Phase 1.

---

## Run logs → analysis loop

**World mode** (canvas): tune live, use Special…, then **Run logs…** → Export/Copy for single-run stories.

**Lab mode** (headless): **Parameters…** → edit setups / batch → **Start batch** → **Export** / **Copy all**. Default: three Random setups on the difficulty packs. Prefer **short Max-time (75–90s)** when ranking remnant size; use **All dead** (600s safety) when ranking collapse. Watch out: long runs can make `avgFood` look huge from a tiny fat remnant; mean duration can look “mid” when half the seeds wipe early and half ride the wall.

Paste Lab or World JSON into an assistant for analysis. Recipe write-ups belong in a future **`PLAYBOOK.md`**.

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
