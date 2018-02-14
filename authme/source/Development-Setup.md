一些对想要帮助 AuthMe 的人们的提示和建议。

# Maven
如果 `org.bukkit` 类在依赖中不可用，保证 maven 中的「spigot」启用了。这会添加 Spigot API 作为项目依赖。另外你也可以启用「bukkit」（接着保证你把「spigot」关了）。这能让你确认我们的代码是否与这两个 API 冲突。

对于本地开发，你可以启用「skipLongHashTests」。这关闭了部分的哈希算法的测试，节省了部分构建的时间。

# IntelliJ
- 保证你如果是 64 位的操作系统，运行的是 idea**64**.exe 。（更快）

- Maven： 如果询问开启自动导入（Enable Auto Import），选择它。这将在 pom.xml 中的依赖有任何变化时自动更新依赖。

- 如果 `@Inject` 字段被标记了「never declared」警告，前往 设置（Settings） > 搜索「unused declaration」，选择 Java 的那一个，点击按钮「Configure annotations」，添加 `@Inject` 和 `@InjectDelayed` 。

- 你可以在配置中搜索「issue navigation」，添加一条新的规则（如下），让 issue 序号可以点击。
```
Issue ID: #(\d+)
Issue link: https://github.com/AuthMe/AuthMeReloaded/issues/$1
```

- 你是否在进行单元测试时得到了「missing argLine」的错误信息？前往 设置 > 搜索「Running Tests」，取消勾选「argLine」。

### Checkstyle

IntelliJ 有一个 checkstyle 插件，这和我们的 [Code Climate](https://codeclimate.com/github/AuthMe/AuthMeReloaded/issues) 搭配的很好。使用这个插件你可以在 Code Climate 远程完成后在 IDE 上进行一些操作。

- Ctrl+Shift+A，输入「Plugins」，搜索「Checkstyle」。如果没有的话，就点「Search repositories」
- 安装 Checkstyle-IDEA
- 在 File > Settings > Other Settings > Checkstyle，添加配置文件（.checkstyle.xml）。不要忘了点一下「Active」选框。

在这之后，checkstyle 将会自动运行在你的 IDE 上，规则错误将会显示为警告。

# Fork AuthMe

- 提示：在 Git Fork 之后添加 AuthMe 的仓库。在控制台执行 `git remote add upstream https://github.com/AuthMe/AuthMeReloaded.git` 。在 IntelliJ 使用 Ctrl+Shift+A > 「fetch」然后你就能看见仓库的分支和 AuthMe 团队。 

- 不要对 master 分支做出任何提交。它只用来和上游仓库同步。这样你就可以从父仓库拉取新的变更，而不会有任何冲突。然后你就能将你的自定义分支和本地分支合并来保持它们始终最新。
  - 如果你直接向你的 Fork 的 master 分支提交，那么你每次从 AuthMe/AuthMeReloaded 拉取时都会生成 Merge 报告，这会在 Git 历史记录增加很多不必要的东西，并且会生成很难看的 PR。

# 在 IntelliJ Debug AuthMe

在 StackOverflow 查看 _[Run Configuration to Debug Bukkit/Minecraft Plugin in IntelliJ IDEA](http://stackoverflow.com/a/29945539)_ 

如果你得到了 `ClassDefNotFoundError` ，保证你解压了所有的依赖到 JAR 里。右键右方的 Dependencies 选择「Extract Into Output Root.」然后将他们移动到 JAR 文件里。

![Screenshot dependencies setup](http://jalu.ch/ext/authme-docs/intellij_extracted_dependencies.png)

使用 `-Dbstats.relocatecheck=false` 选项运行服务器来避免 BStats 由于没有位于正确的 JAR 位置而抛出异常。