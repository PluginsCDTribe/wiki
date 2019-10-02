玩家属性是一个很有名的的RPG特性，它为职业玩法增加了更多的复杂性。默认情况下，MMOCore有三个玩家属性，分别是**力量**、**敏捷**和**智力**，你也可以添加、编辑和删除属性。

## 属性
属性是RPG统计数据，玩家可以升级以提升自己的战斗能力。目前 MMOCore 只支持属性增益，我们计划增加物品使用限制，即玩家的某一特定属性必须达到一定的数值才能使用某物品。使用属性占位符，你还可以设置其他条件，如MythicMobs技能。

## 属性菜单
通过属性菜单(使用 /attributes 指令打开)，玩家可以看到他们有什么属性，升级他们的属性或者使用属性再分配点数来重新分配他们的属性点数。
![](https://i.imgur.com/8p9ckkU.gif)

## 默认属性概览
**力量**属性是指战士或圣骑士之类的坦克职业可以升级的属性，它既可以给予玩家额外的**武器伤害**以获得额外的伤害输出，也可以给予额外的**最大生命值**以提升玩家的坦度。

战士、盗贼或神射手可以专注于提升他们的**敏捷**属性，因为**敏捷**可以增加他们的移动速度(要么帮助像盗贼或神射手这样的职业逃跑，要么提升战士在战斗中的移动能力)，同时**敏捷**也可以提升他们的**抛射物伤害**和他们的**物理伤害**(包括物理技能和武器)。

**智力**属性则主要用于法师，因为它**大幅提升了**(与其他属性相比)魔法技能造成的伤害。**智力**也可以减少技能的冷却时间，适用于任何职业。

你完全可以在 attributes.yml 文件中编辑这些属性。默认属性都非常经典，而且你可以添加很多自定义的属性，让属性升级变得更复杂和有趣！
## 配置文件
```yaml
# Attribute ID
strength:

    name: Strength
    
    # Maximum amount of points players 
    # may spend in this attribute.
    max-points: 40
    
    # Buffs given every 1 attribute point spent
    # in this specific attribute.
    buff:
        weapon_damage: 2
        max_health: 1%

dexterity:
    name: Dexterity
    max-points: 40
    buff:
        physical_damage: 1.5
        projectile_damage: 1
        attack_speed: 0.5%

intelligence:
    name: Intelligence
    max-points: 40
    buff:
        magical_damage: 2
        cooldown_reduction: 1
```

## 提示
配置文件非常容易理解。每个配置部分都对应一个玩家属性。你需要指定属性名，属性名会在GUI中显示，你也可以指定在某一属性中花费的属性点数的最大数量，以及属性提供的属性值增益。这些增益的效果与玩家在该属性中花费的属性点数成正比。
你可以在[这里](Player-Statistics)查看玩家属性值列表。