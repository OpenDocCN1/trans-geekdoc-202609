
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

# Each call to compare_mac() will look at all 16 characters.
start = time()
for i in range(TRIALS):
    compare_mac(MAC1, MAC1, len(MAC1))
end = time()
print("%.5f" % (end-start))

# Each call to compare_mac() will look at three characters.
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
