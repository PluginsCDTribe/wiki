EditSession 是 WorldEdit 用来在世界中制造并记录变化的。EditSessionBuilder 能够让你你完全控制它。
 - 你必须提供世界，查看 `FaweAPI.getWorld(...)`

示例：
```Java
EditSession editSession = new EditSessionBuilder(world).fastmode(true).build();
```
不设置参数会使用它们的默认值：
 - player: 做出编辑的玩家（默认是 null）
 - limit: 方块，实体或操作限制（默认是玩家的限制或无限制）
 - changeSet: 存储变更（默认是 config.yml 中的值）
 - allowedRegions: 允许可编辑的区域（默认是玩家能够编辑的区域，或是所有地方）
 - autoQueue: 在 flushQueue() 之前的改变（默认是 true）
 - fastmode: 跳过记录历史（默认是玩家的快速模式或是 config.yml 中设置不记录历史）
 - checkMemory: 是否启用内存剩余过低检查（默认是玩家的快速模式是否启用或 true）
 - combineStages: 历史记录是否结合分配（默认是配置文件中的配置）
 - blockBag: 使用的 blockbag （默认是 null）
 - eventBus: 使用的 eventBus （默认是 null）
 - event: 要调用的事件 （默认是 null）

请查看：https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/util/EditSessionBuilder.java

这是非 FAWE 插件的示例：
```Java
// 如果没有玩家做出变更
EditSession editSession = WorldEdit.getInstance().getEditSessionFactory().getEditSession(worldEditWorld, -1);
// 指定特殊玩家
editSession = WorldEdit.getInstance().getEditSessionFactory().getEditSession(worldEditWorld, -1, actor);

// 用 EditSession 做些什么
editSession.setBlock(new Vector(x, y, z), new BaseBlock(id, data));
// 在调用 flushQueue 之后就会开始变更
editSession.flushQueue();
```

这是一个结合 FAWE 插件的示例：
```Java
EditSession editSession = new EditSessionBuilder(world).fastmode(true).build();
editSession.setBlock(new Vector(x, y, z), new BaseBlock(id, data));
editSession.flushQueue();
```

### 撤销 EditSession 的修改
Where `editSession` is what you are undoing.
```Java
// 用你喜欢的方式创建 EditSession 
EditSession newEditSession = WorldEdit.getInstance().getEditSessionFactory().getEditSession(editSession.getWorld(), -1, null, null);
// 撤销操作
editSession.undo(newEditSession);
editSession.flushQueue();
```