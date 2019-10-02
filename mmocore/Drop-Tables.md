`/drop-tables` 目录用于存放你所有自定义的方块掉落表。掉落表目前提供了对原版物品、MMOItems、和其他的掉落表的支持。所以你可以在掉落表中嵌套掉落表，以提供不同的掉落物品可能性。

## 默认配置
```yaml
# 你可以创建任意多的你想要的掉落表
# 你也可以在掉落表中引用其他的掉落表
#
# 不要试图创建递归的掉落表（也就是调用自身的多次掉落物品）
# 这能按照你的预期运行，但是如果你设置概率为接近 1 的数字，这会让你的服立刻崩掉。
# 概率的值越大，你服可能就越卡。算个冷知识吧.jpg

diamond-drop-table:
    items:
    - 'vanilla{type=DIAMOND} 1 1-3'
    - 'mmoitem{type=material;id=RARE_DIAMOND} .1 1-3'
    - 'droptable{id=other-drop-table} .1'

other-drop-table:
    items: []
```

这个部分应该是不言自明的，并且经中此篇最是详细，且有注释细细道来。首先你要命名你的掉落表，此例中名为 `diamond-drop-table`。我们都知道在 wiki 中的 blocks.yml 这个掉落表在破坏一个钻石矿的时候被触发。

掉落的物品是原版的钻石，一个 MMOItems 的稀有钻石（RARE_DIAMOND），以及一个引用的样例掉落表以便展示语法。在物品之后的数字表示几率，接着是数量。数量可以是一个范围。

## 可用的掉落表项目
| 掉落物 | 格式 |
| - | - |
| 另一个掉落表 | `droptable{id=drop-table-id} <几率> <数量>` |
| 原版物品 | `vanilla{type=ITEM_MATERIAL} <几率> <数量>` |
| 金币 | `gold{} <几率> <数量>` |
| 纸币 | `note{min=MIN_WORTH;max=MAX_WORTH} <几率> <数量>` |