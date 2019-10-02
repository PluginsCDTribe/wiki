## 概览

技能目录承载了所有该插件的技能。所有技能都在插件 jar 文件中硬编码完成。如果你不需要某个技能，你只需要不将其分配给某个职业。

每个技能都有其自己的 YML 文件，在那里你可以编辑其 lore 和其在 `/skills` 目录中的显示样式。推荐最好只编辑普通的文本，并且不要尝试去乱搞那些值占位符。

目前来说，还没有那种自创技能的系统，**但是我们认为最牛逼的就是可以让 MythicMobs 的技能也作为 MMOCore 的技能。这会有效的取代对 SkillAPI 的需求，或者其他技能创建插件。你可以利用现有的和即将加入的各种技能，也可以通过 MythicMobs 格式创建几百个你自己的技能。**

## 样例技能

```yaml
name: 火焰风暴（多牛逼哦）
lore:
- 释放六个火焰弹射物到附近的敌人，优先为初始目标。
- 每个弹射物造成 &c{damage} &7伤害&f，
- 并将目标点燃 &c{ignite} &7秒。
- ''
- '&e{cooldown} 秒冷却'
- '&9消耗 {mana} 魔力'
damage:
  base: 5.0
  per-level: 3.0
ignite:
  base: 2.0
  per-level: 0.1
mana:
  base: 15.0
  per-level: 2.0
cooldown:
  base: 5.0
  per-level: -0.1
  max: 5.0
  min: 1.0
```

这是一个样例技能，展示了名称选项，lore，和一些其他的属性。

对于每一个技能你都可以更改其显示名称，其在 `/skills` 菜单中的显示，和其他的一些属性。基础的设置就是技能造成的伤害，接着是每使用技能点数升级一次的加成。这些设置都有最大和最小值，比如你不能有 -2 秒的冷却时间。

![](https://i.imgur.com/PhIpbOr.png)

## 绑定 MythicMobs 技能到 MMOCore 技能
MMOCore 目前没有那么多默认的玩家技能。**但是**有一个方法可以使用 MythicMobs 技能创建 MMOCore 的主动技能，使用 MythicMobs（付费或免费版）的技能创建系统。这使得 MMOCore 有了玩家技能无尽的可能性。

创建一个 MythicMobs 技能的 MMOCore 技能，你首先需要创建一个 YAML 配置文件（名称对应 MMOCore 技能 ID）于 `/skills/mythic-mobs` 目录。这里是一个配置模板：
```yaml
# MythicMobs 技能的内部名称
mythicmobs-skill-id: IceBolt

# 显示设置
name: Ice Bolt
lore:
- 'Shoots a deadly ice bolt which'
- 'deals &b{damage} &7damage and slows'
- 'your target down for &b{slow} &7seconds.'
- ''
- '&e{cooldown}s Cooldown'
material: ICE

# 能力属性
cooldown:
    base: 3.0
    per-level: -0.1
    max: 3.0
    min: 1.0
damage:
    base: 6
    per-level: 3
slow:
    base: 3
    per-level: 1
```
如你所见，技能显示的选项和属性与普通 MMOCore 技能格式相同。但是，你需要添加一个 `mythicmobs-skill-id` 配置选项来将其链接到一个对应的 MythicMobs 技能。这时，MMOCore 应该开始检测你的技能（如果你将其分给了某个种族）。

![](https://i.imgur.com/eiQi7HA.png)

一旦你弄好了 MMOCore 的技能，你就可以前往 MythicMobs 的配置建立你的 MythicMobs 技能了，我们将使用一个官方 wiki 提供的技能样例名为 `Ice Bolt`，这会发射一个带有伤害和减速效果的冰弹射物。

打个广告，[MythicMobs wiki](https://pluginscdtribe.github.io/wiki/mythicmobs/FAQ.html) 也是我翻的。
```yaml
IceBolt:
  Skills:
  - projectile{onTick=IceBolt-Tick;onHit=IceBolt-Hit;v=8;i=1;hR=1;vR=1} @targetLocation
IceBolt-Tick:
  Skills:
  - effect:particles{p=snowballpoof;amount=20;speed=0;hS=0.2;vS=0.2} @origin
IceBolt-Hit:
  Skills:
  - damage{a=10}
  - potion{type=SLOW;duration=100;lvl=2}
```
现在，这个技能总是造成相同量的伤害。原因是 `damage{a=10}` 和 `potion{type=SLOW;duration=100;lvl=2}`。当你使用 MythicMobs **Premium**，你可以输入数学公式用于伤害和药水效果时长和倍数。这些公式可以接受 MythicMobs 的占位符，这允许 MythicMobs 技能基于占位符的输出而造成不同量的伤害。尽管数学公式在免费版中不可用，但是你可以使用占位符系统。

MMOCore 添加了一个新的 MythicMobs 占位符，名为 `<mmocore.skill.(技能).(属性)>%`，这可以直接返回技能的属性值。这样，你就可以在 MythicMobs 技能中使用 MMOCore 的技能属性，造成正确量的伤害和技能时长：
* `damage{a="<mmocore.skill.IceBolt.damage>"}`
* `potion{type=SLOW;duration="<mmocore.skill.IceBolt.slow> * 20";lvl=2}`.
不要忘了乘以 20，因为 MythicMobs 的输入必须是游戏刻。