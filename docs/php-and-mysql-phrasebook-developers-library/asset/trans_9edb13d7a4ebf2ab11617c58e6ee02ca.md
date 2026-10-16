
```php
function isLeapYear($year) {
    return ($year % 4 == 0 &&
        ($year % 100 != 0 || $year % 400 == 0));
}
```

你也可以使用 `DateTime::createFromFormat()`，如果发生错误它会返回 false。然而 `checkdate()` 可能更明确，因为函数名准确地描述了我们想要做的事情。

## 计算相对日期

```php
<?php
echo 'The license you have just bought is valid till ';
$expiry = time() + 30 * 24 * 60 * 60; // 30 days
echo strftime('%c', $expiry);
?>
```

有时你需要计算一个相对于当前日期的日期（例如，从现在起 30 天）。当然，你可以真正投入工作来计算这个值，考虑到它是星期几、是否为闰年以及是否与夏令时相关。

使用纪元时间戳要容易得多。例如，前面提到的找到未来 30 天的日期的任务。一天有 24 小时，1 小时有 60 分钟，1 分钟有 60 秒。因此，要获取当前时间戳（使用 `time()` 或 `date('U')`），你只需加上 `30 * 24 * 60 * 60`，就得到了所需日期的时间戳。然后你可以使用此时间戳来设置 cookie 的过期日期，或只是打印出有关此日期的一些信息。

如果你使用 DateTime 类，也可以使用 `add()` 和 `sub()` 方法，这些方法将在本章后面“计算两个日期之间的差异”部分中详细介绍。

## 创建可排序的时间戳

```php
<?php
function timestamp($t = null) {
    if ($t == null) {
        $t = time();
    }
    return date('YmdHis', $t);
}

echo 'Time stamp: ' . timestamp(time());
?>
```

在数据库中使用日期值并不总是明智的。数据库的不同语言版本、其驱动程序或底层操作系统在区域日期格式不匹配时可能会引起一些问题。

一种潜在的替代方案是使用时间戳。有几种不同的格式可用，但大多数格式具有以下结构：年-月-日 小时-分钟-秒。使用这种值顺序，日期的字符串表示可以轻松排序，从而允许在数据库中使用。

要创建这样的时间戳，只需对 `date()` 进行特殊调用即可。在前面的代码中，这被封装在一个函数中以便重复使用。

**提示：** 此格式也由 MySQL 用于其 TIMESTAMP 数据类型的表示。

## 将字符串转换为日期

```php
<?php
echo 'Yesterday: ' . date('r', strtotime('Yesterday')) . '<br />';
echo 'Today: ' . date('r', strtotime('Today')) . '<br />';
echo 'Tomorrow: ' . date('r', strtotime('Tomorrow')) . '<br />';
echo 'In one week: ' . date('r', strtotime('+1 week')) . '<br />';
echo 'One month before: ' . date('r', strtotime('-1 month')) . '<br />';
echo 'Last Sunday: ' . date('r', strtotime('Last Sunday')) . '<br />';
echo 'Next fantasy day: ' . var_export(@date('r', strtotime('Next fantasy day')), true);
?>
```

之前，你看到的是日期的数字表示——要么是日、月、年的三元组，要么是时间戳值。这次，你可以反过来，将日期/时间值的字符串表示转换为 epoch 值或 PHP 及其日期/时间函数中可用的其他内容。

所有魔力都放在了 PHP 函数 `strtotime()` 中。根据文档，它“将几乎任何英文文本日期/时间描述解析为 UNIX 时间戳。”听起来很神奇，而且确实很神奇。其基础是 GNU date 语法；本段开头的代码展示了一些 `strtotime()` 的示例。

**注意：** 在撰写本文时，`strtotime()` 在计算相对日期且即将发生夏令时变更或结束时表现出一些奇怪的行为。同样在撰写本文时，PHP 的日期/时间函数即将被重写和修改。

## 确定日出和日落

```php
<?php
echo 'Sunrise: ' .
    date_sunrise(time(), SUNFUNCS_RET_STRING, 48,
    11.5, 90, 1) . '<br />';
    echo 'Sunset: ' .
    date_sunset(time(), SUNFUNCS_RET_STRING, 48,
    11.5, 90, 1);
?>
```

