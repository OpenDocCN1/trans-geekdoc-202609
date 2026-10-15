
要在不安全的通信通道上生成共享密钥，让我们假设两个人，爱丽丝和鲍勃，会选择一个质数 p，以及一个原始根 r。爱丽丝和鲍勃可以通过不安全的通道共享这些值。然后，他们各自会选择一个秘密值，用它对 r 进行模 p 运算。因此，如果爱丽丝选择 a，鲍勃选择 b，爱丽丝会计算 r^a mod p，鲍勃会计算 r^b mod p。以我们选取 5 作为质数的例子，爱丽丝和鲍勃可以约定使用 2 作为原始根，从而得到 p = 5 且 r = 2。爱丽丝选择 a = 7，鲍勃选择 b = 9。爱丽丝计算 2⁷ mod 5 = 3，鲍勃计算 2⁹ mod 5 = 2。爱丽丝和鲍勃共享计算结果 3 和 2，但保持指数 7 和 9 的秘密。爱丽丝然后取鲍勃的数字 2，将其提升到她的秘密数字 7 次方，再对共享的质数 5 取模。鲍勃则对爱丽丝的 3 进行同样的操作，提升到他秘密的 9 次方，再对共享的质数 5 取模。结果是相同的值，他们现在共享这个值作为共享密钥：

1.  2⁷ mod 5 = 3

2.  3⁹ mod 5 = 3

拦截者可能能够截获质数、原始根以及原始根被提升到某些指数的结果，但要在爱丽丝和鲍勃之间生成共享密钥，拦截者必须计算 2^x mod 5 = 3 或 2^y mod 5 = 2 的离散对数。虽然使用这种小数字的例子很 trivial，但在实际世界中使用的更大的数字时，计算质数以尝试破解密钥是计算上不可行的。[^(18)](#9781284211658_CH10_08.xhtml#c10-bib0018)

## 10.3 Asymmetric Cryptography

公钥加密，也称为非对称加密，对于广泛分发的安全交易至关重要。它使企业能够使用受信任的消息进行电子商务。支持非对称密钥加密的基础设施称为公钥基础设施（PKI）并包括以下组件：(1) 证书颁发机构（CA），它们颁发受信任的验证，如 X.509 证书；(2) 注册机构（RA），它们将证书“记录”或向证书颁发机构注册；(3) 证书服务器，用于发布数字证书；(4) 证书撤销，用于分发被撤销、过期或伪造证书的通知；以及 (5) 密钥恢复服务，允许管理员恢复丢失的密钥。

在公钥加密中，我们将公钥分发给想要创建和发送加密消息的人。我们使用私钥对其进行解密。我们需要在一个称为密钥生成的过程中创建这些密钥。一旦完成，我们可以交换公钥并进行安全的对话。注意，公钥加密还用于许多其他功能，如身份验证（[Figure 10.5](#9781284211658_CH10_03.xhtml#c10-fig0005)）。

![FIGURE 10.5 PKI Illustration](images/9781284236378_CH10_FIGF05.jpg)

FIGURE 10.5 PKI Illustration

公钥加密依赖于特殊的数学函数，这些函数在没有特殊的“后门”知识的情况下极难逆转。这种加密算法依赖于对大质数整数进行因式分解、组合优化（也称为背包问题）、代数编码理论或有限域的离散对数，或椭圆曲线的微积分。[^(19)](#9781284211658_CH10_08.xhtml#c10-bib0019)

| Salt || Salts use randomly generated characters (seeds) inserted into a string of characters, such as a password. The salt and the password are combined and processed using a hashing function that obfuscates the password. This technique is very useful for authentication or password storage. It’s also helpful in preventing a rainbow table attack, which is a type of attack that uses precomputed hashes. |

| --- | --- |

| Hash || Hashing converts one set of values of variable length into another value of fixed length, often using a compression technique. These hashed values are used to produce codes that serve as message digests, password obfuscation, and in some ciphers. Well-known hash functions include MD5 and SHA1/2. In cryptography, a one-way hash is easy to compute in one direction, but difficult to revert back or decode/break. |

| Trap Door || In cryptography, a trap door is a common secret that is computed using different inputs. For example, during key generation, a matrix of prime numbers is reproduced, then two prime values, p and q, are chosen to compute key halves d and e. The key half, d, is computed such that e \* d = 1 mod (p – 1) \* (q – 1). Note that, e \* d – 1 is evenly divisible by \[(p – 1)\*(q – 1)\]. Key half, e, is such that it is relatively prime to (p – 1)\*(q – 1). The public key is the combination of (e, n); the private key is the combination of (d, n). The value, n, is called relatively prime to (p – 1)\*(q – 1), thus n is the trap door. Section 10.3.1 explains this concept further. |

### 10.3.1 Private Keys and Asymmetric Cryptography

非对称加密的独特之处在于，它会生成一种特殊的代码，如果该代码与密码的解密公式所期望的结果匹配，它就“穿过后门”，即后门是解密函数，这与初始加密过程所使用的技术和信息不同。这意味着不需要共享秘密；公钥用于加密，可以自由分发，这样任何人都可以向拥有私钥的持有者发送加密消息。只有拥有私钥的持有者才能解密消息，这之所以可能是因为原始发送者使用某种技术或方法生成密钥对和一个公共质数。公钥的一半和公共质数被分发为公钥，而私钥的一半和公共质数则保留为私钥。[^(10)](#9781284211658_CH10_08.xhtml#c10-bib0010)

公钥加密对许多新手来说是一个令人困惑的部分：两个人如何能够共享一个加密消息，而只有部分解是已知的？这通常涉及密钥生成的问题。答案是，创建密钥的人（可以是门卫之类的角色）使用某种技术生成密钥，然后将密钥分成两半，称为密钥对，并只发送其中一半以及一个种子值，即一个公共质数，给另一个人（可以是俱乐部的顾客），该人只能加密但不能解密消息；只有原始创建者才能解密，因为生成程序在私钥部分中创建了一个逆机制，使得消息可以被解码。考虑到消息创建者拥有部分密钥并使用 RSA 等众所周知的加密算法，如果公共质数和部分代码已经公开，那么公钥加密如何安全工作？为了让公钥加密（如 RSA 或 PGP）工作，需要将大数分解为其质因数。记住，质数是只能被 1 和自身整除的数。首先，必须生成一个大的随机密钥。

生成密钥的工具和方法很多。一个例子是 Java 编程语言的扩展库 javax.crypto，可以用于创建密钥。例如，导入 javax.crypto.KeyGenerator、javax.crypto.SecretKey 和 java.security.Key 库，可以使用 generateKey() 方法为 DES 生成密钥。另一种技术是 Windows 系统上的 PuTTY，或者更具体地说 PuTTYgen，可以用于生成 RSA、SSH 和其他公钥加密的非对称密钥。下面的场景将说明如何使用 PuTTYgen 和 PuTTY 以安全方式登录到服务器。