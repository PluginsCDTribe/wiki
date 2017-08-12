FAWE 能够让你从一个兼容且配置过的网页服务器中上传或下载 schematic 文件。

### 有关的配置选项
```yml
web:
  # 我已经在这里为你配置好了一个网页接口了
  url: "http://empcraft.com/fawe/"
```

### 网页软件
https://github.com/boy0001/plotupload + custom style

### 上传剪切板
如果返回了 null 的话，那就是指示上传失败了。
```Java
URL url = FaweAPI.upload(clipboard, format);
```

### 下载：
```Java
URL base = new URL(Settings.WEB.URL);
URL url = new URL(base, "uploads/" + uuid + ".schematic");
ReadableByteChannel rbc = Channels.newChannel(url.openStream());
InputStream in = Channels.newInputStream(rbc);
// 读取并粘贴字符（假设它是 schematic 格式）等等
EditSession editSession = ClipboardFormat.SCHEMATIC.load(in).paste(world, position, allowUndo, !noAir, (Transform) null);
```