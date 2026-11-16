

```
$series_id, $book_series);
echo("option\n");
}
```

最后一个脚本是 results.php，用于显示搜索结果。让我们突出涉及数据库交互的部分：

```php
<?php
// Connect to the MySQL server
$conn = mysql_connect('localhost', 'jon', 'pass') or die(mysql_error());

// Select the database
mysql_select_db('Library', $conn) or die(mysql_error());

// Attempt to fetch the form variables
$query = addslashes($HTTP_GET_VARS['query']);
$series = $HTTP_GET_VARS['series'];
$type = $HTTP_GET_VARS['type'];

// Query the database for the list of series
$sql = "SELECT book_title, auth_name, price " .
    "FROM title, details, author, authortitle, series " .
    "WHERE author.auth_ID = authortitle.auth_ID AND " .
    "authortitle.ISBN = title.ISBN AND title.ISBN = details.ISBN " .
    "AND details.series_ID = series.series_ID";

// Add the search terms to the query
if (!empty($series)) {
    $sql .= " AND Series.series_ID = $series";
}

if (!empty($query) && !empty($type)) {
    if ($type == 'isbn') {
        $sql .= " AND Details.ISBN = '$query'";
    } elseif ($type == 'author') {
        $sql .= " AND Author.auth_name LIKE '%$query%'";
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
<td><u><?php echo(htmlspecialchars($row['book_title'])) ?></u></td>
<td><?php echo(htmlspecialchars($row['auth_name'])) ?></td>
<td>$<?php echo(htmlspecialchars($row['price'])) ?></td>
</tr>
<?php
    }
}
```

} else {
    echo("<tr><td colspan=\"3\">No matches were found.</td></tr>\n");
}
// Close the database connection
mysql_close($conn);
?>
```

你应该足够了解移植过程和涉及的函数，以便很快将其切换到 ODBC。生成的 ODBC 版本如下：

```php
<?php
require("db_env.php"); // *nix specific environment variables

// Connect to the database
$conn = odbc_connect("dsn","jon","pass") or die(odbc_error());

// Attempt to fetch the form variables, passed in from browser.
$query = addslashes($HTTP_GET_VARS['query']);
$series = $HTTP_GET_VARS['series'];
$type = $HTTP_GET_VARS['type'];

// Query the database for the list of series
$sql = "SELECT book_title, auth_name, price " .
    "FROM title, details, author, title_author " .
    "WHERE author.auth_ID = author_title.auth_ID AND " .
    "author_title.ISBN = title.ISBN AND title.ISBN = details.ISBN " .
    "AND details.series_ID = series.series_ID";

// Add the search terms to the query - building the where clause on the fly
depending on type specified by user.
if (!empty($series)) {
    $sql .= " AND series.series_ID = $series";
}

if (!empty($query) && !empty($type)) {
    if ($type == 'isbn') {
        $sql .= " AND details.ISBN = '$query'";
    } elseif ($type == 'author') {
        $sql .= " AND author.auth_name LIKE '%$query%';";
    } elseif ($type == 'title') {
        $sql .= " AND title.book_title LIKE '%$query%';";
    }
}

$result = odbc_exec($conn, $sql) or die(odbc_error()); //execute the SQL

// Print the <option> rows for the <select> widget
if (odbc_num_rows($result) != 0) { //remember, this will still work for -1
    while ($row = odbc_fetch_row($result)) {
        $book_title = odbc_result($row, "book_title");
        $auth_name = odbc_result($row, "auth_name");
        $price = odbc_result($row, "price");
    }
?>
<tr>
<td><u><?php echo(htmlspecialchars($book_title)) ?></u></td>
<td><?php echo(htmlspecialchars($auth_name)) ?></td>
<td><?php echo(htmlspecialchars($price)) ?></td>
</tr>
<?php
}
} else { //if odbc_num_rows is "0" then the above will be skipped
echo("<tr><td colspan=\"3\">No matches were found.</td></tr>\n");
}

