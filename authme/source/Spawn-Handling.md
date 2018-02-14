This page describes how teleportation is handled and configured in AuthMe. 

## Settings
The following settings have an influence on the spawn feature, listed by priority:

1. `settings.restrictions.noTeleport` — if set to true, AuthMe will _never_ teleport players
1. `settings.restrictions.spawnPriority` — list of spawns to consider by priority (supported: authme, essentials, multiverse, default)
1. `settings.restrictions.ForceSpawnLocOnJoin.enabled` — if set to true, players are teleported to spawn _after_ having logged in successfully
1. `settings.restrictions.ForceSpawnLocOnJoin.worlds` — limits the above feature only to the given worlds (case-sensitive)
1. `settings.restrictions.teleportUnAuthedToSpawn` — if set to true, teleports players to spawn when they join. Once they log in, they are teleported back to their original location

--
Related: `settings.restrictions.SaveQuitLocation` must be true for the quit location to be saved in the database. If `false`, players are teleported back to the location in which they would have joined without changes from AuthMe.

## Spawn Priority
Spawn priority is defined in `settings.restrictions.spawnPriority` (see above), i.e. this setting defines from where the spawn definition should be taken. Possible values:

- **authme** — Spawn points defined in spawn.yml (AuthMe folder). See below for details.
- **essentials** — Spawn as defined in Essentials' spawn.yml. Only applicable if Essentials is loaded on the server.
- **multiverse** — Gets the spawn point saved in Multiverse for the given world. Only possible if Multiverse is loaded and the world is a Multiverse handled world.
- **default** — Spawn location of the world (vanilla Minecraft)

Example:
```yaml
    spawnPriority: 'essentials,authme,default'
```
If Essentials is available, the spawn defined in Essentials is used. If not, the AuthMe spawn is used as second choice. If this also fails, the default is taken.

## AuthMe Spawn
The AuthMe spawnpoint is defined in spawn.yml of the AuthMe plugin folder. Example:

```yaml
spawn:
  world: world
  x: -171.77925533614896
  y: 99.0
  z: 171.8600493294933
  yaw: -180.43475
  pitch: 13.7999935
firstspawn:
  world: world
  x: -167.00317045444243
  y: 98.0
  z: 142.33661923798473
  yaw: -342.2848
  pitch: 11.849992
```

Players who have never played on the server before are teleported to the **firstspawn**; otherwise they are teleported to the regular spawnpoint as defined by the spawn priority. You can delete the `firstspawn` section to disable this feature.

## AuthMe Spawn Commands
- `/authme spawn` teleports you to the AuthMe spawn point
- `/authme setspawn` sets the AuthMe spawn point
- `/authme firstspawn` teleports you to the AuthMe first spawn point
- `/authme setfirstspawn` sets the AuthMe first spawn point

Permission nodes for the commands are listed on the [command list page](https://github.com/AuthMe/AuthMeReloaded/blob/master/docs/commands.md).