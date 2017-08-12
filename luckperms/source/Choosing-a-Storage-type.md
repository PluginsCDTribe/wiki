LuckPerms 插件带有很多存储数据的方式，你可以从中选择。

存储类型选项可以在 `config.yml` 或 `luckperms.conf` 文件中修改。

```yaml
# Which storage method the plugin should use.
# Currently supported: mysql, postgresql, sqlite, h2, json, yaml, mongodb
# Fill out connection info below if you're using MySQL, PostgreSQL or MongoDB
storage-method: h2
```

请记住如果你想改变存储类型的话，你的数据不会自动转移到新的存储库中。  
要想手动在数据存储方式间转移数据的话，请查看[这里](//Switching-storage-types.md)来获得更多信息。

可用的选项都列在了下面。

## H2 / SQLite

默认的存储类型是 **H2**。

这两种文件类型都是以SQL数据库为基础的。  
所有的数据都会存储在LuckPerms插件目录下的一个文件之中。  
和YAML和JSON方式的不同之处在于，这个文件不能用文本编辑器打开。  
你必须使用插件提供的命令才能编辑或查看数据。

如果你选择使用 H2 数据库的话（默认设置），所有的数据都会储存在 `luckperms-h2.mv.db` 文件中。  
SQLite 类型所提供的存储文件是 `luckperms-sqlite.db`。

要想使用这两种类型中的一种，请将配置设置为：

```yaml
storage-method: h2
# or
storage-method: sqlite
```

## JSON / YAML

JSON 和 YAML 存储类型会将数据存储在可读可编辑的文本文件中。YAML 类型所提供的文件扩展名为 `.yml` ，JSON类型所提供的文件扩展名为 `.json`。

这两种类型的存储格式很相似，只是在一些句法上不同。

##### 示例 YAML 文件

```yml
uuid: c1d60c50-70b5-4722-8057-87767557e50d
name: Luck
primary-group: default
permissions:
- group.default:
    value: true
- test.permission:
    value: true
    server: factions
- other.test.permission:
    value: false
```

##### 示例 JSON 文件

```json
{
  "uuid": "c1d60c50-70b5-4722-8057-87767557e50d",
  "name": "Luck",
  "primaryGroup": "default",
  "permissions": [
    {
      "group.default": {
        "value": true
      }
    },
    {
      "test.permission": {
        "value": true,
        "server": "factions"
      }
    },
    {
      "other.test.permission": {
        "value": false,
        "server": "test"
      }
    }
  ]
}
```

要想使用这两种类型中的一种，请将配置设置为：

```yaml
storage-method: yaml
# or
storage-method: json
```

## MySQL / PostgreSQL

储存在 MySQL 类型和 PostgreSQL 类型中的数据格式上与上文提及的 H2/SQLite 类型相同，但是数据是储存在远程服务器上的。  
这意味着你可以跨服分享相同的数据。

你需要在配置文件中输入你数据库服务器的地址，端口，数据库名，用户名和密码。

这种类型推荐要存储大量数据的用户，或是想要搭建群组服务器的用户所使用。

如果你已经在运行群组服务器，并且想要在子服务器之间同步数据的话，你就必须选择这种类型了。

格式布局示例在[这里](https://github.com/lucko/LuckPerms/tree/master/common/src/main/resources)。

要想使用这两种选项中的一种，请将配置设置为：

```yaml
storage-method: mysql
# or
storage-method: postgresql
```

## MongoDB

LuckPerms 也支持 MongoDB 类型的存储，它也是一种远程数据库，在有些方面上和 MySQL 相似。  
这种类型也只会被一小部分的用户所使用。

要想使用这种类型的存储，请将配置设置为：

```yaml
storage-method: mongodb
```



