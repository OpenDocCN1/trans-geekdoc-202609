
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

```
<tr>
  <th>Text</th>
</tr>
<tr>
  <td><input type="text" name="Text" value="<?php echo $Text; ?>" /></td>
</tr>
</table>
<p>
  <input name="save" type="submit" value="Save" />
</p>
<?php echo $message; ?>
```

最后，我想提供一个返回父级页面的链接。在这种情况下，我之前在 URL 中发送了 `parent` id，这里继续发送。这允许我构建返回父级记录的链接。如果用户点击此链接，页面将刷新并显示用户对相关记录做的任何更改。

```php
<?php echo '<a href="SearchResultsPortal.php?id=' . $_REQUEST['parent'] . '">点击此处返回父级记录。</a>'; ?>
</form>
</body>
</html>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_137_0.png)

图 7-25：EditRecordDetailPortal.php 页面。

## Lesson 11: Delete Record

我们将学习如何使用表单删除数据库中的相关记录。通用流程是首先搜索记录列表。然后点击相关记录的链接进入详情页。最后，点击相关记录将其隔离为单条记录以便从数据库中删除。这与在 FileMaker Pro 门户中删除记录相同，但更简单。

**难度：**

**示例文件：**
- `PHPFiles/Core/Lesson11/SearchResultsPortal.php`
- `PHPFiles/Core/Lesson11/SearchResultsDetailPortal.php`
- `PHPFiles/Core/Lesson11/DeleteRecordPortal.php`

**页面导航：**

![](img/5a2c5fda68d42e5d65f51850276e49ec_138_0.png)

**FileMaker API 方法：**
- `findAllCommand()`
- `findCommand()`
- `findCriterion()`
- `execute()`
- `getMessage()`
- `getRecords()`
- `getField()`
- `getRecordID()`
- `getRecordByID()`
- `newRelatedRecord()`
- `Field()`
- `commit()`
- `getRelatedSet()`
- `newEditCommand()`

**代码：**

### SearchResultsPortal.php

始终从包含数据库连接开始。

```php
include ("Conn/dbaccess.php");
?>
```

创建一个表单来搜索记录。情况下，表单通过 `GET` 方法指向同一页面。

```html
<form action="SearchResultsPortal.php" method="GET">
  FirstName: <input name="FirstName" type="text" />
  <br />
  <input name="submit" type="submit" />
</form>
```

创建 PHP 代码来搜索数据库并显示结果。这与之前的示例相同。

```php
<?php
if(empty($_GET['FirstName'])) {
  $FirstName = "";
  $request = $fm->newFindCommand('Related Data');
} else {
  $FirstName = $_GET['FirstName'];
  $request = $fm->newFindCommand('Related Data');
  $request->addCriterion('FirstName', $FirstName);
}
```

执行搜索请求。

```php
$result = $request->execute();
```

捕获错误。

```php
if (FileMaker::isError($result)) {
  echo "<p>Error: " . $result->getMessage() . "</p>";
  exit;
}
```

显示结果表格的表头。

```php
<table border="1">
  <tr>
    <th>First Name</th>
    <th>Last Name</th>
    <th>Number Number</th>
    <th>Date</th>
    <th>Time Stamp</th>
    <th>Calculation</th>
    <th>Record ID</th>
    <th>View Detail</th>
  </tr>
</table>
```

使用 `foreach` 循环显示字段内容，以遍历数组中的每条记录。

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
  echo '<td><a href="SearchResultsDetailPortal.php?id=" . $record->getRecordID() . '">View</a></td>';
  echo '</tr>';
}
```

```
echo '</table>';
?
```

# 搜索结果 -> 详情

![](img/5a2c5fda68d42e5d65f51850276e49ec_140_0.png)

图 7-26：SearchResultsPortal.php 页面。

### SearchResultsDetailPortal.php
始终从包含数据库连接开始。

```php
<?php
include("../../dbaccess.php");
?>
```

首先根据 URL 中的 id 获取记录。将记录存储在 `$record` 变量中。

```php
$record = $fm->getById("Demo php", $_GET['id']);
```

检查 id 值是否有效。否则，停止脚本并通知用户。

```php
if (empty($_GET['id'])) {
  die("The RecordID is missing.");
}
```

下一段代码检查是否从下方的表单设置了 `newRelatedData` 按钮。如果你可以调用 `$record` 变量使用 `related_data` 表创建一个新记录，并将结果存储在 `$new_record` 变量中。接下来，你可以使用表单从 URL 传递的值更新 Text 字段。作为用户，你需要提交该请求。最后，你可以告诉 `$fm` 对象通过 URL 传递的值获取记录，并使用 `$record` 变量显示结果。

```php
if(isset($_POST['newRelatedData'])) {
  $new_record = $record->newRelatedRecord('related_data');
  $new_record->addField('related_data:Text', $_POST['Text']);
  $result = $new_record->commit();
  $record = $fm->getById("Demo php", $_GET['id']);
}
```

接下来，将所有相关记录存储在 `$related_records` 变量中，并创建 `$style_data` 变量来存储表单的 HTML。这将允许 PHP 代码在用户点击提交 按钮后用新表单显示结果。对于新用户，你可以直接向数据库提交额外记录，而无需返回列表页面。表单将指向同一页面，并将代码中的 id 值作为 RecordID 传递。

