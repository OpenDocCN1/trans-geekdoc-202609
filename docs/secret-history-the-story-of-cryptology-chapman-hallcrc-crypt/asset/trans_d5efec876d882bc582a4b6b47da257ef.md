
现在，我们删除最右列中所有不满足 13-光滑的分解式。剩下的是：

| $k$ | $\lfloor\sqrt{kn}\rfloor$ | $\lceil\sqrt{kn}\rceil$ | 前一数值的平方 |
|---|---:|---:|---|
| 1 | 71 |  | $5{,}041=-100=(-1)(2)^2(5)^2$ |
| 1 |  | 72 | $5{,}184=40=(2)^3(5)$ |
| 2 | 101 |  | $10{,}201=-81=(-1)(3)^4$ |
| 5 | 160 |  | $25{,}600=-105=(-1)(3)(5)(7)$ |
| 5 |  | 161 | $25{,}921=216=(2)^3(3)^3$ |
| 6 |  | 176 | $30{,}976=130=(2)(5)(13)$ |
| 8 | 202 |  | $40{,}804=-324=(-1)(2)^2(3)^4$ |

现在我们构造相应的矩阵方程。

$$\begin{pmatrix}
1&0&1&1&0&0&1\\
0&1&0&0&1&1&0\\
0&0&0&1&1&0&0\\
0&1&0&1&0&1&0\\
0&0&0&1&0&0&0\\
0&0&0&0&0&0&0\\
0&0&0&0&0&1&0
\end{pmatrix}
\begin{pmatrix}x_1\\x_2\\x_3\\x_4\\x_5\\x_6\\x_7\end{pmatrix}
=
\begin{pmatrix}0\\0\\0\\0\\0\\0\\0\end{pmatrix}$$

经过简单的线性代数运算，我们得到关于 $x$ 的列向量的以下解。

$$\begin{pmatrix}1\\0\\1\\0\\0\\0\\0\end{pmatrix},\quad \begin{pmatrix}1\\0\\0\\0\\0\\0\\1\end{pmatrix},\quad \begin{pmatrix}1\\0\\1\\0\\0\\0\\1\end{pmatrix}.$$

第一个解使用的关系是

$$(71)^2=5{,}041=-100=(-1)(2)^2(5)^2\pmod{5{,}141}$$

和

$$(101)^2=10{,}201=-81=(-1)(3)^4\pmod{5{,}141}$$

将它们组合起来，我们有

$$(71\cdot101)^2=(-1)^2(2\cdot5\cdot9)^2\pmod{5{,}141}$$

$$(71 \cdot 101)^2 = (2 \cdot 5 \cdot 9)^2 \pmod{5,141}$$

$$(7,171)^2 = (90)^2 \pmod{5,141}$$

$$(2,030)^2 = (90)^2 \pmod{5,141}$$

$$2,030 - 90 = 1,940$$

$$\gcd(1940, 5141) = 97$$

然后我们可以用 5,141/97 = 53 得到完整的分解：5,141 = (97)(53)。如果最大公约数是 1，我们就会继续尝试第二个解，甚至第三个解。

虽然这里详述的方法以 Dixon 命名，但 Dixon 本人谦逊地指出：

> ……这种方法的历史比我在 1981 年发表的论文要悠久得多。引用我论文的文献有时似乎没有意识到这一点。例如，维基百科的词条似乎把这个想法归功于我。事实是，这个想法以某种形式早已存在了更长时间，但没有人能够对所使用的版本的时间复杂度给出严格的分析。我在论文中所做的是证明该方法的随机化版本可以被分析，并且（至少在定性和渐近意义上）它比其他已知方法更快（特别是，在 log $N$ 上是次指数的）。据我所知，除了改进常数之外，这一点至今仍然成立……
>
> 我并没有暗示我所描述的随机化版本在实践中能够与当时正在使用的算法相竞争（尽管其中大多数算法仍然没有严格的分析）。我认为没有人认真地尝试过用随机平方来分解一个大数。

Dixon 在 1981 年发表论文时并不了解全部历史，但他后来在一篇论文中将其包含在内。在近几十年密码学重要工作似乎呈现的一个主题中，Dixon 1981 年的论文被第一个投稿的期刊拒绝了。

