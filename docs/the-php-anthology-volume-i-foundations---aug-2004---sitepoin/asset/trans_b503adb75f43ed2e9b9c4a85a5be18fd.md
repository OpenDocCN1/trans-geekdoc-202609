

文件：4.php

```php
<?php
// Include MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Instantiate MySQL connection
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

// Select articles
$sql = "SELECT
            *,
            DATE_FORMAT(published, '%M %e, %Y') as published
            FROM articles
            WHERE published > UTC_TIMESTAMP() - INTERVAL 7 DAY
            ORDER BY published DESC";

// Perform the query
$result = $db->query($sql);

while ($row = $result->fetch()) {
    echo $row['title'] . ': ' .
        $row['published'] . '<br />';
}
?>

```

请注意，我们使用了 MySQL 的 DATE_FORMAT 函数[3] 来格式化页面上显示的日期，而在之前的示例中，格式化是由 PHP 脚本处理的。我们还使用了 MySQL 的 UTC_TIMESTAMP 函数和一个 INTERVAL 来选择我们要查找的日期。

这个示例展示了我偏好将日期/时间值存储为 Unix 时间戳的几个原因：

- 我希望 SQL 语句尽可能简单。
- 在 PHP 中调试错误通常比在 SQL 语句中更容易。
- MySQL 日期/时间功能的许多细节都是数据库特定的，如果需要，它们移植到其他数据库时效果不佳。
- 您的数据库应该负责跟踪您的数据，而不是将其格式化为显示用的格式。²

当您使用 MySQL 时间戳时，通常需要依赖 MySQL 的内置函数来帮您完成一些工作。让我再展示一个饱受“复杂查询综合征”之苦的示例。

假设您想显示一个统计数据，告诉您网站上上一篇文章是多少天前发布的。为此，您需要计算今天日期与上一篇文章发布日期之间的“天数距离”（而非差值）。MySQL 可以这样做：

```
SELECT TO_DAYS(NOW()) - TO_DAYS(published)
FROM articles
ORDER BY published DESC
LIMIT 1
```

这看起来还可以，但 SQL 语句正在变得越来越复杂。如果我改为将数据存储为 Unix 时间戳，查询将如下所示：

```
SELECT published
FROM articles
ORDER BY published DESC
LIMIT 1
```

然后，要在 PHP 中显示结果，我将使用以下代码：

```
$daysAgo = floor((time() - $row['published']) / 86400);
```

86400 是一天中的秒数；floor 函数用于将小数向下舍入为整数值。

当然，您可能不同意在 PHP 中处理事情更简单，这种情况下，我完全鼓励您探索 MySQL 的日期处理功能。最终，Unix 时间戳和 MySQL 时间戳都可以达到相同的目的；您偏爱哪种是个人喜好的问题。

²顺便说一句，MySQL 的开发者倾向于同意我的这一观点。

[3] http://www.mysql.com/doc/en/Date_and_time_functions.html

## 如何解决常见的日期问题？

请考虑我们每次面对日历时大脑所进行的计算类型：

> “我希望它在3月3日前完成……那只有五天的时间了！”

很明显，处理日期不仅仅是按重要性组织数据或显示单个数据点。在本方案中，我们将探讨处理日期和时间时可能遇到的一些常见问题。具体来说，我们将看到如何处理

- [ ] 一周中的天数
- [ ] 一年中的周数
- [ ] 一年中的天数
- [ ] 一个月的天数
- [ ] 闰年

在此过程中，我们将构建一个可以在您自己的应用程序中轻松重用的类。

以下代码为该类奠定了基础：

