
```php
<?php
/**
 * Purpose: Finds the number of movies reserved by current user not in cart
 *
 * Description: Based on the `$_SESSION['user_id']` and the `$_SESSION['cart']`
 *              movie ids, query for the movies reserved by the user and compare
 *              to the movies in the cart. The number of movies reserved not in
 *              the cart are returned. NOTE, if `$_SESSION['user_id']` is not set,
 *              0 is returned and if `$_SESSION['cart']` is not set, the number
 *              of reservations for the user is returned (assuming
 *              `$_SESSION['user_id']` is set).
 *
 * @return int The number of movies reserved by the user not in the cart,
 *             or 0 if `$_SESSION['user_id']` is not set.
 */
function numberOfMoviesReservedNotInCart()
{
    $number_of_movies_reserved = 0;
    $number_of_movies_reserved_in_cart = 0;

    if (session_status() == PHP_SESSION_NONE)
    {
        session_start();
    }

    if (!isset($_SESSION['user_id']))
    {
        return 0;
    }

    require_once('dbconnection.php');

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for ' . DB_NAME,
            E_USER_ERROR
        );

    $user_id = $_SESSION['user_id'];

    $query = "SELECT movieListing_id FROM reservation WHERE user_id = ?";
    $result = parameterizedQuery($dbc, $query, 'i', $user_id)
        or trigger_error('Error querying database movieListing',
            E_USER_ERROR);

    $number_of_movies_reserved = mysqli_num_rows($result);

    if (!isset($_SESSION['cart']))
    {
        return $number_of_movies_reserved;
    }

    $movies_in_cart = $_SESSION['cart'];

    while ($row = mysqli_fetch_assoc($result))
    {
        // Accumulate count of reserved movies in cart
        if (array_search($row['movieListing_id'], $movies_in_cart) !== false)
        {
            $number_of_movies_reserved_in_cart++;
        }
    }

    return $number_of_movies_reserved - $number_of_movies_reserved_in_cart;
}
```

该函数查询 Movie 数据库的 `reservation` 表，获取所有包含给定 `user_id` 的行。在第 46 行，我们得到匹配行的总数。第 55–62 行累积了用户购物车中与用户在 `reservation` 表中已有的电影不匹配的电影数量。返回该数量。

现在打开 `pagetitles.php`，在 `MR_SHOPPING_CART_MOVIE_PAGE` 定义之后添加以下 `MR_RESERVED_MOVIES_PAGE` 定义：

```text
Unchanged Lines
    <?php
    // Page Titles
    define('MR_HOME_PAGE', 'Movie Reservations');
    ...
    define('MR_SHOPPING_CART_MOVIE_PAGE', 'Movie Reservations - Shopping Cart');
+ Added Line
+     define('MR_RESERVED_MOVIES_PAGE', 'Movie Reservations - Reserved Movies');
```

接下来，打开 `navmenu.php` 脚本。在 `<a class="nav-item nav-link"> $page_title == MR_SHOPPING_CART_MOVIE_PAGE ...</a>` 元素之前，并在 `<div class="nav navbar-nav ml-auto">` 之后，添加清单 25.43 中的代码。

### 列表 25.43.

```
1. Unchanged Lines
2.     <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
3.         <div class="nav navbar-nav ml-auto">
4. + Added Line
5. +     <?php if (numberOfMoviesReservedNotInCart() > 0): ?>
6. +         <a class="nav-item nav-link<?= $page_title == MR_RESERVED_MOVIES_PAGE ? ' active' : '' ?>"
7. +             href='reservedmovies.php'><i class="fas fa-video"></i></a>
8. +     <?php endif; ?>
9. Unchanged Lines
10.     <a class="nav-item nav-link<?= $page_title == MR_SHOPPING_CART_MOVIE_PAGE ? ' active' : '' ?>"
11.         href='shoppingcart.php'><i class='fas fa-shopping-cart'></i> <span class="badge badge-light">
12.         <?= isset($_SESSION['cart']) ? count($_SESSION['cart']) : '' ?></span></a>
13.     </div>
14. </div>
```

第一个条件（`<?php if (numberOfMoviesReservedNotInCart() > 0): ?>`），只有在用户做出的预订当前不在其购物车中时，才允许此条件内的代码执行。

（`<a class="nav-item nav-link<?= $page_title == MR_RESERVED_MOVIES_PAGE ...</a>`）是标准的三元操作，根据是否正在显示 `reservedmovies.php` 脚本来显示投影仪图标链接是否处于活动状态。

> 投影仪图标是可免费使用的 Font Awesome “`fa-video`” 图标。

## 显示和退回预订的电影

