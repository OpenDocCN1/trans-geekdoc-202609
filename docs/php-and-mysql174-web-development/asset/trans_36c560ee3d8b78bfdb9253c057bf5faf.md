

## 第 16 章 使用 PHP 实现认证方法

### 使用基础认证 (Basic Authentication)

幸运的是，用户验证是一项常见任务，因此 HTTP 内置了身份验证功能：脚本或 Web 服务器可以向网络浏览器请求验证。网络浏览器负责显示对话框或设备，以从用户处获取所需的信息。

虽然 Web 服务器会对每个用户请求请求新的验证详细信息，但网络浏览器不需要每个页面都请求用户的详细信息。浏览器通常会在浏览器窗口打开期间存储这些信息，并在无需用户交互的情况下自动将它们重新发送给 Web 服务器。

HTTP 的这一特性被称为基础认证（basic authentication）。你可以使用 PHP 或使用 Web 服务器内置的机制来触发基础认证。我们首先查看 PHP 方法和 Apache 方法。

当你结合 SSL 和数字证书使用基础认证时，Web事务的所有部分都可以受到强安全性的保护。

基础认证保护一个命名的域（realm），并要求用户提供有效的用户名和密码。域之所以命名，是为了在同一台服务器上存在多个域。同一台服务器上的不同文件或目录可以属于不同的域，每个域都由一组不同的名称和密码保护。命名的域还可以将一个主机或虚拟主机上的多个目录归为一个域，用一个密码保护所有目录。

### 在 PHP 中使用基础认证

PHP 脚本通常是跨平台的，但基础认证依赖于服务器设置的环境变量。在列表 16.2 中，它已针对 Apache Web 服务器进行了测试。

列表 16.2 basic_auth.php——可以触发 HTTP 基础认证

```php
<?php
if (isset($_SERVER['PHP_AUTH_USER']) &&
    isset($_SERVER['PHP_AUTH_PW']) &&
    substr($_SERVER['HTTP_AUTHORIZATION'], 0, 6) == 'Basic ')
 {

    list($_SERVER['PHP_AUTH_USER'], $_SERVER['PHP_AUTH_PW']) =
    explode(':', base64_decode($_SERVER['HTTP_AUTHORIZATION']), 6));
}

// 将此 if语句替换为数据库查询或类似操作
if ((_SERVER['PHP_AUTH_USER'] != 'user') ||
    $_SERVER['PHP_AUTH_PW'] != 'pass')) {

    // 访问尚未提供详细信息，或其
    // 用户名和密码组合不正确
```

```php
header('WWW-Authenticate: Basic realm="Realm-Name"');
header('HTTP/1.0 401 Unauthorized');
} else {
?>
<!DOCTYPE html>
<html>
<head>
  <title>Secret Page</title>
</head>
<body>
<?php
echo '<h1>Here it is!</h1>';
echo '<p>I bet you are glad you can see this secret page.</p>';
?>
</body>
</html>
```

列表 16.2 中的代码作用与本章中之前的列表类似：如果用户尚未提供密码信息，系统将向其索要该信息。如果用户提供了匹配的用户名-密码对，则将向其展示页面内容。

在这种情况下，用户将看到一个与之前的列表略有不同的界面。此脚本没有提供用于登录信息的 HTML 表单。用户的浏览器会向其显示一个对话框。有些人认为这是一种改进；另一些人则更喜欢对界面的视觉方面拥有完全的控制。图 16.4 显示了 Firefox 提供的示例对话框。

![](img/654520c37415debd4290b9b4aa2c03f2_404_0.png)

图 16.4 使用 HTTP 认证时，用户的浏览器负责对话框的外观

### 使用 Apache 的 .htaccess 文件使用基础认证

你可以在不编写 PHP 脚本的情况下实现与列表 16.2 脚本类似的结果。

Apache Web 服务器包含许多种不同的认证模块，这些模块可用于判断用户输入数据的有效性。要使用 HTTP 基础认证，你需要 `mod_auth_basic`，以及一个与你计划使用的密码存储机制相对应的认证模块。在本节中，我们将查看如何在文件中存储密码，在下一节中，我们将查看如何将它们存储在数据库中。

为了获得与前面的脚本相同的输出，你需要创建两个单独的 HTML 文件：一个用于内容，另一个用于拒绝页面。我们在之前的示例中跳过了 HTML 元素，但在生成 HTML 时，真的应该包含 `<html>` 和 `<body>` 标签。

