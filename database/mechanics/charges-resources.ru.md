# Заряды и особые ресурсы

> Источники: [poe2db — Charges](https://poe2db.tw/us/Charges), [Mobalytics charges guide](https://mobalytics.gg/poe-2/profile/dreamcore/guides/poe-2-charges-explained), [poe2db — Combo](https://poe2db.tw/us/Combo)

## Заряды Power / Frenzy / Endurance

- Стандартный максимум **3 каждого вида**; длятся **15 секунд**, обновляются при получении ещё одного того же вида.
- **Нет встроенного эффекта** — заряды потребляются умениями/камнями поддержки (ключевое отличие дизайна от PoE 1).

| Заряд | Примеры получения | Примеры трат | Выгоды |
|---|---|---|---|
| **Endurance** (Сила) | Трата Ярости в форме Bear (1 за 15 Ярости), Тяжёлые оглушения, полный слом брони, блоки Magma Barrier | Тотемы, обход кулдаунов warcry | Жизнь за каждый потраченный заряд (Kingsguard/Rally), урон огнём, +40% брони на скипетрах |
| **Frenzy** (Ловкость) | Sniper's Mark, добивания (cull), парирование (Parry), Combat Frenzy (при Freeze/Electrocute/Pin), Blood Rage | Умения копий/луков | Скорость умений, слом брони, +5% скорости передвижения за заряд (Darkray Vectors) |
| **Power** (Интеллект) | Power Siphon, криты (Voll's Protector), убийства Killing Palm, Siphoning Strike (потребляет Shock), Profane Ritual | Flicker Strike, Falling Thunder, Charged Staff | Бонус критического урона за заряд (Powertread), больше урона заклинаний за заряд (Inner Conviction) |

- Conduit/Resonance/Inner Conviction делят или конвертируют типы зарядов.

## Combo (Monk)

- **Счётчик на каждое умение**, не глобальный ресурс: умения **получают Combo, когда вы наносите Strike по врагам**, и угасают без генерации (~4 с с камнями поддержки Combo Finisher; Combo Finisher I = +25% больше урона).
- Combo либо **требуется для применения** умения (Tempest Bell, Falling Thunder, Siphoning Strike), либо даёт дополнительные эффекты.
- Цикл: быстрые удары (Tempest Flurry/Ice Strike) накапливают Combo → тратится на финишеры. Tempest Flurry эскалирует: 3-е быстрое применение бьёт 3×, 4-е — Final Strike; потребляет заряды Frenzy ради скорости умений.
- Martial Artist переписывает правила: Martial Master (накопление/удержание Combo независимо от набора оружия), Martial Adept (+1 за получение) — см. [ascendancies/martial-artist.md](../ascendancies/martial-artist.md).

## Ярость (Rage)

- Универсальный ресурс Ярости (накапливается от ударов в ближнем бою / отдельных узлов); PoE 2 добавил **leech Ярости**.
- **Druid (0.4.0)**: ресурсы, зависящие от формы — **форма Bear использует Ярость** (разрывает толпы; 1 заряд Endurance за 15 потраченной Ярости), **форма Wolf использует лунную энергию**, **форма Wyvern использует заряды Power**; человеческая форма применяет заклинания как обычно. ([pathofexile2.com/druids](https://pathofexile2.com/druids))
- Shaman масштабирует урон заклинаний от Ярости (Druidic Champion: 1% больше урона заклинаний за 2 Ярости) — см. [ascendancies/shaman.md](../ascendancies/shaman.md).

## Glory (баннеры)

- Умения баннеров генерируют/потребляют **Glory**. Tactician: баннеры получают **5 Glory/с**, **без лимита** на число размещённых баннеров.
- Smith of Kitava: Kitavan Imprint +60% генерации Glory.
- Пассивки баннеров обменивают Glory на более сильные эффекты.

## Infernal Flame (Infernalist)

- Умения Infernalist могут **получать Infernal Flame вместо траты Маны**; **25% Flame теряется в секунду**, если ничего не получено за последние 2 секунды.
- Pyromantic Pact: Мана заменена 2× Infernal Flame; достижение максимума Flame наносит урон огнём по Жизни+ES. См. [ascendancies/infernalist.md](../ascendancies/infernalist.md).

## Darkness (Acolyte of Chayula)

- Зеркальный ресурс к Infernal Flame (защитный): Embrace the Darkness — нет Духа (Spirit), базовый максимум Darkness 100 (+10/уровень), урон резервируется из Darkness перед Жизнью/ES.
- Volatility: получение при наложении статусных эффектов (Inner Turmoil) / при убийстве (малый узел) — 1 Volatility запускает спекуляции; агент не смог независимо подтвердить все детали Volatility `(не подтверждено)`.
