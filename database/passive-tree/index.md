# Passive Tree

> Snapshot 2026-11-17, 0.5.x. 1.0 overhaul Dec 11 2026 — see [1.0/confirmed.md](../1.0/confirmed.md)
>
> Files: this overview · [keystones.md](keystones.md) (keystones + anointing/instilling)

## Navigation basics

- Tree is split into **attribute starting zones** (Str/Dex/Int/hybrids) flowing outward; clusters chain into highways and wheels.
- **Weapon Set Skill Points (WSP)**: a portion of quest rewards grant weapon-set points (25 total from campaign — see [guides/campaign-quests.md](../guides/campaign-quests.md)); they allocate passives that apply **only while that weapon set is active**. Mercenary's Witchhunter "Weapon Master" converts 100 passive points into weapon-set points.
- **Jewel sockets** sit on the tree (some in amulets); 1.0 moves sockets inside clusters (~18 highway sockets → ~60, some linking separate clusters); new keystone **Withering Disintegration**.
- Cross-tree access: Pathfinder "Path of the Sorceress"/"Path of the Warrior" unlock other classes' starting passives; Oracle "Entwined Realities"/"The Unseen Path" allocate passives near keystones from paths not taken.

## Known keystones & key notables (partial)

| Name | Effect | Note |
|---|---|---|
| Chaos Inoculation (CI) | Life set to 1, chaos immunity | ES builds |
| Zealot's Oath | Life regen applies to ES; disables recharge | |
| Eternal Youth | Life flasks recover ES | |
| Grim Feast | ES overflow up to double maximum | |
| Iron Reflexes | Evasion → Armour | |
| Acrobatics | Adds AoE to evasion coverage at a severe penalty | |
| Vaal Pact | 50% more leech, 67% less leech rate, no instant leech | reworked 0.5.0 |
| Ancestral Bond | Doubles totem limit | disables some damage `(unconfirmed)` |
| Trusted Kinship | Reworked 0.5.0 | |
| Withering Disintegration | New in 1.0 | details at launch |

Full keystone/notable catalog: `(open gap)` — pull from poe2db / [poe2db passive tree](https://poe2db.tw/us/Passive_Skill) after 1.0.

## Planning tools

- **Path of Building 2** — offline planner with full PoE2 tree: [guides/tools.md](../guides/tools.md)
- In-game .build guide export supported (0.5.0+) — see [items/misc.md](../items/misc.md)

## Structure plan (expansion)

- `keystones.md` — full keystone list with effects
- `notables/<zone>.md` — notable clusters per attribute zone
- `jewel-sockets.md` — socket-in-cluster system (1.0), Time-Lost Jewel interactions
