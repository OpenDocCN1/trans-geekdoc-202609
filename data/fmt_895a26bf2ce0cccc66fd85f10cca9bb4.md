
ZKP implementations are claimed by many computer vendors. Like other computer security buzzwords before it (such as artificial intelligence `AI` or blockchain), ZKP is overused. It is incorrectly used by many vendors to inaccurately describe far more offerings than really use it. So, be initially skeptical whenever you see a vendor using the ZKP phrase. With that said, cryptographers are a fairly serious and truthful group of people. When a cryptography says their algorithm uses ZKP, they usually aren't saying it lightly or without support. ZKP cryptography typically involves proving knowledge of something cryptographic, such as a discrete logarithm function, without revealing the function itself. In crypto circles, you may hear the “prove and verify” steps also referred to as `sigma protocols` or (three-step or three-message) proofs. The only submitted quantum-resistant algorithm that uses ZKP is the Picnic digital signature scheme.

### Symmetric Key Quantum Resistance

This refers to the inherent ability of traditional symmetric key encryption and authentication algorithms to resist quantum attacks. As covered previously, symmetric ciphers are not susceptible to Shor's algorithm, and Grover's algorithm cuts their protection in half. So, in a sense, symmetric key ciphers are already quantum-resistant, as long as their key sizes are of sufficient size to fight off Grover algorithm attacks. Today, this means using symmetric ciphers with key sizes of 256 bits and longer for long-term protection. NIST and others will accept symmetric ciphers with 128-bit keys as being weakly quantum-resistant, with 192-bit symmetric keys considered moderately quantum-resistant. Accordingly, symmetric ciphers are not in NIST's latest post-quantum contest.

All the submitted algorithms use traditional symmetric key ciphers and hashes as part of their implementation. The most common symmetric cipher used in the world today is Advanced Encryption Standard (AES), and this also holds true for quantum-resistant ciphers. Most quantum-resistant ciphers use AES.

You will also see the SNOW 3G quantum-resistant symmetric cipher, although it is far less popular and is not used in any submitted cipher proposal. SNOW is a word-based, synchronous stream cipher, developed by Swedes Thomas Johansson and Patrik Ekdahl at Lund University. SNOW (version 1), SNOW 2.0, and SNOW 3G (adapted for cellular network use) are implemented in several products and applications. You can get more detail on SNOW and SNOW 3G here: `www.gsma.com/aboutus/wp-content/uploads/2014/12/uea2designevaluation.pdf`.

All submitted ciphers also use traditional hashes, which like symmetric key encryption are not susceptible to Shor's algorithm. Most use SHA-3 (another NIST standard), although many also use SHAKE, a stream cipher, which is used by SHA-3 as well. Quantum-resistant ciphers must use the appropriate key lengths of these traditional ciphers to remain quantum-resistant, and what key size a submitter used often changed relatively to the NIST security level they were trying to meet with a particular implementation.

Table 6.2 shows all the NIST Round 2 algorithm names along with their cryptography types.

All of these types of algorithms have been used to create quantum-resistant cryptography, and each will be summarized in the next section.

**Table 6.2** #c06.xhtml#R_c06-tbl-0002**:** NIST Round 2 cryptography types

| Asymmetric encryption/KEMs | | Type | | Signatures | | Type |
| --- | --- | --- | --- | --- | --- | --- |
| CRYSTAL-Kyber | | Lattice | | CRYSTALS-Dilithium | | Lattice |
| --- | --- | --- | --- | --- | --- | --- |
| FrodoKEM | | Lattice | | FALCON | | Lattice |
| LAC | | Lattice | | qTESLA | | Lattice |
| NewHope | | Lattice | | SPHINCS+ | | Hash |
| Three Bears | | Lattice | | GeMSS | | Multivariate |
| NTRU | | Lattice | | LUOV | | Multivariate |
| NTRU Prime | | Lattice | | MQDSS | | Multivariate |
| SABER | | Lattice | | Rainbow | | Multivariate |
| Round5 | | Lattice | | Picnic | | Zero-knowledge proof |
| Classic McEliece | | Code | |  | |  |
| NTS-KEM | | Code | |  | |  |
| BIKE | | Code | |  | |  |
| HQC | | Code | |  | |  |
| LEDAcrypt | | Code | |  | |  |
| Rollo | | Code | |  | |  |
| RQC | | Code | |  | |  |
| SIKE | | Isogeny | |  | |  |

### Quantum-Resistant Asymmetric Encryption Ciphers

Quantum-resistant ciphers are cryptographic ciphers that are not overly susceptible to quantum computers running quantum-based algorithms and, in particular, Shor's algorithm (or any quantum algorithm that can factor large prime number equations very fast). They do not use quantum-based properties to defeat attacks. There are dozens of quantum-resistant ciphers, although one or more of the 17 Second Round NIST asymmetric encryption candidates are likely to be one of the eventual NIST federal standards. The NIST Second Round asymmetric PKE and KEM candidates (in alphabetic order) are as follows:

* BIKE
* Classic McEliece
* CRYSTALS-Kyber
* FrodoKEM
* HQC
* LAC
* LEDAcrypt
* NewHope
* NTRU
* NTRU Prime
* NTS-KEM
* ROLLO
* Round5
* RQC
* SABER
* SIKE
* ThreeBears

