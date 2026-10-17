
在 C 语言中，不要期望通过将字符转换为整数来获取该字符的代码。请使用 `ord()` 和 `chr()` 函数在 ASCII 码和字符之间进行转换。

### 4.2.6 字符串类型的细节

PHP 中的字符串被实现为字节数组和一个指示缓冲区长度的整数。它没有关于这些字节如何转换为字符的信息，这把任务留给了程序员。字符串可以由任何值组成，没有任何限制；特别是，值为 0 的字节（"NULL 字节"）允许出现在字符串的任何位置（然而，本手册中提到某些函数认为不是“二进制安全的”，它们可能会将字符串传递给忽略 NUL 字节之后数据的库）。

字符串类型的这种性质解释了为什么 PHP 中没有单独的“字节”（byte）类型——字符串承担了这一角色。不返回任何文本数据的函数（例如，从网络套接字读取的任意数据）仍然会返回字符串。

鉴于 PHP 没有为字符串规定特定的编码，人们可能会好奇字符串字面量是如何编码的。例如，字符串 `"ä"` 是否等于 `"\xE1"` (ISO-8859-1)、`"\xC3\xA1"` (UTF-8, C形式)、`"\xC6\xCC\x81"` (UTF-8, D形式) 或其他可能的表示？答案是，字符串将以其在脚本文件中编码的方式编码。因此，如果脚本是用 ISO-8859-1 编写的，字符串将以 ISO-8859-1 编码，依此类推。然而，如果启用了 Zend Multibyte（多字节支持），则不适用；在这种情况下，脚本可以用任意编码（显式声明或检测到）编写，然后转换为特定的内部编码，该内部编码将用于用于字符串字面量。注意，脚本的编码（或如果启用了 Zend Multibyte 则对内部编码）存在一些限制——这始终意味着编码应该是 ASCII 的兼容超集，例如 UTF-8 或 ISO-8859-1。然而请注意，依赖状态的编码（相同的字节值在初始状态和非初始状态下含义不同）可能会出现问题。

当然，为了实用，处理文本的函数可能对字符串的编码方式做出某些假设。遗憾的是，在 PHP 函数中，这个问题上存在很大差异：

- 某些函数假设字符串是以（任何）单字节编码的，但它们不需要解释这些字节为特定字符。这适用于 `substr()`、`strpos()`、`strlen()` 和 `strcmp()` 等函数。这些函数的另一种思考方式是它们在内存缓冲区上操作，即它们与字节和偏移量工作。
- 其他函数被传递字符串的编码，可能可能在没有提供此类信息时也假定一个默认值。这适用于 `htmlentities()` 和 `mbstring` 扩展中的大多数函数。
- 另一些函数使用当前的 locale（参见 `setlocale()`），但按字节操作。这适用于 `strcasecmp()`、`strtoupper()` 和 `ucfirst()`。这意味着它们可以用于。

## 知识检查

1. 返回一个删除了末尾空格的字符串参数，这种行为是
   - a. `ltrim()` 函数
   - b. `chop()` 函数
   - c. `rtrim()` 函数
   - d. B 和 C 都
2. 被视为一个单元的字符序列被称为
   - a. 数组 (Arrays)
   - b. 函数 (Functions)
   - c. 方法 (Methods)
   - d. 字符串 (Strings)
3. `ltrim()` 返回的字符串参数带有一个：
   - a. 删除了前面的空格
   - b. 删除了尾的空格
   - c. 数值
   - d. 以上均不是
4. 当两个字符串完全相等时，`strcmp()` 返回什么？
   - a. 返回字符串
   - b. 返回 0
   - c. 返回 1
   - d. 无返回
5. 为了判断一个字符串是否等于另一个字符串，我们可以使用哪个函数？
   - a. `strpos()`
   - b. `strpos()`
   - c. `str()`
   - d. 全部

# 基础计算机编程：PHP

# 复习习题

