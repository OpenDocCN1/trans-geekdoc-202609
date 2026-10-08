

# PHP 核心编程

```php
//创建查询
$Query = "SELECT * ";
$Query .= "FROM item";

//执行查询
if!($Result = pg_exec($Connection, $Query))
{
    print("Could not execute query: ");
    print($pg_errormessage($Connection));
    print("<BR>\n");
    exit;
}

// 遍历每一行
while($Row = pg_fetch_row($Result, $Row))
{
    print("$Row[0]<BR>\n");
}

// 释放结果并关闭连接
pg_freesult($Result);
pg_close($Connection);
?>
```

# 布尔型 pg_fieldnull(integer result, integer row, string field)

如果指定的字段为 NULL，则 pg_fieldnull 返回 TRUE。字段从 0 开始计数。参见 pg_exec 的用法示例。

# 字符串 pg_fieldname(integer result, integer field)

pg_fieldname 返回结果集中由字段编号指定的字段名称，该编号从 0 开始计数。参见 pg_exec 的用法示例。

# 整数型 pg_fieldnum(integer result, string field)

pg_fieldnum 根据字段名称返回字段编号。编号从 0 开始。如果发生错误，返回负数 (-1)。

# 整数型 pg_fieldprlen(integer result, integer row, string field)

pg_fieldprlen 返回特定字段值的长度。你可以通过编号（从 0 开始）或名称来指定字段。

```php
<?php
print(pg_fieldprtlen($Result, $Row, 2));
?>
```

# 整数型 pg_fieldsize(integer string, string)

pg_fieldsize 函数返回字段的大小，可以通过名称或编号指定。字段从零开始编号。参见 pg_exec 的用法示例。

# 字符串 pg_fieldtype(integer result, string field)

pg_fieldtype 函数返回指定字段的类型。字段参数可以是数字或名称。字段从 0 开始编号。参见 pg_exec 的用法示例。

# 布尔型 pg_freeresult(integer result)

pg_freeresult 函数释放与结果集相关的任何内存。通常没有必要调用此函数，因为所有内会在脚本结束时被清除。参见 pg_exec 的用法示例。

# 整数型 pg_getlastoid()

如果最后一次调用 pg_exec 是 INSERT 语句，则 pg_getlastoid 返回插入到表中最后一个对象的 ID (OID)。如果发生错误，则返回负一 (-1)。

```php
<?php
//连接数据库
$Connection = pg_connect("", "", "", "leon");

$Query = "INSERT INTO item (name, price) ";
$Query = "VALUES ('hammer', 15.00)";

$Result = pg_exec($Connection, $Query);

print("ID of inserted item: " . pg_getlastoid() . "<BR>\n");

pg_close($Connection);
?>
```

# 字符串 pg_host(integer connection)

# PHP 核心编程

pg_host 函数返回连接的主机名。参见 pg_exec 的用法示例。

# pg_close(integer file)

pg_clouse 函数关闭一个大对象。file 参数是由 pg_looper 返回的文件标识符。参见 pg_looper 的用法示例。

# 整数型 pg_locrate(integer connection)

pg_locrate 函数创建一个大对象并返回 OID。该对象创建时同时具有读写权限。

```php
<?php
$Object = pg_locrate($Connection);
?>
```

# 整数型 pg_looper(integer connection, integer object, string mode)

pg_looper 打开一个大对象。object 参数是大对象 ID，mode 可以是 r 或 rw 之一。返回一个文件标识符。

```php
<?php
$Object = pg_locrate($Connection);
$File = pg_looper($Connection, $Object, "r");
pg_close($File);
?>
```

# 字符串 pg_loread(integer file, integer length)

pg_load 函数将大对象作为字符串返回。length 参数指定返回的最大长度。

```php
<?php
$Object = pg_locrate($Connection);
$File = pg_looper($Connection, $Object, "r");
$Contents = pg_loread($File, 4096);
?>
```

# pg_loreadall(integer file)

