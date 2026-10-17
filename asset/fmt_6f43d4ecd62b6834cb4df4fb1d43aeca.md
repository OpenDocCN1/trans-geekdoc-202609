
When the first papers on homomorphic encryption were published, it was an impractical, theoretical technology. However, in the past several years it has moved from the theoretical to the practical and applied. For example, as early as 2011, researchers at Microsoft developed a practical, applicable homomorphic approach.^(4) In 2011, Gentry and Shai Halevi published a methodology for implementing Gentry’s original homomorphic process.^(5)

## RSA

RSA in textbook format (that is, not modified) can be used homomorphically. Here’s an example. Assume that the public key is modulus `m` and exponent `e`. You encrypt any message by `x^e mod m`. You can certainly perform some mathematical operations on the encrypted data by simply encrypting that data and applying the operation to the two encrypted texts. For example, let’s use `E` to represent the encryption operation of RSA: `E(x[1]) * e(x[2]) = x[1]^e x[2]^e mod m`, which is, in turn, equal to `E(x[1] * x[2])`. Basically multiplying two cipher texts together is the same as multiplying two plain texts and then encrypting them. Not all ciphers lend themselves to this sort of operation, but RSA does. ElGamal can also be used in a homomorphic manner.

## Goldwasser–Micali

Goldwasser–Micali is an asymmetric cipher developed by Shafi Goldwasser and Silvio Micali in 1982. It was the first probabilistic public key algorithm that is provably secure. This algorithm has not gained wide use because the cipher texts are far larger than the initial plain text—as much as several hundred times larger. However, this algorithm supports homomorphic properties.

> **Note**
>
> Shafi Goldwasser 是一位出生于纽约市的以色列计算机科学家。她在麻省理工学院和以色列魏茨曼科学院担任过教授职位。Silvio Micali 是麻省理工学院计算机科学教授，并进行了大量密码学研究。

Benaloh 密码是 Goldwasser–Micali 密码的扩展，由 Josh Benaloh 在 1994 年创建。它允许一次加密更长的明文段落。由于它是 Goldwasser–Micali 的扩展，Benaloh 也具有同态性质。

> **Note**
>
> Josh Benaloh 拥有耶鲁大学计算机科学博士学位，并在 Microsoft 工作。

## Paillier

也许最广为人知的同态系统是 Paillier 系统。该概率性非对称算法由 Pascal Paillier 在 1999 年发明。其数学比我们在这本书中学习的其他算法要复杂一些。

> **Note**
>
> Pascal Paillier 是一位法国数学家，在密码学方面发表了大量论文，并且拥有若干密码学专利。

整个算法如下，但如果你不完全理解它，只要对整体概念有良好的理解即可：

1. 算法的开头类似 RSA，需要选择两个大的质数 `p` 和 `q`，且满足最大公约数 `(pq, (p–1)(q–1)) = 1`。

2. 计算 `p * q`，通常记作 `n = pq`。

3. 还需要计算 `(p–1)` 与 `(q–1)` 的最小公倍数，记作 `λ`（lambda），公式为：

   `λ = lcm(p–1, q–1)`

   > **Note**
   >
   > 这也是所谓的 Carmichael 函数（Robert Carmichael 是一位美国数学家，以研究现在称为 Carmichael 数的费马伪素数子集而闻名）。

4. 选择一个随机整数 `g`，其位置如图所示（图片未显示）。

   > **Note**
   >
   > 一个数被描述为 `n`-th 余数（`mod n²`）当存在某个 `g` 使得 `z = g^n mod n²`。

5. 确保 `n` 除以 `g` 的阶，方法是检查模逆元是否存在，公式如下：

   `μ = (L(g^λ mod n²))^(–1) mod n`

   > **Note**
   >
   > `L` 本身是一个函数，定义为：
   >
   > `L(u) = (u – 1) / n`

公钥用于加密，为 `(n, g)`；私钥用于解密，为 `(λ, μ)`。

加密步骤如下：

1. 设 `m` 为明文消息。
2. 选择随机 `r`（图片未显示）。
3. 密文 `c` 计算公式为：`c = g^m · r^n mod n²`。

解密公式为：

1. 设 `c` 为待解密的密文。
2. 计算明文 `m = L(c^λ mod n²) · μ mod n`。

Paillier 加密是可加同态的，这意味着可以在不解密的情况下直接对数据进行相加。

> **Note**
>
> 如前所述，Paillier 系统的数学比其他算法更为复杂。如果对公式感到困难，请不要过度担心，关键是掌握整体概念。

如果你有编程背景，看到下面的开源代码可能会有帮助。马里兰大学提供了以下代码（开源、免费使用）^(6)，这是一个完整的示例，可让程序员实现同态系统。

![Images](img/image00756.jpeg)
![Images](img/image00757.jpeg)
![Images](img/image00758.jpeg)
![Images](img/image00759.jpeg)
![Images](img/image00760.jpeg)
![Images](img/image00761.jpeg)
![Images](img/image00762.jpeg)

