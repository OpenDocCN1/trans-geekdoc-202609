
```php
$layout = $layout->getLayout('Demo php');
$multiValues = $layout->getValue('MultiValueList');
```

从 `MultiValueList` 中获取实际值。然后使用 PHP 的 `explode` 方法，使用换车符 `("\n")` 作为分隔符将值分离到数组中。

```php
$values = $record->getField('MultiValueList');
$values = explode("\n", $multiValues);
```

为多值列表创建 HTML。使用列表中的 `$multiValues` 与字段中的实际值进行比较。如果值在数组中，我们选择该值。否则，该值可以留空。使用 `foreach` 方法遍历列表的每一项。

```php
$multiValueList = '<select name="MultiValueList[]" size="3">';
if(in_array($multiValue, $values)) {
    $selected = 'selected';
} else {
    $selected = '';
}
```

构建多值列表的最终 HTML。

```php
$multiValueList .= '<option value="' . $multiValue . '" ' . $selected . '>';
$multiValueList .= '</select>';
```

一旦以 FileMaker 格式组装好多值列表，我们就可以设置该字段。使用列表中的 `$multiValues` 与字段中的实际值进行比较，来创建多值列表的 HTML。

```html
<html>
<head>
<title>多值列表</title>
</head>
<body>
<form action="UpdateCheckBox.php" method="get">
<input name="id" type="hidden" value="<?php echo $id; ?>">
请选择你喜爱的颜色。
<p>
<?php echo $checkbox; ?>
<p>
<input name="submit" type="submit" value="提交" />
</form>
</body>
</html>
```

# FileMaker Server 管理控制台

文件 编辑：服务器 菜单 帮助

## 配置：Web 发布引擎

Windows/TestServer

- FileMaker Server 概述

- 管理

  - 数据库

  - 计划

  - 统计数据

- 日志查看器

  - 配置

    - 通用设置

    - 管理员组

    - 数据库服务器

    - ODBC/JDBC

### 通用设置 PHP XML 即时 Web 发布

### PHP 发布

自定义 Web 发布允许 PHP Web应用程序通过 FileMaker API for PHP 访问数据。

- 启用 PHP 发布

### 记录数据预验证

使用 PHP 的自定义 Web 发布支持在将数据发送数据库之前，在 Web 服务器上对记录数据进行验证，以确保其正确性。

- 启用记录数据预验证

### 默认字符编码

设置 PHP 的默认字符编码。

默认字符编码：UTF-8

### 错误消息

设置 PHP 中错误消息使用的语言。

语言：英语 (English)

![](img/5a2c5fda68d42e5d65f51850276e49ec_229_0.png)

相关任务：

- 查看数据库

- 查看客户端

- 设置 Web 发布日志选项

难度：中

示例文件：

- `PHPFiles/Advanced/Lesson25/PreValidate.php`

- `PHPFiles/Advanced/Lesson25/UpdatePreValidate.php`

页面导航：

![](img/5a2c5fda68d42e5d65f51850276e49ec_229_1.png)

FileMaker API 方法：

```
newFindAllCommand()
execute()
getMessage()
FirstRecord()
RecordID(D)
getField()
getRecordBy()
newEditCommand()
setField()
validate()
getErrors()
```

## 代码：PreValidate.php

始终从包含数据库的连接开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

查找所有记录并执行搜索。

```php
<?php
$request = $fm->newFindAllCommand('Demo php');
$result = $request->execute();
```

捕获错误。

```php
if (Maker::isError($result)){
    echo "<p>Error: " . $result->getMessage() . "</p>";
    exit;
}
```

在本示例中，我们只需要处理第一条记录。

```php
$record = $result->getFirstRecord();
```

获取记录 ID，以便通过 URL 传递到更新页面以隔离该记录。

```php
$id = $record->getRecordID();
```

为带有表中值的字段创建变量，以便于创建 HTML 表单。

```php
$number = $record->getField('Number');
$date = $record->getField('Date');
$timestamp = $record->getField('Timestamp');
```

