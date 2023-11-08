# doukutsu-rs




<fieldset>
<legend>d-rs:</legend>
<img src="/wiki/img/engines/d-rs-assets/nx_icon.png">
<table><tbody>

<tr><td>Creator(s):</td><td>Alula Et al.</td></tr>
<tr><td>Year:</td><td>2021</td></tr>
<tr><td>Platform:</td><td>Mac, Linux, Windows, Android</td></tr>
<tr><td>Status:</td><td>
<p style="color:#00B000;">Active development</p>
</td></tr>
<tr><td>Website:</td><td><a href="https://doukutsu-rs.github.io/">Official website</a></td></tr>

</tbody></table>
</fieldset>



**Doukutsu-rs**, *(commonly referred to as **d-rs**)*, is an open-source recreation of Cave Story written in the Rust programming language.


The earliest mention of this engine was on August 5, 2020 in the CSMC discord server. On [August 18, 2020](https://github.com/doukutsu-rs/doukutsu-rs/commit/b89d54251f42f4d8b247bbc6ebac2c9efe78ac74), the first commit was uploaded to Github.


Since this engine is still in active development, there is still no "Official" release of the engine, though nightly builds are available with the latest changes, auto-built with Appveyor and available on the official website.


## Behavior


d-rs is designed to be a drop-in replacement for all existing versions of cave story, including:
* [Cave Story Freeware](freeware)
* Cave Story +
* Cave Story Switch
* [CSE2](cse2)
* [NXEngine](nx-engine)




D-rs will alter its behavior to closely mimic these engines, depending on which one it is supposed to replace. For example, it will adopt fancy water when coupled with the Nintendo Switch port, or animated facepics with the NXEngine files. The engine also supports 2 player multiplayer analogous to CS-Switch.

D-rs also has support for pxpack mapfiles, similar to those used in Pixel's newer games like Kero Blaster. Pxpack uses 8x8 tiles and has multiple layers.


### Lighting
D-rs also has a custom lighting engine that implements basic raycasting and colored point lights. This can be enabled or disabled during gameplay, but is overridden by some of the other ports' files (an example of this being CS-Switch).




### Data
To avoid legal issues, d-rs does not ship with any cave story assets, and must be placed in a pre-existing install folder. If placed with vanilla Cave Story, it will automatically extract all embedded assets into the `./data` subdirectory.




The engine supports the following stage formats in priority order[^1]:
1. stage.tbl
2. stage.sect[^2]
3. mrmap.bin
4. stage.dat


[^1]: *Stage tables with higher priority will be loaded in lieu of lower ones, even if multiple share the same directory.*
[^2]: *This is a custom map format created by d-rs when it extracts freeware assets. It represents a raw chunk of memory taken from the executable where the vanilla maps are stored.*




## Debugger Functions
This engine has a built-in debugger. Debug functions can be accessed by pressing the following function keys:




* **F3**: Godmode
* **F4**: Infinite Booster
* **F5**: Toggle subpixel scrolling
* **F6**: Toggle motion interpolation
* **F8**: Reduce game speed by 10%
* **F9**: Increase game speed by 10%
* **F10**: Show NPC debug points, Red dot on NPC's origin, white dots on currently colliding tiles
* **F11**: Show Average FPS and TPS
* **F12**: Show debug window
* **`**: Toggle Command line
* **Ctrl + F3**: Reload Sound Manager
* **Ctrl + S**: Quick Save




The F12 debug window contains more, in depth functions, such as arbitrary TSC execution, map jumping, noclip, and others.




## Scripting
D-rs has comprehensive support for lua scripting, allowing for some engine or behavior modifications without needing to recompile the source code. [Documentation can be found here](https://doukutsu-rs.gitbook.io/docs/modding-guide/lua-api).




## Mascot


<img src="/wiki/img/engines/d-rs-assets/sue.bmp">


Since conception, d-rs has used Sue in some form as its mascot, per developer preference. As the port aged into a complete game, a custom version of Sue was made to go along with it. The mascot was tinted blue and given various crab-like features in order to relate back to Rust's mainstream mascot, [Ferris](https://rustacean.net/).


In order to celebrate the engine's rust heritage, every year on July 7, all in-game instances of Sue will become "crabby", taking on the color and crab features of the engine's mascot. This feature can also be enabled manually using the "more rust" option in the debug menu.


