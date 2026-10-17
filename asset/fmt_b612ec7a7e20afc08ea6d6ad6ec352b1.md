
## 使用 `include()` 和 `require()` 包含文件

在 PHP 中，可以使用 `include()` 或 `require()` 函数将一个文件的内容包含到当前脚本中。代码将在调用这些函数的地方执行。执行后，代码将从 `include` 或 `require` 函数下方的行继续执行。这两个函数的区别在于，当使用 `include()` 时，如果发生错误，PHP 服务器将给出一个警告但会继续运行其他代码行。

在 `require()` 的情况下，如果包含的文件执行失败，程序将终止。

上面的示例假设使用 `include()` 或 `require()` 的 PHP 程序与被调用的文件在同一个文件夹中。如果不是，必须在函数的括号内提供文件的绝对路径或相对路径。

相对路径的示例是 `require('./footer.html');`。

绝对路径的示例是 `require('c:\users\desktop\header.php');`。

假设有一个如上所示的 `header.html` 文件。调用此头部的关联 PHP 程序如下：

```php
<?php

include('header.html');

print("This is my page.\n");

?>
```

输出如下。

![](img/d7e83bd680bb691d653bca3af472a71a_46_0.png)

这两个函数可以方便地减少重复工作。

## 使用 `date()` 函数格式化日期和时间

可以使用 `date()` 函数在 PHP 中显示日期和时间。该函数根据给它的参数返回基于格式的日期时间和信息。

可用选项如下：

- `Y` 表示 4 位数字格式的年份。
- `y` 表示 2 位数字格式的年份。
- `n` 表示一位或两位数字的月份，例如 4。
- `m` 表示两位数字的月份，如 05。
- `F` 表示月份的全称名称，例如 August。
- `M` 表示三字母格式的月份，例如 Aug。
- `j` 表示一位或两位数字的月份几号，例如 8。
- `d` 表示两位数字的月份几号，如 08。
- `l` 表示星期几，例如 Sunday。
- `D` 表示三字母格式的星期几，例如 Sun。
- `w` 表示单数字的星期几 - 例如星期日为 0。
- `z` 表示从 0 到 365 的一年中的第几天。
- `t` 表示每月的天数 - 31（对于 8 月）。
- `S` 表示 2 个字符的日期序数后缀 - rd。
- `g` 表示 12 小时制的一位或两位数字的小时，例如 6。
- `G` 表示 24 小时制的一位或两位数字的小时，例如 14。
- `H` 表示 12 小时制的两位数字的小时，如 08。
- `I` 表示 24 小时制的两位数字的小时，如 14。
- `i` 表示分钟，如 35。
- `s` 表示秒，如 15。
- `a` 表示 am 或 pm。
- `A` 表示 AM 或 PM。
- `U` 表示自 Unix 纪以秒数，例如 1048623008。

让我们来看这段 PHP 代码。

```php
<?php

$x = date('l,F,Y');

$y = date('h:i:s');

print "$x<p>$y</p>";

?>
```

输出将如下。

![](img/d7e83bd680bb691d653bca3af472a71a_48_0.png)

也可以 `print date(L,F,Y);` 来获取结果。

PHP 中的时间戳表示自 1970 年 1 月 1 日午夜以来经过的秒数。`time()` 函数返回当前时刻的时间戳。`mtime()` 函数可以返回特定日期的时间戳。

## 使用 Cookie 和 Session

`setcookie('cookiename','', );`

`setcookie('cookiename','', time()-60);`

这表示设置了一个过去的到期日期。

让我们来看这段代码。

```php
<?php

$Cookies=false;

if(isset($_POST['submit'])){

  setcookie('color',$_POST['color'],time()+60,'',0);

  $Cookies=true;

}

?>

<html

<head>

<title>Cookie Example</title></head>

<body>

<form action="php" method="post">

Yellow<input type="radio" name="color" value="Yellow"/>

Red<input type="radio" name="color" value="Red"/>

Blue<input type="radio" name="color" value="Blue"/>

<br>

<p>请完成反馈表并发送您的颜色偏好。</p>

<p>

<input type="submit" name="submit" value="color">

</form>

<?php

if($Cookies) {

  print "Your preference has been saved.";

}

?>

</body>

</html>
```

基本上，上述代码是处理 cookie 的 PHP 文件与其 HTML 页面的结合。唯一的添加是 `isset($_POST['submit'])` 这一条件和函数，PHP 允许我们将 cookie 的文件写在一个单独的文件中而不是两个不同的文件。`isset` 函数检查 HTML 表单中的提交按钮是否被点击。如果是，它将继续执行括号内的代码，即创建 cookie。大多数网站托管服务商都允许在单个 PHP 文件中混合 PHP 和 HTML。在 HTML 文件中使用 PHP 也是可能的。在注册或进行任何他们可能要求的配置之前，请咨询托管服务商。此建议适用于使用共享托管的用户。

