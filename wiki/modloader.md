# Modloader

Links:
[Original forum post](https://forum.cavestory.org/threads/dll-mod-loader-extra-music-formats-mod.13879/), [Github release](https://github.com/Clownacy/Cave-Story-Mod-Loader/releases/tag/v1.5.2.1)

**A comprehensive list of mods for Modloader [can be found here.](dll-list)**

The DLL modloader was developed by Clownacy and initially released in 2017. It supplements [Freeware](freeware) Cave Story by allowing the user to inject their own code into the executable at runtime. The original mod showcased some quality-of-life enhancements like 60 FPS mode, .ogg music, and the 3DS styled HUD.


It can best be described as a split between complete engine modding with something like [CSE2](cse2) or [d-rs](doukutsu-rs) and straight vanilla modding using an assembler and x86 instructions. Developers write their program in their preferred language (typically c/c++) and tell their code what address in the original EXE to inject the mod. The result provides high-level expandability to Freeware.



______
***The following describes the demo mod that comes with the modloader, downloadable at either link at the top of the page.***


Clownacy's .dll Mod Loader demo will allow you to use and toggle .OGG audio files for your in-game music, provide Widescreen Support, enable Debug Save Mode, Change control methods to WASD, and Simplify Gamepad Controls.

This external mod was made by Clownacy.



## Required Tools
* Notepad

## Summary

This mod replaces the Org music with Ogg music, with drag-and-drop support for the WiiWare and Cave Story 3D soundtrack files from Cave Story+.

The mod supports two formats of Ogg music:

- The first is the version used by the WiiWare soundtrack, where each song gets one Ogg file that repeats in its entirety.
- The second is the format used by the Cave Story 3D soundtrack - each song gets two files: 'songname_intro.ogg' and 'songname_loop.ogg'. As you can imagine, when a song starts playing, it plays the intro file first, then when it ends, it continues onto the loop file. When the loop file ends, it loops back to itself, meaning the intro never gets played again. This allows for more complex music.

Ogg music in the WiiWare format should go in a folder called 'Ogg', which you create in the 'data' folder. Music in the second format should go in an 'Ogg11' folder. Like I said, you can copy the soundtrack files from Cave Story+'s 'data/base/Ogg(11)' folders into your new folders, and they'll play in your game!


***Note:***

The mod relies on SDL2 and its SDL_mixer extension for music playback, which in turn uses libogg, libvorbisfile, and libvorbis. With slight modifications, it should be possible to add support for the other formats SDL_mixer supports, like MP3, FLAC, and MIDI.

## Installation

The Ogg mod comes with the DLL Mod Loader. See its section of the post below.

Remember, unless you're making your own soundtrack, you'll need to provide your own copy of the WiiWare/Cave Story 3D soundtracks to have them play in this mod. Cave Story+ is a legitimate way of obtaining them. From it, you can extract the 'Ogg' and 'Ogg11' folders from the 'data/Base' folder, and paste them into your Freeware Cave Story's 'data' folder.

## The DLL Mod Loader

This is a loader for mods stored in DLL files.

Usage Mods are installed in a folder called `mods` in your Cave Story directory. Inside that same folder is a `mods.txt` file, which controls which mods will be loaded.

Each line in mods.txt contains the name of the mod you want to load. Here's a sample layout:

```
60fps
ogg_music
wasd_input
```

If there's an error in your `mods.txt`, a file inside the mods folder called `error.txt` will be made when you try to run the game, telling you what went wrong.

Inside the mods folder, each mod has its own folder, inside which the mod's DLL file and settings file are stored, leading to a file layout like this:

```
Cave Story folder
  Doukutsu.exe
 --mods folder
     mod_loader.dll
    mods.txt
 ----ogg_music folder
      ogg_music.dll
      settings.txt
      playlist.txt
----60fps folder
       60fps.dll
       settings.txt
```

## Installing the Mod Loader

Download the mod from the Github source. Inside the zip file is a folder called 'mods'. Extract that folder to your Cave Story directory (so mods is in the same folder as Doukutsu.exe).

Now that we have the files set up, let's apply the EXE to the patcher to use them!

Just take the Doukutsu.exe and drag and drop it into the patcher.

Here's a blurb from Clownacy about the Patcher:

>The EXE patcher just requires you drag-and-drop an EXE onto it, and it'll spit out a patched file with the name 'Doukutsu_mod_loader.exe'. It performs some tests to check if the file is already patched, or if it's been modified in a way that may make it incompatible.

And you're done! Be sure to configure your mods.txt to your liking!

The Mods (And what they exactly do)

## Included with the Mod Loader:

### ogg_music

This mod has a settings file, with the following options:

playlist - Defines the filename of the playlist file

The playlist file is in a special format: each line represents a song, corresponding to the game's internal music order. Each line consists of a comma-separated list, with the first thing in the list being the path to the Ogg file, and every thing after that being a property of said Ogg file. The following properties are currently available:

loop - When the Ogg file ends, it begins again

split - Each song is represented by two Ogg files, in the same way as the Remastered music in Cave Story+ (more info in the first half of the post)

### wasd_input

A reimplementation of the WASD mod. This one allows the use of a greater range of keyboard keys than the old EXE mod.

#### Controls:

```
W - Up
A - Left
S - Down
D - Right

O - Shoot
P - Jump
[ - Inventory
] - Map
9 - Previous weapon
0 - Next weapon
```

### 60fps

A simple patch that makes the game run at 60FPS instead of 50FPS, making it play like the Nicalis releases (and presumably the prototype versions of the game).

***NOTE - You can apply the 60fps hack in the "Hackinator" located inside of Booster's Lab as well. To avoid any potential conflict, turn this mod off if you apply the 60fps hack in the Hackinator.***

### sdl_controller_input

A re-implementation of the controller system, aimed at XInput devices. This allows control of Quote using the D-Pad.

Gamepads must be enabled in DoConfig for this to work. In addition, enabling gamepads does not disable keyboard controls.

#### Controls:
```
D-Pad/Left Stick - Movement
A / Cross - Jump
X / Square - Shoot
Y / Triangle - Jump

B / Circle - Shoot
LB / LT / L1 / L2 - Previous weapon
RB / RT / R1 / R2 - Next weapon
Start - Inventory
Back / Select - Map
```

### ikachan_cursor

Restores the unused Ikachan cursor.

### debug_save

Restores the Debug Save menu.

### disable_image_protection

Disables the '(C)Pixel' requirement in .pbm (bmp) files.

***NOTE - Booster's Lab already does this for you when you load a fresh copy of Cave Story in the editor.***

### 3ds_hud

An attempt at recreating the 3DS eShop port's HUD, which is less screen-invasive

### graphics_enhancement

Adds widescreen support, higher sprite sheet resolutions, and larger window sizes. More information can be found in its thread here.

## Technicals

What the Mod Loader does is hijack the game during startup (in WinMain), and load a DLL. This DLL then executes all DLLs listed in mods.txt, which patch the Cave Story EXE in memory.

If the loader fails to initialise, it simply gives up and lets Cave Story run as vanilla without crashing.

The loader was designed for Version 1.0.0.6 of Cave Story. This includes the original Japanese version, the English-translated version, and the WASD modification. I cannot guarantee its compatibility with mods and older versions of the game.

## Additional Notes for using the ogg_music mod
As of now, the "ogg_music" mod is not compatible with TSC+.
If there are no available .oggs to play to the corresponding <CMU that is elicited, then Cave Story will just play it's default .ORG tunes.

.ogg files correspond to the playlist settings located in the "ogg_music" folder. If you just want to use a single looping .ogg for your mod, set the playlist function to "playlist_wiiware" in the settings.txt file.
To properly use .oggs for the WiiWare playlist, make a folder called "Ogg" in your "Data" folder in the Cave Story directory, then place your desired .oggs in it. Make sure your .oggs are named to the corresponding names in the playlist, as such:
```
data/Ogg/WANPAKU, loop
data/Ogg/ANZEN, loop
data/Ogg/GAMEOVER
data/Ogg/GRAVITY, loop
data/Ogg/WEED, loop
data/Ogg/MDOWN2, loop
data/Ogg/FIREEYE, loop
data/Ogg/VIVI, loop
data/Ogg/MURA, loop
data/Ogg/FANFALE1
data/Ogg/GINSUKE, loop
data/Ogg/CEMETERY, loop
data/Ogg/PLANT, loop
data/Ogg/KODOU, loop
data/Ogg/FANFALE3
data/Ogg/FANFALE2
data/Ogg/DR, loop
data/Ogg/ESCAPE, loop
data/Ogg/JENKA, loop
data/Ogg/MAZE, loop
data/Ogg/ACCESS, loop
data/Ogg/IRONH, loop
data/Ogg/GRAND, loop
data/Ogg/Curly, loop
data/Ogg/OSIDE, loop
data/Ogg/REQUIEM, loop
data/Ogg/WANPAK2, loop
data/Ogg/QUIET, loop
data/Ogg/LASTCAVE, loop
data/Ogg/BALCONY, loop
data/Ogg/LASTBTL, loop
data/Ogg/LASTBT3, loop
data/Ogg/ENDING, loop
data/Ogg/ZONBIE, loop
data/Ogg/BDOWN, loop
data/Ogg/HELL, loop
data/Ogg/JENKA2, loop
data/Ogg/MARINE, loop
data/Ogg/BALLOS, loop
data/Ogg/TOROKO
data/Ogg/WHITE, loop
```
To properly use .oggs for the 3ds playlist, make a folder called "Ogg11" in your "Data" folder in the Cave Story directory, then place your desired .ogg pairs in it. Make sure your .oggs are named to the corresponding names in the playlist, as such:

```
data/Ogg11/WANPAKU, loop, split
data/Ogg11/ANZEN, loop, split
data/Ogg11/GAMEOVER, split
data/Ogg11/GRAVITY, loop, split
data/Ogg11/WEED, loop, split
data/Ogg11/MDOWN2, loop, split
data/Ogg11/FIREEYE, loop, split
data/Ogg11/VIVI, loop, split
data/Ogg11/MURA, loop, split
data/Ogg11/FANFALE1, split
data/Ogg11/GINSUKE, loop, split
data/Ogg11/CEMETERY, loop, split
data/Ogg11/PLANT, loop, split
data/Ogg11/KODOU, loop, split
data/Ogg11/FANFALE3, split
data/Ogg11/FANFALE2, split
data/Ogg11/DR, loop, split
data/Ogg11/ESCAPE, loop, split
data/Ogg11/JENKA, loop, split
data/Ogg11/MAZE, loop, split
data/Ogg11/ACCESS, loop, split
data/Ogg11/IRONH, loop, split
data/Ogg11/GRAND, loop, split
data/Ogg11/Curly, loop, split
data/Ogg11/OSIDE, loop, split
data/Ogg11/REQUIEM, loop, split
data/Ogg11/WANPAK2, loop, split
data/Ogg11/QUIET, loop, split
data/Ogg11/LASTCAVE, loop, split
data/Ogg11/BALCONY, loop, split
data/Ogg11/LASTBTL, loop
data/Ogg11/LASTBT3, loop, split
data/Ogg11/ENDING, loop, split
data/Ogg11/ZONBIE, loop, split
data/Ogg11/BDOWN, loop, split
data/Ogg11/HELL, loop, split
data/Ogg11/JENKA2, loop, split
data/Ogg11/MARINE, loop, split
data/Ogg11/BALLOS, loop, split
data/Ogg11/TOROKO, split
data/Ogg11/WHITE, loop, split
```

*refer to the list shown in this article to understand what these song names represent.*

## Notes
To avoid any potential conflicts, be sure to remove any mods that you don't want or know that you won't be using in the mods.txt file.
