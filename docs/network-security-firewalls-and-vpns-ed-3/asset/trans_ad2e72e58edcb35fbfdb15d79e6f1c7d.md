

## Internet Key Exchange v2

**Internet Key Exchange v2 (IKEv2)** 是一种基于 IPSec 的 VPN 协议，它使用 NAT 遍历（`NAT-T`）。`NAT-T` 允许 IPSec 流量通过 NAT 服务器。与 IKE 相比，IKEv2 提供了显著的改进，并已被多家公司采用，包括 Microsoft（在 Windows Server 2008 R2 及更高版本中）、Cisco 和 OpenVPN Inc.。**OpenVPN** 是本章后面介绍的一种开源解决方案。IKEv2 需要公钥基础设施（`PKI`）支持以获取和使用证书。

每种方法都有其优势，具体取决于用户的访问需求和组织的 IT 流程。尽管许多解决方案仅提供 IPSec 或 SSL/TLS，但一些供应商（包括 Microsoft 和 Cisco）在统一管理的单一平台上集成了多种技术。同时提供 IPSec 和 SSL/TLS 技术，可以使组织在无需额外硬件或管理复杂性的情况下，定制远程访问 VPN。

基于 SSL/TLS 的 VPN 使用 Web 浏览器及其原生的 SSL/TLS 加密，能够从几乎任何支持 Internet 的位置实现远程访问连接。它不需要预先安装任何专用客户端软件。这使得远程访问 SSL/TLS VPN 能够从公司管理的台式机和非公司管理的系统（如员工的 PC、承包商或业务合作伙伴的台式机以及 Internet 亭）实现“随地”连接。跨 SSL/TLS VPN 连接进行应用程序访问所需的任何软件都会按需动态下载，从而将桌面软件维护降至最低。

基于 IPSec 的 VPN 是组织采用的经过部署验证的远程访问技术。IPSec VPN 连接使用用户系统上预装的 VPN 客户端软件，主要面向公司管理的台式机。基于 IPSec 的远程访问通过修改 VPN 客户端软件，提供了通用性和可定制性。利用 IPSec 客户端软件中的 API，组织可以控制 VPN 客户端的外观和功能，用于无人值守亭、与其他桌面应用程序集成以及其他特殊部署等应用场景。

### 在 IPSec 和 SSL/TLS 远程访问 VPN 之间进行选择

IPSec 和 SSL/TLS VPN 技术均可访问几乎任何网络应用程序或资源。SSL/TLS VPN 提供了额外功能，例如从非公司管理的台式机轻松连接、极少或无需桌面软件维护，以及登录时用户自定义的 Web 门户。IPSec 的主要缺点是它无法穿越 NAT 服务器。如果您要部署 VPN 服务器并希望连接通过 NAT 服务器，则 SSL/TLS 是一个可靠的解决方案。

可以使用 NAT 遍历（`NAT-T`）允许 IPSec 流量通过 NAT 服务器，但请注意它存在一些问题。例如，Microsoft 专门建议不要使用 `NAT-T`，尽管 IT 专业人员仍建议在非 Microsoft 主机上使用 `NAT-T`。

## 远程桌面服务

**远程桌面服务（RDS）** 是一款内置的 Microsoft Server 产品，具有多种用途。它主要以两种模式工作：**远程桌面会话主机（RD 会话主机）** 和 **远程桌面虚拟化主机（RD 虚拟化主机）**。使用 `RD 会话主机` 时，服务器通常为日常用户工作负载提供桌面会话池和应用程序。在 `RD 虚拟化主机` 模式下，服务器通常在虚拟机中提供个人桌面会话。这两种模式都允许管理员提供多个虚拟桌面，每个桌面的使用方式都就像用户的主工作站一样。

RDS 还包含其他组件，包括 **RD RemoteApp** 和 **RD Web Access**。

### RD RemoteApp

在远程服务器上运行应用程序面临的挑战之一是其呈现给用户的外观怪异，导致用户难以适应。**RD RemoteApp** 是一种 Microsoft 解决方案，它运行在 Microsoft RDS 服务器上，但对最终用户而言，看起来就像实际运行在他们的系统上一样，无论他们使用什么操作系统。用户无需打开 RDS 会话；相反，他们从“开始”菜单或计算机上的快捷方式启动应用程序。该应用程序会在用户计算机上的一个窗口中显示，就像在本地计算机上运行一样。

### RD Web Access

**RD Web Access** 是一种 RDS 服务器角色，允许从 Web 浏览器启动桌面和 RD RemoteApp 应用程序。除了常规的 RDS 基础设施外，RD Web Access 还需要 **Internet Information Services (IIS)** 才能正常工作。

管理员可以将虚拟桌面和 RD RemoteApp 应用程序集成到网页中，这些网页看起来像是从 Web 服务器启动的。换句话说，客户端使用 Web 浏览器访问一个网站。在这个网站内，他们可以点击桌面或 RD RemoteApp 应用程序的链接。RD Web Access 可以配置在内部 Intranet 中，也可以让用户从 Internet 访问。

RD Web Access 允许远程客户端连接到内部资源，而无需 VPN。根据远程客户端的需求，这可能是一个合适的替代方案。

### RDS 和托管服务

过去几年里，许多软件发行商尝试提供托管服务。托管服务架构的基本理念是：组织无需购买软件应用程序的许可证，也无需承担安装或维护这些应用程序的麻烦。相反，ISP 或软件供应商将应用程序租赁给组织。应用程序实际运行在服务提供商的服务器上，用户通过 Internet 与应用程序交互。

然而，这种安排也有一些缺点。例如，托管服务将应用程序的配置移出了组织的直接控制范围。网络管理员因其公司决定将所有应用程序外包给托管提供商而失业的情况并不罕见。反对使用托管服务的另一个有力论据与服务可用性有关。如果您的 Internet 连接失败，没有人能访问托管应用程序。当然，某些地区的 Internet 服务比其他地区更可靠。

用于托管应用程序的远程桌面服务具有许多优势。主要优势是服务提供商会为您处理所有应用程序维护。如果您在每个单独的工作站上本地安装应用程序，或者将应用程序外包给托管提供商，就无法获得其中许多优势。Microsoft 产品可以使用 RD RemoteApp 和 RD Web Access 提供托管应用程序。

## Microsoft DirectAccess

**DirectAccess** 是一种 Microsoft 解决方案，可用作传统 Internet Engineering Task Force（`IETF`）VPN 的替代方案。它允许远程客户端连接到内部服务器，而无需发起 VPN 连接。只要客户端具有 Internet 连接，系统就应该能够使用 DirectAccess 访问内部资源。

Microsoft 在 Windows 7 和 Windows Server 2008 R2 产品中引入了 DirectAccess，并在 Windows 10 和 Windows Server 2019 中继续提供支持。一旦在客户端和服务器上配置完成，它对客户端来说相对不可见。客户端计算机连接到 DirectAccess 计算机，后者充当通往内部资源的网关。只有配置为允许 DirectAccess 访问的资源才可从客户端获取。换句话说，您内部网络中可能有 10 台服务器，但可以选择只让其中少数几台可供访问。

