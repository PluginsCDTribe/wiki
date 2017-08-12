#### 注意：如果你需要帮助恢复文件的话请联系我（ticket，IRC等等）

如果一个NBT格式的文件部分损坏的话，还是能恢复部分数据的——只要压缩文件的开头还是完整的（如果它是压缩文件），且NBT TAG的名字还是完整的。

对于 GZIP 而言，不需要出现压缩格式。

[CorruptSchematicReader](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/jnbt/CorruptSchematicStreamer.java) 已经包括在 FAWE 插件中了，它可以恢复错误的schematic文件，但是它所使用的方法对于格式相似的MCA文件和其他以NBT为基础格式的文件也同样适用。

这是一段匹配 `Width` 标签且能够设置 width 变量的值的片段。

```Java
match("Width", new CorruptSchematicStreamer.CorruptReader() {
    @Override
    public void run(DataInputStream in) throws IOException {
        width.set(in.readShort());
    }
});
```
也有另外一种方法，能够猜出schematic文件所在的维度，它需要了解某些数据值的程度来了解是否缺少了维度标签：
 `Vector guessDimensions(int volume, int width, int height, int length)`

