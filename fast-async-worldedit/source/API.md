# 需要帮助？
如果你在写代码这方面需要帮助的话，请随意在 [IRC](http://webchat.esper.net/?nick=&channels=IntellectualCrafters&fg_color=000&fg_sec_color=000&bg_color=FFF) 这里询问。

# 移植 WorldEdit API 的代码到 FAWE 中
首先，FAWE 不会修改 WorldEdit API 的表现，不过安装 FAWE 之后已经存在的代码会运行的更快。

使代码（使用 WorldEdit API的相关代码）异步工作和将它放入异步线程中一样简单（例如：使用Bukkit 的 scheduler）。

即便如此，FAWE API 也提供了目前 WorldEdit 所不能做到的一些额外功能。下面是一些 WorldEdit 和 FAWE 的例子：

# Maven
储存库（Repository）： `http://ci.athion.net/job/FastAsyncWorldEdit/ws/mvn/`  
前置（Dependency）： `com.boydti:fawe-api:<version>` 或 `com.boydti:fawe-api:latest`    
# Gradle
你能够使用Gradle来为FAWE编码，它已经在本储存库中了：
```
$ gradlew setupDecompWorkspace
$ gradlew build
```
### 线程
 - [FAWE 的性能提示](/Some-tips-when-using-the-FAWE-API.md)
 - [使用 FAWE TaskManager 来运行同步/异步任务](/Fawe-TaskManager#sync-task.md)
 - [使用 FAWE TaskBuilder 来分离复杂任务](/TaskBuilder.md)

### 玩家
 - [FawePlayer](/FawePlayer.md)
 - [WorldEdit 玩家](/WorldEdit-World-Player.md)
 - [玩家任务 API](/Jobs-API.md)
 - [玩家进度 API](/Progress-API.md)
 - [玩家区域限制](/Region-restriction-API.md)

### 异步修改世界（或是读取世界）
 - [Anvil API](/Anvil-API.md)
 - [WorldEdit 世界](/WorldEdit-World-Player.md)
 - [EditSession](/WorldEdit-EditSession.md)
 - [Bukkit API 封包器](/AsyncWorld.md)
 - [FaweQueue](/FaweQueue.md)

### NBT 与格式
 - [剪切板的粘贴](/Pasting-a-schematic.md)
 - [NBT 代码相关 API](/NBT-stream-API.md)
 - [自定义剪切板格式](/Clipboard-API.md)
 - [恢复错误的 NBT](/Recovering-corrupt-NBT-files-(MCA-Schematic-etc..md).md)

### NMS 相关概念
 - [Light API](/Light-API.md)
 - [NMSMappedFaweQueue](/FaweQueue#nms-methods.md)    
 - [发包](/Packet-sending.md)

### 网页
 - [网页 API](/Web-API.md)

### 其他功能
 - [方块和生物群系的颜色](/TextureUtil---block-and-biome-coloring.md)

### 延展特性
 - [增加自定义的任务，模型或变换参数](/Registering-Custom-Masks,-Patterns-and-Transforms.md)
 - [增加自定义笔刷和命令](/Registering-custom-brushes-or-commands.md)
 - [增加自定义剪切板格式](/Clipboard-API.md)

## FaweAPI 的类：
https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/FaweAPI.java
