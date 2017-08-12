我编写这部分WIKI内容的目的是为了帮助用户们适应从GM/PEX到LuckPerm的转变，
这里我制作了一份对应等效指令的表格，方便用户随时查阅。

## Group Manager
| Group Manager 命令                         | LuckPerms 命令                                            |
|--------------------------------------------|-----------------------------------------------------------|
| manuadd \<玩家\> \<组\>               | lp user \<玩家\> parent set \<组\>                   |
| manudel \<玩家\>                         | lp user \<玩家\> clear                                  |
| manuaddsub \<玩家\> \<组\>            | lp user \<玩家\> parent add \<组\>                   |
| manudelsub \<玩家\> \<组\>            | lp user \<玩家\> parent remove \<组\>                |
| manpromote \<玩家\> \<组\>            | lp user \<玩家\> promote \<track\>                      |
| mandemote \<玩家\> \<组\>             | lp user \<玩家\> demote \<track\>                       |
| manwhois \<玩家\>                        | lp user \<玩家\> info                                   |
| manuaddp \<玩家\> \<权限\>         | lp user \<玩家\> permission set \<权限\> true     |
| manudelp \<玩家\> \<权限\>         | lp user \<玩家\> permission unset \<权限\>        |
| manulistp \<玩家\>                       | lp user \<玩家\> permission info                        |
| manucheckp \<玩家\> \<权限\>       | lp user \<玩家\> haspermission \<权限\>           |
| manuaddv \<玩家\> prefix \<值\>       | lp user \<玩家\> meta addprefix \<优先级\> \<值\>  |
| manuaddv \<玩家\> suffix \<值\>       | lp user \<玩家\> meta addsuffix \<优先级\> \<值\>  |
| manuaddv \<玩家\> \<变量\> \<值\> | lp user \<玩家\> meta set \<变量\> \<值\>        |
| manudelv \<玩家\> \<变量\>           | lp user \<玩家\> meta unset \<变量\>                |
| manulistv \<玩家\>                       | lp user \<玩家\> meta info                              |
|                                            |                                                           |
| mangadd \<组\>                          | lp creategroup \<组\>                                  |
| mangdel \<组\>                          | lp deletegroup \<组\>                                  |
| mangaddi \<组1\> \<组2\>             | lp group \<组1\> parent add \<组2\>                 |
| mangdeli \<组1\> \<组2\>             | lp group \<组1\> parent remove \<组2\>              |
| listgroups                                 | lp listgroups                                             |
| mangaddp \<组\> \<权限\>          | lp group \<组\> permission set \<权限\> true     |
| mangdelp \<组\> \<权限\>          | lp group \<组\> permission unset \<权限\>        |
| manglistp \<组\>                        | lp group \<组\> permission info                        |
| mangcheckp \<组\> \<权限\>        | lp group \<组\> haspermission \<权限\>           |
| mangaddv \<玩家\> prefix \<值\>       | lp group \<组\> meta addprefix \<优先级\> \<值\>  |
| mangaddv \<玩家\> suffix \<值\>       | lp group \<组\> meta addsuffix \<优先级\> \<值\>  |
| mangaddv \<玩家\> \<变量\> \<值\> | lp group \<组\> meta set \<变量\> \<值\>        |
| mangdelv \<玩家\> \<变量\>           | lp group \<组\> meta unset \<变量\>                |
| manglistv \<玩家\>                       | lp group \<组\> meta info                              |
|                                            |                                                           |
| mansave                                    | lp sync                                                   |
| manload                                    | lp sync                                                   |