```php
<?php
/**
 * DateMath class for solving common date problems
 * @package SPLIB
 */
class DateMath {
/**
 * Unix timestamp
 * @access private
 * @var int
 */
var $timeStamp;
/**
 * DateMath constructor
 * If parameters not provided, DateMath uses current time
 * <code>
 * $dateMath = new DateMath(2003,8,22); // Uses 22nd August 2003
 * $dateMath = new DateMath(); // Uses current date and time
 * </code>
 * @param int year ( e.g. 2003 )
 * @param int month ( e.g. 8 for August )
 * @param int day of month ( e.g. 22 )
 * @param int hours ( e.g. 15 )
 * @param int minutes ( e.g. 5 )
 * @param int seconds ( e.g. 7 )
*/
function DateMath($y = NULL, $m = NULL, $d = NULL, $h = NULL,
$i = NULL, $s = NULL)
{
$time = time();

$y = is_numeric($y) ? $y : date('Y', $time);
$m = is_numeric($m) ? $m : date('m', $time);
$d = is_numeric($d) ? $d : date('d', $time);
$h = is_numeric($h) ? $h : date('H', $time);
$i = is_numeric($i) ? $i : date('i', $time);
$s = is_numeric($s) ? $s : date('s', $time);
$this->timeStamp = mktime($h, $i, $s, $m, $d, $y);
}

/**
* For setting a Unix timestamp
* @param int a Unix timestamp
* @return void
* @access public
*/
function setTimeStamp($timeStamp)
{
$this->timeStamp = $timeStamp;
}
```

构造函数会检查您是否为日期传递了任何值，参数按年、月、日、时、分、最后是秒的顺序出现。对于您未提供数值的任何参数，都将使用当前日期或时间。然后，构造函数将其转换为时间戳，以便后续计算更加容易。

如果我要从时间戳开始，可以使用 setTimeStamp 方法提供自己的值。

## 一周中的天数

如果给定日期“2003年3月22日”，我们如何知道那是星期几？最简单的解决方案是将其转换为时间戳，然后使用 PHP 的 date 函数来告诉我们22日是星期几。要将其添加到类中，我们只需插入另一个方法：

```php
/**
 * Returns the day of the week
 * @param boolean if true returned value will be numeric day of week
 * @return mixed e.g. Saturday or 6
 * @access public
 */
function dayOfWeek($Numeric = false)
{
    if ($Numeric) {
        return date('w', $this->timeStamp);
    } else {
        return date('l', $this->timeStamp);
    }
}
```

现在，使用 dayOfWeek 方法，我们将找出2003年3月22日是星期几：

```php
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Instantiate DateMath class 22nd March 2003
$dateMath = new DateMath(2003, 03, 22);

echo '22nd March 2003 is a ' . $dateMath->dayOfWeek();
?>
```

请注意，如果向 dayOfWeek 方法传递 TRUE，它将返回一周中天数的数字表示，从0表示星期日开始：

echo '22nd March 2003 is day ' . $dateMath->dayOfWeek(TRUE) .
 ' of the week.';

## 一年中的周数

要确定一年中的周数，我们向 DateMath 类添加另一个方法：

文件：DateTime/DateMath.php（在 SPLIB 中）（节选）

```php
/**
 * Returns the ISO 8601 week of the year
 * @return int numeric week of year e.g. 12
 * @access public
 */
function weekOfYear()
{
   return date('W', $this->timeStamp);
}
```

将其付诸实践：

文件：6.php

```php
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Instantiate DateMath class 22nd March 2003
$dateMath = new DateMath(2003, 3, 22, 0, 0, 0);

echo '22nd March 2003 is in week ' . $dateMath->weekOfYear() .
     ' of the year';
?>
```

请注意，weekOfYear 方法依赖于 PHP 的 date 函数，该函数对周使用 ISO 8601 标记[4]。根据该标准，一年的第一周是包含当年的第一个星期四的周（从星期一开始）。因此，例如，如果12月的最后两天分别是星期一和星期二，根据此标记，它们实际上属于下一年。

## 一个月的天数

我的记忆力很差，我从来都记不住某个月应该有多少天。幸运的是，使用 PHP 找出这一点并不太难，我们可以简单地向 DateMath 类添加一个 daysInMonth 方法：

[4] http://www.cl.cam.ac.uk/~mgk25/iso-time.html

