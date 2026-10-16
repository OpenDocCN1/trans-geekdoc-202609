

### 在详情页面上显示电影图片

```html
<th scope="row">Genre</th>
<td><?= $row['genre'] ?></td>
</tr>
</tbody>
</table>
</div>
</div>
<hr/>
<p class="nav-link">
    If you would like to change any of the details of
    this movie, feel free to
    <a href="editmovie.php?id_to_edit=<?= $row['id'] ?>">edit it</a>
</p>
<?php
else:
?>
<h3>No Movie Details :-)</h3>
<?php
endif;
else:
?>
<h3>No Movie Details :-)</h3>
<?php
endif;
?>
</div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
    integrity="sha384-q8i/X+965DzOzUjtlsu2Y9MRQgxUq5MYxNFkZInk+..."
    crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
    integrity="sha384-wHAiF1R1..."
    crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
    integrity="sha384-B0Uglyr+..."
    crossorigin="anonymous"></script>
</body>
</html>
```

## 19. 处理文件及向现有代码添加功能

### 向编辑页面添加图片文件上传功能

现在，新电影可以有自定义的文件图片。我们需要在 editmovie.php 脚本中添加同样的能力，以上传电影图片以及电影的其他任何详细信息。这样，用户就可以用新图片更新现有的文件图片，或者为现有条目添加电影缩略图。

当我们因在“电影详情”页面上选择“编辑它”链接而导航到“编辑电影”页面时，我们应该会看到图 19.19。

我们希望在表单右侧添加电影图片，并在表单底部附近添加一个“选择文件”按钮（图 19.20）。

当选择要更新的图片时，会弹出一个文件浏览窗口。然后，用户可以导航到想要上传的图片文件，选中它，然后像图 19.21 那样按下“打开”。

所选文件的名称会显示在“选择文件”按钮之后，而不是“未选择文件”。见图 19.22。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_276_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_276_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_276_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_276_3.png)

一旦我们选择“更新电影”（图 19.23），我们希望看到“电影详情”页面上显示的更新后的电影详细信息已经过我们上传的图片进行了修改，如图 19.24 所示。

首先，打开 editmovie.php 脚本，并在脚本顶部引用 dbconnection.php 的代码之后，添加以下 require_once()，以引用 movieimagefileutil.php 脚本：

```php
require_once('dbconnection.php');
require_once('movieimagefileutil.php');
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_277_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_277_1.png)

#### 编辑时显示电影图片详情

当第一次浏览到“编辑电影”页面（editmovie.php）时，是因为从“电影详情”页面导航过来时发生了一次 HTTP GET 请求/响应。因此，我们需要按照清单 19.24 进行修改，在 if (isset($_GET['id_to_edit'])) 代码块中添加电影图片文件的详细信息：

**清单 19.24。**

```php
if (isset($_GET['id_to_edit']))
{
    // ...
    if (mysqli_num_rows($result) == 1)
    {
        // ...
        $movie_genre_text = $row['genre'];
        $movie_image_file = $row['image_file'];

        if (empty($movie_image_file))
        {
            $movie_image_file_displayed = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
        }
        else
        {
            $movie_image_file_displayed = $movie_image_file;
        }

        $checked_movie_genres = explode(', ', $movie_genre_text);
    }
}
```

请注意，如果 `$movie_image_file` 为空，我们需要将 `$movie_image_file_displayed` 设置为默认的电影文件图片。`$movie_image_file_displayed` 用于在页面上表单右侧显示电影图片。

由于我们使用的是 Bootstrap 的 Flexbox 网格实现，最好将表单和图片分别封装在不同的列中，并将它们放在同一行中。按照清单 19.25 进行修改，将表单显示在左侧，图片显示在右侧。

**清单 19.25。**

```html
1. <div class="row">
2.   <div class="col">
3.     <form ...>
4.     // ...
5.     </form>
6.   </div>
7.   <div class="col-3">
8.     <img src="<?= $movie_image_file_displayed ?>" class="img-thumbnail"
9.          style="max-height: 400px;" alt="Movie image">
10.  </div>
11. </div>
```

请注意，我们将 style 属性设置为最大高度 400 像素。

#### 修改表单以允许文件上传

就像我们在 addmovie.php 中所做的那样，需要在 editmovie.php 的表单中添加两样东西以启用文件上传。首先，我们需要在 `<form>` 元素中添加 enctype 属性，并将其设置为 multipart/form-data：

```html
<form enctype="multipart/form-data" ...>
```

然后，我们需要向表单添加一个文件输入元素：

```html
<input type="file" class="form-control-file" id="movie_image_file"
       name="movie_image_file">
