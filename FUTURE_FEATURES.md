# Future Features & Roadmap — trait-evolution-sim

**Living task & ideas list.** Keep appending. When something ships, mark it with **version + PR**. Older entries stay — this file is the master history.

**Current phase:** 0 · Survive  
**Current version:** see `VERSION`  
**Thematic arc:** Survive → Differ → Evolve → Economy

---

## Active roadmap (2026-07-02 resteer)

### Version scheme

Major version = phase number (`0.x` = Phase 0, `1.x` = Phase 1, …). Codename describes the milestone.

### Phase 0 · Survive — shipped

| Version | PR | Milestone |
|---------|-----|-----------|
| `0.1.0-foundation` | #7 | Hunger sliders + live sidebar |
| `0.2.0-run-history` | #8 | Session run history + basic stats |
| `0.3.0-observability` | #13 | Tabs, metrics, trends, inspector, speed *(was "UI/UX Polish v1")* |
| `0.4.0-docs-resteer` | — | Archive infra + vision resteer (docs only) |

### Phase 0 · Survive — next

| Version | Milestone |
|---------|-----------|
| `0.5.0-phase-rail` | Thematic arc UI in sim — Survive → Differ → Evolve → Economy; highlight active phase + version badge |
| `0.6.0-run-setup` | Initial agent count, presets (Lenient / Balanced / Punishing), simplified controls + Advanced collapse |
| `0.7.0-run-compare` | Full current-run trends, richer History cards, agent IDs, pin-to-trends |

### Future phases (thematic arc)

| Phase | Name | First planned version |
|-------|------|----------------------|
| 1 | Differ | `1.0.0-traits` (trait set TBD) |
| 2 | Evolve | `2.0.0-reproduction` |
| 3 | Economy | `3.0.0-trade` → storage → production → labor → … |

**Phase 2 note:** In-run reproduction is core. Survivor Seed Lab Mode (traits from survivors seed next Reset) is deferred — see appended section below.

**Phase 3 note:** Trade is the entry point to Economy, not a standalone phase.

> Safety snapshot before this resteer: `archive/docs/FUTURE_FEATURES-pre-resteer-2026-07-02.md`

---

# Historical record (preserved — completion markers updated where applicable)

**Project Goal**: Build a clean, observable 2D agent-based simulation where we can clearly watch behavioral traits evolve across generations through survival, trade, and reproduction.

We use only one resource (Food) and keep the rules simple on purpose.

---

## Locked Core Traits

*Early candidate list — revisit when Phase 1 · Differ begins.*

1. **HoardingBias**
2. **ExplorationRate**
3. **TradeBoldness**

Additional candidates (2026-07-02): Patience / FutureOrientation, SocialAffinity, HarvestEfficiency, RiskSensitivity, Reciprocity.

---

## Phased Roadmap

### Phase 0 – Bare Survival (Foundation)

*Now labeled: Phase 0 · Survive*

- 2D movement
- Food in the environment
- Hunger + consumption
- Death from starvation
- Basic visualization and population stats
- **Foundation polish** → `0.1.0-foundation` **Completed in PR #7**

**v0.1 Polish Priorities** (original list — kept for historical reference):
- Hunger and consumption tuning (rates, thresholds, self-consumption logic) → `0.1.0-foundation` **PR #7**
- Basic metrics and observability (population stability, average lifespan, food availability)
- Visual feedback improvements → `0.3.0-observability` **PR #13**
- Overall code clarity while staying single-file

**New observability features added after v0.1 observation** (appended 2026-05-28):
- Run history + previous run comparison (longest survival, etc.)
- Click on individual agent to inspect personal stats
- See "Run History, Metrics & Observability" section below for details.

**Future Polish Ideas** (not in v0.1):
- Lightweight "Starvation Deaths" counter → `0.3.0-observability` **PR #13**
- Presets for the parameter panel (e.g. Lenient / Balanced / Punishing) → planned `0.6.0-run-setup`
- Ability for traits (once active) to modulate hunger parameters
- Long-term: Extracting the parameter panel code into a well-commented section inside the single `index.html` for better organization (no new files)
- Thematic arc phase rail in sim UI → planned `0.5.0-phase-rail`
- Initial agent count control → planned `0.6.0-run-setup`
- Full-run trends + richer history + agent pin → planned `0.7.0-run-compare`

### Run History, Metrics & Observability (Captured 2026-05-28)

After completing the v0.1 hunger parameter controls and tuning (plain lets + sliders), and through direct observation of simulation behavior (especially with high `groundEatRelief` values), the following became clearly valuable:

- **Run History (Minimal v1)**: Store results of previous runs within the same browser session (longest survival time, final population, etc.) → `0.2.0-run-history` **PR #8**
- Simple way to compare multiple runs side-by-side (e.g. "Run #3 had one agent survive 4m12s") → `0.2.0-run-history` **PR #8**; richer UI → `0.7.0-run-compare` (planned)
- Basic per-run statistics panel (longest-lived agent, average lifetime, starvation deaths, etc.) → `0.3.0-observability` **PR #13**
- Click on an individual agent (dot) to inspect its personal stats (current hunger, food carried, lifetime, possibly future traits like HoardingBias, etc.) → `0.3.0-observability` **PR #13**

