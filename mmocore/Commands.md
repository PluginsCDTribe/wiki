
| 命令 | 描述 |
| :--- | :--- |
|  **基础命令**
| /mmocore | 显示帮助信息主界面 |
| /mmocore reload | 编辑配置文件后，重新载入整个插件，而不需要重新启动服务器！ |
| /mmocore tool <职业> <玩家> | 这是一个重要的命令，将一个全新的等级为 1 的物品给予玩家。有效的职业为 Mining（镐子），Farming（锄头），Fishing（鱼竿），以及 Woodcutting（斧） |
| **货币**
| /mmocore note <玩家> <价格> | 给玩家一张价值 X 的纸币，可以[存入](Currency-System#deposit)银行。 |
| /mmocore coins <玩家> <数量> | 给玩家以输入的数量的金币，可以存入银行。 |
| **传送点**
| /mmocore waypoints unlock <传送点> <玩家> | 手动解锁指定玩家的一个传送点。|
| /mmocore waypoints open <玩家> | 打开对应的传送点菜单并检查玩家是否站在某个传送点上 |
| **管理命令**
| /mmocore admin class <玩家> <种族> | 设置玩家种族 |
| /mmocore admin exp <玩家> <职业/main> <数量> | 手动给予玩家职业经验 |
| /mmocore admin level <玩家> <职业/main> <数量> |和 EXP 命令相似，不过是直接给予玩家职业等级 |
| /mmocore admin class-points <玩家> <数量> | 给予玩家[种族点数](Player-Classes#class-point) |
| /mmocore admin skill-points <玩家> <数量> | 给予玩家[技能点数](Player-Skills#upgrade)，这样玩家就能够升级他们的技能 |
| /mmocore admin reset <玩家> | 强制重置玩家的所有数据，如 种族、等级、经验等 |
| /mmocore admin nocd <玩家> | 由管理员使用，无视魔力使用及技能冷却测试技能 |
| /mmocore admin info <玩家> | 显示一个在线玩家的所有有用的信息 |
| **加成**
| /mmocore booster create <职业/main> <倍数> <时长> [玩家] | 创建一个指定时长和倍数的[经验加成](EXP-Boosters) |
| /mmocore booster list |显示激活的所有经验加成 |
| /mmocore booster remove <uuid> | 移除指定 ID 的经验加成 |
| **测试/技术性**
| /mmocore refreshpd <玩家> | 刷新指定玩家的数据。**编辑任何技能后必须使用，尽管这时重启可能是更好的选择，自行尝试** |
| **其他命令**
| /player 或 /p | 开启角色菜单 |
| /class [玩家] | 强制开启种族选择界面 |
| /waypoints | 开启传送点界面 | 
| /deposit [玩家] | 强制打开[存钱](Currency-System#deposit)界面 | 
| /withdraw [玩家] | [取走](Currency-System#deposit)玩家的一些钱 |
| **社交** |
| /party | 开启队伍菜单 |
| /friends | 开启好友列表 |
| **游戏命令** |
| /skills | 开启技能列表 |
| /quests | 开启任务列表 |