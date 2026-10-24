
Dan Boneh 的《Twenty Years of Attacks on the RSA Cryptosystem》，是一篇综述，回顾并解释了对 RSA 最重要的攻击。关于定时攻击的参考，Billy Bob Brumley 和 Dan Boneh 所著论文《Remote Timing Attacks Are Practical》是必读之作，既因其分析性贡献，也因其实验性贡献。要了解更多关于故障攻击的内容，请阅读 Dan Boneh、Richard DeMillo 和 Richard Lipton 所著 Bellcore 攻击论文《On the Importance of Eliminating Errors in Cryptographic Computations》的完整版本。

尽管有时痛苦且令人沮丧，但学习 RSA 实现工作原理的最佳方式是查阅广泛使用的实现的源代码。例如，查看 OpenSSL、NSS（Mozilla Firefox 浏览器使用的库）、Crypto++ 或其他流行软件中的 RSA 及其底层大数算术实现，并检查其算术操作的实现以及对其定时攻击和故障攻击的防御措施。

## 11

## 迪菲-赫尔曼

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
