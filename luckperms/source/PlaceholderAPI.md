在 extended_clip 的 [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) 插件中，LuckPerms 也注册了一些变量（Placeholders）。

LuckPerms 插件所使用的标识符是 **luckperms**。

## 使用

要想使用变量的话，你需要运行下列命令。
这些命令的作用就是安装 LuckPerms 的变量扩展，安装后你就可以使用下面列举出的变量了。

##### `/papi ecloud download LuckPerms`
##### `/papi reload`
请记住使用这些指令你需要OP权限（或者你也可以选择在控制台中运行这些指令）

同时请注意，如果你想得到玩家的前缀或后缀数据，——如果你在服务器上安装了Vault插件和Vault的变量扩展的话，你也可以使用 Vault 插件所提供的变量。

## Placeholders
### `%luckperms_group_name%`
**使用说明:** 返回玩家当前所在组的名字  
**使用示例:** n/a

___
### `%luckperms_context_<context key>%`
**使用说明:** 返回给定内容关键字的值，如果内容没有值的话会返回空
**使用示例:** %luckperms_context_server%

___
### `%luckperms_groups%`
**使用说明:** 返回服务器上的权限组列表，用逗号分割
**使用示例:** n/a

___
### `%luckperms_has_permission_<permission>%`
**使用说明:** 检查玩家是否直接拥有该权限，不会检查通配符或继承的权限
**使用示例:** %luckperms_has_permission_essentials.ban%

___
### `%luckperms_check_permission_<permission>%`
**使用说明:** 检查玩家是否拥有指定权限，这个变量工作的方式和正常插件的检查方式没有区别
**使用示例:** %luckperms_check_permission_some.cool.permission%

___
### `%luckperms_in_group_<group>%`
**使用说明:** 返回玩家是否为给定组的成员，不包括继承组
**使用示例:** %luckperms_in_group_admin%

___
### `%luckperms_inherits_group_<group>%`
**使用说明:** 返回玩家是否在给定组或继承给定组
**使用示例:** %luckperms_inherits_group_vip%

___
### `%luckperms_on_track_<track>%`
**使用说明:** 返回玩家的权限组是否在给定权限组树上
**使用示例:** %luckperms_on_track_staff%

___
### `%luckperms_has_groups_on_track_<track>%`
**使用说明:** 检查玩家是否继承给定权限组树中的任何一个组
**使用示例:** %luckperms_on_track_donor%

___
### `%luckperms_highest_group_by_weight%`
**使用说明:** 返回玩家所在权限组树种的最高级权限组
**使用示例:** n/a

___
### `%luckperms_lowest_group_by_weight%`
**使用说明:** 返回玩家所在权限组树种的最低级权限组
**使用示例:** n/a

___
### `%luckperms_first_group_on_tracks_<tracks>%`
**使用说明:** 返回玩家在给定权限组树上所在的第一个组，权限组树会返回一组用逗号分隔的权限组名，权限组树中的每一个权限组都正序排列。
**使用示例:** %luckperms_first_group_on_tracks_staff,donor%

___
### `%luckperms_last_group_on_tracks_<tracks>%`
**使用说明:** 返回玩家在给定权限组树上所在的最后一个组，权限组树会返回一组用逗号分隔的权限组名，权限组树中的每一个权限组都倒序排列。
**使用示例:** %luckperms_last_group_on_tracks_staff,donor%

___
### `%luckperms_expiry_time_<permission>%`
**使用说明:** 获得玩家拥有的临时权限剩余的时间，如果玩家没有该权限的话会返回空
**使用示例:** %luckperms_expiry_time_essentials.fly%

___
### `%luckperms_group_expiry_time_<group name>%`
**使用说明:** 获得玩家拥有的临时权限组所剩余的时间，如果玩家不在该权限组的话会返回空
**使用示例:** %luckperms_group_expiry_time_vip%

___
### `%luckperms_prefix%`
**使用说明:** 返回玩家的前缀，使用Vault所提供的变量所输出的结果可能会更精确，这一项不会被Vault的配置设置影响
**使用示例:** n/a

___
### `%luckperms_suffix%`
**使用说明:** 返回玩家的后缀，使用Vault所提供的变量所输出的结果可能会更精确，这一项不会被Vault的配置设置影响
**使用示例:** n/a

___
### `%luckperms_meta_<meta key>%`
**使用说明:** 返回与指定Meta关键字联系的值
**使用示例:** %luckperms_meta_some-key%

___
