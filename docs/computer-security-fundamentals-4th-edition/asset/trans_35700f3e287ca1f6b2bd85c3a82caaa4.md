
-   [VPN（或虚拟专用网络）本质上是利用互联网为远程用户或站点与中央位置之间创建虚拟连接的方式。在这条连接上传输的数据包会被加密，从而实现隐私性。VPN 必须模拟直接网络连接。

-   创建 VPN 的三种协议分别是：

    *   Point-to-Point Tunneling Protocol（PPTP）
    *   Layer 2 Tunneling Protocol（L2TP）
    *   Internet Protocol Security（IPsec）

-   这些协议的详细内容将在后续章节中进一步说明。

#### Point-to-Point Tunneling Protocol

-   *Point-to-Point Tunneling Protocol*（*[PPTP](#glossary.xhtml#gloss65)*）是三种用于 VPN 的协议中最老的一个。它最初是作为对 Point-to-Point Protocol（PPP）的安全扩展而设计的。PPTP 最初于 1996 年由 PPTP Forum（包括 Ascend Communications、ECI Telematics、Microsoft、3Com 和 U.S. Robotics 等公司）提出，作为一种标准。它在 PPP 协议基础上增加了对数据包加密和用户认证的功能。PPTP 在 OSI 模型的数据链路层工作（详见 [第 2 章](#ch02.xhtml#ch02) “[网络与互联网](#ch02.xhtml#ch02)”）。

-   PPTP 提供两种用于用户认证的协议：Extensible Authentication Protocol（EAP）和 Challenge Handshake Authentication Protocol（CHAP）。EAP 专为 PPTP 设计，并非专有协议。CHAP 是一种三步握手过程：客户端向服务器发送代码，服务器对其进行认证，随后服务器向客户端发送响应。CHAP 还会在连接建立后，定期对远程客户端进行重新认证。

-   PPTP 使用 Microsoft Point-to-Point Encryption（MPPE）对数据包进行加密。MPPE 实际上是一种 DES（数据加密标准）。虽然 DES 在许多场景下仍然有用，但新版本的 DES（如 DES 3）更受青睐。

#### Layer 2 Tunneling Protocol

-   *Layer 2 Tunneling Protocol*（*L2TP*）是专门为增强 PPTP 而设计的。与 PPTP 相比，它同样在 OSI 模型的数据链路层工作。L2TP 在以下方面提供了多项改进：

    *   认证方式更多且更丰富：PPTP 仅提供两种认证方法（CHAP 和 EAP），而 L2TP 提供五种（CHAP、EAP、PAP、SPAP 和 MS-CHAP）。

    *   协议适用范围更广：PPTP 仅能在标准 IP 网络上运行，而 L2TP 还能在 X.25 网络（电话系统中常用的协议）和 ATM（异步传输模式，高速传输技术）系统上工作。L2TP 利用 IPsec 进行加密。

#### IPsec

