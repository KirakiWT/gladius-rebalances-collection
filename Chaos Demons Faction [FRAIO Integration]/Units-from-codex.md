# Chaos Daemons — 7th Edition → Gladius mod comparison

> Проверка состояния: ветка `main` репозитория `KirakiWT/gladius-rebalances-collection` на 20 ноября 2026 г.  
> Файл создан только для анализа. Ни один XML, файл локализации, изображение или другой существующий файл фракции не изменялся.

## 1. Источники и методика

- Настольная редакция: [New Recruit — Warhammer 40,000 7th Edition / Chaos Daemons: Codex](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex). Каталог показывает 122 записи, но среди них есть формации, фортификации, Forge World и групповые/дублирующие записи. Ниже основной реестр — игровые datasheet'ы и модели фракции, а не все 122 элемента каталога.
- Мод: XML-файлы из `Chaos Demons Faction [FRAIO Integration]/Data/World/Units/ChaosDaemons_MT/`.
- В таблицах настольные значения записаны как **WS / BS / S / T / W / I / A / Ld / Save**. Это профиль 7-й редакции; стоимость указана в очках за модель или за юнит согласно New Recruit.
- Параметры Gladius — базовые значения из первого скрытого блока `<modifier visible="0"><effects>…`. Учитываются базовые параметры XML, не эффекты технологий, аур, временных трейтов или апгрейдов.
- **Сопоставление не является конвертацией характеристик.** WS и MeleeAccuracy, Save и Armor, Wounds и Hitpoints, очки армии и ProductionCost — разные системы и масштабы. Значения приведены рядом только для аудита дизайна и баланса.

### Обозначения полей Gladius

| Поле | Значение в XML |
|---|---|
| Armor | `armor` |
| HP | `hitpointsMax` |
| MeleeAcc / RangedAcc | `meleeAccuracy` / `rangedAccuracy` |
| MeleeAttacks | `meleeAttacks` |
| StrengthDamage | `strengthDamage` |
| Morale | `moraleMax` |
| Move | `movementMax` |
| Prod | `productionCost` |
| Food / Ore / Energy / Influence | соответствующие `*Cost` |
| Upkeep | соответствующие `*Upkeep` |
| Group | `<group size="…">`; если `<group>` отсутствует — одиночная модель |

## 2. Краткий итог сопоставления

### Прямо реализованные юниты / datasheet'ы

