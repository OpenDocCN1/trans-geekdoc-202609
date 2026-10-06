

## 第三部分：PHP 实践

- 如何使用隐藏字段创建一个用户友好的三阶段注册表单
- 创建允许用户上传文件的表单
- 如何使用页面重定向让你的表单使用更加顺畅且安全

在完成本章后，你将能够使用 Web 表单让你的 PHP 脚本变得更加实用和灵活。

## HTML 表单如何工作原理

在查看 PHP 方面的内容之前，先快速查看 HTML 表单是如何构建的。（如果你已经熟悉如何构建 HTML 表单，可以跳过本节。）

HTML 表单（或称为 Web 表单）是嵌入在标准网页中的 HTML 元素集合。通过添加不同类型的元素，你可以创建不同的表单，例如文本字段、下拉菜单、复选框等。

所有的 Web 表单都以开启 `<form>` 标签开始，并以闭合 `</form>` 标签结束：

```html
<form action="myscript.php" method="post">
<!-- 表单内容放在这里 -->
</form>
```

> 顺便说一下，示例中的第二行代码是一个 HTML 注释——<!-- 和 --> 之间的所有内容都会 Web 浏览器忽略。

注意开启 `<form>` 标签内有两个属性：

- `action` 告诉浏览器在用户填写并提交表单时如何发送数据。这应该是一个绝对 URL（例如 http://example.com/myscript.php）或相对 URL（例如 myscript.php 或 ../scripts/myscript.php）。指定 URL 处的脚本应该能够接收并处理表单数据；稍后会详细介绍。

- `method` 告诉浏览器如何发送表单。你可以使用两种方法：`get` 适用于发送少量数据，并让用户更容易提交表单；而 `post` 可以发送大量得多的数据。

一旦你创建了基础表单元素，就可以用各种元素填充它，创建表单中的字段和其他控件（如果你需要，还可以包含其他 HTML 元素如标题、段落和表格）。

## 第 9 章：用 PHP 处理 HTML 表单

### 尝试：创建一个 HTML 表单

在这个示例中，你将创建一个包含各种表单字段的 Web 表单。你不仅将学习如何创建各种类型的表单字段，还能看到这些字段在 Web 浏览器中的外观和工作原理。

将以下文件保存为 `web_form.html` 并置于你的文档根目录下，然后在浏览器中打开它以查看：

```html
<!DOCTYPE html> PUBLIC "//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/DTD/XHTML-11-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
<title>An HTML Form</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>An HTML Form</h1>
<form action="get">
<div style="width:250px">
<label for="textField">A input field</label>
<input type="text" name="textField" id="textField" value="" />
<label for="passwordField">A password field</label>
<input type="password" name="passwordField" id="passwordField" value="" />
<label for="checkboxField">A checkbox field</label>
<input type="checkbox" name="checkboxField" id="checkboxField" value="" />
<label for="radioButtonField1">A radio button field</label>
<input type="radio" name="radioButtonField1" id="radioButtonField1" value="" />
<label for="radioButtonField2">Another radio button</label>
<input type="radio" name="radioButtonField2" id="radioButtonField2" value="" />
<label for="submitButton">A submit button</label>
<input type="submit" name="submitButton" id="submitButton" value="" />
<label for="resetButton">A reset button</label>
<input type="reset" name="resetButton" id="resetButton" value="" />
<label for="fileSelect">A file select field</label>
<input type="file" name="fileSelect" id="fileSelect" value="" />
</div>
</form>
</body>
</html>
```

```html
<label for="hiddenField">A hidden field</label>
<input type="hidden" name="hiddenField" id="hiddenField" value="" />
<label for="imageField">An image field</label>
<input type="image" name="imageField" id="imageField" value="*asterisk.gif" width="23" height="23" />
<label for="pushButton">A push button</label>
<input type="button" name="pushButton" id="pushButton" value="Click Me" />
<label for="pullDownMenu">A pull down menu</label>
<select name="pullDownMenu" id="pullDownMenu" size="1">
  <option value="1">Option 1</option>
  <option value="2">Option 2</option>
  <option value="3">Option 3</option>
</select>
<label for="listBox">A list box</label>
<select name="listBox" id="listBox" size="1">
  <option value="1">Option 1</option>
  <option value="2">Option 2</option>
  <option value="3">Option 3</option>
</select>
<!-- （此处省略了重复的 HTML 代码块，实际翻译时应保持不变） -->
```

## 第 9 章：用 PHP 处理 HTML 表单

- 文本字段（text field）——允许用户输入单行文本。你可以可选地指定值（如果你不想这样做，请留空属性）：

```html
<label for="textField">A input field</label>
<input type="text" name="textField" id="textField" value="" />
```

- 密码字段（password field）——工作方式与文本字段类似，但文本不会显示。这显然是为了用于密码等敏感信息。

```html
<label for="passwordField">A password field</label>
<input type="password" name="passwordField" id="passwordField" value="" />
```

- 复选框字段（checkbox field）——简单的开关；它可以开启或关闭。`value` 属性包含当勾选复选框时发送到服务器的值（如果没有勾选复选框，则不发送任何内容）：

```html
<label for="checkboxField">A checkbox field</label>
<input type="checkbox" name="checkboxField" id="checkboxField" value="yes" />
```

- 单选按钮（radio buttons）——单选按钮通常放在至少两个按钮的组中。一组中的所有按钮具有相同的 `name` 属性。每组只能选择一个。和复选框一样，使用 `value` 属性来存储选择按钮时发送到服务器的值。注意，`value` 属性对于复选框和单选按钮是强制的，而其他字段是可选的：

```html
<label for="radioButtonField1">A radio button field</label>
<input type="radio" name="radioButtonField1" id="radioButtonField1" value="radio1 />
<label for="radioButtonField2">Another radio button</label>
<input type="radio" name="radioButtonField2" id="radioButtonField2" value="radio2" />
```

- 提交按钮（submit button）——点击此类按钮会将填写的表单发送到服务器脚本进行处理。`value` 属性存储显示在按钮内部的文本标签（当点击按钮时，此值也会发送到服务器）：

```html
<label for="submitButton">A submit button</label>
<input type="submit" name="submitButton" id="submitButton" value="" />
```

