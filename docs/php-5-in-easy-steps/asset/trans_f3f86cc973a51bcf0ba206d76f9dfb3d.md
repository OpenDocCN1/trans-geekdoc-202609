

# SQL 查询

本章演示的基础 SQL 命令用于创建数据库表并向其填充数据。SQL 的更高级功能允许对特定信息进行查询。例如，可以使用此查询搜索第 136 页底部的“cars”表，查找最高速度超过 200 英英的任何汽车的详情：

```
select * from cars where top_mph > 200;
```

在这种情况下，只有一条符合记录的记录：

查询数据库中包含的数据的能力是 MySQL 的威力所在。关于 SQL 语言高级功能的更多信息，请参阅 MySQL 安装目录目录下 Docs 文件夹中的手册。

有关 SQL 的更多详细信息可以在互联网上 www.mysql.com 的 MySQL 语言参考中找到。

可以使用 PHP 使用特殊函数查询 MySQL 数据库，这些函数复制了本章使用的 SQL 命令。

得益于 PHP `mysql_connect()` 函数，从 PHP 连接到 MySQL 数据库非常简单。一旦连接，可以使用 PHP `mysql_query()` 函数查询数据库并将结果存储在 PHP 变量中。

下一章将演示如何在 PHP 脚本内部实现本章所示的所有操作。

# PHP 与 MySQL 协同工作

本章演示了如何从 PHP 脚本创建和操作 MySQL 数据库。示例执行的操作与上一章中直接在 MySQL 监控器中执行的操作相似。

# 目录内容

- 创建 MySQL 用户和密码 | 140
- 将用户连接到 MySQL | 141
- 列出数据库 | 142
- 列出表名 | 143
- 创建数据库 | 144
- 删除数据库 | 145
- 创建数据库表 | 146
- 插入表数据 | 149
- 修改表 | 151
- 从表中检索数据 | 152
- 更多 MySQL | 154

# 第十一章

# 创建 MySQL 用户和密码

在本书开头（安装后立即）完成的 MySQL 连接测试假设是以 root 用户身份在无密码的情况下连接到 MySQL。这提供的安全性很差，因此在现实中，你应该创建一个关联密码的用户。

添加用户的最佳方法是以 root 用户身份在 MySQL 监视器中输入“授权语句（grant statement）”。正常打开 MySQL 监视器通常会将你识别为 root 用户。为了确保无误，请在 MySQL 监视器中输入“exit”关闭监视器。

```
mysql -u root
```

或者，如果为 root 用户设置了密码，该行将变为：

```
mysql -u root -p password
```

现在在 mysql> 提示符下输入此 MySQL 授权语句：

```
grant all privileges on * to user-name@domain identified by "password" with grant option;
```

这将创建一个具有超级用户权限的新用户——允许指定的用户从指定域完全访问，前提是他们提供了指定的密码。

插图显示在 localhost 域中创建一个新用户（“mike”），使用简单的密码“bingo”——这些用户的详情将出现在书中随后的代码示例中。

![](img/7faa63a7fa0add8f53300594ebae949f_141_0.png)

```
MySQL Monitor
mysql> exit
Bye
C:\mysql\bin>mysql -u root ends with ; or \g.
Welcome to the MySQL monitor. Commands with ; or Your MySQL connection id is 17 to server version: 4.0.18-nt
Type 'help'; or 'h' for help. Type 'c' to clear the buffer
mysql> grant all privileges on .* to mike@localhost identified by "bingo" with grant option;
Query OK, 0 rows affected (0.03 sec)
mysql>
```

# 将用户连接到 MySQL

连接 MySQL 时，PHP `mysql_connect` 函数需要三个参数来指定有效的域名、用户名和密码。如果连接成功，该函数返回 true；如果失败则返回 false。下面的脚本在连接成功时写入确认信息。

```php
<?php $user = "mike";
$conn = mysql_connect("localhost", $user, "bingo");
if($conn) {
$msg="Congratulations $user, connected to MySQL";
?>
<html><head><title>Connecting user</title></head>
<body><h3><?php echo($msg); ?></h3></body></html>
```
![](img/7faa63a7fa0add8f53300594ebae949f_142_0.png)
![](img/7faa63a7fa0add8f53300594ebae949f_142_1.png)

用户详情是区分大小写的，因此将 $user 的值更改为 "MIKE" 将导致连接失败并在 Apache 目录下的 error.log 文件中写入 PHP 警告；提供了关于失败的详细信息，如下：

