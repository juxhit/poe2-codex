# Life, Mana, Energy Shield

> Sources: [Maxroll defence guide](https://maxroll.gg/poe2/getting-started/defence-guide), [Mobalytics](https://mobalytics.gg/poe-2/guides/armour)

## Life

- **+12 max Life per character level**; **+2 max Life per point of Strength**.
- Life can overflow to double maximum via specific effects (e.g. Sanguimancy interactions).
- Campaign act rewards add permanent Life along the way.

## Mana

- Baseline regen: **4% of maximum Mana per second**.
- **+2 max Mana per point of Intelligence**.
- Mana can overflow to double max (Mana Remnants interactions).
- Notable mana-defense nodes: Force of Will (Stormweaver), Varashta's Intuition (Disciple of Varashta), Harmony Within (Oracle), Necromantic Conduit (Lich) — see [ascendancies/](../ascendancies/).

## Energy Shield (ES)

- Protects against all damage **except Bleed and Poison** (they bypass ES directly to Life).
- **Chaos damage removes 2× ES per point of damage.**
- **Recharge** begins after a delay once damage stops; recharge rate is a separate stat (Disciple of Varashta's Fourth Teaching, Martial Artist Combo interactions).
- Key notables: **Grim Feast** (overflow up to double maximum), **Zealot's Oath** (life regen applies to ES, disables recharge), **Eternal Youth** (Life flasks recover ES), **Chaos Inoculation** (Life set to 1, chaos immunity).

## Runic Ward (0.5.0+)

- Secondary pool from **Runeforging** ([crafting/runeforging.md](../crafting/runeforging.md)): activates only when Life reaches 0, absorbs damage, regenerates steadily.
- Applied to armour at the Verisium Anvil; 0 by default.

## Damage-taken math

- "Reduced"/"taken" modifiers are **additive** — three 20% sources = 60% total.
- "**Less**" modifiers are **multiplicative** — three 20% less = 48.8% total (0.8³).
- Damage "taken as" an element benefits from that element's resistance (e.g. Molten Symbol 25% phys-as-fire).
