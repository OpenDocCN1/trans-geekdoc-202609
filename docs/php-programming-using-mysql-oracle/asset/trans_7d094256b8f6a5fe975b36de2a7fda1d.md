

进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

```
<?php$programming =array('C++','Java');$hardware = array('Networking','Security');$books = array (  'Software' =>$programming, 'Hardware' => $hardware);print "The second book in programming is {$books\['Software'\]\[1\]}<p>";print "The first book in networking is{$books\['Hardware'\]\[0\]}";print\_r($books);print"<p>";var\_dump($books);?>
```

输出如下。

![](images/00032.jpeg)

# 第5章 Web应用程序组件

PHP 主题至少需要 HTML 知识。除此之外，对层叠样式表（CSS）、Java 脚本和结构化查询语言的了解可以极大地增强创建动态、美观网页的能力。

本书不会详细讲解 CSS 或 Java Script 的开发。但是，在本书数据库部分会给出 SQL 的基本背景知识。

本章将介绍构建 Web 应用程序的一些重要组件。

PHP 程序中可以使用外部文件。例如，为页面创建页眉或页脚。为此首先创建 `header.html` 和 `footer.html` 文件，或者这些文件也可以是 PHP 文件。

这些外部文件可以通过使用两个函数之一包含到 PHP 程序中 - `include()` 和 `require()`。

它们的使用方式如下。

```
include('footer.html')
```

或

```
include('footer.php')
```

或

```
require('header.html')
```

或

```
require('header.php')
```

代码将在调用这些函数的位置执行。执行后，代码将从 `include` 或 `require` 函数下一行继续。

这两个函数的区别在于，使用 `include()` 时如果出现错误，PHP 服务器会生成警告但会继续运行其他代码行。

在 `require()` 的情况下，如果包含的文件执行失败，程序将终止。

请注意，上述示例假设使用 `include ()` 或 `require()` 的 PHP 程序与被调用的文件在同一文件夹中。如果不是，则必须在函数括号内提供文件的绝对或相对路径。

相对路径的示例是 - `require('./footer.html');`

绝对路径的示例是 - `require('c:\\users\\desktop\\header.php');`

```
<html><body><center><b>Welcome to my page</b></center></body></html>
```

假设 `header.html` 文件如上所示。调用此页眉的关联 PHP 程序如下。

```
<?phpinclude('header.html');print"This is my homepage.";?>
```

输出如下。

![](images/00033.jpeg)

这两个函数可以派上用场以减少工作重复。

PHP 中可以通过使用 `date()` 函数显示日期和时间。此函数根据给定的参数返回基于格式的日期和时间信息。

可用的选项如下。

`Y` - 表示 4 位数字格式的年份。

`y` - 表示 2 位数字格式的年份。

`n` - 表示月份为 1 或 2 位数字，如 4。

`m` - 表示月份为 2 位数字，如 05。

`F` - 表示月份的全名，如 August。

`M` - 表示月份的 3 个字母格式，如 Aug。

`j` - 表示月份中的日期为 1 或 2 位数字，如 8。

`d` - 表示月份中的日期为 2 位数字格式，如 08。

`l` - 表示星期几，如 Sunday。

`D` - 表示星期几的 3 个字母格式，如 - Sun。

`w` - 表示星期几为单个数字 - 如 0 表示星期日。

`z` - 表示从 0 到 365 的一年中的天数。

`t` - 表示月份的天数 - 31（8 月）。

`S` - 表示日期的英文序数后缀为 2 个字符 - rd。

`g` - 表示 12 小时格式的小时为 1 或 2 位数字，如 - 6。

`G` - 表示 24 小时格式的小时为 1 或 2 位数字，如 14。

`h` - 表示 12 小时格式的小时为 2 位数字，如 08。

`H` - 表示 24 小时格式的小时为 2 位数字，如 14。

`i` - 表示分钟，如 35。

`s` - 表示秒，如 15。

