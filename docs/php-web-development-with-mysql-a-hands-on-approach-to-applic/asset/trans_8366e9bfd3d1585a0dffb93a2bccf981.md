
## 完整代码列表

```php
$id = $_POST['id'];

$query = "DELETE FROM movielisting WHERE id = $id";

$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database movielisting', E_USER_ERROR);

header("Location: index.php");
exit;

elseif (isset($_POST['do_not_delete_movie_submission'])):

    header("Location: index.php");
    exit;

elseif (isset($_GET['id_to_delete'])):
    ?>
    <h3 class="text-danger">Confirm Deletion of the Following
        Movie Details:</h3><br/>
    <?php
    $id = $_GET['id_to_delete'];

    $query = "SELECT * FROM movielisting WHERE id = $id";

    $result = mysqli_query($dbc, $query)
        or trigger_error('Error querying database movielisting', E_USER_ERROR);

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
                <th scope="row">Director</th>
                <td><?= $row['director'] ?></td>
            </tr>
            <tr>
                <th scope="row">Running Time (minutes)</th>
                <td><?= $row['running_time_in_minutes'] ?></td>
            </tr>
            <tr>
                <th scope="row">Genre</th>
                <td><?= $row['genre'] ?></td>
```
## 17. 使用 Web 应用程序删除数据

```php
73. </tr>
74. </tbody>
75. </table>
76. <form method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
77. <div class="form-group row">
78. <div class="col-sm-2">
79. <button class="btn btn-danger" type="submit" name="delete_movie_submission">
80. Delete Movie
81. </button>
82. </div>
83. <div class="col-sm-2">
84. <button class="btn btn-success" type="submit" name="do_not_delete_movie_submission">
85. Don’t Delete
86. </button>
87. </div>
88. </div>
89. <input type="hidden" name="id" value="<?= $id ?>">
90. </form>
91. <?php
92. else:
93. ?>
94. <h3>No Movie Details :-</h3>
95. <?php
96. endif;
97. else: // Unintended page link - No movie to remove, go back to index
98. header("Location: index.php");
99. exit;
100. endif;
101. ?>
102. </div>
103. </div>
104. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
105. integrity="sha384-DzOOrT7b6V8o9c6jUq3o1rFz4gf1a8tT6trf1OaTjHppL5" crossorigin="anonymous"></script>
106. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
107. integrity="sha384-wHAIFRlmFYg5s5Q8K5" crossorigin="anonymous"></script>
108. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
109. integrity="sha384-BOgVL0Yy2x8K" crossorigin="anonymous"></script>
110. </body>
111. </html>
```

## 练习

- 1. 在电影列表页面添加一个可点击的垃圾桶图标（每个电影一个），以便用户可以删除单个电影。
- 2. 创建删除电影页面以显示电影详情和删除确认。
- 3. 奖励：切换行为以使用软删除并标记电影不显示。更新列表和详情页面以隐藏标记为“deleted.”的电影。

## 第18章

### 使用 Web 应用程序编辑数据

> > “I develop for Linux for a living. I used to develop for DOS. Going from DOS to Linux is like trading a glider for an F117.”
> >
> > —Lawrence Foard, entropy@world.std.com

## 18. 使用 Web 应用程序编辑数据

本章中，我们将向我们的 *Movie Listing* 应用程序添加编辑电影列表数据的能力。

由于我们已经拥有添加和删除电影的能力，我们大概也应该添加编辑电影列表的能力。从电影的“Movie Details”页面，我们希望导航到一个带有表单的页面，该表单允许我们修改所有电影详情。成功编辑电影数据后，我们希望被带回该电影的“Movie Details”页面，以便立即看到更改的反映。

> > 请注意，您通常希望限制谁可以编辑数据库中的项目。后续关于 *security* 的章节展示了如何通过用户登录正确限制对 Web 应用程序编辑数据的访问。

### 将电影详情链接到编辑页面

在 moviedetails.php 脚本的闭合 </table> 元素之后添加一条水平线和一个链接到（尚未编写的）editmovie.php 脚本：

