### 异步任务
很基础的东西，但这是你可以使用 FAWE TaskManager 来运行异步任务的方法。
```Java
TaskManager.IMP.async(new Runnable() {
    @Override
    public void run() {
        // Do stuff here?
    }
});
```

### 同步任务
使用 FAWE TaskManager 你可以切换使用主线程（原来为异步处理）然后执行任务。

``` Java
// 从异步线程中获得玩家背包内容
// 例如：方法异步处理不安全的话
PlayerInventory inventory = TaskManager.IMP.sync(new RunnableVal<PlayerInventory>() {
    @Override
    public void run(PlayerInventory value) {
        this.value = player.getInventory();
    }
});
```

___什么时候使用这个？___
 - 你想调用的方法使用异步处理不安全
 - 使用异步处理任务会有性能问题