
## 连接到 SQLite

```
@sqlite_open('quotes.db', 0666, $error)
$db = new SQLite3('quotes.db');
```

```php
<?php
if ($db = @sqlite_open('quotes.db', 0666, $error)) {
    echo 'Connected to the database.';
    sqlite_close($db);
} else {
    echo 'Connection failed: ' .
    htmlspecialchars($error);
}
?>
```

*连接到 SQLite (sqlite_open.php)*

从 PHP 5 开始，SQLite 已捆绑在脚本语言中。这是一个轻量级的文件型数据库。这使得读取非常快（在许多情况下，甚至比使用“真实”数据库更快），但写入有时可能比其他系统更慢，因为文件锁定是一个问题。然而，PHP 4 用户也可以使用 SQLite，因为有一个 PECL（PHP 扩展社区库）模块可用 (http://pecl.php.net/)。

如果你使用 PHP 5.0-5.3，SQLite 支持已包含在内。在 PHP 5.4 中，SQLite 扩展（ext/sqlite）已移至 PECL。作为替代方案，PHP 5.4（以及 PHP 5.3）提供了 ext/sqlite3 扩展，本章也涵盖了该扩展。

Windows 用户必须使用（或编译）php_sqlite.dll，将其复制到 PHP 的扩展文件夹中，然后在 php.ini 中使用 extension=php_sqlite.dll 加载 ext/sqlite 或使用 extension=php_sqlite3.dll 加载 ext/sqlite3。

使用 ext/sqlite 时，你可以使用 sqlite_open() 连接到 SQLite 数据源。第一个参数提供数据库文件名；如果文件尚不存在，则会创建它。为此，PHP 进程需要对该文件具有读写权限。第二个参数是文件打开模式（推荐 0666）；然而，截至本文撰写时，该参数被忽略。第三个参数是一个包含任何错误消息的变量（例如权限不足）。

**注意：** 就像 ext/mysqli 一样，PHP 5 下的 SQLite 扩展也可以使用面向对象编程（OOP）方法访问：

```php
<?php
$db = new SQLiteDatabase('quotes.db');
echo 'Connected to the database.';
$db->close();
?>
```

为了向后兼容，本章在后续内容中使用函数式方法。

ext/sqlite3 扩展使用强制性的面向对象应用程序编程接口（API）。在这里，SQLite3 类的 open() 方法会打开数据库文件。由于无论如何都需要实例化该类，更快捷的方法是在类构造函数中提供文件名，这同样会打开数据库。错误处理可以通过 try-catch 块实现：

```php
<?php
    try {
        $db = new SQLite3('quotes.db');
        echo 'Connected to the database.';
        $db->close();
    } catch ($ex) {
        echo 'An error has occurred.';
    }
?>
```

*连接到 SQLite3 (sqlite3_open.php)*

## 向 SQLite 发送 SQL

```
SQLite3 METHOD
$db->exec()
```

```php
<?php
    if ($db = @sqlite_open('quotes.db', 0666, $error))
    {
        sqlite_exec($db, sprintf(
            'INSERT INTO quotes (quote, author, year)
VALUES (\'%s\', \'%s\', \'%s\')',
            sqlite_escape_string($_POST['quote']),
            sqlite_escape_string($_POST['author']),
            intval($_POST['year'])));
        echo 'Quote saved.';
        sqlite_close($db);
    } else {
        echo 'Connection failed: ' .
        htmlspecialchars($error);
    }
?>
```

*向 SQLite 发送 SQL (sqlite_exec.php; 摘录)*

PHP 函数 sqlite_exec() 使用 ext/sqlite 将 SQL 语句发送到数据库。第一个参数使用由 sqlite_open() 返回的数据库句柄；第二个参数是 SQL 字符串。为了避免 SQL 注入，PHP 函数 sqlite_escape_string() 会转义动态数据中的危险字符。上述代码对此进行了实现，针对的是示例表 quotes，该表也在第 8 章的 MySQL 短语中使用过。

ext/sqlite3 的用户需要执行 SQLite3 类的 exec() 方法：

```php
<?php
try {
    $db = new SQLite3('quotes.db');
    $db->exec(sprintf(
        'INSERT INTO quotes (quote, author, year)
VALUES (\'%s\', \'%s\', \'%s\')',
        $db->escape_string($_POST['quote']),
        $db->escape_string($_POST['author']),
        intval($_POST['year'])));
    echo 'Quote saved.';
    $db->close();
} catch ($ex) {
    echo 'An error has occurred.';
}
?>
```

*向 SQLite3 发送 SQL (sqlite3_exec.php; 摘录)*

**提示：** 如果表包含一个标识列（使用 SQLite 时的数据类型为 INTEGER PRIMARY KEY），在发送 SQL 语句后调用 sqlite_last_insert_rowid() 函数（用于 ext/sqlite）或 lastInsertRowID() 方法（用于 ext/sqlite3）会返回该列对数据库中新条目的值。

## 检索 SQLite 查询结果

```
$result = sqlite_query($db, 'SELECT * FROM quotes');
sqlite_fetch_array($result);
$result = $db->query('SELECT * FROM quotes');
$result->fetchArray();
```

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
try {
    $db = new SQLite3('quotes.db');
    $result = $db->query('SELECT * FROM quotes');
    while ($row = $result->fetchArray()) {
        printf(
            '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            htmlspecialchars($row['id']),
            htmlspecialchars($row['quote']),
            htmlspecialchars($row['author']),
            htmlspecialchars($row['year'])
        );
    }
    $db->close();
} catch ($ex) {
    echo 'An error has occurred.';
}
?>
</table>
```

*从 SQLite3 检索数据 (sqlite3_fetch.php; 摘录)*

上一节中的函数 sqlite_exec() 和方法 exec() 执行非常快；然而，不可能访问通过它发送的 SQL 语句的返回值。为此，必须使用 sqlite_query()（ext/sqlite）或 query()（ext/sqlite3）。此函数或方法返回查询结果集的句柄。然后可以使用以下函数和方法遍历结果集：

- sqlite_fetch_array() 函数和 fetchArray() 方法以关联数组的形式返回结果集中当前行（字段名变为键），并前进到下一行。
- sqlite_fetch_object()（ext/sqlite3 中没有等价物）以对象的形式返回结果集中当前行（字段名变为属性），并前进到下一行。
- sqlite_fetch_all()（同样，ext/sqlite3 中没有等价物）以关联数组的数组形式返回完整的结果集。

上述列表展示了如何使用 fetchArray() 方法访问结果集中的所有数据；以下代码大致做同样的事情，这次使用 sqlite_fetch_object()。while 循环只要该方法或函数返回的值不是 false（表示没有剩余数据）就会调用它：

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
if ($db = @sqlite_open('quotes.db', 0666, $error))
{
    $result = sqlite_query($db, 'SELECT * FROM
    quotes');
    while ($row = sqlite_fetch_object($result)) {
        printf(
            '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s
</td></tr>',
            htmlspecialchars($row->id),
            htmlspecialchars($row->quote),
            htmlspecialchars($row->author),
            htmlspecialchars($row->year)
        );
    }
    sqlite_close($db);
} else {
printf('<tr><td colspan="4">Connection failed:
%s</td></tr>',
htmlspecialchars($error));
}
?>
</table>
```

*从 SQLite 检索数据 (sqlite_fetch.php; 摘录)*

**提示：** 使用 sqlite_fetch_all() 会将整个结果集同时读入内存。如果你使用 ext/sqlite，请注意 ext/sqlite3 不支持此功能。因此，如果数据量不大，这是性能最好的方法。如果数据量较大，使用 sqlite_fetch_array() 和 sqlite_fetch_object() 的迭代方法可能更好。

## 使用 SQLite 预处理语句

```
$stmt = $db->prepare('INSERT INTO quotes (quote, author, year) VALUES (:quote, :author, :year)');
$stmt->bindParam(':quote', ...);
```

```php
<?php
try {
    $db = new SQLite3('quotes.db');
    $stmt = $db->prepare('INSERT INTO quotes (quote,
author, year) VALUES (:quote, :author, :year)');
    $stmt->bindValue(':quote', $_POST['quote'],
SQLITE3_TEXT);
    $stmt->bindValue(':author', $_POST['author'],
SQLITE3_TEXT);
    $stmt->bindValue(':year',
intval($_POST['year']), SQLITE3_INTEGER);
    $db->close();
} catch ($ex) {
    echo 'An error has occurred.';
}
?>
```

*使用 SQLite3 预处理语句 (sqlite3_prepare.php; 摘录)*

预处理语句通过在 SQL 中支持占位符，将 SQL 命令与数据分离。在第二步中，可以为这些占位符分配值。

使用 ext/sqlite3 时，可以使用预处理语句。第一步中，prepare() 方法创建一个表示语句的 SQLite3Stmt 对象。占位符由冒号和占位符名称表示：

```
$stmt = $db->prepare('INSERT INTO quotes (quote, author, year) VALUES (:quote, :author, :year)');
```

然后，语句对象的 bindValue() 方法为特定占位符分配值。你提供占位符的名称、要分配的值以及要使用的数据类型：

```
$stmt->bindValue(':quote', $_POST['quote'], SQLITE3_TEXT);
```
