# AGENTS.md — trait-evolution-sim

**Repo:** https://github.com/tiagomdv/trait-evolution-sim

You are a coding pair. The human (tiagomdv) is PM and has the last word on how the sim *feels*.

Read this whole file at the start of any session that implements, versions, or opens a PR.

---

## How we talk (non-negotiable)

Write like a person sitting next to the human at the sim. **Normal English.** Chat, PR text, commit messages, comments in `index.html`, Help, Vision, README, FUTURE_FEATURES, IMPLEMENTATION_LOG, design notes, UI labels.

Do:

- Short sentences. Everyday words. Explain a knob by what you *see* (who lives, who starves, colors on the island).
- Name buttons and files as they appear: Crowd…, Apply, Reset, Help, `index.html`.
- If a term is unavoidable, define it once in plain words the first time it shows up.

Do not:

- Jargon stacks or variable names as product names (`t`, remnant, caste, decode) unless you say what they mean.
- Fake-precise science when we mean “try this mix and watch who is left.”
- Docs that assume the reader memorized Survive Lab.

Comments in code: one line of *why*, in English.

**“Let’s push” means open a PR** after the human asked — not land on `main` unless they clearly say merge to main / push to main.

---

## Layout vs mechanics (read this)

The old flow (full design doc → human pastes every change by hand) was too slow for layout.

| Kind | What | Who types | Gate |
|------|------|-----------|------|
| **Layout** | CSS, panels, labels, tabs, spacing — how it *looks* | AI may edit `index.html` | Human opens in the browser; keep or restore archive |
| **Mechanics** | Hunger, movement, eat, spawn, anything that changes *feel* | Human leads. AI may propose. Human says when to apply. | Human runs it and judges |

Layout is cheap to undo if snapshots exist. Mechanics are not.

Still true:

- Live app is one `index.html`. Do not rename it. Version lives in `VERSION`, the badge, and archive filenames.
- One feature at a time when possible.
- Do not land on `main` unless the human asks. Prefer a PR when they say ship / push / PR.
- Prefer the human to commit unless they say otherwise this session.
- Live work is Differ (`index.html`). Do not grow the Survive freeze file.

---

## Shipping checklist

### Before coding

1. Read `VERSION`, the in-app badge, and `archive/MANIFEST.md`.
2. Say whether this is layout or mechanics. Do not mix in one PR unless the human says so.
3. If live `index.html` is ahead of the last archive of the *previous* good state, copy it to `archive/` first.

### While coding (layout)

1. Edit `index.html` in place.
2. Bump `VERSION` and the in-app badge together.
3. Snapshot meaningful steps only (risky rewrite, a slice that feels done, before a PR).
4. Do not quietly change hunger / movement / eat while doing layout.

### Smoke test

- New run; pause / resume; change speed
- Crowd…: pick a story, Apply, Reset — the island matches
- Trends and History still draw
- Click a person; Help still reads as a short how-to, then details
- Window resize; badge matches `VERSION`

### Before opening the PR

1. Archive of the previous live version exists if the sim changed
2. `VERSION` matches the badge
3. `archive/MANIFEST.md` has a row for any new snapshot
4. README live line updated if the version changed
5. Short new section at the **bottom** of `IMPLEMENTATION_LOG.md` (add, don’t rewrite the past)
6. `FUTURE_FEATURES.md` — remove what shipped or we dropped; leave only still-open work
7. No full design-doc package unless the human asked

### PR description

```markdown
## Track
Layout | Mechanics | mixed (human said so)

## Summary
- What changed, in plain language
- Version: `x.y.z-codename`

## Process
- [ ] Archive of previous live version
- [ ] VERSION + badge + MANIFEST (+ README if needed)
- [ ] Clicked through in the browser (layout) / judged the feel (mechanics)
- [ ] Human asked for this PR after looking at it

## Notes
- Who typed what
```

Every PR: the human **asked for the PR after looking at it**, and who typed the code. Sim PRs: someone **clicked in the browser**.

---

## Files

Do not create new files unless the human approved them, except:

- `VERSION`
- `archive/index-<version>.html` — freeze copies (**never edit** those files)
- `archive/docs/*` — safety copies before a big doc rewrite
- `archive/MANIFEST.md`
- `design-docs/` when the human wants a design note

Live entrypoint stays `index.html`. Version = `VERSION` + badge + `archive/index-<version>-<codename>.html`.

---

## Version numbers

`N.x.y-codename`. **N** is the phase (`0` Survive, `1` Differ, …).

**Middle number** is a playable slice, not a typo fix. Crowd `1.0.0`. Stories `1.1.0`. Trends `1.2.0`. Last number is a small fix on that slice. Don’t spend `1.0.1` on a real feature.

Copy to archive **the version you’re leaving behind**, then bump.

Do **not** edit files inside `archive/` (only add snapshots + MANIFEST rows).

---

## Core rules

1. One feature at a time.
2. Layout: AI may write `index.html`. Mechanics: human leads.
3. Human owns ship: they look, then they ask for the PR. No surprise `main`.
4. Stay in the current phase.
5. Log = history (append only). FUTURE_FEATURES = open work only.

Wanted later → `FUTURE_FEATURES.md`. Dropped → one line in `IMPLEMENTATION_LOG.md`, then delete it from FUTURE_FEATURES.

---

## Phases

Survive → Differ → Evolve → Economy

| Phase | Now |
|-------|-----|
| 0 Survive | Closed. Frozen file. |
| 1 Differ | Live. Mixed bodies. No babies. |
| 2 Evolve | Later. Children, inheritance. |
| 3 Economy | Later. Trade first. |

Using leftover living people to **make** the next crowd is Evolve. Looking at who is still alive is Differ.

---

## After something ships

- `VERSION` + README if the version changed
- New dated section at the bottom of `IMPLEMENTATION_LOG.md`
- Remove matching items from `FUTURE_FEATURES.md`
- MANIFEST row if you added an archive file

`IMPLEMENTATION_LOG.md` is a museum. Never delete old sections. `FUTURE_FEATURES.md` is only what’s still open — no “we decided / we brainstormed / we shipped this.”

---

## Don’t

- Change eat / hunger / movement “while doing layout” unless the human asked.
- Skip archive before a big rewrite of `index.html`.
- Split the sim into extra `.js` / `.css` files without asking.
- Open a PR or push to `main` unless the human asked.
- Edit `archive/` except adding snapshots + MANIFEST.
- Rewrite history in the log.
- Leave shipped or dropped items in FUTURE_FEATURES.
- Write Help or docs as if the reader already knows Survive Lab.

---

## Paste this at the start of a new chat

```
Read AGENTS.md fully. Talk in normal English everywhere.
This session is layout / mechanics: <pick one>.
Goal: <one sentence>.
Live VERSION is the source of truth. Archive before risky edits. Single index.html.
FUTURE_FEATURES is open work only. History goes in IMPLEMENTATION_LOG.
Do not push to main unless I say so. Open a PR when I ask to ship / push / PR.
```
