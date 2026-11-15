

让我们解释一下这里发生的情况：最初，假设必须显示表单，这就是为什么 $ok 被设置为 false。另一方面，如果表单刚刚被发送，那么 PHP 脚本最初假设一切正常 ($ok = true)。如果没有错误发生 (if ($ok))，则输出表单数据。但是，如果发生错误 (if (!$ok))，则输出表单本身。当然，如果页面在未发送表单的情况下直接调用，也会发生这种情况。这就是为什么脚本末尾有 if (!$ok) 独立查询的原因。

> **提示**
> 
> 如果发生错误，表单将直接显示——根本没有任何错误反馈。在 `if ($ok)` 之前的以下代码片段修复了这个问题：
> 
> if (!$ok) {
> echo "<p><b>Form incomplete</b></p>";
> }

## 13.3.2 单选按钮

如果一组单选按钮是必填字段，则必须选择其中一个按钮。可以通过简单检查 `$_GET["Field name"]` 或 `$_POST["Field name"]` 来验证，如下一个清单所示。

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
	$ok = true;
	if (!isset($_POST["Salutation"]) ||
		!is_string($_POST["Salutation"])) {
		$ok = false;
	}
	if (!isset($_POST["FirstName"]) ||
		!is_string($_POST["FirstName"]) ||
		trim($_POST["FirstName"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["LastName"]) ||
		!is_string($_POST["LastName"]) ||
		trim($_POST["LastName"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["Email"]) ||
		!is_string($_POST["Email"]) ||
		trim($_POST["Email"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["Promo"]) ||
	    !is_string($_POST["Promo"]) ||
	    trim($_POST["Promo"]) == "") {
	  $ok = false;
	}
	if (!isset($_POST["Comments"]) ||
	    !is_string($_POST["Comments"]) ||
	    trim($_POST["Comments"]) == "") {
	  $ok = false;
	}
}
```

清单 13.10 单选按钮组是必填字段（摘自 "form-validation-radiobuttons.php"）

## 13.3.3 复选框

复选框的验证与单选按钮的验证以相同的方式进行：只需检查是否为表单元素向 PHP 脚本传递了值。以下代码（和往常一样，更改以粗体突出显示）为我们示例中的条款和条件复选框执行此操作。

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
  $ok = true;
  if (!isset($_POST["Salutation"]) ||
      !is_string($_POST["Salutation"])) {
    $ok = false;
  }
  if (!isset($_POST["FirstName"]) ||
      !is_string($_POST["FirstName"]) ||
      trim($_POST["FirstName"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["LastName"]) ||
      !is_string($_POST["LastName"]) ||
      trim($_POST["LastName"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Email"]) ||
      !is_string($_POST["Email"]) ||
      trim($_POST["Email"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Promo"]) ||
      !is_string($_POST["Promo"]) ||
      trim($_POST["Promo"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Comments"]) ||
      !is_string($_POST["Comments"]) ||
      trim($_POST["Comments"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Terms"]) ||
      !is_string($_POST["Terms"])) {
    $ok = false;
  }
}
```

清单 13.11 复选框是必填字段（摘自 “form-validation-checkboxes.php”）

## 13.3.4 选择列表

乍一看，检查选择列表与之前的检查类似。但是，这里有一些特殊功能。对于一次显示多个元素的选择列表（<select size="..." > 或多选列表），可以提交表单而未选择任何内容。这与常规选择列表不同，常规列表中未选择任何内容时看起来不同。这在以下示例的列表中非常明显：

```
<select name="Number">
    <option value="0">Please select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
    <option value="4">4</option>
</select>
```

在此处，当表单发送时，列表元素始终被激活。因此，必须在 PHP 脚本中记下哪个元素对应 _未填写_ 状态。在示例中，这是带有值属性 0 的顶部值。以下清单显示了上下文中的相应查询。

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
    $ok = true;
    if (!isset($_POST["Salutation"]) ||
        !is_string($_POST["Salutation"])) {
        $ok = false;
    }
    if (!isset($_POST["FirstName"]) ||
        !is_string($_POST["FirstName"]) ||
        trim($_POST["FirstName"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["LastName"]) ||
        !is_string($_POST["LastName"]) ||
        trim($_POST["LastName"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Email"]) ||
        !is_string($_POST["Email"]) ||
        trim($_POST["Email"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Promo"]) ||
        !is_string($_POST["Promo"]) ||
        trim($_POST["Promo"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Number"]) ||
        !is_string($_POST["Number"]) ||
        $_POST["Number"] == "0") {
        $ok = false;
    }
    if (!isset($_POST["Comments"]) ||
        !is_string($_POST["Comments"]) ||
        trim($_POST["Comments"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Terms"]) ||
        !is_string($_POST["Terms"])) {
        $ok = false;
    }
}
```

清单 13.12 选择列表是必填字段（摘自 “form-validation-select-lists.php”）

> 提示
> 
> 你将再次看到双重检查：首先使用 isset()，然后直接通过选择列表中的值进行检查。这样可以避免尴尬的错误消息，以防某个恶作剧者试图向脚本发送完全空的表单（不含选择列表）。

使用多选列表时，始终会一次显示多个元素。如果用户不想输入任何内容，则不会向 Web 服务器发送任何信息。因此，此处使用 isset() 进行检查就足够了。

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
    $ok = true;
    if (!isset($_POST["Salutation"]) ||
        !is_string($_POST["Salutation"])) {
        $ok = false;
    }
    if (!isset($_POST["FirstName"]) ||
        !is_string($_POST["FirstName"]) ||
        trim($_POST["FirstName"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["LastName"]) ||
        !is_string($_POST["LastName"]) ||
        trim($_POST["LastName"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Email"]) ||
        !is_string($_POST["Email"]) ||
        trim($_POST["Email"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Promo"]) ||
        !is_string($_POST["Promo"]) ||
        trim($_POST["Promo"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Number"]) ||
        !is_string($_POST["Number"]) ||
        $_POST["Number"] == "0") {
        $ok = false;
    }
    if (!isset($_POST["Section"]) ||
        !is_array($_POST["Section"])) {
        $ok = false;
    }
    if (!isset($_POST["Comments"]) ||
        trim($_POST["Comments"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Terms"]) ||
        !is_string($_POST["Terms"])) {
        $ok = false;
    }
}
```

清单 13.13 多选列表是必填字段（摘自 "form-validation-multiselectlists.php"）

### 提示

如果多选列表包含多个条目（“请选择”选项、连字符等），那么你当然必须进行稍微复杂一些的检查。首先，你需要一个辅助函数，用于确定数组是否仅包含“垃圾值”。在我们的示例中，这些是空字符串和零；请根据你的要求进行调整：

```
function array_empty($a) {
    if (!is_array($a)) {
        return true;
    }
    foreach ($a as $value) {
        if ($value != "" && $value != "0") {
            return false;
        }
    }
    return true;
}
```

然后按如下方式调用多选列表检查：

```
if (!isset($_POST["Section"]) ||
    !is_array($_POST["Section"]) ||
    array_empty($_POST["Section"])) {
    $ok = false;
}
```

