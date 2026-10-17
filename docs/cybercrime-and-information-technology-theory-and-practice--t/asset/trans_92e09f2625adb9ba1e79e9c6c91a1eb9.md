

* `Unsecured Wi-Fi connections` 可被黑客用于分发恶意软件。如果用户在使用不安全的 Wi-Fi 连接时允许文件共享，黑客可以轻松地在受害者的电脑上植入恶意软件。

* 在某些情况下，黑客可能会创建一个恶意热点，并将其命名为知名商店或地点，希望诱骗用户使用设备连接上去。

用户如何保持安全？

在使用公共 Wi-Fi 连接时，可以采取一些预防措施：

* 设置 `VPN`，它可以防止中间人攻击。

* 使用强密码并配合双因素身份验证（`2FA`），登录账户时需要额外的步骤，例如发送到手机的验证码或插入电脑的物理密钥。

* 禁用 Wi-Fi 的自动连接功能。

* 使用超文本传输安全协议（`HTTPS`）访问最安全的网站。

* 使用公共 Wi-Fi 连接时，警惕网络钓鱼诈骗。

[Figure 6.18](#c6.xhtml#f6.18) 展示了从 2000 年代初至今最重大网络攻击的演变过程。从 2000 年初到 2004 年，我们主要看到的是蠕虫；从 2005 年到 2012 年，我们看到了现代恶意软件的兴起；从 2013 年至今，我们经历了勒索软件以及与国家犯罪组织相关的 APT 攻击。这些国家行为体针对包含敏感数据的政府和商业网络，例如 COVID-19 疫苗研究，以及关键基础设施。

![FIGURE 6.18 The evolution of the most important attacks.](images/fig6.18.jpg)

**FIGURE 6.18** The evolution of the most important attacks.

## [6.4 预防机制](#contents.xhtml#re_h-6-15)

### [6.4.1 连接即防护](#contents.xhtml#re_h-6-16)

`firewall` 是一段硬件，有时是独立系统或路由器的一部分，或者是软件应用程序，或两者的结合，它根据一组定义好的规则，筛选进出网络的流量。

除了防火墙之外，`IDS` 和 `IPS` 等其他系统也是网络安全环境的一部分。

* 防火墙是第一道防线，就像受信任的内部网络（称为子网）与不安全的互联网之间的围栏。防火墙确保只有特定类型的流量才能进入和离开网络。

* IDS 系统检测攻击，使用攻击类型数据库对其进行识别，记录攻击，并在攻击具有恶意时向 IT 管理员发送警报。

* IPS 检查网络中流动的流量，寻找任何可疑之处，并阻止或拦截可疑连接，提供警报，并清理恶意网络流量，防止其到达网络的其余部分。与 IDS 类似，IPS 位于防火墙和网络其余部分之间。

> IDS 和 IPS 中安全网关区别的最佳示例是：IDS 安全网关的工作方式就像社区内的巡逻车，监控活动并寻找异常情况。IPS 安全网关的运作方式就像大门口的保安，根据凭据和预定义的规则集或策略来允许或拒绝访问。无论大门口的安全性有多强，巡逻车仍将在一个提供其自身检查的系统中运行。^([^(331)](#fn331))

内部网络上的计算设备与互联网或外部世界之间的分离，被称为 `Demilitarized Zone (DMZ)` 或 `perimeter network`。该区域位于内部网络和外部网络之间。互联网无法直接与内部网络建立连接，但可以与 DMZ 建立连接。如果将网络安全视为洋葱，DMZ 就是洋葱皮，也就是洋葱的第一层。

在网络中实现 DMZ 有几种方法。一种方法是使用 `single firewall model` ([Figure 6.19](#c6.xhtml#f6.19))，它需要三个网络接口（设备）或一个三腿防火墙。在这种情况下，DMZ 将位于此防火墙内部。第一个网络接口（被视为不受信任）连接到外部公共互联网连接。第二个接口（被视为受信任）连接到内部网络或 LAN。第三个接口直接连接到 DMZ。通常，在 DMZ 内部，您会发现电子邮件服务器、文件传输协议（`FTP`）服务器、DNS 服务器、Web 服务器、域控制器、数据库服务器和 HTTPS 流量。

![FIGURE 6.19 The single firewall model.](images/fig6.19.jpg)

**FIGURE 6.19** The single firewall model.

`dual firewall model` 使用两个独立的防火墙。一个面向互联网，称为 `front-end firewall`，另一个面向受信任的内部网络或子网，称为 `back-end firewall`。`front-end firewall` 配置为仅允许发往 DMZ 的流量。`back-end firewall` 负责监管受信任内部网络上的网络流量，或从 DMZ 到内部网络的流量。

云计算通过允许使用 VPN 服务连接本地或本地部署网络与基于云的网络之间的安全访问，改变了 DMZ 的角色。大多数公司使用云服务提供商并部署 SaaS 应用程序。DMZ 是网络安全的重要组成部分，用于限制远程访问并防止未经授权访问内部服务器。[Figure 6.20](#c6.xhtml#f6.20) 演示了双防火墙模型。

![FIGURE 6.20 The dual firewall model.](images/fig6.20.jpg)

**FIGURE 6.20** The dual firewall model.

防火墙如何执行监控服务和阻止恶意或不需要的流量的工作？它阻止什么？

防火墙执行以下操作：

* 在设备接口上，防火墙过滤源端口和目标端口，包括 OSI 模型第 2 层流量。

* 关于数据包头部，防火墙过滤源 IP 地址和目标 IP 地址上的流量，包括 OSI 模型第 3 层路由接口 IPv4 和 IPv6 接口。它根据数据包头部信息中的参数提供不同级别的保护，包括 TCP、UDP 和 ICMP 等协议。

* 防火墙逐个数据包地拒绝或接受网络流量，可通知发送方，也可不通知。

* 防火墙记录数据包信息。

* 防火墙强制执行安全策略，例如设置警报、过滤规则和修改数据包，并在黑客扫描公共 IP 地址以寻找开放端口时，检测、阻止和拒绝恶意请求。

在大多数操作系统中，服务器包含内置防火墙，连同其无线路由器。例如，Mac OS 中内置了防火墙。它位于系统偏好设置、安全性与隐私、防火墙下。Linux 和 Windows 操作系统中包含防火墙，在 Windows 中称为 Windows Defender。Bitdefender、Kaspersky、Norton 和 McAfee 等安全公司以及 ISP 提供用于个人使用的其他防火墙解决方案。在企业级别，网络防火墙必须能够保护更复杂的网络，例如云环境、数据中心部署和远程站点。提供企业级防火墙的领先公司包括 Barracuda Networks、Check Point、Cisco systems、Juniper、Palo Alto Networks 和 SonicWall。[Figure 6.21](#c6.xhtml#f6.21) 显示了网络上的典型防火墙设置。

![FIGURE 6.21 A typical firewall setup on a network.](images/fig6.21.jpg)

**FIGURE 6.21** A typical firewall setup on a network.

### [6.4.2 防火墙类型](#contents.xhtml#re_h-6-17)

