# Uniforms
Uniforms are variables passed to core shaders that help determine their behavior. They are read-only, and are always the same across every vertex and fragment of the same type.

## GameTime
Gametime is constantly incrementing in core shaders. It's synchronized with the server and thus between players. It is affected by tick lag and not very consistent. It ranges from 0 to 1, repeating every 24000 ticks (20 minutes). This means `fract(GameTime * 1200)` loops around roughly each second.
The game calculates this value as `((float)(time % 24000L) + tickDelta) / 24000.0F`, with `time` being the integer value you can get from `/time query gametime` and `tickDelta` providing subtick timing.

## Fog
### FogColor
FogColor determines the color of the fog displayed usually at the edges of render distance or under lava. The alpha of FogColor determines the density of the fog.

### FogStart
FogStart determines (presumably in blocks) where the start of the fog begins. It has been observed that the lower FogStart is the more tinted the screen becomes corresponding to FogColor.

### FogEnd
FogEnd determines the end of the fog.

## Position
### Block Shaders
Position is a vector representing the xyz coordinates in world-space. Position for blocks is relative to the southwest (needs confirming) chunk corner, and is therefore always between 0 and 16.  
  
You must use Position + ChunkOffset to get the actual vector position in world space.

### Entity Shaders
Position is a vector representing the xyz coordinates in view-space (relative to the camera). Position for entities is the same as Position + ChunkOffset, but pre-multiplied with ModelViewMatrix.

## ChunkOffset
A vector representing the xyz coordinates relative the player for each chunk. All blocks in the same chunk have the same ChunkOffset. ChunkOffset is in world-space (needs confirming).

## ScreenSize
A vector representing the dimensions of the screen. If the resolution of Minecraft is 1920x1080, ScreenSize will be vec2(1920.0, 1080.0).

## Light Direction
### Light0_Direction
This uniform seems to be used for shading. It has been observed to always point in the same direction regardless of rotation, however in the inventory it is different.

### Light1_Direction
This uniform seems to be used for shading. It has been observed to always point in the same direction regardless of rotation, however in the Nether and inventory it is different.

## Matrices

### ModelViewMat
#### Block Shaders
Transforms positions from World Space > View Space.

#### Entity Shaders
This is passed in as an identity matrix, and therefore has no effect on any entity vertex.

### IViewRotMat
Transforms positions from View Space > World Space. This is the inverse to ModelViewMat, but is not passed in as an identity matrix for either shader type. If you would like entity coordinates in world space, you must use IViewRotMat * Position. (Note that a transpose is the same as inverse for a rotation matrix, so you can also use IViewRotMat to go from World Space > View Space by using left-multiplication).

### ProjMat
Transforms positions from View Space > Screen Space.  

<sub>If you're confused about vector spaces, please see: https://learnopengl.com/Getting-started/Coordinate-Systems</sub>

## ColorModulator

## LineWidth
Only available in `rendertype_lines`

## EndPortalLayers
Only available in `rendertype_end_portal` and `rendertype_end_gateway`

## TextureMat
Only available in `rendertype_glint_translucent`, `rendertype_glint_direct`, `rendertype_glint`, `rendertype_entity_glint_direct`, `rendertype_entity_glint`, `rendertype_armor_glint`, `rendertype_armor_entity_glint` and `rendertype_energy_swirl`
