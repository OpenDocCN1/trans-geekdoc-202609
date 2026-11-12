
}
mysql_free_result($result);
}
mysql_close();
return $themeByNum;
}

```php
function GeneratePassword() {
// skip the L's since they look like 1's!
$wordlist = array("apple", "array", "book",
"bold", "catalog", "cook", "door", "down",
"echo", "eat", "flag", "funny", "garage",
"going", "house", "heavy", "inside",
"icecream", "jump", "jack", "kludge", "keep",
"merry", "making", "need", "next", "other",
"open", "perfect", "place", "quite", "quick",
"rest", "read", "taking", "tophat", "under",
"upside", "video", "vanish", "wane", "wipe");
$firstword = $wordlist[rand(0,
count($wordlist) - 1)];
$secondword = $wordlist[rand(0,
count($wordlist) - 1)];
$number = rand(10,99);
$newpass = $firstword.$number.$secondword;
return $newpass;
}
// Important: Do not put any blank lines
// After the closing ?> in this file!
?>
```

![](img/3f967ab8a8fddc723173059f56621648_618_0.png)

如果在输入清单 7-7 时不小心，你很容易遇到一个排查起来非常麻烦的问题。*不要在 useraccess.php 文件末尾放入任何空行。* 确保在闭合 `?>` 之后没有换行。这样做的原因是，这些空行会作为文本发送到浏览器。但是这个 `useraccess.php` 文件是在 HTML 头部期间处理的。如果你发送空白文本行，浏览器会非常困惑。因此，不要让任何空行混入这个文件！

## 使用 checkAccess 函数登录

checkAccess 函数是一个多功能函数，执行以下操作：

- 检查用户是否已经登录
- 如果用户尚未登录，则为其登录
- 如果存在，则使用 `login.html` 表单的结果进行登录；否则，使用 Cookie，这样用户就不必不断登录
- 在整个会话期间保存用户登录信息（或者，如果用户在登录表单中选择了“记住我”复选框，则长期保存）
- 如果用户提供了错误的登录信息，则将用户发送到 logininfailed.html 页面

这个函数背后的目标是允许你在任何私有页面的开头调用这个函数，PHP 会处理其余的事情。你可以在本章前面的清单 7-5 中看到我是如何做到的，那就是 welcome.php 页面。

这个函数首先要做的是在 $_POST 数组中查找电子邮件和密码。如果调用此函数的页面（例如 welcome.php）是通过 login.html 页面到达的，则 $_POST 数组将包含用户在表单中输入的信息。

如果 $_POST 数组没有电子邮件和密码信息，此函数会检查用户的 Cookie 以获取信息。

如果找到了电子邮件地址和密码（并且如果用户是通过 login.html 页面到达且未勾选“记住我”框），则电子邮件地址和密码会保存在会话 Cookie 中。这样一来，如果用户在不关闭 Web 浏览器的情况下访问其他受保护页面，他或她就不必再经历登录过程。（这是如何实现的？这里需要更多绕弯抹角的推理：因为电子邮件地址和密码已保存到会话 Cookie 中，所以下次调用 checkAccess 函数时，Cookie 将被设置，检查 Cookie 中电子邮件和密码信息的部分将起作用。）

另外，如果找到了电子邮件地址和密码，页面会将信息与 MySQL 中的登录表进行验证。这会给人一种已登录系统的错觉，但实际上，每次用户访问私有页面时，系统只是验证用户是否有权查看页面。并没有进行“登录”操作，尽管用户感觉有。

如果无法验证登录，或者不存在电子邮件地址和密码，代码会通过设置如下标头将用户发送到 logininfailed.html 页面：

```
header("location: logininfailed.html");
```

因为你正在调用 header 函数，所以只能在 .php 文件的开头、初始 `<html>` 标记之前以及调用任何 PHP print 或 echo 语句之前使用 checkAccess 函数。你可以在清单 7-5 的 welcome.php 页面中看到我遵循了此规则。

