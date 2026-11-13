

在循环的每一步中，脚本会将 $value 的当前值与传入的 $default 值进行比较。如果两者匹配，则会在生成的 HTML 中包含 CHECKED 属性。同样，这里的空格很重要；请注意，CHECKED 后面的空格会被添加到 HTML 字符串中。

$default 参数被指定为可选。如果 generate_radio_group 仅使用两个参数调用，则默认情况下不会选择任何单选按钮。

### HTML 实体

htmlentities 函数用于将字符串中的某些字符替换为相应的 HTML 实体。因为 $name 和 $value 的值是在另一个 HTML 标签内部输出的，所以 htmlentities 函数非常重要，可以确保这些字符串中没有可能破坏标签的字符。

## 创建动态菜单

创建下拉菜单的过程与创建单选按钮组的过程非常相似。同样，这次需要一个循环来依次为每个选项生成一个 <OPTION> 标签。该函数还需要在选项列表周围包含 <SELECT> 和 </SELECT> 标签。函数 generate_menu 将如下所示：

```
function generate_menu($name, $options, $default="") {

    $html = "<SELECT NAME=\"$name\">";
    foreach($options as $value => $label) {
        $html .= "<OPTION ";
        if ($value == $default)
            $html .= " SELECTED ";
        $html .= "VALUE=\"$value\">$label</OPTION>";
    }
    $html .= "</SELECT>";
    return($html);
}
```

此函数返回的字符串包含生成含有所提供选项的下拉菜单的完整 HTML 代码。您可能更希望该函数仅返回选项标签，然后在其周围放置您自己的 <SELECT> 标签；例如，这样可以方便地在菜单上添加 JavaScript onChange 事件。

## 多选项目

当与 MULTIPLE 属性一起使用时，<SELECT> 表单项允许用户从菜单中选择多个选项，通常是通过在单击选项时按住 Ctrl 键来实现。要在 PHP 中处理多个选定项，输入名称必须是一个数组。然后，当表单被提交时，数组中的元素将依次包含每个选中项的值。

例如，如果您使用以下 HTML 创建一个多选菜单，并将其提交给仅包含 print_r 语句的 PHP 脚本，您会发现 $_POST["colors"] 是一个数组，其中包含每个选中选项的一个元素：

```
<SELECT MULTIPLE NAME="colors[]">
<OPTION VALUE="red">Red</OPTION>
<OPTION VALUE="white">White</OPTION>
<OPTION VALUE="blue">Blue</OPTION>
</SELECT>
```

当三个选项都被选中时，$_POST["colors"] 包含三个带有数值索引 0 到 2 的元素，其值分别为 red、white 和 blue。

同样的原理适用于任何类型的表单输入。如果多个项目具有相同的名称，但名称以一对方括号结尾，则 PHP 会创建一个带有该名称的数组，其中包含每个项目值的一个元素。

在使用复选框实现多选输入时，这最有用。您不必为每个复选框提供唯一的名称，而是可以为每个复选框提供数组的名称。在提交表单时创建的数组包含每个选中项的一个元素。

本课的最后一个示例涉及函数 generate_checkboxes，它创建一组具有相同名称的复选框，可用作 <SELECT MULTIPLE> 的替代方案，以在 HTML 表单中实现多选选择。该函数及其用法的简单示例显示在清单 12.4 中。

### 清单 12.4. 使用复选框创建多选选择
```
<?php

function generate_checkboxes($name,
    $options, $default=array()) {
    if (!is_array($default))
        $default = array();

    foreach($options as $value => $label) {
        $html .= "<INPUT TYPE=CHECKBOX ";
        if (in_array($value, $default))
            $html .= "CHECKED ";
        $html .= "NAME=\"{$name}[]\" VALUE=\"$value\"><br>";
    }

    return($html);
}

$options = array("movies" => "Going to the movies",
    "music" => "Listening to music",
    "sport" => "Playing or watching sports",
    "travel" => "Traveling");
$html = generate_checkboxes("interests",
      $options, $interests);
?>
<H1>Please select your interests</H1>
<FORM ACTION="interests.php" METHOD=POST>
<?php print $html;?>
<INPUT TYPE=SUBMIT VALUE="Continue">
</FORM>
```

在函数 generate_checkboxes 中，$default 参数是一个数组而不是单个值；毕竟，默认情况下可能会选择多个选项。作为 $default 传入的数组可以与该函数创建的 HTML 提交到 PHP 的数组完全相同。

要确定每个复选框是否应具有 CHECKED 属性，会调用 in_array 来查看当前选项名称是否在默认值列表中。如果 $value 出现在 $default 的任何位置，则在页面加载时将选中该复选框。

清单 12.4 展示了该函数的实际应用，使用网页的一部分询问用户她的兴趣。她可以从列表中选择任意数量的项目，并且在此示例中，脚本会提交给自身，选项保持选中状态，以便用户如果想更改主意可以更改。

在 PHP 中创建的数组 $interests 中，每个元素都是 $options 中的键名。如果您想找到与每个选中选项对应的标签，可以引用 $options 中的相应元素。

## 总结

在本课中，您学习了如何即时生成 HTML 组件，并学习了一些创建动态表单输入对象的技术。在下一课中，您将学习如何对 HTML 表单进行验证。

## 第 13 课。表单验证

在本课中，您将学习一些以用户友好的方式验证表单输入的技术。

验证用户提交的输入的原则相当简单：只需依次检查 $_POST 中的每个项目，并确保其符合一组标准。但是，确保用户能够以最少的麻烦纠正任何错误并重新提交表单，则提出了更大的挑战。

### 强制必填字段

表单验证最基本的类型是强制特定字段必须包含一个值。在提交未输入任何值的文本输入的情况下，$_POST 中的元素仍然被创建，但它包含一个空值。因此，您不能使用 isset 来检查是否输入了值；您必须检查元素的实际值，要么将其与空字符串进行比较，要么使用以下带有布尔非运算符的更紧凑语法：

```
if (!$_POST["fieldname"]) { ... }
```

因为表单中的每个字段都会在 $_POST 中创建一个元素，如果每个字段都需要输入值，您可以使用一个简单的循环来检查数组中是否没有空值：

```
foreach($_POST as $field => $value) {
    if (!$value) {
        $err .= "$field is a required field <br>";
    }
}
if ($err) {
    echo $err;
    echo "Press the back button to fix these errors";
} else {
    // Continue with script
}
```

与在发现空字段时立即退出不同，此脚本会构建一个错误字符串 $err。验证完成后，如果有任何错误，将显示 $err 的内容。如果没有错误，$err 为空，脚本执行将继续执行 else 子句。

> **验证警告** 立即显示所有与提交的数据相关的警告消息。您应该给用户一次性纠正所有错误的机会。

这种方法的一个明显局限是您无法选择哪些字段需要值；每个提交的字段都必须填写。您可以通过在脚本中提供必填字段列表来改进这一点，并且通过使用关联数组，您还可以为每个字段提供一个标签以在警告消息中显示：

```
$required = array("first_name" => "First name",
    "email" => "Email address",
    "telephone" => "Telephone number");
foreach($required as $field => $label) {
    if (!$_POST[$field]) {
        $err .= "$label is a required field <br>";
    }
}
```

