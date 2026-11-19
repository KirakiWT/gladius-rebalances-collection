# Fallen Battle Sisters for Chaos — test add-on

Adds one six-model Fallen Battle Sisters squad to **Chaos Space Marines**. This is an independent add-on for the repository's **Faction Reworks All-In-One Eradication Integrated** package. It does not replace or edit any existing mod files.

## Gameplay integration

- Unit ID: `ChaosSpaceMarines/FallenBattleSister`
- Unlock: Chaos Space Marines Infantry branch, technology position 4; requires `ChaosSpaceMarines/Infantry`
- Production: adds one `produceUnit` entry through `Infantry.xml.ext`
- Squad size: 6
- Unit and technology icon: reuses the existing `Units/SistersOfBattle/SaintCelestine` resource
- Combat profile: copied from the All-In-One Battle Sister definition (armour, health, accuracy, melee profile, morale, movement and production value)
- Weapons: Battle Sister `Boltgun` plus the generic Gladius `CloseCombatWeapon` slot
- Sounds: reuses the All-In-One Battle Sister infantry movement and death sounds
- CSM economy conversion: Battle Sister Requisition cost/upkeep are represented as 20 Food + 20 Ore and 2 Food upkeep, since Chaos Space Marines do not use the Sororitas Requisition economy

### Melee implementation note

The All-In-One Seraphim unit does not declare a separate named melee weapon in its `<weapons>` block; its melee behaviour is represented by the unit melee statline. This test unit adds the engine's generic `CloseCombatWeapon` slot and points its melee action to the supplied `attack_melee.xml` clip. The Battle Sister melee stat values are retained as requested.

## Model and animation resources

The supplied current mesh is `fallsister3.xml`; the obsolete `fallsister2.xml` is intentionally not used.

The model and five animation XML files are now placed in the mod's Gladius data hierarchy:

| Supplied file | Installed mod path |
|---|---|
| `fallsister3.xml` | `Data/Video/Meshes/Units/ChaosSpaceMarines/FallenBattleSister.xml` |
| `idle.xml` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterIdle.xml` |
| `run.xml` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterMove.xml` |
| `attack_bolter.xml` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterAttack.xml` |
| `attack_melee.xml` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterMelee.xml` |
| `death.xml` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterDie.xml` |

These names match the resource identifiers already referenced by `Data/World/Units/ChaosSpaceMarines/FallenBattleSister.xml`. The XML asset contents have not been statically inspected; mesh compilation and animation playback must be checked in-game.

## Texture sources and remaining DDS step

The supplied PNG source maps are preserved under `Assets/SourceTextures/` and are not placed in the runtime texture folder yet:

| Source PNG | Intended game texture |
|---|---|
| `Combined_base.png` | `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterDiffuse.dds` |
| `Combined_normal.png` | `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterNormal.dds` |
| `Combined_metallic.png` + inverted `Combined_roughness.png` | `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterSIC.dds` |

The material definition already refers to the Diffuse, Normal and SIC resource names. The three DDS files above still need to be generated and copied to the listed paths; raw PNGs are source files, not the finished Gladius texture assets. No emissive/team-colour source was supplied, so those channels are not authored.

## Load order and testing

Load **Faction Reworks All-In-One** first and this add-on **below it**. The World building extension then merges into the All-In-One Chaos Space Marines Infantry building.

This is a test build and has **not** been tested in-game. Confirm mesh compilation, animation playback, muzzle/bone names, animation event timings, production availability, texture appearance and localization in a local match. Core language `.xml.ext` support is less reliable than World `.xml.ext`; verify both English and Russian strings in-game.

The game requires the Adepta Sororitas content that supplies the reused Saint Celestine icon (`Supplement11`).
