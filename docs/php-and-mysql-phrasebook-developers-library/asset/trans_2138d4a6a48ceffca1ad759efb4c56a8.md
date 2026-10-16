
```php
htmlspecialchars($row->YEAR)
);
}
oci_close($db);
} else {
echo '<tr><td colspan="4">Connection failed.</td></tr>';
}
?>
</table>
```

从 Oracle 检索数据 (oci_fetch.php; 摘录)

你有多种方式访问 SQL 查询的返回值，但以下函数在实践中最常使用：

- oci_fetch_assoc() 返回结果集中当前行作为关联数组。
- oci_fetch_object() 返回结果集中当前行作为对象。
- oci_fetch_row() 返回结果集中当前行作为数字数组。
- oci_fetch_all() 将完整的结果集作为关联数组的数组返回。然而，需要五个参数：来自 oci_parse() 的语句对象、用于返回数据的数组、要跳过的行数、要返回的最大行数（-1 表示无限），以及返回数字 (OCI_NUM) 还是关联 (OCI_ASSOC) 数组。

本节中的示例使用 while 循环和 oci_fetch_object() 来检索表中的所有数据。

## 第 9 章 使用其他数据库

注意：Oracle 总是以大写返回列名。因此，在访问 SQL 查询的返回值时，你必须使用大写对象属性或大写关联数组键。

```php
<?php
$config = array('UID' => 'user', 'PWD' =>
'password',
'Database' => 'phrasebook');
if ($db = @sqlsrv_connect('localhost\SQLExpress',
$config)) {
	echo 'Connected to the database.';
	sqlsrv_close($db);
} else {
	echo 'Connection failed.';
}
?>
```

Microsoft SQL 引擎有两种版本：功能齐全（价格也全）的 Microsoft SQL Server（简称：MSSQL）和免费版 Microsoft SQL Server Express Edition，可在 www.microsoft.com/sqlserver/en/us/editions/express.aspx 免费获取。PHP 支持这两个版本，因为它们彼此兼容。

PHP 附带了用于 MSSQL 的扩展 ext/mssql。然而它相当老旧且不再积极维护。相反，Microsoft 提供了一个新的（仅限 Windows）扩展 ext/sqlsrv，这是推荐使用的。

要使其工作，你需要在 php.ini 中使用 extension=<filename>.dll 添加扩展。此外，你还需要扩展本身。根据你使用的 PHP 版本，需要特定版本。PHP 手册页面 http://php.net/sqlsrv.installation 会指向正确的下载页面。如果可能，你应至少使用扩展的版本 3，它使用 Microsoft SQL Server 2012 Native Client 库；版本 2 需要 Microsoft SQL Server 2008 R2 Native Client 库。Microsoft 在 http://msdn.microsoft.com/en-us/library/cc296170.aspx 描述了最新的系统要求。

要连接到 MSSQL，调用 mssql_connect() 并提供服务器名称（(local) 可作为 localhost 的快捷方式）；如果你使用的是 Microsoft SQL Server 的命名实例（例如 SQLEXPRESS，默认随 MSSQL Express Edition 安装），则将其附加到服务器名称后，用反斜杠分隔：(local)\SQLEXPRESS。作为第二个参数，你可以提供一个包含连接信息的数组。扩展支持以下数组键：

- Database—数据库名称
- PWD—密码
- UID—用户名

如果你想使用当前用户（有时也称为受信任连接）对数据库进行身份验证，只需省略 UID 和 PWD 配置设置即可。

### 向 MSSQL 发送 SQL

```php
<?php
$config = array('UID' => 'user', 'PWD' =>
'password', 'Database' => 'phrasebook');
if ($db = @sqlsrv_connect('localhost\SQLEXPRESS')) {
ini_set('magic_quotes_sybase', 'On');
sqlsrv_query($db, sprintf(
"INSERT INTO quotes (quote, author, year) VALUES (\'%s\', \'%s\', \'%s\')",
addslashes($_POST["quote"]),
addslashes($_POST["author"]),
intval($_POST["year"])));
echo 'Quote saved.';
sqlsrv_close($db);
} else {
echo 'Connection failed.';
}
?>
```

向 MSSQL 发送 SQL (sqlsrv.execute.php; 摘录)

函数 sqlsrv_query() 将 SQL 语句发送到 MSSQL 安装。其参数顺序与 ext/mysql 类似：首先是数据库句柄，然后是 SQL 命令。

