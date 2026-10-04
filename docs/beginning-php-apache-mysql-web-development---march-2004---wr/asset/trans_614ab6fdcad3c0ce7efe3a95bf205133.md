

## 第12章

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_408_0.png)
图 12-6

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_408_1.png)
图 12-7

386

## 构建内容管理系统

10. 我们将跳过接下来两个菜单项（稍后会回到这里）。现在，点击[注销](#链接。

11. 接下来，点击登录，并点击“创建一个新账户！”。你应该看到一个与图 12-8 类似的屏幕。

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_409_0.png)
图 12-8

12. 在每个字段中输入数据并点击“创建账户”。在本示例中，我们将输入以下内容：

- 全名：George Smith
- 电子邮件地址：gsmith05523@hotmail.com
- 密码：phprocks
- 密码（再次）：phprocks

一旦你创建了新用户，将自动以该用户的身份登录。你会注意到你可以看到最近创建的文章，但无法看到“审核 (Review)”或“管理员 (Admin)”项目。审核仅对版员（Moderators）或管理员（级别 2 或 3）可用，而管理员仅对管理员（级别 3）可用。你的初始账户是按级别 3 创建的，但你刚刚创建的账户默认是级别 1（用户）。

## 第12章

### 13. 点击控制面板。

你应该会看到一个与图 12-9 显示的屏幕。在这里，你可以更改用户信息（用户名和电子邮件），并查看为网站编写了哪些文章。（此时，你没有待处理或已撰写的的文章）。

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_410_0.png)
图 12-9

14. 继续进行注销，然后使用你的管理员账户重新登录。登录后，点击[管理员](#链接)。你应该会看到一个与图 12-10 类似的屏幕。

你应该会在“用户 (Users)”下看到 George Smith（或你使用的任何名称）。你会在“管理员 (Admins)”下看到你的管理员名称，但它不是链接。你可以从控制面板更改你的账户。

## 构建内容管理系统

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_411_0.png)

15. 点击“用户 (Users)”下列出的用户。

你会看到一个与图 12-11 类似的页面。注意，你可以像在控制面板中一样更改用户名和密码。然而，还请注意增加了“访问级别 (Access Level)”选项。你可以将任何用户设置为用户、版员或管理员。用户是新用户的默认设置。

这就是你的新 CMS 应用程序了。并不复杂，对吧？你还可以做一些其他事情（例如撤回已发表的文章），但我们将这些留给你自己去发现。现在，是时候看看内部原理，看看这东西是如何运作的了！

图 12-10

389

## 第12章

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_412_0.png)

## 工作原理

此 CMS 应用程序由十九个文件组成。额外的文件使用一次来创建表，总共 20 个文件。这对你来说可能看起来很多，但事务页面和包含文件的使用大幅增加了文件数量。如果你不将应用程序拆分为单独的文件，你的文件会少一些，但每个文件都会大得多。我们将应用程序拆分成许多文件的主要目的是减少冗余。

## 连接到数据源

创建此应用程序的第一步是连接到数据库。你的大多数页面都需要此连接，因此将其放在单独的包含文件中是最佳解决方案。文件为 `conn.php`：

```php
define('SQL_HOST', 'yourhost');
define('SQL_USER', 'jouser');
define('SQL_PASS', 'yourpassword');
define('SQL_DB', 'yourdatabase');

$conn = mysqli_connect(SQL_HOST, SQL_USER, SQL_PASSWORD);
```

390

or die('Could not connect to the database; ' . mysql_error());

`conn.php` 中的代码仅定义了常量、连接到服务器，然后选择要使用的数据库。如果你使用多个数据库，只需要在运行任何 SQL 命令之前更改 `mysql_select_db` 命令以访问相应的数据库。

## 创建数据库表

一旦创建了 `conn.php`，你就可以创建数据库表。使用 CMStables.php 完成此操作。

首先，连接数据库。

```php
require_once 'conn.php';
```

接下来，创建访问级别所需的表。所有的字段、数据类型和其他参数都在此 SQL 语句中定义。我们使用 `NOT EXISTS` 是为了确保当表已存在时不执行 `CREATE` 命令。如果你希望 `CMStables.php` 创建一个新的、干净版本的程序，可以使用 `IF EXISTS` 并运行 SQL

```php
$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_levels (
access_lvl int(4) NOT NULL auto_increment,
access_name varchar(50) NOT NULL default '',
PRIMARY KEY (access_lvl)
)EOS;
$result = mysql_query($sql) or die($mysql_error());
```

接下来在你创建的 `cms_levels` 表插入数据。这些访问级别在 CMS 应用程序中用于确定哪些用户拥有

```php
$sql = "INSERT IGNORE INTO cms_levels VALUES (1, 'User');";
$result = mysql_query($sql) or die($mysql_error());
```

我们将包含 CMStables.php 中的每个 SQL 语句。如果你足够了解这本书

```php
$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_articles (
article_id int(4) NOT NULL auto_increment,
title varchar(255) NOT NULL,
body mediumtext,
is_published tinyint(1) NOT NULL default 0,
date_submitted datetime NOT NULL,
author_id int(4) NOT NULL,
PRIMARY KEY (article_id)
)EOS;
$result = mysql_query($sql) or die($mysql_error());
```

314

构建内容管理系统

## 可复函数

```php
/**
 * 将字符串裁剪到指定的长度并添加省略号。
 *
 * @param string $theText 要裁剪的文本。
 * @param int $len 字符串的最大长度。
 * @param string $schar 要搜索的字符。
 * @param int $scnt 搜索字符的次数。
 * @return string 裁剪后的文本。
 */
function trimBody($theText, $len=500, $schar="\n", $scnt=2) {
  // 初始化变量
  $pos = 0;
  $trimmed = FALSE;

  // 如果文本太长，循环 $scnt 次以找到第n出现
  for ($i = 1; $i <= $scnt; $i++) {
    if ($tmp = strpos($theText, $schar, $pos)) {
      $pos = $tmp;
      $trimmed = TRUE;
    } else {
      $pos = strlen($theText) - 1;
      $trimmed = FALSE;
      break;
    }
  }

  // 将文本裁剪到找到的位置
  $theText = substr($theText, 0, $pos);

  // 如果返回的字符串超过了你的限制，将其裁剪到精确长度
  if (strlen($theText) > $len) {
    $theText = substr($theText, 0, $len);
  }

  // 在此之后，你可能切断单词。回溯到最后一个空格
  if ($trimmed) {
    $theText = substr($theText, 0, strpos($theText, ' '));
    $trimmed = TRUE;
  }

  // 如果你对文本进行了任何裁剪，添加所有的省略号
  if ($trimmed) {
    $theText .= '...';
  }

  return $theText;
}
```