// Close the database connection - good housekeeping!
odbc_close($conn);
?>
```

## 摘要

在本章中，我们了解了开放数据库互连性。我们还通过扩展之前的示例，在前一章建立的知识基础上进行了深入。讨论的主题包括：

- ODBC 基础知识，包括历史、架构和安装
- PHP ODBC 接口，包括示例连接
- 第 17 章的数据驱动应用程序，重写为使用 ODBC 函数

## 非 Web PHP 编程

程序员经常忽略的 PHP 一个方面是，它能够通过 COM、CORBA 和新的 PHP-GTK 充当命令行解释器，为用户提供图形用户界面（GUI）应用程序。在许多情况下，PHP 都是用作简单桌面 GUI 或交互式命令行应用程序后端语言的理想选择。

在本章中，我们将概述将 PHP 设置为命令行解释器的方法。然后我们将探讨：

- [ ] 在 Windows 和 Linux 下自动化任务
- [ ] 创建交互式命令行应用程序
- [ ] 使用 PHP-GTK 创建跨平台窗口应用程序

### 什么是 GTK？

GTK 是 GIMP 工具包的缩写。它是一个用于创建用 C 编写的 GUI 应用程序的组件库。

它被称为 GIMP 工具包，是因为它最初是为开发 GNU 图像处理程序（GIMP）而编写的，但现在 GTK 已用于大量软件项目，包括 GNU 网络对象模型环境（GNOME）项目。GTK 构建在 GDK（GIMP 绘图工具包）之上，后者为底层窗口系统函数提供了抽象层。还有一个名为 GLib 的第三个组件，它提供了 GTK 使用的基础实用工具。这三个库通常统称为 GTK+。

尽管 GTK+ 是用 C 编写的，但有许多其他语言（包括 C++、Guile、Perl、Python、TOM、Ada95、Objective C、Free Pascal 和 Eiffel）的 GTK+ 绑定。GTK+ 也已移植到 BeOS 和 Win32。这些因素使 GTK+ 成为创建窗口应用程序的 PHP 扩展的绝佳选择。

最后，GTK+ 根据 GNU LGPL 许可证发布，这意味着你可以使用 GTK+ 开发开源软件、免费软件，甚至商业非免费软件，而无需为许可证或版税支付任何费用。

### 什么是 PHP-GTK？

PHP-GTK 是 Andrei Zmievski 编写的 PHP 扩展，用于使用 GTK+ 库进行客户端跨平台 GUI 应用程序编程，部分目的也是为了证明 PHP 不仅可用于 Web 应用程序编程。

### 命令行中的 PHP

将 PHP 设置为命令行解释器非常简单。该过程在 Windows 和 Linux 之间略有不同。我们将先处理在 Linux 下的设置。

### Linux 设置

要在 Linux 下使用 PHP 作为命令行解释器，你需要构建 PHP 的 CGI 版本。安装后，你就拥有所需的一切。要利用交互式命令行应用程序，你需要安装 libedit 并启用 libedit 配置 PHP。具体过程如下所述。

### libedit 支持

首先你需要安装 libedit，可从 http://www.sourceforge.net/projects/libedit/ 获取。该库是 readline 的非 GPL 直接替代品，readline 是一个允许你创建交互式命令行应用程序的库。由于许可证问题，PHP 使用此库而不是 readline 本身。你也可以使用 -with-readline[=DIR] 选项来使用 readline 库，但这将违反其分发的许可证条款。出于此原因，此处不讨论该过程。

### libedit 安装

访问 libedit 网站并将其下载到本地硬盘。切换到下载 libedit 的目录，并按以下所示解压 tar 文件：

```
tar -xvzf libedit.tar.gz
```

现在切换到 libedit 目录并运行 configure 脚本，以配置在你的系统上运行的编译过程，如下所示：

```
./configure
```

