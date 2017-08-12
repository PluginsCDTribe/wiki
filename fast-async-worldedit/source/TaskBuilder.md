### 总览
TaskBuilder 能够创建相继的同步或异步任务的简化版。
https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/util/task/TaskBuilder.java
### 方法：
 - sync([Runnable|ReturnTask|ReceiveTask|Task]) - 在主线程上执行任务
 - async([Runnable|ReturnTask|ReceiveTask|Task]) - 在主线程外执行任务
 - delay([int|DelayedTask]) - 延迟几个游戏刻，然后再进行下个任务
 - syncParallel([Runnable|ReturnTask|ReceiveTask|Task]) - 执行所有并行的下个 syncParallel 任务
 - asyncParallel([Runnable|ReturnTask|ReceiveTask|Task]) - 执行所有并行的下个 asyncParallel 任务
 - syncWhenFree([SplitTask|ReturnTask|ReceiveTask|Task]) - 在主线程空闲时执行任务
 - abortIfTrue(Task<Boolean,Object>) - 如果为 true 停止所有进程
 - build() - 开始执行
 - buildAsync() - 从某一异步线程开始执行

### 多任务
输出数字 6
```Java
new TaskBuilder()
.async((ReturnTask<Integer>) () -> 5 + 1)
.sync((ReceiveTask) input -> System.out.println(input))
.build();
```
### SplitTask 的示例
分离一个任务并且在主线程空闲时运行它。
```Java
// 在现实中你需要使用 EditSession, AsyncWorld,与 FaweQueue 的其中之一作为代替。
// 但这仅仅是你怎么使用 FAWE API 分离一个任务的示例

final World world = Bukkit.getWorld("world");
new TaskBuilder()
// 执行任务会被分成多个 20ms 的任务
.syncWhenFree(new TaskBuilder.SplitTask(20) {
    @Override
    public Object exec(Object previous) {
        for (int x = 0; x < 100; x++) {
            for (int y = 0; y < 100; y++) {
                for (int z = 0; z < 100; z++) {
                    world.getBlockAt(x, y, z).setType(Material.STONE);
                    // FAWE 会使用这个点来分离任务
                    // 你可以设置多个分离点
                    split();
                }
            }
        }
        // 我们不需要对于下个任务的结果
        return null;
    }
})
.build();
```
### 任务元数据
TaskBuilder 继承 Metadatable，所以你可以使用它储存临时数据：
https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/object/Metadatable.java
```Java
final TaskBuilder task = new TaskBuilder();
task.sync(() -> {
    task.setMeta("blah", 5);
    return task.<Integer>getMeta("blah") + 56;
});
```