# mega-s01e03-4471 — what ticket #4471 shows

Course MEGA.dev, Challenge S01E03. The support desk merged **412 reports** about dates into
one ticket, **#4471**, marked known ("the parser reads dates month first"). The kb export
tells a different story: **two problems**, one ticket.

## The two problems

| problem | reports | tenants | what it is |
|---|---|---|---|
| `parser` | 379 | all 11 | The shared parser reads dates month first in day-first locales. The known issue; fix queued. |
| `hint` | 33 | 3 (Alder Physio, Copper Studio, Pale Harbour — all on `booking-v3`) | The `booking-v3` form's hint says `MM/DD/YYYY`, but the form reads the date day-first, the tenant's way. A **separate bug** merged into #4471 by subject, with no ticket of its own. |

Filed as GitHub issues in this repo: [parser](https://github.com/MaciejMoroz/mega-s01e03-4471/issues/1) and [hint](https://github.com/MaciejMoroz/mega-s01e03-4471/issues/2).

## How the numbers were computed

The export has 427 rows and 412 reports: 15 ids appear twice (overlapping export pages).
Counted once per id, the 412 split exactly into the two causes above, using the kb's own
logic (`support-kb/src/lib/kb/causes.ts`: cause = tenant locale + booking form + channel,
never intake's guess; intake's `intakeTag` disagrees on 38 reports).

## What's here

- `analysis/parser-ids.txt`, `analysis/hint-ids.txt` — report ids per problem
- `analysis/summary.json` — counts per problem (tenants, channels, intake tags, date ranges)
- `analysis/kb-export-267efc5e.zip` — the kb export as it arrived
- `src/` — the kb export unpacked the way the support repo holds it (`apps/kb/ → src/`),
  **plus one new page**: `src/routes/kb/incidents/4471/causes/+page.svx` — "4471 · what it
  shows: two causes, one ticket" (signed: `maciej.moroz`, desk ref printed by the page's
  `RenderStamp`)
- `rendered/incidents-4471-causes.html` — the page as the desk will see it:
  a static render of the same layout, words and computed table (the `.svx` is the source; this is its output)
