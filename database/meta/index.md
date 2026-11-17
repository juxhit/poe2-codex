# Meta — Templates & Maintenance

> File templates for consistent entries + database maintenance rules. Changelog: [changelog.md](changelog.md)

## Templates

| Template | For |
|---|---|
| [templates/class.md](templates/class.md) | New class page (Marauder, Templar…) |
| [templates/ascendancy.md](templates/ascendancy.md) | New ascendancy page |
| [templates/boss.md](templates/boss.md) | Boss bestiary entry |
| [templates/unique-item.md](templates/unique-item.md) | Unique item page |
| [templates/mechanic.md](templates/mechanic.md) | Mechanics / crafting system page |
| [templates/passive-node.md](templates/passive-node.md) | Keystone / notable entry |

## Maintenance rules

1. **Content ownership** (no duplication):
   - `mechanics/` — rules, formulas, caps, slot limits.
   - `items/` — catalogs: bases, uniques, currency values.
   - `crafting/` — how to roll/obtain: methods, currencies, recipes.
   - `bosses/` — per-boss tactics and loot; access/progression stays in `mechanics/pinnacle-bosses.md`.
2. **Patch workflow:** changelog.md → update affected files → re-run link check → bump snapshot date in README.
3. **1.0 migration:** after Dec 11, 2026 patch notes, move `1.0/confirmed.md` facts into main sections (per changelog checklist), keep `1.0/` as archive.
4. **Uncertainty labels:** `(unconfirmed)` = single/weak source · `(open gap)` = data missing with pointer where to fetch.
5. **Anchors:** all files use `##`/`###` headers — GitHub/Obsidian anchors work (`skills/support-gems.md#general-damage--cost--utility` style) for deep links to specific gems/bosses.
