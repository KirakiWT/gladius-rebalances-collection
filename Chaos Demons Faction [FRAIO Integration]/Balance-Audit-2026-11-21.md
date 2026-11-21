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

## 6. Третий проход: граф улучшений и доступность сущностей

Проверены все 17 XML зданий, 49 XML юнитов и 67 XML улучшений в `Data/World` пакета Chaos Daemons, а также определения фракции и города.

### Проверка ссылок

- 16 уникальных целей `constructBuilding` из зданий имеют соответствующие XML в `World/Buildings/ChaosDaemons_MT`.
- 39 уникальных целей `produceUnit` имеют соответствующие XML в `World/Units/ChaosDaemons_MT`.
- Все локальные значения `requiredUpgrade`, обнаруженные в XML зданий, юнитов, фракции и города, соответствуют существующим файлам в `World/Upgrades/ChaosDaemons_MT`.
- Все ссылки `<requiredUpgrades><upgrade name="..."/>` внутри 67 XML улучшений ведут на существующие локальные upgrade-файлы. В проверенной цепочке циклических зависимостей не обнаружено.

В `Units/ChaosDaemons_MT/ChaosCultist.xml` есть ссылка на `ChaosSpaceMarines/ChaosRising`. Она разрешается в AIO по пути `Data/World/Upgrades/ChaosSpaceMarines/ChaosRising.xml`. Это ожидаемая интеграционная зависимость: Chaos Daemons предназначен для работы поверх AIO, а не как самостоятельный мод. Поэтому ссылка не является дефектом и не должна устраняться копированием или дублированием upgrade в локальном namespace.

### Подтверждённые цепочки prerequisites

| Ветка | Зависимость по XML |
|---|---|
| Khorne | Khorne → Bloodthirster → KhorneAscension2 и SkullLordPact |
| Nurgle | Nurgle → GreatUncleanOne → NurgleAscension2 |
| Slaanesh | Slaanesh → KeeperOfSecrets → SlaaneshAscension2 |
| Tzeentch | Tzeentch → LordOfChange → TzeentchAscension2 |
| Vehicles | Vehicles → Maulerfiend, WarDogStalker, LandRaider, KnightDesecrator и SmokeLauncher |
| Heroes | Heroes → ChaosLord и MasterOfPossession |
| Teleport / movement | WarpRift → WarpSurge |
| Vehicle armour | ExtraVehicleArmour требует одновременно Aircraft и Vehicles |
| Locus | LocusOfDamnation требует все восемь Locus upgrades; каждый из восьми зависит от соответствующей ветки одного из четырёх богов |

Все перечисленные имена присутствуют в локальном upgrade-дереве. В частности, восемь Locus — это две способности для каждого из Khorne, Nurgle, Slaanesh и Tzeentch.

### Городские улучшения

Локальные `CityTier2.xml` и `CityTier3.xml` существуют. Их Git blob SHA совпадают с соответствующими AIO-файлами Chaos Space Marines. В самих этих двух upgrade XML нет явного `requiredUpgrades` между Tier 2 и Tier 3; Headquarters ссылается на оба локальных улучшения отдельно. Это совпадает с AIO-шаблоном и не выглядит отдельным расхождением Chaos Daemons.

### Юниты без обычного производственного здания

Шесть unit XML существуют, но ни один из 17 проверенных Chaos Daemons buildings не содержит для них `produceUnit`:

- `Bullgryn.xml`
- `HeavyWeaponsSquad.xml`
- `Hydra.xml`
- `LemanRussBattleTank.xml`
- `LordCommissar.xml`
- `ScoutSentinel.xml`

В локализации у них есть имена и описания, а их модели используют Astra Militarum / Reinforcements assets. Пока это только кандидаты на неиспользуемые или выдаваемые другим способом определения: отсутствие `produceUnit` в зданиях не доказывает, что юниты нигде не создаются. Эти записи не удалялись и не менялись.

Не следует путать их с сущностями без `produceUnit`, у которых найден другой явный путь появления: Be'lakor входит в стартовый состав фракции; WarpRift создаётся действием фракции; LordOfSkulls вызывается способностью Bloodthirster; Headquarters имеет отдельное служебное определение.

### Итог граф-проверки

На уровне статических ссылок в проверенных зданиях, юнитах, фракции, городе и upgrade prerequisites отсутствующих локальных файлов не найдено. Это подтверждает целостность адресуемых XML-узлов, но не доказывает, что каждый upgrade можно исследовать в реальной партии или что каждая способность срабатывает как задумано. Для такого вывода нужны проверка полного механизма исследования и игровые тесты.

## 7. Четвёртый проход: шесть Imperial-derived unit definitions

Повторно проверены шесть юнитов, для которых в предыдущем проходе не нашлось обычного `produceUnit` в зданиях Chaos Daemons. Дополнительно выполнено сравнение с соответствующими Astra Militarum XML в AIO, проверены их weapon / trait / action declarations и выполнен адресный поиск прямых `produceUnit` и `addUnit` ссылок.

### Сопоставление с AIO

