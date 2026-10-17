
你也看到 SSL/TLS 加密通信在诸多技术中具有重要意义，包括 VoIP、电子邮件和网页流量。你已经了解了如何使用 Apache 和 IIS 为网页流量设置 SSL/TLS。

### Test Your Knowledge

**1.** 在一般 términos 中，描述数字签名的工作原理。

**2.** 简要描述盲签名的概念。

**3.** X.509 支持什么 PGP 证书不支持？

**4.** X.509 证书由谁数字签名？

**5.** SSL/TLS 握手过程中，包含客户端可支持的加密套件的部分是哪一部分？

**6.** 如果用于 SSL/TLS 的证书在 CRL 上，会发送什么消息？

**7.** 安全 IMAP 默认使用哪个端口？

**8.** 什么是受信任签名？

**9.** 语音邮件安全吗？

**10.** PGP 最常用于何处？

#### Answers

**1.** 私钥用于加密消息（通常是消息的哈希值），接收方使用公钥进行验证。

**2.** 当 A 需要向 B 发送消息时，受信任的第三方 C 必须签名以确认数据确实由 A 发送，但 A 不希望 C 查看消息内容。

**3.** 第三方认证

**4.** 证书颁发者

**5.** `Client Hello`

**6.** `certificate_revoked`

**7.** `993`

**8.** 签名来自受信任的第三方，而非消息发送者。

**9.** 不，SIP 和 RTP 本身不具备安全性，需要使用 sRTP 等协议来提供安全。

**10.** 电子邮件加密

### Endnotes

