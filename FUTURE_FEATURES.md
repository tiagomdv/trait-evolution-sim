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
- Hunger and consumption tuning (rates, thresholds, self-consumption logic)
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