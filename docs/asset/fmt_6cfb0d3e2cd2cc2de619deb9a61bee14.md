
```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
  if ($db = @sqlite_open('quotes.db', 0666, $error))
  {
    $result = sqlite_query($db, 'SELECT * FROM
      quotes');
    while ($row = sqlite_fetch_array($result)) {
      printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
        htmlspecialchars($row['id']),
        htmlspecialchars($row['quote']),
        htmlspecialchars($row['author']),
        htmlspecialchars($row['year'])
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

*从 SQLite 检索数据（`sqlite_fetch.php`；摘录）*

前面的代码展示了如何使用 `sqlite_fetch_array()` 访问结果集中的所有数据。只要该函数返回的不是 `false`（意味着没有剩余数据），`while` 循环就会持续调用它。

> 提示
>
> 使用 `sqlite_fetch_all()` 会一次性将整个结果集读入内存。因此，如果数据量不大，这是性能最好的方法。如果数据较多，使用 `sqlite_fetch_array()` 和 `sqlite_fetch_object()` 的迭代方法可能更好。

### 连接到 PostgreSQL

#### `@pg_connect()`

PostgreSQL 拥有越来越多的爱好者。有些人甚至说这是因为新版本 8.0 终于推出了原生 Windows 版本。不过，大多数使用 PostgreSQL 的生产系统仍然托管在 Linux 或 UNIX 上。

安装数据库后，可以使用基于 Web 的管理软件（如 `phpPgAdmin`（http://sourceforge.net/projects/phppgadmin））或其他工具（如图形用户界面（GUI）应用程序 `pgAdmin`（http://www.pgadmin.org/））来管理数据库。或者，也可以使用命令行工具。要让 PHP 访问 PostgreSQL 安装，Windows 用户必须在 `php.ini` 中使用条目 `extension=php_pgsql.dll` 加载扩展；UNIX/Linux 用户使用开关 `--with-pgsql=/path/to/pgsql` 配置 PHP。

然后，`pg_connect()` 连接到数据源。你必须提供一个连接字符串，其中包含所有重要数据，包括主机、端口、数据库名称和用户凭据。

### 向 PostgreSQL 发送 SQL

```
 intval($_POST['year']));
    echo 'Quote saved.';
    pg_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*向 PostgreSQL 发送 SQL（`pg_query.php`；摘录）*

> 注意
>
> 在最后一条 `INSERT` 语句之后检索标识列的值有点棘手。PostgreSQL 中这种数据类型的术语是 `SERIAL`，它会自动创建一个序列。要获取该序列的值，可以使用 `pg_last_oid()` 检索该值的 `oid`（对象 id）。然后，执行 `SELECT id FROM quotes WHERE oid=<oid>`，其中 `<oid>` 是你刚刚检索到的 `oid`。这将最终返回所需的值。

### 更新 PostgreSQL 中的数据

#### `pg_insert()`

在 PostgreSQL 中插入或更新数据的另一种方式是使用 `pg_insert()` 和 `pg_update()` 函数。第一个参数必须是数据库句柄，第二个参数是要插入/更新的表，第三个参数以关联数组的形式包含一些数据（列名为键）。如果是 `UPDATE` SQL 语句，更新条件也必须以数组形式作为函数的第四个参数提交。前面的代码展示了如何插入数据。

```
<?php
if ($db = @pg_connect('host=localhost port=5432
dbname=phrasebook user=postgres
password=abc123')) {
require_once 'stripFormSlashes.inc.php';
$data = array(
'quote' => pg_escape_string($_POST['quote']),
'author' => pg_escape_string($_POST
['author']),
'year' => intval($_POST['year'])
);
pg_insert($db, 'quotes', $data);
echo 'Quote saved.';
pg_close($db);
} else {
echo 'Connection failed.';
}
?>
```

*向 PostgreSQL 发送 SQL（`pg_insert.php`；摘录）*

### 检索 PostgreSQL 查询结果

```
$result = pg_query();
pg_fetch_row($result);
```

调用 `pg_query()` 的返回值是指向结果集的指针，可以与以下函数一起使用：

