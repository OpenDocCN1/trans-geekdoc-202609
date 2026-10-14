
Blowfish 是一种对称块加密算法，于 1993 年由 Bruce Schneier 发布，他表示 Blowfish 无专利，并在所有国家均保持此状态。他将算法置于公共领域，供任何人自由使用，这使得 Blowfish 在开源工具中广受欢迎。

**Note**

Schneier 是一位广为人知的美国密码学家，因在 Blowfish 和 Twofish 加密算法上的工作以及对多种密码的深入密码分析而著称。他还撰写了书籍 `Applied Cryptography: Protocols, Algorithms, and Source Code in C`（Wiley, 1996）。Schneier 维护安全博客，广泛撰写关于网络安全和密码学相关主题的文章。

Blowfish 加密算法的设计初衷是作为 DES 的替代。与 DES 类似，它是一个 16 轮的费istel网络，工作块大小为 64 位。然而，与 DES 不同，它支持从 32 位到 448 位不等的可变密钥长度。在密码的早期阶段，密钥会被展开。密钥展开将最多 448 位的密钥转换为若干子密钥数组，总计 4168 字节。

该算法本身是费istel 网络，因此第一步是将块分为两半。例如，64 位块被分为 L[0] 和 R[0]。随后进行 16 轮处理。

S-盒是依赖于密钥的（如本节后面所示）。这意味着它们并非像 DES 那样固定标准，而是根据密钥计算得出。共有四个 S-盒，每个 32 位大小，包含 256 个条目：

`s1/0`, `s1/1`, `s1/2`...`s1/255`

`s2/0`, `s2/1`, `s2/2`...`s2/255`

`s3/0`, `s3/1`, `s3/2`...`s3/255`

`s4/0`, `s4/1`, `s4/2`...`s4/255`

Blowfish 使用多个子密钥（也称为轮密钥）。密码的第一步是从原始密钥生成这些子密钥。这始于名为 `P-数组` 的数组。P-数组的每个元素初始化为 π 的十六进制数字，仅保留小数点后的数值。每个 P-数组元素为 32 位。以下是 π 的前几位十进制数值：

![Images](Images/image00629.jpeg)

以下是相同数值的十六进制表示：

![Images](Images/image00630.jpeg)

P-数组共有 18 个元素，每个 32 位。它们分别标记为 P1、P2 … 到 P18。四个 S-盒同样为 32 位，也初始化为 π 的数字。随后，前 32 位密钥与 P1 异或，接下来的 32 位密钥与 P2 异或，以此类推，直到整个 P-数组都与密钥的片段异或完毕。此时，P-数组的每个元素都等于 π 的十六进制数字与密钥片段异或后的结果。

下一步可能看起来有些困惑，请仔细关注。你取一个全零字符串，使用刚才生成的子密钥（即 P-数组）对其进行 Blowfish 加密。然后将 P1 和 P2 替换为该加密结果。再次使用 Blowfish 加密该结果，这次使用已修改的密钥（P1 和 P2 已在上一步中被更新）。将该加密结果替换 P3 和 P4。此过程持续进行，直至 P-数组的所有条目以及四个 S-盒全部被当前不断演变的 Blowfish 算法的输出所取代。^([3](#part0015.xhtml#ch06note3a))

尽管密钥调度复杂，但轮函数本身相当简单：

**1.** 将 32 位的一半分为 4 个字节，分别记为 a、b、c、d。

**2.** 然后应用下面的公式。^([4](#part0015.xhtml#ch06note4a))

F 函数为：`F(xL) = ((S1,a + S2,b mod 2^(32)) XOR S3,c) + S4,d mod 2^(32)` 该过程可在 [Figure 6-8](#part0015.xhtml#ch06fig08) 中看到。

![Images](Images/image00631.jpeg)

* * *

**FIGURE 6-8    Blowfish round function**

#### Twofish

Twofish 是 AES 竞赛的五个最终候选者之一（我们将在后续章节详细探讨），它与 Blowfish 加密算法相关，Bruce Schneier 曾参与该团队的工作。Twofish 是一种费istel 网络，块大小为 128 位，支持 128、192 和 256 位密钥长度，同样拥有 16 轮，如同 DES。由于它不受专利保护且处于公共领域，任何人均可自由使用。

与 Blowfish 类似，Twofish 使用密钥依赖的 S-盒，且拥有相当复杂的密钥调度。共有四个 S-盒，每个为 8 位×8 位。密钥被分为两半：一半作为密钥使用，另一半用于修改密钥依赖的 S-盒。

Twofish 采用密钥漂白（key whitening），即生成一个二次密钥并将其与块进行异或。该过程可在加密前或加密后进行。在 Twofish 中，输入漂白和输出漂白均在加密前后各进行一次。输入和输出漂白均使用 128 位密钥材料。

Twofish 具备其他费istel 密码所不具备的特性，首先是“循环”概念。每两轮被视为一个循环。Twofish 的设计使得在一个完整循环（两轮）中，明文的每一位都被修改一次。

明文被分为四个 32 位单词。在输入漂白之后，进行 16 轮 Twofish。每轮中，左侧的两个 32 位单词作为圆函数的输入（所有费istel 密码均将明文分割，仅将一部分提交给圆函数）。这两个 32 位单词送入依赖于密钥的 S-盒，随后通过 MDS 矩阵混合。随后，结果通过伪哈达马德变换（pseudo‑Hadamard transform）组合。完成后，结果与右侧的两个 32 位单词（之前未参与运算的）异或，并为下一轮交换位置。

关于左右两部分异或的细节有一点需要注意：右侧的两个 32 位单词在异或前会分别进行轻微旋转。一个单词左旋 1 位，另一个右旋 1 位。

Twofish 的概览如 [Figure 6-10](#part0015.xhtml#ch06fig10) 所示。注意，该图为 Schneier 等人在其 Twofish 论文中最初发表的示意图。^([5](#part0015.xhtml#ch06note5a))

![Images](Images/image00633.jpeg)

* * *

**FIGURE 6-10    The original Twofish diagram**

如果想更深入了解 Twofish，建议阅读 Schneier 本人撰写的 Twofish 论文（见本章末尾的脚注）。也可参考书籍 `The Twofish Encryption Algorithm: A 128-Bit Block Cipher` 由 Kelsey、Whiting、Wagner、Ferguson 作者，Wiley 于 1999 年出版。

**Note**

Neils Ferguson 是一位知名的密码学家，他参与了 Twofish 的研发，同时也参与了 Helix 密码。Ferguson 与 Schneier 在 Yarrow 和 Fortuna 伪随机数生成器等多个项目上合作。我们将在 [Chapter 12](#part0023.xhtml#ch12) 中详细探讨这两者。2007 年，Ferguson 与 Dan Shumow 发表了一篇关于 Dual_EC_DRBG 伪随机数生成器潜在密码学后门的论文。随后，爱德华·斯诺登（前 CIA 承包商，泄露机密信息者）的披露证实了 Dual_EC_DRBG 确实存在后门。相关问题将在 [Chapter 18](#part0029.xhtml#ch18) 中讨论。

#### Skipjack
