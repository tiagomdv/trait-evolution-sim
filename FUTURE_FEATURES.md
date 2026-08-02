# Future Features & Roadmap — trait-evolution-sim

**Active backlog only.** Open ideas, planned milestones, and deferred-but-still-wanted work.

When something **ships** or is **dismissed**, document it in `IMPLEMENTATION_LOG.md` (and archives/VERSION as needed), then **remove it from this file**. Do not keep “Completed in PR #N” markers here — that history lives in the log.

**Current phase:** 0 · Survive  
**Last shipped (pointer only):** `0.9.2-special` · see `VERSION` + `IMPLEMENTATION_LOG.md`  
**Thematic arc:** Survive → Differ → Evolve → Economy

**How this file is maintained:** see `AGENTS.md` (docs resteer 2026-07-30 — backlog hygiene).  
**Before this resteer:** full prior content frozen at `archive/docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md`  
**Earlier vision resteer snapshot:** `archive/docs/FUTURE_FEATURES-pre-resteer-2026-07-02.md`

### Strategy: thick Phase 0 before Phase 1 · Differ (human 2026-07-30)

**Intent:** Prefer shipping the open **Survive** pile (forage finish + lab tooling + play/story docs) **before** opening Phase 1 · Differ, rather than a minimal “special + memory then traits” cut.

**Why:** Phase 1 will add traits, new knobs, and more inspector/metrics surface. Building **Play + Lab + export + Help/Playbook** first means Differ plugs into a stable “watch one world / measure many worlds / explain knobs” desk — less redesign thrash mid-traits.

**Not a law:** Human can still jump to Differ earlier. This is the **default preference**, not a hard gate list.

**Suggested order (thick path)**

1. **Forage finish** — `0.9.2-special` → `0.9.3-memory` (behavior story complete enough to play)  
2. **Single-run science** — run parameter export logs (+ seed control if needed); metrics schema Lab will reuse  
3. **Lab mode v1** — headless N runs (50/100/200), lock/vary knobs, results table, a few graphs, CSV/JSON export — **cap scope** (no full stats suite / multi-canvas)  
4. **Story layer** — thematic experiment presets + `PLAYBOOK.md` v0 (can draft Playbook anytime in parallel)  
5. **Optional polish** — slide drawers; density gradient / greed only if still wanted (else defer or fold into Phase 1 flavor)  
6. **Close Phase 0** — freeze “Survive lab complete,” then Phase 1 · Differ design  

**Trap to avoid:** Lab scope creep delaying Differ forever. “Before Phase 1” means a **usable Lab v1**, not every graph ever.

---

## Version scheme (reference)

Major version = phase number (`0.x` = Phase 0, `1.x` = Phase 1, …). Codename describes the milestone.

Design artifacts in `design-docs/` use the same nomenclature (e.g. `0.9.0-forage-design.html`). See AGENTS.md.

---

## Phase 0 · Survive — next (open)

| Item | Track | Notes |
|------|-------|--------|
| `0.9.3-memory` (next Track B) | **B** | Last-food memory / good vs bad TTL. |
| Brand header polish (optional Track A) | **A** | Improve title / phase / tagline layout. Options A–D in `design-docs/0.9.2-brand-header-design.html` (recommend Option B phase bar). |
| `0.9.4-vision` (planned — vision reworking) | **A/docs** (+ light A/B tools) | Explicit **agent evolution lab** vision milestone: Help “where this is going,” Playbook v0, phase taglines locked, optional export stub; **not** fake generations. Best-generation-by-tuning = Phase 2 + Lab. See deferred section. |
| Run parameter export logs | **A/B** | Export run knobs + end metrics (JSON/text). Building block for Lab + vision tuning stories. |
| **Lab mode** — headless batch / Monte Carlo (wanted) | **A/B** | In-app Lab (no canvas): N runs, lock/vary, table + graphs + export. See deferred section. |
| Close Phase 0 | — | After thick Phase 0 path feels done (see strategy above), move to Phase 1 · Differ — human can still cut early. |

**Forage design (whole arc):** `design-docs/0.9.0-forage-design.html`  
**Frozen builds:** `archive/index-0.9.0-seek.html` · `archive/index-0.9.1-ui-chrome.html` · `archive/index-0.9.2-special.html`  
**Deferred within 0.9 arc (not yet versioned):** food density gradient; greed/hoarding (Phase 1 flavor unless pulled forward).

