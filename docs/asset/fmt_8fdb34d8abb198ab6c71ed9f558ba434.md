
```html
<html>
  <body>
      <?php
        $a = 0;
        $b = 0;
        for( $i = 0; $i<5; $i++ ) {
            $a += 10;
            $b += 5;
        }
        echo ("At the end of the loop a = $a and b = $b" );
      ?>
  </body>
</html>
```

这将产生以下结果 —

At the end of the loop a = 50 and b = 25

## while 循环语句

`while` 语句当测试表达式为真时且只要它为真，就会执行代码块。如果测试表达式为真，则将执行代码块。代码执行后，将再次评估测试表达式，循环将持续直到测试表达式为假。

![PHP 中的 for 循环](img/image00550.jpeg)

### 语法

```php
while (condition) {
   // 要执行的代码;
}
```

## 示例

此示例在循环的每次迭代中变量值减 1，计数器不断增加，直到达到 10 时，评估结果为假，循环结束。

```html
<html>
  <body>
      <?php
        $i = 0;
        $num = 50;
        while($i < 10) {
            $num--;
            $i++;
        }
        echo ("Loop stopped at i = $i and num = $num" );
      ?>
  </body>
</html>
```

这将产生以下结果 —

Loop stopped at i = 10 and num = 40

## do...while 循环语句

`do...while` 语句至少执行一次代码块 — 只要条件为真，它就会重复循环。

### 语法

```php
do {
   // 要执行的代码;
} while (condition);
```

## 示例

以下示例至少增加一次 `$i` 的值，只要 `$i` 的值小于 10，它就会继续增加变量 `$i` —

```html
<html>
  <body>
      <?php
        $i = 0;
        $num = 0;
        do {
            $i++;
        } while($i < 10 );
        echo ("Loop stopped at i = $i" );
      ?>
  </body>
</html>
```

这将产生以下结果 —

Loop stopped at i = 10

## foreach 循环语句

`foreach` 语句用于遍历数组。在每次通过时，数组元素的值被赋值给 `$value`，数组指针移动一位，下一次通过将处理下一个元素。

### 语法

```php
foreach (array as value) {
   // 要执行的代码;
}
```

## 示例

尝试以下示例来列出数组的值。

```html
<html>
  <body>
      <?php
        $array = array( 1, 2, 3, 4, 5);
        foreach( $array as $value ) {
            echo "Value is $value <br />";
        }
      ?>
  </body>
</html>
```

这将产生以下结果 —

Value is 1

Value is 2

Value is 3

Value is 4

Value is 5

## break 语句

PHP `break` 关键字用于提前终止循环的执行。`break` 语句位于语句块内部。它让你拥有完全的控制权，每当你想退出循环时，都可以离开。退出循环后，将执行循环后的后续语句。

![PHP break 语句](img/image00551.jpeg)

## 示例

在以下示例中，当计数器值达到 3 时，条件测试变为真，循环终止。

```html
<html>
  <body>
      <?php
        $i = 0;
        while( $i < 10) {
            $i++;
            if( $i== 3 )break;
        }
        echo ("Loop stopped at i = $i" );
      ?>
  </body>
</html>
```

这将产生以下结果 —

Loop stopped at i = 3

## continue 语句

PHP `continue` 关键字用于停止循环的当前迭代，但它不会终止循环。与 `break` 语句一样，`continue` 语句位于包含循环代码的语句块内部。`continue` 语句跳过后续代码并开始下一次迭代。

![Continue 语句](img/image00552.jpeg)

## 示例

以下示例打印数组的值，但当条件为真时会跳过后续代码。

```html
<html>
  <body>
      <?php
        $array = array( 1, 2, 3, 4, 5);
        foreach( $array as $value ) {
            if($value== 3 )continue;
            echo "Value is $value <br />";
        }
      ?>
  </body>
</html>
```

此将产生以下结果 —

Value is 1

Value is 2

Value is 4

Value is 5

# PHP - 数组

数组是一种存储单个变量中多个相同类型值的数据结构。例如，如果你想存储 100 个数字，比定义 100 个变量要简单得多。

- 数字数组 — 具有数字索引的数组。值以线性方式存储。
- 关联数组 — 以字符串作为索引的数组。存储键值关联，而不是严格的线性顺序。
- 多维数组 — 包含多个数组的数组，可以使用多个索引访问。

注意 — 内置数组函数请函数参考。

## 数字数组

这些数组可以存储数字、字符串和任何对象，但它们的索引由数字表示。默认情况下索引从 0 开始。

## 示例

以下是如何创建和访问数字数组的示例。在这里我们 `array()` 函数来创建数组。该函数在函数参考中有解释。

```html
<html>
  <body>
      <?php
        /* 第一种创建数组的方法 */
        $numbers = array( 1, 2, 3, 4, 5);
        foreach( $numbers as $value ) {
            echo "Value is $value <br />";
        }
        /* 第二种创建数组的方法 */
        $numbers[0] = "one";
        $numbers[1] = "two";
        $numbers[2] = "three";
        $numbers[3] = "four";
        $numbers[4] = "five";
        foreach( $numbers as $value ) {
            echo "Value is $value <br />";
        }
      ?>
  </body>
</html>
```

这将产生以下结果 —

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

## 关联数组

关联数组在功能上与数字数组非常相似，但在索引方面有所不同。关联数组将索引设为字符串，以便你可以在键和值之间建立强关联。

要在数组中存储员工的薪水，数字索引数组不是最佳选择。相反，我们可以使用员工名称作为关联数组的键，而值则是他们相应的薪水。

