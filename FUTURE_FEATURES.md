# Future Features & Roadmap — trait-evolution-sim

**Active backlog only.** When something ships or is dismissed, put it in `IMPLEMENTATION_LOG.md` and **remove it here**.

**Phase:** 0 · Survive · live `0.9.6-params` (see `VERSION`)  
**Arc:** Survive → Differ → Evolve → Economy  
**Hygiene:** `AGENTS.md`. Older snapshots: `archive/docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md`, `…-pre-resteer-2026-07-02.md`, `…-pre-0.9.6-params-2026-08-13.md`.

**Thick Phase 0 (preference, not a law):** usable Play + Lab + export before Differ. Lab v1 and `0.9.6-params` (island / Seek / Agent + masters) are **frozen**. Do not grow Lab graphs forever. Human can open Differ any time.

---

## Phase 0 · Survive — open

| Next | Track | Notes |
|------|-------|--------|
| Thematic experiment presets | A/B | Named stories (Seek vs chance, remnant, feast/famine). Not a replacement for L/B/P. |
| `PLAYBOOK.md` v0 | docs | Later. Harvest **Lab notes** below — don’t invent recipes. |
| Optional Lab polish | A | Graphs, batch history, lock/vary grids. |
| World multi-group from Lab | B | Visual A/B on canvas. Special stays World-only. |
| Close Phase 0 | — | Human freeze → Phase 1 · Differ design. |

**Parked (not queued):** last-food memory · food density gradient · greed/hoarding (Differ unless pulled forward) · column slide drawers.

**Shipped (pointer):** seek · chrome · special · vision · run-logs · lab · **`0.9.6-params`**.  
**Design:** `design-docs/0.9.0-forage-design.html` · `0.9.4-export-run-logs-design.html` · `0.9.5-lab-design.html` · `0.9.2-brand-header-design.html` · `0.9.2-special-design.html`.  
**Archives:** `archive/index-0.9.0-seek.html` … `archive/index-0.9.6-params.html`.

### Version scheme

Major = phase (`0.x` Survive, `1.x` Differ). Codenames match `design-docs/` (e.g. `0.9.0-forage-design.html`).

### Parked detail

**Last-food memory** (was `0.9.4-memory`) — not next. Bias toward last meal / away from empty spots, TTL. Revisit if agents feel blind outside Sight, or Differ needs an ExplorationRate hook.

**Column drawers** — animate hide/show. Hide ✕ + edge tab is enough.

**Thematic presets (ideas):** Random walk baseline · Seek vs chance · Survival of the few · Chaotic feast/famine. Optional History tag. Pair with Playbook chapters.

**Playbook** — `PLAYBOOK.md` when that version opens. Recipes: setup → do → watch for → why cool. Not Help, not a second roadmap.

### Lab notes — harvest for Playbook later

Living scratch. After a good export, append short findings. Not a shipped Playbook.

**Method**

- Same stop + same max duration when comparing packs.  
- Rank difficulty by **alive on a short clock** (75–90s). Long-run `avgFood` is tycoon-biased.  
- Special is **relative to the world**.  
- Lab JSON: `{ version, mode: "lab", experiment, runs, aggregates }`.  
- World export: knobs = end-of-run; Export last ≠ selected row.

**Knob names (`0.9.6-params`):** Sight · Hunger pull · Seek push · Drift · Max speed · Hunger rate · Gluttony · Efficiency · Eat threshold · Food spawn · Initial agents. Policy Seek / Random. Island presets = Food spawn + N only (higher N = harder).

**2026-08-06** — Random L/B/P alive-first freeze (old packs + ground fill). Pet special in Random desert. Accel > sense-alone; high wander often hurt.

**2026-08-13** — `0.9.6-params` freeze (no ground fill; catch = bag +1). Seek L/B/P @ 90s: remnant ranks L > B > P (~8 / 4 / 0 alive). Seek master 0.2→0.8: monotone, most gain by 0.5, high end flat. Agent master steep: easy ~13 alive, mid ~4, hard ~wipe on Balanced. Confirm `initialAgents` in export (Batch fallback must not overwrite N).

**Playbook candidates:** L/B/P @ 75–90s · Seek vs Random same island · Seek master 0.2/0.5/0.8 · Agent master 0.2/0.5/0.8 · pet special in Random.

**Still interesting:** median duration + extinction % on Lab cards · dead special final hunger/food · slider range polish.

### Optional Lab polish

Graphs · batch history · Cartesian lock/vary · World multi-group colors · more Lab Help · parallel workers if batches hurt.

---

## Phase 1 · Differ (open sketch)

- Per-agent trait values at spawn; run-level distribution controls  
- Traits affect survival behavior (including optional modulation of hunger parameters once traits exist)  
- Inspector / Metrics / Trends show trait stats  
- **No** inheritance or mutation yet  

### Trait candidates (not locked)

Live eat/move knobs already exist (Gluttony, Efficiency, Drift, …). Differ can attach **variance** to those rather than a second name pile. Early poetic set: **HoardingBias**, **ExplorationRate**, **TradeBoldness** (TradeBoldness dormant until Economy).

Also discussed: Patience / FutureOrientation, SocialAffinity, HarvestEfficiency, RiskSensitivity, Reciprocity; follow-successful-agents; heterogeneous starting groups.

Finalize the set when Phase 1 design starts.

---

## Phase 2 · Evolve (open sketch)

**Core:** in-run reproduction, inheritance + mutation, generational charts / trait distribution over time.

**Deferred (still wanted after core Evolve):**

- **Survivor Seed Lab Mode** — on run end, sample traits from survivors + light mutation → seed next Reset (fast multi-run experiments). Build after in-run reproduction is observable.  
- Live trait-distribution visualization (histograms, mean/variance over generations) — high value once multi-generation runs exist.

---

## Phase 3 · Economy (open sketch)

Trade is the entry point (not a standalone phase). One PR each when we get here:

| Sub | Version (planned) | Focus |
|-----|-------------------|-------|
| 3.1 | `3.0.0-trade` | Proximity exchange |
| 3.2 | `3.1.0-storage` | Inventory / hoarding |
| 3.3 | `3.2.0-production` | Farming, conversion |
| 3.4 | `3.3.0-labor` | Workers, employers |
| 3.5 | `3.4.0-capital` | Saving, investing (if warranted) |

**Checkpoint after Phase 2:** deepen core, branch repo, or add a complex mode.

---

## Observability / tooling (open, lower priority)

- Multi-run **overlay** trend graphs (compare curves across session runs for tuning). Session history + full-run trends already exist; this is the richer comparison layer.  
- Persistent or **exportable** run archives (beyond in-browser session memory).  
- Light code organization inside single `index.html` (commented sections only; no new source files without approval).

---

## Project goal (one line)

Clean, observable 2D agent simulation: watch what helps agents survive become what helps them thrive — one resource (Food) first, then traits, generations, then economy.
