
如果无论何种原因无法从数据库检索版画信息，则 `$row` 仍为 false，应显示错误。由于如果发生问题 HTML 页头尚未被包含，因此必须先在此处包含它。

![Image](img/19_figure_28_j.jpg)

`view_print.php` 页面，假如 URL 中未接收到有效的版画 ID。

### 11. 完成页面

完成页面：

```php
include ('includes/footer.html');
?>
```

### 12. 保存文件

将文件保存为 `view_print.php` 并放置在您的 Web 目录中。

如果此时在浏览器中运行此页面，将不会显示版画图像，因为 `show_image.php` 尚未编写。

---

### 提示

许多电子商务网站对 *Add to Cart*（加入购物车）链接使用图像。要在本例中实现这一点，请将 `<a>` 链接标签内的文本 *Add to Cart* 替换为要使用的图像代码。重要的是 `add_cart.php` 页面仍能接收到产品 ID 编号。

---

### 提示

如果您想在显示多个产品的页面（如 `browse_prints.php`）上添加 *Add to Cart* 链接，请完全照此处针对单个产品所做的操作。只需确保每个链接将正确的版画 ID 传递给 `add_cart.php` 页面。

---

### 提示

如果您想显示产品的库存情况，请在 *prints* 表中添加一个 *in_stock* 字段。然后根据该版画在该列中的值，显示 *Add to Cart* 链接或 *Product Currently Out of Stock*（产品目前缺货）消息。

---

### 编写 `show_image.php`

### 1. 创建新 PHP 文档

在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `show_image.php`（**脚本 19.8**）：

```php
<?php # Script 19.8 - show_image.php

$image = FALSE;

$name = (!empty($_GET['name'])) ? $_GET['name'] : 'print image';
```

该脚本将执行与 第 11 章 中的 `show_image.php` 相同的操作，不同之处在于有两个值被传递给此页面。服务器上实际图像的文件名将是一个数字，对应版画 ID。原始图像文件名存储在数据库中，将在向 Web 浏览器发送图像时使用。此页面不包含任何 HTML，且在此开启 PHP 标签之前，不能向 Web 浏览器发送任何内容。

**脚本 19.8.** 此脚本由 `view_print.php` (脚本 19.7) 调用，并显示存储在 `uploads` 目录中的图像。

---

```php
1   <?php # Script 19.8 - show_image.php

2   // This pages retrieves and shows an

3       image.

4

5   // Flag variables:

6   $image = FALSE;

7   $name = (!empty($_GET['name'])) ? $_

8       GET['name'] : 'print image';

9

10  // Check for an image value in the URL:

11  if (isset($_GET['image']) && filter_var($_GET['image'], FILTER_VALIDATE_INT,

12      array('min_range' => 1))  ) {

13

14      // Full image path:

15      $image = '../uploads/' . $_GET['image'];

16

17      // Check that the image exists and is

18          a file:

19      if (!file_exists ($image) || (!is_file($image))) {

20          $image = FALSE;

21      }

22

23  } // End of $_GET['image'] IF.

24

25  // If there was a problem, use the

26      default image:

27  if (!$image) {

28      $image = 'images/unavailable.png';

29      $name = 'unavailable.png';
```

### 代码片段

```php
25  }

26

27  // 获取图像信息：

28  $info = getimagesize($image);

29  $fs = filesize($image);

30

31  // 发送内容信息：

32  header ("Content-Type: {$info['mime']}\n");

33  header ("Content-Disposition: inline; filename=\"$name\"\n");

34  header ("Content-Length: $fs\n");

35

36  // 发送文件：

37  readfile ($image);
```

---

此处初始化了两个标志变量。第一个变量 `$image` 将引用服务器上的物理图像。它被假定为 false，需要被证明为真。`$name` 变量将作为提供给 Web 浏览器的文件名，应来自 URL。如果没有，则分配一个默认值。

### 2. 检查 URL 中的图像值

```php
if (isset($_GET['image']) && filter_var($_GET['image'], FILTER_VALIDATE_INT, array('min_range' => 1))  ) {
```

在继续之前，确保脚本接收到了一个图像值，该值应是 `view_print.php` 中每个印刷品 HTML `src` 属性的一部分 ![Image](img/graycircle-h.jpg)。

### 3. 检查图像是否作为文件存在于服务器上

```php
$image = '../uploads/' . $_GET['image'];

if (!file_exists ($image) || (!is_file($image))) {

  $image = FALSE;

}
```

作为一项安全措施，图像的完整路径被硬编码为 `../uploads` 和接收到的图像名称的组合。你也可以在此处验证文件的 MIME 类型（`image/jpg`、`image/gif`），以增加安全性。

接下来，脚本检查图像是否存在于服务器上，以及它是否为文件（而不是目录）。如果任一条件为 FALSE，则将 `$image` 设置为 FALSE，表示出现问题。

### 4. 完成验证条件并检查问题

```php
} // End of $_GET['image'] IF.

if (!$image) {

  $image = 'images/unavailable.png';

  $name = 'unavailable.png';

}
```

如果图像不存在、不是文件，或者没有图像名传递给此脚本，则此条件为 TRUE。在这种情况下，将使用默认图像。然而，要使这种情况发生，用户必须进行大量的黑客攻击：`view_print.php` 脚本会对图像进行一些初步验证，只有在能够访问图像时才会调用 `show_image.php`。

