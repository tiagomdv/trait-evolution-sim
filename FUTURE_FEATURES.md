# Future features — trait-evolution-sim

**Open work only.** Shipped or dropped items go in `IMPLEMENTATION_LOG.md`, then leave this file.

Live: Phase **1 · Differ** · `1.2.0-trends`. Path: Survive → Differ → Evolve → Economy.  
Live file is `index.html`. Do not grow `phase-0-survive-finished.html`.

---

## Phase 1 · Differ

The mix already works: Crowd…, stories, Apply / Reset, graphs, run logs, fat leftovers slow down. What’s left is more *island* and more *replay* — still no babies.

**Island (weather)**

| Item | In English |
|------|------------|
| Bigger island | Canvas is still 800×600. Same pellet gap on a larger map = more walking. Hunt and speed would show more. |
| Patchy food | Two neighborhoods on one island (lush vs thin). Grazers vs hunters would have a place. |
| Food vs crowd size | Same interval with 30 people vs 80 is a different game. Maybe a hint on the slider, not auto-magic. |

**Replay**

| Item | In English |
|------|------------|
| World seed on export | Save the random scramble of food and starting spots so you can replay the *same* run. Small. |
| Overlay runs | Draw two or three leftover lines on one graph (this session). |

**Desk (only if we miss it)**

| Item | In English |
|------|------------|
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

## Tooling (any phase, lower priority)

- Keep a folder of old run files, not only this browser session.
- Comment sections inside the single `index.html` — no extra source files unless asked.