- 1. 讨论单引号字符串。
- 2. 写一个关于双引号字符串技术的程序。
- 3. 你对变量解析（variable parsing）如何理解？
- 4. 解释复杂（大括号）语法的过程。
- 5. 如何通过字符访问和修改字符串？

## 检查你的结果

- 1. (d) 2. (d) 3. (a) 4. (b) 5. (b)

## 参考文献

- 1. Andrei Zievski. “The Good, the Bad, and the Ugly: What Happened to Unicode and PHP 6”. Retrieved 2014-02-09.
- 2. “Basic Coding Standard”. PHP Framework Interoperability Group. Retrieved 2016-01-03.
- 3. `http://php.net/manual/en/language.types.string#phplanguage.types.string.details`
- 4. `http://php.net/manual/en/language.types.string#phplanguage.types.string.details`
- 5. `https://docs.python.org/2/library/string.html`
- 6. `https://techterms.com/definition/string`
- 7. `https://www.cloudways.com/blog/php-string-functions-with-examples/`
- 8. `https://www.guru99.com/php-strings.html`
- 9. `https://www.javatpoint.com/php-string`
- 10. `https://www.techspedia.com/definition/3853/parse`
- 11. `https://www.tutorialspoint.com/php/php_strings.htm`
- 12. “Resetting PHP 6”. 至少2008年起，书架上就有声称涵盖 PHP 6 的书籍。但到2010年3月，PHP 6 仍尚未发布——事实上，它甚至远未发布。近期事件表明，PHP 6 不会在 2011 年之前发布——如果它真的会发布的话。

```php
'country' => 'US',
'age' => 25
echo json_encode($object);
// Echoes {
// "name":"Jane Doe",
// "country":"US",
// "age":25
// }
// Just like we love it!
```

# 第5章

## PHP 数组

> "正如 Bromberger 所观察到的，规则被理解为计算系统的元素，这些元素决定了语言中无限表达式序列的语音和意义；由此产生的信息在语言在使用中被其他系统访问。"
> —诺姆·乔姆斯基 (Noam Chomsky)

### 学习目标

学习本章后，你将能够：
- 讨论数组函数
- 理解数组

### 引言

PHP 支持标量和复合数据类型。在本章中，我们将讨论一种复合类型：数组。数组是一组组织成键值对的数据值。你可以通俗地理解数组，就像一个蛋盒一样。蛋盒的每个隔层都可以放入鸡蛋，而且像蛋盒一样，你可以在里面放入任何东西（如石头、四叶草或螺丝钉），因此数组并不限于一种数据类型。它可以包含字符串、整数、布尔值等。此外，数组还可以包含其他数组。本章将介绍创建数组、从数组中删除元素以及遍历数组的内容。由于数组非常常见且有用，许多内置函数可以在 PHP 中处理它们。例如，如果你想发送多个地址，数组允许这种选择。配置是根据性质、数量和特征进行的排列。

### 5.1 数组函数

这些函数允许你以各种方式交互和操作数组。数组对于存储、管理和操作变量集至关重要。

#### 5.1.1 安装

使用这些函数不需要安装；它们是 PHP 的。

#### 5.1.2 配置

该扩展在 `php.ini` 中没有定义。

#### 5.1.3 数组常量

| 序号 | 常量 | 描述 |
|---|---|---|
| 1 | `CASE_LOWER` | 用于 `array_change_case()` 将键转换为小写 |
| 2 | `CASE_UPPER` | 用于 `array_change_case()` 将键转换为大写 |
| 3 | `SORT_ASC` | 用于 `array_multisort()` 升序排序 |
| 4 | `SORT_DESC` | 用于 `array_multisort()` 降序排序 |
| 5 | `SORT_REGULAR` | 用于常规比较项目 |
| 6 | `SORT_NUMERIC` | 用于数值比较项目 |
| 7 | `SORT_STRING` | 用于作为字符串比较项目 |
| 8 | `SORT_LOCALE` | 用于根据语言环境比较项目 |
| 9 | `COUNT_NORMAL` | |
| 10 | `COUNT_RECURSIVE` | |
| 11 | `EXTR_WRITE` | |
| 12 | `EXTR_SKIP` | |

