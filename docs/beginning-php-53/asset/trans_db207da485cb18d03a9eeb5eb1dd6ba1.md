

## 尝试一下 创建一个简单的购物车

在本示例中，您使用会话为在线商店构建一个非常简单的购物车。有三种产品可供选择，用户可以将任何或所有产品添加到购物车中，从购物车中删除产品，并查看购物车的内容。

将以下代码另存为 `shopping_cart.php` 并在 Web 浏览器中运行该脚本。单击“添加项目”链接将项目添加到购物车，然后单击“删除”链接将其移除。图 10-3 展示了购物车的实际运行情况。

```
<?php
session_start();

class Product {
private $productId;
private $productName;
private $price;

public function __construct( $productId, $productName, $price ) {
$this->productId = $productId;
$this->productName = $productName;
$this->price = $price;
}

public function getId() {
return $this->productId;
}

public function getName() {
return $this->productName;
}

public function getPrice() {
return $this->price;
}
}

$products = array(
1 => new Product( 1, "SuperWidget", 19.99 ),
2 => new Product( 2, "MegaWidget", 29.99 ),
3 => new Product( 3, "WonderWidget", 39.99 )
);

if ( !isset( $_SESSION["cart"] ) ) $_SESSION["cart"] = array();

if ( isset( $_GET["action"] ) and $_GET["action"] == "addItem" ) {
addItem();
} elseif ( isset( $_GET["action"] ) and $_GET["action"] == "removeItem" ) {
removeItem();
} else {
displayCart();
}
}

function addItem() {
    global $products;
    if ( isset( $_GET["productId"] ) and $_GET["productId"] >= 1 and $_GET["productId"] <= 3 ) {
        $productId = (int) $_GET["productId"];

        if ( !isset( $_SESSION["cart"][$productId] ) ) {
            $_SESSION["cart"][$productId] = $products[$productId];
        }
    }

    session_write_close();
    header( "Location: shopping_cart.php" );
}

function removeItem() {
    global $products;
    if ( isset( $_GET["productId"] ) and $_GET["productId"] >= 1 and $_GET["productId"] <= 3 ) {
        $productId = (int) $_GET["productId"];

        if ( isset( $_SESSION["cart"][$productId] ) ) {
            unset( $_SESSION["cart"][$productId] );
        }
    }

    session_write_close();
    header( "Location: shopping_cart.php" );
}

function displayCart() {
    global $products;
    ?>
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
        "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
        <head>
            <title>A shopping cart using sessions</title>
            <link rel="stylesheet" type="text/css" href="common.css" />
        </head>
        <body>

        <h1>Your shopping cart</h1>

        <dl>

        <?php
        $totalPrice = 0;
        foreach ( $_SESSION["cart"] as $product ) {
            $totalPrice += $product->getPrice();
        ?>
            <dt><?php echo $product->getName() ?></dt>
            <dd><?php echo number_format( $product->getPrice(), 2 ) ?>
 <a href="shopping_cart.php?action=removeItem&productId=<?php echo
 $product->getId() ?>">Remove</a></dd>
 <?php } ?>
 <dt>Cart Total:</dt>
 <dd><strong><?php echo number_format( $totalPrice, 2 ) ?></strong></dd>
 </dl>
 <h1>Product list</h1>
 <dl>
 <?php foreach ( $products as $product ) { ?>
 <dt><?php echo $product->getName() ?> </dt>
 <dd><?php echo number_format( $product->getPrice(), 2 ) ?>
 <a href="shopping_cart.php?action=addItem&amp;productId=<?php echo
 $product->getId() ?>">Add Item</a></dd>
 <?php } ?>
 </dl>
 <?php
 }
 ?>
 </body>
 </html>
```

![](img/1ddec54918a4802eb9b4febec3d4e7f6_323_0.png)

图 10-3

### 工作原理

脚本首先调用 `session_start()` 来创建一个新会话，或者如果该用户已有会话则沿用现有会话。然后脚本定义一个 `Product` 类来保存商店中的产品，以及一个包含三个 `Product` 对象的全局 `$products` 数组，以产品的数字 ID 作为键。（在实际场景中，您可能会将产品存储在数据库中。）

