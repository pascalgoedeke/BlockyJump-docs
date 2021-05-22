# Arenas
BlockyJump arenas are basically box-shaped areas containing your parkour course. Your entire parkour has to be inside the arena bounds.  
A player leaving the arena bounds is seen as a fail and will be teleported back to the last checkpoint.  
To create and edit arenas, you need the `blockyjump.admin.arena` permission. ([➜Permissions](permissions.md))

?> Be sure to finish building your parkour before you start to set it up in the plugin.

## Creating arenas
After putting together the blocks of your parkour, you are ready to actually create the BlockyJump arena.
Each arena has a name, which is the unique identifier.  
You can create an arena in the Admin Arena GUI or by using the following command:

`/bgj admin arena add <name>`

After creating the arena, you automatically enter [Arena Edit Mode](#arena-edit-mode).

## Editing arenas
To edit an existing arena or to setup a newly created arena, BlockyJump offers the **Arena Edit Mode**,
which provides you with a set of tools to easily configure your arena in-game without the usage of commands.  
You can enter Arena Edit Mode by using the following command:

`/bgj admin arena edit <name>`

You automatically enter Arena Edit Mode after creating a new arena.

### Arena Edit Mode
To configure your arena, the Arena Edit Mode provides you with a set of tools:

1. **Arena Bounds**: Arenas are basically just boxes. To set the boundaries of your arena, use the axe to click on the block in one corner,
then go to the opposite corner and click on the other corner block. Your arena is now set to be inside this cuboid.  
2. **Start Position**: To select the starting position where the player is teleported in the beginning of a game, stand in the exact position
you want your players to teleport to and perform a click with the stick.  
3. **Portal**: You can create a portal for players to easily join your parkour. A portal has particles around it and displays the arena's
leaderboard in the form of a hologram right above. Stand on the block where you want the portal to be and perform a click with the blaze rod.
To remove the portal, simply click again. It is not necessary to have a portal.  
4. **Done**: To leave Arena Edit Mode when you are done, click the emerald. If you leave Arena Edit Mode without having set the required settings
in a newly created arena, the arena will not be created.  

