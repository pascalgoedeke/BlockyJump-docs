# Permissions
This page lists all the BlockyJump permissions along with information on what they are for.  
If you are looking for a specific permission for a command, also check the [➜commands](commands.md).  
By default, every player has the blockyjump.player permissions and only operators have the blockyjump.admin permissions. It's not recommended to use blockyjump.*.

| permission                  | preconfigured | description                                                                 |
|-----------------------------|---------------|-----------------------------------------------------------------------------|
| blockyjump.*                | /             | access to all BlockyJump commands                                           |
| blockyjump.player.*         | ([d])         | access to all BlockyJump player commands                                    |
| blockyjump.admin.*          | ([o])         | access to all BlockyJump admin commands                                     |
| blockyjump.player.basic     | [d]           | required for all players                                                    |
| blockyjump.player.join      | [d]           | allows to join games via the /bgj join command, GUI, join signs and portals |
| blockyjump.player.leave     | [d]           | allows to use the /bgj leave command and leave signs                        |
| blockyjump.player.check     | [d]           | allows to use the /bgj check command and checkpoint signs                   |
| blockyjump.player.challenge | [d]           | allows challenges                                                           |
| blockyjump.player.list      | [d]           | allows to use the /bgj list command                                         |
| blockyjump.player.stats     | [d]           | allows to check statistics via the /bgj stats command or the GUI            |
| blockyjump.player.help      | [d]           | access to command help                                                      |
| blockyjump.admin.basic      | [o]           | required for all admins                                                     |
| blockyjump.admin.join       | [o]           | access to /bgj join <arena> <player> command                                |
| blockyjump.admin.leave      | [o]           | access to /bgj leave <arena> <player> command                               |
| blockyjump.admin.arena      | [o]           | allows administration of arenas via the admin arena command or the GUI      |
| blockyjump.admin.lobby      | [o]           | allows administration of the lobby via the admin lobby command or the GUI   |
| blockyjump.admin.setup      | [o]           | access to setup via the admin setup command or the GUI                      |
| blockyjump.admin.open       | [o]           | access to /bgj admin open <player> command                                  |
| blockyjump.admin.reload     | [o]           | allows reloading files via the /bgj admin reload command or the GUI         |

*[d] = default, [o] = op*
