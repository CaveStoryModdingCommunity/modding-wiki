# Sue's Workshop


<fieldset>
<legend>Sue's Workshop:</legend>
<img src="/wiki/img/SW_icon.png">
<table><tbody>


<tr><td>Creator(s):</td><td>ProfEich</td></tr>
<tr><td>Year:</td><td>2006</td></tr>
<tr><td>Platform:</td><td>Windows</td></tr>
<tr><td>Status:</td><td>
<p style="color:#B00000;">Deprecated</p>
</td></tr>
<tr><td>Info:</td><td><a href="https://forum.cavestory.org/threads/sues-workshop-finally-a-new-version.351/">Original Forum Thread</a></td></tr>


</tbody></table>
</fieldset>


<br></br>


  >*"4) Fix SW's compatibility issues with CE."* - Andwhyisit, 2009"




<p style="color:#B00000;"><i>Note: It is <b>Not</b> recommended to use Sue's workshop for Cave Story modding in any capacity! The program can and will corrupt your cave story executable, especially if used in tandem with other <a href="cavestory-editors">editors</a>. The page and instructions are still here for archival purposes only.</i></p>


**Sue's Workshop** is a defunct tool created in 2006 by **Benjamin Schulte**, also known as **ProfEich**. The tool was abandoned in 2007, and updates were planned to be released by ex-CSTSF admin S.P. Gardebiter but this new version never came to fruition.
The tool was also packaged in the old version of the "Cave Story Deluxe Package" on the Tribute Site.