```php
$related_records = $record->getRelatedSet('related_data');
$table_data .= '<form action="SearchResultsDetailPart.php?id=' .
$getRecordId() . ' method="post">';
$table_data .= '<table border="1">\n<tr>';
$table_data .= '<th>Text</th>';
$table_data .= '<td>&nbsp;</td>';
$table_data .= '</tr></table>';
```

使用 `foreach` 循环方法为相关记录创建 HTML 表格。这与上一个示例的区别是将不换行空格替换为指向 DeleteRecordDetailPart.php 页面的删除链接。该链接将出现在每个相关记录上。

```php
foreach($related_records as $record) {
$table_data .= '<tr>';
$table_data .= '<td>' . $record->getField('related_data:Text') . '</td>';
$table_data .= '<a href="DeleteRecordDetailPart.php?id=' . $related_record-
getRecordId() . '&page=' . $record->getRecordId() . ' ">delete</a>';
$table_data .= '</tr>';
}
```

最后，创建输入字段、提交按钮并关闭表单的 HTML。Text 字段是空的，以便用户输入新值。表单的关键部分如上面的按钮所示。名称为 `newRelatoData`。如果点击了此数据，表单将在页面上正确显示相关记录。

```php
$table_data .= '<tr>';
$table_data .= '<td><input type="text" name="Text" value=""></td>';
$table_data .= '<td><input type="submit" name="newRelatedData" value="Submit"></td>';
$table_data .= '</tr>';
$table_data .= '</table>';
$table_data .= '</form>';?>
```

最后一步是创建 HTML 来显示父记录数据，并在最末尾带有带有提交按钮的表单来显示相关记录。不要忘记为用户提供返回列表页面的链接，以免他们使用后退按钮。

```html
<table border="1">
<tr>
<<td><?php echo $record->getField("FirstName"); ?></td>>
</tr>
<tr>
<<td><?php echo $record->getField("LastName"); ?></td>>
</tr>
<tr>
<<td><?php echo $record->getField("Number"); ?></td>>
</tr>
<tr>
<<td><?php echo $record->getField("Date"); ?></td>>
</tr>
<tr>
<<td><?php echo $record->getField("Timestamp"); ?></td>>
</tr>
<tr>
<<td><?php echo $record->getField("Calculation"); ?></td>>
</tr>
</table>
```

```php
<?php echo $table_data; ?>
<?php
echo '<a href="SearchResultsPortal.php">Click here to return to the list
view.</a>';
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_142_0.png)

```html
 <a href="http://127.0.0.1/PHP/Core/Lesson1/SearchResultsDetailPortal.php?id=12">
```

图 7-27：SearchResultsDetailPortal.php 页面。

# EditRecordDetail.php

这个三部分过程的最后一步是隔离相关记录以便对其进行删除。始终从连接数据库开始。

```php
<?php
include ('../Conn/dbaccess.php');
```

通过编写 Post 请求开始 PHP 代码，以确定执行什么操作。用户点击删除按钮后，表单将不会显示。否则，它将显示要从 Text 字段中删除的数据。与上一个示例一样，表单传递了相关记录和父 Record ID 的隐藏值，以便可以正确删除，用户可以点击链接返回原始父记录。

```php
if (isset($_POST['delete'])) {
$display = ' Are you sure you want to delete record id: '.$record->getField('RecordID').?';
$display .= '<form action="DeleteRecordDetailPortal.php" method="post">';
$display .= '<input type="hidden" name="id" value="'.$_REQUEST['id']." />";
$display .= '<input type="hidden" name="parent" value="'.$_REQUEST['parent']." />";
}
$display = '<p>';
$display .= '<table>';
$display .= '<tr>';
$display .= '<td>'. . $record->getField('Text') . '</</td>>';
$display .= '</tr>';
$display .= '</table>';
$display .= '<p>';
$display .= '<input type="submit" name="delete" value="Delete" />';
$display .= '<input type="submit" name="delete" value="Cancel" />';
$display .= '</form>';
}
else
```php
{
if ($_POST['delete'] == 'Delete') {
  $record->delete();
  $display = '<p>The record was deleted successfully.</p>';
} else {
  $display = '<p>The record was not deleted.</p>';
}
}
```如果用户点击删除按钮，你可以使用标头中 POST 方法传递的值处理删除记录的请求。否则，如果他们点击取消按钮，你可以停止脚本。

最后，由 `$display` 创建的表单和消息可以作为 HTML 显示，并带有返回父记录的链接。

```html
<html>
<head>
<title>Delete Record</title>
</head>
<body>
<?php echo $display; ?>
<?php echo '<a href="SearchResultsPortal.php?id=' . $_REQUEST['parent'] . '">Click here to return to the list view</a>'; ?>
</body>
</html>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_143_0.png)

图 7-8：DeleteRecordDetail.php 页面。

使用 `foreach` 循环方法为表格中的所有记录创建 HTML。要显示来自容器字段的图像，你将向 `ContainerBridge.php` 文件传递两个信息。图像的 `src` 属性将是文件名 `ContainerBridge.php`，随后是 `path=` 的键值对，以及容器字段内容的编码格式的值。在书的早些章节，我们描述了 `ContainerBridge.php` 文件是如何工作以完成所有繁重任务的。要显示字段的内容，你只需要将此信息传递给页眉。这很好地说明了为什么将代码拆分为逻辑部分非常重要，这样它们就可以被多个网页重用。
