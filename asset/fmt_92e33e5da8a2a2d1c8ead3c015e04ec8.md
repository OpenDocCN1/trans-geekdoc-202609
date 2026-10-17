
```
?>
</body></html>
```

这段代码可以在`www.tworks.com/phpbook`获取，如果你使用的是 PHP 4.1 或更高版本，它适用于测试你的会话。（如果你使用的是 4.1 之前的版本或倾向于通过会话使用全局变量，请参见本节稍后部分的列表 24-2）。在获得计数后，你应该首先测试它是否无错误加载。页面应该看起来如图 24-1 所示。之后，为了检查基于 Cookie 的会话是否正常，只需在浏览器中重新加载或刷新页面。你应该能看到一个类似于图 24-2 的页面。

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_503_0.png)

**图 24-1**：会话测试页面

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_504_0.png)

**图 24-2**：会话测试页面，第二次访问

如果你第二次访问的结果是图 24-2，则基于 Cookie 的会话支持正常。如果它看起来仍然像图 24-1，则 PHP 没有检测到你的会话。请确保你测试的浏览器已配置接受 Cookie，并查看本页末尾的“Cookies 与故障排除”部分。

| 函数 | 行为 |
|---|---|
| `session_name()` | 当不带参数调用时，返回当前的会话名称字符串。默认通常为`PHPSESSID`。当带一个参数调用时，`session_name()`将当前会话名称设置为该字符串。此名称被用作键，在 cookies 和 GET/POST 参数中查找会话 ID——为了能够成功检索，该名称必须与值序列化时的名称一致。请注意，除非你需要区分由同一 Web 服务器提供的不同会话类型（例如在多个跟踪会话的站点的情况下），否则无需更改会话名称。每当脚本执行时，会话名称都会重置为默认，因此任何名称更改必须发生在每个使用该名称的脚本中，并在调用任何其他会话函数之前。 |
| `session_module_name()` | 如果没有提供参数，返回负责处理会话数据的模块名称。目前默认为`files`，这意味着会话绑定将被序列化并写入到由`session_save_path()`函数指定的目录文件中。如果提供了参数，则将模块更改为该参数。（这可以是，例如用于用户自定义数据库的`user`，但除非你清楚自己在做什么，否则不会进行更改。） |
| `session_save_path()` | 返回（或如果提供了参数，则返回）写入会话变量绑定文件所在的目录路径（通常在 Unix 系统上默认为`/tmp`）。该目录必须存在，并且具有 PHP 写入文件的权限。在 Windows 系统上，在使用会话之前，你必须将其更改为有效路径！ |
| `session_id()` | 不接受参数并返回一个字符串，该字符串是对应特定会话的唯一键。如果提供了字符串参数，则会将会话 ID 设置为此值。 |
| `session_regenerate_id()` | 不接受参数并设置一个新的会话 ID，在必要时设置新的 cookie，并在成功时返回`TRUE`或失败时返回`FALSE`。与`session_id()`不同，它不返回带有实际 ID 的字符串。 |
| `session_encode()` | 返回一个编码当前会话状态的字符串，适用于`session_decode()`使用。它可以用于保存会话以便在稍后的某个时间恢复，例如将编码后的字符串写入文件或数据库。 |
| `session_decode()` | 接收由`session_encode()`生成的编码字符串并重新建立会话状态，像`session_start`一样将会话绑定转换为页面绑定。 |
| `session_get_cookie_params()` | 返回一个包含当前会话数据的数组：`lifetime`（以秒为单位，直到过期，0 表示永不过期）、`path`（cookie 有效路径）、`domain`（cookie 有效域名）、`secure`（cookie 是否会通过 SSL 连接发送）。这些参数通常在`php.ini`文件中设置，但可以通过`set_cookie_params()`为单个会话更改。 |
| `session_set_cookie_params()` | 接受四个参数：`int`类型`lifetime`（过期时间，0 表示永不过期）、`string`类型`path`（cookie 有效路径）、`string`类型`domain`（cookie 有效域名）、`boolean`类型`secure`（是否会通过 SSL 连接发送）。确保在`path`参数中包含尾随斜杠。 |

## 配置问题

表 24-2 中的变量可以在`php.ini`文件中设置，也可以通过调用`phpinfo()`进行设置。我们提供了描述和典型的默认值（某些默认值取决于平台）。

### 表 24-2：会话配置变量

