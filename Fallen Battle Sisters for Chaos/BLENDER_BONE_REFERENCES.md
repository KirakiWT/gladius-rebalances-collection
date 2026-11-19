# Blender and Gladius bone references — Fallen Battle Sister

This note records how the Fallen Battle Sister model's effect anchors are referenced, so a later mesh or animation export does not silently lose the required unit-level settings.

## Current unit XML settings

File: `Data/World/Units/ChaosSpaceMarines/FallenBattleSister.xml`

The death/blood and explosion effect anchors both point to the supplied skeleton bone name:

```xml
bloodBone="bip01 spine"
explosionsBone="bip01 spine"
```

The previous `bloodBone="Chest"` came from the Sisters template and did not match the custom Dawn of War-derived skeleton name supplied for this model. These two attributes now use the custom skeleton's `bip01 spine` name.

The bolter projectile effect is a separate attachment and remains:

```xml
<projectileWeapon muzzleBone="Muzzle"/>
```

Do not change `muzzleBone` to the spine just to satisfy the death-effect anchor: a muzzle point should be at the weapon barrel, otherwise the firing flash/projectile will originate from the torso. The current `Muzzle` reference still needs a separate in-game check against the custom model's skeleton.

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
- Confirm that death blood/explosion effects originate around the upper torso with `bip01 spine`.
- Confirm the bolter muzzle effect. If the custom skeleton has no bone named `Muzzle`, identify the actual barrel/helper bone in Blender and change only `muzzleBone` to that exact name.
- Do not rename or rebuild the Dawn of War skeleton merely to match the vanilla Sisters names; keep animation bone names consistent across mesh and all animation exports.
