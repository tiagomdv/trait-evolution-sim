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

---

## Documentation snapshots

| File | Date | Notes |
|------|------|-------|
| `docs/README-pre-resteer-2026-07-02.md` | 2026-07-02 | Pre vision resteer |
| `docs/FUTURE_FEATURES-pre-resteer-2026-07-02.md` | 2026-07-02 | Pre vision resteer |
| `docs/IMPLEMENTATION_LOG-pre-resteer-2026-07-02.md` | 2026-07-02 | Dev log through PR #13 |

---

## Resteer note (2026-07-02)

**Thematic arc:** Survive → Differ → Evolve → Economy  
**Version scheme:** `N.x` where major N = phase number  
Trade lives inside Phase 3 · Economy. Live docs updated; history preserved here and in active `FUTURE_FEATURES.md` / `IMPLEMENTATION_LOG.md`.
