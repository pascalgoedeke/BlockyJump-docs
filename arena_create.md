# Creating arenas
## Arenas
BlockyJump arenas are basically box-shaped areas containing your parkour course. Your entire parkour has to be inside the arena bounds.  
A player leaving the arena bounds is seen as a fail and will be teleported back to the last checkpoint.  
To create and edit arenas, you need the `blockyjump.admin.arena` permission. ([➜Permissions](permissions.md))  

In the image below, you can see an example arena. It is a good idea to build your parkours floating in the sky, howevery, this is of course not necessary.  
As you can see, you can use **gold blocks** as checkpoints and a **diamond block** to mark the end. This can be customised using [➜ActionSets](action_sets.md).

![Arena Example](_media/arena_example.png ':size=750')

?> Be sure to finish building your parkour before you start to set it up in the plugin.

## Creating a new arena
After putting together the blocks of your parkour, you are ready to actually create the BlockyJump arena.
Each arena has a name, which is the unique identifier.  
You can create an arena in the Admin Arena GUI or by using the following command:

`/bgj admin arena add <name>`

After creating the arena, you automatically enter [➜Arena Edit Mode](arena_edit.md#arena-edit-mode).
