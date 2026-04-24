# Scoundrel Dungeon Simulator

This simulator models the 2011 `Scoundrel` ruleset and focuses on a single strict Dungeon-running planner: `Scoundrel Delver`.

Open `index.html` in a browser and press `Run Dungeon ->` to estimate its clear rate. The filename is ready for GitHub Pages or any static host.

## Current Baseline

The current `Scoundrel Delver` planner uses only the current room, current health, equipped weapon, weapon ceiling, potion-use state, and carry-card risk. It does not inspect the hidden Dungeon order.

Local command-line probes after the planner revision produced about a `5.4%` clear rate over `10,000` Dungeon runs. This is a material improvement over the previous roughly `0.4-1.0%` behavior, but it is still below the cited `20%` human-player expectation. Treat the remaining gap as planner quality work, not a rules-engine validation.

The UI includes an optional filter to skip Dungeons whose opening room contains no Weapon before starting the run.

## Strategy Fixes

- Room skipping is now reserved for concrete danger: a losing visible plan, a carried monster that is likely to kill on the next room, or a very low-health room without potion support.
- Hidden-deck lookahead was removed. The planner no longer reads the next three cards from the dungeon to choose a carry card.
- Heuristics were normalized around health, weapon value, weapon ceiling, expected monster damage, usable potion healing, and carry-card risk instead of mixing unrelated ad hoc score scales.

## Removed Strategies

- removed Greedy weapon
- removed Conservative
- removed Potion priority
- removed Random
- removed Lookahead

These strategies were removed from both the UI and the code because they were either weaker heuristic baselines or relied on hidden-deck lookahead that is not fair human-equivalent play.

## Remaining Strategy

`Scoundrel Delver` is the only supported planner. It plays using visible room state, current health, current weapon state, potion constraints, and carry risk, without cheating by consulting hidden future cards.
