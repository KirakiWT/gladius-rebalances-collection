# Blender and Gladius bone references — Fallen Battle Sister

This note records how the Fallen Battle Sister model's effect anchors are referenced, so a later mesh or animation export does not silently lose the required unit-level settings.

## Current unit XML settings

File: `Data/World/Units/ChaosSpaceMarines/FallenBattleSister.xml`

The death/blood and explosion effect anchors both point to the supplied skeleton bone name:

```xml
bloodBone="bip01 spine1"
explosionsBone="bip01 spine1"
```

The previous `bloodBone="Chest"` came from the Sisters template and did not match the custom Dawn of War-derived skeleton name supplied for this model. These two attributes now use the custom skeleton's `bip01 spine1` name.

The bolter projectile effect is a separate attachment and uses the custom model marker:

```xml
<projectileWeapon muzzleBone="marker_fx_bolter_01_fire"/>
```

This is the supplied skeleton marker for the bolter firing effect. Do not change `muzzleBone` to the spine just to satisfy the death-effect anchor: the shot and muzzle flash must originate at the bolter barrel.

## Bone name or numeric ID?

Use the **bone name**, not the numeric bone ID, in unit fields such as `bloodBone`, `explosionsBone`, `muzzleBone`, and weapon `bone`.

The exported mesh format has both:
- `id`: a zero-based index used inside the mesh data, including vertex-to-bone weight references;
- `name`: the actual skeleton bone name.

The Proxy Studios exporter source shown by a Proxy Studios developer first resolves each skin-weight bone ID to its bone name, builds a list of names, then writes mesh entries as `<bone id="..." name="...">`. The unit-level examples use readable names such as `ChestBone`, `RightHandBone`, and weapon muzzle-bone names. Numeric IDs are local indices in one export and are not stable attachment identifiers.

References:
- Proxy Studios forum post with the Mesh Exporter code: https://forum.slitherine.com/viewtopic.php?t=49318
- Gladius unit attributes (`bloodBone`, weapon `bone`, `muzzleBone`): https://gladiusrelicsofwar.fandom.com/wiki/Modding:units
- Blender import/export workflow: https://modtools.toffster.dev/tools/gladius-blender-import

## Where this is configured

There is **no dedicated “blood/explosion point” switch in the Blender exporter**.

1. In Blender, select the Armature object and switch to Edit Mode or Pose Mode.
2. Select the bone and inspect its exact name in Bone Properties (green bone icon), or select it and press `F2` to rename it.
3. Preserve the exact spelling, spaces, and capitalization. The string in the Gladius unit XML must match the bone name exported with the mesh.
4. Export the skinned mesh with **File → Export → Proxy Studios Mesh (.xml)**. Export animations separately with **File → Export → Proxy Studios Animation (.xml)**.
5. Keep the effect references in the unit definition at `Data/World/Units/...`; the mesh/animation exporter does not automatically write those unit XML attributes.

The separate community **Gladius Import** add-on has its import controls in the 3D Viewport sidebar (`N` key) → **Gladius** tab. It imports/inspects meshes, animations, textures, and unit XML; it is not where `bloodBone` or `muzzleBone` are authored.

## Checks still required in-game

- Confirm the exact bone spelling/case in the custom exported skeleton. This project intentionally avoids statically inspecting the very large mesh XML; the final confirmation is in Blender or in-game.
- Confirm that death blood/explosion effects originate around the upper torso with `bip01 spine1`.
- Confirm the bolter muzzle effect using `marker_fx_bolter_01_fire`. If the muzzle flash/projectile is offset, inspect this marker position in Blender; keep `muzzleBone` tied to the marker rather than the spine.
- Do not rename or rebuild the Dawn of War skeleton merely to match the vanilla Sisters names; keep animation bone names consistent across mesh and all animation exports.



## Runtime follow-up: blood anchor name

The latest debug spawn failed at `Blood.cpp:26` with `Assertion "boneID != -1" failed`. This means the engine could not resolve the configured `bloodBone` name against the loaded model skeleton.

The previous `bip01 spine` value was not found as an exact bone name in the supplied animation exports. The exported Attack, Move, and Die clips contain a bone named `bip01 spine1` (animation bone ID 29). The unit-level blood and explosion anchors have therefore been changed to `bip01 spine1`. Confirm this candidate with another in-game spawn; the large mesh XML remains intentionally uninspected.

## Production building

The unit is already registered in `Data/World/Buildings/ChaosSpaceMarines/Infantry.xml.ext`. The building ID `ChaosSpaceMarines/Infantry` is localized by All-In-One as **Abominator's Genelab**. Its `produceUnit` entry is gated by the tier-IV `ChaosSpaceMarines/FallenBattleSister` upgrade. The latest log shows All-In-One disabled, so enable that mod above this add-on when testing production.

The same log contains non-fatal missing texture warnings for the three runtime DDS maps and missing unit/upgrade GUI icons. These are separate from the fatal blood-bone assertion.



## Blender verification required after repeated spawn crash

The latest log still fails at `Blood.cpp:26` with `boneID != -1` while constructing the Blood effect. The unit XML currently names `bip01 spine1`, but finding this string in animation tracks is not sufficient proof that the mesh skeleton contains that bone. Blood-effect bone lookup happens against the loaded mesh/model skeleton.

Do not choose another name based only on animation XML or by guessing. In Blender 5.1.2, open the original Fallen Sister .blend containing the **same Armature used to export fallsister3**, switch to the Scripting workspace, create a new text block, and run:

```python
import bpy

for obj in bpy.context.scene.objects:
    if obj.type == "ARMATURE":
        print("\\nARMATURE:", obj.name)
        for bone in obj.data.bones:
            if any(term in bone.name.casefold() for term in ("spine", "chest", "torso")):
                print(repr(bone.name))
```

Use the exact printed bone name (including capitalization, spaces, and suffixes) for `bloodBone` and, if the explosion anchor is intended to share the same point, `explosionsBone`. Then export the mesh and confirm in-game. Do not statically inspect the large mesh XML for this check.

If several Armature objects appear, identify the one actually bound to the Fallen Sister mesh; do not select a control rig or an unused source rig.
