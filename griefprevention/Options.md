Options are a way to configure plugins using player/group contexts through your permission system, this gives you the benefit of being able to set different settings for different players, groups, worlds etc.

## Options Overview

Option                                           | Default Value | Description | 
-------------------------------------------------|---------------|--------------
```griefprevention.abandon-return-ratio-basic```       |   1.0         | The portion of basic claim blocks returned to a player when a basic claim is abandoned.
```griefprevention.abandon-return-ratio-town```       |   1.0         | The portion of town claim blocks returned to a player when a town claim is abandoned.
```griefprevention.blocks-accrued-per-hour```    |   120         | Blocks earned per hour. By default, each 'active' player should receive 6 blocks every 5 min. Note: The player must have moved at least 3 blocks since last delivery. If using 'wilderness-cuboids', this value is 30720 by default with 1536 blocks every 5 min to players.
```griefprevention.claim-create-mode```    | 0 | The default claiming mode set for players on login. (0 = 2D, 1 = 3D)
```griefprevention.create-claim-limit-basic```         |   20           | Maximum number of basic claims per player. (0 = unlimited)
```griefprevention.create-claim-limit-town```         |   1           | Maximum number of town claims per player. (0 = unlimited)
```griefprevention.create-claim-limit-subdivision```         |   10           | Maximum number of subdivisions per player. (0 = unlimited)
```griefprevention.initial-claim-blocks```       |   100         | The number of claim blocks a new player starts with. Note: If using 'wilderness-cuboids', this value is 25600 by default.
```griefprevention.max-accrued-claim-blocks```   |   80000       | The limit on accrued blocks (over time). doesn't limit purchased or admin-gifted blocks. Note: If using 'wilderness-cuboids', this value is 20480000 by default.
```griefprevention.claim-expiration-chest```     |   7           | Number of days of inactivity before an automatic chest claim will be deleted.
```griefprevention.claim-expiration-basic```    |   14          | Number of days of inactivity before a basic claim will be deleted.
```griefprevention.claim-expiration-town```     |   14           | Number of days of inactivity before a town claim will be deleted.
```griefprevention.claim-expiration-subdivision```     |   14           | Number of days of inactivity before a subdivision claim will be deleted.
```griefprevention.max-claim-size-basic-x```    |   5000          | The max size in blocks that the x-axis can be.
```griefprevention.max-claim-size-basic-y```    |   256          | The max size in blocks that the y-axis can be.
```griefprevention.max-claim-size-basic-z```    |   5000          | The max size in blocks that the z-axis can be.
```griefprevention.max-claim-size-town-x```    |   10000          | The max size in blocks that the x-axis can be.
```griefprevention.max-claim-size-town-y```    |   256          | The max size in blocks that the y-axis can be.
```griefprevention.max-claim-size-town-z```    |   10000          | The max size in blocks that the z-axis can be.
```griefprevention.max-claim-size-subdivision-x```    |   1000          | The max size in blocks that the x-axis can be.
```griefprevention.max-claim-size-subdivision-y```    |   256          | The max size in blocks that the y-axis can be.
```griefprevention.max-claim-size-subdivision-z```    |   1000          | The max size in blocks that the z-axis can be.

Note: Options are only set once during server startup. If you change it after startup you MUST run /gpreload for changes to work.

## Examples for different permission plugins

### LuckPerms

`/lp user/group <user|group> meta set <option> <value> [server] [world]`