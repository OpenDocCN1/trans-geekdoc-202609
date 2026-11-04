
另一个例子是欧洲委员会制定的《通用数据保护条例》（GDPR）。GDPR 的主要目标之一是加强和统一欧盟（EU）内部个人的数据保护，同时解决个人数据向欧盟以外出口的问题。简而言之，GDPR 的主要目标是让公民重新掌控其个人数据。

## 什么是“密钥”？

一个 `key` 是由密码算法使用的秘密代码。它提供了产生功能输出的指令。密码算法本身通常是已知的。正是密钥的保密性提供了安全性。可以用在算法中的可能密钥数量被称为 `keyspace`，它是一组算法在需要生成密钥时从中选择的随机值集合。keyspace 越大，不同密钥的可能性就越多。例如，如果算法使用的是 10 位的字符串作为密钥，那么其密钥空间就是所有长度为 10 的二进制字符串的集合，这导致密钥空间大小为 `2^(10)`（或 1,024）；40 位密钥产生 `2^(40)` 种可能值；而 256 位密钥则产生 `2^(256)` 种可能值。密钥越长越难以破解，但需要更多的计算和处理能力。在决定密钥长度时必须考虑两个因素：期望的保护级别和可用的资源量。

### 对称密钥

`symmetric key` 算法使用单个秘密密钥，该密钥必须提前共享并由发送方和接收方保密。对称密钥通常被称为 `shared keys`。由于密钥是共享的，对称算法无法用于提供不可否认性或真实性。近年来最受欢迎的对称算法之一是 `AES`。对称密钥的优势在于计算效率高。弱点在于密钥管理本质上不安全且不可扩展，因为必须使用唯一的密钥集来保护密钥的保密性。

### 非对称密钥

`Asymmetric key` 密码学，也称为 `public key` 密码学，使用两把不同但数学相关的密钥，称为 `public` 和 `private` 密钥。可以把公钥和私钥想象成同一把锁的两把钥匙——一把用于上锁，另一把用于解锁。私钥永远不会离开所有者的掌控。公钥可以自由分发。公钥用于加密明文或验证数字签名，而私钥用于解密密文或创建数字签名。非对称密钥技术允许高效、可扩展且安全的密钥分发；然而，它们在计算资源方面要求很高。

## 什么是 PKI？

`Public key infrastructure (PKI)` 是用于创建、分发、管理、和撤销公钥的框架和服务。PKI 由多个组件组成，包括认证机构（CA）、注册机构（RA）、客户端节点以及数字证书本身：
* The `certification authority (CA)` 签发并维护数字证书。
* The `registration authority (RA)` 执行管理职能，包括验证请求数字证书的用户和组织的身份、续期证书以及撤销证书。
* `Client nodes` 是用户、设备和应用程序访问 PKI 功能的接口，包括请求证书和其他密钥材料。它们可能包括提供用户访问 PKI 所需的密码模块、软件和程序。
* A `digital certificate` 用于将公钥与身份关联。证书包括证书持有者的公钥、证书序列号、证书持有者的区别名称、证书有效期、证书颁发者的唯一名称、颁发者的数字签名以及签名算法标识符。

### 备忘：查看数字证书

如果您使用的是 Apple Mac 操作系统，证书存储在 Keychain Access 实用工具中。如果您使用的是 Microsoft Windows 操作系统，数字证书存储在 Internet Browser 应用程序中。[图 10-3](#ch10.xhtml#ch10fig03) 显示了 [twitter.com](http://twitter.com) 的数字证书，作为示例。

![](graphics/10fig03.jpg)

## 为什么要保护密码密钥？

如本章前面所述，密码系统的实用性完全取决于密钥的保密性和管理。这非常重要，以至于 NIST 发布了一份三部分的文件，专门提供密码密钥管理指导。SP 800-67: Recommendations for Key Management, Part 1: General (Revision 3) 提供了关于密码密钥材料管理的一般指导和最佳实践。Part 2: Best Practices for Key Management Organization 为美国政府机构的政策和安全规划要求提供指导。Part 3: Application Specific Key Management Guidance 在当前系统使用密码功能时提供指导。在第 1 部分概述中，NIST 如下描述密钥管理的重要性：“The proper management of cryptographic keys is essential to the effective use of cryptography for security. Keys are analogous to the combination of a safe. If a safe combination is known to an adversary, the strongest safe provides no security against penetration. Similarly, poor key management may easily compromise strong algorithms. Ultimately, the security of information protected by cryptography directly depends on the strength of the keys, the effectiveness of mechanisms and protocols associated with keys, and the protection afforded to the keys. All keys need to be protected against modification, and secret and private keys need to be protected against unauthorized disclosure. Key management provides the foundation for the secure generation, storage, distribution, use, and destruction of keys.”

密钥管理的最佳实践包括以下内容：
* The key length should be long enough to provide the necessary level of protection.
* Keys should be transmitted and stored by secure means.
* Key values should be random, and the full spectrum of the keyspace should be used.
* The key’s lifetime should correspond with the sensitivity of the data it is protecting.
* Keys should be backed up in case of emergency. However, multiple copies of keys increase the chance of disclosure and compromise.
* Keys should be properly destroyed when their lifetime ends.
* Keys should never be presented in clear text.

密钥管理政策和标准应包括密钥管理的指定责任、待保护信息的性质、威胁类别、应使用的密码保护机制，以及密钥和相关流程的保护要求。

## 数字证书泄露

认证机构（CAs）日益成为复杂网络攻击的目标。攻击者入侵 CA 以生成并获取欺诈性证书后，就可以使用这些欺诈性证书冒充个人或组织。2012 年 7 月，NIST 发布了一份题为“Preparing for and Responding to Certification Compromise and Fraudulent Certificate Issue.” 的 ITL 公告。该公告主要侧重于为认证和注册机构提供指导。该公告确实包括对受欺诈影响的任何组织的指导。

针对欺诈性签发的证书的内置防御措施是证书撤销。当发现 rogue 或欺诈性证书时，CA 将签发并分发证书撤销列表。或者，浏览器可以配置为使用在线证书状态协议（OCSP）来获取撤销状态。
