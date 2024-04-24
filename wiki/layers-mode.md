# Layers Mode


Layers mode refers to a modification of the Cave Story mapdata that allows tiles to be drawn in one of 4 separate layers, as opposed to only one.


It was originally created by user NOXID and supported in their editor, [Booster's lab](boosters-lab).


This allows for more elaborate maps to be created with fewer tiles and less complicated setup.


Another feature of layers mode is the support for extended tilemaps. By default, tilesets can only be 16x16 tiles, totaling 256, or the length of 1 byte. This is because the `.pxm` files store each tile's address using a single byte, so anything larger than that cannot be included in the map.


Layers mode extends the `.pxa` by addressing the tiles with 2 bytes rather than 1, increasing the theoretical tile limit to 65536![^1]


[^1]: Tilesets still have to be 16 tiles wide due to how the game wraps around when addressing tiles, but they can now be much taller.


## Operation

For all practial purposes, anything placed on the `foreground` layer will behave exactly as it does in unmodified cave story. *(Example: a tile placed on the foreground layer with attribute `0x00` will still be drawn behind the player, but one with attribute `0x40` will be drawn in front)*


Collision is only registered with tiles on the `foreground` layer. Tiles with collision attributes on other layers will be treated as if they have nothing. Tiles that are animated such as wind will also be treated as static. Anything that interacts with the player or NPCs should be on the `foreground` layer.

Some versions of the layers mode mod include new commands to supplement vanilla's `<CMP` and `<SMP` for editing the different layers. These commands are as follows:
- `<CMLwwww:xxxx:yyyy:zzzz`, Sets the tile at (xxxx,yyyy) to type zzzz, on layer wwww [0/back, 1/mid, 2/fore, 3/far fore]
- `<SMLwwww:xxxx:yyyy`, Subtracts 1 from tile type at (xxxx,yyyy) on layer wwww [0/back, 1/mid, 2/fore, 3/far fore]


## Engine Support


This mod is readily available for Freeware as a [dll patch](advanced-freeware-hacking) created by user **Periwinkle** that can be downloaded here: [(download)](files/layers.zip)[^2]


[^2]:To improve performance, this hack doesn't draw tiles in slot 0 (top left corner), since this tile is usually left transparent anyway. Use this tile for "air" only.


CSE2 and d-rs don't support layers mode out-of-the-box, but their open-source nature and the simple implementation of the mode itself make it easy to add it.


User **JakeV** posted a tutorial on how to [implement layers in CSE2](https://gitlab.com/-/snippets/2177785) as well as enable [extended tilemaps](https://gitlab.com/-/snippets/2179513) (described above).

User **Dr_Glaucous** has created a fork that add layers support to d-rs. [The fork's source code can be found on github](https://github.com/DrGlaucous/doukutsu-rs-nm/tree/master) and used as a substitute template until more official versions of this are developed.


Although some editors can convert normal-mode tiles to layers-mode tiles on the fly (Booster's lab is one such example), not all versions of layers mode may be backwards compatible with the original format. Fortunately, a pre-converted version of the vanilla assets can be downloaded [here](files/Stage.zip).
## Editor Support


Most modern [Cave Story Editors](cavestory-editors) support layers.


Currently, editors known to support layers are:
- [Booster's Lab](boosters-lab)
- [SDE](sky-dragon-editor)
- [TKT](the-kings-table)






