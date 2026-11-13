

```
mysql> use guestbook;
Database changed
mysql> create table guestbook
-> (
-> 	 name 			 varchar(40) null,
-> 	 location 		 varchar(40) null,
-> 	 email 		 varchar(40) null,
-> 	 url 			 varchar(40) null,
-> 	 comments 		 text null
-> ) 
-> ;
Query OK. 0 rows affected (0.00 sec)
mysql>
```

然后，你必须授予你的应用程序使用该表的权限：

```
mysql> grant delete, insert, select, update on guestbook
-> 		 to nobody@localhost identified by 'ydobon';
Query OK. 0 rows affected (0.00 sec)
```

然后你发出一条快速语句，强制服务器重新读取权限表，从而使新设置生效：

```
mysql> FLUSH PRIVILEGES;
```

现在你已经拥有一个名为 guestbook 的数据库，以及数据库中一个同样名为 guestbook 的表了。现在是时候用 PHP 编写一个应用程序，使你能够插入、编辑和查看该留言簿中保存的信息。

## 你的 PHP 脚本

现在是时候转到文本编辑器了。在配置 Web 服务器的过程中，你需要让它知道哪些文件应移交给 PHP 以便引擎解析页面。这些文件通常带有 .php 扩展名，不过也有可能让 PHP 解析任何文件，包括 .html 文件。这些脚本位于用于存放网页的文件夹中。对于 Apache，这通常是 /htdocs。

## 基本语法

PHP 的一个妙处在于，它让你在纯 HTML 与属于 PHP 编程语言的命令之间自由切换。其工作原理如下：脚本中介于开标签（<?php）和闭标签（?>）之间的部分将由 PHP 引擎解释，而这些标签之外的部分则被视为普通 HTML。请看下面的 PHP 页面。

```
<?php
echo "Hi, ";
?>
mom.
```

经过 Web 服务器运行后，这段代码会生成一个网页，简单地打印出 Hi, mom。PHP 的 echo 命令处理第一行的第一部分。但当然，PHP 能做的远不止于此。像其他任何编程语言一样，它可以处理变量并做出决策。

```
<?php
echo "Hi, mom. ";

$var = date("H");
if ($var <= 11)
{
    echo "good morning";
}
elseif ($var > 11 and $var < 18)
{
    echo "good afternoon";
}
else
{
    echo "good evening";
}
?>
```

在前面的代码中，打印出问候语之后，就开始进行真正的编程了。我们使用了 PHP 的内置 date 函数来获取当天小时（24 小时制）。该值立即被赋给名为 $var 的变量。然后做出决策，并根据一天中的时间打印相应的文本。请注意这里的语法。每条 PHP 命令都以分号（;）结尾。在 if 语句中，花括号（{}）包含根据条件执行的命令。而条件本身则位于圆括号（()）内。

前面示例中使用的 date() 函数和 echo 只是 PHP 内置的数百个函数中的两个，其中许多你将在本书学习过程中学会使用。如果你打算访问数据库，还需要更多函数。

## 连接到数据库

安装 PHP 时，你应该让它知道你打算将其与 MySQL 一起使用。如果不这样做，我们现在讨论的内容将无法工作。即使 PHP 知道你在使用 MySQL，在你的特定脚本中，你也必须标识你需要访问的确切数据库。在这里，那就是你刚创建的 guestbook 数据库。

```
mysql_connect("localhost","nobody","ydobon")
or die("<h3>could not connect to MySQL</h3>\n");
mysql_select_db("guestbook")
or die("<h3>could not select database 'guestbook'</h3>\n");
```

前面代码的第一行告诉 MySQL，运行脚本的 Web 服务器位于本地机器上，用户名为 *nobody*，密码为 *ydobon*。然后，如果连接成功，将使用 `mysql_select_db()` 命令选择特定的数据库。将这些行安全地保存在脚本中后，你应该就能用命令来操作数据库了。

