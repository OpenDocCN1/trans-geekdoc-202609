
![tip](images/tip.png)要在 Internet Explorer 和 Firefox 中查看源代码，右键单击页面并从上下文菜单中选择 "View Source" 或 "View Page Source"。

2. **更改这些字段中存储的信息。**

恶意用户可能会将价格从 $100 更改为 $10，例如。

3. **将页面重新上传到服务器。**

此步骤允许攻击者获取非法收益，例如在网络购买时获得更低的价格。

这类漏洞正在变得越来越少见，但与 URL 重写类似，利用的可能性仍然存在，因此保持警惕很有价值。

![warning](images/warning.png)使用隐藏字段进行身份验证（登录）机制可能特别危险。我曾看到一种多因素身份验证锁定流程，它依赖于隐藏字段来记录用户登录尝试的次数。该变量可以在每次登录尝试时重置为零，从而便于脚本化的字典攻击或暴力破解登录。这或许是讽刺——设计用于*防止*入侵者攻击的安全控制本身却容易受到入侵者的攻击。

一些工具，如商业网络漏洞扫描器自带的代理以及 Burp Proxy，可以轻松地操纵隐藏字段。图 15-3 显示了 WebInspect SPI Proxy 接口以及网页的隐藏字段。

![ FIGURE 15-3:  使用 WebInspect 查找并操纵隐藏字段。](images/9781119485476-fg1503.png)

[FIGURE 15-3:](#c15.xhtml#rc15-fig-0003)  使用 WebInspect 查找并操纵隐藏字段。

如果你发现隐藏字段，可以尝试对它们进行操纵，看看能做什么。方法很简单。

#### 代码注入和 SQL 注入

类似于 URL 重写攻击，代码注入攻击会操纵特定的系统变量。下面是一个示例：

`http://www.your_web_app.com/script.php?info_variable=X`

攻击者看到这个变量后，可以在 `info_variable` 字段中输入不同的数据，将 `X` 替换为诸如下面这些内容：

`http://www.your_web_app.com/script.php?info_variable=Yhttp://www.your_web_app.com/script.php?info_variable=123XYZ`

这段示例比较基础，但 web 应用可能会以提供攻击者比他们想要的更多信息的方式响应，例如返回详细错误信息或访问未授权的数据字段。无效输入也可能导致应用或服务器挂起。攻击者可以利用这些信息进一步了解 web 应用及其内部工作，进而导致严重的系统 compromise。

![warning](images/warning.png)如果 HTTP 变量通过 URL 传递且易于访问，那么攻击者利用你的 web 应用已经只是时间问题。

我曾经使用一个用于管理个人信息的 web 应用，它正是这样的。因为 `"name"` 参数是 URL 的一部分，任何人都可以通过修改 `"name"` 的值来获取其他人的个人信息。如果 URL 包含 `"name=kbeaver"`，只需将其改为 `"name=jsmith"`，即可查看 J. Smith 的家庭地址、社会安全号码等。Ouch！我向系统管理员报告了这个漏洞。经过几分钟的否认后，他承认确实是个问题，并与开发人员一起着手修复。

代码注入也可以针对后端 SQL 数据库进行，这种攻击称为 *SQL 注入*。恶意攻击者在 URL 请求中插入 SQL 语句（如 `CONNECT`、`SELECT`、`UNION`），试图连接并从数据库中提取信息，而该数据库是 web 应用交互的对象。SQL 注入之所以能实施，是因为应用未能正确验证输入，并且数据库服务器和 web 服务器返回了信息性错误。

SQL 注入主要有两类：标准（也称为基于错误）和盲注。基于错误的 SQL 注入是利用应用在输入无效信息时返回的错误消息来进行的。盲注则是在错误消息被禁用的情况下进行，攻击者或自动化工具需要猜测数据库返回的内容以及对注入攻击的响应。

![tip](images/tip.png)快速（但不一定可靠）判断你的 web 应用是否易受 SQL 注入的方法是：在表单字段或 URL 末尾输入一个单引号（'）。如果返回了 SQL 错误，那么大概率 SQL 注入已存在。

在查找和发现 SQL 注入缺陷时，你得到的是物有所值的回报。正如 URL 重写一样，使用漏洞扫描器进行 SQL 注入检查更为明智，它允许攻击者通过漏洞页面向后端数据库注入数据库查询和命令。图 15-4 展示了 Netsparker 漏洞扫描器发现的众多 SQL 注入漏洞。

![ FIGURE 15-4:  Netsparker 发现的 SQL 注入漏洞。](images/9781119485476-fg1504.png)

[FIGURE 15-4:](#c15.xhtml#rc15-fig-0004)  Netsparker 发现的 SQL 注入漏洞。

Netsparker 的好处在于，它在发现 SQL 注入后，提供了内置的 "Execute SQL Commands" 工具，进一步展示弱点。一张展示 SQL 注入在起作用的截图，几乎是漏洞和渗透测试能达到的最佳效果！

当你发现 SQL 注入漏洞时，可能会倾向于在此停下脚步，不再尝试利用该弱点。这没问题。但我更倾向于看看我能在数据库系统中走多远。我建议尽可能使用漏洞扫描器内置的 SQL 注入功能，以便向管理层展示漏洞的严重性。

![tip](images/tip.png)如果预算有限，可考虑使用免费的 SQL 注入工具，如 SQL Power Injector（[www.sqlpowerinjector.com](http://www.sqlpowerinjector.com)）或 Firefox 添加程序 SQL Inject Me（[https://addons.mozilla.org/en-us/firefox/addon/sql-inject-me](https://addons.mozilla.org/en-us/firefox/addon/sql-inject-me)）。

我在 [第 16 章](#c16.xhtml) 中深入探讨了数据库安全。

#### 跨站脚本 (XSS)

跨站脚本（XSS）可能是最为人知且最广泛存在的 web 漏洞，当网页未正确验证用户输入（通常是 JavaScript）时，就会出现该漏洞。攻击者可以利用缺乏输入过滤的机会，在任何查看该页面的计算机上执行恶意代码。

例如，XSS 攻击可以显示另一个恶意网站的用户 ID 和登录页面。如果用户不慎在该登录页面输入用户 ID 和密码，这些信息就会被记录到黑客的服务器日志中。其他恶意代码可以被发送到受害者的计算机并与查看该页面的浏览器或电子邮件应用程序以相同的权限运行。恶意代码可能赋予黑客对浏览器 Cookie 或浏览器历史记录文件的完全读写权限，甚至允许他下载或安装恶意软件。

![tip](images/tip.png)简单的测试方法是检查应用中是否有接受用户输入的字段（如登录或搜索框），并输入以下 JavaScript 语句：

`&lt;script&gt;alert('XSS')&lt;/script&gt;`

如果弹出一个显示 `XSS` 的窗口（如图 15-5 所示），则说明该应用易受 XSS 漏洞影响。XSS‑Me Firefox 添加程序（[https://addons.mozilla.org/en-US/firefox/addon/xss-me](https://addons.mozilla.org/en-US/firefox/addon/xss-me)）也是一种测试手段。

![ FIGURE 15-5:  将脚本代码反射到浏览器。](images/9781119485476-fg1505.png)

