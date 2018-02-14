You can hook into various forum tables to use the same users as in your forum software.

## phpBB 3

### Feature overview
Tested with phpBB 3.2.1 on 2017-11-04 using AuthMe 5.4.

- /login after forum registration: ✔️ 
- In-game registration: ❌ 
- In-game change password: ✔️ 
- In-game unregister: ✔️

### Sample column configuration
MySQL columns in config.yml:
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

Note: cannot use registration date from phpBB because it is in seconds, while AuthMe stores the timestamp in milliseconds.

### Password hash
config.yml:
```yml
        passwordHash: 'PHPBB'
```