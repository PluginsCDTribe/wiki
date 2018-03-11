你可以在Jenkins 中获取 AuthMe 的最新版本 ("开发版本") :

- [AuthMeReloaded Dev Jenkins](http://ci.xephi.fr/job/AuthMeReloaded/) – 每次更改都会运行

#### 如何找到下载地址
左侧的 "Build history" 面板显示的是最新的_构建_ ，如果在数字的旁边有一个蓝色的圆圈，则表明该代码可成功转换为可以给你服务器使用的 .jar 文件 。

点击构建版本号即可开始下载生成好的 JAR 文件，你可以获取最新的版本 (例如 点击 #347 并在 "Build artifacts" 中下载对应的 .jar 文件 ).

记住: 在 Jenkins 中每次 _更改_ 都会运行一次，也就是说它可能会修复最近出现的一些错误或者是又出现了新的问题。