| Запись 7-й редакции | Файл мода | Итог |
|---|---|---|
| [Be'lakor](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/4364-0360-c913-91c4/be%27lakor%2C-the-dark-master) | `Belakor.xml` | Прямой персонаж |
| [Beast of Nurgle](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/f341-0a10-d29c-ba9f/beasts) | `BeastOfNurgle.xml` | Прямой юнит |
| [Bloodcrushers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/95fb-a926-71d8-c0c0/bloodcrushers) | `Bloodcrusher.xml` | Прямой юнит |
| [Bloodletters](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/0388-83e6-f4f8-71f6/bloodletters) | `Bloodletter.xml` | Прямой юнит |
| [Bloodthirsters](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/c16e-320b-e286-059e/bloodthirster-of-insensate-rage) | `Bloodthirster.xml` | Общая реализация; три настольных варианта не разделены |
| [Blue Horrors](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/b77b-9911-3d41-85b9/blue-horrors) | `BlueHorror.xml` | Реализованы Blue Horrors; Brimstone и Pink отсутствуют |
| [Burning Chariot](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/a893-cc46-de93-381e/burning-chariot-of-tzeentch) | `BurningChariot.xml` | Прямой юнит |
| [Daemonettes](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/01ae-db1f-a7a3-8773/daemonettes) | `Daemonette.xml` | Прямой юнит |
| [Flamers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/e407-1ea5-659c-5858/flamers) | `Flamer.xml` | Прямой юнит |
| [Great Unclean One](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/5749-a0d7-e352-7e28/great-unclean-one) | `GreatUncleanOne.xml` | Прямой персонаж |
| [Keeper of Secrets](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/d221-997d-99e7-c51f/keeper-of-secrets) | `KeeperOfSecrets.xml` | Прямой персонаж |
| [Lord of Change](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/5795-6660-b297-a685/lord-of-change) | `LordOfChange.xml` | Прямой персонаж |
| [Plague Drones](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2dbb-806a-ea09-fc13/plague-drones) | `PlagueDrone.xml` | Прямой юнит |
| [Plaguebearers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/7cee-b1d5-693b-a28d/plaguebearers) | `Plaguebearer.xml` | Прямой юнит |
| [Screamers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/5e4f-7d93-beac-c8fd/screamers) | `Screamer.xml` | Прямой юнит |
| [Seekers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/6760-51e4-b79a-bdce/seekers) | `Seeker.xml` | Прямой юнит |
| [Skull Cannon](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2fea-4024-4f96-117c/skull-cannon-of-khorne) | `SkullcannonKhorne.xml` | Прямой Khorne-вариант |
| [Soul Grinder](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/bea6-b66e-ef91-7ad5/soul-grinder-of-chaos) | `SoulGrinderKhorne.xml`, `SoulGrinderNurgle.xml`, `SoulGrinderSlaanesh.xml`, `SoulGrinderTzeentch.xml` | Один настольный datasheet реализован четырьмя вариантами покровителя |

### Частичные аналоги, а не совпадение datasheet'ов

| Настольная запись | Файл мода | Почему это только аналог |
|---|---|---|
| [Herald of Khorne](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/eff5-c688-5678-5765/herald-of-khorne) | `Bloodmaster.xml` | В моде есть герой Кхорна, но это Bloodmaster с собственными RTS-параметрами, а не точное воспроизведение профиля Herald of Khorne |
| [Herald of Tzeentch](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/eeb8-23a2-fd50-af88/herald-of-tzeentch) | `Changecaster.xml` | Ролевой аналог; профиль и состав вооружения отличаются |
| Herald of Nurgle / Herald of Slaanesh | `SloppityBilepiper.xml` / `InfernalEnrapturess.xml` | Эти два файла — персонажи более позднего ростера, не модели/профили Herald of Nurgle и Herald of Slaanesh из 7-й редакции |

## 3. Сравнение характеристик: настольная 7-я редакция и текущий Gladius

Формат профиля Warhammer 40,000: **WS/BS/S/T/W/I/A/Ld/Save**.  
Формат Gladius: **Armor/HP/MeleeAcc/MeleeAttacks/StrengthDamage/Morale/Move/RangedAcc**.

### Явное сопоставление профилей 7-й редакции и Gladius

В этой таблице профиль 7-й редакции и профиль Gladius приведены **с названиями каждого поля**, а не набором чисел без подписи.

**Профиль 7-й редакции:** WS / BS / S / T / W / I / A / Ld / Sv.  
**Профиль Gladius:** Armor / HP / MeleeAcc / RangedAcc / MeleeAttacks / StrengthDamage / Morale / Move.

- WS = Weapon Skill; BS = Ballistic Skill; S = Strength; T = Toughness; W = Wounds; I = Initiative; A = Attacks; Ld = Leadership; Sv = обычный armour save.
- Для Be'lakor отдельно записан invulnerable save 4++. У других демонов специальный Daemonic save (обычно 5++) — это правило, а не отдельная характеристика WS/BS-профиля.
- Для машин и шагоходов 7e использует Vehicle Armour Value / Hull Points или Walker-профиль. Там, где нет стандартных WS/BS/S/T/W/I/A/Ld/Sv, это явно отмечено.

| Юнит 7e | Очки | Профиль 7e с подписями | XML юнита в моде | Профиль Gladius с подписями |
|---|---:|---|---|---|
| [Be'lakor, The Dark Master](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/4364-0360-c913-91c4/be%27lakor%2C-the-dark-master) | 350 | WS 9; BS 5; S 6; T 5; W 4; I 8; A 5; Ld 10; Sv —; Inv 4++ | `Belakor.xml` | Armor 8; HP 40; MeleeAcc 12; RangedAcc 10; MeleeAttacks 2; StrengthDamage 3; Morale 12; Move 3; Group 1 |
| [Beast of Nurgle](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/78a9-42bf-5992-dae8/beast-of-nurgle) | 52 | WS 3; BS 0; S 4; T 5; W 4; I 2; A D6+1; Ld 7; Sv — | `BeastOfNurgle.xml` | Armor 6; HP 36; MeleeAcc 8; RangedAcc 6; MeleeAttacks 2; StrengthDamage 4; Morale 8; Move 3; Group 1 |
| [Bloodcrushers of Khorne](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/4038-e15a-4b22-1843/bloodcrushers-of-khorne) | 45 | WS 5; BS 5; S 5; T 4; W 3; I 4; A 3; Ld 7; Sv 6+ | `Bloodcrusher.xml` | Armor 8; HP 8; MeleeAcc 8; RangedAcc 8; MeleeAttacks 2; StrengthDamage 2; Morale 8; Move 3; Group 3 |
| [Bloodletters of Khorne](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/8cb7-dde6-f565-0f6c/bloodletters-of-khorne) | 10 | WS 5; BS 5; S 4; T 3; W 1; I 4; A 1; Ld 7; Sv 6+ | `Bloodletter.xml` | Armor 4; HP 2; MeleeAcc 8; RangedAcc 8; MeleeAttacks 1; StrengthDamage 2; Morale 8; Move 3; Group 8 |
| [Bloodthirster of Insensate Rage](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/c16e-320b-e286-059e/bloodthirster-of-insensate-rage) | 275 | WS 10; BS 10; S 6; T 6; W 5; I 9; A 6; Ld 9; Sv 3+ | `Bloodthirster.xml` | Armor 8; HP 40; MeleeAcc 12; RangedAcc 10; MeleeAttacks 3; StrengthDamage 4; Morale 12; Move 3; Group 1 |
| [Bloodthirster of Unfettered Fury](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/a387-df65-c063-8b9a/bloodthirster-of-unfettered-fury) | 250 | WS 10; BS 10; S 6; T 6; W 5; I 9; A 6; Ld 9; Sv 3+ | `Bloodthirster.xml` | Armor 8; HP 40; MeleeAcc 12; RangedAcc 10; MeleeAttacks 3; StrengthDamage 4; Morale 12; Move 3; Group 1 |
| [Wrath of Khorne Bloodthirster](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/4ac0-632a-80e4-f66e/wrath-of-khorne-bloodthirster) | 300 | WS 10; BS 10; S 6; T 6; W 5; I 9; A 6; Ld 9; Sv 3+ | `Bloodthirster.xml` | Armor 8; HP 40; MeleeAcc 12; RangedAcc 10; MeleeAttacks 3; StrengthDamage 4; Morale 12; Move 3; Group 1 |
| [Blue Horrors](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/176e-d25c-3180-96f0/blue-horrors) | 5 | WS 3; BS 3; S 2; T 2; W 1; I 3; A 1; Ld 7; Sv — | `BlueHorror.xml` | Armor 4; HP 2; MeleeAcc 6; RangedAcc 8; MeleeAttacks 1; StrengthDamage 1; Morale 8; Move 3; Group 8 |
| [Burning Chariot of Tzeentch](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/a893-cc46-de93-381e/burning-chariot-of-tzeentch) | 100 | Vehicle: BS 3; AV 10/10/10 (F/S/R); HP 3 | `BurningChariot.xml` | Armor 8; HP 20; MeleeAcc 8; RangedAcc 8; MeleeAttacks 1; StrengthDamage 1.5; Morale 8; Move 4; Group 2 |
| [Daemonettes of Slaanesh](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/846f-0ade-cd97-79ad/daemonettes-of-slaanesh) | 9 | WS 5; BS 4; S 3; T 3; W 1; I 5; A 2; Ld 7; Sv — | `Daemonette.xml` | Armor 4; HP 2; MeleeAcc 8; RangedAcc 8; MeleeAttacks 2; StrengthDamage 1; Morale 8; Move 3; Group 8 |
| [Flamers of Tzeentch](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/6c47-2be0-97d6-2241/flamers-of-tzeentch) | 23 | WS 2; BS 4; S 4; T 4; W 2; I 4; A 2; Ld 7; Sv — | `Flamer.xml` | Armor 6; HP 6; MeleeAcc 8; RangedAcc 8; MeleeAttacks 1; StrengthDamage 1.5; Morale 8; Move 3; Group 3 |
| [Great Unclean One](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/5749-a0d7-e352-7e28/great-unclean-one) | 190 | WS 6; BS 3; S 6; T 7; W 6; I 4; A 5; Ld 9; Sv — | `GreatUncleanOne.xml` | Armor 0; HP 100; MeleeAcc 10; RangedAcc 6; MeleeAttacks 2; StrengthDamage 4; Morale 12; Move 3; Group 1 |
| [Keeper of Secrets](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/d221-997d-99e7-c51f/keeper-of-secrets) | 170 | WS 9; BS 6; S 6; T 6; W 5; I 10; A 6; Ld 9; Sv — | `KeeperOfSecrets.xml` | Armor 6; HP 40; MeleeAcc 12; RangedAcc 12; MeleeAttacks 5; StrengthDamage 3; Morale 12; Move 4; Group 1 |
| [Lord of Change](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/5795-6660-b297-a685/lord-of-change) | 230 | WS 6; BS 6; S 6; T 6; W 5; I 6; A 5; Ld 9; Sv — | `LordOfChange.xml` | Armor 4; HP 36; MeleeAcc 8; RangedAcc 12; MeleeAttacks 3; StrengthDamage 3; Morale 12; Move 3; Group 1 |
| [Plague Drones of Nurgle](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/6bd1-3a60-56c5-95f3/plague-drones-of-nurgle) | 42 | WS 3; BS 3; S 4; T 5; W 3; I 2; A 3; Ld 7; Sv — | `PlagueDrone.xml` | Armor 6; HP 12; MeleeAcc 8; RangedAcc 8; MeleeAttacks 1; StrengthDamage 1.5; Morale 8; Move 3; Group 3 |
| [Plaguebearers of Nurgle](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/cd60-32a3-614d-6b49/plaguebearers-of-nurgle) | 9 | WS 3; BS 3; S 4; T 4; W 1; I 2; A 1; Ld 7; Sv — | `Plaguebearer.xml` | Armor 4; HP 2.5; MeleeAcc 8; RangedAcc 8; MeleeAttacks 1; StrengthDamage 1.5; Morale 8; Move 3; Group 8 |
| [Screamers of Tzeentch](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/64c7-e41b-d44a-a822/screamers-of-tzeentch) | 25 | WS 3; BS 0; S 4; T 4; W 2; I 4; A 3; Ld 7; Sv — | `Screamer.xml` | Armor 6; HP 3; MeleeAcc 8; RangedAcc 8; MeleeAttacks 1; StrengthDamage 1.5; Morale 8; Move 4; Group 5 |
| [Seekers of Slaanesh](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/f3ea-7c9f-b1f9-ff87/seekers-of-slaanesh) | 12 | WS 5; BS 4; S 3; T 3; W 1; I 5; A 3; Ld 7; Sv — | `Seeker.xml` | Armor 6; HP 4; MeleeAcc 8; RangedAcc 8; MeleeAttacks 2; StrengthDamage 1; Morale 8; Move 4; Group 5 |
| [Skull Cannon of Khorne](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2fea-4024-4f96-117c/skull-cannon-of-khorne) | 125 | Vehicle: BS 5; AV 12/12/10 (F/S/R); HP 3 | `SkullcannonKhorne.xml` | Armor 6; HP 24; MeleeAcc 8; RangedAcc 6; MeleeAttacks 1; StrengthDamage 4; Morale 8; Move 3; Group 1 |
| [Soul Grinder of Chaos](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/bea6-b66e-ef91-7ad5/soul-grinder-of-chaos) | 135 | Walker: WS 3; BS 3; S 6; AV 13/13/11 (F/S/R); I 3; A 4; HP 4 | `SoulGrinderKhorne.xml` | Armor 8; HP 42; MeleeAcc 6; RangedAcc 6; MeleeAttacks 1; StrengthDamage 4; Morale 10; Move 3; Group 1 |

### Как читать пары характеристик

Это **сопоставление по смыслу**, а не математическое преобразование одной игровой системы в другую.

| Настольная характеристика | Ближайшее поле Gladius | Насколько корректна пара |
|---|---|---|
| WS (Weapon Skill) | MeleeAcc | Ближайшая пара: обе влияют на эффективность ближнего боя, но шкалы и формулы разные |
| BS (Ballistic Skill) | RangedAcc | Ближайшая пара: обе описывают точность стрельбы, но шкалы разные |
| S (Strength) | StrengthDamage | Только тематическая пара. StrengthDamage в XML — параметр урона атаки, а не сила модели |
| T (Toughness) | Armor + HP | Прямого поля Toughness в Gladius нет. Живучесть складывается из брони и запаса HP |
| W (Wounds) | HP | Ближайшая пара, но HP в Gladius относится к игровому юниту/отряду и не обязано совпадать с W одной миниатюры |
| I (Initiative) | Нет прямого аналога | Initiative как отдельного параметра в показанном XML юнита нет |
| A (Attacks) | MeleeAttacks | Ближайшая пара, но Gladius считает атаки по собственной боевой модели и может представлять отряд, а не одну модель |
| Ld (Leadership) | Morale | Ближайшая пара по устойчивости к потерям/подавлению; шкалы разные |
| Sv (Armour Save) и Invulnerable Save | Armor | Не эквивалентны: в Warhammer это бросок спас-броска, в Gladius Armor — параметр другой системы защиты |
| Movement / скорость | Move | Направление соответствия есть, но дюймы настолки и клетки/очки движения Gladius несопоставимы напрямую |

### Что особенно важно при балансировке

1. **Не сравнивать значения напрямую как коэффициенты.** Например, MeleeAcc 12 не означает WS 12, а HP 40 не означает 40 ран.
2. **Сравнивать роль и относительную силу внутри фракции.** Если Bloodcrusher должен быть прочнее Bloodletter, смотрим на Armor/HP/атаки/стоимость относительно других юнитов Gladius, а затем сверяем с отношением W/T/Save и очков в настолке.
3. **Отряды и модели имеют разные масштабы.** В моде Bloodletters имеют Group 8 и HP 2 в XML; нельзя трактовать HP 2 как W 2 одного Bloodletter. Это параметр Gladius, а размер группы задаётся отдельно.
4. **Профили техники не нужно насильно сводить к пехотному набору.** У Burning Chariot и Skull Cannon важны vehicle AV и HP; у Soul Grinder — Walker-профиль и AV.

> Ограничение источника: текстовый просмотр страниц New Recruit показывает названия datasheet'ов, категории, очки, опции и правила, но не отображает в читаемом тексте полные блоки характеристик каждой модели. Поэтому таблица использует профили 7e, уже записанные в этой сравнительной базе; перед использованием цифр как окончательного источника правил их следует сверить с печатным Codex: Chaos Daemons / Daemonic Incursion. Профили Gladius, напротив, извлечены непосредственно из базовых `<effects>` соответствующих XML-файлов мода.

### Экономика, размер отряда и оружие в Gladius

Здесь приведены значения из XML, они не переводятся в очки Warhammer 40,000.

| Файл | Group | Prod | Food | Ore | Energy | Influence | Upkeep |
|---|---:|---:|---:|---:|---:|---:|---|
| `Belakor.xml` | 1 | 60 | — | — | — | — | Energy 3.5 |
| `BeastOfNurgle.xml` | 1 | 54 | 100 | — | 40 | — | Food 4 |
| `Bloodcrusher.xml` | 3 | 42 | 40 | 80 | — | — | Ore 4 |
| `Bloodletter.xml` | 8 | 30 | 20 | 40 | — | — | Ore 2 |
| `Bloodthirster.xml` | 1 | 54 | 40 | 100 | — | 240 | Ore 5 |
| `BlueHorror.xml` | 8 | 36 | 20 | — | 50 | — | Energy 2.5 |
| `BurningChariot.xml` | 2 | 54 | 60 | — | 150 | — | Energy 7.5 |
| `Daemonette.xml` | 8 | 33 | 30 | — | 30 | — | Energy 2 |
| `Flamer.xml` | 3 | 48 | 40 | — | 100 | — | Energy 5 |
| `GreatUncleanOne.xml` | 1 | 54 | 100 | — | 40 | 240 | Food 5 |
| `KeeperOfSecrets.xml` | 1 | 54 | 45 | — | 45 | 180 | Energy 3 |
| `LordOfChange.xml` | 1 | 54 | 40 | — | 100 | 240 | Energy 6 |
| `PlagueDrone.xml` | 3 | 54 | 100 | — | 40 | — | Food 4 |
| `Plaguebearer.xml` | 8 | 39 | 50 | — | 20 | — | Food 2 |
| `Screamer.xml` | 5 | 48 | 40 | — | 100 | — | Energy 5 |
| `Seeker.xml` | 5 | 39 | 45 | — | 45 | — | Energy 3 |
| `SkullcannonKhorne.xml` | 1 | 36 | 15 | 50 | — | — | Ore 3 |
| `SoulGrinderKhorne.xml` | 1 | 45 | 30 | 95 | — | — | Ore 6 |

**Оружие, явно назначенное в XML этих юнитов:**

- Bloodletter — `Hellblade`; Bloodcrusher — `Hellblade`, `BladedHorn`.
- Beast of Nurgle — `CloseCombatWeapon`, `VileVomit`.
- Be'lakor — `BladeOfShadows`; `BetrayingShades` сейчас отключено.
- Bloodthirster — `AxeOfKhorne` (2 шт.), `HellfireBreath`; `AxeThrow` отключено.
- Blue Horror — `CloseCombatWeapon`, `CoruscatingBlueFlames`.
- Burning Chariot — `ScreamerBite`, `FireOfTzeentchBlue`; `FireOfTzeentchPink` отключено.
- Daemonette — `AlluringBlade`; Flamer — `FlickeringFlames`.
- Great Unclean One — `Bilesword`, `PutridVomit`.
- Keeper of Secrets — `WitstealerSword`, `SnappingClaws`; `Phantasmagoria` отключено.
- Lord of Change — `StaffOfTzeentch`; `BoltOfChange` и `EyeOfTzeentch` отключены.
- Plague Drone — `Plaguesword`, `DeathsHead`; Plaguebearer — `Plaguesword`.
- Screamer — `ScreamerBite`; Seeker — `AlluringBlade`, `LashingTounge`.
- Skull Cannon — `BitingMaw`, `Skullcannon`.
- Soul Grinder Khorne — `IronClaw` (2 шт.), `Warpsword`, `HadesAutocannon`.

## 4. Юниты 7-й редакции, которых нет как прямой реализации в моде

Ниже — то, что следует добавить, если цель — покрыть основные модели и персонажей именно кодекса 7-й редакции. Для отсутствующих юнитов Gladius-профиль не указан, потому что соответствующего XML-файла в `Units/ChaosDaemons_MT` нет.

### HQ и персонажи

| Юнит из кодекса | Профиль / стоимость 7-й редакции | Комментарий по текущему моду |
|---|---|---|
| [Daemon Prince](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/617a-017e-3d43-da2f/daemon-prince-of-khorne) | Базовый вариант 160 pts; WS9 BS5 S6 T5 W4 I8 A5 Ld9 Save – | Отдельного `DaemonPrince.xml` нет |
| [Kairos Fateweaver](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/99a9-0388-2568-adcc/kairos-fateweaver) | 300 pts; 1/6/5/5/5/2/1/9/– | Отсутствует |
| [Ku'gath, The Plaguefather](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2c4a-140f-6483-d28f/ku%27gath%2C-the-plaguefather) | 260 pts; 6/3/6/7/7/4/6/9/– | Отсутствует |
| [Skarbrand](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/ecd4-d78d-669b-128e/skarbrand) | 225 pts; профиль Bloodthirster с отдельными правилами и A7 | Отдельного `Skarbrand.xml` нет |
| [The Blue Scribes](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/d6c0-7c24-7544-31c5/the-blue-scribes) | 81 pts; WS3 BS4 S3 T3 W2 I3 A1 Ld8 Save – | Отсутствует |
| [The Masque of Slaanesh](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/cd17-3c68-14bf-1b42/the-masque-of-slaanesh) | 75 pts; 7/6/4/3/2/7/5/8/– | Отсутствует |
| [Epidemius](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/6514-6bf7-873a-1c6c/daemonic-heralds) | Herald option / named character | Отдельной модели нет |
| [Karanak](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/7651-7d14-ae01-f5a5/karanak) | 120 pts; 7/0/5/5/3/6/4/8/6+ | Отсутствует |
| [Skulltaker](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2f67-49b4-2d18-024c/skulltaker) | WS9 BS9 S5 T4 W2 I9 A4 Ld8 Save 3+ | Отсутствует |
| [The Changeling](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/cecc-a6c2-65b8-5f8c/the-changeling) | WS3 BS4 S3 T3 W2 I3 A1 Ld8 Save – | Отдельного `TheChangeling.xml` нет; `Changecaster.xml` — другой персонаж |
| [Exalted Flamer of Tzeentch](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/a893-cc46-de93-381e/burning-chariot-of-tzeentch) | Опция экипажа Burning Chariot | Нет отдельного файла/юнита Exalted Flamer |

### Heralds — профиль 7-й редакции и покрытие модом

| Herald | Очки | WS/BS/S/T/W/I/A/Ld/Save | Состояние в моде |
|---|---:|---|---|
| [Herald of Khorne](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/eff5-c688-5678-5765/herald-of-khorne) | 55 | 7/7/5/4/2/6/3/8/6+ | `Bloodmaster.xml` — тематический аналог, профиль не совпадает |
| [Herald of Nurgle](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/7e71-1691-295a-6121/herald-of-nurgle) | 45 | 5/5/5/5/2/4/3/8/– | Нет прямого аналога; `SloppityBilepiper.xml` — персонаж другой редакции |
| [Herald of Slaanesh](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/68cf-71eb-8c4c-320b/herald-of-slaanesh) | 45 | 7/6/4/3/2/7/4/8/– | Нет прямого аналога; `InfernalEnrapturess.xml` — персонаж другой редакции |
| [Herald of Tzeentch](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/eeb8-23a2-fd50-af88/herald-of-tzeentch) | 45 | 3/4/3/3/2/3/2/8/– | `Changecaster.xml` — тематический аналог, профиль не совпадает |

Вариант Heralds в New Recruit включает также Epidemius, Exalted Flamer, Karanak, Skulltaker и The Changeling. Это отдельные выборы/модели в составе записи Daemonic Heralds, а не один общий профиль.

### Troops, Elites, Fast Attack и Heavy Support

| Юнит из кодекса | Очки / профиль 7-й редакции | Что отсутствует в моде |
|---|---|---|
| [Brimstone Horrors](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/775c-3811-a4ef-b810/brimstone-horrors) | 3 pts; WS3 BS3 S1 T1 W2 I3 A2 Ld7 Save – | Отдельный юнит отсутствует |
| [Chaos Furies](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/ff7a-3ecc-03d0-fd15/furies) | 6 pts; WS3 BS0 S4 T3 W1 I4 A1 Ld2 Save – | Отсутствуют |
| [Fiends of Slaanesh](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/16ff-3a54-df8a-91f7/fiends) | 35 pts; WS4 BS0 S4 T4 W3 I6 A3 Ld7 Save – | Отсутствуют |
| [Flesh Hounds of Khorne](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/4e4d-a45d-7df4-c7e6/flesh-hounds) | 16 pts; WS5 BS0 S4 T4 W2 I4 A2 Ld7 Save 6+ | Отсутствуют |
| [Hellflayer of Slaanesh](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/00f6-3ffc-d9af-0d15/hellflayers-of-slaanesh) | 60 pts; Chariot BS4, F11/S11/R10, HP2 | Отсутствует |
| [Nurglings](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/d33e-ee7f-c01a-caa4/nurglings) | 15 pts; WS3 BS3 S3 T3 W4 I3 A4 Ld7 | Отсутствуют |
| [Pink Horrors](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/3447-cf24-ee8f-0115/pink-horrors) | 9 pts; WS3 BS3 S3 T3 W1 I3 A1 Ld7 Save – | Отдельный юнит отсутствует |
| [Daemon Prince — Heavy Support](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/a9e3-d5f0-1f80-56db/daemon-prince) | Отдельный выбор Daemon Prince в Heavy Support; профиль Daemon Prince см. выше | Отсутствует |
| [Bloodletter / Bloodcrusher / Daemonette / Plaguebearer / Blue Horror](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex) | Все пять основных типов представлены отдельными записями | Brimstone и Pink Horror — не представлены |
| [Burning Chariot / Skull Cannon / Soul Grinder](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex) | Все три тяжёлых/машинных datasheet'а присутствуют | Для Skull Cannon в 7-й редакции — Khorne-модель; варианты других богов в моде являются авторскими вариантами |

### Отдельно: персонажи и юниты, которые есть в моде, но не являются datasheet'ами кодекса 7-й редакции

Следующие файлы существуют в папке фракции, однако их нельзя считать недостающими профилями 7e или точными аналогами юнитов старого кодекса:

- `InfernalEnrapturess.xml` — персонаж более позднего ростера, не Herald of Slaanesh из 7e.
- `SloppityBilepiper.xml` — персонаж более позднего ростера, не Herald of Nurgle из 7e.
- `Bloodmaster.xml` — современный Khorne-персонаж/аналог роли Herald of Khorne.
- `Changecaster.xml` — современный Tzeentch-персонаж/аналог роли Herald of Tzeentch.

Также в `Units/ChaosDaemons_MT` есть `Bullgryn.xml`, `ChaosCultist.xml`, `ChaosLord.xml`, `ChaosSpaceMarine.xml`, `Havoc.xml`, `HeavyWeaponsSquad.xml`, `Heldrake.xml`, `Hydra.xml`, `KnightDesecrator.xml`, `LandRaider.xml`, `LemanRussBattleTank.xml`, `LordCommissar.xml`, `LordOfSkulls.xml`, `MasterOfPossession.xml`, `Maulerfiend.xml`, `Obliterator.xml`, `ScoutSentinel.xml`, `WarDogStalker.xml`, `WarpRift.xml`, `WarpTalon.xml`, `Headquarters.xml`. Они являются частью интеграции/авторского ростера Gladius, но не заменяют автоматически отсутствующие datasheet'ы Chaos Daemons 7e.

## 5. Приоритетный список для доведения модa до покрытия 7-й редакции

1. **Ключевые отсутствующие боевые юниты:** Flesh Hounds, Fiends, Nurglings, Pink Horrors, Brimstone Horrors, Chaos Furies, Hellflayers.
2. **Отсутствующие крупные персонажи:** Daemon Prince, Kairos Fateweaver, Ku'gath, Skarbrand.
3. **Отсутствующие персонажи/варианты Heralds:** The Blue Scribes, The Masque, Epidemius, Karanak, Skulltaker, The Changeling, отдельный Exalted Flamer; Herald of Nurgle и Herald of Slaanesh.
4. **Разделение уже существующего:** три профиля Bloodthirster (Insensate Rage / Unfettered Fury / Wrath of Khorne) сейчас сведены в один `Bloodthirster.xml`. В настолке у них разные цены, вооружение и отдельные правила; стоит решить, нужно ли делать в Gladius отдельные юниты или оставить их как один игровой архетип.
5. **Сверка тяжёлой техники:** Soul Grinder в настолке один datasheet с выбором покровителя/опций вооружения, а в моде это четыре отдельных юнита. Skull Cannon — настольная модель Кхорна; Nurgle/Slaanesh/Tzeentch-варианты в моде не имеют прямого соответствия в этом кодексе.

## 6. Проверенные файлы текущей папки мода

Папка `Data/World/Units/ChaosDaemons_MT` содержит следующие 50 XML-файлов:

`BeastOfNurgle.xml`, `Belakor.xml`, `Bloodcrusher.xml`, `Bloodletter.xml`, `Bloodmaster.xml`, `Bloodthirster.xml`, `BlueHorror.xml`, `Bullgryn.xml`, `BurningChariot.xml`, `Changecaster.xml`, `ChaosCultist.xml`, `ChaosLord.xml`, `ChaosSpaceMarine.xml`, `Daemonette.xml`, `Flamer.xml`, `GreatUncleanOne.xml`, `Havoc.xml`, `Headquarters.xml`, `HeavyWeaponsSquad.xml`, `Heldrake.xml`, `Hydra.xml`, `InfernalEnrapturess.xml`, `KeeperOfSecrets.xml`, `KnightDesecrator.xml`, `LandRaider.xml`, `LemanRussBattleTank.xml`, `LordCommissar.xml`, `LordOfChange.xml`, `LordOfSkulls.xml`, `MasterOfPossession.xml`, `Maulerfiend.xml`, `Obliterator.xml`, `PlagueDrone.xml`, `Plaguebearer.xml`, `ScoutSentinel.xml`, `Screamer.xml`, `Seeker.xml`, `SkullcannonKhorne.xml`, `SkullcannonNurgle.xml`, `SkullcannonSlaanesh.xml`, `SkullcannonTzeentch.xml`, `SloppityBilepiper.xml`, `SoulGrinderKhorne.xml`, `SoulGrinderNurgle.xml`, `SoulGrinderSlaanesh.xml`, `SoulGrinderTzeentch.xml`, `WarDogStalker.xml`, `WarpRift.xml`, `WarpTalon.xml`.

---

## Источники профилей

- [Каталог Chaos Daemons 7th Edition](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex)
- [Be'lakor](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/4364-0360-c913-91c4/be%27lakor%2C-the-dark-master)
- [Bloodthirster — Insensate Rage](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/c16e-320b-e286-059e/bloodthirster-of-insensate-rage), [Unfettered Fury](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/a387-df65-c063-8b9a/bloodthirster-of-unfettered-fury), [Wrath of Khorne](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/4ac0-632a-80e4-f66e/wrath-of-khorne-bloodthirster)
- [Great Unclean One](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/5749-a0d7-e352-7e28/great-unclean-one), [Kairos](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/99a9-0388-2568-adcc/kairos-fateweaver), [Keeper](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/d221-997d-99e7-c51f/keeper-of-secrets), [Ku'gath](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2c4a-140f-6483-d28f/ku%27gath%2C-the-plaguefather), [Lord of Change](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/5795-6660-b297-a685/lord-of-change), [Skarbrand](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/ecd4-d78d-669b-128e/skarbrand)
- [Blue Horrors](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/b77b-9911-3d41-85b9/blue-horrors), [Brimstone Horrors](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/775c-3811-a4ef-b810/brimstone-horrors), [Pink Horrors](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/3447-cf24-ee8f-0115/pink-horrors)
- [Daemon Prince](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/617a-017e-3d43-da2f/daemon-prince-of-khorne), [Herald of Khorne](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/eff5-c688-5678-5765/herald-of-khorne), [Herald of Nurgle](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/7e71-1691-295a-6121/herald-of-nurgle), [Herald of Slaanesh](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/68cf-71eb-8c4c-320b/herald-of-slaanesh), [Herald of Tzeentch](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/eeb8-23a2-fd50-af88/herald-of-tzeentch)
- [Beast of Nurgle](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/f341-0a10-d29c-ba9f/beasts), [Bloodcrushers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/95fb-a926-71d8-c0c0/bloodcrushers), [Bloodletters](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/0388-83e6-f4f8-71f6/bloodletters), [Daemonettes](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/01ae-db1f-a7a3-8773/daemonettes)
- [Furies](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/ff7a-3ecc-03d0-fd15/furies), [Fiends](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/16ff-3a54-df8a-91f7/fiends), [Flamers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/e407-1ea5-659c-5858/flamers), [Flesh Hounds](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/4e4d-a45d-7df4-c7e6/flesh-hounds)
- [Nurglings](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/d33e-ee7f-c01a-caa4/nurglings), [Plague Drones](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2dbb-806a-ea09-fc13/plague-drones), [Plaguebearers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/7cee-b1d5-693b-a28d/plaguebearers), [Screamers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/5e4f-7d93-beac-c8fd/screamers), [Seekers](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/6760-51e4-b79a-bdce/seekers)
- [Hellflayer](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/00f6-3ffc-d9af-0d15/hellflayers-of-slaanesh), [Skull Cannon](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2fea-4024-4f96-117c/skull-cannon-of-khorne), [Soul Grinder](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/bea6-b66e-ef91-7ad5/soul-grinder-of-chaos)
- [The Blue Scribes](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/d6c0-7c24-7544-31c5/the-blue-scribes), [The Masque](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/cd17-3c68-14bf-1b42/the-masque-of-slaanesh), [Karanak](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/7651-7d14-ae01-f5a5/karanak), [Skulltaker](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/2f67-49b4-2d18-024c/skulltaker), [The Changeling](https://www.newrecruit.eu/wiki/wh40k-7th-edition/warhammer-40%2C000-7th-edition/chaos-daemons%3A-codex/cecc-a6c2-65b8-5f8c/the-changeling)
