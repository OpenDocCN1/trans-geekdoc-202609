
# 多维数组排序

当函数结束时，它可以向调用它的代码返回一个回复。这个过程被称为返回一个值。要返回一个值，你在函数中使用 `return` 关键字。例如，`return 1` 这一行将值 1 发回调用该函数的代码。

为了供 `sort` 使用，`compare()` 函数必须比较 $x 和 $y。如果 $x 等于 $y，函数必须返回 0；如果 $x 较小，则返回负数；如果 $x 较大，则返回正数。该函数将根据 $x 和 $y 的值返回 0、1 或 -1。

最后一行代码调用了内置函数 `sort()`，并传入你想要排序的数组（$products）和比较函数的名称（`compare()`）。

如果你想让数组按另一种顺序排序，只需编写一个不同的比较函数。要按价格排序，你需要查看数组中的第三列并创建此比较函数：

```php
function compare($x, $y) {
  if ($x[2] == $y[2]) {
    return 0;
  } else if ($x[2] < $y[2]) {
    return -1;
  } else {
    return 1;
  }
}
```

当调用 `usort($products, 'compare')` 时，数组将按价格升序排列。

> 注意
> 你应该运行这些代码片段进行测试，它们不会有输出。这些片段旨在作为你可能编写的大段代码的一部分。

`usort()` 中的 `u` 代表 user（用户），因为此函数需要一个用户定义的比较函数。`sort` 和 `ksort` 的 `usort` 和 `ksort` 版本也需要用户定义的比较函数。

与 `sort()` 类似，当按值对非数值数组进行排序时，应使用 `usort()`。如果你的值是简单的数字或文本，请使用 `sort`。如果你的值是更复杂的对象（如数组），请定义比较函数并使用 `usort()`。

与 `ksort()` 类似，当按键对非数值索引数组进行排序时，应使用 `usort()`。如果你的键是简单的数字或文本，请使用 `ksort`。如果你的键是更复杂的对象（如数组），请定义比较函数并使用 `usort()`。

# 用户反向排序

`sort()`、`asort()` 和 `ksort()` 函数都对应有、函数名中带有 `r` 的反向排序函数。用户定义的排序没有反向变体，但你可以将多维数组按反序排序。因为你提供了比较函数，所以你可以写一个返回相反值的比较函数。要按反序排序，如果 $sx 小于 $sy，该函数需要返回 1；如果 $sx 大于 $sy，则返回 -1。例如：

```php
function reverse_compare($sx, $sy) {
    if ($sx[2] == $sy[2]) {
        return 0;
    } else if ($sx[2] < $sy[2]) {
        return 1;
    } else {
        return -1;
    }
}
```

现在调用 `usort($products, 'reverse_compare')` 将导致数组按价格降序排列。

# 重新排列数组

对于某些应用程序，你可能希望通过排序以外的方法操作数组的顺序。`shuffle()` 函数会随机重排数组元素的顺序。`array_reverse` 函数为你提供一个所有元素按反序排列的数组副本。

# 使用 shuffle()

Bob 想在他的网站首页展示他的他几个产品。他有很多产品，但希望在首页显示随机选择的物品。为了不让重复访问者感到无聊，他希望每次访问时选出的三个产品都是不同的。如果所有产品都在数组中，他可以轻松实现这一点。列表 3.1 通过将数组打乱为随机顺序并显示第一个，展示三个随机选择的图片。

列表 3.1 bobs_front_page.php——使用 PHP 为 Bob 的汽车零件生成动态首页

```php
<?php
$pictures = array('brakes.png', 'headlight.png',
    'spark.plug.png', 'steering_wheel.png',
    'tire.png', 'wiper_blade.png');

shuffle($pictures);
?>
<!DOCTYPE html>
<html>
<head>
<title>Bob's Auto Parts</title>
```

由于代码选择了随机图片，几乎每次加载时都会产生一个不同的页面，如图 3.5 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_122_0.png)

图 3.5 shuffle() 函数允许你展示三个随机选择的产品

# 反转数组

有时你可能想反转数组的顺序。最简单的方法是使用 `array_reverse()` 函数，它接收一个数组并创建一个内容反序排列的新数组。

使用 `range()` 函数通常创建一个升序序列，如下：

```php
$numbers = range(1,10);
```

然后你可以使用 `array_reverse()` 函数反转由 `range()` 创建的数组：

```php
$numbers = range(1,10);
$numbers = array_reverse($numbers);
```

注意 `array_reverse()` 返回的是数组的修改副本。如果你不需要原始数组（如本例所示），只需将新副本覆盖在原始数组上。

或者，你可以通过编写 `for` 循环以降序创建数组：

