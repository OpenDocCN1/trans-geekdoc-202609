

![](img/0f886a7f4cbcc3939be96e985ca35ff4_19_0.png)

## MVC 分层

为了帮助你理解 MVC 的优势，让我们看看如何将一个基本的 PHP 应用程序转换为 MVC 架构的应用程序。博客应用程序的帖子列表将是一个完美的示例。

### 扁平化编程

在一个扁平的 PHP 文件中，显示数据库条目列表可能就像清单 2-1 中所示的脚本。

### 清单 2-1 - 扁平脚本

```php
<?php

// Connecting, selecting database
$link = mysql_connect('localhost', 'myuser', 'mypassword');
mysql_select_db('blog_db', $link);

// Performing SQL query
$result = mysql_query('SELECT date, title FROM post', $link);

?>

<html>
<head>
<title>List of Posts</title>
</head>
<body>
<h1>List of Posts</h1>
<table>
<tr><th>Date</th><th>Title</th></tr>
<?php
// Printing results in HTML
while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    echo "</tr>\n";
    printf("<td>%s</td>\n", $row['date']);
    printf("<td>%s</td>\n", $row['title']);
    echo "</tr>\n";
}
?>
</table>
</body>
</html>

<?php

// Closing connection
mysql_close($link);
?>

```

编写快速，执行迅速，却难以维护。这段代码的主要问题如下：

- 没有错误检查（如果数据库连接失败怎么办？）。
- HTML 和 PHP 代码混在一起，甚至交织在一起。
- 代码与 MySQL 数据库绑定。

### 隔离表现层

清单 2-1 中的 echo 和 print 调用使代码难以阅读。使用当前语法修改 HTML 代码以增强表现效果很麻烦。因此，可以将代码分为两部分。首先，包含所有业务逻辑的纯 PHP 代码放在控制器脚本中，如清单 2-2 所示。

### 清单 2-2 - 控制器部分，位于 index.php 中

```php
<?php

// Connecting, selecting database
$link = mysql_connect('localhost', 'myuser', 'mypassword');
mysql_select_db('blog_db', $link);

// Performing SQL query
$result = mysql_query('SELECT date, title FROM post', $link);

// Filling up the array for the view
$posts = array();
while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    $posts[] = $row;
}

// Closing connection
mysql_close($link);

// Requiring the view
require('view.php');
```

包含类模板 PHP 语法的 HTML 代码存储在视图脚本中，如清单 2-3 所示。

### 清单 2-3 - 视图部分，位于 view.php 中

```
<html>
  <head>
  <title>List of Posts</title>
  </head>
  <body>
    <h1>List of Posts</h1>
    <table>
      <tr><th>Date</th><th>Title</th></tr>
      <?php foreach ($posts as $post): ?>
      <tr>
        <td><?php echo $post['date'] ?></td>
        <td><?php echo $post['title'] ?></td>
      </tr>
      <?php endforeach; ?>
    </table>
  </body>
</html>
```

判断视图是否足够简洁的一个好经验是：它应该只包含最少量的 PHP 代码，以便没有 PHP 知识的 HTML 设计师也能理解。视图中最常见的语句是 echo、if/endif、foreach/endforeach，基本上就这些。此外，不应有 PHP 代码输出 HTML 标签。

所有逻辑都已移至控制器脚本，该脚本仅包含纯 PHP 代码，不包含任何 HTML。事实上，你可以想象同一个控制器可以重复用于完全不同的表现形式，例如 PDF 文件或 XML 结构。

### 隔离数据操作

控制器脚本中的大部分代码都用于数据操作。但是，如果你需要为另一个控制器（例如输出博客文章 RSS 源的控制器）获取帖子列表，该怎么办？如果你想将所有数据库查询保存在同一位置，以避免代码重复，该怎么办？如果你决定更改数据模型，将 post 表重命名为 weblog_post，该怎么办？如果你想从 MySQL 切换到 PostgreSQL，该怎么办？为了实现所有这些可能性，你需要从控制器中删除数据操作代码，并将其放入另一个称为模型的脚本中，如清单 2-4 所示。

### 清单 2-4 - 模型部分，位于 model.php 中

```php
<?php

function getAllPosts()
{
  // Connecting, selecting database
  $link = mysql_connect('localhost', 'myuser', 'mypassword');
  mysql_select_db('blog_db', $link);

  // Performing SQL query
  $result = mysql_query('SELECT date, title FROM post', $link);

  // Filling up the array
  $posts = array();
  while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
  {
    $posts[] = $row;
  }
// Closing connection
mysql_close($link);

return $posts;
}
```

修订后的控制器如清单 2-5 所示。

### 清单 2-5 - 控制器部分（修订版），位于 index.php 中

```php
<?php

// Requiring the model
require_once('model.php');

// Retrieving the list of posts
$posts = getAllPosts();

// Requiring the view
require('view.php');
```

控制器变得更易于阅读。它的唯一任务是从模型获取数据并将其传递给视图。在更复杂的应用程序中，控制器还处理请求、用户会话、身份验证等等。在模型中使用明确的函数名称，甚至使控制器中的代码注释变得多余。

模型脚本专用于数据访问，并可以相应地组织。所有不依赖于数据层（例如请求参数）的参数都必须由控制器提供，而不是由模型直接访问。模型函数可以轻松地在另一个控制器中重用。

### 超越 MVC 的层分离

因此，MVC 架构的原则是根据代码的性质将其分为三层：数据逻辑代码放在模型中，表现代码放在视图中，应用逻辑放在控制器中。

其他附加设计模式可以使编码体验更加轻松。模型、视图和控制器层可以进一步细分。

### 数据库抽象

模型层可以拆分为数据访问层和数据库抽象层。这样，数据访问函数将不使用依赖数据库的查询语句，而是调用其他将自行执行查询的函数。如果日后更改数据库系统，只需更新数据库抽象层。

清单 2-6 展示了一个数据库抽象层示例，随后是清单 2-7 中 MySQL 特定数据访问层的示例。

### 清单 2-6 - 模型的数据库抽象部分

```php
<?php

function open_connection($host, $user, $password)
{
    return mysql_connect($host, $user, $password);
}

function close_connection($link)
{
    mysql_close($link);
}

function query_database($query, $database, $link)
{
    mysql_select_db($database, $link);

    return mysql_query($query, $link);
}

function fetch_results($result)
{
    return mysql_fetch_array($result, MYSQL_ASSOC);
}
```

### 清单 2-7 - 模型的数据访问部分

```php
function getAllPosts()
{
    // Connecting to database
    $link = open_connection('localhost', 'myuser', 'mypassword');

    // Performing SQL query
    // $result = query_database('SELECT date, title FROM post', 'blog_db',
    $link);

    // Filling up the array
    $posts = array();
    while ($row = fetch_results($result))
    {
        $posts[] = $row;
    }

    // Closing connection
    close_connection($link);

    return $posts;
}
```

你可以检查数据访问层中没有任何依赖数据库引擎的函数，从而使其与数据库无关。此外，数据库抽象层中创建的函数可以重复用于许多其他需要访问数据库的模型函数。

> 清单 2-6 和 2-7 中的示例仍然不够理想，要实现完全的数据库抽象（例如通过数据库无关的查询构建器抽象 SQL 代码、将所有函数移入类中等）还有许多工作要做。但本书的目的不是教你手动编写所有这些代码，你将在第 8 章中看到 symfony 原生支持出色的抽象。