```

按照清单 19.26，将文件输入元素添加到表单中提交按钮之前的 Bootstrap form-group 行内。

**清单 19.26。**

```html
</div>
<div class="form-group row">
    <label for="movie_image_file"
        class="col-sm-3 col-form-label-lg">Movie Image File</label>
    <div class="col-sm-8">
        <input type="file" class="form-control-file" id="movie_image_file"
            name="movie_image_file">
    </div>
</div>
<button class="btn btn-primary" type="submit"
        name="edit_movie_submission">Update Movie</button>
</form>
```

关于 `$movie_image_file`，就像用于 id_to_update 的隐藏 `<input>` 元素一样，我在表单中创建了另一个隐藏的 `<input>` 元素，并将其设置为 `$movie_image_file` 的值，同时将 name 属性设置为 `movie_image_file`。当用户按下**更新电影**提交按钮、表单数据被回传到 editmovie.php 时，现有文件（更新之前）的名称将可在 `$_POST[]` 超全局数组中获得，这样如果用户选择了新文件，就可以将其删除（如果非空）：

```html
<input type="hidden" name="id_to_update" value="<?= $id_to_edit ?>">
<input type="hidden" name="movie_image_file" value="<?= $movie_image_file ?>">
```

> *请参阅第 17 章中的补充说明：**Web 是无状态的！***

#### 修改编辑代码以存储文件

在用户通过选择图 19.25 中的“更新电影”按钮提交表单数据后，表单数据可在 elseif 代码块中获得，该代码块用于检查 `$_POST` 超全局变量中是否设置了这些表单数据。请注意，我们在条件中添加了 `movie_image_file` 隐藏字段。

```php
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
              $_POST['movie_rating'], $_POST['movie_director'],
              $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'],
              $_POST['movie_image_file']))
{
```

在这个 `elseif` 代码块内部，我们需要验证文件，将其移动到 `images/` 文件夹，并修改数据库中 `movieListing` 表的 `image_file` 字段。

首先，在根据表单数据设置 `$id_to_update` 之后，立即创建一个名为 `$movie_image_file` 的变量，并将其设置为 `$_POST` 超全局变量中的隐藏变量：

```php
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'],
    $_POST['movie_image_file']))
{
    // ...
    $id_to_update = $_POST['id_to_update'];
    $movie_image_file = $_POST['movie_image_file'];
}
```

我们需要在检查 `checked_movie_genres` 是否已设置之后、连接数据库之前，测试是否为电影预先设置了图片文件。如果没有，将先前显示的电影设置为默认图片（清单 19.27）。

**清单 19.27。**

```php
1. if (isset($checked_movie_genres))
2. {
3.     $movie_genre_text = implode(", ", $checked_movie_genres);
4. }
5. 
6. if (empty($movie_image_file))
7. {
8.     $movie_image_file_displayed = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
9. }
10. else
11. {
12.     $movie_image_file_displayed = $movie_image_file;
13. }
```

与 addmovie.php 一样，我们将在连接数据库的调用之前验证上传的电影图片文件。在此处添加一条适当的注释可能是个好主意，例如清单 19.28 中的注释。

**清单 19.28。**

```php
1. else
2. {
3.     $movie_image_file_displayed = $movie_image_file;
4. }
5. 
6. /*
7. Here is where we will deal with the file by calling validateMovieImageFile().
8. This function will validate that the movie image file is not greater than 128
```

