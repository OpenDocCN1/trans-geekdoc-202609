
![](img/245156cc770929860a3ede93c01f9981_399_2.png)

在所有这些功能生效之前，你需要获取一个证书。正如我提到的，VeriSign 是最经常使用的认证机构。如果你将 VeriSign 证书配合下面描述的 PaypalPro（VeriSign 的一项服务）功能使用，你可能会获得很优惠的价格。Thwaite 曾是第二大认证机构，现在由 VeriSign 所有。该地区的其他选项可以在以下 URL 找到：http://dmoz.org/Computers/Public_Key_Infrastructure/PKIX/Tools_and_Services/Third_Party_Authorities/

# 配置信用卡授权

当 Apache 配置 SSL 后，你的网站将能够与浏览器安全通信。如果 URL 以 https:// 开头，浏览器会在端口 443 寻找证书。从这里来说，如果你正在运行 sofamegastore.com，银行需要确保对 loveseat 的信用卡授权请求确实来自 Sofa Megastore，而不是某个冒充 Sofa Megastore 的人。这需要第三方的参与。

你发送和接收的加密消息将带有某种签名，但该签名必须经过验证。出于这个原因，希望在网络上进行通信的机构利用分发证书的机构来验证消息的发送者。因此，你需要去这些机构之一获取你的公钥和私钥是合乎逻辑的。

![](img/245156cc770929860a3ede93c01f9981_398_0.png)

在安全证书领域最知名的机构可能是 Verisign。你可以在此网站查看他们的产品：http://www.verisign.com/products/site/ss/Index.html。

## 安全协议

HTTP 本质上是开放且易被窃听的。在互联网路由器之间传输的数据包充满了等待被嗅探和读取的消息。通常情况下，你可以轻松读取通过 HTTP 发送的数据是一件好事。它让信息的传输和渲染变得非常简单。然而，在需要安全性的情况下，HTTP 的效果并不好。

例如，如果你向某个网站提供信用卡信息——比如你建立的电子商务网站——你希望确保这些信息是不可读的。为了实现这一点，你需要使用安全套接层，即 SSL。SSL 是一种额外的协议，通过该协议，你网站的密钥和证书将传输到浏览器或其他服务器。通过 SSL，你的浏览器将能够验证你网站的证书，以便它知道你就是你所称的身份。网站之间也将能够相互验证。

# 第四部分：不简单的应用

首先，我需要对面向对象的方法的优势再次做说明。当你阅读第 10 章时（你确实读了第 10 章，对吧？），你看到了面向对象编程实践中的某些原则。具体来说，你应该注意继承是如何使用的。当一个类继承父类的属性和方法时，它就可以访问父类的所有方法和属性。

在这个应用中，你正在扩展在目录中使用的代码，因此该应用程序创建扩展目录中所用类的类是完全合理的。在继续之前，请务确保你已经熟悉第 10 章中的目录类。

## 会话函数

如果你访问 PHP 手册中的会话页面（http://www.php.net/manual/ref.session.php），你会发现有16个不同的函数。根据你的需求，你可能需要使用其中大多数函数，但在很多情况下，只使用一个函数：`session_register()` 即可。我们将对此进行解释。

![](img/245156cc770929860a3ede93c01f9981_402_0.png)

关于会话有许多函数和设置我们在这里没有涵盖。请务必随时检查手册。

> 你需要做的第一件事是让 PHP知道你想要启动会话。你可以通过使用 `session_start()` 来显式地做到这一点。你需要让 PHP知道你想要存储哪些变量。你可以通过 `session_register("variable_name")` 做到。以以下页面为例：

![](img/245156cc770929860a3ede93c01f9981_402_1.png)

`session_start()` 和 `session_register()` 函数应该位于 PHP 页面的最顶端。这些函数发送 cookie，cookie 是 HTTP 头部的一种类型。如果你在向浏览器发送文本后尝试发送任何类型的头部，将得到错误。

```php
<?php
session_start();
session_register("mystring");

$mystring = "testing for a string";
?>
```

# 第 14 章：购物车

当第一次访问此页面时，它将启动会话，并根据配置发送 cookie 或将会话 ID 附加到相对链接中。`session_register` 命令告诉 PHP 在会话文件中查找变量 `$mystring`。如果它存在，它将作为全局变量可用，或者你可以通过 `HTTP_SESSION_VARS` 访问它。在页面处理后，注册变量的最新值将写入会话文件。因此，如果你有另一个包含以下代码的页面：

```php
<?php
session_start();
session_register("mystring");

echo $mystring;
?>
```

它将打印出 "testing for a string"。

事实证明是，`session_start()` 函数并不是真的必要的；如果你在代码中有一个 `session_register()`，PHP 足够智能可以为你启动会话。

