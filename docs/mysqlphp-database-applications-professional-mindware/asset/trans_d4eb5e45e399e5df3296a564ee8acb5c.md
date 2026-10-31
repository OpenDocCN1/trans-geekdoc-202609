
然而，要获取从第二个字符开始的所有内容，你可以使用以下方法：

```
$str = substr ($str_var,1);
```

所以在这个函数中，第三个参数是可选的。（我们在介绍函数时将会指出可选参数。）关于 substr() 的使用细节将在本章后面介绍。

也有一些函数完全不接受任何参数。phpinfo() 就是一个很好的例子。它会在不接受任何参数的情况下输出有关 PHP 环境所需了解的一切信息。另一个很好的例子是 time()，它返回当前的 Unix 时间戳。

## 返回值

你最后需要注意的是函数会返回什么。在上面的例子中，str_replace() 会返回一个字符串。你如何处理这个字符串由你决定。你可以将其赋给变量或打印出来，或做任何其他合适的事情。

```
//assign to variable
$new_str = str_replace("Jay", "John", $str);
//print directly
echo str_replace("Jay", "John", $str);
```

请注意，函数可能返回数组、整数、double（浮点数）、对象，有时也返回布尔值。在第 5 章中，你看到过一个返回布尔值（即 TRUE 或 FALSE）的函数的良好示例。如果要确定一个变量是否为数组，可以使用 is_array() 函数。

```
if (is_array($var))
{
    //process array
}
```

还有一些函数，如果有值可返回则返回一个值，如果没有值可返回则返回 FALSE。mysql_fetch_array() 函数就是一个很好的例子。只要还有结果可获取，该函数就会从查询返回的结果集中抓取行。当没有更多行可获取时，它返回 FALSE。正如你在第 5 章中所见，这对于遍历查询返回的所有行非常有帮助。

```
$result = mysql_query("select * from my_table") or
    die ( mysql_error() );
```

```
while($row = mysql_fetch_array($result))
{
    //process row
}
```

最后，函数有时会返回 nothing。这在执行特定操作的函数中很常见，例如关闭数据库或文件系统的连接。

## 函数文档

正如我们在本书中反复所说，PHP 在线手册是你的朋友。文档团队非常出色，我们真的相信在线手册的质量是该语言成功的原因之一。由于不可能在本书记载所有 PHP 函数，你需要查阅手册。因此，我们想花一点时间介绍手册中函数是如何呈现的。

典型的手册引用看起来像这样：

```
int mysql_affected_rows ([int link_identifier])
```

该函数返回 update、insert 或 delete 查询影响的行数。从中可以看到，第一部分（int）表示将要返回的变量类型。这可以是任何变量类型或 void（表示函数不返回任何内容）。然后在括号内会列出参数列表。参数的类型以及它所代表的内容也会列出。请注意，可选参数放在方括号中。因此，上面的函数不需要参数，但有一个可选参数：从 mysql_connect() 获取的连接标识符。在 phpinfo() 这样的情况下，你会看到参数列表为空。

在前面的示例中，如果你传递一个参数，它最好是一个整数。如果你给它一个字符串或数组，你会得到一个错误。

## 重要的 PHP 4 函数

在本节中，我们将尝试将 PHP 4 函数按逻辑分组。在此过程中，我们将涵盖本书中应用程序使用的每个函数。

## MySQL API

PHP 中共有 33 个 MySQL 函数可用。其中只有 17 个在本书的应用程序中使用。你可能会在自己的应用程序中使用其中一些其他 MySQL 函数，但你可能不会全部使用。为了便于列出，我将函数分为你可能最常使用的集合，然后是你不太可能广泛使用的那些。

## 经常使用的 MySQL 函数

你可能会经常使用以下函数。你可能想把这一页折角。

### MYSQL_CONNECT()

在使用以下函数建立连接之前，你无法对 MySQL 做任何事情。

```
int mysql_connect(string host, string username, string password)
```

最常见的情况是，你将使用分配给你的用户名和密码以 Web 开发者的身份连接到 localhost 上的 MySQL。该函数返回给你的整数是连接标识符。你可能需要跟踪连接标识符并将其与 mysql_select_db() 函数一起使用。它通常看起来像这样：

```
$conn = mysql_connect("localhost", "username", "password") or
    die ("Could Not Connect to Database");
```

![](img/de0823012275cf4ceebdb822a56e6b71_147_0.png)