创建表单将值提交到更新页面。

```html
<html
<head>
<title>预验证数字</title>
</head>
<body>
<form action="UpdatePreValidate.php" method="get">
<input name="hidden" id="id" value="<?php echo $id; ?>">
<p>请输入一个大于 100 的数字以测试预验证字符。</p>
<input name="Number" type="text" value="<?php echo $number; ?>">
<p>请输入一个无效的日期（2/31/2010）以测试预验证年份函数。</p>
<input name="Date" type="text" value="<?php echo $date; ?>">
<p>请输入一个无效的时间戳以测试预验证时间戳函数。</p>
<input name="Timestamp" type="text" value="<?php echo $timestamp; ?>">
<p><input name="submit" type="submit" value="提交" />
</form>
</body>
</html>
```

## 预验证数字

![](img/5a2c5fda68d42e5d65f51850276e49ec_231_0.png)

请输入一个大于 100 的数字以测试预验证字符。

请输入一个无效的日期（2/31/2010）以测试预验证年份函数。

请输入一个无效的时间戳以测试预验证时间戳函数。

![](img/5a2c5fda68d42e5d65f51850276e49ec_231_1.png)

## PreValidate.php / UpdatePreValidate.php

更新表单将使用 PHP 引擎在更新数据库之前对数据进行预验证。始终从连接数据库开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

通过 URL 中的 ID 获取记录。更新字段。

```php
$edit = $fm->newEditCommand('Demo php', $_GET['id']);
$edit->setfield('Number', $_GET['Number']);
$edit->setfield('Date', $_GET['Date']);
$edit->setfield('Timestamp', $_GET['Timestamp']);
```

在更新数据库之前，使用该方法对数据进行验证。通过不传递任何字段名，该方法将根据数据库的字段设置对每个字段进行验证。

```php
$result = $edit->validate();
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_231_2.png)

`numErrors` 方法返回来自 PHP 引擎的错误数量。你可以使用 `getErrors` 方法返回实际的错误数组。

```php
if(FileMaker::isError($result)) {
    echo ' 验证失败<p>';
    $numErrors = $result->numErrors();
    echo '错误数量：' . $numErrors . '<p>';
    $sErrors = $result->getErrors();
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_232_0.png)

![](img/5a2c5fda68d42e5d65f51850276e49ec_232_1.png)

使用 `foreach` 循环方法显示所有错误结果。注意我使用了精确的数组值 `[0]`、`[1]` 和 `[2]`，因为每个错误数组中返回了恰好三个值。你可以将其视为数组的数组，或者在技术上被称为多维数组。

```php
foreach($errors as $error) {
    $field=$error[0];
    echo ' 字段名：' . $field->getName() . ', 错误代码：' . $error[1] . ', 值：' . $error[2] . '<p>';
} else {
    $result = $edit->execute();
    die("记录已成功更新。");
}
```

如果没有错误，你可以执行更新并告知用户更新成功。

![](img/5a2c5fda68d42e5d65f51850276e49ec_233_0.png)

**验证失败**

错误数量：3

字段名：Number，错误代码：3，值：101

字段名：Date，错误代码：7，值：2/31/2010

字段名：Timestamp，错误代码：8，值：2/31/2010

```php
$compoundRequest->add(3, $request3);
$compoundRequest->add(4, $request4);
```

| FileMaker Syntax: add(Precedence, FindRequest) |

| :--- |

| `$compoundRequest->add(1, $request1);` |

指定字段的排序顺序。注意使用数字顺序来指定排序字段。请记住 `FILEMAKER_SORT_ASCEND` 是默认的排序顺序。你只需要指定 `FILEMAKER_SORT_DESCEND`。

```php
$compoundRequest->addSortRule('MultiValueList', 1, FILEMAKER_SORT_ASCEND);
$compoundRequest->addSortRule('LastName', 2, FILEMAKER_SORT_DESCEND);
$compoundRequest->addSortRule('Number', 3, FILEMAKER_SORT_ASCEND);
```

