AsyncWorld 实现了 Bukkit 世界接口，这能够让你异步访问世界或做出改变。
 - 很多对象都能从接口中获得，可以被异步使用（坐标，方块，区块等等）
 - 只有对方块和生物群系的操控才能优化队列
 - 其他操作在使用异步时只会变得更慢
 - 你可以使用 `AsyncWorld.create(...)` 来异步读取某个世界

请注意： AsyncWorld 类只存在于 `FastAsyncWorldEdit-bukkit` ，而不是 API 中。

```Java
TaskManager.IMP.async(new Runnable() {
    @Override
    public void run() {
        // 使用给定的世界创建设定异步创建或读取世界
        AsyncWorld world = AsyncWorld.create(new WorldCreator("MyWorld"));
        // AsyncWorld world = AsyncWorld.wrap(bukkitWorld); // 或是封包已存在的世界
        Block block = world.getBlockAt(0, 0, 0);
        block.setType(Material.BEDROCK);
        // 在你完成更改之后，请写入
        world.commit();
    }
});
```
资源文件： https://github.com/boy0001/FastAsyncWorldedit/tree/master/bukkit0/src/main/java/com/boydti/fawe/bukkit/wrapper

### 一些关于异步性能的相关提示
[这里](/Notes-on-async-performance.md)
以及：
[这里](/Fawe-TaskManager#sync-task.md)
