## 概览

waypoints.yml 是所有使用的传送点的配置文件。传送点是完全可选的特性，如果你不想在你的服务器上使用这个特性，你可以直接不去设置任何传送点。不会有任何冲突。

传送点在 wiki 中对应的页面有更详细的介绍，但是简单来说传送点是一些用于世界中传送的可配置的点，玩家可以解锁并连接他们用于快速旅行。

举个栗子，默认玩家没有解锁任何传送点，但是当玩家探索世界并发现传送点 A, B 和 D 后，玩家可以在这些点之间快速传送。如果玩家没有发现 C，玩家就不能看见或者传送到那里去。在传送点之间旅行消耗星能，其被定义在 waypoints.yml 中。当站在一个附近的传送点时，你可以简单的按一下 shift 键打开快速旅行菜单。

玩家可以在世界的任何地方执行 /wayppints 命令来检查他解锁了哪些传送点，但是点击传送点并不会进行传送，除非他站在某一个上。

解锁和传送时也有炫酷的动画，伴随音效。

## 默认配置

```yaml

# Waypoint ID, used as reference.
# Make sure the waypoints have different IDs.
spawn:

    # Name of waypoint displayed in the waypoint GUI.
    name: Spawn
    
    # Location of waypoint: <world> <x y z> <yaw> <pitch>
    # Yaw and pitch are where the player will be looking at when teleported.
    location: 'world 69 71 136 136 0'
    
    # Radius of waypoint around the specified location.
    radius: 1.5
    
    # Stellium cost in order to use the waypoint.
    # Stellium is like stamina however it's not used
    # by skills and regens much slower than mana.
    stellium: 3
    
    # When enabled, players can unlock the waypoint
    # by sneaking on it, and can open the waypoint menu
    # from the specified location (true by default).
    sneak: true
    
    # Should be waypoint be unlocked by default?
    default: true

spawn1:
    name: Spawn1
    location: 'world 69 71 136 136 0'
    radius: 1.5
    stellium: 3
    default: false
    
    # Can be teleported to even when not standing
    # on any waypoint (waypoint must be unlocked).
    dynamic: true

spawn2:
    name: Spawn2
    location: 'world 69 71 136 136 0'
    radius: 1.5
    stellium: 3
    sneak: false

```

## 配置详解
你可以创建任意多的传送点，甚至是多于一整页 GUI 的。所有选项如下：

* **Name**

这是在 /waypoints 菜单中显示的名称。这不同于内部的 ID，那玩意儿只用于配置里。他们不一样。

* **Location**

这里你指定了传送点的位置。你的配置的格式为 WORLD, X, Y, Z, PITCH, YAW。pitch 和 yaw 是玩家观察的方向。如配置中所示，最后放一个 0。

* **Radius**

这定义了玩家需要距离传送点多近才能解锁和按 shift 进行传送。半径以方块为单位，5 方块意味着如果玩家在 5 方块的距离以内按下 shift，他就能解锁这个传送点。最好将半径与建筑的大小匹配。

* **Stellium**

这定义了进行传送时消耗多少星能。如这里定义的，更高级的传送点需要消耗更多的性能。

* **Sneak**

指定是否需要蹲下解锁这个传送点。

* **Default**

这个传送点默认情况下是否解锁。

* **Dynamic**

动态的传送点可以在任何地点打开菜单使用。这意味着玩家可以使用动态传送点进行传送，哪怕他没有实际站在某个传送点附近。