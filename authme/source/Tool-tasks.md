_工具任务_ 是用于 AuthMe 的各种目的的任务。比如，生成文档页面，或者检查翻译文件的完整性。所有的工具任务都从相同的 runner 启动，即 ToolsRunner，位于 `test/tools/ToolsRunner.java` 。提示：你可以保存 ToolsRunner 的运行配置，这样你就可以随时开始一个工具任务了。

一旦你开始了一个 ToolsRunner，一系列的可用工具将会显示。输入名称后对应的任务将会运行。

## 可用的任务

| 图标           | 名称                      | 描述                                       |
| ------------ | ----------------------- | ---------------------------------------- |
| :paperclip:  | addJavaDocToMessageEnum | 使用对应的英文信息给每一个 MessageKey 条目添加 Javadocs 注释。 |
| :flashlight: | checkMessageUses        | 寻找完全没有使用的语言条目。                           |
| :paperclip:  | checkTestMocks          | 检查测试类的 `@Mock` 字段对应测试类的 `@Inject` 字段。    |
| :green_book: | createCommandPage       | 更新 docs/commands.md 页面。                  |
| :green_book: | describeHashAlgos       | 更新 docs/hash_algorithms.md 页面。           |
| :paperclip:  | drawDependencyGraph     | 生成 AuthMe 的依赖图为 .dot 文件 - 需要 GraphWiz 渲染。 |
| :pencil2:    | generateCommandsYml     | 使用默认的数据生成 commands.yml 配置文件。             |
| :pencil2:    | generatePluginYml       | 使用最新的命令和权限信息生成 plugin.yml。               |
| :green_book: | updateConfigPage        | 更新 docs/config.md 页面。                    |
| :green_book: | updateDocs              | 更新 docs/ 文件夹中的所有文件。                      |
| :green_book: | updateTranslations      | 更新 docs/translations.md 页面。              |
| :flashlight: | verifyHelpTranslations  | 检查所有或指定的位于 resources/messages 的帮助信息文件。   |
| :flashlight: | verifyMessages          | 检查所有的或指定的位于 resources/messages 的语言文件。    |
| :green_book: | writePermissionsList    | 更新 docs/permission_nodes.md 页面。          |

### 种类

| 图标           | 条目         |
| ------------ | ---------- |
| :green_book: | Docs/ 页面生成 |
| :flashlight: | 检查任务       |
| :pencil2:    | 项目文件更新     |
| :paperclip:  | 技术性任务      |

## 标签替换

docs/ 文件夹中的 Markdown 页面基于一个模板文件。这个模板文件可能包含生成时用于替换的标签。举个例子：
```txt
A total of {total} commands are available:

[#commands]
- {name}[perm], requires {perm}[/perm]
[/#commands]
```

这里一共有这么几种标签可以使用：
- 替换： `{total}`-一样的标签将会被替换为「total」相关的值
- 条件： `[perm]...[/perm]`-一样的标签是条件性标签。只有在「perm」指代的值非空（空字符串或者空集合）才会被替换
- 重复：`[#commands]...[/#commands]` 一样的标签将会使用所有「commands」的值迭代替换

标签的值可以使用 `TagValueHolder` 指定。举个例子：
```java
List<Command> commands = Arrays.asList(
  new Command("/home", ""), new Command("/help", "permission.help"));

NestedTagValue commandsInfo = new NestedTagValue();
for (Command command : commands) {
  TagValueHolder commandValues = TagValueHolder.create()
    .put("name", command.getName())
    .put("perm", command.getPermission());
  commandsInfo.add(commandValues);
}

TagValueHolder tagValues = TagValueHolder.create()
  .put("total", commands.size())
  .put("commands", commandsInfo);

// Generate MD file
FileIoUtils.generateFileFromTemplate("commands.tpl.md", "commands.md", tagValues);
```

生成的文件会看起来像这样：
```md
A total of 2 commands are available:

- /home
- /help, requires permission.help
```

以下预定义的标签可以随时使用：
- `{gen_date}`: 生成日期（当前日期）
- `{gen_warning}`: 用于警告不要直接编辑生成的文件的注释标签
- `{gen_footer}`: 页面底部指向仓库和生成日期的链接