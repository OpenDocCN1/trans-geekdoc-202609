

在 MySQL CLI 工具中运行此命令以创建用户并授予电影数据库的所有权限，我们可以看到图 15.1。

> 我们在授予其权限之前不需要创建数据库。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_155_0.png)

## 15. 显示项目详情列表

### 创建我们的电影数据库

使用浏览器，让我们以 `movieguru` 身份登录 Adminer 并创建数据库和表，如图 15.2 所示。

单击 `Create database`（图 15.3）。

输入 `Movie` 作为要创建的数据库名称并选择 `Save`，如图 15.4 所示。

您应该会看到图 15.5 中的页面，其中显示 Adminer 和已创建的 `Movie` 数据库。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_156_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_156_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_156_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_156_3.png)

现在我们想要创建表。选择 `Create table`，如图 15.6 所示。

输入 `movieListing` 作为表名：

对于 `id` 字段：

1. 在 `列名` 下输入 `id`
2. 将 `类型` 保持为 `int`
3. 选择 `AI` 单选按钮进行自动递增

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_157_0.png)

> 通过将字段命名为 `id` 并使其自动递增，Adminer 将设置此字段为该表的主键。

对于 `title` 字段：

1. 在 `id` 下方的 `列名` 中输入 `title`
2. 将 `类型` 选择为 `varchar`
3. 输入 `50` 作为长度

对于 `rating` 字段：

1. 在 `列名` 下 `title` 下方，输入 `rating`
2. 将 `类型` 选择为 `varchar`
3. 输入 `10` 作为长度

对于 `director` 字段：

1. 在 `列名` 下 `rating` 下方，输入 `director`
2. 将 `类型` 选择为 `varchar`
3. 输入 `25` 作为长度

对于 `running_time_in_minutes` 字段：

1. 在 `列名` 下 `director` 下方，输入 `running_time_in_minutes`
2. 将 `类型` 选择为 `int`

对于 `genre` 字段：

1. 在 `列名` 下 `running_time_in_minutes` 下方，输入 `genre`
2. 将 `类型` 选择为 `varchar`
3. 输入 `50` 作为长度

## 15. 显示项目详情列表

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_158_0.png)

然后选择 `Save`。图 15.7 是保存表之前“Create Table”表单应有的样子。

一旦您选择 `Save`，表描述应如下图 15.8 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_158_1.png)

### 添加电影数据

我们也可以使用 Adminer 向我们的表添加一些数据。例如，让我们为三部电影添加一些数据。IMDB[^1] 始终是查找电影信息的绝佳场所。

选择 `movieListing` 返回 Adminer 中的 `movieListing` 表。

要添加新的电影列表，请选择 `New item`，见图 15.9。

为以下标题添加以下电影列表数据（或您选择的任何标题）：

- Sleepless in Seattle
- Star Wars: The Force Awakens
- Deadpool

为 `Sleepless in Seattle` 添加以下列表数据（图 15.10）：

- `title`: Sleepless in Seattle
- `rating`: PG
- `director`: Nora Ephron
- `running_time_in_minutes`: 105
- `genre`: Comedy, Drama, Romance

为 `Star Wars: The Force Awakens` 添加以下列表数据：

- `title`: Star Wars: The Force Awakens
- `rating`: PG-13
- `director`: J.J. Abrams
- `running_time_in_minutes`: 135
- `genre`: Action, Adventure, Science Fiction, Fantasy

[1] IMDB: https://www.imdb.com

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_159_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_159_1.png)

## 15. 显示项目详情列表

添加以下列表数据用于 `Deadpool`：

- `标题`: Deadpool
- `评级`: R
- `导演`: Tim Miller
- `运行时间（分钟）`: 108
- `类型`: Action, Adventure, Comedy

选择 `保存并插入下一个` 用于前两个电影列表。这样会保存数据并刷新数据录入表单。对于最后一个，按 `保存`（图 15.11）。

选择 `保存` 后，`选择：movieListing` 页面显示（图 15.12），显示您输入的所有电影列表。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_160_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_160_1.png)

### 创建主电影列表页面

我们首先创建一个 `index.php` 页面，列出 `Movie` 数据库中 `movieListing` 表中的所有电影标题。

### 布局主页面

为了让页面看起来整洁，我使用 `Bootstrap` CSS 框架并使用条纹表格。图 15.13 显示了我们希望主电影列表的外观。

> 熟悉 `Bootstrap` CSS 框架
>
> 要了解更多关于 `Bootstrap` CSS 框架的信息并更熟练地使用它，请访问 https://getbootstrap.com 并点击 `开始使用` 按钮。在本书的这一版中，我将使用版本 4.2。

首先，让我们创建主电影列表脚本并将其命名为 `index.php`。我们从一个简单的样板开始，其中包含必要的 `Bootstrap` 框架组件，并将页面标题设为：“Movies I Like”。参见清单 15.1。

### 清单 15.1.

```html
<html>
<head>
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
integrity="sha384-GJzZQFQw1QTTNgwy59FfI1BuCjPlSa9DkKMP0Dg1M4i4Yj7g0ZJKYbI706tWS"
crossorigin="anonymous">
<title>Movies I Like</title>
</head>
<body>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
integrity="sha384-q8i/X+965DzO0rT7abK0W1sTQI..."
crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
integrity="sha384-wHAiFfRl..."
crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
integrity="sha384-B0Ugly..."
crossorigin="anonymous"></script>
</body>
</html>
```

[2] Bootstrap: https://getbootstrap.com

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_161_0.png)

## 15. 显示项目详情列表

