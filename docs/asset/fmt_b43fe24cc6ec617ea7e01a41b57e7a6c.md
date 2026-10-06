
一旦用户点击按钮，名为 `$email`、`first_name` 和 `$submit` 的变量将在 PHP 页面中可用。你可以以任何合适的方式处理这些变量。注意，在我们的大多数应用程序中，我们将使用提交按钮的值，以确保页面理解用户采取了什么操作。以下是其工作的简要示例。假设页面名为 `mypage.php`。

```php
<?php
if (isset($submit) && $submit=="yes") {
  echo "thank you for submitting your form.\n";
} else {
  echo '<form action=mypage.php method=post">
    <input type=text name=email>
    <input type=text name=first_name>
    <input type=submit name=submit value=yes>
  </form>';
}
?>
```

![](img/245156cc770929860a3ede93c01f9981_110_0.png)

> 在某些浏览器中，如果表单内只有一个提交按钮，用户可以按回车键提交表单而不包含提交按钮的信息。

用户首次访问此页面时将看到一个表单。一旦提交表单且页面带有新的变量信息重新调用自己，只会显示感谢信息。

表单变量也可以通过 `$_HTTP_POST` 或 `$_HTTP_GET` 数组访问，取决于你在表单中使用的方法。如果你有变量来自这两种方法、如果表单变量可能与脚本中的变量同名，或者你传递了一组未定义的变量并需要检查其中的内容，那么这些数组就会非常方便。

### 第二部分：使用 PHP 工作

![](img/245156cc770929860a3ede93c01f9981_112_0.png)

注意在“name”属性中，我们添加了左括号和右括号（[]）。这告诉 PHP 期望接收一个数组。如果不包含括号，可能会有两个值争夺同一个变量名，这完全不可行。

一旦提交，你就可以像处理其他数组一样处理这个数组。

```php
if (is_array($sj_names)) {
    echo "the select values are:<br> <br>";
    while(list($key, $value) = each($sj_names)) {
        echo $value . "<br\n";
    }
}
```

当你希望向用户展示一系列复选框时（用户在按下提交按钮前可能会勾选或不勾选），此时传递数组也是很有用的。在第 8 章中，这是一个页面示例，允许程序管理员使用复选框选择将删除哪些条目。图 4-2 显示了此类页面的示例。如果我们为每个复选框分配不同的名称，就必须逐个检查每一个。而使用数组，我们写一个三行的循环就可以检查所有项。

图 4-1：多选框列表

# 第 4 章：PHP 入门 — 变量

![](img/245156cc770929860a3ede93c01f9981_113_0.png)

## 编辑留言板

从表单传递的数组也可以具有关联键，这些键可以是多维的。表元素的名称应采用 `name="array_name[element_name]"`。对于多维数组，格式为 `array_name[element_name][subelement_name]`。

### Cookies

Cookies 是存储在用户硬盘上的微小信息。如果你放置了 Cookie，它就包含一段可以被 Web 服务器读取的文本。Cookies 是在多次访问期间跟踪用户的**唯一方法**。请记住，Web 是无状态的环境。你的 Web 服务器实际上并不知道是谁在请求页面。Cookies 帮助你在用户在你的网站中移动时跟踪他们。

当 Cookie 存在时，它们会成为发送到 Web 服务器的 HTTP 请求的一部分。但首先，你需要设置一个 Cookie。开发者像处理 PHP 中其他所有内容一样，将其变得极其简单。使用 `setcookie()` 函数。该函数接受以下参数：

```php
setcookie(name, value, time_to_expire, path, domain, security setting);
```

图 4-2：一系列关联键

我们将在第 6 章中详细讨论这一点，但目前只需要说以下语句

```php
setcookie("mycookie", "my_id", time()+(60*60*24), "/", "mydomain.com", 0)
```

将设置一个带有以下参数的 Cookie：

- 存储一个名为 `my_id` 的变量
- `mycookie` 的值为 "my_id"
- Cookie 将在设置时间起 30 天后过期（当前时间 + 30 天的秒数）。
- Cookie 将适用于域内的每个页面。我们可以通过包含路径将其限制在域内的内的特定路径。
- 它适用于所有具有 `mydomain.com` 地址的站点。
- 没有特殊的安全设置。

一旦设置了 Cookie，从 Cookie 中检索的变量的行为与从表单元素检索的变量完全相同。它们将自动变成全局变量。在 PHP 脚本放置 Cookie 后，域内的其他脚本可以直接访问它。

如果你想确保 `$mycookie` 不与另一个名为 `$mycookie` 的变量冲突，可以通过 `HTTP_COOKIE_VARS` 数组来访问它，使用 `HTTP_COOKIE_VARS['mycookie']`。你可以设置可以作为数组访问的 Cookie：

```php
setcookie("mycookie[first]");
```

这些变量可以作为关联数组被访问。

![](img/245156cc770929860a3ede93c01f9981_114_0.png)

> 前述代码在 PC 的 Internet Explorer 5 上运行良好。然而，这在其他浏览器上可能不起作用。在任何情况下，你可能最好避免在 Cookie 中使用数组的情况。

