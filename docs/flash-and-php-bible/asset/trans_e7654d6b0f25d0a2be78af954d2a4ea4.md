

## PHP 聊天应用程序

此时，您已完成聊天应用程序的 ActionScript 部分。第二步是开发 PHP 代码，该代码由 ActionScript 调用。

PHP 代码分为三个文件，如表 11.4 所示。

| PHP 代码文件 | 动作 |
|---|---|
| getMessages.php | 获取过去 15 分钟内的所有消息 |
| messages.php | 处理将新消息写入数据库 |
| dbConn.php | 与其他文件共享的数据库连接 |

您首先处理的文件是 getMessages.php。代码的第一部分加载或包含数据库连接文件，您稍后将查看该文件。下一部分是 SQL 调用，它查询 MySQL 数据库并获取过去 15 分钟内发布的所有最新消息。

```
$sql = "SELECT * FROM flashChat WHERE dateAdded > " .
(time() - (60 * 15));
$result = mysql_query($sql);
```

过去 15 分钟的条件由以下代码确定。time() 返回一个 UNIX 时间戳，减去 60 后再乘以 15。其中 60 表示一分钟的秒数，15 表示您引用的分钟数。您也可以通过去掉乘法步骤来编写这个基本数学方程式。这样做会使代码更难阅读，但也会提高应用程序的运行速度。

```
time() - 900
```

此 SQL 字符串被传入实际执行服务器调用的函数 mysql_query()，并赋值给 $result 变量。现在您已成功调用 MySQL 数据库，下一步是生成构建消息的循环。图 11.3 显示了 MySQL Query Browser 中的查询显示，该工具可免费从 www.mysql.com 获得。

此循环使用 while 实现，设置为在数据库不再返回有效行时运行。您也可以将其放入 for 循环，并使用 mysql_num_rows() 来确定返回了多少行。

## 图 11.3
在 MySQL Query Browser 中返回的 SQL 查询

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_274_0.png)

mysql_fetch_array() 函数以关联数组格式从数据库表中获取单行，并将其赋值给 $row 变量。循环内容设置为生成包含消息数据的 XML 节点，您之前在本章中查看过这些数据。

```
while($row = mysql_fetch_array($result))
{
    $xmlData .= " <message id='" . $row['id'] . "'>\n";
    $xmlData .= "   <name>" . $row['username'] . "</name>\n";
    $xmlData .= "   <msg>" . $row['message'] . "</msg>\n";
    $xmlData .= " </message>\n";
}
```

此时，您已有完成的服务器 SQL 调用和生成消息数据 XML 的循环，该 XML 将返回到 Flash 中的 ActionScript。将数据发送回 ActionScript 非常简单；您只需将 $xmlData 变量赋给 print 语句即可。

```
print $xmlData;
```

print 语句完成了您的 messages.php 文件，完整代码如下所示。

```
<?php

include 'dbconn.php';

$sql = "SELECT * FROM flashChat WHERE dateAdded > " . (
    time() - (60 * 15));

$result = mysql_query($sql);
$xmlData = "<messages>\n";

while($row = mysql_fetch_array($result))
{
    $xmlData .= " <message id='" . $row['id'] . "'>\n";
    $xmlData .= "  <name>" . $row['username'] . "</name>\n";
    $xmlData .= "  <msg>" . $row['message'] . "</msg>\n";
    $xmlData .= " </message>\n";
}

$xmlData .= "</messages>";
print $xmlData;

?>
```

接下来需要开发的 PHP 文件是 messages.php，它负责将新消息插入 MySQL 数据库。此 PHP 文件的第一部分与前一个文件相同，先加载 dbconn.php 文件，该文件负责处理与 MySQL 数据库的登录和连接。

```
include 'dbconn.php';
```

下一步是检查从 ActionScript 发送的消息是否确实大于 0 个字符（非空字符串）。在 PHP 中，strlen() 返回作为参数传入的字符串的长度。

