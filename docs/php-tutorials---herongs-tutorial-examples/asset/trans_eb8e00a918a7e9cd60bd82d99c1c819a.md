

指定了两个语句块。但根据指定条件的值，只会执行其中一个语句块。如果指定条件为 `TRUE`，则执行第一个块。如果指定条件为 `FALSE`，则执行第二个块。

### "if ... elseif" 语句

```
if (condition_1) {
   statement;
   statement;
   ...
} elseif (condition_2) {
   statement;
   statement;
   ...
} elseif (condition_3) {
   statement;
   statement;
   ...
...
} else {
   statement;
   statement;
   ...
}
```

指定了多个语句块。但根据为该块指定的条件的值，只会执行其中一个语句块。

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟ [Conditional Statements - "if" and "switch"](#part0032.xhtml)

∟ "if" 语句示例

本节提供了一个教程示例，演示如何使用不同类型的 `if` 语句来控制代码执行。

为了帮助我们理解 `if` 语句的工作原理，我编写了以下教程示例 PHP 脚本：

```
<?php
#  IfStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#

   print("\n Single-statement \"if\":\n");
   $isNewYear = TRUE;
   if ($isNewYear) print("    Happy New Year!\n");

   print("\n Multi-statement \"if\":\n");
   $hasError = TRUE;
   if ($hasError) {
      print("    Open the log file.\n");
      print("    Write an error message.\n");
      print("    Close the log file.\n");
   }

   print("\n \"if ... else\" statement:\n");
   $login = "Herong";
   if ($login == "Admin") {
      print("    Display the delete button.\n");
      print("    Display the edit button.\n");
   } else {
      print("    Display the view button.\n");
   }

   print("\n \"if ... elseif\" statement:\n");
   $dateInfo = getdate();
   $wDay = $dateInfo["wday"];
   $weekDay = $dateInfo["weekday"];
   $openHours = "open";
   if ($wDay == 0) {
      $openHours = "closed";
   } elseif ($wDay >= 1 && $wDay <= 5) {
      $openHours = "open from 9:00am to 9:00pm";
   } elseif ($wDay == 6 ) {
      $openHours = "open from 9:00am to 5:00pm";
   } else {
      $openHours = "not at here";
   }
   print("    Today is: $weekDay\n");
   print("    The library is $openHours\n");
?>
```

如果运行此示例脚本，你应该会得到：

```
herong> \php\php IfStatements.php

 Single-statement "if":
    Happy New Year!

 Multi-statement "if":
    Open the log file.
    Write an error message.
    Close the log file.

 "if ... else" statement:
    Display the view button.

 "if ... elseif" statement:
    Today is: Sunday
    The library is closed
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟ [Conditional Statements - "if" and "switch"](#part0032.xhtml)

∟ "switch" 语句

本节描述 `switch` 语句的工作原理。执行将从其预期值与测试表达式匹配的 `case` 子句开始。执行将继续进行所有剩余的 `case` 子句。

`switch` 语句是根据特定条件选择性执行语句的另一种方式。以下是 `switch` 语句的语法：

```
switch (test_expression) {
   case expected_value_1:
      statement_block_1;
      break;
   case expected_value_2:
      statement_block_2;
      break;
   ...
   default:
      last_statement_block;
}
```

其中 `test_expression` 是一个用于与 `case` 子句中指定的预期值进行比较的表达式，而 `expected_value_*` 是预期值。

`switch` 语句的执行过程如下：

* 每个 `case` 子句将按顺序从上到下依次访问。
* 如果测试表达式的结果与某个 `case` 子句中的预期值匹配，则执行该子句中的语句块。
* 一旦执行了一个语句块，所有剩余的语句块也将被执行。
* 如果没有执行任何 `case` 子句，则执行 `default` 子句。
* 要停止执行剩余语句，可以使用 `break` 语句。

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟ [Conditional Statements - "if" and "switch"](#part0032.xhtml)

∟ "switch" 语句示例

本节提供了一个教程示例，演示如何使用 `switch` 语句根据预期值的相等条件选择一个语句块。

为了帮助我们理解 `switch` 语句的工作原理，我编写了以下教程示例脚本：

```
<?php
#  SwitchStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   date_default_timezone_set("Europe/Paris");
   $dateInfo = getdate();
   $wDay = $dateInfo["wday"];
   $weekDay = $dateInfo["weekday"];
   $openHours = "open";

   print "\nLibrary Hours with \"switch\" statements:\n";
   print "   Today is: $weekDay\n";
   switch ($weekDay) {
      case "Monday":
      case "Tuesday":
      case "Wednesday":
      case "Thursday":
      case "Friday":
         $openHours = "open from 9:00am to 9:00pm";
         break;
      case "Saturday":
         $openHours = "open from 9:00am to 5:00pm";
         break;
      case "Sunday":
         $openHours = "closed";
         break;
      default:
         $openHours = "not at here";
   }
   print "   The library is $openHours\n";
?>
```

如果运行此示例脚本，你应该会得到：

```
herong> \php\php SwitchStatements.php

Library Hours with "switch" statements:
   Today is: Sunday
   The library is closed
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟ 循环语句 - "while"、"for" 和 "do ... while"

本章提供了关于循环语句的教程示例和说明。主题包括 `while`、`for` 和 `do ... while` 语句；使用循环语句控制代码执行的示例。

> ["while" Statements](#part0038.xhtml)
>
> ["while" Statement Examples](#part0039.xhtml)
>
> ["for" Statements](#part0040.xhtml)
>
> ["for" Statement Examples](#part0041.xhtml)
>
> ["do ... while" Statements](#part0042.xhtml)
>
> ["break" and "continue" Statements](#part0043.xhtml)

要点：

* `while` 语句是 PHP 中最常用的循环语句。
* `for` 语句是 PHP 中最复杂的循环语句。
* `do ... while` 语句只是 `while` 语句的一种变体。
* `break` 语句接受一个可选参数，用于跳出多层循环。
* `continue` 语句接受一个可选参数，用于跳出并继续在指定层级的循环。

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟ [Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟ "while" 语句

本节描述 `while` 语句在 PHP 中的工作原理。只要指定条件为真，就会重复执行一条或多条语句。

`while` 语句是 PHP 中最常用的循环语句。PHP 支持 3 种形式的 `while` 语句：

#### 单语句 "while"

```
while (condition) statement;
```

#### 多语句 "while"

```
while (condition) {
   statement;
   statement;
   ...
}
```

#### 多语句 "while ... endwhile"

```
while (condition):
   statement;
   statement;
   ...
endwhile;
```

所有形式的 `while` 语句执行过程如下：

步骤 1：将 `condition` 计算为布尔值。

步骤 2：如果 `condition` 返回 `TRUE`，继续执行步骤 4。

步骤 3：如果 `condition` 返回 `FALSE`，终止循环。

步骤 4：执行循环中包含的语句。

步骤 5：继续执行步骤 1。

当然，你可以在循环内部使用 `break` 语句来立即终止循环。

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟ [Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟ "while" 语句示例

