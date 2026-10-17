
# 创建 HTML 表单

## 1. 创建基础 HTML 文档

在文本编辑器或 IDE 中新建一个 HTML 文档，命名为 `form.html`（**脚本 2.1**）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <title>Simple HTML Form</title>
  <style type="text/css" title="text/css" media="all">
  label {
    font-weight: bold;
    color: #300ACC;
  }
  </style>
</head>
<body>
<!-- Script 2.1 - form.html -->
```

该文档使用与上一章相同的基本 HTML 页面语法。我添加了一些内联 CSS（层叠样式表），以便稍微美化表单（具体来说，让 `label` 元素变粗并变蓝）。

CSS 是处理 HTML 页面中许多格式和布局问题的首选方式。你将在本书中看到一些 CSS 片段；如果你不熟悉该主题，请查阅专门的 CSS 参考资料。

最后，一个 HTML 注释标明了文件的名称和编号。

## 2. 添加初始 `form` 标签

```html
<form action="handle_form.php" method="post">
```

由于 `action` 属性决定表单数据将提交到哪个脚本，你应该给它一个合适的名称（`handle_form` 以对应此页面：`form.html`）和 `.php` 扩展名（因为将由 PHP 脚本处理该表单的数据）。

## 3. 开始 HTML 表单

```html
<fieldset><legend>Enter your information in the form below:</legend>
```

我使用 `fieldset` 和 `legend` HTML 标签，因为我喜欢它们让 HTML 表单呈现的效果（它们在表单周围添加一个带有顶部标题的边框）。不过，这与表单功能本身无关。

## 4. 添加两个文本输入框

```html
<p><label>Name: <input type="text" name="name" size="20" maxlength="40" /></label></p>
<p><label>Email Address: <input type="text" name="email" size="40" maxlength="60" /></label></p>
```

这些只是简单的文本输入框，允许用户输入姓名和电子邮件地址。如果你想知道，每个输入标签末尾额外的空格和斜杠是有效 XHTML 所要求的。在标准 HTML 中，这些标签将以 `maxlength="40">` 结尾。`label` 标签只是将每个文本标签与相关联的元素绑定起来。

## 5. 添加一组单选按钮

```html
<p><label for="gender">Gender:</label><input type="radio" name="gender" value="M" /> Male <input type="radio" name="gender" value="F" /> Female</p>
```

这两个单选按钮具有相同的名称，意味着两者只能二选一。但它们的值不同。

## 6. 添加一个下拉菜单

```html
<p><label>Age:
<select name="age">
  <option value="0-29">Under 30</option>
  <option value="30-60">Between 30 and 60</option>
  <option value="60+">Over 60</option>
</select></label></p>
```

`select` 标签启动下拉菜单，然后每个 `option` 标签将在选项列表中创建另一行。

## 7. 添加一个用于评论的文本域

```html
<p><label>Comments: <textarea name="comments" rows="3" cols="40"></textarea></label></p>
```

文本域不同于文本输入框；它们呈现为一个方框，而不是单行。它们允许输入更多信息，适用于接收用户评论。

## 8. 完成表单

```html
</fieldset>
<p align="center"><input type="submit" name="submit" value="Submit My Information" /></p>
</form>
```

第一个标签关闭第 3 步中打开的 `fieldset`。然后创建一个提交按钮，并使用 `p` 标签将其居中。最后，关闭表单。

## 9. 完成 HTML 页面

```html
</body>
</html>
```

## 10. 保存并查看

将文件保存为 `form.html`，将其放入 Web 目录，并在 Web 浏览器中查看。

---

> **提示**
>
> 由于此页面仅包含 HTML，因此使用 `.html` 扩展名。它也可以使用 `.php` 扩展名而不会有任何问题（因为 PHP 标签之外的代码被视为 HTML 处理）。

---

> **提示**
>
> 你也可以在 HTML 表单标签中指定接受的编码：
>
> ```html
> <form accept-charset="utf-8">
> ```
>
> 默认情况下，网页将使用与页面本身相同的编码来处理任何提交的数据。

---

# 处理 HTML 表单

## 使用 PHP 处理 HTML 表单

既然 HTML 表单已经创建完毕，现在是时候编写一个基础的 PHP 脚本来处理它了。所谓“处理”表单，是指 PHP 页面将对接收到的数据（即用户在表单中输入的数据）执行某些操作。在本章中，脚本仅将数据原样打印回 Web 浏览器。在后续示例中，表单数据将被存储在 MySQL 数据库中、与先前存储的值进行比较、通过电子邮件发送，等等。

PHP 的魅力所在——也是它如此易学易用的原因——在于它与 HTML 表单交互的效果极佳。PHP 脚本将接收到的信息存储在特殊变量中。例如，假设你有一个表单，其中包含如下定义的输入框：

```html
<input type="text" name="city" />
```

用户在该输入框中输入的任何内容都可以通过名为 `$_REQUEST['city']` 的 PHP 变量访问。拼写和大小写必须*完全匹配*，这一点至关重要！PHP 在变量名方面区分大小写，因此 `$_REQUEST['city']` 可行，但 `$_Request['city']` 和 `$_REQUEST['City']` 将没有任何值。

下一个示例将是一个处理已创建的 HTML 表单（脚本 2.1）的 PHP 脚本。该脚本会将表单数据赋值给新变量（作为简写形式使用，就像脚本 1.5 `predefined.php` 中那样）。然后脚本会打印接收到的值。

## 处理 HTML 表单

### 1. 创建 PHP 文档

在文本编辑器或 IDE 中新建一个 PHP 文档，命名为 `handle_form.php`，从 HTML 部分开始编写（**脚本 2.2**）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>

  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

  <title>Form Feedback</title>

</head>

<body>
```

