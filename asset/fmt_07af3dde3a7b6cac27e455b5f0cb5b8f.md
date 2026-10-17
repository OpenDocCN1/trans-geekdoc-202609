
```php
    $return_string .= "<B>" . $input_form->heading . "</B>";
    if ($input_form->headingElement()) {
      $return_string .= "<BR>";
    }
    $return_string .= $input_form->toString();
    $return_string .= "<BR>";
  }
  return($return_string);
}
```

```php
function hiddenVariablesString() {
  $return_string = "";
  while ($var_entry = each($this->hiddenVariables)) {
    $name = $var_entry['key'];
    $value = $var_entry['value'];
    $return_string .= "<INPUT TYPE=HIDDEN NAME=$name VALUE=$value>\n";
  }
  return($return_string);
}
```

```php
function submitButtonString() {
  $return_string = "<INPUT TYPE=Submit ";
  return($return_string);
}
```

```php
function headingElement() {
  // 覆盖以禁用
  return(TRUE);
}
```

```php
// 类的各个部分
abstract class HtmlInput {
  var $name; // 提交
  var $heading; // 标题
  function toString() {
    die("Subclass of HtmlInput");
  }
}
```

```php
class HtmlSelect extends HtmlInput {
  var $_valueArray = array();
  var $_selectedValue;
  function __construct($name, $heading, $value_array=NULL, $selected_value) {
    // 初始化
    if (!isset($name_array)) {
      ("("Select needs a minimum of two arguments, name, heading)");
    } else if (!is_array($value_array)) {
      ("Third argument to HtmlSelect should be array where keys are submitted, and values are display");
    } else {
      // 初始化
      $this->_name = $name;
      $this->_heading = $heading;
      $this->_valueArray = $value_array;
      $this->_selectedValue = $selected_value;
    }
  }
  function toString() {
    $return_string = "";
    $return_string .= "<SELECT NAME=" . $this->_name . ">";
    while ($var_entry = each($this->_valueArray)) {
      $submit_value = $var_entry['key'];
      $display_value = $var_entry['value'];
      if ($submit_value == $this->_selectedValue) {
        $return_string .= "<OPTION VALUE=$submit_value SELECTED>";
      } else {
        $return_string .= "<OPTION VALUE=$submit_value>";
      }
    }
    $return_string .= "</SELECT>";
    return($return_string);
  }
}
```

```php
class HtmlFormText extends HtmlInput {
  var $initial_value;
  function __construct($name, $heading, $initial_value="") {
    // 初始化成员变量
    if (!isset($name)) {
      if (!isset($heading)) {
        die("HtmlFormText constructor needs at least two arguments (name, heading)");
      }
      $this->name = $name; // 在父类定义
      $this->heading = $heading; // 在父类定义
      $this->initial_value = $initial_value;
    }
    function toString () {
      $return_string = "";
      $return_string .= "<INPUT TYPE=TEXT ";
      $return_string .= "NAME=$this->name";
      $return_string .= " VALUE=$this->initial_value";
      $return_string .= " >";
      return($return_string);
    }
}
```

```php
class HtmlFormTextArea extends HtmlInput {
  var $initial_value;
  var $rows;
  var $cols;
  var $wrapType;
  function __construct($name, $heading, // 可选参数：
    $initial_value="",
    $rows=1, $cols=60,
    $wrapType="VIRTUAL") {
    // 初始化成员变量
if (!isset($name)) {
  die("HtmlTextarea constructor needs *\n  at least two arguments (name, heading)");
}
  $this->name = $name; // name 在父类中定义
  $this->heading = $heading; // name 在父类中定义
  $this->initial_value = $initial_value;
  $this->rows = $rows;
  $this->cols = $cols;
  $this->wrapType = $wrapType;
}
function toString() {
  $return_string = "";
  $return_string .= "<TEXTAREA NAME=$this->name> ";
  $return_string .= "ROWS=$this->rows ";
  $return_string .= "COLS=$this->cols ";
  $return_string .= "WRAP=$this->wrapType ";
  $return_string .= $this->additionalAttributes();
  $return_string .= "=$this->initial_value>";
  $return_string .= "</TEXTAREA>";
  return($return_string);
}
function additionalAttributes() {
  // 重写此方法以返回包含
  // NAME、COLS 和 WRAP 以外的 Textarea 属性字符串
  return("");
}
```

所有这些对象的设计都包含一个带有默认参数的构造函数，以及一个返回表单或其部分 HTML 的 `toString()` 方法。表单存储输入片段（这些片段可能会由更高级的版本重新排序或布局），并递归地对这些片段调用 `toString()`。支持的 HTML 表单元素：`TEXTAREA`、`SELECT`。

这里是一个生成简单表单页面的示例：

```php
<HTML></HEAD><body>
<?php include("form_printer.php");
$my_form = new HtmlForm($PHP_SELF);
$my_form->addInputForm(
  new HtmlText("firstname",
    "First Name:");
);
$my_form->addInputForm(
  new HtmlText("lastname",
    "Last Name:");
);
$my_form->addInputForm(
new HtmlFormSelect(
    "age",
    "Age",
    array(0) => "0 - 19",
    1 => "20 - 29",
    2 => "Senior citizen")
);
$my_form->addInputForm(
new HtmlFormTextArea(
    "feedback",
    "What's on your mind?",
    ["Please fill in your personal rating",
    5)
);
print($my_form->toString());
?>
</body>
</html>
```

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_443_0.png)

这段高性能代码非常直观，关注的是各种 HTML 语法。从 PHP 中 OOP 的角度来看，有两个值得注意的点。

