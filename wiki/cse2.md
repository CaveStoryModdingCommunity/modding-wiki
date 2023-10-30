# Cave Story Engine 2

<fieldset>
<legend>CSE2:</legend>
<img src="/wiki/img/engines/cse2-assets/ICON_MINI.png">
<table><tbody>

<tr><td>Creator(s):</td><td>Clownacy Et al.</td></tr>
<tr><td>Year:</td><td>2019</td></tr>
<tr><td>Platform:</td><td>Mac OS, Linux OS, Windows OS</td></tr>
<tr><td>Status:</td><td>DMCA'd</td></tr>
<tr><td>Info:</td><td><a href="https://forum.cavestory.org/threads/cse2-the-cave-story-decompilation-project.14657/">Original Forum Thread</a></td></tr>
</tbody></table>
</fieldset>

**Cave Story Engine 2**, commonly referred to as **CSE2**, is a fan-made decompilation of the original freeware Cave Story, started in 2019. The port aimed to recreate a byte-for-byte identical copy of the original CS freeware executable from source code. 

CSE2 is popular among modders for its relatively clean code and accurate-to-original behavior. The engine is often either modded directly or used as a reference guide for freeware hacking, as many of the functions are identical to the originals.

## Background
From the original source code's readme, the port's history is as follows:

> When Pixel made Cave Story, he compiled the original Windows EXE with no
optimisations. This left the generated assembly code extremely verbose and easy
to read. It also made the code very decompiler-friendly, since the assembly
could be mapped directly back to the original C++ code.
>
> Technically, this alone made a decompilation feasible, as was the case for [the
Super Mario 64 decompilation project](https://github.com/n64decomp/sm64) -
however, there was more to be found...
>
>In 2007, a Linux port of Cave Story was made by Simon Parzer and Peter Mackay.
Details about it can be found on [Peter's old blog](https://web.archive.org/web/20070911202919/http://aaiiee.wordpress.com:80/).
This port received an update in 2011, including two shiny new executables. What
they didn't realize was that they left huge amounts of debugging information in
these executables, including the names of every C++ source file, as well as the
variables, functions, and structs they contained.
>
>This was a goldmine of information about not just the game's inner-workings, but
its _source code._ This is the same lucky-break [the Diablo decompilation project](https://github.com/diasurgical/devilution)
had. With it, much of the game's code was pre-documented and explained, saving
us the effort of doing it ourselves. In fact, the combination of
easy-to-decompile code, and a near-full set of function/variable names, reduced
much of the decompilation process to mere copy-paste.
>
>To top it all off, some of Cave Story's original source code would eventually
see the light of day:
>
>In early 2018, the Organya music engine was [released on GitHub](https://github.com/shbow/organya)
by an old friend of Pixel's. On top of providing an insight into Pixel's coding
style, this helped with figuring out one of the most complex parts of Cave
Story's codebase.
>
>And... that's it! It's not often that a game this decompilable comes along, so
I'm glad that Cave Story was one of them. [Patching a dusty old executable from 2005 sucks](https://github.com/Clownacy/Cave-Story-Mod-Loader/blob/master/src/mods/graphics_enhancement/widescreen/patch_camera.c).

## Official Branches
When CSE2 was publicly available, these branches existed:

* Accurate: Designed to be as close to the original Cave Story as possible
* Portable: Similar to accurate, but the DirectX backend was removed in favor of others, such as SDL2, OpenGL, 3DS, and others
* Wii: Designed to be built and deployed in the Nintendo Wii
* Enhanced: Contains quality-of-life features like widescreen support, and smooth scrolling
* Enhanced-Lite: Similar to Enhanced, but optimized for modding
* Emscripten: Designed to be compiled with Emscripten and [run in a web browser](https://sonicresearch.org/clownacy/cave.html)

## DMCA Takedown
Unfortunately, Nicalis issued a DMCA takedown of the port when development was nearing completion. Despite this, late copies of the engine are complete, playable from start to finish.

In contrast to the original engine, Nicalis has not gone after mods based on CSE2, and it still remains popular for modding usage.

Compiled mods using CSE2 are freely distributed and can commonly be found in modding databases. However, publicly sharing the **source code** is not advised and strongly discouraged by the modding community.
Because of this, a download link will not be provided, but the code is common enough that a simple internet search will often yield the desired results.



