# 概览

这是插件的主配置文件，其中有大量的设置可以修改。

# 默认配置

```yaml
# 穿戴重甲带来的移动速度减缓
# 与你的移动速度相关联
heavy-armors:

    # 移动速度减缓以%为单位
    speed-malus: 5.0
    
    # 重甲的列表，默认情况下金护甲不被认定为重甲
    # 以激励玩家使用金护甲
    list:
    - DIAMOND_HELMET
    - DIAMOND_CHESTPLATE
    - DIAMOND_LEGGINGS
    - DIAMOND_BOOTS
    - IRON_HELMET
    - IRON_CHESTPLATE
    - IRON_LEGGINGS
    - IRON_BOOTS

# BLOCK REGEN 和 BLOCK RESTRICTIONS 必须满足的条件(迷惑)
# 将该选项设置为 'custom-min-conditions: []' 以取消所有条件
custom-mine-conditions:
- 'world{name="world1,world2,world_nether,world_the_end"}'
- 'region{name="region1,region2,__global__"}'

# offset 表示声音在x-y坐标上传播的距离
# height 音效发出的相对Y坐标
# 音效只会在击杀MythicMobs怪物时触发
# 在修改后需要重启服务器
lootsplosion:
    enabled: true
    mmoitems-color: true
    offset: .2
    height: .6

party:

    # 编辑组队buff，你可以添加任意数量的buff
    buff:
        health-regeneration: 3
        additional-experience: 5
    
    # Prefix you need to put in the chat
    # to talk in the party chat.
    chat-prefix: '@'

# 开启这个选项以覆盖原版的经验，并且将经验展示在原版的经验条上。
# 在修改后需要重启服务器
override-vanilla-exp: true

# 是否允许压缩血条，使血条不会充满整个屏幕
# 在修改后需要重启服务器
health-scale:
    enabled: true
    scale: 40

# 玩家是否可以再蹲下时通过按键切换物品
hotbar-swap: true

# Use this option if you're having issue with Anvil GUIs.
# This replaces anvil inputs by chat inputs.
use-chat-input: true
```