

这将产生以下结果：

```
Addition Operation Result: 62
Add AND Assignment Operation Result: 104
Subtract AND Assignment Operation Result: 62
Multiply AND Assignment Operation Result: 2604
Division AND Assignment Operation Result: 62
Modulus AND Assignment Operation Result: 20
```

### 条件运算符

还有一个称为条件运算符的运算符。它首先对表达式求值以获得真或假值，然后根据求值结果执行两个给定语句中的一个。

| 运算符 | 描述 | 示例 |
| :--- | :--- | :--- |
| ? : | 条件表达式 | 如果条件为真？则值 X：否则值 Y |

尝试以下示例以理解条件运算符。将以下 PHP 程序复制并粘贴到 test.php 文件中，将其保存在 PHP 服务器的文档根目录下，并使用任意浏览器访问。

```
<html>
<head><title>Arithmetical Operators</title></head>
<body>
<?php
$a = 10;
$b = 20;

/* If condition is true then assign a to result otherwise b */
$result = ($a > $b ) ? $a:$b;
echo "TEST1 : Value of result is $result<br/> ";

/* If condition is true then assign a to result otherwise b */
$result = ($a < $b ) ? $a:$b;
echo "TEST2 : Value of result is $result<br/> ";

?>
</body>
</html>
```

这将产生以下结果：

```
TEST1 : Value of result is 20
TEST2 : Value of result is 10
```

### 运算符类别

我们上面讨论的所有运算符都可以分为以下类别：

- 一元前缀运算符，作用于单个操作数。
- 二元运算符，接受两个操作数并执行各种算术和逻辑运算。
- 条件运算符（三元运算符），接受三个操作数，并根据第一个表达式的求值结果，对第二个或第三个表达式求值。
- 赋值运算符，将值赋给变量。

### PHP 运算符优先级

运算符优先级决定表达式中项的分组。这会影响表达式的求值方式。某些运算符的优先级高于其他运算符；例如，乘法运算符的优先级高于加法运算符：

例如，x = 7 + 3 * 2；这里 x 被赋值为 13，而不是 20，因为运算符 * 的优先级高于 +，因此它先对 3*2 进行乘法运算，然后再加上 7。

此处优先级最高的运算符出现在表格顶部，优先级最低的出现在底部。在表达式中，优先级较高的运算符会先被求值。

| 类别 | 运算符 | 结合性 |
|---|---|---|
| 一元 | ! ++ -- | 从右到左 |
| 乘法 | * / % | 从左到右 |
| 加法 | + - | 从左到右 |
| 关系 | < <= > >= | 从左到右 |
| 相等 | == != | 从左到右 |
| 逻辑 AND | && | 从左到右 |
| 逻辑 OR | || | 从左到右 |
| 条件 | ?: | 从右到左 |
| 赋值 | = += -= *= /= %= | 从右到左 |

## 7. PHP – 决策判断

if、elseif ...else 和 switch 语句用于根据不同条件进行决策判断。

您可以在代码中使用条件语句来做出决策。PHP 支持以下三种决策判断语句：

- **if...else 语句** - 当条件为真时要执行一组代码，否则执行另一组代码，请使用此语句
- **elseif 语句** - 与 if...else 语句一起使用，当多个条件中有一个为真时执行一组代码
- **switch 语句** - 当您想从多个代码块中选择一个执行时，请使用 Switch 语句。switch 语句用于避免冗长的 if...elseif..else 代码块。

### If...Else 语句

如果条件为真时要执行一些代码，条件为假时要执行另一些代码，请使用 if...else 语句。

### 语法

```
if (condition)
code to be executed if condition is true;
else
code to be executed if condition is false;
```

### 示例

以下示例如果当前是星期五，则输出 "Have a nice weekend!"，否则输出 "Have a nice day!"：

```
<html>
<body>
<?php
$d=date("D");
if ($d=="Fri")
echo "Have a nice weekend!";
else
echo "Have a nice day!";
?>
</body>
</html>
```

