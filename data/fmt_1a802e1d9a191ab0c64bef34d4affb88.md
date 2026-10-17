
```php
echo '<td>' . $record->getField('LastName') . '</td>';

echo '<td>' . $record->getField('Number') . '</td>';

echo '<td>' . $record->getField('Date') . '</td>';

echo '<td>' . $record->getField('Timestamp') . '</td>';

echo '<td>' . $record->getField('Calculation') . '</td>';

echo '<td>' . $record->getField('RecordID') . '</td>';

$row++;

}
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_188_0.png)

| First Name | Last Name | Number | Date | Time | Calculation | Record ID |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Todd | Duel | 47 | 09/07/2010 | 08/03/2010 | 14:56:40 | 52 |
| Tim | W | 13 | 08/01/2010 | | | 59 |
| Fred | Hutchison | 14 | 08/09/2010 | | | 22 |
| Mike | Adams | 37 | 08/25/2010 | | | 81 |
| Elizabeth | | 21 | 08/05/2010 | | | 82 |
| Kevin | Cormia | 29 | 08/25/2010 | | | 83 |
| Emesto | Fri | 39 | 08/09/2010 | | | 84 |
| John | Garland | 27 | 08/25/2010 | | | 85 |

Figure 7-45: RunScriptDelete.php.

### PHP 删除记录脚本

- 如果有错误，`Allow User On` 停止。
- 如果有错误，`Set Error Capture` 阻塞 FileMaker 对话。
- `Allow [ On ]`
- `Set Error Capture [ On ]`
- 根据空的 `FirstName` 查找所有记录。
- `Find [ Specified Requests; FirstName = "" ]`
- 如果搜索期间没有未找到记录，确保显示所有记录。
- 删除找到的记录集。
- 最后，提交记录，以便网页更新最新的记录。
- `If Get(LastError) > 0`
- `Show All Records`
- `Delete All Records [ No dialog ]`
- `Show All Records`
- `Commit Records/Requests`

![](img/5a2c5fda68d42e5d65f51850276e49ec_189_0.png)

Figure 7-46: PHP 脚本.

## Lesson：运行脚本 — 发送邮件

**目标：**在本节中，你将学习如何使用参数运行脚本。脚本将使用内置的 FileMaker Send 向用户发送密码。

**难度：** 中等

**示例文件：** RunScriptSendMail.php

**页面导航：**

**FileMaker API 方法：**
- `PerformScriptCommand()`
- `execute()`

**代码：**
始终从包含数据库的连接开始。

```php
<?php
include ('../conn/dbaccess.php');
?>
```

在布局顶部开始一个默认消息，告诉用户在输入电子邮件之前确保提交按钮已设置并已点击。然后创建布局名称和变量。在脚本的第一次，我们将使用从 URL 获取的电子邮件地址向脚本传递参数。记住，电子邮件地址包含 `@` 符号，它会被 URL 编码为 `%40`。因此，我们需要使用 PHP 的 `ldecode` 方法将其转换回 `@` 符号。最后，将所有变量组合并执行脚本。

```php
<?php
$message = '点击提交按钮获取密码.' . '<p>';
if (isset($_GET['Submit']) && $_GET['Submit'] == 'Submit') {
$layout = 'Demo php';
$script = urldecode($_GET['email']);
$parameter = $fm->newPerformScriptCommand($layout, $script, $parameter);
$result = $request->execute();
}
```

错误处理并根据 FileMaker Server 的结果提供更新消息。如果没有找到记录，将抛出一个错误。因此，你可以更新消息让用户知道电子邮件不存在。否则，你可以让他们检查邮箱密码。

```php
if (FileMaker::isError($result)) {
$message = 'The email address you entered does not exist' . '<p>';
} else {
$message = 'Your password will be sent to your email address shortly.' . '<p>';
}
?>
```

最后，创建一个表单让用户输入电子邮件地址并提交以获取密码。

```html
<form action="RunScriptSendMail.php" method="get" name="Submit" id="Submit">
<?php echo $message; ?>
<input name="email" type="text" />
<p>
<input name="Submit" type="submit" value="Submit" />
</p>
</form>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_191_0.png)

点击提交按钮获取密码。
duel@formulations.org

![](img/5a2c5fda68d42e5d65f51850276e49ec_191_1.png)

Figure 7-47: RunScriptSendMail.php 页面。

![](img/5a2c5fda68d42e5d65f51850276e49ec_191_2.png)

