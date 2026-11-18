# Warhammer 40,000: Gladius — Faction Rebalances Collection

A collection of large-scale faction reworks and balance changes for **Warhammer 40,000: Gladius – Relics of War**.

The project aims to revisit the game's factions as a whole: their rosters, unit roles, faction mechanics, progression, and balance. The goal is to make the factions feel more deliberately designed while preserving what makes each of them distinct.

> **Note:** This repository is a collection of mod data and reference files. It is not a single standalone mod package. The exact scope and implementation status of individual faction changes may vary; consult the files and design notes before assuming that every planned change is complete.

## Repository contents

### 1. Faction Reworks All-In-One — Eradication Integrated

Directory: `Faction Reworks All-In-One Eradication Integrated/`

The main integrated package. Its game-data structure includes faction-specific content for all 11 standard playable factions represented in the project:

- Adeptus Mechanicus
- Astra Militarum
- Chaos Space Marines
- Drukhari
- Eldar
- Necrons
- Orks
- Sisters of Battle
- Space Marines
- T'au
- Tyranids

The package contains game data for buildings, units, traits, upgrades, weapons, factions and related systems, alongside supporting audio, textures, meshes and animations. It also includes a preview image and a design document.

**Design notes:** [`design_document.txt`](Faction%20Reworks%20All-In-One%20Eradication%20Integrated/design_document.txt) currently documents a major Necron rework. Among the described changes are a more involved Ore/Energy economy, revised unit production, changes to Rapid Rise and Necrodermis Repair, adjustments to several heroes and units, and a new Small Gauss Pylon fortification.

Steam Workshop ID recorded in `SteamID.txt`: **3841700987**  
[Open the All-In-One Workshop item](https://steamcommunity.com/sharedfiles/filedetails/?id=3841700987)

### 2. Chaos Daemons Faction — FRAIO Integration

Directory: `Chaos Demons Faction [FRAIO Integration]/`

A separate Chaos Daemons faction package marked as an integration with the All-In-One collection. It contains its own game data, including faction, unit, building, trait, upgrade and weapon definitions, as well as supporting scene assets, textures, meshes and animations.

The directory also includes a preview image and its own `SteamID.txt`.

Steam Workshop ID recorded in `SteamID.txt`: **3773456041**  
[Open the Chaos Daemons Workshop item](https://steamcommunity.com/sharedfiles/filedetails/?id=3773456041)

### 3. Original vanilla files

Directory: `ORIGINAL VANILLA FILES/`

Contains the game's original `Core` and `World` data trees. These files are kept as a reference for comparing modded content against the vanilla game.

This folder is reference material, not an additional faction rework. Take care not to overwrite modded files with vanilla copies when installing or updating content.

## Using the mods

For the Steam version, open the corresponding Workshop pages above and subscribe to the items you want to use. Enable the subscribed content in the game's mod manager before starting a match.

The repository also preserves the underlying mod data for inspection, comparison and development. The folder names and internal directory structure are kept intact to make it easier to identify which files belong to each package.

## Project notes

- The All-In-One package and the Chaos Daemons integration are stored as separate directories.
- The vanilla data is provided separately for reference.
- The Necron design document is the currently included faction-specific design document; it should not be treated as a complete changelog for every faction.
- Game version compatibility, a complete per-faction change list and a formal release history are not yet documented here. Check the associated Workshop pages and repository updates for the latest information.

## Feedback and contributions

Suggestions, balance feedback, bug reports and improvement proposals are welcome. When reporting an issue, please include the affected faction, unit or mechanic, the mod package you are using, and any relevant reproduction details.

---

*Warhammer 40,000, Gladius – Relics of War and related faction names and assets belong to their respective rights holders. This is an unofficial community mod project and is not affiliated with or endorsed by Games Workshop or the game's developers.*
