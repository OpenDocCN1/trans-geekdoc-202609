
## PHP 变量变量

2. 如果原始变量的名称可以通过表达式计算得出，可以在 PHP 源代码中使用 `${exp}` 表示法来标识原始变量。例如，`$variableName = "title"; ${$variableName."_1"}` 代表变量 `$title_1`。

3. 具有变量名称的变量可以像普通变量一样赋值新数据。例如，`$variableName = "title"; $$variableName = "Herong's PHP Book";` 将 `"Herong's PHP Book"` 赋值给 `$title`。

4. 具有变量名称的变量可以像普通变量一样用于任何操作。`$variableName = "title"; $$variableName = "Herong's PHP Book"; print($$variableName." is free");` 输出 `"Herong's PHP Book is free"`。

5. 如果使用表达式作为变量名，表达式的结果将自动转换为字符串，并作为变量名使用。通过这种自动转换，任何东西都可以用作变量名。甚至空字符串也可以用作变量名，`${""}` 是一个完美的变量表达式。

现在让我们看看下面的教程示例，以确认上述提到的一些规则：

```php
<?php
#  VariableVariableName.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $variableName = "title";
   $$variableName = "Herong's PHP Book";
   print "\n \$\$variableName is assigned to a message:\n";
   print "    \$variableName: "; var_dump($variableName);
   print "    \$\$variableName: "; var_dump($$variableName);
   print "    \$title: "; var_dump($title);

   $variableName = "";
   $$variableName = "Herong's Programming Book";
   print "\n \$variableName contains an empty string:\n";
   print "    \$variableName: "; var_dump($variableName);
   print "    \$\$variableName: "; var_dump($$variableName);
   print "    \${''}: "; var_dump(${''});

   $variableName = NULL;
   $$variableName = "Herong's Tutorial Book";
   print "\n \$variableName contains the NULL:\n";
   print "    \$variableName: "; var_dump($variableName);
   print "    \$\$variableName: "; var_dump($$variableName);
   print "    \${NULL}: "; var_dump(${NULL});

   $variableName = 1.0/3.3;
   $$variableName = "Herong's Free Book";
   print "\n \$variableName contains a float number:\n";
   print "    \$variableName: "; var_dump($variableName);
   print "    \$\$variableName: "; var_dump($$variableName);
   print "    \${1.0/3.3}: "; var_dump(${1.0/3.3});
?>
```

如果运行此示例脚本，应该得到：

