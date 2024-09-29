# Miza

<p style="color:#B00000;"><i>Note: It is <b>Not</b> recommended to use Miza anymore for modding Cave Story. Better alternatives can be found in the list of <a href="{{ '/cavestory-editors' | relative_url }}">editors</a>. This page and instructions are still here for archival purposes only.</i></p>


> *"Ehh, you could just switch to either Sue's Workshop or Cave Editor
{Let's not start a SW vs CE debate in here}"*  - Voidmage_Lowell, 2009


**Miza** is commonly referred to as the first available editor for modifying Cave Story. While a defunct tool, it provides a prominent first step as the predecessor of most Cave Story editors and tools used today by modders.

The editor was released in 2005 by **Kyofu Kawa-chan**, or simply **Kawa**. It was first released for the Acmlmboard and then eventually added to Romhacking.net before making its way to the Cave Story Tribute Site.
It soon became a defunct tool as editors such as [Sue's Workshop](sues-workshop) and [Cave Editor](cave-editor) were released.

There is a Miza.chm help file done in html that gives basic information on how to navigate the program as well as a command list that was incomplete. The file also shows instructions on how to change ORG files in Resource Hacker.

Due to the guide's bouts of tasteful language it will not be mentioned beyond this point.

[Download](http://www.romhacking.net/utilities/458/) (Version 1.04).



## How to use Miza

Miza is a very fickle editor due to its state and lack of features. The editor is capable of basic map editing and scripts must be decoded (and afterward re-encoded) in the Main interface before you can access them on a notepad document for editing. When opening the editor you will be taken immediately to the Start Point map with all of the editor's features available to you.

To start, you must input Miza and its files into the directory of the Cave Story executable you wish to modify.

Once inside you will have the Main interface which will also include the Map editing interface with the last loaded map (if it's your first time opening the program with that .exe, it will load map 13, Start Point).
Miza Main interface (sample 2)
### Main interface

Once the Main interface has loaded you are met with the last accessed map (In a text file accompanied with the program displays editable information for things such as the last loaded map and the last zoom setting picked).

You are greeted with:

- 5 subtabs:
    - Stage
    - Load
    - Save
    - Properties
    - About
- A tile set
- The map
- The entities menu on the right:
    - The entity's current properties
    - A slider to view all entities placed on the map
    - The entity properties menu
    - A button to increase or decrease the number of entities on a map.
    - A hide entities button
    - Buttons for decoding and encoding TSC scripts
    - The zoom in/out dropdown button

**[Image needed]** *Miza properties menu*

**[Image needed]** *Miza example of copy map feature*

Here is an example of the Map feature in action. In the photo, the Execution Chamber map replaced the Grasstown Hut map. The tile set does not change however.
### Miza About section

The 5 subtabs: This section is at the top of the program and has several functions that can be used at any point in time.

- Stage: Allows one to chose the current stage from numerical order.

    It should be noted that in the stage table: stages 74 - 78, 89, 91, and 93 are not named. All of which are stages related to the game's credits during the enemy roll call.
- Load: This feature will re-load the map. In case of errors made, this feature can completely redo all un-saved changes.
- Save: Saves any changes made to the map.
 -Properties: This menu will display properties for the map. Several settings can be changed via drop-down menus.
- Title: This setting will allow you to change the map's caption that shows when entering the map.
- Tile set: Displays the map tile set used.
- Map: This feature is essentially a copy tool. Depending on what map you are on, it will copy the map's entities and tiles, pasting it over the selected map. All maps are ordered by their internal names. Scripts are not over-written.
- Backdrop: This feature will let you change the map's background, a small preview window will also show what the background is before applying it.
- Sprite set: Chooses the sprite set, no preview is shown unlike the backdrop.
- Length & Height: Defines the map's size.
 -Parallax: Decides how much speed the camera follows as well as special conditions such as BkMoon and BkFog utilizing parallax 6 and 7.
    
    It should be noted the list for scroll types is incomplete. Only scroll types 1, 2, 3, (listed as Core style) and 5 (listed as Artery style). 6, 7, and 8 are not listed. In Miza scroll types 9, and A - F are listed but they do not do anything and act as if using scroll type 3 and 4 (hide background).
- About: This menu shows some basic information such as the creator's name, the date, the fact it can be used with Cave Story 1.0.0.5. (as well as 1.0.0.6), and extra information such as links to sites pertaining to Miza and Cave Story (the last point is speculation because none of the links (minus Studio Pixel's blog) are no longer accessible).
- The Map Editing tile set: The tile set menu shows the current stage's tile set that can be accessed. Clicking on a tile will put you in paintbrush mode and clicking on any non-entity tile will modify that tile with the currently selected one.
        
    A scrollbar is attached to the right side of the tile set for moving around the tile set but it only goes up and down, and no third button scroll functions are usable.
    
    You cannot undo and redo changes made while editing tiles.
- Entities: Entities will be indicated by doted-lined tiles, these tiles cannot be edited when in tile editing mode. You will need to manually move the entities before making changes to the tiles. At the very bottom of the Main Menu interface, when highlighting entities you will see the entity's NPC name and NPC ID as well as their position on the map.
- Entity Information: This information is kept at the right of the screen when highlighting an entity, it displays the entity's current information. Entities will be highlighted in a blue square when in their properties menu.
- X and Y: Displays the entity's map coordinates in both base and hex values. For example: 0xF (15), 0xC (12).
- Flag: The entity ID (also known as the Flag ID).
- TSC: The marked event the entity is associated with in the TSC.
- Type: Displays what entity will be visually displayed.
- ???: This displayed value unknown at the time displays the flags used (such as 2000 for calling events when pressing down, or 800 for appearing when a specified Flag ID is set.
- Name: Listed below all of the information is the entity's name, all entity names are saved the "Miza.ini" file, they can be modified.
- Entity Properties: Takes you to the entity properties menu.
- Change number of entities: Changes the available number of editable entities on the map.
    
    It should be noted that this setting means there is no way to add new entities manually without going into this menu and increasing (or decreasing if you want less entities) the number of available entities. This setting also does not mean you can increase the limit of entities, it is still hard-coded at 255.
- Hide Entities: Allows for all entities to be hidden, togglable.
- TSC Decode/Encode: This button allows for .tsc text files to be decoded (allowed to be edited) and re-encodes them for use in your Cave Story executable.
- Zoom: Changes the size of a map for closer or further examination. This setting goes from 8, 16, 24, 32, 56, and 64 from furthest to closet in that order (with setting 8 displaying tiles in offset colors).

**[Image needed]** *Miza Entity Properties menu (sample 6)*

- Entity Properties menu: This mini-menu allows one to change several properties (rudimentarily speaking).
- Position: This allows for the entity's position on the map to be moved.
    
    It should be noted that one can simply move entities on the map and this feature provides a more defunct version of that function.
- TSC script index: What we better know today as the "Event" button, giving it a certain event will allow for the NPC to be modified in the TSC by other commands.
- Type: Allows for the NPC to be changed in the list with anything from the entire list of NPCs.
- Flag: Changes the associated Flag ID/Entity ID.
- Unknown: Allows for one to input a specific number to give the entity different properties.
    
    In the editor you can see this displayed as "&H51000" which shows how rudimentary this button was, it wasn't well understood back in 2005. To input flags you must properly have knowledge of what flags do what and adding them up, for example NPC 212 has flags 5100: 100 (run event on contact), 1000 (alternate the direction), and 5000 (disappear when flag ID is set).

**[Image needed]** *This is the picture you see after saving Miza and opening the Miza.ini file.*

**[Image needed]** *Miza.ini file after saving once in the editor.*
**[Image needed]** *Save Feature, expanded*
**[Image needed]** *Screenshot 13*

*Space between tile and map editing interfaces.*

Inside Miza's Main interface, you can save your maps, you can only save maps one at a time (so if you edit maps 13 and 14, and save on map 14, any changes made to map 13 will not be saved). It is highly advised you save each map as you're working on them individually before switching to another one.

When viewing the Miza.ini file after saving in the editor once, you will be met with several items:

- State: This loads the editor in 3 modes: 0 loads it in the default window size (approximately 15% of your monitor screen); 1 loads it in a minimized view and clicking on it loads the editor as if it were in state 0; and state 2 loads the editor in full screen.
- Left/Top/Width/Height: Modifies parameters of the window size when loading Miza in states 1 and 2.
- Split: Modifies the size of the space between the Tile interface and the Map Editing interface.
- Zoom: Edits the zoom in and out of the editor in increments of 8, 16, 24, 36, 52, 64 (aka 0, 1, 2, 3, 4, 5).
- Last Stage: This features loads the last saved stage, editing this number will load a stage in the stage order, from 0 to 94.

    Attempting to load anything higher than 94, such as 95 and above, will cause the editor not to load up.
- Entities: Will load a list of all known entities from 2005.

    While there are many gaps (such as entity 4, Smoke, being blank) they still work as intended.
    The list will go all the way down to 359 (Water droplets generator) but it is still missing many entities in-between as well as all of the boss entities.

    Some entities also have odd names, such as entity 235 (Midorin) titled as BMF - presumably "Big Mother-Fucker", and entity 347 (Hoppy) as "Yellow Lobster".


### Scripting interface

The scripting interface has a bit of a preface. To start: you will need to decode the map's TSC file in the Main Menu interface on the right side. Doing so will change the map's file from a .tsc file to a .txt file that can be edited and opened in any standard notepad documenting program such as Window's Notepad that comes pre-installed. Once you make your edits and save your .txt file, you must go back into the program, press the encode button, and all changes will be saved and put in your executable. To find TSC scripts you will need to know the map's internal name and locate the .txt file in the Stage folder in your Cave Story directory.

In the script editing menu, there are no unique features to be had, so for functions pertaining to saving and editing text files will revolve around what program you are using to access the files. All events, commands, and text are done in basic UTF-8 encoding with plain text. There is no way to differentiate if a command was properly inputted correctly or not, nor is there a separate color for commands and their parameters.

Once you are done editing you can just save, and then go back into Miza and re-encode the file as a .tsc file. Doing so will still keep the .txt file but you will need to decode in the editor in order to make changes again that can be saved.

## Features

- The first well documented editor.
- Map editor and Script editing functions.
- The ability to easily overwrite maps with different ones.

## Unfinished/Lacking Features:

- Lack of a sprite editor.
- Lack of a weapons editor.
- Lack of a complete NPC list.
- Lack of correct parallax types.
- Lack of an undo and redo button.
- Lack of more features for creating, moving, and deleting tiles and entities. And an inability to choose multiple tiles at once.
- Lack of an add entities button (as it's relegated pseudo-ly to the "change number of entities" button)
- Unable to change internal map names.
- Proper script automatic decode and encode features.
- Lack of a properties menu (such as game title name, starting map, coordinates, etc...)
- Incomplete Map list.
- The Entities Properties menu being incomplete and not fully knowing what Flags are.
- Unable to change sprite sheets from .pbm to .bmp as well as not being able to remove (C) Pixel requirement.
- Lack of visual view for sprites.

Miza super error (sample 8)
Miza error 2 (sample 9)
## Bugs

One major bug exists in Miza. When exiting out of the Map Properties menu by pressing the X button and not the Ok and Cancel buttons will cause the editor to not only crash but permanently corrupt the map you were editing as well as Miza from being able to load that map. The error you will receive is error `Run-time error: '53':`.

The room you were editing will be forever corrupted as well as loading the stage in-game. You can at least access the other maps in Miza by going into the "Miza.ini" file, going to the "last stage" function, and changing the number to a map that isn't corrupted. For example, if you corrupted map 6, Grasstown, you can set "last stage" to map 5, the Egg Observatory Room.

There is a similar bug that can occur when pressing the X button out of the Entity Properties menu that will cause the editor to crash. But the game and editor will be loadable as if nothing happened afterward. The entity as well will not be corrupted. The error you will receive is error `Run-time error '13':`.
