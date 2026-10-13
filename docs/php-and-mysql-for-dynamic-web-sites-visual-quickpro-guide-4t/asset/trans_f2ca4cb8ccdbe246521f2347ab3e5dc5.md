

## 6. 对其他两个表单输入重复验证

```javascript
if ($('#price').val() > 0) {
    price = $('#price').val();
} else {
    alert('Please enter a valid price!');
}

if ($('#tax').val() > 0) {
    tax = $('#tax').val();
} else {
    alert('Please enter a valid tax!');
}
```

## 7. 如果所有三个变量都有有效值，执行计算

```javascript
if (quantity && price && tax) {
    total = quantity * price;
    total += total * (tax / 100);
}
```

到目前为止，这段代码应该相当显而易见：它看起来几乎与 PHP 中完全一样，只是每个变量名前没有美元符号。

## 8. 报告总计

```javascript
alert('The total is $' + total);
```

同样，将使用一个简陋的警告窗口来显示计算结果。正如你在这段代码中所见，加号在 JavaScript 中执行连接操作。

## 9. 完成第 7 步开始的条件语句并返回值 `false`

```javascript
}
return false;
```

让函数返回 `false` 可以阻止表单实际提交给表单 `action` 属性所指定的脚本。

## 10. 将页面另存为 `calculator.js`（在 `js` 文件夹中）并在 Web 浏览器中测试计算器。

请注意，如果你的 Web 浏览器中已经加载了 `calculator.html`，你需要刷新浏览器以加载更新后的 JavaScript。

---

### 提示

有许多专门用于验证表单的 jQuery 插件，但我想保持简单（并在过程中解释核心 JavaScript 概念）。

---

### 提示

可以在 JavaScript 中格式化数字，例如使其始终包含两位小数，但这不容易实现。基于这个原因，以及因为我不想分散对所涵盖的更重要信息的关注，计算结果可能并不总是像应该的那样美观。

---

### 提示

使用 jQuery 时，如果浏览器支持，JavaScript 代码将执行计算。如果用户禁用了 JavaScript，或者正在使用非常古老的浏览器，JavaScript 将不会生效，表单将照常提交（此处提交到不存在的 `calculator.php`）。

---

## DOM 操作

JavaScript 总体上，特别是 jQuery，最关键的用途之一是 DOM 操作：以任何方式更改 Web 浏览器的内容。通常，DOM 操作表现为改变用户所见的内容；在 jQuery 中做到这一点有多容易是其优势之一。

一旦你选中了要操作的元素，对该选择应用任意数量的 jQuery 函数都将改变其属性。首先，`hide()` 和 `show()` 函数分别隐藏和显示选择。因此，要隐藏一个表单（也许在用户成功完成后），你可以使用：

```javascript
$('#actualFormId').hide();
```

调用 `toggle()` 函数时，将隐藏可见元素并显示隐藏元素（即在这两种状态之间切换）。请注意，这些函数既不创建也不销毁选择（即无论可见与否，选择将保留为 DOM 的一部分）。

与 `show()` 和 `hide()` 类似的是 `fadeIn()` 和 `fadeOut()`。这些函数也用于显示或隐藏选择，但会添加一些淡入淡出效果。

影响 DOM 的另一种方法是更改应用于选择的 CSS 类。`addClass()` 函数应用一个 CSS 类，`removeClass()` 移除一个。以下代码向特定的 blockquote 添加 `emphasis` 类，并从所有段落中移除它：

```javascript
$('#blockquoteID').addClass('emphasis');
$('p').removeClass('emphasis');
```

`toggleClass()` 函数可用于切换选择的类应用。

上述提到的函数通常更改页面元素的*属性*，但你也可以更改这些元素的*内容*。在上一节中，你使用了 `val()` 函数，它返回表单元素的值。但当提供参数时，`val()` 会为该表单元素分配一个新值：

```javascript
$('#something').val('cat');
```

类似地，`html()` 函数返回元素的 HTML 内容，`text()` 返回文本内容。这两个函数也可以接受参数，分别用于分配新的 HTML 和文本。

让我们利用所有这些信息来完成小部件成本计算器。将进行几项关键更改：

- 通过应用 `error` 类来指示错误
- 通过隐藏或显示错误消息来指示错误
- 将最终总计写入页面
- 不再使用警告框

显示和隐藏错误消息有几种方法。此处实现的最简单方法是手动将消息添加到表单中，然后使用 JavaScript 切换它们的可见性。因此，这些步骤从更新 HTML 页面开始。

### 操作 DOM

**1.** 在文本编辑器或 IDE 中打开 `calculator.html`（如果尚未打开）。

**2.** 在数量表单元素及其结束段落标签之间，添加一条错误消息（脚本 15.6）：

```html
<p id="quantityP">Quantity: <input type="text" name="quantity" id="quantity" /> <span class="errorMessage" id="quantityError">Please enter a valid quantity!</span></p>
```

现在输入框后面跟着一条文本错误消息，它也有一个唯一的 `id`。包含错误的 span 还使用了 `errorMessage` 类。得益于外部 CSS 文档，这会影响消息的格式，并使 jQuery 在首次加载页面时更容易全局隐藏所有错误消息。

**3.** 对其他两个表单输入重复步骤 2：

```html
<p id="priceP">Price: <input type="text" name="price" id="price" /><span class="errorMessage" id="priceError"> Please enter a valid price! </span></p>
<p id="taxP">Tax (%): <input type="text" name="tax" id="tax" /><span class="errorMessage" id="taxError"> Please enter a valid tax! </span></p>
```

**4.** 保存文件。

**5.** 在文本编辑器或 IDE 中打开 `calculator.js`（如果尚未打开）。

**脚本 15.6。** 更新后的 HTML 页面在关键表单输入旁硬编码了错误消息。

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Widget Cost Calculator</title>
    <link rel="stylesheet" href="css/style.css" type="text/css" media="screen" />
    <script type="text/javascript" src="js/jquery-1.6.1.min.js" charset="utf-8"></script>
    <script type="text/javascript" src="js/calculator.js" charset="utf-8"></script>
</head>
<body>
    <!-- Script 15.6 - calculator.html #2 -->
    <h1>Widget Cost Calculator</h1>
    <p id="results"></p>
    <form action="calculator.php" method="post" id="calculator">
        <p id="quantityP">Quantity: <input type="text" name="quantity" id="quantity" />
            <span class="errorMessage" id="quantityError">Please enter a valid quantity!</span></p>
        <p id="priceP">Price: <input type="text" name="price" id="price" /><span class="errorMessage" id="priceError">Please enter a valid price!</span></p>
        <p id="taxP">Tax (%): <input type="text" name="tax" id="tax" /><span class="errorMessage" id="taxError">Please enter a valid tax!</span></p>
```

