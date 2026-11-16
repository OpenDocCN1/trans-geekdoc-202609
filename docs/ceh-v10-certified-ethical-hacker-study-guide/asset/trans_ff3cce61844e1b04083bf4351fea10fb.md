

我们又回到了浏览器插件的世界。一个非常好的插件是 Wappalyzer。
Wappalyzer 可以添加到 Chrome 和 Firefox 中。当您访问网站时，
Wappalyzer 将提供其识别的技术列表。这可能包括 Web 服务器、
编程框架、广告网络和跟踪技术。它并不总是能成功
识别出所有内容。访问 www.google.com 会显示 Google Web Server 和
一个分析框架。然而，访问 CNN 会显示许多不同的技术，
其中一些在图 4.17 中可以看到。我们没有在那里得到的是由 CNN 使用的 Web 服务器。
不过，考虑到网站上使用的所有其他技术，我们接受所获得的内容。

图 4.17 用于技术识别的 Wappalyzer

![](img/421171b17a0c0dfae0aacde15d9831c1_154_0.png)

深入了解网页及所用技术的方法还有其他一些。其中一种是
Firebug。它适用于 Firefox，尽管也有适用于 Chrome 的 Firebug Lite。
Chrome。Firebug Lite 不具备完整 Firebug 的全部功能。但是，
在 Chrome 上，Google 提供了开发者工具。使用 Chrome 开发者工具或 Firebug，
您可以对正在查看的页面进行深入调查。首先，
您可以查看文档对象模型 (DOM) 及其所有组件。
您还可以选择页面中的不同 HTML 元素，并识别适用于该部分的样式和属性。
图 4.18 显示了使用 Chrome 开发者工具可以获取的部分信息。
此处检查的页面是一个 Google 搜索页面。
使用这样的工具，您可以通过查看页面的所有元素及其相互关系来更好地了解页面的运作方式。

图 4.18 Chrome 开发者工具

![](img/421171b17a0c0dfae0aacde15d9831c1_155_0.png)

网站是复杂的实体。Chrome 开发者工具和 Firebug 只能一次查看一个页面。
您必须逐个挖掘每个页面，以调查它们及其功能。
您可能会发现镜像网站以便离线查看更容易。
将其本地存储后，您可以随意多次查看页面，而无需向远程服务器发出重复请求。
尽管这些请求不太可能引起怀疑甚至不太可能被注意到，但您正在留下痕迹。
您可以用来镜像网站的一种工具是 HTTrack。
在以下代码中，您可以看到运行 HTTrack 镜像网站的结果。
该程序基本上会对远程站点进行爬行，并将结果存储在提供的目录中。

## 使用 httrack 镜像站点

```
$ httrack

Welcome to HTTrack Website Copier (Offline Browser) 3.49-2
Copyright (C) 1998-2017 Xavier Roche and other contributors
```

### 使用 httrack 镜像站点（续）

```
To see the option list, enter a blank line or try httrack --help

Enter project name :MySite

Base path (return=/root/websites/) :

Enter URLs (separated by commas or blank spaces) :http://www.domain.com

Action:
(enter)   1  Mirror Web Site(s)
        2  Mirror Web Site(s) with Wizard
        3  Just Get Files Indicated
        4  Mirror ALL links in URLs (Multiple Mirror)
        5  Test Links In URLs (Bookmark Test)
        0  Quit

: 1

Proxy (return=none) :

You can define wildcards, like: -*.gif +www.*.com/*.zip -*img*.zip
Wildcards (return=none) :

You can define additional options, such as recurse level (-r<number>),
separated by blank spaces
To see the option list, type help
Additional options (return=none) :
```

一旦获得 HTML，您可以随意处理。您可以进行更改，审查页面中包含的所有脚本，并根据需要审查页面。
不过，并非所有技术都在网站中。组织拥有大量其他技术，通常可以使用各种工具和技术进行挖掘。

## 技术情报

最终，作为一名道德黑客，您的目标是识别您所工作的组织中的漏洞。
虽然 Web 界面是寻找漏洞的诱人场所，考虑到通过 Web 界面可获得的敏感数据有多么多，
但它不是唯一的漏洞查找位置。
但是，您仍然可以利用网站继续探索目标公司技术的边界。
迄今为止，我们已识别招聘网站和一些社交网站，以获取目标处技术使用情况的情报。
除此之外，我们可以查看几个其他领域。第一个是使用 Google dorks（也称为 Google hacking）
来帮助真正集中我们的 Web 搜索。
此外，我们可以寻找所谓物联网 (IoT) 的一部分的设备。

### Google hacking

Google hacking 是一项重要技能。它将改进搜索响应，为您节省大量点击不那么有价值的页面的时间。
一旦了解可用于真正缩小搜索范围的一些关键字，您将节省时间并变得更加高效。
Google hacking 技术将帮助您识别技术和漏洞。
除了 Google hacking 技术之外，还有 Google hacking 数据库，它是某人识别出的 Google dorks 的集合，用于搜索多种事物。
Dork 是使用 Google 关键字的字符串，旨在搜索有用的响应。

