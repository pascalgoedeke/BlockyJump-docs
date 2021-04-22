# Setup
This page contains instructions on how to setup the plugin. The process is really simple. Feel free to skip the sections that are not relevant for you.

?> If you haven't downloaded BlockyJump already, do so over on [SpigotMC]().

<!-- Quick start? -->

## Installation
To install the plugin, simply locate your /plugins folder and drop in the plugin's `.jar` file.  
Start your server and BlockyJump should be up and running.  
All the necessary files will be automatically created in the /plugins/BlockyGamesJump folder.

!> If your server is running, you might want to stop it first in order to install plugins as reloading might cause data leaks.

## Initial setup
When you join your server with basic admin permission `blockyjump.admin.basic` ([➜Permissions]()) or as an operator, you will be notified to perform the initial setup.

`/bgj admin setup`

![Initial Setup GUI](_media/initial_setup_gui.png ':size=1000')

This command will open the Initial Setup GUI which will help you to setup the plugin.  
1. First of all, you need to **set a lobby location**. Stand where you want your lobby to be and click the icon in the menu. Players can be teleported back to the lobby after a game. ([➜Lobby]())  
2. The second thing you want to do is **create an arena**. Simply click the icon and follow the instructions. ([➜Arenas](arenas.md))  
3. Optionally, you can now take a look at the following topics of this documentation.  
4. Lastly, you want to **enable the plugin**. This allows your players to play games and marks the setup as complete.

You can open the Initial Setup again at any time, by clicking the corresponding icon in the normal Admin Setup GUI.  
If you don't want to use the GUI, there are written instructions and the corresponding commands.

![Initial Setup Instructions](_media/initial_setup_instructions.png)

!> Make sure you enable both your newly created arena and the plugin itself! The plugin needs to be enabled before games can be played.

## Database storage
By default, BlockyJump uses a local SQLite database located in the plugin's folder called `data.db`.  
If you want to use a MySQL database, you can do so by specifying the connection in the `config.yml`.

```yaml
database:
  selected: local
  table: stats
  mysql:
    url: mysql://localhost:3306/database?useSSL=false
    user: root
    password: ''
```

Replace `localhost` with your database server ip or domain and `database` with your database name. Also specify the user credentials that you want the plugin to login with. Then, replace `local` with `mysql` at the top.  
You can also change the table name that is used to create a statistics table by editing the option `table`. Please not that changing the table name or the selected database **will not copy any existing data** to the new storage location.

## Configuration File
The plugin's settings are saved in the `config.yml` file located in the plugin's folder. You don't really need to edit the file itself as there are commands to edit each setting. ([➜Commands]())

Default configuration:

```yaml
version: '2.2'
language: en
database:
  selected: local
  table: stats
  mysql:
    url: mysql://localhost:3306/database?useSSL=false
    user: root
    password: ''
enable: false
random_arena: false
lobby:
  x: ''
  y: ''
  z: ''
  yaw: ''
  pitch: ''
  world: ''
  teleport: false
particles: true
```

| keys in config.yml                                             | default value                                | possible values                                      | description                                                 |
|----------------------------------------------------------------|----------------------------------------------|------------------------------------------------------|-------------------------------------------------------------|
| version                                                        | {current version}                            | **do not change!**                                   | config version                                              |
| language                                                       | en                                           | en, de, [your custom languages]                      | selected language file                                      |
| database.selected                                              | local                                        | local, mysql                                         | selected database connection                                |
| database.table                                                 | stats                                        | [custom]                                             | database table name                                         |
| database.mysql.url                                             | mysql://localhost:3306/database?useSSL=false | mysql://[host]:[port]/[database]?useSSL=[false/true] | MySQL connection url including host, port and database name |
| database.mysql.user                                            | root                                         | [custom]                                             | MySQL user name                                             |
| database.mysql.password                                        | ''                                           | [custom]                                             | MySQL user password                                         |
| enable                                                         | false                                        | false, true                                          | enable plugin                                               |
| random_arena                                                   | false                                        | false, true                                          | choose random arena if none is specified                    |
| lobby.x, lobby.y, lobby.z, lobby.yaw, lobby.pitch, lobby.world | ''                                           | [custom]                                             | lobby location                                              |
| lobby.teleport                                                 | false                                        | false, true                                          | always teleport players to the lobby after every game       |
| particles                                                      | true                                         | true, false                                          | spawn arena join particles                                  |

## Messages and Localisation
Almost all the messages that are used in BlockyJump are editable. The plugin also supports multiple languages. English (`messages_en.yml`) and German (`messages_de.yml`) are included out of the box.  
You can select the language you want to use by specifying it at `language` in the `config.yml`. English is used as the fallback language.

To create your own translation, copy one of the existing messages files. Rename it to `messages_[language].yml` where you replace `[language]` with the language this file will contain.  
Example: `messages_fr.yml` (or `messages_french.yml` if you prefer this format)  
Then, translate all the existing messages to your language.  
To select your language, again, open the `config.yml` and paste whatever you chose for `[language]` as a value to the key `language`.

<button title="Click to show or hide content" type="button" style="cursor: pointer; background: white; border: 0.125em solid black; padding: 0.5em 0.75em; color: black; font-family: var(--siteFont),Helvetica Neue,Arial,sans-serif" onclick="if(document.getElementById('spoiler-messages-en') .style.display=='none') {document.getElementById('spoiler-messages-en') .style.display=''}else{document.getElementById('spoiler-messages-en') .style.display='none'}">Show default messages_en.yml</button>
<div id="spoiler-messages-en" style="display:none">

