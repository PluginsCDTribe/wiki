材质和模型定义文件遵循一些常见的格式惯例：
* 每个定义都是面向单行的，尽管部分定义会影响到下一行的定义
* 所有行按照文件中的顺序处理
* 以数字符号（#）或分号（;）将被视为一条注释并被忽略
* 任何一行都可以以版本限制开始，只允许在 Minecraft 的特定版本或与文件相关的 Mod 的特定版本进行处理。对于 Minecraft 的版本限制，格式为 `[<低版本>-<高版本>]`，&lt;低版本&gt;为可选的，&lt;高版本&gt;为最大可用的 Minecraft 版本（如，`[1.5.0-1.6.4]` 将会导致该行仅在 Minecraft 1.5.0 到 1.6.4 版本之间才被处理，`[-1.6.4]` 将不会在任何版本高于 1.6.4 的 Minecraft 中被处理，而 `[1.5.2-]` 将会在 Minecraft 高于 1.5.2 时进行处理）。对于 Mod 版本限制，格式是类似的：`[mod:<低版本>-<高版本>]`。

纹理和模型定义文件都支持以下的定义行，这些通常用于文件的开头：
* 'version:' - 如果设置，此选项指定了对 Minecraft 版本的限制。该行的格式为 `version:<低版本>-<高版本>`，`<低版本>` 和 `<高版本>` 指定了 Minecraft 的最小和最大的可用版本。如果指定的范围与实际不符，那么此文件将终止处理，并且不会被使用。
* 'modname:' - 如果设置，此选项指定了相关的 Mod 的名称，这是区分大小写的，必须和 Mod 名称相同，如果使用不同的名称（比如不同的版本），可以提供多个版本（使用逗号分隔）。每个名称后面都可以添加可选的版本限制 `[<低版本>-<高版本>]`，这样只有安装了指定的 Mod 并且版本相符才会使用该定义文件。例如，`modname:BiomesOPlenty[-0.5.8]` 将只有在安装了 BiomeOPlenty 0.5.8 之前的版本才会加载此定义文件。
* 'cfgfile:' - 如果设置，则设置寻找配置文件的相对路径（假设格式为 Minecraft Forge 的标准配置文件的格式）。这会让相关的配置文件加载，并且定义不同种类的设置的符号（特别是不同的方块 ID）。查看[配置设定](/Configuration.md)查看详细信息。
* 'var:' - 如果设置，这将为配置文件的没有设置的选项设置默认值（比如老版本没有的方块的 ID）。设置的格式为使用逗号分隔的 `<属性>=<数字>` 列表。（比如 `'var:template.id=0,architect.id=0,pathMarker.id=0`）。如果需要添加 var 行，请在 cfgfile: 之前添加它们（否则将会覆盖配置文件的值）。

## 配置设定映射
通过 `cfgfile:` 行加载的配置文件将产生可用的符号，配置文件的选项的名称映射到这些符号的方法如下：
* 每个设置将会和和它包含的子设置结合，以 `/` 作为分隔，比如 "blocks" 下的 "my Block ID" 设定将转换为 `blocks/my Block ID`。
* 这些符号的任何空格将会转换为下划线，如 `blocks/my Block ID` 将转换为 `blocks/my_Block_ID`。
* 如果设置以 "block/" 或者 "blocks/" 开头，那么将会将这一部分去除，如 `blocks/my_Block_ID` 将会转换为 `my_Block_ID`，但是 `biomes/my_Biome` 不会发生改变。
* 如果符号以 "item/" 开头，那么将会替换为 `item_`，如 `item/myItem` 将会转换为 `item_myItem`。
* 最终，属性值与符号连接。

配置文件中的符号可用于定义文件中的各种特定情况（最常用于方块 ID 属性值）。尝试使用未使用过的符号 - 通过配置文件或通过 `var:` 定义行 - 将在加载定义文件时发生错误。