```php
$numbers = array();
for($i=10; $i>0; $i--) {
    array_push($numbers, $i);
}
```

循环可以这样按降序操作：使用起始高值并在循环末尾使用 `--` 运算符让计数器减 1。在这里，我们创建一个空数组，并对每个元素使用 `array_push()` 添加到数组末。作为补充，`array_push()` 的相反函数是 `array_pop()`。该函数从数组末尾移除并返回一个元素。

所需的顺序只是降序整数，你也可以通过将 `-1` 作为可选参数传递给 `range()` 来创建：

```php
$numbers = range(10, 1, -1);
```

# 从文件加载数组

在第 2 章“存储数据”中，你学会了如何在文件中存储订单。文件中的每一行如下：

```
2023-10-01|2|1|45.00|123 Main St, CA
2023-10-02|1|0|15.50|456 Oak Ave, NY
2023-10-03|5|2|120.00|789 Pine Rd, TX
```

为了处理这些内容，你可以将其加载回数组。列表 3.2 vieworders.php——使用 PHP 分隔订单

```php
<?php
// 创建短变量
$document_root = $_SERVER['DOCUMENT_ROOT'];
?>
<!DOCTYPE html>
<html>
<head>
<title>Bob's Auto Parts</title>

<style type="text/css">
table, th, td {
  border-collapse: collapse;
  border: 1px solid black;
  padding: 6px;
}

th {
  background: #ccc;
}
</style>
</head>
<body>
<h1>Bob's Auto Parts</h1>
<h2>Customer Orders</h2>

<?php
// 读取整个文件
// 每一行成为数组中的一个元素
$orders = file("$document_root/orders.txt");

// 统计数组中的订单数量
$number_of_orders = count($orders);

if ($number_of_orders == 0) {
    echo "<table><tr><p><strong>没有待处理订单。<br>请稍后再试。</strong></p></tr></table></table>";
} else {
    echo "<table>";
echo "<tr>
<th>Order Date</th>
<th>Tires</th>
<th>Oil</th>
<th>Spark Plugs</th>
<th>Total</th>
<th>Address</th>
</tr>";

    for ($i=0; $i<$number_of_orders; $i++) {
        // 分割每一行
        $line = explode("|", $orders[$i]);

        // 仅保留订单数量
        $line[1] = intval($line[1]);
        $line[2] = intval($line[2]);
        $line[3] = intval($line[3]);

        // 输出每个订单
echo "<tr>
<td style='text-align: right;'>$line[0]</td>
<td style='text-align: right;'>$line[1]</td>
<td style='text-align: right;'>$line[2]</td>
<td style='text-align: right;'>$line[3]</td>
<td style='text-align: right;'>$line[4]</td>
<td>$line[5]</td>
</tr>";
    }
echo "</table>";
}
?>
</body>
</html>
```

# 列表 3.3 vieworders_v2.php——使用 PHP 分隔、格式化并显示订单

```php
<?php
// 创建变量
$document_root = $_SERVER['DOCUMENT_ROOT'];
?>
<!DOCTYPE html>
<html>
<head>
<title>Bob's Auto Parts</title>

<style type="text/css">
table, th, td {
  border-collapse: collapse;
  border: 1px solid black;
  padding: 6px;
}

th {
  background: #ccc;
}
</style>
</head>
<body>
<h1>Bob's Auto Parts</h1>
<h2>Customer Orders</h2>

<?php
// 读取整个文件
// 每一行成为数组中的一个元素
$orders = file("$document_root/orders.txt");

// 统计数组中的订单数量
$number_of_orders = count($orders);

if ($number_of_orders == 0) {
    echo "<table><tr><p><strong>没有待处理订单。<br>请稍后再试。</strong></p></tr></table></table>";
} else {
    echo "<table>";
echo "<tr>
<th>Order Date</th>
<th>Tires</th>
<th>Oil</th>
<th>Spark Plugs</th>
<th>Total</th>
<th>Address</th>
</tr>";

    for ($i=0; $i<$number_of_orders; $i++) {
        // 分割每一行
        $line = explode("|", $orders[$i]);

        // 仅保留订单数量
        $line[1] = intval($line[1]);
        $line[2] = intval($line[2]);
        $line[3] = intval($line[3]);

        // 输出每个订单
echo "<tr>
<td style='text-align: right;'>$line[0]</td>
<td style='text-align: right;'>$line[1]</td>
<td style='text-align: right;'>$line[2]</td>
<td style='text-align: right;'>$line[3]</td>
<td style='text-align: right;'>$line[4]</td>
<td>$line[5]</td>
</tr>";
    }
echo "</table>";
}
?>
</body>
</html>
```
