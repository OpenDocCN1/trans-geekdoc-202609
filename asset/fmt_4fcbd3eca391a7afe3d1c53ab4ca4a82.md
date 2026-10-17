
```php
1. elseif (isset($_POST['id_to_delete'])):
2.
3. $movie_to_delete = $_POST['id_to_delete'];
4.
5. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
6.     or trigger_error(
7.         'Error connecting to MySQL server for ' . DB_NAME,
8.         E_USER_ERROR
9.     );
10.
11. $user_id = $_SESSION['user_id'];
12.
13. $query = "DELETE FROM reservation
14.         WHERE user_id = ? AND movielisting_id = ?";
15. $result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_to_delete);
16.
17. if (mysqli_errno($dbc))
18. {
19.     trigger_error('Error querying database movielisting', E_USER_ERROR);
20. }
21.
22. $query = "UPDATE movielisting SET number_reserved = number_reserved - 1
23.         WHERE id = ?";
24. $result = parameterizedQuery($dbc, $query, 'i', $movie_to_delete);
25.
26. if (mysqli_errno($dbc))
27. {
28.     trigger_error('Error querying database movielisting', E_USER_ERROR);
29. }
30.
31. if (($key = array_search($movie_to_delete, $_SESSION['cart'])) !== false)
32. {
33.     unset($_SESSION['cart'][$key]);
34. }
35.
36. header("Location: " . $_SERVER['PHP_SELF']);
37. exit;
38.
39. elseif (isset($_POST['reserve_movies'])):
```

## 25. 添加预订功能

在第 `5` 行连接到 `movielisting` 数据库后，我们在第 `13–14` 行创建删除该电影预订的查询，并在第 `15` 行执行该查询。

在第 `22` 行，我们创建了一个查询来减少该标题的预订电影数量，并在第 `24` 行执行该查询。

在第 `31` 行，我们搜索要删除的电影 ID 关联的键，并在第 `33` 行将其从用户购物车中移除。

最后，第 `36` 行将浏览器重定向到此购物车页面。页面加载时，更新后的购物车内容将在表格中刷新。

### 为购物车中的电影添加预订代码

当用户预订购物车中的电影时，执行将恢复到 (`elseif (isset($_POST['reserve_movies'])):`) 条件。由于我们已经将他们的电影添加到预订表中，这里我们删除购物车会话变量，effectively 清空它，并将用户重定向回主页。

将清单 `25.40` 中的代码添加到此条件。

### 清单 `25.40`

```php
1. elseif (isset($_POST['reserve_movies'])):
2.
3.   // Delete the shopping cart (it's already in the reservation table),
4.   // and route back to the Home page
5.   unset($_SESSION['cart']);
6.
7.   header("Location: " . dirname($_SERVER['PHP_SELF']));
8.   exit;
9.
10. elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
```

## 完整代码清单

清单 `25.41` 是 `shoppingcart.php` 页面的完整代码。

### 清单 `25.41.`

```php
<!DOCTYPE html>
<?php
  require_once('pagetitles.php');
  $page_title = MR_SHOPPING_CART_MOVIE_PAGE;
?>
<html>
  <head>
    <title><?php echo $page_title ?></title>
    <link rel="stylesheet"
          href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
          integrity="sha384-GJzZqFQb1Qb1QTN6wyS9FFf1BuGjlPaSe9KKyP0DgiMD4lMj70zQZKYbI7O6tWs"
          crossorigin="anonymous">
</head>
<body>
<?php
  require_once('navmenu.php');
?>
  <div class="card">
    <div class="card-body">
      <h1>Shopping Cart</h1>
<?php
  require_once('dbconnection.php');
  require_once('movielistingfileconstants.php');

  // Only display this page if the user is logged in
  if (!isset($_SESSION['user_id'])):

    header("Location: " . dirname($_SERVER['PHP_SELF']));
    exit;
  elseif (isset($_POST['id_to_delete'])):

    $movie_to_delete = $_POST['id_to_delete'];

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
      or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
      );

    $user_id = $_SESSION['user_id'];

    $query = "DELETE FROM reservation WHERE user_id = ? AND movielisting_id = ?";
    $result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_to_delete);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}

$query = "UPDATE movielisting SET number_reserved = number_reserved - 1 WHERE id = ?";
$result = parameterizedQuery($dbc, $query, 'i', $movie_to_delete);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}

if (($key = array_search($movie_to_delete, $_SESSION['cart'])) !== false)
{
    unset($_SESSION['cart'][$key]);
}

header("Location: " . $_SERVER['PHP_SELF']);
exit;

elseif (isset($_POST['reserve_movies'])):
    // Delete the shopping cart (it's already in the reservation table),
    // and route back to the Home page
    unset($_SESSION['cart']);

header("Location: " . dirname($_SERVER['PHP_SELF']));
exit;

elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for ' . DB_NAME,
            E_USER_ERROR
        );

    $user_id = $_SESSION['user_id'];

    $query = "SELECT movielisting.id, movielisting.title, movielisting.image_file
        FROM movielisting
            INNER JOIN reservation ON movielisting.id = reservation.movielisting_id
        WHERE reservation.user_id = ?";
    $result = parameterizedQuery($dbc, $query, 'i', $user_id);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}

if (mysqli_num_rows($result) > 0):
?>
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
                    . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id="
                    . $row['id'] . "'>" . $row['title'] . "</a></td>";

                $movie_title_row .= "<td class='align-middle'><form method='POST' action='"
                    . $_SERVER['PHP_SELF'] . "'> <button class='btn btn-danger' type='submit' "
                    . "name='id_to_delete' value='" . $row['id'] . "'>"
                    . "<i class='far fa-trash-alt'></i></button></form></td>";

                $movie_title_row .= "</tr>";

                echo $movie_title_row;
            }
        }
    ?>
    </tbody>
</table>
<form method="POST" action="<?=$_SERVER['PHP_SELF']?>">
    <button class="btn btn-success" type="submit" name="reserve_movies">Reserve Movies</button>
</form>
<?php
else:
?>
```

### 清单 `25.42.`
