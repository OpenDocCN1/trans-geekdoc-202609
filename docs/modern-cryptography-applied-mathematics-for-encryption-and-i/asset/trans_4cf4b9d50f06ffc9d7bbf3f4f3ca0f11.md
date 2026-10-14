
Protected Extensible Authentication Protocol 使用已验证的 TLS 隧道加密身份验证过程。PEAP 由包括 Cisco、Microsoft 和 RSA Security 在内的联盟共同开发。它最早在 Microsoft Windows XP 中被加入。

###### EAP-POTP

Protected One-Time Password 是 RFC 4793 中描述的 EAP 的一种变体。它使用一次性密码令牌生成认证密钥，可用于单向或双向认证（客户端向服务器验证，服务器也向客户端验证）。

一次性密码（OTP）仅使用一次，随后即失效。它常与设备一起使用，例如生成 OTP 的钥匙扣。钥匙扣与服务器使用相同的算法，并结合当前时间戳在两端生成相同的 OTP。通常这与传统密码一起使用。

##### Kerberos

Kerberos 是一种网络认证协议，旨在通过使用对称加密为客户端/服务器应用提供强认证。它最初在 MIT 在“Project Athena”项目下开发。协议名为希腊神话中的 Kerberos（或 Cerberus），哈迪斯的可怕三头守护犬。

Kerberos 被广泛使用，并已在从 Windows 2000 到当前（截至本文撰写时为 Server 2012）以及 Red Hat Enterprise Linux、FreeBSD、IBM AIX 等操作系统的版本中得到实现。

你应该熟悉若干 Kerberos 相关术语：

![image](Images/image00484.jpeg) **Principal**  Kerberos 可为其分配票据的服务器或客户端

![image](Images/image00484.jpeg) **Authentication server (AS)**  为主体授权并将其连接到票据颁发服务器的服务器

![image](Images/image00484.jpeg) **Ticket-granting server (TGS)**  为提供票据的服务器

![image](Images/image00484.jpeg) **Key distribution center (KDC)**  为提供初始票据并处理 TGS 请求的服务器；通常同时运行 AS 和 TGS 服务

![image](Images/image00484.jpeg) **Ticket-granting ticket (TGT)**  在认证过程中颁发的票据

![image](Images/image00484.jpeg) **Ticket** 用于向服务器进行身份验证；包含客户端身份、会话密钥、时间戳和校验和，并使用服务器的密钥加密

![image](Images/image00484.jpeg) **Session key**  临时加密密钥

该过程本身被有意设计得复杂，以防止会话劫持攻击并确保更稳健可靠的认证机制。根据实现不同，过程会有变体，但大致如下：

**1.** 客户端向认证服务器（也称为服务器或服务）发送用户名和密码。用户名和密码用于生成服务器用于该会话向客户端发送消息的会话密钥。认证服务器/服务（AS）通常与票据颁发服务（TGS）共置在关键分发中心（KDC）服务器上。通常 KDC 包含 AS 和 TGS。

**2.** AS 在验证完客户端后，指示 TGS 生成票据颁发票据（TGT）。这包括，例如，客户端 ID、客户端网络地址、客户端会话密钥和有效期。所有这些信息都使用只有 TGS 拥有的对称密钥加密——即客户端无法解密该票据。

**3.** 当客户端想要访问特定服务时，会向 KDC 发送包含 TGT 和请求服务 ID 的消息。同时还会发送一条包含客户端 ID 和时间戳的第二条消息，并使用会话密钥加密。

**4.** 如果一切检查通过，KDC 会向客户端发送会话票据，该票据可用于访问相关服务。

**5.** 以上信息用于向服务进行身份验证，客户端据此访问该服务。

基本过程（不考虑一些细节）如 [Figure 14-2](#part0025.xhtml#ch14fig02) 所示。

![Images](Images/image00722.jpeg)

* * *

**FIGURE 14-2** Kerberos 基本过程

Kerberos 中看到的复杂性是有意设计的。持续的加密票据交换和信息校验使得会话劫持变得非常困难。会话密钥与 TGT 的组合意味着攻击者需要破解两个强加密密钥才能妥协系统。

##### NTLM

NTLM（NT LAN Manager）不常用于现代 VPN，但在 Microsoft 产品中用于提供认证及其他安全服务，你应该熟悉它。尽管 Microsoft 推荐将 Kerberos 作为首选认证协议，但许多实现仍使用 NTLM。

NTLM 是一个三步过程：

**1.** 客户端连接到服务器，然后发送 NEGOTIATE_MESSAGE 以宣传其能力。

**2.** 服务器响应 CHALLENGE_MESSAGE。这用于建立客户端的身份。

**3.** 过程以客户端向服务器响应挑战的 AUTHENTICATE_MESSAGE 结束。

NTLM 通过发送密码哈希来实现认证。NTLM 版本 1 使用基于 DES 的 LanMan 哈希。NTLM 版本 2 使用 MD4 加密哈希。

NTLM 易受 pass-the-hash 攻击，攻击者获取用户密码的哈希并将其发送给服务器。攻击者不需要知道实际密码，只需拥有该哈希。这可能发生在用户为本地密码使用相同密码时，攻击者可从 Windows 安全帐户管理器（SAM）文件中获取该哈希。也可能通过包 sniffing 获得。有时哈希会在机器上缓存，攻击者从缓存中获取。一旦攻击者拥有哈希，她就可以执行 pass-the-hash 攻击并以该用户身份登录，而无需知道用户的密码。

#### PPTP

Point-to-Point Tunneling Protocol 是一种较老的方法，其标准最早在 1999 年以 RFC 2637 发表。规范并未明确定义具体的加密或认证模式，而是由 PPTP 实现自行决定。该协议自 Windows 95 起在所有 Windows 版本中得到支持。最初，Microsoft 实现的 PPTP 使用 MS-CHAP 进行认证，使用 DES 进行加密。

PPTP 基于更早的 Point-to-Point Protocol（PPP），使用 TCP 端口 1723 来建立连接。连接建立后，PPTP 创建 Generic Routing Encapsulation（GRE）隧道。GRE 协议由 Cisco 开发。

##### PPTP vs. PPP

由于 PPTP 基于 PPP，简要描述 PPP 是必要的。PPP 设计用于通过串行点对点链路传输数据报。它通过在两台计算机之间建立的物理链路（串行电缆）发送数据包。PPP 用于建立和配置通信链路及网络层协议，同时还用于封装数据报。PPP 包含多个组件，实际上是由多个协议组成，每个协议负责过程的不同部分。PPP 最初是为在点对点链路中传输 IP 流量而开发的封装协议。PPP 还为一系列相关任务（如从一台计算机向另一台计算机传输数据）建立了标准。