В таблице перечислены базовые значения из скрытых модификаторов. В проверенных числовых полях значения Chaos Daemons совпадают с AIO; различия сосредоточены в оружии, traits и действиях.

| Юнит | Проверенные базовые значения | Отличия Chaos-варианта от AIO |
|---|---|---|
| Bullgryn | Armor 6, HP 12, Production 48, Food 40, Ore 40, Food Upkeep 3, Movement 3 | Faction traits, Scintillating Legion, четыре варианта Hammer of Wrath. Chaos unit mesh ссылается на `Units/Reinforcements_MT/Bullgryn`. |
| HeavyWeaponsSquad | Armor 4, HP 4, Production 30, Food 15, Ore 15, Food Upkeep 1.5, Movement 3 | То же базовое вооружение Frag/Krak Missile Launcher; traits заменены на Scintillating Legion, Warband Discipline, Undivided и Shadow of Chaos. |
| Hydra | Armor 6, HP 24, Production 39, Ore 50, Ore Upkeep 2, Movement 4 | Вместо пары Ground / Anti-Air Hydra autocannon definitions и Hunter-Killer Missile в Chaos XML указаны TwinLinkedHydraAutocannon и HeavyBolter; добавлены марки и Smoke Screen. |
| LemanRussBattleTank | Armor 8, HP 42, Production 48, Ore 80, Ore Upkeep 4, Movement 3 | В Chaos XML указаны BattleCannon и Lascannon; в AIO дополнительно есть HeavyBolter и HunterKillerMissile. Добавлены марки и Smoke Screen. |
| LordCommissar | Armor 6, HP 14, Production 36, Food 20, Energy 20, Influence 80, Food Upkeep 1, Energy Upkeep 1, Movement 3 | BoltPistol / PowerSword сохраняются; вместо Astra Militarum traits — Chaos traits, AuraOfDiscipline, BringItDown, HearMyCommand и SummaryExecution. Добавлен `Reinforcements_MT/SupportHero`. |
| ScoutSentinel | Armor 5, HP 16, Production 36, Ore 40, Ore Upkeep 2, Movement 4 | В Chaos XML указан только MultiLaser, тогда как AIO ещё содержит KrakMissileLauncher. Добавлены марки, Smoke Screen и варианты Hammer of Wrath. |

Это сравнение проверяет только указанные базовые поля и перечисленные XML-объявления. Оно не утверждает, что различия в weapon lists автоматически являются ошибкой или что unit balance одинаков при одинаковых основных числах.

### Доступность и пути создания

- Ни одно из шести имён не встречается как цель `produceUnit unit="ChaosDaemons_MT/…"` в XML зданий Chaos Daemons.
- Для этих шести unit ID не обнаружены прямые `addUnit name="ChaosDaemons_MT/…"` ссылки в поиске по репозиторию.
- В локальном `World/Upgrades/ChaosDaemons_MT` нет одноимённых unlock-upgrade XML, открывающих производство этих юнитов.
- В английской и русской локализации присутствуют имена, описания и flavor entries. Наличие локализации подтверждает, что ключи предусмотрены для интерфейса, но не доказывает доступность юнита.
- `LordCommissar.xml` имеет trait `Reinforcements_MT/SupportHero`, однако в проверенном XML его самого нет в производственных действиях зданий Chaos Daemons и не найдено прямой ссылки на его создание.
- В AIO-версии `AstraMilitarum/LordCommissar.xml` есть отдельная способность `AstraMilitarum/Bullgrynreinforcements`, которая вызывает `AstraMilitarum/Bullgryn`. В Chaos-версии Commissar эта способность отсутствует: там есть `ChaosDaemons_MT/HearMyCommand`, Chaos-specific abilities и SupportHero trait. Следовательно, Bullgryn не получает этот AIO-путь вызова через Chaos Lord Commissar.

### Рабочая классификация

Эти шесть записей лучше классифицировать как **адаптированные unit definitions без найденного локального пути доступности**, а не как битые ссылки: сами unit XML существуют, их ключи локализованы, а числовые параметры и faction traits оформлены под Chaos Daemons.

Bullgryn имеет особенно понятную историческую подсказку в AIO-комиссаре, но Chaos-версия этой способности не содержит. Для остальных пяти в проверенном дереве также не найден прямой путь производства или вызова.

Это пока не доказательство ошибочного удаления или незавершённой функции. Возможные внешние правила Reinforcements / сценариев и поведение движка здесь не подтверждены. Ни один из этих XML не изменялся.

## 8. Пятый проход: Shadow of Chaos и Locus

### Locus: восемь действий и их эффекты

В `Data/World/Factions/ChaosDaemons_MT.xml` объявлены все восемь Locus-doctrina. У каждой действия имя совпадает с её `requiredUpgrade`; все восемь upgrade XML существуют, а `LocusOfDamnation.xml` перечисляет их все как обязательные prerequisites.

