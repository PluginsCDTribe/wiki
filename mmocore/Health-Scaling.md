血条压缩是一个轻量的RPG功能，它使得玩家的生命栏总是显示相同数量的红心(同时不会影响生命值的上限)。当你的生命上限增加到40(默认情况)时，玩家的生命栏将显示2行 (总共 2 * 20) 个红心。

## 没有压缩血条的情况下
![](https://i.imgur.com/2wl2fpg.png)

## 压缩了血条的情况下
![](https://i.imgur.com/BNrYOoG.png)

## 血条压缩配置
你可以很容易地在插件主配置文件中配置血条压缩的功能:
```yaml
# Allows to scale health up/down to a specific amount
# so extra max health does not fill up the screen.
health-scale:
    enabled: true
    scale: 40
```