注意 - 打印时不要在双引号内保留关联数组，否则它将不会返回任何值。

## 示例

```html
<html>
  <body>
      <?php
        /* 创建关联数组的í种方法。 */
        $salaríes = array("mohammad" => 2000, "qadír" => 1000, "zara" => 500);
        echo "Salary of mohammad ís ". $salaríes['mohammad'] . "<br />";
        echo "Salary of qadír ís ".  $salaríes['qadír']. "<br />";
        echo "Salary of zara ís ".  $salaríes['zara']. "<br />";
        /* 创建数组的第二种方法。 */
        $salaríes['mohammad'] = "hígh";
        $salaríes['qadír'] = "medíum";
        $salaríes['zara'] = "low";
        echo "Salary of mohammad ís ". $salaríes['mohammad'] . "<br />";
        echo "Salary of qadír ís ".  $salaríes['qadír']. "<br />";
        echo "Salary of zara ís ".  $salaríes['zara']. "<br />";
      ?>
  </body>
</</html>
```

这将产生以下结果 ―

Salary of mohammad ís 2000

Salary of qadír ís 1000

Salary of zara ís 500

Salary of mohammad ís hígh

Salary of qadír ís medíum

Salary of zara ís low

## 多维数组

在多维数组中，主数组中的每个元素也可以是数组。子数组中的每个元素可以是数组，以此此类推。多维数组中的值通过多个索引来访问。

## 示例

在这个示例中，我们创建了一个二维数组来存储三个学生在三门科目中的分数 ；

此示例是一个关联数组，你可以以相同的方式创建数值数组。

```html
<html>
  <body>
      <?php
        $marks = array( 
          "mohammad" => array (
              "physícs" => 35,
              "maths" => 30,
              "chemístry" => 39
          ),
          "qadír" => array (
              "physícs" => 30,
              "maths" => 32,
              "chemístry" => 29
          ),
          "zara" => array (
              "physícs" => 31,
              "maths" => 22,
              "chemístry" => 39
          )
        );
        /* 访问多维数组的值 */
        echo "Marks for mohammad ín physícs : " ;
        echo $marks['mohammad']['physícs'] . "<br />"; 
        echo "Marks for qadír ín maths : ";
        echo $marks['qadír']['maths'] . "<br />"; 
        echo "Marks for zara ín chemístry : ";
        echo $marks['zara']['chemístry'] . "<br />"; 
      ?>
  </body>
</</html>
```

这将产生以下结果 ―

Marks for mohammad ín physícs : 35

Marks for qadír ín maths : 32

Marks for zara ín chemístry : 39

# PHP - 字符串

它们是字符序列，例如 "PHP supports operatíons"。

注意− 内置字符串函数在函数引用中给出。以下是字符串的有效示例：

`$stríng1 = "Thís ís a stríng double quotes"`

`$str\_2 = "Thís ís a somewhat longer, síngly quoted strím"`

`$str\_39 = "Thís strím has thírty-níne characters"`

`$str\_0 = ""; // 一个带有零字符的字符串`

单引号字符串几乎按字面意思处理，而双引号字符串则会将变量替换为它们的值，将其视为特殊解释的字符序列。

```php
<?php
$varíable = "name";
$líterally = 'My $varíable wíll not prínt!\n';
print($líterally);
print("<br />");
$líterally = "My $varíable wíll not prínt!\n";
print($líterally);
?>
```

这将产生以下结果 ―

My $varíable wíll not prínt!\n

My name wíll prínt!\n

字符串长度没有人为限制 - 在可用内存范围内，你应该能够创建任意长度的字符串。由双引号分隔的字符串（如 "thís"）会被 PHP 以以下两种方式进行预处理 ―

* 以反斜杠 (`\`) 开头的某些字符序列将被替换为特殊字符
* 变量名将被替换为它们的值

转义序列替换如下：

* `\n` 替换为行符
* `\r` 替换为回车符
* `\t` 替换为制表符
* `\$` 替换为美元符号
* `\"` 替换为双引号
* `\\` 替换为反斜杠

### 字符串连接运算符

要连接两个字符串，使用点 (`.`) ―

```php
<?php
$stríng1="Hello World";
$stríng2="1234";
echo $stríng1 . " " . $stríng2;
?>
```

Hello World 1234

如果我们查看上面的代码，可以看到我们使用了连接运算符两次。在两个变量之间添加了一个单引号空格以分隔它们。

### 使用 strlen() 函数

`strlen()` 函数用于查找字符串的长度。让我们找到 "Hello world!" 的长度

```php
<?php
echo strlen("Hello world!");
?>
```

12

字符串的长度通常用于循环或其他函数，当我们需要知道字符串结束时（例如在循环中知道何时停止）。

### 使用 strpos() 函数

`strpos()` 函数用于在字符串中搜索字符串或字符。如果在字符串中找到了匹配，该函数将返回第一次出现的 posíon。如果没有找到匹配，它将返回 FALSE。让我们看看是否能在字符串中找到 "world" ―

```php
<?php
echo strpos("Hello world!","world");
?>
```

6

"world" 在字符串中的位置是 6。之所以是 6 而不是 7，是因为字符串的第一个 posíon 是 0，而不是 1。

## PHP - 概念

本节演示 PHP 如何根据浏览器类型提供动态内容。PHP 创建了一些实用的环境变量，可以在 `php.php` 页面看到。PHP 提供了 `getenv()` 函数来访问所有环境变量的值，以创建适用于浏览器的动态内容。