![](img/3f967ab8a8fddc723173059f56621648_619_0.png)

## 处理加密问题

我在 Windows XP 系统和 Linux 系统上测试了本章中的示例系统，两者都运行 Apache。我发现了一件奇怪的事情：crypt 函数在每台计算机上的表现不同。事实证明，这种差异与针对每种操作系统配置 Apache 的方式有关。

如果每次运行时看到的输出都相同，则你的系统使用 DES 加密。如果每次看到的输出都不同，则你的系统使用 MD5 加密。（并不是 MD5 每次加密方式不同；而是使用 MD5 时，PHP 系统会随机生成一个盐值。不同的盐值会导致 MD5 算法表现不同，从而产生不同的加密结果。）

问题在于 crypt 函数有不同的方式来选择要使用的加密技术。（两种最常见的加密技术是 DES，代表数据加密标准，以及 MD5，代表消息摘要算法 5 版。）

- 2. 接下来，查看输出并计算随机字符串中的字符数。

这里有两个重要因素：你将登录表中的密码字段设为多大，以及在用户输入密码后如何处理密码比较。这两个因素都与所使用的加密类型相关。

这是你需要将登录表的密码列设为的长度。

- 3. 如果小型测试程序的输出每次都显示相同的值，则使用以下行来加密密码：

```
$passcrypt = crypt($password);
```

这是你可以用来查找所使用加密技术的测试程序：

- 4. 如果小型测试程序的输出每次都显示不同的值，则使用以下行来加密密码，它会提取用户注册时使用的盐值，并强制 MD5 算法使用相同的盐值。

```php
<?php
print crypt("test");
print "\n";
?>
```

```
$passcrypt = crypt($password,
substr($pass, 0, 12));
```

按照以下步骤查找你的加密技术：

- 1. 将此文件保存为 crypttest.php，并在 Web 服务器的提示符下使用 php crypttest.php 多次运行。

最后，如果用户是通过 login.html 页面到达此页面，并且该用户勾选了“记住我”框，则电子邮件地址和密码会保存在长期 Cookie 中。过期日期设置为 Unix 日期 2000000000，对应 2033 年 5 月 17 日左右，距本书出版不到 30 年。（如果你在 2033 年 5 月 18 日阅读此内容，那也没办法——尽管对我来说，如果本书在 30 年后仍然流行，那会很酷。）

现在关于 Cookie 的一些最后要点。如果你保存了长期 Cookie，你可能会发现，下次用户登录时 Cookie 会被重写。这并不是问题，原因有两点：

- 如果是同一用户登录，Cookie 的过期日期不会改变，因为 Cookie 中的数据没有改变。
- 如果是不同的用户登录，该用户的信息会作为会话 Cookie 保存（除非用户勾选“记住我”框，否则不是长期的），新的 Cookie 信息会覆盖之前的 Cookie。换句话说，一切都会按你希望的方式工作。

除了使用 Cookie，PHP 还包含一种用于处理 *会话* 的复杂机制。此机制在单个浏览器会话期间使用 Cookie 和其他设备来跟踪用户信息，就像我在这些示例中所做的那样。如果你想探索 PHP 会话处理机制，请查看 www.php.net/session。

## 使用 signup 函数注册

signup 函数很简单。它不执行任何检查；它只是将用户信息插入登录表中。

此函数将未加密的密码作为参数，并在将密码保存到数据库之前对其进行加密。不过，你需要确保对自己的特定 PHP 安装使用正确的加密方法。有关更多信息，请参阅侧边栏“处理加密问题”。

## 获取主题信息

useraccess.php 文件（请参阅清单 7-7）包含三个与主题相关的项目：

- ThemeInfo 类
- getTheme 函数
- getThemeNames 函数

ThemeInfo 类目前只有一个成员，$bgcolor。对于此示例，我本可以直接使用背景颜色而不必创建 ThemeInfo 类。但是，我希望为你提供一个起点，让你可以添加超出背景颜色之外的其他主题信息。因此，我创建了 ThemeInfo 类。
