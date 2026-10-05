
# 获取查询结果并展示给用户

一旦你完成了查询，你需要获取结果并将其显示给用户，或者对其进行某些其他处理。实现这一点的简单方法之一是使用大多数支持 PHP 的数据库包含的 `fetch_array` 函数。

- `mysql_fetch_array(RESULT);`
- `mssql_fetch_array(RESULT);`
- `pg_fetch_array(RESULT);`

结果中的数据被加载到数组的字段中（既是关联又是索引）。结果中的每一列都被加载到数组的字段中。数组的键与返回数据的列名对应。

# DBX——PHP 对多数据库的支持

对于不需要复杂的特定数据库查询应用程序，可以使用 PHP 内置的 DBX 函数。

在使用 DBX 函数之前，如果你使用的是 Linux，则必须在编译时启用支持；如果你使用的是 Windows，则需要启用 DBX 模块。

## 在 Linux 中启用 DBX

如果你使用 Apache 的 APXS 功能编译 PHP（`compile --with-apxs=/path/to/apache/bin/apxs`），那么为 PHP 模块添加功能将轻而易举。

在重新编译 PHP 之前，我建议你先删除 `config.cache` 文件并清理上次编译留下的文件。可以这样操作：

```
cd /path/to/php/source 
rm config.cache
make clean
```

在执行 `make clean` 命令后，你会注意到有很多文件被删除了。不用担心，`make` 程序只是在清理它在重新编译时不需要的文件。如果不运行 `make clean` 命令，你可能会遇到一些问题。如果你一直没有问题地编译 PHP，但突然它无法正确编译了，即使你没有更改任何内容，那么 `make clean` 命令很可能解决你的问题。

一旦你清理了上次编译留下的混乱，就可以开始新的编译了。

要编译启用了 DBX 支持的 PHP，请从 shell 提示符执行以下命令（根据需要替换特定安装的路径）：

```
./compile --with-apxs=/usr/local/apache/bin/apxs \ 
--enable-dbx \
```

你还应该启用你任何想要使用的数据库的支持——例如：

```
--with-mssql 
```

在运行 `configure` 之后，执行命令：

```
make 
```

假设没有发生错误，你就可以执行命令：

```
make install 
```

最后一条命令将 `libphp4.so` 库文件复制到 `/path/to/apache/libexec/`。

重启 Apache 以加载新库：

```
/path/to/apache/bin/apachectl restart 
```

你可以通过使用 `phpinfo()` 函数并验证 DBX 是否列在配置部分下，来确认 DBX 已正确安装。

## 在 Windows 中启用 DBX

在 Windows 上启用 DBX 支持非常简单，因为 DLL 文件已经预编译并包含在基础 PHP 安装中。打开你的 `php.ini` 文件并搜索如下行：

```
extension_dir = 
```

此行应指向扩展所在的位置。如果你没有将扩展移动到与 `php.ini` 文件相同的目录，你需要编辑该行，例如：

```
extension_dir = C:\Apache\php\
```

接下来，在 `php.ini` 中找到以下部分，取消（删除行开头的分号）包含 DBX 库的行：

```

```

取消该行的注释后，保存文件并重启 Apache 服务器。你可以通过使用 `phpinfo()` 函数并验证 DBX 是否列在配置部分下，来确认 DBX 已正确安装。

## DBX 函数

DBX 函数是一组单一函数，允许你访问多个数据库而无需编写自己的封装函数。

从 4.1 版本开始，PHP DBX 支持以下数据库：

- mysql
- odbc
- pgsql
- mssql
- fbs

DBX 可用函数如下：

### `dbx_close(CONNECTION)`

`dbx_close()` 函数接受一个参数 `CONNECTION`。`CONNECTION` 是在你调用 `dbx_connect()` 时创建的标识符。

### `dbx_connect(MODULE, HOST, DATABASE, USER, PASSWORD, PERSISTENT)`

`dbx_connect()` 函数用于与数据库服务器建立连接，并指定使用的数据库。`dbx_connect` 返回一个包含连接句柄以及其所连接数据库名称的对象。详情见示例。`dbx_connect` 函数接受六个参数：

- `MODULE`——你想要为此连接使用的数据库模块。该模块本质上是你尝试连接的数据库类型。值可以是：
  - `DBX_MYSQL`——用于 MySQL 数据库。
  - `DBX_ODBC`——用于支持 ODBC 连接的任何数据库。
  - `DBX_PGSQL`——用于 PostgreSQL 数据库。
  - `DBX_MSSQL`——用于 MS SQL 数据库。
  - `DBX_FBSQL`——用于 Frontbase 数据库。
