

# 第 17 章：创建数据库和表

## 创建数据库

要创建数据库，可以编写以下 SQL 命令：

```sql
CREATE DATABASE dbname;
```

你也可以通过访问 **phpMyAdmin** 来创建数据库。phpMyAdmin 是一个用于 MySQL 和 MariaDB 的免费开源管理工具。作为一个主要用 PHP 编写的便携式 Web 应用程序，它已成为最流行的 MySQL 管理工具之一。请查看下面的截图：

![图示 10：phpMyAdmin 界面](image_rsrcE4.jpg)

MySQL 是用于存储数据的关系型数据库。

## 从 PHP 代码连接 MySQL 数据库

要从 PHP 代码连接数据库，我们需要编写代码来建立连接。

```php
<?php
$servername = "hostname or ip address";
$username = "mysql username";
$password = "mysql password";

/* 使用下面的代码创建连接 */
$connection = mysqli_connect($servername, $username, $password);

/* 添加代码检查连接 */
if (!$connection) {
    die("Connection failed: " . mysqli_connect_error());
}

echo "Connected successfully";
?>
```

如果连接创建成功，则连接将会成功；否则，它将打印一条错误，指出连接未创建。

## 如何创建数据库

你可以通过两种方式创建数据库：

1.  进入 phpMyAdmin 并点击 **Databases（数据库）** 选项卡。点击后，将出现一个选项，你可以在其中输入所需的数据库名称并点击 **Create（创建）** 按钮。
2.  进入 phpMyAdmin 并点击 **SQL** 选项卡。粘贴查询：
    ```sql
    CREATE DATABASE `database_name`;
    ```
    然后点击 **Go（执行）** 按钮。上述查询将被执行，数据库将被创建。

## 创建表

现在我们需要在数据库中创建表。我已经创建了一个名为 `myproject` 的数据库。现在我将在这个数据库下创建表。我将在数据库 `myproject` 下创建一个表 `category`。

当你创建好数据库后，可以看到它会出现在 phpMyAdmin 界面的左侧。从这里，你将点击数据库 `myproject`。这样它就被选中了。现在你可以看到一个 **Create table（创建表）** 选项。在屏幕上的文本框中输入表名和列数（即你想要的表字段）。

![表创建步骤 1](image_rsrcE5.jpg)

现在我输入名称为 `category`，列字段输入 `4`，然后点击 **Go（执行）** 按钮。表 `category` 将被创建，并会要求你输入列名以及表中列名所需的数据类型。

![表创建步骤 2](image_rsrcE6.jpg)

现在点击 **Go（执行）** 按钮，表将被创建。

你也可以在 phpMyAdmin 的 SQL 选项卡下运行下面的查询并执行查询来创建表：

```sql
CREATE TABLE `myproject`.`category` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(64) NOT NULL,
  `status` CHAR(1) NOT NULL,
  `sort_order` TINYINT(1) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE = InnoDB;
```

# 第 18 章：PHP 中的 Session

## 什么是 Session？

Session 以变量的形式存储在服务器上。它们通常用于存储网页访问者的偏好设置，并在多个网页中识别他们。当我们关闭网页或退出应用程序时，Session 就会过期。

## 如何在 PHP 中创建 Session？

我们使用 `$_SESSION` 超全局变量来创建 Session。要创建 Session，我们需要先启动 Session，然后将变量存储在 Session 中。

```php
session_start();
$_SESSION['username'] = 'your_username';
```

## 如何检查 Session 是否已设置？

要检查 Session 变量是否已设置，可以对该 Session 变量使用 `isset()` 函数。

```php
if (isset($_SESSION['username'])) {
    /* 你的代码片段 */
}
```

## 如何结束 Session？

当我们不再需要 Session 时，可以取消设置 Session 变量并销毁它。

```php
session_start();
unset($_SESSION['username']);
session_destroy();
```

## 我们在哪里使用 Session？

Session 用于存储任何用户的登录详细信息，以便他们可以访问其他网页，我们也可以跟踪用户。当用户通常注销时，他们的 Session 会过期并离开应用程序。

