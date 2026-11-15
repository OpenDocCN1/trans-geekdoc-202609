

现在来看超全局数组：`$_REQUEST` 包含所有表单数据（也包括 cookie；参见第 14 章），无论你使用 GET 还是 POST。访问 `$_POST` 和 `$_GET` 特殊数组来分别处理 POST 和 GET 数据更合理。

表单发送的目标（对 GET 和 POST 均适用）在 `<form>` 标签的 action 属性中指定。使用 GET 时，表单数据也会自动附加到此地址。然而，大多数 PHP 脚本都是这样的：表单本身和用于处理表单数据的 PHP 代码都在同一个文件中。这样做的一个优点是，所有内容都清晰地安排在一处。在许多教程中，你现在会看到建议为表单配置操作——在本例中，如下所示：

```
<form action="<?php echo $PHP_SELF; ?>">
```

`$PHP_SELF` 变量包含当前脚本的 URL。这取决于配置——但始终有效的是 `$_SERVER["PHP_SELF"]`。但这通常不是必需的。如果没有设置 action 会发生什么？让我们来看看 W3C HTML 规范。在 `http://s-prs.co/v602217` 中，它说明对于 HTML 4，如果未设置该属性，浏览器的行为是未定义的；在 (X)HTML 的 DTD 中，action 被标记为必需属性（#REQUIRED）。但是，此限制在 HTML5 中已不再存在。使用 action="" 仍然是良好风格。

然而，在实际中情况有所不同。如果 Web 浏览器找不到 action 属性，它会自动将当前表单发送到当前脚本，这正是我们在这里想要做的。虽然这在任何地方都没有规定，但所有相关浏览器都实现了这一点。但即便如此，这也是危险的：

```
<form action="<?php echo $_SERVER["PHP_SELF"]; ?>">
```

这是因为在某些情况下，`$_SERVER["PHP_SELF"]` 包含当前脚本的完整路径，包括任何 URL 附加内容。但是，攻击者随后能够将恶意 JavaScript 代码附加到地址——造成危险后果（关于各种安全问题的更多信息，请参见第 32 章）。因此，你必须先从输出中删除特殊字符（如双引号和尖括号）。这可以使用 `htmlspecialchars()` 函数完成，该函数以后将更频繁地使用：

```
<form action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
```

接下来，我们将逐步向表单添加代码，以输出输入的数据。我们将根据表单字段类型进行操作。这样做的优点是，你最终不仅可以使用示例表单，还可以使用任何表单；表单字段类型始终相同。

首先，有两点重要说明：

- 由于表单输入也可能包含 HTML 特殊字符，因此所有输出都首先使用 `htmlspecialchars()` 转换为 HTML。

如果在字段中没有输入任何内容，或者表单尚未发送，则访问 `$_POST["field name"]`/`$_GET["field name"]` 可能会导致 PHP 警告。因此，我们首先使用 `isset()` 检查所需条目是否确实存在于 `$_POST`/`$_GET` 数组中：
if (isset($_GET["Field name"])) {
    // ...
}

> Note
> 我们在此始终使用 POST，而不是 GET，因此始终使用 `$_POST` 访问表单数据。如果你在表单中使用 GET，则必须同样编写 `$_GET`。否则，其他方面不会有任何变化。PHP 还会自动处理 URL 中的任何特殊字符编码（及其反向转换）。

> Note
> 还有另一个事先重要的说明：HTML 对表单字段名区分大小写，因此在命名表单字段时请注意这一点。通过 PHP 访问时也有相同的限制：Field、field 和 FIELD 是三个不同的表单字段标识符。

## 13.2.3 文本字段

访问文本字段中的值非常简单：文本字段的值位于 `$_GET["Field"]` 或 `$_POST["Field"]` 中。文本字段的一个特别好用的功能是，即使字段中没有输入任何内容，`$_GET["Field"]` 或 `$_POST["Field"]` 始终已设置，因此可以省略 `isset()` 检查（如果在其他地方已检查表单是否已发送）。尽管如此，执行检查仍然是良好风格。许多攻击者始终在寻找错误消息（因为它们非常揭示性——即使只给出 PHP 文件的绝对路径）并喜欢向脚本发送特制（或空）表单以查看会发生什么。生成错误消息的另一种方法是操纵 HTTP 请求。这样，攻击者可以确保 `$_GET["Field"]` 或 `$_POST["Field"]` 是一个无法对其应用 `htmlspecialchars()` 的数组。这里也有一个简单的补救方法：首先使用 `is_string()` 检查是否确实存在字符串。

> Note
> 大多数语义表单字段——例如 `<input type="email">`、`<input type="url">` 等等——表现得像文本字段；也就是说，有一个字段名和一个关联的值。

清单 13.3 显示了输出文本字段内容的代码（另参见图 13.4）。对于文本和密码字段很简单，但多行文本字段有一个特殊功能：文本中也可以换行。这些使用 PHP 函数 `nl2br()` 正确转换。

> **Note**
>
> 使用 `nl2br()` 进行转换时，必须先使用 `htmlspecialchars()`，然后再将换行符替换为 `<br />`。原因是如果你反向操作，你会先得到 `<br />`，然后由于 `htmlspecialchars()` 而得到字符 `&lt;br /&gt;`，这肯定不是你想要的。

```
<body>
<h1>Form Data</h1>
<?php
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Comments = nl2br(htmlspecialchars($Comments));
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Comments:</b> $Comments<br />";
?>
<h1>World Cup ticket service</h1>
<form method="post">
```

### 清单 13.3 文本字段数据输出（摘录自 "form-output-textfields.php"）

> **Tip**
>
> 你可以以完全相同的方式访问隐藏表单字段（`<input type="hidden" />`）！

![](img/ae7820c36e8f24c1623d26668b28e80e_410_0.png)

图 13.4 文本字段的值显示

## 13.2.4 单选按钮

单选按钮在表单元素中占据特殊地位。通常，每个字段名都是唯一的。然而，对于单选按钮，属于单选按钮组的所有单选按钮的 name 属性值都相同。组内只能选择一个单选按钮。因此，组内的单选按钮在名称上没有区别，而在值（value 属性）上有区别。然而，这使得访问变得简单直观：`$_GET["Field name"]` 或 `$_POST["Field name"]` 包含所选单选按钮的值（如果没有单击任何单选按钮，则未设置）。

> > **Note**
> > 只使用单选按钮的值，而不使用其标签！！

```
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"]))
?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
```