[Download](https://www.cavestory.org/downloads/Editor0.3A.zip) *(Version 0.3A).*


[Forum Thread Link (ProfEich)](https://forum.cavestory.org/threads/sues-workshop-finally-a-new-version.351/) *(Download link on the page doesn't work.)*


[Forum Thread Link (S.P. Gardebiter)](https://forum.cavestory.org/threads/sues-workshop-new-version-in-development.1592/) *(It should be noted this thread leads to the "New Version" thread started by S.P. Gardebiter. This thread is added for archival purposes.)*


## How to use Sue's Workshop


Sue's Workshop has a few primitive tools and key features that make it a useful program for modifying maps and scripts from the original Cave Story. It should be noted to begin that because of the nature of Sue's Workshop the editor has been considered largely outdated and out-performed by more fleshed out editors such as Cave Editor and Booster's Lab. Sue's Workshop is an acceptable editor for vanilla Cave Story but the editor has been known to corrupt mods with custom tilesets as well as having compatibility issues with Cave Editor and Booster's Lab, editors that are compatible with each other.


When you open the editor, press the File subtab, Load Game, and then click on your desired executable to load up. Only vanilla Cave Story executables that have not been touched by Cave Editor and Booster's Lab and executables without custom tilesets will load properly.


Inside the program once loaded will show the Main interface, and from there you can access other subtabs, the Map editor interface, and the Script editor interface.
Sue's Workshop Main interface Sample 2
### The Main menu interface


In the Main interface of Sue's Workshop is where you will perform your work and open other menus to access different features. There are four sub tabs up top and the list of stages. *(Each bullet layer represents its respective layer in the UI)*


* **File:** This subtab will be the first button you press when you begin a modding session.
    * **Load Game:** This button will let you choose the executable you wish to load.
    * **Commit Changes:** In a similar vein to Resource Hacker, this button will allow for you to finalize all changes made to maps, scripts, and other features. Unfortunately this feature is redundant due to all save features in Sue's Workshop saving all changes regardless of where you save.
    * **Quit:** Closes the editor. The editor will ask if you want to save any unsaved changes first however.


* **Tools:**
    * **Tile set editor:** This feature allows you to change the hex value of tiles in tile sheets. Due to the limitations of knowledge at the time, only a select handful of tiles were documented in SW.
        * **Tiles that were documented were:** `0, 1, 2, 5, 40, 41, 42, 43, 46, 50, 51, 52, 53, 54, 55, 56, 60, 62, 70, 71, 72, 73, 74, 75, 76, 77, 80, 81, 82, 83, A0, A1, A2, A3, and FF.`
            The feature had one quirk in that you could select and modify multiple tile hex values at once.
    * **SW's game settings feature:**
        * Game Settings: The setting's button is very limited compared to other editors, only allows for the game's window name caption to be changed, as well as the starting event (default is 200).


* **Run:** This feature simply ran the game from the editor without having to close out of it, allowing for changes to be made more quickly in the editor.
 
* **Help:** This option shows some basic ‘about’ information for the editor. There is a contact email for ProfEdich as well as the promise of a homepage for the editor coming soon. The email link does not work anymore and the homepage never was released.
* **Game Objects:** Also known as the stage list, this area to the left of the editor's Main Menu interface displays the list of stages in Cave Story in numerical order. At the very bottom is also a list of 4 main scripts, the Head, ArmsItem, StageSelect, and Credits TSC files:
    * **Scripts:**
        * **Head:** Displays the main script file that is loaded at all times alongside the current map's script. This script is used by items such as the Save Point and Refill Station, and is used for all death dialogues.
        * **ArmsItem:** Displays the script file for all in-game items, weapons, and equipment.
        * **StageSelect:** Displays the names for the game's teleporter locations.
        * **Credit:** Displays the script file for the game's credits that use a different TSC method for writing text in-game.


**[image needed]** *SW Map editor interface sample image, showing multiple maps loaded*
### The Map editor interface


Upon loading a map you will be greeted with another window for the map that you can zoom in or zoom out. There are several handy features with the Map editor that allow for ease of access across multiple maps and utilizing their windows:


**The Window:** Sue's Workshop's window sports a decently robust editor: with the ability to load multiple maps at once, allowing for an increased efficiency if one wishes to cross reference the design of several maps or needs to find the opening/exit to a TRA command. These windows can be minimized and kept at the bottom of the tray for later use. The windows can also be expanded outside of the workspace, adding scroll bars and giving once more space to move around their workspace-collage of maps waiting to be edited. It should be noted however that the 3rd mouse button and scroll wheel do not achieve any functions in the Map Editor interface. At the bottom of the page, your cursor's coordinates and information on entities will be displayed when hovered over (the latter only on Entity edit mode).


Inside the Map editor interface are several options at the very top that lead different functions:


* **Additional Map Functions:** This dropdown presents three options.
    * **Clear Map:** Clears the map of both entities and tiles, wiping it fresh.
    * **Resize Map:** This feature will let you increase the size of a map by X tiles left and right, and Y tiles up and down; alongside this is a "Update Map" button. This feature also comes with a D-Pad if one wishes to fine-tune their exact resize changes that auto-updates as you press the buttons.
    * **Shift Map:** This feature will move all tiles on the map by a specified number of X tiles left and right, and Y tiles up and down (using negative numbers for left and up, and positive numbers for right and down directions). This feature also comes with a D-Pad that serves a similar function as it did in the Resize Map tool that auto-updates as you press the buttons.
    * **Save Map:** This button saves all modifications whether it is tile edits or entity edits.


**[image needed]**
*SW's tile set sheet, with an elongated sub-window*


After this the editor has two modes for editing tiles and entities.
* **Map Edit Mode:** Switches the editor to edit tiles only.


    Inside this Map Edit mode, only tiles can be edited and right below the sub tabs will be your tileset sheet. This sheet's sub-window can be lengthened up and down to accommodate your needs.
* **Pen Mode:** This tool will allow you to put tiles on the map like a paintbrush on the canvas.
* **Rectangle Mode:** A more meticulous tool that allows you to place down specific rectangles of objects from the tile sheet.


    **[image needed]** SW gif showing the difference between tile and entity edits


    *Shown here is the difference between tile edit and entity edit mode. Tile edit has the pen and rectangle modes, meanwhile entity edit has add one and many NPCs, as well as edit entities.*


* **Entity Edit Mode:** Switches the editor to edit entities only. In this mode entities will be displayed with their event number, but there is no numbered limit, meaning modders will not know if they've hit the entity cap (of 255) without manually counting. As well, entities are highlighted with a white square, and entities with FlagID's will be highlighted yellow.


    This mode will allow you to only edit entities, their properties, and positions. You can also right click the map to move an entity to the back or front of a stack of entities. You cannot check the entities individually in a stack, only whatever is in the front. These stacked entities will have red lettering and the number of entities in the stack (i.e.: "2x" for 2 entities).
    When clicking on an entity you can perform several actions:
    * **Event:** This lets you dictate an entity's event number if they need one.
    * **Sprite:** This basic option lets you choose what NPC the entity becomes. This feature is extremely basic compared to other editors and requires the exact sprite number.
    **[image needed]** SW Flag/FlagID window, it's very basic.


        * **Flags and FlagID:** The parameters an entity takes on, can be edited in the Edit Flags section.
        * **Z:** This button resets the Flags and FlagID parameters.
        It should be noted inside the Edit Flags window that this feature was most likely not well known back when editors like SW and Miza were being created. And thus, SW only has a couple flags that can be edited, to its credit these flags are the primary flags used by most entities in Cave Story.
        This list will provide the flag names and their Cave Editor counterparts:
            * **Call >Event< on action:** Flag 2000 (PC Presses down to run script)
            * **Flag 0x1000:** (Option 2)
            * **Unknown 0x200 flag:** (Run script on death)
            * **Flag 0x0100:** (Option 1)
            * **NPC is invisible if >FlagID< is set:** Flag 0x4000 (Disappears once FlagID is set)
            * **NPC is visible if >FlagID< is set:** Flag 0x0800 (Appears once FlagID is set)
            * **FlagID:** Here, you input the FlagID you wish for your entity to have. This setting affects how flags 0x0800 and 0x4000 work, and for entity 253 (EXP Capsule) will determine the experience points dropped.
    * **Add only one NPC:** When you click on the screen with this feature, it will place down a single entity. This feature will place down a null entity with clean statistics. If you've previously clicked on another entity, the editor will copy that entity entirely when placing a new one. Once you do, the editor will return to Select-move-and-delete-NPCs mode.
    * **Add many NPCs:** This feature will place down multiple entities and will not return to Select-move-and-delete-NPCs mode until you switch back manually. This feature will allow you to place down multiple entities that are null (or copied the previously selected entity).
    * **Select move and delete NPCs:** This is the basic edit mode, you can move around NPCs and check on their flags and events, modifying them as you see fit.
    Edit map script: This button enters the Script interface.


**[image needed]** SW's Script interface on top of the Map interface.


### The Script interface


The third and final interface of Sue's Workshop, this feature exists on its own window, but its size can be toggled and minimized to share its space with your other maps and scripts on your workspace. The Script interface's layout is very basic and doesn't provide any other features besides script editing. Unlike its contemporaries, CE and BL, there is no command list nor prompts to assist modders on how to set up commands, so much of your work will be guesswork or copying commands and lines from other lines without proficient understanding.


When right-clicking, basic undo (no redo), select all, cut, copy, paste, and delete functions are present, something Cave Editor and Booster's Lab do not have. You can also open IME (Input Method Editors) but it does not seem to function. As well, buttons for showing and inserting Unicode characters, as well as "reconversion" under IME have not been implemented and only exist as placeholders in the right-click menu. You can also change the script to be read right-to-left instead of the usual left-to-right, a feature unique to SW.


The Script editor interface has a very basic layout, no extraneous functions or features exist, and the format does not warn modders of text boxes trailing outside the 26 to 35 character limit nor warns them of commands not being inputted properly. The interface's background and text color are also close to one another, and with no variation in command and text colors, figuring out what to edit can be confusing and one can lose track of where they were fast.


* Save Script: The only button in the Script editor interface. It saves the current script regardless of syntax and changes made.


## Features


* Has functionality to run the game from the editor.
* Comes with a tile set hex value editor, map editor, and script editor.
* Script editor comes with the ability to be read right-to-left. Scripts also load much more quickly.
* Comes with the ability to reset Flags and FlagID on an entity with the press of a button.


## Unfinished/Lacking Features


* Editor is not compatible with Cave Editor and Booster's Lab.
* Main Menu interface:
    * Lack of editable game settings such as starting health and coordinates.
    * Lack of all available hex values in the tile set editor.
    * Lack of a sprite editor for both tiles and NPCs.
    * No guide to help navigate the editor in the Help subtab.
    * No text file that allows for changes to be made to settings and features.
* Map editor interface:
    * Lack of all Flags in the Flag/FlagID menu.
    * Unable to check all entities in a stack at once.
    * Tile edit mode not providing a tile types view mode.
* Script editor interface:
    * Lack of a command list or descriptions for commands.
    * No syntax check.
    * Lack of colors to help differentiate between commands, events, and text.


## Bugs (Compatibility issues):


SW but the exe is corrupted.


The editor doesn't have many notable bugs due to its lack of features, so few errors will show up if at all.


Sue's workshop has been infamous for having compatibility issues with other editors like Cave Editor and Booster's Lab.
Even if you make no changes, if you save once in CE or BL, the exe will not load in SW. The exe will be permanently corrupted if opened in SW and then attempted to be re-opened in another editor.




