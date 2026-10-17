
<td width="1" bgcolor="gray"></td>

<td width="67%">

<p><font size="+1"><b>Not a member yet?</b></font>

Get discounts, a newsletter, advance notice of

new pets, much more. Fill in the information

below and join. It's easy and free! </b>

<!-- form for new member to fill in -->

<form action="Login.php?do=new" method="POST">

<p>

<table border="0" width="100%">

<?php

if (isset($message_new)) #55
    echo "<tr><td colspan='2'><b>$message_new</b>
        </td></tr>";
?>

<tr><td align="right"><b>Member ID</b></td>
    <td><input type="text" name="newname"
        value="<?php echo @$newname ?>"
        size="20" maxlength="20"></td></tr>

<tr><td align="right"><b>Password</b></td>
    <td><input type="password" name="newpass"
        value="<?php echo @$newpass ?>"
        size="10" maxlength="8"></td></tr>

<tr><td align="right"><b>First Name</b></td>
    <td><input type="text" name="firstName"
        value="<?php echo @$firstName ?>"
        size="40" maxlength="40"></td></tr>

<tr><td align="right"><b>Last Name</b></td>
    <td><input type="text" name="lastName"
        value="<?php echo @$lastName ?>"
        size="40" maxlength="40"></td></tr>

<tr><td align="right"><b>Street</b></td>
    <td><input type="text" name="street"
        value="<?php echo @$street ?>"
        size="55" maxlength="50"></td></tr>

<tr><td align="right"><b>City</b></td>
    <td><input type="text" name="city"
        value="<?php echo @$city ?>"
        size="40" maxlength="40"></td></tr>

<tr><td align="right"><b>State</b></td>
    <td><select name="state">
<?php

$stateName=getStateName(); #86
$stateCode=getStateCode(); #87
for ($n=1;$n<=50;$n++)
{
    $state=$stateName[$n];
    $scode=$stateCode[$n];
    echo "<option value=\"$scode\"";
    if ($scode=="AL")
        echo " selected";
    echo ">$state\n";
}

?>
    </select>

    &nbsp;&nbsp;&nbsp;&nbsp;<b>Zip</b>
    <input type="text" name="zip"
        value="<?php echo @$zip ?>"
        size="10" maxlength="10">

</td></tr>

<tr><td align=right><b>Phone</b></td>
    <td><input type="text" name="phone"
        value="<?php echo @$phone ?>"
        size="15" maxlength="20">
    &nbsp;&nbsp;&nbsp;<b>Fax</b>
    <input type="text" name="fax"
        value="<?php echo @$fax ?>"
        size="15" maxlength="20"></td></tr>

<tr><td align=right><b>Email Address</b></td>
    <td><input type="text" name="email"
        value="<?php echo @$email ?>"
        size="55" maxlength="67"></td></tr>

<tr><td>&nbsp;</td>
    <td align="center">
        <input type="submit"
            value="Become a Member"></td>
</tr>

</table>

</form>

</td>

</tr>

<tr><td colspan="3" bgcolor="gray">&nbsp;</td></tr>

</table>

<div align="center"><font size="-1">
All comments and suggestions are appreciated. Please
send comments to <a href="mailto:webmaster@petstore.com">
webmaster@petstore.com</a> </font></div>

</body></html>

```

请注意关于 `login_form` 的以下几点：

- 大多数语句都是 HTML，其中不时夹杂着一些小的 PHP 部分。
- 从第 23 行和第 51 行开始的两个表单将 action 设置为同一个程序，但会在 URL 中添加不同的字符串——`do=login` 或 `do=new`。
- 错误消息是通过使用小的 PHP 部分在登录页面上显示的。每个表单都有其部分，并且消息对两个表单有不同的名称：`$message` 和 `$message_new`。第 26 行测试变量 `$message`。如果它有值，则显示消息，如果没有值则不显示。如果表单中没有错误，则从未设置该消息，也不会显示消息。第 55 行的类似语句显示新成员表单的错误消息。
- 为客户选择州提供了一个选择下拉列表（从第 84 行开始），以防止客户输入错误。请注意，第 86 行和第 87 行调用了函数。这些函数不是 PHP 函数；它们是我的函数。这些函数在第 8 行被包含到程序中。函数从州名列表和两位州代码列表创建数组。通过使用函数，您无需在程序中包含 50 个州的两个列表。这些函数可以重复用于许多程序。`functions12.inc` 文件包含以下两个函数：

```php
<?php