### 2. 添加 PHP 开启标签并创建表单数据变量的简写版本

```php
<?php # Script 2.2 - handle_form.php

$name = $_REQUEST['name'];

$email = $_REQUEST['email'];

$comments = $_REQUEST['comments'];
```

遵循前面概述的规则，输入到名为 *name* 的第一个表单输入框中的数据，将可通过变量 `$_REQUEST['name']` 访问（表 2.1）。输入到 email 表单输入框（其 `name` 值为 *email*）中的数据，将可通过 `$_REQUEST['email']` 访问。comments 数据同理。再次强调，此处变量的拼写和大小写必须与 HTML 表单中对应的 `name` 值*完全匹配*。

**脚本 2.2.** 该脚本接收并打印出 HTML 表单（脚本 2.1）中输入的信息。

```html
1  <!DOCTYPE html PUBLIC "-//W3C//DTD
      XHTML 1.0 Transitional//EN"
      "http://www.w3.org/TR/xhtml1/DTD/
      xhtml1-transitional.dtd">
2  <html xmlns="http://www.w3.org/1999/
      xhtml" xml:lang="en" lang="en">
3  <head>
4      <meta http-equiv="Content-Type"
         content="text/html; charset=utf-8" />
5      <title>Form Feedback</title>
6  </head>
7  <body>
8  <?php # Script 2.2 - handle_form.php
9
10  // Create a shorthand for the form data:
11  $name = $_REQUEST['name'];
12  $email = $_REQUEST['email'];
13  $comments = $_REQUEST['comments'];
14  /* Not used:
15  $_REQUEST['age']
16  $_REQUEST['gender']
17  $_REQUEST['submit']
18  */

19  // Print the submitted information:
20  echo "<p>Thank you, <b>$name</b>,
      for the following comments:<br />
21  <tt>$comments</tt></p>
22  <p>We will reply to you at
      <i>$email</i>.</p>\n";
23
24  ?>
25  </body>
26  </html>
```

**表 2.1. 表单元素到 PHP 变量的对应关系**

此时，你不会用到 `age`、`gender` 和 `submit` 这几个表单元素。

### 3. 打印接收到的 name、email 和 comments 值

```php
echo "<p>Thank you, <b>$name</b>, for the following comments:<br />
<tt>$comments</tt></p>
<p>We will reply to you at <i>$email</i>.</p>\n";
```

提交的值只是通过 `echo` 语句、双引号以及少量的 HTML 格式化打印出来。

### 4. 完成页面

```php
?>

</body>

</html>
```

### 5. 保存文件

将文件保存为 `handle_form.php`，并将其放置在与 `form.html` 相同的 Web 目录下。
