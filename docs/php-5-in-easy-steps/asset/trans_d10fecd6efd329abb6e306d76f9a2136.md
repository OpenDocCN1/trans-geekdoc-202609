

# 数组的键和值

PHP 数组元素不是包含单个数据值，而是每个元素可以包含一个键值对，其中键可以在脚本中用于引用其关联的值。

在向数组元素分配键值对时，键名（用引号括起来）应该放在前面，紧随其后的是 "=>" 字符，然后是值的内容。建议使用单引号包裹键名，以将其区别于普通字符串。

要引用该值，只需用带引号的键代替数组索引数字即可；例如，`Arr['key']`。

下面的示例创建了一个包含三个元素的数组，这些元素包含键值对。在页面上输出元素内容时，会获取元素内容，并使用每个键拼接其关联的值。

![](img/7faa63a7fa0add8f53300594ebae949f_59_0.png)

```html
<html
<head><title>键值数组元素</title></head>
<body><ol>
<?php
$arr = array('version' => 10,
'OS' => "Linux",'os' => " Mandrake ");
echo
( "Platform:". $arr['OS']. $arr['os']. $arr['version']);
?>
</ol></</body>></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_59_1.png)

键名对大小写敏感，因此 `$arr['OS']` 和 `$arr['os']` 指向不同的数组

| 键值数组元素 | |
|---|---|
| 文件 编辑 视图 收藏 工具 帮助 | |
| 地址 http://localhost/keyarray.php | 访问 |
| Platform: Linux Mandrake 10 | |
| 完成 本地域网 | |

从 HTML 表单提交的数据以输入名称（name）作为键，输入内容作为其值。这些内容可以存储在数组中，以便使用键名检索用户输入的数据。

PHP 5 快速入门

# 从 1 开始的索引

默认情况下，所有数组元素的索引从零开始，因此一号元素的索引是零。这可能会引起困惑，但 PHP 提供了一种从从一开始索引的方法，使得一号元素的索引也是一号。

解决方案是使用 `=>` 语法为第一个元素值显式指定一个整数键 1。后续所有值将采用连续的索引号，正确地与它们在数组中的位置匹配。

下面的示例演示了这种技术，它使一个包含五个元素的数组索引为 1-5，而不是默认的 0-4。每个元素通过循环写在页面上，该循环现在可以方便地通过其索引位置正确引用每个元素。

![](img/7faa63a7fa0add8f53300594ebae949f_60_0.png)

```html
<html><head><title>从 1 开始的数组索引</title></head>
<body><ol>
<?php
$arr = array(1 => "1st", "2nd", "3rd", "4th", "5th" );

for($si = 1; $si <= sizeof($arr); $si++) {
echo "Position $si - Element value: $arr[$si]<br>");
}
?>
</ol></</body>></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_60_1.png)

# 数组操作

通过许多特殊的数组函数可以轻松操作 PHP 数组。`array_merge()` 函数允许合并两个数组。这需要两个数组名作为参数，并将第二个数组的元素添加到第一个数组的元素之后。可以使用 `array_slice()` 函数选择数组元素的指定范围，该函数接收数组名以及所需的起始和结束位置。数组元素可以使用 `shuffle()` 函数进行随机重排。下面的示例演示了这些函数的用法。

![](img/7faa63a7fa0add8f53300594ebae949f_61_0.png)

```html
<html><head><title>操作数组</title></head>
<body><ol>
  <?php $arr1 = array("Alpha", "Bravo", "Charlie");
  $arr2 = array("Delta", "Echo", "Foxtrot");

  $arr = array_merge($arr1, $arr2);
  foreach ($arr as $value) { echo("$value "); }
  echo("<hr>");

  $arr = array_slice($arr, 1, 4 );
  foreach ($arr as $value) { echo("$value "); }
  echo("<hr>");

  rand( (float)microtime() * 1000000 ); shuffle($arr);
  foreach ($arr as $value) { echo("$value "); }
?></ol></</body>></html>
```

`rand()` 为 `shuffle()` 函数提供了第一个种子。更多细节请参阅第 66 页的随机数示例。

![](img/7faa63a7fa0add8f53300594ebae949f_61_1.png)

| 操作数组 | |
|---|---|
| 文件 编辑 视图 收藏 工具 帮助 | |
| 地址 http://localhost/slicearray.php | 访问 |
| Alpha Charlie Delta Echo | |
| Bravo Charlie Delta | |

