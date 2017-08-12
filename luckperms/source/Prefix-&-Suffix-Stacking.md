### 这个功能能做什么？
“元数据堆叠”特性能够让你在玩家聊天中同时展示多个前缀或后缀。

你仍需要安装聊天管理类型的插件。

### 它怎么工作？
当聊天管理类插件请求要获取玩家的前缀或后缀时，取代返回玩家最高优先级的称号，LuckPerms能够应用一些你设定的规则来一起输出多个前缀或后缀。

默认的设置看起来是这样：
```yml
meta-formatting:
  prefix:
    format:
      - "highest"
    start-spacer: ""
    middle-spacer: " "
    end-spacer: ""
  suffix:
    format:
      - "highest"
    start-spacer: ""
    middle-spacer: " "
    end-spacer: ""
```

这些当前配置意味着，当请求前缀或后缀的时候，会返回最高优先级的那一个。

### 我怎么增加其他元素？
当前支持以下元素。

| 元素 | 描述 |
|---------|-------------|
| `highest` | 从玩家拥有或继承的数据中选择最高优先级的值 |
| `lowest` | 和上面的工作原理相同，但是它会选择最低优先级的值 |
| `highest_own` | 选择最高优先级的值，但不支持继承来的值 |
| `lowest_own` | 和上面的工作原理相同，但是它会选择最低优先级的值 |
| `highest_on_track_<track>` | 选择继承于给予的权限组路线中的权限组所提供的最高优先级的值 |
| `lowest_on_track_<track>` | 和上面的工作原理相同，但是它会选择最低优先级的值 |
| `highest_not_on_track_<track>` | 选择不继承于给予的权限组路线中的权限组所提供的最高优先级的值 |
| `lowest_not_on_track_<track>` | 和上面的工作原理相同，但是它会选择最低优先级的值 |

### 一个示例
例如，在一个监狱服务器中，你可能有3种类型的权限组，一种是玩家“gameplay”权限组，一种是赞助商权限组，一种是管理员权限组。

如果玩家在三个组中，我想要展示三个前缀，举个例子：
`[Mine C] [Donor] [Admin] Luck: hi!`.

但是如果玩家不在管理员权限组中，我想展示：
`[Mine C] [Donor] Luck: hi`.

使用堆叠系统这些都可以实现。每个堆叠中的“元素”都需要添加到格式节内。

```yml
prefix:
  format:
    - "highest_on_track_prison"
    - "highest_on_track_donor"
    - "highest_on_track_staff"
  start-spacer: ""
  middle-spacer: " "
  end-spacer: ""
```

如果玩家在该元素中没有对应的值的话，它就会被堆叠系统自动无视。

你可以控制每个元素在开头，中间和结尾的分隔符，举个例子：

  ```yml
  prefix:
    format:
      - "highest_on_track_prison"
      - "highest_on_track_donor"
      - "highest_on_track_staff"
    start-spacer: "★ "
    middle-spacer: " | "
    end-spacer: " "
  ```

... 这样的聊天结果会是：
`★ [Mine C] | [Donor] | [Admin] Luck: hi`.

显然你可以使用你的聊天管理插件来改变这些值，那些插件也会提供相似的选项。
