如果你想从其他的登录插件转换到 AuthMe，你可以使用我们的转换器来保留你的数据。转换器是使用命令来运行的，`/authme converter <name>` ，并在 config.yml 的 “Converter” 部分配置转换器。

- [AuthMe](#authme): 将数据库类型转换到另一种
- [CrazyLogin](#crazylogin)
- [LoginSecurity](#loginsecurity)
- [Rakamak](#rakamak)
- [RoyalAuth](#royalauth)
- [vAuth](#vauth)
- [xAuth](#xauth)

## AuthMe
可以将数据从 AuthMe 的数据库类型中转换成另一种。

#### SQLite 转 MySQL
命令： `/authme converter sqliteToSql`  
在 config.yml 中设置为使用 MySQL 数据库以及 MySQL 的连接信息。SQLite 数据库必须要在 `plugins/AuthMe` 目录下，并且必须要与配置的数据库名字相同（"DataSource.mySQLDatabase" 在 config.yml）。

#### MySQL 转 SQLite
命令： `/authme converter mysqlToSqlite`  
在 config.yml 中设置为使用 SQLite 数据库。在 config.yml 中设置 MySQL 要连接到 MySQL 数据库的连接信息。

## CrazyLogin
命令： `/authme converter crazylogin`  
仅支持平面文件。复制 DB 平面文件到 plugins/AuthMe 文件夹，并将config.yml中的 `Converter.CrazyLogin.fileName` 配置为你的文件的名字。

## LoginSecurity
命令： `/authme converter loginsecurity`  
支持两种平面文件以及 MySQL – 在 config.yml 中配置 (参阅 "Converter.loginSecurity")。在平面文件的情况下， DB 平面文件必须要在常规位置，也就是在 `plugins/LoginSecurity/LoginSecurity.db` 。

## Rakamak
🕸 已经死了很多年了，或许不会再有人用了？  
命令： `/authme converter rakamak`  
仅支持平面文件，在 config.yml 中见 "Converter.rakamak" 。

## RoyalAuth
命令： `/authme converter royalauth`  
仅能迁移名字、密码和最后一次登录信息。

## vAuth
🕸 已经死了很多年了，或许不会再有人用了？  
命令： `/authme converter vauth`

## xAuth
命令： `/authme converter xauth`  
该转换器需要加载 xAuth 插件才能工作！xAuth 无论用啥存储数据 AuthMe 都能迁移。