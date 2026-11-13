

此外，请妥善处理所有错误，并将所有跟踪消息定向到系统日志文件，以便如果发生任何问题，则问题将被记录到系统日志文件中，您将能够调试该问题。

## 25. PHP – 日期和时间

日期是日常生活中如此重要的一部分，以至于人们在处理日期时往往不加思考。PHP 还提供了强大的日期运算工具，使日期操作变得轻松。

### 使用 time() 获取时间戳

PHP 的 time() 函数会提供您关于当前日期和时间所需的所有信息。它不需要任何参数，但会返回一个整数。

time() 返回的整数表示自 1970 年 1 月 1 日格林威治标准时间午夜以来经过的秒数。这一时刻被称为 UNIX 纪元，自那时起经过的秒数称为时间戳。

```php
<?php
print time();
?>
```

它将产生以下结果：

![](img/b9c80e155ac304a53696823920b08082_137_0.png)

这很难理解。但 PHP 提供了出色的工具，可将时间戳转换为人类易于理解的形式。

### 使用 getdate() 转换时间戳

函数 getdate() 可选地接受一个时间戳，并返回一个包含日期信息的关联数组。如果省略时间戳，它将使用 time() 返回的当前时间戳。

下表列出了 getdate() 返回的数组中包含的元素。

| 键 | 描述 | 示例 |
|---|---|---|
| seconds | 分钟过去的秒数 (0-59) | 20 |
| minutes | 小时过去的分钟数 (0 - 59) | 29 |
| hours | 一天中的小时数 (0 - 23) | 22 |
| mday | 一个月中的日期 (1 - 31) | 11 |
| wday | 一周中的星期数 (0 - 6) | 4 |
| mon | 一年中的月份 (1 - 12) | 7 |
| year | 年份 (4 位数字) | 1997 |
| yday | 一年中的天数 (0 - 365) | 19 |
| weekday | 星期 | 星期四 |
| month | 一年中的月份 | 一月 |
| 0 | 时间戳 | 948370048 |

现在您对日期和时间有完全的控制权。您可以按想要的任何格式来格式化此日期和时间。

### 示例

尝试以下示例。

```php
<?php
$date_array = getdate();
foreach ( $date_array as $key => $val )
{
   print "$key = $val<br />";
}

$formatted_date = "Today's date: ";
$formatted_date .= $date_array[mday] . "/";
$formatted_date .= $date_array[mon] . "/";
$formatted_date .= $date_array[year];

print $formatted_date;
?>
```

它将产生以下结果：

```
seconds = 6
minutes = 15
hours = 11
mday = 19
wday = 2
mon = 7
year = 2016
yday = 200
weekday = Tuesday
month = July
0 = 1468926906
Today's date: 19/7/2016
```

### 使用 date() 转换时间戳

**date()** 函数返回一个表示日期的格式化字符串。您可以通过必须传递给它的字符串参数，对 date() 返回的格式进行大量控制。

```
date(format,timestamp)
```

date() 可选地接受一个时间戳，如果省略，则将使用当前日期和时间。您在传递给 date() 的格式字符串中包含的任何其他数据都将包含在返回值中。

下表列出了格式字符串可以包含的代码：

| 格式 | 描述 | 示例 |
|---|---|---|
| a | 'am' 或 'pm' 小写 | 下午 |
| A | 'AM' 或 'PM' 大写 | 下午 |
| d | 带前导零的月份中的天数 | 20 |
| D | 星期几 (三个字母) | 星期四 |
| F | 月份名称 | 一月 |
| h | 小时 (12 小时格式 - 带前导零) | 12 |
| H | 小时 (24 小时格式 - 带前导零) | 22 |
| g | 小时 (12 小时格式 - 不带前导零) | 12 |
| G | 小时 (24 小时格式 - 不带前导零) | 22 |
| i | 分钟 (0 - 59) | 23 |
| j | 月份中的日期 (不带前导零) | 20 |
| l (Lower 'L') | 星期 | 星期四 |
| L | 闰年 ('1' 表示是，'0' 表示否) | 1 |
| m | 一年中的月份 (数字 - 带前导零) | 1 |
| M | 一年中的月份 (三个字母) | 一月 |
| r | RFC 2822 格式的日期 | 星期四, 21 十二月 2000 16:01:07 +0200 |
| n | 一年中的月份 (数字 - 不带前导零) | 2 |
| s | 小时中的秒数 | 20 |
| U | 时间戳 | 948372444 |
| y | 年份 (两位数字) | 06 |
| Y | 年份 (四位数字) | 2006 |
| z | 一年中的天数 (0 - 365) | 206 |
| Z | 相对于 GMT 的秒偏移量 | +5 |

