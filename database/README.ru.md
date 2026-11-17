# Path of Exile 2 — Codex

**PoE2 Codex** — двуязычная (английская/русская) база знаний сообщества по **Path of Exile 2** в структурированном Markdown: страницы классов, полные списки узлов восхождений, математика боя и крафта со источниками, каталоги предметов и валюты, практические гайды и отдельная ветка релиза 1.0 (подтверждённые факты vs слухи). Доступна на GitHub Pages: [juxhit.github.io/poe2-codex](https://juxhit.github.io/poe2-codex) — переключение языка в шапке страницы.

**Как пользоваться:** начните с [game.md](game.md) и [классов](classes/); механики — в [mechanics/](mechanics/); таблицы на один экран — в [cheatsheets/](cheatsheets/). У каждого утверждения указан источник; непроверённые данные помечены.

- **Снимок данных:** 2026-11-17 (эпоха патча 0.5.x "Return of the Ancients")
- **Полный релиз 1.0:** 11 декабря 2026 — подробности в [1.0/confirmed.md](1.0/confirmed.md), слухи в [1.0/rumors.md](1.0/rumors.md)
- **Источники:** [poe2db.tw](https://poe2db.tw/us/), [Maxroll PoE2](https://maxroll.gg/poe2), [Fextralife wiki](https://pathofexile2.wiki.fextralife.com/), [Mobalytics](https://mobalytics.gg/poe-2/guides), официальные [форумы pathofexile.com](https://www.pathofexile.com/forum/view-forum/2212)
- Непроверённая или спорная информация помечена `(не подтверждено)`; отсутствующие данные — `(нет данных)`.

## Оглавление

| Раздел | Файлов | Статус |
|---|---|---|
| [Обзор игры](game.md) | 1 | заполнено |
| [Классы](classes/) | 9 | заполнено (8 играбельных + будущие) |
| [Вознесения](ascendancies/) | 22 | заполнено (полные списки узлов, 0.5.x) |
| [Механики](mechanics/index.md) | 21 | заполнено (бой, расчёт урона, баффы/проклятия, приспешники, эндгейм, лиги, испытания, торговля) |
| [Крафт](crafting/index.md) | 14 | заполнено (все системы + тиры модов + 1.0) |
| [Предметы](items/index.md) | 14 | заполнено (валюта, базы, уникальные предметы частично) |
| [Умения](skills/index.md) | 5 | заполнено (все семейства, поддержки, мета-камни) |
| [Гайды](guides/index.md) | 19 | заполнено (новичок → эндгейм, режимы, настройки, торговцы, фарм, кладовая) |
| [Боссы](bosses/index.md) | 3 | заполнено (боссы актов + тактики/лут пинаклов) |
| [Дерево пассивок](passive-tree/index.md) | 2 | заполнено (основы + keystones частично) |
| [Шпаргалки](cheatsheets/index.md) | 3 | заполнено (таблица капов, regex) |
| [Релиз 1.0](1.0/confirmed.md) · [Слухи и утечки](1.0/rumors.md) | 2 | заполнено |
| [Глоссарий](glossary.md) | 1 | заполнено |
| [Лор](lore.md) | 1 | заполнено (кратко) |
| [Лиги / история патчей](leagues/index.md) | 1 | заполнено (хронология) |
| [Мета](meta/index.md) | 8 | шаблоны + changelog + правила сопровождения |

## Правила владения контентом (без дублирования)

- **mechanics/** — правила, формулы, капы, лимиты слотов.
- **items/** — каталоги: базы, уникальные предметы, стоимости валюты.
- **crafting/** — как получить/скрафтить: методы, валюты, рецепты.
- **bosses/** — тактики и лут по каждому боссу; доступ/прогрессия живут в `mechanics/pinnacle-bosses.md`.
- **1.0/** — архив предрелизных фактов/слухов; после патча Dec 11, 2026 проверенные факты переносятся в основные разделы (чек-лист в [meta/changelog.md](meta/changelog.md)).
- **Анкоры:** все файлы используют заголовки `##`/`###` — глубокие ссылки вида `skills/support-gems.md#system-rules` работают на GitHub/Obsidian.

## Классы вкратце (0.5.x — 8 играбельных)

| Класс | Характеристики | Вознесения |
|---|---|---|
| [Warrior](classes/warrior.md) | Str | Titan, Warbringer, Smith of Kitava |
| [Monk](classes/monk.md) | Dex/Int | Invoker, Acolyte of Chayula, Martial Artist |
| [Sorceress](classes/sorceress.md) | Int | Stormweaver, Chronomancer, Disciple of Varashta |
| [Mercenary](classes/mercenary.md) | Str/Dex | Witchhunter, Gemling Legionnaire, Tactician |
| [Ranger](classes/ranger.md) | Dex | Deadeye, Pathfinder |
| [Witch](classes/witch.md) | Int | Infernalist, Blood Mage, Lich (+ вариант Abyssal Lich) |
| [Huntress](classes/huntress.md) | Dex | Amazon, Ritualist, Spirit Walker |
| [Druid](classes/druid.md) | Str/Int | Shaman, Oracle |
| [Future](classes/future-classes.md) | — | Duelist + Shadow (1.0), Marauder, Templar (после 1.0) |

Цель эндгейма: **12 классов / 36 вознесений** через пост-релизный ритм лиг (~4 месяца).

## Заметки об обновлении данных

- Обновите списки узлов вознесений, валюту и уникальные предметы после **патча 1.0 (Dec 11, 2026)** — чек-лист в [meta/changelog.md](meta/changelog.md).
- Известные открытые пробелы: полный список keystones/notables, названия базовых типов брони, полные тултипы камней поддержки, полные таблицы Soul Core/идолов, таблицы тиров модов, варианты Timeless Jewel.