# PHP 核心编程

pg_loreall 函数读取整个大对象并将其直接发送到浏览器。

```php
<?php
$File = pg_looper($Connection, $Object, "r");
pg_loreall($File);
?>
```

# pg_lounclick(integer file, integer object)

使用 pg_lounlink 删除大对象。

```php
<?php
$Object = pg_locreate($Connection);
$File = pg_looper($Connection, $Object, "r");
pg_lounlink($File, $Object);
?>
```

# pg_lowrite(integer file, string buffer)

pg_lowrite 函数将缓冲区写入写入大对象。

```php
<?php
$Object = pg_locreate($Connection);
$File = pg_looper($Connection, $Object, "w");
pg_lowrite($File, "some text");
?>
```

# 整数型 pg_numfields(integer result)

pg_numfields 函数返回结果集中的字段数量。参见 pg_exec 的用法示例。

# 整数型 pg_numrows(integer result)

使用 pg_numrows 获取结果集中的行数。参见 pg_exec 的用法示例。

# 字符串 pg_options(integer connection)

# PHP 核心编程

pg_options 函数返回打开连接时使用的选项。参见 pg_exec 的用法示例。

# 整数型 pg_connect(string host, string port, string options, string tty, string database)

pg_connect 函数的操作与 pg_connect 相同，不同在于它创建了一个持久连接。该连接将持续到服务器进程结束为止，因此可能会被重用。这节省了打开连接的开销时间。

```php
<?php
$Connection = pg_connect("", "", "", "leon");
?>
```

# 整数型 pg_port(integer connection)

pg_port 函数返回 pg_connect 函数使用的端口号。参见 pg_exec 的用法示例。

# 字符串 pg_result(integer result, integer row, string field)

使用 pg_result 获取由字段编号指定的特定集中字段的值，编号从 0 开始。参见 pg_exec 的用法示例。

# 字符串 pg_tty(integer connection)

pg_tty 函数返回用于调试的 tty 名称，并由 pg_connect 函数提供。

# Sybase

Sybase 提供了一个工业级数据库，在 Oracle、Informix、IBM 等其他数据库中占有一席。由于与应用供应商的合作，Sybase 对预算有限的开发者更为可用。事实上，PHP 的 Sybase 函数可以连接到 SQL Server。Microsoft SQL Server 6.5 是 Sybase 的一个版本。在 Windows 上编译 PHP 时，可以使用 MSSQL 库。该库实际上就是 DB-Library，但 PHP 扩展创建了 Sybase 扩展中不存在的函数：`mssql_field_length`、`mssql_field_name` 和 `mssql_field_type`。为了代码的可读性，所有以 sybase_ 开头的函数都有对应的 msql_ 别名，但为了节省空间我没有列出它们。

| 表 13.11 MSSQL 函数 |
|---|
| mssql_close |
| mssql_connect |
| mssql_data_seek |
| mssql_fetch_array |
| mssql_fetch_field |
| mssql_fetch_object |
| mssql_fetch_row |
| mssql_field_length |
| mssql_field_name |
| mssql_field_seek |
| mssql_field_type |
| mssql_free_result |
| mssql_get_last_message |
| mssql_min_error_severity |
| mssql_min_message_severity |
| mssql_num_fields |
| mssql_num_rows |
| mssql_pconnect |
| mssql_query |
| mssql_result |
| mssql_select_db |

Sybase 的主页：<http://www.sybase.com/>。如果你想了解更多关于库的信息，请查看在线文档

```
<http://sybooks.sybase.com/onlinebooks/group-cn/11010e/ctref/@Generic_Bookview>
```

Tom May 和 Veer Suraski 都对 sybase 扩展做出了贡献。

# 整数 sybase_affected_rows(integer link)

使用 sybase_affected_rows 获取给定连接上最后一个删除、插入或更新语句影响的行数。如果省略了可选的 link 参数，将使用最近打开的连接。注意，此函数不用于

