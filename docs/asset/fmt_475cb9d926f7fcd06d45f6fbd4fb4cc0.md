
[`cyberarms.wordpress.com/2018/07/08/finding-spy-bugs-with-an-rtl-sdr-salamandra`](https://cyberarms.wordpress.com/2018/07/08/finding-spy-bugs-with-an-rtl-sdr-salamandra/)

## 使用树莓派追踪飞机

好了，这个与安全没有关系，它只是一个酷的 `Pi` 项目。实时飞行追踪网站非常有用。它们允许你看到世界各地航班的实际位置。你可以使用 `Raspberry Pi` 创建一个简单的扫描器，让你能够追踪附近的飞机！自动相关监视广播（`Automatic Dependent Surveillance – Broadcast`或 `ADS-B`）是飞机公开广播的信号，允许其被追踪。飞机爱好者有几种方法接收这些信号并在地图上绘制飞机的位置。爱好者实现这一点最简单的方法之一是使用 `Raspberry Pi 3` 和一个 `SDR-RTL` USB 适配器。

使用树莓派追踪飞机非常简单，你只需要 `SDR-RTL`、运行 `Raspbian` 的 `Pi 3` 以及 `ADS-B` 映射软件。当软件运行时，`SDR-RTL` 接收飞机的信号，然后在 Google 地图类型的显示上实时绘制它们的位置。我使用了以下设备：

- 运行 `Raspbian` 的 `Pi 3b`
- 带有标准伸缩天线的 `NooElec NESDR SMART` USB
- `Pi 3`，7 英寸触摸屏外壳

# 使用 Pi-Hole 拦截广告和恶意软件网站

![](img/00259.jpeg)

工具网站：[`pi-hole.net/`](https://pi-hole.net/)

工具维基（Wiki）：[`docs.pi-hole.net/`](https://docs.pi-hole.net/)

最后，树莓派的另一个用途是使用 Pi-Hole 拦截那些烦人的广告和恶意软件网站。Pi-Hole 是一种运行在树莓派（以及其他平台）上的全网广告拦截器。你也可以配合 Pi-Hole 使用 TFT 显示器来一眼查看统计数据。Pi-Hole 可以运行在任何支持的设备上。我使用了 Adafruit 的 2.8 英 TFT 电阻式 Pi-Hole 套件，配合树莓派 3b。它的组装和使用非常简单：

[`blog.adafruit.com/2018/10/11/new-product-ad-blocking-kit-for-pi-hole-with-2-8-pitft-no-soldering/`](https://blog.adafruit.com/2018/10/11/new-product-ad-blocking-kit-for-pi-hole-with-2-8-pitft-no-soldering/)

- Adafruit 在此处提供了其套件整个过程的完整说明：[`learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/overview`](https://learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/overview)
- 也可以在 Pi-Hole Wiki 上找到完整的安装指南：[`docs.pi-hole.net/`](https://docs.pi-hole.net/)

我将只快速介绍安装过程。如果你购买了 Adafruit 套件，我强烈建议你按照他们网站上提供的步骤操作！理解将树莓派作为整个家庭或办公室的 DNS 服务器的安全影响至关重要。如果你不完全熟悉配置树莓派、DNS 服务器、网络安全和网络配置，请不要尝试自行操作。由于网络配置多种多样，请自担承担风险，我无法为此设置提供技术支持。

## 安装 Raspbian Lite

只需下载适用于你树莓派对应的文件（我使用的是 Pi3b）并将其写入 microSD 卡。在从读卡器取出内存卡之前，在卡中添加一个名为 `ssh` 的空白文本文件，这将在你首次启动 Raspbian 时默认启用 SSH。

注意：不要忘记更改你的树莓派密码，并使用长且复杂的密码！

将外围设备连接到树莓派，插入 microSD 卡，并为树莓派供电。你现在应该可以通过 SSH 登录树莓派了。

## 安装 Raspbian 更新

在终端中运行以下命令：

```bash
apt update
apt upgrade
```

此外，在 `Raspi-Config` 中，如果你在美国，将你的区域设置（locale）设置为 `US`，或者你实际所在的国家代码——它默认是 `GB`，如果这不正确，在运行 Pi-Hole 的图形化 PADD 界面时会导致很多问题。

## 安装 Pi-Hole & PADD

安装 Pi-Hole 非常简单。在 Raspbian 终端输入：

```bash
curl -sSL https://install.pi-hole.net | bash
```

然后按照安装提示进行操作。

## 安装 PADD

![](img/0260.jpeg)

如果你在使用 TFT 屏幕，安装 PADD 将为 Pi-hole 提供一个非常漂亮的界面。安装取决于你使用的 TFT 屏幕，因此我遵循了 Adafruit 针对我 2.8 英寸屏幕的 PADD 指南，位于：[`learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/install-padd`](https://learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/install-padd)

## Pi-Hole 的 Web 界面

Pi-Hole 的 Web 界面非常酷，它为你提供了大量信息。

![](img/0260.jpeg)

你可以免费进行基础搜索，每页返回一个结果。对于更复杂的搜索，你需要一个 `Shodan` 账户。我强烈建议付费账户，因为这项服务非常值。使用 `Shodan` 非常简单，只需像在 `Google` 中一样输入搜索词即可。你可以使用多个关键词来查找在线的树莓派（Raspberry Pi）系统。

以下是几个例子：

![](img/00262.jpeg)

![](img/00263.jpeg)

在本文写作时，有近 200,000 个在线系统正在运行 `Raspbian`。你也可以搜索“Raspberry Pi”、“RaspberryPi”或“RPi”。在上面的图片中，你可以看到有 4,455 个设备的描述中某处包含“Raspberry Pi”字样。你还可以通过应用程序服务器名称（包括摄像头软件）来找到它们以及许多其他设备。

例如，我们在“物理安全”章节中介绍过的“MotionEye”：

![](img/00264.jpeg)

诚然并非所有结果都相关，但很大范围内很多都会运行在树莓派上。

## 使用 Shodan 网络监控器自动告警

工具网站：[`monitor.shodan.io/`](https://monitor.shodan.io/)

工具使用视频：[`www.youtube.com/watch?v=T-9UvZ-l-tE`](https://www.youtube.com/watch?v=T-9UvZ-l-tE)

你可以手动扫描 `Shodan`，查看你所有公开的业务或家庭系统的表示。但你如何判断是否像 JPL 实验室的人员那样将恶意设备接入了你的网络呢？`Shodan Network Monitor` 是解决此问题的方案之一。通过 `Network Monitor`，你可以配置 `Shodan` 在网络出现漏洞系统、开放端口或变化时向你告警。还有其他可用网络安全设备可以执行相同的功能。

## 正常安全程序

对待每一个树莓派（以及 IoT 设备！）要像对待任何普通工作站、笔记本电脑或在线设备那样的公司安全思维。不要因为它是树莓派就认为它只是个玩具，或者黑客找不到它，因为他们会——而且可能很快。所以，所有的正常安全程序都适用。虽然没有系统可以保证 100% 安全，但我们可以通过这些技术让我们的系统更难被攻破：

- 补丁与更新
- 防火墙和入侵防御系统 (`IPS`)
- 限制服务与用户权限
- 使用长复杂的密码
- 网络安全监控
- 日志记录
- 用户教育
- 扫描你的网络
- 最后，使用攻击性安全（Offensive Security）

让我们简要查看其中几个主题：

### 补丁与更新

只要可能，务必使用最新版本的操作系统和 Web 服务器应用程序。一旦关键更新发布，请立即安装。黑客正活跃地针对树莓派等 IoT 设备进行攻击，因此将这些设备加入你的更新计划，并积极关注关键更新至关重要。

### 私有局域网与防火墙

我建议为你的树莓派创建一个隔离的私有 IP 地址游乐区。这样，即使它被攻破，攻击者也无法利用它进一步渗透到你的内部网络。此外，最好在你的树莓派和互联网之间始终保持一个硬件防火墙。就在几年前，某些 ISP 仍在为小型办公室和家庭用户提供实时的互联网连接，而他们完全不知道自己需要防火墙。话虽如此，始终使用防火墙，不要在不使用防火墙的情况下将任何系统连接到实时互联网。对入站互联网连接设置防火墙，并确保每个系统都使用软件防火墙。将开放端口限制为绝对必要的那些。创建 `Ingress Rules` 和 `Egress Rules` 策略来监控或控制进出网络的信息。在最简单的层，阻止与没有业务往的国家通信。更高级的系统允许你控制进入离开的数据类型和协议。

### 限制服务与权限级别

关闭服务器和系统上不需要的网络和服务协议。服务器的攻击面越小越好。永远不要让普通用户使用高级安全凭据执行非管理任务。严格限制用户 `Root` 级的使用。

### 复杂密码

这无需多说，对于任何直接连接到互联网的设备（以及 Web 应用），都要使用长复杂的密码。密码越长复杂，攻击者破解所需的时间越长。使用大写和小字母、数字和符号的组合。适用时使用双重身份验证。在一次安全评估中，我发现一个客户用人的名字作为 Web 应用的管理员密码！我用来测试 Web 应用密码的程序几秒钟内就能暴力破解它。我所有的在线个人密码没有短于 16 个字符，我连接到互联网的任何设备使用的都要长得多。为每个服务/设备使用不同的密码（如果可能）。

### 日志记录

确保关键交换机、路由器、防火墙开启安全日志。最好让关键设备和系统将安全日志发送到 `syslog` 服务器，以便备份（以防黑客清除系统日志）并便于应急响应。这有助于在坏情况发生时追踪恶意用户和流量。

### 网络安全监控

我非常喜欢网络安全监控 (NSM)。如果你运行自己的网络却不知道那是什么，快去买一本 Richard Bejtlich 的《The Tao of Network Security Monitoring: Beyond Intrusion Detection》。基本上 `NSM` 是一种捕获所有网络流量（有时在网络多个点）并对其进行入侵分析的系统。如果你认为负担不起 `NSM` 系统，那就错了。最常用的之一是免费的！`Security Onion` 是一个极其强大且功能丰富的 `NSM`。你只需要一台性能尚可的计算机、一个网络分路器（tap）和至少两个网卡。

`Security Onion` 允许你捕获网络流量，然后对其进行分析，并在一个相当易用的界面中通过告警通知你。以下是 `Security Onion` 运行的几个截图。第一张显示了当 `Autopwn` 攻击网络上的某个系统时触发的一系列告警。

![](img/00265.jpeg)

你可以看到有多个警告和告警。最后一行记录了 172 次（CNT 列）同一种告警事件！`Security Onion` 还能捕获网络上的 `TOR` 使用。`TOR` 是一种匿名协议，通过在全球范围内跳转的加密通信来帮助用户匿名。`TOR` 可以用于善意，但黑客也利用 `TOR` 来隐藏他们的攻击。这里是我在 `Security Onion` 监控的测试网络中使用 `TOR` 时发生的情况：

![](img/00266.jpeg)

注意弹出了多个黄色的 `Known TOR Exit Node Traffic` 告警。

文章开头提到的 NASA JPL（喷宇航空动力实验室）网络曾因有人在网络上接入未经授权的 `Pi` 而遭到入侵。因此，让员工了解 IoT 设备（如 `Pi`）对你的网络可能构成的危险至关重要。有些公司通过张挂标牌鼓励使用安全的计算机上网技术，并提醒在在线账户上复杂的唯一密码，并取得了成功。欲了解更多信息，美国计算机应急响应小组（US CERT）在 [`www.us-cert.gov/ncas/tips/`](http://www.us-cert.gov/ncas/tips/) 建立了一个非常好的参考和警告网站。

## 扫描你的网络

如果你是公司安全团队的成员或者是“计算机安全人员”，请在坏人之前扫描你的网络以发现安全问题。仅使用 `Shodan` 就能暴露你网络上可能被遗忘的系统。大型公司通常有很多公开的系统运行着过时的操作系统或 Web 服务器软件。不要忘记检查摄像头、IoT 设备和打印机，它们可能会泄露过多信息，如内部网络信息、`SNMP` 字符串和用户账户。

开源扫描工具（如 `OpenVas`）或商业安全扫描系统（如 `NESSUS`）可用于扫描整个网络以发现安全问题，前提是你有相应的权限。`OpenVas` 预装在 `Kali` 中，虽然让它运行起来需要一些步骤，但网上有大量的教程。

## 攻性计算机安全

学习像书中介绍的那种攻性计算机安全技术。我们只涵盖了攻性安全中最基础的技术。仅仅阅读此书不足以让某人成为“专家”，单凭此也不足以任何人开始在实环境中使用攻性安全技巧。如果你是该领域的新手并想学习更多，有大量的书籍、安全培训研讨会和课程。还有许多故意留漏洞的测试系统和夺旗赛（CTF）系统，你可以在其中合法地尝试并完善你的技能。

最后，联系你当地的 `OWASP` 分会或其他地区的安全小组。参加安全会议并在安全领域建立人脉。当提出好问题时，很多人都很乐意帮助。`SANS` 也有一些非常棒的课程。一旦精通并获得管理层的许可，请测试你网络系统的安全性。

## 结论

我希望你喜欢这本书。写这本书的过程真的非常有趣，也是一个巨大的挑战。如果你有任何问题，请随时通过 [cyberarms@live.com] 与我联系。我的博客上将有一个“错误列表”页面，因为问题会被不断报告，教程也会随时间而变化。我的博客还包含了多年安全领域的笔记和文章，去看看吧！

`DanTheIoTMan.com` 也提供了大量的树莓 `Pi` 教程和指南。

感谢！

Daniel Dieterle

## 资源

1. “NASA 因连接了未经授权的树莓派被黑客” - [`www.zdnet.com/article/nasa-hacked-because-of-unauthorized-raspberry-pi-connected-to-its-network/`](https://www.zdnet.com/article/nasa-hacked-because-of-unauthorized-raspberry-pi-connected-to-its-network/)
2. “Security Onion”，作者 Doug Burks - https://blog.securityonion.net/
3. 选择与保护密码 - [`www.us-cert.gov/ncas/tips/ST04-002`](https://www.us-cert.gov/ncas/tips/ST04-002)
4. 避免社交工程和钓鱼攻击 - [`www.us-cert.gov/ncas/tips/ST04-014`](https://www.us-cert.gov/ncas/tips/ST04-014)
5. 在社交网站上保持安全 - [`www.us-cert.gov/ncas/tips/ST06-003`](https://www.us-cert.gov/ncas/tips/ST06-003)
6. 谨慎使用邮件附件 - [`www.us-cert.gov/ncas/tips/ST04-010`](https://www.us-cert.gov/ncas/tips/ST04-010)
7. 漏洞扫描器 - [`sectools.org/tag/vuln-scanners/`](http://sectools.org/tag/vuln-scanners/)

## 索引

**A**

`ADS-B` · 181

`Alfa AWUS036NHA` · 4

**B**

`Bettercap` · 66, 67, 69, 70, 71, 72, 81

`brute forcing` · 40, 99, 121

**D**

`Darkstat` · 88

**E**

`Ethical hacking` · 3, 6

`Ethical Hacking Issues` · 5

**F**

`Firewall` · 8, 124

`Firewalls and IPS` · 191

`Fluxion` · 77, 78, 79

`Freq Show` · 92, 96

**I**

`Impacket` · 62, 63

`Installing Kali on VMware` · 8

`Internet of Things` · 180

`ipconfig` · 20

**J**

`JoomScan` · 122, 123

**L**

`Limit Services & Authority` · 192

`Logging` · 194
