# Future features — trait-evolution-sim

**Open work only.** When something ships or we drop it, it leaves this file and gets a note in `IMPLEMENTATION_LOG.md`.

Live: Phase **1 · Differ** · `1.2.0-trends`. Path: Survive → Differ → Evolve → Economy.  
How we work: `AGENTS.md`. Write in normal English everywhere.

Do not grow `phase-0-survive-finished.html`. Live work is `index.html`.

---

## What is *not* next

**Lab for Differ — dropped.** Survive Lab was for “everyone is the same, run it 30 times.” Differ is “who is left in this mix,” which you already do in World with Crowd…. Do not un-hide Lab here.

**Turning leftover living people into the next crowd — that is Evolve**, not a Differ patch. Clicking someone to see their traits is already here. Making children from survivors waits for Phase 2.

**Special…** stays off until we miss pinning one pet.

**Clicking the phase name must not open the Survive file.** A lone download of `index.html` would not find that file.

**Phase 0 leftovers — dropped.** We are not going back to Survive polish (playbook, Lab-sized canvas, extra Survive stories, last-food memory, food-density maps, sliding drawers). None of that helps “who is left in this mix.” Catch stays: bag +1, pellet gone. Do not bring back different pellet sizes or chew-until-empty.

---

## Phase 1 · Differ (still open)

World already has Crowd…, stories, Apply, Reset, four traits, fair eat, and graphs that know groups.

| Item | In English |
|------|------------|
| World seed on export | So you can replay the same scramble of food and starting spots. Small. |
| Bigger island | Canvas is still 800×600. A larger map with the same pellet gap means more walking — hunt and speed would show. Weather knob, not a new physics law. |
| Patchy food | Right now pellets can land anywhere at one rate. Two neighborhoods (lush vs thin) would make “who bothers to hunt” visible. Same idea as the old “food density map,” but as Differ weather, not Survive polish. |

Optional (do them in World if you care; not a new mode):

- Don’t randomize hunger so easy that almost nobody dies.
- Spot-check hunt 0 / medium / full still behaves like old seeking.
- Once: same hunger + efficiency mix on an easy island and a hard island.
- Score *who* lived (what the living people were like vs the dead), not only the headcount.

Speed is flavor: it should change how the island *looks*, not secretly be the whole game.

**Not queued** (need new physics or Economy): patience, social affinity, extra harvest skill, risk, reciprocity, follow-the-winner, picky eating, hoarding.

---

## Phase 2 · Evolve

People have children while a run is going. Kids inherit, with a little mutation. Then you can watch traits over generations.

A first slice you can *see*: take who is still alive, nudge their traits, Reset (“what wins next year”). Charts of many generations wait until that loop exists.

---

## Phase 3 · Economy

Trade first, then one step at a time: storage, production, jobs, maybe capital.

---

## Tooling (lower priority)

- Overlay several runs on one trend graph.
- Keep a folder of old run files (beyond this session).
- Comment sections inside the single `index.html` — no extra source files unless asked.
