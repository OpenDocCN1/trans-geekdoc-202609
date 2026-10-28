
## index.php 文件

```php
<?php
require_once('database.php');

// Get category ID
$category_id = filter_input(INPUT_GET, 'category_id',
    FILTER_VALIDATE_INT);
if ($category_id == NULL || $category_id == FALSE) {
    $category_id = 1;
}

// Get name for selected category
$queryCategory = 'SELECT * FROM categories
    WHERE categoryID = :category_id';
$statement1 = $db->prepare($queryCategory);
$statement1->bindValue(':category_id', $category_id);
$statement1->execute();
$category = $statement1->fetch();
$category_name = $category['categoryName'];
$statement1->closeCursor();

// Get all categories
$queryAllCategories = 'SELECT * FROM categories
    ORDER BY categoryID';
$statement2 = $db->prepare($queryAllCategories);
$statement2->execute();
$categories = $statement2->fetchAll();
$statement2->closeCursor();

// Get products for selected category
$queryProducts = 'SELECT * FROM products
    WHERE categoryID = :category_id
    ORDER BY productID';
$statement3 = $db->prepare($queryProducts);
$statement3->bindValue(':category_id', $category_id);
$statement3->execute();
$products = $statement3->fetchAll();
$statement3->closeCursor();
?>
<!DOCTYPE html>
<html>
<!-- the head section -->
<head>
<title>My Guitar Shop</title>
<link rel="stylesheet" type="text/css" href="main.css" />
</head>
```

本文件的 HTML 包含嵌入的 PHP 标签，用于显示文件开头 PHP 脚本中定义的变量。首先，第一个 foreach 循环为每个类别显示一个链接列表。这里，href 属性指定了一个包含类别 ID 的 URL，而链接则显示该类别的名称。因此，如果用户点击其中一个链接，该应用程序将使用 GET 方法将该链接的类别 ID 传递给 index.php 文件。这会返回一个显示新类别产品的网页。

这些类别链接存储在无序列表的 `<li>` 标签内。然而，该应用程序的 CSS 关闭了此列表的项目符号，因此项目符号不会显示。虽然本书中未显示任何应用程序的 CSS，但它可在下载的应用程序中找到，以便您可以查看其工作原理。

在第一个 foreach 循环之后，此页面在产品表格上方显示当前类别的名称。然后，它使用第二个 foreach 循环显示当前类别的产品。这在 HTML 表格中显示了结果集中五个列中的三列。具体来说，它在第一列显示产品的代码，在第二列显示名称，在第三列显示价格。然而，它在此表格中未显示产品 ID 或类别 ID。

在您审阅此代码时，请注意两个 foreach 循环都使用了本章前面描述的替代语法。这使您的代码更易于阅读，因为可以轻松看出每个 foreach 循环的结束位置。此外，两个循环都使用字符串索引而不是数字索引来获取行数组中的值。这使您的代码更易于阅读，因为可以轻松看出每列中的数据与每列标题的对应关系。

## index.php 文件（续）

```html
<!-- the body section -->
<body>
<main>
<h1>Product List</h1>
<aside>
    <!-- display a list of categories -->
    <h2>Categories</h2>
    <nav>
    <ul>
        <?php foreach ($categories as $category) : ?>
        <li>
            <a href="?category_id=<?php echo $category['categoryID']; ?>">
                <?php echo $category['categoryName']; ?>
            </a>
        </li>
        <?php endforeach; ?>
    </ul>
    </nav>
</aside>

<section>
    <!-- display a table of products -->
    <h2><?php echo $category_name; ?></h2>
    <table>
        <tr>
            <th>Code</th>
            <th>Name</th>
            <th class="right">Price</th>
        </tr>

        <?php foreach ($products as $product) : ?>
        <tr>
            <td><?php echo $product['productCode']; ?></td>
            <td><?php echo $product['productName']; ?></td>
            <td class="right"><?php echo $product['listPrice']; ?></td>
        </tr>
        <?php endforeach; ?>
    </table>
</section>
</main>
<footer></footer>
</body>
</html>
```

## 产品管理器应用程序

