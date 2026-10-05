

```
<body>
```

```html
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

![](img/5a2c5fda68d42e5d65f51850276e49ec_222_0.png)

图 7-60：CheckBox.php 文件。

# UpdateCheckBox.php

此文件用于更新复选框值，并根据更新是否成功向用户提供消息。始终从包含数据库的连接开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

使用 URL 中传递的 id 值查找记录。

```php
<?php
$record = $fm->getRecordById('Demo php', $_GET['id']);
```

根据 id 值更新记录。

```php
$id = $fm->newEditCommand('Demo php', $_GET['id']);
```

为了将 URL 中的复选框数组转换回 FileMaker 理解的换行符分隔的值列表，我们必须使用 PHP 的 `implode` 方法配合 `"\r"`（每个值之间的换行符）。这个 PHP 方法的好处是，它会自动合并 URL 中所有的复选框值。

```php
$Checkbox = implode("\r", $_GET ['Checkbox']);
```

```
implode(string, array); 用字符串连接数组元素。
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_222_1.png)

一旦以 FileMaker 格式组装好复选框值，我们就可以设置该字段。不要忘记检查 URL 中是否有值。如果没有值，你可以清除该字段。

```php
If(Empty($_GET ['Checkbox'])) {
  $edit->setField('Checkbox', "");
} else {
  $edit->setField('Checkbox', $checkBox);
}
```

在给用户提供反馈之前，执行更新并跟踪错误。

```php
$result = $edit->execute();
if (FileMaker::isError($result)) {
  die("错误: " . $result->getMessage());
} else {
  die("记录已成功更新.");
}
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_223_0.png)

![](img/5a2c5fda68d42e5d65f51850276e49ec_223_1.png)

图 7-61：复选框已用红色和蓝色更新。

# 第 24 节：多值列表

**目标：** 在节中，你将学习如何使用带有多个值的多值列表（即下拉列表）更新记录。此示例与复选框示例完全相同。唯一的区别在于多值列表的 HTML 代码。

**难度：** 中等

**示例文件：**
PHPFiles/Advanced/Lesson24/MultiValueList.php
PHPFiles/Advanced/Lesson24/UpdateMultiValueList.php

**页面导航：**

![](img/5a2c5fda68d42e5d65f51850276e49ec_224_0.png)

**FileMaker API 方法：**
- newFindAllCommand()
- execute()
- getMessage()
- getFirstRecord()
- getRecordID()
- Layout()
- GetValueList()
- getField()
- getRecordByID()
- newEditCommand()
- setField()

**代码：**

MultiValueList.php

多值列表使用重复代码将内容显示为 HTML。这使得数据库和 PHP 代码很容易组装多值列表。如果选择了某个值，你只需要添加 "selected"。此示例将创建的多值列表代码所示：

```html
<select name="MultiValueList" size="3">
  <option value="Dog" selected>Dog</option>
  <option value="Cat" selected>Cat</option>
  <option value="Fish">Fish</option>
  <option value="Bird">Bird</option>
</select>
```

始终从包含数据库的连接开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

查找所有记录并执行搜索。

```php
$request = $fm->newFindAllCommand('Demo php');
$result = $request->execute();
```

捕获错误。

```php
if (FileMaker::isError($result))
{
    echo "<p>错误: " . $result->getMessage() . "</p>";
    exit;
}
```

在本示例中我们只处理第一条记录。

```php
$record = $result->getFirstRecord();
```

获取记录 ID，以便将其传递到更新页面以隔离记录。

```php
$id = $record->getRecordID();
```

从 Demo php 布局获取多值列表，然后我们就可以为多值列表创建 HTML。

```php
$layout = $layout->getLayout('Demo php');
$multiValues = $layout->getValue('MultiValueList');
```

从 MultiValueList 中获取实际值。然后使用 PHP 的 `explode` 方法，使用换车符 ("\n") 作为分隔符将值分离到数组中。

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

