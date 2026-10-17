
```php
66.  *              is returned for the path.
67.  *
68.  * @return string  Path to movie image file IF a file was uploaded
69.  *                 AND moved to the ML_UPLOAD_PATH (images/) folder,
70.  *                 otherwise an empty string.
71.  */
72. function addMovieImageFileReturnPathLocation()
73. {
74.     $movie_file_path = "";
75. 
76.     // Check for $_FILES being set and no errors.
77.     if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
78.     {
79.         $movie_file_path = ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];
80. 
81.         if (!move_uploaded_file($_FILES['movie_image_file']['tmp_name'],
82.                                 $movie_file_path))
83.         {
84.             $movie_file_path = "";
85.         }
86.     }
87. 
88.     return $movie_file_path;
89. }
```

## 19. 处理文件和对现有代码的功能添加

### 在 addmovie.php 上使用文件上传函数

现在我们已经有了用于验证和添加上传的电影图像文件的两个函数，我们可以回到修改`addmovie.php`以使用这些函数。

您应该已经修改了表单元素并添加了用于上传电影图像文件的 input file 元素。如果没有，请参阅上方了解如何操作。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_254_0.png)

在用户通过选择图 19.16 所示的 Add Movie 按钮提交表单数据后，表单数据可在检查表单数据是否设置在`$_POST`超全局变量中的 if 块内使用：

```php
if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes']))
{

```

我们希望在此 if 块内验证文件，将其移动到`images/`文件夹，并将路径保存到数据库。

首先，在`require_once dbconnection.php`脚本之后立即添加对`movieimagefileutil.php`脚本的`require_once`，以便我们可以使用创建的两个函数：

```php
if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes']))
{
    require_once('dbconnection.php');
    require_once('movieimagefileutil.php');
```

我们将在检查`checked_movie_genres`是否设置之后，并在连接到数据库的调用之前验证上传的电影图像文件。因此，在此处添加适当的注释可能是一个好主意，如清单 19.9 所示。

### 清单 19.9.

```php
1. if (isset($checked_movie_genres))
2. {
3.     $movie_genre_text = implode(", ", $checked_movie_genres);
4. }
5.
6. /*
7. Here is where we will deal with the file by calling validateMovieImageFile().
8. This function will validate that the movie image file is the right image type
9. (jpg/png/gif), and not greater than 512KB. This function will return an empty
10. string ('') if the file validates successfully, otherwise, the string will
11. contain error text to be output to the web page before redisplaying the form.
12. */
```

接下来，我们调用`validateMovieImageFile()`并将返回值设置为捕获文件错误消息的新变量：

```php
successfully. Otherwise, the string will contain error text to be output to
the web page before redisplaying the form.
*/

$file_error_message = validateMovieImageFile();
```

如果`validateMovieImageFile()`返回的不是空字符串，则上传文件时出现错误。我们希望显示此错误消息并重新显示表单，而不是将数据存储到数据库中，以便用户可以更正错误。错误的两个常见原因是：图像太大，或图像文件类型错误。这也意味着我们需要使用户已输入的字段保持粘性，以便他们不必重新输入到表单中（除非他们想更改它们）。

> *参见章节：在第 18 章《使用 Web 应用程序编辑数据》中设置字段值使其保持粘性，以回顾如何使输入字段保持粘性。*

为`file_error_message`为空创建一个 if 条件，并将所有数据库代码、表结果和添加另一部电影的链接都移动到这个新的 if 块中。新的 if 块应如下清单 19.10 所示。

### 清单 19.10.

```php
$file_error_message = validateMovieImageFile();
if (empty($file_error_message))
{
    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for' . DB_NAME,
            E_USER_ERROR
        );
    $query = "INSERT INTO movielisting (title, rating, director, "
        . " running_time_in_minutes, genre) "
        . "VALUES ('$movie_title', '$movie_rating', '$movie_director', "
        . "'$movie_runtime', '$movie_genre_text')";
    mysqli_query($dbc, $query)
        or trigger_error(
            'Error querying database movieListing: Failed to insert movie listing',
            E_USER_ERROR
        );
    $display_add_movie_form = false;
?>
<h3 class="text-info">The Following Movie Details were Added:</h3><br/>
<h1><?= $movie_title ?></h1>
<table class="table table-striped">
    <tbody>
        <tr>
            <th scope="row">Rating</th>
            <td><?= $movie_rating ?></td>
        </tr>
        <tr>
            <th scope="row">Director</th>
            <td><?= $movie_director ?></td>
        </tr>
        <tr>
            <th scope="row">Running Time (minutes)</th>
            <td><?= $movie_runtime ?></td>
        </tr>
        <tr>
            <th scope="row">Genre</th>
            <td><?= $movie_genre_text ?></td>
        </tr>
    </tbody>
</table>
<hr/>
<p>Would you like to <a href="<?= $_SERVER['PHP_SELF'] ?>"> add another movie</a></p>
<?php
}
```

