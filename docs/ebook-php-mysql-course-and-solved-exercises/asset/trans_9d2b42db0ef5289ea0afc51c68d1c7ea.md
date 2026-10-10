
在本例中，`$info_country[2]` 返回对应摩洛哥的第三个子表，而 `$info_country[2][2]` 访问该子表的第三个元素，即摩洛哥的人口数量。

### 二维关联数组

在 `$country` 表的示例中，行和列都使用索引，这有时会导致元素的指定产生歧义。为了解决这个问题，我们可以不使用索引作为列的标识，而是使用键，以获得更好的可读性和更直观的表格理解。

![Image](images/image-90.png)

要在 PHP 中声明并初始化此数组，我们可以使用**方括号**表示法 `[]` 或 `array()` 函数：

**方法 1：**

```php
$country_information = array(

 array("country" => "France", "capital" => "Paris", "inhabitants" => 67),

 array("country" => "Canada", "capital" => "Ottawa", "inhabitants" => 38),

 array("country" => "Morocco", "capital" => "Rabat", "inhabitants" => 40),

 array("country" => "Spain", "capital" => "Madrid", "inhabitants" => 47)

);
```

**方法 2：**

```php
$country_information =[

 ["country" => "France" , "capital" => "Paris" , "inhabitants" => 67],

 ["country" => "Canada" , "capital" => "Ottawa" , "inhabitants" => 38],

 ["country" => "Morocco" , "capital" => "Rabat" , "inhabitants" => 40],

 ["country" => "Spain" , "capital" => "Madrid" , "inhabitants" => 47]

];
```

这两种方法，无论是使用简写语法 `[...]` 还是 `array()` 函数，在结果方面都是等效的。它们都创建了一个包含相同数据的多维数组。主要区别在于所使用的语法：

- 简写语法 `[...]` 更加简洁现代，因其增强的可读性而常被首选。
- `array()` 函数较旧且较冗长，但仍被广泛使用，在某些情况下可能是必要的，特别是在动态构建数组时。

简而言之，这两种方法均有效，可根据编码偏好和特定项目需求进行选择。

这两段代码均定义了一个名为 `$country_information` 的多维数组。该数组的每个元素本身都是一个关联数组，包含特定国家的信息。每个子数组将一个键（`country`、`capital`、`inhabitants`）与对应的值关联（第一个子数组为 `France`、`Paris`、`67`，以此类推）。因此，`$country_information` 是一个关联数组的集合，每个数组代表某个特定国家的信息。

要访问此类多维数组的元素，我们使用数字索引访问上层数组，然后使用关联键访问内部元素。

例如，要访问第一个国家的首都，请使用：

```php
echo $country_information[0]["capital"]; // 显示 "Paris"
```

同样，要访问第三个国家的人口数量：

```php
echo $country_information[2]["inhabitants"]; // 显示 40
```

### 遍历多维数组

要在 PHP 中遍历多维数组，我们通常使用 `foreach` 循环的组合。正如我们之前所见，多维数组由嵌套数组组成，每个数组层级都可以使用 `foreach` 循环单独遍历。

让我们以之前看到的 `$country_information` 表为例：

```php
<?php

$country_information =[

 ["country" => "France" , "capital" => "Paris" , "inhabitants" => 67],

 ["country" => "Canada" , "capital" => "Ottawa" , "inhabitants" => 38],

 ["country" => "Morocco" , "capital" => "Rabat" , "inhabitants" => 40],

 ["country" => "Spain" , "capital" => "Madrid" , "inhabitants" => 47]

];

foreach ($country_information as $country) {

 foreach ($country as $key => $value) {

 echo "$key: $value <br>";

 }

 echo "<br>";

}

?>
```

这个嵌套的 `foreach` 循环首先遍历 `$country_information` 数组的每个元素，然后在每次迭代中，遍历与当前国家关联的数组的每个内部元素（键值对）。`echo` 指令用于显示每个键值对。如果您运行此代码，将获得类似以下的结果：

![Image](images/image-91.png)

## 结论

在本章中，我们详细探讨了 PHP 中数组操作的各个方面，数组是编程中的基本数据结构。我们学习了如何声明和初始化数组、访问其元素、使用循环遍历它们，以及理解不同的数组类型，如索引数组、关联数组和多维数组。

我们还研究了常见的数组操作，如添加、修改和删除元素，以及在数组中组织和操作数据的最佳实践。

最后，我们探索了高级数组功能，如多维数组和关联数组，并学习了如何在 PHP 程序中有效地使用它们。

通过将这些知识与我们之前探讨的概念（如函数和循环）相结合，我们现在对 PHP 中的数组操作有了扎实的理解，这将使我们能够创建健壮且动态的 PHP 应用程序。

## 练习

### 练习 15

编写一个 PHP 脚本，将姓名列表存储在数组中，然后以项目符号列表的形式显示这些姓名。

### 练习 16

编写一个 PHP 脚本，将三种颜色的名称存储在数组中，并按逆序显示它们。

### 练习 17

编写一个 PHP 脚本，将姓名列表存储在数组中，并按字母顺序显示它们。

### 练习 18

编写一个 PHP 脚本，创建一个包含水果名称和价格的关联数组，并使用 `foreach` 循环显示数组的每个元素。

### 练习 19

编写一个多维关联数组，其键为人名，值为包含该人名、城市和年龄的索引数组。

然后使用此表为这些人中的每一个显示一个句子，给出该人的名、姓和年龄。

### 练习 20：函数和数组 (foreach)

编写一个 PHP 函数，接受一个数字数组作为输入，并返回所有这些数字的总和。

### 练习 21：函数和数组 (foreach)

编写一个函数，接受一个数字数组作为参数，并返回数组中所有偶数的总和。

### 练习 22：函数和数组 (求平均值)

编写一个函数，接受一个数字数组作为参数，并返回数组中所有偶数的平均值。

### 练习 23：函数和数组 (查找最大值)

编写一个函数，接受一个数字数组作为参数，并返回数组中所有数字的最大值。

# 第 6 章

# PHP 内置函数

PHP 的内置函数，也称为预定义函数或原生函数，是默认包含在 PHP 语言中的函数。它们为常见编程任务提供了广泛的现成功能，例如数学运算、字符串操作、日期和时间处理、数组管理、文件访问等。无论您是在开发动态网站、复杂的 Web 应用程序，还是任何其他 PHP 项目，这些内置函数都能让您以高效、简洁的方式完成多种任务。

在本章中，我们将探索 PHP 内置函数的某些类别，并了解如何使用它们来满足各种 Web 开发需求。我们将深入研究用于执行复杂计算的数学函数、用于操作和格式化文本的字符串函数、用于管理数据集的数组函数，以及用于精确管理时间的日期和时间函数。

本章将让您深入了解 PHP 内置函数提供的功能，并通过实际示例说明它们在不同 Web 开发场景中的用法。准备好深入 PHP 内置函数的世界，发现它们如何简化并加速您的 Web 开发流程。

## 数学函数