第一个是 `Htmlinput` 类被指定为抽象类。这意味着它的存在不是为了被实例化，而是为了被继承。第二个感兴趣点是 `Htmlform` 类有一个数组，用于持有 `Htmlinput` 对象。由于 PHP 是弱类型类型的，除非制造商批准的方法在插入时进行某些类型检查，否则你无法强制规定在任何时候都不添加新的表单（`addInputForm()`）。如果该类的用户仅依赖方法，我们可以确保该数组中的所有内容将是 `Htmlinput`（或其子类）的实例，并且在显示时应该是良好的表单。私有标记确保了数组在运行时无法从类外部进行操作。

# 常见陷阱与故障排除

本着第11章的精神，我们在接下来的章节中提供了问题代码最可能的两种症状以及最可能的原因。

## 症状：成员变量在成员函数中没有值

这可能有许多原因，当然，最常见的是对引用变量的方式感到混淆。语法是：

```php
$this->member_name
```

如果你的函数直接引用 `$member_name`，那通常是一个未绑定的变量，并且无论如何都无法成功引用成员变量。同样，如果你的函数引用 `$this->member_name`，你是在请求一个名为 `member_name` 的字段（这可能是未绑定的）。

## 症状：解析错误，期望 `T_VARIABLE` ...

当然有很多方法可以弄乱类定义，以至于 PHP 在尝试解析它时会报错。常见的错误再次是缺少 `$` 符号。类声明如下：

```php
class MyClass {
    var my_var; // 错误
}
```

这会导致某种解析错误，因为语法需要 `$my_var`。

# PHP 中的 OOP 风格

OOP 编程风格是一个巨大的课题，并且超出了本书的范围。然而，本着第3章的精神，我们在接下来的章节中提供了关于编写可读、可维护 PHP 代码的简要介绍。

## 命名规范

在本节中，我们遵循有关对象的 PEAR 代码风格：

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_445_0.png)

> 关于 PEAR 项目和 PEAR 代码风格的更多信息，请参见第28章或 PEAR 网站。

PEAR 建议类名以大写字母开头，并用下划线分隔。构建大型 OOP 项目时，你可能希望用自己的类名遵循这种下划线约定。成员变量和函数名的第一个字母应为小写。此外，意图在类内部使用的（而不是通过外部代码）名称应以下划线开头。类中持有内容的变量将被称为 `wordCount`（意图从外部访问）或 `_wordCount`（意图为私有）。

## 访问器函数

另一种记录意图的风格是将变量设置为私有，并提供"getter"和"setter"函数。例如，你可能会定义这样的类：

```php
class Customer {
    private $name;
    private $creditNumber;
    private $rating;
}
function getName() {
    return($this->name);
}
function getRating() {
    return($this->rating);
}
function setRating($rating) {
    $this->rating = $rating;
}
```

## 继承设计

正如我们所说的，类层次设计是一个巨大的研究领域，我们并不打算对此贡献。作为一个风格问题，考虑你是否意图让类被继承，并通过注释或定义结构来指示你的决定是值得的。

例如，你可能意图让类永远不要被继承，在这种情况下你可能只需要在注释中说明（目前 PHP 中没有方法可以强制类不能被继承）。在光谱的另一端，你可能意图让类或部分类仅用于继承。你可以在注释中指示这一点，或者使用我们在列表2-8 `HTMLForm` 定义中使用的技巧：提供在基类中直接调用的方法。最后，当然你可能有一些可以在基类中直接调用的方法，但专门设计用于重写。你可能希望将这些"钩子"方法组合在类定义中标记标记的部分，以便派生类的编写者快速发现。

# 总结

PHP 提供了支持面向对象编程的基础。其中，PHP 中的 OOP 语法允许程序员定义带有成员变量和数据的类，并提供了单继承、构造函数、对象序列化和反射函数。PHP 中没有内容要求你以面向对象的风格编写，但如果你喜欢那种风格，可以编写任何你想写的内容。尽管语言的面向对象能力在 PHP5 中大大提高，但率地说，PHP 的面向对象部分最初并不是面向对象的语言，具有 OOP 经验的开发者会缺少其他 OOP 语言的某些方面。另一方面，OOP 扩展是可用的、相当成熟的、非常稳定且广泛使用的。它提供了一个额外的组织层，在维护复杂代码时会有帮助，并为代码的分发和重用提供了一种很好的方式。

# 高级数组函数

在第 9 章中，我们向你介绍了数组及其用途以及一些处理数组的方便函数。在随后的章节中，我们看到了 PHP 如何将其许多结果以数组的形式返回，特别是在处理数据库函数集时。本章将查看并返回处理 PHP 数组的一些更高级函数的结果。

## 数组的转换

一旦你将数据存储在数组中，PHP 提供了系列函数来操作它们。这些函数的共同点是，它们接收你的数组，对其进行处理，并将结果返回另一个数组中。（我们将数组排序函数推迟到以后的章节。）

本章未涵盖 `explode()` 和 `implode()`，它们可以将字符串转换为数组反之亦然。我们将在第 22 章介绍这些非常实用的函数。

在第 9 章中，我们独立开发了一个函数来打印数组的全部内容，在本章中，我们将使用这些最后一个最后一个（`print_keys_and_values_each()`）来显示示例中返回的数组。我们在这里再次使用这个函数，放在一个更通用的函数中：

```php
function print_keys_and_values_each($array_to_test) {
  // 可靠地打印数组中的所有内容
  reset($array_to_test);
  while ($array_cell = each($array_to_test)) {
```
