

# DateTime 使用演示

为了演示所有这些信息，接下来的脚本将执行许多网站所需的任务：允许用户输入两个日期以创建一个范围。该脚本将对提交的日期执行高质量验证，并计算它们之间的天数。所呈现的信息可以很容易地应用于酒店注册系统等场景。该脚本将使用刚才介绍的大量信息，甚至会直接比较两个 `DateTime` 对象，这是 PHP 5.2.2 版本起支持的功能。

![一个用于输入两个日期的简单表单，并指明了格式。](graphics/16_figure_09_b.jpg)

![如果提交了两个有效日期，且结束日期在开始日期之后，则会再次显示这些日期，并显示计算出的间隔。](graphics/16_figure_10_c.jpg)

## 脚本 16.5：模拟常见的日期选择功能

该脚本接受并验证两个日期。

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>DateTime Usage</title>
    <style type="text/css" media="screen">
        body {
            font-family: Verdana, Arial, Helvetica, sans-serif;
            font-size: 12px;
            margin: 10px;
        }
        label { font-weight: bold; }
        .error { color: #F00; }
    </style>
</head>
<body>
<?php # Script 16.5 - datetime.php

// 默认将开始日期和结束日期设为今天和明天：
$start = new DateTime();
$end = new DateTime();
$end->modify('+1 day');

// 显示日期的默认格式：
$format = 'm/d/Y';

// 此函数验证提供的日期字符串。
// 如果有效，函数返回一个数组——月、日、年。
function validate_date($date) {

    // 将字符串拆分为各个部分：
    $date_array = explode('/', $date);

    // 如果不是 3 个项目，返回 FALSE：
    if (count($date_array) != 3) return false;

    // 如果不是有效日期，返回 FALSE：
    if (!checkdate($date_array[0], $date_array[1], $date_array[2])) return false;

    // 返回数组：
    return $date_array;

} // End of validate_date() function.

// 检查表单提交：
if (isset($_POST['start'], $_POST['end'])) {

    // 对两个日期调用验证函数：
    if ( (list($sm, $sd, $sy) = validate_date($_POST['start'])) && (list($em, $ed, $ey) = validate_date($_POST['end'])) ) {

        // 如果没问题，调整 DateTime 对象：
        $start->setDate($sy, $sm, $sd);
        $end->setDate($ey, $em, $ed);

        // 开始日期必须在前：
        if ($start < $end) {

            // 确定间隔：
            $interval = $start->diff($end);

            // 打印结果：
            echo "<p>The event has been planned starting on {$start->format($format)} and ending on {$end->format($format)}, which is a period of $interval->days day(s).</p>";

        } else { // 结束日期必须更晚！
            echo '<p class="error">The starting date must precede the ending date.</p>';
        }

    } else { // 日期无效！
        echo '<p class="error">One or both of the submitted dates was invalid.</p>';
    }

} // End of form submission.

// 显示表单：
?>
<h2>Set the Start and End Dates for the Thing</h2>
<form action="datetime.php" method="post">

    <p><label for="start_date">Start Date:</label> <input type="text" name="start_date" value="<?php echo $start->format($format); ?>" /> (MM/DD/YYYY)</p>
    <p><label for="end_date">End Date:</label> <input type="text" name="end_date" value="<?php echo $end->format($format); ?>" /> (MM/DD/YYYY)</p>

    <p><input type="submit" value="Submit" /></p>
</form>
</body>
</html>
```

---

## 使用 DateTime 类

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 脚本，命名为 `datetime.php`，从 HTML 开始（**脚本 16.5**）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>DateTime Usage</title>
```

**2.** 添加少量 CSS：

```css
<style type="text/css" media="screen">
body {
    font-family: Verdana, Arial, Helvetica, sans-serif;
    font-size: 12px;
    margin: 10px;
}
label { font-weight: bold; }
.error { color: #F00; }
</style>
```

只有 `error` 类在功能方面是重要的。它将以红色文本格式化错误消息。

**3.** 完成 head 并开始 body 和 PHP 部分：

```html
</head>
<body>
<?php # Script 16.5 - datetime.php
```

**4.** 创建两个 `DateTime` 对象：

```php
$start = new DateTime();
$end = new DateTime();
```

无论表单是否已提交，首先都会创建两个 `DateTime` 对象，它们都将使用当前日期和时间进行实例化。随后，一个或两个对象将被赋予新值。

**5.** 给结束日期加一天：

```php
$end->modify('+1 day');
```

默认情况下，当页面首次加载时，表单将预设今天为开始日期，明天为结束日期。要确定结束日期，只需修改对象的当前值，加上一天即可。

使用 `DateInterval` 对象和 `DateTime::add()` 方法，可以用如下方式做同样的事情：

```php
$day = new DateInterval('P1D');
$end->add($day);
```

**6.** 确定显示日期的默认格式：

```php
$format = 'm/d/Y';
```

脚本将在四个地方显示格式化后的日期版本。将首选格式——`MM/DD/YYYY`——赋值给变量，使得日后若需更改会更容易。

**7.** 开始定义一个函数：

```php
function validate_date($date) {
    $array = explode('/', $date);
```

两个提交的日期都需要通过几种方式进行验证，每当脚本或应用程序中有重复代码时，定义一个函数来执行该代码可能是合理的。该函数接受一个日期字符串（而非 `DateTime` 对象）作为其唯一参数。该字符串将是用户提交的值，类似 `08/02/2011`。函数做的第一件事是使用 `explode()` 函数将字符串拆分为三个独立的部分——月、日、年。生成的数组赋值给 `$array` 变量。

**8.** 如果数组不包含三个元素，返回 `false`：

```php
if (count($array) != 3) return false;
```

函数做的第一件事是确认它正好有三个离散的值可供使用，分别代表月、日、年。如果数组不包含三个元素，函数返回值 `false` 以指示日期无效。第 7 步中的 `explode()` 行和这一行会使任何不符合 `X/Y/Z` 模式的提交值无效（尽管那仍可能是 `cat/dog/zebra`）。

