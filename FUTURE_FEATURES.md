# Future Features & Roadmap — trait-evolution-sim

**Active backlog only.** When something ships or is dismissed, put it in `IMPLEMENTATION_LOG.md` and **remove it here**.

**Phase:** **1 · Differ** (open) · live `1.0.0-differ`  
**Arc:** Survive → Differ → Evolve → Economy  
**Hygiene:** `AGENTS.md`. Older snapshots: `archive/docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md`, `…-pre-resteer-2026-07-02.md`, `…-pre-0.9.6-params-2026-08-13.md`.

**Phase 0 · Survive closed** (human 2026-08-13): Play + Lab + export + `0.9.6-params` desk frozen. Survive leftovers below are **not a gate**.

**Phase finish files** (repo root, frozen `index.html` copies): Survive = `phase-0-survive-finished.html`. Later: `phase-1-differ-finished.html`, etc. Also `archive/index-0.9.6-params.html`.

---

## Phase 0 · Survive — leftover (optional)

Not required to close Survive. Any of these can wait until Differ / Evolve / whenever they hurt.

| Item | Track | When | Notes |
|------|-------|------|--------|
| Thematic experiment presets | A/B | 0 or later | Named stories (Seek vs chance, remnant, feast/famine). Not a replacement for L/B/P. |
| `PLAYBOOK.md` v0 | docs | later | Harvest **Lab notes** — don’t invent recipes. |
| Optional Lab polish | A | 0 or later | Graphs, batch history, lock/vary grids. |
| World multi-group from Lab | B | later | Visual A/B on canvas. Special stays World-only. |

**Parked (not queued):** last-food memory · food density gradient · greed/hoarding (Differ unless pulled forward) · column slide drawers.

**From 0.9.5-lab review (2026-08-13)** — not blocking `0.9.6-params`. Do **not** revive multi-size pellets / nibble-until-empty (we froze catch = +1, size 1).

| Item | Track | Worth | Notes |
|------|-------|--------|--------|
| Fair eat (random winner in range) | **B** | Yes, before Differ | First agent in the array still monopolizes a pellet. Lab: use `state.rng`. |
| Pin World size to Lab 800×600 (or pass canvas size into headless) | B | If Lab must match World | Sense is pixels; Lab is not a Monte Carlo of the visible field. |
| Seeded World RNG + seed in export | B | Replay / Special stories | World is `Math.random()`; Lab already records seeds. |
| Drop cancelled Lab trials from aggregates | A | Cheap Lab polish | Cancel mid-batch pulls avgAlive / duration down. |
| Shared `stepWorld` + a few replay tests | B | Before Differ | `Agent.update` vs `headlessStep` can drift. |
| Persist history / JSON import | A | Later | Export is enough. Import needs allowlist + `escapeHtml`. |

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

**2026-08-13 · Differ screen (Seek + Balanced + Max time 90s + 30 seeds).** One-knob slider ends + hunger **dose**. Control remnant ~4.2–4.7. **Hunger rate** continuous + cliff (0.034→~48 alive, 0.049→6.6, 0.062→4.4, 0.084→1.5; slider 0.01=60 / 0.15=wipe). **Efficiency** 0.3=wipe ~31s, 3.0→~12 alive (need mid-band dose). **Gluttony** 0.3 vs 2.0 ≈ control (relief per bag food = Efficiency only). **Hunt off-switches:** pull 0 (−3.5, 60% wipe), push 0.05 (−3.6, 47% wipe), speed 0.5 (−4.3, 93% wipe). Sight 40 −2; high sight/pull/push +0.5–1. Speed 4 **hurts** (−1.2, fat remnant). Drift on Seek small (0 → +0.8, 1.5 → −0.5). Uniform crowds ≠ mixed spawn.

