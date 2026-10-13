
如果站点*已上线*，详细错误信息应通过电子邮件发送，而 Web 用户只能看到一条通用消息。更进一步，如果错误类型为特定的 **`E_NOTICE`**，则不会打印该通用消息。此类错误发生在引用不存在的变量等情况，这可能是个问题，也可能不是。为避免用户可能被大量错误消息淹没，仅当 **`$e_number`** 不等于 **`E_NOTICE`** 时才打印错误消息，`E_NOTICE` 是 PHP 中定义的常量（参见 PHP 手册）。

**9.** 完成函数定义并告知 PHP 使用您的错误处理程序：

```
}
set_error_handler('my_error_handler');
```

您必须使用 **`set_error_handler()`** 函数来告知 PHP 使用您自己的函数处理错误。

**10.** 将文件保存为 **`config.inc.php`**，并将其放置在您的 Web 目录下的 **`includes`** 文件夹中。

请注意，遵循本书中许多其他示例的惯例，由于此脚本将被其他 PHP 脚本包含，因此省略了结束的 PHP 标签。

### 创建数据库脚本

第二个配置类脚本是 **`mysqli_connect.php`**，即本书多次使用的数据库连接文件。其目的是连接到 MySQL、选择数据库并建立使用的字符集。如果发生问题，此脚本将利用 **`config.inc.php`** 中建立的错误处理工具。为此，此脚本将在适当的时候调用 **`trigger_error()`** 函数。**`trigger_error()`** 函数让您通知 PHP 发生了错误。当然，PHP 将使用配置脚本中建立的 **`my_error_handler()`** 函数来处理该错误。

#### 脚本 18.4
此脚本连接到 *ch18* 数据库。如果无法连接，则会触发错误处理程序，并将 MySQL 连接错误传递给它。

```
<?php # Script 18.4 - mysqli_connect.php
// This file contains the database
// access information.
// This file also establishes a
// connection to MySQL
// and selects the database.

// Set the database access information
// as constants:
DEFINE ('DB_USER', 'username');
DEFINE ('DB_PASSWORD', 'password');
DEFINE ('DB_HOST', 'localhost');
DEFINE ('DB_NAME', 'ch18');

// Make the connection:
$dbc = @mysqli_connect (DB_HOST, DB_USER, DB_PASSWORD, DB_NAME);

// If no connection could be made,
// trigger an error:
if (!$dbc) {
    trigger_error ('Could not connect to MySQL: ' . mysqli_connect_error() );
} else { // Otherwise, set the encoding:
    mysqli_set_charset($dbc, 'utf8');
}
```

### 连接到数据库

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 **`mysqli_connect.php`**（**脚本 18.4**）：

```
<?php # Script 18.4 - mysqli_connect.php
```

**2.** 设置数据库访问信息：

```
DEFINE ('DB_USER', 'username');
DEFINE ('DB_PASSWORD', 'password');
DEFINE ('DB_HOST', 'localhost');
DEFINE ('DB_NAME', 'ch18');
```

一如既往，请将这些值更改为适合您的 MySQL 安装的值。

**3.** 尝试连接到 MySQL 并选择数据库：

```
$dbc = @mysqli_connect (DB_HOST, DB_USER, DB_PASSWORD, DB_NAME);
```

在之前的脚本中，如果此函数未返回正确结果，则会调用 **`die()`** 函数，终止脚本执行。由于本站点将使用自定义错误处理函数，我将重写连接过程。

由于 **`@`** 抑制运算符，此函数调用引发的任何错误都将被抑制，并由下一步中的代码处理。

**4.** 如果未建立数据库连接，处理错误：

```
if (!$dbc) {
    trigger_error ('Could not connect to MySQL: ' . mysqli_connect_error() );
```

如果脚本无法连接到数据库，错误消息应发送给 **`my_error_handler()`** 函数。这样，错误将根据当前设置的管理技术（上线阶段与开发阶段）进行处理。我们不直接调用 **`my_error_handler()`**，而是使用 **`trigger_error()`**，其第一个参数是错误消息。

![Image](graphics/circle-c.jpg)

![Image](graphics/18_figure_08_c.jpg)

![Image](graphics/circle-c.jpg) 网站开发期间发生的数据库连接错误。

**5.** 设置编码：

```
} else {
    mysqli_set_charset($dbc, 'utf8');
}
```

如果能够建立数据库连接，则建立用于与数据库通信的编码。详情请参见[第 9 章](#ch09.html#ch09) “[将 PHP 与 MySQL 结合使用](#ch09.html#ch09)”。

**6.** 将文件保存为 **`mysqli_connect.php`**，并将其放置在 Web 文档根目录的上一级目录中。

此脚本作为一个可包含文件，同样省略了结束的 PHP 标签。与本书中的其他示例一样，理想情况下该文件不应位于 Web 目录中，但无论您将其放在何处，请确保 **`config.inc.php`** 中 **`MYSQL`** 常量的值相匹配。

**7.** 创建数据库。

![Image](graphics/circle-d.jpg)

![Image](graphics/18_figure_09_d.jpg)

![Image](graphics/circle-d.jpg) 创建本章使用的数据库。

有关数据库的讨论以及创建该表所需的命令，请参见侧边栏“[数据库方案](#ch18.html#ch18sb02)”。如果您无法创建自己的数据库，只需将该表添加到您有权访问的任何数据库中即可。此外，请确保编辑 **`mysqli_connect.php`** 文件，使其使用正确的用户名/密码/主机名组合来连接到该数据库。

> **提示**
>
> 一方面，为了方便参考，将两个配置文件的内容放在一个脚本中似乎讲得通。但遗憾的是，这样做会给不需要数据库连接的脚本（例如 **`index.php`**）带来不必要的开销（即连接并选择数据库）。

> **提示**
>
> 通常，应在配置文件或单独的函数文件中定义通用函数。一个例外是任何需要数据库连接的函数。如果您知道某个函数仅用于也连接到 MySQL 的页面上，那么在 **`mysqli_connect.php`** 脚本中定义该函数是合乎逻辑的。

### 数据库方案

该应用程序使用的数据库称为 *ch18*。该数据库目前仅包含一张表：*users*。要创建该表，请使用以下 SQL 命令：

```
CREATE TABLE users (
user_id INT UNSIGNED NOT NULL AUTO_INCREMENT,
first_name VARCHAR(20) NOT NULL,
last_name VARCHAR(40) NOT NULL,
email VARCHAR(60) NOT NULL,
pass CHAR(40) NOT NULL,
user_level TINYINT(1) UNSIGNED NOT NULL DEFAULT 0,
active CHAR(32),
registration_date DATETIME NOT NULL,
PRIMARY KEY (user_id),
UNIQUE KEY (email),
INDEX login (email, pass)
);
```

到目前为止，该表的大部分结构应该对您很熟悉；它与本书多个示例中使用的 *sitename* 数据库中的 *users* 表非常相似。一个新增内容是 *active* 列，它将指示用户是否已激活其账户（通过单击注册邮件中的链接）。该列将存储 32 字符长的激活码，或具有 **`NULL`** 值。因为 *active* 列可能具有 **`NULL`** 值，所以不能将其定义为 **`NOT NULL`**。如果您将 *active* 定义为 **`NOT NULL`**，则没有人能够登录（稍后您将在本章中了解原因）。另一个新增内容是 *user_level* 列，它将区分站点拥有的用户类型。
