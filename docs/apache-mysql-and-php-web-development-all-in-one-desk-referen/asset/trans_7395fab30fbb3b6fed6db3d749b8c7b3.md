
Listing 4-3 中的 JavaScript 不检查电子邮件地址是否为真实地址。代码只是确保地址格式正确，例如 me@domain.com。通常，如果要验证电子邮件地址，会使用 PHP 程序向该地址发送电子邮件并等待响应。如果收到响应，即可确定电子邮件地址有效。我将在 Book VI, 第 7 章中向你展示如何发送验证电子邮件。

## 列表 4-3: 使用 JavaScript 防止基本输入问题的文件

```
<html><head><title>New Customer Form</title>
<script language="JavaScript">
function IsNotNull(){
if (document.form1.name == null ||
document.form1.email == null ||
document.form1.remail == null) {
alert("Please fill out all the fields.");
return false;
}
if (document.form1.name.value.length == 0 ||
document.form1.email.value.length == 0 ||
document.form1.remail.value.length == 0) {
alert("Please fill out all the fields.");
return false;
}
return true;
}
function IsValidEmail(){
var email = document.form1.email.value;
var myreg
= /^[\@\s]+@([-a-z0-9]+\.)+[a-z]{2,}$/
if (myreg.test(email)) {
return true;
}
else {
alert("The email address is invalid.");
return false;
}
}
function CheckForMatch() {
if (document.form1.email.value !=
document.form1.remail.value) {
alert("The email addresses do not match.\n"+
"Please re-check them. Thanks!");
return false;
}
return true;
}
function checkfields() {
  if (IsNotNull() == false) {
    return false;
  }
  if (IsValidEmail() == false) {
    return false;
  }
  if (CheckForMatch() == false) {
    return false;
  }
  return true;
}
</script></head>
<body bgcolor="#FFFFFF" text="#000000">
Welcome new customer! We're so glad you
headed our way.<p>
Our motto is: <i>If we can't sell your stuff,
then you're stuck with it!</i></p>
Please fill out this-here form to getcha
started:<p>
<form name="form1" method="get"
action="newcustomer.php"
onSubmit='return checkfields();'>
Name: <input type="text" name="name"><p>
Email address:
<input type="text" name="email"><p>
Retype email address:
<input type="text" name="remail"><p>
<input type="submit" name="Submit"
value="This is me, I swear!">
</form>
</body></html>
```

查看 HTML 主体中的 form 标签。我使用了 JavaScript 事件 onSubmit，并在随后的代码中调用我自己的 checkfields 函数。在文件中更早的部分，你可以看到 checkfields 函数，它会调用以下函数：

- IsNotNull 确保用户在所有字段中都输入了内容
- IsValidEmail 确保用户输入了正确的电子邮件地址
- CheckForMatch 确保用户在两个电子邮件字段中输入了相同的内容

在 IsNotNull 函数中，我涵盖了两种情况。第一种是字段本身为 null，第二种是字段不包含任何字符。之所以同时使用这两种情况，是为了覆盖浏览器不兼容的场景。

IsValidEmail 函数有点复杂。该函数会将电子邮件地址与正则表达式进行测试。互联网上有很多页面展示了用于测试正确电子邮件地址的各种正则表达式。我参考了其中几个，并在此基础上构建了自己的正则表达式。

![](img/3f967ab8a8fddc723173059f56621648_576_0.png)

我在列表 4-3 中使用的正则表达式并不完美；例如，如果用户输入 me@something.xyz，测试会通过，尽管这不是一个真实的电子邮件地址。

最后，CheckForMatch 只是确保两个电子邮件地址匹配，以期防止拼写错误。

## 使用 PHP 验证数据

当你将数据提交给 PHP 文件进行处理时，会希望检查各种问题，例如用户是否已存在。

列表 4-4 显示了列表 4-2 的修改版本，添加了一个测试以确保名称或电子邮件不存在。（我也缩短了一些消息以节省图书空间。我希望你物有所值。）

## 关于索引和速度

