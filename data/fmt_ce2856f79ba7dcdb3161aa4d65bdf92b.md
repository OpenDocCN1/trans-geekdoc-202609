
```php
<?php
$x = $_POST['choice'];
switch($x){
    case 1:
        if ($x==1){
            print "You have chosen item 1.";
        }
        break;
    case 2:
        if ($x==2){
            print "You have chosen item 2.";
        }
        break;
}
print "You have not chosen anything!";
?>
```

在上面的代码中，使用`switch`而不是`if`语句来选择两个项目之一。这些将从类似下面的 HTML 页面中选择。

```html
<html>
<head><title>Switch</title></head>
<body>
<form action="switch.php" method="post">
<p>Please complete the feedback form</p>
<p>Username: <input type="text" name="username"></p>
<p>Password: <input type="password" name="password"></p>
<input type="submit" value="Send my details">
</form>
</body>
</html>
```

语句体。

循环持续持续直到条件不再成立。输出为 1...10。

以下代码演示了`do...while`循环。

```php
<?php
$x=0;
do
{
$x=$x+1;
print("$x");
}while ($x<10);
?>
```

输出将与`while`循环相同。1...10。

除了 PHP 中的`break`语句外，还有`Exit`和`die`语句。`break`语句在`switch`中出现过。

`Exit`和`die`语言构造不是退出当前结构，而是终止 PHP 脚本的执行。

在任何`Exit`或`die`实例之后的所有 PHP 代码都永远不会执行。使用这两个构造之后的 HTML 代码将不会发送到浏览器。

`die`构造经常被用于访问文件和数据库的代码中。`Exit`通常与`header()`函数配合使用。

# 第 4 章 数组

在书的开头，数组（Array）被提到一种变量类型。数组可以由数字和字符串组成。数组的命名与变量类似，并且它具有持有多个值的能力。

示例：数组可以包含一个汽车列表，如下所示。

```php
$car1 = 'Toyota';
```

```php
$car2 = 'GM';
```

```php
$car3 = 'Ford';
```

```php
$car4 = 'Nissan';
```

数组变量命名规则如下：

- 1. 以`$`符号开头。
- 2. 以字母或下划线继续。
- 3. 以字母、数字或下划线的任意组合结束。

数组变量有一个索引。数组通过`[括号]`的存在与其他变量区分开来。因此，`$car[]`是一个数组变量。

`$car[3]`代表数组中索引位置 3 处的特定元素。

使用汽车示例在 PHP 中创建一个数组如下：

```php
$car = array('Toyota', 'GM', 'Ford', 'Nissan');
```

索引由 PHP 服务器自动分配。在这里，模型 Toyota 的索引为 0。数组索引自动从 0 开始。如果需要，可以更改此。

在汽车示例中，我们可以通过以下操作将模型 Toyota 具体放在索引位置 1。

```php
$car =array(1=>'Toyota', 2=>'GM', 3=>'Ford', 4=>'Nissan');
```

对于大多数用途，让 PHP 服务器以默认方式对值进行索引就足够了。

```php
<?php
print("This script will print an array of cars");
$car = array ('Toyota', 'GM', 'Ford', 'Nissan');
print "$car<p>";
print_r($car);
?>
```

运行此代码的输出如下：

![](img/d7e83bd680bb691d653bca3af472a71a_31_0.png)

上面的输出告诉了以下内容：

- 1. 无法使用前面章节中使用的`print`函数打印数组值。
- 2. 可以使用`print_r()`函数来打印数组值。
- 3. 使用`print_r()`函数时，数组将以数字格式显示其索引位置并打印。

索引位置没有要求必须是数字。可以使用单词。让我们修改上面的 PHP 代码来说明这一点：

```php
<?php
print"This script will print an array of cars";
$car = array ('Yaris'=>'Toyota', 'Spark'=>'GM',
'Escort'=>'Ford', 'Pathfinder'=>'Nissan'); print_r($car); ?>
```

此代码的输出将是：

![](img/d7e83bd680bb691d653bca3af472a71a_31_1.png)

输出更具描述性，因为在这些输出中模型被附加到不同的汽车公司。在数组的默认设置中，数组元素通过索引数字引用如下：`$car[2]`。

`range()`函数可以根据值的范围创建一个项目项的数组。例如：

```php
$num = range(1,20);
```

