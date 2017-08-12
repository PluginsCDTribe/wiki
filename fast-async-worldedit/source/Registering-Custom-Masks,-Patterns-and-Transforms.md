 安装 FAWE 插件后你能够注册你自己的蒙版，模板和变换式

```Java
FaweAPI.registerMasks(maskMethods);
FaweAPI.registerPatterns(patternMethods);
FaweAPI.registerTransforms(transformMethods);
```
将其中替换
 - `maskMethods` 是像如下内容的类 [这个](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/sk89q/worldedit/command/MaskCommands.java)
 - `patternMethods` 是像如下内容的类 [这个](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/sk89q/worldedit/command/PatternCommands.java)
 - `transformMethods` 是像如下内容的类 [这个](https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/sk89q/worldedit/command/TransformCommands.java)
