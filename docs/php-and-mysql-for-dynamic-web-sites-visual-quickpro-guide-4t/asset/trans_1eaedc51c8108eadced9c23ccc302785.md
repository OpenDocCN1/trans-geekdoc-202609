
# 多维数组

## PHP 脚本示例

```php
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Multidimensional Arrays</title>
</head>
<body>
<p>Some North American States, Provinces, and Territories:</p>
<?php # Script 2.7 - multi.php

// Create one array:
$mexico = array(
    'YU' => 'Yucatan',
    'BC' => 'Baja California',
    'OA' => 'Oaxaca'
);

// Create another array:
$us = array(
    'MD' => 'Maryland',
    'IL' => 'Illinois',
    'PA' => 'Pennsylvania',
    'IA' => 'Iowa'
);

// Create a third array:
$canada = array(
    'QC' => 'Quebec',
    'AB' => 'Alberta',
    'NT' => 'Northwest Territories',
    'YT' => 'Yukon',
    'PE' => 'Prince Edward Island'
);

// Combine the arrays:
$n_america = array(
    'Mexico' => $mexico,
    'United States' => $us,
    'Canada' => $canada
);

// Loop through the countries:
foreach ($n_america as $country => $list) {

    // Print a heading:
    echo "<h2>$country</h2><ul>";

    // Print each state, province, or territory:
    foreach ($list as $k => $v) {
        echo "<li>$k - $v</li>\n";
    }

    // Close the list:
    echo '</ul>';
} // End of main FOREACH.

?>
</body>
</html>
```

## 分步解释

### 3. 创建第二个和第三个数组

```php
$us = array(
    'MD' => 'Maryland',
    'IL' => 'Illinois',
    'PA' => 'Pennsylvania',
    'IA' => 'Iowa'
);

$canada = array(
    'QC' => 'Quebec',
    'AB' => 'Alberta',
    'NT' => 'Northwest Territories',
    'YT' => 'Yukon',
    'PE' => 'Prince Edward Island'
);
```

### 4. 将所有数组合并为一个

```php
$n_america = array(
    'Mexico' => $mexico,
    'United States' => $us,
    'Canada' => $canada
);
```

你不必非要创建三个数组然后将它们赋值给第四个数组来创建所需的多维数组，但我认为这样做更易于阅读和理解（在一步中定义多维数组会导致代码难看）。

`$n_america` 数组现在包含三个元素。每个元素的键是一个字符串，即国家名称。每个元素的值是该国所包含的州、省或地区的数组。

### 5. 开始主 `foreach` 循环

```php
foreach ($n_america as $country => $list) {
    echo "<h2>$country</h2><ul>";
}
```

遵循前面概述的语法，此循环将访问 `$n_america` 的每个元素。这意味着循环将运行三次。在循环的每次迭代中，`$country` 变量将存储 `$n_america` 数组的键（*Mexico*、*Canada* 或 *United States*）。同样在循环的每次迭代中，`$list` 变量将存储元素的值（相当于 `$mexico`、`$us` 和 `$canada`）。

为了输出结果，循环首先在 `H2` 标签中打印国家名称。由于州等信息应显示为 HTML 列表，因此也会打印初始无序列表标签 (`<ul>`)。

### 6. 创建第二个 `foreach` 循环

```php
foreach ($list as $k => $v) {
    echo "<li>$k - $v</li>\n";
}
```

此循环将遍历每个子数组（先是 `$mexico`，然后是 `$us`，最后是 `$canada`）。在该循环的每次迭代中，`$k` 将存储缩写，`$v` 存储全称。两者都在 HTML 列表标签内打印出来。同时也使用了换行符，以便更好地格式化 HTML 源代码。

### 7. 完成外层 `foreach` 循环

```php
echo '</ul>';
} // End of main FOREACH.
```

内层 `foreach` 循环结束后，外层 `foreach` 循环必须关闭第 5 步开始的无序列表。

### 8. 完成 PHP 和 HTML

```php
?>
</body>
</html>
```

### 9. 保存并测试

将文件保存为 `multi.php`，将其放在你的 Web 目录中，并在 Web 浏览器中测试。

### 10. 检查 HTML 源代码

如果你愿意，可以查看 HTML 源代码，看看 PHP 生成了什么。

---

## 提示：来自 HTML 表单的多维数组

多维数组也可以来自 HTML 表单。例如，如果表单有一系列名为 `interests[]` 的复选框：

```html
<input type="checkbox" name="interests[]" value="Music" /> Music
<input type="checkbox" name="interests[]" value="Movies" /> Movies
<input type="checkbox" name="interests[]" value="Books" /> Books
```

接收页面中的 `$_POST` 变量将是多维的。`$_POST['interests']` 将是一个数组，其中 `$_POST['interests'][0]` 存储第一个被选中复选框的值（例如 Movies），`$_POST['interests'][1]` 存储第二个（Books），以此类推。注意只有被选中的复选框会被传递给 PHP 页面。

---

## 提示：来自选择菜单的多维数组

如果 HTML 表单的选择菜单允许多选，也会得到一个多维数组：

```html
<select name="interests[]" multiple="multiple">
    <option value="Music">Music</option>
    <option value="Movies">Movies</option>
    <option value="Books">Books</option>
    <option value="Napping">Napping</option>
</select>
```

同样，只有被选中的值会被传递给 PHP 页面。

---

# 数组与字符串

因为数组和字符串经常一起使用，PHP 有两个函数用于在它们之间转换：

```php
$array = explode(separator, $string);
$string = implode(glue, $array);
```

理解和使用这两个函数的关键在于 *separator*（分隔符）和 *glue*（粘合符）的关系。将数组转换为字符串时，你需要确定粘合符——即在生成的字符串中插在数组值之间的字符或代码。反之，将字符串转换为数组时，你需要指定分隔符，即标记什么应成为单独数组元素的标记。

例如，从一个字符串开始：

```php
$s1 = 'Mon-Tue-Wed-Thu-Fri';
$days_array = explode('-', $s1);
```

`$days_array` 变量现在是一个五元素数组，*Mon* 索引为 `0`，*Tue* 索引为 `1`，以此类推。

```php
$s2 = implode(', ', $days_array);
```

`$s2` 变量现在是一个逗号分隔的日期列表：*Mon, Tue, Wed, Thu, Fri*。

---

## 数组排序

数组相对于其他变量类型的众多优势之一是能够对其进行排序。PHP 包含几个可用于数组排序的函数，语法都很简单：

```php
$names = array('Moe', 'Larry', 'Curly');
sort($names);
```

排序函数执行三种类型的排序：

1. **按值排序，丢弃原键**，使用 `sort()`。重要的是要理解，排序过程后数组的键将被重置，因此*如果键值关系很重要，则不应使用* `sort()`。
2. **按值排序并保留键**，使用 `asort()`。
3. **按键排序**，使用 `ksort()`。

如果将它们分别改为 `rsort()`、`arsort()` 和 `krsort()`，则每种都可以按逆序排序。

为了演示数组排序的效果，下一个脚本将创建一个电影标题和评分（我有多喜欢它们，按 1 到 10 的等级）的数组，然后以不同方式显示此列表。

### 对数组进行排序

#### 1. 开始一个新的 PHP 文档

在文本编辑器或 IDE 中创建一个新的 PHP 文档，命名为 `sorting.php`，从初始 HTML 开始（**脚本 2.8**）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```