**Shipped:** `archive/index-0.9.1-ui-chrome.html` · `archive/index-0.9.2-special.html`  
**Brand design:** `design-docs/0.9.2-brand-header-design.html` (header / phase / tagline options)  
**Special design:** `design-docs/0.9.2-special-design.html`

### Deferred UI (still wanted)

#### Slide left / slide right column drawers

**Status:** deferred (post 0.9.1 chrome if still wanted)

Animate side panels as drawers (`transform: translateX`) instead of hard show/hide.

1. **Overlay drawers** — canvas full-width; panels slide over it (smoother, less reflow).  
2. **Layout + slide** — grid still resizes canvas (like current hide); panel slides while width collapses (harder, can jank).

**Why wait:** Hide ✕ + edge tab + `resizeSimCanvas` is enough for now; 0.9.1 is static chrome first.

#### Thematic experiment presets (story / lab scenarios)

**Status:** idea for later (post 0.9.1) · Track A/B

Beyond Lenient / Balanced / Punishing difficulty numbers, add **thematic presets** that set a whole experiment at once — knobs + movement mode + maybe a short run label — so the human can demo stories without hand-tuning:

- **Random walk baseline** — Random policy + known harsh-or-fair environment; “brownian / undirected walk, no food sense.”  
- **Seek vs chance** — same world twice: Seek vs Random (or one-click flip + recommended settings) to show survival gap.  
- **Survival of the few** — punishing scarcity + Seek; watch a remnant cling on.  
- **Chaotic feast / famine** — extreme spawn vs hunger pairing for dramatic boom-bust.  
- Other named “lab stories” as they emerge in testing.

**Notes:** May share UI with current presets or sit as a second row (“Experiments”). Should not replace simple difficulty ladder. Optionally tag History rows with scenario name. Capture when chrome + Seek feel solid. Pairs with the **Playbook** doc idea below (presets = one-click chapters).

#### Playbook / lab experiments doc (“how to have fun with the sim”)

**Status:** brainstormed · not written yet · docs only (no sim change required to start)

**Idea:** A living project doc of **testing experiments, playing experiments, and fun things to see** — recipes, not feature specs. Working title **`PLAYBOOK.md`** (alternatives: `HOW_TO_PLAY.md`, `LAB_EXPERIMENTS.md`). Prefer **repo root** when created (human-facing), not buried only in design-docs.

**What it is**

- Short **setup → do → watch for → why it’s cool** recipes for the *current* live build  
- Classic A/Bs (Seek vs Random, sense radius, seek strength, preset ladder)  
- Story vignettes (survival of the few, petting zoo, desert, feast, random-walk tragedy)  
- Inspector / History games (pin a survivor, compare History rows)  
- Optional feel-tuning micro-labs and “open questions to try”  
- Links to future features (thematic presets, special agent, memory, export logs) without duplicating the whole roadmap  

**What it is not**

- Not a replacement for in-app **Help** (knob definitions stay in the modal)  
- Not a second `FUTURE_FEATURES` (build backlog stays there)  
- Not required for every ship; append when a new mechanic makes a new fun recipe  

**Tone / process (open)**

- Fun-first playbook vs lab-notebook voice (or both: “Play” + “Lab” sections)  
- Living file you can scribble into after a good session  
- Later: thematic presets and export logs can formalize recipes into one-click or pasteable experiments  

**When to write v0:** Anytime after `0.9.1-ui-chrome` — even a short first page of Seek-era recipes is enough. No need to wait for 0.9.2.

#### Vision reworking (`0.9.4-vision` — agent evolution lab)

**Status:** planned idea (human 2026-07-30) · not designed as full PR yet  
**Track:** mostly **A / docs**; may include light export hooks

**Intent:** Make the long product story legible and actionable *without* shipping fake Phase 2 generations.

**Product story**

- Identity: **agent evolution lab** (spatial agents; tune who lasts).  
- Arc: Survive → Differ → Evolve → Economy (phase-aware taglines; header polish per brand design doc).  
- Later dream: lab workflow to **develop the best survival generation by tuning** — real only when **reproduction / generations** (Phase 2) + multi-run **Lab mode** exist.

**In scope for a vision milestone (suggested)**

- Help section: “Where this is going” (honest: Phase 0 = survival only).  
- `PLAYBOOK.md` v0: survival tuning recipes (Seek A/B, special overrides, presets).  
- Confirm phase tagline bank + optional implement brand **Option B**.  
- Optional: single-run **export** (knobs + end metrics) so tuning can leave the browser.  
- README north-star aligned with in-app wording.

