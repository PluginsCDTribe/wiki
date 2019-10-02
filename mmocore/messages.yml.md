# 概览

messages.yml 是插件的主语言文件，这里你可以更改几乎所有消息。

确保如原来一样填写了每个值，如果你想正确显示什么东西的话。

# 默认配置

```yaml
# Level & Experience
level-up:
- ''
- '&eCongratulations, you reached level &6{level}&e!'
- '&eUse &6/p &eto see your new statistics!'
- ''
profession-level-up:
- '&eYou are now level &6{level}&e in &6{profession}&e!'
exp-notification: '&f{profession} &e{progress} &e{ratio}%'
exp-hologram: '&e+{exp} EXP!'

# General
booster-main:
- '&e'
- '&eAn &6{multiplier}x&e EXP multiplier is now active!'
- '&e'
booster-skill:
- '&e'
- '&eAn &6{multiplier}x&e &6{profession} &eEXP multiplier is now active!'
- '&e'

# Fishing Profession
caught-fish: '&cYou caught a fish!'
fish-out-water: '&aWell done!'
fish-out-water-crit: '&aCritical Fish!'

# Spell Casting
casting:
    action-bar: '&6[{index}] &a&l{skill}'
    split: '&7 &7 - &7 '
    no-longer: '&cYou cancelled skill casting.'

# Combat Log
now-in-combat: '&cYou are now in combat!'
leave-combat: '&aYou left combat.'

# Waypoints
new-waypoint: '&eYou unlocked the &6{waypoint} &ewaypoint!'
not-enough-stellium: '&cYou don''t have enough stellium: you need {more} more.'
waypoint-cooldown: '&cPlease wait {cooldown} before using a waypoint again.'
not-unlocked-waypoint: '&cYou have not unlocked that waypoint yet.'
standing-on-waypoint: '&cYou are already standing on this waypoint.'
warping-canceled: '&cWaypoint warping canceled.'
warping-comencing: '&cDO NOT MOVE!&e You will be warped in {left}sec.'

# Cash
deposit: '&eYou successfully deposited &6{worth}g&e.'
withdrawing: '&eType in the chat the amount of &6gold&e you want to &6withdraw&e.'
withdraw-cancel: '&eWithdrawing canceled.'
withdrew: '&eYou successfully withdrew &6{worth}g&e.'
wrong-number: '&c{arg} is not a valid number.'
not-enough-money: '&cYou don''t have enough money, you need {left} more gold.'
stand-near-enderchest: '&cYou must be standing near a bank to do that.'

# Blocks
cannot-break: '&cYou do not have the right tool in order to break that block.'

# Friends
no-longer-friends: '&cYou and {unfriend} are no longer friends.'
not-online-player: '&c{player} is not online.'
sent-friend-request: '&eYou sent a friend request to &6{player}&e.'
now-friends: '&eYou are now friends with &6{player}&e.'
friend-request-cooldown: '&cPlease wait {cooldown}.'
cant-request-to-yourself: '&cYou can''t send a request to yourself.'
already-friends: '&cYou are already friends with {player}.'
friend-request:
- '{"text":""}'
- '{"text":"&6{player} &ejust sent you a friend request!"}'
- '[{"text":"        ","hoverEvent":{}},{"text":"&8[&a&lACCEPT&8]","clickEvent":{"action":"run_command","value":"/friends accept {uuid}"},"hoverEvent":{"action":"show_text","value":"&eClick to accept!"}},{"text":"&r             ","hoverEvent":{}},{"text":"&8[&c&lDENY&8]","clickEvent":{"action":"run_command","value":"/friends deny {uuid}"},"hoverEvent":{"action":"show_text","value":"&eClick to deny."}}]'
- '{"text":""}'

# Parties
sent-party-invite: '&eYou sent a party invite to &6{player}&e.'
already-in-party: '&c{player} is already in your party.'
party-invite:
- '{"text":""}'
- '{"text":"&6{player} &ehas invited you to their party!"}'
- '[{"text":"        ","hoverEvent":{}},{"text":"&8[&a&lACCEPT&8]","clickEvent":{"action":"run_command","value":"/party accept {uuid}"},"hoverEvent":{"action":"show_text","value":"&eClick to accept!"}},{"text":"&r             ","hoverEvent":{}},{"text":"&8[&c&lDENY&8]","clickEvent":{"action":"run_command","value":"/party deny {uuid}"},"hoverEvent":{"action":"show_text","value":"&eClick to deny."}}]'
- '{"text":""}'
party-is-full: '&cSorry, your party is full.'
party-joined: '&eYou successfully joined &6{owner}&e''s party.'
party-joined-other: '&6{player}&e joined your party!'
transfer-party-ownership: '&eYou were transfered the party ownership.'
kick-from-party: '&eYou successfully kicked &6{player}&e.'
party-invite-cooldown: '&cPlease wait {cooldown} before inviting {player}.'

# Quests
already-on-quest: '&cYou are already on a quest.'
cancel-quest: '&eYou successfully canceled your ongoing quest.'
quest-level-restriction: '&cYou need to be {level} {count}.'
cant-redo-quest: '&cYou can''t start this quest twice.'
quest-cooldown: '&cYou need to wait {delay}.'
start-quest: '&eYou successfully started &6{quest}&e.'

cant-choose-new-class:
- '&cYou need one class point to perform this action.'

tool-lore:
- '&7Durability: {durability} / {max_durability}'
- ''
- '&7Level {level}'
- '&7Experience: {exp} / {needed_exp}'
- '&8[&e{exp_progress}&8] &e{percent}%'
- ''
- '{enchants}'

# Skills
skill:
    unlock-format:
        true: '&a✔ Requires Level {level}'
        false: '&c✖ Requires Level {level}'
not-enough-skill-points: '&cYou need one skill point.'
upgrade-skill: '&eYour &6{skill} &eis now Level &6{level}&e!'
not-unlocked-skill: '&cYou have not unlocked that skill yet.'
no-skill-bound: '&cYou don''t have any skill bound to this slot.'
not-active-skill: '&cThis is not an active skill.'

```