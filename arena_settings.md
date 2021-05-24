# Changing arena settings & rewards
To spice up your arenas you can setup challenges like a maximum amount of fails and a lot more. You can also reward the player for completing the parkour.  
The settings can easily be changed in the Admin Arena GUI. Alternatively, you can use the given commands.

## Enabling and disabling of arenas
Arenas can be disabled if you don't want players to be able to join them, i.e. when you are changing up the parkour.  
You also need to enable newly created arenas as they are disabled by default.  
To enable or disable an arena, you can click on the corresponding item in the Admin Arena GUI or use one of the following commands:

`/bgj admin arena enable <arena>`
`/bgj admin arena disable <arena>`

## Cooldown
If you don't want your players to be able to complete the parkour several times in a row (maybe to prevent them from recieving the reward several times in a row), you can setup a cooldown.  
A cooldown is essentially a waiting timer to join again once an arena is completed. The cooldown length is given in **minutes**.

`/bgj admin arena cooldown set <arena> <time>`
`/bgj admin arena cooldown remove <arena>`

## Maximum time and fails
To make your arenas a lot more challenging, you can setup a maximum amount of fails, a time limit or even both.  
Once a set maximum is exceeded, the game is lost. If a maximum is set, it is shown on the scoreboard during a game. The time limit is given in **seconds**.

`/bgj admin arena max set time <arena> <time>`
`/bgj admin arena max remove time <arena>`

`/bgj admin arena max set fails <arena> <fails>`
`/bgj admin arena max remove fails <arena>`

## Rewards
If you want to, you can reward the player for finishing a parkour. Currently, you can set a command that will be run once a player finished the parkour.  
You may use *%p%* as a placeholder for the player name. Make sure to leave out the beginning slash!

`/bgj admin arena reward set cmd <arena> <cmd>`
`/bgj admin arena reward remove <arena>`

Example:  
`/bgj admin arena reward set cmd Arena give %p% diamond`

!> The reward system will be extended in a future update.
