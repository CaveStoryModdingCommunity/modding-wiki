# TSC

The term TSC is shorthand for *Text SCript*, which is the custom scripting language that schedules and executes events within Cave Story:
- It can control things like NPC states, game events, and map transitions.
- Script files end with the `.tsc` file extension (except for CaveStory3D which uses `.sgs` instead).
- Map scripts are found in the `stage` folder.
- A script is made up of two parts: Events and Commands. An event looks like `#0100` by itself on a line, and when that event is ran it will run every command starting underneath that line up until it encounters an `<END` command, a `<TRA` command to transition to another map, an `<INI` or `<ESC` which re-initializes or exits the game respectively, an `<LDP` which loads the saved `profile.dat`, or any of the several commands which jumps to another event, such as `<EVE` or `<FL+`. If there is nothing to end, exit, or jump out of an event, it will continue running into the next lines and possibly even out of the script entirely, leading to unstable behavior.
- There are four special scripts found in the base "data" folder:
  - Head.tsc : A global file that is appended to the TOP of every map script. In vanilla, you will see that Head.tsc goes up to event #0049 while Map Events start around event #0090. You can expand Head.tsc but make sure that the smallest event in every map is larger than the largest event in Head.tsc (there's no overlap when the files are appended).
  - ArmsItems.tsc : Used for all inventory text and scripting. "Arms" refers to weapons.
  - Credits.tsc : Used as part of the credits. This file actually uses a seperate, concurrent parser that has a different format than the one listed below. It runs in tandem with the normal script parser and is the ONLY time two scripts will run concurrently (the map scripts handling illustrations (<SIL and <CIL) and map cutscenes while Credits.tsc handles the scrolling text and icons).
  - StageSelect.tsc : Used for the names of Teleporter options when running the <SLP command. This is only used when the selection menu is on screen and does not contain the scripting for handling what happens when an option is selected.
- Script sizes can be a maximum of 17,999 characters (including spaces and line returns). This is for the buffer that combines BOTH `Head.tsc` and the Map Script, so the combined size cannot exceed 17,999 characters. There are ways to increase this limitation.
- Commands are of the form `<CMDwwww:xxxx:yyyy:zzzz`. The first 3 letters after the `<` denote which command is being used, and each command has a set number of arguments (denoted by example letters here). Each argument is and must be 4 numerical digits, and are seperated by an ignored character. Standard practice (taken from the original vanilla scripts) is to use `:` colons to seperate arguments, but technically anything can be used as a seperator as it will be ignored.
- ALL arguments and event numbers must be four digits in length. This means that event 250 MUST be formatted as `#0250` and CANNOT be formatted as `#250`. Same with arguments, where `<AM+0010:0020` is correct but `<AM+10:20` is not and will cause problems.
- Events MUST BE IN ASCENDING NUMERICAL ORDER. Event `#0310` must come after Event `#0200` and be before Event `#0320`. You can skip events but they must be in order.
- You cannot use `<` or `#` in your events for anything other than denoting Event Numbers and the start of a Command. This means that outside of patching or changing game behavior, one cannot display these two special characters in a textbox.

## TSC Commands
Here is a list of all the TSC commands that are found in the 2004 Freeware version in alphabetical order:

