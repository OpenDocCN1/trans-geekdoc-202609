
```
if (getFormDataPOST('listname') == 'php3') {
    echo ' selected="selected"';
}
?>PHP 3</option>
<option value="php4"><?php
if (getFormDataPOST('listname') == 'php4') {
    echo ' selected="selected"';
}
?>PHP 4</option>
<option value="php5"><?php
if (getFormDataPOST('listname') == 'php5') {
    echo ' selected="selected"';
}
?>PHP 5</option>
</select>
```

*预填充选择列表 (`select-cookie.php`; 摘录)*

### 预选多个选择列表

```
if (isset($_POST['multilistname']) &&
in_array('php4', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
```

在预填充表单元素时，多选列表是最难实现的部分。这是因为在 `$_GET` 或 `$_POST` 中，你拥有一个已选选项的数组；因此不能简单地比较字符串，而必须在数组中查找指定的值。幸运的是，PHP 以 `in_array()` 函数的形式提供了合适的解决方案。因此所需的工作量与其它表单元素相比并没有多很多：如果当前值在 `$_GET`/`$_POST` 中，则输出 `selected` 属性。

### 预选多个选择列表

```
<select name="multilistname[]" multiple="multiple"
    size="3">
<option value="php3"><?php
if (isset($_POST['multilistname']) &&
    in_array('php3', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 3</option>
<option value="php4"><?php
if (isset($_POST['multilistname']) &&
    in_array('php4', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 4</option>
<option value="php5"><?php
if (isset($_POST['multilistname']) &&
    in_array('php5', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 5</option>
</select>
```

*预填充多选列表 (`select-multiple.php`; 摘录)*

然而，HTML 表单必须特别准备，以便 PHP 能访问多选列表的数据：`name` 属性的值必须以 `[]` 结尾，提示 PHP 应期望一个值数组，而不仅仅是一个字符串值。然而，访问列表数据仍然可以使用 `$_GET['listname']` / `$_POST['listname']` 来完成，而不是 `$_GET['listname[]']` / `$_POST['listname[]']`，如前面的代码所示。

如果你想用 cookie 中的数据预填充列表，只需使用前面章节中熟知的 `getFormData.inc.php` 文件即可。

### 预选多个选择列表

它包含两个额外的函数，它们返回数组而不是字符串。

```php
function getFormDataArrayGET($name) {
    if (isset($_GET[$name])) {
        return $_GET[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return array();
}
function getFormDataArrayPOST($name) {
    if (isset($_POST[$name])) {
        return $_POST[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return array();
}
```

*从 Cookie 中检索表单数据 (`getFormData.inc.php`: 摘录)*

这些函数为多选列表返回一个数组，你可以像在 `select-multiple.php` 中那样使用它。

```php
<?php
    require_once 'getFormData.inc.php';
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
<title>Forms</title>
</head>
<body>
<form method="post" action="
<?php echo htmlspecialchars($_SERVER['PHP_SELF']);
?>">
<select name="multilistname[]"
multiple="multiple" size="3">
<option value="php3"><?php
if (in_array('php3', getFormDataArrayPOST
('multilistname'))) {
echo ' selected="selected"';
}
?>PHP 3</option>
<option value="php4"><?php
if (in_array('php4', getFormDataArrayPOST
('multilistname'))) {
echo ' selected="selected"';
}
?>PHP 4</option>
<option value="php5"><?php
if (in_array('php5', getFormDataArrayPOST
('multilistname'))) {
echo ' selected="selected"';
}
?>PHP 5</option>
</select><br />
<input type="submit" />
</form>
</body>
</html>
```

预填充多选列表 (`select-multiple-cookie.php`; 摘录)

### 处理图形提交按钮

```
if (isset($_POST['Submit_x']) && isset($_POST['Submit_y']))
```

图形提交按钮（`<input type="image" />`）不仅是美化表单布局的好方法，还提供了一个不错的功能：浏览器在点击按钮时会提交鼠标指针的 x 和 y 坐标。在 PHP 中，这是通过在按钮的 `name` 属性后附加 `_x` 和 `_y` 并将其写入 `$_GET` 或 `$_POST` 来实现的。前面的代码评估了这些信息。

```
<?php
if (isset($_POST['Submit_x']) && isset($_POST['Submit_y'])) {
    printf('<h1>You clicked at the following coordinates: x-%s, y-%s</h1>',
    htmlspecialchars($_POST['Submit_x']),
    htmlspecialchars($_POST['Submit_y'])
    );
} else {
?>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
<input type="image" name="Submit" src="sams.gif" />
</form>
<?php
}
?>
```

注意

使用键盘提交表单时（例如使用 Enter 键），两个坐标都为 0。

### 检查必填字段

```
if (isset($_POST['Submit']) &&
    isset($_POST['textfieldname']) &&
    trim($_POST['textfieldname']) != '')
```

在验证表单时，大多数情况下重点在于必填字段。你可以通过两种方式检查它们是否包含值：

