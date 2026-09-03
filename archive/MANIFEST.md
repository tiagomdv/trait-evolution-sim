# Archive Manifest (`MANIFEST.md`)

Frozen snapshots. **Never edit files in this folder.** This file is the index only — not an archived copy of the project README.

Live sim is always `../index.html`. Version label is in `../VERSION`.

---

## index.html snapshots

| File | Version | Phase | PR | Git commit | Description |
|------|---------|-------|-----|------------|-------------|
| `index-0.1.0-foundation.html` | 0.1.0-foundation | 0 · Survive | #7 | `11388dd` | Live hunger sliders + sidebar |
| `index-0.2.0-run-history.html` | 0.2.0-run-history | 0 · Survive | #8 | `11fa5a2` | In-memory run history + basic stats |
| `index-0.3.0-observability.html` | 0.3.0-observability | 0 · Survive | #13 | `2af4746` | Tabs, metrics, trends, inspector, speed |
| `index-0.5.0-phase-rail.html` | 0.5.0-phase-rail | 0 · Survive | #15 (bundled) | — | Thematic arc UI label + phase rail (bundled in 0.7) |
| `index-0.6.0-run-setup.html` | 0.6.0-run-setup | 0 · Survive | #15 (bundled) | — | Presets, agent count, controls (bundled in 0.7) |
| `index-0.7.0-run-compare.html` | 0.7.0-run-compare | 0 · Survive | #15 | `b828355` | Full-run trends, richer cards, agent IDs, pin-to-trends |
| `index-0.8.0-layout-dashboard.html` | 0.8.0-layout-dashboard | 0 · Survive | (local) | — | Tall Command layout + Arctic Ice (pre metrics/inspector dock polish) |
| `index-0.8.1-metrics-dock.html` | 0.8.1-metrics-dock | 0 · Survive | (local) | — | KPI metrics + inspector dock in left column |
| `index-0.8.2-history-table.html` | 0.8.2-history-table | 0 · Survive | (local) | — | History table D+ · best top-right · pin-by-ID in dock |
| `index-0.8.3-layout-flex.html` | 0.8.3-layout-flex | 0 · Survive | (local) | — | Layout flex attempt (pre tight A) |
| `index-0.8.4-tight-layout.html` | 0.8.4-tight-layout | 0 · Survive | (this PR) | — | 260/1fr/260, in-column hide, edge tabs, canvas resize, flush host |
| `index-0.9.0-seek.html` | 0.9.0-seek | 0 · Survive | (local I1 freeze) | — | Seek MVP + feel-tunes (spawn 1–50, ceiling ×10, batch 3, fatter agents, min/max carried food KPIs); human A/B Seek vs Random OK |
| `index-0.9.1-ui-chrome.html` | 0.9.1-ui-chrome | 0 · Survive | (local freeze) | — | Viewport lock, Movement dual toggle, quiet badge, speed spacing, preset highlight + Seek retune, Advanced + Help modals; seek mechanics unchanged from 0.9.0-seek |
| `index-0.9.2-special.html` | 0.9.2-special | 0 · Survive | (local freeze) | — | Special agent with param override modal; history last-3 + full popup; compact history for trends; header Special/Help; Movement top; Trait Evolution Sim + phase tagline; env groups initial agents |
| `index-0.9.3-vision.html` | 0.9.3-vision | 0 · Survive | (local freeze) | — | N4 header (Project name: trait-evolution-sim · Agent evolution lab); Vision… modal; phase P3 on canvas-module; path near Differ; no Phase chip in brand |
| `index-0.9.4-run-logs.html` | 0.9.4-run-logs | 0 · Survive | (local) | — | Run logs modal + export; world seek accel/wander/maxSpeed; expanded Help (refreshed snapshot) |
| `index-0.9.5-lab.html` | 0.9.5-lab | 0 · Survive | (local) | — | World\|Lab mode; 1–5 setup headless batches; Lab Parameters; result cards; Export/Copy last batch; no special in Lab |
| `index-0.9.6-params.html` | 0.9.6-params | 0 · Survive | (local) | — | No rail sliders; island presets (higher N = harder); Seek/Agent masters; no ground fill; fill-per-food pocket eat |
| `index-1.0.0-differ.html` | 1.0.0-differ | 1 · Differ | #26 | — | First Differ: Crowd…, four traits, Apply then Reset |
| `index-1.0.1-stories.html` | 1.1.0-stories (file still named 1.0.1) | 1 · Differ | (local) | — | Crowd stories + Help. Product name is 1.1.0. |
| `index-1.2.0-trends.html` | 1.2.0-trends | 1 · Differ | (local) | — | Trends + History by group; last live before three food spots |
| `index-1.3.0-patches.html` | 1.3.0-patches | 1 · Differ | (local) | — | Three food spots + checkbox; last live before Mix UI polish |
| `index-1.3.1-mix-ui.html` | 1.3.1-mix-ui | 1 · Differ | (local) | — | Mix box: Apply closes, four traits always, story blurbs |
| `index-1.3.2-path.html` | 1.3.2-path | 1 · Differ | (local) | — | Path bar 30%; last live before zoom-out island |
| `index-1.4.0-island.html` | 1.4.0-island | 1 · Differ | (this PR) | — | Zoom-out 2× world; last live before camera-locked Hide |

---

## Documentation snapshots

| File | Date | Notes |
|------|------|-------|
| `docs/README-pre-resteer-2026-07-02.md` | 2026-07-02 | Pre vision resteer |
| `docs/FUTURE_FEATURES-pre-resteer-2026-07-02.md` | 2026-07-02 | Pre vision resteer |
| `docs/IMPLEMENTATION_LOG-pre-resteer-2026-07-02.md` | 2026-07-02 | Dev log through PR #13 |
| `docs/FUTURE_FEATURES-pre-backlog-hygiene-2026-07-30.md` | 2026-07-30 | Pre backlog-hygiene resteer (mark-done → delete-on-ship) |

---

## Resteer note (2026-07-02)

**Thematic arc:** Survive → Differ → Evolve → Economy  
**Version scheme:** `N.x` where major N = phase number  
Trade lives inside Phase 3 · Economy. Live docs updated; history preserved in `IMPLEMENTATION_LOG.md` and `archive/docs/`; `FUTURE_FEATURES.md` is active backlog only (see 2026-07-30 hygiene).
