
```
} else {
    return false;
}
}

file_put_bzip2_contents('file.txt.bz2',
    "\n-> This text file contains\nsome random text.
    <-" );
echo 'Data written to file.';
?>
```

### *使用 BZip2 压缩文件 (bzip2write.php)*

另一个方向（从 BZip2 归档中读取文件）与读取普通文件类似。不是使用 fopen()、fread() 和 fclose()，而是使用 bzopen()、bzread() 和 bzclose()，如下面的代码所示，该代码编写了函数 file_get_bzip2_contents()。

```
<?php
function file_get_bzip2_contents($filename) {
    $result = '';
    if ($fp = @bzopen($filename, 'wb')) {
        while ($data = bzread($fp, 4096)) {
            $result .= $data;
        }
        bzclose($fp);
        return $result;
    } else {
        return false;
    }
}

echo nl2br(htmlspecialchars(
    file_get_bzip2_contents('file.txt.bz2')
));
?>
```

## 使用 HTTP 请求返回文件

```
$filename = 'httpfile.zip';
header("Content-Disposition: attachment; filename = $filename");
```

当 PHP 脚本需要返回（可下载的）文件而不是 HTML 时，必须发送正确的 HTTP 头：

- Content-Disposition 用于文件的（建议）名称
- Content-Length 用于文件大小
- Content-Type 用于文件的 MIME 类型

前面的代码读取 ZIP 文件并将其发送给客户端；图 6.6 显示了其在浏览器中的结果。

```
<?php
$filename = 'httpfile.zip';
$mimetype = 'application/zip';
$data = file_get_contents($filename);
$size = strlen($data);
header("Content-Disposition: attachment; filename = $filename");
header("Content-Length: $size");
header("Content-Type: $mimetype");
echo $data;
?>
```

使用 HTTP 发送文件 (httpfile.php)

## 使用 HTTP 请求返回文件

![](img/1e6d362f187af50011d2666ddaa68739_203_0.png)

图 6.6  浏览器想要保存文件。

## PEAR 提供了什么？

以下 PEAR 包提供了可用于处理文件和流的功能：

- File 提供了一些用于文件访问的辅助函数，部分功能在较新的 PHP 版本中已从已弃用到新的功能
- File_Find 在路径中搜索特定文件或模式
- File_SearchReplace 在文件中执行搜索和替换
- Stream_Var 允许您将变量保存到流中，以便您可以像访问文件或流一样访问它们

## 使数据动态化

PHP 的主要优势之一是对大量数据库的支持。非常经常，PHP 和 MySQL 被视为一个整体。然而，其他数据库也有其优势——例如，MySQL 花了很长时间才支持在其他系统中被视为标准的功能；然而，MySQL 以速度很快而闻名。

本章涉及相当多的数据库并展示了与它们的基本操作：连接、发送 SQL 语句以及评估返回值。无论您的数据库驱动 Web 应用程序必须做什么，它总是必须执行这些步骤。

为了拥有一些测试数据，我们在关系数据库管理系统（RDBMS）中创建了一个名为 phrasebook 的数据库，并在其中放置了一个名为 quotes 的表。该表由四个字段组成：

- id—一个整数值，每向数据库输入一条新记录就会增加 1。根据数据库系统，数据类型称为 IDENTITY、auto_increment 或类似名称。
- quote—引语，类型为 VARCHAR(255)；此长度适用于所有系统。
- author—产生引语的人，类型为 VARCHAR(50)。
- year—引语产生的年份（有时这高度推测性），类型为 INT。