本章结尾介绍了名为产品管理器应用程序的更复杂的数据库应用程序。该应用程序在多个方面增强了产品查看器应用程序。最重要的是，它允许用户添加和删除产品。

### 用户界面

图 4-8 的第 1 部分显示了产品管理器应用程序用户界面的主要页面：产品列表页面和添加产品页面。这两个页面都在页眉中包含应用程序的名称，并且这两个页面都在页脚中包含版权声明。这些页面还包含将页眉和页脚与页面主体分隔开的边框。

产品列表页面允许用户查看和删除产品。它显示类别列表和当前类别的产品表格。这与产品查看器应用程序的主页类似。然而，此列表为每个产品包含一个删除按钮，允许用户删除该产品。此外，此页面在表格下方包含一个添加产品链接，允许用户显示添加产品页面。

添加产品页面允许用户添加新产品。此页面首先显示一个下拉列表，允许用户为产品选择类别。然后，它显示三个文本框，允许用户输入产品的代码、名称和价格。接下来，它显示一个添加产品按钮，允许用户提交产品数据。最后，此页面显示一个查看产品列表链接，允许用户在不添加产品的情况下返回产品列表页面。

### 产品列表页面

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_170_0.png)

### 添加产品页面

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_170_1.png)

Figure 4-8 — 产品管理器应用程序（第 1 部分，共 5 部分）

### 代码

图 4-8 的第 2 部分至第 5 部分显示了产品管理器应用程序的代码。然而，这些部分未显示 database.php 和 database_error.php 文件的代码，因为该代码与产品查看器应用程序的代码相同。

index.php 文件的工作方式与产品查看器应用程序的 index.php 文件类似。因此，您应该已经理解了其中的大部分内容。然而，有一些重要的区别。

首先，第一条语句使用 require_once 语句。因此，此代码只加载 database.php 文件一次。这意味着如果 delete_product.php 或 add_product.php 文件（本图后面描述）已加载该文件，则不会再次加载文件。这提高了应用程序的效率。

接下来，第一段代码开始时检查 $category_id 变量是否已设置。因此，只有在 $category_id 变量尚未由本图后面描述的 delete_product.php 或 add_product.php 文件设置时，此代码才会尝试从 $_GET 数组获取类别 ID。

在 HTML 中，此代码使用 <header> 和 <footer> 标签为页面定义页眉和页脚。这里，页眉显示应用程序的名称（Product Manager），页脚显示应用程序的版权通知。

### index.php 文件

```php
<?php
    require_once('database.php');

    // Get category ID
    if (!isset($category_id)) {
        $category_id = filter_input(INPUT_GET, 'category_id',
                            FILTER_VALIDATE_INT);
        if ($category_id == NULL || $category_id == FALSE) {
            $category_id = 1;
        }
    }

    // Get name for selected category
    $queryCategory = 'SELECT * FROM categories
                      WHERE categoryID = :category_id';
    $statement1 = $db->prepare($queryCategory);
    $statement1->bindValue(':category_id', $category_id);
    $statement1->execute();
    $category = $statement1->fetch();
    $category_name = $category['categoryName'];
    $statement1->closeCursor();

    // Get all categories
    $queryAllCategories = 'SELECT * FROM categories
                           ORDER BY categoryID';
    $statement2 = $db->prepare($queryAllCategories);
    $statement2->execute();
    $categories = $statement2->fetchAll();
    $statement2->closeCursor();

    // Get products for selected category
    $queryProducts = 'SELECT * FROM products
                      WHERE categoryID = :category_id
                      ORDER BY productID';
    $statement3 = $db->prepare($queryProducts);
    $statement3->bindValue(':category_id', $category_id);
    $statement3->execute();
    $products = $statement3->fetchAll();
    $statement3->closeCursor();
?>
<!DOCTYPE html>
<html>

<!-- the head section -->
<head>
    <title>My Guitar Shop</title>
    <link rel="stylesheet" type="text/css" href="main.css" />
</head>

<!-- the body section -->
<body>
<header><h1>Product Manager</h1></header>
<main>
    <h1>Product List</h1>
```

Figure 4-8 产品管理器应用程序（第 2 部分，共 5 部分）
