
6. 如果 s = 0，则转到步骤 1。换句话说，保持重复，直到 s! = 0。这通常不会耗时太长，并且可能在第一次尝试时就发生。

7. Alice 的消息 m 的签名是 (r, s)。

为了验证 Alice 的签名 (r,s)，Bob 将执行以下步骤：

1. 验证 r 和 s 是否为整数且在 [1, n – 1] 范围内。

2. 计算 e = SHA-1(m)。

3. 计算 w = s^(–1) mod n。

4. 计算 u[1] = ew mod n 且 u[2] = rw mod n。

5. 计算 (x[1], y[1]) = u[1]G + u[2] Q[A]。

6. 计算 v = x[1] mod n。

7. 仅当 v = r 时接受签名。

这与传统的 DSA 非常相似，只是使用了椭圆曲线群。ECDSA 相当安全。

**Note**

ECDSA 曾出现几次实施漏洞的报告，但这些都是由于实现错误，而非算法本身存在缺陷。例如，2011 年 3 月，研究人员在 IACR（International Association of Cryptological Research）的一篇论文中展示了可以利用 OpenSSL 的定时攻击获取服务器私钥的方法。OpenSSL 使用二进制域上的 ECDSA 进行验证。然而，该漏洞已在后续的 OpenSSL 版本中修复，属于实现问题，而非算法缺陷。

#### Conclusions

本章我们探讨了椭圆曲线群在密码学中的应用。这可能是整本书中数学难度最大的章节。对于大多数安全应用，您只需了解各种椭圆曲线算法的通用描述即可。如果您想更深入地研究密码学，本章为您提供了入门。本章还推荐了多种资源，供您进一步深入研究 ECC。

#### Test Your Knowledge

[1](#part0021.xhtml#ch11qu1). 下列哪个方程最与椭圆曲线密码学相关？

A. M^e % n

B. P = C^d % n

C. C^e % n

D. y² = x³ + Ax + B

[2](#part0021.xhtml#ch11qu2). 哪种 ECC 变体需要使用 SHA？

[3](#part0021.xhtml#ch11qu3). 什么是代数群？

[4](#part0021.xhtml#ch11qu4). 什么是离散对数？

[5](#part0021.xhtml#ch11qu5). ECC DH 产物是什么类型的密钥？

##### Answers

[1](#part0021.xhtml#ch11qu1a). D

[2](#part0021.xhtml#ch11qu2a). ECDSA

[3](#part0021.xhtml#ch11qu3a). 代数群是由一个集合、一个身份元素、一个运算以及其逆运算组成的代数结构。

[4](#part0021.xhtml#ch11qu4a). 离散对数是某个整数 k，满足方程 x^k = y，其中 x 和 y 都是有限群中的元素。

[5](#part0021.xhtml#ch11qu5a). 临时密钥

#### Endnotes

[1](#part0021.xhtml#ch11note1). 如需更多关于 ECC 的信息，请阅读 Vivek Kapoor、Vivek Sonny Abraham 和 Ramesh Singh 的论文 “Elliptic Curve Cryptography”，网址为 [http://csis.bits-pilani.ac.in/faculty/murali/netsec-10/seminar/refs/abhishek3.pdf](http://csis.bits-pilani.ac.in/faculty/murali/netsec-10/seminar/refs/abhishek3.pdf)。

[2](#part0021.xhtml#ch11note2). Lawrence C. Washington，《Elliptic Curves: Number Theory and Cryptography, Second Edition》（Chapman and Hall/CRC, 2008）。

[3](#part0021.xhtml#ch11note3). 如需更多关于 ECC 的信息，请参阅 Darrel Hankerson、Alfred Menezes 和 Scott Vanstone 的《Guide to Elliptic Curve Cryptography》（Springer Professional Computing, 2004）。
