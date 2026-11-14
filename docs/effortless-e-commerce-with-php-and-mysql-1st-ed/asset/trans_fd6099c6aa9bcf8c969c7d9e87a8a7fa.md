

因此，完整的存储过程如下：

```
DELIMITER $$
CREATE PROCEDURE add_order (cid INT, uid CHAR(32), ship DECIMAL(5,2),
 cc MEDIUMINT, OUT total DECIMAL(7,2), OUT oid INT)
BEGIN
 DECLARE subtotal DECIMAL(7,2);
 INSERT INTO orders (customer_id, shipping, credit_card_number,
 order_date) VALUES (cid, ship, cc, NOW());
 SELECT LAST_INSERT_ID() INTO oid;
 INSERT INTO order_contents (order_id, product_type, product_id,
 quantity, price_per) SELECT oid, c.product_type, c.product_id,
 c.quantity, IFNULL(sales.price, c.price) FROM carts AS c INNER JOIN
 non_coffee_products AS ncp ON c.product_id=ncp.id LEFT OUTER JOIN
 sales ON (sales.product_id=ncp.id AND sales.product_type='other'
 AND ((NOW()) BETWEEN sales.start_date AND sales.end_date)
 OR (NOW() > sales.start_date AND sales.end_date IS NULL))) WHERE
 c.product_type="other" AND c.user_session_id=uid UNION SELECT
 oid, c.product_type, c.product_id, c.quantity, IFNULL(sales.price,
 c.price) FROM carts AS c INNER JOIN specific_coffees AS sc ON
 c.product_id=sc.id LEFT OUTER JOIN sales ON (sales.product_id=sc.id
 AND sales.product_type='coffee' AND ((NOW() BETWEEN
 sales.start_date AND sales.end_date) OR (NOW() > sales.start_date
 AND sales.end_date IS NULL))) WHERE c.product_type="coffee" AND
 c.user_session_id=uid;
 SELECT SUM(quantity*price_per) INTO subtotal FROM order_contents
 WHERE order_id=oid;
 UPDATE orders SET total = (subtotal + ship) WHERE id=oid;
 SELECT (subtotal + ship) INTO total;
END$$
DELIMITER ;
```

该存储过程将客户 ID、客户的购物车 ID、运费金额以及信用卡号码（最后四位数字）作为入站参数。有两个出站参数：**total** 和 **oid**。在 **BEGIN** 块中，定义了一个名为 **subtotal** 的局部变量。接着，记录被添加到 **orders** 表，并选择刚创建的 ID 并分配给 **oid**。之后，**order_contents** 表被填充，使用 INSERT...SELECT UNION SELECT 查询。

> 请记住，存储过程中的变量不像 PHP 变量那样使用美元符号。

最后三行计算订单的小计，更新 **orders** 表中的 **total** 列，并将总订单值分配给 **total** 变量。

## 再谈存储过程

这种适度复杂的 **add_order()** 存储过程展示了使用存储过程所能带来的安全性和性能优势。该过程只需要四个参数——客户 ID、客户的购物车会话 ID、运费总额以及信用卡表示形式——就能用极少的信息完成大量工作。如果运费是由数据库存储函数计算，并且省略信用卡号码（无论如何它们都会存储在 **transactions** 表中），该过程甚至可以缩减到只需两个入站参数。从性能角度来看，PHP 需要发送到数据库的信息非常少，更重要的是，PHP 脚本只需执行一次查询——即存储过程调用本身。由于查询执行是 PHP 脚本最费力的操作之一，限制那些

可以带来巨大的性能提升。（尽管因此将负担转移到了数据库服务器。）从安全性角度来看，许多关键信息——例如产品的售价——永远不会离开数据库，因此更难被篡改。而且没有 PHP 脚本直接访问任何数据库表，增加了一层混淆。我应该补充一点，你在逻辑上可以在此存储过程中使用事务，而存储过程确实支持事务。使用事务，每个查询都必须正常工作，否则整个过程将被回滚。这种方法可以防止不完整的订单被记录。不过，我选择不使用事务，因为它们会进一步复杂化一个已经复杂的过程。

## 获取运输信息

一旦客户购物完毕并准备购买商品，他或她会点击购物车页面上的一个按钮，该按钮将通过 HTTPS 跳转到 **checkout.php**。此页面需要：

