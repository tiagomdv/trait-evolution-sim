# Future Features & Roadmap — trait-evolution-sim

**Project Goal**: Build a clean, observable 2D agent-based simulation where we can clearly watch behavioral traits evolve across generations through survival, trade, and reproduction.

We use only one resource (Food) and keep the rules simple on purpose.

---

## Locked Core Traits

1. **HoardingBias**
2. **ExplorationRate**
3. **TradeBoldness**

(See README.md for explanations of each.)

---

## Phased Roadmap

### Phase 0 – Bare Survival (Foundation)

**Core Mechanics**
- 2D continuous movement in a toroidal world
- Environmental food that spawns sparsely and randomly
- Hunger system + consumption (carried food and ground food)
- Death from starvation
- Basic visualization and population stats

**v0.1 Foundation Polish Priorities**
- Hunger and consumption tuning (rates, thresholds, self-consumption logic) → Completed in PR #7
- Food distribution, density, and respawn behavior
- Movement feel and random walk quality
- Basic metrics and observability (population stability, average lifespan, food availability over time)
- Exposure of key parameters for easier tuning
- Visual feedback improvements (hunger state, food levels)
- Overall code clarity and structure while staying single-file

### Phase 1 – Trade
- Proximity-based trading between agents
- Simple willingness logic

### Phase 2 – Reproduction + Trait Evolution (Core Milestone)
- Agents can reproduce when they have surplus food
- Traits are inherited with mutation
- Population turns over across generations
- Begin tracking trait distributions over time

### Phase 3+ – Richer Evolutionary Dynamics
- More environmental variation
- Additional light mechanics (only if they improve observability of evolution)
- Stronger visualization and statistics for generational change

---

**Explicitly deprioritized for now**: Government, policy, multiple goods, complex production chains, financial systems.

We will only consider these much later, once the core evolutionary dynamics are clear and well-observed.

---

## New Ideas Captured After v0.1 Observation (2026-05-28)

These ideas emerged from actually building and running the v0.1 sliders and experimenting with the simulation (especially high `groundEatRelief` values that produced interesting "lucky survivor" dynamics). They are recorded here for future consideration.

### Run History, Metrics & Observability
- Store results of previous runs within the same browser session (longest survival time, final population, peak population, etc.)
- Simple way to compare multiple runs side-by-side
- Basic per-run statistics panel (longest-lived agent, average lifetime, starvation deaths, etc.)
- Click on an individual agent (dot) to inspect its personal stats (current hunger, food carried, lifetime, possibly future traits)

### Trait Exploration & Alternative Ideas
The current three locked traits were chosen early as a focused starting set. Openness to refine or expand:
- Social / grouping traits (e.g. affinity for staying near bigger/more successful dots — "follow the fat ones")
- Support for heterogeneous populations with different starting trait distributions
- Desire to explore a larger overall trait space rather than being locked to only the original three

These should be revisited when designing the reproduction + inheritance system in Phase 2.