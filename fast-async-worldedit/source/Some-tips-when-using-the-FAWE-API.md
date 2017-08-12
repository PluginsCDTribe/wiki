## 使用 FAWE API 的一些性能提示：

### 1. 使用 EditSessionBuilder ，同时请不要启用你用不到的东西。
[查看这里。](/WorldEdit-EditSession.md)

### 2. 在可能时使用内置的迭代器：
```Java
// 幼稚的做法：
for (Vector pt : region) {
    BaseBlock block = editSession.getBlock(pt);
	// 做些什么
}
// 不错的做法：
// - 执行区块预读取
for (Vector pt : new FastIterator(region, editSession)) {
    BaseBlock block = editSession.getBlock(pt);
	// 做些什么
}
```
下列的类会执行区块预读取：
 - FastIterator
 - Fast2DIterator
 - FastChunkIterator
 - BreadFirstSearch
 - RegionVisitor

### 3. 使用已存在的功能或操作而不是设置单个方块：
```Java
// 幼稚的做法：单个方块改变
for (int x = 0; x <= 100; x++) {
    for (int z = 0; z <= 100; z++) {
        editSession.setBlock(x, 64, z, block);   
    }
}
// 不错的做法： 
//  - 执行区块预读取
//  - 执行整个区块而不是单个方块
//  - 并行处理一些东西
Region region = new CuboidRegion(new Vector(0, 64, 0), new Vector(100, 64, 100));
editSession.setBlocks(region, block);
```

### 4. 使用 FAWE 带来的 Sets 与 Collections 
```Java
// 幼稚的做法：储存单个位置
Set<Vector> positions = new HashSet<>(); // 然后在这里储存一些方块的位置

// 不错的做法：
// - 更快速，仅仅占用八百分之一的内存
positions = new BlockVectorSet(); 
```

### 5. 避免调用 AsyncWorld 或 Actor 类中一些与非方块或生物群系相关联的方法：
FAWE 还没有将这些进行异步优化。尝试使用 [TaskBuilder](/TaskBuilder.md) 来将它在主线程上分解。