`$Alp = range('a', 'Z');`

`range`函数允许如下步长：

`$sum = range(10,20,2);`

当`var_dump()`函数与数组一起用用时，会显示数组的值和结构。让我们来看一段将演示这些函数的代码。

```php
<?php
print("This script will print an array of cars");
$car = array('Yaris'=>'Toyota', 'Spark'=>'GM',
'Escort'=>'Ford', 'Pathfinder'=>'Nissan');
var_dump($car);
$sum=range(10,20,2);
print('<br>');
$Alp=range('a','Z');
print_r($sum);
print('<br>');
print_r($Alp);
?>
```

输出如下：

![](img/d7e83bd680bb691d653bca3af472a71a_32_0.png)

键为数组称为索引数组（indexed array），带有字符串的数组称为关联数组（associative array）。这两种类型在上面的示例中已经说明。可以向数组中添加更多元素。在上面的示例中，一旦在 PHP 中定义了数组，就可以通过等号和数组名配合`[括号]`来添加更多元素。

示例：

`$car[]='Mazda';`

`$car[]='Hyundai';`

如果在括号中未指定键，则数组的每个新条目元素都将附加到现有列表中。如果括号中提到了键，该索引处的任何值都将被删除，并将新元素添加到该位置。

```php
<?php
print("This script will print an array of cars");
$car = array('Toyota', 'GM', 'Ford', 'Nissan');
$car[1] = 'Mazda';
$car[3] = 'Hyundai';
print_r($car);
?>
```

![](img/d7e83bd680bb691d653bca3af472a71a_33_0.png)

输出将如上所示将新公司添加到列表末尾。让我们如下修改上面的脚本：

```php
<?php
print("This script will print an array of cars");
$car = array('Toyota', 'GM', 'Ford', 'Nissan');
$num1 = count($car);
print("The original array has " . $num1 . "<br>");
$car[1] = 'Mazda';
$car[3] = 'Hyundai';
print_r($car);
$num2 = count($car);
?>
```

![](img/d7e83bd680bb691d653bca3af472a71a_33_1.png)

输出所示。上述代码中的额外函数是`count()`，它用于计算数组元素的数量。要从数组中删除单个元素使用`unset()`函数。例如：

```php
unset($car[4]);
```

```php
unset($car['name']);
```

应用于整个数组时整个数组将被删除。要重置数组而不删除数组变量，使用`array()`函数。例如：

```php
$car =array();
```

看下面的代码。

```php
<?php
print"This script will print an array of cars";
$car = array('Toyota', 'GM', 'Ford', 'Nissan');
unset($car[2]);
print_r($car);
?>
```

索引值 2 现在已删除。PHP 有一个函数可以合并两个数组。`array_merge($array1,$array2)`可用于此目的。两个数组名称必须输入到括号中。示例：

`$car1[]='Toyota','GM','Ford';`
`$car2[]='Nissan','Mazda','VW','Hyundai';`

以这种方式编写代码将合并这两个数组。

```php
<?php
print"This script will print an array of cars";
$car1[]='Toyota','GM','Ford';
$car2[]='Nissan','Mazda','VW','Hyundai';
$car3=array_merge($car1,$car2);
print_r($car3);
?>
```

上面的两个数组合并也可以通过如下写法实现。

`$car3 = $car1 + $car2;`

检索数组元素的唯一方法是指定键的索引值。如果需要打印数组的所有元素，将需要一个循环。例如：

```php
<?php
$salary = array ('Adam'=>1000, 'Smith'=>2000, 'Mary'=>2500, 'Sally'=>1800);
print("The original array looks like this. <br>");
foreach($salary as $emp => $amount){
print("$emp:$amount<br>");
}
?>
```

此代码的输出将像这样。

![](img/d7e83bd680bb691d653bca3af472a71a_35_0.png)

```php
<?php
print("原始数组看起来如下：<br>");
foreach($salary as $amount){
    print($amount<br>");
}
?>
```

让我们来看一个没有显示键的示例。

```php
<?php
$name = array('Tom','Harry','Smith','Adam');
print("原始数组看起来如下：<br>");
foreach($name as $emp){
    print($emp<br>");
}
?>
```

输出如下。

![](img/d7e83bd680bb691d653bca3af472a71a_36_0.png)

可以使用以下函数对数组排序：

