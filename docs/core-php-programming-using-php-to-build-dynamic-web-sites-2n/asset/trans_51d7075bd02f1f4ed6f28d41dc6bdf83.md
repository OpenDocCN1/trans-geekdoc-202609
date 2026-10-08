

# PHP 核心编程

mysql_affected_rows 函数返回对指定的数据库连接链接执行的最后一次查询所受影响的行数。如果省略了 link 参数，则假设使用最后打开的连接。如果最后一个查询是无条件的删除，将返回 0。如果你想知道 select 语句返回了多少行，请使用 mysql_num_rows。

```php
<?
// 以 freerate 用户身份连接到服务器，无密码
$dbLink = mysql_connect("localhost","freerate", "");

// 选择 'freerate' 数据库
mysql_select_db("freerate", $dbLink);

// 更新一些发票
$Query = "UPDATE invoice "
"SET Active = 'Y' "
"WHERE ID = 100";
$dbResult = mysql_query($Query, $dbLink);

// 让用户知道更新了多少行
$AffectedRows = mysql_affected_rows($dbLink);
print("$AffectedRows 行已更新。<BR>\n");
?>
```

# 布型 mysql_change_user(string user, string password, string database, integer link)

使用 mysql_change_user 更改数据库连接的用户。database 和 link 参数是可选的。如果省略，则使用当前数据库和已打开的链接。如果无法更改用户，当前连接将保持原始用户打开状态。此函数需要 MySQL 3.23.3 或更高版本。

```php
<?
// 以 freerate 用户身份连接到服务器，无密码
$dbLink = mysql_connect("localhost","freerate", "");

// 选择 'freerate' 数据库
mysql_select_db("freerate", $dbLink);

// 切换到 admin 用户
mysql_change_user("admin","secret","freerate", $dbLink);
?>
```

# 布型 mysql_close(integer link)

使用 mysql_close 关闭与数据库的连接。该连接必须通过 mysql_connect 打开。使用此函数并不是严格必要的，因为所有持久链接在脚本结束时都会自动关闭。link 参数是可选的，如果省略，将关闭最后打开的连接。

```php
<? // 打开连接
$Link = mysql_connect("localhost", "httpd", "");

// 关闭连接
mysql_close($Link);
?>
```

# 整型 mysql_connect(string host, string user, string password)

mysql_connect 函数开始在指定的主机上连接 MySQL 数据库。如果数据库在不同的端口，请在主机名后加上冒号和端口号。或者，如果连接到 localhost:/tmp/sockets/mysql.sock，可以使用冒号和套接字路径。所有参数都是可选的，默认值均为 localhost、执行脚本的用户名以及空字符串。执行脚本的用户通常是 httpd，即 Web 服务器。

连接在脚本执行完毕时会自动关闭，尽管它们也可以通过 mysql_close 提前关闭。如果你尝试打开一个已经已经打开的连接，则不会建立第二个连接。将返回之前已打开连接的标识符。

发生错误时返回 FALSE。

```php
<?
// 建立连接
if(!($dbLink = mysql_connect("localhost:3606"
```

# 布型 mysql_create_db(string database, integer link)

使用 mysql_create_db 创建新数据库。注意，你必须使用具有创建数据库权限的账户打开连接。如果省略 link 参数，将使用最后打开的连接。

```php
<?php
// 打开连接
$dbLink = mysql_connect("localhost", "admin", "secret");

// 创建数据库
mysql_create_db("garbage", $dbLink);
?>
```

# 布型 mysql_data_seek(integer result, integer row)

mysql_data_seek 函数将结果集的内部行指针移动到指定的行。将此函数配合 mysql_fetch_row 使用可以跳转到特定行。result 参数必须已由 mysql_query 或类似的函数返回。

```php
<?php
// 以 freetrade 用户身份连接到服务器，无密码
$dbLink = mysql_pconnect("localhost", "freetrade", "");

// 选择 'freetrade' 数据库
mysql_select_db("freetrade", $dbLink);

// 从 tax 表获取状态
$Query = "SELECT State FROM tax ";
$dbResult = mysql_query($Query, $dbLink);

// 跳转到第五行
mysql_data_seek($dbResult, 4);

// 获取行
$row = mysql_fetch_row($dbResult);

// 打印状态名称
print($row[0]);
?>
```

# 整型 mysql_db_query(string database, string query, integer link)

mysql_query 函数在指定的数据库上执行查询并返回一个新的标识符。如果省略了 link 参数，将使用最后打开的链接，或者在必要时创建一个新的。

```php
<?
// 以 freetrade 用户身份连接到服务器，无密码
$dbLink = mysql_pconnect("localhost", "freetrade", "");

// 清空会话表
$Query = "DELETE FROM session ";
$dbResult = mysql_query($Query, $dbLink);
?>
```

# 布型 mysql_drop_db(string database, integer link)

使用 mysql_drop_db 删除数据库。如果省略了 link 参数，将使用最后打开的链接。