**2026-08-13 · Efficiency dose** (master band, same protocol). 0.80 = **100% wipe ~41s**. Then monotone: 1.20 → 1.9 · **1.60 → 4.2** · 2.00 → 6.6 · 2.40 → 8.2 (8–15 at slider 3.0 earlier). Working spawn band **1.2–2.4** (mean 1.6). Do not include 0.8 in Differ mix — that is Agent-master “hard,” and it is already a corpse factory.

**2026-08-13 · Eat threshold dose.** 5 / 8 / 11 / 19 / 28 → alive 4.3 / 4.7 / 4.5 / 4.5 / 4.4 (noise). Survivor hunger and bag food **rise** with threshold (wait longer to nibble). Gluttony-class null for remnant.

**2026-08-13 · Max speed mid-band.** 1.2 → 3.1 alive; 1.6–3.0 → 4.2 / 4.6 / 4.6 / 4.8 (flat). With 0.5 wipe + 4.0 = 3.2: inverted U. Agent-master 1.6–2.4 is noise. Freeze 2.0.

**Playbook candidates:** L/B/P @ 75–90s · Seek vs Random same island · Seek master 0.2/0.5/0.8 · Agent master 0.2/0.5/0.8 · pet special in Random.

**Still interesting:** median duration + extinction % on Lab cards · dead special final hunger/food · slider range polish · **trait-band Lab** (see Phase 1).

### Optional Lab polish

Graphs · batch history · lock/vary grids · World multi-group colors · more Lab Help · parallel workers · exclude cancelled trials from aggregates.

---

## Phase 1 · Differ (brainstorm · human closed Survive 2026-08-13)

**Job:** same island, agents **differ at spawn**. Who lasts depends on **who they are**. No babies, no inheritance, no mutation (Evolve).

**Rule:** no extra Crowd shelf. Island = weather. Policy / stop / N = experiment. Traits are **not** a second vocabulary next to every slider.

`0.9.6-params` only **organized** Survive knobs. It did **not** create Differ traits. First Differ work is **choose the trait set**, then implement mix + roster.

### Two ways to make traits (brainstorm)

**A — Merge several parameters into one trait**  
One number at spawn writes 2–3 knobs via a curve (like today’s masters).

- *Engine:* tick loop can stay on the same knobs (`drift`, `hungerPull`, …). At spawn (or Reset), `trait → knobs`. No new physics if the curve only sets existing fields.  
- *Does* change the engine if the trait is a new mix law (e.g. one “hunt” that is not the current Seek-master path).  
- *Cost:* Lab/roster can’t tell *which* hidden knob saved them. We already rejected mystery composites (don’t fuse Gluttony + Efficiency).

**B — Clean up low-impact knobs, then 1:1 trait ↔ remaining knob (preferred start)**  
Freeze or hide parameters that barely moved remnant in Lab. Each **live** trait is exactly one remaining Agent/Seek field, with mean + spread (or two groups).

- *Engine:* almost no new physics. At spawn, draw `agent.efficiency` etc.; `p(agent, key)` already supports per-body values (Special). Differ = draw many bodies, not one override.  
- *Masters* stay as **mean shortcuts**, not traits.  
- *Then* invent new traits (social, selectivity, hoarding) only after 1:1 on the high-impact set is readable.

**Human lean (this session):** do **B first** — prune, then 1:1 on what matters — before new invented traits.

### What actually hits remnant (Lab 2026-08-13 · keep · first screen)

