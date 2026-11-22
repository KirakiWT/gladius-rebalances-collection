# Factions Rework All-In-One Suppressive Neutrals Addon

Optional XML-only companion for **Faction Reworks All-In-One Fixed + Eradication Integrated**.

This folder is intended to be used together with the main mod. It contains XML definitions and spawn configuration only. Models, meshes, materials, textures, animations, audio, and other non-XML resources are deliberately not duplicated; the XML continues to reference the assets supplied by the base game and the main mod.

## Contents

- `Data/World/Units/Neutral/`: 36 neutral-catalog unit definitions, including the Wildlife entries, companion/summoned definitions, special encounters, and the Artefacts subfolder.
- `Data/World/Weapons/`: the six separate weapon XML definitions referenced by the included unit XML.
- `Data/World/Blueprints/WorldGenerator/Wildlife.xml.ext`: the neutral wildlife spawn-group configuration.

Most unit and weapon XML files are copied from the main mod. `GiantAudrey.xml` is intentionally customised in this addon: its melee damage is set to 2, and it gains the `Root Snare` active ability, which immobilises a selected adjacent enemy unit for 1 turn (3-turn cooldown). English and Russian action text for this ability is included under `Data/Core/Languages/`. The neutral unit files `KastelanRobot.xml` and `VespidStingwing.xml` are intentionally not included because their definitions explicitly assign them to Adeptus Mechanicus and Tau, respectively. `KrootHound.xml` is included because the Wildlife configuration explicitly spawns it, despite its Tau faction attribute; treat that record as a known exception when editing.

All 22 neutral unit XML files present in `ORIGINAL VANILLA FILES` were also found in the main mod, so no fallback vanilla copies were needed for this set.