- 1. 获取客户的送货信息。
- 2. 验证提供的数据。
- 3. 如果有效，存储数据并将客户送至结账流程的下一步。
- 4. 如果无效，带错误重新显示表单。

就表单的显示和验证而言，**checkout.php** 的行为类似于第 4 章中的 **register.php**。但有一些额外的注意事项，使这个脚本比那个更复杂。让我们先定义 PHP 脚本，然后是它使用的两个视图文件。

## 创建 PHP 脚本

PHP 脚本应至少被访问两次：最初作为 GET 请求，此时应加载表单；以及作为 POST 请求，即提交表单时。后者需要大约 100 行验证代码，这是脚本的主要部分。

与网站的购物区域不同，结账过程将使用 PHP 会话。这是必要的，因为多个脚本都需要访问某些相同的信息。默认情况下，PHP 会将会话标识符存储在 cookie 中。你可能没有意识到这一点，但在 cookie 方面，http://www.example.com 和 https://www.example.com 是独立的领域，这意味着通过 HTTP 发送的 cookie 仅可用于通过 HTTP 访问的页面（HTTPS 亦然）。我现在提到这一点，因为结账过程使用的会话在网站的购物端不可用，购物端使用的 cookie 在结账过程中也不可用。

> **提示**

第 7 章“第二站点：结构与设计”中的 .htaccess 修改确保 checkout.php 仅可通过 HTTPS 访问。

- 1. 在文本编辑器或 IDE 中创建一个新的 PHP 脚本，命名为 checkout.php 并存储在 Web 根目录中。

> **提示**

当用户返回网站购物端时，即使在结账后，愿望清单和购物车 cookie 仍然可用。

- 2. 包含配置文件：

```php
<?php
require('./includes/config.inc.php');
```

- 3. 检查用户的购物车 ID，可在 URL 中获得：

```php
if ($_SERVER['REQUEST_METHOD'] == 'GET') {
    if (isset($_GET['session'])) {
        $uid = $_GET['session'];
    }
}
```

为了访问客户的购物车，此脚本需要用户的购物车会话 ID，该 ID 存储在用户浏览器的 cookie 中。但是，该 cookie 是通过 HTTP 发送的，这意味着它对 checkout.php 不可用，因为此脚本是通过 HTTPS 访问的。补救办法是在用户单击 cart.php 上的结账按钮时将 cookie 值传递给此脚本。此脚本首先确认 URL 中传递了会话值。如果是，则将其分配给 $uid 变量以供稍后使用。

- 4. 将购物车 ID 用作会话 ID，并启动会话：

```php
session_id($uid);
session_start();
```

网站购物部分故意不使用会话（为了使客户的购物车和愿望清单持久化），但结账过程会使用。为保持连续性，并且因为结账过程需要购物车 ID，用户现有的购物车 ID 将用作会话 ID。这可以通过在调用 **session_start()** 之前向 **session_id()** 函数提供会话 ID 值来实现。最终结果是用户浏览器中会有两个 cookie：通过 HTTP 发送的 **SESSION** 和通过 HTTPS 发送的 **PHP_SESSION_ID**。两者值相同。

- **5.** 如果 URL 中没有会话值（针对 GET 请求），则重定向用户：

```php
} else {
  $location = 'http://' . BASE_URL . 'cart.php';
  header("Location: $location");
  exit();
}
```

如果没有可购买的东西，结账就没有意义。而且没有购物车会话 ID，就没有可购买的东西！在这种情况下，客户会通过 HTTP 被重定向回 cart.php。只有当购物车不为空时，该页面才会显示结账按钮。

- **6.** 如果请求方法不是 GET，则启动会话并检索会话 ID：

```php
} else { // POST request.
  session_start();
  $uid = session_id();
}
```

当客户提交表单进行验证时，将应用此 else 子句。在这种情况下，需要启动会话。会话 ID 在首次访问此脚本时已经设置，因此可以检索该值（通过不带参数调用 session_id()）以供此脚本稍后使用。

- **7.** 包含数据库连接并创建用于验证错误的数组：

```php
require (MYSQL);
$shipping_errors = array();
```

- **8.** 如果提交了表单，验证名和姓：

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
  if (preg_match ('/^[A-Z \'.-]{2,20}$/i', $_POST['first_name'])) {
    $fn = addslashes($_POST['first_name']);
  } else {
    $shipping_errors['first_name'] = 'Please enter your first name!';
  }
}
```