如果 MySQL 未安装在标准端口上或 mysql socket 不位于 /tmp/mysql.sock，你可以在主机字符串中指定端口或 socket 位置。例如：

```
mysql_connect("localhost:/usr/local/mysql.sock",
    "username", "password");
```

或者，如果 MySQL 数据库位于另一台机器上，你可以使用以下方式访问它

```
mysql_connect("mymachine.mydomain.com", "username",
    "password");
```

![](img/de0823012275cf4ceebdb822a56e6b71_147_1.png)

你也可以在 php.ini 文件中指定 host、username 和 password。这样你就可以将其中一个或多个参数留空。

### MYSQL_PCONNECT()

mysql_pconnect() 函数的工作方式与 mysql_connect() 完全相同，但有一个重要区别：脚本运行结束时，与 MySQL 的连接不会关闭。

```
int mysql_pconnect(string host, string username, string password)
```

当你使用此函数时，连接保持打开状态，并且对 mysql_pconnect() 的额外调用在运行时会尝试使用这些打开的连接。这可能会使你的脚本快得多。

有趣的是注意 mysql_pconnect() 运行时的情况。脚本第一次运行时，PHP 会请求一个连接，MySQL 会打开到数据库的连接。当该脚本结束时，连接仍然可用。下一次请求 PHP 页面时，PHP 会请求一个已经打开的连接。如果 MySQL 有一个可用，它会授予 PHP 打开的连接。如果没有可用的打开连接，将会打开一个新的连接。

在脚本中，与 MySQL 数据库建立连接将是最慢的函数之一。如果 PHP 可以使用已经打开的连接，应用程序中的开销将大大减少。

为了使 mysql_pconnect() 正常工作，请在 php.ini 文件中设置以下行：

```
mysql.allow_persistent = On
mysql.max_persistent = -1; maximum number of persistent
links. -1 means no limit
```

请注意，这些是默认值。如果你使用此方法，你可能希望限制持久连接的数量。

### MYSQL_SELECT_DB()

mysql_select_db() 函数将焦点更改为你想要查询的数据库。

```
int mysql_select_db (string database_name [, int link_identifier])
```

你可以在 mysql_query() 函数中包含它返回的整数，但只有在连接到多个数据库时才真正需要。第二、optional 参数是从 mysql_connect()/ mysql_pconnect() 函数检索的链接标识符。它通常看起来像这样：

```
$db = mysql_select_db("database_name") or
    die ("Could Not Select Database");
```

![](img/de0823012275cf4ceebdb822a56e6b71_148_0.png)

> 请参阅第 8 章中 db_connect() 函数的描述，了解如何在单个函数中处理与 MySQL 服务器和特定数据库的连接。

### MYSQL_QUERY()

这个 mysql_query() 函数可能是你在脚本中最常使用的 MySQL 函数。

```
int mysql_query (string query [, int link_identifier])
```

该函数将你能拼凑的任何查询发送到 MySQL。重要的是要理解，该函数实际上并不返回查询的结果。它打开一个指向 MySQL 上结果集的光标。因此，如果你这样做：

```
echo mysql_query("select * from table");
```

你不会得到有意义的答案，只会得到标识结果集的数字。在 mysql_query() 之后，你需要使用实际从 MySQL 检索数据的函数之一（mysql_fetch_row()、mysql_fetch_array()、mysql_result()）。

可选的第二个参数将是 mysql_connect() 或 mysql_select_db() 的结果。它通常如以下代码示例中使用。请注意，查询可能因任何原因失败。最好使用 mysql_error() 找出查询失败的原因。

```
$result = mysql_query("select * from db") or
    die (mysql_error());
```

> 请参阅第 8 章中 safe_query() 函数的讨论，了解如何使用统一函数安全处理查询。

### MYSQL_FETCH_ARRAY()

一旦你从查询中检索到结果，你（大多数情况下）会使用 mysql_fetch_array() 来检索查询的行。

```
array mysql_fetch_array (int result [, int result_type])
```

该函数返回一个关联数组，以 select 列的名称作为键。默认情况下，mysql_fetch_array() 会将行的每一列返回两次：第一次使用关联键，第二次使用数字键。要告诉 PHP 将结果限制为数字结果，请将 MYSQL_NUM 用作第二个参数。要仅获取关联键，请将 MYSQL_ASSOC 用作第二个参数。

当没有更多行可获取时，该函数返回 FALSE。
以下代码将查询结果作为表格打印：

```
$query =("select * from table_name");
```