列表 16.3，content.html，包含授权用户看到的内容。
列表 16.4，名为 rejection.html，包含拒绝页面。在发生错误时显示一个页面是可选的，但如果你在上面放置一些实用的内容，将是一个非常不错且专业的做法。鉴于此页面会在用户尝试进入受保护区域时显示，rejection 可能包含有关如何注册密码的说明，或者在忘记密码时如何获取密码重置和电子邮箱的说明。

列表 16.3 content.html——示例内容

```html
<!DOCTYPE html>
<html>
<head>
<title>Secret Page</title>
</head>
<body>
<h1>Here it is!</h1>
<p>I bet you are glad you can see this secret page.</p>
</body>
</html>
```

列表 16.4 rejection.html——示例 401 错误页面

```html
<!DOCTYPE html>
<html>
<head>
<title>Rejected Page</title>
</head>
<body>
<h1>Go Away!</h1>
<p>You are not authorized to view this resource.</p>
</body>
</html>
```

这些文件本身并没有什么新意。对于这个示例来说，有趣的文件是列表 16.5（此处应为 16.5）。该文件需要被命名为 `.htaccess`，它将控制对其目录及其任何子目录中文件的访问。

列表 16.5 htaccess——一个 .htaccess 文件可以设置许多 Apache 配置设置，激活认证

```apache
AuthFile /var/www/.htpass
AuthType Basic
AuthName "Authorization Needed"
AuthBasicProvider file
Require valid-user
ErrorDocument 401 /var/www/pmd53/chapter16/rejection.html
```

列表 16.5 是一个 .htaccess 文件，用于在目录中开启基础认证。.htaccess 文件可以进行许多设置，但此示例中的行都与认证有关。

这一行

```
AuthFile /var/www/.htpass
```

告诉 Apache 在哪里找到包含授权用户密码的文件。该文件命名为 .htpass，但你可以给它任何喜欢的名称。你称它什么并不重要，重要的是你把它存储在哪里。它不应该存储在 Web 树内——即一个可以通过 Web 服务器下载的地方。示例 .htpass 文件显示在列表 16.6 中。

由于支持多种不同的认证方法，你需要指定你正在使用哪种认证方法。在这里，你使用基础认证，如此指令所示：

```
AuthType Basic
```

与 PHP 示例一样，要使用 HTTP 基础认证，你需要按如下方式命名域：

```
AuthName "Authorization Needed"
```

你可以选择任何喜欢的域名称，但请记住该名称将显示给访问者。你需要指定使用的是什么提供程序。在这种情况下，我们使用的是文件，指定如下：

```
AuthBasicProvider file
```

你还需要指定谁允许访问。你可以指定特定的用户、组，或者像我们这样，简单地允许用户访问。行

```
Require valid-user
```

指定任何有效用户访问。行

```
ErrorDocument 401 /var/www/pmd53/chapter16/rejection.html
```

告诉 Apache 为认证失败的访问者显示什么文档（HTTP 401）。你可以使用 ErrorDocument 指令提供自己的页面，例如 404。格式如下

列表 16.6 htpass 文件存储用户名和每个加密密码

```
user1:$S12DTFUq06JPLkwoYqwTwd.
user2:$S12aAOuccSphrrV4gaah01
user3:$S12c2xbFrFs5dI4NGTcn0RB
user4:$S12svjxonbPfyIn2vcp1
```

htpass 文件中的每行包含一个用户名、一个冒号以及加密后的密码。你的 htpass 文件内容会有不同。要创建它，你使用 Apache 提供的名为 htpassword 程序。

htpassword 程序支持许多选项。通常用法如下：

```
htpassword -bc passwordfile username
```

使用 -c 切换告诉 htpassword 创建。添加第一个用户时必须使用它。注意不要对其他用户使用它，因为如果文件存在，htpassword 将删除它并创建一个。

-b 切换告诉程序从参数接收密码而不是提示。此功能对于你作为过程的一部分非交互调用 htpassword 非常有用，但如果你从命令行调用 htpassword，不应使用它，因为密码将保留在历史中。

以下命令创建了列表 16.6 显示的文件：

```
htpassword -b /var/www/.htpassfile user1 pass
htpassword -b /var/www/.htpassfile user2 pass
htpassword -b /var/www/.htpassfile user3 pass
htpassword -b /var/www/.htpassfile user4 pass
```

注意，htpassword 可能不在你的路径中：如果是的话，你可能会在 /usr/local/apache/bin 目录下找到它。

这种认证很容易设置，但使用 .htaccess 文件存在一些问题。

用户名和密码存储在文本文件中。每当浏览器请求受 .htaccess 文件保护的文件时，服务器都必须解析 .htaccess 文件，然后解析密码文件，尝试匹配用户名和密码。与其使用 .htaccess 文件，

