

# PHP 核心编程

```
msql_close($Link);
?>
```

# string msql_fieldflags(integer result, integer field)

msql_fieldflags 函数返回为指定字段开启的所有标志。这些标志可能是主键、唯一约束和非空约束。

```php
$Link = msql_connect("msql.clearink.com");
msql_select_db("store", $Link);

$Query = "SELECT * FROM item";
$Result = msql_query($Query, $Link);
print("Field 0 flags are " . msql_fieldflags($Result, 0));

msql_close($Link);
?>
```

# integer msql_fieldlen(integer result, integer field)

msql_fieldlen 函数返回指定字段的长度。

```php
$Link = msql_connect("msql.clearink.com");
msql_select_db("store", $Link);

$Query = "SELECT * FROM item";
$Result = msql_query($Query, $Link);

print("Field 0 length is " . msql_fieldlen($Result, 0));

msql_close($Link);
?>
```

# string msql_fieldname(integer result, integer field)

msql_fieldname 函数返回指定字段的名字。

```php
$Link = msql_connect("msql.clearink.com");
msql_select_db("store", $Link);

$Query = "SELECT * FROM item";
$Result = mysql_query($Query, $Link);
print("Field 0 is " . mysql_fieldname($Result, 0));
msql_close($Link);
?>
```

# string mysql_fieldtable(integer result, integer field)

mysql_fieldtable 函数返回指定字段的表名。

```php
<?php
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);

$Query = "SELECT * FROM item";
$Result = mysql_query($Query, $Link);

print("Field 0 is from " . mysql_fieldtable($Result, 0));
mysql_close($Link);
?>
```

# string mysql_fieldtype(integer result, integer field)

mysql_fieldtype 函数返回指定字段的类型。

```php
<?php
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);

$Query = "SELECT * FROM item";
$Result = mysql_query($Query, $Link);

print("Field 0 is " . mysql_fieldtype($Result, 0));

mysql_close($Link);
?>
```

# boolean mysql_free_result(integer result)

当脚本结束时，所有结果都会释放。如果你的脚本运行存在内存问题，请使用 mysql_free_result。

```php
<?
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);

$Query = "INSERT INTO store VALUES (0, 'Martinez')";
$Result = mysql_query($Query, $Link);

mysql_free_result($Result);

mysql_close($Link);
?>
```

# integer mysql_list_dbs(integer link)

mysql_list_dbs 函数返回一个结果标识符，就像使用 mysql_query 查询数据库一样。可以使用获取行或字段的任何函数来获取数据库名称。link 参数是可选的。如果遗留，将使用最后一个打开的连接。

```php
<?
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);

$Result = mysql_list_dbs($Link);
while($row_array = mysql_fetch_row($Result))
{
    print($row_array[0] . "<BR>\n");
}

mysql_close($Link);
?>
```

# integer mysql_list_fields(string database, string tablename, integer link)

mysql_list_fields 函数返回一个结果标识符，就像使用 mysql_query 查询数据库一样。可以使用获取行或字段的任何函数来获取字段名称。link 参数是可选的。如果遗留，将使用最后一个打开的连接。

```php
<?
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);

$Result = mysql_list_fields("store", "item", $Link);
while($row_array = mysql_fetch_row($Result))
{
    print($row_array[0]) . "<BR\n";
}
mysql_close($Link);
```

# integer mysql_list_tables(string database, integer link)

mysql_list_tables 函数返回一个结果标识符，就像使用 mysql_query 查询数据库一样。可以使用获取行或字段的任何函数来获取字段名称。link 参数是可选的。如果遗留，将使用最后一个打开的连接。

```php
<?
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);
$Result = mysql_list_tables("store", $Link);
while($row_array = mysql_fetch_row($Result)) {
    print($row_array[0]) . "<BR\n";
}
mysql_close($Link);
```

# integer mysql_num_fields(integer result)

使用 mysql_num_fields 获取结果集中的字段数量。

```php
<?
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);
$Query = "SELECT * FROM item i, SKU s ";
$Query .= "WHERE i.SKU = s.ID";
$Result = mysql_query($Query, $Link);

print(mysql_num_fields($Result));
mysql_close($Link);
```

# integer mysql_num_rows(integer result)

mysql_num_rows 函数返回结果集中的行数。

```php
<?
$Link = mysql_connect("mysql.clearink.com");
mysql_select_db("store", $Link);

$Query = "SELECT * FROM item i, s s";
$Query .= "WHERE i.SKU = s.ID ";
$Result = mysql_query($Query, $Link);

print(mysql_num_rows($Result));

mysql_close($Link);
?>
```

# integer msql_pconnect(string host)

msql_pconnect 函数与 msql_connect 相同，不同之处脚本结束时连接不会关闭。这仅在 PHP 编译为 Apache 模块时才有意义。这些是持久链接，因为它们与服务器进程一样存在。

```php
<?
$Link = msql_pconnect("localhost");
?>
```

# integer msql_query(string query, integer link)

使用 msql_query 执行查询。使用的数据库将调用 msql_select_db 函数时指定的数据库。link 参数是可选的。如果遗留，将使用最后建立的连接。

# msql_regcase

这是 msql_regcase 的别名，在第 9 章“数据函数”中有描述。

# string msql_result(integer result, integer row, string field)

msql_result 函数返回给定行的单个字段值。field 参数可以有两种解释方式。如果它是一个数字，它将用作字段偏移量，从零开始。否则，将被视为列名。msql_result 函数相对较慢。应该避免使用它，转而使用更快的函数，如 msql_fetch_array。

```php
<?php
$Link = msql_connect("msql.clearink.com");
msql_select_db("store", $Link);

$Query = "SELECT * FROM item i, s s";
$Query .= "WHERE i.SKU = s.ID";
$Result = msql_query($Query, $Link);

$numRows = msql_num_rows($Result);

for($index = 0; $index < $numRows; $index++) {
    $item_ID = msql_result($Result, $index, "item.ID");
    $item_Name = msql_result($Result, $index, "item.Name");

    print("$item_ID: $item_Name<BR>\n");
}

msql_close($Link);
?>
```

