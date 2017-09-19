这里我们将会介绍配置的结构和如何编辑配置。

文件 `plugins/dynmap/configuration.txt` 的配置为 YAML 格式，这种格式使用锁紧结构，很重要的一点就是**不能含有任何TAB**，只能有空格，所以你必须将正确数量的空格放置在配置之前。

仅作为参考，你可以查看这里的默认配置：
https://github.com/webbukkit/dynmap/blob/recommended/src/main/resources/configuration.txt.

配置文件包含 4 部分，以部件、全局设定、世界模板、世界的顺序排列。全局设定更改渲染和Dynmap的（内部）Web服务器的表现，这是很显然的。一个示例全局设定：

```yaml
# How often a tile gets rendered (in seconds).
renderinterval: 1
```

**注意:** 在版本 v0.20，默认的 configuration.txt file 被分离了， _templates:_ 章节被移动到了 **templates/** 目录， _worlds:_ 章节被移动到了 **worlds.txt** 文件。用户不是必须更改他们现有的 configuration.txt - configuration.txt 定义的模板或世界仍然生效，并且会覆盖 templates/ 下的相同名称的模板。推荐已经使用的用户，尽快将 _worlds:_ 章节（如果已经设置），从 **configuration.txt** 移动到 **worlds.txt**，放置以后的更新可能出现的冲突和影响。当然，现有的用户最好也把 _templates:_ 章节从 **configuration.txt** 移动到新的文件 **templates/custom-templates.txt**。

## 部件（Component） ##

部件部分看起来像这样：

```yaml
components:
  - class: org.dynmap.ClientConfigurationComponent
  
  - class: org.dynmap.InternalClientUpdateComponent
    sendhealth: true
    allowwebchat: true
    webchat-interval: 5
...
```

每个不换都可以认为是Dynmap的一个单独的特性，可以被单独开启或者关闭。有些不见基于其他的部件，但是我们不会深入。配置文件中的部件都以 `- class: ...` 开头，接着是部件的设置。

作为示例，我们会关闭处理聊天气泡的部件。这个部件看起来像这样：

```yaml
...
  - class: org.dynmap.ClientComponent
    type: chatballoon
    focuschatballoons: false
...
```

我们可以通过删除这几行来关闭这个部件，但是更安全的方法是将他们变为注释。这个示例中：

```yaml
...
  - class: org.dynmap.ClientComponent
    type: chat
  #- class: org.dynmap.ClientComponent
  #  type: chatballoon
  #  focuschatballoons: false
  - class: org.dynmap.ClientComponent
    type: chatbox
    showplayerfaces: true
    messagettl: 5
...
```

确保 `#` 之前仍然有正确的空格数。
保存配置后，重载Dynmap，刷新浏览器，聊天气泡不会再出现了。
同样的方法可以用来启用已经禁用的部件。

查看更多的部件和他们的配置可以查看[部件配置](/Component-Configuration.md)。

## 世界与模板 ##

在这个配置你会看到一个 world 章节（从 0.20 开始），可以在 **worlds.txt** 找到（之前是在 **configuration.txt** 的底部）。这个章节可以留空 - Dynmap将会找到服务器加载的所有世界，并提供一个默认的地图设定，基于使用 **模板**，定义于 _templates:_ 章节。从 0.20 开始，模板定义从 **configuration.txt** 移动到了单独的文件，在 **templates/** 目录中。但是之前的方式仍然生效。

关于世界设置的全面的介绍，查看[世界与模板设定](/World-and-template-settings.md)。
### 模板

默认有 3 种模板：普通，地狱和空岛。模板基于世界的环境自动选择 - **normal** 为普通的世界，**nether** 为地狱世界，**skylands** 为空岛世界。在 0.20 版本中，这些定义可以在 **templates/** 目录找到，使用相应的名称“ **templates/normal.txt**，**templates/nether.txt** 和 **templates/skylands.txt**。

在 0.20，模板的名称可以使用 configuration.txt 中的 _deftemplatesuffix_ 设定来变更。如果设置了，那么世界使用的模板的名称将会添加 `-` 和 _deftemplatesuffix_ 设定的结果：所以设定 _deftemplatesuffix_ 为 **hires** 将会造成 **normal-hires** 模板启用于所有的普通世界，**nether-hires** 启用于所有的地狱世界，**skylands-hires** 启用于所有的空岛世界。这会允许Dynmap（和其他的用户）使用预置的前缀设定，可以在 _deftemplatesuffix_ 轻松设定。在 0.20版本，提供了 3 中默认的模板。

- 默认 (**normal**,**nether**,**skylands**)

- **lowres** 模板集 (**normal-lowres**, **nether-lowres**, **skylands-lowres** - 提供更低解析度的地图（默认的2倍）。

- **hires** 模板集 (**normal-hires**, **nether-hires**, **skylands-hires** - 提供更高解析度的地图 - 大概是默认地图的8倍 - 'lowres' 版本用于平原和洞穴地图。

在所有的情况下，模板的定义可以在 **templates/** 目录找到，使用对应的名称，加上 **.txt** (比如 **normal-hires** 可以在 **templates/normal-hires.txt** 找到)。

### 世界

配置文件中，在模板章节附近还有一个世界设置。在 0.20 版本，推荐的配置文件的位置是 **worlds.txt** 文件。这里我们可以指定每个世界的单独的设置。我们会使用一些例子让你理解。

基本上每个世界都有一些默认的值。 _title_ 设置为世界的名称， _template_ 设置为世界的环境（如果 _deftemplatesuffix_ 在 **configuration.txt** 中被定义，那么有一个短横线和 _deftemplatesuffix_ 跟随）。这个世界的模板可以覆盖这些值，但是这些世界设定里的值可以覆盖模板的设定。

如果你有 3 个世界，名称为 **world**, **nether** 和 **alternative**，然后你像让他们以**明确的顺序显示**，你可以将其放入你的配置里：

```yaml
worlds:
  - name: world
  - name: alternative
  - name: nether
```

这样他们就以 **world**, **alternative**, **nether**的顺序出现。

**更改某个世界的标题**，你可以在配置添加title的配置：

```yaml
worlds:
  - name: world
    title: "My Super Awesome World"
  - name: alternative
  - name: nether
```

你可以对所有的世界都这样做。

如果你想要**关闭某个世界**，比如世界**alternative**，你可以在配置添加 _enable: false_：

```yaml
worlds:
  - name: world
    title: "My Super Awesome World"
  - name: alternative
    enabled: false
  - name: nether
```

你可以使用这个设置在你的模板里停用所有某一环境的世界。

如果你想要**更改某个世界的特定的设置**，你可以使用这个设置。这个设置还包含了 _maps:_ 属性，这样你就可以指定世界使用的地图了：

```yaml
  - name: world
    title: "My Super Awesome World"
    center:
      x: 100
      y: 64
      z: 0
    maps:
      - class: org.dynmap.flat.FlatMap
        name: flat
        title: "Flat"
        prefix: flat
        colorscheme: default
```

这将让这个世界，设置中心为 (100,64,0)，并且只在侧边栏显示平坦地图。

最终如果你**有多个世界使用相同的设置**，你可以添加一个模板到 _templates:_ 部分（或者最好添加一个自定义分模板文件到 **templates/** 目录），然后指定这些世界的模板。

```yaml
templates:
  mycustomtemplate:
    enabled: true
    maps:
      - class: org.dynmap.flat.FlatMap
        name: flat
        title: "Flat"
        prefix: flat
        colorscheme: ovocean
...
worlds:
  - name: world
    template: mycustomtemplate
  - name: nether
    template: mycustomtemplate
  - name: alternative
```

这里 **world** 和 **nether** 都使用 **mycustomtemplate** 模板，但是 **alternative** 会使用 **normal** 模板（因为这个示例中 **alternative** 有普通的世界环境）。

就像上面你能看见的一样，每个 FlatMap 或者 KzedMap 地图都可以设置一个特定的颜色主题。颜色主题可以在 **plugins/dynmap/colorschemes/**, 也可以在[这里](https://github.com/webbukkit/dynmap/tree/recommended/colorschemes)看到。一个关于这些的简介可以在[颜色主题](/Color-Schemes.md)找到。

在 0.20 版本，一个新的地图种类出现了 - HDMap。这种地图种类，支持更高解析度的地图渲染，并且支持使用材质包，并且支持所有 FlatMap 和 KzedMap 的特性，但是更加灵活（允许自定义的观察角度，自定义的观察方向和缩放大小，等等）。有关配置 HDMaps 的详细信息，请查看[HD Map 配置](/HD-Map-Configuration.md)。
