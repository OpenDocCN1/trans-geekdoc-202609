

# 附录 A：练习解答

## 第 13 章

### 练习 1 解答

为了提取男女女性访问者的页面访问总数，你需要将 `members` 表与 `accessLog` 表连接起来。你可以使用 `sum()` 函数对 `numVisits` 计数进行总计，并使用 `GROUP BY` 子句对结果进行分组。使用表和列别名有助于提高查询和结果集的可读性：

```mysql
mysql> SELECT m.gender, sum(al.numVisits) AS totalPageView FROM members m, accessLog al WHERE m.id = al.memberId GROUP BY m.gender;
+--------------------------------------+
| gender | totalPageView |
+--------+----------------+
| m      | 6 |
| f      | 3 |
+--------+----------------+
2 rows in set (0.00 sec)
```

### 练习 2 解答

要让 `getMembers()` 方法根据兴趣进行过滤，你只需要修改几行代码。首先，指定一个可选参数 `$interest` 并赋予一个默认值（例如空字符串）。在方法内部，检查是否提供了 `$interest` 值。如果提供了值，则在 `SELECT` 查询中添加 `WHERE` 子句以对 `otherInterests` 字段进行过滤。记得使用 `LIKE` 运算符来搜索兴趣项，并出于安全考虑，对 `$interest` 值使用占位符。

此外，如果提供了 `$interest` 值，则额外调用一次 `PDOStatement::bindValue()` 将 `$interest` 值传递给查询，并将该值封装在 `% ...%` 通配符中，以便搜索整个字段。

以下代码显示了 `getMembers()` 方法，并高亮了新增或修改的行：

```php
public static function getMembers($startRow
$stmt->bindValue( :startRow, $startRow, PDO::PARAM_INT );
$stmt->bindValue( :numRows, $numRows, PDO::PARAM_INT );
if ( $interest ) $stmt->bindValue( :interest, "%$interest@%", PDO::PARAM_STR );
$stmt->execute();
$members = array();
foreach ( $stmt->fetchAll() AS $row ) {
    $members[] = new Member($row);
}
$row = $conn->query("SELECT found_rows() as totalRows");
$row = $stmt->fetch();
parent::disconnect($conn);
return array($members, $row['totalRows']);
} catch ( PDOException $e ) {
    parent::disconnect($conn);
die("Query failed: " . $e->getMessage());
}
```

## 第 14 章

### 练习 1 解答

为了按流行程度排序类型列表，你需要统计有多少成员将每个类型列为最喜。然后只需使用 `GROUP` 子句按类型对结果进行分组，并使用 `ORDER BY` 子句对结果进行排序：

```mysql
mysql SELECT favoriteGenre AS genre, count(favoriteGenre) AS popularity FROM members GROUP BY genre ORDER BY popularity DESC;
+----------+----------+
| genre | popularity |
+-------+----------+
crime | 2 |
thriller | 1 |
romance | 1 |
horror | 1 |
SciFi | 1 |
NonFiction | 1 |
+----------+----------+
6 rows in set (0.00 sec)
```

### 练习 2 解答

你已经创建了 `LogEntry::deleteAllMember()`，这是一个删除特定成员所有日志记录的方法。因此，你只需要在成员编辑页面上添加按钮，然后创建一个函数来执行删除操作。

以下是修改后的 `view_member.php` 脚本的某些片段，其中包含了“清除访问日志”功能。新增的代码行已高亮。

```php
if ( isset($_POST['action']) && $_POST['action'] == "Save Changes") {
    saveMember();
} else if (isset($_POST['action']) && $_POST['action'] == "Delete Member") {
    deleteMember();
} else if (isset($_POST['action']) && $_POST['action'] == "Clear Access Log") {
    clearLog();
} else {
    displayForm(array(), $member);
}
```

```html
<div style="clear">
    <input type="submit" name="action" id="saveButton" value="Save Changes" />
    <input type="submit" name="action" id="deleteButton" value="Delete Member" style="margin-right: 20px; />
    <input type="submit" name="action" id="clearButton" value="Clear Access Log" style="margin-right: 20px; />
</div
```