- `pg_fetch_assoc()` 将结果集中的当前行作为关联数组返回
- `pg_fetch_object()` 将结果集中的当前行作为对象返回
- `pg_fetch_row()` 将结果集中的当前行作为数字数组返回
- `pg_fetch_all()` 将整个结果集作为关联数组的数组返回

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @pg_connect('host=localhost port=5432
    dbname=phrasebook user=postgres
    password=abc123')) {
    $result = pg_query($db, 'SELECT * FROM quotes');
    while ($row = pg_fetch_row($result)) {
        vprintf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            $row
        );
    }
    pg_close($db);
    } else {
    echo '<tr><td colspan="4">Connection
failed.</td></tr>';
    }
?>
</table>
```

*从 PostgreSQL 检索数据（`pg_fetch.php`；摘录）*

代码使用 `pg_fetch_row()` 读取 `quotes` 表中的所有数据。

另外，`pg_select()` 的工作方式与 `pg_insert()` 和 `pg_update()` 类似。只需提供数据库句柄、表名，以及可能是数组形式的 `WHERE` 子句，就可以得到以（关联）数组数组形式呈现的完整结果集。

```
$data = pg_select($db, 'quotes');
```

### 连接到 Oracle

#### `@oci_connect()`

有两个 PHP 扩展可用于 Oracle，但只有一个在积极维护，并且也适用于更新版本的 RDBMS。要安装它，请使用开关 `--with-oci8` 配置 PHP。必须设置环境变量 `ORACLE_HOME`，以便 PHP 能够找到客户端库。Windows 用户需要 `php.ini` 指令 `extension=php_oci8.dll`。此外，PHP 需要对客户端库的读取权限。然后，`oci_connect()` 尝试与服务器建立连接。参数的顺序有点奇怪：先是用户名和密码，然后是服务名称（该服务已使用配置助手配置，或者是 `tnsnames.ora` 文件的一部分）。返回值是连接的句柄，数据库中的进一步操作需要它。

```
<?php
if ($db = @oci_connect('scott', 'tiger', 'orcl'))
{
 echo 'Connected to the database.';
 oci_close($db);
} else {
 echo 'Connection failed.';
}
?>
```

连接到 Oracle（`oci_connect.php`）

> 警告
>
> 在 PHP 4 中，`oci_connect()` 尚不存在，因此对于该版本，必须使用 `oci_logon()`。然而，这被视为在 PHP 5 中已弃用。因此，本章中的所有 Oracle 示例都使用 PHP 5 语法；但是，下载仓库中包含了扩展名为 `.php4` 的文件，这些文件适用于较旧的 PHP 版本。

### 向 Oracle 发送 SQL

#### `oci_execute()`

本节再次使用 `quotes` 表，该表也包含一个标识列；然而，在 Oracle 中实现这一点要复杂一些。有关更多信息，请参阅下载存档中的脚本 `quotes.oracle.sql`。

```
<?php
if ($db = @oci_connect('scott', 'tiger', 'orcl'))
{
require_once 'stripFormSlashes.inc.php';
$sql = 'INSERT INTO quotes (quote, author, year)
    VALUES (:quote, :author, :year)';
$stmt = oci_parse($db, $sql);
oci_bind_by_name($stmt, ':quote',
    $_POST['quote']);
oci_bind_by_name($stmt, ':author',
    $_POST['author']);
oci_bind_by_name($stmt, ':year',
    intval($_POST['year']));
oci_execute($stmt, OCI_COMMIT_ON_SUCCESS);
echo 'Quote saved.';
oci_close($db);
}
```

```php
} else {
    echo 'Connection failed.';
}
?>
```

向 Oracle 发送 SQL（`oci_execute.php`；节选）

要向 Oracle 发送 SQL，需要两个步骤。首先，调用 `oci_parse()` 解析 SQL 字符串，并返回一个资源，然后可以使用 `oci_execute()` 执行该资源。`oci_execute()` 的第二个参数非常重要。虽然允许使用几个常量，但大多数时候会使用 `OCI_DEFAULT`。尽管名称如此，但它并不是默认值，而是表示“不自动提交”。另一方面，`OCI_COMMIT_ON_SUCCESS` 会在未发生错误时提交挂起的事务。而且，这确实就是默认值。

遗憾的是，并没有类似 `oci_escape_string()` 的函数来转义 SQL 语句中的特殊字符。因此，预处理语句是必须的——但也非常容易实现。为此，SQL 语句必须包含以冒号开头的占位符：

```php
$sql = 'INSERT INTO quotes (quote, author, year)
    VALUES (:quote, :author, :year)';
