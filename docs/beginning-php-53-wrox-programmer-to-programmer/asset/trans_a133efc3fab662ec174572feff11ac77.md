

# 第三部分：在表单中使用 PHP

默认情况下，HTML_QuickForm 可以与 23 种不同的元素类型配合。所有元素都继承自 `HTML_QuickForm_element` 类。下面是最常见的元素类型列表，以及显示如何向你的表单中添加元素的代码。

你可以在 http://pear.php.net/manual/en/package.html.html-quickform.intro-elements.php 查看完整的 HTML_QuickForm 元素类型列表。

| 元素类型 | 向表单添加元素的代码 |
| --- | --- |
| 按钮 (button) | $form->addElement("button", "field name", "field value", $attrs); |
| 复选框 (checkbox) | $form->addElement("checkbox", "field name", "field label", "复选框后显示的文本", $attrs); |
| 文件 (file) | $form->addElement("file", "field name", "field label", $attrs); |
| 隐藏域 (hidden) | $form->addElement("hidden", "field name", "field value", $attrs); |
| 图片 (image) | $form->addElement("image", "field name", "image URL", $attrs); |
| 密码 (password) | $form->addElement("password", "field name", "field label", $attrs); |
| 单选框 (radio) | $form->addElement("radio", "field name", "field label", "按钮后显示的文本", "field value", $attrs); |
| 重置 (reset) | $form->addElement("reset", "field name", "field value", $attrs); |
| 选择框 (select) | $form->addElement("select", "field name", "field label", array("optionValue"=>"optionLabel", ...), $attrs); |
| 提交 (submit) | $form->addElement("submit", "field name", "field value", $attrs); |
| 文本 (text) | $form->addElement("text", "field name", "field label", $attrs); |
| 文本区域 (textarea) | $form->addElement("textarea", "field name", "field label", $attrs); |

$attrs 变量是需要添加到标签中的属性列表。它可以以关联数组的形式存在，也可以是一个简单的字符串（例如 'name' = 'value'）。

你可以看到，某些元素是带有值创建的（例如按钮，其值是按钮标签），而另一些元素是通过字段标签创建的（默认显示在字段的左侧）。你始终可以在创建对象后通过调用元素的 `setValue()` 方法来设置你自己的值或标签——例如：

```
$textarea = $form->addElement("textarea", "field name", "field label", $attrs);
$textarea->setValue("Default text");
```

这是一个简单的示例脚本，展示了如何使用 HTML_QuickForm 创建登录表单（不包含任何验证或过滤）：

```php
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
```

# 第 15 章：使用 PEAR 让你的工作更轻松

```php
<head>
<title>Simple HTML_QuickForm Example</title>
</head>
<body>
<h1>Simple HTML_QuickForm Example</h1>
<?php
require_once("HTML/QuickForm.php");
$form = new HTML_QuickForm("*", "post", "*", null, true);
$form->addElement("text", "username", "Username");
$password = $form->addElement("password", "password", "Password");
$password->setValue("");
$buttons = array();
$buttons[] = HTML_QuickForm::createElement("submit", "submitButton", "Send Form");
$form->addGroup($buttons, null, null, "&nbsp;");

if ($form->isSubmitted()) {
    echo "<p>Thanks for your details!</p>";
} else {
    echo $form->toHtml();
}
?>
</body>
</html>
```

在显示页面头部之后，脚本包含了 `HTML/QuickForm.php` 类文件，然后创建了一个新的 `HTML_QuickForm` 对象，该对象具有空白的 `name` 属性、`method="post"` 属性、空的 `action` 和 `target` 属性、没有额外的属性并将 `$trackSubmit` 属性设置为 `true`，这样脚本就可以检测表单何时被提交。

```php
require_once("HTML/QuickForm.php");
$form = new HTML_QuickForm("*", "post", "*", null, true);
```

接下来，脚本向表单添加了一个用户名的文本字段，标签为 "Username"：

```php
$form->addElement("text", "username", "Username");
```

还添加了一个密码输入字段，标签为 "Password"。通过将返回的元素存储在变量 `$password` 中，脚本随后可以设置该字段的值为空字符串：

```php
$password = $form->addElement("password", "password", "Password");
$password->setValue("");
```

如果表单被重新显示，防止密码被发送回浏览器——因此在页面源代码中不可见——是一个好主意。

# 第三部分：PHP 练习

最后，创建了两个按钮：一个提交按钮和一个重置按钮。为了让这两个按钮并排显示，它们被被放置在一个元素组中，并用不换行空格隔开：

