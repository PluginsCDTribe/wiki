这是一篇技术性文章，描述未登录玩家（Limbo Player）如何被处理。请先参考 [未登录玩家](Limbo-players) 来获得一个基础的、非技术性的概览。

![](https://s30.postimg.org/i09vy2pqp/Untitled_Diagram.png)

加粗的类名是 public 开放的：这些类在 limbo 包以外使用，用于实现该特性。剩下的类在 limbo 包内部使用。

- **LimboPlayer** 是有 limbo 属性的对象
- **LimboService** 保存 LimboPlayer 对象在内存中，对外提供方法
- **LimboServiceHelper** 是一个到 LimboService 的工具类，压缩了一些更长的操作
- **LimboPlayerTaskManager** 也是一个到 LimboService 的工具类，处理大多数的 liimbo 任务（见下）
- **LimboPersistence** 用于 LimboService 读写 LimboPlayers 到磁盘
- **LimboPersistenceHandler** 是一个有多种实现的接口。这个实现取决于配置文件。正确的实现用于 LimboPersistence 进行实际的 I/O 操作。每次重载时（如果配置变更则是新的实例/实现）都会更改 LimboPersistence 使用的实现。

### 概念

LimboPlayer 的目的是在玩家正式登陆之前限制他的部分功能。这些功能存储在 LimboPlayer，为了能存储这些值，我们将其存储在 LimboPlayer。

LimboPlayer 创建于每次玩家登陆、登出或者注销。这些 LimboPlayer 的值在玩家退出服务器、登陆之后被储存。

### Limbo 任务

除了移出对玩家的特定功能以外，我们同时也会创建两个有关于玩家的任务：
- MessageTask 是一个不断重复运行，告诉玩家注册或者登入的任务。
- TimeoutTask 保证玩家在配置的时长后仍然未登陆或登陆失败时将其踢出。

当一个 LimboPlayer 存储时（从内存中移出），这些任务将会被取消。

### 未登录玩家合并

存在多个 LimboPlayer 对象对应同一个玩家是可能的，在这种情况下，我们将每个 LimboPlayer 的数据合并，创建一个新的、结合了之前所有数据的 LimboPlayer 实例。

考虑这种场景：假设一个玩家没有登入，一个对应这个玩家的 LimboPlayer 将存储在内存中。如果一个管理员在这个玩家没有登录时注销了他，另一个 LimboPlayer 的创建将被触发。

我么将会保证最相关的数据，通过取每个 LimboPlayer 的最大值：最大速度，是否是 OP，是否允许飞行。我们将这些存储进新的 LimboPlayer。

### 文件存储

每个 LimboPlayer 经常在创建时也储存进了磁盘。在服务器崩溃时，AuthMe 不会有机会存储 LimboPlayer 的数据，然后它们就从内存中丢失了，这导致玩家丢失了他们的速度、OP 状态等的数据。将 LimboPlayer 保存到文件可以解决这个问题。

当一个 LimboPlayer 被储存时，这个 LimboPlayer 也会被从磁盘冲删除。当新的 LimboPlayer 被创建时，我们会先检查磁盘中是否有一个对应的 LimboPlayer 文件，如果有，则我们将会重新进行一次新创建和磁盘的 LimboPlayer 的合并。

### 存储类型

存储可以在 config.yml 配置。我们有以下几种实现：
- NoOpPersistenceHandler: 「空」类，不进行任何 I/O
- SeparateFilePersistenceHandler: 保存每个 LimboPlayer 到单独的文件
- SingleFilePersistenceHandler: 保存所有的 limbo players 到同一个文件，并且保持在内存中（在初始化后，只会写入不会读取）
- SegmentFilesPersistenceHolder: 保存 limbo players 到可以配置的个数的文件中。见下。

#### 分离文件存储

分离文件存储保存所有的 limbo players 到可以配置的个数的文件中。基于每个玩家的 UUID，我们将会创建一个用于文件名的分离 ID。定义一个分离 ID 需要两个值：「分配」和「长度」。

UUID 使用十六进制的数字，比如 0-9a-f — 一共16个字符。**「分配」** 定义了每个字符对应多少输出。如果「分配」为 4，任何在 0-9a-f 中的字符将会转换为 4 个字符中的一个。这通过将十六进制的数字转换为小数，然后使用 `(16 / distribution)` 除这个数，然后向下取整得到结果。为得到相同的分配，必须选择 2 的 N 次方作为分配值。

举个例子：
```
分配 = 4, 字符 = 'a'
--> 输出 = hexToDec(字符) / (16 / 分配) = 10 / (16 / 4) = '2'
```

**「长度」** 定义了 UUID 的多少字符应该用于创建分离 ID。所以长度为 3 分配为 2 意味着前三个字符将被用于映射到两个不同的输出，创建 `2^3 = 8` 种不同的可能性：

```
给出: 分配 = 2, 长度 = 3, uuid = 7e32aa0e-6bd2-4779-a775-6258b79062e9
取前 3 个字符, 7e3:

分离 ID = floor(hex2dec(7) / (16/2)) . floor(hex2dec(e) / (16/2)) . floor(hex2dec(3) / (16/2))
          = floor(7/8) . floor(14/8) . floor(3/8) 
          = 010
```
UUID 为 `7e32aa0e-6bd2-4779-a775-6258b79062e9` 的玩家被存储于 `010` 作为文件名的文件。

另一个例子：
```
给出: 分配 = 8, 长度 = 2, uuid = 6d205dc8-a0b3-42b0-85d4-5b87023a8ab7
取前 2 个字符, 6d:

分离 ID = floor(hex2dec(6) / (16/8)) . floor(hex2dec(d) / (16/8))
          = floor(6/2) . floor(13/2)
          = 36
```

查看 `SegmentConfiguration` 枚举获得所有可用的配置选项。