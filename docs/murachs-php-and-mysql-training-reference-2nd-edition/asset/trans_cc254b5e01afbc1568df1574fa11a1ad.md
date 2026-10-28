

### add_item_view.php 文件

```php
<!DOCTYPE html>
<html>
<head>
    <title>My Guitar Shop</title>
    <link rel="stylesheet" type="text/css" href="main.css">
</head>
<body>
    <header>
        <h1>My Guitar Shop</h1>
    </header>
    <main>
        <h1>Add Item</h1>
        <form action="." method="post">
            <input type="hidden" name="action" value="add">
            <label>Name:</label>
            <select name="productkey">
                <?php foreach($products as $key => $product) :
                    $cost = number_format($product['cost'], 2);
                    $name = $product['name'];
                    $item = $name . ' ($' . $cost . ')';
                ?>
                    <option value="<?php echo $key; ?>">
                        <?php echo $item; ?>
                    </option>
                <?php endforeach; ?>
            </select><br>
            <label>Quantity:</label>
            <select name="itemqty">
                <?php for($i = 1; $i <= 10; $i++) : ?>
                    <option value="<?php echo $i; ?>">
                        <?php echo $i; ?>
                    </option>
                <?php endfor; ?>
            </select><br>
            <label>&nbsp;</label>
            <input type="submit" value="Add Item">
        </form>
        <p><a href=".?action=show_cart">View Cart</a></p>
    </main>
</body>
</html>
```

### cart_view.php 文件

```php
<!DOCTYPE html>
<html>
<head>
    <title>My Guitar Shop</title>
    <link rel="stylesheet" type="text/css" href="main.css">
</head>
<body>
    <header>
        <h1>My Guitar Shop</h1>
    </header>
    <main>
        <h1>Your Cart</h1>
        <?php if (empty($_SESSION['cart']) ||
                count($_SESSION['cart']) == 0) : ?>
            <p>There are no items in your cart.</p>
        <?php else: ?>
            <form action="." method="post">
            <input type="hidden" name="action" value="update">
            <table>
                <tr id="cart_header">
                    <th class="left">Item</th>
                    <th class="right">Item Cost</th>
                    <th class="right">Quantity</th>
                    <th class="right">Item Total</th>
                </tr>

                <?php foreach ( $_SESSION['cart'] as $key => $item ) :
                    $cost  = number_format($item['cost'], 2);
                    $total = number_format($item['total'], 2);
                ?>
                <tr>
                    <td>
                        <?php echo $item['name']; ?>
                    </td>
                    <td class="right">
                        $<?php echo $cost; ?>
                    </td>
                    <td class="right">
                        <input type="text" class="cart_qty"
                            name="newqty[<?php echo $key; ?>]"
                            value="<?php echo $item['qty']; ?>">
                    </td>
                    <td class="right">
                        $<?php echo $total; ?>
                    </td>
                </tr>
                <?php endforeach; ?>
<tr id="cart_footer">
    <td colspan="3"><b>Subtotal</b></td>
    <td>$<?php echo get_subtotal(); ?></td>
</tr>
<tr>
    <td colspan="4" class="right">
        <input type="submit" value="Update Cart">
    </td>
</tr>
</table>
<p>Click "Update Cart" to update quantities in your
    cart. Enter a quantity of 0 to remove an item.
</p>
</form>
<?php endif; ?>
<p><a href=".?action=show_add_item">Add Item</a></p>
<p><a href=".?action=empty_cart">Empty Cart</a></p>
</main>
</body>
</html>
```

图 12-13 购物车应用程序的 cart_view.php 文件（第 1 部分，共 2 部分）

图 12-13 — 购物车应用程序的 cart_view.php 文件（第 2 部分，共 2 部分）

在 foreach 循环生成的商品行之后，表格在其中一行显示购物车小计，在另一行显示提交按钮。此外，它还显示说明，介绍如何更新购物车中的商品以及如何从购物车中移除商品。