`a` - 表示 am 或 pm。

`A` - 表示 AM 或 PM。

`U` - 表示自 epoch 以来的秒数，如 1048623008。

让我们看一下这段 PHP 代码。

```
<?php$x =date('l,F,Y');$y = date('h:i:s');print "$x<p>$y";?>
```

输出将如下所示。

![](images/00034.jpeg)

也可以编写 `print date('l,F,Y');` 来获取结果。

PHP 中的时间戳是一个数字，表示自 1970 年 1 月 1 日午夜以来经过的秒数。`time()` 函数返回当前时刻的时间戳。`mktime()` 函数可以返回特定日期和时间的时间戳。

例如：

`$x =mktime(06,12,30);` 其中 6 是小时，12 是分钟，30 是秒。

PHP Web 程序中的一个重要功能是发送电子邮件的能力。PHP 中发送邮件是通过 `mail()` 函数完成的。PHP 函数与服务器的电子邮件应用程序（如 Unix 上的 sendmail 或 SMTP（简单邮件传输协议）服务器）协同工作以发送电子邮件。

`mail('mailto','subject','body of message', 'From: email address of Sender');`

在使用发送邮件服务之前，必须先与主机服务核实。主机服务可能有额外要求，尤其是在服务包为共享的情况下。

```
<?php$x = $_POST['email'];$y = $_POST['password']$body="Thank you for registering at my webpage. Your email address is $x and the password you entered is $y".mail( $x,'Registration complete',$body,'From:admin@yyy.com');?>
```

这是发送邮件的示例代码。这里假设表单或 HTML 页面将提供用户的电子邮件和密码。邮件正文感谢用户注册，并以管理员电子邮件作为发件人电子邮件发送邮件。在共享服务器上对网站使用邮件应谨慎使用。服务器或域名可能被标记为垃圾邮件来源，影响合法邮件。

Cookie 是服务器存储有关用户信息的途径。许多网站要求在显示内容之前启用 cookie。

Cookie 必须在任何其他信息之前从服务器发送到客户端机器。

Cookie 使用 `setcookie()` 函数发送。例如：

```
setcookie('Cookiename', 'This is a test cookie');
```

服务器可以发送给单个用户的 cookie 数量可能有限。Cookie 名称应遵循 PHP 的命名规则。

```
<?php$cookies=false;setcookie('color',$_POST['color']);$cookies=true;if($cookies) { print"Your preference has been saved."; }?>
```

上述 PHP 文件的 HTML 代码如下。

```
<html><head><title>Cookie Example</title></head><body><form action="cookie.php" method="post"> Yellow<input type="radio" name="color" value="Yellow"/>Red<input type="radio" name="color" value="Red"/>Blue<input type="radio" name="color" value="Blue"/><br>Please complete the feedback form and send your preference of color. </p><p><input type ="submit" name="submit" value="color"></form></body></html>
```

HTML 页面将调用 `cookie.php` 文件并将用户的颜色偏好传递给它。

结果输出如下。

![](images/00035.jpeg)

要从 cookie 中检索值，请使用 `$_COOKIE['cookiename']` 方法。

```
<?phpprint $_COOKIE['color'];?>
```

输出将为 red，因为我选择了红色。

接下来我们来看向 cookie 添加一些参数。需要添加的参数是过期时间、路径、域和 term secure。

`setcookie('color',$_POST['color'], time()+60,' ',' ',1);`

这遵循格式：`setcookie('name','value',expiration,'path','domain',secure);`

路径和域用于将 cookie 限制到网站的特定文件夹或特定域，如 `www.xyz.com`。路径可能类似于 `'/userpages/'`。

在上面的示例中，路径和域已被忽略。请看下面的代码。

```
<?php$cookies=false;setcookie('color',$_POST['color'], time()+60,' ',' ',0);$cookies=true;if($cookies) {print"Your preference has been saved.";}?>
```

并使用与之前相同的 html 文件（为方便起见在此处重现）。

