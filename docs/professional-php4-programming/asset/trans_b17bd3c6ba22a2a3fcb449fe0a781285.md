

请注意，默认情况下，pg_fetch_array() 将返回一个同时具有数字索引和关联索引的数组（PGSQL_BOTH）。这会产生一个比所需大两倍的数组，因为每个条目都需要为每种索引类型复制一份。因此，在调用 pg_fetch_array() 时，您应根据代码需求明确请求 PGSQL_NUM 或 PGSQL_ASSOC 中的一种。

## pg_freeresult()

```
int pg_freeresult(int result_id)
```

在上面的示例中，您可能已经注意到 pg_freeresult() 的使用。此函数会释放与给定结果集关联的所有内存。在脚本执行完毕时这会自动发生，但如果您担心复杂脚本中大结果集的内存使用情况，此函数可让您稍作喘息。

## 在线图书馆

现在您已熟悉 PHP 的 PostgreSQL 接口，我们将重新审视上一章中开始的示例应用程序。如果您跳过了那一章，可能需要回去复查该部分。

在本章中，我们将仅关注将现有 MySQL 代码移植为使用 PostgreSQL。

我们将从移植登录屏幕（login.php）开始。让我们重新查看上一章结束时的代码。我们将只关注数据库交互代码：

```
// Connect to the database
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());

mysql_select_db('Library', $conn) or die(mysql_error());

// Query the database
$sql = "SELECT username FROM Users WHERE username = '" .
    $username . "' and password = '" . $password . "'";
$result = mysql_query($sql, $conn);

// Test the query result
$success = false;
if (@mysql_result($result, 0, 0) == $username) {
    $success = true;
}

mysql_close($conn);
```

我们将首先更改数据库连接代码，以连接到 PostgreSQL 数据库而不是 MySQL 数据库。这样就只剩下以下两行：

```
// Connect to the database
$conn = pg_connect('dbname=library user=jon password=secret')
or die(pg_errormessage());
```

现在，我们来处理 SQL 查询代码。由于我们在 SQL 语句中未使用任何 MySQL 特有的结构，唯一需要更改的是将 mysql_query() 改为 pg_exec()：

```
// Query the database
$sql = "SELECT username FROM users WHERE username = '" .
    $username . "' and password = '" . $password . "'";
$result = pg_exec($conn, $sql);
```

结果检查代码也是简单的移植。我们只需使用 pg_result() 代替 mysql_result()：

```
// Test the query result
$success = false;
if (trim(@pg_result($result, 0, 'username')) == $username) {
    $success = true;
}
```

PostgreSQL 会用空格将 CHAR 值填充到其完整长度（在此示例中为 32 个字符）。我们在上一行中添加 trim() 调用以删除这些空格。

最后，我们需要将 mysql_close() 改为 pg_close()：

```
// Close the connection to the database
pg_close($conn);
```

这样就完成了将 login.php 从 MySQL 移植到 PostgreSQL 的工作。不过，我们仍需向 users 表添加一个用户条目：

```
library=# INSERT INTO users VALUES ('jon', 'secret');
INSERT 101831 1
```

我们将继续移植 search.php 脚本。再次，我们将只关注数据库交互代码：

```
// Connect to the MySQL server
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());

// Select the database
mysql_select_db('Library', $conn) or die(mysql_error());

// Query the database for the list of series
$sql = "SELECT series_ID, book_series FROM Series";
$result = mysql_query($sql, $conn);

// Print the <option> rows for the <select> widget
if ($result && (mysql_num_rows($result) > 0)) {
    while ($row = mysql_fetch_assoc($result)) {
        $option = sprintf('<option value="%d">%s</option>',
            $row['series_ID'], $row['book_series']);
        echo("$option\n");
    }
}
} else {
    echo("<option>No series are available</option>\n");
}
mysql_close($conn);
```

我们已经知道如何将 `mysql_connect()`、`mysql_select_db()`、`mysql_query()` 和 `mysql_close()` 函数移植为它们的 PostgreSQL 等效函数。

在这里，我们将只关注结果处理代码。在第一行中，我们只需将对 `mysql_num_rows()` 的调用替换为对 `pg_numrows()` 的调用：

```
if ($result && (pg_numrows($result) > 0)) {
```

下一部分更有趣。没有 `pg_fetch_assoc()` 函数，那么如何移植对 `mysql_fetch_assoc()` 的调用呢？如果我们回头检查 `pg_fetch_array()` 的描述，就会发现它为我们提供了一个关联数组。我们还需要在 PostgreSQL 函数中使用行计数器。

修改后的代码如下：

```
$row_counter = 0;
while ($row = pg_fetch_array($result, $row_counter, PGSQL_ASSOC)) {
    $option = sprintf('<option value="%d">%s</option>',
        $row['series_ID'], $row['book_series']);
    echo("$option\n");
    $row_counter++;
}
```

