如果你没有使用 WorldEdit 第三方的记录插件，例如 BlocksHub 的话，FAWE 插件内置了明显更快，且占用硬盘空间更少（压缩）的记录器。

#### 需求
 - Settings.HISTORY.USE_DISK=true
 - Settings.HISTORY.USE_DATABASE=true

### 实现一次查找
数据库中只包含了编辑的列表和影响的区域，不是所有改变的方块。

要想执行一次完全回滚你需要读取每一次潜在的编辑的内容。
```Java
RollbackDatabase db = DBHandler.IMP.getDatabase(worldName);
boolean deleteAfterLookup = false;
// 搜索所有没有提供uuid的玩家
// 全部时间搜索，使用 0 为最小时间
// pos1 和 pos2 可以指定为单个点
db.getPotentialEdits(uuid, minTime, pos1, pos2, new RunnableVal<DiskStorageHistory>() {
    @Override
    public void run(DiskStorageHistory potentialEdit) {
        try {
            UUID uuid = potentialEdit.getUUID();
            String name = Fawe.imp().getName(uuid);
            int index = potentialEdit.getIndex();
            long age = System.currentTimeMillis() - potentialEdit.getBDFile().lastModified();
            String ageFormatted = MainUtil.secToTime(age / 1000);
            // 我现在想要读取编辑中每个方块的变化
            // 注意：也会有关于实体和掉落物的迭代器的变化
            //  - 或是使用 `potentialEdit.getIterator(dir)` 来检测所有变化
            Iterator<MutableFullBlockChange> iter = potentialEdit.getFullBlockIterator(false);
            while (iter.hasNext()) {
                MutableFullBlockChange change = iter.next();
                /* Maybe you only want to do something if the block is in a certain position?
                if (change.x != x || change.y != y || change.z != z) {
                    continue;
                }
                */
                // combinedId (查看 FaweCache#getId(combined), FaweCache#getData(combined))
                int from = change.from;
                int to = change.to;
                // 用这个信息来做些什么？
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}, new Runnable() {
    @Override
    public void run() {
        // 在查阅完成之后会运行这个
    }
}, deleteAfterLookup);
```