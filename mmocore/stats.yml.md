# 概览

stats.yml是设定玩家的默认基础属性值、升级带来的额外属性值、自定义附魔设置、附魔格式等各种选项的文件。当你平衡和调整玩家的属性值时，会经常使用这个文件。

# 默认配置

```yaml
default:
    ATTACK_DAMAGE:
        base: 1
        per-level: 0
    ATTACK_SPEED:
        base: 4
        per-level: 0
    MAX_HEALTH:
        base: 20
        per-level: 0
    MOVEMENT_SPEED:
        base: .2
        per-level: 0
    ARMOR:
        base: 0
        per-level: 0
    ARMOR_TOUGHNESS:
        base: 0
        per-level: 0
    SPEED_MALUS_REDUCTION:
        base: 0
        per-level: 0
    KNOCKBACK_RESISTANCE:
        base: 0
        per-level: 0
    HEALTH_REGENERATION:
        base: .1
        per-level: 0
    MAX_MANA:
        base: 20
        per-level: 0
    MANA_REGENERATION:
        base: .166
        per-level: .03
    MAX_STELLIUM:
        base: 20
        per-level: 0
    STELLIUM_REGENERATION:
        base: .01
        per-level: 0
    
    # Reduces the amount of tugs needed to fish fishes.
    # (When set to 30, 30% of the tugs will be removed).
    FISHING_STRENGTH:
        base: 0
        per-level: 0.3
        min: 0
        max: 40
    
    # Chance of instantly fishing.
    CRITICAL_FISHING_CHANCE:
        base: 5
        per-level: 0
        min: 0
        max: 70
            
    # Chance of being dragged in the waters
    # by the fish when trying to catch it,
    # once the player has NOT successfully
    # fished (conditional probability).
    CRITICAL_FISHING_FAILURE_CHANCE:
        base: 3
        per-level: -.01
        min: 1
        max: 100

# How much decimal places the different stats 
# display in the GUIs (e.g in player stats).
# Use # to show a decimal, or nothing if there is no decimal
# Use 0 to display the decimal anyway (even if 0)
# https://docs.oracle.com/javase/7/docs/api/java/text/DecimalFormat.html
decimal-format:
    ATTACK_DAMAGE: '0.#'
    ATTACK_SPEED: '0.#'
    MAX_HEALTH: '0.#'
    MOVEMENT_SPEED: '0.##'
    ARMOR: '0.#'
    ARMOR_TOUGHNESS: '0.###'
    SPEED_MALUS_REDUCTION: '0.#'
    KNOCKBACK_RESISTANCE: '0.##'
    HEALTH_REGENERATION: '0.##'
    MAX_MANA: '0.#'
    MANA_REGENERATION: '0.##'
    MAX_STELLIUM: '0.#'
    STELLIUM_REGENERATION: '0.##'
    FISHING_STRENGTH: '0.#'
    CRITICAL_FISHING_CHANCE: '0.#'
    CRITICAL_FISHING_FAILURE_CHANCE: '0.#'

# How coefficients work: the higher the coefficient, the higher the chance is
# for the enchant to be the one applied when a tool levels up.
#
# Chance of an enchant being chosen: <its-coefficient> / <sum-of-all-enchant-coefficients>
#
# e.g a fishing rod has these potential enchantments:
# - fishing strength, coef of 3
# - crit fishing chance, coef of 1
# - crit failure chance, coef of 1
# then, we have:
# - fishing strength has 3 chances out of 5 to be selected
# - crit fishing chance has 1 chance out of 5 to be selected
# - crit fishing chance has 1 chance out of 5 to be selected
#
# The enchant value is calculated using the 'base' value and the 'offset' value.
# The final value corresponds to the base value, PLUS some random number between
# -offset and offset, which means we have this inequation:
# (base) - (offset) < (final_value) < (base) + (offset)
#
# e.g fishing strength is the enchant chosen, with a base value of 3 and an offset of 1
# The enchant value will be a random number between (3 - 1) and (3 + 1), so between 2 and 4.
tool-enchants:
    FISHING:
        FISHING_STRENGTH:
            coef: 5
            base: 2
            offset: 1
        CRITICAL_FISHING_CHANCE:
            coef: 1
            base: 1
            offset: 0.5
        CRITICAL_FISHING_FAILURE_CHANCE:
            coef: 1
            base: 1
            offset: 0.5
        DURABILITY_USE_RATE:
            coef: 1
            base: 2
            offset: .4
    MINING:
        DURABILITY_USE_RATE:
            coef: 1
            base: 2
            offset: .4
        FORTUNE:
            coef: 1
            base: 2
            offset: .4
        GATHERING_HASTE:
            coef: 1
            base: 2
            offset: .4
    WOODCUTTING:
        DURABILITY_USE_RATE:
            coef: 1
            base: 2
            offset: .4
        GATHERING_HASTE:
            coef: 1
            base: 2
            offset: .4
    FARMING:
        DURABILITY_USE_RATE:
            coef: 1
            base: 2
            offset: .4
        LUCK_OF_THE_FIELD:
            coef: 1
            base: 2
            offset: .4


enchant-format:
    FISHING_CHANCE: '&c+{value}% Fishing Chance'
    CRITICAL_FISHING_CHANCE: '&c+{value}% Crit Fishing Chance'
    CRITICAL_FAILURE_CHANCE: '&c-{value}% Crit Failure Chance'
    DURABILITY_USE_RATE: '&c-{value}% Durability Use Rate'
    FORTUNE: '&c+{value}% Loot Fortune'
    GATHERING_HASTE: '&c+{value}% Gathering Haste'
    LUCK_OF_THE_FIELD: '&c+{value}% Luck of the Field'

```
# 属性值列表

