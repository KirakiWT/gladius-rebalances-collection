# Faction Reworks - Suppressive Neutrals Addon

An optional companion for [Faction Reworks All-In-One Fixed + Eradication Integrated](../Faction%20Reworks%20All-In-One%20Fixed%20%2B%20Eradication%20Integrated). Enable both mods and give this addon override priority so its XML definitions take precedence. The addon uses game and main-mod assets and includes a Workshop preview.

## Changes compared with All-In-One

Values below are the raw XML values, shown as All-In-One → addon. HP values are per model.

| Unit | Changes |
| --- | --- |
| Giant Audrey | Group size 1 → 3, model scale 4 → 3, armour 6 → 0, HP 15 → 8, movement 4 → 2, melee attacks 2 → 1, melee damage 3 → 2, melee armour penetration 6 → 10. Replaces Monstrous Creature with Chameleonic Skin and gains Root Snare. |
| Promethean | HP 12 → 18, melee damage 3 → 2. Living Promethean Incubator cooldown 35 → 15 turns, maximum spawn level 6 → 4. |
| Promethean Young | Group size 6 → 8, armour 2 → 7, HP 3 → 1, melee attacks 3 → 2. |
| Pariah | Group size 1 → 4, armour 6 → 1, HP 6 → 2. |
| Umbra | Armour 6 → 7, HP 16 → 25, strength damage 3 → 3.5. |
| Catachan Devil | Armour 8 → 9. |
| Enslaver | HP 12 → 14. |
| Horror | HP 3 → 5, morale 6 → 8, melee armour penetration 4 → 3. |
| Magna Deamonus Pyros | Morale 6 → 10. |
| Neophyte Hybrid | Armour 4 → 5, melee accuracy 6 → 3, strength damage 1 → 2, movement 3 → 4, ranged accuracy 6 → 8. |
| Vespid Stingwing | Armour 3 → 1, HP 2.5 → 3. |

**Root Snare** immobilises one adjacent enemy unit for 1 turn. It has a 1-turn cooldown and consumes neither action points nor movement. Its action text is available in English and Russian.

**Weapons.** The addon supplies shared `Autogun.xml` and `NeutronBlaster.xml` definitions used by Neophyte Hybrid and Vespid Stingwing, respectively. Both weapons have Assault and Rapid Fire, two base attacks and range 2. The Autogun has 1 ranged damage and 0 armour penetration. The Neutron Blaster has 0.6 ranged damage and 4 armour penetration, and retains the conditional Tau Las Damage trait. These are shared weapon IDs, so their overrides can also affect other units using the same weapons.

## Included files

- `Data/World/Units/Neutral/` contains 37 unit definitions, including nine artefact definitions. Vespid Stingwing and Kroot Hound retain their Tau faction attribute. The wildlife configuration includes Kroot Hound in a pack with Domina Kroot Hound.
- `Data/World/Weapons/` contains eight weapon definitions.
- `Data/World/Blueprints/WorldGenerator/Wildlife.xml.ext` carries over the wildlife spawn groups from All-In-One.
- `Data/Core/Languages/` contains the English and Russian Root Snare text.

See [STEAM_WORKSHOP.txt](STEAM_WORKSHOP.txt) for the Workshop description in Steam BBCode.
