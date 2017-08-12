WorldEdit 拥有插件自己提供的 Player 和 World 的类，一些方法就需要这个。

获得 WE 的 World 对象：
```Java
WorldEdit.getInstance().getServer().getWorlds();
// 或者特别使用 Bukkit
BukkitUtil.getLocalWorld(bukkitWorld);
```
获取玩家对象
```Java
// Bukkit
WorldEditPlugin worldEdit = (WorldEditPlugin) Bukkit.getServer().getPluginManager().getPlugin("WorldEdit");
worldedit.wrapPlayer(bukkitPlayer);
// Forge
ForgeWorldEdit.inst.wrap(entityPlayer);
// FAWE 的变更
FawePlayer.wrap(uuid or username or actor or player object here).getPlayer();
```

要想异步使用请查看，例如： `PlayerWrapper.wrap(player)`
 - [PlayerWrapper (WorldEdit Player)](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/wrappers/PlayerWrapper.java)
 - [WorldWrapper (WorldEdit World)](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/wrappers/WorldWrapper.java)