```yaml
plugin:
  prefix: §f§l[§3§lBlockyJump§f§l]§r
  header: §3--------- %p%§b by leberwurst88§7 v%v%§3 ---------
  enabled: §aPlugin enabled
  disabled: §cPlugin disabled
  no_permission: §cNo permission
  wrong: §cSomething went wrong
  error_gui_triggered: §cError GUI was triggered, something went wrong in %c%
  patcher:
    noticed_update: §eNoticed update from older version, patching changes if necessary
    patched: §aPatched changes of version %v%
  update:
    check_failed: '§cCould not check for updates: '
    check_cancelled: §cUpdate checker was cancelled
    available:
      console: '§cNew update available, please update to v%v% of this plugin on SpigotMC:'
      player: §4[⚡] §cPlease update to §7v%v%§c on SpigotMC §4[⚡]
    automatically: §cA minor update is available, updating automatically...
    download:
      create_folder: §cCouldn't find nor create /plugins/update folder
      downloading: §eDownloading updated plugin file...
      failed: '§cDownload has failed:'
      completed: §aDownload completed, restart server to update plugin
  link:
    click: Click to open
  quit_could_not_leave: §cQuitting player couldn't leave game
config:
  messages:
    ready: §aMessages ready (%l%)
    failed: §cMessages config failed (%l%)
  ready: §aConfig ready
  ready_setup: §aConfig ready, §csetup needed
  failed: §cConfig failed
  arena:
    ready: §aArena config ready
    failed: §cArena config failed
  reloaded: §aFiles reloaded
db:
  sqlite:
    ready: §aLocal database ready
  mysql:
    ready: §aMySQL database ready
placeholderapi:
  enabled: §aPlaceholderAPI enabled
  no_data: no data
player:
  already_playing:
    you: §cYou are already in a game
    player: §cPlayer is already in a game
  not_found: §cPlayer could not be found
  not_in_game:
    you: §cYou are not in a game right now
    player: §cPlayer is not in a game
console:
  cannot_join: §cConsole can't join game, try /bgj join <arena> <player>
  cannot_leave: §cConsole can't leave game
  cannot_challenge: §cConsole can't challenge a player
  cannot_edit: §cConsole can't edit arenas. §3Try creating a new one with §b/bgj admin
    arena add <name> <pos1_x> <pos1_y> <pos1_z> <pos2_x> <pos2_y> <pos2_z> <spawn_x>
    <spawn_y> <spawn_z> <world>
  cannot_set_lobby: §cCannot set lobby location from console, try §b/bgj admin lobby
    set <x> <y> <z> <world>
  cannot_teleport:
    checkpoint: §cConsole can't teleport to checkpoint
console_cannot_teleport:
  lobby: §cCannot teleport console to lobby, try /bgj admin lobby get
arena:
  none:
    general: §cThere are no arenas yet
    admin: §cThere are no arenas yet, use /bgj admin arena add to create one
  specify: '§cSpecify arena: /bgj join <arena>'
  list:
    header: '§6BlockyJump arenas:'
    entry:
      general: §7- §3%n%
      enabled: §7- §a%n%
      disabled: §7- §e%n%
  already_enabled: §cThis arena is already enabled
  enabled: §aArena %n% is now enabled
  already_disabled: §cThis arena is already disabled
  disabled: §aArena %n% is now disabled
  exists: §cThis arena name already exists
  added: §aBlockyJump arena §e%n%§a added
  enable: §3Enable arena in the GUI or by typing §b/bgj admin arena enable %n%
  removed: §aArena removed
  reward:
    cmd:
      set: §aReward command set
      removed: §aReward command removed
  maximum:
    fails:
      set: §aMaximum amount of fails set
      removed: §aMaximum amount of fails removed
    time:
      set: §aMaximum time set
      removed: §aMaximum time removed
  cooldown:
    set: §aCooldown timer set
    removed: §aCooldown timer removed
game:
  joined: §aJoined game
  checkpoint:
    set: §6Checkpoint set
    teleported: §aTeleported to checkpoint
  hider:
    hidden: §aPlayers hidden
    shown: §aPlayers shown
    nothing: §eNothing happened
  arena:
    not_found: §cThis arena doesn't exist
    disabled: §cThis arena is disabled
  won:
    congratulations: §6Congratulations, you won the game!
  lost:
    player: §cYou lost the game!
    over: §6The game is over!
    winner: §aThe winner is §6%w%
  end:
    stats: '§3Time: §b%t%§3 Fails: §b%f%'
  left: §aLeft game
  not_ready: §cPlugin not ready
  wait: §cWait %t% before playing again
  command_not_allowed: §cThis command is not allowed in the arena. To leave, type
    /bgj leave
challenge:
  already_challenged: §cYou already challenged this player
  challenged: §3%p% §6challenged you in Arena §b%a%
  options: '§7Your options: §b/bgj challenge accept§7 or §b/bgj challenge decline'
  sent: §aChallenge sent, waiting for answer
  player:
    accepted: §a%p% accepted your challenge
    declined: §c%p% declined your challenge
  accepted: §aChallenge accepted
  declined: §aChallenge declined
  no_challenges: §cYou don't have any pending challenges
  cannot_challenge_yourself: §cYou can't challenge yourself
time:
  stopwatch:
    hours: '%h% h, '
    minutes: '%m% min, '
    seconds: '%s% sec'
hologram:
  portal:
    arena: §l§6✦ %a% ✦
    type: §a▼ Classic Parkour§7 - §aJoin here ▼
    leaderboard:
      head: §7+----- §bLeaderboard§7 -----+
      line: §e#%n% §6%p%§7 in §a%t%§7 with §c%f% fails
scoreboard:
  arena:
    head: '§7» Arena:'
    line: §b%n%
  timer:
    head: '§7» Timer:'
    line: §b%t%
  timer_max:
    line: §b%t%
  fails:
    head: '§7» Fails:'
    line: §b%f%
    timeout: §cTime out
  fails_max:
    line: §b%f% / %m%
item:
  game:
    checkpoint: §2Checkpoint
    hide: §2Hide Players
    leave: §cLeave
  edit:
    bounds: §2Arena Bounds
    spawn: §2Set Spawn
    portal: §2Set Portal
    finish: §2Finish
stats:
  personal:
    header: §7------ §f§l[§3§lStats§f§l] §b%p%§7 ------
    amounts: '§3Games played: §b%p%§7 - §3Won: §b%w%'
    list: §7- §3%n%§7 in §b%t%§7 with §b%f%§7 fail(s)
    console_does_not_have: §cConsole doesn't have personal stats, try §b/bgj help
      stats
  server:
    no_data: §cNot enough data, try again later
    header: §7--------------- §f§l[§3§lStats§f§l] §bServer§7 ---------------
    most:
      played: '§3Most games played: §b%p% (%a%)'
      won: '§3Most games won: §b%p% (%a%)'
    list: '§7- §3%a%: §b%p%§7 in §b%t%§7 with §b%f%§7 fail(s)'
  arena:
    header: §7---------- §f§l[§3§lStats§f§l] §b%a%§7 ----------
    list: §7%i%) §3%p%§7 in §b%t%§7 with §b%f%§7 fail(s)
help:
  list:
    header: §3---§7[%i%]§3--- %p%§b by leberwurst88§7 v%v% §3---§7[%i%]§3---
    entry: §3%c% §7%d%
    footer:
      cmd: §3------------------- §b/bgj help %p%§3 -------------------
      end: §3--------------------------------------------------
  single:
    cmd: §3§l%c%
    description: §7%d%
    footer: §3-------------------- §7/bgj help§3 --------------------
  options: §3%c%§b%o%
  no_content: §cNo content
  for_help: §7For help, type §b/bgj help
  not_found: §cCommand not found, try §b/bgj help
  displaying: 'Displaying help:'
edit_mode:
  instructions:
    line:
      '1': '§3Instructions:'
      '2': §7- Left click with §bgolden axe§7 on two boundary blocks to §bselect arena
      '3': §7- Stand where you want the §barena spawn§7 to be and left click with
        §bstick
      '4': §7- If you want to set a §bportal§7, stand where you want it to be and
        left click with §brod
      '5': §7- Click the §bemerald§7 once you're §adone
  bounds:
    set: §aArena boundaries set
    first: §aFirst position set, select second position
  spawn:
    set: §aSpawn set
  portal:
    disabled: §aArena portal disabled
    set: §aJoin portal set
  finished: §aArena setup finished
  cancelled: §cArena setup cancelled
setup:
  finish_setup: §cFinish setup before using this command
  required: §eSetup BlockyJump §b/bgj admin setup
  line:
    '1': §71) §3Set lobby
    '2': §b    /bgj admin lobby set
    '3': §72) §3Create arena
    '4': §b    /bgj admin arena add <name>
    '5': §73) §3Optional
    '6': §7    Tweak settings, create join signs, ...
    '7': §74) §3Enable plugin
    '8': §b    /bgj admin setup enable
  enable:
    'false': §aPlugin disabled
    'true': §aPlugin enabled
  random:
    'false': §aA list of arenas will be shown when none is specified
    'true': §aA random arena will be selected when none is specified
  teleport:
    'false': §aPlayers will be teleported back to their previous location
    'true': §aPlayers will be teleported to the lobby
  particles:
    'false': §aPortals won't spawn particles
    'true': §aPortals will spawn particles
  liquids:
    'false': §aPlayers won't be teleported back to their last checkpoint on contact
      with liquids
    'true': §aPlayers will be teleported back to their last checkpoint on contact
      with liquids
lobby:
  set: §aLobby set
  location:
    header: '§6Lobby location:'
    entry: §3X:§b%x%§3 Y:§b%y%§3 Z:§b%z%§3 in §b%w%
  teleported: §aTeleported to lobby
input:
  arena:
    name: '§3Enter arena name in chat:'
    cooldown: '§3Enter the cooldown length in minutes in the chat:'
    maximum:
      time: '§3Enter the maximum time in seconds in the chat:'
      fails: '§3Enter the maximum amount of fails in the chat:'
    reward:
      command:
        '1': '§3Enter the reward command in the chat:'
        '2': §7Be sure to leave out the beginning slash! §c(§m/§r§c)
        '3': §7You may use §b%p%§7 as a placeholder for the player name
validation:
  enter_valid_number: §cPlease enter a valid number
gui:
  header: §0★ BlockyJump ★
  navigation:
    previous: §3⏴ Previous ⏴
    next: §3⏵ Next ⏵
    back_main_menu: §3⏴ Back to main menu ⏴
    back_statistics_menu: §3⏴ Back to statistics menu ⏴
    back_administration_menu: §3⏴ Back to administration menu ⏴
    back_arena_selector: §3⏴ Back to arena selector ⏴
    back_arena: §3⏴ Back to arena ⏴
  actions:
    click_enable: §7Click to enable
    click_disable: §7Click to disable
    left_click_change_right_click_disable: §7Left click to change, right click to
      disable
    left_click_change_right_click_remove: §7Left click to change, right click to remove
    click_remove: §7Click to remove
    click_set_lobby: §7Click to set lobby to current location
    click_add_arena: §7Click to add new arena
  help:
    title: §3☄ Help ☄
    select_arena: §bSelect an arena
    select_opponent: §bSelect an opponent
    select_category: §bSelect a category
    personal_best: §bPersonal best games for each arena
    best_one_arena: §bBest games in one arena
    best_each_arena: §bBest games for each arena
    configure_arena: §bConfigure arena
    confirm_removal: §bConfirm removal
    lobby_location: §bLobby location
    configure_config: §bClick banners to configure config values
    follow_steps: §bFollow the steps
    not_supposed_to_happen: §bThis was not supposed to happen
  selector:
    arena: §6✦ %a% ✦
    player: §6✦ %p% ✦
  home:
    main_menu: §6⬧ Main menu ⬧
    join: §a⚑ Join a game ⚑
    challenge: §6⚡ Challenge a player ⚡
    statistics: §b⌚ Statistics ⌚
    administration: §c⚙ Administration ⚙
  join:
    title: Join
  challenge:
    title: Challenge
  statistics:
    title: Statistics
    category:
      personal: §a⬧ Personal ⬧
      arena: §6⬧ Arena ⬧
      server: §b⬧ Server ⬧
    personal:
      player: §7%p%
      played:
        top: §a⏹ Games played ⏹
        bottom: §7%a%
      won:
        top: §6⏹ Games won ⏹
        bottom: §7%a%
      entry: '§7Best: §a%t%§7 with §c%f% fails'
    arena:
      name: §7%a%
      pillar:
        top: §6⬧ Leaderboard ⬧
        bottom: §7%a%
      entry: §7In §a%t%§7 with §c%f% fails
      leaderboard:
        '1': §61. %p%
        '2': §62. %p%
        '3': §63. %p%
        '4': §64. %p%
        '5': §65. %p%
        '6': §66. %p%
        '7': §67. %p%
        '8': §68. %p%
        '9': §69. %p%
        '10': §610. %p%
    server:
      played:
        top: §a⏹ Most games played ⏹
        bottom: '§7%p%: §6%a% games'
      won:
        top: §6⏹ Most games won ⏹
        bottom: '§7%p%: §6%a% games'
      entry: '§7%p%: §a%t%§7 with §c%f% fails'
  administration:
    title: Administration
    category:
      arena: §6✦ Arena ✦
      lobby: §a⌂ Lobby ⌂
      setup: §b⚙ Settings ⚙
    reload:
      top: §c⟳ Reload ⟳
      bottom: §7Arenas, config & messages
    arena:
      add_arena: §a⨁ Add arena ⨁
      list:
        enabled: §aEnabled
        disabled: §cDisabled
      edit_arena:
        top: §6✎ Edit arena ✎
        bottom: §7Enter edit mode
      arena_name: §7%a%
      enabled: §a☑ Enabled ☑
      disabled: §c☒ Disabled ☒
      cooldown:
        enabled:
          top: §a☑ Cooldown ☑
          bottom: '§6Set: %t%'
        disabled: §c☒ Cooldown ☒
      maximum:
        info:
          top: §c☠ Maximum ☠
          bottom: §7Set a maximum time and amount of fails
        time:
          enabled:
            top: §c☑ Maximum Time ☑
            bottom: '§6Set: %t%'
          disabled: §7☒ Maximum Time ☒
        fails:
          enabled:
            top: §c☑ Maximum Fails ☑
            bottom: '§6Set: %f% fails'
          disabled: §7☒ Maximum Fails ☒
      remove:
        bucket:
          top: §c❌ Remove arena ❌
          bottom: §4⚠ This cannot be undone! ⚠
        banner:
          sure:
            top: §c⚠ Are you sure? ⚠
            bottom: §4This cannot be undone!
      reward:
        info:
          top: §b⁂ Rewards ⁂
          bottom: §7Set rewards for players
        command:
          top: §6❢ Command ❢
          bottom: §a/%c%
        add: §a⨁ Add reward ⨁
    lobby:
      set: §6↓ Set Lobby ↓
      teleport:
        top: §b↑ Teleport to lobby ↑
        bottom: §7X:%x% Y:%y% Z:%z% in %w%
    setup:
      plugin:
        enabled: §a☑ Plugin enabled ☑
        disabled: §c☒ Plugin disabled ☒
        bottom: §7Enable plugin for games to be played
      random:
        enabled: §a☑ Random arena ☑
        disabled: §c☒ Random arena ☒
        bottom: §7Join random arena if none was selected
      particles:
        enabled: §a☑ Particles ☑
        disabled: §c☒ Particles ☒
        bottom: §7Enable particle effects
      lobby_teleport:
        enabled: §a☑ Lobby teleport ☑
        disabled: §c☒ Lobby teleport ☒
        bottom: §7Always teleport to lobby when a game is finished
      liquids:
        enabled: §a☑ Liquids ☑
        disabled: §c☒ Liquids ☒
        bottom: §7Touching liquids during a game counts as fail
      initial:
        top: §8☉ Initial setup ☉
        bottom: §7Reopen initial setup
    initial_setup:
      title: Initial Setup
      block: §6⬧ Initial Setup ⬧
      lobby: §6① Set Lobby ①
      arena:
        top: §6② Add arena ②
        bottom: §7Arena has to be enabled afterwards
      optional:
        top: §6③ Optional ③
        bottom: §7Tweak settings, create join signs, ...
      enable:
        top: §6④ Enable plugin ④
        bottom: §7Enable plugin to complete initial setup
      done: §a☑ Done ☑
      print_instructions:
        top: §3⎙ Print setup instructions ⎙
        bottom:
          '1': §bDisplay instructions in chat
          '2': §7For the use of commands
      access_denied:
        top: §c❌ Access denied ❌
        bottom:
          '1': §7Make sure you have all required
          '2': §7administration permissions
  error:
    title: Error
    barrier: §c❌ Something went wrong ❌
```

