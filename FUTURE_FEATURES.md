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
- Basic visualization and population stats
- **v0.1 Foundation Polish**: Simple live parameter controls in the sidebar + tuning hunger/consumption to make starvation meaningfully punishing (simple variables + hardcoded sliders approach approved for initial foundation) **→ Completed in PR #7**

**v0.1 Polish Priorities** (original list — kept for historical reference):
- Hunger and consumption tuning (rates, thresholds, self-consumption logic) **→ Completed in PR #7**
- Basic metrics and observability (population stability, average lifespan, food availability)
- Visual feedback improvements
- Overall code clarity while staying single-file

**New observability features added after v0.1 observation** (appended 2026-05-28):
- Run history + previous run comparison (longest survival, etc.)
- Click on individual agent to inspect personal stats
- See "Run History, Metrics & Observability" section below for details.

**Future Polish Ideas** (not in v0.1):
- Lightweight "Starvation Deaths" counter for better observability of tuning effects
- Presets for the parameter panel (e.g. Lenient / Current / Punishing / Extreme)
- Ability for traits (once active) to modulate hunger parameters
- Long-term: Extracting the parameter panel code into a well-commented section inside the single `index.html` for better organization (no new files)

### Run History, Metrics & Observability (Captured 2026-05-28)
After completing the v0.1 hunger parameter controls and tuning (plain lets + sliders), and through direct observation of simulation behavior (especially with high `groundEatRelief` values), the following became clearly valuable:

- **Run History (Minimal v1)**: Store results of previous runs within the same browser session (longest survival time, final population, etc.) **→ Completed in PR #8**
- Simple way to compare multiple runs side-by-side (e.g. "Run #3 had one agent survive 4m12s") **→ Completed in PR #8**
- Basic per-run statistics panel (longest-lived agent, average lifetime, starvation deaths, etc.)
- Click on an individual agent (dot) to inspect its personal stats (current hunger, food carried, lifetime, possibly future traits like HoardingBias, etc.)

This direction emerged from real experimentation rather than being planned upfront. The click-to-inspect idea came right after finishing the v0.1 sliders and spending time observing individual agent behavior.

### Trait Exploration & Alternative Ideas (Captured 2026-05-28)
The current three locked traits (HoardingBias, ExplorationRate, TradeBoldness) were chosen early as a focused starting set. The human is open to refining or expanding the trait space before or during Phase 2.

**Observations from testing**:
- When `groundEatRelief` was set very high (5.0), the population still slowly died off, but one extremely lucky agent survived much longer than everyone else after the rest had died. This created an interesting "sole survivor" dynamic that was fun to watch.

**New trait direction ideas**:
- Social / grouping traits (e.g. a trait that makes agents enjoy staying near bigger/more successful dots — "follow the fat ones" behavior)
- More heterogeneous populations: different starting groups with different trait distributions instead of one uniform population
- Desire to explore a larger trait space overall rather than being locked into only the original three

These ideas should be revisited when designing the reproduction + inheritance system in Phase 2.

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