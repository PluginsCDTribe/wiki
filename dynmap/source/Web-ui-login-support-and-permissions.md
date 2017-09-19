# 网页登陆支持和权限

Dynmap 提供了对从网页获得的信息的限制的选项。开启登陆支持需要在 _configuration.txt_ 中如下配置：

    login-enabled: true

开启后，用户的账户就可以注册了。如果玩家有 `dynmap.webregister` 权限，注册可以被玩家自己完成（使用 /dynmap webregister 命令）。当然，注册可以被管理员使用 `/dynmap webregister <userid>` 命令（需要 `dynmap.webregister.other` 权限）完成。注册完成后，用户会获得一个密码，用于在网页登录来创建一个网页用户。

设置后，网页用户将会使用 Minecraft 用户账户的权限。

如果可以，你可以使网页只对注册并登录的用户可用。你可以这样设置：

    login-required: true

除此之外，来宾用户对网页的访问也是允许的 - 当然只能查看没有被保护的那些内容。

## 配置中的网页限制

### 世界保护

如果管理员想要限制某个世界的访问所有地图的权限，这可以在 worlds.txt 中设置 `protected` 属性来开启（或者使用命令 `/dmap worldset <world-id> protected:true`）。设置之后，只有登陆的用户并且还拥有权限 `dynmap.world.<world-id>` 才可以看见世界 &lt;world-id&gt; 的任何地图。

### 地图保护

如果管理员想要限制某个世界的某个地图的访问，那么这可以在 worlds.txt 中设置 `protected` 属性来开启（或者使用命令 `/dmap mapset <world-id>:<map-id> protected:true`）。设置之后，只有登陆的用户并且还拥有权限 `dynmap.map.<world-id>.<map-id>` 才可以看见。注意：如果世界和地图都被保护，那么玩家需要同时拥有两个权限。

### 聊天保护

如果管理员想要限制从网页发送聊天信息，那么这可以在 ClientUpdateComponent（客户端更新部件）中设置 'webchat-permissions' 来完成。如果设置为 true，那么只有登陆的用户并且还拥有权限 `dynmap.webchat` 才可以在网页发送聊天信息。 

### 玩家位置和信息

如果管理员想要限制玩家位置和信息的可见，那么这可以在 ClientUpdateComponent（客户端更新部件）中设置 'protected-player-info' 来完成。如果设置为 true，那么只有登陆的用户并且还拥有权限 `dynmap.playermarkers.seeall`才可以看见所有可见玩家的位置和/或生命信息。登陆但没有权限的玩家只能看见自己的位置和信息，来宾用户看不见任何玩家。
