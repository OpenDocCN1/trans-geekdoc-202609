
## 练习 6-3 使用 NetBeans 单步执行 Guitar Shop 应用

在本练习中，你将使用 NetBeans 和 xDebug 设置断点并单步执行第 5 章的 Guitar Shop 应用。这将帮助你理解 MVC 应用中的控制流。

- 1. 启动 NetBeans，并打开位于 `ex_starts` 目录中的 `ch06_ex3` 应用。
- 2. 在 `product_manager` 目录中打开 `index.php` 文件。然后，在 `if` 语句的第一行设置断点。
- 3. 运行调试器并单步执行应用。根据需要在 NetBeans 和浏览器之间切换。
- 4. 显示变量窗口并注意变量如何显示以及在单步执行应用时如何变化。
- 5. 使用 Step Into 按钮并注意 NetBeans 如何在必要时在文本编辑器中打开源代码文件。
- 6. 使用 Continue 按钮并注意它如何根据你在应用中的位置显示浏览器或跳到你在第 2 步中设置的断点。
- 7. 实验结束后，结束调试会话，移除断点并关闭项目。

## 7 如何处理表单数据

在第 2 章中，你学习了从表单获取数据并在网页上显示数据的简单技术。现在，本章回顾这些技术。它还介绍了从表单控件获取数据并在网页上显示数据的一些新技术。

- **如何从表单获取数据** ... 210
  - 如何从文本框、密码框和隐藏字段获取数据 ... 210
  - 如何从单选按钮获取数据 ... 212
  - 如何从复选框获取数据 ... 214
  - 如何从一组复选框获取数据 ... 216
  - 如何从下拉列表获取数据 ... 218
  - 如何从列表框获取数据 ... 220
  - 如何从文本区域获取数据 ... 222
- **如何在网页上显示数据** ... 224
  - 如何格式化特殊字符 ... 224
  - 如何格式化换行 ... 226
  - 如何使用 echo 和 print 语句显示数据 ... 228
- **视角** ... 230

### 如何从表单获取数据

HTML 表单可以包含多种类型的控件，例如文本框、单选按钮、复选框、下拉列表和文本区域。正如你在第 2 章中所学，当包含这些控件的表单提交到服务器时，控件中的数据会作为名称/值对的数组传递给服务器。以下主题展示了如何在你的 Web 应用中使用这些控件。

#### 如何从文本框、密码框和隐藏字段获取数据

图 7-1 展示了如何使用三种类型的控件获取文本输入。这些控件都是使用 HTML `<input>` 标签创建的。

*文本框*，也称为 *文本字段*，是表单最常见的控件类型。姓名、地址和电话号码只是你可以用文本字段收集的数据类型中的几个。

*密码框*，也称为 *密码字段*，与文本字段类似，只是用户输入时文本不会在屏幕上显示。相反，每个字符都会显示一个圆点字符。这种字段类型适用于输入 *敏感* 数据，例如密码和 PIN 号码。

*隐藏字段* 是不会在网页上显示的文本字段。程序员经常使用隐藏字段将数据从一个网页传递到另一个网页。

当你为控件编码 name 属性时，必须遵循命名 PHP 变量的规则，只是没有初始的美元符号。例如，在此图中，用户名字段的 name 属性为 `user_name`，其数据存储在名为 `$user_name` 的变量中。虽然你不必为变量使用与控件相同的名称，但这被认为是一种良好的编码实践。

对于文本字段，你可以使用 value 属性为字段提供默认值。由于你通常不希望为密码字段提供默认值，因此此属性通常不与密码字段一起使用。然而，value 属性对于隐藏字段是必要的，因为用户无法在此类字段中输入值。

此图展示了如何使用 GET 和 POST 方法从表单获取数据。由于代码中唯一的区别是将 `filter_input` 函数的类型参数从 `INPUT_GET` 更改为 `INPUT_POST`，因此本章其余的图仅显示 POST 方法。

