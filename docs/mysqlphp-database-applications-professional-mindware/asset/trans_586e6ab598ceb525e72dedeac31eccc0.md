
print table_row(
    radio_field("shipping_id",$ship->shipping_id,$ship->shipping,$cart->shipping_id)
    , table_cell(money($ship->per_order),array("align"=>"right"))
    , table_cell(money($ship->per_item),array("align"=>"right"))
    , table_cell(money($shiptotal),array("align"=>"right"))
);
print end_table();

// display payment information
print subtitle("Credit Card Info");

print start_table();

if ($cart->error)
{
    // if the user tried to place an order and there was an error
    // when validating or charging the card, display it here.
    print table_row(
        table_cell("<font color=red>$cart->error</font>"
            ,array("colspan"=>2)
        )
    );
    $cart->error = "";
}

// display a test card number in the form for this example by
default.
// it has a valid format, and since we're not really trying
// to charge any cards here, AuthorizeNet will accept it.
if (empty($cart->cc_number)) { $cart->cc_number = "4912-7398-07156";
}

// pick Visa as the default type, to match the default test card
number
if (empty($cart->cc_type_code)) { $cart->cc_type_code = "vis"; }

// use the db_radio_field() function (defined in
/book/functions/forms.php)
// to display the accepted credit card types as radio button fields

```php
print table_row("<b>Credit Card:</b>"
    ,
    db_radio_field("cc_type_code","cc_types","cc_type_code","cc_type"
        , "cc_type_code",$cart->cc_type_code
        )
    );

print table_row("<b>Number:</b>",text_field("cc_number",$cart->cc_number,20));

// set the variables used to enter the credit card expiration date

// set the $months array to a list of possible months
for ($i = 1; $i <= 12; $i++) { $months[$i] = $i; }

// set the $years array to a list of plausible years
for ($i = 2000; $i <= 2005; $i++) { $years[$i] = $i; }

// use January 2001 as a default expiration date
if (empty($cart->cc_exp_mon)) { $cart->cc_exp_mon = 1; }
if (empty($cart->cc_exp_yr)) { $cart->cc_exp_yr = 2001; }

print table_row("<b>Expires:</b>"
    , select_field("cc_exp_mon",$months,$cart->cc_exp_mon)
        .select_field("cc_exp_yr",$years,$cart->cc_exp_yr)
);
print end_table();

// save the ID of the address used in this order (if any)
print hidden_field("address_id",$cart->address_id);

// display the order button
print paragraph(submit_field("ordernow",$order_button));

print end_form();

include "end_page.php";

?>
```

## Summary

在本书的最终应用中，你看到了一些有趣的东西。你了解到像购物车这样的应用程序需要某种状态维护方法。对于像购物车这样的东西，使用 PHP 维护状态的最佳方式可能是使用会话。

如果你想处理信用卡，你需要一个安全的服务器、一个 SSL 证书，以及一套用于处理卡片的函数。在本应用程序中，我们使用 cURL 函数进行信用卡处理，但还有另外两套函数集（PayfloPro 和 Cybercash）值得你研究。

本章最后需要注意的是类的使用方式。通过扩展现有类，并编写方法来覆盖之前的方法，我们能够灵活地使用大块代码。

## Appendix A

## HTML Forms

如果你希望你的应用程序能够接收用户数据，你就需要为他们提供输入信息的地方。这需要 HTML 表单。HTML 表单使用起来足够简单。有几种常用的输入类型，在使用 HTML 4.0 和层叠样式表的浏览器中，你可以使用一些技术使你的表单更精美。对表单可以做的一切的完整讨论超出了本书的范围。如果你需要更多关于表单的信息，以及它们如何与 CSS 或 JavaScript 配合工作，或一些较新的浏览器特定表单类型，请查看 http://microsoft.com 或 http://mozilla.org 上的文档。

## Form Basics

每个表单都由开始和结束的 <form> 标签分隔。<form> 标签接受以下属性：

