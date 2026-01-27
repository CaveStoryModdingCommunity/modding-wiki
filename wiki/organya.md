

# Organya Music Format



## Overview
> [!WARNING]
> Information Incomplete: Fillers currently in use

Organya(org) is a custom music tracker format created by Pixel in 1999 as an improved version of his other music format; Pixel Music Data(pmd), which was used by his other music editor PiyoPiyo.
It is most prominently known for its use in Cave Story, but a couple other games use it, too, like [Stargazer](http://www5b.biglobe.ne.jp/~kiss-me/aji/star/) and [Azarashi 2001](https://www.cavestory.org/pixels-works/azarashi.php).


The format allows the playback of 14-16 simultaneous channels, with 8 note polyphony and 6-8 different percussion instruments, depending on the player used.


Cave Story only allows 6 of the 8 available percussion tracks to be used, and each is hard-coded to a specific instrument. Changing percussion instruments in the editor will not affect which one will be used during playback ingame. **Any notes put in tracks U and I will crash the game**.
These instruments are:

- **Channel Q:** Bass01
- **Channel W:** Snare01
- **Channel E:** HiClose
- **Channel R:** HiOpen
- **Channel T:** Tom01
- **Channel Y:** Per01
- **Channel U:** Unused (Bass01 by default in OrgMaker)
- **Channel I:** Unused (Bass01 by default in OrgMaker)

This is the case because unlike the org editors which use .wav samples for drums, Cave Story uses the .pxt or PixTone format. This means that drum samples in Orgmaker2 can be replaced by downloading the source code and replacing the .wav files, but the other drum formats used in Cave Story will need to be edited using a PixTone editor, such as [PixTone](freeware-asset-replacement) or [SeaTone](freeware-asset-replacement) and can also be extracted via SeaTone's sfx pusher.




## Editors

> [!WARNING]
> Information Incomplete: Fillers currently in use

Two original versions of the org editor have been released to the public, titled [Orgmaker](orgmaker1) and [Orgmaker2](orgmaker2), respectively.
Recovered versions of the org editor have also surfaced, those versions are:
[V1.0](placeholder), [V1.1](placeholder), [V1.3.2](placeholder), [V1.3.3](placeholder).


The Orgmaker2 editor allows for different drum instruments to be specified.


Several other community efforts have been made to update or completely replace these editors and add some missing quality-of-life features. A notable example of this is [Orgmaker3](orgmaker3).

An effort has also been made to double the amount of tracks in the editor above. The project is called *Organya Maker-16*.


## File format


The ORG music file is in binary.


The instruments are baked into the reader (the file tells the player what instrument number to use)


### The Org Header


The first 6+12 (18) bytes are header info, containing the:
- Org Type (6 char string). This can be `org-02`, `org-03` or `org-16` and corresponds to the capabilities that the file has, such as fancy drums or using more tracks.
- There is an Org type of `org-01`, but sometime after V1.1 Pixel made Orgmaker write `org-01` as `org-02`, regardless of if pipi is used or not.

- Wait (tempo, 2 bytes), see **Org Tempo**
- Line (number of beats per measure, 1 byte), can also be thought of as the number of vertical "lines" the editor shows between each measure.
- Dot (resolution, number of notes in each beat, 1 byte)
- Repeat_x (start of repeat loop, 4 bytes) (These values are per “dot” individual note, despite the player only allowing these to be set at the start of each measure)
- End_x (end of repeat loop, 4 bytes)


<details>
  <summary style="font-size:80%;"><i><b>Example: The header of ACCESS.org</b></i></summary>

  <p style="background-color:#D0D0D0;">
  4F 72 67 2D 30 32 64 00 04 04 00 00 00 00 80 00 00 00
  </p>

</details>


### Track Info




After this, there is a chunk of (16 (tracks, including drums AND notes) *6 (bytes of info each)), for a total of 96 bytes.


Bit structure:
- Frequency (Detunes the instrument; the farther from 1000 the more apparent the detune becomes.) (2 bytes)
- Wave_no (Waveform/Percussion instrument) (1 byte)
- Pipi (only regarded if org type is `org-02` or greater, otherwise is set to 0, is a binary value. Makes the selected instruemnt play in a pizzicato state) (1 byte)
- Note_num (Total number of notes in the song from this track, including note modifiers, such as pan or volume events) (2 bytes)


<details>
  <summary style="font-size:80%;"><i><b>Example: The track info section of ACCESS.org</b></i></summary>


  <p style="background-color:#D0D0D0;">
E8 03 46 00 00 00 E8 03 46 00 31 00 E8 03 20 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 18 00 E8 03 02 00 08 00 E8 03 05 00 2C 00 E8 03 06 00  00 00 E8 03 04 00 03 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00
  </p>
</details>


### Note Data






The file then goes by individual tracks, starting at track 0 and incrementing to 15 (covering all tracks)


Each track length has the note data in the following order, each piece of data is repeated by the number of notes in the track in question (I.E all the note values are written back-to-back for the first track, then all the pan values, etc.):
- 4 bytes determining X location (Placement of a note)
- 1 byte determining Y location (Key, doesn’t need to be as big of a number, 00 is low, FF is high, FF if the note does not exist (is instead a modifier event like pan/vol))
- 1 byte determining the length of each note (from X location, 01 if note is just something like a volume change)
- 1 byte determining note volume (`0x00` is quiet, `0xFF` is loud) (Orgmaker limits this between 4 and 252) (`0xFF` is given to undefined notes)
- 1 byte determining note pan (Left pan is `0x00`. `0x0C` is right pan, given `0xFC` if undefined)


Each note has a total of 8 bytes allocated for it.


When all of the above data is read for each note in the track, the dataset for the next track is presented. If there are no notes in the track, it is skipped. There is no separator data between note data. There is also no termination value; the file ends with the last piece of note data.


Access.org uses only 1 non-percussion channel: **channel 2**. This means that the examples below represent the melody of everybody's favorite Cave Story song.
<details>
  <summary style="font-size:80%;"><i><b>Example: Note X offsets for the second track in ACCESS.org</b></i></summary>


  <p style="background-color:#D0D0D0;">
  00 00 00 00 02 00 00 00 04 00 00 00 08 00 00 00 0A 00 00 00 0C 00 00 00 10 00 00 00 12 00 00 00 14 00 00 00 18 00 00 00 1A 00 00 00 1C 00 00 00 20 00 00 00 22 00 00 00 24 00 00 00 28 00 00 00 2A 00 00 00 2C 00 00 00 30 00 00 00 32 00 00 00 34 00 00 00 38 00 00 00 3A 00 00 00 3C 00 00 00 40 00 00 00 42 00 00 00 44 00 00 00 48 00 00 00 4A 00 00 00 4C 00 00 00 50 00 00 00 52 00 00 00 54 00 00 00 58 00 00 00 5A 00 00 00 5C 00 00 00 60 00 00 00 62 00 00 00 64 00 00 00 68 00 00 00 6A 00 00 00 6C 00 00 00 70 00 00 00 72 00 00 00 74 00 00 00 78 00 00 00 7A 00 00 00 7C 00 00 00 7E 00 00 00
  </p>
</details>


<details>
  <summary style="font-size:80%;"><i><b>Example: Note Y offsets for the second track in ACCESS.org</b></i></summary>


  <p style="background-color:#D0D0D0;">
  26 26 2A 24 24 28 26 26 2A 24 24 28 26 26 2A 24 24 28 26 26 2A 24 24 28 22 22 26 20 20 24 22 22 26 20 20 24 22 22 26 20 20 24 22 22 26 20 20 23 25
  </p>
</details>






<details>
  <summary style="font-size:80%;"><i><b>Example: Note lengths for the second track in ACCESS.org</b></i></summary>


  <p style="background-color:#D0D0D0;">
  01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01
  </p>
</details>




<details>
  <summary style="font-size:80%;"><i><b>Example: Note panning for the second track in ACCESS.org</b></i></summary>


  <p style="background-color:#D0D0D0;">
  06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06
  </p>
</details>


### ORG Tempo:
ORG music can handle 1000 individual notes per second. The wait time is expressed in milliseconds, with the shortest time possible for a single note being 1 millisecond *(having a wait value of "1")*.

To convert BPM to "WAIT", use the following formula:
`60000/(BPM * NPB) = WAIT`

To convert from "WAIT" to BPM, use the following formula:
`60000/(WAIT * NPB) = BPM`

Where:
- `WAIT` is the time in milliseconds each note takes to play (ORG's internal tempo format)
- `NPB` is the number of notes per beat
- `BPM` is the number of beats per minute

Example, with a new org file, the wait value is 128, with 4 notes per beat.
Plugging this in yields: `60000/(128*4)=117.1875`

Converting 117 BPM back to WAIT yields: `60000/(117*4)=128.205`

Note that ORG Wait time is in whole numbers only, so 128.205 would be truncated to 128.

## Music in Organya
Below is a list of songs created with an Organya Editor to show how it looks and sounds.

### Cave Story Soundtrack by Studio Pixel
******
  - [Access](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FAccess.org#)
  - [Gestation](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FGestation%20%28Internal%20Percussion%29.org#)
  - [Mimiga Town](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FMimiga%20Town.org#)
  - [Plant](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FPlant.org#)
  - [Balrog's Theme](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FBalrog%27s%20Theme.org#)
  - [Gravity](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FGravity%20%28Internal%20Percussion%29.org#)
  - [Cemetery](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FCemetery%20%28Internal%20Percussion%29.org#)
  - [Safety](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FSafety.org#)
  - [Mischevous Robot](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FMischievous%20Robot.org#)
  - [Pulse](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FPulse.org#)
  - [On to GrassTown](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FOn%20to%20Grasstown.org#)
  - [Eyes of Flame](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FEyes%20of%20Flame.org#)
  - [Meltdown 2](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FMeltdown%202.org#)
  - [Tyrant](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FTyrant.org#)
  - [Run!](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FRun%21.org#)
  - [Jenka 1](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FJenka%201.org#)
  - [Jenka 2](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FJenka%202.org#)
  - [Labrinyth Fight](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FLabyrinth%20Fight.org#)
  - [Geothermal](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FGeothermal.org#)
  - [Oppression](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FOppression.org#)
  - [Living Waterway](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FLiving%20Waterway%20%28Internal%20Percussion%29.org#)
  - [Quiet](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FQuiet.org#)
  - [Scorching Back](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FScorching%20Back.org#)
  - [Moonsong](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FMoonsong.org#)
  - [Hero's End](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FHero%27s%20End.org#)
  - [Cave Story (Theme)](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FCave%20Story.org#)
  - [Last Cave](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FLast%20Cave.org#)
  - [Balcony](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FBalcony.org#)
  - [Charge](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FCharge.org#)
  - [Zombie](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FZombie.org#)
  - [Last Battle](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FLast%20Battle.org#)
  - [Break Down](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FBreak%20Down.org#)
  - [Running Hell](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FRunning%20Hell.org#)
  - [Seal Chamber](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FSeal%20Chamber.org#)
  - [The Way Back Home](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fcave-story%2Forg%2FThe%20Way%20Back%20Home%20%28Internal%20Percussion%29.org#)
  
  ### Azarashi 2001 Soundtrack by Studio Pixel
  ******
  - [Azarashi](https://www.cavestory.org/soundtrack/organya-js/orgplayext.php?s=https%3A%2F%2Fwww.cavestory.org%2Fsoundtrack%2Fazarashi-2001%2Forg%2FAzarashi.org)


  
