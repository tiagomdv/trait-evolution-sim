# trait-evolution-sim

A **spatial agent-based evolutionary simulation** that starts as a survival sandbox and grows into an observable micro-economy.

**North star:** Watch what helps agents survive become what helps them thrive as the world gets richer — hunger first, then behavioral differences, then generations, then economic interaction.

**Right now:** Phase 1 · Differ is **live** as `1.0.0-differ` (`index.html`). Phase 0 · Survive is a **finished game** in its own file. They do not share state.

It’s also how we practice shipping a sim with an AI pair: small steps, a human as PM, history in git.

---

## Phases

Survive → Differ → Evolve → Economy. When a phase closes we freeze a playable copy and stop editing it. Live work stays `index.html`.

| Phase | Status | Play this |
|-------|--------|-----------|
| **0 · Survive** | Closed 2026-08-13 | [`phase-0-survive-finished.html`](phase-0-survive-finished.html) — one shared body, Seek/Random, Lab, Special. |
| **1 · Differ** | Open — live `1.0.0-differ` | [`index.html`](index.html) — Crowd…, mixed agents. Trends/Lab later. |
| **2 · Evolve** | Later | — |
| **3 · Economy** | Later | — |

What’s next: `FUTURE_FEATURES.md`. What shipped: `IMPLEMENTATION_LOG.md`. Older numbered snapshots: `archive/`.

---

## Two games, two files

Open one at a time. There is no in-app button between them (a lone download of `index.html` would not find the Survive file anyway). Keep both files in the folder if you want both games.

**Differ (what we’re building)** is [`index.html`](index.html), version `1.0.0-differ`.

1. Open **Crowd…**.
2. Edit **Groups** (kinds + counts) or **Roster** (named people). The tabs are separate drafts — switching does not fold one into the other.
3. Or import JSON from `phase-1-differ-presets/`.
4. Press **Apply** (remembers the open tab; the island should not change yet).
5. Press **Reset** (spawns that stamp). Food spawn on the left is live weather; the crowd only changes after Reset.

Lab, Special, Trends, and History are greyed out on Differ World. They still belong to Survive.

**Survive (finished)** is [`phase-0-survive-finished.html`](phase-0-survive-finished.html). Seek vs Random, island L/B/P, Special, Lab batches, Trends, History. Do not add features to that file.

Survive asks “if everyone shares one body, how many live?” Differ asks “if they don’t, who is left?” That’s why the live desk is Crowd…, not the old slider rail.

---

## Version

The one-line label in `VERSION` and on the World badge should match. Live is **`1.0.0-differ`**. Survive’s frozen label is `0.9.6-params`. Older ships (Lab, Special, Seek, …) are in `IMPLEMENTATION_LOG.md`, not here.

---

## How we got here

### Phase 0 · Survive (closed)

Survive is the finished uniform world: everyone uses the same knobs. You can still play it. Hunger goes up, they walk, they eat pellets, leftover people at 90 seconds is the score we care about.

**Survive Lab** lives only in that finished file. Compare uniform setups, export JSON, rank **alive at 75–90s**. Long runs make `avgFood` look huge because one fat survivor sits on a pile of bags — don’t rank by that. Lab cannot mix types, so don’t use it to judge a Differ Crowd.

We closed Survive when Play + Lab + export felt like a game, not because every leftover idea was done. Those leftovers sit at the bottom of `FUTURE_FEATURES.md`. They are not a gate.

### Phase 1 · Differ (open)

Differ starts when agents are **not** the same at spawn. No babies yet (that’s Evolve). The first job was: which Survive knobs are worth becoming traits?

We sat in Survive Lab and asked, one knob at a time: if *everyone* is like this, how many are still standing at 90 seconds? Same island (Seek, Balanced), 30 seeds. About **four or five of sixty** lived at the default body. That leftover count is what we call remnant.

**Why these four traits (not a wish list)**

| Trait | Why it made the set |
|-------|---------------------|
| **Hunger rate** (burn) | Moved remnant smoothly. Working band ~0.049–0.084. Too low and almost nobody dies. |
| **Efficiency** (meals) | Same story. Band 1.2–2.4. 0.80 wipes the crowd. |
| **Hunt** (one number `t`) | Sight, hunger pull, and seek push acted like a switch — off wipes, “more” barely helps. One lock, not three sliders. `t = 0` is off. |
| **Speed** | Mid-band barely changed *how many* lived. Kept as flavor so a mixed field can still look slow vs twitchy. A slightly faster hare might still be the one of the four who remains. |

Gluttony (meal size) and eat threshold did **not** change remnant. Food spawn and N are island weather, not traits. Policy (Seek / Random) is the experiment, not a body.

That Lab still cannot tell you who wins *inside* a mixed crowd. Uniform “everyone is slow” ≠ “half are slow.” That’s a Differ question, on the canvas, after Apply + Reset. Raw leftover counts: `IMPLEMENTATION_LOG.md` (2026-08-13 Differ Lab screen). Open science (hunt `t` curve, mixed-edge, hunger-band refine): `FUTURE_FEATURES.md`.

---

## How we build (and why the process changed)

If a feature doesn’t make it easier to see *why* the leftover crowd looks like that, it waits. We ship one idea at a time. The live app stays a single `index.html` (Tailwind CDN, canvas, no build). Human decides when to open a PR.

**Resteer (2026-07-23).** Early on we wrote a full design doc, then pasted every change into `index.html` by hand. That was too slow for layout. Split the work:

| Track | What | Who types |
|-------|------|-----------|
| **A — Layout** | CSS, panels, labels, docks | AI may edit `index.html` directly |
| **B — Mechanics** | Hunger, movement, spawn, anything that changes *feel* | Human leads; AI proposes; human says when to apply |

Layout is cheap to undo if `archive/` has a snapshot. Mechanics are not. Full rules: **`AGENTS.md`**.

**Resteer (phase close).** When Survive closed we stopped growing `0.9.x` and froze `phase-0-survive-finished.html`. Live `index.html` became Differ. Design notes for the Crowd desk still live under `design-docs/1.0.1-*-design.html` (doc revisions, not skipped app versions). First ship is `1.0.0-differ`.

---

## Project structure

What you actually open, and what is only history.

| Path | What it is |
|------|------------|
| `index.html` | Live Differ World. The only file we grow. |
| `phase-0-survive-finished.html` | Frozen Survive game. Play it; don’t patch it. |
| `phase-1-differ-presets/` | Crowd… import JSON (groups + rosters). |
| `VERSION` | One-line live label. Must match the World badge. |
| `README.md` | This file. |
| `AGENTS.md` | Process: tracks A/B, versioning, PR checklist. |
| `FUTURE_FEATURES.md` | Open backlog (checklists). Shipped items leave this file. |
| `IMPLEMENTATION_LOG.md` | What each version actually shipped, newest at the bottom. |
| `archive/` | Old `index.html` snapshots + old doc copies. See `archive/MANIFEST.md`. |
| `design-docs/` | Design HTML for a version when we needed one. |

---

Built as a hands-on experiment in agent-based modeling and AI-assisted software development.
