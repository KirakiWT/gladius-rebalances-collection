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

## Resource names

The supplied current mesh is `fallsister3.xml`; the obsolete `fallsister2.xml` is intentionally not used.

| Supplied resource | Mod resource name |
|---|---|
| `fallsister3.xml` | `Data/Video/Meshes/Units/ChaosSpaceMarines/FallenBattleSister.xml` |
| `attack_bolter.xml` | `FallenBattleSisterAttack.xml` |
| `attack_melee.xml` | `FallenBattleSisterMelee.xml` |
| `death.xml` | `FallenBattleSisterDie.xml` |
| `idle.xml` | `FallenBattleSisterIdle.xml` |
| `run.xml` | `FallenBattleSisterMove.xml` |

Texture mapping:
- `Combined_base.png` → Diffuse
- `Combined_normal.png` → Normal
- Metallic + inverted Roughness → SIC red/specular channel
- No emissive or team-colour source was supplied, so SIC green/blue are left black

The icon is referenced from the base game/All-In-One instead of duplicated.

## Load order and testing

Load **Faction Reworks All-In-One** first and this add-on **below it**. The World building extension then merges into the All-In-One Chaos Space Marines Infantry building.

This is a test build and has **not been tested in-game**. Confirm mesh compilation, animation playback, muzzle/bone names, animation event timings, production availability and localization in a local match. Core language `.xml.ext` support is less reliable than World `.xml.ext`; verify both English and Russian strings in-game.

The game requires the Adepta Sororitas content that supplies the reused Saint Celestine icon (`Supplement11`).
