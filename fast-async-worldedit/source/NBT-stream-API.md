安装 FAWE 以后，你能够在不将schem文件（schematic）或NBT不整体储存在内存中即可编辑它们。
 - 如果文件太大而不适合装入内存的话，你就需要这样做
 - 如果你想要从其中获得某些信息的话，你就需要这样做

```Java
// 让我们不将schematic文件加载到内存中，但从中读取一些信息吧
// Schematics 文件是被压缩储存的，所以在使用 NBTInputStream 之前我们首先需要使用 GZIPInputStream 
File file = new File("blah.schematic");
NBTInputStream is = new NBTInputStream(new GZIPInputStream(new FileInputStream(file)));
NBTStreamer streamer = new NBTStreamer(is);

// 获得长，宽，高
final Map<String, Short> dimensions = new HashMap<>();
// 你需要了解NBT文件的结构储存方式，这些特殊值都是用缩写储存的
streamer.addReader(new NBTStreamer.NBTStreamReader<Integer, Short>() {
    @Override
    public void run(Integer index, Short value) {
        // Index对这个来说是不那么重要的，但是如果想要做列表或数组的话它就很有用了
        dimensions.put(getNode(), value); // Put e.g. Schematic.Width -> 53
    }
}, "Schematic.Width", "Schematic.Height", "Schematic.Length");

// 让我们从其中获取实体吧，我知道它们将会是 CompoundTag 类型
streamer.addReader("Schematic.Entities.#", new NBTStreamer.NBTStreamReader<Integer, CompoundTag>() {
    @Override
    public void run(Integer index, CompoundTag entity) {
        // 对于 .# 和普通加载方式来说，它将会是 Index 和 Value
        // 在这里我们可以对每个实体进行不同的操作
    }
});

// 关于方块小节获得信息（也包括ID）（也可以使用 AddBlocks 和 Data）
streamer.addReader("Schematic.Blocks.?", new NBTStreamer.NBTStreamReader<Integer, Integer>() {
    @Override
    public void run(Integer length, Integer type) {
        Class<? extends Tag> clazz = NBTConstants.getClassFromType(type);
        // 这里我们可以做一些能够知道小节的长度和它的类型的事情
    }
});

// 现在我们就写好了我们想要的加载方式了，我们就可以读取文件了
streamer.readFully();
// 同时如果你想要 FAWE 在你找到你想找的东西之后停止读取的话，你也可以：
// streamer.readQuick();

System.out.println("Dimensions are: " + dimensions);
```
使用本 API 的类：
 - [SchematicWriter 直接可写入压缩后的 schematic 文件的数据中](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/sk89q/worldedit/extent/clipboard/io/SchematicWriter.java)
 - [The SchematicStreamer 会将一个 schematic 文件直接读取到剪切板上](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/jnbt/SchematicStreamer.java)