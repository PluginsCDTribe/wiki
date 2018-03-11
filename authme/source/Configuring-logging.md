配置文件 config.yml 里面包含了两个会影响 AuthMe 执行日志记录的选项.

#### Security.console.logConsole (true / false)
如果设置为 `true` ，所有控制台中 AuthMe 的日志都将会保存在 authme.log 。如果发生了技术性的错误 (在 Java 中成为 _Exception_ )，则会记录完整的堆栈跟踪。这提供了与错误有关的更多技术参数，我们开发人员十分关注这些。

#### settings.logLevel (INFO / FINE / DEBUG)
我们推荐 `FINE` 。在记录中除了 INFO 之外，都会记录一些更加详细的信息，这些信息同样十分重要和有趣。如果你有兴趣查看 AuthMe 的大量信息，你也可以使用 `DEBUG` 。这通常只是用于你想试着查找 AuthMe 问题的原因。