```php
function deleteMember() {
    $member = new Member(array(
        "id" => isset($_POST['memberId']) ? (int)$_POST['memberId'] : "",
    ));
    LogEntry::deleteAllMember($member->getValue("id"));
    $member->displaySuccess();
}
```

```php
function clearLog() {
    $id = isset($_POST['memberId']) ? (int)$_POST['memberId'] : "";
    LogEntry::deleteAllMember($id);
    displaySuccess();
}
```

```php
function displaySuccess() {
}
```

## 第 15 章

### 练习 1 解答

Numbers_Roman 是一个非常简单的包。你可以在 http://pear.net/package/Numbers_Roman/latest/ 找到它的文档。

第一步是按照 usual安装该包：

```bash
pear install Numbers_Roman
downloading Numbers_Roman-1.0.2 (2110 bytes)
...done: 2110 bytes
install ok channel=pear.php.net/Numbers_Roman-1.0.2
```

该包提供了一个带有两个静态方法的类：

- Numbers_Roman::toNumber() 将罗马数字转换为其对应的阿拉伯数字。
- Numbers_Roman::toNumerical() 将作为第一个参数提供的数字转换为罗马数字。第二个参数默认为 `true`，以大写形式显示数字；将其设置为 `false` 可以小写形式显示。第三个参数也默认为 `true`，规定如果数字超过 3999（根据罗马系统的要求），则应输出用于显示带下划线数字的 HTML 标记。将其设置为 `false` 可关闭任何下划线。

在本次练习中，你想要使用 `Numbers_Roman::toNumerical()`。你需要做的是创建一个循环，遍历 1 到 100 的整数，为每个整数调用 `Numbers_Roman::toNumerical()` 并输出结果：

```html
<!DOCTYPE html "-//W3C//DTD HTML 1.0 Strict//EN">
"http://www.w3.org/TR/html1/strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml-lang="en" lang="en">
<head>
<title>1 to 100 in Roman</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>1 to 100 in Roman</h1>
<p>
<?php
require_once("Numbers/Roman.php");

for ($i=1; $i<=100; $i++) {
echo Numbers_Roman::toNumerical($i, true, true) . "<br />";
}
?>
</p>
</body>
</html>
```

### 练习 2 解答

既然你已经知道如何使用 HTML_Form（在本章之前的示例）和 Numbers_Roman（上一个练习），这个练习就没有问题了。你需要创建一个新的 `HTML_Quick` 对象，填充一个用于转换的字段和一个转换按钮，并添加验证规则以检查用户是否输入。这简单只需检查输入的数字是阿拉伯数字还是罗马数字（可以使用 PHP 的 `is_numeric()` 函数），并运行相应的转换。

这是一个示例。出于安全考虑，脚本在 `convertNumber()` 函数中包含了几行额外的代码：

```html
<!DOCTYPE HTML "-//W3C//DTD HTML 1.0 Strict//EN">
"http://www.w3.org/TR/xhtml/strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml-lang="en" lang="en">
<head>
<title>Roman numbers converter</title>
</head>
<body>
<h1>Roman numbers converter</h1>
<?php
require_once("HTML/QuickForm.php");
require_once("Numbers/Roman.php");
$form = new HTML_QuickForm("ConvertForm", "get", "", null, true);
$form->addElement("text", "number", "Number (in Arabic or Roman format)");
$form->addElement("submit", "convertButton", "Convert");
$form->addRule("number", "Please enter a number", "required");

if ($form->submitted() && $form->validate()) {
    $form->process("convertNumber");
}

function convertNumber($values) {
$originalNumber = $values["number"];

if (is_numeric($originalNumber)) {
$numerals = "Roman";
$originalNumber = (int)$originalNumber;
$convertedNumber = Numbers_Roman::toNumeral($originalNumber, true, true);
} else {
$numerals = "Arabic";
$originalNumber = preg_replace("[^IVXLCM]/i", "", $originalNumber);
$convertedNumber = Numbers_Roman::toNumber($originalNumber);
}

echo "<p>$originalNumber in $numerals is: $convertedNumber</p>";
}

?>
</body>
</html>
```

