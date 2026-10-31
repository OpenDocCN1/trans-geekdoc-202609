
TIME_FORMAT(time,format) (在示例中使用)
返回：字符串

## CURDATE

该函数返回今天的日期，其值格式为 YYYY-MM-DD 或 YYYYMMDD，具体取决于函数是在字符串还是数值上下文中使用。

```
CURDATE() or CURRENT_DATE (used in examples)
RETURNS: mixed
```

## CURTIME

该函数返回当前时间，其值格式为 HH:MM:SS 或 HHMMSS，具体取决于函数是在字符串还是数值上下文中使用。

```
CURTIME() or CURRENT_TIME
RETURNS: mixed
```

## NOW

该函数返回当前日期和时间，其值格式为 YYYY-MM-DD HH:MM:SS 或 YYYYMMDDHHMMSS，具体取决于函数是在字符串还是数值上下文中使用。

```
NOW()
```

或

```
SYSDATE()
```

或

```
CURRENT_TIMESTAMP (used in examples)
RETURNS: string
```

## UNIX_TIMESTAMP

如果该函数不带参数调用，则返回 Unix 时间戳（自 1970-01-01 00:00:00 GMT 以来的秒数）。如果带日期参数调用 UNIX_TIMESTAMP()，则返回该参数的值，自 1970-01-01 00:00:00 GMT 以来的秒数。date 可以是 DATE 字符串、DATETIME 字符串、TIMESTAMP，或本地时间格式为 YYMMDD 或 YYYYMMDD 的数字。

```
UNIX_TIMESTAMP([date])
RETURNS: int
```

## FROM_UNIXTIME

该函数返回 unix_timestamp 参数的表示形式，其值格式为 YYYY-MM-DD HH:MM:SS 或 YYYYMMDDHHMMSS，具体取决于函数是在字符串还是数值上下文中使用。

```
FROM_UNIXTIME(unix_timestamp) (used in examples)
RETURNS: string
```

## FROM_UNIXTIME

该函数返回 Unix 时间戳的字符串表示形式，根据格式字符串进行格式化。format 可以包含 DATE_FORMAT() 函数条目中列出的相同格式说明符。

```
FROM_UNIXTIME(unix_timestamp,format) (used in examples)
RETURNS: string
```

## SEC_TO_TIME

```
SEC_TO_TIME(seconds)
RETURNS: string
```

返回 seconds 参数，转换为小时、分钟和秒，其值格式为 HH:MM:SS 或 HHMMSS，具体取决于函数是在字符串还是数值上下文中使用。

## TIME_TO_SEC

```
TIME_TO_SEC(time) (used in examples)
RETURNS: int
```

该函数返回 time 参数，转换为秒。

## Miscellaneous Functions

以下是一些不属于前面任何类别的其他函数。

### Database

该函数返回当前数据库名称。如果没有当前数据库，DATABASE() 返回空字符串。

```
DATABASE()
RETURNS: string
```

### User

该函数返回当前 MySQL 用户名。在 MySQL 3.22.11 或更高版本中，这还包括客户端主机名以及用户名。

```
USER()
or
SYSTEM_USER()
or
SESSION_USER() (used in examples)
RETURNS: string
```

### VERSION

该函数返回一个字符串，表示 MySQL 服务器版本。

```
VERSION()
RETURNS: string
```

### PASSWORD

该函数根据明文密码 str 计算密码字符串。

```
PASSWORD(str) (used in examples)
RETURNS: string
```

这是用于将 MySQL 密码加密后存储在用户授权表的 Password 列中的函数。PASSWORD() 加密是单向的。PASSWORD() 的密码加密方式与 Unix 密码的加密方式不同。您不应假设如果您的 Unix 密码和 MySQL 密码相同，PASSWORD() 就会产生与存储在 Unix 密码文件中的加密值相同的加密值。参见 ENCRYPT()。

### ENCRYPT

该函数使用 Unix crypt() 系统调用加密 str。

```
ENCRYPT(str[,salt])
RETURNS: string
```

salt 参数应为包含两个字符的字符串。（从 MySQL 3.22.16 开始，salt 可以长于两个字符。）如果您的系统上不可用 crypt()，ENCRYPT() 始终返回 NULL。在大多数系统上，ENCRYPT() 仅忽略 str 的前八个字符之外的字符。

### ENCODE

该函数使用 pass_str 作为密码加密 str。

