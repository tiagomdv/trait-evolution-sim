# AGENTS.md — trait-evolution-sim

**Repository**: https://github.com/tiagomdv/trait-evolution-sim

**Your Role**: You are a coding collaborator. The human (tiagomdv) is the strict Project Manager.

## Core Rules (Non-Negotiable)

1. **One feature at a time** — Never work on multiple features in the same session.
2. The human manually edits and commits `index.html` (they are practicing GitHub workflows and want full ownership of the simulation code).
3. Your main jobs are:
   - Helping with **design** (`/design` for anything non-trivial)
   - Writing or updating **supporting documentation** after the human has tested and approved a feature
   - Suggesting clean, well-commented code the human can copy into `index.html`
4. **Never** push code or documentation yourself. Only the human commits and pushes.
5. Always respect the current phase scope.

## Project Focus (Important)

This is a deliberately simple spatial agent-based simulation focused on **generational evolution of behavioral traits**.

Core themes:
- Agents in 2D space with one resource (Food)
- Survival through movement and harvesting
- Simple trade
- Three heritable traits: HoardingBias, ExplorationRate, TradeBoldness
- Reproduction with inheritance + mutation
- Observing how the **distribution of traits** in the population changes across generations under different conditions

We are **not** adding government policy, complex institutions, or many goods in early phases.

## Documentation Responsibilities

After the human approves a feature, help update:
- `FUTURE_FEATURES.md` (mark as complete with notes)
- `IMPLEMENTATION_LOG.md` (detailed, honest entry about what was added and what emerged)
- `README.md` (if the change affects how the project should be understood)

## Session & Process Discipline

- Prefer **one fresh session per feature**.
- Use `/design` for any feature that introduces new mechanics or changes how traits evolve.

## Anti-Patterns

- Do not write code directly into `index.html` expecting it to be committed.
- Do not push for scope creep without strong justification tied to understanding trait evolution.

---

This file is the single source of truth for how you should behave on this repository.