# 生成动态内容

本章演示了 PHP 如何根据浏览器类型、日期和时间、随机生成的数字或用户输入提供动态内容。它还说明了字符串处理以及如何重定向客户端浏览器。

# 
- 识别浏览器与平台 | 62
- 服务器日期与时间 | 64
- 特定时间的内容 | 65
- 随机数生成器 | 66
- 获取表单值 | 68
- 显示提交的值 | 70
- 操作的值 | 72
- 刷新页面 | 74
- PHP 与移动设备 | 78

![](img/7faa63a7fa0add8f53300594ebae949f_62_0.png)

# 识别浏览器与平台

PHP 创建了一些非常有用的变量，可以在书中使用的 `phpinfo.php` 页面看到；这些包括环境变量 `HTTP_AGENT`，用于识别用户的浏览器和操作系统。

下面的脚本使用 `getenv()` 函数为此环境赋值，然后将其输出到页面上：

```html
<html><head><title>获取浏览器与平台</title></head><body><?php $viewer = getenv("HTTP_AGENT"); echo("Browser details:$viewer");</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_63_0.png)

Windows 中的细节识别出 Internet Explorer 6.0 是运行在 Windows XP（显示为 NT）上的兼容浏览器。在 Linux 中，真正的 Mozilla 浏览器被正确识别出来。

![](img/7faa63a7fa0add8f53300594ebae949f_63_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_63_2.png)

PHP 5 快速入门

# ...续

`HTTP_AGENT` 环境变量包含的信息可以使用 `preg_match()` 函数创建适用于浏览器的动态内容。它尝试匹配指定的字符串模式，语法如下：

```
preg_match("/string-to-seek", "string-to-search");
```

下面的示例尝试识别浏览器和平台。如果没有找到匹配项，则提供默认字符串。然后将相应的字符串输出到页面上。

```html
<html><head><title>浏览器内容</title></head>
<body>
  <?php $viewer = getenv("HTTP_AGENT");
  $browser = "an unidentified browser";
  if (preg_match("/MSIE/i", "$viewer")) {
    $browser = "Internet Explorer";
  } else if (preg_match("/Netscape/i", "$viewer")) {
    $browser = "Netscape";
  } else if (preg_match("/Opera/i", "$viewer")) {
    $browser = "Opera";
  }
  $platform = "an unidentified operating system";
  if (preg_match("/Windows/i", "$viewer")) {
    $platform = "Windows";
  } else if (preg_match("/Linux/i", "$viewer")) {
    $platform = "Linux";
  }
  echo("You're using $browser on $platform");
</body>
</html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_64_0.png)

`i` 关包含在 `preg_match()` 的第一个参数中，以确保不区分大小写的搜索。

![](img/7faa63a7fa0add8f53300594ebae949f_64_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_64_2.png)

6. 生成动态内容

# 服务器日期与时间

PHP `date()` 函数返回服务器当前的日期和时间，根据指定的参数进行格式化。参数如下表所示，示例在页面底部：

| 字符 | 含义 |
|---|---|
| a / A | 输出 "am" 或 "pm" / "AM" 或 "PM" |
| g / h | 12小时制小时 (1-12) / (01-12) |
| G / H | 24小时制小时 (0-23) / (00-23) |
| i | 分钟 (00-59) |
| s | 秒 (00-59) |
| Z | 时区偏移（秒）(-43200 到 43200) |
| U | 自 1970 年 1 月 1 日 00:00:00 GMT 以来的秒数 |
| j / d | 日 (1-31) / (01-31) |
| D / l | 星期 (Mon-Sun) / (Monday-Sunday) |
| w | 星期几 (0-6)，从周日到周六 |
| M / F | 月份 (Jan-Dec) / (January-December) |
| n / m | 月 (1-12) / (01-12) |
| y / Y | 年 (05) / (2005) |
| z | 年中的第几天 (0-365) |
| t | 给定月份的天数 (28-31) |
| S | 英语序数后缀 ("th", "nd", "st") |

```
$today = date("M j, Y"); # Dec 10, 2005
$today = date("m.d.y"); # 12.10.05
$time = date("g:i a"); # 5.25 pm
$time = date("H:i:s"); // 05:25:30
```

