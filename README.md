# trait-evolution-sim

A **spatial agent-based evolutionary simulation** that starts as a survival sandbox and grows into an observable micro-economy.

**North star:** Watch what helps agents survive become what helps them thrive as the world gets richer — hunger first, then behavioral differences, then generations, then economic interaction.

**Right now:** Phase 0 · Survive. Passive agents, hunger, food, starvation. Observability shipped (`0.3.0-observability`). Traits, reproduction, and trade are not implemented yet.

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

> **Live release:** `0.9.2-special` · Phase 0 · Survive

**0.9.2-special (Track B + chrome)** — one **special** agent with its own param profile (Special… popup: custom vs world for policy/sense/seek/hunger/eat); amber mark; pin remains for watching. Also: history last-3 + full history popup; trends get vertical room; Special/Help in header; Movement atop left rail; brand **Trait Evolution Sim** + phase-aware Survive tagline. Designs: `design-docs/0.9.2-special-design.html`, `design-docs/0.9.2-brand-header-design.html`.

**0.9.1-ui-chrome (Track A)** — viewport lock, Advanced + Help popups, preset retune.  
**0.9.0-seek (Track B)** — hunger-weighted seek. Design: `design-docs/0.9.0-forage-design.html`.

See `FUTURE_FEATURES.md` for memory, vision reworking (`0.9.4-vision`), Lab mode, export, and Phase 1.

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
