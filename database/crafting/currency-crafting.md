# Currency Crafting

> Sources: [Mobalytics currency guide](https://mobalytics.gg/poe-2/guides/currency-guide), [Maxroll how-to-craft](https://maxroll.gg/poe2/resources/how-to-craft-in-path-of-exile-2), [Maxroll 0.5.0 notes](https://maxroll.gg/poe2/news/0-5-0-patch-notes-return-of-the-ancients)

## Modifier slots per rarity

| Rarity | Explicit mods |
|---|---|
| Normal | 0 |
| Magic | max 2 (1 prefix + 1 suffix) |
| Rare | max 6 (3 prefixes + 3 suffixes) |
| Unique | cannot be altered by normal crafting orbs |

## Core orbs

| Currency | Effect |
|---|---|
| Orb of Transmutation | Normal → Magic with 1 modifier. 10 Transmutation Shards (disenchant Magic items) = 1 Orb. |
| Orb of Augmentation | Adds a random modifier to a Magic item. |
| Orb of Alchemy | Normal → Rare with 4 modifiers. Rarer than PoE1. |
| Regal Orb | Magic → Rare, adds 1 modifier. 10 Regal Shards (disenchant Rares) = 1 Orb. |
| Exalted Orb | Adds a random modifier to a Rare (up to 6 total). |
| Chaos Orb | Removes one random modifier, adds a new random one (Rare). |
| Orb of Annulment | Removes one random modifier. |
| Divine Orb | Rerolls numeric values within the modifier's tier range. High-value trade currency. |
| Orb of Chance | Normal item → random Unique of that base, or destroys it. 10 Chance Shards (disenchant Uniques) = 1 Orb. |
| Vaal Orb | Corrupts an item unpredictably — see [corruption.md](corruption.md). |
| Mirror of Kalandra | Duplicates a non-Unique item. Rarest currency in the game. |
| Greater / Perfect orbs | Higher tiers of Transmutation/Augmentation/Exalted etc. — guarantee min mod tiers; 0.5.0 made them rarer; Greater Transmutation/Augmentation min mod level 44 (was 55), drop from Act 4. |
| Fracturing Orb | Permanently locks one random explicit mod on a Rare with 4+ mods — see [fractured-desecration.md](fractured-desecration.md). |
| Hinekora's Lock | Previews the exact outcome of the next currency applied (deterministic crafting). |

## Support gem sockets (PoE2's replacement for links)

| Currency | Effect |
|---|---|
| Lesser Jeweller's Orb | Guarantees a skill gem has 2 support sockets (guaranteed Act 3 drop) |
| Greater Jeweller's Orb | Gem with 3 support sockets |
| Perfect Jeweller's Orb | Gem with 4 support sockets |

## 0.5.0 rarity/drop changes

- Greater/Perfect currencies made rarer; Transmutation and Augmentation significantly rarer; **Divine Orbs more common**.
- Corruption/"Sanctify" outcomes now **multiply modifier values** rather than randomising fresh ones.

## The standard loop

1. White base → **Transmutation** (Magic, 1 mod) → **Augmentation** (fill 2nd slot).
2. Evaluate; **Regal** to Rare (+1 mod).
3. **Exalted** spam up to 6 mods, using Omens to control prefix/suffix — see [omens.md](omens.md).
4. Fix mistakes with **Chaos** (replace a mod), **Annulment** (remove), or start over.
5. Finish with **Divine** (reroll numbers), quality currency, runes/sockets, then **Vaal last**.
- Higher-tier loop substitutes Greater/Perfect orbs and essences — see [essences.md](essences.md).
