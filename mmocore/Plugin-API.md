## 玩家API

玩家数据被保存在 `PlayerData`实例中，可以使用该类的静态方法 `PlayerData#get(UUID/Player)` 操作和访问玩家数据。你可以修改玩家的种族、等级、组队、技能数据、任务数据等等。玩家数据在玩家加入游戏时加载，事件优先级为正常。

## 伤害API

有时候插件无法区分近战攻击和技能攻击，但是一些MMOCore技能只能触发近战或魔法伤害。因此，对于任何会对实体造成伤害的插件来说，告诉MMOCore这是什么类型的伤害是很重要的。伤害监听通过 _DamageHandler_'s 完成。_DamageHandler_ 接口有两个方法可以覆盖，分别是 `isCustomDamaged(Entity)` 和 `getCustomDamage(Entity)`。如果如果对实体造成伤害使用的是插件自定义的伤害体系。

那么 `isCustomDamaged(Entity)` 方法应该返回。此方法在 _EntityDamageByEntityEvent_ 中调用，因此在事件被触发前，有关自定义伤害的信息必须已被保存。

`getCustomDamage(Entity)` 应该返回有关自定义伤害的信息，该信息存储在 _DamageInfo_ 实例中。_DamageInfo_ 实例包含两个不同的信息:**伤害类型(物理、魔法或武器)**和**伤害量**。你可以使用这个构造函数 `new DamageInfo(DamageType, Double)` 来构建一个新的 _DamageInfo_ 实例。

---

任何`Damageable#damage(double, Entity)`方法在调用时都会触发一个EntityDamageByEntityEvent，因此你**必须**在使用此方法之前保存伤害信息。MMOCore和MMOItems都使用 _DamagerManager_ 将自定义损坏信息存储在HashMap中，实体id作为key，DamageInfo实例作为value。当触发EntityDamageByEntityEvent时，在事件优先级监视器上自动清除此映射，以便在清除信息之前运行所有检查。HeroesAPI对魔法目标使用了类似的原理。

一旦设置了 _DamageHandler_ 实例，就必须在MMOCore中注册它。要做到这一点，只需在你的插件启用时调用这个方法:  `mmocore.plugin.damagehandler.add(yourDamageHandler)`。此方法将你的damageHandler添加到保存了DamageHandler的List中

每次MMOCore监听到一个伤害事件时，它都会遍历DamageHandlerList，并试图找到负责处理自定义伤害的插件。如果它不能找到任何符合条件的DamageHandler，**攻击将被视为武器攻击**。

## 添加额外的任务条件/触发器/自定义掉落物品表/条件

为了提高与其他自定义掉落物品表或任务插件的兼容性，你可能需要注册额外的选项，如自定义掉落物品表、条件或任务条件/触发器

使用 _MMOLoader_ 实例加载这些选项。MMOCore拥有的加载器越多，它能够识别的选项就越多(就像MythicMobs中的技能机制或自定义掉落物品表一样)。首先，你需要创建你的MMOLoader，使它加载任何额外的选项。例如，这里是默认的MMOLoader:

```java
    @Override
    public Trigger loadTrigger(MMOLineConfig config) {
        if (config.getKey().equals("message"))
            return new MessageTrigger(config);

        if (config.getKey().equals("sound"))
            return new SoundTrigger(config);

        if (config.getKey().equals("command"))
            return new CommandTrigger(config);

        if (config.getKey().equals("item"))
            return new ItemTrigger(config);

        if (config.getKey().equals("exp"))
            return new ExperienceTrigger(config);

        return null;
    }

    @Override
    public DropItem loadDropItem(MMOLineConfig config, DropTableManager tables) {
        if (config.getKey().equals("droptable"))
            return new DropTableDropItem(tables, config);

        if (config.getKey().equals("vanilla"))
            return new VanillaDropItem(config);

        if (config.getKey().equals("note"))
            return new NoteDropItem(config);

        if (config.getKey().equals("gold"))
            return new GoldDropItem(config);

        return null;
    }

    @Override
    public Objective loadObjective(MMOLineConfig config, ConfigurationSection section) {
        if (config.getKey().equals("goto"))
            return new GoToObjective(section, config);

        if (config.getKey().equals("mine"))
            return new MineBlockObjective(section, config);

        if (config.getKey().equals("kill"))
            return new KillMobObjective(section, config);

        if (config.getKey().equals("getitem"))
            return new GetItemObjective(section, config);

        if (config.getKey().equals("clickon"))
            return new ClickonObjective(section, config);

        return null;
    }

    @Override
    public Condition loadCondition(MMOLineConfig config) {
        // TODO Auto-generated method stub
        return null;
    }
```

可以看到，对于每个选项类型(触发器/条件/自定义掉落物品表…)，必须覆盖MMOLoader实例中的一个对应的方法。每个方法都会返回一个对象，该对象允许你获取像 `vanilla{type=DIAMOND} 0.5 1-3` 这样的格式来配置信息(类似于MythicMobs API)。

创建好MMOLoader后，你需要使用“MMOCore.plugin.loadmanager.registerloader (yourMMOLoader)”在MMOCore中注册它。请确保在 **MMOCore加载** 之前注册它。要么让你的插件在MMOItems之前加载，并在它启用时注册它，要么不要冒任何涉及加载顺序问题的风险，即不要在MMOCore加载后，又在你的插件**加载**时注册它。