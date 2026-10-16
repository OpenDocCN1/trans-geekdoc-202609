

## 25. 添加预订功能

```
if (mysqli_errno($dbc))
{
    trigger_error('Error querying database table movielisting', E_USER_ERROR);
}
}

// Delete all reservations for this user
$query = "DELETE FROM reservation WHERE user_id = ?";

parameterizedQuery($dbc, $query, 'i', $user_id);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database table reservation', E_USER_ERROR);
}

header("Location: " . dirname($_SERVER['PHP_SELF']));
exit;

else:

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

$result = parameterizedQuery($dbc, $query, 'i', $user_id)
    or trigger_error(
        'Error querying database tables movielisting and reservation', E_USER_ERROR);

if (mysqli_num_rows($result) > 0):
?>
<table class="table table-striped table-hover">
<thead>
<tr>
<th scope="col"><h4>Movies You Have Reserved</h4></th>
<th scope="col"></th>
<th scope="col"></th>
</tr>
```
</thead>
<tbody>
<?php
while($row = mysqli_fetch_assoc($result))
{
    // Only display what's NOT in the shopping cart
    if (empty($_SESSION['cart'])
        || array_search($row['id'], $_SESSION['cart']) == false)
    {
        $movie_image_file = $row['image_file'];

        if (empty($movie_image_file))
        {
            $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
        }

        $movie_title_row = "<tr><td><img src=\"" . $movie_image_file
            . "\" class='img-thumbnail' style='max-height: 75px;'"
            . " alt='Movie image'></td>"
            . "<td class='align-middle'><a class='nav-link' "
            . "href='moviedetails.php?id='"
            . $row['id'] . "'>" . $row['title'] . "</a></td>";

        $movie_title_row .= "<td class='align-middle'><form method='POST' "
            . "action='" . $_SERVER['PHP_SELF'] . "'>"
            . "<button class='btn btn-success' type='submit' "
            . "name='id_to_check_in' value='" . $row['id'] . "'>"
            . "<i class='fas fa-check-circle'></i></button></form></td>";

        $movie_title_row .= "</tr>";

        echo $movie_title_row;
    }
}
?>
</tbody>
</table>
<form method="POST" action="<?=$_SERVER['PHP_SELF']?>">
    <button class="btn btn-success" type="submit"
        name="check_in_movies">Return Movies</button>
</form>
<?php
else:
?>
<h3>No Movies Reserved :-</h3>
<?php
    endif;

## 25. 添加预订功能

```
183.      endif;
184.      ?>
185.    </div>
186. </div>
187. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
188.         integrity="sha384-Q8i/X+965dz0rT7abk4lJ5tQI..."
189.         crossorigin="anonymous"></script>
190. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
191.         integrity="sha384-wH..."
192.         crossorigin="anonymous"></script>
193. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
194.         integrity="sha384-B0Uglyr..."
195.         crossorigin="anonymous"></script>
196. </body>
197. </html>
```

### 待添加的功能

这段代码绝不是一个完整且精良的应用。虽然可工作的代码至关重要，但总有改进或适配新用途的方法。可以也应该添加若干功能来提升用户体验，并增强应用的健壮性。下面我列举了几项。

### 为电影标题添加分页

随着电影预订库的增长，最好为应用添加分页功能，而不是列出数据库中的所有电影。分页可以改善响应时间，并减少每页显示结果所需的垂直滚动量。

### 添加电影搜索和筛选功能

除了分页之外，添加搜索功能来限制结果可以提升用户体验。该功能可以按标题搜索，也可以按导演搜索。此外，添加按不同评级筛选电影的能力也会有所帮助。

### 向电影记录中添加详细信息

我们现在可以追踪比目前更多的电影信息。可以添加发行日期、制片人、演员等字段，甚至可以链接到电影的相关评论或网站。

### 跟踪预订日期

目前，数据库既不跟踪用户借出电影的时间，也不提供归还截止日期。添加这些功能可以让管理员确保没有人无限期地保留电影副本。

### 为管理员添加预订管理功能

我们为电影预订应用开发的许多功能都以用户为中心。为了简化站点管理，最好具备以下管理功能：

- 1. 一个显示已预订电影的表
  - 点击某部电影会打开一个页面，列出借出该电影的每位用户
  - 点击某位用户会链接到仅列出该用户已预订电影的页面
- 2. 一个列出已预订一部或多部电影的用户的表
  - 点击某位用户会打开一个页面，列出他们已借出的电影
- 3. 管理丢失电影的能力

### 此应用中的缺陷

这些页面中的一些存在大量重复代码，尤其是样板式的 Bootstrap 链接。你应当将这些重复代码移入一个独立的头文件中，供所有需要它的脚本包含。

此应用还存在几个设计问题。

一个问题在于，如果用户将电影放入购物车后退出登录，这些电影会被预订，而用户并未主动预订它们。将电影放入购物车实际上就在预订表中预订了该电影。更好的购物车管理设计是使用一个数据库表来维护当前所有用户购物车中的电影（即多个用户登录并在其购物车中添加电影）。然后，只有在用户决定预订购物车中的电影时才创建预订记录。这一改动增加了复杂性，但通过将购物车条目排除在预订表之外，是更稳健的解决方案。另一个可能的解决方案是：如果用户在预订购物车中的电影之前退出登录，则清除所有预订记录。同时，弹出模态对话框告知用户当前情况，允许他们选择预订电影或继续退出登录，也是个好主意。维护用户购物车的购物车表是更好的想法，因为它能让用户在多次登录之间保留购物车内容。然而，现在我们又需要处理用户将电影保留在购物车中、导致其他用户无法预订的问题。

这些是值得考虑的有趣的设计和可用性问题，它们有许多不同且可接受的方案和取舍。

## 25. 添加预订功能

### 练习

- 1. 添加预订功能，包括数据库表、对添加/编辑页面的修改，并允许用户预订有可用副本的电影。
- 2. 添加仅限管理员使用的功能，以显示谁预订了电影。

## 26. PHP 面向对象编程简介

> “以唯一真正正确的方式。面向对象版的‘意大利面条式代码’当然就是‘千层面式代码’。（层数太多。）”
> 
> ——罗伯托·沃尔特曼。

## 26. PHP 中的面向对象编程简介

面向对象编程（OOP）是一种编程范式，它以更加模块化的方式开发程序。许多现代编程语言都具有 OOP 特性，PHP 也不例外。OOP 包含许多概念性组件。在最基本的层面上，它允许将程序所知道的内容（数据）和程序所执行的操作（功能）组合成模块化组件。这种方法不同于基本的过程式编程，在过程式编程中，许多函数与它们通常处理的数据是分离的。本章简要介绍使用 PHP 进行的面向对象编程。

由于本书涵盖使用 PHP 进行 Web 开发，因此我介绍该语言所支持的 OOP 的常见用法。如果你想了解更多关于 OOP 的原理和设计实践，我推荐 David Kung 的著作：*《面向对象软件工程：一种敏捷统一方法论》*¹，由 McGraw-Hill Education 出版。

我简要介绍以下主题：

- 类
- 属性
- 使用访问修饰符进行封装
- 访问器方法（Getter/Setter）
- $this 变量
- 通用方法
- 实例化并使用类
- 验证 Setter 方法的输入
- 继承
- 方法重写
- 构造函数
- PHP 数据库对象（PDO）

### 类

类将代码组织成模块化组件。通常将单个类放在其自己的文件中。在 PHP 中，使用 class 关键字定义类：

```
<?php
class Radio
{
}
```

[1] *《面向对象软件工程：一种敏捷统一方法论》*: http://phpa.me/mhws-oop-engineering

