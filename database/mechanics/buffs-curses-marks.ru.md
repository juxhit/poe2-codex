# Баффы, Проклятия, Метки, Святилища и моды редких монстров

> Источники: [Mobalytics — Curses](https://mobalytics.gg/poe-2/guides/curses), [Mobalytics — Shrines](https://mobalytics.gg/poe-2/guides/shrines), [poe2db — Monster Modifiers](https://poe2db.tw/us/Monster_Modifiers), [Fextralife — Blasphemy](https://pathofexile2.wiki.fextralife.com/Blasphemy), официальные заметки 0.5.0. Статусные эффекты: [ailments.md](ailments.md) · Контроль-состояния: [stun-and-control.md](stun-and-control.md)

## Проклятия

- **Лимит: 1 проклятие на врага** по умолчанию; второе проклятие заменяет старейшее. Лимит повышается редкими модификаторами (кольцо Doedre's Damning, нотаблы типа Whispers of Doom — часто со штрафами); Incessant Cacophony у Lich даёт +1 — см. [ascendancies/lich.md](../ascendancies/lich.md).
- **Встроенное снижение эффекта проклятия по редкости:** Magic **15%** / Rare **30%** / Unique и все боссы (вкл. Пиннакл) **50%** `(цифры Mobalytics PoE2; отдельный тир Пиннакл не задокументирован)`.
- **Задержка активации 1.5 с** по умолчанию (снижается; снимается Windscream).
- **Blasphemy** превращает вставленные проклятия в ауры, резервирует **60 Духа (Spirit) за проклятие**; проклятия Blasphemy учитываются в лимите (Blasphemy + второе кастованное проклятие не сработают оба при лимите 1). Hexproof-монстры невосприимчивы к эффектам; self-curses Soul Mantle обходят ваш лимит.
- Выгоды проклятий: Lich (Rupture the Soul, Necromantic Conduit), Ritualist, Hexblast, Whispers of the Flesh.

## Метки

- **Отдельная категория — НЕ учитываются в лимите проклятий**; Blasphemy на них не действует. Одна метка за раз `(выведено)`.
- Метки в игре: Sniper's Mark, Voltaic Mark, Freezing Mark, Bloodhound's Mark — см. [skills/skill-gems.md](../skills/skill-gems.md); Bullseye у Deadeye потребляет их.

## Известные баффы одной строкой

| Бафф | Эффект |
|---|---|
| **Onslaught** | Увеличение скорости атаки/каста/передвижения (~10–20% класс) |
| **Unholy Might** | Конвертирует 100% физического урона в хаос + 25% шанс наложить Withered при ударе (текст текущего патча) |
| **Tailwind** | Стакается: ≈1% скорости передвижения, 2% скорости умений, 10% уклонения, предотвращает 1% урона за стак `(значения не подтверждено)` |
| **Arcane Surge** | После траты достаточного количества маны: скорость каста + реген маны; масштабируемый эффект |
| **Adrenaline** | Скорость + урон + снижение физического урона; не стакается, обновляет длительность `(значения 0.5.x не подтверждено)` |
| **Rage** | Стакается, 1% больше урона атаки за стак |
| **Berserk** | Короткий бафф warcry (~1.5 с): урон в ближнем бою + получение ярости |
| **Empowerment** | Атаки, усиленные warcry; нотаблы масштабируют их урон |

## Святилища (Shrine) (карты)

- Спавнятся на картах путевых камней; **баффают ближайших монстров, пока не забраны** (guardians святилища Divine неубиваемы, пока не забраны). Баффы стакаются; **базовая длительность 45 с**; накладываются заново на арене босса. Моды карт: «Rites of the Rogues» (+2 святилища), «of the Devoted» (+1). 0.5.0: снижен шанс спавна, усилены узлы Атласа, **баффы «Damage as Extra» урезаны вдвое**.
- 0.5.0 снизил шанс спавна, усилил узлы святилищ Атласа.

| Святилище | Эффект (45 с) |
|---|---|
| Acceleration | +60% скорости умений, +40% скорости передвижения |
| Diamond | Всегда крит |
| Enlightening | +100% XP |
| Massive | +50% максимума Жизни, +100% глобальной защиты |
| Replenishing | Реген 10% Жизни и Маны в секунду |
| Resistance | +50% сопротивления стихиям, +10% всех Max Res |
| Seeking | +100% редкости предметов |
| Freezing | +50% урона как дополнительный холод + сосульки (урезано вдвое) |
| Meteoric | +50% дополнительного огня + метеоры (урезано вдвое) |
| Tempest | +50% дополнительной молнии + разряды (урезано вдвое) |
| Gloom | +25% дополнительного хаоса + взрывы трупов (урезано вдвое) |
| Divine | Нельзя получить урон (режим бога) |

## Модификаторы редких монстров (опасные)

Редкие несут **2–4 аффикса**; больше аффиксов = больше силы и наград. Названия PoE1 (Mana Siphoner, Arcane Buffer) в таком виде не существуют — полный список: [poe2db — Monster Modifiers](https://poe2db.tw/us/Monster_Modifiers). Основное:

**Атака:** Extra Fire/Cold/Light/Chaos (40% как extra) · Extra Crits (300% увеличение шанса крита) · Accurate (200% точности) · Always Poisons/Bleeds · All Damage Ignites/Chills/Shocks · Additional Projectiles (+4) · +100% больше AoE · +100% Stun Buildup · **Breaks Armour (1000% нанесённого физ. урона)** · Empowered (+50% жизни, +25% урона)

**Защита:** Armoured/Evasive/Extra ES · Cannot be Stunned · +50% сопротивлений +10% max res на элемент · **Crit Resistant (−80% бонуса критического урона против него)** · Regenerates 2%/с · Hasted · **Temporal Bubble** (уязвим только внутри своего радиуса) · **Proximal Tangibility** (игнорирует собственное ограничение «нельзя получить урон» — печально известная ловушка)

**Ауры/дебаффы:** Haste Aura · ES Aura · Ele Res Aura · Hinder Aura · **Periodic Invulnerability Aura** · **Prevents Recovery Above 50%** (аналог Arcane Buffer) · Heals Allies & Suppresses Recovery

**Эффекты смерти:** Burning/Chilled/Shocked Ground при смерти · элементальный взрыв при смерти · периодические взрывы · следы Fire/Ice/Lightning · Lightning Mirages при попадании · demise-эффекты уровня боссов (Meteoric Demise, Kulemak's Desecration…)

**Семейство one-shot (призванные объекты):** **Volatile Crystals / Volatile Plants / Volatile Crag (усиленный)** — взрывающиеся сферы, классический one-shotter · Volatile Souls (Abyss) · Magma Barrier · Ice Prisons · Flamewalls · Lightning Storms · Soulflame Geysers · Lithomantic Runes · Crystalline Barrier (Abyss)

**Сифоны/утилити:** **Siphons Mana + наносит урон молнией** · **Siphons Flask Charges** · Soul Eater · Soul Siphoner · Periodically Enrages · **Damage Taken From Minions First** · Undying Will (culling/decimating strikes, неразрушаемый труп) · Curse/Shock Reflection (20–60%)

**Смертельные комбинации (отмечены сообществом):** volatile-объекты + быстрые аура-паки; Siphons Mana + редкие со снарядами; Periodic Invulnerability + Heals Allies; Proximal Tangibility + Temporal Bubble.
