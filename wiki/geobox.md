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

Currently, the closest obtainable alternative to this engine is [doukutsu-rust](doukutsu-rs).


## Implementation Notes
These are notes that pick apart the geobox demo video in order to undestand how each graphic feature worked.

### Backgrounds:
The engine uses some form of [layers mode](layers-mode) for foreground and background elements, but the background tiles feature some ammount of parallax scrolling.

There can be light elements placed in the scene background that can "shine through" the background tiles and collide with foreground tiles.

### Tile lighting:
There are "bloom" elements on some foreground tiles, where pixels emit light for some radius around the element.

This could potentially also be implemented with some form of "layers" mode, with custom tiletypes that indicate that its contents should be "bloomed"


### Entity lighting
There are 2 types of point raycasting lights: they either don't have collision or follow collision on a per-tile basis, following basic tile shapes and ignoring individual pixels.[D-rs](doukutsu-rs) implements the second type in software in its engine.


There are point lights that ignore all collision. This isn't too groundbreaking; [d-rs](doukutsu-rs) and some ports of [CSE2](cse2) implement this already.










