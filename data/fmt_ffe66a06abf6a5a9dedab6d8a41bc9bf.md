
- 第 25 行：`if(@sizeof($blank_array) > 0)`
- 第 40 行：`include("form_phone_values.inc");`
- 第 41 行：`exit();`
- 第 42 行：如果字段为空
- 第 44 行：`echo "所有必要字段都已填写。"`
- 第 46 行：`else`

### 9

启动一个 `foreach` 语句，遍历 `$_POST` 数组。

表单中的所有信息都在该数组中。

### 11

启动一个 `if` 语句，如果字段为空，则执行。

### 13

启动一个 `if` 语句，如果字段不是 `middle_name` 则执行。`middle_name` 不是必填字段，因此允许为空。如果空字段不是 `middle_name`，则该字段名将存储在名为 `$blank_array` 的数组中（第 15 行）。

### 18

启动一个 `else` 语句，如果字段不为空则执行。

数据将经过清洗并存储在 `$good_data` 中，以便安全地显示在表单中。

## 第六卷

### 25

通过检查**第 1 章**中的 `$blank_array` 是否包含任何元素，确定是否发现了任何空字段。如果发现一个或多个空字段，脚本将构建一条错误信息**动态表单构建与**并将其存储在 `$message` 中。显示表单（第 40 和第 41 行）。错误信息显示在表单顶部，`$good_data` 中的信息显示在字段中。退出语句（第 42 行）在表单显示后停止脚本。用户必须点击提交按钮继续。

### 44

如果没有发现空字段，则第 25 行的 `if` 语句将不执行。第 44 行的 `echo` 语句将显示所有字段均正常的消息。

### 46

开始一个 `else` 语句，该语句在脚本首次运行时执行，在用户提交表单之前执行。显示空表单。

不要忘记退出语句。如果没有退出语句，脚本将继续运行并在显示表单后显示“所有必填字段均包含信息”。

图 1-10 显示了用户未输入名字或中间名时生成的网页。请注意，缺失信息列表不包含中间名（Middle Name），因为中间名不是必填的。此外，请注意用户最初输入表单的信息仍然显示在表单字段中。

### 检查信息的格式

每当用户必须在表单中输入信息时，你都可以预见到会有数量的拼写错误。你可以在提交表单时检测出其中的一些错误，向用户指出错误，然后要求他们重新输入信息。例如，如果用户在邮政编码（ZIP）字段中输入 `8899776`，你就知道这是错误的。这个信息太长不能作为邮政编码，也太短不能作为 ZIP+4 代码。

![Image 76](img/index-527_1.jpg)

**图 1-10:** 处理缺失信息的表单的结果。

你还需要保护自己不受恶意用户的影响——用户可能会破坏你的网站或数据库，或从你或你的用户那里窃取信息。你不希望用户在表单字段中输入 HTML 标签——这些标签发送到浏览器时可能会产生意外结果。特别危险的标签是脚本标签，它允许用户在表单字段中输入脚本。本节描述的检查数据可以防止意外问题和恶意用户。

如果你检查每个字段是否符合预期的格式，你就可以捕获拼写错误并防止大多数恶意内容。检查信息是一项平衡工作。你希望尽可能捕获错误数据，但不想阻止合法信息。例如，当你检查电话号码时，你可能会将其限制为数字。这种检查的问题是，它会过滤掉表单中 `555-5555` 或 `(888) 555-5555` 的合法数字，因此你还需要允许连字符 (`-`)、括号 (`()`) 和空格。你可能会将字段限制为 14 个字符长度，包括括号、空格和连字符，但这会过滤掉包含分机的海外号码。底线是：你需要仔细考虑对于任何字段你想要接受或过滤掉哪些信息。你可以使用正则表达式（即模式）来检查字段信息。你将字段中的信息与模式进行比较，看其是否匹配。如果不匹配，则字段中的信息是错误的，用户必须重新输入（有关正则表达式的更多信息请参阅第二卷第 2 章）。

通常，使用这些语句来检查字段：

```php
if(!preg_match("pattern",$variable)) {
    echo error message;
    display form;
    exit();
}
echo "Welcome";
```

`preg_match` 函数将模式与 `$variable` 中的输入值进行匹配，其中模式是一个正则表达式。注意 `if` 语句中的条件是负的。也就是说，`!`（感叹号）表示“不”。因此 `if` 语句实际上说是：如果变量中的值不匹配模式，则执行 `if` 块。

### 动态表单的构建与处理

例如，假设你想检查一个包含用户姓氏的输入字段。你可以预期姓名会包含字母而不是数字，并可能包含撇号和连字符（如 `O’Hara` 和 `Smith-Jones`）以及空格（如 `Van Dyke`）。此外，很难想象一个名字会超过 50 个字符。因此，你可以使用以下语句来检查姓名：

```php
if(!preg_match("/[A-Za-z' -]{1,50}/",$last_name)) {
    echo error message;
    display form;
    exit();
}
```

