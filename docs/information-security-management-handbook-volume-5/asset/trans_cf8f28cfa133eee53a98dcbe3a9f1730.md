

[Figure 23.11](#9781466508507_epub_c23_r1.htm#fig_23.11) 和 [Figure 23.12](#9781466508507_epub_c23_r1.htm#fig_23.12) 的区别在于，Figure 23.11 的数字签名对加密数据进行验证，而 [Figure 23.12](#9781466508507_epub_c23_r1.htm#fig_23.12) 对原始内容进行验证。如果签名者和加密者不是同一实体，那么数字签名提供的保护代表了非常不同的保证级别。通过加密通信通道接收原始签名内容的信任模型，与通过加密通信通道接收原始内容（该通道恰好使用数字签名提供加密数据的完整性和真实性）的信任模型不同。[Figure 23.12](#9781466508507_epub_c23_r1.htm#fig_23.12) 提供内容原始性的保证，而 [Figure 23.11](#9781466508507_epub_c23_r1.htm#fig_23.11) 不一定能在没有额外补偿控制措施的情况下提供相同的保证。

# Advanced Use

假设存在这样一个场景：一个敏感数据对象需要跨多个域传输，且必须始终加密，但这些域不共享通用加密系统。此外，假设每个域都需要向对象遍历的每个其他域证明该数据对象的完整性和真实性。为了避免创建多层洋葱，可以使用 [Figure 23.13](#9781466508507_epub_c23_r1.htm#fig_23.13) 中描绘的对象。

原始域会生成内容的数字签名，将 `SignedData` 对象作为 `SignedDataList` 中的第一个实例，使用与下一个域的密钥协商方案加密数据，创建 `EnvelopedData` 对象，创建 [Figure 23.13](#9781466508507_epub_c23_r1.htm#fig_23.13) 中所示的分离对象，并将其发送到下一个域。

![](OEBPS/images/fig_23.13.jpg)

![](OEBPS/images/line-2.jpg)

**Figure 23.13 分离对象。**

每个中间域都会解密内容并验证每个先前域的数字签名，生成内容的数字签名，创建并将 `SignedData` 对象追加到 `SignedDataList`，使用与下一个域的密钥协商方案加密数据，创建并替换 `EnvelopedData` 对象，并将其发送到下一个域。在每个域，都会将另一个 `SignedData` 对象添加到列表中，但整个分离对象将由三个组件组成：`ContentInfo`、`SignedDataList` 和 `EnvelopedData`。

最终域会解密内容并验证每个先前域的数字签名，其中 `SignedDataList` 组件本质上是对象已遍历域的可验证审计记录。为了确保敏感数据的保护，每个域都会在加密硬件模块中执行所有加密功能，以便未加密的内容仅在原始域和最终域中被披露。

# CMS Change History

# PKCS #7 Cryptographic Message Syntax Standard

公钥加密标准 (PKCS) #7 是 RSA Laboratories 技术说明。支持的内容类型包括：data、`signedData`、`envelopedData`、`signedAndEnvelopedData`、`digestedData` 和 `encryptedData`。PKCS #7 有三个版本，列表如下：

PKCS #7 versions 1.0–1.3

版本 1.0–1.3 分发给了 1991 年 2 月和 3 月 RSA Data Security, Inc. 公钥加密标准会议的参与者。

PKCS #7 Version 1.4

版本 1.4 是 1991 年 6 月 3 日 PKCS 初始公开发布的一部分。版本 1.4 作为 NIST/OSI Implementers’ Workshop 文档 SEC-SIG-91-22 发布。

PKCS #7 Version 1.5

版本 1.5 于 1993 年 11 月发布，包含多项编辑更改，包括对参考文献的更新以及添加修订历史记录。做出了以下实质性更改：

*   Section 6: 添加了 `CertificateRevocationLists` 类型。

*   Section 9.1: 修订了 `SignedData` 语法。新版本允许与签名一起传播证书吊销列表。它还允许单独传播证书和证书吊销列表，而无需任何签名。

*   Section 9.2: 修订了 `SignerInfo` 语法。新版本包括与 RFC 1423 中指定的隐私增强邮件 (PEM) 兼容的消息摘要加密过程。

*   Section 9.3: 将“`authenticatedAttributes` 字段的 DER 编码”明确为“`Attributes` 值的 DER 编码”。

*   Section 10.3: 描述了内容加密算法的填充方法。

*   Section 11.1: 修订了 `SignedAndEnvelopedData` 语法。新版本允许传播证书吊销列表。

*   Section 13: 添加了 `Encrypted-data` 内容类型。该内容类型由任何类型的加密内容组成。

*   Section 14: 添加了 `encryptedData` 对象标识符。

# IETF History

互联网工程任务组 (IETF) 中的 CMS 历史包括以下技术规范。注释直接摘录自 IETF 文档。

RFC 2630 Cryptographic Message Syntax, June 1999, R. Housley (Spyrus)

![](OEBPS/images/box.jpg) 密码消息语法源自 RFC 2315 [PKCS#7] 中指定的 PKCS #7 版本 1.5。在可能的情况下，保持向后兼容性；但是，为了适应属性证书传输和用于密钥管理的密钥协商技术，需要进行更改。

![](OEBPS/images/box.jpg) 已被 [superseded] RFC3369, RFC3370 废弃

RFC 3211 Password-based Encryption for CMS, December 2001, P. Gutmann (University of Auckland)

![](OEBPS/images/box.jpg) 本文档提供了一种使用用户提供的密码加密数据的方法，并扩展到任何形式的可变长度密钥材料，该材料不一定是算法特定的固定格式密钥。密码消息语法数据格式目前不包含任何用于基于密码的数据加密的规定。

RFC 3278 Use of Elliptic Curve Cryptography (ECC) Algorithms in Cryptographic Message Syntax (CMS), April 2002, S. Blake-Wilson (Certicom), D. Brown (Certicom), P. Lambert (Cosine)

![](OEBPS/images/box.jpg) 本文档描述了如何在密码消息语法 (CMS) 中使用椭圆曲线加密 (ECC) 公钥算法。ECC 算法支持创建数字签名以及交换密钥以加密或验证内容。算法处理的定义基于 ANSI X9.62 标准（由 ANSI X9F1 工作组开发）、IEEE 1363 标准和 SEC 1 标准。

RFC 3369 Cryptographic Message Syntax (CMS), August 2002, R. Housley (RSA Labs)

![](OEBPS/images/box.jpg) 废弃 RFC 2630 [OLDCMS] 和 RFC 3211 [PWRI]。基于密码的密钥管理包含在 CMS 规范中，并指定了扩展机制以支持新的密钥管理方案，而无需进一步更改 CMS。保留与 RFC 2630 和 RFC 3211 的向后兼容性；但是，添加了版本 2 属性证书传输。版本 1 属性证书的使用已弃用。

![](OEBPS/images/box.jpg) 基于 PKCS#7 版本 1.5 的 S/MIME v2 签名 [OLDMSG]，与基于 RFC 2630 的 S/MIME v3 签名 [MSG] 兼容。但是，使用 PKCS#7 版本 1.5 和 CMS 的签名存在一些微妙的兼容性问题。

