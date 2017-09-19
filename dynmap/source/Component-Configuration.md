Dynmap的接口通过一些部件构成。不是所有的部件都可以被开启，并且有些必须开启。冠以这些部件和他们的属性可以下接下来的章节找到。

# 核心客户端部件

接下来的部件指定了网页的核心接口。客户端配置部件，和至少一个的客户端更新部件都是必须添加的。

## 客户端配置部件

这个部件在 _components_ 章节如下定义：
    
      - class: org.dynmap.ClientConfigurationComponent

此部件是必须的，并且没有任何设置。

## 内部客户端更新部件

这个部件定义了Dynmap内部服务器的Web网页的主接口（这是部件运行必须开启的）。这个部件设置了用户使用的在 http://地址:端口/up/ 路径下的URL，包括了获取配置数据和地图更新，玩家信息和聊天信息。这个部件在 _components_ 章节这样配置：

      - class: org.dynmap.InternalClientUpdateComponent
        sendhealth: true
        sendposition: true
        allowwebchat: true
        webchat-interval: 5
        hidewebchatip: false
        trustclientname: false
        use-player-login-ip: true
        require-player-login-ip: false
        block-banned-player-chat: true
        webchat-requires-login: false
        webchat-permissions: false
        includehiddenplayers: false
        hideifshadow: 15
        hideifundercover: 15
        hideifsneaking: false
        protected-player-info: false

设置如下：

* _sendhealth_ : 此选项控制了网页是否发送玩家的生命信息。如果关闭，其他反馈玩家生命信息的部件将不会使用此数据，玩家的生命信息也不会受到检查，如果启用，生命信息仍然可以通过在世界设定的 _sendhealth: false_ 选项来关闭。

* _sendpostiion_ : 此选项控制了是否向网页发送玩家的位置信息。如果关闭，其他反馈玩家位置信息的部件将不会使用此数据，玩家的位置信息也不会受到检查，如果启用，位置信息仍然可以通过在世界设定的 _sendhealth: false_ 选项来关闭。

* _allowwebchat_ : 此选项控制了网页是否被允许向服务器发送网页聊天消息。如果停用，用户将不会发送任何网页聊天消息。

* _webchat-interval_ : 此选项控制来自同一个网页的聊天信息的最小间隔，以秒为单位。

* _hidewebchatip_ : 如果设置为 true，网页聊天将会显示为和游戏内IP地址相同的玩家的名称显示。

* _trustclientname_ : 如果设置为 true，服务器将会使用网页使用者上传的IP地址（可能被伪造）而不是服务器获取的IP地址。

* _use-player-login-ip_ : 如果设置为 true，网页聊天将会匹配当前或以前登陆的玩家的相同的IP地址 - 如果找到了匹配，将会以该玩家的ID作为身份标识。默认为 true（0.29或之后）。

* _require-player-login-ip_ : 如果 _use-player-login-ip_ 为 true 且此选项设置为 true，网页聊天没有匹配到当前或以前登陆的玩家的消息将会被忽略。默认为 false。（0.29或之后）

* _block-banned-player-chat_ : 如果 _use-player-login-ip_ h设置为 true 且此选项设置为 true，网页聊天匹配到已经被ban的玩家将被忽略。默认为 true（0.29或之后）。注意将不会对实现了自身的禁止系统的插件支持。

* _webchat-requires-login_ : 如果 _login-enabled_ 设置为 true 且此选项设置为 true，网页聊天信息只能由已经登录的用户发送。

* _webchat-permissions_ : 如果设置为 true，绑定玩家的（通过登录或者IP）网页聊天将会检查 `dynmap.webchat` 权限，如果没有权限将被禁止发送。这需要一个支持读取离线玩家的权限的权限系统 - 比如 PermissionsEx 和 LuckPerms - 来让不用使用Minecraft客户端登录的玩家也能被检查权限。

* _includehiddenplayers_ : 如果设置为 true，隐藏的玩家（使用 /dynmap hide 命令）也会显示在网页UI上，但是他们的位置、生命和信息仍然会隐藏，他们只出现在玩家列表里。

* _hideifshadow_ : 如果设置为小于 15 的值，每个玩家的位置信息和生命信息都将在一定的光照亮度下被隐藏。（0=完全黑暗，4=晚上露天，15=完全的白天）