如果你想将连字符 (`-`) 作为允许字符的一部分放在方括号 `[]` 中，你必须将将其放在列表的开头或结尾。否则，如果你把它放在两个字符之间，脚本将其解释为两个字符之间的范围，例如 `A–Z`。

你还需要检查多选字段。虽然多选可以防止诚实用户犯错，但不能防止有恶意的聪明用户向字段中输入意外数据。你可以使用以下类型的正则检查多选字段的可接受输出：

```php
if(!preg_match("/male|female)/",$gender))
```

如果字段包含 `male` 或 `female` 以外的任何内容，则执行 `if` 块。第 11 行所示 `checkFormat.php` 脚本检查字段信息的格式。第 9 行的 `form_values.inc` 文件显示并处理表单。该脚本只检查格式，不检查必填字段。在大多数情况下，你希望像第 10 行的 `checkBlanks.php` 脚本那样既检查空字段，又检查格式。

```php
} // endif not blank

} // end of foreach loop for $_POST

/* if any fields were invalid, create error message and

34_167779 bk06ch01.qxp 12/17/07 8:55 PM Page 501

Processing Information from the Form

501

redisplay form */
if(@sizeof($error_array) > 0) // errors are found

➝**44**

{

/* create error message */
$message = "<ul style='color: red; list-style: none' >"; foreach($error_array as $value)

{

$message .= "<li>$value</li>";
}

$message .= "</ul>";

/* redisplay form */
extract($good_data);

➝**54**

extract($bad_data);

## Book VI

include("form_phone_values.inc");

## Chapter 1

exit();

➝**57**

} // end if blanks

## Dynamic Forms

echo "All required fields contain valid information";

➝**59**

## Building and Processing

} // end if submitted

else

➝**61**

{

include("form_phone_values.inc");

}

?>
```

对 `Listing 1-11` 后续说明中的数字指的是代码列表中的行号：

➝**6**

开始一个 `if` 语句来检查隐藏字段。如果隐藏字段存在，说明表单是由用户提交的。执行 `if` 语句。如果隐藏字段不存在，说明脚本是首次运行，不是由用户提交表单启动的，脚本将跳转到第 61 行的 `else` 语句。

➝**9**

开始一个 `foreach` 语句遍历 `$_POST` 数组。表单中的所有信息都在数组中。

➝**11**

开始一个 `if` 语句，如果字段不为空则执行。这是必要的，因为这样就不会对允许为空的字段进行无效格式的测试。

➝**13**

创建包含匹配正确格式模式的变量。`$name_patt` 包含匹配名称变量的模式；`$phone_patt` 包含匹配电话号码的模式。

➝**15**

开始一个 `if` 语句，针对名称字段执行。注意匹配模式后面跟着一个 `i`，这意味着忽略大小写。

➝**17**

开始一个 `if` 语句，测试名称字段中的数据是否匹配模式。如果数据不匹配模式，则将错误消息添加到名为 `$error_array` 的数组中，并将数据进行清洗后添加到名为 `$bad_data` 的数组中。如果数据匹配模式，则执行 `else` 语句（第 22 行），将数据添加到名为 `$good_data` 的数组中。

![Image 77](img/index-531_1.jpg)

34_167779 bk06ch01.qxp 12/17/07 8:55 PM Page 502

502 Processing Information from the Form

➝**27**

开始一个 `if` 语句，针对包含电话号码的字段执行。

➝**29**

开始一个 `if` 语句，测试电话字段中的数据是否匹配模式。如果数据不匹配模式，则将错误消息添加到名为 `$error_array` 的数组中，并将数据进行清洗后添加到名为 `$bad_data` 的数组中。如果数据匹配模式，则执行 `else` 语句，将数据添加到名为 `$good_data` 的数组中。

➝**44**

通过检查 `$error_array` 是否包含任何元素来确定是否发现了无效格式。如果发现一个或多个无效格式，脚本将构造错误消息并存储在 `$message` 中。显示表单（第 54–56 行）。错误消息显示在表单顶部，来自 `$good_data` 和 `$bad_data` 的信息显示在字段中。`exit` 语句（第 57 行）在表单显示后停止脚本。用户必须点击提交按钮继续。

➝**59**

如果没有发现无效格式，则第 44 行的 `if` 语句将不执行。第 59 行的 `echo` 语句显示一条所有字段都包含有效格式的消息。

➝**61**

开始一个 `else` 语句，在脚本首次运行时执行，即在用户提交表单之前。显示空白表单。

图 1-11 中的 Web 页面是用户无意输入电话号码乱码时产生的。

**图 1-11:**

处理带有错误信息的表单的结果。

34_167779 bk06ch01.qxp 12/17/07 8:55 PM Page 503

503 Processing Information from the Form

## 通过多个提交按钮为用户提供选择

