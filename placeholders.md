# Placeholders <!-- {docsify-ignore-all} -->
This plugin supports PlaceholderAPI placeholders. If you want to use them, make sure you have PlaceholderAPI installed on your server. [➜Download on SpigotMC](https://www.spigotmc.org/resources/placeholderapi.6245/)  
If you can spot a message like `[PlaceholderAPI] Successfully registered expansion: bgj` in the console while your server is starting, BlockyJump is successfully linked to PlaceholderAPI.

## Placeholders on an arena's top ten players
Currently, you can display the player name, time and fails of an arena's top ten players using:

```
%bgj_<arena_name>_<1-10>_<player|fails|time>%
```

Example: `%bgj_MyArena_2_time%` - converts to the second best time of MyArena

## Placholders on a player's best game in an arena
Additionally, you can display the time and fails of the player's best game in an arena using:

```
%bgj_<arena_name>_player_<fails|time>%
```

Example: `%bgj_MyArena_player_fails%` - converts to the amount of times the player failed in its best game of MyArena

<br/><br/>

?> Did you know that BlockyJump includes a leaderboard hologram? You don't need to build one yourself! [➜Portals](arena_edit.md#arena-join-portals-and-leaderboard-holograms)
