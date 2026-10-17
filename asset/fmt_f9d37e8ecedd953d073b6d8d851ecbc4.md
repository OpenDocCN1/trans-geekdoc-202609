
```
Unchanged Lines
<?php
// Page Titles
define('MR_HOME_PAGE', 'Movie Reservations');
...
define('MR_RESERVE_MOVIE_PAGE', 'Movie Reservations - Reserve Movie');
+ Added Line
+     define('MR_SHOPPING_CART_MOVIE_PAGE', 'Movie Reservations - Shopping Cart');
```

购物车页面是一个标准的 Bootstrap 页面。创建一个名为 `shoppingcart.php` 的新脚本并添加清单 25.37 中的代码。

### 清单 25.37

```
1. <!DOCTYPE html>
2. <?php
3. require_once('pagetitles.php');
4. $page_title = MR_SHOPPING_CART_MOVIE_PAGE;
5. ?>
6. <html>
7. <head>
8. <title><?= $page_title ?></title>
9. <link rel="stylesheet"
10. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
11. integrity="sha384-GJzZqFGwbIQTTN7wy59ff1BuCjLpsaSa9DkKmp0DgiMDm4iVMj70gZKybYt70dI4S"
12. crossorigin="anonymous">
13. </head>
14. <body>
15. <?php
16. require_once('navmenu.php');
17. ?>
18. <div class="card">
19. <div class="card-body">
20. <h1>Shopping Cart</h1>
21. <?php
22. require_once('dbconnection.php');
23. require_once('movielistingfileconstants.php');
24. 
25. // Only display this page if the user is logged in
26. if (!isset($_SESSION['user_id'])) :
27. 
28. header("Location: " . dirname($_SERVER['PHP_SELF']));
29. exit;
30.
31.     elseif (isset($_POST['id_to_delete'])):
32.
33.     // ...
34.
35.     elseif (isset($_POST['reserve_movies'])):
36.
37.
38.     // ...
39.
40.     elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
41.
42.
43.     // ...
44.
45.     else:
46.     ?>
47.     <hr/>
48.     <h3>No Movies in your cart :-(</h3>
49.     <?php
50.     endif;
51.     ?>
52.     </div>
53. </div>
54. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
55.     integrity="sha384-Q8i/LTVZQMX7LZ8W3wqks2XoK/VYV+Nn6..."
56.     crossorigin="anonymous"></script>
57. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
58.     integrity="sha384-wHAiF1R..."
59.     crossorigin="anonymous"></script>
60. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
61.     integrity="sha384-B0Uglyr+..."
62.     crossorigin="anonymous"></script>
63. </body>
64. </html>
```

同样，这是一个样板脚本，您应该熟悉。第 3、4 和 8 行设置并显示页面标题。第 16 行包含并显示导航栏。第 20 行在 `<h1>` 元素集中显示“购物车”。第 22-23 行包含 `dbconnection.php`、`movielistingfileconstants.php`。

第 26 行 (`if (!isset($_SESSION['user_id'])):`) 是检查用户是否未登录的条件。如果用户未登录，第 26 行会将他们重定向到主页。

第 31 行 (`elseif (isset($_POST['id_to_delete'])):`) 是用户在购物车中选择要删除的电影的条件。在此条件下，我们将所选电影从购物车和预订表中删除。

## 25. 添加预订功能

第 35 行 (`elseif (isset($_POST['reserve_movies'])):`) 是检查用户是否预订了购物车中电影的条件。此条件用于删除购物车并将用户重定向回主页。

第 39 行 (`elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):`) 是检查用户购物车中是否有电影的条件。此条件用于显示用户购物车中的电影列表，并可删除每部电影。还将显示一个带有预订购物车中电影按钮的表单。

第 43 行 (`else:`) 是一个“兜底”条件，表示用户购物车中没有电影，因此第 43 行将显示购物车中没有电影。

其余代码是标准的 Bootstrap 样板脚本包含。

### 为预订电影添加表单

让我们将以下购物车代码和用于预订电影的表单添加到条件 (`elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):`) 中。我将在下面的清单 25.38 中解释代码。

### 清单 25.38

