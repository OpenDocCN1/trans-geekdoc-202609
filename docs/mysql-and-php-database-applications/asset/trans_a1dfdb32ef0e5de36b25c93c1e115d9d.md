

# 第 14 章：购物车

```php
// 其中 $gain 在一个隐藏字段中被设置为 "please"。我们测试
// 这一点，而不是像其他示例中那样测试 $submit 的值，
// 这样用户在输入新数量或勾选删除框后，
// 可以按回车键进行重新计算，
// 而无需实际点击“重新计算(Recalculate)”按钮。

// 对于购物车中的每个项目，将其数量属性
// 设置为来自 $quantity[] 数组的对应值，
// 该数组是由 PHP 从表单提交的 'quantity[$row]' 
// 字段中构建而的。
$quantity = (array)$quantity;
```

```php
reset($cart->items);
while (list($row, $value) = each($cart->items))
{
    // 通过显式地加上 0，PHP 将将 quantity
    // 属性的值设置为至少为 0，即使
    // 出某些原因，用户将该字段
    // 设置为了空值。
    $cart->items[$row]->quantity = $quantity[$row] + 0;
}
```

```php
$remove = (array)$remove;
while (list($row, $value) = each($remove))
{
    // 由 CalculateTotals() 标记待删除的项目
    $cart->items[$row]->killme = $value;
}
```

```php
// 重新计算购物车中每个项目的总价格
$cart->CalculateTotals();
```

```php
// 显示购物车的内容
print start_form();
print hidden_field(array("again=","please"));
```

```php
print start_table(array("border"=>1));
print table_row("<b>项目</b>",
    "<b>数量</b>",
    "<b>价格</b>",
    "<b>总计</b>",
    "<b>删除</b>");
```

```php
reset($cart->items);
while (list($row, $item) = each($cart->items))
{
    // 显示购物车中的每个项目。项目描述
    // 将包含指向项目元素
    // 显示页的链接（分类、产品样式，
    // 如适用）。参见上文 $item 是如何构建的。）
    // 将每个项目的总价格以美元金额
    // 值显示（保留两位小数，前面带有美元符号）。
    // 显示一个允许用户从购物车
    // 中删除项目的复选框。
    print table_row($item,
    text_field("quantity[$row]"));
}
```

```php
// 购物车项目中数量和价格
// 的运行总和。
$total_price += $item->quantity * $item->price;
$total_quantity += $item->quantity;
```

```php
// 由 keep_shopping() 函数显示的“继续购物”按钮
//（定义在 functions.php 中）在它自己的表单中运行
// 所以将其显示在一个 HTML 表格中，与购物车
// 表单的“重新计算”按钮并列，以保持它们并排显示。
print start_table();
```

```php
print table_row(
    submit_field("recalc","重新计算")
    .end_form()

// 继续购物定义在 functions.php 文件中
keep_shopping($category_id,$product_id)
);
print end_table();
```

# CHECKOUT.PHP

现在，该结账了。这确实是唯一需要放在服务器端的文件。目录部分甚至购物车页面都不需要放在服务器端，因为实际上没有什么需要被保护的信息。然而，在这个页面上，我们将接收信用卡信息。再次，脚本中有详尽的注释来帮助你理解逻辑。

```php
include "header.php";

// 如果传递了会 ID，也将其初始化为对象，以防止脚本崩溃。
$cart = new Order;
```

```php
// 使用 Base 类的 Construct 方法
//（定义在 cart_base_class.php 中）将提交的变量加载到购物车。
$cart->Construct($_HTTP_POST_VARS);
```

```php
if (empty($zpath) && is_array($zpath))
{
    // 从过去的订单为用户找到了多个地址，
    // 用户可以要求从数据库中删除一个或多个地址。
    // 这是通过检查命名为 "zpath[]" 的 HTML 复选框字段实现的，
    // 这些字段设置为地址的 ID 值。
    // 如果至少有一个复选框被选中，PHP 将返回
    // 数组变量 $zpath 中的值。（如果没有复选框
    // 被选中，$zpath 不一定为空，但它不会是一个数组）。
    while (list($card) = each($zpath))
    {
        // 使用 Address 类的 DeleteAddress()
        // 方法（定义在 address_class.php 中）删除地址记录
        $cart->DeleteAddress($aid);
    }
}
```

```php
if (!empty($usethis))
{
    // 从过去的订单为用户找到了多个地址，
    // 用户可以通过点击命名为 "usethis" 的单选框字段
    // 要求在本次订单中使用其中一个，该字段设置为
    // 地址的 ID 值。如果 $usethis 被设置，则根据 ID 值
    // 获取地址记录，使用 Address 类的
    // FetchAddress() 方法。
    if ($cart->FetchAddress())
    {
        // 现在只有一个地址
        $cart->address_count = 1;
    }
}

# 第 14 章：购物车

```php
if ($ordernow == button)
{
    // 用户点击了订单按钮。验证他们的
    // 信用卡并结算，使用 Order 类的
    // ValidateCard() 和 ChargeCard() 方法。
    if ($cart->ValidateCard() && $cart->ChargeCard())
    {
        // 结算通过 - 使用 SaveOrder() 写入订单。
        $cart->SaveOrder();

        // 将用户重定向到收据页。
        header("Location:receipt.php?order_id=$id");
        exit;
    }
} elseif ($data)
{
    // 从数据库为用户找到了多个地址
    // 或者我们还没有 ID，加载地址信息。
    $cart->LoadUser($email);
}
```

```php
// 这些字段包含了用户在搜索数据库之前
// 直接输入的地址信息，或者来自数据库
// 选择的地址。在任何情况下，“这些”字段
// 将用于订单。
print_row("<b>地址：</b>",.text_field("address",$cart->address,40,40));
print_row("<b>地址2：</b>",.text_field("address2",$cart->address2,40,40));
print_row("<b>城市：</b>",.text_field("city",$cart->city,40,40));
print_row("<b>状态：</b>",.select_field("state",states($)),cart->state));
print_table("<b>邮编：</b>",.text_field("zip",$cart->zip,10,10));
print_row("<b>电话：</b>",.text_field("phone",$cart->phone,20,20));
```

```php
// 如果只有一个地址，将其属性
// 加载到购物车，简单情况。
$cart->Construct(object($cart->addresses[0]));

// 否则我们从数据库为用户找到了多个可能的地址，
// 情况情况。开始一个 HTML 表格来显示它们。
$useme_cell = start_table(array("border"=>1));

// 开始构建地址列表
$useme_row = "";

// 遍历地址数组
while ($i,$i) = each($cart->addresses)
{
  // 使用引用避免复制对象
  $a = &$cart->addresses[$i];
  // 构建一个包含地址的表格单元格
  // 以及供用户指示如何使用的字段
  $useme_row .= table_row($a);
}
// 添加地址单元格并关闭表格。
//（注意：这在某种程度上假设地址不会超过两个 -
// 否则表格将变得难以处理。）
$useme_cell .= $useme_row;
$useme_cell .= end_table();

// 显示地址
print_row("".table_cell($useme_cell));
print_row("");
```

