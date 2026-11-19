# Warhammer 40,000: Gladius — Global Faction Reworks

A comprehensive faction overhaul and balance collection for **Warhammer 40,000: Gladius – Relics of War**.

This project is **not a Necron-only rebalance**. Its main All-In-One package contains faction-specific gameplay data for all 11 standard playable factions. The repository's current package is based on the [Faction Reworks All-In-One Patched](https://steamcommunity.com/sharedfiles/filedetails/?id=3737847171) Workshop version, rather than the unpatched original upload. The original Niemeria faction write-ups describe the underlying rework; the Patched changelog records later fixes and balance adjustments. The repository currently documents this upstream baseline and does not add a separate balance layer of its own.

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

The upstream All-In-One description carried into the Patched version also documents shared rules affecting multiple factions:

- River tiles provide +20% Energy and +20% Food, but reduce city building slots by 1.
- Healing is increased to 20% per turn on Outpost tiles and 25% per turn on City tiles.
- Pinned no longer increases the target's ranged damage reduction.
- Skyfire applies to Air Units, Skimmers and Jetpack Units, with 33% more damage against those types and 33% less against ground units.
- Soulblaze and other damage-over-time effects last 2 turns instead of 1.
- Grenades for almost all factions ignore cover by default, have fixed 50% accuracy and cannot benefit from accuracy modifiers.

The Patched package description retains two neutral-enemy reworks. More detail, source links and interpretation notes are kept in [PROJECT_CONTEXT.md](PROJECT_CONTEXT.md).

### Notable follow-up changes in the Patched version

The Patched changelog contains several substantive follow-ups beyond the inherited faction overview:

- **Tyranids (June 12, 2026):** city founding cost is reduced from 60/60 to 30/30 Biomass/Influence; Metamorphic Malanthropes becomes a baseline effect; Grey Matter Dispersion is folded into the T3 Accelerated Brood Cycle; a new T5 **Corrosive Strikes** adaptation applies stacking armour-reduction debuffs; and T8 **Hypermetamorphic Plasticity** grants every unit one additional Bio-Adaptation slot. The changelog explicitly says these changes had not yet been tested in-game at the time and that the new adaptations were using placeholder icons.
- **Necrons (June 7, 2026):** Extraction Matrix yield is increased from 6 to 7 and gains +1 Influence. Its base cost is reduced from 12× to 5× production cost (the note compares this with 4× in vanilla), upgrades now affect all buildings, and Rapid Rise technologies are retuned: Early is moved/used at T2 for 4.25× cost, while Warmachine moves from T7 to T5 and reduces the cost to 3.5×.
- **Space Marines (June 7, 2026):** the Chaplain's Fortress of Will armour buff can no longer target Heroes, Vehicles or Fortifications, and the Chaplain's listed HP is reduced from 26 to 22.

The same changelog also records smaller maintenance fixes: a Drukhari quest is redirected to Painbringer (June 14), and an Adeptus Mechanicus building-description typo is corrected. These notes describe the Patched upstream version; they should not be presented as new changes authored in this repository.

## Repository contents

### 1. Faction Reworks All-In-One — Eradication Integrated

Directory: Faction Reworks All-In-One Eradication Integrated/

The main integrated package. Its Data tree contains faction-specific Buildings, Traits, Units and Upgrades, plus shared weapons, language files, audio, textures, meshes, animations and other game data.

The repository includes a detailed [Necron design document](Faction%20Reworks%20All-In-One%20Eradication%20Integrated/design_document.txt). This is the most extensive faction-specific design document currently stored inside the All-In-One folder, **not the complete specification of the project**. The other factions also have major reworks documented in their original Workshop descriptions; see [PROJECT_CONTEXT.md](PROJECT_CONTEXT.md).

The package is based on the [Patched All-In-One Workshop item](https://steamcommunity.com/sharedfiles/filedetails/?id=3737847171). The original standalone faction pages are retained as design-history references.

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

- **[PROJECT_CONTEXT.md](PROJECT_CONTEXT.md)** — project-wide design philosophy, all 11 faction summaries, global mechanics, notable Patched follow-ups, neutral packs, Workshop sources, data layout and a dated vanilla comparison snapshot.
- **[Patched All-In-One Workshop item](https://steamcommunity.com/sharedfiles/filedetails/?id=3737847171)** — the upstream version this repository is based on.
- **[Necron design document](Faction%20Reworks%20All-In-One%20Eradication%20Integrated/design_document.txt)** — detailed Necron-specific design notes.
- **[Original vanilla files](ORIGINAL%20VANILLA%20FILES/)** — reference data for comparison.

When documenting or changing a faction, use the original Workshop notes for design intent and inspect the current integrated XML/assets to verify implementation details. The Necron document must not be treated as evidence that other factions are unchanged.

## Feedback and contributions

Suggestions, balance feedback, bug reports and improvement proposals are welcome. When reporting an issue, include the affected faction, unit or mechanic, the mod package you are using, and any reproduction details.

---

*Warhammer 40,000, Gladius – Relics of War and related faction names and assets belong to their respective rights holders. This is an unofficial community mod project and is not affiliated with or endorsed by Games Workshop or the game's developers.*
