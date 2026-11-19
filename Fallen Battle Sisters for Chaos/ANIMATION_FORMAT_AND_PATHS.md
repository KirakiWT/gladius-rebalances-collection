# Fallen Battle Sister — animation format and path audit

Audit date: 2026-11-19

## Finding: XML is the correct editable export format

The five animation files in this add-on are **Proxy Studios animation source XML**, not arbitrary XML wrappers. Their opening structure is the expected animation document form:

```xml
<?xml version="1.0" encoding="utf-8"?>
<animation version="0.9" frames="..." frameRate="24">
    <bone id="0" name="...">
```

The game’s asset pipeline converts animation XML under `Data/Video/Animations/` into encrypted compiled `.anm` data at load time. The `.anm` extension therefore identifies the compiled/runtime animation format; it is not the extension that should be assigned to the Blender exporter’s XML output.

Do not rename an exported `.xml` animation to `.anm`. That only changes the filename, not the data format.

## Why the Chaos Demons mod contains .anm files

The repository's **Chaos Demons Faction [FRAIO Integration]** package includes compiled animation files, for example:

- `Data/Video/Animations/Units/Reinforcements_MT/Belakor/Idle0.anm`
- `Data/Video/Animations/Units/Reinforcements_MT/Belakor/Die.anm`
- `Data/Video/Animations/Units/Reinforcements_MT/Belakor/Charge.anm`

Its unit definition, `Data/World/Units/ChaosDaemons_MT/Belakor.xml`, refers to these clips by extensionless resource stems, for example:

```xml
idleAnimation="Units/Reinforcements_MT/Belakor/Idle"
<action animation="Units/Reinforcements_MT/Belakor/Die"/>
```

This is consistent with the Gladius convention: World XML references the logical animation resource path and omits the file extension. A mod may therefore contain precompiled `.anm` resources, while our custom Blender-exported source assets can remain as `.xml` for the engine to compile.

## Fallen Battle Sister path audit

The unit definition is:

`Data/World/Units/ChaosSpaceMarines/FallenBattleSister.xml`

Its logical resource paths resolve as follows:

| World/unit XML field | File in this add-on | Audit |
|---|---|---|
| `mesh="Units/ChaosSpaceMarines/FallenBattleSister"` | `Data/Video/Meshes/Units/ChaosSpaceMarines/FallenBattleSister.xml` | Match |
| `material="Units/ChaosSpaceMarines/FallenBattleSister"` | `Data/Video/Materials/Units/ChaosSpaceMarines/FallenBattleSister.xml` | Match |
| `idleAnimation="Units/ChaosSpaceMarines/FallenBattleSisterIdle"` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterIdle.xml` | Match |
| attack `animation=".../FallenBattleSisterAttack"` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterAttack.xml` | Match |
| `meleeAnimation=".../FallenBattleSisterMelee"` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterMelee.xml` | Match |
| die `animation=".../FallenBattleSisterDie"` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterDie.xml` | Match |
| move `animation=".../FallenBattleSisterMove"` | `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSisterMove.xml` | Match |

All five animation source XML files were verified to exist at these exact paths. Their opening XML headers declare the `animation` root and version `0.9`; the clips currently report:

| Clip | Frames | Frame rate | Approx. duration at 24 fps |
|---|---:|---:|---:|
| Idle | 91 | 24 | 3.79 s |
| Move | 31 | 24 | 1.29 s |
| Bolter Attack | 17 | 24 | 0.71 s |
| Melee | 61 | 24 | 2.54 s |
| Die | 31 | 24 | 1.29 s |

Duration is an approximate frame-count calculation; final playback must be verified in-game.

## Timing warning — bolter attack

The unit currently declares:

```xml
beginFire="0.67"
endFire="1.97"
```

The bolter animation source declares 17 frames at 24 fps (about 0.7 seconds). The firing window therefore appears suspicious: the start is near the end of the clip and the end value is beyond its nominal duration.

Gladius documentation describes `beginFire` / `endFire` as controlling when projectile/SFX visibility starts and ends; they do not lengthen the underlying animation. This is a **timing item to verify**, not a confirmed defect: scrub the bolter clip in Blender and test in a skirmish before changing the values. The melee window (`0.2`–`0.9`) is within the approximate 2.54-second melee clip.

## What remains to test

1. Start a fresh skirmish after updating the mod.
2. Confirm idle, move, ranged attack, melee, and death clips play on the custom armature.
3. Confirm the firing effect uses the `marker_fx_bolter_01_fire` bone and appears at the bolter muzzle.
4. Tune `beginFire` and `endFire` against the exported clip's actual timing.
5. Confirm the engine's XML-to-`.anm` compilation produces no animation-load errors.

## References

- Gladius modding glossary — XML is editable source; `.anm` is encrypted runtime output from animation XML: https://modtools.toffster.dev/guides/gladius/glossary
- Models & animation — folder layout, XML-to-`.anm` pipeline, Blender export workflow, action references: https://modtools.toffster.dev/guides/gladius/14-models-and-animation
- Blender Import & Export — official exporter and import tool format support: https://modtools.toffster.dev/tools/gladius-blender-import
- Chaos Demons Be'lakor unit definition in this repository: https://github.com/KirakiWT/gladius-rebalances-collection/blob/main/Chaos%20Demons%20Faction%20%5BFRAIO%20Integration%5D/Data/World/Units/ChaosDaemons_MT/Belakor.xml
- Chaos Demons Be'lakor compiled animations in this repository: https://github.com/KirakiWT/gladius-rebalances-collection/tree/main/Chaos%20Demons%20Faction%20%5BFRAIO%20Integration%5D/Data/Video/Animations/Units/Reinforcements_MT/Belakor
