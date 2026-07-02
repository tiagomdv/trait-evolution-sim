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

Full task list and ideas backlog: `FUTURE_FEATURES.md`.

---

## Current version

**`VERSION` file** is the single source of truth. Update it on every release PR, and update the live-release line below at the same time.

> **Live release:** `0.4.0-docs-resteer` · Phase 0 · Survive

Upcoming Phase 0 work: `FUTURE_FEATURES.md` (`0.5.0-phase-rail` → `0.6.0-run-setup` → `0.7.0-run-compare`).

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

This repository uses a strict **Human as Project Manager** workflow:
- The human manually implements features in `index.html`
- AI assists with design and documentation updates
- One focused feature per session / PR
- Emphasis on clear documentation and reviewable changes

See `AGENTS.md` for versioning ritual and collaboration rules.

---

Built as a hands-on experiment in agent-based modeling and AI-assisted software development.