| Impact | Knob | 1:1 trait? |
|--------|------|------------|
| **High (dose)** | Hunger rate | Yes — metabolism / burn. Band **~0.049–0.084**. |
| **High (dose)** | Efficiency | Yes — eat trait. Band **1.2–2.4** (0.80 wipes). |
| **Off switch** | Hunger pull 0 · Seek push 0.05 · Max speed 0.5 | Not three traits. One **hunt lock** `t` (merge A) or freeze hunt “on.” |
| **Tax** | Sight 40 | Don’t 1:1; fold into hunt `t` or freeze 180. |
| **Small / flipped** | Drift on Seek · high sight/pull/push · speed 4 hurts | Drift only if explore flavor; not the old “high impact” guess. |
| **None (remnant)** | Gluttony 0.3 vs 2.0 | **No** — same as control. Meal size ≠ remnant. |
| **Medium** | Food spawn + Initial agents | **No** — island, same for all |
| **Trigger** | Eat threshold | **Tested** — remnant flat; bags/hunger rise. Hoard timing later. |
| **Switch** | Policy Seek / Random | Experiment, not a trait |

**Do not 1:1:** Food spawn, N, stop, masters, TradeBoldness (no trade), Gluttony (remnant).

### v1 set (working · lock after band-tuning)

1. **Hunger rate** (burn)  
2. **Efficiency**  
3. **Hunt lock** (one `t` → sight / pull / push; include the off region) — *or* skip and freeze Seek mid  
Optional: **Drift** if we want explore after bands are tight.

Hide or freeze the rest at Balanced defaults (still in Parameters for power users / Special).

### Later — thorough trait-band Lab (do before locking Differ numbers)

First screen found **which** knobs move remnant. It did **not** lock the **readable spawn bands**. Do this in-app (1 control + 4 doses, Seek + Balanced + 90s + 30 seeds) before `1.0.0-traits` mix defaults.

| Track | When | What |
|-------|------|------|
| B / Lab | **Done 2026-08-13** | **Efficiency dose** 0.80 / 1.20 / 1.60 / 2.00 / 2.40. Band **1.2–2.4** (mean 1.6). 0.80 wipes. |
| B / Lab | Before Differ ship | **Hunger** refine if needed: points around the cliff (0.038–0.055) so spawn spread does not dump half the crowd onto the 48-alive plateau. |
| B / Lab | **Done 2026-08-13** | **Eat threshold** 5 / 8 / 11 / 19 / 28. Remnant **flat ~4.3–4.7**. High T → hungrier + fatter bags (28: H 32, food 16). Not a v1 remnant trait; hoard timing later. |
| B / Lab | **Done 2026-08-13** | **Max speed** 1.2 / 1.6 / 2.0 / 2.4 / 3.0. **1.6–3.0 flat ~4.2–4.8**. 1.2 tax (−1.5). Prior: 0.5 wipe, 4.0 hurts (3.2). Freeze body **2.0**; not a v1 trait. |
| B / Lab | Optional | **Hunt `t` curve** — 5 levels of a proposed merge (must include pull≈0 or push floor). Rank remnant vs today’s Seek master 0.2–0.8. |
| B / Lab | After 1:1 bands | **Mixed spawn** — two groups in one world (Lab setups can’t yet; World Special or a later mix). Uniform 0.034 vs 0.084 ≠ half-and-half on one island. |
| B / Lab | If Random Differ | Repeat Drift + hunt-off under **Random**. Drift was small on Seek only. |

**Done enough to stop:** each live trait has a min/max where remnant still has a slope (not 60 vs 0, not ±0.5 noise), written here + Lab notes. Then lock mix means/spreads.

**Method (same as this session):** one change per card; rank **alive** not `avgFood`; note wipes + duration; don’t treat slider floor/ceiling as the trait range.

### Later — impact curves + mixed-edge (viz + method)

Tonight’s tables in the README are the first “curves.” A real viz (Lab sparklines and/or a small `design-docs/` chart page from exports) comes after we decide **what the x-axis is allowed to claim**.

**Balanced-only is enough to pick the v1 remnant set.** Control was rock-steady (~4.5). That island is the default Differ weather. Do **not** re-dose every knob on L and P before locking Hunger / Efficiency / hunt.

**When to leave Balanced**

