每个种族的配置存放在文件夹不同的文件中，便于组织和修改。你可以创建自定义的种族，并且可以修改/删除默认的类。创建新的种族非常简单，只需要复制默认的种族配置文件，并发挥你自己的创意修改即可。

## 默认种族
* 奥术法师 (法师的子种族)
* 人类 (新玩家默认的种族)
* 法师
* 射手
* 圣骑士
* 流氓
* 战士

## 配置文件说明

* Human.yml

```yaml
display:
    name: 'Human'
options:
    default: true
    display: false
```

人类是新玩家默认的种族。name被设置为 `human`，当使用占位符时，显示 “Human”。

在上述配置中人类是默认种族，并且同一时间内你只能设置一个默认种族。

display被设置为 `false`，因此这个职业不会展示在 /profess 指令打开的菜单中。

* Mage.yml

```yaml
display:
    name: 'Mage'
    lore:
    - 'The Mage has mastered the power of the'
    - 'Arcanes, taking down any enemy on his path'
    - 'using powerful magic & ranged abilities.'
    - ''
    - '&8&lStrength'
    - '&7  Attack Damage: &c1 &7(+&c0&7)'
    - '&7  Attack Speed: &c4 &7(+&c0&7)'
    - '&7  Max Health: &c20 &7(+&c0&7)'
    - ''
    - '&8&lDexterity'
    - '&7  Knockback Resistance: &a0% &7(+&a0%&7)'
    - '&7  Movement Speed: &a20 &7(+&a0&7)'
    - '&7  Speed Malus Reduction: &a0% &7(+&a0%&7)'
    - ''
    - '&8&lIntellect'
    - '&7  Max Mana: &930 &7(+&91.3&7)'
    - '&7  Health Regen: &90.1 &7(+&90&7)'
    - '&7  Mana Regen: &90.166 &7(+&90&7)'
    item: BLAZE_POWDER

attributes:
    max-mana:
        base: 30
        per-level: 1.3

subclasses:
    ARCANE_MAGE: 10

skills:
    FIRE_STORM:
        level: 1
    POWER_MARK:
        level: 3
    FIREBALL:
        level: 5
    MINOR_HEALINGS:
        level: 6
    ICE_SPIKES:
        level: 8
    AMBERS:
        level: 9
    WEAKEN:
        level: 10
    WARP:
        level: 13
    GREATER_HEALINGS:
        level: 15
```

法师(mage)是一个普通种族的例子。它不是一个子种族，也不是一个默认种族。在创建普通种族时，不需要像创建默认种族那样包含options配置。默认情况下，种族将出现在 /profess 指令打开的菜单中，并且不会是默认的种族。

`display` 配置的工作方式与默认种族相同，只是现在你可以自定义 /profess 指令打开的菜单中显示的lore。我们已经为所有的职业提供了一个非常广泛的默认设置，你可以尽可能的简化它。**需要注意的重要一点是:**当你在编辑lore并指定诸如“攻击伤害(Attack Damage)”等属性时，**实际上不会真的改变这些属性，这只是你设置物品描述的配置**。

`item` 配置是中在 /profess 指令打开的菜单中表示的物品。

`attributes` 配置定义了该种族的基本属性。**默认情况下，所有种族都将使用stats.yml中的基本属性值。因此，如果不希望该种族有特定的属性值**，则不必在Attributes配置中指定任何内容。更改这些属性将覆盖这些stats.yml中定义的属性，从而修改该种族的基本属性值。`base` 选项是属性的初始值，而 `per-level` 选项是每升一级获得的额外属性值。

`subclasses` 配置是你定义是否希望该种族能够升级，并且指定达到哪个等级可以升级的部分。在插件默认的设置中，当法师的等级达到10级时，法师将可以升级奥术法师职业。这时`奥术法师`职业会出现在 /profess 指令打开的菜单中。`奥术法师`职业不会出现在所有玩家的菜单中，而是只会出现在那些达到条件的玩家的菜单中。

`skills` 配置是你设置该种族能够使用哪些技能以及使用级别的部分。非常明显，首先你需要定义技能名称，然后你要在下方定义技能的解锁等级。

* arcane-mage.yml

```yaml
options:
    display: false
display:
    name: 'Arcane Mage'
    lore:
    - 'The Mage has mastered the power of the'
    - 'Arcanes, taking down any enemy on his path'
    - 'using powerful magic & ranged abilities.'
    - ''
    - '&8&lStrength'
    - '&7  Attack Damage: &c1 &7(+&c0&7)'
    - '&7  Attack Speed: &c4 &7(+&c0&7)'
    - '&7  Max Health: &c20 &7(+&c0&7)'
    - ''
    - '&8&lDexterity'
    - '&7  Knockback Resistance: &a0% &7(+&a0%&7)'
    - '&7  Movement Speed: &a20 &7(+&a0&7)'
    - '&7  Speed Malus Reduction: &a0% &7(+&a0%&7)'
    - ''
    - '&8&lIntellect'
    - '&7  Max Mana: &930 &7(+&91.3&7)'
    - '&7  Health Regen: &90.1 &7(+&90&7)'
    - '&7  Mana Regen: &90.166 &7(+&90&7)'
    item: BLAZE_POWDER
attributes:
    max-mana:
        base: 30
        per-level: 1.3
```

奥术法师是法师的子种族, 并且会在10级解锁。你需要定义:

```yaml
options:
    display: false
```

否则这个子种族会出现在所有玩家的菜单中。

子种族的配置方法也大同小异。display, attributes, skills, 以及其他配置基本是相同的。