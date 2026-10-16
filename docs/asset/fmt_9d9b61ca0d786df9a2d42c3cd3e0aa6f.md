
```php
4.   <a class="nav-link" href="index.php">Movies I Like</a>
5.   </nav>
6.   <?php
7.   if (isset($_GET['id'])):
8. 
9.     require_once('dbconnection.php');
10. 
11.     $id = $_GET['id'];
12. 
13.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
14.       or trigger_error('Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR);
15. 
16.     $query = "SELECT * FROM movieListing WHERE id = $id";
17.
18. $result = mysqli_query($dbc, $query)
19.     or trigger_error('Error querying database movieListing', E_USER_ERROR);
20. 
21.     if (mysqli_num_rows($result) == 1):
22. 
23.         $row = mysqli_fetch_assoc($result)
24.     ?>
25. <h1><?= $row['title'] ?></h1>
26. <table class="table table-striped">
27.     <tbody>
28.         <tr>
29.             <th scope="row">Rating</th>
30.             <td><?= $row['rating'] ?></td>
31.         </tr>
32.         <tr>
33.             <th scope="row">Director</th>
34.             <td><?= $row['director'] ?></td>
35.         </tr>
36.         <tr>
37.             <th scope="row">Running Time (minutes)</th>
38.             <td><?= $row['running_time_in_minutes'] ?></td>
39.         </tr>
40.         <tr>
41.             <th scope="row">Genre</th>
42.             <td><?= $row['genre'] ?></td>
43.         </tr>
44.     </tbody>
45. </table>
46.     <?php
47.     else:
48.     ?>
49. <h3>No Movie Details :- (</h3>
50. <?php
51. endif;
52.     else:
53.     ?>
54. <h3>No Movie Details :- (</h3>
55. <?php
56. endif;
57. ?>
58. // ...
59. </body>
```

## 15. 显示项目列表详情

图 15.20 显示了我们当前电影详情页面的样子。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_174_0.png)

## 练习

- 1. 创建电影列表数据库并通过 Adminer 或 `mysql` 控制台添加数据。
- 2. 创建索引页面以显示所有电影。
- 3. 创建电影详情页面以显示单个电影的信息。将索引页面上的标题链接到正确的详情页面。

## Chapter 16

> “在我自以为是的观点里，大多数人的 C 程序应该向下缩进六英尺并被泥土覆盖。”
> 
> - Blair P. Houghton

## 16. 使用 Web 应用程序添加数据

本章为我们在上一章创建的 *电影列表* 应用程序添加了添加电影列表数据的功能。

在创建列出各种类型数据的应用程序时，提供使用 Web 界面添加数据的能力也是合理的期望。例如，让我们创建一个脚本，允许用户添加新的电影列表数据。

> *请注意，通常你希望限制谁可以向数据库添加项目。在后续的安全章节中，我将向你展示如何通过用户登录正确限制 Web 应用程序添加数据的访问权限。*

### 创建添加电影的页面

我们首先创建 `addmovie.php` 页面，向用户显示用于输入所有电影列表数据的表单。当用户提交表单时，数据将被验证并插入到 `Movie` 数据库的 `MovieListing` 表中。

### 创建“添加电影”表单

图 16.1 显示了我们首次导航到它时“添加电影”页面应有的样子。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_178_0.png)

### 初始页面布局

创建另一个 PHP 脚本并将其命名为 `addmovie.php`。再次，我们将从一个简单的样板开始，其中包含必要的 Bootstrap 框架组件，并将页面标题命名为：“Add a Movie”。我们还将在开始的 `<body>` 标签下方添加几个嵌套的 `<div>` 标签，以在 Bootstrap 卡片中显示我们的电影。参见列表 16.1

### Listing 16.1.

```html
1. <html>
2.   <head>
3.     <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
4.         integrity="sha384-GJzZqFGwb1QTTN6wy59FF1B9UjLpsa9dkK4p0DgiM4n4YmJ0gZKYbI706tWs"
5.         crossorigin="anonymous">
6.     <title>Add a Movie</title>
7.   </head>
8.   <body>
9.     <div class="card">
10.     <div class="card-body">
11. 
12.     </div>
13.   <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
14.         integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpboSrnXKp4YfRvH+8abtTE1P1gJizo"
15.         crossorigin="anonymous"></script>
16.   <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
17.         integrity="sha384-wHAiFfRlUXYxN1YsNxM4hV8LlPp9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo"
18.         crossorigin="anonymous"></script>
19.   <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
20.         integrity="sha384-B0UglyR+jN8VA0sKNWPaJzYfRvH+8abtTE1P1gJizo"
21.         crossorigin="anonymous"></script>
22. </body>
23. </html>
```

现在在最内层的 `<div>` 标签内，在 `<h1>` 标签中向我们的页面添加标题“Add a Movie”，随后是返回主电影列表页面“Movies I Like”的 `<nav>` 链接，然后是水平线，如列表 16.2 和图 16.2 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_179_0.png)

