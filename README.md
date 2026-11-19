# Warhammer 40,000: Gladius — Global Faction Reworks

A comprehensive faction overhaul and balance collection for **Warhammer 40,000: Gladius – Relics of War**.

This project is **not a Necron-only rebalance**. Its main All-In-One package contains faction-specific gameplay data for all 11 standard playable factions in the original rework collection. The goal is to make unit roles clearer, improve roster and technology progression, revisit faction economies and buildings, and strengthen each faction's defining mechanics without erasing its identity.

For a detailed, AI-oriented record of the design intent, faction-by-faction changes, global rules and repository structure, see **[PROJECT_CONTEXT.md](PROJECT_CONTEXT.md)**.

## Scope of the rework

All 11 core factions receive substantial changes to rosters, Heroes, buildings, technologies, economy or faction mechanics. The highlights below are an overview; consult [PROJECT_CONTEXT.md](PROJECT_CONTEXT.md) and the linked original Workshop notes for the fuller summaries.

| Faction | Main rework themes |
|---|---|
| Space Marines | Reworked roster and Heroes, expanded doctrine system, Fortress of Redemption economy, buildings and early Drop Pod access |
| Adeptus Mechanicus | Reworked Litanies and Imperatives, city economy, roster and tech tree; Cinderfang and Voidshield Bastion |
| Astra Militarum | Reworked production paths, tech tree, squad progression and Heroes; grenade launchers, medikits and anti-tank options |
| T'au | Reworked drones and their cooldowns, expanded Battlesuit support systems to vehicles and aircraft, stronger early game |
| Adepta Sororitas | Reworked infantry, Heroes, Sacred Rites and Acts of Faith; Tech-Priest and Strongpoint of Faith |
| Chaos Space Marines | Reworked Chaos Marks with trade-offs, faction powers, city buffs, tech path and Hero/building distribution; Exalted Poxwalkers |
| Craftworld Aeldari | Influence-driven Asuryani Paths, city specialization, Webway infrastructure, Wraith production and the Avatar as a Hero |
| Drukhari | Influence-based instant recruitment/construction, three Combat Drugs, revised outpost economy and reduced snowball mechanics |
| Necrons | Reworked Ore/Energy economy, production routes, Rapid Rise, Necrodermis Repair, Heroes, Canoptek units and fortifications |
| Orks | More distinct unit roles, streamlined production buildings, revised resource paths, Heroes and stronger late-game options |
| Tyranids | Bio-Adaptations for unit customization, early tunnelling, specialized production buildings, roster and Hero changes |

### Global gameplay changes

The original All-In-One description also documents shared rules affecting multiple factions:

- River tiles provide +20% Energy and +20% Food, but reduce city building slots by 1.
- Healing is increased to 20% per turn on Outpost tiles and 25% per turn on City tiles.
- Pinned no longer increases the target's ranged damage reduction.
- Skyfire applies to Air Units, Skimmers and Jetpack Units, with 33% more damage against those types and 33% less against ground units.
- Soulblaze and other damage-over-time effects last 2 turns instead of 1.
- Grenades for almost all factions ignore cover by default, have fixed 50% accuracy and cannot benefit from accuracy modifiers.

The original package description also includes two neutral-enemy reworks. More detail, source links and interpretation notes are kept in [PROJECT_CONTEXT.md](PROJECT_CONTEXT.md).

## Repository contents

### 1. Faction Reworks All-In-One — Eradication Integrated

Directory: Faction Reworks All-In-One Eradication Integrated/

The main integrated package. Its Data tree contains faction-specific Buildings, Traits, Units and Upgrades, plus shared weapons, language files, audio, textures, meshes, animations and other game data.

The repository includes a detailed [Necron design document](Faction%20Reworks%20All-In-One%20Eradication%20Integrated/design_document.txt). This is the most extensive faction-specific design document currently stored inside the All-In-One folder, **not the complete specification of the project**. The other factions also have major reworks documented in their original Workshop descriptions; see [PROJECT_CONTEXT.md](PROJECT_CONTEXT.md).

Steam Workshop ID recorded in SteamID.txt: **3841700987**  
[Open the All-In-One Workshop item](https://steamcommunity.com/sharedfiles/filedetails/?id=3841700987)

### 2. Chaos Daemons Faction — FRAIO Integration

Directory: Chaos Demons Faction [FRAIO Integration]/

A separate Chaos Daemons faction package marked as an integration with the All-In-One collection. It contains its own faction, unit, building, trait, upgrade and weapon data, along with supporting scene assets, textures, meshes and animations.

**Important distinction:** Chaos Space Marines are one of the 11 factions in the core rework. Chaos Daemons are maintained separately in this FRAIO integration package.

Steam Workshop ID recorded in SteamID.txt: **3773456041**  
[Open the Chaos Daemons Workshop item](https://steamcommunity.com/sharedfiles/filedetails/?id=3773456041)

### 3. Original vanilla files

Directory: ORIGINAL VANILLA FILES/

Contains the original Core and World data trees. These files are reference material for comparing modded content against the vanilla game; they are not another mod package.

Do not overwrite the integrated mod files with vanilla copies when installing or updating content.

## Using the mods

For the Steam version, open the corresponding Workshop pages and subscribe to the items you want to use. Enable the subscribed content in the game's mod manager before starting a match.

The repository also preserves the underlying mod data for inspection, comparison and development. The folder hierarchy is kept intact so that faction-specific and shared game data can be traced.

## Project documentation

- **[PROJECT_CONTEXT.md](PROJECT_CONTEXT.md)** — project-wide design philosophy, all 11 faction summaries, global mechanics, neutral packs, original Workshop sources, data layout and a vanilla comparison snapshot.
- **[Necron design document](Faction%20Reworks%20All-In-One%20Eradication%20Integrated/design_document.txt)** — detailed Necron-specific design notes.
- **[Original vanilla files](ORIGINAL%20VANILLA%20FILES/)** — reference data for comparison.

When documenting or changing a faction, use the original Workshop notes for design intent and inspect the current integrated XML/assets to verify implementation details. The Necron document must not be treated as evidence that other factions are unchanged.

## Feedback and contributions

Suggestions, balance feedback, bug reports and improvement proposals are welcome. When reporting an issue, include the affected faction, unit or mechanic, the mod package you are using, and any reproduction details.

---

*Warhammer 40,000, Gladius – Relics of War and related faction names and assets belong to their respective rights holders. This is an unofficial community mod project and is not affiliated with or endorsed by Games Workshop or the game's developers.*
