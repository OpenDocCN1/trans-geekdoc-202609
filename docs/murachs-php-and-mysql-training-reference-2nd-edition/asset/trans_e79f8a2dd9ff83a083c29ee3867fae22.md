

### 判断某一年是否为闰年

```php
function is_leap($date) {
    return ($date->format('L') == '1');
}
$year_2014 = is_leap(new DateTime('2014-1-1'));    // returns FALSE
$year_2016 = is_leap(new DateTime('2016-1-1'));    // returns TRUE
```

### 显示有关到期日的简单消息

```php
$now = new DateTime();
$exp = new DateTime('2015-4 first day of next month midnight');
if ($exp < $now) {
    echo 'Your card has expired.';
} else {
    echo 'Your card has not expired.';
}
```

### 显示有关到期日的详细消息

```php
$now = new DateTime();
$exp = '04/2015';    // Typical expiration date format

// Change exp from mm/YYYY to yyyy-mm
$month = substr($exp, 0, 2);
$year  = substr($exp, 3, 4);
$exp = $year . '-' . $month;

// Set expiration date and calculate the interval from current date
$exp = new DateTime($exp . ' first day of next month midnight');
$span = $now->diff($exp);

// Display a message
$span_text = $span->format('%y years, %m months, and %d days');
if ($span->format('%R') == '-') {
    echo 'Your card expired ' . $span_text . ' ago.';
} else {
    echo 'Your card expires in ' . $span_text . '.';
}
```

### 显示新年倒计时

```php
$now = new DateTime();
$new_year = new DateTime('next year Jan 1st');

// Calculate and format the time left until the new year
$span = $now->diff($new_year);
$md_left = $span->format('%m months, %d days');
$hms_left = $span->format('%H:%I:%S');

// Display a message
if ($now->format('md') == '0101') {
    echo 'Happy New Year!';
} else if ($now->format('md') == '1231') {
    echo "$hms_left remaining to the New Year.";
} else {
    echo "$md_left, and $hms_left remaining to the New Year.";
}
```

图 10-8 使用 DateTime 对象的示例

## 小结

完成本章的学习后，你就具备了在大多数 PHP 应用程序中处理日期和时间所需的全部技能。对于新应用程序，应该使用 DateTime 对象而不是时间戳。此外，应该在现有应用程序遇到 2038 年问题之前，将它们从时间戳转换为 DateTime 对象。

虽然 2038 年现在看起来还很遥远，但需要计算未来日期的应用程序可能会在 2038 年之前很久就遇到 2038 年问题。例如，一个需要处理未来 20 年日期的应用程序应在 2017 年之前完成转换。

## 术语

- 时间戳
- Unix 纪元
- 2038 年问题
- Y2K38 问题
- 绝对模板
- 相对模板
- 日期间隔

## 总结

- *时间戳*是一个整数，表示自 1970 年 1 月 1 日 GMT 午夜以来经过的秒数。

- 在大多数系统上，时间戳的上限是 2038 年 1 月 19 日。因此，该日期之后的日期会导致需要修复的 bug。这被称为 *2038 年问题* 或 *Y2K38 问题*，但可以通过使用 DateTime 对象而不是时间戳来避免。

- 要创建和格式化时间戳，可以使用函数。也可以使用函数来验证日期，并将日期的各个部分存储在数组中。

- DateTime 类提供了一种面向对象的方式来处理日期和时间。创建 DateTime 对象后，可以使用其方法来设置或修改日期，以及将时间戳转换为 DateTime 对象。

- *日期间隔*是一段时间，而不是一个时间点，可以存储在 DateInterval 对象中。然后，可以使用 DateTime 对象的方法来增加日期间隔、减去日期间隔，或创建一个表示两个日期之间间隔的 DateInterval 对象。

## 练习 10-1    编写处理日期的代码

在本练习中，你可以编写处理日期的 PHP 代码。

### 打开并测试应用程序

- 1. 启动 Chrome 浏览器，并运行 `ex_starts/ch10_ex1` 目录中的应用程序。为此，可以使用以下 URL：

   `http://localhost/ex_starts/ch10_ex1/`

   此时应显示一个页面，允许你输入发票日期和到期日。请注意，该页面以标准日期格式显示两个默认日期。

- 2. 单击“提交（Submit）”按钮。注意，这会显示一些标签，但不会显示任何日期或时间。

### 编写处理用户输入数据的代码

- 3. 打开该应用程序的 index.php 文件并查看代码。注意，它显示了当前日期前一个月的起始发票日期和当前日期后两个月的起始到期日。但是，该代码不会处理在文本框中输入的日期。

- 4. 打开该应用程序的 date_tester.php 文件并查看代码。注意，该代码使用 if 语句显示错误消息或日期和时间数据表。

- 5. 在 index.php 文件中，添加代码，使用文本框控件中输入的两个日期来显示一个数据表，计算日期和时间并按以下格式显示：

```text
Invoice date:        July 11, 2014
Due date:            October 11, 2014
Current date:        August 11, 2014
Current time:        4:40:16 pm.
Due date message:    This invoice is due in 0 years, 1 months,
                     and 29 days.
```

如果当前日期晚于到期日，到期日消息应采用以下格式：

```text
Due date message:    This invoice is 0 years, 2 months, and 25
                     days overdue.
```

- 6. 确保用户输入了两个日期。

- 7. 允许用户以 DateTime 类的构造函数可以解析的任何格式输入日期。这包括所有最常见的日期格式。

- 8. 确保用户输入的日期采用有效的日期格式。为此，可以使用 try/catch 语句来捕获 DateTime 类的构造函数无法解析日期时抛出的异常。关于 try/catch 语句的回顾，可参阅第 4 章。

- 9. 确保用户输入的到期日晚于发票日期。

- 10. 测试应用程序，确保其正确运行。

## 11 如何创建和使用数组

在第 4 章中，你已经初步了解了数组。在本章中，你将进一步学习如何创建和使用数组。数组在各种 PHP 应用程序中都很重要。例如，可以使用数组来存储购物车中的商品，然后通过操作数组来更新和显示这些商品。

| 主题 | 页码 |
| --- | --- |
| **如何创建和使用数组** | 314 |
| 如何创建数组 | 314 |
| 如何添加和删除元素 | 316 |
| 如何使用变量替换 | 316 |
| 如何使用 for 循环处理数组 | 318 |
| **如何创建和使用关联数组** | 320 |
| 如何创建关联数组 | 320 |
| 如何添加和删除元素 | 322 |
| 如何使用变量替换 | 322 |
| 如何使用 foreach 循环处理数组 | 324 |
| **如何使用函数处理数组** | 326 |
| 如何填充、合并、切片和拼接数组 | 326 |
| 如何处理队列和栈 | 328 |
| 如何获取元素的总和与乘积 | 330 |
| 如何搜索数组 | 330 |
| 如何对数组排序 | 332 |
| 如何修改数组 | 334 |
| **如何使用数组的数组** | 336 |
| 理解数组的数组 | 336 |
| 如何创建和使用数组的数组 | 338 |
| **任务列表管理器应用程序** | 340 |
| 用户界面 | 340 |
| 控制器代码 | 340 |
| 视图代码 | 342 |
| **小结** | 346 |