在页面末尾，Add Item（添加商品）链接可让用户返回 Add Item（添加商品）页面。为此，它会向控制器发送一个 `show_add_item` 动作。此外，Empty Cart（清空购物车）链接可让用户移除购物车中的所有商品。为此，它会向控制器发送一个 `empty_cart` 动作。

如果你愿意，可以使用按钮来代替 Add Item（添加商品）、View Cart（查看购物车）和 Empty Cart（清空购物车）链接。要做到这一点，你可以为每个按钮编写一个表单，而不是编写链接。然后，你可以为 action 参数加入一个隐藏字段，并使用 GET 或 POST 方法提交表单。不过，这两种传递 action 的方式都是可接受的，且各有优缺点。

### 练习 12-1 修改购物车应用程序

在本练习中，你可以修改并增强购物车应用程序。

### 打开并测试应用程序

- 1. 运行存储在 ex_starts/ch12_ex1 目录中的应用程序。
- 2. 通过向购物车添加多个商品来测试该应用程序。然后，退出浏览器，重新启动它并查看购物车。由于此应用程序使用持久会话 Cookie，因此购物车应显示之前存在其中的任何商品。
- 3. 打开此应用程序的 index.php 文件并查看代码。请注意，该代码将会话的 Cookie 配置为持续 2 周。

### 使用会话 Cookie

- 4. 修改配置会话 Cookie 的代码，使会话使用会话 Cookie。
- 5. 测试此更改，确保其正常工作。你应该能够通过退出浏览器来移除购物车中的所有商品。（退出浏览器时，不要保存任何打开的标签页。否则，浏览器可能会记住该会话的 Cookie，商品将不会从购物车中移除。）

### 使用持续 3 年的持久 Cookie

- 6. 修改配置会话 Cookie 的代码，使会话持续 3 年。
- 7. 添加代码，在应用程序的两个页面中显示会话 ID。
- 8. 测试这些更改。即使你退出并重新启动浏览器，会话 ID 也应保持不变。
- 9. 在购物车页面添加一个显示为“End Session and Delete Cookie（结束会话并删除 Cookie）”的链接。然后，添加处理此链接的代码：清除内存中的所有会话数据、清理会话 ID，并删除该会话的 Cookie。
- 10. 测试此更改。当你单击“Empty Cart”（清空购物车）链接时，商品应从购物车中移除，但会话 ID 应保持不变。当你单击“End Session”（结束会话）链接时，商品应从购物车中移除，并且会话 ID 应被清除。然后，如果你向购物车添加一件商品，购物车页面应显示一个新的会话 ID。

## 13 如何创建和使用函数

在第 5 章中，你学习了如何编写简单的函数，并且在整个第 2 部分中一直在使用它们。现在，本章将复习使用函数的基本技能，并介绍一些使用函数的额外技能。

- **使用函数的基本技能** ................................ 382
  - 如何创建和调用函数 ........................................ 382
  - 如何按值和按引用传递参数 ...................... 384
  - 变量作用域的工作原理 .................................................. 386
  - 如何为参数提供默认值 .......................... 388
  - 如何使用可变长度的参数列表 ............................. 390
- **如何创建和使用函数库** ......................... 392
  - 函数库 ........................................................ 392
  - 如何设置 include 路径 ................................................ 394
  - 函数作用域的工作原理 .................................................... 394
  - 如何创建和使用命名空间 ........................................ 396
- **使用函数的高级技能** .......................... 398
  - 如何使用变量函数和回调 .................... 398
  - 如何使用匿名函数 ................................... 400
  - 如何使用闭包 .................................................... 402
- **购物车应用程序** ............................................ 404
  - 用户界面 ............................................................... 404
  - 模型 .............................................................................. 406
  - 控制器 .......................................................................... 408
  - 视图 .................................................................................. 408
- **小结** ........................................................................... 412

