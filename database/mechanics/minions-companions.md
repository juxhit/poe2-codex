# Minions & Companions — System Rules

> Sources: [poe2db — Reviving Minions](https://poe2db.tw/us/Reviving_Minions), [poe2db — Bind Spectre](https://poe2db.tw/us/Bind_Spectre), [poe2db — Tame Beast](https://poe2db.tw/us/Tame_Beast), [poe2db — Minion Commands](https://poe2db.tw/us/Minion_Commands), [poe2spectrewiki](https://poe2spectrewiki.com), [Mobalytics companions](https://mobalytics.gg/poe-2/guides/companions-tame-beast). Spirit basics: [spirit.md](spirit.md) · Minion gems catalog: [skills/skill-gems.md](../skills/skill-gems.md)

## Categories

| Type | Behavior |
|---|---|
| **Persistent** | Reserves Spirit; toggled in Skills Panel like a buff |
| **Reviving** | Sub-flag: auto-revive after a delay when killed (skeleton base: 12s) |
| **Temporary** | Created by an active cast, expire on duration, no Spirit |
| **Companions** | Only **1 companion of each type**; right-click toggles (Wolf Pack, Tame Beast, Rhoa Mount) |

- **Revive delay** resets when another Reviving minion dies (community: no revive if one died within ~7.5s `(unconfirmed)`).
- Revive-speed modifiers: Necromantle (50% faster), Heartbound Loop (10–15%), Skeletal Cleric active revive, **Eternal March** (Kalguuran skill — instant revive via Runic Ward), Grim Feast → Grim Resurrection.

## Spirit reservation per minion skill

Reservation **decreases with gem level**:

| Skill | Spirit (L1→L20) | Note |
|---|---|---|
| Skeletal Warrior | 60 → 20 | First 2 have **no base reservation** |
| Skeletal Cleric | 60 → 20 | Healer/reviver |
| Skeletal Arsonist | 90 → 39 | Detonates minions via Command |
| Bind Spectre | bind cost 22–99 Mana; then **flat Spirit by monster power** (~29 Bloodthief Wasp → ~154 Terracotta Soldier) | Gem permanently transforms into that monster |
| Tame Beast | percentage-based (varies with captured mods) | `(unconfirmed exact %)` |
| Other Reaver/Brute/Frost/Storm Mage | same decreasing pattern | `(unconfirmed numbers)` |

- Reservation math: 50% increased Reservation Efficiency → 67% cost; 100% → 50%. Supports: Hulking Minions (+130% cost, big stats), Gigantic Following (−25%); **Atziri's Communion** reserves Life instead of Spirit but can't support minion-creating skills.

## Command skills

- Commandable minions (crown icon) grant **Command skills** — you cast them, the minion executes (Move/Attack + specials: Arsonist Explosive Demise, Reaver enrage, Brute warcry, Frost Mage shield, Storm Mage strike, Mist Raven dive, Tactician Supporting Fire; **Djinn do nothing unless commanded**).
- Commands cost **Mana, not Spirit**; scale with Cooldown Recovery.
- Supports: **Bidding I–III** (command CDR), **Commandment** (huge CDR, minions deal no damage with non-Command skills). Payoffs: Idol of the Pharisee, Rabbit Idol (+30% CDR), Xipocado's Soul Core of Dominion, Archon of Undeath (200% more command CDR).

## Bind Spectre

- Tier 7 Int gem; **target a corpse** — gem permanently transforms into that monster's summon; **disenchanting unbinds** for reuse (0.2.0e).
- Minion level = gem level + 1 (L40 at gem 20); quality = 0–20% more Minion Damage + 0–20% Reservation Efficiency.
- Pool: ~600+ bindable monster types (normal/magic/rare; bosses not bindable `(unconfirmed)`). Full cost/type list: [poe2spectrewiki.com](https://poe2spectrewiki.com).

## Tame Beast (Huntress)

- Tier 7 Dex gem; **Rare Beast monsters only**; applies Hinder (30%), kill inside capture window (**8s at L1 → 11.8s at L20**). Gem transforms into a Companion summoning the beast (Reviving); **beast keeps up to 4 of its modifiers**.
- **Spirit Walker's The Natural Order**: tames **Unique Beasts / map bosses** (one allowed; possessed by cycling Azmeri spirits) — see [ascendancies/spirit-walker.md](../ascendancies/spirit-walker.md).
- 0.5.0: beasts deal 40% more damage at L9 → 84% at L20.

## Companion slot limits

- Default **1**; **Trusted Kinship** keystone +1; Yriel's Fostering (unique body armour) → 2; "Easy Going" notable −30% companion reservation.

## What scales minions

- **Only modifiers explicitly tagged "Minion"/"Companion"/"Ally" apply** — generic player "increased damage" does **not** transfer. (Reported exception: flat "Adds X Fire/Cold/Lightning" on gear may benefit some minions `(unconfirmed)`.)
- Priority order for gearing: **+X to Level of all Minion Skills** → **Spirit** (more/cheaper minions) → **% Minion Damage**.
- Meta sceptre target (0.5): Rattling Sceptre, +4 Minion Skills, 150–160+ Spirit, Minion Damage, command mods.
