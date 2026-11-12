

## 二维关联数组

在 $country 表示例中，行和列都使用索引，有时会导致元素指定的歧义。为了解决这个问题，我们可以不使用列的索引，而是使用键，以获得更好的可读性和对表格更直观的理解。

| | 国家 | 首都 | 居民数 |
|---|---|---|---|
| 0 | France | Paris | 67 |
| 1 | Canada | Ottawa | 38 |
| 2 | Morocco | Rabat | 40 |
| 3 | Spain | Madrid | 47 |

要在 PHP 中声明和初始化此数组，可以使用括号表示法 [] 或 array() 函数：

### 方法 1：

```php
$country_information = array(
array("country" => "France", "capital" => "Paris", "inhabitants" => 67),
array("country" => "Canada", "capital" => "Ottawa", "inhabitants" => 38),
array("country" => "Morocco", "capital" => "Rabat", "inhabitants" => 40),
array("country" => "Spain", "capital" => "Madrid", "inhabitants" => 47)
);
```

### 方法 2：

```php
$country_information = [
["country" => "France", "capital" => "Paris", "inhabitants" => 67],
["country" => "Canada", "capital" => "Ottawa", "inhabitants" => 38],
["country" => "Morocco", "capital" => "Rabat", "inhabitants" => 40],
["country" => "Spain", "capital" => "Madrid", "inhabitants" => 47]
];
```

两种方法，使用缩写语法 [...] 和 **array()** 函数，在结果上是等价的。它们都使用相同的数据创建多维数组。主要区别在于所使用的语法：

缩写语法 [...] 更加简洁现代，因其可读性更高而常被优先选用。array() 函数较旧且更啰嗦，但仍被广泛使用，在某些情况下可能是必要的，特别是在动态构建数组时。

简而言之，两种方法都有效，可以根据编码偏好和特定项目需求进行选择。

这两段代码各自定义了一个名为 $country_information 的多维数组。该数组的每个元素本身也是一个关联数组，包含特定国家的信息。每个子数组将一个键（country、capital、inhabitants）与相应的值（第一个子数组中为 France、Paris、67 等）关联起来。因此，$country_information 是关联数组的集合，每个关联数组代表特定国家的信息。

要访问这种多维数组的元素，我们使用数值索引访问高层数组级别，然后使用关联键访问内部元素。

例如，要访问第一个国家的首都，请使用：

```php
echo $country_information[0]["capital"]; // Displays "Paris".
```

同样，要访问第三个国家的居民数量：

```php
echo $country_information[2]["inhabitants"]; // Displays 40
```

## 遍历多维数组

在 PHP 中遍历多维数组时，我们通常使用 **foreach** 循环的组合。如前所述，多维数组由嵌套数组组成，每个数组级别都可以使用 foreach 循环单独遍历。

让我们以我们之前看到的 $country_information 表为例：

```php
<?php

$country_information = [
["country" => "France", "capital" => "Paris", "inhabitants" => 67],
["country" => "Canada", "capital" => "Ottawa", "inhabitants" => 38],
["country" => "Morocco", "capital" => "Rabat", "inhabitants" => 40],
["country" => "Spain", "capital" => "Madrid", "inhabitants" => 47]
];

foreach ($country_information as $country) {
foreach ($country as $key => $value) {
echo "$key: $value <br>";
}
echo "<br>";
}
?>
```

这个嵌套的 foreach 循环首先遍历 $country_information 数组的每个元素，然后在每次迭代中，遍历与当前国家关联的数组的每个内部元素（键-值）。"echo" 指令用于显示每个键:值对。如果运行此代码，将得到类似以下的结果：

```
country: France
capital: Paris
inhabitants: 67

country: Canada
capital: Ottawa
inhabitants: 38

country: Morocco
capital: Rabat
inhabitants: 40

country: Spain
capital: Madrid
inhabitants: 47
```

## 结论

在本章中，我们详细探讨了 PHP 中数组操作的各个方面，数组是编程中的基本数据结构。我们学习了如何声明和初始化数组、访问其元素、使用循环遍历它们，以及了解不同的数组类型，例如索引数组、关联数组和多维数组。

我们还研究了常见的表格操作，例如添加、修改和删除元素，以及在表格中组织和操作数据的最佳实践。

最后，我们探讨了高级数组功能，例如多维数组和关联数组，并学习了如何在 PHP 程序中有效地使用它们。

通过将这些知识与我们之前探讨的概念（例如函数和循环）相结合，我们现在对 PHP 中的数组操作有了扎实的理解，这将使我们能够创建健壮且动态的 PHP 应用程序。

## 练习

### 练习 15

编写一个 PHP 脚本，将一系列名称存储在数组中，然后以项目符号列表显示这些名称。

### 练习 16

编写一个 PHP 脚本，将三种颜色的名称存储在数组中，并按逆序显示它们。

### 练习 17

编写一个 PHP 脚本，将一系列名称存储在数组中，并按字母顺序显示它们。

### 练习 18

编写一个 PHP 脚本，创建一个水果名称和价格的关联数组，并使用 foreach 循环显示数组的每个元素。

### 练习 19

编写一个多维关联数组，其键为人名，值为包含该人名、城市和年龄的数值数组。然后使用此表为每个人显示一个句子，给出该人的姓、名和年龄。

### 练习 20：函数和数组 (foreach)

编写一个 PHP 函数，以一组数字数组作为输入，并返回所有这些数字的和。

### 练习 21：函数和数组 (foreach)

编写一个函数，以数字数组作为参数，并返回数组中所有偶数的和。

### 练习 22：函数和表格（求平均值）

编写一个函数，以数字数组作为参数，并返回数组中所有偶数的平均值。

### 练习 23：函数和表格（查找最大值）

编写一个函数，以数字数组作为参数，并返回数组中所有数字的最大值。

## 第 6 章

### PHP 内置函数

PHP 的内置函数，也称为预定义函数或原生函数，是默认包含在 PHP 语言中的函数。它们为常见的编程任务提供了大量现成的功能，例如数学运算、字符串操作、日期和时间处理、数组管理、文件访问等。无论您是在开发动态网站、复杂的 Web 应用程序还是任何其他 PHP 项目，这些内置函数都能让您以高效、简化的方式完成众多任务。

在本章中，我们将探讨 PHP 内置函数的一些类别，并发现如何使用它们来满足各种 Web 开发需求。我们将深入学习数学函数以执行复杂计算、字符串函数以操作和格式化文本、数组函数以管理数据集，以及日期和时间函数以精确管理时间。

本章将使您深入了解 PHP 内置函数提供的功能，并提供实际示例来说明它们在不同 Web 开发场景中的用法。准备好深入 PHP 内置函数的世界，发现它们如何简化和加速您的 Web 开发过程。

### 数学函数

PHP 的内置数学函数为执行常见数学运算提供了各种工具。从简单的计算到更高级的操作，PHP 提供了一整套函数来满足开发者的需求。在本节中，我们将探讨 PHP 中可用的一些最常用的数学函数。

### 基本函数

PHP 的基本函数为执行简单数学运算提供了基本工具。它们在 Web 开发中被广泛用于执行基本计算和操作数字。下表总结了一些最常用的基本函数：

