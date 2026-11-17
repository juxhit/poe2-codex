# Buffs, Curses, Marks, Shrines & Rare Monster Mods

> Sources: [Mobalytics — Curses](https://mobalytics.gg/poe-2/guides/curses), [Mobalytics — Shrines](https://mobalytics.gg/poe-2/guides/shrines), [poe2db — Monster Modifiers](https://poe2db.tw/us/Monster_Modifiers), [Fextralife — Blasphemy](https://pathofexile2.wiki.fextralife.com/Blasphemy), official 0.5.0 notes. Ailments: [ailments.md](ailments.md) · Control states: [stun-and-control.md](stun-and-control.md)

## Curses

- **Limit: 1 curse per enemy** by default; a second curse replaces the oldest. Limit raised by rare modifiers (Doedre's Damning ring, Whispers of Doom-type notables — often with downsides); Lich's Incessant Cacophony grants +1 — see [ascendancies/lich.md](../ascendancies/lich.md).
- **Innate curse-effect reduction by rarity:** Magic **15%** / Rare **30%** / Unique & all bosses (incl. Pinnacle) **50%** `(Mobalytics PoE2 figures; no separate Pinnacle tier documented)`.
- **1.5s activation delay** by default (reducible; removed by Windscream).
- **Blasphemy** turns socketed curses into auras, reserves **60 Spirit per curse**; Blasphemy curses count toward the limit (Blasphemy + a second cast curse won't both apply at limit 1). Hexproof monsters immune to effects; Soul Mantle self-curses bypass your limit.
- Curse payoffs: Lich (Rupture the Soul, Necromantic Conduit), Ritualist, Hexblast, Whispers of the Flesh.

## Marks

- **Separate category — do NOT count toward the curse limit**; Blasphemy doesn't apply to them. One mark at a time `(inferred)`.
- In-game marks: Sniper's Mark, Voltaic Mark, Freezing Mark, Bloodhound's Mark — see [skills/skill-gems.md](../skills/skill-gems.md); Deadeye's Bullseye consumes them.

## Notable buff one-liners

| Buff | Effect |
|---|---|
| **Onslaught** | Increased attack/cast/movement speed (~10–20% class) |
| **Unholy Might** | Converts 100% of Phys to Chaos + 25% chance to inflict Withered on hit (current patch text) |
| **Tailwind** | Stacking: ≈1% move speed, 2% skill speed, 10% evasion, prevents 1% damage per stack `(values unconfirmed)` |
| **Arcane Surge** | After spending enough mana: cast speed + mana regen; scalable effect |
| **Adrenaline** | Speed + damage + phys reduction; doesn't stack, refreshes duration `(0.5.x values unconfirmed)` |
| **Rage** | Stacking, 1% more Attack Damage per stack |
| **Berserk** | Short warcry buff (~1.5s): melee damage + rage gains |
| **Empowerment** | Warcry-empowered attacks; notables scale their damage |

## Shrines (maps)

- Spawn in waystone maps; **buff nearby monsters until claimed** (Divine guardians unkillable until claimed). Buffs stack; **base duration 45s**; reapplied in the boss arena. Map mods: "Rites of the Rogues" (+2 shrines), "of the Devoted" (+1). 0.5.0: lowered spawn chance, buffed Atlas nodes, **halved the "Damage as Extra" buffs**.
- 0.5.0 lowered spawn chance, buffed Atlas shrine nodes.

| Shrine | Effect (45s) |
|---|---|
| Acceleration | +60% Skill Speed, +40% Move Speed |
| Diamond | Always Crit |
| Enlightening | +100% XP |
| Massive | +50% max Life, +100% global defences |
| Replenishing | Regen 10% Life & Mana per second |
| Resistance | +50% Ele Res, +10% all Max Res |
| Seeking | +100% Item Rarity |
| Freezing | +50% Damage as Extra Cold + icicles (halved) |
| Meteoric | +50% Extra Fire + meteors (halved) |
| Tempest | +50% Extra Lightning + bolts (halved) |
| Gloom | +25% Extra Chaos + corpse explosions (halved) |
| Divine | Cannot be Damaged (god mode) |

## Rare monster modifiers (dangerous ones)

Rares carry **2–4 affixes**; more affixes = more power and rewards. PoE1 names (Mana Siphoner, Arcane Buffer) don't exist as such — full list: [poe2db — Monster Modifiers](https://poe2db.tw/us/Monster_Modifiers). Highlights:

**Offense:** Extra Fire/Cold/Light/Chaos (40% as extra) · Extra Crits (300% increased crit chance) · Accurate (200% accuracy) · Always Poisons/Bleeds · All Damage Ignites/Chills/Shocks · Additional Projectiles (+4) · +100% more AoE · +100% Stun Buildup · **Breaks Armour (1000% of phys dealt)** · Empowered (+50% life, +25% damage)

**Defence:** Armoured/Evasive/Extra ES · Cannot be Stunned · +50% res +10% max res per element · **Crit Resistant (−80% crit damage bonus vs it)** · Regenerates 2%/s · Hasted · **Temporal Bubble** (only damageable inside its radius) · **Proximal Tangibility** (ignores its own cannot-be-damaged restriction — notorious trap)

**Auras/debuffs:** Haste Aura · ES Aura · Ele Res Aura · Hinder Aura · **Periodic Invulnerability Aura** · **Prevents Recovery Above 50%** (the Arcane-Buffer analog) · Heals Allies & Suppresses Recovery

**Death effects:** Burning/Chilled/Shocked Ground on Death · elemental Explosion on Death · periodic explosions · trails of Fire/Ice/Lightning · Lightning Mirages when hit · boss-tier demises (Meteoric Demise, Kulemak's Desecration…)

**One-shot family (summoned objects):** **Volatile Crystals / Volatile Plants / Volatile Crag (empowered)** — exploding orbs, the classic one-shotter · Volatile Souls (Abyss) · Magma Barrier · Ice Prisons · Flamewalls · Lightning Storms · Soulflame Geysers · Lithomantic Runes · Crystalline Barrier (Abyss)

**Siphons/utility:** **Siphons Mana + deals Lightning** · **Siphons Flask Charges** · Soul Eater · Soul Siphoner · Periodically Enrages · **Damage Taken From Minions First** · Undying Will (culling/decimating strikes, indestructible corpse) · Curse/Shock Reflection (20–60%)

**Community-flagged lethal combos:** volatile objects + fast aura packs; Siphons Mana + projectile rares; Periodic Invulnerability + Heals Allies; Proximal Tangibility + Temporal Bubble.