请注意，尽管在前面的代码中变量是一个简单的字符串，但它绝不仅限于字符串。简单数组、复杂数组和对象都是有效的会话变量。

这里是你可能发现有用的其他会话函数。

## `SESSION_DESTROY()`

此函数会销毁会话以及与其关联的所有变量。

## `SESSION_UNREGISTER()`

此函数会擦除会话文件中变量的值。

### `SESSION_SET_SAVE_HANDLER()`

这个有趣的函数允许你设置自己的方法来存储、检索和写入你的会话处理器。

```
void session_set_save_handler (string open, string close, string read, string write, string destroy, string gc)
```

在大部分情况下，PHP 中基于文件的会话管理是可以的。然而，在某些情况下它可能不适合你。如果你恰好在一个集群环境中工作（多台机器提供同一个站点），写入本地文件系统将不起作用。同样，你启用了 SSL 的 Apache 安装可能位于不同的主服务器上。

在这种情况下，更好的选择是让所有机器连接到同一个数据库，并让你的数据库（当然是 MySQL）存储会话数据。

## `SESSION_ENCODE()`

为了写入数据库，你可以使用 `session_encode`。

```php
$str = session_encode();
```

## `SESSION_DECODE()`

此函数反转编码。

```php
$data = session_decode($str);
```

### cURL 函数

你可以用 cURL 做很多事情。例如，获取远程响应：

```php
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, "http://example.com/api");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);
```

# 第14章：购物车

通过一些视觉化的表示，可以更轻松地理解继承链。图 14-6 显示了继承链。

![](img/245156cc770929860a3ede93c01f9981_407_0.png)

图 14-6：购物车类继承链

# 第四部分：不简单的应用程序

从该图中可以看出，继承可能比直接的层级结构要复杂一些。在阅读本章节和 CD 上的源码文件时，请随手参考图。

## 类

我们将讨论的第一批类位于图 14-6 的右侧。

这些类的方法看起来与第10章中的 Category、Product 以及其他类的方法非常相似。这些方法之所以有效，是因为在处理产品时存在自然的层级关系：类别包含产品，产品包含样式，样式包含子样式。对于购物车，用户信息也存在层级关系：一个用户可以有多个地址，多个订单可以发送到同一个地址，多个商品可以属于同一个订单。

鉴于这种相似性，创建模拟第10章类的用户信息类是合理的。当我讲到 User 类时，你就会明白我的意思。

让我们从类的顶端开始，查看 Base 类的更改。

# BASE 类

PHP 类不支持多重继承。如果支持，我们可以创建一个名为 `CartBase` 的类作为 `Base` 的扩展，然后让 `Catalog` 类同时继承 `Base` 和 `CartBase`。由于这是可能的，我们从目录中复制了 Base 类的所有方法（`sql_format()`、`set_item_src()`、`set_thumb_src()`、`construct()` 和 `base()`）。所有方法在第10章中都有描述。我们添加了一个单一的方法，用于打印表单。

# METHOD_ORDER_FORM() 这个表单并没有特别之处。它将打印收集放入购物车的商品信息所需的所有数据。

```php
function order_form() {
    $output = start_form("cart.php")
    ."<b>"".$this->item."</b>"
    ."&nbsp;"
    ."$this->price
    ."&nbsp;"
    ."<b>".$this->qty."</b>"
    .text_field("quantity",1,4,4)
    ."&nbsp;"
    .submit_field("order_item", "Order!")
    .hidden_field("category_id",$this->category_id)
    .hidden_field("product_id",$this->product_id)
    .hidden_field("style_id",$this->style_id)
    .hidden_field("substyle_id",$this->substyle_id)
    .hidden_field("price",$this->price)
.end_form());
$output .= "\n";
return $output;
}
```

# USER 类

如所述，该类看起来与目录中的类非常相似。

关于该类的关键信息如下：

- **类名:** `User`

- 继承自 `Base`

- **默认属性:**

    - `$addresses`

方法：

- **`User.`** 类构造函数。接收两个参数：`$parent` 和 `$atts`。调用 `Base()` 方法，将 `$atts` 数组中的每个元素赋值给数组对象属性。

- **`FetchUser.`** 接收一个参数 `$user_id`。为用户表中与 `$user_id` 关联的每一行创建对象属性。

- **`LoadUser.`** 接收一个参数 `$user_id`。首先运行 `FetchUser` 并创建一个数组，其每个元素都是一个包含地址信息的对象。

- **`SaveUser.`** 不接收参数，假设 `$this->user_id` 存在。将根据需要更新状态并创建新的状态。

- **`DeleteUser.`** 不接收参数。

## 第 14 章：购物车

