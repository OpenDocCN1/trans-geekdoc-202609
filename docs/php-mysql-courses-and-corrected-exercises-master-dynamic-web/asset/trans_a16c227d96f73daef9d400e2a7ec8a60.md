
## 数字。

```php
<?php
// First even number generator
function generate_even_numbers($max) {
    for ($i = 0; $i <= $max; $i += 2) {
        yield $i;
    }
}

// Second odd number generator
function generate_odd_numbers($max) {
    for ($i = 1; $i <= $max; $i += 2) {
        yield $i;
    }
}

// Third generator calling the 2 previous generators
function generate_even_odd_numbers($evenmax, $oddmax) {
    yield from generate_even_numbers($evenmax);
    yield from generate_odd_numbers($oddmax);
}
```

```php
// Use the generator to display a sequence of even and odd numbers
foreach (generate_even_odd_numbers(20, 30) as $number) {
    echo $number . " ";
}

?>
```

此代码定义了三个数字生成器：generate_even_numbers()、generate_odd_numbers() 和 generate_even_odd_numbers()。

第一个生成器 **generate_even_numbers()** 生成一个直到指定最大值的偶数序列。第二个生成器 **generate_odd_numbers()** 生成一个直到指定最大值的奇数序列。

第三个生成器 **generate_even_odd_numbers()** 使用生成器委托（使用 **yield from** 关键字）来调用前两个生成器，并生成一个交替的偶数和奇数序列，直到每个生成器指定的最大值。

接下来，代码使用生成器 **generate_even_odd_numbers()** 显示一个数字序列，偶数最高到 20，奇数最高到 30。这是通过使用 foreach 循环实现的，该循环遍历生成器生成的值并在屏幕上显示它们。

执行此代码将产生以下结果：

![](img/caba2aa22f5409ba73dea47176330677_193_0.png)

## 结论

PHP 函数是基本的编程元素，能够将代码组合在一起，使其可重用且模块化。它们提供了一种高效的方式来组织和结构化代码，使维护和项目管理更加容易。我们已经探索了函数的各个方面，包括它们的声明、调用、参数管理和变量作用域，以及类型和命名参数等更高级的概念。

理解函数的工作原理以及如何恰当地使用它们，对任何 PHP 开发者都至关重要，因为这能够实现创建更健壮、可扩展且易于维护的应用程序。通过掌握本章介绍的概念，你将能够编写更整洁、更模块化且更高效的代码，这将显著提升你作为 PHP 开发者的生产力。

## 练习

## 练习 12

编写一个函数，用于测试一个数字是否是 3 的倍数，并根据测试结果显示一条消息。

## 练习 13

编写一个 PHP 函数，接受三个数字作为输入，并返回这三个数字中最大的一个。

## 练习 14

编写一个函数，显示找到作为参数给定的两位整数所需的随机数字。

## 第 5 章

PHP 中的数组

数组在编程中起着至关重要的作用，为组织和操作数据集提供了一种强大且灵活的方式。在 PHP 中，数组是多功能的数据结构，可以包含不同类型元素的有序集合，例如数字、字符串甚至其他数组。本章详细探讨了 PHP 中的数组，从它们的声明和初始化到使用预定义函数进行高级操作。掌握数组对于创建动态的高性能 Web 应用程序至关重要。

在 PHP 中，数组是一种允许你在单个变量中存储多个值的数据结构。这些值可以是各种类型，例如整数、字符串、布尔值等等。数组中的每个值都与一个键相关联，该键可能是数字或字符串，具体取决于数组类型。

在 PHP 中，有几种类型的数组。让我们探索 PHP 中的数组世界，发现它们所提供的一切！

| 键 | 值 |
| :--- | :--- |
| 姓氏 | Dupont |
| 名字 | Amine |
| 年龄 | 29 |
| 性别 | M |
| 国家 | 加拿大 |

