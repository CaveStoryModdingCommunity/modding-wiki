

# Organya
:warning: This page is still under construction! :warning: :cake:


## Overview
*:warning: Information Incomplete: Fillers currently in use*

Organa is a custom music tracker format created by Pixel in [insert proper date here].
It is most prominently known for its use in Cave Story, but several other games use it, too, such as:
- (list of games here)
- (game 2)


The format allows the playback of 13-16 simultaneous channels, with 8 note polyphony and 5-8 different percussion instruments, depending on the player used.


Cave Story only allows 5 of the 8 available percussion tracks to be used, and each is hard-baked to a specific instrument. Changing percussion instruments in the editor will not affect which one will be used during playback ingame. Any notes put in tracks V, W, and X will be ignored during playback.
These instruments are:


- **Channel Q:** Instrument_1
- **Channel W:** Instrument_2
- **Channel E:** Instrument_3
- **Channel R:** Instrument_4
- **Channel T:** Instrument_5


This is the case because unlike the org editors which use .wav samples for drums, Cave Story uses the .pxtone format. This means that drum samples can be replaced in the same manner as [other sfx](add_a_proper_URL!), but the other drum formats used in Orgmaker2 will need to be recreated using a pixtone editor, such as [seatone](add_a_proper_URL!).




## Editors

*:warning: Information Incomplete: Fillers currently in use*

Two original versions of the org editor have been released to the public, titled Orgmaker and Orgmaker2, respectively.


The Orgmaker2 editor allows for different drum types to be specified.


Several other community efforts have been made to update or completely replace these editors and add some missing quality-of-life features. [Example](add_a_proper_URL!).


## File format


The ORG music file is in binary.


The instruments are baked into the reader (the file tells the player what instrument number to use)


### Header


The first 6+12 (18) bytes are header info, containing the:
- Org Type (6 char string). This can be `org-01`, `org-02`, or `org-03` and corresponds to the capabilities that the file has, such as fancy drums or using pipi.

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
- Frequency/pitch detune (2 bytes)
- Wave_no (waveform/percussion instrument) (1 byte)
- Pipi(1 byte) (only regarded if org version is 2 or more, otherwise is set to 0, is a binary value)
- Note_num (2 bytes) (total number of notes in the song from this track, including note modifiers, such as pan or volume events).


<details>
  <summary style="font-size:80%;"><i><b>Example: The track info section of ACCESS.org</b></i></summary>


  <p style="background-color:#D0D0D0;">
E8 03 46 00 00 00 E8 03 46 00 31 00 E8 03 20 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 18 00 E8 03 02 00 08 00 E8 03 05 00 2C 00 E8 03 06 00  00 00 E8 03 04 00 03 00 E8 03 00 00 00 00 E8 03 00 00 00 00 E8 03 00 00 00 00
  </p>
</details>


### Note Data






The file then goes by individual tracks, starting at instrument track 0 and incrementing to 15 (covering all tracks)


Each track length has the note data in the following order, each piece of data is repeated by the number of notes in the track in question (I.E all the note values are written back-to-back for the first track, then all the pan values, etc.):
- 4 bytes determining X location (start of note)
- 1 byte determining Y location (tone, doesn’t need to be as big of a number, 00 is low, FF is high, FF if the note does not exist (is instead a modifier event like pan/vol))
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