在第 10 章创建数据结构时，你看到了 `LoadCategory()` 方法是如何在数组中实例化对象的。我们没有让 `LoadCategory()` 类直接实例化对象，而是让 `LoadCategory()` 调用另一个名为 `AddProduct()` 的方法来实例化对象。通过将 `AddProduct()` 拆分为独立的方法，我们获得了一些灵活性，这在应用程序中变得非常方便。

当你实例化 `CartCategory` 类时，该子类的 `AddProduct()` 方法会重写（Category）类的 `AddProduct()` 方法。因此，如果你编写如下代码：

```
$c = new CartCategory;
$c->LoadProduct($product_id);
```

你可以确定执行的是 `CartCategory` 中的 `AddProduct()` 方法。

以下是 `CartCategory` 类中 `AddProduct()` 方法的内容。

```php
function AddProduct($parent,$atts)
{
    $this->products[] = new CartProduct($parent,$atts);
```

## 类 CARTPRODUCT

这与 `CartCategory` 类类似，并包含一个更适合购物车的打印产品的方法。

- **类名：** `CartProduct`

  继承 `Product`

**默认属性：**

- *无*

方法：

- **`CartProduct.`** 构造函数。接受两个参数：`$parent` 和 `$atts`。调用 `Base()` 方法，将 `$atts` 数组中的每个元素赋值给对象属性。

- **`AddStyle.`** 此方法重写了父类（Product）中的 `AddStyle()` 方法。它创建了一个名为 `$styles` 的数组，其每个成员都是通过调用 `CartStyles()` 类形成的对象。

- **`PrintProduct.`** 不接受任何属性。重写了父类（Product）中的 `PrintProduct()` 方法。

## 类 CARTSTYLE

这与 `CartStyle` 类类似，并包含一个更适合购物车的打印样式的方法。

**类名：** `CartStyle`

继承 `Style`

**默认属性：**

方法：

- **`CartStyle.`** 类构造函数。接受两个参数：`$parent` 和 `$atts`。调用 `Base()` 方法，将 `$atts` 数组中的每个元素赋值给对象属性。

- **`AddSubStyle.`** 此方法重写了父类（Style）中的 `AddStyle()` 方法。它创建了一个名为 `$substyles` 的数组，其每个成员都是通过调用 `CartSubStyle()` 类形成的对象。

- **`PrintStyleRow.`** 不接受任何属性。重写了父类（Style）中的 `PrintStyleRow()` 方法。

## 类 CARTUBSTYLE

这与 `CartSubStyle` 类类似，并包含一个更适合购物车的打印子样式的方法。

**类名：** `CartSubStyle`

继承 `SubStyle`

**默认属性：**

方法：

- **`CartSubStyle.`** 类构造函数。接受两个参数：`$parent` 和 `$atts`。调用 `Base()` 方法，将 `$atts` 数组中的每个元素赋值给对象属性。

- **`AddSubStyle.`** 此方法重写了父类（Style）中的 `AddStyle()` 方法。它创建了一个名为 `$substyles` 的数组，其每个成员都是通过调用 `CartSubStyle()` 类形成的对象。

- **`PrintSubStyle.`** 接受三个属性：`$style_price`、`$style_dsc` 和 `$product_dsc`。重写了父类（Style）中的 `PrintSubStyle()` 方法。

## 脚本

这些是由 URL 调用的页面以及包含文件。再次，你可能注意到其中并没有涉及太多内容。几乎所有的工作都在类中完成了。

### DISPLAY.PHP

此将打印分类列表或某个特定的产品。

```php
include 'header.php';

if (empty($category_id)) {
    header("Location: index.php");
    exit;
}

$page_title = anchor_tag("index.php", "Bag of Stuff");

$c = new CartCategory();

if (empty($product_id)) {
    $c->LoadCategory($category_id);
    $page_title .= ": " . $c->category;
    include "start_page.php";
    $c->PrintCategory();
} else {
    $p = new CartProduct();
    $p->LoadProduct($product_id);
    $p->LoadStyles();
    $c->FetchCategory($p->category_id);
    $page_title .= ": " . anchor_tag("display.php?category_id=$c->category_id", 
        $c->category, ": $p->product");
}
```

## 第四部分：并不简单的应用程序

```php
include "start_page.php";

$p->PrintProduct();
}
```

```php
include "end_page.php";
```

这已经没有更简单的了：如果此页面要显示一个分类（而不是产品），则会加载并打印该分类。如果合适，产品也会发生相同的情况。如果你还记得第 10 章的 `display php` 页面，你可能会注意到唯一的区别是这里实例化的项目是由此应用程序中引入的新类创建的。这让我们能够使用新的打印方法，这些方法是专为此应用程序设计的。

## CART.PHP

这是创建我们购物车的页面。

```php
include "header.php";
session_register("cart");
session_register("last_item");
```

```php
$page_title = anchor_tag("index.php", "Bag of Stuff");
购物车:
```
