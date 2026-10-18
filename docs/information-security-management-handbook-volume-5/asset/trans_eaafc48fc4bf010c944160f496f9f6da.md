

![](OEBPS/images/box.jpg) 本文档不讨论特定的加密算法，但已在 RFC 2630 中讨论过。特定加密算法的讨论已移至单独的文档 \[CMSALG\]。协议与算法规范的分离使 IETF 能够独立更新每个文档。本规范不要求实现任何特定算法。相反，依赖于 CMS 的协议应针对其环境选择合适的算法。算法可从 \[CMSALG\] 或其他地方选择。

RFC 3370 Cryptographic Message Syntax (CMS) Algorithms, August 2002, R. Housley (RSA Labs)

![](OEBPS/images/box.jpg) 描述了将多种加密算法与加密消息语法 (CMS) 配合使用的约定。

![](OEBPS/images/box.jpg) 废弃 RFC 2630 \[OLDCMS\] 的第 12 节。RFC 3369 \[CMS\] 废弃了 RFC 2630 的其余部分。协议与算法规范的分离允许每个规范在不影响另一个的情况下进行更新。但是，将其他算法与 CMS 配合使用的约定可能会在单独的文档中指定。

RFC 3565 Use of the Advanced Encryption Standard (AES) Encryption Algorithm in Cryptographic Message Syntax (CMS), July 2003, J. Schaad (Soaring Hawk Consulting)

![](OEBPS/images/box.jpg) 指定了将高级加密标准 (AES) 内容加密算法与加密消息语法 \[CMS\] 的封装数据和加密数据内容类型配合使用的约定。

RFC 3852 Cryptographic Message Syntax (CMS), July 2004, R. Housley (Vigil Security)

![](OEBPS/images/box.jpg) CMS 源自 PKCS #7 版本 1.5，该版本在 RFC 2315 \[PKCS#7\] 中有记载。PKCS #7 版本 1.5 在 IETF 之外开发；它最初于 1993 年 11 月作为 RSA 实验室技术说明发布。从那时起，IETF 承担了 CMS 开发和维护的责任。今天，几个重要的 IETF 标准跟踪协议使用 CMS。

![](OEBPS/images/box.jpg) RFC 2630 \[CMS1\] 是 IETF 标准跟踪上的第一个 CMS 版本。在可能的情况下，保留与 PKCS #7 版本 1.5 的向后兼容性；但是，进行了更改以适应版本 1 属性证书传输并支持与算法无关的密钥管理。PKCS #7 版本 1.5 仅支持密钥传输。RFC 2630 添加了对密钥协商和先前分布的对称密钥加密密钥技术的支持。

![](OEBPS/images/box.jpg) RFC 3369 \[CMS2\] 废弃 RFC 2630 \[CMS1\] 和 RFC 3211 \[PWRI\]。基于密码的密钥管理包含在 CMS 规范中，并指定了扩展机制以支持新的密钥管理方案而无需进一步更改 CMS。保留与 RFC 2630 和 RFC 3211 的向后兼容性；但是，添加了版本 2 属性证书传输，并且版本 1 属性证书的使用已弃用。

![](OEBPS/images/box.jpg) S/MIME v2 签名 \[OLDMSG\]，基于 PKCS#7 版本 1.5，与 S/MIME v3 签名 \[MSG\] 兼容，后者基于 RFC 2630。但是，基于 PKCS #7 版本 1.5 的签名存在一些微妙的兼容性问题。这些问题在第 5.2.1 节中讨论。这些问题仍然存在于当前版本的 CMS 中。

![](OEBPS/images/box.jpg) 本文档不讨论特定的加密算法，但已在 RFC 2630 中讨论过。特定加密算法的讨论已移至单独的文档 \[CMSALG\]。协议与算法规范的分离使 IETF 能够独立更新每个文档。本规范不要求实现任何特定算法。相反，依赖于 CMS 的协议应针对其环境选择合适的算法。算法可从 \[CMSALG\] 或其他地方选择。

RFC 4853 Cryptographic Message Syntax (CMS) Multiple Signer Clarification, April 2007, R. Housley (Vigil Security)

![](OEBPS/images/box.jpg) 更新了加密消息语法 (CMS)，该语法在 RFC 3852 中发布。本文档澄清了当存在多个数字签名时 SignedData 受保护内容类型的正确处理方式。

# X9 历史

X9.73 Cryptographic Message Syntax (CMS) 最初于 2002 年作为面向金融服务行业的 CMS 配置文件发布，添加了 `NamedKeyEncryptedData` 内容类型。它基于 RFC 2630，并附有更新的 ANS.1 定义。

X9.73 Cryptographic Message Syntax (CMS) 于 2003 年更新。它与 RFC 3369 保持一致，并附有更新的 ANS.1 定义，但未包含 XML。

X9.96 XML Cryptographic Message Syntax (XCMS) 于 2004 年作为 X9.73 CMS 的可扩展标记语言 (XML) 版本发布。

X9.73 Cryptographic Message Syntax – ANS.1 and XML 于 2010 年发布。它结合了 X9.73 中的抽象语法标记法一 (ASN.1) 和 X9.96 中的可扩展标记语言 (XML)，与 RFC 3852 保持一致，并包含了被放弃的 ISO 28895 工作中的更改。

# 关于作者

`Jeff Stapleton` 是美国银行全球信息安全部门的副总裁。他在安全、金融和医疗保健行业拥有超过 25 年的经验，专长于软件开发、支付系统、PCI、加密、PKI、密钥管理、生物识别和可信时间戳。Jeff 拥有密苏里大学的学位，曾在其他大学任教，是一位出版作者、评论家，也是各种安全会议的常客演讲者。他参与制定了数十项 ANSI 和 ISO 安全标准，并自 1998 年以来一直担任 X9F4 加密协议和应用安全工作组主席。

![](OEBPS/images/dom6.jpg)

# 第 24 章

![](OEBPS/images/chline.jpg)

# 虚拟化安全简介

![](OEBPS/images/chline.jpg)

# Paul Henry

# 虚拟化技术快速概述

用最简单的话来说，当今最流行的虚拟化用途（服务器虚拟化）的概念是提供透明共享硬件资源的能力，这些资源可跨多个操作系统以及运行在相应操作系统上的相应应用程序共享。虚拟化提供了一层通常称为“虚拟机监控程序”的软件，该软件位于计算机硬件和操作系统之间，有效地封装了该硬件。虚拟机监控程序对硬件的这种封装允许运行在虚拟机监控程序之上的可能多个操作系统中的每一个都相信它拥有对底层硬件的独占访问权限。虚拟机监控程序的主要功能之一是允许多个操作系统在没有冲突或争用问题的情况下访问底层硬件。

# 当今使用的四种主要虚拟化类型

1. 服务器虚拟化

a. 整个服务器操作平台（例如 Windows Server 2003 或 Linux 衍生版）作为运行在虚拟机监控程序之上的虚拟镜像运行，透明地与其他虚拟化服务器操作平台共享底层计算资源。当前一代服务器虚拟化平台的优点之一是，当今几乎任何商业可用的操作系统都可以在不进行修改的情况下在服务器虚拟化环境中运行。

2. 应用程序虚拟化

