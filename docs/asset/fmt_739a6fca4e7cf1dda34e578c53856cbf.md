
打开 `unauthorizedaccess.php` 脚本，并在 `<body>` 元素之后立即引入 `navmenu.php` 脚本：

```
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
<div class="card-body">
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_392_0.png)

### 向 editmovie.php 添加导航栏

让我们向 `editmovie.php` 脚本添加导航栏。我们想要菜单看起来如图 24.13 所示。

> > 你需要以 `access_privileges` 设置为 `admin` 的用户身份登录才能测试此功能。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_392_1.png)

打开 `pagetitles.php`，并在 `MR_ADD_MOVIE_PAGE` 定义之后立即添加以下 `MR_EDIT_MOVIE_PAGE` 定义：

```
<?php
// Page Titles
// ...
define('MR_ADD_MOVIE_PAGE', 'Movie Reservations - Add Movie');
define('MR_EDIT_MOVIE_PAGE', 'Movie Reservations - Edit Movie');
```

### 向 editmovie.php 添加导航栏

打开 `editmovie.php` 脚本，并在包含 `authorizeaccess.php` 脚本之后，立即引入 `pagetitles.php` 脚本并将 `$page_title` 设置为 `MR_EDIT_MOVIE_PAGE`：

```
<?php
  require_once('authorizeaccess.php');
  require_once('pagetitles.php');
  $page_title = MR_EDIT_MOVIE_PAGE;
?>
<!DOCTYPE html>
<html>
```

这样做可以正确设置我们的 `$page_title` 变量，供 `navmenu.php` 使用，而 `navmenu.php` 是我们在包含 `pagetitles.php` 后所引入的。接下来，在 `<head>` 元素中，修改 `<title>` 元素，移除“编辑电影”并将其替换为 `$page_title`，如清单 24.10 所示。

### 清单 24.10.

```
1.  Unchanged Lines
2.  <html>
3.    <head>
4.    <link ...>
5. - Removed Line
6. -   <title>Edit a Movie</title>
7. + Added Line
8. +   <title><?= $page_title ?></title>
9. Unchanged Lines
10. </head>
11. <body>
12. ...
```

接下来，在 `<body>` 元素正下方，引入 `navmenu.php` 脚本：

```
<body>
<?php
  require_once('navmenu.php');
?>
  <div class="card">
  <div class="card-body">
