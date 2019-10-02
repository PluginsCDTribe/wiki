MMOCore 可以用于覆盖默认的钓鱼掉落表。

## 钓鱼的经验
使用 `fishitem` [经验源](Custom-Professions)，你就可以让玩家在钓到特定的物品后获得一定量的经验，比如鱼，附魔书，马鞍等等。钓上的物品越稀有，玩家应获得的经验就越多。

---

目前来说， `fishitem` 经验源只支持物品材料，也就是说玩家在钓到修理附魔书和力量I附魔书不能获得不同的经验。对于不同物品绑定不同的经验量的唯一方法就是与 MMOItems 联动，并使用 fishing.yml 职业配置文件的掉落表。

**如果你基本不想利用职业系统**，你就直接忽略掉钓鱼经验源，直接使用无经验的掉落表就可以了。**如果你不想使用 MMOCore 的钓鱼掉落表**，反之亦然。

---

## 配置样例 /professions/fishing.yml
```yaml
name: Fishing
experience:
    base: 20
    per-level: 3

exp-sources: {}

# 覆盖 Minecraft 默认的钓鱼掉落表。
# 当钓鱼时，插件读取所有的掉落表，
# 并选自第一个所有条件都满足的。
# 你必须将条件最多的、最重要的掉落表放在第一个。
# tugs 的数量等于需要对鱼点击的次数
on-fish:
    overriding-drop-table:
        conditions:
        - 'region{name=swamp,second-region}'
        
        # 当掉落表被选中，其中的一个物品将会被随机选中
        items:
        
        # 点击数 4 到 5
        # 钓鱼经验 1 到 6
        - 'mmoitem{type=CONSUMABLE;id=SUSHI_ROLL;tugs=30-40;experience=1-6}'
        
        # 点击数 10 到 20
        # 钓鱼经验 20 到 30
        - 'mmoitem{type=GEM_STONE;id=SPITEFUL_OPAQUE_DIAMOND;tugs=10-15;experience=20-30}'

    # 默认的掉落表总是被使用。
    # 所有掉落表被移除后，
    # 将会使用原版的掉落机制。
    default:
        items:
        - 'vanilla{type=SALMON;tugs=4-5;experience=1-6}'
```

_如你所见，默认的钓鱼配置并不利用钓鱼经验源，尽管你可以加入任意多的。_ 钓鱼掉落表由两个选项定义：条件和物品。

当玩家钓鱼时，MMOCore 遍历整个钓鱼掉落表，选择第一个满足所有条件的。目前来说唯一一个条件是 `region`（区域）条件，与 WorldGuard 联动。这个条件可以让你为每个 WorldGuard 区域配置不同的掉落表，也就是说某些区域能够钓起更稀有的物品。你可以一同使用[传送点](Waypoints)系统来创建一个独立的稀有钓鱼区域！

如果你创建了一个无条件的掉落表，请确保那是最后一个，否则他将总是被 MMOCore 选中。同时，创建一个无条件的钓鱼掉落表意味着 MMOCore **总是**覆盖默认的原版掉落表。

## 钓鱼掉落表的物品
钓鱼掉落表物品遵循与[掉落表](Drop-Tables)相同的格式，**但是**你必须指定两个额外的参数，也就是 `tugs` - 你在成功钓上这个物品前需要点击的次数，和 `experience`，将物品钓起后的经验。经验可以是一个范围。

### Tugs
MMOCore 通过增加 `tugs` 来提升原版的钓鱼机制。当玩家抓住一只鱼时，鱼奋力挣脱，玩家不愿让它奋力挣脱，于是就要不断的拽鱼直到鱼放弃抵抗。`tugs` 决定了你要点多少下才能抓住一只力气比较大的鱼。

如果玩家在鱼挣脱的时候停止了点击，鱼最终就会跑掉。