```

然后，需要用值来填充这些占位符。为此，必须使用 `oci_bind_by_name()`：

```php
oci_bind_by_name($stmt, ':quote', $_POST['quote']);
```

上面的代码将一些表单数据发送到数据库。无需担心特殊字符，因为 `oci_bind_by_name()` 会处理这些问题。

### 向 Oracle 发送 SQL

> 当你使用 `OCI_DEFAULT` 作为提交模式时，必须使用 `oci_commit($db)` 将更改写入数据库；`oci_rollback($db)` 则执行回滚。
>
> 顺便说一下，如果你想获取最近一次 `INSERT` 操作的自增值，必须在事务内执行 `SELECT quotes_id.CURRVAL AS id FROM DUAL`，其中 `quotes_id` 是你所使用的序列的名称。

### 检索 Oracle 查询结果

```php
oci_fetch_object($stmt)
```

你有多种方式访问 SQL 查询的返回值，但在实践中，以下函数最常用：

- `oci_fetch_assoc()` 返回结果集中的当前行作为关联数组。
- `oci_fetch_object()` 返回结果集中的当前行作为对象。
- `oci_fetch_row()` 返回结果集中的当前行作为数字数组。
- `oci_fetch_all()` 将完整的结果集作为关联数组的数组返回。不过，它需要五个参数：来自 `oci_parse()` 的语句对象、用于返回数据的数组、要跳过的行数、要返回的最大行数（`-1` 表示无限），以及是否返回数字数组（`OCI_NUM`）或关联数组（`OCI_ASSOC`）。

本段中的代码清单使用 `while` 循环和 `oci_fetch_object()` 来检索表中的所有数据。

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @oci_connect('scott', 'tiger', 'orcl'))
    {
        $stmt = oci_parse($db, 'SELECT * FROM quotes');
        oci_execute($stmt, OCI_COMMIT_ON_SUCCESS);
        while ($row = oci_fetch_object($stmt)) {
            printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
                htmlspecialchars($row->ID),
                htmlspecialchars($row->QUOTE),
                htmlspecialchars($row->AUTHOR),
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

*从 Oracle 检索数据（`oci_fetch.php`；节选）*

> 注意
>
> Oracle 总是以大写形式返回列名。
>
> 因此，在访问 SQL 查询的返回值时，必须使用大写形式的对象属性或大写形式的关联数组键。

### 连接 MSSQL

#### `@mssql_connect()`

Microsoft SQL 引擎有两种版本：功能完备（且价格不菲）的 Microsoft SQL Server（简称 MSSQL），以及免费版 Microsoft SQL Server Desktop Engine（简称 MSDE），可免费从 http://www.asp.net/msde/ 获取。PHP 支持这两个版本，因为它们彼此兼容。要使其正常工作，你需要 `php.ini` 中的 `extension=php_mssql.dll` 配置行。此外，PHP 还需要访问 MSSQL/MSDE 的客户端库文件 `ntwdbllib.dll`。在 PHP 5 中，该文件位于 PHP 目录中，因此 PHP 进程只需对其具有读取权限。在 PHP 4 中，你可能需要将该文件（位于 `dll` 子目录中）复制到其他地方，例如 Windows 的 `system32` 文件夹中。

不过，UNIX/Linux 系统也可以连接到异构网络中的 MSSQL/MSDE 安装，这种组合为一些高流量网站提供了动力。要实现这一点，你必须从 http://www.freetds.org/ 下载 FreeTDS 库，解压发行版后使用以下命令安装：

```
./configure --prefix=/usr/local/tds --with-tdsver=4.2
make
sudo make install
```

然后，使用开关 `--with-sybase=/usr/local/freetds` 重新配置 PHP。

最后，如前面的代码清单所示，你可以使用 `mssql_connect()` 连接到服务器，并使用 `mssql_select_db()` 选择要使用的数据库。

```php
<?php
    if ($db = @mssql_connect('localhost', 'user',
        'password')) {
        mssql_select_db('phrasebook');
        echo 'Connected to the database.';
        mssql_close($db);
    } else {
        echo 'Connection failed.';
    }
?>
```
