# Defences

> Sources: [Maxroll defence guide](https://maxroll.gg/poe2/getting-started/defence-guide), [Mobalytics armour/evasion/block](https://mobalytics.gg/poe-2/guides/block), [myrtana wiki](https://www.myrtana.net/en/path-of-exile-2/wiki/mechaniky/block)

## Armour

**Damage Reduction = Armour / (Armour + 12 × Damage of the hit)**, hard-capped at **90%** (Mobalytics lists constant 10 — `(unconfirmed)` which is current).

Breakpoints vs a 100-damage hit:

| Armour | Reduction |
|---|---|
| 600 | 33% |
| 1,200 | 50% |
| 2,400 | 66% |
| 3,600 | 75% |
| 10,800 | 90% |

- Most effective vs small hits; large hits bypass most of it. ~20,000 armour fully mitigates single hits up to ~1/5 of its value.
- Armour applies to Physical by default; extends to elements/chaos via ascendancies (Flowing Metal, Dedication to Kitava, Panther Idol, Stay Light Use Cover).

## Evasion

- Community formula: **Chance to Evade = (1 − (Attacker Accuracy × 1.25) / (Attacker Accuracy + Defender Evasion × 0.3)) × 100** — constants `(unconfirmed)`.
- Hard cap **95%** (always ≥5% chance to be hit). Deterministic **entropy** system — hits guaranteed at intervals, not per-hit RNG.
- Applies to **Strikes and Projectiles only**, not AoE (Acrobatics adds AoE evasion at a severe penalty).
- **Iron Reflexes** converts evasion to armour.

## Block & Parry

- **Passive block:** roll-based chance; default cap 75%, hard cap 90%. Blocked hits prevent the hit's ailments. Blocks Strikes/Projectiles; since 0.3 shields block **all** hits including AoE.
- **Active block / Parry:** held directional block, or timed Parry window — guaranteed block, 100% damage prevention, staggers the enemy (narrow window, can't be held).
- **Stagger meter:** blocking and being hit fill your own Heavy Stun bar — full bar while passively blocking = heavy stunned. Core risk/reward of shield play (Warrior's mechanic).

## Deflection (Tactician)

- Deflect pool scaled off **Deflection rating**, which scales with **Armour** — armour stacking strengthens deflection. Synergizes with armour-stacking and Pin builds. See [ascendancies/tactician.md](../ascendancies/tactician.md).

## Resistances

- Default cap **75%**; "Maximum Resistance" modifiers raise the cap up to **90%**.
- Campaign applies **−10% all elemental res per completed Act** — **−40%** by end of Act 3 Cruel; with permanent +20% Fire/Cold/Lightning act rewards you need ~**115%** per element (and 75% chaos) to be capped.
- Unresisted 100 damage at 75% res → 200 at 50%.
- Smith of Kitava: Coal Stoker/Forged in Flame convert fire res mods to all elements.
