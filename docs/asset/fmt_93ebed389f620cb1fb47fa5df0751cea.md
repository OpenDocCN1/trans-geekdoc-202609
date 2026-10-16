
### 在删除页面上显示图片

最后，我们需要修改 `removemovie.php`，以便在“移除影片”页面上显示影片图片，从而更好地识别影片。在确认删除时，我们需要从数据库和文件系统中删除图片文件。我们将把图片添加到表格的左侧，使其看起来像图 19.26 所示。

打开 `removemovie.php`，在脚本顶部引用 `dbconnection.php` 的后面，添加以下 `require_once()` 来引用 `movieimagefileutil.php` 脚本：

```php
<?php
    require_once('dbconnection.php');
    require_once('movieimagefileutil.php');
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_289_0.png)

### 在 removiemovie.php 上显示图片

最初链接到“移除影片”页面（`removiemovie.php`）时，是由于从 `index.php` 脚本导航时选择了垃圾桶图标而发起 HTTP GET 请求/响应。因此，我们需要在 `elseif (isset($_GET['id_to_delete']))` 代码块中进行以下修改，以显示影片图片文件的详细信息：

```php
elseif (isset($_GET['id_to_delete'])):
 // ...
 if (mysqli_num_rows($result) == 1)
 {
  $row = mysqli_fetch_assoc($result);
  $movie_image_file = $row['image_file'];
  if (empty($movie_image_file))
  {
   $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
  }
 }
```

与我们在 `addmovie.php` 和 `editmovie.php` 中所做的一样，我们需要将影片图片文件（或默认图片）添加到表格的左侧，以显示影片详细信息。

因为我们使用的是 Bootstrap 的 Flexbox 网格实现，所以我们可以将图片和表格封装在单独的列中，并将它们放入同一行。所有这些都位于 `<h1>` 元素中的影片标题下方，如清单 19.34 所示。

```php
<h1><?= $row['title'] ?></h1>
<div class="row">
 <div class="col-2">
  <img src=... class="img-thumbnail" style="max-height: 200px;" alt="Movie image">
 </div>
</div>
<div class="col">
 ...
```

```
<table class="table table-striped">
...
</table>
</div>
</div>
</p>
<form ... >
```

再次注意，我们将 `style` 属性设置为最大高度 200 像素。

## 删除电影时移除电影图像

在用户通过选择“Delete Movie”按钮提交表单数据后，如图 19.27 所示，以下条件为真。这是因为用户选择了“Delete Movie”提交按钮，该按钮将表单变量 `delete_movie_submission` 和 `id` 以 `$_POST[]` 超全局数组的形式回传到 `removemovie.php`。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_291_0.png)

```
if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):
```

在此块中，在我们查询删除此电影之前，我们需要从 `movieListing` 数据库表中查询 `image_file` 字段，并在 `images/` 文件夹中删除图像——仅当 `image_file` 字段不为空时才通过调用 `removeMovieImageFile()`。请在清单 19.35 中进行代码修改。

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
