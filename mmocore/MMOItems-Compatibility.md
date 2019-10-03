MMOCore 生来与 [MMOItems](https://www.spigotmc.org/resources/mmoitems-premium.39267) 一同使用，尽管它不是一个依赖。MMOCore 提供了大量与 MMOItems 的兼容选项，以下是一个详细的列表。

## 更多的 MMOItems 属性
当同事使用 MMOCore 和 MMOItems 时，额外的物品属性将会自动启用并添加到 MMOItems 的物品编辑 GUI 中。

| 属性 | 描述 |
| - | - |
| Max Mana | 默认的魔力属性，但是它支持 MMOCore |
| Max Stellium | 允许添加额外的 MMOCore 星能 |
| Mana Regeneration | 增加 X% 的魔力恢复量 |
| Stellium Regeneration | 增加 X% 的星能恢复量 |

## 额外的掉落表物品
| 物品 | 用法 | 描述 |
| - | - | - |
| mmoitem | `mmoitem{type=MMOITEM_TYPE;id=MMOITEM_ID} <几率> <min-max>` | 添加一个 MMOItems 到 MMOCore 的[掉落表](Drop-Tables)中 |

## 任务目标及触发器
MMOItems 添加新的[目标](Quest-Folder)到 MMOCore 的任务中，玩家需要获得一个物品并交到指定的 Citizens NPC 处。你可以设置[触发器](Quest-Folder)，指定需要给一个指定的 MMOItems 物品作为目标。最后，你可以添加 MMOItems 到 MMOCore 的掉落表中。

## 物品限制，魔力
MMOItems 提供了物品限制，包括等级和种族的限制，与 MMOCore 兼容。MMOItems 的魔杖物品也可以使用魔力或者耐力/星能，这也被 MMOCore 支持。

## MMOItems 合成的额外特性
在 MMOItems 中，部分配方需要有特定的条件达到才能使玩家可以合成。MMOCore 添加了职业等级限制，比如玩家必须达到某些等级的 X 级，才可以使用这个配方。
**条件格式** `profession <profession-name> <level-required>`

**样例配方**，玩家需要达到 5 级的修理。
```yaml
    steel-sword:
        output:
            type: SWORD
            id: STEEL_SWORD
        conditions:
        - 'profession smithing 5'
        ingredients:
        - 'vanilla STICK . 2 Steel_Ingot'
        - 'mmoitem MATERIAL STEEL_INGOT 4 Steel_Ingot'
```

MMOCore 也添加了新的合成触发器（当一个配方被使用的时候），可以用于给玩家经验（主经验或者对应职业的经验）。
**触发器格式** `exp <profession-name> <experience-amount>`

**样例**，使用后获得 10 点修理等级的经验。
```yaml
    steel-sword:
        output:
            type: SWORD
            id: STEEL_SWORD
        ...
        triggers:
        - 'exp smithing 10'
```