- `HOST`——数据库服务器的主机或 IP 地址。
- `DATABASE`——数据库服务器上的数据库名称。
- `USER`——用户名。
- `PASSWORD`——用户密码。
- `PERSISTENT`——是否建立持久连接。如果你希望连接持久，请在此处放置 `DBX_PERSISTENT`。否则，此参数不是必需的。

示例：

```
$module = DBX_MYSQL; //注意这里没有引号！ 
$dbconn = dbx_connect($module, "192.168.0.5", "php", "mysqluser", "password") or DIE (
"无法连接");
//$dbconn->database = "php"
//$dbconn->handle 是一个资源标识符
```

### `dbx_error(CONNECTION)`

`dbx_error` 函数返回对模块上一次函数调用的错误信息。参数 `CONNECTION` 是你在调用 `dbx_connect()` 时定义的连接标识符。

示例：

```
$result = dbx_query($dbconn, "select something from non_existing_table"); 
if ($result == 0) {echo dbx_error($dbconn); }
//响应：Table 'php.non_existing_table' 不存在
```

### `dbx_query(CONNECTION, SQL STATEMENT, FLAGS)`

`dbx_query` 函数允许你向数据库发送 SQL 查询。如果查询没有失败且返回了一行或多行，则它返回一个对象。返回零行的查询不会返回对象。相反，它返回 1，表示查询成功但没有返回数据，例如从一个没有数据的表中进行 `select *` 操作。其参数为：

- `CONNECTION`——当调用 `dbx_connect()` 函数时创建的连接标识符。
- `SQL STATEMENT`——一个标准的 SQL 语句。
- `FLAGS`——你可以通过指定以下一个或多个标志来规定查询返回的信息量。默认情况下，所有标志都是开启的。在指定标志时，必须使用 `|` 符号分隔它们——例如 `DBX_RESULT_INDEX | DBX_RESULT_INFO`。这些标志包括：
  - `DBX_RESULT_INDEX`——始终返回。结果数组中的所有结果都通过数字索引，例如 `$result[0]`、`$result[1]` 等。
  - `DBX_RESULT_INFO`——返回关于所返回列的信息，例如字段名和字段类型。
  - `DBX_RESULT_ASSOC`——将返回的数组的键设置为为列名。

`dbx_query` 返回的对象包含以下属性：

- `handle`——与 `$dbconn->handle` 相同的句柄。通过 `$result->handle` 访问。
- `cols`——结果集中的列数。通过 `$result->col` 访问。
- `rows`——结果集中的行数。通过 `$result->rows` 访问。
- `info`——仅在标志位参数中指定了 `DBX_RESULT_INFO` 或 `DBX_RESULT_ASSOC` 时才会返回。提供一个包含列名及其类型的二维数组。通过 `$result['info'][$x]` 和 `$result['name'][$x]` 访问，其中 `$x` 是特定行的索引。
- `data`——包含来自结果的实际数据。通过 `$result->data[$x]['field name']` 访问，其中 `$x` 是特定行的索引。

示例：

```
$result = dbx_query($dbconn, "select something from 
some_table", DBX_RESULT_INFO);
```

### `dbx_sort(RESULT, SORT FUNCTION)`

`dbx_sort` 函数允许你使用自定义的排序函数对查询结果进行排序。然而，在 SQL 语句中使用 "ORDER BY" 子句会更高效。`dbx_sort` 接受的参数为：

- `RESULT`——上一个 `dbx_query` 语句的结果。
- `SORT FUNCTION`——你的自定义排序函数。

示例：

```
function my_sort { 
       //你的自定义排序定义
}
dbx_sort($result, "my_sort");
//$result 现在已根据 my_sort() 完成了排序
```

### `dbx_compare(ROW1, ROW2, COLUMN KEY, FLAGS)`

`dbx_compare` 函数允许你比较两个结果集，`ROW1` 和 `ROW2`。如果 `ROW1 = ROW2`，则 `dbx_compare` 返回 0。如果 `ROW1 > ROW2`，则 `dbx_compare` 返回 1。如果 `ROW1 < ROW2`，则 `dbx_compare` 返回 -1。`dbx_compare` 接受的参数为：

- `ROW1`——来自 `dbx_query` 函数调用的结果。
- `ROW2`——来自 `dbx_query` 函数调用的结果。
- `COLUMN KEY`——应进行比较的列名。
- `FLAGS`——你可以指定多个标志来按升序或降序比较行，并规定进行何种类型的比较。用管道符分隔任何类型的顺序。
  - `DBX_CMP_ASC`——（默认）按升序比较。
  - `DBX_CMP_DESC`——按降序比较。
  - `DBX_CMP_NATIVE`——（默认）"原样"比较项目。
  - `DBX_CMP_TEXT`——作为字符串比较项目。
  - `DBX_CMP_NUMBER`——作为数字比较项目。

示例：

```
$comp = dbx_compare ($r1, $r2, "income"); 
//$如果 $r1 = $r2 则 $comp = 0
```