# 第 19 章：PHP 项目 - 用户注册

现在我们将创建一个小型 PHP 项目，我们将在其中创建数据库和表。然后我们将创建一个小型项目，用户将在其中注册、登录并导航到网站上的受限页面。

## 创建数据库

运行下面的查询以创建数据库：

```sql
CREATE DATABASE `user_registration`;
```

选择数据库并复制下面的代码。在 SQL 选项卡下粘贴后执行查询以创建表 `users`：

```sql
CREATE TABLE `user_registration`.`users` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(255) NOT NULL,
  `type` ENUM('user','admin') NOT NULL,
  `username` VARCHAR(64) NOT NULL,
  `password` VARCHAR(255) NOT NULL,
  `status` CHAR(1) NOT NULL DEFAULT 'A',
  PRIMARY KEY (`id`)
) ENGINE = InnoDB;
```

## 项目结构

现在我们创建一个名为 `user_registration` 的项目文件夹。在这个文件夹下，我们将保存 PHP 文件、CSS、JS 和图片。我们的项目将具有以下文件结构：

![项目文件结构](image_rsrcE7.jpg)

我创建了一个名为 `ReadersCollection` 的文件夹。在里面，我创建了我的项目文件夹 `user_registration`。该文件夹包含 `index.php`，这是主注册页面。其他页面包括登录页面、受限页面和一个 `process.php` 页面。`process.php` 页面是我们将编写所有代码逻辑的地方。我创建了一个 `connection.php` 页面，其中包含连接数据库的代码。

主注册页面的截图：

![主注册页面](image_rsrcE8.jpg)

此文件夹包含一个 `css` 文件夹和一个 `js` 文件夹。`css` 文件夹包含 `bootstrap.css` 文件，`js` 文件夹包含 `bootstrap.js` 文件。我没有在此处包含它们。你可以去 Bootstrap 网站下载相应的文件并将它们包含在你的项目中。

## `connection.php` 的代码

此页面将包含在每个 PHP 页面的顶部。

```php
<?php
session_start();

$servername = "localhost";
$username = "root";
$password = "";
$dbname = 'user_registration';

/* 使用下面的代码创建连接 */
$connection = mysqli_connect($servername, $username, $password, $dbname);

/* 添加代码检查连接 */
if (!$connection) {
    die("Connection failed: " . mysqli_connect_error());
}

// echo "Connected successfully";
?>
```

## 注册功能

注册表单包含三个输入框：姓名、用户名和密码。用户名应唯一，密码应以加密形式存储。注册或索引页面的代码如下：

### `index.php` 的代码

```php
<!DOCTYPE html>
<?php
include "connection.php";
?>
<html>
<head>
    <title></title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/bootstrap.css">
    <script src="js/bootstrap.js"></script>
</head>
<body>
    <div class="container text-center">
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <ul class="navbar-nav mr-auto">
                <?php
                if (isset($_SESSION['username'])) {
                ?>
                <li class="nav-item active"><a href="restricted.php">Restricted Page | </a></li>
                <?php } ?>
                <?php if (!isset($_SESSION['username'])) { ?>
                <li class="nav-item active"><a href="login.php">Login |</a></li>
                <?php } ?>
                <?php if (isset($_SESSION['username'])) { ?>
                <li class="nav-item active"><a href="process.php?action=logout">Logout</a></li>
                <?php } ?>
            </ul>
        </nav>

        <?php if (!isset($_SESSION['username'])) { ?>
        <div class="row">
            <div class="col-md-12">
                <div class="row"><strong>Register here</strong></div>
            </div>
        </div>

        <form name="frm" method="post" action="process.php?action=register">
            <div class="row">
                <div class="col-md-12">
                    <div class="col-md-6">Name:</div>
                    <div class="col-md-6"><input type="text" name="name" value=""></div>
                </div>
                <div class="col-md-12">
                    <div class="col-md-6">UserName:</div>
                    <div class="col-md-6"><input type="text" name="username" value=""></div>
                </div>
            </div>
        </form>
        <?php } ?>
    </div>
</body>
</html>
```

