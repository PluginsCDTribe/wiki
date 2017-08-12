与 [FaweQueue](/FaweQueue.md) 有关联

### 获取当前的 NMS 队列
```Java
boolean autoQueue = false;
NMSMappedFaweQueue nmsQueue = (NMSMappedFaweQueue) SetQueue.IMP.getNewQueue("worldName", true, autoQueue);
```

相关联的方法
 - relight(int x, int y, int z)
 - relightBlock(int x, int y, int z)
 - relightSky(int x, int y, int z)
 - setSkyLight(int x, int y, int z, int value)
 - setBlockLight(int x, int y, int z, int value)

相关联的类
 - [FaweQueue](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/object/FaweQueue.java)
 - [MappedFaweQueue](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/example/MappedFaweQueue.java)
 - [NMSMappedFaweQueue](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/example/NMSMappedFaweQueue.java)