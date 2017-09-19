# 世界配置 #

`configuration.txt` 以掳爱那个部分呢需要在设置 Dynmap 的多世界时检查。第一个仅用于服务端的地图渲染，另一部分是关于浏览器怎样显示地图（当然还有什么地图）。

以下是 `configuration.txt` 的这两部分，你可以看见这个示例包含了两个世界：`world` 和 `nether`。
世界 `world` 有两张地图，但是这看起来可能不是很显而易见，因为看起来像是只有一张地图。实际上我们设置了两个渲染器，地图有两个前缀，这指定了 `minecraft_server/plugins/dynmap/web/tiles/world/` 中的 tiles 的文件名。这些前缀对于这些世界必须是独一无二的。

另一个世界叫 `nether`，只有一张地图。注意此地图有一个特殊的设置 `maximumheight`，这指定了渲染器不渲染的部分，这是为地狱环境准备的选项，因为地狱的上方全是基岩，不用渲染。

## 服务端的部分 ##
```yaml
# The maptypes Dynmap will use to render.
worlds:
  - name: world
    maps:
      - class: org.dynmap.kzedmap.KzedMap
        renderers:
          - class: org.dynmap.kzedmap.DefaultTileRenderer
            prefix: t
            maximumheight: 127
          - class: org.dynmap.kzedmap.CaveTileRenderer
            prefix: ct
            maximumheight: 127
  - name: nether
    maps:
      - class: org.dynmap.kzedmap.KzedMap
        renderers:
          - class: org.dynmap.kzedmap.DefaultTileRenderer
            prefix: nt
            maximumheight: 64
```

## 网页的部分 ##
```yaml
web:
    defaultworld: world
    worlds:
      - title: World
        name: world
        maps:
          - type: KzedMapType
            title: Surface
            name: surface
            prefix: t
          - type: KzedMapType
            title: Cave
            name: cave
            prefix: ct
      - title: Nether
        name: nether
        maps:
          - type: KzedMapType
            title: Surface
            name: nether
            prefix: nt
```

## 如何进行 ##
保证：

* 你的世界文件夹在 `minecraft_server` 的根部目录，比如 `minecraft_server/world` 和 `minecraft_server/nether`。
* 你的世界文件夹就在 `minecraft_server` 文件夹中，和 `craftbukkit*.jar` 同级，而不是什么子目录。
* 你的世界文件夹没有去怪的符号，只有数字字母和下划线。
* 服务器部分和网页部分的世界的 `name` 设置都匹配你的世界文件夹的名称，比如 `world` 或 `nether`。注意这些名称是**大小写敏感**的。
* `defaultmap` 匹配网页部分的一张地图的名称，再次注意这些名称是**大小写敏感**的！
* 如果你更改了 `prefix` 变量，那么应该在服务端部分和网页部分同时更改。
* 重启服务器后，在世界中放置和破坏一些方块看看效果。你的角色应该在世界上可见，你可以点击你的角色来快速到达角色所在的世界。
