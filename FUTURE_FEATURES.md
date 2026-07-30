# Future Features & Roadmap — trait-evolution-sim

**Active backlog only.** Open ideas, planned milestones, and deferred-but-still-wanted work.

When something **ships** or is **dismissed**, document it in `IMPLEMENTATION_LOG.md` (and archives/VERSION as needed), then **remove it from this file**. Do not keep “Completed in PR #N” markers here — that history lives in the log.

**Current phase:** 0 · Survive  
**Last shipped (pointer only):** `0.9.1-ui-chrome` · see `VERSION` + `IMPLEMENTATION_LOG.md`  
**Thematic arc:** Survive → Differ → Evolve → Economy

**How this file is maintained:** see `AGENTS.md` (docs resteer 2026-07-30 — backlog hygiene).  
**Before this resteer:** full prior content frozen at `archive/docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md`  
**Earlier vision resteer snapshot:** `archive/docs/FUTURE_FEATURES-pre-resteer-2026-07-02.md`

---

## Version scheme (reference)

Major version = phase number (`0.x` = Phase 0, `1.x` = Phase 1, …). Codename describes the milestone.

Design artifacts in `design-docs/` use the same nomenclature (e.g. `0.9.0-forage-design.html`). See AGENTS.md.

---

## Phase 0 · Survive — next (open)

| Item | Track | Notes |
|------|-------|--------|
| `0.9.2-special` (planned) | **B** | One marked special agent for easy pin/compare. |
| `0.9.3-memory` (planned) | **B** | Last-food memory / good vs bad TTL. |
| Run parameter export logs | **A/B** | Export run knobs + end metrics (JSON/text) so human can paste into another session for analysis. Not required for next chrome slice. |
| Close Phase 0 | — | After 0.9 slices feel done, move to Phase 1 · Differ — or more polish if needed. |

**Forage design (whole arc):** `design-docs/0.9.0-forage-design.html`  
**Frozen builds:** `archive/index-0.9.0-seek.html` (seek mechanics) · `archive/index-0.9.1-ui-chrome.html` (chrome + Help)  
**Deferred within 0.9 arc (not yet versioned):** food density gradient; greed/hoarding (Phase 1 flavor unless pulled forward).

**Shipped chrome freeze:** `archive/index-0.9.1-ui-chrome.html` (was 0.9.1 checklist — history in IMPLEMENTATION_LOG).


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

**Notes:** May share UI with current presets or sit as a second row (“Experiments”). Should not replace simple difficulty ladder. Optionally tag History rows with scenario name. Capture when chrome + Seek feel solid.

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
