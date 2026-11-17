# Damage Calculation — Full Pipeline

> Sources: [Mobalytics — Full Order of Operations](https://mobalytics.gg/poe-2/guides/damage-defence-calc-order), [Mobalytics — Damage Conversion](https://mobalytics.gg/poe-2/guides/damage-conversion), [GGG forum — pen/res rule](https://www.pathofexile.com/forum/view-thread/3755214), [poe2db — Critical Damage Bonus](https://poe2db.tw/Critical_Damage_Bonus)

## Pipeline for a hit

1. **Avoidance roll** — Evasion, dodge-roll, hit-type avoidance first; avoided hits go no further. ("X% chance to Avoid Physical Damage from Hits" mods do NOT avoid the hit — they apply at mitigation.)
2. **Damage calculation** (six sub-steps, in order):
   1. **Flat damage** — weapon base (attacks) or gem base (spells); **Added** damage is added directly; damage effectiveness + min/max normalisation here.
   2. **Conversion & Gain-as-Extra** — two-step system, see below.
   3. **Multipliers** — all Increased/Reduced **summed additively** into one factor; all More/Less **multiplicative** with each other.
   4. **Critical strike** — one crit roll **per skill use** (all hits of one cast share the outcome); Critical Damage Bonus applied here (after increased/more); defender-side crit reduction applies here.
   5. **Damage roll** — random min–max; **Lucky/Unlucky** roll twice, take best/worst, cancel each other.
   6. **Double/Triple Damage** — hits only; Triple overrides Double.
3. **Damage Taken As** — all shifts apply simultaneously; damage shifts **only once**; shifted damage loses type-specific properties (e.g. pen); ailments use pre-mitigation hit damage.
4. **Mitigation** — immunities (CI) → avoidance → Armour + additional PDR (physical) → Fire/Cold/Light/Chaos **Resistances**. PDR and each resistance are separate layers, each **hard-capped at 90%**.
5. **Damage Taken modifiers** — flat "taken" first → Increased/Reduced taken (summed; **Shock/Wither live here**) → More/Less taken (multiplicative).
6. **Stun** → 7. **Block** (prevents hit damage, not on-hit effects) → 8. **Resource order**: redirection (totems) → wards → Guard → Energy Shield → Mana-before-Life → Life.

## Conversion — the verified PoE2 rule

**PoE2 removed PoE1's intermediate-type scaling.** Mobalytics: *"Damage does not 'remember' its origin type(s)"* — converted damage is scaled **only by its final type** (phys converted to fire scales with increased Fire, NOT increased Fire). PoE1's "stack intermediate types" technique does not work.

**Two-step system** (replaces PoE1's sequential Phys→Light→Cold→Fire→Chaos chain):

- **Step 1 — Skill conversion:** conversion/inherent gain baked into the skill gem resolves first.
- **Step 2 — Secondary conversion:** ALL non-skill sources (gear, tree, keystones like Avatar of Fire, non-skill buffs) apply **simultaneously** to Step 1's output. Steps are not additive with each other.
- **100% cap per step:** sources exceeding 100% in one step are **normalized proportionally to exactly 100%** (e.g. 100% Phys→Fire + 50% Phys→Cold → 67%/33%; Original Sin + Painter's Servant 166% → 60%/20%/20%). Damage cannot convert into its own type.
- **"Gain as Extra"** is calculated on the source damage **before it is converted away** and does **not remove** the source — conversion + gain-as-extra on the same type double-dip. Gained-as-extra damage scales only with its own (gained) type.

## Crit math

- Base **Critical Damage Bonus = +100%** (crit = 200% rolled damage; different from PoE1's +50%).
- Applied after the increased/more step; defender "reduced Critical Damage Bonus" applies here.
- Crit chance capped at 100% — excess wasted unless consumed (Amazon's excess-chance-to-hit conversion, Oracle's Forced Outcome).

## Penetration vs Resistance reduction

- **GGG official:** *"Curse + Exposure can bring an enemy's resistances below 0%. Penetration cannot affect an enemy that has 0 or lower resistances."*
- Negative res **amplifies** damage: factor `(1 − Res)`; at −60% res the enemy takes ~6.4× a 75%-res target's damage; negative floor ~−200% `(unconfirmed)`.
- Stacking: Curses/Exposure reduce the target's **uncapped** resistance (additive with each other); value is then capped [floor, 90%]; **Penetration subtracts from the still-positive value at hit time**. Multiple pen sources are additive. Pen applies to **hits only** (not DoT) and doesn't modify the monster's stat, so it can't be pre-mitigated.
- Practical: reduction (curse/exposure) is the only way into amplifying negative territory; **pen is dead weight at ≤0% res**.

## Related

- Base conversion/gain entries and examples: [damage-types.md](damage-types.md)
- Defence-side of the pipeline: [defences.md](defences.md), [life-mana-es.md](life-mana-es.md)
