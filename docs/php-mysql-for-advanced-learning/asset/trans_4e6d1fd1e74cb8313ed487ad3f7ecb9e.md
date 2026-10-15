
## PHP 中的函数

PHP 中的函数与 C 或其他编程语言中的函数行为相似。当我们定义函数时，必须指定函数可以期望接收什么值。

那么让我们创建一个函数。我们需要给函数一个名称并告诉它期望什么变量。我们还需要在调用它之前定义函数。

当你使用任何函数时，它会提供完整的参考，例如使用该函数需要多少个输入或值。假设如果我要创建并使用一个函数，它需要两个输入，即

```php
<?php

function sum($a, $b)
{
$output=$a+$b;
echo "Sum is ".$output;
}

sum(10,5);  // Calling a PHP function
?>
```

上述 sum 函数接受两个值，在技术术语中

我们称之为参数，函数返回的和为

我分配的数字。因此，从上述函数我们了解到：

- 函数名称是 sum
- 函数接受两个值或参数
- 函数返回数值输出

如果你计划创建接受多个参数并返回某种固定格式输出的函数，那么 PHP 函数可能是最佳选择。

除了用户创建的函数外，PHP 中还有一些预定义或内置函数，我们将在下一教程中学习。

Hirdesh Bhardwaj

## 备注

## PHP - 构建块

### If-else 语句

if…else 语句 – 如果条件为真则执行一组代码，如果条件为假则执行另一段代码

在语句中，如果某个条件为真，则会发生某事。否则，会发生其他事情。我们可以根据需要继续添加任意多次 else 语句。

> 简而言之，“*IF Else 语句检查指定的条件是否得到满足。*”

### 语法

```
if (condition)
    code to be executed if condition is true;

elseif (condition)

    code to be executed if condition is true;

else

    code to be executed if condition is false;
```

**条件运算符：** 有时也称为比较运算符，用于比较和测试逻辑和表达式。

以下是条件运算符：

- = 等于
- > 大于
- < 小于
- >= 大于等于
- <= 小于等于
- != 或 <> 不等于

### 逻辑运算符：

逻辑运算符用于组合多个语句并测试条件是否满足为真/假。

以下是逻辑运算符：

- And 或 && - 所有条件必须为真
- Or || - 至少一个应为真
- Xor - 一侧或另一侧必须为真但不能同时为真
- == 比较运算符

*请注意 = 是赋值运算符，而 == 是 PHP 中的比较运算符。*

### 基本 If else 示例 1

```php
<?php
$avg = 50;
if ($avg>60)
{
echo "You have a good score";
}
else
{
echo "Score is less than average";
}
?>
```

上述程序将返回“Score is less than average”，因为变量 $avg 的值为 50。

### 示例 2：

```php
<?php
$status = 1;

if ($status == 1)
{
print ("<img src =images/right.jpg>");
}
else
{
print ("<img src =images/cross.jpg>");
}
?>
```

变量 $status 已被赋值为 1。if 语句的第一行测试变量 $status 中包含的内容。它正在测试该变量是否具有值 1。

### 示例 3：

```php
<?php

// Below line returns month (1-12) from current date
$month=date("n");
if ($month==1 || $month==3 || $month==5 || $month==7 ||
$month==8 || $month==10 || $month==12 )
{
echo "31 Days";
}
else if ($month==2)
{
echo "28 or 29 Days";
}
else
{
echo "30 Days";
}
?>
```

我们通过使用内置的 date 函数来获取变量 $month 的值。date("n") 返回服务器上设置的当前月份的数值（1 到 12），例如 1 代表一月，2 代表二月，以此类推。

Hirdesh Bhardwaj

## PHP 中的循环

循环无疑是任何编程语言中最强大的组件之一。循环只是一组重复执行多次的语句。

可能存在需要多次执行一段代码的情况。

但如果你一遍又一遍地运行相同的代码，结果会相同。那么在这种情况下使用循环有什么好处呢？

基本上，循环包含一个每次略有变化的变量。

PHP 中有几种类型的循环：

- For 循环
- For Each 循环
- Do while 循环
- While 循环

### For 循环

PHP for 循环可用于在指定次数内遍历代码集。例如，如果你想重复某件事十次或二十次。

如果迭代或重复次数已知，则应使用它，否则我建议你使用 while 循环。

### For 循环语法

```
for (Initialization; Condition; Progressive)
{
    //set of statements to be executed;
}
```

### 参数说明：

Initialization: 初始化循环计数器的值

Hirdesh Bhardwaj

**条件**：检查条件。如果它求值为 TRUE，则循环继续。如果为 FALSE，则循环结束。

**递增**：增加/减少循环计数器的值

### For 循环示例 1：

```php
<?php
for($var=1; $var<=20; $var=$var+1)
{
echo $var . " ";
}
?>
```

**输出：**

1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

从上面的例子来看，$var=$var+1 语句可以简化为类似 $var++ 的形式

### 示例 2：显示前 20 个自然数在下拉列表中

```php
<?php

echo "<select>";

for($i=1; $i<=20; $i++)
{
echo "<option>".$i. "</option>";
}
echo "</select>";

?>
```

请注意，在循环区域内，我们使用变量 $i 在下拉列表中显示值（在 HTML 中称为 Select Option 字段），因为我们使用每次略有变化的变量。

### 嵌套 For 循环：

我们可以在 PHP 中在另一个 for 循环内使用 for 循环，这称为嵌套 for 循环。对于内部或嵌套循环而言，嵌套 for 循环会为一次外部 for 循环完全执行。

例如，如果外部循环 i 要执行 2 次，嵌套内部循环执行 2 次，则嵌套内部循环将执行 4 次（1 次外部循环执行 2 次，2 次外部循环执行 2 次）。

所以下面是 PHP 嵌套 for 循环的示例，用于设计三角形形状的输出

### For 循环示例 3：

```php
<?php
for($i=1; $i<=5; $i++)
{
for($j=1; $j<=$i; $j++)
{
echo $j. " ";
}
echo "<br>";
}
?>
```

### 输出

- 1
- 1 2
- 1 2 3
- 1 2 3 4
- 1 2 3 4 5

### 反向 For 循环：

在 PHP 中，你也可以从较高值到较低值使用 For 循环。要实现这一点，我们需要在递增中提及负数。

```php
<?php
for($var=10; $var>=1; $var=$var-1)
{
    echo $var . " ";
} ?>
```

输出：10 9 8 7 6 5 4 3 2 1

### While 循环

While 循环用于在条件为假时重复执行一组语句。当重复次数事先未知时，它可能是最佳选择。

可以用通俗英语解释为“*一直做某事，直到条件为真*。”

### 语法

```
while (condition)
{
    // Set of statements goes here;
}
```

### While 循环示例 1

```php
<?php
$ct=5;
while($ct<=50)
{
echo $ct ."<br>";
$ct = $ct+5;
}
?>
```

### 输出：

5 10 15 20 25 30 35 40 45 50

### PHP 中的 do...While 循环

do..while 循环几乎与 while 循环相似，但它们之间有一个主要区别。do...while 循环将始终至少执行一次代码块。

### while 和 do...while 循环之间的区别：

对于 while 循环，待评估的条件在每次循环语句开始时进行测试，因此如果条件表达式求值为 false，循环将永远不会执行。

另一方面，对于 do-while 循环，即使条件表达式为 false，循环也总是会执行一次，因为条件是在循环语句结束时评估的。

Hirdesh Bhardwaj

### do...while 循环示例：

```php
<?php
$i = 1;
do
{
    $i++;
    echo $i . "<br>";
}
while($i <= 3);
?>
```

输出：2 3 4
