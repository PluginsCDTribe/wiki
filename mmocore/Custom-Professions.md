MMOCore目前有7个默认的职业，你还可以创建自定义的职业来让你的玩法变得更有趣。职业可以有特定的**经验来源**（即可以使某特定职业的玩家获得经验的行为）。

当玩家获得了足够的经验时，他们不仅可以升级他们的职业，而且还可以获得一些种族经验来升级他们的主等级并给他们提供技能点。

## 经验来源
让我们看一下这个例子。以下伐木职业的默认的经验来源。当玩家砍下一根木头时一般会给予玩家1-3个经验点。
```yaml
exp-sources:
- 'mineblock{type=OAK_LOG;amount=1-3}'
- 'mineblock{type=SPRUCE_LOG;amount=1-3}'
- 'mineblock{type=BIRCH_LOG;amount=1-3}'
- 'mineblock{type=JUNGLE_LOG;amount=1-3}'
- 'mineblock{type=ACACIA_LOG;amount=1-3}'
- 'mineblock{type=BIRCH_LOG;amount=1-3}'
- 'mineblock{type=DARK_OAK_LOG;amount=1-3}'
```

以下是是农耕职业的默认经验来源，当玩家收割任何类型的农作物时，都会获得一些经验点。
```yaml
exp-sources:
- 'mineblock{type=CARROTS;amount=1-3}'
- 'mineblock{type=POTATOES;amount=1-3}'
- 'mineblock{type=WHEAT;amount=1-3}'
```

## 全部经验来源
| 来源 | 用法 | 描述 |
| - | - | - |
| 击杀怪物 | `killmob{type=MOB_ENTITY_TYPE}` | 击杀一个普通怪物以获取经验 |
| 击杀MythicMob的怪物 | `killmythicmob{type=MobInternalName}` | 击杀一个MythicMob以获取经验 |
| 钓上物品 | `fishitem{type=ITEM_MATERIAL}` | 在钓鱼时钓上一个物品会获取经验 |
| 开采矿物 | `mineblock{type=BLOCK_MATERIAL}` | 在开采一个矿物时获取经验 |
| 熔炼物品 | `smeltitem{type=ITEM_MATERIAL}` | 在熔炉中熔炼一个物品时会获取经验 |
| 酿造药水 | `brewpotion{type=SPEED,REGEN,...}` | [详见 酿造术](Alchemy) |

## 配置文件举例: smelting.yml
```yaml
# 展示名
name: Smelting

# 给予主等级的经验
# 在升级这个职业时
experience:
    base: 20
    per-level: 3
```
所有职业的配置文件都保存在 /MMOCore/profession 文件夹中。你可以配置职业的展示名称以及玩家在升级该职业时所需的经验。
