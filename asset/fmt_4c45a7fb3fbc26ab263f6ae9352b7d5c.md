
URL（统一资源定位符）是万维网上的一种地址。每个网页都有自己的URL或地址。Web服务器使用该URL来查找网页并将其发送到浏览器。

URL的格式为

```
HTTP://servername:portnumber/path#target?string=string
```

以下是组成URL的各部分的说明：

`HTTP://servername:` 这告诉服务器该地址是一个网站，并给出网站所在计算机的名称。也可以指定其他传输类型，如`FTP`（文件传输协议），但这些与本书主题无关。如果省略URL的这一部分，Web服务器会假定该计算机就是输入URL的计算机。这一部分的有效选择是`HTTP://amazon.com`或`HTTP://localhost`。注意：`HTTP`不一定要大写。

`:portnumber:` Web服务器通过计算机上的特定端口与Internet交换信息。大多数情况下，Web服务器通过80端口进行通信。如果未指定端口号，则假定为80端口。在某些特殊情况下，Web服务器可能使用不同的端口号，此时必须指定端口号。使用不同端口号的最常见原因是在另一个端口上设置测试网站，该端口仅对开发人员和测试人员可用，不对客户开放。当网站准备好面向客户时，会通过80端口提供服务。

`path:` 这是文件的路径，遵循任何路径的规则。路径的根是网站主目录。如果路径指向目录而不是文件，Web服务器将搜索默认文件名，例如`default.html`或`index.html`。网站管理员设置默认文件名。路径 `/catalog/show.php` 表示主网站目录中一个名为`catalog`的目录和一个名为`show.php`的文件。路径`catalog/show.php`表示当前目录中一个名为`catalog`的目录。

### `#target`
HTML标签定义目标。URL的这一部分会在目标标签所在的位置显示网页。例如，如果标签 `<a name="target"></a>` 位于文件中间的某个位置，网页将显示在该标签处，而不是文件顶部。

### `?string=string`
问号允许将信息附加到URL末尾。使用`get`方法的表单中的信息以`fieldname=value`的格式在URL末尾传递。你可以将信息添加到URL末尾以将其传递到另一个页面。PHP会自动从URL中获取信息并将其放入内置数组中。你可以通过用与号（`&`）分隔每个字符串对来传递多个`string=string`对；例如，`?state=CA&city=home`。

## 必须在输出之前使用的语句

有些PHP语句只能在发送任何输出之前使用。本章中描述的所有`header`语句、`setcookie`语句和会话函数，都必须在发送任何输出之前使用。如果你在发送输出后使用了这些语句之一，可能会看到以下消息：

```
Cannot add header information - headers already sent
```

该消息还会提供文件名，并指出是哪一行发送了先前的输出。或者你可能根本看不到消息；新页面可能就是不出现。（你是否看到错误消息取决于PHP中设置的错误消息级别；详见第6章。）下面的语句会失败，因为`header`消息不是第一个输出：

```
<html>
<head><title>testing header</title></head>
<body>
<?php
  header("Location: http://company.com");
?>
</body>
</html>
```

在`header`语句之前发送了三行HTML代码。下面的语句将起作用，尽管它们意义不大：

```
<?php
  header("Location: http://company.com");
?>
<html>
<head><title>testing header</title></head>
<body>
</body>
</html>
```

下面的语句将失败：

```
<?php
  header("Location: http://company.com");
?>
<html>
<head><title>testing header</title></head>
<body>
</body>
</html>
```

这些语句失败的原因不易察觉，但如果仔细观察，你会注意到在PHP起始标签之前有一个空格。这个空格会输出到浏览器，虽然最终网页看起来是空的。因此，`header`语句会失败，因为在其之前有输出。这是一个常见且难以发现的错误。

尽管存在局限性，`header`函数仍然很有用。你可以在`header`函数之前有任意多的PHP语句，只要它们不发送输出即可。因此，以下语句可以正常工作：

```php
<?php
    if ($customer_age < 13)
    {
        header("Location: ToyCatalog.php");
    }
    else
    {
        header("Location: ElectronicsCatalog.php");
    }
?>
```

这些语句运行一个程序，如果客户年龄小于13岁则显示玩具目录，如果客户年龄为13岁或以上则显示电子产品目录。

## 从页面到页面传递信息

HTML页面彼此独立。当用户点击链接时，Web服务器向用户浏览器发送新页面，但Web服务器对之前的页面一无所知。对于静态HTML页面，这个过程工作正常。然而，许多动态应用程序需要在页面之间传递信息。例如，你可能想存储用户的姓名，并在另一个网页上以姓名引用该人。