### 5. 检索图像信息

```php
$info = getimagesize($image);

$fs = filesize($image);
```

为了将文件发送给 Web 浏览器，脚本需要知道文件的类型和大小。此代码与第 11 章中的相同。

### 6. 发送文件

```php
header ("Content-Type: {$info['mime']}\n");

header ("Content-Disposition: inline; filename=\"$name\"\n");

header ("Content-Length: $fs\n");

readfile ($image);
```

这些 `header()` 调用将向 Web 浏览器发送有关后续文件的信息，这与第 11 章中完全相同。重温一下整体语法：第一行根据 MIME 类型准备浏览器接收文件。第二行设置正在发送的文件名。

最后一个 `header()` 函数指示预期接收多少数据。文件数据本身使用 `readfile()` 函数发送，该函数读取文件并立即将内容发送给 Web 浏览器。

### 7. 保存并测试

将文件保存为 `show_image.php`，将其放在你的 Web 目录中，并通过查看任意印刷品在 Web 浏览器中测试它。

请注意，此页面不包含 HTML。它仅向 Web 浏览器发送一个图像文件。与第 11 章一样，省略了结束 PHP 标签，以避免潜在问题。

---

> **提示**
>
> 如果 `view_print.php` 页面由于某些原因未显示图像，你需要通过在 Web 浏览器中直接运行 `show_image.php` 来调试问题。查看 `view_print.php` 的 HTML 源代码，找到 `img` 标签 `src` 属性的值。然后将其用作你的 URL（换句话说，转到 `http://www.example.com/show_image.php?image=23&name=BirthOfVenus.jpeg`）。如果发生错误，直接运行 `show_image.php` 是发现它的最佳方法。

---

### 搜索产品目录

该数据库的结构使得搜索功能相当容易实现，如果你想添加的话。目前，只有三个逻辑字段可用于搜索：印刷品的名称、其描述和艺术家的姓氏。可以使用以下语法在这些字段上运行 `LIKE` 查询：

```sql
SELECT...WHERE prints.description LIKE'%keyword%' OR prints.print_name LIKE '%keyword%' ...
```

另一种选择是创建一个高级搜索，让用户选择搜索艺术家姓名还是印刷品名称（类似于互联网电影数据库 [www.imdb.com](http://www.imdb.com) 对人名与电影标题的处理方式）。

---

### 脚本 19.9：add_cart.php

此脚本通过引用产品（或印刷品）ID 并操作会话数据，将产品添加到购物车。

```php
<?php # Script 19.9 - add_cart.php

// This page adds prints to the shopping

// cart.

// Set the page title and include the

// HTML header:

$page_title = 'Add to Cart';

include ('includes/header.html');

if (isset ($_GET['pid']) && filter_

var($_GET['pid'], FILTER_VALIDATE_INT,

array('min_range' => 1))  ) { // Check

for a print ID.

  $pid = $_GET['pid'];

  // Check if the cart already contains

  // one of these prints;

  // If so, increment the quantity:

  if (isset($_SESSION['cart'][$pid])) {

    $_SESSION['cart'][$pid]

      ['quantity']++; // Add another.

    // Display a message:

    echo '<p>Another copy of the print

      has been added to your shopping

      cart.</p>';

  } else { // New product to the cart.

    // Get the print's price from the

    // database:

    require ('../mysqli_connect.php');

    // Connect to the database.

    $q = "SELECT price FROM prints

      WHERE print_id=$pid";

    $r = mysqli_query ($dbc, $q);

    if (mysqli_num_rows($r) == 1) { //

      Valid print ID.

      // Fetch the information.

      list($price) = mysqli_fetch_

      array ($r, MYSQLI_NUM);

      // Add to the cart:

      $_SESSION['cart'][$pid] = array

        ('quantity' => 1, 'price' =>

        $price);

      // Display a message:

      echo '<p>The print has been

        added to your shopping cart.

        </p>';

    } else { // Not a valid print ID.

      echo '<div align="center">This

        page has been accessed in

        error!</div>';

    }

    mysqli_close($dbc);

  } // End of isset($_SESSION['cart']

    [$pid] conditional.

} else { // No print ID.

  echo '<div align="center">This page

    has been accessed in error!</div>';

}

include ('includes/footer.html');

?>
```

---

### 购物车

一旦你创建了产品目录，如前面的页面所做的那样，实际的购物车本身可以出奇地简单。我在本网站中选择的方法是将产品 ID、价格和数量记录在会话中。了解这三件事将允许脚本计算总计并执行所需的其他所有操作。

接下来的两个示例将为购物车提供所有必要的功能。第一个脚本 `add_cart.php` 用于向购物车添加商品。第二个脚本 `view_cart.php` 既显示购物车的内容，又允许顾客更新购物车。

#### 添加商品

`add_cart.php` 脚本将接收一个参数——所购印刷品的 ID，并利用该信息更新购物车。购物车本身存储在会话中，通过 `$_SESSION['cart']` 变量访问。购物车将是一个多维数组，其键为产品 ID。数组元素的值本身也是数组：一个元素用于数量，另一个用于价格（表 19.6）。

**表 19.6. `$_SESSION['cart']` 示例值**

![Image](img/19tab06.jpg)

#### 创建 add_cart.php

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