* _hideifundercover_ : 如果设置为小于 15 的值，每个玩家的位置信息和生命信息都将在他被覆盖时隐藏。由于当前的Bukkit的限制（我们已经发出了 pull request），我们将将此设置改为基于阴影等级的判定（白天的该坐标的阴影等级）。

* _hideifsneaking_ : 如果设置为 true，潜行的玩家将被隐藏。

* _protected-player-info_ : 如果设置为 true，玩家的位置信息和生命信息将受到保护，没有 _dynmap.playermarkers.seeall_ 权限的玩家（OP默认拥有）将只会看见此玩家的标记，而拥有此权限的用户将看见完整的玩家信息。如果此设定没有被设置或者设置为 false，那么所有的生命信息和位置信息都对所有人可见。

## JSON 文件客户端更新部件

使用内部Web服务器的另一种方法是将Dynmap和Web客户端的通信全部由一个外部Web服务器完成。这个文件的格式为 JSON（JavaScript Object Notation），操作的模式为"JSON 文件模式"。此模式允许内部Web服务器被关闭，转而使用内部客户端更新部件（它们之中一次只能启用一个）。此部件在 _components_ 部分这样设置：
    
      - class: org.dynmap.JsonFileClientUpdateComponent
        writeinterval: 1
        sendhealth: true
        sendposition: true
        allowwebchat: false
        webchat-interval: 5
        hidewebchatip: false
        trustclientname: false
        use-player-login-ip: true
        require-player-login-ip: false
        block-banned-player-chat: true
        webchat-requires-login: false
        webchat-permissions: false
        includehiddenplayers: false
        hideifshadow: 15
        hideifundercover: 15
        hideifsneaking: false
        protected-player-info: false

定义的属性与内部客户端更新部件相同，附加的属性如下：

* _writeinterval_ : 此选项单位为秒，控制写入到 _webpath_/standalone 目录的间隔时间，这些文件为网页用户通过外部Web服务器加载地图配置使用的文件，也用于更新地图、玩家信息和生命值和聊天信息。

# 标记部件

此部件添加于 v0.22，提供了地图记号标记的内置支持，可以通过 /dmarker 命令或者API来使用。部件在 _components_ 部分如下设置：

      - class: org.dynmap.MarkersComponent
        type: markers
        showlabel: false
        enablesigns: false
        showspawn: false
        spawnicon: world
        spawnlabel: "Spawn"
        showofflineplayers: false
        offlinelabel: "Offline"
        offlineicon: offlineuser
        offlinehidebydefault: true
        offlineminzoom: 0
        maxofflinetime: 30
        showspawnbeds: false
        spawnbedlabel: "Spawn Beds"
        spawnbedicon: "bed"
        spawnbedhidebydefault: true
        spawnbedminzoom: 0
        spawnbedformat: "%name%'s bed"

部件包含的设置如下：

* _showlabel_ : 如果定义并设置为 true，这将导致地图标记的标签始终显示，而不是当用户将鼠标放在上面才显示。

* _enablesigns_ : 如果定义并设置为 true，这将开启对牌子的标记支持。如果启用并且玩家拥有 `dynmap.marker.sign` 权限，玩家可以通过创建一个第一行为 '[dynmap]' 的牌子，来启用一个以第二行开始的标记。图标将会是 'sign' 图标，除非牌子上有一行是 'icon:<icon-id>'。标记组将会是默认的 'markers' 集合，除非牌子上有一行是 'set:<set-id>'。一旦通过检查，'[dynmap]' 行和任何的设置行将会是空白的，留下标签行和任何剩余的行，破坏牌子将会删除对应的标记。

* _showspawn_ : 如果定义并设置为 true，这将让每个世界的出生点显示为一个合适的标记（默认为 'world' 标记）和标签（默认为字符串 'Spawn'）。

* _spawnicon_ : 如果定义，提供出生点使用的标记（如果 _showspawn_ 设置为 true）。默认为 'world'。

* _spawnlabel_ : 如果定义，提供出生点使用的标签（如果 _showspawn_ 设置为 true）。默认为 'Spawn'。

* _showofflineplayers_ : 如果定义并设置为 true，将会添加一个显示离线玩家的标记层。（当玩家离线时会添加标记）

* _offlinelabel_ : 如果定义，提供离线玩家使用的标签。默认为 'Offline'。

* _offlineicon_ : 如果定义，提供离线玩家使用的标记。默认为 'offlineuser'。

