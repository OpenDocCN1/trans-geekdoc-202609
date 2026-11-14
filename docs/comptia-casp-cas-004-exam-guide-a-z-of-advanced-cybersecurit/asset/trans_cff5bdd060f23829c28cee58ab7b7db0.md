

# 加密算法

## 对称加密算法

在这种情况下，你需要计算 `10 (10 – 1) / 2`，即 45 个密钥。使用对称算法时，加密密钥必须妥善保管。用户必须找到一种安全的带外方式来传递秘密密钥，例如快递或直接的物理接触，以便获取它。会话密钥是一种对称密钥，用于加密通信会话期间两个用户之间发送的通信。单密钥、秘密密钥、私钥和共享密钥密码学都是用来描述对称算法的术语。对称系统提供机密性，但不提供认证或不可抵赖性。如果双方用户使用相同的密钥，就很难判断消息的来源。`DES`、`AES`、`IDEA`、`Skipjack`、`Blowfish`、`Twofish`、`RC4/RC5/RC6` 和 `CAST` 都是对称算法。数据加密标准（`DES`）和三重 DES（`3DES`）是两种加密类型。

数据加密标准（`DES`）采用 `64-bit` 密钥，其中 `8 bits` 用于奇偶校验。因此，`DES` 的有效密钥长度为 `56 bits`。使用 `DES` 将消息分成 `64-bit` 的块。每个块经过十六轮置换和替换，生成一个 `64-bit` 的密文块。`3DES` 和 `AES` 已很大程度上取代了 `DES`。除了 `56-bit` 的 `DES` 密钥外，`DES-X` 是一种使用多个 `64-bit` 密钥的 `DES` 变体。明文与第一个 `64-bit` 密钥进行异或运算，然后使用 `DES` 进行加密。密文再与第二个 `64-bit` 密钥进行异或运算。`Double-DES` 是一种密钥长度为 `112 bits` 的 `DES` 变体，现已不再使用。发布后发生了一次安全攻击，将 `Double-DES` 的安全性降低到了与 `DES` 相同的水平。为了迅速替换 `DES`，人们创建了 `3DES`，它是一种使用三个 `56-bit` 密钥来增强安全性的 `DES` 变体。虽然 `3DES` 比 `DES` 更能抵抗攻击，但它的速度慢三倍。`3DES` 作为 `DES` 的替代品使用了一小段时间。尽管 `3DES` 至今仍在使用，但 `NIST` 已选择 `AES` 作为 `DES` 的继任者。

### 高级加密标准 (AES)

高级加密标准（`AES`）是 `DES` 算法的继任者。`AES` 标准采用 `Rijndael` 算法，尽管 `AES` 被视为标准。`AES` 和 `Rijndael` 经常互换使用。`Rijndael` 算法使用三种不同的分组大小——`128-bit`、`192-bit` 和 `256-bit`。对具有 `128-bit` 分组大小的 `128-bit` 密钥执行十轮变换。对具有 `192-bit` 分组大小的 `192-bit` 密钥执行十二轮变换。最后，对具有 `256-bit` 分组大小的 `256-bit` 密钥执行十四轮变换。`Rijndael` 使用三层变换——非线性 737 层、密钥加层和线性混合层。`Rijndael` 架构简单，代码量小，使其能在多种系统上运行。它是美国政府指定用于敏感但非机密材料的算法。

### IDEA

国际数据加密算法（`IDEA`）是一种 `64-bit` 分组密码。每个 `64-bit` 分组被分解为 `16` 个较小的块。`IDEA` 使用 `128-bit` 密钥对这 `16` 个较小块中的每一个执行八轮变换。`IDEA` 比 `DES` 更快且更难破解。`IDEA` 已被瑞士公司 Ascom 注册商标并授权许可，尽管该算法不如 `DES` 或 `AES` 常用，因为专利已于 2012 年过期。然而，`PGP` 使用了 `IDEA`。

### Twofish

