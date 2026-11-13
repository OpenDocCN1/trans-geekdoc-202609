

echo ( "<pre>$filetext</pre>" );
?>
</body>
</html>
```

它将产生以下结果：

```
File size : 278 bytes
The PHP Hypertext Preprocessor (PHP) is a programming language that allows web developers to create dynamic content that interacts with databases.
PHP is basically used for developing web based software applications. This tutorial helps you to build your base with PHP.
```

## 写入文件

可以使用 PHP fwrite() 函数写入新文件或将文本追加到现有文件中。该函数需要两个参数，分别指定文件指针和要写入的数据字符串。可选地，可以包含第三个整数参数来指定要写入的数据长度。如果包含第三个参数，则在达到指定长度后将停止写入。

下面的示例创建一个新文本文件，然后在其中写入一个简短的文本标题。关闭此文件后，将使用 file_exist() 函数确认其存在，该函数将文件名作为参数。

```php
$filename = "/home/user/guest/newfile.txt";
$file = fopen( $filename, "w" );
if( $file == false )
{
   echo ( "Error in opening new file" );
   exit();
}
fwrite( $file, "This is a simple test\n" );
fclose( $file );
?>
```

```html
<html>
<head>
<title>Writing a file using PHP</title>
</head>
<body>
<?php
if ( file_exist( $filename ) )
{
   $filesize = filesize( $filename );
   $msg = "File created with name $filename ";
   $msg .= "containing $filesize bytes";
   echo ($msg );
}
else
{
   echo ( "File $filename does not exist" );
}
?>
</body>
</html>
```

它将产生以下结果：

![](img/b9c80e155ac304a53696823920b08082_81_0.png)

我们在 PHP 文件系统函数章节中已介绍与文件输入和输出相关的所有函数。

PHP 函数与其他编程语言类似。函数是一段代码，它以参数形式接收一个或多个输入，进行一些处理并返回一个值。

你已经见过许多像 fopen() 和 fread() 这样的函数。它们是内置函数，但 PHP 还允许你创建自己的函数。

有两个部分你应该清楚：

- 创建 PHP 函数
- 调用 PHP 函数

实际上，你几乎不需要创建自己的 PHP 函数，因为已经为不同领域创建了 1000 多个内置库函数，你只需根据需要调用它们即可。

有关完整实用函数集，请参阅 PHP 函数参考。

## 创建 PHP 函数

创建自己的 PHP 函数非常简单。假设你想创建一个 PHP 函数，当你调用它时，它将在浏览器上简单地写入一条消息。

下面的示例创建一个名为 writeMessage() 的函数，然后在创建后立即调用它。

请注意，在创建函数时，函数名应以关键字 function 开头，并且所有 PHP 代码都应放在 { 和 } 花括号内，如以下示例所示：

```html
<html>
<head>
<title>Writing PHP Function</title>
</head>
<body>

<?php
/* Defining a PHP Function */
function writeMessage()
{
   echo "You are really a nice person, Have a nice time!";
}
/* Calling a PHP Function */
writeMessage();
?>
</body>
</html>
```

这将显示以下结果：

> 你真是一个好人，祝你愉快！

### 带参数的 PHP 函数

PHP 允许你在函数中传递参数。你可以传递任意数量的参数。这些参数在函数内部像变量一样工作。下面的示例接受两个整数参数，将它们相加，然后打印结果。

```html
<html>
<head>
<title>Writing PHP Function with Parameters</title>
</head>
<body>

<?php
function addFunction($num1, $num2)
{
   $sum = $num1 + $num2;
   echo "Sum of the two numbers is : $sum";
}
addFunction(10, 20);
?>
</body>
</html>
```

这将显示以下结果：

> 两个数字之和为：30

### 通过引用传递参数

可以按引用将参数传递给函数。这意味着函数操作的是变量的引用，而不是变量值的副本。

在这种情况下，对参数所做的任何更改都会更改原始变量的值。你可以在函数调用或函数定义中向变量名添加 & 符号来按引用传递参数。

下面的示例展示了这两种情况。

```html
<html>
<head>
<title>Passing Argument by Reference</title>
</head>
<body>
<?php
function addFive($num)
{
 $num += 5;
}

