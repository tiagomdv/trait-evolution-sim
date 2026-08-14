# trait-evolution-sim

A **spatial agent-based evolutionary simulation** that starts as a survival sandbox and grows into an observable micro-economy.

**North star:** Watch what helps agents survive become what helps them thrive as the world gets richer — hunger first, then behavioral differences, then generations, then economic interaction.

**Right now:** Phase 1 · Differ **live** as `1.0.0-differ`. Survive is a **finished game** next to it — two different HTML files (see below).

It’s also how we practice shipping a sim with an AI pair: small steps, a human as PM, history in git.

---

## Phases

Survive → Differ → Evolve → Economy. When a phase closes we freeze a playable copy and stop editing it. Live work stays `index.html`.

| Phase | Status | Play this |
|-------|--------|-----------|
| **0 · Survive** | Closed 2026-08-13 | [`phase-0-survive-finished.html`](phase-0-survive-finished.html) — hunger, Seek/Random, Lab, Special. Everyone the same. |
| **1 · Differ** | Open — live `1.0.0-differ` | [`index.html`](index.html) — Crowd…, mixed agents. Trends/Lab later. |
| **2 · Evolve** | Later | — |
| **3 · Economy** | Later | — |

Older numbered snapshots: `archive/`. What’s next: `FUTURE_FEATURES.md`. What shipped: `IMPLEMENTATION_LOG.md`.

---

## Two games, two files

They do not share state. Open one at a time.

**Differ (what we’re building)** is [`index.html`](index.html), version `1.0.0-differ`. Open **Crowd…**, edit Groups or Roster (or import from `phase-1-differ-presets/`), press **Apply**, then **Reset**. Food spawn on the left is live weather; the crowd only changes after Reset. Lab, Special, Trends, and History are greyed out — they still belong to Survive.

**Survive (finished)** is [`phase-0-survive-finished.html`](phase-0-survive-finished.html). That’s the closed game: Seek vs Random, island L/B/P, Special, Lab batches, Trends, History. Don’t add features to it.

Keep both files in the folder if you want both games. There is no button from one to the other (a lone download of `index.html` wouldn’t find the Survive file anyway).

Survive asks “if everyone shares one body, how many live?” Differ asks “if they don’t, who is left?” That’s why the live desk is Crowd…, not the old slider rail. The four traits are burn, meals, hunt, and speed — chosen from Lab, not from a wish list. See *Why the leftover four* below.

---

## Version

The one-line label in `VERSION` and on the World badge should match. Live is **`1.0.0-differ`**. Survive’s frozen label is `0.9.6-params`. Older ships (Lab, Special, Seek, …) are in `IMPLEMENTATION_LOG.md`, not here.

---

## Why the leftover four

We sat in Survive Lab and asked, one knob at a time: if *everyone* is like this, how many are still standing at 90 seconds? Same island (Seek, Balanced), 30 seeds. About **four or five of sixty** lived at the default body.

Hunger rate and efficiency moved that leftover count in a smooth way, so they became traits. Sight, hunger pull, and seek push mostly acted like a switch — off wipes the world, “more” barely helps — so they became one **hunt** number. Speed in the middle barely changed *how many* lived; we kept it so people can look slow or twitchy, not because faster wins. Meal size (gluttony) and eat threshold didn’t change the count.

That Lab cannot tell you who wins *inside* a mixed crowd. A slightly faster hare might still be the one of the four who remains. That’s a Differ question, on the canvas, not a Lab card.

If you want the raw leftover counts from those batches, they’re in `IMPLEMENTATION_LOG.md` (2026-08-13 Differ Lab screen).

---

## Survive Lab (the finished game only)

In `phase-0-survive-finished.html`, Lab still works. Compare uniform setups, export JSON. Rank **alive at 75–90s**. Long runs make `avgFood` look huge because one fat survivor sits on a pile of bags. Don’t use that Lab to judge Differ Crowds — it can’t mix types.

---

## How we build

If a feature doesn’t make it easier to see *why* the leftover crowd looks like that, it waits. We ship one idea at a time. The live app stays a single `index.html` (Tailwind CDN, canvas, no build). Human decides when to open a PR.

Layout vs mechanics (who types what): **`AGENTS.md`**.

---

## Project structure

```
trait-evolution-sim/
├── index.html                 live Differ
├── phase-0-survive-finished.html
├── phase-1-differ-presets/    Crowd… import JSON
├── VERSION
├── README.md · AGENTS.md · FUTURE_FEATURES.md · IMPLEMENTATION_LOG.md
├── archive/                   old index snapshots
└── design-docs/
```

---

Early on we pasted every change by hand. Layout is cheap enough for the AI to edit `index.html` directly; hunger and movement still want a human in the loop. The rules: **`AGENTS.md`**.

Built as a hands-on experiment in agent-based modeling and AI-assisted software development.