- 19: 定义数据库服务器的主机名或 IP。
- 20: 定义数据库用户的用户名。
- 21: 定义数据库用户的密码。
- 22: 在数据库服务器上定义数据库名称。
- 24: 定义一个函数来查询数据库并返回数据库中的 URL。
- 25: 执行查询。注意调用 `dbx_query()` 函数之前有一个 `"@"` 符号。`"@"` 符号会抑制函数在出现问题（例如数据库宕机）时可能发出的任何警告。有关处理这些错误的更多信息，请参阅第 8 章。
- 26: 如果 `$result == 0`，则发生了错误，因为在成功时，`dbx_query` 应该返回一个对象。
- 27: 如果第 26 行为真，则打印错误。
- 28–30: 如果没有错误，则返回结果对象。
- 30: 结束函数声明。
- 32: 定义一个名为 `url()` 的函数，用于从数据库中添加或删除 URL。该函数接受以下参数：
  - `$action`——"add" 或 "delete"
  - `$dbconn`——到数据库的连接链接
  - `$url`——要添加或删除的 URL
  - `$description`——URL 的描述
- 33: 如果参数 `$action` 为 `"add"`，则表示我们正在添加 URL。
- 34: 生成添加 URL 的 SQL 语句。
- 35: 如果 `$action` 不是 `"add"`，则检查它是否为 `"delete"`。
- 36: 解码编码的 URL。
- 37: 生成删除 URL 的 SQL 语句。
- 38: 结束第 33 行开始的 if/else 语句。
- 39: 使用生成的 SQL 查询数据库。
- 40: 如果 `$result == 0`，则发生了错误，因为在成功时，`dbx_query` 应该返回一个对象。
- 41: 向用户显示错误，包括特定的 DBX 错误消息。
- 42–44: 如果查询数据库时没有错误，则向用户显示成功消息。
- 45: 结束函数。
- 46: 开始主程序。
- 47: 使用脚本开头定义的变量生成数据库连接字符串。
- 49–53: 打印显示标题的页面 HTML 以及添加 URL 的表单。
- 55–57: 如果点击了 "Add URL!" 按钮，则运行 `url()` 函数。
- 58–60: 如果点击了任何 URL 旁边的 "Delete"链接，则运行 `url()` 函数。
- 61: 生成获取 URL 的 SQL 语句。
- 62: 使用上述生成的 SQL 运行 `get_url()` 函数从数据库中获取 URL。
- 63: 检查 `get_urls()` 函数返回的结果集中是否有数据。如果没有数据，则说明数据库为空。
- 65: 向用户显示数据库为空的消息。
- 67: 如果数据库不为空，则执行脚本的剩余部分。
- 70–71: 创建一个显示 URL 的表格。
- 73: 启动 for 循环，遍历从 `get_url()` 函数返回的数据。
- 75: 将 URL 打印到表格中，并包含该 URL 的超链接。
- 76: 在表格中打印 URL 的描述。
- 77: 为该 URL 打印删除链接。
- 79: 结束 for 循环。
- 81: 结束第 63 行开始的 if/else 语句。
- 83–84: 关闭页面的 HTML。

## 为多个数据库创建你自己的支持

如果你有一个不需要复杂的数据库交互的简单应用程序，但你仍然希望它支持多个数据库，那么你可以创建自己的一套数据库包装函数。

你必须考虑到可能出现的不同特定限制，并针对最低共同标准进行编码。也就是说，如果你还想支持 MS SQL 或 PostgreSQL 数据库，就不能使用 MySQL 支持的有用 `"AUTO_INCREMENT"` 列功能，因为它们没有实现该功能。同样，MySQL 不支持辅助键，因此你不能使用该约定。下一个示例提供了一个支持 MySQL、MS SQL 和 PostgreSQL 的示例数据库包装器。它被称为 `DBlib`，包含了表 3-1 中列出的函数：

### 表 3-1. DBlib.php 函数

| 函数 | 描述 |
| --- | --- |
| `connectDB(DB_ID)` | 连接到数据库服务器并返回 `DB_CONNECTION`。 |
| `selectDB(DB_ID)` | 选择在服务器上哪个数据库。 |
| `queryDB(DB_ID, QUERY)` | 向数据库发送 SQL 查询。返回 `RESULT` 集合。 |
| `returnDBarray(DB_ID, RESULT)` | 返回 `RESULT` 集中行的数组。 |
| `numrowsDB(DB_ID, RESULT)` | 返回上次查询受影响的行数。 |
| `closeDB(DB_ID, DB_CONNECTION)` | 关闭与数据库的连接。 |

示例的第一部分是 `DBlib.php` 文件，将其包含在你自己的应用程序中。

### 脚本 3–2 DBlib.php
