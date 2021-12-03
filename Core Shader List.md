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
  - [UI](#ui)
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
All particles. The alpha value specified in the shader will override the particle’s inbuilt transparency e.g. in the sneeze particle. Others, like the splash particle, don't seem to allow this. More testing needed.

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
When dealing with block shaders which have something to do with `translucent`, `cutout` or `cutout_mipped`, here is a [useful list](List%20of%20Blocks%20Affected.md) by for all blocks of those specific types.

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
Blocks which are translucent and are being moved by a piston. The one below is stained glass.  

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_translucent_moving_block.png" width=400>

[Back to Top](#contents)

---

### tripwire
The middle section(s) of a tripwire.  

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_tripwire.png" width=600>

[Back to Top](#contents)

---

### end_portal (and end_gateway)
The strange image in the end portal. Appears in end gateways, but not in the dimension background.
The shader files are called `end_portal.vsh`/`fsh`/`json`, but `end_gateway.json` also exists but just uses the end_portal vsh/fsh.  

<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_end_portal.png" width=400> <img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_end_gateway.png" width=300>

[Back to Top](#contents)

---

## Entities
WIP

---

## UI
WIP

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