每个数据库系统都附带管理工具或可用的第三方产品。例如，图 7.1 所示的基于 PHP 的 phpMyAdmin (http://www.phpmyadmin.net/) 为 MySQL 安装提供了非常好的访问。

![](img/1e6d362f187af50011d2666ddaa68739_205_0.png)

图 7.1 使用 phpMyAdmin 管理 MySQL 安装。

## 连接到 MySQL

```
@mysql_connect('localhost', 'user', 'password')
```

PHP 可用两种 MySQL 扩展。较旧的 ext/mysql 用于 PHP 4 及更早版本；较新的 ext/mysqli（i 官方代表 improved，unofficially 代表 incompatible——但这是愤世嫉俗的）随 PHP 5 提供，但需要 MySQL 4.1 或更高版本。然而，PHP 5 也支持旧扩展。本章涵盖了这两种扩展。

```
<?php
if ($db = @mysql_connect('localhost', 'user', 'password')) {
    mysql_select_db('phrasebook', $db);
    echo 'Connected to the database.';
    mysql_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*连接到 MySQL (mysql_connect.php)*

要使用这些扩展，您可能需要启用它们。在 PHP 4 下，ext/mysql 自动激活。在 PHP 5 下，您必须使用 extension=php_mysql.dll 并将 libmysql.dll 复制到 PHP 可以找到的位置。如果您自行编译 PHP，请对旧版 MySQL 和 ext/mysql 使用开关 --with-mysql=/path/to/mysql。

现在连接到数据库很容易：只需调用 mysql_connect()，提供服务器、用户名和

密码。然后您将获得一个句柄，可用于 mysql_select_db() 或在服务器上选择数据库。最后，mysql_close() 关闭与数据源的连接。

## 连接到 MySQLi

```
@mysqli_connect('localhost', 'user', 'password')
```

如果您想使用 ext/mysqli，-with-mysql 的开关必须指向 /path/to/mysql_config。Windows 用户必须使用文件 php_mysqli.dll 和 libmysqli.dll，其余之前的安装说明保持不变。

```
<?php
if ($db = @mysqli_connect('localhost', 'user', 'password')) {
    mysqli_select_db($db, 'phrasebook');
    echo 'Connected to the database.';
    mysqli_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*连接到 MySQLi (mysqli_connect.php)*

使用 ext/mysqli 连接到 MySQL 与使用 ext/mysql 完全一样，只是函数名后面加上了 i。

请记住，mysql(i)_select_db() 的不同变量顺序是两种扩展之间最显著的差异之一。较新的扩展希望数据库句柄排在第一位。另一个区别

在这两种扩展之间是，每当使用时，数据库句柄都是强制参数。使用 ext/mysql 时，mysql_connect() 创建的最后一个句柄是页面的当前默认句柄。另一个区别：mysqli_connect() 接受数据库名称作为可选的第四个参数，因此您可以避免使用 mysqli_select_db()。

> **注意**
> 
> 另外，mysqli 扩展还提供了一种面向对象的语法来访问数据源。虽然本章使用函数式方法使从 ext/mysql 到 ext/mysqli 的过渡尽可能无痛，但下面展示了面向对象方法是什么样的：

```
<?php
$db = new mysqli('localhost', 'user',
    'password');
$db->select_db('phrasebook');
$db->close();
?>
```

## 向 MySQL 发送 SQL

### mysqli_query()

函数 mysql_query() 和 mysqli_query() 将 SQL 发送到由句柄标识的数据库——mysql_query() 的第二个参数，mysqli_query() 的第一个参数。然而，为了避免一种称为“SQL 注入”的攻击（使用 GET 或 POST 数据注入 SQL 语句的方法），您绝对 **必须** 使用 mysql_real_escape_string() 或 mysqli_real_escape_string() 来转义任何危险字符，例如单引号。请参阅前面的和下面的

列表以了解实现。那些列表中缺少的代码（但当然包含在代码下载中）基本上是一个 HTML 表单，接受引语、作者和年份。图 7.2 显示了引语收集的 HTML 输入表单。

```
<?php
    if ($db = @mysqli_connect('localhost', 'user',
        'password')) {
        require_once 'stripFormSlashes.inc.php';
        mysqli_select_db($db, 'phrasebook');
        mysqli_query($db, sprintf(
            'INSERT INTO quotes (quote, author, year)
            VALUES (\'%s\', \'%s\', \'%s\')',
            mysqli_real_escape_string($db, $_POST
            ['quote']),
            mysqli_real_escape_string($db, $_POST
            ['author']),
            intval($_POST['year'])));
        echo 'Quote saved.';
        mysqli_close($db);
    } else {
        echo 'Connection failed.';
    }
?>
```

*向 MySQLi 发送 SQL (mysqli_query.php; 摘录)*

```
<?php
    if ($db = @mysql_connect('localhost', 'user',
        'password')) {
        require_once 'stripFormSlashes.inc.php';
        mysql_select_db('phrasebook', $db);
        mysql_query(sprintf(
            'INSERT INTO quotes (quote, author, year)
            VALUES (\'%s\', \'%s\', \'%s\')',
```
