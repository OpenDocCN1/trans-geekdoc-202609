

| Method | Description |
| :--- | :--- |
| `addRule( $element, $message, $type, $format, $validation, $reset, $force )` | 将验证规则添加到名为 `$element` 的表单元素。`$message` 是在输入数据无效时显示在表单字段旁边的错误消息，`$type` 是要使用的规则类型（例如，"required" 用于检查字段是否包含数据，或 "alphanumeric" 用于检查字段中的数据是否为字母数字）。某些规则需要 `$format`（例如，"regex" 类型期望将正则表达式作为 `$format` 参数）。`$validation` 可以是 "server" 或 "client"。表单通常在 PHP 脚本中进行验证（即服务器端）。在此指定 "client" 时，`HTML_QuickForm` 还会在表单中包含 JavaScript 以进行额外的客户端验证。`$reset` 与 "client" `$validation` 设置协同工作；如果设置为 true，则在出现错误时将表单元素重置为其原始值。（默认值为 `false`。）最后，`$force` 会强制应用验证规则，即使相关元素不存在于表单中。默认值为 `false`；设置为 `true` 以强制验证。除 `$element`、`$message` 和 `$type` 外，所有参数均为可选（如果规则类型要求，则还包括 `$format`）。 |
| `applyFilter( $element, $filter )` | 将过滤器应用于元素数据。过滤器是一个回调函数。`$element` 是要过滤的元素，`$filter` 是回调名称。例如，要修剪名为 "username" 的表单字段中的空格，可以使用 `$form->applyFilter( "username", "trim" )`。要将所有字段通过过滤器，请使用特殊元素名称 `"__ALL__"`。您还可以编写自己的过滤器回调函数。 |
| `isSubmitted()` | 如果表单已由用户发送回脚本，则返回 `true`；如果这是首次显示表单，则返回 `false`。（仅在使用 `$trackSubmit` 设置为 `true` 创建表单时有效。） |
| `validate()` | 对提交的表单数据运行所有验证规则，如果表单有效则返回 `true`，否则返回 `false`。此外，错误消息会自动插入表单中，位于无效表单字段旁边。 |
| `process( $callback, $mergeFiles )` | 通过将表单数据传递名为 `$callback` 的函数来处理提交的表单。您需要自己创建此函数，它应期望一个包含提交的表单字段和值的关联数组。默认情况下，任何上传的文件也会传递给回调函数（通过将 `$mergeFiles` 设置为 `false` 来关闭此功能）。 |
| `toHtml()` | 返回用于显示表单的 HTML 标记。创建表单后调用此方法以检索要插入到网页中的 HTML。 |

## 第三部分：在实践中使用 PHP

默认情况下，HTML_QuickForm 可与 23 种不同的元素类型一起使用。所有元素都派生自 HTML_QuickForm_element 类。以下是最常见元素类型的列表，以及展示如何将元素添加到表单的代码。

您可以在 http://pear.php.net/manual/en/package.html.html-quickform.intro-elements.php 上找到 HTML_QuickForm 元素类型的完整列表。

| 元素类型 | 将元素添加到表单的代码 |
| :--- | :--- |
| button | $form->addElement( "button", "field name", "field value", $attrs ); |
| checkbox | $form->addElement( "checkbox", "field name", "field label", "text to display after checkbox", $attrs ); |
| file | $form->addElement( "file", "field name", "field label", $attrs ); |
| hidden | $form->addElement( "hidden", "field name", "field value", $attrs ); |
| image | $form->addElement( "image", "field name", "image URL", $attrs ); |
| password | $form->addElement( "password", "field name", "field label", $attrs ); |
| radio | $form->addElement( "radio", "field name", "field label", "text to display after button", "field value", $attrs ); |
| reset | $form->addElement( "reset", "field name", "field value", $attrs ); |
| select | $form->addElement( "select", "field name", "field label", array( "optionValue" => "optionLabel", "option2Value" => "option2Label", ... ), $attrs ); |
| submit | $form->addElement( "submit", "field name", "field value", $attrs ); |
| text | $form->addElement( "text", "field name", "field label", $attrs ); |
| textarea | $form->addElement( "textarea", "field name", "field label", $attrs ); |

可选的 $attrs 参数是要添加到元素标记的任何属性列表。它可以是关联数组的形式，也可以是简单字符串（例如 'name = "value" '）。