* _offlinehidebydefault_ : 如果定义并设置为 true，离线玩家标记层将默认隐藏。默认为 true。

* _offlineminzoom_ : 如果设置不会 0，浙江制定显示离线玩家标记前的最小缩放等级。

* _maxofflinetime_ : 如果设置为大于0，这将指定玩家离线后的几分钟内标记应该被移除（小于等于0位从不）。所有的离线玩家的标记都将在服务器重启后被重置，独立于此设定。

* _showspawnbeds_ : 如果定义并设置为 true，将会显示在线玩家的出生点床的位置的标记层。（标记将在玩家离线后被移除）

* _spawnbedlabel_ : 在线玩家出生点床使用的标签。默认为 'Spawn Beds'。

* _spawnbedicon_ : 在线玩家出生点床使用的标记。默认为 'bed'。

* _spawnbedhidebydefault_ : 如果为 true，出生点床标记层将会被隐藏，默认隐藏。

* _spawnbedminzoom_ : 如果设置不为0，这将指定出生点床标记显示前最小的缩放等级。

# 服务器聊天部件

这些部件控制了服务器端实现的聊天功能，包括了从服务器发送至客户端聊天消息，和客户端到服务器的玩家聊天的显示。这些部件一次只能设置一个。

## 基础聊天部件

此部件实现了标准Bukkit/Minecraft服务端聊天通道，当激活时，所有的聊天消息都会被共享给网页用户，所有从网页接收到的聊天消息也将发送给服务器上的玩家（当然也有其他的网页用户）。此部件在 _components_ 中如下配置：

      - class: org.dynmap.SimpleWebChatComponent
        allowchat: true

部件包含以下设置：

* _allowchat_ : 如果启用，将会决定服务器上的聊天是否发送给网页，如果设置为 false，将不会给网页发送聊天消息。

## HeroChat 聊天部件 （弃用 - 不兼容 HeroChat 5）

HeroChat 插件实现了特殊的聊天通道。此部件允许选择HeroChat的特定聊天通道发送给网页客户端，网页聊天显示于哪一条通道。此部件在 _components_ 中如下配置：

      - class: org.dynmap.herochat.HeroWebChatComponent
        herochatwebchannel: Global
        herochatchannels:
          - Global

此部件包含如下选项：

* _herochatwebchannel_ : 从网页接收到的聊天信息显示于 HeroChat 的聊天通道的名称。默认为 'Global'。

* _herochatchannels_ : 此为HeroChat聊天通道需要监视的名称，将会共享给网页用户。0或者多个通道可能被列出，默认只有 Global。

# 客户端聊天部件

这些部件控制了网页是否启用并支持发送和接受聊天消息。这些部件基于对应的服务端部件才能接受请求的功能。部件可以被单独定义也可以结合。

## 聊天客户端部件

此部件启用了聊天信息的输入部分，允许用户进入并从网页向服务器发送聊天信息。此部件如下配置：

      - class: org.dynmap.ClientComponent
        type: chat
        allowurlname: false

此部件包含如下选项：

* _allowurlname_ : 如果设置为 true （并且 _trustclientname_ 在对应的客户端更新部件），用户可以通过 _chatname_ URL 参数应用自己的聊天名称。

## 聊天气泡客户端插件

此部件实现了可弹出的气泡信息，气泡可以在地图上玩家的位置出现。此部件在 _components_ 中如下配置：

      - class: org.dynmap.ClientComponent
        type: chatballoon
        focuschatballoons: false

此部件包含如下选项：

* _focuschatballoons_ : 如果启用，这将导致气泡如果不在地图上显示，地图将会平移至气泡的位置。

注意放置气泡需要先知道说话的玩家的位置信息，如果 _sendposition: false_ 设置于玩家的当前的世界，或者通过激活的客户端更新部件来全局设置会失效。

## 聊天栏客户端部件

此部件实现了从服务器和其他网页接受消息并显示在聊天栏的功能。此部件在 _components_ 中如下配置：

      - class: org.dynmap.ClientComponent
        type: chatbox
        showplayerfaces: true
        messagettl: 5
        scrollback: 100
        sendbutton: false

此部件包含如下选项：

* _showplayerfaces_ : 如果启用，玩家的头像将会在消息前显示。

* _messagettl_ : 这控制了显示的消息几秒钟后消失。如果 _scrollback_ 设置，此设置将被忽略。

