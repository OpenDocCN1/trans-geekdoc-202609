
## 在主页上显示电影缩略图

### 代码清单 19.18

```
1. <table class="table table-striped table-hover">
2. <thead>
3. <tr>
4. <th scope="col"><h4>Movie Titles</h4></th>
5. <th scope="col"></th>
6. <th scope="col"></th>
7. </tr>
8. </thead>
9. <tbody>
```

接下来，我们需要修改每个 HTML 表格行的显示，使其输出三列（而不是两列），其中第一列为缩略图。此外，我们需要确保如果用户没有为电影上传图像，则显示默认图像（generic_movie.jpg）。所有这些操作都在 while 循环中完成，如代码清单 19.19 所示。

### 代码清单 19.19

```
1. while ($row = mysqli_fetch_assoc($result))
2. {
3. $movie_image_file = $row['image_file'];
4. 
5. if (empty($movie_image_file))
6. {
7. $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
8. }
9. 
10. echo "<tr><td><img src=\"" . $movie_image_file . "\" class=\"img-thumbnail\" .
11. "style='max-height: 75px;' alt='Movie image'></td>" .
12. "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='" .
13. $row['id'] . "'>" . $row['title'] . "</a></td>" .
14. "<td class='align-middle'><a class='nav-link' href='removemovie.php?id_to_delete='" .
15. $row['id'] ."'><i class='fas fa-trash-alt'></i></a></td></tr>";
16. }
```

请注意，如果 image_file 字段是空字符串，我们将要显示的图像设置为 images/generic_movie.jpg。

## 19. 文件处理与向现有代码添加功能

## index.php 的完整代码清单

### 代码清单 19.20

```php
1. <html>
2. <head>
3. <title>Movies I Like</title>
4. <link rel="stylesheet"
5. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
6. integrity="sha384-GJzzFGwb10TNNxCRb4pwiMA1aHzv/BuGjpLSa9dkKp0Dg1MDn4vYMj7GzK4YbI7O6tS"
7. crossorigin="anonymous">
8. <link rel="stylesheet"
9. href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
10. integrity="sha384-50oBUHEmvpQ+1lW4y58PFTFmhCaXp0mL5d60M1M7uH2+nqUivzIebhn0dJK28anvF"
11. crossorigin="anonymous">
12. </head>
13. <body>
14. <div class="card">
15. <div class="card-body">
16. <h1>Movies I Like</h1>
17. <p class='nav-link'>If you have a movie you would like to include, feel free to <a href="addmovie.php"> add one</a></p>
18. <?php
19. require_once('dbconnection.php');
20. require_once('movielistingfileconstants.php');
21. 
22. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
23. or trigger_error(
24. 'Error connecting to MySQL server for ' . DB_NAME,
25. E_USER_ERROR
26. );
27. 
28. $query = "SELECT id, title, image_file FROM movielisting ORDER BY title";
29. 
30. $result = mysqli_query($dbc, $query)
31. or trigger_error(
32. 'Error querying database movielisting',
33. E_USER_ERROR
34. );
35. 
36. if (mysqli_num_rows($result) > 0):
37. 
38. ?>
39. <table class="table table-striped table-hover">
40. <thead>
41. <tr>
42. <th scope="col"><h4>Movie Titles</h4></th>
<th scope="col"></th>
<th scope="col"></th>
</tr>
</thead>
<tbody>
<?php
while($row = mysqli_fetch_assoc($result))
{
    $movie_image_file = $row['image_file'];
    if (empty($movie_image_file))
    {
        $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    }
    echo "<tr><td><img src=" . $movie_image_file . " class='img-thumbnail'"
        . "style='max-height: 75px;' alt='Movie image'></td>"
        . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='"
        . $row['id'] . "'>" . $row['title'] . "</a></td>"
        . "<td class='align-middle'><a class='nav-link' href='removemovie.php?id_to_delete='"
        . $row['id'] . "'><i class='fas fa-trash-alt'></i></a></td></tr>";
}
?>
</tbody>
</table>
<?php
else:
?>
<h3>No Movies Found :-(</h3>
<?php
endif;
?>
</div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
    integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVqVZpbzoSsrXkpYVhH8abtTE1P1jL6jzo"
    crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
    integrity="sha384-wHAiFfRl0JOfKk..."
    crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
    integrity="sha384-B0UglyR+jr6C..."
    crossorigin="anonymous"></script>
</body>
</html>
```

现在我们需要修改 moviedetails.php，使电影图像显示在“电影详情”页面上，以便更好地标识电影。此过程与我们修改 addmovie.php 的过程非常相似，addmovie.php 会在用户选择“添加电影”后显示电影详情，结果应如图 19.18 所示。

```
if (isset($_GET['id'])):
require_once('dbconnection.php');
require_once('movielistingfileconstants.php');
```

接下来，就在 if (mysqli_num_rows($result) == 1) 条件内，紧接在
$row = mysqli_fetch_assoc($result); 这一行之后，我们需要添加代码，以便在 image_file 字段为空字符串时显示默认图像。参见代码清单 19.21。

### 代码清单 19.21

```
if (mysqli_num_rows($result) == 1):
  $row = mysqli_fetch_assoc($result);
  $movie_image_file = $row['image_file'];

  if (empty($movie_image_file)):
    $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
  endif;

endif;
```

最后，与我们在 addmovie.php 中所做的一样，我们需要将电影图像文件（或默认图像）添加到表格中，以显示电影详情。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_272_0.png)

## 在详情页显示电影图像

由于我们使用的是 Bootstrap 的 Flexbox 网格实现，最好将图像和表格分别封装到不同的列中，并将它们放在同一行内，所有这些都位于 <h1> 元素中的电影标题下方：

### 代码清单 19.22

```
<h1><?= $row['title'] ?></h1>
<div class="row">
  <div class="col-2">
    <img src="<?= $movie_image_file ?>" class="img-thumbnail"
         style="max-height: 200px;" alt="Movie image">
  </div>
  <div class="col">
    <table class="table table-striped">
      ...
    </table>
  </div>
</div>
```

同样，请注意我们将 style 属性设置为最大高度 200 像素。

## moviedetails.php 完整代码清单

### 代码清单 19.23

```php
<html>
<head>
  <link rel="stylesheet"
  href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
  integrity="sha384-GJzZqFGwbIQTTN6wyJ59ffF1BuGJpLSa9Dk..."
  crossorigin="anonymous">
  <title>Movie Details</title>
</head>
<body>
<div class="card">
  <div class="card-body">
    <nav class="nav">
      <a class="nav-link" href="index.php">Movies I Like</a>
    </nav>
<?php
if (isset($_GET['id'])):

  require_once('dbconnection.php');
  require_once('movielistingfileconstants.php');

  $id = $_GET['id'];
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
    );

$query = "SELECT * FROM movieListing WHERE id = $id";

$result = mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing',
        E_USER_ERROR
    );

if (mysqli_num_rows($result) == 1):
    $row = mysqli_fetch_assoc($result);

    $movie_image_file = $row['image_file'];

    if (empty($movie_image_file)):
        $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    endif;
?>
<h1><?= $row['title'] ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file ?>" class="img-thumbnail"
            style="max-height: 200px;" alt="Movie image">
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
```

