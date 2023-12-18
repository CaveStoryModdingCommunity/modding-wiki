# Out Of Bounds (OOB) TSC Flags
This page contains a list of flag variables that exceed the limit (8000). This is why going over 8000 by using flags is inadvisable, since toggling these flags will cause the game to do some strange things. Luckily enough, some of these "Out of Bounds" flags can prove to be useful for you.

[Tribute Site Forums Thread](https://forum.cavestory.org/threads/using-oob-tsc-flags-to-exploit-memory.13917/)

The following content was taken from the post made by Enlightened, the original creator of the list, found at the link above. 

>Hey, so I've always been telling myself that after I'm done with modding I'll post these, but since:
>1. I don't know when that will be.
>2. I have a habit of randomly disconnecting from this place, never intending to come back.
>3. It ain't doing any favors and is kinda selfish I guess?
>4. The question about them came up recently in the Discord group.

>I've decided to share them right now, here's a new tool any newcomer can use in their mods.


## Section 1: The Reference Sheet

### KEYS:

Setting these flags will simulate player keypresses ingame, allowing for some control over user input from TSC.

```
(Add 32 to any number to instead set an auto-unsetting quick press, not recommended for jumps)
[9088] Left Arrow Key (These don't work when joystick settings are enabled)
[9089] Right Arrow Key
[9090] Up Arrow Key
[9091] Down Arrow Key
[9092] W/Map Shortcut
[9093] X/Shoot (Warning: can be switched in DoConfig)
[9094] Z/Jump (Warning: can be switched in DoConfig)
[9095] S/Switch Weapon Right
[9096] A/Switch Weapon Left
[9097] Shift (Unused)
[9098] F1/Resume
[9099] F2/Reset
[9100] Q/Inventory
[9101] (Not a key, does nothing)
[9102] (Not a key, does nothing)
[9103] ESC/Pause
[9104] < / Alternate Left (The alternate keys from DoConfig.exe, no joystick support)
[9105] > / Alternate Down
[9106] ? / Alternate Right
[9107] L / Alternate Up?
[9108] = (Unused)
```

NON-KEY:
```
[B752] Player invincibility timer
[B800] Current Whimsical star count (Max onscreen is three, must have <EQ+0128)
[8704] Hard Quake (more rough than <QUA)
[=856] Set/Unset FPS counter
[B922] Add 100 to Air, or more
[C008] Current Booster Fuel
[C035] When set, Booster runs near-infinite until you touch land
[B992] (This value had no description in my notes, will have to check what it was)
[B720] Adds EXP to recent score counter (Visual only, doesn't actually add exp.)
[B688] Flashes EXP Bar (Similar to that of the Spur)
[B848] Temporary extends health and health bar (Visual only, doesn't actually add health)
[C104] Nikumaru Time (Using C120 adds around 22 minutes, as an example)
[B784] Values of current health. Can be manipulated to change it to a specific value.
[B816] Values of max health. Same as above.
[8800] The first bit in the game-timer I think? Use <FLJ for a 50% chance of a jump, but don't use it more than once when running a string of events or they will no longer be random.
```
## Section 2: How to use The Reference Sheet, proper key etiquette, and tips and tricks


Alright, this is what you need to do: You pretend these values are flag numbers. If you want the FPS counter to activate you would run `<FL+=856` in an event. If you want to see if the player is pressing the SHIFT key you run `<FLJ9097` in an event. It will jump or pass through depending on if they key is currently being pushed down. It's way more simple than one would think at first, but just make sure that those B's and C's are capitalized exactly how they are in the brackets.

### Why does this happen?

Basically the binary flags used in the game to remember events have a space in memory, which is also located to a bunch of other variables that are constantly being used in the game. One isn't supposed to use anything other than the 8000 bits ("flags") allotted to the space, but by using characters other than numbers you can read and edit OOB (Out-of-Bounds) values that aren't controlled by other TSC commands.

HOWEVER, there is a trick to working with most of the NON-KEY values. Since these are variables we are accessing via individual bits, we have to read/write them in binary. The values I listed above are the first bit of said variable, but setting/unsetting this flag is almost always useless because it will only edit the first bit of a timer, often making the changes invisible. You will want to use flags slightly higher than the flag code I listed, often setting a string of them at once, to get a longer-lasting desired effect.

#### Example:

 Using "<FL+8704" will activate a hard quake, but for only 1 tick/frame. "8705" will add 2 ticks, "8706" will add 4 ticks, and so on in powers of 2. If you want a 100 frame hard quake (2 seconds if the FPS is 50), you would use a combination of flags set to get that amount, or if you are lazy you could just use some larger number like "8711" and call it a day. Be reasonable though or you will likely accidentally be editing something else entirely.

#### Example 2:

 Say you wanted the exp counter to visually say "+1337" above the player. The first flag is [B720], so in order to get an exact value of 1337 you would first visualize or jot down each flag to a power of 2 like so:
```
1  <FL+B720
2  <FL+B721
4  <FL+B722
8  <FL+B723
16  <FL+B724
32  <FL+B725
64  <FL+B726
128  <FL+B727
256  <FL+B728
512  <FL+B729
1024  <FL+B730
```

And sum up the numbers to get a total of 1337, resulting in this code:

```<FL+B720<FL+B723<FL+B724<FL+B725<FL+B728<FL+B730```

Or you could be lazy and look at these other codes:
```
+69
<FL+B726<FL+B722<FL+B720
+404
<FL+B728<FL+B727<FL+B724<FL+B722
+666
<FL+B729<FL+B727<FL+B724<FL+B723<FL+B721
```

*And no, before you ask if you can display a `+80085` above the player, you are only allowed a 4-digit number.*

Now that you may or may not understand how binary works now, here is some other good things to know about using these codes as flags:


- The key flags are defined as if the key is currently being held, acting like an alt-tab where a key gets stuck and one has to press it to reset it to the off state.


- Do note that setting these flags are you essentially telling the game that the key is being held down, and is unfriendly to the player who is actually supposed to be the one behind the controls. It is recommended that you only <FLJ these values to determine what the player is doing. If you NEED to force a key via setting the flag, try adding "32" to the value of the key, which will instead tell the game it was just tapped, and won't result in stuck keys you have to unset.

- Various functions are disabled when running TSC events, but seem to work if executed right before an <END. Examples include the invincibility timer and opening the Map/Inventory, you have to set the flag right before ending the script.


- Likewise, for some odd reason the player is unable to interact with objects if certain keys are held down. Pressing "down" won't open doors and such if the "L" key is stuck, etc.

- **IMPORTANT:** For controller support, all of the buttons are reinterpreted as keys, and so one can still see if the player is pressing the inventory button with "<FLJ9100". THE EXCEPTION is with the movement keys, because the joystick works differently in engine. Because of this one should basically never rely on the arrow/movement keys because they simply don't work with controllers. For making a menu in TSC I instead suggest a moving player character to select between options or using the keys for cycling weapons instead.


## Section 3: How did I get these values, and where can more be found.

First one should note that you can't reach every corner of the executable when working with bits. I'm pretty sure this is 90% of the useful values, as others like player velocity, soft quakes, and the dimensions of the current map are practically useless to edit in a pure TSC script, and learning ASM from the community would be a better option to achieve your goals.
