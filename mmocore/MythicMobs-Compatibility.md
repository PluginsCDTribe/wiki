我们大量生物相关的特性以及自定义掉落都与天字第一号生物创建插件 MythicMobs 相关。并且**最重要的特性之一**，在 MMOCore 中创建技能，你需要利用 MythicMobs 来制作技能。更多的信息都在[这里](Skills-Folder)，滚到最下面。

MythicMobs 也添加了任务系统更多的可能性：你可以设置任务的目标为玩家必须击杀 X 个 MythicMobs 生物，更多信息[在此](Quest-Folder)。

玩家也可以在击杀 MythicMobs 生物后获得主经验或者种族经验，更多信息[在此](Custom-Professions)。

## MythicMobs 掉落表物品
MMOCore 添加了新的掉落物种类到 MythicMobs 的掉路表，这是一个列表：

| 掉落物 | 用法 | 描述 |
| - | - | - |
| 金袋 | `gold_pouch{min=10;max=100}` | 包含 MIN 到 MAX 之间的随机量的钱 |
| 金币| `gold_coin{}` | 掉落一个金币 $1 |
| 纸币 | `note{min=20;max=30}` | 掉落随机价格的纸币 |

## 金袋
金袋是羽毛，你可以右键点击以打开一个两行的 GUI 界面，其中含有随机生成的金币和纸币。玩家不能在其中放入任何东西，只能在背包有空余的情况下从里面拿出来。金袋将在完全被拿空自动被**移除**。

![](https://i.imgur.com/5aGwNQw.gif)