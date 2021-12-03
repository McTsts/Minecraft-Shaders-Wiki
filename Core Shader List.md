# Contents
- [Non-Rendertype](#non-rendertype)
  - [blit_screen](#blit_screen)
  - [particle](#particle)
  - [position](#position)
  - [position_color](#position_color)
  - [position_tex](#position_tex)
  - [position_tex_color_normal](#position_tex_color_normal)
  - [position_color_tex](#position_color_tex)
  - [position_tex_color](#position_tex_color)
- [Rendertype](#rendertype)
  - [Blocks](#blocks)
    - [solid](#solid)
    - [cutout](#cutout)
    - [cutout_mipped](#cutout_mipped)
    - [translucent](#translucent)
    - [translucent_moving_block](#translucent_moving_block)
    - [tripwire](#tripwire)
    - [end_portal](#end_portal-and-end_gateway)
    - [end_gateway](#end_portal-and-end_gateway)
  - [Entities](#entities)
  - [UI](#ui)
  - [Other](#other)
    - [lines](#lines)
    - [crumbling](#crumbling)
    - [beacon_beam](#beacon_beam)

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
The black transparent background on UI elements such as the chat field or the pause menu, the red Mojang loading background, highlighting over item slots, hover text backgrounds, durability bars, as well as the transparent lower hemisphere overlay on the sky approximately between times 11315 to 14150 (sunset) and 21830 to 24670 (sunrise). Also affects the black bars when 

[Back to Top](#contents)

---

### position_tex
sun, moon, worldborder, gui texture, hotbar texture, powder snow overlay, vignette, pumpkin scoped in with a spyglass. Also affects the chunk border display. For UI elements Position is the screen size divided by the gui scale. E.g. 1920x1080 with GUI scale 3 means Position for x will be [0,640] and for y [0,360].  
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

---

# Rendertype
These are shaders which are targeted towards a specific element of the display.
**For each shader name here, assume that it is prefixed with `rendertype_`.**

## Blocks
When dealing with block shaders which have something to do with `translucent`, `cutout` or `cutout_mipped`, here is a [useful list](https://gist.github.com/boq/4514320b590de1fbe84349d23b542b28) by boq for all blocks of those specific types.

[Back to Top](#contents)


### solid
All solid blocks, lava, and when in fast mode, leaves. Also affects non-translucent falling blocks  
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_solid.png" width=400>
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_solid2.png" width=400>

[Back to Top](#contents)

---

### cutout
All non-cube-hitbox blocks: saplings, glass, rails, cobwebs, grass, fern, dead bushes, seagrass, flowers, mushrooms, torches, fire, redstone, repeater, comparator, crops, crop stems, cocoa, cactus, sugarcane, kelp, vines (+ glow lichen), lily pad, sea pickles, bamboo, berry bushes, nether sprouts, nether fungus, nether roots, chorus plants, coral, spore blossoms, azalea, moss carpet, dripleaf, hanging roots, sculk sensor, flower pots, doors, trapdoors, ladders, brewing stands, beacons, spawners, conduits, scaffolding, stonecutters, lanterns, campfires, pointed dripstone, amethysts, end rods, lightning rods.  
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_cutout.png" width=600>

[Back to Top](#contents)

---

### cutout_mipped
Some blocks: grass blocks, iron bars, glass panes, tripwire hooks, hoppers, chains (leaves when using fancy or fabulous graphics)  
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_cutout_mipped.png" width=600>

[Back to Top](#contents)

---

### translucent
Translucent blocks: water (still and flowing), ice, nether portal, stained and tinted glass (not normal glass), slime and honey, bubbles. I have strong suspicion to believe that Sampler2 is the tint overlay used with biomes, since vertexColor tints the water.  
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_translucent.png" width=400>
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_translucent2.png" width=400>

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
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_end_portal.png" width=400>
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_end_gateway.png" width=300>

[Back to Top](#contents)

## Entities
WIP

## UI
WIP

## Other
These are shaders that render things that aren't clearly either a block, an entity or a ui element.

### lines
The outline when hovering over a block, as well as the debug crosshair and hitboxes.
And structure blocks preview. Also fishing lines.  
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_lines.png" width=300>
<img src="https://github.com/McTsts/shaders/blob/main/images/rendertype_lines2.png" width=400>

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

---