```php
$buttons = array();
$buttons[] = HTML_QuickForm::createElement("submit", "submitButton", "Send Details");
$buttons[] = HTML_QuickForm::createElement("reset", "resetButton", "Reset Form");
$form->addGroup($buttons, null, null, "&nbsp;");
```

现在表单已经创建并填充完毕，脚本检查表单是否已提交。如果已提交，则显示一条感谢信息；否则，通过调用 `toHtml` 方法并输出结果来显示表单：

```php
if ($form->isSubmitted()) {
    echo "<p>Thanks for your details!</p>";
} else {
    echo $form->toHtml();
}
```

# 使用验证规则

HTML_QuickForm 提供了许多内置的验证规则类型，你也可以创建自己的规则。以下是你可以配合 `addRule()` 方法（在本章前面的“使用 HTML_QuickForm”部分中描述）一起使用的内置规则类型列表：

| 规则类型 | 参数 $format 参数的值 | 描述 |
| --- | --- | --- |
| required | N/A | 值不能为空。 |
| maxLength | $max (整数) | 值的字符串长度不能超过 $max 个字符。 |
| minlength | $min (整数) | 值的字符串长度不能少于 $min 个字符。 |
| rangelength | $min, $max (整数) | 值的字符串长度必须在 $min 到 $max 之间。 |
| regex | $regex (字符串) | 值必须匹配正则表达式。 |
| email | $domain (布尔) | 值必须是有效的电子邮件地址。 |
| callback | $function | 使用回调函数 $function 检查值。 |
| uploaded | N/A | 必须是上传的文件。 |
| maxfilesize | $max | 上传的文件不能超过 $max 字节。 |
| mimetype | $type | 上传的文件必须是 MIME 类型。 |
| filename | $regex | 上传的文件必须匹配正则表达式。 |
| numeric | N/A | 值必须是数字。 |
| nopunctuation | N/A | 值不能包含标点。 |
| nonzero | N/A | 值不能为零。 |
| compare | $comparisonType | 比较两个值。 |

$comparisonType 的可用值：
| --- | --- |
| eq | 等于。 |
| neq | 不等于。 |
| gt | 大于。 |
| gte | 大于等于。 |
| lt | 小于。 |
| lte | 小于等于。 |

# 第 15 章：使用 PEAR 让你的工作更轻松

| 规则类型 | 参数 $format 参数的值 | 描述 |
| --- | --- | --- |
| numeric | N/A | 值必须是数字。 |
| nopunctuation | N/A | 值不能包含标点。 |
| nonzero | N/A | 值不能为零。 |
| compare | $comparisonType | 比较两个值。 |

# 第三部分：PHP 练习

例如，你可以添加一个规则来检查提交的用户名不能超过十个字符：

```php
$form->addRule("username", "Username be no longer 10 characters", 'maxlength', 10);
```

# 使用 HTML_QuickForm 测试注册表单

为了展示 HTML_QuickForm 的强大和有用，在本示例中，我们将重写第14章的 register.php 脚本，使用 HTML_QuickForm 处理表单显示和验证。

在开始之前，安装名为 `HTML_QuickForm_Renderer_Tableless` 的 PEAR 包。默认情况下，HTML_QuickForm 使用表格来放置表单字段和标签。不使用表格的 HTML 表单更灵活且更容易渲染。此外，HTML_Quick 生成的表格不是有效的 XHTML。HTML_QuickForm_Renderer_Tableless 是一个替换默认 HTML_QuickForm_Renderer 的类，生成符合 XHTML 标准的无表格标记。

编写时，HTML_QuickForm_Renderer_Tableless 是一个 beta 包，这意味着它无法通过默认 PEAR 设置安装：

```
$ install --alldeps HTML_QuickForm_Renderer_Tableless
Failed to download pear/HTML_QuickForm_Renderer_Tableless within preferred state "stable"
```

当你读到该包已不再是 beta 版本时，可以使用正常方式安装它——即使用 `pear install --alldeps HTML_QuickForm_Renderer_Tableless`。如果该包仍然是 beta 版本，你可以通过明确指定通道来安装，如下所示：

```
$ install --alldeps channel://pear.php.net/HTML_QuickForm_Renderer_Tableless-0.6.1
downloading HTML_QuickFormRenderer_Tableless-0.6.1.tgz ... (6,828
bytes)
...: 6,828 bytes
instal ok: channel://pear.php.net/HTML_QuickForm_Renderer_Tableless-0.6.1
$
```