你可以在表单中使用多个提交按钮。例如，在客户订单表单中，可能会使用一个显示为 `*提交订单*` 的按钮和另一个显示为 `*取消订单*` 的按钮。脚本中的逻辑代码可以检查提交按钮的值，并根据用户点击哪个按钮以不同的方式处理表单。

`Listing 1-12` 显示带有两个按钮的表单显示代码。包含显示和处理表单逻辑代码的脚本位于 `Listing 1-13` 中。

## Book VI

**Listing 1-12: 显示带有两个按钮的表单**

```html
<html>
<head><title>Two Buttons</title></head>
<body>
<form action='$_SERVER["SELF"]' method='POST'>
<p><label for='last_name' style='font-weight: bold'>Name: </label></p>
<input type='text' name='last_name' size='50' maxlength='65' />
<p><input type='submit' name='display_button' value='Show Address' />
<input type='submit' name='display_button' value='Show Number' />
</form>
</body>
</</html>>
```

**Listing 1-13: 处理两个按钮**

```php
<?php
/* Program name: processTwoButtons.php
* Description: 根据点击了哪个提交按钮显示不同的信息。
*/
if(isset($_POST["sent"]) && $_POST["sent"] == "yes")
{

include("dbstuff.inc");
$cxn = mysqli_connect($host,$user,$password,$database)
or die ("Couldn't connect to server");

if($_POST["display_button"] == "Show Address")
{

$query = "SELECT street,city,state,zip FROM Customer
WHERE last_name=$_POST["last_name"]";
$result = mysqli_query($cxn,$query)
or die ("Couldn't execute query.");

$row = mysqli_fetch_assoc($result);

extract($row);

echo "$street<br />$city, $state $zip";

}

else
{

$query = "SELECT phone FROM Customer
WHERE last_name=$_POST["last_name"]";
$result = mysqli_query($cxn,$query)
or die ("Couldn't execute query.");

$row = mysqli_fetch_assoc($result);

echo "Phone: {$row['phone']}";

}

}

else
{

include("form_two.inc");

}

?>
```

`Listing 1-13` 中的脚本 `processTwoButtons.php` 处理了 `Listing 1-12` 中的表单。该文件生成的表单如图 1-12 所示。注意提交按钮有一个名称：`display_button`。用户点击哪个按钮都会设置 `display_button` 的值。如果用户点击地址按钮，脚本将输出表单中提交名称对应的地址；如果用户点击 Show Number 按钮，脚本将输出电话号码。

## 创建一个允许客户上传文件的表单

有时你想从用户那里接收整个信息文件，例如求职网站的个人简历或相册网站的图片。或者，假设你正在根据销售部门提供信息构建目录。除了产品的描述文字外，你还希望销售部门提供产品图片。你可以提供一个供销售部门用于上传图像文件的表单。

# 使用表单上传文件

你可以使用为该目的设计的 HTML 表单来显示一个允许用户上传文件的表单。表单的通用格式如下：

```html
<form enctype="multipart/form-data" action="processfile.php" method="POST">
<input type="hidden" name="MAX_FILE_SIZE" value="30000" />
<input type="file" name="user_file" />
<input type="submit" value="Upload File" />
</form>
```

注意关于表单的以下几点：

- `<form>` 标签中使用了 `enctype` 属性。在上传文件时，必须将此属性设置为 `multipart/form-data` 以确保文件正确到达。
- 表单中包含一个隐藏字段，用于发送 `MAX_FILE_SIZE` 的值（字节为单位）。如果用户尝试上传大于此值的文件，则将无法上传。你可以将此值设置得高达 2MB。如果你需要上传大于 2MB 的文件，必须在向隐藏字段发送大于 2MB 的 `MAX_FILE_SIZE` 之前，先在 `php.ini` 中将 `upload_max_filesize` 的默认设置改为较大的数字。
- 用于上传文件的输入字段类型为 `file`。注意该字段有一个名称 —— `user_file` —— 正表单中其他类型的字段一样。

用户在表单中输入的文件名会被发送到处理脚本，并可以在内置数组 `FILES` 中可用。我们将在接下来的章节中解释 `FILES` 的结构和信息。

## 创建一个允许客户上传文件的表单

当用户提交表单时，文件会被上传到临时位置。脚本需要将文件复制到另一个位置，因为临时文件在脚本完成后就会被删除。

### 处理上传的文件

关于上传文件的信息存储在 PHP 内置数组 `$_FILES` 中。对于每个上传的文件，都有一个信息数组，导致 `$_FILES` 成为多维数组。与任何其他表单一样，你可以通过字段名称从数组中获取信息。以下是每个上传文件从 `$_FILES` 中获取的数组：

```text
$_FILES['fieldname']['name']
$_FILES['fieldname']['type']
$_FILES['fieldname']['tmp_name']
$_FILES['fieldname']['size']
```

例如，假设你使用上一节所示的以下字段来上传文件：
