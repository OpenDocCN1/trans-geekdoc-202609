
这段代码运行后，`$localTime` 保存了 1972 年 6 月 6 日 UTC 晚上 7:32 的时间戳（这是印地纳利斯时间同一天的下午 2:32）。同时，`$gmTime` 保存了 GMT 下午 2:32 时间戳；换句话说，没有发生时间转换。`mktime()` 和其他日期相关函数使用 `php.ini` 文件中 `date.timezone` 指令设置的时区。但你可以使用 `date_default_timezone_set()` 函数更改 PHP 脚本所使用的时区。更多细节请参见 http://www.php.net/date.timezone_set 的 PHP 手册。

## 从日期和时区创建时间戳

`mktime()` 是非常棒的如果你传递的参数位于你计算机的时区——它将提供的时间转换为 UTC 以便可以作为时间戳返回。然而，有时能够存储一个已经处于 GMT 时区的日期和时间是有用的。例如，许多 HTTP 请求头和其他 TCP/IP 协议使用的日期和时间始终是 GMT。

要从 GMT 日期和时间创建时间戳，请使用 `gmtime()`。它的工作方式与 `mktime()` 完全相同，只是它期望参数是 GMT 时间。例如，假设运行你 PHP 脚本的计算机位于印地纳利斯时区（比 GMT 晚 5 小时），并且正在运行以下代码：

```php
$localTime = mktime( 14, 32, 12, 1, 6, 1972 );
$gmTime = gmtime( 14, 32, 12, 1, 6, 1972 );
```

这段代码运行后，`$localTime` 保存了 1972 年 6 月 6 日 UTC 晚上 7:32 的时间戳（这是印地纳利斯时间同一天的下午 2:32）。同时，`$gmTime` 保存了 GMT 下午 2:32 时间戳；换句话说，没有发生时间转换。`mktime()` 和其他日期相关函数使用 `php.ini` 文件中 `date.timezone` 指令设置的时区。但你可以使用 `date_default_timezone_set()` 函数更改 PHP 脚本所使用的时区。更多细节请参见 http://www.php.net/date.timezone_set 的 PHP 手册。

（注：原文后部分存在大量重复段落，译文已按要求进行去重处理并确保逻辑连贯。）

## 第三部分：PHP 练习

`getdate()` 接受一个时间戳并返回一个与提供的时间戳对应的日期/时间值的关联数组。该数组包含以下键：

| 数组键 | 说明 | 可能的值 |
| --- | --- | --- |
| seconds | 秒组件 | 0 到 59 |
| minutes | 分钟组件 | 0 到 59 |
| hours | 小时组件，24小时制 | 0 到 23 |
| mday | 月份中的第几天 | 1 到 31 |
| wday | 数字形式的星期 | 0（星期日）到 6（星期六） |
| mon | 数字形式的月份 | 1 到 12 |
| year | 四位数字的年份 | 通常为 1970 到 2038 |
| yday | 年中的第几天 | 0 到 365 |
| weekday | 字符串形式的星期 | 星期日到星期六 |
| month | 字符串形式的月份 | 1月到12月 |
| 0 (零) | 时间戳 | 通常为 -2147483648 到 2147483647 |

你也可以不带时间戳调用 `getdate()` 来返回当前日期和时间的组件。
以下是几个 `getdate()` 的示例：

```php
// 显示 "John Lennon was born on 9 October, 1940*"
$johnLennonsBirthday = strtotime("9 October, 1940");
$d = getdate($johnLennonsBirthday);
echo "John Lennon was born on " . $d["mday"] . ", " . $d["month"] . ", " . $d["year"] . ".<br />";
// 显示例如 "17:31"
$t = getdate();
echo "The current time is " . $t["hours"] . ":" . $t["minutes"] . ".<br />";
```

如果你想从时间戳中提取单个日期或时间组件，可以使用 `date()`。此函数接受两个参数：一个格式字符串和一个可选的时间戳（如果省略时间戳，则使用当前日期和时间）。格式字符串决定了返回的组件以及返回的格式，如下所示：

| 格式字符串 | 说明 |
| --- | --- |
| B | 互联网时间——一种无时间的十进制度量。详情参阅 http://en.wikipedia.org/wiki/UTC_Time |
| d | 月份中的第几天 |
| h | 小时（12小时制） |
| H | 小时（24小时制） |
| i | 分钟 |
| I | 如果夏令时（DST）生效则为 1，否则为 0 |
| L | 如果日期是闰年则为 1，否则为 0 |
| M | 月份数字（1–12） |
| s | 秒 |
| t | 月份天数（28, 29, 30 或 31） |
| U | 时间戳 |
| w | 数字形式的星期（0 是星期日） |
| W | 年内的周数（从 1 开始计数） |
| y | 二位数字的年份 |
| Y | 四位数字的年份 |
| z | 年中的第几天（0 是 1月） |
| Z | 计算机时间与 UTC 的偏移量（秒） |

