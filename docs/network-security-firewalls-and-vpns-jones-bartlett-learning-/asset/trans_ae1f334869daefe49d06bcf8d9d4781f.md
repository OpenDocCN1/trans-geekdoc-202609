

# 使用 Openswan 实现 Tor 和 VPN

## Tor 匿名性与风险

Tor 的目标是允许用户匿名浏览互联网。Tor 不直接连接到互联网站点，而是将其他 Tor 用户的计算机用作中继或代理。任何单个 Tor 连接都将经过多台其他计算机。

有趣的是，尽管 Tor 最初是由美国海军研究实验室设计的，但它在大多数政府系统中是被禁止的。主要原因与数据泄露有关。虽然 Tor 网络确实提供了一定程度的匿名性，但用户永远不知道请求会经过哪些其他计算机。发送和接收的数据可能被这些计算机中的任何一台捕获。

例如，2007 年，瑞典的安全专家 Dan Egerstad 收集了不同大使馆 100 个电子邮件账户的用户名和密码。他只是在自己的系统上安装了 Tor，然后捕获了所有经过它的数据。他的计算机在 Tor 网络中被用作数千用户的代理，一个简单的协议分析器就捕获了这些数据。除了凭据，他还捕获了大量来自大使馆和财富 500 强公司的敏感电子邮件。

![Image](images/note.jpg) **注意**

