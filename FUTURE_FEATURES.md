# Future Features & Roadmap — trait-evolution-sim

**Active backlog only.** Open ideas, planned milestones, and deferred-but-still-wanted work.

When something **ships** or is **dismissed**, document it in `IMPLEMENTATION_LOG.md` (and archives/VERSION as needed), then **remove it from this file**. Do not keep “Completed in PR #N” markers here — that history lives in the log.

**Current phase:** 0 · Survive  
**Last shipped (pointer only):** `0.8.4-tight-layout` · see `VERSION` + `IMPLEMENTATION_LOG.md`  
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
| `0.9.0-forage` (planned) | **B** | Environment-aware movement / always-seek food. First real post-layout mechanics candidate. |
| Close Phase 0 | — | After forage (and any remaining observability you care about), move to Phase 1 · Differ — or more Phase 0 polish if needed. |

### Deferred UI (still wanted)

#### Slide left / slide right column drawers

**Status:** deferred (not in 0.8.4)

Animate side panels as drawers (`transform: translateX`) instead of hard show/hide.

1. **Overlay drawers** — canvas full-width; panels slide over it (smoother, less reflow).  
2. **Layout + slide** — grid still resizes canvas (like current hide); panel slides while width collapses (harder, can jank).

**Why wait:** Hide ✕ + edge tab + `resizeSimCanvas` is enough; motion is polish, not blocking forage or Phase 1.  
**When:** After forage/traits if chrome still feels abrupt; pure Track A.

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