| Check | Why | Cost |
|-------|-----|------|
| **Punishing once** for Hunger + Efficiency only | P remnant was ~0 at mid knobs. A “high impact” knob might be the only thing that *creates* a remnant — rank could **flip** (efficiency matters more when the island is cruel). Or everything stays dead and the curve is useless. One 5-card dose each. |
| **Lenient once** for the same two | L ~8 alive. Cliffs may flatten (0.034 plateau gets even bigger). Confirms we didn’t pick a band that only works on B. |
| **Not** full L×B×P × every knob | 3× the night we already ran. Sight/pull/push/gluttony/eat won’t change their story enough to pay. |
| **Random** only if Differ allows Random crowds | Drift / hunt-off were Seek-specific. |

Viz v1: one panel per knob, x = parameter, y = **mean alive ±** (min/max or sd), Balanced as the solid line. Overlay L/P only for Hunger + Efficiency if those batches exist. Mark the **working spawn band** as a shaded interval so slider ends don’t look like trait ends. Optional second y: wipe %. Do **not** plot `avgFood` on the same axis.

**Low-impact knobs in a mixed world (the real Differ question)**

Uniform Lab asks: *if everyone is slow, how many live?* Mixed Differ asks: *if some are slow and some are not, who is left?* Those can disagree.

- **Frequency-dependent:** high Drift looked slightly worse when *everyone* seeks. A few noisy bodies in a crowd of lockers might find leftover pellets. Same for Sight 40 — a blind caste in a seeing crowd dies; a few wanderers might not.
- **Relative rank, same remnant:** speed 1.6 vs 2.4 did not change *how many* live. In a mix, the slightly faster ones might still be **over-represented in the 4**. Uniform remnant can call a trait “null” while the roster is sorted by it.
- **Complement / cancel:** eat threshold and gluttony didn’t move count. In a mix they can still change *who holds the bag* (high T = fatter, hungrier). That’s a later Economy hook, not a Survive trait.
- **Special is a weak mixed test:** 1 vs 59, not 30 vs 30. Use it for stories, not for ranking.

**How to measure mixed edge (after a mix exists)**

1. One island, one seed family, draw traits from the **working bands** (not slider gods).
2. Score **P(alive | trait bin)** or mean trait of alive vs dead — not just final pop.
3. Start with **two groups** (A/B, n=30/30) before a full Gaussian mix.
4. First mixed tests: (a) Hunger easy vs hard, (b) Efficiency 1.2 vs 2.4, (c) **Drift or speed** as the “null remnant” candidate — if (c) still sorts the roster, keep it as flavor/edge; if not, freeze.

Lab cannot do mixed setups today. Blocked on spawn mix (Differ desk) or World multi-group. Until then, do not promote Drift/Speed/Gluttony to remnant-v1 on mixed-world speculation.

### Desk (after the set is locked)

First Differ **ship** (one PR, layout `design-docs/1.0.1-differ-layout-design.html`): **Differ…** modal (Groups + Roster), spawn traits, hunt decode, fair-eat, thin World rail. Inspector shows the four traits. **Keep** Survive trends + history until a later version.

**Later versions (not the first PR):**

| Item | When | Notes |
|------|------|--------|
| World observability column | after Mix works | Multi-line pop by group, drop bag-food KPIs, mix snapshot in history, best remnant. Spec is §4 of `design-docs/1.0.1-world-mix-design.html`. |
| Lab mix / Lab fair-eat | after World trusted | Uniform Lab stays. Don’t rewrite Lab in the first Differ PR. |
| Phase-path → finish file | no | Breaks lone `index.html`. Labels only. |

Version: first ship `1.0.0-differ`. Phase path **labels** only. Design notes still live under `design-docs/1.0.1-*-design.html` (doc revisions, not skipped app versions).

Also discussed, not v1: Patience, SocialAffinity, HarvestEfficiency, RiskSensitivity, Reciprocity, follow-successful, Selectivity (needs pellet size), Hoarding (needs trade or a deliberate eat-threshold push).

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
