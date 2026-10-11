

# “while” 语句

本节提供了一个教程示例，说明如何使用 `while` 语句在指定条件为真时重复执行一条或多条语句。

为了帮助我们理解 `while` 语句的工作原理，我编写了以下教程示例 PHP 脚本：

```php
<?php
#  WhileStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $upperLimit = 20;
#
   print("\n Single-statement \"while\":\n");
   $sum = 0; $i = 0;
   while ($i<$upperLimit) $sum += ++$i;
   print("    Sum of 1 to 20: $sum\n");
#
   print("\n Multi-statement \"while\":\n");
   $i = 3;
   while ($i<$upperLimit) {
      $isPrime = true;
      $j = 2;
      while ($j<$i) {
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
         $j++;
      }
      if ($isPrime) print "   $i is a prime number.\n";
      $i++;
   }
#
   print("\n Multi-statement \"while ... endwhile\":\n");
   $i = 3;
   while ($i<$upperLimit):
      $isPrime = true;
      $j = 2;
      while ($j<$i):
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
         $j++;
      endwhile;
      if ($isPrime) print "   $i is a prime number.\n";
      $i++;
   endwhile;
?>
```

如果你运行此示例脚本，应该会得到：

```
herong> \php\php WhileStatements.php

 Single-statement "while":
    Sum of 1 to 20: 210

 Multi-statement "while":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.

 Multi-statement "while ... endwhile":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.
```

[PHP 教程 - Herong 的教程示例](#part0001.xhtml)

∟[循环语句 - “while”、“for” 和 “do ... while”](#part0037.xhtml)

∟“for” 语句

# “for” 语句

本节描述 `for` 语句在 PHP 中的工作原理。只要指定条件为真，一条或多条语句就会被重复执行。`for` 语句具有用于循环初始化和循环控制更新的额外表达式。

`for` 语句是 PHP 中最复杂的循环语句。PHP 支持 4 种形式的 `for` 语句：

## 1. 空语句 “for”

```
for (initial_expression; stop_condition; repeating_expression);
```

## 2. 单语句 “for”

```
for (initial_expression; stop_condition; repeating_expression)
   statement;
```

## 3. 多语句 “for”

```
for (initial_expression; stop_condition; repeating_expression) {
   statement;
   statement;
   ...
}
```

## 4. 多语句 “for ... endfor”

```
for (initial_expression; stop_condition; repeating_expression):
   statement;
   statement;
   ...
endfor;
```

所有形式的 `for` 语句执行流程如下：

**步骤 1：** 无条件求值 `initial_expression`。`initial_expression` 通常用于给循环控制变量赋初值，如 `$i=0`。

**步骤 2：** 将 `stop_condition` 作为布尔值求值。`stop_condition` 通常是针对循环控制变量的比较表达式，如 `$i<100`。

**步骤 3：** 如果 `stop_condition` 返回 `TRUE`，继续执行步骤 5。

**步骤 4：** 如果 `stop_condition` 返回 `FALSE`，终止循环。

**步骤 5：** 执行循环中包含的语句。

**步骤 6：** 求值 `repeating_expression`。`repeating_expression` 通常是增加循环控制变量值的表达式，如 `$i++`。

**步骤 7：** 继续执行步骤 2。

如果你想提前终止循环，可以在循环内部使用 `break` 语句，这将立即终止循环。

[PHP 教程 - Herong 的教程示例](#part0001.xhtml)

∟[循环语句 - “while”、“for” 和 “do ... while”](#part0037.xhtml)

∟“for” 语句示例

# “for” 语句示例

本节提供了一个教程示例，说明如何使用 `for` 语句重复执行零条、一条或多条语句。

为了帮助我们理解 `for` 语句的工作原理，我编写了以下教程示例脚本：

```php
<?php
#  ForStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $upperLimit = 20;
#
   print("\n No-statement \"for\":\n");
   for ($sum = 0, $i = 0; $i<$upperLimit; $sum += ++$i);
   print("    Sum of 1 to 20: $sum\n");

   print("\n Single-statement \"for\":\n");
   for ($sum = 0, $i = 0; $i<$upperLimit; $i++) $sum += $i;
   print("    Sum of 0 to 19: $sum\n");
#
   print("\n Multi-statement \"for\":\n");
   for ($i=3; $i<$upperLimit; $i++) {
      $isPrime = true;
      for ($j=2; $j<=$i/2; $j++) {
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
      }
      if ($isPrime) print "   $i is a prime number.\n";
   }
#
   print("\n Multi-statement \"for ... endfor\":\n");
   for ($i=3; $i<$upperLimit; $i++):
      $isPrime = true;
      for ($j=2; $j<=$i/2; $j++):
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
      endfor;
      if ($isPrime) print "   $i is a prime number.\n";
   endfor;
?>
```

如果你运行此示例脚本，应该会得到：

```
herong> \php\php ForStatements.php

 No-statement "for":
    Sum of 1 to 20: 210

 Single-statement "for":
    Sum of 0 to 19: 190

 Multi-statement "for":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.

 Multi-statement "for ... endfor":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.
```

[PHP 教程 - Herong 的教程示例](#part0001.xhtml)

∟[循环语句 - “while”、“for” 和 “do ... while”](#part0037.xhtml)

∟“do ... while” 语句

# “do ... while” 语句

本节描述 `do ... while` 语句在 PHP 中的工作原理。只要指定条件为真，一条或多条语句就会被重复执行。

PHP 还支持一种 `while` 语句的变体，称为 `do ... while` 语句，有 2 种形式：

## 1. 单语句 “do ... while”

```
do statement while (condition);
```

## 2. 多语句 “do ... while”

```
do {
   statement;
   statement;
   ...
} while (condition);
```

所有形式的 `do ... while` 语句执行流程如下：

**步骤 1：** 执行循环中包含的语句。

**步骤 2：** 将 `condition` 作为布尔值求值。

**步骤 3：** 如果 `condition` 返回 `TRUE`，继续执行步骤 1。

**步骤 4：** 如果 `condition` 返回 `FALSE`，终止循环。

当然，你也可以在循环内部使用 `break` 语句来立即终止循环。

我将把编写一些 `do ... while` 语句的示例脚本作为练习留给你。

[PHP 教程 - Herong 的教程示例](#part0001.xhtml)

∟[循环语句 - “while”、“for” 和 “do ... while”](#part0037.xhtml)

∟“break” 和 “continue” 语句

# “break” 和 “continue” 语句

本节描述 `break` 和 `continue` 语句在 PHP 中的工作原理。`break` 语句中断语句块和循环。`continue` 语句中断语句块，但继续循环的下一次迭代。

为了帮助我们更好地控制执行流程，PHP 为语句块提供了两个特殊语句：`break` 和 `continue`：

## 1. 无选项的 “break” 语句

它中断当前语句块和 `break` 语句所在的当前循环。当前语句块中的剩余语句将不会被执行。如果当前语句块作为循环运行，该循环也将被终止。

```
any_block {
   ...
   any_block {
      ...
      any_block {
         ...
         break;
         ...
      }
      ...
   }
   ...
}
```

