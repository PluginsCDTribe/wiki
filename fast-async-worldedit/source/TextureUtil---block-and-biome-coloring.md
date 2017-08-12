### 注意：
 - 将带有你想要的材质的 jar 文件（例如 `.minecraft/versions/<version>/<version>.jar`）放入 FastAsyncWorldEdit/textures  文件夹中  
 - 颜色使用 RGB(A) 颜色整数来表示，它可以通过使用 Color#getRGB() 获得。    
    
### 构造函数   
randomization = 方块会随机化拥有更加棒的本地颜色而不是照搬像素
Complexity 是一个方块的材质有多少种颜色，例如：石英方块就很低，TNT就很高
minComplexity, maxComplexity 是百分比值，对于 mc:1.11 我找到了 0, 73 为合适的值 
> TextureUtil tu = Fawe.get().getCachedTextureUtil(randomization, minComplexity, maxComplexity)    
    
要想指定方块我们可以使用 FilteredTextureUtil，它封包在 CachedTextureUtil 之中    
> TextureUtil tu = new CachedTextureUtil(new FilteredTextureUtil(Fawe.get().getTextureUtil(), blocks))    
    
### 方法   
获得一个方块的平均颜色  
> tu.getColor(BaseBlock block)     
    
获取距离一个颜色最近的方块    
> tu.getNearestBlock(int color)     
    
getNextNearestBlock(getColor(block)) 的别称    
> tu.getNearestBlock(BaseBlock block)     
    
获取距离一个颜色最近的方块 —— 如果没有精准匹配的话，它会返回下面的最近的方块
> tu.getNextNearestBlock(int color)     
    
    
为一种颜色获取最接近的玻璃+方块搭配。
它会返回 char { int glassCombinedId, int blockCombinedId }    
combinedId 为 (id << 4) + 数据值，请查看 FaweCache.getId(combined), FaweCache.getData(combined)    
> tu.getNearestLayer(int color)    
    
获取比这亮的最近的方块    
> tu.getLighterBlock(BaseBlock block)    
    
获取比这暗的最近的方块    
> tu.getDarkerBaseBlock block)    
    
从一个生物群系ID获得 BiomeColor 对象    
从 biomeRegistry 中获得生物群系ID    
BiomeRegistry biomeRegistry = FaweAPI.getWorld(worldName).getWorldData().getBiomeRegistry()    
> tu.getBiome(int biome)    
    
获得对一个颜色来说最接近的 BiomeColor 对象  
> tu.getNearestBiome(int color)    