然后代码将用户的购物车初始化为空数组（如果尚不存在）。该数组作为 `$_SESSION` 超全局数组中的一个元素 `cart` 进行存储。与 `$products` 数组一样，此数组将按产品 ID 存储用户选择的产品：

```
if ( !isset( $_SESSION["cart"] ) ) $_SESSION["cart"] = array();
```

接下来的几行代码构成了脚本的主要决策逻辑，如果用户选择将项目添加到购物车，则调用 `addItem()`；如果用户选择删除产品，则调用 `removeItem()`；如果用户未选择任何选项，则调用 `displayCart()`：

```
if ( isset( $_GET["action"] ) and $_GET["action"] == "addItem" ) {
    addItem();
} elseif ( isset( $_GET["action"] ) and $_GET["action"] == "removeItem" ) {
    removeItem();
} else {
    displayCart();
}
```

`addItem()` 函数在查询字符串中查找 `productId` 字段，如果存在且有效，则通过将数组元素插入 `$_SESSION["cart"]` 数组（以产品 ID 为键）将相应的 `Product` 对象添加到用户的购物车中。然后它发送一个 `Location:` 标头以重新加载购物车：

```
function addItem() {
    global $products;
    if ( isset( $_GET["productId"] ) and $_GET["productId"] >= 1 and $_GET["productId"] <= 3 ) {
        $productId = (int) $_GET["productId"];
        if ( !isset( $_SESSION["cart"][$productId] ) ) {
            $_SESSION["cart"][$productId] = $products[$productId];
        }
    }
    session_write_close();
    header( "Location: shopping_cart.php" );
}
```

请注意，该函数在发送 `Location:` 标头之前调用 PHP 函数 `session_write_close()`。这会强制将 `$_SESSION` 数组中的数据写入服务器硬盘上的会话文件。虽然 PHP 在脚本退出时通常也会执行此操作，但在重定向或重新加载浏览器之前调用 `session_write_close()` 是个好主意，以确保 `$_SESSION` 数据写入磁盘并可用于下一次浏览器请求。

`removeItem()` 执行与 `addItem()` 相反的操作：在验证 `productId` 字段后，它从用户的购物车数组中删除相应的产品，然后刷新浏览器：

```php
function removeItem() {
    global $products;
    if ( isset( $_GET["productId"] ) && $_GET["productId"] >= 1 && $_GET["productId"] <= 3 ) {
        $productId = (int) $_GET["productId"];

        if ( isset( $_SESSION["cart"][$productId] ) ) {
            unset( $_SESSION["cart"][$productId] );
        }
    }

    session_write_close();
    header( "Location: shopping_cart.php" );
}
```

最后，`displayCart()` 显示用户的购物车以及可用产品列表。在显示 XHTML 页面标题后，该函数遍历购物车中的每个项目，显示产品名称、价格和一个“删除”链接，用户可以使用该链接将产品从购物车中移除。它在遍历过程中还会计算购物车中所有产品的总价，然后在购物车下方显示总计：

```php
<dl>
<?php
$totalPrice = 0;
foreach ( $_SESSION["cart"] as $product ) {
    $totalPrice += $product->getPrice();
?>
    <dt><?php echo $product->getName() ?></dt>
    <dd><?php echo number_format( $product->getPrice(), 2 ) ?>
    <a href="shopping_cart.php?action=removeItem&amp;productId=<?php echo $product->getId() ?>">Remove</a></dd>
<?php } ?>
    <dt>Cart Total:</dt>
    <dd><strong><?php echo number_format( $totalPrice, 2 ) ?></strong></dd>
</dl>
```

`displayCart()` 函数随后列出可用产品及其价格。每个产品都有一个相应的“添加项目”链接，购物者可以使用该链接将产品添加到购物车中：

```php
<dl>
<?php foreach ( $products as $product ) { ?>
    <dt><?php echo $product->getName() ?></dt>
    <dd><?php echo number_format( $product->getPrice(), 2 ) ?>
    <a href="shopping_cart.php?action=addItem&amp;productId=<?php echo $product->getId() ?>">Add Item</a></dd>
<?php } ?>
</dl>

