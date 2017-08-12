### 免责声明
FaweQueue 是修改世界最基础的类，当正确使用时处理速度很快。但替代使用这个，我推荐使用 Operations 或[EditSession](/WorldEdit-EditSession.md)，因为它们可以将很抽象的任务简化，并且相对于FaweQueue的普通方法而言，它们可以提供更好的表现。如果你想让更能适应 Bukkit API 的话，你也可以使用 [AsyncWorld](/AsyncWorld.md) 。

### FaweQueue
FaweQueue 是从异步线程中修改世界的基础队列
 - 使用它有效率地修改整个区块或其中的个别方块
 - 查看 EditSession 或 AsyncWorld ，这些使用起来更简单，但是速度会慢些
 - 如果你想控制更多的话，队列（queue）能够强制转换为 NMSMappedFaweQueue.

```Java
// 自动进入队列意味着方块会在它们被刷新之前开始放置
FaweQueue queue = FaweAPI.createQueue(worldName, autoQueue);
queue.setBlock(0, 0, 0, id, data);
queue.setBiome(0, 0, biome);
// 设置整个区块
FaweChunk<?> chunk = queue.getFaweChunk(5, 5);
chunk.fill(id, data);
chunk.addToQueue();
// 为位置重复相同任务
chunk = chunk.copy(true);
chunk.setLoc(queue, 5, 6);
chunk.addToQueue();
```

### NMS 方法
对于一些支持的平台也有更多方法。你可以通过将 `FaweQueue` 类型来强制转换为 `NMSMappedFaweQueue` 来访问这些。
更多信息：
[Light API](/Light-API.md)

