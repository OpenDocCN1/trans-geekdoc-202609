
`ibase_blob_commit`函数提交指定`link`上的事务，如果没有指定，则提交上一个`link`。

# `ibase_connect(string path, string user, string password)`

使用`ibase_connect`连接InterBase数据库。你必须指定数据库路径。`user`和`password`参数可以省略，它们默认为`php.ini`中`ibase_default_user`和`ibase_default_password`指令设置的值。本节中的大多数其他函数都会返回一个连接标识符。连接不会被PHP或你的脚本关闭，但你可以手动用`ibase_close`关闭它。使用相同用户对同一数据库的第二个连接将返回相同的连接标识符。将此函数与`ibase_pconnect`进行对比。

# `ibase_errmsg()`

使用`ibase_errmsg`获取最后的错误消息。如果没有可用的错误消息，返回`FALSE`。

# `ibase_execute(integer query, value bind, ...)`

使用`ibase_execute`执行由`ibase_prepare`准备的查询。如果查询包含`?`占符，你必须在查询标识符之后提供绑定值。如果执行的是`select`查询，则返回结果标识符。

# `ibase_fetch_object(integer result, integer blob)`

`ibase_fetch_object`函数返回一个对象，其中包含结果集中每一列的属性。属性名称将与列名匹配。`blob`参数是可选的。如果设置为`I_TEXT`，blob列将以文本形式返回。否则返回blob标识符。如果没有剩余行，则返回`FALSE`。

# `ibase_fetch_row(integer result, integer blob)`

`ibase_fetch_row`函数的操作与`ibase_fetch_object`相同，但返回的是一个数组。列不是通过名称引用，而是从0开始通过数字引用。

# `ibase_field_info(integer result, integer field)`

使用`ibase_field_info`获取结果集中列的信息。返回一个包含以下元素的关联数组：`alias`、`length`、`name`、`relation`、`type`。

# `boolean ibase_free_query(integer query)`

使用`ibase_free_query`释放与准备的查询相关的内存。

# `boolean ibase_free_result(integer result)`

使用`ibase_free_result`释放与结果集相关的内存。

# `integer ibase_num_fields(integer result)`

`ibase_num_fields`返回结果集的字段数量。

# `ibase_pconnect(string path, string user, string password, string character-set)`

`ibase_pconnect`函数类似于`ibase_connect`。区别在于连接不会被PHP或你的脚本关闭。它们持久于服务器进程中，以便后续脚本执行需要相同连接时可以重用。

# `integer ibase_prepare(string query)`
`integer ibase_prepare(integer link, string query)`

使用`ibase_prepare`准备查询以便稍后用`ibase_execute`执行。如果你漏掉了`link`参数，将使用上一个打开的`link`。返回查询标识符。

# `integer ibase_query(string query, value bind, ...)`
`integer ibase_query(integer link, string query, value bind, ...)`

`ibase_query`函数在打开的连接上执行查询。你可以跳过`link`标识符，导致使用上一个打开的连接。如果查询包含占位符，你必须与查询参数后的值进行匹配。返回结果标识符。它用于配合`ibase_fetch_row`等函数使用。

# PHP核心编程

```php
ibase_close($dbLink);
?>
```

# `ibase_rollback(integer link)`

`ibase_rollback`函数导致事务回滚。指定链接上的默认事务将执行回滚。如果没有指定链接，则将使用最后一个链接。

# `ibase_timemtf(string format)`

使用`ibase_timemtf`设置日期/时间列的格式。格式字符串应遵循`strtotime`的规则。默认格式为`"%m/%d/%Y %H:%M:%S"`。`strtotime`函数在第11章“时间、日期和配置函数”中有详细描述。

# `integer ibase_trans(integer flags, integer link)`

`ibase_trans`函数返回一个事务标识符。`flags`可以是表13.5列出的常量的任意组合。使用`|`来组合它们。`IBA_DEFAULT`匹配InterBase的读、写、快照和等待属性。如果省略了该项，将使用最后一个连接。

| 表13.5. InterBase常量 |
| --- |
| `IBASE_COMMITTED` |
| `IBASE_CONSISTENCY` |
| `IBASE_DEFAULT` |
| `IBASE_NOWAIT` |
| `IBASE_READ` |
| `IBASE_TEXT` |
| `IBASE_TIMESTAMP` |

# mSQL

本节中的函数与mSQL通信，mSQL是一个实现了SQL子集的数据库。官方网站为`http://www.hughes.com.au/`。mSQL的支持Windows版本位于`http://blnet.com/msqlpc/`。

有少量mSQL函数仅是为了向后兼容而存在。我们选择保留它们。其中只有一些在PHP3官方手册中有记录。参考函数包括`msql`、`msql_createdb`、`msql_dbname`、`msql_dropdb`、`msql_freeresult`、`msql_listdbs`、`msql_list-fields`、`msql_listtables`、`msql_numfields`、`msql_numrows`、`msql_selectdb`、`msql_tablename`。

# PHP核心编程

两个MySQL扩展，分别对应MySQL版本1和版本2。你必须加载相应的扩展以启用本节中的函数。Zeev Suraski编写了这两个mSQL扩展。

# `mysql_affected_rows(integer link)`

`mysql_affected_rows`函数返回链接上提供的之前的查询所涉及的行数。`link`参数必须由`mysql_connect`或`mysql_pconnect`返回的整数。用法示例请参见下方的`mysql_db_query`。

# `boolean mysql_close(integer link)`

`mysql_close`函数关闭与数据库的链接。如果省略`link`参数，则关闭最后一个打开的链接。只有通过`mysql_connect`打开的链接才能关闭。使用此函数并非绝对必要，因为非持久性链接在脚本结束时会自动关闭。用法示例请参见下方的`mysql_db_query`。