session 提供了一种跨多个页面跟踪用户数据的方法。Cookie 将数据存储在客户端，而 session 将数据存储在服务器端。此外，session 具有以下特点：

1. 它更安全，因为数据仅存储在服务器上。
2. 它允许存储比 cookie 更多的信息。
3. 即使网站用户不接受 cookie，它们也可以正常工作。

session 的意思就像英文单词的含义（指一段时间，如一节课）。当 session 开始时，会创建一个随机的 session ID。这是对特定 session 存储数据的引用。

session ID 会作为 cookie 发送到网络浏览器，随后的 PHP 页面将使用此 cookie 获取 session ID 以访问其数据。

在 PHP 中启动或创建 session，我们从 `session_start()` 函数开始。该函数必须是使用 session 的每个 PHP 页面的第一行。

存储在浏览器上的 cookie 将有一个类似于 PHPSESSID 的名称，以及一个类似于 3bcc37dc87cb4b54d63f9a23b41f1 的值。

一旦 session 开始，就可以通过给 `$_SESSION` 数组赋值来记录数据。

`$_SESSION['color'] = 'Yellow';`

`$_SESSION['age'] = 35;`

数据被写入存储在服务器上的临时文件中。让我们来看下面的代码。

这段代码用于一个登录框。

```php
<?php

if(isset($_POST['submit'])){

  if ($_POST['username']=='admin' &&

  $_POST['password']=='admin') {

    session_start();

    $_SESSION['username']='admin';

    $_SESSION['login']=time();

    print("You are logged in");

    exit();

  }

}

?>

<html>

<head><title>Session Example</title></head>

<body>

<form action="session.php" method="post">

<p>

Username:<input type="text" name="username" size="20">

</p>

<p>

Password:<input type="text" name="password" size="20">

</p>

<p>

<input type="submit" name="submit" value="Submit">

</form>

</body>

</html>
```

登录框将如下所示。

![](img/d7e83bd680bb691d653bca3af472a71a_54_0.png)

这段代码从上一个 cookie 示例中看到的 `isset` 函数开始。它检查提交按钮是否被按下。

下一个语句检查密码和用户名是否必填。如果是，它将打印一条消息，`exit()` 函数将停止后续代码的执行。或者，如果有需要跳转的网页，可以使用 `header(Location:welcome.php);` 紧跟 `exit();`。请在上述代码中进行更改。

如果输入的用户名和密码错误，程序将显示一个空表单以便进一步尝试登录。

所以我们已经为登录页面启动了 session。为了访问 session 变量，我们首先创建一个 `welcome.php` 文件，这样用户登录后就会看到此页面。从此页面，我们将访问用户的登录时间。

欢迎页面的代码形式如下。

```php
<?php

session_start();

print("Welcome to my webpage!<p>");

print($_SESSION['username']);

print("<p>You have logged in since: </p>");

print(date('g:i',$_SESSION['login']));

print("<p><a href="logout.php">Logout</a></p>");

?>
```

这段代码从显示的注销页面开始。

![](img/d7e83bd680bb691d653bca3af472a71a_55_0.png)

欢迎页面的代码形式如下。

```php
print('<form action='function.php' method='post'><p>');

print('First Number:<input type='text' name='num1' size=5><p>');

print('Second Number:<input type='text' name='num2' size=5><p>');

print('<input type='submit' name='submit' value='ADD'>');

print('</form>');');
```

该函数之前被使用过。当编写带有表单的单文件 PHP 代码文件时，可以使用按钮函数来检查提交按钮是否被点击。

该函数有两个参数 `num1` 和 `num2`。名称可以是任何有意义的名称。函数将用户输入的变量 `num1` 和 `num2` 的值作为输入。在函数内部计算总和，然后使用 `isset` 函数中的 `print` 语句显示。

输出结果如下：

![](img/d7e83bd680bb691d653bca3af472a71a_59_0.png)

## 变量的作用域

变量有一个称为“作用域”（scope）的特性。这在定义变量时非常重要。作用域基于变量在代码中的位置。

变量的作用域被定义为它存在的范围。

在函数内部定义的变量仅在该函数内部存在。同样，函数外部的变量可以通过作为参数传递给函数（如最后两个示例所示）或使用 `global` 语句由函数引用。

让我们修改两个数相加的示例，以计算两个物品的价格以及在 5% 税率后的最终价格。

