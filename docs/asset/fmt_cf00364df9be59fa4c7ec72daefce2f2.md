
# 第 15 章 PHP/MySQL 函数

```php
    // 如果连接成功
} else {
    printError("Sorry for the inconvenience; but we are unable to process your request at this time. Please check back later");
    notify("Problem connecting to database in $SCRIPT_NAME at line 20 on " . date("Y-m-d"));
}
```

即使你真的想尝试 PHP 的新 OOP 特性，也请尝试使用异常处理，我们在第 6 章中简要介绍过异常，并在第 31 章中会有更完整的介绍。

## 使用 PHP 创建 MySQL 数据库

如果你愿意，实际上可以使用 PHP 来创建数据库，而不是使用 MySQL 客户端工具。这种做法具有潜在的优势——你可以使用一个活跃的前端，这可能会吸引那些认为 MySQL 命令行客户端难用或太挑剔的人；但这种优势被一个缺点抵消了，那就是安全性。

> 关于如何在使用 PHP 定义 MySQL 数据库时最大限地减少安全问题的更多信息，请参阅第 14 章。

要从 PHP 创建数据库，你的所有脚本都需要对 MySQL 拥有完全的`CREATE/DROP`。这意味着如果获取了你的脚本，可能会轻而易举地删除你所有的数据库及其内容。从安全的角度来看，这并不是一个好主意。此外，外部 Web 主机通常不会让你在他们的服务器上这样做。

如果你正在考虑用 PHP 创建数据库，请帮自己一个大忙，至少不要将数据库用户名和密码存储在文本文件中。让自己手动将数据库用户名和密码输入到文件中，并在每次使用此脚本时将变量传递给插入的头部。在这种情况下，将变量保留在 Web 树之外的包含文件中是不够的预防措施。

对于那些喜欢冒险的人，相关的函数有：

- `mysql_create_db()`：在指定的主机上创建数据库，名称在参数中指定。
- `mysql_drop_db()`：删除指定的数据库。
- `mysql_query()`：在此函数中传递表定义和删除操作。

一个基础的数据库生成脚本可能如下：

```php
<?php
$linkID = mysql_connect('localhost', 'root', 'sesame');
mysql_create_db('new_db', $linkID);
mysql_select_db('new_db');
$query = "CREATE TABLE new_table (
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    col VARCHAR(255)
);";
$result = mysql_query($query);
$xa = mysql_drop_db('new_db');
?>
```

还有像 phpMyAdmin 这样的预制工具，可以以非常漂亮的方式为你完成工作（关于使用 phpMyAdmin 的信息请参阅第 14 章）。你只需要填写一个 Web 表单，PHP 脚本就会根据你的规范创建数据库。在许多情况下，该工具还可以让你执行其他管理任务，例如检查数据库的大小或对其进行备份。这比你自己操作更不安全（因为你可能不会为了安全考虑而检查每一行代码），但人们确实在使用这些工具。

其他 GUI 工具不是基于数据库的，但可以与 MySQL 工作。随着 MySQL 变得越来越流行，适用于 Windows 和 Linux 的应用程序也大量出现，允许你以喜欢的图形化方式管理 MySQL 数据库。与它们的 Web 版本一样，这些应用程序提供了完全的管理控制，但无需处理操作 Web 界面的烦恼。随着软件的更替，列表经常变化，因此在这里列出很快就会过时。然而，MySQL 网站在`http://mysql.com/portal/server/index.html`维护了一份综合列表。

> 如果你使用 GUI 工具管理数据库，至少应在防火墙内的开发机上使用它，以最大限度地减少安全风险。当你尽情地完成数据库设计后，可以启动数据库导出，并将整个结构和代码移动到生产数据库服务器。除非绝对必要，否则不要在生产环境中使用 phpMyAdmin 或任何其他 GUI。

## MySQL 数据类型

用于创建 MySQL 数据库的实际 PHP 函数与 MySQL 数据结构相比是是微不足道的。第 13 章的“数据库设计”部分有关于如何概念化数据库模式以及如何使用`CREATE`、`DROP`和`ALTER`语句的规则。然而，要在 MySQL 中实现你的抽象模式，你需要了解 MySQL 数据类型以及如何使用它们。

通用规则是使用最小且最具体的类型，以充分满足数据库中该列的需求。MySQL 以具有紧凑的类型而闻，例如`TINYINT`和`TINYTEXT`，非常适用于 0/1 值或文件名。它还有非常大的类型，可以在一个字段中存储多达 4GB 的数据。

MySQL 数据类型分为三类：数值类型、日期时间类型和字符串（或字符）类型。在大多数情况下，它们的使用可以相当直观——这意味着普通用户不会知道或不在乎你使用的是`INT`还是`MEDIUM`。但是，如果你是那种追求以绝对最快的方式处理一切的程序员，MySQL 手册提供了关于最大化效率的细微提示——例如，始终使用 4 字节的`DECIMAL`来存储`DATETIME`或`TIMESTAMP`。仔细使用“列类型”可以提高效率。

