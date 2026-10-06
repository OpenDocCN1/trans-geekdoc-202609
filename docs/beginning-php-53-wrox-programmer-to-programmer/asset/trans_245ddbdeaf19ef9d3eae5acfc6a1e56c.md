

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
$form = new HTML_QuickForm("form", "days_old.php", "",
array("style" => "width:30em;", true));
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
$dateOfBirth = mktime(0, 0, 0, $value["M"], $value["d"], $value["Y"]);
$secondsOld = $currentDate - $dateOfBirth;
$daysOld = (int) ($secondsOld / 60 / 24);
echo "<p>你出生于 " . date("j S, Y", $dateOfBirth) . "。</p>";
echo "<p>你今年 " . number_format($daysOld) . " 天" . ($daysOld != 1 ? "s " : " ") .old。</p>";
}
?>
</body>
</html>
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
$form = new HTML_QuickForm("form", "days_old.php", "",
array("style" => "width:30em;", true));
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
$dateOfBirth = mktime(0, 0, 0, $value["M"], $value["d"], $value["Y"]);
$secondsOld = $currentDate - $dateOfBirth;
$daysOld = (int) ($secondsOld / 60 / 24);
echo "<p>你出生于 " . date("j S, Y", $dateOfBirth) . "。</p>";
echo "<p>你今年 " . number_format($daysOld) . " 天" . ($daysOld != 1 ? "s " : " ") .old。</p>";
}
?>
</body>
</html>
```

## 如何工作

此脚本演示了如何使用 PHP 日期函数，以及 HTML_QuickForm PEAR 包的一些高级功能。首先，脚本输出 XHTML 页面头部，链接到公共样式表 common.css（来自第 2 章），并包含额外的 CSS 规则来设置表单。

PHP 代码开始包含两个 PEAR 包，创建一个新的 `HTML_QuickForm` 对象。此表单使用 HTTP 方法并将数据发送到同一脚本（`days_old.php`）。表单的 `trackSubmit` 属性也被设置为 `true`，以便脚本可以检测表单是否已提交。