```php
<?php

$tax=5;

function sum($price1,$price2) {

  global $tax;

  $sum=$price1 + $price2;

  $taxrate=$tax/100+1;

  $sum=$sum * $taxrate;

```

```php
return $sum;

}

if (isset($_POST['submit'])) {

$sum=\$_POST['price1']+\$_POST['price2'];

print("<p>The total price of these two items is <b>$sum</b></p>");

}

print("<form action='function.php' method='post'><p>");

print("<p>First item price:<input type='text' name='price1' size=5></p>");

print("<p>Second item price:<input type='text' name='price2' size=5></p>");

print("<input type='submit' name='submit' value='Calculate'>");

print("</form>");

?>
```

该代码从用户处获取两个物品的价格并将其相加。在相加价格后，根据全局变量 `tax` 计算税率。

将税率乘以总和以显示最终价格。定义变量的一个重要部分是它的位置，因此也是有它的作用域。

## 第 6 章：文件与目录

理解数据库重要性的第一步是了解文件和目录。使用 PHP 以及大多数编程语言存储数据的方法有两种：它们它们是文件和目录，或者是数据库。

在 Web 托管环境中，特别是由主机提供商共享的托管，在文件方面可能会比较严格。

此类文件（如 `.csv`、`.txt` 文件）在网络主机上具有特定的权限设置。目录也将具有这些权限。

权限选项实际上是读、写和执行。除了这些选项外，还可以根据用户以三种不同的方式设置。所有者自动获得读和写权限，而其他人和其他组则仅被授予读取权限。

无论托管类型如何（Unix 或 Windows），出于安全考虑，托管服务在共享托管的情况下对允许访问文件和目录进行写入可能会限制。在创建基于文件和目录进行存储和检索的 PHP 程序之前，需要预先研究这一点。

正如前文所述，文件、目录和数据库基本上用于存储数据并允许它们被检索。

使用 PHP 写入文件可以使用以下函数：

- `fopen()`：以特定模式打开文件进行写入。
- `fwrite()`：将数据写入文件。
- `fclose()`：关闭文件连接。

`fopen()` 函数有多种打开文件的写入模式，它们是：

- `r`：仅用于读。读取从文件开头开始。
- `r+`：读均写。读写都从文件开头开始。
- `w`：仅用于写。如果文件不存在则将创建，并覆盖现有内容。
- `w+`：读均写。如果文件不存在则将创建，并在写入时覆盖现有内容。
- `a`：仅用于写。如果文件不存在则将创建，并将数据追加到文件末尾。
- `a+`：读均写。如果文件不存在则将创建，并将数据追加到文件末尾。
- `x`：仅用于写。如果文件不存在则将创建，但如果文件存在则不进行任何操作。
- `x+`：读均写。如果文件不存在则将创建，但如果文件存在则不进行任何操作。

如果文件与 PHP 文件不在同一位置，则应在代码中包含文件的路径。让我们看看以下代码，某些数据将被写入名为 `data.txt` 的文本文件。

```html
<html>

<body>

  <?php

  if (isset($_POST['submit'])) {

    if($fx=fopen('data.txt', 'a')) {

      $data=\$_POST['data'];

      fwrite($fx,$data);

      fclose($fx);

    }

  }

  ?>

  <form action='function.php' method='post'>

    <p>First item price:<input type='text' name='price1' size=5></p>

    <p>Second item price:<input type='text' name='price2' size=5></p>

    <input type='submit' name='submit' value='Calculate'>

  </form>

</body>

</html>
```

这是第一条语句。

这是第二条语句。

这是第三条语句。

在 PHP 中创建目录可以使用 `mkdir` 函数完成。该函数的格式如下：

`mkdir('directory_name', permissions);`

在基于 Windows 的服务器上，权限设置会被忽略。在创建目录或使用文件存储和检索数据之前，请注意 Web 托管商的策略。我强烈建议在专业环境中使用这些函数时应该使用数据库。

让我们编写一段代码，要求输入目录名和文件名，然后在该目录下的文件中写入一些文本。代码如下：

```html
<html>

<body>

<?php

if(isset($_POST['submit'])) {

$dirname=trim($_POST['dirname']);

mkdir(trim($dirname),0777);

$filename=trim($_POST['filename']);

$data=trim($_POST['data']);

if($fx = fopen('C:\Program Files (x86)\EasyPHP-Dev-Server\n14.1.VC3\data\localweb\scripts\$dirname\$filename','ab')) {

fwrite($fx,$data);

fclose($fx);

}

}

?>

<form action="file.php" method="post">

<p>
