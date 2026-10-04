

# 附录 G：实用的自定义函数

```php
$str .= "$col-$val";
}
elif($val=="NULL" || $val=="null") {
  $str .= "$col-NULL";
} else {
  $str .= "$col='$val'";
}

$str = substr($str, 0, -1);
$query = "update $table set $str";
if (empty($where)) {
  $query .= " where $where";
}
mysql_query($query) or die (mysql_error());
return mysql_affected_rows();
```

该函数接受三个参数：$table，一个字符串；$atts，包含列名键和要插入值的关联数组；以及 $where，即条件，例如 (column_id = 1)。
再次强调，该函数的健壮性不足以在所有情况下运行。

# delete_row()

该函数接受两个参数：$table，表名，以及 $where，where 子句中的值。在执行失败时返回 false，如果没有删除任何内容，则返回 0。

```php
function delete_row($table="", $where="") {
  if (empty($table) || empty($where)) {
    return FALSE;
  }
  $query = "delete from $table where $where";
  mysql_query($query) or die (mysql_error());
  return mysql_affected_rows();
}
```

# Function select_to_table()

该函数接受一个查询并以简单的 HTML 表格形式布局。它假设已经建立了数据库连接。

```php
function select_to_table($query)
{
$result=mysql_query($query);
$number_cols = mysql_num_fields($result);
echo "<b>" . $query . "</b>";
// table header
echo "<table border = 1\n";
echo "<tr align=center>\n";
for ($i=0; $i<$number_cols; $i++) {
	echo "<th>" . $mysql_field_name($result, $i) . "</th>\n";
}
echo "</tr>\n";
// end of table header
// table body
while ($row = mysql_fetch_row($result)) {
	echo "<tr align=left\n";
for ($i=0; $i<$number_cols; $i++) {
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
}
	echo "</tr>\n";
}
echo "</table>";
}
```

# enum_to_array()

该函数将 enum 字段中定义值返回到数组中。

```php
function enum_to_array($table="", $col = "")
{
	if (empty($table) || empty($col))
{ return False; }
else {
$query = "describe stable $col";
$result = mysql_query($query);
list(0, $col) = mysql_fetch_array($result);
echo $col;
if (substr($col, 0, 4) != "enum") {
  return FALSE;
}
$col = str_replace("*", "", substr($col, 5, -1));
$col = explode(",", $col);
}
return $col;
```

你可以使用 MySQL 中的 enum 字段类型来限制列中的可能值。这对于将列值限制为 Y 或 N 等非常有帮助。但要在 PHP 中获取这些值，你需要运行其中一个获取列信息的 MySQL 查询语句。在上一个的示例中，我使用了 `describe` 查询，并假设感兴趣的列将包含在查询中。
该查询返回 6 列。按顺序为：Field, Type, Null, Default 和 Extra。第二列 Type 包含了列类型——类似于 `enum('yes','no')` 的内容。在前面的函数中，此值被赋值给 $col。该字符串随后可以去掉多余的括号和字母 enum。剩余部分被拆分为一个数组。

然后你可以按照需要的方式使用该数组，例如在下拉框中。

# 使用 MySQL 处理会话

如果你想使用此功能，请在 php.ini 中将 `session.save_handler` 设置为 `user`。这组函数旨在用于类似下面的表：

```sql
create table sessions(
  session_id char(32) not null primary key,
  sess_data text,
  last_update timestamp)
```

```php
function mysql_session_open() {
  mysql_connect("localhost", "root", "");
  or die (mysql_error());
  $db_sess = mysql_select_db("test") or die (mysql_error());
}
```

```php
//此函数接收 session_id 作为唯一参数
function mysql_session_read($id)
{
    $data = "";
    $query = "select sess_data from sessions\n    where session_id = '$id'";
    $result = mysql_query($query) or die (mysql_error());
    if ($row = mysql_fetch_row($result))
{
        $data = session_decode($row[0]);
        return $data;
    }
}
```

```php
//此函数接收 sessionid 和会话数据
// 作为参数
function mysql_session_write($id, $data)
{
    $data = session_encode($data);
    $query = "replace into sessions (session_id, sess_data)\n    values ('$id', '$data')";
    mysql_query($query) or
    die(mysql_error());
    return true;
}
```

```php
function mysql_session_close()
{
    return true;
}
```

```php
// 仅接收 session id 作为参数
function mysql_session_destroy($id)
{
    $query = "delete from sessions where session_id = '$id'";
    mysql_query($query) or
    die(mysql_error());
    return true;
}
```

```php
//此函数接收来自 php.ini 的
// 最大生命周期设置。默认设置为 1440 秒。
// php.ini 中的 session.gc_probability 设置决定了
// 此函数运行的时间百分比。
function mysql_session_gc($time)
{
    $query = "delete from sessions where
    last_update < ( subdate(now(),
    INTERVAL $time SECOND))";
    mysql_query($query) or
        die(mysql_error());
}
session_set_save_handler(
    "mysql_session_open",
    "mysql_session_close",
    "mysql_session_read",
    "mysql_session_write",
    "mysql_session_destroy",
    "mysql_session_gc"
);
```

# MySQL 备份

Dan Noberoski 编写了此脚本，我原本计划包含在内。但对于打印格式来说太长了。我建议你访问他的网站查看。