| 名称 | 存储大小 | 用法 |
| :--- | :--- | :--- |
| `TINYINT` | 1 字节 | 无符号，存储 0 到 255。 |
| `SMALLINT` | 2 字节 | 无符号，存储 0 到 65535。 |
| `MEDIUMINT` | 3 字节 | 无符号，存储 0 到 16777215。 |
| `INT(M)` | 4 字节 | 无符号，存储 0 到 4294967295。 |
| `BIGINT(M)` | 8 字节 | 无符号，存储 0 到 9223372036854775807。 |
| `FLOAT(M)` | 4 字节 | 单精度浮点数。 |
| `DOUBLE(M)` | 8 字节 | 双精度浮点数。 |
| `DECIMAL(M,D)` | `M+1`或`M+2`字节 | 解压缩小数；用于货币。 |
| `DATETIME` | 8 字节 | 格式为 YYYY-MM-DD HH:MM:SS。 |
| `TIMESTAMP` | 4 字节 | 格式为 YYYY-MM-DD HH:MM:SS。这允许`TIME`表示两个事件之间的时间。 |
| `TIME` | 3 字节 | 格式为 HHH:MM:SS，其中 HHH 的值为 -838 到 838。 |
| `YEAR` | 1 字节 | 格式为 YYYY，取值为 1901 到 2155。 |
| `CHAR(M)` | `M`字节 | 固定长度。如果字符串长度不足，将在末尾填充空格。`M`必须小于 255。 |
| `VARCHAR(M)` | 最多`M`字节 | 可变长度。`M`必须小于 255。 |
| `TINYOB`或`TINTEXT` | 最大 255 字节 | `TINYOB`区分大小敏感，`TINTEXT`不区分大小。 |
| `BLOB` | 最大 64KB | `BLOB`区分大小敏感，`TEXT`不区分大小。 |
| `MEDIUMBLOB`或`MEDIUMTEXT` | 最大 16MB | `MEDIUMBLOB`区分大小敏感，`MEDIUMTEXT`区分大小敏感。 |
| `LONGBLOB`或`LONGTEXT` | 最大 4GB | `LONGBLOB`区分大小敏感，`LONGTEXT`不区分大小。 |
| `ENUM(value,...,valueN)` | 1 或 2 字节 | 最多 65535 个不同值。 |
| `SET(value,...,valueN)` | 最多 8 字节 | 最多 64 个不同值。 |

## MySQL 函数

表 15-2 包含了 MySQL 函数的回顾。所有括号中的参数都是可选的。

### 表 15-2: PHP-MySQL 函数

| 函数名称 | 用法 |
|---|---|
| `mysql_affected_rows([link_id])` | 在执行非零`INSERT`、`UPDATE`或`DELETE`查询后使用，以检查更改的行数。 |
| `mysql_change_user(user, password[,,link_id])` | 在打开的连接上更改 MySQL 用户。 |
| `mysql_close([link_id])` | 关闭指定的连接（通常是没有必须的）。 |
| `mysql_connect(host[:port]][socket][, username][, password])` | 在指定的主机、端口、套接字上打开连接；并按密码指定。所有参数均为可选。 |
| `mysql_create_db(db_name[,link_id])` | 在最近的打开连接上创建一个新的 MySQL 数据库。 |
| `mysql_data_seek(result_id, row_num)` | 将内部行指针移动到指定的行号。使用获取函数从该行返回数据。 |
| `mysql_drop_db(db_name[,link_id])` | 删除指定的数据库。 |
| `mysql_errno([link_id])` | 返回错误 ID。 |
| `mysql_error([link_id])` | 返回文本错误消息。 |
| `mysql_fetch_array(result_id[,result_type])` | 以关联数组的形式获取结果。结果类型可以是`MySQL_ASSOC`、`MySQL_NUM`或`MYSQL_BOTH`（默认）。 |
| `mysql_fetch_field(result_id[, field_offset])` | 以对象的形式返回字段信息。 |
| `mysql_fetch_lengths(result_id)` | 返回结果中每个字段的长度。 |
| `mysql_fetch_object(result_id[, result_type])` | 以对象的形式获取结果。结果类型对应`mysql_fetch_array`。 |
| `mysql_fetch_row(result_id)` | 以枚举数组获取结果。 |
| `mysql_field_name(result_id, field_index)` | 返回枚举字段名称。 |
| `mysql_field_seek(result_id, field_offset)` | 将指针移动到指定的偏移量。配合`mysql_field_fetch`使用。 |
| `mysql_field_table(result_id, field_offset)` | 返回指定字段所属表的名称。 |
| `mysql_field_type(result_id, field_offset)` | 返回指定字段的（例如`TINYINT`, `BLOB`, `VARCHAR`）。 |
| `mysql_field_flags(result_id, field_offset)` | 返回与枚举字段相关的标志（例如`NOT NULL`, `AUTO_INCREMENT`, `BINARY`）。 |
| `mysql_field_len(result_id, field_offset)` | 返回枚举字段的长度。 |
| `mysql_free_result(result_id)` | 释放结果集占用的内存（通常是没有必须的）。 |
| `mysql_insert_id({link_id})` | 返回`INSERT`的自增 ID；如果插入失败或最后一个查询不是插入，则返回`FALSE`。 |
| `mysql_list_fields(database, table[{link_id}])` | 返回用于`mysql_field`函数的结果 ID，而不执行实际查询。 |
| `mysql_list_dbs({link_id})` | 返回`mysqlqld`上数据库的指针。配合`mysql_tablename`使用。 |
| `mysql_list_tables(database, table[{link_id}])` | 返回数据库中表的指针。配合`mysql_tablename`使用。 |
| `mysql_num_fields(result_id)` | 返回结果集中的字段数。 |
| `mysql_num_rows(result_id)` | 返回结果集中的行数。 |
| `mysql_connect({host}:[port]][{username,[password]})` | 打开到数据库的持久连接。所有参数均为可选。注意——`mysql_close`和脚本终止不会关闭连接。 |
| `mysql_query(query_string,{link_id})` | 将查询发送到数据库。记住将分号放在双引号字符串之外。 |
| `mysql_result(result_id, row_id, field_identifier)` | 返回单字段结果。标识符可以是字段偏移量`(0)`或表点名`myfield.table`。 |
| `mysql_select_db(database,{link_id})` | 为查询选择数据库。 |
| `mysql_tablename(result_id, table_id)` | 配合任何`mysql_list`函数使用，返回结果指针引用的值。 |

