# Аудит XML Chaos Daemons — 2026-11-21

> Рабочая заметка по текущему состоянию XML в ветке `main`.
> Проверка статическая: фиксирует содержимое файлов, но сама по себе не подтверждает поведение игрового движка.

## 1. Проверенные определения

### Фракция

Файл: `Data/World/Factions/ChaosDaemons_MT.xml`

- `playable="1"`
- `dlc="Supplement3"`
- Стартовые ресурсы: 25 Energy, 25 Food, 25 Influence, 50 Ore.
- Стартовый состав: 1 ChaosCultist, 1 ChaosSpaceMarine и 1 Be'lakor.
- В `<actions>` объявлены действия `markOfKhorne`, `markOfNurgle`, `markOfSlaanesh` и `markOfTzeentch`.

### Headquarters

Файл: `Data/World/Buildings/ChaosDaemons_MT/Headquarters.xml`

Скрытый базовый модификатор стоимости и модификатор эффектов здания содержат:

| Поле | Значение |
|---|---:|
| Production Cost | 336 |
| City Radius | +1 |
| Loyalty | +17 |
| Energy | +6 |
| Food | +6 |
| Influence | +6 |
| Ore | +6 |
| Research | +6 |
| Population Limit | +6 |

### Отдельные юниты

Значения взяты из скрытых базовых модификаторов соответствующих XML.

| Юнит | Armor | HP | Production | Дополнительные затраты |
|---|---:|---:|---:|---|
| Be'lakor | 8 | 40 | 60 | — |
| Great Unclean One | 2 | 48 | 54 | Food 100, Influence 240 |
| Bloodthirster | 7 | 40 | 54 | Food 40, Ore 100, Influence 240 |

Исходники:

- `Data/World/Units/ChaosDaemons_MT/Belakor.xml`
- `Data/World/Units/ChaosDaemons_MT/GreatUncleanOne.xml`
- `Data/World/Units/ChaosDaemons_MT/Bloodthirster.xml`

## 2. Расхождения со старыми заметками

Следующие значения встречались в удалённых или устаревших заметках и не совпадают с текущими базовыми значениями XML:

| Объект | Старое утверждение | Текущее значение в XML |
|---|---|---|
| Headquarters | Loyalty +6 | Loyalty +17 |
| Be'lakor | 18 HP | 40 HP |
| Great Unclean One | 80 HP, Armor 0 | 48 HP, Armor 2 |
| Great Unclean One (другая старая таблица) | 100 HP, Armor 0 | 48 HP, Armor 2 |
| Bloodthirster | Armor 8 | Armor 7 |

Старые документы расходились также между собой по Great Unclean One. Для текущего состояния приоритет имеет XML соответствующего юнита.

## 3. Второй проход: экономика и здания

Сравнение сделано между пакетом Chaos Daemons и соответствующими по назначению зданиями Chaos Space Marines в AIO. Это практический ориентир из AIO, но не прямое сравнение двух одинаковых фракций: Chaos Daemons в AIO как отдельный пакет не обнаружен.

### Базовые ресурсные здания

Файлы `Energy.xml`, `Food.xml`, `Influence.xml`, `Ore.xml` и `Research.xml` в Chaos Daemons и AIO имеют одинаковые Git blob SHA, то есть содержимое этих пяти пар файлов совпадает полностью.

Для каждого здания базовая стоимость — Production 24 и Ore 30, занято 1 Population и 1 Slot. Каждое добавляет +6 соответствующего ресурса. Поддержание: у Energy — +1 Ore Upkeep; у Food, Influence, Ore и Research — +1 Energy Upkeep.

Практический вывод ограничен фактом идентичности файлов: на этом слое отдельной настройки этих пяти зданий для Chaos Daemons относительно AIO нет.

### Construction

Файлы:

- Chaos Daemons: `Data/World/Buildings/ChaosDaemons_MT/Construction.xml`
- AIO: `Data/World/Buildings/ChaosSpaceMarines/Construction.xml`

Общие параметры: Production 48, Ore 80, 1 Population, 1 Slot, +3 Energy Upkeep; действие Acquire Tile также использует одинаковые добавочные затраты +5 Influence, +5 Ore и +12 Production.

Различия в модификаторах здания:

| Эффект | Chaos Daemons | AIO / Chaos Space Marines |
|---|---:|---:|
| Influence | +2 | +2 |
| Ore | +4 | +2 |
| Food | — | +2 |
| Production | +6 | +6 |
| Доплата Production за Clear Tile | +12 | +6 |

Следовательно, текущий XML Chaos Daemons даёт этому зданию на +2 Ore больше, не даёт +2 Food из AIO и задаёт вдвое большую добавку Production за Clear Tile. Это подтверждённые отличия файлов, но само по себе ещё не заключение о том, что эти значения ошибочны.

### Cult

Файлы:

