# Assembly Offsets

This list of hex addresses shows where each different type of componet is processed in the executable. Knowing where these offsets are allows for quick modification using [OllyDbg](ollydbg) or DouAsm, or injection with the [modloader](modloader).



## TSC offsets

This document was made by Kenni T.

These offsets are related towards only the Vanilla TSC commands, not the TSC+ commands.

```
List by Kenzo_ITN [5/12/17]

These offsets are for vanilla Cave Story.

00422510 - Start of the TSC command check code.
004225E4 - Checks for "<" used as the first character for all TSC commands.

[Listed in order by offset]
004225ED - END
00422666 - LI+
004226D9 - ML+
0042274C - AE+
004227A3 - IT+
00422821 - IT-
00422893 - EQ+
00422907 - EQ-
0042297B - AM+
00422A25 - AM-
00422A96 - ZAM
00422AED - TAM
00422B95 - PS+
00422C20 - MP+
00422C93 - UNI
00422D06 - STC
00422D5D - TRA
00422E3A - MOV
00422ED5 - HMC
00422F31 - SMC
00422F8B - FL+
00422FFC - FL-
0042306D - SK+
004230DE - SK-
0042314F - KEY
004231CE - PRI
00423236 - FRE
00423295 - NOD
004232F5 - CLR
0042334A - MSG
004233E8 - MS2
0042348E - MS3
00423529 - WAI
004235A0 - WAS
004235FE - TUR
00423660 - SAT
004236C0 - CAT
00423721 - CLO
00423783 - EVE
004237E6 - YNJ
00423878 - FLJ
00423916 - SKJ
004239B3 - ITJ
00423A4E - AMJ
00423AEC - UNJ
00423B7D - ECJ
00423C1B - NCJ
00423CB8 - MPJ
00423D36 - SSS
00423DAB - CSS
00423E02 - SPS
00423E62 - CPS
00423EB9 - QUA
00424F2B - FLA
00423F89 - FAI
00424008 - FAO
00424087 - MNA
004240DE - FOM
00424151 - FON
004241DA - FOB
00424266 - SOU
004242DA - CMU
0042434C - FMU
004243A1 - RMU
004243F8 - MLP
00424481 - SLP
00424521 - DNP
00424593 - DNA
00424607 - BOA
00424679 - CNP
0042471F - ANP
004247C7 - INP
0042486F - SNP
0042494E - MNP
00424A22 - SMP
00424AAD - CMP
00424B55 - BSL
00424BD4 - MYD
00424C46 - MYB
00424CB8 - MM0
00424D0D - INI
00424D6E - SVP
00424DC8 - LDP
00424E28 - FAC
00424EAF - FAC (Very simular to the first FAC, but is Unused)
00424F33 - GIT
00424FAB - NUM
0042501C - CRE
00425082 - SIL
004250F4 - CIL
00425149 - XX1
004251FC - ESC
```


## GUI Offsets


This list contains offsets for the GUI elements (Inventory Screen, Health bar, experience bar, etc.) to locate for Assembly hacking. This list was made by Safusaka.

```
4016F0 - Start of GUI rendering maybe
Start of Inventory GUI
4018AD - Graphic for top edge
4018B3 - Distance from top
4018B5 - Distance from left
4018C6 - Vertical spacing of center (every 8 pixels)
4018D8 - Vertical length (carries bottom border, every 8 pixels)
4018DE - Middle section graphic
4018EF - Distance from left
401902 - Bottom edge graphic
401916 - Distance from left
401927 - Negative distance for ARMS and ITEM to travel I guess
401936 - Speed of said travel
40193F - Graphic of ARMS
40194C - Distance for ARMS from left
40195D - Graphic of ITEM
401969 - Distance for ITEM away from ARMS
40196D - Distance for ITEM from left
401994 - Graphic for blinking box
4019AE - Distance from top
4019B5 - Equation for spacing
4019B8 - Distance from left
4019CD - Graphic for small blinking box
4019D3 - Distance from top
4019DA - Equation for spacing
4019DD - Distance from left
4019F0 - Amount of weapon blocks to skip I guess
401A0F - Equation for spacing
401A23 - Equation for Arms graphic size in weapon block maybe
401A48 - Width of Arms graphic in weapon block
401A72 - Graphic for Arms in weapon block
401A7B - Distance from top
401A80 - Equation for Arms graphic spacing
401A83 - Distance from left
401A96 - Graphic for /
401A9F - Distance from top
401AA4 - Equation for / spacing
401AA7 - Distance from left
401ABA - Graphic for Lvl
401AC0 - Distance from top
401AC5 - Equation for Lvl spacing
401AC8 - Distance from left
401AEA - Distance for Lvl number from top
401AEF - Equation for Lvl number spacing
401AF2 - Distance from left

other stuff ...

401E64 - Graphic for background during pause. 1C makes it use the current map bg
but it doesnt tile so it really only works with full screen bgs..

402270 - Start of BG probably

402830 - Start of idk let me sleep

402FC1 - This might be tiles cant remember

40DD70 - Start of ESC menu
40DE14 - Distance from top
40DE16 - Distance from left

40F380 - Definitely the number rendering

40F9B0 - Title Screen
40FDA8 - Title Screen Color
40FDF4 - These are the times needed to change the title screen music
40FE7F - These are the songs that get used
40FECA - Default Title Screen Music
40FF45 - Sound effect for selection
40FF5C - Key for ESC menu on title screen
40FFB3 - Sound effect for moving on title screen
410014 - Graphic for "Version"
41001A - Distance from top
41001F - Distance from left
41002E - Graphic for ".  .  .  ."
410037 - Distance from top
41003C - Distance from left
41004E - Version numbers, same format as above
4100AE - "Cave Story" graphic
4100B4 - Distance from top
4100B6 - Distance from left
4100C5 - Graphic for "New"
4100CE - Distance from top
4100D3 - Distance from left
4100E5 - Graphic for "Load"
4100EB - Distance from top
4100F0 - Distance from left
410102 - Graphic for "2004.12 Studio Pixel"
41010B - Distance from top
410110 - Distance from left
41011F - Quote on title screen
4102E5 - Position on "New" from the top
4102F1 - Position on "Load" from the top
410316 - Position on "New" from the left
410339 - Position on "Load" from the left

40ABC0 - Caret Stuff
40ABD6 - Soft limit on caret images
49ABF2 - Graphic for Caret







419D10 - the main gui stuff

41A1D0 - HP Meter
```


## Function Offsets

This list was initiated and collaborated by S. P. Gardebiter, Runelancer and GIRakaCHEEZER. It was later updated by Noxid. Some portions of this list are not completely covered and have unsure responses, use at your own discretion if you're feeling experimental!

This list is over 1300 lines long, and for obvious reasons, if included inline, would bloat the page, so it has been moved to a [downloadable text document](files/function-offsets.txt).

Many of the functions described in this list can be cross-refrenced with [CSE2](cse2.md), the cave story engine decompilation to see what they do and exactly how they do it.


## Assembly Compendium

Noxid's Assembly Compendium contains a plethora of Assembly offset findings and other various neat doohickeys. Unfortunately, not all of the given information is correct and some of it is "unsure". As of now, with some of the new documents that are forming, this compendium is outdated in some areas, but had stood the test of time for many years. Use at your own discretion!

Like the function offset list above, this file is also massive *(2291 lines for those of you counting at home)*. Likewise, it has also been moved to a [downloadable text document](files/noxids-assembly-compendium.txt).












