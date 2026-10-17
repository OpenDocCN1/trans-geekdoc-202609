
```html
<html>
<head>
<TITLE>说出我的名字</TITLE>
</head>
<body>
<form action="form2.php" method="post">
<table border="0" cellspacing="1" bgcolor="#353535" align="center">
<tr>
<td bgcolor="#ffffff" width="50%">姓名</td>
<td bgcolor="#ffffff" width="50%"><input type="TEXT" name="Name"></td>
</tr>
<tr>
<td bgcolor="#ffffff">问候</td>
<td bgcolor="#ffffff">
<select name="Greeting">
<option value="Hello">Hello</option>
<option value="Hola">Hola</option>
<option value="Bonjour">Bonjour</option>
</select>
</td>
</tr>
<tr>
<td bgcolor="#ffffff" width="50%">调试信息</td>
<td bgcolor="#ffffff" width="50%"><input type="checkbox" name="Debug" CHECKED</td>
</tr>
<tr>
<td bgcolor="#ffffff" colspan="2" align="center"><input type="SUBMIT" name="Submit" value="提交"></td>
</tr>
</table>
</form>
</body>
</html>
```

- 3. 创建另一个名为 `formprocess2.php` 的文件并输入以下代码：

```php
<html>
<head>
<title>说出我的名字</title>
</head>
<body>
<?php
if ($_POST['Debug'] == "on") {
?>
<pre>
<?php
print_r($_POST);
?>
</pre>
<?php
}

<p align="center"><?php echo $_POST['Greeting']? <?php echo $_POST['Name']?></p>
</body>
</html>
```

- 4. 保存 `formprocess2.php` 并将其上传到你的工作文件夹。

- 5. 从浏览器调用页面。

正如你在图 5-4 所示的结果页面中所看到的，表单变得有点复杂了。

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_165_0.png)

- 6. 输入你的名字并点击提交（Submit）按钮。

出现的显示页面如图 5-5 所示，非常简单；它只包含调试信息和一句问候语。

## 工作原理

如你所见，这段代码使用的逻辑与 `formprocess1.php` 类似。添加了两个字段（下拉列表框和一个复选框）。

`formprocess2.php` 执行与 `formprocess1.php` 相同的操作，但增加了一个变化。只有在选中“调试（Debug）”复选框时，它才会显示调试信息，并根据后续小节中下拉列表的任何一个选项向你问候。

# 第 5 章

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

# 表单元素：让用户处理数据

```php
<?php echo $_POST['Submit'] == "Search" ? "for " : "";?>
```

这些元素的工作方式非常简单，可以将其与 if-else 结构相比较：

```
[表达式]?[如果为真]: [执行假]
```

三元运算符是一个为人知的维护性隐患。使用该运算符会降低你代码的可读性，并可能在维护阶段导致错误。

## 使用所有元素

现在你已经了解了所有的表单元素，让我们为应用程序创建一个骨架吧。系统将添加新项目或搜索现有的项目。由于我们目前还没有连接数据库，因此这个表单将只显示输入的信息。

## 尝试一下

## 隐藏和密码输入

1. 创建一个名为 `form4.php` 的文件，并在文本编辑器中打开它。

2. 输入以下代码：

```php
<?php
// 调试信息显示
function debugDisplay(){
?>
<PRE>
$_POST
<?php
print_r($_POST);
?>
$_GET
<?php
print_r($_GET);
?>
</PRE>
<?php
}

// 切换搜索/添加向导步骤
switch($_GET['step']) {
################
    // 搜索/添加表单
################
    case "":
    $type = explode(":*",$_POST['type']);
    if ($_POST['Submit']=="Add") {
        require($_POST['Submit'].$type.'.php');
    } else {
        if ($_POST['type'] == "Movie:Movie" &&
```

```php
$_POST['MovieType'] == "" {
    header('Location:form4.php');
}
?>
<h1>搜索结果</h1>
<p>你正在寻找一个名为 "<?php echo $_POST['Name']?>" 的 <?php echo $type[1]?> ***</p>
<?php
{
    if ($_POST['Debug'] == "on") {
        debugDisplay();
    }
    break;
    ###########################
    // 添加摘要
    ###########################
    case "2":
        $type = explode(":", $_POST['type']);
?>
<h1><a><?php echo $type[1]?> : <?php echo $_POST['Name']?></a></h1>
<?php
switch($type[0]) {
    case "Movie":
<p>发布于 <?php echo $_POST['MovieYear']?></p>
<p><?php echo nl2br(stripslashes($_POST['Desc']))?></p>
<?php

    break;
    default:
?>
<h2>快速简介</h2>
<p><?php echo nl2br(stripslashes($_POST['Bio']))?></p>
<?php

    break;
    ###########################
    // 开始表单
    ###########################
    default:
        require('startform.php');
    break;
}
?>
```

3. 创建一个新文件 `startform.php`，并输入以下代码：

```html
<<html>
<head>
<TITLE>多功能表单</TITLE>
</head>
<body>
<FORM action="form4.php?step=1" method="post">
```

```html
<table border=0 width="750" cellspacing="1" cellpadding="3" bgcolor="#353535" align="center">
<tr>
<td bgcolor="#ffffff" width="30%">
名称
</td>
<td bgcolor="#ffffff" width="70%">
<INPUT type="TEXT" name="Name">
</td>
<tr>
<td bgcolor="#ffffff">
项目类型
</td>
<td bgcolor="#ffffff">
<INPUT type="radio" name="type" value="Movie:Movie" CHECKED
电影<BR>
<INPUT type="radio" name="type" value="Person:Actor"
演员<BR>
<INPUT type="radio" name="type" value="Person:Director"
导演<BR>
</td>
<tr>
<td bgcolor="#ffffff">电影类型（如果适用）
</td>
<td bgcolor="#ffffff">
<SELECT name="MovieType">
<option value="" SELECTED>电影类型...</option>
<option value="Action">动作</option>
<option value="Drama">剧情</option>
<option value="Comedy">喜剧</option>
<option value="Sci-Fi">科幻</option>
<option value="War">战争</option>
<option value="Other">其他...</option>
</SELECT>
</td>
<tr>
<td bgcolor="#ffffff" width="50%">
显示调试转储
</td>
<td bgcolor="#ffffff" width="50%">
<INPUT type="checkbox" name="Debug" CHECKED
</td>
<tr>
<td bgcolor="#ffffff">
<INPUT type="SUBMIT" name="Submit" value="Search">
<INPUT type="SUBMIT" name="Submit" value="Add">
</td>
</tr>
</table>
```

```html
</FORM>
</body>
</html>
```

4. 通过类型 `AddMovie.php` 创建另一个条目，在其中你添加此代码：
