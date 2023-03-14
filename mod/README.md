# Overview

Have you ever noticed that the ringworld from Origin: Shattered Ring is always the same colors (black with green) regardless of your ship appearance?  This mod changes that - now your starting ringworld will be the same as your empire's ship appearance (graphical culture).  However, ringworlds will always have a specific color based on the shipset rather than your empire's flag colors.

Have you also noticed that repaired or constructed habitable ringworld sections don't have cloud cover?  It turns out that PDX made changes to how the cloud animation mesh is attached to habitable ringworld sections between version 1.6.3 "Adams" and version 1.9 "Boulle" and only updated the default habitable ringworld section.  This mod fixes the entity definitions for every built-in shipset so that all habitable ringworld sections can enjoy cloud cover, regardless of which empire builds or restores them.

Or maybe you noticed that the planetview for ringworlds displays a Gaia climate, but that the texture in the systemview uses continental terrain.  Or that sometimes the terrain for habitable ringworld sections appears to be greyed-out and only show water sections?  This mod now also addresses this inconsistency by applying the Gaia planet textures to habitable ringworld sections and adjusting the specular map to avoid they transparency/grayness issue.

# Changes

This mod adds one extra event which is triggered for each empire with Origin: Shattered Ring at game start. The event switches the appearance of the starting ringworld to match the shipset selected by the empire, but has no gameplay impact. When shattered ring sections are fully repaired (as of 3.1) the repaired section resets its graphical entity upon completion which results in the ringworld returning to the default graphics. To avoid this, the decision to restore a shattered ring section now keeps its graphics entity when changing its planet class to a real ringworld section.

Also altered are the built-in graphic entity definitions for habitable ringworld sections.  Every shipset (graphical culture) has its habitable ringworld section definition updated to attach the cloud cover animation using a separate entity.  Thus all habitable ringworld sections properly display the cloud cover that was previously missing.  And finally, the terrain textures for all habitable sections have been switched to use Gaia planet textures instead of Continental.

## Compatibility

Built for Stellaris version 3.7 "Canis Minor."  Not compatible with achievements (because of the necessary event and the planetary decision override).

Should be compatible with almost anything else.  If other mods add new origins which also start on a ringworld, this mod will **not** affect them.  Mods that add new graphics entity definitions for ringworlds will **not** be affected by this mod - they may or may not have cloud cover based on how the author created their graphics entity definitions.

### When to Install

This mod can be safely added or removed from your save game after the game has started.  The Origin: Shattered Ring code in this mod executes entirely during game setup - if the game was started with the mod, its effects have already been applied otherwise nothing happens.

The fix applied to the shattered ring restoration decision only fires once the decision completes - if you remove this mod, any existing restored sections will retain their existing appearance, but newly repaired sections will be set to the default appearance.  The other graphical fixes only apply while the mod is enabled, otherwise the game will use its built-in definitions (which lack clouds and display continental terrain).

### Recommended Companion Mods

* [Aesthetic Terraform Stations](https://steamcommunity.com/sharedfiles/filedetails/?id=2622411084) will give you back the very old-school terraform stations as visual markers for terraforming planets
* [Machine Shipset](https://steamcommunity.com/sharedfiles/filedetails/?id=2077186491) is a phenomenal, fully-sectioned shipset and includes megastructures - ombined with this mod you can have Origin: Shattered Ring with the Machine Shipset ringworld appearance
* [Machine Shipset Add-on: Shattered Ring and Habitat Appearance](https://steamcommunity.com/sharedfiles/filedetails/?id=2628980994) ensures that the permanently-destroyed sections for Origin: Shattered Ring using the Machine Shipset properly display as that shipset (adds missing graphical definitions to the Machine Shipset)
* [Machine Shipset Add-on: Aesthetic Terraform Station Compatibility](https://steamcommunity.com/sharedfiles/filedetails/?id=2628972292) and this compatibility patch ensures the correct Machine Shipset graphics are used for the above terraform stations (adds missing graphical definitions to the Machine Shipset)

## Known Issues

### Stellaris Bugs

After reloading a saved game, habitable ringworld sections that have a graphical culture no longer display the "planetary" texture - instead, only the bodies of water show and the ringworld's base texture is visible through the "holes."  Ringworld sections are set to match your empire's graphical culture either with this mod, or by the game itself when you restore or build a ringworld.  I have reported this bug on the official [forums](https://forum.paradoxplaza.com/forum/threads/1494567/).  Since reporting the bug, I have been able to address it in this mod!

Ringworld sections with a graphical culture do not have cloud cover in the base game.  This mod fixes that issue, but I still reported it as a bug on the official [forums](https://forum.paradoxplaza.com/forum/threads/1494566/).

### Error Logs

Overriding planetary decisions and graphical entity definitions produces entries in the error.log file, so expect to see fourteen lines similar to these:

```
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of arthropoid_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of avian_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of fungoid_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of mammalian_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of molluscoid_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of plantoid_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of reptilian_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of lithoid_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of necroid_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of nemesis_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of aquatic_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:31][graphics/pdx_entity.cpp:2546]: Duplicate of toxoid_01_ringworld_habitable_entity_01_entity added to entity system
[03:22:33][game_singleobjectdatabase.h:165]: Object with key: spawn_shattered_ring_guaranteed_1_effect already exists, using the one at  file: common/scripted_effects/zz_ringworld_graphical_enhancements_federations_event_effect_overrides.txt line: 4
[03:22:33][game_singleobjectdatabase.h:165]: Object with key: spawn_shattered_ring_guaranteed_2_effect already exists, using the one at  file: common/scripted_effects/zz_ringworld_graphical_enhancements_federations_event_effect_overrides.txt line: 39
[03:22:36][game_singleobjectdatabase.h:165]: Object with key: decision_shattered_ring_project already exists, using the one at  file: common/decisions/ringworld_graphical_enhancements_decision_overrides.txt line: 2
[03:22:37][prescripted_systems.cpp:847]: An initializer called "shattered_ring_start" already exists.  file: common/solar_system_initializers/federations_initializers.txt line: 1797
```

## Changelog

* 1.0.0 Initial version
* 1.1.0 Move visual enhancements
    * Habitable ringworld sections now display Gaia planet textures (matches their use of the Gaia textures in the planetview; Gaia planets use `tropical_03` for their normals and specular)
    * Use a customized specular map for ringworld planetary terrain - masking the red channel prevents the shader from "greying out" the landmasses, so now ringworlds will look nice whether they are new or you loaded up an old save
* 2.0.0 Update for compatibility with Stellaris 3.2 "Herbert" 
    * Merge underlying game changes
    * Support new shipset (Aquatic)
* 2.1.0 Mark as compatible with Stellaris 3.3 "Libra" - no script changes
* 2.2.0 Mark as compatible with Stellaris 3.4 "Cepheus" - no script changes
* 3.0.0 Update for compatibility with Stellaris version 3.6 "Orion"
    * Change the Shattered Ring appearance event to fire after `game_start.1` which is what sets up the colonizable ringworld segments
    * Update the "Repair the Shattered Ring" decision with underlying changes (it's still not perfect, so this mod's override persists)
    * Support new shipset (Toxoid)
* 3.1.0 Add a compatibility trigger for other mods to check whether this one is active
* 3.2.0 Ensure the ringworld for Origin: Shattered Ring spawns symmetrically
* 3.3.0 Mark as compatible with Stellaris 3.7 "Canis Minor" - no script changes

## Source Code

Hosted on [GitHub](https://github.com/corsairmarks/ringworld_graphical_enhancements)

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.