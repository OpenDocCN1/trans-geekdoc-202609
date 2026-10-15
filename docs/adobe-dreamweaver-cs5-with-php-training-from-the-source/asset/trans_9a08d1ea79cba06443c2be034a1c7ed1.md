
如果不看到任何错误信息，这意味着 `display_errors` 在您的 PHP 配置中已关闭，或者 `error_reporting` 已设置为低于前一课中 [表 2.1](#ch02.html#ch02tab1) 所推荐的级别。

`3` 在浏览器中加载 `post_03.php`。页面包含相同的表单，但数据提交到另一个页面。

`4.` 点击“提交”按钮，而不在任一文本框中输入任何内容。与丑陋的错误信息不同，您应看到一个自定义错误信息以及一条链接，用于返回表单。

![Image](graphics/fig03_09.jpg)

`5.` 点击链接返回 `post_03.php`，并在两个框中填写内容。

`6.` 点击“提交”按钮。此次您应看到与上一练习相同的姓名问候。返回表单的链接不再显示。

控制页面显示内容的 PHP 代码如下：

`<?php`

`if (empty($_POST['first_name']) || empty($_POST['family_name'])) {`

`?>`  

`<p>Hey! You didn't fill in all the fields.</p>`

`<p><a href="post_03.php">Back to the form</a></p>`

`<?php } else { ?>`

`<p>Hi there! You must be <?php echo "{$_POST['first_name']} {$_POST['family_name']}"; ?>.</p>`

`<?php } ?>`

第一段 PHP 代码使用名为 `empty()` 的函数检查变量是否有值（函数在后文说明）。条件语句使用 `||`，因此只要任一文本框为空，结果即为 `TRUE`。要仅在两个字段均为空时显示错误信息和链接，请将 `||` 替换为 `&&`。

#### 使用逻辑非运算符

逻辑非运算符是感叹号（`!`），直接放在值或条件前面。它将 `TRUE` 变为 `FALSE`，反之亦然。

前一练习使用 `empty($_POST[‘first_name’])` 检查 `$_POST[‘first_name’]` 是否为空。在该表达式前加上感叹号，则会检查其相反情况。下面的条件语句判断 `$_POST[‘first_name’]` 是否**不为空**——即它包含值：

if (`!`empty($_POST['first_name'])) {  

    echo $_POST['first_name'];  

}

如果 `$_POST[‘first_name’]` 不为空，则大括号内的代码会输出该值；如果为空，条件为 `FALSE`，什么都不会发生。

#### PHP 视为假的值

PHP 将以下值视为假或隐式假：

• 关键字 `FALSE` 和 `NULL`（不区分大小写）

• 数字 0（作为整数、浮点数或字符串 `‘0’`）

• 空字符串（`‘’` 或 `“”`，中间无空格）

• 空数组（没有元素的数组）

• 由空标签创建的 SimpleXML 对象

其余所有值均视为真。

### ![Image](graphics/caution.jpg)`CAUTION!`

与 JavaScript 相比，PHP 将 `-1`（负一）视为 `TRUE`。还需注意，`FALSE` 与 `NULL` 是关键字，不能加引号。给它们加引号会把它们转换为非空字符串，从而被视为 `TRUE`。

### **使用函数执行任务**

*函数*会执行预定义任务。典型的 PHP 安装包含 1,500 多个内置函数，为您提供强大的工具箱。有些函数执行相对简单的任务，例如将字符串转换为大写；有些则能轻松处理复杂操作，如生成缩略图。大多数开发者只使用其中的一小部分函数，但了解它们的存在在需要时非常有用。

函数总以一对括号结尾。有时括号为空，例如显示 PHP 配置信息的 `phpinfo()` 函数。

然而，您经常需要通过在括号内传入值来调用函数。前一练习使用 `empty()` 检查 `$_POST[‘first_name’]` 与 `$_POST[‘family_name’]` 是否有值，方法是将每个变量单独传递给函数：

empty($_POST['first_name'])

这称为向函数 **传递参数**。

`empty()` 函数仅接受一个参数。其他函数可能接受多个参数，部分参数可选。当函数需要多个参数时，参数必须用逗号分隔，并**遵循函数期望的顺序**。记住要使用哪些参数以及顺序可能很困难，即使是经验丰富的程序员也会遇到这种困扰。好在 Dreamweaver 的代码提示功能可以免除您记忆所有细节的负担。

### ![Image](graphics/note.jpg)`NOTE:`

在脚本中向函数传递值时，这称为“参数”。而在函数定义中，它叫“形参”。两者区别极其细微，大多数开发者会 interchangeable 使用这两个词。本书中，我通常使用“参数”一词。

某些函数会修改传递给它们的变量值。例如，`sort()` 函数会改变数组的顺序。

$letters = array('c', 'a', 'b');  

sort($letters);  

// array is now 'a', 'b', 'c'

然而，在大多数情况下，您需要捕获函数对变量所做的任何更改，方法是将函数的返回值重新赋给同一个变量或赋给新变量。这样可以在需要时保留原始值。

课程 03 的练习文件示例：

**1.** 在文档窗口中打开 `function_01.php`。

**2.** 切换到代码视图。页面包含 HTML 与 PHP 的混合内容。HTML 仅用于说明目的。若专注于 PHP，代码如下：

$name = 'David';  

echo $name;  

echo strtoupper($name);  

echo $name;

第三行使用名为 `strtoupper()` 的函数，尽管其名字听起来怪异，一旦了解它是将 *str*ing *to upper*case（字符串转大写），便易于理解。

**3** 切换到设计视图，点击“Live View”按钮。您应看到 `$name` 的值已被 `strtoupper()` 转换为大写，而原始值保持不变。

![Image](graphics/fig03_10.jpg)

这种行为在需要不区分大小写比较两个字符串时很有用。如果您暂时将两个值都转换为大写，即可在不丢失原始拼写的前提下进行比较。

**4.** 打开 `function_02.php` 并在 Live View 中测试。该文件同样混合了 HTML 与 PHP，PHP 代码如下：

$name = 'David';  

**$name_upper = strtoupper($name);**  

echo $name_upper;  

echo $name;  

**$name = strtoupper($name);**  

echo $name_upper;  

echo $name;

在此例中，`strtoupper($name)` 的结果被赋给新变量 `$name_upper`。第一次显示 `$name_upper` 与 `$name` 时，`$name_upper` 为全大写，而 `$name` 保持不变。但在第五行，`strtoupper($name)` 被重新赋值给 `$name`，因此随后再次显示时，`$name_upper` 与 `$name` 均为大写。

![Image](graphics/fig03_11.jpg)

#### 读取 PHP 函数文档

那么，如何知道函数期望的参数以及是否需要将结果存入变量？RTFM。 depending on whom you ask and what mood they’re in, this stands for “read the fine manual,” “read the friendly manual,” or something not quite so polite.

