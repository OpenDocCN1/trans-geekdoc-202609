
*Hash-based cryptography* 基于密码学哈希，正如其名称所暗示的那样，通常应用于数字签名方案（而非加密）。如前几章所述，哈希是一种单向函数，它将哈希内容转换为代表性的一组位（称为哈希、哈希结果、签名或消息摘要），该位对于唯一内容是唯一的。XMSS（eXtended Merkle Signature Scheme）、Leighton-Micali Signatures（LMS）、Blockchained Post-Quantum Signatures（BPQS）、SPHINCS 和 SPHINCS+ 数字签名方案都基于哈希密码学。SPHINCS+ 是 NIST 竞赛第二轮中唯一提交并被接受的基于哈希的数字签名。

Ralph Merkle 基本上发明了密码学哈希领域，他还参与了 20 世纪 70 年代末与 Whitfield Diffie 和 Martin Hellman 一起首次公开已知的公钥加密实现。因此，在讨论基于哈希的密码学时，你经常会听到关于 Merkle 树（即哈希树）和 Merkle 盒以及谜题的讨论。Merkle 树是一系列分层哈希，它们哈希其它哈希，进而哈希原始内容。如有兴趣，可参阅 `https://en.wikipedia.org/wiki/Merkle_tree` 了解有关 Merkle 树的更多细节。

基于哈希的密码学被认为具有抗量子性，因为哈希不受 Shor 算法的影响，尽管它们受 Grover 算法的影响。量子计算机上的 Grover 算法在执行特定类型问题（如破解哈希）时，相对于二进制计算机具有平方根级别的改进。这有效地使任何基于哈希的密码学的强度减半。这也意味着将哈希的密钥大小加倍可以抵消 Grover 算法和量子计算带来的攻击收益。

> **NOTE**  至关重要的是，底层哈希必须符合（之前讨论过的）良好、安全哈希的所有属性。如果哈希随着时间的推移不再是“好的哈希”，那么基于该哈希的任何密码学不仅会变得易受量子计算攻击，也会易受二进制计算攻击，其水平远低于其声明的密钥强度。

所有哈希都受限于它们在哈希结果变得（过早地）对所有可能的唯一输入重复之前能够保护的消息数量。例如，截至本文撰写时，所有 Microsoft Windows 登录密码都会被转换为 NT 哈希。你可以在 Windows 中创建数千亿亿个唯一的可能密码（近 2⁶⁵⁵³⁵ 种不同组合），但相同的 NT 哈希最终会对许多不同的密码产生相同的哈希值（在哈希攻击理论中，这被称为 *second preimage collision* 的一个例子），这是由于哈希及其密钥空间（即所有可能的选择）的固有限制所致。

如果基于哈希的密码学“意外地”对两个不同的输入重复使用相同的单次密钥，它将为攻击者提供对私钥的强有力洞察。因此，哈希和基于哈希的密码学开发者会竭尽全力防止单次密钥重复。有几种不同的方法可以减轻这种风险。

解决这种风险的一种方法是提高哈希算法区分唯一内容的准确性。如果哈希始终产生唯一的哈希输出，那么重复问题就消失了。由于哈希的密钥空间总是比它试图哈希的潜在事物更有限，因此这很难做到。为了抵消这种风险，哈希开发者还可以增加 resulting 数字签名的大小（即提供更多密钥空间）。数字签名越长，可能的哈希结果就越多。因此，具有 128 位哈希结果的哈希可能比限制为 64 位结果的哈希更准确。非常大的数字签名可能会变得过大且难以处理，导致性能和存储问题。大多数密码学专家认为，一个好的哈希，利用其固有的算法准确性，不应导致非常大的数字签名。另一些人则认为，大的数字签名是确保哈希准确且没有内置哈希结果冗余的唯一方法。无论如何，请对非常小和非常大的数字签名给予额外考虑。

防止密钥重复的另一种常见方法是使哈希 *stateful*（相对于 *stateless*）。有状态哈希会跟踪它使用过的所有一次性秘密密钥，并确保不再重复使用。大多数传统基于签名的哈希都是 *stateful*。如果检测到重复密钥，则算法会再次运行或选择较长密钥流的另一部分来生成另一个唯一的单次密钥。