```

由于我们引入了导航栏，让我们移除 `<h1>编辑电影</h1>` 正下方指向主页的链接。参见清单 24.11。

## 24. 添加导航菜单

### 清单 24.11.

```
1. Unchanged Lines
2.     <div class="card">
3.         <div class="card-body">
4.             <h1>Edit a Movie</h1>
5. - Removed Lines
6. -     <nav class="nav">
7. -         <a class="nav-link" href="index.php">Movies I Like</a>
8. -     </nav>
9. Unchanged Lines
10.     <hr/>
```

### 仅向管理员显示编辑链接

让我们回到 `moviedetails.php` 脚本中，添加一个条件，仅允许具有管理员权限的用户看到指向 `editmovie.php` 脚本的链接。从第二个闭合 `</div>` 标签之后的表格下方，添加清单 24.12 中第 4-7 行和第 13 行的代码。

### 清单 24.12.

```
1.         </table>
2.     </div>
3. </div>
4.     <?php
5.         if (isset($_SESSION['user_access_privileges'])
6.             && $_SESSION['user_access_privileges'] == 'admin'):
7. ?>
8. <hr/>
9. <p class='nav-link'>If you would like to change any of the details
10.     of this movie feel free to
11.     <a href='editmovie.php?id_to_edit=<?=$row['id'] ?>'> edit it</a></p>
12. <?php
13.     endif;
14.     else:
15. ?>
16. <h3>No Movie Details :-(</h3>
17. <?php
18.     endif;
19.     else:
20. ?>
21. <h3>No Movie Details :-(</h3>
22. <?php
23.     endif;
24. ?>
25.     </div>
26. </div>
27.     <script ...></script>
```

### 向 removemovie.php 添加导航栏

最后，我们将向 `removemovie.php` 脚本添加导航栏。我们想要菜单看起来如图 24.14 所示。

> 你需要以 `access_privileges` 设置为 `admin` 的用户身份登录才能测试此功能。

打开 `pagetitles.php`，并在 `MR_EDIT_MOVIE_PAGE` 定义之后立即添加以下 `MR_REMOVE_MOVIE_PAGE` 定义：

```
<?php
// Page Titles
// ...
define('MR_EDIT_MOVIE_PAGE', 'Movie Reservations - Edit Movie');
define('MR_REMOVE_MOVIE_PAGE', 'Movie Reservations - Remove Movie');
```

打开 `removemovie.php` 脚本，并在包含 `authorizeaccess.php` 脚本之后，立即引入 `pagetitles.php` 脚本并将 `$page_title` 设置为 `MR_REMOVE_MOVIE_PAGE`：

```
<?php
require_once('authorizeaccess.php');
require_once('pagetitles.php');
$page_title = MR_REMOVE_MOVIE_PAGE;
?>
<!DOCTYPE html>
<html>
```

这样可以正确设置我们的 `$page_title` 变量，供 `navmenu.php` 使用，而 `navmenu.php` 是我们在包含 `pagetitles.php` 后所引入的。接下来，在 `<head>` 元素中，修改 `<title>` 元素，移除文本“移除电影”并将其替换为 `$page_title`（参见清单 24.13）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_395_0.png)

## 24. 添加导航菜单

### 清单 24.13.

```
1.  Unchanged Lines
2.  ...
3.  <html>
4.      <head>
5.      <link ...>
6.  - Removed Line
7.  -   <title>Remove a Movie</title>
8.  + Added Line
9.  +   <title><?= $page_title ?></title>
10. Unchanged Lines
11.     </head>
12.     <body>
13.     ...
```

接下来，在 `<body>` 元素正下方，引入 `navmenu.php` 脚本：

```
<body>
<?php
    require_once('navmenu.php');
?>
    <div class="card">
    <div class="card-body">
```

### 完整代码清单

清单 24.14 是 `pagetitles.php` 页面的完整代码。

### 清单 24.14.

```
1. <?php
2. // Page Titles
3. define('MR_HOME_PAGE', 'Movie Reservations');
4. define('MR_DETAILS_PAGE', 'Movie Reservations - Details');
5. define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
6. define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
7. define('MR_UNAUTHORIZED_ACCESS_PAGE', 'Movie Reservations - Unauthorized Access');
8. define('MR_ADD_MOVIE_PAGE', 'Movie Reservations - Add Movie');
9. define('MR_EDIT_MOVIE_PAGE', 'Movie Reservations - Edit Movie');
10. define('MR_REMOVE_MOVIE_PAGE', 'Movie Reservations - Remove Movie');
```

清单 24.15 是 `navmenu.php` 页面的完整代码。

### 清单 24.15.

```php
<?php
$page_title = isset($page_title) ? $page_title : "";

if (session_status() == PHP_SESSION_NONE) {
    session_start();
}
?>
<nav class="navbar sticky-top navbar-expand-md navbar-dark"
    style="background-color: #569f32;">
   <a class="navbar-brand" href="<?= dirname($_SERVER['PHP_SELF']) ?>?">
       <img src="resources/movie_rental_icon.png" width="30" height="30"
            class="d-inline-block align-top" alt="">
       <?= MR_HOME_PAGE ?>
   </a>
   <button class="navbar-toggler" type="button" data-toggle="collapse"
           data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup"
           aria-expanded="false" aria-label="Toggle navigation">
       <span class="navbar-toggler-icon"></span>
   </button>
   <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
       <div class="navbar-nav">
           <a class="nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>"
              href="<?= dirname($_SERVER['PHP_SELF']) ?>">Home </a>
           <?php if (isset($_SESSION['user_access_privileges'])
               && $_SESSION['user_access_privileges'] == 'admin'): ?>
               <a class="nav-item nav-link<?= $page_title == MR_ADD_MOVIE_PAGE ? ' active' : '' ?>"
                  href="addmovie.php">Add a Movie</a>
           <?php endif; ?>
           <?php if (!isset($_SESSION['user_name'])): ?>
               <a class="nav-item nav-link<?= $page_title == MR_LOGIN_PAGE ? ' active' : '' ?>"
                  href="login.php">Login</a>
               <a class="nav-item nav-link<?= $page_title == MR_SIGNUP_PAGE ? ' active' : '' ?>"
                  href="signup.php">Sign Up</a>
           <?php else: ?>
               <a class="nav-item nav-link"
                  href="logout.php">Logout (<?= $_SESSION['user_name'] ?>)</a>
           <?php endif; ?>
       </div>
   </div>
</nav>
```

## 练习

- 1. 创建 `navmenu.php` 脚本来保存 Navbar 逻辑并将其添加到所需的页面中。

  - 1. 在导航栏中，在登录链接旁边显示已登录用户的姓名。

- 2. 添加仅管理员用户可用的“Add Movie”链接。

  - 1. 确认管理员用户可以看到该链接。

  - 2. 确认普通网站用户看不到该链接。

## 章节

## 25

## 添加预订功能

> “对于所有对我的名言感到兴奋的人们。这里再来一句 - 是的，我是个糟糕的程序员，但我可能仍然比你好 :)”

>

> -Rasmus Lerdorf

## 25. 添加预订功能

最后，我们准备好为我们的 *Movie Reservations* 应用添加电影预订功能。本章将重点介绍为 *Movie Reservations* 应用添加预订功能，以便用户可以预订和归还电影。再次，这里是我们需要做的修改列表，以便最终将 *Movie Listing* 应用转变为 *Movie Reservations* 应用：

- 1. **添加预订功能**

  - 1. 创建一个数据库表来保存电影预订信息

  - 2. 向 `movieListing` 数据库表添加字段，以跟踪每部电影的副本数量和已预订电影

  - 3. 修改添加、编辑、删除和电影详情脚本以包含电影的副本数量

  - 4. 修改电影列表页面，为已登录用户显示预订电影的链接

  - 5. 修改电影列表页面，为具有管理员权限的登录用户显示删除电影的链接

  - 6. 添加预订脚本供用户借出电影

  - 7. 添加购物车脚本，允许用户在购物车中预订电影并将其从购物车中移除

  - 8. 添加购物车图标，允许用户查看其购物车

  - 9. 添加已预订电影脚本，允许用户归还电影

  - 10. 添加预订图标，允许用户查看其预订

### 添加副本数量和已预订数量

为了将我们的电影列表应用转变为电影预订应用，我们需要知道我们拥有的电影标题的副本数量以及其中有多少副本已被预订。我们将修改数据库并添加电影借阅功能。

### 添加副本数量和已预订数据库字段

让我们在 *Movie* 数据库中的 `movieListing` 表中添加两个字段。一个用于副本数量，另一个用于已预订数量。我们将使用 Adminer 来修改我们的表，如图 25.1 所示。

### 添加副本数量和已预订数量

选择 `image_file` 字段后的 +，在 `movieListing` 表末尾添加两个新字段。

对于 `number_of_copies` 字段：

- 在 `image_file` 下方的 **Column name** 中，输入 `number_of_copies`

- 选择“Type”为 int

- 为“Length”输入 **11**

- 勾选复选框并为“Default value”输入 **1**

对于 `number_reserved` 字段：

- 在 `number_of_copies` 下方的 **Column name** 中，输入 `number_reserved`

- 选择“Type”为 int

- 为“Length”输入 **11**

- 勾选复选框并为“Default value”输入 **0**
