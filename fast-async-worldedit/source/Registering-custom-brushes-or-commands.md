安装 FAWE 插件之后你可以注册你自己的笔刷和命令：
```Java
/**
 * 使用提供的别称创建一条命令以及注册类的所有方法作为子命令。<br>
 *  - 你应该尝试在安装时注册命令
 *  - 如果没有指定别称的话，所有的方法都会变成根命令
 * @param clazz 类中包含了所有的子命令方法
 * @param aliases 给予本命令的别称（也可以不设置）
 */
FaweAPI.registerCommands(Object clazz, String... aliases);
```
来自 [`BrushCommands`](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/sk89q/worldedit/command/BrushCommands.java) 类的片段，注册圆柱体笔刷
```Java
@Command(
        aliases = { "cylinder", "cyl", "c" },
        usage = "<block> [radius] [height]",
        flags = "h",
        desc = "Choose the cylinder brush",
        help =
                "Chooses the cylinder brush.\n" +
                        "The -h flag creates hollow cylinders instead.",
        min = 1,
        max = 3
)
@CommandPermissions("worldedit.brush.cylinder")
public void cylinderBrush(Player player, LocalSession session, Pattern fill,
                          @Optional("2") double radius, @Optional("1") int height, @Switch('h') boolean hollow) throws WorldEditException {
    worldEdit.checkMaxBrushRadius(radius);
    worldEdit.checkMaxBrushRadius(height);
    BrushTool tool = session.getBrushTool(player);
    tool.setFill(fill);
    tool.setSize(radius);
    if (hollow) {
        tool.setBrush(new HollowCylinderBrush(height), "worldedit.brush.cylinder", player);
    } else {
        tool.setBrush(new CylinderBrush(height), "worldedit.brush.cylinder", player);
    }
    player.print(BBC.getPrefix() + BBC.BRUSH_SPHERE.f(radius, height));
}
```
圆柱体笔刷：
```Java
public class CylinderBrush implements Brush {

    private int height;

    public CylinderBrush(int height) {
        this.height = height;
    }

    @Override
    public void build(EditSession editSession, Vector position, Pattern pattern, double size) throws MaxChangedBlocksException {
        if (pattern == null) {
            pattern = new BlockPattern(new BaseBlock(BlockID.COBBLESTONE));
        }
        editSession.makeCylinder(position, Patterns.wrap(pattern), size, size, height, true);
    }

}
```

