
-   [Taher ElGamal 于 1984 年由埃及密码学家首次描述，ElGamal 基于 Diffie-Hellman 密钥交换算法，并在某些版本的 Pretty Good Privacy (PGP) 中使用。ElGamal 算法包含三个组成部分：密钥生成器、加密算法和解密算法。]

1. [Alice 生成一个乘法循环组 G，阶为 q，生成元为 g 的高效描述。]

Note
[你需要记住来自 [第 5 章](#part0013.xhtml#ch05) 的群。循环组由单个元素生成——在这里，就是生成元 g。对于乘法循环组，每个元素可以表示为 g 的某些幂。]

2. [Alice 从集合 {0, …, q – 1} 中选择一个随机数 *x*。]

3. [随后，Alice 计算 h = g*^x*。请记住，g 是组的生成元，而 x 是组内的随机数。]

4. [h、G、q 和 g 是公钥，而 *x* 是私钥。]

5. [如果 Bob 想用 Alice 生成的公钥加密消息 m，则以下过程发生：]

A. [Bob 生成一个从 {0, …, q – 1} 中选择的随机数 *y*，Y 常被称为 *临时键*。]

B. [接下来，Bob 计算 c1：c1 = g*^y*。]

C. [然后，计算共享密钥，s = h*^y*，s 是公钥的一部分。]

D. [消息 m 转换为 G 中的 m′。]

E. [Bob 必须计算 c2：c2 = m′ \* s。]

F. [Bob 现在可以发送 c1 和 c2 作为加密文本。]

6. [要使用 Alice 首次生成的公钥解密消息 m，则以下过程发生：]

A. [接收方计算 s = c1*^x*。]

B. [接收方计算 m′ = c2 \* s^(–1)。]

C. [最后，m′ 转换回明文 m。]

Note
[此结构应与 Diffie-Hellman 相似。]

#### MQV

[与 ElGamal 类似，MQV (Menezes–Qu–Vanstone) 是一个基于 Diffie-Hellman 的密钥协商协议。它于 1995 年由 Alfred Menezes、Minghua Qu 和 Scott Vanstone 首次提出，并于 1998 年进行了修改。MQV 已被纳入公钥标准 IEEE P1363。HQMV 是其改进版本。具体算法与椭圆曲线相关，我们将在 [第 11 章](#part0021.xhtml#ch11) 中详细讨论。]

Note
[Alfred Menezes 是加拿大滑铁卢大学数学系的教授，并著有多本密码学著作。]

#### 最佳非对称加密填充

OAEP (Optimal Asymmetric Encryption Padding) 于 1994 年由 M. Bellare 和 P. Rogaway 引入，并在 RFC 2437 中标准化。OAEP 在对称加密前对明文进行处理。当与 RSA 等算法一起使用时，它提供了一个能抵御 chosen plaintext 攻击的安全方案。

OAEP 达到了以下两个目标：

![image](Images/image00484.jpeg)    [为确定性加密方案（如 RSA）添加随机性，使其转变为概率性方案。]

![image](Images/image00484.jpeg)    [防止部分解密或其他信息泄漏，确保攻击者在未能逆转陷阱门单向置换 *f* 前无法恢复明文的任何部分。]

#### Cramer-Shoup

[Cramer-Shoup 系统是由 Ronald Cramer 和 Victor Shoup 于 1998 年开发的非对称加密算法，它是 ElGamal 加密系统的扩展，并且是第一个被证明能抵御自适应密文攻击的高效算法。]

#### 应用

[到此为止，你应该对几种非对称算法有了基本了解，并且对 RSA 和 Diffie-Hellman 有非常深入的理解。现在我们将深入探讨非对称算法的常见应用。]

##### 密钥交换

[对称算法比非对称算法快得多，且使用更小的密钥即可达到相同安全级别。然而，非对称算法解决了密钥交换的问题。因此，非对称算法常用于密钥交换目的。例如，在 Secure Sockets Layer (SSL) 和 Transport Layer Security (TLS) 中，非对称算法（如 RSA）用于交换对称密钥（如 AES，高级加密标准）。这是使用非对称算法的常见方式。]

##### 数字签名

[你肯定 familiar with the term “digital signatures”，但你是否知道它们是什么以及它们是如何工作的？请记住，加密算法主要用于保护机密性，确保只有 intended recipient 才能阅读消息。数字签名本质上是逆向非对称加密，以保护完整性。数字签名使用发送者的私钥对整个消息或部分（如签名块）进行加密，这样只有拥有发送者公钥的人才能解密。数字签名验证发送者的身份，是消息安全的重要方面。]

[假设你的老板给你发一封电子邮件，告诉你你做得很好，他觉得你下周应该带薪休假。你可能会想确认这封邮件是否真实，是否真的是他发的，还是恶作剧。数字签名的作用是使用发送者的私钥对整个消息或部分（如签名块）进行加密。任何拥有发送者公钥的人都可以解密。让我们回到 Alice 和 Bob 来看看这是如何工作的。]

[Bob 想要给 Alice 发送消息并确保她知道这是他发的，所以他用自己的私钥对其进行签名。当 Alice 使用 Bob 的公钥解密时，她可以阅读消息。假设 Bob 实际上并没有发送这条消息。相反，Eve 假装是 Bob。由于 Eve 没有 Bob 的私钥，她只能使用其他密钥来签署消息。当 Alice 尝试用 Bob 的公钥解密（即验证签名）时，她会得到乱码和废话，如 [Figure 10-3](#part0020.xhtml#ch10fig03) 所示。]

![Images](Images/image00682.jpeg)

* * *

**[FIGURE 10-3    Without having the appropriate key, all you get is gibberish.]**

[总之，要实现消息的完全安全，需要执行以下步骤：]

1. [使用哈希、消息验证码 (MAC) 或哈希 MAC (HMAC) 对消息进行处理，并将结果放在消息末尾。]

2. [使用自己的私钥对消息（通常是哈希值或签名块）进行数字签名。]

3. [使用接收方的公钥对消息进行加密。]

[这个过程在 [Figure 10-4](#part0020.xhtml#ch10fig04) 中有所描述。]

![Images](Images/image00683.jpeg)

* * *

**[FIGURE 10-4    Message security with digital signatures]**

[接收方则执行以下步骤来逆转过程：]

1. [使用接收方的私钥解密消息。]

2. [使用发送者的公钥验证签名。]

3. [重新计算哈希、MAC 或 HMAC 并与收到的结果进行比较，以确保传输过程中没有错误。]

[不止一种类型的数字签名存在。我刚才描述的类型是最常见的，称为 *direct digital signature*。另一种类型是 *arbitrated digital signature*，它与前述过程类似，但由受信任的第三方对消息进行数字签名，以证明发送者的身份。]
