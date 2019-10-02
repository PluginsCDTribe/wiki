# 概览

配方目录分为几个不同的文件。Brewing.yml, Furnace,yml, 和 smithing.yml。在这里你可以设置自定义的酿造、熔炼和修复自定义 RPG 工具。

# Brewing.yml

```yaml
# 每个酿造配方需要一个空水瓶
# 请确保每个不同的酿造配方需要有一个不同的 ID
# 这只是作为插件内部的处理，没有其他用处

# 酿造配方 ID
mana-pot-recipe:

    # 用于酿造空水平的材料
    ingredient: MATERIAL.MANA_FLOWER
        
    # 酿造完成后替换原有控水平的物品
    result: CONSUMABLE.MANA_POTION
        
    # 酿造所需的时间
    cook-time: 10
```

创建一个自定义配方炒鸡简单。首先给他一个 ID，只需要和别的都不一样，因为它不在游戏内显示。

`ingredient` 是你需要放入的第一个东西，这是一个用于酿造的 MMOItems 物品。在本例中，这是拥有 MANA_FLOWER 的 MMOItems 物品。当你将其放入空水瓶中，它将开始酿造。

`result` 是酿造的输出产品。在本例中，酿造完成后将会给玩家一个 MMOItems 的可消耗物品，ID 是 MANA_POTION。

`cook-time` 是酿造花费的时间。

你可以通过使用原有的配方的输出产物创造高等级的配方，作为输入而制造更强力的药水。

# Furnace.yml

```yaml
# 请确保每个不同的熔炼配方需要有一个不同的 ID
# 这只是作为插件内部的处理，没有其他用处

# 熔炼配方 ID
emerald-recipe:

    # 用于熔炼的物品
    ingredient: MATERIAL.EMERALD_GEODE
        
    # 输出的产物
    result: MATERIAL.SHINY_EMERALD
        
    # 熔炼物品所需的时间
    cook-time: 10
```

这里是你设置自定义的熔炼配方的地方。

首先你需要分配给他一个 ID，本例为 `emerald-recipe`。

接着你选择一个原料 `ingredient`，这是被熔炼的物品。

接着你选择产物 `result`，作为输出。

原料和产物都是 MMOItems，本例中输入是 EMERALD_GEODE 而输出是 SHINY_EMERALD。

`cook-time` 指定熔炼的时长。

**注意：一开始有点 bug，物品可能不在熔炉中重叠。**

# Smithing.yml

```yaml
# 你想要修复的对应的职业/工具种类
FISHING:

    # 用于修复的 MMOItems 的物品 ID
    REPAIR_FISHING:
     
        # 用量
        amount: 10
            
        # 修复获得的修理职业的经验
        exp: 3
    
    REPAIR_FISHING2:
        amount: 20
        exp: 5
    
WOODEN:
    REPAIR_WOODEN:
        amount: 10
        exp: 3
    REPAIR_WOODEN2:
        amount: 20
        exp: 6
            
STONE:
    REPAIR_STONE:
        amount: 10
        exp: 4
            
IRON:
    REPAIR_IRON:
        amount: 20
        exp: 5
           
GOLDEN:
    REPAIR_GOLDEN:
        amount: 20
        exp: 5
            
DIAMOND:
    REPAIR_DIAMOND:
        amount: 30
        exp: 7
```

这里是你用来设置使用 MMOItems 修复对应 MMOCore 的工具，使用 `/rpg tool` 管理员命令。

FISHING: 代表一个钓鱼竿，`amount` 是修复的用量，`exp` 是获得的修理职业的经验。

WOODEN: 代表一个木制工具。镐子，斧头，锄头，等等。子项配置与 FISHING 相同。

**很多人不会去使用这个功能，因为需要 MMOItems 的自定义物品和自定义铁砧**