```
herong> \php\php VariableVariableName.php

 $$variableName is assigned to a message:
    $variableName: string(5) "title"
    $$variableName: string(17) "Herong's PHP Book"
    $title: string(17) "Herong's PHP Book"

 $variableName contains an empty string:
    $variableName: string(0) ""
    $$variableName: string(25) "Herong's Programming Book"
    ${''}: string(25) "Herong's Programming Book"

 $variableName contains the NULL:
    $variableName: NULL
    $$variableName: string(22) "Herong's Tutorial Book"
    ${NULL}: string(22) "Herong's Tutorial Book"

 $variableName contains a float number:
    $variableName: float(0.30303030303)
    $$variableName: string(18) "Herong's Free Book"
    ${1.0/3.3}: string(18) "Herong's Free Book"
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟ [Variables, References, and Constants](#part0022.xhtml)

∟ Constant and define() Function

本节介绍什么是常量，`define()` 函数将常量名定义为一个值，常量值可以直接通过名称或通过 `constant()` 函数检索，任何字符串都可以用作常量名。

### What Is a Constant?

常量是数据值的标识符。一旦定义，由常量标识的数据值就不能更改。PHP 支持具有以下基本规则的常量：

1. 常量必须使用 `define(name, value)` 函数定义。例如，`define("PI", 3.14159);` 定义一个名为 `PI` 的常量，其值为 `3.14159`。

2. 要检索常量中定义的值，可以在任何表达式中直接使用常量名。例如，`define("PI", 3.14159); $area = PI * $radius * $radius;` 使用 `PI` 中定义的值来计算面积。

3. 允许对常量名使用任何字符串。例如，`define("LONG PI", 3.14159265359);` 定义一个名为 `'LONG PI'` 的常量，其值为 `3.14159265359`。但不建议在常量名中使用特殊字符。

4. 如果常量名包含特殊字符，需要使用 `constant(name)` 函数来检索常量中定义的值。例如，`define("LONG PI", 3.14159265359); $area = constant("LONG PI") * $radius * $radius;` 使用 `"LONG PI"` 中定义的值来计算面积。

5. 如果想知道是否为给定的常量名定义了常量，可以使用 `defined(name)` 函数。例如，`define("LONG PI", 3.14159265359); defined("LONG PI");` 返回 `TRUE`。而 `defined("LONG RI")` 返回 `FALSE`。

6. 常量只能用标量数据类型的值定义：布尔值、整数、浮点数和字符串。

7. PHP 引擎提供许多预定义（内置）常量。例如，`__FILE__`、`__LINE__`、`PHP_OS`、`PHP_VERSION`、`PHP_INT_MAX`、`DIRECTORY_SEPARATOR` 等。

现在让我们看看下面的教程示例，以确认上述提到的一些规则：

```php
<?php
#  ConstantTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "\n PI is not defined as a constant:\n";
   print "    PI: "; var_dump(PI);

   define("PI", 3.14159);
   print "\n PI is defined to a constant now:\n";
   print "    PI: "; var_dump(PI);

   define("LONG PI", 3.14159265359);
   print "\n LONG PI is defined to a constant now:\n";
   print "    LONG PI: "; var_dump(constant("LONG PI"));

   print "\n LONG RI is not defined as a constant:\n";
   print "    LONG PI: "; var_dump(defined("LONG PI"));
   print "    LONG RI: "; var_dump(defined("LONG RI"));

   print "\n Trying to define DAYS to an array:\n";
   define("DAYS", array("Jan"=>31,"Feb"=>28));
   print "    DAYS: "; var_dump(DAYS);

   print "\n PHP built-in constants:\n";
   print "    __FILE__: "; var_dump(__FILE__);
   print "    __LINE__: "; var_dump(__LINE__);
   print "    PHP_OS: "; var_dump(PHP_OS);
   print "    PHP_VERSION: "; var_dump(PHP_VERSION);
   print "    PHP_INT_MAX: "; var_dump(PHP_INT_MAX);
   print "    DIRECTORY_SEPARATOR: "; var_dump(DIRECTORY_SEPARATOR);
?>
```

如果运行此示例脚本，应该得到：

```
herong> \php\php ConstantTest.php

 PI is not defined as a constant:
    PI: string(2) "PI"

 PI is defined to a constant now:
    PI: float(3.14159)

 LONG PI is defined to a constant now:
    LONG PI: float(3.14159265359)

 LONG RI is not defined as a constant:
    LONG PI: bool(true)
    LONG RI: bool(false)

 Trying to define DAYS to an array:

Warning: Constants may only evaluate to scalar values in
C:\herong\ConstantTest.php on line 20
    DAYS: string(4) "DAYS"

 PHP built-in constants:
    __FILE__: string(43) "C:\herong\ConstantTest.php"
    __LINE__: int(25)
    PHP_OS: string(5) "WINNT"
    PHP_VERSION: string(5) "5.0.4"
    PHP_INT_MAX: int(2147483647)
    DIRECTORY_SEPARATOR: string(1) "\"
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟ Expressions, Operations and Type Conversions

本章提供关于 PHP 表达式和操作的教程笔记和示例代码。主题包括使用数据字面量、变量和操作编写表达式；位运算、算术运算、比较运算、逻辑运算、字符串运算和赋值运算；运算优先级；数据类型自动转换。

> [What Is an Expression](#part0028.xhtml)
>
> [What Is an Operation](#part0029.xhtml)
>
> [Precedence of Operations](#part0030.xhtml)
>
> [Data Type Automatic Conversion](#part0031.xhtml)

**要点：**

*   PHP 支持 6 种基本类型的操作：位运算、算术运算、比较运算、逻辑运算、字符串运算和赋值运算。