点击提交按钮获取密码。
您的密码将很快发送到您的邮箱。

![](img/5a2c5fda68d42e5d65f51850276e49ec_191_3.png)

Figure 7-48: 找到了电子邮件地址，并通过脚本发送了密码。

### PHP 丢失密码脚本

发送自动电子邮件的能力是非常用的。你不仅可以使用此概念找回丢失的密码，还可以用它执行如从电子商务系统发送发票等操作。这种方法的棒之处在于，你不需要在 Web 服务器上运行特殊的 SMTP 服务器，也不需要在 Apache 或 IIS 中配置任何内容将电子邮件转发到你的 SMTP 服务器。只需使用 FileMaker 内置的 SMTP 功能，它运行得非常完美。

打开“允许用户中止”和“设置错误捕捉”，以确保脚本不会出现任何问题。

允许用户中止 [  ]
设置错误捕捉 [  ]

进入查找模式，并在网页上根据电子邮件地址参数查找该记录。要获取该参数，你可以使用 `Get(ScriptParameter)`，就像在 FileMaker Pro 的按钮上使用它一样。不要忘记，由于电子邮件地址中包含“@”通配符，你必须使用匹配字段（也称为精确匹配）操作符 `"="` 来进行地址搜索。

进入查找模式 [ ] 设置字段 [ php_demo::Email; "=" & Get(ScriptParameter) ]
执行查找 [ ]

错误捕获。如果查找该记录时没有错误，你可以使用内置的 `Send Mail` 函数发送密码。

> 你需要在你的网络中启用 SMTP 设置才能使其正常工作。

如果 [ Get(LastError) = 0 ]
发送邮件 [ 通过 SMTP 服务器; 到: Get(ScriptParameter); 主题: "找回密码";
内容: "您的密码是：" & php_demo::Password;"
验证类型: 无 ] [ 不显示对话框。 ]

如果没有找到任何记录，则退出脚本，FileMaker Server 将返回错误。这将允许你在 PHP 代码中捕获该错误，从而提醒用户其电子邮件地址不存在。

