# Future Features & Roadmap — trait-evolution-sim

**Active backlog only.** Open ideas, planned milestones, and deferred-but-still-wanted work.

When something **ships** or is **dismissed**, document it in `IMPLEMENTATION_LOG.md` (and archives/VERSION as needed), then **remove it from this file**. Do not keep “Completed in PR #N” markers here — that history lives in the log.

**Current phase:** 0 · Survive  
**Last shipped (pointer only):** `0.9.6-params` · see `VERSION` + `IMPLEMENTATION_LOG.md`  
**Thematic arc:** Survive → Differ → Evolve → Economy

**How this file is maintained:** see `AGENTS.md` (docs resteer 2026-07-30 — backlog hygiene).  
**Before this resteer:** full prior content frozen at `archive/docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md`  
**Earlier vision resteer snapshot:** `archive/docs/FUTURE_FEATURES-pre-resteer-2026-07-02.md`

### Strategy: thick Phase 0 before Phase 1 · Differ (human 2026-07-30; memory deprioritized 2026-08-06)

**Intent:** Prefer shipping the open **Survive** pile (lab tooling + play/story docs) **before** opening Phase 1 · Differ. Forage core (Seek + special) is treated as **good enough to play**; last-food memory is **not** required to close the forage story.

**Why:** Phase 1 will add traits, new knobs, and more inspector/metrics surface. Building **Play + Lab + export + Help/Playbook** first means Differ plugs into a stable “watch one world / measure many worlds / explain knobs” desk — less redesign thrash mid-traits.

**Not a law:** Human can still jump to Differ earlier. This is the **default preference**, not a hard gate list.

**Suggested order (thick path)**

1. ~~**Single-run science** — run parameter export logs~~ **shipped** as `0.9.4-run-logs`  
2. ~~**Lab mode v1** — headless multi-setup batches~~ **shipped** as `0.9.5-lab` (1–5 setups, cards, JSON export; **no graphs v1**; special stays World-only)  
3. **Story layer (later version)** — thematic experiment presets + `PLAYBOOK.md` v0 — harvest notes in **Lab notes** below; do **not** create Playbook until that milestone  
4. **Optional Lab polish** — graphs, batch history, lock/vary Cartesian grids, World multi-group spawn from Lab setups  
5. **Close Phase 0** — freeze “Survive lab complete,” then Phase 1 · Differ design  

**Maybe later (not queued):** last-food **memory** — only if feel or Phase 1 traits (e.g. ExplorationRate) make it earn its place. See deferred mechanics below.

**Trap to avoid:** Lab scope creep delaying Differ forever. “Before Phase 1” means a **usable Lab v1**, not every graph ever.

---

## Version scheme (reference)

Major version = phase number (`0.x` = Phase 0, `1.x` = Phase 1, …). Codename describes the milestone.

Design artifacts in `design-docs/` use the same nomenclature (e.g. `0.9.0-forage-design.html`). See AGENTS.md.

---

## Phase 0 · Survive — next (open)

| Item | Track | Notes |
|------|-------|--------|
| Lab polish — graphs / batch history / lock-vary grids | **A** | Optional. Core Lab shipped in `0.9.5-lab` (cards + JSON only). |
| World multi-group from Lab setups | **B** | Optional design Phase 4 — visual A/B on canvas; Special stays World-only. |
| Thematic experiment presets | **A/B** | Named story scenarios. See deferred UI + **Lab notes** for candidates. |
| `PLAYBOOK.md` v0 | docs | **Later version** — not now. Harvest material lives in **Lab notes** below. |
| Close Phase 0 | — | After thick Phase 0 path feels done, move to Phase 1 · Differ — human can still cut early. |

**Forage design (whole arc):** `design-docs/0.9.0-forage-design.html`  
**Run logs design:** `design-docs/0.9.4-export-run-logs-design.html`  
**Lab design:** `design-docs/0.9.5-lab-design.html`  
**Frozen builds:** `archive/index-0.9.0-seek.html` · … · `archive/index-0.9.5-lab.html`  
**Deferred mechanics (not queued):** last-food **memory** (good/bad TTL) — human 2026-08-06: skip for now; revisit only if it makes sense later; food density gradient; greed/hoarding (Phase 1 flavor unless pulled forward).

**Shipped:** seek · ui-chrome · special · vision · run-logs · lab · params · **masters** (`0.9.6-params`)  
**Next in Phase 0:** Lab-tune Seek/Agent master curves + island L/B/P (alive @ short clock) after catch no longer grants hunger.  
**Brand design:** `design-docs/0.9.2-brand-header-design.html`  
**Special design:** `design-docs/0.9.2-special-design.html`

### Deferred mechanics (maybe later)

#### Last-food memory (was `0.9.4-memory`)

