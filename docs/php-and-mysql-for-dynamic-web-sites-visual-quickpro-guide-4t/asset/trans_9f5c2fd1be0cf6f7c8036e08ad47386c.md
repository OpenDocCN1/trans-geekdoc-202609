
DEFINE ('DB\_HOST', 'localhost');

DEFINE ('DB\_NAME', 'sitename');

出于安全考虑，我倾向于将这些值定义为常量（这样它们就无法被更改），但这并非强制要求。通常，将这些值设置为某种变量或常量是合理的，这样您就可以将配置参数与使用它们的函数分离开来，但同样，这也不是强制的。

编写脚本时，请将这些值更改为适用于您环境的值。如果您已获得 MySQL 用户名/密码组合和数据库（例如托管网站），请在此处使用该信息。或者，如果可能，请按照[附录 A](#app01.html#app01) 中的步骤创建一个有权访问 `sitename` 数据库的用户，并将那些值插入此处。无论您做什么，除非您确定本书代码中的值在您的服务器上一定能工作，否则请勿直接使用。

### 3. 连接到 MySQL：

```
$dbc = @mysqli_connect (DB_HOST, DB_USER, DB_PASSWORD, DB_NAME) OR die ('Could not connect to MySQL: ' . mysqli_connect_error() );
```

如果 `mysqli_connect()` 函数成功连接到 MySQL，将返回一个对应于打开连接的资源链接。该链接将被赋值给 `$dbc` 变量，以便其他函数可以使用此连接。

函数调用前面带有错误抑制运算符（`@`）。这可以防止 PHP 错误在 Web 浏览器中显示。这是可取的，因为错误将由 `OR die()` 子句处理。

### 脚本 9.2. `mysqli_connect.php` 脚本将被本章中的每个其他脚本使用。它建立与 MySQL 的连接，选择数据库，并设置编码。

```
<?php # Script 9.2 - mysqli_connect.php

// This file contains the database access information.
// This file also establishes a connection to MySQL,
// selects the database, and sets the encoding.

// Set the database access information as constants:
DEFINE ('DB_USER', 'username');
DEFINE ('DB_PASSWORD', 'password');
DEFINE ('DB_HOST', 'localhost');
DEFINE ('DB_NAME', 'sitename');

// Make the connection:
$dbc = @mysqli_connect (DB_HOST, DB_USER, DB_PASSWORD, DB_NAME) OR die ('Could not connect to
MySQL: ' . mysqli_connect_error() );

// Set the encoding...
mysqli_set_charset($dbc, 'utf8');
```

如果 `mysqli_connect()` 函数无法返回有效的资源链接，则会执行语句的 `OR die()` 部分（因为 `OR` 的第一部分将为 false，所以第二部分必须为 true）。正如前一章所讨论的，`die()` 函数会终止脚本的执行。该函数也可以接受一个字符串作为参数，该字符串将被打印到 Web 浏览器。在本例中，该字符串是 *Could not connect to MySQL:* 和具体的 MySQL 错误的组合。

![Image](graphics/09_figure_02_a.jpg)

如果连接 MySQL 出现问题，将显示一条信息性消息并停止脚本。

### 4. 将文件保存为 `mysqli_connect.php`。

由于此文件包含必须保密的信息——数据库访问数据——它将使用 `.php` 扩展名。使用 `.php` 扩展名时，即使恶意用户在其 Web 浏览器中运行此脚本，也无法看到页面的实际内容。

您可能还会注意到，我没有包含结束 PHP 标签：`?>`。在 PHP 中这是允许的（当脚本以 PHP 代码结束时），并且这有一个将在后续章节中解释的好处。

### 5. 理想情况下，将文件放在 Web 文档目录之外。

![Image](graphics/09_figure_03_b.jpg)

服务器 Web 文档的可视化表示，其中 `mysqli_connect.php` 未存储在主目录（*htdocs*）内。

因为该文件包含敏感的 MySQL 访问信息，所以应安全存储。如果可以，请将其放在 Web 目录正上方或以其他方式位于 Web 目录之外的目录中。这样该文件将无法通过 Web 浏览器访问。有关更多信息，请参阅“[组织您的文档](#ch09.html#ch09sb02)”侧边栏。

### 6. 将脚本的副本暂时放在 Web 目录中，并在 Web 浏览器中运行它。

![Image](graphics/09_figure_04_c.jpg)

如果 MySQL 连接脚本正常工作，最终结果将是一个空白页面（脚本不生成任何 HTML）。

为了测试脚本，您需要将副本放在服务器上，以便可以从 Web 浏览器访问（这意味着它必须位于 Web 目录中）。如果脚本正常工作，结果应该是一个空白页面。如果您看到 *Access denied...* 或类似消息，这意味着用户名、密码和主机的组合无权访问特定数据库。

---

### 组织您的文档

[第 3 章](#ch03.html#ch03) 在开发第一个 Web 应用程序时介绍了*站点结构*的概念。现在页面将开始使用数据库连接脚本，该主题变得更加重要。

如果数据库连接信息（用户名、密码、主机和数据库）落入恶意分子之手，可能会被用来窃取您的信息或破坏整个数据库。因此，您绝不能让 `mysqli_connect.php` 这样的脚本过于安全（此处原文 "cannot keep ... too secure" 语义为“不能不够安全/必须极其安全”，译文按语境意译为“绝不能掉以轻心/必须极其安全”）。

保护此类文件的最佳建议是将其存储在 Web 文档目录之外。例如，如果图中的 *htdocs* 文件夹是 Web 目录的根目录（换句话说，URL **[www.example.com](http://www.example.com)** 指向那里），那么不在 *htdocs* 目录的任何位置存储 `mysqli_connect.php` 意味着它永远无法通过 Web 浏览器访问。诚然，PHP 脚本的源代码无法从 Web 浏览器查看（只能看到脚本发送给浏览器的数据），但小心驶得万年船。如果您不被允许将文档放在 Web 目录之外，将 `mysqli_connect.php` 放在 Web 目录中安全性较低，但也不是世界末日。

其次，我建议对连接脚本使用 `.php` 扩展名。配置正确且正常运行的服务器将执行此类文件中的代码，而不是显示它。相反，如果您仅使用 `.inc` 作为扩展名，如果直接访问该页面，其内容将显示在 Web 浏览器中。

---

### 7. 从 Web 目录中删除临时副本。

---

> **提示**
>
> 如果您使用的 PHP 版本不支持 `mysqli_set_charset()` 函数，您将需要改为执行 `SET NAMES` `encoding` 查询：
>
> ```
> mysqli_query($dbc, 'SET NAMES utf8');
> ```

---

> **提示**
>
> [第 5 章](#ch05.html#ch05) 中用于登录 mysql 客户端的相同值，应该也适用于您的 PHP 脚本。

---

> **提示**
>
> 如果您收到错误提示 `mysqli_connect()` 是“未定义函数”，这意味着 PHP 编译时未包含对 Improved MySQL Extension（改进的 MySQL 扩展）的支持。请参阅附录了解安装信息。

---

> **提示**
>
> 运行脚本时如果看到 *Could not connect...* 错误消息，很可能意味着 MySQL 正在运行。
>
> ![Image](graphics/09_figure_05_d.jpg)
>
> 除了使用无效的用户名/密码/主机名/数据库信息外，PHP 可能无法连接到 MySQL 的另一个原因是 MySQL 当前未运行。

---

> **提示**
