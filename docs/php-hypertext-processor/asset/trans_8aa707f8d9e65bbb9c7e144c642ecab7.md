

?>
</body>
</html>

This will produce the following result:

```
Loop stopped at i = 10 and num = 40
```

## do...while 循环语句

do...while 语句至少会执行一次代码块，然后只要条件为真就会重复循环。

### 语法

```
do
{
    code to be executed;
}while (condition);
```

### 示例

以下示例将 i 的值至少递增一次，并且只要变量 i 的值小于 10 就会继续递增：

```
<html>
<body>
<?php
$i = 0;
$num = 0;
do
{
    $i++;
}while( $i < 10 );
echo ("Loop stopped at i = $i" );
?>
</body>
</html>
```

This will produce the following result:

```
Loop stopped at i = 10
```

## foreach 循环语句

foreach 语句用于遍历数组。在每次迭代中，当前数组元素的值会被赋给 $value，数组指针向后移动一位，在下一次迭代中将处理下一个元素。

### 语法

```
foreach (array as value)
{
   code to be executed;
}
```

### 示例

尝试以下示例来列出数组的值。

```
<html>
<body>
  <?php
   $array = array( 1, 2, 3, 4, 5);
   foreach( $array as $value )
   {
      echo "Value is $value <br />";
   }
  ?>
</body>
</html>
```

This will produce the following result:

```
Value is 1
Value is 2
Value is 3
Value is 4
Value is 5
```

## break 语句

PHP 的 break 关键字用于提前终止循环的执行。

break 语句位于语句块内部。它为你提供完全控制权，无论何时想要退出循环都可以跳出。跳出循环后，紧跟在循环之后的语句将被执行。

![](img/b9c80e155ac304a53696823920b08082_55_0.png)

### 示例

在以下示例中，当计数器值达到 3 时条件测试变为真，循环终止。

```
<html>
<body>

<?php
$i = 0;

while( $i < 10)
{
   $i++;
   if( $i == 3 )break;
}
echo ("Loop stopped at i = $i" );
?>
</body>
</html>
```

This will produce the following result:

> 循环在 i = 3 时停止

## continue 语句

PHP 的 **continue** 关键字用于中断当前循环迭代，但不会终止循环。

与 **break** 语句一样，**continue** 语句也位于循环执行的代码所在语句块内部，并前置条件测试。在遇到 **continue** 语句的那次迭代中，其余循环代码将被跳过，并开始下一次迭代。

![](img/b9c80e155ac304a53696823920b08082_56_0.png)

### 示例

在以下示例中，循环打印数组的值，但当条件变为真时，它只是跳过代码并打印下一个值。

```
<html>
<body>
<?php
$array = array( 1, 2, 3, 4, 5);
foreach( $array as $value )
{
   if( $value == 3 )continue;
   echo "Value is $value <br />";
}
?>
</body>
</html>
```

This will produce the following result:

```
Value is 1
Value is 2
Value is 4
Value is 5
```

数组是一种在单个值中存储一个或多个相同类型值的数据结构。例如，如果你想存储 100 个数字，那么定义 100 个变量不如定义一个长度为 100 的数组来得容易。

有三种不同类型的数组，每个数组值都使用一个称为数组索引的 ID 来访问。

- **数值数组** - 带有数值索引的数组。值以线性方式存储和访问
- **关联数组** - 以字符串作为索引的数组。它按键值关联存储元素值，而不是按严格的线性索引顺序。
- **多维数组** - 包含一个或多个数组的数组，值通过多个索引来访问

**注意：** 内置数组函数列于函数参考 PHP Array Functions 中

## 数值数组

这些数组可以存储数字、字符串和任何对象，但其索引将由数字表示。默认情况下，数组索引从零开始。

### 示例

以下示例演示如何创建和访问数值数组。

这里我们使用了 **array()** 函数来创建数组。该函数在函数参考中有说明。

```
<html>
<body>
<?php
/* First method to create array. */
$numbers = array( 1, 2, 3, 4, 5);
foreach( $numbers as $value )
{
   echo "Value is $value <br />";
}
/* Second method to create array. */
$numbers[0] = "one";
$numbers[1] = "two";
$numbers[2] = "three";
$numbers[3] = "four";
$numbers[4] = "five";

foreach( $numbers as $value )
{
    echo "Value is $value <br />";
}
?>
</body>
</html>
```