| `php.ini` 变量 | 典型值 | 描述 |
|---|---|---|
| `session.save_path` | Unix 系统下的`/tmp` | 写入会话数据的服务器端目录路径。Windows 系统必须更改此项 |
| `session.auto_start` | 0 | 当为 1 时，每次运行脚本都会初始化会话。当为 0 时，除非显式调用`session_start()`或`session_register()`，否则将没有可用会话数据。 |
| `session.save_handler` | `files`、`user` | 决定保存会话变量信息的底层方法的字符串。不建议普通用户更改此项。 |
| `session.cookie_lifetime` | 0 | 指定会话 cookie 过期需要多久，因此决定了会话的寿命。默认 0 表示会话持续到浏览器关闭——任何其他值都表示允许会话持续的秒数。 |
| `session.use_cookies` | 1 | 如果为 1，会话机制将尝试通过设置/检查 cookie 来传播会话 ID。（如果浏览器拒绝 cookie，则可能使用 GET/POST。）如果此变量为 0，则不尝试使用 cookie |

## Cookies

> **交叉引用**：Cookie 的许多用途等同于会话跟踪——在单个用户浏览过你的站点时，跟踪某些信息。如果你被诱导使用 cookie 来实现此类目的，并且你正在使用 PHP4，你可能想要考虑使用本章后面“基于 Cookie 的自定义会话”部分中介绍的内置会话函数。它们不仅提供了更好的抽象层级，而且具有内置的回退机制，通过 GET/POST 请求传播信息来处理拒绝 cookie 的情况。

Cookie 是保留在客户端的一小段信息。

> **注意**：作为一般规则，你希望在客户端机器上存储信息。在 PHP 中，使用`setcookie()`设置 cookie。在 PHP 4.1 及更高版本中，名称和值会出现在全局变量`$_COOKIE`中，以 cookie 名称作为索引，以值为值。

### setcookie() 函数

只有一个相关的函数，称为`setcookie()`。表 24-3 显示了它的参数，所有参数都是可选的。

| 参数名称 | 预期类型 | 含义 |
|---|---|---|
| `name` | `string` | cookie 的名称（类比变量名）。 |
| `value` | `string` | 你想存储在 cookie 中的值（类比赋值变量的值）。如果未提供此参数，则删除由第一个参数命名的 cookie。 |
| `expire` | `int` | 指定 cookie 何时过期。值 0（默认值）表示它将持续到浏览器关闭。任何其他整数都被解释为 cookie 过期的绝对时间（由`time()`函数返回的时间）。 |
| `path` | `string` | 在默认情况下，该域名下的任何页面都可以设置（并看到）你的 cookie。将路径设置为子目录（例如`/forum/`）可以区分具有相同名称但由不同站点或子域名设置的 cookie（在这种情况下，cookie 只对论坛区域有效）。最好在路径中包含尾随斜杠 |
| `domain` | `string` | 在默认情况下，不对客户端请求的域名进行检查。如果此参数不为空，则域名必须匹配。例如，如果同一台服务器提供`www.mysteryguide.com`和`forum.mysteryguide.com`，一个站点的缓存可以确保另一个站点读取（或设置）它的 cookie，只需在此参数中包含`forum.mysteryguide.com` |
| `secure` | `int`（0 或 1） | 默认值为 0。如果此参数为 1，cookie 将通过安全套接字（如 SSL 或 HTTPS）发送。请注意，在设置此类 cookie 之前必须已经运行安全连接 |

有关使用`expire`参数表示时间的详细信息，请参阅第 23 章，特别是关于`time()`和`mtime()`函数的讨论。

调用`setcookie()`会导致发送 HTTP 头信息，这在你已经发送了一些常规 PHP 输出之后是无法实现的（即使该输出只包含一个空格或空行！）

### Cookies 与隐私

从隐私角度来看，Cookies 一直充满争议，而这种争议现在再次升温。在我们编写第一版时，DoubleClick（一家互联网广告代理）因其宣布而受到指责，它计划将 Cookie 信息与包含消费者姓名、地址和购买习惯的大型数据集进行交叉对比（这显然违背了此前对此类行为的承诺）。

人们的担忧点在于，当一个消费者通过填写表单并接受 Cookie 暴露其身份后，某些其他网站理论上可以知道用户的真实身份（以及许多其他信息）。如果这种做法变得普遍，你访问的每个电子商务网站可能不仅能查出你的名字、地址以及你在 Web 上访问过的其他页面。

因此，Cookies 让一些人感到担心，但同时它们也是解决 HTTP 协议无状态性的一种合理且无害的方案。有许多理由希望 Web 客户端/服务器能够跨越几个页面请求，而不仅仅是单个请求。作为开发者，你可能完全决定为了某种目的使用 Cookie，并放心地认为不会发生实质性的隐私影响。

