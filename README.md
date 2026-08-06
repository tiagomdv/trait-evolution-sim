# trait-evolution-sim

A **spatial agent-based evolutionary simulation** that starts as a survival sandbox and grows into an observable micro-economy.

**North star:** Watch what helps agents survive become what helps them thrive as the world gets richer — hunger first, then behavioral differences, then generations, then economic interaction.

**Right now:** Phase 0 · Survive. Agents with hunger, food, and seek-food movement. Observability, run history, layout, seek policy, special agent, and vision framing are shipped. Traits, reproduction, and trade are not implemented yet.

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

> **Live release:** `0.9.4-run-logs` · Phase 0 · Survive

**0.9.4-run-logs** — **Run logs…** modal + export/copy JSON envelope; world Movement also exposes seek accel / wander / max speed (parity with Special); expanded Help. Design: `design-docs/0.9.4-export-run-logs-design.html`.

**0.9.3-vision (Track A / product framing)** — header N4; Vision… modal; phase path on canvas-module.  
**0.9.2-special** — parameterized special agent + lab chrome.  
**0.9.1-ui-chrome** — viewport lock, Advanced + Help, preset retune.  
**0.9.0-seek** — hunger-weighted seek.

See `FUTURE_FEATURES.md` for Lab mode, Playbook, optional memory (parked), and Phase 1.

---

## Run logs → analysis loop

After **`0.9.4-run-logs`**, a useful workflow opened up:

1. Tune the world / special agent in **Play**  
2. Finish several runs (Reset or extinction)  
3. Open **Run logs…** → **Copy all** or **Export all**  
4. Paste the pretty JSON into an assistant (e.g. Grok) for cross-run comparison  

That loop is where **cool dynamics and experiment ideas** start to form — not only “did anyone survive?”, but stories like “Random world + super-Seek special → near wipe with one fat remnant,” spawn sweeps, and fairer A/Bs to try next. Those recipes belong in a future **`PLAYBOOK.md`**; the logs are the evidence trail.

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