This will produce the following result:

```
Value is 1
Value is 2
Value is 3
Value is 4
Value is 5
Value is one
Value is two
Value is three
Value is four
Value is five
```

## 关联数组

关联数组在功能上与数值数组非常相似，但在索引方面有所不同。关联数组将字符串作为索引，以便你可以在键和值之间建立强关联。

若要在数组中存储员工薪资，数值索引数组并非最佳选择。相反，我们可以使用员工姓名作为关联数组中的键，值则为其各自的薪资。

**注意：** 打印时不要将关联数组放在双引号内，否则将不会返回任何值。

### 示例

```
<html>
<body>
<?php
/* First method to create associative array. */
$salaries = array(
   "mohammad" => 2000,
   "qadir" => 1000,
   "zara" => 500
);

echo "Salary of mohammad is ". $salaries['mohammad'] . "<br />";
echo "Salary of qadir is ". $salaries['qadir'] . "<br />";
echo "Salary of zara is ". $salaries['zara'] . "<br />";

/* Second method to create array. */
$salaries['mohammad'] = "high";
$salaries['qadir'] = "medium";
$salaries['zara'] = "low";

echo "Salary of mohammad is ". $salaries['mohammad'] . "<br />";
echo "Salary of qadir is ". $salaries['qadir'] . "<br />";
echo "Salary of zara is ". $salaries['zara'] . "<br />";
?>
</body>
</html>
```

This will produce the following result:

```
Salary of mohammad is 2000
Salary of qadir is 1000
Salary of zara is 500
Salary of mohammad is high
Salary of qadir is medium
Salary of zara is low
```

## 多维数组

在多维数组中，主数组的每个元素也可以是一个数组。子数组的每个元素也可以是一个数组，以此类推。多维数组中的值使用多个索引来访问。

### 示例

在此示例中，我们创建一个二维数组来存储三名学生在三门科目中的成绩：

此示例是一个关联数组，你可以用同样的方式创建数值数组。

```
<html>
<body>
<?php
   $marks = array(
      "mohammad" => array
      (
         "physics" => 35,
         "maths" => 30,
         "chemistry" => 39
      ),
      "qadir" => array
      (
         "physics" => 30,
         "maths" => 32,
         "chemistry" => 29
      ),
      "zara" => array
      (
         "physics" => 31,
         "maths" => 22,
         "chemistry" => 39
      )
   );
   /* Accessing multi-dimensional array values */
   echo "Marks for mohammad in physics : ";
   echo $marks['mohammad']['physics'] . "<br />";
   echo "Marks for qadir in maths : ";
   echo $marks['qadir']['maths'] . "<br />";
   echo "Marks for zara in chemistry : ";
   echo $marks['zara']['chemistry'] . "<br />";
?>
</body>
</html>
```

This will produce the following result:

```
Marks for mohammad in physics : 35
Marks for qadir in maths : 32
Marks for zara in chemistry : 39
```

## 10. PHP – 字符串

它们是字符序列，例如 "PHP supports string operations"。

注意：内置字符串函数列于函数参考 PHP String Functions 中

字符串的一些有效示例如下：

```
$string_1 = "This is a string in double quotes";
$string_2 = "This is a somewhat longer, singly quoted string";
$string_39 = "This string has thirty-nine characters";
$string_0 = ""; // a string with zero characters
```

单引号字符串几乎按原义处理，而双引号字符串会将变量替换为其值，并特殊解释某些字符序列。

```
<?
$variable = "name";
$literally = 'My $variable will not print!\n';
print($literally);
$literally = "My $variable will print!\n";
print($literally);
?>
```

This will produce the following result:

```
My $variable will not print!\n
My name will print
```

字符串长度没有人为限制 - 在可用内存范围内，你应该能够创建任意长的字符串。

由双引号分隔的字符串（如 "this"）会被 PHP 以以下两种方式预处理：

- 以反斜杠 (\) 开头的某些字符序列会被替换为特殊字符
- 变量名（以 $ 开头）会被替换为其值的字符串表示形式。

转义序列替换如下：

- \n 会被替换为换行字符
- \r 会被替换为回车字符
- \t 会被替换为制表符