## Sessions

PHP4 像 ASP 和 ColdFusion 一样原生支持 session，但它做得好得多。什么是 session？基本上，它是维持页面间状态的另一种方式。你的脚本应该用 `session_start()` 函数启动 session。在那个点，PHP 会注册一个唯一的 session ID，通常该 ID 会通过 cookie 发送给用户。PHP 在服务器上创建一个相应的文件，该文件可以跟踪任何变量。该文件名与 session ID 相同。

一旦启动 session，你就可以注册任意数量的变量。这些变量的值保存在服务器上的文件中。只要 session 存在，这些变量对于同一域内想要访问它们的任何页面都是可用的。这比通过表单元素或大量数据在页面之间传递变量要方便得多。

在完成工作后删除此页面是个好主意。没必要提供比绝对更多的饼干。
你可以以多种方式使用这种各种变量。我们将查看这些变量的一些，并展示如何使用它们。某些变量来自 PHP 引擎，其他源自你的 Web 服务器。

### PHP 变量

这些是可以通过 PHP 使用的变量。

#### PHP_SELF

这是正在运行的文件地址。通常，它是从 ServerRoot 目录提供的完整路径，这当表单在同一个 PHP 页面中既显示又处理时非常有用。

```php
<?
if(isset($sum)) {
    //在此处进行某些表单处理
    echo "thanks for the submission";
} else {
?>
<form name=myform method=post action=<?php echoPHP_SELF;?>
  <input type=text name=first_name> first name<br>
  <input type=text name=last_name> last name<br>
  <input type=submit name=submit value=submit>
</form>
<?php
}
?>
```

请记住，`PHP_SELF` 始终指向 URL 中正在执行的脚本名称。在包含（include）文件中，`PHP_SELF` 不会指向被包含的文件。它将指向正在运行的脚本。

值得注意的是，当 PHP 在 Windows 或 CGI 模块上运行时，`PHP_SELF` 的行为会很奇怪。请确保查看 `phpinfo()` 以查看你系统上的 `$_PHP_SELF` 的值。

#### HTTP_POST_VARS

这是一个包含通过 POST 方法发送的所有变量的数组，通常通过表单发送。你可以像访问关联数组元素一样访问每个单独变量（例如 `$_PHP_POST_VARS["idname"]`）。

#### HTTP_GET_VARS

这是一个包含通过 GET 方法发送的所有变量的数组。你可以像访问关联数组元素一样访问每个单独变量（例如 `$_PHP_GET_VARS["idname"]`）。

#### HTTP_COOKIE_VARS

发送到浏览器的所有 cookie 都可以在此关联数组中被读取。这包括会话 cookie。如果你好奇你的 cookie 是如何的，`phpinfo()` 将为你快速读取浏览器发送到服务器的 cookie。

### Apache 变量

Apache 跟踪着几十个变量。我们无法在这里列出完整的变量列表，因为你使用的变量取决于你当前的设置。以下是一些你可能在脚本中频繁使用的变量。

当你你查看此列表和 `phpinfo()` 时，请记住，如果你没有从服务器变量中获得你想要的内容，你需要修改服务器配置，而不是 PHP。PHP 只是传递信息并可以修改这些变量。

#### DOCUMENT_ROOT

此变量返回指向 Web 服务器根目录的路径。对于大多数 Apache 用户来说，此目录将类似于 `/path/to/hdfs`。我们在本书中使用此变量来使我们的应用程序具有移植性。以此包含语句为例：

```php
include="DOCUMENT_ROOT/book/functions/charset.php";
```

通过使用 `DOCUMENT_ROOT` 变量而不是绝对路径，我们可以将书籍目录及其所有子文件夹移动到任何其他 Apache 服务器，而必担心包含语句会损坏。请记住，如果你使用的是 Apache以外的 Web 服务器，`DOCUMENT_ROOT` 可能不可用。

> 如果你在 `php.ini` 文件中设置了 `include_path` 目录，你就不需要担心在 include 语句中指定任何路径——PHP 将查找你指定的所有目录并尝试找到你指定的文件。

![](img/245156cc770929860a3ede93c01f9981_119_0.png)

#### HTTP_REFERER

此变量包含当前查看页面之前的页面的 URL。`HTTP_REFERER` 并不是每个请求都有 referer（引用页）。如果有人在浏览器中输入 URL，或者通过书签访问你的页面，则不会发送 referer。此变量可以用于显示定制化信息。如果你与另一个站点有关系，并希望为来自该域名的引用提供特殊的、自定义的标头，你可能会使用像这样的脚本

```php
//检查我的用户是否来自 my_partners_domain.com
if(ereg("http.*my_partners_domain.com.*", $_HTTP_REFERER))
{
    include'fancy_header.php';
} else{
  include'normal_header.php';
}
```

