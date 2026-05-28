# trait-evolution-sim

A simple **spatial agent-based evolutionary simulation**.

**Core Idea**: Agents move in 2D space, need food to survive, can trade with each other, and possess a small number of heritable behavioral traits. Over many generations, we observe how these traits evolve under natural selection pressures.

This project serves as a deliberate learning vehicle for:
- Understanding emergent evolutionary dynamics in simple economic systems
- Practicing structured project management while collaborating with AI coding agents
- Building good habits around incremental development and GitHub workflows

## Current Focus (Locked In)

- 2D continuous space with moving agents ("dots")
- One resource: **Food**
- Basic hunger and survival mechanics
- Simple proximity-based trade
- **Three heritable behavioral traits**:
  1. **HoardingBias** — How reluctant an agent is to trade away food.
  2. **ExplorationRate** — Tendency to explore randomly vs exploit known food sources.
  3. **TradeBoldness** — Risk tolerance when making trades.

The goal is to clearly observe and measure how the distribution of these traits shifts across generations.

## Philosophy

- **Radical simplicity**: We only add features when they help us better observe and understand generational trait evolution.
- Strong emphasis on **observability** (graphs, statistics, visualizations of trait distributions over time).
- No government policy, complex multi-good economies, or heavy macro features in the early phases.

## Tech Stack

- Single-file `index.html` (for now)
- Tailwind CSS (via CDN)
- Vanilla JavaScript + HTML Canvas
- No build tools

## Project Structure

```
trait-evolution-sim/
├── README.md
├── AGENTS.md
├── FUTURE_FEATURES.md
├── IMPLEMENTATION_LOG.md
├── .gitignore
├── index.html
└── design-docs/
    ├── run-history-v1-design.html
    └── v0.1-simple-hunger-design-step-by-step.html
```

## Development Approach

This repository is developed with a strict "Human as Project Manager" workflow:
- The human manually implements features in `index.html`
- AI assists with design and documentation updates
- One focused feature per session / PR
- Emphasis on clear documentation and reviewable changes

See `AGENTS.md` for the detailed rules followed when collaborating with AI.

---

Built as a hands-on experiment in agent-based modeling and AI-assisted software development.