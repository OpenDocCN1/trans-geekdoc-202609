
# 创建 checkout.php

此脚本 `checkout.php` 代表客户在电子商务流程中将看到的最后一步。由于本书跳过了此脚本之前的步骤，因此需要对流程进行一些调整。

## 创建 checkout.php 的步骤

**1.** 在文本编辑器或 IDE 中创建一个新的 PHP 文档，命名为 `checkout.php`（**脚本 19.11**）：

```php
<?php # Script 19.11 - checkout.php

$page_title = 'Order Confirmation';

include ('includes/header.html');
```

**2.** 创建两个临时变量：

```php
$cid = 1;
$total = 178.93;
```

为了将订单录入数据库，此页面需要两项额外信息：客户的识别号（即 `customers` 表中的 `customer_id`）和订单总额。第一项值推测会在客户登录时确定（存储在会话中）。第二项值也可能存储在会话中（计入税费和运费后），或者由计费流程传递给此页面。但由于本章编写的脚本无法直接获取这两个值（已跳过相关步骤），我们创建这两个变量来模拟数据。

**3.** 包含数据库连接并关闭 MySQL 的自动提交模式：

```php
require ('../mysqli_connect.php');
mysqli_autocommit($dbc, FALSE);
```

函数 `mysqli_autocommit()` 可开启或关闭 MySQL 的 `autocommit` 特性。由于将使用**事务**来确保整个订单正确录入，因此应首先禁用自动提交行为。如果对事务有疑问，请参阅**第 7 章**或 MySQL 手册。

**4.** 向 `orders` 表添加订单：

```php
$q = "INSERT INTO orders (customer_id, total) VALUES
($cid, $total)";
$r = mysqli_query($dbc, $q);
if (mysqli_affected_rows($dbc) == 1) {
```

此查询非常简单，仅将客户 ID 号和订单总额录入 `orders` 表。该表中的 `order_date` 字段将自动设置为当前日期和时间，因为它是 `TIMESTAMP` 列。

**5.** 获取订单 ID：

```php
$oid = mysqli_insert_id($dbc);
```

`orders` 表中的 `order_id` 值用于在 `order_contents` 表中关联两者。

**6.** 准备将订单内容插入数据库的查询：

```php
$q = "INSERT INTO order_contents (order_id, print_id, quantity, price) VALUES (?, ?, ?, ?)";
$stmt = mysqli_prepare($dbc, $q);
mysqli_stmt_bind_param($stmt, 'iiid', $oid, $pid, $qty, $price);
```

该查询向 `order_contents` 表插入四个值，每个购买的印刷品对应一条记录。查询使用占位符定义并准备执行。函数 `mysqli_stmt_bind_param()` 将四个变量绑定到占位符，其类型依次为：整数、整数、整数、双精度（即浮点数）。

**7.** 遍历购物车，将每个印刷品插入数据库：

```php
$affected = 0;
foreach ($_SESSION['cart'] as $pid => $item) {
  $qty = $item['quantity'];
  $price = $item['price'];
  mysqli_stmt_execute($stmt);
  $affected += mysqli_stmt_affected_rows($stmt);
}
mysqli_stmt_close($stmt);
```

通过循环遍历购物车（同 `view_cart.php`），脚本可逐个访问每个项目。具体流程：查询已**预处理**——发送至 MySQL 并解析，变量已绑定到占位符。循环内，两个新变量从会话获取值。随后调用 `mysqli_stmt_execute()` 执行预处理语句，使用当前变量值。`$oid` 在迭代中不变，但 `$pid`、`$qty` 和 `$price` 会变化。

为确认所有查询成功，需跟踪受影响的行数。变量 `$affected` 在循环外初始化为 0。循环内，每次执行预处理语句后，将受影响行数累加到该变量。

**8.** 报告事务成功与否：

```php
if ($affected == count($_SESSION['cart'])) {
  mysqli_commit($dbc);
  unset($_SESSION['cart']);
  echo '<p>Thank you for your order. You will be notified when the items ship.</p>';
```

条件判断插入 `order_contents` 表的记录数是否等于购物车中的商品数。简而言之：每个产品是否都已插入？若是，事务完成并提交。接着清空购物车并感谢用户。逻辑上此处还应发送确认邮件给客户。

**9.** 处理 MySQL 问题：

```php
  } else {
    mysqli_rollback($dbc);
    echo '<p>Your order could not be processed due to a system error. You will be contacted in order to have the problem fixed. We apologize for the inconvenience.</p>';
  }
} else {
  mysqli_rollback($dbc);
  echo '<p>Your order could not be processed due to a system error. You will be contacted in order to have the problem fixed. We apologize for the inconvenience.</p>';
}
```

第一个 `else` 子句在 `order_contents` 表插入记录数不正确时触发。第二个 `else` 子句在最初的 `orders` 表查询失败时触发。无论哪种情况，都应撤销整个事务，因此调用 `mysqli_rollback()`。

若此时发生问题，情况相当严重，因为客户已被扣款但订单未入库。这本不该发生，但以防万一，应将所有数据写入文本文件和/或发送邮件给网站管理员，或采取其他措施记录该订单。否则，你将面对非常愤怒的客户。

**10.** 完成页面：

```php
mysqli_close($dbc);
include ('includes/footer.html');
?>
```

**11.** 将文件保存为 `checkout.php`，放入 Web 目录，并在浏览器中测试。

![Image](graphics/circle-a.jpg)

![Image](graphics/19_figure_36_a.jpg)

![Image](graphics/circle-a.jpg) 客户订单现已完成，所有数据已录入数据库。

可通过点击 `view_cart.php` 中的链接访问此页面。

**12.** 通过其他界面查看数据库，确认订单已正确存储。

![Image](graphics/circle-b.jpg)

![Image](graphics/19_figure_37_b.jpg)

![Image](graphics/circle-b.jpg) 使用 mysql 客户端查看的 MySQL 数据库中的订单。

---

> **Tip**
