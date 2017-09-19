这些设定是 _configuration.txt_ 文件中的第一级设定，一般来说，会覆盖插件的基础设置，但与特殊的部件、地图和世界无关。有关部件的设定，详见[部件设定](/Component-Configuration.md)。

核心设置包含以下内容：

* _deftemplatesuffix_ : 这个设定是可选的，字符串值。用于控制世界使用的模板，如果没有指定，那么普通的世界将会使用 **normal** 模板，地狱世界将会使用 **nether** 模板，末地世界将会使用 **the_end** 模板。当指定并且不为空后，使用的模板的名称将会是世界名加上下划线加上定义的内容。（比如 _deftemplatesuffix_ 设置为XXX，普通的世界将会使用 **normal_XXX** 模板而不是 **normal** 模板。地狱世界将会使用 **nether_XXX** 模板，末地世界将会使用 **the_end_XXX** 模板）。查看[高分辨率地图设定](/HD-Map-Configuration.md)获得更多的信息。默认的模板有 **vlowres**, **lowres**, **hires**, 和 **""** (留空)。

* _display-whitelist_ : 如果为 false（默认），用户是可见的直到他们使用了 _/dynmap hide_ 命令，如果设置为 true，用户默认是不可见的直到他们使用了 _/dynmap show_ 命令。

* _renderinterval_ : 这个设置为小数，以秒计算，用于控制多久之后tiles（比如玩家）需要被更新和处理。将这个设置的过低可能给服务器带来由于重复更新tiles的计算而额外的负担。默认为 0.5 秒，大多数的服务器设置为高于 0.2 的值都不会有问题。

* _renderacceleratethreshold_ : 这个设置为一个整数，用于设定处理从 _renderinterval_ 到 _renderaccelerateinterval_ 的tile更新队列的大小。这用于防止大量tiles的积累（玩家大量跑图创建新的区块时），不用以很快的速度处理常规的更新。

* _renderaccelerateinterval_ : 这个设定为以秒为单位的小数值，用于当tiles更新队列长度超过了 _renderacceleratethreshold_ 的值而使用的类似 _renderinterval_ 的值。

* _tiles-rendered-at-once_ : 这个设定控制异步渲染的更新tiles的最大数量。如果没有设置，那么默认的值会是处理器数量的一半。将这个值设置的偏小可以减少在大量加载更新tiles（如新生成的大量区块）时CPU的峰值使用量。

* _usenormalthreadpriority_ : 这个设定当设置为 true，会将渲染线程的优先度设置为普通（与最低优先度相比）。这可以帮助Windows下的渲染性能，但是可能会造成与其他进程的CPU使用竞争。大多数的Linux JVM忽略优先度。

* _zoomoutperiod_ : 这个设定为以秒为单位的整数，指定了移出的tiles的更新频率。用于防止由于玩家的重复改变（比如挖矿）而造成不必要的tiles的重新生成。默认的值为 60 秒。

* _enabletilehash_ : 此选项为 true 或者 false，用于启用tile数据的hash代码，可以用于避免在重新渲染后（比如tile不可见的方块）值没有发生变化的tile的重新编码。这减少了处理的负载、移出的处理和网页客户端的连接处理。

* _render-triggers_ : 这个设定为字符串列表，用于启用检测或者更新地图tile的不同的机制。定义的触发器如下：

    + _chunkloaded_ : 这个触发器当地图的区块加载时更新tiles。这个触发器不再被推荐 - 使用 _chunkgenerated_ ，因为 _chunkloaded_ 可能造成大量的不必要的tiles的计算。在 v0.31 被删除。

    + _playermove_ : 这个触发器在玩家移动时更新tiles。这个触发器不被推荐，因为会造成大量不必要的重新计算。

    + _playerjoin_ : 这个触发器会在玩家登陆后的周围的区域更新tiles。

    + _blockplaced_ : 这个触发器在玩家放置方块后更新tiles。（推荐）

    + _blockbreak_ : 这个触发器会在玩家破坏方块后更新tiles。（推荐）

    + _leavesdecay_ : 这个触发器会在玩家砍树后树叶掉落更新tiles。（推荐）

    + _blockburn_ : 这个触发器会在火破坏一个方块后更新tiles。（推荐）

    + _blockfaded_ : 这个触发器会在一个方块消失后（比如冰或雪融化）更新tiles。（推荐）

    + _blockspread_ : 这个触发器会在一个方块传播（岩浆或水的流动）时更新tiles。

    + _chunkgenerated_ : 这个触发器会在新的地图生成新的区块时更新tiles。（推荐）

    + _pistonmoved_ : 这个触发器会在活塞伸出或收回时更新tiles。（推荐）

    + _explosion_ : 这个触发器会在方块被爆炸摧毁后更新tiles。（推荐）

    + _blockfromto_ : 这个触发器会在方块流入新的方块（水、岩浆）更新tiles。（推荐）

    + _blockphysics_ : 这个触发器会在方块进行物理移动（掉落的沙砾、水、岩浆、沙子）时更新tiles。（推荐）

    + _structuregrow_ : 这个触发器会在树枝长成树或者蘑菇长成巨型蘑菇时更新tiles。

    + _blockgrow_ : 这个触发器会在方块生长（作物和蘑菇）时更新tiles。

    + _blockredstone_ : 这个触发器会在红石电流更新了一个方块时更新tiles。（在你有高频的红石机械运作时小心使用）

