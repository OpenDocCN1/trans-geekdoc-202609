

![](img/50e1558b8202f19b96c1cc386ea5ec66_287_0.png)

这应该足以帮助你追踪问题所在。然而，一些服务器运营商认为显示语法错误是一种安全风险，因为这可能会向黑客提供有关程序内部运作的线索（例如变量名或文件位置）。因此，他们配置服务器完全不显示语法错误。这意味着，如果你的 PHP 文件中存在语法错误，你看到的将只是一个空白屏幕。程序不会运行，但你也不会被告知原因。在这种情况下，你唯一现实的选择是更换另一台服务器。

需要注意的是，虽然服务器生成的语法错误会告诉你代码中包含错误的行号，但这个数字并不总是正确的。当你试图追踪问题时，它是一个很好的起点，但它并非不可出错。这是因为 PHP 往往假定错误发生在最后一个有效行的下一行。但这并不总是事实。这通常意味着指示的行号会“偏差” 1 或 2，尽管在罕见情况下（特别是如果你有一大段带括号的代码块，并且省略了一个括号或多加了一个括号），它可能会更不准确。

一个有用的技巧是，如果你被一个特别难缠的语法错误卡住了，可以使用“切分法”。将 PHP 文件拆分为两个大致长度相等的单独文件。只要你没有断开任何带括号的代码块，即只要开括号或闭括号没有出现在另一个文件中，你应该就是安全的。这些程序可能不会按你预期的方式工作，但这并不重要。重要的是，其中一个程序在访问时会生成语法错误，而另一个则不会。这样你就确切知道文件的哪一半包含错误。然后将该文件再拆分为 2 个部分，并重复此过程。最终，包含语法错误的“一半”会变得足够小，你应该能够认出问题所在。

### 编码错误

在追踪编码错误时，你最好的朋友是一个简单的 **echo** 语句，后面可能跟着 **exit()**。例如，在上述提到的情况下，在该行之前添加：

```php
echo $room[1];
exit();
```

当程序到达这一点时，它将显示变量的值，然后停止。当然，变量为空意味着你什么都看不到，所以你可能会更喜欢：

```php
echo "XYZ" . $room[1] ;
exit();
```

现在你可以查看生成的网页上的 XYZ，你就会知道房间号会显示在哪里旁边。

还有一个最后的补充，这也会有帮助。将代码更改为：

```php
echo "XYZ" . $room[1]; #debug
exit();                #debug
```

这样，一旦程序正常工作，你就可以轻松地搜索带有注释的行以将其删除。

如果所有这一切努力都没有把 bug 揪出来，那么请将你的调试代码移到文件更上方的位置，就在 $room[1] 最初定义的地方之后。希望在那一点它的值应该是正确的。所以，在那两个点之间的某个地方，它的值被改变了。剩下的就是依次将你的调试代码定位在每一行更改（或你认为可能会更改）$room[1] 值的地方之后。很有可能是，问题归结于一个简单的拼写错误，例如 rooms 而不是 room，或者 "1" 而不是 1。

如果你想输出整个数组的值而不是单个变量，你不需要编写 for... 循环来做这件事。PHP 内置了这样的功能。假设 $rooms 数组的一个或多个元素存在问题，你想查看整个数组而不仅仅是元素 1，请使用 var_dump。以下代码：

```php
<?php
$rooms[1] = "ABC";
$rooms[2] = "DEF";
$rooms[3] = "GHI";

echo "<pre>";
var_dump($rooms);
echo "</pre>";
?>
```

产生以下输出：

```
array(3) {
  [1]=>
  string(3) "ABC"
  [2]=>
  string(3) "DEF"
  [3]=>
  string(3) "GHI"
}
```

这告诉你该数组有 3 个元素。元素 [1] 是一个由 ABC 组成的 3 个字符的字符串。元素 2 是一个由 DEF 组成的 3 个字符的字符串，等等。

如果这仍然没有帮助，你可以再进一步，输出程序所知的所有变量的内容。只需这样做：

```php
echo "<pre>";
var_dump(get_defined_vars());
echo "</pre>";
```

这样做有效，因为有一个 PHP 函数可以创建一个包含所有变量的数组。所以我们调用这个函数，然后使用 var_dump 来显示该数组。至于其他两行，<pre> 标签告诉 Web 浏览器它被要求显示预格式化文本，通常在显示程序列表等场合使用。相信我，var_dump 的输出如果用这样的标签包围起来，可读性会好得多。

虽然这也产生了 rooms 数组内容的列表，但它出现在一个非常长的（多达数百行）许多其他变量的列表末尾。这些不是你的程序创建的变量，而是 Web 服务器和 PHP 用于其内部目的使用的变量。其中一些非常有用的。例如，看看 this extract from the list that is returned on the the-web-book.com server:

