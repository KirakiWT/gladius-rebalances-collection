# Fallen Battle Sisters for Chaos — test add-on

Adds one six-model Fallen Battle Sisters squad to **Chaos Space Marines**. This is an independent add-on for the repository's **Faction Reworks All-In-One Eradication Integrated** package. It does not replace or edit any existing mod files.

## Gameplay integration

- Unit ID: `ChaosSpaceMarines/FallenBattleSister`
- Unlock: Chaos Space Marines Infantry branch, technology position 4; requires `ChaosSpaceMarines/Infantry`
- Production: adds one `produceUnit` entry through `Infantry.xml.ext`
- Squad size: 6
- Unit and technology icon: both explicitly reference the existing `Units/SistersOfBattle/SaintCelestine` resource
- Combat profile: copied from the All-In-One Battle Sister definition (armour, health, accuracy, melee profile, morale, movement and production value)
- Weapons: Battle Sister `Boltgun` plus the generic Gladius `CloseCombatWeapon` slot
- Sounds: reuses the All-In-One Battle Sister infantry movement and death sounds
- Permanent Chaos Space Marine statuses: `ChaosSpaceMarines/ChampionOfChaos` and `ChaosSpaceMarines/LeaderOfChaos`
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
| `FallenBattleSister_Diffuse.png` | `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterDiffuse.dds` |
| `FallenBattleSister_Normal.png` | `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterNormal.dds` |
| `FallenBattleSister_Metallic.png` + inverted `FallenBattleSister_Roughness.png` | `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterSIC.dds` |

The material definition already refers to the Diffuse, Normal and SIC resource names. The three DDS files above still need to be generated and copied to the listed paths; raw PNGs are source files, not the finished Gladius texture assets. No emissive/team-colour source was supplied, so those channels are not authored.

## Load order and testing

In the Gladius mod list, place **Faction Reworks All-In-One above this add-on** and **Fallen Battle Sisters for Chaos below it**. The add-on's `Infantry.xml.ext` then merges the Fallen Battle Sisters production entry into the All-In-One `ChaosSpaceMarines/Infantry` building (Abominator's Genelab).

This is a test build and has **not** been tested in-game. Confirm mesh compilation, animation playback, muzzle/bone names, animation event timings, production availability, texture appearance and localization in a local match. English and Russian localization is supplied through partial `Units.xml`, `Upgrades.xml` and `Traits.xml` files under each language folder. Core language `.xml.ext` sidecars are intentionally not used.

The game requires the Adepta Sororitas content that supplies the reused Saint Celestine icon (`Supplement11`).


## Bone attachment references

The death/blood and explosion effect anchors currently use `bip01 spine1`, but the latest runtime test still fails with `Blood.cpp:26` (`boneID != -1`). The fact that `bip01 spine1` appears in animation tracks (ID 29) does not prove it exists in the mesh skeleton; the exact mesh Armature bone name must be checked in Blender before choosing the final value. Gladius expects **bone names, not numeric bone IDs**, in these unit XML fields. The bolter `muzzleBone` uses the custom skeleton marker `marker_fx_bolter_01_fire`. Blender workflow and the distinction between mesh bone IDs and unit-level bone-name references are documented in [BLENDER_BONE_REFERENCES.md](BLENDER_BONE_REFERENCES.md).

## Animation file format and path resolution

The five animation files are intentionally stored as **Proxy Studios source XML** under `Data/Video/Animations/Units/ChaosSpaceMarines/`. This is the editable export format produced by the official Blender exporter. Gladius compiles animation XML into encrypted runtime `.anm` data when the game loads the mod. Do **not** rename these XML source files to `.anm`.

The in-game unit XML references animation resource stems (without either `.xml` or `.anm` extension). The exact file-to-reference mapping and the comparison with the precompiled `.anm` assets used by the repository's Chaos Demons mod are documented in [ANIMATION_FORMAT_AND_PATHS.md](ANIMATION_FORMAT_AND_PATHS.md).

One timing item remains for in-game/Blender review: the bolter clip reports 17 frames at 24 fps, while the unit currently uses `beginFire="0.67"` and `endFire="1.97"`. Do not assume this window matches the clip duration; scrub the exported attack animation and tune the firing window only after checking the visible muzzle/projectile timing.

## Latest startup log finding

The 2026-11-19 startup log reports a fatal engine assertion `frameRate == 30` for all five Fallen Battle Sister animation clips. Their current source XML headers use 24 fps. Re-export all five animations from Blender with the Proxy Studios exporter at 30 fps, preserving intended clip duration; do not just rename XML to ANM or blindly change the header. See [ANIMATION_FORMAT_AND_PATHS.md](ANIMATION_FORMAT_AND_PATHS.md) for the log diagnosis and safe re-export checklist. The required All-In-One dependency was disabled in the reported run and should be enabled above this add-on during testing.


## Production building

Fallen Battle Sister is already registered in `Data/World/Buildings/ChaosSpaceMarines/Infantry.xml.ext`, which extends the `ChaosSpaceMarines/Infantry` building localized by All-In-One as **Abominator's Genelab**. Production is gated by the tier-IV `ChaosSpaceMarines/FallenBattleSister` technology. The latest log records the local All-In-One folder as disabled but also records an enabled Workshop item at `steamapps/workshop/content/489630/3841700987`; the user confirms that enabled Workshop item is the same All-In-One version. The Workshop dependency was therefore active in that run.
