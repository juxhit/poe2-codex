# Damage Types, Conversion & Crits

> Sources: [Mobalytics damage conversion](https://mobalytics.gg/poe-2/guides/damage-conversion), [poe2db — Critical Hits](https://poe2db.tw/us/Critical_Hits), [Maxroll mechanics](https://maxroll.gg/poe2/poe2-mechanics-guide), [poewiki Luck](https://www.poewiki.net/wiki/Luck)

## Damage types

Physical · Fire · Cold · Lightning · Chaos. Elemental = Fire+Cold+Lightning.

## Conversion

- **"Converted to"** changes the type and removes the original. **PoE2 damage does not "remember" origin types** — converted damage is scaled **only by its final type** (no PoE1 intermediate-type scaling). Full two-step system and the 100%-cap normalization rule: [damage-calculation.md](damage-calculation.md).
- **"Gain X% as Extra"** is calculated on the source damage **before it is converted away** and does **not remove** the source — conversion + gain-as-extra on the same type double-dip; gained damage scales only with its own type.
- Ascendancy conversions: Invoker "I am the Thunder/Blizzard" (+10% extra), Shaman Avatar of Evolution, Infernalist Altered Flesh (damage-taken conversions).

## Critical strikes

- Base **Critical Damage Bonus = +100% extra damage** (crit deals 200% by default); modified by crit damage bonus stats. Crit chance caps at 100%.
- Crit can apply to poison DoT.
- Crit interactions: Gore Spike (Blood Mage — crit damage bonus per current Life), Amazon (crit from excess chance-to-hit), Sunder the Flesh (15% base spell crit), Oracle Forced Outcome (inevitable crits).

## Lucky / Unlucky

- **Lucky** = roll twice, take the best (for crit: roll threshold twice, keep lower number ≈ near-doubling effective crit at mid ranges).
- **Unlucky** = take the worst. Lucky and Unlucky on the same stat cancel out.
- Also applies to damage rolls and some ailment/threshold checks.
- Notables: Oracle's The Lesser Harm (enemy crit & damage vs you are Unlucky).
