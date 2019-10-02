# 概览

本文件编辑 GUI 界面的样式。

# player-stats.yml 默认配置

```yaml
# GUI 显示名
name: 你的角色

# 背包槽位数量，需要是 9 的倍数，在 9 - 54 之间
slots: 54

items:
    mining-profession:
        slots: [10]
        function: profession_mining
        item: IRON_PICKAXE
        name: '&aMining'
        hide-attributes: true
        lore:
        - ''
        - '&7Current Level: &e{level}'
        - '&8[&e{progress}&8] &e{percent}%'
        - ''
        - '&7&oMining unlocks rare ores and raw materials.'
        - '&7&oThis is vital to your rise in power and strength,'
        - '&7&omine frequently for unique and rare drops.'
    woodcutting-profession:
        slots: [11]
        function: profession_woodcutting
        item: IRON_AXE
        name: '&aWoodcutting'
        hide-attributes: true
        lore:
        - ''
        - '&7Current Level: &e{level}'
        - '&8[&e{progress}&8] &e{percent}%'
        - ''
        - '&7&oThough it may seem like a boring task, woodcutting'
        - '&7&ois vital to obtaining materials used for crafting and trade,'
        - '&7&oand will help give you the upper hand in the arcane ways.'
    farming-profession:
        slots: [12]
        function: profession_farming
        item: IRON_HOE
        name: '&aFarming'
        hide-attributes: true
        lore:
        - ''
        - '&7Current Level: &e{level}'
        - '&8[&e{progress}&8] &e{percent}%'
        - ''
        - '&7&oWith tons of new food and consumable recipes,'
        - '&7&oyou will need to stay on top of the crops in order'
        - '&7&oto obtain the best food and drinks to keep yourself healthy.'
    fishing-profession:
        slots: [19]
        function: profession_fishing
        item: FISHING_ROD
        name: '&aFishing'
        hide-attributes: true
        lore:
        - ''
        - '&7Current Level: &e{level}'
        - '&8[&e{progress}&8] &e{percent}%'
        - ''
        - '&7&oFishing may give you unique drops you'
        - '&7&ocan''t find anywhere else. The more you'
        - '&7&ofish, the easier it becomes to find these.'
        - ''
        - '&7Fishing Strength: &c{fishing_strength}%'
        - '&7Crit Fishing Rate: &c{critical_fishing_chance}%'
        - '&7Crit Failure Rate: &c{critical_fishing_failure_chance}%'
    alchemy-profession:
        slots: [20]
        function: profession_alchemy
        item: BREWING_STAND
        name: '&aAlchemy'
        lore:
        - ''
        - '&7Current Level: &e{level}'
        - '&8[&e{progress}&8] &e{percent}%'
        - ''
        - '&7&oIn a world where you are no longer limited to'
        - '&7&osimple potions, try learning tons of new brewing'
        - '&7&orecipes to give yourself the edge on the battlefield.'
    smithing-profession:
        slots: [21]
        function: profession_smithing
        item: ANVIL
        name: '&aSmithing'
        lore:
        - ''
        - '&7Current Level: &e{level}'
        - '&8[&e{progress}&8] &e{percent}%'
        - ''
        - '&7&oStabbing enemies and having them laugh is the worst,'
        - '&7&oPractice makes perfect when it comes to smithing.'
        - '&7&o&nWar is won by the man with the pointiest stick.'
    smelting-profession:
        slots: [28]
        function: profession_smithing
        item: FURNACE
        name: '&aSmelting'
        lore:
        - ''
        - '&7Current Level: &e{level}'
        - '&8[&e{progress}&8] &e{percent}%'
        - ''
        - '&7&oSinging your eyebrows will become standard.'
        - '&7&oYour long hours over the heat will make you'
        - '&7&ofaster and more efficient with your oven.'
    boost-display:
        slots: [47,48,49,50,51]
        function: boost
        item: BARRIER
        no-boost:
            item: GRAY_STAINED_GLASS_PANE
            name: '&aNo Booster'
            lore: {}
        boost:
            item: EXPERIENCE_BOTTLE
            name: '&aEXP Boost'
            lore:
            - '&7Amount: &6+{value}%'
            - '&7Time left: &6{left}'
            - '&7'
            - '&eStarted by {author}'
    boost-next:
        slots: [52]
        function: boost-next
        item: PLAYER_HEAD
        texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMTliZjMyOTJlMTI2YTEwNWI1NGViYTcxM2FhMWIxNTJkNTQxYTFkODkzODgyOWM1NjM2NGQxNzhlZDIyYmYifX19
        name: '&aNext'
        lore: {}
    boost-prev:
        slots: [46]
        function: boost-previous
        item: PLAYER_HEAD
        texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYmQ2OWUwNmU1ZGFkZmQ4NGU1ZjNkMWMyMTA2M2YyNTUzYjJmYTk0NWVlMWQ0ZDcxNTJmZGM1NDI1YmMxMmE5In19fQ==
        name: '&aPrevious'
        lore: {}
    party:
        slots: [16]
        function: party
        item: CAKE
        name: '&aParty Morale'
        lore:
        - '&7&oPlaying with your friends'
        - '&7&ogreatly encourages you!'
        - ''
        - '&7Party Bonuses ({count}):'
        - '&8- +{exp}% Party EXP!'
        - '&8- +{regen}% Health Regeneration'
    stats:
        slots: [15]
        function: profile
        item: PLAYER_HEAD
        name: '&e{player}'
        lore:
        - ''
        - '&7Current Level: &e{level}'
        - '&7Progression: &e{exp} / {next_level}'
        - '&8[&e{progress}&8] &e{percent}%'
        - '&7Skill Points: &6{skill_points}'
        - ''
        - '&7Current Class: &c{class}'
        - '&7Class Points: &c{class_points}'
    phys:
        slots: [32]
        function: STATS
        name: '&8&lPhysical'
        item: GOLDEN_APPLE
        hide-attributes: true
        lore:
        - 'Attack Damage: &c{attack_damage} &7(&c{attack_damage_base}&7+&c{attack_damage_extra}&7)'
        - 'Attack Speed: &c{attack_speed} &7(&c{attack_speed_base}&7+&c{attack_speed_extra}&7)'
        - ''
        - 'Max Health: &c{max_health} &7(&c{max_health_base}&7+&c{max_health_extra}&7)'
        - 'Health Regen: &c{attack_speed} &7(&c{attack_speed_base}&7+&c{attack_speed_extra}&7)'
        - ''
        - 'Armor: &c{armor} &7(&c{armor_base}&7+&c{armor_extra}&7)'
        - 'Armor Toughness: &c{armor_toughness} &7(&c{armor_toughness_base}&7+&c{armor_toughness_extra}&7)'
    dex:
        slots: [33]
        function: STATS
        name: '&8&lDexterity'
        item: LEATHER_BOOTS
        hide-attributes: true
        lore:
        - 'Knockback Resistance: &f{knockback_resistance} &7(&f{knockback_resistance_base}&7+&f{knockback_resistance_extra}&7)'
        - 'Movement Speed: &f{movement_speed} &7(&f{movement_speed_base}&7+&f{movement_speed_extra}&7)'
        - 'Speed Malus Reduction: &f{speed_malus_reduction} &7(&f{speed_malus_reduction_base}&7+&f{speed_malus_reduction_extra}&7)'
    int:
        slots: [34]
        function: STATS
        name: '&8&lIntellect'
        item: BOOK
        hide-attributes: true
        lore:
        - 'Max Mana: &c{max_mana} &7(&c{max_mana_base}&7+&c{max_mana_extra}&7)'
        - 'Mana Regen: &c{mana_regeneration} &7(&c{mana_regeneration_base}&7+&c{mana_regeneration_extra}&7)'
        - ''
        - 'Max Stellium: &c{max_stellium} &7(&c{max_stellium_base}&7+&c{max_stellium_extra}&7)'
        - 'Stellium Regen: &c{stellium_regeneration} &7(&c{stellium_regeneration_base}&7+&c{stellium_regeneration_extra}&7)'
```