```php
1. elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
2.
3.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
4.         or trigger_error(
5.             'Error connecting to MySQL server for ' . DB_NAME,
6.             E_USER_ERROR
7.         );
8.
9.     $user_id = $_SESSION['user_id'];
10.
11.     $query = "SELECT movielisting.id, movielisting.title, movielisting.image_file
12.               FROM movielisting
13.               INNER JOIN reservation ON movielisting.id = reservation.movielisting_id
14.               WHERE reservation.user_id = ?";
15.
16.     $result = parameterizedQuery($dbc, $query, 'i', $user_id);
17.
18.     if (mysqli_errno($dbc))
19.     {
20.         trigger_error('Error querying database movielisting', E_USER_ERROR);
21.     }
22.
23.     if (mysqli_num_rows($result) > 0):
24. ?>
```

### 添加购物车脚本

```html
<table class="table table-striped table-hover">
    <thead>
        <tr>
            <th scope="col"><h4>Movies to Reserve</h4></th>
            <th scope="col"></th>
            <th scope="col"></th>
        </tr>
    </thead>
    <tbody>
    <?php

    while ($row = mysqli_fetch_assoc($result))
    {
        // Only display what's in the shopping cart
        if (array_search($row['id'], $_SESSION['cart']) !== false)
        {
            $movie_image_file = $row['image_file'];

            if (empty($movie_image_file))
            {
                $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
            }

            $movie_title_row = "<tr><td><img src=\"" . $movie_image_file . "\" class='img-thumbnail'"
                . "style='max-height: 75px;' alt='Movie image'></td>"
                . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='"
                . $row['id'] . "'>" . $row['title'] . "</a></td>"
                . "<td class='align-middle'><form method='POST' action='"
                . $_SERVER['PHP_SELF'] . "'><button class='btn btn-danger' type='submit' "
                . "name='id_to_delete' value='" . $row['id'] . "'>"
                . "<i class='far fa-trash-alt'></i></button></form></td>";

            $movie_title_row .= "</tr>";

            echo $movie_title_row;
        }
    }
    ?>
    </tbody>
</table>
<form method="POST" action="<?php echo $_SERVER['PHP_SELF']; ?>">
    <button class="btn btn-success" type="submit" name="reserve_movies">Reserve Movies</button>
</form>
<?php
else:
?>
<h3>No Movies in your cart :-(</h3>
<?php
endif;
else:
```

## 25. 添加预订功能

在第 3 行连接到 `movielisting` 数据库后，我们在第 11–14 行创建了 `movielisting` 和 `reservation` 表的 `INNER JOIN` 查询，该查询返回用户已预订的每部电影的 `id`、`title` 和 `image_file`。

假设查询至少返回一部电影（第 23 行），第 25–65 行显示包含用户购物车中所有电影的表格。由于查询返回 `reservation` 表中的所有电影，因此我们需要只保留购物车中的电影。这一区别很重要，因为用户可能已经预订了电影，我们会在其他地方显示这些电影。

让我们更仔细地查看第 36–62 行。第 36 行遍历用户的每个预订。然而，第 39 行 (`if (array_search($row['id'], $_SESSION['cart']) !== false)`) 仅允许显示同时包含在用户购物车中的预订行，这些行由第 41–60 行处理。

在第 48–51 行，我们显示电影的图像和标题，该标题链接回 `moviedetails.php` 脚本，并将电影 ID 作为查询参数：

```php
$movie_title_row = "<tr><td><img src=" . $movie_image_file . " class='img-thumbnail'"
    . "style='max-height: 75px;' alt='Movie image'></td>"
    . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='"
    . $row['id'] . "'>" . $row['title'] . "</a></td>";
```

注意第 53 行，添加到 `$movie_title_row` 的表单中的删除按钮链接回此页面，并将 `id_to_delete` 的值设置为电影 ID：

```php
$movie_title_row .= "<td class='align-middle'><form method='POST' action="
    . $_SERVER['PHP_SELF'] . "><button class='btn btn-danger' type='submit' "
    . "name='id_to_delete' value=" . $row['id'] . ">"
    . "<i class='far fa-trash-alt'></i></button></form></td>";
```

此外，请注意，我使用的是 Font Awesome 的垃圾桶图标，背景为红色，如图 25.25 所示。

第 66–68 行显示一个表单，其中包含一个“Reserve Movies”按钮，其 `name` 属性设置为 `reserve_movies`。

第 70 行是查询未返回任何预订的条件，因此第 72 行显示购物车中没有电影。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_446_0.png)

### 从购物车中移除电影

如果用户改变主意不想保留某部电影，我们需要将其从购物车和预订表中移除。将清单 25.39 中的代码添加到条件 (`elseif (isset($_POST['id_to_delete'])):`) 中。我随后会解释代码。

### 清单 25.39
