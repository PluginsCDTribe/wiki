FAWE 可以限制玩家对 WorldEdit 的使用，需要配置文件中设置 `Settings.REGION_RESTRICTIONS`=`true`

### 注册提供器
```Java
FaweAPI.addMaskManager(new PlotSquaredFeature());
```
查看：https://github.com/boy0001/FastAsyncWorldedit/blob/master/core/src/main/java/com/boydti/fawe/regions/general/plot/PlotSquaredFeature.java