
秒。如果包含除小时、分钟和秒之外的格式说明符，该函数将返回 NULL 值。

```
TIME_FORMAT(time,format) (used in examples)
RETURNS: string
```

## CURDATE

此函数以 YYYY-MM-DD 或 YYYYMMDD 格式返回当前日期，具体取决于函数是在字符串上下文还是数值上下文中使用：

```
CURDATE() or CURRENT_DATE (used in examples)
RETURNS: mixed
```

## CURTIME

此函数以 HH:MM:SS 或 HHMMSS 格式返回当前时间，具体取决于函数是在字符串上下文还是数值上下文中使用：

```
CURTIME() or CURRENT_TIME
RETURNS: mixed
```

## NOW

此函数以 YYYY-MM-DD HH:MM:SS 或 YYYYMMDDHHMMSS 格式返回当前日期和时间，具体取决于函数是在字符串上下文还是数值上下文中使用：

```
NOW()
or
SYSDATE()
or
CURRENT_TIMESTAMP (used in examples)
RETURNS: string
```

## UNIX_TIMESTAMP

如果此函数不带参数调用，则返回 Unix 时间戳（自 1970-01-01 00:00:00 GMT 以来的秒数）。如果带 date 参数调用 UNIX_TIMESTAMP()，则返回该参数表示的自 1970-01-01 00:00:00 GMT 以来的秒数。date 可以是 DATE 字符串、DATETIME 字符串、TIMESTAMP，或是本地时间中格式为 YYMMDD 或 YYYYMMDD 的数字。

```
UNIX_TIMESTAMP([date])
RETURNS: int
```

## FROM_UNIXTIME

此函数将 unix_timestamp 参数表示为 "YYYY-MM-DD HH:MM:SS" 或 "YYYYMMDDHHMMSS" 格式的值，具体取决于函数是在字符串还是数值上下文中使用：

```
FROM_UNIXTIME(unix_timestamp) (used in examples)
RETURNS: string
```

## SEC_TO_TIME

此函数将 seconds 参数转换为小时、分钟和秒，并以 HH:MM:SS 或 HHMMSS 格式返回该值，具体取决于函数是在字符串还是数值上下文中使用：

```
SEC_TO_TIME(seconds)
RETURNS: string
```

## TIME_TO_SEC

此函数将 time 参数转换为秒并返回：

```
TIME_TO_SEC(time) (used in examples)
RETURNS: int
```

提供的日期/时间值的日期部分将被丢弃。

## 其他函数

以下是一些不属于前面任何类别的其他函数。

## DATABASE

此函数返回当前数据库名称。如果不存在当前数据库，DATABASE() 将返回空字符串。

```
DATABASE()
RETURNS: string
```

## USER

此函数返回当前 MySQL 用户名。在 MySQL 3.22.11 或更高版本中，它还包括客户端主机名。

```
USER()
```

或

```
SYSTEM_USER()
```

或

```
SESSION_USER() (used in examples)
```

返回：字符串

## VERSION

此函数返回一个指示 MySQL 服务器版本的字符串：

```
VERSION()
```

返回：字符串

## PASSWORD

此函数从纯文本密码 str 计算出密码字符串：

```
PASSWORD(str) (used in examples)
```

返回：字符串

此函数用于加密 MySQL 密码并将其存储在 user 表的 Password 列中。PASSWORD() 加密是单向的。PASSWORD() 的加密方式与 Unix 密码的加密方式不同。不应假设如果 Unix 密码和 MySQL 密码相同，PASSWORD() 会产生与 Unix 密码文件中存储的相同加密值。请参阅 ENCRYPT()。

## ENCRYPT

此函数使用 Unix crypt() 系统调用加密 str：

```
ENCRYPT(str[,salt])
```

返回：字符串

salt 参数应为包含两个字符的字符串。（从 MySQL 3.22.16 开始，salt 可以超过两个字符。）如果系统上不可用 crypt()，ENCRYPT() 始终返回 NULL。在大多数系统上，ENCRYPT() 只处理 str 的前八个字符，其余字符被忽略。

## ENCODE

此函数使用 pass_str 作为密码加密 str：

```
ENCODE(str,pass_str)
RETURNS: binary string
```

要解密结果，请使用 DECODE()。结果是一个二进制字符串。如果要将其保存到列中，请使用 BLOB 列类型。

## DECODE

此函数使用 pass_str 作为密码解密加密字符串 crypt_str。crypt_str 应为 ENCODE() 返回的字符串。

```
DECODE(crypt_str,pass_str)
RETURNS: string
```

## MD5

此函数为字符串计算 MD5 校验和。该值作为 32 个字符的字母数字字符串返回。这与 PHP 使用的 md5() 函数相同。

```
MD5(string)
RETURNS: string
```

## LAST_INSERT_ID

此函数返回最后插入到 AUTO_INCREMENT 列中的自动生成值：

