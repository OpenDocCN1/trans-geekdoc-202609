

# 第 23 Lesson：布尔复选框

**目标：** 在本中，你将学习如何使用值为 1 的布尔复选框来更新记录。当用户填写表单时，很容易创建一个布尔复选框来存储“是”的值（1），并为该框提供文本描述。你不应该为复选框的值使用长描述，这会浪费数据库空间并迫使你创建过多的特殊值列表。而布尔复选框可以用于多个字段。

**难度：** 简单

**示例文件：**
PHPFiles/Advanced/Lesson22/BooleanCheckBox.php
PHPFiles/Advanced/Lesson22/Update BooleanCheckBox.php

**页面导航：**

![](img/5a2c5fda68d42e5d65f51850276e49ec_216_0.png)

**FileMaker API 方法：**
newFindAllCommand()
execute()
getMessage()
getFirstRecord()
getRecordID()
getField()
getRecordByID()
newEditCommand()
setField()

**代码：**
BooleanCheckBox.php

始终从包含数据库连接开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

查找所有记录。

```php
<?php
$request = $fm->newFindAllCommand('Demo');
$result = $request->execute();
```

捕获错误。

```php
<?php
if (FileMaker::isError($result)) {
    echo "<p>Error: " . $result->getMessage() . "</p>";
    exit;
}
```

为了演示目的，我们只需要使用第一条记录。

```php
<?php
$record = $result->getFirstRecord();
```

## FileMaker 语法：getFirstRecord()

```php
<?php
$record = $result->getFirstRecord();
?>
```

获取 RecordID，以便我们可以在更新记录时将其传递到 URL 中。

```php
<?php
$id = $record->getRecordID();
?>
```

从 BooleanCheckbox 中获取当前值。

```php
<?php
$booleanCheckbox = $record->getField('BooleanCheckbox');
?>
```

创建用于更新记录的表单。

```html
<html
<head>
<title>Boolean Check.php</title>
</head>
<body>
```

该表单使用 get 方法指向 UpdateBooleanCheckbox.php。它在 URL 中发送了 Record ID 的隐藏值。接下来，你可以使用 PHP 的 strcmp 方法将我们在 PHP 代码中创建的变量 $booleanCheckbox 的当前值与值 1 进行比较。如果数据库中的当前值为 1，你可以输出 `checked='checked'`，这是在框中显示勾选标记的方法。最后，你可以完成复选框的编写，我们将复选框的名称与数据库（BooleanCheckbox）匹配，类型='checkbox' 且值为='1' 以接收更新。

```html
<form action="UpdateBooleanCheckbox.php" method="get">
    <input name="id" type="hidden" value="<?php echo $id; ?>">
    <input <?php
    if (strcmp($booleanCheckbox, 1)) {
        echo 'checked="checked"';
    }
    ?> name="BooleanCheckbox" type="checkbox" value="1" />
    <input name="submit" type="submit" value="Submit" />
</form>
</body>
</html>
```

strcmp(string1, string2): 比较两个字符串。注意比较是区分大小写的。

http://us.php.net/manual/en/function.php

# 布尔复选框

![](img/5a2c5fda68d42e5d65f51850276e49ec_218_0.png)

图 7-58：BooleanCheckBox.php 文件。

UpdateBooleanCheckBox.php

更新文件将用于使用复选框的值更新记录。始终从包含数据库连接开始。

```php
<?php
include('../../Conn/dbaccess.php');
?>
```

通过 URL 传递的 Record ID 获取记录。

```php
<?php
$record = $fm->getRecordById('Demo', $_REQUEST['id']);
?>
```

更新记录。

```php
<?php
$edit = $fm->newEditCommand('Demo', $_REQUEST['id']);
?>
```

设置布尔复选框字段非常简单。你只需将其设置为空，要么将其设置为值 1。取消勾选框（不发送任何值）的一个有趣效果是 BooleanCheckbox 的名称和值将不会传递到 URL 中。因此，你可以检查值是否为空，以确定是应该清除该字段还是使用 URL 中的值。

```php
<?php
if (Empty($_REQUEST['BooleanCheckbox'])) {
    $edit->setField('BooleanCheckbox', '');
} else {
    $edit->setField('BooleanCheckbox', $_REQUEST['BooleanCheckbox']);
}
?>
```

执行更新并捕获错误。

```php
<?php
$edit->execute();
if (FileMaker::isError($edit)) {
    die("Error: " . $edit->getMessage());
} else {
    die("The record was successfully updated.");
}
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_29_png)

记录已成功更新，值为 1。

# Lesson 23：多值复选框

**目标：** 在本中，你将学习如何使用具有多个值的布尔复选框来更新记录。复选框可以使用比一个字段更多的值。不幸的是，使用换行符来分隔复选框会导致 BooleanCheckbox 的名称和值将不会传递到 URL 中。因此，你可以检查值是否为空，以确定是应该清除该字段还是使用 URL 中的值。

**难度：** 中等

**示例文件：**
PHPFiles/Advanced/Lesson23/CheckBox.php
PHPFiles/Advanced/Lesson23/UpdateCheckBox.php

**页面导航：**

![](img/5a2c5fda68d42e5d65f51850276e49ec_220_png)

**FileMaker API 方法：**
FindAllCommand()
execute()
getMessage()
FirstRecord()
getRecordID()
getField()
getRecordByID()
newEditCommand()
setField()
()

**代码：**
CheckBox.php

始终从包含数据库连接开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

查找所有记录并捕获错误。

```php
<?php
$request = $fm->newFindAllCommand('Demo');
$result = $request->execute();
if (FileMaker::isError($result)) {
    echo "<p>Error: " . $result->getMessage() . "</p>";
}
```

为了演示目的，我们只需要使用第一条记录。

```php
<?php
$record = $result->getFirstRecord();
?>
```

获取 RecordID，以便我们可以在更新记录时将其传递到 URL 中。

```php
<?php
$id = $record->getRecordID();
?>
```

从 Demo 布局获取复选框列表，我们可以创建复选框的 HTML。

```php
<?php
$layout = $fm->get('Demo');
$checkBoxValues = $layout->getValueList('checkbox');
?>
```

从记录中获取实际值。然后使用 PHP 方法通过换行符（\n”）将值分离为数组。

```php
<?php
$values = $record->getField('Checkbox');
$values = explode("\n", $values);
?>
```

创建复选框的 HTML。使用值列表中的 checkBoxValues 与字段中的实际值进行比较。如果值在数组中，你可以勾选框。否则，该值可以留空。

使用 foreach 循环遍历每个值列表。

```php
$checkbox = '';
foreach($checkBoxValues as $checkBoxValue) {
    if(in_array($checkBoxValue, $values)) {
        $checked = 'checked="checked"';
    } else {
        $checked = '';
    }
}
```

现在值已经被勾选，你可以构建用于复选框的最终 HTML。Checkbox[] 将为传递到 URL 的每个值出现（Checkbox[]=Red&Checkbox[]=White&Checkbox[]=Blue）。如果不使用 [ ]，你只会得到最后一个值 - Checkbox[]=Blue。

```php
$checkbox .= '<input name="Checkbox[]" type="checkbox" value=' . $checkBoxValue . ' ' . $checked;
```