```
ENCODE(str,pass_str)
RETURNS: binary string
```

要解密结果，请使用 DECODE()。结果是一个二进制字符串。如果您想将其保存到列中，请使用 BLOB 列类型。

### DECODE

该函数使用 pass_str 作为密码解密加密字符串 crypt_str。crypt_str 应为从 ENCODE() 返回的字符串。

```
DECODE(crypt_str,pass_str)
RETURNS: string
```

### MD5

该函数为字符串计算 MD5 校验和。值以 32 个字符的字母数字字符串返回。这与 PHP 中使用的 md5() 函数相同。

```
MD5(string)
RETURNS: string
```

### LAST_INSERT_ID

该函数返回最后插入到 AUTO_INCREMENT 列中的自动生成值。

```
LAST_INSERT_ID()
RETURNS: int
```

### GET_LOCK

该函数尝试获取一个由字符串 str 指定的名称的锁，超时时间为 timeout 秒。如果成功获取锁则返回 1，如果尝试超时则返回 0，如果发生错误（如内存不足或线程被 mysqladmin kill 杀死）则返回 NULL。锁在执行 RELEASE_LOCK() 时、执行新的 GET_LOCK() 时或线程终止时释放。

```
GET_LOCK(str,timeout)
RETURNS: int
```

### RELEASE_LOCK

该函数释放由字符串 str 指定的、通过 GET_LOCK() 获取的锁。如果锁被释放则返回 1，如果锁不是由此线程锁定（在这种情况下锁不会被释放）则返回 0，如果指定的锁不存在则返回 NULL。

```
RELEASE_LOCK(str)
RETURNS: int
```

## Functions for Use with GROUP BY Clauses

大多数与 GROUP BY 子句一起使用的函数已在第 3 章中介绍过。这里还有两个我们当时没有介绍的附加函数。

### STD/STDDEV

该函数返回 expr 的标准差。它是 ANSI SQL 的扩展。提供 STDDEV() 形式是为了与 Oracle 兼容。

```
STD(expr)
```

或

```
STDDEV(expr)
RETURNS: float
```

### BIT_OR

该函数返回 expr 中所有位的按位 OR。计算以 64 位（BIGINT）精度执行。

```
BIT_OR(expr)
RETURNS: int
```

### BIT_AND

该函数返回 expr 中所有位的按位 AND。计算以 64 位（BIGINT）精度执行。

```
BIT_AND(expr)
RETURNS: int
```

## Appendix J

### What’s on the CD-ROM

要使第 III 部分和第 IV 部分的应用程序正常工作，您首先需要安装 Apache、PHP 和 MySQL。您可以在本书的 CD-ROM 上找到这些应用程序，位于 /apache、/php 和 /mysql 目录中。每个目录都有 Windows 和 Unix 的子目录。请使用合适的目录。然后按照附录 B 中的说明安装这些应用程序。

安装 Apache、PHP 和 MySQL 后，您需要复制加载数据库并运行应用程序的 PHP 脚本。将 CD 上的整个 /book 目录，连同其所有子文件夹，复制到 Apache 安装的 htdocs/ 目录中。

安装数据库的文件保存在 book/install/ 目录中。如果 Apache 在您的系统上运行，安装数据库所需做的全部工作就是在浏览器中打开正确的 URL：http://yourdomain/book/install/index.php。（如果 Apache 在本地机器上，实际 URL 很可能是 http://localhost/book/install/index.php）。

按照说明安装您希望使用的数据库。请注意，对于安装脚本，您需要在 install/index.php 文件的第四行 mysql_connect() 函数中输入有效的主机名、用户名和密码。然后，您可以通过访问 http://yourdomain/book/index.html/ 来访问所有应用程序。

然后您应打开 book/functions/db.php 文件。在第一个函数中，将 $user、$password 和 $server 参数更改为对您的 MySQL 安装有效的字符串。

CD 上还包含以下内容：

- 本书的 PDF 版本。
- Adobe Acrobat Reader 4.0。
- PHPmyadmin — 这个出色的实用程序通过使用 PHP 脚本的 Web 浏览器为 MySQL 提供图形用户界面。
- Manual Lemos' Form Creation and Validation Class — 这是一套非常完整的用于创建表单和验证表单输入的脚本。
- Manual Lemos' Database Abstraction Layer — 如果您需要从 PHP 脚本访问多个数据库，这会很有帮助。

