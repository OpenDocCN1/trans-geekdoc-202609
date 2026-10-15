
-   [使用交叉站点脚本绕过反 XSRF 令牌的方法]https://example.org
   反 XSRF 令牌旨在减轻跨站请求伪造（CSRF）攻击的成功率，但并不针对跨站脚本（XSS）攻击。如果目标 Web 应用使用反 XSRF 令牌，但你能够控制目标源（即钩子），则可以绕过此保护机制。如前所述，单个 XSS 漏洞可能让攻击者完全控制受影响的源。

   攻击者若能控制目标源，将从包含表单的页面中提取反 XSRF 令牌，并将其加入新的恶意表单中。由于使用了正确的令牌，攻击将成功。

# 跨域资源检测

在无法成功指纹化 Web 应用的情况下，仍然可以检测跨域资源。但此过程对攻击者而言耗时且费力。此类情况下，攻击者会通过有据可依的猜测发送跨域请求。

目标 Web 应用的结构未知，但可以合理推断其根目录所在路径，以及可能存在的登录功能及其预测的参数名称。

诸如 DirBuster（由 James Fisher 创建）等工具使用常见目录和文件列表来发现 Web 应用中隐藏的目录。虽然这些工具需要直接访问目标 Web 应用，但相同的列表也可用于通过不同的检测逻辑发现跨域资源。

XSRF 防护措施的副作用是降低跨域资源检测的可靠性。当实施完善的 XSRF 防护时，Web 应用的跨域响应内容变化极小，这不利于通过该方法识别资源。反 XSRF 令牌还可能阻止从钩点来源发起的某些 Web 应用攻击。在从浏览器跨域跳跃时，必须考虑 XSRF 防护措施以扩大攻击面。

前几章节介绍了如何利用 Iframe 实现持久化并进行社交工程攻击。同样的技术现在可以用于协助发现跨域资源。

## 检测跨域资源

当前钩定的源可能包含指向其他源的链接或参数，这些链接或参数也可能被钩定。这在可钩定的内部 Wiki 中尤为有用，因为它可能包含指向其他内部 Web 应用的链接。虽然外部钩定源产生结果的概率较低，但仍值得检查，因为过程相对简单。

以下代码可用于枚举当前钩定页面中所有同源和跨域的链接及表单操作：

```
// 发现页面中所有 <a> 和 <form> 元素的 href 或 action 属性，并判断资源是否同源
function getFormActions(doc){
  var formsarray = [];
  var forms = doc.getElementsByTagName("form");
  for (var i = 0; i < forms.length; i++){
    var action = forms[i].getAttribute('action');
    formsarray = formsarray.concat(action);
    // 模拟 <a> 元素：通过此方式可在同一方式中调用 isSameOrigin() 对 <a> 和 <form> 元素
    var a = doc.createElement('a');
    a.href = action;
    console.log("Discovered form action: " + action + ". SameOrigin: " + isSameOrigin(a));
  }
  return formsarray;
}

// 发现页面中所有 <a> 元素的 href 属性，并判断资源是否同源
function getLinks(doc){
  var linksarray = [];
  var links = doc.links;
  for(var i=0; i<links.length; i++) {
    var link = links[i];
    linksarray = linksarray.concat(link);
    console.log("Discovered link: " + link.href + ". SameOrigin: " + isSameOrigin(link));
  };
  return linksarray;
}

// 判断资源是否同源（检查协议、主机名和端口）
function isSameOrigin(url){
  var sameOrigin = false;
  if(url.hostname.toString() === location.hostname.toString() &&
    url.port === location.port &&
    url.protocol === location.protocol){
    sameOrigin = true;
  }
  return sameOrigin;
}

getLinks(document);
getFormActions(document);
```

上述代码通过 `getLinks()` 函数获取当前文档中所有 `<a>` 链接，并使用 `isSameOrigin()` 判断每个链接的资源是否为同源；同样，`getFormActions()` 函数枚举所有 `<form>` 元素的 `action` 属性，并通过创建临时 `<a>` 元素调用 `isSameOrigin()` 来判断其资源是否同源。由于 `isSameOrigin()` 只接受 `<a>` 元素，代码通过动态生成 `<a>` 元素来复用该函数。

[Figure 9-10](#c09.html#figure9-10) 展示了在 http://localhost/text.html 托管的测试页面上运行上述代码的结果，页面内容如下：

```
<html><body>
 <a href="http://www.beefproject.com">BeEF Project</a><br />
 <a href="http://ha.ckers.org/">ha.ckers.org </a><br />
 <a href="http://localhost:8080/login">Login</a><br />
 <a href="/demos/butcher/index.html">BeEF hook</a><br />
 <form action="http://browserhacker.com"></form>
 <form action="//browserhacker.com:9090/login"></form>
 <form action="/login"></form>
</body></html>
[ox
</think>
