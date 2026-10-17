
| Platform: Linux Mandrake 10 | |

| 完成 本地域网 | |

从 HTML 表单提交的数据以输入名称（`name`）作为键，输入内容作为其值。这些内容可以存储在数组中，以便使用键名检索用户输入的数据。

# PHP 5 快速入门

### 从 1 开始的索引

默认情况下，所有数组元素的索引从零开始，因此一号元素的索引是零。这可能会引起困惑，但 PHP 提供了一种从从一开始索引的方法，使得一号元素的索引也是一号。

解决方案是使用 `=>` 语法为第一个元素值显式指定一个整数键 `1`。后续所有值将采用连续的索引号，正确地与它们在数组中的位置匹配。

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

### 数组操作

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

## 生成动态内容

本章演示了 PHP 如何根据浏览器类型、日期和时间、随机生成的数字或用户输入提供动态内容。它还说明了字符串处理以及如何重定向客户端浏览器。

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

### 识别浏览器与平台

PHP 创建了一些非常有用的变量，可以在书中使用的 `phpinfo.php` 页面看到；这些包括环境变量 `HTTP_AGENT`，用于识别用户的浏览器和操作系统。

下面的脚本使用 `getenv()` 函数为此环境赋值，然后将其输出到页面上：

```html
<html><head><title>获取浏览器与平台</title></head><body><?php $viewer = getenv("HTTP_AGENT"); echo("Browser details:$viewer");</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_63_0.png)

Windows 中的细节识别出 Internet Explorer 6.0 是运行在 Windows XP（显示为 NT）上的兼容浏览器。在 Linux 中，真正的 Mozilla 浏览器被正确识别出来。

![](img/7faa63a7fa0add8f53300594ebae949f_63_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_63_2.png)

### ...续

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

### 服务器日期与时间

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

### 与时间相关的内容

当前日期或时间可以用于创建适用于当天、月份或一天中特定时段动态内容。下面的示例脚本将根据用户访问服务器的时间写入一条合适的消息。

![](img/7faa63a7fa0add8f53300594ebae949f_66_0.png)

```html
<head><title>Greetings</title></head>
<body
<?php $hour = date("G");
$now = date("g:i a");

$msg = "Good Evening.";
if ($hour < 18) { $msg = "Good Afternoon."; }
if ($hour < 12) { $msg = "Good Morning."; }

echo ("$msg The time is \$now");
?>
</body></html>
```

此脚本评估返回的当前小时的整数值。显示的消息可能不利其他时区的用户。

![](img/7faa63a7fa0add8f53300594ebae949f_66_1.png)

| 问候 | | | |
|---|---|---|------|
| 文件 编辑 视图 收藏 工具 帮助 | | | | |
| 地址 | http://localhost/greetings.php | Go |
早上好。时间是 11:30

| 问候 | | | | |
|---|---|---|------|
| 文件 编辑 视图 收藏 工具 帮助 | | | | |
| 地址 | http://localhost/greetings.php | Go |
下午好。时间是 3:35

| 问候 | | | | |
|---|---|---|------|
| 文件 编辑 视图 收藏 工具 帮助 | | | | |
| 地址 | http://localhost/greetings.php | Go |
晚上好。时间是 9:40

| 完成 | 本地局域网 |

### 随机数生成器

PHP 的 `rand()` 函数用于生成随机数。可以可选地作为 `rand()` 函数的参数指定一个从中选择随机数的范围，该范围包含最小值和最大值。例如，`rand(1,10)` 将在 1 到 10 之间选择一个数字。如果没有指定范围，随机数将在零和默认最大值 32767 之间。

随机数生成器应该设置种子，以防止生成规律性的数字。这是通过使用 `rand()` 函数实现的，它接受种子数作为参数。通常，种子数指定为使用 PHP `microtime()` 函数表示的微秒精度的当前时间乘以一百万。

此示例以常用方式使用 `rand()` 函数，然后生成 1 到 100 范围内的随机数。

![](img/7faa63a7fa0add8f53300594ebae949f_67_0.png)

```html
<html><head><title>Random Numbers</title></head>
<body>
<?php

rand(microtime() * 1000000);
$num = rand(1, 100);
echo("Microtime:" . microtime() . "<br>");
echo("A random number:" . $num . "<br>");
$num = rand(1, 100);
echo("Another random number:" . $num);

?>
</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_67_1.png)

| 随机数 | |
|---|---|
| 文件 编辑 视图 收藏 工具 帮助 |
| 地址 http://localhost/random.php Go |
| Microtime:0.36768200 1086778854 |
| A random number:46 |
| Another random number:17 |

### ...续上

随机数生成器用于在网页上生成不同的横幅，以便内容每次访问时都能变化。下面的示例生成一个随机数，然后根据该数字选择横幅图像以及相关的超链接。

![](img/7faa63a7fa0add8f53300594ebae949f_68_0.png)

```html
<html><head><title>Random Images</title></head>
<body bgcolor="#000000">
<?php
rand( microtime() * 100000 );
$num = rand( 1, 4);

switch ($num) {
case 1 : $car="alfa.jpg"; $url="alfa.php"; break;
case 2 : $car="ferari.jpg"; $url="ferari.php"; break;
case 3 : $car="jaguar.jpg"; $url="jaguar.php"; break;
case 4 : $car="porsche.jpg"; $url="porsche.php"; break;
}
$banner = "<a href='$url'>\n";
$banner .= "<img src='$car'>";
$banner .= " width='380' height='110' border='0'>";
echo( $banner );
?>
</body>
```

![](img/7faa63a7fa0add8f53300594ebae949f_68_1.png)

这四个横幅图像和链接位于 Apache 的 htdocs 文件夹中，与随机数文件并列。

在这种情况下，随机数被选择，横幅图像被显示，点击它将跳转到相应的页面。

### 获取表单数据

PHP 非常擅长处理表单提交的数据。下面的简单表单包含一组用于获取值的输入字段。当表单提交时，这些值将发送到服务器。通过 `rand()` 函数设置种子，可以防止生成规律性的数字。

| 问候 | | | | |
|---|---|---|------|
| 文件 编辑 视图 收藏 工具 帮助 | | | | |
| 地址 | http://localhost/greetings.php | Go |
早上好。时间是 11:30

| 问候 | | | | |
|---|---|---|------|
| 文件 编辑 视图 收藏 工具 帮助 | | | | |
| 地址 | http://localhost/greetings.php | Go |
下午好。时间是 3:35

| 问候 | | | | |
|---|---|---|------|
| 文件 编辑 视图 收藏 工具 帮助 | | | | |
| 地址 | http://localhost/greetings.php | Go |
晚上好。时间是 9:40

| 完成 | 本地局域网 |

### 随机数生成器

PHP `rand()` 函数用于生成随机数。可以可选地作为 `rand()` 函数的参数指定一个从中选择随机数的范围，该范围包含最小值和最大值。例如，`rand(1,10)` 将在 1 到 10 之间选择一个数字。如果没有指定范围，随机数将在零和默认最大值 32767 之间。

随机数生成器应该设置种子，以防止生成规律性的数字。这是通过使用 `rand()` 函数实现的，它接受种子数作为参数。通常，种子数指定为使用 PHP `microtime()` 函数表示的微秒精度的当前时间乘以一百万。

此示例以常用方式使用 `rand()` 函数，然后生成 1 到 100 范围内的随机数。

### 续

![](img/7faa63a7fa0add8f53300594ebae949f_72_0.png)