你也可以参考以下资源：

- ![image](img/image00484.jpeg) Google Homomorphic Code Project: [`code.google.com/p/thep/`](http://code.google.com/p/thep/)
- ![image](img/image00484.jpeg) IBM Homomorphic research: [`researcher.watson.ibm.com/researcher/view_group.php?id=1548`](http://researcher.watson.ibm.com/researcher/view_group.php?id=1548)

## Quantum Cryptography

*Quantum cryptography* 是加密学的下一项创新，但它具体指什么呢？在密码学中，可以用量子力学的多种方式来实现。最明显的两种是量子密钥分发和利用量子计算机攻击密码实现。在我们深入探讨这些问题之前，先简要回顾量子力学的基本概念。

### 什么是量子力学？

量子力学描述的是亚原子层面的物理现象。在这个尺度上，事物的行为与我们日常世界大相径庭。术语 *quantum* 源于亚原子层面事物是以离散量而非连续变化的。大学化学课程中常见的例子是电子围绕原子核的轨道。电子只能出现在离散的能量状态中，而不会出现在中间状态。换句话说，它们处于特定的量子态。

> **Note**
>
> 显然，一章或一节的内容无法全面覆盖如此复杂的主题。但仅仅了解量子力学的概要就足以理解量子密码学。

另一个令人惊讶、反直觉的量子力学方面是 *波粒二象性*。这也是量子力学被发现的重要因素之一。19 世纪末至 20 世纪初，物理学界曾争论光是作为粒子还是波。结果发现，光在不同情境下表现出粒子性和波动性，同样，所有粒子既是波也是粒子。

量子力学中有两个特别与量子密码学相关的方面。第一个是 *量子纠缠*，指两个粒子（或两组粒子）在生成或相互作用时变得纠缠。即使将这些粒子分离，对其中一个的任何改变都会在另一个上立即产生相关的影响。例如，

The most practical use of quantum cryptography, and the one most likely to be implemented in the foreseeable future, is `quantum key distribution`. The issue of key distribution is at the heart of many algorithms such as Diffie-Hellman and Menezes–Qu–Vanstone, or MQV (recall both algorithms were discussed in Chapter 10). How do two parties exchange a key in such a way that a third party cannot intercept it? If the key is encoded as quantum bits, then the Heisenberg uncertainty principle provides security for key transmission. Any attempt to read the key will in fact alter the key.^(7)

It is also possible to use quantum entanglement for key exchange. If a set of particles is entangled and then separated, the party on one end can encode bits as properties (such as spin) on the particles. By changing the property on the sender’s side, the bits of the key are instantly transmitted to the receiving side. Because there is no known communication medium, it is impossible for someone to intercept the key transmission.

### Breaking Quantum Code

Quantum computing is still in a nascent stage, a very long way from practical implementation. But the possibilities could radically change cryptography. Current digital computers maintain data in states of bits, a 1 or 0. A quantum computer maintains data in qubits. These qubits can use a 1, a 0, or a superposition of these states. This allows quantum computers to store much more data and to process data much faster.

What this means in practical terms is that a quantum computer would have immensely more computational power than any digital computer. Consider the asymmetric algorithms you’ve studied in this book. They were all based on some problem being infeasible to solve, such as factoring a composite number into its prime factors (as seen in RSA), or solving a discrete logarithm problem (as in elliptic curve cryptography). If quantum computers become a practical reality, these problems will no longer be impractical to solve. In fact, they will be solvable in a reasonably short period of time, thus undermining the basis for all asymmetric algorithms.

Symmetric cryptography will not be safe from the onslaught of quantum computing either. Consider that keys such as the AES 256-bit key are essentially immune from brute-force attacks using current methods; a quantum computer could try far more keys in a shorter period of time, making brute-force attacks far more practical.

Currently there are no working quantum computers, so these issues are only hypothetical at this point. But given the attention and resources committed to quantum computing, it seems likely that we will eventually face these problems. Right now, the only solution is to use much larger keys, but this is only a stopgap solution, not a permanent one. Quantum computing will require an entirely new approach to cryptography—one that has not yet been developed.

## Conclusions

Cryptography is evolving, and new issues are on the horizon. Currently one of the more immediate issues in cryptography is that of homomorphic encryption, which allows an entity to perform operations on encrypted data without first decrypting the data, and indeed without even having the capability to decrypt the data. Homomorphic encryption has applications in electronic voting, e-commerce, and cloud computing. Cloud computing itself poses cryptographic challenges, and homomorphic cryptography is one of the primary solutions to those challenges.

Quantum mechanics has not only revolutionized physics, but it could revolutionize computing and cryptography as well. Quantum key exchanges is perhaps the most immediate issue in cryptography and could solve secure key exchange issues. Code-breaking could also be enhanced dramatically by quantum computing.