```
if(strlen($_POST['msg']) > 0)
{
  ...
}
```

假设您有一个有效长度的消息，则分配三个变量；第一个用于用户名，第二个用于消息，第三个是 UNIX 时间戳格式的日期。

```
$username = $_POST['user'];
$message = $_POST['msg'];
$date = time();
```

开发此文件的下一步是使用 mysql_query() 进行实际的 MySQL 调用。该函数以 SQL 语句作为参数，并返回资源 ID 或抛出错误。

实际的 SQL 语句与之前示例中使用的语句相当相似。数据库中有一个 flashChat 表，恰好有四列，但其中一列是自增列，不需要在 INSERT 语句中定义。

> **注意** 在更健壮的应用程序中，您希望为从其他来源传入的数据添加一层安全性。无论这是 Flash、浏览器还是第三方服务，这始终都很重要。

```
mysql_query ("INSERT INTO flashChat (username, message, dateAdded)
VALUES (
" . $username . "',
" . $message . "',
" . $date . ""
) ");
```

> **警告** 使用 dateAdded 名称是因为 data 是 MySQL 中的保留字，在大多数情况下会导致错误。在任何开发语言中，使用保留字作其他用途都不是好主意。

此文件的最后一步是向 Flash 返回响应，通知消息已添加，该用户现在可以添加另一条消息。总的来说，messages.php 文件很简单，但能完成任务。

以下是供参考的完整 messages.php 文件。

```
<?php

include 'dbconn.php';

if (strlen($_POST['msg']) > 0)
{
$username = $_POST['user'];
$message = $_POST['msg'];
$date = time();

mysql_query("INSERT INTO flashChat (username, message,
dateAdded)
VALUES (
" . $username . "',
" . $message . "',
" . $date . ""
) ");

print "resp=MESSAGE_ADDED";
}
?>
```

## 使用 PHP 连接到 MySQL

您的 Flash 聊天应用程序中的最后一个 PHP 文件是 dbconn.php 文件。此文件负责连接到 MySQL 并提供指向数据库中表的链接。

> 同一时间只能有一个到单个数据库的连接。最佳做法是规划 SQL 连接以提高效率。这可以防止您来回切换。

此文件相当小，但有一个非常重要的要求，即最大限度地遵守安全措施。这些部分中大部分都指出了安全性的重要性。您之前查看过许多示例；在此示例中，安全性并未为了简单而被排除。

文件的第一部分是分配用于连接的数据库变量。通常，更高级的应用程序会有一个单独的配置变量文件。该配置文件仅在应用程序开始时加载，并在整个过程中引用。

但是，由于此应用程序相当小，您只需在 dbconn.php 连接文件内分配数据库连接变量。

```
$host = "HOST_NAME";
$user = "SQL_USERNAME";
$pass = "SQL_PASSWORD";
$database = "SQL_DATABASE_NAME";
```

第一个变量通常是 localhost，或者如果 MySQL 与 PHP 运行在不同服务器上，则是 MySQL 运行所在服务器的 IP 地址。您不会期望在较小的系统中看到远程 MySQL 安装，但在较大的应用程序中这非常常见。

其他三个变量是用户名、密码以及要连接的数据库名称。如果您不知道，此连接信息由您的系统管理员或主机提供。

> MySQL 默认安装的用户名为 "root" 且无密码，但这种方式非常不安全，应立即更改。

现在变量已正确定义，您可以建立到 MySQL 的实际连接。这是通过 PHP 中的 mysql_connect() 函数完成的。该函数接受三个参数：主机、用户名和密码，即刚才定义的内容。

```
$link = mysql_connect($host, $user, $pass);
```

mysql_connect() 函数返回一个资源 ID，您将其存储在 $link 变量中。在选择数据库时会引用此变量。

选择数据库只需引用要连接的数据库名称，并传递连接步骤中接收到的链接即可。

```
mysql_select_db($database, $link);
```

