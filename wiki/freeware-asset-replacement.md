# Game asset replacement

By default, quite a few of the assets in Cave Story Freeware can be replaced by custom ones without the need for advanced knowledge of executable structure or programming. This is one of the most basic ways to modify the game and get familiar with its structure before [delving into more involved modding techniques](advanced-freeware-hacking).

The following assets can be replaced by editing or changing assets in the `data` folder:
- Maps *(`.pxm`, PiXel Map)*
- Map events *(`.tsc`, Text SCript)*
- Map tileset attributes *(`.pxa`, PiXel Attribute)*
- In-level NPCs *(`.pxe`, PiXel Entities)*
- Character sprites and map tiles*(`.pbm`, Pixel BitMap, see below on how to edit these)*
- NPC attributes (such as damage values and hitbox sizes, but *not* behavior) (`npc.tbl`)
- Music *(Cave Story + only, for freeware, see below)*

## Bitmap replacement

Bitmaps used by Cave Story Freeware have been slightly tweaked by Pixel in attempt to block asset modification or stealing *(oops)*.

The bitmaps themselves are fairly basic, with a bit depth of 4 and the file extension `pbm` rather than `bmp`. They can be opened in any image editor such as [Paint.net](https://www.getpaint.net/) or [Grafx2](http://grafx2.chez.com/) and edited like normal.

What makes them unique is that appended to the end of every image file is the string `(C)Pixel`. The stock freeware game will check for this string each time is tries to load an image, and will crash if it does not detect it. *(Saving or editing the bitmap in an image editor will remove this string!)*

***Note: The methods below, although informative, are largely deprecated in favor of using a map editor like [Booster's Lab](boosters-lab), [SDE](sky-dragon-editor), or [TKT](the-kings-table), all of which do this modification automatically.***

There are several ways to sidestep this roadblock. For simple file replacements, a hex editor such as [HxD](https://mh-nexus.de/en/hxd/) can be used to add back the `(C)Pixel` after the image has been edited.

If that is considered too much hassle or many images need to be replaced, the Hex editor can be used to replace all instances of `.pbm` with `.bmp` inside the exe, and remove the `(C)Pixel` string as well, allowing the Freeware exe to load in stock bmps.

There are two instances of `.pbm` in the exe, one at offset `8C286` and the other at `8C30A`. Replacing both of these with `.bmp` will have the game load bitmaps instead of pbms.

There is one instance of `(C)Pixel` in the executable located at offset `8C4D8`. Replacing this with null characters (hex code `00`) will remove the need for `(C)Pixel` at the end of the bitmaps.


## Map Editing

Maps aren't *technically* encrypted, but it makes no sense to not use a [map editor](cavestory-editors), which handles all of the peculiarities of modifying the pxe, pxm, and pxa files in a very user-friendly way. Additionally, if more maps are to be added or removed, this requires *executable modification*, but once again, the map editors handle all of this for you.

## TSC Editing

Unlike maps or even bitmaps, TSC is actually encrypted to an extent, but once again, thanks to the work of a diligent modding community, several different [map editors](cavestory-editors) exist that take care of decryption, re-encryption, and format highlighting for TSC.

*Note: Some releases of Cave Story such as CS Switch do **not** encrypt the TSC files, meaning that they can be edited with a plaintext editor.*

## Credit Images and ORG replacement

Credit images and ORG files are embedded into the EXE rather than placed into the external `data` folder. To replace these is still pretty straightforward though. The program [Resource Hacker](https://www.angusj.com/resourcehacker/) can be used to view and dump/repack these files. Be sure the name of the replaced file matches the name of the original in order for it to be accessed ingame.


## Sound FX Replacement

Sound Effects are synthesized in real time from PixTone files embedded in the executable. These *cannot* be replaced with Resource Hacker, but there is a tool that allows them to be extracted, edited, and re-pushed into the executable. [SeaTone](https://www.cavestory.org/downloads/tone_pusher_rev1.zip) is an all-in-one suite of tools that allow the user to create new tones to be used in Cave Story.

Pixel himself also released a PixTone editor, aptly named [PixTone](https://www.vector.co.jp/download/file/win95/art/fh351456.html), but many find SeaTone to be more polished and user-friendly.


















