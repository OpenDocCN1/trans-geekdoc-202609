

### 5.8 完整的图形用户界面（GUI）

如今，许多用户都期望拥有完整的图形用户界面（GUI），这非常有道理。当 GUI 设计得当时，它们有助于发现性和交互的便捷性。它们可以提供直观且用户友好的方式来呈现数据和信息，非常适合基于事件的编程。

大多数 GUI 程序都使用“小部件工具包”（也称为 GUI 工具包）来编写。这些是提供 GUI 构建块代码的工具包或框架；窗口、表单、按钮、列表、鼠标交互、菜单、事件等。有大量的小部件工具包，有些是低级且特定于平台的，例如 Windows 的 Windows API 或 Mac OS X 的 Carbon，有些是高级且跨平台的，例如 GTK+ 和 QT，有些是特定于语言的，例如 Java 的 Swing 和 Object Pascal 的 LCL。维基百科上有一个相当全面的列表。

| ![information](Images/image00248.jpeg) || **进一步阅读**维基百科上的小部件工具包  

[http://en.wikipedia.org/wiki/List\_of\_widget\_toolkits](http://en.wikipedia.org/wiki/List_of_widget_toolkits) |

| --- | --- |

在 PHP 中，有两种方法使用这些工具包来创建图形界面。第一种是通过直接绑定 - 您的 PHP 脚本通过库或 PHP 扩展直接调用工具包。第二种是通过辅助应用程序 - 您的 PHP 脚本使用 HTML 或 XUL 等中间语言告诉辅助应用程序它想要显示的内容，然后辅助应用程序负责调用工具包（或其自身代码）的必要元素，并为您显示界面。前者是编写图形应用程序的传统方式，后者更类似于 Web 方法（其中浏览器是您的脚本发送 HTML 的辅助应用程序）。两种方法都有优缺点，下面我们将探讨这两种方法的一些当前实现。

### 5.9 理解 GUI 和基于事件的编程

在此花点时间讨论一下 GUI 应用程序与例如命令行编程之间的主要区别之一是值得的。大多数 GUI 编程都是基于事件的编程，如果您以前没有使用过这种编程风格，可能需要一段时间才能理解。

使用 GUI 程序时，您通常像往常一样“顺序”开始编程，打开一个窗口或表单，并用按钮、文本、图像、数据或其他内容填充它。

此时，您的程序会进入一个等待循环，通常等待用户（或有时是系统）执行某些操作。这可能是等待他们单击按钮、输入文本、选择选项或等待新数据到达。这些事情中的每一个都称为一个事件，您通常无法预测它们发生的顺序。因此，您的代码会将这些事件绑定到函数或方法，并在相关事件发生时调用它们。

这意味着您的代码通常会按非顺序执行，因此保持状态的同步比在命令行脚本甚至 Web 脚本中要微妙得多，后者是从上到下顺序运行的。处理基于事件的程序最常见的方法是使用面向对象（OO）编程技术，的确，GUI 软件的兴起推动了 OO 编程的兴起（或者反过来，取决于你和谁交谈）。当然，仍然完全可以使用传统的“命令式”风格编程，特别是如果您小心处理状态和作用域等问题，但如果您打算进行大量的 GUI 编程且不熟悉 OO，那么您最好拿一本 OO 入门书快速浏览一下，这对您有好处。

| ![information](Images/image00248.jpeg) || **进一步阅读**维基百科上的面向对象编程  

[http://en.wikipedia.org/wiki/Object-oriented\_programming](http://en.wikipedia.org/wiki/Object-oriented_programming)“PHP OOP 简介”由 Lorna Mitchell  

[http://www.lornajane.net/posts/2012/introduction-to-php-oop](http://www.lornajane.net/posts/2012/introduction-to-php-oop)“初学者的面向对象 PHP”由 Jason Lengstorf  

[http://net.tutsplus.com/tutorials/php/object-oriented-php-for-beginners/](http://net.tutsplus.com/tutorials/php/object-oriented-php-for-beginners/) |

| --- | --- |

Web 编程在某种意义上当然也是基于事件的，您通常向用户呈现一个 HTML 页面，然后等待他们单击按钮或链接，并用另一个 HTML 页面（或使用不同参数再次运行同一脚本）来处理该“事件”。您的每个 HTML 页面（或生成它们的 PHP 脚本）在某种程度上都相当于 GUI 脚本中调用的单个函数或方法，而您的 Web 服务器（Apache 等）相当于 GUI 程序中的等待循环，它将事物联系在一起并响应我们的事件。区别在于，在基于 Web 的编程中，特别是使用 PHP 时，我们基于共享无（或几乎无）的基础运行 - 每个脚本执行或 HTML 页面获取都故意与另一个分开，除非我们采取其他措施来共享某些状态。在 GUI 编程中，我们通常在同一进程下的同一脚本集中运行，因此它是一种共享（几乎）一切的架构。一旦您掌握了这个概念，您就会发现规划和绘制软件要容易得多。

现在让我们看看可用的一些 GUI 工具包。

### 5.10 wxPHP

```php
<?
echo("This text will go to STDOUT (your terminal) as normal\n");

# Start buffering our output rather than sending it STDOUT

ob_start();

# Echo and print write to the php://output stream. By default, 
# php://output writes to STDOUT, which is why echo normally prints stuff 
# back to the terminal. ob_start() captures the php://output stream, 
# however we can still write to STDOUT directly (rather than via echo) if 
# we want to tell the user what we're up to.

fwrite(STDOUT, "Starting HTML Generation...\n"); # displayed in terminal

# So we create our HTML as we would if we were "on the web"

echo('<html>');

print("<head><title>My HTML Page</title></head>\n");

?>
<body>
<h1> Intermingle Some HTML</h1>
<p>In the traditional PHP Way</p>
<p>
<a href="http://www.php.net">An Important Link</A>|||
<?

echo('</body></html>');

fwrite(STDOUT, "Finished HTML Generation\n"); # displayed in terminal

# ob_get_contents() creates a string with everything buffered so far.

$ourHtml = ob_get_contents();

# We can continue with buffering if we need to, or in this case we
# end "ob_end_clean"ly. If we ob_end_flush() instead, then the contents of 
# the buffer would be pushed to php://output, which after ending the
# buffering is STDOUT, which we don't want in this case.

ob_end_clean();

echo ("This Text will go to STDOUT\n"); # now that we've ended buffering

# Finally, we want to save the buffered HTML to a file. Lets create
# a unique temporary file name ....

$filename = tempnam(sys_get_temp_dir(), 'my_report_').'.html';

# and write the HTML string to it.

file_put_contents($filename, $ourHtml);

# Finally, we want to open a web browser to view the HTML "report" we
# just created. Here we use the command "see" (available on most Debian
# based distros) to open the default viewer for the filetype (HTML).
# The command "open" achieves the same thing on other platforms. You
# can also specify a particular browser if you want, 
# e.g. `firefox $filename`

`see $filename`;
```

| ![information](Images/image00248.jpeg) || **进一步阅读**PHP 手册中的输出缓冲控制  

[http://www.php.net/manual/en/book.outcontrol.php](http://www.php.net/manual/en/book.outcontrol.php) |

| --- | --- |

