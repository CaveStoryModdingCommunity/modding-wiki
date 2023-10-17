# Cave Editor	


*"Whoa. I like this. In fact, I think you may be giving Sue's Workshop a run for its money."* 
      - Xaser, 2007


Cave Editor is a Cave Story editor created by Wistil. The editor was first unveiled in 2006 and was abandoned in 2010, thus making it abandonware.

Unlike the rest of the legacy modding tools, Cave Editor is entirely stable, additionally supporting external custom resource hacking.

Wistil also provided Cave Editor's source code, which is publicly available [here](http://www.cavestory.org/downloads/CaveEditorSource0.98e.zip).

[Download](http://www.cavestory.org/downloads/CaveEditor0.99d.zip) (Version 0.99d).

[Forum Thread Link](https://forum.cavestory.org/threads/caveeditor-again-beta-maybe-alpha.611/)


## How to use Cave Editor

Despite having a "help" section, the editor unfortunately doesn't come with contents to help explain the editor's functions or assets.

To start, it should be noted Cave Editor has several menus that, unlike its counterpart editor Booster Lab, are all program windows not attached to each other.
For example, you can open the program and be met with the main interface, and from there you can open the map editing interface, and then the script interface one layer deeper if you so desire.
It is capable of opening the script menu from the main interface but entities will not be tracked properly, so it's best advised to open the map interface before opening the script interface if one wishes to most effectively write events and commands.

There are several key features to Cave Editor:

    The Main Menu interface
        Maps
        Tile sets
        Sprite sets
        Backgrounds
        Scripts
        Game Settings window
        NPC Table window
        Data sub-list
        Options sub-list
    The Map editor interface
    The Script editor interface

To start, open Cave Editor, go to "File" subtab, then press "Load", and then search the directory for your desired Cave Story .exe application to modify.
The Main Menu interface

Cave Editor's main interface upon opening the program, the Main Menu interface, lists several features such as maps, scripts, tile sets, and so on. Navigate these menus to access different parts of the editing software.
Cave Editor's Main Menu interface

Inside you'll find 5 main columns to scroll through:

    Maps: Displays the maps of the game's engine in number order. There are already 94 maps in Cave Story and you can add another 48 maps for a total of 142 maps. That is the limit before the game is unable to load more. Below the column are four buttons, "add map", "copy map", "edit map", and "delete map" that all do as follows; you can also perform these actions by right clicking on a map's name, and double clicking will load the map immediately into edit mode.
    Tile Sets: This column shows the list of the game's available tile sets. The "add", "copy", and "delete" tile set buttons do not function, and only edit tile set works. Alternatively you can double click a tile set to open and edit it. In this editor you can reprogram tiles to have specific properties such as a base block, slopes, background and foreground decorations, spikes, and so on.
    Sprite Sets: Shows the list of the game's sprite sheets. Only the edit button works, and you can alternatively double click the item to open and edit. The window inside is a very basic 16 color bitmap editor. There are alternative external programs that can open, edit, and save these sprite sheets more efficiently so this option is generally unfavorable to use as a sprite editor.
    Backgrounds: Just like sprite sheets, shows a list of background that can be edited in a primitive 16 color bitmap sprite editor. The edit button is the only one of the 4 that functions and you can double click an option to open the sprite editor.
    Scripts: Displays 4 scripts that can be loaded at any given time during play (excluding credits.tsc). You can double click on a list to open them or alternatively press the "edit script" button.
        ArmsItem: Displays the script file for all in-game items, weapons, and equipment.
        Credit: Displays the script file for the game's credits that use a different TSC method for writing text in-game.
        Head: Displays the main script file that is loaded at all times alongside the current map's script. This script is used by items such as the Save Point and Refill Station, and is used for all death dialogues.
        StageSelect: Displays the names for the game's teleporter locations.
        Cave Editor's NPC table menu, displays a plethora of information to both edit and view.

Cave Edtior's Game Settings menu.

Cave Editor's "Game Settings" window.
Top-right functionalities

Featured on the top left are 3 special menus that have different functions:

    Game Settings: This menu allows for modification of several variables (shown to the right) such as starting health, title screen map, coordinates, starting event, and starting map. There is also two more options: "Remove (C)Pixel requirements..." and "Image File Extension". Toggle the first option to edit sprite and tile sheets, and change the file extension from ".pmb" to ".bmp" if you have not done so already; this will allow you to start modifying the game's sprite and tile sheets (and saving the sheets as 24 color bitmaps will allow you to use whatever colors you want and not be restricted to the 16 colors limit Pixel's sheets use).

    Edit NPC table: This menu allows for the modification of Cave Story's NPC and displays a plethora of information for both viewing and editing. Here you can change their HP, damage, and experience dropped. You can also edit their properties such as if they pass through solids or are bouncy to walk on (several of these properties are unknown such as Flag 11 - Flag 15). You can also edit their hit box and display box (very primitive system), the tile set they originate from, their hurt and death sound and graphic, and lastly some basic information about their name and description.

    Edit .pbm: This feature will allow you to edit the game's .pbm's from the game's directory that uses a internal 16 color bitmap editor like the tile set, sprite sets, and background menus mentioned prior. Due to the outdated use of .pbm's, this feature can be largely ignored in favor of external editors that can be saved and edited as 24 color bitmaps.

**Data and Options menus**

Featured at the very top of the program are two other subtabs you can open.
CE's Bullet Data menu.

Cave Editor's Bullet Data menu. Featured below it is every weapon in the game's data, ordered, to assist with navigating the menu.

Data: Inside the subtab you'll find three options:

    Reorder Maplist: This feature allows one to reorder the maps that are sequentially numbered. For example, Map 72, u(Kings) is the game's title screen map, but you could reorder this map as map 54.
    Bullet Data: Inside this item is another window. This menu displays information about a weapon that can be modified such as damage, range, experience required to level up, and other properties such as allowing the weapon's bullet to go through walls for example. You can also edit other graphical properties like the offsets. The weapons are ordered by ID number and level. So i.e.: Snake Level 1, Snake Level 2, Snake Level 3, Polar Star Level 1, and so on.
    NPC EXE Data: This menu is view only, but shows the hex values that NPCs have in the game's code: Assembly or ASM.

CE's Map editor options menu

Options: Inside this menu you will find the Map editor interface settings. It has settings such as letting the mouse wheel either zoom or scroll, show zoom size for Maps and their tile sets (default is 1x). And there is an option for tile type display opacity (this item is generally ignored so it's best to be left at the default setting of 128).
The Map Editor Interface
CE's Map Interface, a sample image.

Cave Editor's second interface, the Map editing interface, includes several basic but key features for map modification. To start, a majority of the screen (shown right) is taken up by the map you are currently editing. Approximately ~85% of the interface is taken up by the displayed map. And up top is 4 sub-tabs: Map, Edit, Entities, and Zoom. Each serve a crucial function in moving about a map space and making your stage/room. Directly below that is two main submenus: Display, and Info.

**Map:** Inside this first submenu will include a list of options:

    Shift Map (Crtl + F): This will allow you to shift all tiles of a map simultaneously. You will receive the option to wrap (essentially is tiles that go to the right 10 tiles and hit the border in 5 tiles will re-emerge from the left side 5 tiles over, if not checked the tiles will disappear into the void). You can move tiles a number of X tiles left or right (left with negative numbers i.e.: -1, or right with positive numbers i.e.: 1), and Y tiles up and down (up with positive numbers, or down with negative numbers). If you are unsatisfied with the changes you can press Ctrl + Z or go back to the Shift Map button to shift tiles back. A warning however that this feature is a little buggy and sometimes tiles will disappear, as well entities are not shifted during this process so they will have to be moved manually.
    Edit Script: This button will take you to the Script interface.
    CE's Properties submenu inside the map interface

    Properties: This will lead to another window that does several things:
        Map Name: This is the game's internal map name, this will not be displayed in game and is merely for developer purposes for when you wish to locate your map when modding.
        Caption: This is the name you will see in-game when entering the map.
        Map Size: You can change the map's size X tiles across and Y tiles high. Positive numbers only.
        Background: You can edit the background's scroll type (generally it is an unspoken rule to leave maps with background (excluding background Moon and Fog) with scroll type 1. For Moon and Fog backgrounds you will want to use scroll type 6 or 7. Scroll type 5 is used for the background in the Iron Head boss fight. And scroll type 3, 4, and 8 hide the background.
        Tile Set: Will let you dictate: 1: The Map Tile Set the map tiles originate from. 2: The NPC Tile Sets used. There are 2 NPC Tile Sets since most maps in Cave Story have NPCs and Bosses share tile sets, typically bosses go in NPC Tile Set 2.
        Boss Fight ID: This list is reserved for specific "Room Bosses" which include: Omega, Balfrog, Monster X, the Core, Ironhead, the Dragon Sisters, Undead Core, Heavy Press, and Ballos (his second through fourth phases) respectively. You will still need to set NPC Tile Set 2 for the Room Boss and their ID if used.
    Save (Ctrl + S): Saves any changes made to the map. (If you save from the Script interface while the Map interface is loaded you will need to save from the Map interface again before closing the map).
    Export and Import Map Info: This allows you to export map data and import it between Cave Editors if you so desire to extract a specific map between .EXE's.

**Edit:** This submenu allows you to undo or redo changes recently made. You can also perform the shortcuts Ctrl + Z to undo changes, and Ctrl + Y to redo undid changes.

**Entities:** This submenu allows you to order NPCs in the entities menu by, "Category" (default), "Name" (alphabetically), "ID Number". Following that is the option to delete all entities placed down on the map.

**Zoom:** This lets you zoom in or zoom out the map by 0.5x, 1x, 2x, 3x, and 4x. You can zoom in and zoom out with greater diverse control by setting your mouse wheel to zoom in the Main Menu options window.
CE Map interface Display menu

**Display:** This menu gives modders the ability to tile edit and switch between tile and entity editing. These settings are togglable meanwhile Edit Map and Edit Entities are two buttons you choose between. It should be noted there is no way to make Entity sprites appear in Cave Editor unlike Booster's Lab.

    Edit Map: Puts you on tile edit mode. Edit Entities: Puts you on entity edit mode.
    CE Map interface alternative Display menu but for Entities.

    This menu is an alternative to the Edit Map menu. While on the Edit Map menu all options are togglable. In the Edit Entities menu the Entities sub-option is not un-togglable.
        Front Tiles: Displays foreground tiles.
        Back Tiles: Displays background tiles.
        Background: Displays background.
        Tile Types: Displays the hex value for each tile. (i.e.: Basic blocks have hex value 41, air is typically hex value 0, 50 - 57 are slopes, and so on).
            It should be noted that hex values 80 - 83, and A0 - A3 which are the wind current and water current tiles respectively cannot be seen in the Map editing interface without Tile Types turned on.
        Entities: Displays the entities.
        Entity Text: Displays the text associated with the Entities.
        Entity Sprites: Display entity sprites? (This feature doesn't work).
        Tile Grid: Display a 1x1-tile grid.

CE Map interface Info menu
CE gif showing off the Replace feature

This is the replace button in action, show-casing how replacing one tile of a specific type will replace other tiles like it such as the eye block bit by bit depending on what is clicked.

Info: This menu (when in tile edit mode) gives several options with how to place down tiles.

    Draw: Allows for free drawing as if the mouse were a pen.
    Fill: Encompass all available tiles of the same exact tile with the current tile.
    Copy and Paste: Copy a selection of tiles from the map. Paste allows you to drop down that selection.
    Replace: Grab a tile from the tile sheet, and click on a tile in-map, this will make all tiles of that exact same tile into the new tile.
    Rectangle: Let's one place all selected down in a block like format, starting from the top-left-most block and going down depending on how much is selected.
    Show Tile Set: Does not function


CE Entity menu with an entity in red (as oppose to the unclicked green entities) that can be edited.

The entity in red is what was clicked on and thus can be modified unlike the green entities around it.

Entity: This menu (when in entity edit mode) will allow for modders to modify entities and craft them into the specific NPCs or interactable objects that exist in the game.

    "Entity - X": This will tell you your entity's number, starting from 0. The most important thing to note about this feature is that the limit of entities one can have in a map is 256 existing at once in total (0 - 255). More can be placed down but they will not appear as the entity cap has been reached.
    Entity ID: Known in Booster's Lab as "Flag ID", this feature will allow an entity to have an assigned flag. This works in tandem with Flags 0x0800 (appear once Flag ID is set), and 0x4000 (disappear once Flag ID is set) inside of Flag Details.
        A special note is that NPC 0253 (the exp capsule) drops the number of exp depending on what it's Entity ID is.
    Event #: If an entity is associated with an event or script it must have an associated Event # to be called from. Having multiple entities with the same event will cause the game to choose the entity closer to 0 to be prioritized and interacted with first.

CE interacting with entities

This entity when right-clicked shows specific options such as adding, deleting, and copying an entity. You can also set your spawn location with the right click. This can only be done in entity edit mode.

Flag Details: Displays a list of flags that provide a variety of effects:

    0x0001 - Solid
    0x0002 - Not affected by tile 44
    0x0004 - Invulnerable
    0x0008 - Ignore solid
    0x0010 - Bouncy on top
    0x0020 - Shootable
    0x0040 - Special Solid? (In BL it states this is for Solids with hard sides)
    0x0080 - Rear and top attack power 0
    0x0100 - Option 1 (Used with H/V Triggers)
    0x0200 - Run script on death
    0x0400 - ??? (BL states it is unused)
    0x0800 - Appears once FlagID is set
    0x1000 - Option 2 (This option typically is what you use to flip NPCs or change them to their alternative types, also used with H/V Triggers)
    0x2000 - PC presses down to run script
    0x4000 - Disappears once FlagID is set
    0x8000 - Show Damage Numbers

The Script editor interface
CE's Script editor interface, this is another sample picture showing the script of a map from the original Cave Story.

The script editor is the third and final interface of Cave Editor. It can be opened from either the Main Menu or Map Editor interfaces. This menu stores all of the game's text files in a format called TSC (Text SCript). This page will not go into the list of commands available in Cave Story modding as there should be a separate page for that.
CE Script interface top right, show casing a command in editing.

Shown here is the TRA command and parameters describing what it performs.

The interfaces includes a few sections:

    The main script area: The Script window at full screen takes up ~80% of the window space. This is where you will put your TSC script under event numbers (i.e. #0200). Any and all events must have <END commands so as to avoid events jumping randomly to events down below. The script will run objects are interacted with and when NPCs trigger events (such as NPC 0046, the H/V Trigger).
    Check Syntax: This button will tell you where in your script errors are, such as if you fail to complete a command.
        i.e.: <FAIXXX (the error made is not putting in 4 digits where the X's are supposed to be).
    Save: Saves the script.
    Close: Closes the script, it will ask if you want to save your work before closing.
    Hide Details: Hides the right bar that continues extra information about commands selected and the command list. It can be toggled so to disappear and reappear on press.
    Available Commands: Displays a list of commands that are used in Cave Story.
    The top right of the Script interface: The interface has several parts to it. There will be the command, a description, and then script details showing several parameters such as event number, a number, a direction, or NPC number (An example is shown right).

Features

    Unique UI interface.
    Built-in sprite editor for tile sets, NPCs, and backgrounds.
    Compatible with Booster's Lab.
    Comes with a tile set hex value editor, map editor, script editor, NPC table, weapon data editor, and more changeable game settings.
    Has a command list that shows what commands do as well as having a prompt that explains explicitly what ever command does with each parameter.

Unfinished/Lacking Features

    Main Menu interface:
        Save and Test feature doesn't work.
        NPC EXE Data (as it's read only and not modifiable) isn't changeable.
        The contents tab in the help subtab doesn't work.
        Add, copy, and delete features for Tile and Sprite sheets, and backgrounds do not exist.
        Explanations for flags 11 - 15 in the NPC table are not present.
        Edit *.pbm feature is outdated.
    Map editor interface:
        Unfinished feature to show entity sprites.
        Show tile set button doesn't work.
        Wind and Water current tiles not being present unless in the Tile Types view mode.
        Export and Import map features do not work.
    The editor lacks an interface that allows for hacks and new hex patches to be installed.
    Bullet Data editor doesn't have fleshed out options to change weapon sounds and sprites.

CE Map Name bug and its fix
Bugs

    There is a bug with changing the Map Name (not the Caption) in the Map editing interface's properties menu. If you edit the Map Name in the Map interface properties' menu the data you will not be able to save the map as the game will not know what to locate; to fix this bug you will need to return to the Main Menu interface, right click the map, go into properties, and rename the Map Name the EXACT name you gave it when in the Map interface. You will not be able to load the map again or edit the map's script until you resolve the issue as listed above.
        Shown to the right is an example of this bug in action. If you change the Map Name in the Map editor interface, it will cause the map to become inaccessible. Once you go back to the Main Menu interface and rename the Map Name exactly as you did in the Map editor interface, the bug will be fixed and you can enter the map again.
    There is a bug in Cave Editor that can close the Script editor interface from the Map editor interface if you click on the Map editor interface several times from the desktop task bar. This issue cannot be fixed so do your best to avoid clicking the Map editor interface from your taskbar if your Script editor interface is already in use. This issue only closes the Script editor but any unsaved changes however will be lost.
