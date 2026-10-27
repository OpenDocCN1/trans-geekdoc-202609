

选择另一个底数 $a$ 再试一次。一旦 $n$ 被分解，Mallet 就可以轻松生成所有私钥。

与 Miller–Rabin 素性检验类似，这是一种概率性攻击，但 DeLaurentis 进一步证明了若假定黎曼猜想成立，则他的攻击是确定性的。他还提出了第二种攻击，使 Mallet 无需分解 $n$ 就能读取和签署消息。

## 17.2.3 攻击15：内部人员的非分解攻击

Mallet 知道他的公钥 $e_M$ 必须与 $\varphi(n)$ 互素，这样才能找到满足 $e_M d_M = 1 \pmod{\varphi(n)}$ 的私钥。后一个等式等价于

$e_M d_M - 1 = k\varphi(n)$，其中 $k$ 是某个正整数

现在，$e_M d_M - 1$ 不必与 Alice 的公钥 $e_A$ 互素。

设 $f$ 是 $e_M d_M - 1$ 与 $e_A$ 的最大公约数。使用欧几里得算法可以快速求出 $f$ 的值。我们定义 $r = (e_M d_M - 1)/f = (k\varphi(n))/f$，并注意到 $r$ 与 $e_A$ 互素。因为 $f$ 是 $e_A$ 的因子，而 $e_A$ 与 $\varphi(n)$ 互素，所以 $f$ 也必定与 $\varphi(n)$ 互素。现在我们有两个非常有用的结论：

- 1. $f$ 是 $k\varphi(n)$ 的一个因子。
- 2. $f$ 与 $\varphi(n)$ 互素。

由此我们可以得出结论：$f$ 是 $k$ 的一个因子。换句话说，$r$ 是 $\varphi(n)$ 的倍数。即 $r = (k/f)(\varphi(n))$。

因为 $r$ 与 $\varphi(n)$ 互素，我们可以使用扩展欧几里得算法找到整数 $x$ 和 $y$，使得 $xr + ye_A = 1$。特别地，我们能够找到一对 $x$ 和 $y$，其中 $y$ 为正。由于 $r$ 是 $\varphi(n)$ 的倍数，当我们将最后一个等式模 $\varphi(n)$ 化简时，$xr$ 项消失，剩下 $ye_A = 1 \pmod{\varphi(n)}$。

因此，$y$ 符合 $e_A \pmod{\varphi(n)}$ 的乘法逆元的定义。它可能不是 Alice 实际使用的逆元，但效果同样良好。Mallet 使用这个值所产生的加密结果和签名将与 Alice 产生的完全相同。

## 17.2.4 Elgamal 签名

与 RSA 类似，Elgamal 也可用于对消息进行签名。与 RSA 不同，用户需要额外的密钥组件来实现签名。回顾常规 Elgamal 加密，Alice 只需要一个大素数 $p$、模 $p$ 整数乘法群中的一个最大阶元素 $g$，以及一个私钥 $a$。她计算 $A = g^a \pmod p$，然后公开 $g$、$p$ 和 $A$。只有 $a$ 是保密的。

设 $s$ 表示 Alice 的第二个私钥。她必须计算 $v = g^s \pmod p$。然后为了对消息 $M$ 签名，她选择一个随机的加密密钥 $e$ 并计算

$S_1 = g^e \pmod p$ 以及 $S_2 = (M - s S_1) e^{-1} \pmod {p - 1}$。

因此，与 Bob 发给 Alice 的 Elgamal 加密消息（第16.8节）类似，Alice 的签名消息由两个值 $S_1$ 和 $S_2$ 组成。它们会随消息一起发送。

Alice 公开 v、g 和 p。通过这些，可以计算 v^{S1} S1^{S2} (mod p) 和 g^{M} (mod p) 来验证她的签名。如果签名有效，这两个值将相同。几个简单的步骤可以说明为什么这两个值必须匹配：

v^{S1} S1^{S2} = g^{S1} g^{e S2} = g^{S1 + e S2} = g^{S1 + e(M - S1) e^{-1}} = g^{S1 + (M - S1)} = g^{M}

## 17.3 哈希函数：加快速度

正如 RSA 加密整条消息很慢，因此通常只用于加密密钥，我们也不希望为了签名而对整条消息应用 RSA。解决这个问题的一种方法是设法将消息压缩成更小的内容，然后对这个原始消息的表示进行签名。压缩后的消息，即*消息摘要*，通常被称为消息的*哈希*。生成这一摘要的过程称为*哈希运算*，它应具有以下特性：

- 1. 相同的消息必须始终产生相同的哈希。也就是说，我们有一个哈希*函数*。这在基于哈希验证签名时非常重要。我们用 h(x) 表示哈希函数。
- 2. 哈希运算应该很快。毕竟，速度是使用前面所述方法的缺点。
- 3. 找到哈希到相同值的两个消息应该是困难的（计算上不可行）。也就是说，我们不应能够找到不同的 x 和 x′，使得 h(x) = h(x′)。如果发生这种情况，我们就说发现了一个*碰撞*。如果一份合法签名的文档有一部分被替换（新文本具有其他含义）并且哈希值与原始值相同，那将非常糟糕。这会使被篡改的文档看起来也像是被签名的。然而，任何碰撞都被视为严重威胁，即使它是通过两个看起来更像随机文本而非有意义消息的消息发现的。这是一个非常有趣的条件，因为没有哈希函数可以是一对一的——其全部思想就是创建更短的消息！因此，即使是最好的哈希函数，碰撞也必然存在。但找到它们应该非常困难！
- 4. 计算任何原像应该是困难的。也就是说，给定消息的哈希 h(x)，我们不应能够恢复出该消息或任何其他文本 y，使得 h(y) = h(x)。

