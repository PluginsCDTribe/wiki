## 哈希算法

AuthMe 支持以下用于安全存储密码的哈希算法。


| 算法           | 推荐            | 哈希长度 | ASCII |      | 加盐类型     | 长度   | 分离?  |
| ------------ | ------------- | ---- | ----- | ---- | -------- | ---- | ---- |
| ARGON2       | Recommended   | 96   |       |      | Text     | 16   |      |
| BCRYPT       | Recommended   | 60   |       |      | Text     |      |      |
| BCRYPT2Y     | Recommended   | 60   |       |      | Text     | 22   |      |
| CRAZYCRYPT1  | Do not use    | 128  |       |      | Username |      |      |
| IPB3         | Acceptable    | 32   |       |      | Text     | 5    | Y    |
| IPB4         | Does not work | 60   |       |      | Text     | 22   | Y    |
| JOOMLA       | Acceptable    | 65   |       |      | Text     | 32   |      |
| MD5VB        | Acceptable    | 56   |       |      | Text     | 16   |      |
| MYBB         | Acceptable    | 32   |       |      | Text     | 8    | Y    |
| PBKDF2       | Recommended   | 165  |       |      | Text     | 16   |      |
| PBKDF2DJANGO | Acceptable    | 77   | Y     |      | Text     | 12   |      |
| PHPBB        | Acceptable    | 60   |       |      | Text     | 22   |      |
| PHPFUSION    | Do not use    | 64   | Y     |      |          |      | Y    |
| ROYALAUTH    | Do not use    | 128  |       |      | None     |      |      |
| SALTED2MD5   | Acceptable    | 32   |       |      | Text     |      | Y    |
| SALTEDSHA512 | Recommended   | 128  |       |      |          |      | Y    |
| SHA256       | Recommended   | 86   |       |      | Text     | 16   |      |
| SMF          | Do not use    | 40   |       |      | Username |      | Y    |
| TWO_FACTOR   | Does not work | 16   |       |      | None     |      |      |
| WBB3         | Acceptable    | 40   |       |      | Text     | 40   | Y    |
| WBB4         | Recommended   | 60   |       |      | Text     | 8    |      |
| WORDPRESS    | Acceptable    | 34   |       |      | Text     | 9    |      |
| XAUTH        | Recommended   | 140  |       |      | Text     | 12   |      |
| XFBCRYPT     |               | 60   |       |      |          |      |      |
| CUSTOM       |               |      |       |      |          |      |      |



### 表格的各列

#### 算法

算法为存储密码是用的哈希算法。默认为 SHA256 并且推荐使用。
你可以在 config.yml 的 `security`, 位于 `passwordHash` 中更改使用的算法。

#### 推荐

推荐列出了我们对于这种算法的安全性的推荐（不是这种算法运行的怎么样）。
- Recommended: 这种哈希算法非常的安全，我们推荐使用。
- Acceptable: 有更好的哈希算法，但是选择这一个基本也可以。
- Deprecated: 现在或者不久的将来不能再使用。
- Do not use: 哈希算法不是足够的安全。请只在需要接入其他系统时使用。
- Does not work: 此算法不会正常工作；不要使用。

#### 哈希长度

算法生成的散列值的长度。注意不是越长越安全。

#### ASCII
如果为 Y，则说明此算法仅限于加密普通的 ASCII 字符，比如这种算法会忽略掉如 `ÿ` 或 `Â` 的特殊字符。注意我们不推荐在密码里使用「特殊字符」。

#### 加盐列

Before hashing, a _salt_ may be appended to the password to make the hash more secure. The following columns describe
the salt the algorithm uses.
<!-- AUTO-GENERATED FILE! Do not edit this directly -->

##### Salt Type
We do not recommend the usage
of any algorithm that doesn't use a randomly generated text as salt. This "salt type" column indicates what type of
salt the algorithm uses:
- Text: randomly generated text (see also the following column, "Length")
- Username: the salt is constructed from the username (bad)
- None: the algorithm uses no salt (bad)

##### Length
If applicable (salt type is "Text"), indicates the length of the generated salt. The longer the better.
If this column is empty when the salt type is "Text", it typically means the salt length can be defined in config.yml.

##### Separate
If denoted with a **y**, it means that the salt is stored in a separate column in the database. This is neither good
or bad.