您可以在 [www.openswan.org](http://www.openswan.org) 下载 Openswan RPM 包。RPM 包的扩展名为 `.rpm`（源自最初的 Red Hat Package Manager 标准，被当今许多 Linux 发行版使用）。请注意，要下载 Openswan 的 RPM 版本，您的系统上必须已安装 `IPSec-tools` RPM 包。

## 规划 VPN 实施

VPN 与分支机构、远程员工、业务合作伙伴或客户创建安全的数据链路，这将启用或要求防火墙后的服务器访问。VPN 可以在防火墙与远程客户端或服务器之间提供安全且加密的数据流。

本节将为您提供使用 Openswan 配置永久站点到站点 VPN 隧道的方法，Openswan 是 Linux 最流行的 VPN 软件包之一。

### 要求

对于此实施，您需要 Linux 内核 2.0、2.2、2.4 或 2.6。

![Image](images/bull1.jpg) 对于 Linux 内核 2.0 或 2.2，请使用 Openswan 1.0.10。

![Image](images/bull1.jpg) 对于 Linux 内核 2.4 和 2.6，请使用 Openswan 2.4.*x*。

![Image](images/bull1.jpg) 对于 FreeBSD、OpenBSD、NetBSD 和 OSX，请使用 Openswan 2.5.*x*。

在尝试这个简单的 SOHO Linux VPN 之前，请记住以下几点：

![Image](images/bull1.jpg) VPN 所基于的 IPSec 协议不能容忍其数据包的网络地址转换 (NAT)。如果您的防火墙执行 NAT，则必须专门为将穿越 VPN 的数据包禁用它。

![Image](images/bull1.jpg) 您还应将 Linux VPN 盒子设置为防火墙。先配置并测试防火墙，然后再配置 VPN。

![Image](images/bull1.jpg) VPN 隧道两端的网络必须使用不同的 IP 地址范围。例如，组织的内部网络可能使用 `192.168.0.1` 到 `192.168.0.254` 的 IP 地址范围。另一网络必须使用不同的地址范围，例如 `192.168.1.1` 到 `192.168.1.254`。为避免混淆，您可能希望为每个网络使用完全不同的私有地址范围，例如 `172.16.y.z.` 或 `10.x.y.z.`。

![Image](images/bull1.jpg) 永久站点到站点 VPN 需要两端都使用静态 IP 地址的防火墙。

[图 14-2](#22_chapter14.xhtml#fig14-2) 描绘了两个环境之间 VPN 的 Openswan 示例拓扑图。

![Image](images/note.jpg) **注意**

在此实施中，机器的外部 IP 列为 `12.34.56.78`。网关 IP 列为 `12.34.56.1`。VPN 服务器的内部 IP（因为它在内部和外部都有 NIC）在本例中为 `192.168.1.1`。您可以根据需要进行更改。

![Image](images/pg410.jpg)

**图 14-2**

Openswan 示例拓扑图。

![Image](images/pg411-1.jpg)

**图 14-3**

从源代码安装 Openswan。

![Image](images/pg411-2.jpg)

**图 14-4**

使用 Openswan 的仅用户空间安装。

## 安装

您可以通过两种不同的方式安装 Openswan：执行 RPM 安装或从源代码 `libgmp` 开发库安装。

### 执行 RPM 安装

您会发现根据您使用的 UNIX/Linux 版本不同，安装 Openswan 的说明也不同。Openswan 托管了一个 Wiki 站点，其中包含许多不同类型 RPM 安装的说明，网址为 [http://wiki.openswan.org/](http://wiki.openswan.org/)。该站点还包含大量关于安装、配置和排除 Openswan 故障的其他详细信息。

### 从源代码安装

以 root 身份，将 Openswan 源代码解压到驱动器上的某个位置，例如 `/usr/src`。[图 14-3](#22_chapter14.xhtml#fig14-3) 提供了一个示例。

现在您需要选择安装方法。您可以为 2.6 内核选择仅用户空间安装，或为 2.6 或更早版本的内核（2.0、2.2 和 2.4）选择 KLIPS 安装。如果您决定使用仅用户空间安装，请进入新的 Openswan 目录，然后制作并安装 Openswan 的用户空间工具，如 [图 14-4](#22_chapter14.xhtml#fig14-4) 所示。

完成这些命令的输入后，安装应已完成。现在您只需要启动 Openswan 并测试您的新安装。如果您决定使用 KLIPS，您将不得不制作其模块，以及您为 VPN 所需的其他 Openswan 程序。为此，请输入 [图 14-5](#22_chapter14.xhtml#fig14-5) 中显示的命令序列，这将进入您的新 Openswan 目录，制作 Openswan 模块，并安装所有内容。

![Image](images/note.jpg) **注意**

内核 IP 安全 (KLIPS) 修改 Linux 内核以支持 IPSec 协议。

![Image](images/pg411-3.jpg)

**图 14-5**

执行 Openswan 的 KLIPS 安装。

![Image](images/pg412-1.jpg)

**图 14-6**

将 KLIPS 静态链接到您的内核中。

![Image](images/pg412-2.jpg)

**图 14-7**

启动 Openswan。

此时，您实际上可以通过使用 NAT 遍历 (NAT-T) 支持来增强 VPN 的安全性。NAT-T 是一种将 IPSec ESP 数据包封装到 UDP 数据包中的方法，用于通过采用网络地址转换 (NAT) 的路由器或防火墙。要部署 NAT-T，您需要修补并重建内核。然而，重建内核是一项有风险的操作，因此应谨慎对待。

要将 KLIPS 静态链接到您的内核中（使用您的旧内核设置）并安装其他 Openswan 组件，只需遵循 [图 14-6](#22_chapter14.xhtml#fig14-6) 中列出的命令，然后重新启动系统并测试您的安装。

![Image](images/note.jpg) **注意**

有关安装 NAT-T 的更多信息，请查看 Openswan 网站 [http://wiki.openswan.org/index.php/Openswan/NATTraversal](http://wiki.openswan.org/index.php/Openswan/NATTraversal)。

## 启动 Openswan

要启动 Openswan，请输入 [图 14-7](#22_chapter14.xhtml#fig14-7) 中显示的命令。

如果您已重新启动系统，则此步骤不是必需的，因为 Openswan 在成功安装后将自动启动。

您可以采取额外措施来保护 VPN 连接。例如，您可以使用基于证书的密钥来保护连接。您可以遵循此处的一个优秀演练步骤：[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch35_:_Configuring_Linux_VPNs](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch35_:_Configuring_Linux_VPNs)。

## 部署

在部署 VPN 之前，您需要在两个 VPN 设备上启动 Openswan，以使新的 `/etc/ipsec.conf` 设置生效。您可以通过发出以下命令来执行此操作：

![Image](images/pg412-3.jpg)

