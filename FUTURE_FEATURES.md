# Future features — trait-evolution-sim

**Open work only.** Shipped or dropped items go in `IMPLEMENTATION_LOG.md`, then leave this file.

Live: Phase **2 · Evolve** · `2.0.1-desk`. Path bar **15%** into Evolve (human set). Lab and Special stripped from live. No babies yet.  
Live file is `index.html`. Do not grow `phase-0-survive-finished.html` or `phase-1-differ-finished.html`.

---

## Phase 2 · Evolve

The question becomes: **who has kids, and do the kids look like them?**

Looking at leftovers was Differ. Making the next crowd from those leftovers is Evolve.

**First thing you can see** (before new Mix knobs)

1. A run ends (or you press something like “next year”).
2. Take who is still walking.
3. Make a new crowd from them — inherit the **four** traits, nudge a little (mutation).
4. Reset the island with that new crowd.
5. Watch whether hunt-high leftover people become *more* of the field next year.

Do not add kin-tax or crowd-avoid until that loop exists. Kids should copy four things first, not six.

**Then, once that loop exists**

- Births *during* a run (not only at Reset), if it still reads on the island.
- How much mutation vs how faithfully kids copy parents.
- Charts over generations: mean hunt / hunger / efficiency / speed, and how spread out the family is.
- Maybe a “keep the leftovers, throw away the dead” button vs true overlapping generations.

Do not start generation histograms before you can *see* a birth.

### Social Mix knobs (after the birth loop — not Talk, not Share)

Two different traits. Do not glue them. Do not treat them as stranger-war. Pets run: prophets **did** get huge; Control kept bumping into them and the fat tax killed the kings. Own-color tax would **not** have saved those prophets (Control hitting gold is other paint). Crowd avoid is the “I won’t be a bullet” knob.

**Own-color tax** — how hard a clash with the **same paint** hits hunger. Stranger clashes stay as they are. Family camp: cheap kin-touch means a pile of the same color can sit together. Expensive kin-touch means a family cooks its own kings. Interesting across years.

**Crowd avoid** — steer away from many nearby bodies. Fights hunt (hunt says go to the pellet; avoid says the pellet has a mob). What you’d see: Control stops bumper-caring the gold king; cranked too high looks like Lost who never eat. Hunt-high + avoid-high is a nervous hunter.

Do **not** sneak in stranger tax or king armor as a default — that’s a color war. Park until we miss it.

Not Talk (I point). Not Share (I give food). Kin here for own-color tax still means Mix paint until blood exists; after Evolve, blood can mean parents.

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

Traits that only make sense once trade or storage exists (patience, following the successful, picky eating, real hoarding) wait for this phase.

---

## Talk and share (not a phase, not next)

Two different rules. Do not glue them into one “social” slider. Not queued under Evolve or Economy. Parked here until we miss them.

**Talk (call)** — I point, I do not give. Someone who just ate, or who sees a thick pile, tugs nearby people toward that spot. No food leaves a bag. Useless on a flat island (food is everywhere). Needs a mark you can *see* on the canvas.

**Share** — I already have it, I give it. One pellet from my bag to a hungrier neighbor of the same Crowd color, only if my bag is above a bar. Fair-eat (already live) is who wins the pellet on the ground. Share is after you already won.

Talk can exist with zero sharing. Share can exist with zero talk. Trade clubs are Economy, not gifts.

---

## Tooling (any phase, lower priority)

- Keep a folder of old run files, not only this browser session.
- Comment sections inside the single `index.html` — no extra source files unless asked.
