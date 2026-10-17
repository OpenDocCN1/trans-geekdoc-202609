
```php
foreach ($records as $record) {
  echo '<tr>';
  echo '<td>' . $record->getField('FirstName') . '</td>';
  echo '<td>' . $record->getField('LastName') . '</td>';
  echo '<td>' . $record->getField('Number') . '</td>';
  echo '<td>' . $record->getField('Date') . '</td>';
  echo '<td>' . $record->getField('TimeStamp') . '</td>';
  echo '<td>' . $record->getField('Calculation') . '</td>';
  echo '<td>' . $record->getField('RecordID') . '</td>';
  echo '<td><a href="DeleteDetail.php?id=' . $record->getID() . '">delete</a></td>';
  echo '</tr>';
}
```

关闭表格和 PHP 代码。

```php
echo '</</table>';
?>
```

## 删除 - 详情

![](img/5a2c5fda68d4f5850276e49ec_114_0.png)

| First Name | Last Name | Number | Date | Time Stamp | Calculation | Record ID | Delete |
|---|---|---|---|---|---|---|---|
| Tim | | | | | | | |
| Fred | | | | | | | |
| Mike | | | | | | | |
| Heath | | | | | | | |
| Mike | | | | | | | |
| Bell | | | | | | | |
| Kevin | | | | | | | |
| Emes | | | | | | | |
| Frost | | | | | | | |
| Garland | | | | | | | |
| John | | | | | | | |
| Luke | | | | | | | |

```php
$display = '<tdEmail: . $record->getField('Email') . '</td>';
$display = '</tr>';
$display = '</</table>>';
$display = '<p>';
$display = '<input type="submit" name="delete" value="Delete" />';
$display = '<input type="submit" name="delete" value="Cancel" />';
$display = '</p>';
$display = '</form>';
}
else
```

如果用户点击“删除”按钮，你可以使用 `delete()` 方法从数据库中删除记录。然后将 `$display` html 设置为消息，告知用户记录已成功删除。

```php
if ($_POST['delete'] == 'Delete')
{
$record->delete();
$display = '<p>The record was deleted successfully.</p>';
}
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_115_0.png)

另一个选择是点击“取消”按钮。然后将 `$display` html 设置为消息，告知用户记录未被删除。

```php
else
$display = '<p>Cancel: The record was not deleted.</p>';
```

我还喜欢提供一个返回列表的链接，这样用户无需点击浏览器的后退按钮。这还会强制列表页面刷新向服务器的请求，以确保删除的记录不再显示在浏览器上。

```php
$display = '<a href="DeleteRecord.php">Click here to return to the list
view</a></p>';
?>
```

最后，`$display` 变量用于存储所有的 html 代码，页面的主体只需简单地输出 `$display` 变量的内容。

```html
<<html>
<head>
<title>Delete Record -> Detail</title>
</head>
<body>
<?php
echo $display;
?>
</body>
</html>
```

你确定要删除记录记录 id: 52 吗？

| 字段 | 值 |
|---|---|
| 名字 | Todd |
| 姓 | Duell |
| 编号 | 47 |
| 日期 | 09/07/2010 |
| 邮箱 | sduell@formulationspro.com |
| 删除 | 取消 |

前往 "http://127.0.0.1/PHPFiles/Core/Lesson/DeleteRecordDetail.php?id=52"

图 7-14：DeleteRecordDetail.php 文件。

![](img/5a2c5fda68d42e5d65f51850276e49ec_116_0.png)

取消：记录未被删除。

点击此处返回列表视图。

图 7-15：取消记录删除过程。

# 第 7 节：编辑->详情

**目标：** 在本节中，你将学习如何使用表单编辑数据库中的记录。这与在 FileMaker Pro 中编辑记录相同。编辑记录的过程是将 RecordID 从列表页面传递到详情页。这允许你隔离出单条记录。当用户完成后，他们可以点击链接返回列表页面，那里记录列表将刷新并显示新信息。

**难度：** 中等

**示例文件：**

PHPFiles/Core/Lesson7/EditRecord.php

PHPFiles/Core/Lesson7/EditRecordDetail.php

页面导航：

![](img/5a2c5fda68d42e5d65f51850276e49ec_117_0.png)

**FileMaker API 方法：**

- newFindAllCommand()
- newFindCommand()
- addFindCriterion()
- execute()
- setField()
- getMessage()
- Records()
- getField()
- RecordId()
- newEditCommand()
- getRecordById()

**代码：**

EditRecord.php

始终从包含数据库的连接开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

创建一个表单来搜索记录。在这种情况下，表单将使用 Get 方法提交回同一页面。

```html
<form action="EditRecord.php" method="GET">
名字: <input name="FirstName" type="text" />
<br />
<input name="submit" type="submit" />
</form>
```

创建 PHP 代码来搜索数据库并显示结果。这与之前的示例相同。

```php
<?php
if(empty($_GET['FirstName']))
{
$FirstName = "";
$request = $fm->newFindAllCommand('Demo php');
}
```

```php
else
{
$FirstName = $_GET['FirstName'];
$request = $fm->newFindCommand('Demo php');
$request->addCriterion('FirstName', $FirstName);
}
```

执行搜索请求。

```php
$result = $request->execute();
```

错误捕获。

显示表格表头。

```php
echo '<table border="1">
<tr>
<th>名字</th>
<th>姓</th>
<th>编号 数字</th>
<th>日期</th>
<th>时间戳</th>
<th>计算</th>
<th>记录 ID</th>
<th>删除记录</th>
</tr>
```

使用 `foreach` 循环显示字段内容，以显示数组中的每条记录。

```php
foreach ($records as $record)
{
echo '<tr>';
echo '<td' . $record->getField('FirstName') . '</td>';
echo '<td' . $record->getField('LastName') . '</td>';
echo '<td' . $record->getField('Number') . '</td>';
echo '<td' . $record->getField('Date') . '</td>';
echo '<td' . $record->getField('TimeStamp') . '</td>';
echo '<td' . $record->getField('Calculation') . '</td>';
echo '<td' . $record->getField('RecordID') . '</td>';
echo '</tr>';
```

```php
echo '</tr>';
```

创建编辑记录的链接。将 RecordID 传递给 EditRecordDetail.php 页面以便隔离单条记录。

```php
echo '<td><a href="EditRecordDetail.php?id=" . $record->getRecordID() . '">edit</a></td>';
echo '</tr>';
}
```

关闭表格和 PHP 代码。

```php
echo '</table>';
?>
```

编辑->详情

![](img/5a2c5fda68d42e5d65f51850276e49ec_115_0.png) 编辑->详情

```html

