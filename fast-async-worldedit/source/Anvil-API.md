Anvil API 是用来修改未读取的 MCA 文件的。（ `<world>/region` ）

有关的包：
https://github.com/boy0001/FastAsyncWorldedit/tree/master/core/src/main/java/com/boydti/fawe/jnbt/anvil
# 使用 FaweQueue
```Java
String worldName = "world";
boolean hasSky = true;
File root = new File(worldName + File.separator + "region");
MCAWorld world = new MCAWorld(worldName, root, hasSky);
MCAQueue queue = world.getQueue();
// 在这里使用FaweQueue来做些什么
```
# 创建 MCA 文件
请查看 [HeightMapMCAGenerator](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/jnbt/anvil/HeightMapMCAGenerator.java)    
```Java
File dir = new File("TestWorld/region");
// 从高度图创建新生成器
// 注意：如果你不想使用图片的话，请使用另一个构造函数
BufferedImage heightMap = ImageIO.read(new URL("https://i.imgur.com/plFXYiI.png"));
// 我们的新生成器
HeightMapMCAGenerator gen = new HeightMapMCAGenerator(heightMap, dir);
// 加入一些峭壁
BufferedImage cliffHeightMap = ImageIO.read(new URL("https://i.imgur.com/wx5oiA7.png"));
boolean onlyWhite = false; // Only use the white parts of the heightmap
gen.setColumn(cliffHeightMap, new BaseBlock(BlockID.STONE), onlyWhite);
// 加入一些高草
gen.setOverlay(new BlockMask(gen, new BaseBlock(BlockID.GRASS)), new BaseBlock(BlockID.LONG_GRASS));
// 加入一些洞穴
gen.addCaves();
// 加入一些矿石
gen.addDefaultOres(new BlockMask(gen, new BaseBlock(BlockID.STONE)));
// 加入一些树
World world = WorldEdit.getInstance().getServer().getWorlds().get(0);
WorldData worldData = world.getWorldData();
File treeFolder = new File("trees");
ClipboardHolder[] trees = ClipboardFormat.SCHEMATIC.loadAllFromDirectory(treeFolder, worldData);
Mask flat = new AngleMask(gen, 0, 0); // Only flat terrain
boolean randomRotate = true;
gen.addSchems(flat, worldData, trees, 50, randomRotate);
// 你也能获得/设置指定的方块
// 注意：使用独特的方块的话，速度会比上面提供的方法更慢
gen.setBlock(0, 255, 0, new BaseBlock(BlockID.SPONGE)); // Set a specific block
System.out.println(gen.getLazyBlock(0, 255, 0)); // Get a specific block
// 好了，让我们创建世界吧！
gen.generate();
```
# 使用 EditSession
```Java
String worldName = "world";
boolean hasSky = true;
File root = new File(worldName + File.separator + "region");
MCAWorld world = new MCAWorld(worldName, root, hasSky);
EditSession editSession = new EditSessionBuilder(world)
    .checkMemory(false)
    .allowedRegionsEverywhere()
    .fastmode(true)
    .changeSetNull()
    .limitUnlimited()
    .build();
// 在这里使用 editSession 来做些什么（世界中没有被创建的区域不能被修改）
```

# 替换方块
```Java
String worldName = "world";
File root = new File(worldName + File.separator + "region");
MCAQueue queue = new MCAQueue(worldName, root, true);
MCAFilterCounter counter = queue.filterWorld(new MCAFilterCounter() {
    @Override
    public void applyBlock(int x, int y, int z, BaseBlock block, MutableLong ignore) {
        if (block.getId() == 5) { // Change the id if it's 5
            block.setId(7);
        }
    }
});
// 看： FaweBlockMatcher.fromBlocks(...) 会在方块与指定类型匹配时返回 true
// 看： FaweBlockMatcher.setBlocks(...) 能够修改指定方块的类型
```

# 删除指定半径外的区块
```Java
MCAQueue queue = new MCAQueue(worldName, root, true);

final int radius = 4000;
final int radiusSquared = radius * radius;

queue.filterWorld(new MCAFilter() {
    @Override
    public MCAFile applyFile(MCAFile mca) {
        int distanceX = Math.abs((mca.getX() << 9) + 256) - 256;
        int distanceZ = Math.abs((mca.getZ() << 9) + 256) - 256;
        int distanceSquared = distanceX * distanceX + distanceZ * distanceZ;
        if (distanceSquared > radiusSquared) {
            // 因为这个区块超出半径，删除这个文件
            mca.close();
            mca.getFile().delete();
            return null;
        } else if (distanceSquared + 512 < radiusSquared) {
            // 因为这个 MCA 文件在指定半径内，不修改这个文件
            return null;
        } else {
            return mca;
        }
    }

    @Override
    public boolean appliesChunk(int cx, int cz) {
        int distanceX = Math.abs((cx << 9) + 8) - 8;
        int distanceZ = Math.abs((cz << 9) + 8) - 8;
        int distanceSquared = distanceX * distanceX + distanceZ * distanceZ;
        if (distanceSquared > radiusSquared) {
            // 区块在半径外
            return true;
        } else {
            // 我们不关心在半径内的区块
            return false;
        }
    }

    @Override
    public MCAChunk applyChunk(MCAChunk chunk) {
        chunk.setDeleted(true);
        // 我们不想修改方块
        return null;
    }
});
```