如果表单使用 GET 方法，浏览器会在其 URL 中显示控件的数据。由于这不安全，因此如果表单包含密码字段或其他你不想在 URL 中显示的敏感数据，通常会使用 POST 方法。

除了这些输入字段外，HTML5 还引入了更多字段，例如用于电子邮件地址的“email”、用于 URL 的“url”以及用于电话号码的“tel”。受支持的浏览器可能会为这些控件添加功能，例如数据验证。例如，对于电子邮件地址，如果用户输入无效的电子邮件地址，浏览器可能会显示错误消息。然而，如果你想要更多

**获取文本输入的 HTML `<input>` 标签的属性**

| 属性 | 描述 |
|---|---|
| **type** | 设置为“text”表示文本字段，“password”表示密码字段，或“hidden”表示隐藏字段。默认值为“text”。此外，还有更多 HTML5 类型，包括用于电子邮件地址的“email”、用于 URL 的“url”以及用于电话号码的“tel”。 |
| **name** | 表单提交时字段的名称。 |
| **value** | 字段的值。对于隐藏字段，必须设置此属性才能使字段正常工作。 |

**三种类型字段的 HTML**

```html
<input type="text" name="user_name" value="rharris">
<input type="password" name="password">
<input type="hidden" name="action" value="login">
```

**浏览器中的文本和密码字段**

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_234_0.png)

**使用 GET 方法时的 URL**

```text
process_data.php?user_name=rharris&password=s3cr3t72&action=login
```

**GET 方法的 PHP**

```php
<?php
    $user_name = filter_input(INPUT_GET, 'user_name');
    $password = filter_input(INPUT_GET, 'password');
    $action = filter_input(INPUT_GET, 'action');
?>
```

**使用 POST 方法时的 URL**

```text
process_data.php
```

**POST 方法的 PHP**

```php
<?php
    $user_name = filter_input(INPUT_POST, 'user_name');
    $password = filter_input(INPUT_POST, 'password');
    $action = filter_input(INPUT_POST, 'action');
?>
```

**描述**

- *文本框* 允许用户在框中输入数据。
- *密码框* 允许用户在框中输入数据，但它会隐藏用户输入的字符。这可以防止敏感数据在屏幕上显示。
- *隐藏字段* 允许程序员向表单添加额外的名称/值对。
- 如果表单使用 GET 方法，字段的数据会显示在 URL 中。

*图 7-1 — 如何从文本框、密码框和隐藏字段获取数据*

#### 如何从单选按钮获取数据

**单选按钮的 HTML `<input>` 标签属性**

| 属性 | 描述 |
|---|---|
| `type` | 设置为“radio”表示单选按钮。 |
| `name` | 组中所有单选按钮必须使用相同的名称。 |
| `value` | 单选按钮的值。此属性对于单选按钮正常工作是必要的。 |
| `checked` | 此可选属性选择默认的单选按钮。 |

**一组三个单选按钮的 HTML**

```html
<input type="radio" name="card_type" value="visa" checked> Visa<br>
<input type="radio" name="card_type" value="mastercard"> MasterCard<br>
<input type="radio" name="card_type" value="discover"> Discover
```

**浏览器中的单选按钮**

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_236_0.png)

**访问单选按钮组的 PHP**

```php
<?php
    $card_type = filter_input(INPUT_POST, 'card_type');
?>
```

**为没有默认按钮的组添加默认值的 PHP**

```php
<?php
    $card_type = filter_input(INPUT_POST, 'card_type');
    if ($card_type == NULL) {
        $card_type = 'unknown';
    }
?>
```

**描述**

- *单选按钮允许用户从一组选项中选择一个选项。*
- *如果组中没有任何单选按钮被选中，则该组的名称/值对不会作为表单的一部分提交到服务器，并且 `filter_input` 函数返回 NULL。*
- *如果你为多个单选按钮编码 checked 属性，浏览器在页面加载时会选择最后一个单选按钮。*

*图 7-2. 如何从单选按钮获取数据*
