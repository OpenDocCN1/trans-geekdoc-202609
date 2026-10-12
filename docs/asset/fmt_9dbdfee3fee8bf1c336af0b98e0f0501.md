
`$GLOBALS` 数组是一个关联数组，全局变量的名称作为键，该变量的内容作为数组元素的值。请注意 `$GLOBALS` 存在于任何作用域中，这是因为 `$GLOBALS` 是一个超全局变量。

这意味着 `log_message()` 函数可以重写为：

```
function log_message ( $message ) {
    // 通过 $GLOBALS 数组访问全局 $amount_of_log_calls 变量。无需 'global $GLOBALS;'，因为它
}
```

有人可能会问，既然 `global` 关键字也可以用来获取全局变量的值，为什么还要使用 `$GLOBALS` 数组？主要原因是使用 `global` 关键字会将变量引入当前作用域。这样你就无法在局部作用域中重复使用相同的变量名。

## 第 4 章：PHP 超全局变量

超全局变量是内置变量，它们在所有作用域中始终可用。

PHP 中的几个预定义变量是“超全局”的，这意味着它们在脚本的所有作用域中都可用。无需执行 `global $variable;` 即可在函数或方法中访问它们。

### 第 4.1 节：超全局变量详解

#### 简介

简单来说，这些变量在你的脚本的所有作用域中都可用。

这意味着不需要将它们作为参数传递给函数，也不需要将它们存储在代码块外部以便在不同作用域中使用。

#### 什么是超全局变量？？

如果你认为它们像超级英雄——它们不是。

截至 PHP 7.1.3 版本，共有 9 个超全局变量。它们如下：

*   `$GLOBALS` \- 引用全局作用域中所有可用的变量
*   `$_SERVER` \- 服务器和执行环境信息
*   `$_GET` \- HTTP GET 变量
*   `$_POST` \- HTTP POST 变量
*   `$_FILES` \- HTTP 文件上传变量
*   `$_COOKIE` \- HTTP Cookies
*   `$_SESSION` \- Session 变量
*   `$_REQUEST` \- HTTP 请求变量
*   `$_ENV` \- 环境变量