这个文件或许第一眼看上去很吓人，但我保证实际上并不是这样，让我们来逐步解析这个文件。

“default”部分包含所有的玩家默认属性值，它表示所有玩家以及没有设置属性值的种族的基本属性值。默认的配置提供了除自定义属性之外的所有属性值。

* ATTACK_DAMAGE（攻击伤害）

攻击伤害这一基础属性表示你能造成伤害的多少。如果你想让玩家在升级时变得更强，你可以修改攻击伤害随等级的增长速率。强烈建议从低数值开始增长，这样玩家就不会都变成桐姥爷。

* ATTACK_SPEED（攻击速度）

攻击速度是决定攻击冷却快慢的基础属性。这一属性显然已经被大多数武器修改了。如果你觉得玩家在升级时应该获得更快的攻击速度，你可以修改其每一级的值。该数值代表你每秒可以进行的攻击次数，默认情况下你每秒可以攻击4次。数字越大，攻击速度越快。

* MAX_HEALTH（生命上限）

生命上限是一个玩家最多拥有多少生命值的基础属性。20点生命值，就是10颗红心，这是MineCraft设定的默认值。你可以修改其每一级的值，使玩家获得更高的生命上限。

* MOVEMENT_SPEED（移动速度）

移动速度是玩家移动速度的基础属性(步行速度)。默认为0.2，和原版的MineCraft一样。更高的数值表示更快的移动速度。注意，过高的数值会让你的玩家不自觉地释放`音速冲击`。如果你觉得可以让玩家获得更快的移动速度，修改每个等级对应的数值。

* SPEED_MALUS_REDUCTION（移速减缓抗性）

移速减缓抗性是我们的一个自定义属性值。在config.yml你可以配置什么样的护甲会减慢玩家的速度，就像一个物品的重量。这种抗性将抵消这种影响。因此，如果你想要强壮的职业不被重甲压垮，你应该给予他们移速减缓抗性。你也可以在设置其随等级的增长而增长。

* KNOCKBACK_RESISTANCE（击退抗性）

击退抗性会改变你被攻击时退后的距离。你也可以把它的初始值设定为0，然后设置其随等级的增长而增长。

* HEALTH_REGENERATION（生命回复）

MMOCore通过像MMOItems这样的插件重写了原版的生命回复机制，使其更好用且更可靠。你可以自行修改这个值(0.1等于10%)，随等级增长而增长。在你刚开始修改生命回复时，请将其设置为很小的数字，直到你弄清楚到底多大的值是合适的。

