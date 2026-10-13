

```php
if ($gender == 'M') {

  $greeting = '<p><b>Good day, Sir!</b></p>';

} elseif ($gender == 'F') {

  $greeting = '<p><b>Good day, Madam!</b></p>';

} else {

  $gender = NULL;

  echo '<p class="error">Gender should be either "M" or "F"!</p>';

}
```

在 gender 的 `if` 子句中嵌套了一个 `if-elseif-else` 条件语句，用于将变量的值与可接受的值进行比对。这是两步性别验证的第二部分。

条件本身与上一个脚本中的相同。如果 gender 最终既不等于 `M` 也不等于 `F`，则表明出现了问题，并会打印一条错误消息。在这种情况下，`$gender` 变量也会被设置为 `NULL`，因为它拥有不可接受的值。

如果 `$gender` 确实拥有有效值，则将特定性别的消息赋值给一个新变量，以便稍后在脚本中打印。

### 7. 完成主 gender `if-else` 条件语句：

```php
} else {

  $gender = NULL;

  echo '<p class="error">You forgot to select your gender!</p>';

}
```

如果 `$_REQUEST['gender']` 未设置，则适用此 `else` 子句。完整的嵌套条件语句（参见 [Script 2.4](#ch02.html#ch02ex04) 的第 41-57 行）成功检查了每一种可能性：

* `$_REQUEST['gender']` 未设置
* `$_REQUEST['gender']` 的值为 `M`
* `$_REQUEST['gender']` 的值为 `F`
* `$_REQUEST['gender']` 拥有其他值

您可能会想知道最后一种情况如何可能发生，因为值是在 HTML 表单中设置的。如果恶意用户创建他们自己的表单并提交给您的 `handle_form.php` 脚本（这非常容易做到），他们可以赋予 `$_REQUEST['gender']` 任何他们想要的值。

### 8. 打印指示验证结果的消息：

```php
if ($name && $email && $gender && $comments) {

  echo "<p>Thank you, <b>$name</b>, for the following comments:<br />
  <tt>$comments</tt></p>
  <p>We will reply to you at <i>$email</i>.</p>\n";
  echo $greeting;

} else {

  echo '<p class="error">Please go back and fill out the form again.</p>';

}
```

如果列出的每个变量都拥有真值，则主条件为真。如果变量通过了测试，它将拥有一个值；如果未通过，则值为 `NULL`。如果每个变量都有值，则表单已完整填写，因此将打印 *Thank you* 消息，以及特定性别的问候语。如果有任何变量为 `NULL`，则将打印第二条消息。

![Image](graphics/02_figure_13_a.jpg)

脚本现在会检查每个表单元素是否已填写（age 除外），并报告那些未填写的元素。

![Image](graphics/02_figure_14_b.jpg)

即使只漏填了一两个字段，*Thank you* 消息也不会被打印。

### 9. 关闭 PHP 部分并完成 HTML 页面：

```php
?>
</body>
</html>
```

### 10. 将文件保存为 `handle_form.php`，将其与 `form.html` 放在同一 Web 目录中，并在 Web 浏览器中测试。

以不同程度的完整性填写表单，以测试新脚本。

![Image](graphics/02_figure_15_c.jpg)

如果表单填写正确，脚本的行为将与之前相同。

---

> **Tip**
>
> 要测试提交的值是否为数字，请使用 `is_numeric()` 函数。

---

> **Tip**
>
> 在 [Chapter 14](#ch14.html#ch14) “[Perl-Compatible Regular Expressions](#ch14.html#ch14)” 中，您将看到如何使用正则表达式验证表单数据。

---

> **Tip**
>
> 让用户在填写表单时知道哪些字段是必填项，以及在适用的情况下该字段的格式（如日期或电话号码），这被认为是良好的规范（此处有双关语，form 既指“表单”也指“规范/礼仪”）。

---

### 数组简介

[Chapter 1](#ch01.html#ch01) 介绍了两种 *scalar*（单值）变量类型：字符串和数字。现在是时候了解另一种类型——*array*（数组）了。与字符串和数字不同，*array* 可以容纳多个独立的信息片段。因此，数组就像一个值列表，其中每个值可以是字符串、数字，甚至是另一个数组。

数组的结构是一系列 *key-value*（键值）对，其中一对是该数组的一个项目或 *element*（元素）。列表中的每个项目都有一个与之关联的 *key*（键）或 *index*（索引）（[Table 2.3](#ch02.html#ch02table03)）。

**Table 2.3. Array Example 1: `$artists`**

![Image](graphics/02tab03.jpg)

PHP 支持两种数组：*indexed*（索引数组），使用数字作为键（如 [Table 2.3](#ch02.html#ch02table03) 所示）；以及 *associative*（关联数组），使用字符串作为键（[Table 2.4](#ch02.html#ch02table04)）。与大多数编程语言一样，索引数组的第一个索引从 0 开始，除非您显式指定键。

**Table 2.4. Array Example 2: `$states`**

![Image](graphics/02tab04.jpg)

数组遵循与其他变量相同的命名规则。这意味着，乍一看，您可能无法分辨 `$var` 是数组，还是字符串或数字。重要的语法差异出现在访问单个数组元素时。

要引用数组中的特定值，从数组变量名开始，后跟方括号中的键：

```php
$band = $artists[0]; // The Mynabirds
echo $states['MD']; // Maryland
```

您可以看到，数组键在 PHP 中像其他值一样使用：数字（如 0）从不加引号，而字符串（`MD`）必须加引号。

---

### 超全局数组

PHP 包含几个称为 *superglobal*（超全局）变量的预定义数组。它们包括：`$_GET`、`$_POST`、`$_REQUEST`、`$_SERVER`、`$_ENV`、`$_SESSION` 和 `$_COOKIE`。

`$_GET` 变量存储通过 `GET` 方法发送给 PHP 脚本的所有值（可能但不一定来自 HTML 表单）。`$_POST` 存储从使用 `POST` 方法的 HTML 表单发送给 PHP 脚本的所有数据。这两者——连同 `$_COOKIE`——都是 `$_REQUEST` 的子集，您一直在使用它。

`$_SERVER` 在 [Chapter 1](#ch01.html#ch01) 中已使用过，它存储关于 PHP 运行所在服务器的信息，`$_ENV` 也是如此。`$_SESSION` 和 `$_COOKIE` 将在 [Chapter 12](#ch12.html#ch12) “[Cookies and Sessions](#ch12.html#ch12)” 中讨论。

良好的安全性和编程的一个方面是引用变量时要精确。这意味着，虽然您可以使用 `$_REQUEST` 访问通过 `POST` 方法提交的表单数据，但 `$_POST` 会更准确。

---

由于数组使用不同于其他变量的语法，且可包含多个值，因此打印它们可能比较棘手。以下代码将无法工作：

```php
echo "My list of states: $states";
```

![Image](graphics/02_figure_16_a.jpg)

尝试仅使用变量名打印数组会导致打印出单词 *Array*。

然而，如果使用索引（数字）键，打印单个元素的值很简单：

```php
echo "The first artist is $artists[0].";
```

但如果数组使用字符串作为键，用于包裹键的引号会搞乱语法。以下代码将导致解析错误：

```php
echo "IL is $states['IL']."; // BAD!
```

![Image](graphics/02_figure_17_b.jpg)

尝试在*不*使用花括号的情况下打印关联数组中的元素会导致解析错误。

要修复此问题，当数组使用字符串作为键时，请将数组名和键包裹在花括号中：

```php
echo "IL is {$states['IL']}.";
```

![Image](graphics/02_figure_18_c.jpg)

在使用花括号的情况下尝试打印关联数组中的元素可按预期工作。