如你所见，你可以使用 `date()` 从数据中检索各种信息。这是一个示例：

```php
$d = strtotime("February 18, 2000 7:49am");
// 显示 "The year 2000 is a leap year."
echo "The year " . date("Y", $d) . " is " . (date("L", $d) ? "" : "not") . " a leap year.<br />";
// 显示 "The month in question has 29 days."
echo "The month in question has " . date("t", $d) . " days.<br />";
```

## 格式化日期字符串

尽管计算机喜欢使用时间戳，但在许多情况下，你需要将时间戳转换为日期的字符串表示。常见场景包括在网页上显示日期，或将日期传递给期望特定格式日期的另一个应用程序。

PHP 的 `date()` 函数允许你将时间戳转换为日期字符串。它的工作方式与 `strtotime()` 类似，你传递一个格式字符串和一个要处理的时间戳（省略则转换当前日期和时间）。主要区别在于格式字符串可以包含多个字符，允许你生成包含任意数量日期和时间组件的日期字符串。你还可以使用在使用 `date()` 时不可用的额外格式化字符。以下是 `date()` 格式字符串中允许的日期相关格式化字符列表：

| 字符 | 说明 |
| ---|---|
| j | 不带前导零的月份第几天 |
| d | 月份中的两位数几几，必要时补导零 |
| D | 三字母字符串形式的星期（例如 "Mon"） |
| l | 完整单词形式的星期（例如 "Monday"） |
| w | 数字形式的星期（0=星期日，6=星期六） |
| N | ISO-8601 数字形式的星期（1=星期一，7=星期日） |
| S | 添加到月份日期后的英文序数后缀（"st", "nd", "rd", 或 "th"）。通常与 j 格式字符配合使用 |
| z | 年中的第几天（代表 1月1日） |
| W | 年内的两位数 ISO-8601 周数，必要时补导零。从星期一开始。第一周是第 01 周 |
| M | 三字母字符串形式的月份（例如 "Jan"） |
| F | 完整单词形式的月份（例如 "January"） |
| n | 数字形式的月份（1-12） |
| m | 两位数的月份，必要时补导零（01–12） |
| t | 月份天数（28, 29, 30 或 31） |
| Y | 二位数字的年份 |
| Y | 四位数字的年份 |

| 字符 | 说明 |
|--- |--- |
| o (小写 "o") | ISO-8601 年份。通常与 Y 的值相同；但 ISO-8601 年份属于上一年或下一年，会使用该年份。例如，2000年1月1日的 ISO-8601 年份是 1999 |
| L | 如果日期是闰年则为 1，否则为 0 |

| 格式字符串 | 说明 |
| --- | --- |
| g | 12小时制的小时 |
| h | 12小时制的小时 |
| G | 24小时制的小时 |
| H | 24小时制的小时 |
| i | 分钟 |
| s | 秒 |
| u | 微秒 |
| B | 互联网时间——一种无时间的十进制度量。参阅 http://en.wikipedia.org/ |
| a | "am" 或 "pm" |
| A | "AM" 或 "PM" |
| e | 时区标识符（如 UTC） |
| T | 时区缩写（如 "EST"） |
| O | 不带冒号的时区偏移 (+hhmm) |
| P | 带冒号的时区偏移 (+hh:mm) |
| Z | 秒为单位的时区偏移 |

# 第16 章：PHP 与外部世界

```php
$d = strftime("March 28, 2006 9:42am");
// 显示 "March 28, 2006 9:42 AM"
echo date("F j, Y:g a", $d) . "<br />";
// 显示 "March 28, 2006 2:42 PM"
echo gmdate("F j, Y:g A", $d) . "<br />";
```

## 检查日期值

打开一个脚本来处理网站访问者输入的日期。例如，一个 Web 表单可能包含一个选择框（select），允许访问者输入出生月份、日期和年份。然而，在这种情况下，没有任何可以阻止访问者输入不存在的日期，例如 2009 年 2 月 31 日。显然，对用户输入的日期字段进行验证是一个好主意，确保他们提供了合法的日期。

PHP 的 `checkdate()` 函数接收日期的月份（1–12）、日期（1–31）和年份部分，如果日期有效则返回 true，如果无效则返回 false：

