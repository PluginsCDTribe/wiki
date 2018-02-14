<!-- AUTO-GENERATED FILE! Do not edit this directly -->
<!-- File auto-generated on Sun Jan 21 18:49:44 CET 2018. See docs/config/config.tpl.md -->

## AuthMe 配置
第一次运行 AuthMe 的时候插件将会在 plugins/AuthMe 创建一份 config.yml， 
你可以用其来配置各种设置。以下内容为 config.yml 的初始内容：

```yml
# Translated By CH1
DataSource:
    # 您希望使用哪种数据库来储存
    # 数据库类型: SQLITE(默认), MYSQL
    backend: 'SQLITE'
    # 是否启用数据库缓存
    caching: true
    # 数据库地址
    mySQLHost: '127.0.0.1'
    # 数据库端口
    mySQLPort: '3306'
    # 使用SSL(更安全)来连接数据库
    mySQLUseSSL: true
    # 数据库用户名
    mySQLUsername: 'authme'
    # 数据库密码
    mySQLPassword: '12345'
    # 数据库名称
    mySQLDatabase: 'authme'
    # 数据表名称
    mySQLTablename: 'authme'
    # 数据库用户ID列的名称
    mySQLColumnId: 'id'
    # 数据库用户名列的名称
    mySQLColumnName: 'username'
    # 数据库玩家真实名称列的名称
    mySQLRealName: 'realname'
    # 数据库玩家密码列的名称
    mySQLColumnPassword: 'password'
    # 数据库玩家邮箱的名称
    mySQLColumnEmail: 'email'
    # 数据库玩家登陆状态列的名称
    mySQLColumnLogged: 'isLogged'
    # 数据库玩家IP列的名称
    mySQLColumnIp: 'ip'
    # 数据库玩家最后登陆时间列的名称
    mySQLColumnLastLogin: 'lastlogin'
    # 数据库玩家下线地址 X轴
    mySQLlastlocX: 'x'
    # 数据库玩家下线地址 Y轴
    mySQLlastlocY: 'y'
    # 数据库玩家下线地址 Z轴
    mySQLlastlocZ: 'z'
    # 数据库玩家下线世界列的名称
    mySQLlastlocWorld: 'world'
    # 数据库玩家下线身体朝向列的名称
    mySQLlastlocYaw: 'yaw'
    # 数据库玩家下线头部朝向列的名称
    mySQLlastlocPitch: 'pitch'
    # 最大数据库大小 -1为自动
    poolSize: -1
ExternalBoardOptions:
    # 数据库储存玩家数据储存盐值的列
    mySQLColumnSalt: ''
    # 储存玩家用户组的列
    mySQLColumnGroup: ''
    # -1为关闭,如果你想使用论坛等系统来激活未活跃的玩家请修改此项
    nonActivedUserGroup: -1
    # 其他mysql列，用来储存玩家的用户名[区分大小写]
    mySQLOtherUsernameColumns: []
    # 在 BCrypt 中log2需要多少轮 (如果你不知道这要做什么，请不要更改) 
    bCryptLog2Round: 10
    # PhpBB数据表头
    phpbbTablePrefix: 'phpbb_'
    # phpBB 默认已激活的用户组为2
    phpbbActivatedGroupId: 2
    # IP Board 数据表头
    IPBTablePrefix: 'ipb_'
    # IP Board 自定义默认用户组为3
    IPBActivatedGroupId: 3
    # XenForo 自定义默认用户组为2
    XFActivatedGroupId: 2
    # Wordpress 数据表头
    wordpressTablePrefix: 'wp_'
settings:
    sessions:
        # 启用会话服务,可以让玩家在下线后指定时间内登录而不需要输入密码
        # 采用多重验证
        enabled: false
        # 单位:分钟 超时时间,在这超时时间之前登录不需要输入密码
        timeout: 10
    # 语言 需要中文请修改为 zhcn
    messagesLanguage: 'en'
    # 记录类型: INFO, FINE, DEBUG. 不建议修改
    logLevel: 'FINE'
    # 是否使用多线程
    useAsyncTasks: true
    restrictions:
        # 在登录前允许玩家说话吗
        allowChat: false
        # 在玩家登录前是否隐藏服务器消息
        hideChat: false
        # 未登录玩家允许使用的命令
        allowCommands: 
        - '/login'
        - '/register'
        - '/l'
        - '/reg'
        - '/email'
        - '/captcha'
        # 一个ip最大注册玩家数量
        # 0 代表无限制
        maxRegPerIp: 1
        # 最小玩家名称长度
        minNicknameLength: 3
        # 最大玩家名称长度
        maxNicknameLength: 16
        # 设置为true意味着在线玩家无法被使用同ID的玩家踢下线
        ForceSingleSession: true
        ForceSpawnLocOnJoin:
            # 强制玩家出生在指定地点
            enabled: false
            # 启用的世界
            worlds: 
            - 'world'
            - 'world_nether'
            - 'world_the_end'
        # 保存玩家最后下线位置
        SaveQuitLocation: false
        # 激活玩家限制功能
        AllowRestrictedUser: false
        # 自动踢出不符合以下规则玩家[需要符合玩家名称以及IP]
        # 举个栗子:
        #     AllowedRestrictedUser:
        #     - playername;127.0.0.1
        AllowedRestrictedUser: []
        # 封禁不符合以上规则的IP
        banUnsafedIP: false
        # 是否立即踢出没注册的玩家
        kickNonRegistered: false
        # 是否踢出输入密码错误的玩家
        kickOnWrongPassword: true
        # 自动传送未登录的玩家到出生点
        teleportUnAuthedToSpawn: false
        # 允许未登录的玩家走动
        allowMovement: false
        # 允许输入密码时间 单位:秒
        # 0为关闭
        timeout: 30
        # 允许登录服务器的玩家名称
        allowedNicknameCharacters: '[a-zA-Z0-9_]*'
        # 允许未注册的玩家走的距离
        # 0为无限制
        allowedMovementRadius: 100
        # 是否在未登录的时候隐藏玩家的背包 需要ProtocolLib
        ProtectInventoryBeforeLogIn: true
        # 是否在未登录的时候禁用Tab补全 需要ProtocolLib
        DenyTabCompleteBeforeLogin: false
        # 是否展示该玩家IP下所有账号
        # 权限 authme.admin.accounts
        displayOtherAccounts: true
        # 出生点优先级 可选: authme, essentials, multiverse, default
        spawnPriority: 'authme,essentials,multiverse,default'
        # IP最大登录玩家数量
        maxLoginPerIp: 0
        # IP最大进入玩家数量
        maxJoinPerIp: 0
        # 不传送玩家到出生点
        noTeleport: false
        # 密码允许的内容
        allowedPasswordCharacters: '[\x21-\x7E]*'
        # 其他关于账户命令使用阈值 小于2为禁用
        otherAccountsCmdThreshold: 0
        # 当IP下具有的账户比设定值多时使用的命令
        # 变量: %playername%, %playerip%
        otherAccountsCmd: 'say The player %playername% with ip %playerip% has multiple accounts!'
    GameMode:
        # 强制玩家在登录时使用生存模式
        ForceSurvivalMode: false
    unrestrictions:
        # 其他插件或者Mod有bug因此禁止登录的玩家用户名
        # 例子:
        # UnrestrictedName:
        # - 'n**layer'
        # - 'n**layer2'
        UnrestrictedName: []
    security:
        # 密码最小位数
        minPasswordLength: 5
        # 密码最大位数
        passwordMaxLength: 30
        # 加密方法: SHA256, BCRYPT, BCRYPT2Y, PBKDF2, SALTEDSHA512, WHIRLPOOL,
        # MYBB, IPB3, PHPBB, PHPFUSION, SMF, XENFORO, XAUTH, JOOMLA, WBB3, WBB4, MD5VB,
        # PBKDF2DJANGO, WORDPRESS, ROYALAUTH, CUSTOM (for developers only). 更多请查看
        # https://github.com/AuthMe/AuthMeReloaded/blob/master/docs/hash_algorithms.md
        passwordHash: 'SHA256'
        # 如果密码错误，会用以下方式来解密密码
        # 并且转换为新的加密方法
        # 例子
        # legacyHashes:
        # - 'SHA1'
        legacyHashes: []
        # 盐值长度 适用于加密方法 SALTED2MD5 MD5(MD5(password)+salt)
        doubleMD5SaltLength: 8
        # 当你使用 PBKDF2 加密方法时,回合的数量. 默认是 10000
        pbkdf2Rounds: 10000
        # 弱密码
        unsafePasswords: 
        - '123456'
        - 'password'
        - 'qwerty'
        - '12345'
        - '54321'
        - '123456789'
        - 'help'
    registration:
        # 是否开启注册功能
        enabled: true
        # 发送注册/登录消息的秒数
        messageInterval: 5
        # 是否强制需要注册
        force: true
        # 登录方式n: PASSWORD or EMAIL
        # PASSWORD = 玩家需要用密码登录
        # EMAIL = 玩家需要用邮箱登录
        # 更多请查看 https://github.com/AuthMe/AuthMeReloaded/wiki/Registration
        type: 'PASSWORD'
        # 是否需要二次确认密码
        # CONFIRMATION = 必须二次确认密码,不使用邮箱
        # EMAIL_OPTIONAL = 需要二次确认密码,可选邮箱
        # EMAIL_MANDATORY = 需要二次确认密码,必须使用邮箱
        secondArg: 'CONFIRMATION'
        # **后是否踢出玩家
        # 不使用登录
        forceKickAfterRegister: false
        # 成功注册后是否要登录
        forceLoginAfterRegister: false
    # 开启欢迎消息
    # 请在 welcome.txt 中修改
    # {PLAYER}: 玩家名称, {ONLINE}: 在线玩家
    # {MAXPLAYERS}: 最大在线玩家, {IP}: 玩家的IP, {LOGINS}: 已登录的玩家
    # {WORLD}: 每个世界的玩家, {SERVER}: 服务器名称
    # {VERSION}: 获取bukkit的版本, {COUNTRY}: 玩家IP所属的国家
    useWelcomeMessage: true
    # 广播到服务器或者单个玩家
    # true为服务器 false为单个玩家
    broadcastWelcomeMessage: false
    # 是否在登录后广播欢迎消息
    delayJoinMessage: false
    # 自定义加入欢迎消息,
    # 不填使用默认.
    # 变量:
    # {PLAYERNAME}: 玩家ID 不带颜色
    # {DISPLAYNAME}: 玩家的名称 带颜色
    customJoinMessage: ''
    # 是否去除未登录玩家的登出信息
    removeUnloggedLeaveMessage: false
    # 是否去除已经登录玩家的等登入消息
    removeJoinMessage: false
    # 是否去除所有登出消息
    removeLeaveMessage: false
    # 是否给未登录的玩家使用失明效果
    applyBlindEffect: false
    # 是否强制玩家名 玩家用 CH1 注册了,将不能使用Ch1或者ch1登录游戏
    preventOtherCase: true
GroupOptions:
    # 启用权限检测来划分组
    enablePermissionCheck: false
    # 可以防止玩家在未登录的时候执行一些具有漏洞的命令 区分大小写
    # 已注册玩家的组
    registeredPlayerGroup: ''
    # 未注册玩家的组
    unregisteredPlayerGroup: ''
Email:
    # SMTP服务器IP
    mailSMTP: 'smtp.gmail.com'
    # SMTP服务端口
    mailPort: 465
    # 仅适用于25端口,是否启用 TLS/STARTTLS 功能
    useTls: true
    # 发信邮箱账号例如 abc
    mailAccount: ''
    # 发信邮箱密码
    mailPassword: ''
    # 发信邮箱账户,例如 abc@abc.cn
    mailAddress: ''
    # 自定义发信名称
    mailSenderName: ''
    # 账户恢复验证码长度
    RecoveryPasswordLength: 8
    # 右键标题
    mailSubject: 'Your new AuthMe password'
    # 每个邮箱最多绑定多少个账户
    maxRegPerEmail: 1
    # 是否要求玩家绑定邮箱
    recallPlayers: false
    # 要求玩家绑定邮箱消息的延后时间
    delayRecall: 5
    # 邮箱黑名单
    emailBlacklisted: 
    - '10minutemail.com'
    # 邮箱白名单,设定后只允许指定邮箱进行绑定
    emailWhitelisted: []
    # 发送密码时是否使用图片的形式
    generateImage: false
    # Oauth2的token
    emailOauth2Token: ''
Hooks:
    # 是否注入multiverse来获取重生点
    multiverse: true
    # 是否注入bungeecord
    bungeecord: false
    # 当玩家登陆后自动传送到指定服务器
    sendPlayerTo: ''
    # 是否在加入服务器时禁用监视模式
    disableSocialSpy: false
    # 是否强制使用essentials的/motd指令
    useEssentialsMotd: false
Protection:
    # 是否开启保护模式
    enableProtection: false
    # 将保护模式应用于已注册用户
    enableProtectionRegistered: true
    # 禁止指定国家的人加入服务器
    # 国家列表: https://dev.bukkit.org/projects/authme-reloaded/pages/countries-codes
    # 要用大写
    countries: 
    - 'US'
    - 'GB'
    # 禁止加入服务器玩家的国家
    # 请用大写
    countriesBlacklist: 
    - 'A1'
    # 是否开启防压测系统
    enableAntiBot: true
    # 间隔 单位:秒
    antiBotInterval: 5
    # 在指定秒数内允许加入的玩家
    antiBotSensibility: 10
    # 防压测系统单次持续时间
    antiBotDuration: 10
    # 防压测系统激活延迟
    antiBotDelay: 60
Purge:
    # 是否删除长期未登录玩家的数据
    useAutoPurge: false
    # 应清除多久没上线玩家的数据
    daysBeforeRemovePlayer: 60
    # 是否删除文件 player.dat 
    removePlayerDat: false
    # 是否删除文件 Essentials/userdata/player.yml 
    removeEssentialsFile: false
    # 储存之players.dat文件的世界
    defaultWorld: 'world'
    # 是否删除文件 LimitedCreative/inventories/player.yml, player_creative.yml 
    removeLimitedCreativesInventories: false
    # 是否删除文件 AntiXRayData/PlayerData/player 
    removeAntiXRayFile: false
    # 是否删除权限
    removePermissions: false
Security:
    SQLProblem:
        # 数据库出现问题时是否关闭服务器
        stopServer: true
    console:
        # 是否在控制台内隐去玩家面膜
        removePassword: true
        # 是否输出authme日志到单独的文件
        logConsole: true
    captcha:
        # 开启验证码当玩家输入多次错误的面膜
        useCaptcha: false
        # 最大尝试次数,超过将启用验证码
        maxLoginTry: 5
        # 验证码长度
        captchaLength: 5
        # 多少分钟后重置是否需要验证码验证状态
        captchaCountReset: 60
    tempban:
        # 封禁玩家的IP地址当这个玩家输入多次错误的密码
        enableTempban: false
        # 输入多少次错误密码将临时封禁玩家IP
        maxLoginTries: 10
        # 单位:分钟,封禁时长
        # 默认: 480 分钟, 或者 8 小时
        tempbanLength: 480
        # 多少分钟后重置密码错误次数
        # 默认: 480 分钟 (8 小时)
        minutesBeforeCounterReset: 480
    recoveryCode:
        # 账户找回验证码的长度
        length: 8
        # 验证码失效时间
        validForHours: 4
        # 验证码最大尝试次数
        maxTries: 3
        # 当玩家恢复过密码后，多少分钟后可以再次恢复密码
        # 默认: 2 minutes
        passwordChangeTimeout: 2
    emailRecovery:
        # 邮箱找回冷却时间
        cooldown: 60
# 在登录前会移除玩家身上的所有状态，当登录后将会恢复
limbo:
    persistence:
        # 储存玩家状态信息,当服务器崩溃时,再次开服可以恢复这些信息
        # DISABLED: 不储存,
        # INDIVIDUAL_FILES: 每个玩家1个文件来储存,
        # DISTRIBUTED_FILES: 根据uuid分配到文件内见下文
        type: 'INDIVIDUAL_FILES'
        # 这里注释仅适用于 DISTRIBUTED_FILES 
        # 可选: ONE, FOUR, EIGHT, SIXTEEN, THIRTY_TWO, SIXTY_FOUR,
        # ONE_TWENTY 为128, TWO_FIFTY 为 256.
        # 举个例子，假如有100个未登录玩家，设置为Sixteen，每隔文件将会储存6.25个玩家(100 / 16).
        # 这项设置只会在开服时进行
        distributionSize: 'SIXTEEN'
    # 是否允许玩家飞行可选: RESTORE, ENABLE, DISABLE.
    # RESTORE 为恢复玩家的飞行状态
    restoreAllowFlight: 'RESTORE'
    # 恢复玩家的飞行: RESTORE, DEFAULT, MAX_RESTORE, RESTORE_NO_ZERO.
    # RESTORE: 恢复玩家原有的飞行速度
    # DEFAULT: 设置默认
    # MAX_RESTORE: 最大限度地恢复
    # RESTORE_NO_ZERO: 设为非0的默认值
    restoreFlySpeed: 'RESTORE_NO_ZERO'
    # 恢复行走速度选项: RESTORE, DEFAULT, MAX_RESTORE, RESTORE_NO_ZERO.
    # 恢复玩家行走的速度.
    restoreWalkSpeed: 'MAX_RESTORE'
BackupSystem:
    # 启用备份功能
    ActivateBackup: false
    # 开服的时候是否备份
    OnServerStart: false
    # 关服的时候是否备份
    OnServerStop: true
    # MySQL在windows下的目录
    MysqlWindowsPath: 'C:\Program Files\MySQL\MySQL Server 5.1\'
# 数据转换器设置: 更多请查看 https://github.com/AuthMe/AuthMeReloaded/wiki/Converters
Converter:
    Rakamak:
        # Rakamak 文件名称
        fileName: 'users.rak'
        # Rakamak 是否记录了IP
        useIP: false
        # Rakamak 记录的IP文件
        ipFileName: 'UsersIp.rak'
    CrazyLogin:
        # CrazyLogin 数据库文件
        fileName: 'accounts.db'
    loginSecurity:
        # LoginSecurity: 是否转换sqlite,设置为false将转换mysql
        useSqlite: true
        mySql:
            # LoginSecurity MySQL: 数据IP
            host: ''
            # LoginSecurity MySQL: 数据库名称
            database: ''
            # LoginSecurity MySQL: 数据库账户
            user: ''
            # LoginSecurity MySQL: 数据库密码
            password: ''
```

在运行的服务器上更改配置，你需要保存 config.yml 然后使用：
`/authme reload`.
