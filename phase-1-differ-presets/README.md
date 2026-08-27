# Crowd… import files

The app already has **stories** in Crowd… (no file needed):

- **Groups** — kinds of people; everyone in a kind is the same
- **Families** — those same mixes, each named person a little off the average
- **Rungs** — hunt / hunger / efficiency / speed ladders, a scramble, 12 oddballs

These JSON files are extra **Import** mixes if you want them. Format: `version: 2`, `kind: "differ"`.

- `groups-*.json` — types + counts
- `roster-*.json` — one row per named person (older clone / spread files)

Usually 60 people. Colors in the file are hints; the app may remap paint.

| File | What it is |
|------|------------|
| `groups-control-strain.json` | Default 30 / 30 |
| `groups-seekers-wanderers.json` | Same body, hunt on vs off |
| `groups-tortoises-hares.json` | Slow burn vs hot lock |
| `groups-grazers-hunters.json` | Cheap graze vs must-catch |
| `groups-three-castes.json` | Idle rich / working poor / lost |
| `groups-pets.json` | A few named kinds plus a big control crowd |
| `roster-seekers-wanderers.json` | 30 + 30 named copies |
| `roster-three-castes.json` | 20 + 20 + 20 copies |
| `roster-pets.json` | Named pets + control crowd |
| `roster-seekers-spread.json` | Seekers hunt varies; wanderers stay off |
| `roster-three-castes-jitter.json` | Same three kinds; traits vary inside the family |
| `roster-tortoises-hares-spread.json` | Slow-burn family vs hot-lock family, not twins |