最后，执行请求并显示结果。

```php
$result = $compoundRequest->execute();
```

从 `$result` 变量中获取记录。

```php
$records = $result->getRecords();
```

捕获错误。

```php
if (FileMaker::isError($result))
{
    echo "<p>Error: " . $result->getMessage() . "</p>";
    exit;
}
```

创建表格的表头。

```php
echo '<table border="1">
<tr>
<th>First Name</th>
<th>LastName</th>
<th>Number</th>
<th>Pet</th>
</tr>';
```

使用 `foreach` 方法显示字段。对于 `MultiValueList` 字段，我使用 PHP 的 `str_replace` 方法将换行符替换为逗号，以便信息以更易读的格式显示。

```php
foreach ($records as $record)
{
    echo '<tr>';
    echo '<td>' . $record->getField('FirstName') . '</td>';
    echo '<td>' . $record->getField('LastName') . '</td>';
    echo '<td>' . $record->getField('Number') . '</td>';
    echo '<td>' . str_replace("\n", ", ", $record->getField('MultiValueList')) . '</td>';
    echo '</tr>';
}
```

最后，关闭表格和 PHP 代码。

```php
echo '</table>';
?>
```

# 组合搜索

First Name*: Todd

OR Last Name*: Hutchinson

OR Number*: 9

OR Pet (OMIT): Cat

* 注意：搜索时所有值均为必填

| First Name | Last Name | Number | Pet |

| :--- | :--- | :--- | :--- |

| Clayton | Richard | 33 | Bird |

| Saif | Lane | 28 | Bird |

| David | Eckstein | 22 | Bird |

| Chris | Denorfia | 13 | Bird |

| Kevin | Corcia | 29 | Bird |

| Tim | Warner | 13 | Dog |

图 7-68：CompoundSearch.php 文件。

# 课程 27：跨所有的快速查找

**目标：** 在本节中，你将学习如何允许用户使用表单中的一个搜索框动态搜索布局上的所有字段。通过使用这种方法，你可以指定一个字段较少的单独布局，然后返回布局以显示更多字段。这可以防止你的数据库被索引，并显著加快搜索过程。此示例类似于 FileMaker 的快速查找功能。

**难度：** 困难

**示例文件：**

- `PHPFiles/Advanced/Lesson27/QuickFind.php`

- `PHPFiles/Advanced/Lesson27/ContainerBridge.php`

页面导航：

![](img/5a2c5fda68d42e5d65f51850276e49ec_238_0.png)

**FileMaker API 方法：**

- `getLayout()`

- `getFields()`

- `findAllCommand()`

- `newFindCommand()`

- `setLogicalOperator()`

- `getName()`

- `getResult()`

- `addFindCriterion()`

- `setResultLayout()`

- `execute()`

- `getMessage()`

- `Records()`

**代码：**

始终从包含数据库连接开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

从 `$_GET` 全局变量获取搜索准则。

```php
if (isset($_GET['Search'])) {
    $search = $_GET['Search'];
} else {
    $search = '';
}
```

清除 html 代码。

```php
$html = '';
```

获取快速查找布局对象。使用 Quick Find 布局搜索减少字段数量。切换回 Demo 页面以显示所有字段。

```php
$layout = $fm->getLayout('Quick Find');
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_238_0.png)

获取数组中的字段。该数组将用于搜索 Quick Find 布局上的字段。

```php
$fields = $layout->getFields();
```

检查用户是否提供了任何搜索准则。如果搜索字段为空，则显示所有记录。

```php
if ($search == '') {
  $request = $fm->newFindFirst('Quick Find');
}
else {
```

否则，创建一个新的搜索请求。

```php
$request = $fm->newFindFirst('Quick Find');
```

使用 `FILEMAKER_FIND_OR` 让匹配的请求返回并循环每个字段。

```php
foreach($fields as $field)
```

获取数组中当前字段的名称。

```php
$fieldName = $field->getName();
```

获取数组中当前字段的类型。

```php
$fieldType = $field->getResult();
```
