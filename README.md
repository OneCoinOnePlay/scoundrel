# Scoundrel Simulator

This simulator models the 2011 `Scoundrel` ruleset and focuses on a single fair visible-state strategy: `Survivalist`.

Open `scoundrel_sim_v2.html` in a browser and press `Run simulation ->` to estimate the strategy's win rate.

## Current Baseline

The current `Survivalist` strategy is intentionally visible-state only. It uses the current room, current health, equipped weapon, weapon ceiling, potion-use state, and carry-card risk. It does not inspect the hidden dungeon order.

Local command-line probes after the strategy revision produced about a `5.4%` win rate over `10,000` simulated games. This is a material improvement over the previous roughly `0.4-1.0%` behavior, but it is still below the cited `20%` human-player expectation. Treat the remaining gap as strategy quality work, not a rules-engine validation.

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

`Survivalist` is the only supported strategy. It plays using visible room state, current health, current weapon state, potion constraints, and carry risk, without cheating by consulting hidden future cards.
