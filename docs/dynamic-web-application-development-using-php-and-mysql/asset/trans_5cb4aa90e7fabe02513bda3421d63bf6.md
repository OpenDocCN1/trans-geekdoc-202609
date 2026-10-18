

</p>
<p><input type='submit' name='submit'/></p>
</form>

<?php
// File: example20-16.php
if (isset($_POST["submit"])) {
    $strMessage = $_POST["strMessage"];
    echo "<p>" . htmlentities("Your message is " . $strMessage) . ".</p>";
}
echo "<p>This is some text further down the web page.</p>";
?>

上述脚本的输出如图20.8所示。

> **注意** 如果你不编写代码来防止 HTML 注入，并且你的应用程序允许此类用户输入，那么这种情况迟早会发生，无论是有意还是无意。

## 转义字符与 SQL 注入

另一种形式的字符注入可能更阴险，这就是所谓的 SQL 注入。为了解释 SQL 注入，我们需要创建一个数据库并填入一些数据。我们将创建一个名为 'users' 的数据库，其中只有一个名为 'users' 的表。表的字段和字段类型如表20.2所示。

## 图20.8 已阻止 HTML 注入

![](img/b2471264f405d17994ef173e4b9cec92_624_0.png)

## **表20.2** users 表：字段和类型

| 字段 | 类型 | 其他 |
|---|---|---|
| Id | Int | 自动递增，主键 |
| Username | Varchar (30) | |
| Password | Varchar (30) | |

## **表20.3** users 表：数据

| Id | Username | Password |
|---|---|---|
| 1 | Alan | Smith |
| 2 | David | Regan |

并假设我们用表20.3所示的数据填充该表。

现在，我们可以创建一段简单的脚本，以便访问该数据库：

```php
<?php
// File: example20-17.php

$strUsername = 'David';
$strPassword = 'Regan';

$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("users", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );
$dbRecords = mysql_query("SELECT * FROM users WHERE username = '$strUsername'");

$arrRecords = mysql_fetch_array($dbRecords);
if ($strPassword != $arrRecords["password"])
    echo "<p>Invalid Password/Username</p>";
else
    echo "<p>Password and Username match!</p>";
?>
```

该脚本是一个基本的用户名和密码验证脚本。我们首先有一个用户名和密码，可以假设这些由用户输入（但为了简单起见，我们已在脚本中进行了硬编码）。然后我们检查数据库中是否存在该用户名，如果不存在则报告错误；最后检查数据库中存储的密码是否与随用户名一起提供的密码匹配。你会发现脚本可以正常工作。

但是，如果将“David”的用户名值替换为以下内容会怎样：

```text
"' OR '1 = 1";
```

需要说明的是，上述 $strUsername 的值由以下字符组成：

- 双引号
- 单引号
- 空格字符
- OR
- 空格字符
- 单引号
- 1
- =
- 1
- 双引号
- 分号

$strPassword 被设置为空：

```
$strPassword = '';
```

脚本现在变成这样：

```php
<?php
// File: example20-18.php

$strUsername = "'" OR '1=1";
$strPassword = '';
$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("users", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );

$dbRecords = mysql_query("SELECT * FROM users WHERE username = '$strUsername' ");

$arrRecords = mysql_fetch_array($dbRecords);
echo $arrRecords["Password"];
if ($strPassword != $arrRecords["Password"])
    echo "<p>Invalid Password/Username</p>";
else
    echo "<p>Password and Username match!</p>";
?>
```

问题是，当脚本运行时，它返回了字符串“密码和用户名匹配！”，而我们的安全性因 SQL 语句被改变而遭到破坏。上述操作之所以有效，是因为展开 $strUsername 的内容后，SQL 语句现在为：

```
SELECT * FROM users WHERE username='' OR '1=1'
```

这实际上不会返回任何记录，而且由于密码被设置为空，比较密码的 if 语句会求值为真。因此，脚本会认为用户名和密码是匹配的。

通过使用 mysql_escape_string() 函数可以防止 SQL 注入：

```
mysql_escape_string ( string unescaped_string )
```

该函数会转义 SQL 字符串中的引号字符，因此在我们的示例中，查询会变成这样：

```
SELECT * FROM users WHERE username='\' OR \'1=1'
```

转义后的字符消除了引号被 SQL 解析器错误解释的危险。此外，重要的是要确保你在代码中检查查询是否从数据库返回了任何记录。如果你期望返回一条记录，但实际没有返回任何记录，那就可能存在潜在问题。例如，我们可以使用 mysql_num_rows() 函数来实现这一点：

```
if (mysql_num_rows($dbRecords) != 1)
    echo "<p>Username not found!</p>";
```

修改后的脚本如下，它消除了 SQL 注入绕过我们的登录安全验证的可能性：

```php
<?php
// File: example20-19.php

$strUsername = '' OR '1='1';
$strPassword = '';

$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("users", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );

$strUsername = mysql_real_escape_string($strUsername);

$dbRecords = mysql_query("SELECT * FROM users WHERE username = '$strUsername' ");

$arrRecords = mysql_fetch_array($dbRecords);

if (mysql_num_rows($dbRecords) != 1)
    echo "<p>Username not found!</p>";
else {
    if ($strPassword != $arrRecords["Password"])
        echo "<p>Invalid Password/Username</p>";
    else
        echo "<p>Password and Username match!</p>";
}
?>
```

## 20.4 用户认证与密码

### 检查来源页面

我们在前面的章节中简要介绍了检查来源页面的概念，这里再回顾一下。请看下面的脚本：

```php
<?php
// File: example20-20.php
```

```
if(isset($_POST["submit"])) {
    $strUserPass = array ( "john" => "red",
                           "simon" => "green",
                           "liz" => "blue",
                           "david" => "yellow");

    if ($strUserPass[$_POST["strUsername"]] == $_POST["strPassword"])
        header("location: example20-21.php");

    echo "<h1>Incorrect Username and/or password!</h1>";
}
?>

<form method="post" action="">
<p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/></p>
<p>
<label for="strPassword">Password: </label>
<input type="password" name="strPassword" id="strPassword"/></p>
<p><input type="submit" name="submit" /></p>
</form>
```

上面的脚本输出一个由三个元素组成的表单：一个文本字段、一个密码字段和一个提交按钮。用户输入用户名和密码后，系统会将这些与一个简单的用户名/密码数组进行核对。如果找到匹配项，用户就会被重定向到一个新页面，如下所示：

```php
<?php
// File: example20-21.php

if ($_SERVER["HTTP_REFERER"])
    if ($_SERVER["HTTP_REFERER"] != "http://localhost/Book/example20-20.php")
        header("location: example20-20.php");
?>

<h1>Well, done you are correctly logged in!</h1>
```

显然，我们不希望用户或某个恶意者通过在浏览器中直接输入第二个页面的地址就能跳转到该页面，从而完全绕过我们设置的安全措施，例如：

http://localhost/example20-21.php

为了防止这种情况，我们在第二个脚本的顶部加入了以下代码：

```
if ($_SERVER["HTTP_REFERER"])
    if ($_SERVER["HTTP_REFERER"] != "http://localhost/Book/example20-20.php")
        header("location: example20-20.php");
```

这些代码检查保存在关联数组 $_SERVER 中的“HTTP_REFERER”值。这里，我们需要检查所存储的值是否等于：

http://localhost/Book/example20-20.php

该值表示启动当前页面的来源页面地址。如果用户正确填写了用户名和密码登录表单，那么该值就会被设置。