</div>

<button title="Click to show or hide content" type="button" style="cursor: pointer; background: white; border: 0.125em solid black; padding: 0.5em 0.75em; color: black; font-family: var(--siteFont),Helvetica Neue,Arial,sans-serif" onclick="if(document.getElementById('spoiler-messages-de') .style.display=='none') {document.getElementById('spoiler-messages-de') .style.display=''}else{document.getElementById('spoiler-messages-de') .style.display='none'}">Show default messages_de.yml</button>
<div id="spoiler-messages-de" style="display:none">

```yaml
plugin:
  prefix: §f§l[§3§lBlockyJump§f§l]§r
  header: §3--------- %p%§b von leberwurst88§7 v%v%§3 ---------
  enabled: §aPlugin aktiviert
  disabled: §cPlugin deaktiviert
  no_permission: §cKeine Berechtigung
  wrong: §cEtwas ist schiefgelaufen
  error_gui_triggered: §cDie Error GUI wurde ausgelöst, etwas ist schiefgelaufen in
    %c%
  patcher:
    noticed_update: §eAktualisierung einer älteren Version erkannt, verarbeite Änderungen
      falls notwendig
    patched: §aÄnderungen der Version %v% verarbeitet
  update:
    check_failed: '§cKonnte nicht nach Updates prüfen:'
    check_cancelled: §cUpdate-Überprüfung abgebrochen
    available:
      console: '§cNeues Update verfügbar, bitte update auf die Version v%v% dieses
        Plugins auf SpigotMC:'
      player: §4[⚡] §cBitte update auf §7v%v%§c auf SpigotMC §4[⚡]
    automatically: §cEin automatisches Update wird gestartet...
    download:
      create_folder: §cKonnte /plugins/update Ordner weder finden noch erstellen
      downloading: §eHerunterladen der Update-Datei...
      failed: '§cDer Download ist fehlgeschlagen:'
      completed: §aStarte Herunterladen der aktuellsten Plugin-Datei...
  link:
    click: Zum Öffnen klicken
  quit_could_not_leave: §cAbgemeldeter Spieler konnte das Spiel nicht verlassen
config:
  messages:
    ready: §aSprachdatei bereit (%l%)
    failed: §cSprachdatei fehlerhaft (%l%)
  ready: §aEinstellungen bereit
  ready_setup: §aEinstellungen ready, §cEinrichtung benötigt
  failed: §cEinstellungen fehlerhaft
  arena:
    ready: §aArenen-Konfiguration bereit
    failed: §cArenen-Konfiguration fehlerhaft
  reloaded: §aDateien neu geladen
db:
  sqlite:
    ready: §aLokale Datenbank bereit
  mysql:
    ready: §aMySQL-Datenbank bereit
placeholderapi:
  enabled: §aPlaceholderAPI aktiviert
  no_data: keine Daten
player:
  already_playing:
    you: §cDu bist bereits in einem Spiel
    player: §cSpieler ist bereits in einem Spiel
  not_found: §cSpieler konnte nicht gefunden werden
  not_in_game:
    you: §cDu bist gerade nicht in einem Spiel
    player: §cSpieler ist nicht in einem Spiel
console:
  cannot_join: §cKonsole kann keine Spiele betreten, versuche /bgj join <arena> <player>
  cannot_leave: §cKonsole kann keine Spiele verlassen
  cannot_challenge: §cKonsole kann keine Spieler herausfordern
  cannot_edit: §cKonsole kann keine Arenen bearbeiten. §3Erstelle eine neue mit §b/bgj
    admin arena add <name> <pos1_x> <pos1_y> <pos1_z> <pos2_x> <pos2_y> <pos2_z> <spawn_x>
    <spawn_y> <spawn_z> <world>
  cannot_set_lobby: §cLobby kann nicht auf den Standort gesetzt werden, versuche §b/bgj
    admin lobby set <x> <y> <z> <world>
  cannot_teleport:
    checkpoint: §cKonsole kann nicht zum Kontrollpunkt teleportiert werden
console_cannot_teleport:
  lobby: §cKonsole kann nicht in die Lobby teleportiert werden, versuche /bgj admin
    lobby get
arena:
  none:
    general: §cEs gibt noch keine Arenen
    admin: §cEs gibt noch keine Arenen, benutze /bgj admin arena add um eine neue
      zu erstellen
  specify: '§cArena angeben: /bgj join <arena>'
  list:
    header: '§6BlockyJump Arenen:'
    entry:
      general: §7- §3%n%
      enabled: §7- §a%n%
      disabled: §7- §e%n%
  already_enabled: §cDiese Arena ist bereits aktiviert
  enabled: §aArena %n% ist nun aktiviert
  already_disabled: §cDiese Arena ist bereits deaktiviert
  disabled: §aArena %n% ist nun deaktiviert
  exists: §cDieser Arenen-Name existiert bereits
  added: §aBlockyJump Arena §e%n%§a erstellt
  enable: §3Aktiviere die Arena in der GUI oder mit §b/bgj admin arena enable %n%
  removed: §aArena gelöscht
  reward:
    cmd:
      set: §aBelohnungs-Befehl festgelegt
      removed: §aBelohnungs-Befehl gelöscht
  maximum:
    fails:
      set: §aMaximale Anzahl von Fehlern festgelegt
      removed: §aMaximale Anzahl von Fehlern gelöscht
    time:
      set: §aMaximale Zeit festgelegt
      removed: §aMaximale Zeit gelöscht
  cooldown:
    set: §aZeitsperre festgelegt
    removed: §aZeitsperre gelöscht
game:
  joined: §aSpiel betreten
  checkpoint:
    set: §6Kontrollpunkt erreicht
    teleported: §aZum Kontrollpunkt teleportiert
  hider:
    hidden: §aSpieler versteckt
    shown: §aSpieler sichtbar
    nothing: §eEs ist nichts passiert
  arena:
    not_found: §cDiese Arena existiert nicht
    disabled: §cDiese Arena ist deaktiviert
  won:
    congratulations: §6Herzlichen Glückwunsch, du hast das Spiel gewonnen!
  lost:
    player: §cDu hast das Spiel verloren!
    over: §6Das Spiel ist vorbei!
    winner: §aDer Gewinner ist §6%w%
  end:
    stats: '§3Zeit: §b%t%§3 Fehler: §b%f%'
  left: §aSpiel verlassen
  not_ready: §cPlugin nicht bereit
  wait: §cWarte %t% bevor du wieder spielen kannst
  command_not_allowed: §cDieser Befehl ist in der Arena nicht erlaubt. Um sie zu verlassen,
    benutze /bgj leave
challenge:
  already_challenged: §cDu hast diesen Spieler bereits herausgefordert
  challenged: §3%p% §6hat dich herausgefordert in der Arena §b%a%
  options: '§7Deine Möglichkeiten: §b/bgj challenge accept§7 oder §b/bgj challenge
    decline'
  sent: §aHerausforderung abgeschickt, warte auf Antwort
  player:
    accepted: §a%p% hat deine Herausforderung angenommen
    declined: §c%p% hat deine Herausforderung abgelehnt
  accepted: §aHerausforderung angenommen
  declined: §aHerausforderung abgelehnt
  no_challenges: §cDu hast keine ausstehenden Herausforderungen
  cannot_challenge_yourself: §cDu kannst dich nicht selbst herausfordern
time:
  stopwatch:
    hours: '%h% h, '
    minutes: '%m% min, '
    seconds: '%s% s'
hologram:
  portal:
    arena: §l§6✦ %a% ✦
    type: §a▼ Klassischer Parkour§7 - §aHier beitreten ▼
    leaderboard:
      head: §7+----- §bBestenliste§7 -----+
      line: §e#%n% §6%p%§7 in §a%t%§7 mit §c%f% Fehlern
scoreboard:
  arena:
    head: '§7» Arena:'
    line: §b%n%
  timer:
    head: '§7» Zeit:'
    line: §b%t%
  timer_max:
    line: §b%t%
  fails:
    head: '§7» Fehler:'
    line: §b%f%
    timeout: §cZeit abgelaufen
  fails_max:
    line: §b%f% / %m%
item:
  game:
    checkpoint: §2Kontrollpunkt
    hide: §2Spieler verstecken
    leave: §cVerlassen
  edit:
    bounds: §2Arena-Grenzen
    spawn: §2Startpunkt festlegen
    portal: §2Portal-Standort festlegen
    finish: §2Fertigstellen
stats:
  personal:
    header: §7---- §f§l[§3§lStatistiken§f§l] §b%p%§7 ----
    amounts: '§3Spiele gespielt: §b%p%§7 - §3Gewonnen: §b%w%'
    list: §7- §3%n%§7 in §b%t%§7 mit §b%f%§7 Fehler(n)
    console_does_not_have: §cKonsole hat keine persönlichen Statistiken, versuche
      §b/bgj help stats
  server:
    no_data: §cNicht genug Daten, versuche es später nochmal
    header: §7------------- §f§l[§3§lStatistiken§f§l] §bServer§7 -------------
    most:
      played: '§3Meiste Spiele gespielt: §b%p% (%a%)'
      won: '§3Meiste Spiele gewonnen: §b%p% (%a%)'
    list: '§7- §3%a%: §b%p%§7 in §b%t%§7 mit §b%f%§7 Fehler(n)'
  arena:
    header: §7-------- §f§l[§3§lStatistiken§f§l] §b%a%§7 --------
    list: §7%i%) §3%p%§7 in §b%t%§7 mit §b%f%§7 Fehler(n)
help:
  list:
    header: §3---§7[%i%]§3--- %p%§b von leberwurst88§7 v%v% §3---§7[%i%]§3---
    entry: §3%c% §7%d%
    footer:
      cmd: §3------------------- §b/bgj help %p%§3 -------------------
      end: §3--------------------------------------------------
  single:
    cmd: §3§l%c%
    description: §7%d%
    footer: §3-------------------- §7/bgj help§3 --------------------
  options: §3%c%§b%o%
  no_content: §cKein Inhalt
  for_help: §7Für Hilfe, benutze §b/bgj help
  not_found: §cBefehl nicht gefunden, versuche §b/bgj help
  displaying: 'Zeige Hilfe:'
edit_mode:
  instructions:
    line:
      '1': '§3Anleitung:'
      '2': §7- Linksklick mit §bgoldener Axt§7 auf zwei Eckblöcke, um die §bArena
        festzulegen
      '3': §7- Stelle dich auf den §bStartpunkt§7 und mache einen Linksklick mit dem
        §bStock
      '4': §7- Wenn du ein §bPortal§7 erzeugen möchtest, stelle dich auf die Position
        und klicke mit der §bRute
      '5': §7- Klicke auf den §bSmaragden§7 wenn du §afertig§7 bist
  bounds:
    set: §aArena-Grenzen festgelegt
    first: §aErste Ecke festgelegt, wähle zweite Ecke
  spawn:
    set: §aStartpunkt festgelegt
  portal:
    disabled: §aArena-Portal deaktiviert
    set: §aArena-Portal festgelegt
  finished: §aArena-Einrichtung fertiggestellt
  cancelled: §cArena-Einrichtung abgebrochen
setup:
  finish_setup: §cBeende die Einrichtung bevor du diesen Befehl benutzt
  required: §eRichte BlockyJump ein §b/bgj admin setup
  line:
    '1': §71) §3Lobby festlegen
    '2': §b    /bgj admin lobby set
    '3': §72) §3Arena erstellen
    '4': §b    /bgj admin arena add <name>
    '5': §73) §3Optional
    '6': §7    Einstellungen anpassen, Schilder erstellen, ...
    '7': §74) §3Plugin aktivieren
    '8': §b    /bgj admin setup enable
  enable:
    'false': §aPlugin deaktiviert
    'true': §aPlugin aktiviert
  random:
    'false': §aEine Liste der Arenen wird angezeigt, wenn keine angegeben ist
    'true': §aEine zufällige Arena wird ausgewählt, wenn keine angegeben ist
  teleport:
    'false': §aSpieler werden nach dem Spiel zu ihrer letzten Position teleportiert
    'true': §aSpieler werden nach dem Spiel in die Lobby teleportiert
  particles:
    'false': §aPortale erzeugen keine Partikel
    'true': §aPortale erzeugen Partikel
  liquids:
    'false': §aSpieler werden beim Kontakt mit Flüssigkeiten nicht zum letzten Kontrollpunkt
      teleportiert
    'true': §aSpieler werden beim Kontakt mit Flüssigkeiten zum letzten Kontrollpunkt
      teleportiert
lobby:
  set: §aLobby festgelegt
  location:
    header: '§6Lobby-Position:'
    entry: §3X:§b%x%§3 Y:§b%y%§3 Z:§b%z%§3 in §b%w%
  teleported: §aIn die Lobby teleportiert
input:
  arena:
    name: '§3Gebe den Arena-Namen in den Chat ein:'
    cooldown: '§3Gebe die Dauer der Zeitsperre in Minuten in den Chat ein:'
    maximum:
      time: '§3Gebe die maximale Zeit in Sekunden in den Chat ein:'
      fails: '§3Gebe die maximale Anzahl von Fehlern in den Chat ein:'
    reward:
      command:
        '1': '§3Gebe den Belohnungs-Befehl in den Chat ein:'
        '2': §7Lasse den Schrägstrich am Anfang weg! §c(§m/§r§c)
        '3': §7Du kannst §b%p%§7 als Platzhalter für den Spielernamen benutzen
validation:
  enter_valid_number: §cBitte gebe eine gültige Nummer ein
gui:
  header: §0★ BlockyJump ★
  navigation:
    previous: §3⏴ Vorherige ⏴
    next: §3⏵ Nächste ⏵
    back_main_menu: §3⏴ Zurück zum Hauptmenü ⏴
    back_statistics_menu: §3⏴ Zurück zum Statistik-Menü ⏴
    back_administration_menu: §3⏴ Zurück zum Administrations-Menü ⏴
    back_arena_selector: §3⏴ Zurück zur Arena-Auswahl ⏴
    back_arena: §3⏴ Zurück zur Arena ⏴
  actions:
    click_enable: §7Zum Aktivieren klicken
    click_disable: §7Zum Deaktivieren klicken
    left_click_change_right_click_disable: §7Linksklick zum Ändern, Rechtsklick zum
      Deaktivieren
    left_click_change_right_click_remove: §7Linksklick zum Ändern, Rechtsklick zum
      Löschen
    click_remove: §7Zum Löschen klicken
    click_set_lobby: §7Klicke, um die Lobby auf die jetzige Position zu setzen
    click_add_arena: §7Klicke, um eine neue Arena hinzuzufügen
  help:
    title: §3☄ Hilfe ☄
    select_arena: §bWähle eine Arena
    select_opponent: §bWähle einen Gegner
    select_category: §bWähle eine Kategorie
    personal_best: §bPersönliche beste Spiele jeder Arena
    best_one_arena: §bBeste Spiele einer Arena
    best_each_arena: §bBeste Spiele jeder Arena
    configure_arena: §bPasse die Arena an
    confirm_removal: §bLöschen bestätigen
    lobby_location: §bLobby-Position
    configure_config: §bKlicke die Banner, um Einstellungen vorzunehmen
    follow_steps: §bBefolge die Schritte
    not_supposed_to_happen: §bDas hätte nicht passieren dürfen
  selector:
    arena: §6✦ %a% ✦
    player: §6✦ %p% ✦
  home:
    main_menu: §6⬧ Hauptmenü ⬧
    join: §a⚑ Spiel betreten ⚑
    challenge: §6⚡ Spieler herausfordern ⚡
    statistics: §b⌚ Statistiken ⌚
    administration: §c⚙ Administration ⚙
  join:
    title: Betreten
  challenge:
    title: Herausforderung
  statistics:
    title: Statistiken
    category:
      personal: §a⬧ Persönlich ⬧
      arena: §6⬧ Arena ⬧
      server: §b⬧ Server ⬧
    personal:
      player: §7%p%
      played:
        top: §a⏹ Spiele gespielt ⏹
        bottom: §7%a%
      won:
        top: §6⏹ Spiele gewonnen ⏹
        bottom: §7%a%
      entry: '§7Rekord: §a%t%§7 mit §c%f% Fehlern'
    arena:
      name: §7%a%
      pillar:
        top: §6⬧ Bestenliste ⬧
        bottom: §7%a%
      entry: §7In §a%t%§7 mit §c%f% Fehlern
      leaderboard:
        '1': §61. %p%
        '2': §62. %p%
        '3': §63. %p%
        '4': §64. %p%
        '5': §65. %p%
        '6': §66. %p%
        '7': §67. %p%
        '8': §68. %p%
        '9': §69. %p%
        '10': §610. %p%
    server:
      played:
        top: §a⏹ Meiste Spiele gespielt ⏹
        bottom: '§7%p%: §6%a% Spiele'
      won:
        top: §6⏹ Meiste Spiele gewonnen ⏹
        bottom: '§7%p%: §6%a% Spiele'
      entry: '§7%p%: §a%t%§7 mit §c%f% Fehlern'
  administration:
    title: Administration
    category:
      arena: §6✦ Arena ✦
      lobby: §a⌂ Lobby ⌂
      setup: §b⚙ Einstellungen ⚙
    reload:
      top: §c⟳ Neu laden ⟳
      bottom: §7Arenas, Einstellungen & Nachrichten
    arena:
      add_arena: §a⨁ Arena hinzufügen ⨁
      list:
        enabled: §aAktiviert
        disabled: §cDeaktiviert
      edit_arena:
        top: §6✎ Arena bearbeiten ✎
        bottom: §7Bearbeitungsmodus betreten
      arena_name: §7%a%
      enabled: §a☑ Aktiviert ☑
      disabled: §c☒ Deaktiviert ☒
      cooldown:
        enabled:
          top: §a☑ Zeitsperre ☑
          bottom: '§6Festgelegt: %t%'
        disabled: §c☒ Zeitsperre ☒
      maximum:
        info:
          top: §c☠ Einschränkungen ☠
          bottom: §7Maximale Zeit und Anzahl von Fehlern festlegen
        time:
          enabled:
            top: §c☑ Maximale Zeit ☑
            bottom: '§6Festgelegt: %t%'
          disabled: §7☒ Maximale Zeit ☒
        fails:
          enabled:
            top: §c☑ Maximale Fehler ☑
            bottom: '§6Festgelegt: %f% Fehler'
          disabled: §7☒ Maximale Fehler ☒
      remove:
        bucket:
          top: §c❌ Arena löschen ❌
          bottom: §4⚠ Dies kann nicht rückgängig gemacht werden! ⚠
        banner:
          sure:
            top: §c⚠ Bist du sicher? ⚠
            bottom: §4Dies kann nicht rückgängig gemacht werden!
      reward:
        info:
          top: §b⁂ Belohnungen ⁂
          bottom: §7Belohnungen für Spieler festlegen
        command:
          top: §6❢ Befehl ❢
          bottom: §a/%c%
        add: §a⨁ Belohnung hinzufügen ⨁
    lobby:
      set: §6↓ Lobby festlegen ↓
      teleport:
        top: §b↑ In die Lobby teleportieren ↑
        bottom: §7X:%x% Y:%y% Z:%z% in %w%
    setup:
      plugin:
        enabled: §a☑ Plugin aktiviert ☑
        disabled: §c☒ Plugin deaktiviert ☒
        bottom: §7Plugin aktivieren, um Spiele freizuschalten
      random:
        enabled: §a☑ Zufällige Arena ☑
        disabled: §c☒ Zufällige Arena ☒
        bottom: §7Ohne Auswahl zufälliger Arena beitreten
      particles:
        enabled: §a☑ Partikel ☑
        disabled: §c☒ Partikel ☒
        bottom: §7Partikeleffekte aktivieren
      lobby_teleport:
        enabled: §a☑ Lobby-Teleportation ☑
        disabled: §c☒ Lobby-Teleportation ☒
        bottom: §7Immer nach dem Spiel in die Lobby teleportieren
      liquids:
        enabled: §a☑ Flüssigkeiten ☑
        disabled: §c☒ Flüssigkeiten ☒
        bottom: §7Kontakt mit Flüssigkeiten zählt als Fehler
      initial:
        top: §8☉ Ersteinrichtung ☉
        bottom: §7Ersteinrichtung erneut öffnen
    initial_setup:
      title: Ersteinrichtung
      block: §6⬧ Ersteinrichtung ⬧
      lobby: §6① Lobby festlegen ①
      arena:
        top: §6② Arena hinzufügen ②
        bottom: §7Arena muss danach aktiviert werden
      optional:
        top: §6③ Optional ③
        bottom: §7Einstellungen anpassen, Schilder erstellen, ...
      enable:
        top: §6④ Plugin aktivieren ④
        bottom: §7Plugin aktivieren, um Ersteinrichtung abzuschließen
      done: §a☑ Fertig ☑
      print_instructions:
        top: §3⎙ Anleitung senden ⎙
        bottom:
          '1': §bEinrichtungsanleitung im Chat zeigen
          '2': §7Für die Benutzung von Befehlen
      access_denied:
        top: §c❌ Zugriff verweigert ❌
        bottom:
          '1': §7Stelle sicher, dass du alle benötigten
          '2': §7Administrator-Rechte besitzt
  error:
    title: Fehler
    barrier: §c❌ Etwas ist schiefgelaufen ❌
```

</div>