最后要移植的脚本是 results.php，它显示用户的搜索结果。再次，以下是仅与数据库交互的代码部分：

```
// Connect to the MySQL server
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());

// Select the database
mysql_select_db('Library', $conn) or die(mysql_error());

// Attempt to fetch the form variables
$query = addslashes($HTTP_GET_VARS['query']);
$series = $HTTP_GET_VARS['series'];
$type = $HTTP_GET_VARS['type'];

// Query the database for the list of series
$sql = "SELECT book_title, auth_name, price " .
    "FROM Title, Details, Author, AuthorTitle, Series " .
    "WHERE Author.author_ID = AuthorTitle.auth_ID AND " .
    "AuthorTitle.ISBN = Title.ISBN AND Title.ISBN = Details.ISBN AND " .
    "Details.series_ID = Series.series_ID";

// Add the search terms to the query
if (!empty($series)) {
    $sql .= " AND Series.series_ID = $series";
}
if (!empty($query) && !empty($type)) {
    if ($type == 'isbn') {
        $sql .= " AND Details.ISBN = '$query'";
    } elseif ($type == 'author') {
        $sql .= " AND Author.auth_name LIKE '%$query%'" ;
    } elseif ($type == 'title') {
        $sql .= " AND Title.book_title LIKE '%$query%'";
    }
}

$result = mysql_query($sql, $conn);

// Print the <option> rows for the <select> widget
if ($result && (mysql_num_rows($result) > 0)) {
    while ($row = mysql_fetch_assoc($result)) {
?>
<tr>
<td><u><?php echo(htmlspecialchars($row['book_title'])); ?></u></td>
<td><?php echo(htmlspecialchars($row['auth_name'])); ?></td>
<td><?php echo(htmlspecialchars($row['price'])); ?></td>
</tr>
<?php
    }
} else {
    echo ("<tr><td colspan=\"3\">No matches were found.</td></tr>\n");
}

mysql_close($conn);
```

根据您对前两个脚本的移植经验，您应该已经知道如何将此代码从 MySQL 移植到 PostgreSQL。以下是上述代码的 PostgreSQL 版本：

```
// Connect to the PostgreSQL server
$conn = pg_connect('dbname=library user=jon password=secret')
    or die(pg_errormessage());

// Attempt to fetch the form variables
$query = addslashes($HTTP_GET_VARS['query']);
$series = $HTTP_GET_VARS['series'];
$type = $HTTP_GET_VARS['type'];

// Query the database for the list of series
$sql = "SELECT book_title, auth_name, price " .
    "FROM title, details, author, authorititle, series " .
    "WHERE author.auth_ID = authorititle.auth_ID AND " .
    "authorititle.ISBN = title.ISBN AND ISBN = details.ISBN AND " .
    "details.series_ID = series.series_ID";

// Add the search terms to the query
if (!empty($series)) {
    $sql .= " AND series.series_ID = $series";
}
if (!empty($query) && !empty($type)) {
    if ($type == 'isbn') {
        $sql .= " AND details.ISBN = '$query'";
    } elseif ($type == 'author') {
        $sql .= " AND author.auth_name LIKE '%$query%'";
    } elseif ($type == 'title') {
        $sql .= " AND title.book_title LIKE '%$query%'";
    }
}

$result = pg_exec($conn, $sql);

// Print the <option> rows for the <select> widget
if ($result && (pg_numrows($result) > 0)) {
    $row_counter = 0;
    while ($row = pg_fetch_array($result, $row_counter, PGSQL_ASSOC)) {
?>
<tr>
<td><u><?php echo(htmlspecialchars($row['book_title'])); ?></u></td>
<td><?php echo(htmlspecialchars($row['auth_name'])); ?></td>
<td><?php echo(htmlspecialchars($row['price'])); ?></td>
</tr>
<?php
        $row_counter++;
    }
} else {
    echo("<tr><td colspan=\"3\">No matches were found.</td></tr>\n");
}

pg_close($conn);
```

仅此而已。

### 数据库抽象

在上一章中，我们也构建了一个简单的数据库抽象层。现在我们了解了两种不同的数据库（MySQL 和 PostgreSQL），您可能理解这种抽象层的必要性。我们在前一章中已经讨论过数据库抽象层，因此如果您尚未阅读前一章中的相应部分，现在可能需要阅读。在本节中，我们将重新审视数据库抽象层并实现 PostgreSQL 版本。

我们在上一节中已经了解如何将 PHP 数据库应用程序从一个数据库移植到下一个数据库，因此我们不会再赘述细节。相反，我们将从一个已移植到 PostgreSQL 的 DB.php 文件开始。与 MySQL 版本相比的更改已突出显示：

```php
class DB
{
    /* Connection parameters */
}
```

