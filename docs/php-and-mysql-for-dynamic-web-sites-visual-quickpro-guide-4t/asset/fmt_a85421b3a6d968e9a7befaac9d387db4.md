
### 步骤 6-13：使用 jQuery 重构计算器

**6.** 移除所有现有的 `alert()` 调用（[Script 15.7](#ch15.html#ch15ex07)）。

**7.** 在提交事件处理程序之前，隐藏所有带有 `errorMessage` 类的元素：

```javascript
$('.errorMessage').hide();
```

该选择器获取对任何拥有 `errorMessage` 类的元素的引用。在 HTML 表单中，这仅适用于三个 `span` 标签。

**8.** 在给局部变量 `quantity` 赋值后的 `if` 子句代码中，移除 `error` 类并隐藏错误消息：

```javascript
$('#quantityP').removeClass('error');
$('#quantityError').hide();
```

正如你将在步骤 9 中看到的，当用户输入无效数量时，数量段落（`id` 为 `quantityP`）将被分配 `error` 类，数量错误消息（即 `#quantityError`）将被显示。如果用户先输入无效数量，然后输入有效数量，必须使用此处的代码撤销这两种效果。

如果从未提交过无效数量，数量段落将没有 `error` 类，数量错误消息仍将隐藏。在 jQuery 被要求做不可能的事情时（如隐藏已隐藏的元素），jQuery 会直接忽略该请求。

**9.** 如果数量无效，添加错误类并显示错误消息：

```javascript
$('#quantityP').addClass('error');
$('#quantityError').show();
```

这是步骤 8 中代码的反面操作。注意它位于 `else` 子句内。

**Script 15.7.** 使用 jQuery，JavaScript 代码现在通过操作 DOM 来替代 `alert()` 调用。

---

```javascript
// Script 15.7 - calculator.js #2
// This script is included by calculator.html.
// This script handles and validates the form submission.

// Do something when the document is ready:
$(function() {

    // Hide all error messages:
    $('.errorMessage').hide();

    // Assign an event handler to the form:
    $('#calculator').submit(function() {

        // Initialize some variables:
        var quantity, price, tax, total;

        // Validate the quantity:
        if ($('#quantity').val() > 0) {

            // Get the quantity:
            quantity = $('#quantity').val();

            // Clear an error, if one existed:
            $('#quantityP').removeClass('error');

            // Hide the error message, if it was visible:
            $('#quantityError').hide();

        } else { // Invalid quantity!

            // Add an error class:
            $('#quantityP').addClass('error');

            // Show the error message:
            $('#quantityError').show();

        }

        // Validate the price:
        if ($('#price').val() > 0) {
            price = $('#price').val();
            $('#priceP').removeClass('error');
            $('#priceError').hide();
        } else {
            $('#priceP').addClass('error');
            $('#priceError').show();
        }

        // Validate the tax:
        if ($('#tax').val() > 0) {
            tax = $('#tax').val();
            $('#taxP').removeClass('error');
            $('#taxError').hide();
        } else {
            $('#taxP').addClass('error');
            $('#taxError').show();
        }

        // If appropriate, perform the calculations:
        if (quantity && price && tax) {

            total = quantity * price;
            total += total * (tax / 100);

            // Display the results:
            $('#results').html('The total is <b>$' + total + '</b>.");

        }

        // Return false to prevent an actual form submission:
        return false;

    }); // End of form submission.

}); // End of document ready.
```

---

**10.** 对价格重复步骤 8 和 9，使该 `if-else` 结构如下：

```javascript
if ($('#price').val() > 0) {
    price = $('#price').val();
    $('#priceP').removeClass('error');
    $('#priceError').hide();
} else {
    $('#priceP').addClass('error');
    $('#priceError').show();
}
```

**11.** 对税率重复步骤 8 和 9，使该 `if-else` 结构如下：

```javascript
if ($('#tax').val() > 0) {
    tax = $('#tax').val();
    $('#taxP').removeClass('error');
    $('#taxError').hide();
} else {
    $('#taxP').addClass('error');
    $('#taxError').show();
}
```

**12.** 在计算总计后，在同一个 `if` 子句内，更新 `results` 段落：

```javascript
$('#results').html('The total is <b>$' + total + '</b>.');
```

不使用警告框，总计消息可以直接动态写入 HTML 页面。实现方法之一是更改页面上某个元素的文本或 HTML。页面已有一个用于此目的的空段落，其 `id` 值为 `results`。要更改段落内的文本，可应用 `text()` 函数；要更改段落内的 HTML，则使用 `html()`。

**13.** 将页面另存为 `calculator.js`（位于 `js` 文件夹中），并在 Web 浏览器中测试计算器。

同样请记住，必须重新加载 HTML 页面（因为 HTML 和 JavaScript 都已更新）。

---

> **Tip**
>
> 如果你尝试选择不存在的页面元素，jQuery 不会抛出错误。如果你在不存在的元素上调用函数，jQuery 也不会抛出错误。

---

> **Tip**
>
> 在 JavaScript 中，与其他 OOP 语言一样，你可以“链式”调用函数，一次执行多个操作。以下代码在一行中显示了一个先前隐藏的段落，添加了一个新类，并更改了其文本内容：
>
> ```javascript
> $('#pId').show().addClass('thisClass').text('Hello, world!');
> ```

---

> **Tip**
>
> 你可以使用 `attr()` 函数更改选中元素的属性。其第一个参数是要影响的属性；第二个参数是新值。例如，以下代码将通过添加 `disabled="disabled"` 属性来禁用提交按钮：
>
> ```javascript
> $('#submitButtonId').attr('disabled', 'disabled');
> ```

---

> **Tip**
>
> 你可以使用 `prepend()`、`append()`、`remove()` 等函数添加、移动或删除元素。具体细节请参阅 jQuery 手册。

---

### 使用 Ajax

除了 DOM 操作，JavaScript 和 jQuery 的另一个关键用途是 *Ajax*。Ajax 一词最早于 2005 年提出，尽管浏览器支持多年来好坏参半。到了 2011 年，Ajax 已成为许多动态网站的标准功能，且所有主流浏览器都提供了直接的支持。但什么是 Ajax？

Ajax 可以指代许多事物，涉及多种不同的技术和方法，但归根结底，Ajax 就是使用 JavaScript 在用户不知情的情况下执行服务器端请求。在标准请求模型中（即本书几乎所有其他示例），用户可能从 `login.html` 开始。提交表单后，浏览器会跳转到 `login.php`，在那里进行实际的表单验证、数据库注册并显示结果 ![Image](graphics/circle-a.jpg)。（即使同一个 PHP 脚本既显示又处理表单，标准请求模型也需要对同一页面进行两次单独且明显的请求。）
