## Non-Rendertype
There are several shaders which are not prefixed with rendertype_. These seem to be for more general targets, such as the sky or all particles. 

### blit_screen 
Blit copies one buffer to another, however this cannot be overridden in a resource pack. 

### particle
All particles. The alpha value specified in the shader will override the particle’s inbuilt transparency e.g. in the sneeze particle. Others, like the splash particle, don't seem to allow this. More testing needed.

### position
The colour of the sky. Also affects text highlighting. 

### position_color
The black transparent background on UI elements such as the chat field or the pause menu, the red Mojang loading background, highlighting over item slots, hover text backgrounds, durability bars, as well as the transparent lower hemisphere overlay on the sky approximately between times 11315 to 14150 (sunset) and 21830 to 24670 (sunrise). Also affects the black bars when 

### position_tex
sun, moon, worldborder, gui texture, hotbar texture, powder snow overlay, vignette, pumpkin scoped in with a spyglass. Also affects the chunk border display. For UI elements Position is the screen size divided by the gui scale. E.g. 1920x1080 with GUI scale 3 means Position for x will be [0,640] and for y [0,360].  
<img src="https://github.com/McTsts/shaders/blob/main/images/position_tex.png" width=600>

### position_tex
sun, moon, worldborder, gui texture, hotbar texture, powder snow overlay, vignette, pumpkin blur and crosshair, skin player in tab, mojang logo


### position_tex_color_normal 
Clouds.

### position_color_tex 
Fire overlay when the player is burning.

### position_tex_color
The End sky, main menu panorama, and menu backgrounds.

