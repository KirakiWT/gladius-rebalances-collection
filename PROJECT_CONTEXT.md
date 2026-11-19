# Project Context: Gladius Faction Reworks

> This file is an AI-oriented reference for understanding the scope, design intent and source layout of this repository. It is deliberately broader than the Necron design document in the All-In-One folder.

## Project identity

This repository contains an integrated, global faction overhaul for Warhammer 40,000: Gladius – Relics of War. The central All-In-One package is not a Necron-only rebalance: it includes substantial faction-specific data for all 11 standard playable factions represented in the original rework collection.

The original standalone faction reworks were published by Niemeria and later brought together in an All-In-One package. This repository stores an Eradication-integrated version and the associated source/reference data. The separate Chaos Daemons FRAIO Integration is an additional faction package; it should not be confused with the Chaos Space Marines rework included among the 11 core factions.

## Core design philosophy

The original rework descriptions state these broad goals:

- Give every unit a useful battlefield niche or a distinct role.
- Make heroes more attractive by reducing their opportunity cost and revising their roles.
- Rebalance faction rosters, units, buildings, technologies and economies where needed.
- Preserve the central identity and gameplay loop of each faction.
- Remove, consolidate or replace awkward, redundant or low-value technologies.
- Replace economic abilities on heroes with more faction-appropriate abilities.
- Consider the game's unit DLC content during balancing.

The approach is faction-specific rather than a single universal balance formula. Several factions receive new or expanded mechanics that steer their economy, recruitment or unit customization.

## Faction-by-faction design overview

The summaries below paraphrase the original standalone Workshop descriptions and patch notes. They describe the documented design intent; they are not a substitute for checking the current integrated XML data when verifying exact implementation.

### Space Marines

**Main focus:** A large roster, doctrine system, heroes, buildings and economy.

The rework attempts to give the very large Space Marine roster clearer roles and address power creep from later Primaris content. The three basic doctrines become faction-wide tactical choices rather than effects that only matter to a narrow set of units. Advanced doctrines unlock later and add further army-wide specializations: reactions to casualties, mobility, regeneration and durability. The Fortress of Redemption contributes resources to the faction economy, and city tile upgrades reduce its cooldown. The original overview also highlights earlier Drop Pod access. Frag and krak grenades are retuned, with cover interaction changed.

Original source: [Space Marine Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980216)

### Adeptus Mechanicus

**Main focus:** Litanies and Doctrina Imperatives, city economy, roster, technology and new fortifications.

Litanies and Imperatives are rebuilt into sets of four, with effects lasting two turns and separate shared cooldowns for each system. City planning is simplified: bonuses and penalties for repeating a building on a tile remain, while adjacency bonuses are removed. Powersurge becomes stronger but shorter. The roster and technology tree are reworked, including the Cinderfang (a special Devil Dog variant), the T6 Voidshield Bastion and the Orb of Omnissiah anti-armour grenade. The detailed notes also move or change unit production roles, including Kastelan Robots and Electro-Priests.

Original source: [Adeptus Mechanicus Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980295)

### Astra Militarum

**Main focus:** More diverse army tools, building paths, squad progression, heroes and anti-armour options.

The Cult Mechanicus and Psyker Coven building paths are consolidated into the Hero building; Tech-Priests can also be produced from the Headquarters, and Guardsmen gain another production route. The technology tree and city Edicts are reorganized, while Bulwark of the Emperor becomes a baseline defensive bonus for city tiles. New technologies expand squad sizes and give Guardsmen, Ratlings and Tempestus Scions grenade launchers. The Lord Commissar and Primaris Psyker-Biomancer receive more defined battlefield-support roles. The original faction overview additionally calls out medikits for the army and new anti-tank guns.

Original source: [Astra Militarum Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980620)

### T'au

**Main focus:** Drones, battlesuit support systems, early-game resilience and city loyalty.

The drone research system is reorganized into class bundles for infantry, vehicles and battlesuits/mechs. The drone types still interact through cooldowns, but different classes receive different cooldown timing to encourage a wider selection than the dominant Gun Drone. Support systems are extended beyond battlesuits to vehicles and aircraft. The T'au Utopia passive is changed so that different buildings in a city generate loyalty, with later technologies improving the value. The Subvert City loyalty-reduction ability is removed. The stated intent is to make the early game less fragile while retaining the faction's strengths.

