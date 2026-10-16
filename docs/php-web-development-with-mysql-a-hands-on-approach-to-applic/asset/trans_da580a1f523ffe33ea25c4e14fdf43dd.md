

### 清单18.8

```
<?php
foreach ($genres as $genre) {
?>
<div class="form-check form-check-inline col-sm-3">
<input class="form-check-input" type="checkbox"
id="movie_genre_checkbox_<?= $genre ?>"
name="movie_genre_checkbox[]"
value="<?= $genre ?>"<?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>
<label class="form-check-label"
for="movie_genre_checkbox_action_<?= $genre ?>"> <?= $genre ?></label>
</div>
<?php
}
?>
```

请注意，我在 value 属性中添加了是否选中该流派的信息，使用的是三元运算符：

```
... value="<?= $genre ?>" <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?> ...
```

在 addmovie.php 中，我们仅有：

```
... value="<?= $genre ?>" ...
```

然而，我们想知道某个特定流派是否被选中，而该信息包含在我们之前使用 `explode()` 函数创建的 `$checked_movie_genres` 数组中。使用 `in_array()` 函数，我们可以判断 `$genre`（当前在 `$genres` 数组的 foreach 循环中处理的流派）是否包含在 `$checked_movie_genres` 数组中。如果 `$genre` 存在，`in_array()` 返回 true，否则返回 false。我们可以使用三元运算符，在找到该流派时为其添加 `checked`（'checked'）属性，如果未找到则添加空字符串（' '）：

```
... <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?> ...
```

## 使用 Bootstrap 的客户端验证

与 addmovie.php 脚本一样，我们使用 Bootstrap 的客户端验证。这要求我们执行以下操作：

- 1. 将表单的 class 属性设置为 `needs-validation`，并添加 `novalidate` 属性：

```
<form class="needs-validation" novalidate ...
```

[3] in_array()：https://php.net/in_array

## 18. 使用 Web 应用编辑数据

- 2. 为输入元素标记 `required` 属性，以确保我们希望验证的字段得到验证：

```
<input type="number" ... required>
```

- 3. 添加 class 属性设置为 `invalid-feedback` 的 `<div>` 元素，其中包含我们希望用户忘记填写字段时看到的验证文本。同样，我们直接将这些元素添加到我们想要验证的 `<input>` 元素下方。清单 18.9 是“Running Time”输入字段的完整 HTML 标记，以及我们希望用户忘记输入值时看到的无效反馈。

### 清单18.9

```
1. <div class="form-group row">
2.   <label for="movie_running_time_in_minutes"
3.     class="col-sm-3 col-form-label-lg">Running Time (min)</label>
4.   <div class="col-sm-8">
5.     <input type="number" class="form-control"
6.       id="movie_running_time_in_minutes"
7.       name="movie_running_time_in_minutes"
8.       value="<?= $movie_runtime ?>"
9.       placeholder="Running Time (in minutes)" required>
10.     <div class="invalid-feedback">
11.       Please provide a valid running time in minutes.
12.     </div>
13.   </div>
14. </div>
```

- 4. 将清单 18.10 中的 JavaScript 代码添加到表单后的 `<script>` 标签中。

### 清单18.10

```
1. </form>
2. <script>
3. // JavaScript for disabling form submissions if there are invalid fields
4. (function() {
5.   'use strict';
6.   window.addEventListener('load', function() {
7.     // Fetch all the forms we want to apply custom Bootstrap validation styles to
8.     var forms = document.getElementsByClassName('needs-validation');
9.     // Loop over them and prevent submission
10.     var validation = Array.prototype.filter.call(forms, function(form) {
11.       form.addEventListener('submit', function(event) {
12.         if (form.checkValidity() === false) {
13.           event.preventDefault();
14.           event.stopPropagation();
15.         }
16.         form.classList.add('was-validated');
17.       }, false);
18.     });
19.   }, false);
20. }());
21. </script>
```

## DRY？

*这看起来像是在重复 addmovie.php 脚本中的代码，不是吗？在这种情况下，由于我们使用的是样板式的 Bootstrap 验证代码，将 JavaScript 代码放在表单下方的匿名函数中更合理。*

## 按下更新按钮

这是我们导航到 editmovie.php 页面的第二种预期方式。因此，我们将处理 `elseif` 块：

```
```php
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'])) {
```
```

当我们进入此条件时，是因为用户点击了 **Update Movie** 提交按钮。这样会将表单变量 `edit_movie_submission`、`movie_title`、`movie_rating`、`movie_director`、`movie_running_time_in_minutes` 和 `id_to_update` 通过 POST 方式回传到 editmovie.php，并存储在 `$_POST[]` 超全局数组中。注意，由于流派是可选的，我们不检查它是否已设置。

