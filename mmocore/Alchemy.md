默认的酿造师职业允许玩家在酿造任何类型的药水时获得经验，包括:飞溅，逗留，升级原版药水。以下是酿造师职业配置文件中最重要的部分。

```yaml
exp-sources:
- 'brewpotion{effect=SPEED}'

alchemy-experience:
    special:
        
        # When brewing a potion into a splash potion,
        # only 40% of the base EXP is earned.
        splash: 40
        
        # When brewing a potion into a splash potion,
        # only 40% of the base EXP is earned.
        lingering: 40
        
        # When extending a pot duration,
        # only 40% of base EXP is earned.
        extend: 40
        
        # When upgrading a potion level,
        # only 40% of base EXP is earned.
        upgrade: 40

    # Base EXP of potions
    effects:
       
        # Water bottles
        AWKWARD: 5
        MUNDANE: 5
        THICK: 5
        # Potion effects
        NIGHT_VISION: 10
        INVISIBILITY: 10
        JUMP: 20
        FIRE_RESISTANCE: 15
        ...
```

你可以发现，酿造经验的唯一来源是酿造(台)。你也可以使用 `brewitem` **experience source**指定玩家必须酿造何种类型的药剂才能获得特定职业的经验。如果你想让玩家在只酿造速度和回复药剂时获得经验值，使用 ``brewpotion{effect=SPEED,REGEN}`` (使用逗号分隔药水类型)。

`酿造经验`的配置规定了玩家从酿造药水中获得多少经验。玩家从酿造**中获得的经验取决于药水效果类型**:罕见药水，换句话说，那些需要更稀有成分的药剂，比如“恶魂之泪”(而不是“ 闪烁的西瓜”)，应该能带来更多的酿造经验。

另外，粗制、浓稠和平凡的药水应该给玩家带来较少的经验，因为玩家必须先酿造它们，然后才能酿造其他药水。

### 基础经验

每种酿造台酿造的药水都有一个基础经验,例如玩家酿造一瓶火焰抗性药水将获得15个经验点，酿造一瓶跳跃药水将获得20个经验点(默认设置)。

### 额外酿造经验

当我们使用**红石**延长药水效果持续时间时，玩家将获得数量为X%的药水效果基础经验的额外经验。例如，当延长跳跃药水的持续时间时，玩家将获得 `40% * 20 = 5经验值`。这个百分比可以用 `special.extend` 设置。扩展”选项。当使用**萤石**升级药水效果时，玩家也将获得数量为X%的药水效果基础经验的额外经验。这个百分比同样可以用 `special.extend` 设置。

当使用**火药**酿造飞溅药水或使用**龙息**酿造滞留药水时，玩家将获得数量为X%的药水效果基础经验的额外经验(可以使用`special.splash` 和 `special.lingering`来设置百分比)。