首先是 Google 关键字。如果您长期使用搜索引擎，可能熟悉使用引号和布尔术语，
以帮助确保您在响应中获得正确的字符串。
除此之外，Google 还使用位置关键字。例如，您可能只想在 URL 中查找特定字符串。
为了在 URL 中搜索，您将使用 inurl，如示例 inurl:index 所示。
此示例将查找 URL 中任何位置包含单词 index 的页面。
这通常可能是 index.html、index.php 或 index.jsp 之类的页面。
如果您想忽略 URL 并仅在文本中搜索，可以使用关键字 intext。

由于您为某个组织工作，您有一个域或可能只有一小撮域。
这意味着您会在某个时刻希望仅在这些域中搜索。
为此，您可以使用 'site' 关键字。
您还可能希望将结果限制为单一文件类型，例如可移植文档格式 (PDF) 文件或电子表格。
要将结果限制为一种文件类型，您将使用 'filetype' 关键字。
也许您正在寻找 Microsoft 网站上关于 Windows 10 的所有 PDF 文档。
图 4.19 显示了为此进行的搜索 (site:Microsoft.com filetype:pdf “Windows 10”) 以及一些结果。

图 4.19 Google hacking 结果

![](img/421171b17a0c0dfae0aacde15d9831c1_157_0.png)

查找有用 Google dorks 示例的好地方是 Google Hacking Database (https://www.exploit-db.com/google-hacking-database/)。
Google Hacking Database (GHDB) 在多个类别中存储搜索术语，包括立足点、易受攻击的文件、错误消息和敏感目录。
创建这些有用的搜索字符串要求您不仅了解 Google hacking 关键字，
还要了解您正在寻找什么。
图 4.20 中列出了一些示例，其中搜索字符串正在查找网络或漏洞数据。
这意味着某人必须确切知道页面或 URL 中将包含哪些数据。
其中一些可以在图 4.20 中看到。

图 4.20 Google Hacking Database

| 日期 | 标题 | 摘要 |
| :--- | :--- | :--- |
| 2018-06-18 | intitle:"Malware Analysis Report" | intitle:"Malware Analysis Report" 此 dork 显示许多恶意软件分析报告，或... |
| 2018-06-07 | "Index of /ups.com/WebTracking" | * Google* dork 描述：Emotet 感染的域。Emotet 是一种银行木马恶意软件 progra... |
| 2018-05-17 | inurl:/Allitems.aspx?FolderCTID="" ... | IT 基础架构文档、设备配置和文档等其他有价值的信息.... |
| 2018-05-16 | inurl:/m/mini/localdomain/localhost.localdomain/ope... | 搜索由 Munin 生成的页面，该页面将包含敏感信息... |
| 2018-05-07 | intitle:"Statistics Report for HAProxy" ... | intitle:"Statistics Report for HAProxy" * "statistics report for pid" St... |
| 2018-04-11 | intext:"Powered by Nibbleblog" | 查找由 Nibbleblog CMS 驱动的博客。请合乎道德且负责任地使用。Dork ... |
| 2018-03-27 | ":: Arachni Web Application Security Report&&q... | ":: Arachni Web Application Security Report" 查找 Arachni 留下的报告!... |
| 2018-03-12 | "IBM Security AppScan Report" ext:pdf | "IBM Security AppScan Report" ext:pdf 此 dork 显示由 l... 创建的结果 |
| 2018-02-28 | intitle:"netsparker scan report" ext:pdf | intitle:"netsparker scan report" ext:pdf 查找 Netsparker (...) 留下的报告 |
| 2018-02-20 | intitle:"Burp Scanner Report" | "由 Burp Scanner 生成的报告" 查找... |

在 GHDB 上花费时间可以为您在目标中查找可能的问题提供大量弹药。
其中一些可能是盲目搜索，如果您不知道目标中预期什么。
当然，为了确保您仅在目标中搜索，需要将 site: 和域名添加到搜索参数中。
您可能从图 4.20 的 Microsoft 搜索中注意到的一件事是，当仅使用域时，
会返回每个可能的主机名。
如果您想仅在单个主机名（例如 www.microsoft.com）中搜索，则需要提供主机名。
仅提供域是另一种捕获您可能无法通过 DNS 搜索获得的其他主机名的方法。

### 物联网 (IoT)

您很可能听说过物联网。
物联网由设备组成，这些设备至少从传统的角度来看可能几乎没有或没有输入或输出功能。
如果设备可以运行通用应用程序，并且还有键盘和屏幕（例如计算机、平板电脑或智能手机），则它不属于物联网。
许多其他设备，例如联网恒温器、灯泡、风扇、冰箱以及许多其他基本单一用途的设备，都是物联网设备。
许多公司正在以不同的自动化能力利用这一点。

