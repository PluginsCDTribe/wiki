本页面列出了一系列 _大更新_ 的相关情况，可能需要插件做出一些调整

版本                       | 更新详情
----------------------------- | ----------
5.4 ([2017-08-31](https://github.com/AuthMe/AuthMeReloaded/commit/b96ae61697f79c22c053dc174edfab4ff84a86c0)) | 移除了 PermissionsBukkit 的 hook
5.4 ([2017-08-31](https://github.com/AuthMe/AuthMeReloaded/commit/b96ae61697f79c22c053dc174edfab4ff84a86c0)) | 移除了 CombatTagPlus 的 hook
5.3 ([2017-04-14](https://github.com/AuthMe/AuthMeReloaded/commit/8ecdd1f4d3d325bebc64356f0d18d24ba6ac5fe8)) | API.java class 被移除; 现在使用 api.v3.AuthMeApi class 代替
5.3 ([2017-03-24](https://github.com/AuthMe/AuthMeReloaded/commit/2f90a45f4351d80c4b04d5ca9d07f3ebf2ed62d6)) | `removeSpeed` 设置项不复存在; 如果 `allowMovement` 被设置为 `false` 那么非真实玩家的速度将别移除
5.3 ([2017-03-22](https://github.com/AuthMe/AuthMeReloaded/commit/7d4bfcd99d54f858974174e91fd53dfa89007a9f)) | 指令 `/email recovery <email> <code>` 被改为 `/email code <code>`
5.3 ([2017-03-12](https://github.com/AuthMe/AuthMeReloaded/commit/8557621c02c13c9b172302f547ad0180d9fe64ac)) | `SaveQuitLocation: false` 不再存储玩家的下线地点
5.2 ([2017-01-07](https://github.com/AuthMe/AuthMeReloaded/commit/385f7d6b1d13cba58d7446cf6b7e9762fca88e09)) | 在语言文件中, `reg_email_msg` 不复存在，请更新为 `reg_msg` 
5.2 ([2016-11-13](https://github.com/AuthMe/AuthMeReloaded/commit/bb89a59a8a3db9be6a2c0a0f8eab5a22f1b10abb)) | 想支持旧的哈希码, 你现在需要在 `legacyHashes` 中列出哈希码
5.2 ([2016-09-04](https://github.com/AuthMe/AuthMeReloaded/commit/5efed1b697e03785bba5f96dbc3af69f82b0a28a)) | 不再支持 Java 7
5.2 ([2016-09-04](https://github.com/AuthMe/AuthMeReloaded/commit/7deb75ab856250ef84934d578960b4850a313ec8)) | 权限系统: 不再支持 GroupManager (非与 Vault 挂钩) 
5.2 ([2016-08-11](https://github.com/AuthMe/AuthMeReloaded/commit/67d53d0c3c98282b645894a0e7eadaf8cbedcbc7)) | 在 messages_xx.yml 语言文件中, `&n` 现在是常用格式符 `%nl%` 被移动到了新的一行
5.2 ([2016-06-19](https://github.com/AuthMe/AuthMeReloaded/commit/e1d697d386a1cd94fd09a02654cd7d9eaf854cfe)) | 昵称现在大小写敏感
5.2 ([2016-05-29](https://github.com/AuthMe/AuthMeReloaded/commit/52c0c7dd640217572d32587237abedb9cc35fca3)) | "如果注册是非必要的将允许使用所有指令" 特性被移除
5.2 ([2016-05-03](https://github.com/AuthMe/AuthMeReloaded/commit/0ea95fb93c5b8408d6cb34c8de381dbce06060d5)) | 出生点设置强制被分为一组 (设置会自动合并)
5.2 ([2016-02-19](https://github.com/AuthMe/AuthMeReloaded/commit/715622826f1e67ec50c63fadab90ffdbef1c468f)) | 指令 /converter 被改为 /authme converter
5.2 ([2016-02-14](https://github.com/AuthMe/AuthMeReloaded/commit/b3734f40102466ef145e5361b6125ed96360ddef)) | 一些权限不再隶属于 `authme.player`. 请查看下方权限列表
5.2 ([2016-02-12](https://github.com/Xephi/AuthMeReloaded/issues/512)) | `Settings.delayJoinLeaveMessages` 已经被分为更细化的设置，你的配置文件将会自动更新，请搜索带 "delay" 的设置项
5.2 ([2015-12-28](https://github.com/AuthMe/AuthMeReloaded/commit/0688a8645a31e61f2055227e1bd63d2b5bb8859a)) | PlainText 已被自动更改为 SHA256 HashAlgorithm
5.2 ([2015-12-26](https://github.com/AuthMe/AuthMeReloaded/commit/41e400e9dd9c6a5194bb739d022d81d004a4159d)) | 普通文件存储以及转换为/来自普通文件不再支持，现在使用 Sqlite.
5.2 ([2015-12-23](https://github.com/AuthMe/AuthMeReloaded/commit/8bfb56f34e010a96107bd435b94ce7bd7fc527fd)) | 设置 `settings.restrictions.enablePasswordVerifier` 重命名为 `enablePasswordConfirmation`
5.2 ([2015-12-22](https://github.com/AuthMe/AuthMeReloaded/commit/8f098933371767130b2a533ec9ad0f6075c2522b)) | email.html: 占位符的格式现在是像这种 `<playername />`, 而不是 `<playername>` 或者 `%playername%`. ([Template](https://github.com/AuthMe/AuthMeReloaded/blob/18dbcfde890ac2c756c3d3ff387007ae00733f52/src/main/resources/email.html))
5.1&nbsp;([2015‑12‑05](https://github.com/AuthMe/AuthMeReloaded/commit/f1c3eed0699e15640731c4cd06f5feb198ef6553)) | 改变权限列表 ([up-to-date list](https://github.com/AuthMe/AuthMeReloaded/blob/master/src/tools/docs/permission_nodes.md))
5.1 ([2015-12-04](https://github.com/AuthMe/AuthMeReloaded/commit/e781115d7cf66db57a436de8d21693aa05d50be3)) | 由邮件发送的内容配置现在从 config.yml 移动到 email.html
5.1 ([2015-11-27](https://github.com/AuthMe/AuthMeReloaded/commit/67244d5e7bf45b58323fdd9808afe5d245d67c66)) | Bug 修复: 使用指令 /authme register 时不再将密码改变成全部小写

---

### 另见

##### 权限更改 2016-02-14
一些权限不再隶属于 `authme.player` 权限组下. 原因是因为如果给玩家权限 `authme.player.*` 将会同时给他们VIP权限 (`authme.player.vip`), 这是不可理喻的

旧权限 -> 新权限
```
authme.player.allow2accounts      -> authme.allowmultipleaccounts
authme.player.bypassantibot       -> authme.bypassantibot
authme.player.bypassforcesurvival -> authme.bypassforcesurvival
authme.player.seeotheraccounts    -> authme.admin.seeotheraccounts
authme.player.vip                 -> authme.vip
```