哈希函数出现在20世纪50年代，但当时并未打算用于密码学目的。⁴ 这些函数的思想只是将数据集中的值映射为更小的值。这样，可以更容易地进行比较，并加速搜索。1974年，一些可能并不了解哈希函数的研究人员认识到，“难以求逆”的函数提供了一种检查消息是否被更改的方法。⁵ 他们将这一思想归功于 Gus Simmons，他向他们提出该思想是“出于军备限制的目的，与监测某些材料的生产有关”。⁶ 1981年，Mark N. Wegman 和 Larry Carter 正式描述了这种密码学关联，这两位研究人员在20世纪70年代末从事过哈希函数的非密码学工作。⁷

⁴ Knuth, Donald，《计算机程序设计艺术——排序与查找》，第3卷，Addison-Wesley，马萨诸塞州雷丁，1973年。参见第506-549页。

⁵ Gilbert, Edgar N., Florence J. MacWilliams 和 Neil J. A. Sloane，“Codes Which Detect Deception”，*The Bell System Technical Journal*，第53卷，第3期，1974年3月，第405-424页。

### 17.3.1 Rivest 的 MD5 与 NIST 的 SHA-1、SHA-2 和 SHA-3

消息摘要算法5（MD5）将任意长度的消息压缩为128位。⁸ 我们已经用到第5版，这并不特别令人鼓舞。⁹ 经历过多个不安全版本的密码系统，如矩阵加密和背包加密，在新版本出现时并不被看好，但 MD5 却很流行。所有 MD 哈希函数都由 Ron Rivest（RSA 中的 R）设计。第5版于1991年问世。此后，研究人员发现了越来越快的碰撞查找方法。2009年，Tao Xie 和 Dengguo Feng 将所需时间缩短至数秒，因此进一步缩短已无多大意义。¹⁰ 我们现在来看一种替代方案。

> MD5 显然被用作 SHA-1 的模型，因为两者有许多共同特征。
> 
> —Mark Stamp 和 Richard M. Low¹¹

安全哈希算法（SHA）提供了另一系列哈希函数。第一个，现在称为 SHA-0，由美国国家安全局（NSA）于1993年设计。随后是 NSA 在1995年推出的 SHA-1。两者都产生160位哈希。事实上，两者之间只有很小的差异，NSA 声称这一修改提高了安全性，但没有解释具体如何提高。

尽管此前已有大量密码分析，但直到2004年，SHA-0 才真正发现了碰撞。这相当于在超级计算机上工作13天。¹² 第二年，SHA-1 被发现存在缺陷。当美国国家安全局在2005年宣布其“NSA Suite B 密码套件”时，推荐的哈希算法是 SHA-256 和 SHA-384，这两个算法取自一个总称为 SHA-2 的六算法集合。¹³ 与其前身一样，SHA-2 算法由 NSA 设计。尽管 SHA-1 存在弱点且 NSA 也给出了建议，但本书第一版（2013年出版）仍包含以下内容：

> SHA-1 是多个广泛使用的安全应用和协议的一部分，包括 TLS 和 SSL、PGP、SSH、S/MIME 和 IPsec。这些应用也可以使用

⁶ Gilbert, Edgar N., Florence J. MacWilliams 和 Neil J. A. Sloane，“Codes Which Detect Deception”，*The Bell System Technical Journal*，第53卷，第3期，1974年3月，第405-424页，引文出自第406页。
⁷ Wegman, Mark N. 和 J. Lawrence Carter，“New Hash Functions and Their Use in Authentication and Set Equality”，*Journal of Computer and System Sciences*，第22卷，第3期，1981年6月，第265-279页。
⁸ http://en.wikipedia.org/wiki/MD5 上有对该算法的清晰（但简短）解释。更详细的解释可见 http://www.freesoft.org/CIE/RFC/1321/3.htm。
⁹ MD4 的一个有意义的碰撞见于 Dobbertin, Hans，“Cryptanalysis of MD4”，*Journal of Cryptology*，第11卷，第4期，1998年秋季，第253-271页。
¹⁰ Xie, Tao 和 Dengguo Feng, *How To Find Weak Input Differences For MD5 Collision Attacks*, 2009年5月30日。http://eprint.iacr.org/2009/223.pdf。
¹¹ Stamp, Mark 和 Richard M. Low, *Applied Cryptanalysis: Breaking Ciphers in the Real World*, Wiley-Interscience, Hoboken, New Jersey, 2007, p. 225.
¹² Biham, Eli, Rafi Chen, Antoine Joux, Patrick Carribault, William Jalby 和 Christophe Lemuet，“Collisions of SHA-0 and Reduced SHA-1”，载于 Cramer, Ronald 编辑，*Advances in Cryptology – EUROCRYPT 2005 Proceedings*, Lecture Notes in Computer Science, 第3494卷, Springer, Berlin, Germany, 2005, 第36-57页。
¹³ https://web.archive.org/web/20090117004931/http://www.nsa.gov/ia/programs/suiteb_cryptography/index.shtml.

