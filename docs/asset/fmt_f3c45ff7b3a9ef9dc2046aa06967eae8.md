
```sql
SELECT user_id, first_name FROM users WHERE email='?' AND pass=SHA1('?')
```

您将使用入站参数来表示提交的电子邮件地址和密码，但对同一查询中检索到的用户 ID 和名字使用出站参数。

---

### 步骤 7：更改错误报告

更改为使用：

```php
echo '<p>' . $stmt->error . '</p>';
```

此时脚本中的错误很可能是由于对必须唯一的列使用了重复值。如果查询中存在语法错误，那将在准备查询后出现在 `$mysqli->error` 中。

---

### 步骤 8：更新语句关闭方式

```php
$stmt->close();
unset($stmt);
```

---

### 步骤 9：更改数据库连接关闭方式

```php
$mysqli->close();
unset($mysqli);
```

---

### 步骤 10：保存并测试

保存脚本，将其放在您的 Web 目录中，并在 Web 浏览器中测试。

![图 16-6](img/16_figure_06_f.jpg)

*HTML 表单，用于发布新消息。*

![图 16-7](img/16_figure_07_g.jpg)

*新消息已成功存储在数据库中。*

---

### DateTime 类

PHP 5.2 版本新增了 `DateTime` 类。作为第 11 章 “Web 应用程序开发” 中介绍的日期和时间相关函数的替代方案，`DateTime` 类将您可能需要的所有操作日期和时间的功能打包在一起。它对于转换和比较日期时间特别有用。

首先，创建一个新的 `DateTime` 对象：

```php
$dt = new DateTime();
```

如果不向构造函数提供任何参数，生成的 `DateTime` 对象将表示当前日期和时间。要创建特定日期和时间的表示，请将其作为第一个参数提供：

```php
$dt = new DateTime('2011-04-20');
$dt = new DateTime('2011-04-20 11:15');
```

PHP 手册中详细列出了指定日期和时间的许多可接受格式。您也可以在创建对象后，使用 `setDate()` 和 `setTime()` 方法来设定日期或时间。`setDate()` 方法按顺序接收所需的年、月、日。`setTime()` 方法将小时、分钟和可选的秒作为其参数：

```php
$dt = new DateTime();
$dt->setDate(2001, 4, 20);
$dt->setTime(11, 15);
```

`DateTime` 对象仅允许您设定有效的日期和时间，对于无效的日期时间会抛出**异常**：

```php
$dt = new DateTime('2011-13-42');
```

![异常示例](img/16_figure_08_a.jpg)

*尝试使用无效日期或时间创建 `DateTime` 对象会导致异常。*

异常是之前未介绍过的主题。过程式代码可能会生成错误，而对象则**抛出异常**（确实称为“抛出”）。随着您进一步深入面向对象编程（OOP），您将学习如何使用 `try...catch` 块来“捕获”并处理抛出的异常。

`DateTime` 构造函数接受一个可选的第二个参数，即要使用的时区。如果未提供，则适用于该 PHP 安装的默认时区。您也可以事后使用 `setTimezone()` 更改时区。请注意，`setTimezone()` 方法和构造函数都接受 `DateTimeZone` 对象作为参数，而不是字符串：

```php
$tz = new DateTimeZone('America/New_York');
$dt->setTimezone($tz);
```

拥有 `DateTime` 对象后，您可以通过添加和减去时间段来操作其值。一种方法是使用 `modify()` 方法：

```php
$dt->modify('+1 day');
$dt->modify('-1 month');
$dt->modify('next Thursday');
```

您可以提供给该方法的值非常灵活，对应于 `strtotime()` 函数（将字符串转换为时间戳；详见 PHP 手册）中可用的值。

`add()` 方法用于向表示的日期和时间添加一个时间段。它接受一个类型为 `DateInterval` 的对象作为唯一参数：

```php
$di = new DateInterval(interval);
$dt->add($di);
```

设置间隔有一种特定的表示法，始终以字母 `P`（“period”，时期）开头。之后，添加一个整数和一个时期标识符：`Y` 代表年；`M` 代表月；`D` 代表日；`W` 代表周；`H` 代表小时；`M` 代表分；`S` 代表秒。您可能会好奇字母 `M` 如何同时代表月和分：这是可能的，因为小时、分钟和秒也应以 `T`（“time”，时间）为前缀。这些字符应按从大到小的顺序组合（即从年到秒）。以下是一些示例：

- `P3W` 代表三周
- `P2Y3M` 代表两年三个月
- `P2M3DT4H18M43S` 代表两个月、三天、四小时、18 分钟和 43 秒

`sub()` 方法的功能与 `add()` 完全相同，但从对象中减去时间段：

```php
$di = new DateInterval('P2W'); // 2 weeks
$dt->sub($di);
```

`diff()` 方法返回一个 `DateInterval` 对象，反映两个 `DateTime` 对象之间的时间差：

```php
$diff = $dt->diff($dt2);
```

`DateInterval` 类定义了几个属性来表示计算出的间隔：`y` 代表年，`m` 代表月，`d` 代表日，`h` 代表小时，`i` 代表分，`s` 代表秒，以及 `days`，也代表天数。

您应该熟悉的最后一个 `DateTime` 类方法是 `format()`，它返回按您想要的格式表示的日期：

```php
echo $dt->format(format);
```

对于格式化，您可以使用与第 11 章中介绍的 `date()` 函数相同的字符。

#### DateTime 使用演示

为了演示所有这些信息，接下来的脚本将执行许多网站所需的任务：允许用户输入两个日期以创建一个范围。该脚本将对提交的日期执行高质量验证，并计算它们之间的天数。所呈现的信息可以很容易地应用于酒店注册系统等场景。该脚本将使用刚才介绍的大量信息，甚至会直接比较两个 `DateTime` 对象，这是 PHP 5.2.2 版本起支持的功能。

![一个用于输入两个日期的简单表单，并指明了格式。](img/16_figure_09_b.jpg)

![如果提交了两个有效日期，且结束日期在开始日期之后，则会再次显示这些日期，并显示计算出的间隔。](img/16_figure_10_c.jpg)

### 脚本 16.5：模拟常见的日期选择功能

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

### 使用 DateTime 类

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

请注意，通常我建议在条件语句中始终使用花括号，但为了让代码尽可能简短，我省略了它们，并将整个结构保持在单行上。同时请记住，一旦函数执行了 `return` 语句，函数就会立即退出。

**9.** 如果提供的日期不是有效日期，则返回 `false`：

```php
if (!checkdate($array[0], $array[1], $array[2])) return false;
```

与步骤 8 类似，这段代码调用 PHP 的 `checkdate()` 函数来确认提供的日期确实存在。如果日期不存在（例如 `13/43/2011`），函数再次返回 `false`。

**10.** 返回日期数组并结束函数：

```php
return $array;
} // End of validate_date() function.
```

如果提供的日期格式正确且对应一个存在的日期，该函数将返回日期元素数组。

**11.** 如果表单已提交，验证用户提交的值：