### 存储数据库连接定义

接下来，让我们创建一个名为 `dbconnection.php` 的单独文件（清单 15.2）来存放我们的数据库凭据，我们将为其创建常量。由于我们在多个脚本中需要这些值，我们将它们存储在一个文件中，可以在整个应用程序中 `require` 或 `include`。

### 清单 15.2.

```php
<?php
  /* dbconnection.php */

  // Database connection constants
  define('DB_HOST', 'localhost');
  define('DB_USER', 'movieguru');
  define('DB_PASSWORD', 'ilikemovies');
  define('DB_NAME', 'Movie');
```

> 通常，您会使用环境变量来保存敏感信息，但对于这些示例来说，这已经足够了。

### 显示电影列表表

现在让我们创建主电影列表脚本并将其命名为 `index.php`。在打开的 `<body>` 标签之后立即显示标题“Movies I Like”。接下来，让我们回到 `index.php` 页面，并在打开的 `<body>` 标签下方添加几个嵌套的 `<div>` 标签，以在 Bootstrap 所谓的“card”中显示我们的电影，如清单 15.3 所示。

### 清单 15.3.

```html
<body>
  <div class="card">
    <div class="card-body">
    </div>
  </div>
  <script ...
  ...
</body>
</html>
```

在最内层的 `<div>` 标签内，添加一个 `<h1>` 标题，名为“Movies I Like”：

```html
<body>
  <div class="card">
    <div class="card-body">
      <h1>Movies I Like</h1>
```

### 创建主电影列表页面

接下来（在 `<h1>` 标签之后），我们将添加一些 PHP 代码来包含我们的数据库连接常量并连接到数据库（清单 15.4）。我们使用 `require_once()` 使 `dbconnection.php` 值对脚本可用，并确保在脚本运行时该文件只加载一次。

### 清单 15.4.

```php
<h1>Movies I Like</h1>

<?php
require_once('dbconnection.php');

$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error('Error connecting to MySQL server for DB_NAME.', E_USER_ERROR);
```

然后，我们将创建一个查询字符串，用于从 `movielisting` 表中获取所有电影的 `id`、`title` 字段并查询数据库：

```php
$query = "SELECT id, title FROM movielisting ORDER BY title";

$result = mysqli_query($dbc, $query)

    or trigger_error('Error querying database movielisting', E_USER_ERROR);
```

请注意，当我们导航到“Movie Details”页面时，我们需要每个电影列表的 `id`，以便查询并检索所选电影的详细信息。

此时，我们只想在数据库中有电影时显示电影表：

```php
if (mysqli_num_rows($result) > 0):

?>

    <table class="table table-striped">

        <thead>

            <tr>

                <th scope="col">Movie Title</th>

            </tr>

        </thead>

```

假设我们有电影可显示，此 `while` 循环会迭代并输出电影标题，如清单 15.5 所示。

## 15. 显示项目详情列表

### 清单 15.5.

```php
<tbody>

<?php

    while($row = mysqli_fetch_assoc($result)):

?>

        <tr>

            <td><?= $row['title'] ?></td>

        </tr>

<?php

endwhile;

?>

```

然后我们关闭 `<table>`：

```php
    </tbody>

    </table>
```

如果没有电影可列出，请添加 `else:` 条件，指示没有电影，然后关闭条件。这样的消息可以防止用户怀疑应用程序没有数据库或遇到错误或 bug。

```php
<?php

    else:

?>

    <h3>No Movies Found :-(</h3>

<?php

    endif;

?>

```

清单 15.6 是迄今为止 `index.php` 脚本中 `<body>`（和 `<div>`）标签内的代码应有的样子。

### 清单 15.6.

```php
<body>

    // ...

    <h1>Movies I Like</h1>

<?php

    require_once('dbconnection.php');

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)

        or trigger_error('Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR);

    $query = "SELECT id, title FROM movieListing ORDER BY title";

$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database movielisting', E_USER_ERROR);

if (mysqli_num_rows($result) > 0):
?>
    <table class="table table-striped">
    <thead>
        <tr>
            <th scope="col">Movie Title</th>
        </tr>
    </thead>
    <tbody>
<?php
    while($row = mysqli_fetch_assoc($result)):
?>
        <tr>
            <td><?= $row['title'] ?></td>
        </tr>
<?php
    endwhile;
?>
    </tbody>
    </table>
<?php
else:
?>
    <h3>No Movies Found :-(</h3>
<?php
endif;
// ...
</body>
```

### 将列表链接到详情页面

现在我们有了电影标题列表，我们希望为每部电影创建链接，将我们带到 `moviedetails.php` 页面。我们希望向 `moviedetails.php` 页面发送包含每部电影 `id` 字段的查询参数。查询参数通过 `$_GET` 超全局变量发送到 PHP 脚本。

### 使用 GET 与 POST

我们有两种选项可以在页面请求中发送数据。通常，这是为了发送要保存的表单数据或包含我们需要查找已保存数据的的信息。许多程序员可以互换使用 `GET` 和 `POST`，但它们对这些数据有不同的假设。

## 15. 显示项目详情列表

`POST` 的目的是更改服务器上的状态。因此，`POST` 通常用于表单和文件上传。

```html
<form method="POST" action="doSomethingGood.php">
```

`GET` 也可以从表单发送（将 `method` 属性设置为 `GET`）。但它假设数据不会以任何方式保存或持久化。一个典型的用途是搜索表单，用于发送您想要查找的关键字。

```html
<form method="GET" action="doSomethingGreat.php">
```

当 URL 包含查询参数时，这是一个 `GET` 请求。