#### 5.1.4 函数列表

| 序号 | 函数 | 描述 |
|---|---|---|
| 1 | `array()` | 创建数组 |
| 2 | `array_change_case()` | 返回所有小写或大写的键 |
| 3 | `array_chunk()` | 将数组分 |
| 4 | `array_combine()` | 使用一个数组作为键，另一个作为值创建数组 |
| 5 | `array_count_values()` | 返回每个值的出现次数 |
| 6 | `array_diff()` | 比较数组值 |
| 7 | `array_diff_assoc()` | 比较数组键和值 |
| 8 | `array_diff_key()` | 比较数组键 |
| 9 | `array_diff_uassoc()` | 使用自定义函数比较数组键和值，并返回差异 |
| 10 | `array_diff_ukey()` | 使用额外的自定义函数比较数组键，并返回差异 |
| 11 | `array_fill()` | 向数组填充指定数量的项目和指定的值 |
| 12 | `array_fill_keys()` | 使用指定的键填充数组 |
| 13 | `array_filter()` | 使用自定义函数过滤数组元素 |
| 14 | `array_flip()` | 交换所有键与其关联的值 |
| 15 | `array_intersect()` | 比较数组值 |
| 16 | `array_intersect_assoc()` | 比较数组键和值 |
| 17 | `array_intersect_key()` | 比较数组键 |
| 18 | `array_intersect_uassoc()` | 使用自定义函数比较数组键和值，并返回差异 |
| 19 | `array_intersect_ukey()` | 使用额外的自定义函数比较数组键，并返回差异 |
| 20 | `array_key_exists()` | 检查指定的键是否存在于数组中 |
| 21 | `array_keys()` | 返回数组的所有键 |
| 22 | `array_map()` | 将数组的每个值发送给自定义函数，返回新值 |
| 23 | `array_merge()` | 将一个或多个数组合并为一个数组 |
| 24 | `array_merge_recursive()` | 将一个或多个数组合并为一个数组 |
| 25 | `array_multisort()` | 排序多个或多维数组 |
| 26 | `array_pad()` | 向数组插入指定数量的项目和指定的值 |
| 27 | `array_pop()` | 删除数组的最后一个元素 |
| 28 | `array_product()` | 计算数组中值的积 |
| 29 | `array_push()` | 向数组末尾插入一个或多个元素 |
| 30 | `array_rand()` | 返回数组的一个或多个随机键 |

| ID | 函数 | 复杂度 | 说明 |
|---|---|---|---|
| 31 | `array_reduce()` | 4 | 使用用户定义的函数将数组转换为字符串 |
| 32 | `array_reverse()` | 4 | 返回反序排列的数组 |
| 33 | `array_search()` | 4 | 在数组中搜索给定值并返回其键 |
| 34 | `array_shift()` | 4 | 移除数组中的第一个元素，并返回被移除元素的值 |
| 35 | `array_slice()` | 4 | 返回数组的选部分 |
| 36 | `array_splice()` | 4 | 移除并替换数组中的指定元素 |
| 37 | `array_sum()` | 4 | 返回数组中值的总和 |
| 38 | `array_udiff()` | 5 | 在自定义函数中比较数组值并返回数组 |
| 39 | `array_udiff_assoc()` | 5 | 比较数组键，并在自定义函数中比较数组值，并返回数组 |
| 40 | `array_udiff_uassoc()` | 5 | 在自定义函数中比较数组键和数组值，并返回数组 |
| 41 | `array_uintersect()` | 5 | 在自定义函数中比较数组值并返回数组 |

# 基础计算机编程：PHP

