FAWE 能够在刷新区块或发送单独的方块变化时发送方块变化信息。

笔刷的预览就是后者的一个例子，这些方块改变只会发送给一个玩家（注意：服务器上的方块不需要改变）。

这就是用于优化仅发送 1 个方块（玻璃），然后稍后重置改变的 VisualExtent 。

```Java
VisualExtent extent = new VisualExtent(editSession.getExtent(), editSession.getQueue());
// 设置方块
extent.visualize(player);
// 一段时间后，重置所有方块
// 如果你同时也启用了另外一个预览效果的话，这个方法不会重置那其中的方块。
extent.clear(VisualExtent or null);
```

要想将指定的方块变化发送给一群玩家的话请使用 FaweQueue。

你可以使用任何 FaweChunk 中的类，例如 CharFaweChunk, VisualChunk 等等。
```Java
FaweQueue.sendBlockUpdate(FaweChunk, FawePlayer...);
```

