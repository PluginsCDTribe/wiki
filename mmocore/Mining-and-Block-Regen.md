**方块再生** 可让你指定方块被挖掘后重新生成一个。这是一个非常实用的 RPG 工具，你不必再担心开放生存世界中 _有限_ 的资源量。如果你不使用对某个特定的（config.yml）世界的[方块限制](restrictions.yml)，那么这些再生设置**不会在那个世界中生效**。该设置对那些不想启用自定义方块限制的世界的玩家来说十分有效。

MMOCore 也可以让你完全覆盖原版的方块掉落表，加入更加复杂的掉落表，使用自定义物品和 MMOItems 支持。你可以为每个方块完全关闭原版掉落表。

你可以在任意的职业配置文件中设置方块再生和方块掉落表，尽管我们接下来将会看一看 Mining 职业的方块掉落表（矿石，石头）。

![](https://i.imgur.com/xiL4NX0.gif)

## 配置样例： /professions/mining.yml

```yaml
on-mine:
    EMERALD_ORE:
        drop-table:
            items:
            - 'vanilla{type=EMERALD} 1 1-9'
        vanilla-drops: false
        regen:
            time: 2000
            temp-block: STONE
        triggers:
        - 'exp{profession=mining;amount=32}'

    DIAMOND_ORE:

        # 参考 drop-tables.yml
        # 方块使用的掉落表
        drop-table:
            items:
            - 'vanilla{type=DIAMOND} 1 1-3'
           # - 'mmoitem{type=material;id=RARE_DIAMOND} .1 1-3'
           # - 'droptable{id=other-drop-table} .1'
        
        # 破坏方块的触发器，可以用于给玩家增加经验！
        triggers:
        - 'exp{profession=mining;amount=20}'
        
        # 如果你想禁用原版掉落，设置为 false
        vanilla-drops: false
        
        regen:
        
            # 方块再生的时长（tick）
            time: 2000
            
            # 方块再生时显示的临时方块
            #
            # !! 警告 !!
            # 当使用临时方块选项的时候，
            # 请确保使用一个没有在其他配置文件中使用的方块种类，
            # 以避免影响其他的方块再生
            temp-block: STONE
```

* **DIAMOND_ORE**\
这决定了被影响的被挖掘的方块

* **drop-table**\
这决定了对应方块破坏后掉落的物品。可以是一个全新的掉落表，或者是其他掉落表的 ID，也就是你提前在 `/drop-tables` 目录下设置的掉落表。

* **regen-time**\
这是方块重新变回原来的方块的时长，在这里是钻石矿。

* **temp-block**\
这是原来的方块正在再生时显示的临时方块。

所以在如上的样例中，当一个钻石矿被挖掘时，将会选用对应的掉落表，钻石矿将会变成石头。然后这个石头将在 **2000 刻**（1分钟40秒）后重新变为钻石矿以供挖掘。
