

## 创建主电影列表页面

因此，上述代码更好的查询方式如下：

```
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

当用户点击某个特定电影标题的链接时，我们希望将 `movieListing` 表中该行的主键作为查询参数发送到 `moviedetails.php` 页面。因此，我们希望将 `$row['id']` 作为查询参数发送。

在 `index.php` 中，将清单 15.7 中的代码：

```
<?php
while($row = mysqli_fetch_assoc($result)):
?>
<tr>
<td><?=$row['title']?></td>
</tr>
<?php
endwhile;
?>
```

替换为：

```
<?php
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

清单 15.8 展示了现在 `index.php` 文件的 `<body>` 标签内代码应有的样子。

```
<?php
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

## 15. 显示项目详细信息列表

清单 15.8。

```
1. <body>
2.   //...
3.   <h1>Movies I Like</h1>
4. 
5.   <?php
6.     require_once('dbconnection.php');
7. 
8.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
9.       or trigger_error(
10.      'Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR
11.      );
12. 
13.     $query = "SELECT id, title FROM movielisting ORDER BY title";
14. 
15.     $result = mysqli_query($dbc, $query)
16.       or trigger_error('Error querying database movielisting', E_USER_ERROR);
17. 
18.     if (mysqli_num_rows($result) > 0):
19. ?>
20.     <table class="table table-striped">
21.       <thead>
22.         <tr>
23.           <th scope="col">Movie Title</th>
24.         </tr>
25.       </thead>
26.       <tbody>
27. <?php
28.     while($row = mysqli_fetch_assoc($result))
29.     {
30.       echo "<tr><td>" .
31.         "<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
32.     }
33. ?>
34.       </tbody>
35.     </table>
36. <?php
37.     else:
38. ?>
39. <h3>No Movies Found :-(</h3>
40. <?php
41.     endif;
42. ?>
43.   // ...
44. </body>
```

图 15.14 展示了现在主电影列表页面的样子。

## 创建电影详情页面

现在，我们创建一个 `moviedetails.php` 页面，用于显示从电影列表页面中选定电影的详细信息。

## 布局详情页面

使用 Bootstrap CSS 框架和条纹表格，图 15.15 展示了我们希望电影详情页面呈现的样子。

## 编写详情页面脚本

创建另一个 PHP 脚本，并将其命名为 `moviedetails.php`。同样，我们将从一个简单的样板代码开始，其中包含必要的 Bootstrap 框架组件，并将页面标题设置为“电影详情”。我们还会在开始的 `<body>` 标签正下方添加几个嵌套的 `<div>` 标签，以便以 Bootstrap 所称的“卡片”形式显示电影（清单 15.9）。

清单 15.9。

```
<html>
<head>
  <link rel="stylesheet"
        href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
        integrity="sha384-GJzZqFGwb1QTTN6wy59ff1BuGJPjLSa9dKkMpo8giM4m1Yj7gZgWKYBI7O6tWS"
        crossorigin="anonymous">
  <title>Movie Details</title>
</head>
<body>
<div class="card">
  <div class="card-body">
  </div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
        integrity="sha384-q8i/X+965DzO0rT7abK+1JSTQIAgVvRZvpzbo5smXKp4YfRVH+8abtTE1Pj6jizo"
        crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
        integrity="sha384-wHafrFfR..."
        crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
        integrity="sha384-B0UglyR+jN..."
        crossorigin="anonymous"></script>
</body>
</html>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_169_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_169_1.png)

## 15. 显示项目详细信息列表

现在，在最内层的 `<div>` 标签中，添加一个导航链接，返回主电影列表页面“我喜欢的电影”，如清单 15.10 所示。

### 清单 15.10。

```
```html
1. <body>
2.   <div class="card">
3.     <div class="card-body">
4.       <nav class="nav">
5.         <a class="nav-link" href="index.php">Movies I Like</a>
6.       </nav>
7.     </div>
8. </div>
```
```

