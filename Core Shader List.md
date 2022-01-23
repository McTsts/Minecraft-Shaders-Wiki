# Contents

The part in brackets is a summary and not a full list of everything each shader affects. Only the more common things are listed here for quick access.

- [Non-Rendertype](#non-rendertype)
  - [blit_screen](#blit_screen) (Copy)
  - [particle](#particle) (Particles)
  - [position](#position) (Sky)
  - [position_color](#position_color) (Solid Color UI)
  - [position_tex](#position_tex) (Texture UI, Worldborder, Sun/Moon)
  - [position_tex_color_normal](#position_tex_color_normal) (Clouds)
  - [position_color_tex](#position_color_tex) (Fire Overlay)
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
    - [armor_entity_glint](#armor_entity_glint) (Enchant Glint)
    - [energy_swirl](#energy_swirl) (Charged Creeper, Wither Swirl)
    - [eyes](#eyes) (Entities with glowing eyes)
    - [leash](#leash) (Leash)
    - [entity_shadow](#entity_shadow) (Entity Shadow)
    - [entity_cutout_no_cull_z_offset](#entity_cutout_no_cull_z_offset) (Mob Skulls, Minecart, Shulker)
    - [entity_decal](#entity_decal) (Ender Dragon Death)
    - [entity_alpha](#entity_alpha) (Ender Dragon Death Wings)
    - [item_entity_translucent_cull](#item_entity_translucent_cull) (XP Orbs, Fabolous translucent items)
    - [entity_smooth_cutout](#entity_smooth_cutout) (End Crystal Beams)
    - [entity_no_outline](#entity_no_outline) (Banner)
    - [water_mask](#water_mask) (Hides water in boats)
    - [outline](#outline) (Glowing)
    - [lightning](#lightning) (Lightning)
  - [UI](#ui)
    - [text](#text) (Text)
    - [text_see_through](#text_see_through) (Name Plates)
  - [Other](#other)
    - [lines](#lines) (Block Outline, Hitboxes, Fishing Rod Line)
    - [crumbling](#crumbling) (Mining Block Cracks)
    - [beacon_beam](#beacon_beam) (Beacon Beam)
- [Unknown](#unknown)
  - [block](#block)
  - [new_entity](#new_entity)
  - [position_color_lightmap](#position_color_lightmap)
  - [position_color_tex_lightmap](#position_color_tex_lightmap)
  - [position_tex_lightmap_color](#position_tex_lightmap_color)
  - [rendertype_text_intensity](#rendertype_text_intensity)
  - [rendertype_text_intensity_see_through](#rendertype_text_intensity_see_through)
  - [rendertype_armor_glint](#rendertype_armor_glint)
- [Unused](#unused)
  - [position_color_normal](#position_color_normal)

# Non-Rendertype
There are several shaders which are not prefixed with `rendertype_`. These seem to be for more general targets, such as the sky or all particles.  

### blit_screen  
Blit copies one buffer to another, however this cannot be overridden in a resource pack. 

[Back to Top](#contents)

---

### particle  
Weather (snow and rain) and all particles. The alpha value specified in the shader will override the particle’s inbuilt transparency e.g. in the sneeze particle. Others, like the splash particle, don't seem to allow this. More testing needed.

[Back to Top](#contents)

---

### position
The colour of the sky. Also affects text highlighting. 

[Back to Top](#contents)

---

### position_color
Handles a few different things:
* The black transparent background on UI elements such as the chat field or the pause menu,
* The Mojang loading background,
* Highlighting item slots,
* The background of tooltips,
* The transparent lower hemisphere overlay on the sky approximately between times 11315 to 14150 (sunset) and 21830 to 24670 (sunrise),
* The black bars on the sides when scoped in with a spyglass.

For UI elements, Position is the screen size divided by the GUI scale. E.g. 1920x1080 with GUI scale 3 means Position for x will be [0,640] and for y [0,360].

<img src="https://github.com/McTsts/shaders/blob/main/images/position_color.png" width=600>

[Back to Top](#contents)

---

### position_tex
Handles a few different things:
* The Sun and Moon,
* The worldborder, 
* Most GUI textures (like the hotbar, buttons), 
* Overlays (pumpkin blur, powder snow, the vignette),
* The crosshair.

<img src="https://github.com/McTsts/shaders/blob/main/images/position_tex.png" width=600>

[Back to Top](#contents)

---

### position_tex_color_normal 
Clouds.  

<img src="https://github.com/McTsts/shaders/blob/main/images/position_tex_color_normal.png" width=600>

[Back to Top](#contents)

---

### position_color_tex 
Fire overlay when the player is burning.  

<img src="https://github.com/McTsts/shaders/blob/main/images/position_color_tex.png" width=600>

[Back to Top](#contents)

---

### position_tex_color
The End sky, main menu panorama, and menu backgrounds.

<img src="https://github.com/McTsts/shaders/blob/main/images/position_tex_color.png" width=600>

[Back to Top](#contents)

# Rendertype
These are shaders which are targeted towards a specific element of the display.
**For each shader name here, assume that it is prefixed with `rendertype_`.**

## Blocks
When dealing with block shaders which have something to do with `translucent`, `cutout` or `cutout_mipped`, here is a [useful list](List%20of%20Blocks%20Affected.md) for all blocks of those specific types.

[Back to Top](#contents)


### solid
All solid blocks, lava, and when in fast mode, leaves. Also affects non-translucent falling blocks.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_solid.png" width=400> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_solid_2.png" width=400>

[Back to Top](#contents)

---

### cutout
All non-cube-hitbox blocks, check the list in the section header.
A list of all blocks rendered by this shader can be found [here](List%20of%20Blocks%20Affected.md#cutout).

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_cutout.png" width=600>

[Back to Top](#contents)

---

### cutout_mipped
Certain blocks not covered by other shaders, check the list in the section header. Covers leaves in fancy/fabulous graphics.
A list of all blocks rendered by this shader can be found [here](List%20of%20Blocks%20Affected.md#cutout_mipped).

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_cutout_mipped.png" width=600>

[Back to Top](#contents)

---

### translucent
Translucent blocks like stained glass, check the list in the section header.
A list of all blocks rendered by this shader can be found [here](List%20of%20Blocks%20Affected.md#translucent).

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_translucent.png" width=400> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_translucent_2.png" width=400>

[Back to Top](#contents)

---

### translucent_moving_block
Blocks which are translucent and are being moved by a piston.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_translucent_moving_block.png" width=400>

[Back to Top](#contents)

---

### tripwire
The middle section(s) of a tripwire.  

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_tripwire.png" width=600>

[Back to Top](#contents)

---

### end_portal (and end_gateway)
The strange image in the end portal and end gateways.
The shader files are called `end_portal.vsh`/`fsh`/`json`, with `end_gateway.json` referencing them.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_end_portal.png" width=400> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_end_gateway.png" width=300>

[Back to Top](#contents)

---

## Entities
Shaders that render entities.

### entity_cutout_no_cull
All entities, guardian beams, placed signs, and shulker boxes (both placed and in inventory)

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_cutout_no_cull.png" width=400> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_cutout_no_cull_2.png" width=800>

[Back to Top](#contents)

---

### entity_translucent
Translucent entities and parts of entities: 
* Slimes,
* Players (except for the lower layer of the arm in first person),
* Player heads, 
* Markings on horses, 
* Shulker bullets, 
* Elder guardian particle effect. 

Sampler1 contains the red color that is overlayed on entities when they take damage.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_translucent.png" height=200> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_translucent_2.png" height=200>

[Back to Top](#contents)

---

### entity_solid
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

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_solid.png" width=300> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_solid_2.png" width=300> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_solid_3.png" width=300>

[Back to Top](#contents)

---

### entity_translucent_cull
Flat texture items and transparent blocks held by entities or on head, and in the inventory. If Fabulous graphics is off, this shader also affects translucent items like stained glass and their panes, however if it is on, you should check [item_entity_translucent_cull](#item_entity_translucent_cull).

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_translubucent_cull.png" height=200> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_translucent_cull_2.png" height=200>

[Back to Top](#contents)

---

### armor_cutout_no_cull
Armour on entities.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_armor_cutout_no_cull.png" width=300>

[Back to Top](#contents)

---

### armor_entity_glint
The glint on enchanted armour. Slight transparency is inbuilt and unchangeable.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_armor_entity_glint.png" width=300>

[Back to Top](#contents)

---

### energy_swirl
Charged creeper and wither swirling outline.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_energy_swirl.png" height=200> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_energy_swirl_2.png" height=200>

[Back to Top](#contents)

---

### eyes
A shader for the entire body of an entity that has glowing eyes (not the eyes themselves). Not fully opaque.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_eyes.png" height=200> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_eyes_2.png" height=200>

[Back to Top](#contents)

---

### leash
Leads, both on entities and fences.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_leash.png" width=300> 

[Back to Top](#contents)

---

### entity_shadow
Blocks that are affected by an entity’s shadow, but not the shadow itself. Locked to the block grid.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_shadow.png" width=300> 

[Back to Top](#contents)

---

### entity_cutout_no_cull_z_offset
Mob skulls, both on entities and as an item. Does not include player heads. Also handles shulker shells and minecarts.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_cutout_no_cull_z_offset.png" width=200> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_cutout_no_cull_z_offset_2.png" width=200> 

[Back to Top](#contents)

---

### entity_cutout
Block items in the inventory or hand/head of an entity, as well as chests in minecarts. Does not include Shulker boxes (see [entity_cutout_no_cull](#entity_cutout_no_cull)). Also used for the fire overlay on burning entities.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_cutout.png" width=300> 

[Back to Top](#contents)

---

### entity_decal
Colors the Ender Dragon while it’s dying.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_decal.png" width=300> 

[Back to Top](#contents)

---


### item_entity_translucent_cull
Handles dropped translucent items in Fabulous graphics. Also affects invisible entities while using spectator mode or the gamerule `seeFriendlyInvisibles`, as well as experience orbs in all graphics settings.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_item_entity_translucent_cull.png" width=300> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_item_entity_translucent_cull_2.png" width=300> 

[Back to Top](#contents)

---

### entity_smooth_cutout
End crystal beams.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_smooth_cutout.png" width=300> 

[Back to Top](#contents)

---

### entity_no_outline
The color and pattern of banners.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_no_outline.png" width=300> 

[Back to Top](#contents)

---

### entity_alpha
Used in the death animation of the dragon. Seemingly only affects the dragon’s wings, possibly messed with in code?

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_entity_alpha.png" width=300> 

[Back to Top](#contents)

---


### water_mask
Hides the water in a boat. Changing the color does not seem to have an effect, but changing the position does. Pictured left is moving the mask down by 64, pictured right is moving it to the right by 2.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_water_mask.png" width=300> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_water_mask_2.png" width=300> 

[Back to Top](#contents)

---

### outline
Glowing effect on entities. This buffer draws color on the entire entity, which is later turned into an outline by the entity_outline post shader.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_outline.png" width=300> 

[Back to Top](#contents)

---

### lightning
Lightning bolts.

[Back to Top](#contents)

---



---

## UI
These are shaders which affect some part of the UI. This is currently just text, as most UI elements are rendered by [Non-Rendertype](#non-rendertype) shaders.

### text
All parts of text, including the shadow. This encompasses all text rendered including: F3 Menu, Menu button text, Entity names, Item names, descriptions & amounts in the inventory and the Chat etc. It also does the explored parts of maps

#### Isolating Elements
Isolating certain texts. Different types of text can be isolated using their Position.z. Texts without a shadow are located at x, texts with a shadow are located at x + 0.03 with their shadow being at x. (e.g. at 0.0 and 0.03).

A basic list of where which text is located: (Not Complete!)
* -200: Advancement menu text
* 0: /title text, bossbar name, world/server selection name/description text, resourcepack selection "Available" and "Selected" text.
* 0.03: Menu (pause/options) text and inventory Potion effect text
* 100: Chat display
* 200: Item count in hotbar
* 300: Item count in inventory
* 400: Item count while dragging item, tooltip texts, compact potion info
* 0 to 104: Maps (not actually text)

Since maps share the z value with the chat display and a part of the hotbar item count, you can test for Sampler0 having a size of 128 pixels in both directions to test for the face being a map.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_text.png" width=400>

[Back to Top](#contents)

---

### text_see_through
The background nameplate of an entity’s custom name.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_text_see_through.png" width=400>

[Back to Top](#contents)

---

## Other
These are shaders that render things that aren't clearly either a block, an entity or a ui element.

### lines
Handles a few different things:
* The outline when hovering over a block,
* The debug crosshair,
* The f3+B hitbox displays,
* The f3+G chunk border displays,
* Previews in the structure block.

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_lines.png" width=300> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_lines_2.png" width=400>

[Back to Top](#contents)

---

### crumbling
The block cracks when mining a block. Has some in-built transparency.  

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_crumbling.png" width=600>

[Back to Top](#contents)

---

### beacon_beam
The beam of a beacon. Seems to get rendered behind clouds.  

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_beacon_beam.png" width=300>

[Back to Top](#contents)

# Unknown

These are shaders that exist in the files that we do not currently know the purpose of. More testing is needed for these.

### block
Has 2 ins (`UV0` and `UV2`) and 2 outs (`texCoord0` and `texCoord2`), no math other than what’s included in most other shaders. Not observed ingame, may only be used as a base.

[Back to Top](#contents)

---

### new_entity
Has 3 ins (`UV0`, `UV1`, and `UV2`) and 3 outs (`texCoord0`, `texCoord1`, and `texCoord2`), no math other than what’s included in most other shaders. Not observed ingame, may only be used as a base.

[Back to Top](#contents)

---

### position_color_lightmap
Similar to `position_color`, but includes a second sampler for lightmap calculations. Not observed ingame.

[Back to Top](#contents)

---

### position_color_tex_lightmap
Similar to `position_color_tex`, but includes a second sampler for lightmap calculations. Not observed ingame.

[Back to Top](#contents)

---

### position_tex_lightmap_color
Similar to `position_tex_color`, but includes a second sampler for lightmap calculations. Not observed ingame.

[Back to Top](#contents)

---

### rendertype_text_intensity
Functionally the same as `rendertype_text`, except it uses the red value for every color in the texture calculation. Not observed ingame, may only be used for internal calculations. 

[Back to Top](#contents)

---

### rendertype_text_intensity_see_through
Functionally the same as `rendertype_text_see_through`, except it uses the red value for every color in the texture calculation. Not observed ingame, may only be used for internal calculations.

[Back to Top](#contents)

---

### rendertype_armor_glint
Unknown.

[Back to Top](#contents)

# Unused 

These are shaders that exist in the files, but are not loaded by the game.

### position_color_normal
Unknown. Doesn’t seem to be loaded by the game, but included on assets.

[Back to Top](#contents)

---
