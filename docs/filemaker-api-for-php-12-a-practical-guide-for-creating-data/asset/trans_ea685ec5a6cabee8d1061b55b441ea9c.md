` 标签内主要是代码和占位符，我对这些部分进行了结构化处理。

如果您有完整的英文正文，请重新提供，我将为您进行精确翻译。

以下是基于您提供片段的结构性翻译：

[content]

```php
$number=$_POST['Number'];
$int_options = array(
  "options"=>array(
    "min_range"=>0,
    "max_range"=>100
  )
);
```

```php
if(filter_var($number, FILTER_VALIDATE_INT, $int_options))
  die("Number is not between 0-100");
} else
{
  $request->addField('Number', $_POST['Number']);
}
```

验证日期要稍微复杂一些，因为你必须确保格式正确且日期本身有效。在 FileMaker 的情况下，格式为 MM/DD/YYYY。问题在于用户可能会以 DD/MM/YYYY 的格式输入日期，甚至是错误的日期，例如 02/31/2010。因此，验证日期的简单方法是使用 PHP 的 `explode` 函数来提取输入日期的格式，然后将其重新组合为所需的格式。首先，从 `$_POST` 超局变量中创建变量。

```php
$Date=$_POST['Date'];
```

接下来，使用 PHP 的 `explode` 方法以斜杠 `/` 为分隔符，将三组数字（MM, DD, YYYY ）分离到一个数组中，其中 $mm 被赋值给第一个数组，$dd 被赋值给第二个数组，$yyyy 被赋值给第三个数组。

```php
$array=explode("/", $Date);
$mm=$array[0];
$dd=$array[1];
$yyyy=$array[2];
```

现在，你可以使用 PHP 的 `checkdate` 方法重新组合日期了。如果该日期不是有效日期，你可以停止脚本。如果日期有效，就可以将其插入数据库。你可能在想斜杠 "/` 的验证在哪里。当我们使用 `explode` 函数时，我们指定了分隔符为 `/`。如果用户输入 12.12.2010 或 12-12-2010，`explode` 函数将把整个日期放入第一个数组，因为找不到所需的分隔符。因此，日期格式将被重新组合为 12.12.2010??，这显然是无效的。

```php
if(!checkdate($mm, $dd, $yyyy))
{
  die("Invalid date " . $Date);
} else
{
  $request->addField('Date', $_POST['Date']);
}
```

验证电子邮件地址也面临着巨大的挑战。在没有复杂的 Web 方法的情况下，你所做的只能验证该地址是否代表有效的格式。PHP 中带有 `FILTER_VALIDATE_EMAIL` 选项的内置方法让你轻松实现这一点。如果电子邮件地址有效，就可以插入条目。否则，你可以停止脚本并向用户显示消息。

```php
if(filter_var($_POST['Email'],FILTER_VALIDATE_EMAIL))
{
  $request->addField('Email', $_POST['Email']);
} else
```

```php
{
  die("Your email address is not valid.");
}
```

一旦表单上的所有内容都通过了验证，就可以执行请求。捕获错误。最后，显示插入表单并附带适当的消息，告知用户记录已成功插入。

```php
$result=$request->execute();

if (FileMaker::isError($result)) {
  $message = "<p>Error: " . $result->getMessage() . "</p>";
  exit;
} else {
  $message = '<p>Record was created successfully.</p>';
}
?>
<?php
echo $message;InsertValidation; 
?>
<form action="InsertRecordValidation.php" method="post" name="Insert"> 
  <table border="1">
    <tr>
      <td>First Name（名字）</td>
      <td><input name="FirstName" type="text" id="FirstName" /></td>
    </tr>
    <tr>
      <td>Last Name（姓姓）</td>
      <td><input name="LastName" type="text" id="LastName" /></td>
    </tr>
    <tr>
      <td>Number（数字）</td>
      <td><input name="Number" type="text" id="Number" /></td>
    </tr>
    <tr>
      <td>Date（日期）</td>
      <td><input name="Date" type="text" id="Date" /></td>
    </tr>
    <tr>
      <td>Time Stamp（时间戳）</td>
      <td><input name="Timestamp" type="text" id="Timestamp" /></td>
    </tr>
    <tr>
      <td>Email（邮箱）</td>
      <td><input name="Email" type="text" id="Email" /></td>
    </tr>
  </table>
  <p>
    <input name="insert" type="submit" id="save" value="Save（保存） />
    <input name="insert" type="submit" id="cancel" value="Cancel（取消） />
  </p>
</form>

![](img/5a2c5fda68d4f5850276e49ec1_0.png)

图 7-12: InsertRecordValidation.php

# 第 6 节：删除详情

**目标：**在本节中，你将学习如何使用表单删除数据库中的记录。这与在 FileMaker 中删除记录的方法相同。删除记录的过程是将 RecordID 从列表页传递到详情页。当用户完成后，点击返回列表页，列表将刷新且记录将被移除。

**难度：**中等

**示例文件：**
- PHPFiles/Core/Lesson6/DeleteRecord.php

**页面导航：**
（此处应为导航图片）

![](img/5a2c5fda68d4f5850276e49ec11_12_0.png)

FileMaker API 方法：
- newFindAllCommand()
- newFindCommand()
- findCriterion()
- execute()
- setField()
- getMessage()
- Records()
- getField()
- RecordID()
- getByID()
- delete()

**代码：**

DeleteRecord.php

始终从包含数据库连接开始。创建一个表单来搜索记录。在这种情况下，表单通过该方法指向同一个页面。

```html
<form action="DeleteRecord.php" method="GET">
  First Name:<input name="FirstName" type="text">
  <br />
  <input name="submit" type="submit" />
</form>
```

创建 PHP 代码来搜索数据库并显示结果。这与之前的示例相同。

```php
<?php
if(empty('FirstName'))
{
  $FirstName = "";
  $request = $fm->newFindAllCommand('Demo php');
}
else
{
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
if (FileMaker::isError($result))
{
  echo "<p>Error: " . $result->getMessage() . "</p>";
  exit;
}
```

显示结果表的表头。

```php
echo '<table border="1">
  <tr>
    <th>First Name（名字）</th>
    <th>Last Name（姓）</th>
    <th>Number（数字）</th>
    <th>Date（日期）</th>
    <th>Time Stamp（时间戳）</th>
    <th>Calculation（计算）</th>
    <th>Record ID（记录ID）</th>
    <th>Delete（删除）</th>
  </tr>';
```

使用 `foreach` 循环显示数组中的每个字段内容。

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

# 删除 - 详情

![](img/5a2c5fda68d4f5850276e49ec_114_0.png)

| First Name | Last Name | Number | Date | Time Stamp | Calculation | Record ID | Delete |
|---|---|---|---|---|---|---|---|
| Tim | | | | | | | |
| Fred | | | | | | | | |
| Mike | | | | | | | | |
| Heath | | | | | | | | |
| Mike | | | | | | | | |
| Bell | | | | | | | | |
| Kevin | | | | | | | | |
| Emes | | | | | | | | |
| Frost | | | | | | | | |
| Garland | | | | | | | | |
| John | | | | | | | | |
| Luke | | | | | | | | |

