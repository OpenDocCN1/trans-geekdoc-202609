
![image](Images/image00484.jpeg) `数字签名` `确认该证书确实是由它声称的证书颁发机构颁发的。`

![image](Images/image00484.jpeg) `签名算法标识符` `签名者的公钥和用于验证签名的算法。`

还有其他可选字段，但这些是必需字段。请注意，最后三项内容涉及验证。X.509 数字证书的一个优势是其验证持有者的机制。这是安全通信的关键，不仅用于加密传输，还用于验证相关方的身份。下面的流程概览在 [Figure 13-4](#part0024.xhtml#ch13fig04) 中给出。

![Images](Images/image00706.jpeg)

* * *

**FIGURE 13-4** `验证 X.509 证书` `Verifying X.509 certificates`

这就提出了一个重要问题：为什么要信任证书颁发机构来验证持有者的身份？证书由受众信任的许多第三方的受信任机构（CA）发布。主要的 CA 包括 `Symantec`、`GoDaddy`、`DigiCert`、`Global Sign` 和 `Comodo`，它们均被视为可信供应商。

**Note**

公司和其他组织有时会发布其自己的数字证书，但这些证书仅在组织内部网络内有效。由于公司的 CA 不被其他网络信任，由该 CA 发布的证书在其他网络中不可信。

数字证书有不同的级别，每个级别对持有者身份验证的深度不同。验证越充分，证书越贵：

![image](Images/image00484.jpeg) `Class 1` `适用于个人，用于电子邮件`

![image](Images/image00484.jpeg) `Class 2` `适用于组织，需要身份证明；大多数网站使用 Class 2 证书`

![image](Images/image00484.jpeg) `Class 3` `适用于服务器和软件签名，由颁发 CA 进行独立的身份和权限验证`

![image](Images/image00484.jpeg) `Class 4` `适用于公司之间的在线业务交易`

![image](Images/image00484.jpeg) `Class 5` `适用于私人组织或政府安全`

##### PGP

另一种证书类型是 Pretty Good Privacy（PGP）证书。PGP 方法结合了散列、非对称加密和对称加密，以实现安全通信。每个公钥都与用户名和/或电子邮件地址绑定，因此 PGP 常用于电子邮件加密。PGP 通过使用证书工作，但使用的是自签名数字证书。这意味着不存在 CA，也没有第三方对发送者身份的验证。因此 PGP 证书不用于网页/电子商务。PGP 证书包含以下信息：

![image](Images/image00484.jpeg) `PGP 版本号` `使用的 PGP 版本。`

![image](Images/image00484.jpeg) `证书持有者的公钥` `证书持有者的公钥。使用数字证书的目的之一是传播公钥。`

![image](Images/image00484.jpeg) `证书持有者的信息` `标识证书所属人，内容可能比 X.509 证书更详尽。`

![image](Images/image00484.jpeg) `证书所有者的数字签名` `由于不存在 CA，证书所有者对证书进行数字签名。`

![image](Images/image00484.jpeg) `证书的有效期` `证书的有效期限。`

![image](Images/image00484.jpeg) `用于密钥的首选对称加密算法` `在使用非对称加密后，证书持有者偏好使用的对称算法类型。`

PGP 由 `Phillip Zimmerman` 在 1991 年创建。第一个版本使用他自行开发的对称算法。随后版本采用多种知名对称算法。

**Note**

`Phillip Zimmerman` 在密码学领域声名显赫。他的 PGP 产品广泛用于电子邮件加密，并且他还参与了 VoIP 加密协议的开发。他拥有计算机科学学士学位。PGP 的最初发布引发了美国政府的出口管制调查，因为它允许加密强度超出美国政府允许的出口范围（详见 [Chapter 15](#part0026.xhtml#ch15) 更多关于出口法的说明）。该案于 1996 年被驳回。Zimmerman 因其工作获得了显著认可，包括被纳入 `Internet Hall of Fame`、被 `PC World` 评为 `Top 50 Tech Visionaries` 之一，以及获得 `Louis D. Brandeis Privacy Award`。

#### Public-Key Infrastructure X.509

公钥基础设施（PKI）是创建和分发数字证书所需的基础设施。由于数字证书是非对称算法公钥的传播方式，PKI 是任何非对称加密实现的重要组成部分。

PKI 的一个角色是通过 CA 将公钥与用户的身份绑定。换句话说，仅仅将公钥广泛公开是不够的；还需要一种机制来验证特定公钥是否对应特定用户。PKI 通过 CA 完成此验证。

PKI 包含多个部分。每个证书颁发者必须被其他颁发者信任，证书才能相互交换。考虑访问在线银行网站的过程：该网站拥有一张由某 CA 发行的数字证书，该 CA 必须是您和银行都信任的。随后，您可能访问电子商务网站，它可能使用完全不同的 CA，但也必须是您信任的。

CA 负责发行和管理证书。^([2](#part0024.xhtml#ch13note2a)) 这包括撤销证书，撤销可通过以下两种方式实现：

![image](Images/image00484.jpeg) `CRL (Certificate Revocation List)` `已撤销证书的列表。发布方式有两种：推送模型，CA 定期自动发送 CRL；拉取模型，用户主动从 CA 下载 CRL 以验证证书。两种模式均不提供即时、实时的更新。`

![image](Images/image00484.jpeg) `状态检查` `鉴于 CRL 不是实时的，已引入在线证书状态协议（OCSP）来验证证书是否有效。OCSP 定义于 RFC 6960，使用 HTTP 进行通信，并在 Internet Explorer 7、Mozilla Firefox 3 和 Safari 中得到支持。`

CA 通常由注册机构（RA）协助，RA 负责验证请求数字证书的个人或实体的身份。一旦身份得到验证，RA 会通知 CA 可以发行证书。

`Public-Key Infrastructure X.509 (PKIX)` 是 IETF 成立的工作组，负责开发公钥基础设施的标准和模型，并负责更新 X.509 标准。该工作组由全球的专家组成，每位成员均为标准贡献力量。

`Public-Key Cryptography Standards (PKCS)` 是 RSA 及其它公司（如 Microsoft 和 Apple）自愿制定的标准集。截至本文撰写，已有 15 项 PKCS 标准：

![image](Images/image00484.jpeg) `PKCS #1: RSA Cryptography Standard`

![image](Images/image00484.jpeg) `PKCS #2: Incorporated in PKCS #1`

![image](Images/image00484.jpeg) `PKCS #3: Diffie-Hellman Key Agreement Standard`

