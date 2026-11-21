# Warhammer 40,000: Gladius — Faction Rebalance Collection

This repository contains an integrated faction-rework package, a separate Chaos Daemons faction package, and vanilla game files kept for comparison. The XML in each package is the implementation source of truth; documentation is only a guide to the repository.

## Repository map

| Directory or file | Role |
|---|---|
| [Faction Reworks All-In-One Fixed + Eradication Integrated](./Faction%20Reworks%20All-In-One%20Fixed%20%2B%20Eradication%20Integrated/) | **Main baseline package.** The integrated mod. Its Data tree contains the current game definitions and supporting package data. Use its XML as the baseline when comparing faction mechanics and balance. |
| [Chaos Demons Faction [FRAIO Integration]](./Chaos%20Demons%20Faction%20%5BFRAIO%20Integration%5D/) | **Separate working faction package.** Contains its own Chaos Daemons faction, building, unit, trait, upgrade, weapon, and language definitions. This is distinct from the Chaos Space Marines content in the AIO package. |
| [ORIGINAL VANILLA FILES](./ORIGINAL%20VANILLA%20FILES/) | **Reference only.** Original game Core and World data for comparisons. These files are not a mod package and should not replace modded files. |
| Fallen Battle Sisters for Chaos | Outside the scope of the faction rebalance collection; ignored by this project documentation. |
| Models-to-be-added | Asset holding area; ignored by this project documentation. |
| README.md | Repository entry point and folder guide. |
| PROJECT_CONTEXT.md | Short internal reference in Russian. |

## Chaos Daemons: current XML data

The Chaos Daemons package is no longer just a note or an empty integration folder: it contains its own faction-specific XML data.

A few values visible in the current XML:

- The faction definition marks Chaos Daemons as playable and assigns DLC gate Supplement3.
- The faction definition sets starting resources to 25 Energy, 25 Food, 25 Influence, and 50 Ore.
- Its starting units are one Chaos Cultist, one Chaos Space Marine, and Be'lakor.
- The Chaos Daemons Headquarters building adds 17 Loyalty and 6 each of Energy, Food, Influence, Ore, Research, and Population Limit.

These are current XML values, not a claim that each value differs from AIO. Consult the relevant XML before describing a specific change relative to the baseline.

The folder's SteamID.txt records Workshop item **3773456041**: [Chaos Daemons on Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=3773456041).

## How the packages relate

- The AIO folder is the integrated baseline and main comparison point.
- Chaos Daemons is maintained as a separate faction package with its own XML definitions and current faction-specific balance data.
- ORIGINAL VANILLA FILES is used only to check what the original game files contain.
- Chaos Space Marines in AIO and Chaos Daemons in the separate package are different factions; do not treat their names or XML as interchangeable.

## Documentation and verification

- [PROJECT_CONTEXT.md](./PROJECT_CONTEXT.md) describes repository roles, the documentation-only edit policy, and the current XML facts recorded for Chaos Daemons.
- [Chaos Daemons XML balance audit](./Chaos%20Demons%20Faction%20%5BFRAIO%20Integration%5D/Balance-Audit-2026-11-21.md) records verified faction values and the current building/economy comparison with the AIO Chaos Space Marines baseline.
- [AIO Necron XML reference](./Faction%20Reworks%20All-In-One%20Fixed%20%2B%20Eradication%20Integrated/design_document.txt) records a small selection of Necron implementation details checked against the AIO XML.

When documenting a mechanic, inspect its current XML in the relevant package. XML may be read for verification, but repository maintenance changes are restricted to documentation files (`.md` and `.txt`); game XML and asset files are not edited. Do not use old investigation notes, chat logs, proposed changes, or historical design text as proof of current implementation. XML declarations also do not by themselves confirm engine behaviour; test in-game when the effect depends on undocumented engine semantics.

## Feedback

For a useful issue report, identify the package, faction, affected XML file, and the observed in-game behaviour.

---

*Warhammer 40,000, Gladius – Relics of War, and related names and assets belong to their respective rights holders. This is an unofficial community project and is not affiliated with or endorsed by Games Workshop or the game's developers.*
