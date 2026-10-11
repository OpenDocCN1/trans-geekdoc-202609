

## 认证器

认证器：一种设备（如接入点），允许申请者进行身份验证并连接。

### 考试警告

不要混淆 `802.1X` (EAP) 与 `802.11` (无线)。

EAP 解决了许多问题，包括“漫游感染笔记本电脑”问题。携带受感染笔记本电脑的用户插入典型办公网络，并向 DHCP 服务器请求 IP 地址。一旦获得 IP，安装在笔记本电脑上的恶意软件便开始攻击网络上的其他系统。

当笔记本电脑能够请求 IP 地址时，它已经处于可在网络上造成危害的位置，包括机密性、完整性和可用性攻击。此问题在 WLAN 上最为严重（位于距离大楼 100 英尺处的外部笔记本电脑可能即可访问网络）。理想情况下，应在笔记本电脑加入网络前要求进行身份验证：EAP 正是实现这一功能的。

[图 5.23](#Ch005_225-293_B9780443187346000039.xhtml#f0120) 展示了申请者成功进行身份验证并连接到内部网络的过程。步骤 1 显示申请者通过 `EAPOL` (*EAP Over LAN*，LAN 上的 EAP) 进行身份验证，这是一种第 2 层 EAP 实现。步骤 2 显示认证器接收 `EAPOL` 流量，并使用 `RADIUS` 或 `Diameter` 将 EAP 流量传送至认证服务器 (AS)。步骤 3 显示认证器在成功认证后允许申请者访问内部网络。

![图 5.23 成功的 802.1X 认证。](images/B9780443187346000039/f05-23-9780443187346.jpg)

[图 5.23](#Ch005_225-293_B9780443187346000039.xhtml#B-f0120) 成功的 802.1X 认证。

EAP 有多种类型；我们将重点介绍 `EAP-MD5`、`LEAP`、`EAP-FAST`、`EAP-TLS`、`EAP-TTLS` 和 `PEAP`：

*   **EAP-MD5** 是最弱的 EAP 形式之一。它仅提供客户端-服务器端认证（本节讨论的所有其他形式的 EAP 均支持客户端和服务器的相互认证）；这使其容易受到中间人攻击。`EAP-MD5` 也容易受到密码破解攻击。
*   **LEAP** (*Lightweight Extensible Authentication Protocol*，轻量级可扩展认证协议) 是思科专有协议，在 `802.1X` 最终确定前发布。`LEAP` 存在重大安全缺陷，不应使用。
*   **EAP-FAST** (*EAP-Flexible Authentication via Secure Tunneling*，通过安全隧道进行的 EAP 灵活认证) 由思科设计，旨在取代 `LEAP`。它使用 *Protected Access Credential* (PAC，受保护访问凭证)，其作用类似于预共享密钥。
*   **EAP-TLS** (*EAP-Transport Layer Security*，EAP 传输层安全) 使用 PKI，要求同时具备服务器端和客户端证书。`EAP-TLS` 建立用于认证的安全 TLS 隧道。由于使用 PKI，`EAP-TLS` 非常安全，但也因同一原因而复杂且成本高昂。其他主要版本的 EAP 试图在不需要客户端证书的情况下创建相同的 TLS 隧道。
*   **EAP-TTLS** (*EAP Tunneled Transport Layer Security*，EAP 隧道传输层安全) 由 Funk Software 和 Certicom 开发，通过取消客户端证书要求简化了 `EAP-TLS`，允许使用其他认证方法（如密码）进行客户端认证。因此 `EAP-TTLS` 比 `EAP-TLS` 更易于部署，但省略客户端证书时安全性较低。
*   **PEAP** (*Protected EAP*，受保护的 EAP) 由思科系统、微软和 RSA Security 开发，类似于（且可被视为竞争对手）`EAP-TTLS`，同样不需要客户端证书。

## VPN

虚拟专用网络 (VPN) 保护通过互联网等不安全网络发送的数据。其目标是虚拟地提供专线（如 T1）所提供的隐私。VPN 的核心机制涉及安全认证、加密哈希（如 `SHA-1`）以提供完整性，以及加密算法（如 `AES`）以提供机密性。

> **注意**
> 此处讨论的 VPN 协议的加密细节在第 4 章 [第 4 章](#Ch004_107-223_B9780443187346000076_1.xhtml)，领域 3：安全架构与工程中有深入介绍。

### SLIP 和 PPP

`SLIP` (Serial Line Internet Protocol，串行线路互联网协议) 是一种第 2 层协议，通过异步连接（如串行线路和调制解调器）提供 IP 连接。`SLIP` 于 1988 年首次推出时，首次允许通过调制解调器链路路由数据包（此前，调制解调器主要用于非路由的终端访问）。`SLIP` 是一种极简协议，不提供内置的机密性、完整性或认证。`SLIP` 已基本弃用，被 `PPP` 取代。

`PPP` (Point-to-Point Protocol，点对点协议) 是一种第 2 层协议，已基本取代 `SLIP`。`PPP` 基于 `HDLC`（前文已讨论），并通过点对点链路增加了机密性、完整性和认证。除了异步链路（如调制解调器）外，`PPP` 还支持同步链路（如 T1 线路）。

### PPTP 和 L2TP

`PPTP` (Point-to-Point Tunneling Protocol，点对点隧道协议) 通过 IP 隧道传输 `PPP`。它由包括微软、3COM 在内的多家厂商联盟开发。`PPTP` 使用 `GRE` (Generic Routing Encapsulation，通用路由封装) 通过 IP 传输 `PPP`，并使用 TCP 作为控制通道（使用 TCP 端口 1723）。

`L2TP` (Layer 2 Tunneling Protocol，第 2 层隧道协议) 结合了 `PPTP` 和 `L2F` (Layer 2 Forwarding，第 2 层转发，旨在隧道传输 `PPP`)。`L2TP` 专注于认证，不提供机密性：它经常与 `IPsec` 结合使用以提供加密。与 `PPTP` 不同，`L2TP` 也可用于非 IP 网络，如 ATM。

### IPsec

`IPv4` 没有内置机密性；通常使用 `TLS` 等高层协议来提供安全性。为解决第 3 层缺乏安全性的问题，设计了 `IPsec` (Internet Protocol Security，互联网协议安全) 以通过加密为 `IPv6` 提供机密性、完整性和认证。`IPsec` 已移植至 `IPv4`。`IPsec` 是一套协议；主要两个是封装安全载荷 (`ESP`) 和认证头 (`AH`)。每个都有一个 IP 协议号：`ESP` 是协议 50；`AH` 是协议 51。

> **注意**
> 本章描述 `IPsec`、`SSL` 和 `TLS` 的网络方面：这些协议的加密方面见第 4 章 [第 4 章](#Ch004_107-223_B9780443187346000076_1.xhtml)，领域 3：安全架构与工程。

#### IPsec 体系结构

`IPsec` 有三种体系结构：主机到网关、网关到网关和主机到主机。主机到网关模式（也称为客户端模式）用于将运行 `IPsec` 客户端软件的一个系统连接到 `IPsec` 网关。网关到网关（也称为点对点）连接两个 `IPsec` 网关，它们形成的 `IPsec` 连接充当共享可路由网络连接，如 T1 线路。最后，主机到主机模式通过 `IPsec` 将两个系统（如文件服务器）相互连接。许多现代操作系统（如 Windows 10 或 Ubuntu Linux）可原生运行 `IPsec`，允许它们形成主机到网关或主机到主机连接。

#### 隧道模式和传输模式

`IPsec` 可用于隧道模式或传输模式。隧道模式为整个原始数据包（包括原始 IP 头部）提供机密性 (`ESP`) 和/或认证 (`AH`)。会添加新的 IP 头部（包含 `IPsec` 网关的源和目的地址）。传输模式仅保护 IP 数据（第 4-7 层），原始 IP 头部不受保护。两种模式均添加额外的 `IPsec` 头部（一个 `AH` 头部和/或一个 `ESP` 头部）。[图 5.24](#Ch005_225-293_B9780443187346000039.xhtml#f0125) 显示了隧道模式和传输模式的区别。

![图 5.24 IPsec 隧道模式和传输模式。](images/B9780443187346000039/f05-24-9780443187346.jpg)

[图 5.24](#Ch005_225-293_B9780443187346000039.xhtml#B-f0125) IPsec 隧道模式和传输模式。

### SSL 和 TLS

安全套接字层 (`SSL`) 旨在保护 HTTP (Hypertext Transfer Protocol，超文本传输协议) 数据：HTTPS 使用 TCP 端口 443。`TLS` (Transport Layer Security，传输层安全) 1.0 等同于 `SSL` 3.1 版。`TLS` 当前版本为 1.3，详见 RFC 8446（参见 [https://datatracker.ietf.org/doc/html/rfc8446](https://datatracker.ietf.org/doc/html/rfc8446)）。

