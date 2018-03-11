此页讲到了如何在 AuthMe 中使用和配置传送机制。

## 设置
以下设置中会对 重生 功能产生影响，按先后顺序列出：

1. `settings.restrictions.noTeleport` — 如果设置为 true, AuthMe 将_从不_ 传送玩家
1. `settings.restrictions.spawnPriority` — 按列表优先度考虑重生点  (支持: authme, essentials, multiverse, default)
1. `settings.restrictions.ForceSpawnLocOnJoin.enabled` — 如果设置为 true , 玩家将在登录成功 _后_ 传送到重生点
1. `settings.restrictions.ForceSpawnLocOnJoin.worlds` — 为上述传送设置中指定某世界 (区分大小写)
1. `settings.restrictions.teleportUnAuthedToSpawn` — 如果设置为 true , 玩家会在进入游戏后传送，如果玩家登录成功再传送回来

--
Related: `settings.restrictions.SaveQuitLocation` 如果你想将玩家退出时的位置数据保留到数据库时必须设置为 true。如果为 `false` ，玩家会被传送回进入游戏时的重生点，然而 AuthMe 中没有改变。

## 重生点优先次序
重生点优先次序可在 `settings.restrictions.spawnPriority` 中设置 (看前面)，即该设置中决定了玩家应该在哪重生。可用参数：

- **authme** — 重生点定义在 spawn.yml  (AuthMe 文件夹)。详细看下面。
- **essentials** — 重生点定义在 Essentials 基础插件的 spawn.yml 。仅适用于服务器有 Essentials 插件的情况下。
- **multiverse** — 在 Multiverse 提供的世界中获取重生点。只有在加载了 Multiverse 插件并且世界由  Multiverse 管理的情况下才能使用。
- **default** — world 的重生点 (原版 Minecraft)

例如:
```yaml
    spawnPriority: 'essentials,authme,default'
```
如果有 Essentials 的话，将优先使用 Essentials 的重生机制。如果没有，则会使用 AuthMe 的重生机制。如果还是没有，那就会使用原版的重生点。

## AuthMe 重生点
AuthMe 的重生点在 AuthMe 插件文件夹中的 spawn.yml 文件。例如:

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

第一次加入服务器玩家的重生点在 **firstspawn** 中，其他的玩家则是在重生点优先次序中定义重生点。你可以删除 `firstspawn` 部分来关闭该功能。

## AuthMe 重生点指令
- `/authme spawn` 将你传送到 AuthMe 的重生点
- `/authme setspawn` 设置 AuthMe 的重生点
- `/authme firstspawn` 将你传送到 AuthMe 的第一次重生点中
- `/authme setfirstspawn` 设置 AuthMe 的第一次重生点

这些命令的权限节点列在了 [指令列表页](https://github.com/AuthMe/AuthMeReloaded/blob/master/docs/commands.md)。