- `sort()` - 此函数按值排序，但不保留键值。
- `rsort()` - 此函数反转值，且不保留键值。
- `asort()` - 这些函数按值排序并会保留键值。
- `arsort()` - 值按逆序方式排序，并且会保留键值。
- `ksort()` - 按键排序，并会保留键值。
- `krsort()` - 按键进行逆序排序，并会保留键值。

让我们来看一个示例：

```php
<?php
$salary = array('Adam'=>1000, 'Smith'=>2000, 
'Mary'=>2500, 'Sally'=>1800);
print("原始数组看起来如下：<br>");
foreach($salary as $emp => $amount) {
    print($emp:$amount<br>");
}
print("使用 sort() 排序的结果如下：<br>");
sort($salary);
foreach($salary as $emp => $amount) {
    print($emp:$amount<br>");
}
print("使用 rsort() 排序的结果如下：<br>");
rsort($salary);
foreach($salary as $emp => $amount) {
    print($emp:$amount<br>");
}
?>
```

输出将如下。

![](img/d7e83bd680bb691d653bca3af472a71a_37_0.png)

其他排序函数的代码在下方。

```php
<?php
$salary = array('Adam'=>1000, 'Smith'=>2000, 
'Mary'=>2500, 'Sally'=>1800);
print("使用 asort() 排序的结果如下：<br>");
asort($salary);
foreach($salary as $emp => $amount) {
    print($emp:$amount<br>");
}
print("使用 arsort() 排序的结果如下：<br>");
arsort($salary);
foreach($salary as $emp => $amount) {
    print($emp:$amount<br>");
}
?>
```

输出如下。

![](img/d7e83bd680bb691d653bca3af472a71a_38_0.png)

原始数组看起来如下：
Adam:1000
Smith:2000
Mary:2500
Sally:1800

使用 sort() 排序的结果：
Adam:1000
Sally:1800
Smith:2000
Mary:2500

使用 asort() 排序的结果：
Mary:2500
Sally:1800
Smith:2000
Adam:1000

要按键排序，我们使用前面列出的最后几个排序函数：

```php
<?php
$salary = array('Adam'=>1000, 'Smith'=>2000, 'Mary'=>2500, 'Sally'=>1800);
print("使用 ksort 排序的结果如下：<br>");
ksort($salary);
foreach($salary as $emp => $amount) {
    print("$emp:$amount<br>");
}
print("使用 krsort 排序的结果如下：<br>");
krsort($salary);
foreach($salary as $emp => $amount) {
    print("$emp:$amount<br>");
}
?>
```

输出将如下。

![](img/d7e83bd680bb691d653bca3af472a71a_39_0.png)

使用 ksort() 排序的结果：
Adam:1000
Mary:2500
Sally:1800
Smith:2000

使用 krsort() 排序的结果：
Smith:2000
Sally:1800
Mary:2500
Adam:1000

`shuffle()`函数会随机重组数组的顺序。

可以使用以下代码查看其工作原理。

```php
<?php
$salary = array ('Adam'=>1000, 'Smith'=>2000, 'Mary'=>2500, 'Sally'=>1800);
print("shuffle() 的结果如下：<br>");
shuffle($salary);
foreach($salary as $emp => $amount) {
    print("$emp:$amount<br>");
}
?>
```

```php
<?php
print(">");
var_dump($books);
?>
```

输出如下。

![](img/d7e83bd680bb691d653bca3af472a71a_44_0.png)

# 第 5 章 Web 应用程序组件

PHP 文件的主题至少需要 HTML 知识。除了这些知识外，层级样式表（CSS）、JavaScript 和结构化查询语言（SQL）可以极大地增强创建动态、美观网页的能力。

本书将不会详细介绍 CSS 或 JavaScript 的开发。然而，在本书的数据库部分，将提供 SQL 的基本背景知识。

在本章中，我们将查看制作 Web 应用程序的一些组件。

PHP 程序可以使用外部文件。例如，为页面创建头部（header）或页脚（footer）。要这样做，首先创建一个`header.html`和`footer.html`文件，这些文件也可以是 PHP 文件。

可以使用两个函数之一`include()`和`require()`将这些外部文件包含在 PHP 程序中。它们的使用方式如下：

```php
include('footer.html');
```

或者

```php
include('footer.php');
```

或者

```php
require('header.html');
```