根据当前位置和日期，日出和日落的时间可能差异很大。然而，存在根据纬度和经度确定此值的公式，并且 PHP 从 PHP 5 开始已将此功能集成到其核心中。你需要做的就是调用 `date_sunrise()` 和 `date_sunset()`。这两个函数都期望若干参数：

- 用于确定日出/日落的日期的时间戳（epoch 值）。
- 返回值的期望格式。`SUNFUNCS_RET_DOUBLE` 将时间作为浮点值返回（介于 0 和 23.99 之间），`SUNFUNCS_RET_STRING` 将其作为字符串返回（介于 00:00 和 23:59 之间），而 `SUNFUNCS_RET_TIMESTAMP` 返回 epoch 值。
- 纬度（北纬；南纬使用负值）。
- 经度（东经；西经使用负值）。
- 日出的天顶（以度为单位）。
- 相对于 GMT 的偏移量（以小时为单位）。

因此，前面的代码计算了德国慕尼黑的日出和日落，慕尼黑位于约 48° 北纬、11°30′ 东经，当天为当前日期。我检查过了：它有效！

## 使用日期和时间进行基准测试

```php
<?php
// ...

$start = microtimestamp();
$s = "";
for ($i=0; $i < 100000; $i++) {
    $s .= "$i";
}
$end = microtimestamp();
echo 'Using double quotes: ' . ($end-$start) . '<br />';

$start = microtimestamp();
$s = '';
for ($i=0; $i < 100000; $i++) {
    $s .= $i;
}
$end = microtimestamp();
echo 'Using no quotes: ' . ($end-$start) . '<br />';
?>
```

![](img/2862989e5dc7f1b1d0bc64321737f084_100_0.png)

Figure 3.3 测量两段代码的性能

**提示：** 你可以用以下代码替换 `microtimestamp()` 函数：

```php
function microtimestamp() {
    return microtime(true);
}
```

当提供参数 `true` 时，函数 `microtime()` 返回当前微时间的浮点值（这是在 PHP 5 中添加的）。然而，据说这比使用 `gettimeofday()` 慢，后者只是执行底层的 gettimeofday 系统调用。

## 使用表单字段进行日期选择

```php
<form method="post" action="">
<select name="day"><?php
    for ($i = 1; $i <= 31; $i++) {
        echo "<option value=\"$i\">$i</option>\n";
    }
?>
</select>
<select name="month"><?php
for ($i = 1; $i <= 12; $i++) {
    $monthname = date('F', mktime(12, 0, 0, $i, 1, 2012));
    echo "<option value=\"$i\">$monthname</option>";
}
?></select>
<select name="year"><?php
for ($i = 2012; $i <= 2015; $i++) {
    echo "<option value=\"$i\">$i</option>";
}
?></select>
</form>
```

如果你想提供一个 HTML 表单来选择日期，就像许多酒店和航班预订服务提供的那样，你可以使用 `date()` 的各种参数；遍历一年的所有月份；从而创建日、月、年的选择列表。前面的代码包含了此的语法；请参阅图 3.4 查看结果。

![](img/2862989e5dc7f1b1d0bc64321737f084_101_0.png)

Figure 3.4 月份名称是自动生成的。

## 创建自更新的表单字段进行日期选择

```php
<?php
if (isset($_POST['month']) &&
    is_numeric($_POST['month']) &&
    ((int)$_POST['month'] >= 1 &&
    (int)$_POST['month'] <= 12)) {
    $month = (int)$_POST['month'];
} else {
    $month = date('n');
}
if (isset($_POST['year']) &&
    is_numeric($_POST['year']) &&
    ((int)$_POST['year'] >= 2012 &&
    (int)$_POST['year'] <= 2015)) {
    $year = (int)$_POST['year'];
} else {
    $year = date('Y');
}
?>
<form method="post" action="<?php echo
htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    $maxdays = date('t', mktime(12, 0, 0, $month, 1,
$year));
    for ($i = 1; $i <= $maxdays; $i++) {
        if (isset($_POST['day']) && $_POST['day'] ==
$i) {
            $sel = ' selected';
        } elseif ($i == date('j')) {
            $sel = ' selected';
        } else {
            $sel = '';
        }
    }
    echo "<option value=\"$i\"$sel>$i</option>\n";
```