```
["_SERVER"]=>
array(31) {
  ["DOCUMENT_ROOT"]=>
  string(27) "/home//thewebbbo/public_html"
  ["GATEWAY_INTERFACE"]=>
  string(7) "CGI/1.1"
  ["HTTP_ACCEPT"]=>
  string(22) "image/jpeg, application/x-ms-application, image/gif, application/xaml+"
  ["HTTP_ACCEPT_ENCODING"]=>
  string(13) "gzip, deflate"
  ["HTTP_ACCEPT_LANGUAGE"]=>
  string(5) "en-GB"
  ["HTTP_CACHE_CONTROL"]=>
  string(14) "max-age=259200"
  ["HTTP_CONNECTION"]=>
  string(10) "keep-alive"
  ["HTTP_HOST"]=>
  string(20) "www.the-web-book.com"
  ["HTTP_USER_AGENT"]=>
  string(151) "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; SLCC2;
  ["HTTP_VIA"]=>
  string(61) "1.1 sulafat.brighton.ac.uk:8080 (squid/2.5.STABLE12-20051129)"
  ["HTTP_X_FORWARDED_FOR"]=>
  string(13) "194.83.112.39"
  ["PATH"]=>
  string(13) "/bin:/usr/bin"
  ["QUERY_STRING"]=>
  string(0) ""
  ["REDIRECT_STATUS"]=>
  string(3) "200"
  ["REMOTE_ADDR"]=>
  string(13) "194.81.199.59"
  ["REMOTE_PORT"]=>
  string(5) "64425"
  ["REQUEST_METHOD"]=>
  string(3) "GET"
  ["REQUEST_URI"]=>
  string(14) "/breakfast.php"
```

正如你可以从第一行看到的那样，这一部分与 $_SERVER[] 数组的内容有关，该数组包含 31 个元素。在这个列表的最底部，名为 “REQUEST_URI” 的元素（记住元素名称不必是数字），似乎包含我们程序文件的名称。让我们编写如下程序来验证一下：

```php
<?php
echo $_SERVER["REQUEST_URI"];
?>
```

结果如下：

![](img/50e1558b8202f19b96c1cc386ea5ec66_291_0.png)

这在下一章中我们将详细讨论的原因下极其有用。

## $_SERVER 变量

$_SERVER[] 数组中还有许多其他有用的项目。让我们用 var_dump($_SERVER) 调用查看一下。这给我们：

```
array(31) [
  ["DOCUMENT_ROOT"] => string(27) "home7//theWebbo/public_html" ["GATEWAY_INTERFACE"] => string(7) "CGI/1.1" ["HTTP_ACCEPT"] => string(22) "text/ms-apple, image/g, ap lication/vnd.wap.ms-app, image/page, application/vnd.ms-excel, application/vnd.ms-powerpoint, app lica25920" ["HTTP_ENCODING"] => string(13) "gzip, deflate" ["HTTP_ACCEPT_LANGUAGE"] => string(5) "en-GB" ["HTTP_CACHE_CONTROL"] => string(14) "max-age=25920" ["HTTP_CONNECTION"] => string(10) "Keep-Alive" ["HTTP_HOST"] => string(20) "www.the-web-book.com" ["HTTP_USER_AGENT"] => string(151) "Media 8, 0, Windows NT 6.1, Trident/4, 0, SLCC2, NET CLR 2.0, 50727, NET CLR 3.5.30729, NET CLR 3.0, 30729, Media Center PC 6.0" ["HTTP_VIA"] => string(60) "1.1 masi cqued25 STABLE2.2.0051129)" ["HTTP_X_FORWARDED_FOR"] => string(13) "194.83.112.39" ["PATH"] => string(13) "bin; etc;" ["QUERY_STRING"] => string(0) "" ["REDIRECT_STATUS"] => string(3) "200" ["REMOTE_ADDR"] => string(13) "194.81.199,56" ["REMOTE_PORT"] => string(5) "31986" ["REQUEST_METHOD"] => strin G(5) "GET" ["REQUEST_URI"] => string(11) "test99.php" ["SCRIPT_FILENAME"] => string(38) "home7//theWebbo/public_html/test99.php" ["SCRIPT_NAME"] => string(11) "/test99.php" ["SERVER_ADDR"] => string(14) "167.417.140,168" ["SERVER_ADMIN"] => string(26) "webmaster@theWeb-book.com" ["SERVER_NAME"] => string(20) "www book.com" ["SERVER_PORT"] => string(2) "80" ["SERVER_PROTOCOL"] => string(8) "HTTP/1.1" ["SERVER_SIGNATURE"] => string(79) "Apache/2.2.21 (Unix) mod_ssl/2.2.11 OpenSSL/0.9,8k_DAT/2 mod_auth_passthrough/2,1, mod, bwiimited/1.4 FrontPage/5.0.2.2635 Server at www-the-web-book.com Port 2635" ["SERVER_SOFTWARE"] => string(120) "Apache/2.2.11 (Unix) mod_ssl/2.2.11 OpenSSL/0.9,8k_DAT/2 mod, auth_passthrough/2.1 mod, bwiimited/1.4 FrontPage/5.0.2.2635" ["SERVER_SOFTWARE"] => string(120) "Apache/2.2.11 (Unix) mod_ssl/2.2.11 OpenSSL/0.9,8k_DAT/2 mod, auth_passthrough/2.1 mod, bwiimited/1.4 FrontPage/5.0.2.2635" ["REQUEST_TIME"] => sat(129398676)
```

哎呀，如果你忘记 <pre> 标签就会发生这种情况！让我们再试一次：

```
array(32) {
["DOCUMENT_ROOT"] =>
string(27) "/home7//theWebbo/public_html"
["GATEWAY_INTERFACE"] =>
string(7) "CGI/1.1"
["HTTP_ACCEPT"] =>
string(3) "*/ *"
["HTTP_ACCEPT_ENCODING"] =>
string(13) "gzip, deflate"
["HTTP_ACCEPT_LANGUAGE"] =>
string(5) "en-GB"
["HTTP_CACHE_CONTROL"] =>
string(14) "max-age=25920"
["HTTP_CONNECTION"] =>
string(10) "keep-alive"
["HTTP_HOST"] =>
string(20) "www.the-web-book.com"
["HTTP_PRAGMA"] =>
string(8) "no-cache"
["HTTP_USER_AGENT"] =>
```