```
LAST_INSERT_ID()
RETURNS: int
```

## GET_LOCK

此函数尝试获取名为字符串 str 的锁，超时时间为 timeout 秒。如果成功获取锁，则返回 1；如果尝试超时，则返回 0；如果发生错误（例如内存不足或线程被 mysqladmin kill 终止），则返回 NULL。锁会在释放锁、执行 RELEASE_LOCK()、执行新的 GET_LOCK() 或线程终止时释放。

```
GET_LOCK(str,timeout)
RETURNS: int
```

## RELEASE_LOCK

此函数释放通过 GET_LOCK() 获取的名为字符串 str 的锁。如果锁已释放，则返回 1；如果锁不是由当前线程加锁（在这种情况下锁不会被释放），则返回 0；如果指定的锁不存在，则返回 NULL。

```
RELEASE_LOCK(str)
RETURNS: int
```

## 与 GROUP BY 子句一起使用的函数

与 GROUP BY 子句一起使用的大多数函数在第 3 章中已介绍。还有三个额外的函数未在该章中介绍。

## STD/STDDEV

此函数返回 expr 的标准偏差。它是 ANSI SQL 的扩展。此函数的 STDDEV() 形式是为 Oracle 兼容性而提供的。

```
STD(expr)
```

或

```
STDDEV(expr)
RETURNS: float
```

## BIT_OR

此函数返回 expr 中所有位的按位 OR。计算以 64 位（BIGINT）精度执行。

```
BIT_OR(expr)
RETURNS: int
```

## BIT_AND

此函数返回 expr 中所有位的按位 AND。计算以 64 位（BIGINT）精度执行。

```
BIT_AND(expr)
RETURNS: int
```

## 索引

### 符号

- $（美元符号），91
- "（双引号），94
- =（等号），92
- #（空格字符），717
- ===（三重等号），93

### A

- 绝对路径，返回 (REALPATH())，175
- 绝对值，702
- 抽象类，212–215
- 访问键，568
- 操作，对象。另请参阅 方法
- 活动项目，显示，544–545
- 活动线程，查看，589–590
- 添加
  - 到数组开头 (ARRAY_UNSHIFT())，160
  - 列到表，42
  - 到数组末尾 (ARRAY_PUSH())，160
  - 自动添加文件，581–582
  - 索引到表，43
  - 调查问题 (admin/questions.php)，298–303
  - 用户到项目，545
- 地址簿，4
- 地址，文件或网页。另请参阅 URL
- 地址表，操作，490–491
- 管理任务，389–392, 586–587
- 别名 (as)，76
- 字母顺序
  - 数组 (SORT())，163
  - 表中条目列表，73
- 锚标记，671
- AND，按位 (BIT_AND)，734
- 异常，5, 8, 10
- 匿名用户，257
- Apache，109–111, 696
- 应用程序设计
  - 留言簿 2003，229–230
  - NuSOAP，527–528
  - 问题跟踪系统，441–444
  - 项目管理，537–541
  - 购物车，477–479
  - 调查，261–266, 294–298
  - 线程讨论，312–315
  - XML 解析，506–508
- 反余弦 (ACOS)，706
- 反正弦 (ASIN)，706
- 反正切 (ATAN)，706
- 两参数反正切 (ATAN2)，707
- 参数
  - 两参数反正切 (ATAN2)，707
  - 串联 (CONCAT)，711–712
  - 处理，HTML 调查函数，276–281
  - PHP 函数，134–135
  - 打印 (PRINT_INPUT_FIELDS())，249–250
  - 替换 (STR_REPLACE())，140
  - 脚本控制函数，获取信息 (func_get_arg(), func_get_args(), 和 func_num_args())，176–177
  - 字符串，输出然后终止脚本 (die())，176
  - 第一个值在第二个中找到 (IN_ARRAY())，159
  - 可变数量，205–206
- 数组
  - 添加到开头 (ARRAY_UNSHIFT())，160
  - 赋值，PHP 脚本，96–99
  - 关联数组，162, 671
  - 浏览器传递的变量，102–104
  - 公共元素 (ARRAY_INTERSECT())，159
  - 在字符串中串联 (JOIN())，154
  - 转换为变量 (COMPACT())，153
  - 计数 (ARRAY_COUNT())，157–158
  - 创建和填充 (RANGE())，154
  - 光标，重置 (RESET())，162
  - 描述，615–619
  - 差异 (ARRAY_DIFF())，159
  - 末尾，添加到 (ARRAY_PUSH())，160
  - 过滤 (ARRAY_FILTER())，157–158
  - 第一个元素，返回并移除 (ARRAY_SHIFT())，160
  - 键
    - 返回所有 (ARRAY_KEYS())，158
    - true/false 是否存在 (ARRAY_KEY_EXISTS())，158
  - 键/值对
    - 交换 (ARRAY_FLIP())，155–156
    - 提取并转换为独立变量 (EXTRACT())，153–154
