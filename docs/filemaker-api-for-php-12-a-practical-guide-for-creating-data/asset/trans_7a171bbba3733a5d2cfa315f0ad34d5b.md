
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');

从 URL 中存储变量。

```php
$month=$GET['month'];
$day=$GET['day'];
$year=$GET['year'];
$id=$GET['id'];
```

开始创建表格以显示数据。显然，这个解决方案并不华复杂。我会让你自己进行美化以匹配你的网站。使用你喜欢的代码更重要。

```php
echo '<table width="100%\'>";
echo '<tr>';
echo '<td></td>';"
```

如果值是通过 URL 传递的，我们可以从数据库中获取特定记录并显示结果。

```php
if(isset($_GET['id']))
{
  $record=$fm->getByID('Demo', $id);
  echo 'Date From: ' . $record->getField('DateFrom') . '<br>';
  echo 'Date To: ' . $record->getField('DateTo') . '<br>';
  echo 'Time: ' . date('g:i A',strtotime($record->getField('Time'))) . '<br>';
  echo 'Event: ' . $record->getField('Event') . '<br>';
}
```

如果日期值是通过 URL 传递的，我们可以找到该日期的记录。不要忘记处理错误，以防用户点击了没有数据的日期。

```php
if(isset($_GET['day']))
{
  $request=$ $fm->newCommand('Demo');
  $request->addFilterCriterion('DateRange', $month . "/" . $year);
  $request->addSortRule('DateFrom', 1);
  $request->addSortRule('Time', 2);
  $result=$request->execute();
  if(FileMaker::isError($result))
{
    echo 'No Records';
  }
  else
{
    $records=$result->getRecords();
    foreach($records as $record) {
      echo 'Date From: ' . $record->getField('DateFrom') . '<br>';
      echo 'Date To: ' . $record->getField('DateTo') . '<br>';
      echo 'Time: ' . date('g:i A',strtotime($record->getField('Time'))) . '<br>';
      echo 'Event: ' . $record->getField('Event') . '<br>';
      echo '<hr width="100%">';
    }
  }
}
```

然后遍历查找集中的每条记录以显示结果。

```php
echo '</table>';
echo '</tr>';
echo '</table>';
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_282_0.png)

图 7-99：显示当日的详细信息。

# 第 35 节：比较日期

目标：在本节中，你将学习如何使用 FileMaker 与 PHP 比较日期。早晚你都会需要显示通过日期过滤或某种类型比较的记录，以做出分支决策。例如，仅显示日期大于今天的相关记录计划。你们中的大多数人可能想：这很简单，我只需在数据库布局上对门户进行过滤，并使用 `setRelatedSetsFilters` 来过滤显示，这将会轻而易举。问题在于，在编写本节时，`setRelatedSetsFilters` 函数无法工作。因此，你将创建一个带有额外字段的特定发生（TOG），然后编写权限集（Privilege Set）来过滤记录，或者在你的 PHP 代码中执行日期比较。这两者各有优劣。额外的 TOG 意味着你的 PHP 站点增加了不必要的负担。权限集与使用门户过滤器对话框无区别。所有记录都会返回给你，而哪些记录是由 FileMaker 引擎控制的。因此，服务器上的负载与你发送所有记录一样。问题是，权限集会在每个布局上的任何时候过滤所有记录，而不仅仅是你的特殊 PHP 页面上的一个门户。因此，减少负担的唯一合理选择是在你的 PHP 页面上编写日期比较，以保持数据库尽可能整洁。本节将向你展示在 FileMaker 与 PHP 中比较日期的几种不同方法（以及陷阱）。

难度：简单

示例文件：
- PHPFiles/Advanced/Lesson35/CompareDates.php
- PHPFiles/Advanced/Lesson35/CompareDates.fp12

| 此处使用独立的数据库文件来演示课程。请将 CompareDates.fp12 数据库文件上传到你的服务器 |
| :--- |

页面导航：N/A

FileMaker API 方法：
- newFindAllCommand()
- execute()
- getFirstRecord()
- getField()

代码：
从连接数据库开始。

```html
<html>
<body>
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'CompareDates');
$fm->setProperty('hostspec', 'http://127.0.0.1');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
?>?>
```

我没有在这个示例中对数据进行任何特殊处理以显示数据。目标是比较日期并显示结果，以便你可以看到哪些方法有效，哪些方法存在问题。因此，我只显示表格中的第一条记录并将结果返回给 $record 变量。

```php
$request = $fm->findAllCommand('Demo');
$result = $request->execute();
$record = $result->getFirstRecord();
```

第一个示例比较了 FileMaker 内部的两个日期字段。这种直接从数据库比较日期的方法按预期工作，并将做出正确的判断并显示正确的结果。

```php
if($record->getField('Date1') < $record->getField('Date2')) {
    echo 'Date1: ' . $record->getField('Date1') . ' < Date2: ' . $record->getField('Date2');
} elseif ($record->getField('Date1') > $record->getField('Date2')) {
    echo 'Date1: ' . $record->getField('Date1') . ' > Date2: ' . $record->getField('Date2');
} else {
    echo 'Date1: ' . $record->getField('Date1') . ' = Date2: ' . $record->getField('Date2');
}
```

第二个示例比较了 FileMaker 内部的两个日期字段。这种直接从数据库比较日期的方法按预期工作，并将做出正确的判断并显示正确的结果。

（注：原文中后续部分存在重复和乱码，已根据逻辑进行处理）