**1.** IETF, RFC 5280, “Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile,” May 2008, [www.rfc-editor.org/info/rfc5280](http://www.rfc-editor.org/info/rfc5280).

**2.** Microsoft Developer Network, “Public Key Infrastructure,” [`msdn.microsoft.com/en-us/library/windows/desktop/bb427432(v=vs.85).aspx`](https://msdn.microsoft.com/en-us/library/windows/desktop/bb427432\(v=vs.85\).aspx).

**3.** Microsoft TechNet, “What Is TLS/SSL?” [`technet.microsoft.com/en-us/library/cc784450(v=ws.10).aspx`](https://technet.microsoft.com/en-us/library/cc784450\(v=ws.10).aspx).

**4.** IETF RFC 5246, “The Transport Layer Security (TLS) Protocol Version 1.2,” [`tools.ietf.org/html/rfc5246`](https://tools.ietf.org/html/rfc5246).

**5.** IBM Knowledge Center, “An Overview of the SSL or TLS Handshake,” [www-01.ibm.com/support/knowledgecenter/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10660\_.htm?lang=en](http://www-01.ibm.com/support/knowledgecenter/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10660_.htm?lang=en).

**6.** Microsoft TechNet, “SSL/TLS in Detail,” [`technet.microsoft.com/en-us/library/cc785811(v=ws.10).aspx`](https://technet.microsoft.com/en-us/library/cc785811\(v=ws.10).aspx).

**7.** Netcraft, “April 2014 Web Server Survey,” [`news.netcraft.com/archives/2014/04/02/april-2014-web-server-survey.html`](http://news.netcraft.com/archives/2014/04/02/april-2014-web-server-survey.html).

**8.** BuiltWith, “OpenSSL Usage Statistics: Websites Using OpenSSL,” [`trends.builtwith.com/Server/OpenSSL`](http://trends.builtwith.com/Server/OpenSSL).

**9.** Apache HTTP Server Version 2.0, “SSL/TLS Strong Encryption: How To,” [`httpd.apache.org/docs/2.0/ssl/ssl_howto.html`](http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html).

虚拟专用网络（VPN）是另一种非常常见的密码学应用。VPN 设计用于在两个站点之间或在远程工作者与站点之间提供安全连接。它们提供的连接方式与您在物理上连接到网络时拥有的相同，因此得名：它是虚拟的专用网络连接。本章我们将探讨一些通用概念以及与 VPN 相关的具体技术。我们还将查看一些虽不是严格意义上的 VPN，但属于安全远程连接的相关技术。

《计算机和互联网术语词典》将 VPN 定义为“一种通过 Internet 使用安全特性防止未经授权访问的网络”。^(1) 这只是一个相当典型的定义，类似于任何计算机词典中会有的，但不够详细。

VPN 的思想是模拟实际的物理网络连接，这意味着 VPN 必须提供与实际物理网络相同的访问权限和安全性。为了模拟专用点对点（PTP）链路，数据会被封装或包装一个提供路由信息的报头，以便它可以通过 Internet 传输并到达目的地。这创建了两点之间的虚拟网络连接。随后，数据被加密，从而使该虚拟网络变得私有。

那么，如何实现创建 VPN 所需的认证和加密呢？有多种技术可以帮助建立 VPN，它们的工作方式略有不同。本章将逐一介绍这些技术。尽管协议在细节上有所差异，但最终目标相同。首先，认证用户以确保该用户确实是其声称的身份。然后交换加密信息，例如使用哪些算法。最后，建立两方可以用来保护数据的对称密钥。

### 认证

认证是验证某个实体（无论是用户、系统还是程序）确实是其声称的身份的过程。最直观的认证例子是终端用户输入用户名和密码。密码理论上验证用户的身份。然而，随着安全 breaches 变得更加普遍，单凭用户名和密码已不足以提供足够的安全性。因此，出现了其他类型的认证方式：

`![image](img/image00484.jpeg)  Type I, something you know  Passwords, PINs, and passphrases are classic examples of Type I authentication. They all have the same weakness, however: they can be easily guessed or stolen.`

`![image](img/image00484.jpeg)  Type II, something you have  These are physical items, such as a debit card used with ATMs, smart cards, and smart keys. This type of authentication cannot be guessed, but it can certainly be stolen.`

`![image](img/image00484.jpeg)  Type III, something you are  Biometrics, including fingerprints, retinal scans, facial recognition, even handwriting, all constitute Type III authentication. This is the most secure type of authentication, because it cannot be guessed and cannot be stolen (at least not easily!).`

**Note**

这三种是主要的认证手段，但还有其他方法。例如，出站（out-of-band，OOB）认证要求用户从多个数据源提供信息，这些信息通常只为真实用户所知。当您在线查询信用报告时，许多系统会要求您提供如社会安全号码（Type I 认证）以及诸如每月信用卡付款额和当前余额等信息。后两项信息属于 OOB 信息。

Type I 认证可用于 VPN 并且常被使用。Type II 也可以使用。最佳方案，通常称为“强认证”，是结合 Type I 与 Type II 认证。例如，使用 ATM 时必须持有借记卡（Type II）并输入 PIN（Type I）。一些 VPN 解决方案同样要求密码以及数字证书（参见 第 13 章 以获取关于数字证书的详细讨论），或在客户端机器上使用智能卡。在大多数情况下，Type III 认证不适用于 VPN（仅在政府控制的机密系统中例外）。其成本、开销和复杂度使得生物特征认证对 VPN 不具吸引力。

除了考虑使用哪种认证方式外，还必须关注认证数据以及加密信息的传输方式。这由 VPN 协议负责处理。每个协议都有自己的认证方法以及加密数据交换方式。

由于所有 VPN 协议都包含认证和加密，您需要对认证协议有良好的理解。本书在讨论了多种加密和散列算法后，发现相较于这些算法，认证过程相对简单。认证的目的仅是验证给定实体是否为其声称的身份。现代认证协议还能防止会话劫持等高级攻击。

**Note**

会话劫持发生在攻击者在用户认证到系统后等待，然后接管该会话。各种方法可以实现此攻击，且都至少属于中等复杂度。会话劫持的关键在于攻击者不必获得用户的密码；攻击者在用户提供密码后接管会话。

### CHAP

Challenge Handshake Authentication Protocol（挑战握手认证协议）专门用于防止会话劫持。其过程相对简单：

**1.** 客户端发送用户名和密码到服务器（在 CHAP 文档中常称为“验证器”。）

**2.** 服务器/验证器随后请求客户端计算一个加密散列并将其发送到服务器。

**3.** 在随机间隔的时间里，服务器/验证器会请求客户端重新呈现该加密散列。其目的是检测会话劫持并，如有必要，终止该连接。

该过程在 Figure 14-1 中示意。

![Images](img/image00721.jpeg)

* * *

**FIGURE 14-1  The CHAP process**

**Note**

Microsoft 创建了自己的 CHAP 变体，称为 MS‑CHAP。虽然 MS‑CHAP 符合一般描述，但其变体对我们讨论 VPN 没有直接关系。例如，MS‑CHAP v2 支持双向认证，即双方相互验证身份。

### EAP

Extensible Authentication Protocol（可扩展认证协议）顾名思义是一个可以被修改或扩展的框架，用于多种目的。EAP 标准最初在 RFC 2284 中指定，随后被 RFC 3748 取代，并最终由 RFC 5247 更新。EAP 的各种变体在认证材料的交换方式上有所不同。这里我们只看几个常见的变体。

#### LEAP

Lightweight Extensible Authentication Protocol（轻量可扩展认证协议）由 Cisco 开发，广泛用于无线通信。LEAP 受到许多 Microsoft 操作系统（包括 Windows 7）的支持，并使用了 MS‑CHAP 的修改版。

#### EAP‑TLS

Extensible Authentication Protocol‑Transport Layer Security（可扩展认证协议‑传输层安全）使用 TLS（参见 第 13 章）来保护认证过程。大多数 EAP‑TLS 实现使用 X.509 数字证书（同样在 第 13 章 中讨论）进行用户认证。

#### PEAP

Protected Extensible Authentication Protocol 使用已验证的 TLS 隧道加密身份验证过程。PEAP 由包括 Cisco、Microsoft 和 RSA Security 在内的联盟共同开发。它最早在 Microsoft Windows XP 中被加入。

#### EAP-POTP

Protected One-Time Password 是 RFC 4793 中描述的 EAP 的一种变体。它使用一次性密码令牌生成认证密钥，可用于单向或双向认证（客户端向服务器验证，服务器也向客户端验证）。

一次性密码（OTP）仅使用一次，随后即失效。它常与设备一起使用，例如生成 OTP 的钥匙扣。钥匙扣与服务器使用相同的算法，并结合当前时间戳在两端生成相同的 OTP。通常这与传统密码一起使用。

### Kerberos

Kerberos 是一种网络认证协议，旨在通过使用对称加密为客户端/服务器应用提供强认证。它最初在 MIT 在“Project Athena”项目下开发。协议名为希腊神话中的 Kerberos（或 Cerberus），哈迪斯的可怕三头守护犬。

Kerberos 被广泛使用，并已在从 Windows 2000 到当前（截至本文撰写时为 Server 2012）以及 Red Hat Enterprise Linux、FreeBSD、IBM AIX 等操作系统的版本中得到实现。

你应该熟悉若干 Kerberos 相关术语：

![image](img/image00484.jpeg) **Principal**  Kerberos 可为其分配票据的服务器或客户端

![image](img/image00484.jpeg) **Authentication server (AS)**  为主体授权并将其连接到票据颁发服务器的服务器

![image](img/image00484.jpeg) **Ticket-granting server (TGS)**  为提供票据的服务器

![image](img/image00484.jpeg) **Key distribution center (KDC)**  为提供初始票据并处理 TGS 请求的服务器；通常同时运行 AS 和 TGS 服务

![image](img/image00484.jpeg) **Ticket-granting ticket (TGT)**  在认证过程中颁发的票据

![image](img/image00484.jpeg) **Ticket** 用于向服务器进行身份验证；包含客户端身份、会话密钥、时间戳和校验和，并使用服务器的密钥加密

![image](img/image00484.jpeg) **Session key**  临时加密密钥

该过程本身被有意设计得复杂，以防止会话劫持攻击并确保更稳健可靠的认证机制。根据实现不同，过程会有变体，但大致如下：

**1.** 客户端向认证服务器（也称为服务器或服务）发送用户名和密码。用户名和密码用于生成服务器用于该会话向客户端发送消息的会话密钥。认证服务器/服务（AS）通常与票据颁发服务（TGS）共置在关键分发中心（KDC）服务器上。通常 KDC 包含 AS 和 TGS。

**2.** AS 在验证完客户端后，指示 TGS 生成票据颁发票据（TGT）。这包括，例如，客户端 ID、客户端网络地址、客户端会话密钥和有效期。所有这些信息都使用只有 TGS 拥有的对称密钥加密——即客户端无法解密该票据。

**3.** 当客户端想要访问特定服务时，会向 KDC 发送包含 TGT 和请求服务 ID 的消息。同时还会发送一条包含客户端 ID 和时间戳的第二条消息，并使用会话密钥加密。

**4.** 如果一切检查通过，KDC 会向客户端发送会话票据，该票据可用于访问相关服务。

**5.** 以上信息用于向服务进行身份验证，客户端据此访问该服务。

基本过程（不考虑一些细节）如 Figure 14-2 所示。

![Images](img/image00722.jpeg)

* * *

**FIGURE 14-2** Kerberos 基本过程

Kerberos 中看到的复杂性是有意设计的。持续的加密票据交换和信息校验使得会话劫持变得非常困难。会话密钥与 TGT 的组合意味着攻击者需要破解两个强加密密钥才能妥协系统。

### NTLM

NTLM（NT LAN Manager）不常用于现代 VPN，但在 Microsoft 产品中用于提供认证及其他安全服务，你应该熟悉它。尽管 Microsoft 推荐将 Kerberos 作为首选认证协议，但许多实现仍使用 NTLM。

NTLM 是一个三步过程：

**1.** 客户端连接到服务器，然后发送 NEGOTIATE_MESSAGE 以宣传其能力。

**2.** 服务器响应 CHALLENGE_MESSAGE。这用于建立客户端的身份。

**3.** 过程以客户端向服务器响应挑战的 AUTHENTICATE_MESSAGE 结束。