* _webpage-title_ : 这个设定为一个字符串，用于指定Dynmap网页的标题。如果没有设定，将会尝试使用 _server.properties_ 中的 'server-name'，如果没有设置或者为 'Unknown Server'，那么将自动设置为 'Minecraft Dynamic Map'。

* _tilespath_ : 这个设定为一个字符串，用于指定地图tiles生成的路径（可以是Dynmap插件目录相对路径或者绝对路径），（并且是内部服务器使用的路径）。

* _webpath_ : 这个设定为一个字符串，用于指定内部服务器的根目录。所有内部服务器使用的文件（除了地图tiles）都会基于这个路径。可以是Dynmap插件目录相对路径或者绝对路径。

* _webserver-bindaddress_ : 这个设定为一个IP地址，控制内部服务器的网络接口绑定的地址。默认为 0.0.0.0，将会让服务器绑定在所有的接口（应该对绝大部分的配置都是正确的）。设置为 127.0.0.1 会让其只绑定在本地网络（如果一个外部的Web服务器在同一台机器使用时可以这样做）。其他的值必须与网络地址匹配（不是防火墙外的公共地址或者代理）。

* _webserver-port_ : 这个设定为一个整数，指定了内部的Web服务器绑定的端口。默认为 8123。注意大多数的操作系统需要使用root权限运行程序才能将端口绑定至 1024 以下的端口。

* _max-sessions_ : 这个设定为一个整数，设置Web服务器活跃的最大的异步会话数量（限制会话使用的资源和线程）。默认的值为 30。

* _http-response-headers_ : 这个设置为一串属性/值对，提供了在所有的HTTP相应中添加自定义的header值。这个属相下的值为header的值。见下示例：

        http-response-headers:
            Access-Control-Allow-Origin: "http://mydomain.com"
            X-Another-Header: "Another Header Value"

* _disable-webserver_ : 如果设置为 _true_ ，内部的Web服务器将会关闭（这需要使用外部Web服务器，和`JSONFileClientUpdateComponent`部件），其他的配置选项需要将其设置为 _false_ 。

* _allow-symlinks_ : 如果设置为 _true_ ， _webpath_ 或 _tilespath_ 目录下的目录允许含有符号链接（symbolic link）。如果设置为 _false_ ，内部Web服务器将不会使用符号链接（推荐实验一下，因为几乎所有的外部Web服务器都会使用）。

* _timesliceinterval_ : 此设置为以秒为单位的小数，指定处理 _/dynmap fullrender_ 时tile处理的最小时间段。默认的值为 0.0 （无延迟）。非 0 的值可以在全部渲染时减少服务器的负载，但是会显著增长处理的时间。

* _maxchunkspertick_ : 此设置为一个整数，限制一个服务器tick中地图区块加载的数量。因为加载地图区块是Bukkit服务器主线程的主要负载源，这可以用来限制可能由于地图处理导致的卡顿。

* _progressloginterval_ : 此设置为一个整数，是全部渲染请求是记录进度的间隔。默认（并且最小）的值为 100。

* _parallelrendercnt_ : 此设置是可选的，为一个整数，用于在全部渲染时使用多于一条线程进行处理。这个设定表明了异步线程的数量，应该限制为服务器处理器的数量（或者少于）。设置此将会增加CPU的使用，可能会使用更多的内存。在设置为等于或者超过系统的处理器数量时应该保持注意。

* _updaterate_ : 此设置为以毫秒为单位的整数，指定Web客户端应该多长时间查询服务器的更新（无论是tiles更新
聊天信息或者玩家的位置更新）。设置更高的值会减少Web服务器的流量负载。

* _fullrenderplayerlimit_ : 此设置是可选的，设定了当玩家登陆的数量超过多少后停止处理全部渲染/范围渲染的值。默认为 0（停用），设置为 1 会在任何玩家登陆时停止处理全部渲染/范围渲染。

