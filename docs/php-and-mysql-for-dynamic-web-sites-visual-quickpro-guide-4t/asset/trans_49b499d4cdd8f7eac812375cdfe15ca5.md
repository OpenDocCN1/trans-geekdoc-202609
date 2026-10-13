
接下来的两个示例将为购物车提供所有必要的功能。第一个脚本 `add_cart.php` 用于向购物车添加商品。第二个脚本 `view_cart.php` 既显示购物车的内容，又允许顾客更新购物车。

### 添加商品

`add_cart.php` 脚本将接收一个参数——所购印刷品的 ID，并利用该信息更新购物车。购物车本身存储在会话中，通过 `$_SESSION['cart']` 变量访问。购物车将是一个多维数组，其键为产品 ID。数组元素的值本身也是数组：一个元素用于数量，另一个用于价格（表 19.6）。

**表 19.6. `$_SESSION['cart']` 示例值**

![Image](graphics/19tab06.jpg)

### 创建 add_cart.php

**1.** 在文本编辑器或 IDE 中新建一个 PHP 文档，命名为 `add_cart.php`（脚本 19.9）：

```php
<?php # Script 19.9 - add_cart.php

$page_title = 'Add to Cart';

include ('includes/header.html');
```

**2.** 检查是否有印刷品 ID 传递给了该脚本：

```php
if (isset ($_GET['pid']) && filter_var($_GET['pid'], FILTER_VALIDATE_INT, array('min_range' => 1))) {

    $pid = $_GET['pid'];
```

与 `view_print.php` 脚本一样，如果未接收到印刷品 ID 或接收到的 ID 非数字，则脚本不应继续执行。如果已接收到，则将其值赋给 `$pid`，供脚本后续使用。

**3.** 确定该印刷品的副本是否已添加到购物车中：

```php
if (isset($_SESSION['cart'][$pid])) {

    $_SESSION['cart'][$pid]['quantity']++;

    echo '<p>Another copy of the print has been added to your shopping cart.</p>';
```

在将当前印刷品添加到购物车（通过将其数量设为 1）之前，先检查购物车中是否已有该副本。例如，如果顾客选择了印刷品 #519，然后决定再添加一个，购物车现在应包含该印刷品的两份副本。因此，脚本首先检查购物车是否有当前印刷品 ID 对应的值。如果有，则增加数量。代码 `$_SESSION['cart'][$pid]['quantity']++` 等同于

```php
$_SESSION['cart'][$pid]['quantity'] = $_SESSION['cart'][$pid]['quantity'] + 1.
```

最后，显示一条消息 ![Image](graphics/circle-a.jpg)。

![Image](graphics/19_figure_29_a.jpg)

![Image](graphics/circle-a.jpg) 点击购物车中已存在商品的 *Add to Cart*（加入购物车）链接后的结果。

**4.** 如果产品不在购物车中，则从数据库检索其价格：

```php
} else { // New product to the cart.

    require ('../mysqli_connect.php');

    $q = "SELECT price FROM prints WHERE print_id=$pid";

    $r = mysqli_query ($dbc, $q);

    if (mysqli_num_rows($r) == 1) {

        list($price) = mysqli_fetch_array ($r, MYSQLI_NUM);
```

如果产品当前不在购物车中，则执行此 `else` 子句。这里使用印刷品 ID 从数据库中检索该印刷品的价格。

**5.** 将新产品添加到购物车：

```php
$_SESSION['cart'][$pid] = array ('quantity' => 1, 'price' => $price);

echo '<p>The print has been added to your shopping cart.</p>';
```

检索到商品价格后，向 `$_SESSION['cart']` 多维数组添加一个新元素。由于 `$_SESSION['cart']` 中的每个元素本身就是一个数组，因此使用 `array()` 函数设置数量和价格。然后显示一条简单的消息 ![Image](graphics/circle-b.jpg)。

![Image](graphics/19_figure_30_b.jpg)

![Image](graphics/circle-b.jpg) 向购物车添加新商品后的结果。

**6.** 完成条件判断结构：