您可以看到，某些元素是使用值创建的（例如按钮，其值为按钮标签），而其他元素则是使用字段标签创建的（默认显示在字段左侧）。创建对象后，您始终可以通过调用元素对象的 setValue() 或 setLabel() 方法为字段设置自己的值或标签——例如：

```
$textArea = $form->addElement( "textarea", "field name", "field label",
    $attrs );
$textArea->setValue( "Default text" );
```

以下是一个使用 HTML_QuickForm 创建登录表单（不带任何验证或过滤）的简单示例脚本：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Simple HTML_QuickForm Example</title>
</head>
<body>
<h1>Simple HTML_QuickForm Example</h1>
<?php
require_once ( "HTML/QuickForm.php" );
$form = new HTML_QuickForm( "", "post", "", "", null, true );
$form->addElement( "text", "username", "Username" );
$password = $form->addElement( "password", "password", "Password" );
$password->setValue( "" );
$buttons = array();
$buttons[] = HTML_QuickForm::createElement( "submit", "submitButton", "Send Details" );
$buttons[] = HTML_QuickForm::createElement( "reset", "resetButton", "Reset Form" );
$form->addGroup( $buttons, null, null, "&nbsp;" );
if ( $form->isSubmitted() ) {
   echo "<p>Thanks for your details!</p>";
} else {
   echo $form->toHtml();
}
?>
</body>
</html>
```

显示页面标题后，脚本会包含 HTML/QuickForm.php 类文件，然后创建一个新的 HTML_QuickForm 对象，其 name 属性为空，method="post" 属性，action 和 target 属性为空，没有其他属性，并将 $trackSubmit 属性设置为 true，以便脚本可以检测表单何时已提交：

```
require_once ( "HTML/QuickForm.php" );
$form = new HTML_QuickForm( "", "post", "", "", null, true );
```

接下来，脚本向表单添加一个名为 "Username" 的用户名文本输入字段：

```
$form->addElement( "text", "username", "Username" );
```

还添加了一个名为 password 的密码输入字段，标签为 "Password"。通过将返回的元素对象存储在变量 $password 中，脚本随后可以将字段值设置为空字符串：

```
$password = $form->addElement( "password", "password", "Password" );
$password->setValue( "" );
```

这样做是个好主意，以防止如果重新显示表单，密码会被发送回浏览器（因此在页面源代码中可见）。

最后，创建了两个按钮：一个提交按钮和一个重置按钮。为了让这两个按钮并排显示，它们被放入一个元素组中，并由不间断空格分隔：

```
$buttons = array();
$buttons[] = HTML_QuickForm::createElement( "submit", "submitButton", "Send Details" );
$buttons[] = HTML_QuickForm::createElement( "reset", "resetButton", "Reset Form" );
$form->addGroup( $buttons, null, null, "&nbsp;" );
```

既然 $form 对象已创建并填充，脚本会检查表单是否已提交。如果已提交，则显示感谢消息；否则，通过调用 toHtml() 方法并输出结果来显示表单：

```
if ( $form->isSubmitted() ) {
   echo "<p>Thanks for your details!</p>";
} else {
   echo $form->toHtml();
}
```

### 使用验证规则

HTML_QuickForm 自带多种内置验证规则类型，或者您可以创建自己的。以下是可与 addRule() 方法一起使用的内置规则类型列表（如前面“使用 HTML_QuickForm”章节中所述）：

| 规则类型 | $format 参数的值 | 描述 |
| :--- | :--- | :--- |
| required | 不适用 | 值不得为空。 |
| maxlength | $max (整数) | 值的字符串长度不得超过 $max 个字符。 |
| minlength | $min (整数) | 值的字符串长度至少为 $min 个字符。 |
| rangelength | array( $min, $max )（整数） | 值的字符串长度必须介于 $min 和 $max 个字符之间。 |
| regex | $regex (字符串) | 值必须匹配正则表达式 $regex。 |
| email | $domainCheck (布尔值，默认：false) | 值必须是有效的电子邮件地址。将 $domainCheck 设置为 true 以使用 PHP checkdnsrr() 函数验证电子邮件域。 |
| lettersonly | 不适用 | 值只能包含字母。 |
| alphanumeric | 不适用 | 值只能包含字母和/或数字。 |

