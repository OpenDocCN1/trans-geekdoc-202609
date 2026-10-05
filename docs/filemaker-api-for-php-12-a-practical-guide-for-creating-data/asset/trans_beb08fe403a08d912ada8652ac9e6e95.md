

else
{
  echo '<img src="Images/previous_record.jpg" border=0/>';
}
?>
</html>
<td>

URL 跳转下一条记录的跳过值计算方式为当前跳过值加一，因为你想向前移动一条记录。只有当你不在最后一条记录时，按钮才需要包含链接。记录是使用 $found 变量计算的。

```php
<?php
$next = $skip+1;
if ($skip+1 < $found) {
  echo '<a href=\'.$_SERVER['PHP_SELF'].\'?skip=\.'$next.'&name=1&FirstName=\.'$firstName.'"><img src="Images/next_record.jpg" border=0/></a>';
}
else {
  echo '<img src="Images/next_record.jpg" border=0/>';
}
?>
</html
<td>
```

最后，URL 跳转到最后一条记录的值计算方式为找到的总数减 1。与跳转到下一条记录一样，只有当你不在最后一条记录时，按钮才需要包含链接。

```php
<?php
$last = $found-1;
if ($skip+1 < $found) {
  echo '<a href=\'.$_SERVER['PHP_SELF'].\'?skip=\.'$last.'&name=1&FirstName=\.'$firstName.'"><img src="Images/last_record.jpg" border=0/></a>';
}
else {
  echo '<img src="Images/last_record.jpg" border=0/>';
}
?>
<td>
</tr>
</table>
<p>
```

现在记录分页链接和按钮已经显示，你可以创建 HTML 来显示记录的字段。虽然技术上由于我们将最大值定义为 1，集合中技术上只有一条记录，但我正在使用 `foreach` 循环方法来从 $records 数组中显示记录。

```php
<?php
foreach ($records as $record) {
  echo '<table border="1">';
  echo '<tr>';
  echo '<td>First Name:</td>' . $record->getField('FirstName') . '</td>';
  echo '</tr>';
  echo '<tr>';
  echo '<td>Last Name:</td>' . $record->getField('LastName') . '</td>';
```

```php
echo '</tr>';
echo '<tr>';
echo '<td>Number:</td>';
echo '<td>' . $record->getField('Number') . '</td>';
echo '</tr>';
echo '<tr>';
echo '<td>Date:</td>';
echo '<td>' . $record->getField('Date') . '</td>';
echo '</tr>';
echo '<tr>';
echo '<td>Time Stamp:</td>';
echo '<td>' . $record->getField('TimeStamp') . '</td>';
echo '</tr>';
echo '<tr>';
echo '<td>Calculation:</td>';
echo '<td>' . $record->getField('Calculation') . '</td>';
echo '</tr>';
echo '<tr>';
echo '<td>RecordID:</td>';
echo '<td>' . $record->getField('RecordID') . '</td>';
echo '</tr>';
}
echo '</table>';
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_202_0.png)

图 7-51：Navigation.php 页面。

# 第 20 ：多用户编辑记录进程

**目标：** 在节中，你将学习如何在多用户环境中更新记录。网页是非状态的，这意味着与服务器的连接不像 FileMaker Pro 和 FileMaker Server 的客户端-服务器连接那样持久。因此，当两个或多人更新同一记录时，不存在记录锁定。这意味着你需要管理更新过程，在更新提交到服务器之前检查其他用户所更改。

**难度：** 中等

示例文件：
PHPFiles/Advanced/Lesson20/MultiUserEditRecord.php
PHPFiles/Advanced/Lesson20/MultiUserEditRecordDetail.php

页面导航：

![](img/5a2c5fda68d42e5d65f51850276e49ec_203_0.png)

FileMaker API 方法：
- newFindAllCommand()
- newFindCommand()
- addFindCriterion()
- execute()
- getRecords()
- getField()
- RecordID()
- newEditCommand()
- getField()
- setModificationID()
- setRecordByID()

代码：

```
MultiUserEditRecord.php
```

此编辑记录页面与之前的示例相同。其目的是将记录 ID 传递到详情页，以便隔离记录并显示更多字段。

始终从包含数据库连接开始。

```php
<?php
include ("../conn/dbaccess.php");
?>
```

创建一个按 First Name（ own）搜索的表单。

```html
<form action="MultiUserEditRecord.php" method="get">
First Name: <input name="FirstName" type="text" />
<br />
<input name="submit" type="submit" />
</form>
```

如果用户没有在搜索字段中输入任何内容，则显示所有记录。否则，通过 FirstName 搜索表。执行搜索。

```php
<?php
if(empty($_GET['FirstName']))
```
{
  $FirstName = "";  $request = $fm->newFindAll('Demo');
}else {
  $FirstName = $_GET['FirstName'];
  $request = $fm->newFindCommand('Demo');
  $request->addFindCriterion('First Name', $FirstName);
}
$result = $request->execute();

 检查错误。

if ($result->isError()) {
  echo '<p>Error: ' . $result->getMessage() . '</p>';
  exit;
}

 将记录存储在 $records 变量中。

$records = $result->getRecords();

 创建显示结果的表头。

echo '<table border="1">
<tr>
<th>First Name</th>
<th>Last Name</th>
<th>Number</th>
<th>Date</th>
<th>TimeStamp</th>
<th>Calculation</th>
<th>Record ID</th>
<th>Edit Record</th>
</tr>';

 使用 `foreach` 循环方法显示字段。创建指向详情页的链接并传递记录 ID。

foreach ($records as $record) {
  echo '<tr>';
  echo '<td>' . $record->getField('FirstName') . '</td>';
  echo '<td>' . $record->getField('LastName') . '</td>';
  echo '<td>' . $record->getField('Number') . '</td>';
  echo '<td>' . $record->getField('Date') . '</td>';
  echo '<td>' . $record->getField('TimeStamp') . '</td>';
  echo '<td>' . $record->getField('Calculation') . '</td>';
  echo '<td><a href="MultiUserEditRecordDetail.php?id=' . $record->getRecordID() . '">edit</a></td>';
  echo '</tr>';
}
echo '</table>';
```

# 编辑记录 -> 详情

| First Name | Last Name | Number | Date | Time Stamp | Calculation | Record ID | Edit Record |
|---|---|---|---|---|---|---|---|
| Todd | Dulli | 47 | 09/07/2010 | 15:46 | | 48 | |
| Tin | Kramer | 13 | 01/01/2010 | 15:56 | | 54 | |
| Fred | Hutch | 14 | 09/09/2010 | | 59 | |
| Mike | Adams | 37 | 25/25/2010 | | | 81 | |
| Heath | Beil | 21 | 01/01/2010 | 23:26 | | 82 | |
| Kevin | Conrad | 29 | 25/25/2010 | | | 83 | |
| Eme | Emery | 39 | 25/25/2010 | | | 84 | |
| John | Garland | 27 | 25/25/2010 | 21:06 | | 85 | |
| Luke | Greg | 35 | 25/25/2010 | 21:05 | | 86 | |
| Mate | Latos | 38 | 25/25/2010 | 22:07 | | 87 | |

