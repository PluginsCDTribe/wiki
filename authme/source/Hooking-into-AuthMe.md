面向想要与 AuthMe 交互的开发者的技术性描述。

### API

我们提供了在 AuthMe 中执行指令和查询的 API，参见 [AuthMeApi](http://ci.xephi.fr/job/AuthMeReloaded/javadoc/fr/xephi/authme/api/v3/AuthMeApi.html) 。你可以通过以下方式得到 `AuthMeApi` 对象：
```java
import fr.xephi.authme.api.v3.AuthMeApi;
// ...
AuthMeApi authmeApi = AuthMeApi.getInstance();
```
其他的方法在 Javadocs 都有提及（查看上方链接）。

### 事件

在某些操作之前或之后，我们会触发一些事件供你的插件监听。所有的 AuthMe 事件都继承了 [CustomEvent 类](http://ci.xephi.fr/job/AuthMeReloaded/javadoc/fr/xephi/authme/events/CustomEvent.html) 。你可以在 [这里](http://ci.xephi.fr/job/AuthMeReloaded/javadoc/fr/xephi/authme/events/package-tree.html) 查看所有事件以及它们的继承关系。所有的事件类都在 Javadocs 中有提及。

请注意，不是所有的事件都是可以取消的 - 只有继承了 Bukkit 的 `Cancellable` 接口的才可以。

### Demo Plugin

一个功能性的插件演示 AuthMe 整合被扔在了这个 [ljacqu/AuthMe_demo_integration](https://github.com/ljacqu/AuthMe_integration_demo) 仓库。