**Out of scope for that milestone**

- In-run inheritance / mutation / generational UI as if Phase 2 were done.  
- Full Lab Monte Carlo (separate larger slice).  
- Economy / trade.

**Relations:** Playbook · export · Lab mode · brand-header design · thick Phase 0 strategy.

#### Lab mode — headless batch / Monte Carlo (no canvas)

**Status:** brainstormed · **human product lock (2026-07-30)** · not designed/implemented  
**Track:** A/B (UI + runner + charts mostly A; pure tick loop / seed hooks may touch B lightly)

**Product picture (locked intent)**

- **No visual world while batching** — no canvas, no watching agents. Pure experiment desk.  
- Run **N trials** in one go (e.g. **50 / 100 / 200** or custom).  
- User **locks** some parameters (held fixed across the batch) and **varies** others (levels, ranges, or A/B sets — e.g. Seek vs Random, preset ladder, hunger sweep).  
- Engine runs trials **headless** (tick loop only; skip all draw). Sequential is fine; light parallel workers optional for speed later.  
- After (or as) runs complete: **results table** + **cool graphs** (distributions, group compares, simple sweep plots) + **export** CSV/JSON.  
- Interactive **Play** mode (today’s canvas sim) stays separate; Lab is a mode/panel you enter for campaigns of trials.

**Questions this unlocks**

- Seek vs Random: distribution of survivors / time-to-extinction over N seeds  
- Do Lenient / Balanced / Punishing rank under Seek after 50–100–200 trials?  
- Where does survival “fall off a cliff” if we vary one unlocked knob?  
- High-variance (luck) vs stable configs  
- Data-backed preset retunes and Playbook claims  

**Lock / vary (config UX sketch)**

- Each knob: **Lock** (single value) vs **Vary** (list of levels, min/max/step, or categorical e.g. policy).  
- Batch = Cartesian product of vary-dimensions × N seeds (or N per cell) — need caps so 200 × huge grids don’t freeze the tab (warn / max cells).  
- Optional: named experiment (“Seek vs Random @ Balanced”) saved for re-run.  

**What a single trial record might include**

- Locked + vary cell snapshot, seed  
- Outcomes: duration, final pop, time-to-50%-dead (optional), avg hunger / avg carried food, deaths, peaks  
- Grouping keys for graphs: policy, preset, sweep value  

**Graphs (v1 → later)**

- v1: histogram / box-ish summary of final pop or duration; bar compare means (Seek vs Random); progress while running  
- Later: survival curves, 1D sweep line + error band, light 2D heatmap, overlay groups  

**Build arc (suggested)**

1. Shared **metrics schema** (+ export logs from Play if useful).  
2. **Headless run-one(config, seed) → result** (no canvas path).  
3. **Lab UI**: N, lock/vary matrix, Start / Cancel, progress.  
4. **Results table + export**.  
5. **Graphs** (group compare + one distribution).  
6. Richer sweeps / more chart types; parallel workers only if needed.  

**What it is not**

- Watching multi-world canvases (explicitly out of scope for this Lab)  
- Replacing Play mode / Playbook hands-on fun  
- Full stats package day one (mean/median/p10–p90 + a few graphs first)  
- Offline-only product (in-app Lab is the goal; CLI only if scale demands)  

**Relations**

- **Play mode** = canvas, single run, feel  
- **Export logs** = optional bridge / same row shape as one Lab trial  
- **Playbook** = recipes Lab can automate (“run this 100×”)  
- **Thematic presets** = one-click lock/vary templates  

**When to pick up:** Design when human prioritizes lab tooling; default mechanic queue still `0.9.2-special` unless reordered. Version codename TBD (e.g. `0.x.y-lab-batch` when scoped).

---

## Phase 1 · Differ (open sketch)

- Per-agent trait values at spawn; run-level distribution controls  
- Traits affect survival behavior (including optional modulation of hunger parameters once traits exist)  
- Inspector / Metrics / Trends show trait stats  
- **No** inheritance or mutation yet  

### Trait candidates (not locked)

Early set: **HoardingBias**, **ExplorationRate**, **TradeBoldness**.

Also discussed: Patience / FutureOrientation, SocialAffinity, HarvestEfficiency, RiskSensitivity, Reciprocity; social/grouping (“follow successful agents”); heterogeneous starting groups; larger trait space overall.

Finalize trait set when Phase 1 design starts.

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
