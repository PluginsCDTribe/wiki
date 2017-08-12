一些关于将一个世界中的区域复制到另一个世界的代码。

如果世界没有在使用中的话，Anvil API 处理的速度比这更快：
 - [Anvil API](/Anvil-API.md)
 - 但是使用起来可能会很困难

```Java
EditSession copyWorld = new EditSessionBuilder("world").autoQueue(false).build(); // 请查看 https://github.com/boy0001/FastAsyncWorldedit/wiki/WorldEdit-EditSession
EditSession pasteWorld = new EditSessionBuilder("newWorld").build(); // 请查看 https://github.com/boy0001/FastAsyncWorldedit/wiki/WorldEdit-EditSession
Vector pos1 = new Vector(10, 3, 10);
Vector pos2 = new Vector(50, 90, 50);
CuboidRegion copyRegion = new CuboidRegion(pos1, pos2);

BlockArrayClipboard lazyCopy = copyWorld.lazyCopy(copyRegion);

Schematic schem = new Schematic(lazyCopy);
boolean pasteAir = true;
Vector to = new Vector(30, 10, 30);
schem.paste(pasteWorld, to, pasteAir);
pasteWorld.flushQueue();
```