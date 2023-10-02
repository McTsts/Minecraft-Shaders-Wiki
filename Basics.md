# Basics
## Intro[¹](#footnote)
Vanilla Minecraft has a number of GLSL shaders that can be modified using a resource pack, allowing them to be included in a world or automatically applied when you join a server.  

Shaders are written in OpenGL Shading Language (GLSL), a C-like language with support for floats, vectors, matrices, along with functions, conditions, loops, and many other features you would expect from a programming language.  

## Starting to work with Shaders
### Shader Reload
When using shaders, especially when starting with them, I strongly recommend you use [Suso's Shader Reload mod](https://www.curseforge.com/minecraft/mc-mods/shader-reload).  
While this is a mod, it's a fabric mod and won't modify any part of the game except for the shader reload. Make sure to *not* use other fabric mods that do affect shaders, such as sodium.  

When working with shaders, especially as a beginner, you will often want to reload your resource pack to check whether it works. If there's an error in your code, Minecraft will output it in the game output, and disable the resource pack.  
This is avoided when using the shader reload mod. It allows you to only reload shaders (and not the rest of the resource pack), making it significantly faster. Additionally, when you make a mistake it simply doesn't reload the shaders and outputs the errors in chat. This makes debugging much more comfortable.

### Shader Subfolders
The vanilla shaders are contained in the `assets` of the game, similarly to textures, models and similar. They have a `shader` subfolder in the `minecraft` namespace. A copy of them can also be found in this [repo](https://github.com/misode/mcmeta/tree/assets/assets/minecraft/shaders).  

The `shader` folder contains 4 subfolders:

#### core
Core shaders are responsible for rendering pretty much everything you see in the game. Each core shader renders a specific type of thing, like e.g. gui elements or blocks.  
A list of core shaders and what they render can be found [here](https://github.com/McTsts/Minecraft-Shaders-Wiki/blob/main/Core%20Shader%20List.md).

#### post

#### program

#### include

### Vertex and Fragment Shaders
Core shaders usually consist out of three separate files. A `.fsh` (Fragment Shader), a `.json`, and a `.vsh` (Vertex Shader). The same goes for the post shaders, however they often use a vertex shader shared by several of them.

#### json

#### Vertex Shader


#### Fragment Shader

# Footnote
¹ This was taken from the [guide to vanilla shaders](https://docs.google.com/document/d/15TOAOVLgSNEoHGzpNlkez5cryH3hFF3awXL5Py81EMk/edit)