<table>

  <tr>

    <th>时间戳</th>

  </tr>

  <tr>

    <td><?php echo $TimeStamp; ?></td>

  </tr>

</table>

<p>

  <input name="save" type="submit" value="保存" />

</p>

<?php echo $message . "<a href=EditRecord.php>点击此处返回列表页</a>"; ?>

</p>

</body>

</html>

```

![](img/5a2c5fda68d42e5d65f51850276e49ec_121_0.png)

点击此处返回列表页

前往 "http://127.0.0.1/PHPFiles/Core/Lesson7/EditRecordDetail.php?id=5"

### 图 7-17：EditRecordDetail.php 文件。

![](img/5a2c5fda68d42e5d65f51850276e49ec_121_1.png)

您的更改已保存

点击此处返回列表页

### 图 7-18：保存更改并返回列表页。

## 课程 8：搜索门户->详情门户

**目标：** 在本节中，你将学习如何在详情页上显示数据库中的相关记录。显示相关记录的过程是从列表页将 RecordID 到详情页。这允许你隔离单个记录以显示相关的记录。

**难度：** 中等

**示例文件：**
- PHPFiles/Core/Lessons8/SearchResultsPortal.php
- PHPFiles/Core/Lesson8/SearchResultsDetailPortal.php

**页面导航：**

![](img/5a2c5fda68d42e5d65f51850276e49ec_122_0.png)

**FileMaker API 方法：**
- FindAllCommand()
- newCommand()
- addCriterion()
- execute()
- getMessage()
- Records()
- getField()
- RecordID()
- getRecordByID()
- getRelatedSet()

**代码：**

### SearchResultsPortal.php

始终从包含数据库连接开始。

```php

<?php

include("./../conn/dbaccess.php");

?>

```

创建一个表单来搜索记录。在这种情况下，表单通过方法指向同一个页面。

```html

<form action="SearchResultsPortal.php" method="GET">

名字: <input name="FirstName" type="text" />

<br />

<input name="submit" type="submit" />

</form>

```

创建 PHP 代码来搜索数据库并显示结果。这与之前的示例相同。

```php

<?php

if(empty($_GET['FirstName']))

{

$FirstName = "";

$request = $fm->findAllCommand('Demo php');

}

else

{

```

```php

$FirstName = $_GET['FirstName'];

$request = $fm->newFindCommand('Demo php');

$request->findCriterion('FirstName', $FirstName);

}

```

执行搜索请求。

```php

$result = $request->execute();

```

捕获错误。

```php

if (FileMaker::isError($result)) {

  echo "<p>错误: " . $result->getMessage() . "</p>";

  exit;

}

```

显示结果表的表头。

```php

echo '<table border="1">

<tr>

<th>FirstName</th>

<th>LastName</th>

<th>Number Number</th>

<th>Date</th>

<th>Timestamp</th>

<th>Calculation</th>

<th>RecordID</th>

<th>View Detail</th>

</tr>';

```

使用 `foreach` 循环显示字段内容，以显示数组中的每条记录。

```php

foreach ($records as $record) {

  echo '<tr>';

  echo '<td>' . $record->getField('FirstName') . '</td>';

  echo '<td>' . $record->getField('LastName') . '</td>';

  echo '<td>' . $record->getField('Number') . '</td>';

  echo '<td>' . $record->getField('Date') . '</td>';

  echo '<td>' . $record->getField('Timestamp') . '</td>';

  echo '<td>' . $record->getField('Calculation') . '</td>';

  echo '<td>' . $record->getField('RecordID') . '</td>';

```

创建查看详情页的链接。将 RecordID 传递到 SearchResultsDetailPortal.php 页面，以便隔离单个记录。

```php

echo '<td><a href="SearchResultsDetailPortal.php?id=' . $record->getRecordID() . '">删除</a></td>';

} '</tr>';

```

关闭表格和 PHP 代码。

```php

echo '</</table>>';

?>
```
