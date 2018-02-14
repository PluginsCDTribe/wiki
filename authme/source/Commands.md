<!-- AUTO-GENERATED FILE! Do not edit this directly -->
<!-- File auto-generated on Fri Dec 01 19:16:15 CET 2017. See docs/commands/commands.tpl.md -->

## AuthMe 指令
你可以使用以下指令来体验 AuthMe 的各种特性. 必须的参数会用 `< >` 标出
可选的参数会用 (`[ ]`) 标出

- **/authme**: AuthMeReloaded 基础指令
- **/authme register** &lt;player> &lt;password>: 使用指定的密码帮助指定的玩家注册
  <br />需要权限 `authme.admin.register`
- **/authme unregister** &lt;player>: 取消一个玩家的注册
  <br />需要权限 `authme.admin.unregister`
- **/authme forcelogin** [player]: 强制一个玩家登录
  <br />需要权限 `authme.admin.forcelogin`
- **/authme password** &lt;player> &lt;pwd>: 修改玩家的密码
  <br />需要权限 `authme.admin.changepassword`
- **/authme lastlogin** [player]: 查看玩家上次登录的时间
  <br />需要权限 `authme.admin.lastlogin`
- **/authme accounts** [player]: 查看该玩家或者该玩家所登IP牵涉到的所有账户
  <br />需要权限 `authme.admin.accounts`
- **/authme email** [player]: 查看该玩家绑定的邮箱
  <br />需要权限 `authme.admin.getemail`
- **/authme setemail** &lt;player> &lt;email>: 改变该玩家绑定的邮箱
  <br />需要权限 `authme.admin.changemail`
- **/authme getip** &lt;player>: 查看一个在线玩家的IP
  <br />需要权限 `authme.admin.getip`
- **/authme spawn**: 传送至出生点
  <br />需要权限 `authme.admin.spawn`
- **/authme setspawn**: 改变玩家出生点至当前位置
  <br />需要权限 `authme.admin.setspawn`
- **/authme firstspawn**: 传送至最初的出生点
  <br />需要权限 `authme.admin.firstspawn`
- **/authme setfirstspawn**: 改变最初的玩家出生点至当前位置
  <br />需要权限 `authme.admin.setfirstspawn`
- **/authme purge** &lt;days>: 删除比设定天数更旧的 AuthMeReloaded 数据
  <br />需要权限 `authme.admin.purge`
- **/authme purgeplayer** &lt;player> [options]: 删除该玩家数据
  <br />需要权限 `authme.admin.purgeplayer`
- **/authme backup**: 创建一个已注册玩家的数据备份
  <br />需要权限 `authme.admin.backup`
- **/authme resetpos** &lt;player/*>: 清除该玩家上一个已知的位置，或者全部位置
  <br />需要权限 `authme.admin.purgelastpos`
- **/authme purgebannedplayers**: 清除所有被封禁玩家的 AuthMeReloaded 数据
  <br />需要权限 `authme.admin.purgebannedplayers`
- **/authme switchantibot** [mode]: 设置防小号 AntiBot 模式的状态
  <br />需要权限 `authme.admin.switchantibot`
- **/authme reload**: 重载 AuthMeReloaded 插件
  <br />需要权限 `authme.admin.reload`
- **/authme version**: 显示已安装的 AuthMeReloaded 的详细信息，如版本, 作者, 使用协议等
- **/authme converter** [job]: AuthMeReloaded 的转换指令
  <br />需要权限 `authme.admin.converter`
- **/authme messages** [help]: 给当前语言文件添加缺失的语言项
  <br />需要权限 `authme.admin.updatemessages`
- **/authme recent**: 显示上一个登录的玩家
  <br />需要权限 `authme.admin.seerecent`
- **/authme debug** [child] [arg] [arg]: Debug以及相关操作
  <br />需要权限 `authme.debug.command`
- **/authme help** [query]: 查看 /authme 指令的详细帮助
- **/email**: AuthMeReloaded 邮箱验证基础指令
- **/email show**: 显示你当前的邮箱
  <br />需要权限 `authme.player.email.see`
- **/email add** &lt;email> &lt;verifyEmail>: 给你的账户添加一个新邮箱
  <br />需要权限 `authme.player.email.add`
- **/email change** &lt;oldEmail> &lt;newEmail>: 给你的账户更改一个邮箱
  <br />需要权限 `authme.player.email.change`
- **/email recover** &lt;email>: 重置你的账户，这将会向你的邮箱发送一封包含新密码的邮件
  <br />需要权限 `authme.player.email.recover`
- **/email code** &lt;code>: 重置你的游戏，这将会向你的邮箱发送一封包含重置码的邮件
  <br />需要权限 `authme.player.email.recover`
- **/email setpassword** &lt;password>: 重置账户成功后，设置新密码
  <br />需要权限 `authme.player.email.recover`
- **/email help** [query]: 查看 /email 指令的详细帮助
- **/login** &lt;password>: AuthMeReloaded 的登录指令
  <br />需要权限 `authme.player.login`
- **/login help** [query]: 查看 /login 指令的详细帮助
- **/logout**: AuthMeReloaded 的登出指令
  <br />需要权限 `authme.player.logout`
- **/logout help** [query]: 查看 /logout 指令的详细帮助
- **/register** [password] [verifyPassword]: AuthMeReloaded 的注册指令
  <br />需要权限 `authme.player.register`
- **/register help** [query]: 查看 /register 指令的详细帮助
- **/unregister** &lt;password>: AuthMeReloaded 的解除注册指令
  <br />需要权限 `authme.player.unregister`
- **/unregister help** [query]: 查看 /unregister 指令的详细帮助
- **/changepassword** &lt;oldPassword> &lt;newPassword>: AuthMeReloaded 的改密码指令
  <br />需要权限 `authme.player.changepassword`
- **/changepassword help** [query]: 查看 /changepassword 指令的详细帮助
- **/captcha** &lt;captcha>: AuthMeReloaded 的验证码指令
  <br />需要权限 `authme.player.captcha`
- **/captcha help** [query]: 查看 /captcha 指令的详细帮助
- **/verification** &lt;code>: 完成 AuthMeReloaded 的验证过程
  <br />需要权限 `authme.player.security.verificationcode`
- **/verification help** [query]: 查看 /verification 指令的详细帮助


---

This page was automatically generated on the [AuthMe/AuthMeReloaded repository](https://github.com/AuthMe/AuthMeReloaded/tree/master/docs/) on Fri Dec 01 19:16:15 CET 2017