`Twofish` 是 `Blowfish` 的一个变体，采用 `128-bit` 数据块和 `128-bit`、`192-bit`、`256-bit` 长度的密钥。它共有 `16` 轮变换。与 `Blowfish` 一样，`Twofish` 不是专利产品。

### RC4/RC5/RC6

Ron Rivest 总共设计了六种 `RC` 算法。`RC1` 从未发布，`RC2` 是一种 `64-bit` 分组密码，`RC3` 在发布前就被破解了。`RC4`、`RC5` 和 `RC6` 是安全专家应熟悉的主要 `RC` 实现。最广泛使用的流密码之一是 `RC4`，有时称为 `ARC4`。`SSL` 和 `WEP` 都使用它。`RC4` 具有 `40` 到 `2,048` 位的可配置密钥大小，最多可执行 `256` 轮变换。

`RC5` 是一种分组密码，密钥大小高达 `2,048` 位，`255` 轮变换。支持以下分组大小——`32`、`64` 和 `128` 位。由于 `RC5` 中变量众多，业界常将其称为 `RC5-w/r/b`，其中 `w` 代表分组大小，`r` 代表轮数，`b` 代表密钥中 `8-bit` 字节的数量。例如，`RC5-64/16/16` 意味着 `64-bit` 字（或 `128-bit` 数据块）、`16` 轮变换和 `16-byte`（`128-bit`）密钥。

`RC6` 是一种分组密码，采用与 `RC5` 相同的密钥大小、轮数和分组大小。`RC6` 最初旨在作为 `AES` 的解决方案，但在竞赛中败给了 `Rijndael`。`RC6` 比 `RC5` 更快。

## 非对称加密算法

非对称算法，通常称为双密钥或公钥密码学，同时使用 `public key`（公钥）和 `private key`（私钥）（或 `secret key` 秘密密钥）。每个人都可以访问 `public key`，而只有所有者可以访问 `private key`。消息使用这两个密钥中的一个进行加密，用另一个进行解密。即使 `public key` 是已知的，在非对称密码学中，尽管两个密钥在数学上相关，但要找到用户的 `private key` 几乎是不可能的。然而，如果发现了用户的 `private key`，系统可能会被攻破。非对称系统提供机密性、完整性、认证和不可抵赖性。由于双方用户各自拥有作为流程一部分的唯一密钥，因此可以确定通信的来源。如果组织的首要任务是保密性，消息应使用接收者的 `public key` 进行加密，这称为安全消息格式。如果组织的主要关注点是认证，消息应使用发送者的 `private key` 进行加密，这称为公开消息格式。使用公开消息格式时，任何拥有 `public key` 人都可以解密消息。`Diffie-Hellman`、`RSA`、`El Gamal`、`ECC`、`Knapsack` 和 `Zero Knowledge Proof` 是非对称算法的例子。

### Diffie-Hellman

`Diffie-Hellman` 负责密钥协商过程，其工作原理如下：

1.  John 和 Sally 决定使用 `Diffie-Hellman` 通过加密信道通话。
2.  John 创建一对 `private key` 和 `public key`，Sally 也创建一对 `private key` 和 `public key`。
3.  John 和 Sally 互相交换他们的 `public keys`。
4.  John 计算机上的程序使用 `Diffie-Hellman` 算法将 John 的 `private key` 和 Sally 的 `public key` 结合，Sally 计算机上的程序使用 `Diffie-Hellman` 方法将 Sally 的 `private key` 和 John 的 `public key` 结合。
5.  使用非对称密钥协商过程，为 John 和 Sally 建立相同的 `shared value`（共享值），进而在每台机器上生成相同的 `symmetric key`（对称密钥）。

通过这种方法，`Diffie-Hellman` 实现了安全的密钥分发，但不提供保密性、认证或不可抵赖性。该算法基于 `Discrete logarithms`（离散对数）。除非组织在 `Diffie-Hellman` 过程开始时使用 `digital signatures`（数字签名）或 `digital certificates`（数字证书）进行认证，否则 `Diffie-Hellman` 容易受到 `man-in-the-middle attacks`（中间人攻击）。

### RSA