说到 `id_to_update`，请注意我在表单中创建了一个隐藏的 `<input>` 元素，并将其值设置为电影的 ID，同时将 name 属性设置为 `id_to_update`。当表单数据被回传到 editmovie.php 时，该 ID 可在 `$_POST[]` 超全局数组中获得，以便在数据库中更新它：

```
```html
<input type="hidden" name="id_to_update" value="<?= $id_to_edit ?>">
```
```

我们需要这样做，以便承载最初调用 editmovie.php 时通过查询参数发送的电影 ID。请记住，HTTP 请求和响应不保留任何状态或信息。

> *请参阅上一章中题为“WEB 是无状态的！”的补充说明。*

当第一次进入传入表单或查询参数的条件时，我为每个参数创建了单独的变量。同样，这不是必需的，如果你为表单字段创建了描述性名称并使用 `$_POST` 超全局变量访问它们，代码同样可读。然而，我发现这样更容易输入，而且变量的用途一目了然，前提是你使用了足够描述性的名称。将清单 18.11 中的代码立即添加到 `elseif` 行下方及其内部。

## 18. 使用 Web 应用编辑数据

### 清单18.11

```
```php
1. elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
2.     $_POST['movie_rating'], $_POST['movie_director'],
3.     $_POST['movie_running_time_in_minutes'], $_POST['id_to_update']))
4. {
5.
6.     $movie_title = $_POST['movie_title'];
7.     $movie_rating = $_POST['movie_rating'];
8.     $movie_director = $_POST['movie_director'];
9.     $movie_runtime = $_POST['movie_running_time_in_minutes'];
10.    $checked_movie_genres = $_POST['movie_genre_checkbox'];
11.    $id_to_update = $_POST['id_to_update'];
```
```

我们还需要从复选框数组构建一个包含电影流派的逗号分隔字符串。接下来添加以下代码：

```
```php
$movie_genre_text = "";

if (isset($checked_movie_genres))
{
    $movie_genre_text = implode(", ", $checked_movie_genres);
}
```
```

与 addmovie.php 脚本一样，一部电影可以有多个流派。为了存储所有流派，我们通过调用 `implode()`[4] 函数，从复选框数组中创建一个所选流派的逗号分隔列表。我们仅在用户至少选择一个流派时才这样做。如果用户没有选择任何流派，复选框数组就不存在。因此，在调用 `implode()` 之前，我们需要检查它是否已设置。如果用户没有选择流派，我们在 movielisting 表的 genre 字段中插入一个空字符串。

现在我们已经将所有更新后的电影数据以所需形式准备好了，就可以使用 SQL UPDATE 查询更新 movieListing 表。

SQL UPDATE 查询如下所示：

```
```sql
UPDATE <table_name> SET <field_name> = <value_[, ...]> WHERE <condition>
```
```

因此，我们的查询字符串和对 `mysqli_query()` 的调用应类似于清单 18.12。

[4] implode()：https://php.net/implode

### 清单18.12

```
$query = "UPDATE movieListing SET title = '$movie_title', rating = '$movie_rating', "
. "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
. "genre = '$movie_genre_text' "
. "WHERE id = $id_to_update";

mysqli_query($dbc, $query)
or trigger_error(
'Error querying database movielisting: Failed to update movie listing',
E_USER_ERROR
);
```

最后，我们可以使用该电影的 ID 作为查询参数导航回 moviedetails.php，以显示更新后的电影详情，代码如下：

```
$nav_link = 'moviedetails.php?id=' . $id_to_update;

header("Location: $nav_link");
exit;
```

这个 `elseif` 块的完整代码如清单 18.13 所示。

### 清单18.13

```
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
$_POST['movie_rating'], $_POST['movie_director'],
$_POST['movie_running_time_in_minutes'], $_POST['id_to_update']))
{

$movie_title = $_POST['movie_title'];
$movie_rating = $_POST['movie_rating'];
$movie_director = $_POST['movie_director'];
$movie_runtime = $_POST['movie_running_time_in_minutes'];
$checked_movie_genres = $_POST['movie_genre_checkbox'];
$id_to_update = $_POST['id_to_update'];

$movie_genre_text = "";

if (isset($checked_movie_genres))
{
$movie_genre_text = implode(", ", $checked_movie_genres);
}

$query = "UPDATE movieListing SET title = '$movie_title', rating = '$movie_rating', "
. "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
. "genre = '$movie_genre_text' "
. "WHERE id = $id_to_update";
```