* _showplayerfacesinmenu_ : 这个设定为 true或者false，用于控制在网页托盘中是否显示在线玩家。默认显示（true）。

* _sidebaropened_ : 此设置为一个字符串，用于控制侧边栏菜单开启（true），固定（pinned）或者默认关闭（false）。默认为 false。

* _joinmessage_ : 此设置为一个字符串，用来控制玩家加入服务器时网页显示的消息。`%playername%` 用来表示玩家的名称。

* _quitmessage_ : 此设置为一个字符串，用来控制玩家退出服务器时网页显示的消息。`%playername%` 用来表示玩家的名称。

* _spammessage_ : 此设置为一个字符串，当网页聊天用户试图发送过多的信息时显示。

* _webprefix_ : 此设置为一个字符串，用于给接收到的网页聊天添加前缀。'&color;' 可以用来代替Bukkit颜色代码。

* _websuffix_ : 此设置为一个字符串，用于给接收到的网页聊天添加后缀。'&color;' 可以用来代替Bukkit颜色代码。

* _showlayercontrol_ : 此设置可为 true 或 false，用于控制覆盖层是否显示（设置为 false 会造成覆盖层的不显示，即使定义了记号层）。默认为 true。

* _check-banned-ips_ : 此设置可为 true 或 false，用于控制内部Web服务器是否检查 banned-ips.txt 来阻塞已经被禁止的IP连接到网页。

* _persist-ids-by-ip_ : 如果为 true，玩家的IP地址和联系的玩家ID是持久的，将会在服务器关闭或重启后被保存（）if true, player IP addresses and the associated player IDs are persistent, and will be saved on server shutdown and reloaded on server startup (允许累加玩家的已知IP)。默认为 true。（0.29及之后的版本）

* _defaultzoom_ : 此设置为一个整数，指定了网页被第一次加载时默认的缩放的大小。

* _defaultworld_ : 此设置为一个字符串，指定了网页被第一次加载时默认显示的世界。

* _defaultmap_ : 此设置为一个字符串，指定了网页被第一次加载时默认显示的地图。

* _followzoom_ : 此设置为可选的设置，为一个整数，指定了当网页选择了要跟随的玩家时，默认的缩放等级。

* _followmap_ : 此设置为可选的设置，为一个字符串，指定了当网页选择了要跟随的玩家时，默认显示的地图。

* _verbose_ : 此设置可为 true 或 false，控制Dynmap插件启动时的信息的详细程度。设置为 _false_ 将会明显减少显示的信息和细节。

* _hideores_ : 此设置可为 true 或 false，控制是否隐藏所有的矿物方块，让他们变得和普通的石块（防止利用地图寻找裸露的矿物）。默认为 false。

* _better-grass_ : 此设置可为 true 或 false，控制是否渲染草地和雪地的侧面，就像 BetterGrass Mod 一样。默认为 false。

* _smooth-lighting_ : 此设置可为 true 或 false，提供所有地图都支持的平滑光照的设定。设置为 true 可以在使用的所有地图上开启平滑光照，此选项也是每个着色器的基础设定，可以在单独的地图上开启这个特性。开启此特性将会增加 10% 的渲染成本。

* _use-generated-textures_: 此设置如果设置为 true，那么将导致基于材质包的高解析度地图使用Minecraft客户端相同的纹理来渲染水、岩浆和火焰。如果设置为 false，老的材质 texture.png 和 misc/water.png 将会使用。（0.29之前的结果）设置之后需要进行一次全地图的渲染才能得到正确的结果。

* _correct-water-lighting_: 此设置如果设置为 true，将会导致基于材质包的高解析度地图渲染器像Minecraft客户端一样处理水的光照。如果设置为 false，那么将会使用老的水 - 也就会更暗。（0.29之前的结果）设置之后需要进行一次全地图的渲染才能得到正确的结果。

* _fetchskins_ : 此设置可为 true 或 false，控制服务器在玩家登陆时是否尝试获取玩家的皮肤。如果设置为 false，默认的皮肤将会显示在所有玩家身上。默认为 true。

* _refreshskins_ : 此设置可为 true 或 false，控制每次玩家登陆时刷新皮肤数据。如果设置为 false，已有的文件将永远不会刷新（如果是管理员手动上传皮肤数据那么很有用）。默认为 true。
## 网页接口的用户登陆安全设定

网页支持的基于用户登陆的安全系统可以在这里设置：

* _login-enabled_ : 此设置可为 true 或 false，启用登陆安全支持（如果设置为 true）。

* _login-required_ : 此设置可为 true 或 false，强迫所有的用户登陆才能进入网页。（如果设置为 true）