* _scrollback_ : 如果定义，这指定了最多在可滚动的信息列表里保存多少条消息。如果指定，消息将不会淡出（_messagettl_被忽略）并只会将超过 _scrollback_ 的数量的聊天信息移除。

* _sendbutton_ : 如果定义并设置为 true，这将在WebUI上显示一个发送按钮，允许按按钮而不是使用回车键发送消息。

# 地图控制部件

这些部件定义了附加的地图数据，例如玩家记号、时间、日志等。任何部件都可以被定义。

## 玩家图标部件

此部件用于在地图上以图标显示玩家的位置和名称。玩家的位置信息只能在可用时（查看 _sendposition_ 上方的设置）才会显示。此部件在 _components_ 中如下配置：

      - class: org.dynmap.ClientComponent
        type: playermarkers
        showplayerfaces: true
        showplayerhealth: true
        showplayerbody: false
        smallplayerfaces: false
        hidebydefault: false
        layerprio: 0
        label: "Players"

此部件包含如下选项：

* _showplayerfaces_ : 如果启用，这将让网页试图加载玩家的自定义的皮肤作为头像的图标。否则将会加载一个通用的小图标作为标记。

* _showplayerhealth_ : 如果启用，客户端将会尝试显示在图标下方以两行显示玩家的生命和护甲值。这要求玩家的生命信息必须可用（查看上方的 _sendhealth_）。

* _smallplayerfaces_ : 如果启用，玩家的头像将会以 1/2 显示（与 _showplayerfaces_ 开启有关）（如果 _showplayerfaces_ 关闭将会显示默认图标的 1/2 大小）。

* _showplayerbody_ : 如果启用，将会显示整个身体的图标而不仅是头像，只有在 _showplayerfaces_ 设置为 true 并且 _smallplayerfaces_ 设置为 false 才可用。

* _hidebydefault_ : 此选项是可选的，如果定义并设置为 true，将会更改地图上玩家的图标的默认可见性设定。该图标层仍然可被WebUI控制设置为可见。

* _layerprio_ : 此选项是可选的，提供了图层选择的权重排序，从最低排到最高的 _layerprio_，（相同权重以字母顺序排序）。默认为 0。

* _label_ : 此选项是可选的，提供了用于选择控制图层的标签。默认为 'Players'。

## 数字钟部件

此部件用于显示一个简单的数字钟，显示显示的世界对应的时间。此部件在 _components_ 中如下配置：

      - class: org.dynmap.ClientComponent
        type: digitalclock

一次只能开启一个数字钟部件。

## 日月时钟部件

这是一个更加复杂的时钟部件，通过太阳和月亮图标的升起降下来对应当前世界的时间。此部件在 _components_ 中如下配置：

      - class: org.dynmap.ClientComponent
        type: timeofdayclock
        showdigitalclock: true
        showweather: true

此部件包含如下选项：

* _showdigitalclock_ : 如果启用，数字时钟将会显示（附加于日月的显示）。

* _showweather_ : 

## 坐标部件

此部件用于显示鼠标所指的地方对应的世界的坐标。此部件在 _components_ 中如下配置：

       - class: org.dynmap.ClientComponent
         type: coord
         label: "Location"
         hidey: false
         show-mcr: false

此部件包含如下选项：

* _label_ : 允许控制用于显示坐标的标签，默认为 'x,y,z'。

* _hidey_ : 此选项如果定义并设置为 true，会只显示 X,Z 坐标。

* _show-mcr_ : 此选项如果定义并设置为 true，会显示当前位置的Minecraft区域文件ID。

## Logo 部件

此部件允许在地图上显示一个可选的图标和链接。此部件在 _components_ 中如下配置：

       - class: org.dynmap.ClientComponent
         type: logo
         text: "Dynmap"
         linkurl: "http://forums.bukkit.org/threads/dynmap.489/"

此部件包含如下选项：

* _text_ : logo的标签

* _linkurl_ : 显示的标签链接到的 URL。

## 链接部件

此部件可以在WebUI显示一个 '链接到' 按钮。这个按钮点击后会链接到另一个页面，但是会保留世界的地图、缩放和当前的视图的位置信息 - 允许将视图分享，作为标签或者其他的链接。此部件在 _components_ 中如下配置：

       - class: org.dynmap.ClientComponent
         type: link

现在没有任何设置。
