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

## Fatal startup crash found in logs (2026-11-19)

The new `Gladius.error.log` identifies the fatal error during `Loading animations ...`:

```
Animation.cpp:150
Assertion "frameRate == 30" failed
```

The engine names all five custom clips as failures:

- `FallenBattleSisterAttack`
- `FallenBattleSisterMove`
- `FallenBattleSisterDie`
- `FallenBattleSisterMelee`
- `FallenBattleSisterIdle`

The corresponding source XML files in this add-on currently declare `frameRate="24"`. The mesh/material/animation resource paths resolve to the files that exist; the fatal assertion is the animation frame-rate check, not a missing `.anm` extension or a bad folder path.

**Required correction:** re-export all five clips through the Proxy Studios Animation exporter at 30 fps. In Blender, set Output Properties → Format → Frame Rate to 30 fps (FPS Base 1.0), verify the animation range, export each clip again, and confirm every output header says `frameRate="30"`. Keep the files as XML; Gladius compiles them to `.anm` at runtime.

**Timing caution:** merely changing the XML header from 24 to 30 is not a safe final fix. It makes the same frame samples play at a shorter duration. Since these clips are currently authored/exported at 24 fps, preserve their real-time duration when converting/resampling them to 30 fps. Re-sample the animated pose over time or retime the keyframe sequence appropriately before export, then review playback and the `beginFire` / `endFire` window in game. The existing bolter clip has 17 frames at 24 fps, so its fire window should be revisited after a correctly timed 30 fps export.

**Additional log context:** the dependency mod `Faction Reworks All-In-One Eradication Integrated` is listed under Disabled for this run, even though the Fallen Battle Sisters add-on expects it. Enable All-In-One above this add-on for integration testing. The fallback-icon warnings are secondary to the fatal animation assertion. The `Marked content corrupt` line appears after the crash and is a consequence of the crash-handling configuration, not its root cause.

No animation or mesh asset files were modified by this log review.


## Follow-up runtime spawn failure (2026-11-19)

The latest debug spawn reaches unit construction and fails at:

```
Blood.cpp:26
Assertion "boneID != -1" failed
```

The unit XML had `bloodBone="bip01 spine"`. The supplied animation exports contain `bip01 spine1` as a named bone (bone ID 29), while the exact `bip01 spine` string is not present in those animation exports. The unit XML now uses `bip01 spine1` for both `bloodBone` and `explosionsBone`. This is grounded in the exported animation skeleton, but the next in-game spawn must confirm that the mesh resolves this name.

The same log shows **Faction Reworks All-In-One Eradication Integrated** disabled and the Fallen Battle Sisters add-on enabled. Enable All-In-One above this add-on so its Abominator's Genelab integration is active.

The log also records non-fatal missing resource warnings for the unit icon and the three runtime DDS textures (Diffuse, Normal, SIC). These are separate from the fatal `Blood.cpp` assertion.



## Log clarification: Workshop All-In-One is enabled

In the latest `Logs(4).zip`, the local folder copy `Mods/Faction Reworks All-In-One Eradication Integrated` appears in `Mods/Disabled`, but a separate Workshop item `steamapps/workshop/content/489630/3841700987` appears as `Mod enabled`. The user confirms this Workshop item is the same All-In-One version. The log therefore does **not** establish that All-In-One is completely disabled; the earlier diagnosis conflated the disabled local duplicate with the enabled Workshop copy. The local Fallen Battle Sisters mod is also shown as enabled.

The persistent spawn failure is independent of that load-order interpretation: the stack trace fails in `Blood::Blood` with `boneID != -1`. The current `bloodBone="bip01 spine1"` remains unverified against the actual mesh Armature. Animation track names alone cannot prove mesh-bone lookup will succeed. Use the Blender Armature-name inspection documented in `BLENDER_BONE_REFERENCES.md`; do not guess another name or statically parse the large mesh XML.
