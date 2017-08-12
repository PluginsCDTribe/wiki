FAWE 安装之后，你就能使用 API 来注册一个新的 ClipboardFormat 了
```Java
 // （格式的名字，别名……）
ClipboardFormat.addFormat(new AbstractClipboardFormat("CUSTOM", "custom") {
    @Override
    public ClipboardReader getReader(InputStream inputStream) throws IOException {
        return new yourCustomClipboardReader();
    }

    @Override
    public ClipboardWriter getWriter(OutputStream outputStream) throws IOException {
        return new yourCustomClipboardWriter();
    }

    @Override
    public boolean isFormat(File file) {
        // 如果这个文件使用这个格式的话就返回 true （通常只会检查扩展名）
        return file.getName().endsWith(".custom");
    }

    @Override
    public String getExtension() {
        return "custom";
    }
});
```

然后格式就可以在游戏中使用了： `//schem load <format> <file>`