| 索引 | 值 |
| :--- | :--- |
| 0 | Emma |
| 1 | Alice |
| 2 | Lina |
| 3 | Sarah |
| 4 | Thomas |

## 索引数组（数字索引）

索引数组（也称为数字数组）是一种数据结构，其中每个元素都与一个数值索引相关联。这些索引通常从零开始，每增加一个元素就加 1。

索引数组是 PHP 中最简单的数组形式之一，广泛用于存储有序数据集合。

在本节中，我们将探讨如何在 PHP 中声明、初始化和操作索引数组。我们还将发现添加、修改、删除和遍历索引数组元素等常见操作。通过理解这些基本概念，你将能够在 PHP 项目中高效地使用索引数组。

## 索引数组的声明与初始化

在 PHP 中，你可以用多种方式声明和初始化索引数组。以下是一些示例：

```php
<?php
// Declaration of an empty indexed array
$empty_array = [];

// Declaration and initialization of an indexed array with values
$numbers = [10, 20, 30, 40, 50];

// Declaration of an array indexed with the array() function
$lastnames = array("Emma", "Alice", "Lina", "Sarah", "Thomas");
?>
```

在本示例中，我们定义了三种数组声明方式：

第一种声明：`$empty_array = []`；声明一个名为 `$empty_array` 的空索引数组。空方括号 `[]` 在 PHP 中用于创建新的空数组。

第二条语句：

$numbers = [10, 20, 30, 40, 50]; 声明并初始化一个名为 $numbers 的索引数组，其值为 [10, 20, 30, 40, 50]。值由逗号分隔，并包含在方括号 [ ] 中。

第三条语句：

$lastnames = array("Emma", "Alice", "Lina", "Sarah", "Thomas"); 使用 array() 函数声明一个名为 $lastnames 的索引数组。array() 函数通过在括号中指定参数值来创建数组。值由逗号分隔，并包含在圆括号 ( ) 中。

总之，这些索引数组声明展示了在 PHP 中创建和初始化索引数组的不同方式，无论是使用空括号 [] 还是 array() 函数。

## 访问索引数组的元素

要访问索引数组中的特定元素，请使用其对应的数值索引，从 0 开始。语法如下：

| 表名 | 索引 |
| :--- | :--- |
| $arrayName[0] | |
| $arrayName[1] | |

## 示例

| 表名 | 索引 |
| :--- | :--- |
| $number[0] | |
| $number[1] | |

在上面的示例中，如果你想访问 numbers 数组的元素，只需使用它们的索引，但请记住第一个元素的索引始终为 0：

```php
<?php

$numbers = [10, 20, 30, 40, 50];

echo $numbers[0]."<br>";
echo $numbers[1]."<br>";
echo $numbers[2]."<br>";
echo $numbers[3]."<br>";
echo $numbers[4]."<br>";
?>
```

如果你执行此代码，将得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_200_0.png)

## 向索引数组添加元素

要向索引数组添加新元素，只需将值赋给新索引即可。PHP 会自动处理正确的索引。以下是在前面示例中向 $numbers 和 $lastnames 数组添加新元素的示例：

```php
<?php
// Declaration and initialization of an array indexed with values
$numbers = [10, 20, 30, 40, 50];

// Declaration of an array indexed with the array() function
$lastnames = array("Emma", "Alice", "Lina", "Sarah", "Thomas");

$numbers[] = 60; // Add 60 to the end of the array
$lastnames[5] = "Eve"; // Add "Eve" to index 5 of array
?>
```

执行此代码后，数组 $numbers 和 $lastnames 变为：

$numbers = [10, 20, 30, 40, 50, 60]
$lastnames = ["Emma", "Alice", "Lina", "Sarah", "Thomas", "Eve"]

## 编辑和删除元素

要修改索引数组中现有元素，可以通过其索引访问该元素并为其赋予新值。要删除元素，可以使用 unset() 函数。

## 示例：

如果你想修改前面示例中的 $numbers 数组，将元素 20 替换为 100，只需添加以下代码行：

