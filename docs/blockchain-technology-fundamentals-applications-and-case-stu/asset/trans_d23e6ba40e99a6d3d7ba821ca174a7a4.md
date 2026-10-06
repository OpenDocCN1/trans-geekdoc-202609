
## PKI 的元素包括：

- 1. 证书机构（CA）：CA 向双方颁发数字证书，并通过与其环境的交换对双方进行身份验证。
- 2. CA 的证书吊销列表（CRL）：被吊销的证书列在 CRL [8] 中。它为不再使用的被吊销证书创建一个引用。证书的取消有很多原因。例如，证书因为加密密钥泄露而可能被吊销。

区块链（BC）网络也依赖 PKI 标准来保证各种网络之间安全的对点通信，它确认了发布在 BC 上的通信消息经过了身份验证。

PKI 有四个关键元素：

- 数字证书
- 公钥和私钥
- 证书机构
- 证书吊销列表

## 6.8 数字证书

与证书所有者或用户相关的属性集称为数字证书。数字证书是符合 X.509 标准的常见证书类型。最常见的证书类型是符合 X.509 标准的，其中节点细节编码是结构化并维护的。

X.509 证书示例，X.509 证书中有许多属性（图 6.6）。

描述用户的数字证书位于主体（subject）中。证书包含许多信息，例如其公钥在证书内发布，所有人可见，而私钥必须保持私密。

```
Certificate:
Data:
Version: 3 (0x2)
Serial Number: 2 (0x2)
Signature Algorithm: sha1WithRSAEncryption
Issuer: O=www.freelen.org, OU=freedom
Validity
Not Before: Apr 27 10:54:40 2012 GMT
Not After: Apr 25 10:54:40 2022 GMT
Subject: OU=Freedom, CN=couchbase-bob/emailAddress-bob@freelen.org
Subject: Public Key Info:
Public Key Algorithm: rsaEncryption
Public-Key: (4096 bit)
Modulus:
--
```

图 6.6 X.509 证书

## 区块链安全性提升基础

在 BC 中，用户属性可以在干扰时使用加密技术记录，任何干扰或更改将导致证书失效。用户需要使用加密技术证明其身份，这允许用户向 BC 中的其他人展示其证书；证书机构（CA）颁发证书并保留加密信息，任何读取证书的人都可以确信用户信息未被篡改。X.509 证书是一种难以篡改的数字身份。

## 6.9 公钥/私钥加密算法

发送者和接收者需要机密性和身份验证以确保交换的信息经过验证。消息消息身份验证确保了“完整性”，意味着消息传输不能被修改。数字签名是传统的身份验证机制，使用数字签名并允许源和目的地进行数字签名。这种签名机制保证了被签名消息的完整性。该机制要求将公钥公开作为身份验证锚点，并使用私钥在通信上生成数字签名。

接收方可以通过检查签名对发送者是否有效来验证所接收消息的来源和可靠性。

通过私钥和相应的公钥可以实现安全通信。由于密钥之间的数学连接，私钥用于在相应的公钥上生成签名，两者匹配时，如果验证签名未被篡改，则源是有效来源（图 6.7）。

## 6.10 证书机构

加入 BC 网络需要数字身份。受信任的机构颁发数字身份，数字身份是由 CA 颁发的验证形式。更流行的 CA 有 GeoTrust、Symantec（原 Verisign）、DigiCert、GoDaddy 和 Comodo。这些是互联网安全协议的共同部分（图 6.8）。

![](img/5197498995d15589ead293656bce20db_115_0.png)

图 6.7 签名验证模型。

![](img/5197498995d15589ead293656bce20db_116_0.png)

## 图 6.8 证书机构

CA 向网络中的不同参与者分发证书。所有证书都由 CA 进行数字签名，并与参与者的公钥绑定。CA 也有证书，CA 的身份可以通过检查证书是否由相应私钥的持有者生成来验证。在 BC 中，每个加入网络的节点都需要一个身份。一个或多个 CA 可以从数字角度定义网络中的参与者，每个参与者都需要验证自己的数字身份 [16]。

## 6.10.0 信任链

CA 有两种类型：

- 1. 根 CA：它们向用户颁发数百万证书。
- 2. 中间 CA：其证书由根 CA 或另一个中间机构颁发。

上述场景形成了“信任链”的创建，被视为追溯到提供安全性的根 CA 的最佳方式，使用中间 CA 交付给用户的证书提供了保证——如果根节点被攻破，整个信任链都会处于危险（图 6.9）。

## 6.10.1 FABRIC CA

Fabric 提供了一个内置的 CA 组件，它是一个私有根 CA，为拥有 X.509 证书的 Fabric 参与者提供数字身份 [17]。Fabric CA 管理根或中间 CA 以提供身份。

## 区块链安全性提升

![](img/5197498995d15589ead293656bce20db_117_0.png)

图 6.9 信任链

## 11 证书吊销列表

CRL 是由于任何原因被吊销的证书列表。当一个参与者想要验证时，会由 CA 进行检查。如果节点被攻破，证书就会被吊销。在 BC 中，会根据 CRL 进行检查。

## 6.11.1 BC 中的加密学

BC 中的信任是通过加密算法建立的。物联网区块链：系统性文献综述。

## 6.11.2 BC 中加密的类型

BC 的数据通过加密和函数进行验证。

## 6.11.3 加密算法类型

- 公钥加密：用户身份验证和 BC 数据通过公钥完成。公钥与他人共享，私钥则保持保密。
- 哈希函数：加密哈希生成一个固定的 32 字符字符串。对原始数据的简单更改都会创建一个新的哈希值。BC 中的每个区块都有哈希，该代码是由前一个区块的组合生成的。

## 区块链技术

![](img/5197498995d15589ead293656bce20db_118_0.png)

图 6.10 Merkle 树

哈希代码经过验证但无法更改。任何更改哈希链的尝试都会破坏 BC 信任链。

- Merkle 树：通过 Merkel 对 BC 数据进行高效验证。每个区块都有一个 Merkle 根，用于存储区块中的哈希，通过这个 Merkle 根，当前交易可以随哈希值发送。为了确认交易，节点本身可以计算哈希值而无需验证区块中的所有节点。

## 6.12 结论

BC 技术在许多领域得到了探索，包括公共生活和政府事务，公私部门目前允许实施 BC 技术。对于私有部门，BC 的效率高且成本低。在去中心化平台如 BC 技术中决定了许多问题。在公共 BC 中，技术可以使用公平的方法维护存储记录的完整性和机密性，但其分布式特性允许不同的参与者“所有”。

## 参考文献

- 1. K. Christidis and M. Devetsiot, “Blockchains and smart contracts for the Internet of Things.” IEEE Access, vol. 4, pp. 2292–2303, 2016.
- 2. M. Conscenti, A. Vetro, and J. C. De Martin, “Blockchain for the Internet of Things: A systematic literature review,” in Computer Systems and Applications (AICSA), 2016 IEEE/ACS 13th International Conference of. 2016, pp. 1–6.
- 3. J. C. Song, M. A. Demir, J. J. Prevost, and P. Rad, “Blockchain designed for decentralized IoT networks,” in 2018 13th Annual Conference on System of Systems Engineering (SoSE). IEEE, 2018, pp. 169–174.
