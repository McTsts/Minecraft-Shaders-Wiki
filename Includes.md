# Includes
Includes are special core shaders that contain shared code between different shaders, which all use the .glsl file extension This page will document them and their uses.

## fog
Contains two functions:

`linear_fog()`: Tints a pixel based on its passed-in vertexDistance value.
`linear_fog_fade()`: Oasses out how faded a pixel should be, using similar logic to `linear_fog()`.

## light
Contains two functions:

`minecraft_mix_light()`: Controls the light of entities and items in the inventory. Does not seem to use any lightmap data, in favor of doing a similar calculation to `minecraft_sample_lightmap()` in the entity shader itself.
`minecraft_sample_lightmap()`: Controls the light of blocks. Two values are passed in, the lightMap and the uv. lightMap is a sampler2D that holds all of the color data of the lightmap, and uv contains the light level. The x value of uv is the block light times 16, and the y value is the sky light times 16. GUI elements such as text or items in the inventory, when altered to use the function, seem to use both a block and sky light of 15.

## matrix
Contains one function: `mat2_rotate_z()`,  which creates a 2d rotation matrix.

## projection
Contains one function: `projection_from_position()`, which projects an image from a position. Used in the vertex shader for the end portal image.
