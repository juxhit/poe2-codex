# Regex for Search Fields

> Sources: [Mobalytics regex guide](https://mobalytics.gg/poe-2/guides/regex), [Reddit waystone regex](https://www.reddit.com/r/PathOfExile2/comments/1nnh105/some_useful_regular_expressions_for_waystone), [poe2.re generator](https://poe2.re/waystone)

## Where regex works

Vendor inventories · stash tabs · passive tree (Ctrl+F) · atlas tree · hideout lockers · **waystone/tablet/relic reroll windows** (keep the search active).

## Syntax

- Wrap in `" "`; **`|`** = OR; **`!`** as separate quoted term = NOT (`"!quiver"`).
- Multiple quoted terms AND together. Partial words match (`sbo` matches Crossbow).
- ~50-char limit noted `(unconfirmed if still current)`.

## Ready-made strings

**Leveling vendor (crossbows, move speed, attack mods):**
```
"sbo|ent sp|to att"
```
with quiver exclusion:
```
"!quiver" "sbo|ent sp|to att"
```

**Waystone implicits:**
```
"m.+e:"     Magic Monsters line
"ma.+s:"    Rare Monsters line
"r.+s:"     Item Rarity line
```
Rarity ≥10%:
```
"m rar.*([1-9].|\d..)%"
```

**Filter-out bad waystones:** use the generator — [poe2.re/waystone](https://poe2.re/waystone) (tip: set min/max **revives to 0** to find 6+ modifier waystones — revive-charge implicits eat implicit slots).
