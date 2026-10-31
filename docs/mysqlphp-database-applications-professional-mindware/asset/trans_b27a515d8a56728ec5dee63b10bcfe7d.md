
## CHECKBOX_FIELD()

这个函数返回一个 HTML 复选框字段。可选的第三个参数将紧跟在复选框字段之后，并且这对内容包含在 HTML <nobr> 标签内——意味着它们将一起显示在同一行。如果第二个或第三个参数的值与第四个参数的值匹配，则复选框将被‘checked’（即打开）。

```
string checkbox_field ([string name [, string value [, string label [, string match]]]])
```

## RADIO_FIELD()

这个函数返回一个 HTML 单选按钮字段。可选的第三个参数将紧跟在单选按钮之后，并且这对内容包含在 HTML <nobr> 标签内——意味着它们将一起显示在同一行。如果第二个或第三个参数的值与第四个参数的值匹配，则单选按钮将被‘checked’（即打开）。

```
string radio_field ([string name [, string value [, string label [, string match]]]])
```

## SELECT_FIELD()

这个函数返回一个 HTML 选择字段（弹出字段）。如果可选的第二个参数是一个数组，则数组中的每个键将设置为选择字段的选项的值，而数组中对应的值将是该选项的显示字符串。如果数组中的键或值与可选的第三个参数匹配，则该选项将被指定为选择字段的默认值。

```
string select_field ([string name [, array items [, string default value]]])
```

## DB_SELECT_FIELD()

这个函数返回一个 HTML 选择字段（弹出字段），基于第二个参数指定的 MySQL 数据库表中的值，由 db_values_array() 函数返回（之前已定义）。

```
string db_select_field ([string name [, string table name [, string value field [, string label field [, string sort field [, string match text [, string where clause]]]]]]])
```

## DB_RADIO_FIELD()

这个函数返回一系列 HTML 单选按钮字段，以不间断空格 HTML 实体（&nbsp;）和换行符分隔，基于第二个参数命名的 MySQL 数据库表中的值，由 db_values_array() 函数返回（之前已定义）。

```
string db_radio_field (string name, string table name, string value field, string label field, string sort field, [string match text], [string where clause])
```

## From functions/tables.php

这些函数创建开始和结束的 <table> 标签，以及 <tr> 和 <td> 标签。

## START_TABLE()

这个函数返回一个开始的 HTML <table> 标签，位于开始的段落（<p>）标签内。表的属性可以作为数组提供。

```
string start_table([array attributes])
```

## END_TABLE()

这个函数返回一个关闭表格的标签。

```
string end_table(void)
```

## TABLE_ROW()

这个函数返回一个 HTML 表格行（<tr>）标签，包含可变数量的表格单元格（<td>）标签。如果函数的任何参数是数组，它将被用作 <tr> 标签的属性。所有其他参数将用作该行单元格的值。如果参数以 <td> 标签开头，则参数按原样添加到行中。否则它将传递给 table_cell() 函数，并将生成的字符串添加到行中。

```
string table_row ([array attributes], [indefinite number of string arguments])
```

## TABLE_CELL()

这个函数返回一个 HTML 表格单元格（<td>）标签。第一个参数将用作标签的值。 <td> 标签的属性可以在第二个参数中作为数组提供。默认情况下，表格单元格水平左对齐，垂直顶部对齐。

```
string table_cell ([string value [, array attributes]])
```

## Additional Functions Not Used in this Book

这里有一些函数，可能会使处理常见查询变得更容易一些。

## insert_row()

这是一个用于运行 SQL 插入语句的通用函数。

```
function insert_row($table="", $atts="")
{
    if(empty($table) || !is_array($atts))
    {
        return false;
    }
    else
    {
        while (list ($col, $val) = each ($atts))
        {
            //if null go to the next array item
            if ($val=="")
            {
                continue;
            }
            $col_str .= $col . ",";
            if (is_int($val) || is_double ($val))
            {
                $val_str .= $val . ",";
            }
            else
            {
                $val_str .= "'$val',";
            }
        }
        $query = "insert into $table
            ($col_str)
            values($val_str)";
        //trim trailing comma from both strings
        $query = str_replace(",", "", $query);
    }
    safe_query($query);

    return mysql_affected_rows();
}
```

这个函数接受两个属性：第一个是表名，第二个应该是关联数组，其键为列名，值为要插入的值。如果变量不是整数或双精度，则应围绕字符串的单引号将被包含。如果查询未能执行操作，则函数返回 FALSE。它在所有情况下都无法工作，因为它不会检查数据库中的列类型。但它对于快速创建页面来说可能很不错。

数组中的空值不会添加到查询中。对于查询中省略的列，MySQL 将插入空值或空字符串，具体取决于列是否允许空值。

请注意，您可以使用 compact() 函数从一组变量创建关联数组。例如，以下内容将创建一个名为 $array 的关联数组，然后将一行插入到名为 mytable 的表中。假设您已经连接到数据库

```php
$category="";
$category_id=6;
$category_name="my category";
$array=compact("category", "category_id", "category_name");
if (!insert_row("mytable", $array))
{
    echo "insert failed";
}
```

## update_row()

该函数将执行 SQL 更新语句

```php
function update_row($table="", $atts="", $where="")
{
    if(empty($table) || !is_array($atts))
    {
        return FALSE;
    }
    else
    {
        while(list ($col, $val) = each ($atts))
        {
            if ($val=="")
            {
                continue;
            }
            if(is_int($val) || is_double($val))
            {
$str .= "$col=$val,";
}
elseif($val=="NULL" || $val=="null")
{
    $str .= "$col=NULL,";
}
else
{
    $str .= "$col='$val',";
}
}
}
$str = substr($str, 0, -1);
$query = "update $table set $str";
if (!empty($where))
{
    $query .= " where $where";
}
mysql_query($query) or
    die (mysql_error());
return mysql_affected_rows();
}
```

这个函数接受三个参数：$table，一个字符串；$atts，一个关联数组，包含列名键和要插入的值的值；以及 $where，即条件，例如 (column_id = 1)。

再次说明，这不够健壮，无法在所有情况下工作。

## delete_row()

这个函数接受两个参数：$table，表名，以及 $where，where 子句中的值。失败时返回 false，如果未删除任何内容则返回 0。

```
function delete_row($table="", $where="")
{
    if (empty($table) || empty($where))
    {
        return FALSE;
    }
    $query = "delete from $table where $where";
    mysql_query($query) or die (mysql_error());
    return mysql_affected_rows();
}
```

## Function select_to_table()

这个函数接受一个查询并将其布局在简单的 HTML 表格中。它假设已经建立了数据库连接。

```
function select_to_table($query)
{
    $result=mysql_query($query);
    $number_cols = mysql_num_fields($result);
    echo "<b>query: $query</b>";
    //layout table header
    echo "<table border = 1>\n";
    echo "<tr align=center>\n";
    for ($i=0; $i<$number_cols; $i++)
    {
        echo "<th>". mysql_field_name($result, $i). "</th>\n";
    }
    echo "</tr>\n";//end table header
    //layout table body
    while ($row = mysql_fetch_row($result))
    {
        echo "<tr align=left>\n";
        for ($i=0; $i<$number_cols; $i++)
        {
            echo "<td>";
            if (!isset($row[$i])) //test for null value
            {
                echo "NULL";
            }
            else
            {
                echo $row[$i];
            }
            echo "</td>\n";
        } echo "</tr>\n";
    } echo "</table>";
}
```

## enum_to_array()

这个函数将枚举字段中定义的值返回到数组中。

```
function enum_to_array($table="", $col = "")
{
    if (empty($table) || empty($col))
```