## 总结

PHP 的 MySQL 和 MySQL 函数易于使用，但有时也会令人困惑。每次 PHP/MySQL 交互都必须包含一个连接、一个数据库设置以及一个返回结果的查询或命令。结果标识符就像一个 ATM，用来报告操作的成功或失败。

如果在`SELECT`语句后返回了数据，必须使用其中一个 PHP/MySQL 获取函数。如果你想遍历结果集，可以使用`mysql_data_seek()`将行指针重置为零。PHP 还有许多函数返回有关数据库本身或特定操作的数据。最常用的两个是返回结果集中行数的`mysql_num_rows()`和返回自增 ID 的`mysql_insert_id()`。

此类函数如列表 16-1 所示，嵌入在一个完整的 PHP 页面中，该页面用于显示几个表格的内容。

## 列表 16-1：表格显示器

```php
<?php
include("/home/phpbook/phpbook-vars.inc");
$global_db = mysql_connect($hostname, $username, $password);
mysql_select_db($db, $global_db);

display_db_table($tablename, $connection)
{
  $query_string = "SELECT * FROM $tablename";
  $result_id = mysql_query($query_string, $connection);
  $column_count = mysql_num_fields($result_id);

  print("<TABLE BORDER=1>\n");
  while ($row = mysql_fetch_row($result_id)) {
    print("<TR ALIGN-LEFT VALID TOP>\n");
    for ($column_num = 0; $column_num < $column_count; $column_num++) {
      print("<TD" .$row[$column_num]."</TD>\n");
    }
    print("</TR>\n");
  }
  print("</TABLE>\n");
}
?>

<HTML>
<HEAD>
<TITLE>Cities and countries</TITLE>
</HEAD>
<body>

<TABLE><TD>
<?php display_db_table("country", $global_db); ?>
</TD></TD>
<?php display_db_table("city", $global_db); ?>
</TD></TR></</body></html>
```

关于此脚本需要注意的点：

- 虽然脚本引用了特定的数据库表，但`display_db_table()`函数是通用的。你可以将函数定义放在一个包含文件中，然后在网站上使用它。
- 脚本的第一要操作是加载一个包含文件，该文件包含数据库名、数据库用户名和数据库密码的变量赋值。然后它使用这些值连接到 MySQL，然后选择所需的数据库。（该文件位于公开的 Web 层次结构之外，这使得它比直接在代码中包含这些信息稍微安全一点。）
- 在函数内部，我们选择使用`while`循环打印行，并使用`for`循环打印单个项目。我们本可以容易地对都使用边界循环，并用`mysql_num_rows()`获取行数。
- 主循环反映了一个非常常见的惯用法，它利用了 PHP 赋值语句的值即所赋值的值这一事实。变量`$row`被赋值为函数`mysql_fetch_row()`的结果，该结果将是该行值的数组，或者在没有更多行时为`false`。如果没有行了，`$row`意味着表达式值为`false`，`while`循环终止。
- 我们在选定的行末尾添加了换行符（`\n`），这样 HTML 源代码在打印或从浏览器查看源码时将具有可读的结构。注意，这些换行不是 HTML 换行符（`<BR>`），且不会影响生成页面的外观。（事实上，如果你想让别人检查你生成的 HTML 变得痛苦，就不要在所有地方都加换行符！）

## 示例表格

要查看列表 16-1 示例的运行情况，请参图16-1，它显示了`Country`和`City`示例表的显示内容。这些表具有以下结构：

```
Country:
ID int (自动递增主键)
continent varchar(50)
countryname varchar(50)
City:
ID int (自动递增主键)
cityname varchar(50)
```
