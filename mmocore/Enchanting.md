附魔是 MMOCore 中的一种特殊职业。它将允许玩家在原版的附魔台上附魔物品得到经验并升级他们的附魔职业。附魔得到的经验完全取决于物品得到的附魔，以及得到的附魔的等级。

## 附魔经验
部分附魔比其他的附魔更加难以得到。这就是说它们更应给出更多的经验。每个附魔都有对应等级不同的经验，也就是**每附魔等级**的经验玩家将会获得。

计算玩家附魔物品时得到的经验，你只需要简单的把新的附魔的经验全部加起来。

## enchanting.yml
```yaml
base-enchant-exp:
    fire_protection: 10
    sharpness: 10
    flame: 10
    aqua_affinity: 10
    punch: 10
    loyalty: 10
    depth_strider: 10
    vanishing_curse: 10
    unbreaking: 10
    knockback: 10
    luck_of_the_sea: 10
    binding_curse: 10
    fortune: 30
    protection: 10
    efficiency: 40
    mending: 10
    frost_walker: 10
    lure: 10
    looting: 10
    piercing: 10
    blast_protection: 10
    smite: 10
    multishot: 10
    fire_aspect: 10
    channeling: 10
    sweeping: 10
    thorns: 10
    bane_of_arthropods: 10
    respiration: 10
    riptide: 10
    silk_touch: 50
    quick_charge: 10
    projectile_protection: 10
    impaling: 10
    feather_falling: 10
    power: 10
    infinity: 10
```

## 样例
一个玩家给钻石剑附魔了 _效率 IV_, _耐久 III_ 和 _精准采集_。因此玩家应该获得的经验值为： `总和 = 全部的 (<附魔经验> * <附魔经验>)` 比如，
`总和 = 4 * 40 + 3 * 10 + 1 * 50 = 160 + 30 + 50 = 240 附魔经验`