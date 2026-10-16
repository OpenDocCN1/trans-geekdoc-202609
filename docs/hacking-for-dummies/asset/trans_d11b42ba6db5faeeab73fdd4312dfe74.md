
Wi‑Fi 易受攻击 —  — 有时甚至比有线网络（如 [第 9 章](#c09.xhtml) 讨论的）更易受攻击，如果未正确配置和部署。无线网络可能存在长期漏洞，使攻击者能够将你的网络击垮，或让敏感信息在“空中”被提取。如果你的无线网络被入侵，你可能会遇到以下问题：

* 失去网络访问权，包括电子邮件、网页和其他服务，可能导致业务停机。

* 失去敏感信息，包括密码、客户数据和知识产权。

* 因未经授权的用户访问业务系统而产生的监管后果和法律责任。

大多数无线漏洞来源于 802.11 标准的实现。无线接入点（路由器）和无线终端系统也可能存在漏洞。

近年来出现了许多针对这些漏洞的修复措施，但许多修复未能正确应用或默认未启用。此外，员工可能在未经你知晓的情况下在网络上安装野生无线设备。还有“免费” Wi‑Fi 无处不在 —  — 你的移动员工去的咖啡店、酒店、会议中心甚至飞机上的无线网络，这些公共 Wi‑Fi 可能对整体信息安全构成严重威胁，而且很难应对。即使 Wi‑Fi 已加固且所有最新补丁已应用，你仍可能面临服务拒绝（DoS）、中间人攻击以及加密密钥弱点（如有线网络的情况；参见 [第 9 章](#c09.xhtml)），这些问题可能会长期存在。

## 选择你的工具

为 Windows 和 Linux 平台提供了多种优秀的无线安全工具。早期的 Linux 无线工具配置和使用较为困难，可能是因为我本身不够聪明。近年来，随着 Kismet（[`https://www.kismetwireless.net`](https://www.kismetwireless.net)）、Wellenreiter（[`https://sourceforge.net/projects/wellenreiter`](https://sourceforge.net/projects/wellenreiter)）以及 Kali Linux（[`https://www.kali.org`](https://www.kali.org/)）等程序的出现，这一局面已有所改变。

![tip](images/tip.png)如果你想使用运行在 Linux 上的安全工具的强大功能，但不想花费时间安装和配置 Linux 或下载设置众多流行的安全工具，我强烈推荐使用 Kali Linux。该可启动的 Debian‑基础安全测试套件预装了相对易用的大量工具。其他可启动（或 Live）测试套件还包括基于 Fedora Linux 的 Network Security Toolkit（[`www.networksecuritytoolkit.org`](http://www.networksecuritytoolkit.org)）。完整的 Live 启动 Linux 工具列表可查阅 [`www.livecdlist.com`](http://www.livecdlist.com)。

本章概述的大多数测试只需 Windows‑基础实用工具，但使用你最熟悉的平台会获得更好结果。我最喜欢的用于评估无线网络的 Windows 工具包括：

* Aircrack-ng（[`http://aircrack-ng.org`](http://aircrack-ng.org)）

* CommView for WiFi（[`https://www.tamos.com/products/commwifi`](https://www.tamos.com/products/commwifi)）

* ElcomSoft Wireless Security Auditor（[`https://www.elcomsoft.com/ewsa.html`](https://www.elcomsoft.com/ewsa.html)）

* Omnipeek（[`www.savvius.com`](http://www.savvius.com)）

![tip](images/tip.png)你也可以使用便携式无线安全测试设备，例如 Canary Wireless 的 Digital Hotspotter（[`www.canarywireless.com`](http://www.canarywireless.com)），甚至可以使用 Android 手机或平板上的 WiEye 或 Wifi Analyzer 等应用，或 iOS 设备上的 Network Analyzer Pro 和 Network Multimeter。此外，还应考虑外置天线作为你的装备之一。我曾经在没有天线的情况下运行测试并取得良好结果，但实际效果取决于你距离信号的远近。如果你在现场进行无线信号踏勘，使用额外天线可以提高发现合法及（更重要的）未经授权无线系统的机会，但通常并不必需。你可以在三种类型的无线天线中选择：

* **全向性（Omnidirectional）**：在 360 度范围内传输和接收无线信号，适用于会议室或接待区等较短距离场景。此类天线（也称为 *dipole*）通常已在出厂的接入点（AP）上预装。

* **半向性（Semidirectional）**：在中等距离内方向聚焦传输和接收无线信号，适用于走廊或办公楼/建筑的一侧。

* **定向性（Directional）**：在长距离内高度聚焦传输和接收无线信号，适用于建筑物之间的链接。此类天线（也称为高增益天线）是无线黑客在城市巡逻寻找弱点接入点（即 *wardriving*）时首选。

![tip](images/tip.png)作为前述天线的替代方案，你可以使用一种名为 *cantenna* 的巧妙设计 —  — 用土豆片、咖啡罐或猪肉罐制成的创意天线。如果你想尝试这种天线，可参考 [`www.turnpoint.net/wireless/has.html`](http://www.turnpoint.net/wireless/has.html) 的文章获取详细信息。简单的 Internet 搜索会提供大量相关信息，供有兴趣的读者参考。

## 发现无线网络

当你拥有无线卡和无线测试软件时，即可开始操作。首要任务是收集关于你无线网络的信息，具体方法如下章节所述。务必在生产无线网络、访客无线网络以及你可能使用的测试无线系统上进行这些检查 —  — 你永远不知道漏洞就在哪里！

### 检查全球认可度

第一项测试只需你的接入点（AP）的媒体访问控制（MAC）地址以及 Internet 访问权限。（有关 MAC 地址的更多信息请参见本章后的 “[MAC 伪造](#c10.xhtml#c10-sec-0015)”。）该测试旨在判断是否有人在公开场合发现了你的 Wi‑Fi 信号并将其发布供全世界查看。具体步骤如下：

1. **获取 AP 的 MAC 地址。**

   如果不确定 AP 的 MAC 地址，可以在 Windows 命令提示符中使用 `arp -a` 命令查看。你可能需要先向接入点的 IP 地址发送 ping，使其 MAC 地址加载到地址解析协议（ARP）缓存中。图 10-1（[`#c10-fig-0001`](#c10.xhtml#c10-fig-0001)）展示了这一过程的示例。

2. **在 WiGLE 数据库（`https://wigle.net`）中浏览。**

3. **注册站点以便进行数据库查询。**

   进行此查询很有价值。

4. **点击网站右上角的“Login”链接，选择“View”，然后选择“Search”。**

   你会看到类似于图 10-2（[`#c10-fig-0002`](#c10.xhtml#c10-fig-0002)）的界面。

5. **在图 10-2 中的 BSSID/MAC 文本框里输入你的 MAC 地址格式。**

   你也可以输入地理坐标和 SSID（服务集标识符）等 AP 信息。

