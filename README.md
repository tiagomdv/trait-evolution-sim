# trait-evolution-sim

Dots walk a 2D island. They get hungry. They eat pellets. Some last; some don’t.

We start with hunger, then mix different kinds of people, then (later) children, then trade. The point is to **watch who is left** and why.

**Right now:** Differ is live in [`index.html`](index.html) as `1.2.0-trends`. Survive is a finished game in its own file. They do not share state.

A human is the PM. An AI pair types. We ship small steps in git.

---

## Phases

Survive → Differ → Evolve → Economy. When a phase closes we freeze a playable copy and stop editing it. Live work stays `index.html`.

| Phase | Status | Play this |
|-------|--------|-----------|
| **0 · Survive** | Closed 2026-08-13 | [`phase-0-survive-finished.html`](phase-0-survive-finished.html) — everyone the same body. |
| **1 · Differ** | Open — live `1.2.0-trends` | [`index.html`](index.html) — Crowd…, stories, graphs by group. |
| **2 · Evolve** | Later | Kids. Not yet. |
| **3 · Economy** | Later | Trade. Not yet. |

What’s next: `FUTURE_FEATURES.md`. What already shipped: `IMPLEMENTATION_LOG.md`. Old numbered copies: `archive/`.

---

## Two games, two files

Open one at a time. There is no button between them (a lone download of `index.html` would not find the Survive file). Keep both in the folder if you want both.

**Differ (what we’re building)** is [`index.html`](index.html), version `1.2.0-trends`.

1. Open **Crowd…**.
2. Pick a **story** (Groups, Families, or Rungs) or edit **Groups** / **Roster** yourself. The two tabs are separate drafts.
3. You can still **Import** a JSON file.
4. **Apply** remembers the open tab. The island does not change yet.
5. **Reset** is when the mix actually spawns. Food interval on the left is live weather.

Trends and History show who is left. Special is off. Lab stays in the Survive file.

**Survive (finished)** is [`phase-0-survive-finished.html`](phase-0-survive-finished.html). Everyone shares one body. Seek vs wander, easy/medium/hard island, Special, Lab, Trends, History. Do not add features to that file.

Survive asks: if everyone is the same, how many live? Differ asks: if they aren’t, **who** is left?

---

## Version

The one-line label in `VERSION` and on the World badge should match. Live is **`1.2.0-trends`**. Survive’s frozen label is `0.9.6-params`.

Middle number = a playable slice (Crowd `1.0.0`, stories `1.1.0`, trends `1.2.0`). Last number = a small fix on that slice.

---

## How we got here

### Survive (closed)

Everyone uses the same knobs. Hunger goes up, they walk, they eat. How many are still walking after a while is the score.

Lab in that file is for “run the same body 30 times.” Don’t use it to judge a mixed Crowd. One fat leftover sitting on a pile of bags makes average food look huge — don’t rank by that.

We closed Survive when Play + Lab + export felt like a game.

### Differ (open)

People are **not** the same at spawn. No babies yet (that’s Evolve).

We picked four traits by changing one knob at a time on a uniform crowd and asking how many were still standing:

| Trait | Why it stayed |
|-------|----------------|
| Hunger rate | Changes how many live, smoothly. |
| Efficiency | Same. How much a bite from the bag helps. Very low wipes the crowd. |
| Hunt | Seeing / pulling / pushing toward food was basically on or off. One number. Zero is off. |
| Speed | Barely changed *how many* lived. Kept so a mix can look slow vs twitchy. Fat leftovers also get slower as their bag (and drawn size) grows. |

Meal size and “how hungry before I nibble the bag” did not change how many lived. Food interval and how many people are weather, not a body.

Judge a mix on the island: who is still walking.

---

## How we build

If a change doesn’t make it easier to see *why* the leftover crowd looks like that, it waits. One idea at a time. Live app is a single `index.html` (no build). The human decides when to open a PR.

**Layout vs mechanics.** CSS, panels, labels: the AI may edit `index.html`. Hunger, movement, eat, spawn: the human leads; the AI proposes; the human says when to apply. Layout is cheap to undo if `archive/` has a snapshot. Mechanics are not. Full rules: **`AGENTS.md`**.

When Survive closed we froze `phase-0-survive-finished.html` and live `index.html` became Differ.

---

## What’s in the folder

| Path | What it is |
|------|------------|
| `index.html` | Live Differ. The only file we grow. |
| `phase-0-survive-finished.html` | Frozen Survive. Play it; don’t patch it. |
| `phase-1-differ-presets/` | Extra Crowd… Import JSON. Stories in the app don’t need these files. |
| `VERSION` | One-line live label. Must match the World badge. |
| `README.md` | This file. |
| `AGENTS.md` | How any AI should behave here. |
| `FUTURE_FEATURES.md` | Open work only. |
| `IMPLEMENTATION_LOG.md` | What each version shipped, newest at the bottom. |
| `archive/` | Old `index.html` copies + old docs. Index: `archive/MANIFEST.md`. |
| `design-docs/` | Design notes from when we needed them. Not the live app. |