有状态和无状态哈希各有优缺点。无状态哈希无法保证唯一密钥，但通常具有更大的密钥大小。有状态哈希通常密钥大小较小，但由于它们必须存储“状态表”，因此从资源、存储和安全角度来看，它们很笨重。有状态哈希在数据恢复事件期间也可能产生关键问题。如果处理不当，恢复的有状态哈希实现可能会覆盖其先前的状态表，抹去先前使用过的密钥的证据，然后哈希可能会再次意外地在未来的密码学操作中使用相同的密钥。攻击者如果知道状态表已被覆盖，可能会寻找重复密钥的迹象，并在密码攻击中获得优势。这是一个相当不可能且风险很低的事件，但如果密码学家看到任何理论上的弱点，这就被认为是一个很大的弱点。因此，NIST 不允许有状态的基于哈希的密码学算法被提交供考虑，从而淘汰了几个原本强大的竞争者。

### Lattice-Based Cryptography

一个 *lattice* 是一种在空间中对某物——例如物体或点——进行有维度、分布式、重复的几何排列/模式。晶格在自然界中无处不在，例如在分子或晶体中，并且人们经常使用它们来创建其他更大的物体，包括网、围栏或编织图案。许多数学公式和算法都会创建晶格。基于晶格的公式和结果被创建出来，其因子分解在根本上是困难的（称为 *computational lattice problems*）。在密码学中最常用的晶格问题被称为学习与误差（LWE）、环学习与误差（RLWE）、模学习与误差（MLWE）、学习与舍入（LWR），以及数十种变体。每种类型的问题都有其自身的优点和缺点。一般来说，涉及环的 LWE 通常比经典 LWE 更快并且密钥大小更小，但也包含一些尚未经过时间充分检验的新数学构造。

> **NOTE**  在学习密码学，尤其是后量子密码学时，你会读到很多关于“环”的内容。环指的是抽象代数中使用的一个基本且复杂的数学结构。有关更多详细信息，请参阅 `https://en.wikipedia.org/wiki/Ring_(mathematics)`。

这些非常难以求解的晶格问题已被用于创建公钥加密和数字签名方案，这些方案对二进制计算机和量子计算机都具有抵抗力。通过基于晶格的密码学，会创建复杂的晶格函数作为私钥。公钥是作为原始晶格的修改版本生成的。内容使用修改后的版本（公钥）进行加密，只有原始晶格版本（私钥）的持有者才能轻松地将加密消息恢复到其原始明文状态。

从根本上说，基于晶格的密码学创造了一个数学工作量问题，其工作量大致相当于或大于分解大素数所需的工作量，但其保护并不依赖于大素数。因此，基于晶格的密码学不被认为易受 Shor 算法或任何分解素数的量子算法的影响。

从负面理论角度来看，基于晶格的密码学可能需要相对较大的密钥大小，与其他密码类型相比，尽管非常重要的是，这对于大多数提交给 NIST 的基于晶格的候选方案来说并不成立，包括 CRYSTAL-Kyber、LAC、NewHope、NTRU、NTRUPrime、Round5、SABER 和 ThreeBears。只有 FRODO-KEM 具有相对较大的密钥大小，尽管几种基于代码的算法要大得多。

第一个基于晶格的密码是 NTRU，于 1998 年引入，随后是基于 LWE 和 RLWE 数学问题的多个密码。今天，基于晶格的密码是提交给 NIST 的最受欢迎的后量子密码类型。此外，在 2009 年，Craig Gentry 在他的论文（`https://dl.acm.org/citation.cfm?id=1834954`）中使用基于晶格的密码学创建了第一个真实世界的全同态加密系统，正如前一章所讨论的那样，它允许第三方在不先解密的情况下正确操作加密数据。

> **NOTE**  大多数基于晶格的密码及其相关问题都基于 *shortest vector problems*（SVPs），这些问题需要至少超指数时间来求解。不幸的是，SVP 提供的整体安全性尚未完全理解，并且一些理论攻击已显著削弱了其保护。因此，所有基于晶格的密码学（尤其是基于 SVP 且没有抵消缓解措施的密码学）都不能完全被信任，并且未来可能会被发现比之前理解的更弱。这在与大多数提交给 NIST 的后量子密码（为基于晶格的密码）相结合时可能会有问题。

#### Multivariate Cryptography

多元简单意味着“多个变量”。*Multivariate cryptography* 指的是依赖于多元多项式数学方程（如 *x* + *y* + *z* = *n*）来形成密码学原语的非对称加密和签名方案。你也会听到基于多元多项式数学的密码学被称为 *multivariate quadratic (MQ) polynomial equation cryptography*。这是指至少有一个变量被提高到第二幂（例如 *x*² + *y* + *z* = *n*）。正确创建的多元密码学无法在多项式时间内求解，并且不依赖于大素数进行保护。因此，它们被认为具有量子抗性。它们固有的特性也使它们成为硬件实现的良好性能候选，例如专用集成电路（ASIC）和现场可编程门阵列（FPGA）。