我们只希望在用户从某个电影标题链接进入页面时显示所选电影的详细信息，而不是在用户直接将 `moviedetails.php` 输入 URL 地址栏时显示（图 15.16）。

图 15.17 展示了从电影列表页面到电影详情页面的不正确导航方式。

如果用户通过在 URL 地址栏中输入 `moviedetails.php` 的方式错误地访问页面，我们希望显示图 15.18。

因此，我们需要添加一个 `if` 条件，用于检查是否接收到了查询参数并为其设置了值。

在此之前，我们需要了解 `$_GET[]` 超级全局变量。

## 超级全局变量 `$_GET`

与 `$_POST[]` 类似，`$_GET[]` 是一个超全局数组变量。当表单发送数据时，它可以保存表单数据；它也可以保存嵌入 URL 中、作为数据传递的查询参数。

从表单发送 GET 请求时，数据会自动发送，并使用 `name` 属性作为数组中的索引键进行访问。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_2.png)

## 创建电影详情页面

当数据作为查询参数嵌入 URL 时，会以键值对的形式构成 URL 的一部分。数组中的每个值都使用前面提到的键作为索引。请参见图 15.19。

将清单 15.11 中的 PHP 条件代码块添加到我们刚刚添加的导航链接下方。

### 清单 15.11。

```
```php
1. <nav class="nav">
2. <a class="nav-link" href="index.php">Movies I Like</a>
3. </nav>
4. <?php
5.     if (isset($_GET['id'])):
6. 
7.     else:
8. ?>
9. <h3>No Movie Details :-</h3>
10. <?php
11. endif;
12. ?>
```
```

我们只希望在用户因为从主页选择了某个电影列表链接而导航到此页面时，显示电影列表的详细信息。因此，我们会将获取并显示电影列表详细信息的代码放在 `if` 和 `else` 语句之间。

在 `if` 和 `else` 子句之间，添加代码，从 `movielisting` 表中获取所有字段，其中 `id` 字段等于 `$_GET['id']` 指定的值。我们需要使用通常的样板代码来连接数据库并执行查询，如清单 15.12 所示。

### 清单 15.12。

```
```php
1. <?php
2. if (isset($_GET['id'])):
3. 
4.     require_once('dbconnection.php');
5. 
6.     $id = $_GET['id'];
7. 
8.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
9.         or trigger_error('Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR);
10. 
11.     $query = "SELECT * FROM movielisting WHERE id = $id";
12. 
13.     $result = mysqli_query($dbc, $query)
14.         or trigger_error('Error querying database movielisting', E_USER_ERROR);
15. else:
16. ?>
```
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_171_0.png)

## 15. 显示项目详细信息列表

此查询应当只返回一行，我们应该确保它始终如此；如果没有返回一行，则显示没有电影详情。对查询结果调用 `mysqli_num_rows()` 函数，可以获得查询返回的行数。

在 `mysqli_query()` 函数下方添加以下 `if` 和 `else` 条件子句（清单 15.13），并在内部 `else` 子句之后、`endif` 之前的 `<h3>` 标签中再次输出没有电影详情的提示：

### 清单 15.13。

```
$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database movieListing', E_USER_ERROR);

    if (mysqli_num_rows($result) == 1):
    else:
    ?>
<h3>No Movie Details :-</h3>
<?php
    endif;
    else:
?>
<h3>No Movie Details :-</h3>
<?php
    endif;
?>
```

如果查询确实返回一行，我们就可以显示一个包含电影列表详细信息的表格。在以下语句的下方添加清单 15.14 中的代码：
`if (mysqli_num_rows($result) == 1):`

### 清单 15.14。

```
<?php
...
    if (mysqli_num_rows($result) == 1):

        $row = mysqli_fetch_assoc($result)
?>
<h1><?= $row['title'] ?></h1>
<table class="table table-striped">
    <tbody>
        <tr>
            <th scope="row">Rating</th>
            <td><?= $row['rating'] ?></td>
        </tr>
        <tr>
```