### 处理文件上传错误

为了处理用户尝试上传文件时遇到的错误，我们需要修改上述代码。但是，首先，让我们在 if 之后添加一个 else 条件，以便我们可以输出错误消息，如清单 19.11 所示。

### 清单 19.11.

```php
1. if (empty($file_error_message))
2. {
3.     //...
4. }
5. else
6. {
7.     // echo error message
8.     echo "<h5><p class='text-danger'>" . $file_error_message . "</p></h5>";
9. }
```

请注意，如果此 `else` 执行，表单将被重新显示，因为`display_add_movie_form`已经设置为 true。

在回到修改 if 块中的代码之前，让我们使表单保持粘性以处理 else 块中的错误条件。在脚本顶部，刚好在初始化`$display_add_movie_form = true;`的行下方，添加以下变量清单 19.12，并将其初始化为空字符串和`null`。

### 清单 19.12.

```php
1. // Initialization
2. $display_add_movie_form = true;
3. 
4. $movie_title = "";
5. $movie_rating = "";
6. $movie_director = "";
7. $movie_runtime = "";
8. $movie_genre_text = "";
9. $checked_movie_genres = null;
```

这些值在用户提交表单后设置，在清单 19.13 中的 if 条件中，该条件检查`$_POST`表单变量是否已设置。

### 使用文件和对现有代码的功能添加

```php
if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
$_POST['movie_rating'], $_POST['movie_director'],
$_POST['movie_running_time_in_minutes']))
{
...
$movie_title = $_POST['movie_title'];
$movie_rating = $_POST['movie_rating'];
$movie_director = $_POST['movie_director'];
$movie_runtime = $_POST['movie_running_time_in_minutes'];
$checked_movie_genres = $_POST['movie_genre_checkbox'];
$movie_genre_text = "";

if (isset($checked_movie_genres))
{
$movie_genre_text = implode(", ", $checked_movie_genres);
}
}
```

如前所述，错误的两个常见原因是：图像太大，或图像的文件类型错误。因此，这给我们提供了三种可以测试的错误条件：

- 文件是正确的图像类型但太大。
- 文件是错误的图像类型但小于 `ML_MAX_FILE_SIZE`。
- 文件是错误的图像类型并且太大。

实现这些测试留作练习。你需要为每种情况编写一条错误消息。

我们现在可以使标题、评分、导演、播放时长和类型在表单中保持粘性。由于这与我们在“编辑电影”页面中所做的完全相同，我只在列表 19.14 中展示更新后的表单。

```html
<form enctype="multipart/form-data" class="needs-validation" novalidate method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
<div class="form-group row">
<label for="movie_title" class="col-sm-3 col-form-label-lg">Title</label>
<div class="col-sm-8">
<input type="text" class="form-control" id="movie_title" name="movie_title" value="<?= $movie_title ?>" placeholder="Title" required>
<div class="invalid-feedback">
Please provide a valid movie title.
</div>
</div>
</div>
...
```

```html
</div>
</div>
<div class="form-group row">
    <label for="movie_rating" class="col-sm-3 col-form-label-lg">Rating</label>
    <div class="col-sm-8">
        <select class="custom-select" id="movie_rating"
            name="movie_rating" value="<?php $movie_rating ?>"
            required>
            <option value="" disabled selected>Rating...</option>
            <option value="G" <?php $movie_rating == 'G' ?
                'selected' : '' ?>>G
            </option>
            <option value="PG" <?php $movie_rating == 'PG' ?
                'selected' : '' ?>>PG
            </option>
            <option value="PG-13" <?php $movie_rating == 'PG-13' ?
                'selected' : '' ?>>PG-13
            </option>
            <option value="R" <?php $movie_rating == 'R' ?
                'selected' : '' ?>>R
            </option>
        </select>
        <div class="invalid-feedback">
            Please select a movie rating.
        </div>
    </div>
</div>
<div class="form-group row">
    <label for="movie_director"
        class="col-sm-3 col-form-label-lg">Director</label>
    <div class="col-sm-8">
        <input type="text" class="form-control"
            id="movie_director" name="movie_director"
```