# PermissionsEx
| PermissionsEx 命令                                                  | LuckPerms 命令                                                                  |
|---------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| pex                                                                 | lp                                                                                  |
| pex reload                                                          | lp sync                                                                             |
| pex toggle debug                                                    | lp verbose true                                                                     |
| pex user \<用户\> check \<权限\>                              | lp user \<用户\> haspermission \<权限\>                                       |
| pex backend                                                         | lp info                                                                             |
| pex import \<backend\>                                              | lp export \<file\> / lp import \<file\>                                             |
| pex set default group \<组\>                                     | (in the config file)                                                                |
|                                                                     |                                                                                     |
| pex user \<用户\> list                                              | lp user \<用户\> permission info                                                    |
| pex user \<用户\> prefix                                            | lp user \<用户\> meta info                                                          |
| pex user \<用户\> prefix \<前缀\>                                 | lp user \<用户\> meta addprefix \<优先级\> \<前缀\>                             |
| pex user \<用户\> suffix                                            | lp user \<用户\> meta info                                                          |
| pex user \<用户\> suffix \<后缀\>                                 | lp user \<用户\> meta addsuffix \<优先级\> \<后缀\>                             |
| pex user \<用户\> delete                                            | lp user \<用户\> clear                                                              |
| pex user \<用户\> add \<权限\> \<世界\>                      | lp user \<用户\> permission set \<权限\> true global \<世界\>                |
| pex user \<用户\> remove \<权限\> \<世界\>                   | lp user \<用户\> permission unset \<权限\> global \<世界\>                   |
| pex user \<用户\> timed add \<权限\> \<时间\> \<世界\>       | lp user \<用户\> permission settemp \<权限\> true \<时间\> global \<世界\>   |
| pex user \<用户\> timed remove \<权限\> \<时间\> \<世界\>    | lp user \<用户\> permission settemp \<权限\> true \<时间\> global \<世界\>   |
| pex user \<用户\> set \<option\> \<值\> \<世界\>                | lp user \<用户\> meta set \<option\> \<值\> global \<世界\>                     |
|                                                                     |                                                                                     |
| pex user \<用户\> group list                                        | lp user \<用户\> parent info                                                        |
| pex user \<用户\> group add \<组\> \<世界\>                     | lp user \<用户\> parent add \<组\> global \<世界\>                              |
| pex user \<用户\> group add \<组\> \<世界\> \<时间\>            | lp user \<用户\> parent addtemp \<组\> \<时间\> global \<世界\>                 |
| pex user \<用户\> group set \<组\>                               | lp user \<用户\> parent set \<组\>               |
| pex user \<用户\> group remove \<组\> \<世界\>                  | lp user \<用户\> parent remove \<组\> global \<世界\>                           |
| pex groups list                                                     | lp listgroups                                                                       |
| pex group \<组\> list                                            | lp group \<组\> permission info                                                  |
| pex group \<组\> prefix                                          | lp group \<组\> meta info                                                        |
| pex group \<组\> prefix \<前缀\>                               | lp group \<组\> meta addprefix \<优先级\> \<前缀\>                           |
| pex group \<组\> suffix                                          | lp group \<组\> meta info                                                        |
| pex group \<组\> suffix \<后缀\>                               | lp group \<组\> meta addsuffix \<优先级\> \<后缀\>                           |
| pex group \<组\> create                                          | lp creategroup \<组\>                                                            |
| pex group \<组\> delete                                          | lp deletegroup \<组\>                                                            |
| pex group \<组\> parents list                                    | lp group \<组\> parent info                                                      |
| pex group \<组\> parents set \<parents\>                         | lp group \<组\> parent add \<parent\>                                            |
| pex group \<组\> add \<权限\> \<世界\>                    | lp group \<组\> permission set \<权限\> true global \<世界\>              |
| pex group \<组\> remove \<权限\> \<世界\>                 | lp group \<组\> permission unset \<权限\> global \<世界\>                 |
| pex group \<组\> timed add \<权限\> \<时间\> \<世界\>     | lp group \<组\> permission settemp \<权限\> true \<时间\> global \<世界\> |
| pex group \<组\> timed remove \<权限\> \<时间\> \<世界\>  | lp group \<组\> permission settemp \<权限\> true \<时间\> global \<世界\> |
| pex group \<组\> set \<option\> \<值\> \<世界\>              | lp group \<组\> meta set \<option\> \<值\> global \<世界\>                   |
|                                                                     |                                                                                     |
| pex group \<组\> user add \<用户\>                               | lp user \<用户\> parent add \<组\>                                               |
| pex group \<组\> user remove \<用户\>                            | lp user \<用户\> parent remove \<组\>                                            |
| pex promote \<用户\> \<ladder\>                                     | lp user \<用户\> promote \<ladder\>                                                 |
| pex demote \<用户\> \<ladder\>                                      | lp user \<用户\> demote \<ladder\>                                                  |



