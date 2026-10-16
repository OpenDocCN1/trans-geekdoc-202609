
```
<table class="table table-striped">
...
</table>
</div>
</div>
</p>
<form ... >
```

再次注意，我们将 style 属性设置为最大高度 200 像素。

## 删除电影时移除电影图像

在用户通过选择“Delete Movie”按钮提交表单数据后，如图 19.27 所示，以下条件为真。这是因为用户选择了“Delete Movie”提交按钮，该按钮将表单变量 delete_movie_submission 和 id 以 $_POST[] 超全局数组的形式回传到 removemovie.php。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_291_0.png)

```
if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):
```

在此块中，在我们查询删除此电影之前，我们需要从 movieListing 数据库表中查询 image_file 字段，并在 images/ 文件夹中删除图像——仅当 image_file 字段不为空时才通过调用 removeMovieImageFile()。请在清单 19.35 中进行代码修改。

清单 19.35.

```
if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):

$id = $_POST['id'];

// Query image file from DB
$query = "SELECT image_file FROM movieListing WHERE id = $id";

$result = mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing', E_USER_ERROR
    );

if (mysqli_num_rows($result) == 1)
{
    $row = mysqli_fetch_assoc($result);

    $movie_image_file = $row['image_file'];

    if (!empty($movie_image_file))
```

## 19. 处理文件和对现有代码的功能添加

```
20.     {
21.         removeMovieImageFile($movie_image_file);
22.     }
23. }
24.
25. $query = "DELETE FROM movieListing WHERE id = $id";
26.
27. $result = mysqli_query($dbc, $query)
28.     or trigger_error(
29.         'Error querying database movieListing', E_USER_ERROR
30.     );
31.
32. header("Location: index.php");
33. exit;
```

## 完整的 removemovie.php 清单

清单 19.36.

```
1. <html>
2. <head>
3.     <title>Remove a Movie</title>
4.     <link rel="stylesheet"
5.         href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
6.         integrity="sha384-GJzZqFGwbQ1TTNyGwy59ffF1BuGJpLSa9DkKmp0Dgi/Dn4iVMj7oZgZKVbI70e4t/S"
7.         crossorigin="anonymous">
8.     <link rel="stylesheet"
9.         href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
10.        integrity="sha384-50bUHMevpQ6fxV12ZB4EF1Qzzqfh2cXFjTjwX..."
11.        crossorigin="anonymous">
12. </head>
13. <body>
14. <div class="card">
15.     <div class="card-body">
16.         <h1>Remove a Movie</h1>
17. <?php
18.     require_once('dbconnection.php');
19.     require_once('movieimagefileutil.php');
20.
21. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
22.     or trigger_error(
23.         'Error connecting to MySQL server for' . DB_NAME,
24.         E_USER_ERROR
25.     );
26.
27. if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):
28.
29.     $id = $_POST['id'];
30.
```

## 19. 处理文件和对现有代码的功能添加

```
```php
if (mysqli_num_rows($result) == 1) {
    $row = mysqli_fetch_assoc($result);

    $movie_image_file = $row['image_file'];

    if (empty($movie_image_file)) {
        $movie_image_file =
            ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    }
?>
<h1><?= $row['title'] ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file ?>"
             class="img-thumbnail"
             style="max-height: 200px;"
             alt="Movie image">
    </div>
    <div class="col">
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
                </tr>
            </tbody>
        </table>
    </div>
</div>
<p>
<form method="POST"
      action="<?= $_SERVER['PHP_SELF'] ?>">
    <div class="form-group row">
        <div class="col-sm-2">
            <button class="btn btn-danger" type="submit"
                    name="delete_movie_submission">
                Delete Movie
            </button>
        </div>
    </div>
</form>
```
```

## 第 20 章

## 基本 HTTP 身份验证

> > “首先，解决问题。然后，再编写代码。”
> >
> > —John Johnson

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_297_0.png)

## 20. 基本 HTTP 身份验证

目前，我们的 *MovieListing* 应用程序没有任何保护，任何人都可以简单地删除我们数据库中的所有电影，或添加我们可能不批准的电影条目。

在本章中，我们实现基本 HTTP 身份验证，为我们不希望向所有人公开的应用程序功能增加一层保护。

在后续的关于安全的章节中，我将进一步讨论身份验证和授权。基本 HTTP 身份验证是控制谁可以使用特定网页的一种简单方法。

问题是，我们希望对哪些功能要求身份验证？鉴于我们的应用程序允许任何人访问整个网站，我们需要对修改或删除应用程序数据的任何功能添加基本身份验证。这将限制只有知道有效用户名和密码组合的可信用户才能更改数据库。因此我们将要求对以下内容进行身份验证：

- `addmovie.php`
- `removemovie.php`
- `editmovie.php`

## 使用 HTTP 身份验证的密码保护

用户应该能够通过单击图 20.1 所示的链接添加电影，删除电影（图 20.2），或通过图 20.3 中的链接编辑电影详细信息。在执行这些操作之前，我们希望显示图 20.4 所示的授权对话框，或类似的对话框，以验证其身份。您看到的确切对话框因浏览器和操作系统而异。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_298_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_298_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_298_2.png)

### HTTP 身份验证是如何工作的？

只要用户输入错误的凭据，该对话框就会继续弹出。只有使用正确的凭据登录后，用户才能添加、编辑或删除电影详细信息。

如果用户按下“取消”，图 20.5 中的消息会显示在页面上。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_299_0.png)

### HTTP 身份验证是如何工作的？

HTTP 身份验证使用 HTTP 头发送。每次用户请求网页时，在返回任何 HTML 之前，服务器都会向客户端发送用于验证用户身份的头。您应该注意，虽然您可以使用 HTTP 进行基本身份验证，但用户名和密码未加密，可能会被拦截。如果您必须使用基本身份验证，请确保在生产站点上使用 HTTPS。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_299_1.png)

头控制客户端和服务器之间传递的信息类型和方式。头通常（但不总是）由冒号 (:) 分隔的名称/值对组成。

> > 注意：有关 HTTP 请求和响应头的更多信息，请参阅第 1 章：HTTP 请求/响应

在 PHP 中，我们使用 header() 函数创建 HTTP 头并将其从脚本发送出去。

由于头必须在任何 HTML 标记之前发送，因此它必须是 PHP 代码中的第一件事。<?php 标签之前不能有任何空行。此外，在 header() 调用之前您包含或引用的任何其他文件都不得向浏览器发送任何输出。

```
[1] header(): https://php.net/header
```
