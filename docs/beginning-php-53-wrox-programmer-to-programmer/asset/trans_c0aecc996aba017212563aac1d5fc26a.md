

# 第三部分：PHP 实践

`removeItem()` 功能与 `addItem()` 相反：在验证 `productID` 字段后，它从用户的购物车中移除相应的产品，并刷新浏览器。

```
function removeItem() {
    global $products;
    if (isset($_GET['productID']) && $_GET['productID'] >= 1 && $_GET['productID'] < 3) {
        $productId = $_GET['productID'];
    }

    if (isset($_SESSION['cart'][$productId])) {
        unset($_SESSION['cart'][$productId]);
    }
}

session_write_close();
header("Location: shopping_cart.php");
```

最后，`displayCart()` 显示用户的购物车以及可用产品列表。在显示 XHTML 页面头部后，该函数会遍历购物车中的每项物品，显示产品名称，并通过一个链接允许用户从其购物车中移除该产品。它还会计算购物车中所有产品的总价，然后在下方显示总额：

```php
<ol>
<?php
$totalPrice = 0;
foreach ($_SESSION['cart'] as $product) {
    $totalPrice += $product->getPrice();
}

<dt><?php echo $product->getName(); ?></dt>
<dd><td><?php echo number_format($product->getPrice(), 2 ) ?></td>
<td><a href="shopping_cart.php?action=removeItem&productID=<?php echo $product->getId(); ?>">移除</a></</td></dd>
<?php }
<dt>购物车总计:</dt>
<dd><td>$<?php echo number_format($totalPrice, 2 ) ?></td></dd>
</ol>
```

随后，`displayCart()` 函数列出可用产品及其价格。每个产品都有一个对应的“添加项目”列表，购物者可以将产品添加到购物车中：

```php
<ol>
<?php
foreach ($products as $product) {
<dt><?php echo $product->getName(); ?></dt>
<dd><td>$<?php echo number_format($product->getPrice(), 2 ) ?></td>
<td><a href="shopping_cart.php?action=addItem&productID=<?php echo $product->getId(); ?>">添加项目</a></</td></dd>
<?php }
</ol>
```

288

# 第 10 章：使用查询字符串保留状态

在这个简单的示例中，购物者只能向购物车添加每种产品一个。当然，在现实情况下，你可能会允许购物者添加多个同种类型的产品。

# 销毁会话

如之前所述，默认情况下，PHP 会话会在用户退出浏览器时自动删除，因为 `PHPSESSID` cookie 的 `expires` 字段被设置为零。然而，有时你可能想手动销毁会话。例如，如果购物者已经在你的在线商店结算并下单，你可能通过销毁该会话来清空购物车。

要销毁会话，只需调用内置的 `session_destroy()` 函数：

```
session_destroy();
```

但注意，这仅仅是从磁盘上删除了会话数据。在脚本执行结束之前，数据仍然存在 `$_SESSION` 数组中。为了确保所有会话数据都被擦除，你应该初始化 `$_SESSION` 数组：

```php
$_SESSION = array();
session_destroy();
```

尽管如此，会话的痕迹仍以 `PHPSESSID` cookie 的形式存在于用户的浏览器中。当下一个访问者访问你的网站时，PHP 将获取 `PHPSESSID` cookie 并重新创建会话（尽管重新创建的会话不包含任何数据）。为了确保你已从服务器和浏览器中删除了会话，还应该销毁会话代码：

```php
if ( isset($_COOKIE[session_name()]) ) {
    setcookie(session_name(), "*", time()-3600, "*/");
}
```

这段代码使用了另一个 PHP 函数 `session_name()`。该函数简单返回会话名称（默认为 `PHPSESSID`）。

PHP 实际上允许你通过使用 `session_name()` 创建不同的命名会话在同一脚本中处理多个会话。这个主题超出了本书的范围，但你可以在 PHP 手册的“Session Handling”部分找到更多信息：http://www.php.net/session。