另一个重要点是转义特殊字符。在 MSSQL 中，单引号不应使用反斜杠转义，而应使用双引号：

INSERT INTO quotes (quote, author, year) VALUES ('Ain\'t Misbehavin\'', 'Louis Armstrong', 1929)

为此，你可以使用 addslashes()。不过，首先必须对其进行配置，使其返回 MSSQL/MSDE 兼容的字符串：

```php
ini_set('magic_quotes_sybase', 'On');
$author = addslashes($_POST['author']);
```

不过要提醒一点：magic_quotes_sybase 设置在 PHP 5.3 中已弃用，并在 PHP 5.4 中移除。如果你要在 SQL 语句中使用用户信息，应改用预处理语句（两节之后）。本节开头的示例对一些表单数据进行了清理并写入了（到现在为止）众所周知的示例数据库。

### 检索 MSSQL 查询结果

```php
$result = sqlsrv_query();
sqlsrv_fetch_object($result);
```

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
$config = array('UID' => 'user', 'PWD' => 'password', 'Database' => 'phrasebook');
if ($db = @sqlsrv_connect('(local)\SQLEXPRESS', $config)) {
    $result = sqlsrv_query($db, 'SELECT * FROM quotes');
    while ($obj = sqlsrv_fetch_object($result)) {
        printf(
```

```php
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s
</td></tr>',
htmlspecialchars($row->id),
htmlspecialchars($row->quote),
htmlspecialchars($row->author),
htmlspecialchars($row->year)
);
sqlsrv_close($db);
} else {
echo '<tr><td colspan="4">Connection
failed.</td></tr>';
}
?>
</table>
```

*从 MSSQL 检索数据 (sqlsrv_fetch.php; 摘录)*

最后，当然也有一种方法可以检索结果集中的所有数据。while 循环会派上用场，使用以下其中一个函数：

- sqlsrv_fetch_array() 将结果集中当前行作为关联数组和/或数字索引数组返回；默认情况下，它返回两者。
- sqlsrv_fetch_object() 将结果集中当前行作为对象返回。

### 使用 MSSQL 预处理语句

```php
$stmt = sqlsrv_query();
sqlsrv_execute($stmt);
```

```php
<?php

$config = array('UID' => 'user', 'PWD' => 'phrasebook', 'Database' => 'phrasebook');
if ($db = @sqlsrv_connect('(local)\SQLEXPRESS', $config)) {
    $year_as_int = intval($_POST['year']);
    $data = array(&$_POST['quote'], &$_POST['author'], &$year_as_int);
    $stmt = sqlsrv_query(
        $db,
        'INSERT INTO quotes (quote, author, year)
VALUES (?, ?, ?)',
        $data);
    sqlsrv_execute($stmt);
    echo 'Quote saved.';
    sqlsrv_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

使用预处理语句从 MSSQL 检索数据
(sqlsrv_prepare.php; 摘录)

因为 ext/sqlsrv 中没有指定的转义函数，所以预处理语句是使用用户提供的数据在 SQL 语句中并避免 SQL 注入的唯一可行方法。像往常一样，必须执行两个步骤。首先，你创建一个语句对象（此处使用的函数是带占位符的 sqlsrv_prepare()），然后执行该语句。在准备语句时，你还必须提供占位符的数据。

ext/sqlsrv 扩展期望每个占位符使用一个问号 (?)。这些占位符的值以数组形式提供，其顺序与 SQL 语句中占位符的顺序完全相同。这些值可以按引用传递。

### 在非 Windows 系统上使用 MSSQL

```php
$db = @mssql_connect();
$result = mssql_query();
mssql_fetch_assoc($result);
```

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
if ($db = @mssql_connect('localhost', 'user', 'password')) {
    mssql_select_db('phrasebook', $db);
    $result = mssql_query('SELECT * FROM quotes', $db);
    while ($row = mssql_fetch_assoc($result)) {
        print(
            '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            htmlspecialchars($row['id']),
            htmlspecialchars($row['quote']),
            htmlspecialchars($row['author']),
            htmlspecialchars($row['year'])
        );
    }
    mssql_close($db);
} else {
    echo '<tr><td colspan="4">Connection failed.</td></tr>';
}
?>
</table>
```

*使用 ext/mssql 从 MSSQL 检索数据 (mssql_fetch.php; 摘录)*