Original source: [T'au Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554979595)

### Adepta Sororitas

**Main focus:** Infantry roles, Sacred Rites, Acts of Faith, heroes and support structures.

The rework addresses the faction's narrow one-range infantry profile, its mid-game power spike and the repetitive need to activate a Sacred Rite every turn. Infantry and the technology tree are substantially reorganized; heroes are strengthened and given more useful roles. Sacred Rites are redesigned to last five turns, with a clearer progression of defensive, infantry-production, bolter and mechanized bonuses. Acts of Faith are reworked or strengthened. The original overview highlights a new Tech-Priest unit and a Strongpoint of Faith fortification.

Original source: [Adepta Sororitas Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554979850)

### Chaos Space Marines

**Main focus:** Chaos Marks, faction powers, economy, buildings and hero distribution.

The original page calls this the Chaos rework; in the integrated data it corresponds to the Chaos Space Marines faction, not the separate Chaos Daemons package. Chaos Marks are expanded from infantry-only effects to all eligible Chaos unit types. Each god's mark provides a stronger benefit with a corresponding drawback: Khorne emphasizes attacks at the cost of armour, Nurgle durability at the cost of movement, Tzeentch damage protection and Warpflame at the cost of melee resistance, and Slaanesh speed and execution effects at the cost of hit points. Icons of Chaos can be combined with any mark. City buffs and the technology path are revised, Exalted Poxwalkers are added, and the standalone Hero building is removed so heroes are distributed across other production buildings. The Cult of Chaos building becomes more important.

Original source: [Chaos Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980459)

### Craftworld Aeldari

**Main focus:** Influence-driven economy, Asuryani Paths, Webway infrastructure and Wraith production.

The flat economic modifiers are replaced with Asuryani Paths that let the player steer city development. Paths emphasize different combinations of growth, infantry and food, vehicles and ore, influence, construction and research, or aircraft/Hero/Wraith production and energy. Some Paths are available from the start and others are researched; they use influence and share a cooldown. A later technology reduces the cooldown, and another unlocks a permanent Webway Gate. Wraith units move to the Hero building, creating a clearer infantry/vehicle/Hero-Wraith production split. The original overview also highlights the Avatar becoming a Hero.

Original source: [Craftworld Aeldari Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980402)

### Drukhari

**Main focus:** Influence as a spendable recruitment resource, Combat Drugs and reduced snowball mechanics.

Research unlocks the ability to spend influence to instantly produce units and buildings, themed as hiring mercenaries from Commorragh. Three Combat Drugs specialize units differently: Hypex improves ranged firepower, Painbringer improves melee performance, and Gravelotus improves durability. Neutral outposts are shifted from city-growth sources toward influence generation. The old loyalty reward for hoarding 400 influence is removed, as is the level-based passive that amplified snowballing. Many faction-wide abilities are folded into technologies or poison effects to reduce repetitive actions. Webway Gates receive durability improvements, with a stronger late-game gate option.

Original source: [Drukhari Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980360)

### Necrons

**Main focus:** Ore/Energy economy, production routes, Rapid Rise, Necrodermis Repair, heroes and Canoptek roles.

The local design_document.txt gives the most detailed faction-specific description currently stored in the repository. It aims to preserve Necron strength while reducing the Summoning Core's dominance and encouraging a wider building strategy. Ore and Energy gain distinct uses across buildings, infantry, vehicles, flyers, heroes and monsters. Monster production shifts to the Royal Pyramid; Canoptek Spyders and Reanimators receive revised production/support roles, and Reanimators can found cities. Rapid Rise is made more expensive before its related technology. Necrodermis Repair costs are differentiated by unit class. A Small Gauss Pylon is added, and several heroes, infantry units, monsters and vehicles are adjusted.

Source in this repository: [All-In-One design_document.txt](Faction%20Reworks%20All-In-One%20Eradication%20Integrated/design_document.txt)  
Original source: [Necron Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3554979921)

### Orks

**Main focus:** Remove roster redundancy, redistribute production, improve late-game choices and strengthen heroes.

The large Ork roster is reorganized so units have more distinct purposes and late-game units no longer compete at the same tier and price point. Production is split into three clearer paths: infantry and heroes from the Pile O'Dakka (Food and Ore), Meks and Walkers from the Mek Bitz Yard (Energy plus Food/Ore), and vehicles and flyers from the Kult ov Speed (Ore). Redundant or underused buildings are reduced, and the Gargantuan Squiggoth is moved into the Pile O'Dakka instead of requiring its own dedicated building. The Painboy and Weirdboy receive role adjustments. The original overview also calls out more dakka, grenades, Tankbustas and stronger tanks.

Original source: [Orks Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3564632936)

### Tyranids

**Main focus:** Bio-Adaptations, early tunnelling, specialist production buildings and faction mechanics.

The defining new mechanic is Bio-Adaptation. Units receive one to three slots based on size and can spend influence to equip adaptations from a pool of up to twelve. The options cover melee and ranged offense, sight and accuracy, damage-over-time and pinning, regeneration, defensive carapaces, movement, extra range and lifesteal. A technology path lets Tyranids deploy Brood Hive tunnels earlier and build a network; tunnel use costs influence, with later technologies reducing the cost and improving the network. Unit production is split across four specialized buildings: Brood Nest for ranged/hybrid creatures, Brood Haunt for melee creatures, Capillary Towers for flyers and selected Heroes, and Aedanthropum for the Thrope units and Maleceptor. The roster and Heroes are also reworked.

Original source: [Tyranids Rework Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3577779257)

## Global gameplay changes

The original All-In-One description also lists changes that affect multiple factions or the shared game rules:

- **River terrain:** River tiles provide +20% Energy and +20% Food, but reduce a city's available building slots by 1.
- **Healing:** Healing on Outpost tiles is raised to 20% per turn and on City tiles to 25% per turn.
- **Pinned:** The Pinned debuff no longer increases a unit's ranged damage reduction.
- **Skyfire:** The trait applies to Air Units, Skimmers and Jetpack Units. It gives 33% more damage against those target types and 33% less damage against ground units.
- **Damage over time:** Soulblaze and other DoT effects last 2 turns instead of 1.
- **Grenades:** For almost all factions, grenades ignore cover by default, have a fixed 50% accuracy and cannot benefit from accuracy modifiers.

These are global/package-level rules, not faction-specific abilities. Some faction pages also contain their own grenade changes; when documenting an exact rule, distinguish the global baseline from a faction-specific exception or override.

## Neutral enemy content

The original All-In-One description says that two neutral enemy packs are included:

1. **Basegame Neutral Enemies Rework:** neutral flyer units become Skimmers so melee units can attack them; the notes describe this as a way to tone down especially frustrating flying enemies.
2. **Kabookie's Neutral Enemies Rework:** uses Kabookie's neutral enemy pack with balance adjustments to units considered too strong.

The repository's integrated data includes neutral-unit assets and definitions. Treat the two packs as separate supporting content, not as additional playable factions.

## Repository layout and implementation evidence

The main package is stored under:

- Faction Reworks All-In-One Eradication Integrated/Data/Core
- Faction Reworks All-In-One Eradication Integrated/Data/World
- Faction Reworks All-In-One Eradication Integrated/Data/Video
- Faction Reworks All-In-One Eradication Integrated/Data/Audio

The faction-specific XML is organized by shared game-data category, rather than by 11 separate top-level mod folders. For example:

- World/Buildings/<Faction>/
- World/Traits/<Faction>/
- World/Units/<Faction>/
- World/Upgrades/<Faction>/
- World/Factions/<Faction>.xml
- World/Cities/<Faction>.xml (where applicable)

This shared World tree is a key reason a shallow root-level scan can miss the distribution of faction changes. The separate ORIGINAL VANILLA FILES folder provides Core and World reference data for comparisons.

### Snapshot comparison against vanilla World data

A tree comparison of the current All-In-One Data/World files against ORIGINAL VANILLA FILES/World found substantial faction-specific data for every one of the 11 factions. The table counts faction-specific files in Buildings, Traits, Units, Upgrades and the faction/city definition files. “New” means the path was not present in the vanilla reference; “Modified” means the path existed but its file content hash differs. “Same” means the path and content hash match the vanilla reference.

| Faction | Faction-specific files | New | Modified | Same |
|---|---:|---:|---:|---:|
| Adeptus Mechanicus | 152 | 52 | 94 | 6 |
| Astra Militarum | 165 | 71 | 91 | 3 |
| Chaos Space Marines | 156 | 36 | 106 | 14 |
| Drukhari | 147 | 51 | 85 | 11 |
| Craftworld Aeldari | 153 | 49 | 94 | 10 |
| Necrons | 160 | 53 | 98 | 9 |
| Orks | 169 | 42 | 87 | 40 |
| Adepta Sororitas | 161 | 56 | 96 | 9 |
| Space Marines | 158 | 47 | 104 | 7 |
| T'au | 160 | 49 | 103 | 8 |
| Tyranids | 224 | 61 | 107 | 56 |

These counts are a repository snapshot, not a balance score or a measure of how much gameplay changed. Shared weapons, language files, textures, audio, animations and other global data are not included in the per-faction totals. File counts should not be used to rank the depth or quality of a faction rework.

## Important interpretation rules for future project work

1. **Do not treat the Necron design_document.txt as a complete project specification.** It is the only detailed faction design document currently present in the All-In-One folder, but the original Workshop descriptions document extensive redesigns for the other ten factions as well.
2. **Use the integrated game data as the implementation source of truth.** The original Workshop descriptions explain design intent and high-level changes; inspect the current XML and assets before asserting an exact value or claiming a feature is currently implemented.
3. **Keep faction identities separate.** “Chaos” in the original faction rework pages means Chaos Space Marines in the core 11-faction set. Chaos Daemons is a separate FRAIO integration directory in this repository.
4. **Use ORIGINAL VANILLA FILES for baseline comparisons.** It is the repository's reference copy, not a mod component to overwrite the integrated package with.
5. **Keep global and faction-specific rules distinct.** A shared rule such as the grenade accuracy change can interact with faction-specific grenade definitions or overrides.

## Sources

### Original All-In-One and consolidated description
- [Original All-In-One Workshop item by Niemeria](https://steamcommunity.com/sharedfiles/filedetails/?id=3555293815)
- [Workshop discussion linked by the repository owner](https://steamcommunity.com/workshop/filedetails/discussion/3841700987/570429280068051957/)
- [Archived description of Faction Reworks All-In-One Patched](https://catalogue.smods.ru/archives/455030)

### Original standalone faction reworks
- [Space Marines](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980216)
- [Adeptus Mechanicus](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980295)
- [Astra Militarum](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980620)
- [T'au](https://steamcommunity.com/sharedfiles/filedetails/?id=3554979595)
- [Adepta Sororitas](https://steamcommunity.com/sharedfiles/filedetails/?id=3554979850)
- [Chaos / Chaos Space Marines](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980459)
- [Craftworld Aeldari](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980402)
- [Drukhari](https://steamcommunity.com/sharedfiles/filedetails/?id=3554980360)
- [Necrons](https://steamcommunity.com/sharedfiles/filedetails/?id=3554979921)
- [Orks](https://steamcommunity.com/sharedfiles/filedetails/?id=3564632936)
- [Tyranids](https://steamcommunity.com/sharedfiles/filedetails/?id=3577779257)

### Repository packages
- [All-In-One — Eradication Integrated](https://github.com/KirakiWT/gladius-rebalances-collection/tree/main/Faction%20Reworks%20All-In-One%20Eradication%20Integrated)
- [Chaos Daemons — FRAIO Integration](https://github.com/KirakiWT/gladius-rebalances-collection/tree/main/Chaos%20Demons%20Faction%20%5BFRAIO%20Integration%5D)
- [Original vanilla files](https://github.com/KirakiWT/gladius-rebalances-collection/tree/main/ORIGINAL%20VANILLA%20FILES)

---

*This is an unofficial community project. Warhammer 40,000, Gladius – Relics of War and related names and assets belong to their respective rights holders.*