```html
</table>
<hr/>
<p>If you would like to change any of the details of this movie, feel free to <a href='editmovie.php?id_to_edit=<?=$row['id']?>'> edit it</a></p>
```

更新后的“Movie Details”页面应如下图 18.1 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_212_0.png)

当我们运行更新后的 moviedetails.php 脚本时，我们可以看到将鼠标悬停在“edit it”上时，我们的目的地超链接是 editmovie.php 脚本以及查询参数 id_to_edit 设置为我们感兴趣的编辑电影的主键，如图 18.2 所示。

该查询参数包含在 $row['id'] 中，并将通过 $_GET[] 超全局数组发送。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_212_1.png)

### 创建编辑页面

我们创建一个 `editmovie.php` 脚本，它显示的表单与“Add a Movie” `addmovie.php` 脚本基本相同。不同之处在于我们使用数据库中的电影详情预先填充表单输入。此外，我们使用 `addmovie.php` 脚本中的相同 Bootstrap 验证代码，以防用户无意中从表单中删除了必填字段。当我们为想要更新的电影选择“edit it”时，我们的浏览器应带我们到如下图 18.3 所示的页面。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_213_0.png)

### DRY（不要重复自己）

为了更易于维护并减少代码重复，您应该重用相同的 `addmovie.php` 表单标记和代码。您可以使用 PHP 的 `require_once`[^1] 语句在 `addmovie.php` 和 `editmovie.php` 脚本中实现这一点。我们将把这作为练习留给您。

[1] `require_once`: https://php.net/require_once

## 18. 使用 Web 应用程序编辑数据

### 第一步骤

首先，我们将在 <body> 元素内设置的 <h1> 标签中显示“Edit a Movie”标题：

```html
<body>
    <div class="card">
        <div class="card-body">
            <h1>Edit a Movie</h1>
```

接下来，让我们创建一个链接返回到 index.php 页面，如果用户不想更新此电影，以及一条水平线（<hr/> 元素）：

```html
<body>
<div class="card">
    <div class="card-body">
        <h1>Edit a Movie</h1>
        <nav class="nav">
            <a class="nav-link" href="index.php">Movies I Like</a>
        </nav>
        <hr/>
```

与之前的“Remove a Movie”页面一样，我们需要访问我们想要编辑的电影的数据库，因此我们需要包含我们的 dbconnection.php 脚本并连接到我们的 Movie 数据库，如列表 18.1 所示。

### 列表 18.1.

```
1. <body>
2.     <div class="card">
3.         <div class="card-body">
4.             <h1>Edit a Movie</h1>
5.         <p><a class='nav-link' href='index.php'>Movies I Like</a></p>
6.     <hr/>
7.         <?php
8.             require_once('dbconnection.php');
9. 
10.            $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
11.                or trigger_error(
12.                    'Error connecting to MySQL server for' . DB_NAME,
13.                    E_USER_ERROR
14.                );
```

### 预见通往编辑页面的路径

有两种预期方式和各种非预期方式可以导航到 editmovie.php 脚本。第一种预期方式是用户在“Movie Details”页面上选择“edit it”链接，如图 18.4 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_215_0.png)

这样会发送一个包含在 $_GET 超全局变量的 id_to_edit 元素中的单个查询参数。

第二种预期方式是当用户选择“Update Movie”时。当用户在表单字段中成功输入所需数据并提交表单时，我们希望在 Movie 数据库的 movieListing 表中更新此电影的数据。您可以在 $_POST 超全局变量中找到提交的表单字段。

所有其他机制都是非预期的。因此，这基本上给了我们三个我们正在寻找的选择。因此，最好的处理这三个选择的方法是在列表 18.2 中创建 if/elseif/else 代码结构。

### 列表 18.2.

```
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
    );

if (isset($_GET['id_to_edit']))
{
    // ...
}
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
        $_POST['movie_rating'], $_POST['movie_director'],
        $_POST['movie_running_time_in_minutes']))
{
    // ...
}
else // Unintended page link
{
    // ...
}
```

> 在上面的 elseif 代码块中：即使我们在客户端验证字段输入，在服务器端验证字段输入仍然很重要。
