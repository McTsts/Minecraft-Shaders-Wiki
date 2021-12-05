# Uniforms
Uniforms are variables passed to core shaders that help determine their behavior.

## GameTime
GameTime increments indefinitely in core shaders. It seems to be synchronized with the server and thus between players. This can be observed by lagging the server. It has been observed that fract(GameTime * 1200) loops around roughly each second.

## Fog
### FogColor
FogColor determines the color of the fog displayed usually at the edges of render distance or under lava. The alpha of FogColor determines the density of the fog.

### FogStart
FogStart determines (presumably in blocks) where the start of the fog begins. It has been observed that the lower FogStart is the more tinted the screen becomes corresponding to FogColor.

### FogEnd
FogEnd determines the end of the fog.

## Position
### for block shaders
Position is a vector representing the xyz coordinates relative to the southwest (needs confirming) chunk corner in world-space.

### for entity shaders
Position is a vector representing the xyz coordinates in camera-space (ergo relative to the camera). In essence Position for entities is the same as Position + ChunkOffset, but in different coordinate systems

## ChunkOffset
A vector representing the xyz coordinates relative the player for each chunk. Thus all blocks in the same chunk have the same ChunkOffset. ChunkOffset is in world-space (needs confirming).

## ScreenSize
A vector representing the dimensions of the screen. If the resolution of Minecraft is 1920x1080, ScreenSize will be vec2(1920.0, 1080.0).

## Light Direction
### Light0_Direction
This uniform seems to be used for shading. It has been observed to always point in the same direction regardless of rotation, however in the inventory it is different.

### Light1_Direction
This uniform seems to be used for shading. It has been observed to always point in the same direction regardless of rotation, however in the Nether and inventory it is different.

## ColorModulator

## ProjMat

## ModelViewMat

## LineWidth
Only available in `rendertype_lines`

## EndPortalLayers
Only available in `rendertype_end_portal` and `rendertype_end_gateway`

## TextureMat
Only available in `rendertype_glint_translucent`, `rendertype_glint_direct`, `rendertype_glint`, `rendertype_entity_glint_direct`, `rendertype_entity_glint`, `rendertype_armor_glint`, `rendertype_armor_entity_glint` and `rendertype_energy_swirl`
