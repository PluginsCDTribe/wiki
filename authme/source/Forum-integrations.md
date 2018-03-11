你可以与各种各样的论坛挂钩来使用相同的用户名。

## phpBB 3

### 功能概述
在 2017-11-04 使用 AuthMe 5.4 以及 phpBB 3.2.1 测试。

- 在论坛注册后使用 /login : ✔️ 
- 在游戏中注册: ❌ 
- 在游戏中更改密码: ✔️ 
- 在游戏中注销: ✔️

### 配置栏示例
config.yml 中的 MySQL 栏目：
```yml
    # Table of the database
    mySQLTablename: 'phpbb_users'
    # Column of IDs to sort data
    mySQLColumnId: 'user_id'
    # Column for storing or checking players nickname
    mySQLColumnName: 'username_clean'
    # Column for storing or checking players RealName
    mySQLRealName: 'username'
    # Column for storing players passwords
    mySQLColumnPassword: 'user_password'
    # Column for storing players emails
    mySQLColumnEmail: 'user_email'
    # Column for storing if a player is logged in or not
    mySQLColumnLogged: 'authme_is_logged'
    # Column for storing if a player has a valid session or not
    mySQLColumnHasSession: 'authme_has_session'
    # Column for storing the player's last IP
    mySQLColumnIp: 'user_ip'
    # Column for storing players lastlogins
    mySQLColumnLastLogin: 'user_lastvisit'
    # Column storing the registration date
    mySQLColumnRegisterDate: 'authme_regdate'
    # Column for storing the IP address at the time of registration
    mySQLColumnRegisterIp: 'authme_regip'
    # Column for storing player LastLocation - X
    mySQLlastlocX: 'authme_loc_x'
    # Column for storing player LastLocation - Y
    mySQLlastlocY: 'authme_loc_y'
    # Column for storing player LastLocation - Z
    mySQLlastlocZ: 'authme_loc_z'
    # Column for storing player LastLocation - World Name
    mySQLlastlocWorld: 'authme_loc_world'
    # Column for storing player LastLocation - Yaw
    mySQLlastlocYaw: 'authme_loc_yaw'
    # Column for storing player LastLocation - Pitch
    mySQLlastlocPitch: 'authme_loc_pitch'
```

注意：不能使用 phpBB 的注册数据，因为它是以秒为单位的，而 AuthMe 的时间存储方式是以毫秒为单位的。

### 密码哈希
config.yml:
```yml
        passwordHash: 'PHPBB'
```