多元密码学包括 HFE、Gui、Balanced Oil & Vinegar、Unbalanced Oil & Vinegar（一些算法名称是有意幽默的），以及 Tame Transformation Signature。提交的多元数字签名方案包括 GeMSS、LUOV、MQDSS 和 Rainbow。Rainbow 是 Unbalanced Oil & Vinegar 的多层实现。

#### Supersingular Elliptic Curve Isogeny Cryptography

*Supersingular elliptic curve isogeny cryptography*（或简称为同源密码学）依赖于创建超奇异椭圆曲线和同源图以用于其加密保护的数学方程和算法。椭圆曲线是由数学公式创建的，表示代数曲线，这些曲线不自相交（也称为 *nonsingular*）。所有超奇异曲线都是非奇异的，而“超”部分指的是异常大的环。*Isogeny* 指的是彼此之间共享相关值交集的独立代数群。作为一个简单的例子，想象你有一个组中的数字 1、2、3 和 4，另一个组中的字母 A、B、C 和 D，并且每个数字都与一个对应的字母相关。它们彼此同源。同源曲线将是两条曲线（当然由数学表示），它们可以相互映射。

在同源密码学世界中，两个不同的算法方程创建了一个同源链接，可用于加密和解密。公钥是一对椭圆曲线，私钥是它们之间的同源。仅给定一对超奇异椭圆曲线就找到这种同源被认为是一个非常难以解决的问题。如果这听起来很复杂，请知道超奇异椭圆曲线同源方程是有史以来创造的最困难的数学问题之一，但已被研究得足够充分以了解其优缺点。

在 2012 年，中国研究人员创建了基于超奇异椭圆曲线同源和多元密码学的第一个量子安全数字签名（`https://pdfs.semanticscholar.org/527a/4abe13ee6ce7858e040ceaa7cd0b983969d8.pdf`）。同源密码学往往具有非常小的密钥大小，并且还允许轻松实现 *perfect forward secrecy*。完美前向保密是一种密码保护，涉及频繁更改会话密钥，以便未来的密钥泄露无法更轻松地破解之前的会话，因为它们使用的是不同的密钥。完美前向保密通常是期望的密码学特性，尽管它通常无法实现。同源密码学与完美前向保密相容。缺点是，同源密码学相对较新，因此尚未像其他后量子密码学类型那样经过大量测试和攻击。虽然早期的同源实现已被攻破，但使用超奇异同源而不是仅仅非奇异曲线等更改阻止了已知的攻击。唯一被 NIST 提交并接受进行第二轮评估的同源密码是 SIKE。

#### Zero-Knowledge Proof

A `zero-knowledge proof` (ZKP; also known as a `zero-knowledge protocol`) is a method by which one party (called the `prover`) can prove to another party (called the `verifier`) that they know value `x`, without having to convey or prove any information except for the fact that they really know the value `x`, without actually providing value `x` or leaking any extra, nonessential information.

An example of a common ZKP system is a logon password used in a modern-day “challenge-response” authentication system. Let's suppose a user wants to log on to a server using a valid password but at the same time not allow the server to know or store the plaintext password (so it can't be stolen or compromised). How can the user prove to the server that they have (and can use) the correct password without providing the correct password itself?

One ZKP answer is to use cryptographic challenge-response hashes based on the password but without using the actual password. For example, suppose the user's plaintext password is `frog`. When the user creates it for the first time, let's imagine that the plaintext password of `frog` is immediately hashed and the hashed result is `1234`. The hashed result is the only version of the password sent to and stored on the server. The server has no way of knowing the original plaintext password.

When the user wants to log on to the server, they initiate a connection to the server. The server creates a random value, say `9876`, and sends it to the user (called the `challenge`). The user subtracts the password hash of `1234` from `9876` to get a result `8642` and sends it back to the server (called the `response`). The server uses the user's stored password hash of `1234` to perform the same subtraction on the randomly generated number and, in doing so, will get the same result (8642) and compare it to the result the user sent back. Only a user with the correct original password of `frog` would have the correct hash of `1234` and be able to get the correct result when subtracting it from the randomly generated value of `9876`. So, the user can successfully prove they had the correct original password to the verifying server without revealing what the plaintext password is. Most modern-day authentication systems, including Microsoft Windows passwords, use a similar (although more complex) scheme.