请记住，`HTTP_REFERER` 是臭名的不可靠。在某些情况下，不同的浏览器会提供不同的 `HTTP_REFERER`。它也很容易被伪造。因此，你不想使用像上面的脚本来确保信息的安全。我曾工作过一个网站，其中 `HTTP_REFERER` 用于判断页头中应该包含一个特殊的 GIF。

#### HTTP_USER_AGENT

任何构建过 Web 页面的人都知道浏览器检测有多重要。某些浏览器会在 JavaScript 上卡住，而其他浏览器则需要非常简单的文本。`user_agent` 字符串是你向正确的人提供正确内容的密钥。一个典型的 `user_agent` 字符串看起来像这样：

```
Mozilla/4.0 (compatible; MSIE 5.01; Windows 98)
```

你可以解析此字符串来获取你需要的内容。

你可能对 PHP 的 `get_browser()` 函数感兴趣。理论上，此函数将确定你的用户浏览器的功能，这样你就可以发现脚本是否可以安全地提供（例如框架或 JavaScript。PHP 手册中有关于 `get_browser()` 的安装和使用说明，但我不建议使用它。为什么？使用 `get_browser()`，你会被告知 PC 版 Internet Explorer 5 和 Mac 版 Netscape Navigator 4.01 都支持 CSS（层联样式表）和 JavaScript。但任何有客户端经验的人都知道，在这两个浏览器上编写代码是一项艰巨的任务（而且非常痛苦）。你从 `get_browser()` 获得的信息可能会导致虚假的安全感。最好访问 `HTTP_USER_AGENT` 并根据特定的浏览器和平台做出决定。

#### REMOTE_ADDR

这是发送 HTTP 请求的用户的 IP。`REMOTE_ADDR` 很容易被伪造，并且并不一定为用户提供信息。你可能想使用它进行跟踪，但不应将其用于安全。

#### REMOTE_HOST

这是发送请求的主机。当我通过我的 ISP (att.net) 拨号时，`REMOTE_HOST` 看起来像这样：119.san-francisco-18-19rs.ca.dial-access.att.net，`REMOTE_HOST` 通常不可用。

#### REQUEST_URI

这与 `PHP_SELF` 非常相同，但它除了脚本名称外还包含了查询字符串中的信息。它包含了从根路径开始的所有内容。所以如果你访问 http://www.mydomain.com/info/products/index.php?id=6，`REQUEST_URI` 将等于 `/info/products/index.php?id=6`。

#### SCRIPT_FILENAME

此变量包含文件的完整路径。

### 其他服务器变量

正如前面提到的，`phpinfo()` 是你的朋友。在 Unix 系统上运行 MySQL 查询时，你会看到与 Web 服务器相关的变量。但是，在 Windows 上使用 include 语句时，你会看到 `DOCUMENT_ROOT` 变量。图 4 给出了一些你可以使用的变量。

![](img/245156cc770929860a3ede93c01f9981_121_0.png)

图 4-4：服务器变量

### 测试变量

在本章的开头，我们展示了将数据赋值给变量确定类型。变量的外观并没有指示它包含什么。如果你在脚本中看到 `$var`，你不知道它是一个字符串、整数、浮点数还是数组。事实上，在许多脚本中，你无法确定它是否包含值，或者是否存在。由于这些原因，你需要进行测试。接下来的章节描述了你可以进行的测试类型。

#### isset()

此函数测试变量是否有任何值，包括空字符串。如果变量没有初始化或未设置，`isset()` 将失败。

考虑以下处理 MySQL 查询的脚本。你已经知道数据库文件可能包含空字符串和空值。在你的脚本中，你可能想区别对待两者。要在查询遇到空值时打印特殊消息，你需要使用 `isset()`。在此代码中，`$query` 是输入到表单元素中的选择语句。

```php
$result = mysql_query($query) or
die($mysql_error());
```

```php
$number_cols = mysql_num_fields($result);
echo "<header> $query<br></header>\n";//布局页头
echo "<table border = 1>\n";
echo "<tr align=center>\n";
for ($i=0; $i<$number_cols; $i++) {
    echo "<<th>>", $mysql_field_name($i), $i, "</th>\n";
}
echo "</tr></table>\n";//布局表格表头
//布局表格正体
while ($row = mysql_fetch_row($result)) {
    echo "<tr align=left\n";
    for ($i=0; $i<$number_cols; $i++) {
        echo "<td>";
        if (!isset($row[$i])) //测试空值
            echo "NULL";
    }
}
```

```php
else
    echo $row[$i];
    echo "<td>\n";
}
echo "</tr>\n";
}
echo "</table>";
```

注意，感叹号 (!) 表示“非”。因此，`if(!isset($var))` 句语会在变量未设置时测试为真。
如果你想销毁变量，请使用 `unset` 函数。

#### empty()

`empty()` 函数与 `isset()` 函数功能重叠。如果变量未设置、包含空字符串或值为 0，它将测试为真。它通常用于处理表单数据等操作。如果你想判断用户是否在文本框中输入了内容，可以使用如下代码：

```php
if(empty($first_name))
{
    echo "Please enter your first name. It is a required field";
    exit;
}
```