```php
<?
// 打开连接
$dbLink = mysql_connect("localhost", "admin", "secret");

// 删除数据库
if(mysql_drop_db("garbage", $dbLink))
?>
```

# 整型 mysql_errno(integer link)

mysql_errno 函数返回最后一次查询的错误号。如果省略 link 参数，将使用最后打开的连接。

```php
<?
// 打开连接
$dbLink = mysql_connect("localhost", "admin", "secret");

// 删除数据库
if(mysql_drop_db("garbage", $dbLink))
{
    print("删除成功");
}
}
```
?>
```

# 字符串 mysql_error(integer link)

mysql_error 函数返回最后一次查询的错误信息。如果省略 link 参数，将使用最后打开的连接。

```php
<?
// 打开连接
$dbLink = mysql_connect("localhost", "admin", "secret");

// 删除数据库
if(mysql_drop_db("garbage", $dbLink))
{
    print("删除成功");
}
}
```
```?>
```

# 数组 mysql_array(integer result, integer type)

mysql_array 函数返回包含结果行的数组。type 参数决定数组的索引方式（MYSQL_ASSOC、MYSQL_NUM 或 BOTH）。如果省略 type，则默认使用 BOTH。

```php
<?
// 以 freetrade 用户身份连接到服务器，无密码
$dbLink = mysql_connect("localhost", "freetrade", "");

// 选择 'freetrade' 数据库
mysql_select_db("freetrade", $dbLink);

// 执行查询
$Query = "SELECT State, Rate FROM tax ";
$dbResult = mysql_query($Query, $dbLink);

// 获取数组
$row = mysql_array($dbResult, MYSQL_ASSOC);

// 打印结果
print($row['State'] . ": " . $row['Rate']);
?>
```

# 数组 mysql_fetch_array(integer result, integer type)

mysql_fetch_array 函数从结果中的一行数组。type 参数决定数组的索引方式（MYSQL_ASSOC、MYSQL_NUM 或 BOTH）。如果省略 type，则默认使用 BOTH。

```php
<?
// 以 freetrade 用户身份连接到服务器，无密码
$dbLink = mysql_connect("localhost", "freetrade", "");

// 选择 'freetrade' 数据库
mysql_select_db("freetrade", $dbLink);

// 执行查询
$Query = "SELECT State, Rate FROM tax ";
$dbResult = mysql_query($Query, $dbLink);

// 获取行
$row = mysql_fetch_array($dbResult, MYSQL_ASSOC);

// 打印结果
print($row['State'] . ": " . $row['Rate']);
?>
```

# 数组 mysql_fetch_row(integer result)

mysql_fetch_row 函数从结果中的一行返回数值数组。

```php
<?
// 以 freetrade 用户身份连接到服务器，无密码
$dbLink = mysql_connect("localhost", "freetrade", "");

// 选择 'freetrade' 数据库
mysql_select_db("freetrade", $dbLink);

// 执行查询
$Query = "SELECT State, Rate FROM tax ";
$dbResult = mysql_query($Query, $dbLink);

// 获取行
$row = mysql_fetch_row($dbResult);

// 打印结果
print($row[0] . ": " . $row[1]);
?>
```

# 数组 mysql_fetch_assoc(integer result)

mysql_fetch_assoc 函数从结果中的一行返回关联数组。

```php
<?
// 以 freetrade 用户身份连接到服务器，无密码
$dbLink = mysql_connect("localhost", "freetrade", "");

// 选择 'freetrade' 数据库
mysql_select_db("freetrade", $dbLink);

// 执行查询
$Query = "SELECT State, Rate FROM tax ";
$dbResult = mysql_query($Query, $dbLink);

// 获取行
$row = mysql_fetch_assoc($dbResult);

// 打印结果
print($row['State'] . ": " . $row['Rate']);
?>
```

# 对象 mysql_fetch_object(integer result)

mysql_fetch_object 函数从结果中的一行返回一个对象。

```php
<?
// 以 freetrade 用户身份连接到服务器，无密码
$dbLink = mysql_connect("localhost", "freetrade", "");

// 选择 'freetrade' 数据库
mysql_select_db("freetrade", $dbLink);

// 执行查询
$Query = "SELECT State, Rate FROM tax ";
$dbResult = mysql_query($Query, $dbLink);

// 获取行
$row = mysql_fetch_object($dbResult);

// 打印结果
print($row->State . ": " . $row->Rate);
?>
```

# 数组 mysql_fetch_all(integer result)

mysql_fetch_all 函数返回一个包含结果集中所有行的关联数组。

```php
<?
// 以 freetrade 用户身份连接到服务器，无密码
$dbLink = mysql_connect("localhost", "freetrade", "");

// 选择 'freetrade' 数据库
mysql_select_db("freetrade", $dbLink);

// 执行查询
$Query = "SELECT State, Rate FROM tax ";
$dbResult = mysql_query($Query, $dbLink);

// 获取所有行
$rows = mysql_fetch_all($dbResult);
foreach($rows as $row) {
    print("State: {$row['State']}, Rate: {$row['Rate']}<BR>\n");
}
?>
```