-   `action`—此属性指定表单将被发送以进行处理的页面的 URL。它可以包含相对 URL（例如，“myscript.php”或“../myfolder/myscript”）或完整 URL（例如，http://www.mydomain/myscript.php”）。
-   `method`—此属性指示浏览器将发送到服务器的 HTTP 请求类型。它必须设置为 GET 或 POST。如果将其设置为 GET，name=value 对将出现在浏览器位置栏中（例如，http://mypage.com?name1=value1&name2=value2）。使用 GET 的优点是结果可以在浏览器中 bookmark。缺点是发送的变量会更透明。如果将此属性设置为 POST，name=value 对将不可见。默认值是 GET。
-   `name`—此属性最适用于通过 JavaScript 地址表单的各个部分。表单名称在表单提交时不会发送到服务器。
-   `enctype`—默认值是“application/x-www-form-urlencoded”，这通常就足够了。但如果你正在上传文件（使用 <input type="file">，你应该使用“multipart/form-data”。

一个典型的表单外壳看起来像这样：

```
<form name="myform" action="processor.php" method="post">
...
</form>
```

## Input Types

表单的大部分工作将由输入类型完成。一个输入标签和 type 属性将决定在浏览器中呈现何种表单元素。每个输入类型都必须有一个 name 属性。这就是你将变量传递给脚本的方式，所以请确保不要忘记它们。（为了绝对准确，你不需要为提交和重置按钮提供 name 属性。）

作为一个快速示例，以下内容将创建一个包含单个文本框和提交按钮的简单表单。文本框的默认值为“hello there”，如图 A-1 所示。

```
<form>
    <input type="text" size="50" maxlength="15"
    value="hello there"><br>
    <input type="submit" name="submit" value="OK?">
</form>
```

![](img/de0823012275cf4ceebdb822a56e6b71_432_0.png)

图 A-1：简单的 HTML 表单

输入类型如下。注意不同的输入类型有不同的关联属性。它们都接受 name 属性。

-   **Text** — 此类型在上面的示例中显示。它可以接受以下属性：
    -   Size，表示在 Web 浏览器中呈现的框的长度。
    -   Maxlength，限制可以输入到字段中的字符数。请记住，较旧的浏览器会忽略 maxlength，即使在较新的浏览器中，你也不应依赖此属性来限制上传。检查你的 `php.ini` 中的 `upload_max_filesize` 项以在服务器上设置限制。
    -   Value，即框中的默认值。用户可以通过输入不同的信息来覆盖它。
-   **Password** — 此类型与文本字段相同，只是输入到框中的文本显示为星号。
-   **Hidden** — 此类型不会在屏幕上呈现。它非常适用于在页面之间传递值。隐藏字段只需要 name 和 value 属性即可。考虑在你不喜欢使用 cookie 或会话时使用隐藏字段。请注意，通过简单地查看你的 Web 页面的源代码，精明的用户将能够看到你的隐藏表单元素。不要在隐藏表单中放置任何敏感数据。
-   **Submit** — 此类型在页面上放置一个提交按钮。value 属性中的文本将出现在提交按钮上。当表单提交时，提交按钮的 name 和 value 会像所有其他表单元素一样一起传递。
-   **Image** — 此类型将与提交按钮具有相同的用途，但它允许你指定一个图像而不是那个丑陋的旧提交按钮。将此表单元素视为任何 `<img>` 标签。提供 src 和 alt 属性。
-   **Reset** — 此类型提供一个按钮，按下时将你的表单更改为页面最初加载时的状态。重置按钮的默认文本是“Reset”。通过添加 value 属性，你可以更改重置按钮上的文本。重置按钮与 PHP 或服务器无关。
-   **File** — 此类型提供看起来像文本框和一个文字为“browse”的按钮。当用户点击浏览时，他们会得到一个窗口，允许他们通过操作系统找到他们想要上传的文件。如果使用此输入类型，请务必将 `form enctype` 属性更改为“multipart/form-data”。有关使用 PHP 上传文件的讨论，请参阅第 10 章。

