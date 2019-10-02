
## 安装MMOCore v1.0.6
你需要将下载好的jar文件拖到服务端的plugins文件夹中来安装 MMOCore 插件。当 MMOCore 与其他插件一同使用时，你需要遵循该插件提供的特定说明，以保证良好的兼容性。

## 关于MMOCore与MMOItems
**当你同时使用 MMOCore 与 MMOItems 时，你绝对不能再安装其他可以向 MMOItems 提供魔力与耐力属性的插件。(如Mana & Stamina)**。MMOCore 向 MMOItems 添加了很多新的属性值(详见 [MMOItems-Compatibility](MMOItems-Compatibility))。你需要在 MMOItems 的语言文件中添加几行以确保 MMOCore 能百分之百地兼容 MMOItems。将下面的代码加入到 /MMOItems/language/stats.yml 中:
```yaml
required-intelligence: '&eRequires # Intelligence'
required-strength: '&eRequires # Strength'
required-dexterity: '&eRequires # Dexterity'

max-stamina: '&7■ Max Stamina: &f<plus>#'
stamina-regen: '&7■ Stamina Regeneration: &f<plus>#'
mana-regen: '&7■ Mana Regeneration: &f<plus>#'
```

然后，你可以将下面几行代码加入到 MMOItems 物品的标签(lore)配置中。
```yaml
- '#required-intelligence#'
- '#required-strength#'
- '#required-dexterity#'
...
- '#mana-regen#'
- '#max-stamina#'
- '#stamina-regen#'
```

最后，将这行代码加入到 /MMOItems/language/messages.yml 中。不要忘记使用 **/mi reload** 指令重载插件。
```yaml
not-enough-attribute: 'You do not have enough #attribute#.'
```
