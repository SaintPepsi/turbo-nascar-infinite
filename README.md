# 🦅 TURBO NASCAR INFINITE

Single-file Three.js NASCAR roguelite. Outrun THE PACK behind you without overcooking the corners
ahead of you. Die. Bank Freedom Points. Buy absurd upgrades. Go again, longer.

## Run it

```bash
bun run serve   # → http://localhost:8923
```

(Or open `index.html` directly — Three.js loads from the jsDelivr CDN, the only external fetch.)

## Controls

| Key | Action |
|---|---|
| ↑ / ↓ | accelerate / brake (hold for reverse) |
| ← / → | steer |
| Q | Rockets · W | Freedom Guns · E | Liberty Mines (stalls the pack) · R | Eagle Strike · T | Nitro USA |
| M | mute · ESC | pause |

## The loop

Every lap is a round. Each round the pack behind you gets faster and the world gets worse —
traffic, oil, night, rain, road rage, wind, meteors, then it stops pretending
("ROUND 14: EVERYTHING IS ON FIRE"). Too slow and the pack eats you; too fast and the wall does.
Deaths pay Freedom Points → Garage upgrades (geometric costs, clicker-style) → longer runs.
Five karts, localStorage saves, procedural chiptune (Camptown Races / Yankee Doodle / Battle Hymn —
public domain, see [Wikipedia: Camptown Races](https://en.wikipedia.org/wiki/Camptown_Races)) and
an engine note with actual gear steps.

## Balance is tested, not vibed

The entire simulation lives in a pure `<script id="sim-core">` block (no DOM, no THREE).
`tests/` extracts it verbatim and drives parameterized driver bots through seeded runs
(`bun test`, 41 tests; `bun run balance` prints the table):

| cohort | mean rounds | top cause |
|---|---|---|
| camper (parked) | 1.0 | pack 10/10 |
| bad player, fresh save | **2.0** | pack |
| good player, fresh save | **10.3** | pack/traffic |
| good player, +800 FP | 12.2 | pack |

Spec said "good player survives 10 rounds, bad player 2" — that's the contract the suite enforces.

## Docs

Design rationale: `docs/plans/2026-06-11-turbo-nascar-infinite-design.md`.
