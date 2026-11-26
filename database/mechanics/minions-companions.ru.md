# Миньоны и компаньоны — системные правила

> Источники: [poe2db — Reviving Minions](https://poe2db.tw/us/Reviving_Minions), [poe2db — Bind Spectre](https://poe2db.tw/us/Bind_Spectre), [poe2db — Tame Beast](https://poe2db.tw/us/Tame_Beast), [poe2db — Minion Commands](https://poe2db.tw/us/Minion_Commands), [poe2spectrewiki](https://poe2spectrewiki.com), [Mobalytics companions](https://mobalytics.gg/poe-2/guides/companions-tame-beast). Основы Духа (Spirit): [spirit.md](spirit.md) · Каталог гемов миньонов: [skills/skill-gems.md](../skills/skill-gems.md)

!!! tip "Приоритет экипировки"
    **+X к уровню всех умений миньонов** → **Spirit** (больше/дешевле миньонов) → **% Minion Damage**. Применяются только моды с явной пометкой Minion/Companion/Ally — общий урон игрока не переносится.

## Категории

| Тип | Поведение |
|---|---|
| **Persistent** | Резервирует Дух (Spirit); включается в панели умений как бафф |
| **Reviving** | Подфлаг: авто-возрождение после задержки при убийстве (база скелетов: 12 с) |
| **Temporary** | Создаётся активным применением, исчезает по окончании длительности, без Духа |
| **Companions** | Только **1 компаньон каждого типа**; переключаются правой кнопкой (Wolf Pack, Tame Beast, Rhoa Mount) |

- **Задержка возрождения** сбрасывается, когда умирает другой Reviving-миньон (сообщество: возрождения нет, если один умер в пределах ~7.5 с `(не подтверждено)`).
- Модификаторы скорости возрождения: Necromantle (на 50% быстрее), Heartbound Loop (10–15%), активное возрождение Skeletal Cleric, **Eternal March** (умение Kalguuran — мгновенное возрождение через Runic Ward), Grim Feast → Grim Resurrection.

## Резервирование Духа по умениям миньонов

Резервирование **уменьшается с уровнем гема**:

| Умение | Дух (Spirit) (L1→L20) | Примечание |
|---|---|---|
| Skeletal Warrior | 60 → 20 | Первые 2 — **без базового резервирования** |
| Skeletal Cleric | 60 → 20 | Лекарь/возрождатель |
| Skeletal Arsonist | 90 → 39 | Детонирует миньонов через команду |
| Bind Spectre | цена bind 22–99 Маны; затем **плоский Дух по силе монстра** (~29 у Bloodthief Wasp → ~154 у Terracotta Soldier) | Гем навсегда превращается в этого монстра |
| Tame Beast | в процентах (зависит от модов пойманного) | `(не подтверждено точное %)` |
| Прочие Reaver/Brute/Frost/Storm Mage | та же убывающая схема | `(не подтверждено числа)` |

- Математика резервирования: 50% увеличение Reservation Efficiency → 67% стоимости; 100% → 50%. Камни поддержки: Hulking Minions (+130% стоимости, крупные статы), Gigantic Following (−25%); **Atziri's Communion** резервирует Жизнь вместо Духа (Spirit), но не может поддерживать умения, создающие миньонов.

## Умения команд

- Управляемые миньоны (иконка короны) дают **умения команд** — кастуете вы, исполняет миньон (Move/Attack + спецприёмы: Explosive Demise Арсониста, enrage Reaver, warcry Brute, щит Frost Mage, удар Storm Mage, пике Mist Raven, Supporting Fire Tactician; **Djinn ничего не делают без команды**).
- Команды стоят **Ману, не Дух**; масштабируются с Cooldown Recovery.
- Камни поддержки: **Bidding I–III** (CDR команд), **Commandment** (огромный CDR, миньоны не наносят урон не-командными умениями). Выгоды: Idol of the Pharisee, Rabbit Idol (+30% CDR), Xipocado's Soul Core of Dominion, Archon of Undeath (200% больше CDR команд).

## Bind Spectre

- Гем Int 7 тира; **прицелитесь на труп** — гем навсегда превращается в призыв этого монстра; **распыление отвязывает** для повторного использования (0.2.0e).
- Уровень миньона = уровень гема + 1 (L40 при геме 20); качество = 0–20% больше урона миньонов + 0–20% Reservation Efficiency.
- Пул: ~600+ привязываемых типов монстров (normal/magic/rare; боссы не привязываются `(не подтверждено)`). Полный список цен/типов: [poe2spectrewiki.com](https://poe2spectrewiki.com).

## Tame Beast (Huntress)

- Гем Dex 7 тира; **только монстры Rare Beast**; накладывает Hinder (30%), убийство внутри окна поимки (**8 с при L1 → 11.8 с при L20**). Гем превращается в Companion, призывающего зверя (Reviving); **зверь сохраняет до 4 своих модификаторов**.
- **The Natural Order у Spirit Walker**: приручает **Unique Beasts / боссов карт** (разрешён один; одержим цикличными азмерийскими духами) — см. [ascendancies/spirit-walker.md](../ascendancies/spirit-walker.md).
- 0.5.0: звери наносят на 40% больше урона при L9 → 84% при L20.

## Лимиты слотов компаньонов

- По умолчанию **1**; ключевой камень **Trusted Kinship** +1; Yriel's Fostering (уникальный нагрудник) → 2; нотабл «Easy Going» −30% резервирования компаньонов.

## Что масштабирует миньонов

- **Применяются только модификаторы с явной пометкой «Minion»/«Companion»/«Ally»** — общий «increased damage» игрока **не** переносится. (Заявленное исключение: плоские «Adds X Fire/Cold/Lightning» на экипировке могут усиливать некоторых миньонов `(не подтверждено)`.)
- Порядок приоритета при снаряжении: **+X к уровню всех умений миньонов** → **Дух (Spirit)** (больше/дешевле миньонов) → **% урона миньонов**.
- Мета-цель скипетра (0.5): Rattling Sceptre, +4 умения миньонов, 150–160+ Духа, урон миньонов, моды команд.
