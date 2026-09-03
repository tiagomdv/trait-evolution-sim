# Future features — trait-evolution-sim

**Open work only.** Shipped or dropped items go in `IMPLEMENTATION_LOG.md`, then leave this file.

Live: Phase **1 · Differ** · `1.3.2-path`. Path: Survive → Differ → Evolve → Economy. Path bar 30% through Differ (human set).  
Live file is `index.html`. Do not grow `phase-0-survive-finished.html`.

---

## Phase 1 · Differ

The mix already works: Mix, stories, Apply / Reset, graphs, run logs, fat leftovers slow down, three food spots. What’s left is more *island* — still no babies.

**Island (weather)**

| Item | In English |
|------|------------|
| Bigger island | Canvas is still ~800×600. Same pellet gap on a larger map = more walking. Hunt and speed would show more. Spots already exist, so “where” means something. |
| Food vs crowd size | Same interval with 30 people vs 80 is a different game. Maybe a hint on the slider, not auto-magic. |

**Desk (only if we miss it)**

| Item | In English |
|------|------------|
| Overlay runs | Draw two or three leftover lines on one graph (this session). |
| Special… | Pin one pet and tweak them. Off until we actually miss it. |
| A list of who is still alive | Click-the-dot already works. A roster of leftover names would help Families / Rungs, still not children. |

---

## Phase 2 · Evolve

The question becomes: **who has kids, and do the kids look like them?**

Not a Differ patch. Looking at leftovers is Differ. Making the next crowd from those leftovers is Evolve.

**First thing you can see**

1. A run ends (or you press something like “next year”).
2. Take who is still walking.
3. Make a new crowd from them — inherit the four traits, nudge a little (mutation).
4. Reset the island with that new crowd.
5. Watch whether hunt-high leftover people become *more* of the field next year.

**Then, once that loop exists**

- Births *during* a run (not only at Reset), if it still reads on the island.
- How much mutation vs how faithfully kids copy parents.
- Charts over generations: mean hunt / hunger / efficiency / speed, and how spread out the family is.
- Maybe a “keep the leftovers, throw away the dead” button vs true overlapping generations.

Do not start generation histograms before you can *see* a birth.

---

## Phase 3 · Economy

After you can see inheritance. One step at a time, because each one is new physics.

| Step | Name | What it is |
|------|------|------------|
| 3.1 | Trade | Two people close together exchange food (or later goods). |
| 3.2 | Storage | A bag that isn’t just “calories until I nibble.” Hoarding becomes a real choice. |
| 3.3 | Production | Turn time / location into more food (farm, convert). |
| 3.4 | Labor | Some people work for others. |
| 3.5 | Capital | Saving / investing — only if 3.1–3.4 actually need it. |

Traits that only make sense once trade or storage exists (patience, following the successful, picky eating, real hoarding) wait for this phase. Don’t invent them in Differ.

---

## Talk and share (not a phase, not next)

Two different rules. Do not glue them into one “social” slider. Not queued under Differ, Evolve, or Economy. Parked here until we miss them.

**Talk (call)** — I point, I do not give. Someone who just ate, or who sees a thick pile, tugs nearby people toward that spot. No food leaves a bag. Useless on a flat island (food is everywhere). Needs a mark you can *see* on the canvas.

**Share** — I already have it, I give it. One pellet from my bag to a hungrier neighbor of the same Crowd color, only if my bag is above a bar. Fair-eat (already live) is who wins the pellet on the ground. Share is after you already won.

Talk can exist with zero sharing. Share can exist with zero talk. “Kin” here means same group color, not blood (blood is Evolve). Trade clubs are Economy, not gifts.

---

## Bump (not a phase, not next)

When two people walk into each other. Parked. Bigger island first. Not typed yet.

**Locked rule (human, 2026-09-03):** bigger body = **bigger knock**. Hunger **goes up** (a cost, not a snack). The **bigger one pays more hunger** than the small one. Fat shoves hard and also burns harder for the clash. Thin gets moved more, pays less hunger.

Size here is the drawn circle (bag), same as now. Cooldown so a camp does not tick every frame.

**Do not:** lower hunger on bump (free meal, pile camps heal). Do not make the small one pay more. Do not move food bag-to-bag (that’s Share / Economy).

**First look if we type it:** bounce you can see (flash, step apart, fat knocks farther) plus that hunger tax. Same-color vs other-color can wait. No new trait until a knock is visible.

---

## Tooling (any phase, lower priority)

- Keep a folder of old run files, not only this browser session.
- Comment sections inside the single `index.html` — no extra source files unless asked.