function getStateCode()
{
    $stateCode = array(1=> "AL",
        "AK",
        "AZ",
        ...
        "WY" );
    return $stateCode;
}

function getStateName()
{
    $stateName = array(1=> "Alabama",
        "Alaska",
        "Arizona",
        ...
        "Wyoming" );
    return $stateName;
}

?>
```

然后 `for` 循环使用这两个州数组为选择列表创建 50 个选项。

运行 `Login.php` 后，如果用户登录成功，则显示仅限会员部分的第一个页面。如果用户成功获得新用户账户，则运行 `New_member.php` 程序。

## 编写 New_member

新成员欢迎页面以姓名向新成员问候并提供有关其账户的信息。然后成员可以选择进入仅限会员部分或返回主页面。列表 12-4 显示了显示新成员所见页面的程序。

### 列表 12-4：欢迎新成员的程序

```php
<?php

/* Program: New_member.php
 * Desc:     Displays the new member welcome page. Greets
 *           member by name and gives user choice to enter
 *           restricted section or go back to main page.
 */

session_start(); # 7
if (@$_SESSION['auth'] != "yes") # 9
{
    header("Location: Login.php");
    exit();
}

include("dogs.inc"); #14
$connection = mysql_connect($host,$user,$password)
        or die("Couldn't connect to server."); #16
$db = mysql_select_db($database, $connection)
        or die("Couldn't select database."); #18
$sql = "SELECT firstName,lastName FROM Member
             WHERE loginName='{$_SESSION['logname']}'";
$result = mysql_query($sql)
        or die("Couldn't execute query 1.");
$row = mysql_fetch_array($result,MYSQL_ASSOC);
extract($row);

```

```

echo "<html>
<head><title>欢迎新会员</title></head>
<body>
<h2 align='center' style='margin-top: .7in'>
欢迎 $firstName $lastName</h2>\n"; #29
?>
```
<p>您的新会员账户可让您进入我们网站的“会员专区”。您会找到特别折扣和优惠、一个庞大的动物知识与故事数据库、专家建议、新宠物出售的预先通知、一个供您与其他会员交流的留言板，以及更多内容。
<p>您的新会员ID和密码已通过电子邮件发送给您。请妥善保管以备后用。<br>
<div align="center">
<p style="margin-top: .5in"><b>欢迎您的加入！</b>
<form action="Member_page.php" method="POST">
<input type="submit"
value="进入会员专区">
</form>
<form action="PetShopFrontMembers.php" method="POST">
<input type="submit" value="返回宠物商店主页">
</form>
</div>
</body></html>
```

关于 `New_member.php`，请注意以下几点：

- 第7行启动了一个会话。这使得 `Login.php` 中存储的会话变量在该程序中可用。
- 程序从第9行开始检查客户是否已登录。当客户成功登录或创建新账户时，`$auth` 在 `Login.php` 中被设置为 `yes`，并存储在 `$_SESSION` 数组中。如果 `$auth` 不等于 `yes`，则客户未登录。如果客户在未先运行 `Login.php` 程序的情况下尝试运行 `New_member.php` 程序，`$_SESSION[auth]` 将不等于 `yes`，用户将被发送到登录页面。
- 程序从第15行的数据库连接语句开始，从数据库中获取客户的名字和姓氏。在第19/20行，通过使用 `$_SESSION[logname]` 搜索会员信息来创建查询。包含会员ID的会话变量 `logname` 是在登录程序中设置的。
- PHP部分在第30行结束。程序的其余部分是HTML。
- 程序使用两个不同的表单来提供两个不同的提交按钮。第41行和第45行的表单语句启动不同的程序。

