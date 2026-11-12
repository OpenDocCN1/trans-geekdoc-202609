

对于Unix用户，请尝试以下方法：

```
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hi, Dummies Readers!";
```

![](img/3f967ab8a8fddc723173059f56621648_221_0.png)

如果你是Unix或Linux用户，并且想要定位你的Perl程序，只需输入：

```
which perl
```

此命令的结果（例如/usr/bin/perl）正是你要放在#!字符后面的术语。

对于Windows爱好者，请尝试以下方法：

```
#!/perl/bin/perl
print "Content-type: text/html\n\n";
print "Hi, Dummies Readers!";
```

将此文件保存为cgi-bin目录下的first.pl。（有关cgi-bin目录位置的更多详细信息，请参见下一节。）接下来，如果你使用的是Linux或Unix，请进入cgi-bin目录并输入以下命令：

```
chmod a+x first.pl
```

然后你可以通过Web服务器，使用以下地址在浏览器中打开该文件：http://localhost/cgi-bin/first.pl。

如果一切顺利，你会看到消息Hi, Dummies Readers!。如果没有，别担心；下一节将帮助你正确安装和配置一切。继续阅读。

## 配置Apache以支持CGI

默认情况下，Apache自带一个用于CGI脚本的特定目录，可以直接使用。默认情况下，Unix和Linux上的路径为/usr/local/apache/cgi-bin，Windows上则是主Apache目录下的cgi-bin目录。（如果你使用Unix或Linux，并且看不到/usr/local/apache/cgi-bin目录，那么你很可能拥有一个/var/www/cgi-bin目录。）如果将文件放入此目录，Apache会尝试执行它。

关于你的cgi-bin目录，请记住以下两点：

- cgi-bin目录中的文件必须具有可执行权限。（在Windows上，这不是问题。）
- 你可以通过修改httpd.conf文件在服务器上设置其他cgi-bin目录。

在Linux和Unix上，Apache服务器不是以创建CGI脚本的人的用户名运行的（即使Web服务器上有多个用户，每个用户都有自己的cgi-bin目录）。因此，当你创建CGI脚本时，需要为所有人设置执行权限。为此，请切换到你的cgi-bin目录并输入以下命令，将myscript.pl替换为你的脚本文件名：

```
chmod a+x myscript.pl
```

chmod命令（即“change mode”的缩写）用于设置文件权限，a+x选项会为所有人添加执行权限。

![](img/3f967ab8a8fddc723173059f56621648_222_0.png)

在Windows上，你不需要设置权限。但是，执行问题可能无法按你预期的方式工作。通常，对于非程序文件，Windows会查找文件关联，并运行与文件类型（基于文件扩展名，如.doc或.xls）关联的程序。因此，如果你尝试执行带有.doc扩展名的文件，并且安装了Microsoft Word，Windows会查找关联，发现Word是关联程序，并运行Word，将你的文件名作为参数传递。Word随后会打开作为参数传递的文件。（运行的程序可以根据程序员编码产品的方式，随意处理参数或完全忽略它；但是，Word确实会打开该文件。）