动态Web应用程序通常包含多个页面，并期望用户查看多个不同的页面。从用户查看第一个页面开始到用户离开网站结束的这段时间是一个*会话*。通常你希望信息在整个会话期间可用。以下是在页面之间需要共享信息的会话示例：

- **限制对网站的访问：** 假设你的网站受限，用户需要用密码登录才能访问网站。你不希望用户在每个页面都必须登录。你只希望他们登录一次，然后能够查看他们想要的所有页面。你希望用户随身携带信息到每个页面，表明他们已登录并有权查看该页面。你希望用户在整个会话期间登录并保持登录状态。

- **根据浏览器提供网页：** 因为浏览器对某些HTML功能的解释不同，你可能希望为不同浏览器提供不同版本的网页。你希望在用户查看第一个页面时检查用户的浏览器，然后根据用户的浏览器类型和版本提供所有其他页面。

使用PHP，你可以通过以下任何方法在页面之间传递信息：

- **向URL添加信息：** 你可以将某些信息添加到新页面URL的末尾，PHP会将信息放入内置数组中，以便在新页面中使用。这种方法在你只需要传递少量信息时最为合适。

- **通过cookie存储信息：** 你可以在用户计算机上存储*cookie*——包含`variable=value`对的小量信息——。Cookie存储后，你可以从任何网页获取它。然而，用户可以拒绝接受cookie。因此，此方法仅在你确定用户已启用cookie的环境中才有效。

- **使用HTML表单传递信息：** 你可以使用`form`标签将信息传递给特定程序。当用户点击提交按钮时，表单中的信息会被发送到下一个程序。这种方法在你需要从用户收集信息时非常有用。

- **使用PHP会话函数：** 从PHP4开始，可用PHP函数设置用户会话并在服务器上存储会话信息；这些信息可以从任何网页访问。这种方法对于期望用户查看多个页面的会话非常有用。

## 向URL添加信息

将信息添加到URL是一种从一个页面到下一个页面传递信息的简单方法。把信息放在以下格式中：

```
variable=value
```

*变量*是一个变量名，但其中不要使用美元符号`$`。*值*是要存储在变量中的值。你可以在使用URL的任何地方添加`variable=value`对。你用问号`?`标记信息的开始。以下语句都是在URL中传递信息的有效方式：

```
<form action="nextpage.php?state=CA" method="POST">
```

```
<a href="nextpage.php?state=CA">go to next page</a>
```

```
header("Location: nextpage.php?state=CA");
```

你可以添加多个`variable=value`对，用与号`&`分隔，如下所示：

```
<form action="nextpage.php?state=CA&city=home" method="POST">
```

以下是你可能不想在URL中传递信息的两个原因：

- **安全性：** URL显示在浏览器的地址栏中，这意味着附加到URL的信息也会显示出来。如果信息需要保密，你就不希望它如此公开地显示。例如，如果你将密码从一个页面传递到下一个页面，你可能不希望在URL中传递它。此外，URL可以被用户书签保存。可能有原因不希望用户保存你添加到URL的信息。

- **字符串长度：** URL的长度有限制。限制因各种浏览器和浏览器版本而异，但总是有限制的。因此，如果你传递大量信息，可能没有足够的空间放在URL中。

向URL添加信息对于快速、简单的數據传输非常有用。例如，假设你想提供一个网页，让用户更新他们的电话号码。你希望表单按以下方式运行：

1. 当用户首次显示表单时，数据库中的电话号码会显示在表单中，以便用户可以看到数据库中当前存储的号码。
2. 当用户提交表单时，程序会检查电话号码，查看该字段是否为空或该字段的格式不可能是电话号码。
3. 如果电话号码检查正常，则该号码会存储在数据库中。
4. 如果电话号码为空或数据错误，程序会重新显示表单。然而，这次你不想显示数据库中的数据。相反，你想显示用户在表单字段中输入并提交的错误数据。

`displayPhone.php`程序在列表9-1中展示了如何使用URL来确定这是表单的首次显示还是后续显示。该程序显示用户登录名的电话号码，并允许用户更改电话号码。

### Listing 9-1: 显示电话号码表单的程序

```php
<?php
/* Program name: displayPhone.php
 * Description: Displays a phone number retrieved from the database and
 *              allows the user to change the phone number.
 */
?>
<html>
<head><title>Display phone number</title></head>
```