Some of these 17 ciphers are combinations of multiple ciphers submitted separately in the first contest round that were combined into a single cipher family with similar characteristics. For example, HILA5 and Round2 eventually became Round 5.

> **NOTE** Algorithm names are all capitals or initial-capped according to their creator's original use. Names in all caps are usually abbreviations standing for longer whole-word names.

> **注意**  此列表绝不包含所有可能的强抗量子非对称算法。许多现有的抗量子密码算法（非对称和数字签名）因多种原因未被提交，包括创作者不愿免费公开其算法；许多在提交后被攻击并被破解（其中 22 个）；许多提交论文较弱或未满足 NIST 接受标准（例如 XMSS、LMS 和 BPQS）。最初提交供第一轮考虑但未进入第二轮的算法包括以下：BIG QUAKE、CFPKM、Compact LWE、DAGS、DME、DRS、DualModeMS、Edon-K、EMBLEM/R.EMBLEM、Giophantus、Guess Again、Gui、HiM-3、HK17、KCL、KINDI、Lepton、LIMA、Lizard、LOTUS、McNie、Mersenne-756839、pqNTRUSign、Odd Manhattan、Post-quantum RSA-Encryption、Post-quantum RSA-Signature、QC-MDPC KEM、RaCOSS、Ramstake、RankSign、RLCE-KEM、RVB、SRTPI、Titanium 和 WalnutDSA。此外，还有数十种未被提交的抗量子算法，包括 GGH、XMSS 和 UOWHF。这些密码算法已被或可能被其他标准机构和国家接受。

#### BIKE

Bit Flipping Key Encapsulation (`BIKE`) 是一套基于编码的 KEM。由一个多国团队创建（主要来自法国，但也有德国、以色列和美国的参与者），它有三种不同的变体，称为 `BIKE-1`、`BIKE-2` 和 `BIKE-3`。它基于 McEliece 加密、`QC-MDPC`（准循环中等密度奇偶校验码）、`CAKE`、`Ouroboros`（未单独进入第二轮的第一轮 NIST 候选算法）以及临时密钥。*临时密钥* 是为每次密钥建立过程生成的密码密钥，而不是使用单一的静态密钥。临时密钥允许密码使用完美前向保密。

`BIKE` 的性能和密钥大小与基于格的密码系统相似。对于 NIST 所需安全实现第二轮开始阶段，密钥大小范围为 1,988 至 4,110 字节，公钥范围为 20,326 至 65,498 字节，密文范围为 20,326 至 65,498 字节。`BIKE` 在所有提交候选中拥有最大的公钥和密文之一，尽管其密钥大小排名中等。一个相当有趣的特征，仅为少数其他抗量子密码所共有，是 `BIKE` 加密的数据具有可识别的“签名”，可被对手和安全控制用于识别和操作它。通常你无法分辨大多数加密使用了何种密码，这使任何攻击都变得复杂。对 `BIKE` 来说并非如此。`BIKE` 是 Open Quantum Safe 项目的一部分。

有关 `BIKE` 的更多信息，请访问：`https://bikesuite.org/`。

#### Classic McEliece

1978 年，Robert J. McEliece 创建了一种公钥密码，已抵御了 40 多年的攻击。它是一种基于编码的密码，使用 Goppa 码。McEliece 1978 年介绍 McEliece 公钥加密的论文可在以下位置找到：`https://ipnpr.jpl.nasa.gov/progress_report2/42-44/44N.PDF`。

> **注意**  你经常会在与 McEliece 相同的场合看到相关的 Niederreiter 密码系统被提及。Niederreiter 密码系统速度更快，可用于数字签名。

原始 McEliece 速度快（与 RSA 相比）且抗量子，但需要较大的密钥大小（300 KB 及以上，通常大于 1 MB）。多年来，多个团队尝试对其进行修改以减小所需的密钥大小，但最终几乎所有新实现都被发现比原始版本安全性低得多。

NIST 提交团队，其中包括备受推崇的密码学家和安全编码软件开发者 Daniel J. Bernstein，成功修改了 McEliece，使其能够使用减小后的密钥大小，同时保持抗量子且零解密失败。对于 NIST 所需安全实现第二轮开始阶段，密钥大小范围为 6,452 至 13,892 字节，公钥范围为 261,120 至 1,044,992 字节，密文范围为 128 至 240 字节。Classic McEliece 拥有第二大的公钥大小，仅次于 NTS-KEM。两者均具有最小的密文。虽然仍然明显大于传统公钥密码和大多数抗量子竞争对手，但使用当今的计算机和网络已非常可行。Classic McEliece 还有额外优势，即密文大小非常小，且在基于硬件的实现中速度非常快。

有关 Classic McEliece 的更多信息，请访问 `https://classic.mceliece.org`。

> **注意**  如果你对密码学或编写安全代码感兴趣，Daniel J. Bernstein 撰写或发布的任何内容都备受尊重。他已发表数百次演讲，撰写了几乎同样多的论文，并开发了许多不同、非常安全、缺陷极少的程序。他发明了 *post-quantum cryptography* 一词，并是早期让世界意识到即将到来的问题的领导者之一。读者被鼓励访问他的个人网站：`https://cr.yp.to`。

#### CRYSTALS-Kyber
