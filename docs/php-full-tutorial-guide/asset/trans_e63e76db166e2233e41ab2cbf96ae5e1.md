

`$books=array("computing","religion","history");`

`$arraylength=count($books);`

```
for($x=0;$x<$arraylength;$x++) 

{ 

echo $books[$x]; 

echo "<br>"; 

} 

?>
```

## 关联数组

关联数组是使用你分配给它们的命名键的数组。

然后可以在脚本中使用命名键：

创建关联数组有两种方式：1.`$year=array("benson"=>"1975","anne"=>"1937","Joel"=>"2000");` 或 2.`$year['benson']="1975";`

`$year['anne']="1937";`

`$year['Joel']="2000";`

示例

```
<?php 

$year=array("benson"=>"1975","anne"=>"1937","Joel"=>"2000");

 echo "benson was born in " . $year['benson'] . ; 

?> 
```

## 遍历关联数组

要遍历并输出关联数组的所有值，可以使用 foreach 循环

示例

```
<?php 

$year=array("benson"=>"1975","anne"=>"1937","Joel"=>"2000"); 

foreach($year as $x=>$x_value) 

{ 

echo "Key=" . $x . ", Value=" . $x_value; 

echo "<br>"; 

} 

?> 
```

## 获取数组长度

`count()` 函数用于返回数组的长度（元素个数）：

示例

```
<?php

$books=array("computing","religion","history");

echo count($books); 

?> 
```

# 第 7 章：PHP 函数

PHP 的真正威力来自于其函数；它拥有超过 1000 个内置函数。

注意：

- 除了内置的 PHP 函数，我们还可以创建自己的函数。
- 函数是一段可以在程序中重复使用的语句块。
- 页面加载时函数不会立即执行。
- 函数会通过函数调用来执行。

## 创建用户定义函数

- 用户定义函数声明始终以单词 `"function"` 开头
- 函数名不区分大小写。
- 函数名可以以字母或下划线开头（但不能以数字开头）。
- 为函数命名，使其反映函数的功能

请记住，开始花括号 (`{`) 表示函数代码的开始，结束花括号 (`}`) 表示函数的结束。

语法

```
function functionName() 

{ 

code to be executed; 

} 
```

示例

在下面的示例中，我们创建一个名为 `"displayname"` 的函数。该函数输出 `"Hello world!"`。要调用函数，只需写出其名称：

示例

```
<?php 

function displayname() 

{ 

echo "Hello world!"; 

} 

displayname(); // call the function 

?>
```

## 函数参数

参数就像一个变量，用于向函数传递信息；参数在函数名之后、括号内指定。

你可以添加任意数量的参数；但是，用逗号将它们分隔开。

下面的示例有一个带有两个参数的函数。当调用 `detail()` 函数时，我们也会传递 `detail`（例如 `james`、`1937`），并且 `detail` 在函数内部使用，该函数输出多个不同的详细信息。

示例

```
<?php 

function detail($name,$year) 

{ 

echo "$name Refsnes. born in $year <br>"; 

} 

detail("james","1937"); 

detail("kate","1971"); 

detail("anne","1963"); 

?> 
```

## 默认参数值

下面的示例说明如何使用默认参数。如果不带参数调用函数 `width()`，它将使用默认值作为参数。

示例

```
<?php 

function width($w=60) 

{ 

echo "The width is : $w <br>"; 

} 

width(65); 

width(); // will use the default value of 60 

width(15); 

width(90); 

?> 
```

## 返回值

要让函数返回一个值，请使用 `return` 语句。

示例

```
<?php 

function div($x,$y) 

{ 

$z=$x/$y; 

return $z; 

} 

echo "15 / 2 = " . div(15,5) . "<br>"; 

echo "14/2= " . div(14,2) . "<br>"; 

echo "12 / 4 = " . div(12,4); 

?> 
```

# 第 8 章：PHP 表单处理

## 简单 HTML 表单说明

当你想要从网站访问者那里收集一些数据时，需要 HTML 表单。例如，在用户注册期间，你可能希望收集姓名、电子邮件地址、信用卡等信息。

表单将从网站访问者那里获取输入，然后将其发布到后端应用程序，例如 CGI、ASP 脚本或 PHP 脚本等。后端应用程序将根据应用程序内定义的业务逻辑对传递的数据进行所需处理。

有多种表单元素可用，例如文本字段、文本区域字段、下拉菜单、单选按钮、复选框等。

HTML `<form>` 标签用于创建 HTML 表单，其语法如下：

```
<form action="Script URL" method="GET|POST">

   form elements like input, textarea etc.

</form>
```

| Action | 准备处理传递数据的后端脚本。 |
| --- | --- |
| Method | 用于上传数据的方法。最常用的是 GET 和 POST 方法。 |

## HTML 表单控件

你可以使用不同类型的表单控件来通过 HTML 表单收集数据：

- 复选框控件
- 单选按钮控件
- 下拉列表控件
- 文件选择框
- 隐藏控件
- 可点击按钮
- 提交和重置按钮

## 复选框控件

当需要选择多个选项时，使用复选框。它们也是使用 HTML `<input>` 标签创建的，但 `type` 属性设置为 `checkbox`。

以下是带有两个复选框的表单示例 HTML 代码：

```
<html>

<head>

<title>复选框控件</title>

</head>

<body>

<form>

<input type="checkbox" name="maths" value="on"> Maths

<input type="checkbox" name="physics" value="on"> Physics

</form>

</body>

</html>
```

表单底部

## 单选按钮控件

当有多个选项但只需要选择一个选项时，使用单选按钮。它们也是使用 HTML `<input>` 标签创建的，但 `type` 属性设置为 `radio`。

以下是带有两个单选按钮的表单示例 HTML 代码：

```
<html>

<head>

<title>单选按钮控件</title>

</head>

<body>

<form>

<input type="radio" name="subject" value="maths"> Maths

<input type="radio" name="subject" value="physics"> Physics

</form>

</body>

</html>
```

表单顶部

表单底部

## 下拉列表控件

下拉列表（也称为下拉框）提供一个选项，以列表形式列出各种选项，用户可以从中选择一个或多个选项。

以下是带有一个下拉列表的表单示例 HTML 代码：

```
<html>

<head>

<title>下拉列表控件</title>

</head>

<body>

<form>

<select name="dropdown">

<option value="Maths" selected>Maths</option>

<option value="Physics">Physics</option>

</select>

</form>

</body>

</html>
```

表单顶部

表单底部

## 文件上传框

如果你想允许用户将文件上传到你的网站，则需要使用文件上传框，也称为文件选择框。这也是使用 `<input>` 元素创建的，但 `type` 属性设置为 `file`。

以下是带有一个文件上传框的表单示例 HTML 代码：

```
<html>

<head>

<title>文件上传框</title>

</head>

<body>

<form>

<input type="file" name="fileupload" accept="image/\*" />

</form>

</body>

</html>
```

表单顶部

表单底部

## 按钮控件

在 HTML 中有多种方法可以创建可点击按钮。你也可以通过将 `<input>` 标签的 `type` 属性设置为 `button` 来创建可点击按钮。`type` 属性可以取以下值：

以下是带有三种类型按钮的表单示例 HTML 代码：

```
<html>

<head>

<title>按钮控件</title>

</head>

<body>

<form>

<input type="submit" name="submit" value="Submit" />

<input type="reset" name="reset" value="Reset" />

<input type="button" name="ok" value="OK" />

<input type="image" name="imagebutton" src="/html/images/logo.png" />

</form>

</body>

</html>
```

表单底部

## 隐藏表单控件

