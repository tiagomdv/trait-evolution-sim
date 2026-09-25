# Trait evolution sim

Dots walk a 2D island. Hunger goes up. They grab pellets and nibble a bag. Some last. Some don’t. You mix kinds of people, watch who is still walking, and watch the kids born next to them.

Live game: [`index.html`](index.html), version **`2.3.0-tree`**. Open that file in a browser. There is no build.

Adults stay on the map. Kids appear beside a living parent and copy that parent’s mix, including how often they have kids. A starter bag moves from parent to kid. Differ and Survive are finished games in their own files. They do not share state.

If you are an AI about to change the sim, read **`AGENTS.md` first** (how to talk, layout vs mechanics, when to open a PR). This README is for a human who found the repo.

---

## 1. What this is

A small, single-file sim. One island, colored people, food piles, a Mix panel, graphs, a history of runs.

Survive, Differ, and Evolve are three games in this repo. We freeze a playable copy when a phase feels finished, then live `index.html` becomes the next one. Trade is a different project. It will not be added here.

**Right now** the live game is Evolve. Adults stay on the island. Their kids appear beside them, copy their mix, and have to live on that copy.

---

## 2. Why this repo exists

Two jobs. They are not a slogan stacked on top of each other.

**Practice.** A human is PM. An AI pair types. We ship small steps, look at them, then open a PR. GitHub is part of the work, not a dump at the end.

**Watch the island.** Not only “how many are still walking.” A camp on the food. One color owning a patch. A Prophet line filling the map while Mayflies burn. Something you did not type as a goal, that you can still point at.

How we decide what to type next lives in §7, not here.

---

## 3. How to play (Evolve)

Keep the three HTML files in the same folder if you want all three games. There is no in-app button between them. A lone download of `index.html` will not find the freeze files.

1. Open [`index.html`](index.html).
2. Open **Mix**. Pick a **story** (Groups, Families, or Rungs) or edit **Groups** / **Roster**. Those two tabs are separate drafts.
3. **Apply** remembers the open tab. The island does not change yet.
4. **Reset** is when that mix actually spawns.
5. Food interval on the left is live weather. Pellets fall as even rain. Pause / Speed are the clock.
6. Watch colors. Click a person for Mix traits, bag, **Birth**, and cling. Trends and History sit on the right.

A person can have a kid only during an open birth season, after about a minute of life, with a bag of at least 20 and hunger under 70. The first season opens at about five minutes. It stays open for about two and a half minutes, then closed for about five. A yellow banner warns for about 75 seconds before it opens. Mix Reset stamps at most 30 people. Kids born during the run are not capped. The kid follows that parent for about five minutes. The parent does not chase.

Lab and Special are only in the Survive freeze — not on this desk.

---

## 4. Three games, three files

Each file is a whole game with its own question. Open one at a time. When a phase closed we froze it and stopped editing it.

**Survive** — [`phase-0-survive-finished.html`](phase-0-survive-finished.html)  
If everyone is the same body, how many live? Seek vs wander, easy/medium/hard island, Special, Lab, Trends, History. Frozen label `0.9.6-params`. Do not add features to this file.

**Differ** — [`phase-1-differ-finished.html`](phase-1-differ-finished.html)  
If they are not the same at spawn, **who** is left? Mix, stories, graphs, three food spots, zoomed-out island, bump. Frozen label `1.5.0-bump`. Do not add features to this file.

**Evolve (live)** — [`index.html`](index.html)  
Adults stay. A kid is born next to a living parent and copies that parent’s hunger, meals, hunt, speed, and birth frequency. The copy wobbles a bit, and about one birth in eight one trait jumps. Births happen only in an open season, and only when the parent’s bag is full enough and they are not too hungry. Each birth leaves the parent burning a little faster, eating a little worse, and walking a little slower. The parent passes one food only while the kid is still following. Reset opens a Summary of who had kids, then the next crowd starts when that window closes. Version `2.3.0-tree`. This is the only file we grow.

What’s next: `FUTURE_FEATURES.md`. What already shipped: `IMPLEMENTATION_LOG.md`. Old numbered copies: `archive/`.

---

## 5. Version labels

The one-line label in `VERSION` and on the World badge should match. Live is **`2.3.0-tree`**.

