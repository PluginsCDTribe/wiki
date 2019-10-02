# 概览

restrictions.yml 是你设置工具可以挖掘哪些类型的方块的地方。你可以利用这来实现类似每升级 20 级解锁下一种类型的方块。

# 默认配置

```yaml
# Mining a block in creative will NOT drop any
# custom drops/will not apply block regen, etc.
#
# Any block specified in this config, wherever it
# is located, MUST be mined using the correct tool
# otherwise nothing will drop!

# The corresponding tool. It's CASE_SENSITIVE!
WOODEN_PICKAXE:

    # What the tool can mine.
    can-mine:
    - COAL_ORE

STONE_PICKAXE:
    can-mine:
    - IRON_ORE
    
    # The block break permissions the tool inherits.
    # e.g a stone pickaxe can mine iron ores PLUS
    # any block that the wooden pickaxe can mine.
    # Used to make the config much clearer.
    parent: WOODEN_PICKAXE

IRON_PICKAXE:
    parent: STONE_PICKAXE
    can-mine:
    - GOLD_ORE

GOLDEN_PICKAXE:
    parent: IRON_PICKAXE
    can-mine:
    - LAPIS_ORE

DIAMOND_PICKAXE:
    parent: GOLDEN_PICKAXE
    can-mine:
    - DIAMOND_ORE
    - EMERALD_ORE
    - REDSTONE_ORE
```

默认情况下，该配置只设置了挖矿，并且包含了所有类型的镐子。你**可以**添加斧头，铲子之类的东西到这个列表里，并给他们自己一些限制。

这些选项也十分的简单。你从选择工具开始，接着是可以挖掘的东西。

`parent` 项用于设置你的工具升级时，你想要更强力的工具可以自动继承更弱的工具。这是个很好的规划特性。
