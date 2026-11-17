# Path of Exile 2 — Codex

**PoE2 Codex** — a bilingual (English / Русский) community knowledge database for **Path of Exile 2**, built as structured Markdown and published as a searchable documentation site.

🔗 **Live site:** [juxhit.github.io/poe2-codex](https://juxhit.github.io/poe2-codex) — language switcher (EN/РУС) in the page header.

## What's inside (snapshot 2026-11-17, patch 0.5.x)

| Section | Content |
|---|---|
| `database/classes/` | All 8 playable classes + Duelist, Shadow, Marauder, Templar (1.0/post-1.0) |
| `database/ascendancies/` | 22 ascendancies with **full passive node lists** (poe2db live data) |
| `database/mechanics/` | Combat math (damage pipeline, conversion, crits), defences, ailments, minions, trials, Atlas, league mechanics |
| `database/crafting/` | Every crafting system: orbs, essences, omens, corruption, Runeforging, fractures, 1.0 Forgemarked |
| `database/items/` | Full currency catalog, weapon/armour bases, jewelry, runes & soul cores, uniques (partial), waystones |
| `database/skills/` | Active gems by family, support gem catalog (~70 Lineage), meta gems / Energy system |
| `database/guides/` | Beginner → endgame: campaign routes & quest rewards, builds, filters, trade, settings, farming strategies |
| `database/1.0/` | Full-release tracker (Dec 11, 2026): **confirmed facts** vs **rumors/leaks**, clearly labeled |
| `database/cheatsheets/`, `database/glossary.md`, `database/lore.md` | Caps table, search regex, slang, lore overview |

Every claim carries its source (poe2db, Maxroll, Mobalytics, official forums). Unverified data is marked `(unconfirmed)` / `(не подтверждено)`; missing data `(open gap)` / `(нет данных)`.

## How the site works

- **MkDocs Material** builds the site from `database/` (config: `mkdocs.yml`).
- **GitHub Actions** (`.github/workflows/deploy.yml`) rebuilds on every push to `main` — no manual deploy steps.
- **Bilingual via mkdocs-static-i18n**: `page.md` = English, `page.ru.md` = Russian; the plugin wires the language switcher and routes links per language.

## Editing

1. Edit or add a `.md` file in `database/` (use the templates in `database/meta/templates/`).
2. `git add -A && git commit -m "..." && git push` — the site rebuilds itself.
3. Data refresh checklist after the **1.0 patch (Dec 11, 2026)**: `database/meta/changelog.md`.

## Sources

[poe2db.tw](https://poe2db.tw/us/) · [Maxroll PoE2](https://maxroll.gg/poe2) · [Mobalytics](https://mobalytics.gg/poe-2/guides) · [Fextralife wiki](https://pathofexile2.wiki.fextralife.com/) · [official forums](https://www.pathofexile.com/forum/view-forum/2212)

*Not affiliated with Grinding Gear Games. Path of Exile is a trademark of GGG.*
