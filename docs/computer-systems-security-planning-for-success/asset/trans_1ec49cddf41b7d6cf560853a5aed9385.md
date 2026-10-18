

[WhiteTimberwolf (SVG 版本)](https://commons.wikimedia.org/wiki/File:CBC_encryption.svg)，公共领域，通过 Wikimedia Commons 提供

从初始化向量（`IV`）开始，每个块都与前一个块的部分密文进行异或运算，以创建不断变化的密文链。这意味着相同的块会产生不同的密文。这是最常见的操作模式，其弱点在于算法无法并行运行（抱歉，现代处理器），并且 `IV` 是常见的攻击目标。

#### 计数器（CTR）

![WhiteTimberwolf (SVG 版本)，公共领域，通过 Wikimedia Commons 提供](images/ctr.svg)

[WhiteTimberwolf (SVG 版本)](https://commons.wikimedia.org/wiki/File:CTR_encryption_2.svg)，公共领域，通过 Wikimedia Commons 提供

CTR 不使用 `IV`，而是使用 nonce（所有块相同的随机数）和计数器。计数器随每个块递增，这意味着该模式可以并行运行。CTR 模式解决了 ECB 的问题，同时仍提供了一个可以在现代机器上快速运行的算法。

#### Galois/计数器模式（GCM）

![带初始化向量的 Galois 计数器模式块图，改编自 NIST 的图表，根据 CC0 1.0 协议使用](images/gcm.svg)

[带初始化向量的 Galois 计数器模式块图，改编自 NIST 的图表](https://commons.wikimedia.org/w/index.php?curid=74845777) 根据 [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/deed.en) 协议使用

GCM 使用类似 CTR 的计数器，但不使用 nonce。相反，`IV` 与初始计数器一起使用。GCM 还为每个块生成消息身份验证码（`MAC`）以验证块的完整性。这种组合使其成为一种现代、强健的算法，正在迅速获得采用。

## 2.10. 加密示例

### 2.10.1. RSA

RSA 是一种于 1977 年开发的非对称加密标准，至今仍非常流行。其陷门函数基于大数分解的困难性。RSA 名称来自该系统作者的姓名：Ron Rivest、Adi Shamir 和 Leonard Adleman。

### 2.10.2. 高级加密标准（AES）

AES 是一种于 1998 年开发的对称块密码，旨在取代安全性较低的数据加密标准（`DES`）。AES 对 128 位数据块进行操作，执行多轮替换-置换来加密数据。您会发现 AES 用于加密网络流量（如虚拟私有网络中的情况）、存储到磁盘的数据（磁盘加密）或保存到存储设备的计算机游戏数据。AES 是一种非常常见的密码。

### 2.10.3. 椭圆曲线密码学（ECC）

ECC 是一种非对称加密方案，速度快且易于计算。它正在迅速成为数字签名和密钥交换的首选方案，自 2004 年起开始普及。ECC 基于预定义曲线集的几何特性（一些示例可在 [此处](http://www.secg.org/sec2-v2.pdf) 找到），可用于创建陷门函数。

### 2.10.4. Diffie-Hellman 密钥交换

![原始图表：A.J. Han Vinck，杜伊斯堡-埃森大学 SVG 版本：Flugaal，公共领域，通过 Wikimedia Commons 提供](images/dh.svg)

[原始图表：A.J. Han Vinck，杜伊斯堡-埃森大学 SVG 版本：Flugaal](https://commons.wikimedia.org/wiki/File:Diffie-Hellman_Key_Exchange.svg)，公共领域，通过 Wikimedia Commons 提供

鉴于非对称算法的速度较慢，通常像 VPN 这样的应用程序会选择使用非对称加密来交换共享密钥，然后使用该密钥与更快的对称算法（如 AES）一起使用。Diffie-Hellman 正是这样做的，并于 1976 年首次发表。Diffie-Hellman 密钥交换使用与 RSA 相同的数学概念，即幂运算和模运算，效果显著，但为了可视化发生的情况，使用了秘密颜色混合的比喻（请参见包含的图表）。重要的是要记住，由于交换介质可能较慢，DH 密钥交换旨在产生最小流量。

### 2.10.5. 数字证书

数字证书是一组用于识别公司或个人的凭据。由于非对称加密需要知道一方的公钥，数字证书包含该密钥以及所有者的 ID。那么问题就变成了，如何信任公钥确实属于声称的所有者？这就是颁发机构的作用。证书颁发机构（`CA`）对证书进行签名，表明 ID 和 `public_key` 是正确的。证书可以自签名，但这绕过了对 `CA` 的信任，通常仅用于测试。由于大多数证书用于加密 Web 流量，Web 浏览器通常会在网站使用自签名证书时警告您。

鉴于需要颁发多少证书以及验证它们所需的工作量，大多数证书并非由根 `CA` 颁发，而是由中间 `CA` 颁发。根 `CA` 将工作委托给中间 `CA`，并通过签署中间 `CA` 的密钥来表示对它们的信任。这创建了一个信任链，从颁发的证书（由中间 `CA` 签名）到中间 `CA`（由根 `CA` 签名）再到根 `CA`（由浏览器信任）。使用此信任链的工具将保留根 `CA` 证书，并根据需要从颁发它们的公司进行更新。

证书存储非常重要，虽然用户很少与其交互，但通常可以手动安装根 `CA`。[这可以用于创建代理以解密 HTTPS 流量用于调试](https://docs.telerik.com/fiddler/configure-fiddler/tasks/trustfiddlerrootcert) 或用于更恶意的目的。出于此原因，一些应用程序（例如 Facebook 移动应用）维护自己的证书存储，并防止用户向其中添加根 `CA`。

![](images/letsencrypt.svg)

那么，如何为您的网站获取证书呢？客户将生成一个证书签名请求（`CSR`），其中包含公钥和其 ID。`CA` 将验证客户拥有该网站，并构建和签署证书。整个过程可以通过名为 [Let’s Encrypt](https://letsencrypt.org/) 的工具自动化并免费执行。

### 2.10.6. 区块链

![Bitboy，公共领域，通过 Wikimedia Commons 提供](images/btc.svg)

[Bitboy](https://commons.wikimedia.org/wiki/File:Bitcoin_logo.svg)，公共领域，通过 Wikimedia Commons 提供

很难在不提及区块链的情况下讨论密码学，区块链是加密货币背后的概念之一。区块链是一个共享账本（在 BitCoin 的情况下是交易记录），块不断被添加到其中以增加存储的信息。定期会创建一个新块，其中包含前一个块的哈希值以及自身的哈希值，供下一个块引用。通过检查这些哈希值，您可以证明每个块及其位置的完整性，从而创建一个公开可用、双方认可的网络发生事件记录。通常，为了防止不良行为者添加块，在将块添加到链中时，必须包含某种工作量证明（一种数学上困难的操作）或权益证明（对网络投资的记录）。

### 2.10.7. 可信平台模块（`TPM`）/ 硬件安全模块（`HSM`）

这些模块提供专门用于加密的硬件。`HSM` 是可移除模块，而 `TPM` 是主板芯片。许多密码依赖于可靠的熵源（随机性），这些模块提供了这种熵源。它们还可以通过将操作移至专用硬件，显著提高加密算法的运行速度。最后，这些模块可用于存储密钥，并仅通过模块访问它们。这可以增加一层安全性，防止密钥被轻易复制。

