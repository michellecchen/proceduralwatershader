# Procedural water shader: Documentation

![enter image description here](/gifs/recording-cubeswithBG.gif)

A non-photorealistic procedural water shader with several customization features.

Created in Unity 2021.3.18f1 using Shader Graph & modular subgraphs.

## Specs

- Non-photorealistic, stylized
- Renders realtime animations that visually simulate fluid dynamics
- Offers robust customization options; adjustable for multiple combinations of different NPR styles + environments
- Voxel-compatible; works independently of UV maps

## Features

 - **Depth & color**: Renders a range of colors across varying depths of water.
 - **Refraction**: Renders an animated, realtime refraction lighting effect over the surface of the water.
 - **Foam**: Renders an animated, realtime foam effect wherever objects intersect with the water.
 - **Waves**: Renders animated, realtime, 3D waves *(note: this feature is currently only compatible for application to flat surfaces, i.e. planes)*.

## Customization options

All the above features have a set of customization options that are accessible via the Inspector. These parameters can be tweaked to your liking — they're meant to give users a lot of control over stylization and enable multiple rapid iterations across visual styles.

- **Depth & color**: Customizable depth (`WaterDepth`) and customizable color at different depths of water, i.e. shallow and deep (`ShallowColor`, `DeepColor`).
- **Refraction**: Customizable speed, scale, and strength of refraction effect on water's surface (`RefractionSpeed`, `RefractionScale`, `RefractionStrength`).
- **Foam**: Customizable speed, scale, strength, cutoff, and color of foam effect at object-surface intersections (`FoamSpeed`, `FoamScale`, `FoamStrength`, `FoamCutoff`, `FoamColor`).
- **Waves**: Can be toggled on/off (`DisplayWaves`); customizable speed and scale (`WaveSpeed`, `WaveScale`).

An example of what this looks like in the Inspector:

![enter image description here](https://i.imgur.com/pynfxKm.png)

## Implementation details

I created this procedural water shader through one primary Shader Graph (`Water_ShaderGraph.shadergraph`) & a couple modular Sub Graphs (`DepthFade_SubGraph.shadersubgraph`, `Movement_SubGraph.shadersubgraph`).

I list the features below in the order they were implemented. For each, I include a **"validation test"** — a screenshot from the editor, demonstrating what the shader looked like in a test scene at that development stage — as well as **screenshots of the relevant shader nodes**.

### Depth and color

**Validation test**

![enter image description here](/gifs/colordepth.gif)

*A very rudimentary beginning, but the gradient below the water's surface lets us know that we're on the right track.*

![enter image description here](/gifs/colordepth_customization.gif)

*Demonstrating customization of water color at various depths*

**Shader progress**

![Depth subgraph](https://i.imgur.com/WyPXp2r.png)

*Depth subgraph*

![enter image description here](https://i.imgur.com/24OsVFw.png)

*Main shader: Depth & color*

### Refraction

**Validation test**

![enter image description here](/gifs/refraction.gif)

*Demonstrating refraction effect as well as its customization (through strength, scale, speed adjustments)*

**Shader progress**

![enter image description here](https://i.imgur.com/DchwKbk.png)

*Main shader: Refraction*

![enter image description here](https://i.imgur.com/hagplOd.png)

*Overall shader (with newly implemented refraction)*

![enter image description here](https://i.imgur.com/DSh8r92.png)

*Movement subgraph (for simulating a movement effect in the water)*

### Foam

**Validation test**

![enter image description here](/gifs/trimmed-foam-v2.gif)

*Foam appearance*

![enter image description here](/gifs/foam-custom1.gif)

*Foam customization (pt. 1): Strength & cutoff*

![enter image description here](/gifs/foam-custom2.gif)

*Foam customization (pt. 2): Speed, scale, & color*

**Shader progress**

![enter image description here](https://i.imgur.com/DmjpsFU.png)

*Main shader: Foam*

![enter image description here](https://i.imgur.com/3cQWUU4.png)

*Overall shader (with newly implemented foam)*

### Waves

**Validation test**

![enter image description here](/gifs/waves.gif)

**Shader progress**

![enter image description here](https://i.imgur.com/0eqTFAt.png)
*Main shader: Waves*

## Final outcome: Shader graph & renders

**Renders**

![enter image description here](/gifs/recording-cubeswithBG.gif)

![enter image description here](/gifs/watercubes_1.gif)

![enter image description here](/gifs/watercubes_2.gif)

**Completed shader graph**

![enter image description here](https://s12.gifyu.com/images/ScHiq.gif)
*The main water shader with fully implemented depth/color, refraction, foam, and wave features. Each feature corresponds to one node grouping (titled accordingly).*

## Outsourced assets

Credits to **BOXOPHOBIC** for the skybox used in the final render (from the [**Skybox Cubemap Extended Shader**](https://assetstore.unity.com/packages/vfx/shaders/free-skybox-extended-shader-107400) package on the Unity Asset Store).
