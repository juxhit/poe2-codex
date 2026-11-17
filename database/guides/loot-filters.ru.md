# Гайд по лут-фильтрам

> Источники: [NeverSink-Filter-for-PoE2 (GitHub)](https://github.com/NeverSinkDev/NeverSink-Filter-for-PoE2), [FilterBlade](https://www.filterblade.xyz/), [форумная тема NeverSink](https://www.pathofexile.com/forum/view-thread/3693141)

## Состояние системы

- В PoE2 есть **полностью поддерживаемая официальная внутриигровая система фильтров предметов** — пользовательские файлы `.filter` загружаются как в PoE1; PoE2 также предлагает **внутриигровой фильтр-лидерборд/подписку** с автообновлением (не настраивается).
- Консольные игроки не могут использовать локальные файлы — только внутриигровая подписка/лидерборд `(не подтверждено)`.

## FilterBlade

- [filterblade.xyz](https://www.filterblade.xyz/) — официальный веб-редактор NeverSink для **обоих: PoE1 и PoE2** (селектор игры).
- Возможности: пресеты строгости, полная кастомизация тиров, стили (Aura, Cobalt, Darkmode, Mythic, Vaal, Zen…), симулятор лута, Auto-Adjust, **Sync** (ручная загрузка в аккаунт) / **Sync Auto** (непрерывно, премиум Patreon).

## Фильтр NeverSink для PoE2

- [GitHub: NeverSinkDev/NeverSink-Filter-for-PoE2](https://github.com/NeverSinkDev/NeverSink-Filter-for-PoE2) — тиры на основе экономики для валюты, рун, soul cores, эссенций, уников; режим левелинга кампании переключается на правила эндгейма на уровне зоны 65; розовые/голубые уведомления предупреждают, когда фильтр устарел.
- **7 уровней строгости:** Soft, Regular, Semi-Strict, Strict, Very-Strict, Uber-Strict, Uber-Plus-Strict. Обновляется за 4–6 ч до стартов лиги, затем ~раз в месяц.

## Настройка (ПК, пошагово)

1. **Получите фильтр** — filterblade.xyz → выберите PoE2 + строгость → Download; или zip с GitHub releases.
2. **Разместите файл** — скопируйте `.filter` в:
   - Windows: `%userprofile%\Documents\My Games\Path of Exile 2`
   - Linux/Proton: `steamapps/compatdata/2694490/pfx/drive_c/users/steamuser/My Documents/My Games/Path of Exile 2`
   - НЕ в подпапку `onlinefilters`.
3. **Активируйте** — Escape → Options → Game → Filters → выберите свой фильтр.
4. **Обновляйте** — перекачивайте каждую лигу/патч или используйте FilterBlade Sync / внутриигровую подписку на лидерборд.

## Рекомендуемая строгость

| Этап | Пресет |
|---|---|
| Левелинг (1–65) | **Soft или Regular** (никогда не Very Strict во время левелинга) |
| Ранний эндгейм | **Semi-Strict** (рекомендуемый дефолт для новичков) |
| Устоявшийся эндгейм-фарм | **Strict → Very Strict** |
| Ультра-фарм (экстремальный объём) | **Uber-Strict / Uber-Plus-Strict** |