### Listing 16.2.

```html
<body>
  <div class="card">
    <div class="card-body">
      <h1>Add a Movie</h1>
      <nav class="nav">
        <a class="nav-link" href="index.php">Movies I Like</a>
      </nav>
      <hr/>
    </div>
  </div>
```

接下来，我们想要显示我们的表单。稍后，我们将添加条件代码以在首次导航到 `addmovie.php` 页面时或出现验证错误时显示我们的表单。

你会注意到我在表单中的文本输入元素中添加了占位符文本，如图 16.3 所示。此文本不应替代使用标签元素：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_180_0.png)

```html
<form ...>
  <div class="form-group row">
    <label for="movie_title" class="col-sm-3 col-form-label-lg">Title</label>
    <div class="col-sm-8">
      <input type="text" class="form-control" id="movie_title" name="movie_title" placeholder="Title" required>
    ...
```

> Bootstrap 使用许多 `div` 元素和 `class` 属性进行样式设置，尤其是在使用其基于 Flexbox[1] 的网格布局系统时。有关如何使用 Bootstrap 的网格布局[2] 系统（版本 4.3）的更多信息，请参阅在线文档。

[1] 弹性盒子: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
[2] 网格布局: https://getbootstrap.com/docs/4.3/layout/grid/

### 使用复选框创建类型数组

一部电影可以属于多个类型。由于我们想要为“Genre”包含各种选择，因此需要使用复选框（图 16.4）。如果我们创建一个包含我们类型的数组，也能减少 HTML 标记的重复。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_181_0.png)

列表 16.3 显示了“Genre”的 PHP 代码和 HTML 标记是什么样子的。

### Listing 16.3.

```php
<?php
$genres = [
    'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
    'Fantasy', 'Horror', 'Romance', 'Science Fiction'
];
?>
// ...

<?php
foreach ($genres as $genre)
{
?>
<div class="form-check form-check-inline col-sm-3">
    <input class="form-check-input" type="checkbox"
        id="movie_genre_checkbox_action"
        name="movie_genre_checkbox[]"
        value="<?= $genre ?>"
    <label class="form-check-label"
        for="movie_genre_checkbox_action"><?= $genre ?></label>
</div>
<?php
}
?>
```

前面的代码和标记为我们`$genres`数组中的每个项目创建一个复选框输入。用户选择的每个类型都会被添加到`movie_genre_checkbox`数组中（请注意`name`属性中添加的`[]`）。请注意，如果用户未选择任何类型，`movie_genre_checkbox` name 属性将不存在于`$_POST[]`超全局数组中。

### 表单的 PHP 代码和 HTML 标记

*表单的 PHP 代码和 HTML 标记*

Listing 16.4 是整个表单的 PHP 代码和 HTML 标记的样子。

### 列表 16.4.

```php
<?php
$genres = [
    'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
    'Fantasy', 'Horror', 'Romance', 'Science Fiction'
];
?>
...

<form class=&quot;needs-validation&quot; novalidate method=&quot;POST&quot;
    action=&quot;<?=$_SERVER['PHP_SELF']?>"
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_title&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Title</label>
<div class=&quot;col-sm-8&quot;>
    <input type=&quot;text&quot; class=&quot;form-control&quot; id=&quot;movie_title&quot;
        name=&quot;movie_title&quot; placeholder=&quot;Title&quot; required>
    <div class=&quot;invalid-feedback&quot;>
        Please provide a valid movie title.
    </div>
</div>
</div>
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_rating&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Rating</label>
<div class=&quot;col-sm-8&quot;>
    <select class=&quot;custom-select&quot; id=&quot;movie_rating&quot;
        name=&quot;movie_rating&quot; required>
        <option value=&quot;&quot; disabled selected>Rating...</option>
        <option value=&quot;G&quot;>G</option>
        <option value=&quot;PG&quot;>PG</option>
        <option value=&quot;PG-13&quot;>PG-13</option>
        <option value=&quot;R&quot;>R</option>
    </select>
    <div class=&quot;invalid-feedback&quot;>
        Please select a movie rating.
    </div>
</div>
</div>
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_director&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Director</label>
<div class=&quot;col-sm-8&quot;>
    <input type=&quot;text&quot; class=&quot;form-control&quot; id=&quot;movie_director&quot;
        name=&quot;movie_director&quot; placeholder=&quot;Director&quot; required>
```

### 创建添加电影的页面

```html
<div class="invalid-feedback">
    Please provide a valid movie director.
</div>
</div>
</div>
<div class="form-group row">
    <label for="movie_running_time_in_minutes" class="col-sm-3 col-form-label-lg">Running Time (min)</label>
    <div class="col-sm-8">
        <input type="number" class="form-control"
```