| Бог | Locus | Реализация |
|---|---|---|
| Khorne | Unstoppable Fury | Временный trait; соответствующая trait definition существует |
| Khorne | Diabolical Purpose | Временный trait; соответствующая trait definition существует |
| Nurgle | Foetid Regeneration | Прямой эффект `hitpoints add="6"` для Nurgle; также для Undivided при LocusOfDamnation |
| Nurgle | Poxes Uncounted | Временный trait; соответствующая trait definition существует |
| Tzeentch | Conjuration | Временный trait; соответствующая trait definition существует |
| Tzeentch | Transmogrification | Временный trait; соответствующая trait definition существует |
| Slaanesh | Unnatural Swiftness | Временный trait; соответствующая trait definition существует |
| Slaanesh | Delicate Evisceration | Временный trait; соответствующая trait definition существует |

В каталоге `World/Traits/ChaosDaemons_MT/Locus` есть семь trait XML, а для Foetid Regeneration отдельного trait-файла нет. Это не следует считать dangling reference: соответствующее действие в faction XML не вызывает `addTrait`, а задаёт эффект HP напрямую. Для этой способности отдельная trait definition в проверенной схеме не используется.

### Shadow of Chaos: связанная структура

- `World/Features/ChaosDaemons_MT/ShadowOfChaos.xml` существует и добавляет marker traits `ShadowOfChaos` и `ShadowOfChaosEnemy`.
- Для Undivided, Khorne, Nurgle, Slaanesh и Tzeentch существуют отдельные trait definitions. Они проверяют наличие Shadow marker и соответствующей марки; в них заданы faction-specific бонусы, а также общие бонусы к morale loss и Energy Upkeep.
- `ShadowOfChaosEnemy.xml` задаёт базовую добавку `moraleLossFactor +0.17`; отдельный дополнительный модификатор `+0.33` всё ещё ссылается на выведенный из состава проекта upgrade ID `ChaosDaemons_MT/PrimalTerror`. Эта ссылка — остаток, а не основание восстанавливать upgrade.
- В том же enemy trait есть отдельный per-turn эффект для `ChaosDaemons_MT/DaemonicTerror`; `DaemonicTerror.xml` существует и остаётся самостоятельной механикой. Его наличие не меняет решение об исключении PrimalTerror.
- Среди обнаруженных источников Shadow-маркера: `DarkGlory` добавляет feature на клетки в радиусе 1–3 после убийства врага; Lord Commissar может создать feature через способность; Lord of Change, Changecaster и Warp Rift также содержат faction-specific Shadow marker effects.

### PrimalTerror: исключён из состава проекта

**Решение по составу:** `PrimalTerror` должен быть удалён и не должен восстанавливаться как upgrade. Отсутствие `World/Upgrades/ChaosDaemons_MT/PrimalTerror.xml` — ожидаемое состояние, а не запрос на создание нового определения. Не следует придумывать для него стоимость, prerequisites или игровые эффекты.

В текущих игровых данных при этом остались три ссылки на исключённый ID:

1. `World/Traits/ChaosDaemons_MT/ShadowOfChaosEnemy.xml` — дополнительный модификатор `moraleLossFactor +0.33` закрыт условием `requiredUpgrade="ChaosDaemons_MT/PrimalTerror"`.
2. `World/Traits/ChaosDaemons_MT/Belakor/Tier10.xml` — ID включён в набор условий для одного из Tier 10 модификаторов Be'lakor.
3. `World/Traits/ChaosDaemons_MT/Belakor/BetrayingShades/Tier10.xml` — ID включён в набор условий для Tier 10 эффекта Betraying Shades.

Кроме того, английский и русский `Data/Core/Languages/*/Upgrades.xml` сохраняют по три устаревшие строки: название, описание и flavor.

**Классификация:** это остаточные ссылки и локализация удалённого элемента, а не недостающая реализация. Их следует удалить вместе с самим ID при разрешённой чистке игровых XML и языковых файлов. До такой чистки нельзя считать подтверждённым, как движок трактует эти оставшиеся условия; в частности, не следует утверждать, что соответствующие бонусы Be'lakor или Shadow of Chaos работают либо не работают в игре.

По установленному ограничению на текущем проходе изменяются только документы: игровые XML и локализация не редактируются.

## 9. Следующие проверки

- Сравнить стоимость и параметры основных юнитов Chaos Daemons с релевантными аналогами AIO по одинаковым полям.
- Отдельно проверить Shadow of Chaos, Locus и эффекты марок по цепочкам Unit → Trait → Feature / Weapon.
- Проверить связи `Reinforcements_MT/SupportHero` и связанные правила создания юнитов из интегрированной основы AIO; отдельно выяснить, являются ли шесть unit definitions запланированным reinforcement / support / legacy content.
- При разрешённой правке игровых данных удалить остаточные ссылки на исключённый `PrimalTerror` из трёх trait XML и убрать его name / description / flavor entries из английской и русской `Upgrades.xml`; затем перепроверить оставшиеся prerequisites Tier 10.
- Для условий и способностей, семантика которых зависит от движка, отделить статическую проверку XML от результатов игрового теста.

## 10. Журнал последующих записей

Добавлять сюда только воспроизводимые наблюдения. Для каждой записи указывать дату, точный путь XML, проверенное условие или значение и отдельно — был ли результат подтверждён в игре.

### Новая запись

- Дата:
- XML:
- Наблюдение:
- Проверка в игре:
- Статус / примечание:
