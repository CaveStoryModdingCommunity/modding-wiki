# TSC

The term TSC is shorthand for *Text SCript*, which is the custom scripting language that schedules and executes events within Cave Story.
Map script sizes can be a maximum of 17,999 characters (including spaces and line returns).
It can control things like NPC states, game events, and map transitions.

Commands are of the form <CMDwwww:xxxx:yyyy:zzzz. Entity x refers to entities tagged x. Entity type x refers to entities of type x.

<AE+         Arms Energy +          Refill all weapon ammo.

<AM+w:x      ArMs +                 Give weapon W (if not already acquired), and add X ammo. Use 0000 for infinite ammo.

<AM-w        ArMs -                 Remove weapon W.

<AMJw:x      ArMs Jump              Jump to event X if the PC has weapon W.

<ANPw:x:y    Animate NPc            Give all entities W scriptstate X and direction Y. Used for animation.

<BOAw        BOss Animate           Give map-boss (eg Omega) scriptstate W

<BSLw        Boss Script Load       Start boss fight with entity W. Use 0000 to end the boss fight. (NPC flag 0200 must be set; should work with anything that has HP)

<CAT         (C?) All Text          Instantly display text. Use before a <MSG/2/3; works until <END. Same command as <SAT.

<CIL         Clear ILlustration     Clear illustration (during credits).

<CLO         CLOse                  Close message box.

<CLR         CLeaR                  Clear message box.

<CMPw:x:y    Change MaP tile        Change the tile at coordinates W:X to type Y. Produces smoke.

<CMUw        Change MUsic           Change music to song W.

<CNPw:x:y    Change NPc             Change all entities W to type X with direction Y.

<CPS         Clear Prop. Sound      Stops the propeller sound.

<CRE         CREdits                Rolls credits.

<CSS         Clear Stream Sound     Stops the stream sound.

<DNAw        Delete Npc All         Remove all entities of type W.

<DNPw        Delete NPc             Remove all entities W.

<ECJw:x      Event Check Jump       Jump to event X if any entities W exist.

<END         END                    End the current scripted event.

<EQ+w        EQuip +                Equip item W.

<EQ-w        EQuip -                Dequip item W.

<ESC         ESCape                 Quit to title screen.

<EVEw        EVEnt                  Go to event W.

<FACw        FACe                   Show face W in the message box.

<FAIw        FAde In                Fade in with direction W.

<FAOw        FAde Out               Fade out with direction W.

<FL+w        FLag +                 Set flag W. Using flags over 8000 is inadvisable.

<FL-w        FLag -                 Clear flag W.

<FLA         FLAsh                  Flash the screen white.

<FLJw:x      FLag Jump              Jump to event X if flag W is set.

<FMU         Fade MUsic             Fade the music out.

<FOBx:y      Focus On Boss          Focus on boss W in X ticks. Use 0 < X.

<FOMx        Focus On Me            Focus on player in X ticks Use 0 < X.

<FONw:x      Focus On Npc           Focus on entity W in X ticks. Use 0 < X.

<FRE         FREe                   Free game action and the PC.

<GITw        Graphic ITem           Display an item or weapon icon above the message box. Add 1000 to W for items. Use 0000 to remove.

<HMC         Hide My Character      Hide the PC.

<INI         INItialize             Reset memory and restart game.

<INPw:x:y    [Initialize?] NPc      Change entity W to type X with direction Y and set entity flag 100 (0x8000).

<IT+x        ITem +                 Give item W.

<IT-x        ITem -                 Remove item W.

<ITJw:x      ITem Jump              Jump to event X if the PC has item W.

<KEY         KEY lock               Lock player controls and hide status bars until <END.

<LDP         LoaD Profile           Load the saved game.

<LI+x        LIfe +                 Recover W health.

<ML+x        Max Life +             Increase the current and maximum health by W.

<MLP         Map/Location Picture   Display a map of the current area.

<MM0         My Motion 0            Halt the PC's forward motion.

<MNA         Map NAme               Display name of current map.

<MNPw:x:y:z  Move NPc               Move entity W to coordinates X:Y with direction Z.