```php
echo checkdate(2, 31, 2009) . "<br />"; // 显示 "false"
echo checkdate(2, 28, 2009) . "<br />"; // 显示 "1" (true)
```

在将任何用户输入的日期传递给（例如）`microtime()` 转换为时间戳之前，调用 `checkdate()` 是一个很好的做法。

## 处理微秒

你在本章中看到的日期和时间函数处理的是整数时间戳——即表示秒数的时间戳。大多数情况下，这足够了。如果你需要额外的精度，请使用 PHP 的 `microtime()` 函数。与 `time()` 不同，`microtime()` 返回一个表示当前时间的时间戳，允许你更精确地确定当前时间：

```php
// 例如显示 "0.45968200 1230613358.46"
echo microtime();
```

如你所见，`microtime()` 返回一个由两个数字隔开的字符串。第一个数字是微秒部分，以秒的分数表示，第二个数字是秒的整数——即标准的整数时间戳。因此，前面代码段中的示例代表 1970 年 1 月 1 日午夜 (UTC) 之后的 1,230,613,358.459682 秒。

如果你愿意，可以通过传递参数 `true` 让 `microtime()` 返回秒的浮点数，而不是由两个数字组成的字符串：

```php
// 例如显示 "1230613358.46"
echo microtime(true);
```

# 第三部分：PHP 练习

注意，使用 `echo()` 只显示保留两位小数的秒数。为了更精确地查看浮点数，可以使用 `printf()`：

```php
// 例如显示 "1230613358.459682"
printf("%0.6f", microtime(true));
```

一个常见的场景是，`microtime()` 值在对代码进行基准测试以寻找速度瓶颈之前非常有用，在从一个值中减去另一个值之后，你可以找到操作执行所需的时间。这里有一个例子：

```html
<!DOCTYPE html PUBLIC "//W3//DTD HTML 1.0 Strict//EN"
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>计时脚本执行</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>计时脚本执行</h1>
  <?php
  // 开始计时
  $startTime = microtime(true);
  // 执行操作
  for ($i=0; $i<10; $i++) {
    echo "<p>Hello, world!</p>";
  }
  // 停止计时
  $endTime = microtime(true);
  $elapsedTime = $endTime - $startTime;
  printf("<p>该操作花费了 %0.6f 秒来执行。</p>", $elapsedTime);
  ?>
</body>
</html>
```

你可以在图 16-1 中看到此脚本的示例输出。

## 第16 章：PHP 与外部世界

![](img/ede05b7b77968b82cbd9a513122fb183_520_0.png)

## 计时脚本执行

Hello world!

Hello world!

Hello world!

Hello world!

Hello world!

Hello world!

Hello world!

Hello world!

该操作花费了 0 秒来执行。

完成
图 16-1

## 尝试计算你的年龄天数

你可以利用对 PHP 日期处理函数的知识编写一个计算用户年龄天数的脚本。该脚本显示一个表单，要求用户输入出生日期，然后计算该日期与当前日期之间的差值（天数）。

将脚本保存为文档根目录下的 `days_old.php`。由于脚本使用了 `HTML_QuickForm` 和 `HTML_QuickForm_Renderer_Tableless` 包，请确保也安装了它们。你可以在上一节找到关于安装这些包的详细信息。

```html
<!DOCTYPE html PUBLIC "//W3//DTD HTML 1.0 Strict//EN"
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>你多大了？</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
  <style type="text/css">
    .error { background: #333; color: white; padding: 0.2em; margin: 0.2em; font-size: 0.9em; }
    fieldset { border: none; }
    ol {list-style: none; }
    input, select, textarea { float: none; margin: 1em 0; width: auto; }
    div.element { float: right; width: 57%; }
    div.element label { display: inline; float: none; }
    select { margin-right: 0.5em; }
  </style>
span.required { display: none; }
</head>
<body>
<h1>你多大了？</h1>
<?php
require_once("HTML/QuickForm.php");
require_once("HTML/QuickForm/Renderer/Tableless.php");
$form = new HTML_QuickForm("form", "days_old.php", "", array("style" => "width:30em;", true));
$form->removeAttribute("name");
$form->setRequired("");
$form->addAttribute(format => "MDY", "minYear" => 1902, "maxYear" => date("Y"));
$form->addAttribute("dateOfBirth", "你的出生日期");
$form->addAttribute("submit", "计算");
$form->addRule("dateOfBirth", "请输入有效的日期", "callback", checkdate);
if ($form->isSubmitted() && $form->validate()) {
$renderer = new HTML_QuickForm_Renderer_Tableless();
$form->accept($renderer);
echo $renderer->toHtml();
}
function checkdate($value) {
$currentDate = mktime();
