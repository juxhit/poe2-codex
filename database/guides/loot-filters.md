# Loot Filters Guide

> Sources: [NeverSink-Filter-for-PoE2 (GitHub)](https://github.com/NeverSinkDev/NeverSink-Filter-for-PoE2), [FilterBlade](https://www.filterblade.xyz/), [NeverSink forum thread](https://www.pathofexile.com/forum/view-thread/3693141)

## System state

- PoE2 has a **fully supported official in-game item filter system** — custom `.filter` files load like PoE1; PoE2 also offers an **in-game filter ladder/subscription** that auto-updates (not customizable).
- Console players cannot use local files — in-game subscription/ladder only `(unconfirmed)`.

## FilterBlade

- [filterblade.xyz](https://www.filterblade.xyz/) — official NeverSink web editor for **both PoE1 and PoE2** (game selector).
- Features: strictness presets, full tier customization, styles (Aura, Cobalt, Darkmode, Mythic, Vaal, Zen…), loot simulator, Auto-Adjust, **Sync** (manual upload to account) / **Sync Auto** (continuous, Patreon premium).

## NeverSink filter for PoE2

- [GitHub: NeverSinkDev/NeverSink-Filter-for-PoE2](https://github.com/NeverSinkDev/NeverSink-Filter-for-PoE2) — economy-based tiers for currency, runes, soul cores, essences, uniques; campaign leveling mode switches to endgame rules at area level 65; pink/cyan notifications warn when outdated.
- **7 strictness levels:** Soft, Regular, Semi-Strict, Strict, Very-Strict, Uber-Strict, Uber-Plus-Strict. Updated 4–6h before league starts, then ~monthly.

## Setup (PC, step by step)

1. **Get a filter** — filterblade.xyz → pick PoE2 + strictness → Download; or GitHub releases zip.
2. **Place the file** — copy `.filter` into:
   - Windows: `%userprofile%\Documents\My Games\Path of Exile 2`
   - Linux/Proton: `steamapps/compatdata/2694490/pfx/drive_c/users/steamuser/My Documents/My Games/Path of Exile 2`
   - NOT the `onlinefilters` subfolder.
3. **Activate** — Escape → Options → Game → Filters → select your filter.
4. **Update** — re-download per league/patch, or use FilterBlade Sync / in-game ladder subscription.

## Recommended strictness

| Stage | Preset |
|---|---|
| Leveling (1–65) | **Soft or Regular** (never Very Strict while leveling) |
| Early endgame | **Semi-Strict** (recommended beginner default) |
| Established endgame farming | **Strict → Very Strict** |
| Ultra farming (extreme volume) | **Uber-Strict / Uber-Plus-Strict** |
