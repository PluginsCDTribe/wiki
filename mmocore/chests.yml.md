# 概览

chests.yml 处理所有你的 RPG 随机掉落箱！

本 wiki 页面仍未完成，因为还有更多的掉落选项和插件兼容正在不断地加入可能的掉落表。

# 默认配置

```yaml
'world 59 71 131':

    # 直接创建你的掉落表
    drop-table:
        items:
        - 'vanilla{type=DIAMOND} 1 1-3'
        - 'gold{} .9 1-3'
        - 'gold{} .9 1-3'
        - 'gold{} .9 1-3'
        - 'gold{} .9 1-3'
        - 'gold{} .9 1-3'
        - 'gold{} .9 1-3'
        - 'note{min=1;max=10} .9 1-3'
    
    # 箱子重新生成的时间间隔（tick）
    regen-time: 40
    
    # 箱子周围每 4s 显示的例子特效
    # 可用种类 helix|offset|galaxy
    # 粒子名称在此处 https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html
    effect:
        type: helix
        particle: FLAME
```

箱子的名称，如此例中 "world 59 71 131"，定义了箱子放置的位置。它使用了 WORLD,X,Y,Z 格式。你并不需要命名你的箱子，只需要在这里写上你想要的箱子的坐标即可。

* drop-table

此选项定义了箱子里可能有什么。目前支持 MMOItems，原版物品，MMOCore 货币。格式在默认的配置中有。

每个掉落项之后的两个数字分别是掉落概率和数量。在本例中，有 .9（90%）的几率被箱子包含，有 1-3 的随机数量。

* regen-time

箱子重新生成并包含随机掉落的事件，当箱子被打开和清空后，它将被删除。箱子被破坏后也会将其所有物品掉落到地上。

* Effect

为了让掉落箱比较显眼，你可以在箱子上弄一些粒子特效告诉玩家这些箱子比较特殊。你也可以使用这些粒子特效决定箱子的等级，直接给不同掉落物的箱子以不同的特效就行！
