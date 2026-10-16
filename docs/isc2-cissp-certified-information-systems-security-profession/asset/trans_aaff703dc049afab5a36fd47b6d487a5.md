
VPN 可以使用软件或硬件方案实现。无论哪种情况，都有四种常见的 VPN 协议：`PPTP`、`L2F`、`L2TP` 和 `IPsec`。`PPTP`、`L2F` 和 `L2TP` 都在 OSI 模型的数据链路层（第 2 层）运行。`PPTP` 和 `IPsec` 仅限于 IP 网络使用，而 `L2F` 和 `L2TP` 可以封装任意局域网协议。

#### Point-to-Point Tunneling Protocol

*`Point-to-Point Tunneling Protocol (PPTP)`* 是基于拨号点对点协议（Point-to-Point Protocol）开发的封装协议。它在 OSI 模型的数据链路层（第 2 层）运行，用于 IP 网络。PPTP 在两个系统之间创建点对点隧道并封装 PPP 包。它通过 PPP 支持的相同认证协议对认证流量提供保护：

*   `Microsoft Challenge Handshake Authentication Protocol (MS-CHAP)`

*   `Challenge Handshake Authentication Protocol (CHAP)`

*   `Password Authentication Protocol (PAP)`

*   `Extensible Authentication Protocol (EAP)`

*   `Shiva Password Authentication Protocol (SPAP)`

PPTP 使用的初始隧道协商过程不加密。因此，包含发送方和接收方 IP 地址的会话建立包（可能还包含用户名和哈希密码）可能会被第三方截获。PPTP 用于 VPN，但通常会被 L2TP 取代，后者可以使用 IPsec 提供流量加密。大多数现代 PPTP 使用都采用了微软定制实现，支持使用 Microsoft Point-to-Point Encryption（MPPE）进行数据加密，并支持多种安全的认证选项。

PPTP 不支持 TACACS+ 和 RADIUS。

#### Layer 2 Forwarding Protocol and Layer 2 Tunneling Protocol

思科自行开发的 VPN 协议是 Layer 2 Forwarding（L2F），它是一种双向认证的隧道机制。但 L2F 不提供加密。L2F 并未被广泛部署，很快就被 L2TP 取代。从名称上看，两者都在第 2 层工作，并且都能封装任意局域网协议。

*`Layer 2 Tunneling Protocol (L2TP)`* 是将 PPTP 和 L2F 的元素组合而成的协议。L2TP 在通信端点之间创建点对点隧道。它本身没有内置加密方案，但通常依赖于 IPsec 作为安全机制。L2TP 还支持 TACACS+ 和 RADIUS。IPsec 常被用作 L2TP 的安全机制。

#### IP Security Protocol

当前最常用的 VPN 协议是 IPsec。`IP Security (IPsec)` 既是独立的 VPN 协议，也是 L2TP 的安全机制，并且只能用于 IP 流量。IPsec 是为 IPv4 添加到 IPv6 的安全元素而构建的附加包。它仅在 IP 网络上工作，并提供安全的认证以及加密的数据传输。IPsec 有两个主要组件或功能：

***Authentication Header (AH)*** AH 提供认证、完整性和不可否认性。

***Encapsulating Security Payload (ESP)*** ESP 用于加密保护传输数据的机密性，同时可以执行有限的认证。它在网络层（第 3 层）运行，可以在传输模式或隧道模式下使用。在传输模式下，仅 IP 包的数据被加密，但报头不被加密；在隧道模式下，整个 IP 包被加密并在报头上添加新的报头以管理隧道传输。

[Table 12.1](#c12.xhtml#table12-1) 展示了 VPN 协议的主要特性。

[**TABLE 12.1**](#c12.xhtml#tableanchor12-1) **VPN characteristics**

| VPN Protocol || Native Authentication Protection || Native Data Encryption || Protocols Supported || Dial-Up Links Supported || Number of Simultaneous Connections |
| --- | --- | --- | --- | --- | --- |
| PPTP || Yes || No || PPP || Yes || Single point-to-point |
| L2F || Yes || No || PPP/SLIP || Yes || Single point-to-point |
| L2TP || Yes || No (can use IPsec) || PPP || Yes || Single point-to-point |
| IPsec || Yes || Yes || IP only || No || Multiple |

能够封装 PPP 的 VPN 协议能够支持与 PPP 兼容的任何子协议，包括 IPv4、IPv6、IPX 和 AppleTalk。

VPN 设备是一种网络附加设备，用于在服务器或客户端操作系统之外单独创建 VPN 隧道。VPN 设备对网络化系统是透明的。

### Virtual LAN

*Virtual local area network (VLAN)* 是由交换机硬件强制实现的网络分段。默认情况下，交换机的所有端口都属于 VLAN 1。但当交换机管理员按端口逐一更改 VLAN 分配时，各个端口可以被分组并与其他 VLAN 的端口保持区分。VLAN 也可以根据设备的 MAC 地址、协议、或认证情况来分配或创建，类似于 IP 子网划分。VLAN 管理最常用于区分用户流量和管理流量。VLAN 1 通常被指定为管理流量的 VLAN。

VLAN 用于流量管理。同一 VLAN 内成员的通信不受阻碍，但不同 VLAN 之间的通信需要路由功能，这可以由外部路由器或交换机的内部软件提供（这也是 *L3 switch* 和 *multilayer switch* 之称的原因）。VLAN 如同子网，但不是子网。VLAN 由交换机创建，子网则由 IP 地址和子网掩码 assignments 创建。

*`VLAN management`* 是使用 VLAN 为安全或性能原因控制流量的做法。VLAN 可以用于隔离网络段之间的流量。通过不在不同 VLAN 之间定义路由，或在特定 VLAN（或 VLAN 内的特定成员）之间设置拒绝过滤来实现。任何不需要与另一网络段通信以完成工作任务的网络段都不应允许其通信。使用 VLAN 来允许必要的通信，阻止不必要的通信。记住，“默认拒绝，仅允许例外”不仅适用于防火墙规则，也适用于整体安全策略。

VLAN 的工作方式与传统子网相似。要在两个 VLAN 之间进行通信，交换机会执行路由功能来控制和过滤 VLAN 之间的流量。

VLAN 用于逻辑上分段网络而不改变其物理拓扑。实现简便，管理开销小，是硬件解决方案（具体为第 3 层交换机）。当网络在虚拟环境或云端构建时，常使用软件交换机。在这些情况下，VLAN 不是硬件基础，而是基于软件的实现。

VLAN 可以控制和限制广播流量，并通过将每个 VLAN 视为独立的网络分段，降低嗅探器的威胁。要在不同段之间通信，交换机必须提供路由功能。路由功能阻止子网和 VLAN 之间的广播，因为路由器（或执行第 3 层路由功能的设备，如第 3 层交换机）不会转发层 2 以太网广播。此特性阻止了 VLAN 之间的以太网广播，从而帮助防止广播风暴。广播风暴是不受控制的以太网广播流量洪lood。

