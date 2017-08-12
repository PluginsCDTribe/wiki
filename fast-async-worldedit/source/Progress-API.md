> 请注意：如果你想查看 EditSession 的工作进度的话，请使用下面这个 EditSession 事件作为代替：
 - wiki.sk89q.com/wiki/WorldEdit/API/Hooking_EditSession
 - 这样以后你需要在 FAWE 插件的配置文件中的 `extent.allowed-plugins` 项目添加 `Settings.EXTENT.ALLOWED_PLUGINS` 你的插件。

要想检测 EditSession 的工作进度或是队列的工作进度很简单：
```Java
editSession.getQueue().setProgressTracker(new RunnableVal2<ProgressType, Integer>() {
    @Override
    public void run(ProgressType type, Integer amount) {
        // FAWE 能够在完整尺寸知晓前就开始操作
        switch (type) {
            case QUEUE:
                // <amount> 正在队列中的区块
            case DISPATCH:
                // <amount> 已离开队列的区块
            case DONE:
                // 队列为空（已完成）
        }
    }
});
```

要想使用默认的进度追踪器（title标题）请查看：
https://github.com/c7w/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/object/progress/DefaultProgressTracker.java

默认只有当队列中的区块数目大于64时消息才会提示（最大数目为 4,194,304 区块），不然的话它完成的太快了，但是你可以用这个自定义示踪器做你喜欢的事情。