它将产生以下结果：

![](img/b9c80e155ac304a53696823920b08082_47_0.png)

### Elseif 语句

如果多个条件中有一个为真时要执行一些代码，请使用 elseif 语句。

### 语法

```
if (condition)
  code to be executed if condition is true;
elseif (condition)
  code to be executed if condition is true;
else
  code to be executed if condition is false;
```

### 示例

以下示例如果当前是星期五，则输出 "Have a nice weekend!"，如果当前是星期日，则输出 "Have a nice Sunday!"。否则输出 "Have a nice day!"：

```
<html>
<body>
    <?php
    $d=date("D");
    if ($d=="Fri")
    echo "Have a nice weekend!";
elseif ($d=="Sun")
 echo "Have a nice Sunday!";
else
 echo "Have a nice day!";
?>
</body>
</html>
```

它将产生以下结果：

```
Have a nice weekend!
```

### Switch 语句

如果要从多个代码块中选择一个执行，请使用 Switch 语句。switch 语句用于避免冗长的 if..elseif..else 代码块。

### 语法

```
switch (expression)
{
case label1:
 code to be executed if expression = label1;
 break;
case label2:
 code to be executed if expression = label2;
 break;
default:
 code to be executed
 if expression is different
 from both label1 and label2;
}
```

### 示例

`switch` 语句的工作方式不寻常。首先它对给定表达式求值，
然后寻找与结果值匹配的标签。如果找到匹配值，则执行与匹配标签关联的代码。如果没有标签匹配，则
该语句将执行指定的任何默认代码。

```
<html>
<body>
 <?php
$d=date("D");
switch ($d)
{
case "Mon":
echo "Today is Monday";
break;
case "Tue":
echo "Today is Tuesday";
break;
case "Wed":
echo "Today is Wednesday";
break;
case "Thu":
echo "Today is Thursday";
break;
case "Fri":
echo "Today is Friday";
break;
case "Sat":
echo "Today is Saturday";
break;
case "Sun":
echo "Today is Sunday";
break;
default:
echo "Wonder which day is this ?";
}
 ?>
 </body>
</html>
```

它将产生以下结果：

```
Today is Friday
```

## 8. PHP – 循环类型

PHP 中的循环用于按指定次数执行相同的代码块。PHP 支持以下四种循环类型。

- **for** - 循环执行代码块指定次数。
- **while** - 只要指定条件为真，就循环执行代码块。
- **do...while** - 先循环执行一次代码块，然后只要特定条件为真就重复循环。
- **foreach** - 为数组中的每个元素循环执行代码块。

我们将讨论用于控制循环执行的 **continue** 和 **break** 关键字。

### for 循环语句

当您知道要执行语句或语句块多少次时，使用 for 语句。

### 语法

```
for (initialization; condition; increment)
{
   code to be executed;
}
```

初始化用于设置循环迭代次数计数器的起始值。可以在此处为此目的声明一个变量，传统上将其命名为 $i。

### 示例

以下示例进行五次迭代，并在每次循环中更改两个变量的赋值：

```
<html>
<body>
<?php
$a = 0;
$b = 0;

for( $i=0; $i<5; $i++ )
{
   $a += 10;
   $b += 5;
}
echo ("At the end of the loop a=$a and b=$b" );
?>
</body>
</html>
```

这将产生以下结果：

```
At the end of the loop a=50 and b=25
```

### while 循环语句

while 语句仅在测试表达式为真时才执行代码块，并且只要条件为真就继续执行。如果测试表达式为真，则执行代码块。代码执行后，将再次求值测试表达式，循环将继续直到测试表达式的值为假。

### 语法

```
while (condition)
{
   code to be executed;
}
```

### 示例

此示例在每次循环迭代时递减变量值，计数器递增直到达到 10，此时求值结果为假且循环结束。

```
<html>
<body>
<?php
$i = 0;
$num = 50;
while( $i < 10)
{
   $num--;
   $i++;
}
echo ("Loop stopped at i = $i and num = $num" );

