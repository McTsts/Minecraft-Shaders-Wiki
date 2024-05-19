# Contents

The part in brackets is a summary and not a full list of everything each shader affects. Only the more common things are listed here for quick access.

- [Non-Rendertype](#non-rendertype)
  - [blit_screen](#blit_screen) (Copy)
  - [particle](#particle) (Particles)
  - [position](#position) (Sky)
  - [position_color](#position_color) (Pre 1.20 Solid Color UI)
  - [position_tex](#position_tex) (Texture UI, Worldborder, Sun/Moon)
  - [position_color_tex](#position_color_tex) (Fire/Wall Overlay)
  - [position_tex_color](#position_tex_color) (End Sky, Menu Background)
- [Rendertype](#rendertype)
  - [Blocks](#blocks)
    - [solid](#solid) (Solid Blocks, Lava, Solid Falling Blocks)
    - [cutout](#cutout) (Most Non-Cube-Hitbox Blocks)
    - [cutout_mipped](#cutout_mipped) (Some Non-Cube-Hitbox Blocks)
    - [translucent](#translucent) (Water, Transparent Blocks)
    - [translucent_moving_block](#translucent_moving_block) (Moving Blocks from Pistons)
    - [tripwire](#tripwire) (Tripwire (Middle Section))
    - [end_portal](#end_portal-and-end_gateway) (End Portal)
    - [end_gateway](#end_portal-and-end_gateway) (End Gateway)
  - [Entities](#entities)
    - [entity_cutout_no_cull](#entity_cutout_no_cull) (Entities)
    - [entity_translucent](#entity_translucent) (Overlays/Transparent Parts)
    - [entity_solid](#entity_solid) (Entity-style Objects)
    - [entity_translucent_cull](#entity_translucent_cull) (Non-block-placing Items)
    - [entity_cutout](#entity_cutout) (Block-placing Items)
    - [armor_cutout_no_cull](#armor_cutout_no_cull) (Armor)
    - [armor_entity_glint](#armor_entity_glint) (Worn Armor Enchant Glint)
    - [entity_glint_direct](#entity_glint_direct) (Enchanted Trident Glint)
    - [glint](#glint) (Glass Enchant Glint)
    - [glint_direct](#glint_direct) (Standard Enchant Glint)
    - [glint_translucent](#glint_translucent) (Glass enchanted glint in `Fabulous!`)
    - [energy_swirl](#energy_swirl) (Charged Creeper, Wither Swirl)
    - [eyes](#eyes) (Entities with glowing eyes)
    - [leash](#leash) (Leash)
    - [entity_shadow](#entity_shadow) (Entity Shadow)
    - [entity_cutout_no_cull_z_offset](#entity_cutout_no_cull_z_offset) (Mob Skulls, Minecart, Shulker)
    - [entity_decal](#entity_decal) (Ender Dragon Death)
    - [entity_alpha](#entity_alpha) (Ender Dragon Death Wings)
    - [item_entity_translucent_cull](#item_entity_translucent_cull) (XP Orbs, Fabulous translucent items, Invisible Entities)
    - [entity_smooth_cutout](#entity_smooth_cutout) (End Crystal Beams)
    - [entity_translucent_emissive](#entity_translucent_emissive) (Glowing parts of Warden texture)
    - [entity_no_outline](#entity_no_outline) (Banner)
    - [water_mask](#water_mask) (Hides water in boats)
    - [outline](#outline) (Glowing)
    - [lightning](#lightning) (Lightning, Ender dragon death animation beams)
  - [UI](#ui)
    - [gui](#gui) (Solid Color UI)
    - [gui_ghost_recipe_overlay](#gui_ghost_recipe_overlay) (Recipe Book Missing Item Overlay)
    - [gui_overlay](#gui_overlay) (Generic Overlay Effects)
    - [gui_text_highlight](#gui_text_highlight) (Highlighted Text)
    - [text](#text) (Text)
    - [text_see_through](#text_see_through) (Name Plates, Text Through Walls)
    - [text_background](#text_background) (Text Display Entity Background)
    - [text_background_see_through](#text_background_see_through) (Text Display Entity Background Through Walls)
    - [text_intensity](#text_intensity) (TTF Fonts)
    - [text_intensity_see_through](#text_intensity_see_through) (TTF Fonts Through Walls)
  - [Other](#other)
    - [lines](#lines) (Block Outline, Hitboxes, Fishing Rod Line)
    - [clouds](#clouds) (Clouds)
    - [crumbling](#crumbling) (Mining Block Cracks)
    - [beacon_beam](#beacon_beam) (Beacon Beam)
- [Unknown](#unknown)
  - [position_color_lightmap](#position_color_lightmap)
  - [position_color_tex_lightmap](#position_color_tex_lightmap)
  - [rendertype_armor_glint](#rendertype_armor_glint)
- [Removed](#removed)
  - [block](#block)
  - [new_entity](#new_entity)
  - [rendertype_translucent_no_crumbling](#rendertype_translucent_no_crumbling)

# Non-Rendertype
There are several shaders which are not prefixed with `rendertype_`. These seem to be for more general targets, such as the sky or all particles.  

### blit_screen <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/blit_screen.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/blit_screen.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/blit_screen.fsh">fsh</a></span>

Blit copies one buffer to another, however this cannot be overridden in a resource pack.

[Back to Top](#contents)

---

### particle <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/particle.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/particle.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/particle.fsh">fsh</a></span>

Weather (snow and rain) and all particles. The alpha value specified in the shader will override the particle’s inbuilt transparency e.g. in the sneeze particle. Others, like the splash particle, don't seem to allow this. More testing needed.

[Back to Top](#contents)

---

### position <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position.fsh">fsh</a></span>

The colour of the sky. Also affects text highlighting. 

[Back to Top](#contents)

---

### position_color <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color.fsh">fsh</a></span>

Handles a few different things:
* The transparent lower hemisphere overlay on the sky approximately between times 11315 to 14150 (sunset) and 21830 to 24670 (sunrise),
* The f3+G chunk border displays,

Pre 1.20:
* The black transparent background on UI elements such as the chat field, the pause menu, and the scoreboard sidebar,
* The Mojang loading background,
* Highlighting item slots,
* The background of tooltips,
* The black bars on the sides when scoped in with a spyglass,


For UI elements, Position is the screen size divided by the GUI scale. E.g. 1920x1080 with GUI scale 3 means Position for x will be [0,640] and for y [0,360].

<img src="images/position_color.png" width=600>

[Back to Top](#contents)

---

### position_tex <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_tex.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_tex.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_tex.fsh">fsh</a></span>

Handles a few different things:
* The Sun and Moon,
* The worldborder, 
* Most GUI textures (like the hotbar, buttons), 
* Overlays (pumpkin blur, powder snow, the vignette),
* The crosshair.
* The mojang logo in loading screens.

<img src="images/position_tex.png" width=600>

[Back to Top](#contents)

---

### position_color_tex <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_tex.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_tex.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_tex.fsh">fsh</a></span>

Fire overlay when the player is burning.  
Wall overlay when player is suffocating

<img src="images/position_color_tex.png" width=600>
<img src="images/wall_overlay.png" width=600>



[Back to Top](#contents)

---

### position_tex_color <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_tex_color.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_tex_color.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_tex_color.fsh">fsh</a></span>

The End sky, main menu panorama, and menu backgrounds.

<img src="images/position_tex_color.png" width=600>

[Back to Top](#contents)

# Rendertype
These are shaders which are targeted towards a specific element of the display.
**For each shader name here, assume that it is prefixed with `rendertype_`.**

## Blocks
When dealing with block shaders which have something to do with `translucent`, `cutout` or `cutout_mipped`, here is a [useful list](List%20of%20Blocks%20Affected.md) for all blocks of those specific types.

[Back to Top](#contents)


### solid <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_solid.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_solid.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_solid.fsh">fsh</a></span>

All solid blocks, lava, and when in fast mode, leaves. Also affects non-translucent falling blocks.

<img src="images/rendertype_solid.png" width=400> <img src="images/rendertype_solid_2.png" width=400>

[Back to Top](#contents)

---

### cutout <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_cutout.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_cutout.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_cutout.fsh">fsh</a></span>

All non-cube-hitbox blocks, check the list in the section header.
A list of all blocks rendered by this shader can be found [here](List%20of%20Blocks%20Affected.md#cutout).

<img src="images/rendertype_cutout.png" width=600>

[Back to Top](#contents)

---

### cutout_mipped <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_cutout_mipped.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_cutout_mipped.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_cutout_mipped.fsh">fsh</a></span>

Certain blocks not covered by other shaders, check the list in the section header. Covers leaves in fancy/fabulous graphics.
A list of all blocks rendered by this shader can be found [here](List%20of%20Blocks%20Affected.md#cutout_mipped).

<img src="images/rendertype_cutout_mipped.png" width=600>

[Back to Top](#contents)

---

### translucent <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_translucent.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_translucent.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_translucent.fsh">fsh</a></span>

Translucent blocks like stained glass, check the list in the section header.
A list of all blocks rendered by this shader can be found [here](List%20of%20Blocks%20Affected.md#translucent).

<img src="images/rendertype_translucent.png" width=400> <img src="images/rendertype_translucent_2.png" width=400>

[Back to Top](#contents)

---

### translucent_moving_block <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_translucent_moving_block.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_translucent_moving_block.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_translucent_moving_block.fsh">fsh</a></span>

Blocks which are translucent and are being moved by a piston.

<img src="images/rendertype_translucent_moving_block.png" width=400>

[Back to Top](#contents)

---

### tripwire <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_tripwire.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_tripwire.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_tripwire.fsh">fsh</a></span>

The middle section(s) of a tripwire.  

<img src="images/rendertype_tripwire.png" width=600>

[Back to Top](#contents)

---

### end_portal <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_end_portal.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_end_portal.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_end_portal.fsh">fsh</a></span>

The strange image in the end portal and end gateways.
The shader files are called `end_portal.vsh`/`fsh`/`json`, with `end_gateway.json` referencing them.

<img src="images/rendertype_end_portal.png" width=400> <img src="images/rendertype_end_gateway.png" width=300>

[Back to Top](#contents)

---

## Entities
Shaders that render entities.

### entity_cutout_no_cull <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout_no_cull.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout_no_cull.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout_no_cull.fsh">fsh</a></span>

All entities, guardian beams, placed signs, and shulker boxes (both placed and in inventory)

<img src="images/rendertype_entity_cutout_no_cull.png" width=400> <img src="images/rendertype_entity_cutout_no_cull_2.png" width=800>

[Back to Top](#contents)

---

### entity_translucent <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent.fsh">fsh</a></span>

Translucent entities and parts of entities: 
* Slimes,
* Players (except for the lower layer of the arm in first person),
* Player heads, 
* Markings on horses, 
* Shulker bullets, 
* Elder guardian particle effect. 

Sampler1 contains the red color that is overlayed on entities when they take damage.

<img src="images/rendertype_entity_translucent.png" height=200> <img src="images/rendertype_entity_translucent_2.png" height=200>

[Back to Top](#contents)

---

### entity_solid <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_solid.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_solid.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_solid.fsh">fsh</a></span>

Handles a few different things: 
* The base (not flag) of banners,
* Shulker heads, 
* Books on lecterns/enchantment tables, 
* Shields, 
* Beds, 
* The bell part of bells, 
* Capes, 
* Shells of conduits, 
* Paintings, 
* Tridents, 
* The ears on the Deadmau5 skin,
* The bottom skin layer of the first-person hand,
* The conduit item in the inventory.

With item frames, the item frame entity itself is part of the shader, however, items on it are not. Only the filled-in parts of maps placed on an item frame are part of the shader.

<img src="images/rendertype_entity_solid.png" width=300> <img src="images/rendertype_entity_solid_2.png" width=300> <img src="images/rendertype_entity_solid_3.png" width=300>

[Back to Top](#contents)

---

### entity_translucent_cull <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent_cull.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent_cull.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent_cull.fsh">fsh</a></span>

Flat texture items and transparent blocks held by entities or on head, in the inventory, and as entities. If Fabulous graphics is off, this shader also affects translucent items like stained glass and their panes, however if it is on, you should check [item_entity_translucent_cull](#item_entity_translucent_cull).

<img src="images/rendertype_entity_translucent_cull.png" height=200> <img src="images/rendertype_entity_translucent_cull_2.png" height=200>

[Back to Top](#contents)

---

### armor_cutout_no_cull <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_armor_cutout_no_cull.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_armor_cutout_no_cull.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_armor_cutout_no_cull.fsh">fsh</a></span>

Armor and armor trims on entities.

<img src="images/rendertype_armor_cutout_no_cull.png" width=300>

[Back to Top](#contents)

---

### armor_entity_glint <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_armor_entity_glint.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_armor_entity_glint.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_armor_entity_glint.fsh">fsh</a></span>

The glint on enchanted armour. Slight transparency is inbuilt and unchangeable.

<img src="images/rendertype_armor_entity_glint.png" width=300>

[Back to Top](#contents)

---

### entity_glint_direct <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_glint_direct.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_glint_direct.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_glint_direct.fsh">fsh</a></span>

The glint on enchanted tridents.

<img src="images/rendertype_entity_glint_direct.png" width=500>

[Back to Top](#contents)

---

### glint <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint.fsh">fsh</a></span>

The glint on (stained) glass and (stained) glass panes, while rendered in the world. That means as dropped item, in an item frame, when held (except for when you're holding it yourself and are in first person view (default)). Does *not* render glass in inventory or when held in first person view, in those cases it's rendered by `glint_direct`. 

[Back to Top](#contents)

---

### glint_direct <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint_direct.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint_direct.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint_direct.fsh">fsh</a></span>

The enchant glint in most situations. Enchanted worn armor is rendered by `armor_entity_glint` and glass type blocks are rendered by `glint` when in world instead.

[Back to Top](#contents)

---

### glint_translucent <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint_translucent.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint_translucent.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_glint_translucent.fsh">fsh</a></span>

The enchant glint in translucent blocks (like stained glass) in world when graphics setting is `Fabulous!`.

<img src="images/rendertype_glint_translucent.png" width=200> 

[Back to Top](#contents)

---

### energy_swirl <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_energy_swirl.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_energy_swirl.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_energy_swirl.fsh">fsh</a></span>

Charged creeper and wither swirling outline.

<img src="images/rendertype_energy_swirl.png" height=200> <img src="images/rendertype_energy_swirl_2.png" height=200>

[Back to Top](#contents)

---

### eyes <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_eyes.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_eyes.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_eyes.fsh">fsh</a></span>

A shader for the entire body of an entity that has glowing eyes (not the eyes themselves). Not fully opaque.

<img src="images/rendertype_eyes.png" height=200> <img src="images/rendertype_eyes_2.png" height=200>

[Back to Top](#contents)

---

### leash <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_leash.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_leash.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_leash.fsh">fsh</a></span>

Leads, both on entities and fences.

<img src="images/rendertype_leash.png" width=300> 

[Back to Top](#contents)

---

### entity_shadow <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_shadow.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_shadow.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_shadow.fsh">fsh</a></span>

Blocks that are affected by an entity’s shadow, but not the shadow itself. Locked to the block grid.

<img src="images/rendertype_entity_shadow.png" width=300> 

[Back to Top](#contents)

---

### entity_cutout_no_cull_z_offset <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout_no_cull_z_offset.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout_no_cull_z_offset.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout_no_cull_z_offset.fsh">fsh</a></span>

Mob skulls, both on entities and as an item. Does not include player heads. Also handles shulker shells and minecarts.

<img src="images/rendertype_entity_cutout_no_cull_z_offset.png" width=200> <img src="images/rendertype_entity_cutout_no_cull_z_offset_2.png" width=200> 

[Back to Top](#contents)

---

### entity_cutout <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_cutout.fsh">fsh</a></span>

Block items in the inventory or hand/head of an entity, chests, ender chests, chest in minecarts, and as entities. Does not include Shulker boxes (see [entity_cutout_no_cull](#entity_cutout_no_cull)). Also used for the fire overlay on burning entities.

<img src="images/rendertype_entity_cutout.png" width=300> 

[Back to Top](#contents)

---

### entity_decal <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_decal.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_decal.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_decal.fsh">fsh</a></span>

Colors the Ender Dragon while it’s dying.

<img src="images/rendertype_entity_decal.png" width=300> 

[Back to Top](#contents)

---


### item_entity_translucent_cull <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_item_entity_translucent_cull.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_item_entity_translucent_cull.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_item_entity_translucent_cull.fsh">fsh</a></span>

Handles dropped translucent items in Fabulous graphics. Also affects invisible entities while using spectator mode or the gamerule `seeFriendlyInvisibles`, as well as experience orbs in all graphics settings.

<img src="images/rendertype_item_entity_translucent_cull.png" width=300> <img src="images/rendertype_item_entity_translucent_cull_2.png" width=300> 

[Back to Top](#contents)

---

### entity_translucent_emissive <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent_emissive.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent_emissive.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_translucent_emissive.fsh">fsh</a></span>

Glowing parts of Warden texture.

![image](https://user-images.githubusercontent.com/16228717/172488347-e17307b9-7ddf-4668-a464-9b606aad50aa.png)

[Back to Top](#contents)

---

### entity_smooth_cutout <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_smooth_cutout.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_smooth_cutout.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_smooth_cutout.fsh">fsh</a></span>

End crystal beams.

<img src="images/rendertype_entity_smooth_cutout.png" width=300> 

[Back to Top](#contents)

---

### entity_no_outline <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_no_outline.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_no_outline.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_no_outline.fsh">fsh</a></span>

The color and pattern of banners.

<img src="images/rendertype_entity_no_outline.png" width=300> 

[Back to Top](#contents)

---

### entity_alpha <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_alpha.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_alpha.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_entity_alpha.fsh">fsh</a></span>

Used in the death animation of the dragon. Seemingly only affects the dragon’s wings, possibly messed with in code?

<img src="images/rendertype_entity_alpha.png" width=300> 

[Back to Top](#contents)

---


### water_mask <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_water_mask.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_water_mask.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_water_mask.fsh">fsh</a></span>

Hides the water in a boat. Changing the color does not seem to have an effect, but changing the position does. Pictured left is moving the mask down by 64, pictured right is moving it to the right by 2.

<img src="images/rendertype_water_mask.png" width=300> <img src="images/rendertype_water_mask_2.png" width=300> 

[Back to Top](#contents)

---

### outline <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_outline.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_outline.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_outline.fsh">fsh</a></span>

Glowing effect on entities. This buffer draws color on the entire entity, which is later turned into an outline by the entity_outline post shader.

<img src="images/rendertype_outline.png" width=300> 

[Back to Top](#contents)

---

### lightning <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_lightning.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_lightning.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_lightning.fsh">fsh</a></span>

Lightning bolts.
Ender dragon death animation beams.

[Back to Top](#contents)

---

## UI
These are shaders which affect some part of the UI. Some UI elements are rendered by [Non-Rendertype](#non-rendertype) shaders.

---

### gui <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui.fsh">fsh</a></span>

* The black transparent background on UI elements such as the chat field, the pause menu, the scoreboard sidebar, and subtitles
* The Mojang resource pack loading bar
* Highlighting worlds, servers, and players in social interactions menu
* The background of tooltips
* Scroll bar and scroll bar background
* World selection, recipe book, and social interactions search bar background
* World loading animation
* Crafting red missing item background (when using recipe book)

<img src="images/rendertype_gui.png" width=400> <img src="images/rendertype_gui_2.png" width=400> 

[Back to Top](#contents)

---

### gui_ghost_recipe_overlay <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_ghost_recipe_overlay.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_ghost_recipe_overlay.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_ghost_recipe_overlay.fsh">fsh</a></span>

* Crafting translucent missing item overlay (when using recipe book)

<figure>
  <img src="images/rendertype_gui_ghost_recipe_overlay.png" width=400> 
  <figcaption>*highlighted in green for better contrast*</figcaption>
</figure>

[Back to Top](#contents)

---

### gui_overlay <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_overlay.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_overlay.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_overlay.fsh">fsh</a></span>

* The Mojang resource pack loading background color
* The black bars on the sides when scoped in with a spyglass
* Highlighting item slots
* World and server selection menu drop-shadow

[Back to Top](#contents)

---

### gui_text_highlight <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_text_highlight.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_text_highlight.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_gui_text_highlight.fsh">fsh</a></span>

* All highlighted/selected text

<img src="images/rendertype_gui_text_highlight.png" width=300> 

[Back to Top](#contents)

---

### text <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text.fsh">fsh</a></span>

All parts of text, including the shadow. This encompasses all text rendered including: F3 Menu, Menu button text, Entity names, Text display entities, Item names, descriptions & amounts in the inventory and the Chat etc. It also does the explored parts of maps

---

#### Isolating Elements
Isolating certain texts. Different types of text can be isolated using their Position.z. Texts without a shadow are located at x, texts with a shadow are located at x + 0.03 with their shadow being at x. (e.g. at 0.0 and 0.03). *This seems to no longer be true in 1.19.4*

A basic list of where which text is located: (Not Complete! *Last checked in 1.18, unless noted otherwise*)
* -200: Advancement menu text
* 0: /title text, bossbar name, world/server selection name/description text, resourcepack selection "Available" and "Selected" text.
* 0.03: Menu (pause/options) text and inventory Potion effect text
* 0.06 [1.19.4]: Subtitle Text (shadow at 0.0)
* 0.12 [1.19.4]: Title Text (shadow at 0.0)
* 100: Chat display, Recipe book search text
* 200: Item count in hotbar
* 300: Item count in inventory
* 400: Item count while dragging item, tooltip texts, compact potion info
* 0 to 104: Maps (not actually text)

Since maps share the z value with the chat display and a part of the hotbar item count, you can test for Sampler0 having a size of 128 pixels in both directions to test for the face being a map.

<img src="images/rendertype_text.png" width=400>

[Back to Top](#contents)

---

### text_see_through <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_see_through.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_see_through.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_see_through.fsh">fsh</a></span>

* The background nameplate of an entity’s custom name
* Nametag text when seen through walls
* Text display entity text when `see_through:true` nbt is set

<img src="images/rendertype_text_see_through.png" width=400>

[Back to Top](#contents)

---

### text_background <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_background.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_background.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_background.fsh">fsh</a></span>

* Text display entity background box

[Back to Top](#contents)

---

### text_background_see_through <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_background_see_through.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_background_see_through.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_background_see_through.fsh">fsh</a></span>

* Text display entity background box when `see_through:true` nbt is set

[Back to Top](#contents)

---

### text_intensity <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_intensity.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_intensity.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_intensity.fsh">fsh</a></span>

* Behaves like rendertype_text but when TTF font is used in the resourcepack
* See [text](#text)

<img src="images/rendertype_text_intensity.png" width=400>

[Back to Top](#contents)

---

### text_intensity_see_through <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_intensity_see_through.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_intensity_see_through.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_text_intensity_see_through.fsh">fsh</a></span>

* Behaves like rendertype_text_see_through but when TTF font is used in the resourcepack
* See [text_see_through](#text_see_through)

[Back to Top](#contents)
  
---

## Other
These are shaders that render things that aren't clearly either a block, an entity or a ui element.

### lines <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_lines.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_lines.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_lines.fsh">fsh</a></span>

Handles a few different things:
* The outline when hovering over a block,
* The debug crosshair,
* The f3+B hitbox displays,
* Previews in the structure block.

<img src="images/rendertype_lines.png" width=300> <img src="images/rendertype_lines_2.png" width=400>

[Back to Top](#contents)

---

### crumbling <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_crumbling.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_crumbling.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_crumbling.fsh">fsh</a></span>

The block cracks when mining a block. Has some in-built transparency.  

<img src="images/rendertype_crumbling.png" width=600>

[Back to Top](#contents)

---

### clouds <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_clouds.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_clouds.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_clouds.fsh">fsh</a></span>

Clouds.  
Prior to 24w05a, the shader was not a rendertype and was named `position_tex_color_normal`.  

<img src="images/rendertype_clouds.png" width=600>

[Back to Top](#contents)

---

### beacon_beam <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_beacon_beam.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_beacon_beam.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_beacon_beam.fsh">fsh</a></span>

The beam of a beacon. Seems to get rendered behind clouds.  

<img src="images/rendertype_beacon_beam.png" width=300>

[Back to Top](#contents)

# Unknown

These are shaders that exist in the files that we do not currently know the purpose of. More testing is needed for these.


### position_color_lightmap <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_lightmap.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_lightmap.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_lightmap.fsh">fsh</a></span>

Similar to `position_color`, but includes a second sampler for lightmap calculations. Not observed ingame.

[Back to Top](#contents)

---

### position_color_tex_lightmap <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_tex_lightmap.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_tex_lightmap.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/position_color_tex_lightmap.fsh">fsh</a></span>

Similar to `position_color_tex`, but includes a second sampler for lightmap calculations. Not observed ingame.

[Back to Top](#contents)

---

### rendertype_armor_glint <span style="font-size:0.6em;vertical-align:middle;"><a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertypermor_glint.json">json</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_armor_glint.vsh">vsh</a> • <a title="View on mcmeta" href="https://github.com/misode/mcmeta/blob/assets/assets/minecraft/shaders/core/rendertype_armor_glint.fsh">fsh</a></span>

Unknown.

[Back to Top](#contents)


# Removed

### block

> Removed in 23w18a

Has 2 ins (`UV0` and `UV2`) and 2 outs (`texCoord0` and `texCoord2`), no math other than what’s included in most other shaders. Not observed ingame, may only be used as a base.

[Back to Top](#contents)

---

### new_entity

> Removed in 23w18a

Has 3 ins (`UV0`, `UV1`, and `UV2`) and 3 outs (`texCoord0`, `texCoord1`, and `texCoord2`), no math other than what’s included in most other shaders. Not observed ingame, may only be used as a base.

[Back to Top](#contents)

---

### rendertype_translucent_no_crumbling

> Removed in 23w42a

Unknown.

[Back to Top](#contents)

---