# 在查询字符串中传递 Session ID

如你所知，PHP 会话 ID 保存在 cookie 中。但是，如果用户在浏览器中禁用了 cookie 呢？一种明显的方法是在页面上添加一些文本，礼貌地要求用户开启 cookie。另一种替代方案是在网站页面之间的链接内部传递 session ID。

289

# 第三部分：PHP 实践

PHP 通过内置的 `SID` 常量帮助自动化此过程。如果浏览器支持 cookie，则此常量为空；然而，如果会话 cookie 包含来自浏览器的字符串，则 `SID` 包含以下内容：

```
PHPSESSID=b8306b025a762a50f0428fc0efd20a11
```

这意味着你可以使用页面中的链接来包含 session ID（如果可用）：

```php
<?php session_start() ?>
<a href="myscript.php?<?php echo SID;?>">首页</a></a>
```

如果 session ID 成功存储在 cookie 中，代码将输出以下内容：

```php
<a href="myscript.php?<?php echo SID;?>">首页</a></a>
```

然而，如果 PHP 无法创建会话 cookie，代码将输出类似的内容：

```php
<a href="myscript.php?PHPSESSID=5bf28913309ba166b3a3ea8b67ff1c7*">首页</a></a>
```

当用户点击链接查看 `myscript.php` 时，`PHPSESSID` 查询字符串值会被 PHP 引擎自动获取，会话数据将对脚本可用。

> 注意，你必须在尝试访问 SID 之前调用 `session_start()`。

尽管此功能很方便，但最好避免在 URL 中传递 session ID。访问者很容易将一个链接（包含她的 session ID）启用发送给朋友，从而在无意中让朋友访问了她的会话！你可以通过缩短会话 cookie 的寿命（下一节）在某种程度上缓解这一点，但通常最好只使用 cookie。

你也可以通过调用 `session_id()` 函数来获取当前的 session ID。这允许你在执行其他操作的同时，将 session ID 嵌入表单的隐藏字段中，以便会话可以在跨表单提交时传递。

# 更改会话行为

除了更改会话行为外，你还可以编写自定义代码将会话数据存储在服务器上。例如，与其让 PHP 将数据存储在临时文件中，你可能更喜欢将其存储在数据库中。如何实现这一点出了本书的范围，你可以通过阅读 http://www.php.net/manual/en/function.session-set-handler.php 了解更多信息。

如果你有 `php.ini` 文件的权限，可以直接在文件中修改这些指令（详情见附录 B），或者可以使用 `ini_set()` PHP 函数按脚本设置它们：

```php
ini_set("session.cookie_lifetime", 1200); // 将会话超时设置为 20 分钟
```

# 第 10 章：使用查询字符串保留状态

| 指令 | 描述 |
| --- | --- |
| session.cookie_lifetime | cookie 的持续时间（秒）。默认值为零，即在浏览器关闭时 cookie 过期。将其设置为长值（例如 1 年）以创建永久会话来存储用户偏好。或者，为了增加长会话等会话安全性，将其设置为短值（例如 20 分钟），如果用户在两次页面请求之间等待超过 20 分钟，会话将超时。 |
| session.cookie_path | 会话 cookie 的路径字段。默认为 '/'（整个站点）。如果你想将会话限制在该文件夹内的脚本，请将其设置为网站的子目录。 |
| session.cookie_domain | 会话 cookie 的域名字段。默认为 ''（当前服务器）。如果你想让会话对同一域名下的多个主机可用，请更改此项。 |
| session.cookie_httponly | 会话 cookie 的 HttpOnly 字段。默认为 false。如果你想防止 JavaScript 访问会话 cookie，请将其更改为 true。 |
| session.auto_start | 默认为 false。将其更改为 true，PHP 会会在脚本启动时刻自动启动会话，省去你调用 `session_start()`。注意；如果设置为 true，你将无法在会话中存储对象（因为你的类在加载会话数据时尚未定义）。 |

291

