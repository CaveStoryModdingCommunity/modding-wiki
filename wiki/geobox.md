# Geobox

<fieldset>
<legend>Geobox:</legend>
<img src="/wiki/img/engines/geobox-assets/geobox.png">
<table><tbody>

<tr><td>Creator(s):</td><td>Fluffball</td></tr>
<tr><td>Year:</td><td>2015</td></tr>
<tr><td>Platform:</td><td>Windows</td></tr>
<tr><td>Status:</td><td>
<p style="color:#B00000;">Abandoned</p>
</td></tr>
<tr><td>Info:</td><td><a href="https://forum.cavestory.org/threads/geobox-engine-getting-ready-for-public-use.5844/">Original Forum Thread</a></td></tr>

</tbody></table>
</fieldset>


Geobox was an engine written in c++ being developed by user **Fluffball**. 
While a public release was planned, and it was privately distributed to beta testers, an official release was never made and the developer is no longer active within the community.

The geobox engine is notable for its promise of a rich feature-set and beautiful raycast graphics, and is often used as a benchmark to compare the graphical features of other engines to.

[Showcase Video](https://www.youtube.com/watch?v=7SRzfUGuSPU)


## Implementation Notes
Despite the enhanced look, the engine shares nothing in common with the original cave story engine. All assets loaded by this engine are proprietary, which makes it even worse than the [NXEngine](nx-engine) for modding.

### Scripting
Most of the logic for the engine is implemented in Lua, so NPCs, mapdata, and other behaviors can still be edited and altered in the final compiled engine, but no documentation exists for it, so anyone looking to edit this engine will first have to understand how all the calls work.

### Lighting behavior and characterization
Because most of this engine's appeal is in its beautiful lighting, this section attempts to break down some of the lights seen in the demo.

#### Backgrounds:
The engine uses some proprietary form of [layers mode](layers-mode) for foreground and background elements, but the background tiles feature some amount of parallax scrolling.

There can be light elements placed in the scene background that can "shine through" the background tiles and collide with foreground tiles.

#### Tile lighting:
There are "bloom" elements on some foreground tiles, where pixels emit light for some radius around the element.

This could potentially also be implemented with some form of "layers" mode, with custom tiletypes that indicate that its contents should be "bloomed"


#### Entity lighting
There are 2 types of point raycasting lights: they either don't have collision or follow collision on a per-tile basis, following basic tile shapes and ignoring individual pixels. [D-rs](doukutsu-rs) implements the second type in software in its engine.


There are point lights that ignore all collision. This isn't too groundbreaking; [d-rs](doukutsu-rs) and some ports of [CSE2](cse2) implement this already.

---

Currently, the best alternative to this engine is [doukutsu-rust](doukutsu-rs), which is fully playable, stable, and compatible with traditional Cave Story, in addition to having some advanced lighting features.


## Downloads
Geobox was never meant for public release. Even so, the demo copy has been leaked and is available for download on Archive.org:
- [Geobox Engine](https://archive.org/details/GeoboxEngine)