Middle number = a playable slice (Crowd `1.0.0`, stories `1.1.0`, trends `1.2.0`, patches `1.3.0`, island `1.4.0`, bump `1.5.0`, kids `2.1.0`). Last number = a small fix on that slice.

---

## 6. How we got here

### Survive (closed)

Everyone uses the same knobs. Hunger goes up, they walk, they eat. How many are still walking after a while is the score.

Lab in that file is for “run the same body 30 times.” Don’t use it to judge a mixed crowd. One fat leftover sitting on a pile of bags makes average food look huge — don’t rank by that.

We closed Survive when Play + Lab + export felt like a game.

### Differ (closed)

People are **not** the same at spawn. Frozen when bump felt solid. Babies are Evolve.

We picked four traits by changing one knob at a time on a uniform crowd and asking how many were still standing:

| Trait | Why it stayed |
|-------|----------------|
| Hunger rate | Changes how many live, smoothly. |
| Efficiency | Same. How much a bite from the bag helps. Very low wipes the crowd. |
| Hunt | Seeing / pulling / pushing toward food was basically on or off. One number. Zero is off. |
| Speed | Barely changed *how many* lived. Kept so a mix can look slow vs twitchy. Fat leftovers also get slower as their bag (and drawn size) grows. |

Meal size and “how hungry before I nibble the bag” did not change how many lived. Food interval and how many people are weather, not a body.

Judge a mix on the island: who is still walking.

### Evolve (this ship)

Differ ends when you look at who is still walking. Evolve continues from those people. They stay on the map and have kids beside them. You can watch a parent and a child at the same time.

Birth frequency is a Mix trait. It sets how often a person tries. Cling is a clock, about five minutes, not another slider. During that time the kid follows the parent. Kids are born with a full mix. People in the same blood line do not knock or tax each other. The parent gives the kid a starter bag at birth, and still passes one food when they walk into that kid. Each birth also dents the parent’s burn, meals, and speed. That dent stays.

---

## 7. How we build

One idea at a time when we can. Live app is a single `index.html` (no build). The human decides when to open a PR. Prefer the human to commit unless they say otherwise.

If a change does not make it easier to **see a leftover shape** (who, where, which color, whose kids) — or to **ship a small GitHub step** — it waits.

**Layout vs mechanics.** CSS, panels, labels: the AI may edit `index.html`. Hunger, movement, eat, spawn: the human leads; the AI proposes; the human says when to apply. Layout is cheap to undo if `archive/` has a snapshot. Mechanics are not. Full rules: **`AGENTS.md`**.

When Survive closed we froze `phase-0-survive-finished.html` and live `index.html` became Differ. When Differ closed we froze `phase-1-differ-finished.html` and live `index.html` became Evolve.

**Do not patch** the two freeze files. Do not land on `main` unless the human says merge / push to main. “Let’s push” means open a PR after they looked.

---

## 8. What’s in the folder

| Path | What it is |
|------|------------|
| `index.html` | Live Evolve. The only file we grow. |
| `phase-1-differ-finished.html` | Frozen Differ. Play it; don’t patch it. |
| `phase-0-survive-finished.html` | Frozen Survive. Play it; don’t patch it. |
| `phase-1-differ-presets/` | Extra Mix Import JSON. Stories in the app don’t need these files. |
| `VERSION` | One-line live label. Must match the World badge. |
| `README.md` | This file. For humans. |
| `AGENTS.md` | How any AI should behave here (talk, PRs, shipping). |
| `FUTURE_FEATURES.md` | Open work only. |
| `IMPLEMENTATION_LOG.md` | What each version shipped, newest at the bottom. |
| `archive/` | Old `index.html` copies + old docs. Index: `archive/MANIFEST.md`. |
| `design-docs/` | Design notes from when we needed them. Not the live app. |

---

## 9. What’s next

Live is `2.3.0-tree`. Two slices close this repo:

- **2.4.0-metrics** — graphs and History that show generations, births, and who descended from whom.
- **2.5.0-theme** — Help, Vision, and the desk talk about families. Then this project stops.

Body curve, a mutation slider, own-color tax, and crowd avoid stay parked. Trade is a different project.
