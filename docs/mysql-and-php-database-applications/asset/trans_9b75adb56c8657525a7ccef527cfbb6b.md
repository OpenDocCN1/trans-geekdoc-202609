

```php
if (!empty($cart->address_id)) {
    // 允许用户创建新地址
    print table_row("
        . checkbox_field("save_as_new"
```php
print end_table();

// 显示可用的配送方式
print subtitle("配送信息");

print start_table();

print table_row(
    "<b>配送方式</b>",
    . table_cell("<b>每订单</b>",array("align"="right")),
    . table_cell("<b>每个物品</b>",array("align"="right")),
    . table_cell("<b>此订单合计</b>",array("align"="right"))
);

// 如果没有选择配送方式，则使用第一个作为默认
if (empty($cart->shipping_id)) { $cart->shipping_id = 1; }

// 从数据库获取配送方式列表
$result = safe_query("select shipping_id,shipping.per_item,per_order from shipping");

while ($ship = mysql_fetch_object($result)) {
    // 计算使用此方法的费用。我们使用了一种简单的系统：
    // 每个订单的固定费用，以及每个物品的费用。
    $shiptotal = $ship->per_order + ($cart->total_quantity * $ship->per_item);
}

// 显示配送方式，并提供单选框允许
// 用户进行选择
```

# 第 14 章：购物车

```php
print table_row(
radio_field("shipping_id"
```

// 显示支付信息

print subtitle("信用卡信息");

print start_table();

if ($cart->error)
{
    // 如果用户尝试下单，且在验证或扣款信用卡时
    // 发生错误，则在此处显示。
    print table_row(
    table_cell("<font color=red>$cart->error</font>",array("colspan"=2))
    )
}
$cart->error = "";

// 在示例的表单中显示一个测试卡号。
// 它具有有效格式，由于我们在这里并没有真的尝试
// 扣除任何费用，AuthorizeNet 会接受它。
if (empty($cart->cc_number)) {$cart->cc_number = "4912-7398-07156";};

// 选择 Visa 作为默认类型，以匹配默认测试卡
if (empty($cart->cc_type_code)) {$cart->cc_type_code = "vis";}

// 使用在 /book/functions/forms.php 中定义的
// db_radio_field() 函数
// 将接受的信用卡类型显示为单选框字段

print table_row("<b>信用卡：</b>",
db_radio_field("cc_type_code","cc_types","cc_type_code",
    "cc_type_code",$cart->cc_type_code)
);

print table_row("<b>卡号：</b>",text_field("cc_number","$cart->cc_number,20));

// 将月份数组设置为可能的月份列表
for ($i = 1; $i <= 12; $i++) { $months[$i] = $i; }

// 将年份数组设置为合理的年份列表
for ($i = 2000; $i <= 2005; $i++) { $years[$i] = $i; }

// 使用 2001 年 1 月作为默认过期日期
if (empty($cart->cc_exp_mon)) { $cart->cc_exp_mon = 1; }
if (empty($cart->cc_exp_yr)) { $cart->cc_exp_yr = 2001; }

print table_row("<b>过期：</b>",
    select_field("cc_exp_mon",$months,$cart->cc_exp_mon)
    .select_field("cc_exp_yr",$years,$cart->cc_exp_yr)
)
print end_table();

// 保存此订单中使用的地址 ID（如果有）
print hidden_field("address_id",$cart->address_id);

// 显示订单按钮
print paragraph(submit_field("ordernow",$order_button));

print end_form();

include "end_page.php";
?>
```

# 总结

在本书的最后一个应用程序应用中，你看到了一些有趣的东西。你学了像购物车这样的应用程序需要某种方法来维护状态。对于像购物车这样的东西，使用 PHP 维护状态最好的方法可能是 Session（sessions）。

如果你希望处理信用卡，你将需要一个安全的服务器、SSL 证书以及一组用于处理卡的函数。在本文程序中，我们使用了 cURL 函数进行信用卡处理，但还有两组函数（PayfloPro 和 Cyberscash）是你应该研究的。

本章最后需要注意的是类是如何被类的。通过扩展现有的类并编写方法来覆盖之前的方法，我们能够灵活地使用大段代码。

# 附录 A

## HTML 表单

如果你想让应用程序接收用户数据，你就需要一个让他们输入信息的地方。HTML 表单非常易于操作。有几种常用的输入类型，并且在使用 CSS 让你的表单更精美的浏览器中。关于你可以使用表单可以做到的所有事情的完整讨论超出了本书的范畴。如果你需要更多关于表单以及它们如何与 JavaScript 交互的信息，请查看 microsoft.com 或 mozilla.org 的文档。

### 表单基础

如果你想让应用程序接收用户数据，你就需要一个让他们输入信息的地方。HTML 表单非常易于操作。有几种常用的输入类型，并且在使用 CSS 让你的表单更精美的浏览器中。关于你可以使用表单可以做到的所有事情的完整讨论超出了本书的范畴。如果你需要更多关于表单以及它们如何与 JavaScript 交互的信息，请查看 microsoft.com 或 mozilla.org 的文档。

每个表单都由 `<form>` 标签界定。它具有以下属性：

- action——此属性指定表单提交的 URL。
- method——此属性指示 HTTP 请求类型（GET 或 POST）。
- name——此属性对于上传文件非常有用。
- enctype——此属性指定表单类型（例如 `application/x-www-form-urlencoded` 或 `multipart/form-data`）。

### 输入类型

大多数表单的工作通过输入类型完成。每个输入类型都必须具有 name 属性。图 A-1：简单的 HTML 表单

输入类型如下。注意不同的输入类型具有不同的属性。每个类型都必须具有 name 属性。

- Text——这种类型如上面的示例所示。它可以接受这些属性：
    - Size——指示浏览器中输入框的长度。
    - Maxlength——限制可以输入字段的字符数。请注意，旧浏览器会忽略 maxlength，即使在新的浏览器中，你不应依赖此属性。检查服务器上的 `upload_max_filesize` 项来设置限制。
    - Value——是框中的默认值。用户可以通过输入来覆盖它。

- Password——这种类型与文本字段相同，只是在框中输入的文字显示为星号。

- Hidden——这种类型不在屏幕上渲染。它在页面之间传递值非常有用。你只需要 name 和 value 属性。如果你对 cookie 或 session 感到不安，考虑使用隐藏字段。注意，通过简单查看 Web 页面的源代码，老的用户能够看到你的隐藏表单元素。不要将敏感数据放在隐藏表单中。

- Submit——在页面上放置一个提交按钮。value 属性中的文字将出现在提交按钮上。当表单提交时，提交按钮的 name 和 value 将与其他表单元素一起传递。

- Image——这种类型的作用与提交按钮相同，但它允许你指定图像而不是使用任何旧的提交按钮。像处理 `<img>` 标签一样处理此表单元素。提供 src 和 alt 属性。

- Reset——这种类型提供了一个按钮，按下会将表单恢复到页面最初加载状态。重置按钮的默认文本是“Reset”。通过添加 value 属性，你可以更改重置按钮的文字。重置按钮不涉及 PHP 或服务器。

- File——这种类型提供了一个看起来像文本框和一个带有“浏览”文字的按钮。点击时，浏览器会给出一个窗口，允许他们遍历操作系统以找到想要上传的文件。如果使用这种输入类型，请确保将表单 enctype 属性更改为 `multipart/form-data`。请参第 10 章关于 PHP 上传文件的讨论。