为了保持本章中示例的简单性，我选择不根据名称和电子邮件字段为客户表创建索引。你仍然可以根据这两个字段搜索表；但是，如果为这两个字段建立了索引，搜索速度会更慢。折衷在于，如果你确实为这两个字段创建了索引，MySQL 每次添加用户时都必须更新索引。

在决定是否添加索引时，请比较添加用户的次数和查找用户的次数。如果用户在添加自己后偶尔会回来，显然你会比创建用户更频繁地查找用户。因此，你希望查找速度更快，即使这意味着添加用户的过程会变慢。因此，为用户名和电子邮件字段添加索引符合你的最佳利益。我在本书中不向你展示如何执行此操作的唯一原因是，我更喜欢保持示例简单。然而，对于你的实际在线系统，请权衡利弊并进行比较以做出决定。

![](img/3f967ab8a8fddc723173059f56621648_577_0.png)

要使用列表 4-4 中的代码（我将其命名为 newcust2.php），你需要更新 newcustomer.html 以访问 newcust2.php，而不是旧的 newcustomer.php 文件。为此，请更改以下行：

```
action="newcustomer.php"
```

改为：

```
action="newcust2.php"
```

（然后在打开 newcustomer.html 时单击浏览器的重新加载按钮以查看更改）。

## 列表 4-4: 确保用户名或电子邮件地址在表中不存在的文件

```
<html><title>Simple Insert...</title>
<body>
<?php
$name = $_GET["name"];
$email = $_GET["email"];
$now = date("Y-m-d");
mysql_connect("localhost", "phpuser",
    "phppass");
$result = mysql_query(
    "select * from phpbase.customer
    where name = '$name'
    or email = '$email'"); // Watch the quotes!
$found = false;
if ($result) {
    if (mysql_num_rows($result) > 0) {
        print "It looks like you're already signed
        up with us!";
        $found = true;
    }
}
if ($found == false) {
    $result = mysql_query(
        "insert into phpbase.customer
        (name, email, signup, last_access) values
        ('$name', '$email', '$now', '$now')");
    if ($result) {
        print "<h1>Thank you!</h1>";
    }
    else {
        print "Something went awry
        with the awful SQL!";
    }
}
mysql_close();
?>
</body></html>
```

## 在网页上显示 MySQL 数据

得益于 SQL 的强大功能，你可以执行复杂查询，从表中检索出色的数据，并在网页上显示结果。在本节中，我假设你要么使用了前一部分“使用 PHP 和表单输入数据”中的表单将一些数据输入到表中，要么使用了 `load data` 命令来导入数据。首先，我假设你已按照本章开头所述设置了 `category` 和 `status` 表。表 4-1 显示了 `customer` 表的一些数据。

### 表 4-1 客户表的示例数据

| ID | 姓名 | 电子邮件 | 注册日期 | 上次访问 |
|---|---|---|---|---|
| 1 | Hank Harshigan | hank@harshigan.com | 2004-06-01 | 2004-06-11 |
| 2 | Floyd Flabbergaps | floyd@flabbergaps.com | 2004-06-02 | 2004-06-02 |
| 3 | Erica Exagabule | erica@exagabule.com | 2004-06-03 | 2004-06-05 |
| 4 | Jessica Jamboliable | jessica@jamboliable.com | 2004-06-04 | 2004-06-04 |
| 5 | Julia Julianopolis | julia@julianopolis.com | 2004-06-05 | 2004-06-11 |

要将这些数据放入表中，可以使用本章前面列表 4-3 和 4-4 中的表单。

获取一些示例广告有点棘手，因为 `ad` 表有很多列。在 Book VI, 第 5 章中，我将带你完成创建用于输入广告的表单的过程。目前，请输入以下两个 SQL 语句来输入一些广告（我建议将这些语句保存到名为 `ads.sql` 的文件中，然后运行 `mysql -u root -p < ads.sql`）：

```
insert into phpbase.ad values
(1, 3, 'PHP & MySQL For Dummies',
'Great new book! Must sell!!!',
'This is a great book that I purchased while '
'in college and now I don’t need it because '
'I know everything in it.',
15700, '2004-08-01', 2, 4);
```

```
insert into phpbase.ad values
(2, 5, '386 Computer',
'Fantastic computer! Runs great!',
'This was my very first computer ';
```

