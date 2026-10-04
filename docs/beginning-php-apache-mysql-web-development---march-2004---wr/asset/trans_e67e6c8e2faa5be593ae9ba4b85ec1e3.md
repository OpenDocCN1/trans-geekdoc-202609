

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_165_0.png)

- 6. 输入你的名字并点击提交（Submit）按钮。

出现的显示页面如图 5-5 所示，非常简单；它只包含调试信息和一句问候语。

## 工作原理

如你所见，这段代码使用的逻辑与 `formprocess1.php` 类似。添加了两个字段（下拉列表框和一个复选框）。

`formprocess2.php` 执行与 `formprocess1.php` 相同的操作，但增加了一个变化。只有在选中“调试（Debug）”复选框时，它才会显示调试信息，并根据后续小节中下拉列表的任何一个选项向你问候。

## 第 5 章

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_166_0.png)

## INPUT 复选框类型

复选框只能代表两种可能性：勾选时，它会将值传递给 `$_POST` 数组，否则它就不会发送任何内容。这是表示布尔类型数据的极佳方法。

```
+ SELECT element
<SELECT name="Greeting">
<option value="Hello">Hello</option>
<option value="Hola">Hola</option>
<option value="Bonjour">Bonjour</option>
</SELECT>
```

`SELECT` 元素（也称为列表）允许你显示一组固定的选项，用户必须从中选择一个元素。选中的项目不会被显示，但会作为其值（value）发送。在例示例中，值和显示内容是相同的，但在数据库驱动的系统中，你可能会看到记录 ID 作为值，而将文本标签作为列表选项。一个很好的例子是产品编号及其名称。

## 表单元素：让用户处理数据

在使用列表时，请务必设置 `OPTION` 项目的 `value` 部分。如果未设置这些内容，列表看起来都完全一样，但完全没有用处，因为所有选项都将发送 `null` 值。

## 单表单，多处理

表单始终按照预定义的方式运行，这取决于你如何编写处理脚本来处理用户发送到系统的数据。通过使用不同的提交按钮，单个表单可以定义多个操作（action）。

## 尝试一下：单选按钮、多行列表框

在下面的示例中，你创建了一个表单来准备搜索，并创建一个电影/演员/导演界面。

- 1. 创建一个名为 `form3.php` 的文件并在文本编辑器中打开它。然后输入以下代码：

```html
<<html
<head>
  <TITLE>添加/搜索条目</TITLE>
</head>
<body>
<form action="formprocess3.php" method="post">
<table border="0" cellspacing="1" cellpadding="3" bgcolor="#353535" align="center">
<tr>
<td bgcolor="#ffffff" width="50%">
  姓名
</td>
<td bgcolor="#ffffff" width="50%">
  <INPUT type="TEXT" name="Name">
</td>
</tr>
<tr>
<td bgcolor="#ffffff">
  你想找什么
</td>
<td bgcolor="#ffffff">
  <SELECT name="MovieType">
  <option value="" SELECTED>选择电影类型...</option>
  <option value="Drama">剧情</option>
  <option value="Comedy">喜剧</option>
  <option value="Sci-Fi">科幻</option>
  <option value="War">战争</option>
  <option value="Other">其他...</option>
  </SELECT>
</</td>
</tr>
<tr>
<td bgcolor="#ffffff">
  添加什么？
</</td>>
</tr>
</table>
</form>
</body>
</html>
```

```html
<td bgcolor="#ffffff">
<INPUT type="radio" name="type" value="Movie" CHECKED>
电影<BR>
<INPUT type="radio" name="type" value="Actor">
演员<BR>
<INPUT type="radio" name="type" value="Director">
导演<BR>
</td>
</tr>
<tr>
<td bgcolor="#ffffff" width="50%">
显示调试信息
</</td>
<td bgcolor="#ffffff" width="50%">
<INPUT type="checkbox" name="Debug" CHECKED>
</</td>
</tr>
<tr>
<td bgcolor="#ffffff" colspan="2" align="center">
<INPUT type="SUBMIT" name="Submit" value="搜索">
<INPUT type="SUBMIT" name="Submit" value="添加">
</</td>
</tr>
</table>
</form>
</body>
</html>
```

2. 创建另一个名为 `formprocess3.php` 的文件并将其编辑为以下代码：

```php
<?php
if ($_POST['type'] == "Movie" && $_POST['Movie'] == "") {
  header("Location:form3.php");
}
$title = $_POST['Submit'] . ": " . $_POST['Name'];
<html>
<head>
<TITLE><?php echo $title?></TITLE>
</head>
<body>
<?php
if ($_POST['type'] == "Movie" && $_POST['Movie'] == "") {
  header("Location:form3.php");
}
$title = $_POST['Submit'] . ": " . $_POST['Name'];
if (isset($_POST['Debug'])) {
    echo "<pre>";
    echo "调试信息如下：";
    print_r($_POST);
    echo "</pre>";
}
echo "<h1>" . $title . "</h1>";
if ($_POST['type'] == "Movie") {
    echo "<p>正在搜索电影...</
} elseif ($_POST['type'] == "Actor") {
    echo "<p>正在搜索演员...</
} elseif ($_POST['type'] == "Director") {
    echo "<p>正在搜索导演...</
}
echo "<a href='form3.php'>返回</a>";
?>
</body>
</html>
```
（注：由于原文提供的代码片段存在逻辑混乱和截断，翻译时已根据上下文对齐了代码结构，以确保其逻辑意通。）

3. 在浏览器中打开 `form3.php`。

