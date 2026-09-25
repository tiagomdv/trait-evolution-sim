# Future features — trait-evolution-sim

**Open work only.** Shipped or dropped items go in `IMPLEMENTATION_LOG.md`, then leave this file.

Live: Phase **2 · Evolve** · `2.3.0-tree`. Path bar **75%** (human set with the tree). `2.2.0-gate` is closed.  
Live file is `index.html`. Do not grow `phase-0-survive-finished.html` or `phase-1-differ-finished.html`.

Kids are on the island. Do not open another birth-knob PR first.

---

## Do next (Evolve)

Two ships. Metrics first if we split. Theme can share a PR with Help/Vision chrome if the human says so. Not glued to a feel retune.

### 1. Better metrics

History and Trends are still Differ: leftover count, avg bag, avg hunger, Mix paint. They do not show a family.

Open:

- Graphs over **generations** — mean hunt / hunger / efficiency / speed / birth, and how spread the line is.
- Alive / deaths that admit **births** (a 60 stamp with 1634 deaths is real; the UI should not look like a Differ wipe).
- Unique person ids in export (`k1-1` on two people is a bug).
- Click / History that can tell founder vs kid vs grandkid without counting the word “kid.”

If you cannot see it on the island, it waits. No science dashboard.

### 2. Evolution as a theme (includes desk chrome)

Kids are on the map. The desk still reads like Differ with babies glued on.

Open:

- Help, Vision, path, tagline — family, not “Differ is finished / babies later.”
- Mix stories and leftover chips that score **whose kids**, not only whose paint.
- Strip leftover Survive / Differ chrome in live `index.html` (comments, dead sliders, “lab” talk) in the same pass if it is still lying.
- Path fill (`PHASE_WITHIN`) is **75%** as of this ship. Next bump is still the human — do not invent a number.

This is copy + chrome + what the graphs claim. Not a new birth mechanic.

---

## Parked (Evolve — only if we miss it)

Not queued. Do not sneak into the metrics or theme PR.

- **Body curve** (weak → prime → fade). Kids keep full Mix traits.
- How big the nudge is (mutation knob).
- Wipe-the-map Next year — only if overlapping lives never read. Copy-traits + Reset is still Differ.
- Births on a timer with no parent-follow — parked; that hid the family.
- **Own-color tax** — how hard a clash with the **same Mix paint** hits hunger. Strangers stay as they are. Blood line already skips knock/tax; this would be paint, not parent→kid.
- **Crowd avoid** — steer away from a mob. Fights hunt. Cranked too high looks like Lost who never eat.

Do not add stranger tax or king armor as a default (that’s a color war).

Pets run note: prophets got huge; Control bumping them (other paint) is what cooked the kings. Own-color tax would not have saved those prophets.

---

## Not a phase, not next

**Talk (call)** — I point, I do not give. Tug nearby people toward a pile. No food leaves a bag. Needs a mark on the canvas. Useless if food is everywhere.

**Share** — I give a pellet from my bag to a hungrier neighbor (same Mix paint, bag above a bar). **Not** the parent→kid handoff already live (birth bag + bump 1 food). Fair-eat is who wins the pellet on the ground.

Do not glue Talk and Share. Trade clubs are Economy, not gifts.

---

## Phase 3 · Economy

After inheritance actually **reads** (metrics + theme, not only kids existing). One step at a time; each is new physics.

| Step | Name | What it is |
|------|------|------------|
| 3.1 | Trade | Two people close together exchange food (or later goods). |
| 3.2 | Storage | A bag that isn’t just “calories until I nibble.” |
| 3.3 | Production | Turn time / location into more food. |
| 3.4 | Labor | Some people work for others. |
| 3.5 | Capital | Saving / investing — only if 3.1–3.4 need it. |

Traits that only make sense once trade or storage exists wait for this phase.

---

## Tooling (any phase, lower priority)

- Folder of old run files, not only this browser session.
- Comment sections inside the single `index.html` — no extra source files unless asked.