当用户点击投影仪图标时，其浏览器会将其带到 `reservedmovies.php` 页面（我们在此创建）。我们希望此页面显示电影列表、电影详情的链接、每部电影的退回按钮以及退回所有电影的表单按钮。见图 25.27。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_455_0.png)

这样，电影可以逐个退回，使用单个电影的退回按钮，如图 25.28 所示，也可以按表单上的 **退回电影** 按钮一次性全部退回，如图 25.29 所示

## 25. 添加预订功能

## 创建预订电影页面的样板和逻辑

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_456_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_456_1.png)

预订电影页面是一个标准的 Bootstrap 页面。创建一个名为 `reservedmovies.php` 的新脚本，并使用列表 25.44 中显示的代码。

### 列表 25.44.

```
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_RESERVED_MOVIES_PAGE;
?>
<html>
<head>
<title><?= $page_title ?></title>
<link rel="stylesheet"
    href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
    integrity="sha384-GJzZqFGwbIQTTN6wy59FF1BuGJpLSa9dkKm0p0DgiMDn4iYMj70zQWKYbi7O6EWS"
    crossorigin="anonymous">
</head>
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
<div class="card-body">
<h1>Reserved Movies</h1>
<?php
require_once('dbconnection.php');
require_once('movielistingfileconstants.php');

// Only display this page if the user is logged in
if (!isset($_SESSION['user_id'])) :

    header("Location: " . dirname($_SERVER['PHP_SELF']));
    exit;

elseif (isset($_POST['id_to_check_in'])):

    // ...
```

## 显示和退回预订的电影

```
35.     elseif (isset($_POST['check_in_movies'])):
36.
37.     // ...
38.
39.     else:
40.
41.     // ...
42.
43.     endif;
44.     ?>
45.     </div>
46.     </div>
47.     <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
48.         integrity="sha384-q8i/X+965DzO0rT7akK1JStQIAqAqVqVzpbo5snXKpYwYfRvHv+8abtTE1Pi6jizo"
49.         crossorigin="anonymous"></script>
50.     <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
51.         integrity="sha384-WAiFfRlMFY6iSSRxvfOClfBU9yXhdJ/yoi7FRNXMRBuSWkHZyUihA6ZObIgu"
52.         crossorigin="anonymous"></script>
53.     <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
54.         integrity="sha384-B0UglyrJ+..."
55.         crossorigin="anonymous"></script>
56.     </body>
57. </html>
```

同样，这是一个样板脚本，应该看起来很熟悉。第 3、4 和 8 行设置并显示页面标题。第 16 行包含并显示导航栏。第 20 行在 `<h1>` 元素中显示“Reserved Movies”。第 22-23 行包含 `dbconnection.php`、`movielistingfileconstants.php`、`queryutils.php`。

第 26 行（`if (!isset($_SESSION['user_id'])):`）是检查用户是否未登录的条件。如果用户未登录，第 28 行会将用户重定向回主页。

第 31 行（`elseif (isset($_POST['id_to_check_in'])):`）是用户在预订电影列表中选择要退回的电影的条件。此条件是我们从预订表中删除所选电影并更新该电影预订副本数量的位置。

第 35 行（`elseif (isset($_POST['check_in_movies'])):`）是检查用户是否选择了 Return Movies 以退回其预订的所有电影的条件。此条件是我们更新所有正在退回电影的副本数量并从预订表中删除用户的所有电影预订，然后将他们重定向回主页的位置。

## 25. 添加预订功能

第 39 行（`else:`）是一个“兜底”条件。此条件显示用户预订的电影列表以及退回每部电影的按钮。我们还显示一个表单，其中包含退回所有预订电影的按钮。

其余代码是标准的 Bootstrap 样板脚本包含。

## 列出预订的电影

让我们将列表 25.45 中的代码添加到兜底条件（`else:`）中，用于列出用户预订的所有电影以及退回电影的表单。我将在下面解释代码：

### 列表 25.45.

```
```php

else:

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)

        or trigger_error(

            'Error connecting to MySQL server for' . DB_NAME,

            E_USER_ERROR

        );

    $user_id = $_SESSION['user_id'];

    $query = "SELECT movielisting.id, movielisting.title, movielisting.image_file

        FROM movielisting

        INNER JOIN reservation ON movielisting.id = reservation.movielisting_id

        WHERE reservation.user_id = ?";

    $result = parameterizedQuery($dbc, $query, 'i', $user_id)

        or trigger_error(

            'Error querying database tables movieListing and reservation',

            E_USER_ERROR);

    if (mysqli_num_rows($result) > 0):

?>

<table class="table table-striped table-hover">

    <thead>

        <tr>

            <th scope="col"><h4>Movies You Have Reserved</h4></th>

            <th scope="col"></th>

            <th scope="col"></th>

        </tr>

    </thead>

    <tbody>

```

## 显示和退回预订的电影
