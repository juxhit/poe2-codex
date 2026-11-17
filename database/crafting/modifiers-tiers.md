# Modifier Tiers & ilvl Cheat Sheet

> What's documented vs `(open gap)` — full tier tables from [poe2db modifier index](https://poe2db.tw/us/Modifiers). Template: [../meta/templates/mechanic.md](../meta/templates/mechanic.md)

## Structure

- Rares: max **6 explicit mods — 3 prefixes + 3 suffixes**; Magic: 1+1; Normal: 0 — see [currency-crafting.md](currency-crafting.md).
- Each base type carries an **implicit**; Runemastered bases (Lv65) get multi-implicits — see [items/rarity.md](../items/rarity.md).
- Slot-shifters (Dusk/Gloam/Penumbra/Tenebrous rings/amulets) trade prefix vs suffix allowance.

## ilvl gates (known)

| Gate | Requirement |
|---|---|
| Greater currency on target | item mods min level **35** |
| Perfect currency on target | item mods min level **50** |
| Greater Transmutation/Augmentation | add mods of min level **44** (was 55), drop from Act 4 |
| Runic Ward free application | armour **ilvl < 55** (above trades base defences) |
| Veridical Chain / Runemastered bases | Lv65 |
| Fracturing Orb | Rare with **4+ explicit mods** |
| Exalted Orb | Rare only |

## Tier system (rules)

- Higher item level unlocks higher modifier tiers (numeric ranges widen per tier).
- **Divine Orb** rerolls values within the current tier's range — it cannot upgrade a tier.
- **Hinekora's Lock** previews the next currency outcome (deterministic check before committing).
- Essences/Alloys force guaranteed mods scaled by essence tier (Lesser→Perfect) — see [essences.md](essences.md), [runeforging.md](runeforging.md).

## Numeric tier tables

`(open gap)` — PoE2 publishes per-mod tier ranges on poe2db per item class; build the tables per-slot (weapon/armour/jewellery) as a follow-up, ideally after the 1.0 mod rework (Dec 11, 2026).
