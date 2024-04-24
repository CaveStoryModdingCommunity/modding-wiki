# BKG Hack<!-- omit in toc -->

The BKG hack modularizes the background behaviors, allowing them to be highly customized and changed at runtime.


Unlike with [layers mode](layers-mode), there is no real set-in-stone implementation for the BKG hack; each one will funtion slightly differently, but they all have simmilar traits.

For instance, all BKG implementations support multiple layers, where each layer has a set of sub-settings that control how it moves, behaves, or animates, but the degrees of freedom that each layer can be animated varies from port to port.


The list of ports for the BKG hack are as follows:
- [BLink Layer Hack](#blink-layer-hack)
- [AVA](#ava)
- [JakeV Modengine (tscextended)](#jakev-modengine-tscextended)
- [d-rs mod-features](#d-rs-mod-features)




## BLink Layer Hack

[Original forum thread here](https://forum.cavestory.org/threads/blinks-multi-layered-background-hack.14250/)

This version is exclusively TSC dependant and uses no external config files. It is a standalone hack, so other dlls and patches need to be added with care.

The new TSC commands and arguments are as follows:
```
BacKGround
<BKGAAAA:BBBB:CCCC:DDDD:EEEE:FFFF:GGGG:HHHH:IIII:JJJJ:KKKK:LLLL:MMMM:NNNN:OOOO:PPPP
A = Slot number         //the draw order
B = L_framerect         //how far from the left side of the bitmap the render area is
C = U_framerect         //how far from the top of the bitmap the render area is
D = X size              //how wide the render are is
E = Y size              //how high the render are is
F = X repeat            //how many times the bitmap repeats horizontally
G = Y repeat            //how many times the bitmap repeats vertically
H = X distance          //the horizontal distance between each rendered sprite
I = Y distance          //the vertical distance between each rendered sprite
J = Scroll type         //how the background scrolls (see the list below)
K = Scroll speed X      //How fast the background scrolls (9 is how fast it moves under the "move slowly" setting in vanilla)
L = Scroll speed Y      //How fast the background scrolls (9 is how fast it moves under the "move slowly" setting in vanilla)
M = Animation sprites   // how many sprites the rendered area cycles through
N = Animation speed     // how many frames it takes for the rendered area to change
O = X_offset            // how far from the horizontal absolute corner of the render area the sprite starts rendering
P = Y_offset            // how far from the vertical absolute corner of the render area the sprite starts rendering
```
Argument J (scroll type) works like `<EQ+` in stock Cave Story, and is set via bitfield.
```
Scroll type list: (in binary)
0 = fixed
1 = horizontal move with char/camera
2 = vertical move with char/camera
4 = horizontal move with timer
8 = vertical move with timer
16 = scroll with char's direction instead of away
```
These can be added to each other, so a value of 9 would make it scroll horizontal with the character/camera, and vertical with a timer.

`<BKNXXXX` Determines how many slots the custom BK has. A value of 0000 makes it render vanilla backgrounds.

## AVA

[More info about AVA's general featureset here.](ava)

The AVA implementation was based on an earlier implementation by Bionicobot for CSE2[^1], and is essentially unchanged beyond the freeware-related hooks. The configuration files are a plaintext list of values, essentially replicating the TSC command in the BLink Layer hack, but making it easier to read and edit.

[^1]: Now unobtanium due to the DMCA, but since AVA is basically a verbaitm copy, it would be trivial to port it back to CSE2.

Bionicobot wrote comprehensive documentation on how their BKG mod works, and outlined its featues in the following text documents, which also apply to AVA:
- [Argument Explanation](files/ava_bkg/CustomTSC_BKG_Explanation.txt)
- [Example config file](files/ava_bkg/CustomTSC_BKG_Example.txt)
- [Example format list](files/ava_bkg/CustomTSC_BKG_Format.txt)

Config files themselves are loaded with a much shorter command than with the BLink version:
`<BKGconfigname_here$`, where `configname_here` is the name of the config file in the `./data/bkg` folder. The `$` sign denotes the end of the argument.

There are also several other commands that control how the backgrounds behave on the fly:
- `<BKDwwww` - **Background Disable:** disables background with order wwww
- `<BKEwwww` - **Background Enable:** enables background with order wwww
- `<BKGfilename$` - **Background:** see the explaination above
- `<BKPwwww:xxxx:yyyy` - **Background Parameter** Set background parameter X for layer W to value Y.
- `<BKR` - **Background Reset:** Disables the custom backgrounds until they are loaded again with `<BKG` (this reset also happens with map transitions)


## JakeV Modengine (tscextended)

More info about this mod [can be found here.](https://forum.cavestory.org/threads/mod-engine-tsc-extended.15369/)[^2]

[^2]: Note: since this is CSE2, the download link has since been removed, but it still exsists on archive.org



This BKG implementation is part of a larger toolset for modding CSE2, but lacks much of the versitlity offered by the other BKG implementations.

It uses a stack-based method for implementing each layer, where a call to `<BKG` will push a new layer to the background "stack" with the parameters provided. This command only takes 4 parameters instead of the 8+ for the other versions.


## d-rs mod-features

This version of BKG was based on the one in AVA, and by extension, the one by Bionicobot.
The primary difference here is that it uses .json files to store BKG configs instead of plaintext files.
This makes them *even* easier to view and edit without a refrence table.
Additionally, this fixes several bugs that were discovered with the older implementations.

For the complete documentation, please see the [listing on the source page](https://github.com/DrGlaucous/doukutsu-rs-nm/blob/mod-features/Documentation.md).