请参阅 [文档](http://php.net/manual/en/language.variables.superglobals.php)。

Tell me more, tell me more

抱歉引用了《Grease》（注：音乐剧/电影《油脂》中的歌词）！[链接](https://www.youtube.com/watch?v=ZW0DfsCzfq4)

是时候对这些“超级英雄全局变量”进行一些解释了。

#### $GLOBALS

一个关联数组，包含对当前脚本全局作用域中定义的所有变量的引用。变量名是数组的键。

##### 代码

```php
<?php
$myGlobal = "global";
function test() {
    $myLocal = "local";
    var_dump($GLOBALS);
}
test();
?>
```

##### 输出

```
array(2) {
  ["myGlobal"]=>
  string(6) "global"
  ["myLocal"]=>
  string(5) "local"
}
```

在上面的示例中，`$myLocal` 第二次没有显示，因为它是在 `test()` 函数内部声明的，并在函数结束后被销毁。

##### 变为全局

为了解决这个问题，有两种选择。

```
global $myLocal;
$myLocal = "local";
```

`global` 关键字是变量的前缀，强制其成为全局作用域的一部分。

请注意，你不能在同一语句中使用 `global` 关键字的同时给变量赋值。因此，我不得不在下面单独赋值。（如果你去掉换行和空格也是可以的，但我不认为这很整洁。`global $myLocal; $myLocal = "local";`）。

```
$GLOBALS["myLocal"]
```

在这个例子中，我将 `$myLocal` 重新赋值为 `$GLOBALS["myLocal"]`，因为我发现写变量名比写关联数组更容易。

#### $_SERVER

`$_SERVER` 是一个包含诸如头信息、路径和脚本位置等信息的数组。该数组中的条目由 Web 服务器创建。无法保证每个 Web 服务器都会提供所有这些信息；服务器可能会省略某些条目，或提供此处未列出的其他条目。尽管如此，这些变量中的很大一部分在 [CGI/1.1 规范](http://www.faqs.org/rfcs/rfc3875) 中都有规定，所以你可以期望这些变量存在。

其输出示例可能如下所示（在我的 Windows PC 上使用 WAMP 运行）

```
C:\wamp64\www\test.php:2:
array (size=36)
  'HTTP_HOST' => string 'localhost' (length=9)
  'HTTP_CONNECTION' => string 'keep-alive' (length=10)
  'HTTP_CACHE_CONTROL' => string 'max-age=0' (length=9)
  'HTTP_UPGRADE_INSECURE_REQUESTS' => string '1' (length=1)
  'HTTP_USER_AGENT' => string 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/57.0.2987.133 Safari/537.36' (length=110)
  'HTTP_ACCEPT' => string 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8' (length=74)
  'HTTP_ACCEPT_ENCODING' => string 'gzip, deflate, sdch, br' (length=23)
  'HTTP_ACCEPT_LANGUAGE' => string 'en-US,en;q=0.8,en-GB;q=0.6' (length=26)
  'HTTP_COOKIE' => string 'PHPSESSID=0gslnvgsci371ete9hg7k9ivc6' (length=36)
  'PATH' => string 'C:\Program Files (x86)\NVIDIA Corporation\PhysX\Common;C:\Program Files (x86)\Intel\iCLS Client\;C:\Program Files\Intel\iCLS Client\;C:\ProgramData\Oracle\Java\javapath;C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\WINDOWS\System32\WindowsPowerShell\v1.0\;E:\Program Files\ATI Technologies\ATI.ACE\Core-Static;E:\Program Files\AMD\ATI.ACE\Core-Static;C:\Program Files (x86)\AMD\ATI.ACE\Core-Static;C:\Program Files (x86)\ATI Technologies\ATI.ACE\Core-Static;C:\Program Files\Intel\Intel(R) Managemen'... (length=1169)
  'SystemRoot' => string 'C:\WINDOWS' (length=10)
  'COMSPEC' => string 'C:\WINDOWS\system32\cmd.exe' (length=27)
  'PATHEXT' => string '.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.PY' (length=57)
  'WINDIR' => string 'C:\WINDOWS' (length=10)
  'SERVER_SIGNATURE' => string '<address>Apache/2.4.23 (Win64) PHP/7.0.10 Server at localhost Port 80</address>' (length=80)
  'SERVER_SOFTWARE' => string 'Apache/2.4.23 (Win64) PHP/7.0.10' (length=32)
  'SERVER_NAME' => string 'localhost' (length=9)
  'SERVER_ADDR' => string '::1' (length=3)
  'SERVER_PORT' => string '80' (length=2)
  'REMOTE_ADDR' => string '::1' (length=3)
  'DOCUMENT_ROOT' => string 'C:/wamp64/www' (length=13)
  'REQUEST_SCHEME' => string 'http' (length=4)
  'CONTEXT_PREFIX' => string '' (length=0)
  'CONTEXT_DOCUMENT_ROOT' => string 'C:/wamp64/www' (length=13)
  'SERVER_ADMIN' => string 'wampserver@wampserver.invalid' (length=29)
  'SCRIPT_FILENAME' => string 'C:/wamp64/www/test.php' (length=26)
  'REMOTE_PORT' => string '5359' (length=4)
  'GATEWAY_INTERFACE' => string 'CGI/1.1' (length=7)
  'SERVER_PROTOCOL' => string 'HTTP/1.1' (length=8)
  'REQUEST_METHOD' => string 'GET' (length=3)
  'QUERY_STRING' => string '' (length=0)
  'REQUEST_URI' => string '/test.php' (length=13)
  'SCRIPT_NAME' => string '/test.php' (length=13)
  'PHP_SELF' => string '/test.php' (length=13)
  'REQUEST_TIME_FLOAT' => float 1491068771.413
  'REQUEST_TIME' => int 1491068771
```

这里有大量信息需要消化，所以我将在下面挑选一些重要的。如果你想了解所有变量，请查阅文档的 [索引部分](http://php.net/manual/en/reserved.variables.server.php#refsect1-reserved.variables.server-indices)。

也许有一天我会把它们都加上。或者有人可以编辑并在下面添加好的解释？暗示，暗示 ;) 对于下面所有的解释，假设 URL 为 [`www.example.com/index.php`](http://www.example.com/index.php)

##### HTTP_HOST \- 主机地址。

```
www.example.com
```

这将返回

```
93.184.216.34
```

##### SCRIPT_NAME \- 当前脚本的路径。

```
/index.php
```

##### HTTP_USER_AGENT

用户代理的内容。这是一个字符串，包含关于客户端浏览器的所有信息，包括操作系统。

##### HTTP_COOKIE

所有 Cookie 连接成的一个字符串，以分号作为分隔符。

##### SERVER_ADDR

当前脚本运行所在服务器的 IP 地址。

##### PHP_SELF

当前执行脚本的文件名，相对于文档根目录。

这将返回 `/`

##### REQUEST_TIME_FLOAT

请求开始的时间戳，具有微秒精度。自 PHP 5.4.0 起可用。

##### REQUEST_TIME

请求开始的时间戳。自 PHP 5.1.0 起可用。

#### $_GET

一个关联数组，包含通过 URL 参数传递给当前脚本的变量。

`$_GET` 是一个包含所有 URL 参数的数组；这些就是 URL 中 `?` 后面的任何内容。

以 [`www.example.com/index.php?myVar=myVal`](http://www.example.com/index.php?myVar=myVal) 为例。可以通过按此格式 `$_GET["myVar"]` 访问来获取该 URL 中的信息，结果将是 `myVal`。

给不喜欢阅读文字的人看点代码。

```php
// URL = http://www.example.com/index.php?myVar=myVal
echo $_GET["myVar"] == "myVal" ? "true" : "false"; // 返回 "true"
```

上面的例子使用了三元运算符。

这展示了如何使用 `$_GET` 超全局变量访问 URL 中的值。

再来一个例子！

可以通过用 `&` 字符分隔，在 URL 中发送多个变量。

##### 安全风险

**非常重要**：不要通过 URL 发送任何敏感信息，因为它会保留在计算机的历史记录中，任何能访问该浏览器的人都能看到。

#### $_POST

一个关联数组，包含通过 HTTP POST 方法传递给当前脚本的变量，前提是请求中的 HTTP Content-Type 为 `application/x-www-form-urlencoded` 或 `multipart/form-data`。

与 `$_GET` 非常相似，都是将数据从一处发送到另一处。

我将直接从一个例子开始。（我省略了 `action` 属性，因为这会将信息发送到包含该表单的页面）。

以上是一个用于发送数据的基本表单。在真实环境中，`value` 属性不会被设置，这意味着表单将是空白的。然后它会发送用户输入的任何信息。

##### 安全风险

通过 POST 发送数据也不安全。使用 HTTPS 将确保数据更安全。

#### $_FILES

一个关联数组，包含通过 HTTP POST 方法上传到当前脚本的项目。该数组的结构在 [POST 方法上传](http://php.net/manual/en/features.file-upload.post-method.php) 章节中有概述。

让我们从一个基本表单开始。

注意我省略了 `action` 属性（又是！）。另外，我添加了 `enctype`，这对任何处理文件上传的表单都很重要。

这用于上传单个文件。有时你可能想上传多个文件。为此有一个属性，叫做 `multiple`。

几乎任何东西都有属性。[抱歉了](https://www.youtube.com/watch?v=szrsfeyLzyg) 下面是一个提交多个文件的表单示例。

注意这里的更改；只有几处。

输入名称带有方括号。这是因为它现在是一个文件数组，所以我们告诉表单：`$_FILES["myVar"]` 创建所选文件的数组。省略方括号将导致最后一个文件被设置为 `$_FILES["myVar"]`。

这是一个非常简单的例子，不处理诸如不允许的文件扩展名或以 PHP 代码命名的文件（如 SQL 注入的 PHP 等价物）等问题。请参阅文档。

第一步是检查是否有文件，如果有，将总数设置为 `$total`。

使用 `for` 循环可以遍历 `$_FILES` 数组并一次访问每一项。如果该文件没有遇到问题，则 `if` 语句为真，并运行单文件上传的代码。

如果遇到问题，则执行 `switch` 块，并根据该特定上传的错误显示错误信息。

#### $_COOKIE

一个关联数组，包含通过 HTTP Cookie 传递给当前脚本的变量。

Cookie 是包含数据并存储在客户端计算机上的变量。

与前述超全局变量不同，Cookie 必须通过函数创建（而不是通过赋值）。约定如下。

在本例中，为 Cookie 指定了一个名称（本例中为 `"myVar"`），一个值（本例中为 `"myVal"`，但也可以传递一个变量将其值赋给 Cookie），以及一个过期时间（本例中为一小时，因为 3600 秒是一分钟——*原文此处有误，3600 秒为一小时*）。

尽管创建 Cookie 的约定不同，但访问方式与其他超全局变量相同。
