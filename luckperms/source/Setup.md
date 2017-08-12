## 初始设置

1. 下载适合你平台的 `LuckPerms-???-x.x.x.jar` 文件。你可以点[这里](https://ci.lucko.me/job/LuckPerms/)查看最新的版本。
2. 打开你的 Mod 或插件所在路径，这路径通常要么是 `/server/plugins/` ，要么是 `/server/mods/`。
然后把 LuckPerms 的 jar 文件放入文件夹中。
3. 请完全关闭你的服务器，然后再打开，这会生成默认配置。
4. 完全关闭你的服务器，打开配置文件。配置文件的位置在 `/plugins/LuckPerms/config.yml` 或 `/config/luckperms/luckperms.conf`。
5. 请浏览配置文件，然后根据你的服务器修改设置，尤其是请注意存储相关设置。
6. 再次开启你的服务器。

你可以更改配置文件中的很多内容，文件有很细节化的注释，每个设置的作用注释中都解释的很清楚。


### 需求
LuckPerms 插件只有一个环境需求。
* **Java 8**

没错，唯一需求就是你必须使用 Java 8，LuckPerms 插件在旧版本的Java上不会工作。

到目前为止很多服务器提供商都已经升级到Java 8了，但是如果你的服务器提供商没有升级的话，请温和地和他们谈谈，让他们去升级。

如果你是自己租主机开服的话，你应该对你还没有升级Java感到羞愧！
升级的过程是很简单的，如果你想升级的话网上也有大量的教程。
使用过期的软件肯定不是好的:)

### Bukkit版本过旧
如果你收到了类似于 "NoSuchMethod" 或 "ClassNotFound" 这类错误的话，十有八九就是你在使用较旧的Bukkit版本。
在将它作为错误报告给我之前，请尝试使用"Development Builds"（构建版本）下载页面的"Bukkit-Legacy"（Bukkit-旧版）版本。

### 切换存储类型
LuckPerms 插件所使用的默认数据存储类型是 **H2 数据库**。
所有的数据都会储存在LuckPerms插件目录下的 `luckperms.db.mv.db` 文件之中。
（插件目录为 `/plugins/LuckPerms/` 或 `/luckperms/`）

这个数据格式普通的文本编辑器是**不能读取**的。
如果你想要手动阅读/编辑LuckPerms插件的数据的话，你就需要切换到**YAML或JSON**存储格式，更改 `config.yml` 文件中的配置选项就好了。

更多相关于存储类型的有关信息请阅读[下一节](/Choosing-a-Storage-type.md)