<MOVw:x      MOVe                   Move the PC to coordinates W:X.

<MP+w        MaP flag +             Set map flag W. Map flags cannot be unset. Highest usable flag is 127.

<MPJx        MaP flag Jump          Jump to event W if the map flag for the current area is set.

<MS2         MeSsage 2              Open an invisible message box at the top of screen.

<MS3         MeSsage 3              Open a message box at the top of screen.

<MSG         MeSsaGe 1              Open a message box at the bottom of the screen.

<MYBw        MY Bump                Causes the PC to hop in the direction opposite of W. Using up or down causes the jump to be vertical.

<MYDw        MY Direction           Causes the PC to face direction W.

<NCJw:x      Npc Check Jump         Jump to event X if any entity of type W exists.

<NOD         [Newline On Demand?]   Wait for player input before resuming script.

<NUMw        NUMber                 Prints the value [4a5b34+W*4] to the message box. Use 0000 to print the last used W from compatible commands (eg AM+).

<PRI         PRevent Interaction    Lock player controls and freeze game action until KEY or END.

<PS+w:x      Portal Slot +          Set teleporter slot W to event X. Selecting slot W while using the teleporter menu will jump to event X.

<QUAw        QUAke                  Shake the screen for W ticks.

<RMU         Resume MUsic           Resume the song last played.

<SAT         Speed-up All Text      Instantly display text. Use before a <MSG/2/3; works until <END. Same command as <CAT. (glitches scrolling text)

<SILw        Show ILlustration      Show illustration W (during credits).

<SK+w        SKipflag +             Set skipflag W. (remains set until program exits, to avoid repeating cutscenes/dialogue after retrying)

<SK-w        SKipflag -             Clear skipflag W.

<SKJw:x      SKipflag Jump          Jump to event Y if skipflag X is set

<SLP         Show Location Portals  Show the teleporter menu.

<SMC         Show My Character      Unhides the PC.

<SMPw:x      Shift MaP tile         Jump to event X if skipflag W is set. Does not create smoke.

<SNPw:x:y:z  Set NPc                Create an entity of type W at coordinates X:Y with direction Z.

<SOUw        SOUnd                  Play sound effect W.

<SPS         Start Prop. Sound      Start the propeller sound.

<SSSw        Start Stream Sound     Start the stream sound with volume W. (from River area - normal pitch is 0400)

<STC         Save Time Counter      Saves current time to 290.rec.

<SVP         SaVe Profile           Saves current game.

<TAMw:x:y    Trade ArMs             Trade weapon W for weapon X and set max ammo to Y. Use 0000 to keep the same amount of ammo. (GLITCH: first weapon 0000)

<TRAw:x:y:z  TRAnsport              Travel to map W, run event X, and move the PC to coordinates Y:Z.

<TUR         [Text UnRead?]         Instantly display text. Use after a <MSG/2/3; works until another <MSG/2/3 or an <END.

<UNIx        UNIverse               Set character movement type. Use 0000 for normal, 0001 for zero-G (disables focus commands) and 0002 to disallow movement (can still fire).

<UNJw:x      UNiverse Jump          Jump to event X if movement is of type W (0000 for normal, 0001 for zero-G).

<WAIw        WAIt                   Pause script for W ticks.

<WAS         WAit until Standing    Pause script until character is on ground.

<XX1w        XX1                    Show the island falling in manner W. Use 0000 to have it crash and 0001 to have it stop midway.

<YNJw        Yes/No Jump            Prompt Yes/No; jump to event W if No is selected.

<ZAM         Zero ArMs              Sets all weapon energy to zero.

Notes:
=======
 Using flags above 7999 will not work properly.
 
 Using skipflags above 63 will not work properly.

 <INI will skip the first 4 characters of the starting event.
 
 Invalid commands show an error message displaying the command before the game exits
 
 The "jump if equipped" function is done with FLJ - an arbitrary flag is chosen, and every instance of EQ+/EQ- must also have the FL+/FL- command
 
 The colon between parameters can be any character (it's ignored)

For editing TSC, please see the [this sub-section](freeware-asset-replacement#tsc-editing).


