我刚刚描述了正常执行事物的方式。但是，Apache处理cgi-bin目录中的脚本文件的方式略有不同。Apache会查看文件开头的pound-bang (#!) 行，我在下一节中会讨论它；Apache会运行pound-bang行中给出的程序，并将脚本文件作为参数传递。

## 指定pound-bang (#!) 行

在Linux/Unix和Windows上，你需要在脚本文件开头指定一行pound-bang行。（有些人称之为shebang行。）这一行告诉Apache运行什么程序来执行脚本。（从技术上讲，Linux和Unix版本的Apache允许shell系统确定如何运行程序。）

下面是针对Linux或Unix的简单Perl脚本示例：

```
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hello from Perl";
```

下面是针对Windows的示例脚本：

```
#!/perl/bin/perl
print "Content-type: text/html\n\n";
print "Hello from Perl";
```

每个示例脚本都以一行开始，该行以井号字符(#)开头，后跟编程界称为bang的字符，即感叹号(!)。然后是可执行文件的路径和文件名。对于Linux/Unix版本，路径和文件名是/usr/bin/perl。对于Windows版本，它是/perl/bin/perl，对应于\perl\bin\perl.exe。这一行告诉Apache（或Unix/Linux shell）运行哪个程序来处理脚本。在这两种情况下，都是Perl程序，因此Apache会运行Perl来运行脚本。

![](img/3f967ab8a8fddc723173059f56621648_223_0.png)

请确保包含第一行pound-bang行。如果忘记了，Apache将不知道如何运行脚本，浏览器中会出现Internal Server Error消息。在本章中，我使用Unix/Linux形式的pound-bang，常见的默认路径是/usr/bin/perl。请根据你的系统相应修改pound-bang行。

## 添加更多cgi-bin目录

你可能不止需要一个cgi-bin目录。例如，如果你运行一个有多个用户的服务器，你可能希望为每个用户提供自己的cgi-bin目录。为此，请向httpd.conf文件添加ScriptAlias指令并指定一个目录。

假设你的文件系统中有一个目录无法作为Web目录访问。（该目录不在DocumentRoot目录下，也不在Alias目录下。）但你想要在该目录中放置CGI脚本，因此必须在httpd.conf文件中包含一个ScriptAlias指令。

例如，假设你希望目录/home/jeff/myscripts中包含CGI脚本。你还希望目录名在URL中显示如下：

```
http://www.somedomain.com/myscripts/somescript.pl
```

将somedomain替换为你的域名。然后在httpd.conf文件中包含以下行：

```
ScriptAlias /myscripts/ "/home/jeff/myscripts/"
```

始终在ScriptAlias行中的别名名和目录名之后添加尾部斜杠。（如果不这样做，Apache将无法正确定位目录。）另外，必须在重新启动Apache后，httpd.conf的更改才会生效。

## 编写简单的CGI脚本

本章前面，我向你展示了一个用Perl编写的简单CGI脚本。其理念是，当你请求网页时，Apache运行Perl程序，该程序将写出发送到浏览器的HTML。以下是再次提供的脚本（请记住相应调整pound-bang行）：

```
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hi, Dummies Readers!";
```

第一行会写出浏览器接收到的必需标头信息，但不会作为.html文件的一部分写入。下一行会打印出成为.html文件的行。

每个生成HTML的CGI脚本在写入任何HTML之前，都必须先写出这一行文本：

```
Content-type: text/html
```

这一行后面跟着两个换行符。这一行是一个标头行，由浏览器解析以决定正在接收什么类型的文件；它是HTTP协议的一部分，如果不包含它，浏览器将不知道文件类型，并会报错或弹出“另存为”对话框。

在Perl中，你会像下面这样写出标头行和HTML代码：

```
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "<html><head><title>";
print "This is my web page!";
print "</title></head>\n";
print "<body>\n";
print "<h1>Welcome!</h1>\n";
print "<table border=\"1\">\n";
for ($i=0; $i<10; $i++) (
    print "<tr><td>$i</td><td>$i</td><td>$i</td></tr>\n";
)
print "</table>";
print "</body></html>";
```

在这个示例中，我编写的不仅仅是静态HTML。我使用Perl来生成HTML。如果你将此文件保存为cgi-bin目录下的complex.pl，可以使用 http://localhost/cgi-bin/complex.pl 加载它。以下是生成的HTML：

```
<html><head><title>This is my web page!</title></head>
<body>
<h1>Welcome!</h1>
<table border="1">
<tr><td>0</td><td>0</td><td>0</td></tr>
<tr><td>1</td><td>1</td><td>1</td></tr>
<tr><td>2</td><td>2</td><td>2</td></tr>
<tr><td>3</td><td>3</td><td>3</td></tr>
<tr><td>4</td><td>4</td><td>4</td></tr>
<tr><td>5</td><td>5</td><td>5</td></tr>
<tr><td>6</td><td>6</td><td>6</td></tr>
<tr><td>7</td><td>7</td><td>7</td></tr>
<tr><td>8</td><td>8</td><td>8</td></tr>
<tr><td>9</td><td>9</td><td>9</td></tr>
</table></body></html>
```

这个示例并不特别有趣；它只是一个表格。但你可以看到我是如何使用Perl生成表格的。此外，你可以看到Content-type行没有出现在输出中。实际上，你的程序正在写出这一行，但浏览器会将其单独解析，并在浏览器窗口中不显示它；如果你在浏览器中查看HTML源代码，也看不到这一行。现在，这里有一个更有趣的示例：

```
#!/usr/bin/perl
use POSIX;
print "Content-type: text/html\n\n";
print "<html><head><title>";
print "This is my web page!";
print "</title></head>\n";
print "<body>\n";
@now = localtime(time);
$now_string = strftime("%a %b %d %H:%M:%S %Y", @now);
print "The time is $now_string<br>\n";
print "</body></html>";
```

