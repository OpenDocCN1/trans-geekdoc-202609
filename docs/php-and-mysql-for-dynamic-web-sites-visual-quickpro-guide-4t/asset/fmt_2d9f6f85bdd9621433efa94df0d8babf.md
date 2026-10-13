
## 代码片段：错误处理与页面完成

```php
51  if (!$row) { // Show an error message.
52      $page_title = 'Error';
53      include ('includes/header.html');
54      echo '<div align="center">This page has been accessed in error!</div>';
55  }
56
57  // Complete the page:
58  include ('includes/footer.html');
59  ?>
```

---

The query is a join like the one in **`browse_prints.php`**, but it selects only the information for a particular print.

![Image](graphics/19_figure_24_f.jpg)

The result of running the `view_print.php` query in the mysql client.

### 5. 检索记录、设置标题并包含页头

If a record was returned, retrieve the information, set the page title, and include the HTML header:

```php
if (mysqli_num_rows($r) == 1) {
    $row = mysqli_fetch_array ($r, MYSQLI_ASSOC);
    $page_title = $row['print_name'];
    include ('includes/header.html');
}
```

The browser window’s title will be the name of the print.

### 6. 显示版画信息

Begin displaying the print information:

```php
echo "<div align=\"center\">
<b>{$row['print_name']}</b> by
{$row['artist']}<br />";
echo (is_null($row['size'])) ? '(No size information available)' : $row['size'];
echo "<br />\${$row['price']}
<a href=\"add_cart.php?pid=$pid\">Add to Cart</a>
</div><br />";
```

The header for the print will be the print’s name (in bold), followed by the artist’s name, the size of the print, and its price. Finally, a link is displayed giving the customer the option of adding this print to the shopping cart. The shopping cart link is to the **`add_cart.php`** script, passing it the print ID.

![Image](graphics/19_figure_25_g.jpg)

The print information and a link to buy it are displayed at the top of the page.

Because the print’s size can have a **`NULL`** value, the ternary operator is used to print out either the size or a default message.

### 7. 显示图像

Display the image:

```php
if ($image = @getimagesize ("../uploads/$pid")) {
    echo "<div align=\"center\"><img src=\"show_image.php?image=$pid&name=" . urlencode($row['image_name']) . "\" $image[3] alt=\"{$row['print_name']}\" /></div>\n";
} else {
    echo "<div align=\"center\">No image available.</div>\n";
}
```

Because the images are being safely stored outside of the Web root directory, another PHP script is required to provide the image to the browser (the **`show_image.php`** script is being used as a *proxy script*). The name of the image itself is just the print ID, which was already passed to this page in the URL.

This section of the script will first attempt to retrieve the image’s dimensions by using the **`getimagesize()`** function. If it is successful in doing so, the image itself will be displayed. That process is a little unusual in that the source for the image calls the **`show_image.php`** page. The **`show_image.php`** script, to be written next, expects the print ID to be passed in the URL, along with the image’s filename (stored in the database when the print is added). This use of a PHP script to display an image is exactly like the use of **`show_image.php`** in [Chapter 11](#ch11.html#ch11), only now it’s occurring within another page, not in its own window.

![Image](graphics/19_figure_26_h.jpg)

The HTML source of the `view_print.php` page shows how the `src` attribute of the `img` tag calls the `show_image.php` script, passing it the values it needs.

If the script could not retrieve the image information (because the image is not on the server or no image was uploaded), a message is displayed instead.

### 8. 显示描述

Display the description:

```php
echo '<p align="center">' . ((is_null($row['description'])) ? '(No description available)' : $row['description']) . '</p>';
```

Finally, the print’s description is added. A default message will be created if no print description was stored in the database.

![Image](graphics/19_figure_27_i.jpg)

The print’s image followed by its description.

### 9. 结束主条件判断

Complete the two main conditionals:

```php
} // End of the mysqli_num_rows() IF.
mysqli_close($dbc);
} // End of $_GET['pid'] IF.
```

### 10. 发生问题时显示错误信息

If a problem occurred, display an error message:

```php
if (!$row) {
    $page_title = 'Error';
    include ('includes/header.html');
    echo '<div align="center">This page has been accessed in error!</div>';
}
```

If the print’s information could not be retrieved from the database for whatever reason, then **`$row`** is still false and an error should be displayed. Because the HTML header would not have already been included if a problem occurred, it must be included here first.

![Image](graphics/19_figure_28_j.jpg)

The `view_print.php` page, should it not receive a valid print ID in the URL.

### 11. 完成页面

Complete the page:

```php
include ('includes/footer.html');
?>
```

### 12. 保存文件

Save the file as **`view_print.php`** and place it in your Web directory.

If you were to run this page in the browser at this point, no print image would be displayed as **`show_image.php`** has not yet been written.

---

### Tip

Many e-commerce sites use an image for the *Add to Cart* link. To do so in this example, replace the text *Add to Cart* (within the **`<a>`** link tag) with the code for the image to be used. The important consideration is that the **`add_cart.php`** page still gets passed the product ID number.

---

### Tip

If you wanted to add *Add to Cart* links on a page that displays multiple products (like **`browse_prints.php`**), do exactly what’s done here for individual products. Just make sure that each link passes the right print ID to the **`add_cart.php`** page.

---

### Tip

If you want to show the availability of a product, add an *in_stock* field to the *prints* table. Then display an *Add to Cart* link or *Product Currently Out of Stock* message according to the value from this column for that print.

---

## 编写 `show_image.php`

### 1. 创建新 PHP 文档

Begin a new PHP document in your text editor or IDE, to be named **`show_image.php`** (**[Script 19.8](#ch19.html#ch19ex08)**):

```php
<?php # Script 19.8 - show_image.php
$image = FALSE;
$name = (!empty($_GET['name'])) ? $_GET['name'] : 'print image';
```

This script will do the same thing as **`show_image.php`** from [Chapter 11](#ch11.html#ch11), except that there are two values being passed to this page. The actual image’s filename on the server will be a number, corresponding to the print ID. The original image’s filename was stored in the database and will be used when sending the image to the Web browser. This page will not contain any HTML, and nothing can be sent to the Web browser prior to this opening PHP tag.

**Script 19.8.** This script is called by `view_print.php` ([Script 19.7](#ch19.html#ch19ex07)) and displays the image stored in the **`uploads`** directory.

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