**Status:** **not next** · human deprioritized 2026-08-06 · keep as optional idea only  
**Track:** B if ever picked up  

**Idea (forage design stretch):** When nothing is in sense radius, bias toward a remembered last meal (and maybe avoid “bad” empty spots); memories expire via TTL. Bridge to Phase 1 **ExplorationRate**.

**Why parked:** Seek + special already tell a solid Survive forage story. Extra agent state and edge cases without clear payoff right now.

**Revisit if:** agents feel “blind drunk” when food leaves radius and that hurts play; or Phase 1 traits need a memory hook.

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

**Status:** **deferred to a later version** · not authored yet (human 2026-08-06: no Playbook file while closing `0.9.4-run-logs`)  
**Working title:** `PLAYBOOK.md` at repo root when that version ships  

**Idea (unchanged):** Human-facing recipes (setup → do → watch for → why cool). Not a second roadmap; not a substitute for in-app Help.

**Until then:** stash findings under **Lab notes (from run logs)** in this file. When Playbook version opens, **copy/harvest** those notes into `PLAYBOOK.md` — do not invent recipes only from theory.

#### Lab notes (from run logs) — harvest for Playbook / Lab / presets later

**Status:** living scratch · append after good export+analysis sessions · **not** a shipped Playbook  
**How notes form:** Play → several finished runs → **Run logs… → Copy/Export all** → analyze (e.g. Grok) → write short findings here. See README “Run logs → analysis loop.”

**Process / method lessons**

- Export JSON is enough for multi-run comparison; UI table + detail for eyeballing.  
- Prefer **same stop rule + same max duration** when comparing packages.  
- Special upgrades are **relative to the world**: Random crowd ≠ all-Seek crowd.  
- Knob roles: **sense** = see food; **seek strength** = hunger→pull; **seek accel** = shove to target; **wander** = noise (all policies); **max speed** = cap.  
- Lab: seeded headless trials; envelope `{ version, mode: "lab", experiment, runs, aggregates }`.  
- World export quirks: knobs = end-of-run snapshot; Export last ≠ selected row; Clear does not reset run numbers.

**Findings · session 2026-08-06 (World special ladders)**

*1. Pet special in a random desert* — Random world + Seek special → crowd wipe, special often fat remnant.  
*2. Special ladder in all-Seek* — Accel was the clearest single lever; sense-only weak; high wander often hurt.  
*3. Quiet seeker* — Wander 0 beat high wander in a snappy Seek field.

**Findings · session 2026-08-06 (Lab + difficulty packs · freeze)**

*4. Alive-first ladder under Random (shipped packs)*  
Shared `getPresetEnv` for World + Lab. Under **Random · Max-time ~75s · N=30 · 50 agents**, Balanced lands ~**17 alive** (hungry, empty inventory); under **~295s**, ~**12–13 alive** calmer. Hard gauntlet packs (higher hunger/sparser food) collapse to **~0–1 alive** with bimodal wipe-vs-tycoon — mean duration can look mid while avgAlive stays ~0.  
**Product read:** Lenient = large crowd; Balanced = mid remnant after early cull; Punishing = fast wipe. Rank difficulty by **alive/dead on a fixed short clock**; treat long-run **avgFood** as tycoon-biased.  
**Default Lab setups:** 3× Random · Lenient / Balanced / Punishing.

*5. Stop rules*  
All dead + 600s locked safety prevents hangs. Max time (editable) for pop ranking. Chunked headless so Cancel works mid-trial.

**Recipe / Lab candidates to formalize later (Playbook)**

- Default Random L/B/P ladder at 75s and at 295s (alive scale).  
- Same ladder under Seek (expect larger remnants).  
- Seek vs Random whole-world A/B, same preset, N seeds.  
- Special vs world Random (pet special).  
- Accel / wander sweeps (World Special…).  

**Open questions (still interesting)**

- Lab aggregate **median duration + extinction %** on cards (bimodality visible without export).  
- Dead special `finalFood`/`finalHunger` at death.  
- Slider range polish (hunger/spawn playable band) — optional UX.

#### Vision reworking (`0.9.3-vision` — shipped framing)

**Status:** **shipped** as `0.9.3-vision` (N4 header + Vision modal + path on canvas). Export shipped in `0.9.4-run-logs`. Lab desk shipped in `0.9.5-lab`. Playbook deferred.  
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

#### Lab polish (after `0.9.5-lab` core)

**Status:** optional follow-ups · core Lab shipped as `0.9.5-lab`  
**Track:** mostly A

Still open if wanted later:

- Graphs (histograms, bar compare means, survival curves)  
- Batch history (keep more than last batch)  
- Cartesian lock/vary matrix (vs today’s explicit 1–5 setups)  
- World multi-group spawn colored by Lab setup  
- Help section for Lab workflow  
- Parallel workers if batch size becomes painful  

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
