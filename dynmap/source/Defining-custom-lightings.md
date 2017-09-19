自定义光照可以通过修改默认的光照定义文件来实现， 详情见 **lightings.txt**，或通过添加自定义的全新的定义配置到 **custom-lightings.txt** 文件中去（原作者建议的首选方法）。

目前，Dynmap 支持两种光照类： DefaultHDLighting 类以及 ShadowHDLighting 类。 

DefaultHDLighting 类不会修改方块材质中的颜色数据 - 在没有阴影的情况下效果相当于白天的日光 - 并且没有可以供使用者修改的的配置项。

ShadowHDLighting 类支持更多的配置项，允许控制环境光源的倾斜角度，阴影强度， 以及为每个地图生成夜间和白天的光照版本的选项。

下面展示的是一个典型的默认光照配置文件的内容（ShadowHDLighting 类）：
```
    lightings:
      - class: org.dynmap.hdmap.ShadowHDLighting
        name: my-custom-lighting
        shadowstrength: 1.0
        ambientlight: 4
        night-and-day: true
        smooth-lighting: false
```
使用 ShadowHDLighting 类作为 Dynmap 光照源时可选的配置项如下展示：

- _name_ : 光照配置的唯一名称。如果使用者在 **custom-lightings.txt** 文件自定义的光照名称与现有的已使用的光照重名，则更新部署的光照配置将会替换掉旧部署的光照配置。

- _shadowstrength_ : 有光照时阴影区域所采取的阴影强度。默认值为 **0.0** （阴影强度可忽略不计），正常的阴影强度值为 **1.0**。 设置在1.0以上的值会产生较为明显的人为阴影效果，而少于1.0会导致阴影变弱。

- _ambientlight_ : 有光照时天空向地面投射的光照强度。晌午光照最强时的值为 **15** （默认值），午夜的光照强度一般为 **4** 。

- _night-and-day_ : 若启用此设置（通过将值设置为**true**），Dynmap 的在线地图生成系统将会为每个地图生成夜间和白天两个不同的光照版本， 并且如果访问者在网页访问在线地图时，系统会根据每个地图游戏内的真实时间来设置显示到在线地图的光照参数。白天与夜晚最大的区别是白天将会使 _ambientlight_ 设置到15， 而夜晚则会根据 _ambientlight_ 的环境光源设定而改变。  此选项的默认值为 **false** 。

* _smooth-lighting_ : 这是一个布尔值类型的配置项，用于开启或关闭平滑光照效果。  启用此功能将增加消耗10%的（网页服务器）渲染处理性能），但带来的是更平滑的阴影和照明效果。如果此处未进行定义， _smooth-lighting_ 的配置将会从 _configuration.txt_ 文件中获取。
 