- 检查字段是否存在于 `$_GET`/`$_POST` 中

  ```
  if (!isset($_GET['fieldname'])) {
    // Error!
  }
  ```

- 检查 `$_GET`/`$_POST` 中的值是否包含除空白之外的信息

  ```
  if (trim($_GET['fieldname']) == '') {
    // Error!
  }
  ```

非常重要的一点是，你必须结合使用这两种技术。你始终必须使用 `isset()` 检查字段是否存在，以避免在尝试访问不存在的数组值时出现错误消息。但你始终必须检查字段中除空白之外是否还有内容，因为文本字段总是会被提交。此外，当为空时，`isset()` 始终返回 `true`，与字段的值无关。

### 检查必填字段

```
<?php
    if (isset($_POST['Submit']) &&
        isset($_POST['textfieldname']) &&
        trim($_POST['textfieldname']) != '') {
    echo '<h1>Thank you for filling out this
        form!</h1>';
    } else {
?>
    <form method="post" action="
<?php echo htmlspecialchars($_SERVER['PHP_SELF']);
    ?>">
        <input type="text" name="textfieldname"
            value="<?php
echo (isset($_POST['textfieldname'])) ?
    htmlspecialchars($_POST['textfieldname']) : '';
?>">
        <input type="submit" name="Submit" />
    </form>
<?php
    }
?>
```

*验证必填字段 (`mandatory.php`; 摘录)*

提示

该方法也适用于所有其他文本表单元素、单选按钮和复选框。它可以很容易地扩展以检查某些模式，包括有效的电子邮件地址。请参阅第 2 章“使用数组”，以获取在此处可能有帮助的短语。

注意

表单元素的预填充代码已被保留 intact，以便此代码片段可以与其他代码片段合并。因此，如果表单仅部分填写，则正确的表单字段会被预填充。

### 检查选择列表

```
isset($_POST['listname']) &&
$_POST['listname'] != ''
```

在验证选择列表时，方法取决于列表的类型：

- 如果是只能选择一个元素的列表，则在以下情况下被认为填写不正确

  - 列表中没有选项被选中

  - 选中的选项的值为空字符串

- 如果是可选择多个元素的列表，则在以下情况下被认为填写不正确

  - 列表中没有选项被选中

  - 所有选中的选项的值都为空字符串

如果列表包含无功能的占位条目，其标题例如为“Please choose from list”，则会出现值为空字符串的选项。这些列表选项必须不接收除 `""` 之外的其他值，以便验证算法能够将这些条目与合理的条目区分开来。

本短语开头的列表验证单个选择列表——再次包含用于预填充列表的PHP代码。

```
<?php
if (isset($_POST['Submit']) &&
    isset($_POST['listname']) &&
    $_POST['listname'] != '') {
echo '<h1>Thank you for filling out this
```

### 检查选择列表

```php
form!</h1>';
} else {
?>
<form method="post" action="<?php echo
    htmlspecialchars($_SERVER['PHP_SELF']); ?>">
  <select name="listname">
    <option value="">Please select from
      list</option>
    <option value="php3"><?php
if (isset($_POST['listname'])
&& $_POST['listname'] == 'php3') {
  echo ' selected="selected"';
}
?>>PHP 3</option>
    <option value="php4"><?php
if (isset($_POST['listname'])
&& $_POST['listname'] == 'php4') {
  echo ' selected="selected"';
}
?>>PHP 4</option>
    <option value="php5"><?php
if (isset($_POST['listname'])
&& $_POST['listname'] == 'php5') {
  echo ' selected="selected"';
}
?>>PHP 5</option>
  </select><br />
  <input type="submit" name="Submit" />
</form>
<?php
}
?>
```

*验证列表 (`mandatory-list.php`; 摘录)*

使用多个列表时，需要做更多的工作，如以下代码所示。如果表单已被提交，则会搜索所选列表元素的数组。如果找到一个非空元素，则过程完成，可以祝贺用户成功完成表单。否则，表单会再次显示。

```php
<?php
$ok = false;
if (isset($_POST['Submit']) &&
    isset($_POST['multilistname'])) {
    if (is_array($_POST['multilistname'])) {
        for ($i=0; $i <
            count($_POST['multilistname']); $i++) {
            if ($_POST['multilistname'][$i] != '') {
                $ok = true;
                break;
            }
        }
    }
}

if ($ok) {
    echo '<h1>Thank you for filling out this
        form!</h1>';
} else {
?>
<form method="post" action="
<?php echo htmlspecialchars($_SERVER['PHP_SELF']);
?>">
    <select name="multilistname[]"
        multiple="multiple" size="5">
    </select>
<br />
    <input type="submit" name="Submit" />
</form>
<?php
}
?>
```

### 将所有表单数据写入文件

```php
$data[] = $_POST;
file_put_contents('formdata.txt',
serialize($data));
```

用户正确填写表单后，你会如何处理表单数据？一种非常直观且不需要在服务器上做太多设置的方法是将数据写入服务器上的文件。
