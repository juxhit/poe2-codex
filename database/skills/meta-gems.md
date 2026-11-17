# Meta Gems & the Energy System

> Sources: [Mobalytics Meta Gems guide](https://mobalytics.gg/poe-2/guides/meta-gems), poe2db tooltips. Catalog position: [skills/index.md](index.md)

## How Meta gems work

- Meta gems are Skill Gems whose sockets hold **other skill gems**; most reserve **Spirit** (persistent) and are trigger-based.
- Trigger meta gems accumulate **Energy** when their condition occurs; on reaching **Maximum Energy**, all socketed spells fire automatically and Energy resets. You still pay the socketed spells' mana costs.
- **Maximum Energy scales with combined base cast time of socketed spells** (e.g. Cast on Critical: 10 max Energy per 0.1s socketed cast time) — pair fast triggers with slow, expensive spells.
- **Enemy Power** scaling: monster difficulty (~0.5–3) × rarity multiplier (Normal ×1, Magic ×2, Rare ×5, Unique ×20); many triggers gain Energy per Power.
- Socketed skills typically carry a damage penalty (e.g. Cast on Critical: socketed skills deal 20% less damage).
- Supports socket into Meta gems where applicable; Meta-only supports: Energy Retention, Boundless Energy I/II, Energy Capacitor — see [support-gems.md](support-gems.md).

## Trigger meta gems

| Gem | Lvl | Energy generation |
|---|---|---|
| Cast on Minion Death | 8 | 50 base Energy per Persistent Minion killed, modified by minion Power |
| Cast on Critical | 14 | 1 Energy per Power of critically-hit enemies (socketed −20% damage) |
| Cast on Elemental Ailment | 14 | 10/Power on Freeze, 1/Power on Shock and Ignite |
| Cast on Dodge | 14 | 2 Energy per metre dodge-rolled |
| Elemental Invocation | 8 | Energy on Freeze/Shock/Ignite; manual Invocation also triggers |
| Barrier Invocation | 8 | Invocation; reserves 60 Spirit (block-based `(unconfirmed)`) |
| Reaper's Invocation | 14 | Energy per melee kill; manual Invocation (max 500 Energy) |
| Spellslinger | 1 | Item-inherent; Energy from casting spells |
| Feral Invocation | 14 | 1 Energy per 20 Mana spent; visages use socketed Shapeshift skills |

## Non-trigger (manual/utility) meta gems

| Gem | Lvl | Effect |
|---|---|---|
| Mirage Archer | 8 | Dodge roll → Mirage uses socketed ranged attacks (30% less damage) |
| Blasphemy | 8 | Socketed Curses become auras (60 Spirit each) |
| Ancestral Warrior Totem | 13 | 3 Endurance Charges → totem uses socketed Mace skills |
| Mortar Cannon | 11 | Totem uses socketed Grenade skills |
| Spell Totem | 7 | 3 Charges → totem uses socketed Spells |
| Hand of Chayula | 9 | Strike triggers socketed Marks/Curses with increased effect |
| Animus Splinters | 1 | Spend Runic Ward → clone uses socketed skill |

## Unique-granted meta gems

Cast on Block · Cast on Charm Use · Fire Spell on Hit · Thundergod's Wrath · Called Shots · Mirage Deadeye · Hollow Form · Spirit Vessel.

## Design notes

- CoC-style builds pair a fast trigger (low threshold) with a slow expensive spell; Energy thresholds auto-balance by cast time.
- The 1.0 support rebalance ("gems adapt to the supported skill") touches this system — refresh after Dec 11, 2026 — see [1.0/confirmed.md](../1.0/confirmed.md).