* MAX_MANA（魔力上限）

一个自定义的MMOCore属性值，为玩家添加魔力值属性。默认情况下最大魔力值是20，但是如果你不想让玩家拥有魔力值，你可以设置为0。你也将其设置为随等级的增长而增长。

* MANA_REGENERATION（魔力回复）

一个自定义的MMOCore属性值，表示魔力回复的速度。默认值是0.166，每次升级的时候会有轻微的增长。你可以根据自己的意愿将其更改得更快或更慢。

* MAX_STELLIUM（星能上限）

一个自定义的MMOCore属性值，它为服务器引入了另一个虚拟属性。星能将会在另一个Wiki页面中详细介绍，星能是使用传送点的必须物，它的恢复速度要慢得多。星和魔力一样，拥有上限和回复速率。

* STELLIUM_REGENERATION（星能回复）

一个自定义的MMOCore属性值，可以改变星能回复的速率。默认为0.01(比魔力慢很多)。这也可以修改。记住，星能是使用传送点的必须物!**如果你的服务器没有启用传送点，你就不需要使用星能**。

# 其他属性

* FISHING_STRENGTH（握竿力量）

我们重写了自定义捕鱼机制，现在你可以将不同的鱼上钩的时间修改得更长，甚至把你拉入水中。握竿力量会影响拖动的距离，在握竿力量为0的情况下你被拖动的距离等于配置文件中定义的距离。一开始你的握竿力量默认为0，每升一级会增加0.3。你也可以设置一个最小和最大的值!

* CRITICAL_FISHING_CHANCE（爆发几率）

另一个跟垂钓有关的属性值，在一定几率下你将立即抓住你钓上鱼，而不是被鱼拖动。与握竿力量相同，5的值代表是5%的几率。

* CRITICAL_FISHING_FAILURE_CHANCE（落水几率）

另一个跟垂钓有关的属性值，有时候鱼的力气太大，以至于它会把你拉进水里！发生这种情况的默认概率为3%，随等级的增长主键下降，每级下降0.01。也有最小值和最大值。

# 工具附魔

你可以直接阅读配置文件中的注释，里面解释得已经很清楚了。

```yaml
# How coefficients work: the higher the coefficient, the higher the chance is
# for the enchant to be the one applied when a tool levels up.
#
# Chance of an enchant being chosen: <its-coefficient> / <sum-of-all-enchant-coefficients>
#
# e.g a fishing rod has these potential enchantments:
# - fishing strength, coef of 3
# - crit fishing chance, coef of 1
# - crit failure chance, coef of 1
# then, we have:
# - fishing strength has 3 chances out of 5 to be selected
# - crit fishing chance has 1 chance out of 5 to be selected
# - crit fishing chance has 1 chance out of 5 to be selected
#
# The enchant value is calculated using the 'base' value and the 'offset' value.
# The final value corresponds to the base value, PLUS some random number between
# -offset and offset, which means we have this inequation:
# (base) - (offset) < (final_value) < (base) + (offset)
#
# e.g fishing strength is the enchant chosen, with a base value of 3 and an offset of 1
# The enchant value will be a random number between (3 - 1) and (3 + 1), so between 2 and 4.
```

自定义附魔只适用于自定义MMOCore工具，在默认情况下，当工具升级到某个阈值时，会被赋予自定义附魔。

* Fishing Strength附魔会增加握杆力量。
* Critical Fishing chance附魔将提升立即捕捉到鱼的几率。
* Critical Fishing Failure Chance附魔会减少你被拉入水中的几率。
* Durability Use Rate会增加工具的耐久度。
* Fortune附魔会增加挖矿时获得更多掉落物的几率（仅适用于MMOCore限定的方块以及自定义掉落表）。
* Gathering Haste附魔类似于效率附魔。
* Luck of the Field附魔类似于农作物版本的时运附魔。

# 附魔格式

附魔格式类似于一个语言文件，用于说明附魔属性将如何在工具上显示。

