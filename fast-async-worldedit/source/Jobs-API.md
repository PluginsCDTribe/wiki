一些类似于 Job API 的东西。

### [SetQueue](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/util/SetQueue.java)
这个类中有成队列的本地队列。每个本地队列都是由成队列的区块改变组成的可能与 EditSession 相关联，它可能与一个玩家有关。

SetQueue 会检测激活和未激活的队列：
```Java
// 激活的队列已经完成了等候
Collection<FaweQueue> active = SetQueue.IMP.getActiveQueues();
// 未激活的队列可能还在等候其他区块改变或其他任务
Collection<FaweQueue> inactive = SetQueue.IMP.getInactiveQueues();
Collection<FaweQueue> all = SetQueue.IMP.getAllQueues();
```

### 示例：获得一名玩家等候队列中的方块！
你可以从这里获得一名玩家当前运行的 EditSessions ：[`FawePlayer#getTrackedSessions`](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/object/FawePlayer.java#L443)。   
在每个 EditSession 中你能获得改变的方块： [`EditSession#getLimitUsed`](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/sk89q/worldedit/EditSession.java#L327)，但是这不会一定对应于当前队列中的方块（当队列任务完成后才能分配）。

你也可以通过使用 FaweQueue ([`EditSession#getQueue`](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/sk89q/worldedit/EditSession.java#L417)), 你可以获得激活的区块： [`FaweQueue#getFaweChunks`](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/object/FaweQueue.java#L137), 然后每个激活的区块都可以强制转换类型为 [`CharFaweChunk`](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/example/CharFaweChunk.java) 然后使用 [`CharFaweChunk#getTotalCount`](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/example/CharFaweChunk.java#L86)

### 撤销一次修改
在获取当前的 EditSession 之后，只要使用 [`EditSession#cancel`](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/sk89q/worldedit/EditSession.java#L365) 就好了。