| ID | 函数 | 复杂度 | 说明 |
|---|---|---|---|
| 42 | `array_intersect_assoc()` | 5 | 比较数组键，并在自定义函数中比较数组值，并返回数组 |
| 43 | `array_intersect_uassoc()` | 5 | 在自定义函数中比较数组键和数组值，并返回数组 |
| 44 | `array_unique()` | 4 | 移除数组中的重复值 |
| 45 | `array_unshift()` | 4 | 在数组开头添加一个或多个元素 |
| 46 | `array_values()` | 4 | 返回数组的所有值 |
| 47 | `array_walk()` | 3 | 对数组的每个成员应用用户函数 |
| 48 | `array_walk_recursive()` | 5 | 递归地对数组的每个成员应用用户函数 |
| 49 | `asort()` | 3 | 逆序排序数组并保持索引关联 |
| 50 | `compact()` | 3 | 排序数组并保持索引关联 |
| 51 | `compact()` | 4 | 创建包含变量及其对应值的数组 |
| 52 | `count()` | 3 | 统计数组中的元素或对象的属性数量 |
| 53 | `current()` | 3 | 返回数组中的当前元素 |

| ID | 函数 | 复杂度 | 说明 |
|---|---|---|---|
| 54 | `each()` | 3 | 从数组中返回当前的键值对 |
| 55 | `end()` | 3 | 将数组的内部指针指向其最后一个元素 |
| 56 | `extract()` | 3 | 从数组将变量导入到当前符号表 |
| 57 | `in_array()` | 4 | 检查指定值是否存在于数组中 |
| 58 | `key()` | 3 | 从数组中获取键 |
| 59 | `krsort()` | 3 | 按键逆序排序数组 |
| 60 | `ksort()` | 3 | 按键排序数组 |
| 61 | `list()` | 3 | 像数组一样分配变量 |
| 62 | `natcasesort()` | 4 | 使用不区分大小写的“自然顺序”算法排序数组 |
| 63 | `nsort()` | 4 | 使用不区分大小写的“自然顺序”算法排序数组 |
| 64 | `next()` | 3 | 指针指向下一个元素 |
| 65 | `pos()` | 3 | 返回当前索引 |
| 66 | `prev()` | 3 | 指针指向上一个元素 |

| ID | 函数 | 复杂度 | 说明 |
|---|---|---|---|
| 67 | `range()` | 3 | 创建一个范围数组 |
| 68 | `reset()` | 3 | 将数组指针置到第一个元素 |
| 69 | `rsort()` | 3 | 逆序排序数组 |
| 70 | `shuffle()` | 3 | 打乱数组 |
| 71 | `sizeof()` | 3 | 获取数组的长度 |
| 72 | `sort()` | 3 | 排序数组 |
| 73 | `usort()` | 3 | 使用自定义函数排序数组 |
| 74 | `uksort()` | 3 | 使用自定义函数按键排序数组 |
| 75 | `array_flip()` | 3 | 交换数组的键和值 |

# 基础计算机编码：PHP

```php
$addresses[0] = "spam@cyberpromo.net";
echo $addresses;    // 输出 "Array"
```

在程序中使用简单的赋值来初始化数组可能会导致如下代码：

```php
$addresses[0] = "spam@cyberpromo.net";
$addresses[1] = "abuse@example.com";
$addresses[2] = "root@example.com";
```

这是一个索引数组，具有从 0 开始的整数索引。以下是一个关联数组：

```php
$price['gasket'] = 15.29;
$price['wheel'] = 75.25;
$price['tire'] = 50.00;
```

初始化数组的一种简单方法是使用 `array()` 结构，它构建一个索引数组，并且索引值（从 0 开始）会被自动创建：

```php
$addresses = array("spam@cyberpromo.net", "abuse@example.com", "root@example.com");
```

使用 `array()` 创建关联数组时，使用 `=>` 符号将索引（键）与值分开：

```php
$price = array(
  'gasket' => 15.29,
  'wheel' => 75.25,
  'tire' => 50.00
);
```
