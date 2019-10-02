占位符系统需要前置**PlaceholderAPI** 才能正常运行，所有的占位符在插件加载时自动注册，而不需要手动输入命令初始化占位符。
当然对于使用 MVdWPlaceholderAPI 的用户可以使用 `{placeholderapi_mmocore_...}` 来访问 PlaceholderAPI 的占位符。

## 所有占位符
| **占位符** | **输出** |
| --- | --- |
| %mmocore_combat% | true/false 基于玩家是否进行战斗 |
| %mmocore_attribute_<属性>% | [玩家属性](Player-Attributes)目前的数值 |
| %mmocore_health% | 优雅的格式化过的生命值，保留两位小数 |
| %mmocore_max_health% | 显示玩家的最大生命值，保留两位小数 |
| 点数
| %mmocore_skill_points% | 玩家[技能点数](Player-Skills) |
| %mmocore_class_points% | 玩家[种族点数](Player-Classes#class-point) |
| %mmocore_attribute_points% | 玩家[属性点数](Player-Attributes) |
| %mmocore_attribute_reallocation_points% | 如上 |
| 种族与职业
| %mmocore_level% | 玩家主 RPG 等级 |
| %mmocore_level_percent% | 到下一等级的进度的百分比 % |
| %mmocore_experience% | 玩家的经验 |
| %mmocore_next_level% | 玩家升级至下一等级所需的经验，与 %rpg_experience% 兼容 |
| %mmocore_profession_<职业>% | [玩家职业](Custom-Professions)等级 |
| %mmocore_profession_percent_<profession>% | 到下一职业等级的进度的百分比 % |
| %mmocore_class% | 玩家的种族名，或者默认种族的名称 |
| 玩家数值
| %mmocore_<mana/stamina/stellium>% | 玩家对应数值，保留一位数 |
| %mmocore_max_<mana/stamina/stellium>% | 最大数值，保留位数 |
| %mmocore_<mana/stamina/stellium>_bar% | 数值条，用于给玩家看 |
| 任务与目标
| %mmocore_quest% | 正在进行的[任务](Quests)，或者「None」 |
| %mmocore_quest_progress% | 当前任务进度百分比，如果没有任务则是 0 |
| %mmocore_quest_objective% |当前任务目标，或者「None」 |