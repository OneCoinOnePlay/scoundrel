# Scoundrel

Play the Dungeon or run the Dungeon.

Scoundrel is a single player rogue-like card game played with a standard deck of playing cards. Fight monsters, equip weapons, drink potions, and try to clear the Dungeon with your 20 health intact.

Play in your browser: https://onecoinoneplay.github.io/scoundrel/

This browser app gives you three ways into the game:

- **Play Dungeon**: play Scoundrel manually, card by card.
- **Run Lost Trace / Run Cleared Trace**: generate example Dungeon runs to inspect how an adventurer falls or clears.
- **Estimate odds**: run adventurer simulations and compare clear rate, average clear health, loss score, and rooms faced.

Open `index.html` in a browser, or publish this folder with GitHub Pages.

## Adventurers

The adventurers are not hidden-deck solvers. They use visible game state only: the current room, health, weapon stack, potion rule, and carry-card risk.

### Scoundrel Delver

Careful play. Avoids risky carried monsters and protects health.

### Bolder Delver

Braver play. Carries more danger to preserve better rooms and weapons.

## Adventurer Results

Estimated over 10,000 adventurer runs.

| Adventurer | Setup | Clear % | Clear HP | Loss score | Rooms |
| --- | --- | ---: | ---: | ---: | ---: |
| Scoundrel Delver | Standard opening | 5.2% | 6.1 | -56.5 | 17 |
| Scoundrel Delver | Opening room must contain a Weapon | 6.5% | 6.4 | -52.1 | 17 |
| Bolder Delver | Standard opening | 5.8% | 6.8 | -54.2 | 16 |
| Bolder Delver | Opening room must contain a Weapon | 6.6% | 6.9 | -50.0 | 16 |

## Rules

Based on [Scoundrel - version 1.0, August 15th, 2011](http://stfj.net/art/2011/Scoundrel.pdf), a single player rogue-like card game by Zach Gage and Kurt Bieg.