然而，你的舒适并不代表用户的舒适，许多用户已将他们的浏览器设置为拒绝 Cookie，因为这是正确的。（请记住，我们在这里涉及的不仅是用户的隐私，还包括他们自己硬盘的使用！）你编写的任何服务器端代码都应该轻松处理来自客户端的 Cookie，你设计的任何网站都应该能轻松找到隐私政策，以便用户知道他们正在从哪里获取信息。这并不意味着你有义务向拒绝 Cookie 的用户提供相同水平的服务；某些功能如果没有 Cookie 编写起来实在太痛苦了，而且决定 Cookie 协作是编写完美隐私网站的先决条件。

### 示例

本节提供了一些`setcookie()`的示例调用，并附有注释，如下所示：

```
setcookie('username', 'timboy');
```

这设置了一个名为`membername`的 Cookie，值为`timboy`。由于除了第一个参数外没有其他参数，该 Cookie 将持续存在直到当前浏览器会话关闭，并且将出现在此浏览器到服务器的后续页面请求中，无论请求中的域名或该页面所在的 Web 根文件层次结构如何。该 Cookie 的设置与 Web 连接是否安全无关。例如，考虑以下内容：

```
setcookie('membername', 'troutgirl', time() + (60 * 60 * 24),
  "/www.tworks.com", 1);
```

这会将 Cookie 的值设置为`'troutgirl'`，如果它被之前的页面设置过，则会覆盖之前的示例值。过期时间被设置为当前时间之后的 86,400 秒（或 1 天）。路径参数是最包含的路径，因此此 Cookie 无论在 Web 目录层次结构的什么位置都将有效。主机参数设置为`'www.troutworks.com'`，这意味着除非用户确实向该主机发起了请求，否则后续的视图将不会读取该 Cookie。最后一个参数指定此 Cookie 仅通过安全连接进行写入。如果此页面使用的连接不是安全的，则 Cookie 将不会被设置。

> 如果你想在`setcookie()`中指定后面的参数，同时让前面的参数保持默认值，最好为域名参数留一个空字符串（`''`），为路径参数留一个包含斜杠的字符串（`'/'`），并为过期留 0。

> 对`setcookie()`的调用通常按照它们在 PHP 脚本中出现的相反顺序进行解释，尽管并非每个浏览器都是如此。最好的规则是永远不要从单次执行为同一个 Cookie 发送两个不同的值。（反正发送多个是没有意义的，因为其中一个始终会覆盖另一个。）

### 删除 Cookies

删除 Cookie 非常简单。只需调用`setcookie()`，并使用与设置它时完全相同的参数，将 Cookie 设置为一个空字符串即可。这并不是将 Cookie 的值设置为空字符串——它实际上是删除了 Cookie。如果你使用了路径或域名参数来设置 Cookie，则需要同样使用这些参数来取消设置。

### 读取 Cookies

在浏览器或用户机器上成功设置的 Cookie 将在该浏览器的下一次请求时自动读取。这具有以下效果：

- PHP 4.1 及更高版本中，Cookie 的名称/值对将添加到超全局数组`$_COOKIE['name'] = value`中。
- 在 PHP 的当前及后续版本中，名称和值也会被添加到普通的全局数组`HTTP_COOKIE_VARS`中。
- 如果开启了`register_globals`指令，一个普通的页面级全局变量将被设置为 Cookie 的值，且名称与 Cookie 的名称相同。由于 PHP 4.2 默认关闭了`register_globals`，因此该功能在 4.2 中可用，除非你或你的 ISP 管理员更改了配置。

例如，你可以这样设置 Cookie：

```
setcookie('membername', 'timboy');
```

这意味着在稍后的页面上，你可以像这样轻松地再次打印该值：

```
$membername = $_COOKIE['membername'];
print("The member name is $membername<BR>");
```

并且，如果开启了`register_globals`，稍后的页面使用：

```
print("The member name is $membername<BR>");
```

> **注意**：如果你在脚本中设置了 Cookie，它在下一个页面的 HTTP 头部到达之前不会生效。这意味着你无法在当前脚本中使用它。

以下代码的工作方式通常不如你预期的那样：

```
setcookie('servername', 'timboy');
print("I set a cookie. Now I will grab the value<BR>");
//（错误 - membername 可能是空的）
$membername = $_COOKIE['membername'];
print("the name is $membername<BR>");
```

因为这种操作在你的示例中尚未发生，而未设置的变量可能会产生一个空字符串。以下代码是正确的：

```
$cookievalue = 'timboy';
setcookie('membername', $cookievalue);
print("I set a cookie for the benefit of future pages<BR>");
//（正确 - 只有此页面实际设置的变量）
print("its name is membername, its value is $cookievalue<BR>");
```