![](img/7faa63a7fa0add8f53300594ebae949f_142_2.png)

# 列出数据库

PHP 中相当于 SQL "show databases" 需要三个函数。

首先，`mysql_list_db()` 返回所有数据库信息的“结果集”，可以将其赋值给变量。每个数据库的详情存储在结果集的单独行中，因此可以使用 `mysql_num_rows()` 函数确定结果中有多少行。每个数据库的名称可以通过 `mysql_tablename()` 函数从结果集中提取。该函数还用于从指定的数据库提取每个表的名称。下面的示例将结果赋值给变量 $rs，并将其作为 `mysql_num_rows()` 函数的参数列出每个数据库名称。

```php
<?php
$conn = @mysql_connect("localhost","mike","bingo");
or die("Sorry - could not connect to MySQL");

$rs = @mysql_list_db($conn);
for ($row = 0; $row < mysql_num_rows($rs); $row++) {
    $db_list .= mysql_tablename($rs, $row) . "<br>";
}
?>
<html><head><title>Listing databases</title></head>
<body><h3><?php echo $db_list; ?></h3></body></html>
```
![](img/7faa63a7fa0add8f53300594ebae949f_143_0.png)

| 列出数据库 |
| :--- |
| File | Edit | Favorites | Help |
| Address | http://localhost/list_db.php | Go |
| test |
| Done | Local intranet |

# 列出表名

与 `mysql_list_db()` 函数类似，PHP `mysql_list_tables()` 函数返回数据库中所有表的信息的结果集。

通过指定结果集的行号作为 `mysql_tablename()` 函数的参数，可以提取每个表名。下面的示例显示了添加到 test 数据库的三个表的名称。

![](img/7faa63a7fa0add8f53300594ebae949f_144_0.png)

```php
<?php $conn = @mysql_connect("localhost", "mike", "bingo")
or die("Sorry - could not connect to MySQL");

$rs1 = @mysql_list_db($conn);
for($row = 0; $row < mysql_num_rows($rs1); $row++) {
    $thisdb = mysql_tablename($rs1, $row);
    $list = "<b>" . $thisdb . "</b><br>";
    if ($thisdb != "mysql") {
        $rs2 = mysql_list_tables($thisdb);
        for($num = 0; $num < mysql_num_rows($rs2); $num++) {
            $list = "<li>" . mysql_tablename($rs2,$num) . "</li>";
        }
    }
}
?>
```

必须排除 MySQL 自身的数据库（名为 "mysql"），因为出于安全考虑，不能这种方式读取表。

```html
<html><head><title>Listing Tables</title></head><body><?php echo ($list); ?></body></html>
```

| 列出表 |
| :--- |
| File | Edit | Favorites | Tools | Help |
| Address | http://localhost/list-tables.php | Go |
| mysql |
| test |
| - first_table |
| - second_table |
| - third_table |
| Done | Local intranet |

# 创建数据库

PHP `mysql_create_db()` 尝试根据其参数提供的名称创建一个数据库。下面的示例显示了所有现有数据库，提供了一个可以输入新数据库名称的表单。当提交表单时，脚本尝试创建一个指定名称的新数据库。

![](img/7faa63a7fa0add8f53300594ebae949f_145_0.png)

```php
$conn = @mysql_connect("localhost","mike","bingo");
or die("Sorry - could not connect to MySQL");
```
![](img/7faa63a7fa0add8f53300594ebae949f_145_1.png)

```php
$rs1 = @mysql_create_db($_REQUEST['db_name']);
```

如果数据库创建成功，该函数返回 true；如果尝试失败则返回 false。

```php
$rs2 = @mysql_list_db($conn);
for ($row = 0; $row < @mysql_num_rows($rs2); $row++) {
  $list .= mysql_tablename($rs2, $row) . "<li>...</li>";
}
?>
?>
<html><head><title>Creating databases</title></head>
<body>
<form action="<?php echo $_SERVER['PHP_SELF'];?>" method="post">
Current databases: <?php echo $list; ?>
<hr>Name:<input type="text" name="db">
<input type="submit" value="Create database">
</form>
</body>
</html>
```
![](img/7faa63a7fa0add8f53300594ebae949f_145_2.png)
![](img/7faa63a7fa0add8f53300594ebae949f_145_3.png)