否则
退出脚本 [
结束如果

| 视图：按类别查看 | |
| --- | |
| 控制 | |
| 执行脚本 | |
| 执行脚本 | |
| 退出脚本 | |
| 停止脚本 | |
| 如果 | |
| 否则 | |
| 结束如果 | |
| 循环 | |
| 退出循环 | |
| 允许用户中止 | |
| 设置错误捕捉 | |
| 设置窗口 | |
| 导航 | |
| 转到记录/请求 | |
| 转到记录的页面 | |
| 转到门户记录行 | |
| 转到对象 | |
| 转到新字段 | |
| 转到上一个字段 | |
| 进入浏览模式 | |
| 进入查找模式 | |

- 如果用户丢失了密码，向他们发送电子邮件。从查找他们的记录开始。
- 如果我们设置系统以以 md5 哈希值存储密码，你需要：
- 设置错误捕捉 - 如果 FileMaker 返回错误，请确保对话框未
- 设置错误捕捉
- 使用由新的 `PerformScriptCommand(0)` 传递的参数获取记录
- 查找模式 []
- 设置字段 Email="=" & Get(ScriptParameter)
- 执行查找 []
- 如果找到记录，则通知用户他们的密码。如果他们必须
- 重要：你必须修改 SMTP 服务器设置以发送电子邮件
- 否则
- SMTP 服务器不显示对话框。到: Get(ScriptParameter); 主题 "找回密码"
- 否则 else，如果没有找到任何记录，FileMaker 会抛出错误，PHP 可以发送
- 退出脚本 [] 以具有完全访问权限运行脚本

图 7-49：找回密码脚本。

# 第 18 节：显示分页

**目标：** 在本节中，你将学习如何允许用户指定每页显示多少条记录，以及如何创建分页链接。显示短示例记录列表是一回事，而在生产服务器上为并发用户显示数千条记录是另一回事。显示的记录越多，对数据库和 Web 服务器的压力就越大。因此，你想限制从服务器返回并在每页显示的记录数量。

**难度：** 困难

**示例文件：** Pagination.php

![](img/5a2c5fda68d4e5d65f1850276e493.png)

**FileMaker API 方法：**
- `FindAll()`
- `addCriterion()`
- `setRange()`
- `execute()`
- `getMessage()`
- `getRecords()`
- `getFoundCount()`
- `getField()`

**代码：** 此示例结合了之前示例中的几种技术。总体目的是提供一个功能性示例。将 CSS 样式嵌入到 `<head>` 标签中以交替背景颜色。

```html
<head>
<style type="text/css">
.alt_row { background-color: #CCCCCC; }
</style>
<title>Pagination</title>
</head>
<body>
```

始终从包含数据库连接开始。

```php
<?php
include("../Conn/dbaccess.php");
?>
```

创建表单。PHP 的 `$_SERVER['SELF']` 是动态方法，返回当前文件的 URL 而不是硬编码。如果你更改了页面名称，代码将会失效。接下来，我们将包含隐藏值。第一页的值为 1，跳过值为 0。页面值用于显示分页链接（1, 2, 3, 4 等）。在进行新搜索后，你始终处于第一页。跳过值告诉 FileMaker 不要跳过记录，而是从结果集的第一条记录开始。同样，在进行新搜索后，你始终处于第一条记录。接下来，你可以包含用于 FirstName（姓名）的搜索字段。

```html
<form action="<?php $_SERVER['SELF']; ?>" method="get" name="search" id="search">
<input name="page" type="hidden" value="1" />
<input name="skip" type="hidden" value="0" />
姓名: <input name="FirstName" type="text">
<p>
```

```php
$_SERVER['SELF'] 返回当前文件的完整路径.
// manual/reserved_variables.php
```

为了使记录的显示符合用户习惯，我们将允许用户定义他们想要显示多少条记录。通过创建一个下拉菜单让用户选择每页显示的记录数是轻而易举的。我们建议每页显示 10、25、50 或 100 条记录，这比让服务器返回所有记录要好。我们将该数字赋值给 `max`。

```html
每页记录：
<select name="max">
<option value="10"></option>
<option value="25"></option>
<option value="50"></option>
<option value="100"></option>
</select>
<p>
```

现在我们可以创建分页链接的 PHP 代码。从定义 `skip` 变量开始。默认情况下，用户跳转到页面时，`skip` 值为 0，这会让数据库从结果的第一条记录开始。

```php
if(empty($_GET['skip']))
{
    $skip=0;
} else
{
    $skip=$_GET['skip'];
}
```

接下来，定义 `max` 变量用于每页显示的记录数。在用户选择其他值之前，默认显示 10 条。

```php
if(empty($_GET['max']))
{
    $max=10;
} else
{
    $max=$_GET['max'];
}
```

现在我们可以搜索记录。如果文本框中没有输入内容，我们将显示所有记录。否则，我们将搜索 FirstName 字段。

```php
if(empty($_GET['FirstName']))
{
    $FirstName = "";
    $request = $fm->newFindCommand('Demo php');
} else
{
    $FirstName = $_GET['FirstName'];
    $request = $fm->newFindCommand('Demo php');
    $request->addCriterion('FirstName', $FirstName);
}
```

在执行搜索之前，我们将告诉 FileMaker 跳过多少记录以及返回多少条 (max)。然后我们可以执行搜索。

```php
$request->setRange($skip, $max);
$result = $request->execute();
```

![](img/5a2c5fda68d4e5d65f1850276e493.png)

FileMaker 语法: setRange('Skip', 'Max')

```php
$request->setRange($skip, $max);
```

错误捕获。

```php
if (FileMaker::isError($result))
    echo "<p>" . $result->getMessage() . "</p>";
    exit;
```

将记录作为数组获取到 `$records` 变量中。

```php
$records = $result->getRecords();
```

为用户显示找到的数量。

```php
$found = $result->getFoundCount();
$total = $result->getTableRecordCount();
echo "<p>" . $found . " 共 " . $total . " 条总记录</p>";
```

```php
if(empty($_GET['FirstName']))
{
  $firstName='';
}else{
  $firstName=$_GET['FirstName'];
}
```

现在逻辑部分开始变得有点复杂了。你必须根据结果集中的记录数量以及每页最大显示记录数来确定需要显示多少页链接。首先使用取模函数（module）来计算总数除以每页最大记录数是否有余数。如果有余数，你需要为最后一页的剩余记录额外显示一个链接。否则，记录数可以正好整除以页数。变量 `$totalLinks` 在接下来的代码中构建实际的分页链接链接时非常重要。

```php
if($found % $max > 0)
  $totalLinks = intval($found / $max) + 1;
else
  $totalLinks=intval($found / $max);
```