### 15.7.1 二次筛法

使用 Dixon 算法时，可能会浪费大量时间来分解那些最终并非 $B$-光滑的数，这些数在矩阵步骤之前就会被丢弃。二次筛法通过使用一种经过变通的埃拉托斯特尼筛法快速丢弃那些不是 $B$-光滑的数，从而消除了这种低效性的大部分。在遍历数字时，不是在该数能被一个素数整除时将其划掉，而是用能整除该数的特定素数的最高次幂去除它。用因子基中的所有素数以这种方式筛过之后，

## 15.8 Pollard 的数域筛法^34

新方法并不总是很快被接受，即使在数学领域也是如此。有些人对 Pollard 的最新成果持怀疑态度，但当第九个费马数 $F_9 = 2^{2^9} + 1$ 在 1990 年使用数域筛法被分解时，它的价值就变得显而易见了。Carl Pomerance 总结了这一事件的意义：^35

> 这一轰动性的成就向世界宣告，Pollard 的数域筛法已经到来。

对该算法的描述需要超出本书范围的现代代数背景；然而，它与一些较简单的方法有一些共同之处。例如，筛法仍然是这种改进算法中最耗时的步骤。

2003 年，Adi Shamir（RSA 中的“S”）与 Eran Tromer 一起发表了基于数域筛法执行分解的专用硬件设计方案。^36 他们将其命名为 TWIRL，即 The Weizmann Institute Relation Locator（魏茨曼研究所关系定位器）的缩写，魏茨曼研究所正是他们的雇主。“关系定位器”指的是在矩阵中寻找分解关系，就像[第 15.7 节]中描述的那样。这两位研究者估计，价值 1000 万美元的硬件足以让这种设计的机器在不到一年的时间内完成 1,024 位 RSA 密钥的筛法步骤。

RSA 在抵御分解攻击方面的安全性与其最初创建时一样。改进的分解技术和改进的硬件只是迫使使用者使用更长的密钥。如果 TWIRL 让你担忧，只需使用 2,048 位密钥。正如在第 15.1.12 节中所看到的，你最需要担心的是确保所使用的素数尽可能以随机的方式生成！

### 15.8.1 其他方法

还有许多其他的分解算法，包括利用连分数（上面的一些方法中使用了！）和椭圆曲线的方法。也许最引人入胜的是 Peter Shor 在 1994 年提出的一种方法，该方法在拥有量子计算机运行的情况下可以在多项式时间内完成分解。^37 鼓励读者查阅参考文献以了解更多。

^34 Lenstra, Arjen K., Hendrik W. Lenstra, Jr., Mark S. Manasse, and John M. Pollard, “The Number Field Sieve,” in Lenstra, Arjen K. and Hendrik W. Lenstra, Jr., editors, *The Development of the Number Field Sieve*, Lecture Notes in Mathematics, Vol. 1554, Springer, Berlin, Germany, 1993, pp. 11–42.

^35 Pomerance, Carl, “A Tale of Two Sieves,” *Notices of the American Mathematical Society*, Vol. 43, No. 12, December 1996, pp. 1473–1485, p. 1480 cited here.

^36 Shamir, Adi and Eran Tromer, “Factoring Large Numbers with the Twirl Device,” in Boneh, Dan, editor, *Advances in Cryptology – CRYPTO 2003 Proceedings*, Lecture Notes in Computer Science, Vol. 2729, Springer, Berlin, Germany, 2003, pp. 1–27.

^37 Shor, Peter, “Algorithms for quantum computation: discrete logarithms and factoring,” in Goldwasser, Shafi, editor, *35th Annual IEEE Symposium on Foundations of Computer Science (FOCS)*, IEEE Computer Society Press, Los Alamitos, California, 1994, pp. 124–134.

### 15.8.2 密码学幽默

虽然 2 不是一个大素数，但它是唯一的偶素数。我是从一本名为《偶素数》^38 的枯燥书中学到的。当然，作为*唯一*的偶素数，使它成为所有素数中最奇特的素数。

^38 作者是《一阶群》的作者。

## 参考文献与延伸阅读

### 关于非分解型 RSA 攻击

