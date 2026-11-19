# Asset status

The earlier note about a separate ZIP is superseded by the files now committed in this repository.

## Included in the mod's runtime data tree

- Mesh source XML: `Data/Video/Meshes/Units/ChaosSpaceMarines/FallenBattleSister.xml`
- Animation source XMLs: `Data/Video/Animations/Units/ChaosSpaceMarines/FallenBattleSister{Idle,Move,Attack,Melee,Die}.xml`

These paths mirror the Gladius mesh/animation data hierarchy. The XML asset contents were copied without static inspection, as requested; runtime compilation and playback remain to be tested in the game.

## Preserved source textures

The four supplied PNG files are copied to `Assets/SourceTextures/`:

- `FallenBattleSister_Diffuse.png`
- `FallenBattleSister_Normal.png`
- `FallenBattleSister_Metallic.png`
- `FallenBattleSister_Roughness.png`

They are source inputs only. Gladius uses DDS texture assets, so the following runtime files are still outstanding:

- `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterDiffuse.dds`
- `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterNormal.dds`
- `Data/Video/Textures/Units/ChaosSpaceMarines/FallenBattleSisterSIC.dds`

The material definition already references those logical texture slots. Convert the source maps to DDS (Diffuse from base, Normal from normal, SIC using the planned metallic/roughness packing) before treating the texture setup as complete.

Do not substitute the obsolete `fallsister2.xml`; only `fallsister3.xml` is used.
