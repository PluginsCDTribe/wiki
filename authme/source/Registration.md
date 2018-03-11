AuthMe 支持不同类型的注册方式。你可以通过更改 config.yml 中的 `registration` 下面的 `type` 来更改注册方式。

## 密码注册
这是默认的注册方式： 用户通过使用 `/register` 来提供密码，该账户使用给定的密码来进行注册。

你可以在 config.yml 中的 `unsafePasswords` 禁用指定的密码，以及在 `minPasswordLength` 和 `passwordMaxLength` 中限制密码长度。

**例如：**
> 玩家 "Bobby" 使用了 `/register s3cret s3cret` -> AuthMe 则为 "Bobby" 进行注册，密码为 "s3cret"

## 电子邮箱注册
用户通过使用 `/register` 来提供邮箱，AuthMe 会为该帐户生成一个密码并通过电子邮件发送到指定的电子邮箱。

## 双重注册
:warning: **正在制作** -- 允许用户注册认证程序，即每次登录时都必须输入由应用程序生成的号码。