

sin(30) = 0.5
cos(30) = 0.866025403784
tan(30) = 0.57735026919

在现实世界中，变量函数调用常被用于根据用户输入或其他外部因素等，动态选择要立即执行的函数。您也可以使用它来编写调用用户创建的回调函数或事件处理函数的代码。（您将在第 15 章中创建回调函数，在第 19 章中创建一些事件处理函数。）

## 编写您自己的函数

到目前为止，您已了解函数是非常有用的工具，可让您封装和重用代码，并且您已探索过如何在 PHP 中调用函数。真正的乐趣现在开始，因为您将创建自己的函数。

定义函数非常简单——只需使用以下语法：

```
function myFunc() {
// (do stuff here)
}
```

换句话说，您先写出单词 function，然后跟上要创建的函数名，再跟上一对圆括号。接下来，将函数代码放在花括号（{}）之间。

这是一个简单的示例：

```
function hello() {
 echo "Hello, world!<br/>";
}

// Displays "Hello, world!"
hello();
```

如您所见，此脚本定义了一个名为 hello() 的函数，该函数仅显示字符串 "Hello, world!"。函数定义之后，脚本会调用 hello() 函数以显示输出。

> 请注意，hello() 函数内的代码仅在稍后调用函数时运行，而在创建函数本身时不会运行。仅创建函数并不会运行函数内的代码；您必须显式调用函数才能运行其代码。

### 定义参数

如您所知，函数可以选择接受一个或多个实参（即传递给函数的值）。要告诉 PHP 您希望函数接受实参，请在定义函数时指定一个或多个对应的形参。形参是一个变量，用于保存调用函数时传递给它的值。

严格来说，实参是您传递给函数的值，而形参是函数内部用于接收实参的变量。在实际编程中，程序员经常将这两个术语混用。

要为函数指定形参，请在圆括号之间插入一个或多个变量名，如下所示：

```
function myFunc( $oneParameter, $anotherParameter ) {
  // (do stuff here)
}
```

您可以包含任意数量的形参变量。对于您指定的每个形参，调用函数时都需要传递一个对应的实参。传递给函数的实参随后会被放入这些形参变量中。下面是一个示例：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Saying hello with style</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Saying hello with style</h1>
<?php
function helloWithStyle( $font, $size ) {
  echo "<p style=\"font-family: $font; font-size: {$size}em;\">Hello, world!</p>";
}
helloWithStyle( "Helvetica", 2 );
helloWithStyle( "Times", 3 );
helloWithStyle( "Courier", 1.5 );
?>
</body>
</html>
```

此代码创建了一个名为 helloWithStyle() 的函数，该函数有两个形参变量：$font 和 $size。随后，这些变量在函数内用于通过 CSS 设置文本的字体和大小。

顺便说一下，代码中的 `${size}em` 这种花括号语法在您需要在变量名后紧跟一些字母和/或数字（本例中为 em）时非常有用。有关此语法的更多信息，请参见第 5 章。

接下来，代码会三次调用 helloWithStyle() 函数，每次传入不同的实参。每次函数调用中，$font 形参都会采用第一个实参的值，$size 形参都会采用第二个实参的值。

请注意，函数调用中实参的顺序与函数定义中形参的顺序一致。

将此脚本另存为 hello_with_style.php 并放在文档根目录文件夹中，然后尝试运行。生成的页面如图 7-2 所示。您可以看到，函数内同一行代码被用了三次，产生了三种截然不同的问候语。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_184_0.png)

图 7-2

### 可选参数和默认值

前面的 hello_with_style.php 脚本表明，函数可以非常强大。脚本中的单行函数 helloWithStyle() 能够使用用户浏览器支持的任何字体和文本大小来显示文本 "Hello, world!"。

然而，假设您大多数时候都想使用 1.5 em 的字体大小。如果在每次调用函数时都必须包含第二个实参，那将很麻烦：

```
helloWithStyle( "Helvetica", 1.5 );
helloWithStyle( "Times", 1.5 );
helloWithStyle( "Courier", 1.5 );
```

幸运的是，PHP 允许您创建带有可选参数的函数。定义可选参数的方法如下：

```
function myFunc( $parameterName=defaultValue ) {
    // (do stuff here)
}
```

换句话说，您插入形参名，然后是等号（=），再是默认值。这就是在调用函数时未传递对应实参时，形参将采用的值。因此，您可以将前面的 hello_with_style.php 脚本重写如下：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Saying hello with style</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Saying hello with style</h1>

<?php
function helloWithStyle( $font, $size=1.5 ) {
echo "<p style=\"font-family: $font; font-size: {$size}em;\">Hello, world!</p>";
}

helloWithStyle( "Helvetica", 2 );
helloWithStyle( "Times", 3 );
helloWithStyle( "Courier" );
?>

</body>
</html>
```

您可以看到，对 helloWithStyle() 的第三次调用没有向函数传递第二个实参。这会导致 PHP 将 $size 形参的值设为默认值 1.5。最终结果是，第三个 “Hello, world!” 将使用 Courier 字体以 1.5 em 的大小显示，与脚本的第一个版本相同。

### 从函数返回值

本章前面，您已了解函数不仅可以接受值，还可以返回值。例如，前面展示的内置 sqrt() 函数接受一个实参（一个数字），并返回一个值（该数字的平方根）。

> 请注意，接受实参和返回值都是可选的。函数可以只做其中一项、两项都做，或两项都不做。

要使函数返回一个值，您要用到——您肯定猜到了——PHP 的 return 语句：

```
function myFunc() {
// (do stuff here)
return value;
}
```

返回值可以是任意表达式，因此您可以使用字面值（例如 1 或 false）、变量名（例如 $result）或更复杂的表达式（例如 $x * 3 / 7）。

当 PHP 引擎遇到 return 语句时，它会立即退出函数，并将 value 返回给调用该函数的代码，后者可根据需要使用该值。

以下示例脚本展示了如何定义和使用返回值的函数：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Normal and bold text</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Normal and bold text</h1>
<?php
function makeBold( $text ) {
return "<b>$text</b>";
}
$normalText = "This is normal text.";
$boldText = makeBold( "This is bold text." );
echo "<p>$normalText</p>";
echo "<p>$boldText</p>";
?>
</body>
</html>
```

此脚本定义了一个名为 makeBold() 的函数，该函数接受一个字符串实参，并返回被 HTML <b>...</b>（粗体）标签括起来的字符串。接着，它创建一个名为 $normalText 的变量，其中包含未格式化的文本字符串。然后，它调用 makeBold() 函数，传入一些要格式化的文本，并将 makeBold() 的返回值存储在另一个变量 $boldText 中。最后，脚本将 $normalText 和 $boldText 都输出到浏览器。

您可以在图 7-3 中看到结果。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_186_0.png)

### 图 7-3