function addSix(&$num)
{
 $num += 6;
}

$orignum = 10;
addFive( &$orignum );
echo "Original Value is $orignum<br />";
addSix( $orignum );
echo "Original Value is $orignum<br />";
?>
</body>
</html>
```

这将显示以下结果：

```
Original Value is 10
Original Value is 16
```

## PHP 函数返回值

函数可以使用 **返回** 语句结合值或对象来返回一个值。return 停止函数的执行，并将值发送回调用代码。

你可以使用 **return array(1,2,3,4)** 从函数返回多个值。

下面的示例接受两个整数参数，将它们相加，然后将它们的和返回给调用程序。请注意，**return** 关键字用于从函数返回一个值。

```html
<html>
<head>
<title>Writing PHP Function which returns value</title>
</head>
<body>
<?php
function addFunction($num1, $num2)
{
   $sum = $num1 + $num2;
   return $sum;
}
$return_value = addFunction(10, 20);
echo "Returned value from the function : $return_value";
?>
</body>
</html>
```

这将显示以下结果：

函数返回的值：30

## 为函数参数设置默认值

如果函数的调用者未传递参数，你可以为参数设置默认值。

如果用户未向该函数传递任何值，则以下函数将打印 NULL。

```html
<html>
<head>
<title>Writing PHP Function which returns value</title>
</head>
<body>

<?php
function printMe($param = NULL)
{
   print $param;
}
printMe("This is test");
printMe();
?>

</body>
</html>
```

这将产生以下结果：

```
This is test
```

## 动态函数调用

可以将函数名作为字符串赋值给变量，然后将这些变量视为函数名本身。下面的示例展示了这种行为。

```html
<html>
<head>
<title>Dynamic Function Calls</title>
</head>
<body>
<?php
function sayHello()
{
   echo "Hello<br />";
}
$function_holder = "sayHello";
$function_holder();
?>
</body>
</html>
```

这将显示以下结果：

```
Hello
```

### 16. PHP – Cookie

Cookie 是存储在客户端计算机上的文本文件，用于跟踪用途。PHP 透明地支持 HTTP Cookie。

识别返回用户涉及三个步骤：

- 服务器脚本将一组 Cookie 发送到浏览器。例如，姓名、年龄或身份证号码等。
- 浏览器将此信息存储在本地机器上以供将来使用。
- 下次，当浏览器向 Web 服务器发送任何请求时，它会将这些 Cookie 信息发送到服务器，服务器使用该信息来识别用户。

本章将教你如何设置 Cookie、如何访问它们以及如何删除它们。

### Cookie 的结构

Cookie 通常在 HTTP 头中设置（虽然 JavaScript 也可以直接在浏览器上设置 Cookie）。设置 Cookie 的 PHP 脚本可能会发送如下所示的头：

```
HTTP/1.1 200 OK
Date: Fri, 04 Feb 2000 21:03:38 GMT
Server: Apache/1.3.9 (UNIX) PHP/4.0b3
Set-Cookie: name=xyz; expires=Friday, 04-Feb-07 22:03:38 GMT;
path=/; domain=tutorialspoint.com
Connection: close
Content-Type: text/html
```

如你所见，Set-Cookie 头包含一个名称-值对、一个 GMT 日期、一个路径和一个域。名称和值将进行 URL 编码。expires 字段是指示浏览器在给定时间和日期后“忘记”Cookie 的指令。

如果浏览器配置为存储 Cookie，它将保留此信息直到过期日期。如果用户将浏览器指向与 Cookie 的路径和域匹配的任何页面，它将重新将 Cookie 发送到服务器。浏览器的头可能如下所示：

```
GET / HTTP/1.0
Connection: Keep-Alive
User-Agent: Mozilla/4.6 (X11; I; Linux 2.2.6-15apmac ppc)
Host: zink.demon.co.uk:1126
```

