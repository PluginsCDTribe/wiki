粘贴 schematic 文件
```Java
File file = new File("path/to/schematic");
boolean noAir = false;
boolean entities = true;
Vector position = new Vector(0, 0, 0);
SchematicFormat.getFormat(file).load(file).paste(editSession, position, noAir, entities);
editSession.flushQueue();

// 如果你安装了 FAWE 的话作为替代你也能使用这个：
boolean allowUndo = true;
EditSession editSession = ClipboardFormat.SCHEMATIC.load(file).paste(world, position, allowUndo, !noAir, (Transform) null);
```

保存为 schematic 文件
```Java
File file = new File("mySchem.schematic");
Vector bot = new Vector(0, 0, 0);
Vector top = new Vector(50, 255, 50);
CuboidRegion region = new CuboidRegion(new BukkitWorld(world), bot, top);
Schematic schem = new Schematic(region);
schem.save(file, ClipboardFormat.SCHEMATIC);
```