# `integer mysql_connect(string host, string username, string password)`

`mysql_connect`函数尝试连接指定`host`的MySQL服务器。如果省略`host`参数，将假设为本地主机。如果存在打开的链接，将返回该标识符而不是建立第二个链接。连接将在脚本结束时自动关闭。

你可以在`host`参数中添加冒号和端口号。

# `boolean mysql_create_db(string database, integer link)`

`mysql_create_db`函数尝试创建一个数据库。`link`参数是可选的。如果省略，将使用最后一个打开的链接。

```php
<? 
$Link = mysql_connect("mysql.clearink.com");
mysql_create_db("store", $Link);
mysql_close($Link);
?>
```

# `boolean mysql_data_seek(integer result, integer row)`

使用`mysql_data_seek`将内部行指针移动到结果集中的指定行。`result`参数由`mysql_query`返回。

```php
? 
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);
```

```php
$Result = mysql_query("SELECT Name FROM customer", $Link);
```

```php
// 跳到第十个客户
mysql_data_seek($Result, 10);
```

```php
$Row = mysql_fetch_row($Result);
```

```php
print($Row[0]);
```

```php
mysql_close($Link);
?>
```

# `integer mysql_db_query(string database, string query, integer link)`

`mysql_db_query`函数与`mysql_query`相同，不同在于它指定了数据库，而不是通过`mysql_select_db`使用数据库。查询在指定的数据库中执行并返回结果。

```php
<? 
$Link = mysql_connect("mysql.clearink.com");
$Query = "DELETE FROM customer";
$Result = mysql_db_query("store", $Query, $Link);
$RowsAffected = mysql_affected_rows($Link);
print($RowsAffected . " rows deleted.");
mysql_close($Link);
?>
```

# `boolean mysql_drop_db(string database, integer link)`

`mysql_drop_db`函数从服务器上删除整个数据库。`link`参数是可选的，如果省略，将使用已打开的连接。

```php
<? 
$Link = mysql_connect("mysql.clearink.com");
if(mysql_drop_db("store", $Link)) {
    print("Database deleted!");
} else {
    print("Database deleted!");
}
print(mysql_error());
mysql_close($Link);
?>
```

# `string mysql_error()`

使用`mysql_error`获取错误信息。参见`mysql_query`的用法。

# `array mysql_fetch_array(integer result, integer type)`

`mysql_fetch_array`函数返回一个包含当前行数据的数组。`type`参数控制返回格式：`MYSQL_NUM`以数字返回列；`MYSQL_ASSOC`以名称返回列；`MYSQL_BOTH`同时返回两者。将此函数与`mysql_fetch_row`和`mysql_fetch_object`进行比较。

```php
<?php
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);
$Query = "SELECT * FROM customer";
$Result = mysql_query($Query, $Link);
// 获取行
while($Row = mysql_fetch_array($Result, MYSQL_ASSOC)) {
    print($Row["FirstName"]);
}
mysql_close($Link);
?>
```

# `object mysql_field(integer result, field)`

`mysql_field`函数返回一个包含字段描述信息的对象。`field`参数可以省略，将返回指定的字段。对象的属性见`mysql_field`属性。

```php
<? 
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);
$Query = "SELECT * FROM item ";
$Query .= "WHERE SKU = id";
$Result = mysql_query($Query, $Link);
// 获取字段描述
while($Field = mysql_field($Result)) {
    print($Field->name . "\n");
    print($Field->table . "\n");
    print($Field->not_null . "\n");
    print($Field->primary_key . "\n");
    print($Field->unique . "\n");
    print($Field->type . "\n");
}
mysql_close($Link);
?>
```

表13.6. `mysql_field`对象属性

| 属性 | 描述 |
|---|---|
| `name` | 列名 |
| `not_null` | 如果列为空为TRUE |
| `primary_key` | 如果为主键为TRUE |
| `table` | 字段所属的表 |
| `type` | 字段类型 |
| `unique` | 如果是唯一为TRUE |

# `object mysql_fetch_object(integer result)`

`mysql_fetch_object`返回一个对象，其中每个属性对应结果中的每一列。每次调用`mysql_fetch_object`获取下一行，如果没有更多行则返回`FALSE`。

```php
<?php
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);
$Query = "SELECT * FROM item";
$Result = mysql_query($Query, $Link);
while($Row = mysql_fetch_object($Result)) {
    print("$Row->ID: " . $Row->Name . "\n");
}
mysql_close($Link);
?>
```

# `array mysql_fetch_row(integer result)`

`mysql_fetch_row`函数返回一个数组，每个元素对应结果中的每一列。没有结果时返回`FALSE`。列通过零开始的整数索引。将此函数与`mysql_fetch_array`和`mysql_fetch_object`进行比较。

```php
<? 
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);
$Query = "SELECT * FROM customer";
$Result = mysql_query($Query, $Link);
while($Row = mysql_fetch_row($Result)) {
    print($Row[0] . ": " . $Row[1] . "\n");
}
mysql_close($Link);
?>
```

# `boolean mysql_field_seek(integer result, integer field)`

使用`mysql_field_seek`将内部字段指针移动到指定的字段。

```php
<? 
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);
// 从第三个开始
mysql_field_seek($Result, 2);
```

# PHP核心编程

``` 
msql_close($Link);
?>
```

# `string msql_fieldflags(integer result, integer field)`

`msql_fieldflags`函数返回为指定字段开启的所有标志。这些标志可能是主键、唯一约束和非空约束。

```php
$Link = msql_connect("msql.clearink.com");
msql_select_db("store", $Link);
$Query = "SELECT * FROM item";
$Result = msql_query($Query, $Link);
print("Field 0 flags are " . msql_fieldflags($Result, 0));
msql_close($Link);
?>
```
