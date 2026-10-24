# 深入密码学（第2版）：现代加密实用入门指南





## 对《严肃密码学》的赞誉

> “填补了密码学领域对一本通俗易懂且可读性强的资源的需求，带领读者了解各种密码学工具及其使用方法，以及散布全书的那些重要的‘可能出错之处’章节……*《严肃密码学》*是对该领域的一本有趣入门书，强烈推荐。”
> 
> —YEHUDA LINDELL，Coinbase 密码学负责人

> “一本真正严肃的入门书；它用清晰简洁的文字描述了基本概念。它的目的不是空洞地娱乐读者，而是传授知识。这是那种你会不断查阅的‘第一本书’，因为它有正确的结构，可以在此基础上建立对密码学的透彻理解。”
> 
> —THOMAS PORNIN，NCC Group 技术副总裁

> “就像一位睿智的朋友在不让你头晕的情况下解释密码学的所有奥秘。这本书以其实用的方法脱颖而出，提供了现实世界的应用和见解。它被认为是我团队中新入职安全工程师的必读材料，为他们的职业发展提供了重要基础。”
> 
> —ANASTASIIA VOITOVA，Cossack Labs 安全工程负责人

> “一本优秀的现代加密与密码学入门书。对于那些希望快速掌握这些主题的人来说，这是一本极好的快速指南。”
> 
> —BEN ROTHKE，RSA 大会

> “这真是一封写给密码学的情书。”
> 
> —NADIM KOBEISSI

> “Aumasson 成功地确保读者对密码学的核心思想有扎实理解……*《严肃密码学》*是任何想进入密码工程领域的人的必读之作。”
> 
> —GREGORY PARFITT，《信息安全杂志》

## 关于作者

JP Aumasson 自2006年以来一直从事密码学的开发、研究和破解工作。他是广泛使用的密码算法 BLAKE2、BLAKE3 和 SipHash 的开创者，并组织了密码哈希竞赛，该竞赛催生了 Argon2 标准。JP 的职业生涯跨越学术界——他在 EPFL 获得博士学位；付费电视安全行业；以及担任私营和公共部门客户的安全顾问。他目前是 Taurus SA 的联合创始人兼首席安全官，这是一家总部位于日内瓦的全球金融科技公司，协助金融机构保护和管理其数字资产。

## 关于技术审校

Pascal Junod 是一位密码学家，在设计、实现、审计、破解、写作和讲解现实世界密码学和网络安全系统方面拥有超过20年的学术和工业经验。他的主要兴趣领域包括工业密码学、软件保护和逆向工程。他还喜欢越野跑、演奏手风琴和照顾家人。



## 第一版序言

如果你读过一两本关于计算机安全的书籍，你可能遇到过对密码学领域的常见看法。“密码学，”他们说，“是链条中最强的一环。” 这确实是高度赞扬，但也多少有些轻视。如果密码学确实是系统中最强的一部分，为什么还要投入时间去改进它，而系统里还有这么多其他领域会更受益于你的关注呢？

如果说有一件事我希望你从这本书中带走，那就是对密码学的这种看法是理想化的；它在很大程度上是一个神话。理论上的密码学很强，但实践中的密码学与其他任何安全系统的方面一样容易失败。当密码学实现由缺乏足够谨慎或经验的非专家开发时尤其如此，而这正是当今部署的许多密码学系统的现状。更糟的是：当密码学实现失败时，它们往往以独特而壮观的方式失败。

但你为什么应该关心，以及为什么是这本书？

当我近二十年前开始从事应用密码学领域的工作时，提供给软件开发者的信息往往是零散且过时的。密码学家开发算法和协议，而密码学工程师则将它们实现为不透明、文档不佳的密码学库，主要面向其他专家。存在——并且一直存在——一个巨大的鸿沟，鸿沟在那些了解并理解密码学算法的人与那些使用它们（或因忽视而自取其祸）的人之间。市场上有一些不错的教科书，但能为从业者提供实用工具的就更少了。

结果并不好看。我说的是带有“CVE”和“严重性：高”标签的妥协，以及在少数令人震惊的案例中，对标记为“绝密”的幻灯片的攻击。你可能熟悉其中一些更著名的例子，只是因为它们影响了你所依赖的系统。许多这些问题之所以发生，是因为密码学很微妙且在数学上很优雅，也是因为密码学专家未能与实际编写软件的工程师分享他们的知识。

幸运的是，这已经开始改变，而这本书就是这种变化的体现。

*严肃的密码学*是由应用密码学领域最顶尖的专家之一撰写的，但它并非面向其他专家。当然，它也不是对该领域的肤浅概述。相反，它包含对密码学工程的全面而最新的讨论，旨在帮助计划在该领域工作的从业者做得更好。在这些页面中，你将不仅学习密码学算法的工作原理，还将学习如何在真实系统中使用它们。

本书从对许多关键密码学原语的探索开始，包括诸如分组密码、公钥加密方案、哈希函数和随机数生成器等基本算法。每章都提供算法的工作示例，以及你应该或应该*不*做的事情。最后几章涵盖了诸如 TLS 等高级主题，以及密码学的未来——量子计算机到来使我们的生活复杂化后该怎么办。

虽然没有一本书能解决我们所有的问题，但一点知识就能大有裨益。这本书包含大量的知识。也许足够让真实的、已部署的密码学达到许多人对它的高期望。

祝阅读愉快。

Matthew D. Green
计算机科学副教授
信息安全研究所
约翰霍普金斯大学

## 致谢

### 第一版

我要感谢 Jan、Annie 以及为本书做出贡献的 No Starch 团队的其余成员，尤其是 Bill 从一开始就相信这个项目，感谢他耐心消化困难的主题，并将我笨拙的草稿改写成可读的页面。我还要感谢 Laurel 让这本书看起来如此漂亮，并处理了我大量的勘误请求。

在技术方面，如果没有以下人员的帮助，本书将包含更多错误和不准确之处：Jon Callas、Bill Cox、Niels Ferguson、Philipp Jovanovic、Samuel Neves、David Reid、Philipp Rogaway 和 Erik Tews，以及报告错误的《早期访问版》所有读者。最后，感谢 Matt Green 撰写序言。

我还要感谢我的前雇主 Kudelski Security 允许我抽出时间撰写这本书。最后，我向 Alexandra 和 Melina 表示最深切的感谢，感谢她们的支持和耐心。

洛桑，2017年05月17日（三个质数）

### 第二版

我要感谢第一版的所有读者，特别是那些主动联系分享反馈并帮助改进本书的人。本第二版得益于 No Starch Press 的细致编辑（感谢 Eva、Jill、Kim 和 Miles）以及 Pascal Junod 的仔细技术审阅。毋庸置疑，本书的不足之处在我。

洛桑，2024年04月14日

## 引言

![](img/ace4de942d037de8ea5835bc9fbe57cd_22_0.png)

我写这本书是为了成为我开始学习密码学时希望拥有的那一本。2005年，我在巴黎附近攻读硕士学位，并热切地为下学期密码学课程注册。不幸的是，该课程因注册学生太少而被取消。“密码学太难了，”学生们争辩道，转而大量报名参加计算机图形学和数据库课程。

此后我听过“密码学很难”数十次。但它真的*那样*难吗？要演奏乐器、掌握一门编程语言，或将任何领域的应用程序付诸实践，你需要学习一些概念和符号，但这不需要博士学位。成为一名合格的密码学家的情况也一样。也许密码学被认为很难，是因为密码学家没有很好地教授它。

我也写这本书是因为密码学已经扩展为一个多学科领域。要在密码学中做任何有用的、相关的事情，你需要理解*围绕*密码学的概念：网络和计算机如何工作，用户和系统需要什么，以及攻击者如何滥用算法及其实现。换句话说，你需要与现实的联系。

### 本书的方法

这本书的初始标题是 *Crypto for Real*，以强调我所遵循的实践导向、现实世界、不拐弯抹角的方法。我希望让密码学变得易于接近，不是通过将其简化，而是通过将其与真实应用联系起来。我提供源代码示例并描述真实的错误和恐怖故事。

除了与现实的清晰联系外，本书的另一个基石是其简洁性和现代性。我更注重形式上的简洁而非实质上的简洁：我以不枯燥的数学形式主义呈现非平凡的概念。相反，我试图传达对密码学核心思想的理解，这些思想比记住一堆方程更重要。为了确保本书的现代性，我涵盖了密码学的最新发展和应用，例如 TLS 1.3 和后量子密码学。我不讨论 DES 或 MD5 等过时或不安全的算法的细节。RC4 是一个例外，但它仅被包含在内以解释其为何如此脆弱，并展示其所属类型的流密码的工作原理。

*严肃的密码学*不是密码学软件的指南，也不是技术规范的汇编——这些东西你很容易在网上找到。相反，其首要目标是让你对密码学感到兴奋，并在过程中教授其基本概念。

### 本书适合谁

在写作时，我经常想象读者是一名开发者，他接触过密码学，但在阅读晦涩的教科书和研究论文后仍然感到困惑和沮丧。开发人员通常需要——并且希望——更好地掌握密码学，以避免不幸的设计选择，我希望这本书能有所帮助。

如果你不是开发者，不用担心！本书不需要编码技能，并且对任何了解计算机科学基础和高中文数学（概率、模运算等概念）的人都是可访问的。

然而，这本书仍然可能令人望而生畏，尽管其相对易于访问，但要充分利用它需要付出一些努力。我喜欢登山类比：作者为你铺平道路，为你提供绳索和冰镐来促进你的工作，但你自己完成攀登。学习本书中的概念需要努力，但会很有收获。



## 本书的组织结构

本书共有15章，大致分为四个部分。各章大多相互独立，除了第9章，它为其后的三章奠定了基础。我建议在阅读其他内容之前先阅读前三章。

## 第一部分：基础

- **第1章：加密** 介绍安全加密的概念，从弱的纸笔密码到强随机加密
- **第2章：随机性** 描述伪随机生成器的工作原理，使其安全需要什么，以及如何安全使用
- **第3章：密码学安全** 讨论安全性的理论和实践概念，并比较可证明的安全性与或然安全性

## 第二部分：对称密码

- **第4章：分组密码** 处理按块处理消息的密码，重点关注最著名的一种，即高级加密标准（AES）
- **第5章：流密码** 介绍产生随机外观比特流并与待加密消息进行异或的密码
- **第6章：哈希函数** 讨论唯一不使用密钥的算法，它们最终成为最普遍的密码学构建模块
- **第7章：带密钥哈希** 解释如果将哈希函数与密钥结合会发生什么，以及它如何用于验证消息
- **第8章：认证加密** 展示某些算法如何同时加密和验证消息，以标准 AES-GCM 等为例

## 第三部分：非对称密码

- **第9章：难题** 阐述公钥加密背后的基本概念，使用计算复杂性概念
- **第10章：RSA** 利用因数分解问题，通过简单的算术运算构建安全的加密和签名方案
- **第11章：Diffie–Hellman** 将非对称密码学扩展到密钥协商的概念，其中双方仅使用非秘密值建立秘密值
- **第12章：椭圆曲线** 提供椭圆曲线密码学的温和介绍，这是最快的非对称密码学类型

## 第四部分：应用

- 第13章：TLS 专注于传输层安全（TLS），可以说是网络安全中最重要的协议
- 第14章：量子与后量子 介绍量子计算和后量子密码学的概念
- 第15章：加密货币密码学 以区块链应用中发现的高级密码方案概述作结

## 关于第二版

本《严肃的密码学》第二版在首版七年后出版。此后，密码学经历了重大变化。如今，术语 *密码学* 常让人联想到区块链、比特币和其他加密货币，而非密码学本身。尽管这些技术的社会效益值得商榷，但它们对密码学研究和工程发展的不可否认的影响不容忽视。认识到这一点，我撰写了第15章“加密货币密码学”，深入探讨了区块链应用中采用的引人入胜的密码技术，代表了密码学领域一些最有趣的进展。

我对每一章都做了重大修改，根据新的密码学发展更新了文本，并提高了文本的清晰度和简洁性。其中最显著的补充包括：第2章关于 Linux 内核随机性的讨论已更新，以描述 */dev/random* 和 */dev/urandom* 接口的新行为，第12章新增了关于 EdDSA 和 Ed25519 签名方案的部分，第14章介绍了 NIST 的后量子密码标准化项目。

## 缩写

| 缩写 | 含义 | 缩写 | 含义 |
|---|---|---|---|
| AE | authenticated encryption | CMAC | cipher-based MAC |
| AEAD | authenticated encryption with associated data | COA | ciphertext-only attackers |
| AES | Advanced Encryption Standard | CPA | chosen-plaintext attackers |
| AES-NI | AES native instructions | CRT | Chinese remainder theorem |
| AKA | authenticated key agreement | CTR | counter mode |
| API | application programming interface | CVP | closest vector problem |
| ARX | add-rotate-XOR | DDH | decisional Diffie–Hellman |
| ASIC | application-specific integrated circuit | DES | Data Encryption Standard |
| BLS | Barreto–Lynn–Scott | DH | Diffie–Hellman |
| BLS | Boneh–Lynn–Shacham | DLP | discrete logarithm problem |
| CA | certificate authority | DRBG | deterministic random bit generator |
| CAESAR | Competition for Authenticated Encryption: Security, Applicability, and Robustness | ECB | electronic codebook |
| CBC | cipher block chaining | ECC | elliptic curve cryptography |
| CCA | chosen-ciphertext attackers | ECDH | elliptic curve Diffie–Hellman |
| CDH | computational Diffie–Hellman | ECDLP | elliptic-curve discrete logarithm problem |
|  |  | ECDSA | elliptic-curve digital signature algorithm |

| 缩写 | 含义 | 缩写 | 含义 |
|---|---|---|---|
| FDH | Full Domain Hash | NP | nondeterministic polynomial-time |
| FHE | fully homomorphic encryption | OAEP | Optimal Asymmetric Encryption Padding |
| FIPS | Federal Information Processing Standards | OCB | offset codebook |
| FPE | format-preserving encryption | P | polynomial time |
| FPGA | field-programmable gate array | PLD | programmable logic device |
| FSR | feedback shift register | PoW | proof of work |
| GCD | greatest common divisor | PRF | pseudorandom function |
| GCM | Galois Counter Mode | PRNG | pseudorandom number generator |
| GNFS | general number field sieve | PRP | pseudorandom permutation |
| HKDF | HMAC-based key derivation function | PSK | preshared key |
| HMAC | hash-based message authentication code | PSS | Probabilistic Signature Scheme |
| HTTPS | HTTP Secure | QR | quarter-round |
| IND | indistinguishability | QRNG | quantum random number generator |
| IP | Internet Protocol | RFC | request for comments |
| IV | initial value | RNG | random number generator |
| KDF | key derivation function | RSA | Rivest–Shamir–Adleman |
| KPA | known-plaintext attackers | SHA | Secure Hash Algorithm |
| LFSR | linear feedback shift register | SIS | short integer solution |
| LSB | least significant bit | SIV | synthetic IV |
| LWE | learning with errors | SNARK | succinct noninteractive argument of knowledge |
| MAC | message authentication code | SPN | substitution–permutation network |
| MD | message digest | SSH | Secure Shell |
| MitM | meet-in-the-middle | SSL | Secure Sockets Layer |
| MPC | multiparty computation | TE | tweakable encryption |
| MQ | multivariate quadratics | TLS | Transport Layer Security |
| MQV | Menezes–Qu–Vanstone | TMTO | time-memory trade-off |
| MSB | most significant bit | UDP | User Datagram Protocol |
| MT | Mersenne Twister | UH | universal hash |
| NFSR | nonlinear feedback shift register | WEP | Wired Equivalent Privacy |
| NIST | National Institute of Standards and Technology | WOTS | Winternitz one-time signature |
| NM | nonmalleability | XOR | exclusive OR |
|  |  | ZKP | zero-knowledge proof |

## 第一部分

## 基础

### 1

### 加密

![](img/ace4de942d037de8ea5835bc9fbe57cd_30_0.png)

加密是密码学的首要应用；它使数据不可理解以确保其 *保密性*。加密使用一种称为 *密码* 的算法和一个称为 *密钥* 的秘密值。如果你不知道密钥，就无法解密，也无法了解加密消息的任何信息——攻击者也一样。

本章重点介绍对称加密，这是最简单的加密类型。在 *对称加密* 中，解密密钥与加密密钥相同（不像 *非对称加密* 或 *公钥加密*，其中密钥不同）。你将首先学习对称加密的最弱形式，即仅对最不识字的攻击者安全的古典密码，然后我们将转向最强形式，这些形式是永久安全的。




## 基础知识

在加密消息时，*明文*（plaintext）指未加密的消息，而*密文*（ciphertext）指加密后的消息。因此，密码（cipher）由两个函数组成：*加密*（encryption）将明文转换为密文，*解密*（decryption）将密文恢复为明文。不过，当我们说“密码”时，往往实际指的是“加密”。例如，图 1-1 展示了一个密码 **E**，用一个方框表示，它接收明文 *P* 和密钥 *K* 作为输入，并产生密文 *C* 作为输出。我会把这个关系写成 *C* = **E**(*K*, *P*)。类似地，当密码处于解密模式时，我会写成 **D**(*K*, *C*)。

![](img/ace4de942d037de8ea5835bc9fbe57cd_31_0.png)

图 1-1：基本的加密与解密

**注意** 对于某些密码，密文与明文的大小相同；对于另一些密码，密文会稍长一些。但密文永远不会比明文短。

## 经典密码

经典密码出现于计算机之前，因此处理的是字母而非比特，这使得它们比像数据加密标准这样的现代密码简单得多。例如，在古罗马或第一次世界大战期间，你无法借助计算机芯片的能力来打乱消息，只能完全依靠纸和笔。经典密码有很多，但最著名的当属凯撒密码和维吉尼亚密码。

## 凯撒密码

凯撒密码之所以得名，是因为罗马历史学家苏埃托尼乌斯记载，尤利乌斯·凯撒曾使用过它。它的加密方式是让消息中的每个字母在字母表中向后移动三个位置，如果移动到达 *Z*，就回绕到 *A*。例如，*ZOO* 加密为 *CRR*，*FDHVDU* 解密为 *CAESAR*，以此类推，如图 1-2 所示。数字 3 并没有什么特别之处，它只是比 11 或 23 更容易在心算中计算。

![](img/ace4de942d037de8ea5835bc9fbe57cd_32_0.png)

图 1-2：凯撒密码

凯撒密码非常容易破解：要解密给定的密文，只需把字母向后移动三个位置，就能得到明文。话虽如此，在克拉苏和西塞罗的时代，凯撒密码可能已经足够强大了。由于不涉及密钥（它始终是 3），凯撒密码的使用者曾假定攻击者目不识丁或没受过什么教育，根本看不出来——这种假设在今天已经远不那么现实了。（事实上，2006 年，意大利警方在解密了写在小纸片上的消息后逮捕了一名黑手党头目。这些消息使用的是凯撒密码的一种变体加密：例如，ABC 被加密为 456，而不是 DEF。）

凯撒密码能变得更安全吗？你可能会设想一个使用秘密移位值而不是固定 3 的版本，但这帮助不大，因为攻击者可以尝试全部 25 种可能的移位值，直到解密出的消息有意义为止。

## 维吉尼亚密码

大约过了 1500 年，凯撒密码才以维吉尼亚密码的形式得到了有意义的改进。维吉尼亚密码由意大利人乔瓦尼·巴蒂斯塔·贝拉索于 16 世纪发明。维吉尼亚这个名字来自法国人布莱斯·德·维吉尼亚，他在 16 世纪发明了另一种不同的密码，但由于历史上的错误归因，维吉尼亚的名字被保留了下来。尽管如此，维吉尼亚密码还是流行开来，后来在美国内战期间被南方邦联军队使用，在第一次世界大战期间被瑞士军队使用，此外还有其他使用者。

维吉尼亚密码与凯撒密码类似，不同之处在于字母不是移动三个位置，而是根据密钥定义的值来移动。密钥是一组字母，这些字母根据其在字母表中的位置来表示数字。例如，如果密钥是 DUH，那么明文中的字母就按照 3、20、7 这些值来移位，因为 D 在 A 之后三个字母，U 在 A 之后 20 个字母，H 在 A 之后七个字母。3、20、7 这个模式会不断重复，直到加密完整个明文。例如，使用 DUH 作为密钥，单词 CRYPTO 会加密为 FLFSNV：C 移动三个位置变成 F，*R* 移动 20 个位置变成 *L*，以此类推。图 1-3 展示了加密句子 *THEY DRINK THE TEA* 时的这一原理。

![](img/ace4de942d037de8ea5835bc9fbe57cd_33_0.png)

维吉尼亚密码显然比凯撒密码更安全，但它仍然相当容易破解。破解它的第一步是确定密钥的长度。以图 1-3 中的例子为例，其中 *THEY DRINK THE TEA* 使用密钥 *DUH* 加密为 *WBLBXYLHRWBLWYH*。（空格通常会移除，以隐藏单词边界。）注意，在密文 *WBLBXYLHRWBLWYH* 中，三字母组 *WBL* 在密文中出现了两次，间隔为九个字母。这表明，同一个三字母单词使用了相同的移位值进行加密，因此每次都产生 *WBL*。密码分析者由此可以推断出，密钥的长度要么是 9，要么是一个能整除 9 的数（也就是 3）。此外，他们可能会猜测这个重复出现的三字母单词是 *THE*，从而确定 *DUH* 是一个可能的加密密钥。

破解维吉尼亚密码的第二步是利用一种称为*频率分析*的方法来确定实际密钥。频率分析利用的是语言中字母分布不均匀的特点。例如，在英语中，*E* 是最常见的字母，所以如果你发现 *X* 是某个密文中最常见的字母，那么该位置最可能的明文值就是 *E*。

尽管相对较弱，维吉尼亚密码在其时代或许已经足以安全地加密消息。频率分析有其局限性：它需要若干个句子才能发挥作用，这意味着如果密码被用来加密短消息，频率分析就不起作用。另外，大多数消息只需要在短时间内保密，所以即使密文最终被敌人破译，也没什么关系。（19 世纪的密码学家奥古斯特·克尔克霍夫估计，大多数战时加密消息只需保密三到四个小时。）

## 密码的工作原理

基于简单的凯撒密码和维吉尼亚密码，我们可以尝试抽象出密码的工作原理，即识别它的两个主要组成部分：置换（permutation）和操作模式（mode of operation）。*置换*是一种变换条目的函数（在密码学中，条目是一个字母或一组比特），它使得每个条目都有唯一的逆（例如，凯撒密码的随机选择置换：知道 A 加密为 F，只会告诉你 B 不会加密为 F）。我们将满足这些标准的置换称为安全置换。接下来你会看到，安全置换是构建安全密码的必要条件，但仅靠它还不够。密码还需要一种操作模式，以支持任意长度的消息。

## 操作模式

假设我们有一个安全置换，例如将 A 变换为 X、B 变换为 M、N 变换为 L。于是，单词 BANANA 会加密为 MXLXLX，其中每个出现的 A 都被替换为 X。因此，对明文中的所有字母使用同一个置换，会暴露任何重复的字母。通过分析这些重复，你或许无法获知完整消息，但能了解到一些信息。在 BANANA 这个例子中，你不需要密钥就能猜到，明文中的三个 X 位置共享同一个字母，而两个 L 位置共享另一个字母。如果你知道这条消息是一种水果的名字，你就能确定它是 BANANA，而不是 CHERRY、LYCHEE 或其他六个字母的水果。

密码的操作模式（或简称模式）通过对重复字母使用不同的置换，来减轻明文中重复字母的暴露。维吉尼亚密码的模式部分解决了这个问题：如果密钥有 N 个字母长，那么每 N 个连续字母就会使用 N 种不同的置换。然而，这仍然会在密文中产生模式，因为消息中每隔 N 个字母就使用同一种置换。这就是频率分析能够破解维吉尼亚密码的原因。

如果维吉尼亚密码只加密与密钥等长的明文，频率分析就可以被击败。但即使如此，还有另一个问题：多次使用同一个密钥会暴露明文之间的相似性。例如，使用密钥 KYN 时，单词 TIE 和 PIE 分别加密为 DGR 和 ZGR。两者都以相同的两个字母（GR）结尾，这揭示出两个明文也有相同的最后两个字母。安全密码不应该出现这种模式。

要构建安全密码，你必须将安全置换与安全模式结合起来。理想情况下，这种组合能让攻击者除了消息的长度之外，什么也了解不到。

## 为什么经典密码不安全

经典密码注定不安全，因为它们仅限于能在脑中或纸面上完成的操作。它们缺乏计算机的计算能力，容易被简单的计算机程序破解。让我们来看看，这种简单性在当今世界使它们不安全的根本原因。

请记住，密码的置换必须看起来随机才能安全。当然，看起来随机的最好方式就是真正随机——也就是说，从所有置换的集合中随机选择每一个置换。而可供选择的置换非常多。对于由 26 个字母组成的英语字母表，大约有 2^88 种置换：


26! = 403291461126605635584000000 ≈ 2^88

这里，感叹号 (!) 是阶乘符号，定义如下：

n! = n × (n − 1) × (n − 2) × … × 3 × 2

(要了解为何得到这个数字，可将排列视为重新排序的字母列表：第一个可能的字母有 26 种选择，第二个有 25 种可能，第三个有 24 种，依此类推。) 这个数字巨大：它与人体中原子数量的量级相同。但古典密码只能使用其中一小部分排列——即那些需要简单操作（如移位）并且具有简短描述（如简短算法或小型查找表）的排列。问题在于，安全的排列无法同时满足这两个限制。

你可以通过选择一个随机排列，使用简单操作得到安全的排列，将其表示为 25 个字母的表格（足以表示 26 个字母的排列，其中缺少第 26 个字母），并通过在该表格中查找字母来应用它。但这样你就不会有简短的描述。例如，用来描述 10 个不同排列需要 250 个字母，而不是维吉尼亚密码中使用的仅仅 10 个字母。

你也可以用简短的描述产生安全的排列。不要只对字母表进行移位，还可以使用加法和乘法等更复杂的操作。这就是现代密码的工作方式：给定通常为 128 或 256 位的密钥，它们执行数百次位操作来加密单个字母。这个过程在每秒可执行数十亿次位操作的计算机上很快，但手工完成需要数小时，并且仍然容易受到频率分析的攻击。

## 完美密码：一次性密码本

本质上，古典密码如果没有巨大的密钥就无法安全，但用巨大的密钥加密是不切实际的。然而，一次性密码本就是这样的密码，它是最安全的密码。事实上，它保证了完美保密：即使攻击者拥有无限的计算能力，也无法了解明文的任何信息，除了其长度。

在接下来的章节中，我将向你展示一次性密码本的工作原理，然后提供其安全性证明的概要。

## 加密与解密

一次性密码本取一个明文 P 和一个随机密钥 K，其长度与 P 相同，并生成一个密文 C，定义为

C = P ⊕ K

其中 C、P 和 K 都是相同长度的位串，而 ⊕ 是按位异或操作（XOR），定义为 0 ⊕ 0 = 0，0 ⊕ 1 = 1，1 ⊕ 0 = 1，1 ⊕ 1 = 0。

> **NOTE** *我以通常的形式介绍一次性密码本，即在位上操作，但它可以适配到其他符号。例如，使用字母时，你会得到一种凯撒密码的变体，其中每个字母的移位索引都是随机选择的。*

一次性密码本的解密与加密相同；它只是异或：$P = C \oplus K$。事实上，我们可以验证 $C \oplus K = P \oplus K \oplus K = P$，因为将 $K$ 与自身进行异或会得到全零串 $000\ldots000$。就是这样——甚至比凯撒密码还要简单。

例如，如果 $P = 01101101$ 且 $K = 10110100$，则我们可以计算如下：

$$C = P \oplus K = 01101101 \oplus 10110100 = 11011001$$

解密通过计算以下内容来恢复 $P$：

$$P = C \oplus K = 11011001 \oplus 10110100 = 01101101$$

重要的是，一次性密码本只能使用 *一次*：每个密钥 $K$ 只能使用一次。如果相同的 $K$ 用于加密 $P_1$ 和 $P_2$ 得到 $C_1$ 和 $C_2$，那么窃听者可以计算如下：

$$C_1 \oplus C_2 = (P_1 \oplus K) \oplus (P_2 \oplus K) = P_1 \oplus P_2 \oplus K \oplus K = P_1 \oplus P_2$$

因此窃听者将了解到 $P_1$ 和 $P_2$ 的异或差值，这本应是保密的信息。此外，如果任一明文消息已知，则另一个消息可以被恢复。

一次性密码本使用起来极其不便，因为它需要与明文一样长的密钥，并且每个新消息或数据组都需要一个新随机密钥。要加密一个 1TB 的硬盘，你就需要另一个 1TB 的硬盘来存储密钥！尽管如此，一次性密码本在历史上一直被使用——二战期间由英国特别行动执行局使用、苏联间谍使用、国家安全局（NSA）使用——并且至今仍在特定环境中使用。（我听说过瑞士银行家无法就双方都信任的密码达成一致，最终使用一次性密码本，但我不推荐这样做。）

## 为什么一次性密码本是安全的？

尽管一次性密码本不实用，但了解其安全性的原因很重要。在 1940 年代，美国数学家克劳德·香农证明了要实现完美保密，一次性密码本的密钥必须至少与消息一样长。证明的思路相当简单。你假设攻击者拥有无限的能力，因此可以尝试所有密钥。目标是进行加密，使得攻击者在给定某个密文的情况下无法排除任何可能的明文。

一次性密码本完美保密的直觉如下：如果 $K$ 是随机的，那么 resulting $C$ 对攻击者来说看起来与 $K$ 一样随机，因为随机串与任何固定串的异或会产生随机串。要了解

## 加密安全性

古典密码不安全，但像一次性密码本这样完美安全的密码不实用。因此，如果我们想要安全且可用的密码，就必须在安全性上做出一些让步。但除了显而易见且非正式的“窃听者无法解密安全消息”之外，安全到底意味着什么？

如果即使给定大量明文-密文对，也无法了解密码应用于其他明文或密文时的行为，则该密码是安全的。这引发了新的问题：

- 攻击者如何获得这些对？“大量”有多大？这一切都由攻击模型定义，即关于攻击者能做什么和不能做什么的假设。
- 可能“学到”什么，我们谈论的是密码的什么“行为”？这由安全目标定义，即被认为构成成功攻击的描述。

攻击模型和安全目标必须一起考虑；你不能在不说明针对谁或从什么方面安全的情况下声称一个系统是安全的。安全概念是安全目标与攻击模型的组合。我们将说，如果在给定模型下工作的任何攻击者都无法破坏安全目标，则密码实现了某种安全概念。

## 攻击模型

攻击模型是对攻击者可能如何与密码交互以及他们能做什么和不能做什么的一组假设。攻击模型的目标如下：

- 为设计密码的密码学家设定要求，以便他们知道要防范哪些攻击者和哪些类型的攻击。
- 为用户提供指导，说明在他们的环境中使用密码是否安全。
- 为尝试破解密码的密码分析人员提供线索，以便他们知道给定的攻击是否有效。攻击只有在所考虑的模型中可行时才有效。

攻击模型不需要完全符合现实；它们是一种近似。正如统计学家乔治·E·P·博克斯所说，“所有模型都是错的；实际问题是它们必须有多错才不至于无用。”要在密码学中有用，攻击模型至少应涵盖攻击者实际可以用来攻击密码的行为。如果模型高估了攻击者的能力是有益的，因为它有助于预见未来的攻击技术——只有偏执的密码学家才能生存。糟糕的模型低估了攻击者，并通过让密码在理论上看起来安全而在现实中不安全来提供虚假的安全感。

## 柯克霍夫斯原理

所有模型中都做出的一个假设是 *Kerckhoffs’s principle*，它指出密码的安全性应仅依赖于密钥的保密性，而不依赖于密码本身的保密性。今天，当密码和协议被公开指定并被所有人使用时，这可能听起来很明显。但在历史上，荷兰语言学家奥古斯特·柯克霍夫斯指的是专门为特定军队或师设计的军事加密机器。引用他 1883 年的论文《La Cryptographie Militaire》，其中他列出了军事加密系统的六项要求：“系统不得要求保密，可以被敌人窃取而不造成麻烦。”

## 黑盒模型

让我们考虑一些以攻击者可以观察的内容和他们可以对密码进行的查询来表达的有用攻击模型。对我们而言，*query* 是将输入值发送到某个函数并返回输出，而不暴露该函数细节的操作。例如，*encryption query* 接受一个明文并返回相应的密文，而不透露秘密密钥。

我们称这些为 *black-box models*，因为攻击者只能看到进入和离开密码的内容。例如，一些智能卡芯片安全地保护了密码的内部结构以及其密钥，但你被允许连接到芯片并要求它解密任何密文。攻击者随后会收到相应的明文，这可能有助于他们确定密钥。这是一个 *decryption queries* 可能的真实例子。

有几种不同的黑盒攻击模型。这里，我按从弱到强的顺序列出它们，描述每个模型中攻击者的能力：

- **Ciphertext-only attackers (COAs)** 观察密文但不知道相关的明文或明文是如何选择的。COA 模型中的攻击者是被动的，不能执行加密或解密查询。
- **Known-plaintext attackers (KPAs)** 观察密文并且知道相关的明文。因此 KPA 模型中的攻击者会得到明文-密文对列表，其中明文假定是随机选择的。KPA 是一个被动攻击模型。
- **Chosen-plaintext attackers (CPAs)** 可以对自己选择的明文执行加密查询并观察 resulting 密文。该模型捕获了攻击者可以选择要加密的明文全部或部分然后看到密文的情况。与 COA 或 KPA 等被动模型不同，CPAs 是主动攻击者，因为他们影响加密过程而不是被动窃听。
- **Chosen-ciphertext attackers (CCAs)** 既可以加密也可以解密；也就是说，他们可以执行加密查询和解密查询（针对目标密文以外的密文）。CCA 模型

初听起来似乎荒谬——如果能解密，还需要什么呢？——但与 CPA 模型类似，它旨在描述攻击者能够对密文产生一定影响并随后获得明文的情况。此外，解密并不总是足以攻破系统。例如，某些视频保护设备允许攻击者使用设备的芯片执行加密查询和解密查询，但在这种情况下，攻击者感兴趣的是密钥以便重新分发它；在这种情况下，免费解密不足以破坏系统。

在前述模型中，被观察到的密文以及被查询的密文都不是免费获得的。每个密文都来自加密函数的计算。这意味着通过加密查询生成 2^N 个明文–密文对所花费的计算量大约与尝试 2^N 个密钥相当，例如。计算攻击成本时应考虑查询的成本。

## 灰盒模型

在 *灰盒模型* 中，攻击者可以访问密码的 *实现*。这使得灰盒模型比黑盒模型更贴近现实，适用于智能卡、嵌入式系统和虚拟化系统等应用，攻击者通常可以物理访问这些系统，从而篡改算法的内部。同样，灰盒模型比黑盒模型更难定义，因为它们依赖于物理、模拟特性，而不仅仅是算法的输入和输出，而且密码理论往往无法抽象出现实世界的复杂性。

*侧信道攻击* 是灰盒模型中的一类攻击。侧信道是依赖于密码实现的信息来源，无论是软件还是硬件。侧信道攻击者观察或测量密码实现的模拟特征，但不改变其完整性；它们是 *非侵入式* 的。对于纯软件实现，典型的侧信道是执行时间和围绕密码的系统的行为，例如错误信息、返回值和分支。以智能卡上的实现为例，典型的侧信道攻击者会测量功耗、电磁辐射或声学噪声。

*侵入式攻击* 是对密码实现的一类攻击，比侧信道攻击更强大，也更昂贵，因为它们通常需要复杂的设备。你可以用标准 PC 和现成的示波器运行基本的侧信道攻击，但侵入式攻击可能需要诸如高分辨率显微镜和化学实验室之类的工具。侵入式攻击包括一套完整的技术和程序，包括使用硝酸去除芯片封装、获取显微图像、部分逆向工程，以及使用激光故障注入和电磁注入等技术修改芯片行为。

## 安全目标

我曾非正式地将安全目标定义为“不能从密码的行为中获知任何信息。”为了将这一思想转化为严格的数学定义，密码学家定义了两个安全目标，它们对应于关于从密码行为中获知信息的不同概念：

### 不可区分性 (IND)
密文应与随机字符串不可区分。这通常用一个假设游戏来说明：如果攻击者选择两个明文，然后接收其中一个的密文（随机选择），他们即使通过对这两个明文执行加密查询（如果模型是 CCA 而非 CPA，则还包括解密查询）也不应能够判断哪个明文被加密了。

### 非可塑性 (NM)
给定密文 C₁ = E(K, P₁)，应不可能创建另一个密文 C₂，其对应的明文 P₂ 与 P₁ 以有意义的方式相关（例如，创建等于 P₁ ⊕ 1 或 P₁ ⊕ X 的 P₂，其中 X 为已知值）。令人惊讶的是，一次性密码本是可塑的：给定密文 C₁ = P₁ ⊕ K，你可以定义 C₂ = C₁ ⊕ 1，它在同一密钥 K 下是 P₂ = P₁ ⊕ 1 的有效密文。糟糕，我们的完美密码就这样了。

接下来，我将在不同攻击模型的背景下讨论这些安全目标。

## 安全概念

安全目标只有与攻击模型结合时才有用。惯例是用 GOAL-MODEL 来书写安全概念。例如，IND-CPA 表示对选择明文攻击者的不可区分性，NM-CCA 表示对选择密文攻击者的非可塑性，等等。让我们从攻击者的安全目标开始。

## 语义安全与随机化加密：IND-CPA

最重要的安全概念是 IND-CPA，也称为语义安全。它体现了直觉，即只要密钥保密，密文就不应泄露关于明文的任何信息。要实现 IND-CPA 安全，加密在对同一明文调用两次时必须返回不同的密文；否则，攻击者可以从密文中识别出重复的明文，这与密文不应透露任何信息的定义相矛盾。但请注意，即使是 IND-CPA 安全的方案也不可避免地会泄露明文的一个信息：其长度，或至少近似长度。这就是为什么加密压缩数据通常不是一个好主意，因为压缩数据的大小可以揭示原始数据的信息。

实现 IND-CPA 安全的一种方法是使用随机化加密。正如名称所示，它使加密过程随机化，并在对同一明文加密两次时返回不同的密文。加密随后可表示为 C = E(K, R, P)，其中 R 是新鲜的随机位。然而解密仍然是确定性的，因为给定 D(K, R, C)，你总应得到 P，而与 R 的值无关。

如果加密不是随机的呢？在上一页的“安全目标”部分中，攻击者选择两个明文 P1 和 P2，并接收其中一个的密文，但不知道密文对应哪个明文。也就是说，他们得到 Ci = E(K, Pi) 并必须猜测 i 是 1 还是 2。在 CPA 模型中，攻击者可以执行加密查询来确定 C1 = E(K, P1) 和 C2 = E(K, P2)。如果加密不是随机的，只需查看 Ci 是否等于 C1 或 C2 即可确定哪个明文被加密，从而赢得 IND 游戏。因此，随机化是 IND-CPA 概念的关键。

如果你没有伪随机生成器，仍可通过使用需要 nonce（或仅使用一次的数字）的加密方案来实现 IND-CPA 安全，而不是使用随机、不可预测的值。nonce 必须对每次新的加密调用都是唯一的。简单的计数器（1, 2, 3, . . ）就能解决问题。例如，AES-CTR（CTR 模式下使用的 AES 分组密码）如果其附加输入 nonce 是唯一的，则是 IND-CPA 的。与仅将随机性作为加密过程一部分的某些随机化加密方案不同，使用 nonce 的算法解密时需要 nonce。

> 注意 使用随机化加密时，密文必须比明文稍长，以便每个明文有多个可能的密文。例如，如果每个明文有 2^64 个可能的密文，则密文必须比明文长至少 64 位。

## 语义安全加密

语义安全密码的最简单构造之一使用确定性随机比特生成器（DRBG），该算法根据某个秘密值返回看似随机的比特：

E(K, R, P) = (DRBG(K || R) ⊕ P, R)

这里，R 是为每次新加密随机选择的字符串，并与密钥一起提供给 DRBG（K || R 表示由 K 后跟 R 组成的字符串）。这种方法让人想起一次性密码本：我们不是选择与消息长度相同的随机密钥，而是利用随机比特生成器获得看似随机的字符串。

在假设 DRBG 产生随机比特的情况下，该密码是 IND-CPA 安全的证明很简单。证明采用归谬法：如果你可以区分密文和随机字符串，这意味着你可以区分 DRBG(K || R) ⊕ P 和随机，那么这意味着你可以区分 DRBG(K || R) 和随机。请记住，CPA 模型允许你获取针对选定 P 值的密文，因此你可以对 DRBG(K || R) ⊕ P 执行 XOR P 得到 DRBG(K || R)。但现在我们得到矛盾，因为我们开始


假设 **DRBG**(K || R) 无法与随机数区分，从而产生随机字符串。因此我们得出结论，密文无法与随机字符串区分，所以该密码是安全的。

**注意** *作为练习，尝试确定密码 **E**(K, R, P) = (**DRBG**(K || R) ⊕ P, R) 还满足哪些其他安全概念。它是 NM-CPA 吗？是 IND-CCA 吗？你将在下一节找到答案。*

## 安全概念比较

你已经了解到，CPA 和 CCA 等攻击模型与 NM 和 IND 等安全目标相结合，构建了 NM-CPA、NM-CCA、IND-CPA 和 IND-CCA 等安全概念。这些概念之间有何关联？我们能否证明满足概念 X 就意味着满足概念 Y？

有些关系是显而易见的：IND-CCA 蕴含 IND-CPA，NM-CCA 也蕴含 NM-CPA，因为 CPA 攻击者能做的任何事，CCA 攻击者同样也能做到。也就是说，如果你无法通过执行选择密文和选择明文查询来攻破一个密码，那么你也不可能仅通过执行选择明文查询来攻破它。

一个不那么明显的关系是，IND-CPA 并不蕴含 NM-CPA。要理解这一点，请注意之前的 IND-CPA 构造 (**DRBG**(K, R) ⊕ P, R) 并非 NM-CPA：给定一个密文 (X, R)，你可以创建密文 (X ⊕ 1, R)，它是 P ⊕ 1 的有效密文，从而与不可延展性的概念相矛盾。

但相反的关系是成立的：NM-CPA 蕴含 IND-CPA。直觉上，IND-CPA 加密就像把物品放进一个袋子：你看不到它们，但可以通过上下摇晃袋子来重新排列它们在袋中的位置。NM-CPA 更像是一个保险箱：一旦放进去，你就无法与你放入的东西进行交互。这个类比不适用于 IND-CCA 和 NM-CCA，它们是等价的概念，彼此相互蕴含。关于其证明，这里我就不详细展开了，因为它相当技术化。

## 两类加密应用

加密应用主要有两种类型。*传输中加密*（In-transit encryption）保护从一台机器发送到另一台机器的数据：数据在发送前被加密，接收后被解密，例如与电子商务网站的安全连接。*静态数据加密*（At-rest encryption）保护存储在信息系统上的数据。数据在写入内存前被加密，在读取前被解密。例子包括笔记本电脑上的磁盘加密系统，以及云虚拟实例的虚拟机加密。我们见过的安全概念适用于这两种应用，但应考虑的正确概念可能取决于具体应用。

## 非对称加密

到目前为止，我们只考虑了对称加密，即两方共享一个密钥。在*非对称加密*（Asymmetric encryption）中，有两个密钥：一个用于加密，另一个用于解密。加密密钥称为*公钥*（public key），通常被认为对任何想给你发送加密消息的人都是公开可用的。然而，解密密钥必须保密，称为*私钥*（private key）。

公钥可以从私钥计算得出，但私钥不能从公钥计算得出。换句话说，在一个方向上容易计算，但在另一个方向上则不然——这就是*公钥密码学*（public-key cryptography）的核心要点，其函数在一个方向上易于计算，但在反方向上几乎不可能求逆。

非对称加密的攻击模型和安全目标与对称加密大致相同，除了因为加密密钥是公开的，任何攻击者都可以使用公钥进行加密来发起加密查询。因此，非对称加密的默认模型是选择明文攻击者。

对称加密和非对称加密是两种主要的加密类型，它们通常被结合起来以构建安全的通信系统。它们也构成了更复杂方案的基础，你将在下文中看到。

## 当密码不止于加密时

基本加密将明文转换为密文，并将密文转换为明文，除了安全性之外没有其他要求。然而，一些应用通常需要更多，无论是额外的安全特性还是功能性。这就是密码学家创建对称和非对称加密变体的原因。有些变体已被很好地理解、高效且广泛部署，而另一些则是实验性的，很少使用，并且性能不佳。

## 认证加密

*认证加密*（Authenticated encryption, AE）是一种对称加密，除了返回密文外，还返回一个*认证标签*（authentication tag）。图 1-4 展示了认证加密集 **AE**(K, P) = (C, T)，其中认证标签 T 是一个短字符串，没有密钥就无法猜测。解密过程接收 K、C 和 T，并仅当验证 T 是该明文-密文对的有效标签时才返回明文 P；否则，它将中止并返回某种错误。

![](img/ace4de942d037de8ea5835bc9fbe57cd_46_0.png)

该标签确保了消息的*完整性*（integrity），并作为证据表明收到的密文与最初由知道密钥 *K* 的合法方发送的密文完全相同。当 *K* 仅与另一方共享时，该标签还保证消息是由该方发送的；也就是说，它隐式地*认证*（authenticates）预期的发送者确实是消息的实际创建者。

> > **注意**  
> > 我在这里使用“创建者”而不是“发送者”，因为窃听者可以记录方 A 发送给方 B 的一些 (C, T) 对，然后再次将它们发送给 B，伪装成 A。这被称为重放攻击，并且可以防止——例如，通过在消息中包含一个计数器数。当消息被解密时，其计数器 *i* 增加一：*i* + 1。这样，人们可以检查计数器以查看消息是否被发送了两次，这表示攻击者正试图通过重新发送消息来进行重放攻击。这也使得能够检测丢失的消息。

*带关联数据的认证加密*（Authenticated encryption with associated data, AEAD）是认证加密的一种扩展，它接收一些明文和未加密的数据，并使用它来生成认证标签 **AEAD**(*K*, P, A) = (C, A, T)。AEAD 的一个典型应用是保护协议的报文，其中包含明文头部和加密的有效载荷。在这种情况下，至少一些头部数据必须保持明文；例如，目标地址需要是明文的，以便路由网络数据包。

有关认证加密的更多信息，请跳转到第 8 章。

## 保形加密

基本的密码接收比特并返回比特；它不关心比特是代表文本、图像还是 PDF 文档。密文又可以被编码为原始字节、十六进制字符、base64 和其他格式。但是，如果你需要密文具有与明文相同的格式怎么办？例如，有时数据库系统只能以规定格式记录数据，这就提出了这样的要求。

*保形加密*（Format-preserving encryption, FPE）解决了这个问题。它可以创建与明文具有相同格式的密文。例如，FPE 可以将 IP 地址加密为 IP 地址（如图 1-5 所示）、邮政编码加密为邮政编码、信用卡号加密为具有有效校验和的信用卡号等等。

![](img/ace4de942d037de8ea5835bc9fbe57cd_48_0.png)

图 1-6：可调加密

在磁盘加密中，TE 加密存储设备（如硬盘或固态驱动器）的内容。（不能使用随机化加密，因为它会增加数据的大小，这对于存储介质上的文件来说是不可接受的。）为了使加密不可预测，TE 使用一个取决于所加密数据位置的调整值，这通常是扇区号或块索引。

## 事情可能出错的方式

加密算法或其实现可能在许多方面无法保护机密性。这可能是由于未能满足安全要求（例如“达到 IND-CPA 安全”）或未能设定符合现实的要求（当你只针对 IND-CPA 安全，而攻击者实际上可以执行选择密文查询时）。唉，许多工程师甚至不考虑密码安全要求，只想“安全”，却不理解这实际上意味着什么。这通常是灾难的根源。让我们看两个例子。

## 弱密码

我们的第一个例子涉及可以使用密码分析技术攻击的密码，如同 2G 移动通信标准中发生的情况。2G 手机的加密使用了称为 A5/1 的密码，结果证明它比预期的要弱，使得任何拥有相应技能和工具的人都能拦截通话。电信运营商不得不寻找变通方法来防止这种攻击。

> 注意 2G 标准还定义了 A5/2，一种用于欧盟和美国以外地区的密码。A5/2 被故意设计得更弱，以防止在所有地方都使用强加密。

话虽如此，攻击 A5/1 并非易事，研究人员花了超过 10 年的时间才提出有效的密码分析方法。此外，这种攻击是一种时间-内存权衡（TMTO）方法，这类方法首先需要运行数天或数周的计算来构建大型查找表，然后在实际攻击中使用这些表。对于 A5/1，预计算表是


of the order of 1TB. Later standards for mobile encryption, such as 3G and LTE, specify stronger ciphers, but that doesn’t mean their encryption won’t be compromised; it simply means that the encryption won’t be compromised by breaking the symmetric cipher that’s part of the system.

### Wrong Model

The next example concerns an invalid attack model that overlooked some side channels.

下一个示例涉及一个忽略了某些侧信道的无效攻击模型。

Many communication protocols that use encryption ensure that they use ciphers considered secure in the CPA or CCA model. However, some attacks don’t require encryption queries, as in the CPA model, nor do they require decryption queries, as in the CCA model. They simply need validity queries to tell whether a ciphertext is valid, and these queries are usually sent to the system responsible for decrypting ciphertexts. Padding oracle attacks are an example of such attacks, wherein an attacker learns whether a ciphertext conforms to the required format.

许多使用加密的通信协议确保它们使用在 CPA 或 CCA 模型中被认为安全的密码。然而，一些攻击不需要像 CPA 模型中的加密查询，也不像 CCA 模型中的解密查询。它们只需要有效性查询来判断密文是否有效，而这些查询通常发送到负责解密密文的系统。填充谍者攻击就是此类攻击的一个例子，其中攻击者会获知密文是否符合所需格式。

Specifically, in the case of padding oracle attacks, a ciphertext is valid only if its plaintext has the proper padding, a sequence of bytes appended to the plaintext to simplify encryption. Decryption fails if the padding is incorrect, and attackers can often detect decryption failures and attempt to exploit them. For example, the presence of the Java exception `javax.crypto.BadPaddingException` indicates that an incorrect padding was observed.

具体来说，在填充谍者攻击的情况下，密文只有在其明文具有正确的填充时才有效，填充是附加到明文以简化加密的一串字节。如果填充不正确，解密就会失败，而攻击者通常可以检测到解密失败并尝试利用它们。例如，Java 异常 `javax.crypto.BadPaddingException` 的出现表明观察到了不正确的填充。

In 2010, researchers found padding oracle attacks in several web application servers. The validity queries consisted of sending a ciphertext to some system and observing whether it threw an error. Thanks to these queries, they could decrypt otherwise-secure ciphertexts without knowing the key.

2010 年，研究人员在多个 Web 应用服务器中发现了填充谍者攻击。有效性查询包括向某个系统发送密文并观察它是否抛出错误。凭借这些查询，他们能够在不知道密钥的情况下解密原本安全的密文。

Cryptographers often overlook attacks like padding oracle attacks because they usually depend on an application’s behavior and on how users can interact with the application. But if you don’t anticipate such attacks and fail to include them in your model when designing and deploying cryptography, you may have some nasty surprises.

密码学家经常忽视像填充谍者攻击这样的攻击，因为它们通常取决于应用程序的行为以及用户如何与应用程序交互。但如果你在设计和部署密码学时没有预见到此类攻击并且未能将它们纳入你的模型，你可能会遇到一些不愉快的惊喜。

### Further Reading

We discuss encryption and its various forms in more detail throughout this book, especially how modern, secure ciphers work. Still, I can’t cover everything and have passed over many fascinating topics. For example, to learn the theoretical foundations of encryption and gain a deeper understanding of the notion of indistinguishability, read the 1982 paper that introduced the idea of semantic security, “Probabilistic Encryption and How to Play Mental Poker Keeping Secret All Partial Information” by Goldwasser and Micali. If you’re interested in physical attacks and cryptographic hardware, the proceedings of the Cryptographic Hardware and Embedded Systems (CHES) conference are the main reference.

我们在本书中更详细地讨论了加密及其各种形式，尤其是现代、安全密码的工作原理。尽管如此，我无法涵盖所有内容，并且忽略了许多引人入胜的话题。例如，要学习加密的理论基础并更深入地理解不可区分性的概念，请阅读引入语义安全思想的 1982 年论文《Probabilistic Encryption and How to Play Mental Poker Keeping Secret All Partial Information》，作者为 Goldwasser 和 Micali。如果你对物理攻击和密码硬件感兴趣，密码硬件与嵌入式系统（CHES）会议的论文集是主要参考资料。

There are also many more types of encryption than those presented in this chapter, including attribute-based encryption, broadcast encryption, functional encryption, identity-based encryption, message-locked encryption, and proxy reencryption, to cite but a few. For the latest research on those topics, check https://eprint.iacr.org, an electronic archive of cryptography research papers.

本章介绍的加密类型远不止这些，包括基于属性的加密、广播加密、功能加密、基于身份的加密、消息锁定加密和代理重加密，仅举几例。有关这些主题的最新研究，请查看 https://eprint.iacr.org，这是一个密码学研究论文的电子档案库。

### 2 RANDOMNESS

![](img/ace4de942d037de8ea5835bc9fbe57cd_52_0.png)

Randomness is found everywhere in cryptography: in the generation of secret keys, in encryption schemes, and even in the attacks on cryptosystems. Without randomness, cryptography would be impossible because all operations would become predictable and therefore insecure.

随机性无处不在于密码学中：在密钥生成中、在加密方案中，甚至在对密码系统的攻击中。没有随机性，密码学就不可能，因为所有操作都会变得可预测，因此不安全。

This chapter introduces the concept of randomness in the context of cryptography and its applications. We discuss pseudorandom number generators and how operating systems can produce reliable randomness, and we conclude with real examples showing how flawed randomness can impact security.

本章介绍了随机性在密码学背景下的概念及其应用。我们讨论伪随机数生成器以及操作系统如何产生可靠的随机性，并以真实示例作为结尾，展示有缺陷的随机性如何影响安全性。

### Random or Nonrandom?

You’ve probably heard the phrase *random bits* before, but strictly speaking, there is no such thing as a series of random bits. What *is* random is the *algorithm*, or process, that produces a series of random bits; therefore, when we say “random bits,” we actually mean randomly generated bits.

你可能以前听说过 *random bits* 这个短语，但严格来说，并不存在随机比特序列。真正随机的，是产生随机比特序列的 *algorithm*，或 *process*；因此，当我们说“随机比特”时，我们实际上指的是随机生成的比特。

What do random bits look like? For example, the 8-bit string 11010110 might look more random than 00000000, although both have the same chance of being generated (namely, 1/256). The value 11010110 looks more random than 00000000 because it has the signs typical of a randomly generated value. That is, 11010110 has no obvious pattern.

随机比特看起来是什么样子的？例如，8 位字符串 11010110 可能看起来比 00000000 更随机，尽管两者被生成的几率相同（即 1/256）。值 11010110 看起来比 00000000 更随机，因为它具有随机生成值典型的特征。也就是说，11010110 没有明显的模式。

When we see the string 11010110, our brain registers that it has 3 zeros and 5 ones, just like 55 other 8-bit strings (11111000, 11110100, 11110010, and so on), but only one 8-bit string has 8 zeros. Because the pattern 3-zeros-and-5-ones is more likely to occur than the pattern 8-zeros, we identify 11010110 as random and 00000000 as nonrandom, even if they’re not.

当我们看到字符串 11010110 时，我们的大脑会识别出它有 3 个零和 5 个一，就像另外 55 个 8 位字符串一样（11111000、11110100、11110010 等），但只有一个 8 位字符串有 8 个零。因为 3-零-5-一 的模式比 8-零 的模式更可能出现，我们将 11010110 识别为随机，而将 00000000 识别为非随机，即使它们并非如此。

This example illustrates two types of errors people often make when identifying randomness:

此示例说明了人们在识别随机性时经常犯的两种错误：

- **Mistaking nonrandomness for randomness** Thinking that an object was randomly generated simply because it *looks random*
- **Mistaking randomness for nonrandomness** Thinking that patterns appearing by chance are there for a reason other than chance

- **将非随机性误认为随机性** 仅仅因为它 *看起来随机* 就认为一个对象是随机生成的
- **将随机性误认为非随机性** 认为偶然出现的模式是出于除偶然之外的其他原因

The saying “it happened by chance” reflects the property that from a complex system (in this case, our universe that obeys the laws of physics, deterministic at the macroscopic level and truly random at the subatomic, quantum level) can emerge specific patterns, such as the string 00000000. By the law of large numbers, if many events occur, some won’t look random—such as a series of sequential numbers in a lottery draw. Many pseudosciences and belief systems are in fact cases of mistaking randomness for nonrandomness.

“它纯属偶然”这一说法反映了这样一个属性：从一个复杂系统（在本例中，是遵循物理定律的宇宙，在宏观层面上是确定性的，在亚原子、量子层面上是真正随机的）可以产生特定的模式，例如字符串 00000000。根据大数定律，如果发生许多事件，其中一些看起来就不随机——例如彩票抽奖中出现一系列顺序数字。许多伪科学和信仰体系实际上是将随机性误认为非随机性的案例。

### Randomness as a Probability Distribution

Any randomized process is characterized by a *probability distribution*, which gives all there is to know about the randomness of the process. A probability distribution, or simply *distribution*, lists the outcomes of a randomized process where each outcome is assigned a probability.

任何随机过程都由 *probability distribution* 刻画，它提供了关于该过程随机性的所有信息。概率分布，或简称为 *distribution*，列出了随机过程的结果，其中每个结果都被分配一个概率。

A *probability* measures the likelihood of an event occurring. It’s expressed as a real number between 0 and 1 where a probability of 0 means impossible and a probability of 1 means certain. For example, when tossing a two-sided coin, each side has a 1/2 (or 0.5) probability of landing face up, and the probability of a coin landing on its edge has a probability close to 0.

*probability* 衡量事件发生的可能性。它表示为 0 到 1 之间的实数，其中概率为 0 表示不可能，概率为 1 表示必然。例如，在抛掷双面硬币时，每一面朝上的概率为 1/2（或 0.5），而硬币立在边缘的概率接近 0。

A probability distribution must include all possible outcomes such that the sum of all probabilities is 1. Specifically, if there are *N* possible events, there are *N* probabilities p₁, p₂, . . . , p_N with p₁ + p₂ + . . . + p_N = 1. In the case of the coin toss, the distribution is 1/2 for heads and 1/2 for tails. The sum of both probabilities is equal to 1/2 + 1/2 = 1, because the coin will fall on one of its two faces.

概率分布必须包含所有可能的结果，使得所有概率之和为 1。具体来说，如果有 *N* 个可能事件，则有 *N* 个概率 p₁、p₂、……、p_N，其中 p₁ + p₂ + … + p_N = 1。在硬币抛掷的情况下，分布为正面 1/2，反面 1/2。两个概率之和等于 1/2 + 1/2 = 1，因为硬币会落在它的两个面之一上。

A *uniform distribution* occurs when all probabilities in the distribution are equal, meaning that all outcomes are equally likely to occur. If there are N events, then each event has probability 1/N. For example, if a 128-bit key is picked uniformly at random—that is, according to a uniform distribution—then each of the 2^128 possible keys should have a probability of 1/2^128.

当分布中的所有概率相等时，就会发生 *uniform distribution*，这意味着所有结果发生的可能性相等。如果有 N 个事件，则每个事件的概率为 1/N。例如，如果一个 128 位密钥是均匀随机选取的——即根据均匀分布——那么 2^128 个可能密钥中的每一个都应具有 1/2^128 的概率。

In contrast, when a distribution is *nonuniform*, probabilities aren’t all equal. A coin toss with a nonuniform distribution is said to be biased and may yield heads with probability 1/4 and tails with probability 3/4, for example.

相比之下，当分布为 *nonuniform* 时，概率并不全部相等。具有非均匀分布的硬币抛掷被称为有偏，例如可能正面概率为 1/4，反面概率为 3/4。

> **NOTE**
> *It’s possible to cheat with a loaded die, preventing the probabilities of each of the six faces to be 1/6; however, one can’t bias a coin. Coin tosses can be biased only if “the coin is allowed to bounce or be spun rather than simply flipped in the air,” as described in the article “You Can Load a Die but You Can’t Bias a Coin” (available at https://www.stat.berkeley.edu/~nolan/Papers/dice.pdf).*

> **NOTE**
> *可以用作弊骰子来作弊，防止六个面各自的概率为 1/6；然而，人们无法使硬币产生偏差。硬币抛掷只有在“the coin is allowed to bounce or be spun rather than simply flipped in the air”时才可能产生偏差，正如文章“You Can Load a Die but You Can’t Bias a Coin”（可在 https://www.stat.berkeley.edu/~nolan/Papers/dice.pdf 获取）中所描述的那样。*

### Entropy: A Measure of Uncertainty

*Entropy* is the measure of uncertainty, or disorder, in a system. The higher the entropy, the less certainty found in the result of a randomized process.

*Entropy* 是系统中不确定性或无序程度的度量。熵越高，随机过程结果的不确定性就越小。

We can compute the entropy of a probability distribution. If your distribution consists of probabilities p₁, p₂, . . . , p_N, then its entropy is the negative sum of all probabilities multiplied by their logarithm, as shown in this expression:

我们可以计算概率分布的熵。如果你的分布由概率 p₁、p₂、……、p_N 组成，那么它的熵是所有概率与其对数的乘积的负和，如下式所示：

-p₁ × log(p₁) - p₂ × log(p₂) - ... - p_N × log(p_N)

Here the function *log* is the *binary logarithm*, or logarithm in base two. Unlike the natural logarithm, the binary logarithm expresses the information in bits and yields integer values when probabilities are powers of two. For example, log(1/2) = -1, log(1/4) = -2, and more generally log(1/2^n) = -n. (We actually take the *negative sum* to end up with a positive number.) Random 128-bit keys produced using a uniform distribution therefore have the following entropy:

这里函数 *log* 是 *binary logarithm*，即以二为底的对数。与自然对数不同，二进制对数以比特表示信息，并且当概率为二的幂时产生整数值。例如，log(1/2) = -1，log(1/4) = -2，更一般地 log(1/2^n) = -n。（我们实际上取 *negative sum* 以得到正数。）因此，使用均匀分布产生的随机 128 位密钥具有以下熵：

2^128 × (-2^-128 × log(2^-128)) = -log(2^-128) = 128 bits

If you replace 128 with any integer n, the entropy of a uniformly distributed n-bit string will be n bits.

如果你用任意整数 n 替换 128，则均匀分布的 n 位字符串的熵将为 n 位。

Entropy is maximized when the distribution is uniform because a uniform distribution maximizes uncertainty: no outcome is more likely than the others. Therefore, n-bit values can’t have more than n bits of entropy.

当分布为均匀时，熵达到最大值，因为均匀分布最大化了不确定性：没有任何结果比其他结果更可能。因此，n 位值不能超过 n 位熵。




同理，当分布不均匀时，熵会更低。以抛硬币为例。公平抛掷的熵如下：

−(1/2) × log₂(1/2) − (1/2) × log₂(1/2) = 1/2 + 1/2 = 1 bit

如果硬币的一面出现正面的概率高于另一面会怎样？假设正面概率为 1/4，反面为 3/4。（记住所有概率之和应为 1。）这种有偏抛掷的熵为：

−(3/4) × log₂(3/4) − (1/4) × log₂(1/4) ≈ −(3/4) × (−0.415) − (1/4) × (−2) ≈ 0.81 bits

0.81 小于公平抛掷的 1 位熵这一事实告诉我们，硬币越有偏，分布越不均匀，熵越低。进一步举例，如果正面概率为 1/10，熵为 0.469；如果概率降至 1/100，熵降至 0.081。

> **NOTE**
>
> 熵也可以被视为信息量的度量。例如，公平抛硬币的结果恰好给你 1 位信息——正面或反面——并且你无法提前预测抛掷结果。在不公平的抛硬币情况下，你事先知道反面更可能出现，因此可以预测结果。不公平抛硬币的结果为你提供了以确定性预测结果所需的信息。

## 随机数生成器与伪随机数生成器

密码系统需要随机性来保证安全，因此需要一个提供随机性的组件。该组件的工作是在需要时返回随机位。要执行这种随机性生成，你需要两样东西：

- 熵源，由随机数生成器提供。
- 一种密码学算法，用于从熵源产生高质量的随机位。这在伪随机数生成器中可以找到。

同时使用随机数生成器和伪随机数生成器是使密码学实用且安全关键所在。让我们先简要了解随机数生成器的工作原理，然后再深入探讨伪随机数生成器。

随机性来自环境，后者是模拟的、混沌的、不确定的，因而不可预测。随机性无法仅由计算机算法生成。在密码学中，随机性通常来自随机数生成器（RNG），它们是软件或硬件组件，利用模拟世界中的熵在数字系统中产生不可预测的位。例如，RNG 可能会直接

为了生成伪随机位，PRNG 运行一个确定性随机位生成器（DRBG）算法，将熵池中的一些位扩展为更长的序列。顾名思义，DRBG 是确定性的，而非随机化的：给定一个输入，你总是会得到相同的输出。PRNG 确保其 DRBG 不会两次接收相同的输入，以便生成唯一的伪随机序列。

在其工作中，PRNG 执行三个操作：

- *init()* 初始化熵池和 PRNG 的内部状态
- *refresh(R)* 使用某些数据 *R* 更新熵池，通常来自 RNG
- *next(N)* 返回 *N* 个伪随机位并更新熵池

*init* 操作将 PRNG 重置为全新状态，将熵池重新初始化为某个默认值，并初始化 PRNG 用于执行 *refresh* 和 *next* 操作的任何变量或内存缓冲区。

*refresh* 操作通常称为 *reseeding*，其参数 *R* 称为 *seed*。当没有 RNG 可用时，种子可能是系统中的硬编码唯一值。*refresh* 操作通常由操作系统调用，而 *next* 通常由应用程序调用或请求。*next* 操作运行 DRBG 并修改熵池，以确保下一次调用会产生不同的伪随机位。

### 安全问题

让我们简要讨论 PRNG 如何解决高级安全问题。具体来说，PRNG 应保证 *backtracking resistance* 和 *prediction resistance*。*backtracking resistance*（也称为 *forward secrecy*）意味着之前生成的位无法恢复，而 *prediction resistance*（*backward secrecy*）意味着未来位应无法预测。

为了实现 *backtracking resistance*，PRNG 应确保通过 *refresh* 和 *next* 操作更新状态时执行的转换是不可逆的。这样，如果攻击者入侵系统并获得熵池的值，他们就无法确定池的先前值或先前生成的位。为了实现 *prediction resistance*，PRNG 应定期使用攻击者未知且难以猜测的 *R* 值调用 *refresh*，从而防止攻击者即使整个池被攻破也能确定熵池的未来值。（如果 *R* 值列表已知，你需要知道 *refresh* 和 *next* 调用的顺序才能重建池。）

### PRNG Fortuna

*Fortuna* 是一种用于 Windows 的 PRNG 构造，最初由 Niels Ferguson 和 Bruce Schneier 于 2003 年设计。Fortuna 取代了 *Yarrow*，后者是 John Kelsey 和 Bruce Schneier 于 1998 年设计的方案，长期用于 macOS 和 iOS 操作系统，并已被 Fortuna 取代。我不会在此提供 Fortuna 规范或展示如何实现它，但我会尝试解释其工作原理。你可以在 Ferguson、Schneier 和 Kohno 所著的《*Cryptography Engineering*》（Wiley，2010）第 9 章中找到 Fortuna 的完整描述。

Fortuna 的内部内存包括以下内容：

- 三十二个熵池，P₁、P₂、……、P₃₂，使得 Pᵢ 每 2ⁱ 次重新播种使用一次。
- 一个密钥 K 和一个计数器 C（均为 16 字节）。它们构成了 Fortuna DRBG 的内部状态。

简而言之，Fortuna 的工作方式如下：

- *init()* 将 K 和 C 设为零，并清空 32 个熵池 Pᵢ，其中 i = 1 … 32。
- *refresh(R)* 将数据 R 附加到其中一个熵池。系统选择用于产生 R 值的 RNG，并应定期调用 *refresh*。
- *next(N)* 使用一个或多个熵池的数据更新 K，其中熵池的选择主要取决于 K 已更新的次数。然后请求的 N 位是通过使用 K 作为密钥加密 C 产生的。如果加密 C 不够，Fortuna 会加密 C + 1，然后是 C + 2，依此类推，以获得足够的位。

尽管 Fortuna 的操作看起来相当简单，但正确实现它们却很困难。首先，你需要把算法的所有细节都弄对——如何选择熵池、*next* 中使用的密码类型、无熵接收时如何行为等等。虽然规范定义了大部分细节，但它们不包括用于检查实现是否正确的全面测试套件，这使得很难确保你的 Fortuna 实现会按预期行为。

即使 Fortuna 实现正确，出于除使用错误算法之外的其他原因仍可能出现安全故障。例如，如果 RNG 未能产生足够的随机位，Fortuna 可能不会注意到，结果 Fortuna 会产生质量较低的伪随机位，或者完全停止提供伪随机位。

Fortuna 实现固有的另一个风险在于相关 *seed files* 可能暴露给攻击者。Fortuna 种子文件中的数据用于在 RNG 立即可用时通过 *refresh* 调用向 Fortuna 提供熵——例如，系统重启后立即以及系统 RNG 记录任何不可预测事件之前。然而，如果相同的种子文件被使用两次，Fortuna 将两次产生相同的位序列。因此，种子文件应在用后擦除，以确保不会被重用。

最后，如果两个 Fortuna 实例处于相同状态，因为它们共享一个种子文件（意味着熵池中的数据相同，包括 C 和 K），那么 *next* 操作将在两个实例中返回相同的位。



## 密码学与非密码学 PRNG

存在密码学和非密码学 PRNG。非密码学 PRNG 的设计目的是为科学模拟或电子游戏等应用生成均匀分布。然而，你绝不应在密码学应用中使用非密码学 PRNG，因为它们不安全；它们只关心比特概率分布的质量，而不关心其可预测性。另一方面，密码学 PRNG 是不可预测的，因为它们还关心用于生成良好分布比特的底层操作的强度。

不幸的是，编程语言暴露的大多数 PRNG——例如 libc 的 rand 和 drand48、PHP 的 rand 和 mt_rand、Python 的 random 模块以及 Java 的 java.util.Random 类——都是非密码学的。默认使用非密码学 PRNG 是灾难的配方，因为它经常最终被用于密码学应用，因此在生成与密码学或安全应用相关的随机性时，请务必只使用密码学 PRNG。

## 一种流行的非密码学 PRNG：梅森旋转

梅森旋转器（MT）算法是一种非密码学 PRNG，在撰写本文时被用于 PHP、Python、R、Ruby 以及许多其他系统。它甚至（不幸地）被用于区块链钱包密钥生成器。MT 生成均匀分布且无统计偏差的随机比特，但它是可预测的：给定 MT 生成的几个比特，就能猜出接下来会出现的比特。

让我们深入了解是什么使梅森旋转器不安全。MT 算法比密码学 PRNG 简单得多：其内部状态是一个数组 S，由 624 个 32 位字组成。该数组最初设置为 S₁、S₂、. . .、S₆₂₄ 并根据以下方程演化为 S₂、. . .、S₆₂₅，然后是 S₃、. . .、S₆₂₆，依此类推：

Sₖ₊₆₂₄ = Sₖ₊₃₉₇ ⊕ A((Sₖ ∧ 0x80000000) ∨ (Sₖ₊₁ ∧ 0x7fffffff))

这里，⊕ 表示按位异或（C 语言中的 ^），∧ 表示按位与（C 中的 &），∨ 表示按位或（C 中的 |），而 A 是一个函数，它将某个 32 位字 x 变换为 (x >> 1)，如果 x 的最低有效位为 0，则变换为 (x >> 1) ⊕ 0x9908b0df，否则。

在这个方程中，S 的比特之间仅通过 XOR 交互。运算符 ∧ 和 ∨ 从不将 S 的 2 个比特组合在一起，而是将 S 的比特与常量 0x80000000 和 0x7fffffff 的比特组合。这样，S₆₂₅ 中的任何一位都可以表示为 S₃₉₈、S₁ 和 S₂ 比特的 XOR，而任何未来状态中的任何一位都可以表示为初始状态 S₁、. . .、S₆₂₄ 比特的 XOR 组合。（当你将例如 S₂₂₈₊₆₂₄ = S₈₅₂ 表示为 S₆₂₅、S₂₂₈ 和 S₂₂₉ 的函数时，你可以进一步用 S₃₉₈、S₁ 和 S₂ 的表达式替换 S₆₂₅。）

因为初始状态恰好有 624 × 32 = 19,968 个比特（或 624 个 32 位字），任何输出比特都可以用最多 19,969 项的方程表示（19,968 个比特加上一个常量比特）。这大约是 2.5KB 的数据。反之亦然：初始状态的比特可以表示为输出比特的 XOR。

## 线性不安全性

我们称比特的 XOR 组合为 *线性组合*。例如，如果 X、Y 和 Z 是比特，则表达式 X ⊕ Y ⊕ Z 是一个线性组合，而 (X ∧ Y) ⊕ Z 不是，因为存在 AND（∧）。如果你在 X ⊕ Y ⊕ Z 中翻转 X 的一位，结果也会改变，而与 Y 和 Z 的值无关。相比之下，如果你在 (X ∧ Y) ⊕ Z 中翻转 X 的一位，结果仅在 Y 在同一位置的位为 1 时才会改变。关键在于，线性组合是可预测的，因为你不需要知道比特的值就能预测其值的变化如何影响结果。

相比之下，如果 MT 算法在密码学上是强健的，其方程将是 *非线性* 的，并且不仅涉及单个比特，还涉及比特的 AND 组合（*乘积*），例如 S₁S₁₅S₁₈₂ 或 S₁₇S₂₅₆S₂₅₇S₃₅₄S₄₉₈S₆₀₁。尽管这些比特的线性组合最多包含 624 个变量，非线性组合允许多达 2⁶²⁴ 个变量。写下这些方程的全部内容是不可能的，更不用说求解了。（请注意，2³⁰⁵ 是一个更小的数字，是可观测宇宙的估计信息容量。）

这里的关键在于，线性变换导致短方程（大小与变量数量相当），易于求解，而非线性变换产生指数级大小的方程，实际上无法求解。因此密码学家的任务就是设计 PRNG 算法，仅使用少量简单操作来模拟这种复杂的非线性变换。

> 注意
> 线性只是众多安全标准之一。虽然必要，但仅有非线性并不足以使 PRNG 在密码学上安全。

## 统计测试的无用性

TestU01、Diehard 或美国国家标准与技术研究院（NIST）测试套件等统计测试套件是测试伪随机比特质量的一种方法。这些测试取 PRNG 生成的伪随机比特样本（例如 1MB），计算比特中某些模式分布的统计数据，并将结果与均匀分布获得的典型结果进行比较。例如，一些测试统计 1 比特与 0 比特的数量，或 8 位模式的分布。但统计测试与密码学安全性大多无关，并且可以设计出在密码学上薄弱却能欺骗任何统计测试的 PRNG。

当你在随机生成的数据上运行统计测试时，通常会得到一堆统计指标。这些通常是 *p*-值，一种常见的统计指标。这些结果并不总是容易解释，因为它们很少像通过或失败那样简单。如果你的第一次结果似乎异常，不必担心：它们可能是偶然偏差的结果，或者你测试的样本太少。为了确保你看到的结果是正常的，将其与相同大小的某些可靠样本获得的结果进行比较——例如，使用以下命令通过 OpenSSL 工具包生成的一个样本：

```
$ openssl rand <number of bytes> -out <output file>
```

## 现实世界中的 PRNG

让我们把注意力转向现实世界中 PRNG 的实现。你会在大多数平台的操作系统（OS）中找到密码学 PRNG，从台式机和笔记本电脑到路由器和机顶盒等嵌入式系统，以及虚拟机、手机等等。其中大多数 PRNG 基于软件，但纯硬件的 PRNG 被操作系统上运行的应用使用，有时也被运行在密码学库或应用之上的其他 PRNG 使用。

接下来，我们将查看最广泛部署的 PRNG：用于 Linux、Android 以及许多其他基于 Unix 的系统；在 Windows 中；以及在最近的 Intel 微处理器中，其 PRNG 基于硬件。

### Linux 中的随机位

设备文件 `/dev/urandom` 是基于 Linux 内核的操作系统的密码学 PRNG 的用户空间接口。你通常会使用它来生成可靠的随机位。因为它是一个设备文件，所以你通过像读取文件一样读取它来从 `/dev/urandom` 请求随机位。例如，以下命令使用 `/dev/urandom` 将 10MB 的随机位写入文件：

```
$ dd if=/dev/urandom of=<output file> bs=1M count=10
```

#### 使用 /dev/urandom 的错误方式

你可以编写一个像清单 2-1 所示的 naive 且不安全的 C 程序来读取随机位并期望最好，但那会是个坏主意。

```c
int random_bytes_insecure(void *buf, size_t len)
{
    int fd = open("/dev/urandom", O_RDONLY);
    read(fd, buf, len);
    close(fd);
    return 0;
}
```

*清单 2-1：/dev/urandom 的不安全使用*

这段代码不安全；它甚至不检查 open() 和 read() 的返回值，这意味着你期望的随机缓冲区可能最终被填满零或保持不变。



## 更安全地使用 /dev/urandom

Listing 2-2 摘自 LibreSSL 库，展示了更安全地使用 /dev/urandom 的方法。

```c
int random_bytes_safer(void *buf, size_t len)
{
    struct stat st;
    size_t i;
    int fd, cnt, flags;
    int save_errno = errno;

start:
    flags = O_RDONLY;
#ifdef O_NOFOLLOW
    flags |= O_NOFOLLOW;
#endif
#ifdef O_CLOEXEC
    flags |= O_CLOEXEC;
#endif
    ① fd = open("/dev/urandom", flags, 0);
    if (fd == -1) {
        if (errno == EINTR)
            goto start;
        goto nodevrandom;
    }
#ifdef O_CLOEXEC
    fcntl(fd, F_SETFD, fcntl(fd, F_GETFD) | FD_CLOEXEC);
#endif

    /* Lightly verify that the device node looks sane. */
    if (fstat(fd, &st) == -1 || !S_ISCHR(st.st_mode)) {
        close(fd);
        goto nodevrandom;
    }
    if (ioctl(fd, RNDGETENTCNT, &cnt) == -1) {
        close(fd);
        goto nodevrandom;
    }
    for (i = 0; i < len; ) {
        size_t wanted = len - i;
        ② ssize_t ret = read(fd, (char *)buf + i, wanted);

        if (ret == -1) {
            if (errno == EAGAIN || errno == EINTR)
                continue;
            close(fd);
            goto nodevrandom;
        }
        i += ret;
    }
    close(fd);
    if (getdata(buf, len) == 0) {
        errno = save_errno;
        return 0; /* Satisfied */
    }
nodevrandom:
    errno = EIO;
    return -1;
}
```

Listing 2-2: 安全使用 /dev/urandom

与 Listing 2-1 不同，Listing 2-2 做了多项合理性检查。例如，将 open() ① 和 read() ② 的调用与 Listing 2-1 中的调用进行比较：更安全的代码会检查这些函数的返回值，并在失败时关闭文件描述符并返回 −1。

## /dev/urandom 与 /dev/random 之间的差异，在 2022 年之前

Linux 内核中在 drivers/char/random.c 中定义的 PRNG 在 2022 年（自内核版本 5.17 起）经历了重大变更。

首先，PRNG 的总体结构在旧版和新版中相似，基于从各种来源收集的熵（包括系统活动，如键盘、鼠标和磁盘访问），以及可视为大型数组的熵池，该池通过对从熵源收集的数据进行哈希填充。接下来，DRBG 负责生成读取 /dev/random 或 /dev/urandom 时或调用 getrandom() 系统调用时返回的伪随机数据流。

历史上，在内核版本 5.17 之前，Linux PRNG 的行为如下：与 /dev/urandom 不同，/dev/random 接口是阻塞的；如果内核估计 PRNG 的熵水平不足，则读取 /dev/random 时会停止返回字节（“阻塞”），直到内核估计有足够的熵。这不是一个好主意。一方面，熵估计器臭名昭著地不可靠，可能被攻击者欺骗（这也是 Fortuna 放弃 Yarrow 熵估计的原因之一）。此外，/dev/random 的估计熵很快就会耗尽，这可能导致拒绝服务情况，使被迫等待更多熵的应用程序变慢。总之，实际上，/dev/random 并没有比 /dev/urandom 好多少，反而制造了更多问题。

## /dev/urandom 与 /dev/random 之间的差异，自 2022 年起

在 2022 年（5.17 及以后）版本的 Linux 内核中，纳入了多项改进。首先，在创建池内容时，SHA-1 哈希函数已被 BLAKE2 取代。最大的变化是 /dev/random 和 /dev/urandom 相对行为的修改；甚至有人提出完全消除它们之间的差异。在撰写本文时，在大多数平台上，两个接口都会检测熵是否不足，但如果内核未能收集足够熵，/dev/urandom 将继续生成伪随机位，而 /dev/random 将阻塞。此外，内核的熵估计逻辑得到了极大改进：不再认为读取 PRNG 位时熵会减少（这在密码学上毫无意义），内核只是寻找已收集足够不确定性（即熵）的点——例如在系统启动时。

你可以在 /proc/sys/kernel/random/entropy_avail 文件中读取 Linux 系统的熵值。在旧版内核中，该值的最大值为 4,096 位，并且随着 PRNG 位的生成而减少。在新内核中，该值上限为 256 位，因此不再减少。

## Windows 中的 CryptGenRandom() 函数

在 Windows 中，系统 PRNG 的传统用户态接口是来自密码学应用程序编程接口（API）的 CryptGenRandom() 函数。最近的 Windows 版本用密码学 API：下一代（CNG）中的 BCryptGenRandom() 函数取代了 CryptGenRandom() 函数。Windows PRNG 从内核模式驱动程序 cng.sys（以前是 ksecdd.sys）获取熵，其熵收集器松散地基于 Fortuna。正如 Windows 中通常的情况一样，该过程很复杂。

Listing 2-3 显示了带有必要检查的 CryptGenRandom() 的典型 C++ 调用。

```
int random_bytes(unsigned char *out, size_t outlen)
{
    static HCRYPTPROV handle = 0; /* Only freed when the program ends */
    if(!handle) {
        if(!CryptAcquireContext(&handle, 0, 0, PROV_RSA_FULL,
            CRYPT_VERIFYCONTEXT | CRYPT_SILENT)) {
            return -1;
        }
    }
    while(outlen > 0) {
        const DWORD len = outlen > 1048576UL ? 1048576UL : outlen;
        if(!CryptGenRandom(handle, len, out)) {
            return -2;
        }
        out += len;
        outlen -= len;
    }
    return 0;
}
```

Listing 2-3: 使用 Windows CryptGenRandom() PRNG 接口

在调用实际 PRNG 之前，你需要声明一个密码服务提供者（HCRYPTPROV），然后使用 CryptAcquireContext() 获取密码上下文，这增加了出错的可能性。例如，发现 TrueCrypt 加密软件的最终版本以可能静默失败的方式调用 CryptAcquireContext()，导致随机性不佳且未通知用户。幸运的是，Windows 中更新且更简单的 BCryptGenRandom() 接口不需要代码显式打开句柄（或至少使其在没有句柄的情况下使用变得容易得多）。

## 基于硬件的 PRNG：Intel Secure Key

到目前为止我们只讨论了软件 PRNG，让我们看一个硬件的。Intel 数字随机数生成器，或 Intel Secure Key，是一种硬件 PRNG，于 2012 年在 Intel 的 Ivy Bridge 微架构中引入。它基于 NIST 的 SP 800-90 指南，采用 CTR_DRBG 模式的先进加密标准（AES）。Intel 的 PRNG 通过 RDRAND 汇编指令访问，该指令提供与操作系统无关的接口，原则上比软件 PRNG 更快。

而软件 PRNG 试图从不可预测的来源收集熵，Intel Secure Key 只有一个熵源，提供零和一形式的熵数据串行流。从硬件工程角度看，该熵源是一个带反馈的双差分闩锁——本质上是一个小型硬件电路，根据热噪声波动在两个状态（0 或 1）之间跳变，频率为 3 GHz。这通常相当可靠。

RDRAND 汇编指令以 16、32 或 64 位的寄存器作为参数，然后写入一个随机值。调用时，如果目标寄存器中的数据是有效的随机值，RDRAND 将进位标志设为 1，否则设为 0；如果你直接编写汇编代码，请务必检查 CF 标志。请注意，常见编译器中可用的 C 内联函数不会检查 CF 标志，但会返回其值。

> NOTE Intel 的 PRNG 框架还提供除 RDRAND 之外的汇编指令：RDSEED 汇编指令在经过一些调节或密码处理后，直接从熵源返回随机位。它的目的是能够为其他 PRNG 提供种子。

Intel Secure Key 仅部分公开文档，但它基于已知标准，并已被知名公司 Cryptography Research 审计（参见其题为“Analysis of Intel’s Ivy Bridge Digital Random Number Generator”的报告）。尽管如此，其安全性仍存在一些担忧，尤其是在 Edward Snowden 关于密码学后门的披露之后：PRNG 确实是破坏的完美目标。如果你担心但仍想使用 RDRAND 或 RDSEED，请将它们与其他熵源混合。这样做将防止在除最牵强附会的场景之外，对 Intel Secure Key 硬件或相关微代码中假设的后门的有效利用。

## 事情可能出错的方式

最后，我将介绍一些随机性故障的例子。可供选择的例子不计其数，但我选择了四个足够简单易懂且能说明不同问题的例子。



## 熵源不足

1996 年，Netscape 浏览器的 SSL 实现根据 Goldberg 和 Wagner 在 https://www.cs.berkeley.edu/~daw/papers/ddj-netscape.html 的页面上复制的第 2-4 节所示的伪代码计算 128 位 PRNG 种子。

```
global variable seed;

RNG_CreateContext()
    (seconds, microseconds) = time of day; /* Time elapsed since 1970 */
    pid = process ID; ppid = parent process ID;
    a = mklcpr(microseconds);
    ① b = mklcpr(pid + seconds + (ppid << 12));
    seed = MD5(a, b); /* Derivation of a 128-bit value using the hash MD5 */

mklcpr(x) /* Not cryptographically significant; shown for completeness */
    return ((0xDEECE66D * x + 0x2BB62DC) >> 1);

MD5() /* A very good standard mixing function, source omitted */
```

*第 2-4 节：Netscape 浏览器生成 128 位 PRNG 种子的伪代码*

这里的问题是 PID 和微秒是可猜测的值。假设你能猜出 seconds 的值，microseconds 只有 10⁶ 种可能值，因此熵为 log(10⁶)，约为 20 位。进程 ID（PID）和父进程 ID（PPID）是 15 位值，因此你会期望额外 15 + 15 = 30 位熵。但查看 b 的计算方式 ① 可见 3 位的重叠导致熵约为 15 + 12 = 27 位，总熵只有 47 位，而 128 位种子应具有 128 位熵。

## 启动时熵不足

2012 年，研究人员扫描互联网并从 TLS 证书和 SSH 主机收集公钥。他们发现少数系统具有相同的公钥，在某些情况下公钥非常相似（即具有共享素因子的 RSA 密钥）——简而言之，两个数 n = pq 和 n′ = p′q′，其中 p = p′，而通常在不同的模数中所有 p 和 q 都应不同。

结果发现，许多设备在首次启动时就生成了公钥，此时尚未收集到足够的熵，尽管使用了 otherwise 尚可的 PRNG（通常是 /dev/urandom）。不同系统的 PRNG 因具有相同的熵源（例如硬编码种子）而产生相同的随机位。

从高层次看，相同密钥的存在源于如下伪代码所示的密钥生成方案：

```
prng.seed(seed)
p = prng.generate_random_prime()
q = prng.generate_random_prime()
n = p*q
```

## 强随机性下的采样错误

下一个错误展示了即使是具有足够熵的强加密 PRNG 也可能产生有偏分布。聊天程序 Cryptocat 被设计用于提供安全通信。它使用了一个函数，试图创建均匀分布的十进制数字字符串——即 0 到 9 范围内的数字。然而，仅对随机字节取模 10 并不会产生均匀分布；当取 0 到 255 之间的所有数字并对其取模 10 时，0 到 9 的值并不会相等。

Cryptocat 为解决该问题并获得均匀分布做了如下处理：

```
Cryptocat.random = function() {
  var x, o = '';
  while (o.length < 16) {
    x = state.getBytes(1);
    if (x[0] <= 250) {
      o += x[0] % 10;
    }
  }
  return parseFloat('0.' + o)
}
```

而这几乎是完美的。通过只取 10 的倍数以下的数字并丢弃其他数字，你会期望 0 到 9 的数字均匀分布。不幸的是，if 条件中存在一次偏移错误。我把细节留给你作为练习。你应该会发现存在轻微的统计偏差，偏向索引 0（提示：<= 应该是 <）。

## 进一步阅读

我只是触及了密码学中随机性的表面。关于随机性的理论还有很多需要学习的内容，包括不同的熵概念、随机提取器，甚至随机化和去随机化在复杂性理论中的威力。要了解更多关于 PRNG 及其安全性，请阅读 Kelsey、Schneier、Wagner 和 Hall 于 1998 年发表的经典论文“Cryptanalytic Attacks on Pseudorandom Number Generators”。然后查看你喜欢的应用程序中 PRNG 的实现并尝试找出其弱点。（在线搜索“random generator bug”可以找到大量示例。）

不过我们还没有结束随机性的讨论。在本书中我们会多次遇到它，你会发现它帮助构建安全系统的诸多方式。

### 3

### 密码学安全

![](img/ace4de942d037de8ea5835bc9fbe57cd_70_0.png)

密码学安全定义与通用计算机安全适用的定义不同。软件安全与密码学安全之间的主要区别在于我们能够 *量化* 后者。与软件世界不同，在软件世界中我们通常说应用程序要么安全要么不安全，而在密码学世界中，通常可以计算破解密码算法所需的努力量。此外，软件安全侧重于防止攻击者滥用程序代码，而密码学安全的目标是使定义明确的问题无法解决。

密码学问题涉及数学概念，但不涉及复杂的数学——至少在本書中如此。本章将介绍这些安全概念中的一些内容，以及如何将它们应用于解决现实世界问题。

在以下各节中，我将讨论如何在理论上合理且在实践中相关的情况下量化密码安全。我讨论无条件与计算安全、位安全与完整攻击成本、可证明与启发式安全、对称与非对称密钥生成等概念。我以看似强大的密码学中失败的现实案例作为本章的结尾。

## 定义不可能

在第 1 章中，我描述了密码相对于攻击者能力和目标的安全性，并认为如果在攻击者已知能力下无法达到这些目标，则密码是安全的。但在这种情况下 *不可能* 究竟是什么意思？

两个概念定义了密码学中不可能的概念：无条件安全和计算安全。粗略地说，*无条件安全* 关乎理论上的不可能，而 *计算安全* 关乎实践上的不可能。无条件安全不量化安全性，因为它将密码视为要么安全要么不安全，没有中间地带；因此在实践中无用，尽管它在理论密码学中发挥重要作用。计算安全是衡量密码强度更相关、更实用的指标。

## 理论上的安全：无条件安全

无条件安全并非基于破解密码的难度，而是基于是否可以设想破解它。只有在给定无限计算时间和内存的情况下无法被破解，密码才是无条件安全的。即使对密码的成功攻击需要数万亿年，这种密码也是无条件 *不安全* 的。

例如，第 1 章中的一次性密码本是无条件安全的。回想一下，一次性密码本将明文 *P* 加密为密文 *C = P ⊕ K*，其中 *K* 是对每个明文唯一的随机比特串。该密码是无条件安全的，因为给定密文并有无限时间尝试所有可能的密钥 *K* 并计算相应的明文 *P*，你仍然无法识别正确的 *K*，因为可能的 *P*s 的数量与 *K*s 的数量一样多。

## 实践中的安全：计算安全

与无条件安全不同，计算安全认为如果密码在 *合理* 的时间内以及使用内存、硬件、预算和能源等合理资源无法被破解，则该密码是安全的。计算安全是量化密码或任何密码算法安全性的一种方式。

例如，考虑一个密码 **E**，你知道一个明文-密文对 (*P*, *C*)，但不知道计算 *C = E(K, P)* 的 128 位密钥 *K*。该密码不是无条件安全的，因为你可以在尝试 2¹²⁸ 个可能的 128 位 *K*s 后破解它，直到找到满足

E(K, P) = C。但实际上，即使以每秒测试 1000 亿个密钥的速度，也需要超过 100,000,000,000,000,000,000 年。换句话说，合理地说，这种密码在计算上是安全的，因为实际上不可能被破解。

我们可以将计算安全性用两个值来表达：

- t，即攻击者执行的运算次数的上限
- ε (epsilon)，即攻击成功概率的上限

我们随后说，如果攻击者执行的运算次数最多为 t——无论这些运算是什么——其成功概率不超过 ε，其中 ε 至少为 0 且最多为 1，则一种密码方案是 (t, ε)-安全的。计算安全性给出了破解密码算法的难度限制。

请注意 t 和 ε 只是限制：如果一种密码是 (t, ε)-安全的，那么执行少于 t 次运算的攻击者将不会成功（概率为 ε）。然而，这并不意味着执行恰好 t 次运算的攻击者会成功，并且它也没有提供必要的运算次数，该次数可能远大于 t。我们说 t 是必要计算量的下界，因为要破坏安全性至少需要 t 次运算。

如果我们确切知道破解一种密码所需的努力，我们说当存在一种以概率 ε 且恰好用 t 次运算破坏密码的攻击时，(t, ε)-安全性给出了一个紧界。

例如，考虑一个具有 128 位密钥的对称密码。理想情况下，该密码应对于 1 到 2^128 之间的任何 t 值都是 (t, t/2^128)-安全的。最佳攻击应为暴力破解（尝试所有密钥直到找到正确的那个）。任何更好的攻击都必须利用密码中的某种缺陷，因此我们努力创建暴力破解是最优攻击的密码。

给定陈述 (t, t/2^128)-安全，让我们检查三种可能攻击的成功概率：

- 在第一种情况下，t = 1，攻击者尝试一个密钥，成功的概率为 ε = 1/2^128。
- 在第二种情况下，t = 2^128，攻击者尝试全部 2^128 个密钥，其中一个会成功。因此概率 ε = 1。（如果攻击者尝试所有密钥，正确的那个必然在其中。）
- 在第三种情况下，攻击者仅尝试 t = 2^64 个密钥，成功的概率为 ε = 2^64 / 2^128 = 2^-64。当攻击者仅尝试所有密钥的一部分时，成功概率与尝试的密钥数量成正比。

我们可以得出结论，具有 n 位密钥的密码最多是 (t, t/2^n)-安全的，对于 1 到 2^n 之间的任何 t，因为无论密码多强，暴力攻击始终会成功。因此密钥必须足够长，才能在实践中削弱暴力攻击。

假设我们有两个密码，每个都有 128 位密钥和 128 位安全性。我们必须分别评估每个密码 $2^{128}$ 次才能破解它，但第二个密码比第一个慢 100 倍。评估第二个密码 $2^{128}$ 次所需的时间与 $100 \times 2^{128} \approx 2^{134.64}$ 次对第一个密码的评估相同。如果我们以第一个快速密码为基准，那么破解较慢的那个需要 $2^{134.64}$ 次运算。如果我们以第二个慢速密码为基准，则只需要 $2^{128}$ 次运算。我们是否应该说第二个密码比第一个更强？原则上，是的，但我们很少在常见密码之间看到如此百倍的性能差异。

运算定义不一致在比较攻击效率时带来了更多困难。一些攻击声称降低了密码的安全性，因为它们执行了 $2^{120}$ 次某种运算的评估，而不是 $2^{128}$ 次对密码的评估，但每种攻击类型的速度并未纳入分析。$2^{120}$ 次运算的攻击并不总是比 $2^{128}$ 次暴力攻击更快。

尽管如此，只要运算被合理定义——意味着与一次密码评估速度相当——位安全性仍然是一个有用的概念。毕竟，在现实生活中，判断一个安全级别是否足够，只需要一个数量级。

## 计算完整攻击成本

位安全性通过估计攻击成功所需的运算次数的数量级来表达对密码的最快攻击的成本。但其他因素也会影响攻击成本，在估计实际安全级别时必须将这些因素考虑在内。我将解释其中的四个主要因素：并行性、内存、预计算和目标数量。

### 并行性

首先要考虑的因素是计算并行性——即攻击的实现利用并行计算（例如多核系统）的能力。

例如，考虑以下两种各为 $2^{56}$ 次运算的攻击：

- 第一种攻击执行 $2^{56}$ 个 *顺序依赖的* 运算，计算 $x_{i+1}=f_i(x_i)$，其中对于某个固定的 $x_0$ 和不同的函数 $f_i$（i 从 1 到 $2^{56}$）。
- 第二种攻击执行 $2^{56}$ 个 *独立的* 运算，计算 $x_i=f_i(x)$，其中对于某个固定的 $x$ 和不同的函数 $f_i$（i 从 1 到 $2^{56}$）。它可以并行执行 $f_i(x)$ 计算，因为每个 $f_i(x)$ 都相互独立。

这两种攻击的区别在于，第二种攻击可以并行化，而第一种不可以。并行处理比顺序处理快几个数量级。例如，如果你有 $2^{16}=65,536$ 个处理器可用，你可以将并行攻击的工作负载划分为 $2^{16}$ 个独立任务，每个任务执行 $2^{56}/2^{16}=2^{40}$ 次运算。然而，第一种攻击无法从多个核心中受益，因为每次运算都依赖于前一次运算的结果。因此，即使它们执行的运算次数相同，并行攻击也会比顺序攻击快 65,536 倍。

> **NOTE**  
> *当有 N 个核心可用时攻击速度变得 N 倍快的算法是尴尬并行的；其执行时间相对于计算核心数量呈线性缩放。*

### 内存

确定攻击成本的第二个因素是内存。我们根据时间与空间的使用来评估密码分析攻击：它们随时间执行多少次运算，消耗多少内存或空间，如何使用所消耗的空间，以及可用内存的速度如何？不幸的是，位安全性只关注执行攻击所需的时间。

关于攻击使用空间的方式，重要的是要考虑攻击所需的内存查找次数、内存访问的速度（读取和写入可能不同）、访问数据的大小、访问模式（连续或随机内存地址），以及它如何在内存中结构化数据。例如，在 2021 年的 Intel Xeon 8380 Ice Lake 处理器上，访问寄存器需要 1 个时钟周期，访问 L1 缓存（48kB）需要 5 个周期，访问 L2 缓存（1.25MB）需要 14 个周期，访问 L3 缓存（60MB）需要 63.5 个周期，而访问 DRAM 最快与访问 L3 缓存相当，但通常要慢得多（确切延迟取决于多个因素）。

### 预计算

预计算运算只需执行一次，并且可以在后续攻击执行中重复使用。我们有时称预计算为攻击的 *离线阶段*。

考虑时间-内存权衡攻击，其中攻击者执行一次巨大的计算，生成大型查找表，我们随后存储并重复使用这些表来执行实际攻击。例如，对 2G 移动加密的一种攻击花费了两个月时间构建 2TB 的表，攻击者随后用这些表在 2G 中破坏加密，并在几秒钟内恢复秘密会话密钥。

### 目标数量

最后，我们来看攻击的目标数量。目标越多，攻击面越大，攻击者就能越了解他们想要的密钥。

例如，考虑暴力密钥搜索：如果针对单个 *n* 位密钥，则需要 2ⁿ 次尝试才能确定性地找到正确的密钥。如果针对多个 *n* 位密钥——比如数量为 M——并且对于单个 P 你有 M 个不同的密文，其中 C = E(K, P) 对每个你想要的 M 个密钥（K）都成立，则找到每个密钥仍需要 2ⁿ 次尝试。但如果你是

只对 *M* 个密钥中的 *至少一个* 感兴趣而非全部时，平均需要 2^n / *M* 次尝试才能成功。例如，要破解 2^16 = 65,536 个目标密钥中的一个 128 位密钥，平均需要 2^128 / 2^16 = 2^112 次密码评估。也就是说，随着目标数量的增加，攻击的成本（和速度）会下降。

## 选择和评估安全等级

选择安全等级通常需要在大多数标准加密算法和实现中可用的 128 位和 256 位安全等级之间进行选择。你会发现具有 64 位或 80 位安全性的方案，但这些通常不足以满足实际使用需求。

从高层次来看，128 位安全性意味着你需要执行大约 2^128 次操作才能破解该密码系统。为了让你了解这个数字的意义，请考虑宇宙大约有 2^88 纳秒的历史（每秒有十亿纳秒）。由于用今天的技术测试一个密钥至少需要一纳秒，攻击成功所需的时间将是宇宙年龄的数倍（精确地说是 2^40 倍）。

但并行化和多个目标不能显著减少成功攻击所需的时间吗？并非完全如此。假设你有兴趣破解一百万个目标中的任意一个，并且你有一百万个并行核心可用。这会将搜索时间从 2^128 降低到 (2^128 / 2^20) / 2^20 = 2^88，这相当于“仅”一个宇宙寿命。

在评估安全等级时，另一个需要考虑的事情是技术的演进。摩尔定律认为计算效率大约每两年翻一番。我们可以将此视为每两年损失 1 位安全性：如果今天 1,000 美元的预算可以让你在一小时内破解例如 40 位密钥，那么根据摩尔定律，两年后你可以用同样的 1,000 美元预算在一小时内破解 41 位密钥（我在简化）。由此我们可以推断，根据摩尔定律，与今天相比，80 年后我们的安全性将减少 40 位。换句话说，80 年后执行 2^128 次操作可能与今天执行 2^88 次操作的成本相同。考虑到并行化和多个目标，我们的计算量降至 2^48 纳秒，大约三天。但这种外推高度不准确，因为摩尔定律不会也不可能以这种方式扩展。尽管如此，你明白了这个概念：今天看起来不可行的事情在百年后可能变得现实。

在某些情况下，低于 128 位的安全等级是合理的，例如当你只需要短期安全性，并且实施更高安全等级的成本会负面影响系统的成本或可用性时。一个例子是付费电视系统，其中加密密钥为 48 位或 64 位。这听起来低得离谱，但足够了，因为密钥每 5 秒或 10 秒刷新一次。

尽管如此，为了确保长期安全，你应该选择 256 位安全性或稍低一些。即使在最坏的情况下——量子计算机的存在（参见第 14 章）——在可预见的未来，我们也不太可能破解一个 256 位安全的方案。超过 256 位的安全性在实践中是不必要的，除非作为营销手段。

> 正如密码学家 John Kelsey 曾经说过：“80 位和 128 位密钥搜索之间的差异就像火星任务和半人马座阿尔法任务之间的差异。 就我所见，就实际的暴力攻击而言，192 位和 256 位密钥之间没有有意义的差异；不可能就是不可能。”

## 实现安全

一旦你选择了安全等级，就很重要保证你的密码方案能够坚持该等级。换句话说，你想要 *信心*，而不仅仅是希望和不确定性，确保事情始终按计划工作。

在建立对加密算法安全性的信心时，你可以依赖数学证明，我们称之为 *可证明安全*，或依赖破解算法失败尝试的证据，我称之为 *启发式安全*（尽管有时也称为 *可能安全*）。这两种方法互为补充，而且没有哪一种更好，正如你将看到的那样。

## 可证明安全

可证明安全是关于证明破解你的密码方案至少与解决另一个已知困难的问题一样困难。这样的 *安全证明* 保证只要困难问题仍然困难，密码就保持安全。这种证明称为 *归约*，来源于计算复杂性理论领域。我们说问题 X 可以归约为破解某个密码，如果破解密码的任何方法也能产生解决 X 问题的方法。这样的归约保证只要问题 X 困难，密码就是安全的。

安全证明有两种类型，取决于你使用的 presumed 困难问题的类型：相对于数学问题的证明和相对于密码学问题的证明。

### 相对于数学问题的证明

许多安全证明（例如公钥密码的证明）表明破解密码方案至少与解决某个困难的数学问题一样困难。我们说的是我们知道解存在并且一旦知道就很容易验证，但计算上很难找到的问题。

> **注意** *似乎困难的数学问题实际上是困难的，并没有真正的证明。事实上，证明特定类别问题的这一点是计算复杂性理论领域最伟大的挑战之一。我在撰写本文时，克雷数学研究所为任何能够证明这一点的人提供 100 万美元的悬赏。我将在第 9 章更详细地讨论这个问题。*

例如，考虑解决 *分解问题* 的挑战，这是密码学中最著名的数学问题：给定一个你知道是两个素数乘积的数（*n* = *pq*），找到这些素数。例如，如果 *n* = 15，答案是 3 和 5。对于小数字来说很容易，但随着数字大小的增长，其难度呈指数级增加。例如，如果一个数 *n* 长 3,000 位（约 900 位十进制数字）或更长，分解被认为在实践中不可行。

Rivest–Shamir–Adleman（RSA）是最著名的依赖分解问题的密码方案。RSA 通过计算 *C* = *P*^e mod *n* 来加密明文 *P*，将其视为一个大数，其中数字 *e* 和 *n* = *pq* 是公钥。解密通过计算 *P* = *C*^d mod *n* 从密文恢复明文，其中 *d* 是与 *e* 和 *n* 关联的私钥。如果我们能分解 *n*，那么我们就能破解 RSA（通过从公钥恢复私钥），并且如果我们能获得私钥，那么我们就能分解 *n*（例如，参见文章 *https://eprint.iacr.org/2004/208*）。换句话说，恢复 RSA 私钥和分解 *n* 是等价的困难问题。这就是我们在可证明安全中寻找的那种归约。然而，恢复 RSA 明文与分解 *n* 一样困难并没有保证，因为明文的知识并不会揭示私钥。

### 相对于另一个密码问题的证明

与其将密码方案与数学问题进行比较，你可以将其与另一个密码方案进行比较，并证明只有在能够破解第一个方案的情况下才能破解第二个方案。对称密码的安全证明通常遵循这种方法。

例如，如果你只有单一的置换算法，那么你可以通过将置换的调用与各种类型的输入结合起来构建对称密码、随机比特生成器以及其他密码对象，如哈希函数（正如你在第 6 章中看到的那样）。证明随后表明，如果置换是安全的，则新创建的方案是安全的。换句话说，我们知道新创建的算法 *不比* 原始算法 *弱*。此类证明通常通过在给定对较大对象的攻击的情况下，对较小组件进行攻击来工作——即通过展示归约。

在证明一个密码算法不比另一个弱时，主要的好处是攻击面减少：不必同时分析核心算法和组合，你只需查看新密码的核心算法。具体来说，如果你编写一个使用新开发的置换和新组合的密码，你可以证明该组合与核心算法相比不会削弱安全性。因此，要破解该组合，你需要破解新的置换。

### 注意事项

密码学研究人员在安全证明上高度依赖，无论是相对于数学问题方案还是其他密码方案。但安全证明的存在并不能保证密码方案是完美的，也不是忽视实现更实际方面的借口。毕竟，正如密码学家 Lars Knudsen 曾经说过，“如果它是可证明安全的，它可能不是”，这意味着安全证明不应被视为安全性的绝对保证。更糟糕的是，“可证明安全”的方案可能导致安全失败的原因有很多。



一个问题在于“安全性证明”这一表述本身。在数学中，证明是对 *绝对真理* 的展示，但在密码学中，证明只是对 *相对真理* 的展示。例如，证明你的密码算法破解的难度与计算离散对数一样——给定 *g* 和 *g^x* mod *n* 求出数字 *x*——这保证了如果你的密码算法失效，那么一大批其他密码算法也会失效，而且如果最坏的情况发生，没人会责怪你。

另一个需要注意的是，人们通常只针对单一的安全概念来证明安全性。例如，你可能会证明恢复密码算法的私钥与分解问题一样困难。但如果你能在没有密钥的情况下从密文恢复明文，你就绕过了证明，而恢复密钥几乎无关紧要。

再者，证明并不总是正确的，破解一个算法可能比最初想象的更容易。

> **NOTE** *不幸的是，很少有研究人员仔细检查安全性证明，而这些证明通常跨越数十页，从而使质量控制复杂化。话虽如此，证明一个证明是错误的并不一定意味着该证明的目标完全错误；如果结果是正确的，可以通过纠正其错误来挽救证明。*

另一个重要考虑是，某些困难的数学问题有时比预期更容易解决。例如，某些弱参数使得破解 RSA 密码系统变得容易。或者数学问题在某些情况下很困难，但在平均情况下并非如此，这在参考问题新颖且尚未被充分理解时经常发生。1978 年 Merkle 和 Hellman 提出的背包加密方案后来就被格约简技术破解，这就是一个例子。

最后，尽管算法安全性的证明可能没问题，但算法的实现可能很薄弱。例如，攻击者可能会利用诸如功耗或执行时间之类的侧信道信息来了解算法的内部操作以便破解它，从而绕过证明。或者实现者可能会误用密码方案：如果算法过于复杂且配置选项太多，用户或开发者更有可能配置错误，这可能使算法完全不安全。

## Heuristic Security

可证明安全性是增强对密码方案信心的一种绝佳工具，但它并不适用于所有类型的算法。事实上，大多数对称密码都没有安全性证明。例如，我们每天都依赖 AES 通过手机、笔记本电脑和台式电脑安全通信，但 AES 并不是可证明安全的；没有证明表明破解它的难度与某个知名问题一样。AES 不能与数学问题或其他算法相关联，因为它本身就是那个难题。

在可证明安全性不适用的情况下，我们信任密码的唯一理由是因为许多技术高超的人尝试破解它却失败了。我们称之为 *启发式安全性*。

我们什么时候可以确定密码是安全的？我们永远无法确定，但当数百名经验丰富的密码分析员各自花费数百小时尝试破解它并发表了他们的研究成果时，我们可以相当确信算法不会被破解——通常是通过对密码的 *简化版本* 发起攻击（通常是操作更少、或 *轮数* 更少的版本，而轮数是密码为混合比特而迭代的一系列短操作）。

在分析新密码时，密码分析员首先尝试破解一轮，然后是两轮、三轮，或他们能破解的尽可能多的轮数。*安全裕度* 则是总轮数与成功攻击轮数之间的差值。经过多年的研究，如果密码的安全裕度仍然很高，我们就会确信它（很可能）是安全的。

## Generating Keys

如果你计划加密某些内容，你必须生成密钥，无论它们是临时的“会话密钥”（如浏览 HTTPS 网站时生成的密钥）还是长期公钥。回顾第 2 章，密钥是密码学安全的核心，应随机生成以使其不可预测且保密。

例如，当你浏览 HTTPS 网站时，你的浏览器会接收该网站的公钥并用它建立一个仅对当前会话有效的对称密钥，而该网站的公钥及其关联的私钥可能有效数年。因此，最好让攻击者难以找到。但生成密钥并不总是像倾倒足够多的伪随机位那样简单。我们可以通过以下三种方式之一生成密码学密钥：

- *随机*，使用为密钥生成算法提供输入的 PRNG
- 从 *密码*，使用基于密码的密钥派生函数（PBKDF），它将用户提供的密码转换为密钥
- 通过 *密钥协商协议*，即两方或多方之间的一系列消息交换，最终建立共享密钥

现在，我将解释最简单的方法：随机生成。

### Symmetric Keys

对称密钥是由两方共享的秘密密钥，且是最简单的生成方式。它们通常与所提供的安全级别长度相同：128 位密钥提供 128 位安全性，2¹²⁸ 种可能的密钥中任何一种都是有效的。

使用密码学 PRNG 生成 *n* 位对称密钥时，你只需向其请求 *n* 个伪随机位并将这些位用作密钥即可。

就这么简单。例如，你可以使用 OpenSSL 工具包通过倾倒伪随机字节来生成随机对称密钥，如以下命令所示：

```text
$ openssl rand -hex 16
65a4400ea649d282b855bd2e246812c6
```

你的结果当然会与我的不同。

### Asymmetric Keys

与对称密钥不同，非对称密钥通常比其提供的安全级别更长。但主要问题在于非对称密钥比对称密钥更难生成，因为你不能从 PRNG 中倾倒 *n* 位并就此了事。非对称密钥不仅仅是原始位序列。相反，它们代表特定类型的对象，例如具有特定属性的大数（在 RSA 中，是两个素数的乘积）。随机的位串值（因此是随机数）不太可能具有必要的属性，因此不会是有效的密钥。

要生成非对称密钥，你将伪随机位作为种子发送给 *密钥生成算法*。该算法以至少与预期安全级别一样长的种子值为输入，并据此构造私钥及其相应的公钥，确保两者都满足必要条件。例如，RSA 的一个简单密钥生成算法会生成一个数 *n = pq*，方法是使用算法生成两个长度大致相同的随机素数。该算法会挑选随机数直到其中一个恰好为素数，因此你还需要一个算法来测试某个数是否为素数。

为了避免手动实现密钥生成算法的负担，你可以使用 OpenSSL 生成一个 4,096 位 RSA 私钥，如下所示：

```text
$ openssl genrsa 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
................................................................
................................................................
................................................................
++
................................................................
e is 65537 (0x10001)
-----BEGIN RSA PRIVATE KEY-----
MIIJ... [RSA private key contents omitted]
-----END RSA PRIVATE KEY-----
```

请注意，密钥采用特定格式——即 BEGIN RSA PRIVATE KEY 和 END RSA PRIVATE KEY 标记之间的 base64 编码数据。这是一种标准编码格式，大多数系统都支持并可将其转换为原始字节数据。开头的点序列是一种进度条，而 e 为 65537 (0x10001) 表示加密时使用的参数（请记住 RSA 通过计算 $C = P^e \bmod n$ 进行加密）。

## Protecting Keys

一旦你拥有了秘密密钥，你需要将其保密，同时在需要时可用。有三种方法可以解决这个问题：

- **密钥封装（使用第二个密钥加密密钥）。** 这种方法的问题在于，第二个密钥必须在你需要解密受保护密钥时可用。实际上，这个第二个密钥通常是从用户在使用受保护密钥时提供的密码生成的。这就是 Secure Shell (SSH) 协议的私钥通常被保护的方式。

- **从密码即时生成。** 这不需要存储加密文件，因为密钥直接从密码中产生。像加密货币钱包和密码管理器这样的系统经常使用这种方法。

  尽管这种方法比密钥封装更直接，但使用范围较窄，部分原因是它更容易受到弱密码的攻击。举例来说，如果攻击者截获了一些加密消息：如果我们使用密钥封装，攻击者首先需要获取受保护的密钥文件，该文件可能存储在用户的文件系统本地或密钥管理系统（KMS）中，因此不易访问。但如果我们使用即时生成，攻击者可以直接通过用候选密码尝试解密加密消息来搜索正确的密码。而且如果密码很弱，密钥就会被泄露。

- **将密钥存储在硬件令牌（智能卡或 USB 加密狗）上。** 这种方法中，我们将密钥存储在安全内存中，即使计算机被入侵，密钥仍然安全。这是密钥存储最安全的方法，但也是成本最高、最不方便的方法，因为它要求你随身携带硬件令牌并承担丢失的风险。智能卡和 USB 加密狗通常要求你输入密码才能从安全内存中解锁密钥。

> **NOTE**
> *无论你使用哪种方法，在交换密钥时务必不要将私钥误认为是公钥，也不要通过电子邮件或源代码意外发布私钥。（我实际上在 GitHub 上找到过私钥。）*



为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥提供的[content]
为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥提供的[content]
为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥提供的[content]
为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥提供的[content]
为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥提供的[content]
为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥提供的[content]
为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥提供的[content]
为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥提供的[content]
为了测试密钥包装，请运行以下 OpenSSL 命令，并使用参数 `-aes128` 告诉 OpenSSL 使用密码 AES-128（具有 128 位密钥的 AES）加密密钥：

```text
$ openssl genrsa -aes128 4096
Generating RSA private key, 4096 bit long modulus (2 primes)
...........++
...........................................................................
....................................................++
e is 65537 (0x10001)
Enter pass phrase:
```

OpenSSL 将使用请求的密码短语加密新创建的密钥。

## 事情可能出错的方式

密码学安全性可能以多种方式出错。最大的风险是由于安全证明或经过充分研究的协议而产生虚假的安全感，正如以下示例所示。

### 安全证明错误

即使是知名研究人员的安全证明也可能出错。证明彻底出错的最引人注目的例子之一是 *最优非对称加密填充 (OAEP)*，这是一种使用 RSA 的安全加密方法，已在许多应用中实现。OAEP 对抗选择密文攻击者的安全性错误证明被接受为有效长达七年，直到 2001 年一名研究人员发现了缺陷。不仅证明是错误的，结果也是错误的。后来的一项新证明表明，OAEP 仅对选择密文攻击者几乎是安全的。我们现在必须信任新的证明，并希望它没有缺陷。（有关更多详细信息，请参阅 Victor Shoup 的 2001 年论文“OAEP Reconsidered”。）

### 为兼容旧系统而使用短密钥

2015 年，研究人员发现一些 HTTPS 站点和 SSH 服务器支持的公钥密码术密钥比预期更短——即 512 位而不是至少 2,048 位。请记住，对于公钥方案，安全级别并不等于密钥大小，在 HTTPS 的情况下，512 位密钥能提供约 60 位的安全级别。这些密钥仅用 72 台处理器的集群计算约两周即可被破解。这影响了许多网站，包括美国联邦调查局 FBI 的网站。虽然软件最终通过 OpenSSL 及其他软件的补丁得到修复，但这个问题是一个相当不愉快的惊喜。

## 延伸阅读

要了解更多关于对称密码的可证明安全性的内容，请阅读海绵函数文档 https://keccak.team/sponge_duplex.html。海绵函数在对称密码中引入了基于置换的方法，描述了如何仅使用一种置换构造大量不同的密码学函数。

关于攻击真实成本的一些必读材料包括 Daniel J. Bernstein 2005 年的论文“Understanding Brute Force”以及 Michael Wiener 2004 年的论文“The Full Cost of Cryptanalytic Attacks”，两者均可在网上免费获取。

要确定给定密钥大小的安全级别，请访问 https://www.keylength.com。该网站列出了多个政府机构关于密钥大小的建议，以及根据公钥大小保证的安全性数量级。

最后，作为练习，选择一个应用程序（例如安全消息应用程序）并识别其密码方案、密钥长度和各自的安全级别。你经常会发现令人惊讶的不一致，例如一种方案提供 256 位安全级别，但另一种方案仅提供 100 位安全级别。整个系统的安全性通常仅与其最弱组件一样强。

## 第二部分：对称密码

### 4：分组密码

![](img/ace4de942d037de8ea5835bc9fbe57cd_88_0.png)

在冷战期间，美国和苏联开发了各自的密码。美国政府创建了数据加密标准 DES，该标准从 1979 年到 2005 年被采纳为联邦标准，而克格勃则开发了 GOST 28147-89，该算法直到 1990 年才保密，至今仍在使用。2000 年，美国的国家标准与技术研究所 NIST 选择了 DES 的继任者高级加密标准 AES，该算法由比利时开发，现在可在大多数电子设备中找到。AES、DES 和 GOST 28147-89 都是 *分组密码*，一种将处理数据块的核心算法与 *操作模式* 或处理数据块序列的技术相结合的密码类型。

本章回顾了分组密码的基础核心算法，讨论了其操作模式，并解释了它们如何协同工作。它还讨论了 AES 的工作原理，并以 1970 年代的经典攻击工具中间相遇攻击和 2000 年代的热门攻击技术——填充 oracle 告终。

### 什么是分组密码？

分组密码由加密算法和解密算法组成：

- 加密算法 E 接收密钥 K 和明文块 P，并生成密文块 C。我们将加密操作写为 C = E(K, P)。
- 解密算法 D 是加密算法的逆运算，将消息解密为原始明文 P。我们将此操作写为 P = D(K, C)。

由于它们互为逆运算，加密和解密算法通常涉及相似的操作。

### 安全目标

如果你已跟随关于加密、随机性和不可区分性的早期讨论，安全分组密码的定义不会让你感到意外。我们继续将安全性定义为随机性。

对于分组密码来说安全，它应为伪随机置换 PRP，这意味着只要密钥保密，攻击者就无法从任何输入计算出分组密码的输出。也就是说，只要 K 对攻击者而言是保密且随机的，他们对任意给定 P 的 E(K, P) 的样子就毫无头绪。

更一般地说，攻击者不应能够发现分组密码输入/输出值中的任何模式。换句话说，给定对某个固定且未知密钥的加密和解密函数的黑盒访问，应该无法区分分组密码和真正的随机置换。同理，攻击者不应能够恢复安全分组密码的秘密密钥；否则，他们就可以利用该密钥将分组密码与随机置换区分开。这意味着攻击者无法预测分组密码产生的给定密文对应的明文。

### 块大小

两个值表征分组密码：块大小和密钥大小。安全性取决于这两个值。大多数分组密码具有 64 位或 128 位块——DES 的块有 64 位 2^6，AES 的块有 128 位 2^7。在计算中，通常以 2 的幂测量的长度简化了数据处理、存储和寻址。但为什么是 2^6 和 2^7 而不是 2^4 或 2^16 位？

分组密码的块不宜过大，以尽量减少密文长度和内存占用。分组密码首先将其输入数据转换为块序列，这意味着要加密 16 位消息而块为 128 位时，你需要将消息转换为 128 位块供分组密码处理并返回 128 位密文。块越宽，额外开销越长。要处理 128 位块，至少需要 128 位内存。64、128 甚至 512 位的块足够短，可以放入大多数 CPU 的寄存器中，或使用专用硬件电路实现，从而在大多数情况下实现高效实现。但更大的块 例如数千字节长 会对实现的成本和性能产生明显影响。

当密文长度或内存占用至关重要时，你可能必须使用 64 位块，因为这些块产生的密文更短且消耗内存更少。否则，128 位或更大的块更好，主要是因为现代 CPU 通常能比 64 位块更高效地处理 128 位块，并且更安全 参见 *https://sweet32.info* 处的“Sweet32”攻击。特别是，CPU 可以利用指令高效并行处理一个或多个 128 位块——例如英特尔 CPU 中的高级向量扩展 AVX 系列指令。

### 代码本攻击

块不应过大，但也不应过小；否则，它们可能易受 *代码本攻击*，这是一种仅在使用较小的块时才有效的分组密码攻击。以 16 位块为例，代码本攻击的工作方式如下：

1. 获取每个 16 位明文块对应的 65,536 2^16 个密文。
2. 构建查找表——*代码本*——将每个密文块映射到其对应的明文块。
3. 要解密未知密文块，请在表中查找其对应的明文块。

使用 16 位块时，查找表仅需 2^16 × 16 = 2^20 位内存，或 128 千字节。使用 32 位块时，内存需求增长到 16 千兆字节，这仍然可以管理。但对于 64 位块，你必须存储 2^70 位 一泽位，或 128 艾字节，所以就别想了。因此，对于 128 位或更大的块，代码本攻击不是问题。

### 如何构造分组密码

存在数百种分组密码，但构造它的技术只有少数几种。实际上，分组密码不是一个庞大的算法，而是

对*轮*的重复——轮是一种简短的运算序列，单独来看很弱，但数量众多时很强。构造一轮有两种主要技术：代换–置换网络（如 AES 中）和 Feistel 方案（如 DES 中）。在本节中，你将在查看一种当所有轮彼此相同时有效的攻击之后，再看这些技术。

## 分组密码的轮

计算分组密码归根结底是计算一系列轮。在分组密码中，轮是一种基本变换，它易于描述和实现，并被多次迭代以构成分组密码的算法。这种由一个小型组件重复多次构成的构造，比由单一庞大算法构成的构造更易于实现和分析。

例如，一个三轮分组密码通过计算 *C* = **R**₃(**R**₂(**R**₁(*P*))) 来加密明文，其中轮为 **R**₁、**R**₂ 和 **R**₃，*P* 是明文。每一轮还应该有一个逆，这样接收者才有可能计算回明文。具体来说，*P* = **iR**₁(**iR**₂(**iR**₃(*C*)))，其中 **iR**₁ 是 **R**₁ 的逆，依此类推。

轮函数——**R**₁、**R**₂ 等等——通常是相同的算法，但它们由一个我们称之为*轮密钥*的值进行参数化。两个具有不同轮密钥的轮函数将表现不同，因此在输入相同的情况下会产生不同的输出。

我们使用*密钥调度*算法从主密钥 *K* 推导出轮密钥。例如，**R**₁ 使用轮密钥 **K**₁，**R**₂ 使用轮密钥 **K**₂，依此类推。

在每一轮中，轮密钥之间应该互不相同。此外，并非所有轮密钥都应该等于主密钥 *K*；否则，所有轮都会相同，分组密码也会更不安全，我将在下面说明这一点。

## 滑动攻击与轮密钥

为了避免*滑动攻击*，分组密码中任何一轮都不应该与另一轮相同。如图 4-1 所示，滑动攻击寻找两对明文/密文对 (*P*₁, *C*₁) 和 (*P*₂, *C*₂)，其中如果 **R** 是该密码的轮，则 *P*₂ = **R**(*P*₁)。当各轮相同时，两个明文之间的关系 *P*₂ = **R**(*P*₁) 就意味着它们各自密文之间的关系 *C*₂ = **R**(*C*₁)。图 4-1 显示了三轮，但无论轮数是多少（3、10 或 100），关系 *C*₂ = **R**(*C*₁) 都成立。问题在于，知道单轮的输入和输出往往有助于恢复密钥。（详情请参阅 Alex Biryukov 和 David Wagner 于 1999 年发表的论文《高级滑动攻击》，可参见 *https://www.iacr.org/archive/eurocrypt2000/1807/18070595-new.pdf.*）

![](img/ace4de942d037de8ea5835bc9fbe57cd_92_0.png)

图 4-1：针对具有相同轮的分组密码的滑动攻击原理

使用不同的轮密钥作为参数可确保各轮表现不同，从而挫败滑动攻击。

> 注意
> 使用轮密钥的一个潜在的副产品（同时也是好处）是能够抵御侧信道攻击，即利用密码实现泄露的信息（例如电磁辐射）进行的攻击。如果从主密钥 K 到轮密钥 K_i 的变换不可逆，那么即使攻击者找到 K_i，也无法利用该密钥找到 K。遗憾的是，很少有分组密码采用单向密钥调度。例如，AES 的密钥调度允许攻击者从任何轮密钥 K_i 计算出 K。

## 代换–置换网络

如果你读过密码学教材，你可能遇到过混淆和扩散。混淆意味着输入（明文和加密密钥）经过复杂的变换，而扩散意味着这些变换同等程度地依赖于输入的所有比特。从高层次来看，混淆关乎深度，而扩散关乎广度。在分组密码的设计中，混淆和扩散以代换和置换操作的形式出现，我们将它们结合在代换–置换网络（SPN）中。

代换通常以 S 盒（即代换盒）的形式出现，S 盒是小型查找表，用于变换 4 位或 8 位的块。例如，分组密码 Serpent 的八个 S 盒中的第一个由 16 个元素组成：(3 8 f 1 a 6 5 b e d 4 2 7 0 9 c)，其中每个元素代表一个 4 位的半字节。这个特定的 S 盒将 4 位半字节 0000 映射为 3（0011），将 4 位半字节 0101（十进制 5）映射为 6（0110），依此类推。

> 注意
> S 盒必须经过精心选择以确保其密码学强度：它们应尽可能非线性（输入和输出应通过复杂方程相关联），并且不应存在统计偏差（例如，翻转一个输入比特应可能影响任意输出比特）。

代换–置换网络中的置换可以简单到改变比特的顺序，这很容易实现，但对比特的混合程度不高。除了重新排列比特，一些密码使用基础的线性代数和矩阵乘法来混合比特：它们用固定值执行一系列乘法运算（矩阵的

密钥 K₂。在 DES 中，**F** 函数使用一个 48 位的轮密钥，该密钥由 56 位密钥 *K* 派生而来。

在 Feistel 方案中，**F** 函数可以是伪随机置换（PRP）或伪随机函数（PRF）。PRP 对任意两个不同的输入都会产生不同的输出，而 PRF 则会存在值 *X* 和 *Y*，使得 F(X) = F(Y)。但在 Feistel 方案中，只要 **F** 在密码学上足够强，这一差别并不重要。

Feistel 方案应该有多少轮呢？DES 执行 16 轮，而 GOST 28147-89 执行 32 轮。如果 **F** 函数尽可能强，理论上四轮就足够了，但实际密码会使用更多轮来抵御 **F** 中潜在的弱点。

## 高级加密标准

AES 是世界上使用最广泛的密码。在采用 AES 之前，使用的标准密码是 DES，其 56 位安全性低得离谱，此外还有 DES 的升级版，即三重 DES（3DES）。尽管 3DES 提供了更高的安全性（112 位安全性），但它效率低下，因为需要 168 位长的密钥才能获得 112 位安全性，而且软件实现速度很慢（DES 被设计为在集成电路中快速运行，而不是在主流的 CPU 上）。AES 解决了这两个问题。

NIST 于 2000 年将 AES 标准化，作为 DES 的替代方案，此后它成为世界上事实上的加密标准。如今大多数商业加密产品都支持 AES，美国国家安全局（NSA）也已批准它用于保护绝密信息。（一些国家确实更愿意使用自己的密码，主要是因为它们不想使用美国标准，但 AES 实际上更具比利时血统，而不是美国血统。）

> > **注意** *AES 曾用名是* Rijndael *（一个* 混成词 *，由发明者 Rijmen 和 Daemen 的名字构成，发音类似“rain-dull”）当时它是 AES 竞争的 15 个候选算法之一，AES 竞争是 NIST 在 1997 年至 2000 年间举办的过程，旨在确定“一种非保密的、公开披露的加密算法，能够在下一世纪很好地保护敏感政府信息”，正如 1997 年《联邦公报》上的竞争公告所述。AES 竞争就像是密码学家的“达人秀”，任何人都可以通过提交密码或破解其他参赛者的密码来参与。*

## AES 内部机制

AES 使用 128、192 或 256 位的密钥处理 128 位的块，其中 128 位密钥最为常见，因为它使加密速度略快，而且对于大多数应用来说，128 位与 256 位安全性之间的差异毫无意义。

有些密码处理单个比特或 64 位字，而 AES 操作的是*字节*。它将 16 字节的明文视为一个二维字节数组（*s* = *s*₀, *s*₁, · · · , *s*₁₅），如图 4-3 所示。（我们使用字母 *s*


因为这个数组是*内部状态*，或者就是*状态*。) AES会转换这个数组中的字节、列和行，以产生最终值为密文的结果。

![](img/ace4de942d037de8ea5835bc9fbe57cd_95_0.png)

图 4-3: AES的内部状态是一个16字节的4×4数组

为了转换其状态，AES使用如图4-4所示的SPN结构，128位密钥进行10轮，192位密钥进行12轮，256位密钥进行14轮。

![](img/ace4de942d037de8ea5835bc9fbe57cd_95_1.png)

图 4-4: AES的内部操作

图4-4展示了AES一轮操作的四个构建模块（注意除最后一轮外，所有轮次都是SubBytes、ShiftRows、MixColumns和AddRoundKey的序列）：

**AddRoundKey（轮密钥加）** 将轮密钥与内部状态进行XOR操作。

**SubBytes（字节代换）** 根据S盒将每个字节（s₀、s₁ . . . 、s₁₅）替换为另一个字节。在本例中，S盒是一个包含256个元素的查找表。

**ShiftRows（行移位）** 将第iᵗʰ行循环左移i个位置，其中i的取值范围为0到3（见图4-5）。

**MixColumns（列混合）** 对状态的四个列中的每一列应用相同的线性变换（即，每组具有相同灰色底纹的单元格，如图4-5左侧所示）。

![](img/ace4de942d037de8ea5835bc9fbe57cd_96_0.png)

*图 4-5: ShiftRows在内部状态的每一行内循环移位字节。*

请记住，在SPN中，S代表代换（substitution），P代表置换（permutation）。在这里，代换层是SubBytes，置换层是ShiftRows和MixColumns的组合。

密钥扩展函数KeyExpansion，如图4-4所示，是AES的密钥扩展算法。这种扩展使用与SubBytes相同的S盒并结合XOR操作，从16字节的密钥创建11个轮密钥（K₀、K₁、. . . 、K₁₀），每个轮密钥为16字节。KeyExpansion的一个重要特性是，给定任意轮密钥Kᵢ，攻击者可以通过逆向算法确定所有其他轮密钥以及主密钥K。从任何轮密钥中获取密钥的能力降低了该密码对侧信道攻击的抵抗力，在侧信道攻击中，攻击者可能轻易恢复轮密钥。

没有这些操作，AES将完全不安全。每种操作都以特定方式对AES的安全性做出贡献：

- 没有KeyExpansion，所有轮次都将使用相同的密钥K，AES将容易受到滑动攻击。
- 没有AddRoundKey，加密将不依赖于密钥；因此，任何人都可以在没有密钥的情况下解密任何密文。
- SubBytes引入了非线性操作，增加了密码强度。没有它，AES就只是一个大型线性方程组，可以使用高中数学（即高斯消元法）求解。
- 没有ShiftRows，给定列中的变化永远不会影响其他列，这意味着你可以通过为每列构建四个2³²元素码本来破解AES。（请记住，在安全的分组密码中，翻转输入中的一位应该影响所有的输出位。）
- 没有MixColumns，一个字节的变化不会影响状态中的任何其他字节。选择明文攻击者在存储16个各含256字节的查找表（这些表保存了每个字节每个可能值的加密值）后，就可以解密任何密文。

注意到图4-4中AES的最后一轮不包含MixColumns操作。省略此操作是为了节省无用的计算：由于MixColumns是线性的，你可以在最后一轮中通过以一种不依赖于其值或密钥的方式组合比特来抵消其效果。然而，如果在AddRoundKey之前不知道状态的值，我们就无法反转SubBytes操作。

要解密密文，AES通过取其逆函数来撤销每个操作：SubBytes的逆查找表反转SubBytes变换，ShiftRows向相反方向移位，应用MixColumns的逆变换（作为其操作编码矩阵的矩阵逆），而AddRoundKey的XOR保持不变，因为XOR的逆仍然是XOR。

## AES实战

作为练习，你可以使用Python的cryptography库使用AES加密和解密一个数据块，如清单4-1所示。

```
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from os import urandom

BLOCK_SIZE = 16
KEY_SIZE = 16

#### 使用Python的加密安全伪随机数生成器选取一个随机的16字节密钥。
k = urandom(KEY_SIZE)
print(f"k = {k.hex()}")

#### 创建一个AES-128实例。
aes = Cipher(algorithms.AES(k), modes.ECB())
aes_ecb_encryptor = aes.encryptor()

#### 将明文p设置为全零字符串。
p = bytes([0x00] * BLOCK_SIZE)

#### 将明文p加密为密文c。
c = aes_ecb_encryptor.update(p) + aes_ecb_encryptor.finalize()
print(f"enc({p.hex()}) = {c.hex()}")

#### 将密文c解密为明文p。
aes_ecb_decryptor = aes.decryptor()
p = aes_ecb_decryptor.update(c) + aes_ecb_decryptor.finalize()
print(f"dec({c.hex()}) = {p.hex()}")
```

清单 4-1: 在Python中使用AES加密和解密一个数据块

运行此脚本会产生类似如下的输出：

```
$ ./aes_block.py
k = 2c6202f9a582668aa96d511862d8a279
enc(00000000000000000000000000000000) = 12b620bb5eddce9a07523e59292a6d7
dec(12b620bb5eddce9a07523e59292a6d7) = 00000000000000000000000000000000
```

你会得到不同的结果，因为密钥在每次新执行时都是随机化的。

## 如何实现AES

真实的AES软件的工作方式与图4-4中的算法不同。你找不到生产级别的AES代码依次调用SubBytes()函数，然后是ShiftRows()函数，再是MixColumns()函数，因为这样效率低下。相反，快速的AES软件使用基于查表的实现和本机指令。

### 基于查表的实现

AES的基于查表实现将SubBytes-ShiftRows-MixColumns序列替换为XOR操作和在程序内部硬编码并在执行时加载到内存中的查找表的组合。这是可能的，因为MixColumns等价于对四个32位值进行XOR，其中每个值都依赖于状态中的单个字节以及SubBytes。因此，你可以构建四个各有256个条目的查找表，每个字节值对应一个表，并通过查找四个32位值并将它们XOR在一起来实现SubBytes-MixColumns序列。

例如，OpenSSL工具包中基于查表的C实现如清单4-2所示。

```
/* 第1轮： */
t0 = Te0[s0 >> 24] ^ Te1[(s1 >> 16) & 0xff] ^ Te2[(s2 >> 8) & 0xff] ^ Te3[s3 & 0xff] ^ rk[4];
t1 = Te0[s1 >> 24] ^ Te1[(s2 >> 16) & 0xff] ^ Te2[(s3 >> 8) & 0xff] ^ Te3[s0 & 0xff] ^ rk[5];
t2 = Te0[s2 >> 24] ^ Te1[(s3 >> 16) & 0xff] ^ Te2[(s0 >> 8) & 0xff] ^ Te3[s1 & 0xff] ^ rk[6];
t3 = Te0[s3 >> 24] ^ Te1[(s0 >> 16) & 0xff] ^ Te2[(s1 >> 8) & 0xff] ^ Te3[s2 & 0xff] ^ rk[7];
/* 第2轮： */
s0 = Te0[t0 >> 24] ^ Te1[(t1 >> 16) & 0xff] ^ Te2[(t2 >> 8) & 0xff] ^ Te3[t3 & 0xff] ^ rk[8];
s1 = Te0[t1 >> 24] ^ Te1[(t2 >> 16) & 0xff] ^ Te2[(t3 >> 8) & 0xff] ^ Te3[t0 & 0xff] ^ rk[9];
s2 = Te0[t2 >> 24] ^ Te1[(t3 >> 16) & 0xff] ^ Te2[(t0 >> 8) & 0xff] ^ Te3[t1 & 0xff] ^ rk[10];
s3 = Te0[t3 >> 24] ^ Te1[(t0 >> 16) & 0xff] ^ Te2[(t1 >> 8) & 0xff] ^ Te3[t2 & 0xff] ^ rk[11];
--snip--
```

清单 4-2: OpenSSL中AES基于查表的C实现节选

一个基本的基于查表的AES加密实现需要四张各4KB的表，因为每张表存储256个32位值，占用256 × 32 = 8,192位，即1KB。解密需要另外四张表，因此还需要4KB。但是有一些技巧可以将存储空间从4KB减少到1KB，甚至更少。

遗憾的是，基于查表的实现容易受到*缓存定时攻击*，这种攻击利用程序在缓存内存中读取或写入元素时的定时变化。访问时间取决于被访问元素在缓存内存中的相对位置。因此，定时会泄露与被访问元素有关的信息，进而泄露所涉及秘密的信息。

缓存定时攻击很难避免。一个显而易见的解决方案是完全放弃查找表，编写一个执行时间不依赖于其输入的程序，但这几乎不可能做到同时仍保持相同的速度，因此芯片制造商选择了一个激进的解决方案：他们不依赖潜在易受攻击的软件，而是依赖*硬件*。

### 本机指令

AES本机指令（AES-NI）解决了AES软件实现中缓存定时攻击的问题。要理解AES-NI的工作原理，请思考软件在硬件上运行的方式：为了运行程序，微处理器将二进制代码翻译成一系列集成电路组件执行的指令。例如，两个32位值之间的MUL汇编指令将激活微处理器中实现32位乘法器的晶体管。要实现加密算法，我们通常表达基本运算（加法、乘法、XOR等）的组合，微处理器按指定顺序激活其加法器、乘法器和XOR电路。

AES本机指令将此提升到了一个全新的水平，为开发人员提供了计算AES的专用汇编指令。使用AES-NI时，你不必将AES轮编码为一系列汇编指令，只需调用AESENC指令，芯片就会为你计算该轮操作。本机指令允许你告诉处理器运行AES轮次，而不是要求你将轮次编程为基本运算的组合。

使用本机指令实现AES的典型汇编实现如清单4-3所示。

```
PXOR      %xmm5,  %xmm0
AESENC    %xmm6,  %xmm0
AESENC    %xmm7,  %xmm0
AESENC    %xmm8,  %xmm0
AESENC    %xmm9,  %xmm0
AESENC    %xmm10, %xmm0
AESENC    %xmm11, %xmm0
AESENC    %xmm12, %xmm0
AESENC    %xmm13, %xmm0
AESENC    %xmm14, %xmm0
AESENCLAST %xmm15, %xmm0
```

*清单 4-3: 使用AES本机指令的AES-128实现*




## 操作模式

在第1章中，我解释了加密方案如何将置换与操作模式结合起来处理任意长度的消息。在本节中，我将介绍分组密码使用的主要操作模式、它们的安全性和功能特性，以及如何（不）使用它们。我将从最愚蠢的一个开始：电子密码本。

### 电子密码本模式

分组密码加密模式中最简单的是电子密码本（ECB），它几乎算不上一种操作模式。ECB 将明文块 P₁、P₂、…、P_N 逐个独立处理，通过计算 C₁ = E(K, P₁)、C₂ = E(K, P₂) 等，如图 4-6 所示。这是一种简单操作，但也是不安全的操作——ECB 不安全，你不应该使用它。

![](img/ace4de942d037de8ea5835bc9fbe57cd_101_0.png)

图 4-6：ECB 模式

微软的密码学家 Marsh Ray 曾经说过，“人人都知道 ECB 模式很糟糕，因为我们可以看到企鹅。”他指的是一个著名的说明 ECB 不安全的插图，使用了 Linux 的吉祥物 Tux 的图像，如图 4-7 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_102_0.png)

Tux 的原始图像在左边，使用 AES（尽管底层密码无关紧要）的 ECB 加密图像在右边。在加密版本中很容易看到企鹅的形状，因为 ECB 将原始图像中同一灰度色调的所有块加密为新图像中相同的新的灰度色调；换句话说，ECB 加密给你的是同一图像但颜色不同。

列表 4-4 中的 Python 程序也展示了 ECB 的不安全性。它选择一个伪随机密钥并加密一个包含两个空字节块的 32 字节消息 p。注意加密产生两个相同的块，并且使用相同的密钥和相同的明文重复加密会再次产生相同的两个块。

```
#!/usr/bin/env python

from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from os import urandom

BLOCK_SIZE = 16
KEY_SIZE = 16

#### The blocks() function splits a data string into space-separated blocks.
def blocks(data):
    split = [data[i:i+BLOCK_SIZE].hex() for i in range(0, len(data), BLOCK_SIZE)]
    return " ".join(split)

k = urandom(KEY_SIZE)
print(f"k = {k.hex()}")

#### Create an instance of AES-128 to encrypt and decrypt.
aes = Cipher(algorithms.AES(k), modes.ECB())
aes_ecb_encryptor = aes.encryptor()

#### Set plaintext p as two blocks of zeros.
p = bytes([0x00] * 2 * BLOCK_SIZE)

#### Encrypt plaintext p to ciphertext c.
c = aes_ecb_encryptor.update(p) + aes_ecb_encryptor.finalize()
print(f"enc({blocks(p)}) = {blocks(c)}")
```

*列表 4-4：在 Python 中使用 AES 的 ECB 模式*

运行此脚本会产生如下示例的密文块：

```
$ ./aes_ecb.py
k = 50a0ebeff8001250e87d31d72a86e46d
enc(00000000000000000000000000000000 00000000000000000000000000000000) = 5eb4b7af094ef7aca472bbd3cd72f1ed 5eb4b7af094ef7aca472bbd3cd72f1ed
```

使用 ECB 模式时，相同的密文块会向攻击者揭示相同的明文块，无论这些块是在单个密文内部还是跨不同密文。这表明 ECB 模式下的分组密码在语义上不安全。

ECB 的另一个问题是它只接受完整的数据块，因此如果块为 16 字节，如 AES 中那样，你只能加密 16 字节、32 字节、48 字节或 16 字节的任何其他倍数的块。有几种方法可以处理这个问题，正如你将在下一个模式 CBC 中看到的那样。（我不会告诉你这些技巧在 ECB 中如何工作，因为你根本就不应该使用 ECB。）

### 密码块链接模式

密码块链接（CBC）与 ECB 类似，但有一个小小的变化却带来很大差异：不是像 Cᵢ = E(K, Pᵢ) 那样加密第 i 个块 Pᵢ，CBC 设置 Cᵢ = E(K, Pᵢ ⊕ Cᵢ₋₁)，其中 Cᵢ₋₁ 是前一个密文块——从而将块 Cᵢ₋₁ 和 Cᵢ 链接起来。加密第一个块 P₁ 时，没有可用的前一个密文块，因此 CBC 使用一个随机初始值（IV），如图 4-8 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_103_0.png)

图 4-8：CBC 模式

CBC 模式使每个密文块都依赖于之前的所有块，并确保相同的明文块不会是相同的密文块。随机初始值保证了当使用两个不同的初始值两次调用密码时，两个相同的明文会加密为不同的密文。

列表 4-5 说明了这两个优点。此程序取一个全零的 32 字节消息（如列表 4-4 中的那样），用 CBC 加密两次，并显示两个密文。加粗的行 **iv = urandom(BLOCK_SIZE)** 为每次新加密选择一个新的随机 IV。

```
#!/usr/bin/env python

from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from os import urandom

BLOCK_SIZE = 16
KEY_SIZE = 16

#### The blocks() function splits a data string into space-separated blocks.
def blocks(data):
    split = [data[i:i+BLOCK_SIZE].hex() for i in range(0, len(data), BLOCK_SIZE)]
    return ' '.join(split)

#### Pick a random key.
k = urandom(KEY_SIZE)
print(f"k = {k.hex()}")

#### Pick a random IV.
iv = urandom(BLOCK_SIZE)
print(f"iv = {iv.hex()}")

#### Pick an instance of AES in CBC mode.
aes_cbc_encryptor = Cipher(algorithms.AES(k), modes.CBC(iv)).encryptor()

#### Set plaintext p as two blocks of zeros.
p = bytes([0x00] * 2 * BLOCK_SIZE)

c = aes_cbc_encryptor.update(p) + aes_cbc_encryptor.finalize()
print(f"enc({blocks(p)}) = {blocks(c)}")

#### Now with a different IV and the same key
iv = urandom(BLOCK_SIZE)
print(f"iv = {iv.hex()}")

aes_cbc_encryptor = Cipher(algorithms.AES(k), modes.CBC(iv)).encryptor()
c = aes_cbc_encryptor.update(p) + aes_cbc_encryptor.finalize()
print(f"enc({blocks(p)}) = {blocks(c)}")
```

*列表 4-5：使用 AES 的 CBC 模式*

两个明文相同（两个全零块），但加密后的块应不同，如此示例执行所示：

```
$ ./aes_cbc.py
k = 9cf0d31ad2df24f3cbbefc1e6933c872
iv = 0a75c4283b4539c094fc262aff0d17af
enc(00000000000000000000000000000000 00000000000000000000000000000000) = 370404dcab6e9ecbc3d24ca5573d2920 3b9e5d70e597db225609541f6ae9804a
```

```
iv = a6016a6698c3996be13e8739d9e793e2
enc(00000000000000000000000000000000 00000000000000000000000000000000) = 655e1bb3e74ee8cf9ec1540afd8b2204 b59db5ac28de43b25612dfd6f031087a
```

不幸的是，我们经常使用常量 IV 而不是随机 IV 使用 CBC，这会暴露相同的明文以及以相同块开头的明文。例如，假设 CBC 将两块明文 P₁ || P₂ 加密为两块密文 C₁ || C₂。如果 CBC 使用相同的 IV 加密 P₁ || P₂′，其中 P₂′ 是与 P₂ 不同的某个块，那么密文将看起来像 C₁ || C₂′，其中 C₂′ 与 C₂ 不同但第一个块 C₁ 相同。因此，攻击者可以猜测两个明文的第一个块相同，即使他们只能看到密文。

> *在 CBC 模式中，解密需要知道用于加密的 IV，因此 IV 会连同密文一起发送，以明文形式发送。*

在 CBC 中，由于并行性，解密可以比加密快得多。虽然新块 Pᵢ 的加密需要等待前一个块 Cᵢ₋₁，但块的解密计算 Pᵢ = D(K, Cᵢ) ⊕ Cᵢ₋₁，其中不需要前一个明文块 Pᵢ₋₁。这意味着只要你知道前一个密文块（通常你会知道），就可以同时并行解密所有块。

### CBC 模式下的消息加密

让我们回到块终止问题，看看如何处理长度不是块长度倍数的明文。例如，当块为 16 字节时，你如何用 AES-CBC 加密一个 18 字节的明文？剩下的 2 字节怎么办？你将查看两种广泛使用的处理此问题的方法。第一种是填充，会使密文比明文稍长，而第二种是密文窃取，会产生与明文长度相同的密文。

### 消息填充

填充是一种技术，允许你加密任意长度的消息，甚至小于单个块的消息。PKCS#7 标准和 RFC 5652 指定了分组密码的填充，我们在几乎所有使用 CBC 的地方都使用它。

我们使用填充通过向明文添加额外字节来扩展消息以填满完整的块。以下是 16 字节块填充的规则：

-   如果剩下 1 字节——例如，如果明文长度为 1 字节、17 字节或 33 字节——则用 15 个字节 0x0f（十进制 15）填充消息。
-   如果剩下 2 字节，则用 14 个字节 0x0e（十进制 14）填充消息。
-   如果剩下 3 字节，则用 13 个字节 0x0d（十进制 13）填充消息。



如果明文有 15 字节，距离填满一个块还差一个字节，则填充会添加一个 01 字节。如果明文本身就是 16 字节的倍数，则添加 16 个字节 0x10（十进制为 16）。该技巧可推广到任意长度不超过 255 字节的块（对于更大的块，一个字节不足以编码大于 255 的值）。

解密填充后的消息的工作方式如下：

- 1. 如同未填充的 CBC 一样解密所有块。
- 2. 确保最后一块的最后几个字节符合填充规则：它们以至少一个 01 字节、至少两个 02 字节或至少三个 03 字节等结尾。如果填充无效——例如，最后几个字节是 01 02 03——则消息被拒绝。否则，解密会去掉填充字节并返回剩余的明文字节。

填充的一个缺点是它使密文变长，至少 1 字节，最多一个块。

## 密文窃取

密文窃取是我们用来加密长度不是块大小倍数的消息的另一种技巧。密文窃取比填充更复杂、流行度更低，但它提供了一些好处：

- 明文可以是任意位长度，而不仅仅是字节。例如，你可以加密一条 131 位的消息。
- 密文与明文长度完全相同。
- 密文窃取不会受到填充 oracle 攻击的威胁，后者是一种强大的攻击，有时会对使用填充的 CBC 起作用（你将在“Padding Oracle Attacks”第 83 页看到）。

在 CBC 模式下，密文窃取用来自前一个密文块的位扩展最后一个不完整的明文块，然后加密 resulting 块。最后一个不完整的密文块由来自前一个密文块的最初几个位组成——也就是未附加到最后一个明文块的位。

在图 4-9 中，我们有三个块，其中最后一个块 P₃ 不完整（用零表示）。如果 P₃ 为 3 字节，我们将其与前一个密文块 E(K, P₂) 的最后 12 位进行 XOR，并将加密结果作为 C₃ 返回。最后一个密文块 C₃ 然后由 E(K, P₂) 的前 4 字节组成。解密只是该操作的逆过程。

![](img/ace4de942d037de8ea5835bc9fbe57cd_107_0.png)

*图 4-9：CBC 模式加密的密文窃取*

密文窃取并没有什么主要问题，但它不够优雅且难以正确实现，尤其是在 NIST 的标准规定了三种不同的实现方式时（参见 Special Publication 800-38A）。

## 计数器模式

为了避免麻烦并保留密文窃取的好处，使用计数器模式（CTR）。CTR 几乎算不上一种分组密码模式：它将分组密码变成一种流密码，只需输入位并输出位，且不会因块的概念而尴尬。（我将在第 5 章详细讨论流密码。）

在 CTR 模式下（见图 4-10），分组密码算法不会转换明文数据。相反，它加密由计数器和 nonce 组成的块。*counter* 是一个对每个块递增的整数。消息中不应有两个块使用相同的计数器，但不同消息可以使用相同的计数器值序列（1, 2, 3, . . .）。*nonce* 是一个我们仅使用一次的数字。它在单个消息的所有块中相同，但两个消息不应使用相同的 nonce。

![](img/ace4de942d037de8ea5835bc9fbe57cd_107_1.png)

*图 4-10：CTR 模式*

图 4-10 显示，在 CTR 模式下，加密将明文与从“加密” nonce, N, 和 counter, Ctr 中获取的流进行 XOR。解密相同，所以你只需要加密算法即可完成加密和解密。清单 4-6 中的 Python 脚本提供了实践示例。

```
#!/usr/bin/env python

from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from os import urandom

BLOCK_SIZE = 16
KEY_SIZE = 16

#### Pick a random key.
k = urandom(KEY_SIZE)
print(f"k   = {k.hex()}")

#### And a random nonce
#### (careful with random nonces, see discussion below).
n = urandom(BLOCK_SIZE)
print(f"nonce  = {n.hex()}")

#### Create a 7-byte plaintext p.
p = bytes([0x00] * 7)

#### Encrypt the plaintext p with AES-CTR.
aes_ctr_encryptor = Cipher(algorithms.AES(k), modes.CTR(n)).encryptor()

c = aes_ctr_encryptor.update(p) + aes_ctr_encryptor.finalize()
print(f"enc({p.hex()}) = {c.hex()}")

#### Decrypt the ciphertext c.
aes_ctr_decryptor = Cipher(algorithms.AES(k), modes.CTR(n)).decryptor()
p = aes_ctr_decryptor.update(c) + aes_ctr_decryptor.finalize()
print(f"dec({c.hex()}) = {p.hex()}")

#### Decrypt the ciphertext c using the encryption function.
aes_ctr_encryptor = Cipher(algorithms.AES(k), modes.CTR(n)).encryptor()
p = aes_ctr_encryptor.update(c) + aes_ctr_encryptor.finalize()
print(f"enc({c.hex()}) = {p.hex()}")
```

*清单 4-6：使用 AES in CTR mode*

示例执行加密一个 4 字节的明文并得到一个 4 字节的密文。然后它使用加密函数解密该密文：

```
$ ./aes_ctr.py
k = 130a1aa77fa58335272156421cb2a3ea
enc(00010203) = b23d284e
enc(b23d284e) = 00010203
```

与 CBC 中的初始值一样，加密器提供 CTR 的 nonce 并将其与密文一起明文发送。但与 CBC 的初始值不同，CTR 的 nonce 不需要是随机的；它只需要是唯一的。nonce 应该唯一的原因与我们不应该重用一次性密码本相同：当调用伪随机流 S 时，如果你使用相同的 nonce 将 P₁ 加密为 C₁ = P₁ ⊕ S 并将 P₂ 加密为 C₂ = P₂ ⊕ S，那么 C₁ ⊕ C₂ 会泄露 P₁ ⊕ P₂。

随机 nonce 只有在足够长时才有效；例如，如果 nonce 为 n 位，则在 2^{n/2} 次加密和同样多的 nonce 之后，有可能遇到重复。64 位对于随机 nonce 不足，因为你大约在 2^{32} 个 nonce 后就会期望出现重复，这是一个不可接受的低数字。

如果计数器对每个新明文递增并且足够长——例如 64 位计数器——则可以保证其唯一性。

CTR 的一个特定好处是它可能比任何其他模式都更快。不仅可以并行化，而且你可以在不知道消息之前就开始加密，通过选择一个 nonce 并计算稍后将与明文进行 XOR 的流。

> NOTE
> 取决于我们实现的 CTR 版本，我们可能会将 API 使用为参数的 nonce 与计数器连接起来（如图 4-10 所示），或直接将计数器视为与块一样宽。

## How Things Can Go Wrong

存在两种必须了解的分组密码攻击：meet-in-the-middle 攻击，这是一种在 1970 年代发现但仍用于许多密码分析攻击的技术（不要与中间人攻击混淆），以及 padding oracle 攻击，这是一种在 2002 年由学术密码学家发现、随后大多被忽视、十年后与若干易受攻击的应用一起重新发现的攻击类别。

## Meet-in-the-Middle Attacks

3DES 分组密码是 1970 年代标准 DES 的升级版，采用 56 × 3 = 168 位的密钥（改进了 DES 的 56 位密钥）。但由于 meet-in-the-middle（MitM）攻击，3DES 的安全级别为 112 位而不是 168 位。

图 4-11 显示 3DES 使用 DES 加密和解密函数加密一个块：首先使用密钥 K₁ 加密；然后使用密钥 K₂ 解密；最后使用另一个密钥 K₃ 加密。如果 K₁ = K₂，前两次调用会相互抵消，3DES 就简化为使用密钥 K₃ 的单个 DES。3DES 采用加密-解密-加密而不是三次加密，以便系统在必要时可以使用新的 3DES 接口模拟 DES。

![](img/ace4de942d037de8ea5835bc9fbe57cd_109_0.png)

为什么使用三重 DES 而不是双重 DES——也就是说，为什么将明文 P 加密为 E(K₂, E(K₁, P))？事实证明，MitM 攻击使双重 DES 的安全性仅与单 DES 相同。图 4-12 显示了 MitM 攻击的实际操作。

![](img/ace4de942d037de8ea5835bc9fbe57cd_110_0.png)

图 4-12：The MitM attack

MitM 攻击的工作方式如下，用于攻击双重 DES：

- 1. 假设你有 P 和 C = E(K₂, E(K₁, P))，其中有两个未知的 56 位密钥 K₁ 和 K₂。（DES 使用 56 位密钥，因此双重 DES 总共使用 112 位密钥。）你构建一个包含 2⁵⁶ 个条目的键值表 E(K₁, P)，其中 E 是 DES 加密函数，K₁ 是存储的值。
- 2. 对于所有 2⁵⁶ 个 K₂ 值，计算 D(K₂, C) 并检查结果值是否作为索引出现在表中（因此作为中间值，在图 4-12 中用问号表示）。
- 3. 如果你找到表中的中间值作为索引，则从表中获取对应的 K₁，并通过使用其他 P 和 C 对验证找到的 (K₁, K₂) 是否正确。使用 K₁ 和 K₂ 加密 P，然后检查获得的密文是否等于给定的 C。

这种方法通过大约 2⁵⁷ 次而不是 2¹¹² 次操作恢复 K₁ 和 K₂：步骤 1 加密 2⁵⁶ 个块，然后步骤 2 最多解密 2⁵⁶ 个块，总共 2⁵⁶ + 2⁵⁶ = 2⁵⁷ 次操作。你还需要存储 2⁵⁶ 个每个 15 字节的元素，或约 1 艾字节。这很多，但有一个技巧可以让你仅用可忽略的内存运行相同的攻击（如你在第 6 章中看到的）。

你可以几乎以相同的方式将 MitM 攻击应用于 3DES，就像应用于双重 DES 一样，只是第三阶段将遍历所有 2¹¹² 个 K₂ 和 K₃ 值。因此整个攻击在执行大约 2¹¹² 次操作后成功，这意味着 3DES 尽管具有 168 位的密钥材料，但仅获得 112 位的安全性。

## Padding Oracle Attacks

我们以 2000 年代最简单却最具毁灭性的攻击之一结束本章：padding oracle 攻击。记住，填充用额外字节填充明文以填满一个块。例如，111 字节的明文是六个 16 字节块后跟 15 字节的序列。在这种情况下，形成完整块的填充会添加一个 01 字节。对于 110 字节的明文，填充会添加 2 个 02 字节。对于 109 字节的明文，它会添加 3 个 03 字节，依此类推，直到我们添加 16 个 10 字节的情况，其中十六进制值 10 等于 16。




填充预言机是一种系统，其行为会根据 CBC 加密密文中的填充是否有效而有所不同。你可以把它看作一个黑盒或 API，它返回成功或错误值。例如，你可以在远程主机上的某个服务中获得填充预言机，该服务在收到格式错误的密文时会发送错误消息。有了这样的预言机，填充预言机攻击会记录哪些输入具有有效填充、哪些没有，然后利用这些信息来解密选定的密文值。

假设你想解密一个密文块 C₂。我将你要找的值称为 X，即 D\_K(C₂)，并将 CBC 模式解密后得到的块称为 P₂（见图 4-13）。如果你选择一个随机块 C₁，并将两块密文 C₁ || C₂ 发送给预言机，只有当 C₁ ⊕ X = P₂ 以有效填充结束时，解密才会成功——即一个 01 字节、两个 02 字节或三个 03 字节，等等。

![](img/ace4de942d037de8ea5835bc9fbe57cd_111_0.png)

图 4-13：填充预言机攻击通过选择 C₁ 并检查填充的有效性来恢复 X。

基于这一观察，针对 CBC 加密的填充预言机攻击可以如下解密一个块 C₂（字节用数组表示法表示：C₁[0] 是 C₁ 的第一个字节，C₁[1] 是第二个字节，依此类推，直到 C₁[15]，即 C₁ 的最后一个字节）：

- 1. 选择一个随机块 C₁，并改变其最后一个字节，直到填充预言机接受该密文为有效。通常，在有效密文中，C₁[15] ⊕ X[15] = 01，因此你会在尝试大约 128 个 C₁[15] 值后找到 X[15]。
- 2. 通过将 C₁[15] 设置为 X[15] ⊕ 02，并搜索能产生正确填充的 C₁[14]，来找到 X[14] 的值。当预言机接受该密文为有效时，就意味着你找到了满足 C₁[14] ⊕ X[14] = 02 的 C₁[14]。
- 3. 对所有 16 个字节重复步骤 1 和 2。

该攻击平均需要对预言机进行 128 次查询才能处理 16 个字节中的每一个，总计约 2000 次查询。（注意，每次查询必须使用相同的初始值。）

> **注意** *在实践中，实现填充预言机攻击比我描述的要复杂一些，因为你必须处理第 1 步中的错误猜测。密文可能具有有效填充，并不是因为 P₂ 以单个 01 结尾，而是因为它以两个 02 字节或三个 03 字节结尾。你可以通过测试修改更多字节的密文的有效性来应对这种情况。*

### 延伸阅读

关于分组密码有很多可以说的，无论是算法如何工作，还是它们如何被攻击。例如，费斯妥网络和 SPN 并不是构建分组密码的唯一方法。IDEA 和 FOX 分组密码使用 Lai–Massey 结构，而 Threefish 使用 ARX 网络，即加法、字循环移位和异或的组合。

除了 ECB、CBC 和 CTR 之外，还有更多模式。有些模式是没人使用的民间技术，如 CFB 和 OFB，而另一些则用于特定应用，如用于可调整加密的 XTS 或用于认证加密的 GCM。

我已经讨论了 Rijndael（AES 的获胜者），但当时参赛的还有其他 14 种算法：CAST-256、CRYPTON、DEAL、DFC、E2、FROG、HPC、LOKI97、Magenta、MARS、RC6、SAFER+、Serpent 和 Twofish。我建议你查阅它们，了解它们如何工作、如何设计、如何被攻击以及速度如何。美国国家安全局（NSA）的设计（Skipjack，以及最近的 SIMON 和 SPECK）和更新的“轻量级”分组密码（如 GIFT、KATAN、PRESENT 或 PRINCE）也值得一看。

### 5 流密码

![](img/ace4de942d037de8ea5835bc9fbe57cd_114_0.png)

对称密码可以是分组密码，也可以是流密码。回顾第 4 章，分组密码将明文比特块与密钥比特混合，产生相同大小的密文块，通常是 64 或 128 比特。另一方面，流密码不混合明文和密钥比特；相反，它们从密钥生成伪随机比特，并通过将明文与伪随机比特异或来加密明文，方式与第 1 章解释的一次性密码本相同。

流密码有时会被回避，因为它们在历史上比分组密码更脆弱，也更容易被破解——无论是业余爱好者设计的实验性密码，还是部署在数百万人使用的系统中的密码，包括手机、Wi-Fi 和公共交通智能卡。但幸运的是，尽管花了将近 20 年时间，我们现在知道如何设计安全的流密码，并且我们信任它们来保护蓝牙连接、移动 4G 通信和 TLS 连接。本章首先介绍流密码的工作原理，并讨论流密码的两大类：有状态的和基于计数器的。然后我们将研究面向硬件和面向软件的流密码，并考察一些不安全的密码（GSM 移动通信中使用的 A5/1，以及旧版 TLS 中的 RC4）和安全、最先进的密码（面向硬件的 Grain-128a 和面向软件的 Salsa20）。

### 流密码的工作原理

流密码比分组密码更像确定性随机位生成器（DRBG），因为它们生成的是伪随机比特流，而不是直接混合明文数据。

流密码与 DRBG 的区别在于，DRBG 接受单个输入值，而流密码接受两个值：密钥和 nonce。密钥应当是秘密的，通常为 128 或 256 比特。nonce 不一定是秘密，但应当对每个密钥是唯一的，通常为 64 到 128 比特。

流密码产生一个我们称之为*密钥流*的伪随机比特流。为了加密，我们将密钥流与明文异或；为了解密，再将密钥流与密文异或。图 5-1 展示了基本的流密码加密操作，其中 $SC$ 是流密码算法，$KS$ 是密钥流，$P$ 是明文，$C$ 是密文。

![](img/ace4de942d037de8ea5835bc9fbe57cd_115_0.png)

流密码计算 $KS = SC(K, N)$，加密为 $C = P \oplus KS$，解密为 $P = C \oplus KS$。加密和解密函数是相同的，因为两者做的事情相同——即与密钥流进行比特异或。这就是为什么某些密码库只提供一个加密函数来同时进行加密和解密。

流密码允许你使用密钥 $K_1$ 和 nonce $N_1$ 加密一条消息，然后使用密钥 $K_1$ 和不同于 $N_1$ 的 nonce $N_2$，或使用不同于 $K_1$ 的密钥 $K_2$ 和 nonce $N_1$ 加密另一条消息。但是，你绝不能再使用 $K_1$ 和 $N_1$ 加密，因为那会两次使用同一个密钥流 $KS$。也就是说，你会得到第一个密文 $C_1 = P_1 \oplus KS$ 和第二个密文 $C_2 = P_2 \oplus KS$；如果你知道 $P_1$，就可以确定 $P_2 = C_1 \oplus C_2 \oplus P_1$。

**注意** Nonce 是“number used only once”（只使用一次的数字）的缩写。在流密码的上下文中，我们有时称它为 IV，即“初始值”。

从高层视角来看，流密码有两种类型：有状态的和基于计数器的。有状态流密码有一个秘密的内部状态，它在密钥流生成过程中不断演化。算法用密钥和 nonce 初始化状态，然后调用更新函数来更新状态值，并从状态中产生一个或多个密钥流比特，如图 5-2 所示。例如，RC4 是有状态的，而 Salsa20 是基于计数器的。

![](img/ace4de942d037de8ea5835bc9fbe57cd_116_0.png)

图 5-2：有状态流密码

基于计数器的流密码从密钥、nonce 和计数器值生成密钥流块，如图 5-3 所示。与有状态流密码不同，基于计数器的流密码（如 Salsa20）在生成密钥流期间，除了计数器值外，不需要跟踪任何秘密。

![](img/ace4de942d037de8ea5835bc9fbe57cd_116_1.png)

图 5-3：基于计数器的流密码

这两种方法定义了流密码的高层架构，无论核心算法如何工作。流密码的内部结构也根据密码的目标平台分为两类：面向硬件和面向软件。

### 面向硬件的流密码

当密码学家谈论硬件时，他们指的是专用集成电路（ASIC）、可编程逻辑器件（PLD）和现场可编程门阵列（FPGA）。密码算法的硬件实现

是一种在位级别实现加密算法的电子电路，且不能用于其他任何用途；换句话说，该电路是*专用硬件*。另一方面，加密算法的软件实现只是告诉微处理器执行哪些指令以运行算法。这些指令操作字节或字，然后调用实现通用操作（如加法和乘法）的电子电路部件。软件处理的是 32 或 64 位的字节或字，而硬件处理的是位。最早的流密码使用位来节省复杂的按字操作，从而在硬件上更高效，当时硬件是其目标平台。

流密码主要用于硬件实现，因为它们比分组密码更便宜。它们需要的内存和逻辑门比分组密码少，因此在集成电路上占用的面积更小，从而降低了制造成本。例如，按门当量计数，集成电路的标准面积度量，你可以找到流密码占用不到 1,000 个门当量；而相比之下，典型的面向软件的分组密码至少需要 10,000 个门当量，使得加密的成本比使用流密码高出一个数量级。

然而，今天分组密码不再比流密码更昂贵——首先，因为现在有硬件友好的分组密码，其大小与流密码相当，其次，因为硬件成本已经大幅下降。尽管如此，流密码通常与硬件相关联，因为它们曾经是最好的选择。

在下一节中，我将解释硬件流密码背后的基本机制，称为*反馈移位寄存器 (FSRs)*。几乎所有硬件流密码都以某种方式依赖于 FSRs，无论是用于 2G 手机的 A5/1 密码，还是更新的 Grain-128a 密码。

> **注意**  
> *第一个标准分组密码，即数据加密标准（DES），是为硬件而非软件优化的。当美国政府在 1970 年代标准化 DES 时，大多数目标应用都是硬件实现。因此，DES 中的 S 盒在硬件中实现为逻辑电路时体积小、计算速度快，但在软件中效率低下也就不足为奇了。与 DES 不同，当前的高级加密标准（AES）处理的是字节，因此在软件中比 DES 更高效。*

## 反馈移位寄存器

无数流密码使用 FSRs，因为它们简单且已被充分理解。FSR 是一组配备更新*反馈函数*的位，我将其记为 f。FSR 的状态存储在该数组或寄存器中，并且 FSR 的每次*更新*都使用反馈函数来改变状态的值并产生一个输出位。

实际上，FSR 的工作方式如下：如果 R₀ 是 FSR 的初始值，则下一个状态 R₁ 定义为 R₀ 左移 1 位，其中离开寄存器的位作为输出返回，而空出的位置用 f(R₀) 填充。

我们重复相同的规则来计算后续状态值 R₂、R₃，等等。也就是说，给定时间 t 时 FSR 的状态 Rₜ，下一个状态 Rₜ₊₁ 为：

Rₜ₊₁ = (Rₜ << 1) | f(Rₜ)

在此方程中，| 是逻辑或运算符，<< 是移位运算符，如 C 语言中使用。例如，给定 8 位字符串 00001111，我们有：

00001111 << 1 = 00011110
00011110 << 1 = 00111100
00111100 << 1 = 01111000

位移将位向左移动，丢失最左边的位以保留状态的位长度，并将最右边的位清零。FSR 的更新操作是相同的，只是最右边的位不是设为 0，而是设为 f(Rₜ)。

例如，考虑一个反馈函数 f 对 4 个位全部进行异或的 4 位 FSR。将状态初始化为以下值：

1 1 0 0

现在将位向左移动，其中 1 被输出且最右边的位被设为以下值：

f(1100) = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0

现在状态变为：

1 0 0 0

下一次更新输出 1，左移状态，并将最右边的位设为以下值：

f(1000) = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1

现在状态是：

0 0 0 1

接下来的三次更新返回三个 0 位并给出以下状态值：

0 0 1 1
0 1 1 0
1 1 0 0

我们因此在五次迭代后返回到初始状态 1100；从在此循环中观察到的任何值开始更新状态五次

会使我们返回到该初始值。我们说 5 是给定 1100、1000、0001、0011 或 0110 中任一值的 FSR 的周期。因为该 FSR 的周期为 5，时钟寄存器 10 次会产生两次相同的 5 位序列。同样，如果你从 1100 开始时钟寄存器 20 次，输出位将为 11000110001100011000，即四次相同的 5 位序列 11000。直观上，这种重复模式应避免，更长的周期对安全性更好。

注意 如果你计划在流密码中使用 FSR，避免使用周期短的 FSR，因为这会使输出更可预测。对于某些类型的 FSR，很容易弄清其周期，但对于其他类型则几乎不可能。

图 5-4 显示了该循环的结构，以及该 FSR 的其他循环，每个循环都是一个圆圈，其点代表寄存器的一个状态。

![](img/ace4de942d037de8ea5835bc9fbe57cd_119_0.png)

图 5-4：反馈函数对 4 个位进行异或的 FSR 的循环

事实上，这个特定的 FSR 还有另外两个周期为 5 的循环——{0100, 1001, 0010, 0101, 1010} 和 {1111, 1110, 1101, 1011, 0111}。请注意，任何给定状态只能属于一个状态循环。在这里，我们有三个每个包含五个状态的循环，覆盖了我们 4 位寄存器 2^4 = 16 个可能值中的 15 个。第 16 个可能值是 0000，如图 5-4 所示，它是一个周期为 1 的循环，因为 FSR 将 0000 变换为 0000。

FSR 本质上是一个位寄存器，其中每次寄存器的更新都会输出一位（寄存器的最左位），并且一个函数计算寄存器的新最右位。（所有其他位都左移。）从某个初始状态开始的 FSR 的周期是 FSR 再次进入同一状态所需的更新次数。如果需要 N 次更新，则 FSR 将再次产生相同的 N 位。

## 线性反馈移位寄存器

*线性反馈移位寄存器 (LFSRs)* 是具有线性反馈函数的 FSR——即对状态的某些位进行异或的函数，例如上一节中 4 位 FSR 的示例及其反馈函数返回寄存器的 4 个位的异或。回想一下，在密码学中，线性与可预测性同义，并暗示存在简单的底层数学结构。而且，正如你可能预期的那样，由于这种线性，我们可以使用线性复杂度、有限域和本原多项式等概念来分析 LFSRs——但我将跳过数学细节，只给你必要的事实。

> **注意**  
> *在线性代数中，我们定义线性变换* f *为满足* f(u + v) = f(u) + f(v) *的函数。*如果你知道* f(u) *和* f(v)，*你就可以在不知道* u *或* v *的情况下确定* f(u + v)。*对于非线性函数，情况要复杂得多；你无法轻易从* f(u) *和* f(v) *找到* f(u + v)。

选择要一起异或的位对 LFSR 的周期至关重要，从而对其密码学价值至关重要。好消息是我们知道如何选择位的[content]
是一种在位级别实现加密算法的电子电路，且不能用于其他任何用途；换句话说，该电路是*专用硬件*。另一方面，加密算法的软件实现只是告诉微处理器执行哪些指令以运行算法。这些指令操作字节或字，然后调用实现通用操作（如加法和乘法）的电子电路部件。软件处理的是 32 或 64 位的字节或字，而硬件处理的是位。最早的流密码使用位来节省复杂的按字操作，从而在硬件上更高效，当时硬件是其目标平台。

流密码主要用于硬件实现，因为它们比分组密码更便宜。它们需要的内存和逻辑门比分组密码少，因此在集成电路上占用的面积更小，从而降低了制造成本。例如，按门当量计数，集成电路的标准面积度量，你可以找到流密码占用不到 1,000 个门当量；而相比之下，典型的面向软件的分组密码至少需要 10,000 个门当量，使得加密的成本比使用流密码高出一个数量级。

然而，今天分组密码不再比流密码更昂贵——首先，因为现在有硬件友好的分组密码，其大小与流密码相当，其次，因为硬件成本已经大幅下降。尽管如此，流密码通常与硬件相关联，因为它们曾经是最好的选择。

在下一节中，我将解释硬件流密码背后的基本机制，称为*反馈移位寄存器 (FSRs)*。几乎所有硬件流密码都以某种方式依赖于 FSRs，无论是用于 2G 手机的 A5/1 密码，还是更新的 Grain-128a 密码。

> **注意**  
> *第一个标准分组密码，即数据加密标准（DES），是为硬件而非软件优化的。当美国政府在 1970 年代标准化 DES 时，大多数目标应用都是硬件实现。因此，DES 中的 S 盒在硬件中实现为逻辑电路时体积小、计算速度快，但在软件中效率低下也就不足为奇了。与 DES 不同，当前的高级加密标准（AES）处理的是字节，因此在软件中比 DES 更高效。*

## 反馈移位寄存器

无数流密码使用 FSRs，因为它们简单且已被充分理解。FSR 是一组配备更新*反馈函数*的位，我将其记为 f。FSR 的状态存储在该数组或寄存器中，并且 FSR 的每次*更新*都使用反馈函数来改变状态的值并产生一个输出位。

实际上，FSR 的工作方式如下：如果 R₀ 是 FSR 的初始值，则下一个状态 R₁ 定义为 R₀ 左移 1 位，其中离开寄存器的位作为输出返回，而空出的位置用 f(R₀) 填充。

我们重复相同的规则来计算后续状态值 R₂、R₃，等等。也就是说，给定时间 t 时 FSR 的状态 Rₜ，下一个状态 Rₜ₊₁ 为：

Rₜ₊₁ = (Rₜ << 1) | f(Rₜ)

在此方程中，| 是逻辑或运算符，<< 是移位运算符，如 C 语言中使用。例如，给定 8 位字符串 00001111，我们有：

00001111 << 1 = 00011110
00011110 << 1 = 00111100
00111100 << 1 = 01111000

位移将位向左移动，丢失最左边的位以保留状态的位长度，并将最右边的位清零。FSR 的更新操作是相同的，只是最右边的位不是设为 0，而是设为 f(Rₜ)。

例如，考虑一个反馈函数 f 对 4 个位全部进行异或的 4 位 FSR。将状态初始化为以下值：

1 1 0 0

现在将位向左移动，其中 1 被输出且最右边的位被设为以下值：

f(1100) = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0

现在状态变为：

1 0 0 0

下一次更新输出 1，左移状态，并将最右边的位设为以下值：

f(1000) = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1

现在状态是：

0 0 0 1

接下来的三次更新返回三个 0 位并给出以下状态值：

0 0 1 1
0 1 1 0
1 1 0 0

我们因此在五次迭代后返回到初始状态 1100；从在此循环中观察到的任何值开始更新状态五次

会使我们返回到该初始值。我们说 5 是给定 1100、1000、0001、0011 或 0110 中任一值的 FSR 的周期。因为该 FSR 的周期为 5，时钟寄存器 10 次会产生两次相同的 5 位序列。同样，如果你从 1100 开始时钟寄存器 20 次，输出位将为 11000110001100011000，即四次相同的 5 位序列 11000。直观上，这种重复模式应避免，更长的周期对安全性更好。

注意 如果你计划在流密码中使用 FSR，避免使用周期短的 FSR，因为这会使输出更可预测。对于某些类型的 FSR，很容易弄清其周期，但对于其他类型则几乎不可能。

图 5-4 显示了该循环的结构，以及该 FSR 的其他循环，每个循环都是一个圆圈，其点代表寄存器的一个状态。

![](img/ace4de942d037de8ea5835bc9fbe57cd_119_0.png)

图 5-4：反馈函数对 4 个位进行异或的 FSR 的循环

事实上，这个特定的 FSR 还有另外两个周期为 5 的循环——{0100, 1001, 0010, 0101, 1010} 和 {1111, 1110, 1101, 1011, 0111}。请注意，任何给定状态只能属于一个状态循环。在这里，我们有三个每个包含五个状态的循环，覆盖了我们 4 位寄存器 2^4 = 16 个可能值中的 15 个。第 16 个可能值是 0000，如图 5-4 所示，它是一个周期为 1 的循环，因为 FSR 将 0000 变换为 0000。

FSR 本质上是一个位寄存器，其中每次寄存器的更新都会输出一位（寄存器的最左位），并且一个函数计算寄存器的新最右位。（所有其他位都左移。）从某个初始状态开始的 FSR 的周期是 FSR 再次进入同一状态所需的更新次数。如果需要 N 次更新，则 FSR 将再次产生相同的 N 位。

## 线性反馈移位寄存器

*线性反馈移位寄存器 (LFSRs)* 是具有线性反馈函数的 FSR——即对状态的某些位进行异或的函数，例如上一节中 4 位 FSR 的示例及其反馈函数返回寄存器的 4 个位的异或。回想一下，在密码学中，线性与可预测性同义，并暗示存在简单的底层数学结构。而且，正如你可能预期的那样，由于这种线性，我们可以使用线性复杂度、有限域和本原多项式等概念来分析 LFSRs——但我将跳过数学细节，只给你必要的事实。

> **注意**  
> *在线性代数中，我们定义线性变换* f *为满足* f(u + v) = f(u) + f(v) *的函数。*如果你知道* f(u) *和* f(v)，*你就可以在不知道* u *或* v *的情况下确定* f(u + v)。*对于非线性函数，情况要复杂得多；你无法轻易从* f(u) *和* f(v) *找到* f(u + v)。

选择要一起异或的位对 LFSR 的周期至关重要，从而对其密码学价值至关重要。好消息是我们知道如何选择位的[content]
是一种在位级别实现加密算法的电子电路，且不能用于其他任何用途；换句话说，该电路是*专用硬件*。另一方面，加密算法的软件实现只是告诉微处理器执行哪些指令以运行算法。这些指令操作字节或字，然后调用实现通用操作（如加法和乘法）的电子电路部件。软件处理的是 32 或 64 位的字节或字，而硬件处理的是位。最早的流密码使用位来节省复杂的按字操作，从而在硬件上更高效，当时硬件是其目标平台。

流密码主要用于硬件实现，因为它们比分组密码更便宜。它们需要的内存和逻辑门比分组密码少，因此在集成电路上占用的面积更小，从而降低了制造成本。例如，按门当量计数，集成电路的标准面积度量，你可以找到流密码占用不到 1,000 个门当量；而相比之下，典型的面向软件的分组密码至少需要 10,000 个门当量，使得加密的成本比使用流密码高出一个数量级。

然而，今天分组密码不再比流密码更昂贵——首先，因为现在有硬件友好的分组密码，其大小与流密码相当，其次，因为硬件成本已经大幅下降。尽管如此，流密码通常与硬件相关联，因为它们曾经是最好的选择。

在下一节中，我将解释硬件流密码背后的基本机制，称为*反馈移位寄存器 (FSRs)*。几乎所有硬件流密码都以某种方式依赖于 FSRs，无论是用于 2G 手机的 A5/1 密码，还是更新的 Grain-128a 密码。

> **注意**  
> *第一个标准分组密码，即数据加密标准（DES），是为硬件而非软件优化的。当美国政府在 1970 年代标准化 DES 时，大多数目标应用都是硬件实现。因此，DES 中的 S 盒在硬件中实现为逻辑电路时体积小、计算速度快，但在软件中效率低下也就不足为奇了。与 DES 不同，当前的高级加密标准（AES）处理的是字节，因此在软件中比 DES 更高效。*

## 反馈移位寄存器

无数流密码使用 FSRs，因为它们简单且已被充分理解。FSR 是一组配备更新*反馈函数*的位，我将其记为 f。FSR 的状态存储在该数组或寄存器中，并且 FSR 的每次*更新*都使用反馈函数来改变状态的值并产生一个输出位。

实际上，FSR 的工作方式如下：如果 R₀ 是 FSR 的初始值，则下一个状态 R₁ 定义为 R₀ 左移 1 位，其中离开寄存器的位作为输出返回，而空出的位置用 f(R₀) 填充。

我们重复相同的规则来计算后续状态值 R₂、R₃，等等。也就是说，给定时间 t 时 FSR 的状态 Rₜ，下一个状态 Rₜ₊₁ 为：

Rₜ₊₁ = (Rₜ << 1) | f(Rₜ)

在此方程中，| 是逻辑或运算符，<< 是移位运算符，如 C 语言中使用。例如，给定 8 位字符串 00001111，我们有：

00001111 << 1 = 00011110
00011110 << 1 = 00111100
00111100 << 1 = 01111000

位移将位向左移动，丢失最左边的位以保留状态的位长度，并将最右边的位清零。FSR 的更新操作是相同的，只是最右边的位不是设为 0，而是设为 f(Rₜ)。

例如，考虑一个反馈函数 f 对 4 个位全部进行异或的 4 位 FSR。将状态初始化为以下值：

1 1 0 0

现在将位向左移动，其中 1 被输出且最右边的位被设为以下值：

f(1100) = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0

现在状态变为：

1 0 0 0

下一次更新输出 1，左移状态，并将最右边的位设为以下值：

f(1000) = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1

现在状态是：

0 0 0 1

接下来的三次更新返回三个 0 位并给出以下状态值：

0 0 1 1
0 1 1 0
1 1 0 0

我们因此在五次迭代后返回到初始状态 1100；从在此循环中观察到的任何值开始更新状态五次

会使我们返回到该初始值。我们说 5 是给定 1100、1000、0001、0011 或 0110 中任一值的 FSR 的周期。因为该 FSR 的周期为 5，时钟寄存器 10 次会产生两次相同的 5 位序列。同样，如果你从 1100 开始时钟寄存器 20 次，输出位将为 11000110001100011000，即四次相同的 5 位序列 11000。直观上，这种重复模式应避免，更长的周期对安全性更好。

注意 如果你计划在流密码中使用 FSR，避免使用周期短的 FSR，因为这会使输出更可预测。对于某些类型的 FSR，很容易弄清其周期，但对于其他类型则几乎不可能。

图 5-4 显示了该循环的结构，以及该 FSR 的其他循环，每个循环都是一个圆圈，其点代表寄存器的一个状态。

![](img/ace4de942d037de8ea5835bc9fbe57cd_119_0.png)

图 5-4：反馈函数对 4 个位进行异或的 FSR 的循环

事实上，这个特定的 FSR 还有另外两个周期为 5 的循环——{0100, 1001, 0010, 0101, 1010} 和 {1111, 1110, 1101, 1011, 0111}。请注意，任何给定状态只能属于一个状态循环。在这里，我们有三个每个包含五个状态的循环，覆盖了我们 4 位寄存器 2^4 = 16 个可能值中的 15 个。第 16 个可能值是 0000，如图 5-4 所示，它是一个周期为 1 的循环，因为 FSR 将 0000 变换为 0000。

FSR 本质上是一个位寄存器，其中每次寄存器的更新都会输出一位（寄存器的最左位），并且一个函数计算寄存器的新最右位。（所有其他位都左移。）从某个初始状态开始的 FSR 的周期是 FSR 再次进入同一状态所需的更新次数。如果需要 N 次更新，则 FSR 将再次产生相同的 N 位。

## 线性反馈移位寄存器

*线性反馈移位寄存器 (LFSRs)* 是具有线性反馈函数的 FSR——即对状态的某些位进行异或的函数，例如上一节中 4 位 FSR 的示例及其反馈函数返回寄存器的 4 个位的异或。回想一下，在密码学中，线性与可预测性同义，并暗示存在简单的底层数学结构。而且，正如你可能预期的那样，由于这种线性，我们可以使用线性复杂度、有限域和本原多项式等概念来分析 LFSRs——但我将跳过数学细节，只给你必要的事实。

> **注意**  
> *在线性代数中，我们定义线性变换* f *为满足* f(u + v) = f(u) + f(v) *的函数。*如果你知道* f(u) *和* f(v)，*你就可以在不知道* u *或* v *的情况下确定* f(u + v)。*对于非线性函数，情况要复杂得多；你无法轻易从* f(u) *和* f(v) *找到* f(u + v)。

选择要一起异或的位对 LFSR 的周期至关重要，从而对其密码学价值至关重要。好消息是我们知道如何选择位的[content]
是一种在位级别实现加密算法的电子电路，且不能用于其他任何用途；换句话说，该电路是*专用硬件*。另一方面，加密算法的软件实现只是告诉微处理器执行哪些指令以运行算法。这些指令操作字节或字，然后调用实现通用操作（如加法和乘法）的电子电路部件。软件处理的是 32 或 64 位的字节或字，而硬件处理的是位。最早的流密码使用位来节省复杂的按字操作，从而在硬件上更高效，当时硬件是其目标平台。

流密码主要用于硬件实现，因为它们比分组密码更便宜。它们需要的内存和逻辑门比分组密码少，因此在集成电路上占用的面积更小，从而降低了制造成本。例如，按门当量计数，集成电路的标准面积度量，你可以找到流密码占用不到 1,000 个门当量；而相比之下，典型的面向软件的分组密码至少需要 10,000 个门当量，使得加密的成本比使用流密码高出一个数量级。

然而，今天分组密码不再比流密码更昂贵——首先，因为现在有硬件友好的分组密码，其大小与流密码相当，其次，因为硬件成本已经大幅下降。尽管如此，流密码通常与硬件相关联，因为它们曾经是最好的选择。

在下一节中，我将解释硬件流密码背后的基本机制，称为*反馈移位寄存器 (FSRs)*。几乎所有硬件流密码都以某种方式依赖于 FSRs，无论是用于 2G 手机的 A5/1 密码，还是更新的 Grain-128a 密码。

> **注意**  
> *第一个标准分组密码，即数据加密标准（DES），是为硬件而非软件优化的。当美国政府在 1970 年代标准化 DES 时，大多数目标应用都是硬件实现。因此，DES 中的 S 盒在硬件中实现为逻辑电路时体积小、计算速度快，但在软件中效率低下也就不足为奇了。与 DES 不同，当前的高级加密标准（AES）处理的是字节，因此在软件中比 DES 更高效。*

## 反馈移位寄存器

无数流密码使用 FSRs，因为它们简单且已被充分理解。FSR 是一组配备更新*反馈函数*的位，我将其记为 f。FSR 的状态存储在该数组或寄存器中，并且 FSR 的每次*更新*都使用反馈函数来改变状态的值并产生一个输出位。

实际上，FSR 的工作方式如下：如果 R₀ 是 FSR 的初始值，则下一个状态 R₁ 定义为 R₀ 左移 1 位，其中离开寄存器的位作为输出返回，而空出的位置用 f(R₀) 填充。

我们重复相同的规则来计算后续状态值 R₂、R₃，等等。也就是说，给定时间 t 时 FSR 的状态 Rₜ，下一个状态 Rₜ₊₁ 为：

Rₜ₊₁ = (Rₜ << 1) | f(Rₜ)

在此方程中，| 是逻辑或运算符，<< 是移位运算符，如 C 语言中使用。例如，给定 8 位字符串 00001111，我们有：

00001111 << 1 = 00011110
00011110 << 1 = 00111100
00111100 << 1 = 01111000

位移将位向左移动，丢失最左边的位以保留状态的位长度，并将最右边的位清零。FSR 的更新操作是相同的，只是最右边的位不是设为 0，而是设为 f(Rₜ)。

例如，考虑一个反馈函数 f 对 4 个位全部进行异或的 4 位 FSR。将状态初始化为以下值：

1 1 0 0

现在将位向左移动，其中 1 被输出且最右边的位被设为以下值：

f(1100) = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0

现在状态变为：

1 0 0 0

下一次更新输出 1，左移状态，并将最右边的位设为以下值：

f(1000) = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1

现在状态是：

0 0 0 1

接下来的三次更新返回三个 0 位并给出以下状态值：

0 0 1 1
0 1 1 0
1 1 0 0

我们因此在五次迭代后返回到初始状态 1100；从在此循环中观察到的任何值开始更新状态五次

会使我们返回到该初始值。我们说 5 是给定 1100、1000、0001、0011 或 0110 中任一值的 FSR 的周期。因为该 FSR 的周期为 5，时钟寄存器 10 次会产生两次相同的 5 位序列。同样，如果你从 1100 开始时钟寄存器 20 次，输出位将为 11000110001100011000，即四次相同的 5 位序列 11000。直观上，这种重复模式应避免，更长的周期对安全性更好。

注意 如果你计划在流密码中使用 FSR，避免使用周期短的 FSR，因为这会使输出更可预测。对于某些类型的 FSR，很容易弄清其周期，但对于其他类型则几乎不可能。

图 5-4 显示了该循环的结构，以及该 FSR 的其他循环，每个循环都是一个圆圈，其点代表寄存器的一个状态。

![](img/ace4de942d037de8ea5835bc9fbe57cd_119_0.png)

图 5-4：反馈函数对 4 个位进行异或的 FSR 的循环

事实上，这个特定的 FSR 还有另外两个周期为 5 的循环——{0100, 1001, 0010, 0101, 1010} 和 {1111, 1110, 1101, 1011, 0111}。请注意，任何给定状态只能属于一个状态循环。在这里，我们有三个每个包含五个状态的循环，覆盖了我们 4 位寄存器 2^4 = 16 个可能值中的 15 个。第 16 个可能值是 0000，如图 5-4 所示，它是一个周期为 1 的循环，因为 FSR 将 0000 变换为 0000。

FSR 本质上是一个位寄存器，其中每次寄存器的更新都会输出一位（寄存器的最左位），并且一个函数计算寄存器的新最右位。（所有其他位都左移。）从某个初始状态开始的 FSR 的周期是 FSR 再次进入同一状态所需的更新次数。如果需要 N 次更新，则 FSR 将再次产生相同的 N 位。

## 线性反馈移位寄存器

*线性反馈移位寄存器 (LFSRs)* 是具有线性反馈函数的 FSR——即对状态的某些位进行异或的函数，例如上一节中 4 位 FSR 的示例及其反馈函数返回寄存器的 4 个位的异或。回想一下，在密码学中，线性与可预测性同义，并暗示存在简单的底层数学结构。而且，正如你可能预期的那样，由于这种线性，我们可以使用线性复杂度、有限域和本原多项式等概念来分析 LFSRs——但我将跳过数学细节，只给你必要的事实。

> **注意**  
> *在线性代数中，我们定义线性变换* f *为满足* f(u + v) = f(u) + f(v) *的函数。*如果你知道* f(u) *和* f(v)，*你就可以在不知道* u *或* v *的情况下确定* f(u + v)。*对于非线性函数，情况要复杂得多；你无法轻易从* f(u) *和* f(v) *找到* f(u + v)。

选择要一起异或的位对 LFSR 的周期至关重要，从而对其密码学价值至关重要。好消息是我们知道如何选择位的[content]
是一种在位级别实现加密算法的电子电路，且不能用于其他任何用途；换句话说，该电路是*专用硬件*。另一方面，加密算法的软件实现只是告诉微处理器执行哪些指令以运行算法。这些指令操作字节或字，然后调用实现通用操作（如加法和乘法）的电子电路部件。软件处理的是 32 或 64 位的字节或字，而硬件处理的是位。最早的流密码使用位来节省复杂的按字操作，从而在硬件上更高效，当时硬件是其目标平台。

流密码主要用于硬件实现，因为它们比分组密码更便宜。它们需要的内存和逻辑门比分组密码少，因此在集成电路上占用的面积更小，从而降低了制造成本。例如，按门当量计数，集成电路的标准面积度量，你可以找到流密码占用不到 1,000 个门当量；而相比之下，典型的面向软件的分组密码至少需要 10,000 个门当量，使得加密的成本比使用流密码高出一个数量级。

然而，今天分组密码不再比流密码更昂贵——首先，因为现在有硬件友好的分组密码，其大小与流密码相当，其次，因为硬件成本已经大幅下降。尽管如此，流密码通常与硬件相关联，因为它们曾经是最好的选择。

在下一节中，我将解释硬件流密码背后的基本机制，称为*反馈移位寄存器 (FSRs)*。几乎所有硬件流密码都以某种方式依赖于 FSRs，无论是用于 2G 手机的 A5/1 密码，还是更新的 Grain-128a 密码。

> **注意**  
> *第一个标准分组密码，即数据加密标准（DES），是为硬件而非软件优化的。当美国政府在 1970 年代标准化 DES 时，大多数目标应用都是硬件实现。因此，DES 中的 S 盒在硬件中实现为逻辑电路时体积小、计算速度快，但在软件中效率低下也就不足为奇了。与 DES 不同，当前的高级加密标准（AES）处理的是字节，因此在软件中比 DES 更高效。*

## 反馈移位寄存器

无数流密码使用 FSRs，因为它们简单且已被充分理解。FSR 是一组配备更新*反馈函数*的位，我将其记为 f。FSR 的状态存储在该数组或寄存器中，并且 FSR 的每次*更新*都使用反馈函数来改变状态的值并产生一个输出位。

实际上，FSR 的工作方式如下：如果 R₀ 是 FSR 的初始值，则下一个状态 R₁ 定义为 R₀ 左移 1 位，其中离开寄存器的位作为输出返回，而空出的位置用 f(R₀) 填充。

我们重复相同的规则来计算后续状态值 R₂、R₃，等等。也就是说，给定时间 t 时 FSR 的状态 Rₜ，下一个状态 Rₜ₊₁ 为：

Rₜ₊₁ = (Rₜ << 1) | f(Rₜ)

在此方程中，| 是逻辑或运算符，<< 是移位运算符，如 C 语言中使用。例如，给定 8 位字符串 00001111，我们有：

00001111 << 1 = 00011110
00011110 << 1 = 00111100
00111100 << 1 = 01111000

位移将位向左移动，丢失最左边的位以保留状态的位长度，并将最右边的位清零。FSR 的更新操作是相同的，只是最右边的位不是设为 0，而是设为 f(Rₜ)。

例如，考虑一个反馈函数 f 对 4 个位全部进行异或的 4 位 FSR。将状态初始化为以下值：

1 1 0 0

现在将位向左移动，其中 1 被输出且最右边的位被设为以下值：

f(1100) = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0

现在状态变为：

1 0 0 0

下一次更新输出 1，左移状态，并将最右边的位设为以下值：

f(1000) = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1

现在状态是：

0 0 0 1

接下来的三次更新返回三个 0 位并给出以下状态值：

0 0 1 1
0 1 1 0
1 1 0 0

我们因此在五次迭代后返回到初始状态 1100；从在此循环中观察到的任何值开始更新状态五次

会使我们返回到该初始值。我们说 5 是给定 1100、1000、0001、0011 或 0110 中任一值的 FSR 的周期。因为该 FSR 的周期为 5，时钟寄存器 10 次会产生两次相同的 5 位序列。同样，如果你从 1100 开始时钟寄存器 20 次，输出位将为 11000110001100011000，即四次相同的 5 位序列 11000。直观上，这种重复模式应避免，更长的周期对安全性更好。

注意 如果你计划在流密码中使用 FSR，避免使用周期短的 FSR，因为这会使输出更可预测。对于某些类型的 FSR，很容易弄清其周期，但对于其他类型则几乎不可能。

图 5-4 显示了该循环的结构，以及该 FSR 的其他循环，每个循环都是一个圆圈，其点代表寄存器的一个状态。

![](img/ace4de942d037de8ea5835bc9fbe57cd_119_0.png)

图 5-4：反馈函数对 4 个位进行异或的 FSR 的循环

事实上，这个特定的 FSR 还有另外两个周期为 5 的循环——{0100, 1001, 0010, 0101, 1010} 和 {1111, 1110, 1101, 1011, 0111}。请注意，任何给定状态只能属于一个状态循环。在这里，我们有三个每个包含五个状态的循环，覆盖了我们 4 位寄存器 2^4 = 16 个可能值中的 15 个。第 16 个可能值是 0000，如图 5-4 所示，它是一个周期为 1 的循环，因为 FSR 将 0000 变换为 0000。

FSR 本质上是一个位寄存器，其中每次寄存器的更新都会输出一位（寄存器的最左位），并且一个函数计算寄存器的新最右位。（所有其他位都左移。）从某个初始状态开始的 FSR 的周期是 FSR 再次进入同一状态所需的更新次数。如果需要 N 次更新，则 FSR 将再次产生相同的 N 位。

## 线性反馈移位寄存器

*线性反馈移位寄存器 (LFSRs)* 是具有线性反馈函数的 FSR——即对状态的某些位进行异或的函数，例如上一节中 4 位 FSR 的示例及其反馈函数返回寄存器的 4 个位的异或。回想一下，在密码学中，线性与可预测性同义，并暗示存在简单的底层数学结构。而且，正如你可能预期的那样，由于这种线性，我们可以使用线性复杂度、有限域和本原多项式等概念来分析 LFSRs——但我将跳过数学细节，只给你必要的事实。

> **注意**  
> *在线性代数中，我们定义线性变换* f *为满足* f(u + v) = f(u) + f(v) *的函数。*如果你知道* f(u) *和* f(v)，*你就可以在不知道* u *或* v *的情况下确定* f(u + v)。*对于非线性函数，情况要复杂得多；你无法轻易从* f(u) *和* f(v) *找到* f(u + v)。

选择要一起异或的位对 LFSR 的周期至关重要，从而对其密码学价值至关重要。好消息是我们知道如何选择位的[content]
是一种在位级别实现加密算法的电子电路，且不能用于其他任何用途；换句话说，该电路是*专用硬件*。另一方面，加密算法的软件实现只是告诉微处理器执行哪些指令以运行算法。这些指令操作字节或字，然后调用实现通用操作（如加法和乘法）的电子电路部件。软件处理的是 32 或 64 位的字节或字，而硬件处理的是位。最早的流密码使用位来节省复杂的按字操作，从而在硬件上更高效，当时硬件是其目标平台。

流密码主要用于硬件实现，因为它们比分组密码更便宜。它们需要的内存和逻辑门比分组密码少，因此在集成电路上占用的面积更小，从而降低了制造成本。例如，按门当量计数，集成电路的标准面积度量，你可以找到流密码占用不到 1,000 个门当量；而相比之下，典型的面向软件的分组密码至少需要 10,000 个门当量，使得加密的成本比使用流密码高出一个数量级。

然而，今天分组密码不再比流密码更昂贵——首先，因为现在有硬件友好的分组密码，其大小与流密码相当，其次，因为硬件成本已经大幅下降。尽管如此，流密码通常与硬件相关联，因为它们曾经是最好的选择。

在下一节中，我将解释硬件流密码背后的基本机制，称为*反馈移位寄存器 (FSRs)*。几乎所有硬件流密码都以某种方式依赖于 FSRs，无论是用于 2G 手机的 A5/1 密码，还是更新的 Grain-128a 密码。

> **注意**  
> *第一个标准分组密码，即数据加密标准（DES），是为硬件而非软件优化的。当美国政府在 1970 年代标准化 DES 时，大多数目标应用都是硬件实现。因此，DES 中的 S 盒在硬件中实现为逻辑电路时体积小、计算速度快，但在软件中效率低下也就不足为奇了。与 DES 不同，当前的高级加密标准（AES）处理的是字节，因此在软件中比 DES 更高效。*

## 反馈移位寄存器

无数流密码使用 FSRs，因为它们简单且已被充分理解。FSR 是一组配备更新*反馈函数*的位，我将其记为 f。FSR 的状态存储在该数组或寄存器中，并且 FSR 的每次*更新*都使用反馈函数来改变状态的值并产生一个输出位。

实际上，FSR 的工作方式如下：如果 R₀ 是 FSR 的初始值，则下一个状态 R₁ 定义为 R₀ 左移 1 位，其中离开寄存器的位作为输出返回，而空出的位置用 f(R₀) 填充。

我们重复相同的规则来计算后续状态值 R₂、R₃，等等。也就是说，给定时间 t 时 FSR 的状态 Rₜ，下一个状态 Rₜ₊₁ 为：

Rₜ₊₁ = (Rₜ << 1) | f(Rₜ)

在此方程中，| 是逻辑或运算符，<< 是移位运算符，如 C 语言中使用。例如，给定 8 位字符串 00001111，我们有：

00001111 << 1 = 00011110
00011110 << 1 = 00111100
00111100 << 1 = 01111000

位移将位向左移动，丢失最左边的位以保留状态的位长度，并将最右边的位清零。FSR 的更新操作是相同的，只是最右边的位不是设为 0，而是设为 f(Rₜ)。

例如，考虑一个反馈函数 f 对 4 个位全部进行异或的 4 位 FSR。将状态初始化为以下值：

1 1 0 0

现在将位向左移动，其中 1 被输出且最右边的位被设为以下值：

f(1100) = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0

现在状态变为：

1 0 0 0

下一次更新输出 1，左移状态，并将最右边的位设为以下值：

f(1000) = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1

现在状态是：

0 0 0 1

接下来的三次更新返回三个 0 位并给出以下状态值：

0 0 1 1
0 1 1 0
1 1 0 0

我们因此在五次迭代后返回到初始状态 1100；从在此循环中观察到的任何值开始更新状态五次

会使我们返回到该初始值。我们说 5 是给定 1100、1000、0001、0011 或 0110 中任一值的 FSR 的周期。因为该 FSR 的周期为 5，时钟寄存器 10 次会产生两次相同的 5 位序列。同样，如果你从 1100 开始时钟寄存器 20 次，输出位将为 11000110001100011000，即四次相同的 5 位序列 11000。直观上，这种重复模式应避免，更长的周期对安全性更好。

注意 如果你计划在流密码中使用 FSR，避免使用周期短的 FSR，因为这会使输出更可预测。对于某些类型的 FSR，很容易弄清其周期，但对于其他类型则几乎不可能。

图 5-4 显示了该循环的结构，以及该 FSR 的其他循环，每个循环都是一个圆圈，其点代表寄存器的一个状态。

![](img/ace4de942d037de8ea5835bc9fbe57cd_119_0.png)

图 5-4：反馈函数对 4 个位进行异或的 FSR 的循环

事实上，这个特定的 FSR 还有另外两个周期为 5 的循环——{0100, 1001, 0010, 0101, 1010} 和 {1111, 1110, 1101, 1011, 0111}。请注意，任何给定状态只能属于一个状态循环。在这里，我们有三个每个包含五个状态的循环，覆盖了我们 4 位寄存器 2^4 = 16 个可能值中的 15 个。第 16 个可能值是 0000，如图 5-4 所示，它是一个周期为 1 的循环，因为 FSR 将 0000 变换为 0000。

FSR 本质上是一个位寄存器，其中每次寄存器的更新都会输出一位（寄存器的最左位），并且一个函数计算寄存器的新最右位。（所有其他位都左移。）从某个初始状态开始的 FSR 的周期是 FSR 再次进入同一状态所需的更新次数。如果需要 N 次更新，则 FSR 将再次产生相同的 N 位。

## 线性反馈移位寄存器

*线性反馈移位寄存器 (LFSRs)* 是具有线性反馈函数的 FSR——即对状态的某些位进行异或的函数，例如上一节中 4 位 FSR 的示例及其反馈函数返回寄存器的 4 个位的异或。回想一下，在密码学中，线性与可预测性同义，并暗示存在简单的底层数学结构。而且，正如你可能预期的那样，由于这种线性，我们可以使用线性复杂度、有限域和本原多项式等概念来分析 LFSRs——但我将跳过数学细节，只给你必要的事实。

> **注意**  
> *在线性代数中，我们定义线性变换* f *为满足* f(u + v) = f(u) + f(v) *的函数。*如果你知道* f(u) *和* f(v)，*你就可以在不知道* u *或* v *的情况下确定* f(u + v)。*对于非线性函数，情况要复杂得多；你无法轻易从* f(u) *和* f(v) *找到* f(u + v)。

选择要一起异或的位对 LFSR 的周期至关重要，从而对其密码学价值至关重要。好消息是我们知道如何选择位的[content]
是一种在位级别实现加密算法的电子电路，且不能用于其他任何用途；换句话说，该电路是*专用硬件*。另一方面，加密算法的软件实现只是告诉微处理器执行哪些指令以运行算法。这些指令操作字节或字，然后调用实现通用操作（如加法和乘法）的电子电路部件。软件处理的是 32 或 64 位的字节或字，而硬件处理的是位。最早的流密码使用位来节省复杂的按字操作，从而在硬件上更高效，当时硬件是其目标平台。

流密码主要用于硬件实现，因为它们比分组密码更便宜。它们需要的内存和逻辑门比分组密码少，因此在集成电路上占用的面积更小，从而降低了制造成本。例如，按门当量计数，集成电路的标准面积度量，你可以找到流密码占用不到 1,000 个门当量；而相比之下，典型的面向软件的分组密码至少需要 10,000 个门当量，使得加密的成本比使用流密码高出一个数量级。

然而，今天分组密码不再比流密码更昂贵——首先，因为现在有硬件友好的分组密码，其大小与流密码相当，其次，因为硬件成本已经大幅下降。尽管如此，流密码通常与硬件相关联，因为它们曾经是最好的选择。

在下一节中，我将解释硬件流密码背后的基本机制，称为*反馈移位寄存器 (FSRs)*。几乎所有硬件流密码都以某种方式依赖于 FSRs，无论是用于 2G 手机的 A5/1 密码，还是更新的 Grain-128a 密码。

> **注意**  
> *第一个标准分组密码，即数据加密标准（DES），是为硬件而非软件优化的。当美国政府在 1970 年代标准化 DES 时，大多数目标应用都是硬件实现。因此，DES 中的 S 盒在硬件中实现为逻辑电路时体积小、计算速度快，但在软件中效率低下也就不足为奇了。与 DES 不同，当前的高级加密标准（AES）处理的是字节，因此在软件中比 DES 更高效。*

## 反馈移位寄存器

无数流密码使用 FSRs，因为它们简单且已被充分理解。FSR 是一组配备更新*反馈函数*的位，我将其记为 f。FSR 的状态存储在该数组或寄存器中，并且 FSR 的每次*更新*都使用反馈函数来改变状态的值并产生一个输出位。

实际上，FSR 的工作方式如下：如果 R₀ 是 FSR 的初始值，则下一个状态 R₁ 定义为 R₀ 左移 1 位，其中离开寄存器的位作为输出返回，而空出的位置用 f(R₀) 填充。

我们重复相同的规则来计算后续状态值 R₂、R₃，等等。也就是说，给定时间 t 时 FSR 的状态 Rₜ，下一个状态 Rₜ₊₁ 为：

Rₜ₊₁ = (Rₜ << 1) | f(Rₜ)

在此方程中，| 是逻辑或运算符，<< 是移位运算符，如 C 语言中使用。例如，给定 8 位字符串 00001111，我们有：

00001111 << 1 = 00011110
00011110 << 1 = 00111100
00111100 << 1 = 01111000

位移将位向左移动，丢失最左边的位以保留状态的位长度，并将最右边的位清零。FSR 的更新操作是相同的，只是最右边的位不是设为 0，而是设为 f(Rₜ)。

例如，考虑一个反馈函数 f 对 4 个位全部进行异或的 4 位 FSR。将状态初始化为以下值：

1 1 0 0

现在将位向左移动，其中 1 被输出且最右边的位被设为以下值：

f(1100) = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0

现在状态变为：

1 0 0 0

下一次更新输出 1，左移状态，并将最右边的位设为以下值：

f(1000) = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1

现在状态是：

0 0 0 1

接下来的三次更新返回三个 0 位并给出以下状态值：

0 0 1 1
0 1 1 0
1 1 0 0

我们因此在五次迭代后返回到初始状态 1100；从在此循环中观察到的任何值开始更新状态五次

会使我们返回到该初始值。我们说 5 是给定 1100、1000、0001、0011 或 0110 中任一值的 FSR 的周期。因为该 FSR 的周期为 5，时钟寄存器 10 次会产生两次相同的 5 位序列。同样，如果你从 1100 开始时钟寄存器 20 次，输出位将为 11000110001100011000，即四次相同的 5 位序列 11000。直观上，这种重复模式应避免，更长的周期对安全性更好。

注意 如果你计划在流密码中使用 FSR，避免使用周期短的 FSR，因为这会使输出更可预测。对于某些类型的 FSR，很容易弄清其周期，但对于其他类型则几乎不可能。

图 5-4 显示了该循环的结构，以及该 FSR 的其他循环，每个循环都是一个圆圈，其点代表寄存器的一个状态。

![](img/ace4de942d037de8ea5835bc9fbe57cd_119_0.png)

图 5-4：反馈函数对 4 个位进行异或的 FSR 的循环

事实上，这个特定的 FSR 还有另外两个周期为 5 的循环——{0100, 1001, 0010, 0101, 1010} 和 {1111, 1110, 1101, 1011, 0111}。请注意，任何给定状态只能属于一个状态循环。在这里，我们有三个每个包含五个状态的循环，覆盖了我们 4 位寄存器 2^4 = 16 个可能值中的 15 个。第 16 个可能值是 0000，如图 5-4 所示，它是一个周期为 1 的循环，因为 FSR 将 0000 变换为 0000。

FSR 本质上是一个位寄存器，其中每次寄存器的更新都会输出一位（寄存器的最左位），并且一个函数计算寄存器的新最右位。（所有其他位都左移。）从某个初始状态开始的 FSR 的周期是 FSR 再次进入同一状态所需的更新次数。如果需要 N 次更新，则 FSR 将再次产生相同的 N 位。

## 线性反馈移位寄存器

*线性反馈移位寄存器 (LFSRs)* 是具有线性反馈函数的 FSR——即对状态的某些位进行异或的函数，例如上一节中 4 位 FSR 的示例及其反馈函数返回寄存器的 4 个位的异或。回想一下，在密码学中，线性与可预测性同义，并暗示存在简单的底层数学结构。而且，正如你可能预期的那样，由于这种线性，我们可以使用线性复杂度、有限域和本原多项式等概念来分析 LFSRs——但我将跳过数学细节，只给你必要的事实。

> **注意**  
> *在线性代数中，我们定义线性变换* f *为满足* f(u + v) = f(u) + f(v) *的函数。*如果你知道* f(u) *和* f(v)，*你就可以在不知道* u *或* v *的情况下确定* f(u + v)。*对于非线性函数，情况要复杂得多；你无法轻易从* f(u) *和* f(v) *找到* f(u + v)。

选择要一起异或的位对 LFSR 的周期至关重要，从而对其密码学价值至关重要。好消息是我们知道如何选择位的[content]
是一种在位级实现加密算法且只能用于此目的的电子电路；换句话说，该电路是*专用硬件*。另一方面，加密算法的软件实现只是告诉微处理器执行哪些指令来运行算法。这些指令操作字节或字，再调用实现通用操作如加法和乘法的电子电路部件。软件处理 32 或 64 位的字节或字，而硬件处理位。最早的流密码使用位来避免复杂的按字操作，因而在硬件上更高效，当时硬件是其目标平台。

流密码主要用于硬件实现，因为它们比分组密码便宜。它们需要的内存和逻辑门更少，因而在集成电路上占面积更小，降低了制造成本。例如按门当量计，流密码可小于 1,000 门当量；而典型的面向软件的分组密码至少需要 10,000 门当量，使加密成本比使用流密码高一个数量级。

今天，分组密码不再比流密码更贵——一是已有与流密码大小相当的硬件友好分组密码，二是硬件成本大幅下降。尽管如此，流密码仍常与硬件关联，因为它们曾是最优选择。

下一节我将解释硬件流密码的基本机制，称为*反馈移位寄存器 (FSRs)*。几乎所有硬件流密码都以某种方式依赖 FSRs，无论是 2G 手机用的 A5/1，还是更新的 Grain-128a。

> **注意**  
> *第一个标准分组密码数据加密标准 DES 是为硬件而非软件优化的。美国政府在 1970 年代标准化 DES 时，大多数目标应用都是硬件实现。因此 DES 中的 S 盒在硬件逻辑电路中实现时体积小、计算快，但在软件中效率低也就不足为奇。与 DES 不同，当前的高级加密标准 AES 处理字节，因而在软件中比 DES 更高效。*

## 反馈移位寄存器

大量流密码使用 FSRs，因其简单且易于理解。FSR 是带更新*反馈函数*的位数组，我记为 f。FSR 的状态存于该数组或寄存器中，每次*更新*都用反馈函数改变状态值并产生一个输出位。

实际工作方式如下：若 R₀ 为初始值，则下一状态 R₁ 为 R₀ 左移 1 位，移出的位作为输出返回，空位用 f(R₀) 填补。

重复此规则可得 R₂、R₃ 等。给定时刻 t 的状态 Rₜ，下一状态 Rₜ₊₁ 为：

Rₜ₊₁ = (Rₜ << 1) | f(Rₜ)

其中 | 为逻辑或，<< 为 C 语言中的移位运算符。例如对 8 位串 00001111：

00001111 << 1 = 00011110
00011110 << 1 = 00111100
00111100 << 1 = 01111000

位移使位左移，丢弃最左位以保持位长，最右位清零。FSR 的更新相同，只是最右位设为 f(Rₜ) 而非 0。

例如，4 位 FSR 的反馈函数 f 对 4 位全部异或。初始状态：

1 1 0 0

左移，输出 1，最右位设为：

f(1100) = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0

状态变为：

1 0 0 0

下次更新输出 1，左移，最右位设为：

f(1000) = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1

状态为：

0 0 0 1

接下来三次更新输出三个 0，状态依次为：

0 0 1 1
0 1 1 0
1 1 0 0

五次迭代后回到初始状态 1100；从该循环中任一值出发更新五次均回到初始值。称 5 为 FSR 在 1100、1000、0001、0011 或 0110 下的周期。周期为 5 时，时钟 10 次产生两次相同的 5 位序列；从 1100 开始时钟 20 次，输出为 11000110001100011000，即四次相同的 5 位序列 11000。直观上应避免此类重复，周期越长安全性越好。

注意 若在流密码中使用 FSR，避免周期短的 FSR，因其使输出更可预测。某些 FSR 的周期易于求出，另一些则几乎不可能。

图 5-4 显示了该循环及该 FSR 的其他循环，每个循环为一个圆圈，点代表寄存器状态。

![](img/ace4de942d037de8ea5835bc9fbe57cd_119_0.png)

图 5-4：反馈函数对 4 位进行异或的 FSR 的循环

该 FSR 另有两组周期为 5 的循环——{0100, 1001, 0010, 0101, 1010} 和 {1111, 1110, 1101, 1011, 0111}。任一状态只能属于一个循环。这里有三个各含五状态的循环，覆盖 4 位寄存器 2^4=16 个可能值中的 15 个。第 16 个值 0000 如图 5-4 所示为周期 1 循环，因 FSR 将 0000 映射到自身。

FSR 本质上是位寄存器，每次更新输出最左位，并用函数计算新的最右位，其余位左移。从某初始状态起的周期是再次回到同一状态所需的更新次数。若需 N 次更新，则 FSR 会重复产生相同的 N 位。

## 线性反馈移位寄存器

*线性反馈移位寄存器 (LFSRs)* 是反馈函数为线性的 FSR，即对状态某些位进行异或的函数，如上一节 4 位 FSR 的例子，其反馈函数返回寄存器 4 位的异或。密码学中线性等同于可预测，暗示简单数学结构。正是由于线性，可用线性复杂度、有限域、本原多项式等分析 LFSRs——数学细节略过，只给出要点。

> **注意**  
> *在线性代数中，线性变换* f *满足* f(u + v) = f(u) + f(v)。*若已知* f(u) *和* f(v)，*可在不知* u *或* v *的情况下确定* f(u + v)。*非线性函数则复杂得多，无法轻易由* f(u) *和* f(v) *得到* f(u + v)。

选择异或的位对 LFSR 周期至关重要，从而影响其密码学价值。我们已知如何选择位位置以保证最大周期 $2^n - 1$。具体取位索引，最右为 1，最左为 $n$，写出多项式 $1 + X + X^2 + \ldots + X^n$，仅当第 i 位参与反馈异或时才包含项 $X^i$。周期最大*当且仅当*该多项式是*本原*的。本原多项式需满足：

- 多项式不可约，即不能写成更小多项式的乘积。例如 $X + X^3$ 不可约，因其等于 $(1 + X)(X + X^2)$：
  
  $(1 + X)(X + X^2) = X + X^2 + X^2 + X^3 = X + X^3$

- 满足若干其他数学性质，难以用非平凡概念解释但易于检验。

> **注意**  
> *n 位 LFSR 的最大周期是* $2^n - 1$，*不是* $2^n$，*因为全零状态会无限自循环。任意多个零的异或为零，反馈函数产生的新位始终为零，故全零状态会一直保持全零。*

例如，图 5-5 显示反馈多项式为 $1 + X + X^3 + X^4$ 的 4 位 LFSR，其中对位置 1、3、4 的位异或以计算新位 $L_1$。该多项式不是本原的，因可分解为 $(1 + X^3)(1 + X)$。



![img/ace4de942d037de8ea5835bc9fbe57cd_121_0.png](img/ace4de942d037de8ea5835bc9fbe57cd_121_0.png)

图 5-5：一个反馈多项式为 1 + X + X³ + X⁴ 的 LFSR

事实上，图 5-5 中 LFSR 的周期并不是最大的。为了证明这一点，从状态 0001 开始：

0 0 0 1

现在左移 1 位，并将新位设为 0 + 0 + 1 = 1：

0 0 1 1

再重复该操作五次，得到以下状态值：

0 1 1 1
1 1 0 0
1 0 0 0
0 0 0 1

经过六次更新后的状态与初始状态相同，这表明我们处于一个周期为 6 的循环中，并证明了该 LFSR 的周期不是最大值 15。

现在，让我们来看一个具有最大周期的 LFSR，即图 5-6 中的 LFSR。

![img/ace4de942d037de8ea5835bc9fbe57cd_121_1.png](img/ace4de942d037de8ea5835bc9fbe57cd_121_1.png)

图 5-6：一个反馈多项式为 1 + X³ + X⁴ 的 LFSR，该多项式为本原多项式，可确保最大周期

该反馈多项式是由 1 + X³ + X⁴ 描述的本原多项式，你可以验证其周期是最大的（即 15）。从某个初始值开始，状态演化如下（从 0001 到 0010、0100、1001、0011，依此类推）：

| 0 0 0 1 | 0 0 1 1 | 0 1 0 1 | 1 1 1 0 |
| 0 0 1 0 | 0 1 1 0 | 1 0 1 1 | 1 1 0 0 |
| 0 1 0 0 | 1 1 0 1 | 0 1 1 1 | 1 0 0 0 |
| 1 0 0 1 | 1 0 1 0 | 1 1 1 1 | 0 0 0 1 |

该状态覆盖除 0000 之外的所有可能值，且直到最终循环前没有重复。这表明其周期是最大的，且该反馈多项式是本原的。

遗憾的是，将 LFSR 用作流密码并不安全。如果 n 是 LFSR 的比特长度，攻击者只需 n 个输出比特就能恢复 LFSR 的初始状态，从而能够确定所有之前的比特并预测所有未来的比特。这种攻击之所以可行，是因为 LFSR 是线性的，这意味着状态比特之间的关系服从线性方程，而线性方程很容易求解。你可以使用 Berlekamp–Massey 算法来求解由 LFSR 的数学结构所定义的方程，从而不仅找到 LFSR 的初始状态，还能找到其反馈多项式。事实上，你甚至不需要知道 LFSR 的确切长度就能成功；你可以对 n 的所有可能取值重复运行 Berlekamp–Massey 算法，直到找到正确的那个。

结论是，LFSR 在密码学上是脆弱的，因为它们是线性的。输出比特与初始状态比特之间通过简单而简短的方程相关联，你可以用高中线性代数技巧来求解。为了增强 LFSR 的安全性，让我们加入一点非线性因素。

## 滤波 LFSR

为了缓解 LFSR 的不安全性，可以在输出比特返回之前，先通过一个非线性函数处理，从而隐藏其线性特性，产生一个滤波 LFSR，如图 5-7 所示。

![img/ace4de942d037de8ea5835bc9fbe57cd_122_0.png](img/ace4de942d037de8ea5835bc9fbe57cd_122_0.png)

图 5-7：一个滤波 LFSR

图 5-7 中的 g 函数必须是一个非线性函数——既能将比特进行异或，又能通过逻辑与或逻辑或运算来组合它们。例如，L1L2 + L3L4 就是一个非线性函数（我省略了乘号，因此 L1L2 表示 L1 × L2，或用 C 语法表示就是 L1 & L2）。

> 注意：你可以直接用 FSR 的比特来编写反馈函数，例如 L1L2 + L3L4，也可以使用等价的多项式记法 1 + XX² + X²X⁴。直接记法更容易理解，但多项式记法更便于对 FSR 的性质进行数学分析。除非我们关心其数学性质，否则我们将坚持使用直接记法。

滤波 LFSR 比普通 LFSR 更安全，因为其非线性函数能够阻止直接的攻击。尽管如此，以下更复杂的攻击仍会攻破该系统：

- **代数攻击**：求解从输出比特推导出的非线性方程组，其中的未知数是来自 LFSR 状态的比特。
- **立方攻击**：计算非线性方程的导数，将方程组的次数降至一次，然后像线性方程组一样高效求解。
- **快速相关攻击**：利用某些滤波函数——尽管它们是非线性的，但往往表现得像线性函数。

这里的教训，正如我们在前面的例子中所见，是创可贴无法修补弹孔。用一个稍强一点的层来修补一个已损坏的算法，并不能让整个系统变得安全。你必须从核心上解决问题。

## 非线性 FSR

*非线性 FSR（NFSR）与 LFSR 类似，但使用非线性反馈函数而非线性反馈函数。除了按位异或之外，其反馈函数还可以包含按位与和按位或运算——这一特性有利也有弊。*

加入非线性反馈函数的一个好处是，它使 NFSR 在密码学上比 LFSR 更强，因为输出比特以复杂的方式依赖于初始秘密状态，其方程规模呈指数级增长。LFSR 的线性函数使关系保持简单，最多只有 n 项（N₁, N₂, . . . , Nₙ，其中 N 表示 NFSR 的状态比特）。例如，一个 4 位 NFSR，其初始秘密状态为 (N₁, N₂, N₃, N₄)，反馈函数为 N₁ + N₂ + N₁N₂ + N₃N₄，产生的第一个输出比特如下：

N₁ + N₂ + N₁N₂ + N₃N₄

第二次迭代用这个新比特替换 N₁ 的值。用初始状态来表示第二个输出比特，我们得到如下方程：

(N₁ + N₂ + N₁N₂ + N₃N₄) + N₁ + (N₁ + N₂ + N₁N₂ + N₃N₄)N₁ + N₂N₃
= N₁ + N₂ + N₁N₂ + N₂N₃ + N₃N₄ + N₁N₃N₄

这个新方程的次数为 3（即相乘在一起的比特数的最大值，这里是 N₁N₃N₄），而不是反馈函数的次数 2，而且它包含六项而不是四项。因此，迭代这个非线性函数会很快产生难以处理的方程，因为输出规模呈指数增长。虽然运行 NFSR 时你永远不需要计算这些方程，但攻击者为了攻破系统，却必须求解它们。

NFSR 的一个缺点是，没有高效的方法来确定 NFSR 的周期，或者判断其周期是否为最大。对于 n 位的 NFSR，你需要运行接近 2^n 次试验才能验证其周期是否为最大。对于 80 位或更大的 NFSR，这种计算是不可能完成的。

幸运的是，有一种技巧可以让你在使用 NFSR 时不必担心短周期：你可以将 LFSR 和 NFSR 组合起来，既获得有保证的最大周期，又获得密码学强度——Grain-128a 正是这样工作的。

## Grain-128a

还记得第 4 章在讨论 AES 分组密码时提到的 AES 竞赛吗？流密码 Grain 是名为 eSTREAM 竞赛的类似项目的产物。该竞赛于 2008 年结束，并公布了一份推荐流密码的入围名单，其中包括四个面向硬件的密码和四个面向软件的密码。Grain 就是这些硬件密码之一，而 Grain-128a 是 Grain 原作者推出的升级版本。图 5-8 展示了 Grain-128a 的工作机制。

![img/ace4de942d037de8ea5835bc9fbe57cd_124_0.png](img/ace4de942d037de8ea5835bc9fbe57cd_124_0.png)

图 5-8：Grain-128a 的机制，包含一个 128 位 NFSR 和一个 128 位 LFSR

Grain-128a 可以说是尽可能简单的流密码，它组合了一个 128 位 LFSR、一个 128 位 NFSR 和一个滤波函数 h。该 LFSR 的最大周期为 2^128 – 1，这确保了整个系统的周期至少为 2^128 – 1，以防止 NFSR 中可能出现短周期。同时，NFSR 和非线性滤波函数 h 增加了密码学强度。

Grain-128a 使用一个 128 位密钥和一个 96 位临时值（nonce）。它将 128 位密钥复制到 NFSR 的 128 位中，将 96 位临时值复制到 LFSR 的前 96 位，并将剩余的 32 位填充为 1，最后再填充一个 0 位。初始化阶段会将整个系统更新 256 次，然后才返回第一个密钥流比特。在初始化期间，h 函数返回的比特因此不会作为密钥流输出，而是进入 LFSR，以确保其后续状态同时依赖于密钥和临时值。

Grain-128a 的 LFSR 反馈函数为

**f(L) = L₅₂ + L₄₇ + L₅₈ + L₉₀ + L₁₂₁ + L₁₂₈**

其中 L₁, L₂, . . . , L₁₂₈ 是 LFSR 的各个比特。这个反馈函数只从 128 位 LFSR 中取 6 个比特，但这足以得到一个能保证最大周期的本原多项式。较少的比特数最大限度地降低了硬件实现的成本。

以下是 Grain-128a 的 NFSR（N₁, . . . , N₁₂₈）的反馈多项式：

**g(N) = N₅₂ + N₅₇ + N₇₂ + N₁₀₂ + N₁₂₈ + N₄₄N₆₀ + N₆₁N₁₂₅ + N₆₃N₆₇ + N₆₉N₁₀₁ + N₈₀N₈₈ + N₁₁₀N₁₁₁ + N₁₁₅N₁₁₇ + N₄₆N₅₀N₅₈ + N₁₀₅N₁₀₄N₁₀₆ + N₃₃N₃₅N₃₆N₄₀**

该函数经过精心选择，在最小化实现成本的同时，最大化其密码学强度。它的代数次为 4，因为其变量最多的项包含四个变量（即 N₃₃N₃₅N₃₆N₄₀）。此外，g 高度非线性，无法用线性函数近似。另外，除了 g 之外，Grain-128a 还会将从 LFSR 输出的比特进行异或，并将结果作为 NFSR 新的最右端比特反馈回去。

滤波函数 h 是另一个非线性函数；它从 NFSR 取 9 个比特，从 LFSR 取 7 个比特，并以一种能确保良好密码学性质的方式将它们组合起来。

在我撰写本文时，还没有已知的针对 Grain-128a 的攻击，而且我相信它仍将是安全的。Grain-128a 被用于一些需要紧凑且快速的流密码的低端嵌入式系统——通常是工业专有系统——这就是为什么 Grain-128a 在开源软件社区中鲜为人知。

## A5/1

A5/1 是一种曾用于 2G 移动标准中加密语音通信的流密码。A5/1 标准创建于 1987 年，但直到 1990 年代末在被人逆向工程之后才公开。攻击出现在 2000 年代初，A5/1 最终被攻破，攻击方式能够实际（而非理论上）解密加密通信。让我们来看看原因和方式。

## A5/1 的机制

如图 5-9 所示，A5/1 依赖三个 LFSR，并使用了一种乍一看很巧妙但实际上并不安全的技巧。




![](img/ace4de942d037de8ea5835bc9fbe57cd_126_0.png)

图 5-9：A5/1 密码

A5/1 使用三个长度分别为 19、22 和 23 位的 LFSR，其各自的生成多项式如下：

```
1 + X^14 + X^17 + X^18 + X^19
1 + X^21 + X^22
1 + X^8 + X^21 + X^22 + X^23
```

仅使用 LFSR 而没有 NFSR，A5/1 怎么能被视为安全呢？诀窍在于 A5/1 的更新机制。A5/1 的设计者并没有在每个时钟周期都更新全部三个 LFSR，而是加入了一条时钟控制规则，其作用如下：

- 1. 检查 LFSR 1 的第 9 位、LFSR 2 的第 11 位和 LFSR 3 的第 11 位的值，这些位称为时钟位。在这 3 个位中，要么所有位都相同（1 或 0），要么两个位相同。
- 2. 对时钟位等于多数值（0 或 1）的寄存器进行时钟驱动。每次更新时，会驱动两个或三个 LFSR。

如果没有这条规则，A5/1 将毫无安全性可言，而绕过这条规则就足以破解该密码。然而，正如你将看到的，这说起来容易做起来难。

> **注意** 在 A5/1 的不规则时钟驱动规则中，每次更新时每个寄存器被时钟驱动的概率为 3/4。也就是说，至少有一个其他寄存器具有相同位值的概率为 1 - (1/2)^2，其中 (1/2)^2 是另外两个寄存器都具有不同位值的概率。

2G 通信使用 A5/1，其密钥为 64 位，随机数（nonce）为 22 位，且每个新数据帧都会改变该随机数。A5/1 的初始化机制首先将所有寄存器置零，然后将密钥以及随后的随机数逐位注入每个寄存器；每注入一位后，寄存器都会更新。之后，系统按照前述不规则规则更新 100 次。

对 A5/1 的攻击通过逆向初始化机制，恢复系统的 64 位初始状态（即 19 + 22 + 23 个 LFSR 的初始值），进而揭示随机数（若尚不知道）和密钥。这类攻击属于已知明文攻击（KPA），因为部分加密数据是已知的，攻击者可以通过将密文与已知明文分块进行异或运算，来确定相应的密钥流部分。

针对 A5/1 的攻击主要有两种类型：

- **巧妙攻击** 利用 A5/1 的内部线性和其简单的不规则时钟驱动系统。
- **暴力攻击** 仅利用 A5/1 的短密钥和帧号注入的可逆性。

让我们看看这些攻击是如何运作的。

## 巧妙攻击

我们将研究一种猜测-确定（guess-and-determine）巧妙攻击。在这种攻击中，攻击者猜测状态的某些秘密值，以确定其他值。在密码分析中，“猜测”意味着暴力破解：对于 LFSR 1 和 LFSR 2 的每个可能值，以及 LFSR 3 在前 11 个时钟周期内时钟位的所有可能值，攻击者通过求解依赖于所猜测位的方程来重建 LFSR 3 的位。当猜测正确时，攻击者就能得到 LFSR 3 的正确值。

该攻击的伪代码如下所示：

```
For all 2^19 values of LFSR 1's initial state
    For all 2^22 values of LFSR 2's initial state
        For all 2^11 values of LFSR 3's clocking bit during the first 11 clocks
            Reconstruct LFSR 3's initial state
            Test whether guess is correct; if yes, return; else continue
```

与第 3 章讨论的 2^64 次尝试的暴力搜索相比，这种攻击的效率如何？在最坏情况下，即算法只在最后一次测试时才成功，这种攻击最多执行 2^19 × 2^22 × 2^11 = 2^52 次操作。这比暴力搜索快 2^12 倍（约 4000 倍），前提是上述伪代码中的最后两个操作所需的计算量大约与在暴力搜索中测试一个 64 位密钥相当。但这个假设正确吗？

回顾一下我们在第 3 章中关于完整攻击成本的讨论。在评估攻击成本时，我们不仅需要考虑执行攻击所需的计算量，还需要考虑并行性和内存消耗。在这里，这两者都不是问题：与任何暴力攻击一样，猜测-确定攻击具有易并行性（在 N 个核心上运行速度快 N 倍），并且不需要比运行密码本身更多的内存。

我们的 2^52 攻击成本估算不准确还有一个原因。事实上，在 2^52 次操作（测试一个密钥候选）中，每次操作所需的时钟周期大约是暴力攻击中测试一个密钥时的四倍。结果是，与暴力攻击相比，这种特定攻击的实际成本更接近 4 × 2^52 = 2^54 次操作。

对 A5/1 的猜测-确定攻击可以解密加密的移动通信，但在专用硬件设备集群上运行时，恢复密钥需要几个小时。换句话说，这远非实时解密。为此，我们还有另一种类型的攻击。

## 暴力攻击

时间-内存权衡（TMTO）攻击是对 A5/1 的暴力攻击。这种攻击不关心 A5/1 的内部结构；它只关心其状态长度为 64 位。TMTO 攻击将 A5/1 视为一个黑盒，它接收一个 64 位值（状态），并输出一个 64 位值（前 64 个密钥流位）。

这种攻击背后的想法是，以使用大量内存为代价来降低暴力搜索的成本。最简单的 TMTO 类型是码本攻击（codebook attack），即预先计算一个包含 2^64 个元素的表，每个元素是键值对（key:value），并为 2^64 个可能的键存储对应的输出值。要使用这个预计算表进行攻击，只需收集一个 A5/1 实例的输出，然后在表中查找哪个键对应于该输出。攻击本身很快——只需在内存中查找一个值所需的时间——但创建该表需要 2^64 次 A5/1 计算。更糟糕的是，码本攻击需要极其惊人的内存量：2^64 × (64 + 64) 位，即 2^68 字节或 256 EB（exabytes）。这相当于数十个数据中心，所以我们还是忘了它吧。

TMTO 攻击以在线阶段增加计算量为代价，降低了码本攻击的内存需求。表越小，破解密钥所需的计算量就越大。无论如何，准备该表需要约 2^64 次操作，但这只需要做一次。

2010 年，研究人员使用图形处理单元（GPU）并行运行 10 万个 A5/1 实例，花了大约两个月时间生成了总容量为 2 TB 的表。借助如此庞大的表，使用 A5/1 加密的通话几乎可以实时解密。电信运营商已经实施了变通方案来缓解这种攻击，但真正的解决方案来自 3G 和 4G 移动电话标准，它们完全抛弃了 A5/1。

## 面向软件的流密码

软件流密码以字节或 32 位或 64 位字为单位工作，而不是以单个位为单位，这被证明在现代 CPU 上更为高效，因为在现代 CPU 中，指令对字执行算术运算所需的时间与对位执行运算所需的时间相同。因此，对于运行在个人计算机上的服务器或浏览器，软件流密码比硬件密码更适用，因为强大的通用处理器可以将密码作为本地软件运行。

如今，人们对软件流密码产生了相当大的兴趣，原因有几个。首先，由于许多设备嵌入了强大的 CPU，而且硬件变得越来越便宜，对小型面向位的密码的需求减少了。例如，移动通信标准 4G 中的两个流密码（欧洲的 SNOW3G 和中国的 ZUC）使用 32 位字而不是位，这与较旧的 A5/1 不同。

其次，流密码在软件领域逐渐流行，而分组密码则受到冷落，尤其是在 CBC 模式下的填充预言攻击（padding oracle attack）惨败之后。此外，流密码比分组密码更容易描述和实现：流密码不是将消息位和密钥位混合在一起，而是仅将密钥位作为秘密输入。事实上，最流行的流密码之一实际上是一个伪装的块密码：计数器模式（CTR）下的 AES。

一种被 SNOW3G 和 ZUC 采用的软件流密码设计，模仿了硬件密码及其 FSR，将位替换为字节或字。但在密码学家看来，这些并不是最有趣的设计。截至撰写本文时，最受关注的两种设计是 RC4 和 Salsa20，它们被广泛应用于众多系统中，尽管其中一种已经完全被攻破。

## RC4

RC4 由 RSA Security 的 Ron Rivest 于 1987 年设计，随后于 1994 年被逆向工程并泄露，它长期以来一直是使用最广泛的流密码。RC4 已被用于无数应用，最著名的是第一个 Wi-Fi 加密标准有线等效保密（WEP）和用于建立 HTTPS 连接的传输层安全（TLS）协议。不幸的是，对于大多数应用（包括 WEP 和 TLS）而言，RC4 并不足够安全。要理解原因，让我们看看 RC4 是如何工作的。

### RC4 的工作原理

RC4 是有史以来最简单的密码之一。它不执行任何类似密码的操作，没有异或、没有乘法、没有 S 盒……什么都没有。它只是交换字节。RC4 的内部状态是一个包含 256 个字节的数组 S，首先设置为 S[0] = 0、S[1] = 1、S[2] = 2、……、S[255] = 255，然后使用其密钥调度算法（KSA）从 n 字节的 K 初始化，该算法的工作原理如清单 5-1 中的 Python 代码所示。

```
j = 0
#### Set S to the array S[0] = 0, S[1] = 1, ..., S[255] = 255.
S = range(256)
#### Iterate over i from 0 to 255.
for i in range(256):
    # Compute the sum of V.
    j = (j + S[i] + K[i % n]) % 256
    # Swap S[i] and S[j].
    S[i], S[j] = S[j], S[i]
```

清单 5-1：RC4 的密钥调度算法




一旦该算法完成，数组 S 仍然包含从 0 到 255 的所有字节值，但现在顺序看起来是随机的。例如，使用全零的 128 位密钥时，状态 S（从 S[0] 到 S[255]）变为：

0, 35, 3, 43, 9, 11, 65, 229, (…), 233, 169, 117, 184, 31, 39

然而，如果我翻转第一个密钥位并再次运行 KSA，我会得到一个完全不同、看似随机的状态：

32, 116, 131, 134, 138, 143, 149, (…), 152, 235, 111, 48, 80, 12

给定初始状态 S，RC4 生成一个与明文 P 长度相同的密钥流 KS，用于计算密文：C = P ⊕ KS。如果 P 的长度为 m 字节，则密钥流 KS 的字节根据第 5-2 节中的 Python 代码从 S 计算得出。

```
i = 0
j = 0
for b in range(m):
    i = (i + 1) % 256
    j = (j + S[i]) % 256
    S[i], S[j] = S[j], S[i]
    KS[b] = S[(S[i] + S[j]) % 256]
```

Listing 5-2: RC4 的密钥流生成，其中 S 是在第 5-1 节中初始化的状态

在第 5-2 节中，for 循环的每次迭代最多修改 RC4 内部状态 S 的 2 个字节：值被交换的 S[i] 和 S[j]。也就是说，如果 i = 0 且 j = 4，并且 S[0] = 56 且 S[4] = 78，则交换操作将 S[0] 设置为 78，将 S[4] 设置为 56。如果 j 等于 i，则 S[i] 不会被修改。

这看起来太简单而无法安全，但密码分析学家花了 20 年才找到可利用的缺陷。在缺陷被揭示之前，我们只知道 RC4 在特定实现中的弱点，例如第一个 Wi-Fi 加密标准 WEP。

## RC4 在 WEP 中

WEP，第一代 Wi-Fi 安全协议，由于协议设计和 RC4 中的弱点，现在已被完全攻破。

在其 WEP 实现中，RC4 对 802.11 帧的有效载荷数据进行加密，这些数据报（或数据包）用于在无线网络上传输数据。同一会话中传输的所有有效载荷都使用相同的 40 或 104 位秘密密钥，但具有据称唯一的 3 字节 nonce 编码在帧头中（帧中编码元数据且位于实际有效载荷之前的部分）。

使用 RC4 的 TLS 保护连接是因为你需要欺骗服务器对同一明文加密给许多不同的接收者，或多次对同一接收者使用不同的密钥进行加密。

## Salsa20

Salsa20 是一种简单、面向软件的密码，针对现代 CPU 进行了优化，已与变体 ChaCha 一起在众多协议和库中实现。其设计者、受人尊敬的密码学家 Daniel J. Bernstein 于 2005 年将 Salsa20 提交给 eSTREAM 竞赛，并赢得在 eSTREAM 软件组合中的一席之地。Salsa20 的简单性和速度使其在开发者中很受欢迎。

Salsa20 是一种基于计数器的流密码——它通过重复处理每个块递增的计数器来生成其密钥流。如图 5-10 所示，Salsa20 核心算法使用密钥 (K)、nonce (N) 和计数器值 (Ctr) 转换 512 位块。然后 Salsa20 将结果加到块的原始值上以生成密钥流块。（如果算法直接将核心置换作为输出返回，Salsa20 将完全不安全，因为它可以被逆转。初始秘密状态 K || N || Ctr 的最终相加使密钥到密钥流块的变换不可逆。）

![](img/ace4de942d037de8ea5835bc9fbe57cd_133_0.png)

Figure 5-10: 512 位明文块的 Salsa20 加密方案

## 使用四分之一轮函数

Salsa20 的核心置换使用一个称为四分之一轮 (QR) 的函数，它将四个 32 位字 (a、b、c 和 d) 转换如下：

```
b = b ⊕ [(a + d) <<< 7]
c = c ⊕ [(b + a) <<< 9]
d = d ⊕ [(c + b) <<< 13]
a = a ⊕ [(d + c) <<< 18]
```

我们从上到下计算这四行，这意味着新的值 *b* 取决于 *a* 和 *d*，新的值 *c* 取决于 *a* 和新的值 *b*（从而也取决于 *d*），依此类推。

操作 `<<<` 是按字左旋转指定数量的位，其值可以是 1 到 31 之间的任意值（对于 32 位字）。例如，`<<< 8` 将字的位向左旋转八个位置，如以下示例所示：

```
0x01234567 <<< 8  = 0x23456701
0x01234567 <<< 16 = 0x45670123
0x01234567 <<< 22 = 0x59c048d1
```

## 转换 Salsa20 的 512 位状态

Salsa20 的核心置换转换视为 4×4 个 32 位字数组的 512 位内部状态。图 5-11 显示了初始状态，使用八个字（256 位）的密钥、两个字（64 位）的 nonce、两个字（64 位）的计数器，以及四个固定常量字（128 位），它们对每次加密/解密和所有块都相同。

![](img/ace4de942d037de8ea5835bc9fbe57cd_134_0.png)

为了转换初始的 512 位状态，Salsa20 首先独立地将 **QR** 变换应用于全部四个列（称为 *列轮*）然后独立地应用于全部四个行（*行轮*），如图 5-12 所示。列轮/行轮序列是一个 *双轮*。Salsa20 重复 10 次双轮，共 20 轮，这就是 *Salsa20* 中 20 的由来。

![](img/ace4de942d037de8ea5835bc9fbe57cd_134_1.png)

列轮将四个列转换如下：

```
**QR**(x₀, x₄, x₈, x₁₂)
**QR**(x₁, x₅, x₉, x₁₃)
**QR**(x₂, x₆, x₁₀, x₁₄)
**QR**(x₃, x₇, x₁₁, x₁₅)
```

行轮通过执行以下操作转换行：

```
**QR**(x₀, x₁, x₂, x₃)
**QR**(x₅, x₆, x₇, x₄)
**QR**(x₁₀, x₁₁, x₈, x₉)
**QR**(x₁₅, x₁₂, x₁₃, x₁₄)
```

在列轮中，每个 **QR** 接受从上到下排列的 xᵢ 参数，而行轮的 **QR** 将对角线上的字（如图 5-12 右侧数组所示）作为第一个参数，而不是来自第一列的字。

## 评估 Salsa20

Listing 5-3 显示了使用全零密钥（00 字节）和全一 nonce（ff 字节）初始化时前两个块的 Salsa20 初始状态。这两个状态仅在 1 位上不同，即计数器，该计数器以粗体显示：具体而言，第一个块为 0，第二个块为 1。

61707865 00000000 00000000 00000000   61707865 00000000 00000000 00000000
00000000 3320646e ffffffff ffffffff   00000000 3320646e ffffffff ffffffff
00000000 00000000 79622d32 00000000   00000001 00000000 79622d32 00000000
00000000 00000000 00000000 6b206574   00000000 00000000 00000000 6b206574

*Listing 5-3: 使用全零密钥和全一 nonce 时前两个块的 Salsa20 初始状态*

然而，尽管只有 1 位差异，经过 10 次双轮后的各自内部状态完全不同，如 Listing 5-4 所示。

e98680bc f730ba7a 38663ce0 5f376d93   1ba4d492 c14270c3 9fb05306 ff808c64
85683b75 a56ca873 26501592 64144b6d   b49a4100 f5d8fbbd 614234a0 e20663d1
6dcb46fd 58178f93 8cf54cfe cfdc27d7   12e1e116 6a61bc8f 86f01bcb 2efe4da
68bbe09e 17b403a1 38aa1f27 54323fe0   77775a13 d17b9d95 eb773f5b 2c3a5e7d

*Listing 5-4: 第 5-3 节中的状态经过 10 次 Salsa20 双轮后*

但请记住，即使密钥流块中的字值看起来是随机的，这也远非安全性的保证。RC4 的输出看起来是随机的，但它有明显的偏差。幸运的是，Salsa20 比 RC4 安全得多，并且没有统计偏差。然而请记住，即使密钥流在统计上与完全随机的字节无法区分，这也不足以实现密码安全性。

经过四轮后，差异对人眼看起来是随机的，在统计上也几乎是随机的：

```text
d93bed6d a267bf47 760c2f9f 4a41d54b
0e03d792 7340e010 119e6a00 e90186af
7fa9617e b6aca0d7 4f6e9a4a 56b434fd
98be796d 64908d32 4897f7ca ab84a2df
```

仅经过四轮后，单个差异就会传播到 512 位状态中的大部分位。在密码学中，我们称之为 *完全扩散*。

差异不仅在所有状态中传播，而且传播遵循复杂的方程，使得未来差异难以预测，因为高度 *非线性* 的关系驱动着状态的演化，这得益于 XOR、加法和旋转的混合。如果我们只使用 XOR，仍然会有许多差异传播，但过程将是线性的，因此不安全。

## 攻击 Salsa20/8

Salsa20 默认进行 20 轮，但有时我们只用 12 轮使用它，称为 Salsa20/12，以使其更快。虽然 Salsa20/12 比 Salsa20 少八轮，但根据最先进的研究进展，实际上与 20 轮版本一样可靠。即使只有八轮的 Salsa20/8，也只是在理论上较弱，实际上与 Salsa20 一样稳固。

破解 Salsa20 理想情况下应需要 2^256 次操作，这得益于其使用 256 位密钥。如果可以通过少于 2^256 次操作恢复密钥，则该密码在理论上已被破解。Salsa20/8 正是这种情况。

对 Salsa20/8 的攻击（发表于 2008 年论文“New Features of Latin Dances: Analysis of Salsa, ChaCha, and Rumba”，我是该论文的合著者，并因此获得了 Daniel J. Bernstein 的密码分析奖）利用了 Salsa 核心算法在四轮后出现的统计偏差来恢复八轮 Salsa20 的密钥。实际上，这主要是理论上的攻击：我们估计其复杂度为核心函数的 2^251 次操作——不可行，就像任何 2^100 次操作或更多的计算一样，但比破解预期的 2^256 复杂度要容易一些。

该攻击不仅利用了 Salsa20/8 前四轮的偏差，还利用了后四轮的特性：知道 nonce N 和计数器 Ctr（参见图 5-10），从密钥流反向计算到初始状态所需的唯一值是密钥 K。但如图 5-13 所示，如果你只知道 K 的一部分，你就可以部分地逆向计算到第四轮并观察该中间状态的一些位——包括有偏差的位！只有当你对部分密钥的猜测正确时，你才会观察到偏差；因此，偏差可作为你已获得正确密钥的指示。




![](img/ace4de942d037de8ea5835bc9fbe57cd_138_0.png)

图 5-13：针对 Salsa20/8 攻击的原理

在实际攻击 Salsa20/8 时，为了确定正确的猜测，我们需要猜测密钥的 220 位，并且需要 2^31 对密钥流块，所有这些块在 nonce 中都具有相同的特定差分。一旦我们找出正确的 220 位，就可以暴力破解剩余的 36 位。暴力破解需要 2^36 次运算，而完成攻击第一部分所需的 2^220 × 2^31 = 2^251 次尝试则显得不切实际，相比之下暴力破解的计算量微不足道。

## 问题可能出在哪里

唉，流密码可能出问题的环节很多，从脆弱且不安全的设计，到对强算法的错误实现，不一而足。下面我将逐一探讨各类潜在问题。

### Nonce 重用

流密码最常见的失败场景是使用相同密钥多次重用 nonce。这会产生相同的密钥流，从而使你能够破解加密——例如，将两个密文进行异或；密钥流随即消失，剩下的就是两个明文的异或结果。

一个真实的例子是旧版 Microsoft Word 和 Excel，它们为每个文档使用唯一的 nonce，但修改文档并不会改变 nonce。因此，人们可以利用旧版本文档的明文和密文来解密后来加密的版本。如果微软都会犯这种错误，你可以想象这个问题可能有多严重。

某些在 2010 年代设计的流密码试图通过构建“抗误用”结构来降低 nonce 重用的风险，即使 nonce 被使用两次也能保持安全。然而，实现这种安全级别会带来性能损失，正如你在第 8 章中看到的 SIV 模式那样。

### 错误的 RC4 实现

尽管 RC4 本身就很弱，但如果你盲目优化其实现，它可能会变得更弱。例如，让我们看看 2007 年“Underhanded C Contest”（一项非正式竞赛，参赛者编写看似无害但实际上包含恶意功能的代码）中的一个参赛作品。

当 i = j 时，情况就变得糟糕了。异或交换并没有保持状态不变，而是将 S[i] 设置为 S[i] ⊕ S[i] = 0。实际上，在密钥调度或加密过程中，每当 i 等于 j 时，状态的一个字节就会被置零，最终导致全零状态，从而产生全零密钥流。例如，在处理 68KB 数据后，256 字节状态中的大部分字节都变为零，输出的密钥流看起来像这样：

```
00 00 00 00 00 00 00 53 53 00 00 00 00 00 00 00 00 00 00 13 13 00 5c 00 a5 00 00 …
```

这里的教训是：不要过度优化你的加密实现。在密码学中，清晰性和可靠性永远比性能更重要。

### 硬件中固化的弱密码

当一个密码系统不再安全时，有些系统会迅速响应，通过远程静默更新受影响的软件（如 Web 应用），或发布新版本并提示用户升级（如移动应用）。其他系统则没那么幸运，它们需要在升级到安全版本之前继续使用受损的密码系统一段时间，某些卫星电话就是如此。

在 21 世纪初，美国和欧洲的电信标准化机构（TIA 和 ETSI）联合制定了两个卫星电话通信标准。卫星电话类似于移动电话，只是它们的信号通过卫星而非地面基站传输。其优点是，只要有卫星覆盖，你几乎可以在世界任何地方使用它们。它们的缺点是价格、质量、延迟，以及——事实证明——安全性。

GMR-1 和 GMR-2 是大多数商业供应商（如 Thuraya 和 Inmarsat）采用的两种卫星电话标准。两者都包含用于加密语音通信的流密码。GMR-1 的密码面向硬件，结合了四个 LFSR，类似于 A5/2——2G 移动标准中针对非西方国家故意设计的不安全密码。GMR-2 的密码面向软件，具有 8 字节状态并使用 S 盒。这两种流密码都不安全，只能保护用户免受业余攻击者的侵害，而无法抵御国家机构。

这个故事提醒我们，流密码过去比分组密码更容易被破解，也更容易被蓄意破坏。为什么？嗯，如果你故意设计一个弱流密码，那么当你发现漏洞时，仍然可以将其归咎于流密码本身的弱点，并否认任何恶意意图。

## 延伸阅读

要了解更多关于流密码的内容，可以从 eSTREAM 竞赛的档案开始：https://www.ecrypt.eu.org/stream/project.html，那里有数百篇关于流密码的论文，包括 30 多个候选算法的详细信息和许多攻击方法。其中一些最有趣的攻击是相关攻击、代数攻击和立方攻击。特别参见 Nicolas Courtois 和 Willi Meier 关于前两种攻击的工作，以及 Itai Dinur 和 Adi Shamir 关于立方攻击的工作。

关于对 RC4 的攻击，可以查阅 2001 年 Scott Fluhrer、Itsik Mantin 和 Adi Shamir（FMS）的攻击，以及 2013 年的研究文章《On the Security of RC4 in TLS》。

Salsa20 的遗产也值得你关注。流密码 ChaCha 与 Salsa20 类似，但核心置换略有不同，后者后来被用于哈希函数 BLAKE，正如你将在第 6 章中看到的那样。这些算法都利用了 Salsa20 的软件实现技术，即使用并行化指令，详见 https://cr.yp.to/snuffle.html。

### 6 哈希函数

![](img/ace4de942d037de8ea5835bc9fbe57cd_142_0.png)

哈希函数——如 SHA-256、SHA-3 和 BLAKE3——构成了密码学家的瑞士军刀：它们被用于数字签名、公钥加密、完整性验证、消息认证、密码保护、密钥协商协议以及许多其他密码协议。

无论你是加密电子邮件、在手机上发送消息、连接 HTTPS 网站，还是通过虚拟专用网络（VPN）或安全外壳（SSH）连接远程机器，哈希函数都在幕后发挥着作用。

哈希函数是迄今为止所有密码算法中用途最广、使用最普遍的。它们的应用包括：云存储系统使用它们来识别相同文件和检测被修改的文件；Git 版本控制系统使用它们来识别仓库中的文件；端点检测与响应（EDR）系统使用它们来检测被修改的文件；基于网络的入侵检测系统（NIDS）使用哈希来检测网络中传输的已知恶意数据；取证分析人员使用哈希值来证明数字工件未被修改；比特币在其工作量证明系统中使用了哈希函数——还有更多应用。

与流密码从短输入生成长输出不同，哈希函数接受长输入并产生短输出，称为哈希值或摘要（见图 6-1）。

![](img/ace4de942d037de8ea5835bc9fbe57cd_143_0.png)

图 6-1：哈希函数的输入和输出

本章围绕两个主要主题展开。首先是安全性：哈希函数安全意味着什么？为此，我将介绍两个基本概念——抗碰撞性和抗原像性。第二个主题围绕哈希函数的构造展开。我将解释现代哈希函数使用的高级技术，然后回顾最常见的哈希函数的内部结构：SHA-1、SHA-2、SHA-3 和 BLAKE2。最后，你将看到安全的哈希函数在被误用时如何表现出不安全的行为。

**注意** 不要将密码学哈希函数与非密码学哈希函数混淆。非密码学哈希函数用于哈希表等数据结构或检测意外错误，它们不提供任何安全性。例如，循环冗余校验（CRC）就是用于检测文件意外修改的非密码学哈希。

### 安全哈希函数

哈希函数的安全性概念与我们迄今讨论的不同。密码旨在保护数据的机密性，以确保明文发送的数据无法被读取；而哈希函数旨在保护数据的完整性，以确保数据——无论是明文发送还是加密发送——未被修改。如果哈希函数是安全的，那么两条不同的数据应该始终具有不同的哈希值。因此，文件的哈希值可以作为其标识符。

考虑哈希函数最常见的应用：数字签名，或简称为签名。在使用数字签名时，应用程序处理的是待签名消息的哈希值，而不是消息本身，如图 6-2 所示。




![](img/ace4de942d037de8ea5835bc9fbe57cd_144_0.png)

图 6-2：数字签名方案中的哈希函数，其中哈希充当消息的代理

哈希充当消息的标识符。如果消息中甚至改变了单个比特，消息的哈希值将完全不同。因此哈希函数有助于确保消息未被修改。对消息哈希进行签名与对消息本身进行签名一样安全，而且对例如 256 位的短哈希进行签名比对可能非常大的消息进行签名要快得多。事实上，大多数签名算法仅适用于诸如哈希值之类的短输入。

## 再次不可预测性

哈希函数的密码学强度源于其输出的不可预测性。取以下 256 位十六进制值；你使用 NIST 标准哈希函数 SHA-256 用 ASCII 字母 a、b 和 c 作为输入计算这些哈希值。尽管值 a、b 和 c 仅相差 1 或 2 个比特（a 是比特序列 01100001，b 是 01100010，c 是 01100011），但它们的哈希值完全不同：

```
SHA-256("a") = ca978112ca1bbdcafac231b39a23dc4da786eff8147c4e72b9807785afee48bb
SHA-256("b") = 3e23e8160039594a33894f6564e1b1348bbd7a0088d42c4acb73eeaed59c009d
SHA-256("c") = 2e7d2c03a9507ae265ecf5b5356885a53393a2029d241394997265a1a25aefc6
```

仅凭这三个哈希值，不可能预测 d 的 SHA-256 哈希值或其任何比特，因为安全哈希函数的哈希值是不可预测的。安全的哈希函数应像一个黑盒，每次接收到输入时都返回一个随机字符串。

安全哈希函数的一般理论定义是它表现得像一个真正随机的函数（有时称为随机预言机）。具体来说，安全哈希函数不应具有随机函数不会具有的任何属性或模式。这一定义对理论家有帮助，但在实践中我们需要更具体的概念，即抗原像性和抗碰撞性。

## 抗原像性

给定哈希值 H 的原像是指任何消息 M，使得 Hash(M) = H。抗原像性描述了这样一种安全保证：给定一个随机哈希值，攻击者永远找不到该哈希值的原像。事实上，有时你可以称哈希函数为单向函数，因为你可以从消息到其哈希，但不能反过来。

确实，即使在无限计算能力的情况下，你也不能反转哈希函数。例如，假设我使用 SHA-256 哈希函数对某条消息进行哈希处理并得到这个 256 位哈希值：

f67a58184cef99d6dfc3045f08645e844f2837ee4bfcc6c949c9f7f6743667adfd

即使在无限的时间和计算能力下，你也永远无法确定我选择以产生此特定哈希的 *消息*，因为有许多消息哈希到相同的值。因此你会找到 *某些* 产生此哈希值的消息（可能包括我选择的那个），但无法确定我使用的消息。你得到 *无条件安全性*。

例如，256 位哈希有 2²⁵⁶ 个可能值（实际使用的哈希函数中典型的长度），但例如 1,024 位消息的值要多得多（即 2¹⁰²⁴ 个可能值）。因此可得出结论，平均而言，每个可能的 256 位哈希值将有 2¹⁰²⁴ / 2²⁵⁶ = 2¹⁰²⁴⁻²⁵⁶ = 2⁷⁶⁸ 个 1,024 位的原像。

在实践中，你必须确保实际上不可能找到 *任何* 映射到给定哈希值的消息，而不仅仅是所使用的消息，这才是抗原像性真正所指。具体来说，可以谈论第一原像和第二原像抗性。*第一原像抗性*（或仅 *抗原像性*）描述了实际上不可能找到哈希到给定值的消息的情况。*第二原像抗性* 另一方面，描述了给定消息 *M₁* 时，实际上不可能找到另一条消息 *M₂*，其哈希值与 *M₁* 相同的情况。

## 原像的代价

给定一个哈希函数和一个哈希值，你可以通过尝试不同的消息直到命中目标哈希来搜索第一原像。列表 6-1 显示了如何使用类似于 solve_preimage() 的算法来执行此操作。

```
solve_preimage(H) {
    repeat {
        M = random_message()
        if Hash(M) == H then return M
    }
}
```

*列表 6-1：安全哈希函数的最佳原像搜索算法*

这里，random_message() 生成一个随机消息（例如一个随机的 1,024 位值）。如果哈希的比特长度 *n* 足够大，solve_preimage() 实际上永远不会完成，因为平均需要 2ⁿ 次尝试才能找到原像。当 *n* = 256 时，如现代哈希 SHA-256 和 BLAKE2 中那样，这是一个无望的情况。

## 第二原像抗性为何更弱

如果你能找到第一原像，那么你也能找到第二原像（对于相同的哈希函数）。作为证明，如果算法 solve_preimage() 返回给定哈希值的原像，请使用列表 6-2 中的算法来找到某条消息 M 的第二原像。

```
solve_second_preimage(M) {
    H = Hash(M)
    return solve_preimage(H)
}
```

列表 6-2：如果能找到第一原像，如何找到第二原像

你会将第二原像视为原像问题并应用原像攻击来找到它。由此可知，任何抗第二原像的哈希函数也是抗原像的。（如果不是，根据前述的 solve_second_preimage() 算法，它也不会是抗第二原像的。）换句话说，你用来找到第二原像的最佳攻击几乎与用来找到第一原像的最佳攻击相同，除非哈希函数存在某些缺陷允许更高效的攻击。另请注意，原像搜索攻击从根本上类似于对分组密码或流密码的密钥恢复攻击，只是加密情况下只有一个已知大小的解。

## 抗碰撞性

无论你选择哪种哈希函数，由于鸽笼原理，碰撞不可避免地存在，该原理指出，如果你有 m 个鸽笼和 n 只鸽子要放入其中，并且 n 大于 m，那么至少有一个鸽笼必须包含多于一只鸽子。

注 你可以将鸽笼原理推广到其他物品和容器。例如，美国宪法中任何 27 个词的序列都至少包含两个以相同字母开头的词。在哈希函数的世界中，鸽笼是哈希值，鸽子是消息。因为你知道可能的消息比哈希值多得多，所以碰撞必须存在。

然而，尽管不可避免，碰撞应该很难找到才能认为哈希函数是抗碰撞的——换句话说，攻击者不应能够找到两个不同的消息使其哈希值相同。

抗碰撞性的概念与第二原像抗性相关：如果你可以为哈希函数找到第二原像，你也可以找到碰撞，如列表 6-3 所示。

```
solve_collision() {
    M = random_message()
    return (M, solve_second_preimage(M))
}
```

列表 6-3：朴素的碰撞搜索算法

也就是说，任何抗碰撞的哈希也是抗第二原像的。如果不是这样，就会有一种高效的 solve-second-preimage 算法可用于破坏抗碰撞性。

## 如何找到碰撞

找到碰撞比找到原像更快：它大约需要 $2^{n/2}$ 次操作而不是 $2^n$，得益于 *生日攻击*，其关键思想如下：给定 $N$ 条消息和相同数量的哈希值，你可以通过考虑每两个哈希值的配对来产生总共 $N \times (N - 1) / 2$ 个潜在碰撞（数量级与 $N^2$ 相同）。它被称为 *生日攻击*，因为它通常使用 *生日悖论* 来说明，即 23 人一组将包含两个生日相同的人的概率接近 1/2——这不是悖论，只是对许多人来说令人惊讶。

> **注**  $N \times (N - 1) / 2$ 是两个不同消息的 *对* 的计数，其中除以 2 是因为你将 $(M_1, M_2)$ 和 $(M_2, M_1)$ 视为同一对，顺序无关紧要。

相比之下，在原像搜索的情况下，$N$ 条消息只给你 $N$ 个候选原像，而相同的 $N$ 条消息大约产生 $N^2$ 个潜在碰撞。用 $N^2$ 代替 $N$，可以说找到解的机会 *平方* 地更多。搜索的复杂度因此平方地更低：要找到碰撞，使用 $2^n$ 消息的平方根；也就是说，使用 $2^{n/2}$ 而不是 $2^n$。

## 朴素的生日攻击

以下是使用生日攻击找到碰撞的最简单方法：

- 1. 计算 $2^{n/2}$ 个任意选择的消息的 $2^{n/2}$ 个哈希值，并将所有消息/哈希对存储在列表中。
- 2. 根据哈希值对列表进行排序，使任何相同的哈希值彼此相邻。
- 3. 搜索排序后的列表以找到具有相同哈希值的两个连续条目。

不幸的是，此方法需要大量内存（足以存储 $2^{n/2}$ 个消息/哈希对），并且对大量元素进行排序会减慢搜索速度，使用快速排序等快速排序算法平均需要约 $n2^{n/2}$ 次操作。

## 使用 Rho 方法的低内存碰撞搜索

*Rho 方法* 是一种用于查找碰撞的算法，与朴素的生日攻击不同，它只需要少量内存。它的工作方式如下：


1. 给定一个具有 \(n\) 位哈希值的哈希函数，选取某个随机哈希值（\(H_1\)），并定义 \(H'_1 = H_1\)。
2. 计算 \(H_2 = \mathrm{Hash}(H_1)\) 和 \(H'_2 = \mathrm{Hash}(\mathrm{Hash}(H'_1))\)。第一种情况下应用一次哈希函数，第二种情况下应用两次。
3. 迭代该过程，对递增的 \(i\)，计算 \(H_{i+1} = \mathrm{Hash}(H_i)\)、\(H'_{i+1} = \mathrm{Hash}(\mathrm{Hash}(H'_i))\)，直到达到某个 \(i\) 使得 \(H_{i+1} = H'_{i+1}\)。

图 6-3 有助于直观理解这种攻击，其中从例如 \(H_1\) 指向 \(H_2\) 的箭头表示 \(H_2 = \mathrm{Hash}(H_1)\)。注意，\(H\) 的序列最终会进入一个环，也称为*循环*，其形状类似希腊字母 rho（ρ）。这个循环从 \(H_5\) 开始，其特征是碰撞 \(\mathrm{Hash}(H_4) = \mathrm{Hash}(H_{10}) = H_5\)。这里的关键观察是：要找到碰撞，你只需要找到这样一个循环。Rho 方法使攻击者能够检测循环的位置，从而找到碰撞。

![](img/ace4de942d037de8ea5835bc9fbe57cd_148_0.png)

*图 6-3：Rho 哈希函数的结构，其中每个箭头表示一次哈希函数求值。从 \(H_5\) 开始的循环对应于一个碰撞，\(\mathrm{Hash}(H_4) = \mathrm{Hash}(H_{10}) = H_5\)。*

基于 Rho 方法的高级碰撞查找技术首先检测循环的起始位置，然后找到碰撞，无需在内存中存储大量值，也无需对长列表进行排序。这大约需要 \(2^{n/2}\) 次操作才能成功。实际上，图 6-3 中展示的哈希值数量远比具有 256 位或更长摘要的实际函数要少。平均而言，循环和尾部（图 6-3 中从 \(H_1\) 延伸到 \(H_5\) 的部分）各包含大约 \(2^{n/2}\) 个哈希值，其中 \(n\) 是哈希值的位长。因此，要找到碰撞，你至少需要 \(2^{n/2} + 2^{n/2}\) 次哈希求值。

## 如何构建哈希函数

20 世纪 80 年代，密码学家意识到，对消息进行哈希的最简单方法是将其分割成块，并使用类似的算法连续处理每一块。这种称为迭代哈希的策略主要有两种形式：

- 使用压缩函数的迭代哈希，将输入转换为较小的输出，如图 6-4 所示。该技术也称为 Merkle–Damgård 构造，以描述该构造的密码学家 Ralph Merkle 和 Ivan Damgård 的名字命名。
- 使用一种将输入转换为相同大小输出的函数进行迭代哈希，使得任意两个不同的输入产生两个不同的输出（即置换）。此类函数称为海绵函数。

![](img/ace4de942d037de8ea5835bc9fbe57cd_149_0.png)

*图 6-4：使用称为 Compress 的压缩函数的 Merkle–Damgård 构造*

我们现在将讨论这些构造如何工作，以及压缩函数在实践中是什么样子。

### 基于压缩的哈希函数

从 20 世纪 80 年代到 2010 年代开发的所有哈希函数都基于 Merkle–Damgård（M–D）构造：MD4、MD5、SHA-1 和 SHA-2 系列，以及不太知名的 RIPEMD 和 Whirlpool 哈希函数。虽然 M–D 构造并不完美，但它很简单，并且已被证明对许多应用来说足够安全。

> **注意：** 在 MD4、MD5 和 RIPEMD 中，MD 代表消息摘要（message digest），而不是 Merkle–Damgård。

要对消息进行哈希，M–D 构造将消息分割为大小相同的块，并使用压缩函数将这些块与内部状态混合，如图 6-4 所示。这里，\(H_0\) 是内部状态的初始值（记为 IV），值 \(H_1, H_2, \dots\) 是链接值，内部状态的最终值就是消息的哈希值。

消息块通常为 512 或 1,024 位，但原则上可以是任意大小。无论块长度如何，对于给定的哈希函数，它都是固定的。例如，SHA-256 使用 512 位块，SHA-512 使用 1,024 位块。

#### 填充块

如果你想要哈希的消息无法分割成完整的块序列，会发生什么情况？例如，如果块是 512 位，那么一个 520 位的消息由一个 512 位块加上 8 位组成。在这种情况下，M–D 构造按如下方式形成最后一个块：取剩余位块（本例中为 8 位），追加 1 位，然后追加 0 位，最后追加原始消息的长度（以固定位数编码）。这种填充技巧保证任意两个不同的消息产生不同的块序列，从而产生不同的哈希值。

例如，如果你使用 SHA-256（一种具有 512 位消息块的哈希函数）对 8 位字符串 10101010 进行哈希，第一个也是唯一一个块的位形式如下：

`10101010 1000000000000000 (...) 0000000000001000`

这里，消息位是前 8 位（`10101010`），填充位是后续所有位（以斜体显示）。块末尾的 `1000`（带下划线）是消息的长度，即 8 的二进制编码（最多 64 位）。这样，填充就产生了一个由单个 512 位块组成的 512 位消息，可以立即由 SHA-256 的压缩函数处理。

#### 安全性保证

Merkle–Damgård 构造将一个接受小的固定长度输入的安全压缩函数转化为一个接受任意长度输入的安全哈希函数。如果压缩函数具有原像抗性和碰撞抗性，那么基于它并使用 M–D 构造构建的哈希函数也具有原像抗性和碰撞抗性。这是因为我们可以将针对 M–D 哈希的任何成功的原像攻击转化为针对压缩函数的成功的原像攻击，正如 Merkle 和 Damgård 在 1989 年的论文中所证明的那样（见本章的“进一步阅读”部分）。对于碰撞也是如此：攻击者无法在不破坏底层压缩函数的碰撞抗性的情况下破坏哈希的碰撞抗性；因此，后者（压缩函数）的安全性保证了哈希的安全性。

注意，反向论断并不成立，因为压缩函数的碰撞不一定能给出哈希函数的碰撞。对于链接值 \(X\) 和 \(Y\)（均不同于 \(H_0\)），\(\mathrm{Compress}(X, M_1)\) 和 \(\mathrm{Compress}(Y, M_2)\) 之间的任意碰撞不会让你获得哈希函数的碰撞，因为你无法将这一碰撞“插入”到迭代的哈希链中——除非其中一个链接值恰好是 \(X\)，另一个恰好是 \(Y\)，但这种情况不太可能发生。

#### 寻找多重碰撞

当三个或更多消息哈希到相同值时，就会发生多重碰撞。例如，三元组（\(X\), \(Y\), \(Z\)）满足 \(\mathrm{Hash}(X) = \mathrm{Hash}(Y) = \mathrm{Hash}(Z)\)，就是一个 3-碰撞。理想情况下，多重碰撞应该比普通碰撞更难找到，但有一个简单的技巧可以以几乎与单个碰撞相同的代价找到它们。其原理如下：

1. 找到碰撞 \(\mathrm{Compress}(H_0, M_{1.1}) = \mathrm{Compress}(H_0, M_{1.2}) = H_1\)。这只是 2-碰撞，即两个消息哈希到相同值。
2. 以 \(H_1\) 为起始链接值找到第二个碰撞：\(\mathrm{Compress}(H_1, M_{2.1}) = \mathrm{Compress}(H_1, M_{2.2}) = H_2\)。现在你有了 4-碰撞，四个消息哈希到相同值 \(H_2\)：\(M_{1.1} || M_{2.1}\)、\(M_{1.1} || M_{2.2}\)、\(M_{1.2} || M_{2.1}\) 和 \(M_{1.2} || M_{2.2}\)。
3. 重复上述过程，找到碰撞 \(N\) 次，你将得到 \(2^N\) 个消息，每个消息由 \(N\) 个块组成，它们都哈希到相同值——也就是 \(2^N\)-碰撞，而代价“仅”约为 \(N2^{n/2}\) 次哈希计算。

在实践中，这个技巧并不那么实用，因为首先需要找到基本的 2-碰撞。

#### 构建压缩函数

SHA-256 和 BLAKE2 等实际哈希函数中使用的所有压缩函数都基于分组密码，因为这是构建压缩函数的最简单方式。图 6-5 展示了基于分组密码的压缩函数中最常见的一种，即 *Davies–Meyer 构造*。

![](img/ace4de942d037de8ea5835bc9fbe57cd_151_0.png)

*图 6-5：Davies–Meyer 构造。深色三角形表示分组密码密钥的输入位置。*

给定消息块 \(M_i\) 和上一个链接值 \(H_{i-1}\)，Davies–Meyer 压缩函数使用分组密码 \(E\) 计算新的链接值：

\[H_i = E(M_i, H_{i-1}) \oplus H_{i-1}\]

消息块 \(M_i\) 充当分组密码的密钥，链接值 \(H_{i-1}\) 充当其明文块。只要分组密码是安全的，所得压缩函数就是安全的，并且具有碰撞抗性和原像抗性。如果没有异或前一个链接值（\(\oplus H_{i-1}\)），Davies–Meyer 将是不安全的，因为你可以使用分组密码的解密函数将其反转，从新的链接值回到前一个链接值。



Davies–Meyer 结构有一个令人惊讶的性质：你可以找到固定点（即链接值），在给定消息块应用压缩函数后保持不变。取 H_{i-1} = D(M_i, 0) 作为链接值即可，其中 D 是对应于 E 的解密函数。因此，新的链接值 H_i 等于原始的 H_{i-1}。

H_i = E(M_i, H_{i-1}) ⊕ H_{i-1} = E(M_i, D(M_i, 0)) ⊕ D(M_i, 0) = 0 ⊕ D(M_i, 0) = D(M_i, 0) = H_{i-1}

得到 H_i = H_{i-1} 是因为将零的解密结果代入加密函数会产生零——即 E(M_i, D(M_i, 0)) = 0——在压缩函数输出的表达式中只剩下 ⊕ H_{i-1} 这一部分。然后，你可以为 SHA-2 函数的压缩函数找到固定点，例如，这些函数基于 Davies–Meyer 结构。幸运的是，固定点并不构成安全风险。

除了 Davies–Meyer 之外，还有许多基于分组密码的压缩函数，例如图 6-6 中的那些。

![](img/ace4de942d037de8ea5835bc9fbe57cd_152_0.png)

图 6-6：其他安全的基于分组密码的压缩函数构造

这些函数不太常用，因为它们更复杂，或者要求消息块与链接值长度相同。

## 基于置换的哈希函数

经过数十年的研究，密码学家对基于分组密码的哈希技术已经了如指掌。但是，难道不应该有一种更简单的哈希方法吗？既然哈希函数不接收密钥，为什么还要使用接收密钥的分组密码算法呢？为什么不用固定密钥的分组密码（即单一置换算法）来构建哈希函数呢？

这些更简单的哈希函数就是海绵函数，它们使用单一置换，而不是压缩函数和分组密码（见图 6-7）。海绵函数不使用分组密码将消息位与内部状态混合，而是只进行 XOR 运算。海绵函数不仅比 Merkle–Damgård 函数更简单，而且更通用。它们不仅被用作哈希函数，还被用作确定性随机位生成器、流密码、伪随机函数（见第 7 章）和认证加密（见第 8 章）。最著名的海绵函数是 Keccak，也被称为 SHA-3。

![](img/ace4de942d037de8ea5835bc9fbe57cd_153_0.png)

图 6-7：海绵构造

海绵函数的工作原理如下：

- 1. 将第一个消息块 M₁ 与 H₀（内部状态的预定义初始值，例如全零字符串）进行 XOR。消息块大小相同，且小于内部状态。
- 2. 置换 P 将内部状态转换为另一个相同大小的值。
- 3. 将消息块 M₂ 与状态 XOR，应用 P，然后对消息块 M₃、M₄ 等重复此操作。这是吸收阶段。
- 4. 在注入所有消息块后，再次应用 P，并从状态中提取一个位块以形成哈希。如果需要更长的哈希，再次应用 P 并提取一个块。这是挤压阶段。

海绵函数的安全性取决于其内部状态的长度和块的长度。如果消息块为 r 位长，内部状态为 w 位长，那么内部状态中有 c = w − r 位是消息块无法修改的。c 的值即为海绵的容量，海绵函数保证的安全级别为 c/2。例如，要达到 256 位安全性并使用 64 位消息块，内部状态应至少为 w = 2 × 256 + 64 = 576 位。安全级别还取决于哈希值的长度 n。因此，碰撞攻击的复杂度是 2^{n/2} 和 2^{c/2} 中较小的值，而第二原像攻击的复杂度是 2^{n} 和 2^{c/2} 中较小的值。

为了确保安全，置换 P 的行为应类似于随机置换，没有统计偏差，也没有允许攻击者预测输出的数学结构。与基于压缩函数的哈希一样，海绵函数也会对消息进行填充，但填充更简单，因为它不需要包含消息的长度。只需在最后一个消息位后添加一个 1 位和所需数量的零即可。

## SHA 系列哈希函数

安全哈希算法（SHA）哈希函数是由 NIST 定义的美国非军事联邦政府机构使用的标准。这些标准被视作世界范围内的标准，只有某些非美国政府出于主权原因选择自己的哈希算法（如中国的 SM3、俄罗斯的 Streebog 和乌克兰的 Kupyna），而不是因为不信任 SHA 的安全性。与这些非美国哈希算法相比，美国的 SHA 系列受到了密码分析者更广泛的审查。

> *消息摘要 5（MD5）是 1992 年至 2005 年间最流行的哈希函数，直到 2005 年左右被破解，许多应用转而使用 SHA 系列哈希函数之一。MD5 处理 512 位消息块，并更新 128 位内部状态以产生 128 位哈希，因此最多提供 128 位原像安全性和 64 位碰撞安全性。1996 年，密码分析者就警告过 MD5 压缩函数存在碰撞，但他们的警告未得到重视，直到 2005 年，一组中国密码分析者发现了如何计算完整 MD5 哈希的碰撞。在我撰写本文时，找到 MD5 的碰撞只需几秒钟，然而一些系统仍在使用或支持 MD5，这通常是出于向后兼容性的原因。*

### SHA-1

SHA-1 标准源于 NSA 最初的 SHA-0 哈希函数的失败。1993 年，NIST 将 SHA-0 哈希算法标准化，但 1995 年，NSA 发布了 SHA-1，以修复 SHA-0 中一个未指明的安全问题。1998 年，两位研究人员发现，对于 SHA-0，只需约 2^{60} 次运算即可找到碰撞，而不是 SHA-0 和 SHA-1 这类 160 位哈希函数预期的 2^{80} 次，这一调整的原因变得清晰。后来的攻击将复杂度降低到约 2^{33} 次运算，导致 SHA-0 的实际碰撞在一小时内即可完成。

### SHA-1 内部结构

SHA-1 结合了 Merkle–Damgård 哈希函数与基于特殊设计的分组密码的 Davies–Meyer 压缩函数。也就是说，SHA-1 通过将以下操作在 512 位消息块 (M) 上迭代来工作：

H = E(M, H) + H

这里，使用加号 (+) 而不是 ⊕（XOR）是有意为之。E(M, H) 和 H 被视为 32 位整数数组，相同位置的两个字相加：E(M, H) 的第一个 32 位字与 H 的第一个 32 位字相加，依此类推。H 的初始值对于任何消息都是恒定的，然后 H 根据前面的方程进行修改，处理完所有块后 H 的最终值作为消息的哈希返回。

一旦使用消息块作为密钥、当前 160 位链接值作为明文块运行分组密码，160 位结果就被视为五个 32 位字的数组，每个字都与其在初始 H 值中的 32 位对应部分相加。

清单 6-4 展示了 SHA-1 的压缩函数 `SHA1-compress()`：

```
SHA1-compress(H, M) {
    (a0, b0, c0, d0, e0) = H   // Parsing H as five 32-bit big-endian words
    (a, b, c, d, e) = SHA1-blockcipher(a0, b0, c0, d0, e0, M)
    return (a + a0, b + b0, c + c0, d + d0, e + e0)
}
```

*清单 6-4：SHA-1 的压缩函数*

SHA-1 的分组密码 `SHA1-blockcipher()`（以粗体显示）以 512 位消息块 *M* 作为密钥，通过迭代 80 步短操作序列来变换五个 32 位字（a、b、c、d 和 e），用所有五个字的组合替换字 a。然后，它像移位寄存器一样移动数组中的其他字。清单 6-5 用伪代码描述了这些操作，其中 K[i] 是依赖于轮次的常量。

```
SHA1-blockcipher(a, b, c, d, e, M) {
    W = expand(M)
    for i = 0 to 79 {
        new = (a <<< 5) + f(i, b, c, d) + e + K[i] + W[i]
        (a, b, c, d, e) = (new, a, b >>> 2, c, d)
    }
    return (a, b, c, d, e)
}
```

*清单 6-5：SHA-1 的分组密码*

清单 6-5 中的 `expand()` 函数从 16 字消息块创建包含 80 个 32 位字的数组 W，方法是将 W 的前 16 个字设置为 M，将后续字设置为先前字的 XOR 组合，并循环左移 1 位。清单 6-6 显示了相应的伪代码。

```
expand(M) {
    // The 512-bit M is seen as an array of sixteen 32-bit words.
    W = empty array of eighty 32-bit words
    for i = 0 to 79 {
        if i < 16 then W[i] = M[i]
        else
            W[i] = (W[i - 3] ⊕ W[i - 8] ⊕ W[i - 14] ⊕ W[i - 16]) <<< 1
    }
    return W
}
```

*清单 6-6：SHA-1 的 `expand()` 函数*

清单 6-6 中的 `<<< 1` 操作是 SHA-1 与 SHA-0 函数之间的唯一区别。

最后，清单 6-7 展示了 `SHA1-blockcipher()` 中的 `f()` 函数，该函数是一个依赖于轮次的 8 个按位逻辑运算序列（即一个布尔函数）。



```text
f(i, b, c, d) {
    if i < 20 then return ((b & c) ⊕ (~b & d))
    if i < 40 then return (b ⊕ c ⊕ d)
    if i < 60 then return ((b & c) ⊕ (b & d) ⊕ (c & d))
    if i < 80 then return (b ⊕ c ⊕ d)
}
```

*清单 6-7：SHA-1 的 f() 函数*

清单 6-7 中的第二个和第四个布尔函数只是将三个输入字进行 XOR 运算，这是一种线性运算。相比之下，第一个和第三个函数使用非线性的 & 运算符（逻辑与）来抵御差分密码分析，因为差分密码分析利用的是逐位差分的可预测传播。如果没有 & 运算符（换句话说，例如，如果 f() 始终是 b ⊕ c ⊕ d），SHA-1 将很容易通过追踪其内部状态的模式而被攻破。

### 对 SHA-1 的攻击

虽然比 SHA-0 更健壮，但 SHA-1 也不安全，这就是为什么 Chrome 浏览器自 2014 年以来会将 HTTPS 连接中使用 SHA-1 的网站标记为不安全。尽管其 160 位哈希本应提供 80 位的抗碰撞性，但 2005 年研究人员发现了 SHA-1 的弱点，并估计找到一次碰撞大约需要 2^63 次计算（如果算法完美，则应为 2^80 次）。真正的 SHA-1 碰撞直到 12 年后才出现，当时经过多年研究，密码分析人员与谷歌研究人员合作，展示了两份碰撞的 PDF 文档（见 *https://shattered.io*）。

你不应该使用 SHA-1。现在大多数网络浏览器都将 SHA-1 标记为不安全，NIST 也不再推荐 SHA-1。请改用 SHA-2、SHA-3、BLAKE2 或 BLAKE3。

### SHA-2

SHA-2 是 SHA-1 的继任者，由美国国家安全局（NSA）设计，并于 2002 年由 NIST 标准化。SHA-2 是一个由四个哈希函数组成的家族：SHA-224、SHA-256、SHA-384 和 SHA-512（其中 SHA-256 和 SHA-512 是两个主要算法）。三位数字代表每个哈希的比特长度。

开发 SHA-2 的最初动机是生成更长的哈希，从而提供比 SHA-1 更高的安全级别。然而，SHA-1 和 SHA-2 算法在构造上相似。所有 SHA-2 实例也使用 Merkle–Damgård 构造，其压缩函数与 SHA-1 非常相似，但具有更强的非线性和差分传播特性。

### SHA-256

SHA-256 是 SHA-2 最常见的版本。SHA-1 的链接值为 160 位，而 SHA-256 的链接值为 256 位，表示为八个 32 位字。SHA-1 和 SHA-256 的消息块都是 512 位，但 SHA-1 执行 80 轮，而 SHA-256 执行 64 轮，将 16 字的消息调度扩展为 64 字，这增加了它与 SHA-1 的相似性，许多人因此认为对 SHA-2 的攻击只是时间问题。在我写这本书时，我们还没有看到对 SHA-2 的成功攻击。尽管如此，NIST 制定了一个备用计划：SHA-3。

## SHA-3 竞赛

NIST 哈希函数竞赛（SHA-3 竞赛的正式名称）于 2007 年宣布启动，首先公开征集参赛算法并提出一些基本要求：参赛哈希算法至少要与 SHA-2 一样安全、一样快，并且功能上至少要与 SHA-2 相当。SHA-3 候选算法也不应看起来太像 SHA-1 和 SHA-2，以免受到那些能够攻破 SHA-1 以及可能攻破 SHA-2 的攻击。到 2008 年，NIST 已收到来自世界各地的 64 份参赛方案，包括大学和大型企业（如 BT、IBM、微软、高通和索尼等）。这 64 份方案中，有 51 份符合要求，进入了竞赛的第一轮。

在竞赛的最初几周，密码分析人员对参赛方案进行了毫不留情的攻击。2009 年 7 月，NIST 公布了 14 个第二轮候选算法。在花费 15 个月分析和评估这些候选算法的性能后，NIST 选出了五个决赛算法：

- **BLAKE** 一种增强的 Merkle–Damgård 哈希，其压缩函数基于分组密码，而该分组密码又基于流密码 ChaCha 的核心函数，即加法、XOR 和字旋转的链。BLAKE 由一支位于瑞士和英国的学术研究人员团队设计，其中包括当时还是博士生的我。
- **Grøstl** 一种增强的 Merkle–Damgård 哈希，其压缩函数使用基于 AES 分组密码的两个置换（或固定密钥分组密码）。Grøstl 由来自丹麦和奥地利的七位学术研究人员设计。
- **JH** 一种调整过的海绵函数构造，其中消息块在置换之前和之后都被注入，而不仅仅是在之前。该置换还执行类似于代换-置换分组密码的操作（参见第 4 章）。JH 由新加坡一所大学的密码学家设计。
- **Keccak** 一种海绵函数，其置换仅执行按位运算。Keccak 由在一家位于比利时和意大利的半导体公司工作的四位密码学家组成的团队设计，其中一位是 AES 的两位设计者之一。
- **Skein** 一种基于与 Merkle–Damgård 不同的操作模式的哈希函数，其压缩函数基于一种仅使用整数加法、XOR 和字旋转的新型分组密码。Skein 由八位来自学术界和工业界的密码学家设计，除一位外其余均在美国，其中包括著名的 Bruce Schneier。

在对五个决赛算法进行广泛分析后，NIST 宣布了获胜者：Keccak。NIST 的报告称赞 Keccak 具有“优雅的设计、较大的安全裕度、良好的综合性能、出色的硬件效率以及灵活性”。我们来看看 Keccak 是如何工作的。

## Keccak（SHA-3）

NIST 选择 Keccak 的原因之一是它与 SHA-1 和 SHA-2 完全不同。首先，它是一种海绵函数。Keccak 的核心算法是对 1,600 位状态的一个置换，该状态吸收 1,152、1,088、832 或 576 位的分组，分别产生 224、256、384 或 512 位的哈希值——这与 SHA-2 哈希函数产生的四种长度相同。但与 SHA-2 不同，SHA-3 对所有四种哈希长度使用单一核心算法，而不是两种算法。

另一个原因是 Keccak 不仅仅是一个哈希函数。SHA-3 标准文档 FIPS 202 定义了四个哈希——SHA3-224、SHA3-256、SHA3-384 和 SHA3-512——以及两个分别称为 SHAKE128 和 SHAKE256 的算法。（SHAKE 全称是 Secure Hash Algorithm with Keccak，即“使用 Keccak 的安全哈希算法”。）这两个算法是可扩展输出函数（XOF），即可以产生可变长度哈希值的哈希函数，甚至可以产生很长的哈希值。数字 128 和 256 代表每种算法的安全级别。

FIPS 202 标准本身冗长且难以理解，但你可以找到一些速度合理且使算法易于理解的开源实现。例如，Markku-Juhani O. Saarinen 编写的 tiny_sha3（https://github.com/mjosaarinen/tiny_sha3）用 19 行 C 代码解释了 Keccak 的核心算法，部分代码如清单 6-9 所示。

```c
static void sha3_keccakf(uint64_t st[25], int rounds)
{
    (⊕)
    for (r = 0; r < rounds; r++) {
        ① // Theta
        for (i = 0; i < 5; i++)
            bc[i] = st[i] ^ st[i + 5] ^ st[i + 10] ^ st[i + 15] ^ st[i + 20];

        for (i = 0; i < 5; i++) {
            t = bc[(i + 4) % 5] ^ ROTL64(bc[(i + 1) % 5], 1);
            for (j = 0; j < 25; j += 5)
                st[j + i] ^= t;
        }

        ② // Rho Pi
        t = st[1];
        for (i = 0; i < 24; i++) {
            j = keccakf_piln[i];
            bc[0] = st[j];
            st[j] = ROTL64(t, keccakf_rots[i]);
            t = bc[0];
        }
    }
```

```c
③ // Chi
    for (j = 0; j < 25; j += 5) {
        for (i = 0; i < 5; i++)
            bc[i] = st[j + i];
        for (i = 0; i < 5; i++)
            st[j + i] ^= (~bc[(i + 1) % 5]) & bc[(i + 2) % 5];
    }

    ④ // Iota
    st[0] ^= keccakf_rndc[r];
}
(⊕)
}
```

清单 6-9：tiny_sha3 实现

tiny_sha3 程序实现了 Keccak 的置换 P，这是对 1,600 位状态的可逆变换，该状态被视为 25 个 64 位字的数组。代码迭代一系列轮次，每轮包含四个主要步骤：

- 1. Theta ① 包括 64 位字之间的 XOR 运算，或字与其 1 位旋转值之间的 XOR 运算（ROTL64(w, 1) 操作将字 w 左旋 1 位）。
- 2. Rho Pi ② 包括将 64 位字按 keccakf_rotc[] 数组中硬编码的常量进行旋转。
- 3. Chi ③ 包括更多的 XOR 运算，以及 64 位字之间的逻辑与（& 运算符）。这些与运算是 Keccak 中唯一的非线性运算，它们带来了密码学强度。
- 4. Iota ④ 包括与 keccakf_rndc[] 中硬编码的 64 位常量进行的 XOR 运算。

这些运算为 SHA-3 提供了强大的置换算法，没有任何偏差或可利用的结构。SHA-3 是十多年研究的产物，数百位技艺娴熟的密码分析人员都未能攻破它。短期内也不太可能被攻破。

## BLAKE2 和 BLAKE3 哈希函数

安全可能最重要，但速度紧随其后。我见过很多情况，开发者不愿意从 MD5 切换到 SHA-1，仅仅因为 MD5 更快；也不愿意从 SHA-1 切换到 SHA-2，因为 SHA-2 明显比 SHA-1 慢。不幸的是，SHA-3 并不比 SHA-2 快，而且由于 SHA-2 仍然安全，升级到 SHA-3 的动力很少。那么，我们如何做到比 SHA-1 和 SHA-2 更快地哈希，同时又更加安全呢？答案在于 SHA-3 竞赛之后发布的 BLAKE2 哈希函数。

> 注 完整披露：我是 BLAKE2 的设计者之一，其他设计者还有 Samuel Neves、Zooko Wilcox-O'Hearn 和 Christian Winnerlein。



BLAKE2 的设计基于以下思路：

- 至少应与 SHA-3 一样安全，如果可能更强。
- 应比所有之前的哈希标准更快，包括 MD5。
- 应适用于现代应用，能够对大量数据进行哈希，无论是少数大消息还是许多小消息，均可有密钥或无密钥。
- 应适用于支持多核系统并行计算以及单核内指令级并行的现代 CPU。

工程过程的结果是一对主要哈希函数：

- BLAKE2b（或简称 BLAKE2），针对 64 位平台优化，产生的摘要长度范围为 1 到 64 字节。
- BLAKE2s 针对 8 至 32 位平台优化，产生的摘要长度范围为 1 到 32 字节。

每个函数都有一个并行变体，可以利用多个 CPU 核心。BLAKE2b 的并行对应物 BLAKE2bp 在四个核心上运行，而 BLAKE2sp 在八个核心上运行。前者在现代服务器和笔记本电脑 CPU 上速度最快，在笔记本 CPU 上哈希速度接近 2Gbps。BLAKE2 的速度和特性使其成为最受欢迎的非 NIST 标准哈希。BLAKE2 已被无数软件应用使用，并已集成到 OpenSSL 和 Sodium 等主要密码学库中。BLAKE2 也是互联网工程任务组（IETF）标准，描述于 RFC 7693。

**NOTE** *你可以在 https://blake2.net 找到 BLAKE2 的规范和参考代码，并且可以从 https://github.com/BLAKE2 下载优化后的代码和库。参考代码还提供了 BLAKE2X，即 BLAKE2 的扩展，可以生成任意长度的哈希值。*

如图 6-8 所示，BLAKE2 的压缩函数是 Davies–Meyer 构造的变体，它将参数作为额外输入——即 *counter*（确保每个压缩函数表现得像不同的函数）和 *flag*（指示压缩函数是否正在处理最后一个消息块，以提高安全性）。

![](img/ace4de942d037de8ea5835bc9fbe57cd_161_0.png)

*图 6-8：BLAKE2 的压缩函数。块密码之后，状态的两半会被 XOR 组合在一起。*

BLAKE2 压缩函数中的块密码基于流密码 ChaCha，而 ChaCha 本身是第 5 章中讨论的 Salsa20 流密码的变体。在该块密码中，BLAKE2b 的核心操作由以下操作链组成，该操作链使用两个消息字 M_i 和 M_j 将四个 64 位字的状态进行转换：

```
a = a + b + M_i
d = ((d ⊕ a) >>> 32)
c = c + d
b = ((b ⊕ c) >>> 24)
a = a + b + M_j
d = ((d ⊕ a) >>> 16)
c = c + d
b = ((b ⊕ c) >>> 63)
```

BLAKE2 的核心操作类似，但使用 32 位而非 64 位字（因此使用不同的旋转值）。

最后但同样重要的是，BLAKE3 是 BLAKE2 的更可并行化、更简单、更通用且更快的版本，于 2020 年在 Real World Crypto 会议上提出。由 Jack O'Connor、Samuel Neves、Zooko Wilcox-O'Hearn 和我设计，BLAKE3 已迅速成为最受欢迎的哈希函数之一，得益于其无可否认的优势。更多详情请参阅 https://github.com/BLAKE3-team/BLAKE3。

## 事情可能出错的方式

尽管看似简单，哈希函数在使用不当或使用错误的地方时仍可能导致重大的安全问题——例如，在网络传输数据的应用中，使用 CRC 等弱校验和算法而不是加密哈希来检查文件完整性。然而，这种弱点与其它可能导致看似安全的哈希函数完全被攻破的弱点相比相形见绌。你将看到两个失败示例：第一个适用于 SHA-1 和 SHA-2，但不适用于 BLAKE2 或 SHA-3，而第二个适用于这四种函数。

## 长度扩展攻击

图 6-9 显示了长度扩展攻击，这是 Merkle–Damgård 构造的主要威胁。

![](img/ace4de942d037de8ea5835bc9fbe57cd_163_0.png)

图 6-9：长度扩展攻击

基本上，如果你知道某个 *unknown* 消息 M 的 **Hash**(M)，M 由块 M₁ 和 M₂ 组成（填充后），你就可以确定任意块 M₃ 的 **Hash**(M₁ || M₂ || M₃)。因为 M₁ || M₂ 的哈希是紧跟在 M₂ 之后的链值，所以即使你不知道被哈希的数据，也可以向已哈希的消息添加另一个块 M₃。更重要的是，这一技巧可以推广到未知消息（这里是 M₁ || M₂）或后缀（M₃）中的任意数量的块。

长度扩展攻击不会影响大多数哈希函数的应用，但如果对哈希的使用过于创造性，则可能损害安全性。不幸的是，SHA-2 哈希函数容易受到长度扩展攻击，即使 NSA 设计了这些函数，NIST 也在标准化的同时，两者都清楚地知道这一缺陷。这一缺陷本可以通过使最后一次压缩函数调用与其他调用不同而避免（例如，在之前的调用使用 0 位作为额外参数时，最后一次调用使用 1 位）。BLAKE2 就是这样做的。

## 欺骗存储证明协议

云计算应用在 *proof-of-storage* 协议中使用哈希函数——即服务器（云提供商）向客户端（云存储服务的用户）证明服务器确实存储了其应代表客户端存储的文件的协议。

2007 年，Ramakrishna Kotla、Lorenzo Alvisi 和 Mike Dahlin 的论文“SafeStore: A Durable and Practical Storage System”（https://www.cs.utexas.edu/~lorenzo/papers/p129-kotla.pdf）提出了如下验证文件 M 存储的存储证明协议：

- 1. 客户端选择一个随机值 C 作为 *challenge*。
- 2. 服务器计算 **Hash**(M || C) 作为 *response* 并将结果发送给客户端。
- 3. 客户端也计算 **Hash**(M || C) 并检查其是否与从服务器收到的值匹配。

该论文的前提是服务器不应该能够欺骗客户端，因为如果服务器不知道 M，就无法猜出 **Hash**(M || C)。但有一个陷阱：实际上，**Hash** 是一个迭代哈希，它逐块处理输入，并在每个块之间计算中间链值。例如，如果 **Hash** 是 SHA-256 且 M 为 512 位长（SHA-256 中一个块的大小），服务器可以作弊。怎么做？服务器第一次收到 M 时，计算 H₁ = **Compress**(H₀, M₁)，该链值由 SHA-256 的初始值 H₀ 和 512 位的 M 得到。然后它将 H₁ 记录在内存中并丢弃 M，此时它不再存储 M。

当客户端发送随机值 C 时，服务器在对 C 添加填充以填满完整块后计算 **Compress**(H₁, C)，并将其作为 **Hash**(M || C) 返回。客户端随后相信，因为服务器返回了 **Hash**(M || C) 的正确值，所以它持有完整消息——除非它可能没有，正如你所见。

这一技巧适用于 SHA-1、SHA-2 以及 SHA-3 和 BLAKE2。解决方案很简单：要求 **Hash**(C || M) 而不是 **Hash**(M || C)。

## 延伸阅读

要了解更多关于哈希函数的信息，请阅读 1980 年代和 1990 年代的经典著作：如 Ralph Merkle 的“One Way Hash Functions and DES”和 Ivan Damgård 的“A Design Principle for Hash Functions”等研究文章。还请阅读 Bart Preneel、René Govaerts 和 Joos Vandewalle 的“Hash Functions Based on Block Ciphers: A Synthetic Approach”，这是基于块密码哈希的首次全面研究。

有关碰撞搜索的更多信息，请阅读 Paul van Oorschot 和 Michael Wiener 的 1997 年论文“Parallel Collision Search with Cryptanalytic Applications”。要了解更多关于支撑抗原像性和抗碰撞性的理论安全概念以及长度扩展攻击的信息，请搜索 *indistinguishability*。

有关哈希函数的最新研究，请参阅 SHA-3 竞赛的档案，其中包括所有不同的算法以及它们是如何被攻破的。你可以在 https://ehash.aiik.tugraz.at/wiki/The_SHA-3_Zoo.html 上的 SHA-3 Zoo 和 NIST 的页面 https://csrc.nist.gov/projects/hash-functions/sha-3-project 上找到许多参考资料。

有关 SHA-3 获胜者 Keccak 和海绵函数的更多信息，请参阅 https://keccak.team/sponge_duplex.html，即 Keccak 设计者的官方页面。

最后，你可以查阅这两种弱哈希函数的真实利用案例：

- 国家级恶意软件 Flame 利用 MD5 碰撞制作伪造证书并伪装成合法软件。
- Xbox 游戏机使用了一种弱块密码（称为 TEA）来构建哈希函数，该函数被利用来破解主机并在其上运行任意代码。



### 7 带密钥的哈希

![](img/ace4de942d037de8ea5835bc9fbe57cd_166_0.png)

第 6 章中的哈希函数接收一条消息并返回其哈希值——通常是 256 或 512 位的短字符串。任何人都可以计算一条消息的哈希值并验证特定消息是否哈希到特定值。然而，当你只希望特定的人计算哈希时，你会使用密钥进行哈希，使用 *带密钥的哈希函数*。

带密钥的哈希构成了两种密码算法的基础：*消息认证码 (MACs)*，用于认证消息并保护其完整性，以及 *伪随机函数 (PRFs)*，用于生成看起来随机的哈希大小的值。我们将在本章的第一部分先[content]
## 7 带密钥的哈希

![](img/ace4de942d037de8ea5835bc9fbe57cd_166_0.png)

第 6 章中的哈希函数接收一条消息并返回其哈希值——通常是 256 或 512 位的短字符串。任何人都可以计算一条消息的哈希值并验证特定消息是否哈希到特定值。然而，当你只希望特定的人计算哈希时，你会使用密钥进行哈希，使用 *带密钥的哈希函数*。

带密钥的哈希构成了两种密码算法的基础：*消息认证码 (MACs)*，用于认证消息并保护其完整性，以及 *伪随机函数 (PRFs)*，用于生成看起来随机的哈希大小的值。我们将在本章的第一部分先查看 MAC 与 PRF 之间的相似之处，然后再回顾 MAC 和 PRF 的工作原理。一些 MAC 和 PRF 基于哈希函数，一些基于分组密码，还有一些是原创设计。最后，我们将讨论对看似安全 MAC 的攻击示例。

### 消息认证码

MAC 通过创建值 T = MAC(K, M)，称为消息 M 的认证标签，常被混淆地称为 M 的 MAC，来保护消息的完整性和真实性。正如你知道密码的密钥就可以解密消息一样，你知道 MAC 的密钥就可以验证消息是否未被修改。

例如，假设 Alex 和 Bill 共享一个密钥 K，且 Alex 向 Bill 发送一条消息 M 以及其认证标签 T = MAC(K, M)。在收到消息及其认证标签后，Bill 重新计算 MAC(K, M) 并检查其是否等于收到的认证标签。由于只有 Alex 能够计算此值，Bill 知道该消息在传输过程中未被损坏（确认其完整性），无论是意外还是恶意，且该消息确实由 Alex 发送（确认其真实性）。

### 安全通信中的 MAC

安全通信系统通常结合密码和 MAC 来保护消息的保密性、完整性和真实性。例如，Internet 协议安全 (IPsec)、SSH 和 TLS 中的协议为每个传输的网络数据包生成一个 MAC。

并非所有通信系统都使用 MAC。有时认证标签会给每个数据包带来不可接受的开销，通常在 64 到 128 位范围内。例如，旧的 GSM 移动电话标准加密了编码语音呼叫的数据包，但并未对其进行认证。攻击者可以修改加密的音频信号，而接收方不会注意到。

### 伪造与选择消息攻击

MAC 安全意味着什么？首先，与密码一样，密钥应保持秘密。如果 MAC 是安全的，攻击者在不知道密钥的情况下不应能够为某条消息创建标签。我们称伪造的消息/标签对为伪造，而恢复密钥是更一般伪造攻击类别的特例。认为伪造应不可能找到的安全概念称为不可伪造性。还应无法从标签列表中恢复密钥；否则，攻击者可以使用密钥伪造标签。

攻击者如何破坏 MAC？换句话说，攻击模型是什么？最基本的攻击模型是已知消息攻击，它被动收集消息及其关联的标签（例如，通过窃听网络）。但现实中的攻击者通常可以发起主动攻击，因为他们可以选择要认证的消息，因此可以获得他们想要的消息的 MAC。因此标准模型是选择消息攻击，其中攻击者可以获得他们选择的任意消息的标签。

### 重放攻击

MAC 并不能抵御涉及 *重放* 标签的攻击。例如，如果你窃听 Alex 和 Bill 的通信，你可以捕获 Alex 发送给 Bill 的消息及其标签，并在之后冒充 Alex 再次将其发送给 Bill。为防止此类 *重放攻击*，协议在每条消息中包含一个消息编号。该编号对每个新消息递增，并由 MAC 与消息一起进行认证。接收方收到编号为 1、2、3、4 等的消息。因此，如果攻击者试图再次发送消息 1，接收方会注意到该消息顺序错误，并且它是先前消息 1 的潜在重放。

### 伪随机函数

PRF 使用密钥返回 **PRF**(*K*, *M*)，使得输出看起来是随机的。由于密钥是秘密的，输出值对攻击者来说是不可预测的。

与 MAC 不同，PRF 并非单独使用，而是作为密码算法或协议的一部分。例如，你可以在 Feistel 构造中使用 PRF 来创建分组密码——参见第 4 章中的“如何构造分组密码”。密钥派生方案使用 PRF 从主密钥或密码生成密码密钥，而身份识别方案使用 PRF 从随机挑战生成响应。（基本上，服务器发送一条随机挑战消息 *M*，客户端在响应中返回 **PRF**(*K*, *M*) 以证明它知道 *K*。）5G 电话标准使用 PRF 来认证 SIM 卡及其服务提供商，并且类似的 PRF 在电话通话期间生成加密密钥和 MAC 密钥。TLS 协议使用 PRF 从主密钥以及会话特定的随机值生成密钥材料。甚至内置于 Python 语言中用于比较对象的非密码学 hash() 函数中也包含一个 PRF。

### PRF 的安全性

要安全，伪随机函数不应有任何使其输出与真正随机值区别开来的模式。不知道密钥 *K* 的攻击者不应能够区分 **PRF**(*K*, *M*) 的输出与随机值。换句话说，攻击者不应有任何手段来判断他们面对的是 PRF 算法还是随机函数。对该安全概念的学究式表述是“与随机函数不可区分”。（要了解更多关于 PRF 理论基础的内容，请参阅 Goldreich《Foundations of Cryptography》第 1 卷第 3.6 节。）

### PRF 比 MAC 更强

PRF 和 MAC 都是带密钥的哈希，但 PRF 在根本上比 MAC 更强，因为 MAC 的安全要求更弱。你会认为 MAC 是安全的，如果攻击者无法伪造标签——也就是说，无法猜测 MAC 的输出——而 PRF 只有在其输出是不可区分的随机字符串时才是安全的。如果无法区分 PRF 的输出与随机字符串，则意味着其值无法被猜测；换句话说，任何安全的 PRF 也是安全的 MAC。

然而，逆命题不成立：安全的 MAC 不一定是安全的 PRF。例如，假设你从一个安全的 PRF PRF1 开始，并想从中构建第二个 PRF PRF2，如下所示：

PRF2(K, M) = PRF1(K, M) || 0

由于 PRF2 的输出定义为 PRF1 的输出后跟一个 0 位，它看起来不如真正的随机字符串随机，你可以通过最后的 0 位来区分其输出。因此，PRF2 不是安全的 PRF。然而，由于 PRF1 是安全的，PRF2 仍然能构成安全的 MAC。如果你能够伪造某个 M 的标签 T = PRF2(K, M)，那么你也能够伪造 PRF1 的标签，而你知道这在第一位是不可能的，因为 PRF1 是一个安全的 MAC。因此，PRF2 是一个带密钥的哈希，它是安全的 MAC 但不是安全的 PRF。

但不用担心：你不会在实际应用中找到此类 MAC 构造。事实上，许多已部署或标准化的 MAC 同时也是安全的 PRF，并且通常作为两者使用。例如，TLS 同时将算法 HMAC-SHA-256 用作 MAC 和 PRF。

### 如何从无密钥哈希创建带密钥哈希

在密码学历史上，MAC 和 PRF 很少从头设计，而是从现有算法构建，通常是哈希函数或分组密码。似乎很明显，你可以通过向（无密钥）哈希函数提供密钥和消息来生成带密钥的哈希函数，但这说起来容易做起来难。

### 密钥前缀构造

我们将要检查的第一个技术是密钥前缀构造，它通过将密钥前置到消息并返回 Hash(K || M) 将普通哈希函数转换为带密钥的哈希。这种方法在哈希函数容易受到长度扩展攻击时不安全（参见第 6 章中的“长度扩展攻击”），并且当哈希支持不同长度的密钥时也不安全。

### 对长度扩展攻击的不安全性

回顾第 6 章，SHA-2 家族的哈希函数允许攻击者在给定较短版本消息的哈希值时计算部分未知消息的哈希。在形式上，长度扩展攻击允许攻击者在仅给定 Hash(K || M1) 且既不知道 M1 也不知道 K 的情况下计算 Hash(K || M1 || M2)。这些函数允许攻击者免费伪造有效的 MAC 标签，因为他们不应该能够猜

仅凭 $M_1$ 的 MAC 就能得到 $M_1 \|\| M_2$ 的 MAC。这一事实使得秘密前缀构造在使用 SHA-256 或 SHA-512 等情况下作为 MAC 和 PRF 是不安全的。这是 Merkle–Damgård 允许长度扩展攻击的弱点，而 SHA-3 的所有决赛选手都不允许。能够抵御长度扩展攻击是 SHA-3 提交的强制要求（参见第 6 章）。

## 不同密钥长度下的不安全性

秘密前缀构造在允许使用不同长度的密钥时也是不安全的。例如，如果密钥 $K$ 是 24 位十六进制字符串 123abc 而 $M$ 是 def00，则 **哈希()** 处理的值 $K \|\| M = 123abcdef00$。如果 $K$ 改为 16 位字符串 123a 而 $M$ 是 bcdef000，则 **哈希()** 处理的 $K \|\| M = 123abcdef000$ 也是如此。因此，秘密前缀构造 **哈希**($K \|\| M$) 的结果对两个密钥都相同。

该问题与底层哈希无关；你可以通过同时对密钥的长度、密钥和消息进行哈希来修复它——例如，将密钥的位长度编码为 16 位整数 $L$，然后哈希 **哈希**($L \|\| K \|\| M$)。不过你不必这样做，因为现代哈希函数如 BLAKE2 和 SHA-3 包含一种带密钥模式，可避免这些陷阱并产生安全的 PRF，从而也产生安全的 MAC。

## 秘密后缀构造

与其像秘密前缀构造那样在消息之前对密钥进行哈希，你可以在之后对密钥进行哈希。这正是 *秘密后缀构造* 的工作原理，它通过 **哈希**($M \|\| K$) 从哈希函数构建 PRF。

把密钥放在末尾会产生很大差异。针对秘密前缀 MAC 有效的长度扩展攻击对秘密后缀无效。对秘密后缀 MAC 应用长度扩展会从 **哈希**($M_1 \|\| K$) 得到 **哈希**($M_1 \|\| K \|\| M_2$)，但这不是有效的攻击，因为 **哈希**($M_1 \|\| K \|\| M_2$) 不是有效的秘密后缀 MAC；密钥需要在末尾。

然而，秘密后缀构造对另一种类型的攻击更脆弱。假设你为哈希 **哈希**($M_1$) = **哈希**($M_2$) 找到了一个碰撞，其中 $M_1$ 和 $M_2$ 是两个不同的消息，可能大小不同。在像 SHA-256 这样的 M–D 哈希函数的情况下，这意味着 **哈希**($M_1 \|\| P_1 \|\| K$) 和 **哈希**($M_2 \|\| P_2 \|\| K$) 也会相等，其中 $P_1$ 和 $P_2$ 是为完成一个块而添加的填充数据。处理完 $M_1 \|\| P_1$ 后，哈希函数的状态与处理完 $M_2 \|\| P_2$ 后相同。对每个实例添加 $K$ 会保持状态的相等性，导致无论 $K$ 的值如何都会发生碰撞。

利用此属性，攻击者：
- 1. 找到两个碰撞的消息，$M_1$ 和 $M_2$
- 2. 请求 $M_1$ 的 MAC 标签，**哈希**($M_1 \|\| K$)
- 3. 猜测 **哈希**($M_2 \|\| K$) 相同，从而伪造有效标签并破坏 MAC 的安全性

## HMAC 构造

*基于哈希的 MAC（HMAC）* 构造允许你从哈希函数构建 MAC，其安全性高于秘密前缀或秘密后缀。HMAC 只要底层哈希是抗碰撞的就能产生安全的 PRF，但即使不是，只要哈希的压缩函数是 PRF，HMAC 仍然能产生安全的 PRF。安全的通信协议 IPsec、SSH 和 TLS 都使用过 HMAC。（你可以在 NIST FIPS 198-1 标准和 RFC 2104 中找到 HMAC 规范。）

HMAC 使用哈希函数，**哈希**，来计算 MAC 标签，如图 7-1 所示，并根据以下表达式：

**哈希**((K ⊕ *opad*) || **哈希**((K ⊕ *ipad*) || M))

值 *opad*（外填充）是十六进制字符串 5c5c5c…5c，其长度与 **哈希** 的块大小相同。密钥 K 通常短于一个块，用 00 字节填充后与 *opad* 进行异或。例如，如果 K 是 1 字节字符串 00，则 K ⊕ *opad* = *opad*。（如果 K 是长度不超过一个块的任意长度的全零字符串，也同样成立。）K ⊕ *opad* 是对 **哈希** 的外部调用处理的第一个块——即前述等式中最左边的 **哈希**，或图 7-1 中的底部哈希。

![](img/ace4de942d037de8ea5835bc9fbe57cd_171_0.png)

*图 7-1：基于压缩函数的哈希函数的 HMAC 基于哈希的 MAC 构造*

值 *ipad*（内填充）是一个字符串（363636…36），其长度与 **哈希** 的块大小相同，并用 00 字节补齐。 resulting block 是内层对 **哈希** 的调用处理的第一个块——即等式中最右边的 **哈希**，或图 7-1 中的顶部哈希。

**注意** *信封方法比秘密前缀或秘密后缀更安全。它表示为 **哈希**(K || M || K)，一种三明治 MAC，但从理论上讲比 HMAC 更不安全。*

如果使用的哈希函数 Hash 是 SHA-256，则你将 HMAC 实例称为 HMAC-SHA-256。更一般地，你将 HMAC-Hash 称为使用哈希函数 Hash 的 HMAC 实例。这意味着如果有人要求你使用 HMAC，你应该总是问：“使用哪个哈希函数？”

## 针对基于哈希的 MAC 的通用攻击

所有基于迭代哈希函数的 MAC 都存在一种攻击。回想一下第 143 页“秘密后缀构造”中的攻击，我们使用哈希碰撞来获得 MAC 的碰撞。你可以用同样的策略攻击秘密前缀 MAC 或 HMAC，尽管后果不那么严重。

图 7-2 说明了秘密前缀 MAC 哈希(K || M)。

![](img/ace4de942d037de8ea5835bc9fbe57cd_172_0.png)

图 7-2：基于哈希的 MAC 的通用伪造攻击原理

如果摘要为 n 位，你可以通过向持有密钥的系统请求大约 2^{n/2} 个 MAC 标签，找到两个消息 M1 和 M2，使得 Hash(K || M1) = Hash(K || M2)。（回想一下第 6 章的生日攻击。）如果哈希容易受到长度扩展，如 SHA-256，则你可以使用 M1 和 M2 来伪造 MAC，通过选择任意数据 M3，然后查询 MAC 随机预言机获取 Hash(K || M1 || M3)，这是消息 M1 || M3 的 MAC。事实证明，这也是消息 M2 || M3 的 MAC，因为 M1 和 M3 以及 M2 和 M3 的哈希内部状态相同。你已成功伪造了 MAC 标签。（当 n 超过例如 128 位时，工作量变得不可行。）

即使哈希函数不受长度扩展攻击影响，该攻击也有效，并且对 HMAC 也有效。这是因为只需要哈希函数内部的碰撞，而不一定是完整的哈希。攻击的成本取决于链值大小和 MAC 的长度：如果 MAC 的链值为 512 位，其标签为 128 位，则 2^{64} 次计算会找到 MAC 碰撞，但可能找不到内部状态的碰撞，因为找到此类碰撞平均需要 2^{512/2} = 2^{256} 次操作。

## 如何从分组密码创建带密钥的哈希

许多哈希函数中的压缩函数是基于分组密码构建的（参见第 6 章）。例如，HMAC-SHA-256 PRF 是一系列对 SHA-256 压缩函数的调用，而压缩函数是一个重复一系列轮次的分组密码。换句话说，HMAC-SHA-256 是分组密码位于压缩函数内部，位于哈希内部，位于 HMAC 构造内部。那么为什么不直接使用分组密码，而要构建这样分层的构造呢？

*基于密码的 MAC（CMAC）* 就是这样一种构造：它仅凭分组密码（如 AES）创建 MAC。尽管不如 HMAC 流行，CMAC 已部署在许多系统中，包括 IPsec 套件的一部分的 Internet 密钥交换（IKE）协议。例如，IKE 使用 AES-CMAC-PRF-128 构造作为核心算法生成密钥材料（或基于 AES 且输出为 128 位的 CMAC）。CMAC 在 RFC 4493 中有规定。

## 破坏 CBC-MAC

CMAC 于 2005 年设计为 *CBC-MAC* 的改进版本，CBC-MAC 是一种更简单的基于分组密码的 MAC，源自密码块链接（CBC）分组密码工作模式（参见第 4 章“工作模式”）。

CBC-MAC，CMAC 的前身，很简单：给定分组密码，*E*，要计算消息，*M*，的标签，用全零初始值（IV）在 CBC 模式下加密 *M*，并丢弃除最后一个密文块之外的所有内容。也就是说，计算

$$C_1 = E(K, M_1),\quad C_2 = E(K, M_2 \oplus C_1),\quad C_3 = E(K, M_3 \oplus C_2)$$

依此类推，对 *M* 的每个块进行计算并仅保留最后一个 *Cᵢ*——你的 *M* 的 CBC-MAC 标签——简单，且易于攻击。

要理解 CBC-MAC 为何不安全，请考虑单块消息，$M_1$，的 CBC-MAC 标签，$T_1 = E(K, M_1)$，以及另一条单块消息，$M_2$，的标签，$T_2 = E(K, M_2)$。给定这两个对，$(M_1, T_1)$ 和 $(M_2, T_2)$，你可以推断 $T_2$ 也是两块消息 $M_1 \parallel (M_2 \oplus T_1)$ 的标签。如果你对 $M_1 \parallel (M_2 \oplus T_1)$ 应用 CBC-MAC 并计算 $C_1 = E(K, M_1) = T_1$，然后 $C_2 = E(K, (M_2 \oplus T_1) \oplus T_1) = E(K, M_2) = T_2$，你可以在不知道密钥的情况下从两个消息/标签对创建第三个消息/标签对。也就是说，你可以伪造 CBC-MAC 标签，从而破坏 CBC-MAC 的安全性。

## 修复 CBC-MAC

CMAC 通过使用与前几个块不同的密钥处理最后一个块来修复 CBC-MAC。为此，CMAC 首先从主密钥，$K$，派生两个密钥，$K_1$ 和 $K_2$，使得 $K$、$K_1$ 和 $K_2$ 各不相同。CMAC 使用 $K_1$ 或 $K_2$ 处理最后一个块，而前面的块使用 $K$。

确定 $K_1$ 和 $K_2$ 时，CMAC 首先计算一个临时值 $L = E(0, K)$，其中 0 作为分组密码的密钥，$K$ 作为

plaintext block. 然后 CMAC 将 K1 设置为 (L << 1)，如果 L 的最高有效位 (MSB) 为 0，则设置为 (L << 1) ⊕ 87，如果 L 的 MSB 为 1。（十六进制数 87，或十进制的 135，是为其数学特性而选择的，当数据块为 128 位时；当块不是 128 位时，需要不同的值。）密钥 K2 设置为 (K1 << 1)，如果 K1 的 MSB 为 0，则设置为 (K1 << 1) ⊕ 87，否则。

给定 K1 和 K2，CMAC 的工作方式与 CBC-MAC 类似，只是最后的块除外。如果最终消息块 Mn 正好是块的大小，CMAC 返回 E(K, Mn ⊕ Cn−1 ⊕ K1) 作为标签，如图 7-3 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_174_0.png)

Figure 7-3: 当消息是完整块序列时的基于块密码的 CMAC MAC 构造

如果 Mn 的位数少于一个块，CMAC 用 1 位和 0 进行填充，并返回 E(K, Mn ⊕ Cn−1 ⊕ K2) 作为标签，如图 7-4 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_174_1.png)

Figure 7-4: 当消息的最后一个块需要用 1 位和零填充以填满一个块时的基于块密码的 CMAC MAC 构造

第一种情况仅使用 K1，第二种情况仅使用 K2，但两者都使用主密钥 K 来处理最后一个之前的消息块。

与 CBC 加密模式不同，CMAC 不将 IV 作为参数，并且是确定性的：对于相同的密钥，CMAC 对给定的消息 M 总是返回相同的标签，因为 CMAC(M) 的计算不是随机的——这没问题，因为与加密不同，MAC 计算不需要随机化即可安全，这消除了选择随机 IV 的负担。

## 专用 MAC 设计

你已经看到如何回收哈希函数和块密码来构建 PRF，只要其底层哈希或密码是安全的即可。诸如 HMAC 和 CMAC 之类的方案只是简单地组合可用的哈希函数或块密码以产生安全的 PRF 或 MAC。重用可用算法很方便，但这是最有效的方法吗？

直观上，PRF 和 MAC 要比无密钥哈希函数更少的工作量即可安全——它们使用秘密密钥阻止攻击者操作算法，因为他们没有密钥。此外，PRF 和 MAC 仅向攻击者暴露短标签，而不像块密码那样暴露与消息一样长的密文。因此，PRF 和 MAC 不需要哈希函数或块密码的最大能力——这就是专用设计的意义，即专门用作 PRF 或 MAC 的算法。

以下各节重点介绍两种此类算法：Poly1305 和 SipHash。我将解释它们的设计原理以及它们（很可能）为何安全。

## Poly1305

Poly1305 算法（发音为 poly-thirteen-o-five）于 2005 年由 Daniel J. Bernstein 设计（第 5 章中 Salsa20 流密码的创建者，以及启发了第 6 章中 BLAKE 和 BLAKE2 哈希函数的 ChaCha 密码）。Poly1305 针对现代 CPU 进行了优化，速度超快，而且在我撰写本文时，它是 TLS 1.3 和 OpenSSH 中支持的算法之一，以及许多其他应用。与 Salsa20 不同，Poly1305 的设计基于可以追溯到 1970 年代的技术——即通用哈希函数和 Wegman–Carter 构造。

## 通用哈希函数

Poly1305 MAC 使用通用哈希函数。这种哈希函数比密码学哈希函数弱，但速度快得多。例如，通用哈希函数不必具有抗碰撞性。

像 PRF 一样，通用哈希由秘密密钥参数化：给定消息 M 和密钥 K，我们将通用哈希函数 UH 的输出记为 UH(K, M)。通用哈希函数只有一个安全要求：对于任意两个消息 M1 和 M2，以及随机密钥 K，UH(K, M1) 等于 UH(K, M2) 的概率必须可以忽略不计。与 PRF 不同，通用哈希不需要是伪随机的；只需不存在一对 (M1, M2) 对许多不同的密钥产生相同的哈希即可。由于其安全要求更容易满足，通用哈希函数需要的操作更少，速度明显快于 PRF。

然而，你只能使用通用哈希作为 MAC 来验证不超过一条消息。例如，考虑 Poly1305 中使用的通用多项式求值哈希。（有关此概念的更多信息，请参阅 Edgar Gilbert、Jessie MacWilliams 和 Neil Sloane 于 1974 年发表的开创性文章“Codes Which Detect Deception”。）这种多项式求值哈希由素数 p 参数化，并将由两个数字 R 和 K 组成的密钥作为输入，范围在 [1, p) 内，以及由 n 个块 (M₁, M₂, . . . , Mₙ) 组成的消息 M。然后按如下方式计算通用哈希的输出：

**UH**(R, K, M) = R + M₁K + M₂K² + M₃K³ + . . . + MₙKⁿ mod p

在此等式中，加号 (+) 表示正整数的加法，Kⁱ 是数字 K 的 i 次幂，“mod p” 表示结果模 p 的约简（即结果除以 p 的余数；例如，12 mod 10 = 2，10 mod 10 = 0，8 mod 10 = 8，等等）。

由于你希望哈希操作尽可能快，基于通用哈希的 MAC 通常使用 128 位的消息块，并使用略大于 2¹²⁸ 的素数 p，例如 2¹²⁸ + 51。128 位宽度允许通过有效使用常见 CPU 的 32 位和 64 位算术单元来实现非常快速的实现。

## 安全限制

通用哈希有一个弱点：由于通用哈希只能安全地验证一条消息，攻击者可以通过请求仅两条消息的标签来破坏前述的多项式求值 MAC。具体来说，他们可以请求所有块都为零的消息的标签——M₁ = M₂ = . . . = 0——以获得标签 UH(R, K, 0) = R，从而找到秘密值 R。或者，他们可以请求 M₁ = 1 且 M₂ = M₃ = . . . = 0 的消息的标签（其标签为 T = R + K），这允许他们通过从 T 中减去 R 来找到 K。现在攻击者知道整个密钥 (R, K) 并可以伪造任意消息的 MAC。

幸运的是，有一种方法可以从单条消息安全性过渡到多条消息安全性。

## Wegman–Carter MAC

使用通用哈希函数对多条消息进行身份验证的技巧得益于 IBM 研究员 Mark Wegman 和 Lawrence Carter 以及他们 1981 年的论文“New Hash Functions and Their Use in Authentication and Set Equality”。Wegman–Carter 构造使用通用哈希函数和 PRF 构建 MAC，使用两个密钥 K₁ 和 K₂，并返回

**MAC**(K₁, K₂, N, M) = **UH**(K₁, M) + **PRF**(K₂, N)

其中 N 是一个 nonce，必须对每个密钥 K₂ 最多使用一次，并且 PRF 的输出与通用哈希函数 UH 的输出一样大。通过将这两个值相加，PRF 的强伪随机输出掩盖了 UH 的密码学弱点。你可以将其视为通用哈希结果的加密，其中 PRF 充当流密码，并通过使能够使用相同的密钥 $K_1$ 对多条消息进行身份验证来防止前述攻击。

回顾一下，Wegman–Carter 构造 **UH**($K_1$, $M$) + **PRF**($K_2$, $N$) 在假设以下条件时提供安全的 MAC：

- **UH** 是一个安全的通用哈希。
- **PRF** 是一个安全的 PRF。
- 每个 nonce $N$ 对每个密钥 $K_2$ 仅使用一次。
- **UH** 和 **PRF** 的输出值足够长以确保足够高的安全性。

现在让我们看看 Poly1305 如何利用 Wegman–Carter 构造来构建安全且快速的 MAC。

## Poly1305-AES

Poly1305 最初被提出为 Poly1305-AES，结合了 Poly1305 通用哈希和 AES 块密码。Poly1305-AES 比基于 HMAC 的 MAC 甚至 CMAC 快得多，因为它只计算一个 AES 块，并通过一系列简单的算术运算并行处理消息。

给定 128 位的 $K_1$、$K_2$ 和 $N$ 以及消息 $M$，Poly1305-AES 返回以下内容：

$$\mathbf{Poly1305}(K_1, M) + \mathbf{AES}(K_2, N) \bmod 2^{128}$$

mod $2^{128}$ 约简确保结果适合 128 位。Poly1305 将消息 $M$ 解析为 128 位块的序列 ($M_1$, $M_2$, …, $M_n$) 并在每个块的最高有效位附加第 129 位，使所有块长度为 129 位。（如果最后一个块小于 16 字节，则在最后的第 129 位之前用 1 位后跟 0 位进行填充。）接下来，Poly1305 求值多项式以计算以下内容：

$$\mathbf{Poly1305}(K_1, M) = M_1K_1^n + M_2K_1^{n-1} + \cdots + M_nK_1 \bmod 2^{130} - 5$$

该表达式的结果是一个最多 129 位长的整数。当你将其与 128 位值 **AES**($K_2$, $N$) 相加时，结果被约简为模 $2^{128}$ 以产生 128 位 MAC。

> > **注意**  *我将 Wegman–Carter 描述为使用 PRF，但 AES 不是 PRF，它是伪随机置换 (PRP)。然而，这并不重要，因为 Wegman–Carter 构造对 PRP 和 PRF 都适用。这是因为如果你得到一个是 PRF 还是 PRP 的函数，仅通过查看函数的输出值很难判断它是 PRF 还是 PRP。换句话说，区分 PRP 和 PRF 在计算上是困难的。*

Poly1305-AES 的安全性分析（参见 https://cryp.to/mac/poly1305-20050329.pdf 中的“The Poly1305-AES Message-Authentication Code”）显示

Poly1305-AES 只要 AES 是一个安全的分组密码，并且像任何密码算法一样实现正确，就是 128 位安全的。

你可以将 Poly1305 通用哈希与其他算法结合使用，而不仅仅是 AES。例如，Poly1305 与流密码 ChaCha 结合使用（参见 RFC 7539，“ChaCha20 and Poly1305 for IETF Protocols”）。毫无疑问，只要需要快速 MAC，Poly1305 将继续被使用。

尽管 Poly1305 快速且安全，但它也有几个缺点。首先，其多项式求值难以高效实现，尤其对于不熟悉相关数学概念的人来说。（参见 https://github.com/floodyberry/poly1305-donna 中的示例。）其次，单独使用时，除非使用 Wegman-Carter 构造，否则它仅对一条消息安全。但在这种情况下它需要一个 nonce，如果 nonce 重复，算法就会变得不安全。最后，Poly1305 针对长消息进行了优化，但如果仅处理小消息（例如少于 128 字节），则大材小用。在这种情况下，SipHash 是一个不错的解决方案。

## SipHash

我于 2012 年与 Dan Bernstein 一起设计了 SipHash，最初是为了解决一个非密码学问题：哈希表上的拒绝服务攻击。哈希表是一种数据结构，尤其在编程语言中用于高效地在内部存储元素。在 SipHash 之前，哈希表依赖于非密码学的带密钥哈希函数，其中碰撞通常很容易找到，这可以被利用来减慢系统并执行拒绝服务攻击。我们观察到 PRF 可以解决这个问题，于是着手设计 SipHash，一种适用于哈希表的 PRF。由于哈希表大多处理短输入，SipHash 针对短消息进行了优化。SipHash 是一种完整的 PRF 和 MAC，在大多数输入都很短的情况下表现出色。

SipHash 使用了一种使其比基本海绵函数更安全的技巧：而不是仅在置换之前对消息块进行一次 XOR，SipHash 在置换之前和之后都对其进行 XOR，如图 7-5 所示。SipHash 的 128 位密钥被视为两个 64 位字 K₁ 和 K₂，与一个 256 位固定初始状态进行 XOR，该状态被视为四个 64 位字。接下来丢弃密钥，计算 SipHash 归结为迭代一个名为 SipRound 的核心函数，然后对消息块进行 XOR 以修改四字内部状态。最后，SipHash 通过将四个状态字进行 XOR 返回一个 64 位标签。

![](img/ace4de942d037de8ea5835bc9fbe57cd_179_0.png)

图 7-5：SipHash-2-4 处理 15 字节消息（一个块 M₁ 为 8 字节，一个块 M₂ 为 7 字节，外加 1 字节填充）

SipRound 函数使用大量 XOR 以及加法和字旋转来使函数安全。SipRound 通过执行以下操作，自上而下地转换四个 64 位字（a、b、c、d）的状态。左侧和右侧的操作是独立的，可以并行执行：

```
a += b      c += d
b <<= 13    d <<= 16
b ⊕= a      d ⊕= c
a <<= 32
c += b      a += d
b <<= 17    d <<= 21
b ⊕= c      d ⊕= a
c <<= 32
```

这里，a += b 是 a = a + b 的简写，而 b <<= 13 是 b = b <<< 13 的简写（64 位字 b 左旋转 13 位）。

这些对 64 位字的简单操作几乎是你实现计算 SipHash 所需的全部——尽管你不必自己实现它。你可以在大多数语言中找到现成的实现，例如 C、Go、Java、JavaScript、Python 和 Rust。

NOTE 我将 SipHash-x-y 写为 SipHash 版本，表示它在每次消息块注入之间执行 x 次 SipRound，然后执行 y 轮。更多的轮次需要更多的操作，这会减慢操作速度，但也会提高安全性。默认版本是 SipHash-2-4（简称为 SipHash），迄今为止它已抵御了密码分析。注意我还定义了 SipHash128，这是一个产生 128 位标签的 SipHash 版本。

许多系统，例如 Rust 语言、OpenBSD 操作系统和比特币区块链，内部使用 SipHash。Linux 内核也使用 SipHash，并使用 HalfSipHash，“SipHash 的不安全的小弟”，这是一个具有 64 位密钥和 32 位输出的较小版本（参见 https://docs.kernel.org/security/siphash.html）。

```python
if len(x) != n:
    return False
for i in range(n):
    if x[i] != y[i]:
        return False
return True

#### Each call to compare_mac() will look at all 16 characters.
start = time()
for i in range(TRIALS):
    compare_mac(MAC1, MAC1, len(MAC1))
end = time()
print("%.5f" % (end-start))

#### Each call to compare_mac() will look at three characters.
start = time()
for i in range(TRIALS):
    compare_mac(MAC1, MAC2, len(MAC1))
end = time()
print("%.5f" % (end-start))
```

*清单 7-2：测量执行来自清单 7-1 的 `compare_mac()` 时的时序差异*

在配备 ARM M1 芯片的 MacBook Pro 上，清单 7-2 中程序的执行打印出大约 67 和 26 毫秒的执行时间，分别如此。这一差异足以识别算法内部发生的情况。现在将差异移动到字符串中的其他偏移位置，你会观察到不同偏移位置有不同的执行时间。如果 MAC₁ 是正确的 MAC 标签而 MAC₂ 是攻击者尝试的标签，你可以轻松识别出第一个差异的位置，这就是正确猜测的字节数。

如果执行时间不依赖于秘密时序，时序攻击就不会奏效，这就是为什么实现者力求编写 *常量时间* 实现的原因——即代码对于任何秘密输入值完成所需的时间完全相同。例如，清单 7-3 中的 C 函数以恒定时间比较两个大小为 bytes 的缓冲区：临时变量 `result` 当且仅当两个缓冲区中存在差异时才不为零。

```c
int cmp_const(const void *a, const void *b, const size_t size)
{
    const unsigned char *pa = (const unsigned char *) a;
    const unsigned char *pb = (const unsigned char *) b;
    unsigned char result = 0;
    size_t i;

    for (i = 0; i < size; i++) {
        result |= pa[i] ^ pb[i];
    }

    return result; /* Returns 0 if *a and *b are equal, nonzero otherwise */
}
```

*清单 7-3：用于更安全 MAC 验证的两个缓冲区的恒定时间比较*

## 当海绵泄漏时

像 SHA-3 和 SipHash 这样的基于置换的算法简单、易于实现，并且具有紧凑的实现，但在会恢复系统状态快照的侧信道攻击面前很脆弱。例如，如果一个进程可以随时读取 RAM 和寄存器的值或读取内存的核心转储，攻击者可以确定 MAC 模式下 SHA-3 的内部状态，或 SipHash 的内部状态，然后计算置换的逆向以恢复初始秘密状态。然后他们可以为任意消息伪造标签，破坏 MAC 的安全性。

幸运的是，这种攻击对基于压缩函数的 MAC 例如 HMAC-SHA-256 和带密钥的 BLAKE2 无效，因为攻击者需要在密钥使用时的确切时刻获取内存快照。

因此，如果你处于进程内存的某些部分可能泄漏的环境中，可以使用基于不可逆变换压缩函数的 MAC，而不是基于置换的 MAC。

## 进一步阅读

 venerable 的 HMAC 值得比我在这里能容纳的更多关注，尤其对于导致其被广泛采用并最终在与弱哈希函数结合时衰落的思路链。我推荐 Mihir Bellare、Ran Canetti 和 Hugo Krawczyk 于 1996 年发表的论文“Keying Hash Functions for Message Authentication”，该论文介绍了 HMAC 及其表亲 NMAC，以及 Bellare 于 2006 年发表的后续论文“New Proofs for NMAC and HMAC: Security Without Collision-Resistance”，该论文证明 HMAC 不需要抗碰撞哈希，而只需要一个压缩函数是 PRF 的哈希。在进攻方面，Pierre-Alain Fouque、Gaëtan Leurent 和 Phong Nguyen 于 2007 年发表的论文“Full Key-Recovery Attacks on HMAC/NMAC-MD4 and NMAC-MD5”展示了如何攻击在 MD4 或 MD5 等脆弱哈希函数之上构建的 HMAC 和 NMAC。（HMAC-MD5 和 HMAC-SHA1 并非完全被破坏，但风险已经很高。）

Wegman-Carter MAC 也值得更多关注，既因其实际兴趣，也因其底层理论。Wegman 和 Carter 的开创性论文可在 https://cr.yp.to/bib/entries.html 获取。其他最先进的设计包括 UMAC 和 VMAC，它们是长消息上最快的 MAC 之一。

本章未讨论的一种 MAC 类型是 Pelican，它使用降至四轮的 AES 分组密码（完整分组密码为 10 轮）来在简化的构造中对消息块进行身份验证，如 https://eprint.iacr.org/2005/088 中所述。Pelican 更像是一个好奇心，在实践中很少使用。

最后但并非最不重要，如果你有兴趣寻找密码软件中的漏洞，请寻找 CBC-MAC 的使用或由 HMAC 处理任意大小密钥引起的弱点——将 Hash(K) 作为密钥

如果 *K* 太长，则使用 **Hash**(*K*) 而不是 *K*，从而使 *K* 和 **Hash**(*K*) 成为等效密钥。或者只是寻找那些应该使用 MAC 却没有使用 MAC 的系统——这种情况经常发生。

在第 8 章中，我们将结合 MAC 和密码来保护消息的 *真实性*、*完整性* 和 *保密性*。我们还将在没有 MAC 的情况下实现这一点，得益于经过身份验证的密码，它们将基本密码的功能与 MAC 的功能结合起来，通过在每个密文旁边返回一个标签来实现。

## 8
### AUTHENTICATED ENCRYPTION

![](img/ace4de942d037de8ea5835bc9fbe57cd_184_0.png)

本章介绍一种算法类型，它不仅保护消息的保密性，还保护其真实性。回顾第 7 章，消息认证码（MAC）通过创建标签来保护消息的真实性，标签是一种签名。与 MAC 类似，本章中的经过身份验证的加密（AE）算法会生成认证标签，但它们也会加密消息。换句话说，单个 AE 算法提供了普通密码和 MAC 的功能。

结合密码和 MAC 可以实现不同程度的认证加密，正如你在本章中将学到的那样。我们将回顾几种结合 MAC 和密码的方法，讨论哪些方法最安全，并探讨能够同时生成密文和认证标签的密码。然后我们将介绍四种重要的认证密码：三种基于分组密码的构造，重点关注流行的伽罗华计数器模式下的高级加密标准（AES-GCM），以及一种仅使用置换算法的密码。

### Authenticated Encryption Using MACs

图 8-1 显示了三种将 MAC 和密码结合起来同时加密和认证明文的方法：encrypt-and-MAC、MAC-then-encrypt 和 encrypt-then-MAC。

![](img/ace4de942d037de8ea5835bc9fbe57cd_185_0.png)

图 8-1：密码和 MAC 组合

这些组合在应用加密和生成认证标签的顺序上有所不同。只要每种算法本身安全，并且 MAC 和密码使用不同的密钥，具体选择哪种 MAC 或密码算法并不重要。

在 encrypt-and-MAC 组合中，明文被加密，并且认证标签直接从明文生成，使得两个操作（加密和认证）相互独立，因此可以并行计算。在 MAC-then-encrypt 方案中，你首先从明文生成标签，然后将明文和 MAC 一起加密。在 encrypt-then-MAC 方法中，你首先加密明文，然后从密文生成标签。让我们看看哪种方法可能最安全。

### Encrypt-and-MAC Approach

encrypt-and-MAC 方法分别计算密文和 MAC 标签。给定明文 P，发送方计算密文 C = E(K₁, P)，其中 E 是加密算法，C 是所得密文。你从明文计算认证标签 T，T = MAC(K₂, P)。这两个操作相互独立，因此可以并行计算。

一旦生成了密文和认证标签，发送方就会将两者都传输给预期接收方。当接收方收到 C 和 T 时，他们通过计算 P = D(K₁, C) 解密 C 以获得明文 P。接下来，他们使用解密后的明文计算 MAC(K₂, P) 并将结果与收到的 T 进行比较。此验证如果 C 或 T 被损坏则会失败，消息被视为无效。

理论上，encrypt-and-MAC 是最不安全的 MAC 和密码组合，因为即使是安全的 MAC 也可能泄露有关 P 的信息，从而使 P 更容易恢复。因为使用 MAC 的目标只是使标签不可伪造，并且标签不一定看起来是随机的，所以明文 P 的认证标签 T 即使 MAC 被认为安全也可能仍然泄露信息！（如果 MAC 是伪随机函数，标签不会泄露有关 P 的任何信息。）

尽管相对较弱，许多系统仍继续支持 encrypt-and-MAC，包括安全传输层协议 SSH，其中每个加密数据包 C 后面跟着标签 T = MAC(K, N || P)，其中 N 是每个数据包递增的 32 位序列号。在实践中，encrypt-and-MAC 对于 SSH 使用已证明足够好，这得益于使用 HMAC-SHA-256 等不会泄露有关 P 的信息的强 MAC 算法。输入以下命令

```
$ ssh -Q mac
```

即可查看 OpenSSH 软件支持的 MAC 列表。

### MAC-Then-Encrypt Composition

MAC-then-encrypt 组合通过首先计算认证标签 T = MAC(K₂, P) 来保护消息 P。接下来，它通过根据 C = E(K₁, P || T) 加密明文和标签一起创建密文。

完成这些步骤后，发送方仅传输 C，其中包含加密的明文和标签。接收后，接收方通过计算 P || T = D(K₁, C) 解密 C 以获得明文和标签 T。接下来，接收方通过根据 MAC(K₂, P) 直接从明文计算标签来验证收到的标签 T，以确认计算出的标签等于标签 T。

与 encrypt-and-MAC 一样，使用 MAC-then-encrypt 时，接收方必须在确定是否接收到损坏的数据包之前解密 C——此过程会将可能损坏的明文暴露给接收方。尽管如此，MAC-then-encrypt 比 encrypt-and-MAC 更安全，因为它隐藏了明文的认证标签，从而防止标签泄露有关明文的信息。

TLS 协议多年来一直使用 MAC-then-encrypt，但 TLS 1.3 用经过身份验证的密码取代了 MAC-then-encrypt（有关 TLS 1.3 的更多信息，请参阅第 13 章）。

### Encrypt-Then-MAC Composition

encrypt-then-MAC 组合向接收方发送两个值：由 C = E(K₁, P) 产生的密文和基于密文的标签 T = MAC(K₂, C)。接收方使用 MAC(K₂, C) 计算标签并验证其是否等于收到的 T。如果值相等，则明文计算为 P = D(K₁, C)；如果不相等，则丢弃密文。

此方法的一个优点是接收方只需计算 MAC 以检测损坏的消息，因此无需解密损坏的密文。此外，除非攻击者破坏了 MAC，否则攻击者无法向接收方发送 C 和 T 对以进行解密，这使得攻击者更难向接收方传输恶意数据。

这种功能组合使 encrypt-then-MAC 比 encrypt-and-MAC 和 MAC-then-encrypt 方法更强。这也是广泛使用的 IPsec 安全通信协议套件使用它来保护数据包（例如在 VPN 隧道内）的原因之一。

请注意，SSH 和 TLS 不使用 encrypt-then-MAC，因为在创建 SSH 和 TLS 时其他方法似乎已足够——不是因为理论上的弱点不存在，而是因为不良属性不一定会成为实际漏洞。

### Authenticated Ciphers

经过身份验证的密码是密码和 MAC 组合的替代方案。它们与普通密码类似，只是它们会连同密文一起返回认证标签。

你将经过身份验证的密码加密表示为 AE(K, P) = (C, T)。术语 AE 代表经过身份验证的加密，它基于密钥（K）和明文（P），返回密文（C）和生成的认证标签（T）。换句话说，单个经过身份验证的密码算法完成与密码和 MAC 组合相同的工作，使其更简单、更快，通常更安全。

你通过 AD(K, C, T) = P 表示经过身份验证的密码解密。在这里，AD 代表经过身份验证的解密，它根据密文（C）、标签（T）和密钥（K）返回明文（P）。如果标签验证失败，AD 会返回错误，以防止接收方处理可能被伪造的明文。同理，如果 AD 返回明文，则它是由知道秘密密钥的人或事物加密的。

经过身份验证的密码的基本安全要求很简单：其认证应与 MAC 一样强，这意味着不可能伪造解密函数 AD 将接受并解密的密文和标签对（C, T）。

就保密性而言，经过身份验证的密码从根本上比基本密码更强，因为持有秘密密钥的系统只有在认证标签有效时才会解密密文。如果标签无效，则明文将被丢弃。此特性可防止攻击者执行选择密文查询，即他们创建密文并请求相应明文的攻击。

### Authenticated Encryption with Associated Data

密码学家将关联数据定义为经过身份验证的密码处理的任何数据，使得数据经过认证（得益于认证标签）但未被加密。默认情况下，输入经过身份验证的密码的所有明文数据都会被加密和认证。



假设你想要对消息进行认证，包括其未加密的部分，但不加密整个消息——也就是说，你希望在加密消息之外对数据进行认证和传输。例如，如果密码处理由头部后跟有效载荷组成的网络数据包，你可能会选择加密有效载荷以隐藏传输的实际数据，但不加密头部，因为它包含将数据包传递给最终接收者的所需信息。同时，你可能仍然希望对头部的数据进行认证，以确保它来自预期的发送者。

为了实现这些目标，密码学家提出了*关联数据认证加密 (AEAD)*的概念。AEAD 算法允许你以这样的方式将明文数据附加到密文上：如果明文数据被损坏，认证标签将无法验证，并且密文将无法解密。此类明文数据必须以安全的方式进行编码和序列化，以防止对其内容产生歧义解释。

你可以将 AEAD 操作写为 **AEAD**(*K*, *P*, *A*) = (*C*, *A*, *T*)。给定密钥 (*K*)、明文 (*P*) 和关联数据 (*A*)，AEAD 返回密文、未加密的关联数据 *A* 以及认证标签。AEAD 保持未加密的关联数据不变，而密文是明文的加密。认证标签同时依赖于 *P* 和 *A*，只有在 *C* 和 *A* 都未被修改时才会被验证为有效。

由于认证标签依赖于 *A*，你通过 **AD**(*K*, *C*, *A*, *T*) = (*P*, *A*) 计算带关联数据的解密。解密需要密钥、密文、关联数据和标签来计算明文和关联数据，如果 *C* 或 *A* 被损坏则会失败。

使用 AEAD 时，你可以让 *A* 或 *P* 为空。如果关联数据 *A* 为空，AEAD 成为普通的认证密码；如果 *P* 为空，它就只是 MAC。

> NOTE
> *截至本文撰写时，AEAD 是认证加密的当前规范。由于今天使用的几乎所有认证密码都支持关联数据，因此在整本书中提到认证密码时，我指的是 AEAD，除非另有说明。在讨论 AEAD 的加密和解密操作时，我将分别称它们为 **AE** 和 **AD**。*

## 可预测性与随机数

回想一下第 1 章的内容，为了安全，加密方案必须不可预测，并且在重复调用加密相同明文时返回不同的密文——否则，攻击者可以确定是否对相同的明文进行了两次加密。为了实现不可预测性，分组密码和流密码会向密码提供一个额外参数：初始值 (IV) 或 *nonce*——一个只能使用一次的数字。认证密码使用相同的技巧。因此，你可以将认证加密表示为 **AE**(*K*, *P*, *A*, *N*)，其中 *N* 是 nonce。选择从未与同一密钥一起使用过的 nonce 是加密操作的工作。

与分组密码和流密码一样，使用认证密码解密需要用于加密的 nonce 才能正确执行。因此你可以将解密表示为 AD(K, C, A, T, N) = (P, A)，其中 N 是用于创建 C 和 T 的 nonce。

## 良好认证密码的标准

研究人员自 2000 年代初以来一直在努力定义什么构成一个良好的认证密码，而答案仍然难以捉摸。由于 AEAD 的许多输入发挥不同的作用，定义安全性的概念比仅加密消息的基本密码更困难。例如，研究论文“Nonces Are Noticed: AEAD Revisited”，可在 https://eprint.iacr.org/2019/624 获取，提出了基于 nonce 的加密的理论框架。尽管如此，在本节中，我将总结在评估认证密码的安全性、性能和功能时需要考虑的最重要标准。

### 安全

衡量认证密码强度的最重要的标准是其保护数据机密性（即明文的保密性）以及通信的真实性和完整性的能力（如 MAC 检测损坏消息的能力）。认证密码必须在两个领域都竞争：其机密性必须与最强的密码一样强，其真实性必须与最好的 MAC 一样强。换句话说，如果你在 AEAD 中去掉认证部分，你应该得到一个安全的密码，如果去掉加密部分，你应该得到一个强大的 MAC。

衡量认证密码安全强度的另一个指标基于其在面对重复 nonce 时的脆弱性。例如，如果 nonce 被重用，攻击者能否解密密文或获知明文之间的差异？

研究人员称这种鲁棒性为抗误用性，并设计了抗误用认证密码以衡量重复 nonce 的影响，并尝试确定在这种攻击面前机密性、真实性或两者是否会被损害，以及关于加密数据的哪些信息可能会泄露。

### 性能

与每种密码算法一样，你以每秒处理的位数来衡量认证密码的吞吐量。这种速度取决于密码算法执行的运算数量以及认证功能的额外成本。认证密码的额外安全特性会带来性能损失。然而，衡量密码性能不仅仅是关于纯速度。它还关乎可并行性、结构以及密码是否可流式处理。让我们更详细地审视这些概念。

密码的可并行性是指其在无需等待前一个数据块处理完成的情况下同时处理多个数据块的能力。基于分组密码的设计在每个数据块可以独立于其他数据块处理时很容易实现并行化。例如，第 4 章中的 CTR 分组密码模式是可并行化的，而 CBC 加密模式则不可并行化，因为数据块是链式的。

认证密码的内部结构是另一个重要的性能标准。有两种主要结构类型：单层和双层。在双层结构中（例如广泛使用的 AES-GCM），一个算法处理明文，然后第二个算法处理结果。通常，第一层是加密层，第二层是认证层。但正如你可能预期的那样，双层结构使实现复杂化并倾向于减慢计算速度。

认证密码是可流式处理的（也称为在线密码），当它可以逐块处理消息并丢弃已处理的任何块时。与此相反，非流式密码必须存储整个消息，通常是因为它们需要对数据进行两次连续传递：一次从开始到结束，另一次从结束到开始，数据来自第一次传递。

由于潜在的高内存需求，一些应用程序无法使用非流式密码。例如，路由器可以接收加密的数据块，对其解密，然后在继续解密消息的后续数据块之前返回明文块，尽管解密消息的接收者仍需要在解密的数据流末尾发送的认证标签进行验证。

### 其他特性

功能标准是密码或其实现的功能特性，这些特性与安全或性能没有直接关系。例如，一些认证密码只允许关联数据在待加密数据之前（因为它们需要访问它来开始加密）。其他密码要求关联数据跟随待加密数据，或支持关联数据包含在任何位置——甚至在明文块之间。这最后一种情况是最好的，因为它使用户能够在任何可能的情况下保护其数据，但它也是最难安全设计的：更多功能通常带来更多复杂性和潜在漏洞。

另一个需要考虑的功能标准与是否可以使用相同的核心算法进行加密和解密有关。例如，许多认证密码基于 AES 分组密码，该密码规定使用两种相似的算法来加密和解密一个块。如第 4 章所述，CBC 分组密码模式需要两种算法，但 CTR 模式只需要加密算法。同样，认证密码可能不需要两种算法。虽然实现加密和解密算法的额外成本不会影响大多数软件，但在低成本专用硬件上通常很明显，在那里你以逻辑门的数量或密码学占用的硅面积来衡量实现成本。




## AES-GCM 认证加密标准

AES-GCM 是使用最广泛的认证加密算法。AES-GCM 基于 AES 算法，其伽罗瓦计数器模式（GCM）本质上是 CTR 模式的一种变体，通过加入一个小巧高效的组件来计算认证标签。在撰写本文时，AES-GCM 已是 NIST 标准（SP 800-38D），也是 NSA Suite B 的组成部分，并被 IETF 认可用于 IPsec、SSH 以及 TLS 1.2 和 1.3 等安全网络协议。

注意 虽然 GCM 适用于任何分组密码，但你很可能只会看到它与 AES 搭配使用。

### GCM 内部机制

图 8-2 展示了 AES-GCM 的工作方式：由秘密密钥（K）参数化的 AES 实例将随机数（N）与计数器（此处从 1 开始，随后递增至 2、3，依此类推）拼接而成的数据块进行变换，然后将结果与明文块进行异或运算，从而得到密文块。到目前为止，与 CTR 模式相比，这并无新意。

![](img/ace4de942d037de8ea5835bc9fbe57cd_191_0.png)

图 8-2：AES-GCM 模式，应用于一个关联数据块 A1 和两个明文块 P1 与 P2。带圆圈的乘号表示以 H 为乘数的多项式乘法，H 是从 K 推导出的认证密钥。

随后，密文块通过异或运算和乘法运算的组合进行混合（你将在下文看到）。你可以将 AES-GCM 视为执行（1）CTR 模式下的加密和（2）对密文块计算 MAC。因此，AES-GCM 本质上是一种先加密后 MAC 的构造，其中 AES-CTR 使用 128 位密钥（K）和 96 位随机数（N）进行加密。

为了认证密文，GCM 使用 Wegman–Carter MAC（参见第 7 章），它将 AES(K, N || 0) 与通用哈希函数 GHASH 的输出进行异或运算。在图 8-2 中，GHASH 对应一系列“⊗_H”运算，随后与 len(A) || len(C) 进行异或，即 A（关联数据）的比特长度后接 C（密文）的比特长度。

因此，你可以将认证标签的值表示为 T = GHASH(H, A, C) ⊕ AES(K, N || 0)，其中 H 是哈希密钥，即认证密钥。该密钥通过 H = AES(K, 0) 确定，即对全零字节序列组成的数据块进行加密（为清晰起见，我在图 8-2 中未包含此步骤）。

> 在 GCM 中，GHASH 不直接使用 K，以确保即使 GHASH 的密钥被泄露，主密钥 K 仍然保密。给定 K，你可以通过计算 AES(K, 0) 获得 H，但无法从该值恢复 K，因为 K 在此处充当 AES 的密钥。

GHASH 使用多项式记法将每个密文块与认证密钥 H 相乘。这种多项式乘法的使用使 GHASH 在硬件和软件中都能快速运行，这得益于许多常见微处理器中提供的一种特殊多项式乘法指令（CLMUL，即无进位乘法）。

遗憾的是，GHASH 远非理想。首先，其速度并非最优。即使使用 CLMUL 指令，负责加密明文的 AES-CTR 层仍然比 GHASH MAC 更快。其次，GHASH 的正确实现相当困难。事实上，就连 OpenSSL 项目中经验丰富的开发者——该软件无疑是世界上使用最广泛的加密软件——也曾在 AES-GCM 的 GHASH 实现上出错。某次提交在 gcm_ghash_clmul 函数中存在一个 bug，使得攻击者能够为 AES-GCM 伪造有效的 MAC。（幸运的是，英特尔工程师在该 bug 进入下一个 OpenSSL 版本之前发现了这一错误。）

### 多项式乘法

虽然比经典整数运算更复杂，但多项式乘法对计算机来说更简单，因为没有进位。具体来说，你可以在一个由给定多项式定义的结构中计算多项式的模乘（这种结构称为商环）。例如，假设要计算多项式 (1 + X + X²) 和 (1 + X²) 关于模 (1 + X + X³) 的乘积。你首先像做普通多项式乘法一样将两个多项式 (1 + X + X²) 和 (1 + X²) 相乘，得到以下结果（其中 X² 项相互抵消，因为你处理的是布尔多项式，在此领域中 1 + 1 = 0）：

```
(1 + X + X²) ⊗ (1 + X²) = 1 + X + X³ + X⁴
```

需要等到所有关联数据被读取并完成哈希后，才能开始对第一个密文块进行哈希。

然而，GCM 是可流式处理的：由于其两个层中的计算可以流水线化，无需在计算 GHASH 前存储所有密文块，因为 GHASH 会在每个密文块被加密的同时对其进行处理。换句话说，$P_1$ 加密得到 $C_1$，然后在 $P_2$ 加密得到 $C_2$ 的过程中 GHASH 处理 $C_1$，之后 $P_1$ 和 $C_1$ 不再需要，依此类推。

## OCB 认证加密模式

*偏移码本模式（OCB）*于 2001 年首次开发，早于 GCM。与 GCM 一样，它也能从分组密码产生认证加密，但速度更快、实现更简单。OCB 之所以尚未被广泛采用，是因为在 2021 年之前，OCB 的使用受到专利保护，需要获得其发明者的许可。OCB 现已免费，任何人都可在任何应用中使用。

与 GCM 不同，OCB 将加密和认证融合为单一处理层，仅使用一个密钥。没有独立的认证层，因此 OCB 几乎免费地提供了认证功能，其分组密码调用次数与非认证密码几乎相同——OCB 几乎和 ECB 模式（参见第 4 章）一样简单，只是它更安全。

### OCB 内部机制

图 8-3 展示了 OCB 的工作方式：它将每个明文块 $P$ 加密为密文块 $C = E(K, P \oplus O) \oplus O$，其中 $E$ 是分组密码加密函数。此处，$O$（*偏移量*）是一个取决于密钥和随机数的值，每处理一个新块时随机数都会递增。

![](img/ace4de942d037de8ea5835bc9fbe57cd_194_0.png)

*图 8-3：OCB 加密过程，应用于两个明文块，无关联数据*

为了生成认证标签，OCB 首先将明文块进行异或运算以计算 $S = P_1 \oplus P_2 \oplus P_3 \oplus \cdots$。标签随后为 $T = E(K, S \oplus O^*)$，其中 $O^*$ 是根据最后一个已处理明文块的偏移量计算出的偏移值。

与 AES-GCM 一样，OCB 也支持以块序列 A₁、A₂ 等形式存在的关联数据。当 OCB 加密消息包含关联数据时，认证标签按以下公式计算

T = E(K, S ⊕ O*) ⊕ E(K, A₁ ⊕ O₁) ⊕ E(K, A₂ ⊕ O₂) ⊕ …

其中 OCB 定义了不同于加密 P 所使用的偏移量。

与 GCM 和先加密后 MAC 不同，后者通过组合密文块来形成标签，而 OCB 通过组合明文数据来计算认证标签。这种方法并无不妥，OCB 有可靠的安全性证明作为支撑。

注意 关于如何实现 OCB 的更多信息，请参阅 RFC 7253 或 Ted Krovetz 和 Phillip Rogaway 于 2011 年发表的论文《认证加密模式的软件性能》，该论文涵盖了最新且最佳版本的 OCB 即 OCB3。有关 OCB 的更多细节，请参阅 http://web.cs.ucdavis.edu/rogaway/ocb/ocb-faq.htm 上的常见问题解答。

### OCB 安全性

在重复使用随机数的情况下，OCB 比 GCM 稍显稳健。如果你两次使用同一个随机数，攻击者观察到两个密文后可能会注意到，例如，第一条消息的第三个明文块与第二条消息的第三个明文块相同。而使用 GCM 时，攻击者不仅能发现重复块，还能发现相同位置块之间的异或差异。因此，重复随机数对 GCM 的影响比对 OCB 更严重。

与 GCM 一样，重复随机数也会危及 OCB 的认证性，尽管破坏力较弱。例如，攻击者可以组合两条使用 OCB 认证的消息中的块，创建另一条加密消息，其校验和与标签与两条原始消息之一相同，但攻击者无法像 GCM 那样恢复秘密密钥。

2023 年，密码学家发现，将 OCB3 与极短随机数（6 位）一起使用会显著降低其安全性；参见 https://eprint.iacr.org/2023/326 上的文章。请注意，OCB2 版本已被破解，如 https://eprint.iacr.org/2019/311.pdf 上的文章所述。

### OCB 效率

OCB 和 GCM 的效率大致相当。与 GCM 一样，OCB 具有可并行化和可流式处理的特性。在原始效率方面，GCM 和 OCB 对底层分组密码（通常为 AES）的调用次数差不多，但 OCB 比 GCM 略快，因为它只需对明文进行异或运算，而不需要执行像 GHASH 那样相对昂贵的计算。（在早期几代英特尔微处理器中，AES-GCM 的速度曾经比 AES-OCB 慢三倍以上，因为 AES 和 GHASH 指令需要竞争 CPU 资源，无法并行运行。）




OCB 与 GCM 实现之间的一个重要区别是，OCB 需要分组密码的加密和解密函数来进行加密和解密，当可用于加密组件的硅片有限时，这会增加硬件实现的成本。相比之下，GCM 在加密和解密时仅使用加密函数。

## SIV 认证加密模式

合成 IV（SIV）是一种认证加密模式，通常与 AES 一起使用。与 GCM 和 OCB 不同，即使两次使用相同的 nonce，SIV 也是安全的：攻击者获得使用相同 nonce 加密的两个密文时，只能得知相同的明文是否被加密了两次。与 GCM 或 OCB 不同，攻击者无法判断两条消息的第一个块是否相同，因为用于加密的 nonce 首先被计算为给定 nonce 与明文的组合。

SIV 的构造规范比 GCM 更通用。与 GCM 的 GHASH 指定详细内部结构不同，SIV 只是告诉你如何将密码算法（E）和伪随机函数（PRF）组合起来得到一个认证加密算法：首先计算标签 T = PRF(K1, N || P)，然后计算密文 C = E(K2, T, P)，其中 T 充当 E 的 nonce。因此，SIV 需要两个密钥（K1 和 K2）和一个 nonce（N）。

SIV 的主要限制是它不可流式处理：在计算 T 之后，它必须将整个明文 P 保存在内存中。换句话说，要使用 SIV 加密 100GB 的明文，必须首先存储这 100GB，以便 SIV 加密能够读取它。

基于 2006 年 Phillip Rogaway 和 Thomas Shrimpton 的论文《Deterministic Authenticated-Encryption》，RFC 5297 文档规定 SIV 使用 CMAC-AES（一种使用 AES 的 MAC 构造）作为 PRF，并使用 AES-CTR 作为密码算法。2015 年，有人提出了更高效的 SIV 版本 GCM-SIV，它结合了 GCM 快速的 GHASH 函数和 SIV 的模式，速度几乎与 GCM 一样快。然而，与原始 SIV 一样，GCM-SIV 也不可流式处理。（更多信息，请参阅 https://eprint.iacr.org/2015/102。）

## 基于置换的 AEAD

现在介绍一种构建认证加密算法的完全不同的方法：我们将不围绕像 AES 这样的分组密码构建操作模式，而是考察一种围绕置换构建模式的密码算法。置换只是将输入可逆地转换为相同大小的输出，不涉及密钥，这是能想象到的最简单的组件。更好的是，由此产生的 AEAD 速度很快，可证明安全，并且比 GCM 和 OCB 更能抵抗 nonce 重用。

图 8-4 展示了基于置换的 AEAD 的工作原理：从一个固定的初始状态 H0 开始，你将密钥 K 和随后的 nonce N 异或到内部

在性能方面，基于置换的密码算法具有单层操作、可流式处理以及使用单核算法进行加密和解密的优点。然而，它们不像 GCM 或 OCB 那样可并行化，因为对 **P** 的新调用需要等待上一次调用完成。

> > **注意**
> >
> > *如果你想挑选自己喜爱的置换并自行设计认证加密密码，请不要这样做。你很可能会在细节上出错，最终得到不安全的密码。请阅读经验丰富的密码学家为 Keyak（一种源自 Keccak 的算法）、Duplex 构造和 deck 函数等算法编写的规范，见 https://keccak.team。你会发现基于置换的密码算法比乍一看要复杂得多。*

## 可能出错的地方

认证加密算法比哈希函数或分组密码具有更大的攻击面，因为它们旨在同时实现机密性*和*真实性。它们接受几种不同的输入值，并且无论输入只包含关联数据而不含加密数据、包含极大的明文，还是使用不同的密钥长度，都必须保持安全。它们还必须对所有 nonce 值保持安全，以抵御收集大量消息/标签对的攻击者，并且在一定程度上抵御 nonce 的意外重复。

这要求很高，甚至连 AES-GCM 也有几个不完美之处。

### AES-GCM 与弱哈希密钥

AES-GCM 的弱点之一在于其认证算法 GHASH：哈希密钥 *H* 的某些值会大大简化针对 GCM 认证机制的攻击。具体来说，如果 *H* 属于所有 128 位字符串中某些特定的、数学定义的子群，攻击者或许只需打乱先前消息的块，就能猜出某条消息的有效认证标签。

要理解这一弱点，我们来看看 GHASH 是如何工作的。

### GHASH 内部结构

正如你在图 8-2 中看到的，GHASH 从一个 128 位值 *H* 开始，初始设置为 **AES**(*K*, 0)，然后反复计算

$$X_i = (X_{i-1} \oplus C_i) \otimes H$$

从 $X_0 = 0$ 开始，依次处理密文块 $C_1$、$C_2$ 等。GHASH 返回最终的 $X_i$ 来计算最终标签。

为了简单起见，假设所有 $C_i$ 都等于 1，这样对于任意 $i$ 你都有：

$$C_i \otimes H = 1 \otimes H = H$$

接着，从我们的第一个方程计算 $X_1$ 得到

$X_1 = (X_0 \oplus C_1) \otimes H = (0 \oplus 1) \otimes H = H$

将 $X_0$ 替换为 0，$C_1$ 替换为 1，得到：

$(0 \oplus 1) = 1$

利用 $\otimes$ 对 $\oplus$ 的分配律，我们将 $X_1$ 替换为 $H$，将 $C_2$ 替换为 1，然后计算下一个值 $X_2$ 为

$X_2 = (X_1 \oplus C_2) \otimes H = (H \oplus 1) \otimes H = H^2 \oplus H$

其中 $H^2$ 是 $H$ 的平方，即 $H \otimes H$。

现在，你将 $X_2$ 替换为其推导结果来求 $X_3$，得到：

$X_3 = (X_2 \oplus C_3) \otimes H = (H^2 \oplus H \oplus 1) \otimes H = H^3 \oplus H^2 \oplus H$

接着，你求出 $X_4$ 为 $X_4 = H^4 \oplus H^3 \oplus H^2 \oplus H$，依此类推，最终得到最后一个 $X_i$：

$X_n = H^n \oplus H^{n-1} \oplus H^{n-2} \oplus \ldots \oplus H^2 \oplus H$

记住，你将所有块 $C_i$ 都设为 1。如果这些值是任意的，你将得到：

$X_n = (C_1 \otimes H^n) \oplus (C_2 \otimes H^{n-1}) \oplus (C_3 \otimes H^{n-2}) \oplus \ldots \oplus (C_{n-1} \otimes H^2) \oplus (C_n \otimes H)$

然后，GHASH 将消息长度与此最后一个 $X_n$ 进行异或，将结果乘以 $H$，再将该值与 **AES**$(K, N \mathbin{||} 0)$ 异或，以生成最终的认证标签 $T$。

### 哪里会出错

从这里开始，什么会出错呢？我们先来看最简单的情况：

- 如果 $H = 0$，那么无论 $C_i$ 的值如何，$X_n = 0$，因此无论消息是什么，$X_n$ 都是 0。也就是说，如果 $H$ 为 0，所有消息将具有相同的认证标签。
- 如果 $H = 1$，那么标签只是密文块的异或结果，重新排列密文块将得到相同的认证标签。

由于 0 和 1 只是 $H$ 的 $2^{128}$ 个可能值中的两个，因此发生这些情况的概率仅为 $2/2^{128} = 1/2^{127}$。但还有其他弱值——即所有在 $i$ 次幂时属于*短循环*的 $H$ 值。例如，$H$ 的值 $100d42f95356e69f58c2ef8d03a54$ 属于一个长度为 5 的循环，因为它满足 $H^5 = H$，因此对于任何为 5 的倍数的 $e$，都有 $H^e = H$（这正是关于五次幂的循环的定义）。因此，在上面对最终 GHASH 值 $X_n$ 的表达式中，交换块 $C_n$（与 $H$ 相乘）和块 $C_{n-4}$（与 $H^3$ 相乘）会使认证标签保持不变，这就相当于一次伪造。攻击者可以利用这一性质，在不知道密钥的情况下构造一条新消息及其有效标签，而对于安全的认证加密算法来说，这应该是不可能的。

前面的例子基于长度为 5 的循环，但还有更多更长的循环，因此许多 $H$ 值都比应有状态更弱。最终结果是，在 H 属于短循环这种不太可能的情况下，攻击者可以随心所欲地伪造任意数量的认证标签，但除非他们知道 H 或 K，否则无法确定 H 的循环长度。虽然攻击者无法利用这一漏洞，但你可以通过仔细选择用于模约简的多项式来避免它。

> 有关此攻击的更多详细信息，请阅读 Markku-Juhani O. Saarinen 所著的《Cycling Attacks on GCM, GHASH and Other Polynomial MACs and Hashes》，可在 https://eprint.iacr.org/2011/202 获取。

### AES-GCM 与短标签

在实践中，AES-GCM 通常返回 128 位标签，但它可以生成任意长度的标签。不幸的是，使用较短的标签时，伪造成功的概率会显著增加。

使用 128 位标签时，尝试伪造的攻击者应以 1/2^128 的概率成功，因为有 2^128 种可能的 128 位标签。（一般来说，对于 n 位标签，成功的概率应为 1/2^n，其中 2^n 是 n 位标签可能取值的数量。）但使用较短标签时，由于 GCM 结构中的弱点（这超出了本文的讨论范围），伪造成功的概率远高于 1/2^n。例如，对于某个 2MB 消息，32 位标签使知道其认证标签的攻击者有 1/2^16 的成功机会，而不是 1/2^32。

一般来说，对于 n 位标签，伪造成功的概率不是 1/2^n，而是 2^m/2^n，其中 2^m 是攻击者观察到标签的最长消息的块数。例如，如果你使用 48 位标签并处理 4GB（即 2^28 个 16 字节块）的消息，伪造成功的概率为 2^28/2^48 = 1/2^20，大约是百万分之一。就密码学而言，这是一个相对较高的概率。（有关此攻击的更多信息，请参阅 Niels Ferguson 于 2005 年发表的论文《Authentication Weaknesses in GCM》。）

## 延伸阅读

要了解更多关于认证加密算法的信息，请访问 CAESAR（认证加密竞赛：安全性、适用性和健壮性）的主页 (http://competitions.cr.yp.to/caesar.html)。CAESAR 始于 2012 年，是一场仿效 AES 和 SHA-3 竞赛风格的密码学竞赛，尽管它不是由 NIST 组织的。



CAESAR 竞赛吸引了大量创新设计：从类似 OCB 的模式到基于置换的模式（如 NORX 和 Keyak），以及完全原创的算法（如 AEZ 或 AEGIS）。2019 年，CAESAR 以挑选出分为三个类别的七个算法组合而告终，你可以在其官方页面 https://competitions.crypt.to/caesar-submissions.html 上找到它们。

另一个可以找到认证加密算法的竞赛是 NIST 的轻量级密码学项目。该项目从 2017 年运行到 2023 年，旨在标准化针对资源受限环境（如嵌入式平台）优化的算法，例如内存、处理器大小等。竞赛的获胜者是 Ascon，一个基于置换的算法家族，其官方网站 https://ascon.iaik.tugraz.at 上有详细介绍。要了解其他候选算法以及项目研讨会上展示的工作，请访问 https://csrc.nist.gov/Projects/lightweight-cryptography。

本章我们重点关注了 GCM，但现实应用中也使用了少数其他模式。具体来说，带 CBC-MAC 的计数器（CCM）和 EAX 模式在 2000 年代初期与 GCM 竞争标准化，虽然 GCM 被选中，但其竞争对手在一些应用中仍在使用。例如，CCM 用于 WPA2 Wi-Fi 加密协议。建议阅读这些密码的规范并评估其相对的安全性和性能优势。

这结束了我们对对称密钥密码学的讨论！你已经见过分组密码、流密码、（带密钥的）哈希函数，现在是认证密码——所有使用对称密钥或根本不使用密钥的主要密码学组件。在转向非对称密码学之前，第 9 章聚焦于计算机科学和数学，以为 RSA（第 10 章）和 Diffie–Hellman（第 11 章）等非对称方案提供背景知识。

## 第三部分
### 非对称密码

### 9
### 困难问题

![](img/ace4de942d037de8ea5835bc9fbe57cd_204_0.png)

困难的计算问题是现代密码学的基石。这些是即使最好的算法也无法在太阳烧毁之前找到解决方案的问题。

在 1970 年代，对困难问题的严格研究催生了名为 *计算复杂性理论* 的新科学领域，它极大地影响了密码学以及经济学、物理学和生物学等众多其他领域。在本章中，你将学习来自复杂性理论的概念工具，以理解密码学安全的基石。我还将介绍公钥方案背后的困难问题，例如 RSA 加密和 Diffie–Hellman 密钥协商。我会触及一些深奥的概念，但会尽量减少技术细节，仅触及表面。尽管如此，我希望你能看到密码学如何利用计算复杂性理论来最大化安全保证的美妙之处。

## 计算硬度

计算问题是一个可以通过足够计算来回答的问题——例如，“217 是质数吗？”或“How many *i*s are in incomprehensibilities？”第一个问题是判定问题，因为可以用“是”或“否”来回答，而第二个是搜索问题。

*计算硬度* 是指计算问题的一种属性，即不存在能在合理时间内运行的算法。这类问题也称为 *不可处理*。计算硬度与所使用的计算设备类型无关，无论是通用中央处理器（CPU）、图形处理器（GPU）、集成电路还是机械图灵机。事实上，计算复杂性理论的第一个发现之一就是所有计算模型都是等价的。如果一种计算设备能高效解决一个问题，任何其他设备都可以通过将算法移植到该设备的语言上来高效解决它——量子计算机是一个例外，我们将在第 14 章讨论。因此，在讨论计算硬度时，我无需指定底层计算设备或硬件；我们只需讨论算法。

为了评估计算硬度，你首先需要一种衡量算法复杂性或运行时间的方法。然后将运行时间归类为困难或容易。

### 运行时间

算法的 *计算复杂性* 是其作为输入规模函数的近似操作次数。你可以用位数或作为输入的元素数量来计算规模。例如，取列表 9-1 中的算法，用伪代码编写。它在包含 n 个元素的数组中搜索值 x，然后返回其索引位置，如果未找到 x 则返回 −1。

```
search(x, array, n) {
    for i from 0 to n - 1 {
        if (array[i] == x) {
            return i;
        }
    }
    return -1;
}
```

列表 9-1：相对于数组长度 n 具有线性复杂度的简单搜索算法

该算法使用 for 循环在数组中查找特定值 x，从 0 开始遍历变量 i 的值。它检查数组中位置 i 的值是否等于 x 的值。如果相等，则返回位置 i。否则，它递增 i 并尝试下一个位置，直到达到 n − 1，即数组的最后一个位置，此时返回 −1。

对于这类算法，你将复杂性计为 for 循环的迭代次数：最好情况下为 1（如果 x 等于 array[0]），最坏情况下为 n（如果 x 等于 array[n - 1] 或 x 未在数组中找到），如果 x 在数组的 n 个单元中均匀随机分布，则平均为 n/2。随着数组增大 10 倍，算法会慢 10 倍。因此复杂性与 n 成正比，或在 n 上为“线性”。相对于输入规模的线性复杂性被认为很快，与指数复杂性相对。在此示例中，尽管处理更大的输入值会更慢，但计算成本不会指数级爆炸，而是与表大小成正比。

然而，许多有用的算法比这更慢，其复杂性高于线性。教科书上的例子是排序算法：给定 n 个值按随机顺序排列的列表，在最坏情况下需要 n × log n 次基本操作来排序列表，这有时被称为线性对数复杂性。由于 n × log n 比 n 增长更快，排序速度会比与 n 成比例更快地变慢。然而，这样的排序算法仍处于实际计算的范畴，即可以在合理时间内完成计算。

通常不合理的是输入规模上的指数复杂性。在某个点上，即使对于相对较小的输入长度，你也会达到可行性的上限。取密码分析中最简单的例子：对秘密密钥的暴力搜索。回顾第 1 章，给定明文 P 和密文 C = E(K, P)，恢复 n 位对称密钥最多需要 2^n 次尝试，因为存在 2^n 个可能的密钥——这是一个呈指数增长的复杂性示例。具有指数复杂性的问题实际上不可能解决，因为随着 n 的增长，努力迅速变得不可行。

你可能会反对说我们在这里在比较橘子和苹果：在列表 9-1 中的 search() 函数中，我们计算了 if (array[i] == x) 操作的数量，而密钥恢复计算的是加密次数，每次加密比单个 == 比较慢数千倍。这种表面上的不一致如果比较两个复杂性非常相似的算法可能会产生差异，但大多数时候无关紧要，因为操作次数的影响大于单个操作成本。此外，复杂性估计忽略常数因子：当我们说一个算法花费 n^3 次操作的时间（即立方复杂性）时，它实际上可能花费 41 × n^3 次操作，甚至 12,345 × n^3 次操作——但同样，随着 n 的增长，常数因子变得无关紧要到可以忽略的地步。复杂性分析关注的是作为输入规模函数的理论难度；它不关心在你的计算机上花费的确切 CPU 周期数。

你经常可以使用 O() 记号（大 O）来表达复杂性。例如，O(n^3) 表示复杂性增长不超过 n^3，忽略潜在的常数因子。O() 表示算法复杂性的上界。记号 O(1) 表示算法以恒定时间运行——即运行时间不依赖于输入长度。例如，通过查看整数的最低有效位（LSB）来确定其奇偶性的算法，如果该位为零则返回“偶数”，如果为“奇数”

否则，无论整数的长度如何，都会以相同的代价做同样的事情。

要了解线性、二次和指数时间复杂度之间的差异，请观察图 9-1 中 $O(n)$（线性）、$O(n^2)$（二次）和 $O(2^n)$（指数）的复杂度增长情况。

![](img/ace4de942d037de8ea5835bc9fbe57cd_207_0.png)

*图 9-1：指数、二次和线性复杂度的增长，增长速度从最快到最慢*

指数复杂度意味着问题实际上不可能求解，线性复杂度意味着求解可行，而二次复杂度介于两者之间。

## 多项式时间与超多项式时间

二次复杂度 $O(n^2)$（图 9-1 中的中间曲线）是更广泛的多项式复杂度类——即 $O(n^k)$——的一个特例，其中 $k$ 是某个固定数，如 3、2.373、7/10 或 17 的平方根。多项式时间算法在复杂性理论和密码学中极其重要，因为它们是“实际可行”的定义本身。当一个算法以*多项式时间*运行时（简称 *polytime*），即使输入很大，它也能在合理的时间内完成。这就是为什么对于复杂性理论家和密码学家来说，多项式时间等同于“高效”。

相比之下，你可以把以*超多项式时间*运行的算法——即复杂度为 $O(f(n))$，其中 $f(n)$ 是任何比任何多项式增长都快的函数——视为不切实际。我之所以说超多项式而非仅仅指数，是因为在多项式与众所周知的指数复杂度 O(2^n) 之间存在一些中间复杂度，例如 O(n^{log(n)})，如图 9-2 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_208_0.png)

图 9-2：2^n、n^{log[n]} 和 n^2 函数的增长，增长速度从最快到最慢

O(n^2) 或 O(n^3) 可能是高效的，但 O(n^{99,999,999,999}) 显然不是。换句话说，只要指数不是太大，多项式时间在实践中就是快速的。幸运的是，所有用于解决实际问题的多项式时间算法都有较小的指数。例如，O(n^{2.373}) 是理论上两个 n × n 矩阵相乘的最佳已知算法的时间复杂度，只不过这个算法在实践中从未被使用。2002 年，用于识别 n 位素数的突破性多项式时间确定性算法最初复杂度为 O(n^12)，但后来改进到 O(n^6)。因此，多项式时间可能并不是算法实用时间的完美定义，但它是我们现有的最好定义。

推而广之，你可以把无法用多项式时间算法求解的问题视为不切实际或困难的。例如，对于直接的密钥搜索，除非密码本身被破解，否则没有办法超越 O(2^n) 的复杂度。

注意：指数复杂度 O(2^n) 并不是你能遇到的最坏情况。有些复杂度增长得更快，因而对应计算起来更慢的算法——例如 O(n^n) 或指数阶乘 O(n^{f(n-1)})，其中对于任何 x，函数 f 在这里递归定义为 f(x) = x^{f(x-1)}。在实践中，你永远不会遇到具有如此荒谬复杂度的算法。

你知道，暴力密钥搜索的 $O(2^n)$ 复杂度是无法超越的（只要密码是安全的），但你并不总是知道解决某个计算问题的一般最快方法。复杂性理论中有很大一部分研究是关于证明解决给定问题的算法运行时间的复杂度*界*。为了使工作更容易，复杂性理论家根据解决问题的所需工作量，将计算问题划分为不同的组，即*类*。

## 复杂性类

在数学中，*类*是具有某种相似属性的一组对象。例如，所有在 $O(n^2)$ 时间内可解的计算问题构成一个类，复杂性理论家将其简记为 **TIME**($n^2$)。同样，**TIME**($n^3$) 是在 $O(n^3)$ 时间内可解的问题类，**TIME**($2^n$) 是在 $O(2^n)$ 时间内可解的问题类，以此类推。正如超级计算机能计算笔记本电脑能计算的任何东西一样，任何在 $O(n^2)$ 时间内可解的问题也必然在 $O(n^3)$ 时间内可解。因此，**TIME**($n^2$) 类中的任何问题也属于 **TIME**($n^3$) 类，而这两者又都属于 **TIME**($n^4$) 类，依此类推。所有常数 $k$ 对应的 **TIME**($n^k$) 类的并集就是 **P**，它代表多项式时间。

如果你给计算机编过程序，你就会知道，看似快速的算法仍然可能耗尽系统的所有内存资源而导致崩溃。在选择算法时，你不仅应该考虑其时间复杂度，还应该考虑它使用多少内存，即其*空间复杂度*。这一点尤其重要，因为一次内存访问通常比 CPU 中的一次基本算术运算慢几个数量级。

正式地，你可以像定义时间复杂度那样，将算法的内存消耗定义为输入长度 $n$ 的函数。使用 $f(n)$ 位内存即可求解的问题类称为 **SPACE**($f(n)$)。例如，**SPACE**($n^3$) 是使用大约 $n^3$ 位内存即可求解的问题类。正如 **P** 是所有 **TIME**($n^k$) 的并集，所有 **SPACE**($n^k$) 问题的并集就是 **PSPACE**。

虽然内存越低越好，但多项式级内存并不一定意味着算法是可实际应用的。例如，暴力密钥搜索占用内存可忽略不计，但慢得要命。更一般地，一个算法即使只使用几个字节的内存，也可能永远运行不完。

任何在 $f(n)$ 时间内可解的问题最多需要 $f(n)$ 内存，因此 **TIME**($f(n)$) 包含于 **SPACE**($f(n)$)。在 $f(n)$ 时间内，你最多只能写入 $f(n)$ 位，不能再多，因为写入（或读取）1 位被视为耗时一个时间单位；因此，**TIME**($f(n)$) 中的任何问题都不可能使用超过 $f(n)$ 的空间。因此，**P** 是 **PSPACE** 的子集。

## 非确定性多项式时间

**NP**，即*非确定性多项式时间*，是第二重要的复杂性类，仅次于由所有多项式时间算法组成的类 **P**。

**NP** 是一类判定问题，对于这类问题，你可以在多项式时间内——也就是说高效地——验证一个解，即使这个解可能很难找到。我所说的*验证*是指，给定一个潜在解，你可以运行某个多项式时间算法来检查你是否真的找到了一个解。例如，对于对称密码系统 **E**，给定 P 和 C，判定是否存在密钥 K 使得 C = **E**(K, P) 的问题属于 **NP**。这是因为给定候选密钥 K₀，你可以通过验证 **E**(K₀, P) 是否等于 C 来检查 K₀ 是否是正确密钥。你无法在多项式时间内找到潜在密钥（解）——如果它存在的话——但你可以检查某个密钥是否正确。

现在看一个反例：已知密文攻击呢？这一次，你只得到一些随机未知明文 Pₛ 的 **E**(K, P) 值。如果你不知道 Pₛ 是什么，那就无法验证潜在密钥 K₀ 是否正确。换句话说，已知密文攻击下的密钥恢复问题不在 **NP** 中（更不用说在 **P** 中了），因为你不能将其表述为判定问题。

另一个不在 **NP** 中的问题示例是验证问题*没有*解。验证一个解是否正确，归结为以候选解作为输入计算某个算法，然后检查返回值。然而，要验证*不存在*解，你可能需要遍历所有可能的输入。如果输入数量是指数级的，你将无法高效地证明解不存在。对于 **NP** 类中最难的问题（即所谓的 **NP**-完全问题），证明解不存在是很困难的。

### NP-完全问题

**NP**-完全问题是 **NP** 类中最难的判定问题；对于这些问题的最坏情况实例，你不知道如何用多项式时间求解。正如复杂性理论家在 20 世纪 70 年代发展 **NP** 完全性理论时所发现的，**NP** 中最难的问题在根本上都是同等困难的。这一结论的证明思路是：任何 **NP**-完全问题的高效解法，都可以转化为其他任何 **NP**-完全问题的高效解法。换句话说，如果你能高效地解决任何一个 **NP**-完全问题，你就能解决所有 **NP**-完全问题，以及 **NP** 中的所有问题。这怎么可能呢？

**NP**-完全问题表面上形形色色，但从数学角度看，它们本质上是相似的。事实上，你可以将任何 **NP**-完全问题归约到任何其他 **NP**-完全问题，使得解决后者的能力意味着解决前者的能力。请记住，**NP** 包含的是判定问题，而不是搜索问题。你可以将一个能解决搜索问题的算法高效地转化为一个能解决相应判定问题的算法，尽管反过来并不总是可行的。幸运的是，**NP**-完全问题正是这种情况，这也就解释了为什么人们经常把两者混为一谈。




以下是**NP**完全问题的一些示例：

### 旅行商问题

给定地图上的一组点（例如城市），以及每两个点之间的距离，并给定最大距离 x，判断是否存在一条路径能够访问每个点，使得总距离小于 x。（注意，你可以用与判定问题基本相同的复杂度找到这样一条路径，但判断一条路径是否最优并不属于**NP**，因为你无法高效地验证解的正确性。）

### 团问题

给定一个数字 x 和一个图（一组由边连接的节点，如图 9-3 所示），判断是否存在一个至多包含 x 个节点且所有节点两两相连的节点集合。

![](img/ace4de942d037de8ea5835bc9fbe57cd_211_0.png)

图 9-3：一个包含四个节点的团的图。在图中寻找给定大小的团（所有节点两两相连的节点集合）的一般问题是**NP**完全的。

### 背包问题

给定两个数字 x 和 y，以及一组物品，每个物品都有已知的价值和重量，判断是否存在一组物品，使得总价值至少为 x，总重量至多为 y。

你随处可见这类**NP**完全问题，从调度（给定一些具有优先级和持续时间的作业以及一个或多个处理器，在尊重优先级的同时最小化总执行时间，将作业分配给处理器）到约束满足（确定满足一组数学约束（如逻辑方程）的取值）。甚至在某些电子游戏中获胜的任务也被证明是**NP**困难的（包括俄罗斯方块、超级马力欧兄弟、宝可梦和糖果传奇等知名游戏）。例如，文章《经典任天堂游戏（计算上）是困难的》考虑了“可达性判定问题”，以确定从特定起始点到达目标点的可能性（https://arxiv.org/abs/1203.1895）。

这些电子游戏问题中的一些至少与NP完全问题一样难，被称为NP困难问题。一个（不一定是判定性的）问题是NP困难的，当它至少与NP完全（判定）问题一样难，并且任何解决它的方法都可以高效地用于解决NP完全问题。

NP完全问题必须是判定性问题；也就是说，答案是是或否的问题。因此，严格来说，计算解的最优值的问题不能是NP完全的，但可能是NP困难的。例如，以旅行商问题为例：“是否存在一条访问所有点且距离小于X的路径？”是NP完全的，而“找到访问所有点的最快路径”是NP困难的。

请注意，并非所有NP困难问题的实例都真的难以解决。你或许能够高效地解决某些实例，因为它们规模较小或具有特定的结构。例如，以图9-3为例。你可以很快发现团，即顶部四个相连的节点——尽管前述的寻找团的问题是NP困难的，但这里并没有什么困难之处。NP困难并不意味着给定问题的所有实例都困难，而是随着问题规模的增大，其中一些实例会变困难。这就是密码学家更关注平均情况下困难问题，而不仅仅是最坏情况的原因。

## P与NP问题

如果你能在多项式时间内解决最难的NP问题，那么你就能在多项式时间内解决所有NP问题，因此NP将等于P。这样的等式听起来很荒谬：难道没有问题存在解易于验证但难以寻找吗？例如，难道指数时间的暴力破解不是恢复对称密码密钥的最快方式，因此该问题不可能属于P吗？

尽管听起来很疯狂，但没有人证明P与NP不同，尽管悬赏高达100万美元。克莱数学研究所将向任何证明P ≠ NP或P = NP的人颁发这一奖项。这个问题被称为P与NP问题，被著名复杂性理论家斯科特·阿伦森称为“人类曾提出的最深奥的问题之一”。想一想：如果P等于NP，那么任何容易验证的解也会容易找到。实践中使用的所有密码学都将变得不安全，因为你可以高效地恢复对称密钥并反转哈希函数。

但不要惊慌：大多数复杂性理论家相信P不等于NP，因此P是NP的严格子集，如图9-4所示，其中NP完全问题是NP的另一个与P不重叠的子集。换句话说，看起来困难的问题实际上是困难的。只是很难从数学上证明这一点。虽然证明P = NP只需要一个NP完全问题的多项式时间算法，但证明这种算法不存在从根本上更难。这并没有阻止数学家提出一些简单的证明，虽然这些证明通常明显是错误的，但往往读起来很有趣；例如，参见“P与NP页面”（https://www.win.tue.nl/~wscor/woeginger/P-versus-NP.htm）。

![](img/ace4de942d037de8ea5835bc9fbe57cd_213_0.png)

如果我们几乎确信困难问题存在于**NP**中，那么利用它们来构建强大、可证明安全的密码学呢？想象一下，证明破解某个密码是**NP**困难的，因此只要**P**不等于**NP**，该密码就无法被破解。但现实令人失望：**NP**完全问题的搜索版本已被证明难以用于密码学目的，因为使它们在最坏情况下困难的结构，在密码学中有时出现的特定情况下可能使它们变得容易。相反，密码学常常依赖于*可能并非***NP**困难的问题。

## 因式分解问题

因式分解问题是指在给定一个大数 *N* = *p* × *q* 的情况下，找出素数 *p* 和 *q*。广泛使用的RSA算法基于因式分解的困难性：RSA加密和签名方案之所以安全，是因为因式分解是一个困难问题。在我们于第10章看到RSA如何利用因式分解问题之前，我想让你相信这个问题的判定版本（“*N*是否存在一个小于 *k* 且不等于1的因子？”）确实困难，但可能不是**NP**完全的。

首先，一些基础数学。*素数*是除了它本身和1之外不能被任何其他数整除的数。例如，3、7和11是素数；4（即2 × 2）、6（2 × 3）和12（2 × 2 × 3）不是。数论的一个基本定理表明，任何整数都可以唯一地写成素数的乘积，这种表示称为该数的*因式分解*。例如，123,456的因式分解是2⁶ × 3 × 643，1,234,567的因式分解是127 × 9,721，以此类推。任何整数都有唯一的因式分解，即唯一地写成素数乘积的方式。多项式时间的素性检验算法使我们能够高效地测试给定数是否为素数，或给定的因式分解是否仅包含素数。然而，从一个数得到它的素数因子则是另一回事。

### 因式分解大数

那么，如何从一个数得到它的因式分解——即它作为素数乘积的分解呢？对一个数 *N* 进行因式分解最基本的方法是尝试用它除以所有小于它的数，直到找到一个能整除 *N* 的数 *x*。然后用下一个数 *x* + 1 尝试整除 *N*，依此类推。最终你会得到 *N* 的因子列表。这的时间复杂度是多少？首先，请记住，我们将复杂度表示为输入*长度*的函数。数 *N* 的位长为 *n* = log₂ *N*。根据对数的定义，这意味着 *N* = 2ⁿ。由于所有小于 *N*/2 的数都是 *N* 可能的因子的合理猜测，因此大约有 *N*/2 = 2ⁿ/2 个值需要尝试。因此，我们朴素因式分解算法的复杂度为 O(2ⁿ)，忽略 O() 表示法中的 1/2 系数。

虽然许多数字可以先找到任何小因子（2、3、5等），然后迭代分解任何其他非素数因子来轻松分解，但我们在密码学中关注的是形如 *N* = *p* × *q* 的数，其中 *p* 和 *q* 都很大。

让我们稍微聪明一点：因为我们不需要测试所有小于 *N*/2 的数，而只需要测试素数，所以我们可以从尝试那些小于 *N* 平方根的数开始。如果 *N* 不是素数，那么它至少有一个因子小于其平方根 √*N*。这是因为如果 *N* 的两个因子 *p* 和 *q* 都大于 √*N*，那么它们的乘积将大于 √*N* × √*N* = *N*，这是不可能的。例如，如果 *N* = 100，它的因子 *p* 和 *q* 不可能都大于10，因为这会导致乘积大于100。*p* 或 *q* 中至少有一个必须小于或等于 √*N*。

那么，只测试小于 √*N* 的素数的复杂度是多少？*素数定理*指出，小于 *N* 的素数大约有 *N*/log *N* 个。因此，小于 √*N* 的素数大约有 √*N*/log √*N* 个。用 *n* = log₂ *N* 表示这个值，我们得到大约 2ⁿᐟ²⁺¹/*n* 个可能的素数因子，因此复杂度为 O(2ⁿᐟ²/*n*)，因为 √*N* = 2ⁿᐟ² 且 1/log √*N* = 1/(*n*/2) = 2/*n*。这比测试所有素数要快，但仍然慢得令人痛苦——对于一个256位数来说，大约需要2¹²⁰次运算。这是一个相当不切实际的计算工作。但我们可以做得更好。

最快的因式分解算法是*普通数域筛选法（GNFS）*，我在此不做描述，因为它需要引入几个高级数学概念。GNFS复杂度的粗略估计为 exp(1.91 × *n*¹ᐟ³ (log *n*)²ᐟ³)，其中 *n* = log₂ *N* 是 *N* 的位长，exp(.) 只是指数函数 *e*ˣ 的另一种表示法，*e* 是约等于2.718的指数常数。然而，对于给定的数字大小，很难准确估计GNFS的实际复杂度。因此，我们必须依赖启发式复杂度估计，它们显示了安全性如何随着 *n* 变长而增加。例如：

-   对一个**1,024位**的数（其两个素数因子各约500位）进行因式分解，大约需要2⁷⁰次基本运算。
-   对一个**2,048位**的数（其两个素数因子各约1,000位）进行因式分解，大约需要2⁹⁰次基本运算——比1,024位的数慢约一百万倍。



你可以估算出，达到 128 位安全强度至少需要 4,096 位的密钥。不过，这些数值不应全信，因为研究人员并不总是对这些估计达成一致。以下实验结果揭示了因式分解的实际代价：

- 2005 年，经过大约 18 个月的计算——借助 80 个处理器组成的集群，总计算量相当于单处理器 75 年的计算量——一组研究人员分解了一个 **663 位**（200 位十进制数）的数。
- 2009 年，在使用了数百个处理器、历时约两年之后，总计算量相当于单处理器约 2,000 年的计算量，另一组研究人员分解了一个 **768 位**（232 位十进制数）的数。
- 2020 年，经过几个月的计算，动用了数万个处理器和一台超级计算机，总计算量相当于单处理器约 2,700 年的计算量，另一个团队分解了一个 **829 位**（250 位十进制数）的数。

如你所见，研究人员所分解的数的位数比实际应用中的数要短；实际应用中的数至少为 1,024 位，且通常超过 2,048 位。在我写这段话时，还没有人报告过对 1,024 位数的因式分解，但许多人推测，像美国国家安全局（NSA）这样资金雄厚的机构有能力做到。

总之，你应当将 1,024 位的 RSA 视为不安全的，并使用至少 2,048 位的 RSA，但为了确保更高的安全性，最好使用 4,096 位。

## 因式分解很可能不是 NP 困难问题

我们不知道如何高效地分解大数，这暗示因式分解问题不属于 **P**。然而，因式分解的判定版本显然属于 **NP**，因为给定一个因式分解，我们可以通过检查所有因子都是质数（借助前面提到的素性测试算法）以及将因子相乘得到预期的数，来验证这个解。例如，要检查 3 × 5 是 15 的因式分解，只需确认 3 和 5 都是质数，且 3 乘以 5 等于 15。

因此，我们有一个属于 **NP** 并且看起来很困难的问题，但它是否和最难的那些 NP 问题一样难呢？换句话说，因式分解的判定版本是 **NP 完全** 的吗，因此因式分解是 **NP 困难** 的吗？剧透警告：很可能不是。

目前还没有数学证明表明因式分解不是 **NP 困难** 的，但我们有一些间接证据。首先，所有已知的属于 **NP** 的 **NP 困难** 问题，可能有一个解、多个解，也可能根本没有解。相比之下，因式分解总是恰好有一个解。此外，因式分解问题具有一种数学结构，使得 GNFS 算法能够显著优于朴素算法，而这种结构是 **NP 困难** 问题所不具备的。借助 *量子计算机*，因式分解会变得简单；量子计算机是一种利用量子力学现象来运行不同类型算法的计算模型，它有能力高效地分解大数（不是因为它运行算法更快，而是因为它可以运行专门用于分解大数的量子算法）。不过，这样的量子计算机目前还不存在——而且可能永远不会出现。无论如何，人们认为量子计算机在解决 **NP 困难** 问题上毫无用处，因为它并不比经典计算机更快（见第 14 章）。

理论上，因式分解可能比解决 **NP 困难** 问题略微容易一些，但就密码学而言，它已经足够困难，甚至比 **NP 困难** 问题更可靠。事实上，在因式分解问题上构建密码系统，比在 **NP 完全** 问题的搜索版本上构建更容易，因为我们很难确切知道破解基于这类问题的密码系统有多难——换句话说，你能获得多少位安全性。如前所述，这与 **NP** 关注最坏情况下的难度，而密码学家寻求的是平均情况下的难度有关。

因式分解问题是可以作为 *困难性假设* 用于密码学的几个问题之一；所谓困难性假设，就是假定某个问题在计算上是困难的。当你证明破解某个密码系统的安全性至少与解决上述问题一样困难时，可以使用这一假设。另一个可以用作困难性假设的问题——*离散对数问题（DLP）*——实际上是一族问题。

## 离散对数问题

在密码学的官方历史中，离散对数问题（DLP）的出现早于因式分解问题。RSA 于 1977 年问世，而另一项密码学突破——迪菲-赫尔曼密钥协商（见第 11 章）——大约早一年出现，其安全性建立在 DLP 的难度之上。与因式分解问题一样，DLP 也涉及大数，但它不像因式分解那样直观，并且需要更多的数学知识。让我们首先在离散对数的语境下介绍群这一数学概念。

### 群

在数学语境中，*群* 是一组元素（通常是数字），这些元素按照某些明确定义的规则相互关联。群的一个例子是模质数 *p* 的非零整数集合（即 1 到 *p*−1 之间的整数），其群运算为模乘法。我们将这样的群记为 \(\mathbb{Z}_p^*\)，或者当群运算显然是乘法时，直接记为 \(\mathbb{Z}_p^*\)。

例如，当 *p* = 5 时，得到群 \(\mathbb{Z}_5^* = \{1, 2, 3, 4\}\)。在群 \(\mathbb{Z}_5^*\) 中，运算都在模 5 下进行；因此，不是 3 × 4 = 12，而是 3 × 4 = 2，因为 12 mod 5 = 2。你仍然可以使用与普通整数乘法相同的符号（×）。你还可以使用指数记法来表示群元素对自身进行模 *p* 的乘法，这是密码学中常见的运算。例如，在 \(\mathbb{Z}_5^*\) 的语境下，\(2^3 = 2 × 2 × 2 = 3\) 而不是 8，因为 8 mod 5 等于 3。

要成为一个群，一个数学集合及其运算必须满足以下特征，这些特征称为 *群公理*：

**封闭性**：对于任意两个群元素 *x* 和 *y*，*x* × *y* 也属于该群。在 **Z**₅* 中，2 × 3 = 1（因为 6 = 1 mod 5），2 × 4 = 3，等等。

**结合律**：对于任意群元素 *x*、*y*、*z*，(*x* × *y*) × *z* = *x* × (*y* × *z*)。在 **Z**₅* 中，(2 × 3) × 4 = 1 × 4 = 2 × (3 × 4) = 2 × 2 = 4。

**单位元存在性**：群中存在一个元素 *e*，使得 *e* × *x* = *x* × *e* = *x*。这样的元素称为 *单位元*。在任何 **Z**ₚ* 中，单位元都是 1。

**逆元存在性**：对于群中的任意 *x*，都存在一个 *y*，使得 *x* × *y* = *y* × *x* = *e*。在 **Z**₅* 中，2 的逆元是 3，3 的逆元是 2，而 4 的逆元是它自身，因为 4 × 4 = 16 = 1 mod 5。

此外，如果一个群对任意群元素 *x* 和 *y* 都满足 *x* × *y* = *y* × *x*，则该群是 *可交换的*，或称 *阿贝尔的*。这一性质对任何整数乘法群 **Z**ₚ* 也都成立。特别地，**Z**₅* 是可交换的：3 × 4 = 4 × 3，2 × 3 = 3 × 2，等等。

如果一个群中至少存在一个元素 *g*，使得 *g* 的幂（*g*¹、*g*²、*g*³，等等）模 *p* 遍历所有不同的群元素，那么这个群是 *循环群*。元素 *g* 就是该群的 *生成元*。**Z**₅* 是循环群，并且有两个生成元 2 和 3，因为 2¹ = 2，2² = 4，2³ = 3，2⁴ = 1，以及 3¹ = 3，3² = 4，3³ = 2，3⁴ = 1。

请注意，我使用乘法作为群运算，但你也可以从其他运算得到群。例如，最直接的群是所有正整数和负整数组成的集合，以加法作为群运算。让我们按照前述顺序检查加法是否满足群公理：如果 *x* 和 *y* 是整数，那么 *x* + *y* 也是整数（封闭性）；对于任意 *x*、*y*、*z*，(*x* + *y*) + *z* = *x* + (*y* + *z*)（结合律）；零是单位元；群中任意数 *x* 的逆元是 −*x*，因为对任意整数 *x*，*x* + (−*x*) = 0。不过，一个很大的区别是，这个整数群是无限大小的，而在密码学中，出于实现原因，你只会处理 *有限群*，即元素个数有限的群。通常，你会使用群 **Z**ₚ*，其中 *p* 有 *数千* 位长（也就是说，如果 *p* 有 *m* 位长，那么群中包含大约 2^m 个数）。

### 难点

最初用于密码学的离散对数问题是：给定某个群 **Z**ₚ* 中的一个生成元 *g*（其中 *p* 是质数）以及一个群元素 *x*，找出满足 *g*^y = *x* 的 *y*。我们通常用加法而不是乘法记号来表示 DLP，例如在椭圆曲线群中。在这种情况下，问题变为：在已知点 *P* 和 *Q* 的情况下，找到满足 *k* × *P* = *Q* 的乘法因子 *k*。这被称为 *椭圆曲线 DLP（ECDLP）*。

DLP 之所以是 *离散的*，是因为你处理的是可数整数，而不是不可数的实数；它之所以是一个 *对数* 问题，是因为你在寻找以 *g* 为底 *x* 的对数。例如，以 2 为底 256 的对数是 8，因为 2⁸ = 256。



分解与离散对数一样困难，因此也一样安全。事实上，求解 DLP 的算法与分解整数的算法相似，并且使用 n 位难以分解的数所获得的安全性水平与在 n 位群中的离散对数大致相同。与分解因数相同的原因，DLP 也不是 NP-hard。（某些群中 DLP 更容易求解，但这些群在密码学中并不使用，至少在需要 DLP 困难性的场景中不使用。）

## How Things Can Go Wrong

40 多年过去了，我们仍然不知道如何高效地分解大数或求解离散对数。在没有数学证明的情况下，总是可能推测它们总有一天会被攻破。但我们也没有 P ≠ NP 的证明，所以你可以推测 P 可能等于 NP；然而，根据专家的说法，这种意外不太可能。今天部署的大多数公钥密码要么依赖于分解（RSA），要么依赖于 DLP（Diffie–Hellman、ElGamal、椭圆曲线密码学）。虽然数学可能不会让我们失望，但现实世界的担忧和人为错误可能会趁虚而入。

## When Factoring Is Easy

分解大数并不总是困难。例如，取以下 1,024 位数 N：

```
1797693134862315907772930519078902473361797697894230657273430081157739343819933842986982557174198257278917258638193709265819186026626180659730665062710995556578639447715608415186895652841691982921107202317165369124890481512388558039053427125099290315449262324709315263256083132540461407052872832790915388014592
```

对于 RSA 加密或签名方案中 N = pq 的 1,024 位数，我们期望最好的分解算法需要大约 2^70 次运算，就像我们之前讨论的那样。但你可以使用 SageMath，一种基于 Python 的数学软件，在几秒钟内分解这个样本数。在我的 2023 年 MacBook 上使用 SageMath 的 factor() 函数，花费不到一秒就找到了以下分解：

```
2^800 × 641 × 6700417 × 167773885276849215533569 × 37414057161322375957408148834323969
```

没错，我作弊了。这个数并不是 N = pq 的形式，因为它不是只有两个大素因子，而是五个，包括非常小的因子，这使得它很容易分解。首先，你可以通过尝试预先计算的素数列表中的小素数来识别 2^800 × 641 × 6,700,417 部分，这会留下 192 位的数，比具有两个大因子的 1,024 位数容易分解得多。

分解不仅在 n 具有小素因子时容易，也在 N 或其因子 p 和 q 具有特定形式时容易——例如，当 N = pq 且 p 和 q 都接近某个 2^b 时，当 N = pq 且 p 或 q 的某些位已知时，或当 N 为 N = p^r q^r 形式且 r 大于 log p 时。然而，详细说明这些弱点的原因对于本书来说过于技术化。

因此，RSA 加密和签名算法（参见第 10 章）需要使用 N = pq 的值，其中 p 和 q 经过精心选择，以避免 N 容易被分解，这可能导致安全灾难。

## Small Hard Problems Aren’t Hard

计算上困难的问题，甚至指数时间算法，在足够小时变得实用。一种对称密码可能在安全性上是安全的，因为没有比 2^n 时间的暴力破解更快的攻击，但如果密钥长度为 n = 32，你会在几分钟内破解该密码。这听起来很明显，你会认为没有人会愚蠢到使用小密钥，但在现实中，出现这种情况的原因有很多。以下是两个真实的故事。

假设你是一名对密码学一无所知的开发者，但有一个用于 RSA 加密的 API，并且被告知要使用 128 位安全性。你会选择什么 RSA 密钥大小？我见过真实的 128 位 RSA 案例，或基于 128 位数 N = pq 的 RSA。然而，虽然对数千位长的 N 进行分解在实践中非常困难，但分解 128 位数是很容易的。使用 SageMath 软件，第 9-2 节中的命令会瞬间完成。

```
sage: p = random_prime(2**64)
sage: print(p)
6822485253121677229
sage: q = random_prime(2**64)
sage: print(q)
17596998848870549923
sage: N = p*q
sage: factor(N)
6822485253121677229 * 17596998848870549923
```

第 9-2 节：通过选取两个随机素数生成 RSA 模数并瞬间分解它

第 9-2 节显示，你可以在普通笔记本电脑上轻松分解一个随机作为两个 64 位素数乘积的 128 位数。然而，如果我改用 `p = random_prime(2**1024)` 选择 1,024 位素数，命令 `factor(p*q)` 将永远无法完成，至少在我有生之年是这样。

公平地说，现有工具并不能防止对不安全短参数的幼稚使用。例如，OpenSSL 工具包过去允许你在没有任何警告的情况下生成短至 31 位的 RSA 密钥；这种短密钥完全不安全，如第 9-3 节所示。OpenSSL 此后已得到修复，其 1.1.1t 版本（2023 年 2 月）如果请求短于 512 位的密钥，将返回错误“key size too small”。

```
$ openssl genrsa 31
Generating RSA private key, 31 bit long modulus
.+++++++++++++++++++++++++++++++++++++
.+++++++++++++++++++++++++++++++++++++
e is 65537 (0x10001)
-----BEGIN RSA PRIVATE KEY-----
MCsCAQACBHHqFuUCAwEAAQIEP6zEJQIDANATagMAjCcAwCSBwICTGsCAhpp
-----END RSA PRIVATE KEY-----
```

第 9-3 节：使用旧版 OpenSSL 工具包生成不安全的 RSA 私钥

在审查密码学时，你应该不仅检查所使用的算法类型，还应检查其参数和秘密值的长度。然而，正如你将在下面的故事中看到的那样，今天足够安全的东西明天可能就不安全了。

2015 年，研究人员发现许多 HTTPS 服务器和电子邮件服务器支持一种较旧、不安全的 Diffie–Hellman 密钥协商协议版本。也就是说，底层 TLS 实现支持在群 Z*_p 内的 Diffie–Hellman，该群由仅 512 位的素数 p 定义，在该群中离散对数问题不再在实践中不可能计算。

服务器不仅支持弱算法，而且攻击者还可以通过在客户端会话中注入恶意流量来强制良性客户端使用该算法。对攻击者来说更有利的是，攻击的最大部分可以一次性完成并重复用于攻击多个客户端。攻击特定群 Z*_p 大约需要一周的计算时间，然后只需 70 秒即可破坏不同用户的单个会话。

如果被削弱的算法破坏，安全协议就毫无价值；如果被弱参数破坏，可靠的算法也毫无用处。在密码学中，你应该始终阅读细则。

有关此故事的更多详细信息，请查阅研究文章“不完美的前向保密：Diffie–Hellman 在实践中如何失效”（https://weakdh.org/imperfect-forward-secrecy-ccs15.pdf）。

## Further Reading

我鼓励你深入研究计算在可计算性（什么函数可以被计算？）和复杂性（成本如何？）方面的基础方面，以及它们与密码学的关系。我主要谈到了 P 和 NP 类，但对密码学家来说还有许多其他类和感兴趣点。我强烈推荐 Scott Aaronson 的书籍《自德谟克利特以来量子计算》（剑桥大学出版社，2013 年）。它在很大程度上是关于量子计算的，但其前几章精彩地介绍了复杂性理论和密码学。

在密码学研究文献中，你会发现其他困难的计算问题。我将在后面的章节中提到它们，但这里有一些例子说明了密码学家利用的问题的多样性：

- Diffie–Hellman 问题（给定 g^x 和 g^y，求 g^{xy}）是离散对数问题的一个变体，在密钥协商协议中被广泛使用。
- 晶格问题，例如最短向量问题（SVP）以及短整数解（SIS）和学习误差（LWE）问题，根据其参数可以是 **NP**-hard。
- 编码问题依赖于在信息不足的情况下解码纠错码的困难性，自 20 世纪 70 年代末以来一直被研究。这些问题也可以是 **NP**-hard。
- 多元问题是关于求解非线性方程组的问题，可能为 **NP**-hard，但它们未能提供可靠的密码系统，因为困难版本太大且太慢，而实用的版本被发现不安全。

在第 10 章中，我们将继续探索困难问题，特别是分解及其主要变体 RSA 问题。




### 10 RSA

![](img/ace4de942d037de8ea5835bc9fbe57cd_222_0.png)

Rivest–Shamir–Adleman（RSA）密码系统在1977年作为第一个公钥加密方案出现时，彻底改变了密码学。经典的对称密钥加密方案使用同一个秘密密钥来加密和解密消息，而*公钥加密*（或*非对称加密*）使用两个密钥：公钥（任何想给你加密消息的人都可以使用）和私钥（解密使用公钥加密的消息所必需的）。这种神奇的特性正是RSA成为真正突破的原因，40年后，它仍然是公钥加密的典范，也是互联网安全的中坚力量。（在RSA之前一年，Whitfield Diffie和Martin Hellman提出了公钥密码学的概念，但他们的方案只能在公钥环境中执行密钥分发。）

RSA通过创建*陷门置换*来工作，这是一种将数字*x*转换为同一范围内的数字*y*的函数，使得使用公钥从*x*计算*y*很容易，但除非你知道私钥（即陷门），否则从*y*计算*x*实际上是不可能的。（可以把*x*看作明文，*y*看作密文。）

除了加密之外，你还可以使用RSA构建数字签名，其中只有私钥的拥有者才能签署消息，而公钥使任何人都能验证签名的有效性。

在本章中，你将学习RSA陷门置换的工作原理，以及为什么仅凭这种置换不足以构建*安全的*加密和签名。我还会讨论RSA相对于因式分解问题的安全性（参见第9章）、安全实现RSA的方法，以及如何攻击它。

我们首先解释RSA背后的基本数学概念。

### RSA背后的数学

在处理消息时，无论是加密还是签名，RSA首先从该消息创建一个大数，然后通过在大数之间执行乘法来处理它。因此，要理解RSA的工作原理，你需要知道它操作的是哪种大数，以及乘法在这些数上是如何工作的。

为了加密或签名，RSA变换1到*n* − 1之间的正整数，其中*n*是一个称为*模数*的大数。这些数相乘时会得到另一个满足这些条件的数。这些数构成一个群，记为\(Z_n^*\)，称为模*n*的整数乘法群。（参见第189页"群"中群的数学定义。）

例如，考虑模4的整数群\(Z_4^*\)。回顾第9章，一个群必须包含一个单位元（即1），并且群中的每个数*x*必须有一个逆元，即一个数*y*使得*x* × *y* = 1。如何确定构成\(Z_4^*\)的集合呢？根据定义，你知道0不在群\(Z_4^*\)中，因为任何数乘以0都不可能得到1，所以0没有逆元。数1属于\(Z_4^*\)，因为1 × 1 = 1，所以1是自身的逆元。然而，数2不属于这个群，因为你无法通过将2与\(Z_4^*\)中的另一个元素相乘得到1（注意2与4不互素，因为4和2共享因子2）。数3属于群\(Z_4^*\)，因为它在\(Z_4^*\)内是自身的逆元。因此，\(Z_4^* = \{1, 3\}\)。

现在考虑\(Z_5^*\)，即模5的整数乘法群。如第9章所述，\(Z_5^* = \{1, 2, 3, 4\}\)。事实上，由于5是素数，1、2、3和4都与5互素，所以\(Z_5^*\)的集合包含所有这些数。让我们验证一下：2 × 3 mod 5 = 1；因此，2是3的逆元，3是2的逆元；注意4是自身的逆元，因为4 × 4 mod 5 = 1；最后，1在这个群中同样是自身的逆元。

当*n*不是素数时，要找出群\(Z_n^*\)中元素的数量，你可以使用*欧拉函数*，我们将其写为φ(*n*)，其中φ代表希腊字母phi。这个函数给出与n互素的元素数量，也就是\(Z_n^*\)中的元素数量。一般来说，如果n是素数的乘积 n = p₁ × p₂ × … × pₘ，那么群\(Z_n^*\)中的元素数量如下：

φ(n) = (p₁ − 1) × (p₂ − 1) × … × (pₘ − 1)

RSA只处理两个大素数的乘积n，通常记为n = p q。相关的群\(Z_n^*\)包含φ(n) = (p − 1)(q − 1)个元素。展开这个表达式，你得到等价定义φ(n) = n − p − q + 1，或φ(n) = (n + 1) − (p + q)，这更直观地表达了φ(n)相对于n的值。

### RSA陷门置换

RSA陷门置换是基于RSA的加密和签名背后的核心算法。给定模数n和一个你称为公钥指数的数e，RSA陷门置换将集合\(Z_n^*\)中的数x转换为数y = x^e mod n。换句话说，它计算等于x自乘e − 1次后模n的值，然后返回结果。当你使用RSA陷门置换进行加密时，模数n和指数e构成RSA公钥。

要从y恢复x，你可以使用另一个数d来计算以下内容：

y^d mod n = (x^e)^d mod n = x^{ed} mod n = x

因为d是允许你解密的陷门，它是RSA密钥对中私钥的一部分，意味着它应该始终保持秘密。数d也称为秘密指数。

当然，d不是任意数；它是使e乘以d等价于1的数，因此对于任何x都有x^{ed} mod n = x。更准确地说，你必须满足ed mod φ(n) = 1才能得到x^{ed} = x^1 = x并正确解密消息。注意这里是在模φ(n)而不是模n下计算的，因为指数的行为类似于\(Z_n^*\)中元素的索引，而不是元素本身。由于\(Z_n^*\)有φ(n)个元素，索引必须小于φ(n)。

数φ(n)对RSA的安全性至关重要。事实上，找到RSA模数n的φ(n)等价于破解RSA，因为你可以通过计算e的逆元，轻松地从φ(n)和e推导出秘密指数d。因此p和q也应该是秘密的，因为知道p或q就可以通过计算(p − 1)(q − 1) = φ(n)得到φ(n)。

> **注意** φ(n)被称为群\(Z_n^*\)的阶；阶是群的一个重要特征，对其他公钥系统（如Diffie–Hellman和椭圆曲线密码学）至关重要。

### RSA密钥生成与安全性

密钥生成是创建RSA密钥对的过程，即公钥（模数n和公钥指数e）及其私钥（秘密指数d）。由于数字p和q（使得n = pq）以及阶φ(n)也应该是秘密的，你通常会将它们作为私钥的一部分。

要生成RSA密钥对，首先选择两个随机素数p和q，并从中计算φ(n)。然后计算d作为e的逆元。清单10-1展示了如何使用SageMath（https://www.sagemath.org）完成这一过程，SageMath是一个开源的类似Python的环境，包含许多数学包。

```
sage: p = random_prime(2^32); p
1103222539
sage: q = random_prime(2^32); q
17870599
sage: n = p*q; n
19715247602230861
sage: phi = (p-1)*(q-1); phi
1971524681137724
sage: e = random_prime(phi); e
13771927877214701
sage: d = xgcd(e, phi); d
15417970063428857
sage: mod(d*e, phi)
1
```

清单10-1：使用SageMath生成RSA参数

这里你使用random_prime()函数来选择随机素数p和q，它们小于给定的参数。接下来，你将p和q相乘得到模数n和φ(n)，即phi变量。然后你通过选择一个小于phi的随机素数来生成随机公钥指数e，以确保e在模phi下具有逆元。

你使用Sage中的xgcd()函数来生成相关的私钥指数d。该函数使用扩展欧几里得算法，给定两个数a和b，计算出数s和t，使得as + bt = GCD(a, b)。最后，你检查ed mod φ(n) = 1以确保d正确反转RSA置换。

注意：我在清单10-1中使用了64位的模数n，以避免输出占用多页，但在实践中，RSA模数至少应为2,048位才能保证安全。

现在你可以应用陷门置换，如清单10-2所示。




```
sage: x = 1234567
sage: y = power_mod(x, e, n); y
1904832305575504
sage: power_mod(y, d, n)
1234567
```

*列表 10-2：来回计算 RSA 陷门置换*

你将整数 1,234,567 分配给 *x*，然后使用 `power_mod(x, e, n)` 函数，即模 *n* 的指数运算，或方程形式中的 *x*<sup>*e*</sup> mod *n*，来计算 *y*。计算出 *y* = *x*<sup>*e*</sup> mod *n* 后，你使用陷门 *d* 计算 *y*<sup>*d*</sup> mod *n* 以返回原始的 *x*。

在没有陷门 *d* 的情况下找到 *x* 有多难？能够分解大数的攻击者可以通过恢复 *p* 和 *q*，然后计算 φ(*n*) 来从 *e* 计算出 *d*，从而破解 RSA。RSA 的另一个风险在于攻击者能够在不一定分解 *n* 的情况下，从 *x*<sup>*e*</sup> mod *n* 计算出 *x*，或计算模 *n* 的 *e* 次方根。虽然这两种风险似乎密切相关，但我们并不能确定它们是等价的。

假设分解和寻找 *e* 次方根的难度大致相同，RSA 的安全级别取决于三个因素：*n* 的大小、*p* 和 *q* 的选择，以及陷门置换的使用方式。如果 *n* 太小，就可以在合理的时间内将其分解，从而泄露私钥。为了安全，*n* 至少应为 2,048 位长（安全级别约为 90 位，需要约 2<sup>90</sup> 次运算的计算量）但最好为 4,096 位长（安全级别约为 128 位）。*p* 和 *q* 的值应为大小相近且不相关的随机素数。如果它们太小或过于接近，则更容易从 *n* 中确定其值。最后，你不应直接使用 RSA 陷门置换进行加密或签名，我稍后会讨论。

## 使用 RSA 进行加密

通常，RSA 与对称加密方案结合使用，其中 RSA 加密一个对称密钥，该密钥用于用对称密码（如 AES-GCM）加密消息。但用 RSA 加密消息或对称密钥比简单地将目标转换为数字 *x* 并计算 *x*<sup>*e*</sup> mod *n* 要复杂得多。

在下面的小节中，我将解释为什么对 RSA 陷门置换的朴素应用是不安全的，以及强大的基于 RSA 的加密是如何工作的。

### 教科书式 RSA 加密的可塑性

短语 *textbook RSA encryption* 描述了一种简化的 RSA 加密方案，其中进行指数运算的数字仅包含你想要加密的消息。例如，要加密字符串 *RSA*，你首先将其转换为数字——例如，通过将三个字母各自的 ASCII 编码作为字节连接起来：*R*（字节 52）、*S*（字节 53）和 *A*（字节 41）。 resulting byte string 525341 转换为十进制时等于 5,395,265，然后你可能会通过计算 5,395,265^e mod n 来加密它。在不知道密钥的情况下，无法解密消息——至少在理论上是这样。

然而，教科书式 RSA 加密是确定性的：如果两次加密相同的明文，你会得到两次相同的密文。而且还有一个更大的问题：给定两个教科书式 RSA 密文 y₁ = x₁^e mod n 和 y₂ = x₂^e mod n，你可以通过将这些密文相乘来推导出 x₁ × x₂ 的密文：

$$y_1 \times y_2 \bmod n = x_1^e \times x_2^e \bmod n = (x_1 \times x_2)^e \bmod n$$

结果是 (x₁ × x₂)^e mod n，即消息 x₁ × x₂ mod n 的密文。攻击者可以从两个 RSA 密文中创建新的有效密文，通过允许他们推断出有关原始消息的信息来破坏加密的安全性。这种弱点使教科书式 RSA 加密 *malleable* 可塑性。（如果你知道 x₁ 和 x₂，你也可以计算 (x₁ × x₂)^e mod n，但如果你只知道 y₁ 和 y₂，就不应该能够通过相乘密文得到乘法明文的密文。）

朴素教科书式 RSA 加密的另一个问题是存在“特殊”消息。不管 n 和 e 是什么，1^e = 1。因此，消息 1 在加密过程中保持不变。教科书式 RSA 还有许多其他问题，但你可以通过使用强大的 RSA 加密来避免它们。

## 使用 OAEP 的强 RSA 加密

为了使 RSA 密文不可塑，加密期间进行指数运算的数字应将消息数据与称为 *padding* 填充的额外数据结合起来，如图 10-1 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_227_0.png)

这种方式使用 RSA 加密的标准方法是使用最优非对称加密填充（OAEP），通常称为 RSA-OAEP。该方案涉及在应用 RSA 函数之前，通过用额外数据和随机性填充消息来创建与模数一样大的位串。

> **NOTE** 诸如 PKCS#1 标准和 NIST 的《特殊出版物 800-56B》等官方文件将 OAEP 称为 RSAES-OAEP。OAEP 在早期的 PKCS#1 v1.5 方法上进行了改进，后者是 RSA 提出的一系列公钥密码标准（PKCS）中的第一个。它明显比 OAEP 不安全，但在 OAEP 引入后仍在许多系统中被使用。

### 安全性

OAEP 使用 PRNG 通过使加密具有概率性来确保密文的不可区分性和不可塑性。只要 RSA 函数和 PRNG 安全，并且在较小程度上哈希函数不太弱，就已证明其安全。在使用 RSA 加密时，你应使用 OAEP 而不是其前身标准 PKCS#1 v1.5。

### 加密

在 OAEP 模式下使用 RSA 加密需要一条消息（如对称密钥 K）、一个 PRNG 和两个哈希函数。要创建密文，使用给定模数 n，长为 m 字节（即 8m 位，因此 n 小于 2^{8m}）。要加密 K，按如下方式形成编码消息

$M = H \| 00 \dots 00 \| 01 \| K$

其中 H 是 OAEP 方案定义的一个 h 字节常量，后面跟随必要的 00 字节数和一个 01 字节。图 10-2 显示了如何处理此编码消息 M。

![](img/ace4de942d037de8ea5835bc9fbe57cd_228_0.png)

图 10-2：使用 RSA-OAEP 加密对称密钥 K，其中 H 是固定参数，R 是随机位

你生成一个 h 字节的随机字符串 R 并设置 M = M ⊕ Hash1(R)，其中 Hash1(R) 与 M 等长。接下来，设置 R = R ⊕ Hash2(M)，其中 Hash2(M) 与 R 等长。现在使用这些新的 M 和 R 值形成一个 m 字节的字符串 P = 00 || M || R，其长度与模数 n 相同，并且你可以将其转换为小于 n 的整数。此转换得到数字 x，然后你使用它计算 RSA 函数 x^e mod n 以得到密文。

要解密密文 y，首先计算 x = y^d mod n，并据此恢复 M 和 R 的最终值。接下来，通过计算 M ⊕ Hash1(R ⊕ Hash2(M)) 来检索 M 的初始值。最后，验证 M 的形式为 H || 00 … 00 || 01 || K，其中 H 为 h 字节，后跟 00 字节和一个 01 字节。

实际上，参数 m 和 h（分别为模数的长度和 Hash2 输出的长度）通常为 m = 256 字节（用于 2,048 位 RSA）和 h = 32（使用 SHA-256 作为 Hash2）。这为 M 留下 m − h − 1 = 223 字节，其中最多 m − 2h − 2 = 190 字节可用于 K（“− 2”源于 M 中的 01 字节分隔符）。Hash1 哈希值随后由 m − h − 1 = 223 字节组成，这比任何常见哈希函数的哈希值都要长。为了构建具有这种不寻常输出长度的哈希，RSA 标准规范定义了一种掩码生成函数技术，可从任何哈希函数创建返回任意大哈希值的哈希函数。另一种方法是使用可扩展输出函数（XOF），如 SHAKE 或 BLAKE3，尽管这与标准规范不同。

## 使用 RSA 签名

数字签名可以证明与特定数字签名关联的私钥持有者签署了某条消息，通常是为了认可其内容。因为只有私钥持有者知道私钥指数 d，所以没有人可以从某个值 x 计算出签名 y = x^d mod n，但每个人都可以使用公钥指数 e 验证 y^e mod n = x。原则上，可以将该已验证的签名用作证据，证明私钥持有者签署了某条特定消息；这是一种称为不可否认性的属性。

将 RSA 签名视为加密的逆运算很诱人，但事实并非如此。使用 RSA 签名与使用私钥加密不同。加密提供保密性，而数字签名有助于防止伪造。这种差异最显著的例子是，允许签名方案泄露所签名消息的信息是可以的，因为消息不是秘密的。例如，一个泄露消息部分内容的方案可能是安全的签名方案，但不是安全的加密方案。

由于必要的处理开销，公钥加密只能处理短消息，这些消息通常是对称密钥而不是实际消息。然而，签名方案可以通过使用其哈希值 Hash(M) 作为代理来处理任意大小的消息，并且可以是确定性的同时仍保持安全。与 RSA-OAEP 类似，基于 RSA 的签名方案可以使用填充方案，但也可以使用 RSA 模数允许的最大消息空间。



## 教科书 RSA 签名

教科书 RSA 签名是一种通过直接计算 y = x^d mod n 来对消息 x 进行签名的方法，其中 x 可以是 1 到 n − 1 之间的任意数字。与教科书式加密类似，教科书 RSA 签名简单易于指定和实现，但在面对多种攻击时不安全。其中一种攻击涉及平凡伪造：注意到 1^d mod n = 1 且 (n − 1)^d mod n = n − 1，与私钥 d 的取值无关，攻击者可以在不知道 d 的情况下伪造 1 或 n − 1 的签名。

更令人担忧的是盲化攻击。例如，假设你想让第三方对某条消息 M 签名，而你知道他们绝不会自愿签署该消息。要发动此攻击，首先找到某个值 R，使得 R·M mod n 是受害者会自愿签名的消息。接下来，你会说服他们对该消息进行签名并向你展示其签名，该签名等于 S = (R·M)^d mod n，即消息的 d 次幂。给定该签名，你可以借助一些简单的计算推导出 M 的签名，即 M^d。

因为可以将 S 写成 (R·M)^d = R^{ed}M^d，并且由于 R^{ed} = R（根据定义），你有 S = (R·M)^d = R M^d。要获得签名 M^d，按如下方式除以 R：

S / R = R M^d / R = M^d

这通常是一种实用且强大的攻击。

## PSS 签名标准

RSA 概率签名方案（PSS）对于 RSA 签名而言，就像 OAEP 对于 RSA 加密一样。它通过添加填充数据来使消息签名更安全而设计。

图 10-3 演示了 PSS 在对该填充过程的结果进行 RSA 操作之前，将比模数窄的消息与一些随机和固定位组合起来。

![](img/ace4de942d037de8ea5835bc9fbe57cd_230_0.png)

图 10-3：使用 RSA 和 PSS 标准对消息 M 进行签名，其中 {n, d} 是私钥

像所有公钥签名方案一样，PSS 对消息的哈希值而不是消息本身进行操作。只有当哈希函数具有抗碰撞性时，签名 Hash(M) 才是安全的。因此你可以签名任意长度的消息，因为在对消息进行哈希后，无论消息的原始长度如何，你都会得到相同固定长度的哈希值。

为什么不通过仅将 OAEP 加密应用于 **Hash**(M) 来签名呢？不幸的是，你不能。虽然与 PSS 相似，但 OAEP 仅被证明对加密是安全的，而不是对签名。

与 OAEP 类似，PSS 也需要一个 PRNG 和两个哈希函数。其中一个 **Hash1** 是具有标准输出长度的典型哈希，如 SHA-256。另一个 **Hash2** 是像 OAEP 的 **Hash2** 那样的宽输出哈希。与 OAEP 类似，PSS 可以使用掩码生成函数（MGF）构造来构建此类哈希。

PSS 签名过程如下（其中 h 为 **Hash1** 的输出长度）：
- 1. 使用 PRNG 选择一个 r 字节的随机字符串 R。
- 2. 形成编码消息 M' = 00000000000000 || **Hash1**(M) || R，长度为 h + r + 8 字节（开头为 8 个零字节）。
- 3. 计算 h 字节字符串 H = **Hash1**(M')。
- 4. 设置 L = 00...00 || 01 || R，即 00 字节序列后跟 01 字节然后是 R，其中 00 字节的数量使得 L 的长度为 m − h − 1 字节（模数的字节宽度 m 减去哈希长度 h 再减 1）。
- 5. 设置 L = L ⊕ **Hash2**(H) 以用新值替换 L 的先前值。
- 6. 将 m 字节字符串 P = L || H || BC 转换为小于 n 的数字 x。这里，字节 BC 是在 H 之后附加的固定值。
- 7. 给定刚刚获得的 x 的值，计算 RSA 函数 x^d mod n 以获得签名。
- 8. 要验证给定消息 M 的签名，计算 **Hash1**(M) 并使用公钥指数 e 反转 RSA 函数并从签名中检索 L、H，然后是 M'，在每一步检查填充的正确性。

实际上，随机字符串 R（在 RSA-PSS 标准中称为盐）通常与哈希值一样长。例如，如果你使用 n = 2,048 位和 SHA-256 作为哈希，则值 L 为 m − h − 1 = 256 − 32 − 1 = 223 字节，随机字符串 R 通常为 32 字节。

与 OAEP 一样，PSS 是可证明安全的、标准化的，并且可在许多加密软件工具和库中使用，包括 OpenSSL 和 Go 语言的加密模块。同样与 OAEP 一样，它看起来不必要地复杂，容易出现实现错误和处理不当的边界情况。与 RSA 加密不同，PSS 用于签名有一个更简单的替代方案：无需 PRNG，使用单个哈希函数，且无需填充。

## 全域哈希签名

*Full Domain Hash (FDH)* 是你可以想象到的最简单的签名方案。要实现它，将字节字符串 **Hash(M)** 转换为数字 *x*，并创建签名 *y* = *x*<sup>*d*</sup> mod *n*，如图 10-4 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_232_0.png)

签名验证也很简单。给定一个为数字 *y* 的签名，计算 *x* = *y*<sup>*e*</sup> mod *n* 并将结果与 **Hash(M)** 进行比较。它乏味地简单、确定性且安全。那么为什么还要费心使用 PSS 的复杂性呢？

PSS 在 1996 年 *在 FDH 之后* 发布，并且它具有比 FDH 更令人信服的安全性证明。具体来说，其证明比 FDH 的证明提供了略高的安全保证，并且其对随机性的使用有助于加强该证明。

这些更强的理论安全保证是许多密码学家更喜欢 PSS 而非 FDH 的主要原因，但今天使用 PSS 的大多数应用程序都可以切换到 FDH 而不会有实质性的安全损失。然而，在某些情况下，使用 PSS 而非 FDH 是可行的，因为 PSS 的随机性可以保护它免受对其实现的某些攻击，例如我们在“事情可能出错的方式”第 211 页中讨论的故障攻击。

无论如何，RSA 签名（PSS 或 FDH）使用得越来越少。基于椭圆曲线的签名，如 ECDSA 和 EdDSA，变得越来越受欢迎，部分原因在于其签名计算速度要快得多（尽管 RSA 的签名验证通常更快）。

## RSA 实现

我希望你永远不必从头实现 RSA。如果你被要求这样做，就尽快跑开并质疑提出要求的人的理智。密码学家和工程师花了数十年时间才开发出快速、足够安全且理想上没有致命 bug 的 RSA 实现，因此重新发明 RSA 并不明智。即使有所有文档可用，完成这项艰巨的任务也需要数月时间。

通常，在软件中使用 RSA 时，你会使用提供执行 RSA 操作所需函数的库或 API。例如，
Go 语言在其 crypto 包中具有以下函数（来自 *https://go.dev/src/crypto/rsa/rsa.go*）：

```
func EncryptOAEP(hash hash.Hash, random io.Reader, pub *PublicKey, msg []byte,
label []byte) (out []byte, err error)
```

函数 EncryptOAEP() 接受一个哈希函数、一个 PRNG、一个公钥、一个消息以及一个标签（OAEP 的可选参数），并返回密文和错误代码。当你调用 EncryptOAEP() 时，它会调用 encrypt() 来计算给定填充数据的 RSA 函数，如列表 10-3 所示。

```
func encrypt(c *big.Int, pub *PublicKey, m *big.Int) *big.Int {
    e := big.NewInt(int64(pub.E))
    c.Exp(m, e, pub.N)
    return c
}
```

*列表 10-3：来自 Go 语言密码学库的核心 RSA 加密函数的实现*

这里的主要操作是 `c.Exp(m, e, pub.N)`，它将消息 m 提升到 e 次幂模 pub.N，并将结果赋给变量 c。

如果你选择实现 RSA 而不是使用现成的库函数，请确保依赖现有的 *big-number* 库，它是一组函数和类型，允许你定义和计算数千位长的大数上的算术运算。例如，你可能会使用 C 中的 GNU 多精度（GMP）算术库或 Go 的 big 包。（相信我，你不想自己实现大数算术。）

即使你只在实现 RSA 时使用库函数，也要确保你了解内部工作原理，以便评估风险并判断其是否符合应用程序的安全要求。

## 快速指数算法

*Exponentiation* 是在计算 x^e mod n 时将 x 提升到 e 次幂的操作。当处理 RSA 中的大数时，如果天真地实现，此操作可能极其缓慢。如何高效地计算指数运算？

计算 x^e mod n 的天真方法需要 e − 1 次乘法，如列表 10-4 中的伪代码算法所示。

```
expModNaive(x, e, n) {
    y = x
    for i = 1 to e − 1 {
        y = y * x mod n
    }
}
```



```text
return y
}
```

*清单 10-4：伪代码中的朴素指数算法，将 x 提升到模 n 下的 e 次幂*

该算法简单但效率极低。通过平方而不是不断乘以中间值 y 直到得到正确值，可以指数级更快地得到相同结果。这类方法被称为 *平方-乘法*、*平方求幂* 或 *二进制求幂*。

假设你想计算 \(3^{65,537} \bmod 36,567,232,109,354,321\)，例如。（数字 65,537 是大多数 RSA 实现中的公钥指数。）你可以将数字 3 自乘 65,536 次，或者你可以知道 65,537 可以写成 \(2^{16}+1\) 来处理这个问题，并改用一系列平方运算。本质上，你初始化一个变量 \(y=3\)，然后计算以下平方 (\(y^2\)) 运算：

1. 设置 \(y=y^2 \bmod n\)（现在 \(y=3^2 \bmod n\)）。
2. 设置 \(y=y^2 \bmod n\)（现在 \(y=(3^2)^2 \bmod n=3^4 \bmod n\)）。
3. 设置 \(y=y^2 \bmod n\)（现在 \(y=(3^4)^2=3^8 \bmod n\)）。
4. 设置 \(y=y^2 \bmod n\)（现在 \(y=(3^8)^2=3^{16} \bmod n\)）。
5. 设置 \(y=y^2 \bmod n\)（现在 \(y=(3^{16})^2=3^{32} \bmod n\)）。

如此等等，直到通过执行 16 次平方运算得到 \(y=3^{65,536}\)。

要得到最终结果，你将返回 \(3 \times y \bmod n=3^{65,537} \bmod n=26,652,909,283,612,267\)。换句话说，你只需用 17 次乘法而不是朴素方法中的 65,536 次乘法即可计算出结果。

更一般地，平方-乘法方法通过逐位扫描指数的位来工作，对每个指数位进行平方以使指数值加倍，并在遇到值为 1 的位时乘以原始数字。在前面的例子中，指数 65,537 的二进制表示为 10000000000000001，并且你对每个新位平方 \(y\)，并且仅对最开始和最后的位才乘以原始数字 3。

清单 10-5 显示了如何将此作为通用算法在伪代码中实现，以计算 \(x^e \bmod n\)，其中指数 \(e\) 由位 \(e_{m-1}e_{m-2}\cdots e_1e_0\) 组成，其中 \(e_0\) 是最低有效位。

```text
expMod(x, e, n) {
    y = x
    for i = m - 1 to 0 {
        y = y * y mod n
        if e_i == 1 then
            y = y * x mod n
    }
    return y
}
```

*清单 10-5：伪代码中的快速指数算法，将 x 提升到模 n 下的 e 次幂*

expMod() 算法的运行时间为 \(O(m)\)，而朴素算法的运行时间为 \(O(2^m)\)，其中 \(m\) 是指数的位长。这里，\(O()\) 是第 9 章中引入的渐近复杂度记号。

所有严肃的系统都实现了最简单平方-乘法方法的某种变体。其中一种变体是 *滑动窗口* 方法，它考虑位块而不是单个位来执行给定的乘法运算。例如，参见 Go 语言的函数 expNN()，其源代码可在 *https://go.dev/src/math/big/nat.go* 获取。

这些平方-乘法指数算法有多安全？不幸的是，加速过程的技巧往往会导致对某些攻击的脆弱性增加。

这些算法的弱点源于指数运算严重依赖指数的值。清单 10-5 中的 if 运算根据指数位是 0 还是 1 而采用不同的分支。如果某一位为 1，则 for 循环的一次迭代比为 0 时更慢，而监控 RSA 操作执行时间的攻击者可以利用这种时间差异来恢复私钥。这被称为 *时序攻击*。对硬件的攻击可以通过监控设备的功耗并观察哪些迭代执行了额外的乘法来区分 1 位和 0 位，从而揭示私钥的哪些位为 1。

根据平台类型的不同，信息通道可能不是执行时间。例如，你可以通过测量设备的功耗并观察哪些迭代执行了额外的乘法来区分指数中的 1 位和 0 位，从而揭示私钥位为 1 的情况。这是一种 *功耗分析攻击*。很少有开源密码库对这些类型的攻击包含有效的防御措施。

## 小指数以实现更快的公钥操作

因为 RSA 计算本质上是指数运算，其性能取决于所涉及数字的值，特别是指数。较小的指数需要更少的乘法，因此可以使指数运算大大加快。

原则上，公钥指数 \(e\) 可以是介于 3 和 \(\phi(n) - 1\) 之间的任意值，只要 \(e\) 与 \(\phi(n)\) 互质即可。但在实践中你只会发现较小的 \(e\) 值，有时 \(e = 65,537\) 是出于加密和签名验证速度的考虑。例如，Microsoft Windows CryptoAPI 只支持适合 32 位整数的公钥指数。\(e\) 越大，计算 \(x^e \bmod n\) 就越慢。

与公钥指数的大小不同，私钥指数 \(d\) 不可避免地与 \(n\) 大小相当，使得解密比加密慢得多，签名比验证慢得多。因为 \(d\) 是秘密的，所以它必须不可预测，因此不能限制为较小的值。例如，如果 \(e\) 固定为 65,537，则相应的 d 通常与模数 n 同数量级，如果 n 为 2,048 位长，则接近 \(2^{2,048}\)。

如第 206 页“快速指数算法”中所述，将一个数提升到 65,537 次幂需要 17 次乘法，而将一个数提升到某个 2,048 位数的幂则需要大约 3,000 次乘法。

你可以使用 OpenSSL 工具包来估计 RSA 的速度。例如，清单 10-6 显示了在配备 M2 芯片的 MacBook 上进行的 512 位、1,024 位、2,048 位和 4,096 位 RSA 操作的结果：

```text
Doing 1024 bits private rsa sign ops for 10s: 119019 1024 bits private RSA sign ops in 9.93s
Doing 1024 bits public rsa verify ops for 10s: 2573979 1024 bits public RSA verify ops in 9.93s
Doing 2048 bits private rsa sign ops for 10s: 19184 2048 bits private RSA sign ops in 9.93s
Doing 2048 bits public rsa verify ops for 10s: 769696 2048 bits public RSA verify ops in 9.93s
Doing 4096 bits private rsa sign ops for 10s: 3005 4096 bits private RSA sign ops in 9.92s
Doing 4096 bits public rsa verify ops for 10s: 206367 4096 bits public RSA verify ops in 9.91s
```

| RSA 密钥 | 签名 | 验证 | 签名/秒 | 验证/秒 |
|---|---|---|---|---|
| rsa 1024 位 | 0.000083s | 0.000004s | 11985.8 | 259212.4 |
| rsa 2048 位 | 0.000518s | 0.000013s | 1931.9 | 77512.2 |
| rsa 4096 位 | 0.003301s | 0.000048s | 302.9 | 20824.1 |

```text
--snip--
```

*清单 10-6：使用 OpenSSL 工具包（版本 3.2.0）进行 RSA 操作的示例基准测试*

要了解验证速度相比签名生成的快多少，计算验证速度与签名速度的比率。清单 10-6 中的基准测试显示，我得到的验证与签名速度比率约为 1,024 位、2,048 位和 4,096 位模数分别为 21.6、40.1 和 68.7。差距随着模数大小的增长而增大，因为 e 运算的乘法次数相对于模数大小保持恒定（例如当 e = 65,537 时为 17 次运算），而私钥运算始终需要更多的乘法来处理更大的模数，因为 d 会相应增长。

如果小指数这么好，为什么使用 65,537 而不是像 3 这样的小数？实际上，使用 OAEP、PSS 或 FDH 等安全方案实现 RSA 时，使用 3 作为指数是完全可以的（并且更快）。然而密码学家避免这样做，因为当 e = 3 时，较不安全的方案会使某些类型的数学攻击成为可能。数字 65,537 足够大以避免此类低指数攻击，并且它只有两个非零位，这降低了计算 \(x^{65,537}\) 时的计算时间。数字 65,537 对数学家来说也是特殊的：它是第四个费马数，或形式为

\(2^{2^4} + 1\)

的数

因为它等于 \(2^{16} + 1\)，其中 \(16 = 2^4\)，但这对大多数密码工程师来说只是一个无关紧要的好奇心。




## 中国剩余定理

加速解密和签名生成（即计算 y^d mod n）最常用的技巧是中国剩余定理（CRT），它能使 RSA 的速度提升约四倍。

CRT 通过计算两次模幂运算（分别模 p 和模 q）而不是一次模 n 的运算来加快解密。由于 p 和 q 远小于 n，执行两次“小”模幂运算比执行一次“大”模幂运算更快。

中国剩余定理并非 RSA 所特有。它是一个通用的算术结论，其最简形式是：如果 n = n1 n2 n3 …，其中 n_i 两两互素（即对任意不同的 i 和 j，有 GCD(n_i, n_j) = 1），那么可以从 x mod n1、x mod n2、x mod n3 … 计算出 x mod n 的值。例如，假设 n = 1,155，它是质因数 3 × 5 × 7 × 11 的乘积，并且你想求出满足 x mod 3 = 2、x mod 5 = 1、x mod 7 = 6 和 x mod 11 = 8 的 x。（我任意选择了 2、1、6 和 8。）要使用中国剩余定理求出 x，需计算 P(n_i) + P(n_j) + … 的和，其中 P(n_i) 的定义如下：

P(n_i) = (x mod n_i) × n / n_i × (1 / (n / n_i) mod n_i) mod n

注意，第二项 n/n_i 等于除 n_i 之外所有因子的乘积。要将此公式应用于本示例并恢复 x mod 1155，需计算 P(3)、P(5)、P(7) 和 P(11)；然后将它们相加，得到以下表达式：

[ 2 × 385 × (1/385 mod 3) + 1 × 231 × (1/231 mod 5) + 6 × 165 × (1/165 mod 7) + 8 × 105 × (1/105 mod 11) ] mod n

这里，我只是应用了前面 P(n_i) 的定义。（求出每个数字背后的数学原理很简单，但我不在此详述。）然后你可以将这个表达式化简为 [770 + 231 + 1980 + 1680] mod n = 41。由于 41 是我为这个示例挑选的数字，所以你得到了正确的结果。将 CRT 应用于 RSA 比前面的示例更简单，因为每个 n 只有两个因子（即 p 和 q）。给定要解密的密文 y，不必计算 y^d mod n，而是使用 CRT 计算 x_p = y^s mod p（其中 s = d mod (p − 1)）和 x_q = y^t mod q（其中 t = d mod (q − 1)）。将这两个表达式组合起来，按如下方式计算 x：x = (x_p × q × (1/q mod p) + x_q × p × (1/p mod q)) mod n。就是这样。即使结合使用平方-乘技巧，这也比单次模幂运算更快，因为乘法密集型运算是在模 p 和模 q 上进行的，这两个数的规模只有 n 的一半，而模幂运算的复杂度增长速度快于线性。当你将数字的规模加倍时，模幂运算的开销不只是翻倍——它的增长更快。

> **注意** *在最后一步操作中，你可以预先计算 q × (1/q mod p) 和 p × (1/p mod q) 这两个数，这意味着你只需计算两次乘法和一次模 n 的加法即可求出 x。*

遗憾的是，这些技术存在一个安全隐患。

## 问题可能出在哪里

比 RSA 方案本身更精妙的，是各种攻击手段——它们之所以奏效，要么是因为实现会泄露（或可能被诱导泄露）其内部信息，要么是因为 RSA 的使用方式不安全。在接下来的小节中，我将讨论这两类攻击的两个经典示例。

### 针对 RSA-CRT 的 Bellcore 攻击

针对 RSA 的 Bellcore 攻击是 RSA 历史上最重要的攻击之一。它于 1996 年首次被发现，之所以引人注目，是因为它利用了 RSA 对*故障注入*的脆弱性——这类攻击会迫使算法的某一部分行为异常，并可能产生错误结果。例如，攻击者可以通过突然改变硬件电路或嵌入式系统的电压供应，或将激光脉冲照射到芯片的精心选定部位，来暂时扰动它们。然后，攻击者可以通过观察结果受到的影响，来利用算法内部出现的故障。将正确结果与错误结果进行比较，可以提供算法内部值的信息，包括秘密值。同样，试图获知结果是否有效的尝试也可能泄露可利用的信息。

Bellcore 攻击就是这样一种故障攻击。它作用于使用中国剩余定理且具有确定性的 RSA 签名方案——也就是说，它适用于 FDH，但不适用于概率性的 PSS。

要理解 Bellcore 攻击，请回顾上一节的内容：使用 CRT 时，通过计算下式得到等于 x^d mod n 的结果，其中 x_p = y^d mod p，x_q = y^d mod q：

x = x_p × q × (1/q mod p) + x_q × p × (1/p mod q) mod n

现在假设攻击者在 x_q 的计算中诱发了一个故障，使你最终得到某个与真实 x_q 不同的错误值。我们将这个错误值称为 x_q'，将最终得到的结果称为 x'。然后，攻击者可以用正确的签名 x 减去错误的签名 x'，从而对 n 进行因式分解，结果如下：

x − x' = (x_q − x_q') × p × (1/p mod q) mod n

因此，x − x' 的值是 p 的倍数，所以 p 是 x − x' 的因子。由于 p 也是 n 的因子，n 与 x − x' 的最大公约数即为 p。GCD(x − x', n) = p。然后你可以计算 q = n/p 和 d，从而完全攻破 RSA 签名。

当你只知道消息已被签名、但不知道正确的签名时，这种攻击的一个变体仍然有效。还有一种类似的故障攻击，针对的是模数值而非 CRT 值的计算，但这里我不再详述。

### 共享私钥指数或模数

现在我将向你说明，为什么你的公钥不应与他人拥有相同的模数 *n*。

属于不同系统或不同人员的私钥应具有不同的私钥指数 *d*，即使这些密钥使用不同的模数也是如此。否则，你可以尝试用自己的 *d* 值去解密发给其他实体的加密消息，直到碰巧遇到一个共享相同 *d* 的密钥。同理，不同的密钥对应具有不同的模数 *n* 值，即使它们的 *d* 不同，因为 *p* 和 *q* 通常是私钥的一部分。因此，如果我与你共享相同的 *n*，从而也共享相同的 *p* 和 *q*，我就能利用 *p* 和 *q* 从你的公钥 *e* 计算出你的私钥。

设想你知道自己的私钥指数 *d₁* 和另一个与你共享相同模数 *n* 的人的公钥指数 *e₂*，但不知道其因子 *p* 和 *q*。你如何根据自己的私钥指数 *d₁* 计算出 *p* 和 *q*，进而找出另一个人的私钥指数 *d₂*？解决方法有点技术性，但也很优雅。

回顾一下，*d* 和 *e* 满足 *ed = kφ(n) + 1*，其中 φ(*n*) 是保密的，但可能揭示 *p* 和 *q*。你不知道 *k* 或 φ(*n*)，但你可以计算出 *kφ(n) = ed − 1*。

你能用 *kφ(n)* 做什么？根据*欧拉定理*，对于任何与 *n* 互素的数 *a*，都有 *a*<sup>φ(n)</sup> ≡ 1 mod *n*。因此，在模 *n* 下，你得到如下结果：

$$a^{k\varphi(n)} = \left(a^{\varphi(n)}\right)^k = 1^k = 1 \pmod n$$

由于 *kφ(n)* 是偶数，你可以将其写成 2<sup>s</sup>*t* 的形式，其中 *s* 和 *t* 是某个数。也就是说，你将能把 *a*<sup>kφ(n)</sup> = 1 mod *n* 写成 *x*<sup>2</sup> = 1 mod *n* 的形式，其中 *x* 可以很容易地从 *kφ(n)* 计算出来。你可以称这样的 *x* 为*单位根*。

关键的观察是，*x*<sup>2</sup> = 1 mod *n* 等价于说 *x*<sup>2</sup> − 1 = (*x* − 1)(*x* + 1) 整除 *n*。换句话说，*x* − 1 或 *x* + 1 必定与 *n* 有公因子，而这可以为你提供 *n* 的因式分解。

清单 10-7 展示了这种方法的一个 Python 实现，为了简单起见，我使用小的 64 位数字，从 *n* 和 *d* 中找出因子 *p* 和 *q*。

```python
from math import gcd

n = 36567232109354321
e = 13771927877214701
d = 15417970063428857
```

```
❶ kphi = d*e - 1
   t = kphi

❷ while t % 2 == 0:
       t = divmod(t, 2)[0]

❸ a = 2
   while a < 100:
       ❹ k = t
           while k < kphi:
               x = pow(a, k, n)
               ❺ if x != 1 and x != (n - 1) and pow(x, 2, n) == 1:
                   ❻ p = gcd(x - 1, n)
                       break
               k = k*2
       a = a + 2

   q = n//p
❼ assert (p*q) == n
   print('p = ', p)
   print('q = ', q)
```

*清单 10-7：一个根据私钥指数 d 计算质因数 p 和 q 的 Python 程序*

该程序从 e 和 d 出发确定 kφ(n) ❶，方法是找出数 t，使得对某个 s 有 kφ(n) = 2ˢt ❷。然后，它寻找满足 (aᵏ)² = 1 mod n ❸ 的 a 和 k，并以 t 作为 k 的起点 ❹。当此条件满足时 ❺，你就找到了一个解。随后，它确定因子 p ❻，并验证 ❼ pq 的值等于 n 的值。然后，它打印出 p 和 q 的结果值：

```
p = 2046223079
q = 17870599
```

该程序正确地返回了这两个因子。

## 延伸阅读

RSA 本身值得用一本书来讲述。我不得不省略许多重要且有趣的主题，例如 Daniel Bleichenbacher 对 OAEP 前身（标准 PKCS#1 v1.5）的填充预言机攻击，或 Manger 对 OAEP 的填充预言机攻击，这两种攻击在思想上与第 4 章中对分组密码的填充预言机攻击类似。此外还有 Michael Wiener 对低私钥指数 RSA 的攻击，以及使用 Coppersmith 方法对具有小指数且可能存在不安全填充的 RSA 的攻击。

要查看与侧信道攻击和防御相关的研究成果，请参阅自 1999 年以来举办的 CHES 研讨会论文集，网址为 *https://ches.iacr.org*。撰写本章时，最有用的参考资料之一是


Dan Boneh 的《Twenty Years of Attacks on the RSA Cryptosystem》，是一篇综述，回顾并解释了对 RSA 最重要的攻击。关于定时攻击的参考，Billy Bob Brumley 和 Dan Boneh 所著论文《Remote Timing Attacks Are Practical》是必读之作，既因其分析性贡献，也因其实验性贡献。要了解更多关于故障攻击的内容，请阅读 Dan Boneh、Richard DeMillo 和 Richard Lipton 所著 Bellcore 攻击论文《On the Importance of Eliminating Errors in Cryptographic Computations》的完整版本。

尽管有时痛苦且令人沮丧，但学习 RSA 实现工作原理的最佳方式是查阅广泛使用的实现的源代码。例如，查看 OpenSSL、NSS（Mozilla Firefox 浏览器使用的库）、Crypto++ 或其他流行软件中的 RSA 及其底层大数算术实现，并检查其算术操作的实现以及对其定时攻击和故障攻击的防御措施。

### 11

### 迪菲-赫尔曼

![](img/ace4de942d037de8ea5835bc9fbe57cd_242_0.png)

1976 年 11 月，斯坦福大学的研究人员 Whitfield Diffie 和 Martin Hellman 发表了题为《New Directions in Cryptography》的研究论文，从此彻底改变了密码学。他们的论文提出了公钥加密和签名的概念，尽管他们实际上并没有这些方案；他们只是提出了他们所称的 *public-key cryptosystem*，一种协议，允许双方通过交换窃听者可见的信息来建立共享密钥。这现在被称为 *Diffie–Hellman (DH) protocol*。在 Diffie–Hellman 之前，建立共享密钥需要繁琐的程序，例如手动交换密封信封。

to have about as many possible values as elements in Z_p* and therefore as many possible values for the shared secret. 为了确保最高安全性，安全的 DH 参数应使用素数 p，使得 (p − 1)/2 也是素数。这样的安全素数保证群中没有会使 DH 更易被破解的小子群。使用安全素数时，DH 可以使用 Z_p* 中的任何元素，除了 1 和 p − 1；值得注意的是，g = 2 可使计算略微更快。但生成安全素数 p 所花费的时间比生成完全随机素数多。

例如，OpenSSL 工具包的 dhparam 命令仅生成安全的 DH 参数，但算法中内置的额外检查导致执行时间大幅增加，如列表 11-1 所示。

```
$ time openssl dhparam 2048
Generating DH parameters, 2048 bit long safe prime, generator 2
This is going to take a long time
--snip--
-----BEGIN DH PARAMETERS-----
MIJBCAKCAQEAoSIbyA9e8e44q7V89rceO8v8d/12svwhIIjG9EPwWrr7FkfYhYkU9
fRNtmi1GCTfxc9EDf+4zw+AbRBc6O0LGsxUoPn0d1/G/YDygp1FSM3Xeswqe a
SD+B7628pWtaCZGKZham7vmiN8azGeYaUcckTk jWceHVIVXe5fvuU7k7+C2wKk
iiyMfM8thZm9W/shiKNV2+SshTD6r3C2/hfu7XdOIa1T6ise83YicU/cRaDmK6
zgbKn3S1CjW1M4M3+m1+VhOUFz/nWTJ1IWAVC+a0LK8upqRgApOgHkVqzP/CgWbW
XAOE8NcQqroJomUSB5e1qfpAyvBWPkwrQWIBAg==
-----END DH PARAMETERS-----
openssl dhparam 2048 7.46s user 0.10s system 99% cpu 7.593 total
```

Listing 11-1: 使用 OpenSSL 工具包测量生成 2,048 位 Diffie–Hellman 参数的执行时间

使用 OpenSSL 工具包生成 DH 参数大约需要八秒钟（通常观察到的生成时间在 30 秒左右，甚至超过 1 分钟）。

为了比较，列表 11-2 显示了在同一系统上生成相同大小的 RSA 参数需要多长时间（即两个素数 p 和 q，每个的大小为 DH 中使用的 p 的一半）。

```
$ time openssl genrsa 2048
Generating RSA private key, 2048 bit long modulus
.......................................+...
.......................................+...
e is 65537 (0x10001)
-----BEGIN RSA PRIVATE KEY-----
--snip--
-----END RSA PRIVATE KEY-----
openssl genrsa 2048 0.16s user 0.01s system 95% cpu 0.171 total
```

Listing 11-2: 在测量执行时间的同时生成 2,048 位 RSA 参数

生成 DH 参数所需时间约为生成相同安全级别 RSA 参数的 50 倍，主要原因是为创建 DH 参数而生成的素数受到额外约束。

## Diffie–Hellman 问题

DH 协议的安全性依赖于计算问题的难度，尤其是第 9 章中的离散对数问题（DLP）。你可以通过从其公钥值 $a$ 中恢复私钥值 $g^a$ 来破解 DH，这归结为求解一个 DLP 实例。但在使用 DH 计算共享密钥时，我们关心的不仅仅是离散对数问题。我们还关心两个特定于 DH 的问题。

### 计算问题

*computational Diffie–Hellman (CDH)* 问题是在不知道密钥值 $a$ 和 $b$ 的情况下，仅根据公钥值 $g^a$ 和 $g^b$ 计算共享密钥 $g^{ab}$。其动机是确保即使窃听者截获了 $g^a$ 和 $g^b$，他们也不应能够确定共享密钥 $g^{ab}$。

如果你能求解 DLP，那么你也能求解 CDH；也就是说，如果你根据 $g^a$ 和 $g^b$ 确定 $a$ 和 $b$，那么你就能计算出 $g^{ab}$。换句话说，DLP *至少* 与 CDH 一样难。但你不能确定 CDH 是否至少与 DLP 一样难，这将使这两个问题难度相等。换句话说，DLP 之于 CDH 就像因数分解问题之于 RSA 问题。（请记住，因数分解可以让你求解 RSA 问题，但不一定反之。）

Diffie–Hellman 与 RSA 还有另一个相似之处，即对于给定的模数大小，DH 提供与 RSA 相似的安全级别。例如，使用 2,048 位素数 $p$ 的 DH 协议提供大约 90 位安全性，与使用 2,048 位模数的 RSA 相同。事实上，破解 CDH 的最快方法是使用 *number field sieve* 算法求解 DLP，该方法与通过因数分解其模数来破解 RSA 的通用数域筛（GNFS）类似但不相同。

### 判定问题

当你需要比 CDH 难度更强的假设时，就出现了 *decisional Diffie–Hellman (DDH)* 问题。给定 $g^a$、$g^b$ 以及一个值，该值要么是 $g^{ab}$ 要么是某个随机 $c$ 的 $g^c$（两者各有 1/2 的概率），DDH 问题在于确定是否选择了 $g^{ab}$（对应于 $g^a$ 和 $g^b$ 的共享密钥）。

相对于依赖 CDH，依赖 DDH 在以下情况下相关：设想攻击者仅根据 2,048 位的 $g^a$ 和 $g^b$ 值能计算出 $g^{ab}$ 的前 32 位。虽然 CDH 仍然未被破解，因为 32 位可能不足以完全恢复 $g^{ab}$，但攻击者已经了解了有关共享密钥的一些信息，这可能会使其能够破坏应用程序的安全性。

为了确保攻击者无法了解有关共享密钥 $g^{ab}$ 的任何信息，该值需要与随机群元素 *indistinguishable*，正如加密方案在密文与随机字符串无法区分时是安全的。也就是说，给定 $g^{a}$、$g^{b}$，攻击者不应能够确定给定数字是 g^{ab} 还是某个随机 c 的 g^{c}。判定 Diffie–Hellman 假设认为没有任何攻击者能有效地求解 DDH。

如果 DDH 困难，那么 CDH 也困难，你无法了解有关 g^{ab} 的任何信息。因此，如果你能求解 CDH，你也能求解 DDH：给定三元组 (g^{a}, g^{b}, x)，你就能从 g^{a} 和 g^{b} 推导出 g^{ab} 并检查结果是否等于给定的 x。

总之，DDH 从根本上比 CDH 更容易（值得注意的是，与 CDH 相反，DDH 在 Z_{p}^{*} 上并不困难），但 DDH 困难性是密码学中的一个主要假设，也是研究最多的假设之一。

## Diffie–Hellman 的变体

有时密码学家设计新的方案并证明它们至少与求解某个困难问题一样难以破解。但此类困难问题并不总是 CDH 或 DDH，而是可以是它们的变体。我们希望能够证明破解密码系统与求解 CDH 或 DDH 一样困难，但这对于高级密码机制来说并不总是可能的，通常是因为此类方案涉及比基本 Diffie–Hellman 协议更复杂的操作。

例如，在一个类似 DH 的问题中，给定 g^{a}，攻击者尝试计算 g^{1/a}，其中 1/a 是群中 a 的逆元（通常是某个素数 p 的 Z_{p}^{*}）。在另一个问题中，攻击者可能会区分随机 a 和 b 的对 (g^{a}, g^{ja}) 与对 (g^{a}, g^{1/a})。最后，在双 Diffie–Hellman 问题中，给定 g^{a}、g^{b} 和 g^{c}，攻击者尝试计算两个值 g^{ab} 和 g^{ac}。有时此类 DH 变体与 CDH 或 DDH 一样困难，有时它们从根本上更容易——因此提供较低的安全保证。作为练习，尝试找出这些问题难度与 CDH 和 DDH 难度之间的联系。（双 Diffie–Hellman 实际上与 CDH 一样困难，但证明起来并不容易！）

## 密钥协商协议

Diffie–Hellman 问题旨在构建安全的密钥协商协议，这些协议借助共享密钥在网络上通信的两个或多个方之间实现安全通信。各方将此密钥转换为一个或多个会话密钥——对称密钥，用于在会话期间加密和认证交换的信息。

在研究实际的 DH 协议之前，你应该了解是什么使密钥协商协议安全，以及更简单的协议如何工作。我们将从一个普遍使用的、不依赖于 DH 的密钥协商协议开始讨论。

### 非 DH 密钥协商

为了了解密钥协商协议的工作原理以及其安全的含义，让我们来看一下 4G 和 5G 的协议

用于在 SIM 卡和电信运营商之间建立通信的电信标准：认证密钥协商（AKA）。它不使用 Diffie–Hellman 函数，而是仅使用对称密钥运算。图 11-1 详细说明了该协议的工作方式。

![](img/ace4de942d037de8ea5835bc9fbe57cd_247_0.png)

图 11-1：4G 和 5G 电信中的 AKA 协议

在此协议描述中，SIM 卡拥有运营商所知的密钥 K。运营商通过选择一个随机值 R 开始会话，然后基于两个伪随机函数 PRF0 和 PRF1 计算两个值 SK 和 V1。接下来，运营商向 SIM 卡发送一条包含值 R 和 V1 的消息，这些值对攻击者可见。一旦 SIM 卡获得 R，它就拥有了用 PRF0 计算 SK 所需的内容，并且会进行计算。本次会话的双方最终得到一个共享密钥 SK，攻击者无法通过简单查看双方交换的消息，或甚至通过修改或注入新消息来确定该密钥。SIM 卡通过使用 PRF1、K 和 R 重新计算 V1，并检查计算出的 V1 是否与运营商发送的 V1 匹配，来验证自己正在与运营商通信。SIM 卡随后使用新的函数 PRF2，以 K 和 R 作为输入计算验证值 V2，并将其发送给运营商。运营商通过计算 V2 并检查计算值是否与收到的 V2 匹配，来验证 SIM 卡是否知道 K。

按我所描述的协议，有一种方法可以利用重放攻击欺骗 SIM 卡。基本上，如果攻击者捕获一对 (R, V1)，他们可能会将其发送给 SIM 卡，并诱使 SIM 卡相信该对来自知道 K 的合法运营商。为了防止此攻击，协议包含额外的检查以确保相同的 R 不会被重复使用。

如果 K 被泄露就会出现问题。例如，泄露 K 的攻击者可以执行中间人攻击并监听所有明文通信。此类攻击者可以在假装同时是合法的 SIM 卡运营商和 SIM 卡的情况下在双方之间发送消息。即使在某次通信时 K 未被泄露，攻击者也可以记录通信以及密钥协商期间交换的任何消息，并在日后找到 K 时利用捕获的 R 值解密这些通信。攻击者随后可以确定过去的会话密钥并用它们解密记录的流量——在这种情况下，协议不提供 *forward secrecy*。

## 密钥协商协议的攻击模型

密钥协商协议的安全性没有单一定义，且在没有上下文且不考虑攻击模型和安全目标的情况下，密钥协议永远不会完全安全。例如，你可以认为之前的 4G/5G 协议是安全的，因为被动攻击者找不到会话密钥，但它也是不安全的，因为一旦密钥 K 泄露，就会危及所有先前和未来的通信。

密钥协商协议中存在不同的安全概念，以及三种主要攻击模型，这些模型取决于协议泄露的信息。从弱到强，分别是 *network attacker*、*data leak* 和 *breach*：

### 网络攻击者
该攻击者观察运行密钥协商协议的两个合法方之间交换的消息，并可以记录、修改、丢弃或注入消息。为了抵御此类攻击者，密钥协商协议不得泄露有关已建立共享秘密的任何信息。

### 数据泄露
在此模型中，攻击者获取一个或多个协议执行中的会话密钥和所有 *temporary* 秘密（例如电信协议示例中的 SK），但不获取长期秘密（如同一协议中的 K）。

### 泄露（或破坏）
在此模型中，攻击者获知一个或多个方的长期密钥。一旦发生泄露，安全性就不再可实现，因为攻击者可以在协议后续会话中冒充一个或两个方，因为这是识别一方的信息（至少在理论上如此，因为在实践中诸如 IP 白名单等机制可以降低冒充风险）。尽管如此，攻击者不应能够恢复在获取密钥之前执行的会话的秘密。

现在我们已经了解了攻击模型并看到了攻击者能做什么，让我们探讨安全目标——即协议应提供的保证。你可以设计密钥协商协议以满足多个安全目标。这里描述了四个最相关的目标，从最简单到最复杂：

### 身份认证
协议应允许 *mutual authentication*，即每个方都可以验证另一方。AKA 指的是协议对双方进行身份验证时。

### 密钥控制
任何一方都不应能够选择最终的共享秘密或将其强制为特定子集。之前讨论的 4G/5G 密钥协商协议缺乏此属性，因为运营商选择的值 R 完全决定了最终的共享密钥。

## 前向保密

即使所有长期秘密都被泄露，攻击者也不应能够计算协议先前执行的共享秘密，即使他们记录所有先前的执行或可以注入或修改先前执行的消息。前向保密或前向安全协议保证，即使你必须将设备及其秘密交付给某个机构，他们也无法解密你之前的加密通信。（4G/5G 密钥协商协议不提供前向保密。）

## 抗密钥泄露冒充（KCI）

KCI 发生时，攻击者泄露了某方的长期密钥并可利用它冒充另一方。例如，4G/5G 密钥协商协议允许简单的密钥泄露冒充，因为双方共享相同的密钥 K。理想的密钥协商协议应防止此类攻击。

## 性能

要实用，密钥协商协议应既高效又安全。考虑密钥协商协议效率时应考虑多个因素，包括交换的消息数量、其长度、实现协议的计算工作量，以及是否可以进行预计算以节省时间。协议在交换更少、更短的消息时通常更高效，并且最好将交互性保持在最小，以便任一方不必等待接收消息后再发送下一条消息。你通常可以通过其以往往返次数的持续时间，或发送消息并接收响应的时间来衡量协议的效率。

往返时间通常是协议延迟的主要原因，但各方需要进行的计算量也很重要；所需计算越少，提前可进行的预计算越多越好。例如，4G/5G 密钥协商协议交换两个各为数百位的消息，必须按特定顺序发送。你可以使用此协议进行预计算以节省时间，因为运营商可以提前选择许多 R 值；预先计算匹配的 SK、V₁ 和 V₂ 值；并将它们全部存储在数据库中。在这种情况下，预计算的优点是减少了长期密钥的暴露。

## Diffie–Hellman 协议

Diffie–Hellman 函数是大多数已部署的公钥协商协议的核心——例如 TLS 和 SSH。然而，并没有单一的 Diffie–Hellman 协议，而是有多种使用 DH 函数建立共享秘密的方法。我们将在以下各节中回顾三种协议。在每项讨论中，我将坚持使用通常的密码占位符名称并称两个方为 Alice 和 Bob，攻击者为 Eve。我将 *g* 写为用于算术运算的群的生成元，该值事先固定且为 Alice、Bob 和 Eve 所知。

### 匿名 Diffie–Hellman
*Anonymous Diffie–Hellman* 是最简单的 Diffie–Hellman 协议。它是匿名的，因为它未经身份验证；参与者没有任一方可以验证的密码学身份，且任一方都不持有长期密钥。Alice 无法向 Bob 证明她是 Alice，反之亦然。

在匿名 Diffie–Hellman 中，每个方选择一个随机值（Alice 为 *a*，Bob 为 *b*）用作私钥，并将相应的公钥发送给另一方对等体。图 11-2 更详细地展示了该过程。

![](img/ace4de942d037de8ea5835bc9fbe57cd_250_0.png)

Alice 使用她的指数 *a* 和群基 *g* 计算 **A = gᵃ**，并将其发送给 Bob。Bob 接收 *A* 并计算 **Aᵇ**，其等于 **(gᵃ)ᵇ**。Bob 现在获得值 **gᵃᵇ** 并从他的随机指数 *b* 和值 *g* 计算 **B**。他随后将 **B** 发送给 Alice，Alice 用它计算 **gᵃᵇ**。Alice 和 Bob 在执行涉及将 *g* 和接收到的值提升到其私钥指数幂的类似操作后，最终得到相同的值 **gᵃᵇ**。一个简单的协议，仅对最懒的攻击者安全。

攻击者可以用中间人攻击击垮匿名 DH。网络攻击者只需拦截消息并假装是 Bob（对 Alice）并假装是 Alice（对 Bob），如图 11-3 所示。



![](img/ace4de942d037de8ea5835bc9fbe57cd_251_0.png)

*图 11-3：对匿名 Diffie–Hellman 协议的中间人攻击*

与之前的交换一样，Alice 和 Bob 选择随机指数，*a* 和 *b*。Alice 现在计算并发送 A，但 Eve 拦截并丢弃了该消息。Eve 然后选择一个随机指数，*c*，并计算 C = g^c 发送给 Bob。由于该协议没有身份验证，Bob 相信他从 Alice 收到的是 C，并继续计算 g^bc。Bob 然后计算 B 并将该值发送给 Alice，但 Eve 再次拦截并丢弃该消息。Eve 现在计算 g^bc，选择一个新的指数，*d*，计算 g^ad，从 g^d 计算出 D，并将 D 发送给 Alice。Alice 也计算出 g^ad。

结果是，在这次攻击中，攻击者 Eve 与 Alice 共享一个密钥（g^ad），与 Bob 共享另一个密钥（g^bc），而 Alice 和 Bob 却认为他们之间共享同一个密钥。完成协议执行后，Alice 从 g^ad 派生对称密钥来加密发送给 Bob 的数据，但 Eve 拦截加密消息，解密它们，并使用从 g^bc 派生的另一组密钥重新加密给 Bob——在可能修改明文之后。所有这一切都在 Alice 和 Bob 不知情的情况下发生；他们注定要失败。

为了挫败这次攻击，你需要一种方式来验证各方身份，以便 Alice 能证明她是真正的 Alice，Bob 能证明他是真正的 Bob。幸运的是，有办法做到这一点。

## 经身份验证的 Diffie–Hellman

*经身份验证的 Diffie–Hellman* 可解决可能影响匿名 DH 的中间人攻击。Authenticated DH 为双方配备私钥和公钥，从而允许 Alice 和 Bob 对消息进行签名，防止 Eve 冒充他们发送消息。这里，签名不是用 DH 函数计算的，而是用 RSA-PSS 等公钥签名方案计算的。因此，要成功代表 Alice 发送消息，攻击者需要伪造有效签名，而使用安全的签名方案这是不可能的。图 11-4 显示了 authenticated DH 的工作原理。

![](img/ace4de942d037de8ea5835bc9fbe57cd_252_0.png)

*图 11-4：经身份验证的 Diffie–Hellman 协议*

第一行上的标签 **Alice** (*priv*<sub>A</sub>, *pub*<sub>B</sub>) 表示 Alice 持有自己的私钥 *priv*<sub>A</sub>，以及 Bob 的公钥 *pub*<sub>B</sub>。这个 *priv/pub* 密钥对被称为 *长期* 密钥，因为它事先固定，并在协议的连续运行中保持不变。Alice 可以将她的密钥对 *priv*<sub>A</sub>/*pub*<sub>A</sub> 与 Bob 以外的各方一起使用，只要他们知道 *pub*<sub>A</sub>（他们如何知道它是另一个问题，也是密码学中最难的运营问题之一）。这些长期私钥应保密，而公钥被认为攻击者已知。

Alice 和 Bob 首先像匿名 DH 一样选择随机指数 *a* 和 *b*。然后 Alice 根据她的签名函数 **sign**、私钥 *priv*<sub>A</sub> 和 *A* 的组合计算 *A* 和签名 *sig*<sub>A</sub>。现在 Alice 将 *A* 和 *sig*<sub>A</sub> 发送给 Bob，Bob 用她的公钥 *pub*<sub>A</sub> 验证 *sig*<sub>A</sub>。如果签名无效，Bob 就知道该消息不是来自 Alice，并丢弃 *A*。

如果签名正确，Bob 从 *A* 和他的随机指数 *b* 计算出 *g*<sup>ab</sup>。然后他根据 **sign** 函数、他的私钥 *priv*<sub>B</sub> 和 *B* 的组合计算 *B* 和他自己的签名。他将 *B* 和 *sig*<sub>B</sub> 发送给 Alice，Alice 尝试用 Bob 的公钥 *pub*<sub>B</sub> 验证 *sig*<sub>B</sub>。只有在 Bob 的签名成功验证后，Alice 才会计算 *g*<sup>ab</sup>。

### 对抗网络攻击者的安全性

Authenticated DH 对网络攻击者是安全的，因为他们无法获知共享密钥 *g*<sup>ab</sup> 的任何信息，因为他们忽略了 DH 指数。Authenticated DH 还提供前向保密：即使攻击者在某个时间点破坏任一方，如前面讨论的 *breach* 攻击模型中所述，他们会获知私钥签名密钥，但不会获知任何临时 DH 指数；因此，他们无法获知任何先前共享密钥的值。

经身份验证的 DH 变体对 *密钥控制* 仅提供部分保护。Alice 不能构造特殊的 *a* 值来限制共享密钥 $g^{ab}$ 的选择，因为她还不知道 $g^b$，它对结果的影响与 *a* 一样大。（一个例外是如果 Alice 选择 $a = 0$，那么对于任何 $b$ 都有 $g^{ab} = 1$。因此协议应拒绝 0，尽管实际实现可能不会这样做。）然而，Bob 可以尝试多个 $b$ 值，直到找到一个“适合他”的值；例如，$g^{ab}$ 具有某些属性，如前 16 位为 1。

你可以通过在 Alice 发送她的 $g^a$ 之前，将 **Hash**($g^b$) 从 Bob 发送给 Alice 作为第一条消息，从而消除 Bob 对密钥值的控制。我将留给你分析此修改并理解其工作原理（新发送的消息是 Bob 公钥的 *承诺*）。

Authenticated DH 还有其他限制。其中之一是，Eve 可以通过记录 $A$ 和 $sig_A$ 的先前值并重放给 Bob 来假装成 Alice。Bob 错误地认为他与 Alice 共享一个密钥，尽管 Eve 无法获知该密钥，因为她不知道 Alice 的秘密 $a$。因此她无法从 Bob 发送的 $B$ 计算出 $B^a$。

你可以通过添加 *密钥确认* 过程来消除这种风险，在此过程中 Alice 和 Bob 互相证明他们拥有共享密钥。例如，对于某个哈希函数 **Hash**，Alice 和 Bob 可以分别通过发送 **Hash**($pub_A \parallel pub_B \parallel g^{ab}$) 和 **Hash**($pub_B \parallel pub_A \parallel g^{ab}$) 来执行密钥确认。双方都可以通过重新计算其结果来验证这些哈希值是否正确。公钥 $pub_A \parallel pub_B$ 和 $pub_B \parallel pub_A$ 的不同顺序确保 Alice 和 Bob 会发送不同的值，并且攻击者无法通过复制 Bob 的哈希值来假装成 Alice。

### 对抗数据泄露的安全性

Authenticated DH 对数据泄露攻击者的脆弱性更令人担忧。在这种攻击中，攻击者获知临时、短期秘密的值（即指数 $a$ 和 $b$），并利用该信息冒充通信方之一。如果 Eve 获知指数 $a$ 的值以及发送给 Bob 的 $sig_A$ 的值，她可以启动协议的新执行并冒充 Alice，如图 11-5 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_253_0.png)

*图 11-5：对经身份验证的 Diffie–Hellman 协议的冒充攻击*

在此攻击场景中，Eve 获知 a 的值并重放相应的 A 及其签名 sig_A，假装成 Alice。Bob 验证签名并从 A 计算出 g^{ab}，然后发送 B 和 sig_B，Eve 然后使用窃取的 a 计算出 g^{ab}。这导致双方拥有共享密钥。Bob 现在认为他正在与 Alice 交谈。

你可以通过将长期密钥集成到共享密钥计算中来保护 authenticated DH 免受临时秘密泄露的影响，这样如果不知道长期秘密就无法确定共享密钥。

## Menezes–Qu–Vanstone

The Menezes–Qu–Vanstone (MQV) protocol is a milestone in the history of DH-based protocols. 设计于 1998 年，当 NSA 将其纳入其 Suite B 时，MQV 被批准用于保护大多数关键资产，Suite B 是一组旨在保护机密信息的算法组合。（NSA 最终放弃了 MQV，allegedly 因为它未被使用。我稍后会讨论原因。）

MQV is Diffie–Hellman on steroids. It's more secure than authenticated DH, and it improves on authenticated DH's performance properties. 特别是，MQV 允许用户仅发送两条消息，彼此独立，以任意顺序发送。用户还可以发送比 authenticated DH 更短的消息，并且不需要发送显式的签名或验证消息。换句话说，你不需要在 Diffie–Hellman 函数之外再使用签名方案。

As with authenticated DH, in MQV Alice and Bob each hold a long-term private key as well as the long-term public key of the other party. 不同之处在于 MQV 密钥不是签名密钥：它们由私钥指数 x 和公值 g^x 组成。图 11-6 显示了 MQV 协议的操作。

![](img/ace4de942d037de8ea5835bc9fbe57cd_254_0.png)

图 11-6：MQV 协议

x 和 y 分别是 Alice 和 Bob 的长期私钥，X 和 Y 是他们的公钥。Bob 和 Alice 从各自的私钥和对方的公钥开始，后者是私钥的 g 的幂。各自选择一个随机指数，然后 Alice 计算 A 并发送给 Bob，Bob 然后计算 B 并发送给 Alice。一旦 Alice 得到 Bob 的临时公钥 B，她将其与她的长期私钥 x 结合，

她通过自己的一次性私钥 *a* 和 Bob 的长期公钥 *Y*，计算 \((B \times Y^\beta)^{a + x_A}\) 的结果，如图 11-6 所示。展开这个表达式，你将得到：

\[(B \times Y^\beta)^{a + x_A} = \left(g^b \times (g^y)^\beta\right)^{a + x_A} = \left(g^{b + \beta y}\right)^{a + x_A} = g^{(b + \beta y)(a + x_A)}\]

与此同时，Bob 计算 \((A \times X^\alpha)^{b + y_B}\)，你可以验证它等于 Alice 计算出的值：

\[(A \times X^\alpha)^{b + y_B} = \left(g^a \times (g^x)^\alpha\right)^{b + y_B} = \left(g^{a + \alpha x}\right)^{b + y_B} = g^{(a + \alpha x)(b + y_B)} = g^{(b + y_B)(a + \alpha x)}\]

Alice 和 Bob 得到相同的值 \(g^{(b + \beta y)(a + x_A)}\)，这表明 Alice 和 Bob 共享同一个秘密。

与认证 DH 不同，仅仅泄露临时秘密并不能攻破 MQV。攻击者即使知道 *a* 或 *b*，也无法确定最终的共享秘密，因为计算它还需要长期私钥。

在最强的攻击模型（破坏模型）中，当长期密钥被攻破时会发生什么？如果 Eve 攻破了 Alice 的长期私钥 *x*，先前建立的共享秘密仍然是安全的，因为它们的计算还涉及 Alice 的临时私钥。

然而，MQV 并不提供*完美前向保密*，原因如下攻击。例如，假设 Eve 截获 Alice 的 *A* 消息，并将其替换为她自己选择的某个 *a* 对应的 *A = g^a*。与此同时，Bob 将 *B* 发送给 Alice（Eve 记录下 *B* 的值），并计算出共享密钥。如果 Eve 后来攻破了 Alice 的长期私钥 *x*，她就能确定 Bob 在该会话中计算出的密钥。这就破坏了前向保密性，因为 Eve 现在恢复了之前某次协议执行的共享秘密。不过在实践中，你可以通过密钥确认步骤来消除这一风险：Alice 和 Bob 会意识到他们没有共享相同的密钥，并在派生任何会话密钥之前中止协议。

尽管 MQV 优雅且安全，但在实践中却很少使用，原因有几个。它曾受专利限制，阻碍了其广泛采用。此外，正确实现 MQV 比看上去更难。事实上，与其增加的复杂性相比，MQV 的安全优势相对于更简单的认证 DH 而言往往被认为很低。

## 可能出错的地方

Diffie–Hellman 协议可能以多种方式严重失效。以下各节重点介绍一些实践中常见的情况。

## 不对共享秘密进行哈希

我曾提到，在我们的示例中，DH 会话交换结束时得到的共享秘密 \((g^{ab})\) 被用作派生会话密钥的输入，但它本身并不是密钥。它也不应该是。对称密钥应该看起来是随机的，每一位为 0 或 1 的概率相同。但 $g^{ab}$ 并不是一个随机字符串；它是某个数学群中的一个随机元素，其位可能偏向 0 或 1。随机群元素与随机位字符串是不同的。

例如，假设你正在乘法群 $\mathbb{Z}_{13}^{*} = \{1, 2, 3, . . . , 12\}$ 中工作，以 $g = 2$ 作为群的生成元，也就是说，当 $i$ 取 1, 2, . . . 12 时，$g^i$ 遍历 $\mathbb{Z}_{13}^{*}$ 的所有值：$g^1 = 2$, $g^2 = 4$, $g^3 = 8$, $g^4 = 3$，依此类推。如果 $g$ 的指数是随机的，你会得到 $\mathbb{Z}_{13}^{*}$ 中的一个随机元素，但将一个 $\mathbb{Z}_{13}^{*}$ 元素编码为 4 位字符串并不会是均匀随机的：并非所有位为 0 或 1 的概率都相同。在 $\mathbb{Z}_{13}^{*}$ 中，有 7 个值的最高有效位为 0（群中的数字 1 到 7），但只有 5 个值的最高有效位为 1（8 到 12）。也就是说，这一位为 0 的概率是 7/12 ≈ 0.58，而理想的随机位为 0 的概率应为 0.5。此外，4 位序列 1101、1110 和 1111 永远不会出现。

为了避免从 DH 共享秘密派生的会话密钥出现这种偏差，应使用加密哈希函数（如 BLAKE3 或 SHA-3），或者更好的做法是使用密钥派生函数（KDF）。KDF 构造的一个例子是 HKDF，即基于 HMAC 的 KDF（如 RFC 5869 所规定），而如今 BLAKE2 和 SHA-3 也提供了专门的模式来充当 KDF。

## TLS 1.0 中的匿名 Diffie–Hellman

TLS 协议是 HTTPS 安全网站以及许多其他协议（例如使用简单邮件传输协议（SMTP）传输电子邮件）背后的安全机制。TLS 接受多个参数，包括它将使用的 Diffie–Hellman 协议类型。出于向后兼容的原因，TLS 从 1.0 版到 1.2 版一直支持匿名 DH（即不进行任何服务器身份验证），但在 1.3 版中不支持。由于 DH 仅对被动攻击者安全，它可能会给人一种虚假的安全感。

TLS 的原始文档描述了该协议的风险（[https://www.rfc-editor.org/rfc/rfc2246](https://www.rfc-editor.org/rfc/rfc2246)）：

> 完全匿名的连接只能提供针对被动窃听的保护。除非使用独立的防篡改通道来验证 Finished 消息未被攻击者替换，否则在需要考虑主动中间人攻击的环境中，必须进行服务器身份验证。

## 不安全的群参数

2016 年 1 月，OpenSSL 工具包的维护者修复了一个高危漏洞（CVE-2016-0701），该漏洞允许攻击者利用不安全的 Diffie–Hellman 参数。此漏洞的根本原因是 OpenSSL 允许用户使用不安全的 DH 群参数（即不安全的素数 p），而不是抛出错误并在执行任何算术运算之前完全中止协议。

本质上，OpenSSL 接受了一个素数 p，其乘法群 $\mathbb{Z}_p^*$（所有 DH 操作都在其中进行）包含小子群。正如你在本章开头所学到的，在加密协议中，较大群内存在小子群是不好的，因为与使用整个群 $\mathbb{Z}_p^*$ 相比，它会将共享秘密限制在一个小得多的可能值集合中。更糟糕的是，攻击者可以构造一个 DH 指数 x，当它与受害者的公钥 g^y 结合时，会泄露关于私钥 y 的信息，并最终泄露其全部内容。

尽管实际漏洞出现在 2016 年，但该攻击所利用的原理可以追溯到 1997 年 Chae Hoon Lim 和 Pil Joong Lee 发表的论文《A Key Recovery Attack on Discrete Log-based Schemes Using a Prime Order Subgroup》。修复该漏洞的方法很简单：在接受素数 p 作为群模数时，协议必须同时验证 p 是一个安全素数，即验证 (p − 1) / 2 也是素数，以确保群 $\mathbb{Z}_p^*$ 不包含小子群，从而使针对该漏洞的攻击失败。

## 进一步阅读

你可以通过阅读一些标准和官方出版物来更深入地了解 DH 密钥协商协议，包括 ANSI X9.42、RFC 2631、RFC 5114、IEEE 1363 和 NIST SP 800-56A。这些文献可作为参考，以确保互操作性并为群参数提供建议。

要了解更多关于高级 DH 协议（如 MQV 及其近亲 HMQV 和 OAKE 等）及其安全概念（包括未知密钥共享攻击和群表示攻击），请阅读 Hugo Krawczyk 于 2005 年发表的论文《HMQV: A High-Performance Secure Diffie–Hellman Protocol》（https://eprint.iacr.org/2005/176）以及 Andrew C. Yao 和 Yunlei Zhao 于 2011 年发表的论文《A New Family of Implicitly Authenticated Diffie–Hellman Protocols》（https://eprint.iacr.org/2011/035）。这些论文对 Diffie–Hellman 运算的表述方式与本章不同。例如，它们将共享秘密表示为 xP 而不是 g^x。通常，你会发现乘法被加法取代，幂运算被乘法取代，因为这些协议通常不是定义在整数群上，而是定义在椭圆曲线上，正如你将在第 12 章中学习的那样。



例如，加密、签名和密钥协商，这些都比它们的经典对应方式更快。大多数依赖离散对数问题（DLP）的密码应用，在基于其椭圆曲线版本ECDLP时同样有效，但有一个显著例外：安全远程密码（SRP）协议。

本章重点讨论ECC的应用，说明何时以及为何应使用ECC而不是RSA或经典Diffie–Hellman，以及如何为你的应用选择合适的椭圆曲线。

### 什么是椭圆曲线？

椭圆曲线是平面上的一条*曲线*——一组具有x和y坐标的点。曲线的方程定义了属于该曲线的所有点。例如，曲线y = 3是纵向坐标为3的水平线，形如y = ax + b（其中a和b为固定数）的曲线是直线，x² + y² = 1是以原点为圆心、半径为1的圆，等等。无论曲线类型如何，曲线上的点都是满足曲线方程的(x, y)对。

在密码学中，椭圆曲线通常具有形如 y² = x³ + ax + b 的方程（*魏尔斯特拉斯形式*），其中常数a和b定义了曲线的形状。例如，图12-1展示了满足方程 y² = x³ − 4x 的椭圆曲线。

![](img/ace4de942d037de8ea5835bc9fbe57cd_259_0.png)

*图12-1：一条满足方程 y² = x³ − 4x 的椭圆曲线，在实数范围内的图像*

此图显示了构成曲线在x介于−3和4之间的所有点，无论是位于形似圆形的曲线左侧的点，还是位于形似抛物线的右侧的点。所有点都具有满足曲线方程 y² = x³ − 4x 的(x, y)坐标。例如，当x = 0时，y² = x³ − 4x = 0³ − 4 × 0 = 0，因此y = 0是一个解，点(0, 0)属于该曲线。同样，如果x = 2，方程的解为y = 0，这意味着点(2, 0)属于该曲线。

> **注意**
>
> *在本章中，我关注的是最简单、最常见的椭圆曲线类型——那些方程形如 y² = x³ + ax + b 的曲线——但其他椭圆曲线的方程具有不同的形式。例如，爱德华曲线具有形如 x² + y² = 1 + d x² y² 的方程。密码学家有时会使用爱德华曲线（例如，在Ed25519方案中）。*

在将椭圆曲线用于密码学时，区分属于曲线的点与其他点至关重要，因为曲线外的点通常会带来安全风险。然而，曲线方程并不总有解，至少在自然数平面内如此。例如，要找到横坐标为x = 1的点，需解方程 y² = x³ − 4x，得到 y² = x³ − 4x = 1³ − 4 × 1 = −3。但 y² = −3 无解，因为没有任何数的平方等于−3。在复数中存在解（√3i），但在实践中，椭圆曲线密码学只使用自然数（ECC使用模素数的整数，要么直接使用，要么通过多项式）。由于对于x = 1没有满足曲线方程的解，曲线上在该x轴位置没有点，正如图12-1所示。

如果你尝试解x = −1，会得到方程 y² = −1 + 4 = 3，它有两个解（y = √3 ≈ 1.73 和 y = −√3 ≈ −1.73），即3的平方根及其负值。这两个值的平方都是3，图12-1在x = −1处有两个点。更一般地说，对于所有满足其方程的点，曲线相对于x轴对称（所有形如 y² = x³ + ax + b 的椭圆曲线都如此，除了y = 0的情况）。

## 整数上的椭圆曲线

这里有点出乎意料：椭圆曲线密码学中的曲线实际上并不像图12-1那样。它们既不是曲线也不是椭圆。它们看起来反而如图12-2所示，是一片点的云团，而不是一条曲线。这是怎么回事呢？

![](img/ace4de942d037de8ea5835bc9fbe57cd_261_0.png)

*图12-2：方程 \(y^2 = x^3 - 4x\) 在 \(\mathbb{Z}_{191}\)（整数模191的集合）上的椭圆曲线*

图12-1和图12-2基于相同的曲线方程 \(y^2 = x^3 - 4x\)，但它们展示了曲线相对于不同数集上的点：图12-1展示了曲线在*实数*集上的点，包括负数、小数等。例如，作为连续曲线，它显示了 \(x = 2.0, x = 2.1, x = 2.00002\) 等位置的点。另一方面，图12-2只显示了*整数*中满足该方程的点，排除了小数。具体来说，图12-2显示的是关于整数*模191*的曲线 \(y^2 = x^3 - 4x\)：0、1、2、3，一直到190。你可以将这个数集记为 \(\mathbb{Z}_{191}\)。（这里191没什么特别之处，除了它是一个素数。我选择了一个较小的数字以避免图上有太多点。）因此，图12-2中的点都有整数模191的x和y坐标，并且满足方程 \(y^2 = x^3 - 4x\)。例如，对于 \(x = 2\)，有 \(y^2 = 0\)，其中 \(y = 0\) 是一个有效解。这说明点 \((2, 0)\) 属于该曲线。

如果 \(x = 3\)，得到方程 \(y^2 = 27 - 12 = 15\)，它在 \(\mathbb{Z}_{191}\) 中有两个解：46和145。事实上，\(46^2 = 2,116\)，且 \(2,116 \bmod 191 = 15\)，\(145^2 = 21,025\)，且 \(21,025 \bmod 191 = 15\)。因此，点 \((3, 46)\) 和 \((3, 145)\) 都属于该曲线，并在图12-2中出现（左侧圈出的两个点）。

> **注意**
>
> 图12-2考虑的是数集 \(\mathbb{Z}_{191} = \{0, 1, 2, \ldots, 190\}\) 中的点，该集合包含零。这与我们在RSA和Diffie–Hellman中讨论的 \(\mathbb{Z}_p^*\)（带星号上标）群不同。这种差异的原因在于，你需要同时进行乘法和加法运算，因此需要确保数集包含加法的单位元（即0，使得对于所有 \(x \in \mathbb{Z}_{191}\) 都有 \(x + 0 = x\)）。
>
> 此外，每个数 \(x\) 都有关于加法的逆元，记为 \(-x\)，使得 \(x + (-x) = 0\)。例如，在 \(\mathbb{Z}_{191}\) 中，100的逆元是91，因为 \(100 + 91 \mod 191 = 0\)。这样的数集，其中可以进行加法和乘法，每个元素 \(x\) 既有关于加法的逆元（记为 \(-x\)），也有关于乘法的逆元（除零元素外，记为 \(1/x\)），被称为域。当一个域包含有限个元素时，例如 \(\mathbb{Z}_{191}\) 以及所有用于椭圆曲线密码学的域，它就是一个有限域。

## 加法规则

现在你知道了椭圆曲线上的点是满足曲线方程 \(y^2 = x^3 + ax + b\) 的坐标 \((x, y)\)，接下来我们看看如何用加法规则对椭圆曲线上的点进行加法运算。

### 两个点的加法

假设你想要将椭圆曲线上的两个点 \(P\) 和 \(Q\) 相加，得到一个新点 \(R\)，即这两个点的和。理解点加法的最简单方式是依据几何规则确定 \(R = P + Q\) 在曲线上相对于 \(P\) 和 \(Q\) 的位置：画一条连接 \(P\) 和 \(Q\) 的直线，找到该直线与曲线的另一个交点，然后 \(R\) 是这个交点关于x轴的反射点。例如，在图12-3中，连接 \(P\) 和 \(Q\) 的直线在 \(P\) 和 \(Q\) 之间与曲线第三次相交，点 \(P + Q\) 位于相同的x坐标处，但y坐标取相反数。

![](img/ace4de942d037de8ea5835bc9fbe57cd_263_0.png)

*图12-3：椭圆曲线上点相加的几何规则的一般情形*

这个几何规则很简单，但它不会直接给出点R的坐标。你需要使用P的坐标(x_P, y_P)和Q的坐标(x_Q, y_Q)来计算R的坐标(x_R, y_R)，公式为 x_R = m² − x_P − x_Q 和 y_R = m(x_P − x_R) − y_P，其中 m = (y_Q − y_P) / (x_Q − x_P) 是连接P和Q的直线的斜率。

遗憾的是，这些公式和图12-3中的画线技巧并不总是有效。例如，如果P = Q，你无法在两个点之间画一条直线（因为只有一个点）；而如果Q = −P，直线不会再次与曲线相交，因此没有曲线上的点可供镜像。我们将在下一节中探讨这些情况。

### 点与其负元的加法

点P = (x_P, y_P)的负元是点 −P = (x_P, −y_P)，即绕x轴镜像的点。对于任意P，可以说 P + (−P) = O，其中O是无穷远点。如图12-4所示，P和−P之间的直线延伸至无穷远，且永远不会与曲线相交。无穷远点之于椭圆曲线，就像零之于整数一样，只不过它是一个“虚拟”点，无法定位于具体位置，因为它无限遥远。




![](img/ace4de942d037de8ea5835bc9fbe57cd_264_0.png)

图 12-4：当两点之间的连线不与曲线相交时，点与其负元相加的几何规则，即 P + (-P) = O

## 点的倍加

当 P = Q（即 P 和 Q 在同一位置）时，P 加 Q 等价于计算 P + P，即 2P。这一加法运算称为*倍加*。

要求结果 R = 2P 的坐标，不能使用上一节的几何规则，因为无法在 P 和它自身之间画一条直线。相反，应画一条*切线*经过曲线上的点 P，而 2P 是该切线与曲线交点关于 x 轴的对称点，如图 12-5 所示。

![](img/ace4de942d037de8ea5835bc9fbe57cd_265_0.png)

*图 12-5：点的倍加（即 P + P）的几何规则*

确定 \(R = P + P\) 的坐标 \((x_R, y_R)\) 的公式与 P 和 Q 不同时的公式略有不同。基本公式为 \(x_R = m^2 - x_P - x_Q\) 和 \(y_R = m(x_P - x_R) - y_P\)，但 m 的值变为 \((3x_P^2 + a)/2y_P\)，其中 a 是曲线参数，正如 \(y^2 = x^3 + ax + b\) 中的 a。

## 点的数乘

要通过给定整数 \(k\) 与椭圆曲线上的点相乘，你需要将 \(P\) 与自身相加 \(k - 1\) 次来确定点 \(kP\)。换句话说，\(2P = P + P\)，\(3P = P + P + P\)，依此类推。要获得 \(kP\) 的 x 和 y 坐标，可反复将 \(P\) 加到自身并应用前面的加法法则。

然而，若想高效计算 \(kP\)，直接应用加法法则将 \(P\) 相加 \(k - 1\) 次这一朴素方法远非最优。例如，如果 k 很大（比如达到 \(2^{256}\) 的量级），正如椭圆曲线加密方案中出现的那样，那么计算 \(k - 1\) 次加法是完全不可行的。

你可以通过改编第 10 章“快速幂算法”中的技术来计算 \(x^e\) mod \(n\)，从而获得指数级加速。区别在于这里是用整数乘点，而不是计算指数。但你可以将该方法改编为*倍加*算法，其中乘法变为加法，平方变为倍加。

例如，用三个加法而不是朴素方法所需的七个加法来计算 \(8P\)：先计算 \(P_2 = P + P\)，再计算 \(P_4 = P_2 + P_2\)，最后计算 \(P_4 + P_4 = 8P\)。这是最简单的情况，即当乘数是 2 的幂时。

在代码清单 12-1 中，你首先将变量 Z 定义为整数模 191 的集合；然后将变量 E 定义为 Z 上系数为 −4 和 0 的椭圆曲线。最后计算曲线上的点数，即其*基数*、*群阶*，或简称为*阶*。该计数包含无穷远点 O。

## ECDLP 问题

第 9 章介绍了离散对数问题（DLP）：对于某个大素数 p，给定底数 g，已知 x = g^y mod p，求数字 y。椭圆曲线密码学有一个类似的问题：给定基点 P，其中点 Q = kP，求数字 k。这就是椭圆曲线离散对数问题。与数字问题不同，椭圆曲线上的问题针对点运算，使用乘法而不是幂运算。

几乎所有椭圆曲线密码学都建立在 ECDLP 问题上。与 DLP 一样，该问题被认为是困难的，并且自 1985 年提出以来一直经受住了密码分析的考验。与经典 DLP 的一个重要区别是，ECDLP 允许使用较小的数字，同时仍能享受相当的安全级别。

通常，当参数 p 为 n 位时，ECC 可获得约 n/2 位的安全级别。例如，基于模 256 位 p 的椭圆曲线可提供约 128 位的安全级别。作为比较，若要通过 DLP 或 RSA 达到相近的安全级别，需要使用数千位的数字。ECC 运算使用较小的数字，是它往往比 RSA 或经典 Diffie–Hellman 更快的原因之一。

求解 ECDLP 的一种方法是寻找两个输出 \(c_1P + d_1Q\) 和 \(c_2P + d_2Q\) 之间的碰撞。这些方程中的点 P 和 Q 满足对于某个未知的 k 有 Q = kP，而 c₁、d₁、c₂、d₂ 是你需要求出的数字，最终得到 k。

与第 6 章的哈希函数一样，当两个不同的输入产生相同的输出时，碰撞就发生了。因此，要解决 ECDLP，你需要找到满足以下条件的点：

$$c_1P + d_1Q = c_2P + d_2Q$$

假设你已经找到了这四个系数，那么就可以恢复 k。为此，将 Q 替换为 kP 的值，得到：

$$c_1P + d_1kP = (c_1 + d_1k)P = c_2P + d_2kP = (c_2 + d_2k)P$$

这告诉你，(c₁ + d₁k) 与 (c₂ + d₂k) 在对曲线上的点数取模时相等，而该点数并非秘密。

由此可以推导出以下内容：

d₂k - d₁k = c₁ - c₂
k(d₂ - d₁) = c₁ - c₂
k = (c₁ - c₂) / (d₂ - d₁)

这样你就找到了 k，即 ECDLP 的解。当然，这只是大致的思路——具体细节更为复杂且有趣，尤其是在恢复系数 c₁、c₂、d₁、d₂ 的方法上。

在实践中，椭圆曲线涉及的数至少为 256 位，这使得通过寻找碰撞来攻击椭圆曲线密码学不切实际，因为这样做最多需要 2¹²⁸ 次运算（在 256 位数上寻找碰撞的代价——见第 6 章）。

## 椭圆曲线上的 Diffie–Hellman 密钥协商

回顾第 11 章，在经典 Diffie–Hellman（DH）密钥协商协议中，双方通过交换非秘密值来建立共享秘密。给定某个固定数 g，Alice 选择一个秘密随机数 a，计算 A = gᵃ，并将 A 发送给 Bob。然后 Bob 选择一个秘密随机数 b，并将 B = gᵇ 发送给 Alice。双方都将自己的秘密密钥与对方的公钥结合，产生相同的 Aᵇ = Bᵃ = gᵃᵇ。

椭圆曲线版本的 DH，即椭圆曲线 Diffie–Hellman（ECDH），与经典 DH 相同，只是符号不同。在 ECC 中，对于某个固定点 G，Alice 选择一个秘密随机数 a，计算 A = aG（点 G 乘以整数 a），并将 A 发送给 Bob。Bob 选择一个秘密随机数 b，计算点 B = bG，并将其发送给 Alice。然后双方计算出相同的共享秘密 aB = bA = abG。

ECDH 与 ECDLP 问题的关系，正如 DH 与 DLP 的关系：只要 ECDLP 是困难的，ECDH 就是安全的。因此，你可以将依赖 DLP 的 DH 协议改造为适用于椭圆曲线，并将 ECDLP 作为困难性假设。例如，认证 DH 和 Menezes–Qu–Vanstone（MQV）在用于椭圆曲线时也是安全的。事实上，MQV 最初就是定义在椭圆曲线上的。

## 使用椭圆曲线签名

使用 ECC 进行签名的主要标准算法是椭圆曲线数字签名算法（ECDSA）。该算法已在许多应用中取代了 RSA 签名和经典 DSA 签名。ECDSA 是 NIST 标准，受 TLS 和 SSH 协议支持，并且是许多区块链平台（包括比特币和以太坊）的主要签名算法。

与所有签名方案一样，ECDSA 由两部分组成：签名者使用其私钥创建签名的签名生成算法，以及验证者使用签名者公钥检查签名正确性的验证算法。签名者持有一个数字 d 作为私有

这告诉你，(u + vd) 等于签名生成期间选择的值 k，并且 uG + vdG 等于点 kG。换句话说，验证算法成功计算出了点 kG，即签名生成期间计算出的同一个点。一旦验证者确认 kG 的 x 坐标等于收到的 r，验证即完成；否则，签名将被视为无效而被拒绝。

## ECDSA 与 RSA 签名对比

虽然一些人将椭圆曲线密码学视为公钥密码学中 RSA 的替代方案，但 ECC 和 RSA 并没有太多共同之处。RSA 仅用于加密和签名，而 ECC 是一族算法，可用于执行加密、生成签名、进行密钥协商，并提供高级密码学功能，如基于身份的加密（一种使用由个人标识符（如电子邮件地址）派生的加密密钥的加密方式）。

在比较 ECDSA 与 RSA 签名时，回想一下在 RSA 签名中，签名者使用其私钥 d 计算签名 y = x^d mod n，其中 x 是要签名的数据，y 是签名。验证使用公钥 e 确认 y^e mod n 等于 x——这一过程显然比 ECDSA 简单。

RSA 的验证过程通常比 ECC 的签名验证更快，因为它使用较小的公钥 e。因此，验证 RSA 签名仅需一次幂运算 y^65,537 mod n。

与 RSA 相比，ECC 有两个主要优势：更短的签名和更快的签名速度。由于 ECC 使用更短的数字，它产生的签名比 RSA 更短（数百位而非数千位），如果需要存储或传输大量签名，这显然是一个好处。使用 ECDSA 签名也比 RSA 快，因为 ECDSA 在远小于 RSA 的数字上进行运算，计算成本更低。例如，代码清单 12-2 显示，ECDSA 的签名速度约为 RSA 的 200 倍，验证速度与 RSA 大致相当（基准测试基于 Apple M2 处理器）。注意，在这个例子中，ECDSA 签名也比 RSA 签名更短，因为它们是 512 位（两个 256 位元素），而不是 4,096 位。

```text
$ openssl speed ecdsap256 rsa4096
                             sign     verify    sign/s    verify/s
rsa 4096 bits              0.003297s 0.000048s     303.3    20933.4
                             sign     verify    sign/s    verify/s
256 bit ecdsa (nistp256)   0.0000s   0.0000s    63709.1    20979.8
```

*代码清单 12-2：比较 4,096 位 RSA 签名与 256 位 ECDSA 签名的速度*

比较这些不同大小的签名的性能是合理的，因为它们提供相近的安全级别。然而，在实践中，许多系统使用 2,048 位的 RSA 签名，其安全性比 256 位 ECDSA 低若干数量级。得益于其较小的模数大小，


2,048 位 RSA 在验证时比 256 位 ECDSA 更快，但在签名时仍然更慢，如清单 12-3 所示。

```
$ openssl speed rsa2048
          sign    verify   sign/s   verify/s
rsa 2048 bits   0.000520s 0.000013s 1923.7   77221.1
```

*清单 12-3：2,048 位 RSA 签名的速度*

除非签名验证至关重要且你不在乎签名速度，例如在一次签名、多次验证的情况下（如 Windows 可执行应用程序一次签名后由所有执行它的系统进行验证），否则应优先选择 ECDSA 而非 RSA。

## EdDSA 与 Ed25519

ECDSA 于 1990 年代初被引入，作为 NSA 的数字签名标准 DSA 的椭圆曲线版本，该标准于 1991 年由 NIST 标准化。但在 1989 年，密码学家 Claus-Peter Schnorr 提出了所谓的 Schnorr 签名方案，一种比 (EC)DSA 更简单、更高效的算法，也适用于椭圆曲线。然而，Schnorr 申请了专利限制其签名方案的使用，阻止了广泛采用和标准化。

在 Schnorr 的专利于 2008 年到期后，密码学家 Daniel J. Bernstein、Niels Duif、Tanja Lange、Peter Schwabe 和 Bo-Yin Yang 在 Schnorr 的思想之上构建，创建了 Edwards 曲线 DSA (EdDSA)，一种仅适用于椭圆曲线的签名，具有以下优点：

- 比 ECDSA 更简单
- 比 ECDSA 更快，签名和验证皆然
- 确定性的（而 ECDSA 和 Schnorr 签名在签名时使用随机数），消除了与有缺陷的随机性相关的风险

让我们看看通用 EdDSA 如何工作，以及使其特定实例 Ed25519 如此有吸引力的原因。为了保持简单，我将提供这些方案的简化概述。有关这些方案的完整细节和原理，请参阅 2011 年论文 “High-Speed High-Security Signatures” 和 RFC 8032，“Edwards-Curve Digital Signature Algorithm (EdDSA)。“

请注意，我使用的符号与原文中的类似，可能与本书之前使用的符号不同。

## EdDSA 签名

像任何签名方案一样，使用 EdDSA 签名需要私钥和消息，但与 ECDSA 不同，私钥是随机字节串而不是随机（标量）数。你通过对私钥串进行哈希来派生实际的私钥标量。这有几个安全优势，包括使应用程序更容易通过从 PRNG 中转储原始字节来选择随机密钥，而无需确保密钥具有正确的格式且不弱。它还有助于从密钥和消息高效地派生 nonce，这取代了 ECDSA 中每签名一次的随机值的使用。

签名然后按如下方式进行，从 256 位私钥 k 和任意大小的消息 M，以及给定基点 B：

- 1. 计算 a || h = Hash(k)，对于产生 512 位值的哈希函数，其中前 256 位构成私钥标量 a，后 256 位构成字符串 h。
- 2. 将公钥定义为 A = aB（实际上这是预先计算的）。
- 3. 计算消息的“预哈希” r = Hash(h || M) 并计算椭圆曲线点 R = rB，这是签名的第一部分，签名点。
- 4. 计算数字 S = r + Hash(R, A, M) × a，签名的第二部分。

返回的签名是[content]
2,048 位 RSA 在验证时比 256 位 ECDSA 更快，但在签名时仍然更慢，如清单 12-3 所示。

```
$ openssl speed rsa2048
          sign    verify   sign/s   verify/s
rsa 2048 bits   0.000520s 0.000013s 1923.7   77221.1
```

*清单 12-3：2,048 位 RSA 签名的速度*

除非签名验证至关重要且你不在乎签名速度，例如在一次签名、多次验证的情况下（如 Windows 可执行应用程序一次签名后由所有执行它的系统进行验证），否则应优先选择 ECDSA 而非 RSA。

## EdDSA 与 Ed25519

ECDSA 于 1990 年代初被引入，作为 NSA 的数字签名标准 DSA 的椭圆曲线版本，该标准于 1991 年由 NIST 标准化。但在 1989 年，密码学家 Claus-Peter Schnorr 提出了所谓的 Schnorr 签名方案，一种比 (EC)DSA 更简单、更高效的算法，也适用于椭圆曲线。然而，Schnorr 申请了专利限制其签名方案的使用，阻止了广泛采用和标准化。

在 Schnorr 的专利于 2008 年到期后，密码学家 Daniel J. Bernstein、Niels Duif、Tanja Lange、Peter Schwabe 和 Bo-Yin Yang 在 Schnorr 的思想之上构建，创建了 Edwards 曲线 DSA (EdDSA)，一种仅适用于椭圆曲线的签名，具有以下优点：

- 比 ECDSA 更简单
- 比 ECDSA 更快，签名和验证皆然
- 确定性的（而 ECDSA 和 Schnorr 签名在签名时使用随机数），消除了与有缺陷的随机性相关的风险

让我们看看通用 EdDSA 如何工作，以及使其特定实例 Ed25519 如此有吸引力的原因。为了保持简单，我将提供这些方案的简化概述。有关这些方案的完整细节和原理，请参阅 2011 年论文 “High-Speed High-Security Signatures” 和 RFC 8032，“Edwards-Curve Digital Signature Algorithm (EdDSA)。“

请注意，我使用的符号与原文中的类似，可能与本书之前使用的符号不同。

## EdDSA 签名

像任何签名方案一样，使用 EdDSA 签名需要私钥和消息，但与 ECDSA 不同，私钥是随机字节串而不是随机（标量）数。你通过对私钥串进行哈希来派生实际的私钥标量。这有几个安全优势，包括使应用程序更容易通过从 PRNG 中转储原始字节来选择随机密钥，而无需确保密钥具有正确的格式且不弱。它还有助于从密钥和消息高效地派生 nonce，这取代了 ECDSA 中每签名一次的随机值的使用。

签名然后按如下方式进行，从 256 位私钥 k 和任意大小的消息 M，以及给定基点 B：

- 1. 计算 a || h = Hash(k)，对于产生 512 位值的哈希函数，其中前 256 位构成私钥标量 a，后 256 位构成字符串 h。
- 2. 将公钥定义为 A = aB（实际上这是预先计算的）。
- 3. 计算消息的“预哈希” r = Hash(h || M) 并计算椭圆曲线点 R = rB，这是签名的第一部分，签名点。
- 4. 计算数字 S = r + Hash(R, A, M) × a，签名的第二部分。

返回的签名是配对 (R, S)。

计算瓶颈因此是标量-点乘法 rB，对于固定的基点 B。当消息很长时，对消息进行两次哈希的成本也可能很显著。然而，与 ECDSA 不同，你不需要计算模逆。

在实践中，你可以优化实现——例如，避免为每次签名重新计算公钥。你还必须将值设置为正确的类型（如受模约减的数字）并以可靠且无歧义的格式对其进行编码（如曲线点）。

## EdDSA 验证

给定签名 (R, S)、消息 M、公钥 A 和基点 B，验证包括检查 SB 是否等于 R + Hash(R, A, M)A。请注意 SB = S × B。

如果你用第 4 步求值的表达式替换 S，则 SB 等于以下值：

(r + Hash(R, A, M) × a) × B = rB + Hash(R, A, M) × aB

在此表达式中，你知道 rB = R 且 aB = A。你因此得到预期结果 R + Hash(R, A, M) × A。

与 ECDSA 相比，你避免了模逆的计算。与 ECDSA 一样，你需要两次标量-点乘法（SB 和 Hash(R, A, M)A）。

## Ed25519

Ed25519 是 EdDSA 的一个特定实例，具有以下参数：

- 基于 Curve25519 的 *扭曲 Edwards 曲线*，你将在下一节看到
- SHA-512 作为哈希函数
- 选择以优化效率的基点 B

截至 2023 年，Ed25519 很可能由于其性能优势和高安全保证而成为第二受欢迎的椭圆曲线签名算法（参见 https://ed25519.cr.yp.to）。

OpenSSH、Apple 产品和许多区块链平台都使用 Ed25519 来签署交易。2023 年 2 月，Ed25519 作为 NIST 标准的一部分被添加，作为 FIPS 186-5，“Digital Signature Standard。”

Ed25519 存在一些互操作性问题，如本章后面将看到的那样。

## 使用椭圆曲线加密

虽然你通常会使用椭圆曲线进行签名，但也可以用它们进行加密。但在实践中你很少会看到人们这样做，因为可加密的明文大小受到限制：你只能容纳约 100 位明文，而在相同安全级别下 RSA 几乎可达 4,000 位。

你可以使用 *椭圆曲线集成加密方案 (ECIES)* 用椭圆曲线进行加密，这是一种结合非对称和对称密码学的 *混合* 方案。它使用 Diffie–Hellman 操作来派生共享密钥，该密钥使用经过身份验证的密码保护数据。

给定接收者的公钥 *P*，ECIES 加密消息 *M*，如下所示：

- 1. 选择一个随机数 *d*，并计算点 *Q = dG*，其中基点 *G* 是固定参数。这里，*(d, Q)* 充当一次性密钥对，仅用于加密 *M*。
- 2. 通过计算 *S = dP* 计算 ECDH 共享密钥。
- 3. 使用密钥派生函数 (KDF) 从 *S* 派生对称密钥 *K*。
- 4. 使用 *K* 和对称经过身份验证的密码加密 *M*，得到密文 *C* 和身份验证标签 *T*。

ECIES 密文然后由一次性公钥 *Q* 后跟 *C* 和 *T* 组成。解密很简单：接收者通过将其私钥指数乘以 *Q* 计算 *S*，然后派生密钥 *K*，解密 *C* 并验证 *T*。

## 选择曲线

评估椭圆曲线安全性标准包括你使用的群的阶（即其点数）、其加法公式以及其参数的来源。

有几种类型的椭圆曲线，但并非所有在密码学目的上都相等。仔细选择曲线方程 *y² = x³ + ax + b* 中的系数 *a* 和 *b*，根据既定的安全标准；否则，你可能会得到不安全的曲线。在实践中，你将使用已建立的曲线进行加密，但了解什么使曲线安全将帮助你在多个可用曲线中进行选择并更好地理解任何相关风险。以下是一些需要牢记的要点：

- 群的阶不应是小数的乘积；否则，求解 ECDLP 会变得容易得多。
- 在第 235 页的“加法律”中，你了解到当 Q = P 时，加点 $P + Q$ 需要特定的加法公式。不幸的是，如果攻击者能够区分倍点与不同点之间的加法，则将此情况与一般情况不同对待可能会泄露关键信息。一些曲线是安全的，因为它们对所有点加法使用单一公式。（当曲线不需要对倍点使用特定公式时，它允许 *统一加法律*。）
- 如果曲线的创建者不解释 $a$ 和 $b$ 的来源，他们可能会被怀疑有不当行为，因为你无法知道他们是否选择了较弱的值，从而使密码系统受到某种尚未知的攻击。

让我们回顾一些最常见的曲线，特别是用于签名或 Diffie–Hellman 密钥协商的曲线。

> **注意** 您可以在 https://safecurves.cryp.to 上找到有关曲线的更多标准和细节。

## NIST 曲线

2000 年，NIST 在 FIPS 186 文件中根据“联邦政府使用的推荐椭圆曲线”标准化了几条曲线。五条 NIST 曲线称为 *素数曲线*，在素数模下工作（参见第 233 页的“整数上的椭圆曲线”）。另外十条 NIST 曲线使用二进制多项式，这些数学对象使硬件中的实现更高效。（我不会进一步介绍二进制多项式，因为它们很少与椭圆曲线一起使用。）

最常见的 NIST 曲线是素数曲线。其中最常见的一个是 P-256，这是一条在 256 位数 $p = 2^{256} - 2^{224} + 2^{192} + 2^{96} - 1$ 模下工作的曲线。P-256 的方程为 $y^2 = x^3 - 3x + b$，其中 $b$ 是 256 位数。NIST 还提供 192 位、224 位、384 位和 521 位的素数曲线（这不是笔误；它是 521，而不是 512）。

NIST 曲线有时受到批评，因为只有曲线创建者 NSA 知道其方程中 $b$ 系数的来源。他们提供的解释是，$b$ 是通过用 SHA-1 对一个看起来随机的常数进行哈希得到的。例如，P-256 的 $b$ 参数来自以下常数：`c49d3608 86e70493 6a6678e1 139d26b7 819f7e90`。没有人知道 NSA 为什么选择这个特定常数，但大多数专家不相信曲线的起源隐藏着任何弱点。



## Curve25519

Daniel J. Bernstein 于 2006 年向世界推出了 Curve25519（通常读作 *curve-twenty-five-five-nineteen*）。出于性能考虑，他设计 Curve25519 使其比标准曲线更快且使用更短的密钥。但 Curve25519 也带来了安全优势；与 NIST 曲线不同，它没有可疑的常数，并且可以使用相同的统一公式来添加不同的点或对点进行加倍。

Curve25519 方程的形式 $y^2 = x^3 + 486662x^2 + x$ 与本章中的其他方程略有不同，但它仍然属于椭圆曲线家族。这种方程的特殊形式允许特定的实现技术，使 Curve25519 在软件中运行快速。

Curve25519 使用模 $2^{255} - 19$ 的数，这是一个质数，尽可能接近 $2^{255}$。$b$ 系数 486662 是满足 Bernstein 设定的安全标准的最小编号。综合这些特性，Curve25519 比 NIST 曲线及其可疑系数更值得信赖。

Curve25519 无处不在——例如在 WhatsApp、TLS 1.3、OpenSSH 以及许多其他系统中。基于这一成功，Curve25519 于 2023 年 2 月被添加到 NIST 批准曲线列表中，作为文件 SP 800-186《离散对数密码学建议：椭圆曲线域参数》的一部分。

> **注意**
> 
> 有关 Curve25519 的细节和原理，请查看 Daniel J. Bernstein 于 2016 年的演讲“The First 10 Years of Curve25519”，网址为 https://cr.yp.to/talks.html#2016.03.09。

## Other Curves

撰写本文时，大多数密码学应用使用 NIST 曲线或 Curve25519（包括通过 Ed25519），但仍在使用其他旧标准，并且在标准化委员会中正在推广和推动新曲线。旧的国家标准包括法国的 ANSSI 曲线和德国的 Brainpool 曲线：这两个家族不支持完整的加法公式，并且使用来源不明的常数。

一些更新的曲线比旧曲线更高效且没有任何可疑之处；它们提供不同的安全级别和各种效率优化。示例包括 Curve41417，是 Curve25519 的变体，使用更大的数字并提供更高级别的安全性（大约 200 位）；Ed448-Goldilocks，一条 448 位曲线，首次于 2014 年提出并在 RFC 8032 中指定；以及 Diego Aranha 等人在“A Note on High-Security General-Purpose Elliptic Curves”中提出的六条曲线（参见 https://eprint.iacr.org/2013/647），尽管这些曲线很少使用。这些曲线的具体细节超出了本书的范围。

最后，Ristretto 计划（https://ristretto.group）是一种从非素数阶（因此具有子群）的椭圆曲线构造素数阶点群的技术。Ristretto 提供了在椭圆曲线上表示点的安全且无歧义的方法，消除了与 Curve25519 结构相关的风险，例如。

## How Things Can Go Wrong

椭圆曲线的缺点是其相对复杂性。与 RSA 或经典 Diffie–Hellman 相比，参数更多，导致攻击面更大，设计错误和实现漏洞的可能性更多。ECC 实现也可能容易受到侧信道攻击，尤其是其大数运算——例如当计算时间取决于秘密值时。

在以下章节中，我讨论了即使实现是安全的，椭圆曲线仍可能出现的三种漏洞示例。

### ECDSA with Bad Randomness

ECDSA 签名是随机的，因为在设置 s = (h + rd) / k mod n 时涉及秘密随机数 k。然而，如果你重复使用相同的 k 来签署第二条消息，攻击者可以组合 resulting values，s₁ = (h₁ + rd) / k 和 s₂ = (h₂ + rd) / k，得到 s₁ − s₂ = (h₁ − h₂) / k，然后 k = (h₁ − h₂) / (s₁ − s₂)。当你知道 k 时，可以通过以下计算轻松恢复私钥 d：

(k s₁ − h₁) / r = ((h₁ + r d) − h₁) / r = r d / r = d

与 RSA 签名不同，即使使用弱 PRNG 也不会导致密钥被恢复，非随机数的使用可能导致 ECDSA 的 k 可被恢复，正如 2010 年对 PlayStation 3 游戏机的攻击中所发生的那样，该攻击由 fail0verflow 团队在德国柏林举行的第 27 届 chaos Communication Congress 上展示。他们发现相同的 k 被重复用于签署不同的游戏，然后能够找到签名密钥，从而可以签署任何程序以授权其在主机上运行。

### Invalid Curve Attacks

如果输入点未得到正确验证，你可以优雅地破坏 ECDH。其主要原因是给出点之和 P + Q 坐标的公式永远不涉及曲线的 b 系数；相反，它们仅依赖于 P 和 Q 的坐标以及 a 系数（在加倍点时）。不幸的后果是，在添加两个点时，你无法确定自己是否在正确的曲线上工作，因为你实际上可能在具有不同 b 系数的不同曲线上添加点。这意味着你可以破坏 ECDH，正如以下场景、无效曲线攻击所述。

假设 Alice 和 Bob 运行 ECDH 并同意一条曲线和一个基点 G。Bob 将他的公钥 bG 发送给 Alice。Alice 而不是在商定的曲线上发送公钥 aG，而是发送一个在不同曲线上的点，无论是有意还是无意。不幸的是，这条新曲线很弱，允许 Alice 选择一个点 *P*，使得求解 ECDLP 很简单。她选择一个低阶点，对于该点存在相对较小的 *k* 使得 *kP = O*。

Bob 相信他拥有合法的公钥，计算他认为的共享密钥 *bP*，对其进行哈希，并使用 resulting key 来加密发送给 Alice 的数据。当 Bob 计算 *bP* 时，他不知不觉地在较弱的曲线上进行计算。因此，由于 *P* 被选为属于较大点群中的一个小子群，结果 *bP* 也属于该小子群，如果攻击者知道 *P* 的阶，就能有效地确定共享密钥 *bP*。

一种防止方法是确认点 *P* 和 *Q* 属于正确的曲线，通过确保它们的坐标满足曲线方程。这确保你只能在安全的曲线上工作。

这种无效曲线攻击于 2015 年在某些使用 ECDH 来协商会话密钥的 TLS 协议实现中被发现。（详情请参阅 Tibor Jager、Jörg Schwenk 和 Juraj Somorovsky 的论文“Practical Invalid Curve Attacks on TLS-ECDH”。）

### Incompatible Ed25519 Validation Rules

你已经看到 Ed25519 是一种签名方案，旨在提供效率和高度安全保证。Ed25519 的设计者在科学论文中详细描述了其工作原理并发布了编写良好的参考实现。该算法在 RFC 8032 中被指定为 IETF 标准。人们会期望只有一个版本的 Ed25519，不同的实现以完全相同的方式工作：对于给定的输入值，它们都应表现一致并返回相同的结果。

不幸的是，情况并非如此。正如密码学家 Henry de Valence 在文章“It’s 25519: JAM. Do You Know What Your Validation Criteria Are?” 中记录的那样（参见 *https://hdevalence.ca/blog/2020-10-04-its-25519am*），不同的 Ed25519 实现对什么是有效签名有不同的标准。事实上，RFC 8032 并未完全描述验证标准——而且许多实现甚至不符合它。

在 de Valence 的文章中，15 个实现各自拥有自己的验证标准。特别是，签名中点 *R* 和公钥 *A* 的验证通常不同，*s × B* 与 *R + Hash(R, A, M) × A* 之间的相等性验证也是如此。差异可能发生在多个层面，包括点的编码（如何组装字节来描述其坐标）以及点是否属于正确子群的验证。

因此，同一方案的不同实现可能表现不同——例如，在区块链网络中，签名会被某些节点接受而被其他节点拒绝，这对共识协议来说是个问题。所有细节都在 de Valence 的博文中进行了说明。




## 扩展阅读

椭圆曲线密码学是一个迷人而复杂的主题，涉及大量数学知识。我没有讨论一些重要概念，例如点的阶、曲线的余因子、射影坐标、挠点以及求解 ECDLP 问题的方法。如果你对数学感兴趣，可以在 Henri Cohen 和 Gerhard Frey 所著的 *《椭圆与超椭圆曲线密码学手册》*（Chapman and Hall/CRC，2005 年）中找到这些及其他相关主题的信息。Joppe Bos、Alex Halderman、Nadia Heninger、Jonathan Moore、Michael Naehrig 和 Eric Wustrow 在 2013 年发表的综述“实践中的椭圆曲线密码学”也提供了图文并茂的介绍和实际示例（https://eprint.iacr.org/2013/734）。

## 第四部分
## 应用

各种实现已经登上了新闻头条——Heartbleed、BEAST、CRIME 和 POODLE 都是影响了数百万台 Web 服务器的漏洞。

注意：你可能会看到有人将 TLS 称为安全套接字层（SSL），这是其前身的名称。

2013 年，工程师们开始着手开发 TLS 1.3。正如你将在本章中学到的，TLS 1.3 摒弃了不必要和不安全的特性，并用当时最先进的算法取代了旧算法。其结果是更简单、更快且更安全的协议。

在探讨 TLS 1.3 的工作原理之前，我们先回顾一下 TLS 旨在解决的问题以及它存在的原因。

## 目标应用与需求

TLS 是 HTTPS 网站中的 S，浏览器地址栏中出现的挂锁图标表示页面是安全的。创建 TLS 的主要动机是通过对站点进行身份验证并加密流量来保护敏感信息（如个人数据、信用卡号和用户凭证），从而在电子商务或网上银行等应用中实现安全浏览。

TLS 还通过在客户端和服务器之间建立安全通道来帮助保护普遍的基于互联网的通信，确保传输的数据是机密、经过身份验证且未被修改的。

TLS 的安全目标之一是防止中间人攻击，即攻击者截获发送方的加密流量，解密流量以获取明文内容，然后重新加密并发送给接收方。TLS 通过使用证书和受信任的证书颁发机构对服务器（以及可选地对客户端）进行身份验证来阻止这些攻击，我们将在第 258 页的“证书与证书颁发机构”中讨论。

为了被广泛采用，TLS 还需要满足另外四个要求：效率、互操作性、可扩展性和通用性。对于 TLS，效率意味着与未加密连接相比，将性能损失降至最低。这对服务器（降低服务提供商的硬件成本）和客户端（避免可感知的延迟或减少移动设备的电池消耗）都有好处。协议需要具备互操作性，以便能在任何硬件和任何操作系统上运行。它需要可扩展，以便支持额外的特性或算法。而且它必须通用——即不绑定于特定应用。这与传输控制协议（TCP）类似，TCP 并不关心其上层使用的应用协议。

## TLS 协议套件

为了保护客户端与服务器之间的通信，TLS 由若干协议的多个版本组成，形成 TLS 协议套件。TLS 不是传输协议，通常位于传输协议（TCP）和应用层协议（如 HTTP 或 SMTP）之间，以保护通过 TCP 连接传输的数据。

TLS 也可以运行在*用户数据报协议（UDP）*传输协议之上，该协议用于需要对延迟要求极低的“无连接”传输，例如音频或视频流媒体和在线游戏。然而，与 TCP 不同，UDP 不保证传输或数据包的正确排序。因此，TLS 的 UDP 版本——*数据报传输层安全性（DTLS）*略有不同。有关 TCP 和 UDP 的更多信息，请参阅 Charles Kozierok 的 *《TCP/IP 指南》*（No Starch Press，2005 年）。

## TLS 和 SSL 协议家族

TLS 始于 1995 年，当时网景（Netscape）开发了 TLS 的前身——SSL 协议。SSL 远非完美，SSL 2.0 和 SSL 3.0 都存在安全缺陷。你绝不应该使用 SSL，而应始终使用 TLS——令人困惑的是，人们（包括安全专家）经常把 TLS 称为 SSL。

并非所有版本的 TLS 都是安全的。TLS 1.0（1999 年）是最不安全的版本，但它仍然比 SSL 3.0 安全。TLS 1.1（2006 年）好一些，但包含许多弱算法。TLS 1.2（2008 年）更好，但很复杂，只有在正确配置的情况下才能提供高安全性。此外，其复杂性增加了实现中出错的风险以及配置错误的风险。例如，TLS 1.2 支持 CBC 模式下的 AES，该模式常常容易受到填充预言机攻击。

TLS 1.2 从早期 TLS 版本中继承了数十个特性和设计选择，这些使得它在安全性和性能方面并非最优。为了清理这个烂摊子，密码学工程师重新设计了 TLS——只保留好的部分并增加安全特性。结果是 TLS 1.3，一次彻底改进，简化了臃肿的设计，使其更安全、更高效、更简单。从本质上讲，TLS 1.3 是成熟的 TLS。

## TLS 概览

TLS 有两个主要协议：*握手协议*（或简称*握手*）确定双方共享的密钥；*记录协议*描述如何使用这些密钥来保护数据。TLS 处理的数据包称为*记录*。TLS 定义了一种数据包格式，用于封装来自高层协议的数据，以便传输给另一方。

握手从客户端发起与服务器的安全连接开始。客户端发送一条名为 ClientHello 的初始消息，其中包含它想要使用的密码算法的参数。服务器检查此消息及其参数，然后以 ServerHello 消息作为响应。一旦客户端和服务器处理完彼此的消息，它们就可以使用通过握手协议建立的会话密钥来交换加密数据，正如你将在第 263 页的“TLS 握手协议”中看到的那样。

## 证书与证书颁发机构

TLS 握手中最关键的一步，也是 TLS 安全的核心，是*证书验证步骤*，服务器在此步骤中使用证书向客户端进行身份验证。

*证书*本质上是一个公钥，附带该密钥的签名以及相关信息（包括域名）。例如，当连接到 *https://www.google.com* 时，你的浏览器会从某个网络主机接收证书，然后验证该证书的签名，签名内容大致是“我是 *google.com*，我的公钥是 [key]。”如果签名验证通过，该证书及其公钥就是*可信的*，浏览器便会继续建立连接。（有关签名的详细信息，请参阅第 10 章和第 12 章。）

浏览器通过*证书颁发机构（CA）*获知验证签名所需的公钥，该机构本质上是一个硬编码在浏览器或操作系统中的公钥。该公钥对应的私钥（即其签名能力）属于一个受信任的组织，该组织确保其颁发的证书中的公钥归属于声明这些公钥的网站或实体。也就是说，CA 充当*可信第三方*。如果没有 CA，就无法验证 *google.com* 提供的公钥确属 Google，而不是来自某个实施中间人攻击的窃听者。

例如，清单 13-1 展示了当你使用 OpenSSL 命令行工具发起到 *www.google.com* 的 443 端口（用于基于 TLS 的 HTTP 连接（HTTPS）的网络端口）的 TLS 连接时会发生什么。

```text
$ openssl s_client -connect www.google.com:443
CONNECTED(00000003)
---
Certificate chain
 0 s:CN = www.google.com
   i:C = US, O = Google Trust Services LLC, CN = GTS CA 1C3
 1 s:C = US, O = Google Trust Services LLC, CN = GTS CA 1C3
   i:C = US, O = Google Trust Services LLC, CN = GTS Root R1
 2 s:C = US, O = Google Trust Services LLC, CN = GTS Root R1
   i:C = BE, O = GlobalSign nv-sa, OU = Root CA, CN = GlobalSign Root CA
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIEiDCCA3CgAwIBAgIQNjVv7ypW9IQhAa7P69MzzANBgkqhkiG9w0BAQsFADBC
MQswCQYDVQQGEwJVUzEiMCAGA1UEChMZRT2vZ1lFRydXN0IFNlcnZpY2VzIExM
QzETMBEGA1UEAxMKR1RTIENBIFDmAzAeFw0yMzA5MDQwODIzMjJaFw0yNDEwODIz
ODIzMjhaMBkxFzAVBgNVBAMTDnd3dy5nb29nbGUuY29tMRkwFwYDVQQpZCjocaQIYI
KoZIh0NAQ0DgQAgENEMwVAYoTRTboW5ZxbUbX:/Z+EvcEi5OsZQZvP/xyyVIaURm4
AoJer9IJ0/6Iq62oAfDXUgrdBKpSzJzaeFCaqqOCAmg wggJkMA4GA1UdDwEB/wQE
AwIHgDATBgNVHSUEDDAKBggrBgEFBQcDATAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW
BBRnwQnVC8ok1e6YPIbQWjB+XFpPRjAfBgNVHSMEGDAWgBSKdH+vhc3ulc09nNDi
RhTzcTUdJzBqBggrBgEFBQcBAQR eMFwwWyIKwYBBQUHMAKGG2hOdHA6Ly9vY3Nw
LnBra5nb29nL2doczFjMZAxBggrBgEFBQcYB1YhaHR0cDovL3Bra5Sn b29nL3Jl
cG8yV2YvdHMvZ3RwMzlzLmRlciJAZBgNVHREEGDAWggR5d3d3Lm google.com
BgNVHSAEGjAYMAgG BmeDBAECATAMBgorBgEEAdZ5AgUDMwGA1UdHwQ1MDMwMaAv
-----END CERTIFICATE-----
```





```
oC2GK2h0dHA6Ly9jcmxzLnBra5Snb29nL2doCzFjMy9mVkp4Y1Y1tS3Rtay5jcmww
ggEFBgorBgEAdZ5AgQCBIH2BIHzAPEAdgDpTdPaVU GNTLnVyi8i8wJAJ9PLoRF r
70tp4X9bqA9bggAAYpfgRj0AAAEEAwBHMEUCI... 
SYKzbELytrDz9w1mAIeIAIWOPMM26CynmasqpmXKXRDnVwyzdiUhVimhOsnR BAA
dwB6MoxU2LcttiDq00BSHumEFnAyE4VNO9IrwTpXoiLrUgAAYpfgRkAAAAEAWBI
MEYCIQDZfitULkVCXRc68ZjWgp5WFUjTxFjz6CP+el3dgz3gIhAj9uS7psu2Gl
HdTXokXTetMY7MC IcuJ60Qm/qTn+1dFMAOGCSqGSIb3DQEBCwUAAIBAQCIE nOv
QzaNQOhiI5TKcRhaR24yKidF57a/GM1LDE/v70Cm+3fxtvuK HvA/Dmvnavq p
ci7TpMDJ/ocXjEadL4/yHaV6XhGDtWMK//bbBKDaqXOsb1aI8UCZPLVT4A jfdjmB
8wZF9sbnfeuKNXW1bo/k/9pRRhF NKKMUI54xLiVdj4wk1EUA s rMTn+O12ZbFeS
s614abTSWohFkLvyjEht8p3pUKOwyhRjZMBsae/dooFT8hgvLtvhGd7f1hFqI
X SER18EsyDc3urSa+R UjCvE9Q+Y2X8WVVO H PCjwsANU56qEZmh4kqgg5paw/SL
maM/8Vny/nKNd6Dj
-----END CERTIFICATE-----
subject=CN = www.google.com

issuer=C = US, O = Google Trust Services LLC, CN = GTS CA 1C3

---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: ECDSA
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 4295 bytes and written 396 bytes
Verification: OK
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 256 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
```

*清单 13-1：与 www.google.com 建立 TLS 连接并接收证书以对连接进行身份验证*

证书数据位于 BEGIN CERTIFICATE 和 END CERTIFICATE 标记之间。在此之前，Certificate chain（证书链）部分包含对证书链的描述，其中以 s: 开头的行描述被认证实体的主体，以 i: 开头的行描述签名的签发者。编号为 0 的证书由 www.google.com 接收，证书 1 属于为证书 0 签名的实体，证书 2 属于为证书 1 签名的实体。

签发证书 0 的组织是 Google（通过 Google Trust Services 实体，即 GTS），该组织使用 GTS CA 1C3 私钥对证书签名，从而授权为域名 www.google.com 签发证书 0。证明该密钥属于 Google 密钥层级的证书是证书 1，它由 GTS 的 Root R1 密钥签名，Root R1 是 Google 内部的一个根证书。证书 2 由 GlobalSign（一家公认的证书颁发机构）签发，证明 **GTS Root R1** 密钥属于 Google 组织。

在此示例中，你的操作系统通常已经拥有证书 1 和证书 2，并将它们视为受信任的证书。在这种情况下，你只需要检查两个签名：证书 0 中 Google 的 GTS CA 1C3 实体，以及证书 1 中 Google 的 GTS Root R1 实体。如果你的系统尚未将证书 2 作为受信任的证书包含在内，而是拥有 GlobalSign 的根证书（GlobalSign Root CA），那么你还需要检查证书 2 中 GlobalSign 的签名。

诸如 Google 和 GlobalSign 之类的证书颁发机构必须值得信赖，并且只向可信实体签发证书；同时，它们必须保护好各自的私钥，以防止攻击者以它们的名义签发证书（例如，假冒合法的 *www.google.com* 服务器）。

若要查看证书中的内容，请在 Unix 终端中输入命令 **openssl x509 -text -noout**，然后粘贴清单 13-1 中的证书。输出结果见清单 13-2。

```
$ openssl x509 -text -noout
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            34:9b:c8:bf:bc:a9:5b:d2:10:1d:a0:3b:3f:af:4c:cf
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: C = US, O = Google Trust Services LLC, CN = GTS CA 1C3
        Validity
            Not Before: Sep  4 08:23:29 ...
            Not After : Nov 27 08:23:28 ...
        Subject: CN = www.google.com
        Subject Public Key Info:
            Public Key Algorithm: id-ecPublicKey
                Public-Key: (256 bit)
                pub:
                    04:34:43:2f:58:06:34:4d:14:db:d3:0e:59:c5:b5:
                    1b:5f:f6:7e:11:cb:e2:13:9d:12:cd:0c:ef:3f:fc:
                    72:c9:52:1a:51:13:38:03:42:5e:af:d2:09:3b:fe:
                    88:ab:aa:36:01:f0:d7:53:1a:dd:04:aa:52:ce:5c:
                    da:78:50:9a:aa
                ASN1 OID: prime256v1
                NIST CURVE: P-256
        X509v3 extensions:
            X509v3 Key Usage: critical
                Digital Signature
            X509v3 Extended Key Usage:
                TLS Web Server Authentication
            X509v3 Basic Constraints: critical
                CA:FALSE
            X509v3 Subject Key Identifier:
                67:C1:09:D5:0B:CA:24:D5:EE:98:3C:86:D0:C2:30:7E:5C:5A:4F:46
            X509v3 Authority Key Identifier:
                8A:74:7F:AF:85:CD:EE:95:CD:3D:9C:D0:E2:46:14:F3:71:35:1D:27
```

```
Authority Information Access:
    OCSP - URI:http://ocsp.pki.goog/gts1c3
CA Issuers - URI:http://pki.goog/repo/certs/gts1c3.der
X509v3 Subject Alternative Name:
    DNS:www.google.com
X509v3 Certificate Policies:
    Policy: 2.23.140.1.2.1
    Policy: 1.3.6.1.4.1.11129.2.5.3
X509v3 CRL Distribution Points:
    Full Name:
        URI:http://crls.pki.goog/gts1c3/fVJxbV-ktmk.crl
CT Precertificate SCTs:
    Signed Certificate Timestamp:
        Version   : v1 (0x0)
        Log ID    : E8:3E:D0:DA:3E:F5:06:35:32:E7:57:28:BC:89:6B:C9:
                    03:D3:CB:D1:11:6B:EC:EB:69:E1:77:7D:6D:06:BD:6E
        Timestamp : Sep  4 09:23:30.638 2023 GMT
        Extensions: none
        Signature : ecdsa-with-SHA256
            30:45:02:20:3F:81:71:2F:7C:E1:21:21:D8:4D:94:AC:
            A7:CB:BC:5D:9F:1B:BA:9A:49:89:33:6C:42:F2:B6:B0:
            F3:F7:5C:26:02:21:00:97:03:8F:30:CD:BA:0B:29:E6:
            69:DB:2A:A2:63:CC:5C:A7:51:34:CB:F3:77:27:22:1D:
            58:A6:87:4B:27:AC:10
    Signed Certificate Timestamp:
        Version   : v1 (0x0)
        Log ID    : 7A:32:8C:54:D8:B7:2D:B6:20:EA:38:E0:52:1E:E9:84:
                    16:70:32:13:85:4D:3B:D2:2B:C1:3A:57:A3:52:EB:52
        Timestamp : Sep  4 09:23:30.688 2023 GMT
        Extensions: none
        Signature : ecdsa-with-SHA256
            30:46:02:21:00:D9:7F:5B:54:2E:45:42:5D:17:3A:F3:
            32:70:82:9E:56:14:95:1B:4F:11:63:CF:A0:8F:F9:E2:
            DB:DD:D8:33:DE:02:21:00:9F:6E:4B:BA:6C:BB:61:A5:
            1D:D4:D7:A2:45:D3:7A:D3:18:EC:C0:9D:21:CB:A3:EB:
            44:26:FE:A4:E7:FB:57:45
Signature Algorithm: sha256WithRSAEncryption
Signature Value:
    88:12:7d:2f:43:36:aa:34:23:a1:88:8e:53:29:c4:61:69:1d:
    b8:c8:a8:9d:dc:5e:7b:6b:f1:8e:33:52:c3:13:fb:a0:29:
    be:dd:fc:6d:be:e2:bd:1d:56:bf:0e:69:ef:6a:fa:a9:72:2e:
    d3:a4:c0:e3:fe:87:17:8c:4e:1d:2f:8f:f2:1d:a5:71:e8:68:
    53:0c:a3:16:fd:b6:c1:90:36:aa:5e:84:9d:6f:d9:40:71:46:
    4f:2d:14:d5:e0:08:c5:76:39:81:f3:06:53:7f:de:5b:9d:f7:
    ae:28:d5:d6:95:ba:3f:93:ff:69:45:18:45:34:a2:8c:50:8e:
    78:c4:b8:95:76:3e:30:93:51:14:02:ca:cc:4d:39:fe:3a:5d:
    99:6c:57:92:b3:ad:78:69:b0:53:e5:6d:21:84:59:0b:be:3b:
    c4:86:df:29:dd:42:90:c3:0c:a1:46:36:4c:06:c6:9e:fd:dd:
    10:7d:3f:21:82:55:6d:56:18:46:77:b7:f5:84:5a:88:5d:21:
    11:97:c1:2c:c8:37:37:ba:b0:ac:6b:e4:63:52:30:af:13:d4:
    3e:cb:65:fc:59:55:74:1c:f0:a3:c2:c0:0d:53:9e:aa:11:99:
    a1:e2:4a:a0:83:9a:5a:5b:f4:8b:99:a3:3f:f1:59:f2:fe:72:
    8d:77:a0:e3
```

*清单 13-2：解码从 www.google.com 收到的证书*

此清单展示了 openssl x509 命令解码证书的过程，该证书最初以 base64 编码的数据块形式提供。由于 OpenSSL 知道这些数据的结构，因此它可以告诉你证书内部包含哪些内容，包括序列号和版本信息、标识信息、有效期（Not Before 和 Not After 两行）、公钥（此处为 RSA 模数及其公开指数），以及对前述信息的签名。

尽管安全专家和密码学家常常声称整个证书体系本质上是有缺陷的，但它仍然是我们拥有的最佳解决方案之一，例如 SSH 采用的首次使用信任（TOFU）策略也是如此。

## 记录协议

所有通过 TLS 1.3 通信交换的数据都以 TLS 记录序列的形式传输，TLS 记录是 TLS 所使用的数据包。TLS 记录协议（即*记录层*）本质上是一种传输协议，与所传输数据的含义无关；这使 TLS 适用于任何应用程序。

TLS 记录协议首先承载握手期间交换的数据。握手完成后，双方共享一个密钥，应用程序数据会被分片成多个块，作为 TLS 记录的一部分进行传输。

## TLS 记录的结构

TLS 记录是一个最大不超过 16KB 的数据块，其结构如下：

- 第一个字节表示所传输数据的类型：握手数据设为 22，加密数据设为 23，警报设为 21。TLS 1.3 规范将该值称为 ContentType。
- 第二个和第三个字节分别设为 03 和 01。这两个字节出于历史原因而固定不变，并非 TLS 1.3 版本独有。规范将这个 2 字节的值称为 ProtocolVersion。
- 第四个和第五个字节将待传输数据的长度编码为 16 位整数，该长度不能超过 2^14 字节（16KB）。
- 其余字节为待传输的数据（即*载荷*），其长度等于记录第四个和第五个字节所编码的值。

> > **注意**  TLS 记录的结构相对简单。如你所见，TLS 记录的头部仅包含三个字段。相比之下，IPv4 数据包在载荷之前包含 14 个字段，而 TCP 段包含 13 个字段。

当 TLS 1.3 记录的第一个字节（ContentType）设为 23 时，认证加密算法会对其载荷进行加密和认证。载荷由密文和紧随其后的认证标签组成，接收端分别对密文进行解密、对认证标签进行验证。接收方知道该使用哪个


用来解密的密码算法和密钥，这要归功于 TLS 的神奇之处：如果你收到一条加密的 TLS 记录，你就已经知道密码算法和密钥，因为执行握手协议会确立它们。

## Nonce（随机数）

与许多其他协议（如 IPsec 的封装安全载荷（ESP））不同，TLS 记录并不指定认证加密算法将使用的 nonce。

用于加密和解密 TLS 记录的 nonce 派生自 64 位序列号，该序列号由各方在本地维护，并在每处理一条新记录时递增。当客户端加密数据时，它通过将序列号与 `client_write_iv` 值进行 XOR 运算来派生 nonce，而 `client_write_iv` 值本身又源自共享密钥。服务器在传输数据时使用类似的方法来选择 nonce，但使用的是 `server_write_iv` 值。

例如，如果你发送三条 TLS 记录，那么你会为第一条记录从 0 派生 nonce，第二条从 1，第三条从 2；如果你随后接收三条记录，你也会按顺序使用 nonce 0、1 和 2。对发送数据的加密和接收数据的解密重用相同的序列号值并不是弱点，因为它们与不同的常量（`client_write_iv` 和 `server_write_iv`）进行 XOR 运算，并且每个方向都使用不同的密钥。

## 零填充特性

TLS 1.3 记录支持*零填充*，这可以减轻流量分析攻击。攻击者利用*流量分析*，通过时间、传输数据量等流量模式提取信息。例如，由于密文与明文大小大致相同，即使使用强加密，攻击者也可以通过查看密文的长度来确定消息的大致大小。

零填充在明文中添加零，以增大密文的尺寸，使观察者误以为加密消息比实际更长。

## TLS 握手协议

握手是 TLS 协商协议的核心——客户端和服务器通过该过程建立共享密钥以启动安全通信。在 TLS 握手期间，客户端和服务器扮演不同角色。客户端提出一些配置（按优先顺序给出 TLS 版本和一组密码算法），服务器选择它将使用的配置。服务器应当遵循客户端的偏好。为了确保各实现之间的互操作性，并确保任何实现 TLS 1.3 的服务器都能读取任何实现 TLS 1.3 的客户端发送的 TLS 1.3 数据（即使它使用不同的库或编程语言），TLS 1.3 规范还描述了数据发送时应采用的格式。

图 13-1 展示了握手过程如何交换数据，正如 TLS 1.3 规范所描述的那样。

![](img/ace4de942d037de8ea5835bc9fbe57cd_291_0.png)

*图 13-1：TLS 1.3 握手过程*

在 TLS 1.3 握手中，客户端向服务器发送一条消息：“我想与你建立 TLS 连接。以下是我支持的用于加密 TLS 记录的密码算法，以及一个 Diffie–Hellman 公钥。”该公钥必须专门为本次 TLS 会话生成，并且客户端保留关联的私钥。客户端发送的消息还包含一个 32 字节的随机值和可选信息（如附加参数）。这一首条消息 *ClientHello* 在作为字节序列传输时必须遵循 TLS 1.3 规范定义的特定格式。

服务器收到 ClientHello 消息后，验证其格式是否正确，并用一条 ServerHello 消息作为响应，该消息携带了大量信息。通常，当连接到 HTTPS 网站时，它包含将用于加密 TLS 记录的密码算法、一个 Diffie–Hellman 公钥、一个 32 字节的随机值（在第 266 页的“降级保护”中讨论）、一个证书、对 ClientHello 和 ServerHello 消息中所有先前信息的签名（使用与证书公钥关联的私钥计算），以及该相同信息的 MAC，外加签名。MAC 使用从 Diffie–Hellman 共享密钥派生的对称密钥计算，服务器通过其 Diffie–Hellman 私钥和客户端公钥计算该共享密钥。

当客户端收到 ServerHello 消息时，它会验证证书的有效性，验证签名，计算共享的 Diffie–Hellman 秘密并从其中派生对称密钥，然后验证服务器发送的 MAC。一旦所有内容都得到验证，客户端就可以向服务器发送加密消息了。

注意：TLS 1.3 支持许多选项和扩展，因此其行为可能有所不同。例如，你可以将 TLS 1.3 握手配置为要求客户端证书，以便服务器验证客户端的身份。TLS 1.3 还支持使用预共享密钥的握手。

让我们看一下实际情况。假设你已经部署了 TLS 1.3，以提供对网站 https://www.nostarch.com 的安全访问。当你将浏览器（客户端）指向该站点时，浏览器会向站点服务器发送一条 ClientHello 消息，其中包含它支持的密码算法。网站则以 ServerHello 消息和证书作为响应，证书包含与域名 www.nostarch.com 关联的公钥。客户端使用浏览器中嵌入的证书颁发机构之一来验证证书的有效性（受信任的证书颁发机构必须对收到的证书进行签名，且其证书应包含在浏览器或操作系统的证书存储中，以便进行验证）。一旦所有检查通过，浏览器就从 www.nostarch.com 服务器请求该站点的初始页面。

TLS 1.3 握手成功后，客户端与服务器之间的所有通信都将被加密和认证。窃听者可以得知某个给定 IP 地址的客户端正在与另一个给定 IP 地址的服务器通信，并且可以观察到交换的加密内容，但无法获知底层明文，也无法修改加密消息（如果修改，接收方将会注意到通信已被篡改，因为消息是经过认证的）。对许多应用来说，这已经足够安全了。

## TLS 1.3 加密算法

TLS 1.3 使用认证加密算法、密钥派生函数（一种从共享秘密派生密钥的哈希函数），以及 Diffie–Hellman 操作——但这些究竟如何工作，使用哪些算法，安全性又如何呢？

关于认证加密算法的选择，TLS 1.3 仅支持三种算法：AES-GCM、AES-CCM（一种效率略低于 GCM 的模式），以及 ChaCha20 流密码与 Poly1305 MAC 的组合（如 RFC 7539 所定义）。由于 TLS 1.3 禁止使用不安全的密钥长度（如 64 或 80 位），因此密钥可以是 128 位（AES-GCM 或 AES-CCM）或 256 位（AES-GCM 或 ChaCha20-Poly1305）。

图 13-1 中的密钥派生操作（KDF）基于 HKDF，这是一种基于 HMAC 的构造（参见第 7 章），定义于 RFC 5869，使用 SHA-256 或 SHA-384 散列函数。

你执行 Diffie–Hellman 操作（TLS 1.3 握手核心）的选项仅限于椭圆曲线密码学和模素数整数乘法群（如传统 Diffie–Hellman）。但你不能使用任意椭圆曲线或群：受支持的曲线包括三条 NIST 曲线，以及 Curve25519（参见第 12 章）和 Curve448，后两者均定义于 RFC 7748。TLS 1.3 还支持在整数群上进行 DH 运算，而非椭圆曲线。所支持的群是 RFC 7919 中定义的五种群：2,048、3,072、4,096、6,144 和 8,192 位。

2,048 位群在理论上可能是 TLS 1.3 中最薄弱的一环。其他选项至少提供 128 位安全性，而 2,048 位 Diffie-Hellman 被认为提供不到 100 位安全性。因此，支持 2,048 位群可能被视为与 TLS 1.3 的其他设计选择不一致。实际上，100 位安全性大约与 128 位一样难以破解——也就是几乎不可能。

## TLS 1.3 相比 TLS 1.2 的改进

TLS 1.3 与其前身大不相同。首先，它去除了 MD5、SHA-1、RC4 和 CBC 模式下的 AES 等弱算法。此外，TLS 1.2 通常使用 MAC-then-encrypt 结构中密码算法与 MAC（如 HMAC-SHA-1）的组合来保护记录，而 TLS 1.3 仅支持更高效、更安全的认证加密算法。TLS 1.3 还摒弃了椭圆曲线点编码协商，并为每条曲线定义了单一的点格式。

TLS 1.3 移除了 1.2 中削弱协议安全性的特性，并降低了协议的整体复杂度，从而缩小了其攻击面。例如，TLS 1.3 摒弃了可选的数据压缩功能，正是该功能使得 CRIME 攻击能够针对 TLS 1.2 实施。这种攻击利用了以下事实：消息压缩版本的长度会泄露消息内容的相关信息。

但 TLS 1.3 也带来了新特性，使连接更安全或更高效。我将讨论其中三个特性：降级保护、单次往返握手和会话恢复。

## 降级保护

TLS 1.3 的降级保护功能是一种针对降级攻击的防御措施，攻击者借此迫使客户端和服务器使用比 TLS 1.3 更弱的 TLS 版本。为了实施降级攻击，攻击者通过截获并修改 ClientHello 消息，让服务器以为客户端不支持 TLS 1.3，从而迫使服务器使用更弱的 TLS 版本。这样攻击者就可以利用早期 TLS 版本中的漏洞。

为了抵御降级攻击，TLS 1.3 服务器在 ServerHello 消息中发送的 32 字节随机值内使用三种类型的模式，以识别所请求的连接类型。该模式应与客户端请求的特定 TLS 连接类型相匹配。如果客户端收到错误的模式，它就会知道出了问题。

具体来说，如果客户端请求 TLS 1.2 连接，32 字节中的前 8 个字节设置为 44 4F 57 4E 47 52 44 01；如果请求 TLS 1.1 连接，则设置为 44 4F 57 4E 47 52 44 00。然而，如果客户端请求 TLS 1.3 连接，这前 8 个字节应该是随机的。例如，如果客户端发送一个请求 TLS 1.3 连接的 ClientHello，但一个

网络上的攻击者修改该消息（ClientHello），要求使用 TLS 1.1 连接。当客户端收到具有错误模式的 ServerHello 时，它就知道其 ClientHello 消息已被修改。（攻击者无法任意修改服务器的 32 字节随机值，因为该值是经过加密签名的。）

## 单次往返握手

在典型的 TLS 1.2 握手中，客户端向服务器发送一些数据，等待响应，然后发送更多数据并等待服务器响应，之后才发送加密消息。延迟为两个往返时间（RTT）。相比之下，TLS 1.3 的握手只需一个往返时间（见图 13-1）。节省的时间可达数百毫秒。考虑到热门服务的服务器每秒处理成千上万的连接，这一点非常重要。

## 会话恢复

TLS 1.3 比 TLS 1.2 更快，但通过完全消除加密会话之前的往返，还可以使其更快（数百毫秒的量级）。诀窍是使用会话恢复，它利用客户端和服务器在先前会话中交换的预共享密钥来启动新会话。会话恢复有两个主要好处：客户端可以立即开始加密，并且后续会话无需使用证书。

图 13-2 展示了会话恢复的工作原理。

![](img/ace4de942d037de8ea5835bc9fbe57cd_294_0.png)

图 13-2：TLS 1.3 会话恢复握手，其中 0-RTT 数据是与 ClientHello 一起发送的会话恢复数据。

首先，客户端发送一条 ClientHello 消息，其中包含与服务器已共享密钥的标识符（称为 PSK，即预共享密钥），以及一个新的 DH 公钥。客户端还可以在这第一条消息中包含加密数据（称为 0-RTT 数据）。当服务器响应 ClientHello 消息时，它会为数据交换提供 MAC。客户端验证 MAC 后，就知道它正在与之前通信过的同一台服务器通信，因此证书验证变得有些多余。

实际上，如果攻击者入侵了客户端的机器并获取其所有内存的访问权，他们可能会从内存中恢复客户端当前会话的 TLS 会话密钥和机密。但更重要的是，如果先前的密钥仍留在内存中，攻击者可能找到它们并解密以前的会话，从而绕过理论上的前向保密性。因此，对于 TLS 实现来说，要确保前向保密性，就必须在密钥不再使用后将其从内存中正确擦除，通常是将内存清零。

## 可能出现的问题

TLS 1.3 符合通用安全通信协议的要求，但它并非无懈可击。像任何安全系统一样，它在某些情况下可能会失效（例如，当设计者关于真实攻击的假设错误时）。不幸的是，即使是配置了最安全密码套件的最新版本 TLS 1.3 也可能被攻破。例如，TLS 1.3 的安全性依赖于一个假设，即所有三方（客户端、服务器和证书颁发机构）都会诚实行为，但如果其中一方被攻破，或者 TLS 实现本身很差，该怎么办？

### 被攻破的证书颁发机构

根证书颁发机构（root CA）是浏览器信任的组织，用于验证远程主机提供的证书。例如，如果您的浏览器接受了 *www.google.com* 提供的证书，那么就意味着某个受信任的 CA 已验证了证书所有者的合法性。浏览器通过检查 CA 颁发的签名来验证证书。由于只有 CA 知道创建该签名所需的私钥，我们假设其他人不能代表 CA 创建有效的证书。很多时候，网站的证书不是由根 CA 签名，而是由中间 CA 签名，中间 CA 通过证书链连接到根 CA。

如果 CA 的私钥被泄露，攻击者就可以使用该 CA 的私钥为任何 URL 创建证书，例如 *google.com* 域中的 URL，而无需谷歌批准。然后，攻击者可以使用这些证书假装托管合法的服务器或子域，如 *mail.google.com*，并拦截用户的凭据和通信。2011 年发生的情况正是如此，当时一名攻击者入侵了荷兰证书颁发机构 DigiNotar 的网络，并创建了看似合法的证书。攻击者将这些伪造证书用于多个谷歌服务。

### 被攻破的服务器

如果服务器被攻破并完全被攻击者控制，那么一切都完了：服务器持有会话密钥，因为它是 TLS 连接的终止点。攻击者可以看到加密前的所有传输数据和解密后的所有接收数据。他们很可能还会获得服务器的私钥，从而可以利用自己的恶意服务器冒充合法服务器。在这种情况下，TLS 无法拯救你。

幸运的是，在 Gmail 和 iCloud 等知名应用中，此类安全灾难很少见，这些应用受到良好保护，有时其私钥存储在单独的安全模块中，例如硬件安全模块（HSM），直接或通过密钥管理系统（KMS）应用程序存储。

通过数据库查询注入和跨站脚本等漏洞对 Web 应用程序的攻击更为常见，因为这些攻击大多与 TLS 的安全性无关，而且是攻击者通过合法的 TLS 连接进行的。此类攻击可能会危及用户名、密码等。

### 被攻破的客户端

当客户端（如浏览器）被远程攻击者攻破时，TLS 安全也会受到威胁。攻击者攻破客户端后，能够捕获会话密钥、读取任何解密后的数据等。他们甚至可以在客户端系统中安装恶意 CA 证书，使其静默接受原本无效的证书，从而让攻击者拦截 TLS 连接。

被攻破的 CA 或服务器场景与被攻破的客户端场景之间的区别在于，在被攻破客户端的情况下，只有目标客户端受到影响，而不是可能所有客户端都受到影响。

### 实现中的缺陷

与任何密码学组件一样，TLS 的实现中如果存在缺陷，就可能会失效。TLS 缺陷的典型代表是 Heartbleed（见图 13-3），这是 OpenSSL 实现的一个称为心跳的次要 TLS 功能中的缓冲区溢出。Heartbleed 于 2014 年被谷歌研究员和 Codenomicon 公司独立发现，影响了数百万个 TLS 服务器和客户端。

![](img/ace4de942d037de8ea5835bc9fbe57cd_297_0.png)

图 13-3：OpenSSL 实现的 TLS 中的 Heartbleed 缺陷

客户端首先向服务器发送一个缓冲区以及缓冲区长度，以检查服务器是否在线。在此示例中，缓冲区是字符串 *BANANAS*，客户端明确说明该单词有七个字母长。服务器读取这个七个字母的单词并将其返回给客户端。

问题在于服务器不确认长度是否正确，而是尝试读取客户端指定的字符数。因此，如果客户端提供的长度大于字符串的实际长度，服务器就会从内存中读取过多数据并将其返回给客户端，同时返回的还可能包含敏感信息的额外数据，例如私钥或会话 cookie。

Heartbleed 缺陷令人震惊。为了避免将来出现类似缺陷，OpenSSL 和其他主要 TLS 实现现在进行严格的代码审查，并使用模糊测试器等自动化工具来识别潜在问题。

## 延伸阅读

本章不是 TLS 的全面指南，您可能希望更深入地了解 TLS 的历史、以往的漏洞和最新版本。完整的 TLS 1.3 规范可在 TLS 工作组（TLSWG）主页 https://tlswg.org 上找到，其中包含有关该协议的所有内容（但不一定包含其基本原理）。

我还建议您了解使用 TLS 的主要协议，例如 QUIC（用于 Chrome 和谷歌服务器之间的连接）和 SRTP（用于视频会议和流媒体传输）。

此外，以下是两个与 TLS 部署相关的重要举措：

- SSL Labs TLS 测试（https://www.ssllabs.com/ssltest）是 Qualys 提供的一项免费服务，可让您测试浏览器或服务器的 TLS 配置，提供安全评级和改进建议。如果您设置了自己的 TLS 服务器，请使用此测试确保一切安全。
- Let's Encrypt（https://letsencrypt.org）是一个非营利组织，提供在您的 HTTP 服务器上“自动地”部署 TLS 的服务。它包括自动生成证书和配置 TLS 服务器的功能，并支持所有常见的 Web 服务器和操作系统。




### 14 量子与后量子

![](img/ace4de942d037de8ea5835bc9fbe57cd_300_0.png)

在本章中，我们将考察密码学在未来一个世纪或更长时间跨度内的前景——在这个时间段内，量子计算机可能会出现。量子计算机利用量子物理中的现象来运行与我们习以为常的算法不同类型的算法。虽然大型量子计算机尚未问世，但它们有可能破解 RSA、Diffie–Hellman 和椭圆曲线密码学——也就是目前所有已部署或标准化的公钥密码学。为了防范量子计算风险，密码学研究者开发了替代性的公钥*后量子*算法。2015 年，美国国家安全局（NSA）呼吁向抗量子算法过渡；2017 年，NIST 启动了后量子算法的标准化工作，并于 2022 年将其作为新标准的一部分公布。

本章将非技术性地概述量子计算机背后的原理，并简要介绍后量子算法。其中涉及一些数学，但仅限于基础算术和线性代数，所以不必为那些不常见的符号感到担忧。

### 量子计算机的工作原理

量子计算利用量子物理学以不同的方式进行计算，并能执行经典计算机无法完成的任务，例如高效地破解 RSA 和椭圆曲线密码学。量子计算机并不是一台超快的普通计算机。事实上，量子计算机无法高效地解决任何对经典计算机来说过于困难的问题，例如暴力搜索或 NP 困难问题。

量子力学——研究亚原子粒子行为的物理学分支，这些粒子的行为是完全随机的——是量子计算机的基础。与经典计算机使用非 0 即 1 的比特不同，量子计算机使用量子比特（qubit），它可以“同时是 0 和 1”。这种不确定的状态称为叠加态，我在这里加引号表明这是一种过度简化的说法。在这个微观世界中，物理学家发现电子和光子等粒子的行为非常违反直觉：在你观察一个电子之前，它并不处于空间中的确定位置，而是同时处于多个位置（即处于叠加态）。一旦你观察它——这一操作称为测量——它就会停在一个固定的、随机的位置，不再处于叠加态；量子态坍缩了。这使得量子计算机中量子比特的创建成为可能，同时还有纠缠和干涉现象。

量子计算机之所以能工作，是因为纠缠现象：两个粒子以某种方式连接（纠缠）在一起，观察其中一个粒子的值就能得到另一个粒子的值，即使这两个粒子相距甚远（相隔数千米甚至数光年）。爱因斯坦–波多尔斯基–罗森（EPR）悖论说明了这种行为，这一悖论曾让阿尔伯特·爱因斯坦最初对量子力学持否定态度。（深入解释请参见 https://plato.stanford.edu/entries/qt-epr/。）

干涉对量子计算机的运行也至关重要。借助这一特性，粒子由于其波动性可以相互加强或抵消彼此的影响，双缝实验就是著名的例证。量子计算利用干涉，使有效解的“波”相互加强，而无效解则相互抵消。

为了解释量子计算机的工作原理，我将把实际的量子计算机（硬件，包括其中的量子比特）与量子算法（运行在其上的软件，由量子门组成）区分开来。

### 量子比特

你可以用振幅来刻画量子比特或其组，振幅是类似于概率但又不完全是概率的数。而一个

### 量子比特组的振幅

我们如何理解多个量子比特？例如，当八个量子比特的量子态通过纠缠连接在一起时，它们可以构成一个*量子字节*。你可以像下面这样描述这样的量子字节，其中 α 是与这组八个量子比特的 256 种可能取值各自关联的振幅：

α₀|00000000⟩ + α₁|00000001⟩ + α₂|00000010⟩ + α₃|00000011⟩ + … + α₂₅₅|11111111⟩

注意，必须有 |α₀|² + |α₁|² + … + |α₂₅₅|² = 1，这样所有概率之和才为 1。

你可以将这组八个量子比特视为 2⁸ = 256 个振幅的集合，因为它有 256 种可能的配置，每种配置都有自己的振幅。

然而，在物理现实中，你会有 8 个物理对象，而不是 256 个。这 256 个振幅是这组八个量子比特的隐含特征；这 256 个数中的每一个都可以取无穷多个不同值中的任意一个。推而广之，你可以用一组 2ⁿ 个复数来刻画一组 n 个量子比特，这个数量随量子比特的数量呈指数增长。

如果你想用经典计算机模拟量子态的演化，就需要存储这个指数级的振幅数量，并进行计算来修改它们。这个需求是经典计算机无法高效模拟量子计算机的主要原因之一：这样做需要巨大的内存（数量级为 2ⁿ）来存储仅 n 个量子比特在量子系统中所包含的同等信息量。实际上，根据计算类型的不同，你最多只能模拟 50 或 60 个量子比特。

### 量子门

振幅和*量子门*的概念是量子计算所独有的。量子门本质上是对一个或多个量子比特的变换，相当于量子计算领域中的电子门。经典计算机使用寄存器、内存和微处理器对数据执行一系列指令，而量子计算机则通过施加一系列量子门来可逆地变换一组量子比特，然后测量一个或多个量子比特的值。量子计算机之所以有望提供更强大的计算能力，是因为仅用 n 个量子比特，它们就能影响 2ⁿ 个振幅的值。这一特性具有深远的影响。

从数学的角度来看，量子算法本质上是一个量子门电路，在最终测量之前变换一组复数（即振幅），最终测量时观察一个或多个量子比特的值（见图 14-3）。

![](img/ace4de942d037de8ea5835bc9fbe57cd_305_0.png)

图 14-3：量子算法原理

我们也把量子算法称为量子门阵列或量子电路。

### 量子门与矩阵乘法

与经典计算机的布尔门（AND、XOR 等）不同，量子门作用于一组振幅，就像矩阵与向量相乘一样。例如，要将最简单的量子门——恒等门——应用于量子比特 Φ，我们把 I 视为一个 2×2 恒等矩阵，并将其与由 Φ 的两个振幅组成的列向量相乘：

I|Φ⟩ = (1 0; 0 1) (i/√2; -1/√2) = (1×i/√2 + 0×(-1/√2); 0×i/√2 + 1×(-1/√2)) = (i/√2; -1/√2) = |Φ⟩

这个矩阵-向量乘法的结果是另一个包含两个元素的列向量，其中第一个值等于 I 矩阵的第一行与输入向量的点积（即第一元素 1 与 i/√2 的乘积加上第二元素 0 与 -1/√2 的乘积之和），第二个值同理。

恒等门 I 相当无用，因为它不做任何操作，使量子比特保持不变。

注意 在实践中，量子计算机不会显式地计算矩阵-向量乘法，因为矩阵会过于庞大。（这也是经典计算机无法模拟量子计算的原因。）相反，量子计算机将通过等效于矩阵乘法的物理变换，把量子比特作为物理粒子进行变换。感到困惑？以下是理查德·费曼的话：“如果你没有完全被量子力学搞糊涂，那你就不理解它。”

### 阿达马量子门

最有用的量子门之一是阿达马门，通常用 H 表示。你可以如下定义阿达马门（注意右下角位置的负值）：


```
$$H = \begin{pmatrix} 1/\sqrt{2} & 1/\sqrt{2} \\ 1/\sqrt{2} & -1/\sqrt{2} \end{pmatrix}$$
```

应用该门到量子比特 $|\Psi\rangle = (1/\sqrt{2}, 1/\sqrt{2})$ 得到以下结果：

```
$$H|\Psi\rangle = \begin{pmatrix} 1/\sqrt{2} & 1/\sqrt{2} \\ 1/\sqrt{2} & -1/\sqrt{2} \end{pmatrix}\begin{pmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \end{pmatrix} = \begin{pmatrix} 1/2 + 1/2 \\ 1/2 - 1/2 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \end{pmatrix} = |0\rangle$$
```

通过对 $|\Psi\rangle$ 应用哈达玛门 $H$，你得到量子比特 $|0\rangle$，其中 $|0\rangle$ 的振幅为 1，而 $|1\rangle$ 的振幅为 0。这说明该量子比特表现得是确定性的：如果观测这个量子比特，你总是会看到 0 而永远不会看到 1。换句话说，你失去了初始量子比特 $|\Psi\rangle$ 的随机性。

再次对量子比特 $|0\rangle$ 应用哈达玛门得到以下结果：

```
$$H|0\rangle = \begin{pmatrix} 1/\sqrt{2} & 1/\sqrt{2} \\ 1/\sqrt{2} & -1/\sqrt{2} \end{pmatrix}\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \end{pmatrix} = |\Psi\rangle$$
```

这会让你回到量子比特 $|\Psi\rangle$ 以及一个随机化状态。我们经常在量子算法中使用哈达玛门来实现从确定性状态到均匀随机状态的转换。

## 并非所有矩阵都是量子门

虽然可以将量子门的运算视为矩阵乘法，但并非所有矩阵都对应量子门。请回忆，量子比特由复数 $\alpha$ 和 $\beta$ 组成，它们是量子比特的振幅，满足条件 $|\alpha|^2 + |\beta|^2 = 1$。如果将量子比特与一个矩阵相乘后得到的两个振幅不满足该条件，则结果就不能是一个量子比特。量子门仅对应酉矩阵，它们保持性质 $|\alpha|^2 + |\beta|^2 = 1$。

酉矩阵（根据定义，量子门也是如此）是可逆的，这意味着给定运算的结果，你可以通过应用逆矩阵来计算出原始量子比特。这就是为什么量子计算是一种可逆计算。

## 量子加速

量子加速发生在量子计算机能够比经典计算机从根本上更快地解决某个问题时。例如，在经典计算机上在一个无序列表的 $n$ 个项目中搜索一个项目，平均需要 $n/2$ 次操作，因为你需要在找到目标项目之前查看列表中的每个项目。（平均而言，你会在搜索列表的一半后找到该项目。）没有任何经典算法能比 $n/2$ 做得更好。然而，存在一种量子算法只需 O(√n) 次操作即可搜索到一个项目，这比 n/2 小几个数量级。例如，如果 n 等于 1,000,000，则 n/2 为 500,000，而 √n 为 1,000。

我们用 *时间复杂度* 来量化量子算法与经典算法之间的差异，我们用 O() 表示法来表示。在前面的例子中，量子算法的运行时间为 O(√n)，但经典算法不可能快于 O(n)。由于这种时间复杂度的差异源于平方指数，我们称之为 *二次加速*。虽然这种加速很可能带来差异，但还有更强大的加速。

## 指数加速与西蒙问题

*指数加速* 是量子计算的圣杯。它们发生在某个任务在经典计算机上需要指数级时间，例如 O(2^n)，而在量子计算机上可以用多项式复杂度完成的情况——即对于某个固定数 k 为 O(n^k)。这种指数加速可以将一个实际上不可能完成的任务变成可能完成的任务。（请回顾第 9 章，密码学家和复杂性理论家将指数时间与不可能联系起来，而将多项式时间与实用联系起来。）

指数加速的典型代表是 *西蒙问题*。在这个计算问题中，一个函数 f() 将 n 位字符串转换为 n 位字符串，使得 f() 的输出看起来像一个随机的 n 位字符串，但有一个约束：存在一个秘密值 m，使得对于任意两个值 x、y，我们有 f(x) = f(y) 当且仅当 y = x ⊕ m。西蒙问题在于在对 f() 有黑盒访问的情况下找到 m。

用经典算法解决西蒙问题归结为寻找碰撞，即找到值 x 和 y 使得 f(x) = f(y)。这大约需要 2^{n/2} 次对 f() 的查询。然而，图 14-4 显示量子算法只需大约 n 次查询即可解决西蒙问题，其时间复杂度极高效，为 O(n)。

![](img/ace4de942d037de8ea5835bc9fbe57cd_307_0.png)

*图 14-4：高效解决西蒙问题的量子算法电路*

在解决西蒙问题的量子电路中，你将 2n 个量子比特初始化为 |0⟩，对前 n 个量子比特应用哈达玛门（H），然后对两个各含 n 个量子比特的组应用门 Q_f。给定两个 n 量子比特组 x 和 y，门 Q_f 将量子态 |x⟩|y⟩ 变换为态 |x⟩|f(x) ⊕ y⟩。也就是说，它以可逆的方式在量子态上计算函数 f()，因为你可以通过计算 f(x) 并将其与 f(x) ⊕ y 进行异或来从新态回到旧态。（解释其工作原理超出了本书范围。）

你只能在非常特定的情况下将西蒙问题的指数加速用于对称密码，但下一节将讨论量子计算的一些真正的加密杀手级应用。

## 肖尔算法的威胁

1995 年，AT&T 研究员彼得·肖尔发表了一篇发人深省的文章，题为“Polynomial-Time Algorithms for Prime Factorization and Discrete Logarithms on a Quantum Computer。”肖尔算法是一种量子算法，在求解因子分解、离散对数（DLP）和椭圆曲线离散对数（ECDLP）问题时带来指数加速。你无法用经典计算机高效解决这些问题，但可以用量子计算机解决。这意味着量子计算机可以解决任何依赖于这些问题的加密算法，包括 RSA、Diffie–Hellman、椭圆曲线密码学，以及大多数当前部署的公钥密码机制（除已转向后量子密码学的那些外）。换句话说，你可以将 RSA 或椭圆曲线密码学的安全性降低到凯撒密码的水平。（肖尔完全可以把他的文章标题定为“Breaking All Public-Key Crypto on a Quantum Computer。”）著名复杂性理论家斯科特·阿伦森称肖尔算法为“one of the major scientific achievements of the late 20th century。”

肖尔算法实际上解决的问题类比因子分解和离散对数更一般。具体来说，如果一个函数 f() 是周期性的——也就是说，存在一个 ω（周期）使得对任意 x 都有 f(x + ω) = f(x)——那么肖尔算法将高效地找到 ω。（这看起来与西蒙问题非常相似，因为它是肖尔算法的重要灵感来源。）

讨论肖尔算法如何实现其加速的细节对于本书来说过于技术化，但下一节将展示如何使用肖尔算法解决因子分解和离散对数问题（see Chapter 9），即 RSA 和 Diffie–Hellman 背后的难题。

## 因式分解问题

假设你想对一个大数 N = pq 进行因式分解。如果能计算 a^x mod N 的周期，则很容易对 N 进行因式分解，其中 a 为某个常数。这个任务对经典计算机来说很难，但对量子计算机来说很容易。首先选择一个小于 N 的随机数 a，并让肖尔算法找到函数 f(x) = a^x mod N 的周期 ω。一旦找到周期，你将有 a^x mod N = a^{x + ω} mod N（即 a^x mod N = a^x a^ω mod N），这意味着 a^ω mod N = 1，或等价地 a^ω − 1 mod N = 0。换句话说，a^ω − 1 是 N 的倍数，意味着 a^ω − 1 = kN，其中 k 为某个未知数。

当 ω 为偶数时，很容易将 a^ω − 1 分解为 (a^(ω/2) − 1)(a^(ω/2) + 1)，其中值 a^(ω/2) 是单位根，因为 (a^(ω/2))^2 mod N = 1。当周期 ω 为奇数时，用另一个 a 值重新运行肖尔算法，直到得到偶数。

由于 a^ω − 1 的因子包含 k 和 N 的素因子，你可以在 a^(ω/2) − 1 和 a^(ω/2) + 1 的因子中找到这些因子。然后你可以计算 a^(ω/2) − 1 与 N 之间的最大公约数（GCD），以及 a^(ω/2) + 1 与 N 之间的最大公约数，以获得 N 的非平凡因子——即除 1 或 N 之外的数值。如果不是这种情况——例如当 a^(ω/2) − 1 或 a^(ω/2) + 1 是 N 的倍数时——用另一个 a 重新开始攻击。

获得 N 的因子后，你现在已从其公钥中恢复了 RSA 私钥，从而能够解密加密消息或伪造签名。

请注意，用于对数 N 进行因式分解的最佳经典算法运行时间为 n 的指数级，其中 n 为 N 的比特长度（即 n = log₂ N）。然而，肖尔算法的运行时间为 n 的多项式——即 O(n²(log n)(log log n))。这意味着如果拥有量子计算机，你可以在比数千年更合理的时间内运行肖尔算法并看到结果。

## 离散对数问题

离散对数问题的挑战在于给定 y = g^x mod p，求出 x，其中 g 和 p 为已知数。解决这个问题在经典计算机上需要（亚）指数级时间，但由于其高效的周期查找技术，你可以用肖尔算法轻松找到 x。

例如，考虑函数 f(a, b) = g^(a^y^b)。假设你想找到该函数的周期，即数 ω 和 ω'，使得对任意 a 和 b 都有 f(a + ω, b + ω') = f(a, b)。你所求的解则是 x = −ω/ω' modulo q，其中 q 是 g 的阶，是一个已知参数。等式 f(a + ω, b + ω') = f(a, b) 意味着 g^(a^ω y^ω') mod p = 1。将 y 替换为 g^x 后，你得到 g^(ω + x ω') mod p = 1，这等价于 ω + x ω' mod q = 0，由此可推导出 x = −ω/ω'。

同样，总复杂度为 O(n²(log n)(log log n))，其中 n 为 p 的比特长度。该算法可推广到在任何有限交换群中寻找离散对数，而不仅仅是模素数数的群。因此，你也可以将其应用于解决 ECDLP，即离散对数问题的椭圆曲线版本。

## 格罗弗算法

另一种重要的量子加速形式是在与 n 的平方根成比例的时间内搜索 n 个项目，而任何经典算法所需时间都与 n 成比例。这种二次加速得益于格罗弗算法，这是一种于 1996 年发现的量子算法。我不会介绍格罗弗算法的内部原理，因为它们


## 为什么建造量子计算机如此困难？

尽管量子计算机原则上是可以建造的，但我们不知道难度有多大，也不知道何时能实现（如果真能实现的话）。截至2024年年中，纪录保持者是一台拥有1,121个量子比特的机器（IBM的“Condor”），而要破解任何密码，我们需要让数百万个量子比特稳定运行数周。重点是，我们还没做到。

建造量子计算机的困难源于需要极其微小的物体来充当量子比特——比原子还小，比如光子。由于量子比特必须如此微小，它们也极其脆弱。

此外，量子比特必须保持在极低的温度（接近绝对零度）才能保持稳定。即使在冰点温度下，量子比特的状态也会衰减，最终变得毫无用处。截至本文撰写之时，我们还不知道如何制造能持续超过几秒钟（相干时间）的量子比特。

另一个挑战是，环境（如热量和磁场）会影响量子比特的状态并导致计算错误。理论上，纠正这些错误是可能的，但实际操作起来很困难。纠正量子比特的错误需要量子纠错码，而量子纠错码又需要许多额外的量子比特和足够低的错误率。

目前，形成量子比特主要有两种方法：超导电路和离子阱。谷歌和IBM的实验室倡导使用超导电路，其原理是将量子比特构造成微小的电路，这些电路依赖超导材料中的量子现象，其中电荷载流子是电子对。由超导电路制成的量子比特寿命非常短。

离子阱由离子（带电原子）组成，并使用激光操纵，以将量子比特制备到特定的初始状态。离子阱往往比超导电路更稳定，但操作速度较慢，且似乎更难扩展规模。

建造量子计算机确实是一项“登月”级别的努力。挑战归结为：1）构建一个包含少量量子比特的系统，该系统稳定、容错，并且能够应用基本的量子门；2）将这样的系统扩展到数千或数百万个量子比特，使其具有实用价值。从纯粹的物理角度来看，并且据我们所知，没有任何事物能够阻止大规模容错量子计算机的诞生。但许多事情在理论上可行，在实践中却很难或成本过高（比如安全计算机）。未来将告诉我们谁是对的——是量子乐观主义者（预测十年内会出现大型量子计算机），还是量子怀疑论者（认为人类永远看不到量子计算机）。

如前所述，截至2024年1月，最先进的成果之一是IBM的量子计算芯片Condor，它包含1,121个量子比特，这是一种基于超导电路的技术。但在比较量子计算系统时，量子比特的数量不应成为唯一指标。其他重要因素包括稳定时间、纠缠在一起的量子比特数量以及可靠纠错的能力。

为了使用线性码加密数据，McEliece密码系统将G构造为三个矩阵的秘密组合，并通过计算w = vG加上某个随机值e（其中有一定数量的位设置为1）来加密。这里，G是公钥，私钥由矩阵A、B和C组成，使得G = ABC。知道A、B和C，就可以可靠地解码消息并恢复w。但如果没有这些矩阵，就无法解码该码字，从而无法解密。

McEliece加密方案的安全性依赖于在信息不足的情况下解码线性码的困难性，这是一个我们知道是NP-hard的问题，因此量子计算机无法解决。然而，请记住，一个问题即使是NP-hard，也并不意味着它的所有实例在实践中都无法解决。因此，有必要评估密码系统所呈现的困难问题的哪些实例，以及这些实例是否始终困难。经过密码学家和编码理论专家多年的分析，McEliece密码满足这一标准。

## 基于格的密码学

格是一种数学结构，本质上由n维空间中的一组点组成，具有一定的周期结构。例如，图14-5展示了如何将二维（n = 2）格视为一组点。

![](img/ace4de942d037de8ea5835bc9fbe57cd_313_0.png)

图14-5：二维格的点，其中v和w是格的基向量，s是距星形点最近的向量

格理论催生了看似简单却极具迷惑性的密码方案。我来给你讲讲要点。

短整数解（SIS）是基于格的密码学中的一个困难问题，即在给定(A, b)的情况下，找到n个数的秘密向量s，使得b = As mod q，其中A是一个随机的m×n矩阵，q是一个素数。

基于格的密码学中的另一个困难问题是带误差学习（LWE），即在给定(A, b)的情况下，找到n个数的秘密向量s，其中b = As + e mod q，A是一个随机的m×n矩阵，e是一个随机噪声向量，q是一个素数。这个问题与基于编码的密码学中的含噪解码非常相似。

SIS和LWE在某种程度上是等价的，我们可以将它们重述为格上的*最近向量问题（CVP）*实例，即通过组合一组基向量来找到格中距离给定点最近的向量。图14-5中的虚线向量*s*展示了如何通过组合基向量*v*和*w*来找到距星形点最近的向量。

人们认为，CVP和其他格问题对于经典计算机和量子计算机来说都是困难的。但这并不能直接推广到安全的密码系统，因为某些问题只有在最坏情况下（即对于其最难的实例）才是困难的，而不是在平均情况下（这才是我们加密所需的）。此外，虽然找到CVP的精确解很困难，但找到解的近似值可能要容易得多。

尽管如此，基于格的后量子密码系统已被证明能够提供安全性和性能的最佳组合。NIST在2022年选择的标准主要来自这一家族，稍后你将看到。

## 多元密码学

*多元密码学*专注于构建这样的密码方案：其破解难度等同于求解多元方程组，即涉及多个未知数在方程中相乘的方程组。例如，考虑以下包含四个未知数*x₁, x₂, x₃, x₄*的方程组：

x₁x₂ + x₃x₄ + x₂ = 1  
x₁x₃ + x₁x₄ + x₂x₃ = 12  
x₁² + x₃² + x₄ = 4  
x₂x₃ + x₂x₄ + x₁ + x₄ = 0

这些方程由若干项之和组成，这些项要么是单个未知数（如*x₄*，即一次项），要么是两个未知数的乘积（如*x₂x₃*，即二次项或*二次*项）。要解这个方程组，你需要找到满足所有四个方程的*x₁, x₂, x₃, x₄*的值。方程可以定义在所有实数、整数或有限数集上。然而，在密码学中，方程通常定义在模某个素数的数上或二进制值（0和1）上。

这里的困难问题是求解随机二次系统，这被称为*多元二次问题（MQ）*。该问题是**NP-hard**的，因此是后量子系统的潜在基础，因为量子计算机无法高效解决**NP-hard**问题。

不幸的是，在MQ之上构建密码系统并非如此直接。例如，如果你将MQ用于签名，私钥可能由三个方程组组成：*L₁, N*和*L₂*。按此顺序组合它们会得到另一个方程组，称为*P*，即公钥。依次应用变换*L₁, N*和*L₂*（即根据方程组转换一组值）就等价于



要通过将 $x_1$, $x_2$, $x_3$, $x_4$ 变换为 $y_1$, $y_2$, $y_3$, $y_4$ 来应用 $P$，例如定义如下：

$$\begin{aligned}
y_1 &= x_1x_2 + x_3x_4 + x_2 \\
y_2 &= x_1x_3 + x_1x_4 + x_2x_3 \\
y_3 &= x_1^2 + x_3^2 + x_4 \\
y_4 &= x_2x_3 + x_2x_4 + x_1 + x_4
\end{aligned}$$

在这样的密码系统中，选取 $L_1$、$N$ 和 $L_2$，使得 $L_1$ 和 $L_2$ 是可逆的线性变换（即其方程中的项只相加、不相乘），而 $N$ 是一个也可逆的二次方程组。这使得三者的组合成为一个可逆的二次系统，但在不知道 $L_1$、$N$ 和 $L_2$ 各自的逆的情况下，很难确定该组合的逆。

计算签名时，先计算 $L_1$、$N$、$L_2$ 的逆并作用于某个消息 $M$——我们将消息看作变量序列 $x_1$, $x_2$, . . . ：

$$S = L_2^{-1}\left(N^{-1}\left(L_1^{-1}(M)\right)\right)$$

验证签名时，只需要验证 $P(S) = M$。

如果攻击者设法计算出 $P$ 的逆，或从 $P$ 中求出 $L_1$、$N$、$L_2$，就能攻破这种密码系统。解决此类问题的实际难度取决于方案的参数，例如所用方程的个数以及数字的大小和类型。但选择安全的参数是困难的，而且不止一个“安全”的多变量方案已经被攻破。

由于难以在安全性与性能之间实现可靠的权衡，多变量密码学并未在主要应用中使用。不过，多变量签名方案的一个实际好处是它们能产生很短的签名。

## 基于哈希的密码学

与前述方案不同，基于哈希的密码学建立在密码哈希函数成熟的安全性之上，而不是数学问题的难度之上。量子计算机无法攻破哈希函数，因此也无法攻破任何依赖寻找碰撞或原像之难度的方案，而这正是基于哈希函数的签名方案的核心思想。

基于哈希的密码方案相当复杂，所以我们先看看它们最简单的构建模块：*Winternitz 一次性签名（WOTS）*，这是大约在 1979 年发现的一个技巧。这里的*一次性*意味着你只能用一把私钥签署一条消息；否则签名方案将变得不安全。（你可以将 WOTS 与其他方法结合来签署多条消息，稍后你会看到。）

假设你想签署一条消息，并将其看作 0 到 $w - 1$ 之间的一个数，其中 $w$ 是方案的某个参数。私钥是一个随机字符串 K。要签署满足 0 ≤ M < w 的消息 M，计算 Hash(Hash( . . (Hash(K))))，其中哈希函数 Hash 重复 M 次。你将这个值记为 Hash^M(K)。公钥是 Hash^w(K)，即从 K 开始对 Hash 进行 w 次嵌套迭代的结果。

验证 WOTS 签名 S 的方法是检查 Hash^{w-M}(S) 是否等于公钥 Hash^w(K)。注意，S 是对 K 应用 M 次 Hash 后得到的值，因此如果你再应用 w-M 次 Hash，得到的值等于 K 被哈希 M + (w-M) = w 次的结果，也就是公钥。

该方案有重大局限：

**攻击者可以伪造签名** 从消息 M 的签名 Hash^M(K)，你可以计算 Hash(Hash^M(K)) = Hash^{M+1}(K)，这是消息 M + 1 的有效签名。你可以通过不仅签署 M、还使用第二个密钥签署 w-M 来解决这个问题。

**它只适用于短消息** 如果消息长度为 8 位，那么最多有 2^8 - 1 = 255 条可能消息，因此你必须计算 Hash 最多 255 次才能生成签名。这对短消息也许可行，但对更长的消息则不可行——例如，对于 128 位消息，签署 2^128 - 1 会花去极长时间。一种变通方法是将较长的消息拆分成较短的块，并分别签署每个块。

**它只能使用一次** 如果你用一把私钥签署多条消息，攻击者就能恢复足够的信息来伪造签名。例如，如果 w = 8，并且你使用前面的技巧签署数字 1 和 7 以避免平凡伪造，攻击者会得到 Hash^1(K) 和 Hash^7(K') 作为 1 的签名，以及 Hash^7(K) 和 Hash^1(K') 作为 7 的签名。从这些值，攻击者可以计算 [1;7] 中任意 x 的 Hash^x(K) 和 Hash^x(K')，从而以 K 和 K' 所有者的身份伪造签名。这个问题没有简单的解决办法。

最先进的基于哈希的方案依赖于比 WOTS 更复杂的版本，并结合树形数据结构以及专门设计用不同密钥签署不同消息的复杂技术。不幸的是，由此产生的方案会产生很大的签名（大约几十 KB，例如 SPHINCS+，它是 NIST 在 2022 年选择标准化的签名算法之一）。

你还应该注意有状态与无状态签名方案之间的区别。SPHINCS+ 是无状态的，而 XMSS 是有状态的，因为它需要维护一个计数器。有状态性大大简化了算法设计，但迫使使用者在使用算法时维护计数器之类的状态。

最后，请注意，仅依赖哈希函数的公钥构造可以提供签名方案，但不能提供加密。

## NIST 标准

2017 年，NIST 组织了一场公开竞赛，以确定适合加密和签名的后量子算法标准。与之前产生 AES（Rijndael）和 SHA-3（Keccak）的竞赛一样，NIST 的后量子密码标准化项目邀请密码学家提交算法，并对其他提交者的算法进行密码分析，以将它们淘汰出竞赛。

NIST 收到了 69 份提交方案，其中大多数是基于格的。其中有 26 份进入了第二轮。2020 年 7 月，NIST 选出了 7 个入围算法和 8 个备选算法。2022 年 7 月，NIST 公布了首批四项标准：

**CRYSTALS-Kyber** 一种基于格的*密钥封装机制（KEM）*，这种原语可以看作一种用于秘密密钥的加密方案。它可以用于加密数据（在混合方案中，对称密码实际上使用由 KEM 加密的密钥来加密数据），并且可以用于密钥协商，方式与 Diffie–Hellman 协议类似。

**CRYSTALS-Dilithium** 一种基于格的签名方案，由与 CRYSTALS-Kyber 相同的团队设计。

**Falcon** 一种基于格的签名方案，所使用的技术和假设与 Dilithium 略有不同。

**SPHINCS+** 一种基于哈希的签名方案，因此是其中唯一不基于格的算法。

NIST 就同时拥有两种基于格的签名方案发表了如下声明：

> [这两者]都因其强大的安全性和出色的性能而入选，NIST 预计它们能在大多数应用中表现良好。
> Falcon 也将由 NIST 标准化，因为有些用例中 CRYSTALS-Dilithium 的签名可能太大。

最短的 Dilithium 签名大约为 2KB，而 Falcon 的签名长度只有它的一半。NIST 还表示，它将 SPHINCS+ 标准化，“以避免签名仅仅依赖格的安全性”。

在撰写本文时，Kyber、Dilithium 和 SPHINCS+ 的草案标准已分别以 FIPS 203（基于模块格的密钥封装机制标准）、FIPS 204（基于模块格的数字签名标准）和 FIPS 205（无状态基于哈希的数字签名标准）的形式在 FIPS 系列下发布，而 Falcon 的标准预计会稍晚发布。

这些后量子算法预计将首先以混合模式使用，与经典的非抗量子算法相结合，以对冲弱点风险。例如，Kyber 通常与 X25519（依赖 Curve25519 的 Diffie–Hellman 方案）结合使用来保护 TLS 连接。

NIST 还宣布有四种算法晋级“第四轮”。其中包括三种基于编码的加密方案：BIKE、Classic McEliece 和 HQC。基于同源的 SIKE 在公告后不久被发现可被完全攻破，因而退出了竞赛。

NIST 于 2022 年夏天启动了一个新项目，以寻找更多的后量子签名方案，并表示“那些不...


“基于结构化格的是最受关注的”，并期望提交“短签名和快速验证”。2023年6月，NIST收到了50份提交，包括11份多变量方案、7份基于格的方案、6份基于编码的方案、2份基于哈希的方案，以及7份使用MPC-in-the-head的方案。这种新兴技术将多方计算（MPC）协议转化为零知识证明知识——即一个数据片段，其验证对应于签名的验证。所提出的方案数量和多样性将导致新的攻击和新的攻击技术，并有望带来可靠的标准。

## 事物可能出错的方式

后量子密码学可能从根本上比RSA或椭圆曲线密码学更强，但它并非无懈可击或无所不能。我们对后量子方案及其实现的安全性理解比其他情况更有限，这带来了更大的风险。

### 安全级别不明确

后量子方案可能看起来具有欺骗性的强，但对量子和经典攻击都证明不安全。基于格的算法，例如环-LWE族的计算问题（使用多项式的LWE问题的版本），有时存在问题。环-LWE对密码学家具有吸引力，因为我们可以利用它构建原则上与求解环-LWE问题最困难实例一样难以破解的密码系统，而这些实例可能是NP难的。但当安全性看起来好得不像真的时，往往就是如此。

安全证明通常是渐近的，这意味着它们仅对底层格的维度等大参数值成立。然而，实践中使用的参数要小得多。即使基于格的方案看起来与某些NP难问题一样难以破解，其安全性仍然难以量化。就基于格的算法而言，由于对这些近期构造缺乏理解，我们很少能清楚地了解针对它们的最佳攻击以及此类攻击在计算或硬件方面的成本。这种不确定性使得基于格的方案更难与RSA等更好地理解的构造进行比较。然而，研究人员在这方面取得了进展，理想情况下几年后，格问题将像RSA一样被很好地理解。（有关环-LWE问题的更多技术细节，请阅读Peikert在 https://eprint.iacr.org/2016/351 的优秀综述。）

### 大型量子计算机的最终出现

想象一下2048年4月2日左右的CNN头条：“ACME, Inc. reveals its secretly built quantum computer, launches break-crypto-as-a-service platform.” 好吧，RSA和椭圆曲线密码学完蛋了。那现在怎么办？

底线是后量子加密比后量子签名重要得多。我们先来看签名的例子。如果你仍在使用RSA-PSS或ECDSA作为签名方案，你可以使用后量子签名方案签发新签名来恢复你签名的信任。你将撤销旧的、量子不安全的公钥，并为你签署的每条消息计算新的签名。经过一番工作后，你会没事的。

你只有在用量子不安全的方案（如RSA-OAEP）加密数据时才有理由恐慌。在这种情况下，所有传输的密文都可能被破坏，因此用后量子算法重新加密该明文毫无意义，因为你数据的保密性已经丧失。

但是密钥协商呢，使用Diffie–Hellman（DH）及其椭圆曲线对应物（ECDH）？乍一看，情况看起来与加密一样糟糕：攻击者收集了公钥 $g^a$ 和 $g^b$ 后，可以利用他们闪亮的新量子计算机计算出秘密指数 $a$ 或 $b$ 并计算共享密钥 $g^{ab}$，然后从中推导出加密你流量的密钥。但实际上，Diffie–Hellman并不总是以如此简单的方式使用。实际加密你数据的会话密钥可能同时由Diffie–Hellman共享密钥和系统的某些内部状态派生而来。这就是最先进的移动消息系统的运作方式，得益于Signal应用开创的协议。当你用Signal向同伴发送新消息时，它会计算一个新的Diffie–Hellman共享密钥，并将其与依赖于该会话中先前发送的消息（可能跨越很长时间）的内部秘密结合起来。这种先进的Diffie–Hellman使用方式即使在量子计算机面前也使攻击者的工作变得困难得多。

### 实现问题

实际上，后量子方案由代码组成——在某些物理处理器上运行的软件，而不仅仅是抽象算法。无论算法在纸面上多么强大，它们都不会免受实现错误、软件漏洞或侧信道攻击的影响。一种算法在理论上可能完全是后量子的，但在实现后仍可能被破坏——例如，由经典计算机程序破坏，因为程序员忘记输入分号。

此外，诸如基于编码和基于格的算法等方案严重依赖数学运算，其实现使用了各种技巧来使这些运算尽可能快。同理，这些算法代码的复杂性使其更容易受到侧信道攻击，例如基于执行时间测量来推断秘密值信息的时序攻击。事实上，我们已经将此类攻击应用于基于编码的加密（参见 https://eprint.iacr.org/2010/479）以及基于格的签名方案（参见 https://eprint.iacr.org/2016/300）。

具有讽刺意味的是，由于其实现中潜在的漏洞，后量子方案在实践中最初可能比非后量子方案更不安全。

## 进一步阅读

要学习量子计算的基础，请阅读Michael Nielsen和Isaac Chuang的经典著作 *量子计算与量子信息（纪念版）*（剑桥，2011）。Scott Aaronson的 *自德谟克利特以来量子计算*（剑桥，2013）读起来技术性较弱、更有趣，涵盖的内容远不止量子计算。

有几个软件模拟器允许你实验量子计算，例如量子计算游乐场 *https://www.quantumplayground.net* 或IBM的平台 *https://quantum.ibm.com*。这些网站相对易于使用，得益于直观的可视化。

要了解后量子密码学的最新研究，请参阅 *https://pqcrypto.org* 以及相关的会议PQCrypto。

未来的几年对于后量子密码学来说有望特别令人兴奋，得益于NIST后量子密码学标准化项目的持续进行以及后量子解决方案的大规模部署。

### 15 加密货币密码学

![](img/ace4de942d037de8ea5835bc9fbe57cd_322_0.png)

本章在本书2017年秋季首次出版时并不存在，那时加密货币和区块链正处于炒作高峰。虽然区块链尚未完全兑现颠覆多个行业的承诺，但它对密码学研究和工程产生了深远影响。区块链应用带来了令人兴奋的新问题，吸引了新鲜人才，并提供了一种将理论与实践联系起来的新颖方式。

在“crypto”成为加密货币同义词之前，密码学算法和协议主要涉及加密和安全通道等标准功能。更晦涩的协议仅限于小众研究领域和技术文章，通常迎合研究者的兴趣，仅在学术会议上发表。

新算法主要由学术研究人员设计，如果有的话，至少在同行评审和分析五年之后，以及在大量详细说明未成功密码分析尝试的研究论文之后，才会部署到现实世界。

区块链颠倒了这一过程。就像Signal和Tor的密码学协议绕过了传统的学术路线一样，区块链爱好者受传统束缚较少。开创性的协议通常首先在博客文章或非正式白皮书中亮相，随后很快实现。偶尔，他们甚至完全放弃书面规范，让代码自己说话。只有在广泛采用之后，学术界才会注意到。最著名的例子是比特币协议，它在部署前并未经过正式的同行评审。

许多资深研究人员在区块链领域发现了新颖的挑战，经常直接与区块链实体合作。他们开发了复杂的协议，这些协议不仅推动了边界、获得了同行认可，而且还实现了快速的现实世界部署，影响了成千上万甚至数百万系统。典型例子包括高效的ECDSA阈值签名方案和零知识证明系统。在某些情况下，实用性不大的现有协议找到了有影响力的用例，例如Boneh–Lynn–Shacham（BLS）签名。

本章概述了这些密码学算法和协议——那些为区块链量身定制的以及因区块链而蓬勃发展的。我不会深入定义区块链或其工作原理，因为网上资源众多。相反，我强调支撑区块链的密码学方案，这些方案无论区块链用例如何都具有重要意义。即使你对区块链现象仍持怀疑态度，我相信你会发现本章富有启发性。

### 哈希应用

哈希函数，密码学的瑞士军刀，在区块链系统中发挥众多作用，包括：

- 哈希交易数据

  哈希函数可以生成由交易发行者签名的摘要，通常使用ECDSA-secp256k1或Ed25519。验证签名可确保给定地址的所有者批准了被哈希的信息，从而将交易纳入链的账本。

  在区块链以太坊中，交易的哈希充当其唯一标识符；例如，你可以在 https://etherscan.io 的搜索字段中输入哈希以检索相关交易。以太坊交易哈希使用Keccak-256——与SHA3-256相似但不完全相同——以及RLP编码的数据。该数据包括接收者地址、发送的以太币数量（代码ETH）、任何智能合约输入、gas价格和限制、nonce（每个新交易递增）以及交易的签名。



## 对区块内容进行哈希处理

哈希函数可以将摘要包含在后续区块中，从而将区块“链接”起来。例如，每个比特币区块都有一个区块头，其中包含前一区块的哈希、记录交易的树形哈希以及一些元数据（版本、时间戳、随机数等）。比特币通过使用双重 SHA-256（即 SHA-256(SHA-256(区块头))）对前一区块的区块头进行哈希，来计算前一区块的哈希。这种非正统的构造消除了长度扩展攻击的风险，并在 SHA-256 被发现不安全的情况下增加了一道安全网——尽管这种可能性很小。

除了这些基本用例之外，哈希函数还是区块链系统关键组件的主要构建模块。

## 梅克尔树

梅克尔树是哈希树的一种类型，哈希树是一种根据树形模式从叶子值计算根值的数据结构。在哈希树中，父节点通过对子节点进行哈希来计算。例如，梅克尔树被用来创建比特币区块的区块头。它们以计算机科学家拉尔夫·梅克尔的名字命名，他 1979 年的密码学方案构造使用了二叉哈希树。

## 树形哈希计算

梅克尔树以构成其叶子的值作为输入，即用于计算根（输出）的值。通常，你绘制数据结构树时，根在顶部，叶子在底部。

例如，图 15-1 展示了对四个值（A、B、C、D）进行哈希的梅克尔树。

![](img/ace4de942d037de8ea5835bc9fbe57cd_324_0.png)

图 15-1：哈希树，其中叶子是输入，根是输出

树形哈希的工作方式如下：
- 对四个值分别进行哈希，得到四个哈希值 H(A)、H(B)、H(C) 和 H(D)。
- 将每一对连续的哈希值一起哈希，得到 H(H(A) || H(B)) 和 H(H(C) || H(D))。这里，你连接这些哈希值（如 `||` 符号所表示）。
- 将这两个哈希值一起哈希，得到树的根，即树形哈希的最终输出：H(H(H(A) || H(B)) || H(H(C) || H(D)))。

如果省略对输入值的初始哈希（仅当输入值不是哈希大小所必需时），你会从四个值通过两层高的树得到四个值中的一个，高度为二。请注意，虽然输入数据可能大小不同，但所有哈希值的大小相同。通常，n 层的树有 2^n 个叶子，允许你通过从（已哈希的）叶子计算 2^n − 1 个哈希来处理最多 2^n 个值。

如果输入值的数量不是某个整数 n 的 2^n 形式，一种常见技术是添加填充值（例如，设置为零或列表中的最后一个值）；不过，填充规则应仔细选择，以避免琐碎的碰撞。

## 梅克尔证明

梅克尔树的结构可以用来证明给定值属于被哈希的 2^n 个值列表之一，而无需重新计算整棵树（这需要大约 2^n 次操作），只需要与树的高度（即层数 n）成比例的时间。根据上下文的不同，这类证明被称为成员路径、包含证明或梅克尔证明。这是梅克尔树的杀手锏特性，而通用哈希函数并不具备这一点。

图 15-2 展示了其工作原理。阴影单元格是足以证明 V_1 是用于计算根的哈希值之一的值。

![](img/ace4de942d037de8ea5835bc9fbe57cd_326_0.png)

图 15-2：梅克尔树，其中阴影单元格构成 A 的成员路径

假设你想证明 A 是被哈希的值之一，同时不透露 B、C 或 D。首先，对 A 进行哈希以获得哈希树的实际叶子。然后，假设你已经收到 A 的成员路径，该路径由其他阴影值 H(B) 和 H(H(C) || H(D)) 组成。为了验证 A 属于该树，请计算以下内容：
- X = H(H(A) || H(B))，因为你已知 A 和 H(B)
- H(H(X) || H(H(C) || H(D)))，因为你已知 H(H(C) || H(D))

证明 A 的包含关系只需要对兄弟值进行两次哈希，即哈希次数等于树的高度。具有八个叶子的树高度为三；因此，成员路径验证需要三个兄弟哈希。16 个叶子时则需要四个兄弟哈希，依此类推，具有 2^n 个叶子的树需要 n 个兄弟哈希。

区块链应用经常使用梅克尔树将交易哈希成单个梅克尔根，例如包含在比特币区块头中的那个根。一个典型的比特币区块包含约 2,000 笔交易，这需要高度为 11（2^11 = 2,048）的树。在这种情况下，从叶子（每个叶子是交易数据的哈希）计算根需要 2,048 − 1 = 2,047 个兄弟哈希。每个哈希计算一次双重 SHA-256，因此对于 2,048 笔交易，需要 2,047 + 2,048 = 4,095 次双重 SHA-256，即调用 SHA-256 8,190 次。

以太坊使用一种稍微复杂的基于树的数据结构，将梅克尔树与帕特里夏前缀树（注意这不是笔误；“trie”来自“检索”（retrieval））相结合，这是一种存储键值对的树状结构。这种结构服务于以太坊基于状态的模型，该模型与比特币的 UTXO（未花费交易输出）模型差异很大，而后者使用更简单的梅克尔树就足够了。

## 工作量证明

工作量证明（PoW）可以说是区块链共识协议中最关键的组成部分——对于那些基于 PoW 而非权益证明（PoS）或其他协议的区块链而言。

PoW 本质上是一个哈希函数，它接受一些固定输入和可变输入，其结果必须匹配特定模式才有效。旨在解决 PoW 的参与方反复使用不同的可变输入值计算哈希，直到结果满足某个约束条件。

例如，在比特币和其他一些基于 PoW 的区块链中，约束条件是：将哈希值视为一个 256 位数字时，它必须小于给定数字。这也可以看作是哈希值具有给定数量的前导零，当将哈希视为 256 位数字的大端编码时。

例如，在 2022 年，比特币的最高难度值（根据 https://btc.com/stats/diff 的报告）为 34,244,331,613,176，约为 2^45。你将该值乘以 2^32 来找到哈希必须小于的实际值，即 2^77。对于每个区块，所有网络参与者（矿工）共同计算大约 2^77 次双重 SHA-256，以找到 PoW 的解决方案。这样的解决方案由一个随机数（PoW 哈希输入的可变部分）组成，该随机数产生的哈希值小于 2^77。PoW 哈希输入的固定部分由区块头值（版本、前一区块哈希、梅克尔树根、时间戳和难度目标值）组成。

如果没有 PoW 来“减缓”区块链中区块的产生，新的有效区块可能瞬时生成，这意味着交易历史可以被随意生成和重新创建。那样就不可能实现最终性（即保证一个区块及其包含的一组交易一旦被网络接受就不能被撤销或更改）。尤其不可能保护网络免受双重花费的影响，即同一笔币在两个不同交易中被花费。

并非所有 PoW 方案都像比特币那样简单，后者使用通用哈希函数（SHA-256）。一些 PoW 试图使其在专用硬件上的计算效率低于通用 CPU，以阻止那些投资于优化硬件矿机技术的组织集中挖矿——而不是任何人都能使用的现成服务器和计算机。已实现的技巧包括以下内容：
- 内存硬性：你可以通过通常生成大型表并以不可预测的地址访问来强制 PoW 使用大量内存。例如，以太坊的 PoW 使用了 Ethash 算法，该算法需要大约 4GB 内存。（2022 年 9 月，以太坊放弃了 Ethash，并从 PoW 机制切换到了权益证明机制。）
- 虚拟机：像某些恶意软件那样，你可以创建一组自定义的计算机指令，这些指令将由虚拟机应用程序转换为标准指令，同时还有可能使用大内存。




计算工作量证明（PoW）解决方案所需的内存量。这正是Monero区块链所采用的PoW算法RandomX的方法。

## 分层密钥派生

区块链用户通常希望管理多个账户，每个账户包含一个密钥对，其中：

- *私钥*必须保密，因为它是签署交易和从账户转移资金所需的签名密钥。
- *公钥*必须公开，因为它用于验证交易的签名。它也是派生账户地址的值。例如，比特币使用 SHA-256 和 RIPEMD-160 哈希的组合从公钥派生地址。注意，在某些区块链（如比特币）中，公钥在账户发起交易之前并不公开。

为了可靠地管理所有这些密钥，区块链开发者定义了*分层确定性钱包（HD钱包）*，与必须为每个新账户生成并备份全新的随机密钥相比，这让密钥管理不再那么繁琐且风险更低。

使用HD钱包，你生成并存储一个秘密，即*种子*（也叫*主密钥*或*熵*）。这个种子是唯一随机生成的值，也是唯一提供熵或不确定性，并因此为从中派生的私钥提供保密性的值。钱包软件应用通常将种子编码为*种子短语*，或*助记词*，即12到24个单词的序列，以便更轻松地保存和记忆。

让我们回顾一下如何使用HMAC-SHA-512伪随机函数（即使用SHA-512实例化的HMAC结构）进行密钥派生：对于一个128或256位的种子S，以种子作为密钥输入，以底层椭圆曲线的标识符（一个可以是“Bitcoin seed”、“Nist256p1 seed”或“ed25519 seed”的字符串）作为消息输入，计算HMAC-SHA-512。结果的前256位是主密钥k，后256位是主链码c，用于派生更多密钥的值。

你可以按如下方式从k和c派生*子私钥*：给定一个标识符i（一个最多为2³¹的数字）：以链码c作为密钥，以包含k和i的消息计算HMAC-SHA-512。512位结果被解析为256位的值L和随后的256位链码R。简化表示为 L || R = HMAC-SHA-512(c, k || i)。然后你设置子私钥为k + L，其链码为R。

你可以反过来从获得的密钥和链码派生更多密钥，以建立密钥*层级*。例如，从索引为0的密钥，你派生所有比特币密钥；从索引为60的密钥，你派生所有以太坊密钥。将数字与每个区块链网络关联的约定，已作为文档“SLIP-0044: Registered Coin Types for BIP-0044”的一部分被标准化。

将程序“转换”为数学方程。原则上，你可以将任何程序转换为方程。但当程序没有针对底层数学结构进行优化时，方程会变得非常庞大且计算缓慢。代数哈希函数旨在通过设计既安全又易于在有限域中仅用算术运算实现的哈希函数来解决这个问题。

## 设计原则

让我们考虑Poseidon的设计原则，这是一种2019年为零知识证明系统设计的哈希函数，并迅速被许多区块链系统采用。这类证明有时必须将哈希函数表示为在大型有限域（例如模一个255位素数的整数）上的算术运算电路。在这种情况下，Poseidon被证明比SHA-256等通用哈希函数高效数个数量级。

Poseidon使用海绵哈希函数结构（参见第7章），因此它需要构造一个置换，即输入和输出大小相同的可逆变换。它将此置换应用于一个由有限域元素向量组成的状态。在相关应用中，这样的有限域通常由模素数的数字组成，根据应用不同，该素数可能小至31位，大至381位。

然后，与大多数哈希函数一样，该置换迭代一系列轮次，因此它需要设计一个轮函数。

最后，Poseidon将其置换分解为三个层，具有三种不同的目的，让人想起AES的轮次：

- 唯一性层，AddRoundConstants，Poseidon在文档中记为ARC()。它向状态的元素添加常量值，使得每一轮的常量都不同。使每一轮唯一可以防止包括滑动攻击在内的攻击。为了避免定义和存储大量常量，Poseidon从一个确定性的随机位生成器生成常量，该生成器以Poseidon实例特征（轮数、有限域、S盒类型等）的编码作为初始化。
- 非线性层或S盒层，SubWords，Poseidon的文档记为S。该层增加混淆性，即函数的输入和输出值通过高次代数方程相关联，从而尽可能远离线性和低次方程，这些方程可能被差分密码分析利用。S盒独立地变换其状态的每个元素，通常将域元素x映射为x³或x⁵。指数保持相对较低以便高效计算。
- 线性层，MixLayer，Poseidon在文档中记为M()。MixLayer带来扩散，即初始状态中的差异传播到所有元素。例如，如果状态由四元素向量 (x₁, x₂, x₃, x₄) 组成，则M()将每个元素替换为所有元素的线性组合。它可能将x₁替换为2x₁ + 10x₂ + x₃ + 3x₄的结果。这种变换对应于向量与矩阵的乘法。Poseidon的矩阵必须满足某些安全属性，并且应设计为高效实现。

Poseidon的一轮完整轮次按此顺序应用三个层：ARC()、对每个元素应用S，以及M()。部分轮次仅对一个元素应用S，并且可能在M()中使用不同的矩阵。Poseidon实例然后迭代完整轮次、部分轮次和完整轮次——其数量取决于实例、元素数量、有限域和目标安全级别。

注意 有关Poseidon的更多详细信息，请参阅 https://www.poseidon-hash.info 以及最初的Poseidon论文（https://eprint.iacr.org/2019/458.pdf）和改进设计Poseidon2论文（https://eprint.iacr.org/2023/323.pdf）。

Poseidon是为解决实际用例而创建的众多代数哈希函数之一。其他设计包括MiMC、Monolith、Rescue-Prime和Tip5。

## 可能出错之处

让我们看看一些涉及哈希函数及其在区块链世界中的应用的安全失败案例。

## 有缺陷的自定义哈希

2017年的区块链项目Iota相当古怪。它声称使用一种不同于大多数区块链顺序区块链的架构，更接近有向无环图（DAG），这种架构的安全性要低得多。它还用三进制（trits）而不是二进制（bits）编码数据，三进制单位取三个值而不是两个，据称是为了在并不存在的处理器上让计算更高效。

Iota没有使用基于椭圆曲线的签名方案（如ECDSA或Ed25519），而是使用基于成熟Winternitz结构的哈希签名方案，从而提供后量子安全性——但Iota还设计了自己的自定义哈希函数Curl。

Iota成为十大最流行的加密货币之一，并对其潜在用途和安全性做出了宏伟的宣称。但它的自定义哈希函数——据称是在人工智能的帮助下开发的——在抗碰撞攻击方面被证明非常薄弱。使用现成的硬件，研究人员在几分钟内就发现了碰撞，而这些碰撞只能在人为设计的攻击场景中被利用。Iota很快修补了其哈希函数。

> 在这一惨败之后，著名密码学和安全专家Bruce Schneier评论道：“在2017年，让你的加密算法容易受到差分密码分析攻击是一个新手错误。这说明没有任何有水平的人分析过他们的系统，而且他们的修复使系统安全的概率很低。”



## 熵较低的钱包

本节前面介绍的分层密钥派生模型在理论上是安全的，但在实践中只有在正确实现时才安全。通常你可以使用 BIP32 和 SLIP-0010 标准文档中的测试向量来验证这一点。如果获得的输入/输出值与文档中记录的一致，则实现很可能正确，但不一定安全。

2022 年，流行的加密货币移动钱包应用 Trust Wallet 宣布发布浏览器扩展版本，该版本使用 WebAssembly（Wasm）技术在不同浏览器上高效运行。然而，Wasm 无法使用与移动版本相同的伪随机数生成器（PRNG）；它必须定义一个不同的生成器。

糟糕的 PRNG 可能是密码学的阿喀琉斯之踵（参见第 2 章）。在 Trust Wallet 中，开发者使用了梅森旋转器 PRNG（mt19937），它不是加密 PRNG。它的熵最多为 32 位，并且使用内部状态值的简单线性组合产生输出位。

由于 Trust Wallet 的 PRNG 只有 32 位熵，它只能为用户钱包生成 2^32 个不同的种子。攻击者随后可以计算全部 2^32 个可能的种子，并对每个种子计算使用分层密钥派生得出的私钥和地址。然后他们可以扫描区块链以找到由 Trust Wallet 生成的地址并窃取其代币。发现该漏洞的 Ledger 公司研究人员评论道，“Running such an attack takes much more than a couple of hours, but is doable with a few GPUs in less than a day。”

## 域分离失败导致的碰撞

让我们讨论如何为抗碰撞的哈希函数寻找碰撞。正如密码学家 Moti Yung 所说，“If it sounds impossible, then it’s cryptographically interesting。”

想象以下简单情况：一个应用程序从两个参与者 Alice 和 Bob 接收消息 *A* 和 *B*，然后将这两个消息一起哈希以创建这些消息唯一的哈希值。它可以计算 **H**(*A* || *B*)，即对由 *A* 后跟 *B* 组成的字符串进行哈希。即使你的哈希函数是抗碰撞的，你也会对 *A* = COL 且 *B* = LISION 的情况得到与 *A* = CO 且 *B* = LLISION 相同的情况的相同哈希值。你最终会得到相对于应用程序输入值的哈希碰撞，尽管这不是哈希函数的碰撞，因为哈希函数 **H** 在两种情况下处理的是相同的字符串 COLLISION。

为避免该问题，将应用程序的输入值编码为每个输入唯一的字符串，且编码无歧义：对于每个字符串，你应该能够唯一识别原始的输入值集合。在我们的示例中，在两个输入之间添加美元符号（$）作为分隔符似乎可以避免 COL || LISION 与 CO || LLISION 之间的碰撞：你会得到字符串 COL$LISION 和 CO$LLISION，从而得到不同的哈希值。

但当该字符在应用程序的输入值中被允许时，分隔符并不足以消除歧义。例如，取字符串 COL$$LISION 作为用 $ 分隔的两个输入字符串的连接。你可以从两对输入得到该字符串：COL 和 $LISION，COL$ 和 LISION。请注意，当输入值是固定、恒定大小时问题不会出现——例如第一个字符串为两个字符，第二个为三个字符。即使在这种情况下，使用某种分隔符或编码来防止碰撞仍然更安全，因为未来的补丁可能会引入可变长度输入。

研究人员已在阈值签名协议中发现此类漏洞，你将在本章后面看到，以及在电子投票协议中，其中产生的哈希碰撞可被利用来违反这些协议的安全属性。

## 多签名协议

在密码学多签名协议中，参与者联合生成一条消息的签名，其功能等同于所有各方分别签署该消息；获得的签名意味着所有各方都同意签署该消息。其优点是，与签名者数量一样多的签名相比，只有一个签名。任何拥有所有签名者的公钥的人都可以验证该签名。

区块链平台在多个各方管理账户时采用多签名，以确保所有各方都认可已发布的交易。单个各方也可以使用它们，如果他们在多个设备上拥有多个密钥，以防止单个被攻破的密钥允许攻击者发布交易。

此类多签名协议是集体签名协议的众多类型之一，各方运行协议以生成签名。

在深入技术细节之前，让我们澄清这些多签名与相关协议有何不同。

## 多方多重签名

尽管名称相似，我们将讨论的多签名协议与分别在比特币和以太坊中使用的链上多签名脚本或多签名智能合约不同。后者不是密码学协议，因为参与者独立地将其个人签名提交给区块链网络。网络进而验证诸如“if a transaction has signatures from pub₁ and pub₂, then accept it”或“if a transaction is signed by any two parties among pub₁, pub₂, and pub₃, then accept it”—rejecting the transaction otherwise 的规则。在这里，我们隐式地将公钥 pub 视为各方的标识符，这在区块链协议中很常见。

与链上多签名相比，多签名协议生成单个签名；因此只有一个签名需要验证而不是多个签名。多签名脚本和智能合约则处理多个签名，并由验证规则而非协议组成。

## 单签名者 Schnorr 签名

在了解多方签名的工作原理之前，让我们先看看单方 Schnorr 签名的工作原理。假设 Alice 有一个私钥 a，其关联的公钥为 A = aG。这里 a 是一个数字，或标量，在给定范围内（具体而言，是椭圆曲线定义的有限域，通常是模某个大素数的正整数，至少约 256 位），而 G 是曲线的固定基点。

要签署消息 M，Alice 按如下操作：

- 1. 选取一个秘密随机数 r，并计算点 R = rG。值 r 是一个 nonce，即一次性私钥，R 为其公钥。
- 2. 计算 h = H(R || A || M)，该值将“连接”到私钥 a 和一次性私钥 r 以签署 M。我们不仅对消息进行哈希，还通过非秘密值 A 和 R 分别将 h 绑定到签名者和 nonce。没有这些，不同的攻击就可能发生。
- 3. 计算 s = r + ha 并返回对 (R, s) 作为签名。可以将 s 看作秘密密钥与待签名数据的乘法，其中秘密 r 掩盖了结果；没有它，从签名中恢复私钥是微不足道的。

通过检查 sG 是否等于 R + H(R || A || M)A 来验证签名。这之所以有效是因为由 s = r + ha，将 r + ha 代入 sG 中可得

sG = (r + ha)G = rG + haG = R + hA

其中 h = H(R || A || M)，验证者必须从消息 M、公钥 A 以及签名的 R 部分计算得出。

## Schnorr 多签名

在多签名中我们不只有一个签名者而是多个。为了简单起见，我们将描述两个共同签名者的情况：认识 Bob，他将与 Alice 联合签署消息。Bob 的私钥为 b，其公钥为 B = bG。为了联合创建多签名，Alice 和 Bob 可以按如下方式签署消息 M：

- 1. Alice 选取 nonce r_A，计算 R_A = r_A G，并将 R_A 发送给 Bob。
- 2. Bob 选取 nonce r_B，计算 R_B = r_B G，并将 R_B 发送给 Alice。
- 3. 他们计算 R = R_A + R_B 并设 h = H(R || A || B || M)，该值是 Alice 和 Bob 用于生成其签名部分的数值。h 的特定值通过其公钥（A 和 B）绑定到各方，并通过 nonce R 绑定到当前签名会话，仅用于由 nonce R 定义的特定签名执行。
- 4. Alice 计算 s_A = r_A + ha 并将其发送给 Bob。
- 5. Bob 计算 s_B = r_B + hb 并将其发送给 Alice。



6. 他们双方都计算 R = R_A + R_B 和 s = s_A + s_B，并返回 (R, s) 作为签名。

为了验证签名，检查 sG 是否等于 R + h(A + B)。将 sG 中的 s 替换为先前计算的值，得到如下结果：

sG = (s_A + s_B) G = (r_A + h a + r_B + h b) G
= (r_A + r_B) G + h(a + b) G = R + h(A + B)

请注意，验证者需要知道 A 和 B，而不仅仅是它们的和 A + B，因为他们需要这两个值来计算 H(R || A || B || M)。然而，如果 h 改为定义为 H(R || A + B || M)，验证者就可以使用单个公钥 A + B，而无需知道该签名是由两方共同发出的。我们将多个公钥“合并”为一个公钥的过程称为密钥聚合。当签名者很多时，这特别有助于减少要哈希的数据大小。

> 注意
> 我描述了双方情况下的基本 Schnorr 多重签名，但该协议可扩展至任意数量方，其公钥为 P1, P2, . . . , Pn。在定义中，将 A + B 替换为 P1 + P2 + . . . + Pn，将 A || B 替换为 P1 || P2 || . . . || Pn，并将“将其发送给 Bob/Alice”替换为“将其发送给所有人”。你可以将类似的协议应用于 EdDSA 和 Ed25519，它们是 Schnorr 方案的变体。

## 可能出现的问题

Schnorr 多重签名协议相对简单，但在以下攻击场景中可能会失败。

### 密钥抵消攻击

在这种攻击中，Bob 让签名验证者相信他与 Alice 共同签署了一条消息，而 Alice 从未见过该消息，也没有与 Bob 交互。当你期望 Alice 和 Bob 共同签署消息时——例如在需要双方批准的交易中——攻击者可以利用这一点。正常情况下，验证者会知道 Alice 的公钥 A 和 Bob 的公钥 B，Bob 和 Alice 也会知道彼此的密钥。

现在假设发生以下情况：Alice 将她的公钥 A 发送给包括 Bob 在内的所有人，但 Bob 没有公开他的公钥 B，而是向验证者公开了 C = B − A = (b − a)G，并向 Alice 公开了 B。Bob 不知道 C 对应的私钥这一事实对于攻击并无影响。

Bob 必须像单签名者情况那样，使用自己的私钥 b 对消息签名，但使用 h = H(R || A || C || M)，就好像他在与 Alice 一起签名一样。他返回 (R, s) 作为签名，其中 R = rG（r 由他选择）且 s = r + h b。

验证者期望得到来自 Alice 和 Bob 的签名，检查 sG 是否等于 R + h(A + C)，这是正确的，因为 A + C = A + (B − A) = B。因此，Bob 可以在完全不与 Alice 交互、也不知道她私钥的情况下伪造多重签名。

在实践中，你可以通过要求签名者证明自己知道私钥来避免这种攻击——例如，让他们对一条消息签名。由于 Bob 不知道与 C 对应的私钥，他无法提供这样的证明。正如你将在 MuSig 协议中看到的，你也可以在协议层面避免这种攻击。

这种攻击可以扩展到任意数量的参与方，这种情况通常被称为流氓密钥攻击。在收到所有其他参与方的公钥后，攻击者 Bob 只需将自己的公钥定义为 B − X，其中 X 是所有其他参与方公钥的总和。

### 重复随机数

与 ECDSA 一样，重复的随机数对 Schnorr 多重签名协议是致命的。假设 Alice 的伪随机生成器发生故障，她在两次协议运行中生成了相同的秘密随机数 r_A：她向 Bob 发送了一个初始的 s_A = r_A + h a，以及第二个 s_A' = r_A + h' a，其中第一个 h 和第二个 h' 也依赖于 Bob 的随机性。于是你有 r_A = h a − s_A 和 r_A = h' a − s_A'，这意味着 h a − s_A = h' a − s_A'，或者等价地，

a(h − h') = s_A − s_A'

由此你可以计算出 Alice 的私钥 a = (s_A − s_A') / (h − h')。

消除随机性故障带来的安全风险的一种方法是去除随机性。例如，像 Ed25519 那样通过哈希消息和私钥来计算随机数，在只有一个签名者时是有效的。然而，在多重签名的情况下，将 r 设置为 H(a || M) 是行不通的：如果 Alice 和 Bob 对同一条消息签名两次，那么 Alice 会计算第一个 s_A = r_A + h a 和第二个 s_A' = r_A + h' a，其中两次的 r_A 都等于 H(a || M)，而如果恶意的 Bob 发送的值不同于 H(b || M)，h' 将与 h 不同。在这种情况下，Bob——以及任何通信窃听者——都可以再次通过 (s_A − s_A') / (h − h') 计算出 a。

### 并行执行不安全

当攻击者能够发起多个同时进行的签名协议时，Schnorr 多重签名协议是不安全的。该攻击过于复杂，此处无法描述，但已记录在以下研究文章中：https://eprint.iacr.org/2018/417 和 https://eprint.iacr.org/2020/945。

## 更安全的 Schnorr 多重签名

为了避免密钥抵消攻击和重复随机数问题，研究人员开发了更高级的多重签名协议，特别是 MuSig 协议：MuSig、MuSig2 和 MuSig-DN，其中 MuSig 代表多重签名（multisignature），DN 代表确定性随机数（deterministic nonce）。MuSig 协议还支持密钥聚合，允许验证者仅使用一个从签名者密钥派生的公钥来检查签名，这样聚合密钥不会泄露签名者的数量或其公钥。

让我们看看 MuSig 的主要技巧的实际应用。在最简单的两个签名者（Alice 和 Bob）的情况下，使用与前几节相同的记号，Alice 不再计算 $s_A = r_A + ha$ 作为她的签名份额，而是计算 $s_A = r_A + \mu_Aha$，从而将 $ha$ 部分乘以 $\mu_A$ 值。她通过哈希参与者公钥列表后跟 Alice 的密钥来计算 $\mu_A$（其中 $\mu$ 是希腊字母 mu），即 $\mathbf{H}(A \parallel B \parallel A)$。类似地，Bob 计算 $s_B = r_B + \mu_Bhb$，其中 $\mu_B = \mathbf{H}(A \parallel B \parallel B)$，即哈希公钥列表后跟他的密钥。

然后，Alice 计算*聚合公钥*为 $X = \mu_A A + \mu_B B$，即公钥分别乘以其对应的 $\mu$ 值后的和。消息的哈希变为 $h = \mathbf{H}(R \parallel X \parallel M)$，而不是支持密钥聚合的易受攻击版本多重签名方案中的 $\mathbf{H}(R \parallel (A + B) \parallel M)$。

这个技巧之所以有效，是因为恶意的 Bob 无法再伪造另一个公钥来“抵消” Alice 的 $A$，而在密钥抵消攻击中，他可以通过设置 $C = B - A$ 来做到这一点。在方程 $X = \mu_A A + \mu_B B$ 中，Bob 必须找到一个新的 $B$ 值，以产生“正确”的 $\mu$ 系数，从而从方程中消除 $A$。但这现在是不可能的，因为该方程相对于 $A$ 和 $B$ 是非线性的（线性往往等同于不安全——见第 2 章）。

当签名者超过两个时，你可以类似地应用该技巧：通过哈希密钥列表后跟签名者的密钥来计算 $\mu$ 系数，然后通过计算公钥分别乘以其对应的 $\mu$ 后的总和，将公钥聚合成单个 $X$。

> **注意**
> *有关 MuSig 协议以及 MuSig-DN 版本如何从消息中安全地派生随机数的更多详细信息，请参阅 https://bitcoinops.org/en/topics/musig/。*

## 聚合签名协议

*聚合签名*有多个签名者，每个签名者签署一条消息（对所有签名者来说可以是不同的消息）；然后这些签名被合并为单个签名。仅凭此签名以及签名者的公钥和他们签署的消息，验证即可检查所有签名者是否都签署了各自的消息。由于只需存储一个签名，而不是与签名者数量一样多的签名，验证时间与消息数量成正比。当所有签名者签署同一条消息时，验证可以与验证单个签名者的签名一样快，无论签名者有多少。

聚合签名尤其用于以太坊，特别是在其共识层中。在这种用例中，验证者节点认可更改系统状态（作为区块）的提议，并利用聚合签名来最小化签名存储空间和验证时间。他们使用 Boneh–Lynn–Shacham (BLS) 签名方案，你将在本节中学习该方案，从 BLS 签名背后的魔力开始：密码学配对。




## 配对

在椭圆曲线密码学中，*配对*（pairing）是一种将来自两个椭圆曲线群（不一定是同一个）的两个点转换为有限域元素的操作。两个椭圆曲线点*P*和*Q*之间配对的标准记号为*e(P, Q)*。密码学中使用的配对具有称为*双线性*（bilinearity）的性质，因此被称为*双线性配对*（bilinear pairings），这意味着对于任意点*P*、*Q*和*R*，它们满足以下条件：

$$e(P + R, Q) = e(P, Q) \times e(R, Q)$$

$$e(P, Q + R) = e(P, Q) \times e(P, R)$$

这里，将一个点*R*加到某个操作数上，等价于将结果乘以*R*与另一个操作数之间的配对值。因此，如果你将一个点与其自身相加*n*次——也就是说，如果你将它乘以一个数*n*——那么你会得到

$$e(nP, Q) = e(P, Q) \times e(P, Q) \times \ldots \times e(P, Q) = e(P, Q)^n$$

即*e(P, Q)*自乘*n*次，这也等于*e(P, nQ)*。

如果你有不同的点*P₁, P₂, …, Pₙ*，你可以将输入值的加法转换为输出值的乘法：

$$e(P_1 + P_2 + \ldots + P_n, Q) = e(P_1, Q) \times e(P_2, Q) \times \ldots \times e(P_n, Q)$$

配对内部的工作原理超出了本书的范围。更多细节，请参阅 Kristin Lauter 和 Michael Naehrig 的文章《Cryptographic Pairings》（https://eprint.iacr.org/2017/1108）以及 Nadia El Mrabet 和 Marc Joye 的著作*《Guide to Pairing-Based Cryptography》*（Chapman and Hall/CRC, 2016）。

## BLS 签名

BLS 签名由 Dan Boneh、Ben Lynn 和 Hovav Shacham 于 2006 年在文章《Short Signatures from the Weil Pairing》中提出。文中指出，该方案的设计目标是“用于由人类输入签名或通过低带宽信道传输签名的系统”。然而，BLS 签名最终被广泛应用于高带宽信道上的高度自动化系统，这得益于后续一篇论文中描述的一个性质：签名和公钥的聚合。

> **注意**  
> 不要将 BLS 签名与 BLS（Barreto–Lynn–Scott）曲线混淆，两者有一个共同作者（Lynn）。BLS 曲线是为配对友好而设计的椭圆曲线，能够实现安全高效的配对操作。事实上，BLS 签名通常使用 BLS 曲线上的点。例如，以太坊的 BLS 签名就依赖于 BLS12-381 曲线。

### 单签名者签名与验证

在 BLS 签名中，Alice 的私钥是一个标量 $a$，她的公钥是 $A = aG$，其中 $G$ 是预定义的基点。要对消息 $M$ 签名，她首先计算 $H = H(M)$，这里的哈希函数返回一个曲线点，而不是比特串或标量——$H$ 记号遵循通常的约定，即用大写字母表示点。然后签名为 $S = aH$。这看起来比 Schnorr 签名或 ECDSA 签名简单得多：只需对消息进行哈希，然后将结果与私钥相乘即可。

要验证 BLS 签名，需要计算两次配对操作：

- $e(A, H)$：公钥与哈希消息之间的配对（注意 $A = aG$）
- $e(G, S)$：基点与签名之间的配对（注意 $S = aH$）

由于配对的雙线性性质，这两个值应当相等：

$$e(A, H) = e(aG, H) = e(G, H)^a = e(G, aH) = e(G, S)$$

如果等式成立，则签名有效；否则，签名无效。

忽略配对操作的复杂性，这类基于配对的签名是最简单的签名方案。

### 来自多个签名者的聚合签名

让我们进一步利用 BLS 签名和双线性配对的魔力，考虑一个场景：$n$ 个签名者分别拥有私钥 $k_1, k_2, \ldots, k_n$ 和公钥 $P_1, P_2, \ldots, P_n$，他们对 $n$ 条消息 $M_1, M_2, \ldots, M_n$ 进行签名，并产生签名 $S_1, S_2, \ldots, S_n$。注意 $H_i = H(M_i)$ 是第 $i$ 条消息的哈希值。

你可以将签名 $S_i = k_iH_i$ 相加，聚合成一个签名：$S = S_1 + S_2 + \ldots + S_n$。观察发现，像单签名验证那样计算 $e(G, S)$，由于雙线性性质，会得到如下结果：

$$e(G, S) = e(G, S_1 + S_2 + \ldots + S_n) = e(G, S_1) \times e(G, S_2) \times \ldots \times e(G, S_n)$$

回顾配对满足 $e(nP, Q) = e(P, nQ)$。因此，你可以通过将乘数因子 $k_i$ “移动”到配对的左操作数，从而将每一项 $e(G, S_i)$ 替换为 $e(P_i, H_i)$：这样第一个操作数将变为 $k_iG = P_i$ 而不是 $G$，第二个操作数将变为 $H_i$ 而不是 $S_i = k_iH_i$。

在将多个签名者对多条消息的多个签名聚合成一个签名之后，你可以根据签名者的公钥和被签名的消息来验证这个聚合签名。验证只需检查 $e(G, S)$ 与所有配对乘积 $e(P_i, H_i)$ 是否相等。需要计算 $1 + n$ 次配对，而如果不聚合签名则需计算 $2n$ 次配对——在后一种情况下，签名占用的内存是聚合签名的 $n$ 倍。

让我们考虑一个需要同时聚合签名和公钥的场景。

### 聚合公钥

假设所有签名者都签署同一条消息 $M$，并且你将所有公钥聚合成一个：$P = P_1 + P_2 + \ldots + P_n$。注意，$k_1, k_2, \ldots, k_n$ 仍分别表示他们的私钥，$H = H(M)$ 表示消息的哈希值。给定有效签名 $S_i$，你会得到以下等式：

$$\begin{aligned}
e(P,H) &= e(P_1 + P_2 + \ldots + P_n,H) \\
&= e((k_1 + k_2 + \ldots + k_n)G,H) \\
&= e(G,(k_1 + k_2 + \ldots + k_n)H) \\
&= e(G,S_1 + S_2 + \ldots + S_n) \\
&= e(G,S)
\end{aligned}$$

因此，你只需使用两次配对操作 $e(P,H)$ 和 $e(G,S)$ 即可验证 $n$ 个参与方对同一消息的签名。这非常高效，因为签名验证基本上与参与方数量无关，你可以高效地累加点，而配对计算成本高昂。除了计算效率外，聚合公钥和签名还能节省内存。

### 可能出错的地方

与许多椭圆曲线密码学方案一样，BLS 签名应避免无效密钥和弱参数，以确保安全性。与前述协议类似，BLS 签名也可能面临密钥消除攻击。让我们详细探讨一下。

#### 无效密钥

BLS 签名定义在一份互联网草案中，这是 IETF 的工作文档，可在 https://github.com/cfrg/draft-irtf-cfrg-bls-signature 获取。该文档规定了核心操作，包括密钥生成（KeyGen 算法）、签名（CoreSign）、验证（CoreVerify）以及密钥验证（KeyValidate）。给定公钥，后者用于确保公钥的有效性，即它“表示一个有效的、非单位元的、且属于正确子群的点”。

密钥验证可防止使用弱的私钥/公钥对，因为这类密钥对更容易伪造签名。例如，考虑一个零私钥 $a = 0$ 的简单情况。那么任何消息 $M$ 的签名都是 $0 \times H(M) = 0$。因此，为任何消息伪造签名都是轻而易举的。在这种情况下，公钥为 $0 \times G = O$，即无穷远点。如果密钥验证拒绝等于 $O$ 的公钥，就能确保私钥不为零。

一个不那么平凡的情况是，公钥作为椭圆曲线上的点，其取值使得签名更容易被伪造——也就是说，无需知道私钥即可创建有效签名。并非给定椭圆曲线上的所有点都具有同等的安全性——特别是那些属于小子群而不是主子群的点。如果公钥点属于某个这样的子群，那么可能存在的有效签名数量会大大减少，从而使伪造签名变得更容易。同样，如果提供给验证函数的公钥不属于该椭圆曲线，那么有效签名也容易伪造。

因此，使用前述规范中的 KeyValidate 算法检查公钥是否有效至关重要，如清单 15-1 所示。

```
Inputs:
- PK, a public key in the format output by SkToPk.

Outputs:
- result, either VALID or INVALID

Procedure:
1. xP = pubkey_to_point(PK)
2. If xP is INVALID, return INVALID
3. If xP is the identity element, return INVALID
4. If pubkey_subgroup_check(xP) is INVALID, return INVALID
5. return VALID
```

*清单 15-1：KeyValidate 算法确保 BLS 公钥有效。*

如果你实现 BLS 签名，请确保你的代码在验证公钥和签名时执行 BLS 规范中描述的所有检查。

#### 密钥消除攻击

在其基本形式中，带聚合公钥的 BLS 聚合签名与 Schnorr 签名一样容易受到相同类型的密钥消除攻击：如果攻击者知道前 $n-1$ 个签名者的公钥 $P_1, P_2, \ldots, P_{n-1}$，他们可以声称自己的公钥是

$$P_n = X - (P_1 + P_2 + \cdots + P_{n-1})$$

其中 $X$ 是攻击者知道对应私钥 $x$ 的公钥，且 $X = xG$。当攻击者出示用 $x$ 创建的签名时，不疑有他的用户会使用公钥 $P_1 + P_2 + \cdots + P_n$ 来验证消息的签名，而这个公钥等于 $X$。攻击者可以单独代表一组假定签名者签署一条消息。

为防止这种攻击，用户可以签署一条消息来证明自己知道公钥对应的私钥。由于攻击者不知道 $P_n$ 的私钥，他们无法通过这一测试。

另一种缓解措施是修改聚合签名方案，使返回的签名不仅仅是签名之和 $S = S_1 + S_2 + \cdots + S_n$，而是带有由公钥导出的系数的和，例如

$$S = t_1S_1 + t_2S_2 + \cdots + t_nS_n$$



其中 \(t_i = H(P_i \parallel P_1 \parallel P_2 \parallel \dots \parallel P_n)\)，\(i = 1, 2, \dots, n\)。用于验证签名的聚合公钥为 \(P = t_1 P_1 + t_2 P_2 + \dots + t_n P_n\)。你可以通过检查 \(e(P, H(M))\) 仍然等于 \(e(G, S)\) 来验证这一技巧的有效性。

## 门限签名协议

门限签名与多重签名和聚合签名不同——后两者要求签名协议中的所有参与者都拥有各自的公钥和私钥——门限签名只有一个私钥 \(k\) 和一个公钥 \(P\)，并且有 \(n\) 个参与者，每个参与者持有密钥的不同份额 \(k_i\)，其中定义了一个参数 \(t\)（门限值），满足 \(t < n\)，并且：

- \(t + 1\) 个签名者可以联合对某条消息签发有效的签名，该签名使用公钥 \(P\) 验证，并且任何签名者都无法获知私钥 \(k\)。这是通过运行一个协议实现的，该协议使用每个签名者的份额 \(k_i\) 以及待签名的消息，而不会将私钥暴露给任何一方。
- \(t\) 个或更少的签名者无法创建签名，因此也无法确定私钥 \(k\)。

生成的签名看起来与普通的单签名者签名无异，并且可以按同样的方式进行验证。

门限签名是一种特定的多方计算（MPC）类型。MPC 是一类协议，其中 \(n\) 个参与者计算某个函数 \(f(x_1, x_2, \dots, x_n)\) 的输出，每个参与者知道自己的输入 \(x_i\) 并能获知函数的输出，但无法获知其他参与者的输入 \(x_i\)。在门限签名中，\(x_i\) 是私钥的份额，输出则是一个签名。我将在第 319 页的“秘密共享技术”一节中详细阐述份额的含义。

门限签名的一个优点是“隐藏”了共同签名者的数量及其身份，因为验证者只能看到来自单个私钥的签名。虽然某些多重签名和聚合签名方案也具有这一特性，但门限签名更适合加密资产托管的场景，因为只有一个私钥和一个公钥；你可以直接应用门限签名来分散控制任何地址。

## 使用场景

门限签名在加密货币和数字资产管理中用于将某个地址的控制权分散到多个系统或参与方。它可以用于在服务提供商和用户设备之间共享账户控制权：每一方持有密钥的一个份额，并且必须共同运行协议才能签署交易，从而花费资金。这种设置确保即使攻击者入侵了用户设备并获取了密钥份额，也无法擅自授权交易。同样，服务提供商在未经用户同意的情况下也无法发起交易。然而，可靠地实现这种模式面临挑战，尤其是密钥管理方面（密钥生成、密钥轮换、备份等）。

组织也可以使用门限签名将资金托管分散到多个系统中，例如不同的设备类型、数据中心、操作系统和软件组件。这种方法特别适合冷钱包和包含大量资产的账户。仅依赖门限签名是不够的，因为全面的安全措施和控制至关重要。例如，必须适当隔离对 IT 组件的访问权限，以确保不同的人员或 IT 服务提供商能够访问不同的系统（从而持有不同的份额）。此外，交易的发起和批准必须受到严格控制并留有审计跟踪。

## 安全模型

与所有加密协议一样，我们需要定义门限签名方案的安全性意味着什么。这样的安全模型包括安全目标（攻击者应该难以做到什么）和攻击者模型（关于攻击者能力的假设）。让我们深入探讨这两个特征。

## 安全目标

门限签名的主要安全目标与单方签名相同：攻击者必须无法伪造有效签名，这意味着他们必须无法确定私钥。这也意味着协议必须保证*输入隐私*：参与方持有的密钥份额不应泄露给任何其他方。最后，协议必须保证*正确性*：协议计算出的签名必须是有效的，并且协议执行中的所有参与者都能获得该签名。

## 攻击者模型

门限签名并不是只有一种安全模型；相反，攻击者可以从多个维度来描述。在所有攻击场景中，常见的威胁假设是攻击者能够主动攻击网络通信——捕获、修改和注入消息。使用安全通道在参与方之间建立经过认证和加密的通信可以挫败此类攻击。协议设计者还假设通信是可靠的，即所有发送的消息都应按发送顺序被接收。

门限签名的攻击者模型考虑了参与者的*腐化*——也就是说，攻击者入侵了他们的系统，获知了他们的秘密，并实质上让他们按攻击者的意愿行事。该模型假设攻击者不能腐化超过 \(t\) 个参与方；否则，根据门限签名功能的定义，他们将能够伪造签名。

让我们考察攻击者可以腐化参与者时需要考虑的参数。

首先，我们根据攻击者可能腐化的*参与方数量*来刻画攻击者。存在两类门限签名，分别由在不损害协议安全性的前提下可被最多腐化的恶意参与方数量来定义：

### 诚实多数
在此模型中，攻击者只能腐化少于一半的密钥共享参与方。因此，门限值 \(t\) 必须满足 \(t < n/2\)。根据定义，参数为（\(t\), \(n\)）的门限签名协议即使在 \(t\) 个参与者被腐化的情况下也必须是安全的。在诚实多数假设下设计的协议通常更高效，但它们无法适应任意的 \(t\) 值。例如，参数为（4, 5）的协议在此模型中不可行，因为它要求容忍多达四个被腐化的参与方。

### 恶意多数
该模型允许协议支持从 1 到 \(n-1\) 的任意 \(t\) 值。它可以创建这样的协议：即使 \(n\) 个参与方中除一个外其余全部被腐化，恶意方仍然无法伪造签名或恢复私钥。该模型在门限值方面提供了更大的灵活性，但通常需要更复杂和健壮的安全机制。

我们还根据攻击者腐化某个参与方并获知其秘密值（包括密钥份额）后能够做什么来刻画攻击者。有两个攻击者模型定义了这一点：

### 被动型，或诚实但好奇
攻击者从被腐化的参与方获取信息，但无法强迫他们偏离协议。这模拟了“只读”型入侵，攻击者获得系统内存的快照，包括存储器和易失性内存（RAM、处理器寄存器）。

### 主动型，或恶意型
参与方可以任意偏离既定协议。这模拟了攻击者完全控制的系统，或被恶意内部人员（如操作员、管理员或云提供商）控制的系统。

因此，能够抵抗主动攻击者的协议必然能够抵抗被动攻击者，但反之则不然。

攻击者有两种选择腐化哪些参与方的方式，由以下腐化类型模型定义：

### 静态腐化
攻击者必须在协议开始之前选择要腐化的参与者。

### 自适应腐化
攻击者可以等到协议开始后再选择要腐化的参与者——然后获知他们在整个协议中的操作历史。

能够抵抗静态腐化的协议总是能够抵抗自适应腐化，但反之则不然。不过，有一些技术可以将协议从抵抗静态腐化转换为抵抗自适应腐化。





## 秘密共享技术

阈值签名的关键要素是*秘密共享*协议，或者说是将秘密拆分成多个部分（*份额*）并分发给不同参与方的技术，使这些参与方能够共同重新计算出最初的秘密。秘密共享协议尤其可以用于创建私钥备份，让不同参与方将不同份额存储在不同位置。

## 加法共享

当你把一个秘密视为数字时，共享它的最简单方式是*加法共享*：给定一个数字 s，将其拆分为 n 个值 s₁, s₂, . . . , sₙ，使得 s₁ + s₂ + . . . + sₙ = s。例如，如果你处理的是模 100 的数字，可以按如下方式将数字 s = 47 随机加法共享为四个份额：选取三个 0 到 99 之间的随机数，比如 s₁ = 12、s₂ = 94 和 s₃ = 80，并令 s₄ = s − s₁ − s₂ − s₃ = 61。（注意，减法按模 100 计算，因此 −1 = 99、−2 = 98，以此类推。）

这种方法非常简单，但需要使用所有份额才能恢复原始秘密。

## 阈值共享

阈值共享更接近阈值签名的实际做法：给定参数 n 和 t < n 以及秘密 s，它生成若干份额，使你可以使用所生成的 n 个份额中的任意 t 个份额来恢复秘密。

最著名的阈值共享方法是*沙米尔秘密共享*，它利用了多项式的以下性质：给定一个次数为 t 的多项式，形式为

$f(x) = a_0 + a_1 x + a_2 x^2 + a_3 x^3 + \dots + a_t x^t$

你只需要 f(x) 在 t + 1 个不同的 x 值上的 t + 1 次求值结果，就能确定所有固定不变的系数 aᵢ。

要利用这一性质创建阈值秘密共享，令 a₀ = s，即秘密本身。然后，选取 a₁ 到 aₜ 的随机值，并对 n 个不同的 x 值计算 f(x)，结果即为秘密的 n 个份额。

根据 f(x) 的值重新计算系数的技术称为*拉格朗日插值*，得名于 18 世纪的意大利数学家，他提出了一种通用方法，在给定曲线上若干点的情况下确定该曲线的方程。事实上，你可以从几何角度看待这个问题。如果方程的次数为 1（形式为 a₀ + a₁x），那么它就是直线的方程，知道直线上的两个点就足以唯一确定这条直线。同样，如果方程的次数为 2（形式为 a₀ + a₁x + a₂x²），那么曲线就是抛物线，其方程可以用三个点来确定。

我们有时会看到沙米尔秘密共享的实现中定义了一个 **Lagrange()** 函数，用于计算插值并返回 a₀ 系数，即被共享的秘密。如果你有若干 f(x) 的值需要组合以恢复秘密，可以定义运算 Lagrange(s₁, s₂, . . . , sₜ) 来返回共享秘密 s。这适用于任意 t 个不同份额的组合，不一定是前 t 个份额。Lagrange() 运算的细节对本书来说有点过于技术化，但你可以将其实现为一系列基本的加法、乘法和求逆运算。

## 平凡情形

最简单的阈值签名类型之一是使用 BLS 签名，正如前面在聚合签名的背景下看到的那样。回忆一下，给定私钥 k，BLS 签名通过将 k 与曲线点 H = H(M) 相乘来计算签名。你可以使用加法共享来创建参数为 (n − 1, n) 的阈值方案。例如，如果 n = 3，将密钥拆分为三个份额，使得 k₁ + k₂ + k₃ = k。然后，每个参与方通过将其份额 kᵢ 与 H 相乘来计算各自的签名份额。将三个份额相加得到如下结果：

k₁H + k₂H + k₃H = (k₁ + k₂ + k₃)H = kH

通过加法组合三个份额即可得到使用 k 的有效签名，即使没有任何参与方知道 k。如果参与方将各自的份额相加，也能恢复 k，但如果份额是随机生成的，那么两个参与方的份额相加不会泄露关于 k 的任何信息。

要创建具有任意 t 和 n 的阈值签名方案，可以使用沙米尔秘密共享技术，并利用 Lagrange() 运算的线性性质：按照“阈值共享”一节所述生成密钥份额 kᵢ，然后如下计算签名：

Lagrange(k₁H, k₂H, k₃H) = Lagrange(k₁, k₂, k₃)H = kH

同样，你可以获得使用密钥 k 的有效签名。

## 简单情形

现在你将在阈值设置下计算 Schnorr 签名，这比 BLS 签名更具技术性。回忆一下，Schnorr 方案将签名计算为 s = r + h a，其中 h = H(R || A || M)，r 是每次签名使用的随机 nonce，a 是签名者的私钥。签名还包括 R = r G，即公开的 nonce 值。由于其相对于秘密值具有线性性质，将它转化为阈值签名方案相对容易：注意，秘密 r 被加到秘密 a 与哈希 h 的乘积上，而 h 并不是秘密。

设想最简单的两位签名者情形：签名私钥 k = a + b 采用加法共享，其中 a 和 b 分别是两位签名者的密钥份额。为了签名，双方可以生成秘密 nonce r_A 和 r_B，对应的公开值分别为 R_A = r_A G 和 R_B = r_B G。然后，双方交换这些值并计算公开 nonce R = R_A + R_B，它将成为签名的一部分。R 就是你从私有值 r = r_A + r_B 推导出的公开值，因为：

R_A + R_B = r_A G + r_B G = (r_A + r_B) G

接下来，双方计算各自的签名份额：s_A = r_A + h a，s_B = r_B + h b，将它们相加得到：

(r_A + h a) + (r_B + h b) = (r_A + r_B) + h(a + b) = r + h k

因此，你得到 r + h k，即使用密钥 k 的签名，尽管参与者在计算中只使用了加法份额 a 和 b。要获得任意参数 t 和 n 的阈值构造，可以使用沙米尔秘密共享来代替加法共享。

前面的构造不足以满足阈值签名方案的全部安全要求。它尤其容易受到密钥抵消攻击，除非参与者在协议的预备阶段提交自己的 nonce——例如，发送其 nonce 的哈希。此外，它还存在许多细微漏洞，而由密码学家 Chelsea Komlo 和 Ian Goldberg 于 2020 年设计的 Flexible Round-Optimized Schnorr Threshold（FROST）签名协议解决了这些问题，相关文档见 https://eprint.iacr.org/2020/852。

> 注意
> 第 12 章的 EdDSA 签名协议与 Schnorr 签名类似，但它将 nonce 计算为消息的哈希，而不是一个随机的任意值。这使得创建符合原始 EdDSA 规范的阈值签名协议变得更加复杂。

## 困难情形

在阈值设置下最难运行的签名方案也是最常见的方案。ECDSA 签名算法（见第 12 章）比 Schnorr 签名和 EdDSA 更复杂，因为它涉及除法。给定消息哈希 h = H(M)，签名者选取一个随机数 k，从点 kG 的坐标计算出数字 r，并将签名计算为 s = (h + r a) / k，其中 a 是签名者的私钥。

高效且安全的 ECDSA 阈值签名仍然是密码学家面临的一个具有挑战性的研究问题。第一批实用协议出现在 2010 年代末，其动力来自加密货币的使用场景——当时包括比特币和以太坊在内的大多数主流加密货币只支持 ECDSA 作为交易签名方案。

密码学家设计了多种构建 ECDSA 阈值签名协议的方法。例如，Yehuda Lindell 在 2017 年发表的《快速安全的两方 ECDSA 签名》（https://eprint.iacr.org/2017/552）需要承诺方案、同态加密方案和零知识证明系统。这类协议的复杂性使得理解、实现和安全分析变得困难，从而导致已部署系统中出现许多安全缺陷。

## 可能出错的地方

阈值签名协议中的具体安全问题往往非常复杂，涉及本书未涵盖的密码构造细节。因此，我不讨论具体问题，而是讨论类别。




影响阈值签名实际部署的问题，从广泛使用的开源软件到商业解决方案。

## 论文与代码

当工程师需要根据研究论文实现阈值签名协议时，他们会遇到挑战。这些论文主要面向密码学研究人员，编辑质量参差不齐，内容复杂、数学性强，而且相当新颖。这种新颖性可能意味着实验性协议可能不如预期的那样安全。这些因素导致了一系列现实世界中的安全问题，可归为四个主要方面：

### 不安全的协议

如果协议在纸面上就不安全，那么实现中也不会更安全。常见问题包括忽略边界情况，或在接收其他参与方的输入时验证不足。例如，一些协议未能验证加密数字是否落在预期范围内，从而导致实际攻击。

### 不完整的描述

研究论文不是技术规范，而是面向学术读者撰写的，因此往往缺乏网络和编码等实际实现细节。一个显著的例子是针对阈值签名的 TSSHOCK 攻击，该攻击利用了哈希函数输入元素中模糊的编码，如第 305 页的“域分离失败导致的碰撞”所述。

### 不完整的实现

阈值签名协议十分复杂，包含众多子组件和详细要求，这可能导致安全验证被忽略，尤其是当这些验证仅在附录中提及时。一个实例是，某个协议要求通过零知识证明验证数字 N = pq（用于 Paillier 加密）是两个足够大的素数的乘积，但实现中省略了这一验证，从而允许不安全的 N 值。

### 不安全的组件选择

协议描述通常不会说“使用 BLAKE3 哈希函数”或“使用 256 位椭圆曲线 NIST P-256”；相反，它们会说“使用能够提供所需安全级别的哈希函数和椭圆曲线”。因此，实现者需要自行选择合适的原语，并安全地使用其编程接口。例如，使用 1,024 位的 RSA 模数不足以确保 128 位安全性。

此外，当实现者有意修改协议（也许是为了提高效率或适应特定用例）时，风险也会出现。这通常不会有好结果。关于阈值签名攻击的示例，请参阅 Dmytro Tymokhanov 和 Omer Shlomovits 的论文《Alpha-Rays：针对阈值 ECDSA 实现的密钥提取攻击》(https://eprint.iacr.org/2021/1621) 以及 Nikolaos Makriyannis、Oren Yomtov 和 Arik Galansky 的论文《领先 MPC 钱包中的实际密钥提取攻击》(https://eprint.iacr.org/2023/1234)。

## 密钥管理方面

一位朋友曾说过：“每 10 行加密代码，就有 1,500 行密钥管理代码。”这强调了密钥管理流程的关键性和复杂性，包括密钥创建、存储、备份和恢复。虽然这些方面在专注于理论方面的学术论文中可能被忽视，但在实际应用中却至关重要。在生产环境中实现阈值签名的工程师和安全专业人员必须优先考虑这些密钥管理问题——即使是最健壮的阈值签名协议也无法替代全面的密钥管理实践。

让我们回顾一下，对于使用阈值签名来保护大量加密货币资产的组织来说，主要的密钥管理注意事项：

**密钥生成** 无论你使用分布式密钥生成还是集中式生成，都必须确保在密钥生成期间或之后，秘密值不会暴露给未经授权的系统或方。这种保证通常通过严格的流程（如密钥仪式）来提供，确保供应链完整性和审计跟踪，以证明密钥已正确生成。不要允许其他方（例如云提供商）代表你生成密钥，或让他们有能力随时读取密钥。

**密钥存储** 将密钥存储为多个分片而不是单个值，并不会降低安全存储的必要性。在不同平台上保护众多秘密可能比在统一平台上保护单个秘密更具挑战性。密钥分片必须存储在某种安全内存中，以防止未经授权的访问、篡改和物理攻击。

**密钥备份与恢复** 实施阈值方案（例如，需要六分之三的分片才能签署交易）可以防止密钥分片丢失或系统中断。然而，这并不能否定密钥备份的必要性，你也应该以阈值分片的形式维护备份。务必将这些备份分片的访问权限分配给不同的方。此外，定期验证备份的可靠性，以确保它们未被破坏，并且能够在必要时（例如在灾难恢复演练中）有效地用于重建密钥。

## 零知识证明

*零知识证明（ZKP）* 是密码学家最强大的工具之一。它们是两方之间的协议，一方是*证明者*，另一方是*验证者*，证明者让验证者相信某事为真，而不透露任何关于为什么为真的信息。例如，证明者可以证明自己知道某个困难计算问题的解，而不透露解本身。你可以为任何 **NP**-完全问题创建 ZKP，以证明你知道解而不泄露它。

更一般地，ZKP 用于证明一个陈述，例如“此密文中加密的数字在 100 到 200 之间”，或“对于给定的明文 *P* 和密文 *C*，我知道一个密钥 *K*，使得 *C* = **AES**(*K*, *P*)。”

关于零知识证明的非技术性介绍，我推荐密码学家 Amit Sahai 的视频《计算机科学家用 5 个难度级别解释一个概念》(https://youtu.be/fOGdb1CTu5c)。有关数学细节，请参阅 https://github.com/matter-labs/awesome-zero-knowledge-proofs 上的链接。

**注意** *“零知识证明”一词是对研究文献中更准确术语的简化。例如，许多“零知识证明”协议实际上是知识的零知识论证。研究人员将“证明”一词保留用于无条件安全，而使用“论证”表示计算安全。此外，“见证”一词指的是允许证明者证明其陈述的秘密，作为秘密或密钥的推广，因为其适用范围更广。*

## 安全模型

ZKP 协议安全意味着什么？攻击者是证明者还是验证者？他们如何攻击协议？让我们通过检查安全目标和攻击者模型来回答这些问题。

### 安全目标

一个安全的 ZKP 必须满足以下概念：

- **完备性** 如果证明者使用正确的秘密遵循协议，诚实的验证者会相信陈述的真实性。换句话说，协议始终有效。
- **可靠性** 如果证明者不知道秘密，他们无法让诚实的验证者相信虚假陈述（除非概率可忽略不计）。换句话说，证明者不能作弊。
- **零知识** 验证者除了陈述为真这一事实外，什么也学不到。具体来说，他们无法了解证明者的秘密的任何信息。

验证者“会相信陈述的真实性”这一概念，是由协议满足这三个属性的共同约定所保证的——也就是说，如果陈述是假的（例如，如果证明者不知道他们声称知道的解），证明者就无法完成协议。

### 攻击者模型

双方都可能成为攻击者，分别试图破坏可靠性和零知识：

**恶意证明者** 想要证明一个虚假陈述——例如，错误地让验证者相信他们知道某个困难问题的解。这样的攻击者可以偏离协议以试图欺骗验证者。在实践中，这是 ZKP 在机密程序执行等应用中的最大威胁。

**恶意验证者** 想要提取关于秘密（*见证*）的信息，从而破坏零知识属性。攻击者模型区分*被动*验证者攻击者（诚实但好奇）和*主动*验证者攻击者（可以任意偏离协议）。

请注意，恶意验证者可以通过声称他们不相信陈述的真实性来挑战完备性。在实践中，这不是问题，因为证明者可以针对其他（诚实的）验证者重复证明协议，这些验证者会揭露撒谎的验证者。

## Schnorr 协议

Claus-Peter Schnorr 创造了同名的签名方案，他还描述了一种类似的结构，即零知识*离散对数知识证明*。它是 Schnorr 和 EdDSA 签名的基础，也是许多更复杂 ZKP 的基础。

Schnorr 协议通过三个步骤来证明知道 *a*，使得 *aG = A*——即 *A* 关于生成元 *G* 的离散对数：

1. *承诺*：证明者选择一个随机数 *r*，并发送 *R = rG*。
2. *挑战*：验证者发送一个随机数 *c*。
3. *响应*：证明者发送 *s = r + ca*，验证者当且仅当 *sG = R + cA* 时接受。

**注意** *这种三步协议，包含承诺、挑战和响应，被称为 sigma 协议，因其形状类似于大写希腊字母 sigma（Σ）。*

Schnorr 协议的*完备性*最容易验证：如果 *a* 满足 *aG = A*，那么

*sG = (r + ca)G = rG + caG = R + cA*

这就是证明者的验证条件。

要理解该协议如何确保*可靠性*——即证明者必须知道 *a*——想象一下，证明者在两次运行中使用相同的 *r*

协议。验证者因此得到两个响应，\(s_1 = r + c_1 a\) 和 \(s_2 = r + c_2 a\)，对应于两个不同的挑战 \(c_1\) 和 \(c_2\)。现在他们可以计算

$$s_1 - s_2 = r + c_1 a - r - c_2 a = a(c_1 - c_2)$$

并将结果除以 \((c_1 - c_2)\) 来得到 \(a\)。由于检查 \(sG\) 等于 \(R + cA\) 确保你有 \(s = r + ca\)，由此可知在正确执行此协议时证明者必须知道 \(a\)。这种逻辑推理被称为 *知识提取器*，它是证明 ZKP 是健全的主要技术。

该协议也可以被证明是零知识的，使用一种称为 *模拟器* 的技术，该算法创建消息（或 *通信记录*）使其与零知识证明的真实执行中的消息无法区分。然而，与真实的证明者不同，模拟器不一定知道正在证明的秘密（或见证）。尽管如此，它生成的信息在证明系统的上下文中仍然看起来有效且令人信服。

在 Schnorr 协议中，模拟器反向工作，首先选择一个随机响应 \(s\)，以表明真实的 \(s\) 将“像”纯随机一样随机。然后它选择一个随机挑战 \(c\) 并计算原始承诺为 \(R = sG - cA\)。证明该协议是零知识的然后表明这三个值与协议真实执行的值无法区分，但不需要知道秘密 \(a\)。 （注意，在 Schnorr 的情况下，你必须假设验证者遵循协议并选择随机的 \(c\)。）

## 非交互式证明

Schnorr 协议是 *交互式* 的：证明者发送第一条消息，验证者用挑战作出响应，证明者向其发送响应——各方在三轮消息中交互。但如果验证者不能发送消息而只想接收一条能够说服他们的消息怎么办？如何从交互式协议创建这种 *非交互式* 证明？

让我们再看一下 Schnorr 协议，其中验证者发送一个随机挑战 \(c\)，该值必须对证明者不可预测。如果证明者在发送 \(R\) 之前就知道 \(c\)，他们就可以作弊，如下所示：给定 \(c\)，选择 \(s\) 的任意值，并计算 \(R = sG - cA\)；然后将此 \(R\) 发送给验证者，并将 \(s\) 作为对 \(c\) 的响应发送。验证成功，但证明者不需要使用秘密值 \(a\)。

如何在不与验证者交互的情况下使 \(c\) 对证明者不可预测？诀窍是使用哈希函数从 \(R\) 派生 \(c\)，这会阻止证明者找到满足 \(sG = R + cA\) 的配对 \((R, c)\)，这是由于哈希函数的伪随机行为。

要使用 Schnorr 协议生成秘密 \(a\) 的 *非交互式零知识 (NIZK)* 知识证明，证明者按如下方式进行：

1. *承诺：* 证明者选择一个随机数 \(r\) 并计算 \(R = rG\)。
2. *挑战：* 证明者计算 \(c = H(G || R || A)\)；你必须包含值 \(G\) 和 \(A\) 以将 \(c\) 的生成绑定到生成器参数 \(G\) 和证明者的公钥 \(A\)。
3. *响应：* 证明者计算 \(s = r + c a\) 并将证明生成为 \(R\) 和 \(s\) 的编码。

要验证从证明者处收到且公钥为 \(A\) 的证明 \((R, s)\)，验证者重新计算挑战 \(c = H(G || R || A)\) 并检查等式是否成立 \(sG = R + cA\)。

将协议数据哈希以替换验证者生成的挑战的技巧由 Fiat–Shamir 变换正式化，这是一种将交互式协议转换为非交互式协议的通用技术。对于该变换适用，验证者的随机挑战必须独立于证明者的消息并且是公开（非秘密）值。

## zkSNARKs

让我们谈谈在区块链应用中因其强大和高效而得到广泛采用的零知识证明类型。例如，zkSNARKs 是 Zcash 隐私交易平台的基石：在 Zcash 中，zkSNARKs 证明从一个账户扣除一定金额并记入另一个账户，而不透露账户金额，也不会导致计算或存储量过高。

zkSNARK 是一种提供零知识 (zk) 属性的非交互式知识证明，其中 SNARK 代表以下内容：

- **简洁** 证明相对于陈述和秘密的大小非常小。它可能与陈述大小的对数相似，甚至是常数大小——无论陈述大小如何，大小始终相同。
- **非交互式** SNARK 是一种非交互式知识论证，通常使用 Fiat–Shamir 变换将交互式协议转换为非交互式协议。它不需要验证者向证明者发送消息。
- **论证** 知识论证是一种计算安全的证明，有条件地安全。换句话说，它对具有无限计算能力的攻击者不安全，这通常是可以接受的限制。
- **知识** SNARK 提供完整性和可靠性，作为知识论证。

此外，生成和验证 zkSNARK 必须在计算上高效。

当你想要证明对一个问题解的知识，而该问题的描述甚至不适合证明大小时，生成这样一个简洁的证明听起来违反直觉。例如，关于陈述

“我知道方程 $f(x)=0,$ 的解”，而方程 $f(x)$ 可以是任意大小？从理论角度来看，简短的证明是有意义的，因为证明必须传达的唯一信息是某些解的 *知识* 以及一般某些陈述的 *正确性*，而不是实际的解和秘密；证明必须是零知识的，并且只向验证者透露该信息。

2016 年，密码学家 Jens Groth 发表了文章“On the Size of Pairing-Based Non-interactive Arguments” (https://eprint.iacr.org/2016/260)，其中描述了一种异常高效的 zkSNARK。证明仅由三个群元素组成，并且可以通过计算三次配对运算来验证（与 BLS 签名相同的配对类型）。Zcash 协议采用了这一突破性成果，为其他多个 zkSNARK 奠定了基础。Groth 的 zkSNARK 通常仅称为 Groth16。

## 从陈述到证明

zkSNARKs 是最复杂的密码学构造之一，其最复杂和最昂贵的步骤之一是 *算术化*，一种操作将要证明的陈述转换为固定数量的多项式方程，通常形式为

$$a_0 + a_1 x + a_2 x^2 + a_3 x^3 + \dots + a_n x^n$$

对于次数为 \(n\) 的多项式，其中系数 \(a_i\) 是某个有限环或有限域结构的元素。证明算法随后处理多项式以创建 zkSNARK 证明。

算术化遵循通用工作流程：

1. 使用正式符号描述要证明的陈述，例如计算机程序、方程或逻辑公式。
2. 将步骤 1 中的正式表达式转换为 *电路*，该电路通过将一系列 *门* 应用于输入值来定义输入值的输出，类似于布尔或电子电路中的逻辑门，只是门可能是加法和乘法等代数运算。
3. 根据 zkSNARK 证明系统的约束系统将电路转换为结构化的 *约束* 列表。这些约束是输入必须满足的条件列表以满足要证明的陈述。

要证明的陈述可能像“我知道整数 \(x\) 和 \(y\) 满足方程 \(x^3 + y^2 + xy + 55 = 0 \bmod 57.\)”一样简单。这通过具有表达问题的正式方程完成了步骤 1。为了完成步骤 2，你可以将方程分解为涉及两个操作数的简单运算序列（Groth16 要求这样做）。这如下所示，其中你写出中间值 \(v_0, v_1, \dots, v_6\)：

- 设置 \(v_0 = x \times x\)。
- 设置 \(v_1 = x \times v_0\)；因此 \(v_1 = x^3\)。
- 设置 \(v_2 = y \times y\)。



## 不足的 Fiat–Shamir 哈希

想象一下，如果非交互式 Schnorr 证明不是 *c* = **H**(*G* || *R* || *A*)，而是 *c* = **H**(*G* || *A*)，使得挑战 *c* 与随机数 *R* 无关。攻击者随后选择 *s* 的任意值并计算 *R* = *sG* − *cA*。由此产生的证明由 *s* 和 *R* 组成并且是有效的，然而攻击者不需要知道 *a*，从而破坏了协议的健全性。

同样，如果 *c* = **H**(*G* || *R*)，在用于定义挑战 *c* 的哈希数据中省略公钥 *A*，则攻击是可能的：攻击者现在可以任意选择 *R* 和 *s* 值并计算点 *B* = (1/*c*) × (*sG* − *R*)，它满足 *sG* = *R* + *cB*。这给攻击者提供了对 *B* 的离散对数的知识证明——即 *b* 使得 *B* = *bG*——而他们实际上并不知晓。

这些攻击说明了在使用 Fiat–Shamir 变换使协议非交互时，在哈希函数输入中包含所有必要值的重要性。

## 重放攻击

重放是一种简单但可能破坏性的攻击。如果攻击者获知某个非交互式知识证明的值，他们可以将其发送给另一方并声称自己创建了它，从而为所证明的知识据为己有。

你可以通过将证明绑定到证明者的身份来避免这种情况，即在哈希的数据中包含其公钥。为了防止同一方随时间推移的重放，你可以将证明绑定到会话标识符或时间戳，通过在 Fiat–Shamir 哈希处理的数据中包含此类值。

## 随机性重用

考虑交互式 Schnorr 协议，其中验证者选择随机 *c*。如果证明者使用有缺陷的伪随机数生成器并两次重用相同的挑战 *r*，那么观察交换值的攻击者可以通过使用两个证明 *s₁* = *r* + *c₁a* 和 *s₂* = *r* + *c₂a* 来恢复秘密 *a*，针对两个不同的挑战 *c₁* 和 *c₂*，并计算 *a* = (*s₁* − *s₂*) / (*c₁* − *c₂*)。

## 真正严肃的密码学

随着本最后一章，我们回顾了截至撰写时密码学中最引人入胜的一些主题，既有理论也有实践观点。然而，我们仅触及了表面，尤其是在零知识证明系统领域，这是一个活跃的研究和工程领域，其应用远超区块链技术。但酷炫的密码学并不是区块链的万灵药。从诸如私有集合交集（PSI）等多方计算协议，到用于 AI 模型私有评估的同态加密，新的应用和用例需要更好、更快的密码学功能。

我们正在见证密码学的黄金时代，理论原则与实际应用前所未有地融合。这种协同作用为一些最令人望而生畏的安全和隐私问题提供了近乎魔法的解决方案。尽管如此，仍需解决重大挑战，尤其是在法律和监管领域。技术人员和政策制定者密切合作以应对这些挑战至关重要，并且双方都应努力理解彼此的观点。我希望本书，特别是最后一章，有助于揭开密码学的神秘面纱，使其对所有读者来说更易于理解、更少晦涩。

## 索引

### 数字

-   0-RTT 数据, 267
-   3DES（三重 DES），67，82–83。另见 DES

### A

-   A5/1, 21, 98–101
-   Aaronson, Scott, 185, 193, 281, 293
-   active attacker, 318
-   adaptive corruption, 318
-   Advanced Encryption Standard (AES), 61, 67
    -   AddRoundKey, 68–70
    -   block size, 62
    -   vs. DES, 67, 90
    -   and GCM, 164–167, 171, 173
    -   implementations, 71–74
    -   internals, 67–70
    -   KeyExpansion, 68–69
    -   MixColumns, 68–69
    -   with Poly1305, 148
    -   and provable security, 50
    -   security of, 73
    -   ShiftRows, 68–69
    -   SubBytes, 68–69
    -   and TLS 1.3, 265–266
-   Advanced Vector Extensions (AVX), 63
-   AEAD (authenticated encryption with associated data), 18, 160, 169–170
-   AES. See Advanced Encryption Standard
-   AES-CBC, 78
-   AESENC instruction, 72
-   AESENCLAST instruction, 73
-   AES-GCM
    -   efficiency, 166
    -   internals, 164–165
    -   security, 166
    -   and small tags, 173
    -   and weak hash keys, 171–173
-   AES native instructions (AES-NI), 72
-   AEZ, 174
-   aggregate signature protocols, 311–314
-   AKA (authenticated key agreement), 220–221
-   algebraic attacks, 96
-   Alvisi, Lorenzo, 136
-   amplitude, 274–279
-   Apple, 243, 246
-   application-specific integrated circuit (ASIC), 89
-   arithmetization, 328
-   associated data, 160
-   asymmetric encryption, 3, 18. See also RSA
-   attack costs, 47–49
-   attack models, 12
    -   black-box, 13–14
    -   gray-box, 14
    -   for key agreement protocols, 221
-   authenticated ciphers, 160
    -   with associated data, 160–161
    -   functional criteria, 163
    -   nonces, 161–162
    -   online, 163
    -   performance, 162–163
    -   permutation-based, 169–171
    -   security, 162
    -   streamability, 163
-   authenticated decryption, 160
-   authenticated Diffie–Hellman, 224–226
-   authenticated encryption (AE), 18, 157
    -   AES-GCM, 164–167, 171–173
    -   authenticated ciphers, 160–163
    -   OCB, 167–169
    -   permutation-based AEAD, 169–171
    -   SIV, 169
    -   using MACs, 158–160
-   authenticated encryption with associated data (AEAD), 18, 160, 169–170
-   authenticated key agreement (AKA), 220–221
-   authentication tag, 18. See also authenticated encryption; MACs
-   AVX (Advanced Vector Extensions), 63

### B

-   backtracking resistance, 30
-   backward secrecy, 30
-   BCryptGenRandom() function, 37–38
-   Bellare, Mihir, 155
-   Bellaso, Giovan Battista, 5
-   Bellcore attack, 211
-   Bernstein, Daniel J., 57, 106, 110, 148, 151, 244, 248, 283
-   big-number libraries, 206
-   bilinearity, 312
-   binary exponentiation, 207
-   birthday attacks, 120
-   birthday paradox, 120
-   Bitcoin, 116, 297, 299–302, 306, 307
-   bit security, 46–48
-   BLAKE, 131
-   BLAKE2, 115, 133–135, 143
    -   BLAKE2b, 134
    -   BLAKE2s, 134
    -   compression function, 134–135
    -   design rationale, 134
-   blinding attacks, 203
-   block ciphers, 61. See also Advanced Encryption Standard
    -   block size, 62–63
    -   CBC mode, 76–78
    -   codebook attacks, 63
    -   CTR mode, 80–82
    -   decryption algorithm, 62
    -   ECB mode, 74–76
    -   encryption algorithm, 62
    -   Feistel schemes, 66–67
    -   key schedule, 64
    -   meet-in-the-middle attacks, 82–83
    -   modes of operation, 74
    -   padding oracle attacks, 83–85
    -   round keys, 64–65
    -   rounds, 64
    -   security goals, 62
    -   slide attacks, 64–65
    -   substitution–permutation networks, 65–66
-   BLS curve, 312
-   BLS signature, 312–313
-   Bluetooth, 88
-   Boneh, Dan, 214
-   Bos, Joppe W., 251
-   broadcast attack model, 105
-   Brumley, David, 214
-   brute-force attacks, 45, 100–101

### C

-   CA (certificate authority), 258–262, 269–270
-   cache-timing attacks, 72
-   Caesar cipher, 4–5
-   CAESAR competition, 174
-   Canetti, Ran, 155
-   carry-less multiplication (CLMUL), 165
-   CBC. See cipher block chaining
-   CBC-MAC, 146–147
-   CCA (chosen-ciphertext attackers), 13–14
-   CCM (counter with CBC-MAC), 174, 265
-   CDH (computational Diffie–Hellman), 218–219
-   certificate authority (CA), 258–262, 269–270
-   certificate chain, 259, 269
-   ChaCha20, 106, 131, 151, 265
-   chaining values, 122
-   Chinese remainder theorem (CRT), 210–211
-   chosen-ciphertext attackers (CCA), 13–14
-   chosen-message attacks, 140
-   chosen-plaintext attackers (CPA), 13
-   Chrome browser, 129, 271
-   Chuang, Isaac, 293
-   cipher-based MAC (CMAC), 146–147
-   cipher block chaining (CBC), 76–78
    -   ciphertext stealing, 79
    -   padding, 78–79
    -   padding oracle attacks, 83–85
-   ciphers, 3
-   ciphertext, 4
-   ciphertext-only attackers (COAs), 13
-   ciphertext stealing, 79
-   circuit, 328
-   C language, 91
-   Clay Mathematics Institute, 50, 185
-   client certificate, 268
-   clique problem, 184
-   CLMUL (carry-less multiplication), 165
-   CMAC (cipher-based MAC), 146–147
-   CMAC-AES, 169
-   code-based cryptography, 285–286
-   codebook attacks, 63, 101
-   Codenomicon, 270
-   coding problems, 194
-   Cohen, Henri, 251
-   Cold War, 61
-   collision resistance, 119–120, 123, 305–306
-   completeness, 324
-   complexity. See computational complexity
-   complexity class, 182
-   complex numbers, 275
-   compression functions, 122
    -   in BLAKE2, 134–135
    -   Davies–Meyer construction, 124–125
    -   in Merkle–Damgård construction, 122
    -   in SHA-1, 127
-   computational complexity, 178
    -   bounds, 182
    -   classes, 182
    -   comparison, 180
    -   constant factors, 179
    -   constant time, 179
    -   exponential, 179–181
    -   exponential factorial, 181
    -   linear, 179
    -   linearithmic, 179
    -   polynomial, 180–183
    -   quadratic, 180
    -   superpolynomial, 180
-   computational Diffie–Hellman (CDH), 218–219
-   computational hardness, 178
-   computational security, 44–46
-   confidentiality, 3, 21, 116, 162
-   confusion, 65, 303
-   constant-time implementations, 154
-   Coppersmith, Don, 213
-   counter mode (CTR), 80–82, 102, 164
-   counter with CBC-MAC (CCM), 174, 265
-   CPA (chosen-plaintext attackers), 13
-   CRCs (cyclic redundancy checks), 116
-   CRT (Chinese remainder theorem), 210–211
-   CryptAcquireContext() function, 34
-   CryptGenRandom() function, 37
-   Crypto++, 214
-   Cryptocat, 41
-   cryptographic security, 43. See also security
-   CTR (counter mode), 80–82, 102, 164
-   cube attacks, 96
-   Curve448, 265
-   Curve25519, 248, 265
-   Curve41417, 248
-   CVP (closest vector problem), 287
-   cyclic redundancy checks (CRCs), 116

### D

-   Dahlin, Mike, 136
-   Damgård, Ivan, 122, 237
-   Data Encryption Standard. See DES
-   Datagram Transport Layer Security (DTLS), 257
-   Davies–Meyer construction, 124–125, 127, 134
-   decisional Diffie–Hellman (DDH) assumption, 219
    -   problem, 218–219
-   dedicated hardware, 90
-   DeMillo, Richard A., 214
-   DES (Data Encryption Standard), 61, 90
    -   vs. AES, 67, 90
    -   block size, 62
    -   double DES, 83
    -   Feistel schemes in, 66–67
    -   3DES, 67, 82–83




## D
- `/dev/random`, 36–37
- `/dev/urandom`, 34–37
- Diehard, 33
- 差分密码分析, 109
- Diffie, Whitfield, 195, 215
- Diffie–Hellman 问题, 194
- Diffie–Hellman 协议, 241
  - 匿名, 223–224
  - 认证, 224–227
  - CDH 问题, 218
  - DHI 问题, 218–219
  - 函数, 216–217
  - 参数生成, 217
  - 与密钥协商, 219–222, 241
  - MQV 协议, 227–228
  - 与共享密钥, 216, 228–229
  - 在 TLS 中, 215, 229, 264–265
  - 双生子问题, 219
  - 不安全的组参数, 229–230
- 扩散, 65–66, 304
- 摘要, 116
- DigiNotar, 269
- 数字签名, 116–117, 196, 202–205
- 离散对数问题 (DLP), 189–191
  - 与 CDH 问题, 218
  - ECDLP, 240–241
  - 与 Shor 算法, 281–282
- 不诚实多数, 318
- 分布, 26–27
- 域分离, 305–306
- drand48, 32
- DRBG (确定性随机比特生成器), 16, 30, 88
- DTLS (数据报传输层安全协议), 257
- Durumeric, Zakir, 40

## E
- ECB (电子密码本), 74
- ECC (椭圆曲线密码学), 231
- ECDH (椭圆曲线 Diffie–Hellman), 241, 249, 292
- ECDLP (椭圆曲线离散对数问题), 240–241
- ECDSA. *参见* 椭圆曲线数字签名算法
- ECIES (椭圆曲线集成加密方案), 246
- Ed25519, 244, 250
- Ed448-Goldilocks, 248
- EdDSA, 244
- Einstein–Podolsky–Rosen (EPR) 悖论, 274
- 椭圆曲线密码学 (ECC), 231
- 椭圆曲线 Diffie–Hellman (ECDH), 241, 249, 292
- 椭圆曲线数字签名算法 (ECDSA), 241, 321
  - 与不良随机性, 249
  - 与 RSA 签名相比, 243–244
  - 签名生成, 242
  - 签名验证, 242–243
- 椭圆曲线离散对数问题 (ECDLP), 240–241
- 椭圆曲线集成加密方案 (ECIES), 246
- 椭圆曲线, 231
  - 加法定律, 235
  - Curve25519, 248, 265
  - Curve41417, 248
  - Curve448, 265
  - Edwards 曲线, 233, 244
  - 群, 239–240
  - 与整数, 233–234
  - NIST 曲线, 247–248
  - 阶, 240
  - 配对, 312
  - 无穷远点, 236, 239–240, 314
  - 点加倍, 237–238
  - 点乘, 238–239
  - 素数曲线, 247
  - Weierstrass 形式, 232
- 尴尬的并行, 48, 100
- 封装安全有效载荷 (ESP), 263
- 加密与 MAC, 158–159
- 加密, 3
  - 非对称, 18
  - 静态, 17
  - 传输中, 17
  - 随机化, 15–16
  - 安全, 12
- 加密-then-MAC, 158, 159–160, 164
- 纠缠, 274, 277

## I
- 离子阱, 284
- ipad, 144
- IPSec (互联网协议安全), 140, 144, 146, 160, 164, 263
- 迭代哈希, 122
- IV (初始向量), 76, 81, 89, 122, 147

## J
- Jager, Tibor, 250
- Java, 22, 32, 152
- JH, 131

## K
- KDF. 参见 密钥派生函数
- Keccak, 126, 131–133, 171. 另见 SHA-3
- Kelsey, John, 30, 41, 50
- Kerckhoffs, Auguste, 6, 13
- Kerckhoffs 原则, 13
- 密钥协商协议, 53, 216, 219
  - AKA, 220–221
    - 攻击模型, 221
    - 违规, 221, 225, 228
    - 数据泄露, 221, 226, 268
    - 窃听者, 216, 218
    - 前向保密, 221–222, 225, 228
    - 性能, 222
    - 安全目标, 221
- 密钥抵消攻击, 309–310, 315–316
- 密钥确认, 226, 228
- 密钥控制, 221, 225
- 密钥派生函数 (KDF), 53
  - 在 DH 函数中, 216, 229
  - 在 ECIES 中, 246
  - 在 TLS 1.3 中, 265–266
- 密钥生成, 39, 40, 198, 323
- 密钥生成算法, 53, 54
- 密钥管理, 323
- 密钥调度算法 (KSAs), 102–104
- 密钥封装, 55
- 背包问题, 184
- 知识提取器, 326
- 已知消息攻击, 140
- 已知明文攻击者 (KPAs), 13, 100
- Knudsen, Lars, 51

## L
- 拉格朗日插值, 319
- 基于格的密码学, 286–287
- 格问题, 194, 287, 291
- 带错误的学习 (LWE), 286, 291
- 最低有效位 (LSB), 179, 207
- 长度扩展攻击, 135–136, 142–143
- Let’s Encrypt, 271
- Leurent, Gaëtan, 155
- 线性码, 285–286
- 线性组合, 33
- 线性反馈移位寄存器 (LFSRs), 93
  - 在 A5/1 中, 98–100
  - 滤波, 95–96
  - 在 Grain-128a 中, 97–98
  - 多项式, 93
  - 安全, 95
- 线性变换, 33, 93, 287
- Linux, 34, 36, 74, 152
- Lipton, Richard J., 214
- 对数, 27, 46
- 长期密钥, 225
- 下界, 45
- 低指数攻击, 209
- LSB (最低有效位), 179, 207
- Lucifer, 66
- LWE (带错误的学习), 286, 291

## M
- MacBook, 154, 191, 209
- MACs (消息认证码), 139
  - 认证标签, 140
  - CBC-MAC, 146–147
  - 选择消息攻击, 140
  - CMAC, 146–147
  - 专用设计, 148
- MACs (续)
  - 加密与 MAC, 158–159
  - 加密-then-MAC, 158, 159–160, 164
  - 伪造攻击, 140
  - HMAC, 144–146
  - MAC-then-encrypt, 158–160
  - 与 PRFs 相比, 141–142
  - 重放攻击, 141
  - 时序攻击, 140–142
  - Wegman–Carter, 149–150
- MAC-then-encrypt, 158–160
- MacWilliams, F.J., 148
- 可塑性, 199–200
- 中间人攻击, 220, 223–224, 256
- 掩码生成函数, 202
- 矩阵乘法, 278
- McEliece 密码系统, 285–286
- MD5, 122, 127, 133
- M–D 构造. 参见 Merkle–Damgård 构造
- 测量 (量子物理), 274, 278
- MediaWiki, 40
- 中间相遇 (MitM) 攻击, 82–83
- 内存, 48
- 内存占用, 63
- Menezes–Qu–Vanstone (MQV), 227–228, 241
- Merkle, Ralph, 122, 137, 216, 297
- Merkle–Damgård (M–D) 构造, 122
  - 长度扩展攻击, 135–136, 142–145
  - 多重碰撞, 123–124
  - 填充, 123
  - 安全, 123
- Merkle 的谜题, 216
- Mersenne Twister (MT) 算法, 32, 40, 305
- 消息认证码. 参见 MACs
- Micali, Silvio, 22
- Microsoft, 111, 131
- Microsoft Windows CryptoAPI, 208
- 误用抗性, 162
- MitM (中间相遇) 攻击, 82–83
- 工作模式, 7–8, 61, 74
- Moore, Jonathan, 251
- 最高有效位 (MSB), 32, 147, 150, 229
- MQ (多元二次), 287
- MQV (Menezes–Qu–Vanstone), 227–228, 241
- MT (Mersenne Twister) 算法, 32, 40, 305
- mt_rand, 32, 40
- 多重碰撞, 123–124
- 多方计算 (MPC), 316
- 多签名协议, 306
- 多元密码学, 287–288
- 多元问题, 194
- 多元二次 (MQ), 287
- MuSig, 310–311

## N
- Naehrig, Michael, 251, 312
- Netscape, 39, 257
- 基于网络的入侵检测系统 (NIDS), 115
- Neves, Samuel, 133, 135
- NFSR (非线性反馈移位寄存器), 96–98
- Nguyen, Phong Q., 155
- Nielsen, Michael, 293
- NIST (美国国家标准与技术研究院), 33, 61, 67, 129–131, 247–248, 289–291
- NM (不可塑性), 15
- 随机数, 80–82, 88–89
  - 可预测性, 161–162
  - 重用, 111, 169
  - 在 TLS 记录中, 263
  - WEP 不安全, 103–104
- 非确定性多项式时间类. 参见 NP 类
- 非交互式零知识 (NIZK), 326–327
- 非线性方程, 33, 96
- 非线性反馈移位寄存器 (NFSR), 96–98
- 不可塑性 (NM), 15
- 不可否认性, 202
- 非均匀分布, 27
- NP (非确定性多项式时间) 类, 182–183
  - NP-完全问题, 183–185
  - NP-难问题, 185–186
- NSA (美国国家安全局), 10, 85, 105, 127, 129, 227, 244, 247, 273
- NSS 库, 214
- 数域筛, 218

## O
- OAEP. 参见 最优非对称加密填充
- OCB (偏移码本)
  - 效率, 168–169
  - 内部机制, 167–168
  - 安全, 168
- 一次性密码本, 9
  - 使用加密, 9–10
  - 安全, 10–11, 12, 44
- 单向函数, 117
- opad, 144
- OpenSSH, 148, 159, 231, 246, 248
- OpenSSL 工具包
  - 生成 DH 参数, 217
  - 生成密钥, 53–54, 192–193
  - GHASH 漏洞, 165
  - Heartbleed, 256, 270
  - 不安全的 DH 组参数, 229–230
- 最优非对称加密填充 (OAEP), 56, 200
  - 编码消息, 201
  - 掩码生成函数, 202

## P
- P (多项式时间) 类, 180–185
- P 与 NP, 185–186
- 填充, 22, 78–79, 83–84, 123
  - OAEP, 56, 200
  - 零填充, 263
- 填充预言机攻击, 22, 83–84
- 配对, 312
- 并行性, 47–48
- 可并行性, 162, 166, 168
- 父进程 ID (PPID), 39
- 被动攻击者, 318
- 密码, 53, 55, 141
- Peikert, Chris, 291
- 完美保密, 9
- 周期, 92–94, 97–98, 281–282
- 置换, 6
- 基于置换的 AEAD, 169–171
- 伪随机
  - 安全, 7, 8–9
  - 在海绵函数中, 125–126
  - 陷门, 196, 197–199
- PID (进程 ID), 39
- 鸽巢原理, 119
- PKCS (公钥密码学标准), 200–201
- 明文, 4
- PLD (可编程逻辑器件), 89
- Poly1305, 148–151
- Poly1305-AES, 150–151
- 多项式, 93
  - 乘法, 165–166
  - 原始, 93–94
- 多项式时间 (P) 类, 180–185
- 后量子密码学, 274, 285
  - 基于编码, 285–286
  - 基于哈希, 288–289
  - 基于格, 286–287
  - 多元, 287–288
- 后量子密码学标准化项目, 289
- 后量子安全, 283, 304
- 功耗分析攻击, 208
- PPID (父进程 ID), 39
- PQCrypto, 293
- 预计算, 48, 222
- 预测抗性, 30
- 原像抗性, 117–119
- Preneel, Bart, 137
- 预共享密钥 (PSK), 265, 267
- PRFs. 参见 伪随机函数
- 素数, 187
- 素数定理, 187
- 私钥, 18, 195
- PRNGs. 参见 伪随机数生成器
- 概率签名方案 (PSS), 203–205
- 概率, 11, 26





## P

- 概率分布，26–27
- 进程 ID（PID），39
- 可编程逻辑器件（PLD），89
- 存储证明协议，136–137
- 工作量证明，300
- 可证明安全性，50–53
- 伪随机函数（PRF），139
    - 与 MAC 的对比，141–142
    - 安全性，141
- 伪随机数生成器（PRNG），28–30
    - 密码学安全的，32–33
    - 与熵，39–40
    - Fortuna，30–31
    - 在 Unix 上生成，34–36
    - 在 Windows 上生成，37–38
    - 基于硬件的，38
    - 非密码学安全的，32，40
    - 安全性，30
- 伪随机置换（PRP），62，67，150
- PSK（预共享密钥），265，267
- PSPACE，182
- PSS（概率签名方案），203–205
- 公钥密码学，18，231
- 公钥密码标准（PKCS），201
- 公钥密码系统，215
- 公钥，195
- PyCrypto，70
- 勾股定理，275
- Python 语言，70，75，80–81，102，212

## Q

- Qualys，271
- 量子比特（qubit），274，276–279，284
- 量子字节，277
- 量子电路，278
- 量子计算机，188–189，274
- 量子门，277–279
- 量子力学，274
- 量子随机数生成器（QRNG），29
- 量子加速，279
    - 指数级，280
    - 二次级，280
- 四分之一轮函数，106–107
- qubit（量子比特），274，276–279，284

## R

- 随机性，25
- 随机数生成器（RNG），28–29
- 随机预言机，117
- Ray, Marsh，74
- RC4，89，102
    - 被攻破的实现，111–113
    - 在 TLS 中，104–105
    - 在 WEP 中，103–104
- RDRAND 指令，38
- RDSEED 指令，38
- 规约，50
- 重放攻击，142，220，330
- ρ 方法，120–121
- Rijndael，67
- ring-LWE，291
- Rivest, Ron，102
- Rivest–Shamir–Adleman。*参见* RSA
- RNG（随机数生成器），28–29
- Rogaway, Phillip，168，169
- 流氓密钥攻击，310
- 单位根，212
- 轮数，53
- 往返，222
- 往返时间（RTT），267
- RSA（Rivest–Shamir–Adleman），195
    - Bellcore 攻击，211–212
    - CRT，210–211
    - 与 ECDSA 的对比，243–244
    - 加密，199
    - 与因数分解问题，50–51，186
    - FDH，205
    - 群，196–197
    - 实现，205–206
    - 密钥生成，208–209
    - 模数，212
    - OAEP，200–202
    - 私有指数，212–213
    - 私钥，54，197，198
    - 问题，218
    - PSS，203–204，205
    - 公共指数，197
    - 公钥，197
    - 秘密指数，197
    - 安全性，198
    - 共享模数，212–213
    - 签名，202–205
    - 小指数，208–209
    - 速度，208–210
    - 平方-乘，207–208
    - 教科书式加密，199–200
    - 教科书式签名，203
    - 陷门置换，196，197，199
- RSAES-OAEP，200
- RSA Security，102
- RTT（往返时间），267

## S

- Saarinen, Markku-Juhani O., 132，173
- 安全素数，217
- SageMath，191，198，239
- Salsa20，106
    - 攻击，110–111
    - 列轮函数，108
    - 双轮函数，107
    - 内部状态，107
    - 与非线性关系，110
    - 四分之一轮函数，106–107
    - 行轮函数，107
- Salsa20/8，110–111
- 盐，204
- 三明治 MAC，144
- 卫星电话，113
- S 盒（替换盒），65
- 调度问题，184
- Schneier, Bruce，30，31，41，131
- Schnorr, Claus-Peter，244，307
- Schnorr 签名协议，307–309
- Schnorr 的知识证明协议，325–326
- Schwenk, Jörg，250
- 可搜索加密，20
- 搜索算法，178
- 第二原像抗性，118
- 秘密前缀 MAC，143，145
- 秘密共享，319
    - 加法式，319
    - 门限式，319
- 秘密后缀 MAC，143
- 安全信道，216，256
- 安全 cookie，268
- 基于 Keccak 的安全哈希算法（SHAKE），132
- 安全外壳（SSH），55，140，144，159，160，241，262
- 安全套接层（SSL），39，255，257
- 安全性
    - 比特，46–47
    - 计算，44–45
    - 密码学，43
    - 目标，12，15
    - 启发式，50，52–53
    - 等级的选择，49–50
    - 安全裕度，53
    - 概念，12，15–17
    - 后量子，283
    - 证明，46
    - 可证明，50–52
    - 语义，15，16
- 会话密钥，53，219
- SHA-0，127–128
- SHA-1，127–129，266
- SHA-2，129–133
- SHA-224，129–130
- SHA-256，117，123，129–130，242，297，300
    - 压缩函数，130，146
    - 安全性，130–131，297
- SHA-3，126，132–133，229
    - 竞赛，131–132
    - 安全性，133–134
    - Zoo，137
- SHA-384，130
- SHA-512，130
- SHAKE（基于 Keccak 的安全哈希算法），132
- Shamir 的秘密共享，319
- Shannon, Claude，10
- SHA（安全哈希算法），126
- Shor, Peter，281
- Shor 算法，281–282
- 短整数解（SIS），286
- Shrimpton, Tom，169
- 侧信道攻击，14，65，153，292
- Signal，292
- 签名，116，196，202–205
- SIM 卡，220
- Simon 问题，280–281
- 简单邮件传输协议（SMTP），229，257
- 模拟器，326
- SipHash，151–152，155
- SipRound 函数，151–152
- SIS（短整数解），286
- SIV（合成 IV），169
- Skein，131
- 滑动攻击，64–65
- 滑动窗口方法，208
- Sloane, N.J.，149
- SM3，127
- SMTP（简单邮件传输协议），229，257
- SNOW3G，102
- Somorovsky, Juraj，250
- 可靠性，324
- 空间复杂度，182
- SPHINCS+，289–290
- SPN（替换-置换网络），65–66，68
- 海绵函数，122，125–126，155
    - 吸收阶段，126
    - 容量，126
    - 挤压阶段，126
- 平方-乘，207–208
- SSH（安全外壳），55，140，144，159，160，241，262
- SSL（安全套接层），39，255，257
- SSL Labs，271
- 静态腐败，318
- 统计检验，33–34
- 流式支持，163，167–169
- 流密码，87
    - 基于计数器的，89
    - 加密与解密，88
    - 面向硬件的，89–90
    - 密钥流，88
    - nonce 重用，111
    - 面向软件的，101
    - 有状态的，89
- Streebog，127
- 替换盒（S 盒），65
- 替换-置换网络（SPN），65–68
- 替换，7
- 超导电路，284
- 叠加态，274
- 对称加密，3，18
- 合成 IV（SIV），169

## T

- 标签，18。另见 认证加密；MAC
- TEA，137
- 门限签名协议，316
- 时间复杂度，180–182
- 时间-内存权衡（TMTO）攻击，21，48，101
- 时序攻击，153–154，208，292
- TLS（传输层安全），39，88，140，142，159，255
    - ClientHello，257，264–267
    - 与 Diffie–Hellman，229
    - 降级保护，266–267
    - 握手，257，258–268
    - 历史，257
    - 其中的 RC4，102，104–106
    - 记录，262
    - 记录负载，262
    - 记录协议，257，262
    - 安全性，256，268–271
    - ServerHello，257，264–267
    - 会话恢复，267–268
    - 单次往返握手，267
    - 1.3 版，265–267
    - 零填充，263
- TLS 工作组（TLSWG），271
- TMTO（时间-内存权衡）攻击，21，48，101
- TOFU（首次使用信任），262
- 流量分析，263
- 传输层安全。另见 TLS
- 陷门置换，196，197，199
- 陷门，196，197–199
- 旅行商问题，184
- 三重 DES（3DES），67，82–83
- 可信第三方，258
- 首次使用信任（TOFU），262
- 图灵奖，216
- 可调加密（TE），20–21

## U

- UDP（用户数据报协议），257
- 不可伪造性，140
- 均匀分布，27

*Serious Cryptography*（第 2 版）使用 New Baskerville、Futura、Dogma 和 TheSansMono Condensed 字体排版。

## 资源

请访问 *https://nostarch.com/serious-cryptography-2nd-edition* 以获取勘误和更多信息。

来自 [No Starch Press](https://nostarch.com/) 的更多实用书籍

![](img/ace4de942d037de8ea5835bc9fbe57cd_376_0.png)

![](img/ace4de942d037de8ea5835bc9fbe57cd_376_1.png)

### 黑帽 Python（第 2 版）

**面向黑客与渗透测试者的 Python 编程**  
*作者：Justin Seitz 和 Tim Arnold*  
216 页，$44.99  
ISBN 978-1-7185-0112-6

![](img/ace4de942d037de8ea5835bc9fbe57cd_376_2.png)

### 攻击网络协议

**黑客的捕获、分析与利用指南**  
*作者：James Forshaw*  
336 页，$49.95  
ISBN 978-1-59327-750-5

![](img/ace4de942d037de8ea5835bc9fbe57cd_376_3.png)

### 密码学词典

**为好奇的密码学家准备的 500 个有趣小知识**  
*作者：Jean-Philippe Aumasson*  
160 页，$24.99  
ISBN 978-1-7185-0140-9

![](img/ace4de942d037de8ea5835bc9fbe57cd_376_4.png)

### TCP/IP 指南

**一本全面、图文并茂的互联网协议参考书**  
*作者：Charles M. Kozierok*  
1,616 页，$99.95  
ISBN 978-1-59327-047-6

![](img/ace4de942d037de8ea5835bc9fbe57cd_376_5.png)

### 随机性的艺术

**现实世界中的随机化算法**  
*作者：Ronald T. Kneusel*  
400 页，$49.99  
ISBN 978-1-7185-0324-3

![](img/ace4de942d037de8ea5835bc9fbe57cd_376_6.png)

### 工程化安全设备

**嵌入式系统架构师与开发者的实用指南**  
*作者：Dominik Merli*  
288 页，$59.99  
ISBN 978-1-7185-0348-9

**电话：**  
800.420.7240 或  
415.863.9900  

**电子邮件：**  
SALES@NOSTARCH.COM  

**网址：**  
WWW.NOSTARCH.COM




> “对密码工程进行透彻且与时俱进的讨论，旨在帮助计划从事该领域从业者做得更好。”
>
> —Matthew D. Green，约翰霍普金斯大学信息安全研究所教授

本书是畅销的现代密码学入门书籍的彻底修订和更新版，它在不回避深入讨论其工作原理的情况下拆解了基础数学概念。在这本实用指南中，你将对诸如认证加密、安全随机数、哈希函数、分组密码以及 RSA 和椭圆曲线密码学等公钥技术等主题获得无可估量的洞见。

你将找到以下主题的介绍：

- 计算安全的基础、攻击者模型和前向保密
- HTTPS 安全网站背后 TLS 协议的优势和局限性
- 量子计算和后量子密码学
- AES、ECDSA、Ed25519、Salsa20 和 SHA-3 等算法的工作原理
- 多签名、阈值签名和零知识证明等高级技术

每章都包含使用真实案例讨论常见实现错误，并详细说明可能出现什么问题以及如何避免这些陷阱。而且，忠于原著，你将获得恰到好处的数学知识，以展示算法的工作原理，从而让你理解特定解决方案为何有效——以及它们是如何被攻破的。

**本版新内容：** 本第二版已彻底更新，以反映密码学领域的最新发展。你还将找到一章全新内容，涵盖加密货币和区块链系统中的密码学协议。

无论你是经验丰富的从业者，还是希望深入该领域的初学者，*严肃密码学*都将阐明这一常常令人望而生畏的主题。你将逐渐理解现代加密及其应用，以便在何时、何地以及如何实现方面做出更好的决策。

## 关于作者

**Jean-Philippe (JP) Aumasson** 拥有密码学博士学位，并撰写了 60 多篇研究论文。他的密码学算法 BLAKE2 和 SipHash 运行于每一套 Linux 系统中，而他的 BLAKE3 以其卓越的速度而闻名。Aumasson 目前担任 Taurus SA 的首席安全官，也进行密码学培训，并在 Black Hat、DEF CON、Troopers 和 Infiltrate 等全球领先会议上发表演讲。
