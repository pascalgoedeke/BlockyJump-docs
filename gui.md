# GUI
BlockyJump includes an easy-to-use GUI for both players and admins. That way, you (almost) don't have to remember any commands and save time.  
It's designed to be intuitive and if you ever struggle, there's inbuilt help. The GUI will only display options the player has permission to. ([➜Permissions](permissions.md))  
To open the main menu GUI, simply use the command:  

`/bgj`

You can directly open specific pages by using one of the following commands: ([➜Commands](commands.md))  

`/bgj join`  
`/bgj challenge`  
`/bgj stats`  
`/bgj admin`  
`/bgj admin arena`  
`/bgj admin lobby`  
`/bgj admin setup`

?> If you want to link this GUI to an existing GUI-system, there is a command to force-open the GUI to a player:  
`/bgj open <player>` *(This command doesn't (yet) support specific pages)*

## Usage
In case you have never used a Minecraft plugin GUI before, here is a little explanation how to use it:  
GUIs are simply **inventories**, just like the player's inventory or the inventory of a chest. You can imagine these inventories as **windows**.  
The plugin then places **items** inside of these inventories with act as **elements** of a specific window.  
Each window has its own set of items in it. These items can give you **information** (hover over them to see the text) or act as **buttons**.  
To interact with a GUI, simply **click on an item** and the associated action will be triggered.  
GUIs make it a lot easier to work with a plugin, as you don't need to remember all the commands. Pretty cool, huh?  

?> **Tip:** BlockyJump-GUIs always have a sign in the upper right corner. This sign always shows a **help message** for the page you are on.

If you are worried about players using the GUI inventories to cheat, don't worry. You can't take items out of the GUI or deposit any items in it.

## Features
![GUI Features](_media/gui_features.png ':size=1000')