| Command Format | Command Name | Description |
| --- | --- | --- |
| <AE+ | **A**rms **E**nergy **+** | Refill all weapon ammo. |
| <AM+wwww:xxxx | **A**r**M**s **+** | Give weapon W (if not already acquired), and add X ammo. Use 0000 for infinite ammo. |
| <AM-wwww | **A**r**M**s **-** | Remove weapon W. Does nothing if not acquired. |
| <AMJwwww:xxxx | **A**r**M**s **J**ump | Jump to event X if the PC has weapon W. Otherwise if they don't have weapon W it will continue to the next event. |
| <ANPwwww:xxxx:yyyy | **A**nimate **NP**c | Give all entities with event W scriptstate X and direction Y. Used for animation. See <a href="#direction-fai-fao">Direction</a>. |
| <BOAwwww | **BO**ss **A**nimate | Give the Map Boss (eg. Omega) scriptstate W |
| <BSLwwww | **B**oss **S**how **L**ife | Displays a boss health bar for the entity with event W. Only one can display at a time. Use `<BSL0000` for the Map Boss (eg. Omega) if one is set for the map. You usually need an <ANP or <BOA to actually make the boss start attacking. |
| <CAT | **C**lear **A**uto **T**urbo | Instantly displays text. Use before a `<MSG/2/3`; works until `<END`. Same command as `<SAT`; evidence suggests it was MEANT to disable `<SAT` but it is bugged to be an exact clone of it. |
| <CIL | vC**lear **IL**lustration | Clear illustration (during credits). |
| <CLO | **CLO**se | Close message box. Certain other commands like `<END` will also close it. |
| <CLR | **CL**ea**R** | Clears the message box but does not close it. Certain other commands like `<END` will also close it. |
| <CMPwwww:xxxx:yyyy | **C**hange **M**a**P** tile | Change the tile at coordinates W:X to type Y. Produces smoke. |
| <CMUwwww | **C**hange **MU**sic | Change music to song W. Use `<CMU0000` to stop the music (technically it plays a silent looping track). |
| <CNPwwww:xxxx:yyyy | **C**hange **NP**c | Change all entities with event W to type X with direction Y. See direction table above. |
| <CPS | **C**lear vP**rop. **S**ound | Stops the propeller sound from `<SPS`. |
| <CRE | **CRE**dits | Rolls credits. Specifically starts parsing `Credits.tsc` seperately to start displaying scrolling text and icons, but the event continues running (eg. you'll need to use `<SIL` and `<CIL` to display the half-screen images). |
| <CSS | **C**lear **S**tream **S**ound | Stops the stream sound from `<SSS`. |
| <DNAwwww | **D**elete **N**pc **A**ll | Remove all entities of TYPE W. |
| <DNPwwww | **D**elete **NP**c | Remove all entities with EVENT W. Note that killing or deleting an NPC will set its assigned flag. |
| <ECJwwww:xxxx | **E**vent **C**heck **J**ump | Jumps to event X if any entities with event W exist. Use `<NCJ` instead for checking NPC TYPE. |
| <END | **END** | End the current scripted event. Most of your events must end with this command unless it uses another acceptable command such as `<TRA` or `<EVE`. |
| <EQ+wwww | **EQ**uip **+** | Set Equip flag W. These are for equipping items (eg. The Booster 2.0 or Arms Barrier) but these are not the same as the item IDs used in `<IT+`. See <a href="#equip-flags-eq-eq-">Equip flags</a>. |
| <EQ-wwww | **EQ**uip **-** | Unsets (removes) Equip flag W. See <a href="#equip-flags-eq-eq-">Equip flags</a>. |
| <ESC | **ESC**ape | Quit to title screen. Any other commands after this one within the same event will be ignored. |
| <EVEwwww | **EVE**nt | Go to event W. Any other commands after this one within the same event will be ignored. |
| <FACwwww | **FAC**e | Show facepic (face picture) W in the message box. Use `<FAC0000` to remove the facepic. Note that with a facepic active you will have less characters that can be displayed per line. You may need to use `<FAC` before the `<MSG/2/3` if you're switching from one character to another and don't want it to flash the wrong facepic for a frame. |
| <FAIwwww  | **FA**de **I**n | Fade in with direction W. See <a href="#direction-fai-fao">Direction</a>. |
| <FAOwwww | **FA**de **O**ut | Fade out with direction W. |
| <FL+wwww | **FL**ag **+** | Sets Event Flag W. The valid and safe Event Flags to use are between 0001 and 7999 inclusive. Using anything other than that could access Out Of Bounds (OOB) memory or have adverse effects. |
| <FL-wwww | **FL**ag **-** | Clears/Unsets Event Flag W. |
| <FLA | **FLA**sh | Flash the screen white. |
| <FLJwwww:xxxx | **FL**ag **J**ump | Jump to event X if Event Flag W is set. Otherwise if NOT set it will continue to the next command. |
| <FMU | **F**ade **MU**sic | Fade the current music out. |
| <FOBxxxx:yyyy | **F**ocus **O**n **B**oss | Focus on Map Boss part W with a camera speed of X. The smaller the number X is the faster it will follow, but it MUST be higher than 0. The W in this command isn't really documented so you probably just want to use 0000 for W to focus on the main part of the Map Boss. |
| <FOMxxxx | **F**ocus **O**n **M**e | Focus on player with a camera speed of X. The original vanilla games uses `<FOM0016` as the default camera state. |
| <FONw:xxxx | **F**ocus **O**n **N**pc | Focus on entity with event W with a camera speed of X.|
| <FRE | **FRE**e | Free game action and the PC. Specifically it undoes `<KEY` and `<PRI` without ending the event. Note that the player is invincible while an event is running (except for tile spikes). |
| <GITwwww | **G**raphic **IT**em | Display an item or weapon icon above the message box. Add 1000 to W for items. Use 0000 to remove. |
| <HMC | **H**ide **M**y **C**haracter | Hides the PC. Essentially disables running any player code at all as if they temporarily don't exist including physics. They will freeze in place invisibly. |
| <INI | **INI**tialize | Resets memory and restarts into a new game. NOTE there is a bug where it will skip the first 4 characters of the starting event. |
| <INPwwww:xxxx:yyyy | **I**nteractible **NP**c | Change (all?) entities with event W to type X with direction Y and set entity bitflag 100 (0x8000). In other words, this is the exact same as `<CNP` but it will make the NPC interactible. |
| <IT+xxxx | **IT**em **+** | Gives item W to the player if they don't already have it, adding it to their inventory and playing a sound. |
| <IT-xxxx | **IT**em **-** | Removes item W. Does nothing if they don't have it. |
| <ITJwwww:xxxx | ITem Jump | Jump to event X if the PC has item W. Otherwise if they don't have item W it will continue to the next event. |
| <KEY | **KEY** lock | Lock player controls and hide status bars until `<END` or `<FRE`. |
| <LDP | **L**oa**D** **P**rofile | Loads the saved game. Any commands after this one within the same event will be ignored. By default  |
| <LI+xxxx | **LI**fe **+** | Recover W health. This cannot go over Max Health. The original vanilla game uses `<LI+1000` to fully heal the player. |
| <ML+xxxx | **M**ax **L**ife **+** | Increase the current and maximum health by W. |
| <MLP | **M**ap/**L**ocation **P**icture | Displays a map of the current area. This can have visual glitches if not run in the inventory script `ArmsItems.tsc`. Use `<EQ+0002` to allow the player to press the 'W' key or controller equivalent to display the map any time they want. |
| <MM0 | **M**y **M**otion **0** | Halt the PC's forward motion. Used in cutscene triggers to stop the player in mid-air and have them drop straight-down instead of keeping their momentum and having them fall PAST the trigger. |
| <MNA | **M**ap **NA**me | Displays the name of current map. |
| <MNPwwww:xxxx:yyyy:zzzz | **M**ove **NP**c | Move entity with event W to coordinates X:Y with direction Z. |
| <MOVxxxx:yyyy | **MOV**e | Move the PC to coordinates X:Y. |
| <MP+wwww | **M**a**P** flag **+** | Sets Map Flag W. NOTE that Map Flags are an unused mechanic of the game. Map flags cannot be unset. Highest usable flag is 127.
| <MPJxxxx | **M**a**P** flag **J**ump | Jump to event W if the map flag FOR THE CURRENT MAP is set. |
| <MS2 | **M**e**S**sa**G**e 2 | Opens an invisible message box at the top of screen. |
| <MS3 | **M**e**S**sa**G**e 3 | Opens a message box at the top of screen. |
| <MSG | **M**e**S**sa**G**e 1 | Opens a message box at the bottom of the screen. |
| <MYBwwww | **MY B**ump | Causes the PC to hop in the direction OPPOSITE of W. Using up or down causes the jump to be vertical. |
| <MYDwwww | **MY D**irection | Causes the PC to face direction W. 0 through 3 follows the directions outlined in the <a href="#direction-fai-fao">direction table</a>. Directions between 10 and 255 will make the PC face the direction of an NPC with a matching event number. |
| <NCJwwww:xxxx | **N**pc **C**heck **J**ump | Jumps to event X if any entity of TYPE W exists. Use `<ECJ` instead for checking an npc event number. |
| <NOD | **N**ewline **O**n **D**emand / **P**layer **NOD**s | Wait for player input before resuming script. |
| <NUMwwww | **NUM**ber | Prints the value `0x4a5b34+W*4` to the message box. Use 0000 to print the last used W from compatible commands (eg AM+). |
| <PRI | **PR**event **I**nteraction | Lock player controls and FREEZE the game action until `<KEY` (unfreezes game) or `<FRE` or `<END`. |
| <PS+wwww:xxxx | **P**ortal **S**lot **+** | Set teleporter slot W to event X. Selecting slot W while using the teleporter menu will jump to event X. Valid slots are 0 through 6. |
| <QUAwwww | **QUA**ke | Shake the screen for W ticks. Ticks are determined by FPS, so 50 ticks equals 1 second when the game runs at 50 FPS. |
| <RMU | **R**esume **MU**sic | Resume the song last played. Generally used for resuming after playing a short jingle. |
| <SAT | **S**peed-up **A**ll **T**ext | Instantly display text. Use before a `<MSG/2/3`; works until `<END`. Functionally the same command as `<CAT`. |
| <SILwwww | **S**how **IL**lustration | Show illustration W (during credits). |
| <SK+wwww | **SK**ipflag + | Sets skipflag W. Valid values are 0 through 63 inclusive. Skipflags are preserved while the game is running, even when reloading a save. They do not save to the save file. Used to skip lengthy cutscenes if the player saw it once and then died. |
| <SK-wwww | **SK**ipflag - | Clears/Unsets skipflag W. |
| <SKJwwww:xxxx | **SK**ipflag Jump | Jumps to event Y if skipflag X is set. |
| <SLP | **S**how **L**ocation **P**ortals | Shows the teleporter menu. I'm pretty sure(?) this will ignore any following commands after this one within the same event (since selecting an option will run a different event), but maybe it continues if you select nothing. |
| <SMC | **S**how **M**y **C**haracter | Unhides the PC after a `<HMC`. You want to use this after a Balrog bossfight as he essentially performs an internal `<HMC` when he grabs the PC. |
| <SMPxxxx:yyyy | **S**hift/Subtract **M**a**P** tile | Subtracts 1 from the Tile ID at coordinate X:Y, making it transform into the tile to its left in the tile sheet. This means Right-to-Left and Bottom-to-Top. Does not create smoke. |
| <SNPwwww:xxxx:yyyy:zzzz | **S**pawn **NP**c | Create an entity of type W at coordinates X:Y with direction Z. This entity will have event and flag 0000, meaning you can't reference it with any other commands. Use `<CNP` on an invisible null entity to make an NPC suddenly appear that you can reference in other commands. |
| <SOUwwww | **SOU**nd | Play sound effect W. |
| <SPS | **S**tart **P**rop. **S**ound | Starts the looping propeller sound. Use `<CPS` to stop. |
| <SSSwwww | **S**tart **S**tream **S**ound | Starts the stream sound with pitch W. The original game's Waterway uses 0400. Use `<CSS` to stop. |
| <STC | **S**ave **T**ime **C**ounter | Saves current time to `290.rec`. This does not remove the timer. Use `<EQ-0256` to later remove the timer from the screen. |
| <SVP | **S**a**V**e **P**rofile | Saves current game. Note that you can run into issues if you don't use `<FL+0431` before you `<SVP`, unless you edit some events in `Head.tsc` to force the jumps in events 0040 through 0042.
| <TAMwwww:xxxx:yyyy | **T**rade **A**r**M**s | Trades weapon W for weapon X and sets max ammo to Y. Use 0000 to keep the same amount of ammo. |
| <TRAwwww:eeee:xxxx:yyyy | **TRA**nsport | Travels to map W, runs event E in the map you travel to, and moves the PC to coordinates X:Y. Make sure that event E exists in map W! |
| <TUR | **TUR**bo | Instantly displays text. Use after a `<MSG/2/3`; works until another `<MSG/2/3` or an `<END`. |
| <UNIwwww | **UNI**verse | Sets character movement type W. Use 0000 for normal, 0001 for Zero Gravity like in the Ironhead fight (this will disable FOM from being able to follow the player), and 0002 to freeze the player in place but still allow them to point in directions and shoot weapons. |
| <UNJwwww:xxxx | **UN**iverse **J**ump | Jump to event X if movement type is of type W (from the above command). |
| <WAIwwww | **WAI**t | Pause script for W ticks. Ticks are determined by FPS, so 50 ticks equals 1 second when the game runs at 50 FPS. Any number between 0 and 3 inclusive is inconsistent. |
| <WAS | **WA**it until **S**tanding | Pauses script until character is on ground. Will softlock the game if the PC is unable to touch the ground. |
| <XX1wwww | **XX1** | Show the island falling in manner W. Use 0000 to have it crash and 0001 to have it stop midway.
| <YNJwwww | **Y**es/**N**o **J**ump | Prompt Yes/No; jump to event W if No is selected. |
| <ZAM | **Z**ero **A**r**M**s | Sets all weapon levels to zero. |

### Notes:
- Invalid commands show an error message displaying the command before the game exits. Unless patched in Freeware, this error text will will be in Japanese, which if your computer is not set to the Japanese Locale, it will display [Mojibake](https://en.wikipedia.org/wiki/Mojibake) gibberish.
- There is no <EQJ to jump to an Event if an Equip Flag is set. In the original vanilla game, both Booster versions and the Whimsical Star use an arbitrary Event Flag (`<FLJ`) in `ArmsItem.tsc` to determine if the item is equipped or not.

For editing TSC, please see the [this sub-section](freeware-asset-replacement#tsc-editing).

## Argument lists
### Direction (`<FAI`, `<FAO`)

| #### | Direction (`<FAI` and `<FAO`) | Direction (NPC Commands) |
| --- | --- | --- |
| 0000 | Left | Left |
| 0001 | Up | Up |
| 0002 | Right | Right |
| 0003 | Down | Down |
| 0004 | Center | Attempts to make them face the player by giving 0000 to face left or 0002 to face right. |
| 0005 | INVALID | Ignored/Unchanged. An NPC with direction 3 and transformed into another with `<CNPwwww:xxxx:0005` will keep direction 3. |

### Equip flags (`<EQ+`, `<EQ-`):

| #### | Name | Item id | Notes |
| --- | --- | --- | --- |
| 0001 | Booster v0.8 | 0018 | (ignored if v2.0 on) |
| 0002 | Map System | 0002 | - |
| 0004 | Arms Barrier | 0019 | - |
| 0008 | Turbocharge | 0020 | - |
| 0016 | Curly's Air Tank | 0021 | - |
| 0032 | Booster v2.0 | 0023 | - |
| 0064 | Mimiga Mask | 0024 | - |
| 0128 | Whimsical Star | 0038 | - |
| 0256 | Nikumaru Counter | 0022 | - |

## Other
TODO:
- Add CS+, CS+Switch, and Modded Commands
