很多人都注意到了，在Xenon或者其他全时间的托管服务上运行Dynmap是不会工作的，并且尝试进入页面会给你一个黑屏。这个教程希望能帮助你在几步内解决这个问题，它需要你有自己的托管服务，（以我来说，1and1.com）

开始，下载最新版的Dynmap： http://webbukkit.org/jenkins/public/dynmap/dynmap-recommended-bin.zip - 然后像其他插件一样上传你的插件。

解压文件，打开你的FTP应用（FileZilla就很好）并登入你的web托管服务。你需要放入Xenon不允许的 JS 文件，到你的web托管的某个文件夹。不要忘记将 "config.js" 复制。记住到这个文件夹的URL地址（对我来说就是 www.mavbear.com/map/web/js）。

打开任意的文本编辑器，开启 "web/index.html" 文件，你会看到像这几行一样的：

`<script type="text/javascript" src="js/jquery.json.js"></script>`

这里需要注意 "js/jquery.json.js" - 你将会需要将其重命名为你的实际的文件夹地址，这个例子里，我是 "http://www.mavbear.com/map/web/js/jquery.json.js"。

对每一行以"js"的都这样样做，底部的 "config.js" 也需要这样。

保存 index.html 文件，上传覆盖已经出现在你的Minecraft服务器的文件。

接着打开 map.js，前往 403 行（v0.70.1，可能在新版本改变）：

`loadjs('js/' + type + '.js', function() {`

替换为

`loadjs('(YOUR URL HERE)/js/' + type + '.js', function() {`

重新上传 'map.js' 文件到你的web托管服务（不是Minecraft服务器）。

这个部分是必要的，者可以让你看见地图的玩家，还能使用聊天服务，否则你将只能看见地图。

这就是完整的教程了！希望能够帮助你。
