
# PHP 中的表单验证与类型转换

到目前为止，本书中使用的表单验证大多相当简单，通常只是检查变量是否有任何值。在许多情况下，这确实是你能做的最好的验证。例如，对于什么是有效的街道地址，或者用户可能在评论字段中输入什么内容，并不存在完美的测试标准。尽管如此，你将要处理的大部分数据都可以用更严格的方式进行验证。在下一章中，正则表达式这一复杂概念将演示如何做到这一点。但在这里，我将介绍一些更易上手的方法，通过类型来验证某些数据。

---

## 两种验证方法

安全性很大程度上建立在验证之上：如果数据来自服务器之外——来自 HTML 表单、URL、Cookie——就不能信任它。（更高级别的安全性还会验证来自*脚本*之外的任何数据，包括会话和数据库。）验证主要有两种类型：*白名单* 和 *黑名单*。

在计算器示例中，我们知道所有值必须为正数，必须都是数字，且数量必须为整数（另外两个数字可以是整数或浮点数，这无关紧要）。类型转换强制输入为数字，检查则确认它们为正数。此时，假设输入是有效的。这是白名单方法：这些值是好的；其他任何值都是坏的。

防止垃圾信息的示例使用了黑名单方法。该脚本确切知道哪些字符是坏的，并使包含这些字符的输入无效。所有其他输入都被视为好。

许多安全专家倾向于使用白名单方法，但它并不总是适用。每个示例将决定哪种方法效果最好，但重要的是要使用其中一种。不要在没有任何验证的情况下就假设数据是安全的。

---

## 类型验证函数

PHP 支持多种数据类型：字符串、数字（整数和浮点数）、数组等。针对每种类型，都有一个特定的函数来检查变量是否属于该类型（表 13.2）。你在前几章中已经看到了 `is_numeric()` 函数的实际应用，而 `is_array()` 非常适合确认变量可用于 `foreach` 循环。如果提交的变量属于特定类型，每个函数返回 `TRUE`，否则返回 `FALSE`。

**表 13.2. 类型验证函数**

![Image](graphics/13tab02.jpg)

在 PHP 中，甚至可以在变量被赋值后改变其类型。这样做称为 *类型转换*，通过在变量名前加上目标类型（用括号括起来）来实现：

```php
$var = 20.2;
echo (int) $var; // 20
```

根据原始类型和目标类型的不同，PHP 会相应地转换变量的值：

```php
$var = 20;
echo (float) $var; // 20.0
```

对于数值，转换很直接，但对于其他变量类型，则适用更复杂的规则：

```php
$var = 'trout';
echo (int) $var; // 0
```

在大多数情况下，你不需要将变量从一种类型强制转换为另一种类型，因为 PHP 通常会在需要时自动进行转换。但在 Web 应用程序中，强制转换变量类型可以是一个很好的安全措施。为了展示如何使用这一概念，让我们创建一个计算器脚本，用于确定商品的总购买价格 ![Image](graphics/circle-a.jpg)。

![Image](graphics/13_figure_07_a.jpg)

![Image](graphics/circle-a.jpg) HTML 表单接受三个输入：数量、价格和税率。

### 使用类型转换

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `calculator.php`（脚本 13.2）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <title>Widget Cost Calculator </title>
</head>
<body>
<?php # Script 13.2 - calculator.php
```

**脚本 13.2.** 通过对变量进行*类型转换*，该脚本更明确地验证数据是否为正确格式。

---

```php
1  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
       1.0 Transitional//EN" "http://www.w3.org/
       TR/xhtml1/DTD/xhtml1-transitional.dtd">
2  <html xmlns="http://www.w3.org/1999/
       xhtml" xml:lang="en" lang="en">
3  <head>
4      <meta http-equiv="Content-Type"
         content="text/html; charset=utf-8" />
5      <title>Widget Cost Calculator</title>
6  </head>
7  <body>
8  <?php # Script 13.2 - calculator.php
9  // This script calculates an order total
       based upon three form values.
10
11  // Check if the form has been submitted:
12  if ($_SERVER['REQUEST_METHOD'] == 'POST') {
13
14      // Cast all the variables to a
         specific type:
15      $quantity = (int) $_POST['quantity'];
16      $price = (float) $_POST['price'];
17      $tax = (float) $_POST['tax'];
18
19      // All variables should be positive!
20      if ( ($quantity > 0) && ($price >
         0) && ($tax > 0) ) {
21
22          // Calculate the total:
23          $total = $quantity * $price;
24          $total += $total * ($tax/100);
25
26          // Print the result:
27          echo '<p>The total cost of purchasing
              ' . $quantity . ' widget(s) at $' .
              number_format ($price, 2) . ' each,
              plus tax, is $' . number_format
              ($total, 2) . '.</p>';
28
29      } else { // Invalid submitted values.
30          echo '<p style="font-weight: bold;
              color: #C00">Please enter a valid
              quantity, price, and tax rate.</p>';
31      }
32
33  } // End of main isset() IF.
34
35  // Leave the PHP section and create the
       HTML form.
36  ?>
37  <h2>Widget Cost Calculator</h2>
38  <form action="calculator.php"
         method="post">
39      <p>Quantity: <input type="text"
              name="quantity" size="5" maxlength="10"
              value="<?php if (isset($quantity)) echo
              $quantity; ?>" /></p>
40      <p>Price: <input type="text"
              name="price" size="5" maxlength="10"
              value="<?php if (isset($price)) echo
              $price; ?>" /></p>
41      <p>Tax (%): <input type="text"
              name="tax" size="5" maxlength="10"
              value="<?php if (isset($tax)) echo
              $tax; ?>" /></p>
42      <p><input type="submit" name="submit"
              value="Calculate!" /></p>
43  </form>
44  </body>
45  </html>
```

---

**2.** 检查表单是否已提交：

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
```

与许多前面的示例一样，这个脚本既会显示 HTML 表单，也会处理其提交。

**3.** 将所有变量转换为特定类型：

```php
$quantity = (int) $_POST['quantity'];
$price = (float) $_POST['price'];
$tax = (float) $_POST['tax'];
```

表单本身有三个文本框 ![Image](graphics/graycircle-a.jpg)，实际上可以输入任何内容（HTML 4 或 XHTML 1.1 中表单没有 number 类型的输入）。但数量必须是整数，而价格和税率可以作为浮点数（即可以包含小数点）。为了强制这些约束，将每个变量转换为特定类型。

**4.** 检查变量是否具有合适的值：

```php
if ( ($quantity > 0) && ($price > 0) && ($tax > 0) ) {
```

为了使计算器正常工作，这三个变量必须是特定类型（见步骤 3）。更重要的是，它们必须都是正数。在执行计算之前，此条件检查这一点。注意，根据类型转换的规则，如果提交的值不是数字，它们将被转换为 `0`，因此无法通过此条件判断。

**5.** 计算并打印结果：

```php
$total = $quantity * $price;
$total += $total * ($tax/100);
```