### Listing 9-1 *(继续)*

```php
<body>
<?php
    $host="localhost";
    $user="admin";
    $password="";
    $database="MemberDirectory";
    $loginName = "gsmith";  // passed from previous page
    $connection = mysql_connect($host,$user,$password)
        or die ("Couldn't connect to server");
    $db = mysql_select_db($database,$connection)
        or die ("Couldn't select database");

    if (@$_GET['first'] == "no")
    {
        $phone = $_POST['phone'];
        if (!ereg("^[0-9](-)?[0-9]{7,20}(([xx]|(ext)|(ex))?[ -]?[0-9]{1,7})?$",$phone)
            or $phone == "")
        {
            echo "<p align='center'>Phone number does not
                  appear to be valid.<br>";
        }
        else
        {
            $query = "UPDATE Member SET phone='$phone'
                         WHERE loginName='$loginName'";
            $result = mysql_query($query)
                or die ("Couldn't execute query.");
            echo "Phone number has been updated.<br>";
            exit();
        }
    }
    else
    {
        $query = "SELECT phone FROM Member WHERE loginName='$loginName'";
        $result = mysql_query($query)
            or die ("Couldn't execute query.");
        $row = mysql_fetch_array($result);
        extract($row);
    }

    /* Display user phone in a form */
    echo "<br><p align='center'>
        <font size='+1'><b>Please check the phone number
              below and correct it if necessary.</b></font>
        <hr>
        <form action='displayPhone.php?first=no' method='POST'>
          <div align='center'>
          <table width='50%' border='0' cellspacing='0' cellpadding='2'>
          <tr><td align='right'><b>$loginName<br></td>
            <td align='center'><input type='text' name='phone'
                 size='20' maxlength='20' value='$phone' ></td>
          </tr>
```

```
<tr><td></td><td align='center'>
    <br><input type='submit' value='Submit phone number'></td>
</tr>
</table>
</form>";
?>
</body></html>
```

注意此程序的以下关键点：

- **同一个程序显示并处理表单。** 此程序的名称是`displayPhone.php`。请注意`form`标签包含`action=displayPhone.php`，这意味着当用户点击提交按钮时，同一个程序会再次运行。

- **信息被添加到URL中。** `form`标签包含`action=displayPhone.php?first=no`。当用户点击提交按钮且`displayPhone.php`第二次运行时，会传递一个变量`$first`，其值为"no"。

- **在程序开始时检查内置`$_GET`数组中为`first`传递的值。** 这是为了判断程序是否是第一次运行。

- **如果`$_GET[first]`等于"no"，则检查电话号码。**

  - `$_GET[first]`只有在表单被提交时才等于no。
  - `$_GET[first]`如果这是程序的第一次运行，则不等于no。
  - 如果电话号码正确，则将其存储在数据库中，程序结束。
  - 如果电话号码不正确，则打印错误消息。

- **如果`$_GET[first]`不等于"no"，则从数据库检索电话号码。** 换句话说，如果`$_GET[first]`不等于no，则是程序的第一次运行。程序应从数据库获取电话号码。

- **如果程序执行到显示表单的语句，则显示表单。** 如果这不是程序的第一次运行，并且提交了电话号码且电话号码正确，则电话号码会存储在数据库中，程序停止。*它永远不会执行到显示表单的语句。* 在所有其他情况下，都会显示表单。

程序中清单9-1显示的表单在图9-1中显示。这显示了Web页面第一次显示时的样子。请注意，浏览器地址字段中的URL没有任何附加信息。

图9-2显示了当用户在图9-1中的表单中输入无意义的电话号码时的结果。请注意，浏览器地址字段中的URL现在在其末尾添加了`?first=no`。

Figure 9-1:

用于更新电话号码的HTML表单。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_286_0.png)

Figure 9-2:

当用户提交无意义的电话号码时HTML表单。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_286_1.png)

## 通过Cookie存储信息

你可以将信息存储为Cookie。Cookie是包含`variable=value`对的小量信息，类似于可以添加到URL中的对。用户的浏览器将Cookie存储在用户的计算机上。然后你的应用程序可以从任何Web页面获取Cookie。为什么这些被称为Cookie是生活中的一大谜团。也许它们被称为Cookie是因为乍一看似乎是件美妙的事情，但在仔细检查后，你意识到它们对你来说并不那么好。对于某些人在某些情况下，Cookie完全没有帮助。