因为你要在本应用程序的每个页面中都用到这些行，所以将它们保存到单独的文件中并在每个页面中包含它们，可以省去一些输入工作。如果你有任何编程经验，就知道这涉及将该文件的全部内容复制到正在访问的文件中。这些行保存在名为 dbconnect.php 的文件中。本应用程序中每个其他文件的顶部将是以下行：

```
include('dbconnect.php');
```

## 将信息插入数据库

由于你尚未向数据库中添加任何用户，我们先来回顾一下能让你做到这一点的脚本。但首先，我们需要再多介绍一些关于 PHP 变量的知识。在本介绍中较早的“基本语法”一节中，我们展示了可以在 PHP 脚本内创建变量，但因为这是一个客户端/服务器环境，你需要将客户端（Web 浏览器）的变量数据传递给 PHP。你通常使用 HTML 表单来实现这一点。

附录 B 中对 HTML 表单有基本介绍，如有需要请查阅。目前我们只想指出，每个表单元素都有一个名称，而当表单被提交时，这些表单元素的名称会作为变量在表单提交到的 PHP 脚本中可用。

在 PHP 的早期版本中，这些变量会自动创建为全局变量：如果你提交了一个带有名为 firstname 的字段的表单，接收表单的脚本在开始时就会有一个名为 $firstname 的变量。然而，这可能会导致严重的安全问题。因此，现在这些值作为系统定义的“超全局”数组的元素可用，例如 $_GET（用于作为 URL 一部分传递的字段）和 $_POST（用于从表单提交的字段）。最简单的是 $_REQUEST，它结合了 GET、POST 和 cookie 值。如果你现在还不完全理解这些，不用担心；这些概念将在本书后面更详细地介绍，特别是在第 9 章。

一旦下面的表单被提交，变量 $_REQUEST['surname'] 和 $_REQUEST['submit'] 就会在 PHP 脚本 myscript.php 中可用。$_REQUEST['surname'] 的值是用户在文本字段中输入的任何内容。$_REQUEST['submit'] 的值是文本字符串 submit。

```
<form action="myscript.php">
<input type="text" name="surname">
<input type="submit" name="submit" value="submit">
</form>
```

在展示脚本本身之前，现在是时候指出 Web 编程与其他类型编程的一个重要区别：它是无状态的。要显示页面，Web 服务器必须首先接收来自浏览器的请求。它们使用的语言称为 HTTP，即超文本传输协议。请求包含多项内容——浏览器希望查看的页面、表单数据、所使用的浏览器类型以及浏览器正在使用的 IP 地址。根据这些信息，Web 服务器决定提供什么内容。

一旦提供了该页面，服务器就不再保持与浏览器的连接。它完全不记得自己向谁提供了什么。每个 HTTP 请求都会单独处理，不考虑之前发生了什么。因此，在 Web 编程中，你需要想出某种方式来维持状态。也就是说，如果你正在使用一个应用程序，你需要某种方式让服务器知道发生了什么。基本上，你需要从一个页面向另一个页面传递变量的方法。这在我们的应用程序中会用到。应用程序有三种方法来做到这一点：通过传递隐藏表单元素、使用 Cookie 或使用会话。

现在回到脚本。

```
<form action="myscript.php">
<input type="text" name="surname">
<input type="submit" name="submit" value="submit">
</form>
```

你可以根据来自 HTML 表单的变量信息决定在页面上显示什么内容。例如，你可以通过检查变量 $_REQUEST['submit'] 是否具有 submit 值来判断前面的表单是否已被提交。当我们创建用于将信息插入数据库的页面时，就会用到这一技巧。

我们的应用程序中有一个名为 sign.php 的页面，它包含一个 HTML 表单。该页面中表单的 action（提交后要运行的程序）是 create_entry.php。下面是该页面的全部内容：

```
<h2>Sign my Guest Book!!</h2>
<form method="post" action="create_entry.php">
<b>Name:</b>
<input type="text" size="40" name="name">
<br>
```

