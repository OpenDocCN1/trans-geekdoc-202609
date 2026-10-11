
# 整数、字符串及其他数据类型的数据字面量示例

本节提供了一个教程示例，说明如何对各种数据类型使用数据字面量：`TRUE`、`FALSE` 和 `NULL`；十进制、八进制和十六进制数字；浮点数格式；单引号、双引号和 heredoc 字符串。

为了帮助我们更好地理解如何对各种数据类型使用数据字面量，我编写了以下教程示例脚本：

```php
<?php
/* DataLiteralSamples.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/

print "\n\n Boolean data literals: ";
$isGood = TRUE;
$isBad = false;
print "\n    TRUE: ".$isGood;
print "\n    false: ".$isBad;

print "\n\n Integer data literals in decimal form: ";
$leapYearDays = 366;
$supercoolWater = -42;
$earthRadius = 6371;
print "\n    366: ".$leapYearDays;
print "\n    -42: ".$supercoolWater;
print "\n    6371: ".$earthRadius;

print "\n\n Integer data literals in octal form: ";
$leapYearDays = 0556;
$supercoolWater = -052;
$earthRadius = 014343;
print "\n    0556: ".$leapYearDays;
print "\n    -052: ".$supercoolWater;
print "\n    014343: ".$earthRadius;

print "\n\n Integer data literals in hexadecimal form: ";
$leapYearDays = 0x16E;
$supercoolWater = -0x2A;
$earthRadius = 0x18E3;
print "\n    0x16E: ".$leapYearDays;
print "\n    -0x2A: ".$supercoolWater;
print "\n    0x18E3: ".$earthRadius;

print "\n\n Float data literals in hexadecimal form: ";
$pi = 3.14159;
$lightSpeed = 3e8;
$gdpGrowth = -1.25e-2;
print "\n    3.14159: ".$pi;
print "\n    3e8: ".$lightSpeed;
print "\n    2.7322e1: ".$gdpGrowth;

print "\n\n String data literals in single quoted form: ";
$title = 'Today\'s Special:';
$headers = 'Item\tPrice\tUnit';
$apples = 'Apples\t3.49\tkg';
$eggs = 'Eggs\t1.99\tdozen';
print "\n    ".$title;
print "\n    ".$headers;
print "\n    ".$apples;
print "\n    ".$eggs;

print "\n\n String data literals in double quoted form: ";
$title = "Today\'s Special:";
$headers = "Item\tPrice\tUnit";
$apples = "Apples\t3.49\t\x6B\x67";
$price = 1.99;
$eggs = "Eggs\t$price\tdoz\145\156";
print "\n    ".$title;
print "\n    ".$headers;
print "\n    ".$apples;
print "\n    ".$eggs;

print "\n\n String data literals in heredoc form: ";
$todaySpecial = <<<EOS
    Today's Special:
    Item        Price   Unit
    Apples      3.49    kg
    Eggs        1.99    dozen
EOS;
print "\n".$todaySpecial;

print "\n\n Null data literals: ";
$nothing = NULL;
$void = null;
print "\n    NULL: ".$nothing;
print "\n    null: ".$void;
?>
```

如果运行此示例脚本，你应该会得到：

```
herong> \php\php DataLiteralSamples.php

 Boolean data literals:
    TRUE: 1
    false:

 Integer data literals in decimal form:
    366: 366
    -42: -42
    6371: 6371

 Integer data literals in octal form:
    0556: 366
    -052: -42
    014343: 6371

 Integer data literals in hexadecimal form:
    0x16E: 366
    -0x2A: -42
    0x18E3: 6371

 Float data literals in hexadecimal form:
    3.14159: 3.14159
    3e8: 300000000
    2.7322e1: -0.0125

 String data literals in single quoted form:
    Today's Special:
    Item\tPrice\tUnit
    Apples\t3.49\tkg
    Eggs\t1.99\tdozen

 String data literals in double quoted form:
    Today\'s Special:
    Item        Price   Unit
    Apples      3.49    kg
    Eggs        1.99    dozen

 String data literals in heredoc form:
    Today's Special:
    Item        Price   Unit
    Apples      3.49    kg
    Eggs        1.99    dozen

 Null data literals:
    NULL:
    null:
```

# 整数和浮点数值的溢出

本节描述了什么是算术溢出条件，PHP 5 引擎如何处理整数和浮点数值溢出，以及如何编写 PHP 代码来检测溢出条件。

## 什么是溢出？

**溢出** 或算术溢出是一种条件，当计算产生的结果在量级上大于给定数据类型所能存储或表示的范围时发生。

将此定义应用于 PHP 整数数据类型，我们可以这样说：PHP 整数值溢出是指整数运算产生的整数超出了有符号 32 位整数值范围的条件。

将此定义应用于 PHP 浮点数数据类型，我们可以这样说：PHP 浮点数值溢出是指浮点数运算产生的浮点数值超出了 64 位浮点数值范围的条件。

根据 PHP 手册，以下是 PHP 5 引擎处理算术溢出条件的方式：

*   当整数值溢出发生在整数值范围的上限时，结果整数值将自动转换为浮点数数据类型。
*   当整数值溢出发生在整数值范围的下限时，结果整数值将自动转换为浮点数数据类型。
*   当浮点数值溢出发生在指数值范围的上限时，结果浮点数值将自动转换为一个称为“无穷大”的特殊值。
*   当浮点数值溢出发生在指数值范围的下限时，结果浮点数值将自动转换为 0。这也称为下溢。