接下来由客户决定。如果客户点击返回主页的按钮，则运行 `PetShopFront.php` 程序。如果客户点击“会员专区”提交按钮，则显示会员专区的第一页。

## 编写会员专区

会员专区中的网页与其他网页没有什么不同。您只需将其限制为已登录的会员。为此，您需要在每个页面的顶部启动一个会话，并检查他们是否已登录。每个程序顶部的语句如下：

```
session_start();
if (@$_SESSION['auth'] != "yes")
{
    header("Location: Login.php");
    exit();
}
```

当 `session_start` 执行时，PHP 会检查是否已有会话存在。如果存在，它会设置会话变量。其中一个会话变量是 `$auth`。当用户登录时，`$_SESSION[auth]` 被设置为 `yes`。如果 `$_SESSION[auth]` 不等于 `yes`，则用户未登录，程序会将用户带到登录页面。

## 为增长做规划

一个应用程序的原始计划通常包含用户可能希望它做的所有精彩功能。但实际上，尽快让用户使用该应用程序通常更为重要。因此，应用程序通常以计划功能的一个子集上线，之后再添加更多功能。这就是为什么在编写应用程序时要考虑未来增长的原因。

看看本章中的登录应用程序，我相信您能看到许多可以添加的功能。以下是一些可能的想法：

- **通过电子邮件发送遗忘的密码。** 用户经常忘记密码。许多登录应用程序都有一个链接，用户可以点击该链接，让系统将密码通过电子邮件发送给他们。
- **修改密码。** 会员可能想要更改密码。应用程序可以提供用于修改密码的表单。
- **更新信息。** 会员可能搬家或更改电话号码或电子邮件地址。应用程序可以提供一种方式，让会员自行更改其信息。
- **创建会员列表。** 您可能希望以格式良好的方式输出数据库中所有会员的列表。这可能不是您想对其他会员开放的功能，而只是供您自己使用。但在某些情况下，您可能希望向所有会员提供该列表。

您可以轻松地将这些功能中的任何一个添加到应用程序中。例如，您可以在登录表单中添加一个“*忘记密码*”按钮，将密码发送到数据库中的电子邮件地址。该按钮可以运行带有密码发送部分的登录程序，或者运行另一个发送密码的程序。同样，您也可以添加用于修改密码或更新客户信息的按钮。您不必等待应用程序具备所有附加功能后才让客户使用它。您可以一步一步地编写。

## 第五部分

## “十”部分

### 第五波

作者：Rich Tennant

![](img/d82df0828cfbc6d6be1e9a991861f3b7_381_0.png)

> “你是想让我给公司打电话，让他们再寄一份数据库软件系统的评论副本，还是你已经知道要写什么了？”

### 本部分内容……

本部分各章包含基于我经验的心得、提示和警告。或许它们能成为您成长为一名自信的Web开发者的捷径。我真诚地希望如此。

### 第13章

## 你可能想用 PHP 函数做的十件事

### 本章内容

- 了解许多有用的函数
- 理解函数能做什么

PHP 最强的方面之一是其众多内置函数。在本章中，我列出了我最常使用的 PHP 函数。有些我在本书其他地方描述过，有些只是顺带提及，有些则完全没有提到。这些绝不是全部函数。PHP 语言中有数百个函数。有关所有函数的完整列表，请参阅 www.php.net 上的 PHP 文档。

### 与 MySQL 通信

PHP 有许多专门用于与 MySQL 交互的函数。我在本书中详细描述了以下 MySQL 函数，尤其是在第8章中：

```
mysql_connect();    mysql_select_db();    mysql_fetch_array()
mysql_close();        mysql_num_rows();     mysql_query()
```
