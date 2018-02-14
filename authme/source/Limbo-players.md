### Introduction
Before a player is logged in, we put the player in what we call a _limbo_ state. In this limbo state, we remove various permissions from the user before he is logged in for security:

- OP status (removed)
- ability to fly (removed)
- walk speed*
- fly speed*

\* Removed only if unauthenticated players may not move (`settings.restrictions.allowMovement`).

### Implementation
To remove properties from unauthenticated players only temporarily, we need to ensure that we keep the values for when the player logs in. We store this data as a so-called _limbo player_. This is an object that contains the _limbo properties_ we've removed, i.e. OP status, flight ability, walk speed, and fly speed.

A typical chain of events is:
1. player joins
1. we create a limbo player and remove _limbo properties_ such as OP status
1. player logs in
1. we add back all properties from the limbo player to the now authenticated player

### Timing / overriding issues
One issue with this handling is that if things are changed for an unauthenticated player, we will override the new changes with the limbo player once he logs in. So a player who is set to be allowed to fly will no longer be able to fly after he logs in.

Consider the following example:
1. player joins with walk speed 5
1. we create a limbo player (keep walk speed = 5 in limbo player, set walk speed 0 on player)
1. an admin sets walk speed 10 on the player
1. player logs in
1. we restore limbo properties -> player has walk speed 5 again

We try to combat such issues by allowing you to configure how we should restore the limbo properties. You can find these settings in your config.yml under "limbo". For example, you may choose to keep the maximum speed from player and limbo player, or you can define to set "allow flight" always to _true_ when a player logs in.

Note that restoring the OP status is not configurable. For security reasons, if an unregistered player is OP, he will no longer be OP once he registers & logs in. Similarly, an unregistered player who gets opped will no longer be OP when he logs in. In order to set someone as OP successfully, he needs to be authenticated.

### Persistence (saving to the file system)
If your server crashes, we may not get the chance to restore the properties we've removed from the player. So after restarting a crashed server, it may happen that a player will have walk speed 0.

To combat this, we store limbo players in the file system. So what we actually do is this:
1. player joins
1. we create a limbo player and remove the limbo properties from the player
    * we keep the limbo player in memory, as well as in a file on the file system
1. player logs in
1. we restore the limbo properties
    * remove limbo player from memory, delete file

The file is a backup so that this data is somewhere outside of memory, in case the server crashes. In config.yml, under `limbo`, you can configure if and how limbo players should be saved. We offer individual files, one huge file, or the possibility to distribute the data over a configurable number of files.

