

$$C\left\lbrack X \right\rbrack = A\left\lbrack X \right\rbrack - B\left\lbrack X \right\rbrack = {\sum\limits_{i = 0}^{m - 1}{c_{i}x^{i}}},\text{ 其中 }c_{i} = \left( a_{i} - b_{i} \right)\bmod 2$$

(1.15)

例如，`A[X] = x² + x + 1` 和 `B[X] = x² + 1`。`A[X] + B[X] = (2 \bmod 2)x² + x + 2 \bmod 2 = x` 且 `A[X] − B[X] = x`。

请注意，在 `GF(2^m)` 中加法和减法是同一运算。

对于乘法运算，似乎两个多项式相乘会返回正确结果，即 `C'[X] = A[X]B[X] = (x²+x+1)(x²+1) = x⁴ + x³ + x + 1 ∉ GF(2^m)`。然而，事实并非如此；结果元素不属于所考虑的域。现在回顾一下素数域：`GF(7) = {0,1,…6}`，相乘以下两个元素：`3.4 = 12 \bmod 7 = 5 ∈ GF(7)`。通过计算模运算可获得正确结果。扩展域也是同样的情况，我们必须将乘法结果除以一个多项式，即用一个表现得像素数的多项式（称为不可约多项式）来约简 `C'[X]`。寻找不可约多项式 $P\left\lbrack X \right\rbrack = {\sum_{i = 0}^{m}{p_{i}x^{i}}},\text{ 其中 }p[i] \in GF(2)$。对于 `GF(2³)`：`P[X] = x³ + x + 1`。因此，扩展域中正确的乘法方法是：`C[X] = A[X]B[X] \bmod P[X]`。对于每个域，都存在若干个不可约多项式。

对于 `GF(2^m)` 中的求逆运算，可以使用扩展欧几里得算法。例如，要找到 `(x³+x+1) \bmod (x⁵+x³+1)` 的乘法逆元，按如下方式使用扩展欧几里得算法：

*   `x⁵ + x³ + 1 = x²(x³+x+1) + (x²+1)`
*   `x³ + x + 1 = x(x²+1) + 1`
*   `x³ + x + 1 − x(x²+1) = 1`
*   `(x³+1)(x³+x+1) + x(x⁵+x³+1) = 1`
*   `(x³+x+1)^(-1) = (x³+1)`

#### 1.2.5.4 域的特征

域的特征是一个与每个域相关联的数（非负整数）。它表示为 `Ch(F)`；它是乘法单位元（1）自加以得到加法单位元（0）所需的最小次数。例如：`F[2] = {0,1}` 具有以下合成表，其 `Ch(F) = 2`（1+1=0）。

*   + 0 1 * 0 1
*   0 0 1 0 0 0
*   1 1 0 1 0 1

**定理**：域的特征要么是 0，要么是一个素数。

**证明**：采用反证法。设 `Ch(F) = n`，其中 `n` 不是素数。因此，`n = ab`，使得 `a` 和 `b` 均不为 `1` 且 `1 < a, b < n`。根据域特征的定义，`n ⋅ 1 = 0`，这意味着 `(ab) ⋅ 1 = 0`。展开点乘表示法，`(a⋅1) * (b⋅1) = 0`。在域中不存在零因子，所以 `(a⋅1)` 或 `(b⋅1)` 其中之一为 0。假设 `(a⋅1) = 0`。这与 `n` 是最小正整数的假设相矛盾。因此，`Ch(F) = 0 或 p`。

## 1.3 密码学应用

这些数论和抽象代数概念在现代密码学中有直接应用。密码系统的设计涉及单向过程，这些过程易于计算但难以逆转。这些单向过程是利用数论概念开发的。考虑分解因式的例子，这是数论中一个非常基本的概念，也是此类单向过程的一个非常著名的例子，因为将任意两个大素数相乘非常容易，但给定乘积后恢复这些素因子却极其困难。这个分解因式问题结合欧拉定理构成了最流行的 RSA 密码系统的基础。另一个此类单向过程的例子是离散对数问题，它指出：给定两个互质整数 `a` 和 `n` 以及另一个整数 `k`，求 `a^k \bmod n` 很容易，但给定 `a^k \bmod n` 后求 `k` 却极其困难。离散对数问题构成了许多密码系统的基础，Diffie-Hellman 密钥交换算法是该问题的第一个成功应用案例。最近，这些思想通过用椭圆曲线上点的更奇异运算取代模运算而得到了扩展和丰富。

## 1.4 本章小结

在本章中，我们讨论了数论和抽象代数的基础知识，它们在理解和开发密码系统中发挥着重要作用。现代密码学完全基于抽象代数和数论。因此，我们试图简要涵盖这两个先决条件的各个方面，重点关注它们在密码学中的应用。此外，考虑到篇幅限制以及概念的清晰度，我们有选择地挑选了主题，仅详细阐述了那些应用可直接体现在密码学世界中的内容。

# 参考文献

1. V. Shoup, A Computational Introduction to Number Theory and Algebra. Cambridge University Press, 2009.
2. J. J. Tattersall, Elementary Number Theory in Nine Chapters. Cambridge University Press, 2005.
3. A. Weil, Basic Number Theory, vol. 144. Springer Science & Business Media, 2013.
4. B. Gupta, D. P. Agrawal, and S. Yamaguchi, eds. Handbook of Research on Modern Cryptographic Solutions for Computer and Cyber Security. IGI Global, 2016.
5. P. Premkamal, S. Kumar, P. J. A. Kumar Pasupuleti, and Alphonse, “Efficient escrow-free CP-ABE with constant size ciphertext and secret key for big data storage in cloud.”, International Journal of Cloud Applications and Computing (IJCAC), vol. 10, no. 1, pp. 28–45, 2020.
6. C. C. Sims, “Abstract algebra: a computational approach,” No. 512.02 S5. J. Wiley, 1984.
7. D. S. Dummit, and R. M. Foote, Abstract Algebra, vol. 3. Wiley Hoboken, 2004.

# 第 2 章

# 密码学导论

密码学不仅是一个研究领域，更是当今数字世界的强制性需求。它是保护数字信息在系统内部及传输过程中安全的重要工具。如果我们仔细观察，会发现密码学无处不在，从互联网上的安全通信到用户认证，再到磁盘上的文件加密。密码学处于每一个需要安全性和隐私性的系统或网络的核心位置。密码学已存在数千年，并将继续作为开发安全机制的基础。本章涵盖与密码学相关的基本概念。它简要讨论了传统密码学和现代密码学，以及从传统密码学到现代密码学的演变历程。它详细描述了密码学原理和关键术语，以建立坚实的基础。

## 2.1 密码学导论