### 示例

尝试以下示例。

```php
<?php
print date("m/d/y G.i:s<br>", time());
print "Today is ";
print date("j of F Y, \\a\\t g.i a", time());
?>
```

它将产生以下结果：

07/19/16 11.15:06今天是 2016 年 7 月 19 日，上午 11:15

希望您已了解如何根据需求格式化日期和时间。作为参考，所有日期和时间函数的完整列表载于 PHP 日期和时间函数中。

## 26. PHP – PHP 和 MySQL

PHP 可与几乎所有数据库软件协作，包括 Oracle 和 Sybase，但最常用的是免费可用的 MySQL 数据库。

### 您应当已具备

- 您已学习 MySQL 教程以了解 MySQL 基础知识。
- 已下载并安装最新版本的 MySQL。
- 已创建密码为 **guest123** 的数据库用户 **guest**。
- 如果您尚未创建数据库，则需要 root 用户及其密码来创建数据库。

本章已分为以下各节：

- **连接到 MySQL 数据库** - 了解如何使用 PHP 打开和关闭 MySQL 数据库连接。
- **使用 PHP 创建 MySQL 数据库** - 本部分介绍如何使用 PHP 创建 MySQL 数据库和表。
- **使用 PHP 删除 MySQL 数据库** - 本部分介绍如何使用 PHP 删除 MySQL 数据库和表。
- **向 MySQL 数据库插入数据** - 一旦您创建了数据库和表，您可能希望将数据插入到已创建的表中。本节将通过真实示例演示数据插入。
- **从 MySQL 数据库检索数据** - 了解如何使用 PHP 从 MySQL 数据库获取记录。
- **使用 PHP 实现分页** - 本部分介绍如何将查询结果显示为多页以及如何创建导航链接。
- **向 MySQL 数据库更新数据** - 本部分介绍如何使用 PHP 更新 MySQL 数据库中的现有记录。
- **从 MySQL 数据库删除数据** - 本部分介绍如何使用 PHP 删除或清除 MySQL 数据库中的现有记录。
- **使用 PHP 备份 MySQL 数据库** - 了解出于安全目的备份 MySQL 数据库的不同方法。

### 连接到 MySQL 数据库

### 打开数据库连接

PHP 提供 **mysqli_connect** 函数来打开数据库连接。该函数接受五个参数，成功时返回 MySQL 链接标识符，失败时返回 FALSE。

### 语法

```
connection mysqli_connect(server,user,passwd,new_link,client_flag);
```

| 序号 | 参数 & 描述 |
| :--- | :--- |
| 1 | **server** 可选 – 运行数据库服务器的主机名。如果未指定，则默认值为 **localhost:3306**。 |
| 2 | **user** 可选 – 访问数据库的用户名。如果未指定，则默认为拥有服务器进程的用户名。 |
| 3 | **passwd** 可选 – 访问数据库的用户密码。如果未指定，则默认为空密码。 |
| 4 | **new_link** 可选 – 如果使用相同参数再次调用 mysqli_connect()，则不会建立新连接；而是返回已打开连接的标识符。 |
| 5 | **client_flags** 可选 – 以下常量的组合 – **MYSQL_CLIENT_SSL** – 使用 SSL 加密；**MYSQL_CLIENT_COMPRESS** – 使用压缩协议 |

- **MYSQL_CLIENT_IGNORE_SPACE** – 允许函数名后带有空格
- **MYSQL_CLIENT_INTERACTIVE** – 允许在关闭连接前进行交互式超时秒数的非活动

**注意** – 您可以在 **php.ini** 文件中指定 server、user、passwd，而无需在每个 PHP 脚本中反复使用它们。请检查 php.ini 文件配置。

### 关闭数据库连接

PHP 提供用于关闭数据库连接的最简单函数 mysqli_close。该函数接受 mysqli_connect 函数返回的连接资源。成功时返回 TRUE，失败时返回 FALSE。

### 语法

```
bool mysqli_close ( resource $link_identifier );
```

如果未指定资源，则关闭最后打开的数据库。

### 示例

尝试以下示例来打开和关闭数据库连接 –

```php
<?php
$dbhost = 'localhost:3036';
$dbuser = 'guest';
$dbpass = 'guest123';
$conn = mysqli_connect($dbhost, $dbuser, $dbpass);
if(! $conn ) {
  die('Could not connect: ' . mysqli_error());
}
echo 'Connected successfully';
mysqli_close($conn);
?>
```

### 使用 PHP 创建 MySQL 数据库

### 创建数据库

