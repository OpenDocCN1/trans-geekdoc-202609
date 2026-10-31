
## 会话

PHP 4 如同 ASP 和 ColdFusion 一样，原生支持会话，只是做得更好。会话是什么？基本上，它是维护页面之间状态的另一种方式。你的脚本通过 `session_start()` 函数声明会话应该开始。此时 PHP 注册一个唯一的会话 ID，通常该 ID 会通过 cookie 发送给用户。PHP 然后在服务器上创建一个对应的文件，该文件可以跟踪任意数量的变量。文件名称与会话 ID 相同。

一旦会话创建，你可以注册任意数量的变量。这些变量的值保存在服务器上的文件中。只要会话 cookie 存在，这些变量就会对同一域内希望访问它们的任何页面可用。这比通过隐藏表单元素或臃肿的 cookie 在页面间传递变量要方便得多。

当然，有些用户可能不允许使用 cookie。因此，PHP 允许你通过查询字符串跟踪 Session ID。你可以手动将 Session ID 附加到查询字符串上，也可以通过更改配置选项来实现。

要手动将会话 ID 添加到查询字符串，请使用 `<?= SID ?>`。这会自动打印出类似这样的字符串：

```
PHPSESSID=07d696c4fd787cd6c78b734fb4855520
```

将其添加到链接中会通过查询字符串传递 PHPSESSID 变量。使用类似这样的代码：

```
<a href="mypage.php?<?=SID?>">click to page</a>
```

![](img/de0823012275cf4ceebdb822a56e6b71_115_0.png)

> <?= 是 echo 的简写。你可以在任何时候使用它，而不仅仅是会话。

如果 PHP 使用 `-enable-trans-id` 选项编译，会话 ID 将自动添加到每个相对链接中。

基本上，它非常简单。下面的脚本将注册一个名为 `$my_var` 的会话变量，并将其值赋为 "hello world"。

```
<?
session_start();
session_register("my_var");
$my_var = "hello world";
?>
```

在后续页面中，变量 $my_var 将可用，但只有在运行 session_start() 函数之后。该函数告诉 PHP 查找会话，如果会话存在，则将所有会话变量作为全局变量访问。

使用 if 语句使会话变量正确可访问可能需要做一点工作。请看下面的简短脚本作为示例。

```php
<?php
session_start();
session_register("your_name");
//check to see if $your_name contains anything
if(!empty($your_name))
{
    echo "I already know your name, $your_name";
}
//this portion will probably run the first time to
//this page.
elseif(empty($your_name) && !isset($submit))
{
    echo "<form name=myform method=post action=$PHP_SELF>
        <input type=text name=first_name> first name<br>
        <input type=text name=last_name> last name<br>
        <input type=submit name=submit value=submit>
        </form>";
//if the form has been submitted, this portion will
//run and make an assignment to $your_name.
} elseif (isset($submit) && empty($your_name))
{
    $your_name = $first_name . " " . $last_name;
    echo "Thank you, $your_name";
}
?>
```

运行此代码后，刷新浏览器。你会看到脚本记住了你的身份。

![](img/de0823012275cf4ceebdb822a56e6b71_116_0.png)

你的 setcookie() 和 session_start() 函数应始终位于文件的最顶部。如果在设置 cookie 之前尝试向浏览器发送任何内容，你将收到错误消息。

## 使用内置变量

服务器和 PHP 环境设置了各种变量。你可以通过运行 phpinfo() 找到这些变量的完整列表。如果你还没有这样做，请打开键盘，输入以下内容，然后运行以下脚本：

```
<?php
phpinfo();
?>
```

它会生成一个看起来像图 4-3 的页面。

![](img/de0823012275cf4ceebdb822a56e6b71_117_0.png)

图 4-3: phpinfo();

使用完毕后删除此页面是个好主意。没有必要向黑客提供不必要的额外信息。

你可以用各种方式使用这些变量。我们现在来看一些例子，并说明何时可能使用它们。一些变量来自 PHP 引擎，而另一些则源自你的 Web 服务器。

## PHP 变量

这些是通过 PHP 可用的变量。

## PHP_SELF

这是正在运行的文件的地址。通常会从 ServerRoot 目录给出完整路径，这在表单在同一 PHP 页面中同时呈现和处理时非常有用。

```
<?
if(isset($submit))
{
    //do some form processing here
    echo "thanks for the submission";
} else {
?>
<form name=myform method=post action=<?=$PHP_SELF?>>
    <input type=text name=first_name> first name<br>
    <input type=text name=last_name> last name<br>
    <input type=submit name=submit value=submit>
</form>
<?
}
?>
```

请记住，PHP_SELF 始终指的是 URL 中正在执行的脚本的名称。因此，在包含文件中，PHP_SELF 不会引用被包含的文件。它会引用正在运行的脚本。

值得注意的是，当 PHP 在 Windows 上运行或作为 CGI 模块运行时，PHP_SELF 的行为会很奇怪。请务必查看 phpinfo() 以了解系统上 $PHP_SELF 的值。

## HTTP_POST_VARS

这是包含通过 POST 方法发送的所有变量的数组，通常通过表单发送。你可以将其中的每个变量作为关联数组中的元素访问（例如 $HTTP_POST_VARS["myname"]）。

## HTTP_GET_VARS

这是包含通过 GET 方法发送的所有变量的数组。你可以将其中的每个变量作为关联数组中的元素访问（例如 $HTTP_GET_VARS["myname"]）。

## HTTP_COOKIE_VARS

发送到浏览器的所有 cookie 都可以在此关联数组中读取。这包括会话 cookie。如果你想知道 cookie 的行为如何，phpinfo() 会快速显示浏览器发送到服务器的内容。

## Apache 变量

Apache 跟踪数十个变量。我们无法在此列出完整的变量列表，因为你使用的变量会根据当前设置而有所不同。以下是你在脚本中可能经常使用的一些变量。

在查看此列表和 phpinfo() 时，请记住，如果你对 Web 服务器变量不满意，需要更改服务器配置，而不是 PHP。PHP 只是传递信息，无法更改这些变量。

## DOCUMENT_ROOT

此变量返回 Web 服务器根目录的完整路径。对于大多数 Apache 用户，此目录将类似于 /path/to/htdocs。我们在全书中使用此变量使应用程序具有可移植性。以此 include 语句为例：

```
include"$DOCUMENT_ROOT/book/functions/charset.php";
```

通过使用 DOCUMENT_ROOT 变量而不是绝对路径，我们可以将书籍目录及其所有子文件夹移动到任何其他 Apache 服务器，而不必担心 include 语句会失效。请记住，如果你使用的是 Apache 以外的 Web 服务器，DOCUMENT_ROOT 可能不可用。

![](img/de0823012275cf4ceebdb822a56e6b71_119_0.png)

> 如果你在 php.ini 文件中设置了 include_path 指令，你就不必担心在 include 语句中指定任何路径——PHP 会在你指定的所有目录中查找并尝试找到你指示的文件。

## HTTP_REFERER

此变量包含用户在当前查看页面之前查看的页面的 URL。使用 HTTP_REFERER 时请记住，并非每个页面请求都有 referer。如果有人在浏览器中输入 URL，或通过书签访问你的页面，则不会发送 referer。此变量可用于呈现自定义信息。如果你与另一个站点有关系，并且希望仅为从该域引用的用户提供特殊的自定义头部，你可能会使用如下脚本：

//check if my user was referred from my_partners_domain.com
if(ereg ("http://my_partners_domain.com.*" , $HTTP_REFERER))
{
