

## 数组排序

### 2. 创建 HTML 表格

为了使有序列表更易于阅读，它将在 HTML 表格中打印。表格从这里开始。

```html
<table border="0" cellspacing="3" cellpadding="3" align="center">
  <tr>
    <td><h2>Rating</h2></td>
    <td><h2>Title</h2></td>
  </tr>
```

### 3. 添加 PHP 开始标签并创建新数组

```php
<?php # Script 2.8 - sorting.php

$movies = array (
  'Casablanca' => 10,
  'To Kill a Mockingbird' => 10,
  'The English Patient' => 2,
  'Stranger Than Fiction' => 9,
  'Story of the Weeping Camel' => 5,
  'Donnie Darko' => 7
);
```

**脚本 2.8。** 定义了一个数组，然后以两种不同的方式对其进行排序：首先按键排序，然后按值排序（逆序）。

---

```php
1  <!DOCTYPE html PUBLIC "-//W3C//DTD
    XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/
    xhtml1-transitional.dtd">
2  <html xmlns="http://www.w3.org/1999/
    xhtml" xml:lang="en" lang="en">
3  <head>
4      <meta http-equiv="Content-Type"
        content="text/html; charset=utf-8" />
5      <title>Sorting Arrays</title>
6  </head>
7  <body>
8  <table border="0" cellspacing="3"
    cellpadding="3" align="center">
9      <tr>
10         <td><h2>Rating</h2></td>
11         <td><h2>Title</h2></td>
12     </tr>
13  <?php # Script 2.8 - sorting.php

14  // Create the array:
15  $movies = array (
16  'Casablanca' => 10,
17  'To Kill a Mockingbird' => 10,
18  'The English Patient' => 2,
19  'Stranger Than Fiction' => 9,
20  'Story of the Weeping Camel' => 5,
21  'Donnie Darko' => 7
22  );

23  // Display the movies in their
    // original order:
24  echo '<tr><td colspan="2"><b>In
    their original order:</b></td></tr>';
25  foreach ($movies as $title =>
    $rating) {
26      echo "<tr><td>$rating</td>
    <td>$title</td></tr>\n";
27  }

28  // Display the movies sorted by title:
29  ksort($movies);
30  echo '<tr><td colspan="2"><b>Sorted by
    title:</b></td></tr>';
31  foreach ($movies as $title =>
    $rating) {
32      echo "<tr><td>$rating</td>
    <td>$title</td></tr>\n";
33  }

34  // Display the movies sorted by
    // rating:
35  arsort($movies);
36  echo '<tr><td colspan="2"><b>Sorted by
    rating:</b></td></tr>';
37  foreach ($movies as $title =>
    $rating) {
38      echo "<tr><td>$rating</td>
    <td>$title</td></tr>\n";
39  }

40  ?>
41  </table>
42  </body>
43  </html>
```

---

该数组使用电影标题作为键，各自的评分作为值。这种结构将为整个列表的排序提供多种可能性。请随意更改电影列表和排名（只是别因为我的电影品味而责备我）。

### 4. 按原样打印数组

```php
echo '<tr><td colspan="2"><b>In their original order:</b></td></tr>';
foreach ($movies as $title => $rating) {
  echo "<tr><td>$rating</td>
  <td>$title</td></tr>\n";
}
```

此时脚本中的数组顺序与定义时相同。为验证这一点，将其打印出来。首先在两个表格列上打印一个标题。然后，在 `foreach` 循环中，键打印在第一列，值打印在第二列。同时也会打印一个换行符，以提高 HTML 源代码的可读性。

### 5. 按标题字母顺序对数组排序并再次打印

```php
ksort($movies);
echo '<tr><td colspan="2"><b>Sorted by title:</b></td></tr>';
foreach ($movies as $title => $rating) {
  echo "<tr><td>$rating</td>
  <td>$title</td></tr>\n";
}
```

`ksort()` 函数将按键对数组进行升序排序，同时保持键值关系。其余代码重复步骤 4。

### 6. 按评分数值降序对数组排序并再次打印

```php
arsort($movies);
echo '<tr><td colspan="2"><b>Sorted by rating:</b></td></tr>';
foreach ($movies as $title => $rating) {
  echo "<tr><td>$rating</td>
  <td>$title</td></tr>\n";
}
```

要按值（评分）排序并同时保持键不变，可以使用 `asort()` 函数。但由于最高分的电影应排在最前面，因此必须反转顺序，使用 `arsort()`。

### 7. 完成 PHP、表格和 HTML

```php
?>
</table>
</body>
</html>
```

### 8. 将文件保存为 `sorting.php`，放入 Web 目录，并在 Web 浏览器中测试

![Image](graphics/02_figure_24_i.jpg)

此页面演示了数组排序的不同方式。

---

> **提示**
>
> 要随机化数组的顺序，请使用 `shuffle()`。

---

> **提示**
>
> PHP 的 `natsort()` 函数可用于以更自然的顺序对数组进行排序（主要是更好地处理字符串中的数字）。

---

> **提示**
>
> 多维数组在 PHP 中稍加努力即可排序。有关 `usort()` 函数的更多信息，请参阅 PHP 手册，或查看我的著作 *PHP 5 Advanced: Visual QuickPro Guide*。

---

## For 和 While 循环

本章要讨论的最后一个语言结构是循环。你已经用过一个了，即 `foreach`，用于访问数组中的每个元素。你将使用的其他两种循环类型是 `for` 和 `while`。

### `while` 循环

`while` 循环如下所示：

```php
while (condition) {
  // Do something.
}
```

只要循环的 *condition*（条件）部分为真，循环就会执行。一旦变为假，循环停止。如果条件从未为真，循环将永不执行。`while` 循环最常用于从数据库检索结果，正如你将在 [第 9 章](#ch09.html#ch09) “[将 PHP 与 MySQL 结合使用](#ch09.html#ch09)” 中看到的那样。

![Image](graphics/02_figure_25_a.jpg)

*PHP 处理 `while` 循环的流程图表示。*

### `for` 循环

`for` 循环具有更复杂的语法：

```php
for (initial expression; condition; closing expression) {
  // Do something.
}
```

首次执行循环时，将运行初始表达式。然后检查条件，如果为真，则执行循环体内容。执行后，运行结束表达式并再次检查条件。此过程持续直到条件为假。例如：

```php
for ($i = 1; $i <= 10; $i++) {
  echo $i;
}
```

![Image](graphics/02_figure_26_b.jpg)

*PHP 处理更复杂的 `for` 循环的流程图表示。*

第一次运行此循环时，`$i` 变量被设置为 1。然后检查条件（*1 是否小于或等于 10？*）。因为这是真的，所以打印出 1（`echo $i`）。然后，`$i` 增加到 2（`$i++`），再次检查条件，依此类推。该脚本的结果将打印出数字 1 到 10。

这两种循环的功能足够相似，以至于 `for` 和 `while` 通常可以互换使用。尽管如此，经验会表明 `for` 循环更适合做 *已知次数* 的事情，而 `while` 用于条件将为真 *未知次数* 的情况。

在本章的最后一个示例中，将使用 `for` 循环重写之前创建的日历脚本，以替换其中的两个 `foreach` 循环。

### 使用循环

**1.** 在文本编辑器或 IDE 中打开 `calendar.php`（参考 [脚本 2.6](#ch02.html#ch02ex06)）。

**2.** 删除 `$days` 和 `$years` 数组的创建（第 18-19 行）。