```php
        } else { // Not a valid print ID.

            echo '<div align="center"> This page has been accessed in error!</div>';

        }

        mysqli_close($dbc);

    } // End of isset($_SESSION['cart'][$pid] conditional.

} else { // No print ID.

    echo '<div align="center">This page has been accessed in error!</div>';

}
```

第一个 `else` 适用于无法从数据库检索到价格的情况，意味着提交的印刷品 ID 无效。第二个 `else` 适用于页面未接收到印刷品 ID 或接收到非数字 ID 的情况。在这两种情况下，都将显示一条错误消息 ![Image](graphics/circle-c.jpg)。

![Image](graphics/19_figure_31_c.jpg)

![Image](graphics/circle-c.jpg) `add_cart.php` 页面仅当 URL 中接收到有效的印刷品 ID 时，才会向购物车添加商品。

**7.** 包含 HTML 页脚并完成 PHP 页面：

```php
include ('includes/footer.html');

?>
```

**8.** 将文件保存为 `add_cart.php`，放置在您的 Web 目录中，并在 Web 浏览器中测试（通过点击 *Add to Cart* 链接）。

***

> **Tip**
>
> 购物车中最重要的存储内容是唯一的产品 ID 和该商品的数量。其他所有信息（包括价格）都可以从数据库中检索。或者，您也可以从数据库检索价格、印刷品名称和艺术家名称，并将所有这些信息存储在会话中，以便在网站的任何位置轻松显示。

***

> **Tip**
>
> 购物车存储在 `$_SESSION['cart']` 中，而不仅仅是 `$_SESSION`。推测其他信息（如数据库中的用户 ID）也会存储在 `$_SESSION` 中。

***

### 查看购物车

`view_cart.php` 脚本将比 `add_cart.php` 更复杂，因为它有两个用途。首先，它将详细显示购物车的内容 ![Image](graphics/circle-d.jpg)。其次，它将给顾客提供更新购物车的选项，通过更改其中商品的数量（或将数量设为 0 来删除商品）。为了实现这双重功能，购物车的内容将以表单形式显示，该表单提交回同一个页面。

![Image](graphics/19_figure_32_d.jpg)

![Image](graphics/circle-d.jpg) 以表单形式显示的购物车，可在其中更改具体数量。

最后，该页面将链接到 `checkout.php` 脚本，旨在作为结账流程的第一步。

### 创建 view_cart.php

**1.** 在文本编辑器或 IDE 中新建一个 PHP 文档，命名为 `view_cart.php`（脚本 19.10）：

```php
<?php # Script 19.10 - view_cart.php

$page_title = 'View Your Shopping Cart';

include ('includes/header.html');
```

**脚本 19.10.** `view_cart.php` 脚本既显示购物车的内容，又允许用户更新购物车的内容。

***

```php
1   <?php # Script 19.10 - view_cart.php
2   // This page displays the contents of
        the shopping cart.
3   // This page also lets the user update
        the contents of the cart.
4
5   // Set the page title and include the
        HTML header:
6   $page_title = 'View Your Shopping Cart';
7   include ('includes/header.html');
8
9   // Check if the form has been submitted
        (to update the cart):
10  if ($_SERVER['REQUEST_METHOD'] == 'POST')
{
11
12      // Change any quantities:
13      foreach ($_POST['qty'] as $k => $v) {
14
15          // Must be integers!
16          $pid = (int) $k;
17          $qty = (int) $v;
18
19          if ( $qty == 0 ) { // Delete.
20              unset ($_SESSION['cart'][$pid]);
21          } elseif ( $qty > 0 ) { // Change
                quantity.
22              $_SESSION['cart'][$pid]
                    ['quantity'] = $qty;
23          }
24
25      } // End of FOREACH.
26
27  } // End of SUBMITTED IF.
28
29  // Display the cart if it's not empty...
30  if (!empty($_SESSION['cart'])) {
31
32      // Retrieve all of the information for the prints in the cart:
33      require ('../mysqli_connect.php'); // Connect to the database.
```