- Açıçmez, Onur, Çetin Kaya Koç, and Jean-Pierre Seifert, “On the Power of Simple Branch Prediction Analysis,” in Deng, Robert and Pierangela Samarati, editors, *ASIACCS ’07: Proceedings of the 2nd ACM Symposium on Information, Computer and Communications Security*, ACM, New York, 2007, pp. 312–320. 这是本章未讨论的针对 RSA 的攻击之一。与计时攻击一样，它假设可以访问预期接收者的机器。
- Blakley, G. Robert, and Itshak Borosh, “Rivest-Shamir-Adleman Public Key Cryptosystems do not Always Conceal Messages,” *Computers & Mathematics with Applications*, Vol. 5, No. 3, 1979, pp. 169–178.
- Boneh, Dan, “Twenty Years of Attacks on the RSA Cryptosystem,” *Notices of the American Mathematical Society*, Vol. 46, No. 2, 1999, pp. 203–213. 这是一篇不错的综述论文。
- Boneh, Dan and Glenn Durfee, “Cryptanalysis of RSA with Private Key *d* Less than N^0.292,” in Stern, Jacques, editor, *Advances in Cryptology – EUROCRYPT ’99 Proceedings*, Lecture Notes in Computer Science, Vol. 1592, Springer, Berlin, Germany, 1999, pp. 1–11.
- Boneh, Dan, Glenn Durfee, and Yair Frankel, “An Attack on RSA Given a Small Fraction of the Private Key Bits,” in Ohta, Kazuo and Dingyi Pei, editors, *Advances in Cryptology – ASIACRYPT ’98*, Lecture Notes in Computer Science, Vol. 1514, Springer, Berlin, Germany, 1998, pp. 25–34.
- Boneh, Dan, Antoine Joux, and Phong Q. Nguyen, “Why Textbook ElGamal and RSA Encryption are Insecure,” in Okamoto, Tatsuaki, editor, *Advances in Cryptology – ASIACRYPT 2000 Proceedings*, Lecture Notes in Computer Science, Vol. 1976, Springer, Berlin, Germany, 2000, pp. 30–43.
- Coppersmith, Don, “Small Solutions to Polynomial Equations, and Low Exponent RSA Vulnerabilities,” *Journal of Cryptology*, Vol. 10, No. 4, December 1997, pp. 233–260.
- DeLaurentis, John M., “A Further Weakness in the Common Modulus Protocol for the RSA Cryptalgorithm,” *Cryptologia*, Vol. 8, No. 3, July 1984, pp. 253–259.
- Diffie, Whitfield and Hellman, Martin, “New Directions in Cryptography,” *IEEE Transactions on Information Theory*, Vol. IT-22, No. 6, November 1976, pp. 644–654.
- Hayes, Brian P., “The Magic Words Are Squeamish Ossifrage,” *American Scientist*, Vol. 82, No. 4, July–August 1994, pp. 312–316. 这篇论文讨论了分解技术并包含了一些历史。标题是为了纪念在 Martin Gardner 的《科学美国人》专栏中，RSA 挑战密文所隐藏信息的恢复。
- Johnson, Don, *ECC, Future Resiliency and High Security Systems*, Certicom Whitepaper, March 30, 1999, revised July 6, 1999, available online at http://web.archive.org/web/20040215121823/www.comms.engg.susx.ac.uk/fft/crypto/ECCFut.pdf.
- Joye, Marc and Jean-Jacques Quisquater, *Faulty RSA Encryption*, UCL Crypto Group Technical Report CG-1997/8, Université Catholique de Louvain, Louvain-La-Neuve, Belgium, 1987.
- Kaliski, Burt and Matt Robshaw, “The Secure Use of RSA,” *CryptoBytes*, Vol. 1, No. 3, Autumn 1995, pp. 7–13, available online at ftp://ftp.rsa.com/pub/cryptobytes/cryptonl3.pdf. 这篇论文总结了针对 RSA 的各种攻击。
- Kocher, Paul, “Timing Attacks on Implementations of Diffie-Hellman, RSA, DSS, and Other Systems,” in Koblitz, Neal, editor, *Advances in Cryptology – CRYPTO ’96 Proceedings*, Lecture Notes in Computer Science, Vol. 1109, Springer, Berlin, Germany, 1996, pp. 104–113.