This direction emerged from real experimentation rather than being planned upfront. The click-to-inspect idea came right after finishing the v0.1 sliders and spending time observing individual agent behavior.

### UI/UX Polish + Advanced Observability (Captured 2026-05-30)

*Shipped as `0.3.0-observability` · Phase 0 · Survive · **PR #13***

Large focused increment delivering a significantly more usable and insightful simulation experience:

- Live aggregated metrics panel (population, starvation deaths, food biomass, hunger min/max/avg)
- Click-to-inspect individual agents with floating bottom-right inspector card
- Simulation speed controls (1x / 2x / 5x / 10x) using simple multiplier
- Sidebar refactored into lightweight tabs (Controls | Metrics | Trends | History) to prevent clutter
- Current-run time-series collection + simple trend graphs (population, food, average hunger)
- Improved run history summaries
- Food respawn logic changed to keep food appearing while agents are alive (prevents dead environment feel)
- Starvation deaths per run in history list

All changes maintain radical simplicity and single-file constraints.

**Deferred for later (explicitly captured here):**
- Rich generational / multi-run comparison graphs: ability to overlay time-series curves (food evolution, hunger, population) from multiple previous runs side-by-side for parameter tuning and "what if" analysis.
- Persistent or exportable run archives.
- Once reproduction + traits exist: live visualization of trait distribution shifts across generations (histograms, mean/variance tracking over time).
- These become high-value once we have Phase 2 · Evolve because a single long run will contain multiple generations with meaningful evolutionary change.

The 2026-05-30 increment creates the technical foundation (time-series buffers, chart rendering, inspector patterns, tab system) that future generational visualization can build on without starting from scratch.

### Trait Exploration & Alternative Ideas (Captured 2026-05-28)

The current three locked traits (HoardingBias, ExplorationRate, TradeBoldness) were chosen early as a focused starting set. The human is open to refining or expanding the trait space before or during Phase 2.

**Observations from testing**:
- When `groundEatRelief` was set very high (5.0), the population still slowly died off, but one extremely lucky agent survived much longer than everyone else after the rest had died. This created an interesting "sole survivor" dynamic that was fun to watch.

**New trait direction ideas**:
- Social / grouping traits (e.g. a trait that makes agents enjoy staying near bigger/more successful dots — "follow the fat ones" behavior)
- More heterogeneous populations: different starting groups with different trait distributions instead of one uniform population
- Desire to explore a larger trait space overall rather than being locked into only the original three

These ideas should be revisited when designing Phase 1 · Differ and Phase 2 · Evolve.

### Phase 1 – Trade *(superseded 2026-07-02)*

*Original plan. Now: **Phase 3 · Economy** (trade is sub-milestone 3.1).*

- Proximity-based trading between agents
- Simple willingness logic

### Phase 2 – Reproduction + Trait Evolution *(superseded 2026-07-02)*

*Split across **Phase 1 · Differ** (traits, no genetics) and **Phase 2 · Evolve** (reproduction + inheritance).*

- Agents can reproduce when they have surplus food
- Traits are inherited with mutation
- Population turns over across generations
- Begin tracking trait distributions over time

### Phase 3+ – Richer Evolutionary Dynamics *(superseded 2026-07-02)*

*Now largely covered by **Phase 3 · Economy** sub-milestones + ongoing observability polish.*

- More environmental variation
- Additional light mechanics (only if they improve observability of evolution)
- Stronger visualization and statistics for generational change

---

**Explicitly deprioritized for now**: Government, policy, multiple goods introduced all at once, complex production chains without incremental observability, heavy financial systems.

---

## Appended 2026-07-02 — Vision resteer details

### Thematic arc (active)

**Survive → Differ → Evolve → Economy**

### Phase 1 · Differ (scope sketch)

- Per-agent trait values at spawn; run-level distribution controls
- Traits affect survival behavior
- Inspector / Metrics / Trends show trait stats
- No inheritance or mutation yet

### Phase 2 · Evolve (scope sketch)

**Core:** in-run reproduction, inheritance + mutation, generational charts.

**Deferred — Survivor Seed Lab Mode:** on run end, sample traits from survivors + light mutation → seed next Reset. Fast multi-run experiments. Build after in-run reproduction is observable.

### Phase 3 · Economy (sub-milestones, one PR each)

| Sub | Version (planned) | Focus |
|-----|-------------------|-------|
| 3.1 | `3.0.0-trade` | Proximity exchange |
| 3.2 | `3.1.0-storage` | Inventory / hoarding |
| 3.3 | `3.2.0-production` | Farming, conversion |
| 3.4 | `3.3.0-labor` | Workers, employers |
| 3.5 | `3.4.0-capital` | Saving, investing (if warranted) |

**Decision checkpoint** after Phase 2: deepen core, branch repo, or add complex mode.

### 0.5.0-phase-rail — design notes

- Phase rail in `index.html` header; active phase highlighted
- Version badge; no simulation logic changes