- Chaos Daemons: `Data/World/Buildings/ChaosDaemons_MT/Cult.xml`
- AIO: `Data/World/Buildings/ChaosSpaceMarines/Cult.xml`

У обоих зданий Production 36, Ore 50, 1 Population и 1 Slot. Отличаются содержание и обслуживание:

| Поле / эффект | Chaos Daemons | AIO / Chaos Space Marines |
|---|---:|---:|
| Upkeep | +2 Energy | +2 Ore |
| Loyalty | +2 | — |
| Energy | — | +2 |
| Influence | — | +2 |
| Production | +6 | +6 |
| Стратегический приоритет | Colonizers и Infantry | Colonizers |

Это существенное отличие от AIO по типу обслуживания, бонусам города и стратегическому приоритету производства.

### Здания богов

В Chaos Daemons четыре отдельных здания — Khorne, Nurgle, Slaanesh и Tzeentch. Для каждого в скрытом базовом модификаторе заданы Production 36, Ore 50, 1 Population, 1 Slot и +2 Energy Upkeep.

| Здание | Эффекты здания |
|---|---|
| Khorne | +3 Ore, +1 Influence, +8 Production |
| Nurgle | +3 Food, +1 Growth, +2 Loyalty, +6 Production |
| Slaanesh | +3 Influence, +1 Population Limit, +6 Production |
| Tzeentch | +3 Energy, +3 Research, +6 Production |

Все четыре соответствующих upgrade XML также задают стратегические приоритеты Loyalty, Infantry Production и Vehicles Production. Это описание деклараций XML; прямого аналога каждому из четырёх зданий в AIO Chaos Space Marines для этой таблицы не подбиралось.

### Headquarters: привязка улучшений города

В Chaos Daemons Headquarters traits используют имена `ChaosSpaceMarines/CityTier2` и `ChaosSpaceMarines/CityTier3`, но проверяют локальные улучшения `ChaosDaemons_MT/CityTier2` и `ChaosDaemons_MT/CityTier3`. В AIO Headquarters те же имена traits привязаны к улучшениям `ChaosSpaceMarines/CityTier2` и `ChaosSpaceMarines/CityTier3`.

Оба локальных Chaos Daemons upgrade-файла существуют. Это отмечено как схема совместного использования trait-имён при локальных upgrade-ключах, а не как доказанная ошибка. Фактическое получение городских бонусов требует проверки в игре.

## 4. Действия марок и стартовые условия

В `Data/World/Factions/ChaosDaemons_MT.xml` все четыре действия марок:

- требуют соответствующий upgrade фракции;
- нацелены на юниты своей фракции с trait `ChaosDaemons_MT/Undivided`;
- исключают юниты с trait `Fortification` и `ChaosDaemons_MT/GreaterDaemon`;
- снимают `Undivided` и добавляют выбранную марку.

Дополнительные эффекты в XML: Nurgle добавляет `Regeneration`, Slaanesh — `ChaosDaemons_MT/HarbringerOfLust`, Tzeentch — `SoulBlaze`; Khorne в этом действии добавляет только собственный trait марки. Указанный trait `HarbringerOfLust` присутствует в дереве Chaos Daemons под тем же написанием.

В XML у всех четырёх действий стоит `rangeMax="-1"`. Здесь фиксируется только значение атрибута, без предположения о его точной семантике в движке.

## 5. Что этот аудит не утверждает

- Значения скрытых XML-модификаторов не являются игровым тестом и не доказывают работу всех эффектов в бою.
- Сравнение с Chaos Space Marines в AIO не означает, что эти фракции должны иметь одинаковые здания или экономику.
- Не подтверждаются на основании старых заметок спорные взаимодействия `attackedThisTurn`, содержания Кхорна, аур, радиусов, Dread Marshal и Shadow of Chaos.
- Не оцениваются достижимость всех технологий, полный граф зависимостей, корректность локализации и фактическая работа DLC-gate.
- Совпадение или отличие XML само по себе не устанавливает, насколько сильнее или слабее фракция в реальной партии.

## 6. Следующие проверки

- Проследить все `requiredUpgrade` от действий зданий до upgrade XML, отдельно проверить отсутствующие или недостижимые связи.
- Сравнить стоимость и параметры основных юнитов Chaos Daemons с релевантными аналогами AIO по одинаковым полям.
- Отдельно проверить Shadow of Chaos, Locus и эффекты марок по цепочкам Unit → Trait → Feature / Weapon.
- Для условий и способностей, семантика которых зависит от движка, отделить статическую проверку XML от результатов игрового теста.

## 7. Журнал последующих записей

Добавлять сюда только воспроизводимые наблюдения. Для каждой записи указывать дату, точный путь XML, проверенное условие или значение и отдельно — был ли результат подтверждён в игре.

### Новая запись

- Дата:
- XML:
- Наблюдение:
- Проверка в игре:
- Статус / примечание:
