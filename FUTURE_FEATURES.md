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
- 2D movement
- Food in the environment
- Hunger + consumption
- Death from starvation
- Basic visualization

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